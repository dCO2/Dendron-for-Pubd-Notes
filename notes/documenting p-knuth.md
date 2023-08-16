---
id: 6t1kh5r5dr6hn6a9rcb76cc
title: documenting p-knuth
desc: ''
updated: 1692203071053
created: 1690796396798
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
- It is usually the case that it is the thought process towards a solution (EDIT: or rather, it is the conditions, dependencies, reasons, intent, hows, whys (why this condition in the for loop), &.c within the code for the algorithm/solution) for a problem that one would want to remember. This is most times difficult to do for non-simple problems or for a beginner.
- It is also important to understand that algorithms designed with the technical interview process in mind are not in their final form. They could be modified into shorter and easier-to-think-about code by employing the programming language's standard library. Employing this standard algorithms library is a skill.
  - For example... "_Design an algorithm that, given the head of an unsorted linked list of integers, returns the head to the linked list sorted using insertion sort_"
  - To solve this, if the input is not a linked list but an array, one could go on and implement the insertion sort procedure. But it is usually better to employ standard lbrary algorithm. The algorithm below is an implementation of the insertion sort procedure on an array, making use of the `std::rotate`, `std::upper_bound`, and `std::next` algorithms in c++.

    ```cpp
    for(auto i = start; i != end; i++){
      std::rotate(std::upper_bound(start, i, *i), i, std::next(i));
    }
    ```
- coding problems are puzzles you solve by thinking/tinkering first, without code. after you've got the solution, you translate the idea you've got into code. the most useful/transferrable learning comes in this stage.
  - curiously, there's no way to accurately decouple the puzzle-solving process from the translation process because you inevitably think in code. you think in the affordances & constraints of your programming language; "is there a way to do this easily, with a few characters of code in python? etc" the two are conceptually separate and yet bound.
  - [Leetcode problem 2551](https://leetcode.com/problems/put-marbles-in-bags/) (Put Marbles in Bags) illustrates this
- it is best to "remember" the outline of the (coded) solution to each problem—which is easier to do when you actually understand the solution—so that it is easier to think about a solution for related problems which (by definition) should build upon (or be similar to) the coded solution for the initial problem.
  - The coded solution for the [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem is similar to that of [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/) such that if the former is solved before the latter and the solution remembered, it is easy to implement the solution for the latter since relatively little thinking/figuring-out will be required.
  - Also for [Number of Islands](https://leetcode.com/problems/number-of-islands) and [Max Area of Island](https://leetcode.com/problems/max-area-of-island/).
- we don't care about puzzles or finding the patterns of algorithm design thinking in our household lives because we don't particularly care about optimization; the data is not fully available at our grasp at any given moment &c. But for companies whose profit or life & death status is dependent on how well they cut their losses, optimization is important.
- I think it is best to play around the solution of an algorithm problem as a beginner (if you don't want to move fast), this way you get a feel of the breadth or landscape of the (mathematical) patterns in the problem.
- (leet)coders tutoring on youtube are not teachers, beginners will get the wrong impression that that [top-down coding] with ease is how problems are solved. ([[on the difficulty of communication]])
  - [this is a good example](https://youtu.be/yiAaGRWdqVA) of a youtuber thinking through a problem?
  - including some from [exponent](https://www.youtube.com/@tryexponent/videos)
- how do you convince yourself with quick proofs that the algorithm you're blindly putting together will compile and give the correct results?
  - this is very important and is one the reasons some problems feel difficult.. they feel tricky because you cannot prove to yourself that so and so step that you envision will be "correct" and you don't eventually foray into that path or you probably couldn't even see it. ([Integer Break](https://leetcode.com/problems/integer-break/))
  - (written after attempting the [Merge Intervals](https://leetcode.com/problems/merge-intervals/) problem)
    - I was too unsure the step I was taking led to a solution

- **_[[backtracking]]_** is retraced recursion ([[thinking non-intuitively about recursion]])
- [[What is the pattern in the way decision trees are used to think about solution to problems]]?
- [[What is the pattern in the code for algorithms that solve backtracking problems]]?
- [[What is the pattern in the repeated work of problems that can be solved using dynamic programming]]?
- It is curious that I have not come across or solved a lot of Simulation problems _(like [Robot Bounded In Circle
](https://leetcode.com/problems/robot-bounded-in-circle/)_ or []()). OR RATHER, I have not primed myself to think about identifying them in interviews. So, I was a bit unsure what step to take when I encountered two simulations problems (which I didn't initially classify) in a GS interview. `August 15th`
  - But it turns out I have solved about 9 of these through Leetcode (_Spiral Matrix II, Game of Life, Fizz Buzz, Baseball Game, Asteroid Collision, Backspace String Compare, Validate Stack Sequences, Shift 2D Grid, Build Array from Permutation_)
- A good problem: _[Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)_
