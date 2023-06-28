---
id: v8ay60viiedly293nqkmfl6
title: documenting project-knuth
desc: ''
updated: 1687942889011
created: 1687939612373
---

`project begin date: Jan 04, 2022`  
`project end date: Indefinite`  
`completion rate: 50%`  
`success rate: 40%`  
`remarks: difficult; work in progress`


- Why learn Algorithm design?
  - "It is usually the case that when engineers learn algorithm design, they do so not primarily because it is fascinating to think about technical problems but because getting a FANG job is a big motivation. The prospects of getting a FANG job doesn't excite me anymore. I just, now, want to reach back to that initial spark that made me find something really fascinating about the implementation of computer algorithms. The genesis, most of the time is mathematics. The beauty of it. The promise that by understanding some fact deeply, you can see and appreciate its beauty in some other thing."
- What makes Algorithm design troublesome but fun for me?
  - I tend to treat learning a skill like mastering a landscape? And so I depend on categorised paths from easy to hard or linked-lists to graphs that teach specific lessons on how to think about solving random unlabelled problems. This helps with remembering problem solutions so they can be reapplied. But if that categorised landscape is absent, the problem solutions are easy to forget and a new solution, hard to find.
- How do you remember the wandering of thought processes that went into implementing the code for an algorithm? Even after months of implementing the code? Especially when you don't have all the time to practice?
  - For example, See [Leetcode 5, Longest Palindromic Substring]() & Leetcode 647, Palindromic Substrings.
- Write down your thought process when thinking about a solution for problems.
  - Leetcode 985, [Sum Of Even Numbers After Queries](/2022/09/21/sum-of-even-number-after-queries).
  - Leetcode 000, "_Insert title here_"---
- See [[Using Anki to think about algorithm design problems]].
  - [[are you not cramming code?]]---Oh no, actually not.
- Some algorithms become more Interesting because it is clear how they are very practically useful. (See Sean Parent and `std::rotate` in [C++ GoingNative 2013](https://www.youtube.com/watch?v=W2tWOdzgXHA&t=2396s)).
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
- ...