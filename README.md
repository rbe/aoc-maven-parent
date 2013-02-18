# art of coding Parent POM

## User Settings

Define a base directory in `$HOME/.m2/settings.xml`:

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
        <profiles>
            <profile>
                <id>aoc default</id>
                <properties>
                    <aoc.basedir>${user.home}/project</aoc.basedir>
                </properties>
            </profile>
        </profiles>
    </settings>


See `example-settings.xml`.
