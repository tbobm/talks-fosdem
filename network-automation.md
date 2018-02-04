# Network automation journey

author:

ref:

> bare metal

---

Multi data center setup

Who manages the net setup?
Especially if really complexe ?

think about containers, hosts...

## Start of the journey

Main pull back: people you are working with.
Convince them about the benefits.

Technology is easy to deal with. Technical debt can be resolved
Process too. Can be fixed

> take care of people

## Context

How to do net automation if you are sys engineer.

Provide context, understand who you are talking too
what tech you are going to use.

Imagine virtual company which has 4 data centers.
team are 5/5 for net eng and infra & cabling
less than 200 switches

have CMDB
IPAM
NMS:SNMP based

setup: traditionnal 3 tier architecture "Core-Distribution-Access" w/ extended layer 2

frequent operational activities
Changes, troubleshooting, new applications

constraints
linear process, lots of control.


## Entreprise network management trends.

- CLI
    + Based on Cisco traditions
    + Cut & paste using a notepad
- Frameworks & controllers
    + Excel
    + Python scripting
    + Templating
    + Ansible
    + Chef
    + Puppet
- Event driven automation
    + Sensor triggered events
    + napalm logs
    + Salt
    + IFTTT
        - StackStorm
        - Ansible AWX
- Intent based Networking
    + Declarative
    + Network intent composition
    + Aspen
    + Boulder
    + Based on Machine Learning

---

1996: telnet
2013: ssh

- Manual
- Cut & paste
- Serial
- Inconsistent
- Error prone

## Why we are not automating ?

- just a fad
- not relevant to our setup
    + mixed vendors and legacy platforms. no solution can handle this
        cost prohibitive
    + do not need a bazooka to handle a mosquito
    + busy, shortage of resources
    + none of my acquaintances does this.

---

Example of in-house Visual Basic template App


## Kickstart: brainstorm

- What is NetOps, NetDevOps?
- problems?
- visibility into operation?
- responsibilities?
- task/process reponsible for?
- how much time to dedicate to automation?
- what current tools are in place for automation? (processes or tools)
- why automation processes/tools?
- what automations would like to have ? processes/tools?
- how should activity communications be enhanced?
- how should we start?

## Possible Business Drives?

- Pressing needs:
    + Scale
    + Optimization
    + Failure management; consistency
- Opportunities
    + IoT
    + Big Data
    + etc

## What to automate?

- Config archive
- Config generation
- Config deploy
- Reporting

- Day 0 provisioning
- Software upgrade
- Compliance checks
- Pro/post checks
- Anomaly detection
- Troubleshooting
- Software qualification

## Top traditionnal network issues

Spanning tree misconfigurations
VLAN(s) misconfiguration
Firewall policies (Calico)
and more

## Application and sytem automation

Huge progresses

## History of programmable network

Didnt change much

## The network world perspective

Ansible, OpenCOnfig...


...

## Ansible! However


Configuration can become complex.
Inventory, variables, playbooks, roles...
Need to add testing process, review, before applying to production network


- Collaboration
- Version Control
- How to manage scale and growth
- Testing

## Process & Technology, KISS Workflow

- VSCODE
    + Syntax highliting
    + Validation, linting, indentation
    + Automation UX
- AWX
    + Configuration management
    + Orchestration
    + Role based access
    + Scheduling
    + Remove Execution
    + Event based triggers
- GITLAB
    + History
    + etc...


## Start small and simple

## Recomendations

- Take care of themselves
- Favor open solutions over proprietary
- Gain yearly savings of over 25% in 2023
- Invest back the savings into the people
- PP-RPC # Premium People - Reward Premium Compensation
- Create cross-functionnal assignments

## Think ahead

> Devices processes automation

- Standardize network elements as much as possible
    + Avoid massive variatiions (OS, platforms...)
    + Avoid massive variation in topologies and feature use
- Insist on hardware that does have usable API 
  avoid relying on screen-scraping for automation

## Configuration management 101

### Yang

IETF Data modeling language standard

- Models configruation and operational state data
- Data source of truth
- Easy to extend on existing models "DRY"

### NetConf

Net configuration protocol

IETF net managemnet protocol

meant to CRUD configuration (uses SSH :83)

### RestConf

works along with NetConf

HTTP based
uses Yang too

### Yang Yet Another Next Generation

### Ansible netconf module

### Hit Refresh

- Continuous Improvements
