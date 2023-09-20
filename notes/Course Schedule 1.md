---
id: se7z11lj9u73lux14dtjhv9
title: course schedule 1
desc: ''
updated: 1695114723568
created: 1695037431519
---

https://leetcode.com/problems/course-schedule/

- What 'visual tool'/illustration can I use to easily SEE the relationship/pattern between the _dependency graph_ AND any one correct schedule or all the possible correct schedules?
  - Something better than this:
    - ![courseschedule1-img-1](/assets/images/courseschedule1-img-1.png)
      - this is just one instance from all the possible succession of elements that can be made.
      - i need a visual tool that captures all the possibilties in one image.
  - this one is a step in the right direction:
    - ![courseschedule1-img-2](/assets/images/courseschedule1-img-2.png)
  - a DAG (like the one shown below) is not exactly what we need because it is generated once the [[Course Schedule 2]] problem has been solved. Whereas here, we are yet to solve the problem.
    - ![courseschedule1-img-3](/assets/images/courseschedule1-img-3.png) https://en.wikipedia.org/wiki/Tsort
- One solution to this problem is to `return False` if there is any loop in the graph 
