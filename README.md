# AWSense

## 📌 Project Description

Serverless AWS Lambda function serving a contact form with DynamoDB
integration for storing submissions.
This project demonstrates how to build a simple serverless web app on
AWS where users can submit a contact form.
The data is stored in **Amazon DynamoDB**, and users are redirected to a
thank-you page after submission.

------------------------------------------------------------------------

## 🚀 Features

-   Serverless architecture using **AWS Lambda**\
-   Frontend contact form (`contactus.html`)\
-   Backend Lambda function (`lambda_function.py`)\
-   Data persistence with **Amazon DynamoDB**\
-   Thank-you page after successful form submission (`success.html`)

------------------------------------------------------------------------

## 📂 Project Structure

    .
    ├── contactus.html     # Contact form page
    ├── success.html       # Thank-you page
    └── lambda_function.py # AWS Lambda backend

------------------------------------------------------------------------

## ⚙️ How It Works

1.  User opens `contactus.html` (served by AWS Lambda on **GET**
    request).\
2.  User fills in the form and submits (triggers a **POST** request).\
3.  `lambda_function.py` receives the form data and inserts it into
    **DynamoDB** (`anikettable`).\
4.  On success, Lambda returns `success.html` as a response.

------------------------------------------------------------------------

## 🛠️ Setup Instructions

### Prerequisites

-   AWS account\
-   DynamoDB table (`anikettable`)\
-   AWS CLI & SAM CLI configured\
-   Python 3.x installed

### Steps

1.  **Clone the repository**

    ``` bash
    git clone https://github.com/your-username/aws-contact-form.git
    cd aws-contact-form
    ```

2.  **Create DynamoDB table**

    ``` bash
    aws dynamodb create-table      --table-name anikettable      --attribute-definitions AttributeName=fname,AttributeType=S      --key-schema AttributeName=fname,KeyType=HASH      --billing-mode PAY_PER_REQUEST
    ```

3.  **Deploy Lambda Function**

    -   Zip the project files:

        ``` bash
        zip -r lambda_function.zip lambda_function.py contactus.html success.html
        ```

    -   Deploy to AWS Lambda (via AWS Console or CLI).

4.  **Set API Gateway**

    -   Create API Gateway with methods:
        -   **GET** → Returns `contactus.html`
        -   **POST** → Stores form data in DynamoDB, returns
            `success.html`

------------------------------------------------------------------------

## 📸 Screenshots

### Contact Form

![Contact Form](./screenshots/contactus.png)

### Success Page

![Success Page](./screenshots/success.png)


