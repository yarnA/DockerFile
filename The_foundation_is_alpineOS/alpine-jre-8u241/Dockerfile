# AlpineLinux with Oracle Java 7
# Using alpine-glibc instead of alpine  is mainly because JDK relies on glibc
FROM cserver.com.cn:5000/basis/alpine-glibc
# Author
MAINTAINER YangLei (yarn2856@163.com)

# Set Java Version and other ENV
ENV JRE_HOME /usr/java/jdk1.8.0_241/
ENV PATH ${PATH}:${JRE_HOME}/bin

# A streamlined jre
ADD server-jre-8u241-linux-x64.tar.gz  /usr/java/

# do all in one step
RUN { set -ex \
     && cd ${JAVA_HOME} \
     && rm -rf COPYRIGHT \
               LICENSE \
               README.html \
               release \
               THIRDPARTYLICENSEREADME.txt \

     && echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf ; \
}
