---
id: 3ejaxv4xm6o2psn0du528yw
title: Documenting Netpin
desc: ''
updated: 1687975967602
created: 1686741481395
---

I rushed through a quick app last week within ~10 days in order to learn about the libraries & tools I made use of, including; [[Next-js]], TailwindCSS, Prisma, and [[Ant Design]]. It is a basic notes app, [deployed on Netlify](https://netpin.netlify.app/) and [Vercel](https://netpin-0-1-1.vercel.app/). The app, however, doesn't work in production (i.e., deployment) as it did in development (remark: All API endpoints are currently unresponsive)

_This note (and other linked notes) details & explains the choices I rushed through while building the app and also documents thoughts on alternative choices that might be preferable for cleaner & effective code._

On mobile, the app looks like this:  

![screen-grab of netpin on mobile](/assets/images/image.png)  

...containing 3 sections:
- an header,
- an instruction text,
- a login-input, and
- a createnote-area.  

There is one more section which shows up below the createnote-area when a user logs in and creates a note.  

This was not the initial design though. The initial sketchy design is shown below. It is seen that I had no idea, before-hand, on how exactly to implement any of the sections or components.    

![initial rough prototype for netpin](/assets/images/image-1.png)

The initial intent was to design some quick and simple app to post some text (that eventually expires) to the web, and obtain a shareable link. But I couldn't resist adding more features.

It was cool to make it possible to create persisting notes that can be shared and editted. But to revisit a note in order to edit it, a constraint on who can edit which note had to be implemented. That is, authors (or users) with unique IDs had to be linked to each note. Hence, a login component in the app had to be implemented.

Implementing the login-input (with simple logic and minimal code) was a bit tricky while trying to ensure:  
1. new users select unique names, and  
2. users cannot see other users' notes  

Hence, the need for "existing user" and "new user" checkboxes alongside login. This way, the use of passwords, and all the logic+code that come with it is avoided. (See [[how was login implemented]])

In order to avoid the case where a note is created & a request sent to the create-note API endpoint, the note-card is disabled before a user creates a user-name or before an existing user logs in. (See [[why is the search and note-card area disabled by default]])

[[the directory for the netpin site currently looks like this]]

- [[how was the apps state handled]]
- [[how was the note-card text-input implemented]]
- [[how was login implemented]]
- [[how was search implemented]]
- [[why is the search and note-card area disabled by default]]
- [[how are the user-notes persisted into a database]]


