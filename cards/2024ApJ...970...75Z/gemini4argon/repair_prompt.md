# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...970...75Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version June 13, 2024
Typeset using L [A] TEX **twocolumn** style in AASTeX631


**The** **resolved** **star** **formation** **law** **in** **NGC** **7469** **from** **JWST,** **ALMA** **and** **VLA**


Maria [Vittoria](http://orcid.org/0000-0001-7883-496X) Zanchettin, [1, 2] Marcella [Massardi](http://orcid.org/0000-0002-0375-8330), [3] Francesco [Salvestrini](http://orcid.org/0000-0003-4751-7421), [2] Manuela [Bischetti](http://orcid.org/0000-0002-4314-021X), [4, 2]

Chiara [Feruglio](http://orcid.org/0000-0002-4227-6035), [2, 5] Fabrizio Fiore, [2, 5] and [Andrea](http://orcid.org/0000-0002-4882-1735) Lapi 1, 5, 3, 6


1 _SISSA,_ _Via_ _Bonomea_ _265,_ _I-34136_ _Trieste,_ _Italy_
2 _INAF_ _Osservatorio_ _Astronomico_ _di_ _Trieste,_ _via_ _G.B._ _Tiepolo_ _11,_ _34143_ _Trieste,_ _Italy_
3 _INAF,_ _Istituto_ _di_ _Radioastronomia,_ _Italian_ _ARC,_ _Via_ _Piero_ _Gobetti_ _101,_ _I-40129_ _Bologna,_ _Italy_
4 _Dipartimento_ _di_ _Fisica,_ _Universit`a_ _di_ _Trieste,_ _Sezione_ _di_ _Astronomia,_ _Via_ _G.B._ _Tiepolo_ _11,_ _I-34131_ _Trieste,_ _Italy_
5 _IFPU_ _-_ _Institute_ _for_ _fundamental_ _physics_ _of_ _the_ _Universe,_ _Via_ _Beirut_ _2,_ _34014_ _Trieste,_ _Italy_
6 _INFN,_ _Sezione_ _di_ _Trieste,_ _via_ _Valerio_ _2,_ _Trieste_ _I-34127,_ _Italy_


ABSTRACT


We investigate the star formation process within the central 3.3 kpc region of the nearby luminous
infrared Seyfert NGC 7469, probing scales ranging from 88 to 330 pc. We combine JWST/MIRI
imaging with the F770W filter, with CO(2-1) and the underlying 1.3 mm dust continuum data from
ALMA, along with VLA radio continuum observations at 22 GHz. NGC 7469 hosts a starburst ring
which dominates the overall star formation activity. We estimate a global star formation rate SFR
_∼_ 11 _._ 5 M _⊙_ yr _[−]_ [1] from the radio at 22 GHz, and a cold molecular gas mass M(H2) _∼_ 6 _._ 4 _×_ 10 [9] M _⊙_ from
the CO(2-1) emission. We find that the 1.3 mm map shows a morphology remarkably similar to those
traced by the 22 GHz and the 7.7 _µ_ m polycyclic aromatic hydrocarbon (PAH) emission observed with
JWST. The three tracers reproduce the morphology of the starburst ring with good agreement. We
further investigate the correlations between the PAHs, the star formation rate and the cold molecular
gas. We find a stronger correlation of the PAHs with the star formation than with the CO, with
steeper correlations within the starburst ring ( _n_ _>_ 2) than in the outer region ( _n_ _<_ 1). We derive
the correlation between the star formation rate and the cold molecular gas mass surface densities,
the Kennicutt-Schmidt star formation law. Comparisons with other galaxy populations, including
starburst galaxies and active galactic nuclei, highlighted that NGC 7469 exhibits an intermediate
behavior to the Kennicutt-Schmidt relations found for these galaxy populations.


_Keywords:_ AGN host galaxies (2017) — Molecular gas (1073) – Star formation (1569) — Interstellar
medium (847)



1. INTRODUCTION


Schmidt (1959, 1963) proposed the existence of empirical scaling relations between the properties of the interstellar gas and the star formation rate (SFR) in the same
environment. Later, Kennicutt (1998a,b) confirmed the
correlation between global measurements of galaxy gas
mass and SFR in nearby galaxies. Consequently, this
correlation has become known as the Kennicutt-Schmidt
(K-S) star formation law.
Spatially unresolved studies that target molecular gas
and SFR help to derive global disk properties and are


Corresponding author: Maria Vittoria Zanchettin

mazanch@sissa.it



necessary to test the redshift dependence of the gas–star
formation relation (Genzel et al. 2010; Schruba et al.
2011). However, to understand the physical mechanisms behind the star formation (SF) process, spatially
resolved measurements in nearby targets are necessary.
These observations allow us to study how the SF properties, such as the timescales for gas consumption and the
SF efficiency, vary across the galaxy environments (Onodera et al. 2010; Bigiel et al. 2011; Leroy et al. 2013;
Ford et al. 2013; Kreckel et al. 2018; Dey et al. 2019;
Pessa et al. 2022; Sun et al. 2023). The tracers most
commonly used to quantify the SFR are the most commonly observed optical spectral lines (e.g. H _α_ and [O
II]), the global radio continuum, mid- and far- infrared
(MIR and FIR), and ultraviolet (UV) emission. Such

2


SFR indicators refer to various wavelengths that trace
stellar populations at different evolutionary stages (see
Kennicutt & Evans 2012, for a review). Optical lines
and UV light are emitted predominantly by young stars
and are sensitive to SF on _∼_ 10 Myr and _∼_ 10–100 Myr
timescales respectively (Hao et al. 2011; Murphy et al.
2011). However, accurate SFR estimates from UV data
are affected by large uncertainties due to the dust extinction correction (Mahajan et al. 2019). The thermal
free-free and non-thermal synchrotron radio emission at
low frequency (1-10 GHz) are a measure of past formation of massive stars, resulting in a SF time sensitivity of
about 150-300 Myr (Klein & Emerson 1981; Gioia et al.
1982; Tabatabaei et al. 2017; Arango-Toro et al. 2023).
The MIR (3–25 _µ_ m) emission of star forming galaxies
is dominated by the polycyclic aromatic hydrocarbon
(PAH) features both at low and high redshift (Puget
& Leger 1989; Genzel et al. 1998; Armus et al. 2007;
Valiante et al. 2007; Farrah et al. 2008; Veilleux et al.
2009; Riechers et al. 2014). In particular PAHs has been
proposed as a good indicator of SFR over timescales of
up to a few hundred million years (Peeters et al. 2004;
Shipley et al. 2016; Xie & Ho 2019). Moreover a connection between PAHs and the properties of the cold molecular gas, traced by the CO emission, has been proposed
by several studies (Cortzen et al. 2019; Alonso-Herrero
et al. 2020). Taking advantage of interferometric mm
and cm, and JWST data of nearby galaxies, it is possible to perform spatially resolved studies of the SF process in galaxies, down to hundred-parsec scales and to
investigate the correlations between the PAHs, the SFR
surface density (Σ SFR ) and the mass surface density of
molecular gas (Σ H2 ), which is the direct fuel of the formation of stars.

In this paper, we study the SF process in the inner
( _∼_ 3 kpc) region of NGC 7469, a nearby (z = 0.01627)
luminous infrared galaxy (L IR _,_ 8 _−_ 1000 _µ_ m = 10 [11] _[.]_ [6] L _⊙_ ),
and type-1.5 Seyfert (Landt et al. 2008) with a bolometric AGN luminosity of L bol _,_ AGN = 3 _._ 5 _×_ 10 [44] erg
s _[−]_ [1] (Gruppioni et al. 2016). From VLA 8.4 GHz observations at 0.3 arcsec resolution, P´erez-Torres et al. (2009)
estimated the nuclear radio emission L 8 _._ 4 GHz _∼_ 10 [36] _[.]_ [96]

erg s _[−]_ [1] . NGC 7469 may host a radio core–jet structure
as resolved on 0.3 arcsec scale by the VLA (Lonsdale
et al. 2003; Alberdi et al. 2006; Orienti & Prieto 2010),
and no evidence of a radio jet–ISM interaction has yet
been reported (Xu & Wang 2022). NGC 7469 is known
to host a prominent starburst (SB) ring with an outer
radius of 900 pc, which dominates the global SFR of
_∼_ 20 _−_ 50 M _⊙_ yr _[−]_ [1] (Genzel et al. 1995; Soifer et al. 2003;
Gruppioni et al. 2016; Song et al. 2021). A bar-like feature connects the SB ring to a circumnuclear disk (CND)



located in the inner 300 pc (see Davies et al. 2004; Izumi
et al. 2015, 2020, and references therein). The molecular gas mass derived from CO(1-0) within the inner
_∼_ 1.2 kpc region is M(H2) = 2 _._ 7 _×_ 10 [9] M _⊙_ (Davies et al.
2004; Izumi et al. 2020). To investigate the SF process inside and outside the SB ring of NGC 7469, we
combine James Webb Space Telescope (JWST) imaging
with the F770W filter of the Mid-InfraRed Instrument
(MIRI), with CO(2-1) and the underlying dust continuum (224.2-243.7 GHz) data obtained from the Atacama
Large Millimeter/submillimeter Array (ALMA), along
with the Karl G. Jansky Very Large Array (VLA) radio
continuum imaging at 22 GHz, resolving physical scales
in the range 88 pc (MIRI) to 330 pc (VLA).
This Paper is organized as follows. In Section 2,
we describe the observations and data reduction. Sec
tion 3 provides details on the data analysis and quantity derivations. Section 4 describes our results. The
adopted luminosity distance of the galaxy is 72.1 Mpc
and the corresponding scale is 0.338 kpc/arcsec.


2. OBSERVATIONS AND DATA REDUCTION


We analyzed band 6 ALMA 12 m observations (program ID 2017.1.00078.S, PI Izumi Takuma) of NGC
7469 of the CO(2-1) line (observed frequency 226.85
GHz) and the underlying continuum (224.2-243.7 GHz).
NGC 7469 was observed in September 2018 by using
the 12m array for a total integration time of 1.48 h
in the configuration C43-4 with 44 antennas, proving
an angular resolution of about 0.4 arcsec and a largest
angular scale of 4.8 arcsec. Visibilities were calibrated
by the NRAO Observatory, using the standard pipeline
and default calibrators. Imaging was performed with
the Common Astronomy Software Applications (CASA;
McMullin et al. 2007), version 5.1.1-5. We created
a continuum map by averaging the visibilities in the
four spectral windows (spws), excluding the spectral
range covered by the CO(2-1) emission line. We produced continuum-subtracted datacubes by fitting and
subtracting a first-order polynomial from the visibilities
of the spw covering CO(2-1). Imaging was performed
with task tclean using the `hogbom` algorithm, a threshold
of three times the root mean square (rms) noise, a briggs
weighting scheme with robust parameter _b_ = 0.5 for the
continuum map and a natural weighting scheme for the
CO(2-1) data cube in order to increase the map sensitivity. The resulting synthesized beam for the continuum
map is 0.492 arcsec _×_ 0.360 arcsec (corresponding to
164 pc _×_ 120 pc), with an rms of 0.0121 mJy/beam.
The CO(2-1) data cube has a beam size of 0.508 arcsec _×_ 0.374 arcsec and a rms noise of 0.518 mJy/beam
for a channel width of 5 km s _[−]_ [1] . This translates into

a mass surface density sensitivity of 7.8 M _⊙_ /beam for
a channel width of 5 km s _[−]_ [1], computed using equation
1. Figure 1 shows (left panel) the millimetre continuum map and (right panel) the continuum-subtracted
velocity-integrated map of the CO(2-1) emission.
We analysed archival VLA observations of NGC 7469
in band K (project code 20A-158, PI Krista L. Smith).
The observations were carried out in April 2020 for a
total integration time of 58.9 h in the frequency range
18-26 GHz. We used the standard calibrated visibilites
provided by the VLA data archive l [1] and we used CASA
5.1.1-5 software to generate the map of K band continuum. We averaged the 62 spw and we produced a
clean map using the `tclean` task and a briggs weighting
scheme with robust parameter _b_ = 0.5. We used the
`hogbom` cleaning algorithm with a detection threshold of
3 times the rms sensitivity. The final continuum map
has an rms of 23.2 _µ_ Jy _/_ beam and a clean beam of 1.029
arcsec _×_ 0.967 arcsec (i.e. 342 pc _×_ 322 pc).
JWST/MIRI (Bouchet et al. 2015; Rieke et al. 2015)
imaging of NGC 7469 was obtained with the F770W
(7.7 _µ_ m) filter with both the BRIGHTSKY and SUB128
subarray modes (program ID 1328, PI Armus Lee). In
this paper we focus the analysis on the SUB128 subarray
data, where the nucleus remained unsaturated, taken on
2022 July 2 with an exposure time of 48 s. The field of
view of 14.8 arcsec _×_ 16.4 arcsec and the pixel size is
0.11 arcsec. The calibrated JWST/MIRI 7.7 _µ_ m map
has a sensitivity of 12 MJy sr _[−]_ [1] pixel _[−]_ [1] . We used the
calibrated images provided by the STSCI Observatory,
downloaded through the MAST portal [2] .


3. ANALYSIS


Within CASA, we modeled and subtracted the central
point source emission in the VLA map to remove its contribution from the circumnuclear region. We used the
task `os.system` to model a point source at the AGN
position (23:03:15.617 +08:52:26.00 J2000, Izumi et al.
2020) with a flux of 5.037 mJy at 22 GHz, corresponding
to 90% of the central beam flux. We performed several
tests with different point source flux normalization, and
checked that with the assumed fraction we avoid arti
ficial over-subtracted regions. The final circumnuclear
region flux is corrected by 15 % and its value is consistent with the central beam flux after point source subtraction. We used the `uvsub` task to subtract the point
source model from the visibility data, so obtaining the
final visibilities. We followed the cleaning procedure de

1 (https://science.nrao.edu/facilities/vla/archive

2 [https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html](https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html)



3


scribed in section 2 to obtain the final map reported in
Figure 2, left panel.
We used the WebbPSF [3] tool version 1.2.1 (Perrin
et al. 2014) to simulate the point-spread function (PSF)
of the JWST/MIRI F770W filter image, with a pixel
size of 0.027 arcsec. We modeled the radial PSF con
tribution by using circular sectors with a radius equal
to the grid cells size, see Section 3, and we derived the
radial correction for the F770W filter map. We corrected both the F770W filter fluxes extracted with the
grid and their associated errors for the PSF contribution
according to their distance from the center, by following
standard error propagation (i.e., convolving the square
of the error map with the square of the PSF error). Due
to the limitations in the current theoretical model for

the JWST PSF, we do not have a robust method for
removing the PSF spikes (see Williams et al. 2024, and
references therein). Therefore we applied this conservative method to subtract and model the PSF contri
bution. We excluded from the analysis the central 1
arcsec ( _∼_ 330 pc) region where the PSF contribution is
dominant.

We used the continuum-subtracted velocity-integrated
CO(2-1) line intensity map to derive the mass surface density of the cold molecular gas, VLA radio map
at 22 GHz to estimate the SFR surface density and
JWST/MIRI F770W filter map to estimate the PAH
emission at 7.7 _µ_ m. Since we analyzed one single PAH
feature at 7.7 _µ_ m, we omit the 7.7 _µ_ m wording from this
point onward. We extract fluxes from a common grid
applied to all maps. First, we regridded all the maps at
the VLA spatial resolution, i.e. the coarser resolution of
our data. The grid is centered at the AGN position and
has 1 arcsec wide (i.e. 0.330 kpc) squared cells, equal
to regridded maps resolution, and a total size of 10 arcsec _×_ 10 arcsec (i.e. 3.3 kpc _×_ 3.3 kpc). Fluxes are
extracted from each cell. If the mean flux in the cell is
below 3rms per pixel, we consider it as an upper limit.
For each grid cell, we derived the corresponding cold
molecular gas mass (M H2 ) surface density (Σ H2 ), SFR
surface density (Σ SFR ) and PAH flux density (Σ PAH ).
The central cell (i.e. the one that contains the AGN) is
not used, since it is not possible to determine and disentangle the AGN contribution to the measured flux with
good accuracy. Indeed, in this region, we expect both a
significant contribution in the JWST image arising from
the dust-reprocessed AGN emission from the torus, and
a possible contribution to the VLA continuum due to
the presence of a core jet-like structure (Lonsdale et al.


3 [https://webbpsf.readthedocs.io](https://webbpsf.readthedocs.io/en/latest/)

4











**Figure** **1.** Left panel: 1.3 mm continuum map. Labels from A to E indicate the five clumps of emission. The position of A
corresponds to the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020). Contours are drawn at (3, 5, 10, 15,
20, 40) _σ_, _σ_ = 0 _._ 0121 mJy/beam. The clean beam (0.492 arcsec _×_ 0.360 arcsec, PA=46 deg) is indicated by the gray ellipse.
Right panel: velocity integrated CO(2-1) (moment-0) map. White contours are drawn at (3, 5, 10, 15, 20, 30) _σ_, _σ_ = 0 _._ 56
Jy/beam.km/s. The clean beam (0.508 _×_ 0.374 arcsec, PA=45 deg) is indicated by the gray ellipse. Regions with emission
below 1 _σ_ are blanked out.


0.00012



4


2


0


2


4



0.00010


0.00008


0.00006


0.00004


0.00002


0.00000



4


2


0


2


4



10 [2]


10 [1]



4 2 0 2 4

Relative RA [arcsec]



4 2 0 2 4

Relative RA [arcsec]



**Figure** **2.** Left panel: VLA 22 GHz radio continuum map (color scale), with corresponding white contours drawn at (3, 5, 8,
10, 15) _σ_, _σ_ = 0 _._ 023 mJy/beam. The clean beam (1.03 arcsec _×_ 0.97 arcsec, PA=-13 deg) is indicated by the gray ellipse. Right
panel: JWST MIRI/F770W image (color scale), with white contours drawn at (3, 5, 10, 15, 20, 30, 50) _σ_, _σ_ = 27 MJy/sr. The
black contours in both panels show the 1.3 mm continuum emission (same as in Figure 1, left panel).



2003; Alberdi et al. 2006). We note that Armus et al.
(2023) verified that in the total mid-infrared spectrum of
NGC 7469 PAH emissions are significantly weaker at the
nucleus, due to the AGN heating effect. They reported
that the SFR from PAH in the nuclear region, 0.3 arcsec

_∼_
( 100pc) diameter circular region, is less than 1% of the
total SFR in NGC 7469.



The Σ H2 in units of M _⊙_ pc _[−]_ [2] is derived from the
velocity-integrated CO(2-1) flux density as:



where _F_ 21 is the conversion factor from the flux density
to the line luminosity _L_ _[′]_ in K km s _[−]_ [1] pc [2] (see Solomon
& Vanden Bout 2005), _i_ is the galaxy inclination angle,



Σ _H_ 2 = _α_ _CO_ _S_ _CO_ (2 _−_ 1) _F_ 21 _cos_ _i_ (1)

_R_ 21

5





1.25


1.50


1.75


2.00


2.25


~~2.50~~


2.75





1.4


1.2


1.0


0.8


0.6


0.4


|MCMC linear fit r < rout<br>MCMC linear fit r > rout|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|MCMC linear fit r < rout<br>MCMC linear fit r > rout|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout||||||||||||||
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|||||||||||||||
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|||||||||||||||
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|||||||||||||||
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout||||||||||||||||||||
|MCMC linear fitr < rout<br>MCMC linear fitr > rout|MCMC linear fitr < rout<br>MCMC linear fitr > rout|||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||



0.4 0.2 0.0 0.2 0.4 0.6 0.82.4 2.6 2.8 3.0 3.2 3.4 3.6
log SFR [[M] [yr] 1 kpc 2 ] log H2 [[M] [pc] 2 ]



**Figure** **3.** Surface brightness at 7.7 _µ_ m from JWST/MIRI imaging versus Σ SFR (left panel), and Σ H 2 (right panel), within the
central 10 arcsec _×_ 10 arcsec region of NGC 7469. The symbols are colored according to their distance from the galaxy center
(color bar). The dashed blue (red) lines are the fits to data for r _<_ r SB (r _>_ r SB ), where r SB _∼_ 900pc is the outer SB ring radius
(Song et al. 2021).


**Table** **1.** Derived parameters for the Σ SFR         - SB PAH and Σ H2         - SB PAH correlations.

|Col1|ΣSFR −SB PAH Σ H2 −SB PAH|Col3|
|---|---|---|
|radius<br>number data points<br>(a)<br>(b)|_ρ_<br>_τ_<br>_n_<br>_k_<br>(c)<br>(d)<br>(e)<br>(f)|_ρ_<br>_τ_<br>_n_<br>_k_<br>(c)<br>(d)<br>(e)<br>(f)|
|r_ >_ 0<br>82<br>r_ <_ rSB<br>31<br>r_ >_ rSB<br>51|0.91<br>0.75<br>1.77 _±_ 0.08<br>-2.56 _±_ 0.03<br>0.76<br>0.56<br>2.16 _±_ 0.20<br>-2.78 _±_ 0.02<br>0.77<br>0.56<br>0.83 _±_ 0.10<br>-2.36 _±_ 0.03|0.84<br>0.68<br>2.17 _±_ 0.11<br>-15.48 _±_ 0.36<br>0.71<br>0.52<br>2.61 _±_ 0.25<br>-10.25 _±_ 0.03<br>0.66<br>0.47<br>0.72 _±_ 0.09<br>-4.39 _±_ 0.03|



**Notes.** The columns report (a) the radius of the data points, (b) the number of data points, (c) the Pearson _ρ_ correlation coefficient, (d)
the Kendall _τ_ rank correlation coefficient, (e) the slope _n_ and (f) the zero-point _k_ of the linear fit _y_ = _nx_ + _k_ .



and _α_ CO is the CO-to-H 2 conversion factor. We adopt
a CO ladder correction factor of _R_ 21 = 0.7 equal to
the mean value found by Casasola et al. (2015), and
_α_ CO = 4 _._ 2 _−_ [+1] 1 _[.]_ _._ [961] 341 [M] _[⊙]_ [(K km s] _[−]_ [1] [ pc] [2] [)] _[−]_ [1] [derived] [adopting]
equation 25 in Accurso et al. (2017), for a stellar mass
of log( _M_ _∗_ _/M_ _⊙_ ) = 10 _._ 5 (D´ıaz-Santos et al. 2007). The
_cos i_ factor is the correction for galaxy inclination, which
we assume _i_ =45 deg (Davies et al. 2004).
Assuming that most of the radio 22 GHz continuum
emission arises from SF, we adopt the radio luminosity
at 22 GHz to derive the SFR. First, we derived the radio luminosity at 1.4 GHz by assuming an average radio
spectrum steepness _α_ = _−_ 0 _._ 85 for the entire galaxy. We
obtained the _α_ parameter by fitting the radio Spectral
Energy Distribution (SED) using the integrated radio



fluxes reported by NED [4] . The _α_ parameter adopted is
consistent with the values used to describe SF regions
in normal galaxies and LIRGs (e.g. Murphy et al. 2012;
Linden et al. 2019, 2020) and with the values derived
by Song et al. (2021). However, we cannot exclude local
variations in the steepness of the radio spectrum that
can affect the final SFR values. Song et al. (2021) derived the spectral index measured from 15 to 33 GHz,
finding values in between _∼_ -0.7 and _∼_ -0.9 in the NGC
7469 nuclear ring. These variations translate into corrections to the SFR up to 10% which will be taken into
account further in the discussion. We then obtained the


4 [https://ned.ipac.caltech.edu](https://ned.ipac.caltech.edu)

6



1.4


1.2


1.0


0.8


0.6


0.4



1.5


1.0


0.5


0.0


0.5


1.0





1.8 2.0 2.2 2.4 2.6 2.8 3.0 3.2 3.4 3.6

2
log H2 [[M] [pc] ]


**Figure** **4.** Spatially resolved star formation law within the central 10 arcsec _×_ 10 arcsec region of NGC 7469. Circles show the
derived quantities in each cell of the grid, coloured according to their distance from the AGN (color bar). The dashed green
lines are the linear fit to the data logΣ SFR = (1 _._ 02 _±_ 0 _._ 07)logΣ H2 + ( _−_ 2 _._ 85 _±_ 0 _._ 02), derived by using the python _emcee_ library
(Foreman-Mackey et al. 2013). Triangles show the derived quantities for NGC 2992 (Zanchettin et al. 2023). The yellow shaded
area shows the best-fit correlation with 0.33 dex scatter found using global measurements for (Kennicutt & De Los Reyes 2021):
logΣ SFR = (0 _._ 98 _±_ 0 _._ 07)logΣ H2 + ( _−_ 2 _._ 27 _±_ 0 _._ 21). The purple shaded area shows the range of values found by Casasola et al.
(2015) for local AGN host galaxies: logΣ SFR = (1 _._ 14 _±_ 0 _._ 01)logΣ H2 + ( _−_ 3 _._ 41 _±_ 0 _._ 02). Solid, dashed, and dotted black lines
represent gas depletion times _τ_ _dep_ of 0.1, 0.5, and 1 Gyr, respectively.



SFR adopting the correlation reported by Shao et al.
(2018) in section 3.2, and the corresponding star formation surface density, Σ SFR, by correcting for galaxy
inclination, i.e. multiplying by the _cos_ _i_ factor as in
equation 1.
The MIRI F770W allows us to sample the 7.7 _µ_ m PAH
emission complex in NGC7469. Although the band is
dominated by the PAH emission feature, it may also include continuum emission due to hot dust. Whitcomb
et al. (2023) showed that the Spitzer/IRS spectra of the
star-forming regions in 75 nearby galaxies (SINGS sample) may have up to 10% continuum contamination in
the F770W filter. Therefore, in a conservative approach,
we assumed that 90% of the flux is attributed to PAH
(Chastenet et al. 2023).


4. DISCUSSION AND CONCLUSION


4.1. _Morphology_ _of_ _the_ _SB_ _ring_



We estimate the global SFR integrated over the central 3.3 kpc _×_ 3.3 kpc into SFR = 11 _._ 5 _±_ 0 _._ 3 M _⊙_ yr _[−]_ [1],
following the prescription of Shao et al. (2018), see Section 3. This estimate does not include the contribution

from the central 330 pc _×_ 330 pc cell. The uncertainty
accounts for a realistic estimate of the systematic scatter in the 1.4 GHz-based method ( _∼_ 0.3 dex according
to Shao et al. 2018). Our SFR estimate is consistent
with the SFR = 21 _±_ 2 _._ 1 M _⊙_ yr _[−]_ [1] by Song et al. (2021)
from the 3-to-33 GHz radio continuum, and with the
range of SFR = 10-30 M _⊙_ yr _[−]_ [1] reported by Lai et al.
(2022) using optical emission lines, namely the Pf _α_ recombination line, [Ne II] and [Ne III]. We found that
the majority, approximately 60%, of the SF occurs in
the SB ring, consistent with Song et al. (2021).
We computed the molecular gas mass over the central 3.3 kpc _×_ 3.3 kpc M(H2) = (6 _._ 4 _±_ 2 _._ 0) _×_ 10 [9] M _⊙_,
where the error is dominated by the uncertainty on _α_ CO
(0.165 dex, Accurso et al. 2017). This estimate is con

sistent within 2 sigma with the values reported in the
literature using different CO transitions (Davies et al.
2004; Izumi et al. 2020; Nguyen et al. 2021; Zhang & Ho
2023). We note that these works focus on the inner _∼_ 1
kpc region of NGC 7469, i.e. the SB ring. We computed
that _∼_ 50% of the total cold molecular gas mass is contained in the SB ring, M(H2) SB = (3 _._ 3 _±_ 1 _._ 0) _×_ 10 [9] M _⊙_ .
The central concentration of gas and SFR is in line with
those observed in local LIRGs (D´ıaz-Santos et al. 2010,
2011). Adopting our estimate of M(H2) and SFR, we
derived the characteristic gas depletion timescale, _τ_ dep
= M(H 2 ) _/_ SFR. We obtained _τ_ dep = (0 _._ 56 _±_ 0 _._ 18) Gyr
for the central 3.3 kpc _×_ 3.3 kpc region, and a shorter
_τ_ dep = (0 _._ 47 _±_ 0 _._ 15) Gyr for the SB ring. Considering
the errors associated with the values, the depletion times
are consistent within one sigma.
Figure 1 shows the distribution of the 1.3 mm continuum and the integrated CO(2-1) flux map (Moment
0 map). In the continuum map, we identify five representative positions (A–E), that are detected as clumps
with SNR _>_ 15. Clumps from A to D are named as in
Izumi et al. (2020), who first identified the clumps using the ALMA 860 _µ_ m continuum map. In addition,
we identify clump E (23:03:15.60 +08:52:24.56, J2000)
where we detect 1.3 mm emission with a statistical significance of _∼_ 18 _σ_ . The 1.3 mm central peak position,
labeled as clump A, is consistent with the AGN position
from VLA 3.5 cm and ALMA 860 _µ_ m continuum emission (Condon et al. 1991; Orienti & Prieto 2010; Izumi
et al. 2020). Due to the PSF smearing of the central
AGN emission in MIRI 7.7 _µ_ m, we excluded from the
following analysis the central cell, which contains also
the CND (Davies et al. 2004; Izumi et al. 2015). Figure 2 shows the VLA 22 GHz emission map (left panel)
and the JWST/MIRI PAH emission map (right panel),
both with 1.3 mm emission contours overlaid. The 1.3

continuum map traces the dust distribution across the
SB ring, which shows a morphology that is remarkably
similar to those traced by PAHs and radio continuum
at 22 GHz. The three tracers reproduce the morphology of the SB ring with good agreement. In particular,
clumps B, C, and D are detected with similar morphology and size in the dust continuum, CO(2-1), 22 GHz,
and the PAH emission. The overall clumps distribution
appears to be consistent also with the 860 _µ_ m continuum (Izumi et al. 2020), suggesting that the 1.3 mm
emission is mainly tracing thermal dust emission heated
by young stars in the SB ring. While the dusty clumps
B, C, D, and E all show prominent counterparts also in
the CO map (Figure 2), the dusty clump E exhibits no
evident counterpart in the radio or mid-IR maps. Interestingly, the 22 GHz radio continuum map presents



7


an emission peak with a significance of 15 _σ_ (23:03:15.63
+08:52:24.98 J2000), offset by about 0.5 arcsec with respect to E along the north-east direction (white and
black contours in the left panel of Figure 3). We exclude
a contribution from the unresolved radio jet at this location, as a core jet-like structure was only detected at
the nucleus (Lonsdale et al. 2003; Alberdi et al. 2006).
Indeed, the local enhancement in the radio emission may
be attributed to a gas inflow associated to the SB ring
and to the two-arm spiral structure, suggested by the
high velocity dispersion of the cold molecular gas at this
location (Nguyen et al. 2021). Clumps B and D are located at the endpoints of a bar-like feature identified
by Davies et al. (2004); Fathi et al. (2015); Izumi et al.
(2015). Although the bar structure is detected at a significance level of 12 _σ_ in the CO(2-1) map, it remains
undetected down to 3 _σ_ in the radio continuum and in

the 7.7 _µ_ m maps, despite the high angular resolution of
JWST/MIRI.


4.2. _PAH_ _emission_


In the following, we investigate the correlation between Σ SFR, Σ H 2 and PAH surface brightness, SB PAH .
Figure 3 shows SB PAH versus Σ SFR (left panel), and Σ H 2
(right panel), within the region of NGC 7469 sampled
by the grid. The PAH surface brightness correlates both
with the SFR and the cold molecular gas surface densities. We derived the Pearson _ρ_ and the Kendall _τ_ rank
correlation coefficients (Table 1), finding a higher correlation of SB PAH with Σ SFR than with Σ H2, both for the
SB ring and for external regions. Although the signal-tonoise ratio (SNR) of the radio map is lower than that of
the CO map (Section 2), the correlation between SB PAH
and Σ SFR is stronger and narrower than that with Σ _H_ 2 .
This is likely due to PAH emission being more affected
by the ionizing radiation field of young stars rather than
by the availability of molecular gas (see Jensen et al.
2017; Belfiore et al. 2023, and references therein).
We also observe a steepening of both relations moving
towards the center of the galaxy, as highlighted in Figure
3 by the color gradient of the symbols. To quantify this
steepening, we divided the data into two subsamples: an
inner region within the SB ring (r _<_ r SB ) and an outer
region with r _>_ r SB, where r SB = 900 pc. This value
has been measured by (Song et al. 2021) using the 3 to
30 GHz continuum and is consistent with our maps. We
fit a linear relation _y_ = _nx_ + _k_ to each subsample using
Python package _emcee_ (Foreman-Mackey et al. 2013),
and assuming a constant error on Σ H2 and Σ SFR, equal
to the rms noise of each regridded map. The uncertainty
associated to SB PAH is obtained by convolving the rms
noise of the regridded MIRI map with the uncertainty

8


due to the PSF contribution (Section 3). Blue and red
solid lines in Figure 3 show the fits for r _<_ r SB and
for r _>_ r SB, respectively. For both Σ SFR and Σ H2, the
SB ring shows a steeper slope with respect to r _>_ r SB
(Table 1). In particular, the slope at the SB ring is
_n_ = (2 _._ 16 _±_ 0 _._ 20) whereas at r _>_ r SB is _n_ = (0 _._ 83 _±_ 0 _._ 10).
A similar behavior is seen for the Σ H2 correlation. The
steepening of these relations may be attributed to an
enhancement of recent SF activity in the SB ring structure, as already observed using the 11.3 _µ_ m PAH feature
by Jensen et al. (2017). This is consistent with the presence of a young population of ionizing stars in the SB
ring, as reported by D´ıaz-Santos et al. (2007). Jensen
et al. (2017) measured a negligible contribution of AGNheated dust to the continuum flux at 11 _µ_ m above 200
pc. Therefore, we exclude that this steepening is due
to an increased contribution of AGN-heated dust to the

continuum emission measured in the JWST F770W filter, at the location of the SB ring. Regarding a possible
AGN contribution to PAH destruction, we do not expect a significant effect given the modest luminosity of
our target (L bol _,_ AGN = 3 _._ 5 _×_ 10 [44] erg s _[−]_ [1], Gruppioni
et al. 2016).
Still local variations in gas properties, including composition, turbulence, and metallicity, significantly influence the CO-to-H2 conversion factor (Leroy et al. 2011;
Narayanan et al. 2012; Papadopoulos et al. 2012; Bolatto
et al. 2013; Sandstrom et al. 2013; Teng et al. 2024).
Oxygen abundances compatible with solar metallicity
were reported for NGC 7469 SB ring and outer region
by Cazzoli et al. (2020) and Zamora & D´ıaz (2023) using optical nebular lines. However, metallicity determination is challenging at all spatial scales, particularly
in AGN-affected nuclear regions where it remains unknown. Considering a CO-to-H2 conversion factor accounting for both solar-like metallicity and gas excitation, as prescribed by Narayanan et al. (2012), we found
that the change in slope between SB ring and outer disk
remains appreciable. A significantly decreasing metallicity gradient toward the nucleus could still mitigate
the slope change in the SB PAH _−_ Σ H2 relation. However, there are no evidence for such trend. Additionally,
several factors, including grain size distribution, temperature, ionization field, metallicity, and dust amount
can affect PAH luminosity (e.g. Chastenet et al. 2023;
Whitcomb et al. 2024). The 7.7 _µ_ m complex is associated with larger, positively charged ions (Galliano
et al. 2008; Draine et al. 2021; Rigopoulou et al. 2021;
Maragkoudakis et al. 2022), and its emission can increase around young stars due to a stronger radiation
field. However, investigating PAH properties such as
grain size distribution and ionization fraction involves



examining the ratios between various MIR PAH features (Lai et al. 2023; Bohn et al. 2023). Finally, spatially resolved studies in nearby galaxies have reported
a steepening of the radio spectral index with increasing
distance from the center (e.g. Paladino et al. 2009; Basu
et al. 2015; Roy & Manna 2021), with additional local
variations in regions of active SF (Westcott et al. 2018).
We therefore cannot exclude that the superposition of
these effects could cause the observed slope change in
the logSB PAH _−_ logΣ SFR relation.


4.3. _The_ _star_ _formation_ _law_


Figure 4 shows the spatially resolved star formation law on a _∼_ 300 pc scale for NGC 7469. The
plot also includes NGC 2992 measurements obtained
with a similar method on _∼_ 200 pc scales (Zanchettin et al. 2023), and the relations derived for compilation of local AGN (Casasola et al. 2015), and ultraluminous/luminous infrared galaxies (U/LIRGs, L IR _>_
10 [12] L _⊙_, and _>_ 10 [11] L _⊙_, respectively, Kennicutt &
De Los Reyes 2021). The purple shaded area shows
the K-S relation for local AGN hosts drawn from
the NUclei of GAlaxies (NUGA) survey, characterized by SFR within _−_ 0 _._ 9 _<_ log SFR _/_ M _⊙_ yr _[−]_ [1] _<_ 0 _._ 8
and cold molecular gas masses in the range 8 _._ 5 _<_
logM(H 2 ) _/_ M _⊙_ yr _[−]_ [1] _<_ 9 _._ 6 (see Casasola et al. 2015, and
references therein). The yellow shaded are shows the
star formation law found for dusty starbursts U/LIRGs,
with 1 _._ 1 _<_ log SFR _/_ M _⊙_ yr _[−]_ [1] _<_ 1 _._ 8, and cold molecular gas masses 9 _._ 4 _<_ logM(H 2 ) _/_ M _⊙_ yr _[−]_ [1] _<_ 10 _._ 2 (Kennicutt & De Los Reyes 2021). We adopted the same
fitting method as described above, taking into account
the uncertainties both on Σ SFR and on Σ H2, and the
best fit linear relation for all data points is logΣ SFR =
(1 _._ 02 _±_ 0 _._ 07)logΣ H2 + ( _−_ 2 _._ 85 _±_ 0 _._ 02) (green solid line
in Figure 4). The slope of this relation is consistent with that obtained by fitting the SB ring alone,
while we find a flatter slope for the fit of the outer region ( _n_ = 0 _._ 5 _±_ 0 _._ 1). As the latter fit is dominated
by data points with low SNR, we consider the global
logΣ SFR _−_ logΣ H2 relation as best-fit for NGC 7469.
The star formation relation derived for the NUGA
AGN (purple shaded area) exhibits a slightly steeper
slope ( _n_ = 1 _._ 14 _±_ 0 _._ 01) and a _∼_ 0.6 dex offset towards
lower SFR surface densities with respect to NGC 7469.
Kennicutt & De Los Reyes (2021) found that starburst
galaxies and U/LIRGs are fitted by a linear relation with
slope _n_ = (0 _._ 98 _±_ 0 _._ 07), consistent with the one derived for NGC 7469 in this work, and a _∼_ 0.6 dex offset
in the zero-point towards higher SFR surface densities
(yellow shaded area). Considering the associated errors,
the slopes of the relations reported by Kennicutt & De

Los Reyes (2021) and Casasola et al. (2015) are roughly
consistent within three sigma. Figure 4 indicates that
the individual regions of NGC 7469 occupy an intermediate area of the logΣ SFR _−_ logΣ H2 plane, corresponding
to an intermediate star formation regime between local AGNs and U/LIRGs. The observed scatter in the
data points can reflect local variations in the physical
conditions of the ISM from which stars form, such as
the morphology and concentration of the gas, and any
differences in gas excitation. Additionally, local fluctuations in physical quantities affect the conversion (e.g.,
CO-to-H2 conversion factor, radio steepness) from observables to physical quantities. In Figure 4, we report
the characteristic gas depletion timescales: NGC 7469
data points show an average _τ_ dep _,_ mean = (0 _._ 66 _±_ 0 _._ 02)
Gyr, where the uncertainty is the standard error of the
mean. The measurements of the circumnuclear region
of NGC 2992 (black triangles, Zanchettin et al. 2023),
derived with a spatial resolution of 200 pc, populate regions of the star formation law chart characterized by
both relatively lower logΣ SFR and logΣ H2, with respect
to NGC 7469. The difference observed between NGC
2992 and our target may reflect the fact that individual
galaxies may show different star formation laws, as highlighted by Casasola et al. (2022) in their work on a set of
nearby spiral DustPedia [5] galaxies. However, NGC 2992
has an average _τ_ dep _,_ mean = (0 _._ 38 _±_ 0 _._ 07) Gyr, consistent
with that measured in our target.



1


2


3


4


5


6


7


8


9


10


11


12


13


14


15


16


17


18


19


20


21


22


23


24


25


26


27


28


29


30



.



9


This work is based in part on observations made with
the NASA/ESA/CSA James Webb Space Telescope.
The data were obtained from the Mikulski Archive for

Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities
for Research in Astronomy, Inc., under NASA contract
NAS 5-03127 for JWST. These observations are asso
ciated with program No. 1328. The _JWST_ data used
in this paper can be found in MAST: [10.17909/3x02-](http://dx.doi.org/10.17909/3x02-0q74)
[0q74.](http://dx.doi.org/10.17909/3x02-0q74) This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2017.1.00078.S ALMA is a
partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ. Based on observations
No. 20A-158 with the National Radio Astronomy Observatory which is a facility of the National Science
Foundation operated under cooperative agreement by
Associated Universities, Inc. We acknowledge financial support from PRIN MIUR contract 2017PH3WAT,
and PRIN MAIN STREAM INAF ”Black hole winds

and the baryon cycle”. We acknowledge support from
the INAF Mini Grant GO/GTO ”SHORES: Serendipitous H-ATLAS fields Observations of Radio Extragalactic Sources”. M.B. acknowledges support from
INAF project 1.05.12.04.01 - MINI-GRANTS di RSN1
”Mini-feedback” and FVG LR 2/2011 project D55microgrants23 ”Hyper-gal”.



Accurso, G., Saintonge, A., Catinella, B., et al. 2017,


MNRAS, 470, 4750, doi: [10.1093/mnras/stx1556](http://doi.org/10.1093/mnras/stx1556)



_Facilities:_ JWST(MIRI), ALMA, VLA


_Software:_ astropy (Astropy Collaboration et al.
2013, 2018), emcee (Foreman-Mackey et al. 2013), CASA
(McMullin et al. 2007), WebbPSF (Perrin et al. 2014)


REFERENCES


Alonso-Herrero, A., Pereira-Santaella, M., Rigopoulou, D.,


et al. 2020, A&A, 639, A43,


doi: [10.1051/0004-6361/202037642](http://doi.org/10.1051/0004-6361/202037642)



Alberdi, A., Colina, L., Torrelles, J. M., et al. 2006, ApJ,


638, 938, doi: [10.1086/498859](http://doi.org/10.1086/498859)


5. ACKNOWLEDGMENTS


5 [http://dustpedia.astro.noa.gr/](http://dustpedia.astro.noa.gr/)



Arango-Toro, R. C., Ciesla, L., Ilbert, O., et al. 2023, A&A,


675, A126, doi: [10.1051/0004-6361/202345848](http://doi.org/10.1051/0004-6361/202345848)


Armus, L., Charmandaris, V., Bernard-Salas, J., et al.


2007, ApJ, 656, 148, doi: [10.1086/510107](http://doi.org/10.1086/510107)


Armus, L., Lai, T., U, V., et al. 2023, ApJL, 942, L37,


doi: [10.3847/2041-8213/acac66](http://doi.org/10.3847/2041-8213/acac66)

10


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J.,

et al. 2013, A&A, 558, A33,

doi: [10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)

Astropy Collaboration, Price-Whelan, A. M., Sip˝ocz, B. M.,
et al. 2018, AJ, 156, 123, doi: [10.3847/1538-3881/aabc4f](http://doi.org/10.3847/1538-3881/aabc4f)

Basu, A., Beck, R., Schmidt, P., & Roy, S. 2015, MNRAS,
449, 3879, doi: [10.1093/mnras/stv510](http://doi.org/10.1093/mnras/stv510)

Belfiore, F., Leroy, A. K., Williams, T. G., et al. 2023,
A&A, 678, A129, doi: [10.1051/0004-6361/202347175](http://doi.org/10.1051/0004-6361/202347175)

Bigiel, F., Leroy, A. K., Walter, F., et al. 2011, ApJL, 730,
L13, doi: [10.1088/2041-8205/730/2/L13](http://doi.org/10.1088/2041-8205/730/2/L13)

Bohn, T., Inami, H., Diaz-Santos, T., et al. 2023, ApJL,

942, L36, doi: [10.3847/2041-8213/acab61](http://doi.org/10.3847/2041-8213/acab61)

Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A,
51, 207, doi: [10.1146/annurev-astro-082812-140944](http://doi.org/10.1146/annurev-astro-082812-140944)

Bouchet, P., Garc´ıa-Mar´ın, M., Lagage, P. O., et al. 2015,
PASP, 127, 612, doi: [10.1086/682254](http://doi.org/10.1086/682254)

Casasola, V., Hunt, L., Combes, F., & Garc´ıa-Burillo, S.

2015, A&A, 577, A135,

doi: [10.1051/0004-6361/201425313](http://doi.org/10.1051/0004-6361/201425313)

Casasola, V., Bianchi, S., Magrini, L., et al. 2022, A&A,
668, A130, doi: [10.1051/0004-6361/202245043](http://doi.org/10.1051/0004-6361/202245043)

Cazzoli, S., Gil de Paz, A., M´arquez, I., et al. 2020,

MNRAS, 493, 3656, doi: [10.1093/mnras/staa409](http://doi.org/10.1093/mnras/staa409)

Chastenet, J., Sutter, J., Sandstrom, K., et al. 2023, ApJL,

944, L12, doi: [10.3847/2041-8213/acac94](http://doi.org/10.3847/2041-8213/acac94)

Condon, J. J., Huang, Z. P., Yin, Q. F., & Thuan, T. X.
1991, ApJ, 378, 65, doi: [10.1086/170407](http://doi.org/10.1086/170407)

Cortzen, I., Garrett, J., Magdis, G., et al. 2019, MNRAS,
482, 1618, doi: [10.1093/mnras/sty2777](http://doi.org/10.1093/mnras/sty2777)

Davies, R. I., Tacconi, L. J., & Genzel, R. 2004, ApJ, 602,

148, doi: [10.1086/380995](http://doi.org/10.1086/380995)

Dey, B., Rosolowsky, E., Cao, Y., et al. 2019, MNRAS,
488, 1926, doi: [10.1093/mnras/stz1777](http://doi.org/10.1093/mnras/stz1777)

D´ıaz-Santos, T., Alonso-Herrero, A., Colina, L., Ryder,

S. D., & Knapen, J. H. 2007, ApJ, 661, 149,

doi: [10.1086/513089](http://doi.org/10.1086/513089)

D´ıaz-Santos, T., Charmandaris, V., Armus, L., et al. 2010,

ApJ, 723, 993, doi: [10.1088/0004-637X/723/2/993](http://doi.org/10.1088/0004-637X/723/2/993)
—. 2011, ApJ, 741, 32, doi: [10.1088/0004-637X/741/1/32](http://doi.org/10.1088/0004-637X/741/1/32)

Draine, B. T., Li, A., Hensley, B. S., et al. 2021, ApJ, 917,
3, doi: [10.3847/1538-4357/abff51](http://doi.org/10.3847/1538-4357/abff51)

Farrah, D., Lonsdale, C. J., Weedman, D. W., et al. 2008,

ApJ, 677, 957, doi: [10.1086/529485](http://doi.org/10.1086/529485)

Fathi, K., Izumi, T., Romeo, A. B., et al. 2015, ApJL, 806,

L34, doi: [10.1088/2041-8205/806/2/L34](http://doi.org/10.1088/2041-8205/806/2/L34)

Ford, G. P., Gear, W. K., Smith, M. W. L., et al. 2013,

ApJ, 769, 55, doi: [10.1088/0004-637X/769/1/55](http://doi.org/10.1088/0004-637X/769/1/55)

Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman,
J. 2013, PASP, 125, 306, doi: [10.1086/670067](http://doi.org/10.1086/670067)



Galliano, F., Madden, S. C., Tielens, A. G. G. M., Peeters,

E., & Jones, A. P. 2008, ApJ, 679, 310,

doi: [10.1086/587051](http://doi.org/10.1086/587051)

Genzel, R., Weitzel, L., Tacconi-Garman, L. E., et al. 1995,

ApJ, 444, 129, doi: [10.1086/175588](http://doi.org/10.1086/175588)

Genzel, R., Lutz, D., Sturm, E., et al. 1998, ApJ, 498, 579,

doi: [10.1086/305576](http://doi.org/10.1086/305576)

Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010,

MNRAS, 407, 2091,

doi: [10.1111/j.1365-2966.2010.16969.x](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

Gioia, I. M., Gregorini, L., & Klein, U. 1982, A&A, 116, 164

Gruppioni, C., Berta, S., Spinoglio, L., et al. 2016,
MNRAS, 458, 4297, doi: [10.1093/mnras/stw577](http://doi.org/10.1093/mnras/stw577)

Hao, C.-N., Kennicutt, R. C., Johnson, B. D., et al. 2011,

ApJ, 741, 124, doi: [10.1088/0004-637X/741/2/124](http://doi.org/10.1088/0004-637X/741/2/124)

Izumi, T., Kohno, K., Aalto, S., et al. 2015, ApJ, 811, 39,

doi: [10.1088/0004-637X/811/1/39](http://doi.org/10.1088/0004-637X/811/1/39)

Izumi, T., Nguyen, D. D., Imanishi, M., et al. 2020, ApJ,
898, 75, doi: [10.3847/1538-4357/ab9cb1](http://doi.org/10.3847/1538-4357/ab9cb1)

Jensen, J. J., H¨onig, S. F., Rakshit, S., et al. 2017,
MNRAS, 470, 3071, doi: [10.1093/mnras/stx1447](http://doi.org/10.1093/mnras/stx1447)

Kennicutt, Robert C., J. 1998a, ApJ, 498, 541,

doi: [10.1086/305588](http://doi.org/10.1086/305588)

—. 1998b, ARA&A, 36, 189,

doi: [10.1146/annurev.astro.36.1.189](http://doi.org/10.1146/annurev.astro.36.1.189)

Kennicutt, Robert C., J., & De Los Reyes, M. A. C. 2021,
ApJ, 908, 61, doi: [10.3847/1538-4357/abd3a2](http://doi.org/10.3847/1538-4357/abd3a2)

Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531,

doi: [10.1146/annurev-astro-081811-125610](http://doi.org/10.1146/annurev-astro-081811-125610)

Klein, U., & Emerson, D. T. 1981, A&A, 94, 29

Kreckel, K., Faesi, C., Kruijssen, J. M. D., et al. 2018,
ApJL, 863, L21, doi: [10.3847/2041-8213/aad77d](http://doi.org/10.3847/2041-8213/aad77d)

Lai, T. S. Y., Armus, L., U, V., et al. 2022, ApJL, 941, L36,

doi: [10.3847/2041-8213/ac9ebf](http://doi.org/10.3847/2041-8213/ac9ebf)

Lai, T. S. Y., Armus, L., Bianchin, M., et al. 2023, ApJL,

957, L26, doi: [10.3847/2041-8213/ad0387](http://doi.org/10.3847/2041-8213/ad0387)

Landt, H., Bentz, M. C., Ward, M. J., et al. 2008, ApJS,

174, 282, doi: [10.1086/522373](http://doi.org/10.1086/522373)

Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ,
737, 12, doi: [10.1088/0004-637X/737/1/12](http://doi.org/10.1088/0004-637X/737/1/12)

Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ,
146, 19, doi: [10.1088/0004-6256/146/2/19](http://doi.org/10.1088/0004-6256/146/2/19)

Linden, S. T., Murphy, E. J., Dong, D., et al. 2020, ApJS,
248, 25, doi: [10.3847/1538-4365/ab8a4d](http://doi.org/10.3847/1538-4365/ab8a4d)

Linden, S. T., Song, Y., Evans, A. S., et al. 2019, ApJ, 881,
70, doi: [10.3847/1538-4357/ab2872](http://doi.org/10.3847/1538-4357/ab2872)

Lonsdale, C. J., Lonsdale, C. J., Smith, H. E., & Diamond,

P. J. 2003, ApJ, 592, 804, doi: [10.1086/375778](http://doi.org/10.1086/375778)

Mahajan, S., Ashby, M. L. N., Willner, S. P., et al. 2019,
MNRAS, 482, 560, doi: [10.1093/mnras/sty2699](http://doi.org/10.1093/mnras/sty2699)

Maragkoudakis, A., Boersma, C., Temi, P., Bregman, J. D.,

& Allamandola, L. J. 2022, ApJ, 931, 38,

doi: [10.3847/1538-4357/ac666f](http://doi.org/10.3847/1538-4357/ac666f)

McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, in Astronomical Society of the Pacific

Conference Series, Vol. 376, Astronomical Data Analysis

Software and Systems XVI, ed. R. A. Shaw, F. Hill, &

D. J. Bell, 127

Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011,
ApJ, 737, 67, doi: [10.1088/0004-637X/737/2/67](http://doi.org/10.1088/0004-637X/737/2/67)

Murphy, E. J., Bremseth, J., Mason, B. S., et al. 2012,
ApJ, 761, 97, doi: [10.1088/0004-637X/761/2/97](http://doi.org/10.1088/0004-637X/761/2/97)

Narayanan, D., Krumholz, M. R., Ostriker, E. C., &

Hernquist, L. 2012, MNRAS, 421, 3127,

doi: [10.1111/j.1365-2966.2012.20536.x](http://doi.org/10.1111/j.1365-2966.2012.20536.x)

Nguyen, D. D., Izumi, T., Thater, S., et al. 2021, MNRAS,
504, 4123, doi: [10.1093/mnras/stab1002](http://doi.org/10.1093/mnras/stab1002)

Onodera, S., Kuno, N., Tosaki, T., et al. 2010, ApJL, 722,

L127, doi: [10.1088/2041-8205/722/2/L127](http://doi.org/10.1088/2041-8205/722/2/L127)

Orienti, M., & Prieto, M. A. 2010, MNRAS, 401, 2599,

doi: [10.1111/j.1365-2966.2009.15837.x](http://doi.org/10.1111/j.1365-2966.2009.15837.x)

Paladino, R., Murgia, M., & Orr`u, E. 2009, A&A, 503, 747,
doi: [10.1051/0004-6361/200911870](http://doi.org/10.1051/0004-6361/200911870)

Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M.,

et al. 2012, MNRAS, 426, 2601,

doi: [10.1111/j.1365-2966.2012.21001.x](http://doi.org/10.1111/j.1365-2966.2012.21001.x)

Peeters, E., Spoon, H. W. W., & Tielens, A. G. G. M. 2004,

ApJ, 613, 986, doi: [10.1086/423237](http://doi.org/10.1086/423237)

P´erez-Torres, M. A., Alberdi, A., Colina, L., et al. 2009,

MNRAS, 399, 1641,

doi: [10.1111/j.1365-2966.2009.15389.x](http://doi.org/10.1111/j.1365-2966.2009.15389.x)

Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al.

2014, in Society of Photo-Optical Instrumentation
Engineers (SPIE) Conference Series, Vol. 9143, Space

Telescopes and Instrumentation 2014: Optical, Infrared,

and Millimeter Wave, ed. J. Oschmann, Jacobus M.,

M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X,

doi: [10.1117/12.2056689](http://doi.org/10.1117/12.2056689)

Pessa, I., Schinnerer, E., Leroy, A. K., et al. 2022, A&A,
663, A61, doi: [10.1051/0004-6361/202142832](http://doi.org/10.1051/0004-6361/202142832)

Puget, J. L., & Leger, A. 1989, ARA&A, 27, 161,
doi: [10.1146/annurev.aa.27.090189.001113](http://doi.org/10.1146/annurev.aa.27.090189.001113)

Riechers, D. A., Pope, A., Daddi, E., et al. 2014, ApJ, 786,

31, doi: [10.1088/0004-637X/786/1/31](http://doi.org/10.1088/0004-637X/786/1/31)

Rieke, G. H., Wright, G. S., B¨oker, T., et al. 2015, PASP,
127, 584, doi: [10.1086/682252](http://doi.org/10.1086/682252)

Rigopoulou, D., Barale, M., Clary, D. C., et al. 2021,
MNRAS, 504, 5287, doi: [10.1093/mnras/stab959](http://doi.org/10.1093/mnras/stab959)

Roy, S., & Manna, S. 2021, MNRAS, 507, 4734,
doi: [10.1093/mnras/stab2441](http://doi.org/10.1093/mnras/stab2441)


Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013,
ApJ, 777, 5, doi: [10.1088/0004-637X/777/1/5](http://doi.org/10.1088/0004-637X/777/1/5)



11


Schmidt, M. 1959, ApJ, 129, 243, doi: [10.1086/146614](http://doi.org/10.1086/146614)


—. 1963, ApJ, 137, 758, doi: [10.1086/147553](http://doi.org/10.1086/147553)


Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142,


37, doi: [10.1088/0004-6256/142/2/37](http://doi.org/10.1088/0004-6256/142/2/37)


Shao, L., Koribalski, B. S., Wang, J., Ho, L. C., &


Staveley-Smith, L. 2018, MNRAS, 479, 3509,


doi: [10.1093/mnras/sty1608](http://doi.org/10.1093/mnras/sty1608)


Shipley, H. V., Papovich, C., Rieke, G. H., Brown, M. J. I.,


& Moustakas, J. 2016, ApJ, 818, 60,


doi: [10.3847/0004-637X/818/1/60](http://doi.org/10.3847/0004-637X/818/1/60)


Soifer, B. T., Bock, J. J., Marsh, K., et al. 2003, AJ, 126,


143, doi: [10.1086/375647](http://doi.org/10.1086/375647)


Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43,


677, doi: [10.1146/annurev.astro.43.051804.102221](http://doi.org/10.1146/annurev.astro.43.051804.102221)


Song, Y., Linden, S. T., Evans, A. S., et al. 2021, ApJ, 916,


73, doi: [10.3847/1538-4357/ac05c2](http://doi.org/10.3847/1538-4357/ac05c2)


Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL,


945, L19, doi: [10.3847/2041-8213/acbd9c](http://doi.org/10.3847/2041-8213/acbd9c)


Tabatabaei, F. S., Schinnerer, E., Krause, M., et al. 2017,


ApJ, 836, 185, doi: [10.3847/1538-4357/836/2/185](http://doi.org/10.3847/1538-4357/836/2/185)


Teng, Y.-H., Chiang, I.-D., Sandstrom, K. M., et al. 2024,


ApJ, 961, 42, doi: [10.3847/1538-4357/ad10ae](http://doi.org/10.3847/1538-4357/ad10ae)


Valiante, E., Lutz, D., Sturm, E., et al. 2007, ApJ, 660,


1060, doi: [10.1086/513306](http://doi.org/10.1086/513306)


Veilleux, S., Rupke, D. S. N., Kim, D. C., et al. 2009, ApJS,


182, 628, doi: [10.1088/0067-0049/182/2/628](http://doi.org/10.1088/0067-0049/182/2/628)


Westcott, J., Brinks, E., Hindson, L., Beswick, R., &


Heesen, V. 2018, MNRAS, 475, 5116,


doi: [10.1093/mnras/sty028](http://doi.org/10.1093/mnras/sty028)


Whitcomb, C. M., Sandstrom, K., Leroy, A., & Smith, J.


D. T. 2023, ApJ, 948, 88, doi: [10.3847/1538-4357/acc316](http://doi.org/10.3847/1538-4357/acc316)


Whitcomb, C. M., Smith, J. D. T., Sandstrom, K., et al.


2024, arXiv e-prints, arXiv:2405.09685,


doi: [10.48550/arXiv.2405.09685](http://doi.org/10.48550/arXiv.2405.09685)


Williams, T. G., Lee, J. C., Larson, K. L., et al. 2024,


arXiv e-prints, arXiv:2401.15142,


doi: [10.48550/arXiv.2401.15142](http://doi.org/10.48550/arXiv.2401.15142)


Xie, Y., & Ho, L. C. 2019, ApJ, 884, 136,


doi: [10.3847/1538-4357/ab4200](http://doi.org/10.3847/1538-4357/ab4200)


Xu, X., & Wang, J. 2022, ApJ, 933, 110,


doi: [10.3847/1538-4357/ac7222](http://doi.org/10.3847/1538-4357/ac7222)

Zamora, S., & D´ıaz, A. [´] I. 2023, arXiv e-prints,


arXiv:2310.12895, doi: [10.48550/arXiv.2310.12895](http://doi.org/10.48550/arXiv.2310.12895)


Zanchettin, M. V., Feruglio, C., Massardi, M., et al. 2023,


A&A, 679, A88, doi: [10.1051/0004-6361/202245729](http://doi.org/10.1051/0004-6361/202245729)


Zhang, L., & Ho, L. C. 2023, ApJL, 953, L9,


doi: [10.3847/2041-8213/acea73](http://doi.org/10.3847/2041-8213/acea73)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[2].provided.evidence[0]",
  "value": "Integrated radio fluxes used to fit the radio SED and obtain the average radio spectral index alpha = -0.85.",
  "failed_quote": "First, we derived the radio luminosity at 1.4 GHz by assuming an average radio spectrum steepness α = −0.85 for the entire galaxy. We obtained the α parameter by fitting the radio Spectral Energy Distribution (SED) using the integrated radio fluxes reported by NED."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Stellar mass log(M_*/M_sun) = 10.5.",
  "failed_quote": "and α_CO = 4.2 +1.961 -1.341 M_⊙ (K km s^-1 pc^2)^-1 derived adopting equation 25 in Accurso et al. (2017), for a stellar mass of log(M_*/M_⊙) = 10.5 (Díaz-Santos et al. 2007)."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Simulated point-spread function (PSF) of the JWST/MIRI F770W filter image generated with WebbPSF version 1.2.1 with a pixel size of 0.027 arcsec.",
  "failed_quote": "We used the WebbPSF tool version 1.2.1 (Perrin et al. 2014) to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image, with a pixel size of 0.027 arcsec."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "CO-to-H2 conversion factor alpha_CO = 4.2 (+1.961/-1.341) M_sun (K km s^-1 pc^2)^-1 derived from equation 25.",
  "failed_quote": "and α_CO = 4.2 +1.961 -1.341 M_⊙ (K km s^-1 pc^2)^-1 derived adopting equation 25 in Accurso et al. (2017), for a stellar mass of log(M_*/M_⊙) = 10.5 (Díaz-Santos et al. 2007)."
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Radio 1.4 GHz luminosity to SFR calibration.",
  "failed_quote": "We then obtained the SFR adopting the correlation reported by Shao et al. (2018) in section 3.2"
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Simulate the JWST/MIRI F770W PSF using WebbPSF (pixel size 0.027 arcsec), model the radial PSF contribution in circular sectors with radius equal to the grid cell size (1 arcsec), and apply radial correction to extracted F770W fluxes and errors.",
  "failed_quote": "We used the WebbPSF tool version 1.2.1 (Perrin et al. 2014) to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image, with a pixel size of 0.027 arcsec."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Simulated PSF pixel size = 0.027 arcsec, circular sector radius = 1 arcsec, central 1 arcsec (~330 pc) excluded",
  "failed_quote": "We used the WebbPSF tool version 1.2.1 (Perrin et al. 2014) to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image, with a pixel size of 0.027 arcsec."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Regrid ALMA CO(2-1), VLA 22 GHz, and JWST F770W maps to the VLA spatial resolution; apply a 10 arcsec x 10 arcsec grid of 1 arcsec x 1 arcsec (0.330 kpc) cells centered on the AGN; exclude the central AGN cell and cells with mean flux < 3 rms/pixel; convert extracted fluxes to Sigma_H2 (Eq. 1), Sigma_SFR (via 1.4 GHz extrapolation and Shao et al. 2018), and SB_PAH, plus integrated M(H2), SFR, and ",
  "failed_quote": "The Σ_H2 in units of M_⊙ pc^-2 is derived from the velocity-integrated CO(2-1) flux density as: Σ_H2 = α_CO S_CO(2−1) / R_21 F_21 cos i (1)"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "Grid size = 10 arcsec x 10 arcsec (3.3 kpc x 3.3 kpc), cell size = 1 arcsec x 1 arcsec (0.330 kpc), detection threshold = 3 rms per pixel, number of valid data points = 82 (31 at r < r_SB, 51 at r > r_SB)",
  "failed_quote": "r > 0 82 r < r_SB 31 r > r_SB 51"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "D_L = 72.1 Mpc (0.338 kpc/arcsec); inclination i = 45 deg; R_21 = 0.7; alpha_CO = 4.2 (+1.961/-1.341) M_sun (K km s^-1 pc^2)^-1 for log(M_*/M_sun) = 10.5; radio spectral index alpha = -0.85 between 1.4 and 22 GHz; 90% of F770W flux from PAH.",
  "failed_quote": "We adopt a CO ladder correction factor of R_21 = 0.7 equal to the mean value found by Casasola et al. (2015), and α_CO = 4.2 +1.961 -1.341 M_⊙ (K km s^-1 pc^2)^-1 derived adopting equation 25 in Accurso et al. (2017), for a stellar mass of log(M_*/M_⊙) = 10.5 (Díaz-Santos et al. 2007). The cos i factor is the correction for galaxy inclination, which we assume i =45 deg (Davies et al. 2004)."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Radio SED fitted using integrated radio fluxes from NED to obtain spectral index alpha = -0.85.",
  "failed_quote": "We obtained the α parameter by fitting the radio Spectral Energy Distribution (SED) using the integrated radio fluxes reported by NED."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "r_SB = 900 pc; N = 82 total points (31 for r < r_SB, 51 for r > r_SB)",
  "failed_quote": "r > 0 82 r < r_SB 31 r > r_SB 51"
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Constant error on Sigma_H2 and Sigma_SFR equal to the rms noise of each regridded map; error on SB_PAH obtained by convolving rms noise of regridded MIRI map with PSF uncertainty.",
  "failed_quote": "assuming a constant error on Σ_H2 and Σ_SFR, equal to the rms noise of each regridded map. The uncertainty associated to SB_PAH is obtained by convolving the rms noise of the regridded MIRI map with the uncertainty due to the PSF contribution (Section 3)."
 },
 {
  "path": "software[0].used_for.evidence[1]",
  "value": "Imaging ALMA Band 6 continuum and CO(2-1) data cube, continuum subtraction, modeling and subtracting central AGN point source in VLA K-band visibilities (uvsub), and imaging VLA 22 GHz continuum (tclean).",
  "failed_quote": "We used the standard calibrated visibilites provided by the VLA data archive l and we used CASA 5.1.1-5 software to generate the map of K band continuum."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Simulating the point-spread function (PSF) of the JWST/MIRI F770W filter image.",
  "failed_quote": "We used the WebbPSF tool version 1.2.1 (Perrin et al. 2014) to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image, with a pixel size of 0.027 arcsec."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "A fifth 1.3 mm continuum clump E (23:03:15.60 +08:52:24.56 J2000) is detected at ~18 sigma with a CO(2-1) counterpart, no mid-IR counterpart, and a 15 sigma 22 GHz radio peak offset by ~0.5 arcsec to the northeast.",
  "failed_quote": "While the dusty clumps B, C, D, and E all show prominent counterparts also in the CO map (Figure 2), the dusty clump E exhibits no evident counterpart in the radio or mid-IR maps. Interestingly, the 22 GHz radio continuum map presents an emission peak with a significance of 15σ (23:03:15.63 +08:52:24.98 J2000), offset by about 0.5 arcsec with respect to E along the north-east direction"
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[1]",
  "value": "Public archival data from ALMA (2017.1.00078.S), VLA data archive (20A-158), and JWST MAST archive (program 1328, DOI: 10.17909/3x02-0q74).",
  "failed_quote": "We used the calibrated images provided by the STSCI Observatory, downloaded through the MAST portal."
 },
 {
  "path": "reproducibility.products_in_archive.evidence[2]",
  "value": "Calibrated JWST/MIRI images from MAST and standard calibrated visibilities from the VLA archive and NRAO ALMA pipeline.",
  "failed_quote": "We used the calibrated images provided by the STSCI Observatory, downloaded through the MAST portal."
 }
]
```
