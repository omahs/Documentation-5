---
description: How to contribute to the Kwenta documentation
---

# Contributing

You want to contribute to the documentation but you don't know where to start? You are at the right spot! This page should give you all the necessary information to contribute efficiently to our documentation.

First off, regardless of the time you have or your experience you can provide meaningful contribution to the documentation. Here are some examples depending on the time you have:

* ⏲️: Add a resource, correct a typo, [deduplicate information](contributing.md#favor-links-to-repetition)
* ⏲️⏲️: Rewrite a paragraph, add information to an existing page, create an issue for an improvement, propose a content template
* ⏲️⏲️⏲️: Propose new content, write an activity report, take an issue

If you really have not much time but you have found a broken link, an error in the documentation or have a minor suggestion, we'd still like to hear from you. Drop us a message on our [Discord](https://discord.gg/kwenta) or create a new [issue](https://github.com/Kwenta/Documentation/issues).

{% embed url="https://github.com/Kwenta/Documentation" %}

## Structure

The documentation is structured around top-level directories that map the different [content types](contributing.md#content-types) of the documentation and create a hierarchical structure between contents. These top-level directories appear as the sections of the documentation.

{% hint style="warning" %}
Subdirectories to top-level directories will be seen as a content with different levels of nesting and not as subsections.
{% endhint %}

If you want to have multiple levels of nesting for your content (hence having multiple files), you can create subdirectories in a top-level directory with a `README.md` file at the root of this subdirectory. The README file will be the top-level content of the subdirectory.

For example, if you want to have a meeting reports page with separate pages for each report you could create the following tree structure :

```
├── dao // top-level section
│   └── meetings
│       ├── first-meeting.md
│       └── README.md
```

In this case, the `README.md` would contain a list of the different meetings and at least a [description of the page](contributing.md#content-templates).

There are no hard limits on the nesting of pages but you should avoid having more than 3 levels.

### Summary

The `SUMMARY.md` file at the root of the page is - as its name suggests - the summary.

{% hint style="warning" %}
If you are modifying content directly by making commits on the github repository, make sure to edit the SUMMARY.md file in order to reflect your changes.
{% endhint %}

### Naming

When creating a new file or directory please follow these rules:

* Use only lowercase letters
* Do not use special characters and spaces
* Use hyphens as a word separation
* Use a filename as close as possible as the title of the page but if it is too long shorten it

### Content types

As the Kwenta documentation aims to be comprehensive it is important to organize the content well so it is easy to find the right information and easy to add information. The more the documentation grows the more this becomes important.

The documentation is organized around topics that enforces the structure of the documentation.

Currently we have the following categories :

* **Onboard**: Introduction to Kwenta and tutorials for first-time users
* **DAO**: A comprehensive documentation of the Kwenta DAO governance, roles and sub-DAOs. Everything community related goes here
* **Tokenomics**: Information with regard to the KWENTA tokenomics,  sovereignty phase and staking
* **Futures**: Tutorials and extensive instructions for the Future platform
* **Shorting**:  Tutorials and information regarding the Kwenta Shorting mechanism
* **Exchange**: Tutorials and information regarding the Kwenta Exchange

You want to provide content and no category fits? Feel free to propose a new content type by creating an issue on the GitHub repository.

## Style guide

In order to have a consistent documentation we'd like you to follow the recommendations/conventions that are underlined below.

#### Markdown

All the documentation is written in [Markdown](http://commonmark.org/help/). You can edit the documentation via any text editor or directly on github.

Regardless on how you plan to edit the documentation you should also check Gitbook's [markdown documentation](https://docs.gitbook.com/editing-content/markdown) as there are some specific syntax that could be useful (e.g. hint boxes).

Embedded HTML is supported but should be avoided. If there are cases where you think it should be used, make an improvement proposal.

#### Media

Adding an image can be done using the proper Markdown syntax, either using an external link or a direct reference to the path of the image. Videos files can also be added to pages as Gitbook supports [embedded content](https://docs.gitbook.com/editing-content/embeds). Do not upload videos to the repository.

When adding image to the documentation :

1. Files must not exceed 150 KB.
2. All files must be stored under `.gitbook/assets` at the root of the documentation
3. Files reused across multiples sections must be in the `common` subdirectory
4. Files specifically used in one section must be in the subdirectory with the same name as the section
5. Following [naming](contributing.md#naming) conventions use clear names describing the content of the media

As the assets directory is at the root of the documentation, to add a link to the image the path must be relative: if you add a page in the section `dao` the image link will be`![]`(`../.gitbook/assets/filename.jpeg)`

#### Content templates

Content templates are markdown files that provides the basic structure for the different content types of the documentation. Creating a new page from a template will allow you to easily ensure that you are using the right structure for your page.

All templates are located in the `templates` hidden folder.

We currently provide the following templates:

* **Basic Template** \[`basic-page.md`]: as the name suggests, it contains the very minimal elements that are required for a page.

If there are no templates for a specific content type, you can propose one by following our [improvement processes](contributing.md#process). As there are some minimal requirements for a page, make sure to use our basic template as a start.

### Writing style

Even if this documentation is not a technical software documentation trying to write in a technical style that is concise, clear and objective should be what we aim for. Here are some general recommendations that you should follow when writing:

* Be as clear as possible to avoid ambiguity
* Use the same word and terminology for the same concept throughout the documentation. This can seems obvious but sometimes using what appears to be synonyms can cause ambiguity.
* When using acronyms provide at least a link to a glossary or if it is the first time it appears on the page, spell it out.
* A good example can help understanding a complex subject, so do not hesitate to provide some. They can take many form: schema, sample code or even a small exercise.

As this documentation targets multiple levels of knowledge you should always have this target in the back of your mind when you write.

For example, if you write for a beginner, do not hesitate to provide comprehensive explanations even for concepts that seem obvious. Some of the readers may be well versed in computer science but may not be so knowledgeable on the DeFi and Ethereum ecosystem, so keep it in mind.

## Process

Ready to propose an improvement? Depending on the type of improvement you want to make, you should follow these processes. Improvements should be proposed via the [github repository](https://github.com/Kwenta/Documentation/).

We can define two category of improvements:

* **Small**: These changes do not necessarily require a discussion and the process is straightforward. (e.g. typo correction, paragraph improvement, adding a resource, etc.)
* **Big**: These changes can have an important impact on the documentation and should therefore be discussed before having to work on it. (e.g. documentation structure change, adding a new section, changing the structure of a page, propose a new process, etc.)

If in doubt, jump on our [Discord](https://www.discord.gg/Kwenta) and the community will be happy to help!

### Github

Using this method is the most straightforward way of proposing a modification for the documentation as it does not require the creation of an account by the documentation admins. Anyone with a github account can propose a pull request or create an issue.

#### Small improvement

1. **Fork** the documentation repository
2. Create a new branch following the branch naming convention, e.g. `fix/typo`
3. Make the changes and commit them
4. Create a pull request on the documentation repository

Once a pull request is submitted, a community manager or core contributor will revise the pull request and merge it if appropriate.

#### Big improvement

1. Create an issue on the documentation repository
2. If you want to add a proposal to your issue you can follow steps 1-3 of the small improvement and add a link to your branch in the issue body
3. If the issue is accepted you can create a pull request from a new branch or from your previously created branch

Once the PR is created the code review will start and after it, the branch will be merged if it meets all the requirements.


## More Information
Further details are to be determined as we go. If you have ideas or suggestions, let us know!

{% hint style="info" %}
As always if you have any doubts or questions around the contribution to the documentation, do not hesitate to contact us on our discord channel `#community-dev`
{% endhint %}
