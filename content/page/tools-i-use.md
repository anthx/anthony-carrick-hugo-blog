---
url: /tools-i-use
date: 2021-08-17T08:28:23.646Z
title: Tools I Use
description: Some of my favourite software development tools.
menu:
    main: 
        weight: -90
        params:
            icon: user
---

I’ve been involving myself in a few projects lately, for both work and personal life. During these projects, I’ve been thinking about what tools and technologies I use, and to use while I’m in the planning process. I’d like to share some of these.

updated: 29th March 2018 – Git Bash for Mac
updated: October 2023 - GitHub Codespaces

Code Editing
============

*   [Visual Studio Code](https://code.visualstudio.com) – for editing and creating static HTML and CSS, as seen on acarrick.com. I’m also using VS Code for some projects at work.
*   [PyCharm](https://www.jetbrains.com/pycharm/) – my Python IDE of choice since Assignment 3. I use the Professional version, while I have a student license, but there is a free Community edition as well which has the core functionality.
*   I also use [TextWrangler](https://www.barebones.com/products/textwrangler/) on the Mac if I want to save battery power and I’m just doing basic edits.
* [GitHub Codespaces](https://github.com/features/codespaces) - Free for personal use Docker based development environment in the web browser. Now you can code on your iPad!

Other Tools
===========

*   [Git Bash for Mac](https://github.com/fabriziocucci/git-bash-for-mac) – this is a Terminal customisation and theme that tries (and succeeds) to replicate the much of the extra functionality that Git Bash provides. I missed Git Bash’s display of the branch, tab autocompletion and remote/refs names display. Now I have it on Mac too!
    
    [![Git Bash For Mac screenshot](https://www.acarrick.com/projects/wp-content/uploads/2017/12/Screen-Shot-2018-03-29-at-4.46.58-pm-300x193.png)](https://www.acarrick.com/projects/wp-content/uploads/2017/12/Screen-Shot-2018-03-29-at-4.46.58-pm.png)
    
    Now by git repos display more prominently!
    

Libraries and Packages
======================

Python
------

*   [Jinja2](http://jinja.pocoo.org/) and [Flask](http://flask.pocoo.org/) – Python libraries used for HTML generation and web serving. In both Chat Log Parser and the new Urban Dictionary Statistics.
*   [Requests](http://docs.python-requests.org/) – a Python library to simplify making HTTP requests and handling the response. I use this in the urban dictionary statistics to fetch the JSON from the API.
*   [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/) – this is an excellent library for scraping websites, querying by XPath, CSS, or a high-level abstraction of the elements of the page. I use this for the UQ course chooser.
*   csv – this is part of the Python standard library used to handle CSV data more reliably writing it yourself. I use this in my chat log parser.
*   [PyMySQL](https://github.com/PyMySQL/PyMySQL) – a pure python implementation MySQL driver suitable reading and writing to a MySQL database using normal SQL. Remember to parameterise your queries to avoid SQL injection.

Web
---

*   [Jquery](https://jquery.com/) – it’s Jquery… Makes DOM element selection easy on the client side. I use jquery on my main website.
*   [W3 CSS](https://www.w3schools.com/w3css/) – a CSS framework by W3 Schools – it’s small and looks nice, I use it on the urban dictionary parser and some work projects. It’s responsive, and has several useful features, but still quite a small size.
*   [Bootstrap](https://getbootstrap.com/) – one of the original CSS frameworks, I used Bootstrap on the recipe site for [WIS](https://www.acarrick.com/projects/web-information-systems/), and on some work projects. I like it as it’s complete and responsive

Data formats & Structures
=========================

In UQ course chooser and chat log backup viewer projects I made extensive use of _objects_ from Object Oriented Programming – I made, Course, Program, and Message, as well as Chat Log and Message an _object_ in their own right, a noun. This gives me the flexibility to add both methods and properties to each object so it can manage its own contents and be updated after creation.

However, with the Urban Dictionary Statistics Tool, I haven’t felt the need to handle each definition that way yet, as I’m just iterating over each definition as a whole and adding the limited results to a result dictionary. But as I add definition-based features to it, I may decide to move to a Definition-as-object technique to abstract the processing.

Another project I have in mind, I’ll be saving data to a database, but I’ll also create snapshots locally, using code. I’ll likely create the snapshots in JSON format due to its ease of use in Python and Ruby; and JSON’s ability to fit into XML nicely (as an exchange format at least).

The Future
==========

I’ll try to review this post as I go along, I’ll try to sticky it or something. If you have any suggestions of tools you use, feel free to suggest them in a comment!