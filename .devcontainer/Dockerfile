FROM mcr.microsoft.com/vscode/devcontainers/universal
#FROM ubuntu:jammy

RUN apt-get update && apt-get install -y sqlite3 jq httpie curl

RUN go get github.com/ericchiang/pup