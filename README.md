uglifyjs-maven-plugin
=====================

A maven plugin that runs UglifyJS on a directory of javascript files.

Forked from https://github.com/tqh/uglifyjs-maven-plugin
which in turn was based on the excellent https://github.com/kawasima/handlebars-maven-plugin

Introduction
------------

uglifyjs-maven-plugin is used to run UglifyJS on the javascript files of your project.

Goals
-----

Goal                 |Description
---------------------|-------------------------------
uglifyjs:uglify      |Compress javascript files

### uglifyjs:uglify

Currently the plugin is using the same artifact from the forked repository. This may change in the future.

Full name
:net.tqh.plugins:uglifyjs-maven-plugin:1.0:uglify

Description
:uglify Run UglifyJS on files in sourceDirectory saving the minified files on the same directory.

#### Optional parameters

Name             |Type    |Description
-----------------|--------|--------------------------------------
skip             |Boolean |Flag that allows user to skip execution of the plugin. (Currently only available when building this plugin from source.)
sources          |FileSet |The directory containing javascript source files.
encoding         |String  |Charset of javascript files.

Repo
----

If you want to use this plugin in your maven project add the following plugin repository

    <pluginRepositories>
      <pluginRepository>
        <id>uglifyjs-maven-plugin</id>
        <url>https://raw.github.com/meiao/uglifyjs-maven-plugin/master/repo</url>
      </pluginRepository>
    </pluginRepositories>

and call the plugin during the build process, e.g.:

    <build>
        <plugins>
            <plugin>
                <groupId>net.tqh.plugins</groupId>
                <artifactId>uglifyjs-maven-plugin</artifactId>
                <version>1.0</version>
                <executions>
                    <execution>
                        <id>uglify-js</id>
                        <phase>compile</phase>
                        <goals>
                            <goal>uglify</goal>
                        </goals>
                        <configuration>
                            <skip>false</skip>
                            <sources>
                                <directory>${project.build.directory}/classes/js</directory>
                                <excludes>
                                    <exclude>org/foo</exclude>
                                    <exclude>org/bar</exclude>
                                    <exclude>**/*.min.js</exclude>
                                </excludes>
                                <includes>
                                    <include>org/foo/lib</include>
                                </includes>
                            </sources>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
