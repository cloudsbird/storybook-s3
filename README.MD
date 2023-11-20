# GitHub Action for Deploying Storybook to AWS S3

This GitHub Action deploys your Storybook to an AWS S3 bucket.

## Inputs

- `aws_s3_bucket`: The name of the S3 bucket where your Storybook will be deployed.
- `aws_access_key_id`: Your AWS access key ID.
- `aws_secret_access_key`: Your AWS secret access key.
- `aws_region`: The AWS region where your S3 bucket is located.
- `aws_s3_host`: The host of your S3 bucket. default is `s3.amazonaws.com`.
- `preview`: A boolean value indicating whether this is a preview deployment. If `true`, the action will deploy to a directory named `pr-[PR number]`. If `false`, it will deploy to a directory named `main`.

## Usage

Here's an example of how to use this action:

```yaml
- name: 'Deploy to S3'
  uses: cloudsbird/storybook-s3@v0.0.1
  with:
    aws_s3_bucket: ${{ secrets.AWS_S3_BUCKET }}
    aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws_region: ${{ secrets.AWS_REGION }}
    aws_s3_host: ${{ secrets.AWS_S3_HOST }}
    preview: 'true'