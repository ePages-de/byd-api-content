#### Versioning

For now, there is only a single version for our API, but we've prepared
for the time when the versions evolve. So, what to do then? It's as
simple as that: always specify the version you want to use with an
`Accept-Version` request header.

We try to avoid major version revisions, but backwards compatible
changes without revising the version can happen for these types of
modifications:

-   New resources

-   New optional request parameters and/or headers

-   New optional properties

-   Changes in the order of properties

-   New values for enumerated fields

-   New HTTP status codes

-   Changes to our ID format

