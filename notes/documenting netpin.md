---
id: 3ejaxv4xm6o2psn0du528yw
title: documenting netpin
desc: ''
updated: 1693823687949
created: 1686741481395
---

I rushed through a quick app last week within ~10 days in order to learn about the libraries & tools I made use of, including; [[Next-js]], TailwindCSS, Prisma, and [[Ant Design]]. It is a basic notes app, [currently deployed on Vercel](https://netpin.vercel.app/). The app, however, doesn't work in production (i.e., deployment) as it did in development (remark: All API endpoints are currently unresponsive) (_**EDIT: The app works in production now**_)

_This note (and other linked notes) details & explains the choices I rushed through while building the app and also documents thoughts on alternative choices that might be preferable for cleaner & effective code._

On mobile, the app looks like this:  

![screen-grab of netpin on mobile](/assets/images/image.png)  

The app is sectioned into 4:
- an header,
- an instruction text,
- a login-input, and
- a createnote-area.  

There is one more section which shows up below the createnote-area when a user logs in and creates a note.  

This was not the initial design though. The initial sketchy design is shown below. It is seen that I had no idea, before-hand, on how exactly to implement any of the sections or components.  

![initial rough prototype for netpin](/assets/images/image-1.png)

The initial intent was to build some quick and simple app to post some text (that eventually expires) to the web, and obtain a shareable link. But I was curious about how extra features in mind will be implemented.

It was cool to make it possible to create persisting notes that can be shared and edited. But to revisit a note in order to edit it, a constraint on who can edit which note had to be implemented. That is, authors (or users) with unique IDs had to be linked to each note. Hence, a login component in the app had to be implemented.

Implementing the login-input (with simple logic and minimal code) was a bit tricky while trying to ensure:  
1. new users select unique names, and  
2. a user cannot see other users' notes  

Hence, the need for the "existing user" and "new user" checkboxes alongside login. This way, the use of passwords, [[and all the logic+code that come with it|Authentication]] is avoided. (See [[how was login implemented]])

In order to avoid the case where a note is created & a request sent to the create-note API endpoint, [[the note-card is disabled before a user creates a user-name or before an existing user logs in|why is the search and note-card area disabled by default]].

- [[how was the apps state handled]]
- [[how was the note-card text-input implemented]]
- [[how was login implemented]]
- [[how was search implemented]]
- [[why is the search and note-card area disabled by default]]
- [[how are the user-notes persisted into a database]]
- [[the directory for the netpin site currently looks like this]]
- how is a link for each note generated?
- how is a POST request handled in next.js?  
- how is a POST request to a DB handled using Prisma in next.js?  
- how is a GET request handled in next.js?  
- how is a GET request from a DB handled using Prisma in next.js?  
- how was the DB schema generated and migrated to the physical database?
- params in nextjs
- PageProps in nextjs

