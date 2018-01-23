# vscode-reveal

This extension let you display a reveal.js presentation directly from an opened markdown document.

![demo](/images/demo2.0-bis.gif)

## Features

- [Markdown](#markdown)
- [Status bar](#statusbar)
- [Sidebar and navigation](#sidebar)
- [Theme](#theme)
- [Highlight Theme](#highlight)
- [Reveal.js Options](#options)
- [YAML Front Matter](#frontmatter)
- [Open preview on right side](#preview)
- [Open in browser](#browser)
- [Print to PDF](#pdf)
- [Export static Website](#htmlexport)
- [FAQ](#faq)

## <a id="markdown"></a> Markdown

Create revealjs presentation directly from markdown file,
open or create a new file in markdown and use default slide separator to see slide counter change in status bar and title appear in sidebar.

Since Reveal.js use marked to parse the markdown string you can use this in you document: 

- GitHub flavored markdown.
- GFM tables

If you need a sample file you can get it here:  
https://raw.githubusercontent.com/evilz/vscode-reveal/master/sample.md


## <a id="statusbar"></a> Status bar

As soon as your markdown documet has at least two slides, slides counter will appear in status bar on right.

![](/images/statusbar.png)

Clicking on slide counter will launch preview on right, and you can now see local address of express server used to host Reveal presentation.
Clicking on the address will launch presentation in browser.

You can stop express server when you want by clicking on red square.

## <a id="sidebar"></a> Sidebar and navigation

**Now in version 2** you can see list of all your slides on sidebar.
List will show the first line of text it found in the slide, most of the time it will be a title, but it can also be a image ref or something else.

Blue icon is used to show horiontal slide, orange is use for vertical ones.

Clincking on slide name will move the cursor on begining of the slide in the editor.
If the preview is opened it will also show the selected slide on it.  

![](/images/sidebar.png)


## <a id="theme"></a> Theme

reveal.js comes with a few themes built in: 
- Black (default) 
- White 
- League 
- Sky 
- Beige 
- Simple 
- Serif 
- Blood 
- Night 
- Moon 
- Solarized

You can set it using `revealjs.theme` parameter in Vs code config or in the document it-self using front matter.

If you want a custom theme you can do it !
Just add custom style in a css file in same folder that your markdown.

exemple : 
if your file name is `my-theme.css` just add this in the front matter header :

```
---
customTheme : "my-theme"
---
```


Note that you can use both theme and custom theme as same time. Your custom theme will be loaded after to override default revealJS theme.



## <a id="highlight"></a> Highlight Theme

You can use code block in your markdown that will be highlitghted by highlight.js.
So you can configure the coloration theme by setting `revealjs.highlightTheme` parameter of VS Code, or set it using front matter.

```
---
highlightTheme : "other theme"
---
```

Get the theme list here https://highlightjs.org/

## <a id="options"></a> Reveal.js Options


You can customise many setting on for your revealjs presentation.

<table><tr><th>Name</th><th>Description</th><th>Default</th></tr><tr><td><code>revealjs.notesSeparator</code></td><td>Revealjs markdown note delimiter</td><td><code>note:</code></td></tr><tr><td><code>revealjs.separator</code></td><td>Revealjs markdown slide separator</td><td><code>^(
?|
)---(
?|
)$</code></td></tr><tr><td><code>revealjs.verticalSeparator</code></td><td>Revealjs markdown vertical separator</td><td><code>^(
?|
)--(
?|
)$</code></td></tr>
<tr><td><code>revealjs.theme</code></td><td>Revealjs Theme (black, white, league, beige, sky, night, serif, simple, solarized</td><td><code>black</code></td></tr>
<tr><td><code>revealjs.highlightTheme</code></td><td>Highlight Theme</td><td><code>Zenburn</code></td></tr>
<tr><td><code>revealjs.controls</code></td><td>Display controls in the bottom right corner</td><td><code>true</code></td></tr><tr><td><code>revealjs.progress</code></td><td>Display a presentation progress bar</td><td><code>true</code></td></tr><tr><td><code>revealjs.slideNumber</code></td><td>Display the page number of the current slide</td><td><code></code></td></tr><tr><td><code>revealjs.history</code></td><td>Push each slide change to the browser history</td><td><code></code></td></tr><tr><td><code>revealjs.keyboard</code></td><td>Enable keyboard shortcuts for navigation</td><td><code>true</code></td></tr><tr><td><code>revealjs.overview</code></td><td>Enable the slide overview mode</td><td><code>true</code></td></tr><tr><td><code>revealjs.center</code></td><td>Vertical centering of slides</td><td><code>true</code></td></tr><tr><td><code>revealjs.touch</code></td><td>Enables touch navigation on devices with touch input</td><td><code>true</code></td></tr><tr><td><code>revealjs.loop</code></td><td>Loop the presentation</td><td><code></code></td></tr><tr><td><code>revealjs.rtl</code></td><td>Change the presentation direction to be RTL</td><td><code></code></td></tr><tr><td><code>revealjs.shuffle</code></td><td>Randomizes the order of slides each time the presentation loads</td><td><code></code></td></tr><tr><td><code>revealjs.fragments</code></td><td>Turns fragments on and off globally</td><td><code>true</code></td></tr><tr><td><code>revealjs.embedded</code></td><td>Flags if the presentation is running in an embedded mode, i.e. contained within a limited portion of the screen</td><td><code></code></td></tr><tr><td><code>revealjs.help</code></td><td>Flags if we should show a help overlay when the questionmark key is pressed</td><td><code>true</code></td></tr><tr><td><code>revealjs.showNotes</code></td><td>Flags if speaker notes should be visible to all viewers</td><td><code></code></td></tr><tr><td><code>revealjs.autoSlide</code></td><td>Number of milliseconds between automatically proceeding to the next slide, disabled when set to 0, this value can be overwritten by using a data-autoslide attribute on your slides</td><td><code></code></td></tr><tr><td><code>revealjs.autoSlideStoppable</code></td><td>Stop auto-sliding after user input</td><td><code>true</code></td></tr><tr><td><code>revealjs.mouseWheel</code></td><td>Enable slide navigation via mouse wheel</td><td><code></code></td></tr><tr><td><code>revealjs.hideAddressBar</code></td><td>Hides the address bar on mobile devices</td><td><code>true</code></td></tr><tr><td><code>revealjs.previewLinks</code></td><td>Opens links in an iframe preview overlay</td><td><code></code></td></tr><tr><td><code>revealjs.transition</code></td><td>Transition style (none/fade/slide/convex/concave/zoom)</td><td><code>default</code></td></tr><tr><td><code>revealjs.transitionSpeed</code></td><td>Transition speed (default/fast/slow)</td><td><code>default</code></td></tr><tr><td><code>revealjs.backgroundTransition</code></td><td>Transition style for full page slide backgrounds (none/fade/slide/convex/concave/zoom)</td><td><code>default</code></td></tr><tr><td><code>revealjs.viewDistance</code></td><td>Number of slides away from the current that are visible</td><td><code>3</code></td></tr><tr><td><code>revealjs.parallaxBackgroundImage</code></td><td>Parallax background image</td><td><code></code></td></tr><tr><td><code>revealjs.parallaxBackgroundSize</code></td><td>Parallax background size (CSS syntax, e.g. 2100px 900px)</td><td><code></code></td></tr><tr><td><code>revealjs.parallaxBackgroundHorizontal</code></td><td>Number of pixels to move the parallax background per slide</td><td><code></code></td></tr><tr><td><code>revealjs.parallaxBackgroundVertical</code></td><td>Number of pixels to move the parallax background per slide</td><td><code></code></td></tr></table>


## <a id="frontmatter"></a> YAML Front Matter

You can change settings directly in your markdown file using front matter style. You can change all extention settings like this :

```
---
theme : "white"
transition: "zoom"
---
```

> Note do not add `revealjs.` prefix before setting name.


## <a id="preview"></a> Open preview on right side

To display the preview on right side you can :
- click on slide count in status bar
- click split icon in sidebar header
- call command `Revealjs: Show presentation by side`


The preview wil be synchronize with the current cursor position.

## <a id="browser"></a> Open in browser

To display presentation in browser you can:
- click on server address in status bar
- click icon in sidebar header
- call command `Revealjs: Open presentation in browser`


This will try to use Chrome that is the best browser to use for reveal.js presentation, if it can't find it, your default browser will be used.


## <a id="pdf"></a> Print to PDF

To export your presentation to pdf you can:
- click on pdf icon in sidebar
- call the command `Revealjs: Export in PDF`


This will try to launch Chrome or your default browser and launch printing.
Be sure to set print setting correctly:
- No margin
- print background


## <a id="htmlexport"></a> Export static Website

To export your presentation to a static website you can:
- click on html icon in sidebar
- call the command `Revealjs: Export in HTML`


This will try to launch Chrome in headless or your default browser it take about 10sec and then open export folder.

## <a id="faq"></a> FAQ


> Note : First time windows will ask you about firewall. If you open the port for the application, you can see your prensentation remotly.


## Known Issues

Please add issues on github.

