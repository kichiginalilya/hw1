- название выполняемого задания - Занятие 1. Vagrant-стенд для обновления ядра и создания образа системы

- текст задания:
1) Обновить ядро ОС из репозитория ELRepo
2) Создать Vagrant box c помощью Packer
3) Загрузить Vagrant box в Vagrant Cloud

- Commands:

- packer build centos.json - команда для создания образа системы
- vagrant box add --name centos8-kernel6 centos-8-kernel-6-x86_64-Minimal.box - добавляем полученный в предыдущей команде бокс в вагрант
- vagrant cloud publish --release kichiginalilya/centos8-kernel6 1.0 virtualbox centos-8-kernel-6-x86_64-Minimal.box - публикуем бокс в вагрант клауде
- vagrant init kichiginalilya/centos8-kernel6 - создаем вагрант инит файл
- редактируем вагрант файл с инфой 
Vagrant.configure("2") do |config|
  config.vm.box = "kichiginalilya/centos8-kernel6"
  config.vm.box_version = "1.0"
end
- vagrant up - запускаем бокс (бокс качается и разворачивается в виртуал боксе)


не загрузился бокс через кли, пришлось загружать через сайт вагранта, потом сняла галку с Private образа, сделав его публичном и отрелизила.
