# homelab-duo-proxy
i use freeipa to provide identity services in my homelab.   I am hoping to use duo for mfa/2fa in the homelab, this will be a containerized build of the duo auth proxy

# installation

summarized from [the duo docs](https://duo.com/docs/authproxy-reference#installation)

```
sudo /bin/bash
apt-get update && apt-get install build-essential libffi-dev perl zlib1g-dev wget -y
mkdir duo-build
cd duo-build
wget https://dl.duosecurity.com/duoauthproxy-latest-src.tgz 
tar xzf duoauthproxy-latest-src.tgz 
cd "$(tar tfz duoauthproxy-latest-src.tgz | head -n 1 | cut -f1)"
make
./duoauthproxy-build/install --install-dir /opt/duoauthproxy --service-user duo_authproxy_svc --log-group duo_authproxy_grp --create-init-script yes
```

configure the proxy by editing `/opt/duoauthproxy/conf/authproxy.cfg`

