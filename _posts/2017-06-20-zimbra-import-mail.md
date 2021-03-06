---
layout: post
title: "Importing Outlook (.msg) files into Zimbra in Bulk from Disk"
slug: "import-outlook-msg-into-zimbra-from-disk"
description: "Importing Outlook (.msg) files into Zimbra in bulk from disk"
category: 
  - zimbra
  - outlook
  - import
  - mail
# tags will also be used as html meta keywords.
tags:
  - zimbra
  - outlook
  - import
  - mail
show_meta: true
comments: true
mathjax: true
gistembed: true
published: true
noindex: false
nofollow: false
# hide QR code, permalink block while printing.
hide_printmsg: false
# show post summary or full post in RSS feed.
summaryfeed: false
## for twitter summary card with squared image and page description or page excerpt:
# imagesummary: foo.png
## for twitter card with large image:
# imagefeature: "http://img.youtube.com/vi/VEIrQUXm_hY/0.jpg"
## for twitter video card: (active for this page)
#videofeature: "https://www.youtube.com/embed/iG9CE55wbtY"
#imagefeature: "http://img.youtube.com/vi/iG9CE55wbtY/0.jpg"
videocredit: tedtalks
---
If you have a bunch of .msg files that you got from a client who would like you to import those outlook emails into zimbra you could use these scripts.
Also if you need to import contacts from vcf files you've come to the right place.

### Requirements
 - zimbra install on linux
 - msgconvert <http://www.matijs.net/software/msgconv/>

```bash
# Install /usr/local/bin/msgconvert
cpan -i Email::Outlook::Message
```
<!--more-->

## Installation

```bash
wget https://github.com/charljmert/zimbra/archive/master.zip
unzip master.zip
cd zimbra-master/
./setup.sh
```

## How to use
1. Convert .msg files to .eml

```bash
zimbra_convert_msg_to_eml.pl MyDir/Emails
```

2. Import files to an Inbox

```bash
zimbra_import.pl MyDir/Emails /Inbox user@email.co.za eml --zimbra-home /opt/zimbra/
```

## Contacts
There are scripts to deal with importing contacts. You can unload a contacts directory on the contact script like so.

```bash
find MyDir/Contacts -type f | zimbra_import_contact.pl user@email.co.za
```

## TODO

 - The main script zimbra_import.pl will handle all importing including msg, eml, vcf, vcs and ics
 - There is no script to deal with importing vcs and ics calendars
 - There is also no script to deal with PST's
