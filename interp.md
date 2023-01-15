# About cl_interp & cl_interp_ratio
***This part is absolutely speculative.*** *The effects of interp can be difficult to research, and a lot of misconceptions have been spread around online. Most of what I'm writing is purely based on personal experimentation.*

Server interpolation (`cl_interp` and `cl_interp_ratio`) are probably the most important settings that can dictate whether you can hit your shots or not. I was told before by a pro player that interp is a placebo command, but I say that's bullshit.

**__The following values are my personal optimal settings for official servers at ~30 ping.__**

~~The equation I use to get the best results are `[desired cl_interp value] * [server's tick rate] = [cl_interp_ratio value]`.
For instance, I find that `cl_interp 0.018` yields favorable results, as it consistently deletes opponents with headshots. Official servers run at `66` tick. To find the best interp ratio value, I would do `0.018 * 66 = 1.188`, thus `cl_interp_ratio 1.188`. *(you could round it to `1.2` if you desire, however I'd try to stick at best to absolute values)*~~ Having tested interp values more, I've noticed that `cl_interp_ratio 1` is significantly better for most settings on low ping. `cl_interp_ratio 2` should be used for higher ping.



My optimal interp settings for classes that have **projectile based attacks**, such as **Pyro**(?), **Demoman**, **Soldier** and **Medic** *(Engineer if you use Rescue Ranger)* are `cl_interp 0.015; cl_interp_ratio 1`, as projectiles are server-sided, thus the lowest value yields the best results. This is the default setting to a lot of pro players for projectile classes.

My optimal interp settings for classes that have **hitscan based attacks**, like **Scout**, **Heavy**, **Sniper** and **Spy** are `cl_interp .0185; cl_interp_ratio 1`. This setting consistently registers headshots when I overlay the crosshair on top of heads. I also use `cl_interp .0182; cl_interp_ratio 1` whenever the former setting doesn't feel right.

I still highly recommend that you **tweak these values to whatever you feel best comfortable with.** These values are what I feel most comfortable with while playing. If you believe you're consistently performing well with your current values, then don't bother tweaking them.

## Why .0185 for hitscan? Why not .015?
`cl_interp .015` is optimal for LAN play for both hitscan and projectiles, as LAN environments have virtually no delay between communicating with the host and the clients. In online servers, I tend to notice while playing Sniper that the hitbox doesn't actually match the model, the hitbox being moved a bit forward from the model during movement. Animations also break much more consistently with that setting. I've experimented with these values for a long time and come to the conclusion that .0185 is the sweet spot to correct these discrepancies while keeping the hitbox as close to the model as possible.

In general, **Higher interp values results in the actual hitbox being more distanced from the player's model.**. In my personal experience, the hitbox seems to lag behind the higher the value, however there are videos clearly showing the model being behind the hitbox.
