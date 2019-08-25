from ubuntu

RUN apt-get update \
	&& apt-get install -y libssl1.0.0:amd64 openssl \
	&& apt-get -y autoremove && apt-get -y clean

COPY ./podrocket /podrocket

RUN mkdir -p /home/podcastrs && cd /home/podcastrs \
	&& mv /podrocket . \
	&& chmod +x podrocket

RUN groupadd -r podcastrs && useradd -r -g podcastrs podcastrs \
	&& chown -R podcastrs:podcastrs /home/podcastrs

USER podcastrs

EXPOSE 8000

CMD ["/home/podcastrs/podrocket"]
