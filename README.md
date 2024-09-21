# org-formation-sso-import

An experimental™️ script to import AWS SSO groups, permission sets and
assignments into a
[OrgFormation](https://github.com/org-formation/org-formation-cli) workspace.

## The problem

If you have already bootstrapped your Landing Zone manually (or with some other
tool other than OrgFormation, e.g. Control Tower) and you want to start using
OrgFormation, you can easily import all your accounts and organizational units
with the `org-formation import` command. However, you will still need to
manually recreate all your AWS SSO groups, permission sets and assignments in
your OrgFormation template.

This script aims to automate this process by importing all your AWS SSO
configuration into your OrgFormation template and making sure all the existing
resources are imported correctly into the CloudFormation stacks managed by
OrgFormation.

## Installation

```bash
npm install -g org-formation-sso-import
```

## Requirements

- Node.js 20.x or later
- AWS CLI (configured with the right permissions - ideally an admin user in the
  management account)

## Usage

In your OrgFormation workspace, run the following command:

```bash
org-formation-sso-import
```

Note: this command assumes that your `organization.yml` file is in the root of
your workspace.

### Configuration options

You can get the list of available options by running:

```bash
org-formation-sso-import --help
```

This will print something like:

```plain
  --stack-name <value>
  -s <value>
  Pass the name of the stack to be deployed (default: "SsoAssignments")

  --identity-store-id <value>
  -i <value>
  Pass the id of the identity store. If not provided will try to fetch for an existing one

  --managing-instance-arn <value>
  -m <value>
  Pass the arn of the managing instance. If not provided will try to fetch for an existing one

  --verbose
  -v
  Enables verbose mode

  --help
  -h
  Prints this help
```