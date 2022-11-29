---
url: /weekend-notes-stats-tool
date: 2021-08-28T02:05:01.082Z
lastmod: 2021-08-28T02:05:01.092Z
tags: ["Project", "Weekend-Notes"]
title: Weekend Notes Stats Tool
description: I’ve made a tool to analyse my article statistics on Weekend Notes.
  Here’s how it works and a bit about the issues I had while building it.
image: ../assets/images/weekend-notes-stats-tool.png
---
I’ve made a tool to analyse my article statistics on Weekend Notes. Though it can be used by other writers since I’ve deployed it as a public site. It’s running on AWS Lambda with the front end on my own site just because it’s easier - though the front end could be deployed to S3 and hosted as a static site since it just posts form data to my Lambda function. Here’s how it works and a bit about the issues I had while building it.

## Analysing the Data

I’ve built my app to use BeautifulSoup to parse the HTML source code of the stats page, this way there’s no risk of exposing anything secret apart stats about one particular article, and I don’t need to worry about logins in code - just let the user login as normal in their web browser and grab the source code and give it to my tool.

I won’t get into the details of the analysis or DOM structure of the Weekend Notes statistics pages, but I’ll talk about the ways I structured the data and my code, as well as things I learnt.

I discovered the Python `calendar.day_name` and `calendar.month_name` for converting integer value to English name

I discovered that you can pass a function to BeautifulSoup so that your function can do the complex matching like in LINQ.

I tried to handle actions in methods rather than in global scope so that I can easier handle errors in input.

You can sort a dictionary so that when you loop over the keys, the values are sorted. (How do I sort a dictionary by value?) That’s handy. 

## Deploying The Script

I created the script to be run as a Flask app using Zappa for Python because I already had some experience with a previous data analysis project in Python. Read about my experiences with Zappa this time around: [AWS Lambda using Zappa](/aws-lambda-and-zappa)

Because Zappa needs to be in a Python virtual environment I knew I had to create the virtual environment and be able to put my Flask app code in it easily. I could develop in the virtual environment (which would keep Python projects from conflicting) but I don’t have any other Python projects on my personal PCs  that I’m concerned about so I didn’t worry. 

So I created two BASH scripts to:

1. Create the virtual environment
2. Copy the files needed and pull down any Python packages (using a requirements.txt file) and run the Zappa commands.

This way I code away and just use a simple script to deploy everything for me. If I wanted to put in a CI/CD pipeline, I could do that too. 

This worked well, except for copying files inside a folder and making it repeatable. I had to mkdir -p (Is there anyway to copy a file to a directory that does not exist?) and also the -R flag on cp will copy recursively. Handy!

Finally, due to PC issues I changed to use my Windows 10 desktop rather than my Mac laptop so I needed to fire up Windows Subsystem for Linux to use my BASH scripts. Unfortunately it was so old the Python was out of date. I tried to update it using apt-get upgrade but that doesn’t actually upgrade the OS. (How To Upgrade to Ubuntu 16.04 LTS from Ubuntu 14.04 LTS ). Actually I stumbled upon do-release-upgrade because the Microsoft Store advised that’s how to upgrade Linux inside WSL. (Actually that page says so too, further down.) After a couple of upgrades and hours later I had a working WSL again and I could just develop on Windows and switch to WSL when I wanted to package up. Wonderful!

## Building the Front End

When I started building the front end, I pretty much took my previous front end HTML form from an earlier project like this and modified the form to POST instead of GET. But of course I quickly remembered that a normal form can’t simply POST plain data as the request body like you’d do in a React project or REST API. A normal form needs either url encoded form fields or multi-part form data. Or you use JavaScript to submit the form and handle the response. I first tried to implement that in JavaScript with our friends Stack Overflow and MDN to give me enough idea to get going:

* https://stackoverflow.com/questions/6665510/sending-a-raw-data-post-request-with-an-html-form
* https://stackoverflow.com/questions/6396101/pure-javascript-send-post-data-without-a-form 
* https://stackoverflow.com/questions/3547035/javascript-getting-html-form-values/41262933 
* https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/open 
* https://stackoverflow.com/questions/3038901/how-to-get-the-response-of-xmlhttprequest 

But I soon realised it was going to be easier just to change my back-end to handle multipart/form-data and let the browser submit it as normal. That way, the browser will also handle the returned page as the standard response.(Like when you submit any other form.)

(It’s hard to build plain HTTP POSTs by hand, much easier to just use Postman or Insomnia): [Mozilla Developer Network POST - HTTP ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST)

Luckily Flask can do both. [Quickstart — Flask Documentation (1.1.x) ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST)

At the same time, I discovered that pasting a large amount of data into a textArea causes Chrome to lockup. Firefox wasn’t locking up so I realised it was a browser issue, which meant it might be possible to code around it. I found:

https://stackoverflow.com/questions/1600398/large-text-in-textarea-freezes-computer 

and then disabled spell check, auto correct, and auto complete. Now Chrome is as responsive as Firefox is when pasting the source code from Weekend Notes.