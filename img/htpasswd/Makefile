IMAGE      := ryodi/htpasswd
BUILDDATE  ?= $(shell date +%Y%m%d.%H%M%S)

BUILDOPTS  := --build-arg builddate=$(BUILDDATE)
BUILDOPTS  += --build-arg repository=https://github.com/ryodi/control
BUILDOPTS  += --build-arg commitish=$(shell ../../util/commitish)

default: build

build:
	docker build --build-arg version=dev $(BUILDOPTS) -t $(IMAGE):latest .

release:
	@echo "Checking that VERSION was defined in the calling environment"
	@test -n "$(VERSION)"
	@echo "OK.  VERSION=$(VERSION)"

	docker build --build-arg version=$(VERSION) $(BUILDOPTS) -t $(IMAGE):latest -t $(IMAGE):$(VERSION) .
	docker tag  $(IMAGE):latest $(IMAGE):$(VERSION)
	docker push $(IMAGE):latest
	docker push $(IMAGE):$(VERSION)
