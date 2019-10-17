# Dependency failing: io.perfmark:perfmark-api:0.16.0 -> com.google.errorprone:error_prone_annotations@[2.3.2,2.3.3], but error_prone_annotations version was 2.3.2.


![error-grpc](/assets/images/error-grpc.png)

## Error:

```powershell
In project 'app' a resolved Google Play services library dependency depends on another at an exact version (e.g. "[2.3.2
,2.3.3]", but isn't being resolved to that version. Behavior exhibited by the library will be unknown.

Dependency failing: io.perfmark:perfmark-api:0.16.0 -> com.google.errorprone:error_prone_annotations@[2.3.2,2.3.3], but 
error_prone_annotations version was 2.3.2.

The following dependencies are project dependencies that are direct or have transitive dependencies that lead to the art
ifact with the issue.
-- Project 'app' depends onto io.grpc:grpc-api@{strictly 1.22.1}
-- Project 'app' depends onto io.grpc:grpc-protobuf-lite@1.22.1
-- Project 'app' depends onto io.perfmark:perfmark-api@{strictly 0.16.0}
-- Project 'app' depends onto io.grpc:grpc-okhttp@1.22.1
-- Project 'app' depends onto io.grpc:grpc-stub@{strictly 1.22.1}
-- Project 'app' depends onto io.grpc:grpc-core@{strictly 1.22.1}
-- Project 'app' depends onto io.grpc:grpc-okhttp@{strictly 1.22.1}
-- Project 'app' depends onto io.grpc:grpc-protobuf-lite@{strictly 1.22.1}
-- Project 'app' depends onto io.grpc:grpc-stub@1.22.1
-- Project 'app' depends onto com.google.errorprone:error_prone_annotations@{strictly 2.3.2}

For extended debugging info execute Gradle from the command line with ./gradlew --info :app:assembleDebug to see the dep
endency paths to the artifact. This error message came from the google-services Gradle plugin, report issues at https://
github.com/google/play-services-plugins and disable by adding "googleServices { disableVersionCheck = false }" to your b
uild.gradle file.
```

## Solution: 

```java
    // app > build.gradle
    // in dependencies
    implementation ("io.grpc:grpc-okhttp:$grpc_version") {
        exclude group: 'io.perfmark', module: 'perfmark-api'
    }
    implementation ("io.grpc:grpc-protobuf-lite:$grpc_version") {
        exclude group: 'io.perfmark', module: 'perfmark-api'
    }
    implementation ("io.grpc:grpc-stub:$grpc_version") {
        exclude group: 'io.perfmark', module: 'perfmark-api'
    }
    implementation ('io.perfmark:perfmark-api:0.16.0') {
        exclude group: 'com.google.errorprone', module: 'error_prone_annotations'
    }
```