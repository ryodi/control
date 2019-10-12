IMAGE := ryodi/traefik-cert-dumper

default: build

build:
	docker build -t $(IMAGE):latest .

release:
	@echo "Checking that VERSION was defined in the calling environment"
	@test -n "$(VERSION)"
	@echo "OK.  VERSION=$(VERSION)"

	sed -i -e 's/^version=.*/version=$(VERSION)/' overlay/bin/ryodi-go
	docker build -t $(IMAGE):latest -t $(IMAGE):$(VERSION) .
	docker tag  $(IMAGE):latest $(IMAGE):$(VERSION)
	docker push $(IMAGE):latest
	docker push $(IMAGE):$(VERSION)
