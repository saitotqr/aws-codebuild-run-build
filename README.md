## AWS CodeBuild Run Build for GitHub Actions :sheep:

This repo forked from [aws-codebuild-run-build@v1.0.13](https://github.com/aws-actions/aws-codebuild-run-build/releases/tag/v1.0.13) and added Params to set sourceVersion


# Examples

`commit-hash-to-override` is a newly added parameter.

```yaml
- name: Configure AWS Credentials
  uses: aws-actions/configure-aws-credentials@v1
  with:
    aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws-region: us-east-2
- name: Run CodeBuild
  uses: aws-actions/aws-codebuild-run-build@v1
  with:
    project-name: CodeBuildProjectName
    buildspec-override: path/to/buildspec.yaml or inline buildspec definition
    compute-type-override: compute-type
    environment-type-override: environment-type
    image-override: ecr-image-uri
    commit-hash-to-override: 0000000000000000000000000000000000000000
    env-vars-for-codebuild: |
      custom,
      requester,
      event-name
  env:
    custom: my environment variable
    requester: ${{ github.actor }}
    event-name: ${{ github.event_name }}
```
