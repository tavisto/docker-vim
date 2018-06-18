FROM ubuntu:18.04

MAINTAINER Tavis Aitken <tavisto@tavisto.net>
# Update and install


RUN apt-get update && apt-get install -y \
      ack-grep \
      bash \
      ctags \
      curl \
      git \
      htop \
      libffi-dev \
      libssl-dev \
      locales \
      netcat \
      python3-dev \
      python3-pip \
      ranger \
      shellcheck \
      software-properties-common \
      sudo \
      sqlite3 \
      tree \
      wget


# Install Neovim
RUN add-apt-repository ppa:neovim-ppa/stable
RUN apt-get update && apt-get install -y neovim

RUN /usr/bin/pip3 install --user neovim \
      jedi \
      psutil \
      setproctitle \
      flake8 \
      flake8-docstrings \
      flake8-isort \
      flake8-quotes

RUN useradd -m tron
USER tron
WORKDIR /home/tron
RUN git clone https://github.com/tavisto/nvim-configs.git .config/nvim
RUN mkdir -p .config/nvim/pack/minpac/opt
RUN git clone https://github.com/k-takata/minpac.git .config/nvim/pack/minpac/opt/minpac
RUN /usr/bin/nvim -c PackUpdate -c exit

RUN git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install

CMD /usr/bin/nvim
