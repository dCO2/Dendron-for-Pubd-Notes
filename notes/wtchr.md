---
id: a1xocljrqxoyx5oqjvwngpa
title: wchr
desc: ''
updated: 1696508627820
created: 1696423706083
---
- W.I.P currently deployed @ https://wchr-one.vercel.app/
- importing variables from another file?
  - `from .config import config`
- how to handle pagination?
  - python generators
- confluent cloud
  - create `wchr` environment
    - choose region _Madrid (europe-southwest)_
  - create `wchr` cluster
  - create schema registry (type definition for stored data)
    - choose region _Frankfurt ()_
  - set-up ksqlDB
    - choose region?
    - `CREATE STREAM ... (... ...,);`
  - obtain keys, keep in kafka config
- `producer = SerializingProducer(kafkaconfig)`, `producer.produce()`
- 