---
templateKey: blog-post
title: How to import an AWS AppSync GraphQL Schema to PostMan
date: 2020-10-07T14:55:09.618Z
description: PostMan does not yet integrate with directly with AWS AppSync
  GraphQL introspection, but you can export/import the schema with a little
  tooling.  By doing so, PostMan will provide some typeahead and validation as
  you enter GraphQL queries.
featuredpost: true
featuredimage: /img/postman-graphql.png
tags:
  - aws appsync graphql import postman
---
## Prereqs

* [Node.js](https://nodejs.org)

## Export from AWS AppSync

1. Locate and make note of the AppSync API URL and authentication requirements.  Generally, this can be found in the AWS AppSync Console.
2. Install [get-graphql-schema](https://www.npmjs.com/package/get-graphql-schema)
3. In a terminal, enter something similar to the following.

   > NOTE: your required authentication headers may vary!

   ```
   get-graphql-schema \
   --header X-API-KEY=MY-API-KEY MY-API-URL \
   > schema.graphql
   ```

## Import to PostMan

1. In Postman, open the **APIs** tab.
2. Select **+ New API**
3. Complete **Name** **Version**
4. For *Schema type*, Select **GraphQL**
5. Use **Select File** to select the file exported file `schema.graphql`

## Use the GraphQL Schema

1. Create a new request
2. Under the **Body** tab, select **GraphQL**
3. In the dropdown, select the newly imported GraphQL schema.
4. Enjoy the typeahead and validation!

