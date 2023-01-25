# Aliases

***This section is a work in progress.***

Aliases can go a long way to make console commands more interactive. The only limits I can think of with aliases' interactivity is that they don't respond at all. They are created as follow :

`alias [name] "[console command]"`

When an alias is created, it is then called in the console or in configs by it's name. It can be also used as a bind.

This can be used either to give meaningful names to console commands, be referred between multiple configs and so on. Aliases are stored in the client's memory and are dumped after you close the game, so **aliases aren't automatically saved once you close the game.** This is why it's best to **define aliases in your *autoexec.cfg* file once you boot it up.**

## Basic aliases
Let's create a basic example.

For this example, let's imagine this scenario : you like having different crosshairs for different classes. For instance, your default crosshair is `cl_crosshair_scale 31; cl_crosshair_file crosshair7`. However, you don't think this crosshair is adequate for Sniper or Spy, so you change it to `cl_crosshair_scale 26; cl_crosshair_file crosshair5`.

These commands are perfectly fine, but what if you realize that you're more comfortable with a different crosshair for Sniper and Spy? That would mean you'd have to manually open every file

This is where aliases come in. In your __autoexec.cfg__, you can make an alias for every crosshair you want to use like this :
```
alias xhair_default     "cl_crosshair_scale 31; cl_crosshair_file crosshair7"
alias xhair_precision   "cl_crosshair_scale 26; cl_crosshair_file crosshair5"
```
These aliases will be stored by the game client until shutdown, which means you can **reuse these aliases in any other config file** or even **use it as a console command**.

## Cycle aliases
**Cycle aliases** are a group of aliases that are used together to have different console commands per use. Here's a template for a 4-step cycle :
```
alias main sub_1
alias sub_1 "[command]; alias main sub_2"
alias sub_2 "[command]; alias main sub_3"
alias sub_3 "[command]; alias main sub_4"
alias sub_4 "[command]; alias main sub_1"
```
This will allow to cycle through multiple commands. In the case of some commands, you will need to refer to these commands from external aliases and call these aliases.
For instance, my favorite use of this is to post dumb garbage in chat that exceeds TF2 chat's character limit :
```
alias concrete conc_cycl_1

alias conc_cycl_1 "conc_say_1; alias concrete conc_cycl_2"
alias conc_cycl_2 "conc_say_2; alias concrete conc_cycl_3"
alias conc_cycl_3 "conc_say_3; alias concrete conc_cycl_4"
alias conc_cycl_4 "conc_say_4; alias concrete conc_cycl_1"

alias conc_say_1  "say Self-leveling concrete has polymer-modified cement that has high flow characteristics and, in contrast to"
alias conc_say_2  "say traditional concrete, does not require the addition of excessive amounts of water for placement. Self-leveling concrete is"
alias conc_say_3  "say typically used to create a flat and smooth surface with a compressive strength similar to or higher than that of traditional"
alias conc_say_4  "say concrete prior to installing interior floor coverings."

bind kp_5 concrete
```
