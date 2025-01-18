# No-SQL-Using-Apache-Casandra
* Create an account on https://accounts.datastax.com/session-service/v1/login
## What is DataStax?
 * DataStax is a company that provides tools and services for managing Apache Cassandra, a powerful NoSQL database.
 * It focuses on making Cassandra more accessible through cloud services, developer tools, and integrations.
* Click on databases tab
  ![image](https://github.com/user-attachments/assets/fa19d5b4-d3f2-498f-a126-4c36ae54fe18)
* Then click on create a new database
 ![image](https://github.com/user-attachments/assets/475fabdb-5946-433e-a49d-c0e963c37c4d)
* Add the information as shown and then click on create 
  ![image](https://github.com/user-attachments/assets/2865f073-8ec7-4d2d-bc7a-ced40410d43f)

- Have patience it takes up to 5mins for the status to turn to active

- To get the token to communicate with the database
- Click on Token in the left corner
- Select Administrator user
  ![image](https://github.com/user-attachments/assets/e578d845-9414-463c-908c-85922fac98f5)
- Copy it and keep it safe

- Click on Connect
  ![image](https://github.com/user-attachments/assets/1ffeb273-8a9a-4b10-bf74-639e58c36a84)
-Scroll down
![image](https://github.com/user-attachments/assets/1885374e-e7c7-4a8a-a3a9-01d4e4162a26)

- Scroll down and click on this link
  ![image](https://github.com/user-attachments/assets/d940065c-e0e0-4e3b-a1f6-07e89c5739c6)

  ![image](https://github.com/user-attachments/assets/e83276f5-8fff-454f-b80f-b98402add917)
- Scroll down and click on execute


- Click on option 2 (we are creating a new collection)
- Here we have to add the token we copied earlier
- The name of the keyspace we created initially
  ![image](https://github.com/user-attachments/assets/7d81d834-e793-49dd-a755-f395ea717e68)
- Click on try it
- To understand the meaning of the number it returned you can use
- https://httpstatusdogs.com/
- Click on cancel
 ![image](https://github.com/user-attachments/assets/e444a7b9-2bb9-4130-9002-21c34794159d)
- Edit some new information
  ![image](https://github.com/user-attachments/assets/8c2c1781-b10d-4e84-a496-966723667a20)
- Click on execute
- Next to see what we did so far (we click on GET)
  ![image](https://github.com/user-attachments/assets/80c1b0ec-cb73-4b9b-a2a3-ca00bf034157)
- It has executed and returned 200!
  ![image](https://github.com/user-attachments/assets/5e51f0e4-68b8-4517-acaa-cb6f96fc04ea)
- This is the meaning of 200
  ![image](https://github.com/user-attachments/assets/4fb41061-9c0d-4742-b47d-f03403916cbb)
- If you want someone to see what you have written
-  go to https://hoppscotch.io/
-  Hoppscotch is a free, open-source API development platform designed to make it easier for developers to test and interact with APIs.
-  Allows users to send requests to APIs and view responses.
- Supports various HTTP methods (GET, POST, PUT, DELETE, etc.).
```diff
HTTP Methods and Their Purpose:
GET: Retrieve data from the server.
POST: Create a new resource on the server.
PUT: Update or replace an existing resource.
DELETE: Remove a resource from the server.
```
  ![image](https://github.com/user-attachments/assets/073ab7fc-a2d6-4968-9b03-64ffa253a1f1)
- here you paste your document ![image](https://github.com/user-attachments/assets/058b96ca-a209-4332-b065-52aabebb2c48)
- Select header and type your token
- ![image](https://github.com/user-attachments/assets/2235e230-bed4-498d-9a3b-92c634c4c1be)
- And Tada you can see your file!

# Part 2: This time we work with Graph API

- Click on connect
  ![image](https://github.com/user-attachments/assets/4ed234b5-9a40-4e15-b7a3-52850856c561)
- Scroll down then Select GraphQL API
  ![image](https://github.com/user-attachments/assets/f398f854-99bb-4e3c-a42e-b1b1aa9ac816)
- Click on GraphQL Playground
  ![image](https://github.com/user-attachments/assets/8097a42f-06f5-4e52-887d-fa39f1ccbca5)
- You would be redirected to the playground
- Now click on Docs (This will help you understand the things we can do with it)
  ![image](https://github.com/user-attachments/assets/e4e6a68a-f64b-4331-b0d7-1c73025e484f)
- Using Doc you can understand the syntax, no need to remember it
  ![image](https://github.com/user-attachments/assets/71e635e0-41fb-4123-a524-0da23a56c7de)
```diff
  mutation {
  createTable(
    keyspaceName: "lets_learn",
    tableName: "events_new",
    partitionKeys: [
      { name: "location", type: { basic: TEXT } }
    ],
    values: [
      { name: "values", type: { basic: TEXT } }
    ]
  )
}
```
- Click on play button to see the execution
- Now we will edit the URL
![image](https://github.com/user-attachments/assets/a0d2711a-fc8a-4191-8d84-1c649b836633)

- We will add our keyspace name (Remember we named it as lets_learn)
![image](https://github.com/user-attachments/assets/734fab59-62a9-4157-b096-d4ca63d2e462)

## Use the following mutation to create two tables:

A movies table to store movie titles and directors.
A directors table to store director names and their associated movie titles.
![image](https://github.com/user-attachments/assets/252c3916-5ec4-41a6-8618-6621dbeb8a37)
```diff
Add two movies to the movies table using the mutation below. This will insert:

"Inception" directed by "Christopher Nolan"
"Interstellar" directed by "Christopher Nolan"
```
```diff
mutation {
  inception: insertmovies(
    value: { title: "Inception", director: "Christopher Nolan" }
  ) {
    value {
      title
    }
  }
  interstellar: insertmovies(
    value: { title: "Interstellar", director: "Christopher Nolan" }
  ) {
    value {
      title
    }
  }
}
```

![image](https://github.com/user-attachments/assets/6d3a0180-0975-419c-8167-33fee1cfc176)

## Retrieve the title and director of the movie "Inception" using this query:

![image](https://github.com/user-attachments/assets/224ae4a1-0936-4451-88a7-ca3db3668106)
```diff
query oneMovie {
  movies(value: { title: "Inception" }) {
    values {
      title
      director
    }
  }
}
```
```diff
1. query oneMovie
This specifies the operation type as a query, which is used to fetch data from the database.
The query is named oneMovie for identification purposes. Naming is optional but helps in organizing and debugging queries in complex systems.
2. movies
movies is the GraphQL field being queried.
It represents the table or resource from which you want to fetch data.

3. (value: { title: "Inception" })
The value argument acts as a filter for the query.
4. title and director:
These are the specific fields from the movies table you want in the response.
In this case, it will return the title and director of the movie.
```















