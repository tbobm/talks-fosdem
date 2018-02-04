# Provisioning vs Configuration Management
# Deployment vs Orchestration

author: Peter Souter
Tech Account Manager @Puppet
github.com/petems

hashtag DadOps

## Intro

can puppet do X ? Yes
should puppet do X ? sometimes no

## Naming things is hard
> meanings evolve overtime

4 terms:
- Provisioning
- Configuration Management
- Deployment
- Orchestration

**Infrastructure as Code**

Eliminate config drift using IaC
> Automation
avoids shell scripts, people's brain and stuff

## Provisioning

Cobble, PXE booting scripts, Kickstart...
Bare metal boot provisioning

> Fog - Ruby lib for AWS

Configuration in ruby
Allows abstraction

Terraform followed this.


### Drift in APIs

can be deprecated, workarounds are needed...

> TugBoat @DigitalOcean


Deprecated of DO 1.0

forge.puppet.com

### Delegate maintaining to authors

i.e.: google modules maintained by google

Terraform provider Dev Program

### Cloud vendor create own framework
i.e.: AWS


## Config management

Puppet aws module
Chef // Knife
Ansible // AWS playbook

Config management + provisioning = single source of truth

----

> No problem I have a shell script

- Hard to scale
- Hard to read
- Wundows ?


## History of config management

CFengine > Puppet > Chef
         > + Cobbler > Ansible

Whatever tools: principle is the same. Config as Code. -> Single source of truth

Reduce cost and time per release
> pre-existing code for often available.
(force, galaxy, supermarket...)

Potential for sharing and reuse

Less arguments about semantics

## How to get the code onto the system?

There is a baseline needed for config management tool.
> Belt and braces

Golden image consideration
Pre-baked initial config
Config M pre-installed
Vendor-specific
Easy for drift to occur & hard to maintain


## Deployment

D has come a long way

"Good" old days

Manually > Script > Deployment tool
Every lang has its own

Ruby - Capistrano
Python > Fabric
PHP > Deployer

--- 

Deployment otol = Roolback or failure management <3

D is generally Dev owned
Config management more ops owned

Collaboration: DevOps


Jenkins Blue Ocean

### Next blurring moment

CI tools like Jenkins can do the 4 referenced terms

CI often end up being main interface.
> Gatekeeper


### Next blurring moment

Package release as deployment


## Orchestration

Diff between O and CM

- info gathering and sys intel
- one-off tasks doesnt fit in state-based
- triggering config managemnt runs withing time-window
- emergency: "oh god need fix"


Ansible feels more orchestration-y than other C M tools

Ssh most basic O tool:w
> @pssh = parallel ssh

### We want to get more advanced

> O tools come in

most C M tools have O app or tool too

puppet // bolt
          bolt plans
Knife

Docker docker dokcer dokcer
Containers Containers Containers

P is least affected
(especially if PaaS)

---
Do we need C M or  if have containers?
> it depends.

There is place for C M in containers world

> % of Orgs using each tool or platform

Host is not a container.

P: Puppet AWS, Knife, Terraform...
Setup O: Puppet ?
Container platform: manages the reste.

Building containers with C M ?
`puppet docker...`

---

P is creation of system
C M managing state on those systems
O actions performed at scale on system
Containers changed the 4, but did not replace them.

------
Immutble infrastrucure is not the anwser
Immutble infrastrucure is really great
