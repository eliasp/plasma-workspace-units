- Make sure a replacement for `kcheckrunning` is either found or not needed anymore

- Fix the insanity of `kstartupconfig`
  - is `kstartupconfig` needed at all in the context of a systemd user-session?
  - `kstartupconfig`'s code is an ugly hack, full of 'goto' and with a nice 'system()' at the end

- Extract all environment variables from http://techbase.kde.org/KDE_System_Administration/Environment_Variables and
  run an analysis against all components to find out which component makes use of which environment variable. Adjust
  environment variables in service units accordingly

- Create a TechBase page to coordinate all further efforts

- As requested by systemd devs in #systemd, announce project on systemd ML once the basics are working to make sure
  we get valuable input in the early project phase to steer the efforts into the right direction

- Extract relevant information from [IRC Log](IRC-Log)

- Figure out how to register `ksmserver` as `Leader` for the logind session. Currently the display-manager (sddm) is
  registered as `Leader` (`loginctl show-session 1`):
```
Id=1
Name=elias
Timestamp=Mon 2014-05-05 00:37:18 CEST
TimestampMonotonic=16782996
VTNr=7
Display=:0
Remote=no
Service=sddm
Scope=session-1.scope
Leader=2639
Audit=1
Type=x11
Class=user
Active=no
State=closing
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
```
  This leads to issues such as:
    - Unable to unlock screen
    - Message `The session is not registered with logind "PID 4970 does not belong to any known session"` in ksmserver journal

  As long as `loginctl show-session 1` doesn't show ksmserver's PID as `Leader`, this issues will persist.

- Make sure https://projects.kde.org/projects/kde/workspace/plasma-workspace/repository/revisions/b551c6dbd4490b04a0548f40e4fbd5e1feeb0e0e is covered/adopted/translated
