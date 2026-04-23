+++
title = 'Updating a fresh Windows 7+SP1 install'
date = 2024-02-05T02:30:19-06:00
+++

**2026 UPDATE**: Use Atak\_Snajpera's [Windows 7 Image Updater](https://forum.videohelp.com/threads/384921-Windows-7-Image-Updater-SkyLake-KabyLake-CoffeLake-Ryzen-Threadripper)

## How to update a fresh Windows 7+SP1 install in 2024

*Mostly taken from http://www.freenode-windows.org/resources/vista-7/windows-update ([archived](https://web.archive.org/web/20220925214048/http://www.freenode-windows.org/resources/vista-7/windows-update))*

Windows 7 Ultimate (SP1) SHA1 hash: `36ae90defbad9d9539e649b193ae573b77a71c83`

## 1. Download rollup updates
First, manually download (but don't install) these updates from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/home.aspx):

1.  [KB3125574](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3125574)
2.  [KB3172605](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3172605)
3.  [KB3020369](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3020369)

## 2. Disable Windows Update

1. Disable the internet connection
2. Disable the Windows Update service (`stop-service wuauserv` in admin PowerShell)
3. Remove cached update files (`remove-item C:\windows\softwaredistribution\WuRedir` in admin PowerShell)

## 3. Install rollup updates

1. Install KB3020369
2. Install KB3172605 and reboot
3. Install KB3125574 and reboot

## 3. Updating via Windows Update

Reconnect to the internet and launch the standard Windows Update program.

Many updates will fail, but if you retry and restart enough, they will eventually succeed.
