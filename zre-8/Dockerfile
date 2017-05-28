FROM frolvlad/alpine-glibc:alpine-3.6

RUN ZULU_VERSION="8.21.0.1-jdk8.0.131" \
 && ZULU_ARCHIVE_NAME="zulu${ZULU_VERSION}-linux_x64" \
 && apk update \
 && apk upgrade --no-cache \
 && apk add --no-cache \
            --virtual=.build-dependencies \
            ca-certificates \
            curl \
 && curl -fSL \
         "https://cdn.azul.com/zulu/bin/${ZULU_ARCHIVE_NAME}.tar.gz" \
         -o "/tmp/${ZULU_ARCHIVE_NAME}.tar.gz" \
 && mkdir -p /opt \
 && tar xzf "/tmp/${ZULU_ARCHIVE_NAME}.tar.gz" -C /opt \
 && rm -f "/tmp/${ZULU_ARCHIVE_NAME}.tar.gz" \
 && mv "/opt/${ZULU_ARCHIVE_NAME}" /opt/zulu \
 && chown -R root:root /opt/zulu \
 && rm -rf /opt/zulu/ASSEMBLY_EXCEPTION \
           /opt/zulu/bin \
           /opt/zulu/demo \
           /opt/zulu/include \
           /opt/zulu/lib \
           /opt/zulu/LICENSE \
           /opt/zulu/man \
           /opt/zulu/sample \
           /opt/zulu/src.zip \
           /opt/zulu/THIRD_PARTY_README \
 && mv -f /opt/zulu/jre/* /opt/zulu/ \
 && rmdir /opt/zulu/jre \
 && echo 'export JAVA_HOME=/opt/zulu' > /etc/profile.d/zulu.sh \
 && echo 'export PATH=$PATH:$JAVA_HOME/bin' >> /etc/profile.d/zulu.sh \
 && apk del .build-dependencies \
 && rm -f /var/cache/apk/*.tar.gz

ENV JAVA_HOME /opt/zulu
ENV PATH ${PATH}:${JAVA_HOME}/bin
