---
id: a1xocljrqxoyx5oqjvwngpa
title: wchr
desc: ''
updated: 1698684466436
created: 1696423706083
---
- W.I.P currently deployed @ https://wchr-one.vercel.app/ (currently inactive)
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
- on ksqlDB's editor
  - create YOUTUBE_VIDEOS stream
    - ```
      CREATE STREAM youtube_videos (
        video_id VARCHAR KEY,
        title VARCHAR,
        views INTEGER,
        comments INTEGER,
        likes INTEGER
      ) WITH (
        KAFKA_TOPIC = 'youtube_videos',
        PARTITIONS = 1,
        VALUE_FORMAT = 'avro'
      );
      ```
- setup producer in python to stream data to ksqldb
  - `producer = SerializingProducer(kafkaconfig)`,
  - `producer.produce( topic="...", key="...", ... )`
  - obtain keys from confluent web ui, keep in kafka config
- on ksqlDB's editor
  - is data streaming in?
    - ```
      SELECT *
      FROM youtube_videos
      EMIT CHANGES;
      ```
  - create YOUTUBE_CHANGES table
    - ```
      CREATE TABLE youtube_changes WITH (KAFKA_TOPIC = 'youtube_changes') AS
      SELECT
        video_id,
        latest_by_offset(title) AS title,
        latest_by_offset(comments, 2)[1] AS comment_previous,
        latest_by_offset(comments, 2)[2] AS comment_current,
        latest_by_offset(views, 2)[1] AS views_previous,
        latest_by_offset(views, 2)[2] AS views_current,
        latest_by_offset(likes, 2)[1] AS likes_previous,
        latest_by_offset(likes, 2)[2] AS likes_current,
      FROM YOUTUBE_VIDEOS
      GROUP_BY video_id;
      ```
  - create TELEGRAM_OUTBOX stream
    - ```
      CREATE STREAM telegram_outbox (
        `chat_id` VARCHAR,
        `text` VARCHAR
      ) WITH (
        KAFKA_TOPIC = 'telegram_outbox',
        PARTITIONS = 1,
        VALUE_FORMAT = 'avro'
      );
      ```
  - create HTTP Sink (from Confluent's Connectors section)
  - stream of table-change events
    - `CREATE STREAM youtube_changes_stream WITH (KAFKA_TOPIC = 'youtube_changes', VALUE_FORMAT='avro');`
  - a stream of table-change events and a stream of outbox-messages bridged with:
    - ```
      INSERT INTO telegram_outbox
      SELECT 
      '6571664148' AS `chat_id`,
      CONCAT(
        'Likes changed! ',
        'From ',
        CAST(likes_previous AS STRING),
        'TO ',
        CAST(likes_current AS STRING),
        '.  ',
        title
      )
        AS `text`
      FROM  YOUTUBE_CHANGES_STREAM 
      WHERE likes_current <> likes_previous;
      ```

