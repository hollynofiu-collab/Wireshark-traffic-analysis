# Findings

## Executive summary

Normal network traffic in the form of DNS resolution, HTTP sessions, TCP connections, and TLS/HTTPS connections can be seen from this packet capture. Web browsing activities performed using a web browser towards internet services and particularly to Google were the main source of this traffic.

## DNS Traffic Analysis

# Objective

Identify DNS queries and responses and determine whether any suspicious domain resolution activity occurred.

# Observed Traffic

-Client IP: 10.0.2.15

-DNS server: 10.0.2.3

-Protocol: UDP/53

# Example packets observed 

-Query: 10.0.2.15 > 10.0.2.3

-Response: 10.0.2.3 > 10.0.2.15

# Resolved domains included services such as:

-Messenger..

-login.live.com

## TCP Analysis
Observed SYN, SYN/ACK, ACK handshake and normal connection closure.

## TLS Analysis
Observed Client Hello and Server Hello packets.
