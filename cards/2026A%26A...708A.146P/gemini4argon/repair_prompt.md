# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...708A.146P\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aanda ©ESO 2026
October 8, 2026

## **MUSE-ALMA Haloes**

### **XIV. The ALMA Large Programme Data Release**


Céline Péroux [1][,][ 2] [⋆], Jianhang Chen [3], Victoria Bollo [1], Tamsyn O’Beirne [1][,][ 4][,][ 5], Capucine Barfety [3], Simon Weng [2], Ramona
Augustin [6], Benedetta Casavecchia [7], Martin Zwaan [1], Linda Tacconi [3], Natascha Föster Schreiber [3], Laurent Chemin [8],
Varsha Kulkarni [9]


1 European Southern Observatory, Karl-Schwarzschild-Str. 2, 85748 Garching near Munich, Germany
2 Aix Marseille Univ., CNRS, LAM, (Laboratoire d’Astrophysique de Marseille), UMR 7326, 13388 Marseille, France
3 Max-Planck-Institut für Extraterrestrische Physik (MPE), Giessenbachstrasse 1, 85748 Garching, Germany
4 Centre for Astrophysics and Supercomputing, Swinburne University of Technology, Hawthorn, Victoria 3122, Australia
5 CSIRO Space and Astronomy, PO Box 1130, Bentley WA 6102, Australia
6 Leibniz-Institut für Astrophysik Potsdam (AIP), An der Sternwarte 16, 14482 Potsdam, Germany
7 Max-Planck-Institut für Astrophysik (MPA), Karl-Schwarzschild-Str. 1, 85741 Garching, Germany
8 Observatoire Astronomique de Strasbourg - UMR 7550, 11 rue de l’Université, 67000 Strasbourg, France
9 Department of Physics and Astronomy, University of South Carolina, Columbia, SC 29208, USA


Received XXX; accepted XXX


**ABSTRACT**


The interactions between gas and galaxies are of paramount importance to our understanding of structure formation. A fundamental
element of such baryon cycle studies is a complete census of the condensed matter (stars and cold gas) in both galaxies and their
immediate surroundings, the so-called circumgalactic medium. Of particular importance are the processes of converting molecular
gas into stars and deciphering whether this <100K gas is tracing gas flows. The MUSE-ALMA Haloes survey has assembled probes
of the neutral atomic gas H i, ionised gas and stellar component for a sample of 79 z∼0.5 galaxies. This is achieved by combining
absorption line spectroscopy of background quasars with projected impact parameter as low as 5 kpc and up to 250 kpc to probe
the low density circumgalactic gas with emission line tracers of both ionised gas and stars. This paper presents the Large Programme
observational set-up and releases the data characterising the molecular phase of some of the MUSE-ALMA Haloes targets so as to
reach a complete census of their condensed baryons. ALMA’s unique millimetre coverage and high sensitivity is ideal to characterise
the CO emission of these z∼0.5 H i-selected galaxies. By measuring the molecular mass, kinematics, gas flows and gas fractions,
this project then: i) quantifies the role of molecular gas in H i-rich galaxies, ii) characterises the molecular phase of gas flows from
morpho-kinematics analyses, and iii) establishes a census of the condensed baryons in the interstellar and circumgalactic media.
Ultimately, these results will provide unique insights into the baryon cycle - a crucial component of galaxy formation.


**Key words.** molecular gas – galaxy evolution – star formation – ISM – high-redshift



**1.** **Introduction**


The mass-energy census of the cosmos is now well constrained.
The vast majority of the Universe’s constituents are in the form
of dark energy and dark matter which are subjects of major research. The total amount of normal baryonic matter is well measured by at least three independent techniques probing the Universe at different epochs: small temperature fluctuations in the
cosmological background spectral energy distribution (Planck
Collaboration et al. 2016), abundance of heavy elements produced during the Big Bang Nucleosynthesis (Cooke et al. 2014)
and dispersion measures of Fast Radio Bursts (Macquart et al.
2020). However, only a minority of the remaining normal baryonic matter can be probed by the observations of starlight within
galaxies (Shull et al. 2012; Nicastro et al. 2018; Mathur et al.
2021; Das et al. 2021), because a major reservoir of the baryons
are in the form of gas (Péroux & Howk 2020).


⋆ Email: cperoux@eso.org



The gas is of prime interest since it flows along the cosmic
filaments and feeds the formation of galaxies, groups and clusters. Indeed, galaxy formation is fed by inflows of gas from the
intergalactic medium or IGM (Dekel et al. 2009). Baryons from
the cosmic web accrete onto galaxies, where they cool into a
dense atomic and later molecular phase, which acts as the fuel
for star formation. Once stars are formed, galaxies interact with
the IGM by polluting it with ionising photons and chemical elements formed in stars and supernovae through galactic winds
(Pettini 2003; Shull 2014; Danforth et al. 2016). Understanding the drivers of the cold gas accretion rate onto galaxies, the
efficiency of converting molecular gas into stars and the role of
outflowing gas in preventing the infall of new accreting material,
has assumed increasing importance in galaxy formation studies.


Therefore, galaxy evolution is strongly driven by the physical processes by which the gas flows inside and outwards of
the galaxy, is converted into stars and either ejected out through
winds or recycled to form a new generation of stars. In particular,
the condensed forms of this gas, notably the cold gas traced by


Article number, page 1 of 18

_A&A proofs:_ manuscript no. aanda



molecular hydrogen, provide the ultimate reservoir of fuel for
forming stars. This cosmic baryon cycle describes the motion
and phase transformation of the baryons (Tacconi et al. 2020;
Walter et al. 2020). These global processes take place in the immediate surrounding of galaxies, thus constituting the so-called
"galaxy baryon cycle" (Péroux & Howk 2020).
The sites of these multi-phase gas exchanges are the immediate surroundings of galaxies, the circumgalactic medium or
CGM (Tumlinson et al. 2017; Peroux & Nelson 2024). With
the advent of precursors of the future Square Kilometre Array
Observatory (SKAO) like MeerKAT (Jonas & MeerKAT Team
2016) or ASKAP (Johnston et al. 2008), surveys aim at detecting
the extended reservoir of low density H i emission around galaxies in the local Universe that are likely responsible for the cold
gas accretion. For instance, the MHONGOOSE H i observations
on MeerKAT (de Blok et al. 2024) is the deepest survey ever
made at 21 cm, spanning M H i = 10 [7] to 10 [11] M ⊙ . One of the key
outcomes of MHONGOOSE is the paucity of low density H i
emission in the atomic gas around galaxies (Marasco et al. 2025;
Veronese et al. 2025), in contrast with expectations from cosmological hydrodynamical simulations. Such a study demonstrates
the need for even more sensitive observations with the SKAO to
reach densities at least an order of magnitude deeper to search
for large amounts of H i gas in isolated clouds, dwarf galaxies
or potential cosmic filaments of neutral hydrogen (de Blok et al.
2024).
An alternative powerful tool to study the cooler phase of that
gas is provided by absorption lines in the spectra of background
quasars as it enables to study regions of under-dense gas (Morris
et al. 1993; Tripp et al. 1998). Indeed, in these quasar absorbers,
the minimum gas density that is probed is set by the brightness
of the background source and thus independent of the redshift
of gas studied. Thus, quasar absorption lines have proven invaluable to probe the neutral atomic gas of foreground galaxies
that would be otherwise too diffuse to be detected (Péroux et al.
2017; Augustin et al. 2018). Recently, 3D Integral Field Spectroscopy, producing data cubes where each pixel on the image
has a spectrum, has proven to be a true game-changer to detect in emission the ionised gas in the circumgalactic medium
of these foreground galaxies. For example, the Guaranteed Time
Observations program MEGAFLOW used Mg ii absorbers in 22
quasar fields to characterise the geometry, kinematics, and impact of gas flows around star-forming galaxies (Bouché et al.
2025). A primary finding of MEGAFLOW is that the cool halo
gas traced by Mg ii absorption is not isotropically distributed
around galaxies. Instead, it shows a strong bimodal distribution in the azimuthal angle relative to the galaxy’s major axis
(Schroetter et al. 2019). By assuming that absorbers near the
minor axis probe outflows (Péroux et al. 2020) and making assumption on _N_ (H i), MEGAFLOW has placed constraints on the
properties of gas flows, including mass loading factor (the ratio
of the mass ejection rate in the wind to the galaxy’s star formation rate). MUSEQuBES is another Guaranteed Time Observations program which uses MUSE to study the CGM of galaxies (Muzahid et al. 2020; Dutta et al. 2024). MUSEQuBES uses
other metal tracers, namely O vi absorption, to study the highly
ionised CGM around low-mass, dwarf galaxies at lower redshifts
(Dutta et al. 2024). This gas is found to be gravitationally bound
to the galaxies and the averaged O vi column density around
low-mass galaxies ( _M_ ⋆ < 10 [8][.][7] ) is significantly lower than that
around more massive galaxies (Dutta et al. 2025a,b). A significant portion of the survey focuses on characterising the CGM of
Lyα emitters at a redshift of z ∼ 3.3, which additionally enables
estimating constraints on the H i column density of the absorbers


Article number, page 2 of 18



from ground-based observations. The survey found significant
excess H i and C iv absorption in the CGM of these Lyα emitters,
extending out to at least 250 pkpc, which corresponds to about 7
times the virial radii of these galaxies (Muzahid et al. 2021). A
key finding is the strong influence of the galactic environment on
the CGM. Lyα emitters which are part of pairs or groups show
significantly stronger absorption and a higher gas covering fraction compared to isolated galaxies (Banerjee et al. 2023, 2025).
The MAGG survey instead investigates the connection between
optically thick gas and galaxies in the early Universe, specifically at redshifts z = 3-4 (Lofthouse et al. 2020, 2023; Galbiati et al. 2024). The survey has shown that Lyα emitters are
situated within cosmic structures that contain multiphase gas,
varying in composition and temperature (Galbiati et al. 2024).
The properties of these gas phases are strongly influenced by the
large-scale galaxy environment, with the strength and kinematics
of the gas correlating positively with the number of associated
galaxies (Galbiati et al. 2024). To benefit from the information
provided by H i at lower redshift, another survey dubbed CUBS
uses absorption-line spectroscopy of 15 UV-bright background
quasars observed with COS and WFC3 to map with MUSE the
diffuse gas in and around galaxies at redshifts z < 1. CUBS has
shown that Lyman Limit Systems (LLSs) originate in diverse
settings, including the halos of low-mass dwarf galaxy pairs,
the extended gaseous disks of star-forming galaxies, the vicinity
of massive quiescent galaxies, and within galaxy groups (Chen
et al. 2020). Recently, signatures of inflows and outflows have
also been reported from emission studies also using the KCWI
instrument on Keck (Guo et al. 2023; Pessa et al. 2024; Erb et al.
2023).


Complementary to these efforts, recent years have also seen
the development of similar approaches at mm wavelengths. Despite its modest primary beam, ALMA can be seen as a 3D spectrograph since it provides simultaneously frequency and spatial
information. On top of the early efforts of the MUSE-ALMA
Haloes survey itself (Klitsch et al. 2018; Péroux et al. 2019),
Kanekar et al. (2018) focus on the nature of galaxies that give
rise to high-metallicity damped Lyman-α (DLA) absorption systems at intermediate redshifts (z = 0.5–0.8) by searching for carbon monoxide (CO) emission, a tracer of molecular gas, from
seven of these absorption-selected galaxies. The authors report
high molecular gas fractions, the ratio of molecular gas mass to
the total baryonic mass, and low SFR in the five systems they
detect. Interestingly, Klitsch et al. (2021) report a high detection
rate in the detection of CO emission in the fields of 6 H 2 -bearing
absorbers. Again, they find that the majority of the H 2 absorbers
are associated with multiple galaxies rather than single, isolated
galactic halos. Recently, Neeleman et al. (2025) presented the results of a survey studying galaxies associated with damped Lyα
absorbers (DLAs) at a redshift around 4. The study found that the
ability to detect the host galaxies of these DLAs in [C ii] emission is strongly dependent on the metallicity of the absorbing gas
itself. The detection rate is high (71%) for DLAs with a metallicity [M/H] > −1.5, but zero for those with lower metallicities.
Otherwise, they find that the detected galaxies have properties
similar to typical star-forming galaxies at this high redshift.


By combining 3D information from both optical and millimetre wavelengths, the MUSE-ALMA Haloes survey builds on
both these lines of effort. With the additional high-spatial resolution imaging enabled by space missions, the stellar continuum
for the same objects is now robustly traced despite the light contamination from the bright background quasar (Augustin et al.
2018; Karki et al. 2023; Augustin et al. 2024; Karki et al. 2026).

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP



Without a quantitative description of the molecular phase however, one cannot reach a full understanding of the baryon cycle.
In this context, this paper introduces the ALMA Large Programme component of the MUSE-ALMA survey whose goal
is indeed to probe the molecular phase of an otherwise wellstudied sample of z∼0.5 galaxies. The overarching objective of
the MUSE-ALMA Haloes project is to use multi-wavelength information to probe the physical processes by which gas is transformed into stars through the baryon cycle. This paper is organised as follows. In Section 2, we describe the selection of
the MUSE-ALMA Haloes targets. Section 3 presents the multiwavelength complementary datasets and the physical properties they constrain. Section 4 describes the ALMA observations,
while Section 5 specifically details ALMA Large Programme
survey design, describes the observational set-up and an extensively reports on the data reduction processes. Section 6 introduces the release of the resulting data products, while Section 7
summarises the science goals of the programme. Finally, Section 8 provides our key conclusions. Throughout this paper, we
use _H_ 0 = 70 kms [−][1] Mpc [−][1], Ω M = 0.3 and Ω Λ = 0.7.


**2.** **The MUSE-ALMA Haloes primary target selection**


The MUSE-ALMA Haloes survey is a multi-facility programme
conducted through various distinct observing campaigns over
the years. Several similar efforts have come to fruition recently.
This includes the impressive PHANGS which is a large, multiwavelength observational program designed to build a comprehensive dataset for studying star formation and the interstellar
medium (ISM) across a representative sample of nearby spiral
galaxies (Schinnerer et al. 2019; Lang et al. 2020; Leroy et al.
2021). By combining data from ALMA, MUSE, HST, and now
JWST, PHANGS enables a multi-phase, multi-scale investigation of the entire star formation cycle (Barnes et al. 2023; Lee
et al. 2023). Likewise, MAUVE is a MUSE and ALMA multiwavelength program designed to investigate how the cluster environment shapes the gas–star formation cycle in galaxies falling
into the Virgo Cluster (Watts et al. 2024). MAUVE aims to characterise the interstellar medium, stellar populations, and star formation activity in 40 late-type Virgo Cluster galaxies at various
stages of infall. The upcoming KILOGAS survey which combines maps at 1 kpc resolution in a sample of over 400 galaxies with available optical integral field spectroscopy from the
MaNGA and SAMI surveys, provides resolution-matched SFR,
metallicity, and stellar maps, as well as ionised gas and stellar
kinematics. In the future, with the availability of new channels
across observatories [1], such multi-wavelength approach is likely
to be key to unveil multi-phase physics in various galactic media.
The MUSE-ALMA Haloes survey uniquely provides accurate information on the H i content and metallicity of the CGM of
its targets. Because of the asynchronous nature of the proposing
cycles, the target selection of the MUSE-ALMA Haloes sample
has been evolving as new information has become available.
In a nutshell, the quasar absorbers of the MUSE-ALMA
Haloes survey were selected on HST/UV spectroscopy to have
the H i column density, log [N(H I)/cm [−][2] ]>18 and _z_ abs < 0.85.
The first of these two elements of the selection is key to enable robust absorption metallicity measurements (Halley et al.
2026) and gas mass estimates in galactic flows (Rahmani et al.
2018b). Indeed, we emphasize that knowing accurately the H i
column density in absorption is key to measure precisely the neutral gas metallicity and assess the potential gas ionisation correc

1 `www.eso.org/sci/observing/phase1/JointVLT-ALMA.html`



**Fig. 1.** MUSE-ALMA Haloes surveys in the context of other comparable efforts. This figure reports surveys targeting quasar absorbers with
known _N_ (H i) column densities as a function of redshift (this work,
Muzahid et al. 2020; Chen et al. 2020; Lofthouse et al. 2023; Erb et al.
2023; Kanekar et al. 2018; Klitsch et al. 2021; Neeleman et al. 2025).
"IFU" refers to both VLT/MUSE and Keck/KCWI. Symbol sizes are
proportional to the number of targets in each surveys. On top of the
sizeable sample, the MUSE-ALMA Haloes survey uniquely combines
3D observations at optical and millimetre wavelengths to enable studies
of the multi-phase gas.


tion (Halley et al. 2026). In addition, _N_ (H i) is a key component
of the estimate of the mass loading factor (Bouché et al. 2013;
Schroetter et al. 2015). This selection criterion adds to other surveys focusing on metal lines (Bouché et al. 2025; Dutta et al.
2025a).
On the other hand, the redshift criterion of the target selection enables both accurate redshift measurements and kinematic
reconstruction (Szakacs et al. 2021; Weng et al. 2023a). This
redshift range enables the robust determination of both the systemic redshift based on narrow emission lines (as opposed to
the resonant Lyα line), as well as the star formation rates and
emission metallicity of these galaxies based on rest-frame optical emission diagnostics. Furthermore, at low-redshift, the larger
apparent size and increased surface brightness enable kinematic
reconstruction of the objects. Finally, the redshift range set to be
_z_ abs < 0.85 complements other efforts at _z_ - 3 (Muzahid et al.
2021).
At the start of the survey, the sample resulting from this selection comprises 32 individual absorbers in 19 distinct quasar
fields (i.e. multiple absorbers per quasar spectra) which are
dubbed "primary targets". Figure 1 presents this number of targets in context of similar surveys targeting quasar absorbers with
known _N_ (H i) column densities as a function of redshift (Muzahid et al. 2020; Chen et al. 2020; Lofthouse et al. 2023; Erb et al.
2023; Kanekar et al. 2018; Klitsch et al. 2018; Neeleman et al.
2025). On top of the sizeable sample, the MUSE-ALMA Haloes
survey uniquely combines 3D observations at optical and mmwavelengths to enable studies of the multi-phase gas.
Archival and new proprietary observations with VLT and
Keck provide additional optical spectroscopy of the background
quasars. All the quasar spectra are observed at high-spectral resolution but one (Q1110+0048 which contains one absorber) due
to the lack of completion of the UVES PI-run. This makes a
sample of 18 quasar fields, with 31 absorbers.


Article number, page 3 of 18



10 [21]


10 [20]


10 [19]


10 [18]


10 [17]


10 [16]


10 [15]


10 [14]


10 [13]



0 1 2 3 4

Redshift

_A&A proofs:_ manuscript no. aanda


**Fig. 2.** MUSE-ALMA Haloes number of targets covered by various observing campaigns. This figure provides a graphical viewing of the numbers
listed in Table 1. The left, middle and right panels illustrate the number of quasar fields, quasar absorbers and galaxies associated with the quasar
absorbers observed by each facility.



**Table 1.** MUSE-ALMA Haloes number of targets covered by various
observing campaigns.


Facility # quasar # absorbers # associated
fields galaxies
HST spectroscopy 19 32 –
UVES/HIRES spec 18 31 –
VLT/MUSE 19 32 79
HST imaging 18 30 79
ALMA 17 25 _[a]_ 60 _[b]_


Note: The table summarises the number of quasar fields, total
number of absorbers in all quasar fields, and galaxies associated with the absorbers in all quasar fields observed by each facility. The quasar fields were initially selected from HST UVspectroscopy, with additional or followed-up observations from
the ground with either Keck or VLT. The associated galaxies
were identified with MUSE and HST imaging, while to optimise
the survey strategy given the size of the primary beams, ALMA
observations targeted a subset of the known galaxies.
_a_ 17 (out of these 25) absorbers were observed as part of the
ALMA Large Programme.
_b_ 39 (out of these 60) associated galaxies were observed as part
of the ALMA Large Programme.


All 19 fields are followed-up with VLT/MUSE to detect in
emission the galaxies associated with the absorbers with impact parameters ranging from b=0 kpc for emission-line objects
(thanks to spectral-PSF subtraction, see Péroux et al. 2019) to
∼250 kpc for all galaxies. Seventy-nine such emitters are detected within ± 500 km/s of the absorber redshift (Weng et al.
2023b). An HST medium broad-band imaging program characterised the stellar content of all these objects but for one quasar
field (Q0058+0019 with 2 absorbers but no galaxies identified
in the VLT/MUSE observations). This leads to a sample of 18
quasar fields, with 30 absorbers and the full 79 associated galaxies. The ALMA observations spread over several cycles to cover
all these fields but one (Q2353−0028 which is found to have
no associated galaxies within 500 km/s in the MUSE observations). Because of the restricted primary beam however, not all
the known associated galaxies detected in MUSE are targeted


Article number, page 4 of 18



with ALMA. The final sample thus contains 17 quasar fields, together containing 25 absorbers. These absorbers are associated
with 60 distinct galaxies. Thirty-nine of these galaxies have been
targeted by the ALMA Large Programme presented in this paper. These samples are listed in Table 1 and illustrated by the
Venn diagrams displayed in Figure 2. In addition to the "primary
targets", a total of 3658 galaxies are detected in the MUSE and
HST datasets and are the subject of parallel studies (Péroux et al.
2022).


**3.** **The MUSE-ALMA Haloes multi-facilities datasets**


In the MUSE-ALMA Haloes survey, several distinct observational campaigns provide information on the multi-phase interstellar and circumgalactic media of the galaxy sample. Indeed,
the project combines absorption and emission data probing the
atomic, molecular and ionised gas as well as stellar populations
in these z∼0.5 objects. This section reviews these datasets complementary to the ALMA observations and the physical properties they constrain. Table A in Appendix lists the MUSEALMA Haloes survey publications to date. The overall approach
is schematically illustrated by Figure 3, a sketch partially AIgenerated with FigureLabs [2] .


_3.1._ _Atomic gas_


3.1.1. Neutral hydrogen gas from space-based UV
spectroscopy


Each background quasar has archival HST/UV spectroscopy
providing reliable N(H I) measurements of the strong intervening low-redshift absorbers with log [N(H I)/cm [−][2] ]>18. The observations were undertaken with either HST/FOS (Harms &
Fitch 1991), COS (Green et al. 2012) or STIS (Kimble et al.
1998). The H i column density measurements quantifies the neutral phase of the circumgalactic gas at an impact parameter of
the associated galaxies and provides accurate absorption redshift
measurements. For lower columns densities, where the gas could
be partly ionised, photo-ionisation models with the CLOUDY
software enabled robust estimates of the ionisation fraction of


2 generated on 12 [th] December 2025 with `[https://chat.](https://chat.figurelabs.ai/)`
```
figurelabs.ai/

```

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP





the gas (Halley et al. 2026). The resulting quantities are provided in columns 2 and 3 of Table B.1 and their distributions are
plotted in the left and central panels of Figure 4.


3.1.2. Gas-phase metallicity from ground-based optical
spectroscopy


Complementary to space-based HST/UV spectroscopy, groundbased spectroscopy of the background quasars provides additional information on the abundance, element ratio and dust
properties of the neutral circumgalactic gas. A number of existing spectra are available through the VLT and Keck archives
as displayed in the last column of Table 1 of Péroux et al.
(2022). Recently, most of the remaining quasars were observed
with VLT/UVES spectroscopy under a new program (ID: 113.A0369; PI: C. Peroux).

When available, archival Keck/HIRES, VLT/UVES and
VLT/X-Shooter data are used. The high-resolution quasar spectra are used to search for new quasar absorbers beyond the "primary targets". Sixteen such systems are discovered so that a total of 48 absorbers with _N_ (H i) measured are now available from
the MUSE-ALMA Haloes survey. These will be presented in a
forthcoming paper Halley et al. (2026). In addition, the quasar
spectra were used to measure the metal line column densities of
ions including FeII, SiII, SiIII, SiIV, dust-free ZnII, CIV from
Voigt profile fitting and performing ionisation and dust depletion corrections where needed (Halley et al. 2026). These highresolution data characterise the neutral circumgalactic gas metallicity. Early results from the archival data (Weng et al. 2023b)
indicate that the metallicity of associated galaxies is typically
larger than the absorber metallicity, which decreases at larger impact parameters. The resulting absorption metallicities are provided in columns 4 of Table B.1 and their distribution is plotted
in the right panel of Figure 4.


_3.2._ _Galaxy emission properties from optical 3D_
_spectroscopy_


3D Integral Field Units (IFU), which produces data cubes where
each pixel on the image has a spectrum, have provided a powerful technique to associate quasar absorbers with galaxies.
Building on early efforts with near-infrared IFU VLT/SINFONI
(Bouché et al. 2007; Péroux et al. 2011a,b, 2013), the potential



**Fig.** **3.** Sketch of multi-phase circumgalactic and interstellar media. The MUSEALMA Haloes uniquely probes the various component of the condensed baryonic matter as indicated in the labels:

neutral molecular & atomic and ionised
gas and stellar components of galaxies.
This is done through various observing
programmes gathering data from multifrequency facilities as indicated in colours.


of this technique for studying the CGM of intervening galaxies has grown with the availability of large optical IFU such
as VLT/MUSE and Keck/KCWI (Bouché et al. 2016; Péroux
et al. 2017; Zabl et al. 2019; Lofthouse et al. 2020; Nielsen
et al. 2020). Over several observing periods, the MUSE-ALMA
Haloes survey has used the VLT/MUSE in particular to identify
79 galaxies responsible for the strong z∼0.5 quasar absorbers
making up the "primary targets".
By detecting the galaxies in emission, it is possible to connect the circumgalactic gas seen in absorption with ionised gas
detected in emission. Indeed, the lower-density extended circumgalactic gas seen in absorption can then be connected with the
higher-density ionised gas detected in emission and likely located closer to/in the galaxies. Weng et al. (2023b) use the measurements of the redshifts and impact parameters (provided in
columns 5 and 6 of Table B.1) with respect to the background
quasars of the 79 detected galaxies to statistical map the neutral circumgalactic gas around galaxies. This work also reports
_N_ (H i) column density of the absorbers is anticorrelated with the
impact parameter (scaled by virial radius) of the nearest galaxy
as expected from simulations. Weng et al. (2023b) additionally
provide accurate estimates of the SFR and emission metallicities
of the objects as reported in column 7 and 9 of Table B.1 in the
appendix and plotted on the right and left panels of Figure 5. Furthermore, Weng et al. (2023a) make use of the 3D spectroscopy
to reconstruct the kinematics of the ionised gas and establish a
connection with the circumgalactic gas probed in absorption. Together these works report that 10% of absorbers are consistent
with gas accretion, a third trace outflows while the reminding
systems are associated with gas in the galaxy disk, the intragroup
medium or possibly low-mass galaxies below the MUSE detection limit. For comparison, the MEGAFLOW survey contains
79 strong MgII absorbers with 86 associated galaxies. Assuming that absorbers near the minor axis probe outflows, Schroetter
et al. (2019) report 26 galaxy–quasar pairs suitable for studying
winds (i.e. 30%). Keck/KCWI has also been used to study targetted galaxies with outflows (Chen et al. 2021; Erb et al. 2023).
IFUs thus provides a key element of probing the baryon cycle in
the MUSE-ALMA Haloes galaxies.


_3.3._ _Stellar properties from space-based broad-band imaging_


An essential component of the MUSE-ALMA Haloes project is
a Cycle 27 forty-orbit medium Hubble Space Telescope pro

Article number, page 5 of 18

_A&A proofs:_ manuscript no. aanda



6


5


4


3


2


1


0








|rim|Col2|
|---|---|
|rim<br>A t|rim<br>A t|
|rim<br>A t||



0.5 1.0

Redshift



18 19 20 21
Gas column density, log [N(HI)/cm 2 ]



3 2 1 0
Neutral CGM Metallicity [M/H]



**Fig. 4.** Properties of the "primary targets" observed with ALMA. _Left panel:_ Redshift distribution of the 32 quasar absorbers making up the primary
sample of MUSE-ALMA Haloes survey. The filled histogram (green) displays the redshift distribution of the 25 intervening absorbers targeted by
ALMA observations. _Middle panel:_ Atomic hydrogen gas column density distribution of these strong absorbers. The selection criterion imposes
the cut at log [N(H I)/cm [−][2] ]>18. _Right panel:_ Neutral gas absorption metallicity measured from archival and new VLT and Keck observations after
ionisation and dust correction Halley et al. (2026). The metallicity is the abundance of all metals, is expressed as [M/H] = log{N(M)/N(H)} −
log{N(M)/N(H)} ⊙ .



12


10


8


6


4


2


0









2 1 0 1
Star Formation Rate, log [M /yr]



8 10 12
Stellar mass [log M ]



8.2 8.4 8.6
Ionised gas metallicity [12 + log (O/H)]



**Fig. 5.** Properties of the associated galaxies. _Left panel:_ Star Formation Rate distribution of the 79 galaxies making up the MUSE-ALMA Haloes
survey. The filled histogram displays the SFR of galaxies observed with ALMA. _Middle panel:_ Stellar mass distribution _Right panel:_ Ionised gas
emission metallicity.



gramme (PI: C. Peroux) providing broad-band imaging with
WFC3 on both the optical (UVIS) and infrared (IR) detectors for
18 quasar fields. We also use an additional 27 orbits of archival
data recorded with WFPC2, making a total of 67 orbits dedicated to this part of the project. The properties of the objects
(catalogues of sky positions, magnitudes in different bands) have
been compiled and made publicly available (Péroux et al. 2022).
We have performed a detailed analysis of these datasets, providing measurements of the stellar mass, dust content, age of the
stellar population, as well as new constraints on their resolved
morphology and large-scale environment. The observations also


Article number, page 6 of 18



enabled the determination of the stellar masses of the associated
galaxies through spectral energy distribution fits (Augustin et al.
2024) and detailed morphological analysis (Karki et al. 2023).


Karki et al. (2023) find that absorption-selected galaxies are
consistent with the star formation main sequence of the global
population. This work combines multi-wavelength information
to demonstrate that more massive absorber counterparts are more
centrally concentrated and are larger in size. Karki et al. (2023)
further report that SFR surface densities of absorption-selected
galaxies are higher than predicted by the Kennicutt–Schmidt re
                                      lation for local galaxies, suggesting a higher star formation effi

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP



ciency in the H i-rich galaxies. Augustin et al. (2024) establish
that these objects probe a wide range of stellar masses: 8.1 <
log( _M_ ∗ /M ⊙ ) < 11.8, as illustrated in the middle panle of Figure 5.

−
The galaxy Q0454 220_4 stellar mass has been recently revised
to be M ∗ = 10 [10][.][6][±][0][.][1] M ⊙ . Given their star-formation rates, most
of these objects lie on the main sequence of galaxies.


Augustin et al. (2024) also confirm a previously reported
anti-correlation between the stellar masses and CGM hydrogen
column density _N_ (H i), indicating an evolutionary trend where
higher mass galaxies are less likely to host large amounts of neutral atomic H i gas in their immediate vicinity up to 120 kpc.
Recently, Karki et al. (2026) made use of HST deep imaging
and MUSE 3D spectroscopy combined to study the low-surface
brightness extended emission around some of the galaxies associated with quasar absorbers. The authors find that galaxies exhibiting these features have enhanced star formation rates, specific star formation rates, SFR surface densities, emission metallicities, and dust reddening compared to galaxies without extended features. These findings point at signatures of galaxy interactions and possible tidal streams. Karki et al. (2026) also note
that features have higher sSFR and higher ionisation parameters but lower SFR, lower emission metallicities, and lower dust
reddening than their host galaxies indicating a different physical
origin of the media.


_3.4._ _Molecular gas content from ALMA observations_


ALMA’s mm coverage and high sensitivity has proven powerful
to characterise the molecular emission of intervening galaxies.
Over the last decade, CO at z<4 and [CII] at higher redshift have
been used to detect in emission galaxies associated with strong
N(H I)-quasar absorbers. Neeleman et al. (2016, 2018); Augustin
et al. (2018); Møller et al. (2018); Fynbo et al. (2018); Neeleman et al. (2020); Kanekar et al. (2020) and others report the
ALMA observations of quasar absorbers in the range z=1–3. At
the same time, the MUSE-ALMA Haloes survey undertook several ALMA runs to probe and analyse the molecular content of
the associated galaxies. While the following section 4 will provide technical details on each of the ALMA datasets, this section
summarises findings from early studies.


Klitsch et al. (2018) used multiple CO transitions and mm
continuum detections to infer that the _N_ (H i) absorber in the

−
MUSE-ALMA Haloes Q0420 0127 quasar field traces either an
outflow from the most massive galaxy or intragroup gas. Péroux
et al. (2019) report 3 CO detections associated with another
MUSE-ALMA Haloes quasar absorber, finding long depletion
time-scales for the molecular gas and kinematics consistent with
the ionised gas. Szakacs et al. (2021) present observations of
another 6 absorbers associated with 9 galaxies, with multiple
galaxies in overdensity being related to the absorbers (see also
Klitsch et al. 2021). Szakacs et al. (2021) perform multi-phase
kinematic studies which show that the molecular and ionised gas
phases are well aligned directionally and that the maximum rotation velocities closely match. Their results demonstrate that the
two gas phases within the disk are strongly coupled. The authors
also report evidence for infalling gas. Together, these studies evidence the power of combining multi-wavelength datasets to gain
important information on the cool baryons in a bounded structures at intermediate redshift.



_3.5._ _Astrometry across multi-wavelength datasets_


A key component of the MUSE-ALMA Haloes survey is
the multi-frequency observational imaging campaign conducted
with VLT/MUSE, ALMA and HST. In order to intercompare
these various datasets, it is essential for the observations to be
recorded on a common astrometric frame. Specifically, detailed
studies of the kinematics of multi-phase gas traced by MUSE
and ALMA require accurate alignment (Péroux et al. 2019; Szakacs et al. 2021). Likewise, search for CO emission in ALMA
data based on MUSE and/or HST galaxy spatial position entailed
precise astrometry (Augustin et al. 2018; Bollo et al. 2026). For
all these reasons, we take the opportunity of the ALMA Large
Programme being completed to make a reappraisal of the astrometry across the various datasets presented in Section 3.


The absolute position accuracy of an ALMA image is theoretically limited by the accuracy of the phase calibrator position
and the quality of the phase transfer during the observations. The
latter depends on the weather conditions, the angle between the
phase calibrator and the centre of the targeted field, the cadence
of observations of the phase calibrator, and the level of errors in
the antenna position measurements. For observations of the type
of the ALMA MUSE Haloes survey, the position accuracy is less
than the synthesized beam width tabulated and greater than 0.1
arcseconds. Therefore, while the primary beam of the ALMA
observations is small with respect to the MUSE and HST images, the accuracy of the astrometry is the most suitable for all
datasets for our scientific purposes.


On the other hand, the HST broad-band images at hand
(Karki et al. 2023) provide large fields-of-view. As a result, a
number of bright objects, typically stars, are covered by each of
the space telescope pointings and in every filters. Based on previous experience (Péroux et al. 2019), we expect some of these
images to be slightly offset but also small rotation of the fields
around the central pointing are not unusual. Thanksfully, the
European Space Agency Gaia with its average high positional
accuracy of 0.05 milli-arcsecond provides an invaluable reference to evaluate the fidelity of the HST images. The Gaia Early
Data Release 3 (EDR3) which took place in December 2020 has
a significant astrometric (positions, parallaxes, proper motions)
and photometric (integrated G, GBP, GRP) improvements (Gaia
Collaboration et al. 2021). To solve for accurate and reliable astrometry, we use the positions of several stars detected both in
HST images and present in the Gaia catalogue. Whenever possible, we use 3 bright objects to solve for potential rotation of
the HST fields. The resulting offsets are sub-arcsec with a mean
value of 0.235 arcsec. After correction, we find the alignment of
our targets between the HST and ALMA data to be excellent.


Finally, the 1-arcmin squared MUSE field-of-view also often includes multiple bright objects. The MUSE individual subexposures were aligned with the ESO pipeline’s `exp_align`
recipe using these point sources resulting in an accurate relative astrometry in the combined single data cube (Péroux et al.
2022). To reach absolute astrometry, we now use the bright stars
to calculate the offset with respect to the corrected HST broadband images. The systemic offsets are in most cases smaller

∼
than the beam size ( 0.8 arcsec). In order to provide an uniform
dataset for various science projects across the collaboration, we
choose to edit the HST images and MUSE cubes header files
to correct to the Gaia DR3 astrometry. As a result, the multiwavelength observations of the MUSE-ALMA Haloes survey
are consistently aligned to the absolute astrometry newly provided by ALMA and Gaia DR3.


Article number, page 7 of 18

_A&A proofs:_ manuscript no. aanda



**4.** **The MUSE-ALMA Haloes ALMA observations**


_4.1._ _Primary targets from pilot programmes_


Before embarking into a Large Programme, the MUSE-ALMA
Haloes survey demonstrated feasibility of the observing strategy
by targeting a few selected "primary targets" in early Cycles. The
results of these observations have been presented in several publications, including Péroux et al. (2019); Klitsch et al. (2018);
Szakacs et al. (2021). Specifically, the quasar field Q1130−1449
was observed in Cycle 4 (PI: C. Peroux), while 9 more associated galaxies were part of a Cycle 5 programme (PI: C. Peroux).
Additionally, a Cycle 6 run (PI: A. Klitsch) targeted one more
quasar field (Q0420−0127). These early observations informed
the optimal strategy for the subsequent Large Programme.


_4.2._ _Primary targets from ALMACAL_


We further make use of ALMACAL to search for overlap with
potential MUSE-ALMA Haloes "primary targets". ALMACAL [3]
is a database of reprocessed ALMA phase and amplitude calibration scans (Bollo et al. 2024). In its latest release (ALMACAL22), the data accumulated from the start of ALMA operations
until May 2022 make up a total of over 2000 hours of integration time over a large area and at all frequencies. ALMACAL
has already enabled a number of specific science findings including measurements of the molecular gas mass density cosmological evolution free of cosmic variance (Klitsch et al. 2019a;
Hamanowicz et al. 2020; Bollo et al. 2025) as well as complete
mm number counts (Chen et al. 2023) and other scientific results (Klitsch et al. 2019b, 2020). The cross-match search between ALMACAL and MUSE-ALMA Haloes results in one target (Q0420−0127) with sufficient observations to enable detailed
study of the system (Klitsch et al. 2018), while more valuable
observations might become available in the future as part of the
ever-growing ALMACAL database.


_4.3._ _Primary targets from ALMA archives_


We also cross-match the ALMA public archives [4] with MUSEALMA Haloes "primary targets". This search led to multiple
matches as reported in Table 3 of Péroux et al. (2022). In particular, two of the MUSE-ALMA quasar fields (Q0058+0019
and Q0138−0005) have been observed with sufficient depth as
part of Cycle 1 (PI: X. Prochaska) and Cycle 3 (PI: N. Kanekar).
Kanekar et al. (2018) report results from these studies which are
included in the following analysis as part of the so-called previous ALMA observations.


_4.4._ _Primary targets from ALMA large programme_


In Cycle 10, we were awarded a Large Programme (PI: C. Peroux, V. Kulkarni, L. Chemin) to complement these early observations in an efficient way and provide information on the
molecular content of most of the MUSE-ALMA Haloes survey
"primary targets". The programme targeted 39 distinct galaxies
known to be associated with strong H i quasar absorbers identified with MUSE and HST. The design of the survey was made
efficient by aiming at several objects per pointings, also including mosaicing of some of the fields. Bollo et al. (2026) report on
the detections of these strong _N_ (H i) quasar absorbers and their
associated physical properties.


3 `[https://almacal.wordpress.com/](https://almacal.wordpress.com/)`
4 `[https://almascience.eso.org/aq/](https://almascience.eso.org/aq/)`


Article number, page 8 of 18



_4.5._ _Serendipitous detections from ALMA large programme_


In addition to the "primary targets" which correspond to MUSEdetected galaxies associated with strong _N_ (H i)-absorbers, the
ALMA Large Programme cubes contain a number of additional
emission line detections also augmented with multi-wavelength
observations. While these are not directly the targets of the primary sample, some of the science described in Section 7 is also
addressed by these serendipitous detections. These typically include CO emitters at intermediate redshifts, some of which are
extremely mm-bright, and are the focus of further studies (Klitsch et al. 2020; Chen et al. 2023). We refer to this sample as
the "serendipitous detections".


**5.** **ALMA large programme**


_5.1._ _Survey design_


The 61.5-hr ALMA Large Programme aims at characterising the
molecular properties of 39 z∼0.5 galaxies (see Table 1) associated with absorbers with known _N_ (H i). This efficient program
simultaneously covers several absorbers at different frequencies
and/or associated galaxies spatially as well as the background
quasar. The strategy of including the quasar in the field-of-view
improves the sensitivity of the observations by enabling selfcalibration hence maximising the detection sensitivity. In addition, Figure 6 provides examples where associated galaxies at
2 distinct redshifts (top row) were targeted and with multiple
ALMA positions including several objects per pointings (bottom row). Table 2 summarises the number of galaxies and the
number of pointings for each of the quasar absorbers.
For the choice of ALMA bands, we devised an observing strategy based on minimising the number of set-ups while
maximising the number of targets, and optimising atmospheric
conditions (hence schedulability) and detection sensitivity. We
targeted properly redshifted frequencies (∼150GHz) to probe
in band 4 CO(2−1) or in one occasion CO(3−2) ( _z_ abs =1.1532
towards Q0454+039). For two targets at higher redshifts
_z_ abs =0.8596 and 0.8999 (towards Q0454+039 and J1211+1030,
respectively), we have observed CO(4−3) in band 6. Table 2
provides a summary of the bands and specific frequencies used
for each quasar fields, which are also plotted in the third panel
of Figure 7. The band 4 primary beam (FWHM ∼44 arcsec;

∼
250kpc at the median sample redshift) corresponds to 75% of
MUSE field-of-view.
All fields were set to be observable with a minimum two distinct ALMA configurations thus maximising the schedulability
of the programme. The run made use of the configurations C3, C-4 and some C-2. This was achieved by choosing a range
of angular resolutions which have proven to enable kinematical
studies of such targets (Péroux et al. 2019; Szakacs et al. 2021;
Barfety et al. 2026). We set angular resolution ranging 0.57-1.02
arcsec to optimise the forward-modelling of the velocity field
and so as to enable comparison with the ionised gas probed in
emission with MUSE and the neutral circumgalactic gas probed
in absorption with VLT and Keck spectroscopy (Rahmani et al.
2018a). Based on early ALMA observations, the sizes of targets
were known to be significantly less than 5 arcsec so that there
were no issues with missing emission which is more extended
than the chosen largest recoverable scale (LAS) of 7 arcsec. The
final list of angular resolutions achieved for each of the ALMA
Large Programme fields can be found in Table 2 and its distribution is plotted on the second panel of Figure 7.
The observations were designed to reach a molecular mass
of log M H2 >9 M ⊙ assuming a Milky Way Spectral Line En

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP


**Fig.** **6.** ALMA Large Programme observing strategy. Example observations of the targeted fields Q1431−0050 and Q0152+0023. _Left_ _panel:_
Broad-band HST/WFPC2 imaging displaying the exquisite spatial resolution afforded by space observations. The top row illustrates cases where
they are distinct quasar absorbers at different redshifts with associated galaxies highlighted in blue and green. The purple star marks the position
of the background quasar labeled "QSO" in the middle panel. _Middle_ _panel:_ VLT/MUSE white light of the same fields showing the position of
the corresponding galaxies for which a spectrum is extracted. _Right_ _panel:_ ALMA observations of the same fields. The bottom row illustrates
that in ALMA band 4, several overlapping pointings (shown as red circles) are used to cover all the galaxies associated with the absorbers and
detected in HST and VLT/MUSE. The ALMA Large Programme observing strategy is thus optimised by targeting spectrally and spatially multiple
VLT/MUSE-detected galaxies.



ergy Distribution (SLED) to convert to CO(1−0) flux (Carilli &
Walter 2013), a galactic conversion factor to estimate molecular
mass of α _CO_ =4.6 M ⊙ (K km/s pc [2] ) [−][1] and the z=0.5 luminosity
distance of dL=2129 Mpc using a (0.3,0.7,0.7) cosmology. The
resulting exposure times ranged from 2.4 to 7.9 hrs, with most
of the targets being observed with shortest intergration times as
illustrated in the left panel of Figure 7. In some cases, the quasar
is bright at mm frequencies (>4 mJy), yet too faint to affect the
dynamical range of the data. The resulting RMS continuum sensitivity does not exceed 500 µmJy/beam in all cases as illustrated
in the right panel of Figure 7.


_5.2._ _Observations_


The MUSE-ALMA Haloes ALMA Large Programme was observed as part of Cycle 10 under ID: 2023.1.00127.L. The observations took place between late December 2023 and May 2024.
The observatory was extremely efficient in performing the obser


vations so that the time between the ALMA panel review results
are known to the proposers (Summer 2023) and the final observations are taken (Spring 2024) was remarkably short.


The observations were performed with one baseband in the
high resolution Frequency Division Mode (FDM), dual polarisation, but binned by a factor 4 to achieve a spectral resolution
of 15 km/s over a total bandwidth of 3600 km/s to resolve the
emission lines. The remaining three basebands are used in Time
Division Mode (TDM) in order to achieve good continuum sensitivity.


A journal of observations summarising the properties of the
ALMA Large Programme run is presented in Table 2. The table
includes exposure times, spatial resolution, targeted frequency
coverage and sensitivity achieved for each of the observations.


Article number, page 9 of 18

_A&A proofs:_ manuscript no. aanda


**Table 2.** The 17 quasar absorbers targeted with the ALMA Large Programme.


Quasar _z_ quasar _z_ abs log t _exp_ Resolution ALMA CO Frequency # galaxies # ALMA Sensitivity
_N_ (H i) RMS

[cm [−][2] ] [hr] ["] Band line [GHz] at _z_ abs pointings [µJy/beam]
J0152−2001 2.06 0.7802 19.10 3.7 0.99 4 2-1 129.52 1 1 227
Q0152+0023 0.59 0.4818 19.78 5.3 0.79 4 2-1 155.77 4 2 206
Q0454+039 1.34 0.8596 20.67 3.2 0.57 6 4-3 247.87 1 1 492
... ... 1.1532 18.59 2.8 0.85 4 3-2 153.68 2 1 198
Q0454−220 0.53 0.4744 19.45 2.4 0.81 4 2-1 156.83 1 1 243
... ... 0.4833 18.65 ... ... 4 2-1 155.77 1 ... ...
Q1110+0048 0.76 0.5604 20.20 2.4 0.85 4 2-1 147.78 3 1 173
J1211+1030 2.19 0.6296 20.30 2.7 1.02 4 2-1 141.43 2 1 215

... ... 0.8999 <18.50 6.3 0.87 6 4-3 242.65 3 3 292
Q1229−021 1.05 0.8311 18.84 4.4 1.01 4 2-1 125.98 4 1 219
Q1342−0035 0.79 0.5380 19.78 2.4 0.84 4 2-1 149.89 2 1 215
Q1345−0023 1.10 0.6057 18.85 2.4 0.95 4 2-1 143.58 2 1 268
Q1431−0050 1.18 0.6085 19.18 2.4 0.92 4 2-1 144.09 2 1 228
... ... 0.6868 18.40 2.4 0.94 4 2-1 136.41 2 1 245
Q1515+0410 1.27 0.5592 20.20 7.3 0.94 4 2-1 147.86 4 2 182
Q1554−203 1.95 0.7869 <19.0 3.5 1.00 4 2-1 129.01 1 1 199
J2131−1207 0.50 0.4298 19.50 7.9 0.92 4 2-1 161.24 4 2 206


Note: The table lists the redshifts and neutral gas column densities, _N_ (H i), as estimated from HST UV-spectra as well as the
number of galaxies with redshift matching _z_ abs, totalling to 39 objects. The penultimate column provides the number of ALMA
pointings required to efficiently cover all these targets. The ALMA primay beam in band 4 is 44 arcsec while it is 27 arcsec in
band 6.


7


6


5


4


3


2


1


0



4 6 8
Integration time, [hr]



0.6 0.7 0.8 0.9 1.0
Spatial resolution [arcsec]



150 200 250
Observed frequency [GHz]



200 300 400 500
RMS sensitivity [mJy/beam]



**Fig. 7.** ALMA Large Programme survey design. The histograms show the distribution of exposure time (first panel), angular resolution (second
panel), frequency (third panel), and noise in the continuum (fourth panel). These values are also tabulated in Table 2. The overall survey design is
rather homogeneous across quasar fields.



_5.3._ _Data reduction_


The data reduction and imaging largely followed the ALMA observatory guidelines. Specifically, we extract the calibrated measurement sets ( _ms_ ) produced with the Common Astronomy Software Applications (CASA, version 6.5.6) by the observatory. In
addition, we apply self-calibration when possible and produce
the images and datacubes with different weighting schemes and
channel widths.

In six of the observed fields, the background quasars are
bright enough at mm frequencies (≥ 4 mJy) to perform selfcalibration. Self-calibration corrects for short-term phase and
amplitude variations, resulting in a marked improvement in the


Article number, page 10 of 18



sensitivity hence dynamical range of the final images. We first
clean the continuum image of the quasar field interactively to
generate the clean model for self-calibration. During the first
round of interactive cleaning, we clean the quasar based on the
point source assumption. Then, we derive a phase-only calibration with various time intervals ranging from 30 seconds to 4
minutes, depending on the brightness of the quasar. We select
the time intervals based on the improvements in the final imaging products. We also apply amplitude self-calibration if the
quasar is brighter than 20 mJy and accepts the signals down to
5σ when constructing the clean models. During self-calibration,
the calibration tables are generated with the task gaincal and
apply to the pipeline-calibrated measurements using applycal.

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP



After self-calibration, the RMS sensitivity is improved by factors ranging from 1.1 to 7.6, compared to the ones without selfcalibration. Besides, our manual self-calibration also improves
the sensitivity by a factor of about 1.2 compared to the automated
observatory-based self-calibration pipeline products. In one of
the fields, Q2131−1207, the quasar is bright leaving some artifacts across the field-of-view. We use the CASA task uvcontsub
to remove the continuum contamination from the bright quasar
while excluding the line-emitting channels of our primary targets.
We then image the (self-)calibrated visibility into continuum
images and 3D images (datacubes) with the CASA task tclean.
For four of the quasar fields, several pointings are used to maximise the spatial coverage of the targets with known sky positions. The images of the mosaic fields are created by setting
the gridder to "mosaic". The images are created with two different weighting schemes. The "natural" weighting is used to
maximize the detection sensitivity, and the "Briggs" weighting
(robust=0.5) is used to achieve an optimal balance between sensitivity and spatial resolution. We chose two distinct velocity
resolutions. The 15 km/s resolution corresponds to the intrinsic spectral resolution. We further apply a spectral binning of
four channels to improve the signal-to-noise ratio, resulting in a
spectral resolution of 60 km/s. As a result, four different types of
images and datacubes are produced, for each of the two weighting schemes and each two of the spectral resolution choices. The
natural weighting with the 60 km/s products is better suited for
searches for line emissions, while the Briggs weighting with different velocity resolutions is better suited for detailed kinematic
analysis of the targets with strong line emissions.
The final RMS noise level of the cubes ranges from 180 to
500 mJy/beam and is typically < 250 mJy/beam. The resulting
angular resolution varies from 0.57 to 1.02 arcsec. The ALMA
primary beam in band 4 is 44 arcsec, while it is 27 arcsec in band
6. The sensitivity and angular resolution of each field are listed
in Table 2.
The search for emission lines was performed on the datacubes without primary beam correction. This provides a homogeneous apparent noise level across the field-of-view. After
we located the sources, their spectra were extracted from the
primary beam-corrected datacubes generated by impbcor, which
properly accounts for the increased noise level near the edge of
the fields. The spectra were extracted within CASA using different aperture sizes and position angles to optimize the final SNR
(Bollo et al. 2026). Fig. 5.3 displays an example of such spectrum. The left panel shows the whole ALMA field, while the
CO(2–1) spatial and spectral detection is reported in the middle
and right panels, respectively.


**6.** **Release of data products**


This paper accompanies the data release of the MUSE-ALMA
Haloes ALMA Large Programme datasets. Because of the legacy
value of the programme, we aim at enabling science beyond
the primary goals of the initial survey. In particular, the sample
additionally provides deep high spatial resolution observations
of mm-bright background quasars (Girdhar et al. 2022, 2024;
Molyneux et al. 2024). We therefore make the fully processed
data available to the whole community roughly two years after
the completion of the observing programme. The processed data
include value-added data products generated by the team. The
data products provided are:


**–**
raw data files.



**–** one README file for each set of enhanced data uploaded
(corresponding to a Group or Member OUS) in ascii (.txt)
format following the observatory-provided template.
**–** a detailed Data Description Document accompanying the
Group (or Member) OUS enhanced data package, which provides the user with a complete list of all the uploaded data
products and a description of their content. The document includes the project title and project code and provides detailed
descriptions of data files (and their provenance) contained in
the delivery. This file provides sufficient detail for a prospective user to reproduce the data reduction and understand the
multiple data sets within the products.
**–** the full combined cubes including the .pbcor. FITS files
according to ALMA standards, the corresponding .mask.,
and .pb. FITS files. The cubes are created with both natural
weighting to maximize the signal-to-noise ratio and Briggs
weighting with robust parameter set to 0.5. Both the spectral resolution of 15 km/s and the four-channel binned (corresponding to a spectral resolution of about 60 km/s) cubes
which improved signal-to-noise are available. Cubes are supplied in FITS format.


While the raw data are available through the ALMA Science Archive [5], the remaining of the products are made available through a dedicated ALMA page [6] . These enhanced data
products are “value added” and supplement the standard ALMA
products that are generated by the ALMA observatory and already stored in the ALMA Science Archive.
In addition, the present paper summarises in Section 3 the
"primary targets" absorption characteristics (redshift, H i column
density and neutral gas metallicity) and emission properties (impact parameter, SFR, stellar mass and ionised gas metallicity).
These values are listed in Table B.1 in the Appendix.


**7.** **Science goals of the ALMA large programme**


The MUSE-ALMA Haloes Large Programme aims at characterising the molecular gas phase of galaxies with robustly determined neutral atomic & ionised circumgalactic gas and stellar components. The overreaching goal is to constrain the full
baryon cycle of a sample of z∼0.5 galaxies. The study tackles
the following key questions:


**–** What role does molecular gas play in H i-rich galaxies? (Section 7.1)

**–**
How do molecular gas kinematics relate to gas flows? (Section 7.2)
**–** What is the condensed baryon census of the circumgalactic
medium? (Section 7.3)


_7.1._ _Quantify the molecular gas content of H I-rich galaxies_


One of the key findings of past observations with integral field
spectroscopy is that strong N(H I) absorbers are associated with
multiple galaxies detected with both VLT/MUSE and ALMA
(Hamanowicz et al. 2020; Dutta et al. 2020; Weng et al. 2023b).
This important conclusion is also supported by hydridynamical
cosmological RAMSES zoom-in and TNG simulations demonstrating that the physical properties of these objects are qualitatively similar to a small group environment, possibly part of a
cosmic filament (Péroux et al. 2019; Augustin et al. 2018; Weng


5 `[https://almascience.eso.org/aq/](https://almascience.eso.org/aq/)`
6 `www.eso.org/~cperoux/MUSE_ALMA_Haloes.html`


Article number, page 11 of 18

_A&A proofs:_ manuscript no. aanda


−
**Fig. 8.** ALMA Large Programme detection example. _Left panel:_ Full ALMA pointing for the Q0454 220 quasar field. The purple star marks the
position of the background quasar labeled "QSO". _Middle panel:_ Zoom-in on the CO(2–1) detection corresponding to the _z_ abs =0.4833 absorber.
The synthetised beam is indicated by the hashed area in the bottom left corner. _Right panel:_ Corresponding ALMA spectrum displaying the flux
emission at the expected frequency at 155.77 GHz. The detections of the full sample are reported in Bollo et al. (2026).



et al. 2024). This challenges the historical view of strong-N(H I)
quasar absorbers being associated with a single bright galaxy.
Instead, several lines of evidence suggest a situation where the
H I gas probed in absorption is related to complex galaxy structures (Klitsch et al. 2018; Hamanowicz et al. 2020). In addition to MUSE detections, ALMA observations have provided
new information on the molecular gas content of these systems
over the last decade. Building on these successes, the MUSEALMA Haloes survey ALMA Large Programme characterises
the molecular phase of the neutral gas of a sample of galaxies
associated with strong H I-absorbers. This dataset quantifies:


i) _CO_ _in_ _H_ i _-selected_ _galaxies_   - we efficiently target 39
galaxies with known sky positions and measured redshifts. What
makes this survey unique with respect to other projects, are accurate estimates of the SFR, metallicity and stellar mass of all
targets. Early studies (Péroux et al. 2019; Szakacs et al. 2021)
have demonstrated that the powerful combination of ALMA
and VLT/MUSE observations is pivotal to securely assess the
redshift of single-line mm detections. The ALMA Large Programme enables stacking analysis of emission lines to reach
even lower flux limits of typically 250 µJy km/s. These results can be contrasted with the latest hydrodynamical cosmological simulations including GRIFFIN (Lahén et al. 2020; Szakacs et al. 2022), COLDSim (Maio et al. 2022; Casavecchia
et al. 2024, 2025; Maio & Péroux 2026) or COLIBRE (Schaye
et al. 2025; Chaikin et al. 2025; Trayford et al. 2026) to constrain
which physical conditions (in terms of temperature and density)
of the gas CO best traces.


ii) _Detection_ _rate_   - some studies have focused their search
on metal-rich absorbers (Neeleman et al. 2016; Kanekar et al.
2018, 2020), whilst the sample targeted here has no prior on
metallicity. The ALMA Large Programme allows us to assess the
frequency of CO emitters down to log M H2 >9 M ⊙ among H Iselected galaxies using an unbiased sample, selected irrespective
of their metallicity. It additionally enables the assessment of the
incidence of "CO-dark" molecular gas, defined as regions where
H 2 exists without detectable CO emission due to low metallicity, reduced dust shielding, or diffuse, extended gas distributions
(Bollo et al. 2026). In case of non-detections, the ALMA Large
Programme is able to establish whether the ionised gas properties of CO detections and non-detections are different.


Article number, page 12 of 18



_7.2._ _Characterise multiphase gas flows_


Galaxy-scale processes through which galaxies accrete and convert their gas into stars need to be studied in selected objects in
order to obtain a complete picture of galaxy formation. In particular importance are the interactions between gas accretion (imposed by large-scale dark matter structures from IGM reservoirs)
and feedback (launched by star-forming regions in galaxies and
active supermassive black holes). It is thus key to study gas flows
into and out of galaxies simultaneously as their mutual interactions affect each other. In particular, characterising the physical processes of the inflows of gas accreting into galaxies and
the outflows carrying away the energy and metals generated inside galaxies. In this context, the MUSE-ALMA Haloes survey
ALMA Large Programme establishes the:


i) _Kinematics_ _of_ _molecular_ _gas_   - forward modelling of the
3-dimensional morpho-kinematics allows us to measure the gas
circular velocity at the position of the background quasar sighline. Software tools for such studies include GalPak [3D] (Bouché
et al. 2015, 2022), LINEFIT (Davies et al. 2011) and DysmalPy
(Davies et al. 2004b,a; Cresci et al. 2009; Wuyts et al. 2016;
Lang et al. 2017; Price et al. 2021; Lee et al. 2025). Dynamical
mass estimates reveal the physics behind the build-up of intermediate redshift galaxies. The ALMA Large Programme indeed
gathers new information on the orientation, geometry and kinematics of these galaxies. These observations, in concert with the
absorption profile along the sightline to the background quasar,
enable identifying signatures of gas flows departing from disk
rotation.


ii) _Ionised and molecular gas kinematics_   - VLT/MUSE and
ALMA observations combined offer an unprecedented view on
the kinematics of the ionised and molecular gas at comparable
spatial and spectral resolutions. The data sets also provide a still
rare opportunity to characterize the galactic cold molecular and
warm ionised gas kinematics _in_ _the_ _same_ galaxies, to address
in particular the issue of whether the associated gas components have similar local velocity dispersion with implications on
the physical driver of gas turbulence (feedback- and/or gravitydriven; e.g. Krumholz et al. 2018; Ginzburg et al. 2022). Specifically, by comparing the outflow velocities to SFRs, dynamical,
and stellar masses, the ALMA Large Programme investigates if

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP



inflow and outflow velocities differ in molecular and ionised gas
(Carniani et al. 2016; Herrera-Camus et al. 2025).


_7.3._ _A census of the circumgalactic medium condensed_
_baryons_


Péroux & Howk (2020) refer to the condensed matter as to the
sum of stars, dust, neutral and molecular gas components. The
cosmic evolution of its density is well measured by current observations. Péroux & Howk (2020) find that the observed z <
2 decline of the star-formation history is caused by the lack of
molecular gas supply related to a drop in net gas accretion rate.
This decline is itself driven by the decreased growth of the dark
matter halos. These observational results are in stark agreement
with the gas regulator model (Lilly et al. 2013; Peng & Maiolino
2014), which describes a continued cycling of baryons flowing
in and out of galaxies regulating galaxy evolution. Interestingly,
the neutral gas density dominates over that of the molecular gas
at all redshifts on global scales (Decarli et al. 2016; Walter et al.
2020; Hamanowicz et al. 2023; Bollo et al. 2025).
These results need to be reconciled with measurement of the
H i and H 2 gas content of galaxy on local scales. Indeed, galaxy
halos appear to be hiding approximately 60% of their baryons
compared to expectations from the cosmological mass density
(McGaugh 2008; Werk et al. 2014). With the wealth of multiwavelength information already available in the MUSE-ALMA
Haloes survey, we are in a unique position to perform a full census of the condensed baryons in these objects (O’Beirne et al.
2026). The ALMA Large Programme characterises the missing
component: the molecular content of these galaxies. As such the
ALMA Large Programme allows us to probe the:
i) _Molecular mass_   - the observations enable estimates of the
molecular masses from CO emission flux measurements, using
updated Spectral Line Energy Distribution (Klitsch et al. 2022)
and CO-to-H 2 conversion factors (Genzel et al. 2015). Combined
with known SFR estimates, these observations enable calculation of the rate of conversion of gas into stars, the so-called
molecular depletion times following: τ depl =M H2 /SFR=1/SFE,
where SFE is the star formation efficiency, a key link to the
baryon cycle. Recent studies of outer disk rotation curves at high
redshift indicate low galactic-scale dark matter mass fractions
f DM among massive star-forming disks, with higher fractions
derived towards lower masses (Genzel et al. 2017; Übler et al.
2018; Genzel et al. 2020; Price et al. 2021; Szakacs et al. 2021;
Bouché et al. 2022; Nestor Shachar et al. 2023; Puglisi et al.
2023). The ALMA Large Programme addresses this puzzle and
uniquely connects the molecular kinematics to the properties of
the dark matter halos at z∼0.5 and over a wide dynamic range in
galaxy mass. These observational results can be contrasted with
expectations of hydrodynamical cosmological simulations such
as TNG50 (Pillepich et al. 2019).
ii) _Baryonic and gas fraction_   - most recent CO-emission surveys such as COLD GASS (Saintonge et al. 2017) or the 2400
objects reported by PHIBBS (Tacconi et al. 2018, 2020) have informed us on the gas fraction of galaxies up to z∼4. The ALMA
Large Programme allows us to characterise the gas fraction of
less massive galaxies by reaching objects with stellar masses
M ∗ <10 [9] M ⊙ .


**8.** **Conclusions**


A complete understanding of the baryon cycle necessitates a
thorough inventory of condensed matter, comprised of stars and



cold gas, within both galaxies and their circumgalactic medium.
Today, the neutral atomic gas H i is best probed by the emerging technique of examining the gas in absorption against background sources whose lines of sight pass through an identified
foreground galaxy’s halo. Recent advancements in 3D Integral
Field Spectroscopy, which generates data cubes with a spectrum
for each image pixel, have significantly improved the detection
of ionised gas emission in the circumgalactic medium of these
foreground galaxies at both optical and mm wavelengths.
The MUSE-ALMA Haloes survey builds on these techniques to yield several key results regarding the connection between galaxies and their CGM. The survey has found a high detection rate of galaxies associated with H I absorbers, with 89%
of the targeted absorbers having at least one associated galaxy
within an impact parameter of 250 kpc (Péroux et al. 2017,
2019; Hamanowicz et al. 2020; Weng et al. 2023b). A significant finding is that most of these absorption systems are associated with pairs or groups of galaxies, indicating the importance
of the galaxy environment in shaping the CGM (Hamanowicz
et al. 2020). Interestingly, the galaxies with the smallest impact
parameters to the quasar sightline are not always the closest in
velocity space to the absorbing gas (Hamanowicz et al. 2020).
There is an anti-correlation between the H I column density of
the absorbers and the impact parameter (scaled by the virial radius) of the nearest galaxy, which is consistent with predictions
from simulations (Weng et al. 2023b). The metallicity of the associated galaxies is typically higher than the metallicity of the
absorbers. The absorber metallicity is also found to decrease
at larger impact parameters from the host galaxy (Weng et al.
2023b). The study found marginal evidence for a bimodal distribution in the azimuthal angles of strong H I absorbers, which
is similar to what has been observed for other absorption lines
like Mg II and O VI (Weng et al. 2023a). Detailed gas kinematics studies have provided unique evidence of gas flows in the
CGM of galaxies, both winds Rahmani et al. (2018b) as well as
accretion (Rahmani et al. 2018a; Szakacs et al. 2021). A caseby-case analysis of the absorbers indicates that about 10% are
consistent with gas accretion, while up to 30% trace outflows.
The remaining absorbers are associated with gas in the galaxy
disk, the intragroup medium, or low-mass galaxies that are below the detection limit of the MUSE instrument (Weng et al.
2023a).
Using HST broad-band imaging observations, Karki et al.
(2023) report that SFR shows a strong correlation with stellar mass, indicating that most absorption-selected galaxies align
with the star formation main sequence of the global galaxy
population. In addition, they find that more massive absorber
counterparts exhibited higher central concentration and larger
sizes. Finally, they report that the SFR surface densities of the
absorption-selected galaxies were higher than predicted by the
Kennicutt–Schmidt relation for local galaxies, which points to
a higher star formation efficiency in these galaxies (Karki et al.
2023).By fitting the spectral energy distribution from HST data,
the survey has determined the stellar masses of the galaxies associated with the absorbers, which span a wide range from 8.1
< log( _M_ ⋆ / _M_ ⊙ ) < 11.8 (Augustin et al. 2024). Most of these
galaxies are found to lie on the main sequence of star-forming
galaxies (Augustin et al. 2024).
Early ALMA observations have enabled the study of the
molecular gas in these galaxies. First findings have found that
H i-selected galaxies tend to have high molecular gas masses
given their low star formation rates, leading to high depletion
times (Klitsch et al. 2018; Péroux et al. 2019; Szakacs et al.
2021). In this paper, we present the Cycle 10 ALMA Large


Article number, page 13 of 18

_A&A proofs:_ manuscript no. aanda



Programme campaign’s which optimised setup enables us to
study objects down to log M H2 >9 M ⊙ at 5-σ thus providing a
large sample required to measure evolution and determine typical properties of these systems. The paper provides a description
of the survey design, details on the observational set-up and an
extensive report of data reduction processes. It also accompanies the data release of the ALMA Large Programme. Finally,
the paper reviews the salient science goals that will be tackled
with these extensive datasets. The project increases the number
of galaxies with observational constraints of their multi-phase
circumgalactic medium by more than a factor 2, thus producing
a representative sample of H i-rich galaxies. The overarching objective of the project is to characterise the multi-phase properties
of a remarkable sample of galaxies with multi-wavelength observations with VLT/MUSE, HST UV spectroscopy and broadband imaging to probe the physical processes by which gas is
transformed into stars. By measuring the molecular mass, gas
flows and gas fractions of this unique sample, the results will:
1) quantify the amount of molecular gas in H i-rich galaxies,
2) characterise the role of molecular gas flows from kinematics
analysis, and 3) perform a first census of the condensed baryons
in the circumgalactic medium. Given the H i-selection, these data
will also prepare for future observations with SKA, including
MeerKAT and ASKAP pathfinders.


_Acknowledgements._ This research was supported by the International Space Science Institute (ISSI) in Bern, through ISSI International Team project #564 (The
Cosmic Baryon Cycle from Space). J.C., C.B., and N.M.F.S. acknowledge funding by the European Union (ERC Advanced Grant GALPHYS, 101055023).
R.A. acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program (grant
agreement 101020943, SPECMAP-CGM). Views and opinions expressed are,
however, those of the author(s) only and do not necessarily reflect those of the
European Union or the European Research Council. Neither the European Union
nor the granting authority can be held responsible for them. V.P.K. gratefully acknowledges support from NSF grants 2007538 and 2009811. This paper makes
use of the following ALMA data: ADS/JAO.ALMA#2023.1.00127.L ALMA is
a partnership of ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ. In addition, publications from NA authors must include the standard NRAO acknowledgement:
The National Radio Astronomy Observatory is a facility of the National Science
Foundation operated under cooperative agreement by Associated Universities,
Inc.


**Data availability**


ALMA data directly related to this publication and its figures are
publicly available. Additionally, the raw data can be downloaded
from the public archives with the respective project codes.


**References**


Augustin, R., Péroux, C., Karki, A., et al. 2024, MNRAS, 528, 6159
Augustin, R., Péroux, C., Møller, P., et al. 2018, MNRAS, 478, 3120
Banerjee, E., Muzahid, S., Schaye, J., et al. 2025, ApJ, 980, 171
Banerjee, E., Muzahid, S., Schaye, J., Johnson, S. D., & Cantalupo, S. 2023,
MNRAS, 524, 5148
Barfety, C., Péroux, C., & Weng. 2026, MNRAS, 524, 5524
Barnes, A. T., Watkins, E. J., Meidt, S. E., et al. 2023, ApJ, 944, L22
Bollo, V., Péroux, C., & Weng. 2026, MNRAS, 524, 5524
Bollo, V., Péroux, C., Zwaan, M., et al. 2025, A&A, 695, A163
Bollo, V., Zwaan, M., Péroux, C., et al. 2024, A&A, 690, A258
Bouché, N., Carfantan, H., Schroetter, I., Michel-Dansac, L., & Contini, T. 2015,
AJ, 150, 92
Bouché, N., Finley, H., Schroetter, I., et al. 2016, ApJ, 820, 121
Bouché, N., Murphy, M., Péroux, C., et al. 2013, Sci, 341, 50
Bouché, N., Murphy, M. T., Péroux, C., et al. 2007, ApJ, 669, L5
Bouché, N. F., Bera, S., Krajnovi´c, D., et al. 2022, A&A, 658, A76


Article number, page 14 of 18



Bouché, N. F., Wendt, M., Zabl, J., et al. 2025, A&A, 694, A67
Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105
Carniani, S., Marconi, A., Maiolino, R., et al. 2016, A&A, 591, A28
Casavecchia, B., Maio, U., Péroux, C., & Ciardi, B. 2024, A&A, 689, A106
Casavecchia, B., Maio, U., Péroux, C., & Ciardi, B. 2025, A&A, 693, A119
Chaikin, E., Schaye, J., Schaller, M., et al. 2025, arXiv e-prints,
arXiv:2509.04067
Chen, H.-W., Zahedy, F. S., Boettcher, E., et al. 2020, MNRAS, 497, 498
Chen, J., Ivison, R. J., Zwaan, M. A., et al. 2023, MNRAS, 518, 1378
Chen, Y., Steidel, C. C., Erb, D. K., et al. 2021, MNRAS, 508, 19
Cooke, R. J., Pettini, M., Jorgenson, R. A., Murphy, M. T., & Steidel, C. C. 2014,
ApJ, 781, 31
Cresci, G., Hicks, E. K. S., Genzel, R., et al. 2009, ApJ, 697, 115
Danforth, C. W., Keeney, B. A., Tilton, E. M., et al. 2016, ApJ, 817, 111
Das, S., Mathur, S., Gupta, A., & Krongold, Y. 2021, ApJ, 918, 83
Davies, R., Förster Schreiber, N. M., Cresci, G., et al. 2011, ApJ, 741, 69
Davies, R. I., Tacconi, L. J., & Genzel, R. 2004a, ApJ, 613, 781
Davies, R. I., Tacconi, L. J., & Genzel, R. 2004b, ApJ, 602, 148
de Blok, W. J. G., Healy, J., Maccagni, F. M., et al. 2024, A&A, 688, A109
Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 69
Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451
Dutta, R., Fumagalli, M., Fossati, M., et al. 2020, MNRAS, 499, 5022
Dutta, S., Muzahid, S., Schaye, J., et al. 2025a, ApJ, 985, 44
Dutta, S., Muzahid, S., Schaye, J., et al. 2025b, MNRAS, 9, 4
Dutta, S., Muzahid, S., Schaye, J., et al. 2024, MNRAS, 528, 3745
Erb, D. K., Li, Z., Steidel, C. C., et al. 2023, ApJ, 953, 118
Fynbo, J. P. U., Heintz, K. E., Neeleman, M., et al. 2018, MNRAS, 479, 2126
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1
Galbiati, M., Dutta, R., Fumagalli, M., Fossati, M., & Cantalupo, S. 2024, A&A,
690, A7
Genzel, R., Förster Schreiber, N. M., Übler, H., et al. 2017, Nature, 543, 397
Genzel, R., Price, S. H., Übler, H., et al. 2020, ApJ, 902, 98
Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20
Ginzburg, O., Dekel, A., Mandelker, N., & Krumholz, M. R. 2022, MNRAS,
513, 6177
Girdhar, A., Harrison, C. M., Mainieri, V., et al. 2022, MNRAS, 512, 1608
Girdhar, A., Harrison, C. M., Mainieri, V., et al. 2024, MNRAS, 527, 9322
Green, J. C., Froning, C. S., Osterman, S., et al. 2012, ApJ, 744, 60
Guo, Y., Bacon, R., Bouché, N. F., et al. 2023, Nature, 624, 53
Halley, M., Kulkarni, V. P., Péroux, C., et al. 2026, MNRAS, 524, 5524
Hamanowicz, A., Peroux, C., Zwaan, M. A., & Rahmani, H. e. a. 2020, MNRAS,
Submitted
Hamanowicz, A., Zwaan, M. A., Péroux, C., et al. 2023, MNRAS, 519, 34
Harms, R. & Fitch, J. 1991, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 1494, Space Astronomical Telescopes
and Instruments, ed. P. Y. Bely & J. B. Breckinridge, 49–65
Herrera-Camus, R., González-López, J., Förster Schreiber, N., et al. 2025, A&A,
699, A80
Johnston, S., Taylor, R., Bailes, M., et al. 2008, Experimental Astronomy, 22,
151
Jonas, J. & MeerKAT Team. 2016, in MeerKAT Science: On the Pathway to the
SKA, 1
Kanekar, N., Prochaska, J. X., Christensen, L., et al. 2018, ApJ, 856, L23
Kanekar, N., Prochaska, J. X., Neeleman, M., et al. 2020, ApJ, 901, L5
Karki, A., Kulkarni, V. P., Weng, S., et al. 2023, MNRAS, 524, 5524
Karki, A., Kulkarni, V. P., Weng, S., et al. 2026, MNRAS, 524, 5524
Kimble, R. A., Woodgate, B. E., Bowers, C. W., et al. 1998, ApJ, 492, L83
Klitsch, A., Christensen, L., Valentino, F., et al. 2022, MNRAS, 514, 2346
Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2021, MNRAS, 506, 514
Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2019a, MNRAS, 490, 1220
Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2018, MNRAS, 475, 492
Klitsch, A., Zwaan, M. A., Péroux, C., et al. 2019b, MNRAS, 482, L65
Klitsch, A., Zwaan, M. A., Smail, I., et al. 2020, MNRAS, 495, 2332
Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS,
477, 2716
Lahén, N., Naab, T., Johansson, P. H., et al. 2020, ApJ, 891, 2
Lang, P., Förster Schreiber, N. M., Genzel, R., et al. 2017, ApJ, 840, 92
Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122
Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJ, 944, L17
Lee, L. L., Förster Schreiber, N. M., Price, S. H., et al. 2025, ApJ, 978, 14
Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43
Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772,
119
Lofthouse, E. K., Fumagalli, M., Fossati, M., et al. 2023, MNRAS, 518, 305
Lofthouse, E. K., Fumagalli, M., Fossati, M., et al. 2020, MNRAS, 491, 2057
Macquart, J.-P., Prochaska, J. X., McQuinn, M., et al. 2020, Nature, 581, 391
Maio, U. & Péroux, C. 2026, A&A, 657, A47
Maio, U., Péroux, C., & Ciardi, B. 2022, A&A, 657, A47
Marasco, A., de Blok, W. J. G., Maccagni, F. M., et al. 2025, A&A, 697, A86
Mathur, S., Gupta, A., Das, S., Krongold, Y., & Nicastro, F. 2021, ApJ, 908, 69

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP


McGaugh, S. S. 2008, in IAU Symposium, Vol. 244, Dark Galaxies and Lost
Baryons, ed. J. I. Davies & M. J. Disney, 136–145
Møller, P., Christensen, L., Zwaan, M. A., et al. 2018, MNRAS, 474, 4039
Molyneux, S. J., Calistro Rivera, G., De Breuck, C., et al. 2024, MNRAS, 527,
4420
Morris, S. L., Weymann, R. J., Dressler, A., et al. 1993, ApJ, 419, 524
Muzahid, S., Schaye, J., Cantalupo, S., et al. 2021, MNRAS, 508, 5612
Muzahid, S., Schaye, J., Marino, R. A., et al. 2020, MNRAS, 496, 1013
Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2018, ApJl, 856, L12
Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A., & Kahinga, L. A.
2025, ApJ, 983, 26
Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581,
269
Neeleman, M., Prochaska, J. X., Zwaan, M. A., et al. 2016, ApJ, 820, L39
Nestor Shachar, A., Price, S. H., Förster Schreiber, N. M., et al. 2023, ApJ, 944,
78
Nicastro, F., Kaastra, J., Krongold, Y., et al. 2018, Nature, 558, 406
Nielsen, N. M., Kacprzak, G. G., Pointon, S. K., et al. 2020, ApJ, 904, 164
O’Beirne, T., Péroux, C., & Weng. 2026, MNRAS, 524, 5524
Peng, Y.-j. & Maiolino, R. 2014, MNRAS, 443, 3643
Péroux, C., Bouché, N., Kulkarni, V. P., & York, D. G. 2013, MNRAS, 436, 2650
Péroux, C., Bouché, N., Kulkarni, V. P., York, D. G., & Vladilo, G. 2011a, MNRAS, 410, 2237
Péroux, C., Bouché, N., Kulkarni, V. P., York, D. G., & Vladilo, G. 2011b, MNRAS, 410, 2251
Péroux, C., Chen, J., & Bollo, V. 2026, MNRAS, 524, 5524
Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363
Peroux, C. & Nelson, D. 2024, arXiv e-prints, arXiv:2411.07988
Péroux, C., Nelson, D., van de Voort, F., et al. 2020, MNRAS, 499, 2462
Péroux, C., Rahmani, H., Quiret, S., et al. 2017, MNRAS, 464, 2053
Péroux, C., Weng, S., Karki, A., et al. 2022, MNRAS, 516, 5618
Péroux, C., Zwaan, M. A., Klitsch, A., et al. 2019, MNRAS, 485, 1595
Pessa, I., Wisotzki, L., Urrutia, T., et al. 2024, A&A, 691, A5
Pettini, M. 2003, Cosmochemistry: The Melting Pot of Elements (New York:
Cambridge Univ. Press.)
Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196
Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13
Price, S. H., Shimizu, T. T., Genzel, R., et al. 2021, ApJ, 922, 143
Puglisi, A., Dudzeviˇci¯ut˙e, U., Swinbank, M., et al. 2023, MNRAS, 524, 2814
Rahmani, H., Péroux, C., Augustin, R., et al. 2018a, MNRAS, 474, 254
Rahmani, H., Péroux, C., Schroetter, I., et al. 2018b, MNRAS, 480, 5046
Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22
Schaye, J., Chaikin, E., Schaller, M., et al. 2025, arXiv e-prints,
arXiv:2508.21126
Schinnerer, E., Hughes, A., Leroy, A., et al. 2019, ApJ, 887, 49
Schroetter, I., Bouché, N., Péroux, C., et al. 2015, ApJ, 804, 83
Schroetter, I., Bouché, N. F., Zabl, J., et al. 2019, MNRAS, 490, 4368
Shull, J. M. 2014, ApJ, 784, 142
Shull, J. M., Smith, B. D., & Danforth, C. W. 2012, ApJ, 759, 23
Szakacs, R., Péroux, C., Zwaan, M., et al. 2021, MNRAS, 505, 4746
Szakacs, R., Péroux, C., Zwaan, M. A., et al. 2022, MNRAS, 512, 4736
Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179
Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157
Trayford, J. W., Schaye, J., Correa, C., et al. 2026, MNRAS, 545, staf2040
Tripp, T. M., Lu, L., & Savage, B. D. 1998, ApJ, 508, 200
Tumlinson, J., Peeples, M. S., & Werk, J. K. 2017, ARA&A, 55, 389
Übler, H., Genzel, R., Tacconi, L. J., et al. 2018, ApJ, 854, L24
Veronese, S., de Blok, W. J. G., Healy, J., et al. 2025, A&A, 693, A97
Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111
Watts, A. B., Cortese, L., Catinella, B., et al. 2024, MNRAS, 530, 1968
Weng, S., Péroux, C., Karki, A., et al. 2023a, MNRAS, 523, 676
Weng, S., Péroux, C., Karki, A., et al. 2023b, MNRAS, 519, 931
Weng, S., Péroux, C., Ramesh, R., et al. 2024, MNRAS, 527, 3494
Werk, J. K., Prochaska, J. X., Tumlinson, J., et al. 2014, ApJ, 792, 8
Wuyts, S., Förster Schreiber, N. M., Wisnioski, E., et al. 2016, ApJ, 831, 149
Zabl, J., Bouché, N. F., Schroetter, I., et al. 2019, MNRAS, 485, 1961



Article number, page 15 of 18

_A&A proofs:_ manuscript no. aanda


**Appendix A:** **MUSE-ALMA haloes survey**
**publications to date**


This appendix introduces Table A which lists the MUSE-ALMA
Haloes survey publications to date.

Reference Paper Title
Péroux et al. (2017) Nature of the absorbing gas associated with a galaxy group at z∼0.4
Rahmani et al. (2018a) Observational signatures of a warped disk associated with cold-flow accretion
Rahmani et al. (2018b) A Lyman limit system associated with galactic winds
Klitsch et al. (2018) A combined ALMA and MUSE survey for neutral, molecular, and ionized gas
Péroux et al. (2019) Multiphase circumgalactic medium probed with MUSE and ALMA
Hamanowicz et al. (2020) MUSE-ALMA Haloes V: physical properties and environment of z≤1.4 HI quasar absorbers
Szakacs et al. (2021) MUSE-ALMA Haloes VI: coupling atomic, ionized, and molecular gas kinematics of galaxies
Péroux et al. (2022) MUSE-ALMA Haloes VII: survey science goals & design, data processing and final catalogues
Weng et al. (2023b) MUSE-ALMA Haloes VIII: Statistical study of circumgalactic medium gas
Karki et al. (2023) MUSE-ALMA Haloes IX: Morphologies and stellar properties of gas-rich galaxies
Augustin et al. (2024) MUSE-ALMA Haloes X: the stellar masses of gas-rich absorbing galaxies
Weng et al. (2023a) MUSE-ALMA Haloes XI: gas flows in the circumgalactic medium
Weng et al. (2024) The physical origins of gas in the CGM using observationally motivated TNG50 mocks
Bollo et al. (2026) MUSE-ALMA Haloes XII: Molecular gas in z∼0.5 HI-selected galaxies
Karki et al. (2026) MUSE-ALMA Haloes XIII: Kinematics and Stellar Properties of Tidal Features
Péroux et al. (2026) MUSE-ALMA Haloes XIV: The ALMA Large Programme Data Release
O’Beirne et al. (2026) MUSE-ALMA Haloes XV: A census of the condensed baryons in _z_ ∼ 0.5 galaxies
Barfety et al. (2026) MUSE-ALMA Haloes XVI: Multiphase kinematics and rotational support of different gas phases
Halley et al. (2026) MUSE-ALMA Haloes XVII: Circumgalactic Medium metallicity


**Appendix B:** **MUSE-ALMA Haloes survey**
**associated galaxy properties**


This appendix presents the table summarising the physical properties of all 79 galaxies associated with the 32 MUSE-ALMA
Haloes primary targeted quasar absorbers.


Article number, page 16 of 18

C. Péroux et al.: MUSE-ALMA Haloes ALMA LP


**Table B.1.** MUSE-ALMA Haloes Survey associated galaxy properties.


Quasar/Gal _z_ [1] abs log _N_ (H i) [1] absorption _z_ [3] gal impact SFR [3] stellar emission
metallicity [2] parameter [3] mass [4] metallicity [3]

[atoms/cm [2] ] [M/H] [kpc] [M ⊙ /yr] [M ⊙ ] 12 + log(O/H)
Q0058p0019 0.6125 20.08±0.15 0.25 [+] − [0] 0 [.] . [19] 19 ... ... ... ... ...
Q0123m0058 0.8686 <18.62 <-1.0 ... ... ... ... ...
Q0123m0058 1.4094 20.08±0.09 -0.6 [+] − [0] 0 [.] . [004] 01 ... ... ... ... ...
Q0138m0005_14 _[b]_ 0.7821 19.81±0.08 0.28 [+] − [0] 0 [.] . [15] 15 0.78212 81.5 6.9 ±2.44 9.8 [+] − [0] 0 [.] . [1] 2 8.72±0.07
Q0152m2001_4 0.3830 <18.8 <-1.5 0.38138 169.6 2.05 ±0.66 11.5 [+] − [0] 0 [.] . [1] 1 8.73±0.1
Q0152m2001_5 _[c]_ 0.3830 <18.8 <-1.5 0.38257 59.9 0.1 ±0.38 11.3 [+] − [0] 0 [.] . [1] 1 8.65±0.08
Q0152m2001_7 0.3830 <18.8 <-1.5 0.38135 146.5 0.16 ±0.42 11.0 [+] − [0] 0 [.] . [1] 1 8.49±0.15
Q0152m2001_13 _[a]_ 0.3830 <18.8 <-1.5 0.38145 84.2 <0.028 11.8 [+] − [0] 0 [.] . [2] 4 ...
Q0152m2001_14 0.3830 <18.8 <-1.5 0.38222 204.4 0.73 ±0.37 10.5 [+] − [0] 0 [.] . [2] 2 8.58±0.08
Q0152m2001_62 0.3830 <18.8 <-1.5 0.38498 144.2 <0.028 10.5 [+] − [0] 0 [.] . [1] 1 ...
Q0152m2001_12 _[a]_ 0.7802 18.87±0.12 -1.9 [+] − [0] 0 [.] . [1] 01 0.78018 55.0 0.18 ±0.4 ... ...
Q0152p0023_7 0.4818 19.78±0.08 -0.1 [+] − [0] 0 [.] . [011] 019 0.48261 154.3 2.6 ±0.96 10.1 [+] − [0] 0 [.] . [2] 1 8.68±0.1
Q0152p0023_13 0.4818 19.78±0.08 -0.1 [+] − [0] 0 [.] . [011] 019 0.48206 140.0 2.7 ±0.86 9.0 [+] − [0] 0 [.] . [2] 1 8.43±0.06
Q0152p0023_20 _[a]_ 0.4818 19.78±0.08 -0.1 [+] − [0] 0 [.] . [011] 019 0.48143 122.9 0.83 ±0.35 8.1 [+] − [0] 0 [.] . [1] 1 8.59±0.12
Q0152p0023_23 _[a]_ 0.4818 19.78±0.08 -0.1 [+] − [0] 0 [.] . [011] 019 0.48068 187.8 <0.243 8.4 [+] − [0] 0 [.] . [1] 1 ...
Q0152p0023_44 _[a]_ 0.4818 19.78±0.08 -0.1 [+] − [0] 0 [.] . [011] 019 0.4832 170.7 <0.243 8.0 [+] − [0] 0 [.] . [6] 6 ...
Q0420m0127_8 _[d]_ 0.6331 18.54±0.09 -1.6 [+] − [0] 0 [.] . [1] 01 0.63318 133.9 1.03 ±0.36 10.3 [+] − [0] 0 [.] . [2] 4 8.59±0.12
Q0420m0127_12 _[d]_ 0.6331 18.54±0.09 -1.6 [+] − [0] 0 [.] . [1] 01 0.63382 144.8 1.24 ±0.42 10.8 [+] − [0] 0 [.] . [1] 1 8.54±0.14
Q0420m0127_13 _[d]_ 0.6331 18.54±0.09 -1.6 [+] − [0] 0 [.] . [1] 01 0.63326 101.4 0.83 ±0.3 9.7 [+] − [0] 0 [.] . [9] 9 8.44±0.18
Q0420m0127_30 0.6331 18.54±0.09 -1.6 [+] − [0] 0 [.] . [1] 01 0.63197 215.8 2.68 ±0.87 9.1 [+] − [0] 0 [.] . [9] 9 ...
Q0454m220_69 _[a]_ 0.4744 19.45±0.03 -0.48 [+] − [0] 0 [.] . [1] 1 0.4745 8.4 4.26 ±1.32 10.8 [+] − [0] 0 [.] . [1] 1 8.66±0.05
Q0454m220_4 _[a]_ 0.4833 18.65±0.02 -0.7 [+] − [0] 0 [.] . [1] 7 0.48377 107.6 0.68 ±0.27 10.6 [+] − [0] 0 [.] . [1] 1 8.33±0.12
Q0454p039_57 _[a]_ 0.8596 20.69±0.06 -1.57 [+] − [0] 0 [.] . [17] 17 0.85877 18.3 7.64 ±2.35 ... ...
Q0454p039_15 _[a]_ 1.1532 18.59±0.02 -0.19 [+] − [0] 0 [.] . [22] 22 1.15497 58.0 0.65 ±0.22 ... ...
Q0454p039_65 _[a]_ 1.1532 18.59±0.02 -0.19 [+] − [0] 0 [.] . [22] 22 1.1547 127.1 0.71 ±0.25 9.9 [+] − [0] 0 [.] . [8] 8 ...
Q1110p0048_6 _[a]_ 0.5604 20.20±0.10 ... 0.56006 59.6 <0.122 9.1 [+] − [0] 0 [.] . [1] 1 8.26±0.09
Q1110p0048_15 _[a]_ 0.5604 20.20±0.10 ... 0.56035 129.7 <0.122 8.8 [+] − [0] 0 [.] . [6] 6 8.46±0.1
Q1110p0048_44 _[a]_ 0.5604 20.20±0.10 ... 0.56118 5.7 <0.122 9.2 [+] − [0] 0 [.] . [3] 3 8.49±0.05
Q1130m1449_18 0.1906 <19.1 <-2.3 0.19048 17.9 0.33 ±0.33 10.9 [+] − [0] 0 [.] . [1] 1 8.52±0.06
Q1130m1449_4 _[c]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31312 45.0 0.56 ±0.33 ... 8.37±0.06
Q1130m1449_5 _[c]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31276 81.6 0.68 ±0.31 10.9 [+] − [0] 0 [.] . [1] 1 8.27±0.06
Q1130m1449_8 _[c]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31138 98.6 0.04 ±0.34 10.5 [+] − [0] 0 [.] . [1] 1 8.57±0.05
Q1130m1449_13 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31184 120.0 <0.018 9.9 [+] − [0] 0 [.] . [2] 2 ...
Q1130m1449_16 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.3135 37.3 0.02 ±0.59 9.3 [+] − [0] 0 [.] . [3] 2 ...
Q1130m1449_17 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31197 17.6 0.1 ±0.33 9.2 [+] − [0] 0 [.] . [4] 4 8.47±0.07
Q1130m1449_24 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31249 17.9 2.08 ±0.42 8.9 [+] − [0] 0 [.] . [2] 2 8.37±0.11
Q1130m1449_31 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31267 73.4 0.1 ±0.34 8.6 [+] − [0] 0 [.] . [2] 3 8.5 ±0.07
Q1130m1449_36 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31322 23.2 0.45 ±0.6 8.8 [+] − [0] 0 [.] . [4] 4 ...
Q1130m1449_43 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.3124 26.8 <0.018 ... ...
Q1130m1449_50 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31437 99.3 0.01 ±0.49 ... 8.45±0.15
Q1130m1449_56 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31215 129.6 2.77 ±0.37 ... 8.7 ±0.05
Q1130m1449_68 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31299 74.7 0.02 ±0.61 8.2 [+] − [0] 0 [.] . [3] 3 8.44±0.17
Q1130m1449_76 _[e]_ 0.3127 21.71±0.07 -1.23 [+] − [0] 0 [.] . [16] 16 0.31295 9.9 0.01 ±0.44 7.9 [+] − [0] 0 [.] . [4] 4 8.43±0.15
Q1130m1449_6 0.3283 <18.9 <-1.1 0.3284 91.1 1.39 ±0.37 7.8 [+] − [0] 0 [.] . [4] 4 8.66±0.06
Q1130m1449_9 0.3283 <18.9 <-1.1 0.32813 75.5 1.02 ±0.36 ... 8.69±0.05
Q1211p1030_7 _[c]_ 0.3929 19.46±0.08 -2.55 [+] − [0] 0 [.] . [94] 94 0.39277 38.2 3.0 ±1.18 8.8 [+] − [0] 0 [.] . [1] 1 ...
Q1211p1030_9 0.3929 19.46±0.08 -2.55 [+] − [0] 0 [.] . [94] 94 0.39288 39.0 3.87 ±1.26 9.7 [+] − [0] 0 [.] . [4] 4 ...
Q1211p1030_17 0.3929 19.46±0.08 -2.55 [+] − [0] 0 [.] . [94] 94 0.39289 36.8 <0.035 8.7 [+] − [0] 0 [.] . [1] 1 ...
Q1211p1030_38 _[a]_ 0.6296 20.30±0.24 -2.82 [+] − [0] 0 [.] . [89] 89 0.63031 138.4 0.71 ±0.26 10.5 [+] − [0] 0 [.] . [5] 5 8.44±0.1
Q1211p1030_57 _[a]_ 0.6296 20.30±0.24 -2.82 [+] − [0] 0 [.] . [89] 89 0.62957 16.9 < 0.386 11.4 [+] − [0] 0 [.] . [3] 4 ...
Q1211p1030_13 _[a]_ 0.8999 <18.5 <-1.2 0.89909 175.3 0.46 ±0.19 8.9 [+] − [0] 0 [.] . [7] 7 8.63±0.2
Q1211p1030_16 _[a]_ 0.8999 <18.5 <-1.2 0.8994 77.4 0.91 ±0.36 ... ...
Q1211p1030_48 0.8999 <18.5 <-1.2 0.9 52.8 3.49 ±0.31 ... 8.28±0.05
Q1211p1030_58 _[a]_ 0.8999 <18.5 <-1.2 0.89894 268.6 0.08 ±0.36 ... 8.46±0.1


Article number, page 17 of 18

_A&A proofs:_ manuscript no. aanda


**Table B.1.** continued


Q1211p1030 1.0496 <18.90 <-1.3 ... ... ... ... ...
Q1229m021_39 _[c]_ 0.3950 20.75±0.07 -0.18 [+] − [0] 0 [.] . [14] 14 0.39531 6.8 0.89 ±0.49 9.5 [+] − [0] 0 [.] . [3] 2 8.63±0.16
Q1229m021_13 _[c]_ 0.7572 18.36±0.09 -0.2 [+] − [0] 0 [.] . [1] 1 0.7575 70.9 2.18 ±0.75 ... 8.42±0.14
Q1229m021_5 0.7691 18.11±0.15 -3.1 [+] − [0] 0 [.] . [2] 1 0.76855 178.3 1.66 ±0.61 9.8 [+] − [0] 0 [.] . [7] 7 8.3 ±0.14
Q1229m021_29 0.7691 18.11±0.15 -3.1 [+] − [0] 0 [.] . [2] 1 0.76852 135.9 0.12 ±0.51 9.6 [+] − [0] 0 [.] . [7] 7 8.6 ±0.11
Q1229m021_40 0.7691 18.11±0.15 -3.1 [+] − [0] 0 [.] . [2] 1 0.76646 60.0 3.0 ±0.95 9.7 [+] − [0] 0 [.] . [7] 7 8.49±0.1
Q1229m021_6 _[a]_ 0.8311 18.84±0.10 -2.6 [+] − [0] 0 [.] . [1] 1 0.8317 182.3 0.51 ±0.21 ... 8.34±0.19
Q1229m021_8 _[a]_ 0.8311 18.84±0.10 -2.6 [+] − [0] 0 [.] . [1] 1 0.8306 125.5 <0.333 8.5 [+] − [0] 0 [.] . [7] 6 ...
Q1229m021_10 _[a]_ 0.8311 18.84±0.10 -2.6 [+] − [0] 0 [.] . [1] 1 0.8319 173.6 6.23 ±2.13 9.7 [+] − [0] 0 [.] . [7] 7 ...
Q1229m021_41 _[a]_ 0.8311 18.84±0.10 -2.6 [+] − [0] 0 [.] . [1] 1 0.83199 186.8 7.79 ±11.62 ... ...
Q1342m0035_4 _[a]_ 0.5380 19.78±0.13 -1.2 [+] − [0] 0 [.] . [1] 1 0.53773 43.6 3.9 ±1.21 10.1 [+] − [0] 0 [.] . [1] 1 8.67±0.06
Q1342m0035_9 _[a]_ 0.5380 19.78±0.13 -1.2 [+] − [0] 0 [.] . [1] 1 0.53877 24.3 0.44 ±0.18 10.9 [+] − [0] 0 [.] . [2] 1 8.6 ±0.18
Q1345m0023_13 _[a]_ 0.6057 18.85±0.20 -0.9 [+] − [0] 0 [.] . [2] 2 0.60697 55.6 3.06 ±1.04 10.1 [+] − [0] 0 [.] . [6] 6 8.64±0.07
Q1345m0023_40 _[a]_ 0.6057 18.85±0.20 -0.9 [+] − [0] 0 [.] . [2] 2 0.6054 162.4 0.51 ±0.18 8.7 [+] − [0] 0 [.] . [6] 6 8.31±0.14
Q1431m0050_10 _[a]_ 0.6085 19.18±0.24 -0.8 [+] − [0] 0 [.] . [1] 1 0.60843 45.4 14.27±4.44 9.8 [+] − [0] 0 [.] . [1] 1 8.62±0.05
Q1431m0050_68 _[a]_ 0.6085 19.18±0.24 -0.8 [+] − [0] 0 [.] . [1] 1 0.60742 73.0 1.84 ±0.72 10.6 [+] − [0] 0 [.] . [2] 3 ...
Q1431m0050_26 _[a]_ 0.6868 18.40±0.07 -1.2 [+] − [0] 0 [.] . [029] 012 0.6871 23.3 0.42 ±0.18 ... ...
Q1431m0050_73 _[a]_ 0.6868 18.40±0.07 -1.2 [+] − [0] 0 [.] . [029] 012 0.68687 188.7 0.89 ±0.39 8.9 [+] − [0] 0 [.] . [6] 6 ...
Q1515p0410_4 _[a]_ 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.55859 10.1 <0.171 11.0 [+] − [0] 0 [.] . [1] 2 ...
Q1515p0410_9 _[a]_ 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.55866 221.0 <0.171 10.2 [+] − [0] 0 [.] . [2] 1 8.75±0.08
Q1515p0410_11 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.55995 216.0 <0.171 10.1 [+] − [0] 0 [.] . [2] 1 ...
Q1515p0410_13 _[a]_ 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.5586 194.1 <0.171 10.2 [+] − [0] 0 [.] . [2] 1 ...
Q1515p0410_42 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.55743 171.3 <0.171 9.1 [+] − [0] 0 [.] . [6] 6 8.53±0.15
Q1515p0410_54 _[a]_ 0.5592 20.20±0.19 0.20 [+] − [0] 0 [.] . [24] 24 0.55892 168.8 <0.171 ... 8.61±0.11
Q1554m203_51 _[a]_ 0.7869 <19.00 <-1.6 0.78558 23.0 0.56 ±0.2 9.4 [+] − [0] 0 [.] . [5] 5 ...
Q2131m1207_5 _[a]_ 0.4298 19.50±0.15 -1.47 [+] − [0] 0 [.] . [22] 22 0.42999 48.5 0.11 ±0.05 10.1 [+] − [0] 0 [.] . [2] 1 8.43±0.12
Q2131m1207_26 _[a]_ 0.4298 19.50±0.15 -1.47 [+] − [0] 0 [.] . [22] 22 0.42971 172.1 0.24 ±0.09 ... 8.12±0.11
Q2131m1207_34 _[a]_ 0.4298 19.50±0.15 -1.47 [+] − [0] 0 [.] . [22] 22 0.4308 59.2 0.05 ±0.03 ... ...
Q2131m1207_43 _[a]_ 0.4298 19.50±0.15 -1.47 [+] − [0] 0 [.] . [22] 22 0.43003 145.9 2.47 ±0.82 ... 8.68±0.05
Q2353m0028 0.6044 21.54±0.15 -1.18 [+] − [0] 0 [.] . [41] 41 ... ... ... ... ...


**Notes.** This table summarises for each of the quasar fields, the main physical properties of the atomic gas probed in absorption (redshift, column
density, neutral gas metallicity) and the galaxies associated with the strong H i quasar absorbers (redshift, distance from quasar sightline, star
formation rate, stellar mass and ionised gas metallicity). The former absorption properties are estimated from HST and VLT/Keck spectroscopy of
the background quasar while the latter are derived from VLT/MUSE and HST imaging emission observations combined. Entries with no number
underscored refer to the 5 quasar absorbers with no associated galaxies identified in MUSE fields.
**References** : [1] Péroux et al. (2022); [2] Halley et al. (2026); [3] Weng et al. (2023b); [4] Augustin et al. (2024).
_a_ denotes ALMA Large Programme targets (this work); _b_ Kanekar et al. (2018); _c_ Szakacs et al. (2021); _d_ Klitsch et al. (2018); _e_ Péroux et al. (2019).


Article number, page 18 of 18


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "UV spectroscopy of background quasars for N(H I) measurements, and WFC3/WFPC2 broad-band optical and IR imaging for stellar properties and morphologies",
  "failed_quote": "An essential component of the MUSE-ALMA Haloes project is a Cycle 27 forty-orbit medium Hubble Space Telescope programme (PI: C. Peroux) providing broad-band imaging with WFC3 on both the optical (UVIS) and infrared (IR) detectors for 18 quasar fields."
 },
 {
  "path": "data.other_facilities[3].provided.evidence[1]",
  "value": "Astrometric reference catalogue of stars used to align HST images and VLT/MUSE data cubes with ALMA astrometry",
  "failed_quote": "As a result, the multi-wavelength observations of the MUSE-ALMA Haloes survey are consistently aligned to the absolute astrometry newly provided by ALMA and Gaia DR3."
 },
 {
  "path": "data.other_facilities[4].provided.evidence[0]",
  "value": "Database of reprocessed ALMA calibration scans cross-matched with primary targets, providing observations for Q0420-0127",
  "failed_quote": "ALMACAL is a database of reprocessed ALMA phase and amplitude calibration scans (Bollo et al. 2024)."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Neutral gas absorption metallicities and ionisation fractions",
  "failed_quote": "For lower columns densities, where the gas could be partly ionised, photo-ionisation models with the CLOUDY software enabled robust estimates of the ionisation fraction of the gas (Halley et al. 2026)."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "CLOUDY photo-ionisation models used to estimate ionisation fractions of the gas",
  "failed_quote": "For lower columns densities, where the gas could be partly ionised, photo-ionisation models with the CLOUDY software enabled robust estimates of the ionisation fraction of the gas (Halley et al. 2026)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "MUSE sub-exposure alignment and data processing",
  "failed_quote": "The MUSE individual sub-exposures were aligned with the ESO pipeline’s exp_align recipe using these point sources resulting in an accurate relative astrometry in the combined single data cube (Péroux et al. 2022)."
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Milky Way Spectral Line Energy Distribution (SLED) to convert higher-J CO to CO(1-0) flux",
  "failed_quote": "The observations were designed to reach a molecular mass of log M_H2 >9 M_⊙ assuming a Milky Way Spectral Line Energy Distribution (SLED) to convert to CO(1−0) flux (Carilli & Walter 2013)"
 },
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Compared RMS sensitivity before and after self-calibration (improved by factors of 1.1 to 7.6) and against automated observatory self-calibration products (improved by ~1.2).",
  "failed_quote": "After self-calibration, the RMS sensitivity is improved by factors ranging from 1.1 to 7.6, compared to the ones without self-calibration."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "Cosmology H_0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7; Milky Way SLED and alpha_CO = 4.6 M_sun (K km/s pc^2)^-1 for survey design mass sensitivity",
  "failed_quote": "The observations were designed to reach a molecular mass of log M_H2 >9 M_⊙ assuming a Milky Way Spectral Line Energy Distribution (SLED) to convert to CO(1−0) flux (Carilli & Walter 2013), a galactic conversion factor to estimate molecular mass of α_CO =4.6 M_⊙ (K km/s pc^2)^-1"
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Photo-ionisation modelling to estimate the ionisation fraction of lower column density HI absorbers",
  "failed_quote": "For lower columns densities, where the gas could be partly ionised, photo-ionisation models with the CLOUDY software enabled robust estimates of the ionisation fraction of the gas (Halley et al. 2026)."
 },
 {
  "path": "software[7].used_for.evidence[0]",
  "value": "Aligning MUSE individual sub-exposures using point sources",
  "failed_quote": "The MUSE individual sub-exposures were aligned with the ESO pipeline’s exp_align recipe using these point sources resulting in an accurate relative astrometry in the combined single data cube (Péroux et al. 2022)."
 },
 {
  "path": "software[11].used_for.evidence[0]",
  "value": "AI-generation of the schematic sketch in Figure 3",
  "failed_quote": "The overall approach is schematically illustrated by Figure 3, a sketch partially AI-generated with FigureLabs."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "RMS sensitivity improvement factor from manual self-calibration vs no self-calibration = 1.1 to 7.6 dimensionless",
  "failed_quote": "After self-calibration, the RMS sensitivity is improved by factors ranging from 1.1 to 7.6, compared to the ones without self-calibration."
 },
 {
  "path": "results_numeric[6].evidence[1]",
  "value": "5-sigma molecular gas mass sensitivity limit of the ALMA Large Programme = > 9 log(M_sun)",
  "failed_quote": "In this paper, we present the Cycle 10 ALMA Large Programme campaign’s which optimised setup enables us to study objects down to log M_H2 >9 M_⊙ at 5-σ"
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "Manual phase and amplitude self-calibration on bright background quasars (>= 4 mJy) in the ALMA field-of-view significantly improves RMS sensitivity (by factors of 1.1 to 7.6) and outperforms automated pipeline self-calibration by ~1.2.",
  "failed_quote": "After self-calibration, the RMS sensitivity is improved by factors ranging from 1.1 to 7.6, compared to the ones without self-calibration."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "The Cycle 10 ALMA Large Programme increases the number of galaxies with multi-phase circumgalactic medium constraints by more than a factor of 2, providing a representative sample of 39 z~0.5 HI-selected galaxies down to log M_H2 > 9 M_sun.",
  "failed_quote": "In this paper, we present the Cycle 10 ALMA Large Programme campaign’s which optimised setup enables us to study objects down to log M_H2 >9 M_⊙ at 5-σ thus providing a large sample required to measure evolution and determine typical properties of these systems."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "Manual self-calibration on the background quasar substantially improves the sensitivity and dynamic range of the ALMA datacubes.",
  "failed_quote": "After self-calibration, the RMS sensitivity is improved by factors ranging from 1.1 to 7.6, compared to the ones without self-calibration."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "Correcting HST and MUSE headers to Gaia DR3 astrometry successfully aligns all multi-wavelength datasets of the survey with ALMA's absolute astrometry.",
  "failed_quote": "As a result, the multi-wavelength observations of the MUSE-ALMA Haloes survey are consistently aligned to the absolute astrometry newly provided by ALMA and Gaia DR3."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "The ALMA Large Programme successfully delivers homogeneous, deep molecular gas observations that more than double the sample of galaxies with multi-phase CGM constraints.",
  "failed_quote": "In this paper, we present the Cycle 10 ALMA Large Programme campaign’s which optimised setup enables us to study objects down to log M_H2 >9 M_⊙ at 5-σ thus providing a large sample required to measure evolution and determine typical properties of these systems."
 },
 {
  "path": "reasoning.how_they_decided_enough.evidence[0]",
  "value": "Exposure times (2.4 to 7.9 hr) were set to reach a 5-sigma molecular gas mass limit of log M_H2 > 9 M_sun at z=0.5 assuming a Milky Way SLED and alpha_CO = 4.6.",
  "failed_quote": "The observations were designed to reach a molecular mass of log M_H2 >9 M_⊙ assuming a Milky Way Spectral Line Energy Distribution (SLED) to convert to CO(1−0) flux (Carilli & Walter 2013), a galactic conversion factor to estimate molecular mass of α_CO =4.6 M_⊙ (K km/s pc^2)^-1 and the z=0.5 luminosity distance of dL=2129 Mpc using a (0.3,0.7,0.7) cosmology."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Raw ALMA data are publicly available in the ALMA Science Archive under project code 2023.1.00127.L.",
  "failed_quote": "While the raw data are available through the ALMA Science Archive, the remaining of the products are made available through a dedicated ALMA page."
 },
 {
  "path": "reproducibility.products_in_archive.evidence[1]",
  "value": "Value-added enhanced data products (.pbcor., .mask., and .pb. FITS cubes for natural and Briggs robust=0.5 weightings at 15 and 60 km/s, plus README and Data Description Document) are released via a dedicated ESO/ALMA webpage.",
  "failed_quote": "While the raw data are available through the ALMA Science Archive, the remaining of the products are made available through a dedicated ALMA page."
 }
]
```
