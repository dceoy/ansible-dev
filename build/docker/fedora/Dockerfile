FROM fedora

RUN set -e \
      && dnf -y upgrade \
      && dnf -y install git redhat-rpm-config gcc sudo openssh openssl-devel python-devel python-pip python2-dnf \
      && dnf clean all

RUN set -e \
      && pip install -U pip \
      && pip install -U ansible

RUN set -e \
      && git clone https://github.com/dceoy/ansible-dev.git \
      && cp -a ansible-dev/build/playbooks /tmp \
      && cp -a ansible-dev/roles /tmp/playbooks \
      && cd /tmp/playbooks \
      && ansible-playbook provision_container.yml

ENTRYPOINT ["/usr/bin/zsh", "-lc"]