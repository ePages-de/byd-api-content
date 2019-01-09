# byd-api-content

This repository manages the editorial content of the Beyond API documentation referenced by Stoplight.
The review process happens by means of pull requests, as usual.
The content is then put into Stoplight.
Once everything is set up, the texts will automatically be referenced by the respective Stoplight text blocks.

Currently, the *markdown_stoplight* subdirectory in this repository holds the following files:

| File name | Content
|---|---
| intro.md | The landing page introductory text.
| use-cases.md | Contains all use cases. The ability to jump to each one is added in Stoplight by means of anchor links.
| changelog.md | The changelog entries which are displayed above the reference.
| http_verbs.md | Introductory material about how to send REST calls.
| headers.md | An introduction to the structure of an HTTP header.
| versioning.md | Short outlook on what to do when versioning becomes relevant.
| pagination.md | Information about paged responses.
| hypermedia.md | Introduction to how we implement the HAL format.
| status_codes_and_errors.md | Status codes and errors to be expected from the Beyond API.
| authentication.md | Details depiction of the authorization process.
| scopes.md | List of all the scopes in our system.
| signers.md | A short introduction to signers.
| custom-apps.md | A short introduction to the steps to take to create a custom app.


