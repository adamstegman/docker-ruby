FROM ubuntu:14.04
MAINTAINER Adam Stegman <astegman@gmail.com>

RUN apt-get -y update

RUN locale-gen en_US.UTF-8
RUN dpkg-reconfigure locales
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Install Ruby
RUN apt-get -y install \
      git-core wget curl zlib1g-dev build-essential python-software-properties \
      libssl-dev libreadline-dev libyaml-dev libffi-dev libcurl4-openssl-dev \
      libxml2-dev libxslt-dev
RUN cd /tmp; \
    wget http://ftp.ruby-lang.org/pub/ruby/2.2/ruby-2.2.3.tar.gz; \
    tar xf ruby-2.2.3.tar.gz; \
    cd ruby-2.2.3; \
    ./configure; \
    make; \
    make install; \
    # Allow whatever user to install gems
    chmod 777 -R /usr/local
RUN gem install bundler --no-ri --no-rdoc

# Clean up the image
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
