---
image: /assets/images/gnu.png
---
![GNU Logo](/assets/images/gnu.png){:.mx-auto}
{:.d-flex}
# debuginfod server for openSUSE
{:.display-4.text-center}
Distributing ELF or DWARF debugging information, plus associated source code, for a collection of binaries.
{:.lead.text-center}

## What is debuginfod?

debuginfod is an HTTP file server that serves debugging resources to debugger-like tools.

Recall that debuginfod exists to distribute ELF or DWARF debugging
information, plus associated source code, for a collection of binaries.
If you need to run a debugger like gdb, a trace or probe tool like perf
or systemtap, binary analysis tools like binutils or pahole, or binary
rewriting libraries like dyninst, you will eventually need debuginfo
that matches your binaries. The debuginfod client support in these tools
enables a fast, transparent way of fetching this data on the fly,
without ever having to stop, change to root, run all of the right
commands. Run `zypper install $package-debuginfo` and try again.
Debuginfo lets you debug anywhere, anytime.

Right now the service serves only
[openSUSE Tumbleweed](https://software.opensuse.org/distributions/tumbleweed)
packages for the x86_64 and aarch64 architectures and runs in an experimental mode.

Client support will be shortly added into binutils, gdb, strace and
other tools.

For more information follow the
[elfutils status page](https://sourceware.org/elfutils/Debuginfod.html).

### Client configuration

The simple and obvious solution to use the debuginfod for openSUSE
Tumbleweed is:

```
export DEBUGINFOD_URLS="https://debuginfod.opensuse.org/"
gdb ...
```

For every lookup, the client will send a query to the debuginfod server
and get's back the requested information.
