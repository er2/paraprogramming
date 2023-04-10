#FROM mcr.microsoft.com/vscode/devcontainers/universal
FROM ubuntu:jammy

RUN apt-get update && apt-get install -y sqlite3 jq httpie curl jc sqlite-utils

RUN go install github.com/ericchiang/pup@latest