# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686A...9M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2024
March 12, 2024

## **Rotation curves in protoplanetary disks with thermal stratification**

### **Physical model and observational evidence in MAPS disks**


P. Martire [1][,][ 2], C. Longarini [1][,][ 8], G. Lodato [1], G. P. Rosotti [1], A. Winter [3], S. Facchini [1], C. Hardiman [4], M. Benisty [3][,][ 5], J.
Stadler [3][,][ 5], A. F. Izquierdo [2] and Leonardo Testi [6][,][ 7] .


1 Dipartimento di Fisica, Università degli Studi di Milano, Via Celoria 16, Milano, I-20133, Italy
e-mail: `martire@strw.leidenuniv.nl`

e-mail: `cl2000@cam.ac.uk`
2 Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA Leiden, The Netherlands
3 Laboratoire Lagrange, Université Côte d’Azur, CNRS, Observatoire de la Côte d’Azur, 06304 Nice, France
4 School of Physics and Astronomy, Monash University, Clayton, VIC 3800, Australia
5 Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France
6 Alma Mater Studiorum Università di Bologna, Dipartimento di Fisica e Astronomia (DIFA), Via Gobetti 93/2, 40129 Bologna,
Italy
7 INAF-Osservatorio Astrofisico di Arcetri, L.go E. Fermi 5, I-50125 Firenze, Italy
8 Institute of Astronomy, University of Cambridge, Madingley Road, Cambridge, CB3 0HA, United Kingdom


Received ; accepted


**ABSTRACT**


_Context._ In recent years, the gas kinematics probed by molecular lines detected with ALMA has opened a new window into the
of study protoplanetary disks. High spatial and spectral resolution observations have revealed the complexity of protoplanetary disk
structure. Drawing accurate interpretations of these data allows us to better comprehend planet formation
_Aims._ We investigate the impact of thermal stratification on the azimuthal velocity of protoplanetary disks. High-resolution gas
observations reveal velocity differences between CO isotopologues, which cannot be adequately explained with vertically isothermal
models. The aim of this work is to determine whether a stratified model can explain this discrepancy.
_Methods._ We analytically solved the hydrostatic equilibrium for a stratified disk and we derived the azimuthal velocity. We tested the
model with SPH numerical simulations and then we used it to fit for the star mass, disk mass, and scale radius of the sources in the
MAPS sample. In particular, we used [12] CO and [13] CO datacubes.
_Results._ When thermal stratification is taken into account, it is possible to reconcile most of the inconsistencies between rotation
curves of different isotopologues. A more accurate description of the CO rotation curves offers a deeper understanding of the disk
structure. The best-fit values of star mass, disk mass, and scale radius become more realistic and more in line with previous studies.
In particular, the quality of the scale radius estimate significantly increases when adopting a stratified model. In light of our results,
we computed the gas-to-dust ratio and the Toomre Q parameter. Within our hypothesis, for all the sources, the gas-to-dust ratio
appears higher but still close to the standard value of 100 (within a factor of 2). The Toomre Q parameter suggests that the disks are
gravitationally stable ( _Q_    - 1). However, the systems that show spirals presence are closer to the conditions of gravitational instability
( _Q_ ∼ 5).


**Key words.** protoplanetary disks – hydrodynamics – accretion, accretion disks



**1.** **Introduction**


Our understanding of the physical properties of protoplanetary
disks has improved in recent years thanks to the Atacama Large
Millimeter Array (ALMA) (ALMA Partnership et al. 2015).
High spectral and spatial resolution gas observations enable us
to probe density, temperature, and velocity fields of protostellar disks, gaining unique information about their structure (Law
et al. 2021; Calahan et al. 2021; Teague et al. 2022; Miotello
et al. 2023; Pinte et al. 2023; Lodato et al. 2023). More recently,
the large program Molecules with ALMA at Planet-forming
Scales (MAPS) (Öberg et al. 2021) targeted five protoplanetary
disks (MWC 480, IM Lup, GM Aur, HD 163296, and AS 209)
in several molecular lines. For optically thick line emission, the
gas temperature can be measured along the emission surface directly from the peak surface brightness of the channel maps (Law
et al. 2021). Given the varying heights of these emitting lay


ers surfaces, it is possible to infer the thermal structure in disks,
proving the existence of a vertical thermal stratification in them
(Dartois et al. 2003; Rosenfeld et al. 2013; Pinte et al. 2018), as
expected from basic radiative transfer arguments (Chiang & Goldreich 1997; D’Alessio et al. 1998, 1999). Although disk models
have usually been considered as vertically isothermal, the vertical gradient of temperature leads to considerable corrections in
the calculation of density structure and azimuthal velocity, which
results in several percent deviations from the Keplerian velocity
(Rosenfeld et al. 2013). Accounting for such differences is important not only to infer stellar masses, but also to accurately
constrain the disk pressure structure and disk mass. Such parameters are of great importance with respect to interpreting velocity
deviations, which may serve as signposts for planets (Pinte et al.
2018; Rabago & Zhu 2021; Bollati et al. 2021; Izquierdo et al.
2021; Bae et al. 2021), dust trapping (Teague et al. 2018; Rosotti


Article number, page 1 of 16

_A&A proofs:_ manuscript no. main



et al. 2020) or disk instabilities (Hall et al. 2020; Terry et al.
2022; Longarini et al. 2021; Barraza-Alfaro et al. 2021).
In this paper, we analytically derive the density and velocity
field of protostellar disks with thermal stratification, generalizing the work of Takeuchi & Lin (2002). A similar analysis of
MAPS data with vertically isothermal disks was performed by
Lodato et al. (2023). We test the model against hydrodynamical simulations and we apply it to the whole MAPS sample for
12 CO and 13 CO data. In Sect. 2, we present the model, solving
the vertical hydrostatic equilibrium and obtaining an expression
for the azimuthal velocity. In Sect. 3, we present the numerical
setup and a comparison between the model and simulations. In
Sect. 4, we apply the model and we discuss our findings. Finally,
in Sect. 5, we compute the gas-to-dust ratio and the Toomre Q
parameter, and we draw our conclusions.


**2.** **Model**


_2.1._ _Assumptions_


In our analytical calculations, we did not make any assumption
on the surface density Σ, considering it as arbitrary. However,
to apply the model to observations, we were forced to choose
a parameterization for the surface density and we assume that
it is described by the self-similar solution from Lynden-Bell &
Pringle (1974):



value at midplane it is necessary that _f_ ( _z_ = 0) = 1 = _g_ ( _z_ = 0).
Assuming a barotropic fluid, the pressure, _P_, is given by:


_P_ ( _R_, _z_ ) = _P_ mid ( _R_ ) _fg_ ( _R_, _z_ ) = _c_ [2] s,mid [(] _[R]_ [)][ρ] [mid] [(] _[R]_ [)] _[ fg]_ [(] _[R]_ [,] _[ z]_ [)][.] (6)


While the profile of _f_ is arbitrary, this does not hold for _g_, whose
value is set by solving the vertical hydrostatic equilibrium.


_2.2._ _Hydrostatic equilibrium and rotation curve_


To compute the vertical density profile we assume a non-selfgravitating disk under the condition of hydrostatic equilibrium
in the vertical direction:

1 _dP_
ρ _dz_ [=][ −] _[d]_ _dz_ [Φ] [⋆] [,] (7)


where Φ ⋆ = − _GM_ ⋆ / _r_ is the stellar potential ( _r_ = ~~√~~ _R_ [2] + _z_ [2] is

the spherical radius). Equation (7) can be written as (for further
details, see Appendix A):



1
log( _fg_ ) = −
_H_ [2]
mid



_dP_

_dz_ [=][ −] _[d]_ _dz_ [Φ] [⋆]



(7)
_dz_ [,]



where Φ ⋆ = − _GM_ ⋆ / _r_ is the stellar potential ( _r_ = ~~√~~



2 −3/2

. (8)
� �



_z_

_c_ [2] s, mid _[f]_ _[d]_ [ lo] _dz_ [g(] _[fg]_ [)] = −Ω [2] k _[z]_ �1 + � _R_




[g(] _[fg]_ [)] _z_

= −Ω [2] k _[z]_ 1 +
_dz_ � � _R_



Solving for log( _fg_ ), we find:



2 [] −3/2

_dz_ [′], (9)

� 



_z_ ′
1 +
 � _R_



� 0 _z_



� 0 _z_



_z_ [′]


_f_



2−γ

, (1)
� �



−γ _R_
exp −
� � � _R_ c



Σ = [(][2][ −] [γ][)] _[M]_ [d]

2π _R_ [2] c



_R_
� _R_ c



and hence the density is given by:



2 [] −3/2


_dz_ [′] .

�  



_z_ [′]


_f_ ( _R_, _z_ [′] )



_z_ ′
1 +
 � _R_



1

−
_H_ [2]
 mid



� 0 _z_



� 0 _z_



where _M_ d and _R_ c are the disk mass and the scale radius respectively; _R_ is the cylindrical radius and γ is a free parameter describing the steepness of the surface density. The disk density at
the midplane ρ mid is:



ρ( _R_, _z_ ) = [ρ] [mid] [(] _[R]_ [)]

_f_ ( _R_, _z_ ) [exp]



ρ( _R_, _z_ ) = [ρ] [mid] [(] _[R]_ [)]



(10)


Assuming the condition of centrifugal balance, the rotation curve
is given by the radial component of Navier-Stokes equation:



_v_ [2] _[R]_
ϕ [(] _[R]_ [,] _[ z]_ [)][ =]




_[R]_ _dP_

ρ _dR_ [(] _[R]_ [,] _[ z]_ [)][ +] _[ Rd]_ _dR_ [Φ] [⋆]



Σ _R_
ρ mid = ∝ _R_ [−][(][γ][+][(3][−] _[q]_ [)][/][2)] exp −
~~√~~ 2π _H_ mid � � _R_ c



2−γ

, (2)
� �



_dR_ [(] _[R]_ [,] _[ z]_ [)][.] (11)



where _H_ mid = _c_ s,mid /Ω k is the typical scale height of the disk
at the midplane, _c_ s, mid = ~~[�]~~ _k_ b _T_ mid /(µ _m_ p ) ∝ _R_ [−] _[q]_ [/][2] is the sound
speed at the disk midplane, _k_ b is the Boltzmann constant, _T_ mid =
_T_ mid,100 ( _R_ /100au) [−] _[q]_ is the temperature at midplane, µ is the
mean molecular weight (usually assumed to be 2.1), _m_ p is the
proton mass, and Ω k = � _GM_ ⋆ / _R_ [3] is the Keplerian angular velocity ( _G_ is the gravitational constant and _M_ ⋆ is the stellar mass).
From the literature (Chiang & Goldreich 1997; Dullemond
et al. 2020) and observational data (Rosenfeld et al. 2013; Pinte
et al. 2018; Law et al. 2021), we know that protoplanetary disks
are thermally stratified. We take this into account by defining a
function, _f_, that describes the dependency of the temperature, _T_,
on height, such that:


_T_ ( _R_, _z_ ) = _T_ mid ( _R_ ) _f_ ( _R_, _z_ ), (3)

_c_ [2] s [(] _[R]_ [,] _[ z]_ [)][ =] _[ c]_ [2] s,mid [(] _[R]_ [)] _[ f]_ [(] _[R]_ [,] _[ z]_ [)][.] (4)


We underline that the isothermal case can be obtained considering _f_ ≡ 1, thus _T_ = _T_ mid ( _R_ ). As for the density, we assume that:


ρ = ρ( _R_, _z_ ) = ρ mid ( _R_ ) _g_ ( _R_, _z_ ), (5)


where _g_ describes how the density changes vertically. We note
that in order to smoothly connect the functions above to their


Article number, page 2 of 16



The first term in Eq.(11) can be written as (for further details,
see Appendix A)



_R_ _dP_ _d_ log _P_ mid

s, mid _[f]_ + _[d]_ [ lo][g(] _[fg]_ [)]
ρ _dR_ [=] _[ c]_ [2] � _d_ log _R_ _d_ log _R_



, (12)
�



_R_



_d_ log _R_



and the second one as



_R_ _[d]_ [Φ] [⋆] k

_dR_ [(] _[R]_ [,] _[ z]_ [)][ =] _[ v]_ [2]



2 [�] −3/2

_z_
1 +, (13)
� � _R_ �



where _v_ k = [√] _GM_ ⋆ / _R_ is the Keplerian velocity. Therefore, the
rotation curve is



_v_ [2] ϕ [(] _[R]_ [,] _[ z]_ [)][ =] _[ v]_ k [2]



_z_ 2 [�] −3/2 _d_ log _P_ mid
1 + +

� � _R_ � � _d_ log _R_ [+]



_H_

+ [d lo][g(] _[fg]_ [)]

d log _R_ �� _R_



2

. (14)

� mid _[f]_ [(] _[R]_ [,] _[ z]_ [)] �



In the self-similar case, this becomes:



2−γ

−
�



_v_ [2] ϕ [(] _[R]_ [,] _[ z]_ [)][ =] _[ v]_ k [2]



2 [�] −3/2

_z_
1 + −

� � _R_ �



γ ′ + (2 − γ) _R_
 � _R_ _c_



− [d lo][g(] _[fg]_ [)]

d log _R_



_H_ 2

, (15)

�� _R_ � mid _[f]_ [(] _[R]_ [,] _[ z]_ [)] �

Martire et al.: Rotation curves in stratified disks



where γ [′] = γ + (3 + _q_ )/2. Each term of Eq. (15) can be easily
interpreted: [1 + ( _z_ / _R_ ) [2] ] [−][3][/][2] is the star contribution at the height
_z_, γ [′] is the effect of the power law scaling of the pressure, (2 −
γ)( _R_ / _R_ _c_ ) [2][−][γ] is the effect of the exponential truncation and the
logarithmic term is the effect of the vertical stratification. Since
the latter is the derivative of a product, we do not know its sign
a priori; thus, we also do not know if the rotation is accelerated
or slowed down by thermal stratification (see Appendix A). In
any case, in all our attempts this term never dominates over the
variation of gravity with _z_ . Thus, we found rotation to slow down
with z and this effect is more pronounced as compared to the
isothermal case when considering the parameters of the MAPS
sample.
We underline that for the isothermal case ( _f_ ≡ 1), this expression reduces to the one derived and analyzed by Lodato et al.
(2023), while Eq. (9) is simplified as:



five disks within the MAPS large program in most of the radial
extent of the disk.
Once the function _f_ is defined, Eqs. (10) and (14) can be
solved semi-analytically and entirely specify the rotation curve.
We have implemented this calculation in DYSC [1] .


**3.** **Comparison with numerical simulations**


In this work, we performed numerical smoothed particle hydrodynamics (SPH) simulations of protostellar disks using the phantom code (Price et al. 2018). This code is widely used in the
astrophysical community to study gas and dust dynamics in accretion disks (Dipierro et al. 2015; Ragusa et al. 2017; Curone
et al. 2022) and it has recently been employed in kinematical
studies (Pinte et al. 2018; Hall et al. 2020; Terry et al. 2022; Verrios et al. 2022). The aim of this simulation is to test the model
before applying it to actual data.
To test the analytical model, we simulated a thermally stratified disk using the parameters of MWC 480 presented in Law
et al. (2021). The simulation has been performed with _N_ = 10 [6]
gas particles, initially distributed as a tapered power law density
profile, smoothed at the inner radius, with γ = 1 and _R_ _c_ = 150au,
between _R_ in = 10au and _R_ out = 400au. The mass of the star is
2.1M ⊙ . For the temperature structure we used the Dullemond
prescription given by Eq. (19), with ζ 0 = 7au, α = 2.78, β =
−0.05, _T_ mid,100 = 27K, _q_ = 0.23, _T_ atm,100 = 69K, and _q_ atm = 0.7.
The α SS Shakura & Sunyaev (Shakura & Sunyaev 1973) viscosity coefficient has been set to 0.005. No self-gravity or dust have
been included in the simulation.
We let the system evolve and reach hydrostatic equilibrium.
We observed that after a couple of orbits the system reaches a
relaxed state. We decided to analyze the output of the simulation
after eight outer orbits (∼ 45kyr). In Fig. 1, we show a comparison between the density and the velocity of the simulations (red
dots) at _z_ = 20 au and both the isothermal and stratified model
predictions. The red dots represent the azimuthal average of the
respective quantity computed by averaging over all SPH particles within each of the 50 radial bins and the error bar is the
corresponding standard deviation. Since we are plotting quantities at z = 20 au, we have excluded the inner points because at
those radii (R < 100 au) the disk has a smaller hydrostatic height
H, causing numerical issues in the resolution of our simulation.
The stratified model perfectly describes the density and the velocity field of the simulation and is a significant improvement
over the isothermal one. In particular, in the right panel of Fig.
1, we can see that the difference between the azimuthal velocity
and the Keplerian velocity ( _v_ [2] k [−] _[v]_ [2] ϕ [)][/] _[v]_ k [2] [reaches the 10] [−] [12% and]
only the stratified model is able to reproduce it.


**4.** **Applying the model**


_4.1._ _The curves_


In this section, we describe how we applied the model to the
entire sample of disks from the MAPS ALMA Large Program
(Öberg et al. 2021). We performed our fits under the assumption
of vertically isothermal or stratified disk to then compare the results. For the vertically isothermal model, the thermal structure
is defined by the hydrostatic height of the disk at _R_ = 100au and
the power law coefficient of the temperature profile, _q_ . These parameters were taken from Zhang et al. (2021). As for the stratified model, Law et al. (2021) obtained the two-dimensional (2D)


1 The code is publicly available at `[https://github.com/](https://github.com/crislong/DySc)`
```
crislong/DySc

```

Article number, page 3 of 16



.




_z_ [′] _dz_ [′]

[1 + ( _z_ [′] / _R_ ) [2] ] [3][/][2] [=][ −] _H_ _[R]_ [2][2]



_H_ [2]
mid



1
log _g_ = −
_H_ [2]
mid



� 0 _z_



_z_ [′] _dz_ [′]



1
1 −
 ~~�~~ 1 + _z_ [2] / _R_ [2]



(16)



Therefore, the density in the isothermal case is given by:



_R_ [2]


_H_ [2]

 mid



_R_ [2]


_H_ [2]





1
 ~~�~~ 1 + _z_ [2] / _R_ [2] [−] [1]



. (17)





ρ( _R_, _z_ ) = ρ mid ( _R_ ) exp



If the disk is self-gravitating, we should add to the right-hand
side of Eq.(11) the self-gravitating term (Bertin & Lodato 1999):



×
�



_k_ [2]
� 1 − _k_ [2]



(18)



_K_ ( _k_ ) − [1]
� 4



_R_ _d_ Φ d


ρ _dR_



_R_



Φ d ∞

_dR_ [(] _[R]_ [,] _[ z]_ [)][ =] _[ G]_ � 0



0




_[R]_ _[z]_ [2]

_r_ [+] _Rr_



_r_
_E_ ( _k_ )
� �� _R_ _[k]_ [Σ][(] _[r]_ [)] _[dr]_ [,]



_r_
� _R_ [−] _[R]_ _r_



_Rr_



where _K_ ( _k_ ) and _E_ ( _k_ ) are complete elliptic integrals (Abramowitz
& Stegun 1970) and _k_ [2] = 4 _Rr_ /[( _R_ + _r_ ) [2] + _z_ [2] ].


_2.3._ _Temperature prescriptions_


The two parameterizations of the vertical temperature more often used are given by Dartois et al. (2003) and Dullemond et al.
(2020). In this work we will use the one by Dullemond et al.
(2020), which is given by:


_z_

_T_ ( _R_, _z_ ) [4] = _T_ ϵ [4] [(] _[R]_ [)][ +] 2 [1] _[T]_ [ 4] atm [(] _[R]_ [)] �1 + tanh � _Z_ _q_ ( _R_ ) [−] [α] � [�] (19)


and, thus,



_T_ atm
� _T_ mid



4
_z_
� ( _R_ )�1 + tanh � _Z_ _q_ ( _R_ ) [−] [α] � [��] [1][/][4],


(20)



_f_ ( _R_, _z_ ) = _T_ ϵ
�� _T_ mid



4
+ [1]
� 2



where the atmospheric temperature is parameterized as
_T_ atm ( _R_ ) = _T_ atm,100 ( _R_ /100au) [−] _[q]_ [atm], _T_ ϵ is considered as an approximation of the temperature at the midplane _T_ ϵ ≃ _T_ mid . _Z_ _q_ ( _R_ ) is
defined as _Z_ _q_ ( _R_ ) = ζ 100 ( _R_ /100au) [β] and α is a parameter that describes where the transition from midplane to atmospheric temperature occurs in the vertical direction. We note that in this case,
_f_ ( _R_, _z_ = 0) � 1 and, thus, the temperature does not smoothly
connect to its value at midplane. We discuss this in Appendix B,
but we underline that Eq. (19) is a good approximation for the

_A&A proofs:_ manuscript no. main


**Fig.** **1.** Comparison between the analytical models and the simulation after eight outer orbits and at _z_ = 20au. Left panel: Density field. Right
panel: Pressure gradient term of the rotation curve. The red dots represent the simulation data, while the blue and orange line show the thermally
stratified model and the isothermal one, respectively. The model with thermal stratification matches very well the simulation.



MWC 480



IM Lup



6


5


4





7


6


5


4


3


2


5


4


3


2


1





0 100 200 300 400 500 600
R [au]


GM Aur



3


2


1

0 100 200 300 400 500
R [au]



HD 163296





10


8


6


4


2





0 100 200 300 400 500 600
R [au]



0 100 200 300 400 500
R [au]



AS 209


8


6


4


2


50 100 150 200
R [au]


**Fig. 2.** [12] CO and [13] CO rotation curves of the MAPS disks extracted with discminer.


Article number, page 4 of 16

Martire et al.: Rotation curves in stratified disks


|Col1|Lup|Col3|
|---|---|---|
||Data<br>Thermal stratification<br>Isothermal||
||0<br>300<br>400<br> [au]|0<br>300<br>400<br> [au]|


|MWC 480|Col2|
|---|---|
|Data<br>Thermal stratification<br>Isothermal|Data<br>Thermal stratification<br>Isothermal|
|100<br>200<br>R [<br>GM|300<br>400<br> au]<br> Aur|
||Data<br>Thermal stratification<br>Isothermal|





0.10


0.08


0.06


0.04


0.02


0.00


0.02


0.04


0.25


0.20


0.15


0.10


0.05


0.00


0.05



50 100 150 200 250 300 350
R [au]


0.10


0.05


0.00


0.05


0.10


0.15



0.15


0.10


0.05


0.00


0.05


0.150


0.125


0.100


0.075


0.050


0.025


0.000


0.025


0.050


AS 209



HD163296







0.20


**Fig. 3.** Relative difference between the squares of observed [12] CO and [13] CO rotation curves predicted by the thermally stratified model (blue line),
the isothermal model (orange line), and the data (red dots). Except for AS 209, where this quantity is negative in the inner part, it is clearly visible
that data are well reproduced by the stratified model. Indeed, the difference of speed between the two curves cannot be explained just in terms of
different height.


Article number, page 5 of 16

_A&A proofs:_ manuscript no. main



MWC 480 [12] CO



MWC 480 [13] CO



8


7


6


5


4


3


2





8


7


6


5


4


3


2





0 100 200 300 400 500
R [au]



100 200 300 400
R [au]



**Fig.** **4.** Left panel: Rotation curve of MWC 480 obtained from [12] CO data (red points), along with our best-fitting curve for the stratified model
(blue line) and the isothermal one (orange line). Right panel: same for the [13] CO data.



7


6



IM Lup [12] CO





IM Lup [13] CO





7


6



5


4


3


2


100 200 300 400
R [au]


**Fig. 5.** Same as Figure 4 but for IM Lup.


temperature structure of the MAPS disks, using the Dullemond
et al. (2020) prescription given by Eq. (19). We note that the
rotation curve traced by a specific molecule is defined by:


_v_ [2] rot [(] _[R]_ [)][ =] _[ v]_ [2] ϕ [(] _[R]_ [,] _[ z]_ [(] _[R]_ [))][,] (21)


where _z_ ( _R_ ) is the height of the emitting layer of the considered
molecule. For the emitting layer, we use:



5


4


3


2


100 200 300 400
R [au]


where the best-fit parameters have been obtained by Izquierdo
et al. (2023). All the parameters used are summarized in Table 1.



_q_ _t_
, (22)
� �



_R_
_z_ ( _R_ ) = _z_ 0
� 100au



ψ _R_
exp −
� � � _R_ _t_



Article number, page 6 of 16

Martire et al.: Rotation curves in stratified disks


GM Aur [12] CO



GM Aur [13] CO



6


5





6





4


3


2


1

100 200 300 400 500
R [au]


**Fig. 6.** Same as Figure 4 but for GM Aur.


**Table** **1.** Velocity extraction method, orientation parameters, thermal
parameters and emitting surfaces for [12] CO and [13] CO data of the MAPS
disks. The orientation parameters and the emitting surfaces are taken
from Izquierdo et al. (2023), the thermal parameters for the isothermal
model are taken from Zhang et al. (2021), for the stratified model from
Law et al. (2021).


**MWC 480** **IM Lup** **GM Aur** **HD 163296** **AS 209**


**Extraction**


12 CO Gauss Dbell Dbell Dbell Gauss
13 CO Gauss Dbell Dbell Dbell Gauss


**Orientation**


_i_ [deg] 37.00 47.50 53.20 46.69 35.00
PA [deg] 328.15 144.50 53.98 312.75 85.20


**Isothermal**


_H_ 100 [au] 10 10 7.5 8.4 6
_q_ 0.82 0.66 0.3 0.84 0.5


**Stratified**


_T_ mid [K] 27 25 20 24 25
_T_ atm [K] 69 36 48 63 37
_q_ 0.23 0.02 0.01 0.18 0.18
_q_ atm 0.7 -0.03 0.55 0.61 0.59
ζ 0 [au] 7 3 13 9 5
α 2.78 4.91 2.57 3.01 3.31
β -0.05 2.07 0.54 0.42 0.02


12 **CO Surface**


_z_ 0 [au] 17.04 34.13 32.00 27.14 16.47
ψ 1.35 0.99 0.97 1.07 1.24
_R_ _t_ [au] 579.43 889.40 729.91 534.00 327.52
_q_ _t_ 1.63 3.18 3.22 2.99 3.01


13 **CO Surface**


_z_ 0 [au] 11.52 22.84 18.21 16.09 4.13
ψ 1.09 1.27 1.14 1.12 0.96
_R_ _t_ [au] 402.77 529.06 512.13 392.75 180.22
_q_ _t_ 1.87 1.65 2.73 3.43 3.59



5


4


3


2


50 100 150 200 250 300 350
R [au]


The rotation curves (Fig. 2) can be obtained through different
moment maps, according to the disk emission. We underline that
rotation curve extraction we are only interested in measuring velocities from the frontside. Since three of the sources have strong
contributions from the disk backside, we used a double-Bell decomposition to distinguish between these two components as introduced (Izquierdo et al. 2022). In this work, we have used an
improved algorithm that performs this decomposition based on
velocity priors obtained from the discminer models (Izquierdo et
al. in prep).


_4.2._ _Results_


We simultaneously fitted the [12] CO and [13] CO data with both
the isothermal and stratified model including the self gravitating contribution. The results are shown in Figs 4, 5, 6, 7, and 8,
and the best-fitting parameters reported in Table 2 and Appendix
C.

To quantify the importance of thermal stratification, we computed the relative difference between the squares of [12] CO and
13 CO rotation curves, as shown in Fig. 3. According to the vertical isothermal model, this quantity is:



which solely depends on the different height of the tracer, since
it is assumed that the temperature does not change vertically. As
for the stratified model, the expression is more complex, since
it involves the evaluation of the term given by Eq.(9) at different heights. In this case, we expect to observe larger differences
between the velocity of the two isotopologues, since there is an
additional shift caused by the different emission temperature. To
determine the importance of vertical stratification, we quantified the maximum value of the velocity shift between [12] CO and


Article number, page 7 of 16



� _v_ [2] 13 [−] _[v]_ [2] 12 �



iso [=] _[ v]_ k [2] _[q]_



�1 + _z_ [2] 12 [/] _[R]_ [2] [ −] �1 + _z_ [2] 13 [/] _[R]_ [2]
(23)
~~�~~ �1 + _z_ [2] 13 [/] _[R]_ [2] [��] 1 + _z_ [2] 12 [/] _[R]_ [2] [�] [,]

_A&A proofs:_ manuscript no. main



13 CO, which can be predicted in the isothermal case:

_v_ [2]
� 13 [−] _[v]_ 12 [2] � iso

[∆] _[z]_ [2]




_[v]_ 12 iso

≈ _q_ [∆] _[z]_ [2]
_v_ [2] 2 _R_ [2]
k



2 _R_ [2] [<][ 5%][,] (24)



claimed that the spiral structure of IM Lup could be generated
by an embedded protoplanet. They performed numerical SPH
simulations of planet-disk interaction and then post-processed
them to compare their results with CO, dust, and scattered light
emission. Interestingly, a high disk mass (∼ 0.1M ⊙ ) is required
to match the scattered light image, so that the sub-micron sized
grains could remain well coupled in the top layers of the disk.
Cleeves et al. (2016) first estimated the disk scale radius _R_ _c_ =
100au by comparing SED to a simple tapered power-law density
profile. Afterwards, Pinte et al. (2018) analyzed CO data and
found that a tapered power law density profile with _R_ _c_ = 284au
more optimally reproduces the data. They also analyzed the rotation curve of the disk and found that while the inner disk is
in good agreement with Keplerian rotation around a 1 ± 0.1M ⊙
star, both the [12] CO and the [13] CO rotation curves become subKeplerian in the outer disk. The authors attributed this effect to
the pressure gradient. Lodato et al. (2023) analyzed [12] CO and
13 CO rotation curves and fitted for star mass, disk mass and scale
radius with an isothermal model. In particular, the authors found
that for the rotation curves extracted with eddy the best-fit are
_M_ ⋆ = 1.012 ± 0.003 _M_ ⊙, _M_ d = 0.096 ± 0.003 _M_ ⊙, _R_ _c_ = 89 ± 1au
and discminer are _M_ ⋆ = 1.02 ± 0.02, _M_ d = 0.10 ± 0.01 _M_ ⊙, _R_ _c_ =
66 ± 1au. We underline that in this work the rotation curves have
been obtained again, and they are different from those of Lodato
et al. (2023). This is also true for the case of GM Aur.
Figure 5 shows both the isothermal and stratified fit. While
for [12] CO, both models describe the rotation curve well, for [13] CO
the isothermal model fails, since the velocity shift is so high that
it cannot be explained just in terms of emitting surface. This
difference is clearly visible when considering the χ [2] red [,] [which]
for the stratified model is considerably smaller. The best-fit parameters for the isothermal model are _M_ ⋆ = 1.055 ± 0.002M ⊙,
_M_ _d_ = 0.200 ± 0.003M ⊙, and _R_ _c_ = 55 ± 1au; while for the stratified model are _M_ ⋆ = 1.1994±0.002M ⊙, _M_ _d_ = 0.106±0.002M ⊙,
and _R_ _c_ = 115 ± 1au. The effects of thermal stratification are visible in Fig. 3. At _R_ ∼ 250au, the difference in the data between
12 CO and 13 CO is on the order of ∼ 10% and it significantly
increases in the outer part. There, neither the stratified model is
able to explain that difference. Izquierdo et al. (2023) pointed
out that the emission from the outer disk is so diffuse that the retrieval of the emitting surface, as well as the velocity extraction,
needs to be taken with care. This is possibly an effect of external
photoevaporation. Indeed, despite the very weak external radiation field irradiating IM Lup, Haworth et al. (2017) showed that
the disk is sufficiently large that the outer part, which is weakly
gravitationally bound, can undergo photoevaporation.


_4.5._ _GM Aur_


GM Aur is a T-Tauri star in the Taurus-Auriga star-forming region that hosts a transition disk. The stellar mass has been estimated dynamically to be _M_ ⋆ = 1.1M ⊙ by Teague et al. (2021), in
agreement with previous measurements (Macías et al. 2018). Its
CO morphology is very complex, showing spiral arms, tails, and
interactions with the environments (Huang et al. 2021). From
thermochemical models of MAPS data, Schwarz et al. (2021)
obtained a disk mass of _M_ _d_ = 0.2M ⊙ and a scale radius of
_R_ _c_ = 111au, making GM Aur a possibly gravitationally unstable disk. Lodato et al. (2023) performed a fitting procedure for
the star mass, disk mass, and scale radius, using an isothermal
model, finding that for GM Aur, the two CO lines provide inconsistent rotation curves, which cannot be attributed only to a
difference in the height of the emitting layer. In addition, the authors provided a simple order-of-magnitude estimate of the ex


where we assumed that typically _z_ / _R_ < 0.5. Hence, if the quantity ( _v_ [2] 13 [−] _[v]_ 12 [2] [)][/] _[v]_ [2] k [is] [higher] [than] [5%,] [the] [system] [cannot] [be] [de-]
scribed by an isothermal model, while it is likely that vertical
stratification plays a significant role. It is important to note that
the Eq. (24) depends on the star mass through _v_ [2] _k_ [. We normalized]
the squared differences of the velocities by the square of the velocity for [13] CO since this quantity is independent of the stellar
mass. Figure 3 shows this quantity for the studied systems.
In the following, we will present the results of each disk,
along with a discussion of the importance of thermal stratification. To compare the results, we performed our fits for both the
vertically isothermal and stratified case. In addition, we computed the dust mass from millimetric emission at 283GHz, using
(Hildebrand 1983):


_d_ [2] _F_ ν
_M_ dust = (25)
κ ν _B_ ν ( _T_ ) [,]


where _d_ is the distance, _F_ ν is the flux density in Jy, κ ν =
2.3(ν/230GHz) [0][.][4] cm [2] g [−][1] is the dust opacity, and _B_ ν is the blackbody spectrum. In our analysis, we assumed _T_ = 20K and
ν = 283GHz, while the flux densities were extracted from MAPS
data. We recall that this equation implies that dust emission is
optically thin. The results are reported in Table 3.


_4.3._ _MWC 480_


MWC 480 is a ∼ 7Myr Herbig Ae star located in the TaurusAurigae star-forming region at a distance of _d_ = 162pc (Montesinos et al. 2009). The most recent value of the stellar mass
has been derived dynamically by Izquierdo et al. (2023) to be
_M_ ⋆ = 1.97M ⊙ . Zhang et al. (2021) through 2D thermochemical
models computed disk mass and scale radius of the MAPS disks.
For MWC 480, these values are _M_ _d_ = 0.16M ⊙ and _R_ _c_ = 200au.
By inspecting the [12] CO and [13] CO rotation curves (Fig. 2),
there is no evident sign of thermal stratification, since the two
curves do not differ significantly. Figure 4 shows that the two
models are nearly indistinguishable, but in Fig. 3 we see that the
stratified model is better at reproducing the data. When we assume an isothermal model, we obtain _M_ ⋆ = 1.969 ± 0.002M ⊙,
_M_ _d_ = 0.201 ± 0.002M ⊙ and _R_ _c_ = 80 ± 1au, while for the stratified model, it is _M_ ⋆ = 2.027 ± 0.002M ⊙, _M_ _d_ = 0.150 ± 0.002M ⊙
and _R_ _c_ = 128 ± 1au. The disk mass obtained with the stratified model is in agreement with the literature value (Zhang et al.
2021). Since the reduced chi-squared χ [2] red [is smaller in the strat-]
ified case (see Table 2), we adopted it as the best-fit model.


_4.4._ _IM Lup_


∼
IM Lup is a young pre-main sequence star ( 1Myr) located in
the Lupus star-forming region at a distance of 158pc (Gaia Collaboration et al. 2018). The dynamical stellar mass is estimated
to be 1.1M ⊙ (Teague et al. 2021), and it hosts an unusually large
disk, extending out to ≈ 300 au in the dust continuum and out to
≈ 1000 au in the gas (Cleeves et al. 2016). The dust continuum
emission shows clear evidence of a spiral morphology, which
may be triggered by gravitational instability (Huang et al. 2018).
Cleeves et al. (2016) first estimated the disk mass from mm visibilities and found a massive disk of 0.2M ⊙ . Verrios et al. (2022)


Article number, page 8 of 16

Martire et al.: Rotation curves in stratified disks



pected velocity shift due to thermal stratification, concluding that
the difference between the two rotation curves could not be explained by this effect. They drew this conclusion by taking into
account the different temperature of the two molecules at their
emission height, _z_ _i_ ( _R_ ), given by Law et al. (2021). However, as
shown in Appendix A, in the azimuthal velocity, it is not only
essential to know the temperature at ( _R_, _z_ ), but also its radial and
vertical gradient at that location.
By analyzing the rotation curves of the two CO isotopolgues
(Fig. 2), a systematic shift between [12] CO and [13] CO curves is
clearly visible, which may possibly be attributed to thermal stratification. When we perform the fitting with the isothermal model,
we obtain (as the best-fit parameters) _M_ ⋆ = 0.872 ± 0.003M ⊙,
_M_ _d_ = 0.312 ± 0.003M ⊙, and _R_ _c_ = 56 ± 1au. This is in agreement
with Lodato et al. (2023) and leads to a high χ [2] red [(see Table][ 2][). As]
a matter of fact, Fig. 6 shows that an isothermal model is not able
to reproduce both [12] CO and [13] CO rotation curves. Conversely,
when thermal stratification is taken into account, the two rotation
curves are compatible and are in agreement with data, especially
for _R_ - 180au. In this case, the best-fit value for the star mass
is _M_ ⋆ = 1.128 ± 0.002M ⊙, which is in line with the literature
values (Teague et al. 2021; Macías et al. 2018). As for the disk
mass, the best-fit value is _M_ _d_ = 0.118 ± 0.002M ⊙ . Finally, the
best-fit value for the scale radius is _R_ _c_ = 96 ± 1au, almost twice
the value obtained with the isothermal model and in good agreement with Schwarz et al. (2021). A stratified model reproduces
the difference between [12] CO and [13] CO rotation curves very well,
as shown in Fig. 3, which leads to a significant decrease in the
χ [2] red [value.]


_4.6._ _HD 163296_


HD 163296 is one of the most well-studied Herbig Ae star system at millimeter wavelengths thanks to its relative close distance ( _d_ = 101pc) and bright disk. The disk presents several features that suggest ongoing planet formation, such as dust rings,
deviations from Keplerian velocities due to gas pressure variations, `"` kinks `"` in the CO emission, and meridional flows (Isella
et al. 2016, 2018; Pinte et al. 2018; Teague et al. 2018; Pinte
et al. 2023; Izquierdo et al. 2022; Calcino et al. 2022; Izquierdo
et al. 2023).
This system has also been extensively studied because there
is considerable evidence to support a massive disk. By modeling the dust lines, Powell et al. (2019) found that the disk
mass is _M_ _d_ = 0.21M ⊙ . As for the scale radius, de GregorioMonsalvo et al. (2013) through radiative transfer modeling found
that _R_ _c_ = 125au is the value that better reproduces dust and CO
ALMA observations. Guidi et al. (2016) presented a multiwavelength ALMA and VLA study of the disk and, via a modeling
of the visibilities, they found that the best-fit value of the scale
radius is _R_ _c_ = 118au, in agreement with de Gregorio-Monsalvo
et al. (2013).

When we fit data with a vertical isothermal model, we obtain (as the best-fit parameters) _M_ ⋆ = 1.842 ± 0.002M ⊙, _M_ _d_ =
0.124 ± 0.001M ⊙ and _R_ _c_ = 38 ± 1au. While the star mass
is realistic, the scale radius is unrealistically small compared
to the gas emission extent on the order of 400au (Law et al.
2021). Additionally, the isothermal model is not able to reproduce the difference between the rotation curves of the two CO
isotopologues (see Fig. 3), resulting in a relatively poor fit with
a large χ [2] red [.] [If] [we] [include] [the] [2D] [thermal] [structure,] [the] [quality]
of the fit increases (see χ [2] red [in] [Table] [2][).] [In] [this] [case,] [the] [best-]
fit for stellar mass and disk mass does not change significantly



( _M_ ⋆ = 1.948±0.002 _M_ ⊙, _M_ d = 0.134±0.001 _M_ ⊙ ), while the scale
radius does shift to _R_ _c_ = 91 ± 1au. Comparing our result for the
disk mass to the literature values, we observe that our fit gives a
value that is roughly half. Figure 7 shows that both the isothermal and the stratified model aptly describe the rotation curve of
12 CO and 13 CO. However, the shift between them, presented in
Fig. 3, is well recovered only by the stratified model, which offers only a partial explanation for the significant increase of the
plotted quantity. The presence of pressure modulated substructures in the rotation curves (Izquierdo et al. 2023) impacts the
quality of the fit (clearly visible in Fig. 3). One possible solution
would be to include them in the fitting model.


_4.7._ _AS 209_


AS 209 is a young T-Tauri star in the Ophiucus star forming
region ( _d_ ∼ 121pc). The most recent stellar mass estimate is
_M_ ⋆ = 1.14M ⊙ (Izquierdo et al. 2023). Fedele et al. (2018) gave
an estimate for the scale radius _R_ _c_ = 80au through the modeling of the mm visibilities . Afterwards, through thermochemical
modeling, they found a dust mass of _M_ dust = 3.5 × 10 [−][4] M ⊙ ; with
a gas-to-dust ratio of 100, this translates into _M_ _d_ = 0.0035M ⊙,
which is in agreement with the recent value _M_ _d_ = 0.0045M ⊙
of Zhang et al. (2021). Interestingly, when inspecting the rotation curves of AS 209 (Fig. 2), the [13] CO is slower compared to
the [12] CO, despite it being closer to the midplane. This trend is
observed up to ∼ 125au. A possible explanation for this is the
compactness of the disk, which makes more difficult to extract
a precise emitting surface due to beam smearing. Indeed, line
centroids from pixels near the center of the disk are an averaged composition of multiple surrounding velocities because of
the limited resolution and the steepness of _v_ ( _r_ ). Since AS209 is
the smallest disk in the sample, it is more prone to be affected
by this in the largest fraction of its total extent compared to
the other sources. When we fit with the isothermal model, we
obtained, as the best-fit parameters, _M_ ⋆ = 1.272 ± 0.003M ⊙,
_M_ _d_ = 0.042 ± 0.003M ⊙, and _R_ _c_ = 45 ± 1au. When we fit
with the stratified model, we obtain as the best-fit parameters
_M_ ⋆ = 1.311 ± 0.001M ⊙, and _R_ _c_ = 126 ± 2au, while for the disk
mass we report a 3−σ upper limit of _M_ _d_ = 0.00025±0.00025M ⊙,
since the best-fit parameter is compatible with zero. Both models are shown in Fig. 8. As for [12] CO, the two models behave in
the same way, showing little difference in the outer edge. Conversely, for [13] CO the isothermal model works better in the inner
part, where [13] CO is slower, while in the outer part the stratified
model describes well the rotation curve. According to the χ [2] red [,]
the stratified model describes the data better (see Table 2).


**5.** **Discussion**


_5.1._ _Thermal stratification in MAPS disks_


Table 2 presents a summary of the findings of this study, comparing the isothermal model with the stratified one. It is evident
from the results that the reduced χ [2] value consistently decreases
when employing the stratified model. This indicates that the inclusion of thermal stratification provides a more effective way
of describing the observed data. In this context, MWC 480 is
particularly interesting. Despite the small kinematic signatures
of thermal stratification, as depicted in Fig. 3, the quality of the
stratified fit is higher and it yields more reliable values for star
mass, disk mass, and scale radius. On the opposite side, GM Aur
is the system that shows the strongest effects of thermal stratification, given that the [12] CO and [13] CO systematically shifted


Article number, page 9 of 16

_A&A proofs:_ manuscript no. main



HD163296 [12] CO



HD163296 [13] CO



10

9

8







7


6


5


4


3


2


0 100 200 300 400 500
R [au]


**Fig. 7.** Same as Fig. 4, but for HD 163296.


AS 209 [12] CO



0 50 100 150 200 250 300 350 400
R [au]


AS 209 [13] CO



10

9


8


7


6


5


4


3


2


8


7





8


7





6


5


4


3


2


50 100 150 200
R [au]


**Fig. 8.** Same as Fig. 4, but for AS 209.


over all the radial extent of the disk. The introduction of thermal
stratification is able to reconcile these differences, reducing the
χ [2] red [by] [an] [order] [of] [magnitude.] [The] [only] [case] [where] [the] [strati-]
fied model encounters challenges in accurately describing both
curves is in AS 209. This system is peculiar because the compactness of the disk influences the extraction of emission surfaces. Consequently, contrary to what expected, we observe that
the [13] CO rotates slower than the [12] CO in the inner part. Despite
that, the χ [2] red [is smaller when thermal stratification is taken into]
account.


Article number, page 10 of 16



6


5


4


3


25 50 75 100 125 150 175
R [au]


_5.2._ _Disk masses_


In this paragraph, we aim to contextualize our work within the
broader framework of disk mass estimation.

One solid tracer of the disk mass is the carbon dioxide HD,
which is a good tracer of the disk gas because it follows the
distribution of molecular hydrogen and its emission is sensitive to the total mass. The first detection of HD emission in
a protoplanetary disk comes from Bergin et al. (2013) for TW
Hya. Afterwards, the detection of HD _J_ = 1 − 0 line was used
to estimate disk mass of GM Aur. The HD based disk mass
is 2.5 − 20.4 × 10 [−][2] M ⊙ (McClure et al. 2016), in line with

Martire et al.: Rotation curves in stratified disks



**Table 2.** Results of the fitting procedure and reduced chi-squared for the
two different models: isothermal and stratified.


_M_ ⋆ [M ⊙ ] _M_ _d_ [M ⊙ ] _R_ _c_ [au] χ [2] red


**MWC 480**


_Isothermal_ 1.969 ±0.002 0.201±0.002 80±1 11.21
_Stratified_ 2.027±0.002 0.150 ± 0.002 128 ±1 6.14


**IM Lup**


_Isothermal_ 1.055 ±0.002 0.200±0.003 55±1 35.68
_Stratified_ 1.194±0.002 0.106 ± 0.002 115 ±1 6.29


**GM Aur**


_Isothermal_ 0.872 ±0.003 0.312±0.003 56±1 90.84
_Stratified_ 1.128±0.002 0.118±0.002 96 ±1 8.48


**HD 163296**


_Isothermal_ 1.842 ±0.002 0.124±0.001 38±1 29.60
_Stratified_ 1.948±0.002 0.134 ± 0.001 91 ±1 19.74


**AS 209**


_Isothermal_ 1.272 ±0.003 0.042±0.003 45±1 25.13
_Stratified_ 1.311±0.001 0.0002 ± 0.0002 126 ±2 10.55


our estimate of 0.118M ⊙ . Finally, the non-detection of HD in
HD163296 (Kama et al. 2020) translates into an upper limit for
the disk mass of 0.067M ⊙, which is almost half of the value we
obtained in this work.

Another reliable method to trace the disk mass uses the
N 2 H [+] . This molecule is a chemical tracer of CO-poor gas and
can be used to measure the CO-H 2 ratio and calibrate CO-based
gas masses. By combining N 2 H [+] with C [18] O, Trapman et al.
(2022) estimated disk masses of three protoplanetary disks, including GM Aur. The value they obtained, 1.5 − 9.6 × 10 [−][2] M ⊙,
is slightly higher compared to our estimate, but it is in an overall
good agreement. This method has also been used to probe disk
masses of protoplanetary disks in the Lupus star-forming region
(Anderson et al. 2022).
In this context, it is worth mentioning observations of the
13 17
C O, a very rare CO isotopologue. Booth et al. (2019) observed this molecule in HD 163296 and this allows for a precise disk mass measurement to be obtained. These authors found
that the disk mass that is better at reproducing observations is
_M_ _d_ = 0.31M ⊙, which is discrepant with our inferred value.
As for the dust, its ability to trace the mass is discussed in
the next subsection.


_5.3._ _Gas-to-dust ratio_


With the knowledge of the disk mass, it is possible to evaluate the
gas-to-dust ratio, using Eq. (25) for the dust mass. The results are
shown in Table 3. We found values between 100 − 250, within
a factor of 2 from the usually assumed valued of 100. This is
surprisingly, due to the assumptions we made to obtain the dust
mass. Indeed, as we have already mentioned, the optically thin
hypothesis for dust emission could lead to a difference of a more
than a factor of 2 in the dust mass calculation (Guidi et al. 2016),
underestimating it. In addition, the dust opacity could also vary
of a factor of ∼ 10, depending on the grain size and composition.
Hence, it is significant overall that the inferred gas-to-dust ratio



**Table 3.** Continuum fluxes at 283 GHz, dust masses from Eq. (25) and
gas-to-dust ratio using the best-fit value of the disk mass of the stratified
model.


_F_ 283 [mJy] _M_ dust [M ⊙ ] Gas-to-dust ratio


**MWC 480** 943.51 0.00138 108
**IM Lup** 536.25 0.00075 134
**GM Aur** 347.95 0.00049 240

**HD 163296** 1127.97 0.00064 202

**AS 209** 414.83 0.00034 < 192


is so close to the standard value. As for AS 209, we estimated an
upper limit for this quantity. Indeed, according to Veronesi et al.
(in prep), the minimum measurable mass with the rotation curve
is 5% of the star mass. Taking this value as an upper limit for
AS 209 disk mass, it is possible to give an upper limit for the
gas-to-dust ratio.


_5.4._ _Toomre Q_


To investigate the presence of gravitational instability, we used
our best-fit parameters for the stratified model to compute the
Toomre parameter (Toomre 1964) which, based on the hypothesis of nearly Keplerian disk (κ ≃ Ω), is



where we used Eq. (1) for the surface density. According to the
WKB quadratic dispersion relation (Lin & Shu 1964; Toomre
1964), the onset of the instability happens when _Q_ ∼ 1. Figure 9 shows the profile of the Q parameter for the MAPS sample, except for AS209, since its disk mass estimate is compatible
with zero. Every disk is gravitationally stable, according to the
Toomre criterion, since _Q_ - 1. Interestingly, the two disks that
showed spiral structures (IM Lup and GM Aur) have a Toomre
profile that is lower than the others, with a minimum value of
∼ 4 for GM Aur and ∼ 6 for IM Lup. Lau & Bertin (1978)
showed that a WKB description of gravitational instability can
still be obtained under less restrictive conditions compared to the
quadratic relation. They showed that disks that are locally stable
according to the Q criterion might still generate large scale spiral
waves. In general, other mechanisms could increase the critical
value of the Toomre parameter, such as external irradiation (Lin
& Kratter 2016; Löhnert et al. 2020) or dust-driven gravitational
instability (Longarini et al. 2023b,a). Hence, we do not exclude
the possibility that gravitational instability is at play in GM Aur
and IM Lup.


**6.** **Conclusions**


The kinematic data of protoplanetary disks display velocity
differences between [12] CO and [13] CO that cannot be explained
through a vertically isothermal model, given the systematic shift
between rotation curves of CO isotopologues. In this work, we
predict how thermal stratification affects the density and the velocity field of a protoplanetary disk.
We used SPH simulations to test our model, finding excellent
agreement, and then we applied it to the MAPS sample. We extracted the rotation curves of CO isotopologues ( [12] CO and [13] CO)
and we carried out fitting for the star mass, disk mass, and scale
radius - both with a vertically isothermal and a stratified model.
The quality of the fit significantly improves when thermal stratification is taken into account and the best-fit parameters are more


Article number, page 11 of 16



, (26)
�



−1
_R_
exp
� � _R_ _c_



_Q_ ≃ _[c]_ [s] [Ω]



_R_



_M_ ⋆


_M_ _d_




_[c]_ [s] [Ω] _[H]_

π _G_ Σ [=][ 2] _R_



_R_
� _R_ _c_



����� mid

_A&A proofs:_ manuscript no. main



25


20





15


10


5


0

25 50 75 100 125 150 175 200
R [au]


**Fig. 9.** Toomre Q parameter of the MAPS disks with the best-fit parameters of the stratified model. We excluded AS 209 because its best-fit
disk mass is compatible with zero.


realistic and aligned with literature. All our results are summarized in Table 2.

Typically, when thermal stratification is considered, the bestfit value for the star mass tends to rise. This can be intuitively
understood, as an isothermal model would favor a star mass that
lies between that of [13] CO and [12] CO; its underestimation is due
to the slower rotation of [12] CO. Conversely, the stratified model
encapsulates the difference between the two curves, mitigating
the underestimation issue and resulting in a more accurate mass
estimate. While an isothermal model provides a satisfactory fit
at small radii, the fit worsens at large radii where the difference
between [12] CO and [13] CO is larger. The fit tries to compensate for
this by increasing the disk mass, most of which resides at large
radii, thereby changing the predicted curve only in the outer parts
of the disk. Ultimately, a more accurate description of the thermal structure through a stratified model leads to a realistic estimate of the scale radius.

We note that the inclusion of the vertical gradient of temperature into our model results in improved χ [2] values across all
systems under examination. This work demonstrates the impact
of thermal stratification in the disk dynamics and highlights the
importance of having a precise knowledge of the disk temperature structure to infer physical quantities such as the stellar mass,
the disk mass and the disk scale radius in a meaningful manner.
Thanks to the generality of our calculations, we can study the
density and velocity profile of thermally stratified disk according different prescription of temperature simply.


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.01055.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO, and NAOJ. This work has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie
Sklodowska-Curie grant agreement # 823823 (RISE DUSTBUSTERS project).
G.R. is funded by the European Union under the European Union’s Horizon Europe Research & Innovation Programme No. 101039651 (discEvol) and by the
Fondazione Cariplo, grant no. 2022-1217. S.F. is funded by the European Union
(ERC, UNVEIL, 101076613). Views and opinions expressed are however those


Article number, page 12 of 16



of the author(s) only and do not necessarily reflect those of the European Union
or the European Research Council. Neither the European Union nor the granting
authority can be held responsible for them. S.F. acknowledges financial contribution from PRIN-MUR 2022YP5ACE. CH is funded by a Research Training Program Scholarship from the Australian Government, and acknowledges funding
from the Australian Research Council via DP220103767. MB and JS have received funding from the European Research Council (ERC) under the European
Union’s Horizon 2020 research and innovation programme (PROTOPLANETS,
grant agreement No. 101002188). The authors thank Pietro Curone and Claudia
Toci for useful discussions.


**References**


Abramowitz, M. & Stegun, I. A. 1970, Handbook of mathematical functions :
with formulas, graphs, and mathematical tables
ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJ, 808, L3
Anderson, D. E., Cleeves, L. I., Blake, G. A., et al. 2022, ApJ, 927, 229
Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJ, 869, L41
Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. 2009,
ApJ, 700, 1502
Bae, J., Teague, R., Andrews, S. M., et al. 2022, ApJ, 934, L20
Bae, J., Teague, R., & Zhu, Z. 2021, ApJ, 912, 56
Barraza-Alfaro, M., Flock, M., Marino, S., & Pérez, S. 2021, A&A, 653, A113
Bergin, E. A., Cleeves, L. I., Gorti, U., et al. 2013, Nature, 493, 644
Bertin, G. & Lodato, G. 1999, A&A, 350, 694
Bollati, F., Lodato, G., Price, D. J., & Pinte, C. 2021, MNRAS, 504, 5444
Booth, A. S., Walsh, C., Ilee, J. D., et al. 2019, ApJ, 882, L31
Calahan, J. K., Bergin, E. A., Zhang, K., et al. 2021, ApJS, 257, 17
Calcino, J., Hilder, T., Price, D. J., et al. 2022, ApJ, 929, L25
Chiang, E. I. & Goldreich, P. 1997, ApJ, 490, 368
Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2016, ApJ, 832, 110
Curone, P., Izquierdo, A. F., Testi, L., et al. 2022, A&A, 665, A25
D’Alessio, P., Cantö, J., Calvet, N., & Lizano, S. 1998, ApJ, 500, 411
D’Alessio, P., Cantó, J., Hartmann, L., Calvet, N., & Lizano, S. 1999, ApJ, 511,
896
Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773
de Gregorio-Monsalvo, I., Ménard, F., Dent, W., et al. 2013, A&A, 557, A133
Dipierro, G., Price, D., Laibe, G., et al. 2015, MNRAS, 453, L73
Dullemond, C. P., Isella, A., Andrews, S. M., Skobleva, I., & Dzyurkevich, N.
2020, A&A, 633, A137
Dutrey, A., Guilloteau, S., Piétu, V., et al. 2008, A&A, 490, L15
Facchini, S., Birnstiel, T., Bruderer, S., & van Dishoeck, E. F. 2017, A&A, 605,
A16
Fedele, D., Tazzari, M., Booth, R., et al. 2018, A&A, 610, A24
Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,
306
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Galloway-Sprietsma, M., Bae, J., Teague, R., et al. 2023, ApJ, 950, 147
Guidi, G., Tazzari, M., Testi, L., et al. 2016, A&A, 588, A112
Hall, C., Dong, R., Teague, R., et al. 2020, ApJ, 904, 148
Haworth, T. J., Facchini, S., Clarke, C. J., & Cleeves, L. I. 2017, MNRAS, 468,
L108
Hildebrand, R. H. 1983, QJRAS, 24, 267
Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018, ApJ, 869, L43
Huang, J., Bergin, E. A., Öberg, K. I., et al. 2021, ApJS, 257, 19
Isella, A., Guidi, G., Testi, L., et al. 2016, Phys. Rev. Lett., 117, 251101
Isella, A., Huang, J., Andrews, S. M., et al. 2018, ApJ, 869, L49
Izquierdo, A. F., Facchini, S., Rosotti, G. P., van Dishoeck, E. F., & Testi, L.
2022, ApJ, 928, 2
Izquierdo, A. F., Testi, L., Facchini, S., Rosotti, G. P., & van Dishoeck, E. F.
2021, A&A, 650, A179
Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113
Izquierdo et al. in prep, 2, 2
Kama, M., Trapman, L., Fedele, D., et al. 2020, A&A, 634, A88
Lau, Y. Y. & Bertin, G. 1978, ApJ, 226, 508
Law, C. J., Teague, R., Loomis, R. A., et al. 2021, ApJS, 257, 4
Lin, C. C. & Shu, F. H. 1964, ApJ, 140, 646
Lin, M.-K. & Kratter, K. M. 2016, ApJ, 824, 91
Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481
Löhnert, L., Krätschmer, S., & Peeters, A. G. 2020, A&A, 640, A53
Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17
Longarini, C., Armitage, P. J., Lodato, G., Price, D. J., & Ceppi, S. 2023a, MNRAS, 522, 6217
Longarini, C., Lodato, G., Bertin, G., & Armitage, P. J. 2023b, MNRAS, 519,
2017
Longarini, C., Lodato, G., Toci, C., et al. 2021, ApJ, 920, L41
Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603
Macías, E., Espaillat, C. C., Ribas, Á., et al. 2018, ApJ, 865, 37

Martire et al.: Rotation curves in stratified disks


McClure, M. K., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 831, 167
Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and
Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura,
501
Molyarova, T., Akimkin, V., Semenov, D., et al. 2017, ApJ, 849, 130
Montesinos, B., Eiroa, C., Mora, A., & Merín, B. 2009, A&A, 495, 901
Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1
Piétu, V., Dutrey, A., Guilloteau, S., Chapillon, E., & Pety, J. 2006, A&A, 460,
L43
Pinte, C., Price, D. J., Ménard, F., et al. 2018, ApJ, 860, L13
Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka,
Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645
Powell, D., Murray-Clay, R., Pérez, L. M., Schlichting, H. E., & Rosenthal, M.
2019, ApJ, 878, 116
Price, D. J., Wurster, J., Tricco, T. S., et al. 2018, PASA, 35, e031
Rabago, I. & Zhu, Z. 2021, MNRAS, 502, 5325
Ragusa, E., Dipierro, G., Lodato, G., Laibe, G., & Price, D. J. 2017, MNRAS,
464, 1449
Rosenfeld, K. A., Andrews, S. M., Hughes, A. M., Wilner, D. J., & Qi, C. 2013,
ApJ, 774, 16
Rosotti, G. P., Teague, R., Dullemond, C., Booth, R. A., & Clarke, C. J. 2020,
MNRAS, 495, 173
Schwarz, K. R., Calahan, J. K., Zhang, K., et al. 2021, ApJS, 257, 20
Shakura, N. I. & Sunyaev, R. A. 1973, A&A, 24, 337
Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14
Simon, M., Guilloteau, S., Beck, T. L., et al. 2019, ApJ, 884, 42
Takeuchi, T. & Lin, D. N. C. 2002, ApJ, 581, 1344
Teague, R., Bae, J., Aikawa, Y., et al. 2021, ApJS, 257, 18
Teague, R., Bae, J., Andrews, S. M., et al. 2022, ApJ, 936, 163
Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018,
ApJ, 860, L12
Terry, J. P., Hall, C., Longarini, C., et al. 2022, MNRAS, 510, 1671
Toci, C., Rosotti, G., Lodato, G., Testi, L., & Trapman, L. 2021, MNRAS, 507,
818
Toomre, A. 1964, ApJ, 139, 1217
Trapman, L., Rosotti, G., Bosman, A. D., Hogerheijde, M. R., & van Dishoeck,
E. F. 2020, A&A, 640, A5
Trapman, L., Rosotti, G., Zhang, K., & Tabone, B. 2023, ApJ, 954, 41
Trapman, L., Zhang, K., van’t Hoff, M. L. R., Hogerheijde, M. R., & Bergin,
E. A. 2022, ApJ, 926, L2
Veronesi, B., Ragusa, E., Lodato, G., et al. 2020, MNRAS, 495, 1913
Veronesi et al. in prep, in prep, 2, 2
Verrios, H. J., Price, D. J., Pinte, C., Hilder, T., & Calcino, J. 2022, ApJ, 934,
L11
Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5



Article number, page 13 of 16

_A&A proofs:_ manuscript no. main



**Appendix A:** **Computing the pressure gradient**


Assuming a barotropic fluid, the pressure contribution to the rotation curve is



+ ρ _[dc]_ s [2]
������ _z_ _dR_



������ _z_



, (A.1)
�



_R_ _dP_


ρ _dR_



= _[R]_
������ _z_ ρ



_d_ ρ
� _c_ [2] s _dR_



which can also be expressed as:



+ _g_ _[d]_ [ρ] [mid]
������ _z_ _dR_



+
�

������ _z_



������ _z_



_R_ _dP_


ρ _dR_



_R_
= _c_ [2] s
������ _z_ ρ mid _g_



_dg_
ρ mid
� _dR_



_dc_ [2]
s,mid
+ _f_
������ _z_ _dR_



_d f_
_R_ _c_ [2]
� s,mid _dR_



=
�



������ _z_



. (A.2)
�



_R_
− γ [′] − (2 − γ)
� � _R_ _c_



**Table B.1.** Values of parameters used in the estimate (B.1).


( _T_ atm / _T_ mid ) 100 _q_ atm − _q_ α |∆( _R_ = 100au)|


_IM Lup_ 1.44 0.05 4.91 5.8 · 10 [−][5]

_GM Aur_ 2.4 0.54 2.57 4.8 · 10 [−][2]

_AS 209_ 1.48 0.41 3.31 1.6 · 10 [−][3]

_HD 163296_ 2.63 0.43 3.01 2.9 · 10 [−][2]

_MWC 480_ 2.56 0.47 2.78 4.1 · 10 [−][2]


**Appendix B:** **Dullemond prescription**


According to Law et al. (2021), the temperature prescription
given by Dullemond et al. (2020) (Eq.(19)) fits the data well,
but we note that in this case, _f_ ( _R_, _z_ = 0) � 1 and the temperature does not smoothly connect to its value at midplane since
_T_ ( _R_, _z_ = 0) � _T_ mid ( _R_ ). To evaluate this discrepancy, considering
_T_ ϵ ( _R_ ) ≈ _T_ mid ( _R_ ), we compute:


∆( _R_ ) = 1 − _[T]_ [(] _[R]_ [,][ 0][)] = 1 − _f_ ( _R_, _z_ = 0) ≈

_T_ mid



_c_ [2] s



2−γ
+ _R_ _[d]_ [ lo][g(] _[fg]_ [)]
� _dR_



Assuming hydrostatic equilibrium in the vertical direction, we
can write an explicit expression for the last term in Eq.(A.2):



− [1]

8


− [1]

8



4

( _R_ )(1 − tanh α) =
�



_T_ atm
� _T_ mid



_T_ atm,100
� _T_ mid,100



2 [�] −3/2
= − _[d]_ [Φ] [⋆]
� _dz_



_z_
−Ω [2] k _[z]_ 1 +
� � _R_




[1] _dP_

ρ _dz_




[Φ] [⋆]

= [1]
_dz_



_dz_ [=]



−4( _q_ atm − _q_ )
(1 − tanh α), (B.1)
�



4
_R_
� � 100au



1 _d_ ( _fg_ )
ρ _[P]_ [mid] _dz_



_fg_ )

_dz_ = _c_ [2] s,mid _[f]_ _[d]_ [ lo] _dz_ [g(] _[fg]_ [)]



(A.3)
_dz_



and, assuming _f_ ( _z_ = 0) = 1 (therefore _T_ ( _R_, _z_ = 0) = _T_ mid ( _R_ )),



−3/2

_dz_ [′] . (A.4)



_z_ [′]


_f_



_z_ ′
1 +
 � _R_



_z_ ′
1 +
 � _R_



� 2 [] 



1
log( _fg_ ) = −
_H_ [2]
mid



� 0 _z_



Deriving with respect to R we obtain:



2

_R_ _[d]_ [ lo][g(] _[fg]_ [)] = _R_

_dR_ ������ _z_ � _H_ mid [3]



1 _z_ [′] _dz_ [′]

[+]
_f_ �1 + ( _z_ [′] / _R_ ) [2] [�] [3][/][2]



_dH_ mid


_dR_



� 0 _z_



which is strongly dependent on _T_ mid, _T_ atm and α. As shown
in Table B.1, the deviation of the actual midplane temperature
from _T_ ( _R_, _z_ = 0) as computed from the prescription given by
Dullemond et al. (2020) is ≲ 10% in our regions of interest
( _R_ - 100au). This discrepancy could have relevance for systems such as GM Aur, HD 163296 and MWC 480. To examine this further, we conducted fits for these systems using both
_T_ mid ( _R_ ) and _T_ ( _R_, _z_ = 0) as the midplane temperature. It was
observed that this choice does not significantly alter the results.
Thus, _T_ mid ≈ _T_ ( _T_, _z_ = 0) and _f_ ( _R_, _z_ = 0) ≈ 1. We can consider
Eqs. (19) and (20) as a good parameterization for the tempera
ture.


**Appendix C:** **Corner plots**


In Figs C.1 and C.2, we present the corner plots of the MCMC
fitting procedure for the studied parameters under, respectively,
the vertically isothermal and the stratified model.



1 _d f_ _z_ [′] _dz_ [′] 1
_f_ [2] _dR_ �1 + ( _z_ [′] / _R_ ) [2] [�] [3][/][2] [−] _H_ mid [2]



1 3 _z_ [′][3] / _R_ [3] _dz_ [′]

_f_ �1 + ( _z_ [′] / _R_ ) [2] [�] [5][/][2]



=
�



� 0 _z_



1

_H_ [2]
mid



� 0 _z_



1 _z_ [′] _dz_ [′]


_f_ (1 + _z_ [′][2] /



˙
_f_ _z_ [′] _dz_ [′]
_f_ [2] (1 + _z_ [′][2] / _R_ [2] ) [3][/][2] [+]



_z_ [′] _dz_ [′] _R_

(1 + _z_ [′][2] / _R_ [2] ) [3][/][2] [+] _H_ mid [2]



� 0 _z_



− _q_
_H_ [2]
mid



� 0 _z_



1



1 _z_ [′] _dz_ [′]


_f_ (1 + _z_ [′][2] /



3

_H_ [2]
mid



� 0 _z_



1



(1 + _z_ [′][2] / _R_ [2] ) [5][/][2] [,]



(A.5)


where · = _d_ / _dR_ . Expanding the logarithmic term is useful since
it is now clear that the azimuthal velocity depends both on the
temperature ( _f_ ) and on the temperature gradient ( _f_ [˙] ) along the radial direction. Moreover, it is easy to see the contribution of the
vertical thermal stratification: in our model _f_ and _f_ [˙] are functions
of _z_ and thus they have to be integrated to compute azimuthal
velocity; whereas in vertically isothermal models, this does not
happen, since _f_ = 1 and _f_ [˙] = 0. We note that it is not analytically
possible to determine generally the sign of Eq. (A.5) and, thus,
the effect that we see on the pressure gradient. However, for all
the considered cases it never overcomes the gravitational contribution and it does lead to a faster deceleration in the rotation.


Article number, page 14 of 16

M = 1.96921 [+0.00072] 0.00074


M


M = 0.87251 [+0.00116] 0.00117


M



M disc = 0.20061 [+0.00081] 0.00078


M disc


M disc = 0.31148 [+0.00140] 0.00134


M disc



Martire et al.: Rotation curves in stratified disks


M = 1.05506 [+0.00109] 0.00110



M


M = 1.84171 [+0.00039] 0.00039


M



R c = 80.06989 [+0.11926] 0.11826


R c


R c = 56.46888 [+0.06167] 0.06677


R c



R c = 55.45156 [+0.13027] 0.12899


R c


R c = 37.76660 [+0.01235] 0.00643


R c



M disc = 0.20026 [+0.00137] 0.00138


M disc


M disc = 0.12420 [+0.00036] 0.00035


M disc



M = 1.27192 [+0.00146] 0.00144


M



M disc = 0.04274 [+0.00155] 0.00157


M disc



R c = 44.84707 [+0.25290] 0.25037


R c



**Fig. C.1.** Corner plots of the MCMC fitting procedure according the vertically isothermal model. They show the distribution of the three relevant
fitting parameters for the five disks of the MAPS large program. From top left to bottom: MWC 480, IM Lup, GM Aur, HD 163296, and AS 209.


Article number, page 15 of 16

M = 2.02682 [+0.00060] 0.00058


M


M = 1.12763 [+0.00105] 0.00102


M



M disc = 0.15010 [+0.00078] 0.00079


M disc


M disc = 0.11840 [+0.00111] 0.00111


M disc



_A&A proofs:_ manuscript no. main


M = 1.19418 [+0.00088] 0.00090



M


M = 1.94772 [+0.00035] 0.00035


M



R c = 128.15549 [+0.14207] 0.14067


R c


R c = 95.91908 [+0.07511] 0.07731


R c



R c = 115.01714 [+0.18328] 0.18033


R c


R c = 91.41981 [+0.03639] 0.03670


R c



M disc = 0.10624 [+0.00124] 0.00125


M disc


M disc = 0.13379 [+0.00046] 0.00046


M disc



M = 1.31123 [+0.00053] 0.00052


M



M disc = 0.00008 [+0.00014] 0.00006


M disc



R c = 125.97150 [+0.76469] 0.75727


R c



**Fig.** **C.2.** Corner plots of the MCMC fitting procedure according the stratified model. They show the distribution of the three relevant fitting
parameters for the five disks of the MAPS large program. From top left to bottom: MWC 480, IM Lup, GM Aur, HD 163296, and AS 209.


Article number, page 16 of 16


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "2D temperature structure parameters for the stratified model (T_mid, T_atm, q, q_atm, zeta_0, alpha, beta)",
  "failed_quote": "As for the stratified model, Law et al. (2021) obtained the two-dimensional (2D) temperature structure of the MAPS disks, using the Dullemond et al. (2020) prescription given by Eq. (19)."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "The MAPS ALMA Large Program provides high spatial and spectral resolution 12CO and 13CO observations with established 2D thermal structures and emitting surfaces for five protoplanetary disks.",
  "failed_quote": "As for the stratified model, Law et al. (2021) obtained the two-dimensional (2D) temperature structure of the MAPS disks, using the Dullemond et al. (2020) prescription given by Eq. (19)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "In the Dullemond et al. (2020) temperature prescription, f(R, z=0) != 1 so the temperature does not smoothly connect to T_mid at the midplane (up to ~5% discrepancy at 100 au).",
  "failed_quote": "We note that in this case, f ( R , z = 0)  1 and, thus, the temperature does not smoothly connect to its value at midplane."
 }
]
```
