# GitHub 

- [REST API](https://docs.github.com/en/rest/repos/repos#list-public-repositories)
- [GraphQL API](https://docs.github.com/en/graphql/overview/explorer)

## REST API

1. [Create PAT token link](https://github.com/settings/personal-access-tokens/new)
1. Export token to environment variable

    ```bash
     export GH_PAT_TOKEN="github_pat_****"
    ```

1. User

    ```bash
    curl --request GET \
        --header "Accept: application/vnd.github+json" \
        --header "Authorization: Bearer $GH_PAT_TOKEN" \
        --url "https://api.github.com/user"
    ```

1. User's Public Repositories

    ```bash
    curl --request GET \
        --header "Accept: application/vnd.github+json" \
        --header "Authorization: Bearer $GH_PAT_TOKEN" \
        --url "https://api.github.com/user/repos?type=owner&sort=created&direction=desc"
    curl --request GET \
        --header "Accept: application/vnd.github+json" \
        --header "Authorization: Bearer $GH_PAT_TOKEN" \
        --url "https://api.github.com/users/ldynia/repos?type=owner&sort=created&direction=desc"
    ```

## GraphQL API

1. User

    ```graphql
    query {
      viewer {
        id
        login
        url
      }
    }
    ```

1. User's Public Repositories
    
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