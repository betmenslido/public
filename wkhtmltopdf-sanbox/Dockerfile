FROM surnet/alpine-wkhtmltopdf:3.15.0-0.12.6-small

RUN \
  apk update && \
  apk upgrade && \
  apk add bash imagemagick && \
  rm -rf /var/cache/apk/*

WORKDIR /otherdir

ENTRYPOINT []

CMD ["/bin/wkhtmltopdf", "--enable-local-file-access", "/workdir/index.html", "/workdir/output.pdf"]
