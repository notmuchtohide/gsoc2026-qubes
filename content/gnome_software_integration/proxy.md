---
title: Proxy in Templates
weight: 3
next: 
---
For Flatpak to be able to work via Gnome Software, the [Qubes updates proxy](https://doc.qubes-os.org/en/latest/user/how-to-guides/how-to-install-software.html#updates-proxy) was required.

As Gnome Software runs Flatpak as a library, the proxy would only be set in Flatpak if it was provided by Gnome Software.

{{< callout type="warning" >}}
  This approach created other problems, which were also addressed:
  1. Gnome Software would [display screenshots](../screenshots).
  2. URLs would be opened in [online](../open_urls_in_dispvms) browsers.
  3. App would be opened with [internet connection](../disable_open).

{{< /callout >}}

---

{{< cards cols="1" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/668 title="Pull Request" icon="code" >}} {{< /cards >}}