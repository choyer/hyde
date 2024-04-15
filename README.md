> [!NOTE]
> This is my personalized fork of [Zola's port of the Hyde theme](https://github.com/getzola/hyde) originally created by [Mark Otto](https://github.com/mdo) as a [Poole Jekyll Theme](https://github.com/poole/hyde). See the changes I've made in the [Differentia](#differentia) section below.

# hyde
Hyde is a brazen two-column [Zola](https://github.com/getzola/zola) based on the Jekyll theme of the same name that pairs a prominent sidebar with uncomplicated content.

![Hyde screenshot](https://f.cloud.github.com/assets/98681/1831228/42af6c6a-7384-11e3-98fb-e0b923ee0468.png)


## Contents

- [Installation](#installation)
- [Differentia](#differentia)
- [Options](#options)
  - [Sidebar menu](#sidebar-menu)
  - [Sticky sidebar content](#sticky-sidebar-content)
  - [Themes](#themes)
  - [Reverse layout](#reverse-layout)


## Installation
First download this theme to your `themes` directory using one of the options based on your use-case:

### Option 1 - Clone

If you want to manage it as part of YOUR code base, make your own modifications and put it under your own source code management then this is a good choice.

```bash
cd themes
git clone https://github.com/choyer/hyde
```


### Option 2 - Submodule

If you want to be able to easily pull updates from this repo

```bash
cd <Zola root dir>
git submodule add https://github.com/choyer/hyde themes/hyde
```

### Enable the Theme

Enable it in your `config.toml`:

```toml
theme = "hyde"
```


## Differentia

Main differences from the original [Zola port](https://github.com/getzola/hyde) include:

- Sidebar navigation call-out of current active page (like the original Jekyll Hyde theme)
- Combined styles into a single stylesheet
- Privacy focused no tracking or CDN references. Locally hosted webfonts
- Ability to define sidebar subtitle via `hyde_sidebar_subtitle = ""` in main `config.toml`
- Ability to define sidebar subtext via `hyde_sidebar_subtext = ""` in main `config.toml`
- Ability to define sidebar 3rd party social profile links via `hyde_social_links = []` in main `config.toml` ([see example](#social-links-example))
- Ability to show sidebar copyright via `hyde_copyright = true`, define copyright license via `hyde_copyright_license = "licensed under CC BY 4.0"` and define copyright license link via `hyde_copyright_license_link = "https://creativecommons.org/licenses/by/4.0/"`
- Icons via an SVG sprite with [documented workflow](#svg-sprite-workflow)

### Social Links example

3rd party social profile links, displayed as icons within the Sidebar, can be defined in the sites `config.toml` via:

```toml
[extra]
hyde_social_links = [
    {name = "github", url = "https://github.com/choyer"},
]
```

> [!TIP]
> I've included some of the most popular social service icons. To add your own following the instructions provided in the [SVG Sprite Workflow](#svg-sprite-workflow) section.

### SVG Sprite Workflow

> [!WARNING]
> Not fully implemented. Still considering my options and whether using a sprite is the best approach. See [External SVGs that you can style](https://dev.to/javar/external-svgs-that-you-can-style-2a37) and [Which SVG technique performs best for way too many icons?](https://cloudfour.com/thinks/svg-icon-stress-test/)

Icons (social, etc.) can be delivered by a single SVG sprite. A basic set of social service from [Simple Icons ](https://simpleicons.org/) is provided.

To add others simply download additional icons from the [Simple Icons ](https://simpleicons.org/) website or any other svg icon source (e.g. Bootstrap Icons) and place them in the themes `/static/icons/src` directory.

To **generate the SVG sprite** you can either use an online tool like [Fontastic](https://fontastic.me/) or a CLI like [Yesvgmap](https://github.com/Blobfolio/yesvgmap).

To use `yesvgmap`:

`yesvgmap -o static/icons/icons.svg -l themes/hydes/static/icons/src/spritelist.txt`


## Options

### Sidebar menu
Set a field in `extra` with a key of `hyde_links`:
```toml
[extra]
hyde_links = [
    {url = "https://google.com", name = "Google.com"},
    {url = "https://google.fr", name = "Google.fr"},
]
```
Each link needs to have a `url` and a `name`.

### Sticky sidebar content
By default Hyde ships with a sidebar that affixes it's content to the bottom of the sidebar. You can optionally disable this by setting `hyde_sticky` to false in your `config.toml`.

### Themes
Hyde ships with eight optional themes based on the [base16 color scheme](https://github.com/chriskempson/base16). Apply a theme to change the color scheme (mostly applies to sidebar and links).

![Hyde in red](https://f.cloud.github.com/assets/98681/1831229/42b0b354-7384-11e3-8462-31b8df193fe5.png)

There are eight themes available at this time.

![Hyde theme classes](https://f.cloud.github.com/assets/98681/1817044/e5b0ec06-6f68-11e3-83d7-acd1942797a1.png)

To use a theme, set the `hyde_theme` field in `config.toml` to any of the themes name:

```toml
[extra]
hyde_theme = "theme-base-08"
```

To create your own theme, look to the Themes section of [included CSS file](https://github.com/poole/hyde/blob/master/public/css/hyde.css). Copy any existing theme (they're only a few lines of CSS), rename it, and change the provided colors.

### Reverse layout

![Hyde with reverse layout](https://f.cloud.github.com/assets/98681/1831230/42b0d3ac-7384-11e3-8d54-2065afd03f9e.png)

Hyde's page orientation can be reversed by setting `hyde_reverse` to `true` in the `config.toml`.
