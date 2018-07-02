# rds_stop_start_lambda_function

create a role "start-stop-rds" and attach following policy to the role

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:*:*:*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "rds:StopDBInstance",
                "rds:StartDBInstance"
            ],
            "Resource": "*"
        }
    ]
}

```

RDS start lambda function

```
import botocore
import boto3

region = 'us-east-1'

DBInstanceIdentifiers_var = [ 'db-rds', 'db-rds-1' ]

def lambda_handler(event, context):
  RDS = boto3.client('rds', region_name=region )
  print("Version is {}".format(botocore.__version__))
  for i in DBInstanceIdentifiers_var:
    RDS.start_db_instance(DBInstanceIdentifier = i )
    print 'started your db instance: ' + i

```

RDS stop lambda function

```
import botocore
import boto3

region = 'us-east-1'

DBInstanceIdentifiers_var = [ 'db-rds', 'db-rds-1' ]

def lambda_handler(event, context):
  RDS = boto3.client('rds', region_name=region )
  print("Version is {}".format(botocore.__version__))
  for i in DBInstanceIdentifiers_var:
    RDS.stop_db_instance(DBInstanceIdentifier = i )
    print 'stopped your db instances: ' + i

```
