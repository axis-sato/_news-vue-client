FROM node:6.10

LABEL maintainer="c8112002"

# Upgrade global npm packages
#RUN npm update -g npm \
#&& npm update -g

WORKDIR /app/news

COPY ./docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
