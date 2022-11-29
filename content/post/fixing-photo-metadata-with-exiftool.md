---
title: "Fixing Photo Metadata with Exiftool"
url: "/fixing-photos-metadata-with-exiftool"
tags: ["Photography"]
image: "../assets/images/fixing-photos-metadata-with-exiftool.png"
description: Let's fix metadata using Exiftool and code!
date: 2019-03-18
lastmod: 2019-03-18
---

So, I’ve recently been scanning some older photos using an Epson flatbed photo scanner. All of the negatives I scanned had the correct camera make and model included in the EXIF data. However, of the prints I scanned only the TIFFs had the camera EXIF data, while the JPGs didn’t, so Lightroom just showed “Unknown Camera” in the Grid view. This was annoying me and I want to be able to find previously scanned photos in the future (plus whatever other key words I may use).

I did some research and found that it isn’t possible to change this metadata directly in Lightroom. (Only the date/time taken, GPS and location data, keywords and a few others can be changed in Lightroom).

The research did mention Exiftool by Phil Harvey, which is also part of another tool I use, Geosetter. Exiftool is a command line tool however and I felt I would rather use a GUI instead. So I looked for one and found a front-end to it, ExiftoolGUI. But it didn’t work, like it just froze up. I realised… I am a programmer and should be able to use the the command line, it’s not hard…

I was going to write a Windows Batch script but a quick search said that Bash scripting is easier, and works in Cygwin, which comes with Git for Windows anyway. And it’s indeed so simple:

```
for file in ./*.jpg
do
	exiftool "$file" -make="SEIKO EPSON CORP." -model="EPSON scanner"
done
```

It even picked up exiftool in the Windows PATH which Powershell didn’t for some reason (maybe I wasn’t patient enough for the restarts).

Run the script and it runs exiftool for each JPG in the folder with the given parameters, -make and -model in this case. By default, exiftool makes a backup of the photos before it updates them too, in the same directory.

I’d prefer Powershell since it’s universal on Windows, but .sh scripts work on Linux and Mac and easily enough in Windows with Cygwin or WSL (Windows Subsystem for Linux).