<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/NXDXYEt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A resource group was set up, and within it, two virtual machines were created: one running Microsoft 10 (Windows 10) and the other running Linux.
</p>
<br />

<p>
<img src="https://i.imgur.com/MhLVvuN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The following steps were taken:

Wireshark Installation: Wireshark was installed within the Windows 10 Virtual Machine.

Filtering ICMP Traffic: ICMP traffic was filtered in Wireshark.

Ping Ubuntu VM: The private IP address of the Ubuntu Virtual Machine was obtained, and ICMP (ping) traffic was initiated from the Windows 10 VM to the Ubuntu VM. The ping requests and replies were observed in Wireshark.

Ping Public Website: From the Windows 10 VM, PowerShell was used to ping a public website (www.google.com).

Perpetual Ping from Windows 10 to Ubuntu VM: A continuous (non-stop) ping was initiated from the Windows 10 VM to the Ubuntu VM.

Network Security Group Configuration: The Network Security Group on the Ubuntu VM was accessed, and incoming (inbound) ICMP traffic was disabled.

Observing ICMP Traffic: In the Windows 10 VM, ICMP traffic was observed both in Wireshark and through the command-line ping activity. Due to the Network Security Group configuration, the ping to the Ubuntu VM likely did not receive replies.

Re-enabling ICMP Traffic: The Network Security Group on the Ubuntu VM had its incoming (inbound) ICMP traffic re-enabled.

Observing ICMP Traffic (After Re-enabling): In the Windows 10 VM, ICMP traffic was observed in Wireshark, and the command-line ping activity was likely to receive replies again when pinging the Ubuntu VM.

These steps involved configuring and observing network activity and security settings between the Windows 10 and Ubuntu VMs, including ICMP traffic both within the local network and to external websites.
</p>
<br />

<p>
<img src="https://i.imgur.com/rofGSeS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, a filter was applied to capture only "SSH traffic." Subsequently, an SSH connection was established from the Windows 10 VM to the Ubuntu Virtual Machine using its private IP address. Various Linux commands like "ls," "pwd," and others were executed within the SSH session. While performing these actions, the SSH traffic was continually observed in Wireshark, reflecting the communication between the two virtual machines.

To exit the SSH connection, the command 'exit' was typed and followed by pressing the [Enter] key, terminating the SSH session.
</p>
<br />

<p>
<img src="https://i.imgur.com/0VkGQa8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, a filter was applied to capture only "DHCP traffic." Subsequently, from the Windows 10 VM, a new IP address was requested and obtained by executing the command "ipconfig /renew" in the command line. As a result of this action, DHCP traffic related to the IP address renewal process was observed in Wireshark, providing insight into the DHCP communication.
</p>
<br />

<p>
<img src="https://i.imgur.com/dl6ckxF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, a filter was applied to capture only "DNS traffic." Subsequently, within the Windows 10 VM's command line, the "nslookup" command was used to inquire about the IP addresses associated with "google.com" and "disney.com." As these DNS queries were executed, the DNS traffic was observed in Wireshark, providing insight into the DNS resolution process for these domain names.
</p>
<br />
