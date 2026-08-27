---
title: Disable screenshots
weight: 4
next: 
---

The `qubes-gnome-software-plugin` disables screenshots before loading, due to security concerns.

{{< callout type="info" >}}
Previously, in Qubes templates Gnome Software was not displaying screenshots, as it didn't have internet connection. However, when integrating Gnome Software with Qubes, it needed access to the updates proxy for [Flatpak support](../flatpak), causing it to have internet connection and download screenshots.{{< /callout >}}

## Gnome Software Screenshots

Gnome Software screenshots follow [AppStream](https://www.freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-screenshots) to get the metadata for each repository.

### Data type

Appstream [screenshots](https://www.freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-screenshots) can be images or videos, both with restricted formats. Gnome Software supports both images and [videos as screenshots](https://github.com/GNOME/gnome-software/blob/0075f5af2508e19221c183fe192ba7f50847052c/NEWS#L961).


<table>
  <thead>
    <tr>
      <th>Screenshots</th>
      <th>Data type</th>
      <th style="text-align:center; background-color:#dbeafe">Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Image</strong></td>
      <td>PNG [recommended], JPEG, WebP or JXL</td>
      <td style="background-color:#dbeafe">Fedora, Debian and Flathub screenshots displayed in Gnome Software are all PNG.</td>
    </tr>
    <tr>
      <td><strong>Video</strong></td>
      <td> <a href="https://www.matroska.org/">Matroska (.mkv)</a> or <a href="https://www.webmproject.org/">WebM</a> container and use <a href="https://www.webmproject.org/vp9/">VP9</a> or <a href="https://aomedia.org/av1-features/">AV1</a> codec </td>
      <td style="background-color:#dbeafe">Fedora, Debian and Flathub don't have videos in their appstream repos.</td>
    </tr>
  </tbody>
</table>

### Sources
[Screenshots](https://gnome.pages.gitlab.gnome.org/gnome-software/help/C/software-metadata.html#screenshots) are sourced from the following locations:

| Template | Application Sources      | Local appstream software catalog | Image URLs included |
|----------|--------------------------|----------------------------------|---------------------|
| Fedora   | dnf (via packagekit)     | `/usr/share/swcatalog/xml/ `       | http://dl.fedoraproject.org/pub/alt/screenshots/f43/ |
| Fedora / Debian  | Gnome web apps   | `/usr/share/swcatalog/xml/`        | urls related to each app's website  |
| Debian   | apt (via packagekit)     | `/var/lib/swcatalog/yml/`           | https://appstream.debian.org/media/trixie |
| Fedora / Debian  | Flathub (3rd party Flatpak) | `/var/lib/flatpak/appstream/flathub/` | https://dl.flathub.org/media/app/ |

{{< callout type="error" >}}
**Security Concerns**
- In Fedora, screenshots are sourced from an **HTTP** website
- Screenshots from webapps are sourced from each **project website**
- Screenshots are **not cryptographically signed**

{{< /callout >}}

### Security mitigations

Only a few screenshot's security mitgations were found do be addressed by Gnome Software.

{{% steps %}}

#### Checking screenshots [type](https://github.com/GNOME/gnome-software/blob/147fab181c3f4c19b5ff897b8f5c827428cef396/plugins/core/gs-plugin-appstream.c#L222).


#### [URL validation](https://github.com/GNOME/gnome-software/blob/147fab181c3f4c19b5ff897b8f5c827428cef396/src/gs-screenshot-image.c#L736) when downloading screenshots.


#### [GskPixbuf](https://github.com/GNOME/gdk-pixbuf) loading to check if screenshots [are images and are not corrupted](https://github.com/GNOME/gnome-software/blob/147fab181c3f4c19b5ff897b8f5c827428cef396/src/gs-screenshot-image.c#L416).

{{% /steps %}}


## Solution

A simple Gnome Software plugin was created for Qubes integrations, where the `refine_async` plugin function clears screenshots from each application. This way, no screenshot is downloaded and the user can see a "No Screenshots" image instead.

The image below shows what this solution looks like from the user perspective:

<img width="998" height="994" alt="Image" src="https://github.com/user-attachments/assets/7b63a7a8-b0b9-44a1-917a-25e5e9365dc2" />


---

{{< cards >}} {{< card link=https://github.com/QubesOS/qubes-issues/issues/10983 title="Issue" icon="github" >}} {{< card link=https://github.com/notmuchtohide/qubes-gnome-software-plugin/pull/1 title="Pull Request" icon="code" >}} {{< /cards >}}