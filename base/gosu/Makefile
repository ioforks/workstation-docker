IMAGE := gosu

REPOSITORY ?= iocanel
VERSION ?= latest
USERNAME ?= iocanel
build: 
	echo "Pulling latest archlinux image..."
	docker pull archlinux:latest
	echo "Building ${IMAGE}:${VERSION}"
	sed -E "s|(FROM [a-zA-Z0-9_\-\/\:]*:)latest|\1${VERSION}|g" Dockerfile > Dockerfile.${VERSION}
	docker build --build-arg username=${USERNAME} -f Dockerfile.${VERSION} -t ${REPOSITORY}/${IMAGE}:${VERSION} .
	rm Dockerfile.${VERSION}
