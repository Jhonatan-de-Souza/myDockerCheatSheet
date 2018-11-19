#What is an Image (And What Isn't)

. App binaries and dependencies
. Metada about the image data and how to run the image
. Not a compelte OS. No kernel, kernel modules(ex: drivers)
. Small as one file or
. Big as Ubuntu distro

# Docker Image tags and Pushing to Docker Hub

. Only  offical docker images have their name without a user prefix, ex: jhonatan/nginx

# Container Lifetime & Persistant Data

. Container should be replaceble but the data should remain intact
. the containers shouldn't container the data, but only the binaries
. The container solves the problem of persistent data with two thing:
    1.Volumes: map to a drive/directory outside the container 
    2.Bind Mounts: link container path to host path