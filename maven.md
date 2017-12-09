To generate mvn file structure
`mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`

`mvn help:effective-pom` to generate effective POM.xml

`mvn exec:java -Dexec.mainClass=org.sonatype.mavenbook.weather.Main -Dexec.args="70112"` to execute a java main class with passed in arg
