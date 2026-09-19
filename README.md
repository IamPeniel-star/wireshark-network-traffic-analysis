# Network Traffic Analysis Using Wireshark

**Tool:** Wireshark  
**Capture interface:** eth0  

## Objective

Capture and analyze network traffic with Wireshark, identify common protocols, inspect IP addresses and ports, analyze TCP connection establishment and application data, and interpret packet-level information.

## Tasks and Results

### 1. Capture Interface
- Interface used: `eth0`
- Local IPv4 address observed: `10.0.2.15`

### 2. IP Address Analysis
- Local/source host: `10.0.2.15`
- HTTP destination observed: `104.20.23.154`
- DNS servers observed: `41.223.65.1` and `8.8.8.8`
- ICMP destination observed: `8.8.8.8`

### 3. TCP Connection
A TCP connection to the HTTP server was identified.

- Source port: `56526`
- Destination port: `80`
- SYN: client → server
- SYN/ACK: server → client
- ACK: client → server
- TCP stream index: `2` for the HTTP conversation

### 4. TCP Flags
The capture shows SYN, SYN/ACK, ACK, FIN/ACK and related TCP packets during the connection.

### 5. Sequence and Acknowledgment Numbers
For the requested TCP packet:

- Sequence Number: `428774349`
- Acknowledgment Number: `3337280002`

### 6. TCP Segment Length
The HTTP GET packet carries **75 bytes** of TCP data.

### 7. HTTP Request
The captured request was:

- Method: `GET`
- URI: `/`
- Host: `example.com`
- HTTP version: `HTTP/1.1`
- User-Agent: `curl/8.20.0`

### 8. HTTP Response
The server returned:

- Status: `HTTP/1.1 200 OK`
- Content-Type: `text/html`
- Server: `cloudflare`
- Transfer-Encoding: `chunked`

### 9. DNS Analysis
DNS traffic was captured for `example.com`, including A and AAAA queries and responses.

One observed A response returned:

- `104.20.23.154`
- `172.66.147.243`

### 10. ICMP Analysis
ICMP echo request/reply traffic was captured between:

- Source: `10.0.2.15`
- Destination: `8.8.8.8`

Multiple echo requests and corresponding replies were observed.

## Wireshark Filters Used

```text
tcp
tcp.flags.syn == 1 && tcp.flags.ack == 1
http
dns
icmp
tcp.stream eq 2
```

## Conclusion

The capture demonstrates how Wireshark can be used to inspect network communication at packet level. The analysis covered Ethernet/IP addressing, TCP connection establishment, TCP ports and flags, sequence and acknowledgment numbers, HTTP request/response traffic, DNS resolution, and ICMP echo traffic.

## Evidence

Screenshots from the Wireshark capture will be placed in the `screenshots/` directory and referenced here as evidence for the analysis above.
