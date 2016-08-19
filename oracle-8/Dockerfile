FROM ubuntu:14.04

MAINTAINER Ian Young <ian@iay.org.uk>

#
# Install Oracle Java 8 JDK via the wedupd8team PPA
#
# Run everything together and clean up after ourselves to avoid
# making many intermediate layers in the resulting image.
#
# The Oracle license prompt is auto-accepted.
#
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:webupd8team/java && \
    apt-get update && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
    apt-get install -y oracle-java8-installer && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /var/cache/oracle-jdk8-installer

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

#
# Unlimited Strength Jurisdiction Policy Files
#
# Step 1: test whether the policies are in effect (expect no).
#
WORKDIR /data
ADD Test.java /data/Test.java
RUN javac Test.java && java Test && rm Test.class

#
# Step 2: Apply the policy files by overwriting the default files.
#
ADD UnlimitedJCEPolicyJDK8/local_policy.jar ${JAVA_HOME}/jre/lib/security/
ADD UnlimitedJCEPolicyJDK8/US_export_policy.jar ${JAVA_HOME}/jre/lib/security/

#
# Step 3: re-test whether the policies are in effect.
#
RUN javac Test.java && java Test && rm Test.class
