couple of useful maven commands

* most often
```bash
mvn clean compile install
```
* to execute a jar
```bash
mvn exec:java -Dexec.mainClass=de.tudarmstadt.ukp.dkpro.examples.stanfordcorecomponents.StanfordCoreComponents
```
* to kindly ask maven to generate the CLASSPATH it uses
```bash
mvn dependency:build-classpath -Dmdep.outputFile=classpath.txt
```
* run specific tests from test class
```bash
mvn -Dtest=NumberTextFilterTests#testEng* test 
```
