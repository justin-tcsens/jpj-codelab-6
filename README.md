# Vehicle Service
Vehicle service endpoint.

## Tasks
- Add JooQ plugin execution goals into Spring Boot processes, after flyway plugin execution goal.
	- Repleace the <package_name> with package name specified in your project.
	- Verify database connection url string, to match with your local environment.

    ```
        <!-- JooQ -->
			<plugin>
				<groupId>org.jooq</groupId>
				<artifactId>jooq-codegen-maven</artifactId>
				<executions>
					<execution>
						<id>generate-postgres</id>
						<phase>generate-sources</phase>
						<goals>
							<goal>generate</goal>
						</goals>
						<configuration>
							<jdbc>
								<driver>org.mariadb.jdbc.Driver</driver>
								<url>jdbc:mariadb://localhost:3306/jpj-training</url>
								<user>app</user>
								<password>password</password>
							</jdbc>
							<generator>
								<database>
									<name>org.jooq.meta.mariadb.MariaDBDatabase</name>
									<includes>.*</includes>
									<excludes></excludes>
									<inputSchema>jpj-training</inputSchema>
									<unsignedTypes>false</unsignedTypes>
									<integerDisplayWidths>false</integerDisplayWidths>
								</database>
								<generate>
									<pojos>true</pojos>
									<pojosEqualsAndHashCode>true</pojosEqualsAndHashCode>
									<javaTimeTypes>true</javaTimeTypes>
									<fluentSetters>true</fluentSetters>
								</generate>
								<target>
									<packageName><package_name>.models</packageName>
									<directory>target/generated-sources/jooq</directory>
								</target>
							</generator>
						</configuration>
					</execution>
				</executions>
			</plugin>
		<!-- JooQ -->
    ```
- Save pom.xml.

### Notes:
- Run '.\mvnw clean install' to install necessary package defined in pom.xml
- Run '.\mvnw spring-boot:run' to start the Spring Boot application.
