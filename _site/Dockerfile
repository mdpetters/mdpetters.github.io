FROM docker.io/library/debian:stable

USER root

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get -y install locales locales-all fish vim ruby ruby-all-dev git make gcc g++ texlive

RUN touch /etc/localtime

RUN gem install bundler

CMD /usr/bin/fish
