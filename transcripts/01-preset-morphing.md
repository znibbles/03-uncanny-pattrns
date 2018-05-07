## Preset Morphing

One useful side-effect of using `[pattrstorage]` for managing your patcher persistence is that you can do **preset morphing** that way. We will take a quick look at how to do that.

I'll copy and paste parts of the cheby waveshaping example to demonstrate the use of `[pattr]` with a multi-parameter GUI object. 

## Using `[autopattr]` for Convenience

So first, let's hide away the wavetable generation in a subpatcher so we have enough space. We then assign a scripting name ('partials') to the `[multislider]` to easily access it later. Let's continue with a `[pattrstorage]` and send it the `[clientwindow(` message. We also load in `[autopattr]`, which auto-names GUI objects according to their scripting name.

We open the pattrstorage's client-window and see that we have a `[live.gain]` object referenced here, as well as the 'partials' `[multislider]`. In the rightmost column, we see the current data of those objects: One volume in dB for the gain object, and 8 float values representing the partials' amplitudes for the multislider.

We also see that we could switch between different interpolation modes, but leave it at 'linear' for the moment.

## Storing Presets...

Let's store some presets. For that we need to send the `[store(` message to the pattrstorage, followed by a preset index. We need to connect that number box to the second outlet of `[autopattr]`, to exclude it from being stored in the pattrstorage, because that would introduce a loop into our logic.

We set some partial amplitudes and actually store the first two presets. If we send `[storagewindow(` to the pattrstorage, we can inspect the values we just stored. We add a third preset and add a `[recall(` message to actually retrieve them.

## ... and Transitioning Between Them

So there are our different waveshaping presets, fed with the "vibes" example. Now, to morph between them, we just need to send a float instead of an integer into the `[recall(` message.

Okay, it's probably not the best idea to do this live, because every move of the mouse triggers a new buffer recalculation, but it can be a very useful tool to discover new timbres hiding in between your presets!


```
----------begin_max5_patcher----------
3610.3oc6crsjahb84Y9JXo1ph8lYTnuQ2jm18gTUdHtRpjGs2ZJjDRC1HPE
WFO1tV+sm9BfnAZ.oQ2FmL0ZIT2Mzm9bsOGN8Y+1s2XOO44fLaq+p06st4lu
c6M2HaRzvMk+9F6M9OuHxOSNL6UQIwEaruS00S9ow9aBj8vaddP56g+dUm7F
BiiBxk2HXWiIE4UsBKaU0T9W1FnfEa66rrm6Gu1152KGxV+7EOFFu9gzfE4p
QAbnyPh+buyxyYli3O1cVD9k2YAgybpu4vkRPLY9GuGRrqehobXOOH8gfX+4
Qxo1oruUIoa7kSiaYKY4eQMDaaQC+ws2J93tIh1VjrYSPbd0TmG7r7ga+t+4
+9e82s9S+s28SeH9CwerHK2J2+SAV9VbDse9OUcCQgwAKRJhk2EZ5HXGyXuc
3NWRMtCnPdXpAjGx9nfNT7JCvEANibQL4Rd5LPfov.8xvOaBxx7WGzgcgC09
QQV+LnWrCrWrCvH1YBXE.jI9h3NHFww9jtpyxSR4s+4v3kIe9juxgdvYt7+X
T9xmBlw3BIDONCBXHb.fcdjLNahEPLShFnv8P1.3d4jMDbIAmCQilXlJ4C7f
XE7Qh2H3y7GWe7FE.HkSevDRGzheQdBeQjuObN3g3bp+2fpO.6vQBzh3O9kD
1f3IXO3oxVRCjz2RrSI5QXW7ofYq8Ci+tvjgbp4OlcOdIiXdneT4lbblAvLp
KWz1YFj3QgthqvH.kAjW44wuTbEE3RAPwUtTL0CK6k5.Px6E434fAV+tbRjj
wiEa7hnP9FENW55bPxcAfw555ndCRmbN07ya9RoN+NnGIqbYmVcF1D3sOTiB
03IHfNCv4rE7y.zfB9Ly7yBwxF7z6Vwy9XVRb884+TvxG3OJNf7fXkGNuHWs
g8lRAJdlFfqKS.nNbVZ.mmUrCOrlDgIUy2TYqs4RGveLPjzBH+JBw4kv1qSy
2QVs1v216CKdLX9WNWDSwVeQb6YfRi8rAY5olokxofaZtEUYUXTvSAoYgb54
NXkS52tsQy2z3VD3pOlHePz6paJLV0DptozfmBqteRcq9o7EZNeUVTxS8Lqx
br3wjrLHMtHTBJpF4TsaqdfU3Fo4c4GtXkq.hMBti4Y95njEeJXoFSSx1f3v
3sb9YNanedIjU28xfU9EQ4OrJINOK7qRfSnjtu9W4uHv3MWqe32R4pzqVa1q
SCWlDK.BM7rn4poiaQhH2OKo4hQNhX+s8byJYNCclwWjEYy8SEjgRIHXUm4I
IQ5cUeeQAqxK6daXbbKrH2Ns4NSCW+3.267DdmaF5YK6I6ghXUuOvkHyePne
Qebb2KJEQ0e7O6GGx8HNHOTQBfN0cpzh7X1hzjnHs0qpmm5omkbN3E7czuL+
Q4D0jYfO7vsULQ10T4kgq45K0aK2ecldKcjN4MULuTB8g7fMai3qB4.9Zb3b
N3kY2XUtKXHMEKapTSq8Asoqqga2taJCvPCYAT8x2j0dy59FQ+W8jUK67O7y
SZBI8nfDQnRgEO2YD9F2.DthR3L9mPbCwmVJHwrlO0V6LXm8haprVbzQvTmW
cHXte0SC2RO83VMKy5n1bq4VQVyODzKvH5EMD5U5d5c83p5AgtUNsBbjegfp
fYL.5VWTsqJkJXn1X04gLLuX0pfzuaI2kj0ul4uYalEC3AOtDF3PDFYXIONT
EfGRRHnHo+gHwtUozQoMNWTQgsAAepjBbHXczgosQg0eYXaGRarMaTAAuKKt
1ZaRzWhS1H8e+7oa+XfsQLQrD7XBE6HxNFbDZLbNabcOsb3PG8ZzwCSNez51
6yIDCNhX1YjwcHwjSIZNlzx4Dk21pOoTlx8DnNpT3hxhjHEjJ7mgwbgTxc8d
En68108lI3hiY2bz3NG1UGyt6zhgyjGOSyqmQ77YTueF0CnQ7BZbOgF0anI3
QzT7JZe7LZ.uiF0Cog8RZXOkF1aoA8XxjWS864jY0Ml8fxtEFP26o15UZaQn
S+iYYn06Biq2NfiKZO.CQYXLCDCuQnABGtlf0X1JLYuv0UZKFo9h.kFIPsjZ
aYn.0941iAZMiz5FpOwjms9K9Dm5z6+8RHYrAIYfQIYGExETFpPjijNAvnIQ
t7tpoWOE771TqedEv5W3eBOcRUmWRDRIPQlFIhcUSh9ZjUVct275VeWI0Qot
C6NIhC8+SbNuFiP6A0w8BaMRgNrGB+BFD+5LUlVbY7iHUeNHSq6.nkV8TkiX
h9dizGz2ZksvOJXoEGN2VjakrxJO0ONaUPp0ph3Exs70dxiWF7bK+otTxD+E
tCVWPCIc8i+kpuxS9ka4aJbLEVjqZEVR68uQj.K+xa1l742vM8+gObG6su8s
2+FHwUqUWdq+42.bczZEKGKBp0HTLzWFYGbMr+AP4VF3ewXXHvUjUjzoP2Af
WAzcWrFUiJIk.fNsjHI6s3EPxgRm8K7e91W+jYDYFjQnPQRNv0lSITFySHpC
lDs14U.stkDpqj.hYcjk4R3rNxx2+ifrLfNiPAXQ1dA7nybQ.hGTj8GSZuMd
uFzi61QxkqF2oijKWb9GDIWtsXlfnxIotdyHNDnqHomXSxSO1q.RJqGisreH
s0xfy3BmLgzIFLCQYdDQdipR.owHkzWAjRbOVPQ+fHGx2IAVXAUHHBPyfb4P
HQkNoSwuwWATO3OjFE490KLIJy7QxL.jaTTjQq3IE64WCt17CgzkxwSU5B4N
IRC9xRZj3uAiCiywFuZNDVf8HTMvCLRMQgY4u0xey1nv7hkAYhnzrJLMK2JP
7FJsdzOcSRb3hLiQpA9+LjEE2LvY5TEvKK9YO4GUvII4IVh3mk+XZRw5GORA
QS+MpKNgli75OkHDw3FltkkTjtnBsV5+gUWjDmUKOLtNUDd+t2xjEoLC82WV
pCE.Y6K.hOy.HceAPzYF.EgOe5PnZrmW.bewfvyL.R1W.DblAP79BfmaRLZu
zyvtDP3dongdIfv8RSC4R.g6kfh6k.BUBmSGEdtkjg6AFzfh8jzkp72z4pEx
kBa.yPN3rB4hWpx9o9jdl4JDuJf8CBcO2P3d.fdCy1BuZAb1v.N5pEvoCC33
qV.2cX.mb0B3jgAb2qV.GOLfSuZAbCZwuPVC2KH2YXHe5AJPF.iQhTvtC5bw
xvj+iLY6e3cAwE5Apn5zBL75d95UgQQ0mIhaLNxarqhmisZz20pasyUAzCC.
xRkABfJKjFH9EDROaan7dAU2Llf8bjUWCrKjhkGJCLChHH4oO2vsC2M2N.O2
xBwAyAqth2Dn6Y5Pd69wqKOjBTm1Q8ky.klrMIs9PcLC4049KxSVm5uLrL.S
ZLp5za8SuhpdKvuKSwsxdCm.F19YJXZtsuG3XkDhVT0C6vAL7gOYny2x5nj4
9QkGVf5GwTNiA6NPB21EsdZOmYeci+VtrMC3ArtGLSOo0l7gMibINHwZmyLG
0Q6SbbsAPmwNmYW1iTbwWCkGcUqi7g1dRmp3puCiyOJGrXjLr1T7XnbxoGk2
NN+Fiw+gyiZDOnde8n5OMdZ1G+DN1LV9Mauaf4OB3rN4N7TOozNicJ+kuBb4
g8u77eNNxw8Dgb1U0S57lJ1gu5amTMvZiG3+A7lrQTZFjlsuv.chvPq.VdTg
AhJf2SBOnCqc2.4EAvnlALmSFfAl.fgOkjM7T4ecOk.A8Z.HlHL.fmPfP9vA
STTFbJAhofJHmZLwTjawTiPQcUZa+pkb6U8WZ3s62WwXp017OnZHmoho7uMd
NXH5HvewiVkkERwuSRCWywrQVbxP7xY8Vxkg00E591fp87h45mx88o1LaZSm
8teeracgHDw1cMTUTDvFJdcjiTEabW41rup1ndw3bnZWYy5nPy7.UUiRHL0W
cbgoEBjXp5+kEtNVTe3Zdk3e0EuFQN6LXIBD6zs1znNNbbGt5EEiQCU5aqKT
gogMqeDUMm8XxmqPiNZxq0BpCHxJSxkjUcqlf6fjnj30CRmzFMGbRy6Y38M1
JztSO8sgS5E8ceyftn0uujays2dCiCEhncwh8Mp5Z+5NklMFTAeP0b93aapp
7fz.UUNDpkBBC9rrTWDxU.8EMB9pUYAspsh0rOpZMxxTtNw5B+PE4eQT3hOU
lvRMauScjPuim51w70hxrhVK61bWU4HMccoKA1+pn7wHDRdJbdP189fY9gqD
+9WiRR1Jr7Jt9oDgT08dMEM63m4TqVmkRoSPfTTx+qJE0PUFj4QLHPtqRPWw
IuLXShRIOmZxmjCQEXvWW5u36Gh1MWUY0T4pLo5SC51bFEUfDGpkRcS3xZgS
iGW6RUCnmRZZsUANinejlBoiXg8sYoMd620ivlICp8UzrNTto8w9ZkdejLga
ovNVfZlvnT6SI1hKs8ohsUU6MmlE5sqUrlCSTHCKCGlQzl6Q5+aAHhadVT3x
9KW90086g1PVENjU86fb9nJsJUpvFXTFEt6tpWJfAKc5SsDSSH0h1PrLHRzF
Y8sXCv7GPOVa56Tnd.khe4DoGmHEEoseLkzkgiIiIWWzxLF6MgK2lDFmWNi7
sYwppQyhiGTYMZFppL48zDzEVuUMLPUQMqaR4KTGFrotbZApFBghyNWwdYyD
XJyzKdMAlvZB5dDVSvCfaPOrXmgoFXhQrlWxsVjjvEU0ZpKX67x.a2oPanGC
ZCYJyzwfyFBNayjyDlI1QXh.ry0DME9A.9XLS3y0RBNAEcs3N0y9rS7TCNE5
ilzT2hZejzo.lh72wPkB3vD+T64nU4IULGsJGosJCocK+nlK6nsK2nxPi1Je
bTq0Qx+lV4cy2t0Td1TEgl9yqlCIeZNv7n4.yel9yaFy4Kig7joJFK2cq47g
QOOXjgu9Ot8+BriLUH.
-----------end_max5_patcher-----------
```
