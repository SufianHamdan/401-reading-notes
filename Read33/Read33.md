# Read: 33 - GraphQL @connection

## review: Intro to Serverless
**What is Serverless Architecture? What are its Pros and Cons?**
  * Serverless - is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers. 
  * Serverless application - runs in stateless compute containers that are event-triggered, ephemeral, and fully managed by the cloud provider. 
  * Traditionally - applications have run on servers which you had to patch, update, and continuously look after late nights and early mornings due to all the unimaginable errors that broke your production. 
  * Serverless - no longer need to worry about the underlying servers, and can be worked on at anytime.

## review: AWS Amplify Kool-Aid
**AWS Amplify**
  * AWS Amplify - set of tools and services that can be used together or on their own, to help front-end web and mobile developers build scalable full stack applications, powered by AWS.
  * Benefits - configure backends fast, seamlessly connect frontends, deploy in a few clicks, and easily manage content.
  * Features and tools - develop, deliver, and manage
  * Develop - configure backend, connect your app, and integrate UI compenets.
  * Deliver - connect repository, configure buildsettings, and deploy your app.
  * Manage - invite team members, manage users, and manage content.
  * Use cases - onboarding flows, real-time collaboration, AI/ML, and targeted campaigns.

## GraphQL @connection section
**GraphQL Add relationships between types**
  * @connection directive - enables you to specify relationships between @model types. 
  * Implement many-to-many relationships using two one-to-many connections and a joining @model type. 
  * Definition : directive @connection(keyName: String, fields: [String!]) on FIELD_DEFINITION
  * Usage - Relationships between types are specified by annotating fields on an @model object type with the @connection directive.
  * fields argument can be provided and indicates which fields can be queried by to get connected objects. 
  * keyName argument can optionally be used to specify the name of secondary index that should be queried from the other type in the relationship. The fields argument should be provided to indicate which field(s) will be used to get connected objects, and if keyName is not provided, then @connection queries the target table’s primary index.
  * Can also define the field you would like to use for the connection by populating the first argument to the fields array and matching it to a field on the type.
  * Has One @connection can only reference the primary index of a model.
  * Has many - one-to-many connection needs an @key that allows comments to be queried by the postID and the connection uses this key to get all comments whose postID is the id of the post was called on. 
  * Belongs to - can make a connection bi-directional by adding a many-to-one connection to types that already have a one-to-many connection. 
  * Many-to-many connections - an implement many to many using two 1-M @connections, an @key, and a joining @model. A bidirectional many-to-many which is why two @key calls are needed on the PostEditor model. You can first create a Post and a User, and then add a connection between them with by creating a PostEditor object.
  * Alternative definition 
    - directive @connection(name: String, keyField: String, sortField: String, limit: Int) on FIELD_DEFINITION
    - Defining index structures using @key and connection resolvers using @connection. There is an older parameterization of @connection that creates indices and connection resolvers that is still functional for backwards compatibility reasons. It is recommended to use @key and the new @connection via the fields argument.
    * Limit - The default number of nested objects is 100, and you can override this behavior by setting the limit argument.