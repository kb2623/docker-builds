NAME:=neovide-dbuild
PATH_FILE:=/usr/local/bin
OUT_FILE:=neovide

all:
	make build
	make copy

build:
	docker build -t $(NAME) .
	
xorgHosts:
	xhost +

run: xorgHosts
	docker run --rm -it \
		-e DISPLAY=$(DISPLAY) \
		-v /tmp/.X11-unix:/tmp/.X11-unix:rw \
		--net=host \
		--device=/dev/dri \
		--device=/dev/snd \
		$(NAME)
	
copy:
	docker cp $(shell docker create --rm $(NAME)):$(PATH_FILE)/$(OUT_FILE) $(OUT_FILE)
	
clean:
	docker rmi $(NAME)
