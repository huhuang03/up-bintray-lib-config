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
add plugin `android-maven, bintray`, add below lines at top of you lib's build.gralde, blow `apply plugin: 'com.android.library'`
```java
apply plugin: 'com.github.dcendents.android-maven'
apply plugin: 'com.jfrog.bintray
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

import `config.gradle` to you lib's `build.gradle`
```java
apply from: 'https://raw.githubusercontent.com/huhuang03/up-bintray-lib-config/master/config.gradle'
```

replace common info in `config.gradle` file, you just need do this once

## Demo
look 'demo.gradle'
