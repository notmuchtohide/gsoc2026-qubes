---
title: Settings' integration
weight: 8
next: 
---

A button integrated with Gnome Software was added to the `Applications` tab in qubes settings.

{{< cards cols="1" >}}
  {{< card 
    title="Add software button"
    image=/images/gs_installed.png
  >}}
{{< /cards >}}


## Gnome Software installed in template

The `Add Software` button feature will only work if Gnome Software is already installed in the template.

{{< cards >}}
  {{< card 
    title="1️⃣ Add software button enabled"
    image=/images/gs_installed_focus.png
  >}}
  {{< card 
    title="2️⃣ Launching Software Manager"
    image=/images/pressed_focus.png
  >}}
{{< /cards >}}

When pressed, the button automatically launches Gnome Software in the respective template.

### When the Gnome Software window is closed

1️⃣ Applications are automatically refreshed

2️⃣ The new app joins the `All available applications`

3️⃣ The installed app can be easily moved to `Applications shown in App Menu` to make it visible in `Qubes Application Menu`.


## Gnome Software not installed in template

{{< cards >}}
  {{< card 
    title="1️⃣ Add software button disabled"
    image="/images/gs_not_installed_focus.png"
  >}}
    {{< card 
    title="2️⃣ Add software button tooltip"
    image="/images/tooltip_focus.png"
  >}}
{{< /cards >}}

The `Add software` button is disabled, as Gnome Software is not installed. The user is informed about it in the tolltip.

---

{{< cards >}} {{< card link=https://github.com/QubesOS/qubes-issues/issues/6310 title="Issue" icon="github" >}} {{< card link=https://github.com/QubesOS/qubes-manager/pull/460 title="Pull Request" icon="code" >}} {{< /cards >}}