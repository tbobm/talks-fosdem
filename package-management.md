# Package management unites us all

author: works for Stripe, and go package management

> Defined terms

## Shared experiences

### Dependency hell

- Issues about the errors of the package manager
- Weird deps management (diamond deps,...)

### Role of the package manager

Has to be the link between outside dangerous package world and 
our baby software

> My sense is that given WOD is chaotic and hard to knw how much we can trust it

-> Test it ! Go and test that.

Want to do that easily, dont want to have to make difficult to replicate
experiment or make coworker's life hard.

Want feedback fast !
(Two conflicting objectives)
Fast & flexible || Reliable

## The ties that bind

Oackage M = Risk M
Modern PM made of communities

### What is a package anyway ?

Floor of definition = Nbr of PM
Deeply incompatible.

-----

Have to be retrieved (.tar?)
Package imposes rules
- metadata files (`package.json`?)
- file layout conform to pattern
- object must conform (tests, lint...)

We can force rules, but there is a gradation of package quality anyway.

------
Exposes metadata

> Example
Author/Maintainer
Deps and constraints

-----
Package has Name and Version (N, V)

Implies multiple version, families

-----
Package universe

> "The set of all packages, at all versions"

But there is also a "Sliced Universe" concept
- laptop scope
- time scope (Ps go away, moves...)
- Windows? Portal? Wormhole? (i.e.: debian/ubuntu's apt) -> Registry
Go is exception, "registry" is DNS


Public registries for languages/Private, external, additionnal...
Registries create a view of a projectable slice of this universe

------

#### A Package

- Must be in the reachable part of the universe
- Must be valid (cf above points)
- Should follow guidelines


Rules, norms, lints are made to obey then and create a helpful ecosystem
> Good actor of the system (follows guidelines), ability to trust

"Packagine rules define norms that people are expected to obey"

## The history

How to prove software is reliable?
"Tests only prove absence of bugs"

Turing: State of a program is good.


### Structured programming
> Away from goto & jump
> closer to foor loops etc


### Modular programming

//Structured prog
Separation of concerns
Information hiding


P define relationship to logic via modules

## Unbinding the Boundaries

ref to npm@5
http://package.community

### System vs Language

Sys 
- Usually create combinatorially safe package universes
- finite group of people work on populating them
- version constraint; usually good; higher quality

- encode more at the metadata level

Lang

-----
Tu duplicate or not?

nix and npm duplicate, most others dont

### SAT

Avoid it if you can, tricky domain

#### Sat as the problem vs as the platform

cc Russ Cox version sat go


### Schaefer's dichotomy

Problems are P or NP-complete
> Subset of boolean relations

-----
> Russ Cox

Minimal Version Selection (SAT as problem)
First to clearly articulate,

- Semver = compatibility between majors
- Only min ver are specified
- Mechanism allows dupe on majors

Using this we're on the P side.

-----
API Shape analysis (SAT as platform)
Version contraints cause pain when too loose or too tight

Peek deeper into relations between packages (refernces ?)
A.Foo references B.Bar

Name ref on B.Bar

@@github.com/clakbw
