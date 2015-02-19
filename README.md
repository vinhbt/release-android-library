release-android-library
=======================

Remote script to create a maven compatible release of an android library (aar or jar) with optional dependency support.

This release comes in a zip or exploded form and is only created locally inside your own build folder. You can these use these files to release to JCenter or Maven Central.

Matching blog post: [Publish Android library to BinTray (JCenter), AAR vs. JAR and optional dependency](http://theartofdev.com/2015/02/19/publish-android-library-to-bintray-jcenter-aar-vs-jar-and-optional-dependency/), update to original blog post by Blundell: [Locally release an Android Library for JCenter or Maven Central inclusion](http://blog.blundell-apps.com/locally-release-an-android-library-for-jcenter-or-maven-central-inclusion/).

####adding to your library
```
apply plugin: 'com.android.library'

ext {
    PUBLISH_GROUP_ID = 'com.namespace'
    PUBLISH_ARTIFACT_ID = 'example-library-name'
    PUBLISH_VERSION = '1.0.0'
}

android {
    // configs, flavors etc
}

// for AAR package
apply from: 'https://raw.githubusercontent.com/ArthurHub/release-android-library/master/android-release-aar.gradle'

// or JAR package
apply from: 'https://raw.githubusercontent.com/ArthurHub/release-android-library/master/android-release-jar.gradle'

dependencies {
    // dependencies
    // optional dependencies
}
```

####useage

`./gradlew clean build generateRelease`

####example output
```
 :engine:zipRelease
 :engine:generateRelease
 Release 1.0.0 can be found at /Users/Blundell/Developer/git_repo/ExampleAndroidLibrary/build/release/1.0.0/
 Release 1.0.0 zipped can be found /Users/Blundell/Developer/git_repo/ExampleAndroidLibrary/build/release-1.0.0.zip

 BUILD SUCCESSFUL
 
 Total time: 23.609 secs
```
