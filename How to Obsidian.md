[Basic Formatting](https://help.obsidian.md/How+to/Format+your+notes)

 
#Learning #Teaching #Obsidian
# This is a heading 1
## This is a heading 2
### This is a heading 3
#### This is a heading 4
##### This is a heading 5
###### This is a heading 6

*This text will be italic*  
_This will also be italic_

**This text will be bold**  
__This will also be bold__

|Style|Syntax|Example|Output|
|---|---|---|---|
|Bold|`** **` or `__ __`|`**Bold text**`|**Bold text**|
|Italic|`* *` or `_ _`|`*Italic text*`|_Italic text_|
|Strikethrough|`~~ ~~`|`~~Striked out text~~`|~~Striked out text~~|
|Highlight|`== ==`|`==Highlighted text==`|==Highlighted text==|
|Bold and nested italic|`** **` and `_ _`|`**Bold text and _nested italic_ text**`|**Bold text and _nested italic_ text**|
|Bold and italic|`*** ***` or `___ ___`|`***Bold and italic text***`|**_Bold and italic text_**|


```
To embed Code you type ` ` ` 3x tilde without spaces
```
A single line of code can be done with one 'TAB' after e return see example

	single line of code

[[How to Obsidian]] - Back Links

[[How to Obsidian | New Name for Link]] - New Name same link

[Link to How to Obsidian](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax)

- Wikilink: `[[Three laws of motion]]`
- Markdown: `[Three laws of motion](Three%20laws%20of%20motion.md)`
- You can use the vertical bar (`|`) to change the text used to display a link. For example, `[[Internal links|custom display text]]`

[[WikiLink]]
[MarkdownLink](How%20To%20%Obsidian.md)

[[WhatDoesThisDo]]

## Link to a block in a note

A block is a unit of text in your note, for example a paragraph, block quote, or even a list item.

You can link to a block by adding `#^` at the end of your link destination followed by a unique block identifier, for example, `[[2023-01-01#^37066d]]`.

Fortunately, you don't need to know the identifier. When you type the caret (`^`), you can select the block from a list of suggestions to insert the right identifier.

You can also create human-readable block identifiers by adding a blank space followed by the identifier, for example `^quote-of-the-day`, at the end of a block:

```md
"You do not rise to the level of your goals. You fall to the level of your systems." by James Clear ^quote-of-the-day
```

Now you can instead link to the block by typing `[[2023-01-01#^quote-of-the-day]]`.

Block identifiers can only consist of letters, numbers, and dashes.



## [Callouts](https://help.obsidian.md/Editing+and+formatting/Callouts)

> [!note]
> Lorem ipsum dolor sit amet

> [!abstract]
> Lorem ipsum dolor sit amet
Aliases: summary, tldr

> [!info]
> Lorem ipsum dolor sit amet

> [!todo]
> Lorem ipsum dolor sit amet

> [!tip]
> Lorem ipsum dolor sit amet
Aliases: hint, important

> [!success]
> Lorem ipsum dolor sit amet
Aliases: check, done

> [!question]
> Lorem ipsum dolor sit amet

> [!warning]
> Lorem ipsum dolor sit amet
Aliases: caution, attention

> [!failure]
> Lorem ipsum dolor sit amet
Aliases: fail, missing

> [!danger]
> Lorem ipsum dolor sit amet
Alias: error

> [!bug]
> Lorem ipsum dolor sit amet

> [!example]
> Lorem ipsum dolor sit amet

> [!quote]
>Alias: cite


## Nested callouts
You can nest callouts in multiple levels.
> [!question] Can callouts be nested?
> > [!todo] Yes!, they can.
> > > [!example]  You can even use multiple layers of nesting.