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
This document explains how to run a performance test with JMeter against the banglapuzzle.com website. Here tested for two major APIs; One is the Home Page and the other is the Contact page. We record the history by using Blazemeter and using it in Jmeter. It was tested on various Threads(users). Then we analyze those reports and make a final report as the performance of this site [Bangla Puzzle](#banglapuzzle.com)

# My Project

- [Load Testing Report](#load-testing-report)
- [Load Testing Report](##load-testing-report1)
# Load Testing Report
## Load Testing Report1
[Section Name](#section-name)
```
oliar rahman
```
# My Project



## Introduction

Introduction text here.

## Installation

### Requirements

List of requirements.

### Steps

Installation steps.

## Usage

### Command Line

How to use the command line interface.

### Python API

How to use the Python API.

## License

License details.
