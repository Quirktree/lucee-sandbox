# Host Configuration

Modify the `/etc/hosts` file on the local system to resolve the sandbox.local domain name to 127.0.0.1.

# Environment

Create a .env file in the root of the directory to specify the given environment variables:

```
LUCEE_PASSWORD=password
MYSQL_ROOT_PASSWORD=password
MYSQL_HOST=appdb
MYSQL_DATABASE=test
AWS_PROFILE=default
AWS_REGION=us-west-2
```

# Application

Lucee will map the _sandbox.local_ hostname to `./sites/www/public`, meaning the `application.cfc` and `index.cfm` should be created at this location. 