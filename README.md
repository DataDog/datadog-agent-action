# Datadog Agent Action

Starts a Datadog agent in a docker container to be used for GitHub Actions CI tests.

## Usage
```yaml
name: Test Code
on: [push]
jobs:
  test:
    steps:
      - uses: datadog/agent-github-action
        with:
            apiKey: ${{ secrets.DD_API_KEY }}
      - uses: actions/checkout@v2
      - run: make tests
```

## Inputs

The action has the following options:

| Name | Description | Required | Default |
| ---- | ----------- | -------- | ------- |
| `api_key` | The API key for the Datadog site. | True | |
| `container_name` | The name for the docker container that runs the agent. | True | `datadog-agent` |
| `image_name` | The docker registry and image to pull. It has to be one of [`datadog/agent` (Docker), `gcr.io/datadoghq/agent` (GCR), `public.ecr.aws/datadog/agent` (ECR)] | True | `datadog/agent` |
| `datadog_site` | The Datadog site to send data to. | True | `datadoghq.com` |