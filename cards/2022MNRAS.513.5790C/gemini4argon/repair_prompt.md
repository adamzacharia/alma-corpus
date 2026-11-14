# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.513.5790C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–10 (2015) Preprint 6 May 2022 Compiled using MNRAS L [A] TEX style file v3.0

## **Variable structure in the PDS 70 disc and uncertainties in** **radio-interferometric image restoration**


Simon Casassus, [1] _[,]_ [2] _[,]_ [3] _[⋆]_ Miguel Cárcamo, [4] _[,]_ [5] _[,]_ [6]

1 _Departamento_ _de_ _Astronomía,_ _Universidad_ _de_ _Chile,_ _Casilla_ _36-D,_ _Santiago,_ _Chile_
2 _Facultad_ _de_ _Ingeniería_ _y_ _Ciencias,_ _Universidad_ _Adolfo_ _Ibáñez,_ _Av._ _Diagonal_ _las_ _Torres_ _2640,_ _Peñalolén,_ _Santiago,_ _Chile_
3 _Data_ _Observatory_ _Foundation,_ _Chile_
4 _Jodrell_ _Bank_ _Centre_ _for_ _Astrophysics,_ _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _Manchester,_
_Alan_ _Turing_ _Building,_ _Oxford_ _Road,_ _Manchester,_ _M13_ _9PL,_ _UK_
5 _University_ _of_ _Santiago_ _of_ _Chile_ _(USACH),_ _Faculty_ _of_ _Engineering,_ _Computer_ _Engineering_ _Department,_ _Chile_
6 _Center_ _for_ _Interdisciplinary_ _Research_ _in_ _Astrophysics_ _and_ _Space_ _Exploration_ _(CIRAS),_ _Universidad_ _de_ _Santiago_ _de_ _Chile_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**


The compact mm-wavelength signal in the central cavity of the PDS 70 disc, revealed by deep ALMA observations,
is aligned with unresolved H _α_ emission, and is thought to stem from a circum-planetary disc (CPD) around PDS 70c.
We revisit the available ALMA data on PDS 70c with alternative imaging strategies, and with special attention to
uncertainties and to the impact of the so-called “JvM correction”, which is thought to improve the dynamic range of
restored images. We also propose a procedure for the alignment and joint imaging of multi-epoch visibility data. We
find that the JvM correction exaggerates the peak signal-to-noise of the data, by up to a factor of 10. In the case of
PDS 70, we recover the detection of PDS 70c from the July 2019 data, but only at 8 _σ_ . However, its non-detection
in Dec. 2017 suggests that PDS 70c is variable by at least 42% _±_ 13% over a 1.75 yr time-span, so similar to models
of the H _α_ variability. We also pick up fine structure in the inner disc, such that its peak is offset by _∼_ 0 _[′′]_ _._ 04 from
the disc centre. The inner disc is variable too, which we tentatively ascribe to Keplerian rotation as well as intrinsic
morphological changes.


**Key** **words:** techniques: interferometric – protoplanetary discs – planets and satellites: formation – stars: individual:
PDS 70



**1** **INTRODUCTION**


The accretion of giant planets in circum-stellar discs is
thought to be regulated by a circum-planetary disc (CPD),
which is fed by intricate flows inside planetary wakes
(e.g. Szulágyi & Ercolano 2020). However, CPD detections
have been remarkably elusive, except for the compact rovibrational CO signal detected in the central cavity of
HD 100546 by (Brittain et al. 2019), or the near-IR blackbody component required to account for the spectral energy
distribution of PDS 70b (Christiaens et al. 2019). In general
such CPDs are expected to be faint compact sources, up to
one Hill radius wide and surrounded by complex structures
in the parent disc (e.g. Szulágyi et al. 2018). The search for
CPDs with ALMA thus requires bringing the instruments to
its limits, and a very good knowledge of the uncertainties in
the resulting images so as to pick-up genuine signal.
Long-baseline ALMA observations of the PDS 70 disc revealed the detection of a compact source inside the cen

_⋆_ E-mail: simon@das.uchile.cl


© 2015 The Authors



tral cavity(Benisty et al. 2021), closely aligned with unresolved H _α_ signal probably associated to an accreting protoplanet (i.e. PDS 70c, Haffert et al. 2019). The compact
mm-wavelength signal may thus stem from a CPD around
PDS 70c (Benisty et al. 2021). However, the data analysis
rests on the “JvM correction” (Jorsater & van Moorsel 1995;
Czekala et al. 2021), an image restoration procedure that is
thought to improve dynamic range. Image restoration, applicable to all synthesis imaging techniques, allows to convey
uncertainties, and to recover faint signal that may have been
missed by model images.


The direct detection of a CPD, thanks to deep ALMA
observations, is a momentous achievement in planetary sciences, whose relevance motivates us to revisit these data with
alternative synthesis imaging tools. Here we perform nonparametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the
more commonly used clean algorithm (Högbom 1974; Rau
& Cornwell 2011). We give special attention to the alignment
of multi-epoch visibility data, and to the impact of the JvM

correction.

2 _S._ _Casassus_ _&_ _M._ _Cárcamo_


Our approach to the alignment of the multi-epoch visibility
data is described in Sec. 2, and is applied to uvmem imaging of PDS 70 in Sec. 3. Sec. 4 summarizes our results. Appendix A describes the standard techniques of image restoration and visibility gridding, before showing that the JvM correction exaggerates the sensitivity of restored images.


**2** **ALIGNMENT** **OF** **VISIBILITY** **DATA**


Datasets obtained with different source acquisitions, i.e.
multi-epoch observations, may have different absolute flux
scales or be affected by different pointing errors. For instance, the flux calibration accuracy for ALMA is thought
to be around _∼_ 10%, and the phase center accuracy (absolute
positional accuracy) is, very approximately, about 1/10 the
size of the clean beam major axis (see for instance Remijan
et al. 2019). In order to restore images using concatenated
datasets, it is necessary to align them. It is also necessary to
scale them in flux, as otherwise different flux calibrations will
lead to stronger residuals.
Here we propose to align such datasets in the _uv−_ plane,
assuming that the source is not variable in time. The result
of our procedure is similar to that of joint self-calibration
(described in Sec. 3.1), but it restricts the number of unknowns to only a single position shift and a flux scale factor, while self-calibration adjusts time-series for the antenna
gains. Another difference is that self-calibration requires a
bright source to define an adequate self-calibration model.
We describe our procedure for two datasets, labeled _S_ and
_L_ anticipating the application to PDS 70, where the datasets
correspond to different array configurations, with shorter and
longer baselines [1] . We extract subsets of each dataset with exactly the same spectral domains in LSRK. We then gridd each
dataset to a common _uv−_ grid, in natural weights, so according to Eqs. A3 and A5 (which are implemented in the pyral


ysis [2] software package). This results in visibilities _V_ ˜ _k_ _[S]_ _N_
� � _k_



_k_ =1
and _V_ ˜ _k_ _[L]_ _N_ [for] [the] [short] [and] [long] [baseline] [datasets,] [re-]
� � _k_ =1 [,]

spectively. The common _uv_ -grid is set by the shortest and
longest baselines. We then aligned each pair by shifting _V_ [˜] _[S]_,
i.e. by minimising




[for] [the] [short] [and] [long] [baseline] [datasets,] [re-]
_k_ =1 [,]



the range where the radial profiles are both above 1/10 their
peak. See Sec. 3.1 below for an example application and for
independent checks on the alignment procedure. This visibility alignment procedure is implemented in the package
VisAlign [3] .


**3** **APPLICATION** **TO** **PDS 70**


**3.1** **Imaging**


We refer to Long et al. (2018), Keppler et al. (2019), Isella
et al. (2019) and Benisty et al. (2021) for a description of the
observations. We followed the same procedures for the extraction of the continuum visibility data, and adopt the same
nomenclature as in Benisty et al. (2021) to refer to the various
datasets. In summary, we used the datasets corresponding to
the following ALMA programmes: `2015.1.00888.S`, from August 2016, with short baselines (15 m to 1.5 km) and referred
to as SB16; `2017.A.00006.S`, from Dec. 2017, with intermediate baselines (15 m and 6.9 km) and referred to as IB17; and
`2018.A.00030.S`, from July 2019, with long baselines (92 m
to 8.5 km) and referred to as LB19.
Provided with the continuum visibility data, we proceeded
to self-calibrate (e.g. Cornwell & Fomalont 1999) each dataset
independently. For bright sources this procedure improves
calibration and may allow reaching thermal noise in the restored image. Given that Benisty et al. (2021) used the JvM
correction, in order to set a comparison point before investigating alternative imaging strategies, we first applied the
standard self-calibration procedure, as implemented in casa,
and composed of successive iterations of the tasks `tclean`,
`gaincal` and `applycal` . We combined all spectral windows
(spws), proceeding as in Benisty et al. (2021), and reached a
peak signal to noise ratio (PSNR) in the final restored images
of 36.3 using Briggs weighting with _r_ = 2.
As an alternative imaging strategy, we used the uvmem
package to replace the `tclean` model in the casa selfcal loop
(see Casassus et al. 2018, 2019a, 2021b, for more details on
uvmem and recent applications to ALMA data of protoplanetary discs). We used an elliptical mask enclosing the source
that restricts the number of free parameters (as in Casassus
et al. 2021b, who used Keplerian masks for line data). For
very bright and compact sources, as in SB16 or IB17, this
mask is redundant in terms of the final PSNR, but it helps in
case of lower dynamic range, as for LB19. For all datasets, we
used a pure least-squared ( _χ_ [2] ) optimization, regularized only
by the requirement of image positivity (i.e. no entropy term
was applied). We then proceeded to self-calibrate the data
using a special purpose programming framework, OOselfcal [4], which is essentially a wrapper for casa tasks `gaincal`
and `applycal` and any choice of imager (in this case uvmem).
OOselfcal allows execution with as little user interaction as

possible. This framework starts with phase-calibration only,
in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s). These
iterations are interrupted when the PSNR [5] decreases, and the
self-calibrated visibility dataset is reverted to the calibration


3 see Data Availability
4 see Data Availability
5 In our framework this PSNR is calculated as the ratio of peak



_χ_ [2] align [(] _[α]_ _R_ _[, δ⃗x]_ [) =]


where



_N_
� _W_ _k_ [align] _∥V_ [˜] _k_ _[L]_ _[−]_ _[V]_ [˜] _k_ _[Lm]_ _∥_ [2] _,_ (1)


_k_ =1



_V_ ˜ _k_ _[Lm]_ = _α_ _R_ _e_ _[i]_ [2] _[π δ⃗x][·][⃗u]_ _[k]_ _V_ [˜] _k_ _[S]_ _[,]_ (2)


corresponds to a spatial shift in origin by _δ⃗x_ and to a scaling
of the absolute fluxes for _V_ [˜] _[S]_ by _α_ _R_ _∈ℜ_ . The weights are

_W_ _k_ [align] = _WW_ _k_ _[S]_ _k_ _[S]_ [+] _[W][ W]_ _k_ _[ L]_ _k_ _[ L]_ _,_ (3)


where _W_ _k_ _[S]_ and _W_ _k_ _[L]_ are each given by Eq. A4, for both
datasets. The overlap in _uv_ -radii, over which the optimisation was carried out, was determined by taking azimuthal
averages in the gridded weights _W_ _[S]_ and _W_ _[L]_, and selecting


1 this alignment procedure can of course be applied to datasets
acquired with the same configuration
2 see Data Availability


MNRAS **000**, 1–10 (2015)

_Image_ _restoration_ _and_ _variability_ _in_ _PDS 70_ 3



tables that yielded the highest PSNR. The phase-calibration
stage is then followed by a single loop of amplitude and phase
self-calibration, also tested for improvement using the PSNR.
For LB19 the phase-calibration progressed until the first iteration, which was enough to reach a PSNR of 56 with _r_ = 2.
For SB16, a PSNR of 266 ( _r_ = 2)was reached after two phase
calibration loops. For IB17, a single iteration in phase yielded
a PSNR of 75 ( _r_ = 2).
Having self-calibrated each dataset independently, they
were concatenated for joint imaging. This required alignment
to a common reference dataset, for which we chose LB19,
both for position and absolute flux calibration. The alignment
was achieved in the _uv_ -plane, using VisAlign (as described
in Sec. 2). We therefore assume that the bulk of PDS 70 is
not variable between the two epochs [6] . We extracted a frequency domain common to all 3 datasets, in LSRK, and then
aligned each pair SB16/LB19 and IB17/LB19. The common
_uv_ -grids correspond to 2048 _×_ 2048 images with pixel sizes of
3 mas and 4 mas, respectively. Fig. 1 shows the visibility amplitudes for the grid corresponding to the IB17/LB19 alignment. For the SB16 and LB19 alignment, the common range
in _uv_ -radii extended from 0 _._ 17 _Mλ_ to 0 _._ 47 _Mλ_ . The fit yielded
_δ⃗x_ = ( _−_ 0 _[′′]_ _._ 012 _±_ 0 _[′′]_ _._ 001 _, −_ 0 _[′′]_ _._ 019 _±_ 0 _[′′]_ _._ 001). The flux scale factor was _α_ _R_ = 0 _._ 788 _±_ 0 _._ 004, which is somewhat smaller
than the ratio of flux densities extracted within the mask, of
0 _._ 861 _±_ 0 _._ 004. The LB19 flux density is biased upwards in our
pure _χ_ [2] reconstructions, because of the positive-definite noise
in the model images. Using entropy regularization resulted in
a lower flux density ratio of 0 _._ 77 _±_ 0 _._ 004 (but with stronger
synthesis imaging artifacts, which is why we use the pure _χ_ [2]

versions). For the IB17 and LB19 alignment, _uv_ -range extended from 0 _._ 17 _Mλ_ to 0 _._ 71 _Mλ_, _α_ _R_ = 1 _._ 001 _±_ 0 _._ 002 and
_δ⃗x_ = ( _−_ 0 _[′′]_ _._ 01401 _±_ 0 _[′′]_ _._ 0003 _, −_ 0 _[′′]_ _._ 0203 _±_ 0 _[′′]_ _._ 0004). An absolute
flux scale difference of _∼_ 20% between SB16 and IB17 or LB19
is not surprising for ALMA Band 7 (Francis et al. 2020). The
alternative, that the flux of the disc itself is time-variable, is
unlikely since the flux scales between IB17 and LB19 are consistent, while the time separations between IB17 and SB16,
and between LB19 and IB17, are similar.
The impact of the alignment is summarised in Figs. 2 and
3. Since the source is a fairly axially symmetric disc, albeit
projected on the sky, we rotated and compressed the _uv_ -plane
to compensate for the disc orientation, with an inclination
_i_ = 130 deg and PA = 160 _._ 4 deg (see below).
As the disc of PDS 70 is essentially a ring, we can use the
center of the ring to test the accuracy of our alignment procedure. The MPolarMaps package (Casassus et al. 2021b)
estimates the disc orientation, under the assumption of axial symmetry, by minimizing the azimuthal dispersion of radial intensity profiles. We compare the LB19 image, in its
restored version (see below), with the IB17 model image (see
below). For LB19, the best fit orientation corresponds to
PA= 160 _._ 4 _±_ 0 _._ 08 deg, _i_ = 130 _._ 0 _±_ 0 _._ 06 deg, and a ring center


signal in the restored images to the noise in the whole residual
image, with a field of view of 4 arcsec in the case of PDS 70
6 Since the bulk of the flux density, by far, is dominated by the
outer ring, Keplerian rotation could trace an arc of _∼_ 10 mas in
length, subtending an angle of _∼_ 0.7 deg in azimuth relative to the
star. This is a small angular rotation, that probably does not bias
the alignment procedure, which fits for a scaling factor and a positional translation


|LB19 20.0 40.0 60.0 mJy|Col2|
|---|---|
|LB19<br>b|LB19<br>b|
|b|b|



offset by ∆ _[⃗]_ LB19 = ( _−_ 0 _[′′]_ _._ 0018 _±_ 0 _[′′]_ _._ 0003 _, −_ 0 _[′′]_ _._ 0036 _±_ 0 _[′′]_ _._ 0003)
relative to the phase center. For IB17, we obtained PA=
160 _._ 5 _±_ 0 _._ 18 deg, _i_ = 129 _._ 9 [+0] _−_ 0 _[.]_ _._ [16] 14 [deg,] [and] [a] [ring] [center] [at]

_⃗_
∆ IB17 = ( _−_ 0 _[′′]_ _._ 0032 [+0] _−_ 0 _[′′][′′]_ _[.]_ _._ [0006] 0009 _[,][ −]_ [0] _[′′]_ _[.]_ [0025] _[ ±]_ [ 0] _[′′]_ _[.]_ [0008)] [relative] [to] [the]

phase center. The ring centers ∆ _[⃗]_ LB19 and ∆ _[⃗]_ IB17 coincide
within _∼_ 1 mas, or 1 _._ 5 _σ_, in support of the accuracy of the
_uv_ -plane alignment with VisAlign.
Having aligned all 3 datasets, we proceeded with joint
imaging. We concatenated the visibility data directly, i.e.
with the application of the `statwt` task in CASA to replace the visibility weights by those corresponding to the dispersion of each datum, but without additional modification.
We applied the OOselfcal framework, which yielded improvements for SB16+IB17+LB19 (PSNR=95) and also for
SB16+IB17 (PSNR=94), both after a single round of phase
calibration. The amplitude and phase self-calibration resulted
in an improvement only for SB16+LB19 (PSNR=84). A selection of images resulting from the present imaging procedure is given in Fig. 4.


**3.2** **Results** **and** **discussion**


_3.2.1_ _Noise_ _level_ _in_ _the_ _LB19_ _image_


The noise level reported in Fig. 4a, of 16.4 _µ_ Jy beam _[−]_ [1], appears to match the expected instrumental sensitivity. The
ALMA Observing Tool (OT, provided by the Joint ALMA
Observatory to prepare ALMA proposals) predicts about 6 h
total execution time to reach a noise level of 17 _µ_ Jy beam _[−]_ [1],
under default weather conditions. This seems fairly consistent
with the actual total execution time for the LB19 dataset, of
3.7h, considering that is was carried out under very good
weather conditions (with precipitable water vapour columns
ranging from 0.6 to 0.7 mm). However, the noise level quoted
by Benisty et al. (2021) for the LB19 dataset using Briggs
robustness parameter of 2.0 is only 6.2 _µ_ Jy beam _[−]_ [1], which
according to the OT would require 2 d. We suggest that this
very low noise level is due to the application of the JvM correction (see Sec. A5).


MNRAS **000**, 1–10 (2015)



20.0 40.0 60.0

mJy



0.5 0.0 0.5


u  / M





0.5


0.0


0.5





0.5 0.0 0.5


u  / M



**Figure** **1.** Gridded visibility amplitudes for datasets IB17 (a) and
LB19 (b). The data have been filtered for the common _uv−_ domain,
according to Eq. 3.

4 _S._ _Casassus_ _&_ _M._ _Cárcamo_



20


0


20









40

6


4


2


0


2







0.1 0.2 0.3 0.4 0.5

uv-radius / M


**Figure** **2.** Visibility _uv_ -spectra for SB16 and LB19, and _uv_ -plane
alignment. We plot the deprojected and azimuthally-averaged visibilities of PDS 70, over a common range in _uv−_ radii (see text), with
real parts in **a)** and imaginary parts in **b)** . The total heights of the
shaded regions correspond to the standard deviation of azimuthal
scatter. We do not plot this scatter for the shifted visibilities to
avoid crowding.



20


0


20


4


2


0


2


4










|VR(LB19)<br>VR(IB17)<br>VR(IB17shifted)|Col2|
|---|---|
|||
|||
|VI(LB19)<br>VI(IB17)<br>VI(IB17shifted)|VI(LB19)<br>VI(IB17)<br>VI(IB17shifted)|



0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8

uv-radius / M


**Figure** **3.** Visibility _uv_ -spectra for IB17 and LB19, and _uv_ -plane
alignment. Annotations follow from Fig. 2.



_3.2.2_ _PDS 70c_


As summarised in Fig. 4, we confirm the detection of signal
coincident with PDS 70c. This is best seen in Fig. 4a, with
point-like signal reaching 126 _µ_ Jy beam _[−]_ [1], or 8 _σ_ . We note
that this point source is surrounded by extended emission, in
the form of a filament or spur, that connects with the cavity
wall. This spur is best seen in Fig. 4b, where it is detected at
3 _σ_ . The color map in Fig. 4 is chosen to higlight the faint fea

MNRAS **000**, 1–10 (2015)



tures and the noise, while also tracing the brighter features. A
more standard color map is used in Fig. 5 (the latter version
is easier to compare with the color coding used by Benisty
et al. 2021, and also with ESO press release eso2111b).
Intriguingly, the point source PDS 70c is missing in
LB19+IB17+SB16. In order to test whether this is an effect of averaging different Keplerian rotation phases, we have
de-projected the LB19+SB16 data, transformed the map by
Keplerian rotation over a period of 1.75 yr around a 0.9 _M_ _⊙_
star, re-projected onto the sky plane and averaged the result
with the initial image. Fig. 5 shows that, while PDS 70c is
somewhat fainter in the average than in the initial image, it
is still quite conspicuous.
The absence of PDS 70c in LB19+IB17+SB16 may perhaps reflect that the signal detected in LB19 has been averaged with its absence in IB17. To test this hypothesis we
also imaged SB16+IB17, as shown in Fig. 4d, e and f. The
noise level in Fig. 4e being 31.9 _µ_ Jy beam _[−]_ [1], and since the
data are aligned in position and flux, a 126 _µ_ Jy point source
should have been picked up at 4 _σ_ . Instead, the intensity at
the location of PDS 70c is _−_ 51 _µ_ Jy beam _[−]_ [1] . In order to test
for synthesis imaging limitations due to the vicinity of the
strong and extended emission from the cavity wall, we injected 4 point sources in the residual visibility data, at the
expected location of PDS 70c, and at symmetrical positions
relative to the disc axes. As summarised in Fig. 6, the corresponding restored image is consistent a 126 _µ_ Jy point source
at all 4 locations within 2 _σ_ .

The absence of PDS 70c in IB17 suggests that it is a variable source. Isella et al. (2019) reported the detection of
sub-mm continuum associated to PDS 70c, using the same
dataset, but from their Fig. 8 it seems to be offset northwards of the H _α_ peak. Also, their astrometry is tied to the
central continuum peak, which may be offset from the star
(see below). In the insets of Figs. 4d and e there are indeed filaments, or spurs, protruding away from the cavity edge more
of less at the position of the clump reported by Isella et al.
(2019), but they do not match the position of PDS 70c given
in Benisty et al. (2021). In addition, these spurs are roughly
aligned with the elongated beam in IB17, and they are absent
in LB19, suggesting that they are imaging artefacts.
The non-detection of PDS 70c in IB17 (Fig. 4d) places a
3 _σ_ upper limit on its flux density of 89 _µ_ Jy. Since its flux
in LB19 is (126 _±_ 16 _._ 4) _µ_ Jy beam _[−]_ [1], if we assign the upper
limit flux density to PDS 70c in IB17, then it brightened by
42% _±_ 13% in the interval of _∼_ 1.75 yr between IB17 and LB19.
This might not be so surprising since stellar, and probably
also sub-stellar, accretion is thought to be variable. Indeed,
Szulágyi & Ercolano (2020) report a variability of the H _α_
flux from CPDs in the range 28% to 58%, over a time-scale
of _∼_ 3 yr. Perhaps the signal stemming from PDS 70c is due
to the free-free emission concomitant to the H _α_ detection. If
so, its spectral index should be _α_ _∼_ 0 _._ 7 (Wright & Barlow
1975), and should be more conspicuous relative to the disc at
lower frequencies.
Alternatively, the signal detected in LB19 might be due
to dust being heated up by episodic accretion, if it has time
to heat-up in 1.75 yr. Using the dust mass estimates from
Benisty et al. (2021) and Portilla-Revelo et al. (2022), the
Rosseland opacities from Casassus et al. (2019b), and for a
flat surface density out to 1 au in radius, the vertical Rosseland optical depth of this CPD would be in the range 5 to

_Image_ _restoration_ _and_ _variability_ _in_ _PDS 70_ 5



0.5


0.0


0.5



0.5


0.0


0.5



1.0


0.5


0.0


0.5


1.0


1.0


0.5


0.0


0.5


1.0



|0.0 0.2 0.4 0.6 mJy/beam|0.8|Col3|
|---|---|---|
|mJy/beam|||
|LB19 r=2<br>a|||
|LB19 r=2<br>a|||
|LB19 r=2<br>a|||
|LB19 r=2<br>a|||


1.0 0.5 0.0 0.5 1.0


0.0 0.2 0.4 0.6 0.8 1.0

|mJy/beam|Col2|Col3|
|---|---|---|
|IB17 r=0.3<br>d|||
|IB17 r=0.3<br>d|||



1.0 0.5 0.0 0.5 1.0


offset / arcsec


|0.0 0.2 0.4 0.6 mJy/beam|0.8|Col3|
|---|---|---|
|mJy/beam|||
|LB19+SB16 r=1<br>b|||
|LB19+SB16 r=1<br>b|||
|LB19+SB16 r=1<br>b|||
|LB19+SB16 r=1<br>b|||


|0.0 0.2 0.4 0.6 0.8 mJy/beam|1.0 1.2|Col3|
|---|---|---|
|mJy/beam|||
|LB19+IB17+SB16 r=1<br>c|||
|LB19+IB17+SB16 r=1<br>c|||
|LB19+IB17+SB16 r=1<br>c|||
|LB19+IB17+SB16 r=1<br>c|||



1.0



1.0



1.0







1.0 0.5 0.0 0.5 1.0


0.0 0.2 0.4 0.6 0.8 1.0 1.2


0.5


0.0


0.5



1.0 0.5 0.0 0.5 1.0


0.0 1.0 2.0 3.0 4.0 5.0


0.5


0.0


0.5



|mJy/beam|Col2|Col3|
|---|---|---|
|SB16+IB17 r=0.3<br>e|||
|SB16+IB17 r=0.3<br>e|||


1.0 0.5 0.0 0.5 1.0


offset / arcsec



1.0



|Jy/beam|Col2|Col3|
|---|---|---|
|SB16+IB17 uvmem<br>f|||
|SB16+IB17 uvmem<br>f|||


1.0 0.5 0.0 0.5 1.0


offset / arcsec



**Figure** **4.** Multi-configuration imaging at 351 GHz in PDS 70. **a:** Restored uvmem image for LB19, with Briggs robustness parameter
_r_ = 2 _._ 0, resulting in a clean beam of Ω _b_ = 0 _[′′]_ _._ 048 _×_ 0 _[′′]_ _._ 039 _/_ 59 deg, where we give the beam major axis (bmaj), minor axis (bmin) and
direction (bpa) in the format bmaj _×_ bmin/bpa. The noise in the residual image is _σ_ = 16 _._ 4 _µ_ Jy beam _[−]_ [1] . The two insets zoom on the central
region, with tick-marks separated by 0 _[′′]_ _._ 1, and on PDS 70c, with tick-marks at 0 _[′′]_ _._ 05. In both insets the linear grey scale stretches over the
range of intensities in each region, and the contour levels start at 3 _σ_ and are incremented in units of _σ_ . Intensities within each contour level
are color-coded differently. **b:** same as a) but for the concatenation LB19+SB16, with Ω _b_ = 0 _[′′]_ _._ 048 _×_ 0 _[′′]_ _._ 039 _/_ 58deg, and _σ_ = 15 _._ 7 _µ_ Jy beam _[−]_ [1]

**c:** same as a) but for the concatenation LB19+SB16+IB17, with Ω _b_ = 0 _[′′]_ _._ 058 _×_ 0 _[′′]_ _._ 047 _/_ 58deg, and _σ_ = 15 _._ 8 _µ_ Jy beam _[−]_ [1] . **d:** Same as a)
but for IB17, restored with _r_ = 1, with Ω _b_ = 0 _[′′]_ _._ 078 _×_ 0 _[′′]_ _._ 064 _/_ 59 deg, and _σ_ = 29 _._ 6 _µ_ Jy beam _[−]_ [1] . In the inset centered on PDS 70c, the tick
marks are separated by 0 _[′′]_ _._ 1, and the green cross marks the position of PDS 70 at the epoch of IB17. **e:** Same as c) but for SB16+IB17,
restored with _r_ = 0 _._ 3, with Ω _b_ = 0 _[′′]_ _._ 067 _×_ 0 _[′′]_ _._ 049 _/_ 60 deg, and _σ_ = 31 _._ 9 _µ_ Jy beam _[−]_ [1] . **f:** uvmem model image for SB16+IB17, with an
approximate resolution of 1/3 the natural weight beam (Cárcamo et al. 2018), or Ω _b_ _≈_ 0 _[′′]_ _._ 033 _×_ 0 _[′′]_ _._ 029 _/_ 88 deg. The contours start at 3 _σ_,
where _σ_ = 0 _._ 1 _µ_ Jy pix _[−]_ [1] is a representative noise level.



5000, depending on maximum grain size and temperature.
The corresponding radiative diffusion crossing time is at most
1 month, so much shorter than the timescale for the H _α_ variability.


_3.2.3_ _The_ _inner_ _disc_


Another interesting feature of the available data in PDS 70
is the structure of the inner disc, which appears to be even
more statistically significant than the detection of PDS 70c.
The face-on view in Fig. 7b, obtained with the disc orientation given above, shows extended substructure in the inner
disc, with a peak at 8 _σ_ (labeled ‘Clump 1’in Fig. 7). Intriguingly, Clump 1 is offset from the ring center by _∼_ 0 _[′′]_ _._ 03 to
0 _[′′]_ _._ 04, which is comparable to the natural-weights beam. At



such small angular scales we expect Keplerian rotation to result in detectable morphological changes in the time-span of
_∼_ 1.75 yr between IB17 and LB19. For a _∼_ 0.9 _M_ _⊙_ star (Keppler et al. 2019), and at a distance of 113.4 pc, material at a
radius of 0 _[′′]_ _._ 04 (4.5 au) would rotate by 62 deg, or 95 deg at
0 _[′′]_ _._ 03 (3.4 au). In Fig. 7a we choose the SB16+IB17 uvmem
model image (from Fig.4f) for a comparison with LB19, as
it has a similar angular resolution as SB16+LB19. Since the
statistical properties of the model image are not well constrained, the comparison is tentative. We find Clump 1 offset
by _∼_ 70 deg in azimuth relative to SB16+LB19, as expected
for Keplerian rotation if the centre of mass coincides with
the ring center. The V-shaped structure with Clump 1 at its
vertex appears to rotate as a rigid body, which might reflect
a wave launched by Clump 1. However, in IB17 another peak,


MNRAS **000**, 1–10 (2015)

6 _S._ _Casassus_ _&_ _M._ _Cárcamo_



0.0 0.2 0.4 0.6 0.8



0.0 0.1 0.1

mJy/beam



0.2


0.1


0.0


0.1


0.2



0.75


0.50


0.25


0.00


0.25


0.50


0.75



0.0 0.2 0.4 0.6 0.8

|0.0 0.2 0.4 0.6 mJy/beam|Col2|6 0.8|Col4|
|---|---|---|---|
|mJy/eam|mJy/eam|||
||SB16+LB19|||
||SB16+LB19|||



0.5 0.0 0.5


offset / arcsec



0.75


0.50


0.25


0.00


0.25


0.50


0.75



0.0 0.2 0.4 0.6 0.8

|0.0 0.2 0.4 0.6 mJy/beam|6 0.8|Col3|
|---|---|---|
|~~Kli ttd~~<br>mJy/eam|||
|~~eperan roae~~<br> & averaged|||
|~~eperan roae~~<br> & averaged|||



0.5 0.0 0.5


offset / arcsec



0.2


0.1


0.0


0.1


0.2





0.2 0.1 0.0 0.1 0.2


minor axis offset / arcsec











0.2 0.1 0.0 0.1 0.2


minor axis offset / arcsec



**Figure** **5.** The impact of Keplerian rotation over a time-span of
1.75 yr. **a)** Restored image for LB19+SB16, same as Fig. 4b but
for a different color scheme. **b)** Average of the image in a), and its
transformation to a Keplerian phase rotated by 1.75 yr.



0.0 0.2 0.4 0.6 0.8 1.0 1.2

mJy/beam



0.0 0.2 0.4 0.6 0.8 1.0 1.2



a) SB16+IB17 b) fake point














|a r=) 0S .B 316+IB17<br>-37 -51<br>61 -18|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|a) SB16+IB17<br>r=0.3<br><br>-51<br>61<br>-18<br>-37||-37|-37|a) SB16+IB17<br>r=0.3|-51|
|a) SB16+IB17<br>r=0.3<br><br>-51<br>61<br>-18<br>-37|61|61|61|61|-18|
|a) SB16+IB17<br>r=0.3<br><br>-51<br>61<br>-18<br>-37|61|61|61|||


|0.0 0.2 0.4 0.6 0.8 1.0 1.2 mJy/beam|Col2|0.|.0 0.2|0.4 0.6 0. mJy/beam|.8 1.0|1.2|
|---|---|---|---|---|---|---|
|b) fake point<br>sources<br><br>91<br>187<br>130<br>93|||||||
|b) fake point<br>sources<br><br>91<br>187<br>130<br>93||93|93|b) fake point<br>sources|91||
|b) fake point<br>sources<br><br>91<br>187<br>130<br>93||93|93|b) fake point<br>sources|91||
|b) fake point<br>sources<br><br>91<br>187<br>130<br>93|187|187|187|187|130|130|
|b) fake point<br>sources<br><br>91<br>187<br>130<br>93|187|187|187||||



**Figure** **6.** Tests of point source sensitivity through the injection
of point sources in IB 17. a): same as Fig. 4e, but with 4 insets that
zoom in on the expect position of PDS 70c, and 3 other locations,
at symmetrical positions relative to the disc axes. The red crosses
mark the centre of each inset, and the numbers close to the red
crosses correspond to the specific intensity value at the cross. b):
same as a), but with the addition of fake 126 _µ_ Jy point sources at
all 4 locations.


labeled Clump 2 in Fig. 7, more compact and that reaches the
same peak intensity as Clump 1, is found offset by _∼_ 0 _[′′]_ _._ 08.
Keplerian rotation on a circular orbit would be insufficient
to bring Clump 2 to its position in LB19; perhaps it is on a
eccentric orbit and/or it is rapidly infalling. If Clump 2 is indeed the same structure in both epochs, it is fainter relative
to Clump 1 in LB19.
The signal from the inner disc appears to be featureless
in the images from Benisty et al. (2021, their Figs. 2 or 3 for
Briggs r=1, or their Fig. 6 for Brigss _r_ = 2). A possible explanation for this difference could be that the structures pickedup here are part of the residuals in Benisty et al. (2021).
For instance the bulk of the inner disc may have been fit by
a medium-scale Gaussian component in multi-scale `tclean`,
while the details of the structure would have required deeper
cleaning. These residuals would have been down-scaled by
the JvM correction (see Sec. A5), and the inclusion of the
extended multi-scale `tclean` component on this central emission may have resulted in a seemingly featureless inner disc.


MNRAS **000**, 1–10 (2015)



**Figure** **7.** Face-on views of the inner disc in PDS 70. Disc rotation is retrograde (clock-wise). The plus sign marks the origin and
coincides with the ring center for each image. The _x_ -axis and _y_ axis are aligned with the disc minor and major axis, respectively.
**a)** Restored image for LB19+SB16 (from Fig. 4b, with the same
contours and noise levels). **b)** uvmem image from Fig. 4f.


**4** **CONCLUSIONS**


In this article we have revisited the ALMA data on PDS 70

using a different imaging strategy than that in the original
publications. We used the synthesis imaging package uvmem,
which is an alternative to `tclean` . We have coupled uvmem
to the standard self-calibration procedure implemented in
CASA, within a programming framework called OOselfcal. We also proposed a strategy for multi-epoch joint image restoration, which requires the alignment of the visibility
data. This alignment was performed in the _uv_ -plane and implemented in the VisAlign package.
As a result of the application of VisAlign and OOselfcal
to the available data in PDS 70, we have reached the following
conclusions:


(i) The point source in PDS 70c is detected, but only at
the 8 _σ_ level.

(ii) The same point source is absent in IB17, suggesting
that it is variable by 42% _±_ 13% on 1 _._ 75 yr timescales.

(iii) The inner disc of PDS70 is structured and variable.
Its peak is offset by _∼_ 0 _[′′]_ _._ 04 from the ring center. We tentatively observe that the peak appears to rotate according to
Keplerian rotation relative to the ring center.


We caution on the use of the JvM correction, which was
applied in the original publication of the long-baseline observations of PDS 70. The JvM correction exaggerates the
peak-signal to noise ratio of the restored images by a factor
of up to ten.


**ACKNOWLEDGEMENTS**


We thank the referee, Prof. Stéphane Guilloteau, for a thorough review and constructive comments that improved the
manuscript, as well as for fixing an error in the extraction of
the power spectra in Figs. 2 and 3. We also thank Jonathan
Williams and Sebastián Pérez for readings of the manuscripts
and useful comments. We acknowledge the help of the dask
and astropy communities for their technical support in the

development of VisAlign and pyralysis. S.C. and M.C. acknowledge support from Agencia Nacional de Investigación
y Desarrollo de Chile (ANID) given by FONDECYT Regular grants 1211496, ANID PFCHA/DOCTORADO BECAS CHILE/2018-72190574 and ANID project Data Observatory Foundation DO210001. This paper makes use of the
following ALMA data: ADS/JAO.ALMA# `2015.1.00888.S,`
`2017.A.00006.S,` `2018.A.00030.S` . ALMA is a partnership
of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


**DATA** **AVAILABILITY**


The reduced ALMA data presented in this article
are available upon reasonable request to the corresponding author. The original or else non-standard
software packages underlying the analysis are available at the following URLs: MPolarMaps ( `[https:](https://github.com/simoncasassus/MPolarMaps)`
`[//github.com/simoncasassus/MPolarMaps](https://github.com/simoncasassus/MPolarMaps)`, Casassus et al.
2021b), uvmem ( `[https://github.com/miguelcarcamov/](https://github.com/miguelcarcamov/gpuvmem)`
`[gpuvmem](https://github.com/miguelcarcamov/gpuvmem)`, Cárcamo et al. 2018), pyralysis ( `[https:](https://gitlab.com/miguelcarcamov/pyralysis)`
`[//gitlab.com/miguelcarcamov/pyralysis](https://gitlab.com/miguelcarcamov/pyralysis)` ), VisAlign
( `[https://github.com/simoncasassus/VisAlign](https://github.com/simoncasassus/VisAlign)` ),
OOselfcal ( `[https://github.com/miguelcarcamov/](https://github.com/miguelcarcamov/objectoriented_selfcal)`
`[objectoriented_selfcal](https://github.com/miguelcarcamov/objectoriented_selfcal)` ).


**REFERENCES**


Andrews S. M., et al., 2021, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac00b9) [916,](https://ui.adsabs.harvard.edu/abs/2021ApJ...916...51A) 51
Benisty M., et al., 2021, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ac0f83) [916,](https://ui.adsabs.harvard.edu/abs/2021ApJ...916L...2B) L2
Briggs D. S., 1995, PhD thesis, New Mexico Institute of Mining
and Technology
Briggs D. S., Schwab F. R., Sramek R. A., 1999, in Taylor G. B.,
Carilli C. L., Perley R. A., eds, Astronomical Society of the
Pacific Conference Series Vol. 180, Synthesis Imaging in Radio
Astronomy II. p. 127
Brittain S. D., Najita J. R., Carr J. S., 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab380b) [883,](https://ui.adsabs.harvard.edu/abs/2019ApJ...883...37B) 37
Cabrera G. F., Casassus S., Hitschfeld N., 2008, [ApJ,](http://dx.doi.org/10.1086/523961) 672, 1272
Cárcamo M., Román P. E., Casassus S., Moral V., Rannou F. R.,
2018, Astronomy [and](http://dx.doi.org/10.1016/j.ascom.2017.11.003) Computing, 22, 16
Casassus S., Cabrera G. F., Förster F., Pearson T. J., Readhead
A. C. S., Dickinson C., 2006, [ApJ,](http://dx.doi.org/10.1086/499517) 639, 951
Casassus S., et al., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/811/2/92) [811,](http://adsabs.harvard.edu/abs/2015ApJ...811...92C) 92
Casassus S., et al., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/sty894) 477, 5104
Casassus S., et al., 2019a, [MNRAS,](http://dx.doi.org/10.1093/mnras/sty3269) 483, 3278
Casassus S., Pérez S., Osses A., Marino S., 2019b, [MNRAS,](http://dx.doi.org/10.1093/mnrasl/slz059) [486,](https://ui.adsabs.harvard.edu/abs/2019MNRAS.486L..58C)

[L58](https://ui.adsabs.harvard.edu/abs/2019MNRAS.486L..58C)

Casassus S., Vidal M., Arce-Tord C., Dickinson C., White G. J.,
Burton M., Indermuehle B., Hensley B., 2021a, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa4016) [502,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502..589C)

[589](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502..589C)

Casassus S., et al., 2021b, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab2359) 507, 3789
Chael A. A., Johnson M. D., Bouman K. L., Blackburn L. L.,
Akiyama K., Narayan R., 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aab6a8) [857,](https://ui.adsabs.harvard.edu/abs/2018ApJ...857...23C) 23
Christiaens V., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz1232) 486, 5819
Cornwell T., Fomalont E. B., 1999, in Taylor G. B., Carilli C. L.,
Perley R. A., eds, Astronomical Society of the Pacific Conference Series Vol. 180, Synthesis Imaging in Radio Astronomy
II. p. 187
Czekala I., et al., 2021, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ac1430) [257,](https://ui.adsabs.harvard.edu/abs/2021ApJS..257....2C) 2
Event Horizon Telescope Collaboration et al., 2019a, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ab0ec7) [875,](https://ui.adsabs.harvard.edu/abs/2019ApJ...875L...1E) L1



_Image_ _restoration_ _and_ _variability_ _in_ _PDS 70_ 7


Event Horizon Telescope Collaboration et al., 2019b, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ab0e85) [875,](https://ui.adsabs.harvard.edu/abs/2019ApJ...875L...4E) L4
Francis L., Johnstone D., Herczeg G., Hunter T. R. ., Harsono D.,
2020, [AJ,](http://dx.doi.org/10.3847/1538-3881/abbe1a) 160, 270
Haffert S. Y., Bohn A. J., de Boer J., Snellen I. A. G., Brinchmann J., Girard J. H., Keller C. U., Bacon R., 2019, [Nature](http://dx.doi.org/10.1038/s41550-019-0780-5)
[Astronomy,](http://dx.doi.org/10.1038/s41550-019-0780-5) 3, [749](https://ui.adsabs.harvard.edu/abs/2019NatAs...3..749H)
Högbom J. A., 1974, A&AS, 15, 417
Isella A., Benisty M., Teague R., Bae J., Keppler M., Facchini S.,
Pérez L., 2019, [ApJ,](http://dx.doi.org/10.3847/2041-8213/ab2a12) 879, L25
Jorsater S., van Moorsel G. A., 1995, [AJ,](http://dx.doi.org/10.1086/117668) 110, 2037
Keppler M., et al., 2019, [A&A,](http://dx.doi.org/10.1051/0004-6361/201935034) 625, [A118](https://ui.adsabs.harvard.edu/abs/2019A&A...625A.118K)
Long Z. C., et al., 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aaba7c) 858, 112
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007,
in Shaw R. A., Hill F., Bell D. J., eds, Astronomical Society
of the Pacific Conference Series Vol. 376, Astronomical Data
Analysis Software and Systems XVI. p. 127
Öberg K. I., et al., 2021, [ApJS,](http://dx.doi.org/10.3847/1538-4365/ac1432) [257,](https://ui.adsabs.harvard.edu/abs/2021ApJS..257....1O) 1
Pearson T. J., et al., 2003, [ApJ,](http://dx.doi.org/10.1086/375508) 591, 556
Portilla-Revelo B., Kamp I., Rab C., van Dishoeck E. F., Keppler
M., Min M., Muro-Arena G. A., 2022, [A&A,](http://dx.doi.org/10.1051/0004-6361/202141764) 658, A89
Rau U., Cornwell T. J., 2011, [A&A,](http://dx.doi.org/10.1051/0004-6361/201117104) 532, A71
Remijan A., et al., 2019, ALMA Technical Handbook,ALMA Doc.
7.3, ver. 1.1, 2019, [doi:10.5281/zenodo.4511522](http://dx.doi.org/10.5281/zenodo.4511522)
Shepherd M. C., 1997, in Hunt G., Payne H., eds, Astronomical
Society of the Pacific Conference Series Vol. 125, Astronomical
Data Analysis Software and Systems VI. p. 77
Sutton E. C., Wandelt B. D., 2006, [ApJS,](http://dx.doi.org/10.1086/498571) 162, 401
Szulágyi J., Ercolano B., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/abb5a2) 902, 126
Szulágyi J., Plas G. v. d., Meyer M. R., Pohl A., Quanz S. P.,
Mayer L., Daemgen S., Tamburello V., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx2602) [473,](https://ui.adsabs.harvard.edu/abs/2018MNRAS.473.3573S)

[3573](https://ui.adsabs.harvard.edu/abs/2018MNRAS.473.3573S)

Thompson A. R., Moran J. M., Swenson George W. J., 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition,
[doi:10.1007/978-3-319-44431-4.](http://dx.doi.org/10.1007/978-3-319-44431-4. )
Wiaux Y., Jacques L., Puy G., Scaife A. M. M., Vandergheynst
P., 2009, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.14665.x) 395, 1733
Wright A. E., Barlow M. J., 1975, [MNRAS,](http://dx.doi.org/10.1093/mnras/170.1.41) [170,](http://adsabs.harvard.edu/abs/1975MNRAS.170...41W) 41


**APPENDIX** **A:** **IMAGE** **RESTORATION**


**A1** **Motivation** **for** **image** **restoration,** **and** **for** **a**
**reconsideration** **of** **the** **JvM** **correction**


The interpretation of radio interferometer observations usually involves a model of the sky image that accounts for the
visibility data (except in the direct measurement of power
spectra, e.g. Pearson et al. 2003). These models are often
parametric (e.g. Event Horizon Telescope Collaboration et al.
2019a). Such parametric models describe the source with few
parameters, and if the model is an adequate representation
of the source, their posterior distributions can be used to assess uncertainties. However, in general the model image is
non-parametric. The traditional synthesis imaging algorithm
clean uses a collection of compact sources, represented by
spikes or circular Gaussians, and distributed by matchingpursuit (Högbom 1974; Rau & Cornwell 2011). A variety of
Bayesian image synthesis algorithms, or more generally regularized maximum likelihood optimizations of the model image, have been proposed. Some use a regular grid to represent
the model image, which is then referred to as the ‘deconvolved
image’, as in the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018), or in ’Closure Imaging’ (Chael et al. 2018;
Event Horizon Telescope Collaboration et al. 2019b), while
others use the Voronoi tessellation (Cabrera et al. 2008) or
compressed sensing (e.g. Wiaux et al. 2009).


MNRAS **000**, 1–10 (2015)

8 _S._ _Casassus_ _&_ _M._ _Cárcamo_


However, the model images by themselves usually lack
noise estimates. This is because the inverse problem in image
synthesis, i.e. the production of a model image from sparse
Fourier data, is intrinsically ill-posed. After gridding the visibility data (see Sec. A3 below), the number of free parameters
reach around a million to cover continuously the _uv_ -plane,
and exceeds the number of independent data points. Estimates of the uncertainties in the model image are therefore
challenging (but see Sutton & Wandelt 2006; Casassus et al.
2015).
As an alternative, to convey the uncertainties in synthesis
imaging it is customary to “restore” the model images (e.g.
Thompson et al. 2017; Briggs et al. 1999) by convolution with
an elliptical Gaussian, which represents the interferometer
angular resolution, and the addition of the “dirty map” of the
residuals, which is essentially the inverse Fourier transform of
the gridded visibility residuals. These residuals encapsulate
both the thermal noise and synthesis-imaging artefacts. They
may also include faint signal that was missed in the model.
However, there are several different definitions of the dirty
map, that correspond to different gridding and data weighting strategies. This degree of freedom has led to a reconsideration of the dirty map units used in standard packages, in
the so-called ‘JvM correction’ (Jorsater & van Moorsel 1995;
Czekala et al. 2021), resulting in noise values that differ from
the standard definition in image restoration. The dirty map of
the residuals is then scaled by the ratio of the dirty and clean
beams, thereby artificially down-scaling the noise level by up
to one order of magnitude. This appendix serves as a caution on the JvM correction, which is increasingly applied in
the recent literature (e.g. Benisty et al. 2021; Andrews et al.
2021; Öberg et al. 2021, and the series of articles derived
from the MAPS ALMA Large Programme).


**A2** **Definition** **of** **the** **restored** **image**


We assume that a model image _I_ _m_ ( _⃗x_ ), defined onto a regular grid, has been obtained so that the associated model
visibilities _{V_ _m_ ( _⃗u_ _j_ ) _}_ _[P]_ _j_ =1 [,]


_V_ _m_ ( _⃗u_ _j_ ) = _I_ _m_ ( _⃗x_ ) _e_ [2] _[πi⃗u]_ _[j]_ _[·][⃗x]_ _dxdy,_ (A1)
�


match the observed visibility data _{V_ ( _⃗u_ _j_ ) _}_ _[P]_ _j_ =1 [according] [to]
some criterion (for instance a least-squares fit). To simplify
notation we have omitted from Eq. A1 the modulation by the
primary beam and by the Jacobian of the direction cosines
(which are both close to unity in the application to PDS 70c).
The residual visibilities are _V_ _R_ ( _⃗u_ _j_ ) = _V_ ( _⃗u_ _j_ ) _−_ _V_ _m_ ( _⃗u_ _j_ ). Given
a model image and a telescope angular resolution represented
by an elliptical Gaussian _g_ _b_ ( _⃗x_ ), the restored image for a single
pointing is


_I_ _R_ = _I_ _m_ _∗_ _g_ _b_ + _R_ _D_ _,_ (A2)


where _R_ _D_ ( _⃗x_ ) is the dirty map of the gridded residual visibil
ities, _V_ ˜ _R_ ( _⃗u_ _k_ ) _N_ [i.e.] [after] [averaging] [the] [sparsely] [sampled]
� � _k_ =1 [,]

_uv_ -data into a regular grid with _N_ cells and weights _{W_ _k_ _}_ _k_ _[N]_ =1 [.]
For an extension of Eq. A2 to mosaics see, for example, Casassus et al. (2021a).


MNRAS **000**, 1–10 (2015)



**A3** **Gridding**


Since the visibility data correspond to the Fourier transform
of the sky image, a first approximation of the sky signal
can be obtain by averaging the visibility data into a regular grid and performing the inverse Fourier transform. When
this gridding procedure does not extrapolate to the _uv_ -cells
devoid of data, which are assigned zero weight, the result is
called a dirty map.
There are several techniques for visibility gridding (e.g.
Thompson et al. 2017; Briggs et al. 1999). Its simplest version
is a straight-forward application of counts in cells to grid the
visibility data _{V_ _j_ _}_ _[P]_ _j_ =1 [in] [a regular grid] [in] [the] _[ uv]_ [-plane,] [with]
_N_ = _n × m_ cells (for a model image defined on an _n × m_
grid):

_V_ ˜ _k_ = �� _Ni_ = _Ni_ _k_ =11 _k_ _[w][w]_ _[i]_ _[V]_ _[i]_ _[i]_ _,_ (A3)


where _N_ _k_ is the number of visibilities that fall in cell ( _u_ _k_ _, v_ _k_ )
and _P_ = [�] _[N]_ _k_ =1 _[N]_ _[k]_ [.] [The] [weights] _[w]_ _[i]_ [are] [propagated] [to] [the]
gridded visibilities, _V_ [˜] _k_, whose weights are then


_W_ _k_ = � _w_ _i_ _._ (A4)


_i∈k_


There is a wide range of different choices for the visibility
weights _{w_ _j_ _}_ _[P]_ _j_ =1 [,] [with] [different] [units] [and] [resulting] [in] [dif-]
ferent intensity scales in the corresponding dirty maps (see
Sec. A4). Natural weights (e.g. Thompson et al. 2017; Briggs
et al. 1999) assign the usual thermal noise weight to each
visibility datum:


_w_ _i_ = _ω_ nat _,i_ = [1] _._ (A5)

_σ_ _i_ [2]


Other weighting schemes are often used to control the effective interferometer resolution. In uniform weights (e.g.
Thompson et al. 2017; Briggs et al. 1999) all cells are assigned the same weight, which is achieved by redefining the
weight for each datum:


_w_ _i_ = _[ω]_ [nat] _[,][i]_ (A6)

_W_ _k_ _[,]_


where _W_ _k_ is the natural weight of the _k_ -th cell where visibility
( _u_ _i_ _, v_ _i_ ) falls. For uniform weights, Eq. A4 gives the weight of
each _uv_ -cell:


_W_ _k_ = � _w_ _i_ _≡_ 1 _._ (A7)


_i∈k_


In Briggs weighting (Briggs 1995),


_w_ _i_ = _ω_ nat _,i_ (A8)
1 + _W_ _k_ _f_ [2]



_f_ [2] = (5 _·_ 10 _[−][r]_ ) [2]

� _k_ _[W]_ _k_ [ 2]
� _i_ _[ω]_ [nat] _[,i]_



_,_



where _r_ is the Briggs robustness parameter ( _r_ = 2 is almost
equivalent to natural weights, _r_ = _−_ 2 is close to uniform
weights).
The gridded weights _W_ _k_ derive from Eq. A4 using the
weights _w_ _i_, adjusted from the original weights _ω_ nat _,i_ according to Eqs. A5, A6 or A8. Thus the units for _W_ _k_ are different
for each scheme.

**A4** **Dirty** **map,** **Dirty** **beam**


The dirty map might be thought of as a uniquely defined image, which would be the Fourier pair of the gridded visibilities. However, the degree of freedom in the choice of weighting
scheme leads to different units for the dirty map. We therefore
adopt the following definition for the dirty map:

_I_ _D_ ( _x, y_ ) = � _αW_ _k_ _V_ [˜] _k_ _e_ _[−]_ [2] _[πi]_ [(] _[ux]_ [+] _[vy]_ [)] ∆ _u_ ∆ _v,_ (A9)


_k_


where _α_ is a constant that sets the units for _I_ _D_ . In order
to determine _α_ we consider a point source with flux density
_F_ at the phase center. We extract its flux from the gridded
visibilities using a least-squares fit,


_χ_ [2] = �( _V_ [˜] _k_ _−_ _V_ [˜] _k_ _[m]_ [)] _[∗]_ [( ˜] _[V]_ _k_ _[−]_ _[V]_ [˜] _k_ _[m]_ [)] _[W]_ _k_ _[,]_ (A10)


_k_

where _V_ [˜] _k_ _[m]_ = _F_ . The root of _[∂]_ _∂F_ _[χ]_ [2] [= 0] [is]



_._ (A11)
_k_ _[W]_ _[k]_



_F_ = [1]

2



�



_k_ [(] _[V]_ _[◦]_ [+] _[ V]_ _◦_ _[∗]_ [)] _[W]_ _k_
� _k_ _[W]_ _[k]_



Assuming that each visibility datum is independent, the error
on _F_ is


1
_σ_ _F_ = _._ (A12)
~~�~~ � _k_ _[W]_ _[k]_


On the other hand, the uncertainty on _I_ _D_ ( _⃗x_ = _[⃗]_ 0) from Eq. A9
is



_σ_ _I_ = _α_ ∆ _u_ ∆ _v_
�


_k_

~~�~~



_W_ _k_ [2] _[σ]_ _k_ [2] [=] _[ α]_ [∆] _[u]_ [∆] _[v]_ �

_k_ _k_
~~�~~



_W_ _k_ _._ (A13)

_k_



_Image_ _restoration_ _and_ _variability_ _in_ _PDS 70_ 9


As another example, we consider the case of a perfect instrument with uniform _uv_ -coverage, that fills the _uv_ -grid,
with arbitrarily deep data and constant weights _W_ _k_ . In this
case the dirty beam should be a unit spike, and rather than
an elliptical clean beam we would use the solid angle subtended by a pixel in the sky image, Ω _b_ = ∆ _x_ ∆ _y_, so that
Eq. A16 yields the same spike in units of Jy pix _[−]_ [1] .
We have checked that the synthesis imaging packages
casa(McMullin et al. 2007) and difmap (Shepherd 1997)
produce dirty maps with consistent units. This can be confirmed by simulating visibility data onto a unit spike in the
absence of noise, and deriving the corresponding dirty map
(using task `tclean` in casa or `mapplot` in difmap), which
yields peak intensities of unity. In fact the dirty map of a
unit spike is of course just the dirty-map PSF and is one of
the default products of tasks `tclean` and `mapplot` .


**A5** **The** **JvM** **correction**


For consistency with the flux scale set by the visibility data
(Eq. A11), the dirty map, as defined by Eq. _A_ 16, bears units
of Jy Ω _[−]_ _b_ [1] [,] [where] [Ω] _[b]_ [is] [the] [“clean”] [beam.] [By] [contrast,] [in] [the]
JvM correction (Jorsater & van Moorsel 1995; Czekala et al.
2021), a ‘dirty beam’ solid angle, here denoted by Ω D, is
introduced to represent the solid angle subtended by the dirty
map of a point source, and to set the units of the dirty map
in Eq. A16 to Jy Ω _[−]_ D [1] [.] [In] [this] [context,] [for] [image] [restoration]
the residual dirty map must be scaled by the beam ratio
_ϵ_ =Jy Ω _[−]_ _b_ [1] [/Jy][ Ω] D _[−]_ [1] before addition with the convolved model
image.
However the solid angle integral for Ω D will in general
not converge, as acknowledged by Czekala et al. (2021), and
which can readily be concluded from Fig. 1 in (Jorsater & van
Moorsel 1995). These authors propose instead two different
solutions to estimate _ϵ_ . In the original formulation of the JvM
correction, Jorsater & van Moorsel (1995) solve for _ϵ_ by comparing the total flux density extracted in a region between
two versions of the restored images. These two versions can
be different depths of cleaning, or simply the dirty and clean
maps. However, the convolution with dirty beam sidelobes
will bias the flux density, in ways that depend on the flux
extraction aperture. In turn, Czekala et al. (2021) adopt a
different definition for Ω D and _ϵ_ . They propose to perform an
azimuthal average of the dirty beam, and truncate the radial
domain of the dirty beam solid angle integral to the first null
in the radial direction.

In both versions of the JvM correction the values for _ϵ_
range from 1 to 1/10, and the extreme corresponds to natural weights. But both choices seem arbitrary, either in the
definition of the flux extraction aperture, or in the choice of
domain for the solid integral. Neither options are consistent
with the requirement set by Eq. A14, since they both re-scale
the units for the dirty maps. The result is an artificial increase
of sensitivity by up to a factor of 1 _/ϵ_ .
The original motivation of the JvM correction may perhaps
stem from the normalisation of the dirty beam: since the
dirty beam is the dirty map response to a unit spike, it may
be thought that its peak intensity should correspond to the
point source flux for the ‘correct beam solid angle’. But this
argument breaks down if the integrated flux diverges.


MNRAS **000**, 1–10 (2015)



Next we assume that the _uv_ -coverage is sufficient to use
the dirty map to approximate the sky image, smoothed by
an elliptical Gaussian that represents the image resolution.
This requires that the distribution of weights in the _uv_ -plane
is approximately Gaussian, so that its Fourier pair is also an
elliptical Gaussian in the image plane, the so-called “clean”
beam _g_ _b_ with full-width-at-half-maximum major and minor
axes BMAJ and BMIN, and that subtends a solid angle
Ω _b_ = 4 log(2) _π_ [BMAJ] _[×]_ [BMIN][.] [Given] [the] [degree] [of] [freedom]
in the weighting scheme, there is no uniquely defined clean
beam for a given visibility dataset, and neither is there a
unique angular resolution. In fact, even for the same weighting scheme, different synthesis imaging packages do not yield
the same angular resolution.
If the units for _I_ _D_ are set to Jy Ω _[−]_ _b_ [1] [, then for a point source]
at the phase center, with flux density _F_, we should have
_σ_ _I_ (A14)

[Jy Ω _[−]_ _b_ [1] []] [=] _[ σ]_ _[F]_


We can then solve for _α_ :


1
_α_ = _._ (A15)
� _W_ _k_ ∆ _u_ ∆ _v_


The dirty map, in units of Jy Ω _[−]_ _b_ [1] [,] [is] [therefore:]



_I_ _D_ ( _x, y_ ) = �


_k_



_W_ _k_ ˜

_V_ _k_ _e_ [2] _[πi]_ [(] _[ux]_ [+] _[vy]_ [)] _,_ (A16)

� _l_ _[W]_ _[l]_



as is standard. As an example, we consider the dirty map of
a unit spike at the phase center, which corresponds to the
dirty-map response, or point-spread function (PSF), and is
usually called the “dirty beam”:



_B_ ( _x, y_ ) = �


_k_



� _W_ _l_ _[W]_ _k_ _[l]_ _[e]_ [2] _[πi]_ [(] _[ux]_ [+] _[vy]_ [)] _[.]_ (A17)

10 _S._ _Casassus_ _&_ _M._ _Cárcamo_


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


MNRAS **000**, 1–10 (2015)


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Dust mass estimates for the CPD",
  "failed_quote": "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius, the vertical Rosseland optical depth of this CPD would be in the range 5 to 5000"
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Rosseland opacities",
  "failed_quote": "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius, the vertical Rosseland optical depth of this CPD would be in the range 5 to 5000"
 },
 {
  "path": "processing.calibration.self_calibration.evidence[0]",
  "value": "Independent self-calibration of each dataset and joint self-calibration of concatenated datasets using OOselfcal (wrapping CASA gaincal and applycal with uvmem models); phase-only loops halving solint from ~50s scan length until PSNR decreases, followed by one amp+phase loop. Also tested standard CASA tclean self-calibration.",
  "failed_quote": "We then proceeded to self-calibrate the data using a special purpose programming framework, OOselfcal, which is essentially a wrapper for casa tasks gaincal and applycal and any choice of imager (in this case uvmem)."
 },
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "uvmem non-parametric pure least-squares (chi^2) optimization regularized by image positivity (and entropy regularization tested)",
  "failed_quote": "Here we perform non-parametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the more commonly used clean algorithm (Högbom 1974; Rau & Cornwell 2011)."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "Briggs weighting with r = 2.0, r = 1, r = 0.3; natural weights used for visibility alignment gridding",
  "failed_quote": "We then gridd each dataset to a common uv−grid, in natural weights, so according to Eqs. A3 and A5 (which are implemented in the pyralysis software package)."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[2]",
  "value": "Briggs weighting with r = 2.0, r = 1, r = 0.3; natural weights used for visibility alignment gridding",
  "failed_quote": "b: same as a) but for the concatenation LB19+SB16, with Ω_b = 0''.048 × 0''.039 / 58deg, and σ = 15.7 µJy beam^-1 c: same as a) but for the concatenation LB19+SB16+IB17, with Ω_b = 0''.058 × 0''.047 / 58deg, and σ = 15.8 µJy beam^-1. d: Same as a) but for IB17, restored with r = 1, with Ω_b = 0''.078 × 0''.064 / 59 deg, and σ = 29.6 µJy beam^-1. ... e: Same as c) but for SB16+IB17, restored with r = 0.3"
 },
 {
  "path": "processing.imaging.image_size.evidence[1]",
  "value": "2048 x 2048 pixels (for common uv-grids); 4 arcsec field of view for residual noise calculation",
  "failed_quote": "In our framework this PSNR is calculated as the ratio of peak signal in the restored images to the noise in the whole residual image, with a field of view of 4 arcsec in the case of PDS 70"
 },
 {
  "path": "processing.imaging.final_rms.evidence[2]",
  "value": "LB19 (r=2.0): 16.4 uJy beam^-1; LB19+SB16 (r=1): 15.7 uJy beam^-1; LB19+SB16+IB17 (r=1): 15.8 uJy beam^-1; IB17 (r=1): 29.6 uJy beam^-1; SB16+IB17 (r=0.3): 31.9 uJy beam^-1; SB16+IB17 uvmem model: ~0.1 uJy pix^-1",
  "failed_quote": "e: Same as c) but for SB16+IB17, restored with r = 0.3, with Ω_b = 0''.067 × 0''.049 / 60 deg, and σ = 31.9 µJy beam^-1. ... The contours start at 3σ, where σ = 0.1 µJy pix^-1 is a representative noise level."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Extract continuum visibilities and combine all spectral windows as in Benisty et al. (2021). Perform iterative self-calibration using OOselfcal (wrapping CASA gaincal and applycal with uvmem image models), starting with phase-only loops halving the solution interval from scan length (~50s) until PSNR decreases, followed by one amplitude+phase loop.",
  "failed_quote": "We then proceeded to self-calibrate the data using a special purpose programming framework, OOselfcal, which is essentially a wrapper for casa tasks gaincal and applycal and any choice of imager (in this case uvmem)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Checked PSNR at each self-calibration loop (ratio of peak signal to noise in whole 4 arcsec residual image) and compared noise level of LB19 (16.4 uJy/beam) against ALMA Observing Tool predictions.",
  "failed_quote": "These iterations are interrupted when the PSNR decreases, and the self-calibrated visibility dataset is reverted to the calibration tables that yielded the highest PSNR."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Extract subsets with identical spectral domains in LSRK, grid each dataset to a common uv-grid in natural weights using pyralysis, and minimize chi^2_align over overlapping uv-radii (where azimuthally averaged weights are >1/10 peak) to fit for a spatial shift (delta x) and flux scale factor (alpha_R) relative to LB19 using VisAlign.",
  "failed_quote": "We extract subsets of each dataset with exactly the same spectral domains in LSRK. We then gridd each dataset to a common uv−grid, in natural weights, so according to Eqs. A3 and A5 (which are implemented in the pyralysis software package)."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Extract subsets with identical spectral domains in LSRK, grid each dataset to a common uv-grid in natural weights using pyralysis, and minimize chi^2_align over overlapping uv-radii (where azimuthally averaged weights are >1/10 peak) to fit for a spatial shift (delta x) and flux scale factor (alpha_R) relative to LB19 using VisAlign.",
  "failed_quote": "The overlap in uv-radii, over which the optimisation was carried out, was determined by taking azimuthal averages in the gridded weights W^S and W^L, and selecting the range where the radial profiles are both above 1/10 their peak."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[1]",
  "value": "The bulk of PDS 70 is not time-variable between epochs",
  "failed_quote": "We therefore assume that the bulk of PDS 70 is not variable between the two epochs."
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Least-squares minimization of chi^2_align (Eq. 1) for spatial shift delta x and real flux scale factor alpha_R",
  "failed_quote": "We then aligned each pair by shifting V˜^S, i.e. by minimising χ^2_align(α_R, δ⃗x) = ∑_k=1^N W_k^align ∥V˜_k^L − V˜_k^Lm∥^2"
 },
 {
  "path": "analysis_steps[1].validation.evidence[1]",
  "value": "Independent check of ring centers and orientation (PA, inclination) between LB19 and IB17 using MPolarMaps, confirming ring centers coincide within ~1 mas (1.5 sigma).",
  "failed_quote": "The ring centers Δ⃗_LB19 and Δ⃗_IB17 coincide within ∼ 1 mas, or 1.5σ, in support of the accuracy of the uv-plane alignment with VisAlign."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Stellar mass = 0.9 M_sun, distance = 113.4 pc; flat surface density out to 1 au radius for CPD optical depth estimate",
  "failed_quote": "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius, the vertical Rosseland optical depth of this CPD would be in the range 5 to 5000, depending on maximum grain size and temperature."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Antenna gain calibration in CASA self-calibration loops",
  "failed_quote": "We then proceeded to self-calibrate the data using a special purpose programming framework, OOselfcal, which is essentially a wrapper for casa tasks gaincal and applycal and any choice of imager (in this case uvmem)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Applying calibration tables in CASA self-calibration loops",
  "failed_quote": "We then proceeded to self-calibrate the data using a special purpose programming framework, OOselfcal, which is essentially a wrapper for casa tasks gaincal and applycal and any choice of imager (in this case uvmem)."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Non-parametric image synthesis and model generation in the self-calibration loop",
  "failed_quote": "Here we perform non-parametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the more commonly used clean algorithm (Högbom 1974; Rau & Cornwell 2011)."
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Automated self-calibration framework wrapping CASA gaincal and applycal with uvmem",
  "failed_quote": "We then proceeded to self-calibrate the data using a special purpose programming framework, OOselfcal, which is essentially a wrapper for casa tasks gaincal and applycal and any choice of imager (in this case uvmem)."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Gridding visibility datasets to a common uv-grid in natural weights",
  "failed_quote": "We then gridd each dataset to a common uv−grid, in natural weights, so according to Eqs. A3 and A5 (which are implemented in the pyralysis software package)."
 },
 {
  "path": "software[8].used_for.evidence[0]",
  "value": "Aligning multi-epoch visibility datasets in the uv-plane in position and flux scale",
  "failed_quote": "This visibility alignment procedure is implemented in the package VisAlign."
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "PDS 70 disc Position Angle (PA) in LB19 = 160.4 deg",
  "failed_quote": "For LB19, the best fit orientation corresponds to PA= 160.4 ± 0.08 deg, i = 130.0 ± 0.06 deg, and a ring center offset by Δ⃗_LB19 = (−0''.0018 ± 0''.0003, −0''.0036 ± 0''.0003) relative to the phase center."
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "PDS 70 disc inclination (i) in LB19 = 130.0 deg",
  "failed_quote": "For LB19, the best fit orientation corresponds to PA= 160.4 ± 0.08 deg, i = 130.0 ± 0.06 deg, and a ring center offset by Δ⃗_LB19 = (−0''.0018 ± 0''.0003, −0''.0036 ± 0''.0003) relative to the phase center."
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "PDS 70 disc Position Angle (PA) in IB17 = 160.5 deg",
  "failed_quote": "For IB17, we obtained PA= 160.5 ± 0.18 deg, i = 129.9^+0.16_-0.14 deg, and a ring center at Δ⃗_IB17 = (−0''.0032^+0''.0006_-0''.0009, −0''.0025 ± 0''.0008) relative to the phase center."
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "PDS 70 disc inclination (i) in IB17 = 129.9 deg",
  "failed_quote": "For IB17, we obtained PA= 160.5 ± 0.18 deg, i = 129.9^+0.16_-0.14 deg, and a ring center at Δ⃗_IB17 = (−0''.0032^+0''.0006_-0''.0009, −0''.0025 ± 0''.0008) relative to the phase center."
 },
 {
  "path": "results_numeric[23].evidence[0]",
  "value": "Clump 2 offset from ring center in IB17 = 0.08 arcsec",
  "failed_quote": "However, in IB17 another peak, labeled Clump 2 in Fig. 7, more compact and that reaches the same peak intensity as Clump 1, is found offset by ∼ 0''.08."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Non-parametric image synthesis with uvmem provides an alternative to CLEAN, and uv-plane alignment via VisAlign restricts free parameters to a single position shift and flux scale factor without requiring a bright source model like joint self-calibration.",
  "failed_quote": "Here we perform non-parametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the more commonly used clean algorithm (Högbom 1974; Rau & Cornwell 2011)."
 },
 {
  "path": "reasoning.how_they_decided_enough.evidence[0]",
  "value": "Self-calibration iterations were stopped when the peak signal-to-noise ratio (PSNR) decreased, reverting to the calibration tables that yielded the highest PSNR.",
  "failed_quote": "These iterations are interrupted when the PSNR decreases, and the self-calibrated visibility dataset is reverted to the calibration tables that yielded the highest PSNR."
 },
 {
  "path": "reproducibility.code_released[0].evidence[0]",
  "value": "All five custom software packages underlying the analysis are publicly released on GitHub/GitLab: MPolarMaps (https://github.com/simoncasassus/MPolarMaps), uvmem (https://github.com/miguelcarcamov/gpuvmem), pyralysis (https://gitlab.com/miguelcarcamov/pyralysis), VisAlign (https://github.com/simoncasassus/VisAlign), and OOselfcal (https://github.com/miguelcarcamov/objectoriented_selfcal).",
  "failed_quote": "The original or else non-standard software packages underlying the analysis are available at the following URLs: MPolarMaps (https://github.com/simoncasassus/MPolarMaps, Casassus et al. 2021b), uvmem (https://github.com/miguelcarcamov/gpuvmem, Cárcamo et al. 2018), pyralysis (https://gitlab.com/miguelcarcamov/pyralysis), VisAlign (https://github.com/simoncasassus/VisAlign), OOselfcal (https://github.com/miguelcarcamov/objectoriented_selfcal)."
 }
]
```
