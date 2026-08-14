# Findings

## Executive summary

Normal network traffic in the form of DNS resolution, HTTP sessions, TCP connections, and TLS/HTTPS connections can be seen from this packet capture. Web browsing activities performed using a web browser towards internet services and particularly to Google were the main source of this traffic.

## DNS Traffic Analysis

## Objective

Identify DNS queries and responses and determine whether any suspicious domain resolution activity occurred.

## Observed Traffic

-Client IP: 10.0.2.15

-DNS server: 10.0.2.3

-Protocol: UDP/53

## Example packets observed 

-Query: 10.0.2.15 > 10.0.2.3

-Response: 10.0.2.3 > 10.0.2.15

## Resolved domains included services such as:

-Messenger..

-login.live.com

## Interpretation

The client sent standard DNS queries requesting IP addresses for internet services. The DNS server successfully responded with various resource records. The time taken for query and response and their structure are consistent with regular browsing and application usage.

## Security Assessment

-No DNS tunnelling indicators observed.

-No unusually long domain names observed.

-No high-volume DNS bursts observed.

-No suspicious or obviously malicious domains identified.

## Assessment 

-Non-threatening DNS Traffic


## TCP Handshake Analysis

## Objective

Verify proper TCP session establishment and identify abnormal connection behavior.

## Observed Handshake Sequence

Example session:

192.168.3.131 → 72.14.213.102 : SYN

72.14.213.102 → 192.168.3.131 : SYN, ACK

192.168.3.131 → 72.14.213.102 : ACK

Additional successful handshakes were observed with:

72.14.213.147

65.55.206.209

65.55.17.37

207.46.148.38

## Interpretation

The TCP three-way handshake completed successfully, confirming that:

-the destination hosts were reachable,

-the services were listening on the target ports,

-and the client established valid TCP sessions.

Some SYN re-transmissions were observed later in the capture, which is commonly caused by packet loss, latency, or delayed responses.

## Security Assessment

-No evidence of SYN flood behavior.

-No evidence of half-open scan activity.

-No rapid multi-port probing observed.

-Connection establishment was largely successful.

Assessment: Normal TCP connection behavior

## TLS/HTTPS Analysis

## Objective

Inspect encrypted connection establishment.

## Observed TLS Records

Example TLS packet:

16 03 01 ...

## Observed sequence:

Client Hello

Server Hello

Certificate

Server Hello Done

Communicating hosts included:

192.168.3.131 → 72.14.213.147

192.168.3.131 → 72.14.213.102

## Interpretation

The browser initiated HTTPS sessions with Google servers. The server presented a certificate and negotiated encryption parameters before encrypted application data was exchanged.

## Security Assessment

-TLS handshake completed normally.

-No SSL downgrade indicators observed.

-No malformed TLS records observed.

-No certificate warnings were visible in the capture.

Assessment: Normal HTTPS encryption activity.

## Additional Traffic Observed

## ARP

ARP requests and replies were observed for local address resolution.

Example: Who has 10.0.2.2? Tell 10.0.2.15

Assessment: Normal local network operation.

## ICMPv6

Router Solicitation

Router Advertisement

Multicast Listener messages.

Assessment: Normal IPv6 neighbor and router discovery traffic.

## Malicious Activity Assessment

The following indicators were specifically reviewed:

Indicator	                             Result

Known malicious domains     	-     Not observed

Known malicious IP addresses	-     Not observed

Port scanning behavior	      -     Not observed

SYN flood pattern	            -     Not observed

Exploit payloads	            -     Not observed

SQL injection strings         -     Not observed

Command injection strings     -   	 Not observed

Excessive failed connections	 -    Not observed

DNS tunneling behavior	      -     Not observed

Large outbound data transfers	 -    Not observed

## Conclusion

Based on the full packet capture, the observed traffic is consistent with:

normal web browsing,

DNS name resolution,

HTTPS session establishment,

and routine operating system network activity.

No clear evidence of malicious activity was identified in this packet capture.
