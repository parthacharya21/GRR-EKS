# Using Ubuntu 18.04 as the base image

FROM ubuntu:22.04


# Update the base image

RUN apt update && apt -y upgrade && apt -y dist-upgrade


# You can also install other tools into the container here.

# As an example, we'll install docker-explorer

RUN apt -y install software-properties-common

RUN add-apt-repository ppa:gift/stable && apt update

RUN apt -y install docker-explorer-tools


# Copy the GRR installation packages into the image

RUN mkdir /tmp/packages
RUN mkdir /configs
RUN mkdir /client_state

COPY "grr_3.4.7.5_amd64.deb" /tmp/packages
COPY configs /configs


# Install the package

RUN dpkg -i --no-triggers "/tmp/packages/grr_3.4.7.5_amd64.deb"




# fleetspeakd.nanny is a script to continually loop and ensure the Fleetspeak client is running

CMD ["/usr/lib/fleetspeakd/fleetspeakd.nanny","/usr/sbin/fleetspeakd","--log_dir=/var/log"]

