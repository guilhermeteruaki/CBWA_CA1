# download latest version of alpine
FROM alpine:latest 

#Install Busybox dependencies 
RUN apk add gcc musl-dev make perl

# Download busybox sources
RUN wget https://busybox.net/downloads/busybox-1.35.0.tar.bz2 \
    #extract the file
  && tar xf busybox-1.35.0.tar.bz2 \
  #move to folder
  && mv /busybox-1.35.0 /busybox \
  #remove compacted file
  && rm xf busybox-1.35.0.tar.bz2

WORKDIR /busybox

# Copy the busybox build config (limited to httpd)
COPY .config .

# Compile and install busybox
RUN make && make install