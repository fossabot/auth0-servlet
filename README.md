
# Auth0 Servlet

This project is no longer a library but a **Java Servlet** sample using the [java-mvc-commons](https://github.com/auth0/auth0-java-mvc-common) library.

If you're looking for the latest version of the library it's still available:

Maven:

```xml
<dependency>
  <groupId>com.auth0</groupId>
  <artifactId>auth0-servlet</artifactId>
  <version>3.4.0</version>
</dependency>
```

or Gradle:

```groovy
compile 'com.auth0:auth0-servlet:3.4.0'
```


## Getting started

Download or clone this repository and follow the instructions below to setup the sample.

### Auth0 Dashboard
1. On the [Auth0 Dashboard](https://manage.auth0.com/#/clients) create a new Client of type `Regular Web Application`. 
1. Add the URL that will be called on an OAuth successful login to the Allowed Callback URLs. i.e.: `https://mysite.com/callback`.
1. Add the URL that will be called on logout to the Allowed Logout URLs. i.e.: `https://mysite.com/logout`.
1. Copy the `Domain`, `Client ID` and `Client Secret` values at the top of the page and use them to configure the Java Application.


### Java Application
Set the client values in the `src/main/webapp/WEB-INF/web.xml` file. They are read by the `AuthenticationControllerProvider` class.

```xml
<context-param>
    <param-name>com.auth0.domain</param-name>
    <param-value>{YOUR_AUTH0_DOMAIN}</param-value>
</context-param>

<context-param>
    <param-name>com.auth0.clientId</param-name>
    <param-value>{YOUR_AUTH0_CLIENT_ID}</param-value>
</context-param>

<context-param>
    <param-name>com.auth0.clientSecret</param-name>
    <param-value>{YOUR_AUTH0_CLIENT_SECRET}</param-value>
</context-param>
```

By default a Code Grant flow with Response Type `code` will be executed. Change the requested Response Type in the `AuthenticationControllerProvider` class to `token` or `id_token` to use Implicit Grant. i.e.:

```java
AuthenticationController.newBuilder(domain, clientId, clientSecret)
    .withResponseType("token")
    .build();
```

Keep in mind that the server uses `POST` to return a Implicit Grant result, you should handle that on your controller too.
 


### Running the sample

Open a terminal, go to the project root directory and run the following command:

```bash
./gradlew clean appRun
```

The server will be accessible on https://localhost:8080/portal/home. After logging in you should see your `user id` in the header.


## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, amont others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free account in Auth0

1. Go to [Auth0](https://auth0.com) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](https://auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE.txt) file for more info.

