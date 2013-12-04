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

###2. Clone the source repositories:
* To easy this job, you can clone only the lunifera-releng-maven repository:    
```git clone git@github.com:lunifera/lunifera-releng-maven.git```
* then use this scripts to clone other related projects:    
``` ./scripts/git-clone-others.sh```

To be able to contribute you must fork the desired lunifera's [github repository](https://github.com/lunifera?tab=repositories) and clone from it.


###3. Build and install the parent POMs:
* before build any other repository you must build and install the releng parent projects:
```cd lunifera-releng-maven```
```mvn clean install```


## Development Tasks

### Getting source changes:
* You can use the git-all script to pull updated from all cloned repositories:    
```./scripts/git-all.sh pull```


### Build a latest kepler p2 repo using the remote federated (composite) p2. 
* open a terminal in the repository root folder and type this:
```mvn -P lunifera.build.p2 -Dlunifera.build.uses.remote.federated.p2```

* The remote federated p2 is the default, so the property 'lunifera.build.uses.remote.federated.p2' can be omitted.
```mvn -P lunifera.build.p2```


### Build a latest kepler p2 repo using the remote federated p2 and deploying the results to local deployment folder. 
* open a terminal in the repository root folder and type this:
```mvn -P lunifera.build.p2 -Dlunifera.build.uses.remote.federated.p2 -Dlunifera.deploy.to.local.federated.p2```


### Build a latest kepler p2 repo using the local federated p2 and deploying the results to local deployment folder. 
* open a terminal in the repository root folder and type this:
```mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.federated.p2 -Dlunifera.deploy.to.local.federated.p2```


### Build a latest kepler p2 repo using both local and remote federated p2 and deploying the results to local deployment folder: 
* open a terminal in the repository root folder and type this:
```mvn -P lunifera.build.p2 -Dlunifera.build.uses.local.federated.p2 -Dlunifera.build.uses.remote.federated.p2 -Dlunifera.deploy.to.local.federated.p2```


