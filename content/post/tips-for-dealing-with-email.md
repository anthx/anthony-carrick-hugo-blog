---
date: 2023-04-16T04:50:46.479Z
lastmod: 2023-04-16T04:50:46.529Z
tags:
  - email
title: Tips for dealing with email
description: I get email. Lots of it. Here are some of my attempts to keep it under control
image: /assets/images/Text-Blog-Featured-Image.png
---
# Outlook

In Outlook.com I make extensive use of Outlook‘s Sweep rules to automatically move emails to folders after 10 days or keep only the most recent email.

Sweep rules can:

* Move all messages from the inbox from that sender
* Move all and future in the inbox from that sender
* Keep only the most email, moving the emails from that sender to a folder or trash
* Always move messages older than 10 days to a folder or trash from that sender

![Screenshot of Outlook for Web’s Sweep Rule feature](../assets/images/mail-anthony-carrick-outlook.png "Creating a new Sweep Rule")

I use the last two rules depending on the types of email:

1. For some emails, I only need to see the one most recent because those emails supersede previous, like hosting services update reminders or certain kinds of newsletters.
2. Emails from Meetup.com for example I‘m happy to delete them after 10 days, but I also use that 10 days to move *particular* emails to a folder of Meetup emails for my records. Like, I don’t to keep every new meetup scheduled, but I want a copy of emails about meetups that I attended.
3. Newsletters I’ll move into a folder for that newsletter after 10 days, because I want to see the few most recent.

Then I’ll use ordinary Filters in Outlook to filter emails that can’t be picked up as precisely by Sweep, just because that feature doesn’t have the same control over triggered emails.

# GMail

Gmail doesn’t actually have a Sweep feature unfortunately, only Filters, so I can’t automatically have it Archive emails after 10 days.

However, I came up with a work around, Google Workspace Apps Script. It doesn’t actually require a paid Workspace account, it works on the free Gmail too.

![Screenshot of Google Apps Script marketing page](../assets/images/apps-script-–-google-apps-script.png "Use Google Apps Script to script your own Google Workspace")