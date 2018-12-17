FROM nginx:stable-alpine

LABEL maintainer="Harsha A Patankar"


RUN apk --update add --no-cache python3 py3-pip zip tar make bash bash-completion wget curl jq git openssl openssh-client nginx \
    && rm -rf /var/lib/apt/lists/*
RUN apk add --no-cache ca-certificates && update-ca-certificates
RUN pip3 install --upgrade pip


# Copy a configuration file from the current directory
ADD nginx.conf /etc/nginx/

RUN mkdir /etc/nginx/logs

# Add a sample index file
ADD index.html /www/data/

COPY index.html /usr/share/nginx/html/

# Append "daemon off;" to the beginning of the configuration
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

# Expose port 80 or 443 for https
EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]


