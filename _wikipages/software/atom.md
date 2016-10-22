---
template: default
title: Atom Text Editor
permalink: software/atom
category: software
---

BC Wiki: Atom Text Editor
=========================

### My Packages

accessible via `apm list --installed --bare`


```
atom-beautify@0.29.13
atom-wrap-in-tag@0.6.0
autocomplete-clang@0.10.0
build@0.65.0
busy@0.7.0
git-plus@5.18.0
highlight-line@0.11.1
highlight-selected@0.11.2
language-ini@1.16.0
language-latex@1.0.0
language-markdown@0.17.0
latex@0.38.1
linter@1.11.18
linter-gcc@0.6.15
markdown-pdf@1.5.0
markdown-preview-plus@2.4.0
markdown-toc@0.4.1
markdown-writer@2.6.1
minimap@4.25.5
minimap-cursorline@0.2.0
minimap-find-and-replace@4.5.1
minimap-highlight-selected@4.4.0
package-list@0.1.2
pdf-view@0.50.0
platformio-ide@1.6.0
platformio-ide-terminal@2.2.0
tool-bar@1.0.1
```

### My Keymap

Access these from 'Application: Open Your Keymap' in fuzzy search.

```
'atom-workspace':
  'ctrl-alt-o': 'unset!'
  'alt-shift-p': 'activate-power-mode:toggle'

'atom-text-editor':
  'ctrl-alt-shift-B': 'unset!'
  'ctrl-alt-a': 'core:select-all'

'atom-text-editor[data-grammar~="latex"]':
  'ctrl-alt-b': 'unset!'
  'ctrl-alt-shift-b': 'latex:build'

'.platform-win32 .editor, .platform-linux atom-text-editor':
  'ctrl-shift-C': 'unset!'
  'ctrl-shift-C': 'editor:copy-path'

'body':
  'ctrl-alt-p': 'unset!'

'atom-workspace atom-text-editor':
  'ctrl-a': 'unset!'
  'ctrl-e': 'unset!'

'atom-text-editor:not([mini])':
  'ctrl-a': 'editor:move-to-first-character-of-line'
  'ctrl-e': 'editor:move-to-end-of-screen-line'
```

### My Snippets

Access these from 'Application: Open Your Snippets' in fuzzy search.

```
'.text.tex.latex':
  'Item':
    'prefix': 'i'
    'body': '\\\\item $1'
  'Fraction':
    'prefix': 'fr'
    'body': '\\\\frac{$1}{$2}$3'
  'Arbitrary Environment':
    'prefix': 'env'
    'body': '\\\\begin{$1}\n\t$2\n\\\\end{$1}'
```

### My Stylesheet

Access these from 'Application: Open Your Stylesheet' in fuzzy search.

```
// customized minimap highlights
.minimap .highlight-selected {
  background: red;
}

// customized minimap cursorline
.minimap .cursor-line {
  background: green;
}

// customize minimap find-and-replace
.minimap .search-result {
  //background: @syntax-result-marker-color-selected;
  background: red;
}
```

### My Bugfixes

As of 2016-10, these changes allow you to follow relative links in the Markdown preview when using the markdown-preview package:

```
edits to ~/.atom/packages/markdown-preview/lib/markdown-preview-view.coffee, line 102:

      'click': (event) =>
        event.stopPropagation()
        @followLink(event)

edits to ~/.atom/packages/markdown-preview/lib/markdown-preview-view.coffee, line 259:

  followLink: (event) ->
    return false if @loading
    if event.target.tagName is 'A' and event.target.protocol is 'file:'
      activeFile = @getPath()
      activeFileDir = path.dirname(activeFile)
      clickedFile = event.target.getAttribute('href')
      clickedPath = path.join(activeFileDir, clickedFile)
      atom.workspace.open clickedPath, {split: 'left'}
```

As of 2016-10, these changes allow you to follow relative links in the Markdown preview when using the non-default markdown-preview-plus package (note that the default markdown-preview package must be disabled!):

```
edits to ~/.atom/packages/markdown-preview-plus/lib/markdown-preview-view.coffee, line 118:

      'click': (event) =>
        event.stopPropagation()
        @followLink(event)

edits to ~/.atom/packages/markdown-preview-plus/lib/markdown-preview-view.coffee, line 288:

  followLink: (event) ->
    return false if @loading
    if event.target.tagName is 'A' and event.target.protocol is 'file:'
      activeFile = @getPath()
      activeFileDir = path.dirname(activeFile)
      clickedFile = event.target.getAttribute('href')
      clickedPath = path.join(activeFileDir, clickedFile)
      atom.workspace.open clickedPath, {split: 'left'}
```

As of 2016-10, these changes allow markdown-pdf to successfully convert Markdown to PDF when using the non-default markdown-preview-plus package (note that the default markdown-preview package must be disabled!):

```
edits to ~/.atom/packages/markdown-pdf/lib/markdown-pdf.js, line 93:

    else if (mdpreview.name === 'markdown-preview-plus') {
      mdpreview.mainModule.copyHtml(cb.write.bind(cb), 200); // copy parsed markdown with maths scaled 200%
    }
```
