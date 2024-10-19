# Rule-Engine-Application
This project is a simple rule engine that evaluates user eligibility based on provided rules. It uses an Abstract Syntax Tree (AST) to represent the rules and evaluates conditions like age, department, salary, and experience to determine eligibility.
Table of Contents
Overview
Technologies Used
Project Setup
Backend Setup
Frontend Setup
API Endpoints
Create Rule
Evaluate Rule
Running the Application
Running Backend
Running Frontend
Example Usage
Creating a Rule
Evaluating a Rule
Overview
This project includes both a backend (Node.js + Express) and a frontend (React + TailwindCSS) application.

Backend: Parses a rule string into an Abstract Syntax Tree (AST) and evaluates it against user data.
Frontend: Provides a user interface for entering rule strings and user data, sending requests to the backend to create and evaluate rules.
Technologies Used
Backend:
Node.js: JavaScript runtime for building the backend.
Express: Web framework for building the API.
CORS: Middleware to allow cross-origin requests.
Frontend:
React: JavaScript library for building user interfaces.
TailwindCSS: Utility-first CSS framework for styling.
Axios: HTTP client for making API requests.
Project Setup
Backend Setup
Clone the Repository:

git clone https://github.com/yourusername/rule-engine-backend.git
cd rule-engine-backend
Install Dependencies:

npm install
Run the Server:

node server.js
The backend server will run on http://localhost:4000.

Frontend Setup
Clone the Repository:

git clone https://github.com/yourusername/rule-engine-frontend.git
cd rule-engine-frontend
Install Dependencies:

npm install
Start the Development Server:

npm start
The frontend app will run on http://localhost:3000.

API Endpoints
1. Create Rule
Endpoint: /create_rule
Method: POST
Description: Parses a rule string and returns the Abstract Syntax Tree (AST).
Request Body:
{
  "ruleString": "((age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing')) AND (salary > 50000 OR experience > 5)"
}
Response:
{
  "message": "Rule created successfully",
  "ast": {
    "type": "AND",
    "left": {
      "type": "OR",
      "left": {
        "type": "AND",
        "left": { "type": "condition", "attribute": "age", "operator": ">", "value": "30" },
        "right": { "type": "condition", "attribute": "department", "operator": "=", "value": "Sales" }
      },
      "right": {
        "type": "AND",
        "left": { "type": "condition", "attribute": "age", "operator": "<", "value": "25" },
        "right": { "type": "condition", "attribute": "department", "operator": "=", "value": "Marketing" }
      }
    },
    "right": {
      "type": "OR",
      "left": { "type": "condition", "attribute": "salary", "operator": ">", "value": "50000" },
      "right": { "type": "condition", "attribute": "experience", "operator": ">", "value": "5" }
    }
  }
}
2. Evaluate Rule
Endpoint: /evaluate_rule
Method: POST
Description: Evaluates a rule (AST) against user data.
Request Body:
{
  "ruleAst": { /* AST generated from create_rule */ },
  "data": {
    "age": 35,
    "department": "Sales",
    "salary": 60000,
    "experience": 3
  }
}
Response:
{
  "result": true
}
Running the Application
Running Backend
Navigate to the Backend Directory:

cd rule-engine-backend
Install Dependencies:

npm install
Run the Backend Server:

node server.js
This will start the backend server on http://localhost:4000.

Running Frontend
Navigate to the Frontend Directory:

cd rule-engine-frontend
Install Dependencies:

npm install
Run the Frontend Server:

npm start
This will start the frontend app on http://localhost:3000.

Example Usage
Creating a Rule
Request: Make a POST request to /create_rule with the following body:

{
  "ruleString": "((age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing')) AND (salary > 50000 OR experience > 5)"
}
Response: You will receive a response with the parsed AST:

{
  "message": "Rule created successfully",
  "ast": {
    "type": "AND",
    "left": { /* ... */ },
    "right": { /* ... */ }
  }
}
Evaluating a Rule
Request: Make a POST request to /evaluate_rule with the following body:

{
  "ruleAst": { /* AST from create_rule response */ },
  "data": {
    "age": 35,
    "department": "Sales",
    "salary": 60000,
    "experience": 3
  }
}
Response: You will receive a response with the evaluation result:

{
  "result": true
}
Conclusion
This Rule Engine application allows users to create rules in a structured format (AST) and evaluate user data based on those rules. The backend handles rule parsing and evaluation, while the frontend provides an easy-to-use interface for interacting with the API.


