# About cl_interp & cl_interp_ratio
***This part is absolutely speculative.*** *The effects of interp can be difficult to research, and a lot of misconceptions have been spread around online. Most of what is written here is purely based on personal experimentation.*

Server interpolation (`cl_interp` and `cl_interp_ratio`) are probably the most important settings that can dictate whether you can hit your shots or not. I was told before by a pro player that interp is a placebo command, but I say that's bullshit.

**__The following values are my personal optimal settings for official servers at ~30 ping.__**

~~The equation I use to get the best results are `[desired cl_interp value] * [server's tick rate] = [cl_interp_ratio value]`.
For instance, I find that `cl_interp 0.018` yields favorable results, as it consistently deletes opponents with headshots. Official servers run at `66` tick. To find the best interp ratio value, I would do `0.018 * 66 = 1.188`, thus `cl_interp_ratio 1.188`. *(you could round it to `1.2` if you desire, however I'd try to stick at best to absolute values)*~~ ~~Having tested interp values more, I've noticed that `cl_interp_ratio 1` is significantly better for most settings on low ping. `cl_interp_ratio 2` is also good enough to make.~~ Turns out `cl_interp_ratio 1`, while viable on servers with >40ms ping, can prove to be risky since it gives no room for error correction. `cl_interp_ratio 2` has proven to be safer in most scenarios.



My optimal interp settings for classes that have **projectile based attacks**, such as **Pyro**(?), **Demoman**, **Soldier** and **Medic** *(Engineer if you use Rescue Ranger)* are `cl_interp 0.015; cl_interp_ratio 1`, as projectiles are server-sided, thus the lowest value yields the best results. This is the default setting to a lot of pro players for projectile classes.

My optimal interp settings for classes that have **hitscan based attacks**, like **Scout**, **Heavy**, **Sniper** and **Spy** are `cl_interp .0185; cl_interp_ratio 1`. This setting consistently registers headshots when I overlay the crosshair on top of heads. I also use `cl_interp .0182; cl_interp_ratio 1` whenever the former setting doesn't feel right.

I still highly recommend that you **tweak these values to whatever you feel best comfortable with.** These values are what I feel most comfortable with while playing. If you believe you're consistently performing well with your current values, then don't bother tweaking them.

## Why .0185 for hitscan? Why not .015/.03/.0?
`cl_interp .015`/`cl_interp 0` is optimal for LAN play for both hitscan and projectiles, as LAN environments have virtually no delay between communicating with the host and the clients. That means communication is instant, and there is virtually no server-side error when it comes to player position/animation, etc.

However, while playing with that setting in online servers, I would notice while playing Sniper that the hitbox wouldn't actually match the model. The hitbox would be slightly ahead of the model in most cases, leading to situations where a headshot on the back of the head would never register, even if blood would be painted on the enemy's model on my client.

As for the other popular option, `cl_interp .03; cl_interp_ratio 2` is great for higher latency play, there is still a noticeable gap between the model and the hitbox. TF2 isn't in an era where internet connections are limited anymore, so it's not optimal for low latency play.

I've experimented with these values for nearly a year, and come to the conclusion that `cl_interp .0185` is the sweet spot to correct these discrepancies while keeping the hitbox as close to the model as possible. This, however, doesn't prevent TF2's dogshit netcode from acting up, nor will it make it easier to get headshots on interp-abusing cheaters.

In general, **Higher interp values results in the actual hitbox being more distanced from the player's model.**. In my personal experience, the hitbox seems to lag behind the higher the value, however it's worth noting there are videos clearly showing the model being behind the hitbox.
