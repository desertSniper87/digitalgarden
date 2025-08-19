---
{"dg-publish":true,"permalink":"/slow-loris/"}
---



- https://www.cloudflare.com/learning/ddos/ddos-attack-tools/slowloris/
> Slowloris is an [[OSI Layer 7\|Application Layer]] attack which operates by utilizing partial [[net/protocols/Hypertext Transfer Protocol\|HTTP]] requests. The attack functions by **opening connections to a targeted Web server** and then keeping **those connections open as long as it can**.

Slowloris is a DDoS attack tool used to perform layer-7 DDoS attacks to take down web infrastructure
- It is distinctly different from other tools in that it uses perfectly legitimate HTTP traffic to take down a target server
- In Slowloris attacks, the attacker sends partial HTTP requests to the target web server or application
- Upon receiving the partial requests, the target server opens multiple connections and waits for the requests to complete
- However, these requests remain incomplete, causing the target server’s maximum concurrent connection pool to be filled up and additional connection attempts to be denied.

![Slow Loris-1754938633785.webp](/img/user/Slow%20Loris-1754938633785.webp)

- https://github.com/gkbrk/slowloris


## Methodology

1. **Opening Connections**: The attacker opens a large number of HTTP connections to the target web server.
2. **Partial Requests**: The attacker sends incomplete HTTP requests (header data only, without completing the body). These incomplete requests keep the connection open but aren’t immediately processed by the server because the HTTP headers aren’t fully received.
3. **Keep-Alive Header**: The attack uses the Keep-Alive HTTP header, which tells the server to maintain the connection open for a longer period of time, even though the request isn’t completed. This effectively ties up server resources for extended periods.
4. **Maintain Connections**: Slowloris keeps the connections open by periodically sending small amounts of data to the server to prevent it from timing out or closing the connection. This keeps the server waiting for the full request, thus blocking legitimate traffic from getting through.
5. **Exhausting Connections**: Over time, the server accumulates many incomplete requests, filling up the available connection pool. When the connection pool is exhausted, new legitimate connections can no longer be established, leading to a **Denial of Service (DoS)**, where legitimate users cannot access the website or services.