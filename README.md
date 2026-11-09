# Mautrix X (Twitter) for YunoHost

Matrix / Synapse puppeting bridge for X (Twitter), packaged for [YunoHost](https://yunohost.org).
Upstream bridge: <https://github.com/mautrix/twitter> (mautrix-twitter v0.2609.0, Go / bridgev2).

## ⚠️ Status: looking for testers

This package installs, upgrades, backs up / restores and registers with Synapse correctly (tested on YunoHost 12, Debian 12), but **logging in with a real X (Twitter) account has not been tested yet**.

If you use X (Twitter) and want to help, please install it and report how it went in the issues (login, sending/receiving messages, media). If it works, I'll propose it to the YunoHost catalog.

## Install

```bash
sudo yunohost app install https://github.com/EpicTGuy/mautrix_twitter_ynh
```

Then, in your Matrix client, open a chat with the bot, send `login` and follow the [official authentication guide](https://docs.mau.fi/bridges/go/twitter/authentication.html).

## Features of this package

- Config generated from the upstream example config, with a config panel for the main settings: permissions, encryption, display name of contacts, number of past messages imported in new chats.
- Settings and bridge secrets are kept across upgrades (`config.yaml` is regenerated from the template, the bridge runs with `-n` and never rewrites it, so upgrades don't print its diff).
- Hardened: the binary and `config.yaml` belong to root and are only readable by the bridge user; strict systemd sandbox (`systemd-analyze security` ≈ 1.3); listens on 127.0.0.1 only.
- Double puppeting enabled automatically when a shared `doublepuppet` appservice is registered in Synapse (`/etc/matrix-<synapse instance>/app-service/doublepuppet.yaml`, see <https://docs.mau.fi/bridges/general/double-puppeting.html>).

Based on the [mautrix_whatsapp_ynh](https://github.com/YunoHost-Apps/mautrix_whatsapp_ynh) package. License: AGPL-3.0-or-later.
