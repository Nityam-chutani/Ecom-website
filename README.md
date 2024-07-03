
# E-commerce Project

This is an e-commerce project built with Node.js, Express, and MongoDB. It includes functionalities for user authentication, product management, and shopping cart operations.

## Getting Started

### Prerequisites

- Node.js
- MongoDB

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/Nityam-chutani/Ecom-website
   ```
 2. Install the dependencies:
	 ```sh 
	  cd ecommerce-project
	 npm install
	 ```
3. Set up your environment variables. Create a `.env` file in the root directory and add the following: 
``` sh
	MONGO_URI=your_mongo_connection_string
    JWT_SECRET=your_jwt_secret
```
Start the server:

```sh
npm start
API Endpoints
User Authentication
POST /signup
```

### Description: Register a new user.
```sh
Request Body:
json
{
  "name": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "address": "string"
}
POST /signin
```

### Description: Authenticate a user and return a JWT.
```sh
Request Body:
json
{
  "email": "string",
  "password": "string"
}
POST /google
```


### Product Management

- **POST /create**
  - Description: Add a new product (admin only).
  - Middleware: `verifyToken`
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "price": "number",
      "category": "string"
    }
    ```

- **GET /getProducts**
  - Description: Retrieve a list of products.

- **GET /:productId**
  - Description: Retrieve details of a specific product.

- **PUT /editProduct/:userId/:productId**
  - Description: Update an existing product (admin only).
  - Middleware: `verifyToken`
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "price": "number",
      "category": "string"
    }
    ```

- **DELETE /deleteProduct/:userId/:productId**
  - Description: Delete a product (admin only).
  - Middleware: `verifyToken`

- **GET /productByCategory/:categoryId**
  - Description: Retrieve products by category.
### Shopping Cart

- **POST /addToCart**
  - Description: Add an item to the cart.
  - Middleware: `verifyToken`
  - Request Body:
    ```json
    {
      "productId": "string",
      "quantity": "number"
    }
    ```

- **GET /:userId**
  - Description: Retrieve the user's shopping cart.
  - Middleware: `verifyToken`

- **DELETE /:cartItemId**
  - Description: Remove an item from the cart.
  - Middleware: `verifyToken`

- **PUT /:cartItemId**
  - Description: Update the quantity of an item in the cart.
  - Middleware: `verifyToken`
  - Request Body:
    ```json
    {
      "quantity": "number"
    }
    ```

## Middleware

- **verifyToken**
  - Description: Middleware to verify the JWT token and authenticate the user.


