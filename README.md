# Hello world program for JSF with Jetty

Run as:

```bash
mvn clean jetty:run
```

And hit:
[http://localhost:8080/hello.xhtml](http://localhost:8080/hello.xhtml)


# JSF quick tour

In JSF, `managed bean` means a Java class that can be accessed from a JSF page and
the same is denoted by the annotation `javax.faces.bean.ManagedBean`

To use the JSF 2.0 components, they need to be declared in the JSF namespace at the
top of the page. Example:
```xml
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:f="http://java.sun.com/jsf/core"
      xmlns:h="http://java.sun.com/jsf/html">
```
With the above declaration, we now have two namespaces: `f` and `h`.  
And we use `h` in the hello.xhtml as:
```xml
	<h:form>
		<h:inputText value="#{helloBean.name}"></h:inputText>
		<h:commandButton value="Welcome Me" action="welcome"></h:commandButton>
	</h:form>
```
`inputText` and `commandButton` are straightforward widgets from JSF.  

Note the use of `helloBean.name`. The helloBean was created because of the annotation
[@ManagedBean](http://docs.oracle.com/javaee/6/api/javax/faces/bean/ManagedBean.html)
on the class HelloBean.java. This annotation is responsible for creating an object of the class
and making it accessible as `helloBean` in the xhtml pages.

Another thing to note is the `action="welcome"` attribute. This attribute is responsible for
linking the two xhtml pages.
