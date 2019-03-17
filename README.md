# gsoc-19-research

## Organizations

- [CNCF](https://github.com/cncf/soc)

### Projects

- CoreDNS
  - [Source IP based query block/allow](https://github.com/cncf/soc#support-source-ip-based-query-blockallow) (Main focus)
  - [Google Cloud Backend](https://github.com/cncf/soc#support-google-cloud-dns-backend)
  - [Azure Backend](https://github.com/cncf/soc#support-azure-dns-backend)

**Links:**
- [Introductory Talk](https://www.youtube.com/watch?v=LIoC6aC--jQ) [TODO: Write notes after watching the talk again]
- [Video on Usage](https://www.youtube.com/watch?v=whEZn7wmrDc)
- [Webinar](https://www.youtube.com/watch?v=dz9S7R8r5gw)
- [CoreDNS in k8s](https://www.youtube.com/watch?v=qRiLmLACYSY)
- [What are DNS Zones](https://www.think-like-a-computer.com/2011/06/11/dns-zones-explained/)


*Contribution Stats: * 1 WIP PR created

#### General Notes about k8s and the whole ecosystem around it

- **Kubernetes** [TODO]

- **CoreDNS**
  - Clients make requests that are routed to the DNS servers (seem like primary but are secondary) through recursives (like Google or Cloudflare)
  - refresh -> how many times the secondary pulls data from the hidden primary
  - retry -> checks if the data has changed, pulls the headers check for change in serial and if it is changed then it refreshes
  
  **Important:** Caddy [middleware](https://github.com/pyed/ipfilter) for block-allow IP mechanism
  Firewall example codebase https://github.com/middelink/mikrotik-fwban
  ipfilter library: https://github.com/jpillora/ipfilter/
  read later: https://www.reddit.com/r/golang/comments/3wpi6w/is_it_possible_to_monitor_and_redirect_http/
