# AWS IAM CLI Command Reference with Examples

A structured overview of all `aws iam` subcommands grouped by function, including a common use case example for each.

---

## 🧑💼 User Management

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-user` | Creates a new IAM user. | `aws iam create-user --user-name Alice` |
| `delete-user` | Deletes an IAM user account. | `aws iam delete-user --user-name Alice` |
| `get-user` | Retrieves details about a specified user. | `aws iam get-user --user-name Alice` |
| `update-user` | Changes a user’s name or path. | `aws iam update-user --user-name Alice --new-user-name Alicia` |
| `list-users` | Lists all IAM users in the account. | `aws iam list-users` |
| `create-login-profile` | Creates a password for AWS Management Console access. | `aws iam create-login-profile --user-name Alice --password "MyPassword123!"` |
| `delete-login-profile` | Deletes the console login credential. | `aws iam delete-login-profile --user-name Alice` |
| `update-login-profile` | Updates a user’s console password. | `aws iam update-login-profile --user-name Alice --password "NewPass456!"` |
| `change-password` | Changes the IAM user’s own password. | `aws iam change-password --old-password old123 --new-password new456` |
| `create-access-key` | Creates a new access key pair for programmatic access. | `aws iam create-access-key --user-name Alice` |
| `delete-access-key` | Deletes a specified access key. | `aws iam delete-access-key --user-name Alice --access-key-id AKIA...` |
| `update-access-key` | Disables or enables an access key. | `aws iam update-access-key --access-key-id AKIA... --status Inactive --user-name Alice` |
| `list-access-keys` | Lists access keys associated with a user. | `aws iam list-access-keys --user-name Alice` |
| `get-access-key-last-used` | Checks when an access key was last used. | `aws iam get-access-key-last-used --access-key-id AKIA...` |
| `upload-ssh-public-key` | Uploads an SSH key for CodeCommit. | `aws iam upload-ssh-public-key --user-name devops --ssh-public-key-body "ssh-rsa AAAA..."` |
| `list-ssh-public-keys` | Lists SSH keys for a user. | `aws iam list-ssh-public-keys --user-name devops` |
| `delete-ssh-public-key` | Deletes a user’s SSH key. | `aws iam delete-ssh-public-key --user-name devops --ssh-public-key-id APK123` |

---

## 👥 Group Management

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-group` | Creates a new group. | `aws iam create-group --group-name Developers` |
| `delete-group` | Deletes a specified group. | `aws iam delete-group --group-name Developers` |
| `list-groups` | Lists all IAM groups. | `aws iam list-groups` |
| `get-group` | Displays users in a group. | `aws iam get-group --group-name Developers` |
| `update-group` | Changes a group’s name or path. | `aws iam update-group --group-name Developers --new-group-name DevTeam` |
| `add-user-to-group` | Adds a user to a group. | `aws iam add-user-to-group --user-name Alice --group-name Developers` |
| `remove-user-from-group` | Removes a user from a group. | `aws iam remove-user-from-group --user-name Alice --group-name Developers` |
| `list-groups-for-user` | Lists groups a user belongs to. | `aws iam list-groups-for-user --user-name Alice` |
| `put-group-policy` | Adds/updates an inline policy in a group. | `aws iam put-group-policy --group-name Developers --policy-name S3Access --policy-document file://policy.json` |
| `get-group-policy` | Retrieves a group’s inline policy. | `aws iam get-group-policy --group-name Developers --policy-name S3Access` |
| `delete-group-policy` | Deletes a group’s inline policy. | `aws iam delete-group-policy --group-name Developers --policy-name S3Access` |
| `attach-group-policy` | Attaches a managed policy to a group. | `aws iam attach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess` |
| `detach-group-policy` | Detaches a managed policy. | `aws iam detach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess` |
| `list-attached-group-policies` | Lists managed policies attached to a group. | `aws iam list-attached-group-policies --group-name Developers` |

---

## 🧱 Role Management

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-role` | Creates a new role with a trust policy. | `aws iam create-role --role-name LambdaExecRole --assume-role-policy-document file://trust.json` |
| `delete-role` | Deletes a role. | `aws iam delete-role --role-name LambdaExecRole` |
| `get-role` | Retrieves role details. | `aws iam get-role --role-name LambdaExecRole` |
| `update-role` | Modifies a role’s path or max session duration. | `aws iam update-role --role-name LambdaExecRole --max-session-duration 7200` |
| `update-assume-role-policy` | Updates a role’s trust policy. | `aws iam update-assume-role-policy --role-name LambdaExecRole --policy-document file://trust.json` |
| `list-roles` | Lists all IAM roles. | `aws iam list-roles` |
| `attach-role-policy` | Attaches a managed policy. | `aws iam attach-role-policy --role-name LambdaExecRole --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole` |
| `detach-role-policy` | Detaches a managed policy. | `aws iam detach-role-policy --role-name LambdaExecRole --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole` |
| `put-role-policy` | Adds or updates an inline policy. | `aws iam put-role-policy --role-name LambdaExecRole --policy-name InlinePolicy --policy-document file://policy.json` |
| `delete-role-policy` | Deletes an inline policy. | `aws iam delete-role-policy --role-name LambdaExecRole --policy-name InlinePolicy` |
| `list-role-policies` | Lists inline policies. | `aws iam list-role-policies --role-name LambdaExecRole` |
| `create-instance-profile` | Creates an instance profile. | `aws iam create-instance-profile --instance-profile-name WebInstanceProfile` |
| `add-role-to-instance-profile` | Adds a role to a profile. | `aws iam add-role-to-instance-profile --instance-profile-name WebInstanceProfile --role-name EC2Role` |

---

## 📜 Policy Management

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-policy` | Creates a new managed policy. | `aws iam create-policy --policy-name S3AccessPolicy --policy-document file://policy.json` |
| `delete-policy` | Deletes a managed policy. | `aws iam delete-policy --policy-arn arn:aws:iam::123456789012:policy/S3AccessPolicy` |
| `create-policy-version` | Creates a new version for a policy. | `aws iam create-policy-version --policy-arn arn:aws:iam::123456789012:policy/S3AccessPolicy --policy-document file://new.json --set-as-default` |
| `delete-policy-version` | Removes a non-default policy version. | `aws iam delete-policy-version --policy-arn arn:aws:iam::123:policy/S3AccessPolicy --version-id v2` |
| `get-policy` | Displays details about a policy. | `aws iam get-policy --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess` |
| `list-policies` | Lists managed policies. | `aws iam list-policies --scope AWS` |
| `list-policy-versions` | Lists a policy’s versions. | `aws iam list-policy-versions --policy-arn arn:aws:iam::123:policy/S3AccessPolicy` |
| `simulate-custom-policy` | Tests access defined by a policy. | `aws iam simulate-custom-policy --policy-input-list file://policy.json --action-names s3:ListBucket` |
| `list-entities-for-policy` | Shows which entities a policy is attached to. | `aws iam list-entities-for-policy --policy-arn arn:aws:iam::123:policy/S3AccessPolicy` |

---

## 🔒 MFA and Security Credentials

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-virtual-mfa-device` | Provisions a new virtual MFA device. | `aws iam create-virtual-mfa-device --virtual-mfa-device-name AliceMFA --outfile QRCODE.png` |
| `enable-mfa-device` | Enables MFA for a user. | `aws iam enable-mfa-device --user-name Alice --serial-number arn:aws:iam::123:mfa/AliceMFA --authentication-code1 123456 --authentication-code2 789012` |
| `list-mfa-devices` | Lists MFA devices for a user. | `aws iam list-mfa-devices --user-name Alice` |
| `deactivate-mfa-device` | Disables MFA for a user. | `aws iam deactivate-mfa-device --user-name Alice --serial-number arn:aws:iam::123:mfa/AliceMFA` |
| `resync-mfa-device` | Resynchronizes codes. | `aws iam resync-mfa-device --user-name Alice --serial-number arn:aws:iam::123:mfa/AliceMFA --authentication-code1 111111 --authentication-code2 222222` |
| `generate-credential-report` | Generates a credential usage report. | `aws iam generate-credential-report` |
| `get-credential-report` | Retrieves the credential report. | `aws iam get-credential-report --output text` |

---

## 🌐 Federated Identity and Providers

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `create-open-id-connect-provider` | Registers an OIDC identity provider. | `aws iam create-open-id-connect-provider --url https://accounts.google.com --thumbprint-list abcd1234 --client-id-list myApp` |
| `get-open-id-connect-provider` | Retrieves OIDC provider info. | `aws iam get-open-id-connect-provider --open-id-connect-provider-arn arn:aws:iam::123:oidc-provider/accounts.google.com` |
| `delete-open-id-connect-provider` | Removes an OIDC provider. | `aws iam delete-open-id-connect-provider --open-id-connect-provider-arn arn:aws:iam::123:oidc-provider/...` |
| `create-saml-provider` | Creates a SAML identity provider. | `aws iam create-saml-provider --saml-metadata-document file://saml.xml --name CorpSAML` |
| `get-saml-provider` | Retrieves SAML provider details. | `aws iam get-saml-provider --saml-provider-arn arn:aws:iam::123:saml-provider/CorpSAML` |
| `delete-saml-provider` | Deletes a SAML provider. | `aws iam delete-saml-provider --saml-provider-arn arn:aws:iam::123:saml-provider/CorpSAML` |
| `create-service-linked-role` | Creates a service-linked role for AWS services. | `aws iam create-service-linked-role --aws-service-name ecs.amazonaws.com` |

---

## 📦 Server Certificates

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `upload-server-certificate` | Uploads a new SSL/TLS cert. | `aws iam upload-server-certificate --server-certificate-name WebCert --certificate-body file://cert.pem --private-key file://key.pem` |
| `get-server-certificate` | Retrieves certificate details. | `aws iam get-server-certificate --server-certificate-name WebCert` |
| `list-server-certificates` | Lists all uploaded certs. | `aws iam list-server-certificates` |
| `update-server-certificate` | Renames or updates metadata. | `aws iam update-server-certificate --server-certificate-name WebCert --new-server-certificate-name NewWebCert` |
| `delete-server-certificate` | Deletes a certificate. | `aws iam delete-server-certificate --server-certificate-name WebCert` |

---

## 🧾 Reporting, Tagging, and Miscellaneous

| Command | Description | Example Use Case |
|----------|--------------|------------------|
| `get-account-summary` | Displays IAM resource counts and limits. | `aws iam get-account-summary` |
| `get-account-password-policy` | Retrieves current account password policy. | `aws iam get-account-password-policy` |
| `update-account-password-policy` | Updates the password requirements. | `aws iam update-account-password-policy --require-symbols --minimum-password-length 12` |
| `delete-account-password-policy` | Deletes the existing password policy. | `aws iam delete-account-password-policy` |
| `generate-service-last-accessed-details` | Generates a report of service access. | `aws iam generate-service-last-accessed-details --arn arn:aws:iam::123:role/LambdaExecRole` |
| `get-service-last-accessed-details` | Fetches usage details for an entity. | `aws iam get-service-last-accessed-details --job-id JOB123` |
| `tag-user` / `untag-user` | Adds or removes tags from a user. | `aws iam tag-user --user-name Alice --tags Key=Environment,Value=Dev` |
| `tag-role` / `untag-role` | Tags or removes tags from roles. | `aws iam tag-role --role-name LambdaExecRole --tags Key=App,Value=API` |
| `wait` | Waits for a specific IAM resource state. | `aws iam wait user-exists --user-name Alice` |
| `wizard` | Invokes setup or guided workflows. | `aws iam wizard create-user` |
| `help` | Displays IAM help text. | `aws iam help` |

---

✅ **Tip:**
Use `aws iam <command> help` to view required parameters and example usage for any specific subcommand.