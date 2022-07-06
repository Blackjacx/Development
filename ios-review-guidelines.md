# Review Guidelines

1. All targets must be able to build an IPA. To check this go to [Bitrise](https://app.bitrise.io/) and select the scheduled build `MATRIX (Beta)`, adjust your branch name and trigger this build. It will build your the specified target from your branch, run the tests and cuploads an IPA. 
1. The [coding guidelines](./ios-coding-guidelines.md) must match.
1. Code duplicates are not allowed.
1. If you found a typo, copy the sentence, paste it in the Github comment and mark the typo using **bold** font. This makes it easier for the reviewer to find them if is e.g. a single word. Additionally remember the PR author to enable spell checking in Xcode which helps to avoid typos in PR reviews.
1. As a PR creator pleae never close the conversations. This should be done by the one who created the feedback/conversation. It is similar to merging PRs which also has to be decided/done by the reviewer and not the PR creator.
1. Try to find the following during review:
    - Code that's hard to understand
    - Code that's complicated (or not needed)
    - Code that's duplicated many times
    - Code that depends too much on other code
    - Code that can't be replaced easily
