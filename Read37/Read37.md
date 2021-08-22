# Read: 37 - S3

## Introduction to Amazon S3
**What is Amazon S3?**
  * Amazon Simple Storage Service (Amazon S3) - is storage for the Internet.
  * Amazon S3 has a simple web services interface that you can use to store and retrieve any amount of data, at any time, from anywhere on the web.
  * Gives any developer access to the same highly scalable, reliable, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of web sites. 
  * Advantages of using Amazon S3
    - Creaing buckets
    - Storing data
    - Downloading data
    - Permissions
    - Standard interfaces
  * Amazon S3 concepts
    - Bucket - a container for objects stored in Amazon S3. Every object is contained in a bucket. They organize the Amazon S3 namespace at the highest level, identify the account responsible for storage and data transfer charges, play a role in access control, and serve as the unit of aggregation for usage reporting. 
    - Objects - the fundamental entities stored in Amazon S3. Objects consist of object data and metadata, and uniquely identified within a bucket by a key (name) and a version ID. 
    - Keys - unique identifier for an object within a bucket. Every object in a bucket has exactly one key. 
    - Regions - can choose the geographical AWS Region where Amazon S3 will store the buckets that you create. You might choose a Region to optimize latency, minimize costs, or address regulatory requirements. Objects stored in a Region never leave the Region unless you explicitly transfer them to another Region. 
  * Amazon S3 data consistency model 
    - Amazon S3 provides strong read-after-write consistency for PUTs and DELETEs of objects in your Amazon S3 bucket in all AWS Regions. 
    - Updates to a single key are atomic. 
    - Amazon S3 achieves high availability by replicating data across multiple servers within AWS data centers.
    - Bucket configurations have an eventual consistency model. 
  * Concurrent applications - when multiple clients are writing to the same items.
  * Amazon S3 features
    - Storage classes - Amazon S3 offers a range of storage classes designed for different use cases.
    - Bucket policies - provide centralized access control to buckets and objects based on a variety of conditions, including Amazon S3 operations, requesters, resources, and aspects of the request. Are expressed in the access policy language and enable centralized management of permissions. The permissions attached to a bucket apply to all of the bucket's objects that are owned by the bucket owner account.
  * AWS identity and access management
    - Can use AWS Identity and Access Management (IAM) to manage access to your Amazon S3 resources.
    - Access control lists - can control access to each of your buckets and objects using an access control list (ACL)
    - Versioning - to keep multiple versions of an object in the same bucket.
    - Operations - create a bucket, write an object, read an object, delete an object, and list keys.
  * Amazon S3 application programming interfaces (API)
    - The Amazon S3 architecture is designed to be programming language-neutral, using AWS supported interfaces to store and retrieve objects.
    - Amazon S3 provides a REST and a SOAP interface. 
    - REST API - is an HTTP interface to Amazon S3, and you use standard HTTP requests to create, fetch, and delete buckets and objects.
    - SOAP API - provides a SOAP 1.1 interface using document literal encoding. 
  * Paying for Amazon S3 - Pricing for Amazon S3 is designed so that you don't have to plan for the storage requirements of your application. Amazon S3 charges you only for what you actually use, with no hidden fees and no overage charges. 

## S3 with Amplify
**Amplify Storage**
  * Amplify Storage category - provides an interface for managing user content for your app in public, protected, or private storage buckets. 
  * Setup
    - Provision backend storage - execute the command:
    amplify add storage, and then answer the questions
    - To push changes to the cloud use the command: amplify push
    - Install Amplify Libraries - add these
      dependencies {
         implementation 'com.amplifyframework:aws-storage-s3:1.17.1'
         implementation 'com.amplifyframework:aws-auth-cognito:1.17.1'
        }
    - Initialize Amplify Storage - initialize the Amplify Auth and Storage categories you call Amplify.addPlugin() method for each category. To complete initialization call Amplify.configure().
    Add the following code:
    Amplify.addPlugin(new AWSCognitoAuthPlugin());
    Amplify.addPlugin(new AWSS3StoragePlugin());
    - Uploading data to your bucket - specify the key and the data object to be uploaded.
    - Upon successfully executing this code, you should see a new folder in your bucket, called public. It should contain a file called ExampleKey, whose contents is Example file contents.