# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.515.1751W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–23 (2022) Preprint 6 July 2022 Compiled using MNRAS L [A] TEX style file v3.0

## Dual constraints with ALMA: new [O iii] 88 μm and dust-continuum ∼ observations reveal the ISM conditions of luminous LBGs at 𝑧 7

### Joris Witstok [1] [,] [2] [★], Renske Smit [1] [,] [2] [,] [3] †, Roberto Maiolino [1] [,] [2] [,] [4], Nimisha Kumari [5], Manuel Aravena [6], Leindert Boogaard [7], Rychard Bouwens [9], Stefano Carniani [8], Jacqueline A. Hodge [9], Gareth C. Jones [1] [,] [2] [,] [10], Mauro Stefanon [9], Paul van der Werf [9], and Sander Schouws [9]

1 _Kavli Institute for Cosmology, University of Cambridge, Madingley Road, Cambridge CB3 0HA, UK_
2 _Cavendish Laboratory, University of Cambridge, 19 JJ Thomson Avenue, Cambridge CB3 0HE, UK_
3 _Astrophysics Research Institute, Liverpool John Moores University, 146 Brownlow Hill, Liverpool L3 5RF, UK_
4 _Department of Physics and Astronomy, University College London, Gower Street, London WC1E 6BT, UK_
5 _AURA for the European Space Agency, Space Telescope Science Institute, 3700 San Martin Drive, Baltimore, MD 21218, USA_
6 _Núcleo de Astronomía, Facultad de Ingeniería y Ciencias, Universidad Diego Portales, Av. Ejército 441, Santiago, Chile_
7 _Max Planck Institute for Astronomy, Königstuhl 17, 69117 Heidelberg, Germany_
8 _Scuola Normale Superiore, Piazza dei Cavalieri 7, I-56126 Pisa, Italy_
9 _Leiden Observatory, Leiden University, NL-2300 RA Leiden, Netherlands_
10 _Department of Physics, University of Oxford, Denys Wilkinson Building, Keble Road, Oxford OX1 3RH, UK_


Accepted —. Received —; in original form —


**ABSTRACT**
We present new [O iii] 88 μm observations of five bright _𝑧_ ∼ 7 Lyman-break galaxies spectroscopically confirmed by ALMA through [C ii] 158 μm, unlike recent [O iii] detections where
Lyman-α was used. This nearly doubles the sample of Epoch of Reionisation galaxies with
robust (5 _𝜎_ ) [C ii] and [O iii] detections. We perform a multi-wavelength comparison with
new deep _HST_ images of the rest-frame UV, whose compact morphology aligns well with

[O iii] tracing ionised gas. By contrast, we find more spatially extended [C ii] emission likely
produced in neutral gas, as indicated by a [N ii] 205 μm non-detection in one source. We find a
correlation between the optical [O iii] + Hβ equivalent width and [O iii]/[C ii], as seen in local
metal-poor dwarf galaxies. Cloudy models of a nebula of typical density harbouring a young
stellar population with a high ionisation parameter adequately reproduce the observed lines.
Surprisingly, however, our models fail to reproduce the strength of [O iii] 88 μm, unless we
assume an α/Fe enhancement and near-solar nebular oxygen abundance. On spatially resolved
scales, we find [O iii]/[C ii] shows a tentative anti-correlation with infrared excess, _𝐿_ IR / _𝐿_ UV,
also seen on global scales in the local Universe. Finally, we introduce the far-infrared spectral
energy distribution fitting code mercurius to show that dust-continuum measurements of one
source appear to favour a low dust temperature and correspondingly high dust mass. This
implies a high stellar metallicity yield and may point towards the need of dust production or
grain-growth mechanisms beyond supernovae.


**Key words:** galaxies: high-redshift – dark ages, reionization, first stars – methods: observational – submillimetre: ISM – techniques: imaging spectroscopy – ISM: dust



**1** **INTRODUCTION**


The Epoch of Reionisation (EoR) marks a critical turning point in
the early Universe and its study is one of the frontiers in modern
astrophysics. During the EoR, the first galaxies emerged and started
to rapidly form stars, which in turn began to ionise the surrounding


_★_ [E-mail: jnw30@cam.ac.uk](mailto:jnw30@cam.ac.uk)

- [E-mail: r.smit@ljmu.ac.uk](mailto:r.smit@ljmu.ac.uk)


© 2022 The Authors



gas – first the interstellar medium (ISM), and eventually the intergalactic medium (IGM; Dayal & Ferrara 2018; Robertson 2021).
Compared to their present-day counterparts, these galaxies have not
had much time to build up an abundance of metals (e.g. Maiolino
& Mannucci 2019). This suggests they have metal-poor stellar populations, which results in an enhanced output of ultraviolet (UV)
photons due to the hardened spectra of O- and B-type stars, in addition to containing a reduced amount of dust, implying these early

2 _J. Witstok et al._


galaxies generally experience less absorption of UV radiation (Stark
2016).
Regions where star formation takes place, especially in the very
early Universe, therefore harbour stellar radiation fields with a strong
intrinsic flux of ionising UV photons. Deep broadband surveys in
the optical and infrared (IR) by the _Hubble Space Telescope_ ( _HST_ )
have indeed proven an effective method of finding star-forming
EoR galaxies via their rest-frame UV emission, having identified a
considerable number through the Lyman-break technique (currently
nearly 2000 candidates at _𝑧_ ≥ 6; see e.g. Bouwens et al. 2021).
Even at the earliest stages of galaxy evolution, however, dust
can be of major influence. Dust grains not only catalyse star formation through the formation of molecules (Chen et al. 2018) and
fragmentation of gas (Schneider et al. 2006), but they also obscure
our view of these UV-bright star-forming regions. Dust is able to
absorb a significant proportion of stellar optical and UV light, reemitting the absorbed energy as thermal IR radiation. It therefore
poses observational challenges to the inference of star formation
rates (SFRs) solely from UV and optical measurements (Kennicutt
& Evans 2012; Madau & Dickinson 2014; Bouwens et al. 2020).
Indeed, recent work renewed attention on an existing notion (Hodge
& da Cunha 2020): that a non-trivial fraction of high-redshift galaxies ( _𝑧_ ≳ 4) may be so-called “ _HST_ -dark” systems which, even in the
deepest _HST_ imaging (reaching _𝐻_ ∼ 27 mag), appear completely
obscured at observed optical and near-infrared (NIR) wavelengths
(Franco et al. 2018; Williams et al. 2019; Wang et al. 2019; Fudamoto et al. 2021; Casey et al. 2021; Manning et al. 2022). But
while dust complicates the interpretation in the rest-frame UV and
optical, its thermal emission also serves as a probe of the mass of
the ISM (e.g. Scoville et al. 2017).
In recent years, the Atacama Large Millimeter/submillimeter
Array (ALMA) has opened a new observational window for the
study of star-forming galaxies at high redshift (see Hodge & da
Cunha 2020 for a review). ALMA is uniquely positioned to observe
their far-infrared (FIR) emission at (sub)millimetre wavelengths,
which serves a twofold purpose. First, these efforts allow ALMA to
directly detect the dust continuum emission. The first explorations
of the FIR spectral energy distribution (SED) of galaxies in the EoR
with ALMA indicate that they may rapidly build up considerable
amounts of dust (e.g. Watson et al. 2015; Laporte et al. 2017).
Second, nebular emission lines enable crucial spectroscopic redshift
confirmations and offer valuable insights into ISM conditions by
probing, for instance, the ionisation state, metal enrichment, and
kinematics of the gas (see Kewley et al. 2019 for a review).
Nebular line emission typically arises in gas surrounding hot
and massive stars. Gas in close vicinity forms a photoionised H ii
region populated by species with an ionisation potential higher
than hydrogen (e.g. O [2][+], which requires ∼ 35 eV to form), whereas
shielded gas further out will contain low-ionisation species such as
C [+] (the ionisation potential of neutral carbon, 11 _._ 3 eV, is just below
that of hydrogen, 13 _._ 6 eV; Abel et al. 2005). These regions can
transition into photodissociation regions (PDRs) – defined as mostly
neutral gas where UV photons still play a significant role in the
chemistry and/or heating – in which carbon is partly photoionised
(instead of hydrogen, as in H ii regions; Hollenbach & Tielens 1999).
The variety of ionised and neutral gas reservoirs comprising the
ISM can be traced by the many ISM coolants in the FIR, notably the

[C ii] 158 μm and [O iii] 88 μm fine-structure lines ([C ii] and [O iii]
hereafter; see e.g. Hashimoto et al. 2019; Katz et al. 2019; Pallottini
et al. 2019; Harikane et al. 2020; Bouwens et al. 2022). [O iii] is
almost exclusively produced in H ii regions, while [C ii] emission
can arise in both H ii regions and PDRs. Other FIR emission lines



further complement the picture: for instance, the [N ii] 205 μm
transition is a powerful proxy of the ionisation state of hydrogen
in the [C ii]-producing ISM (e.g. Nagao et al. 2012; Decarli et al.
2014).
The [C ii] and [O iii] lines shift into high-frequency coverage
of ALMA with sufficient atmospheric transmission (i.e. band 8)
above redshifts _𝑧_ ∼ 2 _._ 8 and _𝑧_ ∼ 5 _._ 8, respectively. For galaxies
in the EoR, where ground-based observing facilities are restricted
to spectroscopic studies of weaker rest-frame UV lines such as the
C iii] _𝜆_ 1907 _,_ [C iii] _𝜆_ 1909 Å doublet (e.g. Topping et al. 2021), observations of the [C ii] and [O iii] with ALMA have first of all proven
an effective spectroscopic confirmation tool, with almost as many
UV-bright galaxies at _𝑧>_ 6 _._ 5 now having been spectroscopically
confirmed via the [C ii] line as with H i Lyman-α (Lyα; Bouwens
et al. 2022). Moreover, the [O iii] and [C ii] lines offer a powerful
way of exploring ISM properties at high redshift, even in “normal”
star-forming galaxies (i.e. SFR ≲ 100 M ⊙ yr [−][1] ). [1] Finally, owing to
its interferometric nature, ALMA produces spatially resolved spectroscopic measurements, in contrast to unresolved slit spectroscopy,
which additionally faces the undesirable effect of slit losses.
In local starburst galaxies, [C ii] is observed to be the dominant FIR line, while in metal-poor dwarfs [O iii] takes over this role
( _𝐿_ [OIII] / _𝐿_ [CII] _>_ 1; e.g. Harikane et al. 2020). Critically, a large
filling factor of diffuse, ionised gas emitting [O iii] 88 μm means
metal-poor systems have a more porous ISM through which ionising
radiation could “leak” (Cormier et al. 2015). The relative strengths
of emission lines, in particular the [O iii] and [C ii] lines, are thus
a powerful indicator of the physical state of the ISM. Interestingly,
recent observations of galaxies in the EoR have systematically revealed [O iii]/[C ii] ratios similar to or even exceeding those in local
metal-poor dwarf galaxies (e.g. Carniani et al. 2020).
In summary, specific properties of the ISM that can be derived from combined observations of line and continuum emission

with ALMA include the dust mass and temperature, probed through
its thermal emission (e.g. Bakx et al. 2020, 2021; Schouws et al.
2022b), as well as the temperature, density, ionisation (e.g. Ferrara
et al. 2019; Pallottini et al. 2019; Vallini et al. 2021), metal enrichment (e.g. Vallini et al. 2015), and gas kinematics (e.g. Jones et al.
2021), all of which can be inferred from emission line strengths and
spectral profiles. In turn, a robust understanding of the ISM conditions in typical EoR star-forming galaxies – that is, both of their
dust and gas content – is crucial in constructing a complete physical
picture of star formation in this earliest epoch and therefore also of
the process of cosmic reionisation.
The main aim of this work is to analyse ALMA observations of
the [C ii] 158 μm, [O iii] 88 μm, [N ii] 205 μm, and underlying dust
continuum emission for a sample of five luminous, star-forming
Lyman-break galaxies (LBGs) at _𝑧_ ∼ 7. Specifically, we present
new observations of the [O iii] 88 μm line with ALMA in addition
to new _HST_ imaging, which significantly increases the number of
EoR sources detected in both [C ii] and [O iii] (currently 9, while
only 5 have detections of at least 5 _𝜎_ in both lines; Carniani et al.
2020). Moreover, the sample considered in this work arguably has
a weaker selection bias since, in contrast to the existing studies, all
galaxies have previously been spectroscopically confirmed through

[C ii] instead of Lyα. Before reionisation is completed, the latter


1 For example, Smit et al. (2018) presented [C ii] detections of two _𝑧_ ∼ 7
photometric galaxy candidates using a combined on-source time of less
than an hour, while typical spectroscopic observations of rest-frame UV
lines require multiple hours of integration time on a 10 m-class telescope.


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 3


**Table 1.** Sources studied in this work (colours for reference). Coordinates are given as right ascension ( _𝛼_ J2000 ), declination ( _𝛿_ J2000 ), and redshift ( _𝑧_ ). These
are followed by general properties of the galaxies: the apparent magnitude ( _𝑚_ UV ) and luminosity ( _𝐿_ UV ) of the rest-frame UV, the stellar mass ( _𝑀_ ∗ ), and the
EW of the optical [O iii] and Hβ lines, EW([O iii] + Hβ), as presented in the works by Smit et al. (2015, 2018) and Schouws et al. (2022a,b).


Source _𝛼_ J2000 (h) _𝛿_ J2000 (deg) _𝑧_ _𝑚_ UV (mag) _𝐿_ UV (10 [11] L ⊙ ) _𝑀_ ∗ (10 [9] M ⊙ ) EW([O iii] + Hβ) (Å)

COS-2987030247 10:00:29.8700 02:13:02.470 6.8076 24 _._ 8 ± 0 _._ 1 1 _._ 3 ± 0 _._ 1 1 _._ 70 [+] − [0] 0 _[.]_ _._ [49] 18 1128 [+] − [166] 166
COS-3018555981 10:00:30.1850 02:15:59.810 6.8540 24 _._ 9 ± 0 _._ 1 1 _._ 1 ± 0 _._ 1 1 _._ 38 [+] − [0] 0 _[.]_ _._ [71] 21 1424 [+] − [143] 143
UVISTA-Z-001 10:00:43.3600 02:37:51.300 7.0611 23 _._ 9 ± 0 _._ 1 2 _._ 9 ± 0 _._ 1 3 _._ 80 [+] − [0] 2 _[.]_ _._ [88] 10 1004 [+] − [442] 206
UVISTA-Z-007 09:58:46.2100 02:28:45.800 6.7498 24 _._ 5 ± 0 _._ 1 1 _._ 5 ± 0 _._ 2 3 _._ 72 [+] − [4] 2 _[.]_ _._ [60] 37 761 [+] − [530] 168
UVISTA-Z-019 10:00:29.8900 01:46:46.400 6.7544 25 _._ 1 ± 0 _._ 2 1 _._ 0 ± 0 _._ 1 3 _._ 24 [+] − [1] 1 _[.]_ _._ [78] 10 628 [+] − [226] 99


**Table 2.** Overview of ALMA observations of the five _𝑧_ ∼ 7 galaxies. For each emission line observed, the observed frequency ( _𝜈_ obs ), total on-source integration
time ( _𝑡_ int ), and channel width (Δ _𝜈_ obs ) are shown. The first indicated beam size, _𝐴_ beam (given as the FWHMs of the major and minor axes), is the one tuned
to match the beam between [C ii] and [O iii] as closely as possible, which is achieved by the listed weighting scheme of either natural or Briggs weighting,
an (optional) _𝑢𝑣_ taper, and the robust parameter (for Briggs weighting; see also Section 2.2.2). The second beam size indicated for a line is one using natural
weighting without tapering. The RMS noise (per channel of the given width) in naturally weighted images is shown in the second to last column, in good
agreement with the theoretically predicted sensitivity (in brackets) computed for use in the tclean task (Section 2.2.2). The final column lists the ALMA
project codes (Section 2.2.1).


Source Emission line _𝜈_ obs _𝑡_ int Δ _𝜈_ obs Weighting scheme: _𝐴_ beam RMS (sensitivity) ALMA project
(GHz) (h) (MHz) (μJy/beam) code(s)
COS-2987030247 [C ii] 158 μm 243.429 3.6 40 Natural (0 _._ 4 [′′] ): 0 _._ 7 [′′] ×0 _._ 6 [′′] 2015.1.01111.S, 2018.1.01359.S

Natural: 0 _._ 4 [′′] × 0 _._ 4 [′′] 76 _._ 3 (89 _._ 5)

[O iii] 88 μm 434.575 1.1 70 Briggs (0 _._ 5): 0 _._ 7 [′′] × 0 _._ 5 [′′] 2018.1.00429.S

Natural: 0 _._ 8 [′′] × 0 _._ 6 [′′] 487 (548)

[N ii] 205 μm 186.996 1.3 30 Natural: 0 _._ 8 [′′] × 0 _._ 7 [′′] 166 (202) 2018.1.01551.S


COS-3018555981 [C ii] 158 μm 241.991 14 40 Natural (0 _._ 4 [′′] ): 0 _._ 6 [′′] ×0 _._ 6 [′′] 2015.1.01111.S, 2017.1.00604.S

Natural: 0 _._ 4 [′′] × 0 _._ 4 [′′] 45 _._ 0 (48 _._ 7)

[O iii] 88 μm 432.008 0.99 70 Briggs (0 _._ 5): 0 _._ 7 [′′] × 0 _._ 5 [′′] 2018.1.00429.S

Natural: 0 _._ 9 [′′] × 0 _._ 6 [′′] 429 (456)


UVISTA-Z-001 [C ii] 158 μm 235.774 4.2 40 Natural: 0 _._ 6 [′′] × 0 _._ 5 [′′] 234 (119) 2015.1.00540.S, 2018.1.00085.S,
2018.1.00933.S, 2019.1.01611.S

[O iii] 88 μm 420.909 1.3 70 Natural (0 _._ 2 [′′] ): 0 _._ 6 [′′] ×0 _._ 5 [′′] 2019.1.01524.S

Natural: 0 _._ 5 [′′] × 0 _._ 5 [′′] 435 (465)


UVISTA-Z-007 [C ii] 158 μm 245.244 0.44 40 Briggs (1 _._ 0): 1 _._ 3 [′′] × 1 _._ 1 [′′] 2018.1.00085.S

Natural: 1 _._ 4 [′′] × 1 _._ 2 [′′] 272 (286)

[O iii] 88 μm 437.817 1.6 70 Natural (1 _._ 0 [′′] ): 1 _._ 1 [′′] ×1 _._ 1 [′′] 2019.1.01524.S

Natural: 0 _._ 6 [′′] × 0 _._ 5 [′′] 738 (641)


UVISTA-Z-019 [C ii] 158 μm 245.099 4.4 40 Natural (0 _._ 2 [′′] ): 0 _._ 4 [′′] ×0 _._ 4 [′′] 2018.1.00085.S, 2019.1.01611.S

Natural: 0 _._ 4 [′′] × 0 _._ 3 [′′] 81 _._ 2 (92 _._ 3)

[O iii] 88 μm 437.557 0.89 70 Briggs (1 _._ 5): 0 _._ 5 [′′] × 0 _._ 4 [′′] 2019.1.01524.S

Natural: 0 _._ 5 [′′] × 0 _._ 4 [′′] 1015 (680)



can namely only escape from galaxies occupying ionised bubbles,
which are indicative of overdense regions (e.g. Leonova et al. 2021).


Our outline is as follows. Section 2 discusses the available

ALMA and _HST_ data and Section 3 briefly discusses the results of
these observations. In Sections 4 and 5, we compare our findings
concerning respectively the dust continuum and emission lines to
other works in the literature and discuss our findings. Section 6
provides a summary.


In our analysis, we adopt the cosmological parameters Ω m =
0 _._ 3, Ω Λ = 0 _._ 7, and _𝐻_ 0 = 70 km s [−][1] Mpc [−][1] throughout (implying
an angular scale of 5 _._ 2 kpc/arcsec at _𝑧_ = 7). All magnitudes are in
the AB system (Oke & Gunn 1983).


MNRAS **000**, 1–23 (2022)



**2** **OBSERVATIONS**


**2.1** **Target selection**


Five galaxies at _𝑧_ ∼ 7, all located in the ∼ 2 deg [2] UltraVISTA field (UVISTA; McCracken et al. 2012), are considered
in this work: COS-2987030247, COS-3018555981, UVISTA-Z001, UVISTA-Z-007, and UVISTA-Z-019 (Table 1). The first two,
COS-2987030247 and COS-3018555981, are contained in the _HST_
CANDELS field (Grogin et al. 2011) and were spectroscopically
confirmed with ALMA observations of [C ii] 158 μm in Cycle
3 (ALMA project code 2015.1.01111.S; Smit et al. 2018). The
two sources were selected for their large optical emission line
EWs, which enables an accurate photometric redshift determination using _Spitzer_ /IRAC broadband photometry at 3 _._ 6 μm and
4 _._ 5 μm (see Smit et al. 2015 for details). The EWs of the optical [O iii] (notably at 4960 Å and 5008 Å) and Hβ lines (hereafter
simply EW([O iii] + Hβ)), presented in Smit et al. (2015), are

4 _J. Witstok et al._


EW([O iii] + Hβ) _>_ 1000 Å, while the median EW at _𝑧_ ∼ 7 is
around 1000 Å (see e.g. Endsley et al. 2021). All five sources are
bright in the UV, with apparent magnitudes between 24 and 25 mag,
implying _𝐿_ UV ∼ 2 _𝐿_ UV [∗] [(] _[𝑧]_ [∼] [7][)][. SED fitting with a][ Chabrier][ (][2003][)]
initial mass function (IMF) yields stellar masses between 1 and 4
times 10 [9] M ⊙ (Smit et al. 2018; Schouws et al. 2022b; see Table 1).
The precise photometric redshift allowed ALMA to perform
efficient blind spectral scans to search for the [C ii] line without
first requiring a spectroscopic confirmation through Lyα. Its success encouraged a second programme in Cycle 6 (2018.1.00085.S;
Schouws et al. 2022a) that has successfully detected the [C ii] line
in three out of six additional galaxies, selected from ground-based
imaging in the wider COSMOS field. Among these are the latter
three sources considered here (UVISTA-Z-001, UVISTA-Z-007,
and UVISTA-Z-019), two of which in comparison have modest
EWs (presented in Schouws et al. 2022a), EW([O iii] + Hβ) ∼ 600700 Å, more typical for UV-bright LBGs at _𝑧_ ∼ 7 (e.g. Endsley
et al. 2021). For an in-depth description of ALMA target selection
strategies and scanning efficacy of [C ii] we refer to Bouwens et al.
(2022), introducing the successor of these two pilot programmes,
the Reionization Era Bright Emission Line Survey (REBELS). This
ALMA Large Program has targeted [C ii] and [O iii] in 40 of the
brightest UV-selected star-forming galaxy candidates at _𝑧>_ 6 _._ 5.


**2.2** **ALMA data**


An overview of the ALMA observations considered in this work is

shown in Table 2. In the following sections, we will briefly describe
the existing ALMA observations of the [C ii] 158 μm line, and the
data reduction process of new measurements of the [O iii] 88 μm
and [N ii] 205 μm lines and the underlying dust continuum.


_2.2.1_ _ALMA programmes used in this study_


In this study, we consider three main follow-up programmes of
the bright LBGs that were confirmed with [C ii] described in Section 2.1. COS-2987030247 was observed in band 5, targeting the

[N ii] 205 μm line with programme 2018.1.01551.S in Cycle 6 (note
that for COS-3018555981 [N ii] 205 μm falls into the atmospheric
feature at the centre of band 5 and could not be included in this

programme). All five bright [C ii] emitting galaxies described in
Section 2.1, were approved for A-ranked observations in band 8 in
Cycle 6 (project code 2018.1.00429.S) and 7 (2019.1.01524.S) for
the CANDELS-COSMOS and UVISTA sources, respectively.
Finally, we also make use of additional [C ii] data that was
taken at high angular resolution ( _𝜃_ beam _<_ 0 _._ 2 [′′] ), co-adding these
with the low-resolution data for all sources except UVISTA-Z007 (2017.1.00604.S, 2018.1.01359.S, 2019.1.01611.S). Similarly,
we include additional band-6 observations of the dust continuum

in UVISTA-Z-001 (2015.1.00540.S, 2018.1.00933.S) presented in
Bowler et al. (2018, 2022).


_2.2.2_ _ALMA data reduction_


All data, including previous observations discussed above (see Table 2), were calibrated and reduced with the automated pipeline of
the Common Astronomy Software Application (casa; McMullin
et al. 2007) version 5.6 (with the exception of 2015.1.00540.S and
2015.1.01111.S, which required version 4.7).
Before the imaging step, we performed the uvcontsub task to



where _𝑘_ B is the Boltzmann constant, _𝑁_ ant is the number of antennas
(where we take the mean if observations obtained with multiple
configurations are combined), _𝑡_ int is the total on-source integration
time, Δ _𝜈_ is the channel width, _𝑇_ sys is the system temperature, and
_𝐴_ eff is the effective collective area of each dish. Given the dish
radius _𝑟_ ant,


_𝐴_ eff = _𝜂𝜋𝑟_ ant [2] _[,]_


which is equal to ∼ 80 m [2] for the 12-meter ALMA antennae assuming an efficiency factor of _𝜂_ ∼ 0 _._ 7 (Cortes et al. 2020). These
sensitivities, which agree well with the empirically measured RMS
noise, were computed for use in the tclean task, where the threshold parameter was set to three times this value.


**2.3** _**HST**_ **imaging**


For sources at a redshift of _𝑧_ ∼ 7, the rest-frame UV is observed in
the NIR, ideally suited for observations with the infrared channel of


2 We note this is a simplified formula which leaves out a few additional
system efficiencies; see Section 9.2.1 of the ALMA Technical Handbook
(Cortes et al. 2020) for a more detailed form.


MNRAS **000**, 1–23 (2022)



separate the continuum and line visibilities specifically for imaging the [C ii] emission in COS-3018555981, UVISTA-Z-001, and
UVISTA-Z-019 as well as the [O iii] emission in UVISTA-Z-001,
where the underlying dust continuum is confidently detected (Section 3.1; see also Schouws et al. 2022b). Images were made with
the tclean task for a large range of parameter sets, using all available data sets combined. We created images using both natural and
Briggs weightings; under the natural weighting scheme, several different _𝑢𝑣_ tapers were considered as well as no taper. For measuring
the total [O iii] and [C ii] line fluxes, a moderately (0 _._ 6 [′′] ) tapered
image was chosen to avoid resolving out extended emission (see e.g.
Carniani et al. 2018a, 2020) as best as possible while maintaining
a good signal-to-noise ratio (SNR). However, a natural weighting
without any tapering was considered for the [N ii] line to maximise
the SNR. Continuum images were created by averaging (i.e. the mfs
mode in tclean) over all available spectral channels that were well
outside the relevant emission line range (i.e. | _𝑣_ | _>_ 1000 km/s). Natural weighting was again used for optimal SNR, however given the
heterogeneity of the ALMA data, the following tapers were applied
on a case-by-case basis to match the beams across various bands:
0 _._ 4 [′′] for the band-6 data of COS-2987030247, 0 _._ 6 [′′] for the band-6
data of COS-3018555981, 0 _._ 8 [′′] for the band-8 data of UVISTA-Z001, 1 _._ 0 [′′] for the band-8 data of UVISTA-Z-007, and 0 _._ 2 [′′] for the

band-6 data of UVISTA-Z-019.

Finally, when comparing the [C ii] and [O iii] lines, we also
tuned the weighting or taper scheme to match the beam sizes as
closely as possible. We use Briggs weighting for the line observed
with lowest spatial resolution with a robust parameter tuned to the
highest resolution achievable while maintaining a reasonable SNR.
The other line is imaged with natural weighting and, if required,
a small taper. Table 2 lists the resulting matched beam sizes for

[C ii] and [O iii] (as well as beam sizes obtained with an untapered,
natural-weighting scheme). Furthermore, the measured root-meansquare (RMS) noise in naturally weighted images is compared in
Table 2 to the theoretically expected value of the sensitivity of an
interferometric image (Thompson et al. 2017), [2]



_𝛿𝑆_ _𝜈_ = 2 _𝑘_ B _𝑇_ sys



_𝐴_ eff ~~√~~



_,_ (1)
_𝑁_ ant ( _𝑁_ ant − 1) _𝑡_ int Δ _𝜈_

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 5











1.5 0.0 1.5







1.5 0.0 1.5





1.5 0.0 1.5







































**Figure 1.** Naturally weighted dust continuum maps of COS-3018555981 (first column), UVISTA-Z-001 (second column), and UVISTA-Z-019 (third column);
beam sizes are indicated in the bottom left. Top row: clear detections at _𝜆_ emit ∼ 160 μm (imaged with varying degrees of taper; see Sections 2.2.2 and 3.1).
Grey contours show subsequent significance levels in steps of 2 _𝜎_ (COS-3018555981) or 1 _𝜎_ (UVISTA-Z-001 and UVISTA-Z-019), starting at 3 _𝜎_ . White
ellipses show the two-dimensional Gaussian fit obtained by imfit procedure in casa. Bottom row: (non-)detections at _𝜆_ emit ∼ 90 μm. Contours are the same as
the top row for UVISTA-Z-001, otherwise solid (dashed) grey lines show positive (negative) 1 _𝜎_, 2 _𝜎_, and 3 _𝜎_ contours and white ellipses show the aperture
used for determining a flux density upper limit (Section 3.1). Since there is significant extended emission at ∼ 160 μm in UVISTA-Z-001, the white ellipses
show the aperture used to measure the flux of the compact component in both the top and bottom panels (Section 3.1).



the Wide Field Camera 3 (WFC3) on board _HST_ . For the two sources
in the COSMOS field, COS-2987030247 and COS-3018555981,
_HST_ imaging is available in the F125W ( _𝐽_ 125 ), F140W ( _𝐽𝐻_ 140 ),
and F160W ( _𝐻_ 160 ) filters as part of CANDELS (GO 12440, PI:
Faber) and the 3D-HST Treasury Programs (GO 12328, PI: Van
Dokkum). [3] Combined, these observations reach a median depth of
26 _._ 1 mag, 25 _._ 5 mag, and 25 _._ 8 mag (5 _𝜎_ for a 1 [′′] -diameter aperture)
in the _𝐽_ 125, _𝐽𝐻_ 140, and _𝐻_ 160 bands, respectively (Grogin et al. 2011;
Koekemoer et al. 2011; Skelton et al. 2014). Throughout this work,
we use a single stacked image, created by weighting the three filters
by their inverse variance (covering 1400 Å ≲ _𝜆_ emit ≲ 2200 Å).
For UVISTA-Z-001, we use _HST_ imaging in the F140W filter (GO
13793, PI: Bowler) presented in Bowler et al. (2017). [4]

For COS-2987030247, we manually remove a foreground
source to the north-west. The foreground source is offset by just
under 1 [′′] and clearly (above 5 _𝜎_ ) detected in the Advanced Camera
for Surveys (ACS) F606W and F814W filters, while for sources at
_𝑧_ ∼ 6 _._ 8, the IGM would absorb any emission below the Lymancontinuum limit at a rest-frame wavelength of 912 Å (observed at
∼ 0 _._ 7 μm). In our stacked image, we replaced pixels with artificial


3 High-level science products are available on `[https://archive.stsci.](https://archive.stsci.edu/prepds/3d-hst/)`
`[edu/prepds/3d-hst/](https://archive.stsci.edu/prepds/3d-hst/)` .
4 [Data may be obtained from the MAST at 10.17909/6gya-3b10.](https://dx.doi.org/10.17909/6gya-3b10)


MNRAS **000**, 1–23 (2022)



noise if they are detected above 4 _𝜎_ in a weighted ACS image that
has been smoothed to match the slightly more extended point spread
function (PSF) of WFC3.
In addition, _HST_ observations to acquire rest-frame UV imaging of UVISTA-Z-007 and UVISTA-Z-019 were awarded in Cycle 28 in the Mid-Cycle General Observer programme ID 16506
(PI: Witstok). [5] Observations were performed with WFC3 using the
F140W ( _𝐽𝐻_ 140 ) filter with a 5 ks exposure per target, motivated by
the goal of properly resolving the spatial substructure of the restframe UV. We divided each orbit into 4 exposures, which allows for
a four-point dithering pattern to improve sampling of the PSF and
to remove bad pixels, cosmic ray impacts, and detector artefacts.
We used the SPARS50 sampling sequence with nsamp = 13 and
nsamp = 14 in two subsequent orbits for both targets.
Calibrated data products were combined using the AstroDrizzle task (e.g. Fruchter & Hook 2002) within the DrizzlePac package [6] setting the final_pixfrac parameter to 0 _._ 8 and choosing a
pixel size of 0 _._ 065 [′′] . The resulting images reach a 5 _𝜎_ depth of
27 _._ 7 mag for a 0 _._ 5 [′′] -diameter aperture (i.e. 25 _._ 9 mag/arcsec [2] ).
The astrometry of all images was calibrated to _Gaia_ data (Gaia


5 [Data may be obtained from the MAST at 10.17909/T9-JHSF-M392.](https://dx.doi.org/10.17909/t9-jhsf-m392)
6 See `[https://www.stsci.edu/scientific-community/](https://www.stsci.edu/scientific-community/software/drizzlepac.html)`
`[software/drizzlepac.html](https://www.stsci.edu/scientific-community/software/drizzlepac.html)` .

6 _J. Witstok et al._


Collaboration et al. 2016, 2021) by fitting a two-dimensional Gaussian to the _HST_ images of a number of nearby stars with a _𝑔_ -band
magnitude of _𝑔_ ≲ 21 mag (7, 5, 6, 4, and 2 for COS-2987030247,
COS-3018555981, UVISTA-Z-001, UVISTA-Z-007, and UVISTAZ-019, respectively). Among the stars in each field, we found the
measured peak offsets relative to _Gaia_ positions agreed very well
within less than 0 _._ 05 [′′] ; taken together, they resulted in a required
median correction of less than about 0 _._ 1 [′′] in all cases.


**3** **RESULTS**


**3.1** **Dust continuum**


Except for a ∼ 4 _𝜎_ detection in UVISTA-Z-001, the dust continuum
at a rest-frame wavelength of _𝜆_ emit ∼ 90 μm remains undetected
for the other sources. The same holds for the dust continuum of

COS-2987030247 around the [N ii] line at 205 μm. The continuum at _𝜆_ emit ∼ 160 μm, however, is detected in COS-3018555981,
UVISTA-Z-001, and UVISTA-Z-019 (see also Schouws et al.
2022b; Bowler et al. 2022). Dust continuum maps of these sources
are shown in Figure 1.
For consistency in the flux measurements across different
ALMA bands, their beams are matched by applying a slight taper
to higher resolution data (see Section 2.2.2). For COS-3018555981
and UVISTA-Z-019, we place 3 _𝜎_ upper limits at ∼ 90 μm by empirically measuring the RMS noise in a beam-shaped aperture matched
in (convolved) size to the source extent at ∼ 160 μm; for COS2987030247 and UVISTA-Z-007, a (FWHM) beam-sized aperture
is used. Since there is significant extended emission at ∼ 160 μm
in UVISTA-Z-001, we measure fluxes of the compact component
in an aperture centred on the peak of the emission and matched
in (convolved) size to the source extent at ∼ 90 μm (implications
for the inferred dust properties will be discussed in Section 4). In
estimating the uncertainties on our continuum detections as well as
upper limits, we conservatively take a systematic flux calibration
uncertainty into account (10% in band 5 and 6, 20% in band 8). [7]

In Table 3, all continuum measurements around the three emission lines (including _𝐴_ dust, the deconvolved source extent in kpc [2], if
detected) are summarised. Also presented in Table 3 are other characteristics of the sources like their corresponding total IR and FIR
luminosities (defined as the integrated luminosity between 8 and
1000 μm and between 42 _._ 5 and 122 _._ 5 μm in the rest frame, respectively; see e.g. Reuter et al. 2020) and other dust properties, leveraging constraints from the combined continuum measurements. These
properties have been derived from a best-fit “greybody” spectrum
(e.g. Casey et al. 2014) if possible and will be discussed in more
detail in Section 4. When only upper limits are available (i.e. for
COS-2987030247 and UVISTA-Z-007; see Section 4.1), we report
3 _𝜎_ upper limits on the IR and FIR luminosities by assuming a fiducial _𝛽_ IR = 1 _._ 5 and _𝑇_ dust = 50 K; we acknowledge the uncertainty
on these parameters by adding an additional 0 _._ 4 dex systematic uncertainty to the integrated luminosities and corresponding obscured
SFR (cf. Carniani et al. 2020) before setting upper limits.


**3.2** **[N ii] 205** μm


We placed a 3 _𝜎_ upper limit on the [N ii] luminosity of COS2987030247 by first measuring the RMS noise in the untapered,
naturally-weighted datacube over a single beam (assuming the


7 See Section A.9.2 of the ALMA Proposers’ Guide (Braatz et al. 2021).



source is unresolved). We obtained an upper limit on the line flux
in Jy km/s by scaling this noise to a range of channels covering
twice the maximum FWHM between the [O iii] and [C ii] lines
(Section 3.3), which we then converted to a luminosity, as shown in
Table 4. The lower limit on the [C ii] 158 μm to [N ii] 205 μm ratio
is _𝐿_ [C ii] / _𝐿_ [N ii] _>_ 4 _._ 8 (3 _𝜎_ ).


**3.3** **[O iii] 88** μm **and [C ii] 158** μm


We obtained moment-zero maps by integrating a naturally weighted,
clean datacube over the FWHM around the line centre. Defining
the SNR as that measured for the peak pixel, the [O iii] and [C ii]
lines are detected with a significance of at least SNR _>_ 5 in all
five sources. Total line fluxes, however, are measured on cleaned
cubes with a 0 _._ 6 [′′] taper to recover extended emission as well as
possible (Section 2.2.2), integrating all channels where line flux is
detected (coloured channels in Figure 2) in a spectrum extracted
from a contiguous region of spaxels reaching at least 2 _𝜎_ in the
moment-zero map, the spectrum each spaxel weighted by its SNR.
In turn, this initial moment-zero map was created by integrating
channels within half of the FWHM from the line centre (used in the
SNR determination described above). Again, we take a conservative
systematic flux calibration uncertainty into account, as discussed in
Section 3.1. The resulting line fluxes, luminosities, and ratios are
listed in Table 4.


**4** **DUST PROPERTIES**


Although accounting for only a small fraction of baryonic matter in
galaxies, dust is highly relevant in the context of galaxy evolution
(e.g. Liang et al. 2019). Representative dust properties of EoR galaxies, however, are still difficult to constrain with current observations
partly due to the degeneracy between dust mass and temperature,
complicated further by the dust opacity. Only in a few cases, multiple constraints on the FIR SED of normal star-forming galaxies
(SFR ≲ 100 M ⊙ yr [−][1] ) in the EoR are available (e.g. Hashimoto
et al. 2019; Bakx et al. 2020, 2021). Here, we use the available

band-6 detections in combination with the non-detections in band

8 to obtain further insights into the (F)IR luminosity, _𝐿_ (F)IR, corresponding obscured and total SFR, [8] dust mass (Section 4.2), and
dust temperature (Section 4.3) of typical UV-bright EoR galaxies.


**4.1** **Dust SED fitting procedure**


A dust-continuum detection at _𝜆_ emit ∼ 160 μm combined with a detection (UVISTA-Z-001) or even an upper limit (COS-3018555981
and UVISTA-Z-019) at _𝜆_ emit ∼ 90 μm can provide insight into
the dust properties beyond those derived with a fixed temperature,
emissivity, and opacity model. To investigate this in detail, we performed a fitting routine using the multimodal nested sampling algorithm multinest (described in Feroz et al. 2009) implemented in
python as the pymultinest package (Buchner et al. 2014), as described below. The full code of this routine which treats detections

and upper limits uniformly and we therefore refer to as mercurius
(Multimodal Estimation Routine for the Cosmological Unravelling
of Rest-frame Infrared Uniformised Spectra), is available online. [9]


8 Obtained from the UV and IR luminosities using the conversions in Kennicutt & Evans (2012).
9 See `[https://github.com/joriswitstok/mercurius/](https://github.com/joriswitstok/mercurius/)` .


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 7


**Table 3.** Average, minimum, and maximum channel rest-frame wavelength and observed frequency used for the aggregate continuum images and corresponding
(upper limits on) continuum fluxes. For non-detections, 3 _𝜎_ upper limits are given (with theoretical 3 _𝜎_ sensitivities, given by equation (1), in brackets). For
detections, deconvolved sizes _𝐴_ dust as measured by the casa imfit procedure are given. Dust-related quantities listed are the mass _𝑀_ dust, mass surface density
Σ dust, and yield _𝑦_ dust, discussed in Section 4.2; the intrinsic SED temperature _𝑇_ dust and peak temperature _𝑇_ peak, discussed in Section 4.3; the integrated IR and
FIR luminosities ( _𝐿_ (F)IR ); and finally, the obscured and total SFRs, SFR IR and SFR tot . These properties are inferred from mercurius fits where possible (i.e.
for COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019), under the fiducial self-consistent opacity model (for a more in-depth discussion, see Section 4.1).
Otherwise, they are approximated under a fully optically thin SED with the fiducial assumptions of _𝑇_ dust = 50 K, _𝛽_ IR = 1 _._ 5, which however introduces large
systematic uncertainties (see Section 3.1 for details). For COS-3018555981, an upper limit (95% confidence) on the dust temperatures is reported in brackets.


Regime Quantity COS-2987030247 COS-3018555981 UVISTA-Z-001 UVISTA-Z-007 UVISTA-Z-019



Band 8


Band 6



_𝜈_ obs (GHz) 426 _._ 2 [+] − [9] 6 _[.]_ _._ [3] 7 422 _._ 5 [+] − [8] 5 _[.]_ _._ [4] 4 413 _._ 0 [+] − [8] 6 _[.]_ _._ [9] 9 434 _._ 5 [+] − [6] 7 _[.]_ _._ [2] 7 434 _._ 4 [+] − [6] 7 _[.]_ _._ [1] 8
_𝜆_ emit (μm) 90 _._ 1 − [+][1] 1 _[.]_ _._ [4] 9 90 _._ 3 [+] − [1] 1 _[.]_ _._ [2] 8 90 _._ 0 [+] − [1] 1 _[.]_ _._ [5] 9 89 _._ 0 [+] − [1] 1 _[.]_ _._ [6] 3 89 _._ 0 [+] − [1] 1 _[.]_ _._ [6] 2
_𝑆_ _𝜈_, obs (μJy) _<_ 163 (160) _<_ 210 (240) 189 ± 100 _<_ 361 (260) _<_ 840 (625)

_𝐴_ dust (kpc [2] ) . . . . . . (5 _._ 2 ± 2 _._ 4)× . . . . . .
(2 _._ 0 ± 1 _._ 3)


_𝜈_ obs (GHz) 250 _._ 3 − [+][7] 9 _[.]_ _._ [3] 8 232 _._ 1 [+] − [13] 8 _._ 0 _[.]_ [3] 232 _._ 9 [+] − [10] 16 _[.]_ _._ [0] 0 242 _._ 4 [+] − [2] 2 _[.]_ _._ [0] 1 237 _._ 3 [+] − [8] 11 _[.]_ [8] _._ 0
_𝜆_ emit (μm) 153 _._ 4 [+] − [6] 4 _[.]_ _._ [2] 4 164 _._ 5 [+] − [5] 8 _[.]_ _._ [9] 9 159 _._ 6 [+] − [11] 6 _._ 6 _[.]_ [8] 159 _._ 6 [+] − [1] 1 _[.]_ _._ [4] 3 162 _._ 9 [+] − [7] 5 _[.]_ _._ [9] 8
_𝑆_ _𝜈_, obs (μJy) _<_ 22 _._ 5 (18 _._ 4) 76 ± 13 97 ± 30 _<_ 69 _._ 6 (81 _._ 8) 131 ± 36

_𝐴_ dust (kpc [2] ) . . . (4 _._ 3 ± 0 _._ 8)× (10 _._ 3 ± 3 _._ 4)× . . . (4 _._ 1 ± 1 _._ 1)×
(3 _._ 6 ± 0 _._ 7) (3 _._ 7 ± 3 _._ 0) (3 _._ 0 ± 0 _._ 9)



_𝜈_ obs (GHz) 195 _._ 6 − [+][6] 9 _[.]_ _._ [4] 4 . . . . . . . . . . . .
Band 5 _𝜆_ emit (μm) 196 _._ 3 [+] − [9] 6 _[.]_ _._ [9] 3 . . . . . . . . . . . .



_𝑆_ _𝜈_, obs (μJy) _<_ 19 _._ 4 (22 _._ 8) . . . . . . . . . . . .


_𝑇_ dust Fixed: 50 K mercurius fit mercurius fit Fixed: 50 K mercurius fit


_𝜆_ 0 (opacity) Optically thin Self-consistent: Self-consistent: Optically thin Self-consistent:
8 _._ 4 [+] − [11] 4 _._ 4 _[.]_ [8] [μ][m] 0 _._ 6 [+] − [0] 0 _[.]_ _._ [7] 3 [μ][m] 4 _._ 2 [+] − [7] 2 _[.]_ _._ [5] 7 [μ][m]


_𝛽_ IR Fixed: 1 _._ 5 Fixed: 1 _._ 5 Fixed: 1 _._ 5 Fixed: 1 _._ 5 Fixed: 1 _._ 5


_𝑀_ dust (M ⊙ ) ≲ 4 · 10 [6] 7 [+] − [19] 5 [·][ 10] [7] 4 [+] − [8] 3 [·][ 10] [6] ≲ 1 · 10 [7] 2 _._ 1 [+] − [7] 1 _[.]_ _._ [6] 6 [·][ 10] [7]

Σ dust (M ⊙ pc [−][2] ) . . . 7 [+] − [18] 4 0 _._ 1 [+] − [0] 0 _[.]_ _._ [3] 1 . . . 2 _._ 3 [+] − [8] 1 _[.]_ _._ [5] 8
_𝑀_ dust / _𝑀_ ∗ ≲ 0 _._ 002 0 _._ 05 [+] − [0] 0 _[.]_ _._ [16] 04 0 _._ 001 [+] − [0] 0 _[.]_ _._ [003] 0007 ≲ 0 _._ 003 0 _._ 007 [+] − [0] 0 _[.]_ _._ [03] 006
_𝑦_ dust, AGB (M ⊙ ) ≲ 0 _._ 1 1 _._ 5 [+] − [4] 1 _[.]_ _._ [6] 1 0 _._ 03 [+] − [0] 0 _[.]_ _._ [08] 02 ≲ 0 _._ 1 0 _._ 2 [+] − [0] 0 _[.]_ _._ [9] 2
_𝑦_ dust, SN (M ⊙ ) ≲ 0 _._ 2 4 _._ 5 [+] − [13] 3 _._ 1 _[.]_ [3] 0 _._ 09 [+] − [0] 0 _[.]_ _._ [2] 06 ≲ 0 _._ 3 0 _._ 6 [+] − [2] 0 _._ 5


_𝑇_ dust (K) . . . 29 [+] − [9] 5 [(] _[<]_ [ 48)] 59 [+] − [41] 20 . . . 47 [+] − [40] 17
_𝑇_ peak (K) . . . 26 [+] − [8] 5 [(] _[<]_ [ 43)] 53 [+] − [37] 17 . . . 42 [+] − [35] 15


8-1000 μm _𝐿_ IR (L ⊙ ) ≲ 2 _._ 1 · 10 [11] 9 _._ 9 [+] − [6] 2 _[.]_ _._ [8] 3 [·][ 10] [10] 2 _._ 0 [+] − [9] 1 _[.]_ _._ [5] 3 [·][ 10] [11] ≲ 6 _._ 9 · 10 [11] 3 _._ 1 [+] − [18] 1 _._ 8 _[.]_ [1] [·][ 10] [11]

42 _._ 5-122 _._ 5 μm _𝐿_ FIR (L ⊙ ) ≲ 1 _._ 4 · 10 [11] 6 _._ 4 [+] − [4] 1 _[.]_ _._ [8] 6 [·][ 10] [10] 1 _._ 1 [+] − [1] 0 _[.]_ _._ [1] 6 [·][ 10] [11] ≲ 4 _._ 7 · 10 [11] 2 _._ 1 [+] − [4] 1 _[.]_ _._ [2] 3 [·][ 10] [11]


IR (8-1000 μm) SFR IR (M ⊙ yr [−][1] ) ≲ 32 15 [+] − [10] 3 30 [+] − [142] 20 ≲ 102 46 [+] − [270] 27
UV + IR SFR tot (M ⊙ yr [−][1] ) ≲ 54 34 [+] − [10] 4 79 [+] − [142] 20 ≲ 128 63 [+] − [270] 27


**Table 4.** Observed line fluxes ( _𝐹_ line ) of [C ii] 158 μm, [O iii] 88 μm, and [N ii] 205 μm, given in units of Jy km/s (i.e. as _𝑆_ _𝜈_ Δ _𝑣_ ; see Sections 3.2 and 3.3 for
details). Also shown are corresponding line luminosities and the [O iii]/[C ii] luminosity ratio. For non-detections, 3 _𝜎_ upper limits are given.


Source _𝐹_ [C ii] (Jy km/s) _𝐿_ [C ii] (10 [8] L ⊙ ) _𝐹_ [O iii] (Jy km/s) _𝐿_ [O iii] (10 [8] L ⊙ ) _𝐿_ [O iii] / _𝐿_ [C ii] _𝐹_ [N ii] (Jy km/s) _𝐿_ [N ii] (10 [8] L ⊙ )
COS-2987030247 0 _._ 250 ± 0 _._ 061 2 _._ 83 ± 0 _._ 69 0 _._ 79 ± 0 _._ 20 16 _._ 0 ± 4 _._ 1 5 _._ 7 ± 1 _._ 8 _<_ 0 _._ 0679 _<_ 0 _._ 591

COS-3018555981 0 _._ 347 ± 0 _._ 027 3 _._ 97 ± 0 _._ 31 1 _._ 58 ± 0 _._ 29 32 _._ 3 ± 5 _._ 9 8 _._ 13 ± 0 _._ 92 . . . . . .

UVISTA-Z-001 0 _._ 564 ± 0 _._ 095 6 _._ 7 ± 1 _._ 1 0 _._ 92 ± 0 _._ 22 19 _._ 6 ± 4 _._ 7 2 _._ 91 ± 0 _._ 66 . . . . . .

UVISTA-Z-007 0 _._ 408 ± 0 _._ 065 4 _._ 57 ± 0 _._ 73 0 _._ 65 ± 0 _._ 30 12 _._ 9 ± 5 _._ 9 2 _._ 8 ± 1 _._ 0 . . . . . .

UVISTA-Z-019 0 _._ 686 ± 0 _._ 049 7 _._ 69 ± 0 _._ 55 0 _._ 83 ± 0 _._ 35 16 _._ 6 ± 7 _._ 0 2 _._ 16 ± 0 _._ 54 . . . . . .



Apart from the main fitting procedure, it also includes a greybody
SED exploration visualisation tool; both are illustrated in a documented example.


Radiative transfer predicts the intensity emerging from a region
of dust at a temperature _𝑇_ dust becomes a modified black body (often


MNRAS **000**, 1–23 (2022)



referred to as a greybody; e.g. Jones et al. 2020a),


_𝐽_ _𝜈_ = �1 − _𝑒_ [−] _[𝜏]_ [(] _[𝜈]_ [)] [�] _𝐵_ _𝜈_ � _𝑇_ dust � _,_ (2)


where _𝐵_ _𝜈_ is the Planck function (Planck 1901), a specific intensity
in units of erg s [−][1] cm [−][2] sr [−][1] Hz [−][1] that is attenuated by the opacity

8 _J. Witstok et al._

































































**Figure** **2.** Detections of the [C ii] 158 μm and [O iii] 88 μm lines. Top row: contour images of the [C ii] and [O iii] lines overlaid on a background of _HST_
rest-frame UV images (see Section 2.3). The line images have matched beam sizes (as listed in Table 2) and are produced by collapsing all channels within
the FWHM of the line (as those of the SNR determination, which however use natural weighting without tapering; Section 3.3). Contours start at 3 _𝜎_ and
increase in steps of 5 _𝜎_ for the [C ii] contours in COS-3018555981 and UVISTA-Z-019, 3 _𝜎_ for the [O iii] contours in COS-3018555981, 2 _𝜎_ for both lines
in UVISTA-Z-001, and 1 _𝜎_ otherwise. Bottom row: SNR-weighted line spectra extracted from a 2 _𝜎_ region in a naturally weighted image integrated over the
FWHM (cf. Section 3.3). Coloured channels, which were used to produce a subsequent moment-zero map for measuring the total line flux, indicate the line
detection. The significance of each line detection is shown in the legend (also see Section 3.3 for details).



term containing the optical depth, _𝜏_ ( _𝜈_ ). However, the observed
flux needs to be corrected for the effect of observing against the
isotropic Cosmic Microwave Background (CMB), which involves
subtracting the Planck function for _𝑇_ CMB ( _𝑧_ ), the CMB temperature
at redshift _𝑧_, from the dust blackbody term (as in equation (18) in da
Cunha et al. 2013). The flux density observed at _𝜈_ obs = _𝜈_ /(1 + _𝑧_ ), [10]

denoted _𝑆_ _𝜈_, obs and given in erg s [−][1] cm [−][2] Hz [−][1], is then given by the
following general form of the observed SED (see also Jones et al.
2020a),



in casa (given in Table 3; see e.g. Figure 1). The absorption cross
section (per unit mass), _𝜅_ _𝜈_, is the frequency-dependent constant
of proportionality. This frequency dependence is parametrised via
a power law with the dust emissivity _𝛽_ IR as its exponent (Draine
2006),



_𝛽_ IR
_._ (5)
�



_𝜅_ _𝜈_ = _𝜅_ _𝜈,_ ref



_𝜈_
� _𝜈_ ref



_𝑆_ _𝜈_, obs = _[𝐴]_ [dust] [ (][1][ +] _[ 𝑧]_ [)]

_𝐷_ [2]
_𝐿_ [(] _[𝑧]_ [)]



�1 − _𝑒_ [−] _[𝜏]_ [(] _[𝜈]_ [)] [��] _𝐵_ _𝜈_ � _𝑇_ dust � − _𝐵_ _𝜈_ � _𝑇_ CMB ( _𝑧_ )�� _,_



Following Schouws et al. (2022b), we used _𝜅_ _𝜈,_ ref =
8 _._ 94 cm [2] g [−][1] at _𝜆_ ref = 158 μm (i.e. _𝜈_ ref = _𝜈_ [C ii] ≃ 1 _._ 90 THz), appropriate for dust ejected by supernovae (SNe) after reverse shock
destruction (values for different dust grain compositions range from
5 cm [2] g [−][1] ≲ _𝜅_ _𝜈,_ ref ≲ 30 cm [2] g [−][1] ; see Hirashita et al. 2014, and
references therein). As will be discussed in Section 4.2, SNe are the
most likely origin of dust in these young, metal-poor star-forming
galaxies. However, since the detailed dust composition is in principle unknown, _𝜅_ _𝜈,_ ref carries with it a systematic uncertainty that
can lower dust masses by ∼ 3× or increase them by ∼ 1 _._ 5×.
For convenience, the optical depth can be expressed in the form



(3)


where _𝐴_ dust is the area subtended by the source. In our fiducial
model, the optical depth is taken to be proportional to the dust mass
surface density Σ dust (Casey et al. 2014) via



_𝜏_ ( _𝜈_ ) ≡ _𝜅_ _𝜈_ Σ dust = _𝜅_ _𝜈_ _𝐶_ _[𝑀]_ [dust], with _𝐶_ ≥ 1 _._ (4)

_𝐴_ dust



Here, we substituted Σ dust by a combination of _𝐶_, a clustering
factor, [11] the dust mass _𝑀_ dust, and _𝐴_ dust, which we take to be the
deconvolved size of the dust emission found by the imfit procedure


10 We note that in quantities related to the emission process (such as _𝐵_ _𝜈_ ),
_𝜈_ is short for the rest-frame frequency _𝜈_ emit, whereas for the observable
quantity _𝑆_ _𝜈_, obs – the redshifted flux density in the observer’s frame – _𝜈_
implicitly stands for the observed frequency, introducing the factor (1 + _𝑧_ ).
11 We introduce the parameterisation of _𝐶_ to relate the true area of dust
emission _𝐴_ [∗] dust [(which] [can] [only] [be] [measured] [with] [infinitely] [high] [reso-]
lution) to its galaxy-averaged value, _𝐴_ dust, via Σ dust = _𝑀_ dust / _𝐴_ [∗] dust [=]
_𝐶𝑀_ dust / _𝐴_ dust, such that 1/ _𝐶_ represents the covering fraction of dust (we
note _𝐶_ ≥ 1 since Σ dust ≥ _𝑀_ dust / _𝐴_ dust ). Unless mentioned otherwise, we
assumed _𝐶_ = 1 throughout as would be expected for a homogeneous distribution, although a clustered dust distribution (on scales below the resolution
of interferometric observations), resulting in _𝐶>_ 1, may be more realistic
(see Section 4.3).



However, this assumption can lead to a significantly underestimated dust temperature and overestimated dust mass if incorrectly
applied on measurements that sample a region where the approx

MNRAS **000**, 1–23 (2022)



_𝜈_ _𝛽_ IR _𝜆_ 0
_𝜏_ ( _𝜈_ ) = =
� _𝜈_ 0 � � _𝜆_



_𝛽_ IR
_,_ (6)
�



which clearly marks the point at which the dust transitions from
optically thin to thick, at _𝜆_ 0 = _𝑐_ / _𝜈_ 0 . For LBGs at high redshift,
_𝜆_ 0 is typically assumed to be well below the sampled wavelength
regime so that it is safe to approximate the entire SED as being
optically thin ( _𝜏_ ( _𝜈_ ) ≪ 1; e.g. Bakx et al. 2021) which simply
reduces equation (3) to



1 + _𝑧_
_𝑆_ _𝜈_, obs = _𝑀_ dust _𝜅_ _𝜈_ � _𝐵_ _𝜈_ � _𝑇_ dust � − _𝐵_ _𝜈_ � _𝑇_ CMB ( _𝑧_ )�� _._ (7)

_𝐷_ [2]
_𝐿_ [(] _[𝑧]_ [)]

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 9



imation does not hold (Cortzen et al. 2020; Jones et al. 2020a). [12]

For a fixed _𝜆_ 0, an a posteriori consistency check on the assumed
opacity model can be performed, since it follows from equations (4)
to (6) that


1/ _𝛽_ IR
_𝜆_ 0 = � _𝜅_ _𝜈,_ ref Σ dust � _𝜆_ ref _._ (8)


Alternatively, equation (8) allows for a self-consistent framework around the general greybody SED model in equation (3) where,
given a dust mass, we infer _𝜆_ 0 a priori, which we took as our fiducial
opacity model.
Under a set opacity model, we then used a freely varying dust
temperature and logarithmic dust mass. As the number of free parameters should not exceed the number of constraints and different

assumptions of _𝜆_ 0 typically dominate over those of the dust emissivity (Casey et al. 2014), we – conservatively, as will become
clear in Section 4.3 – fixed the dust emissivity to _𝛽_ IR = 1 _._ 5. A
flat prior within the range 10 [4] M ⊙ _<_ _𝑀_ dust _<_ _𝑀_ ∗ was assumed on
log 10 _𝑀_ dust ; a gamma distribution with shape parameter _𝑎_ = 1 _._ 5
and shifted to start at _𝑇_ CMB ( _𝑧_ ) was used for the dust temperature
(a standard choice for a parameter with a non-negative continuous
domain as it is the conjugate prior to many likelihood distributions;
we note that there is little difference when assuming a flat prior, but
a maximum temperature has to be assumed). The model’s predicted
observed flux density at a given wavelength are compared with the
actual observed flux densities and a likelihood is assigned based on
the squared residuals between model and observations (weighted by
the inverse variance). Following the formalism in Sawicki (2012),
if the model greybody curve exceeds (falls below) the upper limits,
the likelihood is lowered (increased) according to the significance
of the discrepancy (agreement).
The full SEDs of four galaxies considered in this work are
shown in Figure 3. We show one of the two sources for which
only upper limits on the dust continuum are available (COS2987030247), where a range of dust temperatures (30 K ≤ _𝑇_ dust ≤
100 K) and emissivity parameters (1 _._ 5 ≤ _𝛽_ IR ≤ 2) for templates that
fit the constraints are considered instead of a mercurius fit (idem
for UVISTA-Z-007 not shown here). These templates are created
under an entirely optically thin opacity model (i.e. an SED described
by equation (7)), which is a valid assumption since their dust masses
are too small to be confidently detected (as shown in Table 3). As
can be seen from these templates, the constraints cannot be used to
deduce the best-fit parameters, which is why we report (an upper
limit on) the (F)IR luminosity and other parameters with a fiducial
temperature _𝑇_ dust = 50 K and _𝛽_ IR = 1 _._ 5 (Section 3.1). From Figure 3, it can furthermore be seen that the IR luminosity can vary by
more than an order of magnitude between the most extreme choices
of _𝑇_ dust and _𝛽_ IR (see also Hodge & da Cunha 2020). As described
in Section 3.1, we take the systematic uncertainty resulting from
fixing these parameters into account in our estimates of the (F)IR
luminosity and obscured SFR.
For the three sources for which we have at least one 5 _𝜎_ detec
tion (COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019), on
the other hand, the mercurius fitting routine described above is applied, fixing _𝛽_ IR = 1 _._ 5 but considering different assumptions on the
opacity model: either an entirely optically thin SED or the general
opacity model, with _𝜆_ 0 set self-consistently or fixed to an extreme


12 Together with the fact that the intrinsic dust temperature has a large
impact on the derived dust masses at shorter wavelengths, this is why dust
masses should ideally be inferred from the highest FIR wavelengths ( _𝜆_ emit _>_
450 μm), where the SED certainly is optically thin (Casey 2012).


MNRAS **000**, 1–23 (2022)



200 μm. The “best-fit” line shows the SED curve for the maximum
likelihood in the ( _𝑀_ dust _,𝑇_ dust ) plane, shaded regions show the deviation of the 16th and 84th percentiles from the median (i.e. 50th
percentile) at each wavelength of all curves produced according
to the posterior distribution. We note the best-fit model of COS3018555981 and UVISTA-Z-019 is expected not to pass through
the _𝜆_ emit ∼ 160 μm detection, since the upper limit at ∼ 90 μm is
also taken into account. In the next two sections, we will discuss the
inferred dust properties in more detail. [13]


**4.2** **The build-up of dust: masses and yields**


First, we briefly discuss the estimates of the dust mass of our sources,
while stressing these are fairly uncertain, firstly due to the range of
possible _𝜅_ _𝜈_ depending on the dust composition as discussed in Section 4.1. Secondly, our measurements do not probe the RayleighJeans (RJ) tail of the SED, meaning that the dust mass becomes
sensitive on the intrinsic dust temperature: sampling at a rest-frame
wavelength 200 μm introduces a factor ∼ 5 difference in _𝑀_ dust for a
2× difference in _𝑇_ dust, for instance (Cortzen et al. 2020). The latter
effect, however, is reflected in the uncertainty estimates from the
posterior distributions obtained in the mercurius fitting routine,
which probes a range of temperatures. As will be discussed below,
the distributions are based purely on the likelihood of underlying
dust masses and temperatures producing the observed continuum
(non-)detections and in principle could result in unphysical scenarios (save dust masses above the stellar mass and temperatures below
the CMB temperature, whose solutions are discarded; Section 4.1).
For the five sources considered in this work, we find the dust
mass typically range upwards of a few million solar masses. Interestingly, the tentatively low dust temperature of COS-3018555981
(discussed in more detail in Section 4.3) under the fiducial selfconsistent general opacity model (where _𝜆_ 0 ≃ 10 μm) nominally
implies a relatively high dust mass, _𝑀_ dust = 7 [+] − [19] 5 [·][ 10] [7] [ M] [⊙] [. Since]
the self-consistently derived _𝜆_ 0 is well below the lowest sampled
wavelength ( _𝜆_ emit ∼ 90 μm), an optically thin SED appears a rather
good approximation producing a similar dust mass and temperature,
although the estimated uncertainty in the self-consistent model is
larger and thus more conservative (mainly allowing for even higher
dust masses that are compensated for by an increasing _𝜆_ 0 ).
The estimated dust mass translates into a substantial dust-tostellar mass ratio, _𝑀_ dust / _𝑀_ ∗ = 0 _._ 05 [+] − [0] 0 _[.]_ _._ [16] 04 [(Table] [3][).] [Although] [we]
stress the current evidence is limited, the formal likelihood treatment evidently yields rather extreme solutions; might we expect the
true values be more modest from a physical perspective? We consider dust grains comprise of metals mainly produced by short-lived,
massive stars, while most of the stellar mass instead is dominated by
low-mass stars, so that _𝑀_ dust / _𝑀_ ∗ cannot exceed the stellar metallicity yield – the mass-fraction of metals released into the ISM
compared to the total (remaining) stellar mass – typically assumed
to be a few percent (Maiolino & Mannucci 2019). However, higher
stellar yields are certainly plausible for a (more) top-heavy IMF:
for instance, a Kroupa (2001) or Chabrier (2003) IMF already results in stellar metallicity yields that are twice as high than for a
Salpeter (1955) IMF (Vincenzo et al. 2016). Moreover, we note the
stellar mass estimate of _𝑀_ ∗ = 1 _._ 4 − [+][0] 0 _[.]_ _._ [7] 2 [·][ 10] [9] [ M] [⊙] [(taken] [from] [Smit]
et al. 2018) is a conservative one in this context as it is ∼ 0 _._ 5 dex


13 Unless mentioned otherwise, reported quantities are given as the 50th
(i.e. median), 16th, and 84th percentiles (as a ±1 _𝜎_ confidence range) of the
parameter’s marginalised posterior distribution.

10 _J. Witstok et al._


obs [(mm)]
0.4 0.6 1 2



obs [(mm)]
0.4 0.6 1 2





























































**Figure** **3.** Overview of the dust continuum detections and upper limits for four galaxies investigated in this work. Upper limits are drawn at 3 _𝜎_, with a
line beneath indicating a 1 _𝜎_ level. Where only upper limits are available (i.e. for COS-2987030247), we plot a wide variety of greybody dust SEDs, for
30 K ≤ _𝑇_ dust ≤ 100 K and 1 _._ 5 ≤ _𝛽_ IR ≤ 2 (under an entirely optically thin opacity model). The resulting range of IR luminosities is indicated in the bottom
left, showing _𝐿_ IR can vary by more than an order of magnitude between the most extreme choices of _𝑇_ dust and _𝛽_ IR . For COS-3018555981, UVISTA-Z-001,
and UVISTA-Z-019, on the other hand, the mercurius fitting routine described in Section 4.1 is applied, fixing _𝛽_ IR = 1 _._ 5 but considering various assumptions
on the opacity model: either an entirely optically thin SED or the general opacity model given in equation (6) with either a self-consistent or fixed _𝜆_ 0, the
wavelength separating the optically thick and thin regimes. The “best-fit” line shows the SED curve for the maximum likelihood in the ( _𝑀_ dust _, 𝑇_ dust ) plane,
shaded regions show the 16th and 84th percentiles at each wavelength of all curves produced according to the posterior distribution. We note the best-fit model
of COS-3018555981 and UVISTA-Z-019 is expected not to pass through the _𝜆_ emit ∼ 160 μm detection, since the upper limit at ∼ 90 μm is also taken into
account. The resulting dust mass and temperature are indicated for each fit, as is _𝜆_ [AP] 0 [, the value of] _[ 𝜆]_ [0] [that is inferred a posteriori (if applicable). The inferred]
peak temperature (though measured on the CMB-corrected spectrum; Appendix A) for the fiducial self-consistent opacity model is annotated (see also Table 3).



higher than the best fit found by the REBELS collaboration, who
explored several photometric fitting codes (private communication,
REBELS collaboration 2021; see also Bouwens et al. 2022). Upcoming _James Webb Space Telescope_ ( _JWST_ ) observations (GTO:
1217, GO: 1837) will provide a highly accurate stellar mass and
give insight into the star formation history of this source, and hence
also its age.


By assuming a stellar IMF, the dust-to-stellar mass ratio can
be converted into a dust yield, denoted _𝑦_ dust, which represents the
average dust mass formed per dust-producing star. Here, we follow the method of Michałowski (2015), who considered SNe and
asymptotic giant branch (AGB) stars as sources of dust production, assuming their relevant stellar mass ranges are 8-40 M ⊙ and
3-8 M ⊙, respectively. Both yields from SNe and AGB stars for a
Chabrier (2003) IMF are shown in Table 3. Average AGB dust



yields that are obtained under Salpeter and top-heavy IMFs can be
∼ 2× higher, but this only strengthens the interpretation discussed
below. More critically, however, the inferred SN dust yields could
decrease (increase) by a factor of ∼ 1 _._ 5 for a top-heavy (Salpeter)
IMF since these IMFs result in a higher (lower) number of SN
events, thereby lowering (raising) the required average yield per
SN.

The yield that would be required per AGB star, _𝑦_ dust, AGB ∼
1 _._ 5 [+] − [4] 1 _[.]_ _._ [6] 1 [M] [⊙] [for COS-3018555981, far exceeds the theoretically ex-]
pected value, ∼ 0 _._ 02 M ⊙, even more so when the yield is increased
up to 2× under a different IMF (as already shown for other EoR
galaxies in e.g. Michałowski 2015; Leśniewska & Michałowski
2019; Schouws et al. 2022b). This renders AGB stars an unlikely
candidate as the main source of dust formation in this early cosmic epoch (even within the systematic uncertainty of _𝜅_ _𝜈,_ ref ). In

MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 11



stead, when SNe are considered, a nominally gigantic yield of
_𝑦_ dust, SN = 4 _._ 5 [+] − [13] 3 _._ 1 _[.]_ [3] [M] [⊙] [per dust-producing star would be required.]
We note that the uncertainty estimates, apart from incorporating a
systematic 10% flux calibration uncertainty (Section 3.1), are purely
statistical and the SN dust yield could systematically be reduced by
a high _𝜅_ _𝜈,_ ref resulting in a lower dust mass (see Section 4.1). However, as also discussed in Section 4.1, the current assumption of
_𝜅_ _𝜈,_ ref = 8 _._ 94 cm [2] g [−][1] is valid for dust produced by SNe and thus
other choices would be inconsistent for estimating the SN dust yield.
Even the lowest required yield within the estimated 1 _𝜎_ uncertainties, ∼ 1 _._ 4 M ⊙, is already in slight tension with the maximum
theoretical yield per SN, which is 1 to 2 M ⊙ without the subsequent dust destruction by the SN (e.g. Nozawa et al. 2003). The
discrepancy might even be more serious for various reasons: if dust
destruction does play a significant role, this lowers the theoretical
maximum yield, while the required dust yield per SN is increased
under a different IMF. Finally, we find yet a lower dust temperature
and higher mass and yield increase if we instead assume a higher
dust emissivity 1 _._ 8 ≲ _𝛽_ IR ≲ 2, the value typically found at high
redshift for more massive systems (e.g. Jones et al. 2020a; Cortzen
et al. 2020; Faisst et al. 2020; Casey et al. 2021) – this is why
we conservatively opt for a fiducial _𝛽_ IR = 1 _._ 5 here. Hence, there
is tentative evidence that other evolutionary mechanisms, such as
the growth of dust grains in the ISM (Leśniewska & Michałowski
2019), need to be invoked. A final caveat to this result is that the dust
mass decreases if _𝜆_ 0 is fixed to 200 μm (since higher temperatures
are feasible in this scenario; Section 4.3), thereby bringing the dust
yield down to _𝑦_ dust, SN ∼ 3 M ⊙, which however is still inconsistent
with theoretical expectations. Yet this scenario would perhaps be
equally surprising, as will be discussed further in Section 4.3.


**4.3** **Cosmic evolution of dust temperature: evidence for**
**extremely cold or highly clustered dust?**


In the following, we move on to discuss the dust temperature, arguably one of its most important properties as it is essential in
deriving other observable quantities such as the infrared luminosity
and dust mass from a limited number of photometric data points
(Sommovigo et al. 2020, 2022). Unfortunately, establishing the dust
temperature is not trivial. Directly fitting observed SEDs necessarily yields a luminosity-weighted dust temperature, which may be
skewed towards high temperatures by hot dust in star-forming regions (Liang et al. 2019). Hot dust can only be observed directly,
however, if the emission is optically thin (Faisst et al. 2020). When
little information is available, these effects cause the dust temperature, mass, and opacity to become degenerate.
In Figure 4, measurements of the SED peak temperature across
cosmic time are shown. The peak temperature is defined as a purely
observational quantity, defined similarly to Wien’s displacement
law using the SED peak wavelength [14] in the rest frame, _𝜆_ emit, peak :


_𝑏_
_𝑇_ peak = _𝜆_ emit, peak, where _𝑏_ ≃ 2898 K/μm _._ (9)


Details on the motivation for comparing peak temperatures,
rather than _𝑇_ dust, and the precise data from the literature that is
included can be found in Appendix A. We report “intrinsic” peak
temperatures, in the sense that there is no conversion to the current
epoch ( _𝑧_ = 0) to nullify the effect of CMB heating at the relevant


14 The peak of the intrinsic SED, i.e. after it has been corrected for observing
the dust emission against the CMB (Section 4.1).


MNRAS **000**, 1–23 (2022)



epoch, for two reasons. Firstly, peak temperatures are an observational construct (lower than the intrinsic dust temperature), and
secondly, in most cases, the dust has already largely decoupled from
the CMB and heating (described by equation (12) of da Cunha et al.
2013) starts to become relevant only when going back in cosmic
time significantly or for extremely cold dust that has cooled down
nearly to the CMB temperature. This is illustrated by the red shaded
region, which marks an increase of more than 1% in dust temperature between _𝑧_ = 0 and the relevant redshift (under _𝛽_ IR = 1 _._ 5)
and falls below almost all measurements shown here (although neglected in Figure 4, we will apply this correction when relevant in
the following).


Although a consistent picture starts to emerge at _𝑧_ ≲ 4 (e.g.
Schreiber et al. 2018; Drew & Casey 2022), it is unclear whether
this also applies to galaxies in the EoR due to limited observational
data and the highly uncertain relative importance of the possible
mechanisms of dust formation (Mancini et al. 2015). Theoretical
models predict elevated dust temperatures compared to the local
Universe (e.g. Ma et al. 2019; Sommovigo et al. 2020; Vĳayan
et al. 2022), which is indeed confirmed by observations in some
cases (with extreme examples given in Behrens et al. 2018; Bakx
et al. 2020; Viero et al. 2022). However, the peak temperatures for
several objects – most notably _𝑇_ peak ∼ 28 K seen in J0217-0208
(Harikane et al. 2020) – are lower than what may be expected from
an extrapolation of the trend at low redshift (such as the shown fit
by Schreiber et al. 2018; see also Bouwens et al. 2020) and theoretical predictions from cosmological hydrodynamic simulations
(e.g. Liang et al. 2019; Vĳayan et al. 2022). As pointed out by
Sommovigo et al. (2022), a large scatter in dust temperatures may
be expected at early times owing to strongly varying physical conditions in the complex high-redshift ISM. This encourages detailed
follow-up studies of objects with seemingly extreme dust properties
such as COS-3018555981, as we will discuss in the following.


We place a constraint on the peak temperature through the
mercurius fitting procedure for COS-3018555981, UVISTA-Z001, and UVISTA-Z-019, the three sources for which we have at
least one confident detection. However, despite a ∼ 7 _𝜎_ detection at
∼ 160 μm (Figure 1), the upper limit at _𝜆_ emit ∼ 90 μm is not stringent enough to provide precise constraints on the dust temperature
of UVISTA-Z-019. Therefore, we show its median value and 68%
confidence range in Figure 4 for the fiducial opacity model with
self-consistent _𝜆_ 0 (as listed in Table 3). While this result does not
change significantly under a different opacity model, the estimated
uncertainty is so high that within 1 _𝜎_ deviations, it is consistent with
strongly varying scenarios, confirming the temperature is largely
unconstrained. With two detections, we estimate the dust temperature in UVISTA-Z-001 to be _𝑇_ dust = 59 [+] − [41] 20 [K. However, due to the]
matched apertures we have chosen (see Section 3.1), we note this
temperature is representative for the compact component only; the
data at ∼ 160 μm reveals an extended dust-continuum emission that
is not detected at ∼ 90 μm, suggesting a colder dust reservoir exists
on larger scales (see also Akins et al. 2022).


Similarly, the dust-continuum measurements of COS3018555981 – a deep ∼ 90 μm non-detection combined with a significant ∼ 160 μm detection – favour a low dust temperature for this
object. In the fiducial self-consistent opacity model (where we find
_𝜆_ 0 ≃ 10 μm, i.e. effectively almost optically thin), we even find a
nominal intrinsic temperature of _𝑇_ dust = 29 [+] − [9] 5 [K or alternatively, an]
upper limit of _𝑇_ dust _<_ 48 K (95% confidence). The median estimate

12 _J. Witstok et al._



Age (Gyr)



















0

0 2 4 6 8 10

z



**Figure** **4.** Dust peak temperature, _𝑇_ peak, as a function of cosmic time. Several peak temperatures derived from measurements presented in this work under
the self-consistent general opacity model are drawn: for UVISTA-Z-019, we show its median and 68% confidence range (largely invariant under the chosen
opacity model), while for COS-3018555981 an upper limit (95% confidence) is shown in addition. Further, measurements inferred from stacked spectra and
a (partially extrapolated) linear fit by Schreiber et al. (2018) are shown, as is the power-law fit to the peak-temperature evolution of simulated galaxies by
Liang et al. (2019). Details on the literature data points can be found in Appendix A (SMGs are shown as squares, other high-redshift galaxies as circles
with errorbars). Three sources are highlighted with labels, having either a notably low (J0217-0208), high (MACS0416-Y1), or accurately constrained dust
temperature (A1689-zD1). The grey dashed line shows the CMB temperature over cosmic time, the grey area below representing astrophysically unattainable
temperatures – we note, however, that effective peak temperatures of greybody SEDs can in principle fall below this boundary as they are lower than the dust
temperature itself (Section 4.3). The light-red area above indicates the region where CMB heating has a significant (greater than 1%) effect compared to _𝑧_ = 0
(see Section 4.3 for details).



begins to approach ∼ 21 K, the CMB temperature at _𝑧_ ∼ 7. [15] As
noted in Section 4.2, the temperature becomes even lower (likewise,
the dust mass and dust yield increase) if we instead assume a higher
dust emissivity such as _𝛽_ IR = 2, which effectively causes the optical
depth to drop more quickly towards higher wavelengths. The peak
temperature is _𝑇_ peak = 26 [+] − [8] 5 [K, shown in Figure][ 4][ as the blue circle]
along with an upper limit: _𝑇_ peak _<_ 43 K (95% confidence). Such low
temperatures are at odds with _𝑇_ peak measurements of other galaxies
at _𝑧_ ∼ 7 – with the notable exception of J0217-0208 (Harikane
et al. 2020) – as well as with theoretical predictions (e.g. Liang
et al. 2019) and extrapolated observed behaviour at low redshift
(Schreiber et al. 2018) of the peak-temperature evolution.
In the general opacity case, though, the likelihood of higher
peak temperature increases since greybody SED templates can, if
they are sufficiently optically thick, become possible within the
constraints even when their peak wavelength would otherwise fall
below 90 μm (i.e. _𝑇_ peak ≳ 32 K). When _𝜆_ 0 = 200 μm, the upper
limit relaxes slightly to _𝑇_ peak _<_ 53 K (though the median and 1 _𝜎_
confidence ranges are mostly unaffected, as expected when comparing the peak temperature; see Appendix A for details). Moreover,


15 The lower end of the 68% confidence range actually enters the regime
where CMB heating plays a significant role such that _𝑇_ dust _[𝑧]_ [=][0] [=][ 28] − [+][10] 7 [K when]
translated to _𝑧_ = 0.



this optically thick scenario favours a fit with a significantly higher
intrinsic temperature of _𝑇_ dust = 40 [+] − [24] 11 [K, albeit somewhat uncertain]
since a larger range of temperatures is now allowed.
At first glance, an SED that only turns optically thin at ∼ 200 μm
seems to alleviate the tentative tension of an extremely low dust temperature (and high dust mass and yield, cf. Section 4.2). This in itself
is a surprising finding, though, since such a high _𝜆_ 0 is typically seen
in ULIRGs or even HyLIRGs (e.g. Faisst et al. 2020; Cortzen et al.
2020). LIRGs (luminous infrared galaxies) are a class of galaxies
defined by IR luminosity exceeding 10 [11] L ⊙ (and would therefore
include UVISTA-Z-019 and within the uncertainty, possibly even
the other three sources; Table 3). The ultra- and hyper-variants,
ULIRGs and HyLIRGs, exhibit an _𝐿_ IR of more than 10 [12] L ⊙ and
10 [13] L ⊙, respectively (Sanders & Mirabel 1996); such extreme systems commonly have dust reservoirs of 10 [8] M ⊙ or even larger and
contain very compact star-forming regions accompanied by high
surface densities of SFR, gas, and dust (Clements et al. 2010).
Indeed, we find a comparatively low dust surface mass density
of a few M ⊙ pc [−][2] (Table 3). To put this in perspective, this is
two orders of magnitude lower than ∼ 500 M ⊙ pc [−][2] found for a
massive HyLIRG starburst at _𝑧_ ∼ 4 for which _𝜆_ 0 = 170 ± 23 μm
(Cortzen et al. 2020). Hence, the resulting a-posteriori estimates for
_𝜆_ 0 in an opacity model with fixed _𝜆_ 0 = 200 μm are more than an
order of magnitude lower than what is assumed ( _𝜆_ [AP] 0 ∼ 5 μm; see
Figure 3). This discrepancy would point towards the need of a highly


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 13





10 [3]





100


10


1

|z 0 (DGS, GOALS) This work (z 7)<br>3 < Oz < B6 COS-2987030247<br>(Q S /L G/SMG/LAE)<br>PDR/XDR|Col2|Col3|
|---|---|---|
|HII regions|||
|10<br>1011<br>1012<br>10<br>LFIR (L<br>)|10<br>1011<br>1012<br>10<br>LFIR (L<br>)|13|



**Figure 5.** Luminosity ratio of [C ii] 158 μm over [N ii] 205 μm as a function
of the FIR luminosity. Local galaxies shown are from GOALS (Díaz-Santos
et al. 2017) and DGS (Cormier et al. 2015, 2019); constraints on highredshift galaxies (Decarli et al. 2014; Pavesi et al. 2016, 2019) and SMGs
as part of the SPT survey (Cunningham et al. 2020) are included as well
(see Section 5.1 for details). LBGs are indicated with circles, SMGs with
squares, LAEs with upward facing triangles, and the quasar (QSO) as a
diamond. The luminosity ratio expected for [C ii] emission originating in H ii
regions for typical physical conditions (solar metallicity and log 10 _𝑈<_ −3,
_𝑛_ H _<_ 10 [2] cm [−][3] ; see Section 5.1) is shown as the blue shaded area. A dashed
line demarcates _𝐿_ [C ii] / _𝐿_ [N ii] ≃ 6, the minimum value found across a large
range of PDR models (grey shaded area; a similar neutral medium can be
created in the presence of X-ray dominated regions (XDRs) or shocked gas,
see e.g. Decarli et al. 2014). For COS-2987030247, the 3 _𝜎_ upper limit on

[N ii] is fully consistent with [C ii] production in a PDR-like medium.


clustered distribution of dust in order to produce a self-consistent
optical depth: from equations (4) and (8), this would require _𝐶_ ≫ 1
( _𝐶_ ∼ 10 [3] to increase _𝜆_ [AP] 0 by a factor of 100, for _𝛽_ IR = 1 _._ 5).
In conclusion, the results lead to a paradox with a remarkably
low dust temperature in combination with high dust mass and yield
on the one hand (optically thin SED), or the need of a highly clustered dust distribution (optically thick SED) on the other. In either
case, follow-up observations are needed to clarify the tantalising
dust properties of COS-3018555981.


**5** **EMISSION LINE PROPERTIES**


**5.1** **On the origin of [N ii] 205** μm **and [C ii] 158** μm **emission**


The line ratio of [C ii] to [N ii] is a well-known probe of the ionisation state of the ISM (e.g. Nagao et al. 2012). The [N ii] 205 μm
transition namely has a critical density very close to that of [C ii]
158 μm (∼ 50 cm [−][3] in ionised gas; e.g. Carilli & Walter 2013),
while the ionisation potentials of C [+] (24 _._ 4 eV) and N [+] (29 _._ 6 eV) are
also comparable (e.g. Decarli et al. 2014). In addition, the ionisation
potential of neutral carbon (11 _._ 3 eV) and nitrogen (14 _._ 5 eV) are similar, but crucially just below and above that of hydrogen (13 _._ 6 eV).
Therefore, while [N ii] strictly originates in regions where hydrogen
is (largely) ionised, [C ii] emission can arise in both H ii regions and
PDRs. For this reason, the line ratio of [C ii] to [N ii] is a powerful
proxy of the ionisation state of the [C ii]-producing gas, independent
of, for example, the ionisation parameter (e.g. Nagao et al. 2012).


MNRAS **000**, 1–23 (2022)



**Table** **5.** Molecular gas masses, _𝑀_ mol, estimated from the [C ii] 158 μm
luminosity (Table 4) using the conversion given in Zanella et al. (2018).
Also given are _𝑀_ mol / _𝑀_ dust and _𝑀_ mol / _𝑀_ ∗, (lower limits of) the gas-to-dust
and gas-to-stellar mass ratios (see Section 5.1 for details).


Source _𝑀_ mol (10 [9] M ⊙ ) _𝑀_ mol / _𝑀_ dust _𝑀_ mol / _𝑀_ ∗
COS-2987030247 8 _._ 8 ± 4 _._ 8 ≳ 2 _._ 5 · 10 [3] 5 _._ 2 [+] − [2] 3 _[.]_ _._ [9] 1
COS-3018555981 12 _._ 3 ± 2 _._ 2 1 _._ 7 [+] − [3] 1 _[.]_ _._ [7] 3 [·][ 10] [2] 8 _._ 9 [+] − [2] 3 _[.]_ _._ [2] 4
UVISTA-Z-001 20 _._ 9 ± 7 _._ 9 5 _._ 8 [+] − [13] 4 _._ 5 _[.]_ [3] [·][ 10] [3] 5 _._ 5 [+] − [7] 2 _[.]_ _._ [1] 3
UVISTA-Z-007 14 _._ 2 ± 5 _._ 0 ≳ 1 _._ 2 · 10 [3] 3 _._ 8 [+] − [6] 2 _[.]_ _._ [8] 5
UVISTA-Z-019 23 _._ 8 ± 3 _._ 8 1 _._ 2 [+] − [4] 0 _[.]_ _._ [5] 9 [·][ 10] [3] 7 _._ 4 [+] − [4] 2 _[.]_ _._ [0] 9


In Figure 5, we compare the [C ii]/[N ii] ratio of COS-2987030247
(lower limit of _𝐿_ [C ii] / _𝐿_ [N ii] _>_ 4 _._ 8 at 3 _𝜎_, see Section 3.2) against
a number of sources from the literature, as a function of the FIR
luminosity.
In this figure, several local galaxies are shown, all observed by
_Herschel_ /PACS: local (U)LIRGs from the GOALS survey (DíazSantos et al. 2017), as well as one lower limit that is part of the Dwarf
Galaxy Survey (DGS; Cormier et al. 2015, 2019); both surveys will
be discussed in more detail in Section 5.2. Furthermore, a sample
of 3 ≲ _𝑧_ ≲ 6 SMGs observed by the SPT is shown (Cunningham
et al. 2020; FIR luminosities are presented in Reuter et al. 2020).
We also include several individual high-redshift sources: a quasar
(QSO), SMG, and two Lyα emitting galaxies (LAEs) presented in
Decarli et al. (2014), and several LBGs from Pavesi et al. (2016,
2019).
While Decarli et al. (2014) report the typical luminosity ratio expected for [C ii] emission originating in H ii regions to be
_𝐿_ [C ii] / _𝐿_ [N ii] ∼ 2, we indicate here the range of line ratios found
across a large range of photoionisation models, which will be introduced in Section 5.3. We show the luminosity ratio expected for
pure H ii regions with typical gas conditions (solar metallicity and
log 10 _𝑈<_ −3, _𝑛_ H _<_ 10 [2] cm [−][3] ), but we note the ratio can increase
with a lower metallicity, higher ionisation parameter, and/or higher
gas density (in addition to a sub-solar C/N ratio). The line ratios predicted for models incorporating a PDR (see Section 5.3 for details)
can be substantially higher, suggesting the line ratios of the majority
of the observations are consistent with an additional component of

[C ii] being produced in a neutral PDRs environment (or similarly
in X-ray dominated regions (XDRs) or shocked gas; Decarli et al.
2014, and references therein). For COS-2987030247, the 3 _𝜎_ upper
limit on [N ii] is fully consistent with [C ii] production in a PDR-like
medium. While it does simultaneously allow for H ii regions as the
primary origin of the [C ii] emission, the upper limit suggests this
scenario is unlikely (for reasonable physical conditions) at a ∼ 2 _𝜎_
level.

Having established that a contribution to the [C ii] 158 μm
emission of COS-2987030247 is likely traced to a neutral, PDRlike medium, we expect the same to be true for the other three _𝑧_ ∼ 7
star-forming galaxies with similar physical properties. Indeed, this
is in line with recent findings of high H i gas mass fractions at early
times (Heintz et al. 2021, 2022). Moreover, Zanella et al. (2018)
have showed there exists a linear relation between the [C ii] luminosity and the molecular gas mass of a galaxy, regardless of its gas
depletion time (i.e. starburst or main-sequence phase), redshift, and
metallicity. Since all galaxies have confident [C ii] detections, we
can easily convert _𝐿_ [C ii] into an estimate of _𝑀_ mol, the molecular
gas mass, though we caution our sources are beyond the redshift
(and possibly metallicity) regime at which Zanella et al. established the calibration. We adopted their median conversion factor

14 _J. Witstok et al._


of _𝛼_ [C ii] = 31 M ⊙ L [−] ⊙ [1] [and a systematic 0] _[.]_ [3 dex spread. The results]
are shown in Table 5. We also provide estimates on the gas-to-dust
and gas-to-stellar mass ratios, which, in the form of _𝑀_ mol / _𝑀_ dust
and _𝑀_ mol / _𝑀_ ∗ respectively, are strictly lower limits since we do not
take into account the H i gas mass. Interestingly, we find a modest
gas-to-dust ratio for COS-3018555981 (albeit a lower limit), which
implies a high metallicity (Rémy-Ruyer et al. 2014). We note this
would be consistent with the findings in Section 4.2 requiring a high
metal yield.
We now turn to a discussion focused on the [O iii] 88 μm line
in comparison to [C ii] 158 μm and in the context of the optical

[O iii] lines (inferred from _Spitzer_ broadband photometry so that
these include [O iii] _𝜆𝜆_ 4960 _,_ 5008 Å and Hβ; see Section 2.1).


**5.2** **[O iii] 88** μm **and [C ii] 158** μm **in the local and**
**high-redshift Universe**


In the local Universe, two main samples of galaxies with measurements of several FIR lines (including [O iii] and [C ii]) exist,
as mentioned in Section 5.1: firstly, GOALS has observed over
200 (U)LIRGs at _𝑧_ ∼ 0 with _Herschel_ /PACS and _Herschel_ /SPIRE
(Díaz-Santos et al. 2017); secondly, the DGS uses _Herschel_ /PACS
to investigate just under 50 metal-poor dwarf galaxies (Madden
et al. 2013, 2014; De Looze et al. 2014; Cormier et al. 2015, 2019).
Among the dwarf galaxies of the DGS, the luminosity ratio of [O iii]
88 μm to [C ii] 158 μm varies between 0 _._ 5 and 13 with a median
of 2, whereas the median ratio for 159 of the (U)LIRGs where both
lines are detected is an order of magnitude smaller (namely ∼ 0 _._ 2,
varying between 0 _._ 04 and 3). Cormier et al. (2015) argue that a large
filling factor of diffuse, ionised gas emitting [O iii] 88 μm is needed
to explain the observed ratios in dwarf galaxies. Crucially, metalpoor systems may therefore have a more porous ISM through which
ionising radiation could escape, which implies that the [O iii]/[C ii]
ratio can indicate leakage of Lyman-continuum (LyC) radiation (see
also Inoue et al. 2016; Katz et al. 2020).
Similar to the metal-poor dwarf galaxies, star-forming galaxies in the EoR have been shown to exhibit systematically high

[O iii]/[C ii] ratios between 1 and 10 (Harikane et al. 2020), which is
confirmed by our findings of (integrated) line ratios between around
2 and 8 (Table 4). Given the limited amount of significant detections and ancillary observations, however, it is not straightforward
to disentangle the contributions of various physical properties that
influence the observed ratios of galaxies in the early Universe. First
of all, there may be certain observational systematics or selection
biases. For instance, flux measurements in interferometric data sets
have to be treated carefully, since the spatial extent of the [C ii] emission has been shown to be significantly larger than that of [O iii]
(Carniani et al. 2018a, 2020; see also Section 2.2.2). Even when
accounting for the extended [C ii] emission, various studies have
suggested that the typical EoR galaxy has even higher [O iii]/[C ii]
ratios than found even in local metal-poor dwarf galaxies (Carniani et al. 2020; Harikane et al. 2020). High [O iii]/[C ii] ratios are
generally indicative of strong bursts of star formation with short gas
depletion times ( _𝑡_ dep ≲ 50 Myr; Vallini et al. 2021), which may be
common among the UV-bright galaxies at high redshift that have
typically been selected for follow-up spectroscopy with ALMA.
The specific star formation rate (sSFR) is expected to scale
inversely with the age of the stellar population in a galaxy, implying
that such strong, recent bursts of star formation should be indicated
by a high sSFR (Vallini et al. 2021). Indeed, galaxies at high redshift ( _𝑧_ ≳ 6) that have been observed in both [O iii] 88 μm and [C ii]
158 μm (see e.g. Carniani et al. 2020) are characterised by higher


|z 0(DGS):<br>p = 3 .2 10 7<br>S = 0 .83|Col2|
|---|---|
|||



|Thiswork(z 7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>z 0(DGS):<br>p = 3 .2 10 7<br>S = 0 .83|Col2|Col3|
|---|---|---|
|z<br>0 (DGS):<br>p = 0.97<br>S =<br>0.007|z<br>0 (DGS):<br>p = 0.97<br>S =<br>0.007|z<br>0 (DGS):<br>p = 0.97<br>S =<br>0.007|
|z<br>0 (DGS):<br>p = 0.97<br>S =<br>0.007|||
|z<br>0 (DGS):<br>p = 0.97<br>S =<br>0.007|||
|z<br>0 (DGS)<br>p = 3.2 10<br>4<br>S =<br>0.65|||
|z<br>0 (DGS)<br>p = 3.2 10<br>4<br>S =<br>0.65|||
|z<br>0 (DGS)<br>p = 3.2 10<br>4<br>S =<br>0.65|||
|100<br>EW([O III] +|H|103<br> ) (Å)|


**Figure** **6.** Ratios of the [O iii] 88 μm and [C ii] 158 μm luminosities with
respect to each other (top panel) and with respect to the SFR (middle panel
for [O iii], bottom panel for [C ii]) as a function of the EW of the optical [O iii]
and Hβ lines. If the measured SFR is an upper limit (due to a non-detection
of the dust continuum), unobscured SFR measurements are shown with an
open circle. Small grey circles are galaxies from DGS (see Section 5.2). The
_𝑝_ -value, for a null hypothesis that the data are uncorrelated, and Spearman’s
rank correlation coefficient ( _𝜌_ S ) of these points measured in logarithmic
space are indicated in each panel. Coloured circles show the five _𝑧_ ∼ 7
galaxies considered in this work. There is a significant positive correlation
between the [O iii]/[C ii] ratio and their optical EW among the DGS galaxies,
which seems to derive mostly from a negative correlation between [C ii]/SFR
and the EW; however, the correlation of the [O iii]/[C ii] luminosity ratio is
stronger than that of the (relative) [C ii] luminosity on its own. Furthermore,
it is unclear whether the same is true for the small sample of high-redshift
galaxies.


sSFRs (roughly 1 to 2 dex) than galaxies from the local DGS and
GOALS samples. However, the DGS and GOALS samples share
a similar median sSFR of 0 _._ 31 Gyr [−][1] and 0 _._ 36 Gyr [−][1] respectively,
despite having a factor of ∼ 10 difference in their [O iii]/[C ii] ratios, making the global sSFR of galaxies a poor indicator of high

[O iii]/[C ii] emission. Potentially, the local dwarf galaxies have a
(much) older stellar component (e.g. Mateo 1998), which lowers
their global stellar mass and overall sSFR, while merely their young
star-forming regions – possibly fuelled by recent inflows of gas –


MNRAS **000**, 1–23 (2022)



10


1


10 [8]


10 [7]


10 [7]


10 [6]

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 15



are thought to have the most similar ISM conditions to high-redshift
galaxies. Alternatively, the time scales on which SFRs are measured
may be too long to give an accurate indication of their [O iii]/[C ii]
ratio, since most galaxies in DGS and GOALS have SFRs measured
through their (UV and) IR luminosity (probing time scales on the
order of 100 Myr; e.g. Kennicutt & Evans 2012).
We therefore consider an alternative (inverse) tracer of starburst
age, the EW of the optical [O iii] and Hβ lines, which makes a
fairer comparison between local and distant galaxies specifically
when the EW is measured across the young star-forming regions
of local dwarf galaxies. [16] In the top panel of Figure 6, we show
the [O iii]/[C ii] luminosity ratio as a function of the EW of the
optical [O iii] and Hβ lines both for the DGS and _𝑧_ ∼ 7 galaxies
considered in this work. [17] Among the metal-poor dwarf galaxies,
there is a clear positive correlation: the Spearman’s rank correlation
coefficient measured in logarithmic space is _𝜌_ S ≃ 0 _._ 83 (with a
_𝑝_ -value of 3 _._ 2 · 10 [−][7] ); this is noticeably higher than when EW is
swapped for sSFR, where _𝜌_ S ≃ 0 _._ 35 ( _𝑝_ ≃ 0 _._ 056). In the bottom two
panels of Figure 6, we investigate whether this effect is mostly due to
brighter [O iii] 88 μm line or a [C ii] 158 μm deficit towards higher
EWs (and hence younger ages). The correlation coefficients suggest
it derives mostly from a negative correlation between [C ii]/SFR
and the EW ( _𝜌_ S ≃−0 _._ 65 with _𝑝_ ≃ 3 _._ 2 · 10 [−][4] ) rather than between

[O iii]/SFR and EW ( _𝜌_ S ≃−0 _._ 007 with _𝑝_ ≃ 0 _._ 97); however, the
correlation of the [O iii]/[C ii] luminosity ratio is stronger than that
of the (relative) [C ii] luminosity on its own. Furthermore, it is
unclear whether the same is true for the small sample of highredshift galaxies (where indeed the opposite seems true).
To investigate whether the observed line intensities line up with
theoretical expectations, we will introduce a set of photoionisation
models aimed to mimic the expected physical condition of the ISM
in the following.


**5.3** **Comparing observed emission line strengths to the**
**predictions of photoionisation models**


To gain further insight into the physical conditions of the ISM, we
employed one-dimensional, radiative-transfer models of a planeparallel nebula in Cloudy (v17.02; Ferland et al. 2017) to simulate
an H ii region that smoothly transitions into a PDR. As the incident
radiation field, we used a single burst of star formation with varying
ages generated by bpass v2.1 (Eldridge et al. 2017) under a Salpeter
IMF, ranging in stellar mass from 1 to 100 M ⊙ . Motivated by for example the observed extreme optical EWs, we choose the set of bpass
models where interacting binary stars are included (significantly
boosting the ionising flux; see e.g. Stanway et al. 2016). In addition,
the CMB at _𝑧_ = 7 and a cosmic ray background (crucial to the PDR
physics; see Abel et al. 2005) are included in all models. Following
Cormier et al. (2019), we chose a density law that increases linearly
with column density, resulting in an exponential density profile that
is nearly constant in the H ii region. [18] As in Harikane et al. (2020),
we explored stellar metallicities of _𝑍_ ∗ /Z ⊙ ∈{0 _._ 05 _,_ 0 _._ 2 _,_ 1} where,
as a baseline model, we set the gas metallicity _𝑍_ neb equal to that of


16 The EW measurements of DGS sample will be presented in Kumari et
al. (in prep.).
17 We disregard the GOALS sample here, since their [O iii] and Hβ EWs

are not available.
18 This circumvents the more extreme assumptions of a constant density
throughout the H ii region and PDR or constant pressure, which gives rise
to a density discontinuity at the boundary layer between them.


MNRAS **000**, 1–23 (2022)



the stars under the default abundance pattern in Cloudy (which has
12 + log (O/H) ⊙ = 8 _._ 69; Asplund et al. 2009), except for helium
which we set according to equation (1) in Groves et al. (2004).
We varied the ionisation parameter between log 10 _𝑈_ = −4
and −0 _._ 5, in steps of 0 _._ 5, while fixing the hydrogen density to _𝑛_ H ∼
10 [2] cm [−][3] (both defined at the illuminated face of the cloud). Though
we do explore different gas densities (as discussed below), the choice
for this particular value was motivated both by observations at high
redshift (e.g. Sanders et al. 2016) and typical densities found in local
dwarf galaxies that show similarly strong [O iii] 88 μm emission
relative to their SFR, such as Mrk 209 (Izotov et al. 1997) and ii Zw
40 (Guseva et al. 2000). Graphite and silicate dust grains with Orionlike size distribution and abundance were included, along with a
self-consistent abundance correction to account for the depletion
of metals onto grains. Finally, we set the turbulent velocity of the
gas to 1 _._ 5 km/s (Cormier et al. 2019). The calculation is run until
a visual extinction _𝐴_ _𝑉_ = 10 mag is reached to ensure the full [C ii]
158 μm luminosity is captured, since [C ii] predominantly arises in
PDRs (e.g. Abel et al. 2005). The SFR is measured – as a surface
density Σ SFR in M ⊙ yr [−][1] kpc [−][2], since the geometry is plane parallel
– through the incident UV continuum (i.e. the stellar radiation field
at the illuminated face of the cloud, which is not attenuated by dust)
at 1550 Å via the conversion given by Kennicutt & Evans (2012). [19]

In addition to these “vanilla” simulations of a H ii region
combined with a PDR, we also consider various deviations from
the default scenario, whose impact will be discussed further in
the next sections. Firstly, we varied the hydrogen density between
log 10 ( _𝑛_ H [cm [−][3] ]) = 0 _._ 5 and 3, in steps of 0 _._ 5. Secondly, we ran
simulations that stop when molecules first start to form, changing
the stopping criterion in Cloudy to reaching a molecular hydrogen fraction of 10 [−][6] instead of reaching a certain visual extinction,
thereby effectively stripping away the PDR and leaving only the
bare H ii region. Thirdly, motivated by the observed α/Fe ratio at
high redshift (e.g. Steidel et al. 2016), we considered models with
an enhanced nebular α/Fe ratio, accomplished by scaling up the
individual abundances of α elements (C, O, Ne, Mg, Si, and S) in
the gas by a given factor _𝑋_ α/Fe _,_ neb . This results in an enhancement
by the same factor of the α/Fe ratio relative to the default solar
abundances:



_𝑋_ α/Fe _,_ neb =



�α/Fe� neb = 10 [[] [α][/][Fe] []] [neb] _,_
�α/Fe� ⊙



such that _𝑋_ is simply the linear version of the logarithmic relative number density (bracket notation; Maiolino & Mannucci
2019). In this case, we additionally swap the solar metallicity
case for _𝑍_ ∗ = 0 _._ 005 Z ⊙ . For our default α-enhancement of choice,
_𝑋_ α/Fe _,_ neb = 4 (as seems appropriate from the findings discussed
in the following Section 5.5), the effective nebular metallicities
for α elements correspond to _𝑍_ neb /Z ⊙ = 0 _._ 02, 0 _._ 2, and 0 _._ 8 (for
_𝑍_ ∗ /Z ⊙ = 0 _._ 005, 0 _._ 05, and 0 _._ 2, respectively). Fourthly, we similarly
scaled down the carbon abundances by a certain factor, reflecting a
sub-solar C/O ratio that may be appropriate in the early Universe,
as will be discussed in Section 5.4. Finally, we increased the rate of
cosmic rays (to 10× the Cloudy default) that stimulates PDR heating and line intensities (notably that of [C ii] 158 μm; e.g. Cormier


19 We note that the conversion of Kennicutt & Evans (2012) assumes a
Kroupa & Weidner (2003) IMF, differing from bpass that generates the
incident radiation field with a Salpeter IMF. However, this is consistent with
the conversion used for the observed SFRs (see Section 4); an additional

translation between IMFs would therefore shift both models and observa
tions by an equal amount.

16 _J. Witstok et al._



10 [8]









10 [7]

|30 25 20 15 1<br>. . . .<br>log10U<br>Thiswork(z 7)<br>0<br>COS-2987030247<br>COS-3018555981 5Myr 1Myr<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>1<br>Models with nH = 102 cm 3<br>08 Z * = 0 .005 Z, X /Fe, neb = 4<br>Z * = 0 .05 Z, X /Fe, neb = 4<br>Z * = 0 .2 Z, X /Fe, neb = 4<br>1Myr<br>5Myr<br>07<br>X /Fe, neb = 1<br>100 103<br>EW([OIII]+H )(Å)|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U||||||
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|||||1|
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019|1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019|1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019|1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019|1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019|
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|||||
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|~~r~~|~~r~~|~~r~~|~~r~~|
|1<br>0<br>1 Myr<br>5 M~~y~~r<br>This work (z<br>7)<br>COS-2987030247<br>COS-3018555981<br>UVISTA-Z-001<br>UVISTA-Z-007<br>UVISTA-Z-019<br>100<br>103<br>EW([O III] + H ) (Å)<br>07<br>08<br>1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4<br>3.0<br>2.5<br>2.0<br>1.5<br>1<br>log10U|1 Myr<br>5 M~~yr~~<br>X /Fe, neb = 1<br>Models withnH = 102 cm<br>3<br>Z * = 0.005 Z<br>, X /Fe, neb = 4<br>Z * = 0.05 Z<br>, X /Fe, neb = 4<br>Z * = 0.2 Z<br>, X /Fe, neb = 4|1<br>  H|1<br>  H|03<br> ) (Å)|03<br> ) (Å)|



**Figure 7.** Relative strength of [O iii] 88 μm with respect to [C ii] 158 μm and
SFR as a function of the EW of the optical [O iii] and Hβ lines. Small grey
circles are dwarf galaxies from the DGS (see Section 5.2), coloured circles
are the five _𝑧_ ∼ 7 galaxies considered in this work. Top panel: luminosity
ratio of [O iii] over [C ii]. Grids of Cloudy models discussed in Section 5.3
with _𝑛_ H = 10 [2] cm [−][3] and stellar ages of 1 (right) and 5 Myr (left) are shown
as grids, where the coloured dashed lines indicate a constant metallicity
relative to Solar (see legend in the bottom panel). The gas in the main grids
shown here has an α/Fe ratio enhanced by a factor 4 (see Section 5.3 for
details). Solid lines of fixed ionisation parameter are coloured according
to the colourbar on the top. Bottom panel: ratio of [O iii] luminosity over

SFR. The same Cloudy models as described above are overlaid. An arrow

indicates the average shift of the models (∼ 0 _._ 5 dex) if a solar α/Fe ratio is
considered (i.e. _𝑋_ α/Fe _,_ neb = 1). The observations of [O iii]/SFR at _𝑧_ ∼ 7
(which, if they are limits, show unobscured SFR measurements with open
circles) are mostly reproduced by Cloudy models, provided the metallicity
is nearly at a solar level (Section 5.5).


et al. 2019). In the following, we discuss the theoretical interpretations that can be applied to observed [O iii] 88 μm and [C ii] 158
μm luminosities.


**5.4** **Insights on [O iii] 88** μm **and [C ii] 158** μm


As discussed in Section 5.2, ALMA observations of the [O iii] 88
μm and [C ii] 158 μm lines in several EoR galaxies have hinted at
high [O iii]/[C ii] ratios compared to local (U)LIRGs observed in
GOALS and similar to local metal-poor dwarf galaxies from DGS



with the highest EW([O iii] + Hβ). From a theoretical perspective,
there are many factors that could explain these high line ratios, if
they are not purely caused by observational effects (as discussed in
Section 5.2). Harikane et al. (2020) used Cloudy photoionisation
models to show that the [O iii]/[C ii] luminosity ratio is expected
to increase when increasing the ionisation parameter _𝑈_, mostly
through a decline of the [C ii]/SFR ratio while [O iii]/SFR remains
fairly unchanged, consistent with the observational trends found for
DGS galaxies in Section 5.2. In addition, the hydrogen density _𝑛_ H is
expected to play a role as the density approaches the critical density
of [O iii] (510 cm [−][3] ), which is lower than that of [C ii] produced in
neutral gas (∼ 2 _._ 8 - 10 [3] cm [−][3] when collision partners are atomic and
molecular hydrogen; cf. Carilli & Walter 2013). However, in reality,
the ISM is a complex, multi-phase environment; hence, [C ii] and

[O iii] are typically expected to emerge largely from distinct gas
reservoirs characterised by different densities (e.g. Katz et al. 2022;
Pallottini et al. 2022).
The effect of varying carbon and oxygen abundances are also
difficult to isolate. On its own, altering both abundances equally
would affect the individual line strengths, but to first order leave
their ratio unchanged. A secondary effect, however, is that a lower
metallicity also decreases the dust-to-gas ratio (Galliano et al. 2018).
Less dust allows UV photons to penetrate deeper into neutral gas,
implying larger PDRs can form. Hence, with a lower metallicity,

[C ii] can become more luminous, which would lead to a suppressed

[O iii]/[C ii] ratio. On the other hand, the global metallicity is also
linked to the hardness of the stellar radiation field and the ionisation

parameter, such that a low metallicity would be expected to lead to
more highly ionised gas and thus a higher [O iii]/[C ii] ratio.
A recent study on a large number of simulated galaxies by Katz
et al. (2022) instead argues for the need of a C/O abundance around
8× lower than solar in metal-poor systems, which would provide
a direct explanation for the high [O iii]/[C ii] ratios. This can be
interpreted as a result of rapid metal enrichment by low-metallicity
core-collapse SNe responsible for producing the majority of oxygen,
while type-Ia SNe and AGB stars, an important source of carbon
enrichment, act on longer timescales (Arata et al. 2020; see also
Maiolino & Mannucci 2019). A caveat of these results is that dust is
neglected; still, Arata et al. (2020) report a similar anti-correlation
between metallicity and [O iii]/[C ii] for simulated galaxies where
dust is included, albeit in a smaller sample.
As discussed above, one-dimensional photoionisation codes
are unlikely to capture the complexity of the ISM in its entirety,
particularly in the early Universe. However, they are still useful as
a first-order approximation of the strengths of emission lines given
varying physical conditions. Indeed, any discrepancies between the
predictions of such simulations and observed quantities can point
towards their shortcomings. Therefore, as a reference, Cloudy models described in Section 5.3 are shown in the background of Figure 7. The models span the range of observed [O iii]/[C ii] ratios,
albeit for high values of the ionisation parameter (log 10 _𝑈>_ −1 _._ 5).
However, we note that if the simulated [O iii] luminosity is indeed
underestimated as suggested by the findings in Section 5.5, the
same [O iii]/[C ii] ratio could be accomplished with a lower, more
moderate ionisation parameter. In the case of the [O iii]/[C ii] ratio, varying the gas density does not produce significantly different
results; as expected, stripping the PDR from the H ii region, increasing the α enhancement, and lowering the C/O ratio all boost
the [O iii]/[C ii] ratio, whereas enhancing cosmic ray background
lowers [O iii]/[C ii].
The high luminosity ratios seen at high redshift, and in a subset
of metal-poor dwarf galaxies, can be explained as coming from an


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 17



elevated [O iii] 88 μm luminosity, a [C ii] 158 μm deficit, or a combination of both. Carniani et al. (2020) argued there is no significant

[C ii] deficit, as long as interferometric observations are properly set
up to capture its full spatial extent. In line with these findings, we
will show in the next section that photoionisation models appear to
struggle to reproduce the (relative) strength of the observed [O iii]
88 μm line, pointing towards an [O iii] enhancement causing the elevated [O iii]/[C ii] ratios (even though [C ii] seems to be responsible
for the correlation with EW of the optical lines more than [O iii], as
discussed in Section 5.2).


**5.5** **Optical and FIR lines of [O iii]**


In the bottom panel of Figure 7, results from the Cloudy models discussed above (Section 5.3) are shown in the plane of
relative strengths of key [O iii] emission lines, [O iii] 88 μm
and the [O iii] _𝜆𝜆_ 4960 _,_ 5008 Å lines. Because we infer the restframe optical [O iii] strength from the _Spitzer_ /IRAC [3 _._ 6] −[4 _._ 5]
colour, we estimate the line strength as the combined EW of

[O iii] _𝜆𝜆_ 4960 _,_ 5008 Å and Hβ lines, denoted as EW([O iii] + Hβ)
here, while we estimate the FIR [O iii] 88 μm line strength as
_𝐿_ [O iii] 88 μm /SFR. Using these relative luminosities allows us to
compare local and high-redshift galaxies on a more equal footing.
Additionally, we note dust attenuation (and hence our choice of a
_𝐴_ _𝑉_ = 10 mag stopping criterion) is not of major importance here,
since the [O iii] _𝜆_ 5008 Å line and stellar continuum flux are, to first
order, expected to be affected equally, which cancels out in the EW,
while the [O iii] 88 μm line is optically thin.
Observations of all metal-poor dwarf galaxies from the DGS
are included in addition to the five _𝑧_ ∼ 7 star-forming galaxies
considered in this work, for which we set lower limits using the
unobscured SFR only if no dust continuum was detected. All measurements shown in the bottom panel of Figure 7, except for a few
dwarf galaxies with low EWs, favour models with a young stellar population for the relative strengths of both [O iii] lines to be
successfully reproduced. Observations of the _𝑧_ ∼ 7 galaxies in particular appear to require a young stellar population of between 1 and
5 Myr. Lower gas densities (e.g. _𝑛_ H ∼ 10 [0] _[.]_ [5] cm [−][3] ) slightly increase
the relative [O iii] luminosity and the EW of the optical lines (both
by around 0 _._ 2 dex), though the models with _𝑛_ H ∼ 10 [2] cm [−][3] shown
here coincide better with the data locus of the DGS and high-redshift
galaxies combined. Higher gas densities (e.g. _𝑛_ H ∼ 10 [2] _[.]_ [5] cm [−][3] ),
as sometimes observed in local high-redshift analogues (e.g. Berg
et al. 2016) decrease the relative [O iii] luminosity by ∼ 0 _._ 3 dex. The
presence of PDRs and cosmic rays have a largely negligible impact.
Perhaps most remarkable is the fact that – even with lower
gas densities – the observations seem to require a relatively high
metallicity (in line with the findings of Harikane et al. 2020). We
note that simulations with a very young stellar population of 1 Myr
and fully solar metallicity (i.e. _𝑍_ ∗ = _𝑍_ neb = Z ⊙ ; not shown here)
are just able to recover the relative [O iii] 88 μm luminosity for very
high ionisation parameters but fail to simultaneously replicate the
EWs of the optical lines for the two COSMOS sources in particular.
Out of a large range of models, we find the most consistent are those
where specifically α elements have near-solar nebular abundances,
i.e. [α/H] neb ∼ 0, as illustrated in the bottom panel of Figure 7 by
the arrow, indicating the ∼ 0 _._ 5 dex downwards shift of the grid when
_𝑋_ α/Fe _,_ neb = 1 as opposed to _𝑋_ α/Fe _,_ neb = 4 as shown. This scenario
may be expected from a rapid metal enrichment of the ISM that
causes the stellar metallicity to lag behind the nebular metallicity.
We note such high metal abundances corroborate the finding of a


MNRAS **000**, 1–23 (2022)



seemingly high dust-to-stellar mass ratio discussed in Section 4.2
and modest gas-to-dust mass ratio discussed in Section 5.1.
Interestingly, a metallicity calibration employing the [O iii]
88 μm line suggested by Jones et al. (2020b) indeed predicts relatively high metallicities given the [O iii] 88 μm luminosities of
the _𝑧_ ∼ 7 galaxies; remarkably, this yields a super-solar value of
12+log (O/H) ≃ 8 _._ 72 for COS-3018555981 (solar abundance being
12 + log (O/H) ⊙ = 8 _._ 69; Asplund et al. 2009), as has been reported
(albeit for higher-mass systems) in a number of recent works (Litke
et al. 2022, and references therein). Yet such (α-element) abundances are exceptionally high compared to what may be expected
for young star-forming galaxies less than a billion years after the
Big Bang. Even when assuming there is no evolution in the massmetallicity relation (MZR) beyond a redshift of _𝑧_ ∼ 3 (while evidence of an underlying evolution up to _𝑧_ ∼ 5 is already emerging;
Witstok et al. 2021), a solar metallicity poses a significant offset
(around 0 _._ 5 dex or a factor of ∼ 3) from the predicted metallicity of
a galaxy with _𝑀_ ∗ ∼ 10 [9] M ⊙ (Sanders et al. 2021).
Relatively high [O iii] 88 μm luminosities have previously been
observed in local metal-poor galaxies, as noted by for example
Lebouteiller et al. (2012) in the case of the Large Magellanic Cloud
(LMC) and Cormier et al. (2015, 2019) for the DGS galaxies. The
models of Lebouteiller et al. (2012) point towards the need of a
relatively cool ( _𝑇<_ 10 000 K) ionised gas, consistent with our
metal-rich models that have more efficient cooling: for solar metallicity, for instance, _𝑇_ ∼ 8000 K in the H ii region, as opposed to
_𝑇_ ≳ 10 000 K for _𝑍<_ _𝑍_ ⊙ . On the contrary, the metal-poor dwarf
galaxies from the DGS have directly observed nebular metallicities
of _𝑍_ neb ≲ 0 _._ 3 Z ⊙, which are instead coupled with high temperatures, 15 000 K ≲ _𝑇_ ≲ 20 000 K (e.g. Izotov et al. 1990, 1997;
Izotov & Thuan 1998; Guseva et al. 2000), as would be expected
given the principal role of heavy elements as a cooling agent. This
indicates that photoionisation models seem to be missing a key
ingredient to replicate the strength of the [O iii] 88 μm line.
One of the main assumptions of our simple, one-dimensional
photoionisation model is to consider an ionisation-bounded nebula
(with a smooth density profile and constant metallicity), while – as
noted in Section 5.4 – this is likely not entirely correct, given for
instance the role star-forming galaxies are thought to play in reionising the neutral IGM (Robertson 2021). Indeed, Cormier et al. (2015,
2019) argue for the presence of escape channels which allow ionising radiation to escape H ii regions, leading to a large volume filling
factor of diffuse (i.e. with density comparable to or lower than the
critical density of [O iii] 88 μm, 510 cm [−][3] ) ionised gas. Another
possibility for the discrepancy would be that, in estimating the relative [O iii] luminosity, the observed SFR is underestimated, for
example by considering dust temperatures lower than what they are
in reality (in particular COS-3018555981; cf. Section 4.3); however,
this seems unlikely in the case of COS-2987030247 and UVISTAZ-007 for which we do not detect dust continuum emission (and
thus have an upper limit on the obscured SFR).


**5.6** **Spatially resolved emission line analysis**


In the previous sections, we have discussed the interpretation of line
strengths and their ratios globally (i.e. integrated across the galaxy).
However, the ISM is known to be complex and inhomogeneous,
especially at high redshift (Vallini et al. 2021; Pallottini et al. 2022).
Here, we will instead briefly discuss detections of the [C ii] 158 μm
and [O iii] 88 μm lines on a spatially resolved scale.
Previous works have already demonstrated significant offsets
(as well as different sizes) between the rest-frame UV and [C ii] 158

18 _J. Witstok et al._





1 0 1













1


0





















1


1





1


0

































overlaid by contours of the [O iii] 88 μm line (achieving a ∼ 0 _._ 4 [′′] resolution with natural weighting; see Table 2) of UVISTA-Z-001 (top panel),
UVISTA-Z-007 (middle panel) and UVISTA-Z-019 (bottom panel). Red

[O iii] contours are drawn from 3 _𝜎_ and going up in steps of 1 _𝜎_ . The top
left indicates a physical scale of 2 kpc. Beam sizes for [O iii] are indicated

in the bottom left.



COS-3018555981 (top panel) and UVISTA-Z-019 (bottom panel), where
imaging parameters have been chosen to match beam sizes (see Table 2).
Light grey contours are drawn for the dust continuum (at ∼ 160 μm, with
natural weighting scheme; Section 5.6 for details), starting from 3 _𝜎_ and
going up in steps of 2 _𝜎_ . Purple contours are drawn for the _HST_ imaging
(Section 2.3) of the rest-frame UV (convolved to match the dust continuum
PSF), starting from 5 _𝜎_ and going up in steps of 5 _𝜎_ . Beam sizes are indicated
in the bottom left (partially hiding a foreground source in the _HST_ imaging
of COS-3018555981); the top left indicates a physical scale of 2 kpc. There
is tentative evidence for spatial variation in the [O iii]/[C ii] ratio, including
a gradient with the lowest [O iii]/[C ii] values seeming to align with the
location of the dust emission in COS-3018555981.


μm emission (e.g. Maiolino et al. 2015; Carniani et al. 2018a,b).
Here, we show a detailed comparison between the UV and [O iii]
88 μm emission in Figure 8 for all three UVISTA sources, where
ALMA achieves a moderately high spatial resolution (with a beam
size of ∼ 0 _._ 4 [′′] ). Despite good agreement between the compact morphology of both the rest-frame UV and the [O iii] contours, there
are signs of minor misalignment: most notably, the observed [O iii]
signal is clearly centred on the western component of UVISTA-Z007, whereas the eastern component distinctly lacks [O iii] emission
of comparable strength. We quantified this by fitting separate twodimensional Gaussian components to the _HST_ images, resulting
in two components with very similar integrated UV luminosities


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 19



10


1





0.1


1 100 10 [4]


L IR /L UV


**Figure 10.** Sequence of the [O iii] 88 μm to [C ii] 158 μm ratio as a function
of _𝐿_ IR / _𝐿_ UV . Global measurements of the DGS and GOALS samples are
shown, as are the five _𝑧_ ∼ 7 star-forming galaxies discussed in this work. Furthermore, spatially resolved ratios extracted from individual regions across
all five sources (see Appendix B for details) are shown as squares (smaller
squares if we can only set 2 _𝜎_ limits on both ratios). For clarity, error bars
of the spatially resolved measurements are not shown; the median error of
these points is indicated by the black square in the top left.


of around 7 · 10 [10] L ⊙ (their ratio being ∼ 1 _._ 1) at a separation of
∼ 0 _._ 71 [′′] or 3 _._ 8 kpc, whereas the luminosity ratio of the [O iii] 88
μm line compared to the UV, _𝐿_ [O iii] / _𝐿_ UV, differs by almost a factor two (measured as (1 _._ 2 ± 0 _._ 6) · 10 [−][3] and (2 _._ 2 ± 0 _._ 6) · 10 [−][3] for the
eastern and western components, respectively) in a region encompassing twice the FWHMs. As indicated by its kinematics, this is
likely an ongoing galaxy merger (Schouws et al. 2022a). A similar
double-component UV morphology is seen in UVISTA-Z-001, although the two components separated by ∼ 0 _._ 68 [′′] or 3 _._ 5 kpc display
a more equal _𝐿_ [O iii] / _𝐿_ UV ratio (respectively (6 _._ 3 ± 0 _._ 2) · 10 [−][3] and
(5 _._ 0 ± 0 _._ 2) · 10 [−][3] for the eastern and western components).
To investigate such apparent peculiarities in the [O iii] morphology further, we have regridded images of the [O iii] 88 μm to

[C ii] 158 μm lines (integrated over the FWHM centred on the line,
created from imaging parameters that have been chosen to match
beam sizes; see Table 2) to a common coordinate mesh to create
maps of their ratio in regions where both lines are detected with at
least 3 _𝜎_ so that SNR [O iii]/[C ii] ≳ 2. On the scales down to which
we resolve the lines (around 2 to 3 kpc), the line ratio can indeed also
vary significantly across the galaxy, as illustrated by the example of
COS-3018555981 in the top panel of Figure 9, where the line ratio
varies locally from the order of unity up to more than 10. The ratio
map of UVISTA-Z-019, shown in the bottom panel of Figure 9, also
reveals indications of a spatially varying ratio (on the order of 2 to
4 in the centre). It further shows an enhanced ratio in the northern
and southern outskirts; although the SNR will be reduced in these
regions, this does not appear to be due to noise (demonstrated by
spectra extracted from manually placed beams as in Appendix B).
It lacks strong evidence for a clear gradient, however, as is the case
for the other three sources not shown here (due in part to a lack of
resolution and/or overlap in the [O iii] and [C ii] lines).
The dust continuum and rest-frame UV imaging, shown by
overlaid contours, are matched in PSF by convolving the _HST_ imag

MNRAS **000**, 1–23 (2022)



ing with a kernel found by the Richardson-Lucy algorithm. To maximise SNR, we show the continuum images created under a natural
weighting scheme (see Section 2.2.2), which are therefore at slightly
higher resolution than [O iii] and [C ii]. Interestingly, the location
of the dust continuum seem to mostly coincide with the side of the
galaxy which shows a lower [O iii]/[C ii] ratio. Given SNR of the
continuum detection in this case (∼ 10 _𝜎_ ; see Figure 1 and Table 3)
and the beam size (∼ 0 _._ 7 [′′] ), we estimate the positional accuracy to
be ∼ 0 _._ 1 [′′], indicating the observed offset and alignment with the
northwestern region is significant. [20] Given the link between a high

[O iii]/[C ii] ratio on the one hand and a starburst’s young age or
high ionisation parameter on the other (as shown in Section 5.4; see
also e.g. Vallini et al. 2021), this suggests the relatively unobscured
region in the southeast with high [O iii]/[C ii] may be experiencing
a more recent and/or intense burst of star formation. In contrast,
it appears to be inconsistent with a scenario of UV-bright regions
being slightly more evolved sites of star formation, where SNe (or
other types of feedback) have been able to clear out the dust. A lack
of dust implies the gas is likely low in metallicity, potentially linked
with an inflow of pristine gas triggering the burst of star formation.
This tentative interplay between the FIR line ratio and degree of
dust obscuration is further tested in Figure 10, where we show measurements of [O iii]/[C ii] as a function of the infrared excess (IRX),
IRX ≡ _𝐿_ IR / _𝐿_ UV . Global measurements of the DGS and GOALS
samples are shown, as are the five _𝑧_ ∼ 7 star-forming galaxies discussed in this work. In addition, we placed individual beams across
all five sources to measure these quantities on a spatially resolved
scale (see Appendix B for details).
We considered measurements only when exceeding the estimated sensitivity by at least 2 _𝜎_, setting upper or lower limits (2 _𝜎_ )
if only one of the lines and/or continua shows a detectable signal.
These measurements are clearly pushing the SNR of the data since a
lot of points are in fact limits, mostly due to a lack of significant dust
continuum (see also the large median error bar on non-limits). As
may be expected from the data with the highest SNR, spatially resolved measurements of COS-3018555981 do yield four significant
measurements spanning a [O iii]/[C ii] ratio from 5 to 8 and IRX
from 0 _._ 5 to 0 _._ 9 (both with a spread of around 0 _._ 2 dex). Three measurements of UVISTA-Z-001 are similarly spread out (∼ 0 _._ 2 dex)
at slightly lower [O iii]/[C ii] ratio (3 to 5) and higher IRX (1 to
1 _._ 4). For UVISTA-Z-019, two beams have confidently detected IRX
values, with one [O iii]/[C ii] detection and one upper limit (both
approximately ∼ 2 and ∼ 3, respectively). For several beams placed
over COS-2987030247, IRX ≲ 5, while the [O iii]/[C ii] ratio in

one beam is measured to be ∼ 9.

Combined with the data obtained on a global scale, there is
a tentative negative correlation where a galaxy (region) with high
IRX tends to have a lower [O iii]/[C ii] ratio. This fits in with the
picture sketched above, in which young and/or intense bursts of star
formation, accompanied with a large [O iii]/[C ii] ratio, occur in
unobscured and hence likely metal-poor regions, whereas obscured
star formation is linked to more moderate line ratios.


**6** **SUMMARY AND CONCLUSIONS**


We have presented ALMA observations of the [O iii] 88 μm line in
five _𝑧_ ∼ 7 star-forming (Lyman-break) galaxies that have previously


20 For this estimate, we consulted Section 10.5.2 of the ALMA Technical
Handbook (Cortes et al. 2020).

20 _J. Witstok et al._


been spectroscopically confirmed by ALMA via their [C ii] 158
μm line, each yielding a confident [O iii] detection (SNR _>_ 5).
We complement these observations with new _HST_ rest-frame UV
imaging of two of the sources. Furthermore, we have presented
a non-detection of [N ii] 205 μm in COS-2987030247 in addition
to the corresponding dust continuum measurements around each
emission line. We summarise our findings as follows:


- For two sources, COS-2987030247 and UVISTA-Z-007, we do not
confidently detect dust continuum emission in any ALMA band. For
COS-3018555981 and UVISTA-Z-019, however, we have significant detections at ∼ 160 μm yet we do not detect the continuum
at ∼ 90 μm. In UVISTA-Z-001, we detect compact ∼ 90 μm continuum emission in band 8, in contrast to a more extended dust
reservoir observed at ∼ 160 μm. The compact component has a
seemingly typical dust temperature of ∼ 60 K, while the extended
component is likely colder. The dust-continuum measurements of
COS-3018555981 also favour a low dust temperature coupled with a
high dust mass: the dust temperature, nominally _𝑇_ dust = 29 [+] − [9] 5 [K (or]
_𝑇_ dust _<_ 48 K at 95% confidence) compared to a CMB temperature
of 21 K at _𝑧_ ∼ 7, may be lower than those of all other EoR sources
known, while its dust mass implies a high stellar metallicity yield
(accompanied by a top-heavy IMF) and may point towards the need
of other dust production and/or growth mechanisms beyond SNe.

- The non-detection of [N ii] 205 μm in COS-2987030247 allows us
to set a lower limit on the [C ii]/[N ii] ratio ( _𝐿_ [C ii] / _𝐿_ [N ii] _>_ 4 _._ 8 at
3 _𝜎_ ), which is fully consistent with [C ii] production in a PDR-like
medium, and renders H ii regions the unlikely primary origin of the

[C ii] emission (except in a more extreme physical environment with
low metallicity, high ionisation parameter, and/or high gas density).

- We find modest ratios of [O iii] 88 μm to [C ii] 158 μm (around 2
to 3) for the sources with moderate EWs of the optical [O iii] and
Hβ lines (rest-frame EW ∼ 700 Å) while the ratio is comparatively
higher (6 to 8) for the sources with more extreme EWs (EW _>_
1000 Å), consistent with a positive correlation between EW and

[O iii]/[C ii] seen in local metal-poor dwarf galaxies.

- Through the photoionisation code Cloudy, we find that a young
stellar population embedded in a nebula of typical density with
a high ionisation parameter appears an appropriate model of the
physical environment in which the FIR emission lines originate.
Surprisingly, however, the modelled nebular emission barely reproduces the observed strength of the [O iii] 88 μm line in sources with
high EW([O iii] + Hβ). Moreover, we find the Cloudy modelling
only recovers the observed [O iii] 88 μm line strength when the α/Fe
ratio relative to solar is raised by increasing the abundances of α
elements, leading to a relatively cool ionised gas ( _𝑇_ ∼ 8000 K), in
contrast to direct measurements of potential local analogues (i.e.
metal-poor dwarf galaxies). This suggests luminous LBGs at _𝑧_ ∼ 7
might be more chemically enriched than is often assumed, or else,
that significant [O iii] 88 μm emission emerges from a low density,
moderately cool medium outside of the modelled H ii regions.

- We find the [O iii]/[C ii] ratio shows a tentative anti-correlation
with the degree of dust obscuration (measured through the IRX) on
spatially resolved scales, similar to the trend seen in the local Universe on global scales of metal-poor dwarf galaxies and (U)LIRG
starburst galaxies. This suggests a large [O iii]/[C ii] ratio accompanies young and/or intense bursts of star formation, which occur in
unobscured and hence likely metal-poor regions.



**DATA AVAILABILITY**


_HST_ data underlying this article are available in the MAST
archive at [10.17909/6gya-3b10](https://dx.doi.org/10.17909/6gya-3b10) (GO 13793), [10.17909/T9-JHSF-](https://dx.doi.org/10.17909/t9-jhsf-m392)
[M392](https://dx.doi.org/10.17909/t9-jhsf-m392) (GO 16506) and from `[https://archive.stsci.edu/](https://archive.stsci.edu/prepds/3d-hst/)`
`[prepds/3d-hst/](https://archive.stsci.edu/prepds/3d-hst/)` (the 3D-HST Treasury Program). _Gaia_ data may
be obtained from `[https://gea.esac.esa.int/archive/](https://gea.esac.esa.int/archive/)` . The
ALMA data underlying this article are available in the ALMA science archive at `[https://almascience.eso.org/asax/](https://almascience.eso.org/asax/)` under
by the following project codes (see also Table 2):


– ADS/JAO.ALMA#2015.1.01111.S

– ADS/JAO.ALMA#2018.1.01359.S

– ADS/JAO.ALMA#2018.1.00429.S

– ADS/JAO.ALMA#2018.1.01551.S

– ADS/JAO.ALMA#2017.1.00604.S

– ADS/JAO.ALMA#2015.1.00540.S

– ADS/JAO.ALMA#2018.1.00085.S

– ADS/JAO.ALMA#2018.1.00933.S

– ADS/JAO.ALMA#2019.1.01611.S

– ADS/JAO.ALMA#2019.1.01524.S

– ADS/JAO.ALMA#2018.1.00085.S

– ADS/JAO.ALMA#2019.1.01611.S


Reduced data underlying this article will be shared on reasonable request to the corresponding author.


**ACKNOWLEDGEMENTS**


We are grateful to Caitlin Casey and Seĳi Fujimoto for insightful discussions on the reduction and interpretation of the ALMA measurements. We furthermore thank the anonymous referee for their comments. JW, RS, RM, and GCJ acknowledge support from the ERC
Advanced Grant 695671, “QUENCH”, and the Fondation MERAC.
RS acknowledges support from a Netherlands Organisation for Scientific Research (NWO) Rubicon grant, project number 680-501518, and an STFC Ernest Rutherford Fellowship (ST/S004831/1).
RM also acknowledges funding from a research professorship from
the Royal Society. MA acknowledges support from FONDECYT
grant 1211951, CONICYT+PCI+INSTITUTO MAX PLANCK DE
ASTRONOMIA MPG190030, CONICYT+PCI+REDES 190194
and ANID BASAL project FB210003. JAH gratefully acknowledges support of the VIDI research program with project number 639-042-611, which is (partly) financed by the NWO. This
work has extensively used casa (McMullin et al. 2007), developed
by an international consortium of scientists based at the National
Radio Astronomical Observatory (NRAO), the European Southern Observatory (ESO), the National Astronomical Observatory
of Japan (NAOJ), the Academia Sinica Institute of Astronomy
and Astrophysics (ASIAA), CSIRO Astronomy and Space Science (CSIRO/CASS), and the Netherlands Institute for Radio Astronomy (ASTRON), under the guidance of NRAO. Furthermore,
it has used the following packages in python: the SciPy library
(Jones et al. 2001), its packages NumPy (Van der Walt et al. 2011)
and Matplotlib (Hunter 2007), the Astropy (Astropy Collaboration et al. 2013, 2018), pymultinest (Feroz et al. 2009; Buchner
et al. 2014), and DrizzlePac packages ( `[https://www.stsci.](https://www.stsci.edu/scientific-community/software/drizzlepac.html)`
`[edu/scientific-community/software/drizzlepac.html](https://www.stsci.edu/scientific-community/software/drizzlepac.html)` .
This work was based on observations taken by the Atacama
Large Millimeter/submillimeter Array (ALMA). ALMA is a partnership of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), MOST and ASIAA


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 21



(Taiwan), and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ.
This work was furthermore partially based on new observations made with the NASA/ESA _Hubble_ _Space_ _Telescope_ ( _HST_ ),
obtained at the Space Telescope Science Institute (STScI), which is
operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-26555. These observations
are associated with programme #16506. Additionally, _HST_ archival
data was obtained from the data archive at the STScI. STScI is operated by the Association of Universities for Research in Astronomy,
Inc. under NASA contract NAS 5-26555.

Finally, this work has made use of data from the European
Space Agency (ESA) mission _Gaia_ ( `[https://www.cosmos.esa.](https://www.cosmos.esa.int/gaia)`
`[int/gaia](https://www.cosmos.esa.int/gaia)` ), processed by the _Gaia_ Data Processing and Analysis Consortium (DPAC, `[https://www.cosmos.esa.int/web/](https://www.cosmos.esa.int/web/gaia/dpac/consortium)`
`[gaia/dpac/consortium](https://www.cosmos.esa.int/web/gaia/dpac/consortium)` ). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the _Gaia_ Multilateral Agreement.


**REFERENCES**


Abel N. P., Ferland G. J., Shaw G., Troland T. H., O’Dell C. R., 2005, in
American Astronomical Society Meeting Abstracts. p. 81.17
Akins H., et al., 2022, preprint, ( `[arXiv:2206.06939](http://arxiv.org/abs/2206.06939)` )
Arata S., Yajima H., Nagamine K., Abe M., Khochfar S., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa2809)

[498, 5541](https://ui.adsabs.harvard.edu/abs/2020MNRAS.498.5541A)
[Asplund M., Grevesse N., Sauval A. J., Scott P., 2009, ARA&A, 47, 481](http://dx.doi.org/10.1146/annurev.astro.46.060407.145222)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Bakx T. J. L. C., et al., 2020, MNRAS, 493, 4294](http://dx.doi.org/10.1093/mnras/staa509)

[Bakx T. J. L. C., et al., 2021, MNRAS, 508, L58](http://dx.doi.org/10.1093/mnrasl/slab104)

[Behrens C., Pallottini A., Ferrara A., Gallerani S., Vallini L., 2018, MNRAS,](http://dx.doi.org/10.1093/mnras/sty552)


[477, 552](https://ui.adsabs.harvard.edu/abs/2018MNRAS.477..552B)
[Berg D. A., Skillman E. D., Henry R. B. C., Erb D. K., Carigi L., 2016, ApJ,](http://dx.doi.org/10.3847/0004-637X/827/2/126)

[827, 126](https://ui.adsabs.harvard.edu/abs/2016ApJ...827..126B)
[Bouwens R., et al., 2020, ApJ, 902, 112](http://dx.doi.org/10.3847/1538-4357/abb830)
[Bouwens R. J., et al., 2021, AJ, 162, 47](http://dx.doi.org/10.3847/1538-3881/abf83e)
[Bouwens R. J., et al., 2022, ApJ, 931, 160](http://dx.doi.org/10.3847/1538-4357/ac5a4a)
[Bowler R. A. A., Dunlop J. S., McLure R. J., McLeod D. J., 2017, MNRAS,](http://dx.doi.org/10.1093/mnras/stw3296)

[466, 3612](https://ui.adsabs.harvard.edu/abs/2017MNRAS.466.3612B)
Bowler R. A. A., Bourne N., Dunlop J. S., McLure R. J., McLeod D. J.,
[2018, MNRAS, 481, 1631](http://dx.doi.org/10.1093/mnras/sty2368)
Bowler R. A. A., Cullen F., McLure R. J., Dunlop J. S., Avison A., 2022,

[MNRAS, 510, 5088](http://dx.doi.org/10.1093/mnras/stab3744)
Braatz J., Biggs A., Sanhueza P., Corvillon A., 2021, ALMA Cycle 8 2021 Proposer’s Guide. `[https://almascience.eso.org/](https://almascience.eso.org/documents-and-tools/cycle8/alma-proposers-guide)`
```
  documents-and-tools/cycle8/alma-proposers-guide
```

[Buchner J., et al., 2014, A&A, 564, A125](http://dx.doi.org/10.1051/0004-6361/201322971)

[Carilli C. L., Walter F., 2013, ARA&A, 51, 105](http://dx.doi.org/10.1146/annurev-astro-082812-140953)

[Carniani S., et al., 2018a, MNRAS, 478, 1170](http://dx.doi.org/10.1093/mnras/sty1088)
[Carniani S., Maiolino R., Smit R., Amorín R., 2018b, ApJ, 854, L7](http://dx.doi.org/10.3847/2041-8213/aaab45)
[Carniani S., et al., 2020, MNRAS, 499, 5136](http://dx.doi.org/10.1093/mnras/staa3178)
[Casey C. M., 2012, MNRAS, 425, 3094](http://dx.doi.org/10.1111/j.1365-2966.2012.21455.x)
[Casey C. M., Narayanan D., Cooray A., 2014, Phys. Rep., 541, 45](http://dx.doi.org/10.1016/j.physrep.2014.02.009)
[Casey C. M., et al., 2021, ApJ, 923, 215](http://dx.doi.org/10.3847/1538-4357/ac2eb4)
[Chabrier G., 2003, PASP, 115, 763](http://dx.doi.org/10.1086/376392)
Chen L.-H., Hirashita H., Hou K.-C., Aoyama S., Shimizu I., Nagamine K.,
[2018, MNRAS, 474, 1545](http://dx.doi.org/10.1093/mnras/stx2863)

[Clements D. L., Dunne L., Eales S., 2010, MNRAS, 403, 274](http://dx.doi.org/10.1111/j.1365-2966.2009.16064.x)

[Cormier D., et al., 2015, A&A, 578, A53](http://dx.doi.org/10.1051/0004-6361/201425207)

[Cormier D., et al., 2019, A&A, 626, A23](http://dx.doi.org/10.1051/0004-6361/201834457)
Cortes P. C., et al., 2020, ALMA Technical Handbook. `[https:](https://almascience.eso.org/documents-and-tools/cycle8/alma-technical-handbook)`
```
  //almascience.eso.org/documents-and-tools/cycle8/

  alma-technical-handbook

```

MNRAS **000**, 1–23 (2022)



[Cortzen I., et al., 2020, A&A, 634, L14](http://dx.doi.org/10.1051/0004-6361/201937217)
[da Cunha E., et al., 2013, ApJ, 766, 13](http://dx.doi.org/10.1088/0004-637X/766/1/13)
[Cunningham D. J. M., et al., 2020, MNRAS, 494, 4090](http://dx.doi.org/10.1093/mnras/staa820)
[Dayal P., Ferrara A., 2018, Phys. Rep., 780, 1](http://dx.doi.org/10.1016/j.physrep.2018.10.002)
[De Looze I., et al., 2014, A&A, 568, A62](http://dx.doi.org/10.1051/0004-6361/201322489)
[Decarli R., et al., 2014, ApJ, 782, L17](http://dx.doi.org/10.1088/2041-8205/782/2/L17)
[Díaz-Santos T., et al., 2017, ApJ, 846, 32](http://dx.doi.org/10.3847/1538-4357/aa81d7)
[Draine B. T., 2006, ApJ, 636, 1114](http://dx.doi.org/10.1086/498130)
[Drew P. M., Casey C. M., 2022, ApJ, 930, 142](http://dx.doi.org/10.3847/1538-4357/ac6270)
Eldridge J. J., Stanway E. R., Xiao L., McClelland L. A. S., Taylor G., Ng
[M., Greis S. M. L., Bray J. C., 2017, Publ. Astron. Soc. Australia, 34,](http://dx.doi.org/10.1017/pasa.2017.51)
[e058](https://ui.adsabs.harvard.edu/abs/2017PASA...34...58E)

[Endsley R., Stark D. P., Chevallard J., Charlot S., 2021, MNRAS, 500, 5229](http://dx.doi.org/10.1093/mnras/staa3370)
Faisst A. L., Fudamoto Y., Oesch P. A., Scoville N., Riechers D. A., Pavesi
[R., Capak P., 2020, MNRAS, 498, 4192](http://dx.doi.org/10.1093/mnras/staa2545)
[Ferland G. J., et al., 2017, Rev. Mex. Astron. Astrofis., 53, 385](https://ui.adsabs.harvard.edu/abs/2017RMxAA..53..385F)
[Feroz F., Hobson M. P., Bridges M., 2009, MNRAS, 398, 1601](http://dx.doi.org/10.1111/j.1365-2966.2009.14548.x)
Ferrara A., Vallini L., Pallottini A., Gallerani S., Carniani S., Kohandel M.,

[Decataldo D., Behrens C., 2019, MNRAS, 489, 1](http://dx.doi.org/10.1093/mnras/stz2031)

[Franco M., et al., 2018, A&A, 620, A152](http://dx.doi.org/10.1051/0004-6361/201832928)

[Fruchter A. S., Hook R. N., 2002, PASP, 114, 144](http://dx.doi.org/10.1086/338393)

[Fudamoto Y., et al., 2021, Nature, 597, 489](http://dx.doi.org/10.1038/s41586-021-03846-z)

[Gaia Collaboration et al., 2016, A&A, 595, A1](http://dx.doi.org/10.1051/0004-6361/201629272)

[Gaia Collaboration et al., 2021, A&A, 649, A1](http://dx.doi.org/10.1051/0004-6361/202039657)

[Galliano F., Galametz M., Jones A. P., 2018, ARA&A, 56, 673](http://dx.doi.org/10.1146/annurev-astro-081817-051900)
[Grogin N. A., et al., 2011, ApJS, 197, 35](http://dx.doi.org/10.1088/0067-0049/197/2/35)
[Groves B. A., Dopita M. A., Sutherland R. S., 2004, ApJS, 153, 75](http://dx.doi.org/10.1086/421114)
[Guseva N. G., Izotov Y. I., Thuan T. X., 2000, ApJ, 531, 776](http://dx.doi.org/10.1086/308489)
[Harikane Y., et al., 2020, ApJ, 896, 93](http://dx.doi.org/10.3847/1538-4357/ab94bd)
[Hashimoto T., et al., 2019, PASJ, 71, 71](http://dx.doi.org/10.1093/pasj/psz049)
Heintz K. E., Watson D., Oesch P. A., Narayanan D., Madden S. C., 2021,

[ApJ, 922, 147](http://dx.doi.org/10.3847/1538-4357/ac2231)
Heintz K. E., et al., 2022, preprint, ( `[arXiv:2206.07763](http://arxiv.org/abs/2206.07763)` )
[Hirashita H., Ferrara A., Dayal P., Ouchi M., 2014, MNRAS, 443, 1704](http://dx.doi.org/10.1093/mnras/stu1290)
[Hodge J. A., da Cunha E., 2020, Royal Society Open Science, 7, 200556](http://dx.doi.org/10.1098/rsos.200556)
[Hollenbach D. J., Tielens A. G. G. M., 1999, Reviews of Modern Physics,](http://dx.doi.org/10.1103/RevModPhys.71.173)

[71, 173](https://ui.adsabs.harvard.edu/abs/1999RvMP...71..173H)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
[Inoue A. K., et al., 2016, Science, 352, 1559](http://dx.doi.org/10.1126/science.aaf0714)

[Inoue A. K., Hashimoto T., Chihara H., Koike C., 2020, MNRAS, 495, 1577](http://dx.doi.org/10.1093/mnras/staa1203)
[Izotov Y. I., Thuan T. X., 1998, ApJ, 500, 188](http://dx.doi.org/10.1086/305698)
Izotov I. I., Guseva N. G., Lipovetskii V. A., Kniazev A. I., Stepanian J. A.,
[1990, Nature, 343, 238](http://dx.doi.org/10.1038/343238a0)
[Izotov Y. I., Thuan T. X., Lipovetsky V. A., 1997, ApJS, 108, 1](http://dx.doi.org/10.1086/312956)
Jones E., Oliphant T., Peterson P., et al., 2001, SciPy: Open source scientific
tools for Python, `[http://www.scipy.org/](http://www.scipy.org/)`
[Jones G. C., Maiolino R., Caselli P., Carniani S., 2020a, MNRAS, 498, 4109](http://dx.doi.org/10.1093/mnras/staa2689)
Jones T., Sanders R., Roberts-Borsani G., Ellis R. S., Laporte N., Treu T.,
[Harikane Y., 2020b, ApJ, 903, 150](http://dx.doi.org/10.3847/1538-4357/abb943)
[Jones G. C., et al., 2021, MNRAS, 507, 3540](http://dx.doi.org/10.1093/mnras/stab2226)

[Katz H., et al., 2019, MNRAS, 487, 5902](http://dx.doi.org/10.1093/mnras/stz1672)

[Katz H., et al., 2020, MNRAS, 498, 164](http://dx.doi.org/10.1093/mnras/staa2355)

[Katz H., et al., 2022, MNRAS, 510, 5603](http://dx.doi.org/10.1093/mnras/stac028)

[Kennicutt R. C., Evans N. J., 2012, ARA&A, 50, 531](http://dx.doi.org/10.1146/annurev-astro-081811-125610)
[Kewley L. J., Nicholls D. C., Sutherland R. S., 2019, ARA&A, 57, 511](http://dx.doi.org/10.1146/annurev-astro-081817-051832)
Knudsen K. K., Watson D., Frayer D., Christensen L., Gallazzi A.,
[Michałowski M. J., Richard J., Zavala J., 2017, MNRAS, 466, 138](http://dx.doi.org/10.1093/mnras/stw3066)
[Koekemoer A. M., et al., 2011, ApJS, 197, 36](http://dx.doi.org/10.1088/0067-0049/197/2/36)
[Kroupa P., 2001, MNRAS, 322, 231](http://dx.doi.org/10.1046/j.1365-8711.2001.04022.x)
[Kroupa P., Weidner C., 2003, ApJ, 598, 1076](http://dx.doi.org/10.1086/379105)
[Laporte N., et al., 2017, ApJ, 837, L21](http://dx.doi.org/10.3847/2041-8213/aa62aa)
[Lebouteiller V., et al., 2012, A&A, 548, A91](http://dx.doi.org/10.1051/0004-6361/201218859)
Leonova E., et al., 2021, preprint, ( `[arXiv:2112.07675](http://arxiv.org/abs/2112.07675)` )
[Leśniewska A., Michałowski M. J., 2019, A&A, 624, L13](http://dx.doi.org/10.1051/0004-6361/201935149)
[Liang L., et al., 2019, MNRAS, 489, 1397](http://dx.doi.org/10.1093/mnras/stz2134)
[Litke K. C., et al., 2022, ApJ, 928, 179](http://dx.doi.org/10.3847/1538-4357/ac58f9)
[Ma X., et al., 2019, MNRAS, 487, 1844](http://dx.doi.org/10.1093/mnras/stz1324)

[Madau P., Dickinson M., 2014, ARA&A, 52, 415](http://dx.doi.org/10.1146/annurev-astro-081811-125615)

22 _J. Witstok et al._


[Madden S. C., et al., 2013, PASP, 125, 600](http://dx.doi.org/10.1086/671138)

[Madden S. C., et al., 2014, PASP, 126, 1079](http://dx.doi.org/10.1086/679312)

[Maiolino R., Mannucci F., 2019, A&ARv, 27, 3](http://dx.doi.org/10.1007/s00159-018-0112-2)

[Maiolino R., et al., 2015, MNRAS, 452, 54](http://dx.doi.org/10.1093/mnras/stv1194)
Mancini M., Schneider R., Graziani L., Valiante R., Dayal P., Maio U.,
[Ciardi B., Hunt L. K., 2015, MNRAS, 451, L70](http://dx.doi.org/10.1093/mnrasl/slv070)
[Manning S. M., et al., 2022, ApJ, 925, 23](http://dx.doi.org/10.3847/1538-4357/ac366a)
[Mateo M. L., 1998, ARA&A, 36, 435](http://dx.doi.org/10.1146/annurev.astro.36.1.435)

[McCracken H. J., et al., 2012, A&A, 544, A156](http://dx.doi.org/10.1051/0004-6361/201219507)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in
Shaw R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific
Conference Series Vol. 376, Astronomical Data Analysis Software and
Systems XVI. p. 127
[Michałowski M. J., 2015, A&A, 577, A80](http://dx.doi.org/10.1051/0004-6361/201525644)
Nagao T., Maiolino R., De Breuck C., Caselli P., Hatsukade B., Saigo K.,
[2012, A&A, 542, L34](http://dx.doi.org/10.1051/0004-6361/201219518)
[Nozawa T., Kozasa T., Umeda H., Maeda K., Nomoto K., 2003, ApJ, 598,](http://dx.doi.org/10.1086/379011)
[785](https://ui.adsabs.harvard.edu/abs/2003ApJ...598..785N)

[Oke J. B., Gunn J. E., 1983, ApJ, 266, 713](http://dx.doi.org/10.1086/160817)
[Pallottini A., et al., 2019, MNRAS, 487, 1689](http://dx.doi.org/10.1093/mnras/stz1383)

[Pallottini A., et al., 2022, MNRAS, 513, 5621](http://dx.doi.org/10.1093/mnras/stac1281)
[Pavesi R., et al., 2016, ApJ, 832, 151](http://dx.doi.org/10.3847/0004-637X/832/2/151)
[Pavesi R., Riechers D. A., Faisst A. L., Stacey G. J., Capak P. L., 2019, ApJ,](http://dx.doi.org/10.3847/1538-4357/ab3a46)

[882, 168](https://ui.adsabs.harvard.edu/abs/2019ApJ...882..168P)
[Planck M., 1901, Annalen der Physik, 309, 553](http://dx.doi.org/10.1002/andp.19013090310)
[Rémy-Ruyer A., et al., 2014, A&A, 563, A31](http://dx.doi.org/10.1051/0004-6361/201322803)
[Reuter C., et al., 2020, ApJ, 902, 78](http://dx.doi.org/10.3847/1538-4357/abb599)
Robertson B. E., 2021, preprint, ( `[arXiv:2110.13160](http://arxiv.org/abs/2110.13160)` )
[Salpeter E. E., 1955, ApJ, 121, 161](http://dx.doi.org/10.1086/145971)
[Sanders D. B., Mirabel I. F., 1996, ARA&A, 34, 749](http://dx.doi.org/10.1146/annurev.astro.34.1.749)
[Sanders R. L., et al., 2016, ApJ, 816, 23](http://dx.doi.org/10.3847/0004-637X/816/1/23)
[Sanders R. L., et al., 2021, ApJ, 914, 19](http://dx.doi.org/10.3847/1538-4357/abf4c1)
[Sawicki M., 2012, PASP, 124, 1208](http://dx.doi.org/10.1086/668636)

Schneider R., Omukai K., Inoue A. K., Ferrara A., 2006, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2006.10391.x) [369,](https://ui.adsabs.harvard.edu/abs/2006MNRAS.369.1437S)

[1437](https://ui.adsabs.harvard.edu/abs/2006MNRAS.369.1437S)

Schouws S., et al., 2022a, preprint, ( `[arXiv:2202.04080](http://arxiv.org/abs/2202.04080)` )
[Schouws S., et al., 2022b, ApJ, 928, 31](http://dx.doi.org/10.3847/1538-4357/ac4605)
Schreiber C., Elbaz D., Pannella M., Ciesla L., Wang T., Franco M., 2018,

[A&A, 609, A30](http://dx.doi.org/10.1051/0004-6361/201731506)
[Scoville N., et al., 2017, ApJ, 837, 150](http://dx.doi.org/10.3847/1538-4357/aa61a0)
[Skelton R. E., et al., 2014, ApJS, 214, 24](http://dx.doi.org/10.1088/0067-0049/214/2/24)
[Smit R., et al., 2015, ApJ, 801, 122](http://dx.doi.org/10.1088/0004-637X/801/2/122)
[Smit R., et al., 2018, Nature, 553, 178](http://dx.doi.org/10.1038/nature24631)
Sommovigo L., Ferrara A., Pallottini A., Carniani S., Gallerani S., Decataldo
[D., 2020, MNRAS, 497, 956](http://dx.doi.org/10.1093/mnras/staa1959)
[Sommovigo L., et al., 2022, MNRAS, 513, 3122](http://dx.doi.org/10.1093/mnras/stac302)
[Stanway E. R., Eldridge J. J., Becker G. D., 2016, MNRAS, 456, 485](http://dx.doi.org/10.1093/mnras/stv2661)
[Stark D. P., 2016, ARA&A, 54, 761](http://dx.doi.org/10.1146/annurev-astro-081915-023417)
Steidel C. C., Strom A. L., Pettini M., Rudie G. C., Reddy N. A., Trainor
[R. F., 2016, ApJ, 826, 159](http://dx.doi.org/10.3847/0004-637X/826/2/159)
[Sugahara Y., et al., 2021, ApJ, 923, 5](http://dx.doi.org/10.3847/1538-4357/ac2a36)
[Tamura Y., et al., 2019, ApJ, 874, 27](http://dx.doi.org/10.3847/1538-4357/ab0374)
Thompson A. R., Moran J. M., Swenson George W. J., 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition. SpringerOpen,
[doi:10.1007/978-3-319-44431-4](http://dx.doi.org/10.1007/978-3-319-44431-4)

Topping M. W., Shapley A. E., Stark D. P., Endsley R., Robertson B., Greene
[J. E., Furlanetto S. R., Tang M., 2021, ApJ, 917, L36](http://dx.doi.org/10.3847/2041-8213/ac1a79)
[Vallini L., Gallerani S., Ferrara A., Pallottini A., Yue B., 2015, ApJ, 813, 36](http://dx.doi.org/10.1088/0004-637X/813/1/36)
[Vallini L., Ferrara A., Pallottini A., Carniani S., Gallerani S., 2021, MNRAS,](http://dx.doi.org/10.1093/mnras/stab1674)


[505, 5543](https://ui.adsabs.harvard.edu/abs/2021MNRAS.505.5543V)
Viero M. P., Sun G., Chung D. T., Moncelsi L., Condon S. S., 2022, preprint,
( `[arXiv:2203.14312](http://arxiv.org/abs/2203.14312)` )
[Vĳayan A. P., et al., 2022, MNRAS, 511, 4999](http://dx.doi.org/10.1093/mnras/stac338)
Vincenzo F., Matteucci F., Belfiore F., Maiolino R., 2016, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv2598) [455,](https://ui.adsabs.harvard.edu/abs/2016MNRAS.455.4183V)

[4183](https://ui.adsabs.harvard.edu/abs/2016MNRAS.455.4183V)

[van der Walt S., Colbert S. C., Varoquaux G., 2011, Computing in Science](http://dx.doi.org/10.1109/MCSE.2011.37)
[and Engineering, 13, 22](http://dx.doi.org/10.1109/MCSE.2011.37)
[Wang T., et al., 2019, Nature, 572, 211](http://dx.doi.org/10.1038/s41586-019-1452-4)



Watson D., Christensen L., Knudsen K. K., Richard J., Gallazzi A.,

[Michałowski M. J., 2015, Nature, 519, 327](http://dx.doi.org/10.1038/nature14164)
[Williams C. C., et al., 2019, ApJ, 884, 154](http://dx.doi.org/10.3847/1538-4357/ab44aa)
Witstok J., Smit R., Maiolino R., Curti M., Laporte N., Massey R., Richard
[J., Swinbank M., 2021, MNRAS, 508, 1686](http://dx.doi.org/10.1093/mnras/stab2591)

[Zanella A., et al., 2018, MNRAS, 481, 1976](http://dx.doi.org/10.1093/mnras/sty2394)


**APPENDIX A:** **DUST PEAK TEMPERATURE**

**MEASUREMENTS**


Here, we briefly discuss the significance of the SED peak temperature as defined in equation (9) and various measurements and
predictions reported in the literature which are included in Figure 4.
Importantly, the peak temperature offers a way to compare observations of the dust temperature consistently since this approach avoids
degeneracies introduced by the chosen opacity model, a largely unconstrained quantity that is typically assumed to be a fixed value in
the greybody spectrum (e.g. Casey et al. 2014).
For a perfect blackbody, the intrinsic temperature _𝑇_ dust is exactly equal to the peak temperature but notably, for a greybody _𝑇_ peak
is generally lower (Casey 2012). This effect can be understood by
considering a simplistic two-component dust model, where the radiation field is driven towards thermal equilibrium through absorption
by the colder component in the optically thick regime, resulting in
an observed outward spectrum with a peak wavelength shifted to
a higher wavelength (i.e. lower _𝑇_ peak ). Vice versa, when fitting a
greybody SED template, the inferred intrinsic dust temperature will
strongly depend on the opacity model (e.g. Cortzen et al. 2020),
while the observed peak temperature should remain the same to
best fit the observed data. Indeed, _𝑇_ peak derived from our fits is
approximately unchanged under the assumption of different opacity
models, while the inferred _𝑇_ dust can change drastically: the more optically thick the SED is (i.e. the higher _𝜆_ 0 ), the higher the resulting
intrinsic temperature, _𝑇_ dust (see Section 4.1).
In Figure 4, we show the results at lower redshifts (0 _<_ _𝑧<_ 4)
of Schreiber et al. (2018), who fit detailed SED templates built from
multiple dust components to stacked spectra. Their reported dust
temperatures are thus mass-weighted; however, they find a simple,
linear relation where the mass-weighted temperature is roughly 91%
of the luminosity-weighted one. This implies temperatures inferred
from a greybody, which are necessarily weighted by luminosity,
are similar to (although ∼ 10% higher than) the mass-weighted
temperature, effectively setting an upper limit. We also show the
(partially extrapolated) linear fit obtained by Schreiber et al. (2018)
and the power-law fit to the peak-temperature evolution of simulated
galaxies by Liang et al. (2019).
At intermediate redshifts (2 _<_ _𝑧<_ 6), SMGs from the SPT
survey (Reuter et al. 2020) are shown as squares (all other highredshift galaxies are circles with errorbars). In addition, results for
four star-forming galaxies at _𝑧_ ∼ 6 with photometric detections
in three ALMA bands each are included as circles (Faisst et al.
2020). For five star-forming galaxies at 6 _<_ _𝑧<_ 8 – J1211-0118
and J0217-0208 at _𝑧_ ≃ 6 (Harikane et al. 2020), A1689-zD1 at
_𝑧_ ≃ 7 _._ 13 (Knudsen et al. 2017; Inoue et al. 2020; Bakx et al. 2021),
B14-65666 at _𝑧_ ≃ 7 _._ 15 (Hashimoto et al. 2019; Sugahara et al.
2021), and MACS0416-Y1 at _𝑧_ ≃ 8 _._ 31 (Tamura et al. 2019; Bakx
et al. 2020) – we derive dust properties using the same mercurius fit
described in Section 4.1 for consistency. We allow _𝛽_ IR to vary freely
for A1689-zD1, since there are four dust continuum detections; for
MACS0416-Y1, we take _𝛽_ IR = 2 as this provides a better fit. For
A1689-zD1 and B14-65666 we opt for the fiducial self-consistent


MNRAS **000**, 1–23 (2022)

_ALMA band-8 observations of luminous 𝑧_ ∼ 7 _LBGs_ 23


opacity model (we note this assumption has little impact on the
inferred _𝑇_ peak ), while for MACS0416-Y1 we use an optically thin
SED to obtain a conservative lower limit on the temperature (95%
confidence). We also adopt an optically thin SED for J1211-0118
and J0217-0208 due to the lack of a size measurement.


**APPENDIX B:** **SPATIALLY RESOLVED ANALYSIS**


In Figure A1, we show the placements of individual regions (circles
with a radius 1 _._ 5 times that of the mean circularised beam between

the [C ii] and [O iii] observations) that were used in the spatially
resolved analysis (Section 5.6). The [O iii] 88 μm and [C ii] 158 μm
maps were created from imaging parameters that have been chosen
to match beam sizes; see Table 2; the dust continuum at ∼ 160 μm
has the same imaging parameters (and therefore nearly identical
beam) as the [C ii] line. IR luminosities were calculated similarly
as discussed in Section 4. Finally, the UV continuum has been
convolved with an effective beam found by the Richardson-Lucy
algorithm to match the dust continuum PSF (see also Section 5.6).
For each source, one or several regions are highlighted in the
spectra and correspondingly by their number in the second row
of images. From the spectra, it for instance becomes clear that,
although there still seems to be some residual signal, the [O iii] flux
is weakest in region 2 and 5 of COS-3018555981.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–23 (2022)

**Figure A1.** Beam placement for spatially resolved analysis. The top row of images shows the UV continuum with contours of the ∼ 160 μm dust continuum
(starting from 2 _𝜎_ and going up in steps of 1 _𝜎_ for COS-2987030247 and UVISTA-Z-019, else 2 _𝜎_ ). The peaks of the UV and dust continua (if detected) are
indicated with a black and purple cross, respectively. Contours (at 2 _𝜎_ and 3 _𝜎_ ) of the [C ii] 158 μm and [O iii] 88 μm lines are shown in the second row (and
again the UV and dust peaks). The last two rows contain their spectra, both integrated over the entire 2 _𝜎_ region (in the same colour as their contours) as well
as for the individual regions. For each source, one or several regions are highlighted in the spectra and correspondingly by their number in the second row of
images. The filled-in grey region indicates the spectral channels over which the spectra have been integrated.


MNRAS **000**, 1–23 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "Astrometric calibration for HST images",
  "failed_quote": "The astrometry of all images was calibrated to Gaia data (Gaia Collaboration et al. 2016, 2021) by fitting a two-dimensional Gaussian to the HST images of a number of nearby stars with a 𝑔-band magnitude of 𝑔 ≲ 21 mag"
 },
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "uvcontsub performed before imaging for [C II] in COS-3018555981, UVISTA-Z-001, UVISTA-Z-019 and [O III] in UVISTA-Z-001",
  "failed_quote": "Before the imaging step, we performed the uvcontsub task to separate the continuum and line visibilities specifically for imaging the [C ii] emission in COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019 as well as the [O iii] emission in UVISTA-Z-001, where the underlying dust continuum is confidently detected"
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Conversion of [C II] luminosity to molecular gas mass",
  "failed_quote": "Since all galaxies have confident [C ii] detections, we can easily convert 𝐿[C ii] into an estimate of 𝑀mol, the molecular gas mass, though we caution our sources are beyond the redshift (and possibly metallicity) regime at which Zanella et al. established the calibration. We adopted their median conversion factor of 𝛼[C ii] = 31 M⊙ L−1⊙ and a systematic 0.3 dex spread."
 },
 {
  "path": "processing.inherited[5].what.evidence[0]",
  "value": "Cloudy stellar metallicities explored (Z_* / Z_sun in {0.05, 0.2, 1})",
  "failed_quote": "As in Harikane et al. (2020), we explored stellar metallicities of 𝑍∗/Z⊙ ∈{0.05, 0.2, 1} where, as a baseline model, we set the gas metallicity 𝑍neb equal to that of the stars under the default abundance pattern in Cloudy"
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Calibrate visibilities with the CASA pipeline, subtract continuum in the uv plane with uvcontsub where continuum is detected, and image line cubes and mfs continuum maps with tclean using natural/Briggs weighting and uv tapers.",
  "failed_quote": "Before the imaging step, we performed the uvcontsub task to separate the continuum and line visibilities specifically for imaging the [C ii] emission in COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019 as well as the [O iii] emission in UVISTA-Z-001, where the underlying dust continuum is confidently detected"
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Measure continuum flux densities and deconvolved source sizes with 2D Gaussian fits (CASA imfit) or matched apertures on beam-matched tapered maps; place 3σ upper limits from RMS noise in beam/source-sized apertures.",
  "failed_quote": "For COS-3018555981 and UVISTA-Z-019, we place 3𝜎 upper limits at ∼ 90 μm by empirically measuring the RMS noise in a beam-shaped aperture matched in (convolved) size to the source extent at ∼ 160 μm; for COS-2987030247 and UVISTA-Z-007, a (FWHM) beam-sized aperture is used."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Create moment-zero maps over the line FWHM; extract SNR-weighted spectra from contiguous >=2σ spaxels in 0.6'' tapered cubes and integrate over line channels for [O III] and [C II]; compute 3σ upper limit for [N II] over a single beam and 2x FWHM channel range.",
  "failed_quote": "We placed a 3𝜎 upper limit on the [N ii] luminosity of COS-2987030247 by first measuring the RMS noise in the untapered, naturally-weighted datacube over a single beam (assuming the source is unresolved). We obtained an upper limit on the line flux in Jy km/s by scaling this noise to a range of channels covering twice the maximum FWHM between the [O iii] and [C ii] lines (Section 3.3)"
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "COS-2987030247 is unresolved in [N II] 205 μm",
  "failed_quote": "by first measuring the RMS noise in the untapered, naturally-weighted datacube over a single beam (assuming the source is unresolved)."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "β_IR = 1.5 fixed; T_dust = 50 K fixed for sources with only upper limits; self-consistent opacity model (plus optically thin and fixed λ_0 = 200 μm variants)",
  "failed_quote": "For the three sources for which we have at least one 5𝜎 detection (COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019), on the other hand, the mercurius fitting routine described above is applied, fixing 𝛽IR = 1.5 but considering different assumptions on the opacity model: either an entirely optically thin SED or the general opacity model, with 𝜆0 set self-consistently or fixed to an extreme 200 μm."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Convert [C II] 158 μm luminosities to molecular gas masses using the Zanella et al. (2018) linear calibration and divide by M_dust and M_*.",
  "failed_quote": "Since all galaxies have confident [C ii] detections, we can easily convert 𝐿[C ii] into an estimate of 𝑀mol, the molecular gas mass, though we caution our sources are beyond the redshift (and possibly metallicity) regime at which Zanella et al. established the calibration. We adopted their median conversion factor of 𝛼[C ii] = 31 M⊙ L−1⊙ and a systematic 0.3 dex spread."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "α_[C II] = 31 M_sun L_sun^-1 with 0.3 dex systematic spread",
  "failed_quote": "We adopted their median conversion factor of 𝛼[C ii] = 31 M⊙ L−1⊙ and a systematic 0.3 dex spread."
 },
 {
  "path": "analysis_steps[6].method.evidence[0]",
  "value": "Combine and astrometrically align HST images to Gaia, convolve HST UV to match ALMA continuum PSF using a Richardson-Lucy kernel, regrid beam-matched [O III] and [C II] maps to a common mesh to create ratio maps, and extract spatially resolved [O III]/[C II] and L_IR/L_UV in apertures.",
  "failed_quote": "Calibrated data products were combined using the AstroDrizzle task (e.g. Fruchter & Hook 2002) within the DrizzlePac package setting the final_pixfrac parameter to 0.8 and choosing a pixel size of 0.065′′."
 },
 {
  "path": "analysis_steps[6].method.evidence[2]",
  "value": "Combine and astrometrically align HST images to Gaia, convolve HST UV to match ALMA continuum PSF using a Richardson-Lucy kernel, regrid beam-matched [O III] and [C II] maps to a common mesh to create ratio maps, and extract spatially resolved [O III]/[C II] and L_IR/L_UV in apertures.",
  "failed_quote": "The dust continuum and rest-frame UV imaging, shown by overlaid contours, are matched in PSF by convolving the HST imaging with a kernel found by the Richardson-Lucy algorithm."
 },
 {
  "path": "analysis_steps[6].fitting.evidence[0]",
  "value": "Two-dimensional Gaussian fits to HST UV sub-components and Gaia stars",
  "failed_quote": "The astrometry of all images was calibrated to Gaia data (Gaia Collaboration et al. 2016, 2021) by fitting a two-dimensional Gaussian to the HST images of a number of nearby stars with a 𝑔-band magnitude of 𝑔 ≲ 21 mag"
 },
 {
  "path": "analysis_steps[6].fitting.evidence[1]",
  "value": "Two-dimensional Gaussian fits to HST UV sub-components and Gaia stars",
  "failed_quote": "We quantified this by fitting separate two-dimensional Gaussian components to the HST images, resulting in two components with very similar integrated UV luminosities of around 7 · 1010 L⊙"
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Separating continuum and line visibilities prior to imaging",
  "failed_quote": "Before the imaging step, we performed the uvcontsub task to separate the continuum and line visibilities specifically for imaging the [C ii] emission in COS-3018555981, UVISTA-Z-001, and UVISTA-Z-019 as well as the [O iii] emission in UVISTA-Z-001"
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Combining calibrated HST WFC3 exposures via AstroDrizzle",
  "failed_quote": "Calibrated data products were combined using the AstroDrizzle task (e.g. Fruchter & Hook 2002) within the DrizzlePac package setting the final_pixfrac parameter to 0.8 and choosing a pixel size of 0.065′′."
 },
 {
  "path": "software[5].used_for.evidence[0]",
  "value": "Combining calibrated HST WFC3 exposures",
  "failed_quote": "Calibrated data products were combined using the AstroDrizzle task (e.g. Fruchter & Hook 2002) within the DrizzlePac package setting the final_pixfrac parameter to 0.8 and choosing a pixel size of 0.065′′."
 },
 {
  "path": "results_numeric[35].evidence[0]",
  "value": "COS-3018555981 SN dust yield y_dust,SN = 4.5 M_sun",
  "failed_quote": "𝑦dust, SN (M⊙) ≲ 0.2 4.5+13.1−3.3 0.09+0.2−0.06 ≲ 0.3 0.6+2.5−0.5"
 },
 {
  "path": "results_numeric[42].evidence[0]",
  "value": "UVISTA-Z-001 molecular gas mass M_mol = 20.9 10^9 M_sun",
  "failed_quote": "UVISTA-Z-001 20.9 ± 7.9 5.8+13.5−4.3 · 103 5.5+7.1−2.3"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Tested optically thin, self-consistent λ_0, and fixed λ_0 = 200 μm opacity models, as well as higher dust emissivity (1.8 <= β_IR <= 2) and flat vs. gamma temperature priors in dust SED fitting.",
  "failed_quote": "fixing 𝛽IR = 1.5 but considering different assumptions on the opacity model: either an entirely optically thin SED or the general opacity model, with 𝜆0 set self-consistently or fixed to an extreme 200 μm."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Considered AGB stars as the main source of dust production at z ~ 7, rejected because the required dust yield per AGB star far exceeds theoretical expectations (~0.02 M_sun).",
  "failed_quote": "The yield that would be required per AGB star, 𝑦dust, AGB ∼ 1.5+4.6−1.1 M⊙ for COS-3018555981, far exceeds the theoretically expected value, ∼ 0.02 M⊙, even more so when the yield is increased up to 2× under a different IMF (as already shown for other EoR galaxies in e.g. Michałowski 2015; Leśniewska & Michałowski 2019; Schouws et al. 2022b). This renders AGB stars an unlikely candidate as the main source of dust formation in this early cosmic epoch"
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "ALMA data available in the ALMA Science Archive under the listed project codes; HST data available in MAST; Gaia data in ESA archive; reduced data shared on reasonable request.",
  "failed_quote": "The ALMA data underlying this article are available in the ALMA science archive at https://almascience.eso.org/asax/ under by the following project codes (see also Table 2):"
 }
]
```
