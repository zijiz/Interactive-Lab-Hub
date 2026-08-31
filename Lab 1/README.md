# Recreating the Masters of Interactive Light

_This project is to be done in teams of 2._

**COLLABORATORS:** Ziji Zhang, Nishant Ray

**THE MASTERWORK YOU DREW FROM THE HAT:** The Five-Tone Light Wall. Close Encounters, 1977

---

## Part 0. Know Your Master

Steven Spielberg’s 1977 film Close Encounters of the Third Kind depicts a scene where first contact with aliens is a conversation rather than a battle. In the movie, a team of scientists and government workers faces an enormous alien mothership. Because the two sides do not share a spoken language, the humans use a musical console and a large wall of colored lights to send a simple five-note phrase. The ship answers with the same phrase through its own lights and powerful tones, showing that it has heard and recognized the communication.

The core interaction is a call-and-response conversation in which notes and colored light become a shared language between humans and the ship. The human operator’s input is a sequence played on a keyboard. The system turns each note into both sound and a matching flash of color on the light wall. The mothership responds with its own combinations of tones and lights, and the humans listen, watch, and answer. What begins as the careful repetition of five notes grows faster and more complicated. Eventually the computer cannot keep pace, so the operator begins playing by hand and joins the ship in a musical conversation.

The players include the keyboard operator, the scientists directing the experiment, the military personnel securing the site, and the witnesses who watch in awe. The mothership is also a player: its immense scale, brightness, and volume give it power, but its willingness to repeat and build on the human phrase makes it seem curious rather than hostile. The people do not control the encounter; they offer a small signal, wait, interpret the reply, and adapt. This makes the relationship feel cautious at first, then cooperative and playful as both sides take turns leading. The scene is famous for making communication visible and emotional without translating it into words. Its strongest feature is the immediate feedback loop: play, flash, wait, answer. Repetition confirms that contact has been made, while changes in tempo, pitch, brightness, and scale communicate growing excitement.


## Part A. Plan

**Setting:** Our recreation takes place in a dark room that represents the landing site from Close Encounters of the Third Kind. We do not plan to recreate the full environment from the film. Instead, we will simplify the scene into two sides: a human operator at a computer and a light source several feet away representing the alien spacecraft.
Keeping the room dark allows the light to become the main focus of the interaction.


**Players:** The main players are the human operator, the scientists observing the encounter, and the alien spacecraft.
The human operator uses the five-tone system to initiate communication. The scientists watch and interpret the exchange, while the spacecraft responds through light and sound.
As the interaction becomes faster and more complex, the human operator is eventually no longer able to control the exchange manually.


**Activity:** The interaction begins with the human operator sending a slow sequence of five signals.
The alien light stays dark for a short moment and then repeats the same pattern. This pause is important because it makes the response feel intentional rather than like a prerecorded animation.
The human then sends another sequence. This time, the alien responds faster and adds variation to the pattern. As the exchange continues, the alien signals become faster and more complicated.
Eventually, the human operator cannot keep up and stops trying to control the conversation.
The main progression is:
signal → response → repetition → variation → increasing speed → human falls behind


**Goals:** The human operator is trying to establish communication with an unknown intelligence and understand whether the light is responding intentionally.
The alien's role is to acknowledge the human signal, respond to it, and gradually introduce more complex patterns.
Our goal as designers is to make the audience understand that a conversation is developing using only light, timing, and the reactions of the human operator.

**Our three storyboards** 

Storyboard 1. Basic Call and Response
Our first storyboard focuses on the simplest version of the interaction.
The human operator sends a five-color sequence:
1 → 2 → 3 → 4 → 5
The light turns off for approximately two seconds.
The alien then repeats the same sequence:
1 → 2 → 3 → 4 → 5
The operator reacts when they realize that the signal has been returned.
This version tests whether the basic idea of “we sent something, and something answered us” is clear to the viewer.
![Storyboard 1](storyboard_1.jpg)

Storyboard 2. Pattern Variation
In the second storyboard, we added a small variation to make the exchange feel more like a conversation instead of simple playback.
The human sends:
1 → 2 → 3 → 4 → 5
The alien repeats it.
The human sends the same sequence again.
This time, the alien responds with:
1 → 2 → 3 → 4 → 5 → 3 → 5
The operator pauses and then tries to repeat the new sequence.
This creates a stronger sense that both sides are participating in the interaction and beginning to build a shared pattern.

Storyboard 3. Increasing Speed
For the third storyboard, we kept the same call-and-response structure but added increasing speed and complexity.
The human begins with a slow five-part sequence.
After a short pause, the alien responds with the same sequence.
During the next exchange, the alien responds more quickly and adds additional signals.
The human tries to follow the new pattern, but the alien continues getting faster.
Eventually, the operator is unable to keep up and stops interacting while the light continues rapidly on its own.
This creates a clearer progression from simple communication to a moment where the interaction moves beyond direct human control.


**Feedback and Chosen Direction:** 
The first storyboard was easy to understand, but it felt too much like a simple input-and-output system.
The second storyboard made the light feel more intelligent because the response changed instead of only repeating the original pattern.
The third storyboard created the clearest interaction because it included both variation and increasing speed while still being simple enough to prototype with one phone and one hidden wizard.
We decided to continue with Storyboard 3 for the physical prototype.
It can be staged with a very simple setup, but still captures the main idea we want to recreate: a basic light signal gradually becoming a conversation between a human and another intelligence.


## Part B. Act out the Interaction

We ran it first with one of us waving a phone flashlight while the other played
Peter. Two things we learned that the storyboard hid:

- **The chime matters more than we thought.** Silent, the light looked like a bug.
  The moment we added a little chime on each "speech" blink, Peter's translations
  landed and it became a *character*.
- **Peter's eyeline is half the effect.** When the actor genuinely tracked the
  light with his eyes and body, the light felt alive even when it was barely
  moving. When he didn't, no amount of fancy light movement helped.

**Better on paper than acted out:** the long jealous "buzzing around Wendy" was
tiresome live; we cut it to one sharp flare + dart.

**New idea from acting:** let the light go completely still and dark for a full
beat before the revival — the silence makes the audience *want* to clap.

## Part C. Prototype the Light (light first!)

We used the Tinkerbelle tool: the phone in the browser was the light, and the
laptop drove its brightness and color. We mapped the light's whole vocabulary to
the control panel: a brightness slider (life/mood), a "dart" that we faked by
physically moving the costumed phone while pulsing it, a warm-orange flash button
(jealousy flare), and a blink pattern with a chime for speech.

**We deliberately did nothing but light this week.** We got the four behaviors —
brightness, motion, flare, blink+chime — reading clearly before we let ourselves
add anything. The one non-light element we kept is the chime, because in the
original it's part of how the light "speaks"; everything else is pure light.

**Feedback on Tinkerbelle:** The brightness ramp is smooth and the latency is low
enough for call-and-response, which is exactly what this piece needs. We wished we
could save a "dim slowly over 8 seconds" fade as a one-button cue instead of
riding the slider by hand during the death beat — that was the hardest thing to
perform live.

## Part D. Wizard the Device

One of us hid off-camera as the wizard, watching Peter and driving the laptop; the
other performed Peter and carried the costumed phone. We recorded over Zoom and
pinned the "stage" feed. The wizard's whole job was to answer the actor in real
time — brighten when Peter smiles at her, flare when Wendy enters, and ride the
slow fade on cue.

*(First wizarded run-through video pasted in here in a real submission.)*

The revival beat only worked once the wizard stopped watching the laptop and
watched *the actor and the room*, bringing the light up in time with the clapping.
Driving it by the script alone felt dead; driving it by reading the room felt
alive.

## Part E. Costume the Device

We made three costumes for the phone so the bare screen wouldn't break the spell:

1. **Paper-lantern Tinker Bell** — a small translucent paper globe around the
   phone that diffuses the screen into a soft orb of light. Reads as "fairy" and
   hides the rectangle. *(Our pick.)*
2. **Frosted jar** — phone inside a frosted glass jar; prettier glow but too heavy
   to "dart" convincingly.
3. **Vellum-and-wire wings** — phone clipped behind a pair of translucent wings so
   the light shines through them. Charming but fragile.

**Concerns / opportunities shaping the look:** the object has to be *light enough
to fly* (dart through the air on a stick or by hand), it has to *diffuse* the hard
screen into a soft glow, and it must not show the phone's edges or the operator's
hand. The paper lantern won because it was the lightest and the most diffuse — the
staging need (fast, floaty motion) drove the material choice more than looks did.

## Part F. Record

*(Final ~60-second video sketch pasted in here in a real submission: the nursery
scene through the revival beat, with a real audience clapping the light back.)*

Our aim was the bar from the top of the lab — a viewer who knows *Peter Pan*
recognizes the "clap if you believe" moment instantly, and a viewer who doesn't
still understands that a light became a character the audience chose to save.

**Non-sequential interaction sketch:** see
`tinkerbell_interaction_sketch.svg` in this folder. It's a single hub diagram:
the light at the center with its four-part vocabulary radiating out, the
real-time loop (actor → wizard → light → others & audience → back) running around
the ring, and the revival beat called out as the audience-input / light-output
moment. We drew it as a hub rather than a filmstrip on purpose — the storyboard
already shows the *sequence*; this shows the *system*.

**Collaborators & influences:** Jane and John split wizard/actor duties and traded
off. Thanks to the group in our breakout room who guessed the piece from the
storyboards and pushed us to separate "leading" from "jealousy." Background on the
original staging came from the standard *Peter Pan* production histories.

---

## (Bonus) Part 2 — Make It Your Own

Modeling the second week for you: our critique of the master was that it's totally
dependent on a hidden human operator. So our remix asks: *what if Tink had to run
without a wizard — and what if she didn't use light at all?*

We rebuilt her as a **pocket haptic fairy**: a phone in your pocket that represents
Tink through **vibration** instead of light. A gentle steady buzz when she's near
and content, an excited flutter when she wants your attention, a sharp double-buzz
for "no / danger," and a long slow fade to stillness when she's fading. You revive
her not by clapping but by **holding the phone to your chest** (the accelerometer
detects it) — belief becomes a private, physical gesture instead of a public one.

It trades the theatrical, communal magic of the original for something intimate and
solo — which is exactly the kind of strength/weakness tradeoff Part 0 asked us to
find. *(Storyboard + video pasted in here in a real submission.)*
