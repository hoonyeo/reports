# iOS에서 안드로이드 설정하기
 이 문서는 Markdown 형식으로 작성하였습니다.
## sdkmanager 필수 설치 사항.
```
@] sdkmanager —list
extras;android;m2repository       | 47.0.0       | Android Support Repository       
extras;google;google_play_services | 39           | Google Play services             
extras;google;m2repository        | 46           | Google Repository

platforms;android-xx                
```

## 빌드 시 cordova-plugin-crosswalk-webview 오류
### gradle 버전오류
Platforms/android/cordova/lib//builders/GradleBuilder.js의
 distributionUrl을 cradle-2.13-all.zip으로 변경하거나
 환경변수에 CORDOVA_ANDROID_GRADLE_DISTRIBUTION_URL 변수에 ‘http://services.gradle.org/distributions/gradle-2.13-all.zip’으로 설정.

### build 오류
```
org.xwalk:xwalk_core_library:20+
Incremental java compilation is an incubating feature.

FAILURE: Build failed with an exception.

* What went wrong:
A problem occurred configuring root project 'android'.
> Could not resolve all dependencies for configuration ':_armv7DebugCompile'.
   > Could not find com.android.support:multidex:1.0.1.
     Searched in the following locations:
         https://repo1.maven.org/maven2/com/android/support/multidex/1.0.1/multidex-1.0.1.pom
         https://repo1.maven.org/maven2/com/android/support/multidex/1.0.1/multidex-1.0.1.jar
         https://jcenter.bintray.com/com/android/support/multidex/1.0.1/multidex-1.0.1.pom
         https://jcenter.bintray.com/com/android/support/multidex/1.0.1/multidex-1.0.1.jar
         file:/Users/hoonyeo/git/mip-cusup-ui/platforms/android/libs/multidex-1.0.1.jar
         file:/Users/hoonyeo/git/mip-cusup-ui/platforms/android/libs/multidex.jar
         file:/var/root/.m2/repository/com/android/support/multidex/1.0.1/multidex-1.0.1.pom
         file:/var/root/.m2/repository/com/android/support/multidex/1.0.1/multidex-1.0.1.jar
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/multidex/1.0.1/multidex-1.0.1.pom
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/multidex/1.0.1/multidex-1.0.1.jar
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/multidex/1.0.1/multidex-1.0.1.pom
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/multidex/1.0.1/multidex-1.0.1.jar
     Required by:
         :android:unspecified
   > Could not find any matches for com.android.support:support-v4:[13.0.0,) as no versions of com.android.support:support-v4 are available.
     Searched in the following locations:
         https://repo1.maven.org/maven2/com/android/support/support-v4/maven-metadata.xml
         https://repo1.maven.org/maven2/com/android/support/support-v4/
         https://jcenter.bintray.com/com/android/support/support-v4/maven-metadata.xml
         https://jcenter.bintray.com/com/android/support/support-v4/
         file:/Users/hoonyeo/git/mip-cusup-ui/platforms/android/libs/
         file:/var/root/.m2/repository/com/android/support/support-v4/maven-metadata.xml
         file:/var/root/.m2/repository/com/android/support/support-v4/
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/support-v4/maven-metadata.xml
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/support-v4/
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/support-v4/maven-metadata.xml
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/support-v4/
     Required by:
         :android:unspecified > org.xwalk:xwalk_core_library:20.50.533.12
   > Could not find com.android.support:support-v4:23.0.0.
     Searched in the following locations:
         https://repo1.maven.org/maven2/com/android/support/support-v4/23.0.0/support-v4-23.0.0.pom
         https://repo1.maven.org/maven2/com/android/support/support-v4/23.0.0/support-v4-23.0.0.aar
         https://jcenter.bintray.com/com/android/support/support-v4/23.0.0/support-v4-23.0.0.pom
         https://jcenter.bintray.com/com/android/support/support-v4/23.0.0/support-v4-23.0.0.aar
         file:/Users/hoonyeo/git/mip-cusup-ui/platforms/android/libs/support-v4-23.0.0.aar
         file:/Users/hoonyeo/git/mip-cusup-ui/platforms/android/libs/support-v4.aar
         file:/var/root/.m2/repository/com/android/support/support-v4/23.0.0/support-v4-23.0.0.pom
         file:/var/root/.m2/repository/com/android/support/support-v4/23.0.0/support-v4-23.0.0.aar
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/support-v4/23.0.0/support-v4-23.0.0.pom
         https://download.01.org/crosswalk/releases/crosswalk/android/maven2/com/android/support/support-v4/23.0.0/support-v4-23.0.0.aar
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/support-v4/23.0.0/support-v4-23.0.0.pom
         file:/usr/local/Caskroom/android-sdk/25.2.3/extras/google/m2repository/com/android/support/support-v4/23.0.0/support-v4-23.0.0.aar
     Required by:
         :android:unspecified > com.google.android.gms:play-services-location:9.2.0 > com.google.android.gms:play-services-basement:9.2.0
```
Sdkmanager “extras;android;m2repository” 설치


## iOS 빌드 시 android 명령 deprecated 처리내역
```
hoonyeo@/Users/hoonyeo/git/mip-cusup-ui/platforms/android]android list target --compact
*************************************************************************
The "android" command is deprecated.
For manual SDK, AVD, and project management, please use Android Studio.
For command-line tools, use tools/bin/sdkmanager and tools/bin/avdmanager
*************************************************************************
Running /usr/local/Caskroom/android-sdk/25.2.3/tools/bin/avdmanager list target --compact
```
 따라서, /Users/hoonyeo/git/mip-cusup-ui/platforms/android/cordova/lib/check_reqs.js 파일안에 android list target —compact를 svdmanager list target —compact
