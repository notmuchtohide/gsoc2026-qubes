---
title: Flatpak Support
weight: 7
next: settings
---

Flatpak has become a popular format and Gnome Software officially supports it. With the proxy change mentioned before, flatpaks work, but some nuances exist depending on the template.

## Fedora Templates
In Fedora templates, flatpaks come with an fedoraproject.org "remote", which makes it already possible to search for and install flatpaks.

## Debian Templates
Debian, by contrast, provides no default remote. In practice this means that users need to install add a "remote" to
be able to install Flatpak.

---

{{< cards cols="1" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/668 title="Pull Request" icon="code" >}} {{< /cards >}}