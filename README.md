# Exact dependency checker

<a href="https://github.com/matheusjardimb/js-exact-dependency-action/actions"><img alt="javscript-action status" src="https://github.com/matheusjardimb/js-exact-dependency-action/actions/workflows/test.yml/badge.svg"></a>
<a href="https://img.shields.io/github/v/release/matheusjardimb/js-exact-dependency-action"><img alt="release" src="https://img.shields.io/github/v/release/matheusjardimb/js-exact-dependency-action"></a>

[//]: # (<a href="https://img.shields.io/badge/Contributor%20Covenant-2.0-4baaaa.svg"><img alt="Contributor Covenant" src="https://img.shields.io/badge/Contributor%20Covenant-2.0-4baaaa.svg"></a>)

Use this template to bootstrap the creation of a JavaScript action. :rocket: Alternative
to [`actions/javascript-action`](https://github.com/actions/javascript-action).

This template includes [release automation](.github/workflows), [tests](tests), linting, publishing, starter docs, and
versioning guidance.

## Usage

Reference the published [semantic tag](https://semver.org/), e.g. major:

```yaml
uses: matheusjardimb/js-exact-dependency-action@v1
with:
  milliseconds: 1000
```

or minor:

```yaml
uses: matheusjardimb/js-exact-dependency-action@v1.0
with:
  milliseconds: 1000
```

or patch:

```yaml
uses: matheusjardimb/js-exact-dependency-action@v1.0.0
with:
  milliseconds: 1000
```

See the [actions tab](https://github.com/matheusjardimb/js-exact-dependency-action/actions) for runs of this action! :rocket:

## Development

#### 1. Update your action metadata in `action.yml`

[`action.yml`](action.yml) defines the inputs and output for your action.

Update the action.yml with your name, description, inputs and outputs for your action.

See the [documentation](https://docs.github.com/en/actions/creating-actions/metadata-syntax-for-github-actions).

#### 2. Write your action code in `lib`

Most toolkit and CI/CD operations involve async operations so the action is run in an async function.

```javascript
const core = require('@actions/core');
...

async function run() {
    try {
    ...
    } catch (error) {
        core.setFailed(error.message);
    }
}

run()
```

See the [toolkit documentation](https://github.com/actions/toolkit/blob/master/README.md#packages) for the various
packages.

#### 3. Test your action in `tests`

[Jest](https://jestjs.io/) and [Nock](https://github.com/nock/nock) are included as suggestions for test and mocking
frameworks.

A sample [Unit Test workflow](.github/workflows/test.yml) is provided which runs on every pull request and push to
the `main` branch.

#### 4. Automate releases with GitHub Actions

The entrypoint to your action is defined by `runs.using` in `action.yml`.

This project uses a `prepare` script leveraging `@vercel/ncc` to compile and package the code into one
minified `dist/index.js` file, enabling fast and reliable execution and preventing the need to check in the whole
dependency tree in `node_modules`.

Here, `dist` is intentionally _not_ committed to Git branches for three reasons:

1. Encourage users to reference your action using [semantically versioned](https://semver.org/) tags
   like `v1`, `v1.1.5`, etc. instead of
   branches ([docs](https://docs.github.com/en/actions/creating-actions/about-actions#using-tags-for-release-management)).
2. Avoid a security vulnerability attack vector by encouraging community contributions to source code only, ignoring
   proposed compiled release assets.
3. Let automation do the hard part 🤖.

A sample [Publish workflow](.github/workflows/publish.yml) is provided which runs on a `release` event to compile and
package source code into `dist`, and force push major and minor tag versions according to the semantic version of the
release. You can kick off this workflow and publish to GitHub Marketplace simply
by [using the GitHub UI](https://docs.github.com/en/actions/creating-actions/publishing-actions-in-github-marketplace#publishing-an-action)
to create a new semantically versioned release like `v1.0.3`.

#### 🔁 Commit to open source maintainership

A healthy open source community starts with communication. Either in this repository or in your organization's `.github`
repository, we recommend reviewing, editing, and adopting:

- `CODE_OF_CONDUCT.md` for how to engage in community
- `CONTRIBUTING.md` for how to contribute to this project
- `LICENSE.md` for how to legally use and contribute to the project
- `SECURITY.md` for responsibly disclosing vulnerabilities
- [Issue and pull request templates](https://docs.github.com/en/github/building-a-strong-community/about-issue-and-pull-request-templates)

Issues and pull requests from the open source community should be attended to in a prompt, friendly, and proactive
manner. Two sample workflows, [stale](.github/workflows/stale.yml) and [labeler](.github/workflows/labeler.yml) are
provided to help with two small repetitious tasks.

See [Open Source Guides](https://opensource.guide/best-practices/) for more guidance on maintaining a strong community.

## License

[MIT](LICENSE.md)

## Contributing

Pull requests are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for more.