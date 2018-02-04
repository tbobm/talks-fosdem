# File Access-control using Landlock

author: Mickael Salaun

## Secure user-space software

How to harden an app ?
- secure development
- follow the least privilege principle
- comprtmentalize exposed process

Container constraints
- each image can be unique
- independant from the host
- hence may need dedicated access control rules
-> Embedded security policy

---

What can provide the needed features?

- SELinux: Fine-grained control but no embedded policy or unprivileged use (must be root)
           -> Have to configure the whole host
- seccomp-bpf: no fine graind-control, but embedded policy and unprivileged use
- namespaces: embedded policy but no fine graind-control and partial unprivileged use

- Landlock: fine graind-control, embedded policy, unprivileged use
            -> Tailored access control to match your needs: programmatic access control

unprivileged use is disabled for initial upstream inclusion but will be enabled after test period

## Landlock overview

P(user space) sandboxes itself in Landlock(kernel space) and landlock is asked instead of direct syscall

## L: patch v8

to be released soon

> MVP
> Focused on file system access control
> using eBPF

### eBPF

> extended Berkeley Packet Filter

in-kernel VM
- safely execute code in kernel at run-time
- widely used in the kenerl: network filtering, seccomp-bpf, tracing...
- can call dedicated functions
- can exchange data through maps between eBPF progs and user space

Static program verification at load time
- memory access checks
- register typing and tainting
- pointer leak restrictions
- execution flow restrictions

### The Linux Security Modules framework (LSM)

Linux Security Modules:
- allow or deny user space actions on kernel objects
- policy decisions and enforcement points
- kernel API: support various security models
- 200+ hooks: `inode_permission`, `inode_unlink`, `file_ioctl`

Landlock
- hook: set of actions on a kernel object (e.g: walk a file path)
- program: access control checks stacked on a hook
- triggers: action mask for which a program is run (e.g.: `read`, `write`, `execute`, ...)


### Life cycle of a Landlock program

C source > (build) > eBPF bytecode > (embed program)
    > application > (execute app) > process > (load) > kernel

### Landlock rule example

Goal:
- whitelist of file hierarchies for RO or W access
- enforced on each file system access request for a set of processes

source code: https://landlock.io => FOSDEM 2018

---

eBPF inode map

Goal:
- restrict access to a subset of the file system

Challenges:
- efficient
- updatable from user-space
- unprivileged use (i.e.: no `xattr`)

Solution
- new eBPF map type to identify an inode object (dev + inode nbr)
- use inode as key and associate with 64-bits arbitrary value

---

Chained programs and session

Landlock programs and their triggers (example)

`fs_walk` > `fs_pick` (R)> `fs_pick` (W)

##### Example

- define metadata
- define function

```c
int fs_pick_write(struct landlock_ctx_fs_pick *ctx) {
    __u64 cookie = ctx->cookie;

    cookie = update_cookie(cookie, ctx->inode_lookup,
                           (void *) ctx->inode);
    if (cookie & MAP_MARK_WRITE)
        return LANDLOCK_RET_ALLOW;
    return LANDLOCK_RET_DENY;
}
```
- load program in kernel using ebpf syscall

- apply landlock prog to a process
```c
seccomp(...);
```
## Rule enforment on process hierarchy

[[P1] > P2
    > [P3 > P4]]

## Demo

RO accesses
- /public
- /etc
- /usr
- ...


RW accesses
- /proc/self/fd/1
- /tmp
- ...


```bash
LL_PATH_RO=$LIST_OF_DIRS LL_PATH_RW=$LIST_OF_OTHER_DIRS ./landlock1 /bin/bash -i
```

## Wrap-up

user space hardening:
- programmatic and embeddedable access control
- dynamic security policy
- designed for unprivileged use

## Notes

Excellent against defacing. Allows to easily sandbox

site: https://landlock.io
