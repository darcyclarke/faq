# FAQ
Frequently Asked Questions

### npm 

#### How do I speed up `install`?

- [ ] Use the latest [`node`]() & [`npm`]() versions (ie. `brew update && brew install node` & `npm i -g npm@latest`)
- [ ] If you don't need dev dependencies, add the flag `--production`
- [ ] If you don't need to **audit**, add the flag `--no-audit`
- [ ] If you already have some of your modules cached, add the flag `--prefer-offline`

#### How do I fix a failing `install`?

- [ ] Check if you're using the latest [`node`]() & [`npm`]()
- [ ] Check if the registry is down
- [ ] Check if your network is having issues (ie. slow or intermitant connection)
- [ ] Check if your network is blocking certain requests (ie. behind a corporate firewall)
- [ ] Check if [speeding up your installs]() helps
- [ ] If you're project has peer dependecy conflict warnings or failures, try adding the flag `--legacy-peer-deps`
- [ ] 

#### How dow I generate a `*-debug.log`?

- Add the flag `--timing` to any command run (ex. `npm install express --timing`)

#### How can I get a `*-debug.log` out of GitHub Actions/Workflow?

- Add [`actions/upload-artifact`](https://github.com/actions/upload-artifact) to your workflow
- Example:
```yaml
...
- uses: actions/upload-artifact@v2
  with:
    name: npm-debug-logs
    path: ~/.npm/_logs/*-debug.log
...
```
