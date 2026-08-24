---
title: Open URLs in disposables
weight: 3
next: 
---

It aims to open Gnome Software URLs (project website, donation pages, etc.) in disposables.

This allows the user to check the project website safely before installing apps, while reducing the need for screenshots to recognize the apps in Gnome Software ([qubes-issues#10983](https://github.com/QubesOS/qubes-issues/issues/10983)).

Previously, URLs were opened in offline browsers. However, if Gnome Software had access to the updates proxy (e.g. for Flatpak related actions) it would pass the proxy configurations to the browser and open the URL online.

---

{{< cards cols="1" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/665 title="Pull Request" icon="code" >}} {{< /cards >}}