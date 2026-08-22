# Amazon Bedrock Customer Support Chatbot

An AI-powered customer support chatbot built using Amazon Bedrock Flows.

The flow classifies incoming customer messages and routes them to specialized handlers:

- Bug reports
- Platform questions
- Other customer requests

## Architecture

Customer Message
        |
        v
Flow Input Node
        |
        v
CS Classifier (Amazon Bedrock Prompt)
        |
        |
        +----------------+
        |                |
        v                v

BUG_REPORT     PLATFORM_QUESTION     OTHER

    |                |                 |
    v                v                 v

Bug Report      Platform Question   Other Request
Extractor       Extractor           Extractor

    |
    v

Lambda Function

    |
    v

DynamoDB Ticket Storage


## Technologies Used

- Amazon Bedrock Flows
- Amazon Nova Pro Model
- AWS Lambda
- Amazon DynamoDB
- IAM Roles


## Flow Features

### Request Classification

The classifier assigns each customer message into exactly one category:

- BUG_REPORT
- PLATFORM_QUESTION
- OTHER


### Bug Report Handling

Bug reports are processed by a dedicated extractor and stored as support tickets.

Stored information:

- Ticket ID
- Description
- Steps to reproduce
- Environment
- Status
- Creation timestamp


## Example Input
The checkout page crashes whenever I click the payment button.

Classification:
BUG_REPORT

## Project Structure
customer-support-chatbot-bedrock-flow

│
├── README.md
│
├── bedrock-flow
│ ├── flow-architecture.md
│ └── prompts.md
│
└── lambda
└── create_bug_report.py



## Author

Amazon Bedrock Flow Project