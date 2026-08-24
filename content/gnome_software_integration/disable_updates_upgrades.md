---
title: Disable Updates and Upgrades
weight: 2
next: 
---

{{< cards cols="1" >}}
  {{< card 
    title="Fedora Upgrade Banner"
    image=/images/banner.png
    imageStyle="object-fit:cover; aspect-ratio:16/9;"
  >}}
{{< /cards >}}

When a new Fedora version was available it encouraged users to upgrade the system, which wouldn't work.

Updates were already broken as they were done assuming Gnome Software would be able to restart the system, which can't happen in Qubes. Furthermore, Qubes already has native tools for updates that should be used instead.

Due to these issues, updates and upgrades via Gnome Software were disabled.

---

{{< cards >}} {{< card link=https://github.com/QubesOS/qubes-issues/issues/10984 title="Issue" icon="github" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/664 title="Pull Request" icon="code" >}} {{< /cards >}}