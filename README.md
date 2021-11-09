# terraform-gaps
Brainstorming TF gaps

# Gaps I encounter

Some things that occasionally cause minor hiccups:
- How to avoid chicken/egg scenarios
- How to keep CI/CD pipelines in the same TF infra without manually requiring an `apply`
- How to easily apply permission changes if CodeBuild is restricted
  - e.g. if the build has `iam:*` but needs `ec2:*` we need to run it once to update IAM, then again to apply the EC2 changes

One thought: A "tag" of some sort on resources that allow them to run in a separate pipeline.

example idea of consecutive pipeline stages:
```
tf-static      # contains s3 buckets, secrets, IAM, etc.
build-app      # builds app
db-migrations  # db migrations
tf-dynamic     # creates APIs, lambdas, etc.
```


# Some things are solved by TF CDK

See https://gist.github.com/JAMSUPREME/67635016711e548d07f5e374aa5613bb#what-about-terraform-cdk
