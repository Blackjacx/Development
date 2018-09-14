# Review Guidelines
1. All targets must be able to build an IPA. To check this go to your app on your CI (e.g. [Bitrise](https://app.bitrise.io/)) click the big green button on the upper right called `Start/Schedule Build`, enter your branch name, select `MATRIXTestDeploy` from the workflow list and start it. It will build all app targets, runs the tests and builds the app. If all that works the chances are very high that your PR is able to be build by the CI without errors.
1. The [coding guidelines](./ios-coding-guidelines.md) must match.
1. Code duplicates are not allowed.
