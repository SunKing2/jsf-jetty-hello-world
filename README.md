# JSF Tomcat example sample, works with Jetty too.

Not my original code, I forked this from
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

Add this to the pom.xml file:

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
