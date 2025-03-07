FROM public.ecr.aws/amazonlinux/amazonlinux:2023

#标签
LABEL author='timandy'

#时区
ENV TIMEZONE='Asia/Shanghai'
RUN ln -snf /usr/share/zoneinfo/$TIMEZONE /etc/localtime && echo $TIMEZONE > /etc/timezone

#软件
RUN dnf update -y; \
    dnf install -y net-tools util-linux procps-ng bind-utils findutils iputils htop sudo vim tar zip wget telnet openssl nc less make git; \
    dnf clean all; \
    pwconv; \
    grpconv; \
    chmod 0744 /etc/shadow; \
    chmod 0744 /etc/gshadow;
