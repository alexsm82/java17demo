# Java 17 Migration Demo

This demo application was built to run on Java 8 but contains migration issues when run on Java 17. The slides that go with this demo are available here: https://www.slideshare.net/AlexMotley3/making-the-move-to-java-17-jconf-2022.

Prereqs:
- Maven
- Java 8 and 17 (I am using the latest from https://developer.ibm.com/semeru-runtime-downloads/)
- Download Eclipse Transformer (I am using 0.5 version from https://repo.maven.apache.org/maven2/org/eclipse/transformer/org.eclipse.transformer.cli/0.5.0/ - download distribution jar then unzip)
- For ease, install app in an IDE. I am using Eclipse 2022-06 importing as a Maven project.

Demo flow:

1. Show app, explain what it does and how it works. Also go through the pom.xml

2. To show the application running on Java 8, run `mvn clean install`. Then `java -jar target/java17demo-1.0-jar-with-dependencies.jar`

3. Try running with Java 17, it will fail

4. Run the binary scanner on the app using mvn exec:java

5. Go through the report, make the appropriate updates to the app (and pom.xml). A copy of the needed updates are in the src/main/java/hava17demo/java17 folder

6. Run JDeps on the app to determine if further updates are needed (ensure you are running the JDeps from Java17!): `jdeps -jdkinternals target/java17demo-1.0-jar-with-dependencies.jar`

7. Run the Transformer to update jax-b to the Jakarta packages. `java -jar org.eclipse.transformer.cli-0.5.0.jar ../src`

8. Recompile and run the app with Java 17, it should now work as it did before: `mvn clean install`, `java -jar target/java17demo-1.0-jar-with-dependencies.jar`
