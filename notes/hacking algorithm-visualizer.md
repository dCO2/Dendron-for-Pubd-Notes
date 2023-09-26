---
id: hxldqh4r60sgbia521qrygx
title: hacking algorithm-visualizer
desc: ''
updated: 1695733661049
created: 1695723344835
---
https://algorithm-visualizer.org/  

- ![Alt text](image-1.png) ![Alt text](image-2.png)

- [[the directory for the algo-viz looks like this]]
- App's layout:
  - `<ResizableContainer>`
    - `<Navigator>`
    - `<VisualizationViewer>`
    - `<TabContainer`
      - `<CodeEditor>`
  - ![Alt text](image.png)

- how does `<VisualizationViewer>` work?
  - what is `this.root`?
    - ![Alt text](image-3.png)
    - ![Alt text](image-4.png)
    - ![Alt text](image-5.png)
    - where is `args` in `command` coming from?
      - `commands` are "visualizing commands"
      - "[**tracers/**](src/core/tracers) interprets visualizing commands into visualization data."
      - the components `Player` and `VisualizationViewer` have the most use of the word `command`
- the `<Player>`:
  - ![Alt text](image-6.png)
  - renders this:
    - ![Alt text](image-7.png)

