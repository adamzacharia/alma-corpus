# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...686L..13D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. DeSimone_IRAS4A_diskwind ©ESO 2024
May 1, 2024


Letter to the Editor

## **FAUST XV. A disk wind mapped by CH 3 OH and SiO in the inner 300** **au of the NGC 1333 IRAS 4A2 protostar.**


M. De Simone [1][,][ 2], L. Podio [2], L. Chahine [3], C. Codella [2][,][ 3], C. J. Chandler [4], C. Ceccarelli [3], A. López-Sepulcre [3][,][ 5], L.
Loinard [6][,][ 7], B. Svoboda [4], N. Sakai [8], D. Johnstone [9][,][ 10], F. Ménard [3], Y. Aikawa [11], M. Bouvier [12], G. Sabatini [2], A.
Miotello [1], C. Vastel [13], N. Cuello [3], E. Bianchi [14], P. Caselli [15], E. Caux [13], T. Hanawa [16], E. Herbst [17], D. Segura-Cox [15][,][ 18],
Z. Zhang [8], and S. Yamamoto [19]


_(A_ ffi _liations can be found after the references)_


May 1, 2024


**ABSTRACT**


_Context._ Understanding the connection between outflows, winds, accretion and disks in the inner protostellar regions is crucial for comprehending
star and planet formation process.
_Aims._ We aim to we explore the inner 300 au of the protostar IRAS 4A2 as part of the ALMA FAUST Large Program.
_Methods._ We analysed the kinematical structures of SiO and CH 3 OH emission with 50 au resolution.
_Results._ The emission arises from three zones: i) a very compact and unresolved region (<50 au) dominated by the ice sublimation zone, at ±1.5
km s [−][1] with respect to v sys, traced by methanol; ii) an intermediate region (between 50 au and 150 au) traced by both SiO and CH 3 OH, between
2 and 6 km s [−][1] with respect to v sys, with an inverted velocity gradient (with respect to the large scale emission), whose origin is not clear; iii)
an extended region (> 150 au) traced by SiO, above 7 km s [−][1] with respect to v sys, and dominated by the outflow. In the intermediate region we
estimated a CH 3 OH/SiO abundance ratio of about 120–400 and a SiO/H 2 abundance of 10 [−][8] . We explored various possibilities to explain the
origin of this region such as, rotating disk/inner envelope, jet on the plane of the sky/precessing, wide angle disk wind.
_Conclusions._ We propose that CH 3 OH and SiO in the inner 100 au probe the base of a wide-angle disk wind. The material accelerated in the wind
crosses the plane of the sky, giving rise to the observed inverted velocity gradient, and sputtering the grain mantles and cores releasing CH 3 OH
and SiO. This is the first detection of a disk wind candidate in SiO, and the second ever in CH 3 OH.


**Key words.** Stars: formation — ISM: chemical abundances — ISM: protostars — ISM: molecules — ISM: astrochemistry — ISM: young stellar
objects



**1.** **Introduction**


Solar-like stars form from an accreting object deeply embedded
in a dense envelope that drives bipolar jets. To allow the accretion from the disk onto the protostar, the angular momentum is
extracted from the disk by jets/outflows or disk winds (e.g., Shu
et al. 1987). Understanding the accretion and ejection mechanisms and their impact on the physical and chemical structure of
protostars is of paramount importance to our comprehension of
the evolution of the forming stellar/planetary system.
Low-mass Class 0 protostars (∼10 [4] yr; Andre et al. 2000)
are the most studied objects to investigate both the accreting
region and the molecular outflows. Some protostars hosts hot
(>100 K), compact (<100 au), dense (> 10 [7] cm [−][3] ) regions rich
in iCOMS (interstellar Complex Organic Molecules; Herbst &
Van Dishoeck 2009; Ceccarelli et al. 2017), where the ice mantle
sublimation dominates the chemistry (called hot corinos; Ceccarelli 2004). However, not every protostar possesses a hot corino
(e.g., De Simone et al. 2017; Belloche et al. 2020; Bouvier et al.
2022; Yang et al. 2020; De Simone et al. 2020; De Simone
et al. 2022a), and their physical and chemical structure is still
not clear. Among the few known hot corinos, only a handful
are spatially resolved (SVS13-A, HH212, IRAS 16293A, B335;
Bianchi et al. 2023; Lee et al. 2022a; Maureira et al. 2022; Okoda
et al. 2022). Here, the iCOMs emission seems to probe different
layers of the hot corino or selected regions associated to accretion shocks and/or hot spots.



On the other hand, jets and outflows driven by protostellar
sources have been extensively studied, especially at scales larger
than 500 au (e.g., Ray et al. 2007; Arce et al. 2007; Frank et al.
2014). However, their origin is still debated. Models predict that
magneto centrifugal mechanisms extracts material from the disk
from two regions: close to the dust truncation radius by a stellar magnetosphere (X-wind models: Shu et al. 1994; Arce et al.
2007; Shang et al. 2007), and a wider range of radii outside this
dust truncation radius (disk-wind models: Blandford & Payne
1982; Konigl & Pudritz 2000; Tsukamoto et al. 2022).
These winds have been considered as a solution to the angular momentum problem in the inner 50 au of the disks (e.g.,
Pascucci et al. 2023). However, only a handful of resolved disk
winds observations are available (e.g., Tabone et al. 2017; Zhang
et al. 2018; Louvet et al. 2018; de Valon et al. 2020; Lee et al.
2021a; López-Vázquez et al. 2024). These type of observations provide crucial information (e.g., geometry, kinematical
and chemical structure) to constrain disk wind models, and to retrieve their origin, and the interplay between accretion and ejection mechanisms.

In this Letter we explore the inner 300 au of the IRAS 4A2
protostar as part of the ALMA FAUST [1] (Codella et al. 2021)
Large Program in SiO and CH 3 OH. We study the kinematics of
the gas in the transition zone between a possible disk and the


1 Fifty AU STudy of the chemistry in the disk/envelope systems of
Solar-like protostars; `[http://faust-alma.riken.jp](http://faust-alma.riken.jp)` .


Article number, page 1 of 11

_A&A proofs:_ manuscript no. DeSimone_IRAS4A_diskwind



ouflowing material, and present, for the first time, a wide disk
wind candidate for NGC 1333 IRAS 4A2 traced by SiO.


_The target:_ NGC 1333 IRAS 4A is a very well studied system
in Perseus (∼300 pc away; Zucker et al. 2018). It is composed
of two protostars: IRAS 4A1 (4A1 hereinafter), the brightest in
mm continuum, and IRAS 4A2 (4A2 hereinafter), separated by
about 1 [′′] . 8 (about 540 au; Looney et al. 2000; Santangelo et al.
2015; López-Sepulcre et al. 2017; Tobin et al. 2018). They are
surrounded by a common envelope of about 8 M ⊙ (Maury et al.
2019) and have a total bolometric luminosity of about 9 L ⊙ (Kristensen et al. 2012; Karska et al. 2013). Note that the system is
also known to show, at sub-mm wavelengths on years timescales,
a ∼10% peak to peak variability that can slightly affect the luminosity (Lee et al. 2021b; Mairs et al. 2024). Their mm dust emission is optically thick in the central region (Maury et al. 2019;
Galametz et al. 2019; Li et al. 2017; Ko et al. 2020; GuerraAlvarado et al. 2023) to completely obscure (for 4A1) or partially absorb (for 4A2) the mm iCOMs emission (De Simone
et al. 2020). The two protostars emit large bipolar jet/outflows,
deeply studied with several tracers, such as CO, SiO, SO, HCN
and some iCOMs (including methanol; e.g., Lefloch et al. 1998;
Choi et al. 2011; Ching et al. 2016; De Simone et al. 2020;
Chuang et al. 2021). The southern lobes are blue-shifted, and the
northern ones red-shifted and they cover a large velocity range
(up to 60 km s [−][1] ; Choi 2005; Santangelo et al. 2015; Taquet et al.
2020). However, none of the previous studies resolve the inner
200 au (below 0 [′′] . 7). The FAUST data provide the superb spatial
resolution of 50 au, that allows us to explore for the first time
these inner regions using selected chemical tracers.


**2.** **Observations**


The observation of NGC 1333 IRAS 4A we present here are
part of the Cycle 6 ALMA Large Program FAUST (PI. S. Yamamoto, 2018.1.01205.L). They were performed between October 2018 and September 2019 with baselines for the 12-m array between 15.1 m and 3.6 km. The bandpass and flux calibrator was J0237+2848, while J0336+3218 and J0328+3139 were
used for the phase calibration. The map phase center is at R.A.
(J2000) = 03h29m10s.539, Dec. (J2000)= 31 [◦] 13 [′] 30 [′′] . 92. For this
work we used CH 3 OH (5 1,4 − 4 1,3 A) and SiO (5 − 4) lines at
243.916 GHz and 217.105 GHz, respectively, in the high resolution spectral windows (∆ν = 0.123 kHz, corresponding to about
0.15 km s [−][1] and 0.17 km s [−][1], for CH 3 OH and SiO, respectively).
The data were calibrated using the ALMA calibration pipeline
within CASA [2] with an additional calibration routine to correct
for the Tsys normalization issue [3] . After aligning data from different setups, phase-only self-calibration was performed on the
continuum, generated using a careful manual detection of linefree channels. The continuum model was then subtracted from
the visibilities prior to imaging the line data and a continuum
image was then created in CASA. The resulting continuumsubtracted line cube was created combining the two available
ALMA-12m configurations (i.e. C43-3, C43-6), to have the best
angular resolution, and imaged with the IRAM-GILDAS [4] package, using a 0.56 robust parameter [5] with a resulting synthesized


2 `[https://casa.nrao.edu](https://casa.nrao.edu)`
3 `[https://help.almascience.org/kb/articles/what-are-t](https://help.almascience.org/kb/articles/what-are-the-amplitude-calibration-issues-caused-by-alma-s-normalization-strategy)`
```
he-amplitude-calibration-issues-caused-by-alma-s-nor
malization-strategy
```

4 `[https://www.iram.fr/IRAMFR/GILDAS/](https://www.iram.fr/IRAMFR/GILDAS/)`
5 https://www.iram.fr/IRAMFR/GILDAS/doc/pdf/map.pdf


Article number, page 2 of 11



beam of 0 [′′] . 18 × 0 [′′] . 11 (-13 [◦] ) and 0 [′′] . 14 × 0 [′′] . 096 (-21 [◦] ) for the
SiO and CH 3 OH spectral windows, respectively. The cubes were
then primary beam corrected. We estimate the absolute flux error
of 15% that includes the calibration uncertainty and an additional
error for the spectra baseline determination.


**3.** **The kinematical structure of the IRAS 4A inner**

**regions**


Figure 1 shows the dust continuum emission at 1.3 mm of NGC
1333 IRAS 4A overlaid with the SiO 5-4 low velocity emission
(in the ranges (−6, −2) and (+2, +6) km s [−][1] with respect to the
v sys ; v sys = 6.8 km s [−][1] ; Choi 2001), with a zoom-in on SiO and
CH 3 OH emission lines (listed in Table 1) at < 1 [′′] (<300 au)
scale around IRAS 4A2. At large scale (above 1 [′′] from IRAS
4A2, Figure A.1), both SiO and CH 3 OH trace blue-shifted emission in the south (up to -33 km s [−][1] with respect to v sys ), and
red-shifted emission in the north (up to +35 km s [−][1] with respect to v sys ). However, at small scales the kinematics is different: below 300 au, both SiO and CH 3 OH emit in the velocity
ranges (−6, −2) km s [−][1] and (+2, +6) km s [−][1] with respect to v sys
(see also channel maps in Figure B.1, and B.2) with a velocity gradient inverted with respect to the large scale. Specifically,
CH 3 OH shows blue-shifted emission towards the northeast and
red-shifted emission towards the southwest, that peaks at ∼ 0 [′′] . 15
from IRAS 4A2 and extends out to ∼ 0 [′′] . 3 . The SiO emission has
an S-shape structure that follows the continuum emission from
the dust grains in the circumstellar envelope. In the inner 300 au,
it shows both blue- and red-shifted emission on both sides. However, in the inner 0 [′′] . 3 (∼90 au) the SiO distribution resembles
that of methanol, with an inverted velocity gradient with respect
to the large scale emission. At larger distances, i.e. from 0 [′′] . 3 to
1 [′′], the southern lobe is only blue-shifted (in agreement with the
large scale), while the northern lobe is mainly red-shifted with
a tiny blue-shifted contamination (that dominates closer to the
v _sys_ ; at about −2 km s [−][1], Figure B.1). We also performed PV diagrams along the methanol and SiO PA and perpendicular to the
emission (see Figure D.1,D.2, D.3). The inversion of velocity is
clearly shown, but the PV diagrams are limited in spatial/angular
resolution to reveal any other kinematical structure.
Figure 2 shows the spectra extracted at the position of the
CH 3 OH red- and blue-shifted emission peaks (coordinate offsets
reported in Table 1). The two peaks were identified as the pixel
with the highest flux level in the integrated maps of CH 3 OH in
the (−6, −2) km s [−][1] and (+2, +6) km s [−][1] ranges (see Figure 1).
The CH 3 OH spectrum peaks at low velocity (∼±1.5 km s [−][1] with
respect to v sys ) and is likely dominated by the ice mantle sublimation region (i.e., the hot corino). The SiO spectrum, instead,
peaks at higher velocity (about ±7 km s [−][1] with respect to v sys )
and it is likely dominated by jet/outflow emission due to grain
sputtering/shattering. In the (−6, −2) km s [−][1] and (+2, +6) km s [−][1]
ranges the spectra of CH 3 OH and SiO overlap. In these ranges
we observe the inverted velocity gradient. We measured the intensity ratio CH 3 OH/SiO (Table 1), integrated on the (−6, −2)
km s [−][1] and (+2, +6) km s [−][1] ranges, and the corresponding abundance ratio, estimated assuming LTE (Local Thermodynamic
Equilibrium) optically thin emission and an excitation temperature of 100 K (typical for both hot corino and shocked gas), in the
red- and blue- shifted emission peaks of both SiO and CH 3 OH.
The emission peaks of SiO were identified, as for CH 3 OH, as the
pixel with the highest flux level in the integrated maps (Figure
1). We found that, in general, CH 3 OH is more abundant than SiO
by about two orders of magnitude. Additionally, the moment 0

De Simone et al.: FAUST XVI. A wide disk wind mapped by CH 3 OH and SiO in the inner 300 au of IRAS 4A2.


**Fig. 1.** _Upper left:_ Superposition of the 1.3 mm continuum (grey scale, up to 20% of maximum flux, with contours starting at 15σ _c_ with step of
20σ _c_, where σ _c_ = 8 × 10 [−][2] mJy beam [−][1] ) with SiO red- and blue-shifted emission (salmon and cyan contours, respectively, from 3σ with steps of
4σ, where σ = 2 mJy beam [−][1] km s [−][1] ). _Upper right:_ Zoom-in on IRAS 4A2. Superposition of the red- and blue-shifted emission of SiO (salmon
and cyan color shaded contours) and CH 3 OH (red and blue contours). Contours starts at 3σ with steps of 4σ for SiO and 5σ for CH 3 OH (σ = 2
mJy beam [−][1] km s [−][1] ). Beams are shown in the lower corners. _Lower panels:_ Blue- and red-shifted emission for SiO and CH 3 OH shown separately.
The beams are shown in the inner corner. In all panels, white (and black) stars mark the protostars (IRAS 4A1 and IRAS 4A2). The red- and
blue-shifted emissions are integrated between +2 and +6 km s [−][1], and between −6 and −2 km s [−][1] with respect to the systemic velocity (v sys = +6.8
km s [−][1] ; Choi 2001), respectively. The moment 0 between -6 and 6 km s [−][1] for each species is shown in greyscale.



maps in Figure 1 show that methanol peaks closer to the source
than SiO in both blue and red ranges (by 0.1 [′′], less than a beam).
Even if unresolved, this spatial shift in the red-shifted component seems to be significant. This is supported by the fact that
the CH 3 OH/SiO integrated intensity and abundance ratio estimated by extracting the spectra at the SiO peak are both about a
factor 4 smaller than that estimated at the CH 3 OH peak (Table
1). Finally, in IRAS 4A2 De Simone et al. (2020) estimated an
H 2 density of about 2 × 10 [6] cm [−][3] in the inner 0 [′′] . 24. Using this
gas density, the abundances of CH 3 OH and SiO are ∼10 [−][6] and
∼10 [−][8], respectively.


In summary, the observed emission arises from three zones:
i) a very compact region (< 0 [′′] . 15, <50 au), at ±1.5 km s [−][1] with
respect to v sys, dominated by the hot corino emission and traced
mainly by methanol; ii) an intermediate region (0 [′′] . 15 − 0 [′′] . 5, 50–
150 au ), between 2 and 6 km s [−][1] with respect to v sys, traced by
both SiO and CH 3 OH that shows an inverted velocity gradient,
with respect to the large scale, whose origin is not clear; iii) an
extended region (> 0 [′′] . 5, > 150 au), above 7 km s [−][1] with respect
to the v sys, traced by SiO and dominated by the jet/outflow.



**4.** **On the origin of the inverse velocity gradient**


We now discuss the origin of the intermediate region in the inner
∼ 0 [′′] . 5 (∼150 au), where SiO and CH 3 OH show an observed inverse velocity gradient with respect to the large scale, and their
observed spatial and spectral shift. At this stage, it is important to highlight the formation mechanisms of these two species:
CH 3 OH is formed on the icy grain mantles via CO hydrogenation (e.g., Watanabe & Kouchi 2002; Rimola et al. 2014) and it
can be released into gas phase by either ice mantle sublimation or
by grain mantle sputtering in mild shocks in star forming regions
(e.g., Flower et al. 2010). On the contrary, SiO is formed via the
sputtering/shattering of the grain cores by strong shocks that release Si into the gas phase where it quickly oxygenates. It is estimated that up to ∼10% of Si or SiO can also be frozen into the
grain mantles, and therefore be released by grain mantle sputtering in mild shocks as CH 3 OH (e.g., Caselli et al. 1997; Schilke
et al. 1997; Gusdorf et al. 2008a,b; Guillet et al. 2011). Being
the two species aligned along the same Position Angle (PA), it
can be reasonable to think that they both come from from the
base of the wind launched from the protostellar disk. However,
CH 3 OH is more compact and could also probe the very inner


Article number, page 3 of 11

_A&A proofs:_ manuscript no. DeSimone_IRAS4A_diskwind


**Table** **1.** _Top:_ Spectral properties of CH 3 OH and SiO by Xu et al. (2008) and Müller et al. (2013), respectively, from the CDMS database
(Müller et al. 2005). _Bottom:_ Integrated Area in the blue (from 0.8 to 4.8 km s [−][1] ) and red (from 8.8 to 12.8 km s [−][1] ) velocity ranges from the
spectra extracted at the blue- and red-shifted peaks of CH 3 OH and SiO (see Figure 1 and 2) and corresponding column densities.

|Line|Transition Frequency E u log(A ul/s−1) gu Beam<br>[GHz] [K] ”×”(◦)|
|---|---|
|SiO<br>CH3OH|5-4<br>217.10498<br>31<br>-3.28<br>11<br>0.18 × 0.11(−13)<br>51,4 −41,3 A<br>243.91579<br>50<br>-4.22<br>44<br>0.14 × 0.096(−21)|
||Velocity-integrated intensity (<br>R<br>_I_∆v)_a_ & Column Density (Ncol)_b_|
|Position<br>Ofset_c_|CH3OH Red Peak<br>SiO Red Peak<br>CH3OH Blue Peak<br>SiO Blue Peak<br>(−1′′.35, +1”)<br>(−1′′.27, +0′′.93)<br>(−1′′.41, +1′′.13)<br>(−1′′.44, +1′′.19)|
||R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol<br>[K km s−1]<br>[cm−2]<br>[K km s−1]<br>[cm−2]<br>[K km s−1]<br>[cm−2]<br>[K km s−1]<br>[cm−2]|
|SiO<br>CH3OH|44(6)<br>8.7(1.1)×1013<br>54(8)<br>10(2)×1013<br>51(8)<br>10(2)×1013<br>43(6)<br>8.5(1.1)×1013<br>118(17)<br>37(5)×1015<br>37(6)<br>12(2)×1015<br>67(10)<br>21(3)×1015<br>52(8)<br>16(2)×1015|
||R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol<br>R<br>_I_∆v<br>Ncol|
|CH3OH/SiO|2.7(0.8)<br>420(110)<br>0.7(0.2)<br>120(40)<br>1.3(0.4)<br>210(70)<br>1.2(0.3)<br>190(50)|



_a_ Errors on the integrated intensity include 15% of calibration error and spectral baseline determination.
_b_ N col has been computed assuming an _T_ _ex_ of 100 K. A difference in _T_ _ex_ of 50 K translates into about a factor 2 in N col .
_c_ with respect to the map phase center.



**Fig. 2.** SiO (magenta) and CH 3 OH (black) spectra extracted at the blueand red-shifted peaks of CH 3 OH (offset with respect to the map phase
center are in the upper right corner). The green dashed vertical line
marks the v _sys_ (∼6.8 km s [−][1] Choi 2001). The 3σ level is reported in
black (CH 3 OH) and magenta (SiO) dashed horizontal lines.


part of the envelope where it is released by thermal evaporation.
We investigate the following three possibilities:


_Rotating disk/inner envelope:_ The blue- and red- shifted emission of CH 3 OH might indicate rotation in a disk-like structure
and/or in the inner envelope, where the ice sublimation dominates the chemistry. However, i) the PA (∼−30 [◦] ) of the velocity
gradient differs of ∼ 30 [◦] from the perpendicular direction of the
jet/outflow direction at large scale (above 300 au), as expected
for disk emission. Indeed, the jet/outflow direction is estimated


Article number, page 4 of 11



to have a PA of 25 [◦] −30 [◦] (see figure A.1, and Choi 2005; Santangelo et al. 2015; De Simone et al. 2020, Chahine et al. submit
∼
ted); ii) unfortunately, the present spatial resolution ( 50 au) is
not enough to assess whether the signature of a rotating/infalling
envelope is present in CH 3 OH and/or SiO (see Figure D.2 in appendix); iii) CH 3 OH and SiO are aligned on the same PA, and
both trace the inverted velocity gradient, but only CH 3 OH is a
known disk tracer.

Indeed, while methanol emission can be explained by ice
sublimation, for SiO is not so straightforward. At the methanol
emission site (extending out to 90 au, 0 [′′] . 3, and peaking at 45
au, 0 [′′] . 15, from the protostar) the dust temperature is 65–90 K
, comparable to the CH 3 OH sublimation one (60–130 K) (see
computations in Appendix C). On the other hand, SiO is usually
associated to jet activity, i.e., where the Si is released by grain
sputtering in shocks or entrained in a wind originated inside the
dust sublimation radius (e.g., Cabrit et al. 2007; Gusdorf et al.
2008b; Hirota et al. 2017; Tabone et al. 2020; López-Vázquez
et al. 2024). Even if there is 10% of SiO trapped in the ice mantles (e.g., Gusdorf et al. 2008a,b; Guillet et al. 2011), it is not
clear if this would be released with the ice once sublimated due
to SiO reactivity with water or due to other processes (see details in Appendix C). Alternatively, the two species could be released by grain mantle sputtering at the infalling envelope-disk
interface, where slow shocks (< 5-10 km s [−][1] ) occur (e.g., Sakai
et al. 2014). However, it is unclear if this slow shocks can sputter
enough SiO, and if so, the emission would follow the disk kinematics, for which we do not have strong evidence (see above).
In summary, the observed methanol emission could be the
result of the ice mantle sublimation in the inner rotating envelope/disk, while a fast shock (>10 km s [−][1] ) needs to occur to
sputter the dust grains so to explain the observed SiO abundance.


_Jet/Outflow_ _precessing_ _and/or_ _on_ _the_ _plane_ _of_ _the_ _sky:_ Another possibility is that CH 3 OH and SiO have a non-thermal origin linked to shocks along the jet. The inclination of the IRAS
4A2 jet is yet highly uncertain Yıldız et al. (45 [◦] -88 [◦] 2012); Choi

De Simone et al.: FAUST XVI. A wide disk wind mapped by CH 3 OH and SiO in the inner 300 au of IRAS 4A2.


(45 [◦] -88 [◦] 2005); Marvel et al. (45 [◦] -88 [◦] 2008); Koumpia et al.
(45 [◦] -88 [◦] 2016). If it is close to the plane of the sky one expects
to observe blue- and red-shifted emission in both lobes and along
the whole jet length, not only in the inner 300 au (see e.g., Cabrit
& Bertout 1990; Podio et al. 2021). On the other hand, if the jet
precesses and crosses the plane of the sky it may create a knot
with opposite velocity with respect to previous ejection events.
However, if this was the case we would expect to see an alternation of blue- and red- shifted emission with a periodic pattern
and also at larger scales. Moreover, this scenario has been excluded by Chuang et al. (2021) based on a 3D precession model.
Indeed, this could explain the S-shape structure of the IRAS 4A
outflows traced in SO at large scale, but not the inversion of the
velocity gradient at small scales.



_Wide-angle wind:_ Figure 3 shows a simplistic sketch that summarize our interpretation of the observed spatial-kinematical distribution. The sketch shows the base of a wide and inclined disk
wind that crosses the plane of the sky and shows an inversion
in velocity at 300 au with respect to the large-scale jet/outflow.
The disk wind is plausibly magnetically driven and it is expected
to reach the maximum radius at the Alfvén surface and to recollimate beyond that (Tabone et al. 2020). The prototypical disk
wind in HH212 has been detected at heights below ∼200 au
(Frank et al. 2014; Tabone et al. 2017; Lee et al. 2021a; Nazari
et al. 2024), consistent with our findings. Given the covered velocity ranges between 2 and 6 km s [−][1], the inclination of the gas
crossing the plane of the sky has to be > 55 [◦] with respect to the
line of sight. This is needed to have a reasonable flow velocity
(> 10 km s [−][1] ) to sputter grain mantles and cores so to release
both CH 3 OH and SiO (see Appendix C).
Among the three scenarios, we favour the last one as it explains the inverse velocity gradient, the spatial alignment between SiO and CH 3 OH, and also the observed SiO and CH 3 OH
spectra (where the emission close to v sys is hot corino dominated
and beyond 7 km s [−][1] is jet/outflow dominated). For the first time,
we detect and identify a disk wind candidate toward the IRAS
4A Class 0 protostar traced in SiO and CH 3 OH. This increases
the number of disk wind tracers, complementing the typical SO
(e.g., Tabone et al. 2017; Codella et al. 2018) and supporting
the recently discovered CH 3 OH (Nazari et al. 2024), and gives
important constraints (velocity, inclination, and opening angles)
for disk wind theories. It is important to notice that the emission
of SiO can also be the result of the interaction of the jet with
the disk wind giving rise to an unresolved shocked shell (see
e.g., Lee et al. 2022b), or a disk wind rotation (e.g., Lee et al.
2022b). In this way, SiO can be considered as an indirect tracer.
However, to explain the observed low velocities, the jet/wind inclination needs to be quite high (above 80 [◦] with respect to the
line of sight; see Appendix C). Anyways, observations down to
at least 10 au would be needed to test this scenario.


**5.** **Conclusions**


This Letter presents FAUST observations with 50 au resolution
of IRAS 4A2 as mapped in SiO and CH 3 OH. The high spatial
and spectral resolution observation of FAUST have been crucial
to study the interplay between the disk, the envelope and the outflowing gas. The unique combination of kinematics and chemistry allowed us to disentangle the emission at very small scales
(50 au) using the chemical formation pathway of each species
to retrieve the physical mechanisms at play. The emission below
300 au arises from three zones: i) a very compact region (< 0 [′′] . 1,



**Fig.** **3.** Simplistic sketch (not in scale) of the proposed scenario: The
large scale jet is quite inclined (60 [◦] in the example), and it has a wide
outflowing shocking gas that crosses the plane of the sky. The redshifted blue-shifted emission are represented by red and blue colors respectively. The gray-shadowed box highlight the view of the projected
emission on the plane of the sky that we actually observe.


50 au), at ±1.5 km s [−][1] with respect to v sys, dominated by the ice
mantle sublimation zone and traced by methanol; ii) an intermediate region (0 [′′] . 1 − 0 [′′] . 5, 50-150 au), between 2 and 6 km s [−][1]
with respect to v sys, traced by both SiO and CH 3 OH that shows
an inverted velocity gradient with respect to the large scale, with
unknown origin; iii) an extended region (> 0 [′′] . 5, 150 au), above
7 km s [−][1] with respect to v sys, traced by SiO and dominated by
the outflow. We propose that CH 3 OH and SiO in the intermediate region probe the base of a rotating wide-angle disk wind.
The material accelerated in the wind crosses the plane of the sky,
giving rise to the observed inverted velocity gradient, and sputter
the grains releasing both species. For the first time we observe
the IRAS 4A disk wind traced by, SiO and CH 3 OH, new tracers
beyond the known SO. Finally, we emphasise that observations
down to 10 au will be essential to reveal the presence and the
possible contribution of the unresolved rotating disk.


_Acknowledgements_ : We warmly acknowledge Dr. J. Enrique Romero for the fruitful discussion on the binding energies and the Si, SiO insights, and Dr. F. Bacciotti on disk winds.
This project has received funding from the Marie SklodowskaCurie for the project “Astro-Chemical Origins” (ACO), grant
agreement No 811312, and within the European Union’s Horizon 2020 research and innovation program from the European Research Council (ERC) for the projects “The Dawn
of Organic Chemistry” (DOC), grant agreement No 741002.
Part of the data deconvolution and analysis was performed
using the GRICAD infrastructure ( `[https://gricad.uni](https://gricad.univ-grenoble-alpes.fr)`
`[v- grenoble- alpes.fr](https://gricad.univ-grenoble-alpes.fr)` ). ClCo, LP, and GS acknowledge the PRIN-MUR 2020 BEYOND-2p (Astrochemistry be

Article number, page 5 of 11

_A&A proofs:_ manuscript no. DeSimone_IRAS4A_diskwind


yond the second period elements, Prot. 2020AFB3FX), the
PRIN MUR 2022 FOSSILS (Chemical origins: linking the
fossil composition of the Solar System with the chemistry
of protoplanetary disks, Prot. 2022JC2Y93), the project ASIAstrobiologia 2023 MIGLIORA (Modeling Chemical Complexity, F83C23000800005), the INAF-GO 2023 fundings PROTOSKA (Exploiting ALMA data to study planet forming disks:
preparing the advent of SKA, C13C23000770005), the INAF
Mini-Grant 2022 “Chemical Origins” (PI: L. Podio), and INAFMinigrant 2023 TRIESTE (“TRacing the chemIcal hEritage of
our originS: from proTostars to planEts”; PI: G. Sabatini). D.J.
is supported by NRC Canada and by an NSERC Discovery
Grant. L.L. acknowledges the support of DGAPA PAPIIT grants
IN108324 and IN112820 and CONACyT-CF grant 263356”.
M.B. acknowledges support from the European Research Council (ERC) Advanced Grant MOPPEX 833460. N.C acknoeledges
funding from the European Research Council (ERC) under
the European Union Horizon Europe research and innovation program (grant agreement No. 101042275, project StellarMADE). This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.01205.L (PI: S. Yamamoto). ALMA
is a partnership of the ESO (representing its member states), the
NSF (USA) and NINS (Japan), together with the NRC (Canada)
and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the
ESO, the AUI/NRAO, and the NAOJ.


Article number, page 6 of 11

De Simone et al.: FAUST XVI. A wide disk wind mapped by CH 3 OH and SiO in the inner 300 au of IRAS 4A2.


**Appendix C:** **SiO and CH** **3** **OH: sputtering or**
**sublimation?**


Sublimation: In order to have the desorption of a species from
the ice mantle, the dust needs to reach the species sublimation
temperature. Considering species that are not strongly associated
to each other (e.g, CH 3 OH adsorbed on a surface made mostly
by water or CO) the first order solution for the desorption rate
(k des ) is:


k des = ν des e [−][BE[K]][/][T], (C.1)


where BE is the binding energy (namely, the strength of a species
to remain attached to the surface) in Kelvin, and ν _des_ is the preexponential factor which depends on the species and the surface
(Minissale et al. 2022; Ferrero et al. 2022). Even if the BE is
given most of the time as a single value, recent experiments and
theoretical computations have shown that for each species there
can be a distribution of BEs (Ferrero et al. 2020; Bovolenta et al.
2020; Minissale et al. 2022; Tinacci et al. 2022, 2023). This is
because BE can change based on the site and orientation of the
species with respect to the molecules on the substrate.
To retrieve the sublimation temperature from the desorption
rate (i.e., the BE value) we solve Equation C.1 taking the halflife time t 1/2 as the characteristic time of the desorption, in first
approximation, as (Ceccarelli et al. 2023):



**Fig.** **A.1.** Large scale view of the ALMA FAUST SiO emission. Each
velocity range corresponds to a specific color shown in contours starting
at 4σ with steps of 2σ, where σ= 3, 3.5, 6 mJy beam [−][1] km s [−][1] for the
LV (low velocity: red and cyan), HV (high velocity: orange and blue),
EHV (extremely high velocity: pink and green) range, respectively. In
background, in grey scale, a range around the v sys is shown (4.9–8.5 km
s [−][1] ). The synthesised beam is depicted in the lower left corner, and the
primary beam is shown as a dashed grey circle.


**Appendix A:** **Overview of FAUST SiO at large scale**


Figure A.1 shows the large scale SiO emission of the IRAS 4A
system integrated in different velocity ranges. This provides a
general overview of the whole range of velocities overall involved, for the sake of completeness. Please note that the SiO
emission is actually going beyond the spectral window bandwidth, therefore beyond the upper velocity range value reported
in the figure. It is important to note for the present work that the
northern part is red-shifted and the southern part is blue-shifted.
The study of the large scale structure is out of the scope of this
letter and presented in Chahine et al. (submitted).


**Appendix B:** **Channel maps**


Figure B.1 and B.2 show the channel maps of SiO and CH 3 OH,
respectively. The channels are binned to 1 km s [−][1], for the sake
of clarity, and are zoomed in the inner 300 au of the IRAS 4A2
protostar. The inverted velocity gradient region is present only in
the (−6, −2) and (2, 6) km s [−][1] ranges.



ln(2)

t 1/2 = [ln] k des [(][2][)] = ν des e [−][BE[K]][/][T] [.] (C.2)


Therefore,


BE[K]
T sub = (C.3)
ln(t 1/2 ) + ln(ν des / ln(2)) [.]


Regarding methanol, theoretical predictions by Ferrero et al.
(2020) indicate a BE range of (3770–8618) K, while the preexponential factor ν des is 3.2 × 10 [17] s [−][1] (Minissale et al. 2022).
The BE given by Minissale et al. (2022) is 6621 K, consistent
with the range found by Ferrero et al. (2020). Using the CH 3 OH
BE range and ν _des_ stated above, and assuming that the grain mantles have been warmed up for a timescale of ∼ 10 [4] yr [6], T sub =
60 − 130 K.
We can now estimate the dust temperature at a certain distance from the protostar. When the dust is optically thin, the dust
temperature profile heated by a central source with L ⋆ luminosity, can be approximated by the following equation (Ceccarelli
et al. 2000):



The bolometric luminosity (L bol ) of IRAS 4A1 and IRAS
4A2 is not measured singularly due to the lack of angular resolution observation at infrared wavelengths. The total bolometric
luminosity of the IRAS 4A1+4A2 system is estimated to be 9 L ⊙
(Kristensen et al. 2012; Karska et al. 2013). The blue- and redshifted emission peak of methanol are separated by about 0 [′′] . 15
(about 45 au) and their emission extend up to 0 [′′] . 26 away (about
80 au). If we consider for 4A2 conservatively a bolometric luminosity of 4.5 L ⊙ (half of the total luminosity), the temperature at
80 au from the protostars is about 65 K, while at 45 au is about
90 K.


6 Please note that assuming 1 Myr timescale, _T_ _sub_ could be lower by
about 10 K.


Article number, page 7 of 11



T dust [K] = 75K L ⋆
� 27L ⊙



� 1/4 � 150aur



−1/2
� . (C.4)

_A&A proofs:_ manuscript no. DeSimone_IRAS4A_diskwind


**Fig. B.1.** ALMA FAUST SiO velocity channel maps. Each panel corresponds to a 1 km s [−][1] increment from the systemic velocity (v sys = 6.8 km
s [−][1] ; Choi 2001). The black star marks the position of the IRAS 4A2 protostar. The SiO beam is reported in the lower left corner of the v sys panel
(shown in color scale). First contours and steps are 3σ (σ = 1 mJy beam [−][1] ).



Regarding SiO, it could be possible to investigate if sublimation can play a role, given that it is thought that about 10%
of SiO can be already formed and locked into the ice mantles of
the dust grains (see e.g., Gusdorf et al. 2008a,b; Guillet et al.
2011). The binding energy of SiO is reported to be about 3500 K
(Hasegawa & Herbst 1993), that translate into a sublimation temperature of about 50 K. Therefore, in theory, at 0 [′′] . 2 (60 au) away
from the protostar (at SiO emission peak), the dust temperature
could be enough to sublimate SiO. If we consider the computed
CH 3 OH/SiO column density ratio (see Table 1), we find that the
abundances of SiO should be two order of magnitude lower than
methanol. In IRAS 4A2, De Simone et al. (2020) estimated a gas
density of about 2 × 10 [6] cm [−][3] in the inner 0 [′′] . 24. Using this gas
density, the abundances should be about 10 [−][6] for CH 3 OH and
10 [−][8] for SiO (similar to the typical values in shocked regions;
e.g., Cabrit et al. 2007; Gusdorf et al. 2008b; Taquet et al. 2020).
Considering a 10% of elemental silicon frozen into SiO on the
mantle, we could have an abundance of frozen SiO or Si on the
icy mantle of about 10 [−][7] − 10 [−][8] (see Figure 4 in Ceccarelli et al.
2018; Lodders 2019). Therefore, we could, in principle, explain
the observed abundance. However, SiO and Si could be highly
reactive with the water molecules in the ice preventing the sublimation of pure SiO and Si into the gas phase. New quantum
chemical computations are ongoing to obtain i) updated values
for the SiO binding energy taking into account orientation and
ice morphology (Gelli et al. in prep.), and ii) evaluating how
much reactive the SiO and Si are on interstellar ices (EnriqueRomero et al. private comm.).


Article number, page 8 of 11



Sputtering: SiO is the best known and most studied shock tracers since more than two decades. Several shock models have predicted that the SiO abundance is highly enhanced in high velocity shocks (above 25 km s [−][1] ). Indeed at these velocities the silicon is liberated from the refractory cores of the grains thanks to
sputtering and/or shattering, and goes into the gas phase where
it quickly oxidizes (e.g., Flower & Pineau des Forets 1994;
Caselli et al. 1997; Schilke et al. 1997). At lower velocities, some
species (including Si, directly SiO, and also CH 3 OH) that were
previously frozen on to the grain mantles can still be released
into the gas phase by the sputtering of the icy mantles itself
(Jiménez-Serra et al. 2008; Gusdorf et al. 2008b; Guillet et al.
2011; Lesaffre et al. 2013; Nguyen-Lu’o’ng et al. 2013). The
above models predict that, to liberate Si or SiO from the frozen
mantles, a minimum velocity of about 10 km s [−][1] is needed [7] .
From our observations, the small scale inverse velocity component has a velocity range between 2 and 6 km s [−][1] (see Figure
1, B.1, B.2 ). This represent the line-of-sight velocity component. To retrieve the radial velocity, that would be the responsible for the sputtering, we need information on the jet/outflow
inclination. The IRAS 4A jet inclination is not very well known
yet. Indeed, due to the large extent of the outflows/jets and the
high line-of-sight velocities Yıldız et al. (2012) suggested an inclination of 45 − 60 [◦] with respect to the line of sight. On the
other hand, Choi (2005), Marvel et al. (2008), and Koumpia et al.


7 Please note that these values critically depend on the assumed frozenSiO sputtering threshold energy (see discussion in De Simone et al.
2022b; Flower & Pineau des Forets 1994)

De Simone et al.: FAUST XVI. A wide disk wind mapped by CH 3 OH and SiO in the inner 300 au of IRAS 4A2.


**Fig. B.2.** ALMA FAUST CH 3 OH velocity channel maps. Each panel corresponds to a 1 km s [−][1] increment from the systemic velocity (v sys = 6.8
km s [−][1] ; Choi 2001). The black star marks the position of the IRAS 4A2 protostar. The CH 3 OH beam is reported in the lower left corner of the v sys
panel (shown in color scale). First contours and steps are 3σ (σ = 1.1 mJy beam [−][1] ).


(2016) suggested larger inclination of about 79 [◦], 88 [◦] and 70 [◦],
respectively. However, we can give a constrain on the inclination of the emission at this scale (not necessarily of the jet, see
discussion in Section 4) based on the minimum velocity needed
to have sputtering, so to explain the presence of both SiO and
CH 3 OH. Considering that the observed line-of-sight velocity is
2, 6 km s [−][1] with respect to the v sys, and the velocity required for
sputtering a reasonable amount of SiO and CH 3 OH (see above),
we need an inclination with respect to the line of sight above 55 [◦]
for a radial velocity of 10 km s [−][1], and above 80 [◦] for 35 km s [−][1] .


**Appendix D:** **PV Diagrams**



We selected eight regions 0 [′′] . 1 wide (shown in Figure D.1) where
to extract the PV diagrams: one of 3 [′′] . 6 length passing through
the direction identified by the red- and blue-shifted emission
peak of methanol in the inner 0 [′′] . 5 (PA∼30 [◦] ) and the other seven
are perpendicular to that, each separated by 0 [′′] . 3, and of 1 [′′] . 6
length. The PV diagrams extracted from these regions for SiO
are shown in Figure D.3, while the one extracted from the parallel slice and the path following the SiO structures (shown in red
and white, respectively, in Figure D.1) for both CH 3 OH and SiO
are shown in Figure D.2). It is possible to notice, as also visible
in the channel maps (Figure B.1), that the SiO PV diagram on the
path 0 [′′] . 9 and 0 [′′] . 6 south of IRAS 4A2 are blue-shifted while 0 [′′] . 3
south a red-shifted component appears together with the blueshifted ones. In the north paths the situation is similar with red
and blue-shifted inverted. The emission is confined around ±0 [′′] . 3
of the selected axis, and does not show any peculiar structure.



**Fig.** **D.1.** Regions (colored) where PV diagrams have been extracted.
For reference, the moment 0 of SiO integrated over the whole spectral
window is in grey scale. IRAS 4A2 is marked by the white star.


Only the emission along the path 0 [′′] . 9 south of 4A2, that correspond to the cavity seen in the southern outflow (see Figure 1),
is resolved and shows higher velocities with respect to the small
scale structures (below 0 [′′] . 5). In Figure D.2, the emission along
the slice parallel to CH 3 OH and SiO PA (red in Figure D.1) of
SiO shows a more evident structure. It is noticeable the inversion of velocity gradient, with red emission in the south and blue
emission in the north, below 0 [′′] . 5 from 4A2. The knot at −0 [′′] . 5


Article number, page 9 of 11

_A&A proofs:_ manuscript no. DeSimone_IRAS4A_diskwind


**Fig.** **D.2.** _Left:_ PV Diagram extracted over the path of ∼ 7 [′′] length that follows the SiO structures (white in Figure D.1). The SiO emission is
shown in color scale. Green and white contours at (3,5,10) σ are for CH 3 OH (σ ∼ 2 mJy beam [−][1] ) and SiO (σ _m_ ∼1.6 mJy beam [−][1] ), respectively.
_Right_ PV Diagram extracted over the region of 3 [′′] length passing through methanol and SiO PA in the inner 0 [′′] . 5 (shown in red in the left panel).
The methanol emission is shown in color scale with green contours (at 3,5,10 σ _m_ with σ _m_ ∼3 mJy beam [−][1] ). The SiO emission is shown in white
contours at (3,5,10, 20) σ _s_ with σ _s_ ∼1.5 mJy beam [−][1] . In both panels, the vertical and horizontal dashed lines represent the v sys (∼6.8 km s [−][1] ; Choi
2001), and the 0 [′′] offset (on the 4A2 protostar), respectively.


**Fig.** **D.3.** SiO PV diagrams extracted at the region shown in Figure D.1 and opportunely labelled at the top of each plot. The contours are at
(3,5,10, 20) σ _s_ with σ _s_ ∼1.5 mJy beam [−][1] . The vertical and horizontal dashed lines represent the v sys (∼6.8 km s [−][1] ; Choi 2001), and the 0 [′′] offset
(on the 4A2 protostar), respectively.



can be interpreted as the first knot associated to the outflow. Indeed, the left panel of the figure shows the PV diagram extracted
from a region that follows the SiO structure in the moment 0
(white line in Figure D.1). Here two knots are at ∼ 0 [′′] . 5 and ∼ 1 [′′]
with 8.5 km s [−][1] and 12 km s [−][1] respectively and indicate knots
in the outflow. Comparing SiO and CH 3 OH in Figure D.2 right),
we can see that CH 3 OH is elongated following the SiO emission with inverted velocity gradient. However, we are limited by
spatial resolution to reveal any other kinematical structure.


Article number, page 10 of 11



**References**


Andre, P., Ward-Thompson, D., & Barsony, M. 2000, PPIV, 59
Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in Protostars and Planets V, ed.
B. Reipurth, D. Jewitt, & K. Keil, 245
Belloche, A., Maury, A. J., Maret, S., et al. 2020, arXiv:2002.00592 [astro-ph],
arXiv: 2002.00592

Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2023, Faraday Discussions,
245, 164
Blandford, R. D. & Payne, D. G. 1982, MNRAS, 199, 883
Bouvier, M., Ceccarelli, C., López-Sepulcre, A., et al. 2022, ApJ, 929, 10
Bovolenta, G., Bovino, S., Vöhringer-Martinez, E., et al. 2020, Molecular Astrophysics, 21, 100095
Cabrit, S. & Bertout, C. 1990, ApJ, 348, 530

De Simone et al.: FAUST XVI. A wide disk wind mapped by CH 3 OH and SiO in the inner 300 au of IRAS 4A2.



Cabrit, S., Codella, C., Gueth, F., et al. 2007, A&A, 468, L29
Caselli, P., Hartquist, T. W., & Havnes, O. 1997, A&A, 322, 296
Ceccarelli, C. 2004, in ASPC, Vol. 323, 195
Ceccarelli, C., Caselli, P., Fontani, F., et al. 2017, ApJ, 850, 176
Ceccarelli, C., Castets, A., Caux, E., et al. 2000, A&A, 355, 1129
Ceccarelli, C., Codella, C., Balucani, N., et al. 2023, in Astronomical Society
of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed.
S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 379
Ceccarelli, C., Viti, S., Balucani, N., & Taquet, V. 2018, MNRAS, 476, 1371
Ching, T.-C., Lai, S.-P., Zhang, Q., et al. 2016, ApJ, 819, 159
Choi, M. 2001, ApJ, 553, 219
Choi, M. 2005, ApJ, 630, 976
Choi, M., Kang, M., Tatematsu, K., Lee, J.-E., & Park, G. 2011, Publications of
the Astronomical Society of Japan, 63, 1281
Chuang, C.-Y., Aso, Y., Hirano, N., Hirano, S., & Machida, M. N. 2021, ApJ,
916, 82
Codella, C., Bianchi, E., Tabone, B., et al. 2018, A&A, 617, A10
Codella, C., Ceccarelli, C., Chandler, C., et al. 2021, Frontiers in Astronomy and
Space Sciences, 8, 227
De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3
De Simone, M., Ceccarelli, C., Codella, C., et al. 2022a, ApJ, 935, L14
De Simone, M., Codella, C., Ceccarelli, C., et al. 2022b, MNRAS, 512, 5214
De Simone, M., Codella, C., Ceccarelli, C., et al. 2020, A&A, 640, A75
De Simone, M., Codella, C., Testi, L., et al. 2017, A&A, 599, A121
de Valon, A., Dougados, C., Cabrit, S., et al. 2020, A&A, 634, L12
Ferrero, S., Grieco, F., Ibrahim Mohamed, A. S., et al. 2022, MNRAS, 516, 2586
Ferrero, S., Zamirri, L., Ceccarelli, C., et al. 2020, ApJ, 904, 11
Flower, D. R. & Pineau des Forets, G. 1994, MNRAS, 268, 724
Flower, D. R., Pineau des Forêts, G., & Rabli, D. 2010, MNRAS, 409, 29
Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed.
H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451–474
Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5
Guerra-Alvarado, O. M., van der Marel, N., Di Francesco, J., et al. 2023, arXiv
e-prints, arXiv:2310.11999
Guillet, V., Pineau Des Forêts, G., & Jones, A. P. 2011, A&A, 527, A123
Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau Des Forêts, G. 2008a, A&A,
482, 809
Gusdorf, A., Pineau Des Forêts, G., Cabrit, S., & Flower, D. R. 2008b, A&A,
490, 695
Hasegawa, T. I. & Herbst, E. 1993, MNRAS, 261, 83
Herbst, E. & Van Dishoeck, E. 2009, ARA&A, 47, 427
Hirota, T., Machida, M. N., Matsushita, Y., et al. 2017, Nature Astronomy, 1,
0146
Jiménez-Serra, I., Caselli, P., Martín-Pintado, J., & Hartquist, T. W. 2008, A&A,
482, 549
Karska, A., Herczeg, G. J., van Dishoeck, E. F., et al. 2013, A&A, 552, A141
Ko, C.-L., Liu, H. B., Lai, S.-P., et al. 2020, ApJ, 889, 172
Konigl, A. & Pudritz, R. E. 2000, in Protostars and Planets IV, ed. V. Mannings,
A. P. Boss, & S. S. Russell, 759
Koumpia, E., van der Tak, F. F. S., Kwon, W., et al. 2016, A&A, 595, A51
Kristensen, L. E., van Dishoeck, E. F., Bergin, E. A., et al. 2012, A&A, 542, A8
Lee, C.-F., Codella, C., Ceccarelli, C., & López-Sepulcre, A. 2022a, ApJ, 937,
10
Lee, C.-F., Li, Z.-Y., Shang, H., & Hirano, N. 2022b, ApJ, 927, L27
Lee, C.-F., Tabone, B., Cabrit, S., et al. 2021a, ApJ, 907, L41
Lee, Y.-H., Johnstone, D., Lee, J.-E., et al. 2021b, ApJ, 920, 119
Lefloch, B., Castets, A., Cernicharo, J., & Loinard, L. 1998, ApJ, 504, L109
Lesaffre, P., Pineau des Forêts, G., Godard, B., et al. 2013, A&A, 550, A106
Li, J. I.-H., Liu, H. B., Hasegawa, Y., & Hirano, N. 2017, ApJ, 840, 72
Lodders, K. 2019, arXiv e-prints, arXiv:1912.00844
Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477
López-Vázquez, J. A., Lee, C.-F., Fernández-López, M., et al. 2024, ApJ, 962,
28
Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120
López-Sepulcre, A., Sakai, N., Neri, R., et al. 2017, A&A, 606, A121
Mairs, S., Lee, S., Johnstone, D., et al. 2024, arXiv e-prints, arXiv:2401.03549
Marvel, K. B., Wilking, B. A., Claussen, M. J., & Wootten, A. 2008, ApJ, 685,
285
Maureira, M. J., Gong, M., Pineda, J. E., et al. 2022, ApJ, 941, L23
Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76
Minissale, M., Aikawa, Y., Bergin, E., et al. 2022, ACS Earth and Space Chemistry, 6, 597
Müller, H. S. P., Spezzano, S., Bizzocchi, L., et al. 2013, Journal of Physical
Chemistry A, 117, 13843
Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Structure, 742, 215
Nazari, P., Tabone, B., Ahmadi, A., et al. 2024, arXiv e-prints, arXiv:2402.18631
Nguyen-Lu’o’ng, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88
Okoda, Y., Oya, Y., Imai, M., et al. 2022, ApJ, 935, 136



Pascucci, I., Cabrit, S., Edwards, S., et al. 2023, in Astronomical Society of the
Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 567
Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45
Ray, T., Dougados, C., Bacciotti, F., Eislöffel, J., & Chrysostomou, A. 2007, in
Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 231
Rimola, A., Taquet, V., Ugliengo, P., Balucani, N., & Ceccarelli, C. 2014, A&A,
572, A70
Sakai, N., Oya, Y., Sakai, T., et al. 2014, ApJ, 791, L38
Santangelo, G., Codella, C., Cabrit, S., et al. 2015, A&A, 584, A126
Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A,
321, 293
Shang, H., Li, Z. Y., & Hirano, N. 2007, in Protostars and Planets V, ed.
B. Reipurth, D. Jewitt, & K. Keil, 261
Shu, F., Najita, J., Ostriker, E., et al. 1994, ApJ, 429, 781
Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23
Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6
Tabone, B., Cabrit, S., Pineau des Forêts, G., et al. 2020, A&A, 640, A82
Taquet, V., Codella, C., de Simone, M., et al. 2020, arXiv e-prints, 2002,
arXiv:2002.05480
Tinacci, L., Germain, A., Pantaleone, S., et al. 2023, ApJ, 951, 32
Tinacci, L., Germain, A., Pantaleone, S., et al. 2022, ACE ECS, arXiv e-prints,
arXiv:2205.11954
Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2018, ApJ, 867, 43
Tsukamoto, Y., Maury, A., Commerçon, B., et al. 2022, arXiv e-prints,
arXiv:2209.13765
Watanabe, N. & Kouchi, A. 2002, ApJ, 571, L173
Xu, L.-H., Fisher, J., Lees, R. M., et al. 2008, Journal of Molecular Spectroscopy,
251, 305
Yang, Y.-L., Evans, II, N. J., Smith, A., et al. 2020, arXiv e-prints, 2002,
arXiv:2002.01478
Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2012, A&A, 542, A86
Zhang, Y., Higuchi, A. E., Sakai, N., et al. 2018, ApJ, 864, 76
Zucker, C., Schlafly, E. F., Speagle, J. S., et al. 2018, ApJ, 869, 83


1 ESO, Karl Schwarzchild Srt. 2, 85478 Garching bei München, Ger
many
e-mail: `marta.desimone@eso.org`
2 INAF, Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, 50125
Firenze, Italy
3 Univ. Grenoble Alpes, CNRS, IPAG, 38000 Grenoble, France
4 National Radio Astronomy Observatory 8, 1003 Lopezville Rd, Socorro, NM 87801, USA
5 Institut de Radioastronomie Millimétrique (IRAM), 300 rue de la
Piscine, 38406 Saint-Martin-d’Hères, France
6 Instituto de Radioastronomía y Astrofísica, Universidad Nacional
Autónoma de México, A.P. 3-72 (Xangari), 8701, Morelia, Mexico
7 Instituto de Astronomía, Universidad Nacional Autónoma de México, Ciudad Universitaria, A.P. 70-264, Cuidad de México 04510,
Mexico
8 The Institute of Physical and Chemical Research (RIKEN), 2-1, Hirosawa, Wako-shi, Saitama 351-0198, Japan
9 NRC Herzberg Astronomy and Astrophysics, 5071 West Saanich
Road, Victoria, BC, V9E 2E7, Canada
10 Department of Physics and Astronomy, University of Victoria, Victoria, BC, V8P 5C2, Canada
11 Department of Astronomy, The University of Tokyo, 7-3-1 Hongo,
Bunkyo-ku, Tokyo 113-0033, Japan
12 Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA
Leiden, The Netherlands
13 IRAP, Universitè de Toulouse, CNRS, CNES, UPS, Toulouse,
France
14 Excellence Cluster ORIGINS, Boltzmannstraße 2, 85748, Garching
bei Muünchen, – Germany
15 Center for Astrochemical Studies, Max-Planck-Institut für extraterrestrische Physik (MPE), Gießenbachstr. 1, D-85741 Garching, Ger
many
16 Centre for Frontier Science, Chiba University, 1-33 Yayoi-cho,
Inage-ku, Chiba 263-8522, Japan
17 Department of Chemistry, University of Virginia, McCormick Road,
PO Box 400319, Charlottesville, VA 22904, USA
18 The University of Texas at Austin, 2515 Speedway, Austin, Texas
78712, USA
19 The Graduate University for Advanced Studies (SOKENDAI),
Shonan Village, Hayama, Kanagawa 240-0193, Japan


8 The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.


Article number, page 11 of 11


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[1]",
  "value": "Explore the kinematics and chemical structure of the gas in the inner 300 au transition zone between the disk and outflowing material of the protostar NGC 1333 IRAS 4A2 using SiO and CH3OH.",
  "failed_quote": "We study the kinematics of the gas in the transition zone between a possible disk and the ouflowing material, and present, for the first time, a wide disk wind candidate for NGC 1333 IRAS 4A2 traced by SiO."
 },
 {
  "path": "data.lines_targeted[0].evidence[1]",
  "value": "CH3OH",
  "failed_quote": "CH3OH | 51,4 −41,3 A 243.91579 50 -4.22 44 0.14 × 0.096(−21)"
 },
 {
  "path": "data.lines_targeted[1].evidence[1]",
  "value": "SiO",
  "failed_quote": "SiO | 5-4 217.10498 31 -3.28 11 0.18 × 0.11(−13)"
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0''.18 x 0''.11 (-13 deg) for SiO, 0''.14 x 0''.096 (-21 deg) for CH3OH (~50 au)",
  "failed_quote": "with a resulting synthesized beam of 0′′. 18 × 0′′. 11 (-13◦) and 0′′. 14 × 0′′. 096 (-21◦) for the SiO and CH 3 OH spectral windows, respectively."
 },
 {
  "path": "processing.calibration.self_calibration.evidence[0]",
  "value": "phase-only self-calibration performed on the continuum after aligning setups",
  "failed_quote": "After aligning data from different setups, phase-only self-calibration was performed on the continuum, generated using a careful manual detection of line-free channels."
 },
 {
  "path": "processing.imaging.task.evidence[1]",
  "value": "CASA for continuum image; IRAM-GILDAS package for continuum-subtracted line cubes",
  "failed_quote": "The resulting continuum-subtracted line cube was created combining the two available ALMA-12m configurations (i.e. C43-3, C43-6), to have the best angular resolution, and imaged with the IRAM-GILDAS4 package"
 },
 {
  "path": "processing.imaging.line_free_channels.evidence[0]",
  "value": "manual detection of line-free channels",
  "failed_quote": "After aligning data from different setups, phase-only self-calibration was performed on the continuum, generated using a careful manual detection of line-free channels."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "0''.18 x 0''.11 (-13 deg) for SiO, 0''.14 x 0''.096 (-21 deg) for CH3OH",
  "failed_quote": "with a resulting synthesized beam of 0′′. 18 × 0′′. 11 (-13◦) and 0′′. 14 × 0′′. 096 (-21◦) for the SiO and CH 3 OH spectral windows, respectively."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "Peak offsets wrt phase center: CH3OH Red Peak (-1''.35, +1''), SiO Red Peak (-1''.27, +0''.93), CH3OH Blue Peak (-1''.41, +1''.13), SiO Blue Peak (-1''.44, +1''.19)",
  "failed_quote": "Position Ofsetc | CH3OH Red Peak SiO Red Peak CH3OH Blue Peak SiO Blue Peak (−1′′.35, +1”) (−1′′.27, +0′′.93) (−1′′.41, +1′′.13) (−1′′.44, +1′′.19)"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Imaging the continuum-subtracted line cubes",
  "failed_quote": "The resulting continuum-subtracted line cube was created combining the two available ALMA-12m configurations (i.e. C43-3, C43-6), to have the best angular resolution, and imaged with the IRAM-GILDAS4 package, using a 0.56 robust parameter5"
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Velocity-integrated intensity of SiO at CH3OH Red Peak = 44 K km s^-1",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Column density of SiO at CH3OH Red Peak = 8.7e13 cm^-2",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Velocity-integrated intensity of SiO at SiO Red Peak = 54 K km s^-1",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Column density of SiO at SiO Red Peak = 10e13 cm^-2",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Velocity-integrated intensity of SiO at CH3OH Blue Peak = 51 K km s^-1",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Column density of SiO at CH3OH Blue Peak = 10e13 cm^-2",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Velocity-integrated intensity of SiO at SiO Blue Peak = 43 K km s^-1",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Column density of SiO at SiO Blue Peak = 8.5e13 cm^-2",
  "failed_quote": "SiO | 44(6) 8.7(1.1)×1013 54(8) 10(2)×1013 51(8) 10(2)×1013 43(6) 8.5(1.1)×1013"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Velocity-integrated intensity of CH3OH at CH3OH Red Peak = 118 K km s^-1",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Column density of CH3OH at CH3OH Red Peak = 37e15 cm^-2",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Velocity-integrated intensity of CH3OH at SiO Red Peak = 37 K km s^-1",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Column density of CH3OH at SiO Red Peak = 12e15 cm^-2",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Velocity-integrated intensity of CH3OH at CH3OH Blue Peak = 67 K km s^-1",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Column density of CH3OH at CH3OH Blue Peak = 21e15 cm^-2",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Velocity-integrated intensity of CH3OH at SiO Blue Peak = 52 K km s^-1",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Column density of CH3OH at SiO Blue Peak = 16e15 cm^-2",
  "failed_quote": "CH3OH | 118(17) 37(5)×1015 37(6) 12(2)×1015 67(10) 21(3)×1015 52(8) 16(2)×1015"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "CH3OH/SiO column density (abundance) ratio at CH3OH Red Peak = 420 dimensionless",
  "failed_quote": "CH3OH/SiO | 2.7(0.8) 420(110) 0.7(0.2) 120(40) 1.3(0.4) 210(70) 1.2(0.3) 190(50)"
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "CH3OH/SiO column density (abundance) ratio at SiO Red Peak = 120 dimensionless",
  "failed_quote": "CH3OH/SiO | 2.7(0.8) 420(110) 0.7(0.2) 120(40) 1.3(0.4) 210(70) 1.2(0.3) 190(50)"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "CH3OH/SiO column density (abundance) ratio at CH3OH Blue Peak = 210 dimensionless",
  "failed_quote": "CH3OH/SiO | 2.7(0.8) 420(110) 0.7(0.2) 120(40) 1.3(0.4) 210(70) 1.2(0.3) 190(50)"
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "CH3OH/SiO column density (abundance) ratio at SiO Blue Peak = 190 dimensionless",
  "failed_quote": "CH3OH/SiO | 2.7(0.8) 420(110) 0.7(0.2) 120(40) 1.3(0.4) 210(70) 1.2(0.3) 190(50)"
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "CH3OH peaks slightly closer to the protostar than SiO (by ~0.1'') in both red- and blue-shifted ranges.",
  "failed_quote": "Additionally, the moment 0 maps in Figure 1 show that methanol peaks closer to the source than SiO in both blue and red ranges (by 0.1′′, less than a beam)."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Mm dust emission is optically thick in the central region of IRAS 4A2 and can partially absorb the mm iCOMs emission.",
  "failed_quote": "Their mm dust emission is optically thick in the central region (Maury et al. 2019; Galametz et al. 2019; Li et al. 2017; Ko et al. 2020; Guerra-Alvarado et al. 2023) to completely obscure (for 4A1) or partially absorb (for 4A2) the mm iCOMs emission (De Simone et al. 2020)."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "The individual bolometric luminosities of IRAS 4A1 and 4A2 are not measured separately due to lack of angular resolution in the infrared, and the jet inclination of IRAS 4A2 is highly uncertain (45-88 deg).",
  "failed_quote": "The inclination of the IRAS 4A2 jet is yet highly uncertain Yıldız et al. (45◦ -88◦ 2012); Choi (45◦ -88◦ 2005); Marvel et al. (45◦ -88◦ 2008); Koumpia et al. (45◦ -88◦ 2016)."
 }
]
```
