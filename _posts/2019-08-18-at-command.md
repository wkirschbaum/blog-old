---
layout: post
title:  Simply leave reminders for yourself
date:   2019-08-18 19:13:31 +0200
categories: hints linux
---

```bash
sudo apt install at
```
Then you have quite a few options. Make sure to check out `man at`

```bash
at 8am tomorrow
at> echo "Make sure to get good coffee"
at><CTRL-D>
```

Which will send an email to your user at 8am tomorrow morning.

```bash
at 8am tomorrow
at> notify-send "Make sure to get good coffee"
at><CTRL-D>
```

if you don't have local mail set up.

It is pretty good with understanding complex times

```bash
at midnight
at> clamdscan /
at><CTRL-D>
```
if you want to start a long running job later.
