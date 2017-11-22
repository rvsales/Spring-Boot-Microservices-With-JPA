# Spring-Boot-Microservices-With-JPA
Github repo for the Udemy course: Spring Boot Microservices with JPA



Snippet and resources

-----------------------------------------

## Documentations and useful tutorial ##

How to install JRE 1.8
https://www.java.com/it/download/help/download_options.xml

How to install Maven
https://maven.apache.org/install.html

How to install Git
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

How to install IntelliJIDEA Community Edition
https://www.jetbrains.com/idea/documentation/

How to install XAMPP:
https://www.apachefriends.org/download.html

Documentation for Spring Framework
https://docs.spring.io/spring/docs/current/spring-framework-reference/pdf/spring-framework-reference.pdf

Documentation for Spring Boot
https://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/

Documentation for JPA
https://docs.spring.io/spring-data/jpa/docs/current/reference/pdf/spring-data-jpa-reference.pdf

Good JPA tutorial
https://www.petrikainulainen.net/spring-data-jpa-tutorial/

how to define JPA query methods
https://www.petrikainulainen.net/programming/spring-framework/spring-data-jpa-tutorial-creating-database-queries-from-method-names/
https://www.petrikainulainen.net/programming/spring-framework/spring-data-jpa-tutorial-introduction-to-query-methods/

Documentation for JWT
https://stormpath.com/blog/jwt-java-create-verify
https://stormpath.com/blog/beginners-guide-jwts-in-java
https://github.com/jwtk/jjwt

Documentation for JSR-303
http://beanvalidation.org/1.0/spec/

Project Lombok
https://projectlombok.org/

Encryption library
http://www.jasypt.org/

How to install PostMan
https://www.angeloparziale.it/blog/2017/06/22/postman/

Documentation for AJAX:
https://www.w3schools.com/xml/ajax_intro.asp

------------------------------------------

# Snippets and useful links: #

## Spring Initializer ##
<https://start.spring.io/>

## Database structures ##

 ### name DB: tododb (H2 - in Memory DB) name is not important and never used in the code because it's an in-memory db ###
  
    TABLE users      (String EMAIL, String USERNAME, String PASSWORD) 
  
    TABLE todos      ( (autogenerated Integer) ID, String DESCRIPTION, Date DATE, String PRIORITY, String FK_USER) 
 
  ### name DB: statisticsdb (in MySQL) ###
  
    TABLE latest_statistics      ( (autogenerated Integer) ID, String DESCRIPTION, Date DATE, String EMAIL)
  

------------------------------------------

## pom.xml of ToDoMicroservice ##

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.quicktutorialz.learnmicroservices</groupId>
	<artifactId>ToDoMicroservice</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>ToDoMicroservice</name>
	<description>Demo project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.5.7.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<optional>true</optional>
			<version>1.16.10</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<!-- added -->
		<dependency>
			<groupId>org.jasypt</groupId>
			<artifactId>jasypt</artifactId>
			<version>1.9.2</version>
		</dependency>
		<dependency>
			<groupId>io.jsonwebtoken</groupId>
			<artifactId>jjwt</artifactId>
			<version>0.7.0</version>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
    </project>

------------------------------------------

## pom.xml di StatisticsMicroservice ##

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.quicktutorialz.learnmicroservices</groupId>
	<artifactId>StatisticsMicroservice</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>StatisticsMicroservice</name>
	<description>Demo project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.5.7.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<scope>runtime</scope>
			<version>5.1.39</version> <!-- MySQL version - without it gives errors-->
		</dependency>
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<optional>true</optional>
			<version>1.16.10</version> <!-- lombok added -->
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
    </project>



------------------------------------------
 # Interfaccia FRONT-END #
 
 ## HTML ##
 
 ```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ToDo Application</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.0/css/bulma.css">
    <link href="https://fonts.googleapis.com/css?family=Open+Sans:300,400,700" rel="stylesheet">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.3/jquery.min.js"></script>

</head>
<body>

<div id="signindiv">
    <section class="hero is-fullheight">
        <div class="hero-body">
            <div class="container has-text-centered">
                <div class="column is-4 is-offset-4">
                    <h3 class="title">Login</h3>
                    <p class="subtitle">Please login to proceed.</p>
                    <div class="box">
                        <figure class="avatar">
                            <img src="https://placehold.it/128x128">
                        </figure>
                        <form>
                            <div class="field">
                                <div class="control">
                                    <input class="input is-large" type="email" placeholder="Your Email" autofocus="" id="email">
                                </div>
                            </div>

                            <div class="field">
                                <div class="control">
                                    <input class="input is-large" type="password" placeholder="Your Password" id="password">
                                </div>
                            </div>
                            <a class="button is-block is-info is-large" id="submit">Login</a>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>
</div>


<div id="operationdiv" style="margin: 40px">

    <a id="signout" class="button is-info is-outlined" style="float: right">Sign out</a>
    <h2 class="title"><b>You're logged in!</b></h2>


    <div class="box has-text-centered">

        <h3 class="subtitle"><b>My ToDos</b></h3>

        <table class="table is-striped" style="margin: 0px auto;">
            <thead>
            <tr>
                <th>ID</th>
                <td>DESCRIPTION</td>
                <td>PRIORITY</td>
                <td>DATE</td>
                <td>DELETE</td>
            </tr>
            </thead>
            <tbody id="bodyTableToDos">
            <tr>
                <th>1</th>
                <td>First Description</td>
                <td>high</td>
                <td>12/03/2017</td>
                <td><a class="delete"></a></td>
            </tr>
            <tr>
                <th>2</th>
                <td>Second Description</td>
                <td>low</td>
                <td>11/03/2017</td>
                <td><a class="delete"></a></td>
            </tr>
            <tr>
                <th>3</th>
                <td>Third Description</td>
                <td>low</td>
                <td>10/03/2017</td>
                <td><a class="delete"></a></td>
            </tr>
            <tr>
                <th>4</th>
                <td>Fourth Description</td>
                <td>high</td>
                <td>09/03/2017</td>
                <td><a class="delete"></a></td>
            </tr>
            </tbody>
        </table>
        <br /><br />


        <div class="field has-addons">
            <p class="control">
               <span class="select">
                  <select id="newToDoPriority">
                    <option name="priority" value="" disabled selected>Priority</option>
                    <option value="high">high</option>
                    <option value="low">low</option>
                  </select>
               </span>
            </p>
            <p class="control is-expanded">
                <input class="input" id="newToDoDescription" type="text" placeholder="Description of ToDo"/>
            </p>
            <input type="hidden" id="newToDoEmail" value=""/>
            <p class="control">
                <a class="button is-primary" id="newToDo">
                    New To Do
                </a>
            </p>
        </div>

    </div>


    <div class="box has-text-centered">

        <h3 class="subtitle"><b>Present Statistics</b></h3>

        <table class="table is-striped" style="margin: 0px auto;">
            <thead>
            <tr>
                <th>ID</th>
                <td>DESCRIPTION</td>
                <td>DATE</td>
                <td>EMAIL</td>
            </tr>
            </thead>
            <tbody id="bodyTableStatistics">
            <tr>
                <th>1</th>
                <td>First Description</td>
                <td>12/03/2017</td>
                <td>alex@quicktutorialz.com</td>
            </tr>
            <tr>
                <th>2</th>
                <td>Second Description</td>
                <td>11/03/2017</td>
                <td>alex@quicktutorialz.com</td>
            </tr>
            <tr>
                <th>3</th>
                <td>Third Description</td>
                <td>10/03/2017</td>
                <td>alex@quicktutorialz.com</td>
            </tr>
            </tbody>
        </table>
        <br /><br />

    </div>


</div>

<script src="js/actions.js"> </script>
</body>
</html>
 
 ```

 ## Javascript ##
 
 ```
 $(document).ready(function(){
       $("#signindiv").show();         /* it shows the sign in and hide the operation sections */
       $("#operationdiv").hide();
     });
    /* function used to get the jwt from cookies after having saved it, for later async ajax calls to microservices */
    function getCookie(name) {
       var value = "; " + document.cookie;
       var parts = value.split("; " + name + "=");
       if (parts.length == 2)
          return parts.pop().split(";").shift();
    }
    /* function used to change the text of the url giving the impression we're changing page */
    function changeUrl(title, url) {
       if (typeof (history.pushState) != "undefined") {
          var obj = { Title: title, Url: url };
          history.pushState(obj, obj.Title, obj.Url);
       } else {
          alert("Browser does not support HTML5.");
       }
    }
    function showToDos() {
       //ajax call to ToDoMicroservice/showToDos
       $.ajax({                                                                        /* Ajax call to AccountMicroservice */
           url: 'http://localhost:8383/showToDos',
           type: "POST",
           success: function (data, status, xhr) {
              console.log(data);
              $("#bodyTableToDos").empty();
              jQuery.each(data.response, function(i, val) {
                 $("#bodyTableToDos").append("<tr><th>" + val.id + "</th><td>" + val.description + "</td><td>" + val.priority + "</td><td>" + convertDate(val.date) + "</td><td><p class='delete' onclick='deleteToDo(" + val.id + ")'></p></td></tr>");
              });
           },
           error: function(result) {
              alert("Error!");
              console.log(result);
           }
       });
       //ajax call to StatisticsMicroservice/getStatistics
       $.ajax({                                                                        /* Ajax call to AccountMicroservice */
           url: 'http://localhost:8384/getStatistics',
           type: "POST",
           data: {
             jwt: getCookie("jwt"),
             email: $("#email").val()
           },
           success: function (data, status, xhr) {
              console.log(data);
              $("#bodyTableStatistics").empty();
              jQuery.each(data.response, function(i, val) {
                 $("#bodyTableStatistics").append("<tr><th>" + val.id + "</th><td>" + val.description + "</td><td>" + convertDate(val.date) + "</td><td>" + val.email + "</td></tr>");
              });
           },
           error: function(result) {
              alert("Error!");
              console.log(result);
           }
       });
    }
    function deleteToDo(id) {
       //ajax call to ToDoMicroservice/deleteToDo
       $.ajax({
          url: 'http://localhost:8383/deleteToDo/' + id,
          type: "POST",
          success: function (data, status, xhr) {
             console.log(data);
             //call to showToDos() javascript function to update the list
             showToDos();
          },
          error: function(result) {
             alert("Error!");
             console.log(result);
          }
       });
    }
    function convertDate(inputFormat) {
        function pad(s) { return (s < 10) ? '0' + s : s; }
        var d = new Date(inputFormat);
        return [pad(d.getDate()), pad(d.getMonth()+1), d.getFullYear()].join('/');
    }
    /* sign in submit function */
    $("#submit").click(function(e) {
       e.preventDefault();
       $.ajax({                                                        /* Ajax call to AccountMicroservice for login */
          url: 'http://localhost:8383/login',
          type: "POST",
          data: {
             email: $("#email").val(),
             password: $("#password").val()
          },
          success: function (data, status, xhr) {
             $("#signindiv").hide();                              /* it hides sign in section and shows operation section */
             $("#operationdiv").show();
             changeUrl("ToDos","/todos.html");               /* it changes url after sign in */
             document.cookie = "jwt=" + xhr.getResponseHeader("jwt");  /* it saves in cookies the received token */
             $("#newToDoEmail").val($("#email").val());
             $("#password").val("");
             showToDos();
          },
          error: function(result) {
             alert("Sign in failed!");
             console.log(result);
          }
       });
    });
    /* sign out submit function */
    $("#signout").click(function(e) {
       e.preventDefault();
       document.cookie = "jwt=;expires=Thu, 01 Jan 1970 00:00:01 GMT;";        /* it cancels jwt from cookies */
       $("#signindiv").show();                                            /* it hides operations and shows sign in section */
       $("#operationdiv").hide();
       $("#email").val("");
       emptyForm();
       $("#newToDoEmail").val("");
       alert("You're logged out!");
       changeUrl("Signin","/signin.html");                                     /* it changes url again to signin.html */
    });
    $("#newToDo").click(function(e) {
       e.preventDefault();
       if( $("#newToDoPriority").val() == null ){
           alert("Insert a valid priority value");
       } else if ($("#newToDoDescription").val() == ""){
           alert("Insert a valid description value");
       }else{
           //ajax call to ToDoMicroservice/newToDo
           $.ajax({                                                        /* Ajax call to AccountMicroservice for login */
              url: 'http://localhost:8383/newToDo',
              type: "POST",
              data: {
                 description: $("#newToDoDescription").val(),
                 priority: $("#newToDoPriority").val(),
                 fkUser: $("#newToDoEmail").val()
              },
              success: function (data, status, xhr) {
                 emptyForm();
                 showToDos();
              },
              error: function(result) {
                 alert("Error!");
                 console.log(result);
              }
           });
       }
    });
    function emptyForm() {
       $("#newToDoDescription").val("");
       $("#newToDoPriority").val('');
    }
 ```

