# `iay/java:oracle-8`

This Docker image includes an Oracle Java 8 JDK built on the official Docker
[`ubuntu:14.04`](https://registry.hub.docker.com/_/ubuntu/) image. It also includes
the [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files]
(http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)
to allow the use of algorithms such as AES with 256-bit keys. These capabilities are
included in OpenJDK runtimes by default; this just brings the Oracle JDK up to the
same level.

The `Dockerfile` assumes you have the policy files available:

* Download `jce_policy-8.zip` [from Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).
You will need to accept their license agreement to do this.
* `gunzip jce_policy-8.zip` will generate the `UnlimitedJCEPolicyJDK8`
directory assumed by the `Dockerfile`.

Run `./build` to build the image.
