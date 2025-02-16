
# un seul VM qui va utiliser vagrant sous vbox pour construire les VM

## install vagrant:

``
https://linuxize.com/post/how-to-install-vagrant-on-ubuntu-20-04/
``

## install docker on ubuntu:
``
https://docs.docker.com/engine/install/ubuntu/
``
## lancer le container rancher sur la VM apres installation docker:

``
sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
``
## recuperer le password rancher

``
sudo docker logs 3d5bad502f61 2>&1 | grep "Bootstrap Password:"
``
