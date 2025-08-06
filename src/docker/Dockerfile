FROM ubuntu:24.04

# To make it easier for build and release pipelines to run apt-get,
# configure apt to not require confirmation (assume the -y argument by default)
ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes
RUN apt-get update &&\
    apt-get install -y --no-install-recommends \
        ca-certificates \
        curl
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc  && \
    chmod a+r /etc/apt/keyrings/docker.asc && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null 

RUN curl -fsSL https://deb.nodesource.com/setup_22.x | sh -
RUN apt-get update \
&& apt-get install -y --no-install-recommends \
        ca-certificates \
        jq \
        git \
	      libicu74 \
        libkrb5-3 \
        zlib1g \
        debsums \
        iputils-ping \
        libcurl4 \
        libunwind8 \
        netcat-traditional \
        libssl1.0 \
        docker-ce \
        docker-ce-cli \
        containerd.io \
        docker-buildx-plugin \
	      zip \
        unzip \
        jq \
        net-tools \
        nodejs \
        python3-full \
        python3-kubernetes \
        python3-pip \
&& rm -rf /var/lib/apt/lists/*

RUN curl -LsS https://aka.ms/InstallAzureCLIDeb | bash \
  && rm -rf /var/lib/apt/lists/* && az aks install-cli

RUN node -v && npm -v
WORKDIR /app

RUN npx playwright install --with-deps && \
    npm install -D @playwright/test && \
    npm i create-playwright --quiet --with-deps && \
    npm install -g @usebruno/cli && \
    npm install -g dotenv-cli && \
    npm install -D typescript && \
    npm install --save @types/node

WORKDIR /azp

COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]





