---
{"dg-publish":true,"permalink":"/ids-evasion-dos/"}
---


# Denial-of-Service (DoS) Attack

Multiple types of **Denial-of-Service (DoS)** attacks can target an IDS (Intrusion Detection System). The attacker identifies a point of network processing that requires the allocation of a resource, which leads to a condition where the resource is consumed entirely, preventing the IDS from functioning properly. The resources affected by the attacker include:

- **CPU cycles**
- **Memory**
- **Disk space**
- **Network bandwidth**

## Targeting CPU Resources

Attackers often target the **CPU capabilities** of the IDS. The IDS requires CPU resources to read packets, detect the purpose of those packets, and compare them with saved network states. This requires significant processing power. The attacker can identify the most computationally expensive network processing tasks and compel the IDS to perform useless work, overwhelming its CPU.

## Targeting Memory Resources

IDS requires memory for various tasks such as:

- Generating pattern matches
- Storing TCP connections
- Maintaining reassembly queues
- Producing buffers for data

Initially, the system allocates memory to read the incoming packets. The attacker can force the IDS to allocate memory for meaningless operations, consuming all the available memory and rendering the IDS ineffective.

## Targeting Disk Space

In some cases, the IDS stores activity logs on disk. These logs can quickly occupy most of the available disk space. Since most computers have limited disk space, the attacker can overload the IDS by creating and storing a large number of useless events. This prevents the IDS from storing valid events and renders it useless in terms of security monitoring.

## Targeting Network Bandwidth

Network IDS systems monitor network traffic and analyze packets sent across the network. The attacker can overload the network with meaningless information, preventing the IDS from processing legitimate traffic. This overload makes it impossible for the IDS to keep up with the network activity.

## Centralized Logging Servers

Many IDS solutions use **centralized logging servers** to store alert data. These central servers aggregate the data from multiple IDS devices for analysis. However, if an attacker knows the IP address of the centralized logging server, they can launch a DoS attack against it. This can:

- Slow down the server
- Crash the server, leading to the loss of critical alert data

Once the server is shut down, attacks can go unnoticed because the alerts are no longer logged, leaving the network unmonitored.

## Impact of DoS Attacks on IDS

Using DoS attacks to target IDS can have several impacts:

- **Locking up the device**: The IDS becomes unresponsive and unable to process traffic.
- **Preventing personnel from investigating alarms**: With the IDS unable to function properly, response teams cannot investigate suspicious activities.
- **Overwhelming management systems**: Too many alarms are triggered, exceeding the capacity of management systems (e.g., databases, alert management platforms).
- **Filling up disk space**: The IDS runs out of disk space, preventing legitimate attacks from being logged.
- **Consuming processing power**: The IDS's processing power is consumed by pointless tasks, allowing real attacks to bypass detection.

