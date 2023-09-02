---
id: cqgtfs5prw1scn7xs8h2ojw
title: git internals
desc: ''
updated: 1693582443840
created: 1693555329200
---


- Where exactly is the git repository?
  <details>
  <summary>😎</summary>

  The git repository is actually the hidden `.git` folder

  </details>  

- What is the data model for a directory in git?
  <details>
  <summary>😎</summary>

  tree objects

  </details> 
- What does `git ls-tree` do?
  <details>
  <summary>😎</summary>

  _It lists the contents of a specified tree object._

  "this is a way to look and inspect tree objects and see more information with what's inside them.

  You'll see that there's a few different parts of this tree. First it has the number 100 which means this is a regular regular file. 644 you might recognize recognize this as a UNIX permission you know 644 755 777 like those kinds of things. This is the permissions of the file in the project. So git actually version controls the permissions on disk as well. So if you edit the permissions of a file in your project that's considered a change in git and it will be version controlled.

  Then what type of object does this tree reference? So we're looking at what's inside the tree this is a list of all the items LS so we have one regular file with 6 port permissions which is a blob object and the blob object is referenced by this hash this unique identifier e69d and so on. And then lastly it has the file name.

  And this is very interesting the file name of the file is not stored in the blob object it's stored in the tree. Think about why that might be. What happens if you have multiple files that have the same contents? With this system you're able to have multiplie files with the same contents but get only soars at one time even if they have different file names.

  What happens if you change the name of a file? Should you duplicate that data when you change the name of a file? No. With git all you do is you create a new tree object which has a new file the object in your objects repository that represents the file.

  The blob doesn't change so file name changes don't actually affect the the raw data and so what this means is that we're able to really easily rename files without a high cost so this is what's inside of a tree"

  </details> 
- What does `git commit` do?
  <details>
  <summary>😎</summary>

  _It saves a snapshot of the working directory by creating a tree object in the git repository._

  "So this shows us that when we make a snapshot, when we do git commit, what we're doing is we're creating a moment in time that says this person created a snapshot with this message and that snapshot is represented by this tree.

  A tree represents what your working directory looked like at that point in time of your project. You also see that there's an author here and a committer. This is something about git that confuses people sometimes. The author is the person who actually wrote the code. The committer is the person who saved that change to the repository.

  As git was actually created for Linux kernel development, it's pretty common for somebody to author changes send a patch file to a maintainer and then the maintainer commits it so it allows you to track those two things independently and then you have the message"

  </details> 
- What does `git add` do?
  <details>
  <summary>😎</summary>

  _It takes the files and puts its content into the object folder in the git repository. The name of that file is the hash of the file and some metadata._

  "what it actually did is it it took the file looked at the contents of the file took those contents and put it as a copy into a file in the objects directory which represents a blob which stands for binary large object it's basically just a collection of data blobs don't have names it's just the raw data and then it took that raw data and a little bit of header information like how long the file is what type of object it is and it ran it through the SHA hashing algorithm and after that hashing the hashing algorithm always outputs a 40 character hex kind of output which is in this case e 6 9 te 2 9 dots out dot dot dot all that stuff over there oops if we do this make it a little bit bigger so that's this e 6 9 te whatever this whole line and so it's calculated that hash and then it created a directory in the objects directory called a 6 and then it took the rest of the hash and it used it as the file name and then it stored the raw data which in our case is the empty file so it's a it's a blob object of 0 bytes and that was hashed and that's where it came up with this a 6 thing so what would that what that tells us is that every time you run get add you're actually putting something in your objects directory so that's on your local machine things are being saved but"

  </details>
- ![[git FAQ#^anchor-git-faq-push-commit]]
  - what's the technical reason?
- 
