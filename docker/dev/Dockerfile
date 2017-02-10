FROM madforit/todobackend-base:latest
MAINTAINER Ned Lukies <ned@madforit.com.au>

RUN apt-get update && \
    apt-get install -qy python-dev libmysqlclient-dev libmysqlclient18

RUN . /appenv/bin/activate && \
    pip install wheel --upgrade

ENV WHEELHOUSE=/wheelhouse PIP_WHEEL_DIR=/wheelhouse PIP_FIND_LINKS=/wheelhouse XDG_CACHE_HOME=/cache

# OUPUT: Build artefacts (Wheels)
VOLUME /wheelhouse

VOLUME /build

# OUTPUT: Test reports are ouput here
VOLUME /reports
COPY scripts/test.sh /usr/local/bin/test.sh
RUN chmod +x /usr/local/bin/test.sh

ENTRYPOINT ["test.sh"]
CMD ["python","manage.py","test","--noinput"]

COPY src /application
WORKDIR /application
