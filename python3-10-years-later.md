# Two branches

Often 2 branches in order to have compatibility

# Setuptools ? Package stuff

# Unicode

import six
> six.u("mystring")

# python 3 trolls

doesnt add anything new
> bytes is simpler, would be the way to go
python 3 introduces new unicode issues

## python 2.8

because python2.7 is alive, there should be a 2.8
implying some backports

> CPython core developpers not OK
> They want to focus on future and help migrate

people used to say "3 will never take offo

"durr only 2%"

## PEP 404

Python 2.8 un-release schedule - 2011
2013 -> 39 of top 50 projects support py3
(80%)

> Py2.7 EOL extended to 2020 (5 more years)

# Spring

## #1 solved

- 2011 - pip1.0
- 2014 - py2.7.9 and 3.4 > ensurepip
- pip defacto installer

issue was about having to have admin rights only to install packages
now installers come packaged with pip

## 

new approach:
    stop promoting 2to3
    dont remove py2 support
    instead only add python3 support

- new tools:
    modernize and sixer
    incremental changes tested by a CI

(cc openstack)

solved by multiple very small pull requests
i.e: parenthesis on print

## Large codebase

issue is turnover

- legacy codebase: first add new test to reduce regression

dropbox built `mypy` to add types

by choice python3 *allows* type annotation

`typing` made by GVR and core which provide more types

## Building bridges

reintroducing unicode annotation
> choices have been made

py3k warnings added to py2
py2 backports such as unittest2 enum34

Py3 wall of shame -> wall of superpowers

## Performange improvements

3.6 on average 25% faster, up to 2 times

Lisa Guo and Hui Ding keynote > Pycon 2017
> Instagram on py3
~ 12% on uwsgi/django on CPU
~ 30% memory usage

## Python 2.7 wontfix

Dont want to break a working and mature version of the language.
Backward compatibility is important
py2 sypports legacy platforms


But backward prevents to fix py2 bugs
unicode support, dict issue
not randomized hashes by default
internal clocks issues
subprocess is not threadsafe
RecursiveLock is not signal safe

## Fixed in py3

3.3 clock fixed PEP418
3.4: PEP446
3.5: PEP475

> We are aware of the code breakage this is likely to cause, and doing it anyway for the **good of mankind.**
_Guido van Rossum PEP 446 approval_

## 21 new modules

asyncio, unittests...

f-string for py3.7 <3

### New python3 syntax improvements

type annotation, type hinting, matrix multiplication...


## Should we bury python2?

Fedora and ubuntu already removed py2 from base system

python3statement.org
pythonclock.org

ipython, django are only py3

# Python4 ?

2 to 3 wasnt the best way to migration, new migration will be different.
It will be more like `gtk`, more like a "new version".

Deprecation > warnings > suppresion

TODO: @dict type http header crash server ?
