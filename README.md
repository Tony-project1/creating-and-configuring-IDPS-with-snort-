# Solving the Northbridge Fintech Security Challenges Through SOC Analysis

This project focuses on identifying and addressing network security vulnerabilities within a simulated financial organization, Northbridge Fintech. It demonstrates the implementation of **pfSense Firewall, Snort Intrusion Detection and Prevention System (IDPS), network segmentation, and Wazuh SIEM** to improve network visibility, detect suspicious activities, and strengthen organizational security.

## Table of Contents

- Project Overview
- Network Topology
- Tools and Technologies
- Configuration Steps
- Results and Findings
- Author

## Project Overview

Northbridge Fintech is a simulated financial organization with approximately 100 employees handling confidential customer financial information across its internal network. The organization experienced unusual login patterns that indicated potential unauthorized access.

The primary security challenges identified included:

- Absence of properly configured perimeter firewall protection.
- Lack of an Intrusion Detection and Prevention System (IDPS).
- Insufficient network monitoring and security visibility.
- Potential unauthorized access to internal systems.
- Risk of lateral movement and unauthorized data exfiltration.
- Lack of centralized security log monitoring.

As a **Junior SOC Analyst**, I was tasked with analyzing network traffic, implementing essential network security controls, investigating suspicious activities, and recommending security improvements.

The major objectives of this project were:

- Implement network segmentation to isolate internal hosts from public-facing systems.
- Configure pfSense as the network firewall.
- Deploy and configure Snort as the IDPS.
- Implement least-privilege firewall rules.
- Block suspected malicious IP addresses.
- Integrate firewall and Snort security logs with Wazuh SIEM.
- Establish centralized security monitoring for improved threat detection and investigation.

## Network Topology

The project was implemented in a virtualized laboratory environment using VMware.

The network environment consisted of the following virtual machines and security components:

- **Kali Linux:** Used as the security testing machine and for accessing the pfSense and Snort web interfaces.
- **pfSense Firewall:** Used to manage network traffic, implement firewall rules, create network interfaces, and enforce network segmentation.
- **Snort IDPS:** Deployed on pfSense to monitor network traffic, detect suspicious activities, and provide intrusion prevention capabilities.
- **Ubuntu Linux:** Used as the internal host and endpoint for network connectivity and SSH testing.
- **Wazuh SIEM:** Used for centralized collection and monitoring of firewall logs and Snort security alerts.

### Network Segmentation

A new network interface, `em2`, was created to support network segmentation.

| Network Component    | Configuration    |
| -------------------- | ---------------- |
| Firewall             | pfSense          |
| New interface        | `em2`            |
| Interface IP address | `192.168.2.1/24` |
| Security monitoring  | Snort IDPS       |
| Centralized SIEM     | Wazuh            |
| Testing machine      | Kali Linux       |
| Internal endpoint    | Ubuntu Linux     |

The network segmentation approach was intended to separate internal hosts from public-facing systems through a Demilitarized Zone (DMZ).

The objective was to restrict unnecessary communication between network segments and reduce the possibility of lateral movement in the event of a security breach.

## Tools and Technologies

The following tools and technologies were used in this project:

- **VMware Workstation:** Virtualization platform for hosting the laboratory environment.
- **pfSense:** Open-source firewall and network security platform.
- **Snort:** Intrusion Detection and Prevention System (IDPS) for network traffic inspection.
- **Wazuh SIEM:** Security Information and Event Management platform for centralized log collection and security monitoring.
- **Kali Linux:** Security testing and network administration environment.
- **Ubuntu Linux:** Internal endpoint used for network connectivity and SSH testing.
- **SSH:** Secure Shell protocol used to test remote connectivity between systems.
- **ICMP:** Used to test network connectivity through ping requests and responses.
- **IPv4/IPv6:** Network addressing and firewall rule configuration.
- **Firewall Aliases:** Used to group and manage IP addresses for blocking suspected malicious sources.

## Configuration Steps

### 1. Installation and Configuration of Snort IDPS

1. Accessed the pfSense web interface through the Kali Linux browser.
2. Navigated to **System > Package Manager > Available Packages**.
3. Searched for the Snort IDPS package.
4. Installed the Snort package on pfSense.
5. Configured Snort according to the official documentation.
6. Added Snort to the LAN interface.
7. Started the Snort service.
8. Configured the available WAN and LAN monitoring rules.
9. Used Snort to identify suspicious network activities and manage suspected malicious IP addresses.

Official documentation: [Netgate Snort Package Setup Guide](https://docs.netgate.com/pfsense/en/latest/packages/snort/setup.html)

### 2. Implementation of Network Segmentation

1. Accessed the pfSense firewall configuration interface.
2. Navigated to the interface configuration section.
3. Created a new network interface identified as `em2`.
4. Assigned the IP address `192.168.2.1/24` to the new interface.
5. Established the network segmentation configuration to separate internal hosts from public-facing systems.
6. Planned the use of the DMZ interface to isolate the Kali Linux virtual machine from the internal network.

### 3. Implementation of Least-Privilege Firewall Rules

1. Accessed the firewall rules configuration section in pfSense.
2. Created firewall rules to permit authorized traffic from the LAN to the DMZ.
3. Restricted traffic originating from the DMZ to the LAN.
4. Reviewed the available IPv4 and IPv6 firewall rule configurations.
5. Applied traffic restrictions to improve network isolation and reduce unauthorized access between network segments.

### 4. Blocking Suspected Malicious IP Addresses

1. Navigated to the **Firewall > Aliases** section in pfSense.
2. Created and configured firewall aliases for suspected malicious IP addresses.
3. Added the IP addresses to the appropriate aliases.
4. Used the firewall configuration to block the identified IP addresses.
5. Improved network access control by restricting communication with suspected malicious sources.

### 5. Integration of pfSense and Snort with Wazuh SIEM

1. Configured the security monitoring environment to collect firewall and Snort security logs.
2. Established centralized log collection through Wazuh.
3. Verified the collection of firewall connection logs.
4. Verified that Snort security alerts were being forwarded to the Wazuh monitoring environment.
5. Observed the collected security events through the Wazuh SIEM dashboard.

### 6. Network Connectivity and SSH Testing

1. Used Kali Linux to initiate network connectivity tests against the Ubuntu virtual machine.
2. Performed ICMP echo requests and observed the corresponding responses.
3. Initiated SSH connectivity testing between Kali Linux and Ubuntu.
4. Used the testing process to examine network communication and security monitoring visibility.
5. Observed the available firewall and Snort events through the centralized Wazuh dashboard.

## Results and Findings

The project demonstrated the implementation of essential network security controls and centralized security monitoring within the Northbridge Fintech virtual laboratory.

The following results and findings were documented:

- **Firewall Implementation:** Successfully deployed pfSense as the firewall for managing network traffic and enforcing access restrictions.
- **Snort IDPS Deployment:** Installed and configured Snort on pfSense and attached it to the LAN interface for network traffic monitoring.
- **Network Segmentation:** Created a new network interface, `em2`, with the IP address `192.168.2.1/24` to support network isolation.
- **Least-Privilege Access Control:** Configured firewall rules to permit LAN-to-DMZ communication while restricting DMZ-to-LAN traffic.
- **Malicious IP Blocking:** Used firewall aliases to identify and block selected suspected malicious IP addresses.
- **Centralized Security Monitoring:** Successfully integrated pfSense firewall connection logs and Snort security alerts into Wazuh SIEM.
- **Network Connectivity Verification:** Observed ICMP echo requests and responses, demonstrating network connectivity and security event visibility.
- **Security Visibility:** Established Wazuh as a centralized monitoring platform for reviewing firewall and Snort security events.

### Security Recommendations

Based on the identified security gaps and the implemented controls, the following improvements are recommended:

- Enable and verify Snort inline IPS blocking mode to strengthen active intrusion prevention.
- Maintain strict least-privilege firewall policies across all network interfaces.
- Regularly review Snort alerts and firewall logs for suspicious activities.
- Monitor authentication events to identify unauthorized login attempts.
- Conduct periodic vulnerability assessments and network security testing.
- Maintain centralized security monitoring through Wazuh.
- Regularly update firewall rules, Snort signatures, and security monitoring components.
- Develop an incident response and recovery plan to minimize the impact of security breaches.

## Author

**Aleke Anthony**

Cybersecurity Analyst | SOC Analyst

Port Harcourt, Rivers State, Nigeria

**Areas of Interest:**

- Security Operations Center (SOC) Analysis
- Security Information and Event Management (SIEM)
- Intrusion Detection and Prevention Systems (IDPS)
- Network Security and Firewall Administration
- Threat Detection and Incident Response
- Linux System Administration

**GitHub:** http://github.com/Tony-project1

**Email:** http://tonylouis128@gmail.com

Separate confirmed results from planned steps
