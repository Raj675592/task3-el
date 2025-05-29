## Setup Instructions

### Initialize the project:
mkdir books-api
cd books-api
npm init -y

Install dependencies:
npm install express
npm install --save-dev nodemon

Create server.js file with the provided code
Start the server:
npm start
# or for development with auto-restart:
npm run dev


API Endpoints Testing with Postman
1. GET /books - Get All Books

Method: GET
URL: http://localhost:3000/books
Headers: None required
Expected Response:
json{
  "success": true,
  "count": 3,
  "data": [
    {
      "id": 1,
      "title": "To Kill a Mockingbird",
      "author": "Harper Lee"
    },
    {
      "id": 2,
      "title": "1984",
      "author": "George Orwell"
    },
    {
      "id": 3,
      "title": "The Great Gatsby",
      "author": "F. Scott Fitzgerald"
    }
  ]
}


2. GET /books/:id - Get Specific Book

Method: GET
URL: http://localhost:3000/books/1
Headers: None required
Expected Response:
json{
  "success": true,
  "data": {
    "id": 1,
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee"
  }
}


3. POST /books - Create New Book

Method: POST
URL: http://localhost:3000/books
Headers:

Content-Type: application/json


Body (JSON):
json{
  "title": "The Catcher in the Rye",
  "author": "J.D. Salinger"
}

Expected Response:
json{
  "success": true,
  "message": "Book created successfully",
  "data": {
    "id": 4,
    "title": "The Catcher in the Rye",
    "author": "J.D. Salinger"
  }
}


4. PUT /books/:id - Update Book

Method: PUT
URL: http://localhost:3000/books/1
Headers:

Content-Type: application/json


Body (JSON):
json{
  "title": "To Kill a Mockingbird (Updated)",
  "author": "Harper Lee"
}

Expected Response:
json{
  "success": true,
  "message": "Book updated successfully",
  "data": {
    "id": 1,
    "title": "To Kill a Mockingbird (Updated)",
    "author": "Harper Lee"
  }
}


5. DELETE /books/:id - Delete Book

Method: DELETE
URL: http://localhost:3000/books/1
Headers: None required
Expected Response:
json{
  "success": true,
  "message": "Book deleted successfully",
  "data": {
    "id": 1,
    "title": "To Kill a Mockingbird (Updated)",
    "author": "Harper Lee"
  }
}


Error Scenarios to Test
1. Book Not Found (404)

URL: http://localhost:3000/books/999
Methods: GET, PUT, DELETE
Expected Response:
json{
  "success": false,
  "message": "Book not found"
}


2. Missing Required Fields (400)

Method: POST or PUT
Body:
json{
  "title": "Only Title"
}

Expected Response:
json{
  "success": false,
  "message": "Title and author are required"
}


3. Invalid Route (404)

URL: http://localhost:3000/invalid-route
Expected Response:
json{
  "success": false,
  "message": "Route not found"
}
