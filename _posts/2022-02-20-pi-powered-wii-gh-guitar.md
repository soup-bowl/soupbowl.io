---
layout: post
title:  "I built: Pico Powered Wii Guitar!"
image:  /assets/img/IMG_20201221_122851-1980x1114.webp
author: Casey (Soupbowl)
tags:   [Gadgets, Gaming, Guides, Raspberry Pi]
---

**During the unprecidented times, I surprisingly got big into Guitar Hero... After not playing in about 10 years.**

We got given a Wii by family, that was sitting in a cupboard going unused. And there was always two things I associated with Wii consoles - Wii Sports, and Guitar Hero!

I heard nowadays due to them being slightly rare, the Guitar Hero controllers were quite expensive. I was however able to pick up an Aerosmith and World Tour Gibson Les Paul for about £20... Turns out they were this cheap because they were *broken* (read the damn listing!). I haven't fixed the Aerosmith controller yet (broken blue button, but my partner prefers easy mode), but the World Tour (my favorite) had the typical strum bar misclicking issue, but a soldering iron and [a couple of these bad boys](https://www.tandyonline.com/components/switches/miniature-microswitch-with-short-lever.html) fixed it up good and proper.

We had some good fun with these during lockdown, but our TV then broke. Our replacement TV was a 4K model with **no analogue inputs**. We bought a Wii to HDMI converter, and while this worked okay the visual delay just really screws up these kind of games. Eventually the controllers got put into a cupboard and forgotten about as the Wii got replaced with a Switch.

But I got the itch again... And this time, I learned about **[Clone Hero](https://clonehero.net/)**.

## Clone Hero

The best Guitar Hero game - undeniably - will always be *Guitar Hero III*. And given the oppertunity, I'd buy up that bad boy on PC in a second. The problem is it's barely available anywhere. The game has never been released on *Steam* and physical copies of the game can command quite a decent price.

But the community didn't take this lying down, and there has been many 'clones' of Guitar Hero available for PC for free. *Frets on Fire* was the popular one back when I was a teenager, but *Clone Hero* is the latest on the free market. Imagine Guitar Hero without the stage performanc in the background, and you've got it - they're **that** close!

The best thing though about this game is the community. Due to legal reasons I can't necessarily share the resources, but some resourceful Redditor fans of Clone Hero have ported **all** Guitar Hero game music onto Clone Hero. That's right, you can now basically play the whole repoitore of the series on one game!

Sounds good, right? Well you just need a Guitar to get going- oh wait, I have a **Wii** guitar...

## The Wiitar Problem

Pretty much all but native PC Guitar Hero controllers have some sort of hurdle to overcome, but the Wii Guitar was the only one in the range to actually *offload* the controller functionalites onto another controller. You'd plug in your Wii controller into the Guitar chassis, and then it register as a Guitar on the Wii. Neat huh? Well to use the Wii Guitar on PC would require what's called a **[Raphnet Adapter](https://www.raphnet-tech.com/products/wusbmote_1player_adapter_v3/index.php)**. Nothing wrong with that, but they can be *pricy*.

Well it just so happened I had a Raspberry Pi Pico sitting on my desk. *You can see where this is going.*

## Raspberry Pi Driver

Without a controller, the Guitar Hero controller is just an input device. You've got the 5 button fret, the strum bar, power and menu buttons, the whammy and that wierd touch bar thing. The Wii controller understands these various inputs, and sends them to the console to register the input with what the user did. Simple... Kinda.

In this situation, we're going to be replacing the Wii controller with a Raspberry Pi Pico. That way, our pico is recieving all the various inputs coming from the Guitar Hero controller, and we can use the Pico to parse these instructions and send them to the computer via a "Human Interface Device (HID)". That way, instead of our Wii getting the instructions wirelessly, our PC will be getting them via a USB cable. I found **[4ntu's PicoGuitar](https://github.com/4ntsu/PicoGuitar)**
instructions worked perfectly for getting the Pi to produce HID signals that Clone Hero would understand perfectly.

## What would I need?

This build is **incredibly simple**, but you **may need to solder on 4 pins**! This can be adjusted, but for my build I used:

* **World Tour** Guitar Hero Wii Controller
  * You could probably use others, but you might need to do some further research as the input method is slightly different between models.
* **[Raspberry Pi Pico](https://shop.pimoroni.com/products/raspberry-pi-pico?variant=32402092326995)**
  * Headers are required. Either buy pre-soldered to save you the job, or do it yourself. The pads are quite spacious so it's not a difficult task!
* [Wii Breakout Board](https://shop.pimoroni.com/products/adafruit-wii-nunchuck-breakout-adapter-qwiic-stemma-qt)
  * This has **4 pins** that **need soldering**. You could try using a dupont pin jumper into the pad, but the connection might not be strong enough.
  * Alternatively, cut the connector end off of a dead Nunchuck and strip the wires out. If you add dupont female connectors to this, you might be able to *avoid* soldering.
* [Female to Female jumper cables](https://shop.pimoroni.com/products/jumper-jerky-junior?variant=1076482185)

*I'm not affiliated with Pimoroni. Just like to consolidate my orders to one platform.*

You'll also need a **Soldering iron** and some solder. If you're new to soldering pins onto circuit boards, here's a [good tutorial from the *Raspberry Pi Foundation*](https://youtu.be/8Z-2wPWGnqE). Undoing soldering (desoldering) is far more difficult than soldering itself, so **go slow and be careful** if you don't want to change it from an hour process to 7 hours of screaming and breaking things.

