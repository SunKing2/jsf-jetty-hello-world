# JSF Tomcat example sample, works with Jetty too.

Not my original code, I forked this from user sachingsachin from
[https://github.com/sachingsachin/jsf-jetty-hello-world]

Run as:

```bash
mvn clean jetty:run
```

And hit:
[http://localhost:8080/hello.xhtml](http://localhost:8080/hello.xhtml)


# Code highlights

hello.xhtml:
```xml
	<h:form>
		<h:inputText value="#{helloBean.name}"></h:inputText>
		<h:commandButton value="Welcome Me" action="welcome"></h:commandButton>
	</h:form>
```

#HelloBean.java
```
// package, imports not shown
@ManagedBean
@SessionScoped
public class HelloBean implements Serializable {

    private static final long serialVersionUID = 1L;

    private String name;

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```


# (Optional!!!!) Running final build with $java command

Add this to the pom.xml file (this was tested with the following version of Jetty only: 9.3.21.v20170918):

```xml
<plugin>
  <!-- This plugin copies the jetty-runner plugin which enables
       running the war file as:
           java -jar target/dependency/jetty-runner.jar target/*.war
   -->
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-dependency-plugin</artifactId>
  <version>3.0.2</version>
  <executions>
    <execution>
      <phase>package</phase>
      <goals><goal>copy</goal></goals>
      <configuration>
        <artifactItems>
          <artifactItem>
            <groupId>org.eclipse.jetty</groupId>
            <artifactId>jetty-runner</artifactId>
            <version>${jettyVersion}</version>
            <destFileName>jetty-runner.jar</destFileName>
          </artifactItem>
        </artifactItems>
      </configuration>
    </execution>
  </executions>
</plugin>
```

Then add this as a dependency
```xml

    <dependency>
      <groupId>org.eclipse.jetty</groupId>
      <artifactId>jetty-server</artifactId>
      <version>${jettyVersion}</version>
    </dependency>
```

# My goal for changes on this project (if possible):
- update dependencies to use most modern jars available
- use JavaServer Faces API 2.3 (compatible with Java EE 8).
- reduce lines of code in Java, XHTML, and pom.xml to bare minimum to allow for a JSF demo.
- Use Java 9. (there are early problems with Mojarra implementations under Java 9)
