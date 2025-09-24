
# jPackage

jPackage is a java tool that comes with the JDK. This is used to convert java projects into .exe, .msi,
etc,. In this document, I will explain some of the flags/commands I used to create my .exe.

NOTE: All the commands are done in Command Prompt in the MyProject root folder.
In my command prompt I see that I am in my java project.
```cmd
PS D:\Projects\Java\MyProject>
```

The jar `myProject-1.0-SNAPSHOT.jar` is located in `/target` in the project.

### Start jPackage
to use the jPackage commmand go to ther terminal and type:
```cmd
jpackage
```

## **_IMPORTANT: From now on the following tags are added to jpackage_**

### --input
This is where the generated jar file is located puts the code in the target folder of your javafx maven project. `/target` is located in the root of project.
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
--input <folder/to/myProject-1.0-SNAPSHOT.jar>
```
#### Example
```cmd
--input target
```
<br>

### --name
This flag is used to name the .exe/.msi file.
```cmd
--name <projectName>
```
#### Example
```cmd
--input MyProject
--input "My Project"
```
<br>

### --main-jar
This takes in the name of the jar file for input. Remember that this is .jar compiled.
```cmd
--main-jar <nameOfJar.jar>
```
#### Example
```cmd
--main-jar myProject-1.0-SNAPSHOT.jar
```
<br>

### --main-class
This flag is used to get the Main class of your java project. This needs to be the full path of the class. Meaning the class and its package.
```cmd
--main-class <the/package/of/Main.java>
```
#### Example
```cmd
--main-class com.author.group.MyProject.Main
```
<br>

### --type
This flag will tell what type of application will be after compiling. I have tried only `app-image` but `exe` and `msi` are some of the valid arguments.
```cmd
--type <typeOfExcecutable>
```
#### Example
```cmd
--type app-image
--type exe
--type msi
```
<br>

### --icon
This flag takes in an `.ico` as an argument. This is the icon for the app. This needs the filepath to the icon.
```cmd
--icon <path/to/icon.ico>
```
#### Example
```cmd
--icon D:\Projects\Java\MyProject\javaIcon.ico
```
<br>

### --dest
This below is out project structure. This flag takes in the excecutable file's destnation. The `.exe` will be in this folder.
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
```cmd
--dest <destination\of\myProject.exe>
```
#### Example
```cmd
--dest installer
```
<br>

### --app-version
This flag is for the version of the app. This stores the version number of the project.
```cmd
--app-version <appVersion>
```
#### Example
```cmd
--app-version 1.0.0
```
<br>

### --vendor
This flag takes in to store the organization of this java project.
```cmd
--vendor <companyThatCreatedTheProgram>
```
#### Example
```cmd
--vendor MyCompany
```
<br>


### --verbose
I do not know what this flag does.

### --module-path
The java project uses maven as a build tool. So we need to add all the libraries' .jar files to this. Without this, the program will not work properly. Use `;` to seperate filepaths of the jar files. The path given are the folders that contain the .jar files.
```cmd
--module-path single/jar/file/destination
--module-path "one/jar/file/destination;another/jar/file/destination"
```
#### Example
```cmd
--module-path C:/java/javafx-sdk-23-0-1/lib
--module-path "C:/java/javafx-sdk-23-0-1/lib;C:/java/lib/jSerialComm_v_2_11_2"
```
<br>

### --add-modules
Now that we have the paths for the libraries, we need to add them to be used. Without adding the jars, the paths are useless. To add multiple jars, add them by writing their names of the .jar files. `javafx-controls` from `pom.xml` has a `javafx.controls.jar` in javafx lib folder.
```cmd
--add-modules <jarFileNames>
```
#### Example
```cmd
--add-modules javafx.controls
--add-modules javafx.controls,javafx.fxml,javafx.graphics,java.desktop,javafx.swing,com.fazecast.jSerialComm
```
<br>

### --win-console
By adding this flag, when app is running, it will open the app's terminal. This can be used for debugging.
```cmd
--win-console
```

### --description
This adds a description of the app. When checking Task Manager, the threads will have this text.
```cmd
--description <programDescription>
```
#### Example
```cmd
--description "This is MyProgram"
```
<br>

### --java-options
I believe that this flag is used for vmargs the `String[] args` in `public stativ void main(String[] args)`. This is used so javafx will be able to run. This is used for libraries that have .dll files like javafx. Unlike the other flags, to have multiple arguments, to seperate them, add a space " " like in the example below. Explore the arguments for this flag before creating the executable.
```cmd
--java-options <vmargs>
```
#### Example
```cmd
--java-options "-Djava.library.path=C:/java/lib/javafx-sdk-23.0.1/bin"
--java-options "-Dprism.order=sw -Djava.library.path=C:/java/lib/javafx-sdk-23.0.1/bin"
```
<br>

## The Final jPackage Command
This is the final command that is created with the above flags. Please double check and search for the flags your java project needs. This command might fail as it is possible.
```cmd
jpackage --input target --input MyProject --main-jar myProject-1.0-SNAPSHOT.jar --main-class com.author.group.MyProject.Main --type app-image --icon D:\Projects\Java\MyProject\javaIcon.ico --dest installer --app-version 1.0.0 --vendor MyCompany --module-path "C:/java/javafx-sdk-23-0-1/lib;C:/java/lib/jSerialComm_v_2_11_2" --add-modules javafx.controls,javafx.fxml,javafx.graphics,java.desktop,javafx.swing,com.fazecast.jSerialComm --win-console --description "This is MyProgram" --java-options "-Dprism.order=sw -Djava.library.path=C:/java/lib/javafx-sdk-23.0.1/bin"
```
