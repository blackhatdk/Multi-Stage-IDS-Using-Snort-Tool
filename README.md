# MUTLI STAGE IDS USING SNORT TOOL

In the rapidly evolving landscape of cybersecurity, a robust intrusion detection system (IDS) is paramount to safeguard network infrastructures against a myriad of threats. Our proposed multi-stage IDS, leveraging the Snort tool, offers a comprehensive solution to bolster network security. The IDS comprises two distinct phases: initially, Snort serves as a frontline defense, swiftly identifying known attack methods and suspected fraudulent activities through pre-defined signatures, providing rapid detection and mitigation of recognized threats. Subsequently, the IDS emphasizes anomaly detection to complement Snort's capabilities, establishing a baseline of normal network behavior and identifying deviations indicative of potential intrusions or novel attack patterns. Through the integration of both signature-based and anomaly detection methodologies, our multi-stage IDS provides a robust defense mechanism against a diverse range of cyber threats, enhancing the overall security posture of networks and empowering organizations to effectively mitigate emerging risks.

## **Background**
### **Intrusion Detection Systems, Firewalls, and Network Intrusion Detection Systems**

- An **IDS**, or Intrusion Detection System, reads logs in real time and notifies admins when suspicious activity is spotted. 
- **Firewalls** are pieces of hardware or software that protect networks by deciding which packets go in and out of a network. Firewalls DON'T understand the data inside the packets, for the most part - they filter traffic based on trusted/untrusted hosts.
- IDS' generate more logs than firewalls do. For example, Snort, an IDS, can log alerts, PCAPs, and dropped packets. 
- An IDS installed in front of a network is called a **Network Intrusion Detection System**.

### **Snort**
- Snort is a NIDS and intrusion prevention system that acts similar to a firewall by reading incoming packets, scanning them for unique signatures, and triggering rules if the packets contain a certain signature.
- When a rule in Snort in triggered, the program may fire an alert, log a packet, save a packet, drop a packet, or some combination of all of these things.

### **Reading Snort Logs**
- Reading log files can be an extremely inefficient task for an analyst to perform manually.
- Instead, SIEMs are used to view and analyze the potential thousands of packets that can be transferred across a network.
- SIEMs like Splunk or web apps for network security monitoring like Snorby can be used to interface with Snort in order to simplify logs and alerts.
- Snort has a lot of deep capabilities: can be used as a packet sniffer, a packet logger, or an intrusion detection system.
- There's more theory behind how Snort works, but having a basic understanding of how to run it from the command line will help you do 2 things:
1. Identify suspcious activity in packet captures
2. Quickly test new configurations

## **Objective**
- Interpret premade IDS rules
- Configure Snort thorugh its config file and create custom rules
- Generate network traffic logs and suspicious activity alerts with Snort
- Create a custom rule to catch ICMP traffic
- Simulate an attack in the VM by using Nmap in Kali
- Run a full port scan and SMB attack

## **Process**
- In this project, we'll be looking at Snort from the CLI in Ubuntu Linux. To check if you already have Snort installed, use the command `Snort -V`.
- If Snort isn't already installed, do so by performing `sudo apt-get install snort`.
- In the terminal, run ifconfig to find out the name of your interface and your IP address
- To access the main configuration file for snort, run `sudo gedit /etc/snort/snort.conf` and validate with your password.
- To gain a better understanding of how these rules work, run `sudo snort -T -c /etc/snort/snort.conf -i [interface]`. Doing this will allow you to test and validate your Snort configuration. If they aren't set, you will have to examine the .conf file and edit it.
- Now enter `sudo snort -A console -q -u snort -g snort -c /etc/snort/snort.conf [interface]` in order to start monitoring against cyberattacks.
- Now that monitoring is enabled on the Ubuntu system, you'll want to head over to a Kali Linux box. 
- Run `Nmap [IP address of Ubuntu box]` to perform a scan against the target IP. 
- Now, if you switch back to Snort, you will see information coming in. For example, you will now see "SNMP request", which is classified as an Attempted Info Leak against the OS. 
