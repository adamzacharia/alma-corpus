# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...685A..11K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. RDor_ALMA_only_noSPHERE_accepted ©ESO 2024
February 22, 2024

## **An empirical view of the extended atmosphere and inner envelope** **of the AGB star R Doradus**

### **I. Physical model based on CO lines**


T. Khouri [1][⋆], H. Olofsson [1], W. H. T. Vlemmings [1], T. Schirmer [1], D. Tafoya [1], M. Maercker [1], E. De Beck [1],
L.-Å Nyman [1][,][ 2], M. Saberi [3]


1 Dep. of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, 43992 Onsala, Sweden
2 European Southern Observatory (ESO), Alonso de Córdova 3107, Vitacura 763-0355, Santiago, Chile
3 Rosseland Centre for Solar Physics, University of Oslo, PO Box 1029 Blindern, 0315 Oslo, Norway


February 22, 2024


**ABSTRACT**


_Context._ The mass loss experienced on the asymptotic giant branch (AGB) at the end of the lives of low- and intermediate-mass stars is
widely accepted to rely on radiation pressure acting on newly formed dust grains. Dust formation happens in the extended atmospheres
of these stars, where the density, velocity and temperature distributions are strongly affected by convection, stellar pulsation, and
heating and cooling processes. The interaction between these processes and how that affects dust formation and growth is complex.
Hence, characterising the extended atmospheres empirically is paramount to advance our understanding of the dust-formation and
wind-driving processes.
_Aims._ We aim to determine the density, temperature, and velocity distributions of the gas in the extended atmosphere of the AGB star
R Dor.
_Methods._ We acquired observations using ALMA towards R Dor to study the gas through molecular line absorption and emission.
We use the [12] CO _v_ = 0, _J_ = 2 − 1, _v_ = 1, _J_ = 2 − 1 and 3 − 2 and [13] CO _v_ = 0, _J_ = 3 − 2 lines. We modelled the observations using
the 3D radiative transfer code LIME to determine the density, temperature and velocity distributions up to a distance of ∼ 4 times the
radius of the star at sub-mm wavelengths.
_Results._ The high angular resolution of the sub-mm maps allows for even the stellar photosphere to be spatially resolved. By analysing
the absorption against the star, we infer that the innermost layer in the near-side hemisphere is mostly falling towards the star, while
gas in the layer above that seems to be mostly outflowing. Interestingly, the high angular resolution of the ALMA Band 7 observations
reveal that the velocity field of the gas seen against the star is not homogenous across the stellar disc. The gas temperature and density
distributions have to be very steep close to the star to fit the observed emission and absorption, but become shallower for radii larger
than ∼ 1.6 times the stellar sub-mm radius. While the gas mass in the innermost region is hundreds of times larger than the mass
lost on average by R Dor per pulsation cycle, the gas densities just above this region are consistent with those expected based on the
mass-loss rate and expansion velocity of the large-scale outflow. Our fits to the line profiles require the velocity distribution on the
far side of the envelope to be on average mirrored with respect to that on the near side. Using a sharp absorption feature seen in the
CO _v_ = 0, _J_ = 2 − 1 line, we constrain the standard deviation of the stochastic velocity distribution in the large-scale outflow to be
≲ 0.4 km/s. We characterise two blobs detected in the CO _v_ = 0, _J_ = 2 − 1 line and find densities substantially larger than those of the
surrounding gas. The two blobs also display expansion velocities which are high relative to that of the large-scale outflow. Monitoring
the evolution of these blobs will lead to a better understanding of the role of these structures in the mass-loss process of R Dor.


**Key** **words.** stars: individual: R Doradus – star: winds, outflows – stars: circumstellar matter – stars: AGB and post-AGB – stars:
imaging – stars: mass-loss



**1.** **Introduction**


At the end of their lives, low- and intermediate-mass stars reach
the asymptotic giant branch (AGB) when an inert core rich
in carbon and oxygen has developed at the stellar centre and
nuclear burning of helium and hydrogen has shifted to layers
around the core (Herwig 2005). In response to the restructuring
of the innermost regions, the stellar envelope becomes convective and expands to hundreds of times larger than the stellar size
in the main sequence. Pulsations also develop in this convective
envelope and, together with the action of convective cells, create


⋆ _Send o_ ff _print requests to T. Khouri_
e-mail: `theo.khouri@chalmers.se`



a dense, extended atmosphere. As stars evolve along the AGB
and become cooler, the temperature in the extended atmosphere
becomes low enough for dust condensation and growth to be efficient. The dust interacts strongly with the radiation field and
experiences radiation pressure. A large-scale outflow is triggered
once enough dust has formed for the radiation pressure force on a
mass element to exceed the stellar gravitational pull (e.g. Höfner
& Olofsson 2018).


Despite the well-established qualitative picture and the substantial progress made in the past two decades in understanding the dust-formation and wind-driving mechanism, the complexity of the dust-formation process in the shock-impacted and
non-uniform extended atmospheres still prevents the AGB mass

Article number, page 1 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



loss history of a star with given initial properties to be derived from first principles. It is therefore paramount to investigate the properties of the gas and dust in the dust-formation
and wind-acceleration zones. The picture is particularly complex
for oxygen-rich AGB stars because oxygen-rich dust that is expected to survive close to AGB stars has insufficient absorption
cross-section per unit mass to drive the outflows (Woitke 2006).
The current paradigm is that the nucleation of oxides starts the
dust-formation process, although the exact composition of these
first condensates is still debated (Plane 2013; Gail et al. 2016;
Gobrecht et al. 2022, 2023). The condensation of iron-free silicates is thought to be necessary for the outflows to develop, with
the grains needing to reach sizes ≳ 0.1 µm in order to provide the
required opacity via scattering of photons (Höfner 2008; Höfner
et al. 2016). Theoretical models have advanced substantially and
are now able to calculate dust growth in extended atmospheres
produced in three-dimensional simulations that take into account
convection in the envelopes (Freytag & Höfner 2023).
The advent of high-angular resolution instruments has revolutionised our empirical understanding of the region where dust
forms and is accelerated around AGB stars. Scattered-light observations have revealed that grains in the expected size range do
exist around oxygen-rich AGB stars (Norris et al. 2012; Khouri
et al. 2016a, 2020; Ohnaka et al. 2016, 2017; Adam & Ohnaka
2019). Observations of the molecular gas at high-angular resolution and sensitivity have also allowed the gas density, temperature and velocity distribution around the closest AGB stars to
be studied in unprecedented detail (Wong et al. 2016; Khouri
et al. 2016b, 2018; Vlemmings et al. 2017; Ohnaka et al. 2019).
Studies aiming to constrain the composition of the dust by determining gas-phase abundance of dust-forming elements have
also provided important clues to the composition of the first dust
grains to form in oxygen-rich environments (Khouri et al. 2014,
2018; Kami´nski et al. 2016; Decin et al. 2017; De Beck et al.
2017; Danilovich et al. 2020; Gottlieb et al. 2022), but an empirical overview of the dust formation sequence for AGB stars has
yet to be achieved. Despite the advancements, the physical parameters obtained from observations of the dust and gas have not
yet reached the level of providing direct testing of the feasibility
of the accepted wind-driving mechanism for specific sources.
To empirically constrain the properties of the gas in the innermost layers of AGB envelopes, we study the AGB star R Doradus using the Atacama large sub-millimetre array (ALMA).
The high angular resolution provided by ALMA allow us to
probe the crucial region where dust formation and growth take
place.
This paper is structured in the following way. In Sections 2
and 3 we summarise the properties of R Dor and present the
observations employed in our study, respectively. In Section 4
we discuss empirical results that do not rely on radiative transfer modelling. Then, we perform radiative transfer calculations
to improve the interpretation of the observations and obtain a
quantitative description of the density, temperature and velocity
distribution of the gas in the inner circumstellar environment of
R Dor. The approach for calculating radiative transfer models
and the results we obtain are the subjects of Sections 5 and 6,
respectively. In Sections 7 and 8, we discuss the results and give
a summary of the paper, respectively.


**2.** **R Dor**


R Dor is a semi-regular variable which exhibits two modes of
pulsation, with periods of 362 and 175 days. The star switches
between the two modes on a time-scale of roughly 1000 days


Article number, page 2 of 28



(Bedding et al. 1998). Its initial mass has been estimated to be
between 1.0 and 1.3 M ⊙ (Danilovich et al. 2017) and 1.3 and
1.6 M ⊙ (De Beck & Olofsson 2018). In this work, we adopt an
initial mass of 1.3 M ⊙ . The distance determined from the _Hip-_
_parcos_ parallax (62 ± 3 pc, Perryman & ESA 1997) is in good
agreement with the distance derived by reanalysing the _Hippar-_
_cos_ measurements, 59 pc (Knapp et al. 2003). However, a more
recent estimate suggests a smaller distance of 44 pc (Andriantsaralaza et al. 2022). To be consistent with previous derivations of the mass-loss rate, we adopt a distance of 59 pc in this
study.
According to observations and models of the large-scale CO
emission (Ramstedt et al. 2014; Van de Sande et al. 2018; De
Beck & Olofsson 2018), R Dor is a standard semi-regular variable star with a relatively low mass-loss rate (∼ 10 [−][7] M ⊙ /yr)
and wind expansion velocity (∼ 5.5 km/s). However, when studied in more detail, many of its characteristics are puzzling. For
instance, the star and the inner circumstellar envelope seem to
be rotating hundreds of times faster than expected for an AGB
star (Vlemmings et al. 2018), the presence of a disc has been
suggested (Homan et al. 2018) and has later been disfavoured
(Nhung et al. 2021), and a gas blob has been detected at tens of
AU from the central star moving with a projected radial velocity
at least a few times larger than the maximum expansion velocity
of the outflow (Vlemmings et al. 2018; Decin et al. 2018; Nhung
et al. 2021). It is not clear, however, whether R Dor is atypical
in these characteristics or whether these are common features of

similar sources.
Decin et al. (2018) conducted a spectral scan towards R Dor
using ALMA to reach an angular resolution of ∼ 150 mas. Their
observations allowed them to investigate the dynamics of the
circumstellar envelope, revealing relatively weak high-velocity
wings in several lines. The authors offered two possibilities for
these high-velocity outflow components: a fraction of the wind
not following the smooth radial outflow, or a more forceful acceleration of the outflow globally.
Based on observations of polarised dust-scattered light, Norris et al. (2012) concluded that grains with sizes ∼ 0.3 µm were
responsible for the scattering signal reported by them, while
Khouri et al. (2016a) derived the radial profile of the dust density distribution and concluded that the inferred gas-to-dust ratio
at 5 R ⋆, ≳ 5000, is marginally consistent with the most extreme
values found in wind-driving models, of ∼ 4000 (Bladh et al.
2019).
Using the same Band 7 data employed in this paper, Vlemmings et al. (2019) studied the stellar continuum at ∼ 338 GHz
(∼ 887 µm). They report a size of ∼ 62.2 mas and a brightness
temperature at this frequency of ∼ 2370 K between 330.15 and
344.17 GHz. We use the stellar radius measured at 887 µm,
_R_ [⋆] 887 µ _m_ [=] [1][.][835] [AU][=] [2][.][7] [×] [10] [10] [m,] [as] [a] [reference] [size] [in]
our calculations. At an earlier epoch (45 days before), the stellar disc was measured to vary from 65.3 to 62.1 mas in diameter at frequencies between 129.35 and 229.16 GHz. The authors were able to reproduce the observed variation in size as a
function of wavelength using power-law profiles for the density,
temperature and ionisation. The H 2 density profile obtained is
_n_ H 2 = 4 × 10 [12] ( _r_ / _r_ ◦ ) [−][6] cm [−][3], where _r_ ◦ = 27.5 mas.


**3.** **Observations**


R Dor was observed using ALMA in Band 6 (project ID
2017.1.00824.S, PI Decin) on October 24 and in Band 7 (project
ID 2017.1.00191.S, PI Khouri) on November 9, 2017. The frequency range spanned by these observations covers three [12] CO

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||



180


120


60


0


60


120


180



T. Khouri et al.: R Dor seen by ALMA


Integrated Intensity [mJy GHz/beam] Integrated Intensity [mJy GHz/beam] Integrated Intensity [mJy GHz/beam] Integrated Intensity [mJy GHz/beam]

0 1 2 3 4 5 6 7 0 1 2 3 4 5 0.0 0.2 0.4 0.6 0.8 1.0 0.0 0.4 0.8 1.2 1.6


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||
|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|CO v=0, J=2-1|13CO v=0, J=3-2|13CO v=0, J=3-2|13CO v=0, J=3-2|13CO v=0, J=3-2|13CO v=0, J=3-2|13CO v=0, J=3-2|CO v=1, J=2-1|CO v=1, J=3-2|



18 ~~0~~ 120 60 0 60 120 180



18 ~~0~~ 120 60 0 60 120 180 18 ~~0~~ 120 60 0 60 120 180 18 ~~0~~ 120 60 0 60 120 180



D [miliarcsec]


**Fig. 1.** Continuum-subtracted emission in the four spectral lines considered in our analysis integrated over frequency in mJy×GHz/beam (momentzero map). From left to right, the lines are CO _v_ = 0, _J_ = 2 − 1, [13] CO _v_ = 0, _J_ = 3 − 2, CO _v_ = 1, _J_ = 2 − 1, and 3 − 2. The half-power sizes of the
ALMA gaussian beams are indicated at the bottom left corner of each panel.



(hereafter referred to as only CO) rotational transitions _v_ =
0, _J_ = 2 − 1 and _v_ = 1, _J_ = 2 − 1 and 3 − 2, and one [13] CO
rotational transition _v_ = 0, _J_ = 3 − 2, which we use to study
the physical properties of the gas close to R Dor. We recovered the cubes comprising the lines mentioned above from the
products associated with the projects in the ALMA archive. The
CO _v_ = 1, _J_ = 3 − 2 and the [13] CO _v_ = 0, _J_ = 3 − 2 lines
were imaged using CASA 5.7 and the calibrated measurement
sets provided by ESO. The CO _v_ = 0 and _v_ = 1 _J_ = 2 − 1 line
cubes were obtained from the ALMA archive. The synthesised
beams are ∼ 28 mas and ∼ 20 mas for the observations in bands
6 and 7, respectively. The ALMA observations spatially resolve
even the stellar disc of R Dor at the two frequencies.


The ALMA observations are not sensitive to emission

smooth on scales of ≳ 0 [′′] . 6 and ≳ 0 [′′] . 42 for the observations in
Bands 6 and 7, which corresponds to regions of radius ∼ 10 and
∼ 7 _R_ [⋆]
887 µm [, respectively. However, the configuration of the array]
at the time of the Band 6 observations included some short baselines, which implies that those observations can be somewhat
sensitive to emission even on larger scales than the largest recoverable scale calculated by the ALMA observatory. The emission
region of the vibrationally excited lines is expected to be more
compact than that, and, hence, the observations of these lines
should not be affected by large-scale emission being filtered out
by the interferometer. This expectation is confirmed by the models we discuss below. The lines in the ground vibrational state,
however, have emission regions which are much larger than the
scales probed by ALMA in the configurations employed in the
observations considered here. Hence, a very large amount of
flux is expected not to be recovered. Nonetheless, the surface
brightness of the line emission decreases steeply away from the
star mainly because of the gas density profile, and the effect of
resolved-out flux on the brightness distribution in the inner regions of the envelope is not necessarily strong. Throughout the
paper, we estimate the effect of resolved-out flux by simulating
observations of the calculated models using the relevant array
configurations when comparing models to observations as described in Section 5.1. As discussed in Section 5.1, we also use
observations obtained with the Atacama Compact Array (ACA)
in the context of project ID 2017.1.00595.S (PI Ramstedt) to
constrain the large-scale emission of the low-excitation lines.
The maximum recoverable scale of the maps obtained with the



ACA is approximately 31 [′′] . 5. The beam has major and minor axis
of 6 [′′] . 9 and 5 [′′] . 0, respectively, and a position angle of 78 degrees.


**4.** **Observational results**


_4.1._ _Line emission_


The brightness distribution in the continuum-subtracted CO lines
integrated in frequency shows a bright, thin ring surrounded by
weaker, more extended emission (Fig. 1). The bright ring is the
only morphological component observed in the vibrationally excited lines and is significantly brighter than the more extended
emission in the _v_ = 0 lines. The brightness of the ring is fairly
symmetric around the star, with ratios between the brightest and
the dimmest regions of ∼ 1.5 for the CO _v_ = 0, _J_ = 2 − 1 and
∼ 2.5 for the CO _v_ = 1, _J_ = 2 − 1 and 3 − 2 lines. For the
13
CO line, the ratio is ∼ 2.3. Most of the emission is significantly
closer to the average than the extremes.


The brightness distributions of the ring are somewhat different between the images obtained at the two epochs, but
roughly consistent among the lines obtained in a given epoch.
The CO _v_ = 0, _J_ = 2 − 1 and _v_ = 1, _J_ = 2 − 1 lines observed
in Band 6 show a bright region to the southeast and a weaker
second peak to the northwest (more clearly seen in the _v_ = 1
line). The [13] CO _v_ = 0, _J_ = 3 − 2 and CO _v_ = 1, _J_ = 3 − 2 lines
observed in Band 7 reveal peaks of emission towards the west
and east, with a third peak towards the south more clearly seen
in the _v_ = 1 line. The more extended emission component is very
clearly seen up to about 5 R [⋆] 887 µm [in] [the] [CO] _[v]_ [=] [0][,] _[ J]_ [=] [2][ −] [1]
line, with a more extended bright region towards the northwest.
At 4 R [⋆]
887 µm [, the ratio between emission to the northwest and in]
other directions at the same radius varies between roughly 1.5
and 2.5. The brightness distribution of the lines is affected by
the beam shape and by the signal to noise of the obtained images
and, hence, a physical interpretation of the observed differences
can be best obtained based on models which take into account
the specific different array configurations.


Observed spectra obtained in apertures of different sizes are
shown in Fig. 2. It is clear that in addition to line emission there
is prominent line absorption.


Article number, page 3 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


**Fig. 2.** Extracted CO spectra. The panels show extracted CO spectra (blue histograms) and the best-fit model presented in Section 6. The model
was shifted using a systemic velocity of 7.4 km/s. From left to right, we present spectra extracted from apertures with diameters of 45, 90, 135,
180, and 240 mas. From top to bottom, the lines shown are CO _v_ = 1, _J_ = 3−2, CO _v_ = 0, _J_ = 2−1, CO _v_ = 1, _J_ = 2−1, and [13] CO _v_ = 0, _J_ = 3−2.



_4.2._ _Line absorption_


The absorption produced by the cooler circumstellar gas against
the stellar continuum is more conspicuous in spectra extracted
using apertures smaller than or comparable to the stellar radius.
As the size of the aperture from which the spectrum is extracted
is increased, emission from gas in lines of sight that do not intercept the star progressively fills up the absorption and eventually
hides most of it (Fig. 2).
The dominant effect is from absorption by the high-density
gas close to the star, even for low-excitation lines. Nonetheless,
molecules in the outer, low-density regions of the envelope contribute to the absorption profile, as can be seen from the very
sharp absorption feature at 1.9 km/s in the CO _v_ = 0, _J_ = 2 − 1
line (Fig. 3). This narrow feature arises from the envelope outflowing at the terminal velocity. Even in this case, absorption
from the extended atmosphere clearly dominates the profile.
Both the absorption towards the star and the emission from
the surrounding gas produce line profiles which are ∼ 30 km/s
broad (Fig. 2), expected to be caused by the outflow and infall of
gas in the extended atmosphere which is stirred up by convection
and stellar pulsations. Such gas motions have been known to display velocities of this order from unresolved observations of rovibrational transitions for many decades (e.g. Hinkle 1978; Hinkle et al. 1982). Interestingly, most of the absorption observed
in the CO _v_ = 1, _J_ = 3 − 2 line is shifted to the red (gas falling
back to the star), while absorption in the CO _v_ = 0, _J_ = 2 − 1
and [13] CO _v_ = 0, _J_ = 3 − 2 lines is more centred around the
systemic velocity (Fig. 2). We interpret this as an indication that
the absorbing gas is on average falling back to the star in the
higher-density regions immediately above the stellar millimetre
photosphere where the _v_ = 1 levels are excited.
The Band 7 observations also reveal that the spatial distribution of the absorption is not uniform against the stellar disc


Article number, page 4 of 28



(Fig. 4). In these data, more absorption is seen against the eastern hemisphere (where the 887 µm continuum emission peaks)
than towards the western one.


The absorption features of the CO _v_ = 1, _J_ = 3 − 2 and
13 CO _v_ = 0, _J_ = 3 − 2 lines vary not only in strength between
the two hemispheres but also regarding the velocity field of the
absorbing gas (Fig. 4). Towards the east, each line shows a component slightly red-shifted on average with respect to the star
that is also seen towards the west albeit about a factor of two
weaker. This component must be produced by gas falling back
to the star or moving away from it at, at most, a few km/s, and
it shows more red-shifted velocities in the _v_ = 1 line. For the
CO _v_ = 1, _J_ = 3 − 2 line, a blue-shifted component seen towards the east has no counterpart above the noise level in the
spectra extracted from the west. By scaling the eastern absorption component of the CO _v_ = 1, _J_ = 3 − 2 line to the same level
as the western one, it becomes evident that the velocity distribution of the absorbing gas is indeed different. This blue-shifted
absorption is produced by gas moving away from the star with
speeds of up to ∼ 15 km/s. Although this difference might also
be present in the [13] CO _v_ = 0, _J_ = 3 − 2 line, the noise level and
the relatively bluer absorption make it less conspicuous.


In the CO _v_ = 0, _J_ = 3 − 2 line, we identify a weak absorption feature at υ ∼ 18 km s [−][1] which can be most easily seen
in the spectra from smaller aperture in Fig. 2. To be produced
by CO molecules, the absorbing gas would have to be moving at
velocities of ∼ 25 km s [−][1] with respect to the systemic velocity. It
is unclear from the data at hand whether this is indeed a feature
produced by CO molecules, or by an unidentified molecule. The
detection of this absorption in other CO lines would be necessary to confirm that this is a dynamical component of the outflow
and derive the properties of the absorbing gas. Hence, we refrain
from analysing this feature.

T. Khouri et al.: R Dor seen by ALMA


0.0 0.2 0.4 0.6 0.8 1.0



|0.00|Col2|Spectrum 45 mas|Col4|Col5|
|---|---|---|---|---|
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||
|0.06<br>0.05<br>0.04<br>0.03<br>0.02<br>0.01<br>Intensity [Jy/beam]|||||


0.07
5.0 2.5 0.0 2.5 5.0 7.5 10.0


Velocity [km/s]


**Fig.** **3.** Spectrum of the CO _v_ = 0, _J_ = 2 − 1 line extracted from an
aperture with a diameter of 45 mas towards the star (blue histogram).
Two fits to the sharp absorption feature produced by the large-scale outflow are shown by the yellow and green lines. The dashed lines along
the fit show our assumption for the underlying atmospheric absorption
line on top of which the sharp feature is added. The vertical dashed line
indicates the systemic velocity (∼ 7.4 km/s) inferred from the adopted
expansion velocity of 5.5 km/s.


4.2.1. Absorption from the large-scale envelope


The narrow line profile produced by the large-scale outflow can
be used to constrain the stochastic and thermal Doppler broadening in the outer envelope. In order to do this, absorption in
the inner regions of the envelope has to be disentangled from
that produced in the large-scale outflow. Given the unknown
contribution from different components to the absorption profile shown in Fig. 3, an assumption on the depth of the absorption feature produced in the large-scale outflow has to be made.
Absorption by gas in the extended atmosphere dominates over
most of the velocity range covered by the line profile, while gas
in the wind-acceleration region might contribute significantly to
the profile at velocities between the systemic velocity and the
velocity of the sharp absorption feature (∼ 1.9 km/s).
We consider two extreme scenarios to isolate the absorption
in the outer envelope: i) the absorption feature of the outer wind
corresponds to only the line that can be clearly discerned in the
absorption profile (green line in Fig. 3), or ii) it extends deep into
the profile (yellow line in Fig. 3). Our second scenario implies
that absorption between the yellow and blue lines at velocities
2.5 ≲ υ LSR ≲ 5.5 is produced in the wind-acceleration region.
The spectra without the absorption feature from the large-scale
outflow were created by interpolating the profile in the region of
the feature, as shown by the dashed lines in Fig. 3.
In order to retrieve the broadness of the absorption profile
in the large-scale envelope, we fitted a gaussian function to the
spectra created as described above. The best fits were obtained
using the curve_fit function of the optimize module in the SciPy
(Virtanen et al. 2020) package. In this way, we obtain an upper



Velocity [km/s] Velocity [km/s]


**Fig. 4.** Upper panels: Normalised stellar continuum emission observed
by ALMA in Band 7 (color maps) compared to the emission (red contours) and absorption (blue dashed contours) in the CO _v_ = 1, _J_ = 3 − 2
(left panels) and [13] CO _v_ = 0, _J_ = 3 − 2 (right panels) lines. The positive (red) contours are drawn at 1, 2, 3, 4, and 5 mJy × GHz/beam for
both lines. The negative (blue) contours are drawn at -2.5, -1.5, and 0.5 mJy × GHz/beam for the CO _v_ = 1, _J_ = 3 − 2 line and at -3.6,
-2, and -0.4 mJy × GHz/beam for the [13] CO _v_ = 0, _J_ = 3 − 2 line. The
root-mean-square noise is 0.4 mJy × GHz/beam in both images. Lower
panels: Spectra extracted towards the absorption peak to the east of the
star (yellow histogram) compared to that observed to the west (green
histogram) and to the emission from an aperture with diameter 150 mas
(blue histogram). The absorption profile to the east is also shown scaled
by a factor of 0.5 in comparison (brown histogram). The systemic velocity determined from the fit to the absorption line obtained in Section 4.2.1 (7.4 km/s) is shown by the vertical dahsed lines.


limit to the stochastic velocity in the outflow. We find standard
deviations for the gaussian functions of 0.43 and 0.32 km/s for
scenarios i) and ii), respectively. The uncertainties on the derived values are at most at the 2% level. Hence, both scenarios
imply a standard deviation of at most ∼ 0.4 km/s. This value is
the combination of broadening from thermal and stochastic motion of the gas particles. The thermal broadening at the expected
temperatures in the outer outflow (≲ 100 K) is not necessarily
negligible (≲ 0.2 km/s) and the stochastic broadening might be
significantly smaller than 0.4 km/s. The central velocity of the
fitted profile implies a systemic velocity of 7.4 km/s given the
expansion velocity of 5.5 km/s reported in the literature.


**5.** **Modelling strategy**


To constrain the properties and distribution of the gas, we calculated models to reproduce the observed spectral cubes using
the 3D molecular excitation and radiative transfer code LIME
(Brinch & Hogerheijde 2010). We constrain the temperature,
density and velocity distributions in the models by comparing
the observed CO _v_ = 0, _J_ = 2 − 1 and _v_ = 1, _J_ = 2 − 1 and


Article number, page 5 of 28



50


25


0


25


50



50 0 50



50 0 50



D [miliarcsec]

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



3 − 2, and [13] CO _v_ = 0, _J_ = 3 − 2 lines to the calculated ones.
The model structure was constrained using the CO lines and the
13 CO line was fit by only varying the 13 CO abundance. We initially consider spherically symmetric models to avoid introducing a larger number of free parameters as in a more complex
model. The motivation for this approach is the fairly symmetric
brightness distributions of the modelled lines, with variations in
line intensity not much larger than a factor of two for the molecular lines we consider. The only non-spherically symmetric feature we included in our models from the start is the rotation of
the star and the inner circumstellar envelope reported by Vlemmings et al. (2018). This is implemented as a 2 km/s rotation
about the south-north axis.

The excitation of CO was calculated in non-local-thermodynamical (non-LTE) conditions by considering radiative and
collisional excitation in rotational levels up to _J_ = 40 in the
ground, first and second vibrational states. The collisional rates
employed are those provided by Castro et al. (2017). The lines
predicted under non-LTE and LTE are essentially equal for the
transitions in the ground vibrational state, while the vibrationally
excited lines differ. This is caused by high gas densities in these
inner regions of the circumstellar envelope and the relatively
lower values of the spontaneous decay rates for the rotational
transitions compared to the ro-vibrational ones. Hence, we consider LTE for calculating the excitation of [13] CO and non-LTE
for calculating the excitation of CO, for which vibrationally excited lines are also observed. Including also the _v_ = 2 state in our
calculations affects the populations of the _v_ = 1 levels in comparison to only including the _v_ = 0 and _v_ = 1 levels. Hence, we
use the three vibrational states. We adopt an abundance of CO
relative to H 2 by number equal to 4 × 10 [−][4] throughout the paper.


_5.1._ _Missing flux_


It is essential in our modelling to take into account the effects of
observing an extended source with an interferometer. Hence, we
simulated how the the two lines with a large emission region,
CO _v_ = 0, _J_ = 2 − 1 and [13] CO _v_ = 0, _J_ = 3 − 2, would be seen
by ALMA. We use CASA version 5.7.2 and the simalma task to
create the synthetic visibilities for the appropriate array configurations. These synthetic visibilities were imaged using the task
tclean to produce the synthetic cubes. In this way, our modelling
procedure accounts for the flux missed by each of the array configurations considered.
The largest effect of resolved-out flux on the surface brightness of small-scale structures will come from smooth, extended
components with surface brightnesses that are not insignificant
compared to those of the small-scale components. The decrease
in gas densities as we move away from the star implies that
the surface brightness will decrease with radius, even for lowexcitation CO and [13] CO lines. Therefore, it is important that our
models reproduce the observations on scales comparable to and
somewhat larger than the maximum recoverable scale.
The highest-resolution images of the CO _v_ = 0, _J_ = 2 − 1
line towards R Dor that can be used for this purpose, and are
available in the ALMA archive, were acquired with the Atacama
Compact Array (ACA) and the total-power telescopes on Jan 1,
2018 (project ID 2017.1.00595.S). These ACA data were obtained about two months later than the main array observations
we focus on. The flux density recovered from the central beam
(with size 6 [′′] . 9 and 5 [′′] . 0) peaks between 10 and 17 Jy for different velocities, which is two orders of magnitude larger than the
flux density we measure from the largest region considered by
us (0 [′′] . 24) of 0.15 Jy. This implies that emission from the inner


Article number, page 6 of 28



region we focus on does not affect significantly the flux density within the central ACA beam. This allows us to construct a
model to reproduce the large-scale emission which is mostly independent from the model for the innermost region. This largescale model can, then, be used to estimate the resolved-out flux
in the high-resolution observations.


_5.2._ _Physical structure of the model_


The steep decline in brightness of the CO lines (see Fig. 1) in
the innermost regions requires models with steep density profiles. We identify two main components in the observed maps.
The first is a narrow shell around the star, seen as a ring in the
images, which accounts for emission in the vibrationally excited
lines and corresponds to the brightest region in the maps of the
_v_ = 0 lines. The second is only clearly visible in the maps of the
CO _v_ = 0, _J_ = 2 − 1 line and corresponds to weaker emission
surrounding this inner shell. Based on this, we included three
distinct radial zones in our models. An inner one that corresponds to the inner thin shell, an intermediate one that corresponds to the larger shell, and an outer one that corresponds to
the large-scale wind. The main constraints to the parameters of
density profile in all regions was the brightness distribution of
the CO _v_ = 0, _J_ = 2 − 1 line and the fact that the _v_ = 1 lines are
only observed in a thin ring around the star.
The velocity of the gas where the different lines are produced
can be constrained using their absorption profiles observed towards the star (see Fig. 2). Since the _v_ = 1 lines show only redshifted absorption, the velocity of the inner region was set to, on
average, a slight infall towards the star. The absorption produced
by this inner layer is also clearly visible in the CO _v_ = 0, _J_ = 2−1
and [13] CO _v_ = 0, _J_ = 3 − 2 lines. To fit the observed profile of the
_v_ = 0 lines, the velocity of the intermediate layer was set to, on
average, an outflow away from the star. This is motivated by the
blue-shifted absorption which is visible in the CO _v_ = 0, _J_ = 2−1
line but absent in the _v_ = 1 lines.
We consider a stochastic velocity in the inner and intermediate regions of 4 km/s. This is to account both for stochastic
(small-scale velocity field) and variations of gas velocity on large
scales, which cannot be taken into account in a different way in a
spherically symmetric model. The temperature profile was kept
continuous between the three layers, while discontinuities were
allowed in the velocity and density profiles. Within each of the
three layers, the gas temperature _T_ ( _r_ ), density _n_ ( _r_ ), and radial
velocity υ( _r_ ) as a function of radius, _r_, were approximated by
the following analytical expressions



_T_ ( _r_ ) = _T_ ◦


_n_ ( _r_ ) = _n_ ◦



−ϵ

_r_

, (1)

� _R_ in �



−η

_r_

, and (2)

� _R_ in �



υ( _r_ ) = υ ◦ + (υ f − υ ◦ ) × _r_ − _R_ in
� _R_ out − _R_ in



1.0

, (3)
�



where _T_ ◦, _n_ ◦, and υ ◦ are the gas kinetic temperature, particle
density, and radial velocity at the inner boundary of the given
layer, _R_ in, and υ f is the radial velocity at the outer boundary of
the layer, _R_ out . An overview of the free parameters of the model
is given in Table 1.

T. Khouri et al.: R Dor seen by ALMA


**Table 1.** Parameters considered in the models and summary of main constraints and assumptions. Positive values of the exponents of the temperature and density profiles, ϵ and η, respectively, imply temperature and density decreasing with radius. The velocities between parentheses indicate
the modified velocity field in the far-side hemisphere of the envelope.


Params. Inner Intermediate Outer
Assumptions Best Assumptions Best Assumptions Best
_R_ in _R_ ~~[⋆]~~ 887µm _R_ ~~[⋆]~~ 887µm None 1.6 × _R_ ~~[⋆]~~ 887µm None 5.0 × _R_ ~~[⋆]~~ 887µm
_T_ ◦ _T_ [⋆] _T_ [⋆] _T_ at _R_ [Inner] out 940 K _T_ at _R_ [Interm] out [.] 400 K
_n_ ◦ None 3.5 × 10 [11] cm [−][3] < _n_ [Inner] ◦ 1 × 10 [9] cm [−][3] < _n_ [Interm] ◦ [.] 4 × 10 [7] cm [−][3]
υ ◦ Infall ( _v_ = 1) -6.0 km/s (10.0) Outflow ( _v_ = 0) 13.0 km/s (-6.0) 2.0 km/s 2.0 km/s
υ f None 0.0 km/s (13.0) None 2.0 km/s (-2.0) 5.5 km/s from 10 _R_ [⋆] 887µm
ϵ  - 0 2.0  - 0 0.73  - 0 0.6
η  - 0 7.0  - 0 2.8 Linear acceleration up to 10 _R_ [⋆] 887µm



In our model for the outermost region, the gas density and
radial velocity match those expected from extrapolating inwards
the mass-loss rate (∼ 10 [−][7] M ⊙ yr [−][1] ) and expansion velocity
(∼ 5.5 km/s) derived from models for the large-scale envelope
(Van de Sande et al. 2018). The temperature profile was initially
assumed to be that given by (Van de Sande et al. 2018) but was
modified to make it consistent with the results from the inner region, as described below. We assume an expansion velocity of
2.0 km/s at the inner radius of the outermost region of the model
( _R_ [Outer] in ) and a linear acceleration profile that reaches the maximum expansion velocity at 10 _R_ [⋆] 887µm [.] [We] [varied] [the] [exponent]
of the temperature profile in the outflow, ϵ Outer, to fit the emission in the CO _J_ = 2 − 1 line in the central beam of the ACA

observations.


_5.3._ _Modelling approach_


Our approach can be summarised as:


**–** We obtain a spherically symmetric model that fits the large
scales probed by the ACA observations. When comparing
the large-scale model and the observations, we convolved
the model with the ACA beam. This model is presented in
Section 6.1.

**–** We modify the density, temperature and velocity distributions in the inner five stellar radii (0 [′′] . 155 in radius) to reproduce the higher-resolution observations. As shown in Fig. 2
and presented in Section 6.2, the best model is chosen by
comparison by eye to the observed line profiles extracted
from five different aperture sizes (45, 90, 135, 180, and
240 mas).

**–**
We adjust the large-scale model to make the temperature profile continuous, while still fitting the ACA observations. This
consists of setting _T_ ◦ [Outer] to the temperature value at the outer
radius of the intermediate region. Then, ϵ [Outer] had to be modified to fit the lines observed by the ACA.

**–**
We investigate mismatches between our best model and observations that imply departure from spherical symmetry and
we modify the velocity field to address two of these issues,
as discussed in Section 6.4.


After obtaining a good fit to the data, we estimate the sensitivity of the model to variations of the input parameters to provide an estimate of the uncertainty in the derived physical structure. To this goal, we present a grid of models in Section 6.5
covering the parameter space around the parameters of the temperature and density profiles of the best models with modified
velocity field. The velocity field is not modified in the grid calculations.



As shown in Fig. 2 for the best-fit model, the models were
compared to the data cubes for each of the four transitions considered by matching spectra extracted from the observed and
modelled cubes using five different aperture sizes (45, 90, 135,
180, and 240 mas), which correspond to sizes ranging from
smaller than the stellar photosphere at mm wavelengths up to
∼ 4 stellar radii in radius.


_5.4._ _Central star and radiation field_


We approximate the central star by a black-body source with a
temperature of 2370 K, based on the measurement of the stellarcontinuum brightness temperature from the Band 7 observations
(Vlemmings et al. 2019). This temperature has an important effect on the absorption lines seen towards the star, because the
amount of absorption depends directly on the difference between
the brightness temperature of the stellar continuum and the excitation temperature of the molecules in question.
The stellar radiation field is also important for the excitation of CO through ro-vibrational lines ∆ _v_ = 1 or 2 through
absorption of near-IR photons with wavelengths ∼ 4.6 and
∼ 2.3 µm, respectively. Therefore, the stellar infrared radiation
field at these wavelengths can have a direct effect on the level
populations of the CO _v_ = 1 levels relevant for our study. Van
de Sande et al. (2018) studied the spectral energy distribution of
R Dor employing an effective temperature of 2500 K, which is
very close to the value we use. We do not expect differences of a
few hundred Kelvin in effective temperature to affect the stellar
radiation field at 2.3 and 4.6 µm significantly, while the effect on
the strength of absorption will likely be stronger. Hence, considering a black-body star with temperature equal to 2370 K is the
most appropriate for our study.


**6.** **Modelling results**


_6.1._ _Model for the large-scale outflow_


The profile of the CO _v_ = 0, _J_ = 2 − 1 produced by the model
chosen as representative of the brightness distribution in the region of the central beam of the ACA observations is shown in
comparison to the line observed by the ACA in Fig. 5. Particular care was taken to select a model which produced enough
emission at the systemic velocity, because the emission region
at this projected velocity is expected to be the largest. Hence,
the problem of emission filtered out by the interferometer can be
expected to be more important at this velocity.
To fit the line extracted from the central beam of the ACA
observations, we find that our model requires a systemic velocity of 6.7 km/s and a value of ϵ [Outer] ≈ 0.6 for a gas temperature


Article number, page 7 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



at the inner radius of the outer region, _T_ ◦ [Outer], ≈ 400 K, assuming
a terminal velocity of 5.5 km/s. The value for the temperature
at _R_ [Outer] in (5 _R_ [⋆] 887µm [) was selected based on an initial exploration]
of the gas temperatures required in the inner region to fit the
lines produced in the extended atmosphere. Then, we made adjustments as required as the model for the inner regions of the
circumstellar envelope converged.
Fig. 6 shows an image of the model spanning a region comparable to the ACA beam in the observation of the CO _v_ = 0, _J_ =
2 − 1 line. As can be seen, the surface brightness integrated over
velocity decreases by about a factor of ten between a radius of
0 [′′] . 12 (the maximum radius from which we extract spectra to
compare to our models of the extended atmosphere) and 3 [′′] (the
approximate size of the ACA beam).


_6.2._ _Model for the inner circumstellar envelope_


The velocity, density, and kinetic temperature profiles of our best
spherically symmetric model (with rotation) for the innermost
regions are shown in Fig. 7. The departures from symmetry in the
velocity field discussed in Section 6.4 are also indicated in the
figure by the red lines. We explored freely the parameter space
defined by the three-zone structure presented in Section 5.2 to
produce this model. The constraints discussed in Section 4 allowed us to quickly narrow down the region of the parameter
space that provided good fits to the data. We found clear boundaries on the parameter space beyond which models were unsuitable to fit the observations. For instance, models with densities
≳ 10 [10] cm [−][3] in the intermediate region produce emission in the
_v_ = 1 lines from that region, which is not observed, while models
with densities < 10 [10] cm [−][3] in the inner region failed to produce
the observed emission in these same lines. The temperature profile in the inner region was also well constrained by the relative
amount of absorption and emission in the different lines arising
from that region.
We find the interface between the inner and intermediate region to be located at 1.6 _R_ [⋆] 887µm [and that between the intermedi-]
ate and outer region to be located at 5.0 _R_ [⋆] 887µm [.] [However,] [the]
position of this second interface is not well constrained, and its
purpose is only to mark the transition in the velocity profile as
discussed in Section 6.2.2. The broad lines that are produced in
the extended atmosphere (spanning more than 20 km/s) require
gas distributed over a comparable velocity range (≳ 15 km/s) in
the models, even if we use a relatively high stochastic velocity
for the inner region (4 km/s).
To fit the line profiles of the inner regions, we apply a shift
of 7.4 km/s to the modelled lines. This is in agreement with the
value derived based on the absorption feature discussed in Section 4.2 but not with the value of 6.7 km/s derived from fitting
the large-scale emission observed by the ACA discussed in Section 6.1. The different values of the systemic velocities obtained
by different methods is discussed in Section 7.1.


6.2.1. The innermost region


The innermost layer must be falling towards the star with relatively small velocities for the model to reproduce the observed
absorption features in the observed lines. This is quite well constrained because the _v_ = 1 levels are only significantly excited
in this innermost layer. Hence, all the absorption seen in the
CO _v_ = 1, _J_ = 2 − 1 and 3 − 2 lines is produced by gas in
this innermost region. This layer also accounts for most of the
absorption in the _v_ = 0 lines, because of the relatively high den

Article number, page 8 of 28



|30<br>25<br>20 Fluxdensity[Jy]<br>15<br>10<br>5<br>0|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|0<br>5<br>10<br>15<br>20<br>25<br>30<br>Flux density [Jy]|||||||||


10 5 0 5 10 15 20
Velocity [km/s]


**Fig.** **5.** CO _v_ = 0, _J_ = 2 − 1 line extracted from the central beam of
the ACA observations (blue histogram) compared to the spectrum from
our best model extracted from the same region (solid orange line). The
dashed vertical lines show the two different values derived for the systemic velocity 6.7 km/s and 7.4 km/s, which were derived, respectively,
by fitting the position of the CO _J_ = 2 − 1 line observed with the ACA
(Section 6.1) and using the central velocity of the absorption feature
seen against the star (Section 4.2).


sities discussed below. We find that infall velocities ≲ 6 km/s are
required to reproduce the observed velocity of the absorption
features. Small deviations between the observed and modelled
profiles of the _v_ = 0 and _v_ = 1 lines are apparent. This is likely
not caused by variability because observations in each epoch include both one _v_ = 0 and one _v_ = 1 line.
To produce the ring seen in the maps of the _v_ = 1 lines,
we find that the innermost layer in the models must contain gas
that is relatively warm and dense, with particle densities of ∼
10 [11] cm [−][3] . The density profile is very steep in the innermost
region, with an exponent η ∼ 7. Even at these high densities,
the CO _v_ = 1 levels are sub-thermally populated. To reproduce
the observed ratio between absorption and emission, the models
require a very steep gas temperature profile very close to the star,
with ϵ ∼ 2.


6.2.2. The intermediate and outer regions


After the very steep radial decrease in the innermost region, the
temperature profile becomes shallower, with exponents ≲ 0.7 in
the intermediate and outer regions.
The gas particle density decreases from values between ∼
10 [10] and ∼ 10 [11] cm [−][3] in the inner region, to values between
∼ 10 [8] and ∼ 10 [9] cm [−][3] in the intermediate region, to lower values in the outer region. At 10 _R_ [⋆] 887µm [,] [the] [density] [in] [our] [model]
reaches values of a few times 10 [6] cm [−][3] . The density profile becomes much shallower in the intermediate region, with η ∼ 3.0
between _R_ [Inter][.] and 10 _R_ [⋆]
in 887µm [, where we assume that the terminal]
velocity has been reached. In fact, both the temperature and the
density profiles can be described with a single exponent valid
for both the intermediate and outer regions. The only requirement for introducing a boundary between these two regions is
the velocity profile, which we assume to increase from 2.0 km/s
at 5 _R_ [⋆]
887µm [to 5.5 km][/][s at 10] _[ R]_ [⋆] 887µm [. The relatively high expan-]

T. Khouri et al.: R Dor seen by ALMA



3


2



Normalized line intensity [Jy GHz/beam]
3.0 2.5 2.0 1.5 1.0 0.5 0.0



1


0


1


2


3


3 2 1 0 1 2 3

RA [arcseconds]


**Fig.** **6.** Brightness distribution of the frequency-integrated CO _v_ =
0, _J_ = 2 − 1 line in our model. The colormap shows the base-10 logarithm of the intensity (per pixel) normalised to the peak value in the
image. In the pixels towards the star, where negative values lead to undefined logarithms, we arbitrarily set very negative values. The inset
shows a zoom towards the inner region. The dashed contours mark the
largest aperture from where we extract spectra for our inner-envelope
model (inner contour) and the size of the ACA beam (outer contour).
The brightness decreases by about a factor of ten between these two

contours.


sion velocities at the intermediate layer are required to produce
the blue-shifted absorption observed in the CO _v_ = 0, _J_ = 2 − 1
line but this higher-velocity gas could be located at a different
radial distance within the intermediate region without affecting
our model significantly. Hence, the exact shape of the velocity
profile in the intermediate and outer regions is not very well constrained and, especially in the outer region, depends strongly on
our assumptions.


_6.3._ _The_ [13] _CO line_


The only parameter varied when fitting the observed [13] CO _v_ =
0, _J_ = 3 − 2 line was the [13] CO abundance. We initially assumed
a value of 10 for the [12] CO/ [13] CO ratio as reported in the literature (Ramstedt et al. 2014), which implies a [13] CO abundance of
4 × 10 [−][5] relative to H 2 . However, such a model produces toostrong absorption and emission compared to the observations.
The model for R Dor presented by Ramstedt et al. (2014) consisted of a mass-loss rate of 1.6 × 10 [−][7] M ⊙ /yr and a CO abundance of 2 × 10 [−][4], which differ by a factor of 1.6 and 2.0 from
the mass-loss rate and CO abundance adopted by us. We obtain
a much better fit (shown in Fig. 2) using a [13] CO abundance of
2.7 × 10 [−][5] relative to H 2, which corresponds to a [12] CO/ [13] CO of
15. Given the uncertainties in the models and the different massloss rates and molecular abundances between our study and that
of Ramstedt et al. (2014), the discrepancy is not concerning.



**Table** **2.** Range of parameters explored in the models and steps used.
In the third column, it is indicated by + or × whether the successive
values of the given parameter were obtained by adding or multiplying,
respectively, the previous value and the step size.


Parameter Min. Step Number of steps
Inner Region
_n_ [Inn] ◦ 3.3 × 10 [10] ×3.3 5
η ◦ [Inn] 5 +1 5
ϵ ◦ [Inn] 1.0 +0.5 5
Intermediate Region
_n_ [Inter] ◦ [.] 1.0 × 10 [8] ×3.3 5
η ◦ [Inter][.] 1 +1 5
ϵ ◦ [Inter][.] 0.37 +0.15 5
_T_ ◦ [Inter][.] 540 +200 5 [1]


_6.4._ _Effects of departures from spherical symmetry in the line_
_profiles_


The observations show multiple deviations from our symmetric
model with rotation: a velocity-shift between the _v_ = 0 and _v_ = 1
lines, mismatching contributions to the red-shifted [12] CO _v_ = 0
emission, and two emission blobs. We adjust our model to address the former two, as we interpret these mismatches as being
connected to the description of the velocity field. We describe
the mismatches and our modelling strategy to overcome them
here. We do not attempt to model the blobs in the outflow, but
characterise them in Section 6.6.


6.4.1. Shift between centre velocities of CO lines in the _v_ = 0

and _v_ = 1 states


When we compare both the emission profiles extracted from
larger regions and the absorption profiles, we find a deviation
between the prediction from our spherically symmetric model
with rotation and the observed velocity of the centre of the
CO _v_ = 0, _J_ = 2 − 1 and CO _v_ = 1, _J_ = 3 − 2 lines (Fig. 8).
An inspection of the CO _v_ = 1, _J_ = 3 − 2 channel maps reveals a
much more symmetric emission ring at velocities of ∼ 13.5 km/s
in the observations ( Fig. B.2) than the model with symmetric velocity distribution and rotation ( Fig. B.4). In order to reproduce
the observed brightness distribution, more emission is required
at that (red-shifted) velocity to the east of the star.
To improve the fit to both the line profile and the resemblance
of the channel maps of the CO _v_ = 1 lines, we modified the velocity field of the innermost region of the far-side hemisphere
(with respect to the Earth) by substituting the infall by an outflow with a velocity of ∼ 12 km/s. This shifts the centre of the
CO _v_ = 1 lines by the required amount. Interestingly, the absorption profile shown in Fig. 4 also reveals outflow and infall in the
inner layers towards the east of the star, indicating that at least
parts of the inner layer are indeed moving away from R Dor.
Hence, even if our approximation of an outflowing inner layer
in the far-side of the envelope is somewhat rough, the existence
of outflowing gas in this inner layer which is mostly not seen in
absorption is plausible based on the data.


6.4.2. CO _v_ = 0, _J_ = 2 − 1 line profile


Our model also fails to reproduce the CO _v_ = 0, _J_ = 2 − 1 emission line profiles because emission is not produced at the correct


1 An extra set of models was added with _T_ Inter◦ . = 400 K, increasing to
a total of six grid steps in this parameter.


Article number, page 9 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



Radius [AU]
1.8 9.2 18.4 27.5

|Col1|Col2|Col3|
|---|---|---|
||||
||||



1 5 10 15
Radius R 887 m



2500


2000


1500


1000


500


0



15.0


12.5


10.0


7.5


5.0


2.5


0.0


2.5


5.0



Radius [AU]
1.8 9.2 18.4 27.5

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||
||||||
||||||
||||||
||||||
||||||
||||||
||||||
||||||



1 5 10 15
Radius R 887 m



10 [12]


10 [11]


10 [10]


10 [9]


10 [8]


10 [7]


10 [6]



Radius [AU]
1.8 9.2 18.4 27.5

|Col1|Col2|Col3|
|---|---|---|
||||
||||



1 5 10 15
Radius R 887 m



**Fig.** **7.** Physical structure of the best model shown in Fig. 2 and presented in Section 6. The orange lines show the profiles of radial velocity
(left panel), density (middle panel), and temperature (right panel) in the symmetric model with rotation and the red lines show the modifications
introduced in the velocity field in the far-side hemisphere to improve the fit to the line profiles. The tangential (rotational) velocity is not indicated
in these plots. The grey line in the temperature panel shows a grey atmosphere temperature profile. The vertical light grey lines mark the transition
between the inner and intermediate regions and between the intermediate and outer regions in the model (as shown in Table 1).



velocities on the red-shifted side of the line. This is particularly
noticeable for spectra extracted from apertures with diameters
larger than about 120 mas, when emission dominates with respect to the absorption (e.g. Fig. 8). To suppress emission at the
required velocities, we modified the velocity field in the intermediate region by changing the outflow in the far-side hemisphere
to a slight infall, with velocities ≲ 6 km/s.


_6.5._ _Model sensitivity assessment_


To assess the sensitivity of the model to the input parameters and
quantify the uncertainties of the derived temperature and density
profiles, we ran two grids of models. In these grids, we varied the
density and temperature at the inner radius of the inner and intermediate shells and the exponents of the temperature and density
profiles. Contrary to the models discussed up to this point, we did
not require the temperature profile to be continuous in these calculations. We do not expect this approach to produce physically
viable models, but our intention is to better isolate the effects of
varying different parts of the temperature profile. If the temperature profile is required to be continuous, changes to one region
imply modifications to the others. This makes interpreting the
effects of variation in one parameter more difficult.
The parameters of each region were varied in two independent grids because otherwise a very large number of model calculations would be necessary. For each of the grids, the parameters of the region not being modified were kept the same as those
of the best model (Section 6.2) for that region. The velocity field
in all models was the same and includes the modifications introduced in Sections 6.4.1 and 6.4.2. The parameters of the outer region were always kept the same as the best model (Section 6.2).
The range of parameter space explored in the two grids of
models is given in Table 2 and is shown in Fig. 9. The grid
over the parameters for the inner and intermediate regions consisted of 125 and 750 models, respectively. T [Inn] ◦ was kept fixed
at _T_ [⋆]
887 µm [(2370 K).]


Article number, page 10 of 28



The models were ranked based on the sum of the squares of
the residuals obtained from subtracting a given grid model from
the best model from Section 6.2. The comparison was done using the two lines which provided the strongest constraints, CO
_v_ = 0, _J_ = 2 − 1 and _v_ = 1, _J_ = 3 − 2, extracted from the apertures with 45, 90, 135, 180, and 240 mas in diameter (same line
spectra as shown in Fig. 2). Both models were convolved with
the respective ALMA beam before subtraction, but we did not
perform simulation of ALMA observations with the respective
array configuration for these comparisons. This approach was
chosen because simulating the ALMA observations is time consuming and simulating all models from the grid would require
a large amount of computation time. Since the brightness distribution of the extended outflow was kept unchanged and we
aim to minimise differences in the brightness distribution of the
inner regions, the effect of resolving-out flux would be very similar for any good model. Therefore, by comparing grid models to
the best model in this way, we avoid the long computation time
without introducing any biases or shortcomings in our model selection.

Finally, we compared the top-ranked models by eye to judge
whether the fits were indeed acceptable. This approach was employed because the complexity of the model makes the ranking based on squared residuals too simplistic. We discuss the
model-selection procedure with examples in more detail in the
Appendix A.

Only one model from the grid for the inner region provided
a good fit to the data, while 52 models from the grid for the intermediate region provided good fits. Hence, the model for the
innermost region is very well constrained, with all acceptable
models producing the same set of parameters. The model for the
intermediate region has a larger range of acceptable values. We
attribute this to the stronger constraints provided by emission
detected both in the _v_ = 1 and _v_ = 0 CO lines in the inner region,
while only the CO _v_ = 0, _J_ = 2−1 line is seen in the intermediate
region. This single transition does not allow us to break the de

T. Khouri et al.: R Dor seen by ALMA



|Col1|Col2|
|---|---|
|||
|0.05<br>0.10<br>.||
|0.05<br>0.10<br>.||


|Col1|10 20 30 city [km/s]|
|---|---|
|||
|0.00<br>0.05<br>0.10<br>0.15<br>0.20<br>0.25<br>0.30||
|0.00<br>0.05<br>0.10<br>0.15<br>0.20<br>0.25<br>0.30||


20 10 0 10 20 30 40

Velocity [km/s]


**Fig.** **8.** Comparison between the CO _v_ = 1, _J_ = 3 − 2 (upper panel)
and CO _v_ = 0, _J_ = 2 − 1 (lower panel) line profiles of the model with
symmetric radial velocity field (green dashed line) and the model with
an outflow with the modifications to the velocity field discussed in Sections 6.4.1 and 6.4.2 (yellow solid line). The observed spectra are shown
by the blue histograms and the possible values of the systemic velocity
are indicated by the vertical dashed gray lines. We adopt a systemic velocity of 7.4 km/s when shifting the model to fit the data. All spectra
were extracted from an aperture with 240 mas diameter centred on the
star. In the lower panel, the spectrum of the model with the modifications to the velocity field is shown without simulating of observation by
the ALMA array (dotted red line). In this case, only smoothing to the
beam resolution was carried out. Hence, the comparison between the
red dotted line and the yellow solid line shows how much flux is being
resolved out by simulating the interferometric observations.


generacy between density and temperature distributions for the
intermediate region. The radial profiles of the temperature and
density of the selected grid models are shown in Fig. 9. On average, these models show lower densities in the intermediate region than our best model from Section 6.2.
The density of an outflow with constant velocity of 5.5 km/s
and mass-loss rate of 10 [−][7] M ⊙ /yr is also shown in Fig. 9 by the
black dashed line. For a steady-state wind, the average density
as a function of radius in the inner regions would be expected
to be higher than this line. Since the density in an outflow with
constant mass-loss rate scales proportionally to the inverse of the
expansion velocity, gas densities would be below or above this
line for faster or slower gas velocities, respectively. In a steadystate outwards-accelerating outflow, the dashed line corresponds
to a lower limit for the gas density as a function of radius.


_6.6._ _Blobs_


We identify two blobs of gas are much brighter in the CO _v_ =
0, _J_ = 2 − 1 line than their surroundings in the ALMA observations. The first blob has a small projected distance and seems to
be located very close to the extended atmosphere to the north


west of the star. The second, seems to lie at a significantly larger
distance from the star in the southeast direction.


6.6.1. Inner northwest blob


This blob blends in the images with emission from the inner and
intermediate layers. It is located roughly between 0 [′′] . 08 (4.7 AU,
2.6 _R_ [⋆]
887 µm [) and 0] [′′] [.] [15 (8.85 AU, 4.8] _[ R]_ [⋆] 887 µm [) from the centre of]
R Dor and has an extent in the tangential direction of roughly
110 mas, as shown in Fig. 10. Although an inspection of the
channel maps ( Fig. B.1) suggests that this blob is indeed located
close or even partially inside the extended atmosphere, it is not
certain that this is not a projection effect.
Isolating the blob emission from that of the gas along the
same column is difficult because of its projected location and
velocities very close to those of the high-density regions of the
extended atmosphere. Instead of attempting to integrate emission over the whole blob, we extracted spectra towards the blob
using an aperture of 60 mas in diameter with a centre placed at
0. [′′] 12 (7.1 AU, 3.85 _R_ [⋆] 887 µm [) from the centre of the star towards]
the northwest. This radius and aperture size were chosen so that
the whole aperture lies within the blob while avoiding significant contamination from the bright ring of the extended atmosphere. We also extracted the spectrum towards a corresponding aperture (same size and distance from the star) towards the
southwest (away from blob). This southwest position was chosen because the spectra would be expected to be equal to that of
the region towards the blob, given the sphericity and the southnorth rotation axis considered in the model. We find the observed
CO _v_ = 0, _J_ = 2 − 1 line has a flux of (1.32 ± 0.03) × 10 [−][21] W/m [2]
and a full-width at half maximum (FWHM) of 8.5 ± 0.3 km/s
towards the blob and a flux of (0.80 ± 0.02) × 10 [−][21] W/m [2] and
a FWHM of 8.9 ± 0.3 km/s away from the blob. The spectra are
shown in Fig. 10.
We isolate the blob emission from that of the more extended outflow by subtracting the spectrum obtained towards
the region in the southwest (away from the blob) from that obtained towards the northwest (towards the blob). For this offsetcorrected spectrum, we obtain the fairly gaussian line shown in
Fig. 10, which has an amplitude of 15 mJy, a central velocity
of 13.5 km/s, a FWHM of 4.9 km/s, and an integrated flux of
∼ 5 × 10 [−][22] W/m [2] .
To estimate the excitation temperature, we use eight SO 2
lines, six in Band 7 and two in Band 6, identified in the spectrum extracted from the 60 mas aperture. We measured the line
fluxes by integrating the spectra over the observed line profiles.
The obtained line fluxes were used to calculate the column density of molecules in the upper level, _N_ u, for each transition. We
derived an excitation temperature by fitting the distribution of
level populations of SO 2 molecules following the procedure described in Goldsmith & Langer (1999). The best fit and the associated uncertainty were obtained using the curve_fit function of
the optimize module in the SciPy package. We find an excitation
temperature of SO 2 of 545 ± 113 K (green points in Fig. 11).
Based on the temperature profile in our model, this gas temperature is reached at ∼ 3.4 _R_ [⋆] 887 µm [from] [the] [star.] [Considering]
the one-σ interval in excitation temperature, we find a range in
radii between ∼ 2.6 _R_ [⋆]
887 µm [and][ ∼] [4][.][6] _[ R]_ [⋆] 887 µm [. The upper range]
of this estimated radial distance implies the angle between the
position vector of the blob and the plane of the sky to be at most
∼ 30 [◦] . Taking into account the line-of-sight velocity of the blob
with respect to the systemic velocity (∼ 7 km/s), we find a radial
velocity of ∼ 13 km/s and an ejection timescale ∼ 2 years. If the


Article number, page 11 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



2500


2000


1500


1000


500


0

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||



1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0


|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||



1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0



10 [12]


10 [11]


10 [10]


10 [9]


10 [8]


10 [7]


10 [6]


10 [5]



Radius [R 887 m ] Radius [R 887 m ]


**Fig.** **9.** Models that provide an acceptable fit to the observed CO line profiles (solid lines). The grey region indicates the region over which the
values of gas temperature and density as a function of radius can vary in the context of our model and still fit the data. The black dashed line
indicates the density of an outflow with a constant velocity of 5.5 km/s and a mass-loss rate of 10 [−][7] M ⊙ /yr. The dotted lines represent the limits of
the range explored in the grid calculations for the temperature and density profiles.



blob is closer to the plane of the sky, its radial velocity increases
considerably. For 15 [◦], we find a radial expansion velocity of
∼ 25 km/s. Hence, angles between the position vector of the
blob and the plane of the sky smaller than 15 [◦] imply relatively
high velocities and are unlikely.
Assuming optically thin emission towards the blob, an excitation temperature of CO of 550 K implies an excess gas mass of
∼ 3 × 10 [−][8] M ⊙ is necessary to reproduce the emission measured
within the 60 mas aperture towards the northwest with respect
to the one towards the southwest (green line in Fig. 10). Assuming this region to be representative of the density of the blob
and approximating the blob by an ellipse with minor and major
axes equal to 70 and 110 mas, we find a total excess mass of
∼ 6 × 10 [−][8] M ⊙ . Assuming the size of the blob along the line of
sight to be 5.3 AU (the average between the axes of the ellipse
considered above), we find an excess H 2 density of ∼ 10 [8] cm [−][3] .
This compares to densities of 8 × 10 [7] cm [−][3] and 5 × 10 [7] cm [−][3] in
the CO model at 3.85 and 4.45 _R_ [⋆]
887 µm [, respectively. Hence, the]
gas density within the blob is between a factor of two to three
times that at a similar distance from the star to the southwest.


6.6.2. High-velocity southeast blob


The blob to the southeast of R Dor, shown in Fig. 12, has a projected radial distance of ∼ 0 [′′] . 36 (21.5 AU, 11.7 _R_ [⋆] 887 µm [)] [from]
the centre of the star. Even if this blob is considerably outside
of the region we consider when fitting our model (up to 0 [′′] . 12,
or 4 _R_ [⋆] [in] [radius] [around] [the] [star),] [its] [peculiar] [characteris-]
887 µm [,]
tics make the derivation of its properties potentially relevant for
understanding the wind-driving mechanism.
Using the spectrum extracted from an aperture of 0 [′′] . 14 diameter towards the blob, we find an average line-of-sight velocity of
the blob ∼−14 km/s with respect to the systemic velocity. The
line profile has a full-width at half maximum of ∼ 6.5 km/s, as
can be seen in the spectrum extracted towards the blob (Fig. 12).
We interpret the velocity along the line of sight to be the projection of a radial expansion velocity. An alternative explanation
is that the blob is in orbit and has a tangential, rather than radial, velocity around R Dor. The expected orbital velocities at
21.5 AU from a 1.3 M ⊙ star is ∼ 7 km/s, considerably less than
the observed velocity along the line of sight. Moreover, consid

Article number, page 12 of 28



ering the low probability of observing a blob at an edge-on orbit
near its point of maximum projected velocity along the line of
sight, the scenario in which this is a gas blob orbiting R Dor is
unlikely.
A radially moving blob with projected negative velocity can
be located either at the near side of the circumstellar envelope
and moving away from R Dor (outflow), or at the far side of the
envelope and falling towards R Dor (infall). Given that the flow
velocity gets more negative with increasing distance from the
star, the explanation that the blob is moving away from R Dor
(and towards us) is favoured.
Similarly to the analysis of the inner northwest blob, we use
seven SO 2 lines in the ALMA Band 6 and Band 7 spectra towards the high-velocity blob to estimate the excitation temperature of SO 2 . We find an excitation temperature of 202 ± 12 K
(yellow points in Fig. 11). Assuming the excitation temperature for CO to be the same of SO 2, we derive a gas mass of
∼ 6 × 10 [−][8] M ⊙ . Additionally, the assumed excitation temperature of ∼ 200 K is equal to the gas kinetic temperature in our
model at ∼ 16 _R_ [⋆]
887 µm [from the star, implying an angle between]
the blob position and the plane of the sky ∼ 45 [◦] . For an angle
ranging from 30 [◦] to 60 [◦], we estimate the radial expansion velocity of this blob (υ blob ), its radial distance from R Dor (∆ _r_ blob ) and
the time since its ejection (∆ _t_ blob ) to be 25 < ∆ _r_ blob < 43 AU
(13.5 < ∆ _r_ blob < 23.4 _R_ [⋆] 887 µm [),] [16] [≲] [υ] [blob] [≲] [28] [km][/][s] [and]
4 ≲ ∆ _t_ blob ≲ 12 years. Combined with our mass estimate, this
leads to mass-loss rates between ∼ 5×10 [−][9] and ∼ 2×10 [−][8] M ⊙ /yr
related to the process that created the blob. Assuming the blob
to be roughly as thick in depth as it is in width, we estimate an
average gas density of ∼ 4 × 10 [7] H 2 molecules per cm [3] in the
blob.


**7.** **Discussion**


_7.1._ _Systemic velocity_


The discrepancy between the systemic velocity obtained from
fitting the CO _v_ = 0, _J_ = 2 − 1 line observed using the ACA
(∼ 6.7 km/s) and from fitting the sharp absorption features and
the emission in the CO lines (∼ 7.4 km/s) is noteworthy, but
a systemic velocity of ∼ 7 km/s is a reasonable compromise
between these two values given the uncertainties. Nonetheless,

T. Khouri et al.: R Dor seen by ALMA


Integrated line intensity [mJy km/s/beam]

0 2 4 6 8 10





160


80


0


80


160



32


31


30


29


28


27


26


25


|Col1|TH exV c = 202 ± 12 K<br>TI en xn cer= 545 ± 113 K|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



80 0 80 160


D [miliarcsec]











**Fig.** **10.** Upper panel: integrated line intensity (moment-zero) map of
CO _J_ = 2 − 1 emission integrated in velocity between 9 km/s and
19 km/s. The dashed white circles shows the region from which we
extracted spectra to characterise the blob (circle on the northern hemisphere) and the region for the reference spectrum (circle on the southern
hemisphere). The white ellipse shows the half-power size of the ALMA
beam. Lower panel: spectrum towards the inner blob (blue solid line)
and a corresponding region in the southern hemisphere (brown dashed
line). The dash-dotted green line shows the difference between these
two spectra, the solid yellow gaussian shows the fit to the excess emission in the northwest. The gaussian function has an amplitude of 15 mJy,
a standard deviation of 1.9 km/s and is centred at 13.4 km/s. For reference, the vertical dashed gray line indicates one of the values for the
systemic velocity derived by us (7.4 km/s).


the position of the sharp absorption feature discussed in Section 4.2 and its mismatch with respect to the expected position
(at υ = υ sys − υ ∞ ) indicates that there might be an underlying
cause for the difference in derived systemic velocity between the
two methods.



0 200 400 600 800 1000 1200

E u [K]


**Fig.** **11.** Rotational diagram for SO 2 lines towards inner blob (green)
and high-velocity blob (orange).


One possibility is that the expansion velocity in the largescale outflow adopted by us is too large. A maximum expansion velocity of 4.8 km/s would lead to a consistent value of
υ sys = 6.7 km/s both for the fit to the ACA line and the absorption feature. However, this would produce a too-narrow
CO _v_ = 0, _J_ = 2 − 1 line in comparison to the profile obtained
with the ACA.

Another possible explanation is an asymmetry in the velocity
field of the large-scale outflow. If the approaching hemisphere of
the envelope has an average velocity towards us of 4.8 km/s (and,
accordingly, the receding hemisphere has a velocity of 6.2 km/s),
the fit to the ACA line and the absorption feature would both be
consistent with a systemic velocity of ∼ 6.7 km/s. This scenario
would not explain the improved fit to the lines produced in the
inner circumstellar envelope when using the higher systemic velocity (∼ 7.4 km/s). Since the observed shift is relatively small
in velocity compared to the gas motions observed in the inner
circumstellar envelope, this could most likely be overcome by
modifying the velocity field in the model. Nonetheless, we refrain from exploring this in this study. The most straightforward
way to assess whether there is an asymmetric velocity distribution in the large-scale envelope is through a detailed analysis of
the ACA maps. Such an investigation of the large-scale outflow
is out of the scope of the present study.


_7.2._ _Stochastic velocity in the large-scale outflow_


The value of the stochastic velocity we measure (≲ 0.4 km s [−][1] )
can be compared to previous measurements of 0.7 ± 0.1 km s [−][1]
in the outflow of W Hya (Khouri et al. 2014), and of 1.5 km/s
(De Beck et al. 2012), 0.9 km/s (Huggins & Healy 1986) and
0.35 km/s (Morris et al. 1985) in the outflow of CW Leo. Hence,
we find a relatively low value comparable to that found by Morris et al. (1985) towards CW Leo. Our method of determination
is very direct because it relies solely on the broadening of the absorption feature produced by gas in the large-scale outflow. The
study of W Hya relied on the shift of the line centres which is
also affected by uncertainties on other parameters (such as the
assumed systemic velocity). The studies of CW Leo mentioned
above relied on the line shapes of the large-scale CO emission,


Article number, page 13 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



Integrated line intensity [mJy km/s/beam]

0.0 0.5 1.0 1.5 2.0


600


400


200


0


200


400


600
600 400 200 0 200 400 600


D [miliarcsec]









20 10 0 10 20

Velocity [km/s]


**Fig.** **12.** Upper panel: integrated line intensity (moment-zero) map of
the CO _v_ = 0, _J_ = 2 − 1 emission integrated in velocity between -14
and -1 km/s. The white ellipse in the lower right corner shows the size
at half maximum of the ALMA gaussian beam. Lower panel: spectrum
extracted towards the region defined by the blob in the upper panel (blue
histogram). A gaussian fit to the emission associated with the blob is
shown in the solid orange line. For reference, the vertical dashed gray
line indicates one of the values for the systemic velocity derived by us
(7.4 km/s).


which is subject to uncertainties on asymmetries of the density
distribution and/or velocity field.


Unfortunately, it is often unclear whether the reported values correspond to the standard deviation or the full-width at
half maximum of the gaussian line profiles. The upper limit of
≲ 0.4 km s [−][1] for the standard deviation we report corresponds
to values of ≲ 0.95 km s [−][1] for the full-width at half maximum.
Hence, differences in the quantities being reported might account
for at least part of the spread found in the literature.


Article number, page 14 of 28



_7.3._ _Circumstellar gas mass_


Our model shown in Fig. 2 implies a gas mass of ∼ 3 × 10 [−][5] M ⊙
and ∼ 2 × 10 [−][6] M ⊙ in the inner and intermediate regions, respectively. By integrating the profiles of the acceptable models from our sensitivity study (shown in Fig. 9), we obtain
∼ (3 ± 1) × 10 [−][5] M ⊙ for the inner region and ∼ 1.4 × 10 [−][6] M ⊙,
with an uncertainty of a factor of two, for the intermediate region. Hence, our best model provides gas masses in the inner
and intermediate regions which are very close to the average
values obtained from the accepted models from the sensitivity
study. These values are to be compared to the average mass-loss
rate of R Dor ∼ 10 [−][7] M ⊙ /yr. The crossing times for a velocity
of 5 km/s are ∼ 1 and ∼ 6 yrs for the inner and intermediate
regions, respectively. Therefore, for reasonable outflow velocities, these layers would sustain mass-loss rates of > 10 [−][5] M ⊙ /yr
(inner) and ∼ 2 × 10 [−][7] M ⊙ /yr (intermediate). If the current gas
density distribution is representative of the inner circumstellar
environment of R Dor, these values suggest that the vast majority of gas in the innermost region would fall back to the star or
remain in the extended atmosphere for hundreds of years, while
a significant fraction (or even all) of the mass in the intermediate
region would be expelled. Therefore, our circumstellar model is
consistent with the transition between the inner and intermediate
regions (at 1.6 _R_ [⋆] 887 µm [) corresponding to the transition between]
extended atmosphere and wind.
The (gravitationally bound) extended atmosphere is reminiscent of the gravitationally bound dust shells invoked to explain
aluminium oxide dust emission in W Hya and R Dor (Khouri
et al. 2015; Van de Sande et al. 2018), and also found in winddriving models (Höfner et al. 2016). The aluminium oxide dust
mass inferred for the gravitationally bound dust shell in R Dor
(∼ 6 × 10 [−][10] M ⊙, Khouri 2014) translates to a gas mass of
∼ 4 × 10 [−][6] M ⊙ assuming solar composition (Asplund et al.
2021) and full aluminium condensation. Hence, we find a lot
more gas in the inner regions than required by the gravitationally
bound dust shell models. However, a conclusive correspondence
of these two structures requires determining the distributions of
the aluminium oxide dust and the gas from spatially resolved
observations carried out close in time.


_7.4._ _Temperature profile_


The very steep temperature profile indicates very efficient cooling in the innermost layers of the circumstellar envelope of
R Dor. The steepness (ϵ) is constrained mostly from the ratio
between absorption and emission as a function of aperture radius. In the following paragraphs, we discuss potential alternative ways to reproduce the observations without resorting to a
steep temperature profile, and make comparisons to other observations and expectations from hydrodynamical models.
It is important to note that our models for the [13] CO line imply
a slightly shallower temperature profile in the inner region than
the CO, _v_ = 0 line, because more emission is seen with respect to
absorption than our model produces. Since the [13] CO _v_ = 0, _J_ =
3 − 2 line was observed about two weeks later than the CO _v_ =
0, _J_ = 2 − 1 one, this could be at least partly due to variability.
In such a warmer model, with an exponent for the temperature
in the inner region of 1.6 instead of 2.0, the fit to the [13] CO _v_ =
0, _J_ = 3−2 line is satisfactory when considering a [12] CO/ [13] CO of
10 reported by (Ramstedt et al. 2014), instead of the value of 15
required by our best model. This difference in the temperature
profile corresponds to gas temperatures at 1.6 _R_ [⋆] 887µm [higher] [by]

∼
about 200 K ( 20%).

T. Khouri et al.: R Dor seen by ALMA



Lines that are more optically thick in reality than in our
models could increase the strength of absorption with respect
to emission without the need to make the gas cooler. We note
that the inner regions of our model reach indeed relatively high
optical depths (≲ 10) in the CO _v_ = 0, _J_ = 2 − 1 line. However, two facts speak against even higher optical depths being
responsible for the relatively strong absorption. First, the four
transitions modelled by us have very different optical depths for
a given line of sight, because of differences in level populations
of the given transition or abundance of the given molecule. Second, an inspection of the cubes observed by ALMA reveals that
in the CO _v_ = 0, _J_ = 2 − 1 line (expected to reach the highest optical depths), the maximum brightness temperature in the bright
ring is ∼ 450 K. For optically thick emission, the brightness temperature of spatially resolved structures should reflect the actual
source function, which in turn should be the same as the gas
kinetic temperature for the _J_ = 2 − 1 transition at such high
gas densities. Therefore, this measured brightness temperatures
(which are well reproduced by our model) also imply relatively
low gas kinetic temperatures close to the star even if the optical
depths in our models are underestimated.
Another alternative for the steep temperature profile is a significant asymmetry in the gas densities, with more gas present
in lines of sight towards the star than offset from it. Considering that we identify a few blobs in the vicinity of R Dor, this is
not entirely unlikely. Although we cannot rule out this scenario,
we disfavour it at this point because it requires a specific configuration of the envelope. Multi-epoch observations of R Dor
and/or other targets can help determine whether density fluctuations around the star significantly affect the ratio between observed absorption and emission.
These considerations suggest that the steep temperature profile in the innermost region is indeed a real feature of the envelope at the time of the observations. In fact, a comparison
with other observational results indicates that steep temperature profiles might be a widespread feature of the circumstellar environments of oxygen-rich AGB stars. Observations of the
CO _v_ = 1, _J_ = 3 − 2 line towards Mira (Khouri et al. 2018)
and W Hya (Vlemmings et al. 2017) also reveal low, ≲ 900 K,
excitation temperatures in the inner circumstellar environment
(≲ 2 _R_ ⋆ ). Even if we find that the CO _v_ = 1 levels are likely subthermally excited for the gas densities obtained in these studies, the excitation temperature derived for them is the rotationalexcitation temperature within the _v_ = 1 level, which should be
close to the kinetic temperature at these gas densities (Vlemmings et al. 2017; Woitke et al. 1999).
Spatially resolved observations of the brightness temperature of the continuum using ALMA also reveal a temperature profile for R Dor within < 1.05 _R_ [⋆] 887 µm [which] [is] [signifi-]
cantly steeper than that of a grey atmosphere model (Vlemmings
et al. 2019). The continuum brightness temperature reported at
∼ 1.035 _R_ [⋆] [∼] [2000] [K] [is] [even] [lower] [than] [we] [find] [at] [the]
887 µm [of]
same radial distance (∼ 2240 K). In fact, the difference between
our temperature profile and a grey model over this radial distance
is small (see Fig. 7). We note that the observations of R Dor reported by (Vlemmings et al. 2019) were acquired over one and
a half months, and stellar variability might have played a role in
the observed variations.

Comparisons to predictions from theoretical models is another way to assess whether these findings are expected. However, such comparisons are not simple because the observations
we report provide only one snapshot of the properties of the inner
envelope. Hence, we investigated whether dynamical models can



at all produce temperature profiles as steep as that inferred by us.
Our results imply that the kinetic temperature decreases by a factor ∼ 2.5 between _R_ [⋆]
887 µm [and 1.6] _[ R]_ [⋆] 887 µm [, with the temperature]
at _R_ [⋆]
887 µm [being 2370 K. The most extreme temperature profiles]
presented by Ireland et al. (2011) decrease by at most a factor of
2.2 between the radius at which they reach 2370 K and a 60%
larger radius. The profiles shown by Freytag & Höfner (2023)
and Höfner et al. (2016) have shallower profiles with factors of
at most ∼ 1.7 over the relevant range. This comparison indicates
that existing dynamical models might be able to reproduce the
very steep profile we observe in certain phases of specific models, but not often. If future observations indicate that such steep
profiles are the rule, more efficient cooling in dynamical models
would be necessary. This would likely have a significant impact
on the calculations of dust growth and wind driving in such models.


_7.5._ _Blobs_


7.5.1. Inner blob


The properties of the inner blob identified in the maps seem
consistent with bubbles created from convection in dynamical
models (e.g. Freytag & Höfner 2023), but the inferred expansion ∼ 13 km/s velocities seem rather high at a fairly large distance from the star (∼ 4.6 _R_ [⋆] 887 µm [)] [in] [comparison] [with] [the] [ob-]
served terminal velocity of the outflow, ∼ 5.5 km/s. A study of
the dust content of this inner blob in comparison to the gas properties derived here will be performed in an upcoming publication
(Schirmer et al., _in prep._ ). The gas mass of this blob implies that
a similar blob needs to be ejected at most every few years to
account for the mass-loss rate observed on larger scales.


7.5.2. High-velocity blob


The high-velocity blob seen to the southeast in the CO _v_ = 0, _J_ =
2−1 line stands out as an unexpected feature of the circumstellar
envelope of R Dor. We assume the blob to be moving radially
away from the star, because it seems unlikely that it would have a
high tangential velocity (as argued in Section 6.6.2). The density
estimated from the CO _v_ = 0, _J_ = 2 − 1 line flux is at least one
order of magnitude larger than the densities expected based on
our model (not including blobs).
Although the SO 2 excitation temperature in the blob is quite
well constrained by our population diagram (202 ± 12 K) there
is considerable uncertainty on the blob position because the kinetic temperature is expected to vary slowly with radius at these
distances from the star. Also, for both blobs the excitation temperature of SO 2 might differ from the kinetic temperature, and
the kinetic temperature within the blob might differ from that of
the surrounding gas (and, hence, from our model) given the difference in density. For reference, the kinetic temperature in the
model varies from 220 K to 160 K between 13.5 _R_ [⋆]
887 µm [and]
23.4 _R_ [⋆] [The] [most] [direct] [way] [to] [constrain] [the] [position] [of]
887 µm [.]
the blob would be new measurements to determine its proper
motion, given the short estimated ejection times between 4 and
12 years.


_7.6._ _Velocity distribution and wind-driving mechanism_


Our results reveal a complex velocity distribution around the star,
with outflow and infall of gas in the innermost region. Moreover, we find departures from spherical symmetry both between


Article number, page 15 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted



the near and far hemispheres of the innermost layer, as well as
in the absorption profile observed against the star. The fact that
we observe different absorption profiles against the stellar disc,
which is resolved by only a few resolution elements, indicates
that there is a relatively large-scale component of the velocity
distribution with scales comparable to that of the star. The conclusion that the innermost region is dominated by infall in the
near hemisphere and outflow in the far one points in the same
direction. We attribute the gas velocity distribution in the inner
region to be mostly a consequence of convective motions and
pulsation of the star. Although a much faster rotation than expected for an isolated AGB stars has been reported for R Dor
(Vlemmings et al. 2018), the projected velocities along the line
of sight are much smaller than the radial velocities we infer, and
should not affect significantly the inflow and outflow velocities
we report. We find no evidence in the data examined by us of a
disk around R Dor, as suggested by (Homan et al. 2018).

Outside the inner, dense region, the circumstellar envelope
seems to transition quickly to the outflow which is observed on
large scales. From the absorption profile, we find a relatively fast
layer of outward-moving gas, which might be a shock front as
expected from dynamical models (e.g. Höfner & Freytag 2019).
As discussed above, it is not straightforward to determine the
exact location of the gas producing this absorption, but the fact
that it is not seen in the _v_ = 1 lines indicates that it is located at
_r_ - 1.6 _R_ [⋆] [Regarding] [the] [acceleration] [profile,] [we] [assume]
887 µm [.]
that the terminal velocity of the large-scale outflow is reached
only at 10 _R_ [⋆] 887 µm [in] [our] [model,] [but] [the] [data] [are] [most] [likely]
also consistent with faster acceleration. However, this was not
explored in our calculations.

We introduced the two modifications to the velocity field
only on the far side of the envelope so that they do not affect
the absorption profile produced by our model, which was the
starting point of the modelling procedure and fits the absorption
profiles very well. It is not surprising that the velocity field of the
model we derived based on the absorption observed against the
star does not fit the velocity field in the far hemisphere. However,
it is somewhat surprising that the two hemispheres would have,
on average, the opposite behaviour, as shown in Fig. 7. While in
the near side of the envelope the inner and intermediate regions
in our model are falling towards and moving away from the star,
respectively, in the far side of envelope they flow outwards and
fall back, respectively, instead. As discussed in Section 4.2, we
see signatures of different velocity components in the absorption
profile of the CO _v_ = 1, _J_ = 3 − 2 line, which indicates that
the far-side vs near-side division is only a rough approximation.
Hence, the exact relative size and distribution of the infalling and
outflowing components are not strongly constrained. Nonetheless, the scenario in which the far and near sides of the envelope
have behaviours which on average are quite different is a good
description of the velocity field that reproduces the line profiles
well.

The importance of the gas blobs to the wind-driving process
is not clear from the analysis we have carried out. While the
inner blob could be produced by convection, the process that
produced the high-velocity blob is less clear. It could be driven
by radiation pressure on dust, in principle, because wind-driving
models reach comparable outflow velocities of ∼ 20 km/s (e.g.
Bladh et al. 2019). However, it is unclear why this one blob
would have velocities so much higher than those of the largescale outflow (∼ 5.5 km/s) at such large distances, or how the
interaction between this blob and the slower moving gas proceeds. Decin et al. (2018) argued that a high-velocity component


Article number, page 16 of 28



exists in the circumstellar envelope of R Dor, either because of
blobs or acceleration of the large-scale outflow. An inspection
of the central-beam ACA spectrum we use for constraining the
large-scale outflow (Fig. 5) reveals weak wings extending to
maximum expansion velocities ∼−17 km/s on the blue-shifted
side of the CO _v_ = 0, _J_ = 2−1 line with flux densities < 100 mJy
for velocities < −9 km/s. The CO _v_ = 0, _J_ = 2 − 1 line extracted
from an aperture with 240 mas diameter reveals flux densities at
±10 km/s of ∼ 50 mJy, while the spectrum of the high-velocity
blob peaks at ∼ 50 mJy at ∼−14 km/s. Hence, the combination
of emission from the extended atmosphere and the high-velocity
blob seem to account for all observed high-velocity emission detected in the ACA spectrum. If a significant larger mass of highvelocity gas existed, stronger emission should have been picked
up by the ACA observations.
Based on these considerations, we conclude that the highvelocity blob observed is either a very rare event that will propagate through the envelope at its relatively high velocity, or that
such ejections happen on timescales more comparable to the
inferred ejection timescale (∼ 10 years) and that the produced
blobs get slowed down on a comparable timescale. Although we
cannot reach a definitive conclusion, the second scenario seems
more plausible both based on the unlikelihood of observing a
rare event and on the hydrodynamical interactions between blob
and outflow, which must act to decelerate the blob on long
timescales. If this is indeed the case, this blob should be observed to dissipate in the near future and similar blobs should be
created. We point out that a more complex morphology is seen
in the [29] SiO _v_ = 0, _J_ = 5 − 4 line (Vlemmings et al. 2018), which
could imply this to be a feature that is stable on somewhat longer
timescales than expected in the scenario explored by us.
The inner blob reported by us is a good candidate for producing a new high-velocity blob. Therefore, future observations
of R Dor will shed light on the nature of these features, and will
allow the study of the processes controlling the wind driving in
real time.


**8.** **Summary**


We report observations using ALMA of the AGB star R Doradus. The high-angular resolution of the observations allows
even for the stellar photosphere at sub-mm wavelengths to be
spatially resolved with uniform disc size of ∼ 62 mas, corresponding to ∼ 1.835 AU at 59 pc.
We investigate the properties of the gas in the extended atmosphere around the continuum source using lines _v_ = 0, _J_ = 2 − 1
and the _v_ = 1, _J_ = 2 − 1 and 3 − 2 lines of [12] CO, and
_v_ = 0, _J_ = 3 − 2 of [13] CO. Based on the absorption produced
by the cooler gas against the star, we determine that gas in the
near-side hemisphere can be divided in two layers with different
average velocities. The innermost layer is falling back to the star,
while the layer above that is moving outwards. The Band 7 observations of the CO _v_ = 1, _J_ = 3 − 2 and [13] CO _v_ = 0, _J_ = 3 − 2
lines, which were acquired at higher spatial resolution, also show
how both the intensity of absorption and the velocity distribution
of the absorbing gas change across the stellar disc. The absorption profile of the CO _v_ = 0, _J_ = 2 − 1 line also shows a sharp
feature which we attribute to absorption produced in the largescale outflow. Based on the profile of this feature, we constrain
the standard deviation of the stochastic velocity distribution in
the outer wind to be ≲ 0.4 km/s.
Based on the velocity field inferred from the absorption profiles, we construct a model to fit the observed lines using the 3D
molecular excitation and line radiative transfer code LIME. We

T. Khouri et al.: R Dor seen by ALMA



find temperature and density profiles that are very steep close
to the star and become shallower at radii - 1.6 _R_ [⋆] [While]
887 µm [.]
the innermost region contains a lot of mass - 10 [−][5] M ⊙, most
of which will fall back to the star or remain in this region for
centuries before becoming gravitationally unbound, the circumstellar envelope seems to quickly transition to gas densities consistent with those expected from the mass-loss rate reported in
the literature. We find that our symmetric model including rotation fails to reproduce some aspects of the observed line positions and shapes. This is solved by reversing the velocity field
between the innermost and intermediate layers in the far side of
the envelope. A disagreement between the systemic velocity determined based on the large scale CO _v_ = 0, _J_ = 2−1 line profile
and based on the profile of the absorption against the star leads
us to speculate that the velocity field of the large-scale envelope
might be asymmetric.
We characterise two blobs found at small angular separations
from the central star. One of them, seen very close to the central
star (at a distance of ∼ 4.5 _R_ [⋆] 887 µm [), resembles structures created]
in hydrodynamical models through the action of convection, but
we are unable to determine its formation mechanism. We find
an excess mass in this blob with respect to its surroundings of
∼ 6 × 10 [−][8] M ⊙, which implies that blobs such as this have to
be created every few years to have a substantial effect on the
mass-loss rate of R Dor. The second blob, most likely located
at a radial distance of ∼ 16 _R_ [⋆] [is] [moving] [at] [a] [consider-]
887 µm [,]
ably higher velocity (∼ 20 km/s) than expected at these distances
from the star. Surprisingly, we also infer it to contain a gas mass
of ∼ 6 × 10 [−][8] M ⊙ . We find it was created roughly during the last
10 years.
Understanding the properties of these blobs seems important
for advancing our understanding of the wind-driving mechanism
in AGB stars. Even if the mass-loss rate associated with them
turns out to be much lower than that derived for R Dor, understanding the different processes at play would undoubtedly provide significant insight into the relevant processes at play. The
fate of these blobs when moving through the slower-moving circumstellar envelope is at the moment unclear. Monitoring their
evolution would provide important new constraints.


_Acknowledgements._ The authors would like to thank the anonymous referee for the careful reading of the paper and the constructive comments
which helped improve the quality of this manuscript. This paper makes
use of the following ALMA data: ADS/JAO.ALMA#2017.1.00191.S,
ADS/JAO.ALMA#2017.1.00824.S, and ADS/JAO.ALMA#2017.1.00595.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. TK and
VW acknowledge support from the Swedish Research Council through grants
2019-03777 and 2020-04044, respectively. TS acknowledges support from the
Knut and Alice Wallenberg Foundation through grant nr. KAW 2020.0081. MS
acknowledges support from the research council of Norway, project number:
335497.


**References**


Adam, C. & Ohnaka, K. 2019, A&A, 628, A132
Andriantsaralaza, M., Ramstedt, S., Vlemmings, W. H. T., & De Beck, E. 2022,
A&A, 667, A74
Asplund, M., Amarsi, A. M., & Grevesse, N. 2021, A&A, 653, A141
Bedding, T. R., Zijlstra, A. A., Jones, A., & Foster, G. 1998, MNRAS, 301, 1073
Bladh, S., Liljegren, S., Höfner, S., Aringer, B., & Marigo, P. 2019, A&A, 626,
A100
Brinch, C. & Hogerheijde, M. R. 2010, A&A, 523, A25
Castro, C., Doan, K., Klemka, M., et al. 2017, Molecular Astrophysics, 6, 47
Danilovich, T., Gottlieb, C. A., Decin, L., et al. 2020, ApJ, 904, 110
Danilovich, T., Lombaert, R., Decin, L., et al. 2017, A&A, 602, A14



De Beck, E., Decin, L., Ramstedt, S., et al. 2017, A&A, 598, A53
De Beck, E., Lombaert, R., Agúndez, M., et al. 2012, A&A, 539, A108
De Beck, E. & Olofsson, H. 2018, A&A, 615, A8
Decin, L., Richards, A., Danilovich, T., Homan, W., & Nuth, J. A. 2018, A&A,
615, A28
Decin, L., Richards, A. M. S., Waters, L. B. F. M., et al. 2017, A&A, 608, A55
Freytag, B. & Höfner, S. 2023, A&A, 669, A155
Gail, H.-P., Scholz, M., & Pucci, A. 2016, A&A, 591, A17
Gobrecht, D., Hashemi, S. R., Plane, J. M. C., et al. 2023, A&A, 680, A18
Gobrecht, D., Plane, J. M. C., Bromley, S. T., et al. 2022, A&A, 658, A167
Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209
Gottlieb, C. A., Decin, L., Richards, A. M. S., et al. 2022, A&A, 660, A94
Herwig, F. 2005, ARA&A, 43, 435
Hinkle, K. H. 1978, ApJ, 220, 210
Hinkle, K. H., Hall, D. N. B., & Ridgway, S. T. 1982, ApJ, 252, 697
Höfner, S. 2008, A&A, 491, L1
Höfner, S., Bladh, S., Aringer, B., & Ahuja, R. 2016, A&A, 594, A108
Höfner, S. & Freytag, B. 2019, A&A, 623, A158
Höfner, S. & Olofsson, H. 2018, A&A Rev., 26, 1
Homan, W., Danilovich, T., Decin, L., et al. 2018, A&A, 614, A113
Huggins, P. J. & Healy, A. P. 1986, ApJ, 304, 418
Ireland, M. J., Scholz, M., & Wood, P. R. 2011, MNRAS, 418, 114
Kami´nski, T., Wong, K. T., Schmidt, M. R., et al. 2016, A&A, 592, A42
Khouri, T. 2014, PhD thesis, Univ. of Amsterdam
Khouri, T., de Koter, A., Decin, L., et al. 2014, A&A, 570, A67
Khouri, T., Maercker, M., Waters, L. B. F. M., et al. 2016a, A&A, 591, A70
Khouri, T., Vlemmings, W. H. T., Olofsson, H., et al. 2018, A&A, 620, A75
Khouri, T., Vlemmings, W. H. T., Paladini, C., et al. 2020, A&A, 635, A200
Khouri, T., Vlemmings, W. H. T., Ramstedt, S., et al. 2016b, MNRAS, 463, L74
Khouri, T., Waters, L. B. F. M., de Koter, A., et al. 2015, A&A, 577, A114
Knapp, G. R., Pourbaix, D., Platais, I., & Jorissen, A. 2003, A&A, 403, 993
Morris, M., Lucas, R., & Omont, A. 1985, A&A, 142, 107
Nhung, P. T., Hoai, D. T., Tuan-Anh, P., et al. 2021, MNRAS, 504, 2687
Norris, B. R. M., Tuthill, P. G., Ireland, M. J., et al. 2012, Nature, 484, 220
Ohnaka, K., Weigelt, G., & Hofmann, K.-H. 2016, A&A, 589, A91
Ohnaka, K., Weigelt, G., & Hofmann, K.-H. 2017, A&A, 597, A20
Ohnaka, K., Weigelt, G., & Hofmann, K.-H. 2019, ApJ, 883, 89
Perryman, M. A. C. & ESA, eds. 1997, ESA Special Publication, Vol. 1200,
The HIPPARCOS and TYCHO catalogues. Astrometric and photometric star
catalogues derived from the ESA HIPPARCOS Space Astrometry Mission
Plane, J. M. C. 2013, Philosophical Transactions of the Royal Society of London
Series A, 371, 20120335
Ramstedt, S., Mohamed, S., Vlemmings, W. H. T., et al. 2014, A&A, 570, L14
Van de Sande, M., Decin, L., Lombaert, R., et al. 2018, A&A, 609, A63
Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261
Vlemmings, W., Khouri, T., O’Gorman, E., et al. 2017, Nature Astronomy, 1,
848
Vlemmings, W. H. T., Khouri, T., Beck, E. D., et al. 2018, A&A, 613, L4
Vlemmings, W. H. T., Khouri, T., & Olofsson, H. 2019, A&A, 626, A81
Woitke, P. 2006, A&A, 460, L9
Woitke, P., Helling, C., Winters, J. M., & Jeong, K. S. 1999, A&A, 348, L17
Wong, K. T., Kami´nski, T., Menten, K. M., & Wyrowski, F. 2016, A&A, 590,
A127


Article number, page 17 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


**Appendix A:** **Model selection for grid calculation**


The procedure of selecting models as acceptable fits consisted
of ranking the models based on the value of the sum of the
squared of the residuals in comparison to the best model from
Section 6.2. Then, the line profiles were inspected by eye.
The models shown in Fig. A.1 and A.2 exemplify why the
selection based on the residuals was not enough to select acceptable models. For instance, while a model that produces too
strong absorption for small apertures and too strong emission
for larger ones in the blue-shifted wing might have a value of the
squared residuals that is comparable to a model that produces
slightly too strong emission overall, the former model might be
a clear worse fit for the region producing the emission and absorption of the spatial region in question. In Fig A.3, we show
models calculated with the parameters of the best model for the
inner, intermediate, and outflow regions separately. These can be
used to train the eye to interpret how emission from the different
regions contribute to the line profiles. Of course, the addition of
these profiles is not the same as the profiles of the given model
because of optical depth effects.


Article number, page 18 of 28

T. Khouri et al.: R Dor seen by ALMA


**Fig. A.1.** Top-ranked models from our residual minimisation and considered good fits upon inspection of the line profiles. Observed spectra of the
CO _v_ = 0, _J_ = 2 − 1 line extracted from five different aperture sizes is shown by the blue histogram. From left to right, the apertures diameters
are 45 mas, 90 mas, 135 mas, 180 mas, and 240 mas. The dashed yellow lines represent the models. The first row shows our best model from
Section 6.2, while models from the grid considered acceptable are shown in the following rows.


Article number, page 19 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


**Fig. A.2.** Top-ranked models from our residual minimisation but considered not good fits upon inspection of the line profiles. Observed spectra
of the CO _v_ = 0, _J_ = 2 − 1 line extracted from five different aperture sizes is shown by the blue histogram. From left to right, the apertures
diameters are 45 mas, 90 mas, 135 mas, 180 mas, and 240 mas. The dashed yellow lines represent the models. The first row shows our best model
from Section 6.2, while models from the grid considered acceptable are shown in the following rows. The arrows indicate the main discrepancies
between the given grid models and our best model that led to the classification as unacceptable fits.


Article number, page 20 of 28

T. Khouri et al.: R Dor seen by ALMA


**Fig. A.3.** Spectra of the CO _v_ = 0, _J_ = 2 − 1 line extracted from five different aperture sizes is shown by the blue histogram. From left to right,
the apertures diameters are 45 mas, 90 mas, 135 mas, 180 mas, and 240 mas. The dashed yellow lines represent the models which were calculated
considering our best models and including only the inner layer (top), the intermediated layer (middle) and the outflow (bottom). See text for details
on the models.


Article number, page 21 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


**Appendix B:** **Channel maps**


Article number, page 22 of 28

T. Khouri et al.: R Dor seen by ALMA


250


0


250


500


250


0


250


500


250


0


250


500



250


0


250


500

|000 0.002 0.004 0.006 0.008 0.010 0.012 0.014 0.01|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|-7.6 km/s|-6.0 km/s|-4.4 km/s|-2.9 km/s|-1.3 km/s|
|0.3 km/s|1.9 km/s|3.5 km/s|5.1 km/s|6.7 km/s|
|8.3 km/s|9.8 km/s|11.4 km/s|13.0 km/s|14.6 km/s|
|16.2 km/s|17.8 km/s|19.4 km/s|21.0 km/s|22.5 km/s|



50 ~~0~~ 250 0 250 500



50 ~~0~~ 250 0 250 500



50 ~~0~~ 250 0 250 500



50 ~~0~~ 250 0 250 500



50 ~~0~~ 250 0 250 500



RA offset [milliarcsec]


**Fig. B.1.** Observed channel maps of the CO _v_ = 0, _J_ = 2 − 1 transition given in Jy/beam as a function of velocity.



Article number, page 23 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


**Fig. B.2.** Observed channel maps of the CO _v_ = 1, _J_ = 3 − 2 transition given in Jy/beam as a function of velocity.


Article number, page 24 of 28

T. Khouri et al.: R Dor seen by ALMA


250


0


250


500


250


0


250


500


250


0


250


500



250


0


250


500

|000 0.002 0.004 0.006 0.008 0.010 0.012 0.014 0.01|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|-11.1 km/s|-9.1 km/s|-7.1 km/s|-5.1 km/s|-3.1 km/s|
|-1.1 km/s|0.9 km/s|2.9 km/s|4.9 km/s|6.9 km/s|
|8.9 km/s|10.9 km/s|12.9 km/s|14.9 km/s|16.9 km/s|
|18.9 km/s|20.9 km/s|22.9 km/s|24.9 km/s|26.9 km/s|



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 500



RA offset [milliarcsec]


**Fig. B.3.** Channel maps for the CO _v_ = 0, _J_ = 2 − 1 line in the best model with symmetric velocity distribution and rotation. The emission is shown
in Jy/beam as a function of velocity. The white ellipse on the lower left corner of the upper right panel shows the size of the ALMA gaussian beam
at half power. The models were shifted to a systemic velocity of 6.7 km/s.


Article number, page 25 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


90


0


90


180


90


0


90


180


90


0


90


180



90


0


90


180

|000 0.002 0.004 0.006 0.008 0.010 0.012 0.014 0.01|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|-11.1 km/s|-9.1 km/s|-7.1 km/s|-5.1 km/s|-3.1 km/s|
|-1.1 km/s|0.9 km/s|2.9 km/s|4.9 km/s|6.9 km/s|
|8.9 km/s|10.9 km/s|12.9 km/s|14.9 km/s|16.9 km/s|
|18.9 km/s|20.9 km/s|22.9 km/s|24.9 km/s|26.9 km/s|



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 180



RA offset [milliarcsec]


**Fig. B.4.** Channel maps for the CO _v_ = 1, _J_ = 3 − 2 line in the best model with symmetric velocity distribution and rotation. The emission is shown
in Jy/beam as a function of velocity. The white ellipse on the lower left corner of the upper right panel shows the size of the ALMA gaussian beam
at half power. The models were shifted to a systemic velocity of 6.7 km/s.


Article number, page 26 of 28

T. Khouri et al.: R Dor seen by ALMA


250


0


250


500


250


0


250


500


250


0


250


500



250


0


250


500

|000 0.002 0.004 0.006 0.008 0.010 0.012 0.014 0.01|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|-11.1 km/s|-9.1 km/s|-7.1 km/s|-5.1 km/s|-3.1 km/s|
|-1.1 km/s|0.9 km/s|2.9 km/s|4.9 km/s|6.9 km/s|
|8.9 km/s|10.9 km/s|12.9 km/s|14.9 km/s|16.9 km/s|
|18.9 km/s|20.9 km/s|22.9 km/s|24.9 km/s|26.9 km/s|



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 50 ~~0~~



50 ~~0~~ 250 0 250 500



RA offset [milliarcsec]


**Fig. B.5.** Channel maps for the CO _v_ = 0, _J_ = 2 − 1 line in the best model with non-symmetric velocity distribution and rotation. The emission
is shown in Jy/beam as a function of velocity. The white ellipse on the lower left corner of the upper right panel shows the size of the ALMA
gaussian beam at half power. The models were shifted to a systemic velocity of 6.7 km/s.


Article number, page 27 of 28

_A&A proofs:_ manuscript no. RDor_ALMA_only_noSPHERE_accepted


90


0


90


180


90


0


90


180


90


0


90


180



90


0


90


180

|000 0.002 0.004 0.006 0.008 0.010 0.012 0.014 0.01|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|-11.1 km/s|-9.1 km/s|-7.1 km/s|-5.1 km/s|-3.1 km/s|
|-1.1 km/s|0.9 km/s|2.9 km/s|4.9 km/s|6.9 km/s|
|8.9 km/s|10.9 km/s|12.9 km/s|14.9 km/s|16.9 km/s|
|18.9 km/s|20.9 km/s|22.9 km/s|24.9 km/s|26.9 km/s|



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 18 ~~0~~



180 90 0 90 180



RA offset [milliarcsec]


**Fig. B.6.** Channel maps for the CO _v_ = 1, _J_ = 3 − 2 line in the best model with non-symmetric velocity distribution and rotation. The emission
is shown in Jy/beam as a function of velocity. The white ellipse on the lower left corner of the upper right panel shows the size of the ALMA
gaussian beam at half power. The models were shifted to a systemic velocity of 6.7 km/s.


Article number, page 28 of 28


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "59 pc",
  "failed_quote": "The distance determined from the Hipparcos parallax (62 ± 3 pc, Perryman & ESA 1997) is in good agreement with the distance derived by reanalysing the Hipparcos measurements, 59 pc (Knapp et al. 2003)."
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Knapp et al. 2003",
  "failed_quote": "The distance determined from the Hipparcos parallax (62 ± 3 pc, Perryman & ESA 1997) is in good agreement with the distance derived by reanalysing the Hipparcos measurements, 59 pc (Knapp et al. 2003)."
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "0''.6 (Band 6), 0''.42 (Band 7), ~31''.5 (ACA)",
  "failed_quote": "The ALMA observations are not sensitive to emission smooth on scales of >= 0''.6 and >= 0''.42 for the observations in Bands 6 and 7, which corresponds to regions of radius ~ 10 and ~ 7 R_887um^*, respectively."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Stellar continuum diameter (~62.2 mas, radius R_887um^* = 1.835 AU = 2.7e10 m) and brightness temperature (~2370 K) at ~338 GHz (~887 um)",
  "failed_quote": "Using the same Band 7 data employed in this paper, Vlemmings et al. (2019) studied the stellar continuum at ~ 338 GHz (~ 887 um). They report a size of ~ 62.2 mas and a brightness temperature at this frequency of ~ 2370 K between 330.15 and 344.17 GHz."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Stellar continuum diameter (~62.2 mas, radius R_887um^* = 1.835 AU = 2.7e10 m) and brightness temperature (~2370 K) at ~338 GHz (~887 um)",
  "failed_quote": "We use the stellar radius measured at 887 um, R_887um^* = 1.835 AU = 2.7 x 10^10 m, as a reference size in our calculations."
 },
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "Large-scale envelope mass-loss rate (~10^-7 M_sun yr^-1), expansion velocity (~5.5 km/s), and initial outer temperature profile",
  "failed_quote": "In our model for the outermost region, the gas density and radial velocity match those expected from extrapolating inwards the mass-loss rate (~ 10^-7 M_sun yr^-1) and expansion velocity (~ 5.5 km/s) derived from models for the large-scale envelope (Van de Sande et al. 2018)."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "0.4 mJy GHz/beam in Band 7 moment-zero maps of CO v=1, J=3-2 and 13CO v=0, J=3-2",
  "failed_quote": "The root-mean-square noise is 0.4 mJy x GHz/beam in both images."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Distance of 59 pc",
  "failed_quote": "The distance determined from the Hipparcos parallax (62 ± 3 pc, Perryman & ESA 1997) is in good agreement with the distance derived by reanalysing the Hipparcos measurements, 59 pc (Knapp et al. 2003)."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Stellar radius at 887 um (1.835 AU) and continuum brightness temperature (2370 K)",
  "failed_quote": "Using the same Band 7 data employed in this paper, Vlemmings et al. (2019) studied the stellar continuum at ~ 338 GHz (~ 887 um). They report a size of ~ 62.2 mas and a brightness temperature at this frequency of ~ 2370 K between 330.15 and 344.17 GHz."
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Outer wind mass-loss rate (~10^-7 M_sun yr^-1) and terminal expansion velocity (5.5 km/s)",
  "failed_quote": "In our model for the outermost region, the gas density and radial velocity match those expected from extrapolating inwards the mass-loss rate (~ 10^-7 M_sun yr^-1) and expansion velocity (~ 5.5 km/s) derived from models for the large-scale envelope (Van de Sande et al. 2018)."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Compute 3D radiative transfer models in LIME, convolve with the ACA beam, and fit to the CO v = 0, J = 2 - 1 spectrum from the central ACA beam by varying the outer temperature power-law exponent.",
  "failed_quote": "We varied the exponent of the temperature profile in the outflow, epsilon_Outer, to fit the emission in the CO J = 2 - 1 line in the central beam of the ACA observations."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "R_in^Outer = 5.0 R_887um^*, T_0^Outer = 400 K, n_0^Outer = 4 x 10^7 cm^-3, v_0 = 2.0 km/s, v_f = 5.5 km/s from 10 R_887um^*",
  "failed_quote": "5.0 x R_887um^*"
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[2]",
  "value": "R_in^Outer = 5.0 R_887um^*, T_0^Outer = 400 K, n_0^Outer = 4 x 10^7 cm^-3, v_0 = 2.0 km/s, v_f = 5.5 km/s from 10 R_887um^*",
  "failed_quote": "4 x 10^7 cm^-3"
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Mass-loss rate ~10^-7 M_sun yr^-1, terminal expansion velocity 5.5 km/s reached via linear acceleration from 5 to 10 R_887um^*, CO/H2 = 4 x 10^-4",
  "failed_quote": "In our model for the outermost region, the gas density and radial velocity match those expected from extrapolating inwards the mass-loss rate (~ 10^-7 M_sun yr^-1) and expansion velocity (~ 5.5 km/s) derived from models for the large-scale envelope (Van de Sande et al. 2018)."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[1]",
  "value": "Mass-loss rate ~10^-7 M_sun yr^-1, terminal expansion velocity 5.5 km/s reached via linear acceleration from 5 to 10 R_887um^*, CO/H2 = 4 x 10^-4",
  "failed_quote": "We assume an expansion velocity of 2.0 km/s at the inner radius of the outermost region of the model (R_in^Outer) and a linear acceleration profile that reaches the maximum expansion velocity at 10 R_887um^*."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[2]",
  "value": "Mass-loss rate ~10^-7 M_sun yr^-1, terminal expansion velocity 5.5 km/s reached via linear acceleration from 5 to 10 R_887um^*, CO/H2 = 4 x 10^-4",
  "failed_quote": "We adopt an abundance of CO relative to H2 by number equal to 4 x 10^-4 throughout the paper."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Visual comparison to central ACA beam spectrum, iteratively adjusting T_0^Outer and epsilon^Outer to maintain temperature continuity with the intermediate layer",
  "failed_quote": "We adjust the large-scale model to make the temperature profile continuous, while still fitting the ACA observations. This consists of setting T_0^Outer to the temperature value at the outer radius of the intermediate region. Then, epsilon^Outer had to be modified to fit the lines observed by the ACA."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[2]",
  "value": "Central black-body star with T = 2370 K and R_887um^* = 1.835 AU; CO/H2 = 4 x 10^-4; rotational levels up to J = 40 in v = 0, 1, 2",
  "failed_quote": "We adopt an abundance of CO relative to H2 by number equal to 4 x 10^-4 throughout the paper."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Run two independent grids of LIME models for the inner (125 models) and intermediate (750 models) regions, convolve with ALMA beams, rank by sum of squared residuals against the best model in 5 apertures for CO v=0 J=2-1 and v=1 J=3-2, visually inspect top-ranked models, and integrate density profiles to obtain gas masses.",
  "failed_quote": "By integrating the profiles of the acceptable models from our sensitivity study (shown in Fig. 9), we obtain ~ (3 ± 1) x 10^-5 M_sun for the inner region and ~ 1.4 x 10^-6 M_sun, with an uncertainty of a factor of two, for the intermediate region."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "60 mas diameter aperture at 0''.12 offset for inner blob; 0''.14 diameter aperture at 0''.36 offset for high-velocity blob",
  "failed_quote": "Instead of attempting to integrate emission over the whole blob, we extracted spectra towards the blob using an aperture of 60 mas in diameter with a centre placed at 0.''12 (7.1 AU, 3.85 R_887um^*) from the centre of the star towards the northwest."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Optically thin CO emission in the blobs; CO excitation temperature equals SO2 excitation temperature equals model kinetic temperature at the blob radius",
  "failed_quote": "Assuming optically thin emission towards the blob, an excitation temperature of CO of 550 K implies an excess gas mass of ~ 3 x 10^-8 M_sun is necessary to reproduce the emission measured within the 60 mas aperture towards the northwest with respect to the one towards the southwest (green line in Fig. 10)."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Optically thin CO emission in the blobs; CO excitation temperature equals SO2 excitation temperature equals model kinetic temperature at the blob radius",
  "failed_quote": "Assuming the excitation temperature for CO to be the same of SO2, we derive a gas mass of ~ 6 x 10^-8 M_sun. Additionally, the assumed excitation temperature of ~ 200 K is equal to the gas kinetic temperature in our model at ~ 16 R_887um^* from the star, implying an angle between the blob position and the plane of the sky ~ 45 deg."
 },
 {
  "path": "analysis_steps[4].validation.evidence[0]",
  "value": "Evaluated alternative orbital hypothesis for the high-velocity blob and rejected it based on Keplerian orbital speed (~7 km/s at 21.5 AU for 1.3 M_sun)",
  "failed_quote": "The expected orbital velocities at 21.5 AU from a 1.3 M_sun star is ~ 7 km/s, considerably less than the observed velocity along the line of sight."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Systemic velocity from ACA CO v=0, J=2-1 emission fit = 6.7 km/s",
  "failed_quote": "To fit the line extracted from the central beam of the ACA observations, we find that our model requires a systemic velocity of 6.7 km/s and a value of epsilon^Outer approx 0.6 for a gas temperature at the inner radius of the outer region, T_0^Outer, approx 400 K, assuming a terminal velocity of 5.5 km/s."
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Inner region H2 density at inner boundary (n_0^Inner) = 3.5e11 cm^-3",
  "failed_quote": "n_0 None 3.5 x 10^11 cm^-3 < n_0^Inner 1 x 10^9 cm^-3 < n_0^Interm. 4 x 10^7 cm^-3"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Inner region density power-law exponent (eta^Inner) = 7.0 dimensionless",
  "failed_quote": "eta > 0 7.0 > 0 2.8 Linear acceleration up to 10 R_887um^*"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Boundary radius between inner and intermediate regions (R_in^Intermediate) = 1.6 R_887um^*",
  "failed_quote": "We find the interface between the inner and intermediate region to be located at 1.6 R_887um^* and that between the intermediate and outer region to be located at 5.0 R_887um^*."
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Intermediate region H2 density at inner boundary (n_0^Interm) = 1e9 cm^-3",
  "failed_quote": "n_0 None 3.5 x 10^11 cm^-3 < n_0^Inner 1 x 10^9 cm^-3 < n_0^Interm. 4 x 10^7 cm^-3"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Intermediate region density power-law exponent (eta^Interm) = 2.8 dimensionless",
  "failed_quote": "eta > 0 7.0 > 0 2.8 Linear acceleration up to 10 R_887um^*"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Intermediate region temperature at inner boundary (T_0^Interm) = 940 K",
  "failed_quote": "T_0 T^* T^* T at R_out^Inner 940 K T at R_out^Interm. 400 K"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "12CO/13CO isotopic ratio = 15 dimensionless",
  "failed_quote": "We obtain a much better fit (shown in Fig. 2) using a 13CO abundance of 2.7 x 10^-5 relative to H2, which corresponds to a 12CO/13CO of 15."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Gas mass in the inner region (1.0 to 1.6 R_887um^*) = 3e-5 M_sun",
  "failed_quote": "By integrating the profiles of the acceptable models from our sensitivity study (shown in Fig. 9), we obtain ~ (3 ± 1) x 10^-5 M_sun for the inner region and ~ 1.4 x 10^-6 M_sun, with an uncertainty of a factor of two, for the intermediate region."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Gas mass in the intermediate region (1.6 to 5.0 R_887um^*) = 1.4e-6 M_sun",
  "failed_quote": "By integrating the profiles of the acceptable models from our sensitivity study (shown in Fig. 9), we obtain ~ (3 ± 1) x 10^-5 M_sun for the inner region and ~ 1.4 x 10^-6 M_sun, with an uncertainty of a factor of two, for the intermediate region."
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Inner northwest blob total excess gas mass = 6e-8 M_sun",
  "failed_quote": "Assuming this region to be representative of the density of the blob and approximating the blob by an ellipse with minor and major axes equal to 70 and 110 mas, we find a total excess mass of ~ 6 x 10^-8 M_sun."
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "High-velocity southeast blob gas mass = 6e-8 M_sun",
  "failed_quote": "Assuming the excitation temperature for CO to be the same of SO2, we derive a gas mass of ~ 6 x 10^-8 M_sun."
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "High-velocity southeast blob radial expansion velocity = 16 to 28 km/s",
  "failed_quote": "For an angle ranging from 30 deg to 60 deg, we estimate the radial expansion velocity of this blob (v_blob), its radial distance from R Dor (Delta r_blob) and the time since its ejection (Delta t_blob) to be 25 < Delta r_blob < 43 AU (13.5 < Delta r_blob < 23.4 R_887um^*), 16 <= v_blob <= 28 km/s and 4 <= Delta t_blob <= 12 years."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The velocity field of the gas seen in absorption against the stellar disc in Band 7 is non-uniform across the disc, showing stronger absorption and an additional blue-shifted outflow component (up to ~15 km/s) towards the east compared to the west.",
  "failed_quote": "The Band 7 observations also reveal that the spatial distribution of the absorption is not uniform against the stellar disc (Fig. 4)."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "The vast majority of the gas in the innermost layer (1.0 to 1.6 R_887um^*) is gravitationally bound and will fall back to the star or remain in the extended atmosphere for hundreds of years, while the transition at 1.6 R_887um^* marks the onset of the wind.",
  "failed_quote": "If the current gas density distribution is representative of the inner circumstellar environment of R Dor, these values suggest that the vast majority of gas in the innermost region would fall back to the star or remain in the extended atmosphere for hundreds of years, while a significant fraction (or even all) of the mass in the intermediate region would be expelled. Therefore, our circumstellar model is consistent with the transition between the inner and intermediate regions (at 1.6 R_887um^*) corresponding to the transition between extended atmosphere and wind."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "The combined thermal and stochastic velocity standard deviation in the large-scale outflow is at most ~0.4 km/s.",
  "failed_quote": "Using a sharp absorption feature seen in the CO v = 0, J = 2 - 1 line, we constrain the standard deviation of the stochastic velocity distribution in the large-scale outflow to be <= 0.4 km/s."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Keplerian orbit or far-side infall for the high-velocity southeast blob (rejected because orbital velocity at 21.5 AU around a 1.3 M_sun star is only ~7 km/s vs ~14 km/s observed, and flow velocity becomes more negative with distance).",
  "failed_quote": "The expected orbital velocities at 21.5 AU from a 1.3 M_sun star is ~ 7 km/s, considerably less than the observed velocity along the line of sight."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[3].evidence[0]",
  "value": "Lower terminal expansion velocity (4.8 km/s) to reconcile the systemic velocity discrepancy between ACA emission (6.7 km/s) and absorption against the star (7.4 km/s) (rejected because it produces a too-narrow CO v=0 J=2-1 line compared to the ACA profile).",
  "failed_quote": "A maximum expansion velocity of 4.8 km/s would lead to a consistent value of v_sys = 6.7 km/s both for the fit to the ACA line and the absorption feature. However, this would produce a too-narrow CO v = 0, J = 2 - 1 line in comparison to the profile obtained with the ACA."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Single transitions in the intermediate region (only CO v=0, J=2-1 detected) cannot break the degeneracy between density and temperature distributions in that zone.",
  "failed_quote": "This single transition does not allow us to break the degeneracy between density and temperature distributions for the intermediate region."
 }
]
```
