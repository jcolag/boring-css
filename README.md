# Boring CSS
A set of CSS files (for me) to use for prototyping

I have something of a dirty secret:  I don't like CSS frameworks.

Now, I don't object to those frameworks in principle.  Especially in many larger projects, the design features often work out well.  But I definitely don't like the added work to use them---adding classes to every element---which function more as vendor lock-in than anything useful.

With the stylesheets in this repository, I want to put together a more straightforward approach, at least for my personal prototypes and other quick projects.  In such work, I don't want to tell the browser that---for example---each button should look like a button.  Instead, I want the browser to take it for granted that the buttons should look like buttons.

## Modularity

As I see it, page styling generally has four broad parts:

 1.  Universal choices,
 1.  The color scheme,
 1.  The design language (which most of us build in an ad hoc manner), and
 1.  Everything that needs customization.

I plan to eventually provide at least one file for each of the first three items.

Currently, `base.css` contains my current set of "universal styles," applying to almost all projects, though it relies on having a color scheme.  You can also find a series of files named `*-color.css` implementing standardized color palettes or at least adaptations of them---Solarized, Nord, etc.---each with light and dark modes that depend on the browser setting.  And you can find files named `*-language.css`, which implement the bare bones of design languages, such as Google's Material Design.

As a result, a web app can load the universal styles, a color palette, and---once they exist---a design language, and have a "good enough" design.  I might not love Nord or Material Design, for example, but using CSS that implements them well at least looks professional enough to not need to worry for a while.

[Try it!](https://jcolag.github.io/boring-css/)

### Caveats

Note that these stylesheets will not implement any design language *fully*, for a few reasons.

 * Not all design language features have native HTML counterparts.  Badges and collections have some great uses, but these styles need to work with any page, so non-standard controls need to become custom code, for the purposes of this project.
 * Many design languages include color and font choices.  Good for them, but I consider those choices more fundamental to application identity.  I also often want to use something like Solarized's color palette for its ease on the eyes more than for product identity.
 * Default icon sets get downloaded externally.  It makes no sense to maintain copies of everything here.
 * I could easily miss an obscure HTML element that I rarely use, or an uncommon interaction.

Like I hinted earlier, this repository doesn't have aspirations far beyond "good enough with minimal work."  If a prototype looks more acceptable than an unstyled page, then the stylesheets have done their jobs.  Make your own badge, or move to a more thorough implementation of the design language.

## Usage

Like any CSS, link the stylesheets from any page headers.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link
      href="./base.css"
      media="screen"
      rel="stylesheet"
      type="text/css"
    >
    <link
      href="./solarized-color.css"
      media="screen"
      rel="stylesheet"
      type="text/css"
    >
    <link
      href="./material-language.css"
      media="screen"
      rel="stylesheet"
      type="text/css"
    >
    <title>Page Title</title>
  </head>
  <body>
  <!-- The rest of the page -->
  </body>
</html>
```

Personally, I would recommend using `base.css` unless you have a different standard.  Then pick one of the color palette stylesheets, such as `html-color.css`, for the least-interesting choice.  Next, pick a design language, such as `material-design.css`.  And then you do...*nothing*.  You do actually need to use HTML controls for their intended purposes, though, plus you'll want to wrap checkbox and radio button text in a `span` element.  Most importantly, since these styles don't come as classes, they shouldn't ever interfere with additional styles.

Regardless, with those three stylesheets in place, developers can add their favorite grid system, fonts, animations, and bespoke styles, as needed.

I'll repeat, though:  If you have the urge to use CSS classes for non-semantic reasons, for whatever reason, then you've probably outgrown the need for a project like this.  If you want an `a` link, an `img`, or a `div` to look like a button, this system will only frustrate you.  I also wouldn't recommend using this for a production application, given that you'll probably need the entirety of a consistent design language, and don't want to run around implementing everything *except* standard HTML widgets.

## Contributing

Please do!  If you want to fix some oversight on my part (I can't possibly have caught every HTML element), a standard palette (provided that you can fill in all fifteen colors for both modes) that I might have overlooked, or implement a design language, I'd greatly appreciate it.  Although, you know the drill:  Be nice to people, and so forth.

