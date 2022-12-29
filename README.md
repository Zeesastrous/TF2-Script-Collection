# TF2-Script-Collection

Scripts I have personally made throughout the years of TF2, as well as a short form guide on tips for making your own scripts.

# Good Practices for scripting

*This section is a work in progress.*

Everytime you switch classes in TF2, it will run a .cfg file named after that class. These files are located in `SteamLibrary/common/team fortress 2/tf/cfg`.
The files are named the following : `scout.cfg` `soldier.cfg` `pyro.cfg` `engineer.cfg` `heavyweapons.cfg` `demoman.cfg` `medic.cfg` `sniper.cfg` and `spy.cfg`.

I've arranged all of these config files with the following start :
```
//DEFAULT BINDS & SETTINGS
exec zeesa_default

// for demos
alias mark_highlight "ds_mark [class]_highlight"
ds_mark "playing_[class]"
```
`exec zeesa_default` is a console command that will run the file `zeesa_default.cfg`, which is also located in `tf/cfg`. This is a custom config file that will run default console commands everytime I switch a class. This is incredibly useful to set parameters, aliases and such that are shared by multiple classes, like interp settings or resetting custom binds. 
