Deception Engineering: Uninstalled App Canary
======================

Prior Work
-------------

This builds on the deception engineering work around Windows Service Canaries
https://research.nccgroup.com/2021/03/04/deception-engineering-exploring-the-use-of-windows-service-canaries-against-ransomware/

Thesis
-------------
Certain threat actors uninstall a number of products prior to dropping later stages. We deploy a number of canary apps which fire when uinstalled with relevant names.

Crypto Miner Tradecraft
-------------
During the Microsoft Exchange wars of 2021 we observed the following tradcraft used by a threat actor

```
cmd /c start /b wmic.exe product where "name like '%Eset%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%%Kaspersky%%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%avast%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%avp%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%Security%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%AntiVirus%'" call uninstall /nointeractive
cmd /c start /b wmic.exe product where "name like '%Norton Security%'" call uninstall /nointeractive
```

Configuring
-------------
Edit Security.vdproj and replace REPLACMEE in "Arguments" = "8:REPLACEME.canarytokens.com"

https://github.com/nccgroup/UninstalledAppCanary/blob/main/Security/Security.vdproj#L69
