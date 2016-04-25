**Cascading Style Sheets**, or CSS, is a stylesheet language that describes the presentation of an HTML (or XML) document. It describes how elements must be rendered on screen, on paper, or in other media. Although most often used to set the visual style of Web pages and user interfaces written in HTML and XHTML, the language can be applied to any XML document, including plain XML, SVG, and XUL, and is applicable to rendering in speech or on other media. 

CSS is regarded as a cornerstone technology, in that it is used by many Websites to create visually engaging webpages, user interfaces for Web applications, and user interfaces for many mobile applications.

CSS is designed primarily to enable the separation of document content from document presentation, including aspects such as the layout, colors, and fonts. This separation can improve content accessibility, provide more flexibility and control in the specification of presentation characteristics, enable multiple HTML pages to share formatting by specifying the relevant CSS in a separate .css file, and reduce complexity and repetition in the structural content. This separation of formatting and content makes it possible to present the same markup page in different styles for different rendering methods, such as on-screen, in print, by voice (when read out by a speech-based browser or screen reader and on Braille-based, tactile devices. It can also be used to display the Web page differently depending on the screen size or device on which it is being viewed. Readers may also specify a different style sheet, such as a CSS file stored on their own computer, to override the one the author has specified.

In terms of managing Web resources, changes to the graphic design of a document, or hundreds of documents, can be applied quickly and easily, by editing a few lines in the CSS file(s) they use, rather than by changing markup in the documents themselves.

The CSS specification describes a priority scheme to determine which style rules apply if more than one rule matches against a particular element. In this so-called *cascade*, priorities (or *weights*) are calculated and assigned to rules, so that the results are predictable.

The CSS specifications are maintained by the World Wide Web Consortium (W3C). Internet media type, or MIME type, is registered for use with CSS by [RFC 2318](https://tools.ietf.org/html/rfc2318). The W3C operates a free CSS validation service for CSS documents.

## CSS Syntax

### Declaration block

A declaration block consists of a list of *declarations* in braces. Each declaration itself consists of a *property*, a colon (`:`), and a *value*. If there are multiple declarations in a block, a semi-colon (`;`) must be inserted to separate each declaration.

![selector.gif](resources/2B07A7A024F4C1FD23DB0C07D6119EA5.gif)

Properties are specified in the CSS standard. Each property has a set of possible values. Some properties can affect any type of element, and others apply only to particular groups of elements.

Values may be keywords, such as "center" or "inherit", or numerical values, such as 200px (200 pixels), 50vw (50 percent of the viewport width) or 80% (80 percent of the window width). Color values can be specified with keywords (e.g. "red"), hexadecimal values (e.g. \#FF0000, also abbreviated as \#F00), RGB values on a 0 to 255 scale (e.g.`rgb(255, 0, 0)`), RGBA values that specify both color and opacity (e.g. `rgba(255, 0, 0, 0.8)`), or HSL or HSLA values (e.g. `hsl(000, 100%, 50%)`,`hsla(000, 100%, 50%, 80%)`).