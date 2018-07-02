# rds_stop_start_lambda_function

create a role and attach following policy to the instance

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
