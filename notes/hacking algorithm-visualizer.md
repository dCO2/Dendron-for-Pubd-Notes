---
id: hxldqh4r60sgbia521qrygx
title: hacking algorithm-visualizer
desc: ''
updated: 1695744827049
created: 1695723344835
---
https://algorithm-visualizer.org/  

- ![algorithm-visualizer-1](/assets/images/algorithm-visualizer-1.png)
- ![Alt text](/assets/images/algorithm-visualizer-2.png)
- [[the directory for the algo-viz looks like this]]
- App's layout:
  - `<ResizableContainer>`
    - `<Navigator>`
    - `<VisualizationViewer>`
    - `<TabContainer`
      - `<CodeEditor>`
  - ![algorithm-visualizer-app-code](/assets/images/algorithm-visualizer-app-code.png)
- how does `<VisualizationViewer>` work?
  - what is `this.root`?
    - ![algorithm-visualizer-thisroot-code](/assets/images/algorithm-visualizer-thisroot-code.png)
    - ![algorithm-visualizer-thisroot-code-2](/assets/images/algorithm-visualizer-thisroot-code-2.png)
    - ![algorithm-visualizer-thisroot-code-3](/assets/images/algorithm-visualizer-thisroot-code-3.png)
    - where is `args` in `command` coming from?
      - `commands` are "visualizing commands"
      - "[**tracers/**](src/core/tracers) interprets visualizing commands into visualization data."
      - the components `Player` and `VisualizationViewer` have the most use of the word `command`
- the `<Player>`:
  - ![algorithm-visualizer-player-code-1](/assets/images/algorithm-visualizer-player-code-1.png)
  - renders this:
    - ![algorithm-visualizer-player-code-2](/assets/images/algorithm-visualizer-player-code-2.png)

