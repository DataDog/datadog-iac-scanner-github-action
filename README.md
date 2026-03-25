# Datadog IaC Scanner Github Action

A GitHub action to run the [Datadog IaC Scanner] in your repository and upload the result to Datadog.

This action uses the [datadog-ci] standalone binary (installed via [install-datadog-ci-github-action]), so **no Node.js setup is required**.

For setup instructions, configuration options, and examples, see the [IaC Security and GitHub Actions documentation].

## Basic usage

```yaml
name: Datadog IaC Scan
on: [push]
jobs:
  datadog-iac-scan:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - uses: actions/checkout@v4
      - uses: DataDog/datadog-iac-scanner-github-action@v1
        with:
          dd_api_key: ${{ secrets.DD_API_KEY }}
          dd_app_key: ${{ secrets.DD_APP_KEY }}
```

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.

[Datadog IaC Scanner]: https://github.com/DataDog/datadog-iac-scanner
[datadog-ci]: https://github.com/DataDog/datadog-ci
[install-datadog-ci-github-action]: https://github.com/DataDog/install-datadog-ci-github-action
[IaC Security and GitHub Actions documentation]: https://docs.datadoghq.com/security/code_security/iac_security/github_actions/
