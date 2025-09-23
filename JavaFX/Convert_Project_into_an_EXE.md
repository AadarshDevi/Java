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
> this is where the generated jar file is located puts the code in the target folder of your javafx maven project.

2. --name <ProjectName>
> enter the project name

Example:
```cmd
--input MyJavaFXMavenProject
```

> I do not know if the below works.
```cmd
--input "My JavaFX Maven Project"
```

2. --main-jar

2. --main-class

2. --type app-image

2. --icon <Filepath/to/Icon.ico>

2. --dest <TheFolder/where/the/built/project/will/beIn>

2. --app-version 1.0.0

2. --vendor MyCompany

2. --verbose

2. --module-path

2. --add-modules

2. --win-console

2. --description

2. --java-options

## Final command
```cmd
jpackage --input target --name FloatDataRecorder_2_0 --main-jar float_data_recorder_2-1.0-SNAPSHOT.jar --main-class com.alphagen.studio.float_data_recorder_2.Launcher --type app-image --icon D:\College\Clubs\Miramar_Engineering_Club\float_data_recorder_2_icon.ico --dest installer --app-version 2.0.0 --vendor MiramarWaterJets --verbose --module-path "C:\development\java\lib\javafx-sdk-23.0.1\lib;C:\development\java\lib\jSerialComm_v_2_11_2" --add-modules javafx.controls,javafx.fxml,javafx.graphics,java.desktop,javafx.swing,com.fazecast.jSerialComm --win-console --description "MateROV Float Data Recorder" --java-options "-Dprism.order=sw -Dprism.verbose=true -Djava.library.path=C:\development\java\lib\javafx-sdk-23.0.1\bin"
```
