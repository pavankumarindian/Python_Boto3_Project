## Title - Summary and Scheduling of AWS Resources (EC2, RDS)

Services used - EC2, Boto3, RDS, SNS notifications, Gmail integration, Event bridge, SES

### Phase-1: 

Trigger email to your gmail-id from Lambda 

Summarise all the resources running in your aws account at 6PM everyday (both running and stopped instances)

### Phase-2

Create a Cloudformation script for creating sample EC2 and RDS instances. Update tags to the resources with auto-stop = true.

Stop EC2 instances at 8PM everyday (if they are running) for all resources that have tag updated as auto-stop = true

Stop RDS instances at 8PM everyday (if they are running) for all resources that have tag updated as auto-stop = true

Create a CFT-1 script with following -
  EC2
  RDS

Create a CFT to create the following-
  Eventbridge Rule
  Step Functions
  Lmabda Functions
  IAM Role
  SNS

