This project is intentionally complex and could be convoluted or confusing. This is by design and to simulate real life situations where customers seldom give crystal clear requirements and ask unambiguous questions.

Architecture Implementation:

1. The customer uploads the invoice data to S3 bucket in a text format as per their guidelines and policies. This bucket will have a policy to auto delete any content that is more than 1 day old (24 hours).
2. An event will trigger in the bucket that will place a message in SNS topic.
3. A custom program running in EC2 will subscribe to the SNS topic and get the message placed by S3 event.
4. The program will use S3 API to read from the bucket, parse the content of the file and create a CSV record and save the details in an RDS database.
5. The program will use S3 API to write CSV record to destination S3 bucket as new S3 object.

Note: The custom program codebase and sample invoice have been shared along with this workbook on the repository.

Step 1: SNS and S3 topic creation
Step 2: Run the custom program in the EC2 instance
Step 3: Creation and Verification of SNS subscription and Generation of CSV file

