# My GitHub Profile Repository

This repository is used to display metrics on my GitHub profile. The metrics image below is generated using the [lowlighter/metrics](https://github.com/lowlighter/metrics) GitHub Action.

![Metrics](/github-metrics.svg)

## Setting up the GitHub Action

To set up the GitHub Action for generating the metrics image, follow these steps:

1. Create a GitHub personal token with the necessary permissions.
2. Add the token to your repository secrets as `METRICS_TOKEN`.
3. Create a `.github/workflows/update-readme.yml` file with the following content:

```yaml
name: Metrics
on:
  schedule: [{cron: "0 0 * * *"}]
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          config_timezone: India/Kolkata
          retries: 3
          retries_delay: 300
          config_display: large
          plugin_activity: yes
          plugin_activity_filter: issue, pr, release, fork, review, ref/create
          plugin_introduction: yes
          plugin_isocalendar: yes
          plugin_languages: yes
          plugin_languages_details: bytes-size, percentage
          plugin_languages_colors: rainbow
          plugin_languages_limit: 4
          plugin_lines: yes
          plugin_lines_sections: base, repositories
          plugin_repositories: yes
          plugin_repositories_featured: vishwamartur/vishwamartur
          plugin_repositories_affiliations: owner, collaborator
          plugin_licenses: yes
          plugin_achievements: yes
          plugin_achievements_threshold: bronze
          plugin_achievements_secrets: yes
          plugin_achievements_display: detailed
          plugin_achievements_limit: 5
```

## Generating the Metrics Image

The metrics image is generated automatically by the GitHub Action. You can customize the appearance and content of the image by modifying the configuration in the `.github/workflows/update-readme.yml` file.
