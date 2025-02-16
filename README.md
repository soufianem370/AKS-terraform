
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
nous allons ajouter un cluster depuis des VM linux ubuntu sans aucun prérequis : avec un type d'installation RKE2

``
sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
``
## recuperer le password rancher

``
sudo docker logs 3d5bad502f61 2>&1 | grep "Bootstrap Password:"
``
modifier le passord apres mdp ui rancher (ranchertoortoor)
## ajouter un cluster (--etcd --controlplane --worker):

``
sudo curl --insecure -fL https://18.227.10.54/system-agent-install.sh | sudo sh -s - --server https://18.227.10.54 --label 'cattle.io/os=linux' --token g2xbd9f6gfdpsbzknf59pwxc2c5hkfnz9pmwlz6tztpvgfhzmjqgjj --ca-checksum 50293921b8a80940f3c3b544b2de551964650f650d551be4dea95cd7a67c9d35 --etcd --controlplane --worker
``
## ajouter un cluster ( --worker):

``
sudo curl --insecure -fL https://18.227.10.54/system-agent-install.sh | sudo sh -s - --server https://18.227.10.54 --label 'cattle.io/os=linux' --token g2xbd9f6gfdpsbzknf59pwxc2c5hkfnz9pmwlz6tztpvgfhzmjqgjj --ca-checksum 50293921b8a80940f3c3b544b2de551964650f650d551be4dea95cd7a67c9d35 --worker
``
