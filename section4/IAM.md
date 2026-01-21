### IAM: Users & Groups

- **IAM** = Identity and Access Management, Global service
- **Root account** create by default, shouldn't be used or shard
- **Users** are people whithin your **organizatoin**, and can be grouped
- **Groups** only contain users, not other groups (ex. Developers Group, Group Audit Team )
- Users don't have to belon to a group, and user can belong to multiple groups

### IAM: Permissions

- Users or Groups can be assigned JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the least privilege principle: don't give more permissions than a user needs

### IAM Policies inheritance

- users inherit the policies of the groups they belong to.

### IAM Policies Structure

```
{
  "Version": "2012-10-17".
  "Id": "S3-Account-Permissions",
  "Statement":[
    {
      "Sid": "1",
      "Effect": "Allow",
      "Principal": {
        "AWS": ["arn:aws:iam::123456781012:root"]
      },
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": ["arn:aws:s3::::mybucket/*"]192
    }
  ]
}
```

- Consists of
  - Version: policy language version. always include "2012-10-17"
  - Id: an identifer for the policy (optional)
- Statements consists of
  - Sid: an identifer for the statement(optional)
  - **_Effect_**: (Aloow/Deny) whether the statement allows or denies access
  - **_Pincipal_**: account/user/role/ to which this policy applied to
  - **_Action_**: list of actions this policy allows or denies
  - **_Resource_**: list of resources to which the actions applied to
    -Condition: conditions for when this policy is in effect(Optional)

### IAM - password Policy

- strong passwords = higer security for your account
- In AWS you can setup a password policy
  - Set a minimum password length
  - require specific character types
- Allow all IAM users to change their own passwords
- Require users to change their password after some time

### Multi Factor Authentication

- User have asccess to your account and can possibly change configurations of delete resources in your AWS account
- MFA = password you know + security device you own
- benefit of MFA = if a password is stolen or hacked, the account is not compromised

### MFA device options in AWS

- virtual MFA device
  - Google Autherticator
  - Auty

- Universal 2nd Factor(U2F) Security Key
  - Yubikey by Yubico(3rd party)

- Hardware key Fob MFA Device
  - provided by Gemalto(3rd party)

- Hardware Key Fob MFA Device for AWS GovCloud
  - provided by surePassId
