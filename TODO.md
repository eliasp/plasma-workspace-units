- Make sure a replacement for `kcheckrunning` is either found or not needed anymore

- Make sure, the existence of ~/.config is handled wherever needed (KConfig?)

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
