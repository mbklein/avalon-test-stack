FROM        solr:6.2-alpine
MAINTAINER  Michael B. Klein <mbklein@gmail.com>
RUN         mkdir -p /opt/solr/server/solr/hydra
ADD         conf.tgz /opt/solr/server/solr/hydra
RUN         /opt/solr/bin/solr start && /opt/solr/bin/solr create_core -c hydra
