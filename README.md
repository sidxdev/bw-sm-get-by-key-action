# bw-sm-get-by-key-action

Bitwarden Secrets Manager Action to get secrets by key. Inspired by the official action from Bitwarden https://github.com/bitwarden/sm-action but they only allow fetch by ID currently.


## Usage

To use the action, add a step to your GitHub workflow using the following syntax:

```
- name: Inject Secrets from Bitwarden Secrets Manager
  uses: sidxdev/bw-sm-get-by-key-action@v1.0.0
  with:
    access_token: ${{ secrets.BWS_ACCESS_TOKEN }}
    secrets: |
      SECRET_KEY > ENVIRONMENT_VARIABLE_NAME

- name: Use Secrets
  run: |
    some-command ${{ env.ENVIRONMENT_VARIABLE_NAME }}
```

## Parameters

- `access_token`

  The machine account access token for retrieving secrets.

  Use GitHub's [encrypted secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets) to store and retrieve machine account access tokens securely.

- `secrets`

  One or more secret keys to retrieve and the corresponding GitHub environment variable name to set.
  Multiple secret keys need to be in new lines.

  Example

  ```
      secrets: |
          SECRET_KEY > TEST_EXAMPLE
          SECRET_KEY_2 > TEST_EXAMPLE_2
  ```
