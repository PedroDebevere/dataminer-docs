---
uid: Connecting_to_private_data_sources
description: To make sure DaaS can also access private data sources, a site-to-site VPN connection will need to be set up. 
---

# Connecting to private data sources with DaaS

If you are using a DaaS system, by default you will only be able to connect to data sources that can be accessed from dataminer.services over the internet. To make sure DaaS can also access private data sources, a **site-to-site VPN connection** will need to be set up. This will establish a secured connection between your DaaS system and your self-hosted network (which can be on-premises or hosted by the cloud provider of your choice).

## About the site-to-site VPN connection

To establish this connection, after you have followed the [procedure below](#establishing-the-site-to-site-vpn-connection), Skyline will enable an [Azure VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways) in the virtual network of your DaaS environment.

By default the [Generation 1 VPN Gateway SKU *VpnGw1AZ*](https://learn.microsoft.com/en-us/azure/vpn-gateway/about-gateway-skus) will be used. The "AZ" in this SKU refers to "Zone Redundant", which means it automatically distributes the gateway across multiple availability zones to enhance redundancy and fault tolerance. This setup ensures higher availability and resilience against zone-level failures. However, you can request a different SKU during the setup, and it is also possible to scale up to *VpnGw2AZ* and *VpnGw3AZ* (generation 1) later if necessary.

By default, the IKEv2 protocol will be used. IKEv1 is possible but not recommended.

If a [custom policy](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-compliance-crypto?WT.mc_id=Portal-Microsoft_Azure_HybridNetworking#ipsecike-policy-faq) is preferred, you can request this during the setup.

## Establishing the site-to-site VPN connection

> [!TIP]
> If you are not familiar with any of the terminology used in this section, please refer to [Azure VPN Gateway FAQ](https://docs.azure.cn/en-us/vpn-gateway/vpn-gateway-vpn-faq).

1. Make sure the following prerequisites are met:

   - You have configured a [supported VPN device](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices) for Skyline to connect to.

   - You have configured one of the [supported cryptographic algorithms and key strengths options](https://learn.microsoft.com/en-us/azure/vpn-gateway/ipsec-ike-policy-howto#cryptographic-algorithms--key-strengths).

1. Contact <daas@dataminer.services> to set up a site-to-site VPN connection.

   Provide the following information in your email:

   - The public IP of your VPN device.

   - A pre-shared key to use for the VPN connection.

   - The address space of the network(s) that should be reachable by your DaaS system.

   - If BGP should be enabled, the ASN and BGP peer IP address.

   - The preferred cryptographic algorithms and key strengths. We prefer to use the most secure and efficient settings that are available on your device.

      > [!NOTE]
      > The IPSec Phase 1 or Main Mode lifetime is fixed to 28800 seconds for Azure VPN Gateways.

   - Optionally, if the *VpnGw1AZ* [gateway SKU](https://learn.microsoft.com/en-us/azure/vpn-gateway/about-gateway-skus) does not meet your requirements, the required SKU.

   - Optionally, if you want a [custom policy](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-compliance-crypto?WT.mc_id=Portal-Microsoft_Azure_HybridNetworking#ipsecike-policy-faq) to be used, the required policy.

   - Any other information that might be relevant for your specific setup.

Once the VPN Gateway has been enabled, Skyline will provide you with the following information:

- The public IP of the Azure VPN Gateway.

- The DaaS address space (by default 172.23.0.0/16, but this can be different to prevent an overlap with your address space).

- The BGP ASN (if BGP is set)
