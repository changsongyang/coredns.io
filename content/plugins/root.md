+++
title = "root"
description = "*root* simply specifies the root of where to find files. "
weight = 42
tags = ["plugin", "root"]
categories = ["plugin"]
date = "2024-11-22T08:09:54.87754811"
+++

## Description

The default root is the current working directory of CoreDNS. The *root* plugin allows you to change
this. A relative root path is relative to the current working directory. 
**NOTE: The *root* directory is NOT currently supported by all plugins.** 
Currently the following plugins respect the *root* plugin configuration:

* *file*
* *tls*
* *dnssec*

This plugin can only be used once per Server Block. 

## Syntax

~~~ txt
root PATH
~~~

**PATH** is the directory to set as CoreDNS' root.

## Examples

Serve zone data (when the *file* plugin is used) from `/etc/coredns/zones`:

~~~ corefile
. {
    root /etc/coredns/zones
}
~~~

When you use the *root* and *tls* plugin together, your cert and key should also be placed in the *root* directory.
The example below will look for `/config/cert.pem` and `/config/key.pem`

~~~ txt
tls://example.com:853 {
    root /config
    tls cert.pem key.pem
    whoami
}
~~~

## Bugs

**NOTE: The *root* directory is NOT currently supported by all plugins.** 
Currently the following plugins respect the *root* plugin configuration:

* *file*
* *tls*
* *dnssec*
