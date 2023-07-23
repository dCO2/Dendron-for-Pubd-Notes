---
id: c0f7phx1ur5l65pfs2aei3b
title: refactor old notes
desc: ''
updated: 1690137563354
created: 1689805087708
---

- Big notes violate the guiding principle that notes should actually be atomic. (See [[notes should be atomic]])
    - Notes should not contain sets of information.
    - If not, they become difficult to revise and then, boring
    - Eventually, the big notes become stale.
    - You revise them but do not actually _see_ them.
- Stale notes on the hand, violate the guiding principle that notes should be in motion. (See [[SRS is not a bucket SRS is a pipe]])
- What you want to do is creatively split the note into smaller "revisible" bits. If this is not possible, then delete it.
- That is, when you come across a stale note during your revision session, you should add new questions (i.e, notes) about each of the sets of information in the question and answer pair of the old note.
- For example, the following note is a question that asks too many "things" at once:
![anki-refactor-stale-notes-example-ramanujan](/assets/images/anki-refactor-stale-notes-example-c%2B%2Bramanujan.jpg)
- Where the answer is a piece of code:
![anki-refactor-stale-notes-example-ramanujan-2](/assets/images/anki-refactor-stale-notes-example-c%2B%2Bramanujan-2.jpg)
- To answer the question, one would have to come up with an initial pseudocoded bruteforce solution to the problem, analyze the initial solution, make improvements or explore another approach to solving the problem, and then code it up. That is a lot to think about during a 1hr review session.
    - Sometimes, it is okay to create nonatomic notes (See [[notes should be atomic]]) when you are in a hurry and will attend to the note later.
- To refactor such a stale & old note, on Anki, you can `Forget` that particular note. What this does is it makes the note appear in review sessions as if it was newly added. (See [[using anki feedback to make ideas salient]])
    - Once this is done, for the example of a stale note above, notes such as "_How can cubes of numbers be generated when attempting to generate the ramanujan numbers with C++?_", or "_If you are given a set of cubes, how to you obtain pairs that sum to...?_" etc.. can be newly created and properly tagged/linked.
