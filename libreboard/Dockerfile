FROM phusion/baseimage:0.9.16

MAINTAINER ajjai@ajjai.in

RUN apt-get update && apt-get install -qq -y git curl
RUN useradd -m app

USER app
ENV HOME /home/app
ENV USER app

WORKDIR /home/app
RUN curl https://install.meteor.com/ | sh
RUN git clone https://github.com/libreboard/libreboard.git /home/app/libreboard

USER root
RUN ln -s /home/app/.meteor/packages/meteor-tool/1.1.3/mt-os.linux.x86_64/dev_bundle/bin/npm /usr/bin/npm && \
    ln -s /home/app/.meteor/packages/meteor-tool/1.1.3/mt-os.linux.x86_64/dev_bundle/bin/node /usr/bin/node && \
    ln -s /home/app/.meteor/meteor /usr/bin/meteor

USER app
WORKDIR /home/app/libreboard

ENTRYPOINT ["/usr/bin/meteor"]

