###***Some basic concepts***

----

+ **rigid body** $def:=$ All points on the body have the same angular velocity/accelerations;

-Rotational directions
radial 
rotational

+ rotiaonal vs. traslation

  ![image-20211127172906495](C:\Users\15290\OneDrive - 厦门大学(马来西亚分校)\Desktop\markdown files\image-20211127172906495.png)

> Note: linear=translational motion

+ Reference line to measure 

  ![image-20211127173117884](C:\Users\15290\OneDrive - 厦门大学(马来西亚分校)\Desktop\markdown files\image-20211127173117884.png)

+  Compare $\theta$ and $d(displacement)$ within two different models 
  $$
  \ \theta= 5 \ rev \ (revolution)\\
     \theta=5*(2\pi)=10 \pi
  $$
  θ here can be taken as the path in the linear motions. The unit is rad.
  
+ Three diff. accelerations
  **tangential acceleration**(切向加速度)  $(rad/s^2)$
+ **versus radial accel**.（径向加速度）**/ centripetal accel.**(向心加速度)  $\rightarrow  have\ same\ Unit \ (m/s^2)$

<img src="C:\Users\15290\OneDrive - 厦门大学(马来西亚分校)\Desktop\markdown files\image-20211127173224452.png" alt="image-20211127173224452" style="zoom:67%;" />

+ Kinetic energy of rotation   

​    The kinetic energy is calculated differently because if we do it as it in the linear motion, about the center of rotation/center of mass, it equal zero.

So we should do it in diff way. <u>By the **Newton's first law**, we know that the inertia($I$) is proportional to mass</u>($m$).$*$ . So the moment of inertia be, too.(惯性和转动惯量)

$$
K={1\over2} \ I\ w^2
$$
$I= \sum (mr^2)$ (for discrete mass), where r stands for the  dist. betw. the com of each object to the axis of rotation.

+ Parallel-axis Theorem

$$
I=Icom+Mh^2
$$

where $I_{com}$  is the inertia about center of mass, $M$ is the mass of the whole body, $h$ is a dist. betw two parallel axes<u>(from one to the shifted one).</u>

> **Note**: when there is a "particle", we can always use $I=mr^2 $

<u>(need more explanation for the **Parallel-axis Theorem** here--added in 1st Dec.2021)</u>



####***Torque*: =change the rotational motions**

---

**Contributing Factors**：

+ magnitude of torque;
+ dist betw the $F$ and aixs of rotation/radius;
+ angle betw applied F and radius;  $\tau \ = F_{perp}* r(radius)$

+ some formula transformations 

$$
\tau = r\ F_t =r\ F sin\varphi= r_{\perp} F
$$

see also in the $Figure\ i$

<img src="C:\Users\15290\OneDrive - 厦门大学(马来西亚分校)\Desktop\markdown files\image-20211127174137234.png" alt="image-20211127174137234" style="zoom: 25%;" />

> **Note**: the clockwise is negative; counterclockwise is positive;



Similar to the linear motion model, Torque has is way to be well defined. Applied in the **Newton's Second Law for Rotation** the **net torque** is represented as 
$$
\tau = \alpha \ (angular\ accel.)*I
$$
comparing with $F=ma$, by Newton's First law $*$, the $m$ can be taken as $I$, $I \equiv m$. The units are the same as what is in the linear motion $N\ m$. 

 

####**Work done by the Torque**

----

 Another similarity between. $F$ and $\tau$ is the **work**.

> work done by the force:   $W=\int^{s_1}_{s_2}Fds$ 
>
> work done by the torque: $W=\int^{\alpha_1}_{\alpha_2}\tau d\alpha$ 



## Lecture 7 Rolling, Torque and Angular Momentum

---



#### -Rolling def:=$\downarrow$

- both rotation and translation
- no bumping or bouncing
- in contact with the surface 



#### - Rotational motion

the displacement of r.m. is $s=\theta R$, differentiate s w.r.t. t, we get $v_{rowing}=\omega R$, where $\omega$ is the rotational velocity.



#### - Three types of motions

- pure rotation
- pure translation
- combination of the two above: **Rolling motion**



> Scenario i

Two rolling disks,A and B, with the same energy, both of them are rolling from the same position. Suppose two disks move up an incline that is identical except that it is frictionless.  Which one gets the higher altitude at the peak?

> Scenario ii

A uniform ball rolls from rest down a ramp. Consider the velocity when the ball reaches the ground



#### - Angular momentum



$l=\vec{r}\ \times (cross-multiply)\ \vec{p}=m(r \times v ) $

$l$(angular momentum) is also a vector indeed.

prerequisites : linear algebra(calculate the determinates)

 













