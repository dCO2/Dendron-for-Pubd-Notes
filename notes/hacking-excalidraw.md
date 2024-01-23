---
id: zgrwx6zhve7q5e1p6d7rugq
title: hacking excalidraw
desc: ''
updated: 1706029078968
created: 1705999869296
---

- implementing scroll in (Alt+R) view-mode
  - 
- implementing display filename (beside the menu button)
  - where is "whatever handles text" supposed to go? (so we understand the existing practices in the codebase)
    - seems similar to these hints under the toolbar
    - what handles the hints?
    - turns out it is `HintViewer` and it is a component on its own
    - a different component handles the view for each of mobile & desktop
      - `MobileMenu` on mobile
      - `LayerUI` in desktop
        - `HintViewer` is child of `Island` but positioned absolute to it
    - turns out the "display filename" could+should also be a component on its own.
    - where will it go then? how do we place it beside menu button?
      - where exactly is the menu button rendered?
      - the main menu button is classNamed "main-menu-trigger" which inside a `<MainMenuTunnel.In>` component
      - so we search for `<MainMenuTunnel.Out>`
      - which turns out to be what we're looking for: `<tunnels.MainMenuTunnel.Out />` inside a `const renderCanvasActions` function
- how is the canvas render?
  - interactive canvas is a React.Memo (`export default React.memo(InteractiveCanvas, areEqual);`)
  - in App.tsx, it is used as a component under: `ExcalidrawActionManagerContext.Provider` > `LayerUI` | `InteractiveCanvas`
- what is tunneled UI?
  - "Digs tunnels for React elements to go in and appear somewhere else!" https://github.com/pmndrs/tunnel-rat
  - see [[engineering responsive ui for complex apps]]

