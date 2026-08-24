# AWS-resourse-listing-script
A lightweight Bash script to quickly list resources across common AWS services from the command line — useful for auditing an account, sanity-checking deployments, or just getting a fast inventory without opening the AWS Console.

## Supported Services

| Service | Command Used |
|---|---|
| EC2 | `describe-instances` |
| RDS | `describe-db-instances` |
| S3 | `list-buckets` |
| CloudFront | `list-distributions` |
| VPC | `describe-vpcs` |
| IAM | `list-users` |
| Route53 | `list-hosted-zones` |
| CloudWatch | `describe-alarms` |
| CloudFormation | `describe-stacks` |
| Lambda | `list-functions` |
| SNS | `list-topics` |
| SQS | `list-queues` |
| DynamoDB | `list-tables` |
| EBS | `describe-volumes` |

## Prerequisites

- [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) installed
- AWS CLI configured with valid credentials (`aws configure`)
- IAM permissions to call the relevant `Describe`/`List` actions for whichever services you query (read-only access, e.g. the AWS-managed `ReadOnlyAccess` policy, is sufficient)
- Bash 4+ (for the `${var,,}` lowercase expansion)

## Usage

```bash
./aws_resource_list.sh <aws_region> <aws_service>
```

### Example

```bash
./aws_resource_list.sh us-east-1 ec2
```

```
Listing EC2 Instances in us-east-1
{
    "Reservations": [
        ...
    ]
}
```

## Installation

```bash
git clone https://github.com/<your-username>/aws-resource-lister.git
cd aws-resource-lister
chmod +x aws_resource_list.sh
```

