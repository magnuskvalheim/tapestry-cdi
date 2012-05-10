Tapestry-CDI
============

Tapestry-cdi allows you to inject JSR 299 managed beans into tapestry services and components.


Using @Inject
-------------

Contributes to InjectionProvider so that we can use @Inject (from tap5 or javax.inject).

### @CDI, mostly for internal testing
Alternatively the @CDI annotation can be used which uses own annotation  worker and objectfactory.


Exclude tapestry managed services
---------------------------------

If you have a beans.xml in your tapestry project then cdi could attempt to manage tapestry services. This is undesirable.
An easy solution exist for WELD. You can exclude classes from scanning. http://docs.jboss.org/weld/reference/1.1.0.Final/en-US/html_single/#d0e5767

<pre>
<code>
	&lt;?xml version="1.0"?&gt;
	&lt;beans xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xmlns:weld="http://jboss.org/schema/weld/beans"
		xsi:schemaLocation="
	          http://java.sun.com/xml/ns/javaee http://docs.jboss.org/cdi/beans_1_0.xsd
	          http://jboss.org/schema/weld/beans http://jboss.org/schema/weld/beans_1_1.xsd"&gt;
		&lt;weld:scan&gt;
			&lt;weld:exclude name="com.tapestry.app.**" /&gt;
		&lt;/weld:scan&gt;
	&lt;/beans&gt;
</code> 
</pre>