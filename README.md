# springboot-war-skeleton

This is spring boot war skeleton application.

Requirements:

Java 8

Maven 3

Tomcat 8

Steps:

1. Download and extract https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.9/bin/apache-tomcat-8.5.9.tar.gz 
2. Download springboot-war-skeleton application from Git.
3. Execute 'mvn clean package' from root directory.
4. cp web/target/charlie.war ../../apache-tomcat-8.5.9/webapps/
5. cd ../apache-tomcat-8.5.9/bin/
6. ./startup.sh


Notes:

To get war file executable:

	Edit module web pom.xml 
		<package>war</package>
		<dependency>
		    <groupId>org.springframework.boot</groupId>
		    <artifactId>spring-boot-starter-tomcat</artifactId>
		    <version>1.5.2.RELEASE</version>
		    <scope>provided</scope>
		</dependency>

		<plugin>
			<artifactId>maven-war-plugin</artifactId>
			<configuration>
				<failOnMissingWebXml>false</failOnMissingWebXml>
			</configuration>
		</plugin>

		<finalName>charlie</finalName> <!-- Same name as property field 'server.contextPath' of application.properties file

	Edit file MyApplication.java:

		@SpringBootApplication
		@ComponentScan("com.charlie.example.web.properties,com.charlie.example.services.service, com.charlie.example.services.dao,com.charlie.example.web.controller")
		@EntityScan("com.charlie.example.model.entity")
		public class MyApplication extends SpringBootServletInitializer {

		    @Override
		    protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
			return application.sources(MyApplication.class);
		    }

		    public static void main(String[] args) throws Exception {
			SpringApplication.run(MyApplication.class, args);
		    }
		}    
		

	
