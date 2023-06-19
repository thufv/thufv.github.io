---
layout: default
title: A Translator from P4 Programs to Boogie
permalink: /research/P4-to-Boogie
---

### <center>P4B: A Translator from P4 Programs to Boogie</center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Chong Ye</center>

### <center>Abstract</center>

P4 is a main-streaming language for Software Defined Network (SDN) data planes. Compared to previous SDN protocols, P4 is target-independent, feasible, and configurable. However, logic errors may occur in P4 programs, resulting in improper packet processing, which may cause serious network errors and information disclosure. In addition, P4 programs contain many branches and thus are more challenging to ensure correctness.
Formal verification is a powerful technique to verify the correctness of P4 programs. Unfortunately, current P4 verification studies lack basic toolchains, and their intermediate languages are not expressive enough. We present P4b, an efficient translator from P4 programs to Boogie, a verification-oriented intermediate representation. We provide formal translation rules to ensure the correctness of the translation process. The translated results can be verified by the toolchain of Boogie. We conducted experiments on 170 P4 programs collected from GitHub, and the experiment results demonstrate that our translator is useful and practical.

### <center>Source Code</center>

P4-to-Boogie is the tool that implements our approach. The <a href="https://github.com/Invincibleyc/P4B-Translator">source code</a> contains all source code of P4-to-Boogie. Please refer to `README.md` for instructions to compile P4-to-Boogie.

### <center>Tool Usage</center>

P4B takes P4 programs as input.

```
# Translate P4 into Boogie for Boogie verifier
p4c-translator <P4File> -o <outFile>

# Translate P4 into Boogie for UAutomizer
p4c-translator <P4File> --ua2 --p4ltl <P4LTLSpec> -o <outFile>
```

### <center>Examples</center>

**Example 1:** <a href="https://github.com/p4lang/tutorials/blob/master/exercises/basic/solution/basic.p4">basic.p4</a>

Description: A basic P4 program from <a href="https://github.com/p4lang">p4lang</a>. This program only supports ethernet and IPv4.

```c++
// Translate basic.p4 to boogie
p4c-translator basic.p4 -o out.bpl

// Verify out.bpl with the boogie verifier
boogie out.bpl
	
// P4 source code & Boogie translation result
// ******** Header ********
// Header src (P4)
typedef bit<48> macAddr_t;
header ethernet_t {
	macAddr_t dstAddr;
	macAddr_t srcAddr;
	bit<16>   etherType; // length: 16
}
// Header dst (Boogie)
type macAddr_t = bv48;  // type define
var hdr.ethernet:Ref;   // reference of the header
var hdr.ethernet.valid:bool;
var hdr.ethernet.dstAddr:macAddr_t;
var hdr.ethernet.srcAddr:macAddr_t;
var hdr.ethernet.etherType:bv16;  // bitvector of length 16

// ******** Parser ********
// Parser src (P4)
parser MyParser(packet_in packet, out headers hdr,
	inout metadata meta, inout standard_metadata_t standard_metadata) {
	...
}
// Parser dst (Boogie)
procedure {:inline 1} MyParser()
	modifies drop, hdr.ethernet.valid, hdr.ipv4.valid;
{
	call MyParser$start();  // start is always the 
}

// ******** Parser State ********
// Parser State src (P4)
state start {
	transition parse_ethernet;
}
state parse_ethernet {
	packet.extract(hdr.ethernet);
	transition select(hdr.ethernet.etherType) {
		0x800: parse_ipv4;
		default: accept;
	}
}
// Parser State dst (Boogie)
procedure {:inline 1} MyParser$start()
modifies hdr.ethernet.valid, hdr.ipv4.valid;
{
    hdr.ethernet.valid := true;
    if(hdr.ethernet.etherType == 2048bv16){
        call MyParser$parse_ipv4();
    }
    else{
        call MyParser$accept();
    }
}

// ******** Control ********
// Control src (P4)
control MyIngress(inout headers hdr,
			inout metadata meta,
			inout standard_metadata_t standard_metadata) {
	...
	apply {
		if (hdr.ipv4.isValid()) {
			ipv4_lpm.apply();
		}
	}
}
// Control dst (Boogie)
procedure {:inline 1} MyIngress()
modifies ...; // modified variables are omitted here
{
	if(hdr.ipv4.valid){
		call ipv4_lpm_0.apply();
	}
}

// ******** Action ********
// Action src (P4)
action ipv4_forward(macAddr_t dstAddr, egressSpec_t port) {
	standard_metadata.egress_spec = port;
	hdr.ethernet.srcAddr = hdr.ethernet.dstAddr;
	hdr.ethernet.dstAddr = dstAddr;
	hdr.ipv4.ttl = hdr.ipv4.ttl - 1;
}
// Action dst (Boogie)
procedure {:inline 1} ipv4_forward(dstAddr:macAddr_t, port:egressSpec_t)
modifies forward, hdr.ethernet.dstAddr, hdr.ethernet.srcAddr, hdr.ipv4.ttl, standard_metadata.egress_port, standard_metadata.egress_spec;
{
	standard_metadata.egress_spec := port;
	standard_metadata.egress_port := port;
	forward := true;
	hdr.ethernet.srcAddr := hdr.ethernet.dstAddr;
	hdr.ethernet.dstAddr := dstAddr;
	hdr.ipv4.ttl := add.bv8(hdr.ipv4.ttl, 255bv8);
}

// ******** Table ********
// Table src (P4)
table ipv4_lpm {
	key = {
		hdr.ipv4.dstAddr: lpm;
	}
	actions = {
		ipv4_forward;
		drop;
		NoAction;
	}
	size = 1024;
	default_action = drop();
}
// Table dst (Boogie)
procedure {:inline 1} ipv4_lpm_0.apply()
modifies drop, forward, hdr.ethernet.dstAddr, hdr.ethernet.srcAddr, hdr.ipv4.dstAddr, hdr.ipv4.ttl, standard_metadata.egress_port, standard_metadata.egress_spec;
{
	hdr.ipv4.dstAddr := hdr.ipv4.dstAddr;
	if(ipv4_lpm_0.action_run == ipv4_lpm_0.action.ipv4_forward){
		call ipv4_forward(ipv4_lpm_0.ipv4_forward.dstAddr, ipv4_lpm_0.ipv4_forward.port);
	}
	else if(ipv4_lpm_0.action_run == ipv4_lpm_0.action.drop){
		call drop();
	}
	else if(ipv4_lpm_0.action_run == ipv4_lpm_0.action.NoAction_0){
		call NoAction_0();
	}
	else {
		call drop();
	}
}
```