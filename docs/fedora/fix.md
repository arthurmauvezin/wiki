# Fix Fedora

## Bluetooth not working
* https://forums.fedoraforum.org/showthread.php?315528-Bluetooth-not-found
* https://fedoraproject.org/wiki/Documentation/Bluetooth

```bash
sudo dnf install bluez-hid2hci
```

## Investigate
```bash
dmesg | grep -i bluetooth
hciconfig
systemctl status bluetooth.service
```

## Reset bluetooth
```bash
hciconfig hci0 sspmode 1
hciconfig hci0 down
hciconfig hci0 up
```

## Deactivate fingerprint reading
### Message
```bash
Sep 18 20:18:56 aion dbus-daemon[835]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.163' (uid=0 pid=10502 comm="sudo tail -500f /var/log/kern " label="unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023")
Sep 18 20:18:56 aion systemd[1]: Starting Fingerprint Authentication Daemon...
Sep 18 20:18:56 aion dbus-daemon[835]: [system] Successfully activated service 'net.reactivated.Fprint'
Sep 18 20:18:56 aion systemd[1]: Started Fingerprint Authentication Daemon.
Sep 18 20:18:56 aion audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:init_t:s0 msg='unit=fprintd comm="systemd" exe="/usr/lib/systemd/systemd" hostname=? addr=? terminal=? res=success'
```
### Solution
```bash
sudo systemctl status fprintd.service
```

## Freeze in terminal
### Message
```bash
imestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Sep 18 20:18:27 aion org.gnome.Shell.desktop[1819]: Window manager warning: W21 (Tilix: Def) appears to be one of the offending windows with a timestamp of 1870764.  Working around...
Sep 18 20:18:52 aion org.gnome.Shell.desktop[1819]: Window manager warning: last_user_time (1895184) is greater than comparison timestamp (1894259).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Sep 18 20:18:52 aion org.gnome.Shell.desktop[1819]: Window manager warning: W21 (Tilix: Def) appears to be one of the offending windows with a timestamp of 1895184.  Working around...

# More messages
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: libinput error: client bug: timer event6 keyboard: offset negative (-626ms)
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: libinput error: client bug: timer event18 keyboard: offset negative (-626ms)
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: libinput error: client bug: timer event6 keyboard: offset negative (-397ms)
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: libinput error: client bug: timer event18 keyboard: offset negative (-397ms)
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: Window manager warning: last_user_time (2827900) is greater than comparison timestamp (2827671).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Sep 18 20:34:25 aion org.gnome.Shell.desktop[1819]: Window manager warning: W21 (Tilix: Def) appears to be one of the offending windows with a timestamp of 2827900.  Working around...

# Seems to be correct message
Sep 18 21:15:06 aion org.gnome.Shell.desktop[1819]: Window manager warning: last_user_time (5269516) is greater than comparison timestamp (5269257).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Sep 18 21:15:06 aion org.gnome.Shell.desktop[1819]: Window manager warning: W21 (Tilix: Def) appears to be one of the offending windows with a timestamp of 5269516.  Working around...


Sep 18 23:17:22 aion syslog-ng[843]: Log statistics; processed='src.internal(s_sys#0)=21', stamp='src.internal(s_sys#0)=1537304842', processed='destination(d_spol)=0', processed='destination(d_mlal)=0', processed='center(received)=21', processed='destination(d_mesg)=18049', processed='destination(d_mail)=0', processed='destination(d_auth)=71', processed='destination(d_cron)=15', processed='center(queued)=19766', queued='global(scratch_buffers_count)=34359738368', processed='global(payload_reallocs)=52297', processed='src.journald(journal)=18393', stamp='src.journald(journal)=1537305420', processed='global(sdata_updates)=0', queued='global(scratch_buffers_bytes)=0', processed='destination(d_boot)=0', processed='destination(d_kern)=1631', processed='source(s_sys)=21', processed='global(msg_clones)=36', processed='global(internal_queue_length)=0'
```
### Solution
```bash
# Do not have it at the moment
```
