# Protonmail Bridge

This package builds the CLI version of [protonmail-bridge](https://github.com/ProtonMail/proton-bridge) only. The pacxkage installs a system service, which however has to be started and activated manually once after installation. For

# First start

Before starting the background service, run the foreground app
```
protonmail-bridge --cli
```
to login to your account(s). In the CLI console type `help` for further information on how to login and manage accounts.

# Background service

After logging in and exiting the cli, start the background service with 
```
systemctl --user enable --now protonmail-bridge.service
````

Since only a single exclusive instance of protonmail bridge can run at any single time, the service must be stopped to use the foreground CLI (e.g. to login another user or check credentials). This package supplies the executable wrapper script `protonmail-bridge-cli` that

1. stops the service.
2. starts the CLI.
3. restarts the service when the CLI is closed.

# Requirements
```
sudo dnf install -y golang-bin libsecret-devel libfido2-devel libcbor-devel openssl-devel sqlite-devel
```
