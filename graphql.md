# GitHub 

## GraphQL

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
