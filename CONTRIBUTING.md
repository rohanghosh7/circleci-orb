## Development

There are scripts for creating namespace, orbs, etc in the `package.json`. They all start with an `orb:` prefix, use `npm run` to view them. Usually you need to only run `npm run orb:publish` to publish a new version of the orb.

## Examples

The more examples, the better. All examples in `docs/examples.md` are generated automatically from `src/orb.yml` source code via `npm run docs`. To make sure the examples referenced from the [README.md](README.md) list are correct, the list of links is checked in [scripts/examples.ts](scripts/examples.ts) file.

## Publishing

To see existing orbs:

```shell
$ circleci orb list cypress-io
```

### Commits

Use [simple semantic commit convention](https://github.com/bahmutov/simple-commit-message), just prefix your commits:

```text
major: breaking change
minor: new feature added
fix: a patch release
```

### Development

You can publish a [dev version](https://github.com/CircleCI-Public/config-preview-sdk/blob/master/docs/orbs-authoring.md) of the orb for testing before publishing a production immutable version. For example, to publish version `1.0.0-my-fork`, run:

```shell
node ./scripts/publish --dev 1.0.0-my-fork
```

You can first do a dry dev publish to see the command with:

```shell
node ./scripts/publish --dev 1.0.0-my-fork --dry
```

Note: you can publish a temporary version of the orb using the `dev` label. This is super useful for testing the orb in child projects before publishing an official immutable version. For example:

```
circleci orb publish src/orb.yml cypress-io/cypress@dev:1.1.0
```

It is a good idea to test a dev version of the orb first using [cypress-io/cypress-example-circleci-orb](https://github.com/cypress-io/cypress-example-circleci-orb) before publishing new public version.

### Production

You can publish a new orb version manually, by incrementing the version. For example:

```shell
$ circleci orb publish increment src/orb.yml cypress-io/cypress patch
Orb `cypress-io/cypress` has been incremented to `cypress-op/cypress@1.0.2`.
Please note that this is an open orb and is world-readable.
```

Or by specifying new version:

```shell
circleci orb publish src/orb.yml cypress-io/cypress@0.0.1
```

The better way is to let the [publish.js](publish.js) increment the version, tag the commit and publish the orb.

```shell
npm run orb:publish
```

After publishing, the `package.json` file will have new version (if any). A new git tag will be created and you should push the updated code and tag to GitHub

```shell
git push --tag
```

After pushing, go to [GitHub releases](https://github.com/cypress-io/circleci-orb/releases) and update notes for the new release.

## Additional information

- https://github.com/CircleCI-Public/circleci-orbs
- [Orb configuration](https://github.com/CircleCI-Public/config-preview-sdk/tree/master/docs)
- [Authoring orbs](https://github.com/CircleCI-Public/config-preview-sdk/blob/master/docs/orbs-authoring.md)
- [Testing orbs](https://github.com/CircleCI-Public/config-preview-sdk/blob/master/docs/orbs-testing.md)

## Examples of orbs

- https://github.com/CircleCI-Public/circleci-orbs/blob/master/src/rollbar/orb.yml
- https://github.com/CircleCI-Public/circleci-orbs/blob/master/src/codecov/orb.yml
- https://github.com/CircleCI-Public/circleci-orbs/blob/master/src/heroku/orb.yml

When Forrester released its 2016 report “Open Source Powers Enterprise Digital Transformation,” some people in the open source community were surprised by the results. They weren’t surprised that 41 percent of enterprise decision makers called open source a high priority and planned to increase use of open source in their organizations. They were concerned that the other 59 percent didn’t seem to understand the role open source would play in the future of the enterprise.

Paul Miller, one of the analysts behind the report, wrote, “The myth that open source software is exclusively written by and for lonely – rather odd – individual geeks remains remarkably prevalent. And yet it’s a myth that is almost entirely wrong. Again and again, we encounter executives who do not grasp how much their organization already depends on open source. More importantly, they do not see the key role that open source technologies and thinking will play in enabling their efforts to transform into a customer-obsessed business that really can win, serve, and retain customers.”

Fast-forward to today, and open source skills are among the most in-demand: 83 percent of hiring managers surveyed for the 2018 Open Source Jobs report said hiring open source talent was a priority this year, up from 76 percent last year. (More on that report in a minute.) Hiring managers are touting their organization’s contribution to open source projects as a recruiting strategy for nabbing top talent. Some of the biggest trends in enterprise IT, such as containers and hybrid cloud, rely on open source technologies including Linux and Kubernetes.

The mindset and narrative around open source have changed. Enterprise IT and business leaders should be able to keep up with IT organizations doing innovative work with open source technologies. We’ve rounded up some resources to help you get up to speed – and stay there.
