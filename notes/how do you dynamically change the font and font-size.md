---
id: 6mxdmp3neuhuxzugon2bpzz
title: how do you dynamically change the font and font-size
desc: ''
updated: 1691872343371
created: 1687169675276
---

To style a Codemirror editor, the desired styles/themes have to be injected into the EditorView.

This is a sample theme that sets (on the editor), a fontsize, adds border, sets font-family, etc... 

```javascript
const testTheme = EditorView.theme({
  "&": {
    fontSize: "14pt",
    border: "1px solid #c0c0c0"
  },
  ".cm-content": {
    fontFamily: "Menlo, Monaco, Lucida Console, monospace",
    minHeight: "200px"
  },
  ".cm-gutters": {
    minHeight: "200px"
  },
  ".cm-scroller": {
    overflow: "auto",
    maxHeight: "600px"
  }
});
```
Which is injected alongside other themes as an extension in the `EditorState.create` method:

```javascript
const startState = EditorState.create({
  doc: props.initialDoc,
  extensions: [
    basicSetup,
    keymap.of(defaultKeymap),
    markdown({
      base: markdownLanguage,
      codeLanguages: languages,
      addKeymap: true
    }),
    oneDark,
    testTheme,
    EditorView.lineWrapping,
    EditorView.updateListener.of(update => {
      if (update.changes) {
        onChange && onChange(update.state)
      }
    })
  ]
})
