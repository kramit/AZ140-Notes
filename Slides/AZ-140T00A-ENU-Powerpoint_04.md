# AZ-140T00A-ENU-Powerpoint_04.pptx

## Slide 4-5: Azure Virtual Desktop network connectivity
- Azure Virtual Desktop network topology and connectivity design guidance: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/azure-virtual-desktop/eslz-network-topology-and-connectivity

Instructor Notes: AVD connectivity overview  
Overview: Network design impacts latency, security, and reliability for AVD sessions.  
Key points:
- Place session hosts near users to reduce RTT.
- Use VPN or ExpressRoute for private connectivity.
- Avoid forced tunneling for performance-sensitive RDP traffic.

- About VPN Gateway: https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways

Instructor Notes: VPN connectivity options  
Overview: VPN Gateway enables point-to-site and site-to-site connectivity over the internet.  
Key points:
- P2S is per-client; S2S connects whole networks.
- Encrypted tunnels over the public internet.
- Common for hybrid connectivity when ExpressRoute isn’t required.

- ExpressRoute introduction: https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction

Instructor Notes: ExpressRoute  
Overview: ExpressRoute provides private, high-throughput connectivity to Azure.  
Key points:
- Traffic stays off the public internet.
- Lower, more consistent latency than internet VPN.
- Used for enterprise-grade hybrid access.

## Slide 6-8: Analyze connection quality
- Analyze connection quality in Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/connection-latency

Instructor Notes: Connection quality analysis  
Overview: AVD provides network data (bandwidth, RTT) for troubleshooting user experience.  
Key points:
- NetworkData table includes estimated bandwidth and RTT.
- Correlation IDs tie logs back to specific user sessions.
- Data is collected periodically during active sessions.

- Send diagnostic data to Log Analytics for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/diagnostics-log-analytics

Instructor Notes: Diagnostics to Log Analytics  
Overview: AVD diagnostics send connection and session data to Log Analytics for analysis.  
Key points:
- Enables centralized monitoring and alerting.
- Includes connection, network, and agent health logs.
- Required for AVD Insights and deeper troubleshooting.

## Slide 9-11: RDP bandwidth requirements
- Remote Desktop Protocol (RDP) bandwidth requirements: https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth

Instructor Notes: RDP bandwidth planning  
Overview: RDP adapts to conditions, but bandwidth needs grow with graphics and video.  
Key points:
- Graphics workloads consume most bandwidth.
- Resolution and frame rate drive usage.
- Use guidance as estimates, then validate in pilot.

## Slide 12-20: RDP Shortpath
- RDP Shortpath for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-shortpath

Instructor Notes: RDP Shortpath basics  
Overview: Shortpath creates a UDP-based transport for better latency and reliability.  
Key points:
- Works for managed networks (VPN/ExpressRoute) and public networks.
- STUN provides direct UDP; TURN relays when direct is blocked.
- Falls back to TCP reverse connect if UDP isn’t available.

- Configure RDP Shortpath for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-rdp-shortpath

Instructor Notes: Enabling Shortpath  
Overview: Shortpath is configured on session hosts and can be managed via GPO or Intune.  
Key points:
- Enable appropriate Shortpath types per network scenario.
- Configure ports and listener settings as required.
- Restart session hosts after policy changes.

## Slide 21-22: Quality of Service (QoS)
- Implement Quality of Service (QoS) for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-quality-of-service-qos

Instructor Notes: QoS for RDP traffic  
Overview: QoS prioritizes RDP traffic to reduce jitter, loss, and latency.  
Key points:
- Requires RDP Shortpath for managed networks.
- Uses DSCP marking via Group Policy.
- Must be applied consistently across the network path.

## Slide 23-25: Azure Private Link for AVD
- Azure Private Link with Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/private-link-overview

Instructor Notes: Private Link workflows  
Overview: Private Link can route feed discovery, feed download, and host connections privately.  
Key points:
- Separate endpoints for global feed, workspace feed, and host pool connections.
- Only one global feed endpoint per deployment.
- Requires private DNS configuration.

- Set up Private Link with Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/private-link-setup

Instructor Notes: Private Link setup  
Overview: Private endpoints are created per workspace and host pool.  
Key points:
- Create endpoints for feed and connection sub-resources.
- Plan address space for endpoint growth.
- Validate endpoint connection states after creation.

## Slide 26-27: Azure Bastion
- What is Azure Bastion?: https://learn.microsoft.com/en-us/azure/bastion/bastion-overview

Instructor Notes: Azure Bastion  
Overview: Bastion provides secure RDP/SSH access without public IPs on VMs.  
Key points:
- Connects over TLS via Azure portal or native clients.
- Reduces exposure of RDP/SSH ports to the internet.
- Deployed in a dedicated Bastion subnet.

## Slide 28-29: Network monitoring and troubleshooting
- What is Azure Network Watcher?: https://learn.microsoft.com/en-us/azure/network-watcher/network-watcher-overview

Instructor Notes: Network Watcher  
Overview: Network Watcher offers monitoring, diagnostics, and traffic tools for IaaS networks.  
Key points:
- Includes topology view, connection monitor, and packet capture.
- Helps diagnose NSG, routing, and connectivity issues.
- Automatically enabled per region when VNets are created.

## Related
- [[AZ-140T00A-ENU-Powerpoint_04_Script]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_09]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_03]]
