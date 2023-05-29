# Получение сведений о системе

## Цель работы

Получить сведения об используемой системе.

## Исходные данные

- Ноутбук DELL на базе x64;

- Ubuntu 22.04;

- Интерпретатор командной оболочки bash 5.2.15;

- Эмулятор терминала Konsole.

## План

1. Ввод команд в эмулятор терминала

2. Анализ данных

## Ход работы

1. Сначала получим сведения об используемом дистрибутиве:

```bash
vboxuser@UbuntuVM:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.04.2 LTS
Release: 22.04
Codename: jammy
```

В результате был определён используемый дистрибутив - Ubuntu 22.04.2 LTS.

2.Затем получим сведения о версии ядра:

```bash
vboxuser@UbuntuVM:~$ uname -a
Linux UbuntuVM 5.19.0-42-generic #43~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Apr 21 16:51:08 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

В результате была получена версия ядра - 5.19.0-42, дата компиляции ядра - Fri Apr 21 16:51:08.

3.Далее можно получить сведения о процессоре:

```bash
vboxuser@UbuntuVM:~$ cat /proc/cpuinfo | grep "model name"
model name: Intel(R) Core(TM) i3-5005U CPU @ 2.00GHz
```

Было определено, что используемый процессор - Intel(R) Core(TM) i3-5005U.

4.Далее получим последние 30 строк логов системы:

```bash
мая 25 01:37:47 UbuntuVM systemd[3685]: Starting GNOME Terminal Server...
мая 25 01:37:47 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Successfully activated service 'org.gnome.Terminal'
мая 25 01:37:47 UbuntuVM systemd[3685]: Started GNOME Terminal Server.
мая 25 01:37:47 UbuntuVM systemd[3685]: Started VTE child process 4582 launched by gnome-terminal-server process 4564.
мая 25 01:39:26 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Activating service name='org.gnome.gedit' requested by ':1.37' (uid=1000 pid=3893 comm="/usr/bin/gnome-shell " label="unconfined")
мая 25 01:39:26 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Successfully activated service 'org.gnome.gedit'
мая 25 01:39:30 UbuntuVM gsd-color[4073]: unable to get EDID for xrandr-Virtual-1: unable to get EDID for output
мая 25 01:43:51 UbuntuVM systemd[3685]: gnome-terminal-server.service: Consumed 1.451s CPU time.
мая 25 01:44:00 UbuntuVM gnome-shell[3893]: JS ERROR: TypeError: this.actor is null
                                               _syncEnabled@resource:///org/gnome/shell/ui/windowManager.js:138:25
                                               onStopped@resource:///org/gnome/shell/ui/windowManager.js:150:35
                                               _makeEaseCallback/<@resource:///org/gnome/shell/ui/environment.js:151:22
                                               _easeActorProperty/<@resource:///org/gnome/shell/ui/environment.js:317:60
                                               _destroyWindowDone@resource:///org/gnome/shell/ui/windowManager.js:1596:21
                                               onStopped@resource:///org/gnome/shell/ui/windowManager.js:1564:39
                                               _makeEaseCallback/<@resource:///org/gnome/shell/ui/environment.js:151:22
                                               _easeActor/<@resource:///org/gnome/shell/ui/environment.js:240:64
мая 25 01:44:04 UbuntuVM systemd[3685]: Started Application launched by gnome-shell.
мая 25 01:44:05 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.119' (uid=1000 pid=4634 comm="/usr/bin/gnome-terminal.real " label="unconfined")
мая 25 01:44:05 UbuntuVM systemd[3685]: Starting GNOME Terminal Server...
мая 25 01:44:05 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Successfully activated service 'org.gnome.Terminal'
мая 25 01:44:05 UbuntuVM systemd[3685]: Started GNOME Terminal Server.
мая 25 01:44:06 UbuntuVM systemd[3685]: Started VTE child process 4657 launched by gnome-terminal-server process 4639.
мая 25 01:46:42 UbuntuVM systemd[3685]: gnome-terminal-server.service: Consumed 1.120s CPU time.
мая 25 01:48:09 UbuntuVM systemd[3685]: Started Application launched by gnome-shell.
мая 25 01:48:10 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.123' (uid=1000 pid=4676 comm="/usr/bin/gnome-terminal.real " label="unconfined")
мая 25 01:48:10 UbuntuVM systemd[3685]: Starting GNOME Terminal Server...
мая 25 01:48:10 UbuntuVM dbus-daemon[3706]: [session uid=1000 pid=3706] Successfully activated service 'org.gnome.Terminal'
мая 25 01:48:10 UbuntuVM systemd[3685]: Started GNOME Terminal Server.
мая 25 01:48:10 UbuntuVM systemd[3685]: Started VTE child process 4699 launched by gnome-terminal-server process 4681.
```

## Оценка результата

В результате лабораторной работы была получена базовая информация об используемой системе.

## Вывод

По итогу лабораторной работы мы научились получать сведения о системе, используя команды Linux.
