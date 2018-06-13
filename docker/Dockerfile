FROM ubuntu:16.04
MAINTAINER guro
ENV DEBCONF_NOWARNINGS yes
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get clean
RUN apt-get update -y
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install git make build-essential python-dev python-pip libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libglib2.0-0 libfontconfig1 libxrender1 libsm6 libxext6 vim curl
ENV PYTHONIOENCODING "utf-8"

ENV HOME  /
ENV PYENV_ROOT $HOME/.pyenv
ENV PATH $PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH
RUN git clone https://github.com/yyuu/pyenv.git .pyenv
RUN pyenv install 3.6.3
RUN pyenv global 3.6.3

COPY . /app
WORKDIR /app
RUN pip install -r /app/requirements.txt
ENTRYPOINT ["python", "main.py"]
