---
id: hi2l7n37cbjxkhvarw9gxrk
title: using Anki to think about algorithm design problems
desc: ''
updated: 1693232970327
created: 1692099748781
---

#### Impetus
- There's not much special about using Anki to think about algorithm problems (aka leetcode practice). The motivation for the use is simply to help remember whatever should be remembered when thinking towards a solution to a problem. "Whatever should be remembered" includes any of; problem statement, constraints, solution, etc.
  - ![[documenting p-knuth#^anchor-what-to-rember]]
  - ![[documenting p-mnemosyne#^anchor-chunked-info]]
  - What is exciting though is the possibilities of designing some cognitive tool that'll help make algorithm design practice **MORE** and even more effective. This **MORE** is possible. How?
- Inquiry: If one is proficient at implementing the solution to a related problem, what can be said about the solution of the initial problem in relation to the solution of the related problem? Will be the solution for the 'initial' be necessarily clunky? Is there a always a simpler solution?
  - _Binary Tree Level Order Traversal_ vs _Binary Tree Right Side View_
  - ![[documenting p-knuth#^anchor-relatedvsinitial]]

#### Methods 
- #todo

#### Journal
- 2021-2022 Era: "Design an algorithm that..."
- 2022 Era: "Restate the _`insert-problem-title`_ problem in your own words..."
- 2022 Era: "How will you solve the..."
- 2023 June Era: "What is the code in the 5th section of the algorithm that solves..."
- 2023 August Era: "How many sections of code are in the algorithm that solves..."
- `August 15th`: Revising cards (i.e., problems, solutions, code) at a frequency of about 30 per day is inefficient strategy on memory. It is too much. You want to reduce the Maximum reviews per day to about 3.
  - To do this, I moved all ~364 cards tagged '`algorithm-design-problems`' to a new deck where the `Options` is correspondingly set.
  - On setting the Maximum reviews per day to about 3, Anki suggests "If adding 2 new cards... ...review limit should be at least 20." VIZ:
    - ![review limit should be at least 20](/assets/images/review%20limit%20should%20be%20at%20least%2020.png)
  - The desired Maximum reviews per day can still be set despite that.
  - Now there are 3 problems I should have working memory of for a couple of weeks before they fully become long-term.
    - The question now is; with the current 'options presets', "If I come across a certain 3-problems on day 1 (today), will I come across the same 3-problem set tomorrow?"
      - How do I set any of `Learning steps`, `Graduating Interval`, `Easy Interval`, `Insertion Order`; `Relearning Steps`, `Minimum Interval`, `Leech Threshold`, `Leech Action`, `Maximum Interval`, `Starting Ease`,  `Easy bonus`, `Interval Modifier`, `Hard Interval`, `New Interval`, so that on day 1 after seeing cards; (_Merge K Lists_, _Subsets_, and _Search a 2D Matrix_ ~+ _Kth Largest Element in an Array_ for example), I still see some of them on day 2 and a new one, even less of them and some more new cards on day 3. So that by the end of week 1, I very rarely see them again.^anchor-anki-aim
  - Something is wrong. I'm stiil seeing more than 3 cards per day from the new deck.
    - At this moment, my _Buffer_ superdeck has a _due decks_ number of 42, but all the subdecks have a total of 23 _due decks_. The diff commes from the new ADP subdeck. It seems the options preset didn't work.
      - The temporary solution is; reduce the Maximum reviews per day for the _Buffer_ superdeck from 1000 to 20.
  - It is day 2 (`August 16th`) and I did not come across the cards from day 1 I was expecting.  
  - (`August 18th`): I have now "buried" the cards that are due tomorrow so that I, instead, come across **ONLY** the required 3(+1) cards I want to keep tabs on.  
  - (`August 20th`): I have to continue burying the unwanted cards to get to see what I want.
  - (`August 24th`): I still haven't figured this out properly yet.
  - (`August 26th`): Status: put on hold.
    - Reason: It is tricky to implement the following while also adding one new card per day
      - ![[using Anki to think about algorithm design problems#^anchor-anki-aim]]
      - I need more knowledge (https://youtu.be/Eo1HbXEiJxo)
  - (`August 28th`): Now I see all the due cards (e.g. as many as 20 per day) and just skip a lot of them.
