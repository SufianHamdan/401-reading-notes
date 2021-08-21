# Read: 36 - Cognito

## Amplify and Cognito

**AUTHENTICATION**
  * Amplify Auth category provides an interface for authenticating a user. Behind the scenes, it provides the necessary authorization to the other Amplify categories. 
  * Comes with default, built-in support for Amazon Cognito User Pool and Identity Pool. 
  * The Amplify CLI helps you to create and configure the auth category with an authentication provider.
  * Setup
    - Prerequisites - Android application targeting at least Android SDK API level 16 with Amplify libraries integrated
    - Configure Auth Category with the command: amplify add auth
    - Enter the following when prompted:
      ? Do you want to use the default authentication and security configuration?
        `Default configuration`
      ? How do you want users to be able to sign in?
        `Username`
      ? Do you want to configure advanced settings?
        `No, I am done.`
    - To push your changes to the cloud, execute the command: amplify push
    - Install Amplify Libraries:
      dependencies {
        implementation 'com.amplifyframework:aws-auth-cognito:1.17.1'
      }
    - Initialize Amplify Auth - Add the Auth plugin before calling Amplify.configure. Update the code you added in Prerequisites:
      // Add this line, to include the Auth plugin.
      Amplify.addPlugin(new AWSCognitoAuthPlugin());
      Amplify.configure(getApplicationContext());
    - Check the current auth session:
      Amplify.Auth.fetchAuthSession(
      result -> Log.i("AmplifyQuickstart", result.toString()),
      error -> Log.e("AmplifyQuickstart", error.toString())
      );
