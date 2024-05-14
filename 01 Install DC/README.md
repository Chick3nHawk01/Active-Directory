# 01 Installing the Domain Controller

1. Use `sconfig` to:
    - Change the hostname
    - Change the IP address to static
    - Change the DNS server to our own IP address

2. Install the Active Directory Windows Feature

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```


```
Get-NetIPAddress
```

# Joining the Workstation to the Domain

* Make sure the Workstation's DNS address is our Domain Controller IP address otherwise it will not be able to complete the Domain Joining process

```
Get-DnsClientServerAddress
```

* If DNS IP address is not our Domain Controller's IP address

```
Set-DnsClientServerAddress -InterfaceIndex (Whichever your IP address is using for DNS) -ServerAddresses (Your DC IP Address)
```

```
Add-Computer -Domainname xyz.com -Credential xyz\Administrator -Force -Restart
```