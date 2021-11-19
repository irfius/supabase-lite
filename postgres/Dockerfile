FROM postgres:14.1-bullseye

ENV DEPENDENCIES="postgresql-contrib git apt-utils make"

COPY ./postgres/postgres.conf /usr/share/postgresql/

RUN apt-get -y update \
    && apt-get -y upgrade \
    && apt-get -y install ${DEPENDENCIES} \
    && git clone https://github.com/michelp/pgjwt.git \
    && cd pgjwt \
    && make install \
    && cd .. \
    && rm -rf pgjwt \
    && apt-get -y autoremove ${DEPENDENCIES} 