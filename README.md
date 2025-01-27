## Hi there 👋

<!--
**jjpinto/jjpinto** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


name: Update README

on:
  workflow_dispatch:
  schedule:
    - cron: "0 2 * * *"
jobs:
  update-credly:
    name: Update Readme with badges
    runs-on: ubuntu-latest
    steps:
      - name: Badges - Readme
        uses: pemtajo/badge-readme@2.4.0
        with:       
          CREDLY_USER: "jorg.pinto"
  update-activity:
    runs-on: ubuntu-latest
    name: Update this repo's README with recent activity
    steps:
      - uses: actions/checkout@v4
      - uses: jamesgeorge007/github-activity-readme@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          COMMIT_MSG: "Updated README with recent activity"
          MAX_LINES: 15