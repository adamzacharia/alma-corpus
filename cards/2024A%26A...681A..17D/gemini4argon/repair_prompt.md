# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...681A..17D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. RSGC1_final ©ESO 2023
November 14, 2023

## **ALMA detection of CO rotational line emission in red** **supergiant stars of the massive young star cluster RSGC1**

### **Determination of a new mass-loss rate prescription for red supergiants**


L. Decin [1], A.M.S. Richards [2], P. Marchant [1], and H. Sana [1]


1 Institute of Astronomy, KU Leuven, Celestijnenlaan 200D, 3001 Leuven, Belgium e-mail: Leen.Decin@kuleuven.be
2 JBCA, Department Physics and Astronomy, University of Manchester, Manchester M13 9PL, UK


Received date; accepted date


**ABSTRACT**


_Context._ The fate of stars largely depends on the amount of mass lost during the end stages of evolution. For single stars with an initial
mass between _∼_ 8–30 M _⊙_, most mass is lost during the red supergiant (RSG) phase, when stellar winds deplete the H-rich envelope.
However, the RSG mass-loss rate ( _M_ [˙] ) is poorly understood theoretically, and so stellar evolution models rely on empirically derived
mass-loss rate prescriptions. However, it has been shown that these empirical relations differ largely, with differences up to 2 orders
of magnitude.
_Aims._ We aim to derive a new mass-loss rate prescription for RSGs that is not afflicted with some uncertainties inherent in preceding
studies.
_Methods._ We have observed CO rotational line emission towards a sample of RSGs in the open cluster RSGC1 that all are of a similar
initial mass. The ALMA CO(2-1) line detections allowed us to retrieve the gas mass-loss rates ( _M_ [˙] CO ). In contrast to mass-loss rates
derived from the analysis of dust spectral features ( _M_ [˙] SED ), the data allowed us a direct determination of the wind velocity and no
uncertain dust-to-gas correction factor was needed. _Results._ Five RSGs in RSGC1 have been detected in CO(2-1). The retrieved _M_ ˙ CO values are systematically lower than _M_ ˙ SED .
Although only five RSGs in RSGC1 have been detected, the data allow us to propose a new mass-loss rate relation for M-type red
supergiants with effective temperatures between _∼_ 3200 – 3800 K that is dependent on the luminosity and initial mass, and that is valid
during the phase where nuclear burning determines the evolution along the RSG branch. The new mass-loss rate relation is based onthe _M_ ˙ -prescription yields a good prediction for the mass-loss rate of some well-known Galactic RSGs that are observed in multiple COnew _M_ ˙ CO values for the RSGs in RSGC1 and on prior _M_ ˙ SED values for RSGs in four clusters, including RSGC1. The new
rotational lines, including _α_ Ori, _µ_ Cep and VX Sgr. Moreover, there are indications that a stronger, potentially eruptive, mass-loss
process is occurring during some fraction of the RSG lifetime, suggesting that RSGs might experience a phase change in mass loss
leading to the wind mass-loss rate dominating the RSG evolution at that stage.
_Conclusions._ Implementing a lower mass-loss rate in evolution codes for massive stars has important consequences as to the nature
of their end-state. A reduction of the RSG mass-loss rate implies that quiescent RSG mass loss is not enough to strip a single star’s
hydrogen-rich envelope. Upon core collapse such single stars would explode as RSGs. Mass-loss rates of order _∼_ 6 times higher
would be needed to strip the H-rich envelope and produce a Wolf-Rayet star while evolving back to the blue side of the HertzsprungRussell diagram. Future observations of a larger sample of RSGs in open clusters should allow a more stringent determination of the _M_ ˙ CO -luminosity relation and a sharper diagnostic as to when the phase change in mass loss is occurring.


**Key words.** Stars: evolution, Stars: massive, Stars: mass-loss, Stars: supergiants, Galaxies: clusters: individual: RSGC1, Instrumentation: interferometers



**1.** **Introduction**


The evolution of massive stars up to the point of supernovae
(SNe) remains poorly understood. The steepness of the initial
mass function and their short lifetimes ( _∼_ 15 Myr) make such
stars rare, whilst the brevity of their post main-sequence (MS)
evolution makes the direct progenitors of SNe rarer still. The
pre-SN mass-loss behaviour is the key property that determines
the appearance of the SN, since it dictates the extent to which
the envelope is stripped prior to explosion. It also determines
the nature of the end-state, that is complete disruption, neutron
star, black hole, or total implosion with no supernova (e.g. Heger
et al. 2003).


_Send offprint requests to_ : Leen.Decin@kuleuven.be



The most common of the core-collapse SNe are of type IIP,
which are observed to have red supergiants (RSGs) as their direct progenitors. Smartt (2009) noted that the range of initial
masses of these SN progenitors inferred from pre-explosion photometry, 8 _≤M_ /M _⊙_ _≤_ 17, is at odds with conventional theory,
which predicts that the upper mass limit should be closer to
_∼_ 30 M _⊙_ ; referred to as the ‘red supergiant problem’ (e.g. Ekström et al. 2012). A potential explanation for this discrepancy
is that the missing RSGs (i.e. those with an initial mass between
17 – 30 M _⊙_ ) collapse to form black holes with no observable
SNe. Later on, Davies & Beasor (2020) cautioned that this observational cutoff (of 17 M _⊙_ ) is more likely to be higher and is
fraught with large uncertainties (19 _−_ [+4] 2 [M] _[⊙]_ [) and that also the up-]
per mass limit from theoretical models should be shifted down

Article number, page 1 of 29

_A&A proofs:_ manuscript no. RSGC1_final



wards to _∼_ 25 – 27 M _⊙_ . One of the main uncertainties in both the
data analysis and stellar evolution predictions is our relatively
poor knowledge of RSG mass-loss rates.
Mass loss during the RSG phase can affect the progenitors
of SNe in two ways. Firstly, increased mass loss can strip the
star of a substantial fraction of the envelope, causing the star to
evolve back to the blue before SN (Georgy 2012), and possibly
depleting the stellar envelope of hydrogen (hence changing what
would have been a Type-II SN into a Type-I SN). Secondly, the
mass ejected can enshroud the star in dust, increasing the visual
extinction by several magnitudes (e.g. de Wit et al. 2008; Beasor
& Davies 2018), and causing the observer to underestimate the
pre-SN luminosity of the star, or perhaps preventing the progenitor from being detectable at all (Walmswell & Eldridge 2012).
Hence, accurate knowledge of RSG mass-loss rates is crucial to
our understanding of stellar evolution and SN progenitors.
Despite this, the mass-loss rates ( _M_ [˙] ) of RSGs are relatively
poorly known, in comparison to the winds of hot massive stars
which have been studied extensively (e.g. Sundqvist et al. 2011;
Hawcroft et al. 2021; Rubio-Díez et al. 2022). The mass-loss rate
recipes most often used in evolutionary models are those from de
Jager et al. (1988) and Nieuwenhuijzen & de Jager (1990), which
are somewhat antiquated as they are basically scaled up from red
giants, and which can only predict _M_ [˙] of field RSGs to within _±_ 1
dex (see Fig. 2 below). These recipes assume that _M_ [˙] scales with
mass, luminosity and temperature, but do not take into account
how _M_ [˙] may change as the opacity of the circumstellar material
builds up over time. What is required is a study of the mass-loss
rates of samples of RSGs with uniform initial abundances and
masses, where the evolutionary phase is the only variable.There are several established methods for measuring _M_ ˙ in
cool stars. Arguably the best is to monitor the spectrum of a
companion star as it passes behind the primary’s wind (e.g. Kudritzki & Reimers 1978), but unfortunately there are very few
such systems. Until recently, the only way to study large numbers of RSGs was to observe and model the infrared excess arising from the circumstellar dust (e.g. van Loon et al. 1999; Bonanos et al. 2010). However, most of the material is in molecular gas, and so a large ( _∼×_ 200–500), uncertain correction factor
must be applied to convert the measured dust mass-loss rate into
a gas mass-loss rate (hereafter referred to as _M_ [˙] SED ), while there
is(requiredno informationto get _M_ ˙on). theAlternatively,outflow speedOHormasersradialcandensitybe usedprofileto
measure the gas wind speed. The modelling of the spectral energy distribution (SED) for an assumed gas-to-dust ratio yields a
predicted wind speed that can be compared to the observed one.
The scaling of the SED models to account for the difference between expected and measured expansion velocity, then yields the
gas-to-dust ratios and mass-loss rates of the sample under study
(see, e.g., Goldman et al. 2017). A much better way is to observe
the gas using CO molecular line transitions to derive the expansion velocity and gas mass-loss rate directly from the CO line
profiles — hereafter referred to as _M_ [˙] CO (e.g., Knapp & Morris
1985; Loup et al. 1993; Josselin et al. 1998; Decin et al. 2006;
Ramstedt et al. 2008; Danilovich et al. 2015). The faintness of
these lines has meant that, until now, such observations were
only possible for nearby bright RSGs. One exception for the detection of CO from an extragalactic RSG is IRAS 05280 _−_ 6910
situated in the Large Magellanic Cloud, but the spectral resolution of the data acquired with the _Herschel_ _Space_ _Observa-_
_tory_ did not allow the expansion velocity to be measured (Matsuura et al. 2016). Now, with the immense gain in sensitivity
provided by the Atacama Large Millimeter/submillimeter Array


Article number, page 2 of 29



(ALMA), we can directly measure the expansion velocity and
gas mass-loss rates of homogeneous samples of RSGs with wellconstrained distance and stellar parameters.
With this study, we aim to provide the first measurements of
the gas mass-loss rates ( _M_ [˙] CO ) of RSGs as a function of the specific RSG age. To do this, we have identified a sample of RSGs
which have roughly the same masses and identical initial chemical compositions. Such samples are uniquely found in star clusters. The cluster RSGC1 at a distance, _d_, of _∼_ 6 600 pc contains
14 RSGs and one post-RSG, all with initial masses _∼_ 25 M _⊙_
(Davies et al. 2008; Beasor et al. 2020). The cluster is effectively
coeval, since even a large cluster age spread (0.5 Myr) would
be short compared to the cluster age of 12 Myr (Davies et al.
2008). This means that the range of initial masses of the RSGs
in RSGC1 must be narrow, and since all stars with this initial
mass must follow virtually the same evolutionary track on the
Hertzsprung-Russell (HR) diagram, the differences in the stars’
luminosities are entirely due to how evolved they are. By measuring the mass-loss rates of these stars, we will be able to determine not only accurate mass-loss rates for a sample of RSGs, but
also how mass-loss behaviour changes as the star evolves. In a
next step, using these measurements in conjunction with model
estimates of the RSG lifetimes, one can then integrate over all
stars in the cluster to find the total mass lost during the RSG
phase, a key property when estimating the fate of a star and the
type of SN it will produce.


**2.** **Observations and data reduction**


The 14 RSGs (F01–F14) and 1 post-RSG (F15) in RSGC1 (see
Table 2 in Davies et al. 2008) were observed with ALMA on
2015 June 9 and 11 for proposal code 2013.1.01200.S. We requested observations at both band 9, centred on the CO v=0
J=6-5 rotational line transition and band 6, centred on the CO
v=0 J=2-1 rotational line transition, but only the latter were
obtained. Positions and other details are given in Table A.1.
The observations have three spectral windows (spw); one ‘line’
spw with a width of 1.875 GHz and 3840 channels to cover the
CO(2-1) transition, and two ‘continuum’ 2 GHz spw with 128
channels each centred at 228.5 GHz and 213 GHz. The recorded
line channels are not independent and the minimum effective
spectral resolution of 0.977 MHz is approximately double the
channel width. The spectral resolution of the continuum data is
15.625 MHz. 36 antennas were used with minimum and maximum baselines of 63–783 m, providing a maximum recoverable
scale of _∼_ 4 _[′′]_ _._ 4 in a field-of-view of 26 _[′′]_ . The total integration per
target source was 4.8 min. Standard ALMA Cycle 2 observing
and quality control procedures were used [1] . The flux scale was
set relative to Titan (excluding its atmospheric lines). Compact
quasars J1733-1304 and J1832-1035 were used for bandpass calibration and phase-referencing, respectively.
The data were calibrated using the ALMA Quality Assurance scripts implemented in CASA (the Common Software Applications package) (McMullin et al. 2007). The estimated accuracy of the flux scale as applied to the targets is _∼_ 7%. The targetphase-reference separation is _∼_ 3.7 _[◦]_ (depending on target). Inspection of the (small) slopes in the phase-reference phase solutions, along with the probable antenna position uncertainties in
2015 (Hunter et al. 2016), suggests an absolute astrometric accuracy ≳ 1 _/_ 16 of the synthesised beam, depending on the target
signal to noise ratio (S/N).


1 https://almascience.eso.org/documents-and-tools/cycle-2/cycle-2

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Fig. 1.** CO(2-1) line profiles of 5 red supergiants in RSGC1. The ALMA data are plotted as red histograms. Synthetic line profiles (see Sect. 3) are
overplotted as black solid lines. The grey dashed regions indicate frequency regions that are contaminated by the ISM, a strong noise background,
or other genuine emission (see App. A). The vertical dashed blue lines indicate the local standard of rest velocity, _v_ LSR, as deduced from the ALMA
CO data (see App. A). The dotted and dashed-dotted blue lines indicate the _v_ LSR value as determined by Davies et al. (2008) and Nakashima &
Deguchi (2006), respectively (see Table A.1). The noise in the spectrum is 1.2 – 1.4 mJy (see text for derivation) and is shown as (red) error bar in
each panel. The dotted black line in the upper left panel is an alternative fit to the CO(2-1) line profile of F01, as discussed in App. C.



We inspected the continuum spw for each target and excluded several channels covering the SiO v=3 J=5-4 line seen
around 212.582 GHz for some sources. We imaged each target,
achieving a noise from the full 1.7 GHz range of _σ_ rms _∼_ 0.05 mJy.
The synthesised beam in all images is about (0 _[′′]_ _._ 49 _×_ 0 _[′′]_ _._ 37) at
position angle _∼_ –65 _[◦]_, depending on the frequency. Table A.1
shows that the continuum peaks are less than half the rms in
a 3 km s _[−]_ [1] spectral channel, so we did not perform continuum subtraction. Image cubes were made for the spw covering the CO(2-1) line for each source at 3 km s _[−]_ [1] velocity resolution (approximately 4 input channels), adjusted to constant
velocity in the Local Standard of Rest frame ( _v_ LSR ) with respect to the CO(2-1) rest frequency of 230.538 GHz. We obtained _σ_ rms _∼_ 1.9 mJy. We also made images at 1.3 and 10 km s _[−]_ [1]
resolution but these do not reveal any more detections or significant details. We imaged the SiO v=3 J=5-4 line which, where
detected, covered 2–4 continuum channels (width _∼_ 22km s _[−]_ [1] ).
In these low spectral resolution continuum spw the per-channel
_σ_ rms is _∼_ 0.6 mJy and no other lines were detected. The parameters for all detections are given in App. A–App. C.


For five RSGs (F01, F02, F03, F04, and F13), the CO(21) line emission was detected, with a spatial extent _[<]_ _∼_ 1 _[′′]_ (see
App. C). These are the first detections of spectrally and spatially
resolved CO rotational line emission of sources in an open cluster, in this particular case CO emission arising from the stellar
wind of red supergiants located in RSGC1. For each of those
five RSGs, the CO(2-1) line profile was extracted for a circular
aperture of 0 _[′′]_ _._ 75 centred on the peak of the continuum emission.
Fig. 1 shows the observed line profiles. The noise in the spectrum



(clear of ISM contamination) is given by the _σ_ rms values from
Table A.1 divided by the square root of the number of beams,
resulting in a spectral noise of _∼_ 1.2 – 1.4 mJy. As visible both in
the CO(2-1) channel maps (Fig. C.3–Fig. C.7) and line profiles,
there is contamination by interstellar medium (ISM) emission at
specific frequencies; see the dashed regions in Fig. 1. In general, there is much less (or no) ISM contamination visible on the
high velocity side, although there might be a noise background.
Therefore, the red part of the line profile can also be used to assess the ISM contamination at lower velocities, since the CO line
profiles are expected to be symmetric [2] . For each source, the ISM
contamination and alternative fits are discussed in App. C.
We made total intensity (zeroth moment) maps for each CO
line over the uncontaminated channels. The rms-noise in the total intensity maps ranges between 21 – 29 mJy/beam km/s, with
corresponding peak signal-to-noise ratio between _∼_ 12 – 34 (see
Sect. C). We measured the azimuthally averaged flux in annuli
200-mas thick, taking the minimum of the rms or the median average deviation as the error (see Decin et al. 2018, see Fig. C.2).
These gave flux distributions with full width half maximum sizes
of 460, 400, 480, 600 and 460 mas for F01, F02, F03, F04, F13,
respectively, uncertainty being _∼_ 50 mas. This gives an indication of the relative sizes of the brightest _∼_ 60% of the emission,
rather than the true size, since the flux distribution is not necessarily Gaussian and may be irregular. It is more challenging to
estimate the total size of the CO emission, since our observations


2 The blue side of the line profile can be of slightly lower intensity
when the source function around optical depth _τ_ _ν_ _∼_ 1 probes more outer
regions of the CSE.


Article number, page 3 of 29

_A&A proofs:_ manuscript no. RSGC1_final



are sensitivity-limited and provide a lower limit. We estimated
where 3 _×_ the rms noise (3 _×_ 25 mJy beam _[−]_ [1] km s _[−]_ [1] ) intersected
the azimuthal average profiles. This gave diameters of 700, 530,
770, 650 and 900 mas for F01, F02, F03, F04, F13, respectively
but the position uncertainty is proportional to the phase noise,

_∼_
140 mas at S/N = 3, and the weaker sources, in particular, may
be more extended.


**3.** **Analysis and results**


The five sources detected in CO(2-1) include (i) the three M-type
RSGs with the highest _M_ [˙] SED amongst the sample of red supergiants in RSGC1 analysed by Beasor et al. (2020) (F01, F02, andF03; with _M_ ˙ SED _>∼_ 4 _×_ 10 _[−]_ [6] M _⊙_ /yr); and (ii) the peculiar RSG
F13, which is anomalously red compared to the other RSGs in
the cluster (Davies et al. 2008), and for which the true luminosity
is difficult to determine (Beasor et al. 2020). Ten sources (F05,
F06, F07, F08, F09, F10, F11, F12, F14, F15) remain undetected at a CO(2-1) rms noise value of _∼_ 1.7 mJy/beam. For five
of those sources, Beasor et al. (2020) derived a mass-loss rate
between 1.8 _×_ 10 _[−]_ [7] _≤M_ [˙] SED _≤_ 8.7 _×_ 10 _[−]_ [7] M _⊙_ /yr, implying that
a line sensitivity of at least a factor 5–20 better is required to detect those sources with a similar ALMA setup. The Beasor et al. _M_ ˙ estimates were not yet available at the moment these observations were proposed and a general value of 1 _×_ 10 _[−]_ [6] M _⊙_ /yr was
used for calculating the line sensitivities in the proposal. Moreover, the CO outer envelope radius was then estimated based on
Mamon et al. (1988). However, both the _M_ [˙] -estimate (for the undetected sources) and the CO outer envelope radius (for the detected sources) turned out to be smaller (see Sect. 3.1), implying
an overestimate of the actual CO(2-1) line strength.
For the five sources for which CO(2-1) rotational emission
was detected, we derive the properties of the red supergiant’s
wind from a radiative transfer analysis. The outcomes, in particular the wind mass-loss rates, _M_ [˙] CO, are then compared to (literature) parameters retrieved from an analysis of the dust spectral
features visible in the SED, _M_ [˙] SED .


_3.1._ _Radiative transfer analysis of the CO(2-1) emission_


To retrieve the stellar wind parameters from the CO(2-1) line
profiles, we used the non-local thermodynamic equilibrium
(non-LTE) radiative transfer code GASTR O NO O M (Decin
et al. 2006) based on a multi-level approximate Newton-Raphson
(ANR) operator. The molecular line data are as specified in Appendix A of Decin et al. (2010). When ray-tracing the modelled
circumstellar envelope (CSE), we used a circular model beam
with the same extraction aperture (of 0 _[′′]_ _._ 75 diameter) to allow
direct comparisons. The modelled CSEs were divided into 150
shells, evenly spaced on a logarithmic scale from the stellar radius (R _⋆_ ) out to the outer envelope radius.
The effective temperatures, _T_ eff, and stellar luminosities,
_L_ bol, were taken from Davies et al. (2008); see Table 1 [3] . This
translates into stellar radii of _∼_ 1100 – 1500 R _⊙_ (see Table 1).
Since we only have one rotational CO line, we cannot put constraints on the radial distribution of the kinetic temperature for
the individual sources. We therefore assume that the gas kinetic
temperature follows a power-law radial profile



with _ϵ_ = 0 _._ 6, since such a power law has been shown to be a
good representation of the kinetic temperature in circumstellar
envelopes (Decin et al. 2006, and references therein).
For each of the five detected sources, the radial extent of
the CO emission zone is larger than the beam size (of _∼_ 0 _[′′]_ _._ 5),
but slightly lower than 1 _[′′]_ in diameter (see Fig. C.1). Given
a distance of 6 600 pc to RSGC1 and stellar radii between
7.55 _×_ 10 [13] – 1.04 _×_ 10 [14] cm, this translates into a CO envelope
radius of 250 _< R_ out < 650 R _⋆_ . While the spectra of F01 and F13
are not spatially resolved for an extraction aperture of 0 _[′′]_ _._ 75, the
spectra of F03 and F04 show the clear absorption depth reminiscent of spatially resolving the CSE. This is in line with the
angular sizes estimated from the zeroth moment maps which imply that F03 and F04 have the largest angular extents (Sect. 2).
These considerations yield a CO envelope radius of _∼_ 350 R _⋆_ for
F01 and F13, of _∼_ 400 R _⋆_ for F02, and of _∼_ 600 R _⋆_ for F03 and
F04. Those values are smaller by a factor of _∼_ 1.5 – 2 compared
to the value used for the proposal preparation, that was based on
the _r_ 1 _/_ 2 -value — which marks the radius where the CO abundance drops to half of its initial value — of Mamon et al. (1988)
for a wind mass-loss rate of 1 _×_ 10 _[−]_ [6] M _⊙_ /yr.
To calculate the CO excitation and hence level populations,
we account for excitation by the stellar photons, the microwave
background and the dust radiation field (Decin et al. 2006). For
the latter, we assume silicates (Decin et al. 2006) that start condensing at a temperature of _∼_ 1750 K, which translates into a dust
condensation radius, _R_ dust, of 3–4 R _⋆_ . To get the local mean radiation field at each radial point in the grid, we calculate the dust
radiation field for a canonical gas-to-dust ratio ( _r_ gd ) of 200, representative for a Milky Way cluster (Beasor et al. 2020). As we
discuss in App. D, the specific dust-to-gas ratio has only a minimal effect on the CO excitation by the dust radiation field for
these simulations.

The parametrised _β_ -type accelerating wind is described by



_β_
_._ (2)
�



_v_ gas ( _r_ ) _≃_ _v_ _∞_



1 _−_ _[R]_ [0]
� _r_



The terminal wind velocity, _v_ _∞_, is deduced from the ALMA
CO(2-1) line profiles (see Table 1), uncertainty being _±_ 3 km s _[−]_ [1]
(see App. A). As boundary for the velocity structure, we assume
that the flow velocity of the gas is equal to the local sound velocity, _v_ _s_, at _R_ 0 = _R_ dust . For the region between R _⋆_ and _R_ dust,
_β_ is assumed to be 1/2 (Decin et al. 2006); for the region beyond _R_ dust we follow the general conclusions from Khouri et al.
(2014), Decin et al. (2020), and Gottlieb et al. (2022) that the
value of _β_ should be larger to represent the slowly accelerating
flow in oxygen-rich winds. We here adopt _β_ = 3. We also include
a constant turbulent velocity _v_ turb of 3 km s _[−]_ [1] .
To determine the fractional abundance of CO with regard to
hydrogen, we assume all photospheric carbon to be locked in
CO in the circumstellar envelope (CSE). For a value of _A_ (C) =
log(C _/_ H) + 12 as derived by Davies et al. (2009) for RSGC1,
this yields a CO fractional abundance of 8.9 _×_ 10 _[−]_ [5] .
This set of stellar and circumstellar parameters allows us to
retrieve the mass-loss rate, _M_ [˙] CO, from the ALMA CO(2-1) line
profiles for each of the five detected sources; the derived values
are listed in Table 1, and range between 1.8–42 _×_ 10 _[−]_ [6] M _⊙_ /yr.
The evolution of the four sources with mass-loss rate below
_∼_ 4 _×_ 10 _[−]_ [6] M _⊙_ /yr (F01, F02, F03, and F04) is dominated by nuclear burning, while in the case of F13 the wind mass-loss rate
is currently determining its RSG evolution (see Fig. 2). For the
RSGC1 red supergiants that remained undetected in the CO(2-1)



_ϵ_

(1)
�



_T_ gas ( _r_ ) = _T_ eff



R _⋆_
� _r_



3 We note that those values are slightly different than the ones used in
Beasor & Davies (2016, 2018); Beasor et al. (2020).


Article number, page 4 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Table 1.** Stellar and CSE parameters for the five RSGs in RSGC1 for which CO(2-1) emission was detected.

|Col1|Stellarparameters|CSEparameters|Col4|
|---|---|---|---|
|Star|log(_L_bol_/L⊙_)(_a,e_)<br>_T_ef (_a_)<br>Spectral(_a_) R_⋆_(_a_) _v_LSR(_b_) <br>[K]<br>type<br>[R_⊙_] [km s_−_1]|_R_dust<br>_v∞_(_b_)<br>˙_M_ CO(_b_)<br>˙_M_ SED(_c_)<br> [R_⋆_] [km s_−_1] [10_−_6 M_⊙_/yr] [10_−_6 M_⊙_/yr]|˙_M_ CO_/v∞_<br>˙_M_ SED/25|
|F01<br>F02<br>F03<br>F04<br>F13|5.42+0_._12<br>_−_0_._13<br>3450_±_127<br>M5<br>1450<br>117.5<br>5.56+0_._12<br>_−_0_._13<br>3660_±_127<br>M2<br>1500<br>120.5<br>5.24+0_._12<br>_−_0_._13<br>3450_±_127<br>M5<br>1200<br>123.5<br>5.32+0_._11<br>_−_0_._13<br>3752_±_117<br>M1<br>1100<br>123.5<br>5.45+0_._12<br>_−_0_._13<br>3590_±_45<br>M3(_d_)<br>1430<br>123.5|3<br>8<br>2.0(_e_)<br>5.57+2_._37<br>_−_2_._17<br>3<br>10<br>1.8<br>5.18+2_._72<br>_−_1_._75<br>3<br>13<br>3.2(_e_)<br>4.18+3_._08<br>_−_0_._84<br>3<br>15<br>4.0<br>_−_<br>4<br>22<br>42<br>_−_|0.25<br>0.22<br>0.18<br>0.20<br>0.25<br>0.17<br>0.27<br>_−_<br>1.9<br>_−_|



**Notes.** Listed are the stellar luminosity _L_ bol, the effective temperature _T_ eff, the spectral type, the stellar radius R _⋆_, the local standard of rest
velocityfrom the _v_ CO(2-1) LSR (see discussion in App. A), the dust condensation radiusline, _M_ ˙ CO, and as deduced from an SED analysis by _R_ dust Beasor, the terminal wind velocityet al. (2020), _M_ ˙ SED . The _v_ _∞_ last, and the mass-loss rate as deducedtwo columns compare a density
measure, _M_ [˙] / _v_ _∞_, based on the values deduced in this study (column 11) and used in Beasor et al. (2020) who assumed a terminal wind velocity of
( 25 km s _a_ ) From _[−]_ Davies [1] (column 12).et al. (2008). ( _b_ ) As deduced from the ALMA CO(2-1) lines. The uncertainties on _M_ ˙ CO are discussed in App. C – D. ( _c_ ) From
Beasor et al. (2020). [(] _[d]_ [)] F13 was classified as K2 by Davies et al. (2008). However, later on it became clear that the CO-spectral type correlation
is flawed if a star has a strong stellar wind, and that under these circumstances also the spectral-type – _T_ eff relation from Levesque et al. (2006)
does not hold. We therefore use the effective temperature and spectral type classification from Messineo et al. (2021). [(] _[e]_ [)] Beasor et al. (2020) have
updated the luminosities of the RSGC1 sources published by Davies et al. (2008). In particular, Beasor et al. (2020) derived log _L_ bol (F01) = 5.58
and log _L_ bol (F03) = 5.33. Changing the luminosities to the values from Beasor et al. (2020) induces an increase in _M_ [˙] CO of 10% for F01 and of
3% for F03.


**Fig. 2.** Mass-loss rate as a function of luminosity. Various mass-loss rate relations derived for red supergiants are shown for a fixed stellar mass of
10 M _⊙_ (left panel) and of 25 M _⊙_ (right panel) for an assumed effective temperature of 3450 K (Reimers 1975; de Jager et al. 1988; Nieuwenhuijzen
& de Jager 1990; Salasnich et al. 1999; van Loon et al. 2005; Beasor et al. 2020; Goldman et al. 2017; Kee et al. 2021). Empirical mass-loss rate
relations are displayed with a solid line, the theoretical relation of Kee et al. (2021) is shown with a dashed line for 2 different values of the
atmospheric turbulent velocity _v_ turb [atm] [. For the empirical relation of Goldman et al. (2017), we use the RSG period-luminosity relation as given in]
Eq.data(C.17)of Beasorof Deet Beckal. (seeet Eq.al. (2010),(6)) is shownwhich isasvaliddottedforgreypulsationline; theperiodsnew _M_ between˙ CO -relation _∼_ 300 – 800deriveddays.fromThethe correctedALMA CO(2-1) _M_ [˙] SED -relationmeasurementsbased onof thethe
M-type RSG winds in RSGC1 (Eq. (8)) is shown as full red line. The rate at which hydrogen and helium are consumed by nuclear burning are
shown as thick dashed-triple dotted lines; the single-scattering radiation pressure limit for an expansion velocity of 12 km s _[−]_ [1] is shown as dashed
dark grey line. Stellar mass loss rules the evolution of RSG stars if the wind mass-loss rate exceeds the nuclear burning rate, as indicated by the
light-blue region; the nuclear-burning dominated region is indicated by the light-orange region. The red triangles in the right panel indicate the (L, _M_ ˙ )-values as derived in Sect. 3.1 from the ALMA CO(2-1) line profiles of F01, F02, F03, F04, and F13.



line, an upper limit on the mass-loss rate of _∼_ 7 _×_ 10 _[−]_ [7] M _⊙_ /yr is
derived.
in _M_ Given˙ CO arisesthis setfromof uncertaintiesinput parameters,in thetheterminallargestwinduncertaintyvelocity ( _∼_ 35%), and then in the distance, the outer CO envelope
size, and the CO fractional abundance (each _∼_ 20%); for additional details, readers can refer to App. D. The combined effectof the errors in the individual input parameters on _M_ ˙ CO is a
factorThis error _∼_ 1.4;onfor _M_ ˙ CO additionalis lowerdetails,than thereaderserrorscanonrefer _M_ ˙ SED to;App.see Ta-D.
ble 1. Measurements of dust emission are usually angularly unresolved, hence rely on SEDs, and depend on more factors known



to vary such as composition and size of grains, the stellar contribution to the SED, etc. for which reason estimates of the dustto-gas ratio can differ by an order of magnitude.


We note that terminal wind velocities determined solely from
the half line width at zero intensity might be lower limits since
it was shown by Decin et al. (2018) that line widths are sensitivity limited, and hence that in some cases higher signal-to-noisedata could indicate higher _v_ _∞_ values, and hence higher _M_ ˙ CO
values. However, if the terminal velocity increases, so does the
width of the full line profile and of the width between the two
horns in spatially resolved, optically thin line profiles. We therefore have used all these characteristics together to determine _v_ _∞_ .


Article number, page 5 of 29

_A&A proofs:_ manuscript no. RSGC1_final


_̸_



An increase in terminal velocity by 3 km s _[−]_ [1], would induce an
increase in _M_ [˙] CO by _∼_ 40% (see Table D.1).
The ALMA data also constrain the CO outer envelope radius (see Table 1). In recent studies, Groenewegen (2017) and
Saberi et al. (2019) improved the calculations on CO photodissociation in circumstellar envelopes made by Mamon et al. (1988).
Using the ratio of the maximum flux density over 3 times the
noise as a proxy for the fractional abundance of _f_ 0 _/f_ CO ( _r_ )
(with _f_ 0 being the initial CO abundance), we can use Eq. (3)
of Saberi et al. (2019) and their values for _r_ 1 _/_ 2 and _α_ (their Table B.1.) to compare the theoretical predicted CO envelope size
with the ALMA observations. The observed ALMA CO envelope radius of the four RSGC1 sources F01, F02, F03, and F04 is
only lower by a factor _∼_ 1.1 – 1.8 compared to what Saberi et al.
(2019) predicted, which is a remarkable agreement given the fact
that the values for _r_ 1 _/_ 2 and _α_ were calculated for a standard
Draine (1978) interstellar radiation field (ISRF). The ISRF in the
massive young cluster RSGC1 might actually be higher given
the fact that newly formed stars affect the surrounding materials strongly via their UV photons. However, unlike the case of
47 Tucanae (McDonald et al. 2015), an estimate of the strength
and local variation of the interstellar radiation field in RSGC1
is currently lacking. Groenewegen (2017) has shown that an increase in ISRF by a factor _∼_ 3 leads to a decrease in photodissociation radius by a factor _∼_ 1.5. The notable exception is F13
for which the predicted outer radius is almost an order of magnitude larger than the observed one. F13 stands also out in other
aspects; for further discussion, readers are referred to Sect. 4.


_3.2._ _Comparison to SED retrievals_


In various works, Beasor et al. have derived the mass-loss rate
for red supergiants in four open clusters, including RSGC1,
NGC 7410, _χ_ Per, and NGC 2100 (Beasor & Davies 2016, 2018;
Beasor et al. 2020). The first 3 clusters reside in the Milky Way,
while the latter one is an LMC cluster. For each of those clusters, the age and initial mass _M_ ini of the RSGs was determined.
This yielded values of 12 _±_ 2 Myr and 25 _±_ 2 M _⊙_ for RSGC1.
For the other 3 clusters, the respective values are 21 _±_ 1 Myr and
10 _±_ 1 M _⊙_ (NGC 2100), 20 _±_ 1 Myr and 11 _±_ 1 M _⊙_ (NGC 7419),
and 21 _±_ 1 Myr and 11 _±_ 1 M _⊙_ ( _χ_ Per). The aim of their works
was to derive a new mass-loss rate prescription for red supergiants(2020)thatderivedcan bea generalused in _M_ stellar˙ -luminosityevolutionrelationcodes.thatBeasoris depen-et al.
dent on the initial mass,


log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = ( _−_ 26 _._ 4 _−_ 0 _._ 23 _× M_ ini _/_ M _⊙_ )
+4 _._ 8 log( _L_ bol _/_ L _⊙_ ) _._ (3)


By keeping _M_ ini constrained, Beasor & Davies (2016, 2018)
showed that the _M_ [˙] -luminosity relation has a tighter correlation
with a smaller value for the dispersion. The standard deviation
for the slope is given to be 4.8 _±_ 0.6; the standard deviations
on the other numerical values were not listed by Beasor et al.
(2020), but have been determined in App. E. The slope of Eq. (3)
is steeper than any other mass-loss rate relations derived for red
supergiants (see Fig. 2). We here re-examine the results of Beasor et al. (2020) and compare the SED mass-loss rate to the ones
derived from the ALMA CO(2-1) line in the current work. ˙
In a first step, Beasor et al. (2020) has determined a _M_   luminosity relation for all clusters in their sample by fitting the
relation

_̸_

log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = _a_ + _b_ log( _L_ bol _/_ L _⊙_ ) (4)


Article number, page 6 of 29



to their data points (see Table E.1 and App. E). We repeat the
analysis applying the same IDL routine FITEXY [4] and using the
most conservative error estimates for both _L_ bol and _M_ [˙] SED (see
Table E.1). The fit to Eq. (4) is shown in Fig. 3; the values derived for _a_ and _b_ are listed in Table 2, together with the Pearson correlation coefficient. Similar to Beasor et al. (2020), the
standard deviation on the intercept _a_ and the slope _b_ is large
for the cluster RSGC1. For all clusters, our values for the intercept are systematically higher than the values listed in Table 4 of Beasor et al. (2020) (copied in Table E.2), and lower
for the slopes, although they agree within the 1-sigma uncertainties, the exception being NGC 2100. In particular, for RSGC1
we derive _a_ = _−_ 32.98 _±_ 18.43 and _b_ = 5.03 _±_ 3.44, as compared to
Beasor et al. (2020) who listed _a_ = _−_ 52.0 _±_ 51.2 and _b_ = 8.8 _±_ 9.5
(see left panel in Fig. E.1 and discussion in App. E) [5] .
The values of the slope _b_ obtained from each cluster are compatible with one another. This had led Beasor et al. (2020) to fix
_b_ to 4 _._ 8 _±_ 0 _._ 6 (corresponding to the weighted mean of the slope
obtained for each cluster) in order to decrease the number of
degrees of freedom of the fit from 8 to 5. We follow a similar
strategy to limit the number of degrees of freedom, however we
do not fix _b_ from the previous exercise. We rather fit a common
value of _b_ for all four clusters simultaneously with each individual intercepts ( _a_ _i_ ) using a multivariate linear fitting method implemented with the MPFIT Levenberg-Marquardt least-squares
solver (Markwardt 2009). Uncertainties were estimated through
Monte Carlo (MC) by generating 10 [4] statistically equivalent data
sets randomly drawn from normal distributions centred on the
best fit solutions and repeating the fit for each artificial data set.
The 68%-confidence interval on the best-fit parameters are given
by the 0.16 and 0.84 percentiles of the distributions of obtained
parameters. Fitted at face values, the errors on the individual intercepts _a_ _i_ are tightly correlated. To prevent this correlation, we
adopt a slightly different functional form:


log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = _a_ 1 + ∆ _a_ _i_ + _b_ log( _L_ bol _/_ L _⊙_ ) _,_ (5)


where _a_ 1 is the intercept for the cluster RSGC1, and ∆ _a_ _i_ indicates the difference in intercept of each cluster _i_ = 1,2,3,4 with
regard to the intercept _a_ 1 (hence, ∆ _a_ 1 = 0). That is, each cluster gets its own intercept ( _a_ _i_ = _a_ 1 + ∆ _a_ _i_ ) and the slope is
forced to be identical. The MC method yields _b_ = 3.34 [+0] _−_ 0 _[.]_ _._ [48] 41 [,]
_a_ 1 = _−_ 23.83 [+2] _−_ 2 _[.]_ _._ [15] 64 [with] [corresponding] [∆] _[a]_ _[i]_ [-values] [listed] [in] [the]
last column of Table 2; see right panel in Fig. 3 [6] . While mathematically equivalent to directly fitting the intercept _a_ _i_ instead
of their difference ∆ _a_ _i_ to a reference intercept (here arbitrarily
chosen to be that of RSGC1, but see App. F), the errors on _a_ 1,
∆ _a_ 2, ∆ _a_ 3, ∆ _a_ 4 are now uncorrelated, which allows for a better
sense of whether the intercepts from each cluster vary from one
another from a direct comparison of the ∆ _a_ _i_ values and their

errors.
To parametrise the mass-loss rate in terms of both the luminosity and the initial mass, we perform a MC fit to all four
clusters together using a parametrisation similar to Eq. 3, that is


log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = _R_ + _SM_ ini _/_ M _⊙_ + _b_ log( _L_ bol _/_ L _⊙_ ) _._


4 [https://idlastro.gsfc.nasa.gov/ftp/pro/math/](https://idlastro.gsfc.nasa.gov/ftp/pro/math/fitexy.pro)
[fitexy.pro](https://idlastro.gsfc.nasa.gov/ftp/pro/math/fitexy.pro)
5 We use 2 decimal points in errors to ensure accurate propagation of
uncertainties.

6
Using instead another cluster for determining _a_ _i_ yields similar results
for the value of _a_ _j_ = _a_ _i_ + ∆ _a_ _j_ (with _j_ = _̸_ _i_ ) for the 3 other remaining
clusters; for additional details, readers can refer to App. F.

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Fig. 3.** _M_ [˙] SED -luminosity relations for the four open clusters RSGC1, NGC 2100, NGC 7419, and _χ_ Per. The coloured open symbols represent the
(L bol, _M_ [˙] SED )-values for the four clusters studied by Beasor & Davies (2016) and Beasor et al. (2020); error bars indicate their most conservative
error estimates (see App. E). The dashed lines in the left panel show the individual fits to Eq. (4) where the values of both _a_ and _b_ are free
parameters in each fit. In the right panel, we force the slope _b_ to be identical for all clusters and fit Eq. (5). The best-fit values are listed in the
legend and in Table 2. The shaded areas provide a visualisation of the uncertainties of the fits. They were constructed through MC as the 68%-locus
of all best-fit relations derived from a fit to mock data sets used to assess the errors on the best-fit parameters.


**Table 2.** Best-fit parameters for the _M_ [˙] SED -luminosity relation for each cluster.

|Cluster|Pearsoncorrelation<br>coefficient|Intercept(a) Slope(b)<br>Eq (4) Eq (4)<br>. .|differenceinintercept(∆ai)<br>Eq (5)<br>.|
|---|---|---|---|
|RSGC1<br>NGC 2100<br>NGC 7419<br>_χ_ Per|0.82<br>0.85<br>0.99<br>0.82|_−_32.96_±_18.43<br>5.03_±_3.44<br>_−_20.15_±_3.13<br>3.04_±_0.64<br>_−_21.24_±_3.47<br>3.17_±_0.70<br>_−_23.49_±_4.20<br>3.68_±_0.86|0<br>2.31+0_._40<br>_−_0_._37<br>1.85+0_._40<br>_−_0_._38<br>1.98+0_._42<br>_−_0_._38|



**Notes.** The second column lists the linear Pearson correlation coefficient. The third and fourth column list, respectively, the intercept _a_ and slope
_b_ with their standard deviation derived by fitting Eq. (4) to the data. The fifth column lists the fit to Eq. 5 which yields a best-fit slope _b_ = 3.35 _−_ [+0] 0 _[.]_ _._ [43] 37
and intercept _a_ 1 = _−_ 23.96 [+2] _−_ 2 _[.]_ _._ [00] 32 [.]



(6)

The combined fit yields _R_ = _−_ 20.63 [+1] _−_ 2 _[.]_ _._ [93] 38 [,] _[S]_ [ =] _[ −]_ [0.16] [+0] _−_ 0 _[.]_ _._ [03] 04 [,] [and]
_b_ = 3.47 _−_ [+0] 0 _[.]_ _._ [57] 45 [. This new mass-loss rate relation has a higher con-]
stant _R_ and a shallower dependence on the initial mass and the
luminosity as compared to Beasor et al. (2020); see Eq. 3 and
Fig. 2 (full and dotted grey lines). Except for the mass-dependent
intercept, these values do not agree within their respective 1sigma uncertainties; see the standard deviations for the parameters of Eq. (3) derived in App. E.
However, the uncertainties associated with the intercept _R_
are substantial, spanning two orders of magnitude for the associated mass-loss rate. But it is crucial to acknowledge that these
uncertainties pertaining to the intercept do not reflect the uncertainties on the mass-loss rates within the range of values for
the initial mass and luminosities under study. By normalising
the mass-loss rate, initial mass and luminosities to representative values, the resulting parameter uncertainties become more
readily applicable (e.g. van Loon et al. 2005). This yields the



following analytical relation


log( _M_ [˙] SED _/_ 10 _[−]_ [5] M _⊙_ yr _[−]_ [1] ) = _R_ + _SM_ ini _/_ 10 M _⊙_
+ _b_ log( _L_ bol _/_ 10 [5] L _⊙_ ) _,_ (7)


with _R_ = 1.71 [+0] _−_ 0 _[.]_ _._ [54] 44 [,] _[S]_ [ =] _[ −]_ [1] _[.]_ [63] [+0] _−_ 0 _[.]_ _._ [30] 36 [,] [and] _[b]_ [ = 3.47] [+0] _−_ 0 _[.]_ _._ [57] 45 [;] [the] [un-]
certainties on the intercept now being of the order of 30%.


**4.** **Discussion**


_4.1._ _CO-based mass-loss relation for RSGs_


The CO gas mass-loss rate values of those red supergiants in
common with Beasor et al. (2020) are systematically lower, on
average by a factor of _∼_ 2 (see Table 1) — although we here must
provide the caveat of dealing with small number statistics. CO
mass-loss rates, _M_ [˙] CO, are not afflicted with uncertain dust extinction corrections, dust-to-gas conversion ratios, and unknown


Article number, page 7 of 29

_A&A proofs:_ manuscript no. RSGC1_final



expansion velocities as is the case for _M_ [˙] SED . The main reason
for the difference in _M_ [˙] SED and _M_ [˙] CO for the 3 RSGC1 sources
analysed in both this study and by Beasor et al. (2020) is the
expansion velocity which was assumed to be 25 _±_ 5 km s _[−]_ [1] by
Beasor et al. (2020), but which is lower for all RSGs in which
CO(2-1)as deducedwasfromdetected.the ALMACorrectingCO(2-1)for data,the terminal _M_ ˙ CO andvelocities _M_ ˙ SED
agree very well for the three sources in common to both studies
(F01, F02, and F03) with average difference being a factor _∼_ 0.9
and maximum percentage difference of 32% (see also last two
columns in Table 1).
A point of concern on the reliability of the mass-loss rates
could be binarity. The binary fraction of unevolved massive stars
is thought to be above 70% (Sana et al. 2012; Moe & Di Stefano 2017; Patrick et al. 2022). For a predicted merger fraction
of 20–30%, and a binary interaction fraction of 40–50%, the total RSG binary fraction is estimated around 20% (Patrick et al.
2019, 2020; Neugent et al. 2020; Sana 2022). As discussed by
Decin (2021) and Gottlieb et al. (2022), a binary system with
small orbital distance can develop an equatorial density enhancement (EDE) promoting the formation of dust grains. Hence, it is
expected that for those systems mass-loss rate estimates based
on _M_ ˙ -estimates,dust spectralandfeaturesthat mass-lossin the SEDrate estimatesmight yieldbasedtooonhigha CO-an
analysis should be preferred (Decin et al. 2019). The sensitivity
of the CO(2-1) integrated line flux to binary-induced morphologies has been shown to be less than a factor of _∼_ 2, for both spiral
structures (see Fig. 16 in Homan et al. 2015) and equatorial density enhancements (Decin et al. 2019), the latter morphologies
being much better traced in other molecular diagnostics, such as
the SiO v=0 J=8-7 transition (Kervella et al. 2016; Decin et al.
2020).
Despite of (i) the caveat of dealing with small-number statistics,RSGC1andthat(ii) havethe factthe thatlargestwe _M_ are˙ SED dealing-valueswithfromthethe3 RSGsstudy ofin
Beasor et al. (2020), we can try to improve on the mass-loss rate
prescription derived in Eq. (6). Similar to the analysis of Beasor
et al. (2020), we exclude F13 from the regression analysis since
it stands out in the sample of 14 RSGs in RSGC1: F13 is unusu-ally red, has an _M_ ˙ CO being an order of magnitude larger than
the other four RSGs detected in CO(2-1), and is the only source
for which the observed CO envelope size is much lower than any
prediction for CO photodissociation in a circumstellar envelope
(see Sect. 3.1). This tentatively suggests that another mass-loss
mechanism is active (see Sect. 4.2 and Sect. 4.3). The limited
and biased sample led us decide to fit both the ( _L_ bol, _M_ [˙] CO ) and
( _L_ bol, _M_ [˙] SED ) measurements together with a four parameter set
of equations:


log( _M_ [˙] SED _/_ 10 _[−]_ [5] M _⊙_ yr _[−]_ [1] ) = _R_ SED + _SM_ ini _/_ 10 M _⊙_
+ _b_ log( _L_ bol _/_ 10 [5] L _⊙_ )

log( _M_ [˙] CO _/_ 10 _[−]_ [5] M _⊙_ yr _[−]_ [1] ) = ( _R_ SED + ∆ _R_ )
+ _SM_ ini _/_ 10 M _⊙_
+ _b_ log( _L_ bol _/_ 10 [5] L _⊙_ ) _._ (8)

with _b_ = 3.50best-fit _−_ [+0] 0 _[.]_ _._ [60] 46 [,] values [and] [∆] _[R]_ being [ = 0.49] _R_ [+0] _−_ SED0 _[.]_ _._ [44] 41 = [;] 1 [see] _._ 77 [Fig.] [+0] _−_ 0 _[.]_ _._ [58] 46 [4.][,] [The] _[S]_ [ =] _[ −]_ _M_ ˙ [1] CO _[.]_ [68] [+0] _−_ mea- 0 _[.]_ _._ [31] 40 [,]
surements have an intercept that differs byto the _M_ ˙ SED measurements; the likelihood 0 _._ that5 _±_ 0such˙ _._ 4 compareda difference occurs by chance is only _∼_ 12%. This new _M_ -luminosity
relation derived for M-type supergiants is plotted as full red line


Article number, page 8 of 29



in Fig. 2, and is clearly different from the _M_ [˙] -relation derived by
Beasor et al. (2020) (full grey line in Fig. 2).


To assess the predictive power of Eq. (8), we have compared
its predicted _M_ [˙] -values with _M_ [˙] CO -values derived for some wellknown Galactic M-type supergiants towards which several rotational CO lines have been observed ( _α_ Ori, _µ_ Cep, VX Sgr, and
VY CMa; see App. G). The analysis presented in App. G proves
that Eq. (8) predicts the gas mass-loss rate for M-type red supergiants with effective temperature between _∼_ 3200 – 3800 K with
good accuracy, the average difference only being _∼_ 30% (see Table G.1).


Moreover, we can use the derived _M_ ˙ CO values to derive
the gas-to-dust ratio in the winds of individual sources. This ratio can be determined by comparing _M_ [˙] SED -values with _M_ [˙] CO values (adjusted for differences in wind speed and distance, as
used by different authors). Our analysis reveals a gas-to-dust ratio of 235 _±_ 71 for the RSGC1 sources. For the Galactic sources,
the gas-to-dust ratio ranges between _∼_ 200 – 550. The exception
is the extreme RSG VY CMa for which a low ratio of _∼_ 20
is derived, but there are indications that that ratio is changing
throughout its mass-loss history (see App. G).


Remarkably, the new _M_ ˙ CO values for the M-type red supergiants F01, F02, F03, and F04 are smaller than predicted by
all empirical mass-loss rate prescriptions derived prior to 2020
and used in stellar evolution codes (see right panel in Fig. 2).
Again here, (part of) the explanation is based on the fact that
all empirical _M_ [˙] -relations shown in Fig. 2 are based on an SED
analysis that are prone to uncertain gas-to-dust ratios and expansion velocities, and that samples of stars will be flawed by a large
fraction of stars that experience binary interaction. In addition,
those previous studies were often biased towards samples with
high mass-loss rate objects for which the infrared excess is easier to detect and model, as acknowledged by those authors; see,
for example, the discussion in van Loon et al. (2005). Moreover,
distances — and hence corresponding luminosities — are very
uncertain for Galactic samples. This latter caveat was avoided
in the studies by Beasor et al. who focused on open clusters,
which eventually led in 2020 to the RSG mass-loss prescription
given in Eq. (3) (Beasor et al. 2020) and shown as full grey line
in Fig. 2. The only theoretical mass-loss rate prescription for
RSGs is derived by Kee et al. (2021). That relation can fit the
RSGC1 data under condition of an atmospheric turbulent velocity of _∼_ 15 _±_ 1 km s _[−]_ [1], which is lower than the values quoted in
Table 2 of Kee et al. (2021) for stars with mass around 25 M _⊙_ .


In that regard, it is also worth turning our attention to F13 and
to the mass-loss rate prescriptions from van Loon et al. (2005)
and Goldman et al. (2017) which are derived for dusty RSGs,
some of which displaying clear OH maser action. The relation
of Goldman et al. (2017) yields a mass-loss rate that is a factor
_∼_ 10 higher than what we derive, although we need to remark
that the pulsation period estimated from the period-luminosity
relation given by De Beck et al. (2010) is very uncertain. The
van Loon et al. (2005) relation predicts a mass-loss rate for F13
of _M_ ˙ CO 5.8 _×_ (see10 _[−]_ Fig. [5] M _⊙_ 2)./yr,vanonlyLoona factoret al. 1.4(2005)largerdiscussedthan ourthatderivedtheir
recipe overestimates mass-loss rates for Galactic ‘optical’ RSGs,
on average by a factor _∼_ 2.8 (Mauron & Josselin 2011) with standard deviation on that value being _∼_ 2.5, hence in line with our
result for F13.

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Fig.** **4.** _M_ ˙ -luminosity relations parametrised in terms of log _L_ bol and _M_ ini and fitted jointly for the four open clusters RSGC1, NGC 2100,
NGC 7410, and _χ_ Per. Left panel presents the best-fit to the _M_ [˙] SED measurements of the four clusters (Eq. 7) while the right panel includes in the
fit the _M_ [˙] CO -values of four stars in RSGC1 (purple downward triangles) using Eq. (8). Symbols, colours and shades have the same meaning as in
Fig. 3, with the exception of the addition of the _M_ [˙] CO measurements derived in Sect. 3.1 using the _L_ bol values of Davies et al. (2008).



_4.2._ _Phase change in mass loss_


The amount of mass lost during the RSG phase, its speed, and
how soon before core collapse the material is removed can have
a dramatic effect on the resulting supernova light curve and spectrum (Smith et al. 2009). For luminosities above 10 [5] L _⊙_, a wind
mass-loss rate _≤_ 2 _×_ 10 _[−]_ [5] M _⊙_ /yr implies that the nuclear burning
rate exceeds the wind mass-loss rate (see right panel in Fig. 2),
and hence that core-He burning is dominating the evolution of
F01, F02, F03, and F04 (see Fig. 2). Accounting for the uncertainty in _L_ bol (Table 1) and _M_ [˙] CO, only F13 is above the boundary where the wind mass-loss rate dominates the star’s evolution.
This outcome is in line with the results from van Loon et al.
(1999) and Javadi et al. (2013), who suggested that red supergiants come in two flavours, those dominated by nuclear burning
which takes about 75% of the RSG lifetime, and those dominated
by intense mass loss taking _∼_ 25% of the RSG lifetimes.
The measured wind speed of the four RSGC1 sources
F01, F02, F03, and F04, whose evolution is dominated by
nuclear burning (see Fig. 2), is 11 _±_ 3 km/s. However, in the
case of source F13, the wind speed is significantly higher, at
_∼_ 22 km/s. The measured wind speeds conform to the wind
speed-luminosity relation ( _v_ _∞_ _∝_ _ZL_ [0] _[.]_ [4] ) established by Goldman et al. (2017) for OH/IR stars in the Large Magellanic Cloud
(LMC). However, they are noticeably lower compared to the
Galactic samples (see Fig. 17 in Goldman et al. 2017). This finding aligns with the outcomes reported by Davies et al. (2009),
who identified a subsolar iron content in the RSGC1 sources and
indicated a metallicity between Z = 0.008 and Z = 0.02. This
preliminary alignment with the relation proposed by Goldman
et al. (2017) for lower metallicities tentatively corroborates the
findings of Goldman et al. (2017) of expansion velocities being
consistent with the predictions of dust-driven wind theory (van
Loon 2000).
One advantage of our study is the ability to observe essentially the ‘same’ star at different stages of post-main sequence
evolution within a single cluster. When considering the changes
in mass-loss rate and wind speed, this leads to the hypothesis that



RSGs may undergo one or multiple phase changes in mass loss
during their RSG evolution. It is conjectured that there could be
intense and potentially eruptive mass loss occurring for a shorter
period of the RSG lifetime, which disrupts the otherwise more
tranquil mass-loss process that takes place over a larger portion
of the RSG branch. For further discussion on this topic, we refer
to Sect. 4.3.


_4.3._ _Implications for stellar evolution_


Accurate stellar mass-loss predictions are fundamental for stellar evolutionary models, in particular for the prediction of the
nature of the end-products. The outcome of this study impacts
the formation frequency of core-collapse supernovae of type
IIP, black holes and neutron stars, and hence the frequency of
gravitational wave events that can be detected with current (and
to be developed) detectors. For massive stars with initial mass
_<∼_ 30 M _⊙_, winds during the main-sequence phase will only remove _≤_ 0.8 M _⊙_ (Beasor et al. 2021). Hence, the only evolutionary phase during which these massive stars can potentially loose
a significant amount of mass is during the cool red supergiant
phase, which for a star of _∼_ 25 M _⊙_ lasts _∼_ 10 [5] _[.]_ [5] yr (Meynet et al.
2015).
The MESA evolutionary code (Paxton et al. 2019) was used
to compute the evolution of a 25 M _⊙_ star until core carbon depletion [7] . Following Brott et al. (2011), overshooting was modelled by extending the convective region by 0 _._ 335 pressure scale
heights, while winds during the main sequence and the WolfRayet phase are modelled using the prescriptions of Vink et al.
(2001) and Hamann et al. (1995). For temperatures below 10 [4] K
we switch to either the prescription of Nieuwenhuijzen & de
Jager (1990) or the newly derived one from Eq. (8). Composition and opacities are determined from solar metallicity and
metal fractions as given by Asplund et al. (2009).


7 The files to reproduce the simulations are available at [https://](https://zenodo.org/doi/10.5281/zenodo.10020628)
[zenodo.org/doi/10.5281/zenodo.10020628.](https://zenodo.org/doi/10.5281/zenodo.10020628)


Article number, page 9 of 29

_A&A proofs:_ manuscript no. RSGC1_final



Both simulations evolve to very different endpoints, with the
one using the Nieuwenhuijzen & de Jager (1990) wind prescription managing to strip its outer stellar envelope and evolve to
become a hot Wolf-Rayet star. Using the new prescription of
Eq. (8), only 1.93 M _⊙_ of the hydrogen-rich stellar envelope is
lost (out of a total envelope mass of 11.97 M _⊙_ ) implying that
such massive stars would explode as RSG upon core-collapse
(see Fig. 5). Following Smith et al. (2009), this leads to the suggestion that if F01, F02, F03, or F04 were to explode in their
current RSG phase, this would produce a Type II SN with limited level of interaction with the circumstellar material, without enough inertia to substantially decelerate the blast wave and
with no substantial narrow H _α_ emission from the post-shock gas.
Mass-loss rates of order _∼_ 11.97/1.93 = 6.20 times higher would
be needed to successfully strip the H-rich stellar envelope.


Nieuwenhuijzen & de Jager (1990) New









**Fig.** **5.** Evolutionary track as computed with the MESA evolutionary
code for a star of initial mass 25 M _⊙_ applying the RSG mass-loss rate
prescription from Nieuwenhuijzen & de Jager (1990) (blue) and from
Eq. (8) (orange). To discern long-lived versus short thermal evolution
phases, dots have been added every 10 [5] years; tracks go till carbon depletion indicated by the open square. The inset at the RSG, for a range
in log _T_ eff of 0.01 dex, shows how both tracks digress there.


In that sense, F13 might be an important outlier mass-loss
wise, since its _M_ [˙] CO is more than an order of magnitude larger
than for the other four RSGs. The retrieved _M_ [˙] CO value of F13
does not fit Eq. (8) which is _∼_ 10 times above the prescription.
Both the strong CO(2-1) line of F13 and its high near-infrared
extinction (Davies et al. 2008) indicate that F13 is surrounded
by a lot of circumstellar material produced by a wind with massloss rate higher than the other four RSGC1 sources. It might be
that the luminosity of F13 is underestimated given the high _M_ [˙] CO
and the fact that it is anomalously red compared to the other
RSGs in RSGC1. For fitting the relation Eq. (8), log( _L_ bol _/L_ _⊙_ )
should be 5.74, which would imply that it would be brighter than
any known RSG and is far above the Humphreys-Davidson limit.
Another possibility is an evolutionary phase change. Davies et al.
(2008) has shown that F13 is spatially coincident with H 2 O, OH,
and SiO maser emission [8] . Such maser emission is often associated with evolved stars that are long-period variables (periods of 300 – 500 days) and have winds with a very high mass

8
SiO masers are also detected associated with F01 and F02 (Davies
et al. 2008).


Article number, page 10 of 29



loss rate. This induces the suggestion that another mass-loss
rate mode has become active in F13. Among a coeval sample
of RSGs one may expect to see enhanced mass loss, and hence
masers, in those objects furthest along their evolution, that have
high _L_ _⋆_ / _M_ _⋆_ ratios — close to the (modified) Eddington limit
— so that only small changes in the atmospheric structure —
for example caused by pulsations or changes in the high opacity
due to variations in the hydrogen ionisation beneath the stellar
surface — makes these stars unstable to more furious episodic
mass ejections. Eq. (8) would then represent the more quiescent
mass-loss process, while F13 is an example RSG that undergoes
stronger, potentially eruptive, mass loss.

In that sense, F13 shares its status as extreme RSG with
VY _M_ ˙ CO CMa prediction using Eq. (8) is a factor(see App. G), the only Galactic _∼_ 6.6 too low. VY CMaRSG for which the
is one of a small class of evolved massive stars characterised
by extensive asymmetric ejections and multiple high massloss events lasting several hundred years (Decin et al. 2006;
O’Gorman et al. 2012; Kami´nski 2019; Humphreys et al. 2021)
attributed to large-scale surface and magnetic activity. Both F13
and VY CMa are indicative of a stronger, potentially eruptive,
mass-loss process that breaks from the prescription given in
Eq. (8); they demonstrate that one should be careful about applying any _M_ [˙] -prescription, including Eq. (8), more globally in
stellar evolution models as they will not reproduce the behaviour
of those extreme RSGs; see also the recent discussion by Massey
et al. (2022).

If we consider _F_ to be the fraction of time spent on RSG
phase with stronger mass loss, and _B_ the enhancement of the
mass-loss rate during that stage as compared to the more quiescent mass-loss rate (here _B_ = 10.43), we can estimate that the enhancement of a lifetime averaged mass-loss rate would be equal
to (1 _−_ _F_ ) + _B × F_ . For an enhancement of 6.20 and _B_ = 10.43,
we need _F_ = 0 _._ 55, so 55% of the lifetime on the strong massloss rate RSG phase to successfully strip the H-rich stellar envelope. However, this derived fraction of _F_ = 55% is much higher
than what one derives from using number statistics to determine
the fraction of time spent in the strong mass-loss rate stage. I.e.
out of 14 RSGs in RSGC1, only one of them is observed in the
strong mass-loss rate stage. To assess the likelihood of observing such a ratio (1 out of 14), a binomial distribution can be
employed. By conducting a Bayesian analysis with a flat prior
for _F_, the posterior distribution of _F_ can be determined, which
corresponds to a beta-distribution with shape parameters _α_ = 2
(representing the number of stars in high mass-loss rate phase +
1) and _β_ = 14 (representing the number of stars in the quiescent
RSG mass-loss rate stage + 1). Consequently, a 90% credible interval for _F_ is obtained as 10 _._ 9 [+17] _−_ 8 _._ 5 [%.] [This] [interval] [represents]
the median value along with the range between the 5th and 95th
percentiles.

This tension between the outcome of number statistics and
the fraction of time needed to strip the H-envelope during the
RSG phase when considering both the quiescent and (potentially eruptive) high mass-loss rate phase induces the suggestion
that the RSGs in RSGC1 will not be able to strip their entire
H-envelope and will explode as RSG upon core-collapse. For
the full H-rich envelope to be stripped, mass-loss rates much
stronger than observed for F13 would need to be invoked. A
potential mechanism thereof has been explored by Heger et al.
(1997), who suggested that sufficiently evolved stars become dynamically unstable and exhibit large-amplitude pulsations with
periods of the order of the Kelvin-Helmholtz time scale, which
eventually become strong enough to dynamically eject shells of

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1



matter from the stellar surface, implying the loss of (most of) the
H-rich envelope. Simulations for episodic mass ejections from
common-envelope binaries yield a similar outcome of dynamical
unstable mass ejections with periods in the range of a few years
to a few decades, leading to a time-averaged mass-loss rate of
the order of 10 _[−]_ [3] M _⊙_ /yr (Clayton et al. 2017). The probability
of observing RSGs in such a stage of large amplitude pulsation
and associated strong mass loss ( _∼_ _[>]_ 10 _[−]_ [4] _M_ [˙] /yr) is not very large;
however such events have marked consequence on the appearance of the supernova explosion.
Similarly, F15 is an important outlier, as being the only
post-RSG in the RSGC1 sample of Davies et al. (2008). F15
matches the picture of being a post-RSG star, with its luminosity of log( _L_ bol _/L_ _⊙_ ) _∼_ 5.36 matching that of the brightest RSGs
in RSGC1. Even though no mass-loss constraint could be made,
F15 could be indicative of the mass-loss process operating in the
RSG shutting off as the star becomes hotter ( _T_ eff _∼_ 6850 K) and
transitions to a radiative envelope. If F15 is indeed a post-RSG,
it indicates that the RSG mass loss managed to strip the H-rich
stellar envelope to the point that it would evolve to the blue.


**5.** **Conclusions**


The ALMA detection of CO(2-1) emission towards RSGs residing in the open cluster RSGC1 provides us with a powerful
diagnostic to derive the gas mass-loss rates of those RSGs. Of
importance is that the RSG cluster stars are co-eval, which allows for stars to be studied with the same initial conditions —
mass, metallicity, local environment, etc. Since the cluster stars
all have roughly the same initial masses (of _∼_ 25 M _⊙_, within a
few tenths of a solar mass), the evolutionary path should be the
same, allowing for the luminosity to be used as a proxy for evolution. Based on the CO(2-1) detections, we propose a new massloss rate relation for M-type RSGs with effective temperatures
between _∼_ 3200 – 3800 K, that scales with luminosity and mass.
The new _M_ [˙] -luminosity relation proposed in Eq. (8) is validated
against some other well-known Galactic RSGs towards which
multiple CO rotational lines have been observed.
The gas mass-loss rates derived from CO diagnostics are
systematically lower than the values retrieved from an SED
analysis on which current stellar evolution codes are based
( _M_ [˙] CO _<M_ [˙] SED ). Implementing our new mass-loss rate relation
will impact the frequency rate of type IIP SNe, neutron stars,
and black holes. In particular, models suggest that the RSG mass
loss would not allow single massive stars to evolve back to the
blue and explode as a H-poor SN. However, the mass-loss rate
of both the RSG F13 in RSGC1 and the well-known Galactic
extreme RSG VY CMa are almost an order of magnitude higher
than predicted by Eq. (8), which is indicative of a stronger massloss process different than captured by Eq. (8). Statistical reasoning implies that the RSGs in RSGC1 will not be able to strip
their entire H-rich envelope and will explode as a RSG upon core
collapse.
Only five RSGs in RSGC1 were detected during the current observation run. A completion of this RSGC1 study with
ALMA should allow a more accurate mass-loss rate relation to
be derived, that can be checked against lower mass-loss rate RSG
stars with lower luminosities. Given the fact that ALMA is now
50 – 100% more sensitive than in 2015, such deeper observations are now well feasible and would allow the observation of
large samples that are, as much as possible, uniform and unbiased. In addition, we intend to return to observe other clusters
with slightly different ages, such as RSGC2 (Davies et al. 2007),



which will then allow us to repeat this study but for RSGs with
slightly different masses. Ultimately, we will be able to provide
the time-averaged mass-loss rates and total mass lost during the
RSG phase as a function of initial mass, crucial inputs for the
theory of stellar evolution, and SN progenitors.


_Acknowledgements._ The authors acknowledge the referees for their constructive
feedback. The authors thank Emma Beasor and Benjamin Davies for fruitful discussions. LD acknowledges support from the European Research Council (ERC)
under the European Union’s Horizon 2020 research and innovation programme
(grant agreements No. 646758: AEROSOL with PI L. Decin) and from the FWO
grant G099720N. LD, HS, and PM acknowledge support from the KU Leuven
C1 excellence grant MAESTRO C16/17/007 (PI L. Decin). PM acknowledges
support from the FWO junior postdoctoral fellowship No. 12ZY520N. This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.1.01200.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The authors acknowledge the
UK Science and Technology Facilities Council (SFTC) IRIS for provision of
high-performance computing facilities. This work was partly performed using
the Cambridge Service for Data Driven Discovery (CSD3), part of which is operated by the University of Cambridge Research Computing on behalf of the
STFC DiRAC HPC Facility. The DiRAC component of CSD3 was funded by
BEIS capital funding via STFC capital grants ST/P002307/1 and ST/R002452/1
and STFC operations grant ST/R00689X/1.


**References**


Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481
Beasor, E. R. & Davies, B. 2016, MNRAS, 463, 1269
Beasor, E. R. & Davies, B. 2018, MNRAS, 475, 55
Beasor, E. R., Davies, B., & Smith, N. 2021, ApJ, 922, 55
Beasor, E. R., Davies, B., Smith, N., et al. 2020, MNRAS, 492, 5994
Bonanos, A. Z., Lennon, D. J., Köhlinger, F., et al. 2010, AJ, 140, 416
Brott, I., de Mink, S. E., Cantiello, M., et al. 2011, A&A, 530, A115
Clayton, M., Podsiadlowski, P., Ivanova, N., & Justham, S. 2017, MNRAS, 470,
1788
Danilovich, T., Teyssier, D., Justtanont, K., et al. 2015, A&A, 581, A60
Davies, B. & Beasor, E. R. 2020, MNRAS, 493, 468
Davies, B., Figer, D. F., Kudritzki, R.-P., et al. 2007, ApJ, 671, 781
Davies, B., Figer, D. F., Law, C. J., et al. 2008, ApJ, 676, 1016
Davies, B., Origlia, L., Kudritzki, R.-P., et al. 2009, ApJ, 696, 2014
De Beck, E., Decin, L., de Koter, A., et al. 2010, A&A, 523, A18
de Jager, C., Nieuwenhuijzen, H., & van der Hucht, K. A. 1988, A&AS, 72, 259
de Wit, W. J., Oudmaijer, R. D., Fujiyoshi, T., et al. 2008, ApJ, 685, L75
Decin, L. 2021, ARA&A, 59, 337
Decin, L., De Beck, E., Brünken, S., et al. 2010, A&A, 516, A69
Decin, L., Homan, W., Danilovich, T., et al. 2019, Nature Astronomy, 3, 408
Decin, L., Hony, S., de Koter, A., et al. 2006, A&A, 456, 549
Decin, L., Montargès, M., Richards, A. M. S., et al. 2020, Science, 369, 1497
Decin, L., Richards, A. M. S., Danilovich, T., Homan, W., & Nuth, J. A. 2018,
A&A, 615, A28
Díaz-Luis, J. J., Alcolea, J., Bujarrabal, V., et al. 2019, A&A, 629, A94
Draine, B. T. 1978, ApJS, 36, 595
Ekström, S., Georgy, C., Eggenberger, P., et al. 2012, A&A, 537, A146
Figer, D. F., MacKenty, J. W., Robberto, M., et al. 2006, ApJ, 643, 1166
Georgy, C. 2012, A&A, 538, L8
Goldman, S. R., van Loon, J. T., Zijlstra, A. A., et al. 2017, MNRAS, 465, 403
Gottlieb, C. A., Decin, L., Richards, A. M. S., et al. 2022, A&A, 660, A94
Groenewegen, M. A. T. 2017, A&A, 606, A67
Groenewegen, M. A. T. & Saberi, M. 2021, A&A, 649, A172
Hamann, W. R., Koesterke, L., & Wessolowski, U. 1995, A&A, 299, 151
Hawcroft, C., Sana, H., Mahy, L., et al. 2021, A&A, 655, A67
Heger, A., Fryer, C. L., Woosley, S. E., Langer, N., & Hartmann, D. H. 2003,
ApJ, 591, 288
Heger, A., Jeannin, L., Langer, N., & Baraffe, I. 1997, A&A, 327, 224
Homan, W., Decin, L., de Koter, A., et al. 2015, A&A, 579, A118
Humphreys, R. M., Davidson, K., Richards, A. M. S., et al. 2021, AJ, 161, 98
Humphreys, R. M. & Jones, T. J. 2022, AJ, 163, 103
Hunter, T. R., Lucas, R., Broguière, D., et al. 2016, in Society of Photo-Optical
Instrumentation Engineers (SPIE) Conference Series, Vol. 9914, Millimeter,
Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy VIII, ed. W. S. Holland & J. Zmuidzinas, 99142L
Javadi, A., van Loon, J. T., Khosroshahi, H., & Mirtorabi, M. T. 2013, MNRAS,
432, 2824
Josselin, E., Loup, C., Omont, A., et al. 1998, A&AS, 129, 45


Article number, page 11 of 29

_A&A proofs:_ manuscript no. RSGC1_final


Joyce, M., Leung, S.-C., Molnár, L., et al. 2020, ApJ, 902, 63
Kami´nski, T. 2019, A&A, 627, A114
Kee, N. D., Sundqvist, J. O., Decin, L., de Koter, A., & Sana, H. 2021, A&A,
646, A180
Kemper, F., Stark, R., Justtanont, K., et al. 2003, A&A, 407, 609
Kervella, P., Homan, W., Richards, A. M. S., et al. 2016, A&A, 596, A92
Khouri, T., de Koter, A., Decin, L., et al. 2014, A&A, 561, A5
Knapp, G. R. & Morris, M. 1985, ApJ, 292, 640
Kudritzki, R. P. & Reimers, D. 1978, A&A, 70, 227
Levesque, E. M., Massey, P., Olsen, K. A. G., et al. 2006, ApJ, 645, 1102
Liu, J., Jiang, B. W., Li, A., & Gao, J. 2017, MNRAS, 466, 1963
Loup, C., Forveille, T., Omont, A., & Paul, J. F. 1993, A&AS, 99, 291
Mamon, G. A., Glassgold, A. E., & Huggins, P. J. 1988, ApJ, 328, 797
Markwardt, C. B. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 411, Astronomical Data Analysis Software and Systems XVIII, ed.
D. A. Bohlender, D. Durand, & P. Dowler, 251
Massey, P., Neugent, K. F., Ekstrom, S., Georgy, C., & Meynet, G. 2022, arXiv
e-prints, arXiv:2211.14147
Matsuura, M., Sargent, B., Swinyard, B., et al. 2016, MNRAS, 462, 2995
Mauron, N. & Josselin, E. 2011, A&A, 526, A156
McDonald, I., Zijlstra, A. A., Lagadec, E., et al. 2015, MNRAS, 453, 4324
McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Messineo, M., Figer, D. F., Kudritzki, R.-P., et al. 2021, AJ, 162, 187
Meynet, G., Chomienne, V., Ekström, S., et al. 2015, A&A, 575, A60
Moe, M. & Di Stefano, R. 2017, ApJS, 230, 15
Montargès, M., Cannon, E., Lagadec, E., et al. 2021, Nature, 594, 365
Montargès, M., Homan, W., Keller, D., et al. 2019, MNRAS, 485, 2417
Nakashima, J.-i. & Deguchi, S. 2006, ApJ, 647, L139
Neugent, K. F., Levesque, E. M., Massey, P., Morrell, N. I., & Drout, M. R. 2020,
ApJ, 900, 118
Nieuwenhuijzen, H. & de Jager, C. 1990, A&A, 231, 134
O’Gorman, E., Harper, G. M., Brown, J. M., et al. 2012, AJ, 144, 36
Patrick, L. R., Lennon, D. J., Britavskiy, N., et al. 2019, A&A, 624, A129
Patrick, L. R., Lennon, D. J., Evans, C. J., et al. 2020, A&A, 635, A29
Patrick, L. R., Thilker, D., Lennon, D. J., et al. 2022, MNRAS, 513, 5847
Paxton, B., Smolec, R., Schwab, J., et al. 2019, ApJS, 243, 10
Ramstedt, S., Schöier, F. L., Olofsson, H., & Lundgren, A. A. 2008, A&A, 487,
645
Reimers, D. 1975, Memoires of the Societe Royale des Sciences de Liege, 8, 369
Rubio-Díez, M. M., Sundqvist, J. O., Najarro, F., et al. 2022, A&A, 658, A61
Saberi, M., Vlemmings, W. H. T., & De Beck, E. 2019, A&A, 625, A81
Salasnich, B., Bressan, A., & Chiosi, C. 1999, A&A, 342, 131
Sana, H. 2022, arXiv e-prints, arXiv:2203.16332
Sana, H., de Mink, S. E., de Koter, A., et al. 2012, Science, 337, 444
Schuster, M. T., Marengo, M., Hora, J. L., et al. 2009, ApJ, 699, 1423
Shenoy, D., Humphreys, R. M., Jones, T. J., et al. 2016, AJ, 151, 51
Smartt, S. J. 2009, ARA&A, 47, 63
Smith, N., Hinkle, K. H., & Ryde, N. 2009, AJ, 137, 3558
Sundqvist, J. O., Puls, J., Feldmeier, A., & Owocki, S. P. 2011, A&A, 528, A64
Tabernero, H. M., Dorda, R., Negueruela, I., & Marfil, E. 2021, A&A, 646, A98
van Loon, J. T. 2000, A&A, 354, 125
van Loon, J. T., Cioni, M.-R. L., Zijlstra, A. A., & Loup, C. 2005, A&A, 438,
273
van Loon, J. T., Groenewegen, M. A. T., de Koter, A., et al. 1999, A&A, 351,
559
Verhoelst, T., van der Zypen, N., Hony, S., et al. 2009, A&A, 498, 127
Vink, J. S., de Koter, A., & Lamers, H. J. G. L. M. 2001, A&A, 369, 574
Walmswell, J. J. & Eldridge, J. J. 2012, MNRAS, 419, 2054
Wittkowski, M., Hauschildt, P. H., Arroyo-Torres, B., & Marcaide, J. M. 2012,
A&A, 540, L12
Zhang, B., Reid, M. J., Menten, K. M., Zheng, X. W., & Brunthaler, A. 2012,
A&A, 544, A42


Article number, page 12 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Appendix A:** **ALMA observation**


For each star, the input for the ALMA observations is listed in Table A.1. For the five sources detected in the ALMA band 6
continuum data and in CO(2-1) line emission, Table A.1 lists the coordinates of the peak of the continuum emission, the peak
intensity, and the rms noise of the continuum and CO(2-1) observations.


For each source, Davies et al. (2008) has estimated the local standard of rest velocity, _v_ LSR, based on high spectral-resolution
observations of the 2.293 _µ_ m CO band head (see Table A.1), uncertainty being _±_ 4 km s _[−]_ [1] . These _v_ LSR values were used as input for
the ALMA observations. For sources F01, F02, F04, and F13, Nakashima & Deguchi (2006) also measured _v_ LSR using SiO maser
data, with an uncertainty of _±_ 2 km s _[−]_ [1] (see last column in Table A.1). Using the ALMA data, we have re-assessed the _v_ LSR values
based on the considerations that (i) the CO line profile is symmetric around the _v_ LSR value (see also footnote 2), and (ii) for spatially
resolved sources for which the CO optical thickness is not too high (typically, a maximum _τ_ _ν_ of _∼_ 2), the CO profile is two-horn
like (see Fig. 1). Those values are listed in Table 1 and in Table A.1. Given the spectral resolution of the data, the uncertainty on the
_v_ LSR values is _±_ 3 km s _[−]_ [1] . The newly derived _v_ LSR values for all sources agree with the values from Nakashima & Deguchi (2006).
For the sources F03, F04, and F13, the _v_ LSR values also agree with Davies et al. (2008), F02 is just within the uncertainty range of
both studies, but the value is off for F01. In particular, in the case of F01 Davies et al. (2008) lists a value of 129.5 km s _[−]_ [1], but the
ALMA CO and SiO maser data of Nakashima & Deguchi (2006) indicate a value around 117.5 km s _[−]_ [1] .


**Table A.1.** Data for the stars observed within the ALMA proposal 2013.1.01200.S.

|IDa|InputALMAobservationsb<br>α(J2000 .0) δ(J2000 .0) vLin Sp Rut|ALMAcontinuum<br>α (peak flux) δ (peak flux) Peak intensity σrms<br>[mJy/beam] [mJy/beam]|ALMACO(2 1)<br>-<br>σrms vLSR<br>[mJy/beam] [kms−1]|(c)<br>vLSR<br>[kms−1]|
|---|---|---|---|---|
|F01 <br>F02 <br>F03 <br>F04 <br>F05 <br>F06 <br>F07 <br>F08 <br>F09 <br>F10 <br>F11 <br>F12 <br>F13 <br>F14 <br>F15|18 37 56.29 _−_06 52 32.2 129.5<br> 18 37 55.28 _−_06 52 48.4 114.2<br> 18 37 59.72 _−_06 53 49.4 127.2<br> 18 37 50.90 _−_06 53 38.2 121.2<br> 18 37 55.50 _−_06 52 12.2 124.8<br> 18 37 57.45 _−_06 53 25.3 120.7<br> 18 37 54.31 _−_06 52 34.7 121.6<br> 18 37 55.19 _−_06 52 10.7 128.2<br> 18 37 57.77 _−_06 52 22.2 121.6<br> 18 37 59.53 _−_06 53 31.9 122.0<br> 18 37 51.72 _−_06 51 49.9 124.1<br> 18 38 03.30 _−_06 52 45.1<br>_−_<br> 18 37 58.90 _−_06 52 32.1 125.4<br> 18 37 47.63 _−_06 53 02.3 122.0<br> 18 37 57.78 _−_06 52 32.0 120.8|18 37 56.31<br>_−_06 52 32.25<br>0.420<br>0.051<br>18 37 55.29<br>_−_06 52 48.50<br>0.359<br>0.051<br>18 37 59.74<br>_−_06 53 49.50<br>0.160<br>0.053<br>18 37 50.89<br>_−_06 53 38.45<br>0.097<br>0.055<br>0.051<br>0.051<br>0.055<br>0.050<br>0.053<br>0.051<br>0.052<br>0.051<br>18 37 58.90<br>_−_06 52 32.05<br>0.148<br>0.051<br>0.052<br>0.051|1.7<br>117.5<br>1.9<br>120.5<br>2.1<br>123.5<br>2.0<br>123.5<br>2.0<br>2.0<br>2.2<br>2.0<br>2.4<br>2.0<br>2.0<br>1.8<br>1.8<br>123.5<br>1.7<br>1.9|117.7<br>119.7<br>_−_<br>124.3<br>_−_<br>_−_<br>_−_<br>_−_<br>_−_<br>_−_<br>_−_<br>_−_<br>120.5<br>_−_<br>_−_|



**Notes.** First part of the table lists the target identifier, the input coordinates for the ALMA observations, and the _v_ LSR as derived by Davies et al.
(2008). The second part of the table lists for the four sources detected in the ALMA band 6 continuum data and in CO(2-1) the coordinates of the
peak of the continuum emission, the peak flux, and the rms noise of the continuum observations. The third part lists the CO(2-1) line rms noise and
the _v_ LSR deduced from the ALMA CO(2-1) data. The last part list the _v_ LSR values deduced by Nakashima & Deguchi (2006) from the analysis of
SiO masers.
( _a_ ) The stellar IDs from Figer et al. (2006).
( _b_ ) From Davies et al. (2008).
( _c_ ) From Nakashima & Deguchi (2006).


Article number, page 13 of 29

_A&A proofs:_ manuscript no. RSGC1_final


**Appendix B:** **ALMA SiO and continuum images**


For the five sources in RSGC1 detected in the continuum and in CO v=0 J=2-1 emission, bright SiO v=3 J=5-4 line emission (at
212.582 GHz) is present as well. No other sources showed either line or had significant continuum detections.
Given the weak continuum flux for the five detected sources, we have used the bright SiO emission for locating the source and
its continuum emission. Fig. B.1 shows the SiO v=3 J=5-4 zeroth moment (i.e., total intensity) maps, and Fig. B.2 the continuum
emission. The location of the maximum of the continuum emission and the maximum continuum flux are listed in Table A.1. The
continuum rms noise is listed in Table A.1, and is _∼_ 0.05 mJy/beam. The rms noise in the SiO zeroth moment maps is 28, 34, 29, 34
and 35 mJy/beam km/s for F01, F02, F03, F04, and F13, respectively.



400


350


300


250


200


150


100


50


0


400


350


300


250


200


150


100


50


0


1200


1000



1


0


1


1


0


1


1



F01


1 0 1


Relative RA (arcsec)


F03


1 0 1


Relative RA (arcsec)


F13



1


0


1


1


0


1



F02


1 0 1


Relative RA (arcsec)


F04


1 0 1


Relative RA (arcsec)



1000


800


600


400


200


0


700


600


500


400


300


200


100


0



800


600

0


400


200


1


0

1 0 1


Relative RA (arcsec)


**Fig. B.1.** ALMA band 6 SiO v=3 J=5-4 zeroth moment maps of five red supergiants in RSGC1: F01 (upper left), F02 (upper right), F03 (middle
left), F04 (middle right), and F13 (bottom left). The ordinate and co-ordinate axis give the offset of the right ascension and declination, respectively,
with respect to the input coordinates for the ALMA observations (see columns 2 and 3 in Table A.1). The ALMA synthesised beam is shown as a
white ellipse in the lower right corner of each panel. The contours (in orange) show the SiO emission at [3, 5, 10] times the rms value.


Article number, page 14 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1



F01

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F03

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F13

1.0


0.5


0.0


0.5


1.0



0.40


0.35


0.30


0.25


0.20


0.15


0.10


0.05


0.00


0.16


0.14


0.12


0.10


0.08


0.06


0.04


0.02


0.00


0.14


0.12


0.10


0.08


0.06


0.04


0.02


0.00



F02

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F04

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)



0.35


0.30


0.25


0.20


0.15


0.10


0.05


0.00


0.08


0.06


0.04


0.02


0.00



1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


**Fig. B.2.** ALMA band 6 continuum maps of five red supergiants in RSGC1: F01 (upper left), F02 (upper right), F03 (middle left), F04 (middle
right), and F13 (bottom left). Contours (in orange) are indicated at [50, 60, 90, and 99]% of the peak continuum emission (see Table A.1). The
ordinate and co-ordinate axis give the offset of the right ascension and declination, respectively, with respect to the peak of the SiO v=3 J=5-4
zeroth moment map. The ALMA synthesised beam is shown as a white ellipse in the lower right corner of each panel.


Article number, page 15 of 29

_A&A proofs:_ manuscript no. RSGC1_final


**Appendix C:** **ALMA CO v=0 J=2-1 total intensity and channel maps**


In this section, we first present the ALMA CO v=0 J=2-1 total intensity (zeroth moment) and channel maps for all sources that
were detected in CO(2-1); i.e. F01, F02, F03, F04, and F13. Thereafter, we discuss for each source individually the spectral regions
contaminated by emission from the ISM.
For all sources, the continuum was less than the spectral channel rms so no continuum subtraction was performed. Fig. C.1
shows the CO v=0 J=2-1 total intensity map of F01, F02, F03, F04, and F13. The rms in each image varies due to different amounts
of ISM contamination as well as velocity widths averaged, with values being, respectively, 26, 21, 25, 23, and 29 mJy/beam km/s.
The peak signal-to-noise ratio ranges between _∼_ 12 – 34.



F01

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F03

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F13

1.0


0.5


0.0


0.5


1.0



350


300


250


200


150


100


50


0


400


300


200


100


0


1000


800


600


400


200


0



F02

1.0


0.5


0.0


0.5


1.0

1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


F04

1.0


0.5


0.0


0.5


1.0


Relative RA (arcsec)



200


150


100


50


0


300


250


200


150


100


50


0



1.0 0.5 0.0 0.5 1.0


Relative RA (arcsec)


**Fig. C.1.** ALMA band 6 CO v=0 J=2-1 zeroth moment maps of five red supergiants in RSGC1: F01 (upper left), F02 (upper right), F03 (middle
left), F04 (middle right), and F13 (bottom left). The ordinate and co-ordinate axis give the offset of the right ascension and declination, respectively,
with respect to the input coordinates for the ALMA observations (see columns 2 and 3 in Table A.1). The ALMA synthesised beam is shown as a
white ellipse in the lower right corner of each panel. The contours (in orange) show the CO emission at [3, 5, 10] times the rms value. The cyan
circle has a diameter of size 1 _[′′]_ and is centred on the peak of the continuum emission.


Article number, page 16 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Fig. C.2.** Measurements of the azimuthally averaged flux in annuli of 200-mas thick. The grey line indicates the 3 _×_ 25 = 75 mJy beam _[−]_ [1] km s _[−]_ [1]

cutoff.


For each source, two channel maps are presented, first a zoom onto the central 2 _[′′]_ _._ 2 region and then a larger map of size 8 _[′′]_
(Figs. C.3 – C.7). The combined use of these maps is needed to assess the ISM contamination.


Article number, page 17 of 29

_A&A proofs:_ manuscript no. RSGC1_final



4

4 2 0 2 4


Relative RA

(arcsec)


0.0000 0.0025 0.0050 0.0075 0.0100
Brightness (Jy/beam)


**Fig.** **C.3.** 12 **CO** **v=0** **J=2-1** **channel** **map** **of** **F01.** The ordinate and co-ordinate axis give the offset of the right ascension and declination,
respectively, with respect to the peak of the continuum emission (indicated by the cyan cross in the upper panels). The velocity is given in the
upper left corner of each panel (in units of km s _[−]_ [1] ). The cyan circle indicates the circular aperture of 0 _[′′]_ _._ 75 (diameter) centred on the peak of the
continuum emission that was used for extracting the CO(2-1) line profile. The ALMA beam is shown as a white ellipse in the bottom left corner
of the bottom left panel. Upper plot: The contours (in orange) show the CO emission at [3, 5] _×σ_ rms (see Table A.1). The contours (in yellow) in
the last panel show the continuum emission at [60, 90, and 99]% of the peak continuum emission.


Article number, page 18 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1



4

4 2 0 2 4


Relative RA

(arcsec)


0.0000 0.0025 0.0050 0.0075 0.0100
Brightness (Jy/beam)


**Fig. C.4.** [12] **CO v=0 J=2-1 channel map of F02.** Same as Fig. C.3, but for F02.


Article number, page 19 of 29

_A&A proofs:_ manuscript no. RSGC1_final











4

4 2 0 2 4


Relative RA

(arcsec)


0.000 0.003 0.006 0.009 0.012
Brightness (Jy/beam)


**Fig. C.5.** [12] **CO v=0 J=2-1 channel map of F03.** Same as Fig. C.3, but for F03.


Article number, page 20 of 29

1.0



L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


156.4 153.4 150.4 147.4 144.4 141.4


138.4 135.4 132.4 129.4 126.4 123.4


120.4 117.4 114.4 111.4 108.4 105.4


102.4 99.4 96.4 93.4 90.4



0.5


0.0


0.5


1.0


1.0 0.5 0.0 0.5 1.0


Relative RA

(arcsec)


0.0000 0.0025 0.0050 0.0075 0.0100
Brightness (Jy/beam)

156.4 153.4 150.4 147.4 144.4 141.4


138.4 135.4 132.4 129.4 126.4 123.4


120.4 117.4 114.4 111.4 108.4 105.4


4

102.4 99.4 96.4 93.4 90.4


2


0


2


4

4 2 0 2 4


Relative RA

(arcsec)


0.0000 0.0025 0.0050 0.0075 0.0100
Brightness (Jy/beam)


**Fig. C.6.** [12] **CO v=0 J=2-1 channel map of F04.** Same as Fig. C.3, but for F04.


Article number, page 21 of 29

_A&A proofs:_ manuscript no. RSGC1_final











4

4 2 0 2 4


Relative RA

(arcsec)


0.000 0.005 0.010 0.015 0.020
Brightness (Jy/beam)


**Fig. C.7.** [12] **CO v=0 J=2-1 channel map of F13.** Same as Fig. C.3, but for F13.


Article number, page 22 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


For all sources, there is much less (or no) ISM contamination visible on the high velocity side, although there might be a noise
background. In particular:


F01: At velocities lower than _∼_ 105 km s _[−]_ [1] the ISM emission starts contributing. In general, the angular extent of a spherically
symmetric source with monotonically increasing velocity will be larger around zero rest velocity, and will decrease when going
to redder and bluer velocities. For the source F01, we notice extra emission in the channels from 129.4–135.4 km s _[−]_ [1] offset from
the centre to the north-east, that is also visible as increase in flux density in Fig. 1. Either this is noise (the blob is at _<_ 4 _×σ_ rms )
or it is a genuine source (as, for example, another cluster member, a companion, ...). When fitting the CO(2-1) line profile for
retrieving the gas mass-loss rate, this extra emission is neglected. In the case that F01 would still contribute significant flux in
the 129.4-135.3 km s _[−]_ [1] channels, the terminal velocity would be underestimated. Under the rough assumption that the extra blob
to the north-east would contribute _∼_ 2.8 mJy in the 129.4 – 135.5 km s _[−]_ [1] velocity range, the terminal velocity could reach up to
_∼_ 16 km s _[−]_ [1] . A good prediction of the (flux-corrected) red wing and peak flux around 135 km s _[−]_ [1] (with peak flux then being around
5 mJy) is achieved for a mass-loss rate of 2.2 _×_ 10 _[−]_ [6] M _⊙_ /yr and _v_ LSR around 127 km s _[−]_ [1], but the peak around 115 – 125 km s _[−]_ [1] is
then underpredicted by a factor of _∼_ 2 (see dotted black line in upper left panel in Fig. 1). That value for _M_ [˙] CO is only _∼_ 10% higher
than the value listed in Table 1.


F02: The CO(2-1) spectrum of F02 is quite clean, with the exception of the ISM contamination at velocities lower than
_∼_ 105 km s _[−]_ [1] .


F03: For velocities lower than _∼_ 114.4 km s _[−]_ [1], there is a strong contribution from the ISM, which then vanishes at _∼_ 99.4 km s _[−]_ [1] .
The theoretical line profile for a terminal wind velocity of 13 km s _[−]_ [1] and _M_ [˙] CO of 3.2 _×_ 10 _[−]_ [6] M _⊙_ /yr is slightly underpredicting the
red wing of the ALMA CO(2-1) data (Fig. 1). A terminal wind velocity of 17 km s _[−]_ [1] and _M_ [˙] CO of 3.8 _×_ 10 _[−]_ [6] M _⊙_ /yr gives a better
prediction of the red wing for flux values below _∼_ 4 mJy, but then the typical two-horn profile is predicted too wide. That difference
of 15% in _M_ [˙] CO owing to an uncertainty in _v_ _∞_ is within the quoted uncertainty on the retrieved _M_ [˙] CO -values, see Table D.1.


F04: Similar to F03, the ISM is contaminating the channel maps and spectrum for velocities _[<]_ _∼_ 114.4 km s _[−]_ [1] .


F13: F13 is the source for which the CO(2-1) emission is the least contaminated by the ISM. Only for velocities _[<]_ _∼_ 99.4 km s _[−]_ [1],
the line profile might be contaminated.


**Appendix D:** **Uncertainty estimate on CO(2-1) line profile predictions**


The radiative transfer analysis of the CO(2-1) emission is based on a number of input parameters. To assess the impact of the model
predictions to uncertainties on the different derived or assumed input parameters, we varied the input parameters independently
and calculated the percentage impact on the line profile and the associated uncertainty on the mass-loss rate _M_ [˙] CO (see Table D.1).
Uncertainties on the effective temperature (of _±_ 130 K), luminosity and hence stellar radius R _⋆_ ( _±_ 215 R _⊙_ ), and distance _D_ ( _±_ 890 pc)
are taken from Davies et al. (2008), on the fractional carbon abundance and hence on [CO/H] (of _±_ 1.4 _×_ 10 _[−]_ [5] ) from Davies et al.
(2009), on the terminal wind velocity (of _±_ 3 km/s) and the outer radius (of _±_ 50 R _⋆_ ) from our ALMA data, and on the coefficients
for the wind acceleration profile _β_ ( _±_ 2) and for the temperature profile _ϵ_ ( _±_ 1) from the analysis presented in Decin et al. (2006) and
De Beck et al. (2010). The canonical gas-to-dust ratio of 200 was taken representative for a Milky Way cluster (Beasor et al. 2020),
but is quite ill-constrained. We therefore let it range between 100 – 1000. The largest uncertainty in _M_ [˙] CO arises from uncertainties

_∼_
in the terminal wind velocity ( 35%), and then in the distance, the outer CO envelope size, and the CO fractional abundance (each
_∼_ 20%). Uncertainties on all other parameters only have a minor effect. We note that the uncertainty estimates in Table D.1 are
conservative values since only based on reproducing the peak flux, but not accounting for the full shape of the line profile which
carries important diagnostics on, for example, the optical thickness of a specific line.
To calculate the combined effect of the errors in the individual input parameters on _M_ [˙] CO, one should perform a Monte Carlo
Markov Chain (MCMC) analysis. However, this is not feasible since non-LTE radiative tranfser calculations are too computerintensive to be embedded in a MCMC algorithm. We therefore need to resort to a simpler approach similar to, for example, DíazLuis et al. (2019) who have used an analytical prescription derived by Knapp & Morris (1985) to calculate the mass-loss rate given
some individual parameters such as the expansion velocity, distance, integrated line intensity, and [CO/H] ratio (see, for example,
Eq. 3 in Díaz-Luis et al. 2019). However, we here use our model grid and results presented in De Beck et al. (2010) since based
on the same GASTR O NO O M models, in particular we use Eq. 9 of De Beck et al. (2010). The CO envelope size, _R_ out, is not an
individual input value of Eq. 9 of De Beck et al. (2010), but is inherently captured in Eq. 9 since the [CO/H] ratio determines the
photodissociation radius of the circumstellar envelope. Contrary to Díaz-Luis et al. (2019), we do not add the individual uncertainties
in (unweighted) quadrature, but use a proper error propagation based on Eq. 9 of De Beck et al. (2010) which weighs the sensitivity
of each individual uncertainty. Hence, we derive that the total uncertainty on the estimated _M_ [˙] CO -values is a factor of _∼_ 1.4. In that,
the uncertainty in terminal wind velocity contributes some 50% of the total uncertainty factor and the distance _∼_ 30%.
It might seem surprising that this total uncertainty on _M_ [˙] CO is similar to the highest uncertainty raised by an individual parameter
(of _∼_ 42%) listed in Table D.1. The reason thereof is that Table D.1 uses the sensitivity of the intensity peak to determine the
associated change in _M_ [˙] CO by using a full non-LTE radiative transfer routine, while Eq. 9 of De Beck et al. (2010) is an analytic
relation based on the integrated line intensity with various weightings (in terms of exponential factors) for the input parameters.
Those different approaches hence rule out a one-to-one comparison of both uncertainty values.


Article number, page 23 of 29

_A&A proofs:_ manuscript no. RSGC1_final


**Table D.1.** Uncertainty on the model predictions.

|Parameter|1σuncertaintyparameter|Uncertaintypeakintensity|Uncertainty M˙<br>CO|
|---|---|---|---|
|_D_ = 6600 pc|+890 pc<br>_−_890pc|_−_23%<br>+32%|+19%<br>_−_19%|
|_T_ef = 3450 K|_±_130 K|_∓_4%|_±_1%|
|_R⋆_= 1450 R_⊙_|+215 R_⊙_<br>_−_215 R_⊙_|+10%<br>_−_15%|_−_8%<br>+15%|
|_v∞_= 11 km/s|+3 km/s<br>_−_3 km/s|_−_39%<br>+60%|+35%<br>_−_34%|
|_β_ = 3.0|_±_2|_±_2%|_∓_4%|
|_ϵ_ = 0.6|_±_0.1|_∓_12%|_±_4%|
|_R_out = 400 R_⋆_|+50 R_⋆_<br>_−_50 R_⋆_|+21%<br>_−_21%|_−_12%<br>+23%|
|[CO/H] = 8.9_×_10_−_5|+1.4_×_10_−_5<br>_−_1.4_×_10_−_5|+20%<br>_−_22%|_−_12%<br>+23%|
|_r_gd = 200|_r_gd = 100<br>_r_gd = 1 000|_−_5%<br>+4%|+4%<br>_−_4%|



**Notes.** First column lists the input parameter, second column the 1 _σ_ uncertainty of the input parameter (unless for the gas-to-dust ratio which lists
its range in potential values), third column the associated change in peak intensity, and last column the associated uncertainty on the mass-loss rate _M_ ˙ CO . Non-symmetric changes in the associated peak strength and _M_ ˙ CO are listed separately.


**Appendix E:** _**M**_ **˙** **-luminosity relations from Beasor et al. (2020)**


In a first step, Beasor et al. (2020) has determined a _M_ [˙] -luminosity relation for all clusters in their sample by fitting the relation given
in Eq. (4) to their data points taken from Beasor & Davies (2016), Beasor & Davies (2018) and Beasor et al. (2020) (see Table E.1).
They therefore have used a linear least-square approximation that accounts for both errors on the ordinate and coordinate values.
However, plotting the _M_ [˙] -luminosity relation using the values for the intercept and slope as listed in Table 4 of Beasor et al. (2020)
(repeated here in Table E.2) reveals a problem with those values (see left panel in Fig. E.1): (1) A typo occurred in Table 4 of
Beasor et al. (2020): the intercept _a_ for RSGC1 should not be _−_ 52, but _−_ 53 (Beasor, priv. comm.), which indeed yields a much
better fit to the data (see dotted line in left panel of Fig. E.1); and (2) comparing Fig. 3 and Fig. E.1 with Fig. 2 in Beasor et al.
(2020) shows a problem with the data points plotted in Beasor et al. (2020), for example the maximum _M_ [˙] SED value for NGC 7419
is 1.8 _×_ 10 _[−]_ [5] M _⊙_ /yr (see Table E.1) but is plotted around 7 _×_ 10 _[−]_ [5] M _⊙_ /yr in Fig. 2 of Beasor et al. (2020); similar problems occur
for other data points. For that reason we continue with the data listed in Table E.1; a corrigendum is currently being prepared by
E. Beasor et al.

In a next step, Beasor et al. (2020) chose to fix the gradient in order to reduce the number of degrees of freedom in the fit.
interceptAccounting for the standard deviation on the derivedvalues in their more general mass-dependent _b_ -values, one gets _M_ ˙ -luminosity relation _b_ =4.8 _±_ 0.6. The latter value was then used for deriving thegiven in Eq. (3) (which is Eq. (4) in Beasor et al.
2020). But for RGSC1, the _M_ [˙] -luminosity relation from their Eq. (4) seems at odd with the empirical (L bol, _M_ [˙] SED ) values (see right
panel in Fig. E.1), with the straight-line fit being systematically lower than the empirical values. We therefore have repeated their
analysis for a slope of _b_ =4.8 _±_ 0.6. Fixing the slope, only the intercept has to be determined; the derived values with their standard
deviation are listed in the fourth column of Table E.2. From the analysis of the four clusters, we can determine the mass-dependent
intercept, yielding the following mass-dependent _M_ [˙] SED -luminosity relation


log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = ( _−_ 26 _._ 5 _−_ 0 _._ 22 _× M_ ini _/_ M _⊙_ ) + 4 _._ 8 log( _L_ bol _/_ L _⊙_ ) (E.1)


with standard deviations on the best-fit parameters being _−_ 26.50 _±_ 1.33, _−_ 0.22 _±_ 0.10, and 4.8 _±_ 0.6; which is similar to Eq. (3)
within some round-off errors. Eq. (E.1) implies a slight shift upwards for RSGC1 as compared to Eq. (3) (see red dashed-triple
dotted line in the right panel of Fig. E.1), but that shift is not visible on the scale of the plot for the 3 other clusters.


**Appendix F:** **Sensitivity to intercept** _**a**_ _**i**_


Fig. F.1 shows the fit to Eq. (5), but instead of using RSGC1 for determining _a_ 1, we use NGC 2100 for determining the intercept
_a_ 2 and the difference in intercept of the other 3 clusters, ∆ _a_ _i_ ( _i_ = 1,3,4). We fit both the ( _L_ bol, _M_ [˙] SED ) and ( _L_ bol, _M_ [˙] CO ) together;
corresponding values are listed in Table F.1.


Article number, page 24 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Table E.1.** Values for bolometric luminosity and _M_ [˙] SED for _χ_ Per, NGC 7419, NGC 2100 and RSGC1.

|χPer|NGC7419|
|---|---|
|Star<br>log(Lbol/L_⊙_)<br>˙_M_ SED (10_−_6 M_⊙_yr_−_1)|Star<br>log(Lbol/L_⊙_)<br>˙_M_ SED (10_−_6 M_⊙_yr_−_1)|
|FZ Per<br>4.64+0_._06<br>_−_0_._05<br>0.30+0_._18<br>_−_0_._07<br>RS Per<br>4.92+0_._18<br>_−_0_._07<br>3.03+2_._31<br>_−_0_._94<br>AD Per<br>4.80+0_._08<br>_−_0_._05<br>0.97+0_._33<br>_−_0_._50<br>V439 Per<br>4.53+0_._06<br>_−_0_._05<br>0.10+0_._10<br>_−_0_._01<br>V403 Per<br>4.41+0_._06<br>_−_0_._05<br>0.06+0_._02<br>_−_0_._02<br>V441 Per<br>4.75+0_._10<br>_−_0_._06<br>0.93+0_._72<br>_−_0_._31<br>SU Per<br>4.99+0_._09<br>_−_0_._05<br>1.62+0_._72<br>_−_0_._63<br>BU Per<br>4.67+0_._07<br>_−_0_._05<br>3.24+1_._53<br>_−_1_._28|MY CEP<br>5.19_±_0.07<br>18.04+7_._15<br>_−_8_._54<br>BMD 139<br>4.55_±_0.08<br>0.27+0_._44<br>_−_0_._05<br>BMD 696<br>4.63_±_0.08<br>0.22+0_._17<br>_−_0_._04<br>BMD 435<br>4.54_±_0.11<br>0.18+0_._15<br>_−_0_._04|
|RSGC1|NGC 2100|
|Star<br>log(Lbol/L_⊙_)<br>˙_M_ SED (10_−_6 M_⊙_yr_−_1)|Star<br>log(Lbol/L_⊙_)<br>˙_M_ SED (10_−_6 M_⊙_yr_−_1)|
|F01<br>5.58_±_0.18<br>5.57+2_._37<br>_−_2_._17<br>F02<br>5.56_±_0.18<br>5.18+2_._72<br>_−_1_._75<br>F03<br>5.33_±_0.18<br>4.18+3_._08<br>_−_0_._84<br>F06<br>5.32_±_0.18<br>0.68+0_._69<br>_−_0_._14<br>F07<br>5.31_±_0.18<br>0.28+0_._29<br>_−_0_._06<br>F09<br>5.30_±_0.18<br>0.52+0_._53<br>_−_0_._10<br>F10<br>5.28_±_0.18<br>0.87+0_._89<br>_−_0_._17<br>F12<br>5.22_±_0.19<br>0.18+0_._04<br>_−_0_._04|1<br>5.09_±_0.09<br>9.89+4_._20<br>_−_3_._17<br>2<br>4.97_±_0.09<br>9.97+4_._52<br>_−_3_._19<br>3<br>4.84_±_0.09<br>1.98+1_._07<br>_−_0_._74<br>4<br>4.71_±_0.09<br>3.17+2_._34<br>_−_1_._29<br>5<br>4.73_±_0.09<br>2.54+1_._49<br>_−_0_._86<br>6<br>4.77_±_0.09<br>3.25+2_._12<br>_−_0_._72<br>7<br>4.68_±_0.09<br>0.82+0_._27<br>_−_0_._46<br>8<br>4.68_±_0.09<br>1.29+0_._76<br>_−_0_._51<br>9<br>4.68_±_0.09<br>0.48+0_._26<br>_−_0_._18<br>10<br>4.63_±_0.09<br>1.06+0_._80<br>_−_0_._36<br>11<br>4.55_±_0.09<br>0.28+0_._14<br>_−_0_._16<br>12<br>4.51_±_0.09<br>0.39+0_._21<br>_−_0_._21<br>16<br>4.55_±_0.09<br>2.27+1_._14<br>_−_0_._57<br>17<br>4.49_±_0.09<br>0.23+0_._15<br>_−_0_._15|



**Notes.** Values used for Fig. 3 and Fig. E.1, and reproduced from Table 3 of Beasor & Davies (2016), Table 2 of Beasor & Davies (2018), and
Table 2 of Beasor et al. (2020).


**Table E.2.** Best-fit parameters for the _M_ [˙] SED -luminosity relation for each cluster derived by fitting Eq. (4) to the data.

|Cluster|Intercept(a) Slope(b)|Intercept(a)<br>for fixed b = 4 .8±0 .6|
|---|---|---|
|RSGC1<br>NGC 2100<br>NGC 7419<br>_χ_ Per|_−_52.0_±_51.2<br>8.8_±_9.5<br>_−_30.9_±_3.6<br>5.3_±_0.8<br>_−_22.9_±_4.9<br>3.6_±_1.7<br>_−_27.06_±_4.90<br>4.5_±_1.0|_−_31.90_±_1.16<br>_−_28.59_±_0.75<br>_−_29.01_±_1.41<br>_−_28.97_±_0.99|



**Notes.** The second and third column list, respectively, the intercept _a_ and slope _b_ with their standard deviation as derived by Beasor et al. (2020).
The fourth column lists the intercept _a_ and its standard deviation for a slope fixed to _b_ = 4.8 _±_ 0.6.


**Table F.1.** _M_ ˙ CO ) values for RSGC1. The MC method yields a best-fit slope ( _L_ bol, _M_ [˙] )-relation for each cluster derived when fitting Eq. 5 to the ( _b_ = 3.38 [+0] _−_ 0 _[.]_ _._ [52] 44 [and intercept] _L_ bol, _M_ [˙] SED _[ a]_ [2] ) measurements of the four clusters and the ( [for NGC 2100 of] _[ −]_ [21.75] _−_ [+2] 2 _[.]_ _._ [05] 46 [.] _L_ bol,


Article number, page 25 of 29


|Cluster|differenceinintercept(∆ai)<br>Eq (5)<br>.|
|---|---|
|RSGC1<br>NGC 2100<br>NGC 7419<br>_χ_ Per|_−_2.32+0_._38<br>_−_0_._44<br>0<br>_−_0.47+0_._24<br>_−_0_._25<br>_−_0.33+0_._16<br>_−_0_._16|
|RSGC1(CO)|_−_2.02+0_._38<br>_−_0_._43|

_A&A proofs:_ manuscript no. RSGC1_final


**Fig. E.1.** _M_ [˙] -luminosity relations as determined by Beasor et al. (2020). The coloured symbols represent the (L bol, _M_ [˙] SED )-values for four open
clusters as derived by Beasor & Davies (2016); Beasor et al. (2020); error bars indicate their most conservative error estimates. The straight lines
in both panels show the individual straight-line fits to each relation log( _M_ [˙] SED _/_ M _⊙_ yr _[−]_ [1] ) = _a_ + _b_ log( _L_ bol _/_ L _⊙_ ) for all clusters in the sample.
In the left panel, the dashed lines show the _M_ [˙] - _L_ bol relation using the values for the offset and slope as given in Table 4 of Beasor et al. (2020);
the full lines in the right panel show the fits to the _M_ [˙] - _L_ bol relation once the gradient is fixed to _b_ = 4.8, following Eq. 4 of Beasor et al. (2020) and
using the values for the initial mass as given in Table 1 of Beasor et al. (2020). The red dotted line in the left panel shows the fit to RSGC1 for an
intercept _a_ = -53; see footnote 7. The red dashed-triple dotted lin in the right panel shows the fit to RSGC1 following Eq. (E.1).


**Fig.** **F.1.** _M_ ˙ -luminosity relations for the four open clusters RSGC1, NGC 2100, NGC 7410, and _χ_ Per. Dashed gold, red, black, and blue lines
present the best-fit of Eq. (5) to the ( _L_ bol, _M_ [˙] SED ) measurements of the four clusters (shown as open symbols with corresponding colour), and the
dashed purple line the best-fit to the ( _L_ bol, _M_ [˙] CO ) values of four stars in RSGC1 (filled purple downward triangles).


Article number, page 26 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Appendix G:** **Other Galactic red supergiants**


In this section, we derive _M_ ˙ CO for some well-known Galactic M-type red supergiants following the same modelling strategy as
in Sect. 3.1. The aim is to compare the retrieved _M_ [˙] CO with the values predicted using Eq. (8). We therefore perform a radiative
transfer analysis of the CO rotational line transitions of the red supergiants published by De Beck et al. (2010). In particular, we
analyse the James Clerk Maxwell Telescope (JCMT) data of _α_ Ori, _µ_ Cep, and VX Sgr. The M2 red supergiant VY CMa is excluded
from the current analysis, since the CO rotational line data have already been analysed by Decin et al. (2006) and we will resort
to their outcomes. We also exclude the hypergiant NML Cyg, since its estimated initial mass of _∼_ 40 M _⊙_ (Schuster et al. 2009)
puts its above the mass range of 8 _∼_ _[<]_ _M_ _⋆_ _∼_ _[<]_ 30 M _⊙_ of interest to this study. The JCMT data of _α_ Ori, _µ_ Cep, and VX Sgr are plotted
in Fig. G.1. The intensity is plotted as main beam temperature _T_ mb, in units of K, which can be converted to flux density _F_ _ν_ or
brightness _I_ _ν_ by following formula



_λ_ cm

_T_ mb = _[λ]_ [2] _[ F]_ _[ν]_ [1] _[.]_ [36]

2 _k_ Ω [=] � _θ_ _[′′]_



2

_I_ _ν_ _,_ (G.1)
�



with _λ_ the wavelength, _k_ the Boltzmann constant, Ω the beam solid angle, _λ_ cm the wavelength in units of cm, _θ_ the beam size in
units of arcsec, and _I_ _ν_ the brightness in units of mJy/beam. The beam size of the JCMT CO(2-1), CO(3-2), and CO(4-3) data are
19 _[′′]_ _._ 7, 13 _[′′]_ _._ 2, and 10 _[′′]_ _._ 8, respectively.
Similar to the analysis of the five red supergiants in RSGC1 (Sect. 3.1), we assume that the main wind component can be
represented by a spherically symmetric envelope. As has been discussed in detail in the literature, high spatial and spectral resolution
observations of those Galactic RSGs prove that those winds are composed of a smooth outflow and individual mass ejections in
the form of gas and dust clumps (Decin et al. 2006; Montargès et al. 2019, 2021; Humphreys & Jones 2022). The smooth outflow
contains by far most of the mass and its mass-loss rate is a factor of a few up to almost 2 orders of magnitude higher than that traced
by the individual clumps (Montargès et al. 2019, 2021; Humphreys & Jones 2022). With the aim of (i) deriving the overall (average)
mass-loss rate _M_ [˙] CO, and (ii) comparing _M_ [˙] CO with the predictions from Eq. (8), we only focus on modelling the dominant outflow.
This implies that spikes, visible on top of the JCMT CO line profiles and testifying the presence of individual gas clumps, will not
be modelled.
To retrieve _M_ [˙] CO, we follow the same modelling strategy as outlined in Sect. 3.1. The input stellar and CSE parameters are listed
in Table G.1. For _α_ Ori and _µ_ Cep, the CO outer envelope size can be estimated from radio interferometric observations, while for
VX Sgr we use the photodissociation radius following the results of Groenewegen & Saberi (2021). For each of the sources, the
individual modelling could be optimised by fine-tuning some of the input parameters described in Sect. 3.1. However, we refrain
from doing so since we aim to assess the predictive power of Eq. (8) in relation to our overall modelling strategy of retrieving _M_ [˙] CO .
Given the complexity of the line profiles and the absolute flux calibration accuracy of _∼_ 30% (Kemper et al. 2003), the fits shown in
Fig. G.1 prove that for all sources the main CO component is well reproduced. In contrast to the analysis of the RSGC1 RSGs, the
main uncertainty on the retrieved _M_ [˙] CO values arises from uncertainties on the distance; translating into an _M_ [˙] CO uncertainty of a
factor ofThe _∼_ gas2 – 3.mass-loss rates retrieved from this analysis, _M_ ˙ CO, are listed in Table G.1 and can be compared to the _M_ ˙ -values
predicted using Eq. (8) and using Eq. (3), the latter once following the results of Beasor et al. (2020). With the exception of the cool
extreme supergiant VY CMa, Eq. (8) predicts the gas mass-loss rate for the other 3 red supergiants well — the average difference
only being _∼_ 30%. This result supports the use of Eq. (8) for the prediction of mass-loss rates for M-type red supergiants with
effective temperature _[>]_ _∼_ 3200 K. Eq. (3) predicts the gas mass-loss rates well for _µ_ Cep and VX Sgr, but fails for _α_ Ori and VY CMa.
tic RSGs.The derivedAssuming _M_ [˙] CO avalues can be compared towind speed of 10 km/s and _M_ [˙] SED gas-to-dustretrievals to determine the gas-to-dust ratio of the winds of those Galac-ratio of 100, Verhoelst et al. (2009) derived that _M_ ˙ SED equals
6.3 _×_ 10 _[−]_ [8] M _⊙_ /yr (for a distance of 131 pc) in the case of _α_ Ori, and 2.9 _×_ 10 _[−]_ [7] M _⊙_ /yr (for a distance of 830 pc) in the case of
_µ_ Cep. Similarly we use the values derived by Liu et al. (2017) and Shenoy et al. (2016) for VX Sgr and VY CMa, respectively.
Scaling for the difference in adopted distance and wind speed, we derive a gas-to-dust ratio of 297, 544, 226, and 18 for _α_ Ori,
_µ_ Cep, VX Sgr, and VY CMa, respectively. The gas-to-dust ratio derived for VY CMa might seem very low. However, it should
be noted that Decin et al. (2006) derived that VY CMa underwent a phase of high mass loss ( _∼_ 3.2 _×_ 10 _[−]_ [4] M _⊙_ /yr; see Table G.1)
some 1000 yr ago. This phase took some 100 yr and was preceded by a low mass-loss phase ( _∼_ 1 _×_ 10 _[−]_ [6] M _⊙_ /yr) taking some 800
yr. The current mass-loss rate (of _∼_ 8 _×_ 10 _[−]_ [5] M _⊙_ /yr) was used to derive the gas-to-dust value, which obviously will change during
other mass-loss phases. Moreover, the assumption of a spherical symmetry for the circumstellar envelope of VY CMa is obviously
a simplification on the basis of which the dust mass-loss rate has been derived by Shenoy et al. (2016); see discussion in that paper.


Article number, page 27 of 29

_A&A proofs:_ manuscript no. RSGC1_final


**Table G.1.** Stellar and CSE parameters for the red supergiants observed in various CO rotational lines by De Beck et al. (2010).


Stellar parameters CSE parameters
Star log( _L_ bol _/L_ _⊙_ ) _T_ eff Spectral R _⋆_ _M_ ini _D_ _v_ LSR [(] _[c]_ [)] _v_ _∞_ [(] _[c]_ [)] _R_ out [(] _[c]_ [)] _M_ ˙ CO [(] _[c]_ [)] _M_ ˙ [(] _[c]_ [)] _M_ ˙ [Beasor]
type Eq. (8) Eq. (3)

[K] [R _⊙_ ] [ _M_ _⊙_ ] [pc] [km s _[−]_ [1] ][km s _[−]_ [1] ] [R _⋆_ ] [10 _[−]_ [6] M _⊙_ /yr][10 _[−]_ [6] M _⊙_ /yr][10 _[−]_ [6] M _⊙_ /yr]
_α_ Ori 4.94 [(] _[a]_ [)] 3600 [(] _[a]_ [)] M2Iab [(] _[b]_ [)] 764 [(] _[a]_ [)] 19.5 [(] _[a]_ [)] 168 [(] _[a]_ [)] 3.4 13 800 [(] _[j]_ [)] 0.4 0.6 0.07
_µ_ Cep 5.13 [(] _[d]_ [)] 3551 [(] _[d]_ [)] M2Ia [(] _[b]_ [)] 974 [(] _[d]_ [)] 17.5 [(] _[d]_ [)] 790 [(] _[i]_ [)] 31 21 600 [(] _[k]_ [)] 3.0 6 1.6
VX Sgr 5.01 [(] _[b]_ [)] 3535 [(] _[b]_ [)] M4eIa [(] _[b]_ [)] 855 [(] _[b]_ [)] 11 [(] _[e]_ [)] 1570 [(] _[b]_ [)] 6.5 22 3400 [(] _[l]_ [)] 25 28 13
VY CMa 5.48 [(] _[g]_ [)] 2800 [(] _[g]_ [)] M2/4II [(] _[b]_ [)] 1680 [(] _[f]_ [)] 25 [(] _[h]_ [)] 1200 [(] _[h]_ [)] 22.6 [(] _[g]_ [)] 35 [(] _[g]_ [)] 950 [(] _[g]_ [)] 80 [(] _[g]_ [)] 5 1.4


**Notes.** Listed are the stellar luminosity _L_ _⋆_, the effective temperature _T_ eff, the spectral type, the stellar radius R _⋆_, the initial mass _M_ ini, the distance
_D_, the local standard of rest velocity _v_ LSR, the terminal wind velocity _v_ _∞_, the radius of the CO envelope _R_ out, the gas mass-loss rate _M_ [˙] CO, the
mass-loss rate as predicted from Eq. (8), and the mass-loss rate predicted using the luminosity- _M_ [˙] -relation of Beasor et al. (2020) (Eq. (3)).
( _a_ ) From Joyce et al. (2020). Initial mass estimate ranges between 18–21 M _⊙_ .
( _b_ ) From De Beck et al. (2010).
( _c_ ) Current work.
( _d_ ) From Montargès et al. (2019). Initial mass estimate ranges between 15-20 M _⊙_ .
( _e_ ) From Tabernero et al. (2021). Initial mass estimate ranges between 10-12 M _⊙_ .
( _f_ ) From Zhang et al. (2012).
( _g_ ) From Decin et al. (2006); current mass-loss rate. For fitting the complex CO line profiles, Decin et al. (2006) invoked different shells with
varying mass-loss rate.
( _h_ ) From Wittkowski et al. (2012). Initial mass estimate ranges between 15-35 M _⊙_ .
( _i_ ) Estimates of _µ_ Cep’s distance vary between 390 _±_ 140 and 1818 _±_ 661 pc (Montargès et al. 2019, and references therein). We here take the average
value of the distance estimate of Montargès et al. (2021) (based on physical considerations on the relative size of the MOLsphere, _D_ = 641 [+148] _−_ 144 [pc)]
and of Davies & Beasor (2020) (based on the average parallax of neighbouring OB stars, under the assumption that the RSG is part of the same˙
association; _D_ = 940 [+140] _−_ 40 [pc).] [I.e.,] _[D]_ [ = 790 pc.] [For] [a] [change] [of] [distance] [from] [790 pc] [to] [390 pc,] [the] [retrieved] _M_ CO changes from 3 _×_ 10 _[−]_ [6] to
1 _×_ 10 _[−]_ [6] M _⊙_ /yr.
( _j_ ) The wind of Betelgeuse has various components. O’Gorman et al. (2012) proposes that the S2 flow of _α_ Ori extends out to a radius of 17 _′′_ (or
800 R _⋆_ ), although the measured intensity distribution of CO emission as a function of projected radius extends to _∼_ 8.5 _[′′]_ ( _∼_ 400 R _⋆_ ). Changing the
radius of the CO envelope from 800 R _⋆_ to 400 R _⋆_ changes the retrieved _M_ [˙] CO from 0.4 _×_ 10 _[−]_ [6] M _⊙_ /yr to 0.5 _×_ 10 _[−]_ [6] M _⊙_ /yr.
( _k_ )
Montargès et al. (2019) have used the NOEMA interferometer to get a channel map of the CO(2-1) emission of _µ_ Cep at a spatial resolution of
( 0 _l_ ) _[′′]_ _._ 92For _×_ a0 _[′′]_ _._ mass-loss72, with maximum recoverable scale (MRS) being 8rate around 2 _×_ 10 _−_ 5 M _⊙_ /yr, the predicted _[′′]_ CO. Emission is detected up tophotodissociation radius _∼_ is3 _∼_ _[′′]_ _._ 5 from the central star (or3500 R _⋆_ (Groenewegen & _∼_ Saberi600 R _⋆_ 2021)). or a full
extent of 17 _[′′]_ . The only CO interferometric data currently available for VX Sgr have been obtained in the framework of the ALMA ATOMIUM
large program. However, the MRS of those data is only _∼_ 8–10 _[′′]_ and hence cannot be used to estimate the CO envelope size. For that reason, we
resort to the predictions of Groenewegen & Saberi (2021).


Article number, page 28 of 29

L. Decin et al.: Mass loss from CO rotational line emission of red supergiants in RSGC1


**Fig. G.1.** CO rotational line transitions observed towards _α_ Ori (top panels), _µ_ Cep (middle panels), and VX Sgr (bottom panels) with the JCMT.
The CO(2-1), CO(3-2), and CO(4-3) data are plotted as red histograms. Synthetic line profiles are overplotted as black solid lines. The vertical
dashed grey lines indicate the LSR velocity. Accounting for the absolute flux uncertainty of _∼_ 30%, the JCMT data have been scaled by a factor,
indicated in the upper right corner of each panel.


Article number, page 29 of 29


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Positions, effective temperatures, bolometric luminosities, spectral types, stellar radii, distance, and v_LSR of RSGs in RSGC1",
  "failed_quote": "The effective temperatures, Teff, and stellar luminosities, Lbol, were taken from Davies et al. (2008); see Table 1."
 },
 {
  "path": "data.simulations_or_models_as_data[1].evidence[0]",
  "value": "1D stellar evolution simulations of a 25 Msun star until core carbon depletion computed with MESA",
  "failed_quote": "The MESA evolutionary code (Paxton et al. 2019) was used to compute the evolution of a 25 M⊙ star until core carbon depletion."
 },
 {
  "path": "processing.inherited[5].what.evidence[0]",
  "value": "Convective overshooting, main-sequence wind, Wolf-Rayet wind, and solar metallicity prescriptions in MESA stellar evolution models",
  "failed_quote": "Following Brott et al. (2011), overshooting was modelled by extending the convective region by 0.335 pressure scale heights, while winds during the main sequence and the Wolf-Rayet phase are modelled using the prescriptions of Vink et al. (2001) and Hamann et al. (1995)."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "CO line profiles are intrinsically symmetric around v_LSR, so the uncontaminated red wing can be used to assess ISM contamination on the blue side",
  "failed_quote": "Therefore, the red part of the line profile can also be used to assess the ISM contamination at lower velocities, since the CO line profiles are expected to be symmetric."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Re-fit individual cluster Mdot_SED-L_bol relations using IDL FITEXY, then perform multivariate linear least-squares fits with MPFIT and 10^4 Monte Carlo realisations to jointly fit Mdot_SED (across RSGC1, NGC 2100, NGC 7419, chi Per) and Mdot_CO (for F01-F04 in RSGC1) as a function of L_bol and M_ini.",
  "failed_quote": "We repeat the analysis applying the same IDL routine FITEXY and using the most conservative error estimates for both Lbol and M˙ SED (see Table E.1)."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Common luminosity slope b and initial-mass slope S across all clusters; F13 is excluded as an outlier experiencing a different mass-loss mechanism",
  "failed_quote": "Similar to the analysis of Beasor et al. (2020), we exclude F13 from the regression analysis since it stands out in the sample of 14 RSGs in RSGC1: F13 is unusually red, has an M˙ CO being an order of magnitude larger than the other four RSGs detected in CO(2-1), and is the only source for which the observed CO envelope size is much lower than any prediction for CO photodissociation in a circumstellar envelope (see Sect. 3.1)."
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Tested sensitivity to choice of reference cluster intercept (Appendix F) and validated Eq. (8) against Galactic M-type RSGs (alpha Ori, mu Cep, VX Sgr) observed with JCMT in multiple CO transitions (Appendix G).",
  "failed_quote": "To assess the predictive power of Eq. (8), we have compared its predicted M˙ -values with M˙ CO-values derived for some well-known Galactic M-type supergiants towards which several rotational CO lines have been observed (α Ori, µ Cep, VX Sgr, and VY CMa; see App. G)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Compute stellar evolutionary tracks of a 25 Msun star until core carbon depletion using MESA comparing the new RSG mass-loss prescription (Eq. 8) with Nieuwenhuijzen & de Jager (1990), and perform a Bayesian binomial analysis of the fraction of RSG lifetime spent in the strong mass-loss stage.",
  "failed_quote": "The MESA evolutionary code (Paxton et al. 2019) was used to compute the evolution of a 25 M⊙ star until core carbon depletion."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Initial mass = 25 Msun; convective overshooting = 0.335 pressure scale heights; switch to RSG wind recipe below T = 10^4 K",
  "failed_quote": "Following Brott et al. (2011), overshooting was modelled by extending the convective region by 0.335 pressure scale heights, while winds during the main sequence and the Wolf-Rayet phase are modelled using the prescriptions of Vink et al. (2001) and Hamann et al. (1995). For temperatures below 104 K we switch to either the prescription of Nieuwenhuijzen & de Jager (1990) or the newly derived one from Eq. (8)."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Linear regression fitting via FITEXY",
  "failed_quote": "We repeat the analysis applying the same IDL routine FITEXY and using the most conservative error estimates for both Lbol and M˙ SED (see Table E.1)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Fitting linear Mdot_SED-luminosity relations for individual clusters accounting for errors in both coordinates",
  "failed_quote": "We repeat the analysis applying the same IDL routine FITEXY and using the most conservative error estimates for both Lbol and M˙ SED (see Table E.1)."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Computing stellar evolutionary tracks of a 25 Msun star until core carbon depletion",
  "failed_quote": "The MESA evolutionary code (Paxton et al. 2019) was used to compute the evolution of a 25 M⊙ star until core carbon depletion."
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Upper limit on Mdot_CO for undetected RSGC1 RSGs = 7e-7 M_sun/yr",
  "failed_quote": "For the RSGC1 red supergiants that remained undetected in the CO(2-1) line, an upper limit on the mass-loss rate of ∼7×10−7 M⊙/yr is derived."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[2]",
  "value": "Small number statistics and sample bias towards the brightest/highest mass-loss RSGs in RSGC1 (only 5 of 14 RSGs detected in CO(2-1); Band 9 CO(6-5) was not observed, leaving only a single CO transition that cannot constrain the radial temperature profile independently).",
  "failed_quote": "Despite of (i) the caveat of dealing with small-number statistics, and (ii) the fact that we are dealing with the 3 RSGs in RSGC1 that have the largest M˙ SED-values from the study of Beasor et al. (2020), we can try to improve on the mass-loss rate prescription derived in Eq. (6)."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[1]",
  "value": "ISM CO contamination affects the blue-shifted velocities of the line profiles, and total CO envelope sizes are sensitivity-limited lower limits.",
  "failed_quote": "It is more challenging to estimate the total size of the CO emission, since our observations are sensitivity-limited and provide a lower limit."
 }
]
```
