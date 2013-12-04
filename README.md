# lunifera-releng
==================

## Steps to build:


###1 Set the user settings.xml

As there are dependencies jars that doesn't exist in maven central repository you need to set your environment to use some repositories.

You can use the setting.xml provided here: https://github.com/lunifera/lunifera-releng-maven/blob/master/settings.xml as a template for setting yours.

###2 Install POM-First bundles
Those bundles can't be build by Tycho, so it must be run separately.

- > cd lunifera-deps
- > mvn clean install -f pom-first-aggregator.xml


###3 Generate lunifera-deps P2 repository

- >  mvn clean install -P lunifera.build.p2