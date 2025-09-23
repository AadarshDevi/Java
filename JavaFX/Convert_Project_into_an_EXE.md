# Convert a JavaFX Maven Project into and EXE

### Step 1: Add the Fat Jar Builder to `pom.xml`. Using Maven Shade
```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-shade-plugin</artifactId>
    <version>3.4.0</version>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>shade</goal>
            </goals>
            <configuration>
                <transformers>
                    <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                        <mainClass>com.alphagen.studio.float_data_recorder_2.Launcher</mainClass>
                    </transformer>
                </transformers>
            </configuration>
        </execution>
    </executions>
</plugin>
```

### Step 2: Build jar file > Use command prompt in the project folder in the IDE
```cmd
mvn clean package
```

A jar file for your project is in `target` folder.

### Step 3: Use JPackage to build the project
This is a bit confusing but I will try to make it easy.

1. Start with JPackage
```cmd
jpackage
```

**_From now on add the following tags._**

2. --input target
- this is where the generated jar file is located puts the code in the target folder of your javafx maven project.

2. --name <ProjectName>
- enter the project name

2. --input target
- this puts the code in the target folder of your javafx maven project.

2. --input target
- this puts the code in the target folder of your javafx maven project.

