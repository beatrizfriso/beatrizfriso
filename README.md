### Hey (:
<div align="center">
  <a href="https://www.linkedin.com/in/beatriz-friso-3625a7234/">
  <img height="180em" src="https://github-readme-stats.vercel.app/api?username=beatrizfriso&show_icons=true&theme=dracula&include_all_commits=true&count_private=true"/>
  <img height="60em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=beatrizfriso&layout=compact&langs_count=7&theme=dracula"/>
</div>

  
  on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v2
      - uses: yoshi389111/github-profile-3d-contrib@0.6.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          git commit -m "generated"
          git push
