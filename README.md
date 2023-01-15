# Zeesastrous's TF2 Script Collection

Scripts I have personally made throughout the years I've played TF2. This includes short guide on tips for making your own scripts and cleaning up your configs.

## Good Practices for Scripting

*This section is a work in progress.*

### Common .cfg file for all classes
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
alias interp_hitscan_alt  "cl_interp 0.018; cl_interp_ratio 1.2"
alias interp_projectile   "cl_interp 0.015; cl_interp_ratio 1"
```
This is useful to define certain aliases or settings ***only once per launch***. 

## About cl_interp & cl_interp_ratio
***This part is absolutely speculative.*** *The effects of interp can be difficult to research, and a lot of misconceptions have been spread around. Most of what I'm writing is purely based on personal experimentation.*

Server interpolation (`cl_interp` and `cl_interp_ratio`) are probably the most important settings that can dictate whether you can hit your shots or not. I was told before by a pro player that interp is a placebo command, but I say that's bullshit.

**__The following values are my personal optimal settings for official servers at ~30 ping.__**
The equation I use to get the best results are `[desired cl_interp value] * [server's tick rate] = [cl_interp_ratio value]`.
For instance, I find that `cl_interp 0.018` yields favorable results, as it consistently deletes opponents with headshots. Official servers run at `66` tick. To find the best interp ratio value, I would do `0.018 * 66 = 1.188`, thus `cl_interp_ratio 1.188`. *(you could round it to `1.2` if you desire, however I'd try to stick at best to absolute values)*

My optimal interp settings for classes that have **projectile based attacks**, such as **Pyro**(?), **Demoman**, **Soldier** and **Medic** *(Engineer if you use Rescue Ranger)* are `cl_interp 0.0152; cl_interp_ratio 1`, as projectiles are server-sided, thus the lowest value yields the best results. This is the default setting to a lot of pro players for projectile classes.

My optimal interp settings for classes that have **hitscan based attacks**, like **Scout**, **Heavy**, **Sniper** and **Spy** are `cl_interp .0181818181; cl_interp_ratio 1.2`. This setting consistently registers headshots when I overlay the crosshair on top of heads. I also use `cl_interp .0185; cl_interp_ratio 1.221` whenever the former setting doesn't feel right.
I tend to actually go with `cl_interp 0.03030303; cl_interp_ratio 2` for Scout specifically, as his considerably faster speed makes playing him significantly more different than Engineer's or Pyro's shotgun.

I still highly recommend that you **tweak these values to whatever you feel best comfortable with.** These values are what I feel most comfortable with while playing. If you believe you're consistently performing well with your current values, then don't bother tweaking them.

### Why .0181 for hitscan? Why not .015?
`cl_interp .015` is optimal for LAN play for both hitscan and projectiles. However, I tend to notice while playing Sniper that the hitbox doesn't actually match the model, the hitbox being moved a bit forward from the model during movement. Animations seem to break much more consistently. Nudging these values to .0181 seems to correct these mistakes.

In general, **Higher interp values results in the actual hitbox being more distanced from the playermodel**.
