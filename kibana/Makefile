.SILENT:
.DEFAULT_GOAL := help

COLOR_RESET = \033[0m
COLOR_COMMAND = \033[36m
COLOR_YELLOW = \033[33m
COLOR_GREEN = \033[32m
COLOR_RED = \033[31m

PROJECT := Kibana

## Installs service environment
install: deploy

## Install service kibana using helm install
deploy:
	helm install prd-kibana ../kibana/ -f values.yaml --namespace logging
	
## Update config service kibana
update:
	printf "update"

## Remove service kibana 
delete:
	helm delete prd-kibana


## Prints help message
help:
	printf "\n${COLOR_YELLOW}${PROJECT}\n------\n${COLOR_RESET}"
	awk '/^[a-zA-Z\-\_0-9\.%]+:/ { \
                helpMessage = match(lastLine, /^## (.*)/); \
                if (helpMessage) { \
                        helpCommand = substr($$1, 0, index($$1, ":")); \
                        helpMessage = substr(lastLine, RSTART + 3, RLENGTH); \
                        printf "${COLOR_COMMAND}$$ make %s${COLOR_RESET} %s\n", helpCommand, helpMessage; \
                } \
        } \
        { lastLine = $$0 }' $(MAKEFILE_LIST) | sort
	printf "\n"

