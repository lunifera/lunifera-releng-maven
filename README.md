# lunifera-releng-maven
==================

## Setting up the development environment

###1. Set the local deployment directory:

If you are using Eclipse, go to Preferences/Maven/User Settings. Then click in Open File to open the user's settings.xml file.
I you want this file could be found at ~user/.m2 directory.
In the opened file created a new profile and include the property 'lunifera.developer.home' and set a value for it that points to a created directory where the result of each repository's build will be copied.
See this example:

    <profiles>
      <profile>
        <id>lunifera-dev</id>
        <activation>
          <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
          <lunifera.developer.home>/User/myuser/LuniferaDev/</lunifera.developer.home>
        </properties>
      </profile>
    </profiles>


###2. Build and install the parent POMs:
* before build any other repository you must build and install the releng parent projects:
```cd lunifera-releng-maven```
```mvn clean install```


## Development Tasks

Before contribute code to the project some steps are needed.

### Set the default formatter profile into the Eclipse IDE.
  This is needed to prevent git to have to much conflicts due to format conflicts.

 * Open the Preferences/Java/Code Style/Formatter dialog and import the file lunifera-formatter.xml.
