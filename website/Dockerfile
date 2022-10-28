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

# Create a new user to run the website
RUN adduser -D static

# Switch to the scratch image
FROM scratch

EXPOSE 8080

# Copy over the user
COPY --from=builder /etc/passwd /etc/passwd

# Copy the busybox static binary
COPY --from=builder /busybox/_install/bin/busybox /

# Use our non-root user
USER static
WORKDIR /home/static

# Uploads a blank default httpd.conf
# This is only needed in order to set the `-c` argument in this base file
# and save the developer the need to override the CMD line in case they ever
# want to use a httpd.conf
COPY httpd.conf .

# Copy the static website
RUN wget https://github.com/guilhermeteruaki/webdev_ca2/archive/refs/heads/main.zip
RUN unzip main.zip

# Run busybox httpd
CMD ["/busybox", "httpd", "-f", "-v", "-p", "8080", "-c", "./index.html"]