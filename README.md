# java-docker
Docker base images for Java projects.

Most of my Java projects are based on the official
[`java`](https://registry.hub.docker.com/_/java/) images, which in turn
are based on Debian Jessie and OpenJDK.

Sometimes they are not what I want, however, and this repository contains
Docker image builds for some alternatives.

* `oracle-8` builds `iay/java:oracle-8`, an Oracle Java 8 JDK hosted on
Ubuntu 14.04 LTS as a replacement for the now defunct
`dockerfile/java:oracle-java8`. This variant includes
the Unlimited Strength Jurisdiction Policy Files, allowing the use
of algorithms such as AES with a 256-bit key.

**Note:** Oracle's licensing no longer allows the redistribution of their JDK,
so I will not be pushing built images to any public repositories. If you want
to use these images in your own projects, you will need to build them
yourself; this may involve manually downloading components and accepting the
associated licenses. Build instructions can be found in each subdirectory.
