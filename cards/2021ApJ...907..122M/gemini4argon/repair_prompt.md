# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...907..122M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version November 20, 2020
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**FIR-luminous** **[C** ii **]** **emitters** **in** **the** **ALMA-SCUBA-2** **COSMOS** **survey** **(AS2COSMOS):**
**The** **nature** **of** **submillimeter** **galaxies** **in** **a** **10** **comoving** **Mpc-scale** **structure** **at** _**z**_ _∼_ 4 _._ 6


I. Mitsuhashi, [1, 2] Y. Matsuda, [2, 3] Ian Smail, [4] N. H. Hayatsu, [2] J. M. Simpson, [4, 5, 2] A. M. Swinbank, [4] H. Umehata, [6, 7]

U. Dudzeviˇci¯ut˙e, [4] J. E. Birkin, [4] S. Ikarashi, [4] Chian-Chou Chen, [5] K. Tadaki, [2] H. Yajima, [8] Y. Harikane, [9, 2]

H. Inami, [10] S. C. Chapman, [11] B. Hatsukade, [7] D. Iono, [2, 3] A. Bunker, [12] Y. Ao, [13] T. Saito, [14] J. Ueda, [2] and
S. Sakamoto [1, 2]


1 _Department_ _of_ _Astronomy,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
2 _National_ _Astronomical_ _Observatory_ _of_ _Japan,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-8588,_ _Japan_
3 _Department_ _of_ _Astronomy,_ _School_ _of_ _Science,_ _SOKENDAI_ _(The_ _Graduate_ _University_ _for_ _Advanced_ _Studies),_ _Osawa,_ _Mitaka,_ _Tokyo_
_181-8588,_ _Japan_
4 _Centre_ _for_ _Extragalactic_ _Astronomy,_ _Department_ _of_ _Physics,_ _Durham_ _University,_ _Durham,_ _DH1_ _3LE,_ _UK_
5 _Academia_ _Sinica_ _Institute_ _of_ _Astronomy_ _and_ _Astrophysics,_ _No._ _1,_ _Sec._ _4,_ _Roosevelt_ _Rd.,_ _Taipei_ _10617,_ _Taiwan_
6 _RIKEN_ _Clusterfor_ _Pioneering_ _Research,_ _2-1_ _Hirosawa,_ _Wako,_ _Saitama_ _351-0198,_ _Japan_
7 _Institute_ _of_ _Astronomy,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-0015,_ _Japan_
8 _Center_ _for_ _Computational_ _Physics,_ _University_ _of_ _Tsukuba,_ _Tsukuba,_ _Ibaraki_ _305,_ _Japan_
9 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _College_ _London,_ _Gower_ _Street,_ _London_ _WC1E_ _6BT,_ _UK_
10 _Hiroshima_ _Astrophysical_ _Science_ _Center,_ _Hiroshima_ _University,_ _1-3-1_ _Kagamiyama,_ _Higashi-Hiroshima,_ _Hiroshima_ _739-8526,_ _Japan_
11 _Department_ _of_ _Physics_ _and_ _Atmospheric_ _Science,_ _Dalhousie_ _University,_ _Halifax,_ _NS_ _B3H_ _3J5_ _Canada_
12 _Department_ _of_ _Physics,_ _University_ _of_ _Oxford,_ _Denys_ _Wilkinson_ _Building,_ _Keble_ _Road,_ _OX1_ _3RH,_ _UK_
13 _Purple_ _Mountain_ _Observatory_ _&_ _Key_ _Laboratory_ _for_ _Radio_ _Astronomy,_ _Chinese_ _Academy_ _of_ _Sciences,_ _8_ _Yuanhua_ _Road,_ _Nanjing_
_210034,_ _People’s_ _Republic_ _of_ _China_
14 _Nishiharima_ _Astronomical_ _Observatory,_ _Centre_ _for_ _Astronomy,_ _University_ _of_ _Hyogo,_ _407-2_ _Nishigaichi,_ _Sayo,_ _Sayo-gun,_ _679-5313_
_Hyogo,_ _Japan_


ABSTRACT

We report the discovery of a 10 comoving Mpc-scale structure traced by massive submillimeter galaxies (SMGs) at _z_ _∼_ 4 _._ 6. These galaxies are selected from an emission line search of ALMA Band 7
observations targeting 184 luminous submillimeter sources ( _S_ 850 _µ_ m _≥_ 6 _._ 2 mJy) across 1 _._ 6 degrees [2]

in the COSMOS field. We identify four [C ii] emitting SMGs and two probable [C ii] emitting SMG
candidates at _z_ = 4 _._ 60–4 _._ 64 with velocity-integrated signal-to-noise ratio of SNR _>_ 8. Four of the six
emitters are near-infrared blank SMGs. After excluding one SMG whose emission line is falling at the
edge of the spectral window, all galaxies show clear velocity gradients along the major axes that are
consistent with rotating gas disks. The estimated rotation velocities of the disks are 330–550 km s _[−]_ [1]

and the inferred host dark-matter halo masses are _∼_ 2–8 _×_ 10 [12] M _⊙_ . From their estimated halo masses
and [C ii] luminosity function, we suggest that these galaxies have a high (50–100%) duty cycle and
high ( _∼_ 0 _._ 1) baryon conversion efficiency (SFR relative to baryon accretion rate), and that they contribute _≃_ 2% to the total star-formation rate density at _z_ = 4 _._ 6. These SMGs are concentrated within
just 0.3% of the full survey volume, suggesting they are strongly clustered. The extent of this structure
and the individual halo masses suggest that these SMGs will likely evolve into members of a _∼_ 10 [15] M _⊙_
cluster at _z_ = 0. This survey reveals synchronized dusty starburst in massive halos at _z_ _>_ 4, which
could be driven by mergers or fed by smooth gas accretion.


_Keywords:_ galaxies: evolution    - galaxies: formation    - galaxies: high-redshift    - submillimeter: galaxies



1. INTRODUCTION


The connection between environment and galaxy formation is likely to be critical to understand the variety seen in the galaxy population in the local Universe (Dressler 1980). Studies of the star-formation
activity of galaxies in overdense regions at high redshifts, which are expected to evolve into clusters by the
present day, are a powerful tool to investigate the pro


cesses involved in galaxy formation (e.g., Kodama et al.
2001; Koyama et al. 2013). For example, Romano-D´ıaz
et al. (2014) predicts that galaxies grow predominantly
by smooth gas accretion from cosmological filaments in
high-redshift overdense regions. Observationally testing
such claims is thus a key goal of galaxy evolution studies
(e.g., Umehata et al. 2019).

2 Mitsuhashi et al.



Submillimeter galaxies (SMGs) are dusty stronglystar-forming galaxies at high redshift (e.g., Smail et al.
1997; Barger et al. 1998; Hughes et al. 1998; Scott et al.
2010; Yun et al. 2012), which are believed to be tracers of massive dark-matter halos in the early Universe
(Blain et al. 1999; Hickox et al. 2012; Chen et al. 2016;
Wilkinson et al. 2017; An et al. 2019; Dudzeviˇci¯ut˙e et al.
2020). As such SMGs are potential sign-posts to identify large-scale structures (Tamura et al. 2009; Umehata
et al. 2014, 2015, 2019; Casey et al. 2014; Casey 2016;
Miller et al. 2018; Oteo et al. 2018; Cooke et al. 2019;
Hill et al. 2020; Miller et al. 2020) and also provide insights into the formation processes of massive galaxies.
The majority of SMGs are found at _z_ = 1–4 and they
are thought to be powered by gas-rich mergers or rapid
gas accretion from the cosmic web (e.g., Tacconi et al.
2008; Umehata et al. 2019; McAlpine et al. 2019). Recently, high sensitivity interferometric observations have
revealed that SMGs, including the higher-redshift examples at _z_ _>_ 4, tend to have rotating gas disks, which may
indicate that either fast gas settling in interactions, or
smooth gas accretion, make an important contribution
to fuel high-redshift starbursts (Hodge et al. 2012; De
Breuck et al. 2014; Tadaki et al. 2018). To understand
the formation process of _z_ _>_ 4 SMGs in the cosmological context, we need to study their statistical properties
based on wide-field spectroscopic survey of _z_ _>_ 4 SMGs.
The [2] P 3 _/_ 2 – [2] P 1 _/_ 2 fine structure line of C [+] at 157.74 _µ_ m
(hereafter [C ii]) is one of the brightest far-infrared lines
(e.g., Brauher et al. 2008; Smail et al. 2011). The [C ii]
line is suitable for spectroscopic identifications and studies of gas dynamics of _z_ _>_ 4 SMGs at submillimeter
wavelengths (e.g., Iono et al. 2006; De Breuck et al. 2014;
Jones et al. 2017). For instance, the ALMA-LABOCA
Extended _Chandra_ Deep Field-South Survey (ALESS,
Hodge et al. 2013) and ALMA-SCUBA-2 survey of the
UDS field (AS2UDS, Stach et al. 2019) serendipitiously
detected [C ii] emitting SMGs at _z_ = 4 _._ 4–4.6 from their
ALMA Band 7 snapshot observations of large samples
of submillimeter sources (Swinbank et al. 2012; Cooke
et al. 2018).
In this paper, we report a search for [C ii]-emitting
SMGs in the Cosmic Evolution Survey (COSMOS) field,
based on ALMA Band 7 snapshot observations. We
take advantage of the [C ii] line to investigate the starformation activity in the SMGs and the environments
they reside in. Throughout this paper, we assume
a ΛCDM cosmology with Ω M = 0 _._ 3, Ω Λ = 0 _._ 7 and
_H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1] .


2. DATA


The targets studied in this work represent an effectively complete sample of 184 luminous ( _S_ 850 _µ_ m _≥_
6 _._ 2 mJy) submillimeter sources across a sky area
of _∼_ 1 _._ 64 degrees [2], selected from the SCUBA2 COSMOS survey (S2COSMOS, Simpson et al.
2019). Among the 184 sources, ALMA Band 7 data



of 24 sources are obtained from the ALMA data
archive (2013.1.00034.S 2015.1.00137.S; 2015.1.00568.S;
2015.1.01074.S; 2016.1.01604.S; 2016.1.00478.S). We observed the remaining 160 submillimeter sources in program 2016.1.00463.S and full details of the observation,
reduction and analysis of the whole survey are presented
in Simpson et al. (2020). The observations were performed with standard single continuum setup with a total bandwidth of 7.5 GHz centered on 344 GHz, split into
two sidebands (335.7–339.3 GHz and 347.7–351.4 GHz),
corresponding to frequency of the redshifted [C ii] emission line in sources at _z_ = 4 _._ 40–4 _._ 46 and _z_ = 4 _._ 60–
4 _._ 66 respectively. We estimate that the full survey volume for the [C ii] line emission search in our study is
2 _._ 2 _×_ 10 [6] cMpc [3] . The full width half maximum (FWHM)
of the ALMA primary beam at 344 GHz is _∼_ 17 _[′′]_, which
covers the whole SCUBA-2 beam ( _∼_ 15 _[′′]_ ). The minimum and maximum baseline lengths were 15.0 m and
313.7 m respectively.
We calibrated the data and made dirty image cubes
with Common Astronomy Software Application (casa)
version 5.6.1 (McMullin et al. 2007). The cubes have a
synthesized beam of 0 _._ 8 _[′′]_ _×_ 0 _._ 8 _[′′]_ and a typical 1- _σ_ depth
of _∼_ 2 _._ 4 mJy beam _[−]_ [1] in a 27 km s _[−]_ [1] spectral channel.
A more detailed description of reduction and the full
catalogue of the 260 continuum sources are presented in
Simpson et al. (2020).


3. ANALYSIS AND RESULTS


We search for emission lines in signal-to-noise ratio
(SNR) cubes as shown in Figure 1 (see also Hayatsu
et al. 2017). We start from the dirty cubes without primary beam correction, which have uniform noise levels
across each field. To provide sensitivity to a wide range
of line widths, we bin these data cubes to four different
velocity resolutions (80, 140, 300 and 750 km s _[−]_ [1], see
Cooke et al. 2018). To estimate the continuum level excluding emission lines, we average all channels for each
spatial pixel in the binned data cubes using 2- _σ_ clip


**Figure** **1.** Flowchart of our line search method.

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 3







**Figure** **2.** Sky positions of five [C ii]-emitting SMGs (yellow circles) and the emitter we excluded (orange circle) with the
spatially integrated spectra of their emission lines. The white circles show the positions of the parent sample of 184 SMGs
from the AS2COSMOS survey (Simpson et al. 2020) and green circles show the positions of the sources from S2COSMOS and
A [3] COSMOS (An et al. 2019; Liu et al. 2019) with photometric redshift of _z_ = 4–5. The five emitters are clustered in a small
sky region ( _∼_ 7 _[′]_ or 16 comoving Mpc) and in a narrow redshift range (∆ _z_ [C ii] = 0 _._ 021 or ∆ _v_ = 1100 km s _[−]_ [1] ). The background
image is the 850- _µ_ m SCUBA-2 map from Simpson et al. (2019) and the black solid line shows the survey area of 1.6 degree [2]

corresponding to the _HST_ /ACS coverage. We also show two AGNs at _z_ = 4 _._ 64 (Hasinger et al. 2018, magenta circles) and a
protocluster at _z_ = 4 _._ 53–4.60 (Lemaux et al. 2018, cyan circle). The spectra were binned to a _∼_ 135 km s _[−]_ [1] resolution. Red and
blue lines show single and double Gaussian fits respectively. The dashed lines show the average 1- _σ_ noise of each channel. The
gray shaded regions in each spectrum show the gaps in the spectral coverage.



ping. We iterate this procedure until the 2- _σ_ clipping
converges, and subtract the resulting continuum values
from the data cubes. We check that the 2- _σ_ clipped
average is more stable than a linear fit without oversubtraction. We also confirm that continuum levels estimated from a median agree with those from 2- _σ_ clipped
average within 10% and that the choice of the methods
used in continuum estimation does not affect the following line detection. As the noise is not constant across
the frequency bands, we construct the SNR cubes by
dividing each channel of the binned dirty cubes by the
rms of that channel measured across the full field of the
cube.



In the binned, continuum-subtracted SNR cubes, we
detect six line emitters with peak SNR _>_ 6 _._ 2. We adopt
this 6 _._ 2- _σ_ threshold on the grounds that no false detection appear in any of the inverted data cubes above
this significance. This means that there is no negative
peak exceeding _−_ 6 _._ 2 _σ_ in any of the 184 SNR cubes we
searched. For 80, 140, 300, 750 km s _[−]_ [1] binning scales,
this threshold corresponds to detection limits of [C ii] luminosity of _L_ [C ii] = 0 _._ 5 _,_ 0 _._ 7 _,_ 1 _._ 1 _,_ 1 _._ 8 _×_ 10 [9] L _⊙_ at _z_ _∼_ 4 _._ 5,
or observed frame equivalent width (EW) of EW = 0.4,
0.5, 0.8, 1.3 _µ_ m for a source with _S_ 870 _µ_ m = 6 _._ 2 mJy.
All of the six line emitters are associated with 870_µ_ m continuum sources. We exclude one line emitter
(AS2COS0002.1) because we cannot measure the total

4 Mitsuhashi et al.



line flux or line velocity width of the emission line as it
falls at the edge of the spectral window [1] (see Figure 2).
We measure the SNR of the emission lines from velocity integrated maps between _ν_ obs _−_ 0 _._ 5 _×_ FWHM and
_ν_ obs + 0 _._ 5 _×_ FWHM at the peak pixels. Our final sample comprises five emitters with lines detected at high
significance levels, integrated SNR _>_ 8. We show the
sky distribution of the emitters in Figure 2. All of these
emitters fall within a 7-arcmin diameter region and a
narrow frequency range (337.3–338.5 GHz).
We have checked the completeness of our line search
by simulating 1 _._ 2 _×_ 10 [7] Gaussian-like emission line with
the range of the FWHMs of 80–2000 km s _[−]_ [1] and luminosities of 10 [7] _[.]_ [5] –10 [10] _[.]_ [1] _L_ _⊙_ and injecting them in data
cubes containing pure noise representative of the survey
(2.4 mJy beam _[−]_ [1] per channel). We split FWHMs into
300 cells and luminosities into 700 cells in log space,
thus there are 55 lines in each cell. From this analysis we find that the completeness is almost unity above
_L_ [C ii] = 3 _×_ 10 [9] _L_ _⊙_, which is about _∼_ 10 times higher
than the detection limits for other [C ii] emitting galaxies at _z_ _>_ 4 (see Figure 3).
As the SNRs of our detected lines are not high enough
to require cleaning, we measure the line properties using the dirty, primary-beam-corrected flux data cubes.
We use casa/imfit task to measure the continuum flux
densities, velocity-integrated line fluxes and sizes. The
observed properties are summarized in Table 1. We
re-calculate continuum levels excluding channels containing the emission lines and construct line-free continuum maps. The line-free continuum maps are used
to measure the spatially integrated continuum flux densities with 2-D Gaussian profiles. We also construct
emission line cubes by subtracting the estimated continuum values (shown as green solid lines in Figure 2)
from the cubes. We measure the velocity widths of the
spatially-integrated emission lines using single Gaussian
profiles (see Figure 2). All of the emission lines have
large velocity widths: ≳ 500 km s _[−]_ [1] . Figure 4 shows
the velocity-integrated flux maps (moment 0) and the
velocity maps (moment 1) of the five emitters. The
spatially-integrated line fluxes and beam-deconvolved
major/minor axes are measured by using 2-D Gaussian profiles for the line emitting regions detected above
_>_ 3 _σ_ on the moment 0 maps. We correct for missing
line flux falling into the gaps of the spectral windows
by interpolating the emission lines with single Gaussian
fits. The estimated missing line fluxes are _∼_ 10% for
AS2COS0001.1, _∼_ 25% for AS2COS0001.2 and negligible (less than 5%) for the remaining three sources.
All the five emitters show clear velocity gradients on


1 We confirm that AS2COS0002.1 (R.A. 150.106505 deg, Dec.
2.26362 deg) has a redshift of _z_ = 4 _._ 596 through the detection
of [12] CO(5–4) (Chen et al. in prep) and has a faint near-infrared
counterpart ( _K_ _s_ _>_ 24 ABmag).



**Figure** **3.** [C ii] velocity width vs line luminosity of the
five emitters. Red and black circles show the values before
and after correcting for lensing amplification (See Section
3.2). Black dashed line shows _L_ [C ii] _∝_ FWHM [2] [C ii] [relation]
scaled to the data points of SMGs. Background shows the
completeness of our line search as a function of the input
velocity width and input line luminosity. We confirm that
the completeness is almost unity above _L_ [C ii] = 3 _×_ 10 [9] _L_ _⊙_ .
The literature values come from Iono et al. (2006); Wagg
et al. (2010); Wang et al. (2013); Willott et al. (2013); Ouchi
et al. (2013); Carniani et al. (2013, 2018); Riechers et al.
(2014); Capak et al. (2015); Maiolino et al. (2015); Willott
et al. (2015); Yun et al. (2015); Pentericci et al. (2016); Miller
et al. (2016); Venemans et al. (2016); Smit et al. (2018);
Hashimoto et al. (2019); Harikane et al. (2020)


the moment 1 maps. Since the directions of these velocity gradients match the major axis position angles,
they are likely to be rotating gas disks. Simpson et al.
(2020) and Jim´enez-Andrade et al. (2020) have already
confirmed that AS2COS0001.1/1.2 show clear rotating
features with higher angular resolution ALMA data.


3.1. _Line_ _identification_


Our five line-emitting SMGs have also been detected with AzTEC on the James Clerk Maxwell Telescope (JCMT), with AS2COS0001 and AS2COS0006
corresponding to AzTEC2 and AzTEC9 (Scott et al.
2008; Younger et al. 2009). Later, AS2COS0001,
AS2COS0006 and AS2COS0034 were also identified as AzTEC-C3, AzTEC-C14 and AzTECC30 using AzTEC on the Atacama Submillimeter Telescope Experiment (ASTE, Aretxaga et al.
2011). These SMGs are also detected in the
_Herschel_ /HerMES survey (Oliver et al. 2012) and
an earlier SCUBA-2 850 _µ_ m survey (Casey et al.
2013). While more recently, AS2COS0001.1/1.2,
AS2COS0006.1 and AS2COS0034.1/34.2 were identified
in ALMA Band6 as AzTEC-C3a/C3b, AzTEC-C14 and
AzTEC-C30a/C30b (Brisbin et al. 2017).

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 5


**Table** **1.** Properties of the five emission-line-detected SMGs


ID _[a]_ AS2COS0001.1 AS2COS0001.2 AS2COS0006.1 AS2COS00034.1 AS2COS0034.2


R.A.(deg) _[a]_ 150.03350 150.03268 149.98871 150.10446 150.10572
Dec.(deg) _[a]_ 2.43675 2.43701 2.45850 2.43537 2.43481
_µS_ 870 _µ_ m (mJy) _[b]_ 12 _._ 2 _±_ 0 _._ 4 3 _._ 2 _±_ 0 _._ 2 12 _._ 5 _±_ 0 _._ 5 4 _._ 1 _±_ 0 _._ 3 3 _._ 7 _±_ 0 _._ 2
_µS_ 3GHz ( _µ_ Jy) _[c]_ 15 _._ 0 _±_ 2 _._ 4 28 _._ 8 _±_ 2 _._ 7 13 _._ 2 _±_ 3 _._ 3 13 _._ 0 _±_ 2 _._ 4 3 _._ 9 _±_ 2 _._ 2
_ν_ obs (GHz) 337.90 337.27 338.17 338.49 338.14
_z_ [C ii] 4 _._ 625 _±_ 0 _._ 001 4 _._ 635 _±_ 0 _._ 001 4 _._ 620 _±_ 0 _._ 001 4 _._ 615 _±_ 0 _._ 001 4 _._ 621 _±_ 0 _._ 001
FWHM [C ii] (km s _[−]_ [1] ) 710 _±_ 50 560 _±_ 50 1090 _±_ 80 650 _±_ 80 540 _±_ 60
_Sdv_ [C ii] (Jy km s _[−]_ [1] ) _[d]_ 7 _._ 0 [+0] _−_ 1 _[.]_ _._ [8] 3 4 _._ 7 [+0] _−_ 0 _[.]_ _._ [6] 6 15 _._ 9 _±_ 1 _._ 3 5 _._ 5 [+1] _−_ 1 _[.]_ _._ [0] 1 6 _._ 0 _−_ [+1] 1 _[.]_ _._ [1] 7
_L_ [C ii] (10 [9] _L_ _⊙_ ) 4 _._ 4 [+0] _−_ 0 _[.]_ _._ [5] 8 3 _._ 0 [+0] _−_ 0 _[.]_ _._ [4] 4 10 _._ 1 _±_ 0 _._ 8 3 _._ 5 [+0] _−_ 0 _[.]_ _._ [6] 7 3 _._ 8 _−_ [+0] 1 _[.]_ _._ [7] 1
SFR [C ii] ( _M_ _⊙_ yr _[−]_ [1] ) 390 [+350] _−_ 180 260 [+240] _−_ 120 880 [+790] _−_ 420 310 [+280] _−_ 150 330 [+300] _−_ 160
SNR _[e]_ 15.3 10.0 17.4 8.0 10.7
EW( _µ_ m) _[f]_ 2 _._ 3 _±_ 0 _._ 2 5 _._ 2 _±_ 0 _._ 7 3 _._ 7 _±_ 0 _._ 3 4 _._ 5 _±_ 0 _._ 8 5 _._ 9 _±_ 1 _._ 0
size [C ii] ( _[′′]_ _×_ _′′_ ) _g_ 0 _._ 6 _[±]_ [0] _[.]_ [1] _×_ 0 _._ 4 _[±]_ [0] _[.]_ [1] 0 _._ 6 _[±]_ [0] _[.]_ [1] _×_ 0 _._ 5 _[±]_ [0] _[.]_ [2] 0 _._ 9 _[±]_ [0] _[.]_ [1] _×_ 0 _._ 2 _[±]_ [0] _[.]_ [1] 0 _._ 8 _[±]_ [0] _[.]_ [2] _×_ 0 _._ 1 _[±]_ [0] _[.]_ [3] 0 _._ 6 _[±]_ [0] _[.]_ [3] _×_ 0 _._ 4 _[±]_ [0] _[.]_ [3]

_i_ (deg) 47 _±_ 9 34 [+28] _−_ 34 77 _±_ 8 80 [+10] _−_ 21 52 [+34] _−_ 52
_V_ rot (km s _[−]_ [1] ) 470 _±_ 80 490 _−_ 180 _[h]_ 550 _±_ 40 330 [+50] _−_ 10 340 _−_ 70 _[h]_

_M_ _h_ [ind] (10 [12] M _⊙_ ) 5 _._ 1 _±_ 1 _._ 4 5 _._ 7 _−_ 3 _._ 6 _[h]_ 8 _._ 0 _±_ 1 _._ 1 1 _._ 7 [+0] _−_ 0 _[.]_ _._ [4] 1 1 _._ 9 _−_ 0 _._ 7 _[h]_

_M_ _h_ [NFW] (10 [12] M _⊙_ ) _[i]_ 6 _._ 4 [+2] _−_ 1 _[.]_ _._ [3] 8 - 0 _._ 8 [+0] _−_ 0 _[.]_ _._ [6] 4
_M_ dyn (10 [11] M _⊙_ ) 1 _._ 7 _±_ 0 _._ 3 1 _._ 9 _−_ 0 _._ 9 _[h]_ 2 _._ 3 _±_ 0 _._ 3 0 _._ 8 [+0] _−_ 0 _[.]_ _._ [2] 1 0 _._ 9 _−_ 0 _._ 3 _[h]_

SFR 870 _µ_ m ( _M_ _⊙_ yr _[−]_ [1] ) _[j]_ 390 [+80] _−_ 10 230 [+30] _−_ 10 450 [+10] _−_ 10 260 [+30] _−_ 10 240 [+40] _−_ 10
_µ_ _[k]_ 1 _._ 4 [+0] _−_ 0 _[.]_ _._ [2] 1 1 _._ 2 [+0] _−_ 0 _[.]_ _._ [1] 1     - 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [1] 1 1 _._ 3 [+0] _−_ 0 _[.]_ _._ [3] 1


Note—
_a_ Source IDs and coordinates come from the full AS2COSMOS catalog presented in Simpson et al. (2020).
_b_
total continuum flux densities excluding line emission measured with the CASA/imfit task.
_c_ radio continuum fluxes from Smolˇci´c et al. (2017).
_d_
total emission line flux measured with the CASA/imfit task.
_e_ velocity-integrated peak emission line signal to noise ratio within the FWHM.
_f_ observed-frame line equivalent widths.
_g_ beam deconvolved major and minor axes measured with the CASA/imfit task.
_h_
upper limits cannot be constrained from uncertainty of the inclinations.
_i_
common halo masses assuming NFW dark matter profile.
_jk_ star-formation rate estimated from _S_ 870 _µ_ m and conversion in Dudzeviˇci¯ut˙e et al. (2020).
gravitational magnification factors.



Among the five line emitters, three have been already confirmed to be at _z_ _∼_ 4 _._ 6. Recently, Jim´enezAndrade et al. (2020) observed the two line emitters
(AS2COS0001.1/1.2) with NOrthern Extended Millimeter Array (NOEMA) Band 1 and detected [12] CO(5–4)
lines at _z_ = 4 _._ 63 (see also Simpson et al. 2020). Birkin
et al. (2020) also observed AS2COS0006.1 as a part
of large CO surveys of luminous SMGs and detected
12
CO(5–4) and [C i] at _z_ = 4 _._ 62.
Their multi-wavelength properties, line equivalent
widths and close proximity suggest that the remaining two sources (AS2COS0034.1/34.2) are also likely to
be [C ii] emitters at _z_ = 4 _._ 62. Figure 5 shows multiwavelength images of the five emitters (Koekemoer
et al. 2007; Sanders et al. 2007; McCracken et al. 2012;
Smolˇci´c et al. 2017). The confirmed [C ii] emitters are
near-infrared blank or faint SMGs ( _K_ _s_ _>_ 24 ABmag).
AS2COS0034.1/34.2 do not have any clear optical/near


infrared counterparts, which is consistent with them lying at _z_ ≳ 4 (e.g., Simpson et al. 2014; Wang et al. 2019;
Dudzeviˇci¯ut˙e et al. 2020; Umehata et al. 2020; Smail
et al. 2020). We use the _S_ 870 _µ_ m _/S_ 3GHz flux ratio as a
crude redshift indicator (e.g., Carilli & Yun 1999; Barger
et al. 2000; Smail et al. 2000). AS2COS0034.1/34.2 have
_S_ 870 _µ_ m _/S_ 3GHz flux ratios of 320 _±_ 60 and 950 _±_ 540
respectively. By comparing with the typical SEDs of
SMGs (Silva et al. 1998; Swinbank et al. 2010, 2014;
Dudzeviˇci¯ut˙e et al. 2020, Ikarashi et al. in prep), the
flux ratios suggest that they are likely to be at _z_ = 3–
5 (see Figure 6). In addition, these values are consistent with those of our three confirmed [C ii]-emitters at
_z_ = 4 _._ 62–4 _._ 64. Thus AS2COS0034.1/34.2 are unlikely
to be low- or mid- _J_ CO line emitters at _z_ _≪_ 3 _._ 0. Moreover, the emission lines of AS2COS0034.1/34.2 have
observed-frame equivalent widths of EW = 4 _._ 5 _±_ 0 _._ 8
and 5 _._ 9 _±_ 1 _._ 0 _µ_ m, which are similar to the [C ii] EW

6 Mitsuhashi et al.


**Figure** **4.** Top: The velocity-integrated flux maps of five detected line-emitting SMGs. The black contours show the surface
brightness of the emission lines starting from 3 _σ_ with 2- _σ_ intervals. Velocity offsets, projected spatial separations and directions
of any companions (if they have one) are also shown. The dashed lines show major-axis position angles. Bottom: The velocity
maps with 3- _σ_ clipping. Typical velocities (in km s _[−]_ [1] ) and major axis position angles are also denoted. All of the five sources
show clear velocity gradients along the major axes that are consistent with rotating disks.


**Figure** **5.** Multi-wavelength images of the five line-emitting SMGs. The small red circles show the positions of ALMA Band 7
continuum sources (Table 1). The yellow dashed circles indicates the ALMA field of view. AS2COS0034.1/34.2 do not have
detected counterparts in the optical or near-infrared bands (similar to AS2COS0001.1/1.2), suggesting that they are also likely
to be at _z_ _>_ 4. In the fields of AS2COS0001 and AS2COS0034, there are foreground galaxies near the SMGs, which could
modestly magnify the sources due to gravitational lensing (see Section 3.2).

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 7



**Figure** **6.** The _S_ 870 _µ_ m _/S_ 3GHz flux ratio as a function of redshift. The colored curves show the predicted ratios based
on the SEDs of Arp220, Cosmic Eyelash and various composite SMGs (Silva et al. 1998; Swinbank et al. 2010, 2014;
Dudzeviˇci¯ut˙e et al. 2020, Ikarashi et al. in prep). The flux
ratios of AS2COS0034.1/34.2 suggest that they are likely to
lie at _z_ = 3–5 and are comparable with the ratios of the
confirmed [C ii]-selected SMGs at _z_ = 4 _._ 62–4 _._ 64.


of the _z_ _∼_ 4 _._ 4 SMGs (1.8 and 4.9 _µ_ m) from Swinbank
et al. (2012) and our three confirmed [C ii]-emitters at
_z_ = 4 _._ 62–4 _._ 64 (2.3–5.3 _µ_ m). These observed-frame EWs
are several times larger than high- _J_ CO lines at intermediate redshifts (e.g., Hayatsu et al. 2017) and three times
smaller than [O iii] at _z_ _∼_ 9 (e.g., Tamura et al. 2019).
Thus AS2COS0034.1/34.2 are unlikely to be high- _J_ CO
line or [O iii] emitters. Therefore we treat these two
sources as [C ii] emitter candidates at _z_ _∼_ 4 _._ 6.


3.2. _Gravitational_ _lensing_


There is a _z_ = 0 _._ 73 rich cluster 5-arcmin northeast from AS2COS0006.1 (Guzzo et al. 2007), which
could amplify the emission from the SMGs either due
to cluster-scale gravitational lensing (Aretxaga et al.
2011), or more realistically given the angular separation
to the cluster center, by increasing the projected density
of foreground galaxies, which could act as galaxy-scale
lenses (e.g., Smail et al. 2005). As shown in Figure 5,
there are foreground galaxies near the SMGs in the
fields of AS2COS0001.1/1.2 and AS2COS0034.2/34.2
which could also amplify the emission from the SMGs by
galaxy-galaxy gravitational lensing (the galaxy close to
AS2COS0034.1/34.2 is indeed at _z_ = 0 _._ 73). To assess
the relative importance of these various lensing structures we estimate the amplification factor, _µ_, by using
a simple singular isothermal sphere model.
The foreground _z_ = 0 _._ 73 cluster has an estimated
mass within _R_ 500 (84 arcsec) of _M_ _∼_ 1 _._ 7 _×_ 10 [14] M _⊙_
(Guzzo et al. 2007). An isothermal model would suggest a virial velocity of _V_ vir = 1100 km s _[−]_ [1] within a virial



radius of _r_ vir = 1200 kpc. We extrapolate the isothermal distribution to the source separations and convert
from the rotational velocity to velocity dispersion with
the relationship of _σ_ [2] = _V_ vir [2] _[/]_ [2.] The resulting predicted amplifications for AS2COS0001, AS2COS0006
and AS2COS0034 are _µ_ = 1 _._ 02 _±_ 0 _._ 01, 1 _._ 04 _±_ 0 _._ 01 and
1 _._ 01 _±_ 0 _._ 01, which are less than 5% and negligible.
A foreground galaxy at _z_ = 0 _._ 33 is located near
AS2COS0001.1/1.2 (Faure et al. 2008). This galaxy
has an estimated stellar mass of _M_ _⋆_ = 10 [11] _[.]_ [0] M _⊙_ and
is classified as a quiescent galaxy (Laigle et al. 2016).
We convert the stellar mass to a velocity dispersion
of 170 _±_ 30 km s _[−]_ [1] using the Faber-Jackson relation in
Gallazzi et al. (2006). The predicted amplifications for
AS2COS0001.1/1.2 are then _µ_ = 1 _._ 4 [+0] _−_ 0 _[.]_ _._ [2] 1 [and] [1] _[.]_ [2] [+0] _−_ 0 _[.]_ _._ [1] 1 [re-]
spectively. We confirm that these amplification factors
are almost comparable with the result in the previous
work (Jim´enez-Andrade et al. 2020, 1.5 _×_ and 1.35 _×_ respectively).
Similarly, a foreground galaxy at _z_ = 0 _._ 73 is also located between AS2COS0034.1/34.2 (Lilly et al. 2007).
We note that different velocity peaks and different EW
of the emission lines (see Figure 2 and Table 1) suggest
that these two sources are not strongly-lensed multiple
images of a single galaxy. The foreground galaxy has an
estimated stellar mass of _M_ _⋆_ = 10 [10] _[.]_ [6] M _⊙_ and is classified as a star-forming galaxy (Laigle et al. 2016). We
derive a rotation velocity of _V_ rot = 200 [+70] _−_ 50 [km s] _[−]_ [1] [from]
the Tully-Fisher relation in Di Teodoro et al. (2016).
We then convert from the rotational velocity to velocity
dispersion with the relationship of _σ_ [2] = _V_ rot [2] _[/]_ [2.] [The] [re-]
sulting predicted amplifications for AS2COS0034.1/34.2
are _µ_ = 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [1] 1 [and] [1] _[.]_ [3] [+0] _−_ 0 _[.]_ _._ [3] 1 [respectively.]
The influence of galaxy-galaxy lensing seems dominant for AS2COS0001.1/1.2 and AS2COS0034.1/34.2,
rather than the effect of the foreground _z_ = 0 _._ 73 cluster. Although we have confirmed that the expected
lens amplifications due to foreground galaxies are relatively modest, we correct for these magnification factors
throughout the rest of the paper.


3.3. _Spatial_ _distribution_ _and_ _environment_


Figure 7 shows the 3-D map of our five [C ii] emitting
SMGs (and candidates). We see that these SMGs are
concentrated within a 7 _._ 0 _×_ 1 _._ 4-arcmin region on the sky
(16 _×_ 3 cMpc at _z_ = 4 _._ 6) and a narrow-redshift range of
∆ _z_ = 0 _._ 021 (12 cMpc at _z_ = 4 _._ 6), which correspond to
just _≃_ 0 _._ 3% of the full survey volume (gray shaded regions in Figure 7, see Section 2). The SMG distribution
appears to link to the surrounding larger scale structure
(see Figure 2 and 7). AS2COS0002.1 at _z_ = 4 _._ 596 is located 10-arcmin (20 cMpc in projection) south from the
SMG structure. There are two AGNs at _z_ = 4 _._ 64 very
close to the SMG structure (Hasinger et al. 2018). There
is also a protocluster of LBGs at _z_ = 4 _._ 53–4 _._ 60 (Lemaux
et al. 2018), which is 20-arcmin (40 cMpc in projection)
apart from the SMG structure. There are 91 SMGs with

8 Mitsuhashi et al.



**Figure** **7.** 3-D map of [C ii] emitters (and candidates) in the
full survey volume. Symbols are as in Figure 2. We see that
the [C ii] emitters are both spatially concentrated on the sky
(as shown in )Figure 2), but also in 3-D space.


photometric redshifts of _z_ = 4–5 from S2COSMOS and
A [3] COSMOS (An et al. 2019; Liu et al. 2019). Some
of the SMGs could be at _z_ = 4 _._ 6 and are potentially
related with the SMG structure. Future observations
will be able to reveal their possible connections and the
whole picture of the larger scale structure.


3.4. _Dark_ _matter_ _halo_ _mass_


We estimate the individual dark matter halo masses,
_M_ h, for each of the line emitter SMGs adopting an idealised spherical collapse model (e.g., Barkana & Loeb
2001). This assumes that the galaxy’s measured rotation velocity, _V_ rot, is equal to the circular velocity of
the host halo (i.e., isothermal sphere, see also Posti
et al. 2019) and that the halo is collapsed at the observed redshift. To derive the rotation velocity we
first estimate the inclination angle of the [C ii]-emitting
gas disks, _i_, with _i_ = cos _[−]_ [1] _a_ min _/a_ maj, where _a_ min
and _a_ maj are the deconvolved minor and major axes of

[C ii] emission, respectively (see Table 1). The major
axes span 4–6 kpc. We calculate the rotation velocities from the velocity widths with the following relation, _V_ rot = 1 _/γ_ _×_ FWHM [C ii] _/_ sin _i_ ( _γ_ = 2, Kohandel
et al. 2019). The range of estimated halo masses of our
five SMGs is 2–8 _×_ 10 [12] M _⊙_ within virial radii of 70–
110 kpc. Since it is not clear that the assumption of the
flat rotation curve is applicable to our SMGs, we check
the consistency with different methods for the halo mass
calculation. The mass range of calculated halos corresponds to a bias of _b_ = 8 _._ 3 _±_ 1 _._ 9 at _z_ = 4 _._ 6 (Mo & White
2002), which is consistent with _b_ = 8 _._ 4 _±_ 0 _._ 7 derived



from the clustering analysis for _z_ = 3–5 SMGs (e.g., An
et al. 2019). In addition, the typical separation of our
five SMGs is _∼_ 10 cMpc and this is comparable with
the predicted clustering length of the halos with mass of
_M_ _h_ ≳ 2 _×_ 10 [12] M _⊙_ ( _∼_ 10 cMpc, Mo & White 2002). The
main uncertainties in the halo masses come from the
inclination measurements of the gas disks. The sin _i_ of
AS2COS0001.1, 6.1 and 34.1 are determined with _∼_ 15%
precision. We confirm that the measured inclination and
_V_ rot of AS2COS0001.1 is consistent with those presented
in the previous work with higher resolution data within
1 _σ_ uncertainties ( _i_ = 51 _±_ 3 _[◦]_ and _V_ rot = 540 _±_ 90 km s _[−]_ [1],
Jim´enez-Andrade et al. 2020). We note that we can only
place lower limits on the halo masses for AS2COS0001.2
and 34.2 due to the larger uncertainties of their inclination measurements. Future higher resolution and deeper
observations are needed for more precise estimates.
As shown in Figures 2 and 5, our sample contains two
SMG pairs which each could reside in common halos.
We estimate their common halo masses from the sky
separation and the velocity separation of these pairs assuming an NFW dark-matter profile (Table 1, Navarro
et al. 1997). We use the concentration parameter of
_c_ = 3 _._ 5, as expected for halos of _M_ _h_ _∼_ 10 [12] M _⊙_ at
_z_ _∼_ 4 _._ 5 (Dutton & Macci`o 2014). Since we ignore the
line-of-sight separations and the velocities in the transverse direction, the estimated halo masses with NFW
profile are lower limits. AS2COS0001.1/1.2 have an angular separation of 3 _._ 1 _[′′]_ ( _∼_ 21 kpc) and a redshift offset of ∆ _z_ = 0 _._ 010 _±_ 0 _._ 002 (∆ _v_ = 560 _±_ 50 km s _[−]_ [1] or
∆ _d_ = 1 _._ 04 _±_ 0 _._ 20 pMpc). AS2COS0034.1/34.2 have an
angular separation of 5 _._ 0 _[′′]_ ( _∼_ 33 kpc) and a redshift offset of ∆ _z_ = 0 _._ 006 _±_ 0 _._ 002 (∆ _v_ = 310 _±_ 60 km s _[−]_ [1] or
∆ _d_ = 0 _._ 52 _±_ 0 _._ 20 pMpc). The estimated lower limits are
6 _._ 4 [+2] _−_ 1 _[.]_ _._ [3] 8 _[×]_ [10] [12] [ M] _[⊙]_ [for ASCOS0001 and 0] _[.]_ [8] [+0] _−_ 0 _[.]_ _._ [6] 4 _[×]_ [10] [12] [ M] _[⊙]_
for AS2COS0034, and they are consistent with the halo
masses derived from the rotation velocities of the gas
disks (Figure 8(a)).


4. DISCUSSION


4.1. _Nature_ _of_ _high-redshift_ _SMGs_


We discuss the nature of _z_ _>_ 4 bright SMGs in a cosmological context. By comparing with predictions from
a ΛCDM model, we estimate the duty cycle, baryon conversion efficiency and contribution to the cosmic SFRD
of the high-redshift SMGs with the full COSMOS survey
volume of 2 _._ 2 _×_ 10 [6] cMpc [3] .
In Figure 8(a), we plot the cumulative number density of the five [C ii] emitting SMGs and the _z_ = 4 _._ 6 halo
mass function from Angulo et al. (2012). We also show
1- _σ_ uncertainty of halo mass function comes from the
cosmic variance (Mo & White 2002; Moster et al. 2011).
We find that the 50–100% halos at _z_ = 4 _._ 6 with a mass
of _M_ _h_ ≳ 4 _×_ 10 [12] M _⊙_ host SMGs. Such a high duty
cycle for bright SMGs could be explained by continuous
rapid gas accretion in massive, high-redshift halos or by

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 9


**Figure** **8.** ( **a** ) Cumulative number density of dark matter halos for the three [C ii] emitting SMGs (filled circles) at _z_ = 4 _._ 6 and
two candidates (open circles) calculated using a survey volume of 2 _._ 2 _×_ 10 [6] cMpc [3] . We plot two cases: where the five SMGs
reside in individual halos (red) and where two SMG pairs share common halos (blue). The black and green curves show the
halo mass functions at _z_ = 4 _._ 6 and _z_ = 0 predicted from a ΛCDM model (Angulo et al. 2012) with 1- _σ_ uncertainties assuming
cosmic variance (orange shades, Mo & White 2002; Moster et al. 2011). The gray areas show 50–100% and 10–50% of the
number densities. We find that the 50–100% halos with _M_ _h_ _≥_ 4 _×_ 10 [12] M _⊙_ host SMGs at _z_ = 4 _._ 6. In the same survey volume,
the expected number of _∼_ 10 [15] M _⊙_ halos is about unity at _z_ = 0. ( **b** ) The [C ii] cumulative number densities derived from
five SMGs and two bright ( _S_ 870 _µ_ m _≥_ 6 _._ 2mJy) SMGs in the COSMOS survey area. The value from five SMGs is only a lower
limit due to the fact that these are also continuum-selected sources. We show the previous observational constraints at _z_ _∼_ 4 _._ 5
(Swinbank et al. 2012; Cooke et al. 2018). Our result constrains the bright end of the luminosity function at _z_ = 4 _._ 6. From
the comparison with the model luminosity functions (see text), our constraints imply a baryon conversion efficiency (defined as
SFR divided by baryon accretion rate) of _ϵ ∼_ 0 _._ 1 at least for the most luminous source.



a series of short duration starbursts triggered via galaxy
interactions. We note that the latter interpretation is
more consistent with the fact that several of the SMGs
may share common halos, where the proximity of the
neighboring sources would then also explain the triggering of the intense star-formation within these systems.
McAlpine et al. (2019) predicts that mergers are a necessary, but not sufficient, condition to create an SMG:
a massive gas reservoir is also needed to power the intense star-formation activity. Therefore a combination
of triggering by near-continuous mergers and/or rapid
gas fueling by gas accretion might be necessary to produce bright high-redshift bright SMGs with such high
duty cycles.
Owing to the large survey volume of AS2COSMOS,
we constrain _z_ _∼_ 4 _._ 6 [C ii] luminosity function brighter
than _L_ [C ii] _>_ 3 _×_ 10 [9] _L_ _⊙_ (Figure 8(b)). Above this luminosity, we have confirmed that completeness correction due to our line search is not necessary for our constraints (see Section 3). Here, we calculate the number
densities for two cases, one for the full sample of the
five SMGs, and one with the subset of two SMGs with
_S_ 870 _µ_ m _≥_ 6 _._ 2 mJy. As our continuum survey is complete to the level of 6 _._ 2 mJy, the number density of the
full sample of five SMGs gives only a lower limit due to
the missing fainter-continuum [C ii] emitters in our sur


vey volume. We note that if AS2COS0034.1/34.2 are
not [C ii] emitters, then the number density corresponding to our quoted lower limit should be reduced to 40%
(2/5). With the previous results from Swinbank et al.
(2012) and Cooke et al. (2018) we find that the bright
end of the [C ii] luminosity function gradually decrease
toward _L_ [C ii] _∼_ 10 [10] _L_ _⊙_ .
We compare the [C ii] luminosity function with model
luminosity functions derived from the halo mass function. McBride et al. (2009) predicts that the mean
baryon accretion rate _⟨M_ [˙] _⟩_ into a halo as a function of
virial mass _M_ vir and redshift _z_ is given by the following
equation,



_×_ (1 + 1 _._ 17 _z_ ) ~~�~~ Ω M (1 + _z_ ) [3] + Ω Λ


Where _f_ baryon is the baryon-to-dark matter ratio of
_∼_ 1 _/_ 6. The difference of _⟨M_ [˙] _⟩_ in the corresponding
halo mass range is less than 20% across the literature
(McBride et al. 2009; Dekel et al. 2009; Goerdt et al.
2015). We convert the halo masses to the baryon accretion rates with Equation 1, and calculate SFRs assuming
that accreted gas become into stars with baryon conversion efficiencies of _ϵ_ = 0 _._ 01 _,_ 0 _._ 1 _,_ 1 _._ 0. This baryon con


(1)



_M_ vir
_⟨M_ [˙] _⟩_ = _f_ baryon _×_ 42
� 10 [12] _M_ _⊙_



� 1 _._ 127

10 Mitsuhashi et al.



**Figure** **9.** The cosmic star-formation rate density (SFRD,
Madau & Dickinson 2014) and the contribution from bright
( _S_ 870 _µ_ m _≥_ 6 _._ 2 mJy) SMGs. The red filled circle shows
the SFRD derived from two brightest SMGs in this survey (AS2COS0001.1/6.1). The blue square and curve show
the previous observational constraints from _z_ _∼_ 4 _._ 5 [C ii]
emitting SMGs and _z_ = 1–6 SMGs with _S_ 870 _µ_ m _≥_ 6 _._ 2 mJy
(Cooke et al. 2018; Dudzeviˇci¯ut˙e et al. 2020). We estimate
that the contribution of bright continuum-detected SMGs to
the cosmic star-formation rate density is _≃_ 2% at _z_ = 4 _._ 6.


version efficiency is defined as SFR divided by baryon
accretion rate (c.f., Behroozi et al. 2013, 2019). With
the SFRs, we calculate _L_ [C ii] from the following relation
in De Looze et al. (2014).


log SFR = _−_ 7 _._ 06 + 1 _._ 00 _×_ log _L_ [C ii] (2)


We note that this conversion includes a 1- _σ_ dispersion
of 0 _._ 27 dex (shaded areas in Figure 8(b)). We find that
the model luminosity function with a baryon conversion
efficiency of _ϵ_ _∼_ 0 _._ 1 agrees well with the observed luminosity function at least at the bright end (where our
survey is likely complete). The inferred baryon conversion efficiency of _ϵ_ _∼_ 0 _._ 1 is similar to that estimated
for normal star-forming galaxies with halo masses of
_M_ _h_ _∼_ 10 [12] M _⊙_, although at lower redshifts _z_ _∼_ 2,
(Behroozi et al. 2013), which could also have a high
duty cycle of _>_ 50% (Daddi et al. 2005) and have been
claimed to be fed by smooth gas accretion (Dekel et al.
2009). The halos with a mass of _M_ _h_ ≳ 4 _×_ 10 [12] M _⊙_
at _z_ = 4 _._ 6 are expected to have a smooth gas accretion
rate of ≳ 800 M _⊙_ yr _[−]_ [1], which is about half of the total
baryon accretion rate (Goerdt et al. 2015). Thus the gas
accretion for such halos could be sufficient to achieve the
high SFR seen in the SMGs. Of course this does not rule
out gas accretion through mergers especially given that
four of our five targets are potentially close pairs.
We estimate the contribution of the bright SMGs
at _z_ = 4 _._ 6 to the cosmic star-formation rate density
(SFRD). The contribution of dust-obscured galaxies to
the cosmic SFRD is less well constrained at _z_ _>_ 4 (e.g.,



Madau & Dickinson 2014; Swinbank et al. 2014; Casey
et al. 2018; Zavala et al. 2018; Dudzeviˇci¯ut˙e et al. 2020).
The number density and luminosity of [C ii] emitters
provide robust lower limits on the SFRD at this epoch.
We calculate the SFRD of SMGs based on the two bright
SMGs for which our survey is complete above its flux
level of _S_ 870 _µ_ m _≥_ 6 _._ 2 mJy across the survey volume
(Figure 9). We convert [C ii] luminosities to SFR with
Equation 2. Here, the error is dominated by the uncertainties from the _L_ [C ii] –SFR conversion. We confirm
that the [C ii]-based SFRs are consistent with those derived from the dust continuum assuming the relation in
Dudzeviˇci¯ut˙e et al. (2020).
The contribution of the bright continuum-detected
SMGs to the total SFRD is _≃_ 2 % at _z_ = 4 _._ 6. This
is comparable with the contribution of dust continuum
selected SMGs presented in previous works when we use
the same flux cutoff ( _S_ 870 _µ_ m _≥_ 6 _._ 2 mJy, Cooke et al.
2018; Dudzeviˇci¯ut˙e et al. 2020). In contrast, Zavala
et al. (2018) claimed that the contribution of dustobscured galaxies at _z_ _>_ 4 is _∼_ 35–85% based on an
ALMA 3-mm survey. The apparent lower contribution
of the bright SMGs may come from our high flux cutoff. The flux cutoff of _S_ 870 _µ_ m _≥_ 6 _._ 2 mJy corresponds to
SFR = 330 M _⊙_ yr _[−]_ [1] (Dudzeviˇci¯ut˙e et al. 2020), which
is _∼_ 4 times higher than the flux limit in Zavala et al.
(2018, assuming modified black body with _T_ _d_ = 35 K
and _β_ = 1 _._ 8). In addition, as extensively discussed by
Zavala et al. (2018), their sample may also be biased due
to the survey including sources associated with the primary targets in the archival fields or due to synchrotron
contributions to their 3-mm fluxes. We find that the
cosmic SFRD can be reproduced when we integrate our
model of [C ii] luminosity function with _ϵ_ _∼_ 0 _._ 1 down
to _L_ [C ii] = 10 [7] _[.]_ [5] _L_ _⊙_ and convert the [C ii] luminosity
density to SFRD using the Equation 2. This indicates
that we need at least _∼_ 100 times deeper observations to
place a meaningful constraint to the cosmic SFRD from

[C ii] luminosity function.


4.2. _SMG_ _large-scale_ _structure_ _and_ _the_ _descendant_


The rough alignment of the five SMGs apparent in
Figure 2 may suggest that simultaneous star-formation
activity is occuring in massive halos along the cosmic
web. Numerical simulations predict that more than 90%
of dark matter is in the form of un-virialized filamentary
large scale structure at _z_ _∼_ 5 (Haider et al. 2016).
The scale of the SMG-traced structure is comparable
with expected size of protoclusters at _z_ = 4 _._ 6 (Chiang
et al. 2013). Numerical simulations suggest that most
halos with a mass of _M_ _h_ ≳ 2 _×_ 10 [12] M _⊙_ at _z_ = 4 _._ 6
evolve into a _M_ _h_ ≳ 10 [15] M _⊙_ halo by _z_ = 0 (e.g., Zhao
et al. 2009), which corresponds to the present day’s most
massive cluster. As shown in Figure 8(a), the expected
number of _M_ _h_ _∼_ 10 [15] M _⊙_ halos is about unity in our
survey volume at _z_ = 0. The present-day _∼_ 10 [15] M _⊙_ halos are expected to have a maximum baryon conversion

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 11



efficiency of _ϵ_ _∼_ 0 _._ 1 at _z_ _∼_ 4–7 (Behroozi et al. 2013),
which is consistent with our findings (see Section 4.1).
We suggest, therefore, that we are witnessing efficient,
synchronized star formation in massive galaxies, driven
by mergers and potentially smooth gas accretion, within
a massive protocluster environment at _z_ _∼_ 4 _._ 6 when the
Universe was only 10% of its current age.


5. SUMMARY


We detected emission lines from six SMGs based on

ALMA S2COSMOS Band 7 observations of 184 luminous submillimeter sources with _S_ 850 _µ_ m _≥_ 6 _._ 2 mJy in
the full 1 _._ 6 deg [2] COSMOS field (Simpson et al. 2020).
Among these, four SMGs have been confirmed to be

[C ii](157.74 _µ_ m) emitters at _z_ = 4 _._ 60–4 _._ 64 by independent detections of [12] CO( _J_ =5–4) emission. The remaining two SMGs are also likely to be [C ii] emitters at
_z_ = 4 _._ 62 from their line equivalent widths and multiwavelength spectral energy distributions. Four of the
six SMGs are near-infrared blank SMGs. After excluding one SMG whose emission line is falling at the edge of
spectral window, all line emitting SMGs show clear velocity gradients along the major axes of their [C ii] emission, consistent with gas disks with rotation velocities of
330–550 km s _[−]_ [1] . We estimate that they have individual
dark matter halo masses of 2–8 _×_ 10 [12] M _⊙_, a 50–100%
duty cycle, and a baryon conversion efficiency (SFR relative to baryon accretion rate) of _ϵ ∼_ 0 _._ 1 and contribute
_≃_ 2% to the total SFRD at this redshift. Five SMGs are
concentrated within a 16 _×_ 4 _×_ 12 cMpc [3] region and likely



evolve into members of a massive ( _∼_ 10 [15] M _⊙_ ) cluster
at _z_ _∼_ 0. Our work demonstrates that the combination
of wide-field single dish survey and ALMA follow-up is a
powerful method to investigate the rapid formation process of massive galaxies within the cosmic web at _z_ _>_ 4.


ACKNOWLEDGMENTS


We would like to thank the anonymous referee
for a thoughtful and constructive report which improved the content and clarity of this paper. We
also thank to C. Casey, H. Nagai and T. Michiyama
for the useful discussion and information. YM, HU
and HI acknowledge support from JSPS KAKENHI
Grant (17H04831, 17KK0098, 19H00697, 17K14252,
20H01953 and 19K23462). IRS, JMS, UD, AMS &
JEB acknowledge support from STFC(ST/T000244/1).
CCC acknowledge support from the Ministry of Science and Technology of Taiwan (MOST 109-2112-M001-016-MY3). This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00034.S,
#2015.1.00137.S, #2015.1.00568.S, #2015.1.01074.S,
#2016.1.01604.S, #2016.1.00478.S, #2016.1.00463.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together
with NRC (Canada) and NSC and ASIAA (Taiwan),
in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. Data analysis were carried out on common
use data analysis computer system at ADC/NAOJ.



An, F. X., et al. 2019, ApJ, 886, 48



REFERENCES


Capak, P. L., et al. 2015, Nature, 522, 455



Angulo, R. E., Springel, V., White, S. D. M., Jenkins, A.,

Baugh, C. M., & Frenk, C. S. 2012, MNRAS, 426, 2046


Aretxaga, I., et al. 2011, MNRAS, 415, 3831


Barger, A. J., Cowie, L. L., & Richards, E. A. 2000, AJ,

119, 2092


Barger, A. J., Cowie, L. L., Sanders, D. B., Fulton, E.,

Taniguchi, Y., Sato, Y., Kawara, K., & Okuda, H. 1998,

Nature, 394, 248


Barkana, R., & Loeb, A. 2001, PhR, 349, 125


Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C.

2019, MNRAS, 488, 3143


Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013, ApJ,

770, 57


Birkin, J. E., et al. 2020, arXiv e-prints, arXiv:2009.03341


Blain, A. W., Smail, I., Ivison, R. J., & Kneib, J. P. 1999,

MNRAS, 302, 632


Brauher, J. R., Dale, D. A., & Helou, G. 2008, ApJS, 178,

280


Brisbin, D., et al. 2017, A&A, 608, A15



Carilli, C. L., & Yun, M. S. 1999, ApJL, 513, L13


Carniani, S., Maiolino, R., Smit, R., & Amor´ın, R. 2018,

ApJL, 854, L7


Carniani, S., et al. 2013, A&A, 559, A29


Casey, C. M. 2016, ApJ, 824, 36


Casey, C. M., et al. 2013, MNRAS, 436, 1919


Casey, C. M., Narayanan, D., & Cooray, A. 2014, PhR,

541, 45


Casey, C. M., et al. 2018, ApJ, 862, 77


Chen, C.-C., et al. 2016, ApJ, 820, 82


Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ,

779, 127


Cooke, E. A., Smail, I., Stach, S. M., Swinbank, A. M.,

Bower, R. G., Chen, C.-C., Koyama, Y., & Thomson,

A. P. 2019, MNRAS, 486, 3047


Cooke, E. A., et al. 2018, ApJ, 861, 100


Daddi, E., et al. 2005, ApJL, 631, L13


De Breuck, C., et al. 2014, A&A, 565, A59


De Looze, I., et al. 2014, A&A, 568, A62

12 Mitsuhashi et al.



Dekel, A., et al. 2009, Nature, 457, 451

Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016,

A&A, 594, A77

Dressler, A. 1980, ApJ, 236, 351

Dudzeviˇci¯ut˙e, U., et al. 2020, MNRAS, 494, 3828

Dutton, A. A., & Macci`o, A. V. 2014, MNRAS, 441, 3359

Faure, C., et al. 2008, ApJS, 176, 19

Gallazzi, A., Charlot, S., Brinchmann, J., & White, S.

D. M. 2006, MNRAS, 370, 1106

Goerdt, T., Ceverino, D., Dekel, A., & Teyssier, R. 2015,

MNRAS, 454, 637

Guzzo, L., et al. 2007, ApJS, 172, 254

Haider, M., Steinhauser, D., Vogelsberger, M., Genel, S.,

Springel, V., Torrey, P., & Hernquist, L. 2016, MNRAS,

457, 3024

Harikane, Y., et al. 2020, ApJ, 896, 93

Hashimoto, T., et al. 2019, PASJ, 71, 71

Hasinger, G., et al. 2018, ApJ, 858, 77

Hayatsu, N. H., et al. 2017, PASJ, 69, 45

Hickox, R. C., et al. 2012, MNRAS, 421, 284

Hill, R., et al. 2020, MNRAS, 495, 3124

Hodge, J. A., Carilli, C. L., Walter, F., de Blok, W. J. G.,

Riechers, D., Daddi, E., & Lentati, L. 2012, ApJ, 760, 11

Hodge, J. A., et al. 2013, ApJ, 768, 91

Hughes, D. H., et al. 1998, Nature, 394, 241

Iono, D., et al. 2006, ApJL, 645, L97

Jim´enez-Andrade, E. F., et al. 2020, ApJ, 890, 171

Jones, G. C., et al. 2017, ApJ, 850, 180

Kodama, T., Smail, I., Nakata, F., Okamura, S., & Bower,

R. G. 2001, ApJL, 562, L9

Koekemoer, A. M., et al. 2007, ApJS, 172, 196

Kohandel, M., Pallottini, A., Ferrara, A., Zanella, A.,

Behrens, C., Carniani, S., Gallerani, S., & Vallini, L.

2019, MNRAS, 487, 3007

Koyama, Y., et al. 2013, MNRAS, 434, 423

Laigle, C., et al. 2016, ApJS, 224, 24

Lemaux, B. C., et al. 2018, A&A, 615, A77

Lilly, S. J., et al. 2007, ApJS, 172, 70

Liu, D., et al. 2019, ApJS, 244, 40

Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415

Maiolino, R., et al. 2015, MNRAS, 452, 54

McAlpine, S., et al. 2019, MNRAS, 488, 2440

McBride, J., Fakhouri, O., & Ma, C.-P. 2009, MNRAS, 398,

1858

McCracken, H. J., et al. 2012, A&A, 544, A156

McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, Astronomical Society of the Pacific

Conference Series, Vol. 376, CASA Architecture and

Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell 127

Miller, T. B., et al. 2018, Nature, 556, 469



Miller, T. B., Chapman, S. C., Hayward, C. C., Behroozi,

P. S., Bradford, C. M., Willott, C. J., & Wagg, J. 2016,

arXiv e-prints, arXiv:1611.08552

Miller, T. B., Chapman, S. C., Hayward, C. C., Behroozi,

P. S., Bradford, M., Willott, C. J., & Wagg, J. 2020,

ApJ, 889, 98

Mo, H. J., & White, S. D. M. 2002, MNRAS, 336, 112

Moster, B. P., Somerville, R. S., Newman, J. A., & Rix,

H.-W. 2011, ApJ, 731, 113

Navarro, J. F., Frenk, C. S., & White, S. D. M. 1997, ApJ,

490, 493

Oliver, S. J., et al. 2012, MNRAS, 424, 1614

Oteo, I., et al. 2018, ApJ, 856, 72

Ouchi, M., et al. 2013, ApJ, 778, 102

Pentericci, L., et al. 2016, ApJL, 829, L11

Posti, L., Fraternali, F., & Marasco, A. 2019, A&A, 626,

A56

Riechers, D. A., et al. 2014, ApJ, 796, 84

Romano-D´ıaz, E., Shlosman, I., Choi, J.-H., & Sadoun, R.

2014, ApJL, 790, L32

Sanders, D. B., et al. 2007, ApJS, 172, 86

Scott, K. S., et al. 2008, MNRAS, 385, 2225

Scott, K. S., et al. 2010, MNRAS, 405, 2260

Silva, L., Granato, G. L., Bressan, A., & Danese, L. 1998,

ApJ, 509, 103

Simpson, J. M., et al. 2020, MNRAS, 495, 3409

Simpson, J. M., et al. 2019, ApJ, 880, 43

Simpson, J. M., et al. 2014, ApJ, 788, 125

Smail, I., et al. 2020, arXiv e-prints, arXiv:2010.02250

Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5

Smail, I., Ivison, R. J., Owen, F. N., Blain, A. W., &

Kneib, J. P. 2000, ApJ, 528, 612

Smail, I., Smith, G. P., & Ivison, R. J. 2005, ApJ, 631, 121

Smail, I., Swinbank, A. M., Ivison, R. J., & Ibar, E. 2011,

MNRAS, 414, L95

Smit, R., et al. 2018, Nature, 553, 178

Smolˇci´c, V., et al. 2017, A&A, 602, A1

Stach, S. M., et al. 2019, MNRAS, 487, 4648

Swinbank, A. M., et al. 2012, MNRAS, 427, 1066

Swinbank, A. M., et al. 2014, MNRAS, 438, 1267

Swinbank, A. M., et al. 2010, Nature, 464, 733

Tacconi, L. J., et al. 2008, ApJ, 680, 246

Tadaki, K., et al. 2018, Nature, 560, 613

Tamura, Y., et al. 2009, Nature, 459, 61

Tamura, Y., et al. 2019, ApJ, 874, 27

Umehata, H., et al. 2019, Science, 366, 97

Umehata, H., et al. 2020, A&A, 640, L8

Umehata, H., et al. 2014, MNRAS, 440, 3462

Umehata, H., et al. 2015, ApJL, 815, L8

Bright [C ii] emitting SMGs at _z_ _∼_ 4.6 13



Venemans, B. P., Walter, F., Zschaechner, L., Decarli, R.,


De Rosa, G., Findlay, J. R., McMahon, R. G., &


Sutherland, W. J. 2016, ApJ, 816, 37


Wagg, J., Carilli, C. L., Wilner, D. J., Cox, P., De Breuck,


C., Menten, K., Riechers, D. A., & Walter, F. 2010,


A&A, 519, L1


Wang, R., et al. 2013, ApJ, 773, 44


Wang, T., et al. 2019, Nature, 572, 211


Wilkinson, A., et al. 2017, MNRAS, 464, 1380



Willott, C. J., Carilli, C. L., Wagg, J., & Wang, R. 2015,

ApJ, 807, 180

Willott, C. J., Omont, A., & Bergeron, J. 2013, ApJ, 770,

13

Younger, J. D., et al. 2009, ApJ, 704, 803

Yun, M. S., et al. 2015, MNRAS, 454, 3485

Yun, M. S., et al. 2012, MNRAS, 420, 957

Zavala, J. A., Casey, C. M., da Cunha, E., Spilker, J.,

Staguhn, J., Hodge, J., & Drew, P. M. 2018, ApJ, 869, 71

Zhao, D. H., Jing, Y. P., Mo, H. J., & B¨orner, G. 2009,

ApJ, 707, 354


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "NOEMA Band 1 12CO(5-4) detections at z = 4.63 for AS2COS0001.1/1.2",
  "failed_quote": "Recently, Jim´enez-Andrade et al. (2020) observed the two line emitters (AS2COS0001.1/1.2) with NOrthern Extended Millimeter Array (NOEMA) Band 1 and detected [12] CO(5–4) lines at _z_ = 4 _._ 63 (see also Simpson et al. 2020)."
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "Image-plane: iterative 2-σ clipped channel average per spatial pixel for line search; re-calculated excluding emission line channels for final line cubes",
  "failed_quote": "To estimate the continuum level excluding emission lines, we average all channels for each spatial pixel in the binned data cubes using 2- _σ_ clipping. We iterate this procedure until the 2- _σ_ clipping converges, and subtract the resulting continuum values from the data cubes."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "Iterative 2-σ clipped average per spatial pixel for continuum subtraction",
  "failed_quote": "To estimate the continuum level excluding emission lines, we average all channels for each spatial pixel in the binned data cubes using 2- _σ_ clipping. We iterate this procedure until the 2- _σ_ clipping converges, and subtract the resulting continuum values from the data cubes."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Compare S_870µm / S_3GHz flux ratios with SMG SED templates as a redshift indicator, and compare observed-frame emission line equivalent widths (EW) with confirmed z ~ 4.4-4.6 [C II] emitters, intermediate-z high-J CO lines, and z ~ 9 [O III] lines.",
  "failed_quote": "Moreover, the emission lines of AS2COS0034.1/34.2 have observed-frame equivalent widths of EW = 4 _._ 5 _±_ 0 _._ 8 and 5 _._ 9 _±_ 1 _._ 0 _µ_ m, which are similar to the [C ii] EW of the _z_ _∼_ 4 _._ 4 SMGs (1.8 and 4.9 _µ_ m) from Swinbank et al. (2012)"
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "All five analyzed [C II] emitters show clear velocity gradients along their major axes consistent with rotating gas disks.",
  "failed_quote": "All the five emitters show clear velocity gradients on the moment 1 maps. Since the directions of these velocity gradients match the major axis position angles, they are likely to be rotating gas disks."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The kinematics of all five z ~ 4.6 SMGs are consistent with rotating gas disks.",
  "failed_quote": "All the five emitters show clear velocity gradients on the moment 1 maps. Since the directions of these velocity gradients match the major axis position angles, they are likely to be rotating gas disks."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Excluded AS2COS0002.1 because its emission line falls at the edge of the spectral window, preventing measurement of total line flux or velocity width.",
  "failed_quote": "We exclude one line emitter (AS2COS0002.1) because we cannot measure the total line flux or line velocity width of the emission line as it falls at the edge of the spectral window [1] (see Figure 2)."
 }
]
```
