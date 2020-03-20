---

copyright:
  years: 2018, 2020
lastupdated: "2020-03-20"

keywords: "virtual servers, {{site.data.keyword.vsi_is_short}}, getting started, virtual private cloud, virtual machines, compute, instance, generation 1"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:external: target="_blank" .external}

# Suspend billing
{: #suspend-billing}

When you power off an instance, you don't accrue costs for certain compute resources. Billing stops automatically when you stop the instance. The suspend billing feature helps you reduce cost and prevents you from having to re-create an instance when you need its resources again.

In situations where you want to scale your infrastructure up and down in response to workload needs, you can use the suspend billing feature as a faster alternative to creating and deleting instances.
{:tip}

## Billing details
{: #billing-details}

It's important to understand what costs stop accruing and what costs persist when your virtual server instance is powered off.

Billing is suspended only when you power off your virtual server instance through the IBM Cloud console, CLI, or API. If you power off your virtual server instance directly through the OS, billing isn't suspended for that instance.
{:note}

Review the following table for details on how suspend billing impacts various resource charges.

| Resource                      | Billing stopped   | Billing persists |
| ----------------------------- | ----------------- | ---------------- |
| vCPU                          |          X        |                  |
| RAM                           |          X        |                  |
| Bandwidth upgrades            |          X        |                  |
| Operating system licenses     |          X        |                  |
| Floating IPs, Load balancers, or other attached networking offerings |                   |         X        |
| Storage                       |                   |         X        |
{: caption="Table 6. Resource billing details" caption-side="top"}   

Usage times are calculated per second, for both the in use time and suspended time of your virtual server instance. Even if you never initiate the suspend billing feature by powering off your instance, the billing is calculated per second of the instance's lifecycle.
{:note}


### Suspend billing and sustained usage discounts
{: #suspend-billing-and-sustained-usage-discounts}

For sustained usage discounts, a suspended image picks up where it left off on the discount tier. In other words, a usage discount applies only to the time the image is in use, not to the time the image was suspended.

### Minimum usage charge
{: #minimum-usage-charge}

Virtual server instances have a minimum usage charge per month. If usage is greater than 25% in the billing cycle, you're billed for the actual usage. If usage is less than 25% of the time it existed in the billing cycle, then the minimum charge of 25% applies.

For example, let's say you have an instance running for an entire billing cycle (720 hours). Of that time, the instance was suspended for 577 hours and running for 143 hours. The instance is charged for 180 hours (the minimum of the available hours in that billing period).  

However, let's say you had an instance that was both created and stopped within a billing cycle that lasted for 400 hours total. Of that time, the instance was suspended for 120 hours and ran for 280 hours. The instance would be charged for its usage of 280 hours.

### Billing invoice
{: #billing-invoice}

When you suspend billing on a virtual server, you'll see a few changes in your billing invoice. The relevant charges now appear as usage-based details. For example, you might see the following additions that reflect hours available, hours used, and total number of hours charged:

```
Computing instance usage...
RAM usage...
Operating system usage...
```
{:screen}

## Resource details
{: #resource-details}

### Storage
{: #suspend-billing-storage}

When you suspend billing on a virtual server instance, the associated storage persists, but you can't access data while the virtual server instance is powered off. When you resume billing on the instance, you can then access your data and normal billing begins again.

### IP addresses
{: #suspend-billing-ip-addresses}

All network configurations and IPs (private IPs from the subnet range) remain unchanged while the instance is suspended.

You can view whether your device is stopped on the instance details page. To see when the status changed, click **Activity** in the navigation pane.

### Limitations
{: #suspend-billing-limitations}

Suspended virtual servers will continue to count towards your account-wide device quota.

