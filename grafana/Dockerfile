FROM grafana/grafana:7.3.1-ubuntu
# docker pull grafana/grafana:7.3.1
# FROM grafana/grafana@sha256:afa843fff79a379520c074d51358582f7a5e83b7b6ccda0086abdf6a43137568

LABEL author="Marijani Hussein Karanda <marijani.karanda@eganet.go.tz>"
LABEL version="latest"
LABEL description="Grafana docker image for mikutano"

USER root

RUN echo "kwioo"

RUN apt-get -q update &&\
    DEBIAN_FRONTEND="noninteractive" apt-get -q upgrade -y -o Dpkg::Options::="--force-confnew" --no-install-recommends &&\
    DEBIAN_FRONTEND="noninteractive" apt-get -q install -y -o Dpkg::Options::="--force-confnew" --no-install-recommends curl gosu nano &&\
    apt-get -q autoremove &&\
    apt-get -q clean -y && rm -rf /var/lib/apt/lists/* && rm -f /var/cache/apt/*.bin

ADD run.sh /run.sh
RUN chmod +x /run.sh
RUN mkdir -p /opt/grafana/dashboards
ADD ["*.json", "/opt/grafana/dashboards/"]
ADD ["default-dashboard.yaml", "/etc/grafana/provisioning/dashboards/"]
ADD ["newindex.html","/usr/share/grafana/public/views"]
CMD ["/run.sh"]
