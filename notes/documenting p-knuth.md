---
id: v8ay60viiedly293nqkmfl6
title: documenting project-knuth
desc: ''
updated: 1689007384600
created: 1687939612373
---

`project begin date: Jan 04, 2022`  
`project end date: Indefinite`  
`completion rate: 50%`  
`success rate: 40%`  
`remarks: difficult; work in progress`

- Nuggets:
  - [[inorder traversal]], [[preorder traversal]], [[postorder traversal]] are all [[depth-first]]-ish, very unlike [[level-order traversal]] which is more [[breadth-first]]-ish
  - [[postorder traversal]] is strictly bottom-up. [[inorder traversal]] is slightly bottom-up. [[preorder traversal]] is strictly top-down.

- [[why learn algorithm design]]?
- [[what makes algorithm design troublesome but fun]]?
- How do you remember the wandering of thought processes that went into implementing the code for an algorithm? Even after months of implementing the code? Especially when you don't have all the time to practice?
  - For example, See [Leetcode 5, Longest Palindromic Substring]() & Leetcode 647, Palindromic Substrings.
- Write down your thought process when thinking about a solution for problems. (You actually shouldn't do this)
- See [[using Anki to think about algorithm design problems]].
  - [[are you not cramming code?]]---Oh no, actually not.
- Some algorithms become more Interesting because it is clear how they are very practically useful.
  - (See Sean Parent and `std::rotate` in [C++ GoingNative 2013](https://www.youtube.com/watch?v=W2tWOdzgXHA&t=2396s)).
- Algorithms that easily become a part of you (because they are simple? or their problem statement is straightforward? or the solution is memorable?)
  - Linked List: "_Design an algorithm that, given a pointer to the head of a linked list, returns a pointer to the element at the middle of the list_", [Leetcode Link](https://leetcode.com/problems/middle-of-the-linked-list/)
  - Bit-shifting, Adhoc: "_Design an algorithm that, given a non-empty array of integers where every integer appears twice except for one integer, returns the value of that one integer_", [Leetcode Link](https://leetcode.com/problems/single-number/)
  - Breadth-first search
  - Depth-first search
- Restate problem statement for algorithms in your own words (i.e., compress them)
  - For example, despite the long plot for the problem in [Leetcode 198 - House Robber](https://leetcode.com/problems/house-robber/), the task is basically to _design an algorithm that makes a selection of numbers in an array such that the sum of the selected numbers is maximum but adjacent numbers cannot be selected_.
  - A compressed statement then is; _select maximum sum of non-adjacent numbers from given array_.
- It is usually the case that it is the thought process towards a solution for a problem that one would want to remember. This is most times difficult to do for non-simple problems.
- It is also important to understand that algorithms designed with the technical interview process in mind are not in their final form. They could be modified into shorter and easier-to-think-about code by employing the programming language's standard library. Employing this standard algorithms library is a skill.
  - For example... "_Design an algorithm that, given the head of an unsorted linked list of integers, returns the head to the linked list sorted using insertion sort_"
  - To solve this, if the input is not a linked list but an array, one could go on and implement the insertion sort procedure. But it is usually better to employ standard lbrary algorithm. The algorithm below is an implementation of the insertion sort procedure on an array, making use of the `std::rotate`, `std::upper_bound`, and `std::next` algorithms in c++.

```cpp
for(auto i = start; i != end; i++){
  std::rotate(std::upper_bound(start, i, *i), i, std::next(i));
}
```
- coding problems are puzzles you solve by thinking/tinkering first, without code. after you've got the solution, you translate the idea you've got into code. the most useful/transferrable learning comes in this stage.
  - curiously, there's no way to accurately decouple the puzzle-solving process from the translation process because you inevitably think in code. you think in the affordances of your programming language; "is there a way to do this easily, with a few characters of code in python? etc" the two are conceptually separate and yet bound.
  - [Leetcode problem 2551](https://leetcode.com/problems/put-marbles-in-bags/) (Put Marbles in Bags) illustrates this
- it is best to "remember" the outline of the (coded) solution to each problem—which is easier to do when you actually understand the solution—so that it is easier to think about a solution for related problems which (by definition) should build upon (or be similar to) the coded solution for the initial problem.
  - The coded solution for the [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem is similar to that of [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/) such that if the former is solved before the latter and the solution remembered, it is easy to implement the solution for the latter since relatively little thinking/figuring-out will be required.
