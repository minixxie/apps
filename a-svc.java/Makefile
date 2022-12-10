.PHONY: build
build:
	mvn package -Dmaven.test.skip=true

.PHONY: run
run:
	java -jar target/demo-latest.jar

.PHONY: docker-build
docker-build:
	DOCKER_BUILDKIT=1 docker build . -t a-svc:dont_push
