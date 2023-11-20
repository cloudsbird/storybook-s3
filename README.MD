# GitHub Action for Deploying Storybook to AWS S3

This GitHub Action deploys your Storybook to an AWS S3 bucket.

## Features

- Deploys your Storybook to an AWS S3 bucket.
- Supports preview deployments for pull requests.
- Supports custom AWS S3 hosts. (e.g. DigitalOcean Spaces)
- Supports custom AWS regions.
- If pull preview it will comment on the PR with the URL to the deployed Storybook.
- If pull preview it will delete the deployment when the PR is closed or merged. (optional)

## Inputs

| Input  | Description | Required | Default |
| ------ | ----------- | -------- | ------- |
| `aws_s3_bucket` | The name of the S3 bucket where your Storybook will be deployed. | Yes | - |
| `aws_access_key_id` | Your AWS access key ID. | Yes | - |
| `aws_secret_access_key` | Your AWS secret access key. | Yes | - |
| `aws_region` | The AWS region where your S3 bucket is located. | Yes | - |
| `aws_s3_host` | The host of your S3 bucket. | No | `s3.amazonaws.com` |
| `aws_s3_endpoint` | The endpoint of your S3 bucket. | Yes | - |
| `preview` | A boolean value indicating whether this is a preview deployment. | No | `false` |
| `install_command` | The command to install dependencies. | No | `npm install` |
| `build_command` | The command to build your Storybook. | No | `npm run build-storybook` |

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
  uses: cloudsbird/storybook-s3@v1.0.0
  with:
    aws_s3_bucket: ${{ secrets.AWS_S3_BUCKET }} # e.g. my-bucket
    aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws_region: ${{ secrets.AWS_REGION }} # e.g. fra1
    aws_s3_host: ${{ secrets.AWS_S3_HOST }} # e.g. fra1.digitaloceanspaces.com
    aws_s3_endpoint: ${{ secrets.AWS_S3_ENDPOINT }} # e.g. https://fra1.digitaloceanspaces.com
    preview: 'true' # optional

```

## Examples

For more detailed examples of how to use this action, please see the [examples](./examples) folder in this repository.