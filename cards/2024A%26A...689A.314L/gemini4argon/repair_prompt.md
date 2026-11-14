# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.314L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aanda ©ESO 2024
April 9, 2024

## **JWST/NIRSpec and MIRI observations of an expanding, jet-driven** **bubble of warm H 2 in the radio galaxy 3C 326 N**


J. H. Leftley [1], N. P. H. Nesvadba [1], G. Bicknell [2], R. M. J. Janssen [3][,][ 4], D. Mukherjee [5], R. Petrov [1], M. B. Shende [5], and
H. R. M. Zovaro [2][,][ 6]


1 Université de la Côte d’Azur, Observatoire de la Côte d’Azur, CNRS, Laboratoire Lagrange, Bd de l’Observatoire, CS 34229,
06304 Nice cedex 4, France
2 Research School of Astronomy and Astrophysics, Australian National University, Canberra, ACT 2611, Australia
3 Jet Propulsion Laboratory, California Institute of Technology, 4800 Oak Grove Dr., Pasadena, CA 91109, USA
4 Department of Astronomy, California Institute of Technology, 1216 E California Blvd., Pasadena, CA 91125, USA
5 Inter-University Centre for Astronomy and Astrophysics, Pune-411007, India
6 ARC Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Australia


Received ; accepted


**ABSTRACT**


The physical link between AGN activity and the suppression of star formation in their host galaxies is one of the major open questions
of the AGN feedback scenario. The Spitzer space mission revealed a subset of powerful nearby radio galaxies with unusually bright
line emission from warm ( _T_ ≥ 100 K) molecular hydrogen, while typical star-formation tracers like PAHs or a dust continuum, were
exceptionally faint or undetected. Here we present JWST NIRSpec and MIRI MRS IFU observations of one of the best studied galaxies
of this class, 3C 326 N at z=0.09. We identify a total of 19 lines of the S, O, and Q series of ro-vibrational H 2 emission with NIRSpec
at 0.11 [′′] spatial resolution that probe a small amount (1.4 × 10 [4] M ⊙ ) of gas at temperatures _T_ ∼ 1000 K. We also map the rotational
mid-infrared lines of H 2 0–0 S(3), S(5), and S(6) at a spatial resolution of 0.4 [′′] with MIRI/MRS, which probe most of the 2×10 [9] M ⊙ of
warm H 2 in this galaxy. CO band heads show a stellar component consistent with a "slow-rotator", typical of a massive (3 × 10 [11] M ⊙ )
galaxy, and provide us with a reliable systemic redshift of _z_ = 0.08979 ± 0.0003. Extended line emission shows a bipolar bubble
expanding through the molecular disk at velocities of up to 380 km s [−][1], delineated by several bright clumps along the Northern outer
rim, potentially from gas fragmentation. Throughout the disk, the H 2 is very broad, FWHM ∼ 100 − 1300 km s [−][1], and has complex,
dual-component Gaussian line profiles. Extended [FeII]λ1.644 and Paα follow the same morphology, however [NeIII]λ15.56 is more
symmetric about the nucleus. We show that most of the gas, with the exception of [NeIII]λ15.56, is predominantly heated by shocks
driven by the radio jets into the gas, both for the ro-vibrational and rotational H 2 lines, and that the accompanying line broadening
is sufficient to suppress star formation in the molecular gas. We also compare the morphology and kinematics of the rotational and
ro-vibrational lines, finding that the latter can be a good proxy to the global morphology and kinematic properties of the former in
strongly turbulent environments. This demonstrates the potential of using the higher frequency ro-vibrational lines to study turbulent
molecular gas. Provided they are bright enough, this enables studies of terbulence in galaxies at intermediate and high redshifts well
into the Epoch of Reionisation while most rotational lines are redshifted out of the MIRI bandpass for _z_ ≥ 1.5.



**Key words.**


**1.** **Introduction**


Active Galactic Nuclei (AGN) residing in the centres of galaxies
have been prime suspects of regulating star formation in galaxies for more than two decades. Silk & Rees (1998) were first
to recognise that a small fraction of the immense energy output of AGN would suffice to unbind most of the interstellar gas
from massive host galaxies – provided that the AGN energy can
efficiently be injected into the gas of the host galaxy over kiloparsec scales. This would resolve several of the long standing
open questions of extragalactic astrophysics, including, e.g., the
old stellar populations, low gas content, and star formation rates
in massive galaxies, the metal enrichment in the intra-cluster gas
of massive galaxy clusters, or the tight relationship between the
masses of supermassive black holes and, e.g., the masses or central velocity dispersions of the bulges of their host galaxies (e.g.,
Gebhardt et al. 2000; Ferrarese & Merritt 2000; Springel et al.
2005; Croton et al. 2006; Forman et al. 2005; Kirkpatrick et al.



2009; Bharadwaj et al. 2015; Schaye et al. 2015; Weinberger
et al. 2018; Werner & Mernier 2020).
Many observational and theoretical studies have since been
addressing the question of how the AGN energy is injected into
the surrounding gas, and how this affects star formation. Most
of these studies have focused on the rapid gas removal through
galaxy-wide outflows. However, although many observations
have revealed that outflows of molecular, atomic, or ionised gas
are common in the host galaxies of powerful AGN and more
likely related to the AGN rather than concomitant star formation
(e.g., Fiore et al. 2017; Veilleux et al. 2013), uniquely establishing a physical link between the AGN energy injection and
the suppression of star formation is still a challenge. For example, many host galaxies of powerful AGN, and even AGN-driven
outflows, do not show a concomitant deficit in star formation
(Stanley et al. 2017; Ellison et al. 2016).
A remarkable exception is a subclass of (mostly) powerful
radio galaxies. In about 30% of nearby ( _z_ < 0.2) galaxies from
the 3CRR catalogue (Laing et al. 1983) observed with the In

Article number, page 1 of 22

_A&A proofs:_ manuscript no. aanda



frared Spectrograph (IRS) on-board the Spitzer Space Telescope,
Ogle et al. (2007) and Ogle et al. (2010) identified bright midinfrared line emission from luminous, warm molecular hydrogen (Molecular Hydrogen Emission Galaxies, "MOHEGS", see
also Dicken et al. 2012), while typical AGN and star-formation
tracers like forbidden lines, PAHs, or the mid-infrared dust continuum are either weak or undetected.

Due to its very simple, and highly symmetric structure, the
homonuclear H 2 molecule does not have a permanent electric
dipole moment, and therefore radiates only at high gas temperatures, above of-order 100 K. This makes H 2 line emission so elusive in many star forming molecular clouds, which have typical
temperatures of-order 10 K. The galaxies found by Ogle et al.
are remarkable, in that their H 2 line luminosities can reach up
to about 20% of their total infrared dust luminosity (Ogle et al.
2007), which requires a continuous gas heating mechanism over
long timescales (Nesvadba et al. 2010).
These galaxies show also a marked offset from the
Kennicutt-Schmidt relationship between molecular gas mass and
star-formation rate surface densities, as seen in multiple starformation tracers, including PAHs, cold dust observed with Herschel, the UV continuum, or Hα (e.g., Nesvadba et al. 2010;
Alatalo et al. 2015; Lanz et al. 2016; Nesvadba et al. 2021;
Drevet Mulard et al. 2023). In extreme cases, their star-formation
rates can be one to two orders of magnitude lower at a given gasmass surface density than in normal star-forming galaxies, which
might be a signature of suppression of star formation through the
AGN.

Ogle et al. (2010) and Nesvadba et al. (2010) hypothesised
that the bright H 2 line emission in these galaxies is produced by
shocks that are driven into the molecular gas through interactions with the radio jet, as indicated by several line diagnostics
comparing the luminosity of warm H 2 lines with indicators of
AGN and star-formation activity, like PAHs or the mid-infrared
continuum (e.g., Nesvadba et al. 2011; Guillard et al. 2012). This
is also indicated by enhanced line widths of the warm H 2 lines
in these galaxies (Nesvadba et al. 2010; Guillard et al. 2012).
Comparison with CO observations of cold molecular gas suggest that at least in some of these galaxies, the warm molecular
gas component dominates the overall gas budget (Nesvadba et al.
2010; Ogle et al. 2010), with warm molecular gas masses of up
to few×10 [9] M ⊙ (Ogle et al. 2010; Nesvadba et al. 2010).

Nearly 15 years after the end of the cold Spitzer mission, the
James Webb Space Telescope is now again enabling new midinfrared observations of AGN, at orders of magnitude higher
sensitivity, spectral and spatial resolution, albeit somewhat more
restrictive spectral range (e.g., Pereira-Santaella et al. 2022; Lai
et al. 2022; Armus et al. 2023; Álvarez Márquez et al. 2023).
Here we present new observations of one of the best-studied
MOHEGs, 3C 326 N, at _z_ = 0.09, which we obtained through
open-time observations with the integral-field units (IFUs) of the
JWST/Near-Infrared Spectrograph (NIRSpec) and Mid-Infrared
Instrument (MIRI) in Cycle 1. 3C 326 N is a giant FRII radio
galaxy with a radio power of 2.5 × 10 [26] W Hz [−][1] at 327 MHz,
and two Mpc-sized lobes. Willis & Strom (1978) estimated a
spectral age of the radio source of 200 Myrs. 3C 326 N has a
nearby neighbour, 3C 326 S, making it difficult to identify the
source of the radio emission. Both have radio cores. Rawlings
et al. (1990) argued that 3C 326 N is the better candidate, for its
brighter stellar continuum, higher stellar mass of 3 × 10 [11] M ⊙
(Nesvadba et al. 2010), and for being the only galaxy of the two
that has [OIII]5007 line emission consistent with the usual relationship between [OIII]5007 luminosity and radio power.


Article number, page 2 of 22



3C 326 N was observed with Spitzer/IRS by Ogle et al.
(2007), who identified unusually bright H 2 line emission from
the pure-rotational lines between 5 and 30 µm, whereas many
typical AGN lines, and in particular PAHs, were either very
faint or unobserved. The galaxy was further studied by Nesvadba et al. (2010), who obtained IRAM CO(1–0) observations,
and found that the warm gas is most likely heated by shocks,
and that the warm molecular gas dominates the overall molecular gas budget, with a warm molecular gas mass of 2×10 [9] M ⊙ .
They also found Na D absorption indicating a (likely jet-driven)
outflow of about 30 − 40 M ⊙ yr [−][1] in neutral gas, and a terminal velocity of −1800 km s [−][1] . 3C 326 N has a very low starformation rate (SFR= 0.087 [+] − [0] 0 [.] . [106] 046 [M] [⊙] [yr] [−][1] [from] [Herschel] [dust]
photometry; Lanz et al. 2016), and a radiatively weak AGN
( _L_ _X_ = 10 [40][.][63] erg s [−][1] ; Lanz et al. 2016), so that neither star
formation nor AGN are powerful enough to heat the molecular gas (Nesvadba et al. 2010). Moreover, the Cosmic Ray flux
required to heat the observed amount of molecular gas would
be high enough to destroy the H 2 molecules (Nesvadba et al.
2010), which leaves mechanical heating through shocks driven
by the radio source as the only plausible gas heating mechanism.
This was subsequently confirmed through remarkably broad line
widths (FWHM=650 km s [−][1] ) of ro-vibrational emission lines of
H 2 seen with the VLT/SINFONI near-infrared IFU (Nesvadba
et al. 2011), as well as through very high line ratios of H 2 to
Paα, which are also a good shock indicator (Puxley et al. 1990).
These authors also suggested that the line broadening may be
indicative of high gas turbulence, which, if it cascades down to
the usual scales of giant molecular clouds (∼100 pc) may suppress the star formation by the molecular gas. By comparing the
energy injection that can plausibly be injected through star formation, AGN radiation, or the radio jets, Nesvadba et al. (2010)
concluded that only the radio source is powerful enough to explain the observed gas kinematics.
In this work, we aim to provide a more in depth look, through
novel modelling methods and improved data quality and wavelength coverage, into the molecular and ionised gas structures
of 3C 326 N initially probed in these previous works. We provide a rich set of modelled spectral features which we use to deduce a reliable systemic redshift and investigate the kinematics
and heating mechanism of the molecular gas. We also investigate
the potential of the ro-vibrational lines, that are produced by hot
- 1000 K gas which comprises only a small fraction of the total gas mass, as tracers of turbulence in place of pure rotational
lines which are produced by the bulk of the molecular gas at
cooler ∼ 100 K temperatures. The rotational lines are redshifted
out of the MIRI bandpass at _z_ ≥ 1.5 whereas the ro-vibrational
lines are accessible up to the Epoch of Reionisation if they are
bright enough.
The paper is organised as follows. In Section 2 we describe
our observations and data reduction for the JWST and ancillary
data sets obtained with ALMA and the JVLA. We then explain
our methodology and Bayesian fitting routine in Section 3, before describing our analysis of the stellar and dust continuum, radio morphology, and kinematics of molecular and warm ionised
gas in Section 4. In Section 5 we discuss our results in the context
of multi-phase molecular gas properties, and star formation. We
then use this source to investigate what our results imply about
observations of distant galaxies in the early Universe, where rotational lines are not observable with MIRI, in Section 6. We
summarise our results in Section 7.

Throughout the paper we use the flat Planck Collaboration
et al. (2016) cosmology, where _H_ 0 = 67.8 km s [−][1] Mpc [−][1] and
Ω _M_ = 0.308. In this cosmology, the luminosity distance to

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST



3C 326 N at _z_ = 0.08979 is _D_ _L_ = 423.6 Mpc, and the angular size distance, _D_ _A_ = 356.8 Mpc. 1.729 kpc are projected onto
1 arcsec.


**2.** **Observations and data reduction**


_2.1._ _NIRSpec and MIRI imaging spectroscopy_


3C 326 N was observed with the integral-field units (IFUs) of
the Near-Infrared Spectrograph (NIRSpec) and the MediumResolution Spectrograph (MRS) of the Mid-Infrared Instrument
(MIRI) on the James-Webb Space Telescope as part of program GO1-2162 (PI Nesvadba). NIRSpec data were obtained on
4 March 2023 through the filter F170LP and with the grating
G235H. They cover a near-continuous spectral range between
1.66 µm and 3.17 µm with a gap between 2.40 µm and 2.56 µm
due to the physical gap between the two NIRSpec detectors in
the focal plane of the telescope. The field-of-view of the NIRSpec IFU is 3.0 [′′] ×3.0 [′′], and the dispersion through the G235H
grating is ∆λ = 8.7 × 10 [−][4] µm, which corresponds to a spectral
resolution of 85 − 150 km s [−][1] .

Data were obtained during one visit with 2976 seconds of onsource observing time at four dither positions, using the dither
pattern NRSIRS2RAPID with 50 single-integration groups. We
also obtained a background exposure with the same readout pattern, 10 single-integration groups, one dither position, and a total
exposure time of 160 seconds.

MIRI data were obtained on 28 March 2023 with the four
channels of the LONG setting. Channels 1 to 4 cover spectral
ranges between 6.53 µm and 7.65 µm, 10.02 µm and 11.7 µm,
15.41 µm and 17.98 µm and 24.19 µm and 27.9 µm, respectively.
The spectral resolving power is R=1330-3610, corresponding to
a spectral resolution between 83 and 226 km s [−][1] . The field-ofview of the MIRI IFU is between 3.2 [′′] ×3.7 [′′] in Channel 1 and

6.6 [′′] ×7.7 [′′] in Channel 4.

We used the MRSLONG and MRSSHORT detectors with
the LONG(C) grating, FASTR1 readout pattern, 35 singleintegration groups, and four dither positions that were optimised
for extended sources. The on-source exposure time was 389 seconds per detector. A second visit was used to observe a background frame with the same setup directly following the onsource observations.

Both the NIRSpec and MIRI data were reduced with version 1.12.4 of the official pipeline python package: jwst. We
used the CRDS context collection jwst_1146 for static calibration file association. Both the datasets required no additional data
cleaning beyond what the pipeline performed. In summary, the
raw files were processed with Detector1Pipeline to correct for
detector level effects. The resulting ramp files were passed to
the Spec2Pipeline which performs the WCS correction, flat field
correction, background correction, and flux calibration. Furthermore, the pipeline applies an MSA imprint and pathloss correction for the NIRSpec data as well as a fringe correction for the
MIRI MRS data. We experimentally applied the fringe correction to the NIRSpec data as well but found no improvement. Finally, the data for NIRSpec and MIRI were resampled and combined with the Spec3Pipeline. We used the drizzle combination
method to combine and rotate the NIRSpec data and each MIRI
channel separately. This pipeline also performed outlier detection and a master background subtraction for the MIRI MRS
data.



_2.2._ _ALMA interferometry_


We also obtained archival ALMA data in band 3 from program 2015.1.01120.S, which cover the expected wavelength of
12 CO(1–0) at z=0.0898, 105.8 GHz. Continuum emission from
the nucleus is well detected, with a flux density at 115.3 GHz
in the rest-frame of _S_ 115 _GHz_ = 1.6 ± 0.01 mJy bm [−][1] . CO(1–
0) line emission is not detected. We use this data set to derive
an upper limit on the line flux, which has _RMS_ = 0.2 mJy
bm [−][1] in 15.4 MHz wide spectral channels, for a beam size of
FWHM=0.46 [′′] ×0.26 [′′] along the major and minor axis, respectively, and position angle PA=-13.5 [◦], measured from North towards East.

We follow the prescription of Sage et al. (2007) and Young
et al. (2011) by setting σ [2] _line_ [= ∆] _[v]_ [2] [σ] [2] _[ N]_ _[l]_ [ (1][.] [+] _[N]_ _[l]_ [/] _[N]_ _[b]_ [), where][ σ] _[line]_
is the line-integrated standard deviation of the data set, ∆ _v_ the
line width in km s [−][1], _N_ _l_ the sampling of the line, and _N_ _b_ = 118 is
the number of spectral channels from which σ was estimated.
Assuming a line width of FWHM=100 km s [−][1], a sampling of
43.26 km s [−][1] as in our data, and _RMS_ = 0.2 mJy bm [−][1], we find
σ _line_ = 30.7 mJy km s [−][1] bm [−][1] . Using Equation 3 of Solomon
et al. (1997), we can translate this flux into a line luminosity,
by setting _L_ _CO_ [′] [=] [3][.][25] [×] [10] [7] _[S]_ _[ CO]_ [∆] _[V]_ [ν] _obs_ [−][2] _[D]_ [2] _L_ [(1] [+] _[z]_ [)] [−][3] [,] [where]
_S_ _CO_ ∆ _V_ is the integrated line flux in Jy km s [−][1], ν _obs_ the observed
frequency in GHz, _D_ _L_ the luminosity distance in Mpc, and _z_ the
redshift. To estimate a molecular gas mass from the luminosity,
we adopt the standard conversion factor appropriate for, e.g., the
Milky Way, α _CO_ = 4.3 _M_ ⊙ / [K km s [−][1] pc [2] ] (e.g., Bolatto et al.
2013), and find a 3σ upper limit of 1.5 × 10 [8] _M_ ⊙ bm [−][1] . Assuming that CO line emission would extend over the same area also
seen with NIRSpec in warm molecular gas, we expect that the
total molecular gas mass would be a factor 5.3 larger, i.e., correspond to a total of _M_ _H_ 2, _CO_ = 8 × 10 [8] M ⊙ . This is about a factor 3
less than the _M_ _H_ 2 = 2 × 10 [9] _M_ ⊙ of warm molecular gas previously found with Spitzer (Ogle et al. 2007), and suggests that the
majority of the molecular gas in 3C 326 N is indeed warm.

Nesvadba et al. (2010) previously reported weak CO(1–0)
line emission detected at 5σ with the IRAM Plateau de Bure
interferometer in the D configuration at 5 [′′] beam size. Given
the new, deeper observations available now from ALMA with
a much larger bandwidth, we consider this previous detection
spurious. Although the spectrum was carefully extracted from
the data cube, the large beam size and narrow band width made
it very challenging to isolate the continuum from the line emission, which can explain the faint putative line detection that was
made with the best instrument available at that time.


_2.3._ _JVLA interferometry_


We also obtained deep radio continuum imaging with the Karl G.
Jansky Very Large Array (JVLA) in the A-array in the L, C, and
X-bands at 1.52, 7.25, and 9.0 GHz through program 18A−285
(PI Nesvadba). We observed the source in four sessions between
2 March 2018 and 9 June 2018 with 24 to 27 antennae and a total
allocation of 6.4 hrs. Our main goal was to probe the morphology of the radio core of 3C 326 N, and to search for extended
emission on scales comparable to the 3 [′′] size of the molecular disk. We used 3C 286 as flux and bandpass calibrator, and
J1609+2641 as gain calibrator. In the L-band, we centred the two
basebands on 1.264 and 1.776 GHz to obtain 1 GHz of nominal
band width. In the C and X-bands, we tuned each baseband to
5.5 and 6.5 GHz, and to 9.5 and 10.5 GHz, respectively, reaching 2 GHz of nominal band width.


Article number, page 3 of 22

_A&A proofs:_ manuscript no. aanda



Data were reduced in the standard way using casa Version
5.4.2-5. First, data were flagged, antennae positions corrected,
and an initial flux density scaling was derived from our primary
calibrator 3C 286 in each band. We then did an initial phase calibration for all bands before solving for antennae-based delays
and performing the bandpass calibration in each band, again,
using 3C 286. Complex gains were derived from J1609+2641
before we used the flux of our primary calibrator to derive the
amplitude gains of J1609+2641 and 3C 326 N in each band.
We eventually applied the calibration before reconstructing and
cleaning the images, using briggs=0.5. The final RMS obtained
in this way is about 5 mJy bm [−][1] in the C and X-bands, and
90 mJy bm [−][1] in the L-band, which is strongly affected by RFI.
Beam sizes are around 0.2 [′′] -0.3 [′′] in the C and X-bands, and 1.1 [′′]
in L. The central tuning, beam size and position angle, and RMS
in each band can be found in Tab. 1.


_2.4._ _Relative alignment_


The JWST/NIRSpec and each channel of the MIRI observations
show a small spatial offset with each other and with the ancillary data sets, mainly along right ascension. Relative to the
NIRSpec data, MIRI data are offset in RA by -0.7 [′′], 0.58 [′′], and
0.32 [′′] in channel 1, channel 2, and channel 3, respectively. The
offsets in Dec are subpixel in MIRI and we do not list the offset
for channel 4 due to an extremely tentative continuum detection. The positional offsets are significantly larger than the given
0.1 [′′] pointing accuracy of JWST [1] . We therefore did not simply
use the position on the sky as indicated in the file headers, but
used the stellar continuum peak in the NIRSpec data cube to
align the JWST data relative to the radio data. In aligning the
data sets we made the simple astrophysical assumption that the
radio core falls on top of the peak in the stellar continuum emission, which is also the location of the highest Paα, [FeII]λ1.599
an [FeII]λ1.6440 surface brightness, highlighting the presence
of a faint AGN at that position.


**3.** **Emission line and stellar continuum fitting**


To model the spectral features of the JWST data, we used a
Markov Chain Monte Carlo (MCMC) based fitting method. The
sampling was performed with the python package emcee (Goodman & Weare 2010) and the data file handling was performed by
astropy(Astropy Collaboration et al. 2013).


_3.1._ _Emission Lines_


Unless otherwise stated, the line modelling was performed on
one line at a time, to be able to probe differences in line kinematics or morphology, if present. When modelling a line, we cut
the cube in the spectral direction such that the modelled wavelength range is λ 0 (1 ± 0.01)(1 + _z_ in ) where λ 0 is the lines rest
frame wavelength and _z_ in is our initial redshift guess set to 0.09
based on the measurement of Nesvadba et al. (2011) and visual
inspection of the NIRSpec lines in the central 0.5" of the galaxy.
We reproduced the emission line features using a Gaussian
line profile coupled with a linear continuum in frequency. We
find that the line shape is often complex and requires multiple


1 `[https://jwst-docs.stsci.edu/](https://jwst-docs.stsci.edu/jwst-observatory-characteristics/jwst-pointing-performance)`
```
jwst-observatory-characteristics/
jwst-pointing-performance

```

Article number, page 4 of 22



Gaussians to explain. Therefore, the line profile can be as:



2 []

, (1)
� 



_F_ ν (ν) = _m_ ν + _b_ +



_N_
�(1 + _z_ _n_ ) _A_ _n_ exp

_n_ =1



−0.5 (1 + _z_ _n_ )ν − ν 0
 � σ _n_



where _A_ _n_ is the amplitude of Gaussian _n_, ν is the frequency, ν 0
is the line rest frame frequency, _z_ _n_ is the redshift of Gaussian _n_,
σ _n_ is the standard deviation of line _n_, _m_ is the continuum line
gradient, and _b_ is the continuum intercept. Note that _m_ and _b_ are
not adjusted for redshift when modelled. We allow up to 2 Gaussians and select the number used by the Bayesian Information
Criterion (BIC).
When modelling, we measure the goodness of fit from a parameter set using the maximum likelihood + prior probability
distribution. Our maximum likelihood is defined as



2 ln ( _L_ ) = − � _F_ ν, _ob_ (ν) − _F_ ν (ν, α)� 2 + ln (2πδ), (2)
� []  δ 

δ = _err_ [2] + _f_ [2] _F_ ν (ν, α) [2] (3)


where _err_ is the data uncertainty, _f_ is the fraction by which the
uncertainty is underestimated, and _F_ ν, _ob_ is the observed flux. We
define the prior probability function for all parameters to be uniform between the boundaries and − inf otherwise. We select nonrestrictive boundaries of -5–5, -1–1 Jy, 0–10 mJy, 0.1–300 GHz,
0.088–0.0915 for _m_, _b_, _A_ _n_, σ _n_, and _z_ _n_, respectively For _z_ we define an additional prior probability _P_ _z_ . _P_ _z_ is a normal distribution
such that



2 []


, (4)

� 



_P_ _z_ =



_N_
�

_n_ =1



1
 σ _z_ ~~√~~



exp
2π



−0.5 _z_ _n_ − < _z_  � σ _z_



where < _z_ - is the mean _z_ for all _N_ Gaussians in the model and
the standard deviation of _z_ separation probability σ _z_ = 0.001. We
base this probability distribution on the fact that the separation
between Gaussians for one line can differ but greater separations
are less likely to be part of the same line instead of two unrelated
features. We choose the σ _z_ to be 0.001 to place a 95% chance that
a line emitting source is not separated from the average velocity
of emitting structures in one spaxel by more than ∼550 km s [−][1]
which is similar to the maximum velocity offset between components for _any_ single line in 3C 326 N from Nesvadba et al.
(2011). We find this significantly improves multi-line fits without being overly constraining on the velocity separation of coincidental projected structures. We also set the rule that _z_ _n_ < _z_ _n_ +1
to prevent the degenerate solution of components switching parameters. These additional rules for _z_ have no effect in the one
component case.
All Gaussian components are then modelled simultaneously
for the line and each spaxel is modelled independently. We use
a uniform initial distribution between the boundaries of 0–1 mJy
and 1–100 GHz for the amplitude and standard deviation, respectively, and a normal distribution around 0.09 ± 0.001 for z. We
use 5000 steps and 200 walkers. We then perform a second run
starting from the best fit parameters by likelihood of the first run
with a normal distribution with a 0.1% standard deviation for
the initial positions. The second run also uses 5000 steps and
200 walkers. An example result for a 2 Gaussian fit to the H 2 1–0
S(3) line for different regions of the galaxy can be seen in Fig. 1.
When reporting Gaussian line component amplitudes and
widths, we account for the instrumental line spread function.
These vary slightly between NIRSpec and the different MIRI
channels. The resolution for NIRSpec IFU and MIRI MRS long

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


Band central frequency beam size PA RMS size flux

[GHz] [arcsec] [deg] [µJy bm [−][1] ] [arcsec] [mJy bm [−][1] ]
L 1.52 1.18 × 1.11 −41.8 90 1.08 × 1.01 2.10±0.09

C 7.25 0.29 × 0.26 65.5 4.7 0.29 × 0.24 1.00±0.005

X 9.00 0.22 × 0.20 −32.8 5.3 0.21 × 0.20 1.15±0.005

**Table** **1.** Observational parameters and results of our JVLA observations. Position angle PA is measured from North through East. The most
accurate position of the radio core measured in the X-band is RA=15:52:09.112, Dec=20:05:48.2.



channel 1, 2, 3, and 4 is 2700, 3100—3610, 2860-–3300, 1980—
2790, and 1630—1330, respectively [2] .


_3.2._ _CO band head absorption_


To model the CO band head absorption features, we used a template provided by Winge et al. (2009) instead of a Gaussian line
profile. The templates are of single stars; to adjust for a stellar population we assume the distribution of velocities is normal. We convolve the template spectrum with a Gaussian with
a standard deviation of the stellar velocity dispersion, σ SVD,
and resample it to the spectral resolution of the NIRSpec spectrum using the python package spectres (Carnall 2017). We then
multiply the spectrum by a 2 [nd] order polynomial continuum to
correct for the normalisation applied by Winge et al. (2009).
We compare the adjusted template to the data between the observed wavelengths of 2.485 µm and 2.62 µm which contains
only CO band head features and no emission features (Fig. 2).
Similarly to the emission lines, the instrumental line spread function (R=2700) is accounted for in the given velocity dispersions.
To find the best template to reproduce our data, we compare
every template to the highest signal-to-noise spaxel in the NIRSpec dataset. We find that the template star of HD 9138, a K4III
star, is a very good reproduction of our data without additional
spectral types. We proceed to fit only the HD 9138 template to
every spaxel. We generate an initial position for the walkers using a normal distribution around the best fit parameters of the
highest signal-to-noise spaxel fit with a standard deviation of
1%. We use 2000 steps and 100 walkers when performing the
fitting.
An example of the model fitting can be seen for four selected
spaxels in Fig. 2. It can be seen that the one template can reproduce our observed data very well.


**4.** **Analysis**


_4.1._ _Properties of the radio core_


The GHz radio morphology of 3C 326 N is compact on scales
of few arcsec in all three bands that we observed. As an example, the 10 GHz radio morphology is shown as circumnuclear
contours in Fig. 3. Radio synchrotron emission follows a simple
power law, where the flux, _f_, is set by the frequency, ν, and a
spectral index, α, as _f_ ∝ ν [−][α] . With the values for the radio flux
and central frequencies given in Tab. 2.3, we find a α = 0.21
between 1.52 GHz and 10.0 GHz, a typical value for the flatspectrum radio core of a radio AGN. Although we obtained fairly


2 values from `[https://jwst-docs.stsci.](https://jwst-docs.stsci.edu/jwst-near-infrared-spectrograph/nirspec-observing-modes/nirspec-ifu-spectroscopy)`
```
edu/jwst-near-infrared-spectrograph/
nirspec-observing-modes/nirspec-ifu-spectroscopy
```

and `[https://jwst-docs.stsci.edu/](https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-observing-modes/miri-medium-resolution-spectroscopy)`
```
jwst-mid-infrared-instrument/miri-observing-modes/
```

`[miri-medium-resolution-spectroscopy](https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-observing-modes/miri-medium-resolution-spectroscopy)` for NIRSpec IFU and
MIRI MRS, respectively



deep data, with RMS=90 µJy at 1.52 GHz, and RMS∼5µJy at
7.5 and 10 GHz, we did not detect diffuse emission around the
nucleus in any band.
To investigate whether we may have missed a diffuse component, we compare the flux measured at 1.52 GHz, _S_ 1.52 =
2.10 ± 0.09 mJy, with that of FIRST (Becker et al. 1995; White
et al. 1997), _S_ 1.4 = 3.94 ± 0.14 mJy, finding that 47% of the
flux measured with FIRST at 5.4 [′′] beam size are missing in our
data obtained with a 1.2 [′′] beam. Assuming that such emission
would be of uniform surface brightness and beam-filling in the
FIRST data, we find that we would need to probe down to a surface brightness of 95 µJy in the L-band, which corresponds to
our RMS, so that it is well possible that faint, diffuse emission
is present but not detected. In the higher frequency bands, due
to the much smaller beam size, and likely steep spectral index,
such an extended component would also have been missed. The
5.4 [′′] beam of FIRST is slightly larger than the molecular disk in
3C 326 N.

A similar situation was encountered by Zovaro et al. (2019),
who identified ro-vibrational line emission from molecular
Hydrogen in the z=0.06 radio galaxy 4C31.04 using GEMINI/NIFS, which extended over much larger radii than the radio
source. Their detailed comparison with the relativistic hydrodynamic simulations of Mukherjee et al. (2018) showed a significant component of diffuse radio emission which extends well
beyond the brightest regions, but would require a dynamic range
much greater than the factor 100 or so possible with current radio
facilities to be probed. The same arguments apply to our present

case.


_4.2._ _Emission line and CO band head detections_


We show the source-integrated spectrum obtained with NIRSpec in Fig. 4 and channel 1 of MIRI MRS in Fig. 5. As has
already been pointed out by Nesvadba et al. (2011), the spectrum is strongly dominated by the ro-vibrational emission lines
of molecular Hydrogen. In NIRSpec we cover the 1–0 S and the
1–0 Q series from S(0) to S(7) and Q(1) to Q(9). In NIRSpec,
we also identify the 1–0 O(2) and O(3) lines, and potentially
the 2–1 S(3) and Q(3) lines. With MIRI we detect the rotational
lines, H 2 0–0 S(3), S(5), and S(6), previously observed by Ogle
et al. (2007), as well as [ArII]λ6.985 and [NeIII]λ15.56. Ogle
et al. (2007) detected additional forbidden lines of [FeII]λ5.34,

[SIV]λ10.51, [NeII]λ12.81, [SIII]λ18.71, and [OIV]λ25.89, that
are not covered by our data, but to our knowledge, these are the
first detections of [ArII]λ6.985 and [NeIII]λ15.56. Other lines of
the 0–0 S series are not covered by our setup.
Moreover, with NIRSpec we identify the warm ionised gas
line Paα as well as the iron line [FeII]λ1.644. [FeII]λ1.599 is
tentatively detected but falls within the strong CO 5–2 band head
absorption feature. Brγ is covered, but not detected, probably because the interstellar line emission is filling in the stellar Brγ ab
∼
sorption line. At R 2700, the spectral resolving power of NIRSpec does not allow us to robustly isolate these two components.


Article number, page 5 of 22

_A&A proofs:_ manuscript no. aanda













1e 20



2.0


1.5


1.0









20°05'49.0"


48.5"


48.0"


47.5"

















0.5


0.0





15 [h] 52 [m] 09.20 [s] 09.10 [s]


RA

















1000 0 1000



1000 0 1000



1000 0 1000



Velocity (km s 1 )


**Fig. 1.** Centre: Integrated model flux for H 2 1–0 S(3). Outside: Gaussian model fit to the H 2 1–0 S(3) line for different spaxels of the central image.
The coloured squares in the image represent the position of the plotted spaxel of the same colour. Dashed lines are individual Gaussian components
and the solid line is the summed Gaussians. Shaded regions are 1 σ errors. These spectra area also a good illustration of the high quality of the
date and the automatic fitting routine.


Label F blue F red F Total _A_ blue _A_ red σ blue σ blue _Vel_ blue _Vel_ red

[10 [−][20] W m [−][2] ] [10 [−][20] W m [−][2] ] [10 [−][20] W m [−][2] ] [µJy] [µJy] [km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [km s [−][1] ]
A 0.32 [0][.][022] 0.253 [0][.][023] 0.573 [0][.][013] 2.42 [0][.][12] 2.09 [0][.][1] 112.0 [8][.][9] 103.0 [9][.][1] −15.6 [8][.][4] 283.0 [9][.][7]
0.024 0.022 0.013 0.12 0.1 11.0 9.7 8.9 10.0
B 0.553 [0][.][067] 1.01 [0][.][065] 1.56 [0][.][019] 2.45 [0][.][2] 8.39 [0][.][33] 192.0 [14][.][0] 102.0 [3][.][9] 133.0 [24][.][0] 356.0 [3][.][3]
0.068 0.066 0.02 0.22 0.37 12.0 3.6 23.0 3.3
C 0.343 [0][.][08] 0.813 [0][.][094] 1.15 [0][.][023] 0.948 [0][.][23] 4.11 [0][.][29] 302.0 [32][.][0] 168.0 [10][.][0] 2.71 [74][.][0] 276.0 [8][.][9]
0.089 0.078 0.023 0.31 0.23 34.0 8.8 58.0 10.0
D 0.182 [0][.][047] 0.713 [0][.][049] 0.894 [0][.][018] 0.586 [0][.][12] 5.15 [0][.][19] 258.0 [36][.][0] 118.0 [5][.][3] −83.3 [75][.][0] 156.0 [3][.][6]
0.049 0.045 0.018 0.18 0.18 32.0 4.5 63.0 3.4
E 0.425 [0][.][062] 0.253 [0][.][045] 0.683 [0][.][04] 0.878 [0][.][094] 1.52 [0][.][18] 412.0 [49][.][0] 143.0 [21][.][0] −150.0 [70][.][0] 320.0 [16][.][0]
0.068 0.055 0.041 0.091 0.17 54.0 22.0 60.0 16.0
F 0.355 [0][.][11] 1.09 [0][.][13] 1.43 [0][.][028] 1.0 [0][.][32] 7.0 [0][.][45] 286.0 [45][.][0] 132.0 [7][.][6] −150.0 [88][.][0] −54.0 [4][.][0]
0.12 0.1 0.031 0.49 0.38 46.0 7.1 39.0 4.3
G 0.457 [0][.][09] 0.333 [0][.][075] 0.79 [0][.][017] 1.55 [0][.][39] 2.56 [0][.][36] 250.0 [18][.][0] 112.0 [15][.][0] −131.0 [26][.][0] −75.6 [6][.][7]
0.077 0.092 0.018 0.35 0.32 21.0 16.0 18.0 7.2
H 0.205 [0][.][075] 1.1 [0][.][14] 1.31 [0][.][045] 0.782 [0][.][19] 5.86 [0][.][45] 242.0 [80][.][0] 158.0 [10][.][0] −315.0 [110][.][0] 65.1 [7][.][7]
0.14 0.078 0.046 0.27 0.27 68.0 8.7 160.0 8.4

**Table 2.** The parameters of the Gaussians shown in Fig. 1 with a reference to the fitted spaxel in the figure.



In addition to these emission lines originating from interstellar gas, we also detect the ∆ _v_ = 2 and ∆ _v_ = 3 stellar absorptionline series of [12] C [16] O, i.e., eight lines between _v_ = 2 − 0 and
_v_ = 9 − 7 at 2.29 to 2.51 µm, and six absorption lines between
_v_ = 3 − 0 to _v_ = 8 − 5 at 1.56 to 1.66 µm. We subsequently
use the absorption lines between 2.3 µm and 2.4 µm to determine
the systemic redshift and search for evidence of rotation of the


Article number, page 6 of 22



stellar component. We do not use the redward lines due to contamination from the H 2 1–0 Q series of emission lines and our
templates do not cover the bluer absorption lines.


While a thorough analysis of all detected emission lines is
beyond the scope of this paper, we provide the source integrated fluxes from our spatially resolved 1–2 Gaussian component model fitting described Sect. 3 in Tab. 4. In Tab. 3, we state

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


200


150











1000


900


800


700


600


500


400





100


50


0


50


100


150


200







15 [h] 52 [m] 09.20 [s] 09.10 [s] 09.05 [s]


RA



15 [h] 52 [m] 09.20 [s] 09.10 [s] 09.05 [s]


RA





4.0


3.5


3.0


2.5


2.0





2


1


0


4


3


2





2.28 2.30 2.32 2.34 2.36 2.38 2.40



22.5


20.0


17.5


2.28 2.30 2.32 2.34 2.36 2.38 2.40



Wavelength ( m)


**Fig. 2.** Top left: The CO band head velocity map from our template fit. For clarity, while we model all spaxels, here we only plot the velocities for
spaxels with a average SNR > 10. Top right: The FWHM of the velocity dispersion for the CO features, the spaxels with an average SNR < 10
are omitted. Overplotted as coloured squares are the positions of the four spaxels displayed beneath. The spaxel positions and labels match Fig. 1.
Overplotted on both top plots in purple are contours of the near-IR continuum emission in Fig. 6. Bottom: The model fit to the CO features in four
selected spaxels. The filled regions are the 1 σ uncertainties.



5 σ upper limits to Brγ and the 6.2 µm PAH feature which were
covered by our data but not detected. As a courtesy to the reader
we also perform single Gaussian fits to the source integrated
spectrum and provide the source-integrated redshift and FWHM
line widths of all emission lines except H 2 1–0 Q(2) and H 2 1–0
Q(8) in Tab. 5. The lines are more complex than a single Gaussian and, therefore, the given values are only to give the reader
an estimate of the integrated line properties. For fluxes, we recommend only those from Tab. 4 be used. The 2 omitted Q series
lines become blurred with other spectral features in the source
integrated spectrum. However, they are distinct in the spatially
resolved spectrum.


_4.3._ _Continuum morphology and stellar absorption bands_


3C 326 N has a well extended continuum morphology clearly
observable in the near-IR. We plot the continuum morphology at
1.8 µm in Fig. 6. The extended emission is elliptical with a major
axis position angle of ∼ 155 [◦] .
Since NIRSpec covers the ∆ _v_ = 2 and ∆ _v_ = 3 series of
CO band heads, we can use these absorption features to derive
the systemic redshift and stellar velocity dispersion. Stellar ab


sorption lines are the most robust tracers of the systemic redshift, because the stellar component dominates the mass budget
within the central few kpc of early-type galaxies (3 × 10 [11] M ⊙ in
3C 326 N compared to 2 × 10 [9] M ⊙ in molecular gas Nesvadba
et al. 2010), and because it is not affected by hydrodynamic processes like AGN or starburst-driven winds, which may significantly impact the gas kinematics. This is a particular worry in
case of radio galaxies like 3C 326 N.


When we model the CO band heads, we find no evidence of
a velocity gradient across the galaxy (see Fig. 2). This suggests
that the galaxy stellar population is not rotationally dominated.
Thus, 3C 326 N resembles a classical "slow rotator" as is typical for a massive galaxy of few 10 [11] _M_ ⊙ of stellar mass (e.g.
Emsellem et al. 2011). We also find no significant change in the
FWHM of the model stellar velocity distribution (SVD) with radius. Therefore, we can find the systemic redshift by merging
all posterior probability distributions of each spaxel fit. To reduce uncertainty, we merge the parameter probability distributions for all spaxels with an average wavelength bin SNR > 10
in the modelled data to find the systemic redshift and its uncertainty.


Article number, page 7 of 22

_A&A proofs:_ manuscript no. aanda


**Fig. 3.** H 2 1–0 S(3) emission-line morphology _(top)_, velocities _(centre)_ and FWHM line widths _(bottom)_ with the JVLA 8.4 GHz radio continuum
shown as thick contours near the centre. Thin contours show the emission-line morphology in the top left panel to ease orientation. _(left_ _to_
_right):_ Single-component fit, systemic line component and blueshifted line component. The emission-line morphology and single-component and
systemic velocity maps show an hourglass gas morphology with a strongly blue and redshifted bipolar velocity field, consistent with a pair of
bubbles that are being inflated by the radio source at the centre. The yellow ellipse and blue circle in this and subsequent figures indicate the beam
size of the JVLA and the PSF of the JWST data set.



We find a systemic redshift of _z_ _syst_ = 0.08979 ± 0.0003, consistent with the value of _z_ = 0.09 from Guillard et al. (2015)
measured from [CII]. Ogle et al. (2007) previously measured
_z_ = 0.089 ± 0.001 with Spitzer from the pure-rotational lines of
warm H 2 . Nesvadba et al. (2011) found _z_ = 0.0903±0.0002 from
ro-vibrational lines and Paα measured with VLT/SINFONI. We
use our value as the systemic redshift for all other velocity plots.
From our CO modelling, we also find that the FWHM of the CO
band head velocity dispersion is 5.1 ± 0.8 nm, equivalent to a
velocity of 660 ± 100 km s [−][1] .


_4.4._ _Emission-line morphology and kinematics_


4.4.1. Ro-vibrational line emission of H 2


We will start our discussion of the emission-line morphology
and kinematics with the properties of the ro-vibrational H 2 1–0
lines observed with NIRSpec, using the S(3) line as reference
for this set of lines. S(3) is amongst the brightest lines we detected, not noticeably contaminated by other nearby lines, and
in the blue part of the spectral range covered by our data, thus
maximising spatial resolution. H 2 1–0 S(3) can be contaminated


Article number, page 8 of 22



by [SiVI]λ1.962; however, we note that we find similar modelling results in all high bright H 2 lines, including in MIRI, and
that we find no obvious contamination in this line. Fig. 11 shows
comparisons between different H 2 lines and shows no significant variations in line profile for H 2 1–0 S(3). Other H 2 1–0 lines
also show the same spatial distribution and kinematics within the
measurement uncertainties.


We find that the molecular hydrogen lines show a clear
North-South morphology shown in Fig. 3 roughly centred on the
galaxy nucleus as indicated by the peak in surface brightness of
the stellar continuum emission. Bright line emission is probed
over 2.0 [′′] in North-South direction, and over 0.5 [′′] and 1.2 [′′], in
East-West direction in the Southern and Northern part of the
source, respectively. North of the nucleus we find a cavity-like
structure delineated by several bright, unresolved knots of line
emission at the far (Northern) end. This cavity and the structure
of the components themselves are not mirrored in the continuum supporting the idea that it is not caused by stellar emission.
South of the nucleus, the emission-line morphology is more regular and featureless, and extends to about 0.8 [′′] South from the
nucleus.

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


1.8


1.6


1.4


1.2


1.0

|Q(3) 2-1 H2 Q(9) 1-0 H2 Q(8) 1-0 H2 CO 9-7 Q(7) 1-0 H2 CO 8-6 Q(6) 1-0 H2 (((( )))) 0000 QQQQ HHHH 1111 1345 2222 ---- CC OO 67 45 -- Q(2) 1-0 H2 CO 5-3 CO 4-2 CO 3-1 CO 2-0 S(0) 1-0 H2 Br S(1) 1-0 H2 S(3) 2-1 H2 S(2) 1-0 H2 S(3) 1-0 H2 S(4) 1-0 H2 Pa|Col2|
|---|---|
|2.0<br>2.2<br>Waveleng|2.4<br>2.<br>th ( m)|



**Fig.** **4.** The source-integrated spectrum of 3C 326 N from the NIRSpec observation from 1.5 to 2.9µm showing most of the lines. The flux was
extracted with an elliptical aperture centred on the peak continuum flux with a major axis along Dec of 1.1" and a minor axis of 0.9". Empty
pixels were not included and the pixels within the aperture were sigma clipped with a tolerance of 5 σ. The spectral gap at 2.2 µm is caused by the
NIRSpec IFU detector gap.



We fit Gaussian line profiles to the line emission in all
spaxels as detailed in Sect. 3. Examining the line profiles
(e.g., Fig. 1), we find that fits with two Gaussians are preferred
in almost all regions of the galaxy over single-Gaussian fits. The
exception to this is the lowest surface-brightness regions where
the signal-to-noise is not sufficient to fit two lines components.
Some areas close to the nucleus can also be explained by a single component where the systemic redder component becomes
dominant. For simplicity, we focus most of our discussion on the
two-component modelling. In this discussion, we distinguish the
two components as a redder (higher z) systemic (or "primary")
component and a bluer (lower z, or "secondary"), often broader,
component. The line profiles, quality of the spectra and Gaussian
fits can be seen in Fig. 1.


Generally speaking, the gas velocities in both Gaussian components show a monotonous gradient from blueshifted in the
South towards more redshifted in the North (Fig. 3). The systemic Southern component shows redshifted velocities along its
Western edge. As can be seen from the left panel of Fig. 3, the
same trend can be seen in the single-component fit, although the
gradient is smaller and less pronounced, because of the lower
quality of the fit stemming from fitting a double-peaked profile
with a single Gaussian.


The secondary component, which is always blueshifted relative to the first, shows the same trend between blueshifted gas
South, and redshifted gas North, but is blueshifted by a value
of 100-200 km s [−][1] relative to the first component. Typical line
FWHM are ∼ 400 − 1000 km s [−][1] for the bluer component and
∼ 200 − 400 km s [−][1] for the redder. Other H 2 1–0 lines have similar morphologies and kinematics within the measurement uncertainties.



4.4.2. Rotational line emission of H 2


The pure rotational lines of H 2 were observed with MIRI at about
3 − 4× less spatial resolution than the ro-vibrational lines with
NIRSpec, i.e., with a PSF of 0.3-0.42 [′′] . We will also discuss
these lines on the example of the H 2 0 − 0 S(3) line, which is
at a rest-frame wavelength of λ = 9.66 µm. These lines are interesting to study in parallel to the H 2 1–0 lines, because they probe
the dominant molecular gas component in this galaxy (Sect. 4.5).


The integrated emission-line morphology is shown in Fig. 7.
H 2 0−0 S(3) line emission is also clearly elongated along NorthSouth direction with a projected size of 2.0 [′′] . In the Northern
and Southern part of the source, the East-West extent is 1.0 [′′],
and 0.5 [′′], respectively. Most of the line emission is originating
from the blob South of the nucleus and a bright emission-line
region North of it. There is a region of much fainter line emission between the nucleus and the Northern emission-line region,
which corresponds to the cavity already seen in H 2 1–0 S(3).
Overall, the morphology and gas kinematics follow closely those
already seen in the H 2 1–0 S(3) line, although the blending due
to the lower spatial resolution of the data tend to lower the velocity offsets, enhance the line widths, and generally, smooth out
small-scale features. We will do a more quantitative comparison
between the two lines, including the line kinematics, in Sect. 6,
that takes into account the effect of the different beam sizes. We
do not observe significant differences between the morphology
of the H 2 0–0 S(3) line described here, and the 0–0 S(5) and S(6)
lines, which we also covered.


Article number, page 9 of 22

_A&A proofs:_ manuscript no. aanda


7


6


5


4


3


2


1


0


**Fig.** **5.** The integrated source spectra from the MIRI MRS Channel 1 observation. The flux was extracted with an elliptical aperture centred on
the peak continuum flux with a major axis along Dec of 1.1" and a minor axis of 0.9". Empty pixels were not included and the pixels within the
aperture were sigma clipped with a tolerance of 5 σ.



20°05'50"


49"


48"


47"


46"


15 [h] 52 [m] 09.3 [s] 09.2 [s] 09.1 [s] 09.0 [s]


RA


**Fig. 6.** The 1.8 µm continuum with contours overplotted.


4.4.3. Warm ionised gas lines



10 2


10 3


10 4



NIRSpec and MIRI have also observed several warm ionised
gas lines. We discuss here the lines of Paα, [FeII]λ1.644, and

[NeIII]λ15.56. While it has already been shown conclusively
by Ogle et al. (2007), Nesvadba et al. (2010), and Nesvadba
et al. (2011) that the emission lines of warm H 2 are mainly
heated by shocks driven by the radio source into the gas, the
ionisation mechanism of the other lines is not clear. Paα can
be either heated by shocks, AGN photoionisation or UV photons from young stellar populations (for a review, see, e.g. Kewley et al. 2019), [FeII]λ1.644 can be either heated by shocks or
AGN photoionisation (e.g. Rodríguez-Ardila et al. 2004)], and


Article number, page 10 of 22




[NeIII]λ15.56, which has a high ionisation potential of _E_ _ion_ =
40.96 eV (Levesque & Richardson 2014), either by AGN photoionisation, or, in extreme cases, star formation (Ho & Keto
2007). Spoon & Holt (2009) and Spoon et al. (2009) found that

[NeIII]λ15.56 line emission likely traces circumnuclear gas in
nearby ULIRGs that is strongly perturbed through interactions
with the AGN.

We can use the Paα and [FeII]λ1.644 morphology to conclude that both lines are most likely heated by shocks. Their
morphology follows very closely that of the H 2 1–0 and H 2 0–
0 lines. A contribution from AGN photoionisation near the nucleus, where Paα and [FeII]λ1.644 are brighter than the H 2 1–0
S(3) line, is possible. They follow the North and South components seen in H 2 1–0 S(3), but the North component is comparatively fainter relative to the South and the North component is
brighter on the western side. This can be seen in the single component fits or the systemic component of the 2 Gaussian fit in
Figs. 3,7, 8, and 10; we will discuss this further in Sect. 5.
The [NeIII]λ15.56 emission, as shown in Fig. 9, does extend
North-South but it does not show the same Northern bright spot,
and its morphology is more symmetric around the nucleus than,
e.g., H 2 0–0 S(3), which shows a depression between the nucleus and the Northern clumps co-spatial with the cavity already
identified in the H 2 1–0 S(3) line.


_4.5._ _Mass budgets_


3C 326 N has already several detailed mass estimates of different phases of warm and cold gas. Ogle et al. (2007) and Nesvadba et al. (2010) estimated a mass of warm H 2 from the pure
rotational line emission finding M _H_ 2, _rot_ = 1.1 × 10 [9] _M_ ⊙ and
M _H_ 2, _rot_ = 1.3 − 2.7 × 10 [9] _M_ ⊙, respectively. We will in the following use the latter value, which is appropriate for gas at tem

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


**Fig. 7.** H 2 0–0 S(3) emission-line morphology _(top)_, velocities _(centre)_ and FWHM line widths _(bottom)_ with the JVLA 8.4 GHz radio continuum
shown as thick contours near the centre. Thin contours show the emission-line morphology in the top left panel to ease orientation. _(left_ _to_
_right):_ Single-component fit, systemic line component and blueshifted line component. The emission-line morphology and single-component and
systemic velocity maps show an hour-glass gas morphology with a strongly blue and redshifted bipolar velocity field, consistent with a pair of
bubbles that are being inflated by the radio source at the centre.



peratures _T_ ≥ 150 K, and has taken explicitly into account that
the gas is heated by shocks. Nesvadba et al. (2010) also found
M _ion_ = 2 × 10 [7] M ⊙ for warm ionised gas probed by Hα. Guillard et al. (2015) estimated M _CNM_ = 9.5 × 10 [8] M ⊙, for gas with
_T_ = 100 K and _n_ _H_ = 1000 cm [−][3] . Lanz et al. (2016) estimated
a dust mass of _M_ _dust_ = 6.05 [+] − [0] 0 [.] . [376] 218 [×][ 10] [7] [M] [⊙] [. To complete these]
different mass estimates, we now also provide an estimate of the
warmest H 2 observed through the ro-vibrational lines.

We use the approach of Scoville et al. (1982) and Mazzalay et al. (2013) to estimate the mass of very warm H 2
from the H 2 1–0 S(1) line. They set _M_ _H_ 2, _ro_ − _vib_ = 5.0875 ×
10 [13] _D_ [2] _F_ 1−0 _S_ (1) 10 [0][.][4] _[A]_ [2][.][2], where D is the luminosity distance
in Mpc, _F_ 1−0 _S_ (1) the flux of the H 2 1–0 S(1) line in erg s [−][1]

cm s [−][2], and _A_ 2.2 the extinction at 2.2 µm. Their estimate is
appropriate for gas with T=2000 K, a transition probability of
_A_ _S_ (1) = 3.47 × 10 [−][7] s [−][1], and a population fraction in the upper
level of 1.22%.

We have no estimate of A 2.2, as Paα is the only line of warm
ionised gas that is detected in our data sets, however, Nesvadba
et al. (2010) obtained a global estimate of _A_ _V_ = 0.17 mag from
stellar population modelling in the optical, assuming a Calzetti
et al. (2000) extinction law. This suggests that extinction in the



near- to mid-infrared can be safely ignored, at least for sourceintegrated estimates like the one we are doing here. We will
therefore adopt A 2.2 = 0 mag.


With these assumptions, and for an integrated H 2 1–0 S(1)
line flux of 1.5×10 [−][18] W m [−][2], we find _M_ _H_ 2, _ro_ − _vib_ = 1.4×10 [4] M ⊙ .
This is thus a very small mass component compared to the other
estimates, in spite of the bright line luminosity. The hot gas is
expected to only be a small fraction of the total gas mass because
it needs to be heated to relatively high temperatures, for example
by an AGN or by shocks, and the gas cools rapidly.


It is also interesting to compare the warm and cold molecular
gas mass in 3C 326 N with that of other galaxies, to highlight the
unusual environment that this galaxy provides. Mazzalay et al.
(2013) additionally propose an empirical calibration of warm to
cold gas probed by CO(1–0), which was derived empirically by
comparing both masses in about 50 low-redshift galaxies spanning a wide range of types. Based on their relationship, we would
expect to find a cold molecular gas mass of 9.87 × 10 [9] M ⊙ . In
Sect. 2 we have estimated a 3σ upper limit on the cold molecular gas mass in 3C 326 N of _M_ _H_ 2, _CO_ = 8 × 10 [8] _M_ ⊙, assuming
that cold molecular gas extends over the same area as the warm


Article number, page 11 of 22

_A&A proofs:_ manuscript no. aanda


**Fig. 8.** Paα emission-line morphology _(top)_, velocities _(centre)_ and FWHM line widths _(bottom)_ with the JVLA 8.4 GHz radio continuum shown
as thick contours near the centre. Thin contours show the emission-line morphology in the top left panel to ease orientation. _(left to right):_ Singlecomponent fit, systemic line component and blueshifted line component. The emission-line morphology and single-component and systemic
velocity maps show an hour-glass gas morphology with a strongly blue and redshifted bipolar velocity field, consistent with a pair of bubbles that
are being inflated by the radio source at the centre.


**Fig. 9.** One Component [NeIII]λ15.56 emission-line morphology _(left)_, velocities _(centre)_ and FWHM line widths _(bottom)_ with the JVLA 8.4 GHz
radio continuum shown as thick contours. Due to strong fringing in MIRI channel 3, the blueshifted line, while present, is noisy and difficult show
clearly. Therefore, we do not plot the two component fit.



molecular gas. This is more than an order of magnitude less that
what would be expected in normally star-forming galaxies.


Likewise, from the dust mass estimated by Lanz et al. (2016)
from Herschel SPIRE observations, _M_ _dust_ = 6.05 [+] − [0] 0 [.] . [376] 218 [×][10] [7] [ M] [⊙] [,]
we would expect a cold molecular gas mass of about 6 × 10 [9] _M_ ⊙,
assuming a typical gas-to-dust mass ratio of _G_ / _D_ = 100, as


Article number, page 12 of 22



would be typical for massive early-type galaxies with solar or
super-solar metallicity (Rémy-Ruyer et al. 2014). This is again
about a factor 10 greater than what is observed from CO line
emission for cold molecular gas. Both estimates fall however
within factors of a few from the warm H 2 mass observed in
3C 326 N.

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


**Fig. 10.** [FeII]λ1.644 emission-line morphology _(top)_, velocities _(centre)_ and FWHM line widths _(bottom)_ with the JVLA 8.4 GHz radio continuum
shown as thick contours near the centre. Thin contours show the emission-line morphology in the top left panel to ease orientation. _(left_ _to_
_right):_ Single-component fit, systemic line component and blueshifted line component. The emission-line morphology and single-component and
systemic velocity maps show an hour-glass gas morphology with a strongly blue and redshifted bipolar velocity field, consistent with a pair of
bubbles that are being inflated by the radio source at the centre.



Line λ _rest_ Flux Upper Limit

[µm] [W m [−][2] ]
Brγ 2.1660 2×10 [−][19]

PAH 6.2 1.6×10 [−][18]


**Table** **3.** 5σ upper limits to non-detected emission lines. Please note
that Brγ is in a particularly noisy part of the spectrum.


**5.** **Discussion**


_5.1._ _The nature of the emission-line regions in 3C 326 N_


In the previous section we have described the properties of the
molecular disk in 3C 326 N, which is roughly centred on the
nucleus and extends to a radius of about 1.5 kpc. This disk is
strongly kinematically disturbed with dual-component line profiles throughout the disk, and large line widths, typically 200400 km s [−][1] in the systemic, and up to 1000 km s [−][1] in the secondary, bluer component. Both components show a velocity gradient that increases from South to North, and which resembles
disk rotation when seen at low spatial resolution (Nesvadba et al.
2011). The two components are typically offset from each other
by about 80 − 100 km s [−][1] .
The excellent spatial resolution of NIRSpec reveals a large
cavity in the Northern part of the disk, that is 0.6 [′′] ×0.8 [′′] across
along its minor and major axis, respectively, corresponding to
1.0 kpc×1.4 kpc at the redshift of 3C 326 N (Fig. 3). This cavity
is delineated by three bright clumps in the far North. Inside the
cavity the gas is much fainter (but still detected) and reaches the
highest velocities relative to the nucleus (< 380 km s [−][1] ), which
are best seen in the central panel of Fig. 3.
Such a cavity may either be produced by an expanding bubble driven by AGN or star-formation feedback (e.g., Capetti et al.
1999; Mayya et al. 2023), or indicate the presence of a massive dust lane across the galaxy. Star-formation can be ruled
out given the low star-formation rate estimated with Herschel,
_S FR_ = 0.087 [+] − [0] 0 [.] . [106] 046 [M] [⊙] [(Lanz] [et] [al.] [2016).] [We] [do] [not] [identify]
any bright, warm dust or PAH emission at this location, and in
the optical, the global extinction is very low, _A_ _V_ = 0.17 mag
(Nesvadba et al. 2010), so that the presence of a massive dust
lane able to obscure near and mid-infrared emission in the H 2
1–0 S(3) and 0–0 S(3) lines, seems unlikely. We thus conclude
that we are seeing an inflating, AGN-driven bubble expanding
through the molecular gas, reaching an expansion velocity of up
to 380 km s [−][1] .



The single-line fits plotted in the left panel of Fig. 3 do not
show the true projected gas velocities, because the complex line
profiles are not well represented with a single Gaussian, but they
probe deeper than the dual-Gaussian fit. They show a clear hourglass shaped velocity distribution, which in the North is associated with the cavity, and surrounded by gas at more moderate
velocities. The same feature is identified in the systemic (redder)
component in the dual-Gaussian fits.


In the South, we do not identify an analogous blueshifted
bubble, but the global gas morphology and velocity field of the
systemic component are clearly hourglass shaped, implying a
symmetric underlying structure. The onset of this structure can
be seen in the right panel of Fig. 3, which shows the blueshifted
gas component of H 2 1–0 S(3), with velocities that are offset by
up to about −300 km s [−][1] from the systemic redshift. The structure is better seen in H 2 0–0 S(3) (Fig. 7), and also in warm
ionised gas, in particular Paα (Fig. 8).


The gas velocities are more than previously estimated from
the seeing-limited VLT/SINFONI data (Nesvadba et al. 2011) at
1 [′′] spatial resolution, and also significantly more than the rotation velocity expected for a massive elliptical galaxy. Turnover
velocities of rotating gas disks in elliptical galaxies with 3 × 10 [11]
M ⊙ in stellar mass, similar to 3C 326 N, are ∼ 150 km s [−][1],
with turnover radii around 1.5 kpc, comparable to the size of
the molecular disk in 3C 326 N (Yoon et al. 2021).


The most likely explanation of these features is that we are
seeing a bubble expanding within a massive, rotating, molecular
disk, where the observed velocity gradient is most likely a combination of disk rotation and outflowing motion. The excellent
0.1 [′′] resolution provided by NIRSpec is critical to identify the
complex kinematic features of such a configuration, and to measure gas velocities robustly. Nonetheless, the overall complexity
of the gas kinematics and morphology make it difficult to clearly
separate a kinematically perturbed from the quiescently rotating
part of the disk, and to derive, e.g., a robust estimate of the gas
energetics in a simple, unique, and analytic way. In a companion
paper, we will therefore use hydrodynamic simulations to characterise the interactions between AGN and gas disk in 3C326 N
in a more robust way (Shende et al., 2024, in prep.)


Given that star formation rates and the bolometric luminosity
of the AGN are very low, and are not sufficient to either power
the observed emission-line fluxes or drive outflows or major gas
motions (Nesvadba et al. 2010, 2011), the only possible culprit
that could inflate this bubble is the radio jet.


Article number, page 13 of 22

_A&A proofs:_ manuscript no. aanda


Line λ F T F S F C F N F NE F NW F Bub

[µm] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ] [10 [−][20] W m [2] ]

[Fe2] 1.64355 88.0 [0] 1 [.] . [91] 0 9.6 [0] 0 [.] . [23] 22 6.2 [0] 0 [.] . [45] 46 7.6 [0] 0 [.] . [15] 13 3.7 [0] 0 [.] . [15] 15 7.2 [0] 0 [.] . [11] 11 6.7 [0] 0 [.] . [36] 37
1- 0 S( 8) 1.7146 39.0 [0] 0 [.] . [79] 71 3.4 [0] 0 [.] . [21] 18 4.6 [0] 0 [.] . [24] 29 2.2 [0] 0 [.] . [12] 12 1.3 [0] 0 [.] . [095] 095 1.6 [0] 0 [.] . [1] 11 6.0 [0] 0 [.] . [29] 26
1- 0 S( 7) 1.748 85.0 [1] 1 [.] . [8] 8 11.0 [0] 0 [.] . [54] 81 10.0 [0] 1 [.] . [94] 2 6.6 [0] 0 [.] . [28] 22 2.7 [0] 0 [.] . [12] 099 4.5 [0] 0 [.] . [14] 17 12.0 [0] 0 [.] . [72] 58
1- 0 S( 6) 1.7879 54.0 [1] 1 [.] . [4] 5 5.0 [0] 0 [.] . [54] 42 3.8 [0] 0 [.] . [75] 61 3.7 [0] 0 [.] . [09] 095 2.1 [0] 0 [.] . [16] 19 2.9 [0] 0 [.] . [13] 13 6.6 [0] 0 [.] . [54] 48
1- 0 S( 5) 1.8357 120.0 [0] 0 [.] . [87] 88 16.0 [0] 0 [.] . [33] 3 12.0 [0] 0 [.] . [49] 39 12.0 [0] 0 [.] . [14] 28 5.4 [0] 0 [.] . [087] 09 8.1 [0] 0 [.] . [14] 16 17.0 [0] 0 [.] . [22] 27
Paα 1.875 96.0 [0][.][87] 13.0 [0][.][22] 9.5 [0][.][31] 8.1 [0][.][12] 3.5 [0][.][084] 7.8 [0][.][095] 11.0 [0][.][24]
0.86 0.26 0.27 0.14 0.082 0.12 0.28
1- 0 S( 4) 1.8919 38.0 [0] 0 [.] . [55] 57 4.2 [0] 0 [.] . [094] 12 3.4 [0] 0 [.] . [32] 3 3.4 [0] 0 [.] . [076] 072 1.6 [0] 0 [.] . [086] 081 1.9 [0] 0 [.] . [066] 076 3.7 [0] 0 [.] . [16] 19
1- 0 S( 3) 1.9575 180.0 [1] 1 [.] . [1] 2 26.0 [0] 0 [.] . [18] 23 19.0 [0] 0 [.] . [43] 41 18.0 [0] 0 [.] . [084] 09 8.4 [0] 0 [.] . [062] 069 13.0 [0] 0 [.] . [14] 12 24.0 [0] 0 [.] . [71] 6
1- 0 S( 2) 2.0337 65.0 [0] 0 [.] . [8] 74 8.2 [0] 0 [.] . [17] 21 6.4 [0] 0 [.] . [28] 26 6.0 0 [0] . [.] 12 [091] 2.9 [0] 0 [.] . [1] 13 4.2 [0] 0 [.] . [075] 077 7.8 [0] 0 [.] . [26] 24
1- 0 S( 1) 2.1217 150.0 [1] 1 [.] . [0] 1 21.0 [0] 0 [.] . [36] 86 14.0 [0] 0 [.] . [49] 89 15.0 [0] 0 [.] . [17] 24 7.2 [0] 0 [.] . [078] 066 11.0 [0] 0 [.] . [079] 074 18.0 [0] 0 [.] . [2] 2
1- 0 Q( 1) 2.4065 95.0 [0] 0 [.] . [76] 81 13.0 [0] 0 [.] . [096] 11 8.3 [0] 0 [.] . [15] 12 9.8 [0] 0 [.] . [073] 43 4.7 0 [0] . [.] 073 [079] 6.8 [0] 0 [.] . [065] 064 9.7 [0] 0 [.] . [23] 19
1- 0 Q( 2) 2.4133 89.0 [2] 2 [.] . [2] 3 6.8 [0] 1 [.] . [89] 4 6.8 [0] 1 [.] . [98] 1 9.5 [0] 0 [.] . [22] 33 5.1 [0] 0 [.] . [21] 23 6.8 [0] 0 [.] . [37] 44 9.3 [0] 0 [.] . [4] 4
1- 0 Q( 3) 2.4236 91.0 [0] 0 [.] . [64] 79 13.0 [0] 0 [.] . [091] 13 9.3 [0] 0 [.] . [12] 14 9.0 [0] 0 [.] . [25] 2 3.8 [0] 0 [.] . [072] 051 6.4 [0] 0 [.] . [06] 065 10.0 [0] 0 [.] . [11] 13
1- 0 Q( 4) 2.4374 21.0 [0] 0 [.] . [47] 4 2.2 [0] 0 [.] . [064] 07 1.5 [0] 0 [.] . [092] 083 1.3 [0] 0 [.] . [053] 061 0.78 [0] 0 [.] . [055] 061 0.92 0 [0] . [.] 076 [073] 1.9 [0] 0 [.] . [11] 098
1- 0 Q( 5) 2.4547 69.0 [0] 0 [.] . [51] 55 9.3 [0] 0 [.] . [084] 078 5.9 0 [0] . [.] 11 [088] 7.6 [0] 0 [.] . [059] 058 2.9 [0] 0 [.] . [1] 096 5.1 [0] 0 [.] . [058] 056 7.9 [0] 0 [.] . [11] 1
1- 0 Q( 6) 2.4754 23.0 [0] 0 [.] . [55] 57 2.1 [0] 0 [.] . [061] 059 1.8 [0] 0 [.] . [086] 088 1.3 [0] 0 [.] . [053] 055 0.61 [0] 0 [.] . [064] 061 1.1 [0] 0 [.] . [074] 061 1.4 [0] 0 [.] . [14] 13
1- 0 Q( 7) 2.5 59.0 [1] 1 [.] . [3] 0 6.9 [0] 0 [.] . [55] 39 5.3 [0] 0 [.] . [41] 38 5.2 0 [0] . [.] 14 [085] 2.3 [0] 0 [.] . [093] 084 3.8 [0] 0 [.] . [14] 15 6.3 [0] 0 [.] . [23] 25
1- 0 Q( 8) 2.5277 23.0 [0] 0 [.] . [74] 59 1.1 [0] 0 [.] . [072] 075 1.1 [0] 0 [.] . [19] 14 1.9 [0] 0 [.] . [096] 089 1.0 [0] 0 [.] . [096] 086 0.87 [0] 0 [.] . [086] 079 2.5 [0] 0 [.] . [16] 18
1- 0 Q( 9) 2.5599 40.0 [0] 0 [.] . [78] 9 3.6 [0] 0 [.] . [077] 093 3.2 [0] 0 [.] . [17] 16 2.8 [0] 0 [.] . [17] 17 1.5 [0] 0 [.] . [12] 12 2.5 [0] 0 [.] . [1] 12 3.4 [0] 0 [.] . [23] 24
1- 0 O( 2) 2.6268 51.0 [1] 0 [.] . [1] 87 5.8 [0] 0 [.] . [13] 13 5.1 0 [0] . [.] 14 [14] 3.8 [0] 0 [.] . [23] 19 1.8 [0] 0 [.] . [19] 11 3.2 [0] 0 [.] . [21] 11 5.2 [0] 0 [.] . [21] 19
1- 0 O( 3) 2.8024 100.0 [0] 1 [.] . [85] 1 14.0 [0] 0 [.] . [18] 5 9.4 [0] 0 [.] . [29] 6 11.0 [0] 0 [.] . [12] 13 5.1 [0] 0 [.] . [15] 18 6.2 [0] 0 [.] . [081] 08 11.0 [0] 0 [.] . [39] 33
0- 0 S( 6) 6.1086 160.0 [2] 2 [.] . [1] 3 13.0 [0] 0 [.] . [21] 21 13.0 0 [0] . [.] 41 [35] 15.0 [0] 0 [.] . [2] 24 5.4 0 [0] . [.] 42 [4] 10.0 [0] 0 [.] . [3] 33 18.0 [0] 0 [.] . [37] 38
0- 0 S( 5) 6.9089 590.0 [3] 3 [.] . [2] 3 71.0 [0] 0 [.] . [32] 42 67.0 [0] 1 [.] . [52] 7 62.0 0 [0] . [.] 33 [38] 33.0 [0] 0 [.] . [39] 36 35.0 [0] 0 [.] . [55] 42 83.0 [0] 0 [.] . [53] 88
Ar2 6.98337 140.0 [4][.][4] 14.0 [0][.][3] 15.0 [0][.][44] 7.3 [0][.][28] 3.6 [0][.][54] 9.9 [0][.][57] 15.0 [1][.][3]
3.7 0.23 0.36 0.28 0.6 0.61 1.3
0- 0 S( 3) 9.6645 910.0 [2] 10 [.][2] .0 96.0 [0] 11 [.][24] .0 86.0 [0] 4 [.] . [24] 8 83.0 [0] 0 [.] . [14] 17 51.0 [0] 0 [.] . [14] 16 52.0 0 [0] . [.] 14 [12] 120.0 [0] 0 [.] . [21] 19

[NeIII] 15.5509 93.0 [0] 0 [.] . [82] 89 9.1 [0] 0 [.] . [11] 17 11.0 [0] 0 [.] . [14] 19 6.1 [0] 0 [.] . [44] 39 3.3 [0] 0 [.] . [081] 08 3.8 0 [0] . [.] 073 [071] 15.0 [0] 0 [.] . [16] 16

**Table 4.** Integrated fluxes in the apertures of Fig. 11 for modelled emission lines. Errors are derived from modelling uncertainties.



The radio core is compact in all frequency bands in which
we observed 3C 326 N with the VLA (Sect. 2.3), corresponding
to beam sizes between 0.2 [′′] and 1.2 [′′], respectively, at 9 GHz and
1.4 GHz, respectively. However, we also observe 47% of missing
flux at 1.4 GHz compared to the flux measured at 5.4 [′′] beam size
with FIRST (Becker et al. 1995, Sect. 4.1). This suggests that
significant amounts of radio emission must be present at scales
between about 1 and 4.6 kpc around the nucleus. This is likely
the radio plasma that is permeating the gas disk in 3C 326 N, stirring up the gas, creating turbulence, and inflating the cavity seen
in the Northern hemisphere. A similar situation has previously
been found by Zovaro et al. (2019) in the radio galaxy 4C 31.04.


Qualitatively similar, bipolar gas motions have already been
predicted by Meenakshi et al. (2022) from hydrodynamic simulations of the passage of radio jets through a surrounding gas
disk (their Fig. 5). The jet energy of their simulation, _P_ _j_ = 10 [44]

erg s [−][1], is somewhat less than that estimated by Nesvadba et al.
(2010) for 3C 326 N, _P_ _jet_,326 = 2−13×10 [44] erg s [−][1], obtained with
different methods ranging from X-ray cavity inflation (Bîrzan
et al. 2008) to the 5 GHz core luminosity (Merloni & Heinz
2007). Nonetheless, the simulated bubbles of Meenakshi et al.
(2022) reach gas velocities of up to ∼ 300 km s [−][1], slightly lower
than the 380 km s [−][1] that we observe (albeit not correcting for


Article number, page 14 of 22



inclination), illustrating that the jet in 3C 326 N may well cause
the outstanding gas properties that we observe.
We also note that warm ionised gas in the hourglass component has a general redshift of about 100 − 200 km s [−][1] relative to H 2 . This effect is only seen in the systemic gas component, which shows this hourglass structure, not in the blueshifted
component. We are not aware of any systematic effect that could
cause this behaviour in only one line component, and which is
also seen in other warm ionised gas lines (Fig. 12). We might be
seeing an effect of stratification, where the warm ionised gas is
accelerated to somewhat different velocities, or where different
parts of the same structure are particularly bright in the warm
ionised and molecular gas (i.e. different components of the same
strcture.).


_5.2._ _An extended, turbulent, multi-phase interstellar medium_
_throughout the galaxy_


The spatially resolved line ratios in 3C 326 N provide interesting
information about the gas conditions and heating mechanism of
the gas in this galaxy. While a detailed analysis of the physical
conditions of the warm molecular gas is beyond the scope of
this paper, we can make several interesting conclusions about

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


**Table 5.** Properties of a one Gaussian fit to the integrated spectrum for all detected emission lines.


Line λ F Int FWHM _z_ V off

[µm] [10 [−][20] W m [2] ] [km s [−][1] ] [km s [−][1] ]

[FeII] 1.644 55.8 [0] 0 [.] . [6] 62 573.0 [5] 5 [.] . [8] 5 0.09006 [9] 9 [.] . [9] 8 _[e]_ _e_ [−] − [06] 06 75.1 [2] 2 [.] . [7] 7
H 2 1–0 S(8) 1.7146 19.7 [0] 0 [.] . [48] 51 523.0 [14] 13 [.] . [0] 0 0.09022 [1] 1 [.] . [9] 7 _[e]_ _e_ [−] − [05] 05 119.0 [5] 4 [.] . [1] 7
H 2 1–0 S(7) 1.748 46.2 [0] 0 [.] . [7] 67 822.0 [17] 15 [.] . [0] 0 0.08994 [1] 1 [.] . [7] 7 _[e]_ _e_ [−] − [05] 05 41.6 [4] 4 [.] . [7] 8
H 2 1–0 S(6) 1.7879 26.6 [0] 0 [.] . [51] 47 630.0 [11] 11 [.] . [0] 0 0.09054 [1] 1 [.] . [6] 5 _[e]_ _e_ [−] − [05] 05 206.0 [4] 4 [.] . [5] 0
H 2 1–0 S(5) 1.8357 95.2 [0] 0 [.] . [51] 48 713.0 [4] 3 [.] . [1] 7 0.08998 [4] 5 [.] . [8] 1 _[e]_ _e_ [−] − [06] 06 52.4 [1] 1 [.] . [3] 4
Paα 1.8751 65.5 [0] 0 [.] . [47] 47 571.0 [4] 4 [.] . [7] 7 0.09026 [5] 5 [.] . [5] 4 _[e]_ _e_ [−] − [06] 06 130.0 [1] 1 [.] . [5] 5
H 2 1–0 S(4) 1.8919 22.3 [0] 0 [.] . [33] 34 516.0 [8] 7 [.] . [3] 8 0.09022 [1] 1 [.] . [2] 2 _[e]_ _e_ [−] − [05] 05 118.0 [3] 3 [.] . [2] 2
H 2 1–0 S(3) 1.9575 141.0 0 [0] . [.][39] 35 625.0 [1] 1 [.] . [9] 8 0.09005 [2] 2 [.] . [4] 3 _[e]_ _e_ [−] − [06] 06 70.3 [0] 0 [.] . [65] 64
H 2 1–0 S(2) 2.0337 48.8 [0] 0 [.] . [42] 42 636.0 [6] 6 [.] . [0] 5 0.09009 7 [7] . [.] 5 [1] _e_ _[e]_ − [−] 06 [06] 82.7 [2] 2 [.] . [0] 1
H 2 2-1 S(3) 2.0734 14.4 [0] 0 [.] . [38] 39 669.0 [19] 17 [.] . [0] 0 0.09048 [2] 2 [.] . [5] 6 _[e]_ _e_ [−] − [05] 05 188.0 [7] 7 [.] . [0] 0
H 2 1–0 S(1) 2.1217 118.0 [0] 0 [.] . [35] 36 623.0 [1] 2 [.] . [9] 0 0.0902 [2] 2 [.] . [6] 6 _[e]_ _e_ [−] − [06] 06 112.0 [0] 0 [.] . [71] 7
H 2 1–0 Q(1) 2.4065 65.6 [0] 0 [.] . [58] 58 507.0 [4] 4 [.] . [6] 2 0.09013 [6] 6 [.] . [6] 7 _[e]_ _e_ [−] − [06] 06 92.4 [1] 1 [.] . [8] 9
H 2 1–0 Q(3) 2.4235 101.0 [0] 0 [.] . [69] 64 623.0 [3] 2 [.] . [0] 8 0.09022 [3] 3 [.] . [2] 1 _[e]_ _e_ [−] − [06] 06 118.0 [0] 0 [.] . [88] 85
H 2 1–0 Q(4) 2.4374 27.4 [0] 0 [.] . [45] 45 729.0 [9] 11 [.][7] .0 0.09067 [1] 1 [.] . [6] 6 _[e]_ _e_ [−] − [05] 05 241.0 [4] 4 [.] . [4] 4
H 2 1–0 Q(5) 2.4547 65.4 [0] 0 [.] . [37] 34 620.0 3 [3] . [.] 1 [4] 0.09025 [4] 4 [.] . [5] 5 _[e]_ _e_ [−] − [06] 06 128.0 [1] 1 [.] . [2] 3
H 2 1–0 Q(6) 2.4754 14.8 [0] 0 [.] . [27] 27 487.0 [8] 8 [.] . [6] 8 0.08996 [1] 1 [.] . [5] 4 _[e]_ _e_ [−] − [05] 05 46.9 [4] 3 [.] . [1] 9
H 2 1–0 Q(7) 2.5 46.2 [0] 0 [.] . [59] 59 758.0 [12] 11 [.] . [0] 0 0.09018 [1] 1 [.] . [1] 1 _[e]_ _e_ [−] − [05] 05 107.0 [3] 3 [.] . [1] 1
H 2 1–0 O(2) 2.6268 25.8 [0] 0 [.] . [34] 35 544.0 [8] 7 [.] . [1] 6 0.09001 [1] 1 _[e]_ .1 [−] _e_ [05] −05 60.9 [2] 3 [.] . [9] 0
H 2 1–0 O(3) 2.8024 85.8 [0] 0 [.] . [37] 4 655.0 [3] 3 [.] . [1] 1 0.0902 3 [4] . _[e]_ 8 [−] _e_ [06] −06 113.0 [1] 1 [.] . [1] 1
H 2 0–0 S(6) 6.1086 79.3 [1] 1 [.] . [2] 0 484.0 [7] 6 [.] . [2] 7 0.09003 [9] 1 [.] . [8] 1 _[e]_ _e_ [−] − [06] 05 65.7 [2] 3 [.] . [7] 0
H 2 0–0 S(5) 6.9089 416.0 [1] 1 [.] . [2] 3 560.0 [2] 1 [.] . [0] 8 0.09 [2] 2 [.] . [6] 4 _[e]_ _e_ [−] − [06] 06 58.4 [0] 0 [.] . [7] 65

[ArII] 6.98337 89.4 [1] 1 [.] . [4] 3 616.0 [9] 10 [.][4] .0 0.08995 1 [1] . [.] 3 [2] _e_ _[e]_ − [−] 05 [05] 44.2 [3] 3 [.] . [3] 5
H 2 0–0 S(3) 9.6645 643.0 [0] 0 [.] . [62] 6 684.0 [0] 0 [.] . [67] 65 0.09022 [9] 1 [.] _e_ [5] − _[e]_ 06 [−][07] 118.0 [0] 0 [.] . [26] 28

[NeIII] 15.5509 74.0 [0] 0 [.] . [43] 43 608.0 [3] 3 [.] . [7] 7 0.09012 [4] 5 [.] . [9] 3 _[e]_ _e_ [−] − [06] 06 92.1 [1] 1 [.] . [3] 5



these mechanisms from comparing the line ratios in the different
components of the galaxy.
Nesvadba et al. (2010) and Nesvadba et al. (2011) already
showed that the source-integrated rotational and ro-vibrational
line emission of this galaxy is heated by shocks; however, their
data did not have the spatial resolution necessary to resolve the
different components of this galaxy, and to search for pockets of
star formation that could be embedded in a globally shock heated
interstellar medium.

As first argued by Puxley et al. (1990), ro-vibrational lines
in the NIR are an excellent shock tracer, when comparing their
line fluxes with those of warm ionised gas lines like Brγ or Paα.
Puxley et al. (1990) used 44 HII regions observed in 30 galaxies
to infer that line ratios between H 2 S(1) and Brγ are typically
between 0.1 and 1.5 in star-forming regions, with an average of
0.5 ± 0.3. We note that this empirical ratio does not take into account potential effects from shocks present in these star-forming
regions. Outliers in their sample with much brighter H 2 emission
include in particular NGC 6240 and NGC 3079, known to have
large amounts of shocked gas (e.g., Keel 1990; Veilleux et al.
1994; Meijerink et al. 2013; Medling et al. 2021).
Instead of Brγ and S(1), we will in the following use Paα
and S(3) for our comparison. Paα is significantly brighter than
Brγ, but falls in between the atmospheric windows for nearby
galaxies observed from the ground. For a galaxy at _z_ ∼ 0.1 like
3C 326 N and observations from space like with JWST, this is



however not a concern. Moreover, Paα is less affected by underlying absorption lines from stellar photospheres, which can
artificially lower the measured Brγ flux in medium-resolution
spectra like those provided by the NIRSpec IFU.
The decrement between Brγ and Paα for gas with an electron temperature, T _e_ = 10 [4] K, is F _Pa_ α /F _Br_ γ = 11.2 (e.g., Dopita
et al. 2003), and the line ratio between H 2 1–0 S(3) and S(1)
in 3C 326 N is on average F _S_ (3) /F ( _S_ 1) = 1.2 (Tab. 4). This implies that the Puxley et al. (1990) criterion of F _Br_ γ /F _H_ 2 1−0 _S_ (3) ∼ 1
for line emission from shocked gas translates into a criterion of
F _H_ 2 1−0 _S_ (3) - 0.1 F _Pa_ α .
Line emission throughout 3C 326 N is well above this threshold. When we take the ratio of total source Paα to H 2 1–0 S(3)
we find the same low value 0.5 as in Nesvadba et al. (2011). If
we take the ratios within the apertures defined in Fig. 11, we find
a ratio of 0.5 for aperture S, of 0.6 in aperture NW, 0.45 in N,
and 0.4 in NE.

This implies that shocks dominate the gas heating of molecular gas throughout the galaxy not only in a global sense, but
also for individual features seen in the line maps of Fig. 3. This
includes in particular the compact clumps in the North of the
galaxy, which from their morphology are reminiscent of young
star-forming clusters, as are commonly found in other galaxies.
The line ratios however, suggest that they are not heated by UV
photons from young stars, but from shocks like the ambient gas,
otherwise Paα should be an order of magnitude brighter com

Article number, page 15 of 22

_A&A proofs:_ manuscript no. aanda



pared to the S(3) line than what is observed. They are thus more
likely gas that has fragmented along the rim of the jet-inflated
bubble.

Shocks are also the dominant heating mechanism of the purerotational line emission of H 2 in 3C 326 N, as already shown by
Nesvadba et al. (2010). They constructed a diagnostic diagram
based on PAH, H 2 0–0 S(1), CO(1–0), and 24 µm dust emission, and compared with expectations from theoretical models of
star-forming, photon-dominated regions (PDRs), to find that the
source-integrated S(1) flux of 3C 326 N exceeded the gas heating possible with UV photons from young stars by more than an
order of magnitude. They also disfavoured cosmic ray heating,
arguing that the required cosmic ray flux densities would be so
high that the H 2 molecule would be destroyed, leaving shocks as
only plausible gas heating source.

Nesvadba et al. (2010) also compared the source-integrated
flux measurements of H 2 0–0 S(0) to S(7), and fitted the shock
models of Flower & Pineau Des Forêts (2010), finding that
at least three different shock velocities between _v_ _s_ = 4 and
40 km s [−][1] were needed for C-type shocks to explain the excitation diagram, for two assumptions on gas density, respectively
( _n_ _H_ 2 = 10 [3] and 10 [4] cm [−][3], respectively). From their Fig. 3 we can
read off that the H 2 0–0 S(3) line is most sensitive to gas heated
by intermediate-velocity shocks, whereas the S(5) line is dominated by the highest shock velocities, and representative of the
least important mass component. This is one of the reasons why
we focus the discussion of the warm molecular gas in 3C 326 N
onto the S(3) component.

We also note that, on top of the similar gas morphologies
in different lines of molecular and warm ionised gas highlighted
in Sect. 4, the line profiles and velocities of the H 2 1–0 S(3),
H 2 1–0 S(5), H 2 0–0 S(3), and H 2 0–0 S(5) all agree very well.

[FeII]λ1.644 and Paα also agree with each other and relatively
well with the molecular line profiles. This can be seen by comparing the line maps shown in Figs.3, 7, 8, and 10, and also
by comparing the line profiles extracted from several apertures
within 3C 326 N shown in Fig. 12.
Fig. 12 shows again the offset already discussed in Sect. 5.1
between the velocities of the ionised and molecular emission.
This offset is most apparent in the systemic line component
which is redshifted with respect to the molecular lines by 100200 km s [−][1] in the southern component, the galaxy centre, and the
centre of the northern component (aperture N in Fig. 11). The
systemic component is then in agreement in velocity with the
molecular lines in the Western wing of the northern component.
However, in the Eastern wing of the northern component (aperture NW) both ionised emission lines are double peaked with
both peaks being comparable in amplitude. The second peak is
blueshifted with respect to the molecular lines by 200 km s [−][1] .
The one line with a strongly different morphology is

[NeIII]λ15.56, which does not follow the same morphology seen
in the other lines, but is fairly symmetric about the nucleus.

[NeIII]λ15.56 can be photoionised by AGN, star formation in
extreme cases, or shocks. Nesvadba et al. (2010) estimated a
line ratio of [NeII]λ12.81/[NeIII]λ15.56 ∼ 2.2 for shock conditions favoured by the molecular gas lines. We can use the

[NeII] flux measured by Ogle et al. (2007) of F([NeII]λ12.82)=
4 × 10 [−][19] W m [−][2], and the source-integrated [NeIII]λ15.56
flux in Table 4, to measure a source-integrated line flux of

[NeII]λ12.81/[NeIII]λ15.56= 4.3, which is about twice as large
as the value expected for shocked gas. This would be consistent
with having a second line component present, presumably heated
by AGN photoionisation.


Article number, page 16 of 22



In conclusion, the ionised and molecular lines follow globally the same approximate bulk velocity, although local differences do exist. Similar gas kinematics in different gas phases are
expected in multi-phase media, where the different gas phases
do not probe different components of a galaxy, but are co-spatial
and undergoing a constant mass and energy exchange (Guillard
et al. 2009). This is characteristic for gas in non-equilibrium,
rapidly changing conditions, e.g., in rapidly cooling post-shock
gas following the passage of a shock front, e.g., from an expanding radio source (Mukherjee et al. 2018).


_5.3._ _3C 326 N in the context of turbulence-driven star_

_formation_


5.3.1. Kennicutt-Schmidt diagram


One of the outstanding properties of radio galaxies with
large amounts of warm molecular Hydrogen are their low
star-formation rates compared to their molecular gas content.
Schmidt (1968) and Kennicutt (1989) showed that gas-mass surface densities are a major determinant of the star-formation rate
density in galaxies. A subset of MOHEGs show a significant
offset from the typical relationship between gas mass and starformation rate surface densities in normal star-forming galaxies
by factors 10-100. This offset is seen even in spiral galaxies with
normal stellar mass surface densities and moderately bright radio
jets (Nesvadba et al. 2021).
The offset of radio galaxies in the Kennicutt-Schmidt diagram was first noticed by Nesvadba et al. (2010), who compared the molecular gas mass surface densities of these galaxies with star formation traced by PAH emission. PAHs are an
imperfect tracer of star formation, as PAHs are relatively easily destroyed by shocks (Micelotta et al. 2010; Egorov et al.
2023). Subsequently, this observation was confirmed with Herschel/SPIRE photometry (Lanz et al. 2016). The star-formation
rate of 3C 326 N that these measurements found is SFR=
0.087 − [+] 0 [0] . [.] 046 [106] [M] [⊙] [yr] [−][1] [.]
We have now presented new ALMA observations (Sect. 2.2),
which have revealed that the previous CO(1–0) detection of Nesvadba et al. (2010), based on shallower data observed with the
IRAM Plateau de Bure Interferometer in 2009 could not be confirmed. These data had much smaller bandwidth, and a large,
5 [′′] beam, making it impossible to separate the central continuum emission from putative more extended line emission. The
new ALMA data place an upper limit of 8 × 10 [8] M ⊙ on the cold
molecular gas mass derived from the CO(1–0) line flux for a
Milky-Way like H 2 -to-CO conversion factor of α _CO_ = 4.3 _M_ ⊙ /
(K km s [−][1] pc [2] ).
In Fig. 13, we show the Kennicutt-Schmidt diagram with the
updated position of 3C 326 N, taking these new measurements
into account. We estimated a gas mass surface density of cold
molecular gas by using the upper limit on the molecular gas derived in Sect. 2.2, and assumed that the cold molecular gas morphology follows that of H 2 0–0 S(3). We also assume that star
formation is distributed over the same area. This is a conservative
estimate, as we do not observe any signatures of star formation in
our data. With these estimates and assumptions, 3C 326 N falls
a factor 23 below the usual Kennicutt-Schmidt relationship for
normally star-forming galaxies. Villar Martín et al. (2023) show
that cold gas morphology can be smaller than the H 2 ; however,
a smaller morphology would only increase the discrepancy.
For comparison, we also show where the galaxy falls when
using the observed H 2 0–0 S(3) mass surface densities. To estimate these, we adopted the total mass estimate of warm molecu

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST



H 2 0 0 S(5)


20°05'49.5"


49.0"


48.5"


48.0"


47.5"


47.0"


15 [h] 52 [m] 09.20 [s] 09.10 [s] 09.05 [s]


RA


17.5


15.0


12.5


10.0


7.5


5.0


2.5


0.0

4.5 5.0 5.5 6.0

H 2 0-0 S(3)/H 2 1-0 S(3)



H 2 1 0 S(5) blurred



20°05'49.0"


48.5"


48.0"


47.5"


47.0"







10


8


6


4


2


0



15 [h] 52 [m] 09.20 [s] 09.10 [s] 09.05 [s]


RA


4.5 5.0 5.5 6.0 6.5

H 2 0-0 S(5)/H 2 1-0 S(5)



**Fig. 11.** Top: Integrated flux for the H 2 0–0 S(5) line and the H 2 1–0 S(5) line as titled. The H 2 1–0 S(5) flux image has been convolved to the PSF
at the H 2 0–0 S(5) line. The original PSF for H 2 1–0 S(5) and the post-convolution PSF are the white and black filled circles in the H 2 1–0 S(5) plot,
respectively. Bottom: Ratio of 1–0 to 0–0 line fluxes for the apertures shown in the top image.

























**Fig. 12.** The extracted line profiles for a selection of observed lines. The zero velocity is set by the CO band head absorption lines. The lines are
extracted using the apertures in Fig. 11 as indicated by the coloured marker in the corner of each subplot.


Article number, page 17 of 22

_A&A proofs:_ manuscript no. aanda



lar hydrogen of 2 × 10 [9] _M_ ⊙ (Nesvadba et al. 2010) and assumed
that changes in gas excitation are not large enough to strongly
alter the overall mass-to-light ratio of the gas. This allowed us to
estimate a range of gas-mass surface densities, Σ = 200−680 M ⊙
pc [−][2], from the surface-brightness distribution of the line shown
in Fig. 7. Showing the position of 3C 326 N for warm molecular
Hydrogen in this diagram bears of course a large risk of systematic errors, but allows us also to estimate where this galaxy
would approximately fall if the gas heating that is required to
keep this gas warm, was absent. It can be seen that the galaxy
falls about 2 orders of magnitude below normal star-forming
galaxies in this case.


5.3.2. Turbulent energy in the warm molecular gas


The large line widths observed with NIRSpec and MIRI MRS
show clearly that the gas in 3C 326 N is strongly stirred up and
likely made turbulent through the interactions with the radio jet
(Nesvadba et al. 2010, 2011). The 0.11 [′′] size of the PSF corresponds to a projected size scale of 190 pc, which demonstrates
that the large line widths that have been previously observed are
not due to velocity offsets between different gas components on
kpc scales, but are present even at size scales typical of giant
molecular clouds.
This is an important observation, because interstellar turbulence is now recognised as a major regulation mechanism of
star formation (Krumholz & McKee 2005; Federrath et al. 2010;
Padoan & Nordlund 2011; Hennebelle & Chabrier 2011; Hennebelle & Falgarone 2012). In 3C 326 N, the only energy source
that is powerful enough to power velocity offsets and line widths
as observed, is the radio jet. We know also from hydrodynamic
simulations that radio jets can make surrounding gas turbulent
(e.g., Mukherjee et al. 2018), and impact star formation, by locally compressing, but globally dispersing the gas (Mandal et al.
2021, Mandal et al. 2024 In prep.).
The virial parameter, α _vir_ allows to quantify the amount of
turbulent energy compared to gravitational binding energy in
molecular clouds (Bertoldi & McKee 1992; Sun et al. 2018).
We set α _vir_ = 5σ [2] _cl_ [(][π] _[ G R]_ _[cl]_ [ Σ] _[gas]_ [)] [−][1] [, following Bertoldi & McKee]
(1992). σ _cl_ is the line width dominated by turbulent motion, Σ _gas_
the gas-mass surface density, _R_ _cl_ the size of the cloud, and _G_ the
gravitational constant. Giant molecular clouds in the Milky Way,
as well as nearby spiral galaxies are found to be star-forming for
α _vir_ ∼ 1. In gas with much higher turbulent velocity, star formation is suppressed. Nesvadba et al. (2011) showed with lowresolution SINFONI data, that the high interstellar turbulence in
3C 326 N caused by the radio jet can suppress star formation,
provided that high turbulent velocities prevail down to the typical scales of giant molecular clouds, and cloud complexes.
With our NIRSpec and MRS data, we are now able to test this
prediction, by measuring the line broadening at the spatial resolution limit of our data, i.e., 0.11 [′′] for H 2 1–0 S(3), corresponding to 190 pc, and 0.3 [′′] for H 2 0–0 S(3), corresponding to 530 pc.
In particular, we identified the narrowest widths of both lines,
FWHM=170 km s [−][1] for H 2 1–0 S(3) and FWHM=147 km s [−][1]
for H 2 0–0 S(3).
Both line widths are shown in Fig. 14 as large, upwardpointing arrows to indicate that these values are the lowest
of a set of measurements, where the highest values are 1000 km s [−][1] . The position of these measurements is compared
with several expected distributions. The red dotted line indicates
where clouds fall with α _vir_ = 1, for a gas mass surface density of
Σ = 250 M ⊙ pc [−][2] appropriate for 3C 326 N. Molecular clouds in
the Milky Way fall slightly below that line because the Galac

Article number, page 18 of 22



tic value is somewhat lower (Heyer et al. 2009). The yellow
band indicates the range implied by Larson’s scaling relationship between radius and turbulent velocity for turbulent molecular clouds (Larson 1981), extrapolating from the measured values on 1 kpc scales downward to the scales probed by our new
data, and beyond. We allow for a range of about a factor 8 in variation. The blue line supposes that the H 2 line emission observed
in 3C 326 N is powered by the dissipation of turbulent energy on
sub-parsec scales, which implies that _L_ _H_ 2 / _M_ _H_ 2 = 3/2 _f_ _H_ 2 σ [3] _cl_ [/] _[R]_ _[cl]_
(McKee & Ostriker 2007). _L_ _H_ 2 and _M_ _H_ 2 are the luminosity and
mass of warm _H_ 2, respectively, with _L_ _H_ 2 / _M_ _H_ 2 = 0.06 _L_ ⊙ / _M_ ⊙
(Nesvadba et al. 2010, 2011). We allow for a fiducial fraction
of about 50% to the total radiative gas cooling from other gas
phases, parameterised by the correction factor _f_ _H_ 2 = 0.5.
We find that the new observations fall well within the range
predicted by the previous VLT/SINFONI observations obtained
on kpc scales, which reinforces the previous statement of Nesvadba et al. (2011) that the absence of star formation in 3C 326 N
is well explained by the high turbulent gas velocities. One could
argue that the high temperature rather than the mechanical energy could be the cause, however, since mechanical interactions
of the radio jet with the gas are the primary heating mechanism
in this galaxy, the gas heating is a concomitant effect of the same

process.
The good agreement of our new and old data with the Larson
scaling relationship and radiative efficiency of H 2 line emission
produced through the dissipation of turbulent energy adds further
credence that the interactions between radio jet and gas are indeed raising the turbulent energy in the gas of 3C 326 N. Thanks
to the high spatial resolution of the new data, we can also rule out
that small pockets of less turbulent gas exist in some regions of
3C 326 N. Very broad line widths are found to be ubiquitous in
the molecular gas throughout the galaxy, at least down to scales
of 200 pc.


**6.** **On using the H** **2** **1–0 lines as proxy to the H** **2** **0–0**
**lines in distant galaxies**


The rotational H 2 lines probe the by far dominant mass component of warm, shocked Hydrogen, and are thus very interesting tracers of interstellar turbulence. This makes them important
lines to study in particular in distant galaxies at intermediate to
high redshifts, where massive galaxies were forming stars at high
rates from interstellar gas that had significantly higher mass surface densities and turbulent velocities than today (e.g., Guillard
et al. 2015). Unfortunately, the rotational lines are redshifted out
of the MIRI bandpass at _z_ = 1.89 for H 2 0–0 S(3), and at z=3.04
for H 2 0–0 S(5) for the nominal spectral coverage of the MRS.
The redshift limit becomes even more constraining when taking
into account the loss in count rate in Channel 4 observed during
the first year of JWST operations. For example, without including Channel 4C, the limiting redshifts are _z_ = 0.83 for H 2 0–0
S(3), and _z_ = 1.56 for H 2 0–0 S(5).
The situation is much better for the ro-vibrational lines which
fall into the MRS bandpass out to, e.g., redshift _z_ = 12.1 and
_z_ = 7.3, respectively, for observations of 1–0 H 2 S(3) with and
without Channel 4C. However, it is not clear to what degree observations of the ro-vibrational lines can be used as a proxy of
the pure-rotational lines. The temperature range they probe is
much higher than for the rotational lines (T∼ 1000 K instead to
T∼ 100 K), and in some environments, where the mid-infrared
spectrum is strongly dominated by rotational line emission from
warm shocked molecular Hydrogen, like Stephan’s Quintet (Appleton et al. 2006), the ro-vibrational lines are very faint.

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST


**Fig. 13.** Kennicutt-Schmidt law between star-formation rate and molecular gas mass surface density. The large blue and red dot show the position
of 3C 326 N when using the mass surface density of cold molecular gas probed by CO(1–0) and H 2 0–0 lines, respectively. For the latter estimate,
the black line shows the range of surface-brightness observed with MIRI. Small empty circles show several sets of normally star-forming galaxies
in the nearby Universe taken from Fischer et al. (2013), Kennicutt (2020), and Saintonge et al. (2013). Green and grey squares show the MOHEGs
of Ogle et al. (2010) and Alatalo et al. (2015).



Our MIRI and NIRSpec observations provide us with an excellent opportunity to study in a very clean environment not contaminated by star formation or strong AGN emission, to what
degree information from ro-vibrational lines heated by shocks
can be trusted to infer the basic properties of the gas probed by
pure-rotational lines. For different regions of the galaxy we compare the 1–0 and 0–0 S(3) and S(5) lines to demonstrate whether
the 1–0 lines are good proxies for the 0–0 lines in the case of
galaxies with strong shocks. To this end, we convolved the data
cubes of H 2 1–0 S(3) and S(5) with a Gaussian PSF to produce
data cubes that have the same spatial resolution as the data cubes
of the mid-infrared lines.

We blur the 1–0 lines with a Gaussian using a FWHM based
on the quadratic difference between the 1–0 and 0–0 PSFs. Both
1–0 lines are covered by NIRSpec and therefore can be explained by a PSF of 0.115" in our observing mode (D’Eugenio
et al. 2023). The PSF for the 0–0 lines can be derived by setting _FWHM_ _PS F_ = 0.033λ(µm) + 0.106 from Law et al. (2023).
When extracting line fluxes, we used the apertures in Fig. 11 discarding pixels that have a flux of more than 5 σ away from the
average of the 4×4 pixel median filtered image where σ is the
standard deviation of the difference between the model flux image and the median filtered image. The spectral resolving power
is similar with both instruments, so that no further correction is
required in spectral direction. This allows us to compare directly
whether both sets of lines probe similar morphologies and gas
kinematics.

This can be seen in the images of Fig. 11. For example, there
is a bright blob in the Northern part of the galaxy that is less pronounced in the 1–0 line flux than that of the 0–0 line. Overall, the
ratio for both the 0–0 and 1–0 S(3) and S(5) lines differ slightly
between the Northern and Southern components but remain con


sistent within 15%. The average 0–0/1–0 ratio for all apertures in
Fig. 11, not including the cavity or total source (blue and green
apertures), is 5.5 ± 0.6. The Southern component has a lower line
ratio than the Northern component for both S(3) and S(5) lines.
These variations indicate that the shock conditions are not
exactly the same everywhere in the galaxy, but that the uncertainties that this implies, e.g., for determining global emission-line
morphologies and to isolate individual structures like shocks and
clumps within the galaxy, are not larger than other systematic
uncertainties in this kind of work, e.g., due to the stellar initial
mass function or the CO-to-H 2 conversion factor. Of course, for
a more detailed analysis of the gas conditions, measurements of
the 0–0 lines are still required.
The gas kinematics probed by the rotational and rovibrational lines are also very similar throughout the galaxy.
Fig. 12 shows a comparison of the line profiles of H 2 1–0
S(3) and S(5), H 2 0–0 S(3) and S(5), of Paα, [FeII]λ1.644, and

[NeIII]λ15.56. This comparison is made for the six apertures
shown in Fig. 11.
The systemic components of the 1–0 and 0–0 lines follow
each other very well in velocity and line widths for both S(3)
and (5). The blueshifted component is more enhanced in the 1–0
than in the 0–0 lines in some apertures, however, the differences
are small. This suggests that turbulent line broadening and global
outflow properties can be estimated from the 1–0 lines when the
0–0 lines are not available. We conclude that the shocked molecular Hydrogen in galaxies dominated by turbulent gas motion
shows globally similar kinematics and morphologies in the 1–0
and 0–0 lines. Differences present in blue wings and line ratios
however suggest that dedicated observations of the 0–0 lines are
required to derive robust estimates, e.g., of outflow masses or gas
excitation conditions.


Article number, page 19 of 22

_A&A proofs:_ manuscript no. aanda



**Fig.** **14.** Gaussian line width, σ, of warm molecular gas in 3C 326 N
as a function of radius. The minimal line widths observed in H 2 1–0
S(3) and H 2 0–0 S(3) at spatial resolutions corresponding to 190 pc and
530 pc, respectively, are shown as large, upward-pointing arrows. The
broadest line widths observed in both lines are > 1000 km s [−][1], and fall
well outside the plot. Black dots show previous SINFONI observations
of H 2 1–0 S(3) at kpc-scale resolution. The red dotted line shows the
position of gas clouds with α _vir_ = 1, for the gas-mass surface densities
observed in 3C 326 N. Light blue circles show molecular clouds in the
Milky Way. The yellow band indicates the range where the data should
fall if the Larson (1981) scaling relations of turbulent clouds apply. The
blue line indicates where the lines should fall for typical mass-to-light
ratios of gas cooling through turbulent dissipation. See text for details.


**7.** **Summary**


We have obtained new Cycle-1 open time observations with the
JWST NIRSpec and MIRI integral-field units, to study the interactions of the radio jet and molecular gas in the nearby (z=0.09)
radio galaxy 3C 326 N. This galaxy is one of the best-studied
examples of a subset of radio galaxies characterised by bright
line emission from warm molecular Hydrogen previously seen
with the Spitzer space telescope (Ogle et al. 2007, 2010), while
typical star-formation tracers like PAHs or a dust continuum are
either weak or undetected. Subsequently, Nesvadba et al. (2010)
showed that some of these galaxies fall well below the usual starforming sequence in the Kennicutt-Schmidt diagram, suggesting
that star formation may proceed at lower rates than in galaxies
without radio jets. The main results of our new study are as follows:


**–**
We find bright line emission of 19 ro-vibrational lines of the
S, Q, and O series of warm molecular Hydrogen, and three
lines of pure-rotational line emission, H 2 0–0 S(3), S(5), and
S(6). We also obtain a robust systemic redshift estimate of
_z_ = 0.08979 from the CO band heads observed with NIRSpec, using a K4III giant as well matching template.
**–** The gas probed by these emission lines is in a 3 kpc sized
disk, already identified by Nesvadba et al. (2011) with
seeing-limited data. At 10× higher spatial resolution with
NIRSpec, we identify a kpc-sized cavity in the Northern
hemisphere of the disk, delineated by three bright knots of
line emission at the far end. We interpret this feature as the
signature of an expanding, jet-inflated bubble within a rotating gas disk. Similar morphologies are seen in ro-vibrational
and rotational lines, as well as the warm ionised gas lines

[FeII]λ1.644, Paα and [ArII]λ6.98. Only [NeIII]λ15.56 has
a distinct morphology more centred on the nucleus.


Article number, page 20 of 22



**–**
Line profiles are complex, with at least two line components
throughout the disk seen in the ro-vibrational and rotational
lines of warm H 2 as well as the warm ionised gas lines
Paα and [FeII]. We developed a new Bayesian line fitting
technique based on a Markov Chain Monte Carlo approach,
which allows us to robustly fit both line components throughout the data set. The cavity is associated with the redshifted,
Northern side of a clear hourglass-shaped velocity distribution in the Southern and Northern part of the disk, with maximal velocities of 380 km s [−][1] . We interpret this velocity pattern as the signature of two expanding bubbles, given the
large velocity gradient and line widths, more moderate velocities in fainter surrounding gas, and the clear association
with the cavity in the North.
**–** We also present new JVLA radio observations at 1.5 GHz,
7.3 GHz, and 9 GHz, identifying a compact radio core. Comparison with FIRST shows 47% of missing flux at 1.5 GHz
on scales between 1 and 4.6 kpc from the nucleus. This is
likely emission from the radio plasma that is inflating the
cavity, stirring up the gas, and making it turbulent.
**–** Line emission of H 2 and most warm ionised lines is heated
by shocks. This has already been shown previously from
source-integrated data (Nesvadba et al. 2010), however, we
can now also rule out the presence of smaller areas dominated by heating from young stars, down to scales of 190 pc.
**–** From archival ALMA CO(1–0) observations we found that
a previous detection of cold molecular gas done with the
IRAM Plateau de Bure Interferometer in 2009 was spurious, and we now place an upper limit of 8 × 10 [8] M ⊙, about
3× less than the cold molecular gas mass of Nesvadba et al.
(2010). This highlights the outstanding nature of this galaxy.
3C 326 N falls still below the Kennicutt-Schmidt law if the
new upper limit is not very far from the actual gas mass.
When taking into account that maintaining the observed high
gas mass requires near-constant gas heating through the radio jet (Nesvadba et al. 2010), we also argue that, in absence
of that heating, 3C 326 N would fall about a factor 100 below the Kennicutt-Schmidt relation of star forming galaxies,
an argument derived from using the warm instead of the cold
molecular gas mass for this comparison.

**–**
The broad line widths and bright line emission can be taken
as indicative of enhanced turbulent gas motion and rapid turbulent energy dissipation. We compare observed line widths
and size scales with the characteristics of molecular clouds
and the line emission produced by turbulent dissipation on
sub-pc scales, finding that our data agree with this scenario
from kpc scales and down to scales of 190 pc. Star-formation
theory postulates that enhanced turbulence can suppress star
formation for line widths as observed in 3C 326 N. This reinforces previous arguments that the turbulence injected by
radio jets into the interstellar gas of their host galaxies may
indeed inhibit star formation, as postulated by cosmological
simulations of galaxy evolution.


3C 326 N is a very clear environment where shocks dominate the
properties of the interstellar gas. We compare the morphology
and line widths of the ro-vibrational and rotational lines of warm
H 2 to infer whether the former can be used as a proxy to derive the properties of the latter at redshifts where rotational lines
have moved out of the MIRI bandpass, e.g., at Cosmic Noon.
Rotational lines probe by far the dominant mass component of
warm molecular gas. Galaxies in the early Universe often show
significant line broadening attributed to enhanced levels of turbulence, and often contain high column densities of molecular

Leftley et al.: Warm H 2 in 3C 326 N seen with the JWST



gas, which makes observations of warm H 2 particular interesting. Our results suggest that, while local differences do exist due
to a variation in excitation conditions, the ratio of the S(3) to S(5)
line fluxes in both phases agree to within about 60%, and the line
widths within the measurement uncertainties. This is comparable
to other systematic uncertainties when studying distant galaxies,
e.g., due to the stellar initial mass function or the CO-to-H 2 conversion factor, and suggests that ro-vibrational line emission may
be an interesting tracer to study the turbulent interstellar medium
of distant galaxies, e.g., at Cosmic Noon, and up to the Epoch
of Reionization for particularly bright galaxies and gravitational
lenses.


**References**


Alatalo, K., Lacy, M., Lanz, L., et al. 2015, The Astrophysical Journal, 798, 31,
aDS Bibcode: 2015ApJ...798...31A
Appleton, P. N., Xu, K. C., Reach, W., et al. 2006, The Astrophysical Journal,
639, L51, aDS Bibcode: 2006ApJ...639L..51A
Armus, L., Lai, T., U, V., et al. 2023, The Astrophysical Journal, 942, L37, aDS
Bibcode: 2023ApJ...942L..37A
Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, Astronomy
and Astrophysics, 558, A33
Becker, R. H., White, R. L., & Helfand, D. J. 1995, The Astrophysical Journal,
450, 559, aDS Bibcode: 1995ApJ...450..559B
Bertoldi, F. & McKee, C. F. 1992, The Astrophysical Journal, 395, 140, aDS
Bibcode: 1992ApJ...395..140B
Bharadwaj, V., Reiprich, T. H., Lovisari, L., & Eckmiller, H. J. 2015, Astronomy
and Astrophysics, 573, A75, aDS Bibcode: 2015A&A...573A..75B
Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, Annual Review of Astronomy
and Astrophysics, 51, 207, aDS Bibcode: 2013ARA&A..51..207B
Bîrzan, L., McNamara, B. R., Nulsen, P. E. J., Carilli, C. L., & Wise, M. W. 2008,
The Astrophysical Journal, 686, 859, aDS Bibcode: 2008ApJ...686..859B
Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, The Astrophysical Journal,
533, 682, aDS Bibcode: 2000ApJ...533..682C
Capetti, A., Axon, D. J., Macchetto, F. D., Marconi, A., & Winge, C. 1999, The
Astrophysical Journal, 516, 187, aDS Bibcode: 1999ApJ...516..187C
Carnall, A. C. 2017, SpectRes: A Fast Spectral Resampling Tool in Python,
arXiv:1705.05165 [astro-ph]
Croton, D. J., Springel, V., White, S. D. M., et al. 2006, Monthly Notices of the
Royal Astronomical Society, 365, 11, aDS Bibcode: 2006MNRAS.365...11C
D’Eugenio, F., Perez-Gonzalez, P., Maiolino, R., et al. 2023, A fast-rotator poststarburst galaxy quenched by supermassive black-hole feedback at z=3, publication Title: arXiv e-prints ADS Bibcode: 2023arXiv230806317D
Dicken, D., Tadhunter, C., Axon, D., et al. 2012, The Astrophysical Journal, 745,
172, aDS Bibcode: 2012ApJ...745..172D
Dopita, M. A., Groves, B. A., Sutherland, R. S., & Kewley, L. J. 2003, The
Astrophysical Journal, 583, 727, aDS Bibcode: 2003ApJ...583..727D
Drevet Mulard, M., Nesvadba, N. P. H., Meenakshi, M., et al. 2023, Astronomy
and Astrophysics, 676, A35, aDS Bibcode: 2023A&A...676A..35D
Egorov, O. V., Kreckel, K., Sandstrom, K. M., et al. 2023, The Astrophysical
Journal, 944, L16, aDS Bibcode: 2023ApJ...944L..16E
Ellison, S. L., Teimoorinia, H., Rosario, D. J., & Mendel, J. T. 2016, Monthly Notices of the Royal Astronomical Society, 458, L34, aDS Bibcode: 2016MNRAS.458L..34E
Emsellem, E., Cappellari, M., Krajnovi´c, D., et al. 2011, Monthly Notices
of the Royal Astronomical Society, 414, 888, aDS Bibcode: 2011MNRAS.414..888E

Federrath, C., Roman-Duval, J., Klessen, R. S., Schmidt, W., & Mac Low,
M. M. 2010, Astronomy and Astrophysics, 512, A81, aDS Bibcode:
2010A&A...512A..81F
Ferrarese, L. & Merritt, D. 2000, The Astrophysical Journal, 539, L9, aDS Bibcode: 2000ApJ...539L...9F
Fiore, F., Feruglio, C., Shankar, F., et al. 2017, Astronomy and Astrophysics,
601, A143, aDS Bibcode: 2017A&A...601A.143F
Fischer, T. C., Crenshaw, D. M., Kraemer, S. B., & Schmitt, H. R. 2013, The
Astrophysical Journal Supplement Series, 209, 1
Flower, D. R. & Pineau Des Forêts, G. 2010, Monthly Notices of the Royal
Astronomical Society, 406, 1745, aDS Bibcode: 2010MNRAS.406.1745F
Forman, W., Nulsen, P., Heinz, S., et al. 2005, The Astrophysical Journal, 635,
894, aDS Bibcode: 2005ApJ...635..894F
Gebhardt, K., Bender, R., Bower, G., et al. 2000, The Astrophysical Journal, 539,
L13, aDS Bibcode: 2000ApJ...539L..13G
Goodman, J. & Weare, J. 2010, Communications in Applied Mathematics and
Computational Science, 5, 65



Guillard, P., Boulanger, F., Lehnert, M. D., et al. 2015, Astronomy & Astrophysics, 574, A32, publisher: EDP Sciences
Guillard, P., Boulanger, F., Pineau Des Forêts, G., & Appleton, P. N. 2009, Astronomy and Astrophysics, 502, 515, aDS Bibcode: 2009A&A...502..515G
Guillard, P., Ogle, P. M., Emonts, B. H. C., et al. 2012, The Astrophysical Journal, 747, 95, aDS Bibcode: 2012ApJ...747...95G
Hennebelle, P. & Chabrier, G. 2011, The Astrophysical Journal, 743, L29, aDS
Bibcode: 2011ApJ...743L..29H
Hennebelle, P. & Falgarone, E. 2012, Astronomy and Astrophysics Review, 20,
55, aDS Bibcode: 2012A&ARv..20...55H
Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, The Astrophysical
Journal, 699, 1092, aDS Bibcode: 2009ApJ...699.1092H
Ho, L. C. & Keto, E. 2007, The Astrophysical Journal, 658, 314, aDS Bibcode:
2007ApJ...658..314H
Keel, W. C. 1990, The Astronomical Journal, 100, 356, aDS Bibcode:
1990AJ....100..356K
Kennicutt, R. 2020, 235, 362.01, conference Name: American Astronomical Society Meeting Abstracts #235 ADS Bibcode: 2020AAS...23536201K
Kennicutt, Jr., R. C. 1989, The Astrophysical Journal, 344, 685, aDS Bibcode:
1989ApJ...344..685K
Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019, Annual Review of Astronomy and Astrophysics, 57, 511, aDS Bibcode: 2019ARA&A..57..511K
Kirkpatrick, C. C., Gitti, M., Cavagnolo, K. W., et al. 2009, The Astrophysical
Journal, 707, L69, aDS Bibcode: 2009ApJ...707L..69K
Krumholz, M. R. & McKee, C. F. 2005, The Astrophysical Journal, 630, 250,
aDS Bibcode: 2005ApJ...630..250K
Lai, T. S.-Y., Armus, L., U, V., et al. 2022, The Astrophysical Journal Letters,
941, L36, publisher: The American Astronomical Society
Laing, R. A., Riley, J. M., & Longair, M. S. 1983, Monthly Notices of the Royal
Astronomical Society, 204, 151, aDS Bibcode: 1983MNRAS.204..151L
Lanz, L., Ogle, P. M., Alatalo, K., & Appleton, P. N. 2016, The Astrophysical
Journal, 826, 29, aDS Bibcode: 2016ApJ...826...29L
Larson, R. B. 1981, Monthly Notices of the Royal Astronomical Society, 194,
809, aDS Bibcode: 1981MNRAS.194..809L
Law, D. R., E. Morrison, J., Argyriou, I., et al. 2023, The Astronomical Journal,
166, 45, aDS Bibcode: 2023AJ....166...45L
Levesque, E. M. & Richardson, M. L. A. 2014, The Astrophysical Journal, 780,
100, aDS Bibcode: 2014ApJ...780..100L
Mandal, A., Mukherjee, D., Federrath, C., et al. 2021, Monthly Notices
of the Royal Astronomical Society, 508, 4738, aDS Bibcode: 2021MNRAS.508.4738M
Mayya, Y. D., Alzate, J. A., Lomelí-Núez, L., et al. 2023, Monthly Notices
of the Royal Astronomical Society, 521, 5492, aDS Bibcode: 2023MNRAS.521.5492M
Mazzalay, X., Saglia, R. P., Erwin, P., et al. 2013, Monthly Notices of the Royal
Astronomical Society, 428, 2389, aDS Bibcode: 2013MNRAS.428.2389M
McKee, C. F. & Ostriker, E. C. 2007, Annual Review of Astronomy and Astrophysics, 45, 565, aDS Bibcode: 2007ARA&A..45..565M
Medling, A. M., Kewley, L. J., Calzetti, D., et al. 2021, The Astrophysical Journal, 923, 160, aDS Bibcode: 2021ApJ...923..160M
Meenakshi, M., Mukherjee, D., Wagner, A. Y., et al. 2022, Monthly Notices of the Royal Astronomical Society, 516, 766, aDS Bibcode: 2022MNRAS.516..766M
Meijerink, R., Kristensen, L. E., Weiß, A., et al. 2013, The Astrophysical Journal,
762, L16, aDS Bibcode: 2013ApJ...762L..16M
Merloni, A. & Heinz, S. 2007, Monthly Notices of the Royal Astronomical Society, 381, 589, aDS Bibcode: 2007MNRAS.381..589M
Micelotta, E. R., Jones, A. P., & Tielens, A. G. G. M. 2010, Astronomy and
Astrophysics, 510, A36, aDS Bibcode: 2010A&A...510A..36M
Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018,
Monthly Notices of the Royal Astronomical Society, 479, 5544, aDS Bibcode: 2018MNRAS.479.5544M
Nesvadba, N. P. H., Boulanger, F., Lehnert, M. D., Guillard, P., & Salome, P. 2011, Astronomy and Astrophysics, 536, L5, aDS Bibcode:
2011A&A...536L...5N
Nesvadba, N. P. H., Boulanger, F., Salomé, P., et al. 2010, Astronomy and Astrophysics, 521, A65, aDS Bibcode: 2010A&A...521A..65N
Nesvadba, N. P. H., Wagner, A. Y., Mukherjee, D., et al. 2021, Astronomy and
Astrophysics, 654, A8, aDS Bibcode: 2021A&A...654A...8N
Ogle, P., Antonucci, R., Appleton, P. N., & Whysong, D. 2007, The Astrophysical Journal, 668, 699, aDS Bibcode: 2007ApJ...668..699O
Ogle, P., Boulanger, F., Guillard, P., et al. 2010, The Astrophysical Journal, 724,
1193, aDS Bibcode: 2010ApJ...724.1193O
Padoan, P. & Nordlund, A. 2011, The Astrophysical Journal, 730, 40, aDS Bibcode: 2011ApJ...730...40P
Pereira-Santaella, M., Álvarez Márquez, J., García-Bernete, I., et al. 2022, Astronomy and Astrophysics, 665, L11, aDS Bibcode: 2022A&A...665L..11P
Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, Astronomy and
Astrophysics, 594, A13, aDS Bibcode: 2016A&A...594A..13P


Article number, page 21 of 22

_A&A proofs:_ manuscript no. aanda



Puxley, P. J., Hawarden, T. G., & Mountain, C. M. 1990, The Astrophysical
Journal, 364, 77, aDS Bibcode: 1990ApJ...364...77P
Rawlings, S., Saunders, R., Miller, P., Jones, M. E., & Eales, S. A. 1990, Monthly
Notices of the Royal Astronomical Society, 246, 21P, aDS Bibcode: 1990MNRAS.246P..21R
Rodríguez-Ardila, A., Pastoriza, M. G., Viegas, S., Sigut, T. A. A., & Pradhan, A. K. 2004, Astronomy and Astrophysics, 425, 457, aDS Bibcode:
2004A&A...425..457R
Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, Astronomy and Astrophysics, 563, A31, aDS Bibcode: 2014A&A...563A..31R
Sage, L. J., Welch, G. A., & Young, L. M. 2007, The Astrophysical Journal, 657,
232, aDS Bibcode: 2007ApJ...657..232S
Saintonge, A., Lutz, D., Genzel, R., et al. 2013, The Astrophysical Journal, 778,
2, aDS Bibcode: 2013ApJ...778....2S
Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, Monthly Notices of the Royal
Astronomical Society, 446, 521, aDS Bibcode: 2015MNRAS.446..521S
Schmidt, M. 1968, The Astrophysical Journal, 151, 393
Scoville, N. Z., Hall, D. N. B., Ridgway, S. T., & Kleinmann, S. G. 1982, The
Astrophysical Journal, 253, 136, aDS Bibcode: 1982ApJ...253..136S
Silk, J. & Rees, M. J. 1998, Astronomy and Astrophysics, 331, L1, aDS Bibcode:
1998A&A...331L...1S
Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, The Astrophysical Journal, 478, 144, aDS Bibcode: 1997ApJ...478..144S
Spoon, H. W. W., Armus, L., Marshall, J. A., et al. 2009, The Astrophysical
Journal, 693, 1223, aDS Bibcode: 2009ApJ...693.1223S
Spoon, H. W. W. & Holt, J. 2009, The Astrophysical Journal, 702, L42, aDS
Bibcode: 2009ApJ...702L..42S
Springel, V., Di Matteo, T., & Hernquist, L. 2005, Monthly Notices of the Royal
Astronomical Society, 361, 776, aDS Bibcode: 2005MNRAS.361..776S
Stanley, F., Alexander, D. M., Harrison, C. M., et al. 2017, Monthly Notices
of the Royal Astronomical Society, 472, 2221, aDS Bibcode: 2017MNRAS.472.2221S
Sun, J., Leroy, A. K., Schruba, A., et al. 2018, The Astrophysical Journal, 860,
172, aDS Bibcode: 2018ApJ...860..172S
Veilleux, S., Cecil, G., Bland-Hawthorn, J., et al. 1994, The Astrophysical Journal, 433, 48, aDS Bibcode: 1994ApJ...433...48V
Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, The Astrophysical Journal,
776, 27, aDS Bibcode: 2013ApJ...776...27V
Villar Martín, M., Castro-Rodríguez, N., Pereira Santaella, M., et al. 2023, Astronomy and Astrophysics, 673, A25, aDS Bibcode: 2023A&A...673A..25V
Weinberger, R., Springel, V., Pakmor, R., et al. 2018, Monthly Notices
of the Royal Astronomical Society, 479, 4056, aDS Bibcode: 2018MNRAS.479.4056W
Werner, N. & Mernier, F. 2020, Hot Atmospheres of Galaxies, Groups, and
Clusters of Galaxies, pages: 279-310 Publication Title: Reviews in Frontiers
of Modern Astrophysics; From Space Debris to Cosmology ADS Bibcode:
2020rfma.book..279K
White, R. L., Becker, R. H., Helfand, D. J., & Gregg, M. D. 1997, The Astrophysical Journal, 475, 479, aDS Bibcode: 1997ApJ...475..479W
Willis, A. G. & Strom, R. G. 1978, Astronomy and Astrophysics, 62, 375, aDS
Bibcode: 1978A&A....62..375W
Winge, C., Riffel, R. A., & Storchi-Bergmann, T. 2009, The Astrophysical Journal Supplement Series, 185, 186, publisher: The American Astronomical Society
Yoon, Y., Park, C., Chung, H., & Zhang, K. 2021, The Astrophysical Journal,
922, 249, aDS Bibcode: 2021ApJ...922..249Y
Young, L. M., Bureau, M., Davis, T. A., et al. 2011, Monthly Notices of the Royal
Astronomical Society, 414, 940, aDS Bibcode: 2011MNRAS.414..940Y
Zovaro, H. R. M., Sharp, R., Nesvadba, N. P. H., et al. 2019, Monthly Notices of the Royal Astronomical Society, 484, 3393, aDS Bibcode: 2019MNRAS.484.3393Z
Álvarez Márquez, J., Labiano, A., Guillard, P., et al. 2023, Astronomy and Astrophysics, 672, A108, aDS Bibcode: 2023A&A...672A.108A


_Acknowledgements._ We would like to thank the staff at STScI, at the JVLA, and
at ALMA for their fantastic assistance with preparing the data taking, and with
carrying out the observations. JL, NPHN and DM acknowledge partial financial
support through CEFIPRA program 6504-2. This work was supported by the
French government through the National Research Agency (ANR) with funding
grant ANR AGN_MELBa (ANR-21-CE31-0011). This work is based in large
parts on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes
at the Space Telescope Science Institute, which is operated by the Association
of Universities for Research in Astronomy, Inc., under NASA contract NAS 503127 for JWST. These observations are associated with program #GO1-2162.
This work is partly based on data obtained with the Karl G. Jansky Very Large
Array (JVLA) of the National Radio Astronomy Observatory (NRAO) through
program ID 18A-285. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement


Article number, page 22 of 22



by Associated Universities, Inc. This paper makes use of the following ALMA
data: 2015.1.01120.S. ALMA is a partnership of ESO (representing its member
states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and
ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ.


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "RA=15:52:09.112, Dec=20:05:48.2",
  "failed_quote": "In this cosmology, the luminosity distance to 3C 326 N at z = 0.08979 is D L = 423.6 Mpc, and the angular size distance, D A = 356.8 Mpc."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "z = 0.08979 ± 0.0003 (D_L = 423.6 Mpc, D_A = 356.8 Mpc)",
  "failed_quote": "In this cosmology, the luminosity distance to 3C 326 N at z = 0.08979 is D L = 423.6 Mpc, and the angular size distance, D A = 356.8 Mpc."
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "CO band heads observed with JWST/NIRSpec and flat Planck Collaboration et al. (2016) cosmology",
  "failed_quote": "In this cosmology, the luminosity distance to 3C 326 N at z = 0.08979 is D L = 423.6 Mpc, and the angular size distance, D A = 356.8 Mpc."
 },
 {
  "path": "science.question.evidence[1]",
  "value": "How does AGN jet feedback affect the kinematics, heating, and star formation of warm molecular and ionised gas in the radio galaxy 3C 326 N, and can ro-vibrational H2 lines serve as a proxy for rotational H2 lines in turbulent environments?",
  "failed_quote": "We also investigate the potential of the ro-vibrational lines, that are produced by hot ∼ 1000 K gas which comprises only a small fraction of the total gas mass, as tracers of turbulence in place of pure rotational lines"
 },
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "Integral-field unit spectroscopy from 1.66 to 3.17 um (NIRSpec) and 6.53 to 27.9 um (MIRI MRS) from program GO1-2162",
  "failed_quote": "3C 326 N was observed with the integral-field units (IFUs) of the Near-Infrared Spectrograph (NIRSpec) and the Medium-Resolution Spectrograph (MRS) of the Mid-Infrared Instrument (MIRI) on the James-Webb Space Telescope as part of program GO1-2162 (PI Nesvadba)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Star-formation rate (0.087 +0.106/-0.046 M_sun yr^-1), X-ray luminosity (10^40.63 erg s^-1), and dust mass (6.05 +0.376/-0.218 x 10^7 M_sun) from Herschel",
  "failed_quote": "3C 326 N has a very low star-formation rate (SFR= 0.087 [+] − [0] 0 [.] . [106] 046 [M] [⊙] [yr] [−][1] [from] [Herschel] [dust] photometry; Lanz et al. 2016), and a radiatively weak AGN ( L X = 10 [40][.][63] erg s [−][1] ; Lanz et al. 2016)"
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Two-component Gaussian MCMC fitting with BIC selection captures complex dual-component line profiles across the disk, and stellar CO band head fitting isolates systemic redshift without hydrodynamic wind contamination.",
  "failed_quote": "We find that the line shape is often complex and requires multiple Gaussians to explain."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "UV photons from young stars or cosmic rays as the heating mechanism for the H2 emission and Northern clumps (rejected based on low Pa-alpha/H2 ratios and H2 destruction limits).",
  "failed_quote": "The line ratios however, suggest that they are not heated by UV photons from young stars, but from shocks like the ambient gas, otherwise Paα should be an order of magnitude brighter compared to the S(3) line than what is observed."
 }
]
```
