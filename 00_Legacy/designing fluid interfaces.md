video: https://developer.apple.com/videos/play/wwdc2018/803

it just feel right "you know it when you feel it"
**a tool that feels like an extension of your mind**

![[designing-fluid-interface-1.png|400]]
## Best of worlds:
no latency, respond instantly
allows for constant redirection and interruption
- "i want to look for apps list, ah no! i want to go home"

gesture happen in *parallel* with thought
linear
- thought-decide-gesture-release
versus fluid: video@9:24 (too much for my level of interest 😂)
	thought -->  gesture
	decide   -->  release

spatial consistency (like how elements moves in real world)
- element from right? hide it to the right

hint in the direction of gesture
- e.g. icon - (medium size hint) - full screen ui
- notification center

keep touch interaction lightweight, but amplify their motion @15:52
- like pushing a ball
- scrolling

(instead of timer, use finger acceleration)

it's important for an interface to **respond satisfyingly** to  every interaction
- signaling you that it *understood* you

avoid visually strobes
- motion blur
- motion stretch 

conceptual mass
- photos in photos app is "lighter" than apps in app switch


# Designing with Dynamic Motion

### Seamless motion

"you can't tell when (the car) precisely stopped" ~ infinite motion
the content is always moving, *always able to move*
you don't have to wait for anything to finish

elasticity @31:45
![[elasticity.png]]
that ↑, simplified:


damping (ratio) - how much the element overshoots
(frequency) response - how fast the element's attribute go from initial to target value

![[springing-simplified.png]]

using duration introduces "constant dynamic change" - so avoid it for *elasticity* 
- "in animations like walking cycles or flying sequences, dynamic change adds realism by mimicking the unpredictability of real-life movement, such as slight shifts in speed or direction"

<span style="color: red; font-size: 3rem">stopped at 35:13</span>
continue next time