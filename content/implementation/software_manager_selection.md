---
title: Software Manager Selection
weight: 1
next: gnome_software_integration
type: docs

---

The following software managers were evaluated as candidates for working in Qubes templates, based on [previous discussions](https://github.com/QubesOS/qubes-issues/issues/6310).


{{< cards >}}
  {{< card 
    title="dnfdragora"
    image=/images/dnfdragora.png
    imageStyle="object-fit:cover; aspect-ratio:16/9;"
    link=https://github.com/manatools/dnfdragora
  >}}
  {{< card 
    title="synaptic"
    image=/images/synaptic.png
    imageStyle="object-fit:cover; aspect-ratio:16/9;"
    link=https://github.com/mvo5/synaptic
  >}}
  {{< card 
    title="KDE Discover"
    image=/images/kde-discover.png
    imageStyle="object-fit:cover; aspect-ratio:16/9;"
    link=https://apps.kde.org/discover/
  >}}
  {{< card 
    title="Gnome Software"
    image=/images/gnome-software.png
    imageStyle="object-fit:cover; aspect-ratio:16/9;"
    tag="Selected"
    tagColor="blue"
    tagIcon="sparkles"
    link=https://apps.gnome.org/Software/
  >}}
{{< /cards >}}

## Criteria

Each software manager was evaluated against the following criteria.


{{% steps %}}

### Available Package Managers

<table>
  <thead>
    <tr>
      <th>Software</th>
      <th>Distro</th>
      <th>Version</th>
      <th>apt / dnf</th>
      <th>flatpak</th>
      <th>snap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>synaptic</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">0.91.7</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">❌</td>
      <td style="text-align:center">❌</td>
    </tr>
    <tr>
      <td><strong>dnfdragora</strong></td>
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">2.99.4</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">❌</td>
      <td style="text-align:center">❌</td>
    </tr>
    <tr style="background-color:#dcfce7">
      <td rowspan="2"><strong>Gnome Software</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">48.3</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
    </tr>
    <tr style="background-color:#dcfce7">
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">50.3</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">❌</td>
    </tr>
    <tr style="background-color:#dcfce7">
      <td rowspan="2"><strong>KDE Discover</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">6.3.6</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
    </tr>
    <tr style="background-color:#dcfce7">
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">6.7.4</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
      <td style="text-align:center">✅</td>
    </tr>
  </tbody>
</table>

{{< callout >}}
  **Gnome Software** and **KDE Discover** use PackageKit for RPM and DEB repos, but also have integrations for flatpak repos and snap (except Gnome Software in Fedora).
  This makes possible to install most applications in Qubes just using GUI.
{{< /callout >}}

### UX

<table>
  <tr>
    <td><b>dnfdragora</b></td>
    <td style="color:#f4b400; font-size:20px;">★★☆☆☆</td>
    <td style="color:grey; font-size:12px">(better than terminal)</td>
  </tr>
  <tr>
    <td><b>synaptic</b></td>
    <td style="color:#f4b400; font-size:20px">★★☆☆☆</td>
    <td style="color:grey; font-size:12px">(better than terminal)</td>
  </tr>
  <tr style="background-color:#dcfce7">
    <td><b>Gnome Software</b></td>
    <td style="color:#f4b400; font-size:20px">★★★★★</td>
    <td style="color:grey; font-size:12px">(rounded corners)</td>
  </tr>
    <tr style="background-color:#dcfce7">
    <td><b>KDE Discover</b></td>
    <td style="color:#f4b400; font-size:20px">★★★★☆</td>
    <td style="color:grey; font-size:12px">(easy to use)</td>
  </tr>
</table>

{{< callout >}}
  **Gnome Software** and **KDE Discover** were considered considerably more user friendly.
{{< /callout >}}

### Size

<table>
  <thead>
    <tr>
      <th>Software</th>
      <th>Distro</th>
      <th>Version</th>
      <th>Download Size</th>
      <th>Space Needed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>synaptic</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">0.91.7</td>
      <td style="text-align:center">2,121 kB</td>
      <td style="text-align:center">7,975 kB</td>
    </tr>
    <tr>
      <td><strong>dnfdragora</strong></td>
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">2.99.4</td>
      <td style="text-align:center">2 MiB</td>
      <td style="text-align:center">6 MiB</td>
    </tr>
    <tr>
      <td rowspan="2"><strong>Gnome Software</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">48.3</td>
      <td style="text-align:center">9,615 kB</td>
      <td style="text-align:center">39.3 MB</td>
    </tr>
    <tr>
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">50.3</td>
      <td style="text-align:center">59 MiB</td>
      <td style="text-align:center">170 MiB</td>
    </tr>
    <tr style="background-color:#ffe2e2">
      <td rowspan="2"><strong>KDE Discover</strong></td>
      <td style="text-align:center">Debian 13</td>
      <td style="text-align:center">6.3.6</td>
      <td style="text-align:center">148 MB</td>
      <td style="text-align:center">559 MB</td>
    </tr>
    <tr style="background-color:#ffe2e2">
      <td style="text-align:center">Fedora 44</td>
      <td style="text-align:center">6.7.4</td>
      <td style="text-align:center">215 MiB</td>
      <td style="text-align:center">685 MiB</td>
    </tr>
  </tbody>
</table>

{{< callout type="error" >}}
  **KDE Discover** was considered too heavy to be installed in templates by default.
{{< /callout >}}

{{% /steps %}}

---

{{< cards cols="1" >}}
  {{< card title="Summary" icon="clipboard-list" subtitle="Gnome Software was selected as default the Software Manager in Qubes because comparing with the other solutions, it aligns UX, useful repos and an acceptable size. It is very similar to KDE Discover, however it was chosen for being considerably lighter." >}}
{{< /cards >}}