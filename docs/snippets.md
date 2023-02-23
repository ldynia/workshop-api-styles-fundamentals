# Codespaces

```bash
source /usr/share/bash-completion/completions/git
```

# REST API

1. Visit [GitHub's REST API](https://docs.github.com/en/rest/repos/repos#list-public-repositories)
1. Create `7 days` expiration PAT token called `delete_me` in [Settings > Developer settings > Personal access tokens > Fine-grained tokens](https://github.com/settings/personal-access-tokens/new)

1. Export token to environment variable

    ```bash
    export GH_PAT="github_pat_****"
    ```

1. Get user data

    ```bash
    curl --request GET \
      --header "Accept: application/vnd.github+json" \
      --header "Authorization: Bearer $GH_PAT" \
      --url "https://api.github.com/user" \
      | jq '{id, login, url}'
    ```

1. Get user's public repositories

    ```bash
    # First method
    curl --request GET \
      --header "Accept: application/vnd.github+json" \
      --header "Authorization: Bearer $GH_PAT" \
      --url "https://api.github.com/user/repos?type=owner&sort=created&direction=desc" \
      | jq '.[] | {name, full_name}'

    # Second method
    curl --request GET \
      --header "Accept: application/vnd.github+json" \
      --header "Authorization: Bearer $GH_PAT" \
      --url "https://api.github.com/users/ldynia/repos?type=owner&sort=created&direction=desc" \
      | jq '.[] | {name, full_name}'
    ```

# GraphQL API

1. Visit [GitHub's GraphQL API - GraphiQL](https://docs.github.com/en/graphql/overview/explorer)

1. Get user data

    ```graphql
    query {
      viewer {
        databaseId
        login
        url
      }
    }
    ```

1. Get user's public repositories

    ```graphql
    query {
      viewer {
        login
        url
        repositories(
          first:100,
          isFork: false,
          ownerAffiliations: OWNER
          privacy: PUBLIC
          orderBy: {field: UPDATED_AT, direction: DESC}
        ) {
          edges {
            node {
              name
              url
              updatedAt
            }
          }
        }
      }
    }
    ```
1. Get user's repositories with fragments

    ```graphql
    fragment Repos on RepositoryConnection {
        nodes {
            name
            url
        }
    }

    query ownedRepos {
        viewer {
            archived: repositories(
                first: 100
                ownerAffiliations: OWNER
                privacy: PUBLIC
                isLocked: true
                orderBy: { field: UPDATED_AT, direction: DESC }
            ) {
                ...Repos
            }

        forked: repositories(
                first: 100
                ownerAffiliations: OWNER
                privacy: PUBLIC
                isFork: true
                isLocked: false
                orderBy: { field: UPDATED_AT, direction: DESC }
            ) {
                ...Repos
            }

        original: repositories(
                first: 100
                ownerAffiliations: OWNER
                privacy: PUBLIC
                isFork: false
                isLocked: false
                orderBy: { field: UPDATED_AT, direction: DESC }
            ) {
                ...Repos
            }
        }
    }
    ```

    # Clean Up

    1. Delete `delete_me` PAT token in [Settings > Developer settings > Personal access tokens > Fine-grained tokens](https://github.com/settings/tokens?type=beta)