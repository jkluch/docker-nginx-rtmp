# docker-nginx-rtmp
Refer to alfg/docker-nginx-rtmp for more info on this image, read below for differences

# Why the fork?
* The cuda varient is way heavier than it needs to be, at least for my use cases.
* I don't want the nginx config to live inside the container, I want to be able to modify it on disk and have the container read in the config I set

# What you need to do differently.
The only difference really is that Dockerfile.cuda no longer uses the entrypoint.cuda.sh script and on launch the image copies an `nginx.conf` file from `/config/nginx.conf` and puts it at `/etc/nginx/nginx.conf`.
So you the end user need to mount a directory that contains an `nginx.conf` file (examples in this repo) to the `/config/` directory of the container.