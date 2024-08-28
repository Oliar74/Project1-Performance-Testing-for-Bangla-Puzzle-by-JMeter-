# Performance Testing for Bangla Puzzle Website by using JMeter
Performance Testing for Bangla Puzzle Website's Home Page &amp; Contact Page by using JMeter
## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
  - [Requirements](#requirements)
  - [Steps](#steps)
- [Usage](#usage)
  - [Command Line](#command-line)
  - [Python API](#python-api)
- [License](#license)
# Load Testing Report

| Concurrent Request   | Loop Count   | Avg TPS for Totla Sample | Error Rate% | Total Concurrent API Request |
|----------------------|--------------|--------------------------|-------------|------------------------------|
|       100            |       10     |            0.033         |      0%     |           58                 |
|       200            |       10     |            1.30          |      0%     |           138                |
|       400            |       10     |            2.5           |      0%     |           400                |
|       800            |       10     |            6             |      0%     |           800                |
|      1000            |       10     |            7             |   0.70%     |           933                |
|      1200            |       10     |            5.9           |   6.33%     |           1124               |
|      1600            |       10     |            6             |   21.0%     |           1264               |


## Summary
- While executing 1000 concurrent requests, 933 requests got connection timeout and the error rate is 0.70%.
- Server can handle almost concurrent 800 API calls with almost zero (0) error rate.

# Introduction
This document explains how to run a performance test with JMeter against the banglapuzzle.com website. Here tested for two major APIs; One is the Home Page and the other is the Contact page. We collect the API by using Blazemeter and using it in Jmeter. It was tested on various Threads(users). Then we analyze those reports and make a final report as the performance of this site [Bangla Puzzle](#banglapuzzle.com)

# Installation
### Java
https://www.oracle.com/java/technologies/downloads/

### JMeter
https://jmeter.apache.org/download_jmeter.cgi

Click =>Binaries
=>apache-jmeter-5.5.zip

### We use BlazeMeter to generate JMX files
https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en

# Prerequisites
- As of JMeter 4.0, Java 8 and above are supported.
- We suggest a multicore CPU with Core i5 or more.
- Memory 16GB RAM is a good value.

# Elements of a minimal test plan
1. Thread Group

2. The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

3. HTTP Request Default (Configuration Element)

4. HTTP Request (Sampler)

5. Summary Report (Listener)

# Test Plan

Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the jMeter version you are using)

* Name: Users
* Number of Threads (users): 100 to 1600
* Ramp-Up Period (in seconds): 10
* Loop Count: 1
  * The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  * All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  * Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  * The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.
    
# Collection of API
* Run BlazeMeter
* Collect Frequently used API
* Save JMX file then paste => apache-jmeter-5.5\bin

  ## List of API
  * https://www.banglapuzzle.com/
  * https://www.banglapuzzle.com/contact/
  
  ## Load the JMeter Script
  * File > Open (CTRL + O)
  * Locate the "project1(Bangla-Puzzle).jmx" file contained on this repo
  * Continue open Test100project1(Bangla-Puzzle).jmx to Test800project1(Bangla-Puzzle).jmx
  * Open those file
  * The Test Plan will be loaded
  * Download Test-Plan in several time to given Thread Group>>Number of Threads(user), Rampup-up-period(second)
![image](https://github.com/user-attachments/assets/17cdd8f3-fad8-4baa-bc3f-fc420ca2a784)

# Test execution (from the Terminal)
* JMeter should be initialized in non-GUI mode.
* Make a report folder in the bin folder.
* Run Command in jmeter\bin folder.

## Make jtl file
```
jmeter -n -t Test100project1(Bangla-Puzzle).jmx -l report\Test100project1(Bangla-Puzzle).jtl
```
  * n: non GUI mode
  * t: test plan to execute
  * l: output file with results
##### Then continue to upgrade Threads(100 to 1600) by keeping Ramp-up Same.

![image](https://github.com/user-attachments/assets/abc63b96-5091-4d3d-8d33-872892986801)

After completing this command You will get a .jtl file in that specific folder(report)
![image](https://github.com/user-attachments/assets/00da7f68-180f-4d41-83ef-12629431b311)

## Make html file
```
jmeter -g report\Test100project1(Bangla-Puzzle).jtl -o report\Test100project1(Bangla-Puzzle).html
```
  * g: jtl results file
  * o: path to output folder

![image](https://github.com/user-attachments/assets/0170e509-d4f4-4656-b444-eb38a4df7476)
![image](https://github.com/user-attachments/assets/f8cb6e48-d0a3-476a-a28e-b7ee49c2830f)

# HTML Report
### Number of Threads 1 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|       ![image](https://github.com/user-attachments/assets/43c33772-1fc9-4811-a363-910f9c50aec2) | ![image](https://github.com/user-attachments/assets/3c9023ce-7a64-4c73-9e86-868a1cc2ae9e) |



