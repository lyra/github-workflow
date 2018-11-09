# github-workflow
GitHub workflow proposal for members of the organization, and others.
---
This document aims at providing guidelines for integration of code written either by **PayZen** organization's members, or individuals and companies willing to contribute.

## General principles

All repositories will feature :
* one **master** branch : Identical to what is on production. Used for hotfixes.
* a **release** branche : The Release Candidate (RC) branch, available on the staging environment.
* **tags** : The production environment is built from the tags. eg : v1.0.2 with possibly a message or relative changelog file

For repositories containing plug-ins for other software (Magento, Prestashop...), one repository per **major version** will be used, provided that it breaks the API or architecture of the plug-in, making diffs on the **master** branch irrelevant.

*TODO*: Give examples of software versions from one vendor that had a huge impact on the plug-in architecture.

### Naming convention

* use lower case
* use dashes
* be specific. you may find you have to differentiate between similar ideas later - ie use purchase-rest-service instead of service or rest-service.
* be consistent. consider usage from the various GIT vendors - how do you want your repositories to be sorted/grouped?

* **module repositories** : plugin-[CMS-NAME]
* **product :** productname-sdk


## Life Cycle

### Starting a new project

Management of repositories will be performed by organization's members.

Each developer will have to **fork** organization's repositories. It can be done straight from GitHub's repository page.

Then, the developer has to configure an **upstream** repository, pointing to the organization's repository it has been forked from.

```
git clone git@github.com:username/some-project.git
git remote add upstream https://github.com/payzen/some-project.git
```

It is recommended that you set up a local policy for development in the likes of "one branch per feature", but it's up to you to decide.

Anyway, all your changes should be merged into your fork's **master** branch.

### Keeping your fork up-to-date

```
git fetch upstream
git checkout master
git merge upstream/master
```

### Pushing changes to your fork

```
git push -u origin master
```

### Submitting a Pull Request

Go to the organization's repository page, and click on **New pull request**.

Click on **compare across forks**.

Select your fork as the **head fork**. Review the changes, then confirm.

## For organization's members

Test a submitted pull request by cloning the **developer's fork** from which the Pull Request comes.

If everything's OK, merge the Pull Request (it can be done straight from GitHub).
