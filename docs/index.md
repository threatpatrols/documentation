---
title: Documentation
---

# Documentation - ThreatPatrols.com

## Threat Management
The Threat Patrols API provides the core Threat Patrols platform functionality.  Customers can work with the 
API directly, or have the Threat Patrols team operate the platform for you as a managed cyber threat landscape 
service. 

#### Looking for the API documentation?

Our API documentation is not (yet) public.  We are working hard on getting this sorted out and expect we'll 
make it happen at the same time we publish the `tpcli` command line interface tool since these are closely 
related.

Users with authenticated access to the API are able to access the automatically generated Swagger-UI documentation
directly from https://api.threatpatrols.com


## System Status
 - Threat Patrols Services: [https://status.threatpatrols.com](https://status.threatpatrols.com){target=_blank}
 - Threat Patrols Packages: [https://status.threatpatrols.com/status/package-status](https://status.threatpatrols.com/status/package-status){target=_blank}


## Security.txt
We believe quick easy security contact is an important part of cyber-security operations.  We
like the [`security.txt`](https://securitytxt.org/) RFC9116 proposal and maintain 
a `.well-known/security.txt` HTTP record.

 - HTTP: [https://www.threatpatrols.com/.well-known/security.txt](https://www.threatpatrols.com/.well-known/security.txt)

Additionally, we maintain a `_security` DNS TXT record that references the same HTTP record.

 - DNS TXT: `_security.threatpatrols.com`


## OPNsense Resources
Threat Patrols really loves OPNsense, and we are proud to support the ecosystem with
resources for the OPNsense community.  We currently provide:

 - a public Cloudflare CDN backed mirror; 
 - a package distribution repo; 
 - some awesome OPNsense plugins, Autossh; ConfigSync and MultiCLOUDsense

Find more here: [/opnsense](https://documentation.threatpatrols.com/opnsense/)
