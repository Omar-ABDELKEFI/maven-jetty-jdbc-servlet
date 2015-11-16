
A simple servlet that uses Maven, JDBC, and Jetty to say 'Hello world'

Build / Run
-----------

    mvn clean compile install jetty:run

Then navigate to 

    http://localhost:8080/mjjs/hello

If you get this message:

    Reading /application.properties ...
    Your database is missing or inaccessible

Fire up MAMP, go to localhost:8888/phpMyAdmin, click on SQL tab and
copy paste this line of code into the text box and hit "Go"

    CREATE DATABASE mjjs DEFAULT CHARACTER SET utf8;
    GRANT ALL ON mjjs.* TO 'mjjsuser'@'localhost' IDENTIFIED BY 'mjjspassword';
    GRANT ALL ON mjjs.* TO 'mjjsuser'@'127.0.0.1' IDENTIFIED BY 'mjjspassword';

Refresh the page, and mjjs now appears on the left.
Click on mjjs and then click on the SQL tab. 
Copy paste this command into the text box and hit go

    CREATE TABLE mjjs (name TEXT) ENGINE = InnoDB DEFAULT CHARSET=utf8;
    INSERT INTO mjjs (name) VALUES ('tsugi');

Refresh this page: http://localhost:8080/mjjs/hello
If success, this is what will show up:

    Successfully read 1 rows from the database
    
Background Documentation to Read
--------------------------------

These are some online resources to read that explain how things in this servlet works:

* [How to Write a Hello World Servlet](http://stackoverflow.com/questions/18821227/how-to-write-hello-world-servlet-example)
* [Lesson: JDBC Basics](https://docs.oracle.com/javase/tutorial/jdbc/basics/)
* HttpServlet interface - [javax.servlet.http.HttpServlet](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServlet.html)
* Request Object interface - [javax.servlet.http.HttpServletRequest](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletRequest.html)
* Response Object Interface - [javax.servlet.http.HttpServletResponse](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletResponse.html)
* Database Connection interfaces - [java.sql](http://docs.oracle.com/javase/7/docs/api/java/sql/package-summary.html)


Errors
------

If you end up with this error, 

    No plugin found for prefix 'jetty' in the current project and in the
    plugin groups [org.apache.maven.plugins, org.codehaus.mojo] available
    from the repositories

add this to your

    ~/.m2/settings.xml

    <settings>
        <pluginGroups>
            <pluginGroup>org.mortbay.jetty</pluginGroup>
        </pluginGroups>
    </settings>

