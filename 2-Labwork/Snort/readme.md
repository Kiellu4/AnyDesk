# Labwork Rubric 2 - Snort Installation #

**Individual/Group Members:** 
- **Author:** Ezekiel Mukhriz
- **Partner:** Muhammad Aabas
- **Semester:** Sem 4 / NWS
- **TTO:** Miss Dahlia

---

## Answer all questions: ##

### 1. Explain the basic requirement of the SNORT installation. You may use diagram/screenshot to support your explanation. ### 
= To install and configure Snort on OpenSUSE 15.4 within a VMWare virtual machine, the following are required:-

System Requirements:
- VMWare Workstation 17.5.0 (Virtualization Platform)
- Host OS: Kali Linux 2024.4
- Guest OS: OpenSUSE Leap 15.4
- Snort Version: 2.9.20
- DAQ Version: 2.0.7

Installation Steps:
1. Install Dependencies:
- sudo zypper install gcc gcc-c++ libpcap libpcap-devel libdnet-devel flex bison
2. Download and Install DAQ:
- wget https://www.snort.org/downloads/snort/daq-2.0.7.tar.gz
- tar -xzf daq-2.0.7.tar.gz
- cd daq-2.0.7
- ./configure && make && sudo make install
3. Download and Install Snort:
- wget https://www.snort.org/downloads/snort/snort-2.9.20.tar.gz
- tar -xzf snort-2.9.20.tar.gz
- cd snort-2.9.20
- ./configure --enable-sourcefire && make && sudo make install
4. Verify Installation:
- snort -V

### 2. Explain your expectation from this lab. What is your achievement before and after lab completion? ###
**Before the Lab:** Expected to learn how to install and configure Snort properly, create rules, and analyze network traffic.
**After the Lab:** Successfully installed Snort, created rules, detected attacks (ICMP, HTTP, SSH, Nmap, Hydra), and logged alerts.

### 3. Did you able to complete the lab successfully (YES/NO)? Explain why and how.  Demonstrate and explain the output you achieve from this lab. (Explanation at least in 10 points) ###
= Yes, the lab was completed successfully.
However, there were issues with alert logging initially, which were resolved by:
- Checking Snort Configuration: Ensuring output unified2 was set correctly in snort.conf.
- Verifying Permissions: Running Snort as snort user.
- Using the Correct Interface: snort -c /etc/snort/snort.conf -i eth0 -A console.

Demonstration output:
1. ICMP Attack Detected:
![Q3](Screenshots/icmp.png) 

2. HTTP Traffic Detected:
![Q3](Screenshots/HTTP.png) 

3. SSH Attempt Detected:
![Q3](Screenshots/SSH.png) 

4. Nmap Scan Detected:
![Q3](Screenshots/Nmap.png) 

5. Hydra Scan Detected:
![Q3](Screenshots/Hydra.png)  

### 4. Interpret the result and your findings? Your explanation may include the result of your SNORT and how you elaborate the findings. ###
- Snort detected attacks based on configured rules.
- Alert logging issues were due to output unified2 misconfiguration.
- Hydra brute force detected after 5 attempts in 60 seconds.
- Rules differentiate attacks by protocol, port, flags, and behaviour.
- tcpdump confirmed attack detection.
Rules that I put in ‘local.rules’:

📷 Screenshot:
![Q4](Screenshots/local_rules.png)  