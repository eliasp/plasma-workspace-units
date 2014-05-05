The primary bus name of a service is added to the service's unit file, e.g:
`BusName=org.kde.KWin`
This is used by systemd to detect the point where a service is considered to be "ready".
systemd will wait until the service has registered on the bus using this name before it
returns the state `active` for it.

All bus names (incl. the primary) go to a dbus `session.d/` file, where each file represents
a bus name registered by this service. The service is activated via D-Bus, e.g.:
`SystemdService=org.kde.KWin`
