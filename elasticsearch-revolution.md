# Elasticsearch (R)evolution

author: Philipp Krenn

db-engines.com
dudeabides.com/articles/the\_birth\_of\_compass

used by github, stackoverflow, wikipedia

ref to ELK stack

> Totally about ELK in general.

## Strictness

**5.0**

Fail and fail fast.
> Exemple with typo in query parameter

## Bootstrap checks

Bad Java version ? Crash at installation. (i.e.: garbage collector)

## Rolling Updates

Cluster checkup, reindex helper -> helps painless updating
Awesome.
Can upgrade nodes one-by-one without downtime

## Floodstage Watermark

Used to be:
low 85%
high 90%
floodstage 95%

## Sequence numbers

Track of data (cf postgres>)
Sync between multiples nodes

-> Huge feature. Allow node death.

`_seq_no` field

records every transation/query

## Cross datacenter replication

---

## ~~Types~~

> Removed until 8.0

## Automatic Queue Resizing

Reject if max response time is unreachable due to queue size.
Rejct & Retry

## Adaptive Replica Selection

Pick best nodes (least used)
Piggyback on requests

## Shrink & Split

---

## Benchmarks


> Slow boiling frog problem

# Personal notes

The new version is really interesting, but there is a need
to test in prior to confirming anything.

I'm not sure it would fit small projects, but bigger applications
(with differents needs such as data persistance and all, see 
[sequence numbers](# Sequence numbers)) could benefit from it.

In addition I'm in fond of the rolling update feature, which
is becoming a must-have for this kind of storage.

The strictness provided by the 5.0 is a real plus too, but I
didn't have the occasion to test its lack in lower versions.
