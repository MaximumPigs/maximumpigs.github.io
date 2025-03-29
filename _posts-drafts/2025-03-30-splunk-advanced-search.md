---
layout: post
title: Splunk advanced search
categories: ["Cyber Security"]
tags: ["cyber-security", "siem", "splunk"]
author:
  - MaximumPigs
---

Intro

## How data is indexed

body

  ### TSIDX Files

  1) **Lexicon**  
  Explain what a lexicon is

  2) **Segmentation**  
  Explain how a Lexicon is created using Major and Minor breakers

  2) **Posting List**  
  Explain how a Posting List is used to find slices of data within the Journal

  ### Bloom Filter
  Explain how the bloom filter works


## How data is searched

body

  ### LISPY

  body

  ### TERM() directive

  body

  ### Walklex command

  body

  ### Tstats - PREFIX()

  body


## Practical examples

body

  ### Sysmon - Thinking in LISPY

  Image ParentImage

  DestinationPort

  ### IP Addresses - TERM()

  127.0.0.1

  ### Firewall Events - TERM()

  srcip=IP

  srcip="IP"

  ### WindowsEvent - PREFIX()

  PREFIX(eventcode=)

  ### Sysmon Process Creation - Walklex

  Subsearch Walklex pattern=\*term*

----

- [X] List Item
- [X] List Item
  - [X] Sub-List Item
  - [X] Sub-List Item

---

### Links and References

1. **AWS - (Amazon Web Services)**: [Amazon Web Services Official Site](https://aws.amazon.com/)

---

[1]: https://github.com/MaximumPigs/DetectionLab/tree/v0.1.0 "MaxiumumPigs DetectionLab Version 0.1.0"
