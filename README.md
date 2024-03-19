# Maven GitHub Package

- requires
```
plugins {
    id 'java'
    id 'maven-publish' < MAVEN PUBLSIH
}

group = 'com.brendenvogt'
version = '1.1' < VERISION BUMP

...

publishing { < THIS WHOLE BLOCK
    repositories {
        maven {
            name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/brendenvogt/TestJavaPackageGradle")
            credentials {
                username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
                password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
            }
        }
    }
    publications {
        gpr(MavenPublication) {
            from(components.java)
        }
    }
}
```