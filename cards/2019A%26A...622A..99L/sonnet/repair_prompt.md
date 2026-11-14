# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...622A..99L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. louvet-ngc-2018 ⃝c ESO 2022
March 2, 2022

### **Lack of high-mass pre-stellar cores in the starless MDCs of** **NGC6334**


F. Louvet [1], S. Neupane [1], G. Garay [1], D. Russeil [2], A. Zavagno [2], A. Guzman [1], L. Gomez [4], L. Bronfman [1], and T. Nony [3]


1 Universidad de Chile, Camino el Observatorio 1515, Las Condes, Santiago de Chile e-mail: `flouvet@das.uchile.cl`
2 Aix Marseille Univ., CNRS, LAM, Laboratoire d’Astrophysique de Marseille, Marseille, France
3 Univ. Grenoble Alpes, CNRS, IPAG, F-38000 Grenoble, France
4 Joint ALMA Observatory, Alonso de Córdova 3107, Vitacura, Santiago, Chile


Received November 12, 2017; accepted December 1, 2017


**ABSTRACT**


_Context._ The formation of high-mass stars remains unknown in many aspects. Two families of models compete to explain the formation of high-mass stars. On the one hand, quasi-static models predict the existence of high-mass pre-stellar cores sustained by a
high degree of turbulence. On the other hand competitive accretion models predict that high-mass proto-stellar cores evolve from
low/intermediate mass proto-stellar cores in dynamic environments.
_Aims._ The aim of the present work is to bring observational constraints at the scale of high-mass cores (∼0.03 pc).
_Methods._ We targeted with ALMA and MOPRA a sample of 9 starless massive dense cores (MDCs) discovered in a recent Herschel/HOBYS study. Their mass and size (∼110 M ⊙ and _r_ =0.1 pc, respectively) are similar to the initial conditions used in the
quasi-static family of models explaining for the formation of high-mass stars. We present ALMA 1.4mm continuum observations that
resolve the Jeans length (λ Jeans ∼0.03 pc) and that are sensitive to the Jeans mass (M Jeans ∼0.65 M ⊙ ) in the 9 starless MDCs, together
with ALMA- [12] CO(2-1) emission line observations. We also present HCO [+] (1-0), H [13] CO [+] (1-0) and N 2 H [+] (1-0) molecular lines from
the MOPRA telescope for 8 of the 9 MDCs.
_Results._ The 9 starless MDCs have the mass reservoir to form high-mass stars according to the criteria by Baldeschi et al. (2017).
Three of the starless MDCs are subvirialized with α vir ∼0.35, and 4 MDCs show sign of collapse from their molecular emission
lines. ALMA observations show very little fragmentation within the MDCs. Only two of the starless MDCs host compact continuum
sources, whose fluxes correspond to < 3 M ⊙ fragments. Therefore the mass reservoir of the MDCs has not yet been accreted onto
compact objects, and most of the emission is filtered out by the interferometer.
_Conclusions._ These observations do not support the quasi-static models for high-mass star formation since no high-mass pre-stellar
core is found in NGC6334. The competitive accretion models, on the other hand, predict a level of fragmentation much higher than
what we observe.


**Key words.** Massive star - star formation - NGC6334



**1.** **Introduction**


Two main theoretical scenarios have been proposed to explain
the formation of high-mass stars: _(1)_ monolithic collapse of a
massive dense core (MDC, ∼100 M ⊙ for a radius of ∼0.1 pc)
supported by supersonic turbulent pressure (e.g., McKee & Tan
2002; Krumholz et al. 2007) or _(2)_ competitive accretion in a
proto-cluster environment through Bondi–Hoyle accretion (e.g.,
Bonnell et al. 2004; Bonnell & Bate 2006). These two scenarios
lead to distinct characteristics for the initial stages of high-mass
star formation. The first family of models suppose the existence
of starless MDCs that are supported by high-degrees of microturbulence (σ ∼1.7-2 km s [−][1], Krumholz et al. 2007). The MDCs
contract quasi-statically to become high-mass pre-stellar cores
(∼30 M ⊙ for a radius of ∼0.03 pc) before becoming proto-stellar
cores. Here, “core” names a gaseous structure of ∼0.03 pc (Bontemps et al. 2010; Zhang et al. 2014a; Palau et al. 2015) that will
collapse to form a single star or a small N-tuple binary system.
Hence, quasi-static models predict the existence of one, or a few,
high-mass pre-stellar cores in the starless MDCs.

In the second family of models, high-mass pre-stellar cores
never develop. The starless MDCs fragment into a cluster of lowmass cores with initial masses of the order of the Jeans mass.



The protostars inside these cores start accreting gas from their
envelope, unimpeded by the presence of other protostars. In a
second step, the gas is accreted from regions outside of their
envelopes and therefore from region that can contribute mass to
more than one protostar. This accretion accounts for the bulk of
the mass of the more massive stars. The latter form favourably at
the centre of the MDCs, where the gas density is the highest.


A few high-resolution studies have been performed with
(sub)millimeter interferometers with the aim of identifying prestellar cores and protostars within massive dense cores (MDCs,
see Rathborne et al. 2007; Swift 2009; Zhang et al. 2009; Busquet et al. 2010; Bontemps et al. 2010; Pillai et al. 2011; Wang
et al. 2011; Zhang & Wang 2011; Beuther et al. 2013; Lee et al.
2013; Tan et al. 2013; Wang et al. 2014; Louvet et al. 2014;
Cyganowski et al. 2014; Duarte-Cabral et al. 2014; Fontani et al.
2016; Kong et al. 2017; Palau et al. 2018; Nony et al. 2018).
These attempts revealed either that they were proto-stellar in nature when observed at high resolution (e.g. Duarte-Cabral et al.
2013), or filled with low-mass pre-stellar cores (e.g. Tan et al.
2013; Kong et al. 2017). In total, only five high-mass pre-stellar
core candidates have been reported:


Article number, page 1 of 12

_A&A proofs:_ manuscript no. louvet-ngc-2018




 - The pre-stellar candidate CygX-N53-MM2 (∼25 M ⊙ within
0.025 pc) of Duarte-Cabral et al. (2014); however, owing to
the confusion with the neighbour CygX-N53-MM1 it is hard
to exclude that CygX-N53-MM2 is driving outflows.

 - The pre-stellar candidate G11.92-0.61-MM2 (>30M ⊙ within
0.01 pc) of Cyganowski et al. (2014) but the lack of
(sub)millimeter molecular line emissions casts doubt about
its belonging to the Milky Way.

 - The pre-stellar candidate G11.11-P6-SMA1 (∼30 M ⊙ within
0.02 pc) of Wang et al. (2014). This source seems deprived
of outflows but a spectral survey of this target is necessary to
determine if it hosts a hot core.

 - The source G028CA9 (∼70 M ⊙ within 0.04 pc) of Kong et al.
(2017) but this source still lacks of shock tracer analysis to
address if it is driving outflows. Also, according to the authors, it shows complex kinematics potentially indicative of
two merging structures.

 - The source W43-MM1-#6 (∼55 M ⊙ within 1300 au) of Nony
et al. (2018). The target seems deprived of outflows and
its spectral survey did not reveal strong complex organic
molecule emissions. Nevertheless the study could not rule
out the existence of an unresolved outflow and/or a small
and embedded hot core.


Therefore although many regions have been studied very few
high-mass pre-stellar core candidates have been reported which
proves that, if they exist, they are very elusive. Here, we present
a study of 9 starless MDCs located in NGC6334.
NGC6334 is a giant molecular cloud complex (∼7×10 [5]
M ⊙, see e.g. Russeil et al. 2012) of the Milky Way. It belongs to the Sagittarius-Carina arm, lying at 1.75 kpc from
the sun (Matthews et al. 2008). It is a very active highmass star-forming region hosting more than 2000 young stellar objects identified with _Spitzer_ (Willis et al. 2013), numerous H ii regions, maser sources, and molecular outflows (see
Loughran et al. 1986; Persi & Tapia 2008; Carral et al. 2002).
As part of the _Herschel_ /HOBYS project, Tigé et al. (2017)
analyzed the properties of the MDCs forming in NCG6334,
based on _Herschel_ -PACS&SPIRE, JCMT-SCUBA2, APEXLABOCA, SEST-SIMBA, _Spitzer_ -IRAC&MIPS, _WISE_, and
_MSX_ data. Among other results, they found and characterized
16 candidate starless massive dense cores that remained undetected at 70 µm, have a mass >70 M ⊙, and a deconvolved radius
of ∼0.1 pc. Thirteen of these MDCs were observed with ALMA
(2015.1.00850.S, PI: Louvet, F.). In this article we present 9 of
these MDCs (see Table 1), as the other 4 contain protostars and
will be presented separately (Louvet et al., in prep). We complement our data-set with MOPRA observations to analyse the

∼
large-scale ( 0.1 pc) features of the MDCs. The article is organized such as Section 2 describes the observational data used in
the present work, Sects. 3.1-3.2 present the large-scale feature of
the MDCs at ∼0.1 pc scales, Sect. 3.3 presents the structure of
the MDCs down to ∼0.006 pc scales with ALMA. Section 4 discusses our results with respect to the numerical models of highmass star formation (4.1) and with respect to recent interferometric studies (4.2). Finally, Sect. 5 exposes our conclusions.


**2.** **Observations**


_2.1._ _ALMA observations_


ALMA observations were carried out in Cycle 3 in Band 6 using 39 antennas with baselines ranging from 15 m to 459 m, that
gives access to an angular resolution of ∼0.74 [′′] and a filtering


Article number, page 2 of 12



scale of 11.6 [′′] at 1.4 mm. In this article, we only present continuum emission observations and [12] CO(2-1) emission line observations. The continuum is obtained from a bandwidth spectral
window of 1.875 GHz centred at 214.5 GHz (or 1.40 mm) divided in 128 channels of 31.25 MHz each. The [12] CO(2-1) molecular line emission is obtained from a spectral windows centred
on the [12] CO(2-1) transition at 230.53 GHz with a high spectral
resolution of 0.485 MHz (or 0.63 km s [−][1] ). Each of our 9 sources
was observed for ∼1.4 min in total. The system temperature has
a mean value of 91 K. The data was pipeline-calibrated using
standard procedures of CASA 4.5.2. The continuum was imaged
concatenating together the 128 channels of the spectral window
dedicated to the continuum emission, which is a valid approach
for pre-stellar structures for which no complex organic molecule
emission lines are expected (Motte et al. 2018). The [12] CO(2-1)
emission line was slightly smoothed to a spectral resolution of
0.7 km s [−][1] . Both the continuum and [12] CO line emissions were
imaged with the _Clark_ method using the weighting _Briggs_ with
a robust parameter of 0.5 [1] . The mean achieved root mean square
(rms) noise level is of ∼0.34 mJy/beam in continuum and of 16.6
mJy/beam per channel in [12] CO(2-1), at a resolution of 0.7 km
s [−][1] . The Table 3 details the rms for each source.


_2.2._ _MOPRA observations_


These observations were performed in September 2008 with the
ATNF MOPRA 22-m telescope with the 3mm receiver and the
MOPRA spectrometer (MOPS) in the “zoom mode” that allows
to observe simultaneously up to 16 different frequencies, among
them the HCO [+] (1-0) at 89.18 GHz, the H [13] CO [+] (1-0) at 86.75
GHz, and the N 2 H [+] (1-0) at 93.17 GHz emission lines. Small
maps (between 3 [′] × 3 [′] to 5 [′] × 5 [′] ) were observed in the direction
of the 40 dense cores of Russeil et al. (2010). These maps cover 7
of our 9 MDCs. These maps were done in the OTF mode and the
data reduction was performed with Livedata and Gridzilla tools [2]
producing data-cubes with a spectral and spatial resolution of
0.11 km s [−][1] and 30 [′′] respectively. The MOPRA data-set is complemented with observations from the MALT90 survey (Jackson
et al. 2013) to cover one additional MDC. To sum up, we gather
a coherent sample of spectral lines from the MOPRA telescope
for all our 9 MDCs but the MDC #44.


**3.** **Analysis**


_3.1._ _Large-scale view of the MDCs_


Figure 1 shows the _Herschel_ -250 µm emission of NGC6334,
over-plotted with the positions of the 9 MDCs studied here.
Figures 2-3-4 show the column density map over each MDC
(left columns) and the molecular line emissions in the MDC
(right columns). All observed MDCs are detected in HCO [+] . Five
MDCs are detected in H [13] CO [+], and seven in N 2 H [+] (see Table 1). Only the MDC #11 was undetected in both N 2 H [+] and
H [13] CO [+] . We fitted the lines in _CLASS_ [3] using the _hfs_ procedure
to fit the multiplet N 2 H [+] molecular emission line and Gaussian
functions to fit the HCO [+] and H [13] CO [+] molecular line emissions
(see Table 1). We used the fit to the N 2 H [+] optically thin molecular line to determine the velocity dispersion in the MDCs as


1 Details on the method can be found in the CASA Task reference manual at the following location: https://casa.nrao.edu/docs/taskref/tcleantask.html
2 [see http://www.atnf.csiro.au/computing/software/index.html](http://www.atnf.csiro.au/computing/software/index.html)
3 see https://www.iram.fr/IRAMFR/GILDAS/doc/html/classhtml/class.html.

F. Louvet et al.: Lack of high-mass pre-stellar cores in the starless MDCs of NGC6334


Table 1: Physical parameters of the MDCs


MDC Radius Mass v N 2 H [+] σ N 2 H [+] v HCO [+] v H 13 CO + δV M _vir_ α vir M _thr_ M Jeans λ Jeans Bfield

                                                    -                                                    
[pc] [M ⊙ ] [km/s] [km/s] [km/s] [km/s] [M ⊙ ] [M ⊙ ] [M ⊙ ] [mpc] [mG]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14)
NGC6334-MDC#11 0.140 170 - - -1.8 - - - - 63.7 0.85 46 0.7

NGC6334-MDC#16 0.075 150 -4.0 1.00 -5.6 -3.7 -1.6 60 0.40 27.8 0.21 15 2.2

NGC6334-MDC#17 0.050 150 -7.3 1.72 -7.8 - -0.3 120 0.80 16.2 0.25 11 
NGC6334-MDC#21 0.135 130 -4.9 0.99 -4.6 -4.7 +0.3 107 0.80 85.7 1.31 55 
NGC6334-MDC#27 0.070 105 -5.4 0.77 -5.5 -5.4 -0.1 34 0.30 25.3 0.42 21 1.9

NGC6334-MDC#26 0.040 100 -5.3 1.60 -6.3 -4.8 -0.6 83 0.80 12.0 0.28 10 
NGC6334-MDC#35 0.105 90 -1.9 0.65 -2.0 - -0.2 36 0.35 43.4 0.93 42 0.7

NGC6334-MDC#44 0.150 77 - - - - - - - 69.8 1.15 68 
NGC6334-MDC#45 0.055 76 -8.9 1.12 -9.2 -8.9 -0.3 56 0.75 16.4 0.34 17 0.4

Mean 0.090 116 1.12 71 0.60 40.0 0.64 32 1.2


The MDCs appear either close to virial equilibrium (α _vir_ ∼0.8
for #17, #21, #26, and #45) or sub-virialized (α _vir_ ∼0.35 for #16,
#27, and #35). This indicates that they are not transient objects
and will most likely collapse and form stars.


_3.2._ _Infall motion in MDCs_



|I(N)<br>I<br>V|Col2|Col3|
|---|---|---|
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
|**I(N)**<br>**I**<br>**V**|**I(N)**<br>**I**<br>**V**||
||||


Fig. 1: _Herschel_ -SPIRE-250 µm emission of the NGC6334 region. The 9 MDCs of the present work are located by the blue
stars together with their number, following the nomenclature by
Tigé et al. (2017). Red arrows and Roman numerals (I, V) denote bright far-infrared sources from Kraemer & Jackson (1999).
Credits: ESA, _Herschel_ Science archive.



σ N 2 H [+] = [FWHM] [N] [2] [H] [+]



~~√~~



. We used these velocity dispersion esti8ln2



mates σ N 2 H [+] [4] to derive the virial mass for each MDC as:



5 − 2 _n_
_M_ vir = 3
� 3 − _n_



× _[R]_ [σ] [N] [2] [H] [+] (1)
� _G_



where _R_ is the radius of the MDC, _G_ the gravitational constant, and _n_ is the index of the density profile ρ( _R_ ) ∝ _R_ [−] _[n]_ . Garay
et al. (2007) and Mueller et al. (2002) find, on average, a radial
profile index of 1.8 for massive dense cores. We use this value
of _n_ = 1.8 to derive the virial mass of our MDCs.
We compute the virial parameter α _vir_ = _M_ _vir_ / _M_ _MDC_, where
_M_ _MDC_ is the mass of the MDC, as reported by Tigé et al. (2017).


4 Rigorously, the virial mass should be computed from an average
molecule of weight µ _m_ _p_ where µ = 2.8 (Kauffmann et al. 2008) and _m_ _p_
is the mass of a proton. Considering the N 2 H [+] as the molecule used to



, which
�



The majority of the MDCs show a blue-shifted central velocity
of the optically thick HCO [+] emission line with respect to the optically thin H [13] CO [+] and/or N 2 H [+] emission lines (see Table 1).
Following Mardones et al. (1997), we quantify the asymmetry
parameter δV = (V _thick_ -V _thin_ )/σV _thin_ to measure line asymmetry, where V _thick_ is the peak velocity of the optically thick line,
V _thin_ is the peak velocity of the optically thin line and σV _thin_ is
the line width of the optically thin line. A negative δV value is
indicative of infall, and a positive value of δV is indicative of
expansion motions. The typical error in line asymmetry parameter is of 0.25, which is dominated by the error in determination
of velocity of optically thick line. We report one positive value
of δV (#MDC 21) and 6 negative values of δV. The sources #16,
#17, #26 and #45 further have |δV| values above the typical error,
which strongly indicate infall motions in these MDCs.
Myers et al. (1996) presented a simple model of contracting
cloud, and showed that low-velocity contracting cloud display
optically thick emission lines with double-peak spectra where
the blue-shifted peaks appear stronger than the red-shifted peaks.
At higher infall velocities the red-shifted peak of the optically
thick emission lines disappear, displaying instead a shoulder-like
profile. The four MDCs that have a significant negative δV value
display such profiles. Figure 5 presents the optically thick HCO [+]
emission line superposed with the optically thin H [13] CO [+] emission line (N 2 H [+] for #17) towards these 4 MDCs. In addition to
the blue-shift of the optically thick line with respect to the optically thin line, the optically thick HCO [+] emission lines display
a shoulder-like profile towards the MDCs #17 and #26, and a
higher blue-peak with self absorption dips in the MDCs #16,
and #45. Therefore, from the values of the δV parameters together with the profile of their optically thick lines, we conclude
that these four MDCs are undergoing infalling motions.


_3.3._ _ALMA view of the massive dense cores_


Figures 6-7-8 present ALMA continuum 1.4mm emission maps
toward the 9 starless MDCs. The emission is completely resolved out in the MDCs #11, #17, #21, #27, #35, and #44, indicating that they are emitting at a scale near or larger than
our filtering scale of 11.6 [′′] (or ∼0.1 pc at the adopted distance


Article number, page 3 of 12



1
� 2.8 [−] 29 [1]



measure the dispersion, it gives σ =



�



σ N 2 H + + _[k T]_ _m_ _p_



differs by less than 5% with the value of σ N 2 H + .

_A&A proofs:_ manuscript no. louvet-ngc-2018


Fig. 2: **Left:** _Herschel_ /column density maps toward the 9 MDCs studied here. The black ellipse indicates the position and size of the
MDC as extracted by Tigé et al. (2017), and the magenta circle shows the beam of the MOPRA telescope. **Right:** HCO [+] (1–0) and
H [13] CO [+] (1–0) (or N 2 H [+], see the label in the panels) emission lines toward the MDCs as seen with MOPRA. The lines are adjusted
by a Gaussian (or with the _hfs_ procedure in CLASS to fit the multiplet of the N 2 H [+] ) whose results are presented in Table 1. The
frame on the bottom displays the residuals of the HCO [+] (1-0) emission after subtraction of the Gaussian feature shown on the top
frame.



of NGC6334). On the contrary, the maps toward the MDCs
#16, #26, and #45 display some structure. To extract the compact sources within the fields we used the source extraction tool
_Getsources_ (Men’shchikov et al. 2012). Developed for multiwavelength _Herschel_ images, it calculates the local noise and
local background to properly extract compact sources from a
complex cloud environment (see e.g. Louvet et al. 2014). In total we find 8 cores located in the vicinity of the MDCs #16, #26
and #45. In these three fields, we superposed contours showing
the column density emission derived from the _Herschel_ observations (respectively the JCMT/SCUBA-2/450µm emission for the


Article number, page 4 of 12



MDC#26). In the pointing toward the MDC #16, two fragments
are within the area corresponding to 90% of the column density
peak emission of the MDC. Therefore, these two fragments are
likely forming from the mass reservoir of the MDC#16. In a similar way, one fragment observed with ALMA seems associated
with the MDC#26. On the other hand, the 5 remaining fragments
are offset from the MDC locations, and generally associated with
proto-stellar objects previously identified by Tigé et al. (2017).
The integrated flux of these cores varies between 1 mJy and 15

F. Louvet et al.: Lack of high-mass pre-stellar cores in the starless MDCs of NGC6334


Fig. 3: Same as Figure 2, for the MDCs #16, #17, and #26.



mJy. To derive the corresponding mass, we used the following
expression:


_S_ [int]
_M_ = 1.4mm [×] _[ d]_ [2] (2)

κ 1.4 _mm_ × _B_ 1.4 _mm_


with _d_ = 1.75 kpc, and _B_ 1.4mm the Planck function at the
temperature _T_ dust given in Table 3. The dust mass opacity was
taken to be equal to κ 1.4 _mm_ = 9.9 × 10 [−][3] _cm_ [2] _g_ [−][1], following the
κ ν = 0.1 _cm_ [2] _g_ [−][1] × (ν/1000 _GHz_ ) [β] equation including a gas to
dust ratio of 100 and an opacity index β = 1.5, which is typical
of dense and cool media (Ossenkopf & Henning 1994). The mass
of the cores ranges between 0.2 M ⊙ and 2.6 M ⊙ for a mean size
of ∼0.008 pc. Compared with the mass of the MDCs (∼110 M ⊙ )
it is clear that most of the emission is resolved out even in these



MDCs where substructure is found. The parameters of each lowmass core are reported in Table 2.
The blue and red contours on Figs. 6-7-8 show the blueshifted and red-shifted integrated emissions of the [12] CO(2-1),
highlighting the presence of outflows. The three compact sources
#16-alma1, #16-alma2, #26-alma38 are deprived of outflows and
are therefore pre-stellar core candidates. We report the detection of a bipolar outflow associated with the proto-stellar object
#45-alma1. We also report two [12] CO blue-shifted blobs, plus one
12 CO red-shifted blob in the MDC #11; and one elongated 12 CO
red-shifted emission in the MDC #35. These [12] CO emissions
are not associated with any compact continuum sources, down
to our detection limit of 0.11 M ⊙ corresponding to a 5σ level.
The interpretation of these features goes beyond the scope of the
present paper and will require the addition of complementary
data, e.g. from ACA, to recover the intermediate scale emission.


Article number, page 5 of 12

_A&A proofs:_ manuscript no. louvet-ngc-2018

## **Not observed**


Fig. 4: Same as Figure 2, for the MDCs #35, #44, and #45.



**4.** **Discussion**


_4.1._ _Comparison with models_


Baldeschi et al. (2017) find an empirical high-mass star formation threshold, based on studies of environment with and without high-mass star formation. They suggest that cloud structures
with masses larger than the mass _m_ _threshold_ = 1280 M ⊙ ( _r_ / _pc_ ) [1][.][42],
where _r_ is the source radius, form high-mass stars or will form
high-mass stars in the near future. Applying this relationship to
our ∼0.1 pc MDCs, we find that all have masses above the mass
threshold for high-mass star formation (see Table 1-column 11).

Our 9 MDCs have a mean mass of ∼115 M ⊙ and a mean
radius of 0.1 pc. These conditions are very similar with the initial conditions of the quasi-static models for high-mass star formation (100-200 M ⊙ and radius of 0.1 pc, see e.g. McKee &


Article number, page 6 of 12



Tan 2002; Krumholz et al. 2007). Three of the starless MDCs
are clearly subvirialized with α _vir_ ∼0.35, and three additional
MDCs display evidence of infall from their large-scale molecular line emissions, in contrast with the virial equilibrium assumption used in these models. In the framework of quasi-static
models, where the MDCs ( _r_ ∼0.1 pc) slowly contract down to
the physical scale at which individual (or low N-tuple system)
star formation takes place (∼0.03 pc, see e.g. Bontemps et al.
2010; Zhang et al. 2014b; Palau et al. 2015), one expects to observe high-mass pre-stellar cores. Nevertheless, the ALMA observations toward NGC6334 showed that the few cores that were
detected are low-mass cores (maximum mass of 2.6 M ⊙ ), and
hence they do not have the mass reservoir to form a high-mass

star.
On the other hand the competitive accretion models (e.g.
Bonnell et al. 2004) posits that an MDC of mass _M_ MDC will frag

F. Louvet et al.: Lack of high-mass pre-stellar cores in the starless MDCs of NGC6334


Fig. 5: Line profiles of the optically thick HCO [+] (1-0) emission lines and of the optically thin H [13] CO [+] – respectively N 2 H [+] (1-0) –
emission lines towards the MDCs #16, #17, #26 and #45. The red dotted vertical line shows the velocity of the source determined
from the optically thin line.


Table 2: Physical parameters of the fragments


Source _[a]_ RA DEC Integrated Size Mass _[b]_

[J2000] [J2000] Flux [mJy] [”x”] M ⊙
MDC#16-alma1 17:19:05.25 -36:07:50.48 14.2±0.1 0.8×0.8 2.63±0.02

MDC#16-alma2 17:19:06.11 -36:08:02.44 1.0±0.1 0.8×0.8 0.17±0.02

MDC#26-alma3 17:20:54.66 -35:45:51:44 7.1±0.6 0.8×0.8 0.45±0.04

MDC#26-alma4 17:20:55.68 -35:45:50.72 8.8±0.5 0.9×0.8 0.56±0.03

MDC#26-alma35 17:20:54.93 -35:45:46.8 7.0±0.9 1.2×0.8 0.44±0.05

MDC#26-alma38 17:20:55.21 -35:46:16:07 14.4±0.7 1.6×1.1 0.91±0.04

MDC#45-alma1 17:17:48.59 -36:09:11.45 15.0±0.4 0.8×0.8 1.53±0.04

MDC#45-alma2 17:17:48.66 -36:09:34.63 4.9±0.2 0.8×0.8 0.50±0.02

Mean 9.0±0.4 1.0×0.8 0.90±0.03
( _[a]_ ): The label of the source is defined as the name of the nearest MDC, plus the _Getsources_ extraction number. ( _[b]_ ): The method to
derive the mass follows eq. 2.



ment into _n_ cores where each core will have a mass close to the
_M_ MDC
thermal Jeans mass ( _M_ Jeans ), and _n_ ≃ . From the
2.5 × _M_ Jeans

local cloud density and kinetic temperature computed for each
MDCs (see Table 1 and Tigé et al. 2017), we can calculate the
Jeans mass and Jeans scale (λ Jeans ) as:



σ [3]
th

_M_ Jeans = [π] [5][/][2], λ Jeans = σ th

6 ~~�~~ G [3] ρ



π
(3)
~~�~~ Gρ



the competitive accretion models would have resulted in ∼120
cores of ∼0.3 M ⊙ in mass, whilst we found only a single core
of ∼0.9 M ⊙ in mass. In the remaining 7 MDCs no core is found
associated with the starless MDCs. Therefore the observations
of starless MDCs in NGC6334 do not match the predictions of
competitive accretion models, unless the MDCs are in such early
stage of evolution that the initial fragmentation has not yet taken
place. Most of the mass in the starless MDCs is likely organized
in extended and homogeneous cloud structures (∼ [>] 0.1 pc) that
were filtered by the interferometer. A similar result was reported
by Dunham et al. (2016) who reported that low-mass pre-stellar
cores resembling Bonnort-Ebert spheres would be filtered out
by the interferometers. Combination with short-spacing observations is therefore mandatory to investigate the exact cloud structure of starless MDCs.


It is not clear what prevents the MDCs from fragmenting
into low-mass cores. According to Krumholz & McKee (2008)
the heat produced by accreting low-mass stars in regions with
surface density of at least 1 g cm [−][2] can halt fragmentation of
the MDCs. It could be the case in MDCs #11 and #35 if the
12 CO(2-1) blobs (see Sect. 3.3) were interpreted as monopolar
outflows. The combination of the heat due to the accretion on
the low-mass protostars with the injection of turbulence by the
outflows could prevent the fragmentation in the MDCs. But the
lack of fragmentation is also observed in the MDCs where no
sign of proto-stellar activity is present (MDCs #16-17-21-26-2744-45, see Figs. 6-7-8). Consequently further processes must be
considered.


Article number, page 7 of 12



where G is the gravitational constant, and ρ is the gas density (given in Table 3-column 6). σ th is the thermal broadening of the emission line given by σ _th_ = ~~�~~ _k_ _B_ × _T_ /(µ × _m_ _p_ ),
where _k_ _B_ is the Boltzman constant, µ = 2.8 the mean molecular weight (Kauffmann et al. 2008), _m_ _p_ the mass of a proton,
and _T_ is the temperature of the MDC. We obtained a mean
Jeans mass <M _Jeans_ >=0.65 M ⊙ and a mean Jeans length of
< λ _Jeans_ >=0.03 pc. Our ALMA data probe angular scales down
to 0.74 [′′] (∼0.006 pc at the distance of NGC6334), and have a
mass equivalent 5σ detection threshold of 0.11 M ⊙, hence we are
fully sensitive to the Jeans mass and Jeans scale. Therefore if a
cluster of low-mass cores were forming in our MDCs we should
have detected it. In the case of the MDC #16 where we found
cores associated with the mass reservoir of the MDC, a fragmentation such as predicted by the competitive accretion models would have resulted in ∼280 cores of ∼0.2 M ⊙ in mass. In
contrast we only found two cores of masses of 0.2 M ⊙ and 2.6
M ⊙, respectively. In the MDC #26 a fragmentation such as in

_A&A proofs:_ manuscript no. louvet-ngc-2018


Fig. 6: ALMA 1.4 mm continuum emission toward the 9 MDCs. The blue ellipses show the MDCs as defined by Tigé et al. (2017).
The compact sources extracted by _Getsources_ in the MDCs #16, #26, and #45 (see text and Table 2 for details) are indicated with
small black ellipses and red labels. The blue contours and red contours highlight the ALMA [12] CO(2–1) integrated emission in
the blue-shifted and red-shifted channels, respectively. The contours start at 3σ with a 3σ step in each panel. The values for the
integration in velocities and the resulting rms is given in the Table 4. In the bottom right panel (MDC #16) the black contours show
the column density emission derived from _Hershel_ observations (Tigé et al. 2017). The contours range from 50% to 90% by step of
10% of the peak flux in the MDC #16 (blue ellipse). They show that the continuum sources ALMA#1 and #2 are associated with
the MDC #16.



Numerical models of a protoclusters where a significant
magnetic field is considered show a smaller fragmentation level
than models with weak magnetic support (e.g., Commerçon et al.
2011, see also the theoretical approach by Shu et al. 1987).
Therefore, the magnetic field could play the dual role of _(i)_ limiting the fragmentation of MDCs and _(ii)_ sustaining the MDCs
against collapse together with the turbulence. Following this
hypothesis, we derive the magnetic field strength necessary to
prevent the MDCs from collapsing given their measured turbulence support. The magnetic field strength is computed as
_B_ = σ _A_ × ~~[√]~~ µ 0 ρ, where ρ is the mean density in the MDCs (see
Table 3), µ 0 is the vacuum permeability and σ _A_ is the Alfvén ve

Article number, page 8 of 12



locity such as M vir,B = M MDC = 3 _G_ _[R]_ � 53−−2 _nn_ ��σ [2] + [1] 6 [σ] [2] _A_ �, where the

parameters are the same as for eq 1. The value of the magnetic
field necessary to sustain the MDCs against collapse is given in
Table 1. The mean value of ∼1.2 mG that we obtain is of the
order of the magnetic field strength measured in high-mass star

∼
formation ( 0.1-10 mG, see Motte et al. 2017). It is very likely
that the magnetic field plays a central role in our MDCs. This is
particularly true toward the MDC #27, and #35 where the virial
parameter α vir < 0.4 whereas no infall motion are traced by the
molecular line emissions. This discrepancy is better explained if
magnetic fields are taken into account.



locity such as M vir,B = M MDC = 3 _[R]_



_G_ _[R]_ � 53−−2 _nn_ ��σ [2] + [1] 6

F. Louvet et al.: Lack of high-mass pre-stellar cores in the starless MDCs of NGC6334


Fig. 7: Following of Figure 6. In the bottom left panel the black contours show the JCMT/SCUBA-2/450 µm emission presented in
Tigé et al. (2017). The contours range from 20% to 90% of the peak flux inside the MDC #26 (defined by the blue ellipse) by step
of 10%. They show that the continuum source ALMA#38 is associated with the MDC #26, while the continuum sources ALMA#3,
#4, and #35 belong to another structure.



_4.2._ _Comparison with previous observational studies_


Recently, a handset of large-sample observational studies have
targeted high-mass star-forming regions with interferometers
(Sanhueza et al. 2017; Kong et al. 2017; Csengeri et al. 2017).
First, it is important to note that none of these observations found
a thermal Jeans fragmentation and none could claim the discovery of a high-mass pre-stellar core – in a similar way as the
present study. Interestingly, these studies found different values in term of fragmentation level and/or on the masses of the
cores. Here, it is primordial to remember that these studies probe
different physical scales, with different filtering scales. For instance, Csengeri et al. (2017) report ALMA 7m array observations that probe scales from ∼0.3 pc down to ∼0.06 pc in 35
IR Quiet clumps selected from the ATLASGAL survey Schuller
et al. (2009). At these scales they find that the clumps fragment



on average in 3 MDCs of typically 60 M ⊙, similar to the sample we scrutinized here with ALMA, down to scales of ∼0.006
pc. Csengeri et al. (2017) report that they were able to recover
between 16% and 47% of the large scale fluxes of the clumps
measured by the ATLASGAL survey at a similar wavelength of
870 µm. It is consistent with our observations that report higher
filtering when probing the MDCs at higher angular resolution.


Also we stress that all these studies were conducted in different regions, hence scrutinizing different stages of the high-mass
starless phase. Looking in details at these studies, they actually
seem to fall well onto the empirical sequence proposed by Motte
et al. (2017). Following this sequence, _(i)_ a starless MDC (∼100
M ⊙ within 0.1 pc) would fragment into a few pre-stellar objects
of low/intermediate masses, as we observed here in the MDCs
#16 and #26. This type of fragmentation was also observed by
Kong et al. (2017): they surveyed 32 high-mass surface density


Article number, page 9 of 12

_A&A proofs:_ manuscript no. louvet-ngc-2018


**5.** **Conclusions**


We presented 1.4 mm continuum and [12] CO(2–1) ALMA observations of 9 starless massive dense cores (MDCs) located in
NGC 6334 ( _d_ ∼1.75 kpc) that have a mean mass of 115 M ⊙ and a
radius of ∼0.1 pc. Our ALMA observations probe spatial scales
from ∼0.1 pc down to 0.006 pc, resolving the thermal Jeans
length in these 9 MDCs (< λ Jeans >= 0.03 pc). Our ALMA
observations are also sensitive to the thermal Jeans mass in the
MDCs (< _M_ Jeans >=0.65 M ⊙ ), with a mass equivalent 5σ level
of ∼0.1 M ⊙ . We complemented the ALMA data-set with archive
HCO [+] (1–0), H [13] CO [+] (1–0), and N 2 H [+] (1–0) MOPRA observations toward 8 of the 9 MDCs to examine the gas dynamic at the
MDCs’ scale. Our main results can be summarized as follows:



Fig. 8: Following of Figure 7. The black contours show the column density emission derived from _Hershel_ observations (Tigé
et al. 2017). The contours range from 30% to 90% of the peak
flux in the MDC #45 (blue ellipse) by step of 10% . They show
that the continuum sources ALMA#1 and #2 are not associated

with the MDC #45.


regions in which they detected in total 141 cores, stating that
many of the weakest sources are likely to be noise fluctuation.
They give the characteristics of the 50 more reliable extractions
and present in details the 6 most massive. The 6 most massive
have a mean mass of 3.8 M ⊙ if we don’t consider the most
massive (C9A, see below). Therefore, all the 141 cores of Kong
et al. (2017) but C9A are low or intermediate mass cores. The
most massive C9A core has a mass of ∼70 M ⊙ under their assumptions, and of ∼20 M ⊙ using our mean temperature of 15.5
K and our dust emissivity assumption. Also, it could be constituted of two lower mass cores, and, its evolutionary status is
unknown. _(ii)_ Then, in the sequence of Motte et al. (2017) the
global collapse of the MDC will generate gas flows streams that
will increase the mass of the pre-stellar objects - a process even
more efficient as the pre-stellar objects are located near the gravitational potential of the MDC. This step is well supported by
the observations by Sanhueza et al. (2017). They observe a candidate starless clump (1500 M ⊙ within 0.6 pc) that fragments
into 5 candidate pre-stellar cores with masses ranging from 8.4
M ⊙ to 15 M ⊙ within ∼0.05 pc. It is also supported by the present
study since the two MDCs #16 and #26, that harbour substructure, are collapsing (see Sect. 3.2). _(iii)_ During the accretion process the low/intermediate mass pre-stellar cores eventually start
proto-stellar activities, which would explain why some IR Quiet
MDCs host low/intermediate protostars (Louvet et al. in prep).
_(iv)_ Finally, the low/intermediate protostars eventually become
massive (∼25 M ⊙ within 0.03 pc) and form high-mass stars.


To strengthen this view of high-mass star formation, future studies should target early-type proto-stellar MDCs (∼100
M ⊙ within ∼0.1 pc) to determine the mean mass at which 0.03
pc cores turn proto-stellar.


Article number, page 10 of 12




 - The 9 starless MDCs of our sample have the potential to form
a high mass star according to the mass threshold criteria presented by Baldeschi et al. (2017).

 - Three MDCs are subvirialized with α vir ∼ 0.35 and four
MDCs are roughly virialized with α vir ∼ 0.8. One among
the former and three among the later MDCs further show
an asymmetry of their optically thick HCO [+] molecular line
emissions and blue-shifted emission lines with respect to the
optically thin H [13] CO [+] emission lines, indicative of collapse.

 - ALMA observations show that very few 0.005 pc cores are
forming in starless MDCs. In total, three cores are detected:
two in the MDC #16 with masses of ∼0.2 M ⊙ and 2.6 M ⊙ respectively, and one in the MDC #26 with a mass of 0.9 M ⊙ .
These three cores are deprived of outflows making them candidate pre-stellar cores. These low-mass dense cores do not
have the gas reservoir to form a high-mass star. Therefore
most of the gas must be organized into extended and homogeneous structures near or above our filtering scale (∼ [>] 0.1 pc).

 - These ALMA observations do not support the turbulent-core
models of high-mass star formation since we do not observe
high-mass pre-stellar cores (expected to have ∼25 M ⊙ within

∼
0.03 pc).

 - These ALMA observations do not reproduce the predictions
of the competitive accretion models in term of initial fragmentation of the MDCs. We detected only a few fragments
in our sample, two orders of magnitude below the predicted
fragmentation level. Our observations are therefore incompatible with these models unless the initial fragmentation has
not yet taken place.

 - Present ALMA observations of the starless MDCs of
NGC6334 are consistent with the empirical model by Motte
et al. (2017) in which the first stage of the high-mass star formation scenario is the formation of a few low/intermediate
mass pre-stellar cores within the MDCs, that will grow in
mass by accreting gas from the diffuse gas reservoir of the
MDC.


_Acknowledgements._ The authors thank the anonymous referee for a thorough
report which led to a significant improvement of this paper. FL acknowledges
the help of Arnaud Belloche in the interpretation of optically thick HCO [+] emission lines. FL thanks Timea Csengeri for useful discussions about the main results of the article. FL acknowledges the support of the Fondecyt program n [o]
3170360. FL acknowledges the support of the Programme National de Physique
Stellaire and Physique et Chimie du Milieu Interstellaire of CNRS/INSU (with
INC/INP/IN2P3), co-funded by CEA and CNES. G.G. and L.B. acknowledges
support by CONICYT project Basal AFB-170002. This paper makes use of the
following ALMA data: ADS/JAO.ALMA#2015.1.00850.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan),
together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

F. Louvet et al.: Lack of high-mass pre-stellar cores in the starless MDCs of NGC6334


**References**


Baldeschi, A., Elia, D., Molinari, S., et al. 2017, MNRAS, 466, 3682
Beuther, H., Linz, H., Tackenberg, J., et al. 2013, A&A, 553, A115
Bonnell, I. A. & Bate, M. R. 2006, MNRAS, 370, 488
Bonnell, I. A., Vine, S. G., & Bate, M. R. 2004, MNRAS, 349, 735
Bontemps, S., Motte, F., Csengeri, T., & Schneider, N. 2010, A&A, 524, A18
Busquet, G., Palau, A., Estalella, R., et al. 2010, A&A, 517, L6
Carral, P., Kurtz, S. E., Rodríguez, L. F., et al. 2002, AJ, 123, 2574
Commerçon, B., Hennebelle, P., & Henning, T. 2011, ApJ, 742, L9
Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 600, L10
Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2014, ApJ, 796, L2
Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014, A&A, 570, A1
Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2013, A&A, 558, A125
Dunham, M. M., Offner, S. S. R., Pineda, J. E., et al. 2016, ApJ, 823, 160
Fontani, F., Commerçon, B., Giannetti, A., et al. 2016, A&A, 593, L14
Garay, G., Mardones, D., Brooks, K. J., Videla, L., & Contreras, Y. 2007, ApJ,
666, 309
Jackson, J. M., Rathborne, J. M., Foster, J. B., et al. 2013, PASA, 30, e057
Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, II, N. J., & Lee, C. W. 2008,
A&A, 487, 993
Kong, S., Tan, J. C., Caselli, P., et al. 2017, ApJ, 834, 193
Kraemer, K. E. & Jackson, J. M. 1999, ApJS, 124, 439
Krumholz, M. R., Klein, R. I., & McKee, C. F. 2007, ApJ, 656, 959
Krumholz, M. R. & McKee, C. F. 2008, Nature, 451, 1082
Lee, K., Looney, L. W., Schnee, S., & Li, Z.-Y. 2013, ApJ, 772, 100
Loughran, L., McBreen, B., Fazio, G. G., et al. 1986, ApJ, 303, 629
Louvet, F., Motte, F., Hennebelle, P., et al. 2014, A&A, 570, A15
Mardones, D., Myers, P. C., Tafalla, M., et al. 1997, ApJ, 489, 719
Matthews, H. E., McCutcheon, W. H., Kirk, H., White, G. J., & Cohen, M. 2008,
AJ, 136, 2083
McKee, C. F. & Tan, J. C. 2002, Nature, 416, 59
Men’shchikov, A., André, P., Didelon, P., et al. 2012, A&A, 542, A81
Motte, F., Bontemps, S., & Louvet, F. 2017, ArXiv e-prints, number 1706.00118
Motte, F., Nony, T., Louvet, F., et al. 2018, ArXiv e-prints, number 1804.02392
Mueller, K. E., Shirley, Y. L., Evans, II, N. J., & Jacobson, H. R. 2002, ApJS,
143, 469
Myers, P. C., Mardones, D., Tafalla, M., Williams, J. P., & Wilner, D. J. 1996,
ApJ, 465, L133
Nony, T., Louvet, F., Motte, F., et al. 2018, A&A, 618, L5
Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943
Palau, A., Ballesteros-Paredes, J., Vázquez-Semadeni, E., et al. 2015, MNRAS,
453, 3785
Palau, A., Zapata, L. A., Román-Zúñiga, C. G., et al. 2018, ApJ, 855, 24
Persi, P. & Tapia, M. 2008, Star Formation in NGC 6334, ed. B. Reipurth, 456
Pillai, T., Kauffmann, J., Wyrowski, F., et al. 2011, A&A, 530, A118
Rathborne, J. M., Simon, R., & Jackson, J. M. 2007, ApJ, 662, 1082
Russeil, D., Zavagno, A., Adami, C., et al. 2012, A&A, 538, A142
Russeil, D., Zavagno, A., Motte, F., et al. 2010, A&A, 515, A55
Sanhueza, P., Jackson, J. M., Zhang, Q., et al. 2017, ApJ, 841, 97
Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415
Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23
Swift, J. J. 2009, ApJ, 705, 1456
Tan, J. C., Kong, S., Butler, M. J., Caselli, P., & Fontani, F. 2013, ApJ, 779, 96
Tigé, J., Motte, F., Russeil, D., et al. 2017, A&A, 602, A77
Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS
Wang, K., Zhang, Q., Wu, Y., & Zhang, H. 2011, ApJ, 735, 64
Willis, S., Marengo, M., Allen, L., et al. 2013, ApJ, 778, 96
Zhang, B., Moscadelli, L., Sato, M., et al. 2014a, ApJ, 781, 89
Zhang, Q., Qiu, K., Girart, J. M., et al. 2014b, ApJ, 792, 116
Zhang, Q. & Wang, K. 2011, ApJ, 733, 26
Zhang, Q., Wang, Y., Pillai, T., & Rathborne, J. 2009, ApJ, 696, 268


**6.** **Appendix**


Article number, page 11 of 12

_A&A proofs:_ manuscript no. louvet-ngc-2018


Table 3: Additional parameters of the MDCs


Data-set from Tigé et al. (2017) ALMA-cycle 3 observations
Source _[a]_ RA DEC L _[a]_ _bol_ M/L < _n_ H 2 - _[a]_ T _[a]_ σ _[b]_ 12 _CO_ σ _cont_ Mass Sensitivity

[J2000] [J2000] [L ⊙ ] [M ⊙ /L ⊙ ] [cm [−][3] ] [K] [mJy/Beam] [µJy/Beam] at 5σ _[c]_

NGC6334-MDC#11 17:20:02.16 -36:12:14.5 110 1.55 2.4×10 [5] 14.1 15.8 273 0.11 M ⊙
NGC6334-MDC#16 17:19:05.24 -36:07:57.8 11 13.64 1.6×10 [6] 9.9 15.8 263 0.19 M ⊙
NGC6334-MDC#17 17:19:51.86 -35:57:07.7 230 0.65 4.8×10 [6] 16.5 16.8 310 0.10 M ⊙
NGC6334-MDC#21 17:20:30.91 -36:00:54.8 390 0.33 2.2×10 [5] 18.3 16.9 283 0.06 M ⊙
NGC6334-MDC#27 17:19:39.66 -35:56:52.0 120 0.88 1.3×10 [6] 15.6 16.4 292 0.07 M ⊙
NGC6334-MDC#26 17:20:55.36 -35:46:05.7 740 0.14 7.5×10 [6] 21.1 17.6 656 0.16 M ⊙
NGC6334-MDC#35 17:19:58.00 -36:13:13.5 140 0.64 3.4×10 [5] 16.4 17.2 318 0.11 M ⊙
NGC6334-MDC#44 17:22:25.58 -35:16:59.9 27 2.85 1.0×10 [5] 12.8 16.5 281 0.08 M ⊙
NGC6334-MDC#45 17:17:47.95 -36:09:28.5 60 1.27 2.0×10 [6] 14.7 16.5 352 0.14 M ⊙
mean - - 203 2.44 2.0×10 [6] 15.5 16.6 336 0.11 M ⊙
**(a)** : The sources name, radius, bolometric luminosity, and density follow the work by Tigé et al. (2017). **(b)** : The 1σ rms noise level
is given per channel, where the channel width is of 0.7 km s [−][1] . **(c)** : The method to estimate the mass from the 5σ value follows the
equation (2).


Table 4: Integration parameters of the CO line in the MDCs

|MDC|Blue-shifted 12CO(2 –1) emission Red -shifted 12CO(2 –1) emission|Col3|
|---|---|---|
||Velocity range<br>1σ value<br>[km/s]<br>mJy/beam.km s−1|Velocity range<br>1σ value<br>[km/s]<br>mJy/beam.km s−1|
|NGC6334-MDC#11<br>NGC6334-MDC#16<br>NGC6334-MDC#17<br>NGC6334-MDC#21<br>NGC6334-MDC#27<br>NGC6334-MDC#26<br>NGC6334-MDC#35<br>NGC6334-MDC#44<br>NGC6334-MDC#45|[-19.4 ; -7.9 ]<br>11.1<br>[-8.5 ; -5.5 ]<br>11.9<br>[-13.3 ; -8.9 ]<br>20.1<br>[-12.6 ; -9.7 ]<br>4.5<br>[-18.6 ; -9.3 ]<br>8.2<br>[-30.1 ; -20.5 ]<br>7.8<br>[-9.8 ; -4.5 ]<br>7.4<br>[-16.5 ; -7.5 ]<br>6.3<br>[-23.3; -17.0]<br>9.6|[0.0 ; 3.1 ]<br>6.2<br>[1.0 ; 6.1 ]<br>7.3<br>[-0.1 ; 5.7 ]<br>5.7<br>[10.9 ; 14.2 ]<br>7.9<br>[-2.2 ; 6.4 ]<br>9.3<br>[-7.9 ; -5.3 ]<br>15.9<br>[1.8 ; 5.4 ]<br>4.8<br>[1.5 ; 10.7 ]<br>6.6<br>[0.5; 13.3]<br>9.9|



Article number, page 12 of 12


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Gaussian fits to HCO+ and H13CO+, hfs fit for N2H+ in CLASS",
  "failed_quote": "We fitted the lines in CLASS using the hfs procedure to fit the multiplet N 2 H [+] molecular emission line and Gaussian functions"
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "B = σ_A sqrt(μ0 ρ) with σ_A from M_vir,B = M_MDC",
  "failed_quote": "The magnetic field strength is computed as B = σ A × µ 0 ρ"
 }
]
```
