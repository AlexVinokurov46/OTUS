Описание домашнего задания:
1) Обновить ядро ОС из репозитория ELRepo
2) Создать Vagrant box c помощью Packer
3) Загрузить Vagrant box в Vagrant Cloud


# 1 - kernel-update listing
```
va@va-ubuntu:~/Centos8OTUSPacker$ ls
packer  Vagrantfile
```
# Поднимаем виртуалку Вагрантом
```
va@va-ubuntu:~/Centos8OTUSPacker$ vagrant up
```
# Подключаемся к виртуальной машине
```
va@va-ubuntu:~/Centos8OTUSPacker$ vagrant ssh
```
# Проверяем версию ядра
```
[vagrant@kernel-update ~]$ uname -r
4.18.0-516.el8.x86_64
```
[vagrant@kernel-update ~]$ history
