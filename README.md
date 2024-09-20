# NiFi Custom Processor Project

## English Instructions

This repository provides a template for creating custom Apache NiFi processors using Java and Maven. The project includes the necessary configuration to create a NAR (NiFi Archive) file that can be deployed in a NiFi instance.

### 1. How to Clone the Project

To start, clone the repository to your local machine:

` git clone https://github.com/StopSandal/NifiCustomProcess `

### 2. Set Up the Target JDK Version

Ensure the target JDK version is set to match the NiFi instance's requirements. NiFi typically runs with Java 11, but you can adjust this in the pom.xml file.

In the pom.xml, find the <properties> section and set the correct Java version:

```xml
<properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
```

If you are using a NiFi Docker container, you can specify the Java version when building the image or updating the Docker configuration.

### 3. How to Build the NAR File
To build the project and create the NAR file, run the following Maven command:

```bash
mvn nifi-nar:nar -f pom.xml
```

This command will compile the project and generate the NAR file in the target folder.

Or go to Maven->plugins->nifi-nar->nar then Double-click

### 4. Adding the NAR File to a NiFi Docker Container
Follow these steps to add your custom processor to NiFi running in a Docker container:

1. Create a folder with name 'extensions' on yours device.

2. Copy the compiled NAR file into the extensions folder.

3. Access the NiFi container and navigate to the correct directory.

4. Inside the container, find the 'nifi-current' folder located at /opt/nifi/nifi-current.


5. Replace the existing folder with your new extensions folder by copying your folder into nifi-current.

Press on 'nifi-current' folder, then RMB, at context menu press import, and choose the previosly created extensions folder.

Then restart Nifi or container.

Now, your custom processor should be available in NiFi.

