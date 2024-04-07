# IMC Prosperity 2 Submitter

[![Build Status](https://github.com/jmerle/imc-prosperity-2-submitter/workflows/Build/badge.svg)](https://github.com/jmerle/imc-prosperity-2-submitter/actions/workflows/build.yml)
[![PyPI Version](https://img.shields.io/pypi/v/prosperity2submit)](https://pypi.org/project/prosperity2submit/)

This repository contains a command-line submitter for [IMC Prosperity 2](https://prosperity.imc.com/) algorithms. It uploads the algorithm, monitors its progress, downloads the logs, logs the final profit / loss, and opens the submission in my [IMC Prosperity 2 Visualizer](https://github.com/jmerle/imc-prosperity-2-visualizer) (optional), all in one command.

## Usage

Basic usage:
```sh
# Install the latest version of the submitter
$ pip install -U prosperity2submit

# Submit an algorithm
$ prosperity2submit <path to algorithm file>
```

Run `pip install -U prosperity2submit` again when you want to update the submitter to the latest version.

Submitting requires your Prosperity ID token that is stored in the local storage item with the `CognitoIdentityServiceProvider.<some id>.<email>.idToken` key on the Prosperity website. You can inspect the local storage items of a website by having the website open in the active tab, pressing <kbd>F12</kbd> to open the browser's developer tools, and going to the _Application_ (Chrome) or _Storage_ (Firefox) tab. From there, click on _Local Storage_ in the sidebar and select the website that appears underneath the sidebar entry.

The submitter will prompt you for the token when it needs it. The token is then stored in your system's credentials store for convenience. ID tokens are short-lived, so you'll be prompted somewhat regularly and old tokens persisted in the credentials store do not pose much of a security risk.

By default, the submitter automatically downloads the submission's logs after simulation is done to `submissions/<timestamp>.log`. You can change this file using the `--out <path to log file>` option, or disable downloading logs altogether using the `--no-logs` flag.

If you use my [IMC Prosperity 2 Visualizer](https://github.com/jmerle/imc-prosperity-2-visualizer), the `--vis` flag will automatically open the submission in the visualizer after the simulation ends successfully.

## Development

If you want to make changes to the submitter, clone (or fork and clone) this repository and run `pip install -e .` in the project's root. This installs the project in editable mode, so any changes you make are automatically taken into account the next time you run `prosperity2submit`.
