FROM tomcat:9
LABEL godasisatish "godasisatish"
ENV PATH /docker-java-home/bin:$PATH
# Layer: base
RUN \
  apt update -qq && \
  apt autoremove openjdk* -y && \
  apt install wget -y && \
  echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections && \
  echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" > /etc/apt/sources.list.d/webupd8team-java-trusty.list && \
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886 && \
  apt-get update -y && \
  apt-get install -y oracle-java8-installer oracle-java8-set-default && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /docker-java-home && \
  mv /usr/lib/jvm/java-8-oracle /docker-java-home
EXPOSE 8080
CMD ["catalina.sh", "run"]

