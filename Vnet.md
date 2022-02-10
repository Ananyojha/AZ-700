- Azure VNets enable resources in Azure to securely communicate with each other, the internet, and on-premises networks

[MS LEARN](https://docs.microsoft.com/en-us/learn/modules/introduction-to-azure-virtual-networks/2-explore-azure-virtual-networks)

## Public IP

- Why Public IP?
> Public networks like the Internet communicate by using public IP addresses. Private networks like your Azure Virtual Network use private IP addresses, which are not routable on public networks

- WHY TALK TO INTERNET ? 
> public resources like web servers must be accessible from the internet.
Or you want to download something from Internet.

- HOW WE CAN ENABLE INTERNET COMMUNICATION WITH OUR VNET ?
> Use PUBLIC IP or NAT 

- A public IP address in Azure is dedicated to a specific resource. LIKE VM, AZURE LB 

- NAT `FOR ONLY OUTBOUND TRAFFIC TO INTERNET` -- network address translation services, where Azure dynamically assigns an available IP address that isn't dedicated to the resource.

**Public IP** 
Some of the resources you can associate a public IP address resource with:

- Virtual machine network interfaces
- Internet-facing load balancers
- VPN gateways
- Application gateways
- Azure Firewall

Public IP addresses are allocated from a range that's unique to each region in each Azure cloud. Public IP addresses can't be moved between regions; all IP addresses are region-specific



> 2 IP -- STATIC AND DYNAMIC

The dynamic IP address is allocated when you create or start a VM. The IP address is released when you stop or delete the VM. In each Azure region, public IP addresses are assigned from a unique pool of addresses. The default allocation method is dynamic.

Static IP doesn't change like for AD domain  controllers DNS servers 

*Standard SKU uses STATIC IP ONLY*

## AZURE DNS

**Considerations** - 
- The name of the zone must be unique within the resource group, and the zone must not exist already.
- The same zone name can be reused in a different resource group or a different Azure subscription.
- Where multiple zones share the same name, each instance is assigned different name server addresses.
- Root/Parent domain is registered at the registrar and pointed to Azure NS.
- Child domains are registered in AzureDNS directly.
 
📚 Note

You do not have to own a domain name to create a DNS zone with that domain name in Azure DNS. However, you do need to own the domain to configure the domain.

Each registrar has their own DNS management tools to change the name server records for a domain. In the registrar’s DNS management page, edit the NS records and replace the NS records with the ones Azure DNS created.

## Private DNS 

> Windows Server Active Directory domains, resolve DNS names between virtual networks. To cover these scenarios, Azure provides the ability for you to use your own DNS servers.

Doubt -- Access to the recursive resolvers in Azure is provided via the virtual IP 168.63.129.16.
 It's important to recognize that it's the Azure Resource name that is registered, not the name of the guest OS on the VM.

`Limitations of Internal DNS`

✓ Can't resolve across different VNets.
✓ Registers resource names, not guest OS names.
✓ Does not allow manual record creation.


DNS forwarding also enables DNS resolution between virtual networks and allows your on-premises machines to resolve Azure-provided host names.

![](https://docs.microsoft.com/en-us/learn/wwl-azure/introduction-to-azure-virtual-networks/media/inter-vnet-dns-812cc9a7.png)

**Azure Internal DNS** -- Any VM created in the VNet is registered in the internal DNS zone and gets a DNS domain name like myVM.internal.cloudapp.net.

### Azure Pvt DNS 

![](https://docs.microsoft.com/en-us/learn/wwl-azure/introduction-to-azure-virtual-networks/media/dns-zones-d964f066.png)

`name resolution for on prem + azure`
.
![](https://docs.microsoft.com/en-us/learn/wwl-azure/introduction-to-azure-virtual-networks/media/external-dns-fwd-7c81c29f.png)


### Vnet Peering 

When you Allow Gateway Transit the virtual network can communicate to resources outside the peering. For example, the subnet gateway could:

✓ Use a site-to-site VPN to connect to an on-premises network.
✓ Use a VNet-to-VNet connection to another virtual network.
✓ Use a point-to-site VPN to connect to a client

In these scenarios, gateway transit allows peered virtual networks to share the gateway and get access to resources. This means you do not need to deploy a VPN gateway in the peer virtual network.

The benefits of using a hub and spoke configuration include cost savings, overcoming subscription limits, and workload isolation.

[MS LEARN ABOUT UDR](https://docs.microsoft.com/en-us/learn/modules/introduction-to-azure-virtual-networks/9-implement-virtual-network-traffic-routing)
