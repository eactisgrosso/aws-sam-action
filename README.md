# aws-sam-action

Github action for building and deploying with aws sam

## Example usage

```yaml
on: [push]

jobs:
  aws_sam:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@master

      - name: sam deploy
        uses: eactisgrosso/aws-sam-action
        with:
          node_version: 12.x
          stack_name: mystack
          parameter_overrides: StageName=Production
          no_fail_on_empty_changeset: true
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_DEFAULT_REGION: us-east-1
```

## Inputs

- `node_version` Nodejs version to install. (default: '12.x')
- `stack_name` Name of the Cloud Formation stack to create
- `parameter_overrides` Passes arguments to the template.yaml
- `no_fail_on_empty_changeset` Avoids raising an exception when there's no changes to deploy

## ENV

- `AWS_ACCESS_KEY_ID` **Required**
- `AWS_SECRET_ACCESS_KEY` **Required**

Get `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` from secrets.

## License

[MIT](LICENSE)

## Author

[eactisgrosso](https://github.com/eactisgrosso)
