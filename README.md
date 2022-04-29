# Build Vue and deploy it to Github Pages 🚀
This Action will Build your Vue Project and deploy it to a specified branch

## Getting Started 🎉
1. If you are using GitHub pages (`gh-pages` branch), create the `vue.config.js` file and add this to your `vue.config.js` (and rename "YourRepoName" to your repo name)
```javascript
module.exports = {
    publicPath: '/YourRepoName/'
}
```
2. Create a Github Actions Workflow file and add this to it (and replace "YourGithubName" and "YourRepoName" with the names)
```yml
name: Build Vue
on: [push]
jobs:
  build_vue:
    runs-on: ubuntu-latest
    name: Build Vue
    steps:
    - uses: actions/checkout@v2
    - id: Build-Vue
      uses: xRealNeon/VuePagesAction@1.0.1
      with:
        username: 'YourGithubName'
        reponame: 'YourRepoName'
        token: ${{ secrets.GITHUB_TOKEN }} # Leave this line unchanged
        branch: 'YourBranchName' # defaults to 'gh-pages' but can be changed
```
3. If you want to use GitHub Pages, go to Settings -> Scroll down to GitHub Pages -> Select your branch name as branch and `/` as directory 

## Options 🔧
|   Name    |            Description           |     Default    | Required |
|:---------:|:--------------------------------:|:--------------:|:--------:|
| username  |           Your username          |        -       |     ✅    |
| reponame  |       Your repository name       |        -       |     ✅    |
|   token   | Please leave this line unchanged |        -       |     ✅    |
| gitemail  |         Git commit email         | CI@example.com |     ❌    |
|  gitname  |          Git commit name         |       CI       |     ❌    |
|  gitmsg   |        Git commit message        |     deploy     |     ❌    |
| gitbranch |           Custom branch          |    gh-pages    |     ❌    |
|  useyarn  |         Use yarn to build        |      false     |     ❌    |
