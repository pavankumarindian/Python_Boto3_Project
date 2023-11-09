# AWS Resource Management Script

This repository contains Python scripts and configurations for automating the management of AWS resources, including EC2 and RDS instances, using Boto3, AWS Lambda, AWS Step Functions, and AWS EventBridge.

## Table of Contents
- [Introduction](#introduction)
- [Phases](#phases)
- [Setup](#setup)
- [Usage](#usage)
- [License](#license) 

## Introduction

This project aims to automate the management of AWS resources in two phases:
1. **Phase 1**: Daily summary of running and stopped EC2 and RDS instances sent to a Gmail account.
2. **Phase 2**: Automatic stopping of EC2 and RDS instances tagged with `auto-stop=true` at a specified time.

Additionally, the project leverages AWS Step Functions to orchestrate and manage the overall resource management process.

## Phases

### Phase 1: Sending Resource Summary Email

- A Lambda function is triggered daily at 6 PM using AWS EventBridge.
- The Lambda function uses Boto3 to collect information about running and stopped EC2 and RDS instances.
- Summarized information is sent as an email to the configured Gmail account using SNS notifications.

### Phase 2: Stopping EC2 and RDS Instances

- A Lambda function is triggered daily at 8 PM using AWS EventBridge.
- The Lambda function uses Boto3 to stop EC2 and RDS instances with the `auto-stop=true` tag.
- Stopped instances are identified and stopped automatically.

## AWS Step Functions State Machine

- An AWS Step Functions state machine orchestrates the entire resource management process, combining Phase 1 and Phase 2.
- The state machine defines the sequence of execution, handling error scenarios and transitions between phases.

## Setup

To set up and run this script, follow these steps:

1. Clone this repository to your local machine:


git clone <repository-url>
cd aws-resource-management


2. Install the required Python libraries and dependencies:

pip install boto3



3. Configure the following:
- Gmail SMTP settings and credentials in the Phase 1 Lambda function.
- AWS IAM roles and permissions for Lambda functions to interact with EC2, RDS, and SNS.
- AWS EventBridge rules to schedule the Lambda functions at the desired times.
- Ensure proper tagging of EC2 and RDS instances with `auto-stop=true`.
- Create an AWS Step Functions state machine to orchestrate the resource management process. Define the states, input/output parameters, and error handling as needed.

## Usage

1. **Phase 1**: Once the setup is complete, the summary email will be sent daily at 6 PM as part of the AWS Step Functions state machine execution.

2. **Phase 2**: The Lambda function for stopping instances will run daily at 8 PM as part of the state machine and automatically stop EC2 and RDS instances tagged with `auto-stop=true`.

3. **AWS Step Functions**: Start the AWS Step Functions state machine execution manually or schedule it using AWS EventBridge to manage the entire resource management process.

##  License
This repository is licensed under the MIT License.
