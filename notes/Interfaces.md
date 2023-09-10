---
id: myi5w5hqehiuvd65iyisdu1
title: Interfaces
desc: ''
updated: 1694369787629
created: 1688658911947
---

### Physical UI
- [[thumbstick]]
- [[button]]
### Digital UI Libraries
[[Platforms]]
#### [[Ant Design]]
#### Trying out [Radix UI](https://www.radix-ui.com/)  
- What exactly does it offer?
  - _'Radix Websites'_ do have that [[iOS look and feel]] (probably just due to the font? (`"Untitled Sans"`, `apple-system`, `BlinkMacSystemFont`, `Segoe UI`, etc.)). But is that what users get out-of-the-box once they import and begin using Radix?
    - Not quite;
      - [from the list of Case studies on the official Radix Website](https://www.radix-ui.com/primitives/case-studies), although [Vercel](https://vercel.com/), [CodeSandbox](https://codesandbox.io/), [Composer](https://www.composer.trade/), and [Compound](https://withcompound.com/) are quite similar in style, [Teamflow](https://www.teamflowhq.com/), [Atom](https://atomlearning.com/), etc., manage to be, yet, 'different'.
  - Following through with _Implementing a Popover_ demo on the [Getting Started page](https://www.radix-ui.com/primitives/docs/overview/getting-started),
    - This is what a user gets on importing & using the Popover primitive:
      - ![radix-popover-demo-result-1](/assets/images/radix-popover-demo-result-1.png)
        - onclick:/assets/images/.png
        - ![radix-popover-demo-result-2](/assets/images/radix-popover-demo-result-2.png)
    - The JS code:
      - ![radix-popover-demo-jscode](/assets/images/radix-popover-demo-jscode.png)
    - The CSS:
      - ![radix-popover-demo-csscode](/assets/images/radix-popover-demo-csscode.png)
    - The number of styles is still a lot (I had the thought that even without a lot of styles, that [[iOS look and feel]] should still be preserved. This is wrong. So, [[what does Radix &co. do?|Ant Design]])
    - It is quite clear though that it is a lot of work if not impossible to satisfactorily implement a Popover with bare CSS from scratch. Radix and other UI libraries offer that.
    - Without the CSS, this is what Radix offers (the fllwg is from the CandSandbox, hence the slight change in bckgnd):
      - ![radix-popover-demo-withoutcss-1](/assets/images/radix-popover-demo-withoutcss-1.png)
        - onclick:
        - ![radix-popover-demo-withoutcss-2](/assets/images/radix-popover-demo-withoutcss-2.png)
  - Radix is faster than [[Ant Design]]?



Misc.
- _An awesome work: https://rauno.me/craft, https://interfaces.rauno.me/_
- https://pages.cpsc.ucalgary.ca/~saul/581/presentations/06-physical-user-interfaces/581-physical-user-interfaces.pdf
- https://universaldesign.ie/technology-ict/archive-irish-national-it-accessibility-guidelines/smart-cards/smart-card-guidelines/physical-user-interface/
