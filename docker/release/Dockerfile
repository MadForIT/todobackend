FROM madforit/todobackend-base:latest
MAINTAINER Ned Lukies <ned@madforit.com.au>

COPY target /wheelhouse

RUN . /appenv/bin/activate && \
  pip install --no-index -f /wheelhouse todobackend && \
  rm -rf /wheelhouse
