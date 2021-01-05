# Custom Keycloak container

## Why we need a custom keycloak
On computers with slower HDDs, Keyclok fails to initiate the database because 
the transactions are rolled back before they are completed (due to timeout).
This container has a script to modify these timeouts in order to run keycloak successfully.
The concerned timeouts are in the `jboss-config.batch` file.


## Why not modify the timeouts in JAVA_OPTS_APPEND or JAVA_OPTS
As far as we know, certain timeouts are a property of subsystems of `jboss` and not of JVM.
So, they could not be modified through `JAVA_OPTS_APPEND` environment variables.
However, they can be modified through modifying the XML config or by running commands through
jboss CLI before running keycloak. We adopted the second approach.


