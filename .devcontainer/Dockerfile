FROM ubuntu:kinetic

ENV TZ="America/New_York"
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y sqlite3 jq httpie curl jc sqlite-utils golang wamerican libxml-xpath-perl

RUN go install github.com/ericchiang/pup@latest

# RUN snap install yq
