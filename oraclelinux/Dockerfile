# FROM alpine:edge
FROM oraclelinux:7-slim

MAINTAINER Tavis Aitken <tavisto@tavisto.net>

COPY ./public-yum-ol7.repo /etc/yum.repos.d/public-yum-ol7.repo
RUN curl -o /etc/yum.repos.d/dperson-neovim-epel-7.repo https://copr.fedorainfracloud.org/coprs/dperson/neovim/repo/epel-7/dperson-neovim-epel-7.repo
RUN yum install -y bash bash-completion vim neovim python3 python3-dev fzf git gcc gperf
RUN /usr/bin/pip3 install --user neovim jedi psutil setproctitle
RUN mkdir -p ~/.config/nvim
RUN git clone https://github.com/k-takata/minpac.git ~/.config/nvim/pack/minpac/opt/minpac
CMD /usr/bin/nvim
