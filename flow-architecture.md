# Flow Architecture


## Nodes


### Flow Input Node

Receives the customer message.


### CS_Classifier

Uses Amazon Nova Pro to classify the request.


Output categories:

- BUG_REPORT
- PLATFORM_QUESTION
- OTHER


### Condition Node

Routes execution based on classifier output.


Conditions:
conditionInput == "BUG_REPORT"

Routes to:
Bug_Report_Extractor

conditionInput == "PLATFORM_QUESTION"

Routes to:
Platform_Question_Extractor

conditionInput == "OTHER"
Routes to:
Other_Request_Extractor


## Lambda Integration

Bug reports are sent to AWS Lambda.

Lambda creates a support ticket and stores it in DynamoDB.