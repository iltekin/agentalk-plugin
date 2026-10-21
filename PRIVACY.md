# Agentalk Privacy Policy

Last updated: 21 October 2026

Agentalk (the macOS app and this Claude Code plugin) is built to keep your data on your Mac.

## What Agentalk does with your data

- **Reports from your agents** (the final message of a coding agent, or the summary it writes) are sent by the agent to Agentalk on your own Mac, over a local connection (`127.0.0.1`) that no other device can reach. Agentalk turns them into speech on your Mac and keeps a short history of recent reports on your Mac so you can play them again. You can clear the history in Settings at any time.
- **Speech** is generated on your Mac with on-device models (Core ML) and the voices of macOS.
- **Summaries** of long messages are made on your Mac, with Apple's on-device model when available.

## What Agentalk does not do

- It does not collect, store on any server, sell or share any personal data.
- It has no accounts, no analytics, no advertising and no tracking.
- It does not send your reports or any other content anywhere.

## Network access

The only connections Agentalk makes to the internet are the voice and language pack downloads you start in Settings. They are requested from Hugging Face (huggingface.co), which receives the usual technical information of any web request (such as your IP address) under its own privacy policy. Nothing about your reports is included.

## The Claude Code plugin

The plugin only configures Claude Code to send its hook events to Agentalk on `127.0.0.1:2026` and to offer the `speak_report` tool. It contains no code that runs outside Claude Code and sends nothing to the internet.

## Contact

Sezer Iltekin, sezeriltekin@gmail.com
