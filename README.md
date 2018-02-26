This repository is built to help de-mystify `root` attribute of eslint
configuration.

There are two folders: `root-true` and `root-false`; only
`root-true/.eslintrc.yaml` includes `root: true`.

And only `./.eslintrc.yaml` has `no-unused-vars`.

```shell
~/p/eslint-test (master) $ eslint --print-config root-true/b/foo.js
{
  "globals": {},
  "env": {},
  "rules": {
    "semi": [
      "error",
      "never"
    ]
  },
  "parserOptions": {},
  "root": false
}
~/p/eslint-test (master) $ eslint --print-config root-false/b/foo.js
{
  "globals": {},
  "env": {},
  "rules": {
    "no-unused-vars": [
      "error"
    ],
    "semi": [
      "error",
      "never"
    ]
  },
  "parserOptions": {},
  "root": false
}
```

Both report says `"root": false`, but for `root-true` case, rule
`no-unused-vars` is not included, indicating that `root: true` is in effect and
`root-true/.eslintrc.yaml` successfully works as a project root config which
stops the configuration from upper folders (i.e. `./.eslintrc.yaml`) to be read
in.

