+++
title = 'Reverse Engineering _Neon Genesis Evangelion: Girlfriend of Steel_'
date = 2026-04-22T20:30:53-05:00
+++

Last year, I started reverse enginering _Neon Genesis Evangelion: Girlfriend of Steel_ with the intention of writing a replacement engine that runs on modern computers.
I ended up losing interest, but not before cracking a few of the game data formats. I'm going to document them here, that way anyone who takes a similar
interest in restoration or modding can have a head start.

The source code of the abandoned project is available here: [fantatech-1776908508.tar.gz](/files/girlfriend-of-steel-re/fantatech-1776908508.tar.gz).
It includes [ImHex](https://imhex.werwolv.net/) patterns and rudimentary decoders for some of the formats described below.

## What game am I talking about?

I actually looked at two different games. I will share the information I know about the 1997 formats, but the primary focus will be on the 2006 version.
VNDB has a good record of all the available ports and translations here: [https://vndb.org/v556](https://vndb.org/v556).

**_Neon Genesis Evangelion: Girlfriend of Steel (1997, PC)_**: This is the original release of the game. It's also the most widely available.
I was able to buy a factory sealed copy on eBay. Surprisingly, you can still mount the ISO and run the ~30 year old binaries on Windows 11. It plays mostly
fine with a [Shift-JIS locale emulator](https://github.com/xupefei/Locale-Emulator).
The chunky bitmap graphics and audio, although charming, are considerably lower quality than in the 2006 version.

**_Neon Genesis Evangelion: Girlfriend of Steel (Special Edition) (2006, PC)_**: Also called _Shin Seiki Evangelion: Koutetsu no Girlfriend Tokubetsu-hen_, is a remake.
It has upgraded sounds and visuals, additional scenarios, and a full-motion video (Cinepak) intro sequence. It's also filled to the brim with DRM that makes it completely
broken on any system that isn't running Windows XP with Direct3D acceleration.
This will only run in VMWare because VirtualBox dropped 3D acceleration support for Windows XP guests.

I have not been able to find a physical copy of the PC version of Special Edition for sale anywhere.
The PSP version is available, but the image resolutions are smaller than those found in the PC version.

Luckily, someone in 2020 found a copy and had the foresight to rip the disc and upload it to the The Internet Archive. This is the raw, original disc; DRM and all:
[https://archive.org/details/ssekngpcredump](https://archive.org/details/ssekngpcredump) - [http://redump.org/disc/74520/](http://redump.org/disc/74520/).

MD5: `536adbefc80a84378b65224fddf122e7` SHA-1: `77a03fb1823cb96189ac50b9afece8930e709c93`

## Defeating the DRM

TODO remember how I did this, then write about it

## Custom file types (1997)

* **BP2**: Image (1997)
* **BP3**: Image (2006)
* **LB5**: Lump file
* **TXT**: Game script
* **ZDF**: Animation data

## Prior work

When reverse engineering the 1997 game executable, I found several strings referencing something called "bmpwaku".
This was the name given to the tiled bitmap rasterizer written by programmer Ritsurō Hashimoto.

A small portion of the source code is still available on his website to this day: [bmpwaku.cpp](http://www.ritsuro.com/prog1/bmpwaku.html).
This wasn't particularly useful, but it was cool to find.

Aside from that, here are the existing tools I looked at:
* [evac010](https://www.vector.co.jp/soft/win95/art/se055672.html): BP2 <-> BMP transcoder, likely written when the game came out in the 1990s.
* [mdukat/EvaGOS\_engine](https://github.com/mdukat/EvaGOS_engine): Includes partial documentation of the game scripting language from the 1997 game.
* [lb5\_decode.c](https://d3suu.neocities.org/EvaGOS_engine/lb5_decode.txt): LB5 unpacker, written by either mdukat or roxfan.
* [Durik256/GOS2-Tools](https://github.com/Durik256/GOS2-Tools): Tools for dealing with files found in Girlfriend of Steel 2. Some overlap.
