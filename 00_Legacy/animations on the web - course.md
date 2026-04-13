#### Be able to build anything that **looks** and **feels** great!
(Experiment: Re-watch and re-read the whole course several times to master?)

## Goals:
- [x] grasp his theory behind great animations
- [x] grasp how he think about animations
- [x] grasp how he choose the right easing, duration, etc
- [ ] create animations that are **elegant** and **intuitive** even on the web
	- [ ] create something to share in the group and make them **WOW**


## Mastery Checklist: ***(how to tell that you've mastered these concepts?)***
- [ ] easing
- [ ] ~~spring animation~~
	- [ ] ~~mass~~
	- [ ] ~~stiffness/tension~~
	- [ ] ~~velocity~~
- [x] duration


----
September 9, 2024
- ✨an animation that "feels great" is like a living organism
- when things change instantly, it feels robotic

September 10, 2024
- there is an easing function suited for each type of animation
- consider:
	- meaning, consequences of actions**?**
		- *"It should link actions to consequences in a logical and understandable way"*
	- taste**?**

September 12, 2024
- *"However, on the web, there's an **additional layer of abstraction**; we rely on a mouse and keyboard to navigate, which makes creating natural, fluid, and intuitive interfaces more challenging."*
- ✨easing affect the perception of speed/performance
- default easing curves are sluggish, use custom easing instead!
- *"reference the [blueprint](https://animations.dev/learn/easing-curves) as much as possible"*

September 13, 2024
- spring animation does not have a specific duration
- spring animation are *not constrained by duration* --> feel continuous and fluid
- spring animations are *interruptible*
- while CSS animations are not interruptible
-  Generally, having no bounce at all should be your default to ensure that your transitions feel natural and elegant

September 16, 2024
- ✨Generally, *larger animations require longer durations* as they are **"heavy"**
- Hover transitions should be faster than other animations, *as we are focused on the element already*. Additionally, *our eyes are quite sensitive to color changes*, so we can use even shorter duration for color and opacity transitions.
- When to animate?
	- *when it enrich the information on the page*
	- the purpose of most animations should be *to add context*
		- The easier this task is, the more context your animation provides
- When **not** to animate?
	- when the user will often see it (e.g. opening Raycast)
	- keyboard interaction

**Taste**
- the ability to form opinions with your gut that you can also justify with your head
	- I don’t fully agree, instead of justifying with head, the more important thing is the ability to express that gut feel in reality

September 17, 2024

**Framer Motion**
- motion HTML element wrapper
- initial {}
- animate {} - end
- transition {} - "settings"
- AnimatePresence - wrap the component that will be removed but wanted to animate
	- exit {} - like 'end'/animate but specifically when component is 'removed'
- *With this type of animations, it's important to include `initial={false}` on `AnimatePresence`. This tells Framer Motion not to animate on the initial render.*
>**Tip**
> If an animation that involves `AnimatePresence` is not working as expected, make sure that you have a `key` prop on the element you're animating. Otherwise, the component won't be unmounted and the exit animation won't be triggered.
- ❌ Problem: There is a small period of time when the old and the new element are both present; that causes one of them to shift
	- ✅ Solution: AnimatePresence mode="popLayout" - the exit animation has position absolute, which means that it does not occupy any space in the button**...?**

September 19, 2024
- The most powerful feature of Framer Motion library is the `layout` prop.
	- For layout animations to work, we need to change the actual style of the element.

September 21, 2024
- ❌ Avoid transform: translate for centering at it will cause instant shift
	- conflict with Framer Motion's transform values
- ✨ simply adding AnimatePresence makes the component *interruptible*
- if you want to change the transition for the layout only, do:
`
transition = {{
	layout: {duration: 2.0, type: 'spring', bounce: 0.2 }
}}
`
-`MotionValue` is a primitive from Framer Motion that updates its value *outside of React's render cycle*. That's what allows Framer Motion to animate at 60 frames per second, as we are not triggering any re-renders.


September 22, 2024
- ✨ `layoutId` is very powerful, and it's even more powerful once you become a bit creative with it. In this case, we created an illusion. The placeholder is not an actual placeholder, but it looks like one.
- `popLayout` mode is often times the right mode for your animations. If you see your exit animation breaking, think about the `mode` prop
- *"I want it to feel kinda calm so that's the reason for longer duration"*
- `MotionConfig` - self-explanatory :D
- When an element is animating out using `AnimatePresence` its state is stale. To work around this, you can use the `custom` prop on our `motion.div` as well as on `AnimatePresence`. This will ensure that all leaving components are using the latest data. ![[custom-prop.png]]
- ❌ [Rapid switching](https://animations.dev/learn/coding-animations/multi-step-component#rapid-switching)
	- When you switch quickly between states in animate presence, you might eventually see both elements being visible in the DOM. That's a bug in Framer Motion that will hopefully be fixed. If you are experiencing it and you can't work around it, I suggest installing version `11.0.10` of Framer Motion where this bug is not present.
- *How I came up with these (delay, duration) values?* [@6:01](https://animations.dev/learn/coding-animations/trash-interaction)
	- not guess
	- try stuff out, record animation, and play frame by frame to see whether a given set of values (is correct to what I want) touches the trash for example 
- We now need to create this nice drop animation. However, **we can't influence the way shared layout animations are done**. What we can do is we can animate the parent div so that the images will follow it.

> ---
> My opinion:
> animations **does not need to be very thorough** as we humans always do *fill-in-the-blanks*
> for example: if you can animate the whole container nicely, you do not need to animate each buttons inside it one-by-one--> just because you think that these will affect the unconscious whatever
> ---

#### The big little details
- slow animations (like Stripe's marketing website) ==> looks Premium and Reliable , "we're not in a hurry"
- easeInOut curves ==> Young, Edgy feel
- *Usually our goal is to make animations that feels fast and not annoying*
- **Orchestration**
	- A "detail" that can take your animation to the next level.
- **Blur** 
	- mask any potential imperfection in animation
	- use when your animation "feels off" and you cannot tell why
	- makes animation feels more natural
- ✅ *Reviewing your work*
	- after stepping away, you'll notice things you haven't seen before



September 23, 2024
- feels fast - so probably an easeOut easing or a spring animation with no bounds
- ❌ border distortion in framer motion: use border in px
	- > There is a small border radius distortion happening. That's because layout animations are done with `transform`, which can distort properties like `border-radius` and `box-shadow`. Framer Motion is able to fix such distortions, but only if our border radius value is in pixels.
- ✅ key prop when using ternary for 2 different components in AnimatePresence
- "we will use position *absolute* so the performance impact of it is not that big"
	- AH! Because it will not need to push/move other elements aside from itself! 🤩
- ✨ whenever you need a **shake**-like animations, go for **keyframes** (rotate)
- ✨ a great use case for AnimatePresence as each number is *rendered separately*
- ✨*popLayout mode* - to animate exit and enter at the same time
- ✨ scaling down to zero does not look good on some type of animation


September 24, 2024
*Emil's views on Dynamic Island*
- element either scales down or up when transitioning 🤔
- each animations has different bounce
> You might have expected a more sophisticated solution, but I think it's worth showing that sometimes solutions like this one also give you the expected results. I do this often when I'm prototyping something to save time.

**Performance**
- ✅ The rule of thumb here is that you should try to animate with `transform` and `opacity` as they only trigger the third rendering step (composite) while `padding` or `margin` triggers all three.
- Transforms don't trigger layout recalculation as they only affect the visual representation of an element, not its position in the document flow.
- The problem with JS animations arises when they are using `requestAnimationFrame` to animate. Javascript code will _always_ run on the main thread. This means that if the browser is busy doing something else, it might skip a frame, causing the animation to drop frames.
-  Framer Motion is using `requestAnimationFrame` (calculates in the main thread)
- Personally, I often times combine CSS animations with Framer Motion. CSS for simple animations and those that should be hardware-accelerated, and Framer Motion for more complex/sophisticated animations.
- ❌ Once the content of the drawer got bigger than ~20 list items the drag gesture became laggy, and I couldn't figure out why. Dragging was done without any re-renders, so what could cause it to drop frames? Every time the drag position gets updated, I changed a CSS variable which is then used as the value for `translateY()`.
	-  Since CSS Variables are inheritable, changing them will cause style recalculation for all children, meaning the more items I have in my drawer, the more expensive the calculation gets. Updating the style directly on the element fixed the issue. This seems like a quick fix in retrospect, but it took me hours to figure out.



----
**Custom component note:** When using `popLayout` mode, any immediate child of AnimatePresence that's a custom component **must** be wrapped in React's `forwardRef` function, forwarding the provided `ref` to the DOM node you wish to pop out of the layout.