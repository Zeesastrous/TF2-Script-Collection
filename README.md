# Zeesastrous's TF2 Script Collection

Scripts I have personally made throughout the years I've played TF2. This includes short guide on tips for making your own scripts and cleaning up your configs.

# Good Practices for Scripting

*This section is a work in progress.*

## Common .cfg file for all classes
Everytime you switch classes in TF2, it will run a .cfg file named after that class. These files are located in `SteamLibrary/common/team fortress 2/tf/cfg`.
The files are named the following : `scout.cfg` `soldier.cfg` `pyro.cfg` `engineer.cfg` `heavyweapons.cfg` `demoman.cfg` `medic.cfg` `sniper.cfg` and `spy.cfg`.

I've arranged all of these config files with the following start :
```
//  [class].cfg
//DEFAULT BINDS & SETTINGS
exec zeesa_default

// for demos
alias mark_highlight "ds_mark [class]_highlight"
ds_mark "playing_[class]"

// insert every class-specific console commands below this point
```
- `exec zeesa_default` is a console command that will run the file `zeesa_default.cfg`, which is also located in `tf/cfg`. This is a custom config file that will run default console commands everytime I switch a class. This is incredibly useful to set parameters, aliases and such that are shared by multiple classes, like interp settings or resetting custom binds. 
- **Optional :** `alias mark_highlight "ds_mark [class]_highlight"` and `ds_mark "playing_[class]"` are purely for recording demos, which was my previous method of getting footage from TF2 before I switch to OBS. Of course, `[class]` is the respective class of the cfg file.
- `alias mark_highlight "ds_mark [class]_highlight"` was bound to a fairly accessible key, so when looking back at the demo's text file I could easily fast forward through the demo to get bits I thought are worth recording.

```
//  zeesa_default.cfg
cl_crosshair_scale 31 //pixel perfect xhair scale 1080p

//reset custom binds
//	resets mwheel stuff
unbind mwheelup
unbind mwheeldown
```
Basically, this file is meant for game-specific console settings that should alter between specific classes, such as interp config.
For instance, I reset the crosshair scale to 31, as I play Sniper with a slightly smaller crosshair. Since I don't want the small crosshair to carry over when I switch to other classes, I reset it in the common class.

### autoexec.cfg

`autoexec.cfg` is a file that runs when you boot up TF2. Because I use mastercomfig for graphical settings, I only use `autoexec.cfg` to define a few variables and override a few settings that mastercomfig changes when booting up the game.

```
//  autoexec.cfg

//interp settings
alias interp_hitscan      "cl_interp 0.03; cl_interp_ratio 2"
alias interp_hitscan_alt  "cl_interp 0.018; cl_interp_ratio 1"
alias interp_projectile   "cl_interp 0.015; cl_interp_ratio 1"
```
This is useful to define certain aliases or settings ***only once per launch***. 
