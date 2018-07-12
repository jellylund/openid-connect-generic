## OpenID Connect Generic Client

License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

A simple client that provides SSO or opt-in authentication against a generic OAuth2 Server implementation.

### Description

This plugin allows to authenticate users against OpenID Connect OAuth2 API with Authorization Code Flow.
Once installed, it can be configured to automatically authenticate users (SSO), or provide a "Login with OpenID Connect"
button on the login form. After consent has been obtained, an existing user is automatically logged into WordPress, while 
new users are created in WordPress database.

Support is also integrated for the [Groups plugin](https://wordpress.org/plugins/groups/) when using AWS Cognito as IDP.

Much of the documentation can be found on the Settings > OpenID Connect Generic dashboard page.

### Installation

1. Upload to the `/wp-content/plugins/` directory
2. Activate the plugin
3. Visit Settings > OpenID Connect and configure to meet your needs

#### Composer

The original version of OpenID Connect Generic is on [packagist](https://packagist.org/packages/daggerhart/openid-connect-generic)
This fork lives at [github.com/ianknox-jv/openid-connect-generic](https://github.com/ianknox-jv/openid-connect-generic) and won't be added to packagist.

Installation:

`$ composer config repositories.openid-connect-generic vcs https://github.com/ianknox-jv/openid-connect-generic`
`$ composer require daggerhart/openid-connect-generic:dev-<name_of_branch_in_fork>`

### Frequently Asked Questions

**What is the client's Redirect URI?**

Most OAuth2 servers should require a whitelist of redirect URIs for security purposes. The Redirect URI provided
by this client is like so:  `https://example.com/wp-admin/admin-ajax.php?action=openid-connect-authorize`

Replace `example.com` with your domain name and path to WordPress.

### AWS Cognito Settings

Cognito doesn't adhere to the ODIC spec very closely when it comes to endpoints. To make matters worse their documentation isn't too clear either.
* Login: https://<name>.auth.<region>.amazoncognito.com/login
* Userinfo: https://<name>.auth.<region>.amazoncognito.com/oauth2/userInfo
* Token Validation: https://<name>.auth.<region>.us-west-2.amazoncognito.com/oauth2/token
* End Session: https://<name>.auth.<region>.us-west-2.amazoncognito.com/logout

### To Do

* Groups plugin integration in non-cognito setups
* IDP groups -> WP Roles integration