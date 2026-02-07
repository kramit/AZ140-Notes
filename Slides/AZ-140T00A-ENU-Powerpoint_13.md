# AZ-140T00A-ENU-Powerpoint_13.pptx

## Slide 4-7: Configure log collection and analysis (Diagnostics + Log Analytics)
- Send diagnostic data to Log Analytics for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/diagnostics-log-analytics
- Access Log Analytics workspaces: https://learn.microsoft.com/en-us/azure/virtual-desktop/diagnostics-log-analytics#how-to-access-log-analytics

Instructor Notes: Diagnostics and Log Analytics  
Overview: Enable diagnostics on AVD objects and route logs to Log Analytics for analysis.  
Key points:
- Enable diagnostics per host pool, app group, and workspace.
- Categories include Management Activities, Connections, Errors, and more.
- Log Analytics tables are prefixed with WVD.

## Slide 8-10: Monitor Azure Virtual Desktop by using Azure Monitor
- Enable Insights to monitor Azure Virtual Desktop (configuration workbook): https://learn.microsoft.com/en-us/azure/virtual-desktop/insights

Instructor Notes: Azure Monitor for AVD  
Overview: Use Azure Monitor and AVD Insights to view health, usage, and performance.  
Key points:
- Requires a dedicated Log Analytics workspace for session hosts.
- Collect diagnostics, performance counters, and Windows Event Logs.
- Insights hub provides host pool and session analytics.

## Slide 11-13: Customize Azure Monitor workbooks for AVD Insights
- Configuration workbook and diagnostic settings: https://learn.microsoft.com/en-us/azure/virtual-desktop/insights#set-up-the-configuration-workbook

Instructor Notes: Workbooks and DCR  
Overview: Workbooks guide setup and configure diagnostics and session host data.  
Key points:
- Enable diagnostics tables (Management, Feed, Connections, Errors, Checkpoints, HostRegistration, AgentHealthStatus).
- Use Azure Monitor Agent and Data Collection Rules (DCR) for session host metrics.
- Workbooks can be customized for environment-specific views.

## Slide 14-19: Monitor Azure Virtual Desktop by using Azure Advisor
- Azure Advisor recommendations for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/azure-advisor-recommendations
- Required URL list (for Advisor recommendation): https://learn.microsoft.com/en-us/azure/virtual-desktop/safe-url-list

Instructor Notes: Azure Advisor  
Overview: Advisor provides operational excellence and performance guidance for AVD.  
Key points:
- “No validation environment enabled” and “Not enough production environments” are common alerts.
- Use validation host pools to test updates safely.
- Ensure required URLs are unblocked for session host registration.

## Slide 20-22: Diagnose graphics performance issues
- Diagnose graphics performance issues in Remote Desktop (RemoteFX counters): https://learn.microsoft.com/en-us/azure/virtual-desktop/remotefx-graphics-performance-counters

Instructor Notes: Graphics counters  
Overview: Performance Monitor counters help pinpoint frame rate, stalls, and latency.  
Key points:
- Use qwinsta to find session name and counter instance.
- Check Output Frames/Second vs Input Frames/Second.
- Frames Skipped/Second counters identify server/network/client bottlenecks.

## Slide 23-24: Implement scaling plans in host pools
- Create and assign an autoscale scaling plan: https://learn.microsoft.com/en-us/azure/virtual-desktop/autoscale-create-assign-scaling-plan
- Autoscale scaling plans and scenarios: https://learn.microsoft.com/en-us/azure/virtual-desktop/autoscale-scenarios

Instructor Notes: Scaling plans  
Overview: Autoscale schedules power state changes for cost optimization.  
Key points:
- Requires RBAC role Desktop Virtualization Power On Off Contributor.
- Define ramp-up, peak, ramp-down, and off-peak schedules.
- Assign one scaling plan per host pool.

## Slide 25-26: Optimize capacity and performance
- Use Performance Diagnostics in Azure Monitor (VM diagnostics): https://learn.microsoft.com/en-us/azure/azure-monitor/vm/performance-diagnostics

Instructor Notes: Performance Diagnostics  
Overview: PerfInsights provides continuous and on-demand diagnostics on VMs.  
Key points:
- Continuous mode collects data every 5 seconds with insights every 5 minutes.
- On-demand mode provides deeper analysis for active issues.
- Reports are stored in a storage account for review.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_13_Script]]
- [[overview]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
