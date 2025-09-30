---
title: Ida Free with efiXplorer
description: Just so you know ida sdk was open sourced released this september, with binarly's efiXplorer developed in C++. This allows us to use the plugin in Free version of Ida.
date: 2025-09-30 11:00:00 +0200
categories: [Fyi, Tools]
tags: [idafree, ida, idasdk, analysis, efi, efixplorer, firmware]
pin: true
---

---
***
## Info
Ida Free has just became more powerful with Binarly's efiXplorer Ida plugin. Coupling efiXplorer with Ida Free's online decompiler support while limited to x86 and x64 decompilation, it provides plenty enough capability for a reverse engineer to analyze efi firmware, especially analysing malicious efi.

The [efiXplorer Build](https://github.com/binarly-io/efiXplorer/wiki/Build-instruction-and-installation) is pretty straight forward. I build mine using the CMAKE instruction.

Here is a screenhot of blacklotus efi under Ida Free and efiXplorer Plugin:
![idafreeimg](/assets/post/2025/09September/ida/idafree_efiXplorer.png)

> The loader may not work, this is due to Ida Free being limited to PE/ELF/MACHO, just continue loading the firmware, once loaded run the efiXplorer plugin.
{: .prompt-tip }

## [Reference:]
- https://hex-rays.com/blog/open-sourcing-ida-sdk 
- https://github.com/binarly-io/efiXplorer