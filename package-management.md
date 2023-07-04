---
title: "Software and package management"
date: 2023-07-04T08:39:45+02:00
draft: false
weight: 4
objective: 711.2
---
Now that we have a system up and running, we can make it a useful system by installing software on it.
The package manager on all three versions of BSD is `pkg` but while FreeBSD uses subcommands, both OpenBSD and NetBSD use different commands.
This means that on FreeBSD you type a space between `pkg` and the actual command (e.g. `info`) while on NetBSD and OpenBSD you use an underscore: `pkg_info`.

Suppose we want to install the Apache HTTP server, we then must first search for the package name.
It could be called `httpd` or `apache` or perhaps something else entirely.

{{< highlight bash >}}
% pkg search httpd
% pkg search apache
{{< /highlight >}}

As these results can be quite long, you can filter for additional keywords, e.g.

{{< highlight bash >}}
% pkg search httpd | grep -i apache
% pkg search apache | grep -i http
% pkg search apache | grep -i web
{{< /highlight >}}

Once you find the package (apache24 in this case), you can install it.

{{< highlight bash >}}
# pkg install apache24
{{< /highlight >}}
