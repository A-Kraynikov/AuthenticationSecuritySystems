# Получение сведений о системе
## Цель работы
Получить сведения об используемой системе
## Исходные данные

## План работы
1. Ввод команд в эмулятор терминала
2. Анализ данных
## Ход работы
1. Сначала получим сведения об используемом дистрибутиве:

    engle@engle-VirtualBox:~$ lsb_release -a
    No LSB modules are available.
    Distributor ID: Ubuntu
    Description: Ubuntu 22.04.2 LTS
    Release: 22.04
    Codename: jammy

В результате был определён используемый дистрибутив - Ubuntu 22.04.2 LTS
2. Получим сведения о версии ядра:


# Получение сведений о системе

## Цель работы

Получить сведения об используемой системе

## Исходные данные

- Ноутбук DELL на базе x64

- Ubuntu 22.04

- Интерпретатор командной оболочки bash 5.2.15

- Эмулятор терминала Konsole

## План работы

1. Ввод команд в эмулятор терминала

2. Анализ данных

## Ход работы

1. Сначала получим сведения об используемом дистрибутиве:

```bash
engle@engle-VirtualBox:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.04.2 LTS
Release: 22.04
Codename: jammy
```

В результате был определён используемый дистрибутив - Ubuntu 22.04.2 LTS

2.Затем получим сведения о версии ядра:

```bash
engle@engle-VirtualBox:~$ uname -a
Linux engle-VirtualBox 5.19.0-32-generic #33~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Jan 30 17:03:34 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

В результате была получена версия ядра - 5.19.0-32, дата компиляции ядра - Mon Jan 30 17:03:34.

3.Далее можно получить сведения о процессоре:

```bash
engle@engle-VirtualBox:~$ cat /proc/cpuinfo | grep "model name"
model name: AMD Ryzen 7 5800H with Radeon Graphic
model name: AMD Ryzen 7 5800H with Radeon Graphics
model name: AMD Ryzen 7 5800H with Radeon Graphics
model name: AMD Ryzen 7 5800H with Radeon Graphics
```

Было определено, что используемый процессор - четырёхпоточный AMD Ryzen 7 5800H.

4.Далее получим последние 30 строк логов системы:

```bash
engle@engle-VirtualBox:~$ journalctl -q -b| tail -n 30
мар 01 19:54:48 engle-VirtualBox systemd[1]: Finished Record Runlevel Change in UTMP.
мар 01 19:54:48 engle-VirtualBox systemd[1]: Startup finished in 1.955s (kernel) + 32.119s (userspace) = 34.074s.
мар 01 19:54:52 engle-VirtualBox systemd[1]: systemd-timedated.service: Deactivated successfully.
мар 01 19:54:53 engle-VirtualBox pulseaudio[1150]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
мар 01 19:54:53 engle-VirtualBox dbus-daemon[645]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
мар 01 19:55:01 engle-VirtualBox systemd[1]: systemd-hostnamed.service: Deactivated successfully.
мар 01 19:55:02 engle-VirtualBox systemd[1]: systemd-localed.service: Deactivated successfully.
мар 01 19:55:30 engle-VirtualBox systemd[1141]: Started Application launched by gnome-session-binary.
мар 01 19:55:30 engle-VirtualBox geoclue[1402]: Service not used for 60 seconds. Shutting down..
мар 01 19:55:30 engle-VirtualBox systemd[1]: geoclue.service: Deactivated successfully.
мар 01 19:55:31 engle-VirtualBox systemd[1141]: Started Application launched by gnome-session-binary.
мар 01 19:55:32 engle-VirtualBox pkexec[1970]: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
мар 01 19:55:32 engle-VirtualBox pkexec[1970]: engle: Executing command [USER=root] [TTY=unknown] [CWD=/home/engle] [COMMAND=/usr/lib/update-notifier/package-system-locked]
мар 01 19:55:32 engle-VirtualBox ubuntu-appindicators@ubuntu.com[1297]: unable to update icon for software-update-available
мар 01 19:55:32 engle-VirtualBox ubuntu-appindicators@ubuntu.com[1297]: unable to update icon for livepatch
мар 01 19:55:38 engle-VirtualBox systemd[1141]: Started Application launched by gnome-shell.
мар 01 19:55:38 engle-VirtualBox dbus-daemon[1177]: [session uid=1000 pid=1177] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.105' (uid=1000 pid=1988 comm="/usr/bin/gnome-terminal.real " label="unconfined")
мар 01 19:55:38 engle-VirtualBox systemd[1141]: Created slice Slice /app/org.gnome.Terminal.
мар 01 19:55:38 engle-VirtualBox systemd[1141]: Starting GNOME Terminal Server...
мар 01 19:55:38 engle-VirtualBox dbus-daemon[1177]: [session uid=1000 pid=1177] Successfully activated service 'org.gnome.Terminal'
мар 01 19:55:38 engle-VirtualBox systemd[1141]: Started GNOME Terminal Server.
мар 01 19:55:38 engle-VirtualBox systemd[1141]: Started VTE child process 2019 launched by gnome-terminal-server process 1993.
мар 01 19:59:19 engle-VirtualBox systemd[1]: Starting Download data for packages that failed at package install time...
мар 01 19:59:19 engle-VirtualBox systemd[1]: update-notifier-download.service: Deactivated successfully.
мар 01 19:59:19 engle-VirtualBox systemd[1]: Finished Download data for packages that failed at package install time.
мар 01 19:59:22 engle-VirtualBox dbus-daemon[645]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.20' (uid=0 pid=666 comm="/usr/lib/snapd/snapd " label="unconfined")
мар 01 19:59:22 engle-VirtualBox systemd[1]: Starting Time & Date Service...
мар 01 19:59:22 engle-VirtualBox dbus-daemon[645]: [system] Successfully activated service 'org.freedesktop.timedate1'
мар 01 19:59:22 engle-VirtualBox systemd[1]: Started Time & Date Service.
мар 01 19:59:52 engle-VirtualBox systemd[1]: systemd-timedated.service: Deactivated successfully.
```

## Оценка результата

В результате лабораторной работы была получена базовая информация об используемой системе.

## Вывод

Таким образом. мы научились, используя команды Linux, получать сведения о системе.
