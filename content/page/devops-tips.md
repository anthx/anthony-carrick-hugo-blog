---
title: DevOps Tips
url: "/devops-tips"
description: Tips and Resources I've discovered relating to DevOps
menu:
    main: 
        weight: -90
        params:
            icon: adjustments-heart
toc: true
---
# Useful Powershell things #

  ```
  Start-Sleep -Seconds 10
  ```

## Get the date ##
  ```
  Get-Date -Format F
  ```

## Append stuff to a file ##
  ```
  "Write this line" | Add-Content -Path D:\log.txt
  ```

## Combine ##
  ```
  Get-Date -Format F | Add-Content -Path D:\log.txt
  ```

## Test File Exist ##
```Powershell
$oFile # New-Object System.IO.FileInfo $Path
  if ((Test-Path -Path $Path) -eq $false) {
    Write-Host "not exist"
    return $true
  }
```

## Test Can Get Lock ##
```Powershell
  try {
      $oStream # $oFile.Open([System.IO.FileMode]::Open, [System.IO.FileAccess]::ReadWrite, [System.IO.FileShare]::None)
      if ($oStream) {
        $oStream.Close()
      }
    Write-Host "not locked" 
  
  } catch {
      Write-Host "locked" 
      # file is locked by a process.
      return $false
  }
```

# Trace Through Logs on *nix #


If they are zipped you can:

```
gunzip -c [zipped logfile] | less
```

while in less, you can press / and type strings to search for. Press "n" to go the next line/screen and  Shift-N to go the previous screen. This way you can see the context.

if you aren't sure what log file to look in use:
```
grep [search terms] [log file] and see if it returns anything.
```

# How to find disk usage in Linux (and free some) #
## Finding large folders ##

As detailed on, https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux
```
# U.S.
sudo du -h . | grep '[0-9\.]\+G'
# Others
sudo du -h . | grep '[0-9\,]\+G'
```

or put a desired directory in place of the dot of course.

## Another way ##
```
du -h --max-depth=1
```

## Check logs sizes and log rotate if possible ##
```
ls /var -l -h
cd /etc/logrotate.d
sudo logrotate -fv /etc/logrotate.d/<file name>
```

If you get something like:
```
error: skipping "/var/log/mail.log" because parent directory has insecure permissions 
(It's world writable or writable by group which is not "root")
 Set "su" directive in config file to tell logrotate which user/group should be used for rotation.
```

Follow instructions:
* https://askubuntu.com/questions/695999/var-log-syslog-not-rotating
* https://support.microfocus.com/kb/doc.php?id#7005219 (or the owner of /var/log)


## Clear old packages ##
```
sudo apt-get autoclean
sudo apt-get autoremove
```
