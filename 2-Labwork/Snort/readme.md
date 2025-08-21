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
