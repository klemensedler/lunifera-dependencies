# lunifera-releng
==================

## Steps to build:


###1 Build the components that do not exists in any maven repository 

There is not binary version of Icepush-gwt So it is needed to download the source, build it and install it in local m2 repository.

- download the icepush-gwt-2.0.0-alpha3.zip that contains the source from here: http://www.icesoft.org/java/downloads/icepush-downloads.jsf;
- unzip it and enter in the created folder;
- build it using the command: ant;
- install the jars:
		'''mvn install:install-file -Dfile=icepush.jar -DgroupId=org.icefaces 
			\ -DartifactId=icepush -Dversion=2.0.0-alpha3 -Dpackaging=jar
	       
	       mvn install:install-file -Dfile=icepush-gwt.jar -DgroupId=org.icefaces 
			\ -DartifactId=icepush-gwt -Dversion=2.0.0-alpha3 -Dpackaging=jar'''

###2 Install POM-First bundles
Those bundles can't be build by Tycho, so it must be run separately.

- > cd lunifera-deps
- > mvn clean install -f pom-first-aggregator.xml


###3 Generate lunifera-deps P2 repository

- >  mvn clean install -P lunifera.build.p2