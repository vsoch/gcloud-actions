FROM gcr.io/cloud-builders/gsutil@sha256:4ef6a16978684fb174b7ab1fd6237a8d5f1ce98e2242a90444057f228f5112dc

LABEL "name"="gsutil"
LABEL "version"="1.0.0"
LABEL "maintainer"="GitHub Actions <support+actions@github.com>"

LABEL "com.github.actions.name"="GitHub Action for Google Storage Utility"
LABEL "com.github.actions.description"="Wraps the gsutil command for Google Storage."
LABEL "com.github.actions.icon"="upload-cloud"
LABEL "com.github.actions.color"="blue"
COPY LICENSE README.md THIRD_PARTY_NOTICE.md /

ENV DOCKERVERSION=18.06.1-ce
RUN apt-get update && apt-get -y --no-install-recommends install curl \
  && curl -fsSLO https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKERVERSION}.tgz \
  && tar xzvf docker-${DOCKERVERSION}.tgz --strip 1 \
                 -C /usr/local/bin docker/docker \
  && rm docker-${DOCKERVERSION}.tgz \
  && rm -rf /var/lib/apt/lists/*

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
