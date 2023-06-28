---
id: dqs1xi7wx1q8xb0urwpzo2l
title: documenting plain-net-lib
desc: ''
updated: 1687946974078
created: 1687943371932
---

In an attempt to learn React with hands-on projects, I built a simple single-page site that uses the Google Books API to obtain a list of books related to a user-selected search-query. The user then is able to add any of the books to a shelf. The app was not built with specific real-world use-case in mind but to test my skill at using React to build basic web functionality.

On desktop, the homepage of the site look like this:

![homepage-pnl](/assets/images/homepage-pnl.png)

A user will have to type in a word or the name of a book in the search bar and then hit the search icon on the far-right, which opens up the searchpage with a list of results, as demoed, with a "car" query:

![demo-searchpage-pnl](/assets/images/demo-searchpage-pnl.png)

Hovering atop the 'action menu' for each card reveals that any of the books can be added to one or all of the shelves in the homepage:

![demo-searchpage-card-pnl](/assets/images/demo-searchpage-card-pnl.png)

Adding a few select books at random, and returing to the homepage by clicking the icon (![homepage-icon-pnl](/assets/images/homepage-icon-pnl.png)), it is seen that the respective shelves have been populated;

![populated-reading-shelf-pnl](/assets/images/populated-reading-shelf-pnl.png)
or also;
![populated-homepage-pnl](/assets/images/populated-homepage-pnl.png)

Each of the books can be moved to a different shelf or deleted as seen (demoed) in the action menu:

![demo-homepage-card-pnl](/assets/images/demo-homepage-card-pnl.png)

There are a few hiccups with functioning of the site. For example,
- it should be impossible to add a book more than once to the same shelf;
- if a book is added more than once, all the instances of the same book should not be moved when one of the instance is moved to another shelf or deleted.
- the UI is not well-responsive for mobile, etc.
