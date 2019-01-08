# Cross-Account Kinesis Firehose Delivery

Use-Case: Customer wants to manage a Kinesis Firehose Delivery Stream in an account they control, that assumes a role in an account they don't control to write data to a bucket owned by another team.


# Account A (account_a.yaml) - Source

* Kinesis Delivery Stream (Assuming Role in Account B, Writing to Bucket in Account B)

# Account B (account_b.yaml) - Destination

* Kinesis Role (Assumed by Delivery Stream in Account A)
* IAM Policy (Attached to Kinesis Role)
* S3 Bucket (Data Delivered From Stream in Account A)

# Deployment

1. Deploy Account B Template First
2. Deploy Account A Template Second (Reference Outputs of Account B Template)


# Issues

1. Account B Template deploys without issue.
2. Account A Template fails with folllowing error.

(CF Template Deployed as IAM User with AdministratorAccess in Account A)

User: arn:aws:iam::[ACCT_#]:user/[IAM_USER] is not authorized to access this resource (Service: AmazonKinesisFirehose; Status Code: 400; Error Code: AccessDeniedException; Request ID: [REQ_ID_HERE])