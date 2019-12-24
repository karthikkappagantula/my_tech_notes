# Identity and Resource Policies

## Identity policy
An IAM policy is basically a JSON file consisting statements. Usually a statement consisting of 3 key-value pairs.
* Effect - Determines whether the access is allowed or denied
* Action - List of APIs calls on AWS resource. Can have Single or List of actions or All (done using `*`) or mix of both (`S3:*`)
* Resource - Which resource the statement applies to.
* Condition - adds conditional permissions.

Simple example of a statement allowing all actions on S3 on any AWS resource:
```
{ 
  "Version" : "2019-01-01",
  "Statement" : {
      {
        "Effect" : "Allow",
        "Action" : "s3:*",
        "Resource" : "*"
      }
   }
}
```

It is always best to use AWS managemened identity policies or custom identity policies rather than using policy for each user.

## Resource policy
An IAM policy that applies to particular AWS resource. A deny policy on a resource will override any allow identity policy.
Principal is required/mandatory for a resource policy which is the identity trying to access resource. Identity can be a non IAM user too, like a user trying to access a image from bucket through publicly hosted website through resource policy set to allow access.

#### Important points:
* An explicit deny will override any explicit allow permissions.

* * *
# AWS official documents
IAM Policy ->  https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html




