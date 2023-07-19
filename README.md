# Protocol-Buffer
Protobuf Learning &amp; Practise

resources :
   1. https://protobuf.dev/programming-guides/proto3/
   2. https://protobuf.dev/getting-started/javatutorial/
   3. https://drive.google.com/drive/folders/1t4VzmV9D2u4bnd8jcYD0hEMyNq8Ue6Tb?usp=sharing



necessary dependencies in pom file :
    
    <properties>
        <protobuf.version>3.14.0</protobuf.version>
        <protobuf-plugin.version>0.6.1</protobuf-plugin.version>
        <grpc.java.version>1.54.0</grpc.java.version>
        <java.version>11</java.version>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>
    
    <dependencies>
        <!--
        By adding this dependency to our project, we enable your application to interact with gRPC services
        as a client. The gRPC Stub library abstracts the underlying communication details
        and provides a convenient API for making remote procedure calls to the gRPC server.
        It handles serialization and deserialization of data and provides a seamless experience for developers,
        making it feel like they are calling local methods even though they are communicating with a remote gRPC server.
        The grpc-stub dependency is crucial for implementing gRPC clients in application and
        enabling communication with gRPC services.
        -->
        <dependency>
            <groupId>io.grpc</groupId>
            <artifactId>grpc-stub</artifactId>
            <version>${grpc.java.version}</version>
        </dependency>
        
        <!--
        The gRPC Protobuf library provides the necessary runtime support for working with Protocol Buffers,
        which are used for serializing and deserializing structured data in a language-agnostic and efficient way.
        gRPC itself uses Protocol Buffers as its default serialization format for messages in communication
        between client and server.By adding this dependency in project,
        we can use gRPC's protobuf capabilities to define service contracts and messages
        using Protocol Buffers and then use gRPC to generate the necessary client and server code
        -->
        <dependency>
            <groupId>io.grpc</groupId>
            <artifactId>grpc-protobuf</artifactId>
            <version>${grpc.java.version}</version>
        </dependency>
        

    <!--These dependencies are necessary for Java 9+ compatibility
            when using gRPC (Google Remote Procedure Call) with the protobuf (Protocol Buffers) library.
            Java 9 introduced some changes to the classpath and module system,
            and These dependencies helps ensure compatibility with older Java-based libraries
            like Apache Tomcat that may not have been updated to fully support Java 9 and later.-->

        <dependency>
            <!-- Java 9+ compatibility - Do NOT update to 2.0.0 -->
            <groupId>jakarta.annotation</groupId>
            <artifactId>jakarta.annotation-api</artifactId>
            <version>1.3.5</version>
            <optional>true</optional>
        </dependency>


         <!--        <dependency>
                    &lt;!&ndash; necessary for Java 9+ &ndash;&gt;
                    <groupId>org.apache.tomcat</groupId>
                    <artifactId>annotations-api</artifactId>
                    <version>6.0.53</version>
                    <scope>provided</scope>
                </dependency>
                            -->


                <configuration>
                    <!-- protocol's configuration for linux-->
                    <protocArtifact>com.google.protobuf:protoc:${protobuf.version}:exe:linux-x86_64</protocArtifact>
                    <pluginId>grpc-java</pluginId>
                    <pluginArtifact>io.grpc:protoc-gen-grpc-java:${grpc.java.version}:exe:linux-x86_64</pluginArtifact>
                </configuration>

<!--                <configuration>
                     <!-- protocol's configuration for windows-->
                    <protocArtifact>com.google.protobuf:protoc:${protobuf.version}:exe:win32-x86_64</protocArtifact>
                    <pluginId>grpc-java</pluginId>
                    <pluginArtifact>io.grpc:protoc-gen-grpc-java:${grpc.java.version}:exe:win32-x86_64</pluginArtifact>
                </configuration>-->

<!--                <configuration>
                     <!-- protocol's configuration for macOS-->
                    <protocArtifact>com.google.protobuf:protoc:${protobuf.version}:exe:osx-x86_64</protocArtifact>
                    <pluginId>grpc-java</pluginId>
                    <pluginArtifact>io.grpc:protoc-gen-grpc-java:${grpc.java.version}:exe:osx-x86_64</pluginArtifact>
                </configuration>-->
