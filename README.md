# FAQ
Frequently Asked Questions

### `npm`

#### Table of Contents
- ["How do I speed up `install`?"](#speed)
- ["How do I fix a failing `install`?"](#failing)
- ["How do I generate a `npm-debug.log`?"](#debug)
- ["How can I get a `npm-debug.log` out of GitHub Actions/Workflow?"](#actions)
- ["How can I `audit` a package without installing it?"](#audit-no-install)
- ["How can I fully cache or vendor my deps so they're available offline?"](#vendor-deps)

#### <a name="speed"></a>"How do I speed up `install`?"

- [ ] Use the latest [`node`]() & [`npm`]() versions (ie. `brew update && brew install node` & `npm i -g npm@latest`)
- [ ] If you don't need dev dependencies, add the flag `--production`
- [ ] If you don't need to **audit**, add the flag `--no-audit`
- [ ] If you already have some of your modules cached, add the flag `--prefer-offline`

#### <a name="failing"></a>"How do I fix a failing `install`?"

- [ ] Check if you're using the latest [`node`]() & [`npm`]()
- [ ] Check if the registry is down
- [ ] Check if your network is having issues (ie. slow or intermitant connection)
- [ ] Check if your network is blocking certain requests (ie. behind a corporate firewall)
- [ ] Check if [speeding up your installs]() helps
- [ ] If you're project has peer dependecy conflict warnings or failures, try adding the flag `--legacy-peer-deps`
- [ ] 

#### <a name="debug"></a>"How do I generate a `npm-debug.log`?"

- Add the flag `--timing` to any command run (ex. `npm install express --timing`)

#### <a name="actions"></a>"How can I get a `npm-debug.log` out of GitHub Actions/Workflow?"

- Add a [`actions/upload-artifact`](https://github.com/actions/upload-artifact) step dedicated to saving debug logs as part of your workflow

```yaml
# example: ./github/workflows/*.yml
- uses: actions/upload-artifact@v2
  with:
    name: npm-debug-logs
    path: ~/.npm/_logs/*-debug.log
```

#### <a name="audit-no-install"></a>"How can I `audit` a package without installing it?"

- Use this [`npm-audit` bash script](https://gist.github.com/darcyclarke/6d9e9de555997e9aa9fe828fe1fdef7d) (note: it runs `install` in a tmp directoy w/ `--package-lock-only` & then `audit` - should avoid firewalls/network issues w/ downloading vulnerable tars)

#### <a name="vendor-deps"></a>"How can I fully cache or vendor my deps so they're available offline?"

- Set your `cache` config (ex. in `.npmrc` `cache = ./some-local-cache-dir` or w/ `npm config set cache ./some-local-cache-dir`)
- Run `npm install`
- You should now be able to run `npm install` w/ the flag `--offline` or kill your network & it'll just work™️
- [Example in the wild](https://github.com/darcyclarke/npm-offline-cache)
