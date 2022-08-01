JMeter maven project Amazon Web Service client API library for Java application

Download JMeter from Apache

Fork source code to local machine. Open file Login.jmx for more detail about test scenario.

Run command to run JMeter by maven plugin

mvn verify

        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.14.1</version>
            </plugin>
            <plugin>
                <groupId>com.lazerycode.jmeter</groupId>
                <artifactId>jmeter-maven-plugin</artifactId>
                <version>2.2.0</version>
                <executions>
                    <execution>
                        <id>jmeter-tests</id>
                        <phase>verify</phase>
                        <goals>
                            <goal>jmeter</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>com.lazerycode.jmeter</groupId>
                <artifactId>jmeter-analysis-maven-plugin</artifactId>
                <version>1.0.6</version>
                <executions>
                    <execution>
                        <phase>verify</phase>
                        <goals>
                            <goal>analyze</goal>
                        </goals>
                        <configuration>
                            <!--
                            An AntPath-Style pattern matching a JMeter XML result file to analyze. Must be a fully qualified path.
                            File may be GZiped, must end in .gz then.
                            Default: not set.
                            Required.
                            -->
                            <source>${project.build.directory}/**/*.jtl</source>

                            <!--
                            directory where to store analysis result files.
                            Default: ${project.build.directory}
                            Required.
                            -->
                            <targetDirectory>${project.build.directory}/jmeter/results</targetDirectory>
                            <processAllFilesFound>true</processAllFilesFound>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
