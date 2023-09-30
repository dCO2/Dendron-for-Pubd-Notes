---
id: 5nuxybcjbiir99ydklsry3b
title: quadtree
desc: ''
updated: 1696071363315
created: 1695884225673
---

- thoughts on this:
  - as i add the points with the mouseDragged, and the number of points (within the root quadtree) exceeds the bucket capacity, what should i do?
    - yes, i should assign new quadtrees to the root's children, but then, what next?
    - how do you select which 'next' region of the root quadtree to divide?
  - well first off, have you thought about how to obtain the number of points within a region on a 2D plane? that, i think, will come in handy
    - you can sort the list of points by the x-coordinates first, then count (the number of points) up-to the x-coordinate of the region. you should obtain a new set of points.
    - sort this new set of points again by the y-coordinate, then count as above. 
  - this does not work
    - ![creating-subquadtree-1](/assets/images/creating-subquadtree-1.png)
    - ![creating-subquadtree-2](/assets/images/creating-subquadtree-2.png) (this tries to avoid using an `is_quadtree_divided?` boolean; such that if a child quadtree exists is the parent's children array, then it was created/the parent was divided)
- p5js
  - fill(COLOR)
  - translate(X, Y) https://p5js.org/reference/#/p5/translate
  - scale(1, -1) https://p5js.org/reference/#/p5/scale
  - rectMode(RADIUS) https://p5js.org/reference/#/p5/rectMode
  - line https://p5js.org/reference/#/p5/line
  - mouseMoved https://p5js.org/reference/#/p5.Element/mouseMoved
  - mouseDragged https://p5js.org/reference/#/p5/mouseDragged
  - errors
    - `Failed to execute 'postMessage' on 'DOMWindow': The target origin provided ('file://') does not match the recipient window's origin ('null').` https://stackoverflow.com/questions/22194409/failed-to-execute-postmessage-on-domwindow-the-target-origin-provided-does
  - i have forgotten how `draw()` works
    - what's the diff btw these:
      - ![p5-draw-order-1](/assets/images/p5-draw-order-1.png) (last call to recurse doesn't appear)
      - ![p5-draw-order-2](/assets/images/p5-draw-order-2.png) (nothing appears)
      - ![p5-draw-order-3](/assets/images/p5-draw-order-3.png) (both recurse calls superposed)
      - ![p5-draw-order-4](/assets/images/p5-draw-order-4.png) (something shows up)
      - ![p5-draw-order-5](/assets/images/p5-draw-order-5.png) (nothing shows up)
- javascript
  - sort array of arrays by second element in each inner array: `this.allPoints.sort( (pointA, pointB) => pointA[1] > pointB[1] );`
