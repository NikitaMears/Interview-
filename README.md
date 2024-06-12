
## Full Stack Developer Interview Questions

### GraphQL

1. **What is GraphQL, and how does it differ from REST?**
   - **Answer:** GraphQL is a query language for APIs and a runtime for executing those queries by using a type system you define for your data. Unlike REST, which has multiple endpoints that return fixed data structures, GraphQL uses a single endpoint and allows clients to specify the exact data they need. This reduces over-fetching and under-fetching of data.

2. **Can you explain the concepts of queries, mutations, and subscriptions in GraphQL?**
   - **Answer:**
     - **Queries:** Used to fetch data from the server. They are analogous to GET requests in REST.
     - **Mutations:** Used to modify server-side data. They are analogous to POST, PUT, DELETE requests in REST.
     - **Subscriptions:** Used to maintain a real-time connection with the server, allowing clients to receive updates when data changes. They are similar to WebSockets.

3. **How do you handle authentication and authorization in a GraphQL API?**
   - **Answer:** Authentication is typically handled by passing a token (e.g., JWT) in the HTTP headers of the GraphQL request. Authorization can be enforced at the resolver level by checking the user's permissions before executing the resolver's logic. Middleware functions or directives can also be used for authorization checks.

4. **Describe a situation where you used GraphQL to solve a complex data-fetching problem.**
   - **Answer:** In a project requiring data from multiple related resources, using REST would have resulted in multiple round-trips to the server and over-fetching of data. By using GraphQL, I defined a single query to fetch only the necessary fields from multiple types, reducing the number of network requests and the amount of data transferred.

5. **What are the benefits and potential drawbacks of using GraphQL?**
   - **Answer:**
     - **Benefits:** Flexibility in querying data, reduced over-fetching and under-fetching, strong typing, and a single endpoint for all data requests.
     - **Drawbacks:** Complexity in setting up and maintaining the server, potential for performance issues with poorly designed queries, and the need for clients and servers to agree on the schema.

---

### README

# Full Stack Developer Interview Questions

This document contains a list of potential interview questions for a junior full stack developer role, focusing on React, Node.js, MongoDB, PostgreSQL, and GraphQL.

## React

1. **What is the virtual DOM in React, and how does it improve performance?**
   - The virtual DOM is an in-memory representation of the real DOM. React updates the virtual DOM first, calculates the differences, and then updates the actual DOM, minimizing direct manipulation and improving performance.

2. **Explain the purpose and use of hooks in React.**
   - Hooks allow state and other React features to be used in functional components. Common hooks include `useState` for state management and `useEffect` for side effects.

3. **How do you manage state in a React application? Compare using Redux vs. the Context API.**
   - State can be managed locally, via the Context API, or with Redux. Context API is simpler for small apps or deeply nested components, while Redux offers a scalable, centralized state management solution for larger applications.

4. **What is the purpose of `useEffect`? Can you give an example?**
   - `useEffect` handles side effects in functional components, such as data fetching. It runs after the render and can optionally clean up.
   ```javascript
   useEffect(() => {
     fetch('/api/data')
       .then(response => response.json())
       .then(data => setData(data));
   }, []);
   ```

5. **What are the benefits of using React Router for navigation in a React application?**
   - React Router offers declarative routing, nested routes, dynamic route matching, code-splitting with lazy loading, and easy integration with state.

## Node.js

1. **What is the role of the event loop in Node.js?**
   - The event loop handles asynchronous operations, allowing Node.js to perform non-blocking I/O by offloading tasks to the system kernel and processing callbacks when tasks complete.

2. **Can you explain the difference between CommonJS and ES6 modules in Node.js?**
   - CommonJS uses `require` and `module.exports`, whereas ES6 modules use `import` and `export` statements, enabling static analysis and tree shaking.

3. **Describe a situation where you used middleware in an Express application.**
   - Middleware functions in Express can handle logging, authentication, and error handling. For example, a logging middleware logs request details:
   ```javascript
   app.use((req, res, next) => {
     console.log(`${req.method} ${req.url}`);
     next();
   });
   ```

4. **How do you handle error logging and monitoring in a Node.js application?**
   - Using libraries like Winston or Morgan for logging, and tools like PM2 for monitoring. Integrating with services like Sentry or Loggly helps track and analyze errors.

5. **What are streams in Node.js, and how are they used?**
   - Streams allow reading or writing data in chunks, suitable for handling large files or data sources. Types include Readable, Writable, Duplex, and Transform.
   ```javascript
   const fs = require('fs');
   const readStream = fs.createReadStream('file.txt');
   readStream.on('data', chunk => {
     console.log(chunk.toString());
   });
   ```

## MongoDB

1. **What are the advantages and disadvantages of using MongoDB over a relational database like PostgreSQL?**
   - **Advantages:** Flexible schema design, horizontal scalability, high availability.
   - **Disadvantages:** Lacks transactional integrity for complex operations, potential for high storage consumption.

2. **Explain the concept of schemas in MongoDB. How do they differ from schemas in SQL databases?**
   - MongoDB is schema-less, allowing varied structures in documents within a collection. SQL databases enforce fixed schemas with predefined table structures.

3. **How do you perform aggregation operations in MongoDB? Can you give an example?**
   - Using the `aggregate` method with stages like `$match`, `$group`, `$sort`:
   ```javascript
   db.collection.aggregate([
     { $match: { status: "active" } },
     { $group: { _id: "$category", total: { $sum: 1 } } },
     { $sort: { total: -1 } }
   ]);
   ```

4. **Describe a situation where you used indexing in MongoDB. How did it improve performance?**
   - Indexing on the `email` field of a `users` collection:
   ```javascript
   db.users.createIndex({ email: 1 });
   ```
   Improved query performance significantly by speeding up lookups.

5. **What are MongoDB’s data models, and how do they support the document-oriented nature of the database?**
   - MongoDB’s data models use BSON format, supporting nested structures and arrays, allowing complex data relationships within a single document.

## PostgreSQL

1. **How do you design a database schema in PostgreSQL? What factors do you consider?**
   - Define tables, columns, data types, and relationships. Consider data normalization, indexing strategies, constraints, performance, and scalability.

2. **Can you explain the concept of transactions in PostgreSQL? Why are they important?**
   - Transactions ensure a sequence of operations is executed atomically, maintaining data integrity and allowing rollback in case of errors.

3. **How do you perform joins in PostgreSQL? Can you provide an example query?**
   - Joins combine rows from multiple tables based on related columns. Example of an INNER JOIN:
   ```sql
   SELECT users.name, orders.amount
   FROM users
   INNER JOIN orders ON users.id = orders.user_id;
   ```

4. **What are the benefits of using PostgreSQL over other SQL databases?**
   - Advanced features, support for complex queries, JSON data types, full-text search, reliability, extensibility, and strong community support.

5. **How do you handle database migrations in PostgreSQL?**
   - Using tools like Flyway or Liquibase, or ORMs like Sequelize or TypeORM for version control of schema changes and ensuring consistency across environments.

## GraphQL

1. **What is GraphQL, and how does it differ from REST?**
   - GraphQL is a query language for APIs, using a single endpoint to request exactly the data needed, reducing over-fetching and under-fetching compared to REST’s fixed endpoints.

2. **Can you explain the concepts of queries, mutations, and subscriptions in GraphQL?**
   - **Queries:** Fetch data from the server.
   - **Mutations:** Modify server-side data.
   - **Subscriptions:** Maintain real-time connections for updates.

3. **How do you handle authentication and authorization in a GraphQL API?**
   - Authentication via tokens (e.g., JWT) in HTTP headers. Authorization through resolver checks, middleware functions, or directives.

4. **Describe a situation where you used GraphQL to solve a complex data-fetching problem.**
   - Reduced multiple network requests and data transfer by defining a single query to fetch necessary fields from multiple types, optimizing performance.

5. **What are the benefits and potential drawbacks of using GraphQL?**
   - **Benefits:** Flexible queries, reduced data over-fetching/under-fetching, strong typing, single endpoint.
   - **Drawbacks:** Setup complexity, potential performance issues with poorly designed queries, schema agreement between clients and servers.

---

This document provides a comprehensive set of interview questions and answers to help assess the knowledge# Interview-
