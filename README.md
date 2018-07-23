# typescript-node-module

Very opinionated TypeScript node module template, with batteries included.

Loosley based other boilerplates I looked at for _inspiration_, namely https://github.com/Microsoft/TypeScript-Node-Starter and https://github.com/jsynowiec/node-typescript-boilerplate.

# Install

Just clone/fork and start coding. Make any changes you need. Feel free to suggest any ideas or improvements, but keep in mind this is _very opinionated_, so while I will for sure appreciate the discussion, it's very likely I will not take many PRs.

## Manual process

```sh
mkdir cool-module
cd cool-module
git init
git remote add upstream git@github.com:mvaldesdeleon/typescript-node-module.git
git pull upstream master
git remote add origin git@github.com:youareawesome/cool-module
git push -u origin master
```

# Philosophy

When working in large teams/enterprises, consistency is key. And in our everyday chores as a developer, there are many places to be inconsistent.

The goal of this project is to remove some of those oportunities completely.

By using this template, you surrender your control over the following:

-   Code style
-   Commit messages
-   Branching convention
-   Tagging convention
-   Changelog generation
-   Release convention
-   Code quality

All checks are local, so you can circumvent them if you want to. But if that's the case, then you should not be using this template.

## Code style

[prettier](https://github.com/prettier/prettier), [lint-staged](https://github.com/okonet/lint-staged), [husky](https://github.com/typicode/husky)

All _\*.ts_, _\*.js_, _\*.json_, and _\*.md_ files are ran through `prettier --write` via a _pre-commit_ githook. This keeps you from commiting wrongly-formatted code.

Additionally, `prettier` can be invoked via the `format` and `format-check` npm scripts. The first script will format the entire codebase, while the second will just output the list of files that require formatting.

## Commit messages

[commitlint](https://github.com/marionebl/commitlint), [commitizen](https://github.com/commitizen/cz-cli), [husky](https://github.com/typicode/husky)

[Conventional Commits](https://conventionalcommits.org/) are enforced by `commitlint` via a _commit-msg_ githook.

To aid in producing valid commits, `commitizen` is installed and can be invoked via the `commit` npm script. For those who insist on using `git commit`, a `.gitmessage` file is provided. Said file will be used automatically, as the local git `commit.template` setting is set by the `postinstall` npm script, after running `npm install`.

## Branching and tagging convention

[pre-push-valid](https://github.com/mvaldesdeleon/pre-push-valid), [husky](https://github.com/typicode/husky)

Refs pushed to remotes will be validated to ensure they conform to [gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

Only the following branches can be pushed to a remote:

-   `master`
-   `develop`
-   `release/*`
-   `feature/*`
-   `hotfix/*`

Additionally, only tags conforming to [semver](https://semver.org/), **without** the `v` prefix!

## Changelog generation

[standard-version](https://github.com/conventional-changelog/standard-version)

Based on the conventional commits, a [conventional changelog](https://github.com/conventional-changelog/conventional-changelog) will be automatically generated for each release.

## Release convention

[git-branch-is](https://github.com/kevinoid/git-branch-is), [standard-version](https://github.com/conventional-changelog/standard-version)

When it's time to ship, use the `release` npm script to produce a new release.

Releases can only be triggered from the `master` branch, and the working directory must be clean before a new release can be produced.

The `release` script will:

-   Decide the new semantic version, based on the conventional commits since the last release
-   Update the `package.json` file to reflect this new version
-   Update the `CHANGELOG.md` file to include the changes since the last release
-   Lint and commit these changes
-   Tag the release commit with the new version
-   Push the changes along with the tag to the tracking remote

Depending on your workflow, you might also want to add a `npm publish` call at the end of the `posttag` script for `standard-version`.

## Code quality

[tslint](https://github.com/palantir/tslint), [husky](https://github.com/typicode/husky)

Attempting to push code with linting errors will fail.

# Usage

Check the `scripts` section of the `package.json` for more. Eventually I will document this, but there are no surprises there, all your basic scripts are provided.

# Observations

As per their install instructions, `prettier` and `cz-conventional-changelog` are pinned down to their exact versions at the `package.json` file.

# License

MIT
