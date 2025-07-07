# Vocera Run Test Auto

Run automated test scenarios against Vocera agents directly from your GitHub workflow.

This composite action allows you to configure and execute scenarios against specified Vocera agents.

## Usage

Add the following workflow to your repository (e.g., `.github/workflows/deploy.yml`):

```yaml
name: Vocera Run Test Auto

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  run-scenarios:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - name: Run Vocera Scenarios
        uses: vocera-ai/vocera-run-test-auto@main
        with:
          API_BASE_URL: ${{ secrets.API_BASE_URL }}
          API_KEY: ${{ secrets.API_KEY }}
          agent_id: ${{ env.AGENT_ID }}
          scenarios: ${{ env.SCENARIOS }}
          frequency: ${{ env.FREQUENCY }}
          timeout: ${{ env.TIMEOUT }}
          poll_interval: ${{ env.POLL_INTERVAL }}
```

## Secrets

| Name          | Description                           | Required |
|---------------|---------------------------------------|----------|
| API_BASE_URL  | Base URL for connecting to Vocera API | true     |
| API_KEY       | API Key for authentication            | true     |

## Environment Variables

| Name          | Description                                  | Required |
|---------------|----------------------------------------------|----------|
| AGENT_ID      | ID of the agent where scenarios are executed | true     |
| SCENARIOS     | Comma-separated list of scenario IDs         | true     |
| FREQUENCY     | Number of times to run each scenario         | true     |
| TIMEOUT       | Timeout in seconds                           | true     |
| POLL_INTERVAL | Poll interval in seconds                     | true     |

Make sure to configure the secrets in your GitHub repository settings under "Settings" → "Secrets and variables" → "Actions". And the environment variables in your repository settings under "Settings" → "Secrets and variables" → "Actions".

## License

This project is licensed under the [MIT License](LICENSE).

## Support

For questions or assistance, please open an issue in this repository or contact Vocera AI support.

---

© 2024 Vocera AI. All rights reserved.
