---
id: z01wvozxqgirbdm77ijrpck
title: live-watch—dev lesson notes
desc: ''
updated: 1704305480360
created: 1704300101281
---

- add repo license in git terminal
  - just nano a "LICENSE" file. cop-&-paste the license statement.
  - what is the ISC license? (https://github.com/isaacs/node-lru-cache?tab=ISC-1-ov-file)
- center vert & hor
  ```jsx
      <main className="flex flex-col h-screen items-center">
      <div className="flex flex-col my-auto">
        <div className="flex">
          {/* <VideoBox/> */}
          video-box
        </div>
        <div className="flex">
          {/* <CommentBox/> */}
          comment-box
        </div>
      </div>
    </main>
  ```
- using cdn fonts on nextjs
  - [[wasegundotcom]] (adding fonts to specific components in Nextjs)
- in what folder should font asset best be in nextjs?
  - public?
- what is the display key in the LocalFont function for?
  ```jsx
  const cmufont = localFont({
    src: '../public/cmunbmr-webfont.woff',
    display: 'swap',
  })
  ```