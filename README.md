# Java 21 Template

This is a Java 21 template with Maven and JUnit. It can be used to experiment with many modern Java
features, and experience which functional features Java offers. You can use this template, for
example, to build a compiler.

## Usage

Building happens with `make`, running with `./hello`. The project build process is executed via the
Maven wrapper which means that you do not need Maven on your machine.

To execute the application, first build the application, then run it. 

```bash
make
./hello Petra
```

## Changes

Remember to update the `pom.xml` with your actual main class. If the class `Hello` in the
package `com.felixseifert.java` contains the main method of your whole application, the Maven file
should include the following line.

```xml

<mainClass>com.felixseifert.java.Hello</mainClass>
```

After running the command `make` in your home directory, Maven compiles a JAR of your application.
To run this JAR via the provided executable script `hello`, change the name of the JAR in the
script `hello` to the name of your compiled JAR. For the JAR name
`java-21-maven-project-1.0-SNAPSHOT`, the script includes the following line.

```bash
exec java -jar target/java-21-maven-project-1.0-SNAPSHOT.jar "$@"
```

You can also rename the executable script. If the executable should be called `hola`, then run:

```bash
mv hello hola
```

## Tests

To run the tests, execute `make test`. This will internally trigger the execution of `make build`
before actually triggering the tests.

The tests are written with JUnit and can be found in the abstract class
[`AbstractHelloTest`](src/test/java/com/felixseifert/java/AbstractHelloTest.java). The same tests
are executed in two different ways: once via
[calling the Java main method](src/test/java/com/felixseifert/java/HelloJavaTest.java) and once via
[calling the executable script](src/test/java/com/felixseifert/java/HelloCmdTest.java) (which calls
the JAR). You can observe how the same tests use different configs via implementing abstract
methods.
