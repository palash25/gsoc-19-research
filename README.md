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


#### General Notes about k8s and the whole ecosystem around it

- **Kubernetes** [TODO]

- **CoreDNS**
  - Clients make requests that are routed to the DNS servers (seem like primary but are secondary) through recursives (like Google or Cloudflare)
  - refresh -> how many times the secondary pulls data from the hidden primary
  - retry -> checks if the data has changed, pulls the headers check for change in serial and if it is changed then it refreshes
  
  
 ###### Firewalling project 
 -  **Important:** Caddy [middleware](https://github.com/pyed/ipfilter) for block-allow IP mechanism
 -  Firewall example codebase https://github.com/middelink/mikrotik-fwban
 -  ipfilter library: https://github.com/jpillora/ipfilter/
 -  read later: https://www.reddit.com/r/golang/comments/3wpi6w/is_it_possible_to_monitor_and_redirect_http/


###### Azure DNS backend project

AWS

- ListHostedZonesByNameWithContext		
- ListResourceRecordSetsPagesWithContext	

AZURE

- [(ZonesClient) List](https://godoc.org/github.com/Azure/azure-sdk-for-go/services/dns/mgmt/2017-10-01/dns#ZonesClient.List)

- [(RecordSetsClient)ListAllByDNSZone](https://godoc.org/github.com/Azure/azure-sdk-for-go/services/dns/mgmt/2017-10-01/dns#RecordSetsClient.ListAllByDNSZone)

Record types

Azure provides the following record types that will be supported as a part of this project

```go
const (
    A     RecordType = original.A
    AAAA  RecordType = original.AAAA
    CAA   RecordType = original.CAA
    CNAME RecordType = original.CNAME
    MX    RecordType = original.MX
    NS    RecordType = original.NS
    PTR   RecordType = original.PTR
    SOA   RecordType = original.SOA
    SRV   RecordType = original.SRV
    TXT   RecordType = original.TXT
)
```

### GCP DNS backend

- API Ref:  https://cloud.google.com/dns/docs/apis
- golang sdk: https://godoc.org/google.golang.org/api/dns/v1

- Listing resource records:  https://cloud.google.com/dns/docs/reference/v1/resourceRecordSets/list
  - [golang sdk method](https://godoc.org/google.golang.org/api/dns/v1#ResourceRecordSetsListCall.Do)

- Listing managed zone:  https://cloud.google.com/dns/docs/reference/v1/managedZones/list
  - [golang sdk method](https://godoc.org/google.golang.org/api/dns/v1#ManagedZonesListCall.Do)
