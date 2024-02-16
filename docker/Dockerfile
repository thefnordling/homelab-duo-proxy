FROM ubuntu:22 as build-env
RUN apt-get update && apt-get install build-essential libffi-dev perl zlib1g-dev wget -y
RUN wget https://dl.duosecurity.com/duoauthproxy-latest-src.tgz && \
    tar xzf duoauthproxy-latest-src.tgz && \
    cd "$(tar tfz duoauthproxy-latest-src.tgz | head -n 1 | cut -f1)" && \
    make && \
    mkdir /duo-proxy \
    install --install-dir /duo-proxy --service-user duo_authproxy_svc --log-group duo_authproxy_grp --create-init-script yes

tar tfz duoauthproxy-latest-src.tgz | head -n 1 | cut -f1