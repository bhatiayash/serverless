# Serverless

This serverless AWS Lambda function processes GitHub repository submissions triggered by an Amazon Simple Notification Service (SNS) message. The function downloads a submitted GitHub repository as a zip file, uploads it to Google Cloud Storage, and sends a success or failure email notification using Amazon Simple Email Service (SES). Additionally, it stores relevant details in DynamoDB for auditing purposes.

## Prerequisites
Before deploying and running the function, ensure the following:

- All libraries are installed.
- Amazon SES is set up with appropriate permissions.
- Infrastructure is created properly.

## Lambda Function Flow
1. The Lambda function is triggered by an SNS message containing GitHub repository details.
2. It parses the SNS message and extracts relevant information.
3. It downloads the GitHub repository as a zip file using the provided URL.
4. If successful, the zip file is uploaded to Google Cloud Storage.
5. Based on the upload result, a success or failure email is sent using SES.
6. Email details are stored in DynamoDB.

## Function Structure
- **`handler`**: The main Lambda function that orchestrates the process.
- **`downloadGitHubRepo`**: Downloads a GitHub repository as a zip file.
- **`uploadToGoogleStorage`**: Uploads a file to Google Cloud Storage.
- **`sendEmail`**: Sends an email using Amazon SES and stores details in DynamoDB.
