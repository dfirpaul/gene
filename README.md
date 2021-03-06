# GENE: Go Evtx sigNature Engine

The idea behind this project is to provide an efficient and standard way to
look into Windows Event Logs (a.k.a EVTX files). For those who are familiar with
Yara, it can be seen as a Yara engine but to look for information into Windows
Events.

Here are some of our motivations:
  1. By doing IR frequently we quickly notice the importance of the information
  we can find inside EVTX files (when they don't get cleared :)).
  2. Some particular events can be considered as IOCs and are sometimes the only
  ones left on the system.
  3. To the best of my knowledge, there is no easy way to query the logs and
  extract directly the interesting events.
    * because we (at least I) never remember all the interesting events
    * we cannot benefit of the other's knowledge
  4. You might tell me, "Yeah! But I push all the interesting events to the SIEM
  and can query them very easily". To what I would reply that it is not that easy.
    * there are events you do not know they exist before you find it in an incident
    so it is very unlikely you push it into your SIEM
    * considering the example of Sysmon logs, it would be quite challenging to push
    everything interesting into your SIEM. Either you have few machines on your
    infra or you are very rich (or at least the company you are working for :)).
  5. Before writing that tool I was always ending up implementing a custom piece
  of software in order to extract the information I needed, which in the end is
  not scalable at all and very time consuming.
  6. I wanted a cross platform tool

# Use Cases

  1. Gene can be used to quickly grab interesting information from EVTX at whatever
  stage of analysis.
    * Early compromise information collection
    * Infected host analysis
    * IOC scan on all your machines
  2. If you are forwarding the Windows Event somewhere, you can use it as a
  scheduled task to extract relevant piece of information from those logs.
  3. It can be used to retro search into your EVTX backup
  4. It can be combined with Sysmon in order to build up use cases in a minute
  (the time to write the rule) and it is much more flexible than the Sysmon
  configuration file.
    * Suspicious process spawned by another one
    * Suspicious Driver load events
    * Unusual DLL loaded by a given process
    * ...

# Documentation
Please visit: https://rawsec.lu/doc/gene/1.4/

# Notes

This project is quite new and may still have little bugs, so do not hesitate to
open issues for those.
