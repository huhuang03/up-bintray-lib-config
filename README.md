## Purpose
To upload a lib to jcenter is complex, after google it's a way to do this but need complex config.
```java
apply plugin: 'com.github.dcendens.android-maven'
apply plugin: 'com.jfrog.bintray'
```
In my opinion, we just config our common info like userSite name etc once. And config three property to each project
```html
group: group
module: module
version: verison

(option)
desc: A lib's desc
svcUrl: source version control url
```

## Usage
set user apikey in local.property

```
bintray.apikey=apikey on bintray
bintray.user=user in bintray
```

add this in your top `build.gradle`, in `buildscript{ dependencies {} }` closure
```gradle
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'
classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7'
````

add plugin `android-maven, bintray`, add below lines at top of you lib's build.gralde, blow `apply plugin: 'com.android.library'`
```java
apply plugin: 'com.github.dcendents.android-maven'
apply plugin: 'com.jfrog.bintray'
```

config `group module version` in your lib's build.gradle

```java
ext {
  group = "com.tonghu.view"
  module = "badgeContainer"
  version = "1.0.1"
}
```

(option) config the `desc url` if you want
```java
ext {
  desc: "A desc"
  svcUrl: "github url"
}
```

replace common info in `config.gradle` file, you just need do this once

import `config.gradle` to you lib's `build.gradle`, you should use your config
```java
apply form: file_location_of_your_modified_config.gradle
```

or 
```
apply from: 'https://raw.githubusercontent.com/huhuang03/up-bintray-lib-config/master/config.gradle'

```


## Demo
look `demo.gradle`
