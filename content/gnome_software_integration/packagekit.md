---
title: Fixing PackageKit
weight: 1
next: 
---

PackageKit is called by Gnome Software (and KDE Discover) for managing DEB and RPM repos. However, it was not working correctly in Qubes.

## Problems found

### 1. Internet connection
PackageKit checks for internet connection using [glib's default network monitor](https://github.com/PackageKit/PackageKit/blob/f3c049c28b12d68ac1913716f7ec13c82fd59aef/src/pk-backend.c#L856-L861) (NetworkManager) and was reporting that the network was offline in both Debian and Fedora templates.

#### Fedora vs. Debian
On Fedora, PackageKit was working despite that, as it has a code path to work when it [is offline](https://github.com/PackageKit/PackageKit/blob/b864c3a/backends/dnf5/dnf5-backend-utils.cpp#L112). However, as it was always working offline, it was not getting the latest updates and it was impossible to use every feature.

On Debian it was not working, getting the error message ["Cannot download packages whilst offline"](https://github.com/PackageKit/PackageKit/blob/f3c049c28b12d68ac1913716f7ec13c82fd59aef/backends/apt/pk-backend-apt.cpp#L515).

#### Previous work

Some workarounds were created to make NetworkManager believe there is a network to manage ([example 1](https://gitlab.gnome.org/GNOME/gnome-software/-/work_items/2336) , [example 2](https://cockpit-project.org/faq#error-message-about-being-offline)). However, these solutions could also affect other system components.

#### Fix

In theory, it would be possible to select a different network monitor using the environment variable `GIO_USE_NETWORK_MONITOR` and setting it to `base`, which would report it as being online in templates. This is exactly what was done for [Gnome Software in Qubes](https://github.com/marmarek/qubes-core-agent-linux/commit/331e757425f2316ee6665a425d2f6b5bf6eda564#diff-57da99e402c18a99174019ab5b82dd29b4cacfb04073ca2ab99bc9afbdf4da67R1). However, in practice it seems that PackageKit is ignoring those environment variables, leading to the next problem.

### 2. Keep environment
On one hand, PackageKit clears the environment. On the other hand, pkcon can't inform PackageKit about environment variables inserted in the terminal, so the prior solution wouldn't work.

#### Fix
However, `packagekitd` has a `–-keep-environment` argument to "Don't clear environment on startup". 


In the past this could also be set in `PackageKit.conf`, but it is not possible anymore.


## Final solution
Set the file `/usr/lib/systemd/system/packagekit.service.d/30_qubes.conf` with:

```
[Service]
Environment='GIO_USE_NETWORK_MONITOR=base'
ExecStart=
ExecStart=/usr/libexec/packagekitd --keep-environment
```

This way, the environment variable `GIO_USE_NETWORK_MONITOR=base` is set when starting the packagekit systemd service, reporting it as online and the `packagekitd --keep-environment` argument ensures the environment is not cleaned.

{{< callout >}}
**With these fixes, it is possible to...**
- ✅ Install software using PackageKit in Debian
- ✅ Correctly install software using PackageKit in Fedora
- ✅ Install software from DEB or RPM repos in Gnome Software
- ✅ Install software from DEB or RPM repos in KDE Discover

{{< /callout >}}

---

{{< cards >}} {{< card link=https://github.com/QubesOS/qubes-issues/issues/10954 title="Issue" icon="github" >}} {{< card link=https://github.com/QubesOS/qubes-core-agent-linux/pull/659 title="Pull Request" icon="code" >}} {{< /cards >}}