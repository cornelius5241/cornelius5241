<head>
<div id="header" align="center">
  <img src="https://media.giphy.com/media/W6jfN7vS0jJTyehuuC/giphy.gif" width="100"/>
</div>

<div id="badges" align="center">
  <a href="https://www.linkedin.com/in/corneliu-tutuianu/">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge"/>
  </a>
  <a href="https://www.facebook.com/corneliu.tutu94/">
    <img src="https://img.shields.io/badge/Facebook-blue?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook Badge"/>
  </a>
  <a href="https://www.instagram.com/t.corneliu/">
    <img src="https://img.shields.io/badge/Instagram-orange?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram Badge"/>
  </a>
</div>

<div id="visits" align="center">
  <img src="https://komarev.com/ghpvc/?username=cornelius5241&style=flat-square&color=blue" alt=""/>
</div>

<div id="hello" align="center">
<h1>
  Hey there, I'm Corneliu
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>
</div>

<div align="center">
  <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="600" height="300"/>
</div>
</head>

on:
  schedule:
    - cron: '0 */12 * * *' # every 12 hours
  push:
    branches:
      - master
      - main
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        fetch-depth: 0
    - name: Generate README.md
      uses: teoxoy/profile-readme-stats@v1
      with:
        token: ${{ secrets.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 }}
    - name: Update README.md
      run: |
        if [[ "$(git status --porcelain)" != "" ]]; then
        git config user.name github-actions[bot]
        git config user.email 41898282+github-actions[bot]@users.noreply.github.com
        git add .
        git commit -m "Update README"
        git push
        fi
