# What Happens When You Type `google.com` and Press Enter

Concise, step-by-step walkthrough of the network, transport, and application processes when a user enters `google.com` in a browser and presses Enter.

This README is adapted from [home/schpser/holbertonschool-softy-pinko-docker/README.md](home/schpser/holbertonschool-softy-pinko-docker/README.md). See this file for style reference.

Files:
- This file: [home/schpser/holbertonschool-network/what_happens_when_your_type_google_com_in_your_browser_and_press_enter/README.md](home/schpser/holbertonschool-network/what_happens_when_your_type_google_com_in_your_browser_and_press_enter/README.md)
- Example model: [home/schpser/holbertonschool-softy-pinko-docker/README.md](home/schpser/holbertonschool-softy-pinko-docker/README.md)

## Overview (high level)
1. Browser parses URL and decides navigation vs search.
2. DNS resolution resolves domain → IP.
3. TCP 3-way handshake establishes connection.
4. TLS handshake (for HTTPS) negotiates keys and verifies server.
5. HTTP request/response exchanged.
6. Browser parses and renders content; fetches resources.
7. Caching, redirects, connection reuse, and teardown.

## Visuals

DNS + TCP + TLS + HTTP simplified flow:

Client (Browser)
|
|-- DNS query --> Resolver --> Authoritative DNS
|      (get A/AAAA) 
|
|-- TCP SYN --> Server
|   <-- SYN-ACK
|-- ACK (connection established)
|
|-- TLS ClientHello --> ServerHello / Certificate
|   (key exchange, verify cert)
|-- Encrypted HTTP request --> Encrypted HTTP response
|
|-- Browser parses HTML → requests CSS/JS/images → render

Sequence diagram (ASCII):

Client                           Resolver                           Origin
  |                                 |                                 |
  |----(1) DNS query--------------->|                                 |
  |<---(2) DNS answer---------------|                                 |
  |----(3) TCP SYN --------------------------------->|                 |
  |<---(4) TCP SYN-ACK -------------------------------|                 |
  |----(5) TCP ACK --------------------------------->|                 |
  |----(6) TLS ClientHello -------------------------->|                 |
  |<---(7) TLS ServerHello + Cert -------------------|                 |
  |----(8) TLS Finished ---------------------------->|                 |
  |----(9) HTTP GET (encrypted) ------------------->|                 |
  |<---(10) HTTP/2 or HTTP/1.1 Response (encrypted) -|                 |
  |                                 |                                 |

Rendering flow:

HTML -> DOM
CSS -> CSSOM
DOM + CSSOM -> Render Tree
JavaScript -> may modify DOM/CSSOM -> Layout -> Paint -> Composite

## Key details (concise)
- DNS: cache → /etc/hosts → recursive resolver → authoritative server.
- TCP handshake: SYN, SYN-ACK, ACK (three-way).
- TLS: ClientHello, ServerHello, Certificate, Key Exchange, Finished.
- HTTP: request includes Host header; responses include status, headers, body.
- Redirects (3xx) cause new navigations; caching uses ETag / If-Modified-Since.
- Connection reuse: keep-alive / HTTP/2 multiplexing; FIN/ACK or RST closes.

## Commands to observe
- DNS: dig google.com
- TCP/TLS capture: sudo tcpdump -i any host google.com and port 443 -w capture.pcap
- HTTP: curl -v https://google.com
- Browser: DevTools → Network tab

## References
- RFC 1034 / 1035 (DNS)
- RFC 793 (TCP)
- TLS RFCs (RFC 5246 / RFC 8446)
- HTTP/1.1 (RFC 7230–7235) and HTTP/2