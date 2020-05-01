# AlpineLinux with Oracle Java 7
# Using alpine-glibc instead of alpine  is mainly because JDK relies on glibc
FROM cserver.com.cn:5000/basis/alpine-glibc
# Author
MAINTAINER YangLei (yarn2856@163.com)

# Set Java Version and other ENV
ENV JRE_HOME /usr/java/jre1.7.0_80/
ENV PATH ${PATH}:${JRE_HOME}/bin

# A streamlined jre
ADD jre-7u80-linux-x64.tar.gz  /usr/java/

# do all in one step
RUN { set -ex \
     && cd ${JAVA_HOME} \
     && rm -rf COPYRIGHT \
               LICENSE \
               README \
               release \
               THIRDPARTYLICENSEREADME-JAVAFX.txt \
               THIRDPARTYLICENSEREADME.txt \
               Welcome.html \

               lib/plugin.jar \
               lib/ext/jfxrt.jar \
               bin/javaws \
               lib/javaws.jar \
               lib/desktop \
               plugin \
               lib/deploy* \
               lib/*javafx* \
               lib/*jfx* \
               lib/amd64/libdecora_sse.so \
               lib/amd64/libprism_*.so \
               lib/amd64/libfxplugins.so \
               lib/amd64/libglass.so \
               lib/amd64/libgstreamer-lite.so \
               lib/amd64/libjavafx*.so \
               lib/amd64/libjfx*.so \
     && echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf ; \
}
