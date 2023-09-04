---
id: 2s5s0oltg02uyq4dl3wnshy
title: React.js
desc: ''
updated: 1693842713612
created: 1693839815837
---

- `useEffect(setup, dependencies?)`
  - [useEffect](https://react.dev/reference/react/useEffect) is a React Hook that lets you [[synchronize a component with an external system]].
  - What is the useEffect "array parameter" used for?
    - for useEffect dependencies. So that useEffect runs again only when any of the variables inside the array changes. If you want useEffect to run once, then you don't need anything inside the array.
  - When does the useEffect in a component run?
    - useEffect runs after rendering the component
  - how do dependencies work?
  - primitive and non-primitive dependencies
  - https://youtu.be/QQYeipc_cik
