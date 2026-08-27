---
title: Disable Opening Apps
weight: 6
next: 
---

The `qubes-gnome-software-plugin` plugin removes the ability to launch apps from Gnome Software, as a mitigation for opening software with internet connection, in templates.

{{< callout type="info" >}}
Previously, in Qubes templates applications were opened without internet connection. However, when integrating Gnome Software with Qubes, it needed access to the updates proxy for [Flatpak support](../flatpak), causing it to pass the proxy configurations to each app and open them with internet connection.{{< /callout >}}

The image below shows what this solution looks like from the user perspective:

<img width="998" height="994" alt="Image" src="https://github.com/user-attachments/assets/7b63a7a8-b0b9-44a1-917a-25e5e9365dc2" />

---

{{< cards cols="1" >}} {{< card link=https://github.com/notmuchtohide/qubes-gnome-software-plugin/pull/1 title="Pull Request" icon="code" >}} {{< /cards >}}