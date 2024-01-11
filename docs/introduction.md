# Introduction

<figure markdown>
  ![img](https://sites.psu.edu/wled480eslworldcampus/wp-content/uploads/sites/29670/2016/01/Meme1.jpg){: style="width:480px"}
</figure>

---

## Problem Statements

- Pros and cons in the Internet search engines, passive DNS/SSL services:
  - e.g. I can find CVE-xxx in X but not Y.
- Data management. (How do you manage search results?)
- Searching is boring and human error is inevitable.

## Mihari Is to Rescue

- One Sigma-like rule to rule multiple services like the One Ring.

<figure markdown>
  ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/One_Ring_Blender_Render.png/125px-One_Ring_Blender_Render.png)
</figure>

- SQL database based data management.

- Automate all the things!

<figure markdown>
  ![img](https://static.movingpackets.net/2017/01/mp_automate_all_the_things.jpg)
</figure>

## Use Cases

- C2 tracking
- ASM?
- Bug Bounty/Pentest?

## User's Voice

> Mihari is single-handedly one of the most helpful and versatile tools a CTI analyst can have in their toolkit and repertoire. It removes the complexity of needing to develop custom tooling, and provides a simple yet coherent mechanism through which to develop a collections programme leveraging services such as Censys, Shodan and VirusTotal. Combined with Shimon, **Mihari is the definitive tool for tracking malicious infrastructure**.
>
> Mihari’s extensible nature, including its API, ensures it remains flexible enough to integrate within existing analysis pipelines. Ultimately, Mihari can help reduce a CTI teams’ reliance on vendor IOC feeds, by allowing teams to rapidly develop and automate their own high-fidelity collections to meet specific organisational intelligence requirements and priorities.
>
> <div style="text-align: right; margin-right: 10%;">Sajid Nawaz Khan, Principal Analyst, FTSE 100 <a href="https://infosec.exchange/@snkhan" target="_blank">(@snkhan@infosec.exchanges)</a></div>

## References

- INES by Félix Aimé (ex-Kaspersky GReAT)
  - Developed to help run continuous queries on services like Censys/Shodan.
- [3c7/infrastructure-tracking-schema](https://github.com/3c7/infrastructure-tracking-schema)
  - The goal is to have a common rule schema that allows querying a variety of services and chaining those queries together.
- [InQuest/ThreatIngestor](https://github.com/InQuest/ThreatIngestor)
  - Extract and aggregate threat intelligence.

## Alternatives

- [projectdiscovery/uncover](https://github.com/projectdiscovery/uncover)
  - Quickly discover exposed hosts on the internet using multiple search engines.
- [projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)
  - Fast and customizable vulnerability scanner based on simple YAML based DSL.
