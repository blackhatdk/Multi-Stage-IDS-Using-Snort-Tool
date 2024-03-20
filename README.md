# MUTLI STAGE IDS USING SNORT TOOL

In the rapidly evolving landscape of cybersecurity, a robust intrusion detection system (IDS) is paramount to safeguard network infrastructures against a myriad of threats. Our proposed multi-stage IDS, leveraging the Snort tool, offers a comprehensive solution to bolster network security. The IDS comprises two distinct phases: initially, Snort serves as a frontline defense, swiftly identifying known attack methods and suspected fraudulent activities through pre-defined signatures, providing rapid detection and mitigation of recognized threats. Subsequently, the IDS emphasizes anomaly detection to complement Snort's capabilities, establishing a baseline of normal network behavior and identifying deviations indicative of potential intrusions or novel attack patterns. Through the integration of both signature-based and anomaly detection methodologies, our multi-stage IDS provides a robust defense mechanism against a diverse range of cyber threats, enhancing the overall security posture of networks and empowering organizations to effectively mitigate emerging risks.


# **Snort**

- Snort: Open-source Network Intrusion Detection and Prevention System (NIDS/IPS) developed by Sourcefire, now Cisco-owned.
- Functionality: Analyzes real-time network traffic against predefined rules or signatures.
- Purpose: Detects and prevents various network attacks and suspicious activities.
- Flexibility: Allows customization of rules to suit specific network security requirements.
- Modes: Operates in Sniffer, Packet Logger, and Network Intrusion Detection (NIDS) modes.
- Alerting: Generates alerts upon detecting matches between network traffic and rules, facilitating further analysis or action.
  
## **Reading Snort Logs**
- Reading log files can be an extremely inefficient task for an analyst to perform manually.
- Network security monitoring like Snort by can be used to interface with Snort in order to simplify logs and alerts.
- Snort has a lot of deep capabilities: can be used as a packet sniffer, a packet logger, or an intrusion detection system.
- There's more theory behind how Snort works, but having a basic understanding of how to run it from the command line will help you do 2 things:

     1. Identify suspcious activity in packet captures
     2. Quickly test new configurations

## **Objective**
- Interpret premade IDS rules
- Configure Snort thorugh its config file and create custom rules
- Generate network traffic logs and suspicious activity alerts with Snort
- Simulate an attack in the VM by using Nmap in Kali


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
