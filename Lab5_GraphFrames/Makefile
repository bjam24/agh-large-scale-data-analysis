REPO_NAME=graphframes-spark
PREFIX=adzd

all: push

container: image

image:
	docker build -t $(PREFIX)/$(REPO_NAME) .

run:
	docker run --rm -p 8888:8888 -v $(PWD):/work --name graphframes-notebook $(PREFIX)/$(REPO_NAME):latest start-notebook.sh --ip='*' --NotebookApp.token='' --NotebookApp.password=''

clean:

