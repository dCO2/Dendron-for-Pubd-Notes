---
id: 8ep0769ljfznxb1log35znt
title: boxtype
desc: ''
updated: 1707217889755
created: 1706081669853
---

- version 0.0.0
  - ![boxtype-000.png](/assets/images/boxtype-000.png)
- build notes
  - features
  - what data should be in 'appState'?
    - thinking basically:
      - if the app's entire state is in some useState hook:
        - is it right to hold the necesary 'initial state' data in one variable?
          - asin: `const [appState, setAppState] = useState(initialState)`
          - `initialState` = `{...}` an object holding...
      - what is the default App state?
    - screen width, height
    - toast: (on exports & imports)
    - dragged TextFrame
    - resized TextFrame
    - focused TextFrame (frame currently being edited)
    - textframe locked to gutter
      - zoomToFrame
    - selected TextFrame (frame with  the selected highlight. you have to tab into the selected frame to edit it)
    - export Selected Frame
    - export All Frames
    - scrollX, scrollY
    - list of elements
      - list of text-frames
        - content
          - font-size, font-family
          - bold? italic? underline?
          - text-align
        - x, y, width, breadth, z-index
          - if collapsed?
          - collapsedX (boolean)
          - collapsedY (boolean)
    - editmode
      - cursorState
        - frame-pointer? (the cross)
        - text-cursor?
      - events:
        - panning
        - zooming
        - typing
        - shortcuts
          - move cursor diagonal
          - move cursor tab left
          - move cursor tab right
          - move cursor tab up
          - move cursor tab down
          - tab cursor outside text-frame left
          - tab cursor outside text-frame right
          - tab cursor outside text-frame up
          - tab cursor outside text-frame down
    - viewmode
    - exporting?
      - export Selected Frame
      - export All Frames
      - export as svg, png, txt, separate .txts