# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...655A..65T\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. main ©ESO 2021
July 14, 2021

## **Which molecule traces what:** **chemical diagnostics of protostellar sources**


Łukasz Tychoniec, [1][,][ 2] Ewine F. van Dishoeck, [2][,][ 3] Merel L.R. van ’t Hoff, [4] Martijn L. van Gelder, [2] Benoît Tabone, [2]

Yuan Chen, [2] Daniel Harsono, [5] Charles L. H. Hull, [6][,][ 7] Michiel R. Hogerheijde, [2][,][ 8] Nadia M. Murillo, [9] John J. Tobin [10]


1 European Southern Observatory, Karl-Schwarzschild-Strasse 2, 85748 Garching bei München, Germany
e-mail: `lukasz.tychoniec@eso.org`
2 Leiden Observatory, Leiden University, PO Box 9513, 2300RA, Leiden, The Netherlands
3 Max-Planck-Institut für Extraterrestrische Physik, Giessenbachstrasse 1, D-85748 Garching, Germany
4 Department of Astronomy, University of Michigan, 500 Church Street, Ann Arbor, MI 48109, USA
5 Institute of Astronomy and Astrophysics, Academia Sinica, No. 1, Sec. 4, Roosevelt Road, Taipei 10617, Taiwan, R. O. C.
6 National Astronomical Observatory of Japan, NAOJ Chile, Alonso de Córdova 3788, Office 61B, 7630422, Vitacura, Santiago,
Chile
7 Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura, Santiago, Chile
8 Anton Pannekoek Institute for Astronomy, University of Amsterdam, Science Park 904, 1098 XH Amsterdam, The Netherlands
9 Star and Planet Formation Laboratory, RIKEN Cluster for Pioneering Research, Wako, Saitama 351-0198, Japan
10 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA


July 14, 2021


**ABSTRACT**


_Context._ The physical and chemical conditions in Class 0/I protostars are fundamental in unlocking the protostellar accretion process
and its impact on planet formation.
_Aims._ The aim is to determine which physical components are traced by different molecules at sub-arcsecond scales (<100 – 400 au).
_Methods._ We use a suite of Atacama Large Millimeter/submillimeter Array (ALMA) datasets in Band 6 (1 mm), Band 5 (1.8 mm)
and Band 3 (3 mm) at spatial resolutions 0 [′′] . 5 – 3 [′′] for 16 protostellar sources. For a subset of sources, Atacama Compact Array (ACA)
data at Band 6 with a spatial resolution of 6 [′′] are added. The availability of both low- and high-excitation lines, as well as data on
small and larger scales, are important to unravel the full picture.
_Results._ The protostellar envelope is well traced by C [18] O, DCO [+] and N 2 D [+], with the freeze-out of CO governing the chemistry at
envelope scales. Molecular outflows are seen in classical shock tracers like SiO and SO, but ice-mantle products such as CH 3 OH and
HNCO released with the shock are also observed. The molecular jet is a key component of the system, only present at the very early
stages, and prominent not only in SiO and SO but also occasionally in H 2 CO. The cavity walls show tracers of UV-irradiation such as
hydrocarbons C 2 H and c-C 3 H 2 as well as CN. The hot inner envelope, apart from showing emission from complex organic molecules
(COMs), also presents compact emission from small molecules like H 2 S, SO, OCS and H [13] CN, most likely related to ice sublimation
and high-temperature chemistry.
_Conclusions._ Sub-arcsecond millimeter-wave observations allow to identify those (simple) molecules that best trace each of the
physical components of a protostellar system. COMs are found both in the hot inner envelope (high excitation lines) and in the outflows
(lower-excitation lines) with comparable abundances. COMs can coexist with hydrocarbons in the same protostellar sources, but they
trace different components. In the near future, mid-IR observations with JWST–MIRI will provide complementary information about
the hottest gas and the ice mantle content, at unprecedented sensitivity and at resolutions comparable to ALMA for the same sources.


**Key words.** stars: formation, astrochemistry, techniques: interferometric, ISM: molecules, submillimeter: ISM



**1.** **Introduction**


The formation of Sun-like stars is set in motion by the collapse
of a cold, dense cloud. Many different physical processes take
place in the protostellar stage – first few 10 [5] yrs that are critical
to the subsequent evolution of the star and its planetary system
(Lada 1987). The mass of the star and that of its circumstellar
disk are determined during this embedded phase (Hueso & Guillot 2005) and the first steps of planet formation must take place
then (Greaves & Rice 2010; Williams 2012; ALMA Partnership
et al. 2015; Manara et al. 2018; Harsono et al. 2018; Tobin et al.
2020; Tychoniec et al. 2018; Tychoniec et al. 2020; Segura-Cox
et al. 2020). At the same time, on larger scales, the collapsing
envelope is dispersed by the energetic action of bipolar jets and



winds emanating from the star-disk system which create outflows of entrained gas and dust (Arce & Sargent 2006; Offner
& Arce 2014)


Rotational transitions of molecules are a powerful tool to
probe other components of the system and can be used to infer densities, temperatures, UV fields, chemical abundances and
kinematics (van Dishoeck & Blake 1998; Evans 1999). Until recently, studies of low-mass protostars have suffered from insufficient spatial resolution to disentangle these different physical
components. The advent of submillimeter interferometry opened
the possibility to study protostellar systems at much smaller
scales than with single-dish observations (e.g., Chandler & Carlstrom 1996; Hogerheijde et al. 1999; Schilke et al. 1992; Wilner
et al. 2000; Jørgensen et al. 2005a; Tobin et al. 2011).


Article number, page 1 of 38

_A&A proofs:_ manuscript no. main



With the Atacama Large Millimeter/submillimeter Array
(ALMA), it is possible to image many molecular lines on the
relevant physical scales with achievable observing times at subarcsecond resolution. Impressive ALMA studies of individual
low-mass protostars have been presented, focusing both on simple species (< 6 atoms) and complex molecules (> 6 atoms)
(e.g., Sakai et al. 2014a; Jørgensen et al. 2016; López-Sepulcre
et al. 2017; Lee et al. 2019a; Codella et al. 2018; Lee et al.
2019b; Manigand et al. 2020; van Gelder et al. 2020; Bianchi
et al. 2020). The first ALMA surveys of complex molecules on
a larger sample are taking place (Yang et al. 2021) and of Class
I disks (Podio et al. 2020; Garufi et al. 2021). The CALYPSO
survey with NOEMA studied a larger sample of protostars but
at more limited resolution and sensitivity (Belloche et al. 2020;
Maret et al. 2020; Podio et al. 2021).
Here we present ALMA data of 16 protostellar sources covering rotational transitions of various molecules; we use these
data to build a complete picture of what types of molecules trace
which physical structures in protostars. This sample constitutes
one of the largest combinations of high-resolution ALMA observations of Class 0/I protostars to date in ALMA Band 3, 5, and 6.
Covering a broad range of protostellar properties within the lowmass regime, the aim is to identify and describe key molecular
tracers of future Sun-like stars and what physical components
of star-forming sources they correspond to. Parts of the ALMA
datasets presented here have been already published, focusing on
different aspects: complex organic molecules (van Gelder et al.
2020; Nazari et al. 2021); Class I disks temperature structure
(van ’t Hoff et al. 2020a); outflows and high-velocity jets in Serpens (Hull et al. 2016; Tychoniec et al. 2019), molecular emission associated with magnetic fields (Hull et al. 2017; Le Gouellec et al. 2019). In this work we make a comprehensive overview
of these different datasets, making full use of those observations,
with uniform analysis methods. This allows to reveal and systematise the molecular tracers of Class 0/I protostars. Out of
16 presented sources 11 are included in upcoming _James Webb_
_Space Telescope_ (JWST) observations with the Mid-Infrared Instrument (MIRI; Wright et al. 2015) (GTO1290; GTO1257) and
Near-Infrared Spectrograph (NIRSpec) ( GO1960; GTO1186;
GO1798; GO2104)


_1.1._ _Physical components of a protostellar system_


Class 0 sources are defined by their strong excess of submillimeter luminosity and very low bolometric temperatures <70 K
(André et al. 1993; Chen et al. 1995). These sources are associated with powerful outflows, and the envelope mass dominates
the mass of the entire system. Class I sources are defined by having an infrared spectral index indicating strong reddening (Lada
1987) with bolometric temperatures of 70–650 K (Chen et al.
1995). Those systems have already converted most of their envelope mass into disk and protostar (Crapsi et al. 2008; van Kempen et al. 2009b; Maury et al. 2011). For the typical envelope
masses of sources presented here and average disk masses found
by Tychoniec et al. (2020), the _M_ disk / _M_ env ≃ 1% for Class 0 and
≃ 20% for Class I, with values up to 75–98% in cases of rotationally supported disks (Jørgensen et al. 2009).
The different components of protostellar systems vary significantly in their physical conditions, such as density and temperature, molecular enrichment, and dynamics. Our current knowledge about them is described briefly below to set the scene for
the interpretation of our data.
_Envelope._ The envelope surrounding a protostar is the material that fuels the accretion process onto the star and disk. The


Article number, page 2 of 38



physical conditions in the outer envelope on scales of a few 1000
au are reminiscent of those of starless cores with heavy freezeout, and their chemical composition is directly inherited from the
cloud out of which the star is being born (Caselli & Ceccarelli
2012). Systematic motions such as infall or expansion can occur but otherwise they are characterized by low turbulence and
narrow (FWHM < 0.5 - 1 km s [−][1] ) line profiles indicative of quiescent gas (Jørgensen et al. 2002).
_Warm inner envelope_ . In the innermost part of the envelope
on scales of the disk, temperatures rise above 100 K, so any water and complex organic molecules (COMs) contained in ices
are released from the grains back into the gas where they are
readily observed at submillimeter wavelengths. This region with
its unique chemical richness is called the hot core, or to distinguish it from its high-mass counterpart, hot corino (Herbst & van
Dishoeck 2009).
_Jets_ _and_ _outflows_ . As the material is accreting from the envelope onto the disk, excess angular momentum has to be transported via a still elusive process to allow material to accrete on
the growing protostar. Jets and outflows constitute compelling
candidates to extract angular momentum via magnetic fields. In
the earliest stages when the mass loss is at its peak, the densities are high enough to form molecules in the internal shocks in
the jet (Bachiller & Gomez-Gonzalez 1992; Tafalla et al. 2010).
Much slower (<20 km s [−][1] ) and less collimated gas moving away
from the protostar is called an outflow. Their origin remains debated. Large scale outflows reveal bow-shock shells and cavities
possibly driven by the fast intermittent jet (Gueth et al. 1996;
Gueth & Guilloteau 1999; Tychoniec et al. 2019). Temperatures
in shocked regions are much higher than in the surrounding envelope, up to a few thousand K, and sputtering of grain cores
and ice mantles can further result in unique chemical signatures
(Arce et al. 2008; Flower & Pineau des Forêts 2013).
_Outflow cavity walls._ These are the narrow zones in between
the cold dense quiescent envelope material and the lower-density
warm cone where outflows are propagating at large velocities.
Cavity walls are exposed to UV radiation from the accreting
star-disk boundary layer, which can escape through the outflow
cavity without being extincted (Spaans et al. 1995). This creates
conditions similar to those found in Photon Dominated Regions
(PDRs), which occur throughout the interstellar medium near
sources of intense UV radiation (Hollenbach & Tielens 1997).
In units of the interstellar radiation field (ISRF, Draine 1978),
typical values of 10 [2] –10 [3] are found on scales of ∼ 1000 au (van
Kempen et al. 2009a; Yıldız et al. 2012; Benz et al. 2016; Karska
et al. 2018).
_Young disk._ In the inner envelope, a protoplanetary disk starts
to form as the natural outcome of a rotating collapsing core (Ulrich 1976; Cassen & Moosman 1981; Terebey et al. 1984). A
young disk should be rotating in Keplerian motion. At early
stages it is difficult to identify whether the so-called embedded disk is rotationally supported, since any molecular emission
from the disk is entangled with that from the envelope. In recent years several embedded disks have been identified to have
Keplerian rotational structure on scales of ∼100 au (Tobin et al.
2012; Murillo et al. 2013; Ohashi et al. 2014; Yen et al. 2017).
Molecular tracers in young disks, apart from providing the kinematic information, can probe their temperature structure as well
(van ’t Hoff et al. 2018b).
This work is organized as follows. In Section 2, the observations used in this work are presented, Section 3 presents
the results of this work including detections and morphology of
the targeted molecules. In Section 4 the results are discussed.
with special focus on which molecular tracers are correspond

Tychoniec et al.: Which molecule traces what


Table 1: Targeted protostellar systems


Source name R.A. Decl. _d_ Class _L_ bol _T_ bol _M_ env Ref.
(J2000) (J2000) (pc) (L ⊙ ) (K) (M ⊙ )
Serpens SMM1 18:29:49.8 +01:15:20.5 439 0 109 39 58 (1)
Serpens S68N 18:29:48.1 +01:16:43.3 439 0 6 58 10 (2)
Ser-emb 8 (N) 18:29:48.7 +01:16:55.5 439 0 — — — —
Serpens SMM3 18:29:59.2 +01:14:00.3 439 0 28 38 13 (1)
BHR 71 12:01:36.3 -65:08:53.0 200 0 15 44 2.7 (1)
IRAS 4B 03:29:12.0 +31 13 08.1 293 0 7 28 4.7 (1)
Per-emb-25 03:26:37.5 +30:15:27.8 293 0/I 1.9 61 2.0 (2)
B1-c 03:33:17.9 +31:09:31.8 293 0 5 48 15 (2)
HH211-mm 03:43:56.8 +32:00:50.2 293 0 2.8 27 19 (2)
L1448-mm 03:25:38.9 +30:44:05.3 293 0 13 47 15 (2)
L1527 IRS 04:39:53.9 +26:03:09.5 140 0/I 1.6 79 0.12 (3)
B5-IRS1 03:47:41.6 +32:51:43.7 293 I 7 181 3.5 (2)
TMC1 04:41:12.7 +25:46:34.8 140 I 0.9 101 0.14 (1)
IRAS 04302 04:33:16.5 +22:53:20.4 140 I 0.7 300 0.05 (1)
L1489 IRS 04:04:43.0 +26:18:57.0 140 I 3.8 200 0.2 (1)
TMC1A 04:39:34.9 +25:41:45.0 140 I 2.7 118 0.2 (1)


(1) Kristensen et al. 2012, (2) Enoch et al. 2009, (3) Green et al. 2013



ing to each of the physical components. The focus is on a qualitative description, rather than quantitative analyses for which
source specific models and more rotational transitions of a given
molecule would be needed. We summarize our work in Section

5.


**2.** **Observations**


_2.1._ _Datasets_


Six different ALMA 12m datasets at Band 3, 5, and 6 are used
in this work to cover 14 out of 16 sources. The spatial resolution
of all ALMA 12m datasets is comparable (0 [′′] . 3–0 [′′] . 6), except for
2017.1.01174.S, where Band 3 observations are obtained at 3 [′′] .
Additionally for 6 out of 16 sources in Band 6, ACA observations with 7m antennas were obtained at 6 [′′] resolution.
The targeted protostars are well-known objects located in
different star-forming regions. They span a range of properties
within the low-mass regime; the probed range of _L_ bol, _T_ bol and
_M_ env is shown in Table 1, and are provided by a suite of observations across the infrared and submillimeter spectrum (Enoch
et al. 2009; Kristensen et al. 2012; Green et al. 2013).
The details of the observations are summarized in Table A.1.
The spatial resolution allows to observe protostellar systems at
solar-system scales; Band 5 and 6 observations provide a resolution of ∼0 [′′] . 5, which corresponds to a 70–220 au diameter for
sources in our sample. Thus, regions down to 35-110 au radius
in the inner envelope are probed. The Band 3 data achieve moderate resolution of ∼3 [′′] which provides information on intermediate envelope scales of 500–1500 au. The ACA observations of
six sources at 6 [′′] resolution probe envelope scales of 800–2000

au.


_2.2._ _Spectral setup of the observations_


A collection of different datasets using different ALMA bands
implies varying spectral and spatial resolution as well as spectral
coverage across the analysis. This is the reason that throughout
this paper the sources shown in the figures differ when presenting
detections and maps of different molecules. In all cases, when
the molecule is discussed, only those sources where the given



transition has been targeted are discussed. All non-detections are
explicitly stated. Table A.2 provides a list of targeted molecular
transitions, with sources that have a particular line covered and
detected or not detected.
The ALMA observations presented here target different
spectral setups across Band 3, 5, and 6. This allows to probe
the strongly varying physical scales and conditions. In particular, our Band 3 data grants access to lines at very low excitation
levels that enable tracing more extended material. Dust is less
optically thick in Band 3 compared with Band 6 which potentially allows to peek inside the densest inner regions. Band 6
offers a usual set of tracers of outflows: CO, SiO and SO.
Cold outer envelopes with temperatures < 20 K are probed
with low _E_ up transitions. Additionally, non-thermal processes
such as sputtering of material from the grains in the outflow, will
also be seen in low _E_ up due to their lower critical densities. On
the other hand, thermal desorption from grains in the innermost
regions are best probed with lines with high _E_ up . With the large
span of frequencies of the observations, different transitions of
the same molecule can be detected and used to trace different
components of the system (e.g., a HNCO line at _E_ up = 15 K is
available in Band 3 and lines at 70 and 125 K are covered in
Band 6).


**3.** **Results**


_3.1._ _Continuum emission from protostars_


Figure 1 presents continuum emission maps toward four example protostars obtained with ALMA at ∼ 0 [′′] . 5. The examples illustrate most characteristic features observed in the continuum
maps. The continuum images for all sources are presented in
Fig. B.1.
The continuum emission observed at millimeter wavelengths
(1.3 - 3 mm in our observations) traces thermal dust emission
from the inner envelope and the embedded disk. In the Class 0
protostars, the central continuum source generally appears compact _R_ <100 au (e.g., B1-c, Fig. 1). The example of SMM3 (Fig.
B.1) shows a large resolved dust structure perpendicular to the
outflow, but its classification as a disk is not certain. The fact
that we observe primarily compact continuum emission towards


Article number, page 3 of 38

_A&A proofs:_ manuscript no. main


Fig. 1: Continuum emission at 1.3 mm of four example protostellar systems obtained with ALMA at 0 [′′] . 5 resolution. Symbols of stars
point to confirmed protostellar sources, circles show condensations of continuum emission, without confirmed protostellar nature,
dotted lines show outflow cavity walls, and dashed lines show streams of envelope material. Arrows indicate outflow directions.



Class 0 sources is consistent with observations of confirmed
rotationally-supported disks (e.g., Tobin et al. 2018; Maury et al.
2019; Tobin et al. 2020) and predictions of models (Visser &
Dullemond 2010; Harsono et al. 2015b; Machida et al. 2016).
While we assume that this compact emission belongs to the
young, embedded disk, we do not have spatial and kinematic
resolution to confirm the presence of Class 0 Keplerian disks in
our sample.

The extended continuum emission in Class 0 sources is consistent with a significant amount of envelope material surrounding the protostar. In the case of the SMM1 system, presented
in Fig. 1 (left), the continuum clumps outside the central emission are components of multiple protostellar systems, marked
with stars, confirmed by the presence of individual molecular
outflows (Hull et al. 2016, 2017). Binary components are also
seen in TMC1, BHR71, and IRAS 4B (Fig. B.1). In the case of
S68N presented in Fig. 1, two emission peaks that stand out from
the diffuse envelope emission are marked with circles, but their
protostellar nature is not confirmed.


_3.2._ _Protostellar envelope_


We present molecules that trace the bulk of the protostellar envelope in Fig. 2. The protostellar envelope has a typical radius
on the order of a few 1000 au (Jørgensen et al. 2002; Kristensen
et al. 2012). Thus, the sub-arcsecond ALMA 12m array observations tend to resolve-out the envelope emission. For instance,
the maximum recoverable scale (MRS) of ALMA Band 6 observations at 0 [′′] . 4 presented here is 5 [′′], which is between 600–2000
au diameter depending on distance to the source. For that reason, we discuss in this section mainly the ALMA-ACA observations obtained at lower spatial resolution (6 [′′] ; 750–2500 au) for
six sources in our datasets; Class 0 sources: B1-c, BHR71, Peremb-25, SMM3, and IRAS 4B, and Class I source TMC1. The
ACA can zoom-in on what was previously contained in a singledish beam of 15–20 [′′], while the MRS of ACA (30 [′′] ) enables us
to preserve sensitivity to large-scale emission. The MRS of all
observations presented here are reported in Table A.1.
In Fig. 2 typical envelope tracers C [18] O 2–1 ( _E_ up = 16 K),
DCO [+] 3–2 ( _E_ up = 21 K), and N 2 D [+] 3–2 ( _E_ up = 22 K), ob

Article number, page 4 of 38



served at 6 [′′] resolution with the ACA, are presented toward example Class 0 and Class I sources – B1-c and TMC1, respectively. The emission from the presented molecules exhibits similar behaviour for all Class 0 sources, therefore B1-c serves as a
representative case; TMC1 is the only Class I source in the sample with 7m observations available. The maps for all sources for
which these molecules have been targeted can be found in Appendix C. All envelope tracers presented here are characterized
by narrow line profiles with FWHM ∼ 1 km s [−][1] .


The C [18] O emission peak coincides with the continuum peak
for our six sources and appears to be compact, less than 1000 au
diameter for B1-c and TMC1. For B1-c and all Class 0 sources
(Fig. C.1), low-level extended C [18] O emission is seen along the
outflow direction. For the only Class I source targeted with the
ACA, emission is marginally resolved in the direction perpendicular to the outflow.


In our observations N 2 D [+] is seen extended in the direction
perpendicular to the core major axis toward B1-c (Fig. 2) and
other Class 0 sources except IRAS 4B (Fig.C.2). In the case of
IRAS 4B the emission from this molecule appears dominated
by large-scale emission from the filament detected toward this
source, connecting it with IRAS 4A (Sakai et al. 2012). The peak
of the N 2 D [+] emission is significantly shifted from the continuum
peak in all cases, with a significant decrease in the inner regions
in some cases (see BHR 71 in Fig. C.2). Similar extended N 2 D [+]
emission in other Class 0 sources was seen by Tobin et al. (2013)
based on lower resolution SMA and IRAM-30m data. For TMC1
the N 2 D [+] molecule is not detected.


The DCO [+] emission is seen extended in a similar fashion to
what is observed for N 2 D [+] . However, contrary to N 2 D [+], DCO [+]
is brightest on the continuum peak for all sources except TMC1

                                      and Per-emb-25. For these two sources, the emission peak is off
set by 1000–2000 au from the continuum source in the direction
perpendicular to the outflow. In the Class I source TMC1, DCO [+]
is present on much smaller scales (< 2000 au radius) than in
Class 0 sources.

Tychoniec et al.: Which molecule traces what


Fig. 2: Maps of key envelope tracers toward B1-c (Class 0, top) and TMC1 (Class I, bottom) obtained with ACA. Contours represent continuum emission at 1.3 mm observed with ACA. Note different distances to B1-c and TMC1 resulting in different spatial
resolutions of the maps. _Left:_ C [18] O 2 – 1 _Middle:_ N 2 D [+] 3 – 2. _Right:_ DCO [+] 3 – 2. All moment 0 maps are integrated from -2.5 to
2.5 km s [−][1] w.r.t � sys .



_3.3._ _Outflows and jets_


Figure 3 presents the extremely high-velocity (EHV) molecular
jet component for HH211, B1c, and SMM3 observed in SiO with
the ALMA 12m array; the L1448-mm EHV is shown in Fig. 12.
The latter and HH211 are well-known EHV sources (Guilloteau
et al. 1992; Lee et al. 2007) while SMM3 and B1-c are new detections of the jet component. HH211 shows SiO emission at
low-velocities because the outflow is almost in the plane of the
sky, but the high velocities are evident from the large proper motion movements of the bullets (∼115 km s [−][1] ; Lee et al. 2015).
CO, H 2 CO, and SiO in the EHV jets of Emb8N and SMM1
are presented in detail in Hull et al. (2016) and Tychoniec et al.
(2019).


These data are particularly interesting as still only few
molecules tracing EHV jets have been identified to date (see Lee
2020 for review). Apart from those presented here – CO, SiO,
SO, and H 2 CO– molecules such as HCO [+] and H 2 O have been
seen in this high-velocity component (Kristensen et al. 2012; Lee
et al. 2014). What is especially important to highlight is the third
detection of a H 2 CO bullet in SMM3 after IRAS 04166 (Tafalla
et al. 2010) and Emb8N (Tychoniec et al. 2019). These detec


tions mean that either a significant fraction of ice-coated dust is
released with the jet, or that the H 2 CO is efficiently produced in
the jet through gas-phase chemistry.
In the case of L1448-mm and HH211, there are several
molecular bullets along the jet axis with velocities up to 100
km s [−][1], while both B1-c and SMM3 show a much simpler structure with two bullets detected on one side in the former and a
single pair of symmetrically placed bullets observed in the latter
case. B1-c actually has a pair of bullets ∼ 200 au from the continuum peak, with the other bullet at 2500 au only seen in the
redshifted part of the jet. The emission in SiO and SO appears
very similar (Fig. D.2, Fig. D.3). There are no other molecules
tracing the high-velocity component toward this source. H 2 CO
and [12] CO are not targeted with our ALMA 12m datasets toward
B1-c. The SMM3 jet has two distinct high-velocity bullets at

∼
3200 au from the source which appear similar in CO, SiO and
SO (see zoom-in on Fig 4). Additionally, the redshifted bullet
shows faint, but significant emission from H 2 CO. No traces of
H 2 CO are found in the blueshifted outflow.
Figure 5 presents low-velocity outflow tracers CO 2–1
( _E_ up = 16 K) for TMC1, SO 5 6 –4 5 ( _E_ up = 35 K), and SiO 4–
3 ( _E_ up = 21 K) for B1-c. In Fig. D.1 we present an overview of


Article number, page 5 of 38

_A&A proofs:_ manuscript no. main


Fig. 3: Maps of the EHV jets observed in SiO. Moment 0 maps are presented in color scale with continuum emission at 1.3 mm
presented in black contours, both obtained with 12m observations. SiO 4–3 map of HH211 integrated from -20 to -10 and from 10
to 20 km s [−][1] w.r.t � sys ; B1-c ntegrated from -70 to -40 and from 40 to 70 km s [−][1] w.r.t � sys ; SMM3 integrated from -60 to -40 and
from 20 to 35 km s [−][1] w.r.t � sys .



CO 2–1 emission for five sources obtained with the ALMA 12 m
array at 0 [′′] . 4 resolution. The sources show a variety of emission
structures in the low velocity gas (<20 km s [−][1] ). In all cases, we
do not capture the entirety of the outflows as they extend beyond
the primary beam of observations (∼ 30 [′′] ). SMM3 and Emb8N
have very narrow outflow opening angles (< 20 degrees), while
SMM1, S68N and TMC1 present larger opening angles.

CO emission is especially prominent in the cavity walls,
which can be related to both the limb brightening effect as well
as higher (column) density of the material in the outflow cavity walls. This is especially highlighted in the Class I source,
TMC1, where CO emission is almost exclusively seen in the outflow cavity walls. Even though CO is piling up in this region, it
is observed at velocities up to 15 km s [−][1] so it is clearly tracing
the entrained material and not the envelope. The lower envelope
density in Class I results in less material to be entrained in the
outflow. In SMM1, three CO outflows from SMM1-a, SMM1-b,
and SMM1-d are overlapping (Hull et al. 2016; Tychoniec et al.
2019).

In Fig. D.2, SiO maps are presented: Band 5 SiO 4–3 ( _E_ up =
21 K) and Band 6 SiO 5–4 ( _E_ up = 31 K) data are shown in velocity ranges corresponding to the low-velocity outflow. In contrast to CO emission, the low-velocity SiO is mostly observed in
clumps of emission instead of tracing the entirety of the outflowing gas. Several such clumps can be seen in the S68N source. In
some cases, the clumps are relatively symmetric (Emb8N, B1c), while monopolar emission is seen in other examples (L1448mm, SMM1-d). In the case of SMM1-a and SMM1-b, very weak
SiO emission at low velocities is observed. SiO emission in outflows is exclusively present in the Class 0 sources, while absent
in the Class I sources, TMC1 and B5-IRS1, covered in these data

sets.

Fig. D.3 presents SO 5 6 –4 5 ( _E_ up = 35 K) and SO 6 7 –5 6
( _E_ up = 47 K) observations in Band 6. The emitting regions of
SO are comparable with those of SiO for the Class 0 sources.
The cases of S68N and B1-c show that SO emission also peaks
at the source position while SiO is absent there. Thus, SO and


Article number, page 6 of 38



SiO do not always follow each other and some SO might be
associated with hot core emission (Drozdovskaya et al. 2018).
Important differences are observed for TMC1, where SO seems
to be associated with the remainder of the envelope or the disk,
while the SiO is not detected toward this source, as mentioned
above.

HCN 1–0 ( _E_ up = 4 K) and H [13] CN 2–1 ( _E_ up = 12 K) maps
are presented in Fig. D.4 and D.5, respectively. HCN is clearly
seen in outflowing material enhanced in similar regions as lowvelocity SiO. For Emb8N the HCN emission has been associated with intermediate velocity shock (Tychoniec et al. 2019). In
B1-c and L1448-mm weak extended emission along the outflow
direction is detected but H [13] CN strongly peaks on source. In the
case of HH211, H [13] CN is seen only in the outflow, with a geometry consistent with the outflow cavity walls, but with velocity
profiles that are consistent with the outflowing material.
Ice-mantle tracers are a different class of molecules detected
in low-velocity protostellar outflows. They are produced and entrained through interactions between the jet and the envelope.
Here we present ALMA 12m array observations in Band 6 at
0 [′′] . 5 resolution for CO 2 – 1 ( _E_ up = 17 K), CH 3 OH 2 1,0 – 1 0,0
( _E_ up = 28 K), and H 2 CO 3 0,3 – 2 0,2 ( _E_ up = 21 K), and in Band
3 at 3 [′′] for CH 3 CN 6 1 – 5 1 ( _E_ up = 26 K), CH 3 CHO 6 1,6,0 –
5 1,5,0 ( _E_ up = 21 K), and HNCO 5 0,5 – 5 0,4 ( _E_ up = 16 K). Fig.
6 compares maps of integrated emission from those molecules
with those of CO for S68N. All ice-mantle tracers detected in the
outflow are observed in their low-energy transitions. Additional
maps for S68N are presented in the Appendix (Fig. D.6): Band
6 0 [′′] . 5 resolution image of CH 3 CHO 14 0,14 –13 0,13 ( _E_ up = 96 K)
and H 2 CCO 13 1,13 –12 1,12 ( _E_ up = 101 K), which is overlapping
with NH 2 CHO 12 2,10 –12 2,10 ( _E_ up = 92 K), and the Band 3 image
at 3 [′′] resolution of CH 3 OCHO 10 0,10 –9 0,9 ( _E_ up = 30 K).
Around the frequency of H 2 CCO 3 1,13 –12 1,12 ( _E_ up = 101
K) line an extended emission can be seen in the outflow, this is
however coincident with the NH 2 CHO which is only 4 km s [−][1]
apart (Fig. D.6). NH 2 CHO is more commonly observed in the
shocked regions than H 2 CCO (Ceccarelli et al. 2017; Codella

Fig. 4: Zoom-in on molecular bullets from the SMM3 jet (see Fig. 3). CO, SiO, SO, and H 2 CO molecular transitions are presented.
_Top:_ Norther/blueshifted bullet. Moment 0 maps are integrated from -60 to -40 km s [−][1] w.r.t � sys . The map center is offset from the
SMM3 continuum center by (–3 [′′] . 7, +10 [′′] . 3). _Bottom:_ Southern/redshifted bullet. Moment 0 maps are integrated from 20 to 40 km
s [−][1] . The map center is offset from the SMM3 continuum center by (+2 [′′] . 7, –7 [′′] . ).


Fig. 5: Low-velocity outflow in CO, SO, and SiO. Moment 0 maps of CO toward TMC1, SO and SiO map toward B1c are integrated
from -10 to 10 km s [−][1] w.r.t � sys .



et al. 2017); it is possible that those lines are blended. More lowenergy transitions would be required to confirm the identification
of these lines.


The velocities observed for ice-mantle tracers in the outflow
are <15 km s [−][1] with respect to the systemic velocity. This is
slower than the CO and SiO outflow line wings which have ve


locities up to 20–30 km s [−][1] . On the other hand, the lines are
clearly broader than those of molecular tracers of UV-irradiated
regions that trace passively heated gas (see Section 4.3).


Ice-mantle tracers are also detected in SMM3 and B1-c, two
Class 0 protostars (Fig. D.7 and D.8). For SMM3 only a lower
_A_ _i j_ transition of CH 3 OH with _E_ up = 61 K was targeted and not


Article number, page 7 of 38

_A&A proofs:_ manuscript no. main


Fig. 6: Maps of the ice mantle tracers toward the S68N outflow, with the CO low-velocity outflow map for reference. _Top:_ CO,
H 2 CO and CH 3 OH moment 0 maps obtained in Band 6 at 0 [′′] . 5 resolution. Circles show regions from which spectra were obtained
for analysis in Section 7.1. _Bottom:_ CH 3 CHO, HNCO, and CH 3 CN moment 0 maps obtained in Band 3 at 2 [′′] . 5 resolution. The
emission is integrated from -10 to -1 km s [−][1] and from 1 to 10 km s [−][1] w.r.t � sys .



detected towards this source. B1-c has its methanol emission
confused with the high-velocity SO emission, whereas emission
from other COMs in the outflow is weak and appears only on
the redshifted part of the outflow. Thus, S68N is the best case to
study the composition of shock-released ice mantles.


_3.4._ _Outflow cavity walls_


In this section, we highlight key molecules detected in the outflow cavity walls. It is challenging to precisely distinguish cavity walls from the outflowing material. The velocity of the gas
in the cavity walls should be lower than in the outflow, as the
cavity wall contains envelope material at rest but which is passively heated by UV radiation. We first discuss maps of species
associated with cavity walls and then their line profiles.

Figure 7 presents integrated emission maps of key tracers
discussed in this section for two examples: SMM3 and B1-c.
Plots for the remaining sources (S68N, Emb8N, and TMC1) are
presented in the Appendix in Fig. E.1. Key tracers of the outflow
cavity walls are simple unsaturated hydrocarbon molecules: cC 3 H 2 4 4,1 –3 3,0 ( _E_ up = 32 K) for SMM3 and TMC1, and C 2 H


Article number, page 8 of 38



3 2.5,3 –2 1.5,2 ( _E_ up = 25 K) for S68N, B1-c, and Emb8N, as seen
in maps obtained with ALMA Band 6 at 0 [′′] . 5 resolution.


In Emb8N and SMM3 the emission from C 2 H and c-C 3 H 2,
respectively, is symmetric; it appears similar in extent and shape
on both sides of the continuum source. Comparison with CO
emission, which traces the bulk of the outflowing gas, indicates
that the hydrocarbons are located in the outflow cavity walls
close to the source. A higher energy transition of c-C 3 H 2 7 2,6 –
7 1,7 _E_ up =61 K is seen towards SMM3 closer to the protostar
compared with the lower-energy transition. This reflects the increase of temperature of the cavity walls closer to the source. For
B1-c, the emission from C 2 H is U-shaped suggestive of a cavity wall, stronger on the blueshifted side of the outflow, which
could be either a projection effect or an asymmetry in the envelope structure. For B1-c no ALMA CO observations exist to
compare with the bulk of the outflow at comparable resolution;
however, the other outflow tracer, SO, confirms the outflow direction and rough extent of the outflow cavity walls. Moreover,
the shape of the cavity walls is consistent with the appearance
of the CO 3–2 outflow observed with SMA toward this source at
4 [′′] resolution (Stephens et al. 2018).

Tychoniec et al.: Which molecule traces what


Fig. 7: Maps of the outflow cavity wall tracers toward SMM3 and B1c, with low-velocity outflow map for reference. _Top:_ Moment
0 maps toward SMM3 of CO 2–1, c-C 3 H 2 6 1,6 –5 0,5, and [13] CS 5–4 obtained in Band 6 at 0 [′′] . 5 resolution and CN 1–0 in Band 3 at
3 [′′] with continuum emission at the same band and resolution in black contours. _Bottom:_ Moment 0 maps toward B1c of SO 6 7 –5 6,
C 2 H 3 2.5,3 –2 1.5,1 and H [13] CO [+] 3–2 obtained at 0 [′′] . 5 and CN 1–0 at 3 [′′] with continuum emission at the same band and resolution in
black contours. The emission is integrated from -5 to -1 km s [−][1] and from 1 to 5 km s [−][1] w.r.t � _lsr_ . Outflow directions and delineated
cavity walls are shown in C 2 H and C 3 H 2 maps.



S68N presents a chaotic structure (Fig. E.1, top), but C 2 H
is found elongated in the outflow direction. While it is difficult
to identify the cavity wall, the C 2 H emission surrounds the CO
outflow emission. The C 2 H emission toward this source is asymmetric, with stronger emission in the blueshifted part of the outflow. Emission of c-C 3 H 2 toward the Class I source TMC1 (Fig.
E.1, bottom) is not directly related to the cavity walls, but is extended perpendicular to the outflow, which suggests that c-C 3 H 2
traces the envelope or extended disk material.
Figure 7 also shows CN 1–0 ( _E_ up = 5 K) observed at 3 [′′]
resolution in Band 3 for SMM3 and B1-c. Compared with C 2 H,
CN is tracing similar regions. In S68N CN has a similar extent
as C 2 H but not over the full extent of the outflow traced by CO.
In B1-c, the CN emission has a similar shape of the cavity wall
cone as seen in C 2 H, but also a significant contribution from
larger scales is detected. In all cases the CN emission avoids the
central region, which likely results from on-source absorption by
the foreground CN molecules.
In some cases, like SMM3, the extent of the CN is broader
than hydrocarbons, more comparable with CO, but the narrow
linewidths suggest that this emission is still associated with passively irradiated envelope rather than with the entrained outflow.
TMC1 presents a high-resolution example of CN emission
(Fig. E.1). The offset between CO and CN reveals a physical
structure of the inner regions of the protostellar system: the en


trained outflow traced with CO appears closer to the jet axis,
while CN highlights the border between the outflow cavity wall
and quiescent envelope. CN is sensitive to UV radiation, as it
can be produced with atomic C and N, whose abundances are enhanced in PDRs, with UV photodissociation of HCN contributing as well (Fuente et al. 1993; Jansen et al. 1995; Walsh et al.
2010; Visser et al. 2018).
H [13] CO [+] emission is presented for B1c (Fig. 7), and S68N
and Emb8N (Fig. E.1) observed in Band 6 at 0 [′′] . 4 resolution. The
bulk of the emission from this molecule appears to be related
to the cold envelope, however streams of material can be seen
in B1-c and S68N. The streams of gas observed in H [13] CO [+] are
coincident with the cavity wall observed in C 2 H. As H [13] CO [+]
is expected to probe the dense envelope, the similarity of the
morphology of the traced material between H [13] CO [+] and C 2 H
and CN shows that the envelope material is UV-irradiated. [13] CS
observed in Band 6 with the 12m array is detected for SMM3
(Fig. 7). The morphology of [13] CS emission is very similar to
that of c-C 3 H 2 .

In Fig. 8 spectra of ice mantle tracers, CH 3 OH and H 2 CO,
and the hydrocarbon molecules, C 2 H and C 3 H 2 are presented.
All spectra are shifted by their source velocity to zero km s [−][1] .
In case of S68N, it is seen that C 2 H and CH 3 OH have very similar line profiles indicating that they trace similar material. The
width of ∼ 10 km [−][1] suggests that this material is entrained with


Article number, page 9 of 38

_A&A proofs:_ manuscript no. main


Fig. 8: Spectra obtained at the cavity wall positions for hydrocarbons (red) and ice-mantle tracers (blue). _Left:_ C 2 H 3 2.5,2 –2 1.5,1
( _E_ up = 25 K) and CH 3 OH 2 1,0 –1 0,1 ( _E_ up = 28 K) spectra for S68N, _Middle:_ C 2 H 3 2.5,2 –2 1.5,1 ( _E_ up = 25 K ) and SO 6 7 –5 6 ( _E_ up = 48
K) spectra for B1-c, _Right:_ c-C 3 H 2 4 4,1 –3 3,0 ( _E_ up = 32 K), H 2 CO 3 2,1 –2 2,0 ( _E_ up = 68 K), and [13] CS 5–4 ( _E_ up = 33 K) spectra for
SMM3.



the outflow. A narrow component appears to be superposed at
systemic velocities. Note that fine splitting of C 2 H blends the
spectra although the other transition at +2 km s [−][1] does not affect the blueshifted velocity component. In contrast, B1c shows
only remarkably narrow C 2 H line profiles with a FWHM of ∼ 2
km s [−][1], and SMM3 has similarly narrow c-C 3 H 2 and [13] CS lines
compared with broader H 2 CO emission (Fig. 8, right).


_3.5._ _Inner envelope_


Fig. 9 shows emission from H 2 CCO, HNCO, t-HCOOH, SO,
H 2 CS, and H [13] CN for the Class 0 protostar B1-c, and H 2 S and
OCS lines for SMM3; all observed with the ALMA 12m array
at 0 [′′] . 5. Several molecules tracing the inner hot envelope are detected in 7m data and are presented in Fig. F.1. CCS is detected
for SMM3, BHR71, and IRAS 4B, while non-detected for B1-c,
TMC1, and Per-emb-25. OCS and H 2 S (Fig. F.1) for all targeted
in 7m Class 0 sources while non-detected for Class I sources.
The SO 6 7 –5 6 _E_ up = 48 K line is seen to peak on the central source for B1-c and S68N (Fig. D.3). SO has already been
discussed in the outflow (Section 4.2.2), but it is also prominent
in the inner envelope. While the spatial resolution does not allow to disentangle the hot core emission from the small-scale
outflow on a few hundred au scale, there is a difference between these two sources and SMM3 and Emb8N. The latter two
sources show a substantial decrease in SO intensity towards the
continuum peak, i.e., they have prominent SO emission in the
outflow, but not from the hot core. This suggests that sources
like B1-c and S68N, which are bright in SO toward the continuum emission peak, have an additional component responsible
for SO emission. This is highlighted by the narrower lines of SO
toward the continuum peak compared with the outflow in S68N
(Fig. G.1). The narrow component, visible in spectra taken onsource, has a width of ∼ 5 km s [−][1] . The main component of the
spectrum taken in the blueshifted outflow has a similar width but
has a more prominent line wing up to 20 km s [−][1] .
TMC1 clearly shows SO emission toward both components
of the binary system, slightly offset from their peak positions
(Fig. D.3). There is also a molecular ridge present in SO close to
the disk-envelope interface.


Article number, page 10 of 38



HNCO and HN [13] CO are detected toward B1-c and S68N
peaking on source in higher _E_ up transitions (Nazari et al. 2021).
For lines with _E_ up <90 K an extended component is also detected
in the outflow. SMM3 and Emb8N have no detections of HNCO
on source, but for SMM3 this molecule appears in the outflow.
For all Class I sources where the relatively strong HNCO 11 0,11 –
10 0,10 line ( _A_ _i j_ = 2 × 10 [−][4] s [−][1], _E_ up =70 K) was targeted, it was
not detected.
OCS is detected toward SMM3 peaking in the center; S68N
and SMM1 show centrally peaked O [13] CS detection, a minor isotopologue signalling a high abundance of OCS (Fig. F.2). In all
cases the emission is moderately resolved; of size ∼ 200 au in
case of SMM3 and detected up to 500 au away from source for
S68N and SMM1.
H 2 S shows strong emission toward SMM3 and is also weakly
present in TMC1. For SMM3 the emission is resolved along the
outflow direction and perpendicular to the expected disk axis.
Those are the only two sources for which H 2 S 12m array data
were taken. Additionally, the 7m data presented in the Appendix
(Fig. F.1) show prominent, centrally peaked H 2 S emission for
four more Class 0 sources.
H 2 CS is detected for B1-c, S68N and L1448-mm through
a line with _E_ up = 38 K. Another transition with _E_ up = 46 K
is found in Class I disks: IRAS-04302, L1489, and TMC1A. In
B1-c, the emission is marginally resolved, while in IRAS-04302
the molecule is clearly seen across the midplane, indicating sublimation from icy grains at temperatures of at least 20 K (van ’t
Hoff et al. 2020a; Podio et al. 2020).
H 2 CCO is detected for B1-c and S68N. For the lower _E_ up =
100 K transition, the molecule is also detected in the outflow. For
Class I sources, the transition at comparable energy is not detected. HCOOH is detected for B1-c and S68N with low-energy
transitions that are seen both on source and in the outflow, while
the higher energy line ( _E_ up = 83 K) is seen only on source.
H [13] CN is detected in B1-c and L1448-mm on source, additionally to the outflow component.
Disks are commonly observed in Class I sources (Harsono
et al. 2014; Yen et al. 2017), as the envelope clears out. Fig.
10 presents maps of the C [17] O 2–1 ( _E_ up = 16 K) and CN 2–1
( _E_ up =16 K) lines toward Class I disks and L1527-IRS, which is

Tychoniec et al.: Which molecule traces what


**4.** **Discussion**


Figure 11 summarizes current understanding about which
molecule traces which component in Class 0/I protostars. Table 2 lists all molecules discussed in this work with indication of
the physical component that they trace. Below, we will address
several implications of the results. We note that the discussion is
confined to the molecules targeted and detected in our datasets,
but is by no means complete. Other relevant tracers not discussed
here are NH 3 and N 2 H [+], which are tracing the envelope well
(e.g., Tobin et al. 2011; Chen et al. 2007). PO and PN have been
recently suggested as a cavity walls or outflow tracers, but have
very low abundances (Bergner et al. 2019). SO 2 is an important
tracer of the warm gas in the disk-envelope interface (Artur de la
Villarmois et al. 2019). Finally, this work focuses on low-energy
transitions observed with ALMA _E_ up <100 K with the exception
for hot core tracers.


_4.1._ _Cold envelope_


4.1.1. C [18] O



Fig. 9: Compact emission for B1-c and SMM3 for various
molecules tracing the warm inner envelope (hot core). Moment
0 maps shown in colorscale integrated from -3 to 3 km s [−][1] w.r.t
� sys . 1.3 mm continuum presented in contours.


identified as a Class 0/I object, observed with ALMA 12m at 0 [′′] . 3
resolution. The C [17] O and H 2 CO emission for disks in Taurus using these data are analyzed in detail by van ’t Hoff et al. (2020a).
Here we discuss CN in comparison with C [17] O. C [17] O is observed
concentrated towards the continuum emission for all disks, and
is a much cleaner tracer of the disk than any other more abundant CO isotopologues, although even C [17] O still shows some
trace emission from the surrounding envelope.



C [18] O is a good tracer of high column density material because
of its low critical density. However, it becomes less abundant
as soon as the dust temperature drops below the CO freeze-out

∼
temperature ( 20–25 K). There is also a density threshold: CO
freeze-out only occurs at densities above ∼ 10 [4] –10 [5] cm [−][3], because at lower densities the timescales for freeze-out are longer
than the lifetime of the core (Caselli et al. 1999; Jørgensen et al.
2005b).
For 4 out of 6 sources presented here at 6 [′′] resolution, Kristensen et al. (2012) performed modeling of the SED and sub-mm
spatial extent using the DUSTY code (Ivezic & Elitzur 1997).
The results provide, among other properties, a temperature structure throughout the envelope and the radius at which the temperature drops below 10 K, which is considered as the border
between envelope and the parent cloud. Kristensen et al. (2012)
obtained radii of 3800, 5000, 6700, and 9900 au for IRAS4B,
TMC1, SMM3, and BHR71, respectively. The compact C [18] O
emission observed on-source and its non-detection over the full
expected extent of the protostellar envelope can be explained by
CO freeze-out occurring already within the inner 1800 – 2500
au radius, which is the spatial resolution of our observations for
Class 0 sources. This upper limit on the CO snowline is consistent with CO snowlines typically observed and modeled toward other Class 0 protostars (Jørgensen et al. 2004; Anderl et al.
2016; Hsieh et al. 2019).
Equation 1 from Frimann et al. (2017) allows to calculate the
expected CO snow line for the current luminosity of the example
sources B1-c and TMC1 presented in Fig. 2 in the absence of
an outburst. For B1-c the snowline is expected to be at 200–
400 au radius depending on the assumptions of the sublimation
temperature (larger radii for 21 K and smaller for 28 K), while
the TMC1 CO snowline is expected to be at 100–200 au. For
the most luminous source with C [18] O 7m observations available,
the expected radius is at 400–750 au. Therefore clearly in all
cases the expected CO snowline is well within the 7m beam. In
high-resolution studies, the CO emission is often seen at greater
distances than expected from the current luminosities of those
protostars. This is attributed to accretion bursts of material which
increase their luminosities resulting in a shift of the observed CO
emission radius up to a few times its expected value (but usually
still within a 1000 au radius) (Jørgensen et al. 2015; Frimann
et al. 2017; Hsieh et al. 2019).


Article number, page 11 of 38

_A&A proofs:_ manuscript no. main


Fig. 10: Images of Class I disks observed with ALMA 12m in Band 6 (van ’t Hoff et al. 2020a). _Top:_ Moment 0 maps of C [17] O at
0 [′′] . 4 resolution integrated from -10 to 10 km s [−][1] w.r.t � sys . _Bottom:_ Moment 0 maps of CN integrated from -2 to 2 km s [−][1] w.r.t � sys .
Continuum contours in black.



4.1.2. N 2 D [+] and DCO [+]


Both DCO [+] and N 2 D [+] are considered cold gas tracers (e.g., Qi
et al. 2015). N 2 D [+] is efficiently destroyed by CO in the gasphase, therefore freeze-out of CO results in N 2 D [+] being retained
in the gas-phase at larger radii of the envelope, where temperatures are lower. This behaviour has been demonstrated in several
other protostellar sources by Tobin et al. (2011, 2013, 2019).


Both DCO [+] and N 2 D [+] are produced through reactions with
H 2 D [+] . At cold temperatures the H 2 D [+] abundance is enhanced
through the H [+] 3 [+][ HD][ →] [H] [2] [D] [+] [+][ H] [2] [reaction, which is exother-]
mic by 230 K. As the reverse reaction is endothermic, low temperatures increase H 2 D [+] . Additionally, both H [+] 3 [and] [H] [2] [D] [+] [are]
enhanced in gas where CO has been depleted. However, the CO
molecule is still needed for the production of DCO [+] through the
H 2 D [+] + CO reaction. Therefore, DCO [+] is expected to be most
abundant around the CO snowline (Jørgensen et al. 2004; Mathews et al. 2013). Warmer production routes through CH 2 D [+] +
CO are also possible (Wootten 1987; Favre et al. 2015; Carney
et al. 2018).


The difference between DCO [+] and N 2 D [+] chemistry is reflected in morphology of both molecules in the dense regions
close to the continuum peak. As DCO [+] requires gas-phase CO
for its formation, it peaks close to the CO snowline, which is
within the resolution of our observations (∼1800–2500 au radius), while N 2 D [+] is only located where CO is not present in the
gas phase. Therefore we observe a significant decrease of N 2 D [+]
in the inner envelope. If the warm production of DCO [+] is triggered in the inner regions, this will additionally produce DCO [+]
within the beam of our observations, hence DCO [+] does not decrease in the inner envelope. The extent of the DCO [+] and N 2 D [+]
emission in each source is comparable, ranging from ∼ 5000 au
in B1-c and BHR71 to 1500 au in TMC1, suggesting that their


Article number, page 12 of 38



outside radii trace the region where CO becomes present again
in the gas phase due to the low density.


The morphology of the emission from cold gas tracers such
as DCO [+] and N 2 D [+] is sensitive to the density and temperature
profile of the system, which can be affected by system geometry (i.e., outflow opening angle, disk flaring angle, flattening of
the envelope). DCO [+] has been shown to increase its abundance
in the cold shadows of a large embedded disk (Murillo et al.
2015). Emission from DCO [+] and N 2 D+ is consistent with a picture of a dissipating envelope in Class I sources, resulting in less
dense, warmer gas surrounding the protostar. TMC1 has an order of magnitude lower envelope mass compared to the Class
0 sources (Table 1; Kristensen et al. 2012). This causes the extent of the cold and dense region to shrink, preventing N 2 D [+]
from being detected, and limiting the extent of DCO [+] emission.
The dense gas toward TMC1 is clearly present only in the flattened structure surrounding the binary system, likely forming a
young, embedded disk. In fact this source is suggested to have
a rotationally-supported circumbinary disk (Harsono et al. 2014;
van ’t Hoff et al. 2020a). The geometry of the disk can create
favourable conditions for the DCO [+] enhancement in the cold

shadows of the disk.


Other relevant molecules that trace the quiescent envelope
material but are not presented here are HCO [+] and H [13] CO [+]
(Hogerheijde et al. 1997; Jørgensen et al. 2007; Hsieh et al. 2019,
van ’t Hoff et al. in prep.). These molecules have been shown
to probe the material outside of the water snowline (Jørgensen
et al. 2013; van ’t Hoff et al. 2018a). As water sublimates at temperatures ∼ 100 K, much higher than CO, HCO [+] can be seen
throughout the envelope, except for the warmest inner regions.
N 2 H [+] is tracing the envelope material and CO snowline and has
been shown to peak closer to the central protostar than N 2 D [+]
(Tobin et al. 2013). Their ratio can potentially be used as an evo

Tychoniec et al.: Which molecule traces what


Fig. 11: Summary cartoon presenting key molecular tracers of different components, limited to molecules presented in this work
except for NH 3 and N 2 H [+] which are important large scale envelope tracers. CN molecule is shown on top of the disk as it traces the
disk atmosphere and not the midplane. Protostar indicated in the center in yellow.



lutionary tracer of protostars (Emprechtinger et al. 2009). NH 3 is
also observed to map similar components as N 2 H [+] (Tobin et al.
2019).


In summary, the quiescent envelope material is traced by
dense and/or cold gas tracers. Chemical interactions result
in N 2 D [+] tracing the outer envelope where CO is frozen-out,
whereas DCO [+] is seen both in the outer envelope as well as in
the inner regions, tracing the unresolved CO snowline. C [18] O is
a good tracer of dense ( _n_ - 10 [5] cm [−][3] ) and warm ( _T_ - 30 K)
regions in the inner 2000 au radius of the protostellar systems.
The evolution of the physical conditions from Class 0 to Class I
is evident as the envelope becomes less dense and the protostellar luminosity can heat up dust and gas more easily.


_4.2._ _Outflows and jets_


Outflowing material from protostellar systems is best analyzed
with kinematic information. In the following section, we will
discuss three different componfents of protostellar outflows observed with the ALMA 12m array: 1) the high-velocity jet (>30
km s [−][1] ), 2) the low-velocity outflow (<30 km s [−][1] ), 3) the gas
that results from the interaction with the outflow – ice sputtering
products at velocities close to that of ambient material, but with
linewidths significantly broader (up to 15 km s [−][1] ) than the quiescent envelope tracers. The three components are presented in
Fig. 12 with examples of S68N, a representative case of a promi


nent outflow and ice sputtering, and L1448-mm, a source with a
prototypical high-velocity jet.


4.2.1. Extremely high-velocity (EHV) jet


There are 6 out of 7 Class 0 sources targeted at high-resolution
strengthen the conclusion that EHV jets are more common than
previously thought in Class 0 sources (Podio et al. 2021). It is argued that the molecular jet tracers have a very different physical
origin than the protostellar outflows; contrary to the low-velocity
outflow, which consists mostly of entrained envelope material,
the EHV jet is expected to be directly launched from the innermost region of the system (Tafalla et al. 2010; Lee 2020). The
high-velocity jet is comprised of atomic material which readily
forms molecules in the high-density clumps (internal working
surfaces; Raga et al. 1990; Santiago-García et al. 2009) that are
resulting from shocks in the jet, which are produced by the velocity variations of the ejection. This in turn means that by observing the high-velocity bullets, one gains insight on the variability of the accretion process (Raga et al. 1990; Stone & Norman 1993). The new EHV sources B1c and SMM3 show bullet
spacings of 1200 au in B1c and 3200 au in SMM3, which can be
converted using the terminal velocity of the jets (not corrected
for inclination) to the dynamical ages of 80 and 250 years, respectively. If the central mass of the protostar can be estimated
this can be used to provide the orbital period of the component
causing the variability (Lee 2020).


Article number, page 13 of 38

_A&A proofs:_ manuscript no. main


Table 2: Molecular tracers of physical components exclusive to this work


Molecule Envelope Disk Hot Outflow Jet Cavity

core

CO  — —   
C [18] O   —  — 
13 CO   —  — 
C [17] O    — — 
H [13] CO [+]  — —  — 
H 2 CO      —
H 2 CS —   — — —
SO —     —

SiO — — —   —
DCO [+]  — — — — —
N 2 D [+]  — — — — —
OCS — —  — — —
O [13] CS — —  — — —

HNCO — —   — —
H 2 CCO — —   — —
HCOOH — —   — —
13 CS  — — — — 

CN   — — — 

HCN — — —  — —
H [13] CN — —   — —
C 2 H  — —  — 
c-C 3 H 2 — — — — — 
CH 3 CHO — —   — —
CH 3 CN — —   — —
CH 3 OCHO — —   — —
CH 3 OH — —   — —
13 CH 3 OH — —  — — —



The fact that the EHV jet tracers are dominated by O-bearing
molecules has been associated with a low C/O ratio in the jet material (Tafalla et al. 2010). For high mass-loss rates, molecules
are produced efficiently in the jet from the launched atomic material (Glassgold et al. 1991; Raga et al. 2005; Tabone et al.
2020). Additionally the ratio of SiO-to-CO can indicate the presence of dust in the launched material, which can in turn inform
about the jet launching radius, i.e., whether it is inside or outside the dust sublimation radius (Tabone et al. 2020). The new
detections of high-velocity jets suggest that this process may be
occurring in every young Class 0 object. Studying large samples of objects with ALMA and combining with multi-transition
observations can unveil the atomic abundances of the inner regions, which are difficult to measure otherwise directly (McClure 2019).
The presence of H 2 CO in the jet could result from gas-phase
production through the reaction of CH 3 with O. Alternatively, if
the icy grains were launched with the jet, they could be sputtered
in the internal working surfaces at high velocities (Tychoniec
et al. 2019).
In summary: O-bearing species such as CO, SiO, SO, and
H 2 CO observed at high velocities are excellent tracers of the
chemistry within the protostellar jet. Those molecules most
likely formed in the internal working surfaces from the material
carried away from the launching region of the jet.


4.2.2. Low-velocity outflow


The CO molecule traces the bulk of the gas as it is the most
abundant molecule detectable in the sub-mm regime. It serves


Article number, page 14 of 38



as an indicator of the outflow extent and gas morphology, as
it is not affected by chemical processing in shocks. It can also
be used to quantify the total mass-loss rates, using the dense
cloud abundance ratio of CO/H 2 ∼ 10 [−][4] . A well-known correlation between molecular outflows and protostellar luminosities
indicates a strong link between the accretion and ejection processes (Cabrit & Bertout 1992; Bontemps et al. 1996; Mottram
et al. 2017). The decrease in accretion and total envelope mass
with evolution of the system also results in fainter, less powerful outflows. The weak emission from the Class I source TMC1,
which is an order of magnitude lower in intensity with respect to
outflows from Class 0 protostars, is consistent with this trend.


SiO is a molecule that is enhanced by several orders of magnitude in shocks compared with gas in cold and dense clouds
where most of the Si is locked in the grains (e.g., Guilloteau
et al. 1992; Dutrey et al. 1997). Shocks release Si atoms from the
grains by means of sputtering and grain destruction, leading to
subsequent reactions with OH, another product of shocks, forming SiO (Caselli et al. 1997; Schilke et al. 1997; Gusdorf et al.
2008b,a). Thus, SiO is much more prominent in high-velocity
gas, where grains are more efficiently destroyed (see Section
4.2.1), than in low-velocity shocks.


SO is enhanced in shocks through reactions of atomic S released from the grains with OH, as well as through H 2 S converted to SO with atomic oxygen and OH (Hartquist et al. 1980;
Millar & Williams 1993). Shocks could also explain the emission toward TMC1, where weak accretion shocks onto the disk
could enhance the SO abundances (Sakai et al. 2014b; Yen et al.
2014; Podio et al. 2015). Overall, there is a clear decrease of
both SiO and SO low-velocity emission from Class 0 to Class I.

Tychoniec et al.: Which molecule traces what


Fig. 12: Maps of three different components of the outflow. Moment 0 maps are presented in color scale with continuum emission
at 1.3 mm in black contours, both obtained with ALMA 12m observations. _Left:_ An extremely high-velocity (EHV) molecular jet
illustrated with the SiO (4–3) map for L1448-mm integrated from -70 to -50 and from 50 to 70 km s [−][1] w.r.t � sys . _Middle:_ Lowvelocity outflow illustrated with the CO 2–1 map for S68N integrated from -15 to -3 and from 3 to 15 km s [−][1] w.r.t � sys . _Right:_ Ice
mantle content released with shock sputtering presented with the CH 3 OH (2 1,0 – 1 0,0 ) map for S68N integrated from -8 to -1 and
from 1 to 8 km s [−][1] w.r.t � sys . The CO outflow from Ser-emb-8N is present at the edge of the map.



Either the less powerful jet cannot destroy the grains and create
conditions for the production of SiO and SO and/or the much
less dense envelope and outflow cavity walls do not provide
enough dust grains for creating large column densities of those
molecules; additionally, the excitation conditions might change
significantly with evolution of the protostellar system, hampering the detection of even low- _J_ SO and SiO transitions with critical densities in the 10 [5] − 10 [6] cm [−][3] range.
HCN is associated with the most energetic outflows (Jørgensen et al. 2004; Walker-Smith et al. 2014) and is enhanced
at high temperatures in shocks. H [13] CN is likely associated with
both the hot inner regions (not detected in HCN due to optical
thickness of the line) and the low-velocity outflow (Tychoniec
et al. 2019; Yang et al. 2020). The geometry of H [13] CN emission seen in HH211 resembles a cavity wall: it could be a result
of CN produced by UV-photodissociation and subsequent production of HCN via the H 2 + CN reaction, which requires high
temperatures (Bruderer et al. 2009; Visser et al. 2018). The fact
that H [13] CN is seen at outflow velocities shows that shocks are
required to produce HCN, which is likely released at the cavity
walls and then dragged with the outflow.


4.2.3. Shock sputtering products


Ice-mantle tracers are detected in outflows of SMM3, B1-c and
S68N protostars. As indicated in Section 3.3 S68N is the best
test-case to study the composition of shock-released ice mantles.
The morphology of the emission of ice-mantle tracers in S68N is
somewhat uniform. CH 3 CN and HNCO are clearly brighter on
the redshifted part of the outflow (south-east) and CH 3 CHO are
brighter in the blueshifted (north-west) side. CH 3 OH and H 2 CO
show an even distribution between the two lobes. The peak intensity for all species occurs at significant distances from the

∼
source ( 5000 au) and in some cases the emission drops below
the detection limit closer to the source. This is contrary to the
CO emission, which can be traced all the way back to the central
source. In all tracers the emission is also detected at the continuum position, however, this emission has a narrow profile and



results from thermal sublimation of ices in the hot core of S68N
(van Gelder et al. 2020).
The velocities observed for CH 3 OH and other ice-mantle
tracers are high enough for these molecules to be material near
the outflow cavity walls, where ice mantles could be sputtered.
These molecules therefore most likely trace low-velocity entrained material with a considerable population of ice-coated
grains that are sputtered in the shock (Tielens et al. 1994; Buckle
& Fuller 2002; Arce et al. 2008; Jiménez-Serra et al. 2008;
Burkhardt et al. 2016). Thermal desorption of molecules from
grains is not likely as dust temperatures at distances of few times
10 [3] au from the protostar are well below the desorption temperatures for most COMs. The fact that there is no enhancement of
these tracers closer to the source also argues against emission
being related to high temperature.


_4.3._ _Outflow cavity walls_


Emission from hydrocarbons and CN in the outflow cavity walls
is directly related to the exposure of those regions to the UV radiation from the accreting protostar. Both c-C 3 H 2 and C 2 H have
been prominently observed in PDRs such as the Horsehead Nebula and the Orion Bar tracing the layers of the cloud where UVradiation photodissociates molecules, which helps to maintain
high atomic carbon abundance in the gas-phase that is needed
to build these molecules. C 2 H is enhanced in the presence of
UV radiation at cloud densities (Fuente et al. 1993; Hogerheijde
et al. 1995) and c-C 3 H 2 usually shows a good correlation with
C 2 H (Teyssier et al. 2004). Both molecules have efficient formation routes involving C and C [+], although models with only PDR
chemistry tend to underpredict their abundances, especially for
c-C 3 H 2 . A proposed additional mechanism is the top-down destruction of PAHs (Teyssier et al. 2004; Pety et al. 2005, 2012;
Guzmán et al. 2015); the spatial coincidence of PAH emission
bands with hydrocarbons in PDRs is consistent with that interpretation (van der Wiel et al. 2009).
It is instructive to compare the conditions between classic
PDRs and outflow cavity walls around low-mass protostars.The


Article number, page 15 of 38

_A&A proofs:_ manuscript no. main



_G_ 0 value for Orion Bar is estimated at 2.6 × 10 [4] (Marconi et al.
1998), while the Horsehead Nebula has a much more moderate
radiation field of 10 [2] (Abergel et al. 2003). The UV radiation
field around low-mass protostars measured by various tracers
is 10 [2] –10 [3] at ∼ 1000 au from the protostar (Benz et al. 2016;
Yıldız et al. 2015; Karska et al. 2018), therefore the PDR origin
of small hydrocarbons is plausible. The top-down production of
hydrocarbons due to PAHs destruction does not appear to be an
efficient route here, as PAHs are not commonly observed in lowmass protostellar systems (Geers et al. 2009), and the UV-fields
required for this process are above 10 [3] (Abergel et al. 2003).


The difference in morphology of hydrocarbons between
Class 0 and Class I systems – outflow cavity walls in Class 0
versus rotating disk-like structure in Class I – is most likely related to the evolution of the protostellar systems. Class 0 sources
have a dense envelope and the UV radiation can only penetrate
the exposed outflow cavity walls, while for Class I it is likely
much easier for both the UV radiation from the accreting protostar and the interstellar radiation to reach deeper into the envelope or disk. This is consistent with emission from well-defined
cavity walls seen toward those sources.


The case of moderate ∼ 10 km s [−][1] velocity material observed
toward S68N indicates that the C 2 H line does not in all sources
trace exclusively the quiescent cavity walls. The profile is consistent with the observed morphology of the line (see Fig. E.1)
– emission is seen up to a few thousand au from the source and
its shape does not resemble a cavity wall as clearly as in other
sources. The narrow component centered at systemic velocity
seen in Fig. 8 indicates that while the broad component might
be dominating the emission, the UV-irradiated cavity wall also
contributes to the emission observed for S68N.


S68N could be a very young source, as the chaotic structure
of its outflow and envelope indicates (Le Gouellec et al. 2019).
The high abundances of freshly released ice-mantle components
described in Section 4.2.3 are consistent with this interpretation.
It is also possible that UV radiation produced locally in shocks is
causing the enhancement of C 2 H emission at higher velocities.


The [13] CS molecule, as a high-density tracer likely traces the
material piling up on the cavity walls pushed by the outflow.
This emission is usually slow (± 2 km s [−][1] ) indicating that this
is not outflowing gas but rather envelope material on the outflowing cavity walls. The non-detection of [13] CS in 12m data
(Fig. E.1) towards the Class I source TMC1 is consistent with
the dissipating envelope as the source evolves, hence no highdensity material is seen in the remnant cavity walls, even though
they are still highlighted by the CO emission. In the remaining
Class 0 sources with the [13] CS detections – Emb8N, SMM1 and
S68N (Fig. E.2), – emission also follows other cavity wall tracers. SMM1 is the only source that shows higher velocity structure (> 7 km s [−][1] ) of the [13] CS emission on one side of the cavity
wall. As this is spatially coincident with the high-velocity jet observed in CO (Hull et al. 2016), this emission might be related
to the material released with the jet from the envelope.


To summarize, we observe the hydrocarbons C 2 H and cC 3 H 2, as well as CN, H [13] CO [+] and [13] CS in the outflow cavity
walls of Class 0 protostars. C 2 H, as the most abundant of the
hydrocarbons presented here, is also seen prominently across
the envelope at velocities comparable to the low-velocity outflow whereas c-C 3 H 2 appears as a clean tracer of the quiescent,
UV-irradiated gas in the cavity walls in the Class 0 sources.


Article number, page 16 of 38



_4.4._ _Warm inner envelope_


4.4.1. Compact emission


The inner regions of young protostellar systems are characterized by high temperatures which result in a rich chemistry
as molecules that form efficiently in ices on grains in cold
clouds sublimate into the gas phase. Complex organic molecules
(COMs) detected in these datasets are discussed quantitatively in
detail elsewhere, for both O-bearing by van Gelder et al. (2020)
and for N-bearing species by (Nazari et al. 2021) In this section we focus on smaller molecules that also trace the innermost
hot core regions and therefore are likely abundant in ices. This
includes several small S-bearing molecules.
Both B1-c and S68N are sources characterized as hot cores
(Bergner et al. 2017; van Gelder et al. 2020), which means that
the conditions in their inner regions are favourable for release
of molecules from the ice mantles. For the well-studied case of
IRAS16293-2422, Drozdovskaya et al. (2018) have also identified a hot core component of SO based on isotopologue data, in
addition to an SO component in the large scale outflow. Overall,
SO observed in protostars appears to be related mostly to evaporation of grain mantle.
The SO appearance close to the central protostar could be
related to accretion shocks onto the disk, which are weaker than
shocks that cause the SO emission seen in the outflows (Section
4); in accretion shocks, SO can be released from the icy mantles
with the infalling material (Sakai et al. 2014b). However, narrow
linewidths of SO toward TMC1 seem to rule out the accretion
shock scenario, and points to emission along the cavity walls
(Harsono et al. 2021).
HNCO emission has been modeled by Hernández-Gómez
et al. (2018) and suggested to be a superposition of both warm
inner regions of the envelope as well as the colder, outer envelope. Its similar behaviour to sulphur-bearing species, also observed in our work, is proposed to be related to the fact that O 2
and OH are involved in formation of species like SO and HNCO
(Rodríguez-Fernández et al. 2010).
H 2 S is expected to be the dominant sulphur carrier in ices
(Taquet et al. 2020). However, it has not yet been detected in
ice absorption spectra to date (Boogert et al. 2015). The weak
emission from H 2 S in dark clouds has been modeled as a result
of the photodesorption of ices at the outside of the cloud (like in
the case of H 2 O, Caselli et al. 2012), while chemical desorption
is important for grains deeper inside the cloud but outside the
water snowline (Navarro-Almaida et al. 2020). These models are
consistent with H 2 S ice containing most of the sulphur. Multiple
lines of H 2 CS are a powerful tool to probe the warm - 100 K,
innermost regions of the protostellar systems (van ’t Hoff et al.
2020b).
While B1-c and S68N are characterized as hot cores with
many COM lines detected (van Gelder et al. 2020), and L1448mm has warm water in the inner regions (Codella et al. 2010),
SMM3 does not appear to have significant emission from COMs.
Moreover, simple molecules associated with the hot cores for
B1-c, such as SO and H 2 CO, are only seen outside of the SMM3
central source. While it is possible that the optically thick continuum prevents a detection of COMs in its inner envelope (De
Simone et al. 2020a), differences in chemistry or physical structure (e.g., a large cold disk, see Section 3.5) between the SMM3
and the hot core sources are also possible. The fact that emission
from OCS and H 2 S is centrally peaked (Fig. 9, bottom row) suggests that continuum optical depth is not an issue, although both
those species could be a result of grain destruction or ices sputtering, therefore not necessarily coming from the midplane but

Tychoniec et al.: Which molecule traces what



rather from the surface of a disk-like structure. The additional
detection of CCS in 7 data towards SMM3, which is on the other
hand not detected in B1-c could hint at different chemical composition of the two protostellar systems.


4.4.2. Embedded disks


In the case of large edge-on disks like IRAS-04302 and L1527,
the vertical structure of the emission can be probed, as well as
the radius where CO freeze-out occurs. Overall, Class I disks
are warmer than their Class II counterparts with CO freeze-out
taking place only in the outermost regions (Harsono et al. 2015a;
van ’t Hoff et al. 2018a, 2020a; Zhang et al. 2020).
We detect CN in all observed Class I disks, although it does
not trace the midplane of the disk. In the near edge-on example
of IRAS-04302, the CN emission originates from the upper layers of the disks, in the same direction as the outflow, which is
perpendicular to the disk in this source. This opens a possibility
that the emission is also related to the irradiated residual cavity
walls in those sources. TMC1A is a clear example where CN is
tracing the same material as probed by Bjerkeli et al. (2016) in
CO, which is attributed to a disk wind. TMC1 and L1527 show
CN oriented in the same direction as the disk; in TMC1 there is
also a clear filament structure on larger scales irradiated by the
UV from the protostar, seen also in other tracers.
In comparison with the C [17] O emission, which traces the midplane disk, CN thus appears in the upper layers and in the outflow, therefore in most cases the two molecules are mutually exclusive. This picture is consistent with the bulk density traced by
CO and the irradiated layers of the disk and envelope exposed
to UV traced by CN. Recent observations of a sample of Class I
sources including IRAS-04302 by Garufi et al. (2021) is consistent with CN not tracing the disk midplane.
In the younger Class 0 or borderline Class 0/I sources characterization of the disk is much more difficult because of the strong
envelope emission. Nevertheless, several Keplerian disks have
been identified with observations of CO isotopologues like C [18] O
and [13] CO (Tobin et al. 2012; Murillo et al. 2013). Our data allow
us to investigate this for the case of SMM3. Fig. G.2 shows the
red and blue-shifted emission from C [18] O toward SMM3. There
is a clear rotational signature in the direction perpendicular to the
outflow on scales of a few hundred au. However, to unambiguously identify the disk and its radius, higher spatial and spectral
resolution data are necessary.


_4.5._ _COMs in outflow versus hot core_


The complex organic molecules are already detected in the
prestellar stage of star formation (Bacmann et al. 2012; Scibelli
& Shirley 2020), where they are efficiently produced on the surfaces of icy grains (e.g., Watanabe et al. 2004; Öberg et al. 2009).
COMs can be subsequently released back into the gas through
various non-thermal desorption processes and/or be re-formed
by gas-phase reactions. In the inner envelope, temperatures are
high enough that thermal desorption of ices is enabled. In the
outflow cavity walls, sputtering by shocks can release ices from
the grains. In the hot core, COMs are detected through high excitation lines, while in the outflow, they are observed primarily
through transitions with low _E_ up . Therefore, comparing the observations of molecular complexity in outflows with hot cores
can unveil if there is any warm temperature processing of the
ices and whether some molecules also have a gas-phase production route.



Therefore, we compare abundance ratios between different
ice mantle species and methanol at three positions for S68N:
one on the source, obtained from van Gelder et al. (2020) and
Nazari et al. (2021), and one each in the blueshifted and redshifted part of the outflow, which are calculated from the fluxes
obtained in this work. We measure the abundance of the species
in a 3 [′′] region centered on CH 3 OH peak on the blueshifted and
redshifted regions. The size of the region is based on the spatial
resolution of the Band 3 data. The regions are indicated in Fig. 6.
From these regions, we extracted spectra and calculated column
densities using the spectral analysis tool CASSIS [1] .
For the CASSIS model, we assume _T_ ex = 20 K, typical of
subthermally excited molecules with large dipole moments in
outflow gas. The FWHM of the lines was fixed at 3 km s [−][1],
which is the width of the CH 3 OH line. With those parameters,
an LTE calculation provides column densities for the observed
line intensities under the assumption of optically thin emission
(see Tychoniec et al. (2019) for a discussion on uncertainties in
this method.)
Only a single CH 3 OH line 2 1,0 –1 0,1 ( _E_ up = 28 K) is detected in the outflow of S68N. Escape probability calculations
with RADEX (van der Tak et al. 2007) show that even at the
lower densities in outflows this CH 3 OH line is likely optically
thick. No optically thin CH 3 OH isotopologue is detected in the
outflow; therefore, we provide an upper limit for the [13] CH 3 OH
2 1,1 -1 0,1 ( _E_ up =28 K). The upper limit on this [13] CH 3 OH line of
1 × 10 [14] cm [−][2] translates to an upper limit on the CH 3 OH column
density of 7 × 10 [15] cm [−][2] assuming [12] C / [13] C = 70 (Milam et al.
2005).
The column density calculated from the flux measurement
of the CH 3 OH line gives of 2 × 10 [15] cm [−][2] ; thus, the methanol
abundance can be underestimated by a factor of 4. With the information available, we assume that the CH 3 OH column density
is between 2 × 10 [15] cm [−][2] and 7 × 10 [15] cm [−][2] and we compare
abundances of other molecules with respect to CH 3 OH using this
range of values. The hot core methanol column density of S68N
in van Gelder et al. (2020) is corrected for optical thickness with
CH [18] 3 [OH.]
Figure 13 compares the abundance ratios of various species
with respect to methanol for S68N. First, it shows that the relative abundances are remarkably similar on both sides of the outflow, well within the uncertainties. Second, most abundances relative to CH 3 OH are found to be comparable to the S68N hot core
within our uncertainties and those of van Gelder et al. (2020)
and Nazari et al. (2021), noting that due to lack of optically
thin CH 3 OH line detected in the outflow, our uncertainties are
larger. The greatest difference is seen for CH 3 CHO and H 2 CCO,
which could be attributed to the additional gas-phase formation
in shocks. While the difference is well beyond the conservative
uncertainties assumed here, this result should be confirmed with
a larger sample of sources with different properties. The jump in
CH 3 CHO abundance with respect to methanol in the outflow has
been also reported for two other sources - L1157 and IRAS4A
(De Simone et al. 2020b).
For the well-studied L1157 outflow, Codella et al. (2020) find
CH 3 CHO/CH 3 OH is 0.5%. which they find in agreement with
ratios in hot cores toward different protostars, but not including L1157 itself. In the case of S68N we uniquely show a comparison between the emission from molecules in the outflows
and hot core for the same source. While modeling by Codella
et al. (2020) shows that the similar spatial origin of CH 3 OH and
CH 3 CHO does not imply that they are both solely grain sput

1 http://cassis.irap.omp.eu/


Article number, page 17 of 38

_A&A proofs:_ manuscript no. main


Fig. 13: Ratio of complex organic molecules with respect to CH 3 OH in S68N. The ratios are shown for a 3 [′′] region in both redshifted
and blueshifted part of the outflow. The abundance ratios in the hot cores are taken from van Gelder et al. (2020) and Nazari et al.
(2021). The errorbars mark the lower and upper limit on the ratios, as calculated from the optically thick CH 3 OH emission (lower
limit) and [13] CH 3 OH (upper limit). All outflow abundances obtained from the Band 6 data at 0 [′′] . 45 resolution except for CH 3 OCHO
and CH 3 CN which were derived from Band 3 data at 3 [′′] .



tering products, an agreement between hot cores and outflows
could mean that similar processes are responsible for emission
in both regions.
It is interesting that the SMM3 outflow shows ice mantle
tracers in the outflow but not on the source. Thus, the lack of
hot core emission is likely due to the physical conditions in the
inner regions such as a large disk (Section 3.5) or continuum optical depth (De Simone et al. 2020a) and not to the lack of complex molecules on the grains. Since methanol is not detected,
we cannot provide abundance ratios for this outflow. B1-c - another source with an outflow containing ice mantle products, has
methanol lines overlapping with the high-velocity SO outflow,
therefore precise abundance measurements are not possible.
_JWST_ will be able to provide information on the ice content
due to rich absorption spectra in the mid-IR. The abundances of
COMs in the gas-phase provided by ALMA (van Gelder et al.
2020; Nazari et al. 2021) can then be directly compared with the
ice content. So far, the ice content observed on cloud scales with
_Spitzer_ does not show a correlation with the gas content but those
data do not probe thermally desorbed ices (Perotti et al. 2020).


_4.6._ _Carbon-chains and other hydrocarbons vs COMs_


Early observations at low spatial resolution suggested that large
carbon-chains such as C 5 H, HC 7 N, and HC 9 N and complex organic molecules are mutually exclusive, and therefore the two
were proposed to be tracers of two different categories of protostellar sources driven by different chemistry, namely warm
carbon-chain chemistry (WCCC) and hot core chemistry (Sakai
& Yamamoto 2013). Warm carbon-chain chemistry is thought to
occur above the sublimation temperature of CH 4 ∼ at 30 K. The
proposed difference then lies in the WCCC sources collapsing
more rapidly than the hot core sources, which prevents CO to
accumulate on the ices, leaving a higher CH 4 ice content. Thus,
in WCCC sources, there would be less CO to form more complex organic molecules such as CH 3 OH, and an underabundance
of COMs is indeed observed. This scenario has been supported
by the lower deuteration observed in WCCC sources (Sakai et al.


Article number, page 18 of 38



2009). With ALMA observations at higher resolution and sensitivity, sources harboring both COMs and small hydrocarbons,
c-C 3 H 2, and C 2 H, have now been observed (Imai et al. 2016;
Oya et al. 2017).


Fig. 14: Emission maps of an example COM and hydrocarbon
toward B1-c. _Left:_ CH 3 CHO moment 0 map, _Right:_ C 2 H moment 0 map; both integrated from -2 to 2 km s [−][1] w.r.t � sys .


Our data also show detection of small hydrocarbons and
COMs in the same sources (Fig. 14). However, our high resolution maps now show those hydrocarbons to originate in the
UV irradiated outflow cavity walls (Section 6). Both c-C 3 H 2 and
C 2 H can be solely explained by PDR chemistry (Guzmán et al.
2015; Cuadrado et al. 2015) even in moderate UV fields of lowmass protostars and therefore WCCC chemistry does not need to
be invoked for the sources presented in this work. The PDR origin is consistent with our observed geometry at the edges of the
cavities, where lower extinction allows the UV radiation from
the protostellar accretion to easily reach this region. It also explains the confinement of this emission to the inner 2000 au of
the envelope as the UV radiation decreases with distance from
the source. A deep search for larger hydrocarbons like HC 5 N in
cavity walls could help to understand their origin.

Tychoniec et al.: Which molecule traces what



_4.7._ _Class 0 vs Class I in different components_


Many processes take place within the protostellar lifetime of a
few 10 [5] yr that alter the chemical composition and physical conditions. First, the envelope is dissipating, and the radius where
key molecules are in the gas-phase is becoming smaller (Jørgensen et al. 2005b). With high-resolution studies, it is possible
to probe different snowlines in unprecedented detail now (van
’t Hoff et al. 2018a; Hsieh et al. 2019). There is a clear evolutionary trend observed in temperature – Class 0 disks are generally warmer than Class II disks, with Class I sources in between, which has major impact on the richness of their spectra
(van ’t Hoff et al. 2020a,b). This is also observed in our sample where all Class 0 show either complex organic molecules or
small molecules related to grain evaporation but no evidence of
those molecules is found in Class I sources (Section 4.4.1). Table 3 summarizes the evolution of the molecular composition of
protostellar systems.
Complex organic molecules are a key tracer of chemistry at
the early stages. We see them in the outflows only in Class 0
sources, likely due to the decrease of the outflow force and mass
and envelope density. In the inner regions, physical conditions
such as temperature and density also favour the early stages for
the abundances of COMs. In rare cases of rich chemistry in Class
I disks, it is usually attributed to accretion outbursts heating up
the disk (van ’t Hoff et al. 2018c; Lee et al. 2019a).
Molecular EHV jets are only present in the Class 0 phase
(Nisini et al. 2015). In our sample 6 out of 7 sources have highvelocity component and none is detected in Class I (Section
4.2.1), whereas the lower velocity outflows in these stages are
rich in ice mantle tracers (Section 4.2.3). The Class I jets are
invisible in molecular tracers, and their outflows show CO primarily, with much less contribution from shock tracers such as
SO and SiO (Section 4.2.2).
Cavity walls are seen prominently in the Class 0 sources in
molecules whose abundances are sensitive to UV radiation. In
Class I sources, a flared disk and weak outflow remain. While
there is less envelope to attenuate the UV radiation, there is
also less material to irradiate and accretion luminosity of older
sources decrease, which results in less prominent emission from
UV tracers on large scales in Class I (Section 4.3). Another example of a transition of molecular appearance between Class 0
and I is SO: this molecule traces the outflow in Class 0 and the
disk-envelope interface in Class I primarily.


**5.** **Conclusions**


In this work, we have presented an overview of the molecular
tracers of the physical components in protostellar Class 0 and
Class I systems. Table 2 and Fig. 11 present an overview of the
results, which are summarized below.


**–**
Protostellar envelopes are primarily traced with the dense gas
tracers such as C [18] O and CO, and snowline tracers such as
DCO [+], N 2 D [+], H [13] CO [+] . For this component, it is essential to
use observations that are sensitive to large scales of ∼ 5000

au.
**–** Protostellar outflows are separated into different components. High-velocity molecular jets are traced by O-bearing
molecules CO, SiO, SO, and H 2 CO. Entrained outflow material can be probed by low-velocity CO, SiO, SO, H 2 CO,
HCN as well as molecules released from ices by sputtering, such as CH 3 OH, CH 3 CHO, HNCO, CH 3 CN, and
CH 3 OCHO.



**–**
Outflow cavity walls are pronounced in UV irradiation tracers: C 2 H, c-C 3 H 2, and CN, and high-density tracers such as
13 CS.

**–** Hot cores, the inner warm envelopes, are probed predominantly by COMs and simple molecules released from ice
mantles and produced by high-temperature chemistry such
as SO, H 2 S, H 2 CS, OCS, H [13] CN, HCOOH, and HNCO.
**–** Embedded disks, which are most clearly seen in Class I
sources, can be seen in C [17] O and H 2 CO while CN traces
their upper layers. CO isotopologues can be used to probe
disks in Class 0 sources. However, the confusion with the
envelope emission requires a detailed analysis of the kinematics to confirm that a Keplerian disk is present.


Hydrocarbons and COMs are found to co-exist routinely in
protostellar sources: the former are present in the UV-irradiated
cavity walls and the latter in the hot core and in the outflows. It
is plausible that PDR chemistry for the formation of hydrocarbons is sufficient to explain the presence of molecules such as
C 2 H and c-C 3 H 2, and that no warm carbon-chain chemistry is
required, which relies on abundant CH 4 in ices. Observations of
more complex carbon chains in cavity walls and envelopes are
necessary to understand whether the WCCC plays a role there.
_JWST_ will be able to probe the CH 4 ice content at spatial scales
comparable to ALMA, which will show if there are any differences in the ice composition between sources.
Throughout this study, the availability of both low-lying
molecular lines to probe the cold extended envelope and outflow, as well as high-excitation lines to trace compact hot cores
has been a key for the analysis. The occurrence of the same
molecules in different physical components provides an opportunity to study the processes involved in their formation and excitation. For example, ice mantle tracers sputtered from the grains
in outflows give useful insight on the ice composition, whereas
comparison with abundances of thermally released COMs in the
inner region is a powerful tool to probe whether gas-phase formation routes contribute to complex molecules formation.
_JWST_ -MIRI will provide unprecedented resolution and sensitivity in mid-IR that will allow probing the emission from hot
gas in shocks as well as ice absorption features. _JWST_ observations can then be combined with our understanding of the kinematics and spatial origin of molecules revealed by ALMA.
_Acknowledgements._ The authors are grateful to the anonymous referee for comments that improved the quality of the
paper. This paper makes use of the following ALMA data:
ADS/JAO.ALMA# 2017.1.01174.S, ADS/JAO.ALMA#
2017.1.01350.S, ADS/JAO.ALMA# 2017.1.01371.S,
ADS/JAO.ALMA# 2017.1.01413.S, ADS/JAO.ALMA#
2013.1.00726.S, ADS/JAO.ALMA# 2016.1.00710.S. ALMA
is a partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC (Canada),
MOST and ASIAA (Taiwan), and KASI (Republic of Korea),
in co-operation with the Republic of Chile. The Joint ALMA
Observatory is operated by ESO, AUI/NRAO and NAOJ. Astrochemistry in Leiden is supported by the Netherlands Research
School for Astronomy (NOVA). Ł.T. acknowledges the ESO
Fellowship Programme. M.L.vG. acknowledges support from
the Dutch Research Council (NWO) with project number NWO
TOP-1 614.001.751. C.L.H.H. acknowledges the support of
the NAOJ Fellowship and JSPS KAKENHI grants 18K13586
and 20K14527. The National Radio Astronomy Observatory is
a facility of the National Science Foundation operated under
cooperative agreement by Associated Universities, Inc. This
research has made use of NASA’s Astrophysics Data System


Article number, page 19 of 38

_A&A proofs:_ manuscript no. main


Table 3: Summary of evolution of chemical tracers


Component Class 0 Class I
Envelope Cold, dense envelope results in cold tracers Envelope dissipates, extent of cold tracers is much
(DCO [+], N 2 H [+], N 2 D [+] ) smaller
Jet O-bearing molecules (CO, SiO, SO, H 2 CO) are Molecular jet disappears, seen only in atomic and
present in high-velocity bullets ionised gas
Outflow Ice sputtering (CH 3 OH, HNCO) and grain de- Decreased outflow mass and less dense envelope
struction (SO, SiO) tracers are present result in no tracers of sputtering and grain destruction, only faint CO remains
Cavity walls Prominent signs of UV-irradiated cavity walls No prominent signs of hydrocarbons in cavity
(CN, C 2 H, c-C 3 H 2 ) walls, CN still present
Hot core COMs and simple tracers of ice sublimation and Small extent plus disk shadowing results in less
high-temperature chemistry (H 2 S, OCS) complexity, except for outbursting sources
Disk Warm disk with COMs, dust obscuration Colder disk molecules, Keplerian rotation seen in
H 2 CO, C [18] O, CN in the disk surface.



Bibliographic Services. This research made use of NumPy
(Harris et al. 2020); Astroquery (Ginsburg et al. 2019); Astropy,
a community-developed core Python package for Astronomy
(Astropy Collaboration et al. 2018, 2013); Pandas (McKinney
2010, 2011); and Matplotlib (Hunter 2007).


**References**


Abergel, A., Teyssier, D., Bernard, J. P., et al. 2003, A&A, 410, 577
ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJ, 808, L3
Anderl, S., Maret, S., Cabrit, S., et al. 2016, A&A, 591, A3
André, P., Ward-Thompson, D., & Barsony, M. 1993, ApJ, 406, 122
Arce, H. G., Santiago-García, J., Jørgensen, J. K., Tafalla, M., & Bachiller, R.
2008, ApJ, 681, L21
Arce, H. G. & Sargent, A. I. 2006, ApJ, 646, 1070
Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A,
626, A71
Astropy Collaboration, Price-Whelan, A. M., Sip˝ocz, B. M., et al. 2018, AJ, 156,
123
Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558,
A33
Bachiller, R. & Gomez-Gonzalez, J. 1992, A&A Rev., 3, 257
Bacmann, A., Taquet, V., Faure, A., Kahane, C., & Ceccarelli, C. 2012, A&A,
541, L12
Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198
Benz, A. O., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 590, A105
Bergner, J. B., Öberg, K. I., Garrod, R. T., & Graninger, D. M. 2017, ApJ, 841,
120
Bergner, J. B., Öberg, K. I., Walker, S., et al. 2019, ApJ, 884, L36
Bianchi, E., Chandler, C. J., Ceccarelli, C., et al. 2020, MNRAS, 498, L87
Bjerkeli, P., van der Wiel, M. H. D., Harsono, D., Ramsey, J. P., & Jørgensen,
J. K. 2016, Nature, 540, 406
Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996, A&A, 311, 858
Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541
Bruderer, S., Benz, A. O., Bourke, T. L., & Doty, S. D. 2009, A&A, 503, L13
Buckle, J. V. & Fuller, G. A. 2002, A&A, 381, 77
Burkhardt, A. M., Dollhopf, N. M., Corby, J. F., et al. 2016, ApJ, 827, 21
Cabrit, S. & Bertout, C. 1992, A&A, 261, 274
Carney, M. T., Fedele, D., Hogerheijde, M. R., et al. 2018, A&A, 614, A106
Caselli, P. & Ceccarelli, C. 2012, A&A Rev., 20, 56
Caselli, P., Hartquist, T. W., & Havnes, O. 1997, A&A, 322, 296
Caselli, P., Keto, E., Bergin, E. A., et al. 2012, ApJ, 759, L37
Caselli, P., Walmsley, C. M., Tafalla, M., Dore, L., & Myers, P. C. 1999, ApJ,
523, L165
Cassen, P. & Moosman, A. 1981, Icarus, 48, 353
Ceccarelli, C., Caselli, P., Fontani, F., et al. 2017, ApJ, 850, 176
Chandler, C. J. & Carlstrom, J. E. 1996, ApJ, 466, 338
Chen, H., Myers, P. C., Ladd, E. F., & Wood, D. O. S. 1995, ApJ, 445, 377
Chen, X., Launhardt, R., & Henning, T. 2007, ApJ, 669, 1058
Codella, C., Bianchi, E., Tabone, B., et al. 2018, A&A, 617, A10
Codella, C., Ceccarelli, C., Bianchi, E., et al. 2020, A&A, 635, A17
Codella, C., Ceccarelli, C., Caselli, P., et al. 2017, A&A, 605, L3
Codella, C., Ceccarelli, C., Nisini, B., et al. 2010, A&A, 522, L1
Crapsi, A., van Dishoeck, E. F., Hogerheijde, M. R., Pontoppidan, K. M., &
Dullemond, C. P. 2008, A&A, 486, 245


Article number, page 20 of 38



Cuadrado, S., Goicoechea, J. R., Pilleri, P., et al. 2015, A&A, 575, A82
De Simone, M., Ceccarelli, C., Codella, C., et al. 2020a, ApJ, 896, L3
De Simone, M., Codella, C., Ceccarelli, C., et al. 2020b, A&A, 640, A75
Draine, B. T. 1978, ApJS, 36, 595
Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS,
476, 4949
Dutrey, A., Guilloteau, S., & Bachiller, R. 1997, A&A, 325, 758
Emprechtinger, M., Caselli, P., Volgenau, N. H., Stutzki, J., & Wiedner, M. C.
2009, A&A, 493, 89
Enoch, M. L., Evans, II, N. J., Sargent, A. I., & Glenn, J. 2009, ApJ, 692, 973
Evans, Neal J., I. 1999, ARA&A, 37, 311
Favre, C., Bergin, E. A., Cleeves, L. I., et al. 2015, ApJ, 802, L23
Flower, D. R. & Pineau des Forêts, G. 2013, MNRAS, 436, 2143
Frimann, S., Jørgensen, J. K., Dunham, M. M., et al. 2017, A&A, 602, A120
Fuente, A., Martin-Pintado, J., Cernicharo, J., & Bachiller, R. 1993, A&A, 276,
473
Garufi, A., Podio, L., Codella, C., et al. 2021, A&A, 645, A145
Geers, V. C., van Dishoeck, E. F., Pontoppidan, K. M., et al. 2009, A&A, 495,
837
Ginsburg, A., Sip˝ocz, B. M., Brasseur, C. E., et al. 2019, AJ, 157, 98
Glassgold, A. E., Mamon, G. A., & Huggins, P. J. 1991, ApJ, 373, 254
Greaves, J. S. & Rice, W. K. M. 2010, MNRAS, 407, 1981
Green, J. D., Evans, II, N. J., Jørgensen, J. K., et al. 2013, ApJ, 770, 123
Greene, T. P., Meyer, M. R., Ressler, M. E., Rieke, M. J., & Van Dishoeck, E. F.
GTO1186, Protostar (YSO) Spectroscopy, JWST Proposal. Cycle 1
Gueth, F. & Guilloteau, S. 1999, A&A, 343, 571
Gueth, F., Guilloteau, S., & Bachiller, R. 1996, A&A, 307, 891
Guilloteau, S., Bachiller, R., Fuente, A., & Lucas, R. 1992, A&A, 265, L49
Gusdorf, A., Cabrit, S., Flower, D. R., & Pineau des Forêts, G. 2008a, A&A,
482, 809
Gusdorf, A., Pineau des Forêts, G., Cabrit, S., & Flower, D. R. 2008b, A&A,
490, 695
Guzmán, V. V., Pety, J., Goicoechea, J. R., et al. 2015, ApJ, 800, L33
Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357
Harsono, D., Bjerkeli, P., Jorgensen, J., et al. GO2104, Mapping the hot gas
where an outflow is launched from a protoplanetary disk, JWST Proposal.
Cycle 1
Harsono, D., Bjerkeli, P., van der Wiel, M. H. D., et al. 2018, Nature Astronomy,
2, 646
Harsono, D., Bruderer, S., & van Dishoeck, E. F. 2015a, A&A, 582, A41
Harsono, D., Jørgensen, J. K., van Dishoeck, E. F., et al. 2014, A&A, 562, A77
Harsono, D., van der Wiel, M. H. D., Bjerkeli, P., et al. 2021, A&A, 646, A72
Harsono, D., van Dishoeck, E. F., Bruderer, S., Li, Z. Y., & Jørgensen, J. K.
2015b, A&A, 577, A22
Hartquist, T. W., Dalgarno, A., & Oppenheimer, M. 1980, ApJ, 236, 182
Herbst, E. & van Dishoeck, E. F. 2009, Annual Review of Astronomy and Astrophysics, 47, 427
Hernández-Gómez, A., Sahnoun, E., Caux, E., et al. 2018, Monthly Notices of
the Royal Astronomical Society, 483, 2014–2030
Hogerheijde, M. R., Jansen, D. J., & van Dishoeck, E. F. 1995, A&A, 294, 792
Hogerheijde, M. R., van Dishoeck, E. F., Blake, G. A., & van Langevelde, H. J.
1997, ApJ, 489, 293
Hogerheijde, M. R., van Dishoeck, E. F., Salverda, J. M., & Blake, G. A. 1999,
ApJ, 513, 350
Hollenbach, D. J. & Tielens, A. G. G. M. 1997, ARA&A, 35, 179
Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2019, ApJ, 884, 149
Hueso, R. & Guillot, T. 2005, A&A, 442, 703

Tychoniec et al.: Which molecule traces what



Hull, C. L. H., Girart, J. M., Kristensen, L. E., et al. 2016, ApJ, 823, L27
Hull, C. L. H., Girart, J. M., Tychoniec, Ł., et al. 2017, ApJ, 847, 92
Hunter, J. D. 2007, Computer Science and Engineering, 9, 90
Imai, M., Sakai, N., Oya, Y., et al. 2016, ApJ, 830, L37
Ivezic, Z. & Elitzur, M. 1997, MNRAS, 287, 799
Jansen, D. J., Spaans, M., Hogerheijde, M. R., & van Dishoeck, E. F. 1995, A&A,
303, 541
Jiménez-Serra, I., Caselli, P., Martín-Pintado, J., & Hartquist, T. W. 2008, A&A,
482, 549
Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2005a, ApJ, 632, 973
Jørgensen, J. K., Hogerheijde, M. R., Blake, G. A., et al. 2004, A&A, 415, 1021
Jørgensen, J. K., Johnstone, D., Kirk, H., & Myers, P. C. 2007, ApJ, 656, 293
Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2002, A&A, 389, 908
Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2004, A&A, 416, 603
Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2005b, A&A, 435, 177
Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595,
A117
Jørgensen, J. K., van Dishoeck, E. F., Visser, R., et al. 2009, A&A, 507, 861
Jørgensen, J. K., Visser, R., Sakai, N., et al. 2013, ApJ, 779, L22
Jørgensen, J. K., Visser, R., Williams, J. P., & Bergin, E. A. 2015, A&A, 579,
A23
Karska, A., Kaufman, M. J., Kristensen, L. E., et al. 2018, ApJS, 235, 30
Kristensen, L. E., van Dishoeck, E. F., Bergin, E. A., et al. 2012, A&A, 542, A8
Lada, C. J. 1987, in IAU Symposium, Vol. 115, Star Forming Regions, ed. M. Peimbert & J. Jugaku, 1–17
Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106
Lee, C.-F. 2020, A&A Rev., 28, 1
Lee, C.-F., Codella, C., Li, Z.-Y., & Liu, S.-Y. 2019a, ApJ, 876, 63
Lee, C.-F., Hirano, N., Zhang, Q., et al. 2014, ApJ, 786, 114
Lee, C.-F., Hirano, N., Zhang, Q., et al. 2015, The Astrophysical Journal, 805,
186
Lee, C.-F., Ho, P. T. P., Palau, A., et al. 2007, The Astrophysical Journal, 670,
1188
Lee, J.-E., Lee, S., Baek, G., et al. 2019b, Nature Astronomy, 3, 314
López-Sepulcre, A., Sakai, N., Neri, R., et al. 2017, A&A, 606, A121
Machida, M. N., Matsumoto, T., & Inutsuka, S.-i. 2016, MNRAS, 463, 4246
Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3
Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48
Marconi, A., Testi, L., Natta, A., & Walmsley, C. M. 1998, A&A, 330, 696
Maret, S., Maury, A. J., Belloche, A., et al. 2020, A&A, 635, A15
Mathews, G. S., Klaassen, P. D., Juhász, A., et al. 2013, A&A, 557, A132
Maury, A. J., André, P., Men’shchikov, A., Könyves, V., & Bontemps, S. 2011,
A&A, 535, A77
Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76
McClure, M. K. 2019, A&A, 632, A32
McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference,
Vol. 445, Austin, TX, 51–56
McKinney, W. 2011, Python for High Performance and Scientific Computing, 14
Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005,
ApJ, 634, 1126
Millar, T. J. & Williams, D. A. 1993, Dust and chemistry in astronomy (The
Graduate Series in Astronomy, Bristol: IOP Publishing)
Mottram, J. C., van Dishoeck, E. F., Kristensen, L. E., et al. 2017, A&A, 600,
A99
Murillo, N. M., Bruderer, S., van Dishoeck, E. F., et al. 2015, A&A, 579, A114
Murillo, N. M., Lai, S.-P., Bruderer, S., Harsono, D., & van Dishoeck, E. F. 2013,
A&A, 560, A103
Navarro-Almaida, D., Le Gal, R., Fuente, A., et al. 2020, A&A, 637, A39
Nazari, P., van Gelder, M. L., van Dishoeck, E. F., et al. 2021, A&A, 650, A150
Nisini, B., Santangelo, G., Giannini, T., et al. 2015, ApJ, 801, 121
Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504,
891
Offner, S. S. R. & Arce, H. G. 2014, ApJ, 784, 61
Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131
Oya, Y., Sakai, N., Watanabe, Y., et al. 2017, ApJ, 837, 174
Perotti, G., Rocha, W. R. M., Jørgensen, J. K., et al. 2020, A&A, 643, A48
Pety, J., Gratier, P., Guzmán, V., et al. 2012, A&A, 548, A68
Pety, J., Teyssier, D., Fossé, D., et al. 2005, A&A, 435, 885
Podio, L., Codella, C., Gueth, F., et al. 2015, A&A, 581, A85
Podio, L., Garufi, A., Codella, C., et al. 2020, A&A, 642, L7
Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45
Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128
Raga, A. C., Canto, J., Binette, L., & Calvet, N. 1990, ApJ, 364, 601
Raga, A. C., Williams, D. A., & Lim, A. J. 2005, Rev. Mexicana Astron. Astrofis., 41, 137
Ray, T. P., Beuther, H., Caratti o Garatti, A., et al. GTO1257, The Young Protostellar Outflow HH211, JWST Proposal. Cycle 1
Rodríguez-Fernández, N. J., Tafalla, M., Gueth, F., & Bachiller, R. 2010, A&A,
516, A98



Sakai, N., Ceccarelli, C., Bottinelli, S., Sakai, T., & Yamamoto, S. 2012, ApJ,
754, 70
Sakai, N., Oya, Y., Sakai, T., et al. 2014a, ApJ, 791, L38
Sakai, N., Sakai, T., Hirota, T., Burton, M., & Yamamoto, S. 2009, ApJ, 697, 769
Sakai, N., Sakai, T., Hirota, T., et al. 2014b, Nature, 507, 78
Sakai, N. & Yamamoto, S. 2013, Chemical Reviews, 113, 8981
Santiago-García, J., Tafalla, M., Johnstone, D., & Bachiller, R. 2009, A&A, 495,
169
Schilke, P., Walmsley, C. M., Pineau des Forêts, G., & Flower, D. R. 1997, A&A,
321, 293
Schilke, P., Walmsley, C. M., Pineau Des Forets, G., et al. 1992, A&A, 256, 595
Scibelli, S. & Shirley, Y. 2020, ApJ, 891, 73
Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228
Spaans, M., Hogerheijde, M. R., Mundy, L. G., & van Dishoeck, E. F. 1995, ApJ,
455, L167
Stephens, I. W., Dunham, M. M., Myers, P. C., et al. 2018, ApJS, 237, 22
Stone, J. M. & Norman, M. L. 1993, ApJ, 413, 210
Tabone, B., Godard, B., Pineau des Forêts, G., Cabrit, S., & van Dishoeck, E. F.
2020, A&A, 636, A60
Tafalla, M., Santiago-García, J., Hacar, A., & Bachiller, R. 2010, A&A, 522, A91
Taquet, V., Codella, C., De Simone, M., et al. 2020, A&A, 637, A63
Terebey, S., Shu, F. H., & Cassen, P. 1984, ApJ, 286, 529
Teyssier, D., Fossé, D., Gerin, M., et al. 2004, A&A, 417, 135
Tielens, A., McKee, C., Seab, C., & Hollenbach, D. 1994, The physics of graingrain collisions and gas-grain sputtering in interstellar shocks., 431: 321–340
Tobin, J., Calvet, N., Fischer, W. J., et al. GO1798, Characterizing Accretion Signatures in the Youngest Protostars: The Case of L1527 IRS, JWST Proposal.
Cycle 1
Tobin, J. J., Bergin, E. A., Hartmann, L., et al. 2013, ApJ, 765, 18
Tobin, J. J., Bourke, T. L., Mader, S., et al. 2019, ApJ, 870, 81
Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2011, ApJ, 740, 45
Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2012, Nature, 492, 83
Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2018, ApJ, 867, 43
Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130
Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101
Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19
Tychoniec, Ł., Tobin, J. J., Karska, A., et al. 2018, ApJS, 238, 19
Ulrich, R. K. 1976, ApJ, 210, 377
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck,
E. F. 2007, A&A, 468, 627
van der Wiel, M. H. D., van der Tak, F. F. S., Ossenkopf, V., et al. 2009, A&A,
498, 161
Van Dishoeck, E. F., Beuther, H., Boogert, A. C., et al. GO1960, The JWST
Protostellar Ice Legacy Survey, JWST Proposal. Cycle 1
Van Dishoeck, E. F., Beuther, H., Caratti o Garatti, A., et al. GTO1290, MIRI
EC Protostars Survey, JWST Proposal. Cycle 1
van Dishoeck, E. F. & Blake, G. A. 1998, ARA&A, 36, 317
van Gelder, M. L., Tabone, B., Tychoniec, Ł., et al. 2020, A&A, 639, A87
van Kempen, T. A., van Dishoeck, E. F., Güsten, R., et al. 2009a, A&A, 507,
1425
van Kempen, T. A., van Dishoeck, E. F., Salter, D. M., et al. 2009b, A&A, 498,
167
van ’t Hoff, M. L. R., Harsono, D., Tobin, J. J., et al. 2020a, ApJ, 901, 166
van ’t Hoff, M. L. R., Persson, M. V., Harsono, D., et al. 2018a, A&A, 613, A29
van ’t Hoff, M. L. R., Tobin, J. J., Harsono, D., & van Dishoeck, E. F. 2018b,
A&A, 615, A83
van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018c, ApJ, 864, L23
van ’t Hoff, M. L. R., van Dishoeck, E. F., Jørgensen, J. K., & Calcutt, H. 2020b,
A&A, 633, A7
Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75
Visser, R. & Dullemond, C. P. 2010, A&A, 519, A28
Walker-Smith, S. L., Richer, J. S., Buckle, J. V., Hatchell, J., & Drabek-Maunder,
E. 2014, MNRAS, 440, 3568
Walsh, C., Millar, T. J., & Nomura, H. 2010, ApJ, 722, 1607
Watanabe, N., Nagaoka, A., Shiraki, T., & Kouchi, A. 2004, ApJ, 616, 638
Williams, J. P. 2012, Meteoritics and Planetary Science, 47, 1915
Wilner, D. J., Myers, P. C., Mardones, D., & Tafalla, M. 2000, ApJ, 544, L69
Wootten, A. 1987, in IAU Symposium, Vol. 120, Astrochemistry, ed. M. S.
Vardya & S. P. Tarafdar, 311–319
Wright, G. S., Wright, D., Goodson, G. B., et al. 2015, PASP, 127, 595
Yang, Y.-L., Evans, Neal J., I., Smith, A., et al. 2020, ApJ, 891, 61
Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, arXiv e-prints, arXiv:2101.11009
Yen, H.-W., Koch, P. M., Takakuwa, S., et al. 2017, ApJ, 834, 178
Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1
Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2012, A&A, 542, A86
Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2015, A&A, 576,
A109
Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJ, 891, L17


Article number, page 21 of 38

_A&A proofs:_ manuscript no. main



**Appendix A:** **Tables**


Article number, page 22 of 38

Tychoniec et al.: Which molecule traces what



Article number, page 23 of 38

_A&A proofs:_ manuscript no. main



Article number, page 24 of 38

Tychoniec et al.: Which molecule traces what


**Appendix B:** **Continuum images**


Fig. B.1: Continuum emission from the sources in the sample.



Article number, page 25 of 38

_A&A proofs:_ manuscript no. main


**Appendix C:** **Envelope tracers**


Fig. C.1: Moment maps of C [18] O 2–1 ( _E_ up =16 K) at 6 [′′] resolution. Contours: continuum, color scale: C [18] O integrated from -2 to 2
km s [−][1] w.r.t � sys


Article number, page 26 of 38

Tychoniec et al.: Which molecule traces what


Fig. C.2: Moment maps of N 2 D [+] 3–2 ( _E_ up =22 K) at 6 [′′] resolution. Contours: continuum, color scale: moment 0 map integrated
from -2 to 2 km s [−][1] w.r.t � sys


Article number, page 27 of 38

_A&A proofs:_ manuscript no. main


Fig. C.3: Moment maps of DCO [+] 3–2 ( _E_ _up_ =21 K) at 6 [′′] resolution. Contours: continuum, color scale: moment 0 map integrated
from -2 to 2 km s [−][1] w.r.t � sys


Article number, page 28 of 38

Tychoniec et al.: Which molecule traces what


**Appendix D:** **Outflow**


Fig. D.1: Moment maps of low-velocity CO 2–1 ( _E_ up =17 K) outflow at 0 [′′] . 4 resolution. Contours: continuum, color scale: moment
0 map integrated from -10 to 10 km s [−][1] w.r.t � sys


Article number, page 29 of 38

_A&A proofs:_ manuscript no. main


Fig. D.2: Moment maps of low-velocity SiO 5–4 ( _E_ up =34 K) and 4–3 ( _E_ up =21 K) outflow at 0 [′′] . 4 resolution. Contours: continuum,
color scale: moment 0 map integrated from -15 to 15 km s [−][1] w.r.t � sys


Article number, page 30 of 38

Tychoniec et al.: Which molecule traces what


Fig. D.3: Moment maps of low-velocity SO 5 6 –4 5 ( _E_ up =35 K) and 6 7 –5 6 ( _E_ up =48 K) outflow at 0 [′′] . 4 resolution. Contours: continuum, color scale: moment 0 map integrated from -10 to 10 km s [−][1] w.r.t � sys


Fig. D.4: Moment maps of HCN 1–0 ( _E_ up =4 K) at 0 [′′] . 5 resolution. Color scale: moment 0 map integrated from -15 to 15 km s [−][1]
w.r.t � sys


Fig. D.5: Moment maps of H [13] CN 2–1 ( _E_ up =14 K) at 0 [′′] . 4 resolution. Contours: continuum, color scale: moment 0 map integrated
from -7 to 7 km s [−][1] w.r.t � sys


Article number, page 31 of 38

_A&A proofs:_ manuscript no. main


Fig. D.6: Additional plots of sputtering products for S68N. CH 3 CHO 14 0,14 –13 0,13 ( _E_ up = 96 K), H 2 CCO 13 1,13 –12 1,12 ( _E_ up =101 K)
which are separated by 4 km s [−][1], CH 3 OCHO 10 0,10 –9 0,9 ( _E_ up =30 K).


Fig. D.7: Moment 0 map in colourscale and 1.3 mm continuum in contours of SMM3. CO 2–1 ( _E_ up =17 K), H 2 CO 3 2,1 -2 2,0 _E_ up =
68 K and CH 3 OH 4 2 –5 1 _E_ up =60 K moment 0 maps obtained in Band 6 at 0 [′′] . 5 resolution. CH 3 CHO 6 1,6,1 –5 1,5,1 _E_ up =21 K, HNCO
5 0,5 –4 0,4 _E_ up =16 K, CH 3 CN 6 0 –5 0 _E_ up =19 K, and CH 3 OCHO 9 5,5 –8 5,4 _E_ up =43 K. Map of the sputtering products emission toward
SMM3 in Band 3 at 3 [′′] resolution. Moment 0 map integrated from -4 to 4 km s [−][1] w.r.t - � sys .


Article number, page 32 of 38

Tychoniec et al.: Which molecule traces what


Fig. D.8: Moment 0 map in colourscale and 1.3 mm continuum in contours of B1-c. CO 2–1 _E_ up =48 K, CH 3 OH 4 2 –5 1 E _up_ =60
K moment 0 maps obtained in Band 6 at 0 [′′] . 5 resolution. Sputtering products emission toward SMM3 in Band 3 at 3 [′′] resolution
CH 3 CHO 6 1,6,1 –5 1,5,1 E up =21 K, HNCO 5 0,5 –4 0,4 E up =16 K, and CH 3 CN 6 0 -5 0 E up =19 K and CH 3 OCHO 9 5,5 –8 5,4 E up =43 K.
Moment 0 map integrated from -10 to 10 km s [−][1] w.r.t � sys for SO and from -2 to 2 km s [−][1] w.r.t � sys for the other molecules.


Article number, page 33 of 38

_A&A proofs:_ manuscript no. main


**Appendix E:** **Cavity walls**


Fig. E.1: Maps of the outflow cavity wall tracers toward S68N, TMC1, and Emb8N with the CO low-velocity outflow map for
reference. _Top:_ Moment 0 maps toward S68N of CO, C 2 H, H [13] CO [+] obtained in Band 6 at 0 [′′] . 5 resolution and CN in Band 3 at 3 [′′] .
_Middle:_ Moment 0 maps toward TMC1 of CO, c-C 3 H 2 and [13] CS and CN obtained at 0 [′′] . 5. The emission is integrated from -5 to -1
km s [−][1] and from 1 to 5 km s [−][1] w.r.t � sys . _Bottom:_ Moment 0 maps toward Emb8N of CO, c-C 2 H, H [13] CO [+] [13] CS at 0 [′′] . 5 in Band 6.
and CN in Band 3 at 3 [′′] . The emission is integrated from -5 to 5 km s [−][1] w.r.t � sys .


Article number, page 34 of 38

Tychoniec et al.: Which molecule traces what


Fig. E.2: [13] CS 5–4 ( _E_ up =33 K) integrated from -5 to 5 km s [−][1] w.r.t � sys in Band 6 at 0 [′′] . 5.


Fig. E.3: c-C 3 H 2 7 2,6 –7 1,7 ( _E_ up =63 K) integrated from -1.5 to 1.5 km s [−][1] w.r.t � sys .


Article number, page 35 of 38

_A&A proofs:_ manuscript no. main


**Appendix F:** **Inner envelope**


Fig. F.1: CCS 19 18 –18 17 _E_ up =111 K, OCS 19–18 _E_ up =111 K, H 2 CO 9 1,8 –9 1,9 _E_ up =174 K, H 2 S 2 2 –2 1 _E_ up =83 K moment 0 maps
from ACA Band 6 observations and 6 [′′] resolution integrated from -2 to 2 km s [−][1] w.r.t � sys .


**Appendix G:** **Additional plots**


Article number, page 36 of 38

Tychoniec et al.: Which molecule traces what


Fig. F.2: O [13] CS 18–17 _E_ up =99 K integrated from -3 to 3 km s [−][1] w.r.t � sys .


Fig. G.1: Spectra of SO 6 7 –5 6 for S68N. Spectra averaged over the 0 [′′] . 6 diameter circle on positions: central source (black),
blueshifted outflow (blue). Both spectra normalized to the peak emission at the position


f


Article number, page 37 of 38

_A&A proofs:_ manuscript no. main


Fig. G.2: Map of the C [18] O emission toward SMM3. Moment 0 map in colourscale and 1.3 mm continuum in contours. _Left:_ Moment
0 map integrated from -3 to -0.5 km s [−][1] w.r.t � sys . _Right:_ Moment 0 map integrated from 0.5 to 3 km s [−][1] w.r.t � sys .


Article number, page 38 of 38


</paper>

## Items to check

```json
[
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "C18O",
  "failed_quote": "In Fig. 2 typical envelope tracers C [18] O 2–1 ( _E_ up = 16 K), DCO [+] 3–2 ( _E_ up = 21 K), and N 2 D [+] 3–2 ( _E_ up = 22 K), observed at 6 [′′] resolution with the ACA, are presented"
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "DCO+",
  "failed_quote": "In Fig. 2 typical envelope tracers C [18] O 2–1 ( _E_ up = 16 K), DCO [+] 3–2 ( _E_ up = 21 K), and N 2 D [+] 3–2 ( _E_ up = 22 K), observed at 6 [′′] resolution with the ACA, are presented"
 },
 {
  "path": "data.lines_targeted[2].evidence[0]",
  "value": "N2D+",
  "failed_quote": "In Fig. 2 typical envelope tracers C [18] O 2–1 ( _E_ up = 16 K), DCO [+] 3–2 ( _E_ up = 21 K), and N 2 D [+] 3–2 ( _E_ up = 22 K), observed at 6 [′′] resolution with the ACA, are presented"
 },
 {
  "path": "data.lines_targeted[37].evidence[0]",
  "value": "O13CS",
  "failed_quote": "O [13] CS 18–17 _E_ up =99 K integrated from -3 to 3 km s [−][1] w.r.t  sys ."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Integrate spectral line emission over specific velocity ranges relative to systemic velocity to produce moment 0 maps for envelope, jet, outflow, cavity wall, inner envelope, and disk tracers; extract spectra at selected positions.",
  "failed_quote": "All moment 0 maps are integrated from -2.5 to 2.5 km s [−][1] w.r.t  sys ."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "Velocity integration ranges: e.g., -2.5 to 2.5 km s^-1 (envelope), -70 to -40 and 40 to 70 km s^-1 (B1-c EHV jet), -10 to 10 km s^-1 (low-velocity outflow), -5 to -1 and 1 to 5 km s^-1 (cavity walls), -3 to 3 km s^-1 (hot core)",
  "failed_quote": "All moment 0 maps are integrated from -2.5 to 2.5 km s [−][1] w.r.t  sys ."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[1]",
  "value": "Velocity integration ranges: e.g., -2.5 to 2.5 km s^-1 (envelope), -70 to -40 and 40 to 70 km s^-1 (B1-c EHV jet), -10 to 10 km s^-1 (low-velocity outflow), -5 to -1 and 1 to 5 km s^-1 (cavity walls), -3 to 3 km s^-1 (hot core)",
  "failed_quote": "B1-c ntegrated from -70 to -40 and from 40 to 70 km s [−][1] w.r.t  sys"
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[2]",
  "value": "Velocity integration ranges: e.g., -2.5 to 2.5 km s^-1 (envelope), -70 to -40 and 40 to 70 km s^-1 (B1-c EHV jet), -10 to 10 km s^-1 (low-velocity outflow), -5 to -1 and 1 to 5 km s^-1 (cavity walls), -3 to 3 km s^-1 (hot core)",
  "failed_quote": "Moment 0 maps shown in colorscale integrated from -3 to 3 km s [−][1] w.r.t  sys ."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "H2CCO 13_1,13-12_1,12 and NH2CHO 12_2,10-12_2,10 in S68N are only 4 km s^-1 apart and possibly blended; more low-energy transitions are required to confirm line identification.",
  "failed_quote": "NH 2 CHO is more commonly observed in the shocked regions than H 2 CCO (Ceccarelli et al. 2017; Codella et al. 2017); it is possible that those lines are blended. More low-energy transitions would be required to confirm the identification of these lines."
 }
]
```
