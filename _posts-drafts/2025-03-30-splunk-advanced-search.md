---
layout: post
title: Splunk advanced search
categories: ["Cyber Security"]
tags: ["cyber-security", "siem", "splunk"]
author:
  - MaximumPigs
---

After stumbling accross a fantastic presentation named "Fields, Indexed Tokes, And You" by Martin Müller from Splunk .conf 2017, I've been diving down the rabit hole exploring the world of the splunk lexicon and how it can be leveraged to achieve insanely efficient queries.

I've done all the Splunk user training, and most of what follows in this post is covered in one course or another to some degree but not to the extent in which I believe they deserve.

I could certainly just post a link to Martin and others presentations and be done with it, but I would like to do something a little different in this post and give some real world examples of where I have personally put my newly gained knowledge to the test for some great results.

So, let's say you're a Splunk user. Why should you care about search efficiency? What difference does it make to you whether a search takes one second, or one minute? as long as you get the data you were looking for. The answer from a purely self-centred persoective, is employability. A large Splunk instance is an abolute beast which can cost upwards of several million dollars a year in licensing and infrastructure, and with large costs comes large pressure to reduce those costs. I've not met an organisation yet who hasn't been actively trying to squeeze more and more out of their Splunk instance without outlaying more money to expand it. Particularly for those in the Cyber Security field, Splunk Enterprise Security is heavy with scheduled searches and even moreso after adding a whole bunch of correlation searches running constantly, hunting for suspicious activity. By making those searches as efficient as possible, your instance will not only run faster but you can squeeze more out of it before the need to expand it. Not only will you make your Splunk admins happy, but when you show your executive team how you postponed the need to expand the Splunk instance - you'll be worth your weight in gold (or Splunk license costs) in their eyes.

Before we get into the examples, there are a few important concepts that need to be covered. After all, thinking about a search from the perspective of the lexicon requires a different approach to what you may be used to. We'll be focusing less on traditional search techniques such as field/value pairs and search time enrichments, and far more on the structure of the raw data and how it is indexed. I'll cover them lightly, but if you would like to dive down the rabit hole like I have then check out is  great presentation by Martin Müller:

- [Fields, Indexed Tokens, And You - Presentation - Martin Müller](https://www.youtube.com/watch?v=oZ-teiqqKB4)
- [Fields, Indexed Tokens, And You - Slides - Martin Müller](https://conf.splunk.com/files/2017/slides/)


## How data is indexed

Before we can start lexicon centric searching, we need to know what the lexicon is and how it's created. The intention here is to give you the knowledge to start recognising segments from raw events which will appear in the lexicon, as well as little bit about how Splunk uses these segments to return events from the index.

  ### TSIDX Files

  1) **Lexicon**  
  Explain what a lexicon is

  1) **Segmentation**  
  Explain how a Lexicon is created using Major and Minor breakers

  1) **Posting List**  
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


## Thinking about _raw

Stop looking at search time fields, start looking at _raw.

## Practical examples

body

  ### Sysmon - Thinking in terms of TERMS

  Image ParentImage (EventCode=1)

  TargetFilename (EventCode=11?)

  TargetObect (EventCode=12,13,14?)

  DestinationPort (EventCode=3)

  ### It was the best of TERMs, it was the blurst of TERMs.

  Venn Diagram

  Best:
  IP Addresses: 127.0.0.1
  AWS / Azure resources
  Registry Keys (Wildcard)
  Firewall events srcip=<ip>

  In between:
  Email addresses
  File Paths
  
  Blurst:
  Quoted values

  ### NOT vs NOT

  NOT TERM() = [ AND [ NOT term ] ] - Very useful use of TERM()
  vs
  NOT field=TERM() = [ AND ] - Completely useless use of TERM()

  ### WindowsEvent - PREFIX()

  Works on major terms.
  Case sensitive (and terms are lower case, so always use lower case)? Are they?
  PREFIX(eventcode=)

  ### Sysmon Process Creation - Walklex

  Subsearch Walklex pattern=\*term*

## Links and References

1) [Fields, Indexed Tokens, And You - Presentation - Martin Müller](https://www.youtube.com/watch?v=oZ-teiqqKB4)
1) [Fields, Indexed Tokens, And You - Slides - Martin Müller](https://conf.splunk.com/files/2017/slides/)
1) [Interactive Bloom Filter](https://www.jasondavies.com/bloomfilter/)
1) [TSTATS and PREFIX](https://conf.splunk.com/files/2020/slides/PLA1089C.pdf)
