# NoSQL means No security?

author: Philipp Krenn
ref: @xeraa
works for elastic - developer advocate

NoSQL ? No SQL injection. (lmao)

## Injections

- javascript injections

ref: diaspora kalzumeus.com

- problem: js evaluation

solution: deactivate: --noscripting

## Ransomwares

Feb 2015: first article about sec issue
> Massive ransomware attacks takes out 27k mongodb servers
ref: techrepublic

used to dump data, drop it, then ask for money

## MongoDB

MongoDB 3.6 comes hardened against databsae ransomware by default
Auth disabled
MongoDB has great Auth and authorization

> Enable: auth=true
<=3.0 Challenge auth
>=3.0 SCRAM-SHA-1

Configurable `iterationCount`
Predefined roles.

>=3.0 SSL included

## Redis

used to bind to all interfaces

### proected mode

>=3.2.0
answer local queries but not remote

auth:          y
authorization: n

PLAINTEXT password in `redis.conf`
`AUTH <password`

no builtin ssl or rate limits

### hiding commands

set in `redis.con`

`rename-command CONFIG mysecretconfigname`

> Security by obscurity way

`rename-command CONFIG ""`

> Command kind of gone

ps: don't pass in random lua scripts


## Elasticsearch

Not to all interfaces anymore

> change cluster name

cant run as root.

"Cockroaches"
think it goes away when proven wrong, but comes back anytime

### scripting

now uses "painless", used to have groovy

why would you create scripting language ?
need just the right features for elasticsearch

painless is the new default; python ruby and groovy deprecated.

## Shodan


# Personal notes

Watch that lightning talk again later.

potential talk ?
