---
id: d049v5agaal82wytcmoz2de
title: sql
desc: ''
updated: 1697020517861
created: 1697018682151
---

- If you have a relational database sharded across multiple servers, how do you generate the uniqueid column, if the id automatically increments, in such a way that there are no id collisions?
- inverted index (https://sirupsen.com/napkin/problem-10-mysql-transactions-per-second/)
- define a composite primary key in SQL (https://sirupsen.com/napkin/problem-6)
  - `PRIMARY KEY (FieldID1, FieldID2)`
  - https://stackoverflow.com/questions/1110349/how-can-i-define-a-composite-primary-key-in-sql
- netpin's migration.sql
  - why should you not conceive it as a user having a list of notes & a note having a single user, but instead, a note having a relation to a user? ([[documenting netpin]]) 
  - `CONSTRAINT "User_pkey" PRIMARY KEY ("uid")`
  - `ALTER TABLE`
  - `CREATE UNIQUE INDEX "User_name_key" ON "User"("name");`
  - ```sql
    -- CreateTable
    CREATE TABLE "User" (
        "uid" INT4 NOT NULL DEFAULT unique_rowid(),
        "name" STRING NOT NULL,
        "createdAt" TIMESTAMP(3) NOT NULL DEFAULT CURRENT_TIMESTAMP,
        "expiresAt" TIMESTAMP(3),

        CONSTRAINT "User_pkey" PRIMARY KEY ("uid")
    );

    -- CreateTable
    CREATE TABLE "Note" (
        "nid" INT4 NOT NULL DEFAULT unique_rowid(),
        "rid" INT4 NOT NULL,
        "link" STRING NOT NULL,
        "createdAt" TIMESTAMP(3) NOT NULL DEFAULT CURRENT_TIMESTAMP,
        "expiresAt" TIMESTAMP(3),
        "title" STRING NOT NULL,
        "content" STRING NOT NULL,

        CONSTRAINT "Note_pkey" PRIMARY KEY ("nid")
    );

    -- CreateIndex
    CREATE UNIQUE INDEX "User_name_key" ON "User"("name");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_link_key" ON "Note"("link");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_title_key" ON "Note"("title");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_content_key" ON "Note"("content");

    -- AddForeignKey
    ALTER TABLE "Note" ADD CONSTRAINT "Note_rid_fkey" FOREIGN KEY ("rid") REFERENCES "User"("uid") ON DELETE RESTRICT ON UPDATE CASCADE;
  
  ```
- pass