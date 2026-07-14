# 👮 Check User Permission

![](https://img.shields.io/github/workflow/status/actions-cool/check-user-permission/CI?style=flat-square)
[![](https://img.shields.io/badge/marketplace-check--user--permission-blueviolet?style=flat-square)](https://github.com/marketplace/actions/check-user-permission)
[![](https://img.shields.io/github/v/release/actions-cool/check-user-permission?style=flat-square&color=orange)](https://github.com/actions-cool/check-user-permission/releases)

## 🚀 How to use?

```yml
name: Check User Permission

on:
  issues:
    types: [opened, edited]

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions-cool/check-user-permission@v2
```

### Input

| Name | Desc | Type | Required |
| -- | -- | -- | -- |
| token | GitHub token | string | ✖ |
| require | Test whether the user meets the required permission | string | ✖ |
| username | Obtained from the context by default, can also be customized to pass in | string | ✖ |
| check-bot | Check whether the user is a bot | boolean | ✖ |
| check-contributor | Check whether the user is contributor | boolean | ✖ |

- User permission: `admin` > `write` > `read`
- `username` support [github context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context)
  - `actor`: The Default
  - `triggering_actor`: The username of the user that initiated the workflow run even re-run
  - Example: `username: github.triggering_actor`

### Output

- `user-permission`: `read` | `write` | `admin`
- `require-result`: The result of require
- `check-result`: The result of check


> How to use?
> - https://github.com/actions-cool/issues-helper#outputs-%E4%BD%BF%E7%94%A8
> - https://github.com/actions-cool/check-user-permission/blob/main/.github/workflows/check-permission.yml
> - https://github.com/actions-cool/test-ci/blob/main/.github/workflows/test-check-user.yml

## ⚡ Feedback

You are very welcome to try it out and put forward your comments. You can use the following methods:

- Report bugs or consult with [Issue](https://github.com/actions-cool/check-user-permissionissues)
- Submit [Pull Request](https://github.com/actions-cool/check-user-permission/pulls) to improve the code of `check-user-permission`

欢迎加入 钉钉交流群

![](https://github.com/actions-cool/resources/blob/main/dingding.jpeg?raw=true)

## Changelog

[CHANGELOG](./CHANGELOG.md)

## LICENSE

[MIT](./LICENSE)

## Privacy

This Action contacts Chainguard's licensing server to verify authorization. Connection metadata (IP address, GitHub repository identifier, timestamp, and any metadata encoded in the auth token) is transmitted to Chainguard, Inc. even if authorization is denied in accordance with our [Privacy Notice](https://www.chainguard.dev/legal/privacy-notice)
