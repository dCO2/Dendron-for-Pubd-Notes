---
id: 96uafepnjg67x3urkpe7hbs
title: documenting codeprop
desc: ''
updated: 1693659389317
created: 1687165621232
---

While working on some app I cannot remember, I had a brief thought of explaining my thought process as I wrote the app. I wanted to show just how the constraints and processes in the interface of an app is specified in the web of textual code. One way to do this is to explain, showing the interface and the related snippet(s) of code side-by-side, so I had the thought of finding lazy & quick ways of screengrabbing only code that was in focus.. in the spotlight of the explanation, so that connected but less important code is blurred.

There are existing apps that do this, like [Raycast](https://ray.so/), [Codeshot](https://codeshotapp.com/); But I was curious to understand the engineering that goes into the interface of such an app, so I thought about building mine.

Attempting to build such an app from scratch by applying HTML, CSS and Javascript elements, you'd imagine, yes, a textarea is possibly needed but then you begin to imagine how syntax highlighting will be done, And not just that but also parsing, language-detection, and other (optional) features. If the app is to be useful, it should be able to work with more than one language, and implementing this is not a quick walk in the park for one person.

Fortunately, a library that does this exists. [Codemirror](https://codemirror.net/). The only hiccup is that it is a full-blown text-editor. And, as I see it, the learning curve is steep. By that I mean, to figure out how to implement desire features in your code takes quite some head-racking to do;
- [[how do you dynamically change the font and font-size]]?
- Having set the font, how do you make sure it is responsive on larger/smaller screens... use TailwindCSS?
- How do you implement switching between light and dark themes?
- How do you implement choosing a language?
- How do you implement language auto-detection?
- How do you implement folding a section of code?
- How do you implement blurring code outside highlighted spotlight but keeping that within spotlight sharp/in-focus?

#### [Codeprop is currently deployed to Netlify](https://codeprop.netlify.app/).

### Misc
[[CodeMirror]] 
#### Build a Text Editor
[Build Your Own Text Editor](https://viewsourcecode.org/snaptoken/kilo/) C
[Designing a Simple Text Editor](http://www.fltk.org/doc-1.1/editor.html) C++
[Python Tutorial: Make Your Own Text Editor](https://www.youtube.com/watch?v=xqDonHEYPgA) Python
[Create a Simple Python Text Editor!](http://www.instructables.com/id/Create-a-Simple-Python-Text-Editor/) Python
[Build a Collaborative Text Editor Using Rails](https://blog.aha.io/text-editor/) Ruby
[Hecto: Build your own text editor in Rust](https://www.flenker.blog/hecto/) Rust

