---
sidebar_position : 7
---

AWS a été la plateforme utilisé afin de supporter ce projet cloud

il a fallut importer la machine Samba sur aws, et pour ce faire, les étapes suivantes on été réaliser : 

- Importation de la VM depuis virtualbox en OVA

tout d'abord sur la machine local, il faudra récuperer le disque dur virtuel du serveur

```
tar -xvf nom_vm.ova
```
on obtient le fichier .vmdk de la vm, qu'on devra ensuite rendre au format RAW
```
qemu-img convert -f vmdk -O raw nom_vm-disk.vmdk nom_vm.raw
```
On peut ensuite transférer l'image vers AWS dans le service S3

Il faudra tout d'abord créer un bucket en configurant ses options

puis on ouvre le cloudshell de aws et on entre
```
aws s3 cp nom_vm.raw s3://nom_bucket/
```

l'importation peut durer plusieurs minutes voir heure dépendant de la taille du disque.

Une fois importer dans aws dans le bucket, il faudra importer l'image en tant qu'AMI

```
aws ec2 import-image --disk-containers "Format=raw,UserBucket={S3Bucket=nom_bucket,S3Key=nom_vm.raw}"
```

Il faudra noté l'ID de **"import-ami-xxxxxxx"** qui sera retourné

Il n'y a plus qu'a attendre que la conversion se fasse, on peut vérifier l'avancement avec la commande suivante.
```
aws ec2 describe-import-image-tasks --import-task-ids import-ami-xxxxxxxx
```

une fois que la status est passé a "completed" alors on peut créer l'instance dans **AWS EC2**

une fois l'instance créer, vous pouvez recuperer l'ip publique et vous connecter en ssh en récupérant la clé de sécurité fourni lors de la création de l'instance.