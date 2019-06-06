FROM nginx:latest

RUN apt-get update \
	&& apt-get install curl sudo git -y \
	&& rm -rf /var/log/nginx/*.log \
	&& touch /var/log/nginx/access.log \
	&& touch /var/log/nginx/error.log

ADD ./start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh
CMD [ "/usr/local/bin/start.sh" ]
