[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Embed](https://docs.evidence.dev/components/ui/embed)

# Embed

Use the `Embed` component to display external content, such as videos, maps, or other embeddable media, within your markdown pages. This component allows you to customize dimensions, add borders, and ensure responsive styling.

## [Default usage](https://docs.evidence.dev/components/ui/embed\#default-usage)

preview

code

Using Build Time Variables to Create Customer Reports - YouTube

Evidence

225 subscribers

[Using Build Time Variables to Create Customer Reports](https://www.youtube.com/watch?v=UiCioBZ5IDU)

Evidence

Search

Info

Shopping

Tap to unmute

If playback doesn't begin shortly, try restarting your device.

You're signed out

Videos you watch may be added to the TV's watch history and influence TV recommendations. To avoid this, cancel and sign in to YouTube on your computer.

CancelConfirm

Share

Include playlist

An error occurred while retrieving sharing information. Please try again later.

Watch later

Share

Copy link

Watch on

0:00

/ •Live

•

[Watch on YouTube](https://www.youtube.com/watch?v=UiCioBZ5IDU "Watch on YouTube")

```text-sm markdown
<Embed
    url="https://www.youtube.com/embed/UiCioBZ5IDU?si=dychrQurRTlhz9DN"
    title="Sample Video"
/>
```

### [Custom size](https://docs.evidence.dev/components/ui/embed\#custom-size)

preview

code

Using Build Time Variables to Create Customer Reports - YouTube

Evidence

225 subscribers

[Using Build Time Variables to Create Customer Reports](https://www.youtube.com/watch?v=UiCioBZ5IDU)

Evidence

Search

Info

Shopping

Tap to unmute

If playback doesn't begin shortly, try restarting your device.

You're signed out

Videos you watch may be added to the TV's watch history and influence TV recommendations. To avoid this, cancel and sign in to YouTube on your computer.

CancelConfirm

Share

Include playlist

An error occurred while retrieving sharing information. Please try again later.

Watch later

Share

Copy link

Watch on

0:00

/ •Live

•

[Watch on YouTube](https://www.youtube.com/watch?v=UiCioBZ5IDU "Watch on YouTube")

```text-sm markdown
<Embed
    url="https://www.youtube.com/embed/UiCioBZ5IDU?si=dychrQurRTlhz9DN"
    title="Sample Video"
    width=800
    height=450
/>
```

### [No border](https://docs.evidence.dev/components/ui/embed\#no-border)

preview

code

Using Build Time Variables to Create Customer Reports - YouTube

Evidence

225 subscribers

[Using Build Time Variables to Create Customer Reports](https://www.youtube.com/watch?v=UiCioBZ5IDU)

Evidence

Search

Info

Shopping

Tap to unmute

If playback doesn't begin shortly, try restarting your device.

You're signed out

Videos you watch may be added to the TV's watch history and influence TV recommendations. To avoid this, cancel and sign in to YouTube on your computer.

CancelConfirm

Share

Include playlist

An error occurred while retrieving sharing information. Please try again later.

Watch later

Share

Copy link

Watch on

0:00

/ •Live

•

[Watch on YouTube](https://www.youtube.com/watch?v=UiCioBZ5IDU "Watch on YouTube")

```text-sm markdown
<Embed
    url="https://www.youtube.com/embed/UiCioBZ5IDU?si=dychrQurRTlhz9DN"
    title="Sample Video"
    border=false
/>
```

## [Options](https://docs.evidence.dev/components/ui/embed\#options)

[url](https://docs.evidence.dev/components/ui/embed#props-url)

Required

The URL of the embeddable content.

[title](https://docs.evidence.dev/components/ui/embed#props-title)

A description or title for the embed, useful for accessibility purposes.

[width](https://docs.evidence.dev/components/ui/embed#props-width)

The width of the embed (in pixels).

Options:numberDefault:100%

[height](https://docs.evidence.dev/components/ui/embed#props-height)

The height of the embed (in pixels).

Options:numberDefault:400

[border](https://docs.evidence.dev/components/ui/embed#props-border)

Whether to display a border around the embed

Options:

true false

Default:true

[class](https://docs.evidence.dev/components/ui/embed#props-class)

Pass custom classes to control the styling of the embed wrapper. Supports [Tailwind classes](https://tailwindcss.com/).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/embed/index.md)