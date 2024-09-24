FROM python:3-alpine

RUN apk add --no-cache \
	bash

RUN set -x \
	&& apk add --no-cache --virtual .build-deps \
		build-base \
		libffi-dev \
		openssl-dev \
	&& pip install --upgrade \
		--pre azure-cli \
		--no-cache-dir \
	&& apk del .build-deps

ENTRYPOINT	[ "az" ]

CMD ["version"]