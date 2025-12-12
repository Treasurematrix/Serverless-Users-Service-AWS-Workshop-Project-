# 🟦 **README.md – Serverless Users Service (AWS Workshop Project)**

# Serverless Users Service – AWS Serverless Workshop

This project is a fully serverless backend service built as part of the **AWS Serverless Patterns Workshop**.  
It demonstrates how to design and deploy a **scalable, event-driven Users microservice** using:

- **AWS Lambda**
- **Amazon DynamoDB**
- **Amazon API Gateway**
- **AWS Identity & Access Management (IAM)**

The service exposes a public REST API that returns user data stored in DynamoDB, using a synchronous invocation pattern.

---

## 🚀 Project Overview

Modern applications require scalability, low operational overhead, and rapid iteration.  
This project represents the **Users Service** of a fictional hyperlocal food-delivery platform that uses electric bike couriers.  

The service provides:

- Creation of user records (programmatically via Lambda)
- Retrieval of all user records via a REST API
- Secure and scalable integration between compute, data, and API layers

---

## 🏗️ Architecture

The service uses the classic **serverless synchronous pattern**:

```

Client → API Gateway → Lambda → DynamoDB → Lambda → API Gateway → Client

````

### **Components**
| Service | Purpose |
|--------|----------|
| **Amazon DynamoDB** | Stores user records in a fully managed NoSQL table |
| **AWS Lambda** | Computes logic for adding and retrieving data |
| **API Gateway (REST API)** | Public API entry point for `/users` endpoint |
| **IAM** | Controls secure access between services |

---

## 📦 Features Implemented

### ✔ Serverless database
- Created a DynamoDB table: `serverless_workshop_intro`
- Partition key: `_id` (String)
- Added items both manually and via Lambda

### ✔ Lambda functions
- `first-function` – initial test function  
- `m1-add-sample-data` – inserts demo users using `batch_writer()`  
- `get-users` – retrieves all items from DynamoDB using `scan()`

### ✔ API Gateway REST API
- Created a REST API named **ServerlessREST**
- Added resource: `/users`
- Integrated GET method with the `get-users` Lambda function
- Deployed API to stage: `v1`

### ✔ IAM permissions
- Lambda execution roles updated to allow:
  - `AmazonDynamoDBFullAccess` (for write function)
  - `AmazonDynamoDBReadOnlyAccess` (for read function)

---

## 🧪 Testing

### Test via Browser or cURL

**GET all users**

```bash
curl https://<api-id>.execute-api.<region>.amazonaws.com/v1/users
````

Expected response:

```json
[
  {
    "_id": "abc123...",
    "Userid": "marivera",
    "FullName": "Martha Rivera"
  },
  ...
]
```

### Test Lambda functions

Each Lambda function was tested using the **AWS Console Test Events**.

---

## 📁 Project Structure

```
├── dynamodb/
│   └── serverless_workshop_intro (table)
├── lambdas/
│   ├── first-function
│   ├── m1-add-sample-data
│   └── get-users
└── api/
    └── ServerlessREST → /v1/users
```

---

## 📚 Key Concepts Learned

* Serverless architecture and event-driven design
* Writing Lambda functions in Python
* DynamoDB table and item modelling
* REST API creation with API Gateway
* IAM execution roles and permissions
* Testing and debugging serverless resources
* Deploying and consuming a fully functional serverless API

---

## 🔧 Technologies Used

* **Python 3.10**
* **AWS Lambda**
* **Amazon DynamoDB**
* **Amazon API Gateway (REST)**
* **IAM**
* **AWS Management Console**

---

## 🌱 Future Improvements

These enhancements would turn this into a full production-ready service:

* Implement authentication with Amazon Cognito
* Add unit tests and integration tests (pytest + SAM local testing)
* Deploy infrastructure using **AWS SAM** or **CDK**
* Add observability with CloudWatch and AWS Lambda Powertools
* Add input validation and request filtering
* Expand into Orders and Profile services

---

## 🏁 Conclusion

This project demonstrates a complete, scalable, cost-efficient serverless microservice built using core AWS services.
It shows foundational Cloud and DevOps skills, as well as practical experience with AWS’s event-driven serverless ecosystem.

---

### 👤 Author

**Chioma Nwosu**
Cloud | DevOps | AWS | Serverless

```


```
