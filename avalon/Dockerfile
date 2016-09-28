FROM        ruby:2.3-slim
MAINTAINER  Michael B. Klein <mbklein@gmail.com>
ENV         DEBIAN_FRONTEND=noninteractive
ADD         jessie-backports.list /etc/apt/sources.list.d/jessie-backports.list
RUN         apt-get update
RUN         apt-get install -y mediainfo sudo ffmpeg nodejs libsqlite3-dev git build-essential
RUN         useradd -G sudo -d /home/coder -m -p '' coder
USER        coder
WORKDIR     /home/coder
ENV         RAILS_ENV=test
ENV         AVALON_BRANCH=develop
RUN         git clone https://github.com/avalonmediasystem/avalon.git
RUN         cd avalon && git checkout develop && bundle install --without development:production
RUN         for f in avalon/config/*.example; do mv $f ${f%%.example}; done
ADD         env.test /home/coder/avalon/.env.test
WORKDIR     /home/coder/avalon
CMD         git fetch origin && \
            git checkout $AVALON_BRANCH && \
            git pull origin $AVALON_BRANCH && \
            bundle install && \
            rake db:migrate && \
            rspec -c -fp --order=random:$RANDOM spec
