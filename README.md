Gradle composite builds can be useful for testing and making use of your contributions
to an open-source project before they are merged upstream, but projects that use dependency
management plugins for gradle can make it difficult to get a composite build working. Also
[Twitch4j](https://github.com/twitch4j/twitch4j) uses an environment variable to determine the version when publishing, which causes
the dependencies to not be found if the variable is not set. This template automatically
sets the environment variable on every build, and adds all dependencies of Twitch4j to
`build.gradle` so they exist in the classpath.

Note that the global "build" button in IntelliJ will try to build all of the submodules at
the same time as the main module, and it's likely that at some point during that process,
the respective gradle daemons will be trying to access the same file at the same time,
causing it to fail. If each module is built separately, it should work fine, and any run
configurations will only build the module they need.