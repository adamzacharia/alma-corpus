# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...986..150H\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 10, 2025
Typeset using L [A] TEX **twocolumn** style in AASTeX7


**Origin** **of** **the** **Shell** **Structure** **in** **the** **Primary** **Outflow** **from** **IRAS** **15398-3359**


3
Tomoyuki Hanawa, [1] Yuki [Okoda](http://orcid.org/0000-0003-3655-5270), [2, 3] [Yao-Lun](http://orcid.org/0000-0001-8227-2816) Yang, [3] and Nami [Sakai](http://orcid.org/0000-0002-3297-4497)


1 _Center_ _for_ _Frontier_ _Science,_ _Chiba_ _University,_ _1-33_ _Yayoi-cho,_ _Inage-ku,_ _Chiba_ _263-8522,_ _Japan_
2 _NRC_ _Herzberg_ _Astronomy_ _and_ _Astrophysics,_ _5071_ _West_ _Saanich_ _Road,_ _Victoria,_ _BC,_ _V9E_ _2E7,_ _Canada_
3 _Star_ _and_ _Planet_ _Formation_ _Laboratory,_ _RIKEN_ _Cluster_ _for_ _Pioneering_ _Research,_ _Wako-shi,_ _Saitama,_ _351-0106,_ _Japan_


(Received March 31, 2025; Revised May 8, 2025; Accepted May 12, 2025)


Submitted to The Astrophysical Journal


ABSTRACT


IRAS 15398-3359, a Class 0 protostar in Lupus I star forming region, is associated with three
generations of outflows. The primary outflow, i.e., the most recent one, shows internal structure
named “shell structure” in the near infrared emission map. The shell structure is also seen in the
emission lines of CO, H 2 CO, and others species. We find a similar structure in an underexpanded jet
produced in aerodynamics and other engineering applications. A high pressure gas ejected through a
nozzle expands to form a supersonic flow. When the pressure of the ejected gas becomes lower than
that of the ambient gas, the jet is compressed to form a shock wave. The shock heated gas expands
again to form substructures along the jet. We examine the similarity between the primary outflow
of IRAS 15398-3359 and industrial underexpanded jet and the possibility that the shell structure of
the former is due to repeated expansion and compression in the direction perpendicular to the jet
propagation.


_Keywords:_ Star formation (1569); Protostars (1302); Stellar jets (1607)



1. INTRODUCTION


Jets and outflows are important signatures of protostars. They emerge within 100 au from a protostar and
can reach a few parsec away from the origin. Recent
high resolution imaging observations with ALMA and
JWST are valuable for studying their launch. IRAS
15398 _−_ 3359 is one of the sources that both ALMA and

JWST have observed to obtain sub-arcsecond images in
the radio and infrared wavelengths.
IRAS 15398 _−_ 3359 is a Class 0 protostar in the Lupus
I star forming region located at a distance of 154.9 [+3] _−_ 3 _[.]_ _._ [2] 4
pc (Galli et al. 2020) and is associated with multiple
outflows. Tachihara et al. (1996) discovered a CO outflow with a 4m single dish telescope. Oya et al. (2014)
observed the primary outflow extended in the northeast and southwest with ALMA. The northeastern and

southwestern outflows are red- and blue-shifted respectively. Okoda et al. (2021a) discovered a secondary outflow extending to the southeast. The secondary out

Email: hanawa@faculty.chiba-u.jp



flow is 8 _[′′]_ away from the protostar on the plane of the
sky, while the primary outflow seems to be connected
to the protostar. Sai et al. (2024) discovered another
pair of outflows at a distance of 30 _[′′]_ _−_ 75 _[′′]_ in the northern and southern regions. This third outflow is also reported by Guzm´an Ccolque et al. (2024). The secondary
and third outflows indicate that the outflow activity of
IRAS 15398 _−_ 3359 is episodic and the primary outflow is
due to the most recent activity (Okoda et al. 2021a; Sai
et al. 2024; Guzm´an Ccolque et al. 2024). Since these
three generations of outflow extend in different directions, they are likely to be driven by different alignment
channels.

The primary outflow has an internal structure. The
integrated intensity of H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ) emission line
shows a node at a distance of _∼_ 5 _[′′]_ in the blue-shifted
outflow (see Figure 1(a) of Okoda et al. 2021a). Vazzano
et al. (2021) shows the change in the intensity-weighted
line-of-sight velocity in [12] CO ( _J_ = 2 _−_ 1) near this node.
The infrared image taken with JWST shows four shells
also in the blue-shifted outflow (Yang et al. 2022). Figure 1, the reproduction of Figure 1 of Okoda et al.

2















_z_




|Col1|Col2|Col3|
|---|---|---|
||_v_0|_v_0|
||_v_0||
||||
||||









**Figure** **1.** RGB image built from a composite of the three
filter (F560W, F770W, and F1000W) MIRI images. The
angular separation 5 _[′′]_ correspond to the deprojected distance
of 824 au for the assumed inclination angle of 20 _[◦]_ (Oya et al.
2014). Reproduction of the top panel of Figure 1 of Okoda
et al. (2025).


(2025), shows the infrared emission obtained with the
three filters (F560W, F770W, and F1000W) of JWST
by a composite image. The base of the primary outflow is bright in infrared. Since the infrared emission is
rich in the rotational transition of H 2 molecules (Yang
et al. 2022), the outflow gas is hot ( _T_ ≳ 10 [3] K) at least
within the regions of several hundreds au (see Okoda
et al. 2025, for the temperature distribution). The thermal energy may accelerate the outflowing gas. Since the
internal structure seen in the infrared emission is cor
related with that observed in the radio line emissions,
they are likely to have a common origin.
A possible origin of the internal structure is time variability of the outflow activity. Vazzano et al. (2021)
considered a scenario that IRAS 15398 _−_ 3359 has un
dergone four accretion outbursts which have initiated
four times of outflow activities. Another possibility is
magnetohydrodynamical instability of the outflow (see,
e.g., Shang et al. 2023). However, these scenarios are not
conclusive. It is worth seeking another possibility as an
origin of the internal structure in the primary outflow.
Jets and outflows have been studied for more than a
half century in aeronautical engineering (see, e.g, Franquet et al. 2015, for a review). A high pressure gas
emerging from a nozzle evolves into a supersonic flow
called “underexpanded outflow.” Figure 2 shows the
internal structure of the underexpanded outflow for a
high jet/ambient over pressure ratio schematically. For
simplicity, we omitted expansion fans often included in



**Figure** **2.** A schematic view of an underexpanded outflow
from a nozzle. The blue curves denote the shock waves and

highlighted by the thick curve is the Mach disk. The cyan
curves denote the jet boundary, i.e., the boundary between
the outflowing and ambient gases. The symbols and letters
explain the terminology used in the text.


the similar diagrams. The initially high pressure gas
expands preferentially in the direction normal to the
exit plane of the nozzle to be collimated. It is well
known that the the underexpanded jet outflow has “barrel structure”, i.e., semi-periodic change in the outflow
width. The barrel closest to the nozzle is bounded by
shock waves (see Figure 2). The thick blue line is called
Mach disk where the gas is highly compressed through
a shock. The side of the barrel is bounded by oblique
shocks. The jet gas is decelerated once to be hot, dense,
and subsonic at the shock. The gas decelerated at the
Mach disk expands again to be accelerated and repeats
expansion from and convergence to the jet axis. We
think that a similar mechanism is responsible for the
shell structure of IRAS 15398 _−_ 3359.

_−_
In this paper we compare IRAS 15398 3359 and engineering underexpanded jet outflow and its substructure
to examine the possibility that the former’s shell structure and latter’s barrel structure are formed by the same
physical mechanism. If they have a common origin, we
can repurpose the knowledge in industrial science for our
understanding of protostellar outflows.
This paper is organized as follows. We analyze the
outflow from IRAS 15398 _−_ 3359 using the archival data
of ALMA and JWST in §2. We review the underexpanded jet outflow in §3 and show a simple hydrodynamic model in §4. Discussions and conclusion are given
in §5.


2. OBSERVATIONS


2.1. _Observation_ _Specifications_


Our analysis is based on the archival data of ALMA
and JWST. The H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ) and CS ( _J_ =
5 _−_ 4) lines were observed in the project 2018.1.01205.L
(PI: Satoshi Yamamoto), as a part of ALMA large
program FAUST (Codella et al. 2021, [http://faust-](http://faust-alma.riken.jp)
[alma.riken.jp).](http://faust-alma.riken.jp) The [12] CO ( _J_ = 2 _−_ 1) line was taken
from the ALMA archival data (2013.1.00879.S; Yen et al.

2013). The observation parameters are described by
Okoda et al. (2021a), Okoda et al. (2023), and Yen et al.
(2017). The data reduction details of both data are also
given by Okoda et al. (2025).
The MIRI images and spectral cubes were taken
with the Medium Resolution Spectroscopy (MRS) by
the JWST CORINOS program (Yang et al. 2022)
(program 2151, PI: Y.-L. Yang). The imaging data
were reduced with JWST calibration pipeline v.1.14.0
(Bushouse et al. 2024) using the calibration reference
data `jwst` `1231.pmap`, while the spectroscopic data
were reduced with JWST calibration pipeline v.1.12.5
(Bushouse et al. 2023) using the calibration reference
data `jwst` ~~`1`~~ `183.pmap` . The MIRI images were taken
with three filters, F560W, F770W, and F1000W, centered at 5.6, 7.7, and 10.0 _µ_ m, respectively. The FWHM
of the PSF ranges from 0 _[′′]_ _._ 207 to 0 _[′′]_ _._ 328. We use the
imaging data taken simultaneously with the spectroscopic observation pointing toward a dedicated background position, because the field of view (FoV) of the
image serendipitously covers the blue-shifted outflow of
IRAS 15398 _−_ 3359. The MRS data cover the 4.9–28 _µ_ m
range with four integral field units, which have their
FoVs range from 3 _[′′]_ _._ 2 _×_ 3 _[′′]_ _._ 7 to 6.6 _[′′]_ _×_ 7.7 _[′′]_ . The spectral resolving power ( _λ/_ ∆ _λ_ ) decreases from _∼_ 3700 to _∼_ 1300
with wavelengths.


2.2. _Observation_ _Results_


Figure 1 shows the southwest part of the primary outflow by RGB image built from a composite of three filter
(F560W, F770W, and F1000W) MIRI images (Okoda
et al. 2025). The MIRI image shows four bright shells
named shells 1, 2, 3, and 4 in the ascending distance
from the protostar. As mentioned earlier, the MIRI image traces a hot molecular gas since the line emission
of H 2 molecule is dominant in the filters (see, e.g, Yang
et al. 2022). The shell structure implies the spatial variation in the temperature and density. The first shell is
_d_ s1 =340 au (2 _[′′]_ _._ 06 from the protostar on the sky) while
the diameter of the barrel is _D_ w1 = 322 au (2 _[′′]_ _._ 08). The
aspect ratio, _d_ s1 _/D_ w1 = 1 _._ 05, gives a clue to estimate the
pressure ratio when an underexpanded outflow model
is applied. The second shell is _d_ s2 = 1060 au (6 _[′′]_ _._ 42)
away from the protostar and the jet diameter is _d_ w2 =
448 au (2 _[′′]_ _._ 87). Here, _d_ s1 and _d_ s2 denote the deprojected
distances while _D_ w1 and _D_ w2 denote the projected distance on the sky. The aspect ratios derived from these
numbers are also useful for assessing our model.
A similar structure is also seen in the molecular emission lines of H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ), CS ( _J_ = 5 _−_ 4) (Okoda
et al. 2021b), and [12] CO ( _J_ = 2 _−_ 1) (Vazzano et al.
2021). Not only the integrated intensity but also the



3


Doppler shift of molecular line emission shows features
correlated with the shell structure (see Figure 4 of Vazzano et al. 2021). Throughout this paper we adopt the
systemic velocity of _v_ sys = 5 _._ 24 km s _[−]_ [1], the central value
measured by Yen et al. (2017) from the C [18] O ( _J_ =2 _−_ 1)
emission line. Figure 3 shows the weighted velocity distribution and position-velocity of (a) H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ),
(b) CS ( _J_ = 5 _−_ 4), and (c) [12] CO ( _J_ = 2 _−_ 1) emission
lines. The left panels show the whole primary outflows
while the right panels are enlargement around the protostar. The position of the protostar is designated by
the plus signs on each panel. The locations of shells 1,
2, 3, and 4 are shown in the left panel of Figure 3b. Shell
1 is denoted also by the red dashed curves in the right
panels. We find a semi-periodic change in the velocity
not only in the blue lobe but also in the red lobe. See
also Figure 4 of Thieme et al. (2023) for a higher angular resolution map of [12] CO ( _J_ = 2 _−_ 1) around the
protostar. The weighted velocity of H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 )
and CS ( _J_ = 5 _−_ 4) are similar while that of [12] CO
( _J_ = 2 _−_ 1) is slightly different. We think that the difference is mainly due to the optical depth, i.e., the abundance and excitation condition. The velocities of H 2 CO
(3 0 _,_ 3 _−_ 2 0 _,_ 2 ) and CS ( _J_ = 5 _−_ 4) show only small deviation
from the systemic velocity ( _v_ sys = 5.24 km s _[−]_ [1] ) around
the protostar. The line emission is clearly blue-shifted
between shells 1 and 2. This velocity change implies acceleration of the outflow. The weighted velocity between
shells 1 and is low especially in the CS ( _J_ = 5 _−_ 4) emission. Note the red-shifted emission in the blue lobe and
the blue-shifted one in the red lobe (see also Figure 2 of
Okoda et al. 2025). These apparently reverse flows appear near the outflow axis. The slow and reverse flows
imply deceleration. We do not find significant asymmetry with respect to the outflow axis, which means
that rotation around the outflow axis is insignificant. If
the outflow rotates fast, we will find a velocity gradient
perpendicular to the outflow axis (see, e.g., Matsushita
et al. 2021, for an example of rotating outflows). [12] CO
( _J_ = 2 _−_ 1) shows a larger and smoother deviation from
the systemic velocity (note that the color scale of [12] CO
( _J_ = 2 _−_ 1) is different from those of H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 )
and CS ( _J_ = 5 _−_ 4)). Still we find a similar decrease
in the weighted velocity between shells 2 and 3 in [12] CO
( _J_ = 2 _−_ 1). All the lines show the northwestern hole of
a slow (or reverse) flow at a distance of _∼_ 7 _[′′]_ ( _∼_ 1000
au) from the protostar.
Figure 4 shows the position velocity diagrams for
H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ) and CS ( _J_ = 5 _−_ 4) along the outflow
axis shown in the left panel of Figure 3a. The vertical
dotted lines denote the locations of shells 1, 2, and 3.
They show a red component in addition to a blue com

4



(a)


(b)















|(c)|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|||
|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|||
|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|Vsys =5.24 km・s<br>-1|||
|Vsys =5.24 km・s<br>-1|||||||


**Figure** **3.** Moment 1 maps of (a) H 2 CO (3 0 _,_ 3 _−_ 2 0 _,_ 2 ) (b) CS ( _J_ = 5 _−_ 4) and (c) [12] CO ( _J_ = 2 _−_ 1). The right panels are the
enlargement of the left panels around the protostar (+). The jet axis (P.A. 235 _[◦]_ ) and the shell locations are shown in the left
panels of (a) and (b), respectively. The red dashed curves in the right panels represent shell 1 shown in Fig. 1.

|Col1|Col2|Sh|(a)<br>ell1 Sh|PA<br>. .<br>ell2 Shel|235°<br>l3|Col7|
|---|---|---|---|---|---|---|
|||||Vsys<br>5.24|=<br> km・s<br>-1|=<br> km・s<br>-1|


|Col1|Col2|Col3|(b)|PA<br>. .|235°|Col7|
|---|---|---|---|---|---|---|
||||||||


Direction along the outflow axis [arcsec]


**Figure** **4.** PV diagrams along the outflow axis (P.A. 235 _[◦]_ ).
The white dotted lines show the positions of the four shell
structures. The systemic velocity of 5.24 km s _[−]_ [1] is shown in
the horizontal dotted lines.


ponent in the interval between the protostar and shell
3. The blue component shows a steep velocity gradient
suggesting acceleration and terminates at shell 1. The
red component appears around 1 _[′′]_ ( _∼_ 150 au) from the
protostar. The red component of CS ( _J_ = 5 _−_ 4) looks
to continue beyond shell 2 while changing the velocity
and intensity. We find another steep velocity gradient
starting from shell 1. Existence of the two components
imply either diverging or converging flow along the line
of sight, i.e., in the direction perpendicular to the outflow axis. The velocity gradient is more likely to be due
to acceleration/deceleration in the outflow rather than
the initial velocity at the time of ejection.

Okoda et al. (2025) derived the temperature and column density of H 2 molecules from the JWST MIRI MRS
observations, which covers a _∼_ 3 _[′′]_ _−_ 5 _[′′]_ region around



5


the protostar (see their Figures 4a and 4b for the temperature and column density, respectively). The temperature is as high as _∼_ 1300 K near the protostar and
decreases with the distance below 1000 K at shell 1. The
column density is as high as _N_ _≃_ 10 [20] cm _[−]_ [2] around the
protostar and decreases to _N_ _≃_ 10 [19] _[.]_ [5] cm _[−]_ [2] near shell

1.

Infrared emission from ionized elements supports the
idea that the outflow gas is hot. Figure 5 show
continuum-subtracted intensity of [Fe II ] 25.99 _µ_ m,
17.935 _µ_ m, and [Ne II ] 12.81 _µ_ m. The blue background
denotes MIRI F560W image taken with JWST (Yang
et al. 2022). [Fe II ], [Ne II ], and [Ne II ] emissions are
strong around the protostar and between the first and
second shells. In other words, they have a gap near
the first shell, which is consistent with the temperature derived from H 2 line emissions. These ionized el
ements also show the substructure correlated with the

shell structure. Differences among the line emissions
maps are mostly due to the wavelength dependent angular resolutions.
The temperature decrease with the distance from the
protostar is not likely to be radiative cooling. If the thermal energy is lost by radiative cooling, we need another
heating source for the hot region between shells 1 and
2. It is likely to be due to adiabatic expansion, which is
consistent with the decrease in the column density and
the increase in the blue-ward shift in the emission line.

The adiabatic expansion converts thermal energy into a
kinetic one, which can be used to heat up again the gas
through a shock wave.


3. UNDEREXPANDED JET


A high pressure gas emerging from a nozzle evolves
into an underexpanded jet. The study of such a jet has
a long history. It can be traced back to the 19th century. A review by Franquet et al. (2015) summarizes
the history and current knowledge. Though many numerical simulations have been done for astronomical jets
and outflows, most of them are focused on the launch
and collimation. Some simulations are focused on the

internal structure, i.e., the formation of the Mach disk
(see, e.g., Norman et al. 1982; Komissarov & Falle 1998;
Smith & Keogh 2022; Smith & Richards 2023) and related structure. However, industrial jets have been studied much more intensively and the theory is verified by
experiments and well established. Thus, we refer to
Franquet et al. (2015) in the following since other reviews show essentially the same results.
In aeronautical science, the jet is divided into three
zones: (1) the nearfield zone, (2) the transition zone,
and (3) the farfield zone (see, e.g., Franquet et al. 2015).

6



34°09'05.00"


10.00"


15.00"


20.00"



10 [2]







10 [2]


10 [1]



10 [2]


10 [1]



15 [h] 43 [m] 02.50 [s] 02.00 [s] 01.50 [s]


Right Ascension (J2000)



15 [h] 43 [m] 02.50 [s] 02.00 [s] 01.50 [s]


Right Ascension (J2000)



15 [h] 43 [m] 02.50 [s] 02.00 [s] 01.50 [s]


Right Ascension (J2000)



**Figure** **5.** Contours show intensities of (left) [Fe II ] 25.99 _µ_ m, (center) 17.935 _µ_ m, and (right) [Ne II ] 12.81 _µ_ m taken with
JWST (Yang et al. 2022). The color denotes MIRI image taken with F560W filter on JWST.



The nearfield zone is further divided into two components: the core and the mixing layer. The gas expands
adiabatically in the core, where the pressure, density,
and temperature decreases with distance from the end of
nozzle. The pressure gradient accelerates the ejected gas
to be supersonic. The supersonic jet undergoes a shock
and gets compressed to be hot and dense. The structure made by the shock is called the Mach disk. The
jet between the nozzle end to the Mach disk is named
“barrel” from its appearance (see Figure 2). The jet
width is controlled by the pressure balance between the
jet and the ambient gas. The hot dense gas ahead of
the Mach disk is accelerated again to form subsequent
substructures along the jet axis.
The morphology and structure of the jet depends
mainly on the pressure ratio, _P_ 0 _/P_ _∞_, where _P_ 0 and _P_ _∞_
denote the initial pressure of the injected gas and the
ambient gas pressure, respectively. The distance to the
Mach disk ( _L_ m ) is proportional to the diameter of the
nozzle ( _D_ _j_ ). Crist et al. (1966) derived an approximate
formula,



derived an empirical formula



_D_ m



_P_ 0 _−_ 3 _._ 9 _,_ (2)
� _P_ _∞_



=0 _._ 36
_D_ j



for smooth convergent nozzle, where _D_ m denotes the diameter of the Mach disk. The ratio depends only slightly
on the nozzle shape in particular when the pressure ratio
is high.
When the pressure ratio is high, the jet is variable.
Though the flow in the core is laminar, the flow beyond
the Mach disk is turbulent. See Figure 3 of Yu et al.
(2013) shows the instantaneous and time-averaged images of the jet for _P_ 0 _/P_ _∞_ = 10.
We can evaluate the acceleration of the jet gas applying the Bernoulli’s theorem. When the flow is stationary
adiabatic in the barrel, the sum of the kinetic energy and
specific enthalpy




[1] _γP_ [1]

2 _[v]_ [2] [ +] ( _γ −_ 1) _ρ_ [=] 2



_H_ = [1]




[1] 2 _[v]_ 0 [2] [+] ( _γ −γP_ 1) 0 _ρ_ 0 _,_ (3)



is constant along the stream line, where _v_, _ρ_, and _γ_
denote the velocity, density, and specific heat ratio, respectively. Given the initial velocity is much lower than
the sound speed ( _|v_ 0 _| ≪_ _[√]_ _γP_ 0 _/ρ_ 0, the jet becomes transonic when the temperature reaches _T_ = 2 _T_ 0 _/_ ( _γ_ + 1).
The specific enthalpy is evaluated to be



_L_ m


=
_D_ j



_P_ 0
_,_ (1)
~~�~~ 2 _._ 4 _P_ _∞_



analytically. Young (1975) discussed that the coefficient
in Equation (1) should be a function of the specific heat
ratio, though the dependence is weak. Equation (1) is
valid for a wide range of _P_ 0 _/P_ _∞_ . Hatanaka & Saito
(2012) examined the effects of the nozzle shape on the
aspect ratio. Equation (1) gives a fairly good fit in
the range 14 ≲ _P_ 0 _/P_ _∞_ ≲ 80 when the nozzle is either
straight or divergent. Equation (1) overestimate _D_ _m_ _/D_ _j_
a little when the nozzle is straight. We can expect Equation (1) gives a good estimate for an astronomical jet
though it does not emerge from a nozzle.
The pressure ratio controls the ratio between the diameters of the Mach disk and jet nozzle. Addy (1981)



_γP_ _T_
�5 _._ 0 km s _[−]_ [1] [�] [2] [ �] _,_ (4)
( _γ −_ 1) _ρ_ [=] 2000 K �



for a molecular gas having the mean molecular weight,
_µ_ = 2 _._ 3 _m_ H . Equation (4) provides an estimate for the
gas velocity accelerated by the pressure.


4. HYDRODYNAMIC MODEL


4.1. _Model_ _Setting_


We make a hydrodynamic model to reproduce the
shell structure seen in IRAS 15398 _−_ 3359. For simplicity

7



we assume that the outflow source maintain high temperature and high density . We ignore gravity, magnetic
field, radiative cooling/heating processes for simplicity.
We use the cylindrical coordinates, ( _r, φ, z_ ) and assume the symmetry in the _φ_ -direction ( _∂/∂φ_ = 0).
Thus, the density ( _ρ_ ), pressure ( _P_ ), and velocity ( **v** =
( _v_ _r_ _, v_ _z_ )) are functions of ( _r, z, t_ ), where _t_ denotes the
time, which is set to be _t_ = 0 at the initial stage, i.e.,
the onset of the outflow ejection. The gas is assumed
to be an ideal gas having the mean molecular weight
_µ_ = 2 _._ 3 and the specific heat ratio, _γ_ = 7 _/_ 5. Then the
pressure and density are expressed as


_P_ = _nk_ B _T,_ (5)


_ρ_ = _µm_ H _n,_ (6)


where _k_ B and _m_ H denote the Boltzmann constant and
the mass of hydrogen atom, respectively. We use the
number density ( _n_ ) and temperature ( _T_ ) instead of _P_
and _ρ_ when we show our numerical results.
We assume a geometrically thin gas disk placed at
_z_ = 0 and consider the half space above the disk plane
( _z_ _>_ 0). The half space is occupied initially by an ambient gas of which density and pressure are _ρ_ _∞_ and _P_ _∞_,
respectively. The ambient gas is at rest at the initial
stage ( _t_ = 0).
We use the finite volume method in our numerical simulations. The spatial resolution, i.e., the numerical cell
width is uniform at ∆ _r_ in the main part of the computation domain, 0 _≤_ _r_ _≤_ _N_ _r_ ∆ _r_ and 0 _≤_ _z_ _≤_ _N_ _z_ ∆ _z_,
where _N_ _r_ and _N_ _z_ are 780 and 7560, respectively. The
cell width increases exponentially beyond _r_ _>_ _N_ _r_ ∆ _r_
and _z_ _>_ _N_ _z_ ∆ _r_ . The cell width is larger by a factor
of 1.25 compared to that of the inner adjacent cell. We
placed 40 cells in the _r_ - and _z_ -directions outside the
main part. Thus the outer boundary is located very far
from the main part. We placed a fixed outer boundary
at _r_ = 2 _._ 47 _×_ 10 [4] au and _z_ = 2 _._ 47 _×_ 19 [4] au but no

disturbance reaches the outer boundary.
We set an outflow engine as a boundary condition on
_z_ = 0 plane. The nozzle of the jet is assumed to be a
circle having the radius, _R_ 0 . The pressure is fixed to be



fixed to be



_ρ_ ( _r, z_ _<_ 0)=








 _ρ_ 0 ( _r_ _≤_ _R_ )

 _ρ_ _∞_ ( _r_ _> R_ )



_,_ (8)
_ρ_ _∞_ ( _r_ _> R_ )



_v_ _r_ ( _r, z_ _<_ 0)=0 (9)



_v_ _z_ ( _r, z_ _<_ 0)=








 _v_ jet ( _r_ _≤_ _R_ )

0 ( _r_ _> R_ )



_,_ (10)
0 ( _r_ _> R_ )



_P_ ( _r, z_ = 0)=








 _P_ 0 ( _r_ _≤_ _R_ 0 _−_ 3∆ _r_ )

 _P_ _∞_ ( _z_ _≥_ 0)



_._ (7)
_P_ _∞_ ( _z_ _≥_ 0)



As summarized in Table 1 we set the initial flow to be
subsonic ( _v_ jet _/_ � _γP_ 0 _/ρ_ 0 = 0 _._ 27). Remember that the
supersonic collimated outflow was given as the initial
condition in the simulations of Norman et al. (1982),
Smith & Keogh (2022), and others. Our simulations
include initial acceleration and collimation though we
assume hot dense gas and disk as a source of acceleration
and collimation, respectively.
We use the number density, _n_ 0 = _ρ_ 0 _/_ ( _µm_ H ) and
_n_ _∞_ = _ρ_ _∞_ _/_ ( _µm_ H ), instead of _ρ_ 0 and _ρ_ _∞_ to specify the
initial density distribution. We also use _T_ 0 = _P_ 0 _/_ ( _k_ B _n_ 0 )
and _T_ _∞_ = _P_ _∞_ _/_ ( _k_ B _n_ _∞_ ) to define the pressure distribution. We solve the hydrodynamical equations numerically with the second order accurate scheme which can
capture a shock wave without spurious oscillations. We
employ a flux split method based on approximate Riemann solution to avoid negative density and pressure.
Our numerical code has been proved to reproduce a
strong shock wave by solving the shock tube problem.
It has been applied to gas accretion to a gas disk rotating around a protostar (Hanawa & Matsumoto 2021;
Hanawa et al. 2022, 2024).


4.2. _Canonical_ _Model_


First we show model A in which the model parameters
are taken to be _n_ 0 = 10 [7] cm _[−]_ [3], _n_ _∞_ = 5 _×_ 10 [6] cm _[−]_ [3],
_T_ 0 = 2000 K, and _T_ _∞_ = 100 K. Then the pressure ratio
is set to be _P_ 0 _/P_ _∞_ = _n_ 0 _T_ 0 _/_ ( _n_ _∞_ _T_ _∞_ ) = 40. The jet is
assumed to emerge from the circle of _R_ = 50 au with
the initial velocity _v_ jet = 0 _._ 845 km s _[−]_ [1], which is much
smaller than the sound speed at 2000 K, 3.18 km s _[−]_ [1] .
The spatial resolution is ∆ _r_ = 0 _._ 714 au in the main
part of the computation box of 0 _≤_ _r_ _≤_ 557 au and
0 _≤_ _z_ _≤_ 5400 au. The jet emerging circle is resolved
with _R/_ ∆ _r_ = 70 numerical cells.
Figure 6 shows model A by a snap shot at _t_ =
7 _._ 47 _×_ 10 [3] yr. The top and second panels show the
density ( _n_ ) and the temperature ( _T_ ) in the logarithmic
scale by color. The third and fourth panels show the velocity ( _v_ _r_ _, v_ _z_ ). Each panel shows also the area of _r_ _<_ 0,
which is flipped over from that of _r_ _>_ 0, for comparison with IRAS 15398 _−_ 3359. All the panels show the
Mach disk at _z_ _≃_ 300 au. Though the flow is laminar in the barrel ( _z_ ≲ 300 au), it is turbulent in the



The pressure decreases from _P_ 0 to _P_ _∞_ in the _R_ 0 _−_ 3∆ _r_ _<_
_r_ _< R_ 0 at a constant rate. The density and velocity are

8


**Figure** **6.** Each panel shows the number density ( _n_ ), temperature ( _T_ ), and velocity ( _v_ _r_, _v_ _z_ ) at _t_ = 7 _._ 47 _×_ 10 [3] yr in
model 40. The time evolution of model A is shown in the

associated movie. The animation shows that the gas emerges
from the left and the head proceeds rightward. The outflow
is turbulent and associated with shock waves. The animation

shows the sequence from zero to 443.98 years. The duration
of the animation is 18 seconds.


region beyond the Mach disk. The flow is variable as
shown in the animation associated with Figure 6. Still
we find a semi-periodic change in the velocity, ( _v_ _r_ _, v_ _z_ ).
This change is due to the pressure balance between the
outflow and ambient gases. The longitudinal velocity is
negative ( _v_ _z_ _<_ 0) near _z_ = 1000 au. This substructure
evolves into the second shell. The outflow compresses
the ambient gas ahead of it through a shock. The shock
compressed gas has the highest density and a moderate
temperature of several hundreds K.


model _P_ 0 _/P_ _∞_ _n_ 0 _/n_ _∞_ _T_ 0 _T_ _∞_ _v_ jet
A 40 2.0 2000 K 100 K 0.85 km s _[−]_ [1]


B 62.5 3.125 2000 K 100 K 0.85 km s _[−]_ [1]


C 40 0.4 2000 K 20 K 0.85 km s _[−]_ [1]


**Table** **1.** Model Parameters.


Figure 7 is the same as Figure 6 but shows a later
stage at _t_ = 1 _._ 498 _×_ 10 [4] yr. The outflow head reaches
_z_ _∼_ 2200 au and the density is highest in the shock



**Figure** **7.** The same as Figure 6 but for the stage at
_t_ = 1 _._ 498 _×_ 10 [4] yr.


compressed gas ahead of it. The semi-periodic structure
is prominent in the velocity.
Figure 8 shows the barrel structure at _t_ = 1 _._ 498 _×_
10 [4] yr. The upper and lower panels denote the density and temperature distributions by color, respectively.
The arrows overlaid on the upper panel denote the velocity. As expected, the structure is essentially the same
as that illustrated in Figure 2. A hot dense gas flows
between the jet boundary and the oblique shock wave.
The Mach disk is bent at this stage. See the animation
associated with Figure 8 for the formation and evolution
of the Mach disk.
Figure 9 shows the longitudinal velocity ( _v_ _z_ ) at the
stage shown in Figure 7 as a function of _z_, i.e., the distance from the nozzle. The dark blue curve denotes _v_ _z_
on the _z_ -axis while the light blue curve shows the maximum of _v_ _z_ at a given _z_ . The jet flow is not straight as
shown in the bottom panel of Figure 7. The longitudinal
velocity has a large jump at several places, i.e., at the
shock fronts. The Mach number, the ratio of the flow
velocity and sound speed, reaches 4.75 and drops suddenly at _z_ = 293 au, i.e., just in front of the Mach disk.
The Mach number exceeds unity at _z_ = 7 _._ 5 au and the
flow is supersonic from there to the Mach disk. The jet
flow is off-axis in the range of 300 au ≲ _z_ ≲ 800 au. The
flow is reverse ( _v_ _z_ _<_ 0) around the axis in this range.
Remember that Figure 4 shows two velocity components

9



log n (cm -3 )



t=14978.4 yr





10 7


10 6


10 5



200


100


0
100 200 300 400


z (au)


log T (K)


200


100


0
100 200 300 400



7


6


5


3


2



z (au)


**Figure** **8.** The flow structure in the barrel in model A at
_t_ = 1 _._ 498 _×_ 10 [4] yr. The associated movie shows the fluctuation of the Mach disk. The first barrel is persistent but
fluctuates. The animation shows the sequence from zero to
29455.5 years. The duration of the animation is 12 seconds.


8



10 4 0 500 1000 1500 2000 2500 3000
z (au)


**Figure** **10.** The density distribution on the _z_ -axis in model
A at several epochs.


1000



100







6


4


2


0


-2


-4



0 500 1000 1500 2000 2500 3000
z (au)





**Figure** **9.** The longitudinal velocity ( _u_ _z_ ) at
_t_ = 1 _._ 498 _×_ 10 [4] yr in model A.


along the outflow axis. The blue-shifted may be the offaxis flow along our line of sight while the red-shifted one
may be the flow near the outflow axis.
Figures 10 and 11 show the density and temperature
distributions on the _z_ -axis at several epochs, respectively. The density and temperature decrease steeply
as soon as the gas emerges from the nozzle. Remember
that the jet gas has _n_ 0 = 10 [7] cm _[−]_ [3] and _T_ 0 = 2000 K at
_z_ = 0. Also the pressure decreases steeply near the nozzle. Since the pressure ratio is very high _P_ 0 _/P_ _∞_ = 40,
the jet gas expands rapidly and adiabatically. The flow



0 500 1000 1500 2000 2500 3000
z (au)


**Figure** **11.** The temperature distribution on the _z_ -axis in
model A at several epochs.


is supersonic in the barrel. The density and temperature decrease below 10 [5] cm _[−]_ [3] and 350 K, respectively,
on the upstream side of the Mach disk. They rise again
to 5 _×_ 10 [5] cm _[−]_ [1] and _∼_ 2000 K on the downstream

side of the Mach disk by the shock compression. This
dense hot gas expands again to accelerate the gas ahead.
Figures 10 and 11 show the laminar flow in the barrel
( _z_ _<_ 300 au) is stationary while the flow beyond the
Mach disk is variable. The head of the jet proceeds at
almost constant rate.

We measure the width and height of the barrel from
the velocity profile. The tangential and longitudinal
components of the velocity ( _v_ _r_ and _v_ _z_ ) are discontinuous on the side of the barrel and at the Mach disk,
respectively. We measure the radius where _v_ _r_ turns to
decrease at a given height, _z_ and define it as the local
barrel radius. The barrel diameter ( _D_ _b_ ) is defined as
twice the maximum barrel radius. We define the barrel
height as the place where _v_ _z_ turns to decrease on the

10



400


350


300


250


200


150



0 1×10 4 2×10 4 3×10 4 4×10 4 5×10 4





t (yr)


**Figure** **12.** The time evolution of the barrel width (red)
and height (black) in model A.


axis ( _r_ = 0). Figure 12 shows the width and height
of the barrel in model A. The height is slightly smaller
than expected from Equation (1), 408 au. The height is
_∼_ 20% larger than the width, though both of them are
oscillating substantially. The diameter of the Mach disk
is 210 au at the stage shown in Figure 6.


4.3. _Higher_ _Pressure_ _Ratio_ _Model_


We show model B to examine the effects of a higher
pressure ratio. The initial state of model B is the same
as that of model A except for the pressure ratio (see Table 1), i.e., the density ratio. The initial density of the
injected gas is set to be _n_ 0 = 10 [7] cm _[−]_ [3] for easier comparison with model A. Accordingly, the ambient density
is lower in model B. The temperature ratio remains at
( _T_ 0 _/T_ _∞_ = 20). Figure 13 is the same as Figure 7 but for
the stage at _t_ = 1 _._ 494 _×_ 10 [4] yr in model B. As shown in
the animation associated with Figure 13, models A and
B are qualitatively similar.
Figure 14 is the same as Figure 12 but for model B.
The first barrel of model B has a larger height and width
than that of model A. The aspect ratio, the height over
the width is larger in model B, i.e., the first barrel is
more slender in model B. Both the height and width of
the outflow are larger for a higher pressure ratio. But,
the dependence of the width on the pressure ratio is
weaker than that of the height. Another difference is
the density contrast between the outflow and ambient
gas. The ambient gas is less dense in model B.


4.4. _Cold_ _Ambient_ _Gas_ _Model_


We construct model C in which the ambient gas is set
to be cold ( _T_ _∞_ = 20 K). The pressure ratio is set to
be _P_ 0 _/P_ _∞_ = 40 for comparison with model A. Since the
temperature contract is _T_ 0 _/T_ _∞_ = 100, the ambient gas
is 2.5 times denser than that of the injected gas.



**Figure** **13.** The same as Figure 7 but for model B at
_t_ = 1 _._ 494 _×_ 10 [4] yr. The associated animation shows the
development of the outflow in model B. The outflow is turbulent and associated with shock waves. The first barrel is
persistent. The animation shows the sequence from zero to
20874.4 years. The duration of the animation is 9 seconds.


400





350


300


250


200


150



0 5.0×10 3 1.0×10 4 1.5×10 4 2.0×10 4 2.5×10 4



t (yr)


**Figure** **14.** The same as Figure 12 but for model B.


Figure 15 shows the stage at _t_ = 3 _._ 545 _×_ 10 [4] yr in
model C. Model C is also qualitatively similar to models A and B. The outflow shows the barrel and subsequent semi-periodic structure. However, the outflow is
less prominent since the ambient gas is much denser.
Also the outflow propagates more slowly than in models A and B. The slow propagation is also due to the

**Figure** **15.** The same as Figure 7 but for model C at
_t_ = 3 _._ 545 _×_ 10 [4] yr. The associated animation shows the
development of outflow in model C. The propagation is substantially slower in model C. The animation shows the sequence from zero to 31289.8 years. The duration of the animation is 18 seconds.


dense ambient gas. The larger inertia of the ambient gas
decelerates the outflow propagation substantially. This
density dependence is similar to that found by Smith &
Keogh (2022) though their initial set-up is different.


5. DISCUSSIONS AND SUMMARY


As shown in the previous sections, our simple hydrodynamic model explains several characters of the primary outflow in IRAS 15398 _−_ 3359. First, it explains
the shell structure in the intensity and that in the velocity. Second, it explains the anti-correlation between
the temperature and velocity. It also explains the magnitude of the outflow velocity. Equations (3) and (4)
suggest that the outflow is accelerated to _∼_ 7 km s _[−]_ [1] if
most of the initial thermal energy is converted into the
kinetic energy at _T_ 0 = 2000 K. The inferred value is consistent with the observations since the outflow is inclined
from our line of sight. Fourth, our model shows a backward ( _v_ _z_ _<_ 0) flow in the outflow, which may explain
the red-shifted flow in the blue lobe. Our model demonstrates that we need not invoke short time variability in
the outflow activity to explain the shell structure.
Our model is an oversimplification in some regards.
We assumed that the outflow source maintains constant



11


pressure, density and temperature after a sudden onset.
However, the outflow activity is likely to decay after a
short rise. The pressure ratio may be a little higher in
the early phase of the primary outflow activity. Uniform
density in the source region is also an oversimplification.
Thus, we think that our model has limitations to explain
the primary outflow of IRAS 15398 _−_ 3359.
Nevertheless, our model gives some constraints on a
better model. First, the ambient gas density should
be low enough. The outflow gas is hot ( _T_ _>_ 1000 K)
and should have a high pressure to accelerate the gas
to be highly supersonic. The density of the outflow
gas decreases considerably during the acceleration. If
the initial density of the outflow is comparable or lower
than that of the ambient gas, the outflow is decelerated by the inertia of the ambient gas (see model
C). IRAS 15398 _−_ 3359 experienced at least two earlier outflow activities (Okoda et al. 2021a; Sai et al.
2024). The ambient gas around IRAS 15398 _−_ 3359
can be blown off by the third or even earlier outflow.
Redaelli et al. (2019) estimated the gas density to be
_n_ H 2 = 2 _._ 6 _×_ 10 [4] cm _[−]_ [3] around IRAS 15398 _−_ 3359 from
the radio and far infrared continuum emission observed

with Herschel. They derived the value by approximating
the gas cloud to be a uniform sphere having the effective radius 0.1 pc. Thus, this value should be taken as
an average in the region of 2 _×_ 10 [4] au around IRAS
15398 _−_ 3359. If the gas density around the primary
outflow is similarly low, the outflowing gas will have
a higher density than the ambient gas if the outflowing
gas has the initial density _n_ H 2 _≈_ 10 [7] cm _[−]_ [3] . Second, the
gas temperature should be as high as 2000 K around
the protostar. The outflow gas has a high temperature
( _T_ _>_ 1000 K, Okoda et al. 2025) and substantial velocity. This implies the outflow gas has a higher temperature before acceleration unless it is heated up during
the acceleration. Third, the source of the outflow should
have a radial size of _∼_ 50 au if the first shell located at
300 au from the protostar is due to the Mach disk.
Though JWST observed IRAS 15398 _−_ 3359, the measurement of the gas temperature is limited to a narrow
region around the protostar (see Figure 8 of Okoda et al.
2025), i.e., the field of view of the spectroscopic observation. It is interesting to measure the temperature and
density in the outflow beyond the second shell. Similarly, ALMA observed only a limited portion of the primary outflow with the highest observation (Thieme et al.
2023). It would be interesting to study the kinematics
around shells 3 and 4 with ALMA.

Also interesting is to study outflows showing similar
substructures. Herbig-Haro 211 (hereafter HH 211) is
an example showing a similar substructure in the CO

12


( _J_ = 2 _−_ 1) (Gueth & Guilloteau 1999)) and H 2 (2.1 _µ_ m)
(McCaughrean et al. 1994) emission lines. Figure 1
of Cabrit et al. (2011) shows the correlation between
the substructures. The infrared emission from HH 211

was further studied with Spitzer telescope Tappe et al.
(2012) and JWST (Ray et al. 2023). Ray et al. (2023)
identified that the 4.5 _µ_ m localized emissions are largely
due to the CO fundamental rotational-vibrational transitions. This means that the CO gas is hot ( _∼_ 1000 K)
only in the narrow regions where the 4.5 _µ_ m emission is
strong. Other examples are CALMA 7 and DG Tau B.
Plunkett et al. (2015) discovered semi-regularly placed
knots in the outflow from CARMA 7, a Class 0 source
in the Serpens South star forming region. They found
11 knots each in the red and blue lobes. (de Valon et al.
2020) discovered shell structure in the outflow cavity of
DG Tau B. The shells appear near the protostar in the
widely open conical cavity. We may find other examples
from archival data of ALMA.


ACKNOWLEDGEMENTS


This work is supported by the MEXT/JSPS Grant-inAid from the Ministry of Education, Culture, Sports,
Science, and Technology of Japan (20H00182, 20H05844,
20H05845, 20H05847, and 22K20389). Y.O., Y.-L.Y.,
and N.S. are grateful for support from the RIKEN pioneering project: Evolution of Matter in the Universe.
Y. O. is supported by RIKEN Special Postdoctoral Re


searcher Program (Fellowships) and the Japan Society for the Promotion of Science (JSPS), Overseas Research Fellowship. Japan Society for the Promotion of
Science (JSPS), Overseas Research Fellowship. This
work is based in part on observations made with the
NASA/ESA/CSA James Webb Space Telescope. The
data were obtained from the Mikulski Archive for Space
Telescopes at the Space Telescope Science Institute,
which is operated by the Association of Universities for
Research in Astronomy, Inc., under NASA contract NAS
5-03127 for JWST. These observations are associated

with program #2151. The data were retrieved from the
Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, operated by the Association of
Universities for Research in Astronomy (AURA), Inc.,
under NASA contract NAS 5-03127. The data presented
in this paper were obtained from the Mikulski Archive
for Space Telescopes (MAST) at the Space Telescope
Science Institute. The specific observations analyzed
can be accessed via DOI: [10.17909/wv1n-rf97 and Salyk](https://doi.org/10.17909/wv1n-rf97)
et al. (2024). This paper makes use of the following
ALMA data: ADS/JAO.ALMA#2013.1.00879.S and
ADS/JAO.ALMA#2018.1.01205.L. ALMA is a partnership of the ESO (representing its member states), the
NSF (USA) and NINS (Japan), together with the NRC
(Canada) and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by the ESO, the AUI/NRAO,
and the NAOJ.



Addy, A. L. 1981, AIAA Journal, 19, 121,


doi: [10.2514/3.7751](http://doi.org/10.2514/3.7751)



REFERENCES


Franquet, E., Perrier, V., Gibout, S., & Bruel, P. 2015,


Progress in Aerospace Sciences, 77, 25,



Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023,


JWST Calibration Pipeline, 1.12.5, Zenodo,


doi: [10.5281/zenodo.10022973](http://doi.org/10.5281/zenodo.10022973)


—. 2024, JWST Calibration Pipeline, 1.14.0, Zenodo,


doi: [10.5281/zenodo.10870758](http://doi.org/10.5281/zenodo.10870758)


Cabrit, S., Ferreira, J., & Dougados, C. 2011, in IAU


Symposium, Vol. 275, Jets at All Scales, ed. G. E.


Romero, R. A. Sunyaev, & T. Belloni, 374–382,


doi: [10.1017/S1743921310016431](http://doi.org/10.1017/S1743921310016431)


Codella, C., Ceccarelli, C., Chandler, C., et al. 2021,


Frontiers in Astronomy and Space Sciences, 8, 227,


doi: [10.3389/fspas.2021.782006](http://doi.org/10.3389/fspas.2021.782006)


Crist, S., Glass, D. R., & Sherman, P. M. 1966, AIAA


Journal, 4, 68, doi: [10.2514/3.3386](http://doi.org/10.2514/3.3386)


de Valon, A., Dougados, C., Cabrit, S., et al. 2020, A&A,


634, L12, doi: [10.1051/0004-6361/201936950](http://doi.org/10.1051/0004-6361/201936950)



doi: [10.1016/j.paerosci.2015.06.006](http://doi.org/10.1016/j.paerosci.2015.06.006)


Galli, P. A. B., Bouy, H., Olivares, J., et al. 2020, A&A,


643, A148, doi: [10.1051/0004-6361/202038717](http://doi.org/10.1051/0004-6361/202038717)


Gueth, F., & Guilloteau, S. 1999, A&A, 343, 571


Guzm´an Ccolque, E., Fern´andez L´opez, M., Vazzano,


M. M., et al. 2024, A&A, 686, A143,


doi: [10.1051/0004-6361/202348816](http://doi.org/10.1051/0004-6361/202348816)


Hanawa, T., Garufi, A., Podio, L., Codella, C., &


Segura-Cox, D. 2024, MNRAS, 528, 6581,


doi: [10.1093/mnras/stae338](http://doi.org/10.1093/mnras/stae338)


Hanawa, T., & Matsumoto, Y. 2021, ApJ, 907, 43,


doi: [10.3847/1538-4357/abd2b2](http://doi.org/10.3847/1538-4357/abd2b2)


Hanawa, T., Sakai, N., & Yamamoto, S. 2022, ApJ, 932,


122, doi: [10.3847/1538-4357/ac6e6a](http://doi.org/10.3847/1538-4357/ac6e6a)


Hatanaka, K., & Saito, T. 2012, Shock Waves, 22, 427,


doi: [10.1007/s00193-012-0391-x](http://doi.org/10.1007/s00193-012-0391-x)

Komissarov, S. S., & Falle, S. A. E. G. 1998, MNRAS, 297,

1087, doi: [10.1046/j.1365-8711.1998.01547.x](http://doi.org/10.1046/j.1365-8711.1998.01547.x)

Matsushita, Y., Takahashi, S., Ishii, S., et al. 2021, ApJ,

916, 23, doi: [10.3847/1538-4357/ac069f](http://doi.org/10.3847/1538-4357/ac069f)

McCaughrean, M. J., Rayner, J. T., & Zinnecker, H. 1994,
ApJL, 436, L189, doi: [10.1086/187664](http://doi.org/10.1086/187664)

Norman, M. L., Winkler, K. H. A., Smarr, L., & Smith,

M. D. 1982, A&A, 113, 285

Okoda, Y., Oya, Y., Francis, L., et al. 2021a, ApJ, 910, 11,
doi: [10.3847/1538-4357/abddb1](http://doi.org/10.3847/1538-4357/abddb1)
—. 2021b, ApJ, 910, 11, doi: [10.3847/1538-4357/abddb1](http://doi.org/10.3847/1538-4357/abddb1)
—. 2023, ApJ, 948, 127, doi: [10.3847/1538-4357/acc1e5](http://doi.org/10.3847/1538-4357/acc1e5)

Okoda, Y., Yang, Y.-L., Evans, II, N. J., et al. 2025, ApJ,
982, 149, doi: [10.3847/1538-4357/adb83f](http://doi.org/10.3847/1538-4357/adb83f)

Oya, Y., Sakai, N., Sakai, T., et al. 2014, ApJ, 795, 152,
doi: [10.1088/0004-637X/795/2/152](http://doi.org/10.1088/0004-637X/795/2/152)

Plunkett, A. L., Arce, H. G., Mardones, D., et al. 2015,

Nature, 527, 70, doi: [10.1038/nature15702](http://doi.org/10.1038/nature15702)

Ray, T. P., McCaughrean, M. J., Caratti o Garatti, A.,

et al. 2023, Nature, 622, 48,

doi: [10.1038/s41586-023-06551-1](http://doi.org/10.1038/s41586-023-06551-1)

Redaelli, E., Alves, F. O., Santos, F. P., & Caselli, P. 2019,

A&A, 631, A154, doi: [10.1051/0004-6361/201936271](http://doi.org/10.1051/0004-6361/201936271)

Sai, J., Yen, H.-W., Machida, M. N., et al. 2024, ApJ, 966,

192, doi: [10.3847/1538-4357/ad34b7](http://doi.org/10.3847/1538-4357/ad34b7)

Salyk, C., Yang, Y.-L., Pontoppidan, K. M., et al. 2024,
ApJ, 974, 97, doi: [10.3847/1538-4357/ad62fe](http://doi.org/10.3847/1538-4357/ad62fe)



13


Shang, H., Liu, C.-F., Krasnopolsky, R., & Wang, L.-Y.

2023, ApJ, 944, 230, doi: [10.3847/1538-4357/aca763](http://doi.org/10.3847/1538-4357/aca763)


Smith, M. D., & Keogh, T. L. R. 2022, MNRAS, 516, 2757,

doi: [10.1093/mnras/stac2310](http://doi.org/10.1093/mnras/stac2310)


Smith, M. D., & Richards, C. 2023, MNRAS, 526, 3407,

doi: [10.1093/mnras/stad2879](http://doi.org/10.1093/mnras/stad2879)


Tachihara, K., Dobashi, K., Mizuno, A., Ogawa, H., &

Fukui, Y. 1996, PASJ, 48, 489, doi: [10.1093/pasj/48.3.489](http://doi.org/10.1093/pasj/48.3.489)


Tappe, A., Forbrich, J., Mart´ın, S., Yuan, Y., & Lada, C. J.

2012, ApJ, 751, 9, doi: [10.1088/0004-637X/751/1/9](http://doi.org/10.1088/0004-637X/751/1/9)


Thieme, T. J., Lai, S.-P., Ohashi, N., et al. 2023, ApJ, 958,

60, doi: [10.3847/1538-4357/ad003a](http://doi.org/10.3847/1538-4357/ad003a)


Vazzano, M. M., Fern´andez-L´opez, M., Plunkett, A., et al.

2021, A&A, 648, A41, doi: [10.1051/0004-6361/202039228](http://doi.org/10.1051/0004-6361/202039228)


Yang, Y.-L., Green, J. D., Pontoppidan, K. M., et al. 2022,

ApJL, 941, L13, doi: [10.3847/2041-8213/aca289](http://doi.org/10.3847/2041-8213/aca289)


Yen, H.-W., Koch, P. M., Takakuwa, S., et al. 2017, ApJ,

834, 178, doi: [10.3847/1538-4357/834/2/178](http://doi.org/10.3847/1538-4357/834/2/178)


Yen, H.-W., Takakuwa, S., Ohashi, N., & Ho, P. T. P. 2013,

ApJ, 772, 22, doi: [10.1088/0004-637X/772/1/22](http://doi.org/10.1088/0004-637X/772/1/22)


Young, W. S. 1975, Physics of Fluids, 18, 1421,

doi: [10.1063/1.861039](http://doi.org/10.1063/1.861039)


Yu, J., Vuorinen, V., Kaario, O., Sarjovaara, T., & Larmi,

M. 2013, International Journal of Heat and Fluid Flow,

44, 140, doi: [10.1016/j.ijheatfluidflow.2013.05.015](http://doi.org/10.1016/j.ijheatfluidflow.2013.05.015)


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "H2 temperature and column density distributions from JWST MIRI MRS observations",
  "failed_quote": "Okoda et al. (2025) derived the temperature and column density of H 2 molecules from the JWST MIRI MRS observations, which covers a ∼ 3 ′′ − 5 ′′ region around the protostar"
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "Both blue-shifted and red-shifted velocity components are present in the blue lobe between the protostar and shell 3, indicating diverging/converging flow or reverse flow near the axis.",
  "failed_quote": "They show a red component in addition to a blue component in the interval between the protostar and shell 3."
 }
]
```
