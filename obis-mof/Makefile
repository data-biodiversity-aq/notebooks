## ---------------------------------------------------------------------------------
## Documentation
## Prerequisite: Docker (https://www.docker.com/)
## The notebook uses jupyer-docker-stacks 
## 		(https://jupyter-docker-stacks.readthedocs.io/en/latest/using/common.html)
## ---------------------------------------------------------------------------------

.PHONY: help docker_image docker_run

help:
# https://stackoverflow.com/questions/8889035/how-to-document-a-makefile
		@sed -ne '/@sed/!s/## //p' $(MAKEFILE_LIST)

# Variables for docker command
DEV_IMAGE:=jupyter/robis-mof
CURRENT_DIR:=$(notdir $(patsubst %/,%,$(dir $(mkfile_path))))
WORKDIR:=/work/


docker_image: 	## Build docker image.
	@docker build -f Dockerfile -t $(DEV_IMAGE) .

docker_run: 	## Run a docker image. Run `make docker_image` first.
	@docker run -it --rm \
	--name robis-mof \
	-p 8888:8888 \
	-w  $(WORKDIR) \
	-v $(PWD):$(WORKDIR) \
	$(DEV_IMAGE) bash -c 'jupyter notebook'
