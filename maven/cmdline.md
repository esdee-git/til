couple of useful maven commands

most often
mvn clean compile install

to execute a jar
mvn exec:java -Dexec.mainClass=de.tudarmstadt.ukp.dkpro.examples.stanfordcorecomponents.StanfordCoreComponents

to kindly ask maven to generate the CLASSPATH it uses
mvn dependency:build-classpath -Dmdep.outputFile=classpath.txt

run specific tests from test class
mvn -Dtest=NumberTextFilterTests#testEng* test 

