
# Accounts for Children (Google Summer of Code 2022)



## Introduction
This document proposes an implementation of improvements regarding privacy and personal data protection, with special emphasis on users under 13 years of age (U13 users). These functionalities are derived from the Children's Online Privacy Protection rule (COPPA),  California Consumer Privacy Act (CCPA) and GDPR, and they are inspired by the implementations done by other organizations such as Khan Academy.
## Documentation

[Full Proposal](https://docs.google.com/document/d/1m46X9jlLD_kbu_CVVIDwAdUYWPsNTtFNlWUPQpdfDQ8/edit?usp=sharing)


## Design Overview

U13 will always be private and therefore they will not show up in rankings and their details will not be visible to any other user besides their parent and site admins.

## Database:
The database will need to be modified to store a link from U13 accounts to parental figure accounts, and to also store whether an account has been verified by the parent or not.
Existing U13 accounts will be given 7 days to register the email address of their parent and for their parent to verify their account.

## API

1. A list of APIs will be modified to disallow U13 from performing them. This includes all content creation APIs (create problem/contest/course/etc).
2. A list of APIs will be modified to show only manually curated content (problems, courses and contests) to U13 and anonymous users. The only exception will be when a U13 was manually added as a participant of a private course/contest.
3. Three new APIs will be created:
      - An API for parents to verify their children's account.
      - An API for users to request the deletion of their account. This will be performed by deleting all personal information from their account in the database and redacting their username.
      - An API for users to request the deletion of their account. This will be performed by deleting all personal information from their account in the database and redacting their username.
## Frontend

- Add a date of birth field in sign up form.
- Forward existing users who didn't record a birthdate to the edit profile page the next time they sign in.
- Add a field in the profile page where users can register their parent's account.
- Add a banner reminding U13 users they have X days left for their parents to verify their account.
- Add a button where users can delete their child's account or their own account.
- Add a new page where parents can view a report of their child's activity.
## Authors

- [@Anmol](https://github.com/anmode)


## Here are the link to all PRs Commited to repo.

1. API parental token [https://github.com/omegaup/omegaup/pull/6743]
2. Cookie Consent Modal [https://github.com/omegaup/omegaup/pull/6634]
3. API Changes U13 Can't perfom [https://github.com/omegaup/omegaup/pull/6718]
6. API user can delete their account [https://github.com/omegaup/omegaup/pull/6646]
7. Created a birthdate picker and designed the sign up form [https://github.com/omegaup/omegaup/pull/6695]
8. Create an entrypoint to verify the parent token. [https://github.com/omegaup/omegaup/pull/6773]
4. Arenav2 pagination [https://github.com/omegaup/omegaup/pull/6546]
5. Added New Fields to Users Table. [https://github.com/omegaup/omegaup/pull/6670]


#### I have mentioned only the PRs with long commits.

## API Reference

#### Get all items

```http
  GET /api/user/deleteConfirm/
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `token` | `string` | |

#### Get item

```http
  /api/user/deleteRequest/
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `username`      | `null\|string` |  |

#### returns

| Parameter | Type     |                        |
| :-------- | :------- | :--------------------- |
| `token`      | `string` |  |


