# `iay/java:oracle-8`

## Archived Project

I've stopped using this project because the Ubuntu PPA (Personal Package
Archive) on which it depended is no longer available.

Java distributions are a lot better in general than when I needed this; now
I'm generally content to use any OpenJDK release, with a preference to use
[Amazon Corretto](https://aws.amazon.com/corretto/) when possible.

## Previous Text

This Docker image includes an Oracle Java 8 JDK built on the official Docker
[`ubuntu:16.04`](https://registry.hub.docker.com/_/ubuntu/) image. It also includes
the [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files]
(http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)
to allow the use of algorithms such as AES with 256-bit keys. These capabilities are
included in OpenJDK runtimes by default; this just brings the Oracle JDK up to the
same level.

The `Dockerfile` assumes you have the policy files available:

* Download `jce_policy-8.zip` [from Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).
You will need to accept their license agreement to do this.
* `unzip jce_policy-8.zip` will generate the `UnlimitedJCEPolicyJDK8`
directory assumed by the `Dockerfile`.

Run `./build` to build the image.

During the build, you will see `Test.java` being executed twice to verify the
state of the cryptographic policy in use. Before the policy files have
been updated, you should see this:

    AES with 128-bit key OK.
    AES with 256-bit key not permitted.
    SHA-256 algorithm is present.

Afterwards, the output should look like this instead:

    AES with 128-bit key OK.
    AES with 256-bit key OK.
    SHA-256 algorithm is present.

You can always compile and execute `/data/Test.java` in a container to verify
the final state.
