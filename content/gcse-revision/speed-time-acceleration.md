+++
title = "Speed, velocity and acceleration"
description = "Explaining speed, velocity and acceleration"
summary = "A page explaining speed, velocity and acceleration and how each three of these things can be worked out. (Physics OCR 21st Century)"
date = 2025-09-28
draft = false
showPagination = false
+++

### Speed and velocity

Scalars are a magnitude (how big in size something is).

Vectors are both a magnitude (how big something is) and the direction an object travels in.

Distance is a measurement of how far an object has travelled, regardless of where it starts or ends. Because of this, distance is described as a scalar (it only measures how far something has travelled, disregarding where it has travelled). It is measured in metres (m).

Displacement is a measurement of how far an object has travelled from its starting point. Since displacement takes into account where the object has travelled, it is a vector. Like distance, it is also measured in metres (m).

The average speed of an object is equal to the distance it has travelled divided by how much time it took to travel that distance. Or in other terms:

$$
\text{speed}=\frac{\text{distance}}{\text{time}} 
$$



The average velocity of an object is equal to how far it has travelled from its starting point, divided by how much time it took to travel there. Or in other terms:
$$
\text{velocity}=\frac{\text{displacement}}{\text{time}} 
$$

{{< notice note >}}
Make sure you don't confuse velocity with speed.

Velocity is a vector (measures how fast an object moves in a certain direction), whereas speed is a scalar (measures how fast an object moves regardless of where it moves)
{{< /notice >}}

### Acceleration

Acceleration is the rate of change of a given object's velocity. In other terms, it measures how fast an object goes from one speed to another. It is measured in metres per second squared. It can be worked out with the below equation:

$$
\text{acceleration}=\frac{\text{change in velocity}}{\text{time}} 
$$

Or:

$$
\let\acceleration=A \let\finalvelocity=v \let\initialvelocity=u \let\time = t
\acceleration = \frac{\finalvelocity - \initialvelocity}{\time}
$$

Where:
* `A` means acceleration
* `v` means the final velocity of an object
* `u` means the initial velocity of an object
* `t` is the total amount of time an object takes to accelerate.

### First motion equation for acceleration

The final velocity of an object can be worked out with the below equation:
$$
\text{final velocity}=\text{initial velocity} + \text{acceleration} \times \text{time}
$$

Or:
$$
\let\acceleration=a \let\finalvelocity=v \let\initialvelocity=u \let\time = t
\finalvelocity = \initialvelocity + \acceleration\time
$$

<u>Example:</u>

> Work out the velocity of a greyhound, accelerating from stationary at 4m/s², after 2 seconds.
1) Write out the full equation:
$$
\let\acceleration=a \let\finalvelocity=v \let\initialvelocity=u \let\time = t
\finalvelocity = \initialvelocity + \acceleration\time
$$
2) Insert your numbers (0 for initial velocity, as the greyhound was stationary, 4 for acceleration, and 2 for time)
$$
\let\finalvelocity=v
\finalvelocity = 0 + 4 \times 2
$$
3) Follow the order of operations to get your answer:
$$
\let\finalvelocity=v
\finalvelocity = 8
$$
4) Remember to add in the units:
$$
\let\finalvelocity=v 
\finalvelocity = 8\text{m}/\text{s}^2
$$

Therefore, the greyhound's final speed is 8m/s²

### Second motion equation for acceleration

The distance an object has travelled from its starting point (its displacement) can be calculated from its initial velocity, time, acceleration, as shown below:
$$
\text{displacement} = \text{initial speed} \times \text{time} + \frac{1}{2} \times \text{acceleration} \times \text{time}^2
$$

Or:

$$
\let\displacement = s \let\initialvelocity = u \let\time = t \let\acceleration = a
\displacement = \initialvelocity \time + \frac{1}{2} \acceleration \time^2
$$

* `s` means displacement (make sure you don't confuse this as for meaning "speed")
* `u` means the initial velocity of an object
* `t` means time

<u>Example:</u>

> A car starts from rest and accelerates at 2m/s² for 5 seconds. How far does the car travel in this time?

How far does the car travel in that time?
1) Write out the full equation:
$$
\let\displacement = s \let\initialvelocity = u \let\time = t \let\acceleration = a
\displacement = \initialvelocity \time + \frac{1}{2} \acceleration \time^2
$$
2) Insert your numbers (0 for initial speed, as the car was stationary or "at rest", 2 for acceleration, and 5 for time)
$$
\let\displacement = s
\displacement = 0 \times 5 + \frac{1}{2} \times 2 \times 5^2 
$$
3) Follow the order of operations to get your answer:
$$
\let\displacement = s
\displacement = 25
$$
4) Remember to add in the units:
$$
\let\displacement=s 
\displacement = 25\text{m}
$$

The car travels 25 metres.

### Third motion equation for acceleration

You can calculate the initial or final velocity of an object based of acceleration and displacment, alongside the velocity that is known, as shown below:

$$
(\text{final velocity})^2 - (\text{initial velocity})^2 = 2 \times \text{acceleration} \times \text{displacement} 
$$

Or:

$$
\let\displacement = s \let\initialvelocity = u \let\finalvelocity = v \let\acceleration = a 
\finalvelocity^2 - \initialvelocity^2 = 2\acceleration\displacement
$$

This means that the object's final velocity can be figured out by rearranging the above equation into the one below:
$$
\let\displacement = s \let\initialvelocity = u \let\finalvelocity = v \let\acceleration = a
\finalvelocity = \sqrt{\initialvelocity^2 + 2\acceleration\displacement}
$$

Keep in mind, there is no plus-or-minus symbol before the square root because a velocity cannot be negative. 

The same applies to the object's initial velocity:
$$
\let\displacement = s \let\initialvelocity = u \let\finalvelocity = v \let\acceleration = a
\initialvelocity = \sqrt{\finalvelocity^2 - 2\acceleration\displacement}
$$

<u>Example:</u>
> A train accelerates to 10m/s at an acceleration at 2m/s². It does this in 18m, what speed did it start at?

1) Write out the full equation:
$$
\let\displacement = s \let\initialvelocity = u \let\finalvelocity = v \let\acceleration = a
\initialvelocity = \sqrt{\finalvelocity^2 - 2\acceleration\displacement}
$$
2) Insert your numbers (10 for final velocity, 2 for acceleration, 18 for displacement)
$$
\let\initialvelocity = u
\initialvelocity = \sqrt{10^2 - 2 \times 2 \times 18}
$$
3) Follow the order of operations to get your answer:
$$
\let\displacement = s
\displacement = \sqrt{28} \enspace \text{or} \enspace 2\sqrt{7}
$$
4) Remember to add in the units:
$$
\let\displacement=s 
\displacement = 2\sqrt{7}\text{m/s}
$$

If the question says to approximate the above number to a certain amount of decimal places or significant figures, then do so.


{{< katex >}}