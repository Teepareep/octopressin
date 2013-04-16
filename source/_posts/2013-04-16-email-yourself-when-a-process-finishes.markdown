---
layout: post
title: "Email Yourself When A Process Finishes"
date: 2013-04-16 13:11
comments: true
categories: [bash, linux, cpanel]
published: false
---

If you write a command in bash that will take a while, consider the following:

```
for i in $(ls /var/cpanel/users); do /scripts/pkgacct $i; done && echo done | mail -v -s 'cPanel Accounts Fully Packaged' support@hostchopper.com 
```

What if you want an even more extravgant loop with more useful email content *and* a carbon copy?

```
/bin/ls /var/cpanel/users | while read a; do echo "** $a ** Now Packaging";  /scripts/pkgacct $a  2>&1 | tee -a /home/pkgacctlog.log ; done ; cat /home/pkgacctlog.log | mail -s "Accounts Packaged on `hostname`" -v -c support@hostchopper.com backuplogs@gmx.com
```

How do I email myself upon completion of an already running process?
```
( while (pgrep rsync 2>&1 > /dev/null); do sleep 10; done; echo done | mail -v -s 'Rsync Complete' backuplogs@gmx.com ) &
```
