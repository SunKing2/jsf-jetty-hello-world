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
