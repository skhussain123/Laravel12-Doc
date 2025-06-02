


## What is Api.
An API (Application Programming Interface) is a set of rules and tools that allows different software applications to communicate with each other.

### Simple Explanation:
Think of an API like a waiter in a restaurant:

You (the user) tell the waiter (API) what you want (e.g., “a burger”).

* The waiter takes your order to the kitchen (server).
* The kitchen prepares the food and gives it to the waiter.
* The waiter brings it back to you.

You don’t need to know how the kitchen works—you just use the menu (API documentation) and the waiter (API) handles everything.

### Example in Web Development

* You use a weather API to get live weather data.
* Your app sends a request like:
```bash
GET https://api.weather.com/v1/current?city=karachi
```
**The API responds with:**

```bash
{
  "city": "Karachi",
  "temperature": "33°C",
  "status": "Sunny"
}
```
You don’t need to collect weather data yourself. The API gives it to you.


### Types of APIs:

* REST API: Most common, uses HTTP methods like GET, POST, PUT, DELETE.
* SOAP API: Older, uses XML messages.
* GraphQL API: Flexible, you can request exactly what you need.


## What is a REST API?
REST API stands for Representational State Transfer Application Programming Interface.
It is a popular way to create APIs that use HTTP requests to perform CRUD operations (Create, Read, Update, Delete) on data.

###  Key Concepts:
| Term             | Meaning                                                          |
| ---------------- | ---------------------------------------------------------------- |
| **Client**       | The application that sends requests (e.g., frontend, mobile app) |
| **Server**       | The backend that provides data and handles logic                 |
| **Resource**     | The data being accessed (e.g., users, posts, products)           |
| **HTTP Methods** | Used to perform actions on resources                             |


###  Common HTTP Methods in REST API:
| Method     | Purpose             | Example             |
| ---------- | ------------------- | ------------------- |
| **GET**    | Read data           | Get a list of users |
| **POST**   | Create new data     | Add a new user      |
| **PUT**    | Update entire data  | Update user details |
| **PATCH**  | Update part of data | Update only email   |
| **DELETE** | Delete data         | Remove a user       |


### Example of REST API Endpoints for users
| Action              | HTTP Method | URL            | Description                  |
| ------------------- | ----------- | -------------- | ---------------------------- |
| List all users      | GET         | `/api/users`   | Get all users                |
| Get a specific user | GET         | `/api/users/1` | Get user with ID 1           |
| Create a new user   | POST        | `/api/users`   | Add a new user               |
| Update user         | PUT         | `/api/users/1` | Update all details of user 1 |
| Delete a user       | DELETE      | `/api/users/1` | Remove user 1                |

### REST API Principles:

* Stateless – No user session stored on server.
* Uniform Interface – Consistent way to access resources.
* Client-Server – Separation of frontend and backend.
* Cacheable – Responses can be cached for performance.


## What is a SOAP API?
SOAP stands for Simple Object Access Protocol.
It is an older, XML-based protocol used to exchange structured data between computers over a network.

Unlike REST APIs (which are lightweight and flexible), SOAP APIs are strict, formal, and highly standardized — often used in enterprise systems like banking, government, and telecom.


### Key Features of SOAP API:
| Feature                  | Description                                                                 |
| ------------------------ | --------------------------------------------------------------------------- |
| **Uses XML**             | Data is sent in XML format only.                                            |
| **Strict Standards**     | Follows strict rules defined in a WSDL (Web Services Description Language). |
| **Protocol Independent** | Can run over HTTP, SMTP, TCP, etc.                                          |
| **Built-in Security**    | Supports WS-Security (e.g., for encryption, authentication).                |
| **Formal Contracts**     | Requires WSDL file that defines the service, request, and response format.  |


### Example SOAP Request (in XML):
**Service: Get Weather Info**

```bas
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:web="http://example.com/weather">
   <soapenv:Header/>
   <soapenv:Body>
      <web:GetWeather>
         <web:City>Karachi</web:City>
      </web:GetWeather>
   </soapenv:Body>
</soapenv:Envelope>

```

###  Response from Server (also XML):

```bash
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
   <soapenv:Body>
      <web:GetWeatherResponse>
         <web:Temperature>33°C</web:Temperature>
         <web:Condition>Sunny</web:Condition>
      </web:GetWeatherResponse>
   </soapenv:Body>
</soapenv:Envelope>

```

### SOAP vs REST (Quick Comparison):
| Feature     | SOAP                            | REST                    |
| ----------- | ------------------------------- | ----------------------- |
| Format      | XML only                        | JSON, XML, HTML, etc.   |
| Protocol    | Works over HTTP, SMTP, etc.     | Works over HTTP only    |
| Speed       | Slower (XML heavy)              | Faster (lightweight)    |
| Flexibility | Less flexible, very strict      | More flexible           |
| Security    | Built-in security (WS-Security) | Use HTTPS, tokens, etc. |
| Use Case    | Banking, enterprise systems     | Modern web/mobile apps  |


### Where is SOAP still used?

* Banking and Finance
* Telecom companies
* Insurance systems
* Enterprise Resource Planning (ERP) tools


## GraphQL API:
GraphQL is a query language for APIs and a runtime for executing those queries by using a type system you define for your data.
It was developed by Facebook in 2012 and released publicly in 2015.

### REST vs GraphQL
| Feature                      | REST API                       | GraphQL API                         |
| ---------------------------- | ------------------------------ | ----------------------------------- |
| Data Fetching                | Multiple endpoints             | Single endpoint                     |
| Over-fetching/Under-fetching | Common issue                   | Avoided — get exactly what you need |
| Versioning                   | Often versioned (v1, v2, etc.) | No need for versioning              |
| Flexibility                  | Less flexible                  | Very flexible                       |
| Performance                  | May require multiple requests  | Typically fewer requests            |


### How GraphQL Works

* You send a query to the server.
* The server responds with only the requested data.
* It's like asking: “Give me the name and email of users,” and it returns just that.

### Example
**Query:**
```bash
{
  user(id: "1") {
    name
    email
  }
}

```

**Response:**
```bash
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "john@example.com"
    }
  }
}

```

###  Key Concepts

* Query: Fetch data.
* Mutation: Modify data (create, update, delete).
*  Subscription: Get real-time data updates.
* Schema: Defines types and structure of your API.
* Resolver: Functions that fetch the data for each field in a query.

###  Benefits

* Fetch exactly what you need.
* Single endpoint for all requests.
* Strongly typed schema (easier debugging).
* Great for front-end developers.



### Common Uses:
Integrating payment systems (Stripe, PayPal)

* Logging in with Google or Facebook
* Displaying maps (Google Maps API)
* Connecting with mobile apps or frontends in web development

Let me know if you want examples in Laravel, JavaScript, or any other language.
