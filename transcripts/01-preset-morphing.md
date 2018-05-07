##

One useful side-effect of using `[pattrstorage]` for managing your patcher persistence is that you can do **preset morphing** that way. We will take a quick look at how to do that.

I'll copy and paste parts of the cheby waveshaping example to demonstrate the use of `[pattr]` with a multi-parameter GUI object. 

So first, let's hide away the wavetable generation in a subpatcher so we have enough space. Let's start with a `[pattrstorage]` and send it the `[clientwindow(` message. We also load in `[autopattr]`, which auto-names GUI objects according to their scripting name.

We open the pattrstorage's client-window and see that we have a `[live.gain]` object referenced here, as well as the `[multislider]` we named `partials`. In the rightmost column, we see the current data of those objects: One volume in dB for the gain object, and 8 float values representing the partials' amplitudes for the multislider.

We also see that we could switch between different interpolation modes, but leave it at 'linear' for the moment.