---
title: Disable Updates and Upgrades
weight: 2
next: 
---

{{< cards >}}
  {{< card 
    title="Upgrades"
    image=/images/banner.png
    subtitle="This banner would encourage users to upgrade Fedora via Gnome Software when a new version is available."
    tag="Fedora"
    tagColor="red"
  >}}
  {{< card 
    title="Updates"
    image=/images/updates_tab.png
    subtitle="Gnome Software had a dedicated page to manage updates and would send notifications when updats are available."
  >}}
{{< /cards >}}


{{< callout type="error" >}}
  Updates and updates didn't work in Qubes as they required Gnome Software itself to be able to restart the system, which is not possible.
{{< /callout >}}

## Solution
Updates and upgrades were disables via gsettings, by overriding ```org.gnome.software allow-updates``` to ```false```.

---

{{< cards cols="1" >}}
  {{< card title="Summary" icon="clipboard-list" subtitle="Updates and upgrades via Gnome Software were disabled and Qubes native tools should be used instead." >}}
{{< /cards >}}

{{< cards >}} {{< card link=https://github.com/QubesOS/qubes-issues/issues/10984 title="Issue" icon="github" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/664 title="Pull Request" icon="code" >}} {{< /cards >}}