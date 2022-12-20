# About Project - Tutorial GraphQL
The free and open-source tutorial to learn all around GraphQL to go from zero to production.
https://www.howtographql.com/graphql-ruby/0-introduction/



## Set up

1. Clone the project
```
git clone git@github.com:derikbf/rails-graphql.git
```
```
cd rails-graphql
```
2 - exec create and migrate
``` 
bundle exec rails db:create db:migrate
``` 
3. Install dependencies
``` 
bundle
``` 
4. Start the project
```
bundle exec rails server
```
http://localhost:3000/graphiql


## Query and Mutations
### create user
```
mutation {
  createUser(input: {
    name: "Test User",
    authProvider: {
      credentials: {
        email: "email@example.com",
        password: "123456"
      }
    }
  }
  ) {
    id
    name
    email
  }
}
```

### Get token
```
mutation {
  signinUser(input: {
    credentials: {
      email: "email@example.com",
      password: "123456"
    }
  }) {
    token
    user {
      id
    }
  }
}
```

### create link
```
mutation {
  createLink(input: {
    description: "http://npmjs.com/package/graphql-tools",
    url: "Best tools!"
  }) {
    id
    url
    description
    postedBy {
      id
      name
    }
  }
}
```

### createVote
```
mutation {
  createVote(input: {linkId: "1"}) {
    link {
      description
    }
    user {
      name
    }
  }
}
```

### Query
```
query allLinks
{
  allLinks {
    id
    postedBy {
      name
      votes {
        link {
          description
        }
      }
    }
  }
} 
```
