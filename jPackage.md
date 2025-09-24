
# JPackage

jPackage is a java tool that comes with the JDK. This is used to convert java projects into .exe, .msi,
etc,. In this document, I will explain some of the flags/commands I used to create my .exe.

NOTE: All the commands are done in Command Prompt in the MyProject root folder.

### Start jPackage
to use the jPackage commmand go to ther terminal and type `jpackage`.

### **_IMPORTANT: From now on the following tags are added to jpackage_**

#### --input target
This is where the generated jar file is located puts the code in the target folder of your javafx maven project.
If the jar `myProject-1.0-SNAPSHOT.jar` is located in `/target` in the project, then the passed data would be target.
`/target` is located in the root of project.
```
├── src
│   ├── main
│   │   ├── java
│   │   │    └── Main.java
│   │   └── resource
├── target
│   ├── compiled files/folders
│   └── myProject-1.0-SNAPSHOT.jar (The JAR Compiled)
└── installer
```
The input jar for `jpackage` is in `/target`
```cmd
--input target
```

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
