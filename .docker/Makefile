VERSION := 0.1.0
PREFIX  := xaptum/xtt-cpp

.DEFAULT_GOAL := all

all:
	$(MAKE) build && $(MAKE) release

pull: Dockerfile
	docker pull $(PREFIX):$(VERSION)

build: Dockerfile
	docker build --rm --force-rm -t $(PREFIX):$(VERSION) .

release: Dockerfile
	@if ! docker images $(PREFIX) | awk '{ print $$2 }' | grep -q -F $(VERSION); then echo "$< version $(VERSION) is not yet built. Please run 'make build'"; false; fi
	@docker push $(PREFIX):$(VERSION)
