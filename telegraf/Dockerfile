FROM telegraf:latest

LABEL author="Alexis Le Provost <alexis.leprovost@outlook.com>"
LABEL version="1.0.0"
LABEL description="Telegraf docker image"

USER root

RUN apt-get update && apt-get -y install build-essential hddtemp apt-utils

ADD telegraf.template.conf /telegraf.template.conf

ADD run.sh /run.sh

RUN chmod +x /*.sh

CMD ["/run.sh"]

