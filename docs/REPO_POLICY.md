# Repo policy
This public repository stores **reusable prompts, templates, validators, documentation and code only**.

Never commit API keys, credentials, private files, third-party media without permission, sensitive evidence or platform session cookies. Do not assume a web-visible asset may be redistributed.

For each new episode duplicate `templates/EPISODE_STARTER/` into a separate working directory with a new EPxxx ID. Large audio/video/PNG/MP4 data should be stored outside Git or in an approved licensed asset store; commit a manifest and integrity hash instead.

Do not edit the EPISODE_STARTER template in place when producing EP001, EP002, etc. Changes to reusable formats require version bump, examples and validator changes.

Branch + pull request for substantive changes. Do not merge to main until required QA and approval.
