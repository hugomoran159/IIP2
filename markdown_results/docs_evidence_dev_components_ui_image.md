[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Image](https://docs.evidence.dev/components/ui/image)

# Image

Note that you can also use [markdown syntax for images](https://docs.evidence.dev/reference/markdown#images). This component is useful when you need to customize the dimensions or styling of the image.

The `Image` component allows you to add responsive and styled images to your markdown pages. This component is useful for embedding images with optional alignment, width, and height settings, and includes accessibility features through the description attribute.

## [Examples](https://docs.evidence.dev/components/ui/image\#examples)

### [Custom size](https://docs.evidence.dev/components/ui/image\#custom-size)

preview

code

![Sample placeholder image](https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png)

```text-sm markdown
<Image
    url="https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png"
    description="Sample placeholder image"
    height=80
/>
```

### [Aligned Left](https://docs.evidence.dev/components/ui/image\#aligned-left)

preview

code

![Sample placeholder image](https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png)

```text-sm markdown
<Image
    url="https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png"
    description="Sample placeholder image"
    height=80
    align="left"
/>
```

### [With Border & Custom Padding](https://docs.evidence.dev/components/ui/image\#with-border--custom-padding)

preview

code

![Sample placeholder image](https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png)

```text-sm markdown
<Image
    url="https://raw.githubusercontent.com/evidence-dev/media-kit/refs/heads/main/png/wordmark-gray-800.png"
    description="Sample placeholder image"
    height=80
    border=true
    class="p-4"
/>
```

## [Options](https://docs.evidence.dev/components/ui/image\#options)

[url](https://docs.evidence.dev/components/ui/image#props-url)

Required

The URL of the image.

[description](https://docs.evidence.dev/components/ui/image#props-description)

The description of the image for accessibility purposes.

[width](https://docs.evidence.dev/components/ui/image#props-width)

The width of the image (in pixels)

Options:number

[height](https://docs.evidence.dev/components/ui/image#props-height)

The height of the image (in pixels)

Options:number

[border](https://docs.evidence.dev/components/ui/image#props-border)

Whether to display a border around the image

Options:

true false

Default:false

[align](https://docs.evidence.dev/components/ui/image#props-align)

The alignment of the image

Options:

center left right

Default:center

[class](https://docs.evidence.dev/components/ui/image#props-class)

Pass custom classes to control the styling of an accordion item. Supports [tailwind classes](https://tailwindcss.com/).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/image/index.md)