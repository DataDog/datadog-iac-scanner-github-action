# Datadog IaC Scanner Github Action

A GitHub action to run the [Datadog IaC Scanner] in your repository and upload the result to Datadog.

This action uses the [datadog-ci] standalone binary (installed via [install-datadog-ci-github-action]), so **no Node.js setup is required**.

## Usage

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

### Scan only certain directories and files

```yaml
- uses: DataDog/datadog-iac-scanner-github-action@v1
  with:
    paths: prepare,deploy,configs/config1.yaml
    dd_api_key: ${{ secrets.DD_API_KEY }}
    dd_app_key: ${{ secrets.DD_APP_KEY }}
```

### Upload the results to a different DataDog site

```yaml
- uses: DataDog/datadog-iac-scanner-github-action@v1
  with:
    dd_site: datadoghq.eu
    dd_api_key: ${{ secrets.DD_API_KEY }}
    dd_app_key: ${{ secrets.DD_APP_KEY }}
```

## Inputs

| Name         | Description                                                                                                          | Required | Default         |
| ------------ | -------------------------------------------------------------------------------------------------------------------- | -------- | --------------- |
| `dd_api_key` | Your Datadog API key. This key is created by your [Datadog organization] and should be stored as a [secret].         | Yes      |                 |
| `dd_api_key` | Your Datadog application key. This key is created by your [Datadog organization] and should be stored as a [secret]. | Yes      |                 |
| `dd_app_key` | Datadog application key.                                                                                             | Yes      |                 |
| `dd_site`    | The [Datadog site] to upload the results to.                                                                         | No       | `datadoghq.com` |
| `paths`      | A comma-separated list of directories or files to scan.                                                              | No       | `.`             |

## Supported platforms

| Runner OS | Architecture  |
| --------- | ------------- |
| Linux     | x86_64, arm64 |
| macOS     | arm64         |
| Windows   | x86_64        |

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.

[Datadog IaC Scanner]: https://github.com/DataDog/datadog-iac-scanner
[datadog-ci]: https://github.com/DataDog/datadog-ci
[install-datadog-ci-github-action]: https://github.com/DataDog/install-datadog-ci-github-action
[Datadog organization]: https://docs.datadoghq.com/account_management/api-app-keys/
[secret]: https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository
[Datadog site]: https://docs.datadoghq.com/getting_started/site/
