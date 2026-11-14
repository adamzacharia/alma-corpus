# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020PASJ...72...29O\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Publ._ _Astron._ _Soc._ _Japan_ (2018) 00(0), 1–11

doi: 10.1093/pasj/xxx000

## **ALMA band 8 observations of DLA 2233+131 at** z = 3.150


**Kazuyuki** **O** **GURA** [1] **, Hideki** **U** **MEHATA** **,** [2] **, Yoshiaki** **T** **ANIGUCHI** [3] **, Yuichi**
**M** **ATSUDA** [4] **, Nobunari** **K** **ASHIKAWA** [5] **, Kartik** **S** **HETH** [6] **, Katsuhiro** **M** **URATA** [7] **,**
**Masaru** **K** **AJISAWA** [8,] [9] **, Masakazu A. R.** **K** **OBAYASHI** [10] **, Takashi** **M** **URAYAMA** [11]

**and Tohru** **N** **AGAO** [9]


1 Faculty of Education, Bunkyo University, 3337 Minamiogishima, Koshigaya, Saitama,
343-8511, Japan
2 RIKEN Cluster for Pioneering Research, 2-1 Hirosawa, Wako, Saitama 351-0198, Japan
3 The Open University of Japan, 2-11 Wakaba, Mihama-ku, Chiba 261-8586, Japan
4 National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
5 Department of Astronomy, Graduate School of Science, The University of Tokyo, 7-3-1
Hongo, Bunkyo, Tokyo 113-0033, Japan
6 NASA Headquarters, Washington, DC 20546-0001, USA
7 Department of Physics, Tokyo Institute of Technology, 2-12-1 Ookayama, Meguro-ku, Tokyo
152-8551, Japan
8 Graduate School of Science and Engineering, Ehime University, Bunkyo-cho, Matsuyama,
Ehime 790-8577, Japan
9 Research Center for Space and Cosmic Evolution, Ehime University, 2-5 Bunkyo-cho,
Matsuyama, Ehime 790-8577, Japan
10 Faculty of Natural Sciences, National Institute of Technology, Kure College, 2-2-11,
Agaminami, Kure, Hiroshima, 737-8506, Japan
11 Astronomical Institute, Graduate School of Science, Tohoku University, Aramaki, Aoba,
Sendai 980-8578, Japan


_∗_ E-mail: ogurakz@koshigaya.bunkyo.ac.jp


Received ; Accepted


**Abstract**


We present our ALMA Band 8 observations of a damped Ly _α_ absorption (DLA) system at _z_ =
3.150 observed in the spectrum of the quasar Q2233+131 at _z_ = 3.295. The optical counterpart of this DLA has been identified and it shows a double-peaked Ly _α_ emission line. Since
one possible origin of DLAs at high redshift is an outflowing gas from star-forming galaxies,
DLA2233+131 provides a good laboratory to investigate the nature of high- _z_ DLAs. Motivated
by this, we have carried out ALMA band 8 observations to study the [C II] line in this system.
However, we do not detect any significant emission line in the observed pass bands.
Instead, we have serendipitously found three submm continuum sources in the observed sky
area. One appears to be the quasar Q2233+131 itself while the other two sources are newly
identified submm galaxies (SMGs), called SMG1 and SMG2 in this paper. They are located
at a separation of 4 _[′′]_ .7 and 8 _[′′]_ .1 from Q2233+131, respectively. Their 646 _µ_ m fluxes are 6.35
mJy and 6.43 mJy, respectively, being higher than that of Q2233+131, 3.62 mJy. Since these
two SMGs are not detected in the optical images obtained with the Hubble Space Telescope
and the Subaru Telescope, they have a very red spectral energy distribution. It is, therefore,


_⃝_ c 2018. Astronomical Society of Japan.



**1**

**2** _Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0


suggested that they are high-redshift galaxies or very dusty galaxies at intermediate redshift
although we cannot rule out the possibility that they are optically very faint SMG analogs at
low redshift. Follow up observations will be necessary to explore the nature of this interesting
region.


**Key words:** intergalactic medium — quasars: absorption lines — galaxies: high-redshift



**1** **Introduction**


Quasar absorption line systems in ultraviolet (UV) spec
tra of high-redshift quasars have been used to investigate
the nature of the intergalactic medium (IGM) and inter
vening objects such as gas-rich galaxies along lines of sight
of quasars (Wolfe et al. 1986; Wolfe et al. 2005). Among

such quasar absorption line systems, damped Ly _α_ absorption (DLA) systems [ _N_ (HI) _≥_ 2 _×_ 10 [20] cm _[−]_ [2] (Wolfe et
al. 1986)] as well as Lyman limit systems (LLSs) [10 [17]

cm _[−]_ [2] _≤_ _N_ (HI) _<_ 2 _×_ 10 [20] cm _[−]_ [2] (P´eroux et al. 2003)],
and metal-line absorbers like Mg ii absorbers (Bergeron,

& Boiss´e 1991; Steidel 1995b; Rao et al. 2006; Monier

et al. 2009; Rao et al. 2011) are useful in studying the

evolution of gas-rich galaxies from high through interme
diate to low redshifts. However, one serious problem is

that their optical counterparts are rarely identified (Wolfe
et al. 2005; Krogager et al. 2017). Moreover, even when

they are identified, their impact parameters are sometimes

large, several tens kpc to more than 100 kpc; e.g., Rao et
al. (2011); Fynbo et al. (2018); Mackenzie et al. (2019).
Christensen et al. (2014) examined the mass-luminosity
(MZ) relation for DLAs (e.g., Møller et al. 2013) to find

that the stellar masses of optical counterparts of DLAs

show a good agreement with those predicted by the MZ

relation, at least for the metal-rich DLAs. Krogager et al.
(2017) showed that the low detection rate of optical DLA

counterparts and the distribution of impact parameters be
tween DLAs and background quasars are explained by a

simple scenario where the “metallicity-luminosity relation”
of a DLA is given by _M_ UV = _−_ 5 _×_ [M _/_ H + 0 _._ 3] _−_ 20 _._ 8 and

the cross-section of DLA is proportional to the luminosity
following a relation _σ_ DLA _∝_ _L_ [0] _[.]_ [8] .


An open question for the nature of high- _z_ DLAs is how

the counterpart makes the absorption feature. The most

probable candidates are disks of gas-rich galaxies including dwarf and low-surface brightness ones (e.g., Prochaska,

& Wolfe 1997; Prochaska, & Wolfe 1998; Jimenez et al.

1999). On the other hand, in these two decades, the following new ideas have been proposed; galactic outflows (e.g.,
Taniguchi & Shioya 2000; Nagamine et al. 2004), tidal tails
in the galaxy interaction (e.g., Kacprzak et al. 2010), and
cosmic filaments (e.g., Fumagalli et al. 2017).



In the case of DLAs with a larger impact parameter,

outflowing gas is a good candidate of the origin of absorption feature. For example, Taniguchi & Shioya (2000)

proposed that an initial starburst in a galaxy with mass
of _∼_ 10 [11] _M_ _⊙_ makes a large-scale shocked gaseous shell

around the galaxy because of the superwind outflow. Since

its typical radius reaches to _∼_ 100 kpc, this can explain the

observed large impact parameters of DLAs. The galaxy

itself could become fainter during the course of its passive

evolution making it difficult to identify optical counter
parts in many cases which would then explain the observed

low detection rate of DLA counterparts in the optical. The

metal enrichment by Type II supernovae gives a typical
metallicity of _Z ∼_ 0 _._ 02 _Z_ _⊙_ or [M/H] _∼−_ 1 _._ 7 in the shocked

shell, consistent with the observed metallicity of DLAs.
According to Taniguchi, & Shioya (2001), the shock velocity ranges from _∼_ 0 km s _[−]_ [1] to a few thousands km s _[−]_ [1],

depending on the energy of a superwind, the evolution
ally phase of a superwind, and the viewing angle toward a

part of the shocked shell. They also found a positive cor
relation between the metallicity and velocity width, being

consistent with the observed velocity-metallicity relation
of high- _z_ DLAs (e.g., Ledoux et al. 2006). Such superwind

models can also explain the observed H i column density
distribution function (Nagamine et al. 2004). Although

it is unclear whether or not the galactic outflow is a ma
jor origin of high- _z_ DLAs, some DLAs at high redshift
with evidence for outflows have been observed so far (e.g.,

Christensen et al. 2004; Krogager et al. 2013; Kashikawa et
al. 2014). For understanding the nature of high- _z_ DLAs, it

is important to confirm the plausible origin of each DLA.


Optical observations even with the largest and most

sensitive telescopes are extremely challenging because

these systems are extremely faint in the optical due to

cosmological surface brightness dimming whereas millimeter/submillimeter windows offer a relatively constant flux

due to the negative K-correction. Therefore, instead of

the optical window, we are now able to choose the mil
limeter/submillimeter windows using the Atacama Large
Millimeter and Submillimeter Array (ALMA). In fact, re
cently, ALMA has been used to investigate the nature

of high-redshift DLA counterparts by using dust con
tinuum emission and radio atomic and molecular emis

_Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0 **3**



sion lines such as [C ii] 158 _µ_ m and CO emission lines
(Neeleman et al. 2016; Neeleman et al. 2017; Fynbo et al.

2018; Kanekar et al. 2018; Møller et al. 2018; Neeleman

et al. 2018; Neeleman et al. 2019). Encouraged by these

pioneering ALMA observations of high-redshift DLAs, in

this study, we focus on a _z_ = 3 _._ 150 DLA system in the

line of sight of Q2233+131 whose redshift is _z_ = 3 _._ 295
(Christensen et al. 2004). Because the Ly _α_ emission from

this optical counterpart shows a double-peaked profile, a

possible origin of this DLA is thought to be outflowing

gas. Since this DLA has been well studied by optical
observations (Djorgovski et al. 1996; Christensen et al.
2004; Christensen et al. 2007; Kashikawa et al. 2014), it

provides a good laboratory to examine the scenario for the

origin of the DLA, by combining optical and submm prop
erties.


The structure of this paper is as follows. In

Section 2, we summarize general properties of our target,

DLA2233+131. Section 3 describes the observations and

data reduction. The results of our ALMA observations are

shown in Section 4. In Section 5, we discuss possible sce
narios to explain the origin of DLA2233+131 and serendipitously detected submm galaxies (SMGs). Finally, we

present our concluding remark in Section 6. Throughout

this paper, we adopt a flat cosmology with Ω m = 0.3, Ω Λ
= 0.7, and _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1] .


**2** **Our target:** **DLA2233+131**


Our target is DLA2233+131 found toward the quasar
Q2233+131 at _z_ = 3 _._ 295 (see Table 1). This is the first

intervening DLA whose optical counterpart was identified

in both Ly _α_ emission and stellar continuum by Djorgovski
et al. (1996). The H i column density of DLA2233+131 has
been measured as follows; log _N_ (H i) (cm _[−]_ [2] ) = 20.00 (Lu
et al. 1993), 20.2 (Curran et al. 2002), and 19.95 [SDSS
DR5; see Kashikawa et al. (2014)]. Since all these values
are smaller than log _N_ (H i) (cm _[−]_ [2] ) = 20.3 required to de
fine the DLA, strictly speaking, this absorber is not a DLA
but a sub-DLA or a Lyman limit system (LLS); see P´eroux
et al. (2003). However, following Djorgovski et al. (1996),

we refer this absorber as DLA2233+131 in this paper. Its

optical image obtained with the Hubble Space Telescope

is shown in the right panel of Figure 2.


This DLA is located 2 _[′′]_ .3 away from the quasar at PA

= 159 _[◦]_ . The projected separation from the line of sight

to Q2333+133 is _∼_ 18 kpc. A summary of the position of

DLA2233+131 measured in the literature is given in Table

1. Note that the presence of this DLA feature was already
found by Sargent et al. (1989) and by Lu et al. (1993) and

the quasar Q2233+131 was found in the CFHT Blue Grens



**Table 1.** Positional information of Q2233+131 and


DLA2233+131


Q2233+131

_α_ (J2000) _δ_ (J2000) _z_ ref.

22:36:19.19 +13:26:20.30 3.295 1


DLA 2233+131

Relative offset from DLA 2233+131
∆ _α_ (arcsec) ∆ _δ_ (arcsec) _z_ ref.
+0.8 –2.1 3.150 _[∗][,]_ _[†]_ 2

+1.0 –2.1 3.151 3

+1.0 –2.3 3.1501 4
+0.9 –2.2 3.108   - 3.157 [#] 5


**References:** (1) SDSS DR5, (2) Djorgovski et al. (1996), (3)
Steidel et al. (1995a); N1 in their Table 12, (4) Møller et al.
(2002); N-16-1D, (5) Kashikawa et al. (2014).
_∗_ The value of _z_ DLA is taken from Lu et al. (1993).

_†_ # _z_ Since Ly _α,_ em the= 3narrowband _._ 1530 _±_ 0 _._ 0003filterinNB502Djorgovski( _λ_ c 5025et al.˚A(1996).and ∆ _λ_ = 60 [˚] A)
is used in Kashikawa et al. (2014), the redshift coverage is shown

here.


Quasar Survey Plates by Crampton et al. (1985).


After the optical identification of DLA2233+131 by
Djorgovski et al. (1996), a number of follow up studies have
been made to date. First, its metallicity is found as [Fe/H]
= _−_ 1.4 (Lu et al. 1997). Møller, & Christensen (2019)
re-derived the metallicity to be [Si/H] = _−_ 0 _._ 97 _±_ 0 _._ 13.
Since Fe tends to be depleted by dust (e.g., Wolfe et al.
2005; Rafelski et al. 2014), we use [Si/H] as the metal
licity of DLA2233+131 throughout this paper. The Ly _α_

emission-line region is further investigated by Christensen
et al. (2004) and Kashikawa et al. (2014). Christensen et al.
(2004) performed integral field spectroscopic (IFS) obser
vations of this DLA2233+131 to find a spatially extended

Ly _α_ blob with a size of _∼_ 23 kpc _×_ 38 kpc. However, the

extended morphology of Ly _α_ emission was not confirmed
by higher spectral resolution IFS observations (Christensen
et al. 2007). Christensen et al. (2007) claimed that the IFS
data obtained by Christensen et al. (2004) is likely affected

by the systematic noise. Furthermore, Kashikawa et al.
(2014) found not an extended but a compact Ly _α_ emission
line region at DLA2233+131. Their analysis shows that

its effective radius is 1.35 arcsec, corresponding to 10.24

kpc, and the Sersic index is _n_ = 1.80. Christensen et

al. (2014) estimated the stellar mass of the counterpart
of DLA2233+131 to be _∼_ 10 [9] _[.]_ [8] _M_ _⊙_ based on their SED

fitting. The observational properties of DLA2233+131

are summarized in Table 2. It is noted that another ab
sorber at _z_ = 2 _._ 543 is also identified in the UV spectrum

of Q2233+131 (Steidel et al. 1995a). However, we call the

absorber at _z_ = 3 _._ 150 as DLA2233+133 in this paper.

**4** _Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0


**Table 2.** Previously reported properties of the optical counterpart of DLA2233+131


Redshift ( _z_ DLA _,_ em ) of the counterpart measured from its emission line

_z_ DLA _,_ em References Note
3.1476 Christensen et al. (2004)


Impact parameter ( _b_ )

_b_

[arcsec] [kpc] References Note
2.3 17.5 Steidel et al. (1995a) broad-band imaging
2.3 17.5 Djorgovski et al. (1996) long-slit spectroscopy
2.37 18.0 Christensen et al. (2004) IFS
2.41 18.3 Kashikawa et al. (2014) narrow-band imaging


Photometric measurements

Measurements References Note

_V_ = 25 _._ 1, _R_ = 24 _._ 8 Steidel et al. (1995a)
_H_ = 25 _._ 34 Warren et al. (2001) HST/NICMOS
_V_ 50 = 25 _._ 75 Møller et al. (2002) _V_ 50 is a _V_ -band filter of HST/STIS
_V_ _>_ 24 _._ 40, _R >_ 24 _._ 44, _N_ 502 = 24 _._ 30 Kashikawa et al. (2014) N502 is a narrow-band filter of Subaru/FOCAS
( _λ_ eff = 5025 [˚] A, _FWHM_ = 60 [˚] A)


Ly _α_ flux measurements

Measurements References Note

(6 _._ 4 _±_ 1 _._ 2) _×_ 10 _[−]_ [17] [erg s _[−]_ [1] ] Djorgovski et al. (1996) broad-band imaging
(2 _._ 8 _±_ 0 _._ 3) _×_ 10 _[−]_ [16] [erg s _[−]_ [1] ] Christensen et al. (2004) IFS, overestimated _[∗]_

24.30 [AB mag] Kashikawa et al. (2014) narrow-band imaging

_∗_ Christensen et al. (2007).



**3** **Observations and data reduction**


We observed a sky area with a radius of 11 _[′′]_ centered at
the position of Q2233+131 in ALMA Cycle 5 (Proposal ID
2017.1.00345.S, PI: Y. Taniguchi). The observations were

conducted on 24 May 2018 using forty-six 12-m antennas

with baseline lengths of 15.0 m – 313.7 m. We used the
ALMA Band-8 receivers to detect redshifted [C ii] 158 _µ_ m

and continuum emissions from the counterpart of DLA at

_z_ = 3 _._ 150 along the sightline to Q2233+131. We used 4

bands with a width of 1.875 GHz which are divided into

128 channels. We set the central frequency of the band to
be 457.329 GHz and 459.121 GHz for the [C ii] line, while

469.329 GHz and 471.121 GHz for the continuum emission.

The total on-source integration time was 31.7 minutes.


All the data were reduced by using the Common
Astronomy Software Application (CASA) ver 5.4.0
(McMullin et al. 2007). To search for the emission line,
we create a dirty cube per 100 km s _[−]_ [1] bin. We then ap
plied uvcontsub task for each side band to make the final

cube with the natural weighting. As for the continuum

emission, we first created a dirty map with natural weight
ing using all the 4 spectral windows. We then performed

tCLEAN down to 2 _σ_, resulting that we detected 3 contin
uum sources, one of which is Q2233+131. We detected no



other objects with _>_ 3 _σ_ . Here, the 1 _σ_ noise level is _∼_ 67
_µ_ Jy/beam at the phase center. The synthesized beam size
is 0 _[′′]_ .84 _×_ 0 _[′′]_ .61 with a position angle of 52 degree. The

maximum recoverable scale is 5 _[′′]_ .15. Flux measurements

were performed via Gaussian fitting with the CASA task,

imfit. We extracted spectra of these 3 continuum sources
by adopting 1 _[′′]_ .0 diameter aperture.


**4** **Results**


4.1 The ALMA Band 8 Image


In Figure 1, we show the obtained ALMA Band 8 image

around the quasar Q2233+131. The field of view shown in
Figure 1 is approximately 22 _[′′]_ in diameter. However, note

that the sky area in which the primary beam response
exceeds 50 percent is 13 _[′′]_ in diameter (the inner dotted
circle in Figure 1), and that above 30 percent is 16 _[′′]_ .5 in
diameter (the outer dashed circle in Figure 1).


As shown in this figure, we have detected three bright

continuum sources. One is the quasar Q2233+131 itself

that is located in the center of the field of view. Since

the observed optical rest-frame magnitudes of Q2233+131,
_B_ = 18.29 and _V_ = 18.15 (Djorgovski et al. 1996) are

brighter by _∼_ 7 magnitude than those of DLA2233+131

_Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0 **5**



**Fig. 1.** The ALMA rest-frame 646 _µ_ m continuum map (S/N) of the

DLA2233131/Q2233+131 field (north is up and east is left). The field-ofview of the image is _∼_ 22 _[′′]_ in diameter. The dotted inner and dashed outer

circles indicate the area where the primary beam response exceeds 50 and

30 percent, respectively. The black field circle in the lower left corner indicates the FWHM size of the PSF (0 _[′′]_ _._ 84 _×_ 0 _[′′]_ _._ 61 with a position angle of 52

degree).


**Table 3.** Flux measurements

Objects R.A. Dec. _S_ 646 _µ_ m [mJy] _[∗]_

Q2233+131 22:36:19.19 +13:26:20.30 3.62 _[†]_ _±_ 0.10

SMG 1 22:36:19.51 +13:26:19.71 6.35 _±_ 0.17

SMG 2 22:36:19.25 +13:26:12.29 6.43 _±_ 0.47


_∗_ Integrated flux density.

_†_ This value is thought to come not from DLA2233+131 but
mostly from Q2233+131 (see text) .


(see Table 2), we assume that the most submm emission

comes not from DLA2233+131 but from Q2233+131. In

Figure 2, we compare ALMA band 8 and HST images

around Q2233+131. We find no continuum source at the

position of the optical counterpart of DLA2233+131.


The other two continuum sources are unknown ones

that are considered to be SMGs although their redshifts are

also unknown. Hereafter, we call them SMG1 and SMG2

in this paper. Their angular distances from Q2233+131
are 4 _[′′]_ .7 and 8 _[′′]_ .1, respectively. In Table 3, we give basic

observational properties of the above three bright contin
uum sources. We here note that the newly found SMGs are

brighter by a factor of two than the quasar Q2233+131.







**Fig. 2.** Comparison of our ALMA image with the HST optical image around
Q2233+131 (10 _[′′]_ _×_ 10 _[′′]_ ). The ALMA rest-frame 646 _µ_ m continuum map

(left) is compared with the HST WFPC2 F702W image (right) around

DLA2233+131/Q2233+131. The ALMA source shown at the left edge in

the left panel is SMG1 (see Figure 1).


4.2 The ALMA Band 8 Spectra of DLA2233+131,
SMG1, and SMG2


In Figure 3, we show the obtained spectrum of

DLA2233+131 together with those of Q2233+131, SMG1,

and SMG2. None of these objects show significant emis
sion lines at any observed frequency intervals. Here we use
a 1 _[′′]_ aperture for all these sources. Since the frequency

coverages of our band 8 observations are from 456.5 GHz

to 459.8 GHz and from 468.5 GHz to 471.8 GHz, our non
detection means that [C ii] 158 _µ_ m emission does not ap
pear at the redshift intervals of _z_ = 3.028 - 3.057 and _z_ =

3.133 - 3.163.


Now, let us estimate the upper limit of [C ii] 158 _µ_ m

emission line using a velocity integrated map. Here, we use

the following three methods. Method A: Aperture photometry at the Q2233+131 position with an aperture of 0 _[′′]_ .5 in

radius, Method B: Standard deviation of 300-point random
aperture photometry with an aperture of 0 _[′′]_ .5 in radius,
and Method C: RMS of the map in units of mJy/beam.

To carry out these estimates, we first combine images with
two velocity intervals, 200 km s _[−]_ [1] and 700 km s _[−]_ [1] . These

two intervals correspond to a typical FWHM for a star

forming galaxy and the lowest FWHM of Ly _α_ emission
observed by Christensen et al. (2004). The velocity center
is set to be 458.184 GHz at which [C ii] 158 _µ_ m emission

is expected to be detected at _z_ DLA . The results are sum
marized in Table 4. Although we do not know which is the

best estimate, here we adopt the result of Method B with
FWHM([C ii]) = 700 km s _[−]_ [1] . In this case, the 3 _σ_ velocity
weighted upper limit is estimated as 330 mJy km s _[−]_ [1] .

**6** _Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0




**Table 4.** Various estimates of the 1 _σ_ upper limit of [C ii ] 158 _µ_ m


emission for DLA2233+131
FWHM([C ii] ) Method A Method B Method C
(mJy km s _[−]_ [1] ) (mJy km s _[−]_ [1] ) (mJy/beam)
200 km s _[−]_ [1] 75 61 91

700 km s _[−]_ [1] 24 110 160


**5** **Discussion**


5.1 Why no detection in [C ii] from DLA2233+131 ?


As described in Section 4, we cannot detect [C ii] 158

_µ_ m emission from DLA2233+131. However, the previous

ALMA observations detected this emission from a sample

of high- _z_ DLAs at _z_ _>_ 3 _._ 6 except one target at _z_ = 4 _._ 6
(Neeleman et al. 2017; Neeleman et al. 2019); see Table 5.

Although their impact parameters range from _∼_ 20 kpc to
_∼_ 40 kpc, the velocity coverage of [C ii] 158 _µ_ m emission is
nearly the same as that of DLA, the detected [C ii] 158 _µ_ m

emission appears to come from the object associated with

the DLA in each case. The observed large impact param
eters from a few tens to several tens kpc are significantly

larger than typical sizes of such high- _z_ galaxies. It is thus

suggested that these DLA counterparts have a large halo



of dense, neutral gas around them.


Possible origins of such large halos are considered to

be either outflows from a DLA counterpart or cooling

flows from primordial gas in cosmic webs. Our target

DLA2233+131 has an evident optical counterpart observed

in both Ly _α_ emission line and UV continuum. The presence of the double-peaked Ly _α_ emission line (Christensen
et al. 2004) is considered as evidence for outflowing gas.
However, no [C ii] 158 _µ_ m emission is detected in our ob
servations. Therefore, it is important to consider possible

reasons for this non-detection.


A simple explanation is that our observations are too

shallow to detect the [C ii] 158 _µ_ m emission line. Indeed,
previously detected [C ii] lines from high- _z_ DLAs are
fainter than our detection limit (see Table 5). We estimate
a probable expected flux of [C ii] 158 _µ_ m emission using

the Ly _α_ emission line flux obtained by Djorgovski et al.
(1996); _f_ (Ly _α_ ) = (6 _._ 4 _±_ 1 _._ 2) _×_ 10 _[−]_ [17] erg cm _[−]_ [2] s _[−]_ [1] . Using

the luminosity distance to DLA2233+131, _D_ L = 26951.9

Mpc given the cosmological parameters adopted in this paper, we obtain the Ly _α_ luminosity, _L_ (Ly _α_ ) = 5 _._ 5 _×_ 10 [42] erg
s _[−]_ [1] . Adopting the case B recombination case, the Ly _α_ /H _α_
intensity ratio of 8.7, we obtain the H _α_ luminosity, _L_ (H _α_ )
= 6 _._ 4 _×_ 10 [41] erg s _[−]_ [1] . Based on this H _α_ luminosity, we
can estimate the star formation rate, _SFR_ _∼_ 5 _M_ _⊙_ yr _[−]_ [1]

using the relation of _SFR_ ( _M_ _⊙_ y _[−]_ [1] ) = 7 _._ 9 _×_ 10 _[−]_ [42] _L_ (H _α_ )

[erg s _[−]_ [1] ] (Kennicutt 1998). Using this _SFR_, we estimate
the far-infrared (FIR) luminosity, _L_ (FIR) = 1 _._ 1 _×_ 10 [44]

erg s _[−]_ [1] where FIR means the wavelength interval be
tween 1 _µ_ m and 1000 _µ_ m. Here, we use the relation
_SFR_ ( _M_ _⊙_ yr _[−]_ [1] ) = 4 _._ 5 _×_ 10 _[−]_ [44] _L_ (FIR) [erg s _[−]_ [1] ] (Kennicutt
1998). Adopting the [C ii] 158 _µ_ m emission to FIR luminosity ratio of 10 _[−]_ [2] _[.]_ [5] for _L_ (FIR) _<_ 10 [12] _L_ _⊙_ (Luhman
et al. 2003; Maiolino et al. 2009), we obtain the expected

[C ii] 158 _µ_ m emission luminosity, _L_ ([C ii]) = 3 _._ 7 _×_ 10 [41]

erg s _[−]_ [1] . Now, we can estimate the expected velocity
integrated flux of [C ii] 158 _µ_ m emission as _S_ ([C ii])
_δv_ = _L_ ([C ii]) (1+ _z_ )(1 _._ 04 _×_ 10 _[−]_ [3] ) _[−]_ [1] _ν_ rest ([C ii]) _D_ L _[−]_ [2] [, where]
_z_ = 3 _._ 150, _ν_ rest ([C ii]) = 1900.5 GHz, and _D_ L = 26951.9
Mpc (Solomon & Vanden Bout 2005). We then obtain
_S_ ([C ii]) _δv_ = 302 mJy km s _[−]_ [1] . This is lower than 3 _σ_
limit of our observations (330 mJy km s _[−]_ [1] ), as discussed

in Section 4.2.


Here, it should be noted that the [C ii]/FIR relation of high- _z_ galaxies shows a broad scatter (Carilli, &
Walter 2013; Malhotra et al. 2017) ranging [C ii]/FIR
_∼_ 10 _[−]_ [3] _[.]_ [6] _−_ 10 _[−]_ [1] _[.]_ [5] . Based on this, the estimated [C ii] flux
ranges _S_ ([C ii]) _δv_ = 24 – 3200 mJy km s _[−]_ [1] . The nondetection of [C ii] emission from DLA2233+131 implies
the low [C ii]/FIR ratio of DLA2233+131. Malhotra et
al. (2017) showed that the main determining factor for the

_Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0 **7**




[C ii]/FIR ratio is the dust temperature; lower values of

[C ii]/FIR suggest higher dust temperatures. On the other

hand, we have not detected the dust continuum emission

from DLA2233+131. Moreover, Christensen et al. (2004)

estimate the SFR of DLA2233+131 not only from the

Ly _α_ luminosity but also from the broad-band photometry,
_SFR_ (UV) = 12 _±_ 5 _M_ _⊙_ yr _[−]_ [1] . The _SFR_ (Ly _α_ )/ _SFR_ (UV)

ratio of DLA2233+131 is comparable to those of high
_z_ Ly _α_ emitters, suggesting that the DLA2233+131 host

galaxy has only little dust content. Therefore, there could
be other possibilities for the reason why [C ii] emission has

not detected.


A possible explanation is that the DLA counterpart

is optically thick enough to activate the self-shielding effect (Worseck et al. 2014). In this scenario, the [C ii]

emission line is expected to be unobservable because the

photodissociation region (PDR) cannot be formed. This

is consistent with almost all hydrogens in systems with
_N_ HI _>_ 10 [19] _[.]_ [5] are likely neutral (Viegas 1995). Although
Christensen et al. (2007) and Kashikawa et al. (2014) did

not confirm largely extended structure of DLA2233+131
reported by Christensen et al. (2004), there appear to be

some faint Ly _α_ emitting regions to the east of the galaxy
associated with an idea that the DLA (see Figure 2 of

Christensen et al. 2007 and Figure 2 of Kashikawa et al.
2014). Christensen et al. (2004) reported the Ly _α_ emis
sion line from DLA2233+131 shows a double peak profile

which is confirmed by the follow-up observations with a

higher spectral resolution performed by Christensen et al.
(2007). These properties suggest the existence of the out
flowing gas. If the optically thick scenario is the case, the

origin of the faint Ly _α_ emission in the east part of the

counterpart of DLA2233+131 can be explained by the res
onant scattering. This scenario is similar to that proposed
by Christensen et al. (2004), where Ly _α_ photons radiated

by star-forming regions are scattered by surrounding H i

clouds that are extended by the galactic outflow, although

its spatial extent is not so large.


In summary, we have estimated the [C ii] 158 _µ_ m flux to
be _S_ ([C ii]) _δv_ = 24 – 3200 mJy km s _[−]_ [1] based on the SFR

of the counterpart. A large spread of the estimated flux is
due to a broad scatter of observed [C ii]/FIR ratio. Our
non-detection suggests a low [C ii]/FIR value and the ex
posure time of our observations may be too short to detect

[C ii] emission from DLA2233+131. Indeed, most of previously detected [C ii] emission from high- _z_ DLAs is fainter
than the limiting flux of our observations (Neeleman et al.
2017; Neeleman et al. 2019). Thus it is recommended that

a new observation with a longer integration time will be

executed in future. Although there is no guideline for in
tegration time, a couple of hours integration may be fine



as a trial. Note that the previous successful detection of

[C ii] 158 _µ_ m emission from DLAs at _z ∼_ 4 has been made
with integration time of a couple of hours (Neeleman et al.
2017; Neeleman et al. 2019).


5.2 What are the two SMGs ?


We have serendipitously found the two SMGs in the
Q2233+131 field, SMG1 and SMG2 (see Fig. 1 and Table
3). In this subsection, we discuss their origins.


**5.2.1** **Basic** **properties** **of** **SMGs**


Projected separations from SMG 1 and 2 to Q2233+131
are 4 _[′′]_ .7 and 8 _[′′]_ .1, respectively. At present, we have no

direct information on their redshifts. We search for the

available data to date to estimate their redshifts.


First, in order to search for their optical counterparts,

we examine the HST/WFPC F702W and HST/NICMOS

F160W images of the Q2233+131 field in the upper central

and upper right panel of Figure 4, respectively. However,

we find no optical counterpart. Note that these image were
retrieved from the HST archive by Christensen et al. (2004)
(see their Figure 7) and Warren et al. (2001) (N16 in their
Figure 8), respectively. As for HST/STIS high-resolution
image for DLA2233+131, see Møller et al. (2002) in which

DLA2233+131 is called as N-16-1D. However, since only a

4 arcsec by 4 arcsec area is displayed, the two SMGs are not
found there. Next, Kashikawa et al. (2014) obtained broad

and narrow-band images of the Q2233+131 field to find

an optical counterpart of DLA2233+131 using the Faint
Object Camera and Spectrograph (FOCAS; Kashikawa et
al. 2002) on the Subaru Telescope. We again find no optical

counterpart at the position of the SMGs in their FOCAS

images (see the lower two panels of Figure 4). The 3 _σ_
limiting AB magnitudes of FOCAS images in a 2 _[′′]_ aperture

are _B_ = 24 _._ 40, and _V_ = 24 _._ 44, respectively.


We then checked MIR and FIR images obtained by
Wide-field Infrared Survey Explorer (WISE; Wright et al.
2010) in the framework of the ALLWISE program (Cutri
et al. 2014). Although the Q2233+131 itself is detected
in all the WISE band images (3.4, 4.6, 12, and 22 _µ_ m),
the spatial resolution of WISE (6 _[′′]_ .1 – 12 _[′′]_ .0 depending on
bands) is not high enough to resolve the quasar and the

two SMGs. Note that no image around the Q2233+131

field had been taken by the Spitzer Space Telescope.


It has been reported that most samples of previously

observed SMGs are high- _z_ objects with a median redshift
of _z ∼_ 2 _._ 5 and _∼_ 20% of SMGs are at _z >_ 3 (e.g., Chapman
et al. 2005; Yun et al. 2012; Danielson et al. 2017). At low
redshifts, Oteo et al. (2017) defined the _z <_ 0 _._ 5 analogs of

SMGs based on their dust temperatures and total IR lumi

**8** _Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0


**Table 5.** Summary of [C ii ] observations of DLA with ALMA


_z_ DLA Quasar log _N_ HI [M/H] _b_ _f_ (line) FWHM _SFR_ ref.

[ _[′′]_ ] [kpc] [mJy km s _[−]_ [1] ] [km s _[−]_ [1] ] _M_ _⊙_ yr _[−]_ [1]

4.2584 J0817+1351 21.30 _±_ 0.15 –1.15 _±_ 0.15 (S) _[∗]_ 6.2 42 13.1 460 _±_ 50 110 _±_ 10 1
3.5795 J1201+2117 21.35 _±_ 0.15 –0.747 _±_ 0.15 (Si) _[∗]_ 2.5 18 7.1 330 _±_ 50 24 _±_ 8 1
4.3900 J0834+2140 21.30 _±_ 0.10 –1.30 _±_ 0.20 (S) _[∗]_ 4.0 27 173 270 _±_ 60 _[†]_ 7 _±_ 2 2
4.3446 J1101+0531 21.00 _±_ 0.20 –1.07 _±_ 0.12 (Si) _[∗]_ 4.0 27 62 370 _±_ 60 _[†]_ _<_ 7 2

4.6001 J1253+1046 20.30 _±_ 0.15 –1.36 _±_ 0.16 _[∗∗]_ – – _<_ 42 – _<_ 9 2
4.2241 PSS1443+2724 21.10 _±_ 0.10 –0.95 _±_ 0.20 _[∗∗]_ 2.3 16 846 510 _±_ 60 _[†]_ 15 _±_ 4 2

3.150 Q2233+131 19.95  - 20.20 _−_ 0 _._ 97 _±_ 0 _._ 13 (Si) 2.3 18 _<_ 330 – 22 _±_ 12 3


**References:** (1) Neeleman et al. (2017),


(2) Neeleman et al. (2019), (3) This work.


_∗_ Measured by Rafelski et al. (2012).


_∗∗_ [M/H] = [Fe/M] + 0.3 dex (Rafelski et al. 2012).

_†_ These values correspond to ∆ _V_ 90, the velocity width


encompassing 90% of the integrated optical depth,


(e.g., Prochaska, & Wolfe 1997).



nosities. All of these low- _z_ SMG analogs are detected in op
tical observations. However, since low- _z_ SMG analogs are

selected by utilizing available spectral redshift, the sam
ples may be biased toward optically bright ones. Yun et
al. (2012) found some SMGs at _z <_ 1 in their deep submm

imaging survey. All the SMGs at _z <_ 1 confirmed by them
are brighter than _i_ =23 _._ 5 mag. Danielson et al. (2017) con
firmed spectroscopic redshifts of 73 SMGs with the Keck

Telescope. Twelve out of 73 SMGs are at _z_ _<_ 1 and all

of them are brighter than _R_ = 24 _._ 2. As for 1 _<_ _z_ _<_ 1 _._ 5
SMGs, 75% (6/8) of them have _R <_ 23 _._ 8. Again, we note

that these samples may be biased toward optically bright

objects. Taking account of the non-detection of SMG1 and

SMG2 in the optical with HST and the Subaru Telescope,

it is more likely that these SMGs are located at high red
shifts. While we found that the two SMGs are dusty and

invisible at shorter wavelengths, it is hard to derive pho
tometric redshifts for them due to the limited available

photometric points at present.


**5.2.2** **Are** **the** **two** **SMGs** **associated** **with**

**Q2233+131** **at** _z_ = 3 _._ 3 **?**


Since we cannot derive any secure redshifts of the SMGs

by utilizing the current dataset, we discuss their possi
ble association to Q2233+131 based on our ALMA data.

Although some submm detected DLA counterparts without optical detection have been found (Neeleman et al.
2019), the two SMGs in this study may not be associated

to DLA2233+131 at _z_ = 3 _._ 150 because both of them show

no [C ii] emission line as shown in Figure 3.


Hence, we discuss their association to Q2233+131.


SMG1 and SMG2 are located in the sky area within a



diameter of 16 _[′′]_ .5, in which the primary beam response

exceeds 30 percent. In this case, the presence of the

three sources, SMG1, SMG2, and Q2233+131, gives a surface number density of 1 _._ 4 _×_ 10 _[−]_ [2] arcsec _[−]_ [2], corresponding to _∼_ 50.4 deg _[−]_ [2] . We compare this surface density
with that obtained by the ALMA twenty-six arcmin [2] survey of GOODS-S at one millimeter (ASAGAO) survey
(Hatsukade et al. 2018). According to the ASAGAO sur
vey, the surface number density of SMGs at _z ∼_ 3 is estimated as _∼_ 900 deg _[−]_ [2] for SMGs with their flux density of

_S >_ 1 mJy at _λ_ = 1.2 mm, giving a surface number density
of 4 _._ 7 _×_ 10 _[−]_ [4] arcsec _[−]_ [2] . Here we estimate the flux densities

at _λ_ = 1.2 mm of the two SMGs, SMG1 and SMG2, and the

quasar Q2233+131. If we adopt a typical SED for SMGs
at _∼_ 3 (Swinbank et al. 2014), we obtain 1.4 mJy, 1.4 mJy,

and 1.0 mJy for the three sources, respectively. Therefore

the surface density of SMGs with their flux density of _S >_ 1
mJy at _λ_ = 1.2 mm is kept as 1.4 _×_ 10 _[−]_ [2] arcsec _[−]_ [2] . It is here

noted that the quasar Q2233+131 is also included as an

SMG. This surface number density is higher by a factor of

_∼_ 30 than that obtained with the ASAGAO project. Note

that, when we do not limit to _z_ _∼_ 3, the cumulative sur
face number density of ASAGAO SMGs with flux density
of _S_ _λ_ _>_ 1 _._ 350 mJy (the brightest bin) at _λ_ = 1.2 mm is
4.2 [+4] _−_ 2 _[.]_ _._ [1] 3 _[×]_ [ 10] [2] [deg] _[−]_ [2] [(see] [Table] [4] [of] [Hatsukade] [et] [al.] [2018]
for further details). This is _∼_ 8 times higher than the SMG

surface number density of our target field.


The obtained high surface number density with respect

to that of the ASAGAO survey suggests that the two SMGs

and Q2233+131 are located in an over density region at

_z_ _∼_ 3. This also suggests that our target region comprises a so-called quasar-SMG association (e.g., Fu et al.

_Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0 **9**

|(a) ALMA Band-8|Col2|Col3|(b)HST/WFPC2F702|Col5|Col6|(c)HST/NICMOSF160W|Col8|
|---|---|---|---|---|---|---|---|
||(d) Subaru/FOCAS B-band|(d) Subaru/FOCAS B-band|(d) Subaru/FOCAS B-band||(e) Subaru/FOCAS V-band|(e) Subaru/FOCAS V-band||



**Fig. 4.** Comparison between ALMA band 8 image (upper left) and optical images of the Q2233+131 field (20 _[′′]_ _×_ 20 _[′′]_ ); (a) ALMA 646 _µ_ m, (b) HST WFPC2

F702W, (c) HST NICMOS F160W, (d) Subaru FOCAS B, and (e) Subaru FOCAS V image. Three continuum sources, Q2233+131, SMG1, and SMG2, are

shown by yellow circles. The dashed circle in the panels (b), (c), (d), and (e), shows a sky area with a diameter of 16.5 arcsec.



2017; Trakhtenbrot et al. 2017). Their typical separations

are _∼_ 10 _−_ 100 kpc. Such quasar-SMG systems are considered to be gas-rich merging systems (e.g., Guilloteau et al.
1999; Wang et al. 2013; Willott et al. 2013; Fu et al. 2017).

If SMG1 and SMG2 are located at the same redshift as

that of Q2233+131, _z_ = 3 _._ 3, their projected distances from

Q2233+131 are 35.2 kpc and 60.2 kpc, respectively. If this

is the case, the environment around Q2233+131 provides

a good laboratory for future investigations of a merging

system at such a high redshift. We note that most of pre
viously discovered gas-rich merging systems are identified

as an unresolved single SMG by using either Herschel or

WISE whereas they contain multiple submm sources based

on ALMA observations. Here we note again that our three
systems (one quasar with the two SMGs) are also a single

source in the WISE observation.


However, currently, there are no lines of secure evidence

for their physical association. Future follow-up observa
tions will be important to examine this scenario. If the

SMG(s) is an optically faint object at low redshift, we

may be able to measure its redshift by deep optical spec
troscopic observations such as very sensitive long-slit or

integral field spectroscopy. If the SMGs are too faint to

detect even with very deep optical spectroscopy, ALMA

is the best telescope for the redshift measurement. The

next step will be a search for [C ii] 158 _µ_ m emission at the

Q2233+131 redshift, _z ∼_ 3 _._ 3. If still no detection, another

plan is to carry out spectral scan observations. In this case,

CO emission lines may be useful because such SMGs have



been forming stars with a high SFR and thus it is expected

that there is a lot of molecular gas in them. In this case,
CO(3-2) or CO(4-3) seems a better choice, if _z ∼_ 2 _−_ 3, be
cause this line can be detected at Band 3 whose observing

condition is generally better than that at Band 8 in the
ALMA site; e,g., Fynbo et al. (2018) and Neeleman et al.
(2018). If the SMGs are at _z <_ 1, the CO(2-1) line is useful
to the redshift measurement (e.g., Møller et al. 2018).


**6** **Summary**


We have conducted ALMA Band-8 observations of

DLA2233+131 at _z_ = 3 _._ 150 found in the UV spectrum of

quasar Q2233+131 at _z_ = 3 _._ 295. This DLA is the first in
tervening DLA at high redshift whose optical counterpart
was identified (Djorgovski et al. 1996). The Ly _α_ emission

associated with this DLA shows double peak profile whose
separation corresponds to 600 – 750 km s _[−]_ [1] (Christensen
et al. 2004). High spectral resolution IFS observations by
Christensen et al. (2007) and an excellent quality image obtained by Kashikawa et al. (2014) showed the optical coun
terpart of DLA2233+131 is a compact galaxy, although

some faint extended Ly _α_ emitting regions appear to be

associated.


To investigate the origin of this DLA, we have conducted ALMA Band 8 observations to detect [C ii] 158 _µ_ m
emission. However, we have not detected significant [C ii]

emission in our ALMA observations. A possible reason of

this non-detection is that the line is too faint to be de

**10** _Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0



tected in the relatively short integration carried out here.
We estimate the expected [C ii] from DLA2233+131 based
on its SFR derived by optical observations, _S_ ([C ii]) _δv_ =
24 – 3200 mJy km s _[−]_ [1] . The large spread of estimated flux
comes from the scatter of observed [C ii]/FIR ratio. In the
case that the [C ii]/FIR ratio is significantly low, the expected [C ii] flux is fainter than the detection limit of our
ALMA observations. Although such a lower [C ii]/FIR
value suggests higher dust temperature (Malhotra et al.
2017), optical observations imply that DLA2233+131 may

have only little dust content. This is consistent with the

non-detection of dust continuum from DLA2233+131 in

this work. Therefore, we consider another possible sce
nario in which the counterpart of DLA2233+131 is opti
cally thick enough to activate the self-shielding effect. In
this scenario, the PDR cannot be formed and thus [C ii]

emission is not radiated. The observed double peak Ly _α_

emission implies the existence of the outflowing gas. The

origin of faint emissions around DLA2233+131 may be ex
plained by the resonant scattering.


The previous ALMA [C ii] 158 _µ_ m or CO observations

of low- to intermediate- to high- _z_ DLAs are successful
(Neeleman et al. 2016; Neeleman et al. 2017; Fynbo et al.

2018; Kanekar et al. 2018; Møller et al. 2018; Neeleman et

al. 2018; Neeleman et al. 2019). Although we cannot detect [C ii] 158 _µ_ m emission from DLA2233+131, we would

like to recommend that one carry out a systematic search
for [C ii] 158 _µ_ m emission for a large sample of DLA from

low to high redshifts. One problem is that it is difficult

to estimate reasonable integration time because we do not

have any reliable line flux estimators. Therefore, the first

step is to carry out this survey with one hour integration

for any DLAs. Such a large survey will tell us useful in
formation on the origin of DLAs although there may be a

variety of DLA counterparts, e.g., outflowing gas, disks of

gas-rich galaxies from dwarf to giant ones.


Despite the non-detection of [C ii] 158 _µ_ m emission

from DLA2233+131, we have serendipitously found the

two SMGs in the observed field; SMG1 and SMG2. Their
angular separation from Q2233+131 are 4 _[′′]_ .7 and 8 _[′′]_ .1, re
spectively. They are not detected in the optical imaging

with HST and the Subaru Telescope. Since most of pre
viously observed low- _z_ SMGs are also detected in optical

observations, they may not be low- _z_ galaxies although we

cannot rule out the possibility that they are optically very

faint low- _z_ objects.


Because it is hard to drive the redshifts of SMG1 and

SMG2, we consider the possibility that these two SMGs

and Q2233+131 are associated with each other; i.e., SMG1

and SMG2 are at _z_ = 3 _._ 3 as well as Q2233+131. If this is

the case, the linear projected separations from the quasar



to SMG1 and SMG2 are 35 and 60 kpc, respectively. These

separations are similar to that of gas-rich merging systems
observed as quasar-SMG pairs at high redshift (10 – 100
kpc). If this is the case, the Q2233+131 provides an in
teresting target to study gas-rich merging systems at high

redshift. Because we cannot confine the redshifts of two

SMGs, new ALMA and/or deep optical observations will

be necessary to obtain their redshifts.


**Acknowledgments**


We are very grateful to the referee, Lise Chiristensen, for care
ful reading and many helpful comments. This paper uses the
ALMA data ADS/JAO.ALMA#2017.1.00345.S. KO is grateful
to Masahiro Nagasima for kindly giving many useful comments.

This work is supported from JSPS KAKENHI No. 16H02166
(PI: Y. Taniguchi). YT would like to thank Jason X. Prochaska
for his kind communication for these years. Actually, he showed
me ALMA observations made by his group prior to publication.

We would also like to thank Kotaro Kohno for useful discus
sion on the metallicity effect for the detection of [C ii] 158 _µ_ m

emission from DLAs.


**References**


Bergeron, J., & Boiss´e, P. 1991, A&A, 243, 344

Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105

Chapman, S. C., Blain, A. W., Smail, I., et al. 2005, ApJ, 622,

772

Christensen, L., S´anchez, S. F., Jahnke, K., et al. 2004, A&A,

417, 487

Christensen, L., Wisotzki, L., Roth, M. M., et al. 2007, A&A,

468, 587

Christensen, L., Møller, P., Fynbo, J. P. U., et al. 2014,

MNRAS, 445, 225

Curran, S. J., Webb, J. K., Murphy, M. T., et al. 2002, PASA,

19, 455

Cutri, R. M., & et al. 2014, VizieR Online Data Catalog, II/328

Crampton, D., Schade, D., & Cowley, A. P. 1985, AJ, 90, 987

Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2017,

ApJ, 840, 78

Djorgovski, S. G., Pahre, M. A., Bechtold, J., & Elston, R. 1996,

Nature, 382, 234

Fu, H., Isbell, J., Casey, C. M., et al. 2017, ApJ, 844, 123

Fumagalli, M., Mackenzie, R., Trayford, J., et al. 2017,

MNRAS, 471, 3686

Fynbo, J. P. U., Prochaska, J. X., Sommer-Larsen, J., et al.

2008, ApJ, 683, 321

Fynbo, J. P. U., Heintz, K. E., Neeleman, M., et al. 2018,

MNRAS, 479, 2126

Guilloteau, S., Omont, A., Cox, P., et al. 1999, A&A, 349, 363

Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ,

70, 105

Jimenez, R., Bowen, D. V., & Matteucci, F. 1999, ApJL, 514,

L83

Kacprzak, G. G., Murphy, M. T., & Churchill, C. W. 2010,

_Publications of the Astronomical Society of Japan_, (2018), Vol. 00, No. 0 **11**



MNRAS, 406, 445

Kanekar, N., Prochaska, J. X., Christensen, L., et al. 2018,

ApJL, 856, L23

Kashikawa, N., Aoki, K., Asai, R., et al. 2002, PASJ, 54, 819

Kashikawa, N., Misawa, T., Minowa, Y., et al. 2014, ApJ, 780,

116

Kennicutt, R. C., Jr. 1998, ARA&A, 36, 189

Krogager, J.-K., Fynbo, J. P. U., Ledoux, C., et al. 2013,

MNRAS, 433, 3091

Krogager, J.-K., Møller, P., Fynbo, J. P. U., et al. 2017,

MNRAS, 469, 2959

Ledoux, C., Petitjean, P., Fynbo, J. P. U., et al. 2006, A&A,

457, 71

Lu, L., Wolfe, A. M., Turnshek, D. A., et al. 1993, ApJS, 84, 1

Lu, L., Sargent, W. L. W., & Barlow, T. A. 1997, ApJ, 484, 131

Luhman, M. L., Satyapai, S., FIcsher, J., et al. 2003, ApJ, 594,

758

Mackenzie, R., Fumagalli, M., Theuns, T., et al. 2019, MNRAS,

1435

Maiolino, R., Caselli, P., Nagao, T., et al. 2009, A&A, 500, L1

Malhotra, S., Rhoads, J. E., Finkelstein, K., et al. 2017, ApJ,

835, 110

McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap,

K. 2007, Astronomical Data Analysis Software and Systems

XVI, 376, 127

Møller, P., Warren, S. J., Fall, S. M., et al. 2002, ApJ, 574, 51

Møller, P., Fynbo, J. P. U., Ledoux, C., et al. 2013, MNRAS,

430, 2680

Møller, P., Christensen, L., Zwaan, M. A., et al. 2018, MNRAS,

474, 4039

Møller, P., & Christensen, L. 2019, arXiv e-prints,

arXiv:1908.05362

Monier, E. M., Turnshek, D. A., Rao, S. M., et al. 2009, AJ,

138, 1609

Nagamine, K., Springel, V., & Hernquist, L. 2004, MNRAS,

348, 435

Neeleman, M., Prochaska, J. X., Ribaudo, J., et al. 2016, ApJ,

820, L39

Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2017,

Science, 355, 1285

Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2018, ApJL,

856, L12

Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A.,

& Carilli, C. L. 2019, ApJL, 870, L19

Oteo, I., Smail, I., Hughes, T., et al. 2017, arXiv e-prints,

arXiv:1707.05329

Prochaska, J. X., & Wolfe, A. M. 1997, ApJ, 487, 73

Prochaska, J. X., & Wolfe, A. M. 1998, ApJ, 507, 113

P´eroux, C., McMahon, R. G., Storrie-Lombardi, L. J., & Irwin,

M. J. 2003, MNRAS, 346, 1103

Rafelski, M., Wolfe, A. M., Prochaska, J. X., et al. 2012, ApJ,

755, 89

Rafelski, M., Neeleman, M., Fumagalli, M., et al. 2014, ApJL,

782, L29

Rao, S. M., Turnshek, D. A., & Nestor, D. B. 2006, ApJ, 636,

610

Rao, S. M., Belfort-Mihalyi, M., Turnshek, D. A., et al. 2011,



MNRAS, 416, 1215

Sargent, W. L. W., Steidel, C. C., & Boksenberg, A. 1989, ApJS,

69, 703

Solomon, P. M.., & Vanden Bout, P. A. 2005, ARA&A, 43, 677

Steidel, C. C. 1995, QSO Absorption Lines, 139

Steidel, C. C., Pettini, M., & Hamilton, D. 1995, AJ, 110, 2519

Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014,

MNRAS, 438, 1267

Taniguchi, Y., & Shioya, Y. 2000, ApJL, 532, L13

Taniguchi, Y., & Shioya, Y. 2001, ApJ, 547, 146

Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8

Viegas, S. M. 1995, MNRAS, 276, 268

Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

Warren, S. J., Møller, P., Fall, S. M., et al. 2001, MNRAS, 326,

759

Willott, C. J., Omont, A., & Bergeron, J. 2013, ApJ, 770, 13

Wolfe, A. M., Turnshek, D. A., Smith, H. E., & Cohen, R. D.

1986, ApJS, 61, 249

Wolfe, A. M., Gawiser, E., & Prochaska, J. X. 2005, ARA&A,

43, 861

Worseck, G., Prochaska, J. X., O’Meara, J. M., et al. 2014,

MNRAS, 445, 1745

Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010,

AJ, 140, 1868

Yun, M. S., Scott, K. S., Guo, Y., et al. 2012, MNRAS, 420,

957


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "2''.3 away from Q2233+131 at PA = 159 deg",
  "failed_quote": "This DLA is located 2 $['']$ .3 away from the quasar at PA = 159 $[^\\circ]$ ."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "z = 3.150 (D_L = 26951.9 Mpc)",
  "failed_quote": "This DLA is located 2 $['']$ .3 away from the quasar at PA = 159 $[^\\circ]$ ."
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Lu et al. (1993)",
  "failed_quote": "This DLA is located 2 $['']$ .3 away from the quasar at PA = 159 $[^\\circ]$ ."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Ly-alpha emission line flux of DLA2233+131, f(Ly-alpha) = (6.4 +/- 1.2) x 10^-17 erg cm^-2 s^-1, and optical magnitudes of Q2233+131 (B = 18.29, V = 18.15)",
  "failed_quote": "Since the observed optical rest-frame magnitudes of Q2233+131, $B$ = 18.29 and $V$ = 18.15 (Djorgovski et al. 1996) are brighter by $\\sim$ 7 magnitude than those of DLA2233+131 (see Table 2), we assume that the most submm emission comes not from DLA2233+131 but from Q2233+131."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Submm emission at Q2233+131 position comes mostly from Q2233+131 rather than DLA2233+131 because Q2233+131 is ~7 mag brighter in rest-frame optical.",
  "failed_quote": "Since the observed optical rest-frame magnitudes of Q2233+131, $B$ = 18.29 and $V$ = 18.15 (Djorgovski et al. 1996) are brighter by $\\sim$ 7 magnitude than those of DLA2233+131 (see Table 2), we assume that the most submm emission comes not from DLA2233+131 but from Q2233+131."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Q2233+131 646 um integrated continuum flux density = 3.62 mJy",
  "failed_quote": "Q2233+131 22:36:19.19 +13:26:20.30 3.62 $^{[\\dagger]}$ $\\pm$ 0.10"
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "SMG1 and SMG2 have very red SEDs and are likely high-redshift or very dusty intermediate-redshift galaxies, though optically very faint low-redshift SMG analogs cannot be completely ruled out.",
  "failed_quote": "It is, therefore, suggested that they are high-redshift galaxies or very dusty galaxies at intermediate redshift although we cannot rule out the possibility that they are optically very faint SMG analogs at low redshift."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Low [C II]/FIR ratio caused by high dust temperature was considered as an explanation for the [C II] non-detection, but optical SFR(Ly-alpha)/SFR(UV) ratios and the continuum non-detection imply little dust content, leading the authors to also consider self-shielding in optically thick neutral gas preventing PDR formation.",
  "failed_quote": "Malhotra et al. (2017) showed that the main determining factor for the [C ii]/FIR ratio is the dust temperature; lower values of [C ii]/FIR suggest higher dust temperatures."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "Photometric or spectroscopic redshifts cannot be derived for SMG1 and SMG2 with the currently available data, leaving their physical association with Q2233+131 unconfirmed and low-z optically faint SMG analogs not ruled out.",
  "failed_quote": "It is, therefore, suggested that they are high-redshift galaxies or very dusty galaxies at intermediate redshift although we cannot rule out the possibility that they are optically very faint SMG analogs at low redshift."
 }
]
```
