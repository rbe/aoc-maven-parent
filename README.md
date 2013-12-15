# art of coding Parent POM

## User Settings

Define a base directory in `$HOME/.m2/settings.xml`:

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
        <profiles>
            <profile>
                <id>default</id>
                <properties>
                    <project.basedir>${user.home}/project</project.basedir>
                    <maven.basedir>${user.home}/maven</maven.basedir>
                    <maven.local.repo.public>file://${maven.basedir}/public-repo</maven.local.repo.public>
                    <maven.local.repo.private>file://${maven.basedir}/private-repo</maven.local.repo.private>
                    <maven.local.site>${maven.basedir}/site</maven.local.site>
                </properties>
            </profile>
        </profiles>
    </settings>


See `example-settings.xml`.

## Distribution Management

    <distributionManagement>
        <!-- maven-site-plugin -->
        <site>
            <id>localsite</id>
            <url>file://${maven.local.site}/${project.groupId}</url>
        </site>
        <repository>
            <id>publiclocaldisk</id>
            <name>Public Local Repository</name>
            <url>file://${maven.local.repo.public}</url>
        </repository>
    </distributionManagement>

## Profiles

### Java EE

    <profiles>
        <!-- JBoss -->
        <profile>
            <id>jboss-as-711</id>
            <dependencyManagement>
                <dependencies>
                    <!-- jboss-as-dist -->
                    <dependency>
                        <groupId>org.jboss.as</groupId>
                        <artifactId>jboss-as-dist</artifactId>
                        <version>7.1.1.Final</version>
                    </dependency>
                </dependencies>
            </dependencyManagement>
            <build>
                <pluginManagement>
                    <plugins>
                        <!-- jboss-as-maven-plugin, http://docs.jboss.org/jbossas/7/plugins/maven/latest/ -->
                        <plugin>
                            <groupId>org.jboss.as.plugins</groupId>
                            <artifactId>jboss-as-maven-plugin</artifactId>
                            <version>7.1.1.Final</version>
                        </plugin>
                    </plugins>
                </pluginManagement>
            </build>
        </profile>
        <!-- GlassFish -->
        <profile>
            <id>glassfish-3122</id>
            <dependencyManagement>
                <dependencies>
                    <!-- glassfish-embedded-all -->
                    <dependency>
                        <groupId>org.glassfish.main.extras</groupId>
                        <artifactId>glassfish-embedded-all</artifactId>
                        <version>3.1.2.2</version>
                    </dependency>
                </dependencies>
            </dependencyManagement>
            <build>
                <pluginManagement>
                    <plugins>
                        <!-- maven-glassfish-plugin -->
                        <plugin>
                            <groupId>org.glassfish.maven.plugin</groupId>
                            <artifactId>maven-glassfish-plugin</artifactId>
                            <version>2.1</version>
                        </plugin>
                    </plugins>
                </pluginManagement>
            </build>
        </profile>
    </profiles>

## Packaging

    <build>
        <plugins>
            <!-- maven-bundle-plugin -->
            <plugin>
                <groupId>org.apache.felix</groupId>
                <artifactId>maven-bundle-plugin</artifactId>
                <version>2.4.0</version>
            </plugin>
            <!-- maven-jar-plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>2.4</version>
            </plugin>
            <!-- maven-war-plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>2.3</version>
            </plugin>
            <!-- maven-ear-plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-ear-plugin</artifactId>
                <version>2.8</version>
            </plugin>
        </plugins>
    </build>

## Delivery 
