## Import a Certificate

from the jre folder (either standalone or within a jdk), and running cmd as an ADMIN:
- `keytool -import -alias sonar -keystore cacerts -file sonar.cer`

where 
- sonar.cer is the certificate file, exported as Base-64 encoded X.509 (.CER)
- cacerts is a file, use /cacerts if it's a folder
- sonar is the alias

## Setting CLASSPATH

to give the java compiler access to certain jar files

can do so either all the time (classpath) or per application (cmd)

detailed here:

https://docs.oracle.com/javase/7/docs/technotes/tools/windows/classpath.html


