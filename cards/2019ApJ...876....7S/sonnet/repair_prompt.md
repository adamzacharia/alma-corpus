# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...876....7S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version March 22, 2019
Preprint typeset using L [A] TEX style AASTeX6 v. 1.0


AN ANALYTICAL MODEL OF RADIAL DUST TRAPPING IN PROTOPLANETARY DISKS


Anibal Sierra [1], Susana Lizano [1], Enrique Mac´ıasFlock [2], Carlos [4] Carrasco-Gonz´alez [1], Mayra Osorio [3], Mario


1 Instituto de Radioastronom´ıa y Astrof´ısica, UNAM, Apartado Postal 3-72, 58089 Morelia Michoac´an, M´exico
2 Department of Astronomy, Boston University, 725 Commonwealth Avenue, Boston, MA 02215, USA
3 Instituto de Astrof´ısica de Andaluc´ıa (CSIC) Glorieta de la Astronom´ıa s/n E-18008 Granada, Spain
4 Max Planck Institute f˝ur Astronomy (MPIA), K˝onigsthul 17, 69117 Heidelberg, Germany


ABSTRACT


We study dust concentration in axisymmetric gas rings in protoplanetary disks. Given the gas surface
density, we derived an analytical total dust surface density by taking into account the differential
concentration of all the grain sizes. This model allows us to predict the local dust-to-gas mass ratio
and the slope of the particle size distribution, as a function of radius. We test this analytical model
comparing it with a 3D magneto-hydrodynamical simulation of dust evolution in an accretion disk.
The model is also applied to the disk around HD 169142. By fitting the disk continuum observations
simultaneously at _λ_ = 0 _._ 87, 1.3, 3.0 mm, we obtain a global dust-to-gas mass ratio _ϵ_ global = 1 _._ 05 _×_ 10 _[−]_ [2]

and a viscosity coefficient _α_ = 1 _._ 35 _×_ 10 _[−]_ [2] . This model can be easily implemented in numerical
simulations of accretion disks.

_Keywords:_ accretion disks     - dust migration     - protoplanetary disks     - stars: individual: HD 169142



1. INTRODUCTION


In the last few years, high quality (sub)mm observations of disks at high angular resolution have shown that
a significant fraction of them hosts one or more concentric rings and gaps (e.g. ALMA Partnership et al.
(2015), Andrews et al. (2018)). These radial structures
have been seen in both, the gas and the dust (e.g. Isella
et al. (2016)). Although their origin is still under debate
(see e.g. Carrasco-Gonz´alez et al. (2016) and references
therein), these structures must have a strong impact on
the evolution of the dust and gas. Ultimately, understanding this evolution is fundamental to figure out how
the formation of planetary systems takes place.
Dust grains migrate radially in protoplanetary disks
due to their interaction with the gas molecules: the radial pressure gradient felt by the gas is responsible for
the shear in the angular velocity between the dust grains
and the gas molecules, which causes an angular momentum interchange between both components via a drag
force. The dust radial velocity is proportional to the
radial pressure gradient (e.g. Whipple (1972), Weidenschilling (1977)). For a disk with decreasing density and
temperature radial profiles, the pressure gradient points
radially inward and causes a radial migration of the dust
grains toward the central star. In addition, the magnitude of the velocity depends on the size of the dust grains
(e.g., (Takeuchi & Lin 2002)). Small dust grains ( _∼_ _µ_ m)
are well coupled with the gas, and large grains with sizes



less than _∼_ 1 meter feel a strong drag force and are expected to accrete to the star in a timescale much less
than the lifetime of the gaseous disk, this problem is
known as the radial drift barrier, first discussed by Weidenschilling (1977).
If the gas pressure has local maxima, as in the case of
vortices (e.g., Barge & Sommeria (1995)) or rings (e.g.,
Pinilla et al. (2012)), the dust grains could be trapped,
avoiding or retarding their accretion toward the star,
promoting the appropriate conditions to build planetesimals.

Pohl et al. (2017) recently studied the disk around
HD 169142 where two main gaps, probably created by
Jupiter-mass planets, perturb the local gas and trap
dust grains in the outer zone of the gaps, where the
gas pressure has a maximum. Using their dust evolution model that includes migration and grain growth,
they can explain the 1 _._ 3 mm continuum emission of the
disk observed by Fedele et al. (2017), showing that the
millimeter grain sizes have had an important evolution
(migration + growth) within the disk. Pohl et al. also
modeled the population of small dust grains in order to
explain the dust scattering at near-IR wavelengths. This
small dust population is well mixed with the gas.
In this paper we study from an analytic point of view
how the dust grains could be trapped in axisymmetric
rings where the gas pressure has local maxima, and apply this model to the disk around HD 169142. In this

2


approach, the dust grains radially migrate toward the
pressure maxima and reach an equilibrium with the turbulent mixing which depends on the grain size, but they
do not grow. We do not address what creates the gas
gaps (which in turns creates the gas pressure maxima),
but we are only interested in the redistribution of dust
grains given the gas surface properties, i.e., the dust dynamics is only influenced by the drag force and turbulent
mixing. Possible gravitational interactions with planets
within the gaps are also ignored.
The structure of this paper is as follows: Section 2 describes the analytical model of dust concentration within
the gas pressure maxima based on the dust dynamics
within protoplanetary disks. Section 3 tests the analytical dust model by comparing it with recent dust and gas
disk simulations. This model is then used to describe the

dust emission of the disk around the HD 169142 star
(Section 4). The observational properties of the disk
are summarized in Subsection 4.1. In Subsection 4.2 we

derive a model for the HD 169142 gas surface density,
which is used together to the radiative transfer solution described in Subsection 4.3 in order to obtain the

dust surface density from a best fit model by comparing
with the disk emission at multi-wavelength millimeter
observations (Subsection 4.4). In Section 5 we discuss
the degeneration between the dust properties that can
produce the same observed value of the spectral index.
Conclusions are presented in Section 6.


2. ANALYTICAL MODEL


Dust grains can be described as a pressure-less fluid,
so their evolution in a thin disk can be followed by the
advection-diffusion equation



In the Epstein regime (where the radii of the dust
grains are smaller than 4/9 of the mean free path of the
gas), the radial dust velocity is given by (e.g., Windmark
et al. (2012))



_St_
_v_ _ϖ_ = � 1 + _St_ [2]



1
� ΩΣ g



_dP_
(3)
_dϖ_ _[,]_



where
_St_ = _[π][ρ]_ _[m]_ _[a]_ _,_ (4)

2Σ g


is the Stokes number of a dust grain with radius _a_ and
material density _ρ_ _m_, and _P_ = Σ g _c_ [2] _s_ [is] [the] [gas] [pres-]
sure, where _c_ _s_ is the sound speed. Assuming that the
dust diffusion coefficient is _D_ = _D_ g _/_ (1 + _St_ [2] ) (Youdin
& Lithwick 2007), where _D_ g = _αc_ [2] _s_ _[/]_ [Ωis] [the] [gas] [diffu-]
sion coefficient, Ωthe angular speed and _α_ the viscosity
coefficient, then, the Equation (2) can be written as



_St_
� _−_ _αc_ [2] _s_ Σ g



_._ (5)
�



_d_
0 =
_dϖ_



Σ d
� Σ g



_dP_

_dϖ_



Σ d
� Σ g



Neglecting the thermal gradients with respect to the
density gradients, [1] the solution of the above equation

is




[Σ] [d] [(] _[ϖ]_ [0] [)] _ϖ_

Σ g ( _ϖ_ 0 ) [exp] �� _ϖ_ 0



Σ d ( _ϖ_ ) [Σ] [d] [(] _[ϖ]_ [0] [)]
Σ g ( _ϖ_ ) [=] Σ g ( _ϖ_ 0 )



_ϖ_ 0



_St_



(Σ g ) _dϖ_ _,_ (6)

_dϖ_ �



_St_ _d_ ln(Σ g )


_α_ _dϖ_



where Σ d ( _ϖ_ 0 ) _,_ Σ g ( _ϖ_ 0 ) are the dust and gas densities at
a reference radius _ϖ_ 0 . Finally, the dust surface density
can be written as


Σ d ( _ϖ, a_ ) = _ϵ_ 0 Σ g ( _ϖ_ ) exp [ _−ka_ ] _,_ (7)


where



_,_ (8)
�



1 1
� Σ g ( _ϖ_ ) _[−]_ Σ g ( _ϖ_ 0 )



_∂_ Σ d Σ d

_∂t_ = _∇·_ (Σ d _⃗v_ ) _−∇·_ � _D_ Σ g _∇_ � Σ g



_,_ (1)
��



and _ϵ_ 0 is the dust-to-gas mass ratio at the reference
radius _ϖ_ 0 . Figure (1) shows the normalized dust
surface density for grains of different sizes _a_ [cm] =
10 _[−]_ [4] _,_ 10 _[−]_ [3] _,_ 10 _[−]_ [2] _,_ 10 _[−]_ [1] _,_ 10 [0], _α_ = 10 _[−]_ [2], and a gas surface density with two local maxima at _ϖ_ = 24 AU and
60 AU (black dashed line). This profile corresponds to
the gas surface density profile of HD 169142 discussed in
subsection 4.1 below. Note that the largest dust grains
are more concentrated around the first maxima. As the
radii of the grains decrease, the dust particles tend to be
well mixed with the gas. The grains with a size smaller
than 10 _[−]_ [3] cm (yellow dashed line) trace the gas surface
density.


1 For typical sound speed and gas surface density gradients,
_d_ ln _c_ [2] 2 _[/dϖ]_ _[∼−]_ [1] _[/]_ [2] [and] _[d]_ [ ln Σ] [g] _[/ϖ]_ _[∼−]_ [1,] [there] [would] [be] [an]
correction term of 3/2 in front of the second term in eq. (5).
However, for a disk with gaps, the difference tends to be larger
_|d_ ln Σ g _/dϖ| ≫|d_ ln _c_ [2] 2 _[/dϖ][|]_ [.]



_k_ = _[π][ρ]_ _[m]_

2 _α_



where _D_ _{_ cm [2] s _[−]_ [1] _}_ is the dust diffusion coefficient, Σ d
and Σ g are the dust and gas surface densities, respectively, and _⃗v_ = ( _v_ _ϖ_ _, v_ _φ_ ) is the dust velocity in cylindrical coordinates ( _ϖ, φ_ ). A steady state solution can
be reached if the flux of dust grains toward pressure
maxima is balanced by diffusion, in contrast with disks
where the pressure monotonically decreases with the radius and where the dust grains always migrate radially
inward. In an axisymmetric disk with local pressure
maxima, the steady state solution of Equation (1) is
given by



_._ (2)
�



_d_
0 = Σ d _v_ _ϖ_ _−_ _D_ Σ g _dϖ_



Σ d
� Σ g



This equation assumes that the dust follows the gas, i.e.,
that there is not back reaction of the dust on the gas.
This effect can be neglected if the dust-to-gas mass ratio
is less than 1 (e.g., Taki et al. (2016)).

3


strained by the total dust mass in the disk. If _ϵ_ global
is the global dust-to-gas mass ratio (typically _∼_ 1 _/_ 100),
then



1.0


0.8


0.6


0.4





�



_A_ [Σ] [d] [(] _[ϖ]_ [)] _[dA]_

_,_ (12)
_M_ g



�



_ϵ_ global =



� _A_ [Σ] [d] [(] _[ϖ]_ [)] _[dA]_

� _A_ [Σ] [g] [(] _[ϖ]_ [)] _[dA]_




[=]
_A_ [Σ] [g] [(] _[ϖ]_ [)] _[dA]_



where _M_ g is the total gas mass. Therefore, using Equation (11) one obtains



Σ g ( _ϖ_ )erf( _[√]_ ka max ) _ϖdϖ_
~~_√_~~ _ka_ max



� _−_ 1



�



_R_

_π_
� 0



0.2


0.0



_ϵ_ 0 = _ϵ_ global _M_ g



_,_



0



0 20 40 60 80 100

[AU]


**Figure** **1** . Normalized dust surface density for grains of different sizes.



(13)
where _R_ is the disk radius. Finally, replacing Equation
(13) in Equation (11) one obtains the total dust surface
density as a function of the gas surface density, the maximum grain size and the global dust-to-gas mass ratio

as



Equation (7) can also be written as



_._

�



Σ g erf( _[√]_ ka max ) _/_ _[√]_ ka max
� � 0 _R_ [Σ] [g] [erf(] ~~_[√]_~~ [ka] [max] [)] _[/]_ ~~_[√]_~~ [ka] [max] _[ϖ]_ [d] _[ϖ]_



_ϵ_ ( _ϖ, a_ ) _/ϵ_ 0 _∝_ exp[ _−_ 1 _/_ Σ g ( _ϖ_ )] _,_ (9)


where _ϵ_ ( _ϖ, a_ ) is the local dust-to-gas mass ratio. Therefore the local dust to gas mass ratio follows the gas extrema (maxima or minima). Equation (7) also predicts
that the gaps in the dust surface density are deeper than
in the gas surface density. Note that, because the dust
mass is conserved, the maxima are enhanced due to the
redistribution of the dust grains.
The total dust surface density is given by the sum of
the dust densities for each grain size. For a dust size
distribution where _n_ ( _a_ ) _da_ _∝_ _a_ _[−][p]_ _da_ is the number of
dust grains per unit volume with a radius between _a_ and
_a_ + _da_, with minimum and maximum grain sizes, _a_ min
and _a_ max, respectively, the total dust surface density is



Σ d ( _ϖ_ ) = _[ϵ]_ [g][lobal] _[M]_ [g]

2 _π_



(14)
This equation gives the dust surface density when the
gas surface density in axisymmetric rings is known.
Since the gas surface density evolves in a diffusion
timescale which is much longer than the advection
timescale of the dust (See Appendix B), the dust will
always concentrate following the gas maxima.
Recently, Dullemond et al. (2018) proposed a dust
model that assumes that the gas pressure maxima are
given by gaussian functions. To obtain the dust surface
density of grains with a single size, they assume locally
a maximum gas surface density given by Toomre stability criterion. Instead, our model uses a gas profile
that can be obtained from observations or simulations.

Given this profile, it predicts the total dust surface density taking into account the differential concentration of
all grain sizes. For non-axisymmetric disks, Sierra et al.
(2017) modelled the total dust concentration in disk vortices taking into account the distribution of dust grains

sizes.


3. APPLICATION OF THE MODEL TO A

NUMERICAL SIMULATION


Flock et al. (2015), Ruge et al. (2016) performed nonideal 3D magneto-hydrodynamical simulations of a protoplanetary disk where they followed the dynamics of
dust particles of different sizes. As expected, they found
that the largest grains tend to be more concentrated
around the pressure maxima. In this section we compare the dust surface density from the simulation for
each grain size with that predicted by our analytic dust
model (Equation 7). Then, the gas surface density that
appears in the dust model equation is given by the azimuthally averaged gas density profile from the simula
tion.



Σ d ( _ϖ_ ) =



� _aa_ minmax [Σ] [d] [(] _[ϖ, a]_ [)] _[a]_ [3] _[n]_ [(] _[a]_ [)] _[da]_
� _aa_ minmax _[a]_ [3] _[n]_ [(] _[a]_ [)] _[da]_ _._ (10)



In this equation, the factor _a_ [3] _n_ ( _a_ ) _da_ weights the
amount of mass associated to each dust grain size, which
is assumed to be constant because the dust grains are
only redistributed in the disk without coagulation or
fragmentation. In addition, the redistribution of the
dust grains is taken into account by the factor Σ d ( _ϖ, a_ ),
which includes the dust size differential migration, see
Figure (1). [2] Thus, the integral can be computed using
the global values of the disk ( _a_ max _, p_ ).
In particular, if the original value of the particle size
distribution is _p_ = 3 _._ 5 and _a_ max _≫_ _a_ min, the integral is

Σ d ( _ϖ_ ) = _ϵ_ 0 Σ g erf( ~~�~~ ka max ) _,_ (11)
2 ~~_[√]_~~ _ka_ max



where erf is the error function. Furthermore, _ϵ_ 0 is con

2 The local changes in the particle size distribution are discussed
in Section (5).

4


0.200


0.175


0.150


0.125


0.100


0.075


0.050


0.025


5.0 4.5 4.0 3.5 3.0 2.5 2.0 1.5 1.0

log( )


**Figure** **2** . Error estimation between the analytic model and
simulations as a function of _α_ .


We choose a snapshot of the simulation at a time of
400 inner orbits of the disk. At this time the gas surface
density has developed a ring structure without vortices [3],
and the dust grains have had enough time to concentrate in the ring following the drag force of the gas. The
gas density profile has a local maximum (ring) centered
at 65 AU. We consider the gas density profile between
55 to 85 AU, where the radial drift has stopped and the
dust has achieved a steady state.
The concentration of the dust surface density depends on the assumed value of the viscosity coefficient
_α_ (Equation 8) which is found from the best fit model
by minimizing the function






|10<br>.<br>08<br>.<br>06 . norm<br>)d,<br>04 (<br>.<br>02<br>.|mod, a = 0 .05 cm<br>sim, a = 0 .05 cm<br>mod, a = 0 .09 cm<br>sim, a = 0 .09 cm<br>mod, a = 1 .0 cm<br>sim, a = 1 .0 cm|mod, a = 0 .05 cm<br>sim, a = 0 .05 cm<br>mod, a = 0 .09 cm<br>sim, a = 0 .09 cm<br>mod, a = 1 .0 cm<br>sim, a = 1 .0 cm|Col4|
|---|---|---|---|
|0.0|0.0|0.0||



�


_a_



_σ_ [2] = [1]

_N_ _a_



1

_N_ _p_



�


_ϖ_



2
�Σ [sim] d _,_ norm [(] _[ϖ, a]_ [)] _[ −]_ [Σ] d [mod] _,_ norm [(] _[ϖ, a]_ [)] � ;



(15)
where _N_ _a_ is the number of dust particle sizes, and _N_ _p_
is the number of radial points sampled, Σ [mod] d _,_ norm [is] [the]
normalized dust surface density profile of the model,
and Σ [sim] d _,_ norm [is the normalized azimuthally-averaged dust]
density profile of the simulation.
The sum over _ϖ_ compares the radial profiles and the
sum over _a_ take into account all the grain sizes, which
vary from 50 _µ_ m to 1 _._ 0 cm in 10 logarithmically equally
spaced bins. Figure (2) shows _σ_ [2] as a function of _α_ . The
minimum is obtained for _α_ _b_ = 1 _._ 3 _×_ 10 _[−]_ [3], which is of the
same order of magnitude of the averaged value, 3 _×_ 10 _[−]_ [3],
found in the simulation. The value of dust-to-gas mass
ratio _ϵ_ 0 is not fitted because the dust particles included
in the simulation are only a representative sample of the
total dust mass; that is the reason why we compare the
normalized dust surface densities.
Figure (3) shows the normalized surface densities from
the model (solid lines) and the simulation (dotted lines)


3 The azimuthal fluctuations of the gas surface density in the
ring with respect to the azimuthal average are smaller than 6%.



60 65 70 75 80

[AU]


**Figure** **3** . Normalized surface density from the model (solid
lines) and the simulation (dotted lines) for grains with sizes
_a_ = 0 _._ 05 cm (red line), 0 _._ 09 cm (green line) and 1 _._ 0 cm (blue
line).


using the viscosity coefficient _α_ _b_ and for three representative dust grain sizes: _a_ = 0 _._ 05 cm (red line), 0 _._ 09 cm
(green line), and 1 _._ 0 cm (blue line). In all cases the
width of the model profiles match the simulation profiles.


4. APPLICATION OF THE MODEL TO HD 169142


In this section we applied the analytical model (Equation 14) that gives the dust surface density Σ _d_ ( _ϖ_ ) to
simultaneously explain the millimeter dust emission of
the disk around HD 169142 at different wavelengths
_λ_ = 0 _._ 87 _,_ 1 _._ 3 _,_ 3 _._ 0 mm, using the observed gas proper
ties.

Subsection 4.1 summarizes the observed properties of

the central star and the disk in this source. In subsection

4.2 we derive the disk gas surface density and excitation
temperature from the [12] CO and [13] CO maps. These disk
gas properties are used in the analytical model to predict
the dust surface density, in order to determine the best
fit values for the global dust-to-gas mass ratio ( _ϵ_ global )
and the viscosity coefficient ( _α_ ). We choose the parameters that minimize the reduced chi-squared of the dust
continuum emission of the observed dust maps and the
emission of a grid of models. Subsection 4.3 describes
how to compute the emergent specific intensity of the
models and subsection 4.4 presents the results for the
best values of _ϵ_ global and _α_ .


4.1. _HD_ _169142_


HD 169142 is a Herbig Ae star (The et al. 1994) in the
Sagittarius constellation with an age of 10 Myr (Pohl et
al. 2017), a mass of _M_ _∗_ = 1 _._ 65 _M_ _⊙_ (Blondel & Djie 2006)
with an effective temperature _T_ _∗_ = 8100 K, a star radius
of _R_ _∗_ = 2 _._ 2 _R_ _⊙_ (Osorio et al. 2014), and at a distance
of _d_ = 117 _±_ 4 pc (Gaia Collaboration et al. 2016). The
disk around HD 169142 is seen almost face-on, with an
inclination angle of _∼_ 14deg (cos _i_ = 0 _._ 974), and with its

5



major axis along a position angle P.A. = 5 deg (Raman
et al. 2006) on the plane of the sky.
IR-polarized scattered-light images (Quanz et al.
2013) revealed that the disk has a central cavity, surrounded by a bright rim of radius _∼_ 0 _._ 21 _[′′]_ ( _∼_ 25 AU
at 117 pc), and an annular gap ranging from _∼_ 0 _._ 28 _[′′]_ 0 _._ 48 _[′′]_ ( _∼_ 33-56 AU) in radius. An unresolved IR source
was detected inside the central cavity (Biller et al. 2014,
Reggiani et al. 2014) at a radius of _∼_ 0 _._ 16 _[′′]_ (19 AU) and
was interpreted as a substellar or planetary companion
candidate. The dust thermal emission of the disk was
first imaged with the VLA at 7 mm (Osorio et al. 2014,
Mac´ıas et al. 2017). These 7 mm observations confirmed
the IR results and revealed that the ring of radius 25
AU is indeed narrow and azimuthally asymmetric, with
a bright knot at PA= _−_ 40 deg. These 7 mm images also
suggest the presence of a possible new gap at radius _∼_
85 AU, located very close to the CO snowline, as imaged
from DCO [+] ALMA data (Mac´ıas et al. 2017). Finally,
the VLA observations revealed a compact source of ionized material near the center of the cavity that could be
tracing a weak radio jet, a photoionized inhomogeneous
region of the inner disk, or an independent orbiting object.
The HD 169142 disk has been observed with ALMA
at _λ_ = 0 _._ 87 mm, 1 _._ 3 mm, and 3 mm (archival data from
program 2012.1.00799.S, Fedele et al. 2017, and Macias
et al. in prep. respectively). The submillimeter and
millimeter continuum ALMA maps of the dust nicely
confirmed the ringed structure of the disk initially revealed by the infrared polarized images and the 7 mm
observations. The line emission of the gas has been observed with ALMA using [12] CO, [13] CO, C [18] O _J_ : 2 _→_ 1
rotational transitions by Fedele et al. (2017).
In all the cases, the contrast between the rings and the
gaps in the line emission maps is weaker than in the continuum maps. For the [12] CO this could be a consequence
of the line emission being optically thick. However, the
13 CO emission, that is usually optically thin, also shows
a smaller contrast compared to the dust emission; this
behavior is similar to the dust model described in Sec
tion 2. Also, the line emission extends to a radius of
_∼_ 240 AU, significantly larger than the radius inferred
from the dust continuum emission, which only extends
to _∼_ 100 AU. This difference could be explained by the
radial dust migration (e.g., Brauer et al. (2008)).
Figure (4) shows the normalized azimuthally-averaged
specific intensity of the dust continuum emission at
_λ_ = 870 _µ_ m (red solid line), 1 _._ 3 mm (yellow dash-dotted
line), and 3 mm (green dashed line) [4] . It also shows


4 Table C1 shows the parameters of the images at each wavelength.


|= 0 .87 mm<br>= 1 .3 mm<br>= 3 .0 mm<br>13CO(J : 2 1)<br>12CO(J : 2 1)<br>Gas beam<br>Dust beam|Col2|
|---|---|
|Dust beam<br>Gas beam<br>= 0.87 mm<br>= 1.3 mm<br>= 3.0 mm<br>13CO(J : 2<br>1)<br>12CO(J : 2<br>1)||



_T_ ex = _hν/k_ _B_ _,_ (17)

_hν/k_ _B_
ln �1 + _T_ 0 [12] [+] _[J]_ [ 12] [(2] _[.]_ [7K)] �



1.0


0.8


0.6


0.4


0.2


0.0







0 25 50 75 100 125 150 175 200

[AU]


**Figure** **4** . Normalized HD 169142 specific intensities as a
function of disk radius. The continuum dust emission at _λ_ =
0 _._ 87 _,_ 1 _._ 3 _,_ and 3 _._ 0 mm are represented by the red solid line,
yellow dash-dotted line, and green dashed line respectively.
The line gas emission of the [13] CO and [12] CO molecules are
the cyan solid line and the blue dash-dotted line respectively.
The dust emission maps have been convolved to a beam f 0.2
arcsec, while the gas maps were convolved to a beam of 0.16
arcsec (bottom left bars).


the normalized azimuthally-averaged profiles the [13] CO
_J_ : 2 _→_ 1 (cyan solid line) and the [12] CO _J_ : 2 _→_ 1
(blue dash-dotted line) line emission. All the dust maps
were convolved to the same circular beam of 0.20 arc
sec, while the gas maps have a circular beam of 0.16
arcsec. These beams are equivalent to 23 _._ 4 and 18 _._ 7 AU
at the assumed distance of 117 pc respectively. Note
that, since the dust analytical model depends on the
gas surface density (Equation 14), the model can only
resolve dust structures with the angular resolution of
the gas maps; this is the reason why we choose a higher
angular resolution in the gas; however, prior to compare
the dust properties from the observations and the analytic model, we convolve the analytic dust model such
that the final beam coincide with the observations.


4.2. _Gas_ _surface_ _density_


The gas surface density can be inferred using both
an optically thin and an optically thick line. We use
the _J_ : 2 _→_ 1 lines and assume that [12] CO is optically
thick and the [13] CO is optically thin. The [13] CO column
density for the _J_ : 2 _→_ 1 rotational transition (e.g.
Estalella & Anglada (1994)) is given by



_N_ [13CO] = _c_ 0 _τ_ 0 [13] _[T]_ [ex] [∆] _[v]_ � exp [exp[ _hν/_ 3 _hν_ ( _/k_ ( _B_ 2 _Tk_ ex _B_ _T_ )] ex _−_ )]1



_,_ (16)
�



where _c_ 0 = 16 _πk_ _B_ _ν_ [2] _J/_ [(2 _J_ +1) _hc_ [3] _A_ _J,J−_ 1 ], _h, k_ _B_ are the
Planck and Boltzmann constants, ∆ _v_ is the line width
and _ν_ = 230 GHz, _A_ 2 _,_ 1 = 3 _._ 25 _×_ 10 _[−]_ [7] s _[−]_ [1] are the frequency and the Einstein coefficient for this transition,
respectively. The excitation temperature _T_ ex is given by

6



15


10


5


0


1.5


1.0


0.5


1.0





4.3. _Dust_ _properties_ _and_ _radiative_ _transfer_ _model_


The emergent specific intensity is given by



_τ_ _ν_
_I_ _ν_ = _I_ _ν_ [bg] _[e]_ _[−][τ]_ _[ν]_ [+] _S_ _ν_ ( _T_ ) _e_ _[−][t]_ _dt_ (19)
� 0



0.5


0.0

|Col1|Col2|
|---|---|
|||
|= 0.87mm<br>= 1.3mm<br>= 3.0mm|= 0.87mm<br>= 1.3mm<br>= 3.0mm|



0 20 40 60 80 100

[AU]


**Figure** **5** . HD 169142 disk properties. Top panel: Gas surface density model derived from the assumed [12] CO (optically
thick) and [13] CO (optically thin) emission. Middle panel:
Spectral index _β_ (between _λ_ = 870 _µ_ m and 3 mm) of the
dust emission . Bottom panel: Optical depth at _λ_ = 0 _._ 87
mm (magenta solid line), 1.3 mm (green dash-dotted line),
and 3.0 mm (red dashed line).


where _T_ 0 [12] is the brightness temperature of the [12] CO
J: 2 _→_ 1 line, _J_ _ν_ ( _T_ ) = ( _hν/k_ ) _/_ (exp( _hν/kT_ _−_ 1) is the
intensity in units of temperature, and _J_ [12] (2 _._ 7K) is the
intensity at the frequency of the [12] CO J: 2 _→_ 1 evaluated at the background temperature. Finally, the optical depth of the [13] CO J: 2 _→_ 1 line ( _τ_ 0 [13] [)] [is] [given] [by]



where _I_ _ν_ [bg] is the background intensity, _τ_ _ν_ = ( _κ_ _ν_ + _σ_ _ν_ )Σ _d_
is the optical depth at the frequency _ν_, where _κ_ _ν_ is the
mass absorption coefficient and _σ_ _ν_ is the mass scattering coefficient. The source function _S_ _ν_ ( _T_ ) is given by
(Mihalas 1978)


_S_ _ν_ ( _T_ ) = _ω_ _ν_ _J_ _ν_ + (1 _−_ _ω_ _ν_ ) _B_ _ν_ ( _T_ ) _,_ (20)


where the albedo is _ω_ _ν_ = _σ_ _ν_ _/_ ( _κ_ _ν_ + _σ_ _ν_ ), _B_ _ν_ ( _T_ ) is the
Planck function, and _J_ _ν_ is the local mean intensity.
We approximate _J_ _ν_ by the analytical solution found by
Miyake & Nakagawa (1993) (hereafter MI93) for a vertically isothermal slab. Then, the source function can
be written as


_S_ _ν_ ( _T_ ) = _B_ _ν_ ( _T_ ) [1 + _ω_ _ν_ _f_ ( _t, τ_ _ν_ _, ω_ _ν_ )] _,_ (21)


where



_τ_ _ν_ is the total optical depth and _t_ is the variable optical depth, both measured perpendicular to the disk mid
plane, and
_ϵ_ _ν_ = _√_ 1 _−_ _ω_ _ν_ _._ (23)


For a face-on and vertically isothermal disk, the solution
of Equation (19) using Equations (21)-(23) and setting
_I_ _ν_ [bg] = 0 is


_I_ _ν_ = _B_ _ν_ ( _T_ ) [(1 _−_ exp( _−τ_ _ν_ )) + _ω_ _ν_ _F_ ( _τ_ _ν_ _, ω_ _ν_ )] _,_ (24)


where



_√_
_f_ ( _t, τ_ _ν_ _, ω_ _ν_ ) = [ex][p(] _[−]_



3 _ϵ_ _ν_ _t_ ) + exp( _√_




[(22)]
3 _ϵ_ _ν_ _τ_ _ν_ )( _ϵ_ _ν_ _−_ 1) _−_ ( _ϵ_ _ν_ + 1) _[,]_



_√_ 3 _ϵ_ _ν_ _t_ ) + exp( _√_ 3 _ϵ_ _ν_ ( _t −_ _τ_ _ν_ ))

[ex][p(] _[−]_

exp( _−_ ~~_√_~~ 3 _ϵ_ _ν_ _τ_ _ν_ )( _ϵ_ _ν_ _−_ 1) _−_ ( _ϵ_ _ν_ + 1)



_τ_ 0 [13] = _−_ ln �1 _−_ _J_ [13] ( _T_ ex ) _−JT_ 0 [13] [13] (2 _._ 7K)



_,_ (18)
�



where _T_ 0 [13] is the brightness temperature of the [13] CO
J: 2 _→_ 1 line, and _J_ [13] ( _T_ ex ) is the intensity evaluated
at the excitation temperature. We find that _τ_ 0 [13] _<_ 0 _._ 8
throughout the disk.
To obtain the gas surface density at each radius
13
one needs an abundance factor between CO and
H 2 (which dominates the gas mass), such that Σ g =
_m_ H 2 [H 2 _/_ [13] CO] _×_ N [13CO] . The abundance is obtained by
normalizing the gas surface density with the total mass
_R_
of the disk _M_ disk = 2 _π_ � 0 [Σ] [g] _[ϖdϖ]_ [.] [For] [a] [disk] [mass] [of]
_M_ disk = 0 _._ 019 _M_ _⊙_ (Fedele et al. 2017), the abundance
between the [13] CO and the H 2 molecules of [ [13] CO/H 2 ]
= 1 _._ 0 _×_ 10 _[−]_ [5], similar to values found in the ISM (e.g.
Dickman (1978)).
The top panel of Figure (5) shows the gas surface density model as a function of the radius. The width of the
line gives the uncertainty in the gas surface density due
to the noise of the CO maps and the error propagation.
In the next section we use this gas surface density to
model the dust surface density using Equation (14).



_ω_ _ν_
_I_ _ν_ [thick] = _B_ _ν_ ( _T_ ) 1 _−_
� ( _ϵ_ _ν_ + 1)( ~~_√_~~



1
_F_ ( _τ_ _ν_ _, ω_ _ν_ )=
exp( _−_ ~~_√_~~ 3 _ϵ_ _ν_ _τ_ _ν_ )( _ϵ_ _ν_



exp( _−_ ~~_√_~~ 3 _ϵ_ _ν_ _τ_ _ν_ )( _ϵ_ _ν_ _−_ 1) _−_ ( _ϵ_ _ν_ + 1) _[×]_


1 _−_ exp( _−_ ( _√_ 3 _ϵ_ _ν_ + 1) _τ_ _ν_ )

~~_√_~~ 3 _ϵ_ _ν_ + 1

�



_−_ ( _√_ 3 _ϵ_ _ν_ + 1) _τ_ _ν_ )

~~_√_~~ 3 _ϵ_ _ν_ + 1



3 _ϵ_ _ν_ + 1



_√_
+ [ex][p(] _[−][τ]_ _[ν]_ [)] _[ −]_ [ex][p(] _[−]_



�



_._ (25)




_[ −]_ [ex][p(] _[−]_ _√_ 3 _ϵ_ _ν_ _τ_ _ν_ )

~~_√_~~ 3 _ϵ_ _ν_ _−_ 1



3 _ϵ_ _ν_ _−_ 1



Then, in the optically thin regime, the emergent intensity is


_I_ _ν_ [thin] = _B_ _ν_ ( _T_ ) _τ_ _ν_ (1 _−_ _ω_ _ν_ ) = _B_ _ν_ ( _T_ ) _κ_ _ν_ Σ d _,_ (26)


independent of the albedo (see MI93). In the optically
thick regime, the emergent intensity is



3 _ϵ_ _ν_ + 1)



_,_ (27)
�



consistent with the discussion in D’Alessio et al. (2001)
(hereafter DA01).

7



We assume a power-law dust temperature



10 [2]


10 [1]




_[β]_





_−q_
_,_ (28)
�



_T_ d = _T_ 0



_ϖ_
� _ϖ_ 0



where _T_ 0 = 500 K at _ϖ_ 0 = 1 AU and _q_ = 1 _/_ 2. This
slope is estimated by assuming an equilibrium between
the star incident radiation and the dust grains emission,
such that _T_ d [4] _[≈]_ _[T]_ [ 4] _∗_ _[W]_ [(] _[ϖ]_ [),] [where] _[W]_ [(] _[ϖ]_ [)] [is] [the] [dilution]
factor given by _W_ ( _ϖ_ ) = 1 _/_ 2(1 _−_ [1 _−_ ( _R_ _∗_ _/ϖ_ ) [2] ] [1] _[/]_ [2] ), and
_T_ _∗_ _, R_ _∗_ are the effective temperature and radius of the
star respectively (Subsection 4.1). Since a large dust
central hole has been previously reported in the disk
around HD 169142 (e.g. Fedele et al. 2017, Mac´ıas et
al. 2017), the inner and outer dust radius are set to be
15 AU and 90 AU respectively.
The monochromatic opacity ( _χ_ _ν_ = _κ_ _ν_ + _σ_ _ν_ ) and
albedo are computed with the code of (DA01) for a dust
composition of silicates, organics, and ice with the relative abundances described by Pollack et al. (1994). In
this code, the total dust opacity is given by



10 [0]


10 1


(red dashed line).



appears in Equation (24), _τ_ _ν_ = _τ_ 0 ( _ν/ν_ 0 ) _[β]_, where _τ_ 0 is
the optical depth at a reference frequency _ν_ 0 .
The middle panel of Figure (5) shows _β_ derived from
the dust continuum observations following the latter
procedure, without assuming optically thin emission nor
the Rayleigh-Jeans approximation, and including the
mass scattering opacity. The width of the curve represents the error in the fit. The error is negligible for
_ϖ_ _<_ 80 AU, where the signal-to-noise ratio in the dust
emission maps is high. The bottom panel of the same
Figure shows the optical depth at _λ_ = 870 _µ_ m (magenta
solid line), 1.3 mm (green das-dotted line), and 3.0 mm
(red dashed lin): the disk is optically thin at _λ_ = 1 _._ 3mm
and 3 _._ 0 mm; it is only marginally thick close to the two
maxima at _λ_ = 870 _µ_ m.
Figure (6) shows the maximum grain size, _a_ max ( _ϖ_ ),
as a function of the disk radius assuming a slope of the
particle size distribution of _p_ = 2 _._ 5 (magenta solid line),
3 _._ 0 (green dash-dotted line), and 3 _._ 5 (red dashed line)
(see more details in Appendix A). In the following we
assume _p_ = 3 _._ 5 and in Section (5) we discuss this assumption.
We find that _a_ max ( _ϖ_ ) is very large at the position of
the first maximum and decreases with the disk radius,
reaching a value of _∼_ 2 mm at _ϖ_ = 90 AU. This behavior could be due to differential radial migration of
the dust grains toward the gas pressure maxima and/or
dust growth.


4.4. _Best_ _fit_ _dust_ _model_


The dust-to-gas mass ratio _ϵ_ global and the _α_ parameter
that appear in Equations (8) and (14) are the unknown
parameters of the dust model.
These parameters are fitted by creating a grid of
models and comparing their radial intensity profiles
( _I_ _λ_ [mod] ( _ϖ_ )) with the observed azimuthally averaged intensity profiles ( _I_ _λ_ [obs] ( _ϖ_ )) at each wavelength. We vary



_χ_ _ν_ =



_a_ max ( _ϖ_ )
� a min _χ_ _ν_ ( _a_ ) _n_ ( _a_ ) _da_
_a_ max ( _ϖ_ ) _,_ (29)
� a min _n_ ( _a_ ) _da_



where _χ_ _ν_ ( _a_ ) is the opacity of each dust grain size
at frequency _ν_, and the particle size distribution has
_n_ ( _a_ ) _da_ _∝_ _a_ _[−][p]_ _da_ with _p_ = 3 _._ 5, the minimum grain size
is _a_ min = 0 _._ 05 _µ_ m, and the maximum grain size _a_ max ( _ϖ_ )
depends on the disk radius. The opacity and albedo
curves as a function of the wavelength for different dust
size distributions are shown in Figures 9 and 10 of Sierra
et al. (2017).
To determine the maximum grain size, _a_ max ( _ϖ_ ), one
has to fit a power-law to the observed intensity _I_ _ν_ . This
comes from the following considerations: in the optically thin limit and, including only the mass absorption coefficient _κ_ _ν_, _I_ _ν_ _∝_ _κ_ _ν_ _B_ _ν_ ( _T_ ). Also, at low frequencies, the Planck function can be approximated as
_B_ _ν_ ( _T_ ) = _ν_ [2] _kT/_ 2 _c_ [2] (Rayleigh-Jeans regime), and the
opacity is given by a power-law of the frequency _κ_ _ν_ _∝_ _ν_ _[β]_

(Beckwith et al. 1990). Then the specific intensity will
follow a power-law of the frequency as _I_ _ν_ _∝_ _ν_ [2+] _[β]_ . In
general, _β_ will be a function of radius. Since, for a
given slope _p_ of the dust size distribution, _β_ depends on
the maximum grain radius (e.g., Ossenkopf & Henning
(1994); Pollack et al. (1994)), one can find _a_ max ( _ϖ_ ) at
each radius [5] . Nevertheless, one can avoid the assumptions of optically thin emission and the Rayleigh-Jeans
regime, and include the scattering mass opacity _σ_ _ν_ in
the total opacity, _χ_ _ν_ = _κ_ _ν_ + _σ_ _ν_ . In this case, the parameter _β_ can be derived from the optical depth that


5 See discussion about on the degeneracy between _a_ max and the
slope _p_ in Section 5.

8


**Table** **1** . Best physical parameters


_λ_ (mm) _α/_ 10 _[−]_ [2] _ϵ_ global _/_ 10 _[−]_ [2]


0.87 1.26 1.05


1.3 1.53 1.05


3.0 1.26 1.05


_α_ from 10 _[−]_ [5] to 10 _[−]_ [1], while _ϵ_ global varies from 10 _[−]_ [4] to
10 _[−]_ [1] . The number of models for each parameter is 50
(the total number of models is 50 _×_ 50) and the values
are logarithmically equally spaced. The top panels of
Figure (7) show the reduced chi-squared



the non-axisymmetric structures, which are not taken
into account in the dust model.
For the best averaged parameters, Figure (10) shows
the dust surface density (the red solid line), the local
dust-to-gas mass ratio (green dashed line), the global
dust-to-gas mass ratio _ϵ_ global (green dotted line), and the
gas surface density scaled by the global dust-to-gas mass
ratio (blue dash-dotted line). The latter would mimic
the dust surface density if there is no dust migration,
which is not the case in HD 169142. The local dust
to-gas mass ratio in the first maximum increases by a
factor of 6 compared with the global dust-to-gas mass
ratio; while in the second local maximum it is below
the average value. In addition, this figure shows that
the maximum dust-to-gas mass ratio is less than 0.06,
therefore, one can neglect the back reaction of the dust
on the gas.
The amplitude of the dust surface density in the second maximum ( _ϖ_ = 60 AU) is much smaller than in
the first maximum ( _ϖ_ = 24 AU), in contrast with the
behaviour of the intensity profiles (bottom panels of Figure (7)); this occurs because of opacity effects associated
to the maximum grain size at each radius: In the first
maximum, the grains have a maximum size larger than
10 cm; such grains do not have a large opacity at millimeter wavelengths. However, in the second maximum,
the grains have a maximum size _∼_ 2 mm, which have a
large opacity at millimeter wavelengths. For this reason,
the contrast in the maxima of the dust surface density
is larger than expected. Appendix A explains the effect
of the maximum grain size in the opacity for different
slopes of the particle size distribution.


5. _A_ MAX _, P_ DEGENERATION


In this section we study the local changes of the particle size distribution due to dust size differential migration. This effect has been already found by e.g. Pinte
et al. (2016), Sierra et al. (2017).
The model to obtain the slope _p_ as a function of the
disk radius based on the results of the analytical model
(Section 2) as follows: If the total dust surface density
is given by Equation (10), the term Σ d ( _ϖ, a_ ) _n_ ( _a_ ) _da_ can
be interpreted as proportional to the local particle size
distribution after dust concentration. If _n_ 2 ( _a_ ) _da_ is this
new distribution and _c_ 1 the proportionality factor, then,


_n_ 2 ( _a_ ) _da_ = _c_ 1 Σ d ( _ϖ, a_ ) _n_ ( _a_ ) _da._ (32)



2

_,_ (30)
�



_χ_ [2] _r,λ_ [=] _N_ [1] _p_



�


_ϖ_



I mod _λ_ ( _ϖ_ ) _−_ I [obs] _λ_ [(] _[ϖ]_ [)]
� _σ_ _λ_ [obs] [(] _[ϖ]_ [)]



of the dust models at _λ_ = 870 _µ_ m (left panel), 1 _._ 3 mm
(middle panel), and 3 _._ 0 mm (right panel), where _N_ _p_ is
the number of radii and _σ_ _λ_ [obs] [(] _[ϖ]_ [) is the uncertainty of the]
observed intensity at each radius. The latter is given by


_σ_ _λ_ [obs] [(] _[ϖ]_ [) = RMS] _[λ]_ _[/][√][n][,]_ (31)


where RMS _λ_ is the root mean square noise of the observed map, and _n_ is the number of beams within the
area of each ring. The bottom panels show the intensity
profiles of the best dust models (red solid line), the optical depth models (green dashed line), and the observed
intensity profiles (blue line) whose error is given by the
width of the line.
Figure (8) plots the isocontours where the value of
the reduced chi-squared is 1.5 times the minimum value
of _χ_ [2] _r,λ_ [for] [all] [wavelengths:] _λ_ = 870 _µ_ m (red solid
line), 1 _._ 3 mm (green dashed line), and 3 _._ 0 mm (blue
dash-dotted line). The best parameters at each wavelength are summarized in Table (1). To obtain a global
model, one requires that the parameters do not depend
on wavelength. The best values for _ϵ_ global are the same,
and the best values of _α_ slightly differ with wavelength.
Therefore, the best averaged parameters that describe
the dust concentration in the disk of HD 169142 are:
_ϵ_ global = 1 _._ 05 _×_ 10 _[−]_ [2] and _α_ = 1 _._ 35 _×_ 10 _[−]_ [2] ; this means
that the total dust mass is 2 _._ 0 _×_ 10 _[−]_ [4] _M_ _⊙_ .
Note that the fitted value of _α_ depends on the resolution of the gas structure. For example, if in higher
angular resolution observations a ring fragments into
thinner rings, that would require a smaller value of _α_
to concentrate the dust in these rings.
Figure (9) shows the disk maps for different wavelengths; the left panels are the observed maps, the middle panels show the emission of the dust model with
the best averaged parameters, and the right panels are
the maps of absolute differences ( _|_ observation _−_ model _|_ ).
The wavelength increases from top to bottom ( _λ_ =
870 _µ_ m, 1 _._ 3 mm, 3 mm respectively). Note that the
main difference between the observations and model are



_A_
_c_ 1 = (33)
� _A_ [Σ] [d] [(] _[ϖ, a]_ [)] _[dA.]_



The number of particles per unit volume must be the
same as the original when averaged in all the disk area
_A_ ; then � _A_ _[n]_ [2] [(] _[a]_ [)] _[da dA]_ [ =] � _A_ _[n]_ [(] _[a]_ [)] _[da dA]_ [.] [So,] [the] [propor-]



_A_ _[n]_ [2] [(] _[a]_ [)] _[da dA]_ [ =] �



_A_ ; then � _A_ _[n]_ [2] [(] _[a]_ [)] _[da dA]_ [ =] � _A_ _[n]_ [(] _[a]_ [)] _[da dA]_ [.] [So,] [the] [propor-]

tionality factor is constrained by

9



-1.08
-1.24
-1.41
-1.57
-1.73
-1.9

-2.06
-2.22
-2.39
-2.55
-2.71
-2.88
-3.04
-3.2

-3.37
-3.53
-3.69
-3.86
-4.02
-4.18
-4.35
-4.51
-4.67
-4.84
-5.0


0.025


0.020


0.015


0.010


0.005


0.000



log( global )





log( global )



log( global )





-1.08
-1.24
-1.41
-1.57
-1.73
-1.9

-2.06
-2.22
-2.39
-2.55
-2.71
-2.88
-3.04
-3.2

-3.37
-3.53
-3.69
-3.86
-4.02
-4.18
-4.35
-4.51
-4.67
-4.84
-5.0





4.0


3.5


3.0



2.5


2.0


1.5



-1.08
-1.24
-1.41
-1.57
-1.73
-1.9

-2.06
-2.22
-2.39
-2.55
-2.71
-2.88
-3.04
-3.2

-3.37
-3.53
-3.69
-3.86
-4.02
-4.18
-4.35
-4.51
-4.67
-4.84
-5.0





4.0


3.5


3.0


2.5


2.0


1.5


1.0



3.5


3.0


2.5


2.0


1.5


1.0


0.5





















1.0







0 20 40 60 80 100 120 140

[AU]



0 20 40 60 80 100 120 140

[AU]



0 20 40 60 80 100 120 140

[AU]



**Figure** **7** . Exploration of the parameter space for the dust continuum emission at _λ_ = 870 _µ_ m (left panels), 1 _._ 3 mm (middle
panels), and 3 _._ 0 mm (right panels). Top panels: Reduced chi-squared ( _χ_ _r_ [2] [)] [for] [different] [dust] [models] [in] [the] [(] _[ϵ]_ global _[, α]_ [)] [space.]
Bottom panels: Best model at each wavelength; the blue line is the observational dust continuum emission, the red solid line is
the best emission model and the green dashed line is the best optical depth model.



-1.08
-1.24

-1.41

-1.57
-1.73
-1.9

-2.06
-2.22
-2.39
-2.55
-2.71
-2.88
-3.04
-3.2

-3.37
-3.53
-3.69
-3.86
-4.02
-4.18
-4.35
-4.51
-4.67
-4.84
-5.0





log( global )


**Figure** **8** . Isocontours where the reduced chi-squared is equal
to 1.5 times the minimum value of _χ_ _r_ [2] [for] [each] [wavelength]
_λ_ = 870 _µ_ m (red solid line), 1 _._ 3 mm (green dashed line), and
3 _._ 0 mm (blue dash-dotted line).


Then, substituting Equation (7) and Equation (33) in
Equation (32), one obtains



_n_ 2 ( _a_ ) _da_ = _A_ Σ g ( _ϖ_ ) exp[ _−ka_ ]
� � _A_ [Σ] [g] [(] _[ϖ]_ [) exp[] _[−][ka]_ []] _[dA]_



ticle size distribution does not change, i.e., _p_ 2 = _p_ .
For the gas surface density Σ g ( _ϖ_ ) in the top panel
of Figure (5), we fit the term within the brackets of
the Equation (34) with a power-law in order to obtain
the value of _p_ 2 for different values of _α_ . The top panel
of Figure (11) shows _p_ 2 as a function of the radius for 3
values of _α_, assuming that the original distribution has a
slope _p_ = 3 _._ 5. The blue solid line represents a relatively
low value of _α_, the green dashed line of an intermediate
value, and the red dash-dotted line of a high value [6] .
One recovers the original value of _p_ for the large value
of _α_ as expected. For intermediate and low values of _α_,
the slope _p_ 2 decreases from its original value ( _p_ ) in the
inner disk and increases in the outer disk.
The bottom panel of Figure (11) shows the maximum
grain size _a_ max needed to explain the value of _β_ shown
in the middle panel of Figure (5), given the _p_ 2 curves
shown in the top panel (see Appendix A). Note that
in these cases, the maximum grain size _a_ max increases
with _α_ . Therefore, any physical process that changes
the slope _p →_ _p_ 2, will alter the inferred value of _a_ max .


6. CONCLUSIONS



We present an analytic model of the dust concentration on gas pressure maxima in disk rings. This model


6 One refers to the magnitude of _α_ compared with the Stokes
number. A large, intermediate and low value of _α_ in this context
means _St/α ≫_ 1 _, St/α ∼_ 1, and _St/α ≪_ 1 respectively.



exp[ _−ka_ ]
_a_ _[−][p]_ [2] _∝_
� � _A_ [Σ] [g] [(] _[ϖ]_ [) exp[] _[−][ka]_ []] _[dA]_



_n_ ( _a_ ) _da,_
�


_a_ _[−][p]_ _._ (34)
�



Equation (34) only depends on the viscosity coefficient
_α_ via the factor _k_ defined in Equation (8). One expects
that, if the viscosity coefficient _α_ _→∞_ (i.e. _k_ _→_ 0),
there is no dust differential migration and the dust par

10



25


20


15


10


5


0


10


8


6


4


2


0


1.2


1.0


0.8


0.6


0.4


0.2


0.0



100


50


0


50


100


100


50


0


50


100


100


50


0


50


100



|=3 mm|Col2|Col3|Col4|
|---|---|---|---|
|||||


100 0 100

x[AU]



Observation Model |Difference|



100 0 100

x[AU]



100 0 100

x[AU]



**Figure** **9** . Maps of the thermal dust emission at _λ_ = 870 _µ_ m (first row), 1 _._ 3 mm (second row), and 3 _._ 0 mm (third row). The
left, middle and right panels are the observational, model and difference maps.



assumes steady state and only considers the dust radial
redistribution, without fragmentation or coagulation. In
addition, the model does not consider the back reaction
of the dust on the gas, which is negligible if the local
dust-to-gas mass ratio is smaller than 1. In the case of
HD 169142, this condition is satisfied.
The inward dust migration can be stopped (or retarded) by axi-symmetric gas pressure maxima, which
act as dust traps. The dust grains concentrate around
the gas pressure maxima and change the local dust properties (the particle size distribution, the opacity, the
dust-to-gas mass ratio). The dust concentration depends on the grain size, while the small grains are well
coupled with the gas, the large grains tend to decouple
and concentrate more around the pressure maxima due
to the drag force. Diffusion prevents a strong concentration of dust grains around gas maxima. If the viscosity



coefficient _α_ is large, then the dust grains of all sizes tend
to follow the gas distribution. If the viscosity coefficient
is small, the large dust grains (those with _St/α_ _≫_ 1)
strongly concentrate around the pressure maxima, while
the small grains (those with _St/α_ _≪_ 1) are well mixed
with the gas (e.g., Birnstiel et al. (2013), Lyra & Lin
(2013), Dullemond et al. (2018)). This migration has
important consequences in the emergent intensity and
the maps of the disks. To model the disk emission we
have considered spherical grains with a global particle
size distribution _n_ ( _a_ ) _da_ _∝_ _a_ _[−]_ [3] _[.]_ [5] _da_, and the composition given by Pollack et al. (1994), which determine the
values of opacity exponent _β_ in Figure (A1) used to interpret the local physical conditions of the grains. With
this in mind, we summarize below our main conclusions.


1. Our analytical model can explain the behaviour of

1.0


0.8


0.6


0.4


0.2


0.0






|Col1|Col2|Col3|0.06|
|---|---|---|---|
|dust<br>gas ×<br>global|dust<br>gas ×<br>global|dust<br>gas ×<br>global|0.02<br>0.03<br>0.04<br>0.05<br>0.06<br>(<br>)|
|global|global|global|~~0.01~~|
|global|global|global|global|
|global|global|global|0.00|



0 20 40 60 80 100 120

[AU]


**Figure** **10** . Dust properties using the best averaged parameters: _ϵ_ global = 1 _._ 05 _×_ 10 _[−]_ [2], _α_ = 1 _._ 35 _×_ 10 _[−]_ [2] . The red solid
line is the dust surface density, the blue dash-dotted line is
the gas surface density scaled by the global dust-to-gas mass
ratio, the green dashed line is the local dust-to-gas mass ratio, and the green dotted line is the global dust-to-gas mass
ratio.



3.8





3.6


3.4


10 [1]


10 [0]


10 1

20 40 60 80 100

[AU]


**Figure** **11** . Degeneration between _p_ and _a_ max to explain the
profile of _β_ in the HD 169142 disk.


the dust grains trapped in a gas ring of the simulation performed by Flock et al. (2015), Ruge et
al. (2016). It can also explain the main characteristics of the thermal dust emission of the disk

around the HD 169142 star. Because in both cases

the gas surface density has local maxima, an equilibrium between the drag force and diffusion can
be reached at these maxima, allowing the accumulation of dust and preventing its migration toward
the central star.


2. This model can be easily implemented in numerical simulations that follow only the gas in protoplanetary disks to account for the dust concentration, saving computational time.



11


3. The redistribution of dust grains effectively increases the dust-to-gas mass ratio and the thermal dust emission within the gas pressure maxima.
However, in the case of large grains ( _a_ max _>_ 1 cm
for millimeter observations), even though they
provide most of the mass, the emergent intensity does not increase linearly with the dust-to-gas
mass ratio because these grains have a low opacity
at mm wavelengths.


4. The small spectral index derived from the ALMA
observations in the inner ring of HD 169142 (10 ≲
_ϖ_ ≲ 40 AU) can be explained by the presence of
large grains. The maximum dust size in the center
of the inner ring ( _∼_ 27 AU) is _a_ max _>_ 10 cm. This
value monotonically decreases, reaching a value of
_∼_ 2 mm in the outer region of the disk.


5. The best parameters that describe the dust dynamics in the disk around HD 169142 according to
the analytical model described in Section 2 are a
global dust-to-gas mass ratio _ϵ_ global = 1 _._ 05 _×_ 10 _[−]_ [2]

(similar to the ISM), and a viscosity coefficient
_α_ = 1 _._ 35 _×_ 10 _[−]_ [2] . These parameters can simultaneously explain the dust emission profiles at
_λ_ = 870 _µ_ m, 1 _._ 3 mm, and 3 _._ 0 mm.


_Acknowledgements._ A. S. and S. Lizano acknowledge
support from PAPIIT-UNAM IN101418 and CONACyT 23863. M.O. acknowledges financial support from
the MINECO (Spain) AYA2017-84390-C2 grant (cofunded by FEDER) and also from the State Agency
for Research of the Spanish MCIU through the “Center of Excellence Severo Ochoa” award for the Instituto
de Astrofsica de Andaluca (SEV-2017-0709). MF acknowledges funding from the European Research Council (ERC) under the European Unions Horizon 2020 research and innovation programme (grant agreement No.
757957). We thank useful comments from an anonymous referee that helped clarified some aspects of the

paper.
This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2013.1.00592.S,
ADS/JAO.ALMA#2012.1.00799.S,
ADS/JAO.ALMA#2016.1.01158.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada) and NSC and ASIAA (Taiwan) and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


_Software:_ CASA (v 4.7.0) (McMullin et al. 2007)

12



6.0

5.8

5.6

5.4

5.2

5.0

4.8

4.6

4.4

4.2

4.0

3.8

3.6

3.4

3.2

3.0

2.8

2.6

2.4

2.2

2.0



3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0



6.0

5.8

5.6

5.4

5.2

5.0

4.8

4.6

4.4

4.2

4.0

3.8

3.6

3.4

3.2

3.0

2.8

2.6

2.4

2.2

2.0



17.5


15.0


12.5


10.0


7.5


5.0


2.5



log(a max [cm])



log(a max [cm])



**Figure** **A1** . Left panel: _β_ between _λ_ = 870 _µ_ m and 7 mm as a function of _a_ max and _p_ . The black dashed line corresponds to the
isocontour where _β_ = 0 _._ 5. Right panel: Dust total opacity (absorption + scattering) at _λ_ = 3 mm for the same space parameter.
Both maps were computed using the DA01 code.


APPENDIX


A. SPECTRAL INDEX _β_ AND DUST OPACITY


The spectral index _β_ between 870 _µ_ m and 7 mm is computed from the opacities obtained from the DA01 code using
the Pollack et al. (1994) abundances, in a grid varying the maximum grain size ( _a_ max ) and slope _p_ of the particle size
distribution _n_ ( _a_ ) _∝_ _a_ _[−][p]_ . The minimum grain size in all the cases is set to 0.05 _µ_ m, this value is relevant only in the
case when the mass of the particle size distribution is dominated by the small grains, which occurs when _p >_ 4.
Left panel of Figure (A1) shows the map of _β_ as a function of _a_ max and _p_ . Note that in the region of small dust
grains with _a_ max ≲ 60 _µ_ m or high slope _p_ ≳ 4, the value is _β_ _∼_ 1 _._ 8, which is characteristic of the interstellar medium
(Draine 2006). The region with _β_ _<_ 1 (blue) can only be explained by large dust grains _a_ max ≳ 2 mm and _p_ ≲ 4.
The black dashed line is the isocontour where _β_ = 0 _._ 5. The slope _β_ shows a local maximum for intermediate particles
(60 _µ_ m _< a_ max _<_ 2 mm and _p_ ≲ 4), which has been previously reported in the literature (e.g., Ricci et al. (2010)).
Right panel of Figure (A1) shows as an example the map of the total dust opacity _χ_ at _λ_ = 3 mm as a function of
_a_ max and _p_ ; the units of _χ_ 3mm are cm [2] per gram of dust. The dust opacity has a local maximum for _a_ max _∼_ 0 _._ 13 cm
and low _p_ ; this occurs because when _a_ max _≫_ _λ_ the largest dust grains do not contribute to the effective cross section
but they dominate the dust mass. In general, when _a_ max _≫_ _λ_, the opacity decreases as _χ_ _ν_ _∝_ _a_ [3] max _[−][p]_ [for] [3] _[<]_ _[p]_ _[<]_ [4]
(DA01).
Also, the dust opacity is low for large values of the slope of the particle size distribution ( _p_ ≳ 4), this occurs because
for _p_ _>_ 4 the mass is dominated by the small grains, however they do not have a large effective cross section at
millimeter wavelengths. For small grains log( _a_ max ) _<_ 1 _._ 5, the opacity at _λ_ = 3 mm is also small for all the values of
_p_, due to their effective cross section at millimeter wavelengths is small.
The behaviour of the dust opacity at other millimeter wavelengths is qualitatively the same, the difference is the value
of _a_ max where the opacity is maximum. We find that total opacity has a maximum at _a_ max _∼_ _λ/π_ . The maps of Figure
(A1) can be used to find the opacity at other wavelengths between _λ_ = 870 _µ_ m and 7 mm via _χ_ _ν_ = _χ_ 3mm ( _ν/ν_ 3mm ) _[β]_ .


B. GAS AND DUST TIMESCALES


The dynamics of the gas and dust grains is different due to the drag force. In particular, the advection timescale of
the dust grains is



_t_ adv _,_ d = _v_ _[L]_ _ϖ_ _,_ (B1)



where _L_ is a characteristic length scale and _v_ _ϖ_ is the magnitude of the dust velocity relative to the gas (Equation 3).
The diffusion timescale of the gas and the dust grains are



_t_ diff _,_ g = _D_ _[L]_ [2] g _._ (B2)



_t_ diff _,_ d = _[L]_ [2] (1 + _St_ [2] ) _,_ (B3)

_D_ g

13



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]







10 1

|t/t(a = 1 cm)|17.5|
|---|---|
|tdiff, d/tadv, d(a = 1 cm)<br>tdiff, g/tadv, d(a = 1 cm)<br>tdiff, g/tadv, d(a = 1 mm)|0.0<br>2.5<br>5.0<br>7.5<br>10.0<br>12.5<br>15.0<br>.<br>g(<br>)[g/cm2]|
|g|g|


0 20 40 60 80 100

[AU]


**Figure** **B2** . Ratio of the diffusion and advection timescales as a function of radius for the HD 169142 disk. The thick blue
line is the dust diffusion to advection timescales ratio for grains of 1 cm. The thick and thin red lines are the ratio of the gas
diffusion to the dust advection timescales for 1 cm and 1 mm, respectively. The gas surface density is shown for reference in the
background as a green dotted line.


where _D_ g is the gas diffusion coefficient and _St_ the Stokes number (Youdin & Lithwick 2007). Then, the ratio between
the diffusion and advection timescales of the dust is given by



_t_ diff _,_ d = _[St]_
_t_ adv _,_ d _α_



_ϖ_
���� Σ g



_d_ Σ g


_dϖ_



_,_ (B4)
����



If this ratio is much larger than 1, the dust concentrates in pressure maxima. The ratio between the diffusion timescale
of the gas and the dust advection timescale is



_ϖ_
����� Σ g



_t_ diff _,_ g = _[St]_
_t_ adv _,_ d _α_



1
� 1 + _St_ [2]



_d_ Σ g


_dϖ_



_._ (B5)
����



If this ratio is much larger than 1, as the gas evolves, the dust quickly adjusts to the gas density structure and
concentrates in gas pressure maxima.
In general, the Stokes number for millimeter and centimeter dust grains ( _St_ (1 mm) _∼_ 0 _._ 1, _St_ (1 cm) _∼_ 1). Also,
the logarithmic density gradient in accretion disks _|_ ( _ϖ/_ Σ g )( _d_ Σ g _/dϖ_ ) _|_ ) is in general, of the order of 1, but in pressure
maxima, it is much larger than 1. For example, consider a gaussian function at a radius _ϖ_ 0 and a total width
2 _σ_, Σ g _∝_ exp( _−_ [1] 2 [(] _[ϖ]_ _[−]_ _[ϖ]_ [0] [)] [2] _[/σ]_ [2] [).] [Then,] [the] [logarithmic] [gradient] [is] _[ϖ][|]_ [(] _[ϖ]_ _[−]_ _[ϖ]_ [0] [)] _[|][/σ]_ [2] [.] [For] [narrow] [rings] [such] [that]

_ϵ_ = 2 _σ/ϖ_ 0 _<_ 1, the logarithmic gradient is larger than 1, except in the neighborhood of _ϖ_ 0 where the dust grains
are already close to the equilibrium point. Then, because the viscosity coefficient _α_ is much smaller than 1, the
advection timescale of the dust grains is smaller than the diffusion timescale of both the gas and dust, allowing a fast
concentration of the dust grains in the gas pressure maxima.
Figure B2 shows the ratio between the diffusion and advection timescales for the best fit model of the HD 169142
disk . The different lines show these ratios for dust sizes of 1 cm and 1mm. Because the Stokes number for 1 mm
particles is small, the ratio of the dust diffusion to advection timescales and the ratio of the gas diffusion to the dust
advection timescales are the same. Note that the ratios between the timescales are larger than 1 throughout the disk,
with local minima at the position of the gas maxima, where the dust grains concentrate. Thus, a fast trapping scenario
and the steady state assumption are feasible in the HD 169142 disk.


C. IMAGING PARAMETERS


Continuum images were created using CASA (v 4.7.0) [7] . Table (C1) shows the relevant imaging parameters used
for each wavelength.


7 CASA, the Common Astronomy Software Applications pack- astronomical telescopes.
age, is a software developed to support data processing of radio

**Table** **C1** . Parameters of continuum and line Images


Original synthesized beam size rms noise image


_λ_ _ν_ Clean Weighting Major x Minor; P.A. [a] Original Convolved


Band (mm) (GHz) (arcsec _×_ arcsec; deg) ( _µ_ Jy/beam) ( _µ_ Jy/beam)


dust 7 0.87 330 Briggs; robust=0.5 0.19 _×_ 0.12; 84.97 170 196


dust 6 1.3 230 Natural weighting 0.19 _×_ 0.13; 63.42 100 91


dust 3 3.0 100 Briggs; robust=-1 0.17 _×_ 0.07;-89.22 25 23

12 CO 6 1.3 220 Natural weighting 0.16 _×_ 0.16, 0.0 3650 [b]    
13 CO 6 1.3 220 Natural weighting 0.16 _×_ 0.16, 0.0 2961    

a All dust continuum images were finally convolved to the same circular beam of 0.20 arcsec.


b The noise of the CO maps corresponds to the rms of the zeroth moment maps.


REFERENCES



ALMA Partnership, Brogan, C. L., P´erez, L. M., et al. 2015,
ApJL, 808, L3
Andrews, S. M., Huang, J., P´erez, L. M., et al. 2018, ApJL, 869,

L41

Barge, P., & Sommeria, J. 1995, A&A, 295, L1
Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R.
1990, AJ, 99, 924
Biller, B. A., Males, J., Rodigas, T., et al. 2014, ApJL, 792, L22
Birnstiel, T., Dullemond, C. P., & Pinilla, P. 2013, A&A, 550, L8
Blondel, P. F. C., & Djie, H. R. E. T. A. 2006, A&A, 456, 1045
Brauer, F., Dullemond, C. P., & Henning, T. 2008, A&A, 480,

859

Carrasco-Gonz´alez, C., Henning, T., Chandler, C. J., et al. 2016,
ApJL, 821, L16
D’Alessio, P., Calvet, N., & Hartmann, L. 2001, ApJ, 553, 321
Draine, B. T. 2006, ApJ, 636, 1114
Dickman, R. L. 1978, ApJS, 37, 407
Dullemond, C. P., Birnstiel, T., Huang, J., et al. 2018,

arXiv:1812.04044

Estalella, R., Anglada, G., 1994, ISBN 84-8338-098-6
Fedele, D., Carney, M., Hogerheijde, M. R., et al. 2017, A&A,
600, A72
Flock, M., Ruge, J. P., Dzyurkevich, N., et al. 2015, A&A, 574,
A68

Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2016,
A&A, 595, A2
Isella, A., Guidi, G., Testi, L., et al. 2016, Physical Review
Letters, 117, 251101
Lyra, W., & Lin, M.-K. 2013, ApJ, 775, 17
Mac´ıas, E., Anglada, G., Osorio, M., et al. 2017, ApJ, 838, 97
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap,
K. 2007, Astronomical Data Analysis Software and Systems
XVI (ASP Conf. Ser. 376), ed. R. A. Shaw, F. Hill, & D. J.
Bell (San Francisco, CA: ASP), 127



Mihalas, D. 1978, San Francisco, W. H. Freeman and Co.,
1978. 650 p.,
Miyake, K., & Nakagawa, Y. 1993, Icarus, 106, 20
Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943
Osorio, M., Anglada, G., Carrasco-Gonz´alez, C., et al. 2014,
ApJL, 791, L36
Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012, A&A, 538, A114
Pinte, C., Dent, W. R. F., M´enard, F., et al. 2016, ApJ, 816, 25
Pohl, A., Benisty, M., Pinilla, P., et al. 2017, ApJ, 850, 52
Pollack, J. B., Hollenbach, D., Beckwith, S., et al. 1994, ApJ,
421, 615
Quanz, S. P., Avenhaus, H., Buenzli, E., et al. 2013, ApJL, 766,

L2


Raman, A., Lisanti, M., Wilner, D. J., Qi, C., & Hogerheijde, M.
2006, AJ, 131, 2290
Reggiani, M., Quanz, S. P., Meyer, M. R., et al. 2014, ApJL,
792, L23
Ricci, L., Testi, L., Natta, A., et al. 2010, A&A, 512, A15
Ruge, J. P., Flock, M., Wolf, S., et al. 2016, A&A, 590, A17
Sierra, A., Lizano, S., & Barge, P. 2017, ApJ, 850, 115
Takeuchi, T., & Lin, D. N. C. 2002, ApJ, 581, 1344
Taki, T., Fujimoto, M., & Ida, S. 2016, A&A, 591, A86
The, P. S., de Winter, D., & Perez, M. R. 1994, A&AS, 104, 315
Weidenschilling, S. J. 1977, MNRAS, 180, 57
Whipple, F. L. 1972, From Plasma to Planet, 211
Windmark, F., Birnstiel, T., G¨uttler, C., et al. 2012, A&A, 540,
A73

Youdin, A. N., & Lithwick, Y. 2007, Icarus, 192, 588


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "7 mm imaging used for context",
  "failed_quote": "The dust thermal emission of the disk was first imaged with the VLA at 7 mm (Osorio et al. 2014, Macías et al. 2017)."
 }
]
```
