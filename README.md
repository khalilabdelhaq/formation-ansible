## Notes sur le système d'automatiqation Ansible.

Actuellement, Ansible peut être exécuté à partir de n'importe quelle machine sur laquelle Python 2 (version 2.7) ou Python 3 (version 3.5 et supérieures) est installé (l'interpréteur python est installé par défaut sur les machines Linux). Cela inclut Red Hat, Debian, CentOS, macOS, n'importe lequel des BSD, etc. Cependant, Windows n'est pas pris en charge pour le nœud de contrôle.

- Le fichier host contient l'inventaire de tous les serveur de votre parc. Vous pouvez utiliser la commande ansible-inventory pour valider et obtenir des informations sur votre inventaire Ansible

```
 $ ansible-inventory -i hosts --list

```

"Un bon devopsien, est un informaticien qui automatise ses tâches !", nous allons automatiser le provisionnement de nos nœuds esclaves depuis l'outil Vagrant dans l'hyperviseur Virtualbox.
Pour provisionner vos deux nouvelles VMs. Ouvrez un terminal et placez vous d'abord au même niveau que le fichier Vagrantfile et lancez ensuite la commande suivante :

```
$ vagrant up

```

- Pour arrêter les MV

```
$ vagrant halt

```

- pour vérifier la connection à vos host vous pouvez utiliser le module ping :

```
$ ansible all -m ping -u vagrant -i hosts

```

- Pour se connecter directement au serveur sans pour autant saisir le mots de passe à chaque fois il suffit de taper la commande suivante :

```
$ ssh-copy-id -p 2222 vagrant@127.0.0.1

```

- Pour débugger votre playbook

```
ansible-playbook -i hosts playbook.yml --check

```
