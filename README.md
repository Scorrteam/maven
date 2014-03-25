SCORR Maven repository - user's guide
===

Corporate Maven Repository for 3rd-party artifacts

### How to use SCORR repository

Add the following to the project's pom.xml file

    <repositories>
        <repository>
            <id>scorr-maven</id>
            <url>http://maven.scorr.ru/master/releases/</url>
            <name>SCORR Maven Repository</name>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
    </repositories>

### How to deploy broken 3rd-party artifacts to SCORR repository

1. git clone Scorrteam maven repo
2. Checkout artifact source
3. Refine its pom.xml file (Java version, plugins, dependencies, scopes, sources and javadocs generation, etc)
4. Install to cloned scorr repo (see code below)
5. commit new artifacts
6. git push origin master

mvn clean package install:install-file 
  -Dfile=target/trendrr-nsq-client-1.3-SNAPSHOT.jar 
  -Dsources=target/trendrr-nsq-client-1.3-SNAPSHOT-sources.jar
  -Djavadoc=target/trendrr-nsq-client-1.3-SNAPSHOT-javadoc.jar 
  -DartifactId=trendrr-nsq-client 
  -DgroupId=com.github.dustismo 
  -Dversion=1.3 
  -Dpackaging=jar 
  -DpomFile=./pom.xml 
  -DupdateReleaseInfo=true 
  -DlocalRepositoryPath=../maven/releases
