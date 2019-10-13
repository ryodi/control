IMAGES := $(patsubst %/Dockerfile,%,$(shell find . -type f -name Dockerfile))

default:
	for img in $(IMAGES); do (cd $$img; make); done

release:
	@echo "Checking that VERSION was defined in the calling environment"
	@test -n "$(VERSION)"
	@echo "OK.  VERSION=$(VERSION)"
	for img in $(IMAGES); do (cd $$img; make release VERSION=$(VERSION)); done
