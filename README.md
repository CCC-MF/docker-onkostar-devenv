# Docker based environemt for Onkostar plugin development

## Issues with Apache Tomcat >= 9.0.74

Since Onkostar has some issues using Apache Tomcat >= 9.0.74, the environment makes
use of Apache Tomcat 9.0.73 intentionally.

## Where to place files?

Place a copy of Onkostar WAR file and a valid license file into directory
`onkostar.d`.

There should be only one WAR and license file within `onkostar.d`.
The license file should have the ending `.xml.sign`.

Place an initial database dump file into directory `initdb.d`.
The database will pick up those files in alphabetical order and import SQL files
on first start.

To add any plugins or to test a plugins JAR file, flace them into directoy
`plugins.d`.

## How to start Onkostar?

### Database init

If the database is not initialized yet, run

```
docker-compose up mariadb
```

This will initialize the database and import SQL files from `initdb.d`.
If you see the logs stopping after SQL file import with a line presenting:
```
mariadb: ready for connections
```
you can press <CTRL>+C to stop the initialized database.

### Start complete environment

Now you are able to start the environment using

```
docker-compose up
```

This will show the complete onkostar logging until you stop the environment.

## How to stop or restart the environment?

To stop the environment, simply press <CTRL>+C.

You are able to restart the environment by running the `up` command again

```
docker-compose up
```
