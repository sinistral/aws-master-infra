## AWS Organization master bootstrap

[AWS Organizations][awsorgs] offers policy-based management for multiple AWS
accounts.  This repository provides CloudFormation templates to bootstrap an
account that is designated as the master in an organisation.  It currently
features IAM policies for role-based access to slave accounts, enforcing MFA
for both console and API access.

Corresponding CloudFormation templates to [bootstrap Subordinate
accounts][slaves] and take advantage of a suitably bootstrapped master are also
available.

## Usage

```
aws --region ${AWS_REGION} cloudformation create-change-set \
    --stack-name master \
    --change-set-name ${USER}-$(date -ju +"%Y%m%dT%H%M%S") \
    --change-set-type UPDATE \
    --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM \
    --template-body file://template/master.yaml
```

## License

Published under the [2-clause BSD license][license].

[awsorgs]: https://aws.amazon.com/organizations
[slaves]: https://github.com/sinistral/aws-slave-infra

[license]: https://opensource.org/licenses/BSD-2-Clause
