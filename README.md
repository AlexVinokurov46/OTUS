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
# Подключаем репозиторий Enterprise Linux, обновляем ядро на стабильное, обновляем конфигурацию загрузчика и ставим новое ядро загружаться по умолчанию, перезагружаемся
```
[vagrant@kernel-update ~]$ history
 sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm 

    3  sudo yum --enablerepo elrepo-kernel install kernel-ml -y

    4  sudo grub2-mkconfig -o /boot/grub2/grub.cfg

    5  sudo grub2-set-default 0

    6  history

    7  uname -r

    8  reboot
```
# Проверяем ядро после перезагрузки
```
[vagrant@kernel-update ~]$ uname -r

6.6.11-1.el8.elrepo.x86_64
```
# Ядро обновлено
# Собран vagrant box через packer, добавлен в vagrant
```
vagrant box add --name centos8-kernel6 centos-8-kernel-6-x86_64-Minimal.box 

==> box: Box file was not detected as metadata. Adding it directly...

==> box: Adding box 'centos8-kernel6' (v0) for provider: 

    box: Unpacking necessary files from: file:///home/va/Centos8OTUSPacker/packer/centos-8-kernel-6-x86_64-Minimal.box
==> box: Successfully added box 'centos8-kernel6' (v0) for ''!

```
# загрузка полученного box vagrant cloud обрывается на 100% 

