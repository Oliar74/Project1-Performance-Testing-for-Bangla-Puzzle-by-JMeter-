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

* Click =>Binaries
* =>apache-jmeter-5.5.zip and Unzip this file
* Open bin folder and click on jmeter.bat file
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
### Number of Threads 100 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|       ![image](https://github.com/user-attachments/assets/43c33772-1fc9-4811-a363-910f9c50aec2) | ![image](https://github.com/user-attachments/assets/3c9023ce-7a64-4c73-9e86-868a1cc2ae9e) |

### Number of Threads 200 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|       ![image](https://github.com/user-attachments/assets/160b23e3-1859-41c4-8429-d778f9a71b6c) | ![image](https://github.com/user-attachments/assets/0b26fa2c-9415-4a18-8d65-f245bef5825c) |

### Number of Threads 400 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/13d97c87-a0ad-442f-b3d2-aeff5e557f8d) | ![image](https://github.com/user-attachments/assets/9a4d06dc-c06a-4209-b350-8bed1876c446) |

### Number of Threads 800 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/1892efad-b825-4ba9-a788-acd023f246bb) | ![image](https://github.com/user-attachments/assets/90063532-a6ff-43f9-b191-eabe6647bc9c) |

### Number of Threads 1000 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/6c6991c5-5c51-4b59-9725-08c6aa20612c) | ![image](https://github.com/user-attachments/assets/61381449-21e5-4c3b-ad3b-1be3f3e6411e) |


# Stress Testing
Stress Testing is a type of software testing that evaluates how the software responds under extreme conditions. It verifies how robust a system will be, and its response capabilities and error handling when it is subjected to conditions where its normal functioning can be compromised.

## Number of Threads 1200 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/55b5b16f-a246-4b4c-961b-ebba4a786cc1)| ![image](https://github.com/user-attachments/assets/47d228e3-5784-4d34-ae23-3398994a9f27) |

# Spike Testing
Spike testing is a type of performance testing where the demand for an application is suddenly and drastically increased or decreased. Spike testing's objective is to ascertain how a software program will behave under highly variable traffic conditions.
## Number of Threads 1600 ; Ramp-Up Period 10s
| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/50edc361-57ca-4b84-ad09-5e3e420f2888) | ![image](https://github.com/user-attachments/assets/40150ca6-fa7d-46a1-8230-e42848f99260) |

# Endurance Testing
An application may be put through endurance testing to see if it can handle the processing load that will be placed on it over an extended period of time. Memory usage is tracked throughout endurance tests to identify potential issues.

## Start Threads count 2 ; Initial Delay 0s ; Start up Time 10s ; Hold load for 500s ; Shutdown Time 0s

| Requests Summary  | Errors   |
|-------------------|----------|
|  ![image](https://github.com/user-attachments/assets/b0598014-38d7-4bb4-bd32-3cde024c7845) | ![image](https://github.com/user-attachments/assets/14a73d48-c38b-446d-8204-6bc9b8e23855)|
