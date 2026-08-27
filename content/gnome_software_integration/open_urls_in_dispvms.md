---
title: Open URLs in disposables
weight: 5
next: 
---

It aims to open Gnome Software URLs (project website, donation pages, etc.) in disposables.

This allows the user to check the project website safely before installing apps, while reducing the need for [screenshots](../screenshots) to recognize the apps in Gnome Software.

{{< callout type="info" >}}
Previously, in Qubes templates URLs were opened in offline browsers.  However, when integrating Gnome Software with Qubes, it needed access to the updates proxy for [Flatpak support](../flatpak), causing it to pass the proxy configurations to the browser and open URLs online.{{< /callout >}}

---

{{< cards cols="1" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/665 title="Pull Request" icon="code" >}} {{< /cards >}}