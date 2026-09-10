---
description: This page describes the Drime Cloud integration
---

# Drime Cloud

Duplicati supports using [Drime Cloud](https://drime.cloud) as the storage destination since stable release v2.4. Note that Duplicati stores compressed and encrypted volumes on Drime Cloud and does not store files so they are individually accessible from Drime Cloud.

## User interface

<figure><picture><source srcset="../../.gitbook/assets/Screenshot 2026-09-10 at 14.42.18.png" media="(prefers-color-scheme: dark)"><img src="../../.gitbook/assets/Screenshot 2026-09-10 at 14.42.12.png" alt="Configuring the Drime Cloud destination"></picture><figcaption></figcaption></figure>

To configure the Drime Cloud destination, enter a unique path for the backup and an [API token](https://app.drime.cloud/account-settings#developers).

You can create an API token from the "Developers" section of your Drime Cloud account settings. The token is used as-is by Duplicati, so it will also work if you have 2FA enabled on your account.

## URL format for Commandline

To use Drime Cloud, use the following URL format:

```
drimecloud://<folder>/<subfolder>?api-token=*****
```

You can get an API token by visiting the [Developers section of your Drime Cloud account settings](https://app.drime.cloud/account-settings#developers).

It is also possible to use a username/password combination, but this is not recommended as the login does not support 2FA, so it will not work if 2FA is enabled on the account:

```
drimecloud://<folder>/<subfolder>?auth-username=email&auth-password=*****
```

If you use the username/password method, Duplicati will log in to Drime Cloud and obtain an access token for the session, which adds an extra round-trip before the backup can start.

## Advanced options

The following options can be added to the URL, or set as advanced options in the user interface:

* `--workspace-id`: The Drime Cloud workspace to store the backup in. Use `0` for the personal workspace, which is the default.
* `--soft-delete`: When enabled, files deleted by Duplicati are moved to the Drime Cloud trash instead of being permanently deleted. This is disabled by default.
* `--page-size`: Adjusts how many entries are requested per page when listing files. Defaults to `50`.
* `--api-url`: Set the Drime Cloud API URL if using a non-standard URL. Defaults to `https://app.drime.cloud/api/v1`.
