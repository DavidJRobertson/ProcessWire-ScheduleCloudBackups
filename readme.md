# ProcessWire - ScheduleCloudBackups

This module backs up your site to Amazon S3. Other storage providers may be
supported in the future.

## Instructions for setting up S3

1. If you haven't already, [create an AWS account](https://aws.amazon.com/).
2. Log in to the [S3 Management Console](https://console.aws.amazon.com/s3/home).
3. Click 'Create Bucket', give it a name, choose a region, and hit 'create'.
4. Next, head to the [IAM Management Console](https://console.aws.amazon.com/iam/home#users) and create a new user. Be sure to note down the security credentials shown, they will not be shown again.
5. Select the user you just created, then in the permissions tab, choose 'Attach User Policy'.
6. Choose 'Custom Policy', give it a name, and paste in the IAM policy shown below these steps, substituting `YOUR_BUCKET_NAME` with the bucket name chosen in step 3.
7. Fill in the access key ID, secret access key, and bucket name in the ScheduleCloudBackups module config.
8. Don't forget to set up a cron job to run the backup task!

### IAM Policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": [
          "arn:aws:s3:::YOUR_BUCKET_NAME/*",
          "arn:aws:s3:::YOUR_BUCKET_NAME",
      ]
    }
  ]
}
```
