# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...647A..10G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. aa_sulfur_bar_accepted ©ESO 2021
February 12, 2021

## **Bottlenecks to interstellar sulfur chemistry**

### **Sulfur-bearing hydrides in UV-illuminated gas and grains**


J. R. Goicoechea [1], A. Aguado [2], S. Cuadrado [1], O. Roncero [1], J. Pety [3], E. Bron [4],
A. Fuente [5], D. Riquelme [6], E. Chapillon [3][,][ 7], C. Herrera [3], and C. A. Duran [6][,][ 8]


1 Instituto de Física Fundamental (CSIC). Calle Serrano 121-123, 28006, Madrid, Spain. e-mail: `javier.r.goicoechea@csic.es`
2 Facultad de Ciencias. Universidad Autónoma de Madrid, 28049 Madrid, Spain.
3 Institut de Radioastronomie Millimétrique (IRAM), Grenoble, France.
4 LERMA, Observatoire de Paris, PSL Research University, CNRS, Sorbonne Universités, 92190 Meudon, France.
5 Observatorio Astronómico Nacional (OAN), Alfonso XII, 3, 28014 Madrid, Spain.
6 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany.
7 OASU/LAB-UMR5804, CNRS, Université Bordeaux, 33615 Pessac, France.
8 European Southern Observatory, Alonso de Cordova 3107, Vitacura, Santiago, Chile.


Received 25 October 2020 / Accepted 23 December 2020


**ABSTRACT**


Hydride molecules lie at the base of interstellar chemistry, but the synthesis of sulfuretted hydrides is poorly understood and their
abundances often crudely constrained. Motivated by new observations of the Orion Bar photodissociation region (PDR) – 1 [′′] resolution
ALMA images of SH [+] ; IRAM 30m detections of bright H [32] 2 [S,] [H] [34] 2 [S,] [and] [H] [33] 2 [S] [lines;] [H] [3] [S] [+] [(upper] [limits);] [and] [SOFIA][/][GREAT]
observations of SH (upper limits) – we perform a systematic study of the chemistry of sulfur-bearing hydrides. We self-consistently
determine their column densities using coupled excitation, radiative transfer as well as chemical formation and destruction models.
We revise some of the key gas-phase reactions that lead to their chemical synthesis. This includes _ab initio_ quantum calculations of
the vibrational-state-dependent reactions SH [+] + H 2 ( _v_ ) ⇄ H 2 S [+] + H and S + H 2 ( _v_ ) ⇄ SH + H . We find that reactions of UV-pumped
H 2 ( v ≥ 2) molecules with S [+] ions explain the presence of SH [+] in a high thermal-pressure gas component, _P_ th / _k_ ≈ 10 [8] cm [−][3] K, close to
the H 2 dissociation front (at _A_ _V_ < 2 mag ). These PDR layers are characterized by no or very little depletion of elemental sulfur from
the gas. However, subsequent hydrogen abstraction reactions of SH [+], H 2 S [+], and S atoms with vibrationally excited H 2, fail to form
enough H 2 S [+], H 3 S [+], and SH to ultimately explain the observed H 2 S column density ( ∼ 2.5 × 10 [14] cm [−][2], with an ortho-to-para ratio of
2.9 ± 0.3; consistent with the high-temperature statistical value). To overcome these bottlenecks, we build PDR models that include a
simple network of grain surface reactions leading to the formation of solid H 2 S (s-H 2 S) . The higher adsorption binding energies of S
and SH suggested by recent studies imply that S atoms adsorb on grains (and form s-H 2 S ) at warmer dust temperatures ( _T_ _d_ < 50 K ) and
closer to the UV-illuminated edges of molecular clouds. We show that everywhere s-H 2 S mantles form(ed), gas-phase H 2 S emission
lines will be detectable. Photodesorption and, to a lesser extent, chemical desorption, produce roughly the same H 2 S column density
(a few 10 [14] cm [−][2] ) and abundance peak (a few 10 [−][8] ) nearly independently of _n_ H and _G_ 0 . This agrees with the observed H 2 S column
density in the Orion Bar as well as at the edges of dark clouds without invoking substantial depletion of elemental sulfur abundances.


**Key words.** Astrochemistry — line: identification — ISM: clouds — (ISM:) photon-dominated region (PDR) — ISM: clouds



**1.** **Introduction**


Hydride molecules play a pivotal role in interstellar chemistry
(e.g., Gerin et al. 2016), being among the first molecules to
form in diffuse interstellar clouds and at the UV-illuminated
edges of dense star-forming clouds, so-called photodissociation
regions (PDRs; Hollenbach & Tielens 1997). Sulfur is on the
top ten list of most abundant cosmic elements and it is particularly relevant for astrochemistry and star-formation studies.
Its low ionization potential (10.4 eV) makes the photoionization
of S atoms a dominant source of electrons in molecular gas at
intermediate visual extinctions _A_ _V_ ≃ 2 - 4 mag (Sternberg & Dalgarno 1995; Goicoechea et al. 2009; Fuente et al. 2016).


The sulfur abundance, [S/H], in diffuse clouds (e.g., Howk
et al. 2006) is very close to the [S/H] measured in the solar
photosphere ([S/H] ⊙ ≃ 1.4×10 [−][5] ; Asplund et al. 2009) . Still, the
observed abundances of S-bearing molecules in diffuse and
translucent molecular clouds ( _n_ H ≃ 10 [2] − 10 [3] cm [−][3] ) make up a



very small fraction, < 1 %, of the sulfur nuclei (mostly locked
as S [+] ; Tieftrunk et al. 1994; Turner 1996; Lucas & Liszt 2002;
Neufeld et al. 2015). In colder dark clouds and dense cores
shielded from stellar UV radiation, most sulfur is expected in
molecular form. However, the result of adding the abundances
of all detected gas-phase S-bearing molecules is typically a
factor of ∼10 [2] -10 [3] lower than [S/H] ⊙ (e.g., Fuente et al. 2019) .
Hence, it is historically assumed that sulfur species deplete
on grain mantles at cold temperatures and high densities (e.g.,
Graedel et al. 1982; Millar & Herbst 1990; Agúndez & Wakelam 2013). However, recent chemical models predict that the
major sulfur reservoir in dark clouds can be either gas-phase
neutral S atoms (Vidal et al. 2017; Navarro-Almaida et al. 2020)
or organo-sulfur species trapped on grains (Laas & Caselli 2019) .
Unfortunately, it is difficult to overcome this dichotomy from an
observational perspective. In particular, no ice carrier of an abundant sulfur reservoir other than solid OCS (hereafter s-OCS, with
an abundance of ∼ 10 [−][8] with respect to H nuclei; Palumbo et al.


Article number, page 1 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted



1997) has been convincingly identified. Considering the large
abundances of water ice ( s-H 2 O ) grain mantles in dense molecular clouds and cold protostellar envelopes (see reviews by van
Dishoeck 2004; Gibb et al. 2004; Dartois 2005), one may also expect hydrogen sulfide ( s-H 2 S ) to be the dominant sulfur reservoir.
Indeed, s-H 2 S is the most abundant S-bearing ice in comets such
as 67P/Churyumov–Gerasimenko (Calmonte et al. 2016). However, only upper limits to the s-H 2 S abundance of ≲ 1 % relative to
water ice have so far been estimated toward a few interstellar sightlines (e.g., Smith 1991; Jiménez-Escobar & Muñoz Caro 2011) .
These values imply a maximum s-H 2 S ice abundance of
several 10 [−][6] with respect to H nuclei. Still, this upper limit could
be higher if s-H 2 S ices are well mixed with s-H 2 O and s-CO ices
(Brittain et al. 2020).
The bright rims of molecular clouds illuminated by nearby
massive stars are intermediate environments between diffuse and
cold dark clouds. Such environments host the transition from
ionized S [+] to neutral atomic S, as well as the gradual formation
of S-bearing molecules (Sternberg & Dalgarno 1995). In one
prototypical low-illumination PDR, the edge of the Horsehead
nebula, Goicoechea et al. (2006) inferred very modest gas-phase
sulfur depletions. In addition, the detection of narrow sulfur radio
recombination lines in dark clouds (implying the presence of S [+] ;
Pankonin & Walmsley 1978) is an argument against large sulfur
depletions in the mildly illuminated surfaces of these clouds.
The presence of new S-bearing molecules such as S 2 H, the first
(and so far only) doubly sulfuretted species detected in a PDR
(Fuente et al. 2017), suggests that the chemical pathways leading
to the synthesis of sulfuretted species are not well constrained;
and that the list of S-bearing molecules is likely not complete.
Interstellar sulfur chemistry is unusual compared to that
of other elements in that none of the simplest species,
X=S, S [+], SH, SH [+], or H 2 S [+], react exothermically with H 2 (v = 0)
in the initiation reactions X + H 2 → XH + H (so-called hydrogen
abstraction reactions). Hence, one would expect a slow sulfur chemistry and very low abundances of SH [+] (sulfanylium)
and SH (mercapto) radicals in cold interstellar gas. However,
H 2 S (Lucas & Liszt 2002), SH [+] (Menten et al. 2011; Godard
et al. 2012), and SH (Neufeld et al. 2012, 2015) have been detected in low-density diffuse clouds ( _n_ H ≲ 100 cm [−][3] ) through
absorption measurements of their ground-state rotational lines [1] .
In UV-illuminated gas, most sulfur atoms are ionized, but the
very high endothermicity of reaction


S [+] ( [4] _S_ ) + H 2 ( [1] Σ [+], ν = 0) ⇄ SH [+] ( [3] Σ [−] ) + H ( [2] _S_ ) (1)


( _E_ / _k_ = 9860 K, e.g., Zanchet et al. 2013a, 2019) prevents
this reaction from being efficient unless the gas is heated
to very high temperatures. In diffuse molecular clouds
(on average at _T_ k ∼ 100 K), the formation of SH [+] and SH only
seems possible in the context of local regions of overheated gas
subjected to magnetized shocks (Pineau des Forets et al. 1986) or
in dissipative vortices of the interstellar turbulent cascade (Godard
et al. 2012, 2014). In these tiny pockets ( ∼ 100 AU in size), the
gas would attain the hot temperatures ( _T_ k ≃ 1000 K) and/or ionneutral drift needed to overcome the endothermicities of the above
hydrogen abstraction reactions (see, e.g., Neufeld et al. 2015).
Dense PDRs ( _n_ H ≃ 10 [3] − 10 [6] cm [−][3] ) offer a complementary
environment to study the first steps of sulfur chemistry. Because
of their higher densities and more quiescent gas, fast shocks or
turbulence dissipation do not contribute to the gas heating. Instead, the molecular gas is heated to _T_ k ≲ 500 K by mechanisms


1 SH was first reported by IR spectroscopy toward the cirumstellar
envelope around the evolved star R Andromedae (Yamamura et al. 2000).


Article number, page 2 of 25



that depend on the flux of far-UV photons (FUV; _E_ < 13.6 eV).
A different perspective of the H 2 (v) reactivity emerges because
certain endoergic reactions become exoergic and fast when a
significant fraction of the H 2 reagents are radiatively pumped to
vibrationally excited states v ≥ 1 (Stecher & Williams 1972; Freeman & Williams 1982; Tielens & Hollenbach 1985; Sternberg
& Dalgarno 1995). In this case, state-specific reaction rates for
H 2 (ν, _J_ ) are needed to make realistic predictions of the abundance
of the product XH (Agúndez et al. 2010; Zanchet et al. 2013b;
Faure et al. 2017). The presence of abundant FUV-pumped
H 2 (v ≥ 1) triggers a nonthermal “hot” chemistry. Indeed, CH [+]
and SH [+] emission lines have been detected in the Orion Bar PDR
(Nagy et al. 2013; Goicoechea et al. 2017) where H 2 lines up to
v = 10 have been detected as well (Kaplan et al. 2017).
In this study we present a systematic (observational and
modeling) study of the chemistry of S-bearing hydrides in
FUV-illuminated gas. We try to answer the question of whether
gas-phase reactions of S atoms and SH [+] molecules with vibrationally excited H 2 can ultimately explain the presence of abundant H 2 S, or if grain surface chemistry has to be invoked.
The paper is organized as follows. In Sects. 2 and 3 we report
on new observations of H [32]
2 [S, H] [34] 2 [S, H] [33] 2 [S, SH] [+] [, SH, and H] [3] [S] [+]
emission lines toward the Orion Bar. In Sect. 4 we study their
excitation and derive their column densities. In Sect. 6 we discuss
their abundances in the context of updated PDR models, with
emphasis on the role of hydrogen abstraction reactions


SH [+] ( [3] Σ [−] ) + H 2 ( [1] Σ [+] ) ⇄ H 2 S [+] ( [2] A [′] ) + H ( [2] _S_ ), (2)


H 2 S [+] ( [2] _A_ [′] ) + H 2 ( [1] Σ [+] ) ⇄ H 3 S [+] (X [1] _A_ 1 ) + H ( [2] _S_ ), (3)


S ( _[3]_ _P_ ) + H 2 ( [1] Σ [+] ) ⇄ SH (X [2] Π) + H ( _[2]_ _S_ ), (4)


photoreactions, and grain surface chemistry. In Sect. 5 we summarize the _ab initio_ quantum calculations we carried out to determine the state-dependent rates of reactions (2) and (4). Details of
these calculations are given in Appendices A and B.


**2.** **Observations of S-bearing hydrides**


_2.1._ _The Orion Bar_


At an adopted distance of ∼ 414 pc, the Orion Bar is an interface
of the Orion molecular cloud and the Huygens H ii region that
surrounds the Trapezium cluster (Genzel & Stutzki 1989; O’Dell
2001; Bally 2008; Goicoechea et al. 2019, 2020; Pabst et al. 2019,
2020). The Orion Bar is a prototypical strongly illuminated dense
PDR. The impinging flux of stellar FUV photons ( _G_ 0 ) is a few
10 [4] times the mean interstellar radiation field (Habing 1968). The
Bar is seen nearly edge-on with respect to the FUV illuminating
sources, mainly θ [1] Ori C, the most massive star in the Trapezium.
This favorable orientation allows observers to spatially resolve the
H [+] -to-H transition (the ionization front or IF; see, e.g., Walmsley
et al. 2000; Pellegrini et al. 2009) from the H-to-H 2 transition
(the dissociation front or DF; see, e.g., Allers et al. 2005; van
der Werf et al. 1996, 2013; Wyrowski et al. 1997; Cuadrado et al.
2019). It also allows one to study the stratification of different
molecular species as a function of cloud depth (i.e., as the flux
of FUV photons is attenuated; see, e.g., Tielens et al. 1993; van
der Wiel et al. 2009; Habart et al. 2010; Goicoechea et al. 2016;
Parikka et al. 2017; Andree-Labsch et al. 2017).

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry

|U V radiation AL M DF AF o V|Col2|
|---|---|
|**ALMA FoV**<br>**DF**<br>**UV radiation**||
|**ALMA FoV**<br>**DF**<br>**UV radiation**||
|**ALMA FoV**<br>**DF**<br>**UV radiation**||



**Fig. 1.** Overview of the Orion Bar. The (0 [′′], 0 [′′] ) position corresponds to α 2000 = 05 [h] 35 [m] 20.1 [s] ; δ 2000 = − 05 [◦] 25 [′] 07.0 [′′] . _Left panel_ : Integrated line
intensity maps in the [13] CO _J_ = 3-2 (color scale) and SO 8 9 -7 8 emission (gray contours; from 6 to 23.5 K km s [−][1] in steps of 2.5 K km s [−][1] ) obtained
with the IRAM 30 m telescope at 8 [′′] resolution. The white dotted contours delineate the position of the H 2 dissociation front as traced by the infrared
H 2 v = 1–0 _S_ (1) line (from 1.5 to 4.0 × 10 [−][4] erg s [−][1] cm [−][2] sr [−][1] in steps of 0.5 × 10 [−][4] erg s [−][1] cm [−][2] sr [−][1] ; from Walmsley et al. 2000). The black-dashed
rectangle shows the smaller FoV imaged with ALMA (Fig. 3). The DF position has been observed with SOFIA, IRAM 30 m, and Herschel. Cyan
circles represent the ∼15 [′′] beam at 168 GHz. _Right panel_ : H 2 S lines lines detected toward three positions of the Orion Bar.



Regarding sulfur [2], several studies previously reported the
detection of S-bearing molecules in the Orion Bar. These include
CS, C [34] S, SO, SO 2, and H 2 S (Hogerheijde et al. 1995; Jansen
et al. 1995), SO [+] (Fuente et al. 2003), C [33] S, HCS [+], H 2 CS, and NS
(Leurini et al. 2006), and SH [+] (Nagy et al. 2013). These detections
refer to modest angular resolution pointed observations using
single-dish telescopes. Higher-angular-resolution interferometric
imaging of SH [+], SO, and SO [+] (Goicoechea et al. 2017) was
possible thanks to the _Atacama Compact Array_ (ACA).


_2.2._ _Observations of H_ 2 _S isotopologues and H_ 3 _S_ [+]


We observed the Orion Bar with the IRAM 30 m telescope at
Pico Veleta (Spain). We used the EMIR receivers in combination
with the Fast Fourier Transform Spectrometer (FTS) backends at
200 kHz resolution ( ∼ 0.4 km s [−][1], ∼ 0.3 km s [−][1], and ∼ 0.2 km s [−][1] at
∼ 168 GHz, ∼ 217 GHz, and ∼ 293 GHz, respectively). These observations are part of a complete line survey covering the frequency
range 80 − 360 GHz (Cuadrado et al. 2015, 2016, 2017, 2019)
and include deep integrations at 168 GHz toward three positions
of the PDR located at a distance of 14 [′′], 40 [′′], and 65 [′′] from the
IF (see Fig. 1). Their offsets with respect to the IF position at
α 2000 = 05 [h] 35 [m] 20.1 [s], δ 2000 = − 05 [◦] 25 [′] 07.0 [′′] are (+10 [′′], -10 [′′] ),
(+30 [′′], -30 [′′] ’), and (+35 [′′], -55 [′′] ). The first position is the DF.
We carried out these observations in the position switching
mode taking a distant reference position at (−600 [′′], 0 [′′] ) . The
half power beam width (HPBW) at ∼ 168 GHz, ∼ 217 GHz, and
∼ 293 GHz is ∼ 15 [′′], ∼ 11 [′′], and ∼ 8 [′′], respectively. The latest observations (those at 168 GHz) were performed in March 2020 . The
data were first calibrated in the antenna temperature scale _T_ A [∗] [and]
then converted to the main beam temperature scale, _T_ mb, using


2 Sulfur has four stable isotopes, in decreasing order of abundance:
32 S ( _I_ N = 0), 34 S ( _I_ N = 0), 33 S ( _I_ N = 3/2), and 36 S ( _I_ N = 0), where _I_ N is the
nuclear spin. The most abundant isotope is here simply referred to as S.



_T_ mb = _T_ A [∗] [/][η] [mb] [, where] [ η] [mb] [ is the antenna e][ffi][ciency] [ (][η] [mb] [ =][ 0.74] [ at]

∼
168 GHz). We reduced and analyzed the data using the GILDAS
software as described in Cuadrado et al. (2015). The typical rms
noise of the spectra is ∼3.5, 5.3, and 7.8 mK per velocity channel
at ∼ 168 GHz, ∼ 217 GHz, and ∼ 293 GHz, respectively. Figures 1
and 2 show the detection of _o_ -H 2 S 1 1,0 − 1 0,1 (168.7 GHz),
_p_ -H 2 S 2 2,0 − 2 1,1 (216.7 GHz), and _o_ -H 2 [34] S 1 1,0 − 1 0,1 lines
(167.9 GHz) (see Table E.1 for the line parameters), as well as
several _o_ -H 2 [33] S 1 1,0 − 1 0,1 hyperfine lines (168.3 GHz).


We complemented our dataset with higher frequency H 2 S
lines detected by the _Herschel Space Observatory_ (Nagy et al.
2017) toward the “CO [+] peak” position (Stoerzer et al. 1995),
which is located at only ∼ 4 [′′] from our DF position (i.e., within the
HPBW of these observations). These observations were carried
out with the HIFI receiver (de Graauw et al. 2010) at a spectralresolution of 1.1 MHz (0.7 km s [−][1] at 500 GHz). HIFI’s HPBW
range from ∼ 42 [′′] to ∼ 20 [′′] in the 500 - 1000 GHz window (Roelfsema et al. 2012). The list of additional hydrogen sulfide lines
detected by Herschel includes the _o_ -H 2 S 2 2,1 − 2 1,2 ( 505.5 GHz),
2 1,2 − 1 0,1 ( 736.0 GHz), and 3 0,3 − 2 1,2 ( 993.1 GHz), as well as the
_p_ -H 2 S 2 0,2 − 1 1,1 ( 687.3 GHz) line. We used the line intensities,
in the _T_ mb scale, shown in Table A.1 of Nagy et al. (2017).


In order to get a global view of the Orion Bar, we also obtained 2.5 [′] × 2.5 [′] maps of the region observed by us with the
IRAM 30 m telescope using the 330 GHz EMIR receiver and
the FTS backend at 200 kHz spectral-resolution ( ∼ 0.2 km s [−][1] ).
On-the-fly (OTF) scans were obtained along and perpendicular to
the Bar. The resulting spectra were gridded to a data cube through
convolution with a Gaussian kernel providing a final resolution of
∼ 8 [′′] . The total integration time was ∼ 6 h. The achieved rms noise
is ∼ 1 K per resolution channel. Figure 1 shows the spatial distribution of the [13] CO _J_ =3-2 (330.5 GHz) and SO 8 9 -7 8 (346.5 GHz)
integrated line intensities.


Article number, page 3 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


_2.3._ _ALMA imaging of Orion Bar edge in SH_ [+] _emission_



We carried out mosaics of a small field of the Orion Bar using twenty-seven ALMA 12 m antennas in band 7 (at ∼ 346 GHz).
These unpublished observations belong to project 2012.1.00352.S
( P.I.: J. R. Goicoechea ) and consisted of a 27-pointing mosaic
centered at α(2000) = 5 _[h]_ 35 _[m]_ 20.6 _[s]_ ; δ(2000) = -05 _[o]_ 25 [′] 20 [′′] . The
total field-of-view (FoV) is 58 [′′] × 52 [′′] (shown in Fig. 1). The two
hyperfine line components of the SH [+] _N_ _J_ = 1 0 − 0 1 transition
were observed with correlators providing ∼ 500 kHz resolution
(0.4 km s [−][1] ) over a 937.5 MHz bandwidth. The total observation
time with the ALMA 12 m array was ∼ 2h. In order to recover the
large-scale extended emission filtered out by the interferometer,
we used deep and fully sampled single-dish maps, obtained with
the total-power (TP) antennas at 19 [′′] resolution, as zero- and
short-spacings. Data calibration procedures and image synthesis
steps are described in Goicoechea et al. (2016). The synthesized
beam is ∼ 1 [′′] . This is a factor of ∼ 4 better than previous interferometric SH [+] observations (Goicoechea et al. 2017). Figure 3
shows the resulting image of the SH [+] 1 0 − 0 1 _F_ = 1/2-3/2 hyperfine emission line at 345.944 GHz. We rotated this image 37.5 _[o]_
clockwise to bring the FUV illumination in the horizontal direction. The typical rms noise of the final cube is ∼ 80 mK per
velocity channel and 1 [′′] -beam . As expected from their Einstein
coefficients, the other _F_ = 1/2-1/2 hyperfine line component at
345.858 GHz is a factor of ∼ 2 fainter (see Table E.2) and the
resulting image has low signal-to-noise (S/N).
We complemented the SH [+] dataset with the higher frequency lines observed by HIFI (Nagy et al. 2013, 2017) at
∼ 526 GHz and ∼ 683 GHz (upper limit) . These pointed observations have HPBWs of ∼ 41 [′′] and ∼ 32 [′′] respectively, thus they
do not spatially resolve the SH [+] emission. To determine their
beam coupling factors ( _f_ b ), we smoothed the bigger 4 [′′] -resolution
ACA + TP SH [+] image shown in Goicoechea et al. (2017) to the
different HIFI’s HPBWs. We obtain _f_ b ≃ 0.4 at ∼ 526 GHz and
_f_ b ≃ 0.6 at ∼ 683 GHz. The corrected intensities are computed as
_W_ corr = _W_ HIFI / _f_ b . These correction factors are only a factor of ≲ 2
lower than simply assuming uniform SH [+] emission from a 10 [′′]
width filament.


_2.4._ _SOFIA/GREAT search for SH emission_


We finally used the GREAT receiver (Heyminck et al. 2012)
on board the _Stratospheric_ _Observatory_ _For_ _Infrared_ _Astron-_
_omy_ (SOFIA; Young et al. 2012) to search for the lowestenergy rotational lines of SH ( [2] Π 3/2 _J_ = 3/2-1/2) at 1382.910 and
1383.241 GHz (e.g., Klisch et al. 1996; Martin-Drumel et al.

2012). These lines lie in a frequency gap that Herschel/HIFI
could not observe from space. These SOFIA observations belong
to project 07 _ 0115 ( P.I.: J. R. Goicoechea ). The SH lines were
searched on the lower side band of 4GREAT band 3. We employed the 4GREAT/HFA frontends and 4GFFT spectrometers
as backends. The HPBW of SOFIA at 1.3 THz is ∼ 20 [′′], thus
comparable with IRAM 30 m/EMIR and Herschel/HIFI observations. We also employed the total power mode with a reference
position at ( − 600 [′′],0 [′′] ). The original plan was to observe during
two flights in November 2019 but due to bad weather conditions,
only ∼70 min of observations were carried out in a single flight.
After calibration, data reduction included: removal of a first
order spectral baseline, dropping scans with problematic receiver
response, rms weighted average of the spectral scans, and calibration to _T_ mb intensity scale (η mb = 0.71) . The final spectrum,
smoothed to a velocity-resolution of 1 km s [−][1] has a rms noise of
∼ 50 mK (shown in Fig. 4). Two emission peaks are seen at the


Article number, page 4 of 25



**Fig. 2.** Detection of H 2 [33] S (at ∼ 168.3 GHz) toward the DF position of
the Orion Bar. Red lines indicate hyperfine components. Blue lines show
interloping lines from [13] CCH. The length of each line is proportional
to the transition line strength (taken from the Cologne Database for
Molecular Spectroscopy, CDMS; Endres et al. 2016).


frequencies of the Λ-doublet lines. Unfortunately, the achieved
rms is not enough to assure the unambiguous detection of each
component of the doublet. Although the stacked spectrum does
display a single line (suggesting a tentative detection) the resulting line-width (∆v ≃ 7 km s [−][1] ) is a factor of ∼ 3 broader than
expected in the Orion Bar (see Table E.3). Hence, this spectrum
provides stringent upper limits to the SH column density but
deeper integrations would be needed to confirm the detection.


**3.** **Observational results**


_3.1._ _H_ 2 [32] _S, H_ 2 [34] _S, and H_ 2 [33] _S across the PDR_


Figure 1 shows an expanded view of the Orion Bar in the
13
CO ( _J_ = 3-2) emission. FUV radiation from the Trapezium stars
comes from the upper-right corner of the image. The FUV radiation field is attenuated in the direction perpendicular to the
Bar. The infrared H 2 v = 1–0 _S_ (1) line emission (white contours)
delineates the position of the H-to-H 2 transition, the DF. Many
molecular species, such as SO, specifically emit from deeper
inside the PDR where the flux of FUV photons has considerably decreased. In contrast, H 2 S, and even its isotopologue H [34] 2 [S,]
show bright 1 1,0 -1 0,1 line emission toward the DF (right panels
in Fig. 1; see also Jansen et al. 1995). Rotationally excited H 2 S
lines have been also detected toward this position (Nagy et al.
2017), implying the presence of warm H 2 S close to the irradiated
cloud surface (i.e., at relatively low extinctions). The presence
of moderately large H 2 S column densities in the PDR is also
demonstrated by the unexpected detection of the rare isotopologue H [33] 2 [S] [toward] [the] [DF] [(at] [the] [correct] [LSR] [velocity] [of] [the]
PDR: v LSR ≃ 10.5 km s [−][1] ). Figure 2 shows the H [33] 2 [S] [ 1] [1][,][0] [-1] [0][,][1] [line]
and its hyperfine splittings (produced by the [33] S nuclear spin). To
our knowledge, H [33] 2 [S lines had only been reported toward the hot]
cores in Sgr B2 and Orion KL before (Crockett et al. 2014).
The observed _o_ -H 2 S/ _o_ -H [34] 2 [S 1] [1][,][0] [-1] [0][,][1] [line] [intensity] [ratio]
toward the DF is 15 ± 2, below the solar isotopic ratio of
32 34
S/ S = 23 (e.g., Anders & Grevesse 1989). The observed ratio
thus implies optically thick _o_ -H 2 S line emission at ∼ 168 GHz.
However, the observed _o_ -H [34] 2 [S][/] _[o]_ [-H] [33] 2 [S 1] [1][,][0] [-1] [0][,][1] [ intensity ratio is]
6 ± 1, thus compatible with the solar isotopic ratio ( [34] S/ [33] S = 5.5 )
and with H [34]
2 [S and H] [33] 2 [S optically thin emission.]

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry





**Fig.** **3.** ALMA 1 [′′] -resolution images zooming into the edge of the Orion Bar in [12] CO 3-2 ( _left_ _panel_, Goicoechea et al. 2016) and
SH [+] 1 0 -0 1 _F_ = 1/2-3/2 line ( _middle_ _panel_, integrated line intensity). The _right_ _panel_ shows the H 2 v = 1–0 _S_ (1) line (Walmsley et al. 2000).
We rotated these images (all showing the same FoV) with respect to Fig. 1 to bring the FUV illuminating direction in the horizontal direction (from
the right). The circle shows the DF position targeted with SOFIA in SH (20 [′′] beam) and with the IRAM 30m telescope in H 2 S and H 3 S [+] .



_3.2._ _SH_ [+] _emission from the PDR edge_


Figure 3 zooms into a small field of the Bar edge. The ALMA
image of the CO _J_ = 3-2 line peak temperature was first presented
by Goicoechea et al. (2016). Because the CO _J_ = 3-2 emission
is nearly thermalized and optically thick from the DF to the
molecular cloud interior, the line peak temperature scale ( _T_ peak )
is a good proxy of the gas temperature ( _T_ k ≃ _T_ ex ≃ _T_ peak ). The CO
image implies small temperature variations around _T_ k ≃ 200 K .
The middle panel in Fig. 3 shows the ALMA image of the SH [+]
_N_ _J_ = 1 0 -0 1 _F_ = 1/2-3/2 hyperfine line at 345.944 GHz. Compared
to CO, the SH [+] emission follows the edge of the molecular PDR,
akin to a filament of ∼ 10 [′′] width (for the spatial distribution
of other molecular ions, see, Goicoechea et al. 2017). The SH [+]
emission shows localized small-scale emission peaks (density or
column density enhancements) that match, or are very close to,
the vibrationally excited H 2 (v = 1-0) emission (Fig. 3). We note
that while some H 2 (v = 1-0) emission peaks likely coincide with
gas density enhancements (e.g., Burton et al. 1990), the region
also shows extended emission from FUV-pumped H 2 (v = 2-1)
(van der Werf et al. 1996) that does not necessarily coincide with
the H 2 (v = 1-0) emission peaks.


**Fig. 4.** Search for the SH [2] Π 3/2 _J_ =5/2-3/2 doublet (at ∼1383 GHz) toward the DF position with SOFIA/GREAT. Vertical magenta lines indicate the position of hyperfine splittings taken from CDMS.



_3.3._ _Search for SH, H_ 3 _S_ [+] _, and H_ 2 _S_ ν 2 _= 1 emission_


We used SOFIA/GREAT to search for SH [2] Π 3/2 _J_ =5/2-3/2 lines
toward the DF (Fig. 4). This would have been the first time
that interstellar SH rotational lines were seen in emission.
Unfortunately, the achieved rms of the observation does not allow a definitive confirmation of these lines, so here we will only
discuss upper limits to the SH column density. The red, green,
and blue curves in Fig. 4 show radiative transfer models for
_n_ H = 10 [6] cm [−][3], _T_ k = 200 K, and different SH column densities
(see Sect. 4 for more details).

Our IRAM 30 m observations toward the DF neither resulted
in a detection of H 3 S [+], a key gas-phase precursor of H 2 S. The
∼ 293.4 GHz spectrum around the targeted H 3 S [+] 1 0 -0 0 line is
shown in Fig. 5. Again, the achieved low rms allows us to provide
a sensitive upper limit to the H 3 S [+] column density. This results
in _N_ (H 3 S [+] ) =(5.5-7.5) × 10 [10] cm [−][2] (5 σ ) assuming an excitation
temperature range _T_ ex = 10-30 K and extended emission. Given
the bright H 2 S emission close to the edge of the Orion Bar, and because H 2 S formation at the DF might be driven by very exoergic
processes, we also searched for the 1 1,0 -1 0,1 line of vibrationally
excited H 2 S (in the bending mode ν 2 ). The frequency of this line
lies at ∼ 181.4 GHz (Azzam et al. 2013), thus at the end of our
2 mm-band observations of the DF ( rms ≃ 16 mK ). However, we
do not detect this line either.


**Fig.** **5.** Search for H 3 S [+] toward the Orion Bar with the IRAM 30 m
telescope. The blue curve shows the expected position of the line.


Article number, page 5 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted



**4.** **Coupled nonlocal excitation and chemistry**



In this section we study the rotational excitation of the observed
S-bearing hydrides [3] . We determine the SH [+], SH (upper limit),
and H 2 S column densities in the Orion Bar, and the “average” gas
physical conditions in the sense that we search for the combination of single _T_ k, _n_ H, and _N_ that better reproduces the observed
line intensities (so-called “single-slab” approach). In Sect. 6 we
expand these excitation models to multi-slab calculations that
take into account the expected steep gradients in a PDR.
In the ISM, rotationally excited levels are typically populated
by inelastic collisions. However, the lifetime of very reactive
molecules can be so short that the details of their formation and
destruction need to be taken into account when determining how
these levels are actually populated (Black 1998). Reactive collisions (collisions that lead to a reaction and thus to molecule
destruction) influence the excitation of these species when their
timescales become comparable to those of nonreactive collisions.
The lifetime of reactive molecular ions observed in PDRs (e.g.,
Fuente et al. 2003; Nagy et al. 2013; van der Tak et al. 2013;
Goicoechea et al. 2017, 2019) can be so short that they do not
get thermalized by nonreactive collisions or by absorption of the
background radiation field (Black 1998). In these cases, a proper
treatment of the molecule excitation requires including chemical formation and destruction rates in the statistical equilibrium
equations (d _n_ _i_ / d _t_ = 0) that determine the level populations:

� _n_ _j_ _A_ _ji_ + � _n_ _i_ � _B_ _ji_ _J_ [¯] _ji_ + _C_ _ji_ � + _F_ _i_ = (5)



_n_ _j_ _A_ _ji_ + �
_j_ - _i_ _j_ � _i_



_n_ _i_ � _B_ _ji_ _J_ [¯] _ji_ + _C_ _ji_ � + _F_ _i_ = (5)
_j_ � _i_



_j_ � _i_



This “formation pumping” formalism has been previously
implemented in large velocity gradient codes to treat, for example,
the local excitation of the very reactive ion CH [+] (Nagy et al. 2013;
Godard & Cernicharo 2013; Zanchet et al. 2013b; Faure et al.
2017). However, interstellar clouds are inhomogeneous and gas
velocity gradients are typically modest at small spatial scales.
This means that line photons can be absorbed and reemitted
several times before leaving the cloud. Here we implemented
this formalism in a Monte Carlo code that explicitly models the
nonlocal behavior of the excitation and radiative transfer problem
(see Appendix of Goicoechea et al. 2006).
Although radiative pumping by dust continuum photons does
not generally dominate in PDRs, for completeness we also included radiative excitation by a modified blackbody at a dust
temperature of ∼ 50 K and a dust opacity τ λ = 0.03 (150/λ[µm]) [1][.][6]
(which reproduces the observed intensity and wavelength dependence of the dust emission in the Bar; Arab et al. 2012). The
molecular gas fraction, _f_ (H 2 ) = 2 _n_ (H 2 )/ _n_ H, is set to 2/3, where
_n_ H = _n_ (H) + 2 _n_ (H 2 ) is the total density of H nuclei . This choice
is appropriate for the dissociation front and implies _n_ (H 2 ) = _n_ (H) .
As most electrons in the DF come from the ionization of carbon
atoms, the electron density _n_ _e_ is set to _n_ _e_ ≃ _n_ (C [+] ) = 1.4×10 [−][4] _n_ H
(e.g., Cuadrado et al. 2019). For the inelastic collisions with _o_ -H 2
and _p_ -H 2, we assumed that the H 2 ortho-to-para (OTP) ratio is
thermalized to the gas temperature.


_4.1._ _SH_ [+] _excitation and column density_


We start by assuming that the main destruction pathway of
SH [+] are reactions with H atoms and recombinations with
electrons (see Sect. 6.1). Hence, the SH [+] destruction rate is
_D_ ≃ _n_ _e_ _k_ e ( _T_ ) + _n_ (H) _k_ H ( _T_ ) (see Table 1 for the relevant chemical destruction rates). For _T_ k = _T_ e = 200 K and _n_ H = 10 [6] cm [−][3]
(e.g., Goicoechea et al. 2016) this implies _D_ ≃ 10 [−][4] s [−][1] (i.e., the
lifetime of an SH [+] molecule in the Bar is less than 3 h). At
these temperatures and densities, _D_ is about ten times smaller
than the rate of radiative and inelastic collisional transitions that
depopulate the lowest-energy rotational levels of SH [+] . Hence,
formation pumping does not significantly alter the excitation of
the observed SH [+] lines, but it does influence the population of
higher-energy levels. Formation pumping effects have been readily seen in CH [+] because this species is more reactive [5] and its
rotationally excited levels lie at higher-energy (i.e., their inelastic
collision pumping rates are slower, e.g., Zanchet et al. 2013b)
Figure 6 shows results of several models: without
formation pumping (dotted curves for model “ _F_ = _D_ = 0” ),
adding formation pumping with SH [+] destruction by H
and _e_ [−] (continuous curves for model “ _F_, _D_ ” ), and using
a factor of ten higher SH [+] destruction rates (simulating a
dominant role of SH [+] photodissociation or destruction by
reactions with vibrationally excited H 2 ; dashed curves for
model “ _F_, _D_ ×10” ). Since the formation of SH [+] is driven by
reaction (1) when H 2 molecules are in v ≥ 2, here we adopted
_T_ form ≃ _E_ (v = 2, _J_ = 0) / _k_ − 9860 K ≈ 2000 K . Because these are
constant column density _N_ (SH [+] ) excitation and radiative transfer
models, we used a normalized formation rate _F_ = [�] _F_ _i_ that
assumes steady-state SH [+] abundances consistent with the varying
gas density in each model. That is, _F_ = [�] _F_ _i_ = _x_ (SH [+] ) _n_ H _D_

[cm [−][3] s [−][1] ], where _x_ refers to the abundance with respect to H
nuclei.


5 CH + is more reactive than SH + because CH + does react with H 2 ( v =0)
exothermically producing CH [+] 2 [at] _[ k]_ [ =][ 1.2] [×] [10] [−][9] [ cm] [3] [ s] [−][1] [(][Anicich 2003][)]
and also because reaction of CH [+] with H is faster, _k_ = 7.5 × 10 [−][10] cm [3] s [−][1] .



, (6)




= _n_ _i_



�
 _j_ < _i_



_A_ _i j_ + �
_j_ < _i_ _j_ � _i_



� _B_ _i j_ _J_ [¯] _ij_ + _C_ _ij_ � + _D_ _i_



where _n_ _i_ [cm [−][3] ] is the population of rotational level _i_, _A_ _i j_
and _B_ _i j_ are the Einstein coefficients for spontaneous and induced emission, _C_ _i j_ [s [−][1] ] is the rate of inelastic collisions [4]

( _C_ _i j_ = [�] _k_ [γ] _i j_, _k_ _[n]_ _k_ [, where] [ γ] _ij_, _k_ [(] _[T]_ [) [cm] [3] [s] [−][1] []] [ are the collisional rate]
coefficients and _k_ stands for H 2, H, and _e_ [−] ), and _J_ [¯] _i j_ is the
mean intensity of the total radiation field over the line profile.
In these equations, _n_ _i_ _D_ _i_ is the destruction rate per unit volume of the molecule in level _i_, and _F_ _i_ its formation rate per
unit volume (both in cm [−][3] s [−][1] ). When state-to-state formation
rates are not available, and assuming that the destruction rate is
the same in every level ( _D_ _i_ = _D_ ), one can use the total destruction rate _D_ [s [−][1] ] (= [�] _k_ _[n]_ _k_ _[k]_ _k_ [(] _[T]_ [)][ +] [photodestruction rate,] [where]
_k_ _k_ [cm [3] s [−][1] ] is the state-averaged rate of the two-body chemical
reaction with species _k_ ) and consider that the level populations
of the nascent molecule follow a Boltzmann distribution at an
effective formation temperature _T_ form :


_F_ _i_ = _F_ g _i_ _e_ [−] _[E]_ _[i]_ [/] _[kT]_ [form] / _Q_ ( _T_ form ). (7)


In this formalism, _F_ [cm [−][3] s [−][1] ] is the state-averaged formation
rate per unit volume, g _i_ the degeneracy of level _i_, and _Q_ ( _T_ form ) is
the partition function at _T_ form (van der Tak et al. 2007).


3 Readers interested only in the chemistry of these species and in depthdependent PDR models could directly jump to Section 6.
4 We use the following inelastic collision rate coefficients γ _ij_ :

- SH [+] – _e_ [−], including hyperfine splittings (Hamilton et al. 2018).

- SH [+] – _o_ -H 2 and _p_ -H 2, including hyperfine splittings (Dagdigian 2019).

- SH [+] – H, including hyperfine splittings (Lique et al. 2020).

- _o_ -H 2 S and _p_ -H 2 S with _o_ -H 2 and _p_ -H 2 (Dagdigian 2020).

- SH– He, including fine-structure splittings (Kłos et al. 2009).


Article number, page 6 of 25

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


_4.2._ _SH excitation and column density_



**Fig. 6.** Non-LTE excitation models of SH [+] . The horizontal lines mark
the observed line intensities in the Orion Bar. Dotted curves are for a
standard model ( _F_ = _D_ = 0) . Continuous curves are for a model that
includes chemical destruction by H atoms and _e_ [−] (model _F_, _D_ ) . Dashed
lines are for a model in which destruction rates are multiplied by ten
(model _F_, _D_ ×10). The vertical black line marks the best model.


The detected SH [+] rotational lines connect the fine-structure
levels _N_ _J_ = 1 0 -0 1 (345 GHz) and 1 2 -0 1 (526 GHz). Upper limits
also exist for the 1 1 -0 1 (683 GHz) lines. SH [+] critical densities
( _n_ cr = _A_ _i j_ / γ _ij_ ) for inelastic collisions with H or H 2 are of the same
order and equal to several 10 [6] cm [−][3] . As for many molecular ions
(e.g., Desrousseaux et al. 2021), SH [+] –H 2 (and SH [+] –H ) inelastic
collisional rate coefficients [4] are large ( γ _ij_ ≳ 10 [−][10] cm [3] s [−][1] ). Thus,
collisions with H (at low _A_ _V_ ) and H 2 (at higher _A_ _V_ ) generally dominate over collisions with electrons ( γ _ij_ of a few 10 [−][7] cm [3] s [−][1] ). At
low densities (meaning _n_ H < _n_ cr ) formation pumping increases
the population of the higher-energy levels (and their _T_ ex ), but
there are only minor effects in the low-energy submillimeter
lines. At high densities, _n_ H - 10 [7] cm [−][3], formation pumping with
_T_ form = 2000 K produces lower intensities in these lines because
the lowest-energy levels ( _E_ u / _k_ < _T_ k < _T_ form ) are less populated.

The best fit to the observed lines in model F, D is
for _N_ (SH [+] ) ≃ 1.1×10 [13] cm [−][3], _n_ H ≃ 3×10 [5] cm [−][3], and _T_ k ≃ 200 K .
This is shown by the vertical dotted line in Fig. 6 . This
model is consistent with the upper limit intensity of the
683 GHz line (Nagy et al. 2013) . In this comparison, and following the morphology of the SH [+] emission revealed by
ALMA (Fig. 3), we corrected the line intensities of the SH [+]
lines detected by Herschel/HIFI with the beam coupling factors discussed in Sec. 2.3, The observed 1 2 -0 1 /1 0 -0 1 line ratio ( _R_ = _W_ (526.048)/ _W_ (345.944) ≃ 2 ) is sensitive to the gas density. In these models, _R_ is 1.1 for _n_ H = 10 [5] cm [−][3] and 3.0 for
_n_ H =10 [6] cm [−][3] . We note that _n_ H could be lower if SH [+] formation/destruction rates were faster, as in the _F_, _D_ ×10 model. This
could happen if SH [+] photodissociation or destruction reactions
with H 2 (v ≥2) were faster than reactions of SH [+] with H atoms or
with electrons. In Sec. 6 we show that this is not the case.



SH is a [2] Π open-shell radical with fine-structure, Λ-doubling, and
hyperfine splittings (e.g., Martin-Drumel et al. 2012). However,
the frequency separation of the SH [2] Π 3/2 _J_ = 5/2-3/2 hyperfine
components is too small to be spectrally resolved in observations
of the Orion Bar (see Fig. 4).The available rate coefficients for
inelastic collisions of SH with helium atoms do not resolve the
hyperfine splittings. Hence, we first determined line frequencies,
level degeneracies, and Einstein coefficients of an SH molecule
without hyperfine structure. To do this, we took the complete set
of hyperfine levels tabulated in CDMS. Lacking specific inelastic
collision rate coefficients, we scaled the available SH– He rates
of Kłos et al. (2009) by the square root of the reduced mass ratios
and estimated the SH– H and SH– H 2 collisional rates.
The scaled rate coefficients are about an order of magnitude smaller than those of SH [+] . However, the chemical destruction rate of SH at the PDR edge (reactions with H, photodissociation, and photoionization, see Sect. 6.1) is also slower
(we take the rates of SH–H reactive collisions from Zanchet
et al. 2019). We determine _D_ ≃ 3 × 10 [−][6] s [−][1] for _n_ H = 10 [6] cm [−][3],
_T_ k = 200 K, and _A_ _V_ ≃ 0.7 mag. Models in Fig. 7 include these
chemical rates for _T_ form = _T_ k (a lower limit to the unknown formation temperature). Formation pumping enhances the intensity of
the [2] Π 3/2 _J_ = 5/2-3/2 ground-state lines by a few percent only.

To estimate the SH column density in the Orion Bar we compare with the upper limit intensities of the SH lines targeted
by SOFIA. If SH and SH [+] arise from roughly the same gas at
similar physical conditions ( _n_ H ≃ 10 [6] cm [−][3] and _T_ _k_ ≃ 200 K ) the
best model column density is for _N_ (SH) ≤ (0.6-1.6)×10 [14] cm [−][2] .
If densities were lower, around _n_ H ≃ 10 [5] cm [−][3], the upper limit
_N_ (SH) column densities will be a factor ten higher.


**Fig. 7.** Non-LTE excitation models of SH emission lines targeted with
SOFIA/GREAT. Horizontal dashed lines refer to observational limits,
assuming extended emission (lower intensities) and for a 10 [′′] width
emission filament at the PDR surface (higher intensities).


Article number, page 7 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


**Fig. 8.** Non-LTE excitation models for _o_ -H 2 S and _p_ -H 2 S. Thin horizontal lines show the observed intensities assuming either extended emission
(lower limit) or emission that fills the 15 [′′] beam at 168.7 GHz. The vertical line marks the best model, resulting in an OTP ratio of 2.9 ± 0.3.



_4.3._ _H_ 2 _S excitation and column density_


H 2 S has a _X_ [2] _A_ ground electronic state and two nuclear spin
symmetries that we treat separately, _o_ -H 2 S and _p_ -H 2 S. Previous studies of the H 2 S line excitation have used collisional
rates coefficients scaled from those of the H 2 O – H 2 system.
Dagdigian (2020) recently carried out specific calculations of
the cross sections of _o_ -H 2 S and _p_ -H 2 S inelastic collisions with
_o_ –H 2 and _p_ -H 2 at different temperatures. The behavior of the new
and the scaled rates is different and it depends on the H 2 OTP
ratio (e.g., on gas temperature) because the collisional cross sections are different for _o_ -H 2 –H 2 S and _p_ -H 2 –H 2 S systems. At the
warm temperatures of the PDR, collisions with _o_ -H 2 dominate,
resulting in rate coefficients for the ∼ 168 GHz _o_ -H 2 S line that are
a factor up to ∼2.5 smaller than those scaled from H 2 O–H 2 .


H 2 S is not a reactive molecule. At the edge of the PDR its
destruction is driven by photodissociation. We determine that the
radiative and collisional pumping rates are typically a factor of
∼ 100 higher than _D_ ≈ 2×10 [−][6] s [−][1] (for _n_ H = 10 [6] cm [−][3], _T_ k = 200 K,
_G_ 0 ≃ 10 [4], and _A_ _V_ ≃ 0.7 mag). Figure 8 shows non-LTE _o_ -H 2 S and
_p_ -H 2 S excitation and radiative transfer models. As H 2 S may have
its abundance peak deeper inside the PDR and display more
extended emission than SH [+] (e.g., Sternberg & Dalgarno 1995),
we show results for _T_ k = 200 and 100 K. When comparing with
the observed line intensities, we considered either emission that
fills all beams, or a correction that assumes that the H 2 S emission only fills the 15 [′′] beam of the IRAM 30m telescope at
168 GHz. The vertical dotted lines in Fig. 8 show the best model,
_N_ (H 2 S) = _N_ ( _o_ -H 2 S)+ _N_ ( _p_ -H 2 S) = 2.5×10 [14] cm [−][2], with an OTP
ratio of 2.9 ± 0.3, thus consistent with the high-temperature
statistical ratio of 3/1 (see discussion at the end of Sect. 6.4). Models with lower densities, _n_ H ≃ 10 [5] cm [−][3], show worse agreement,
and would translate into even higher _N_ (H 2 S) of ≳ 10 [15] cm [−][2] . In
either case, these calculations imply large columns of warm H 2 S
toward the PDR. They result in a limit to the SH to H 2 S column
density ratio of ≤ 0.2-0.6 . This upper limit is already lower than
the _N_ (SH)/ _N_ (H 2 S) = 1.1-3.0 ratios observed in diffuse clouds
(Neufeld et al. 2015). This difference suggests an enhanced H 2 S
formation mechanism in FUV-illuminated dense gas.


Article number, page 8 of 25



**5.** **New results on sulfur-hydride reactions**


In this section we summarize the _ab initio_ quantum calculations
we carried out to determine the vibrationally-state-dependent
rates of gas-phase reactions of H 2 (v > 0) with several S-bearing
species. We recall that all hydrogen abstraction reactions,


[+][H] [2] [+][H] [2] [+][H] [2] +H 2
S [+] −−−→ SH [+] −−−→ H 2 S [+] −−−→ H 3 S [+], S −−−→ SH,
(1) (2) (3) (4)


are very endoergic for H 2 ( v = 0), with endothermicities in Kelvin
units that are significantly higher than _T_ k even in PDRs. This
is markedly different to O [+] chemistry, for which all hydrogen
abstraction reactions leading to H 3 O [+] are exothermic and fast
(Gerin et al. 2010; Neufeld et al. 2010; Hollenbach et al. 2012).
The endothermicity of reactions involving H _n_ S [+] ions decreases as the number of hydrogen atoms increases. The potential
energy surfaces (PES) of these reactions possess shallow wells at
the entrance and products channels (shown in Fig. 9). In addition,
these PESs show saddle points between the energy walls of reactants and products whose heights increase with the number of H
atoms. For reaction (2), the saddle point has an energy of 0.6 eV
( ≃ 7,000 K) and is slightly below the energy of the products. However, for reaction (3), the saddle point is above the energy of the
products and is a reaction barrier. These saddle points act as a
bottleneck in the gas-phase hydrogenation of S [+] .
If one considers the state dependent reactivity of vibrationally
excited H 2, the formation of SH [+] through reaction (1) becomes
exoergic [6] when v ≥ 2 (Zanchet et al. 2019). The detection of bright
H 2 S emission in the Orion Bar ( Figs. 1 and 4 ) might suggest that
subsequent hydrogen abstraction reactions with H 2 (v ≥ 2) proceed as well. Motivated by these findings, and before carrying out
any PDR model, we studied reaction (2) and the reverse process
in detail. This required to build a full dimensional quantum PES
of the H 3 S [+] (X [1] A 1 ) system (see Appendix A).
In addition, we studied reaction (4) (and its reverse) through
quantum calculations. Details of these _ab initio_ calculations and
of the resulting reactive cross sections are given in Appendix B .


6 If one considers H 2 rovibrational levels, reaction (1) becomes exoergic
for v = 0, _J_ ≥ 11 and for v = 1, _J_ ≥ 7 (Zanchet et al. 2019).

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


**Table 1.** Relevant rate coefficients from a fit of the Arrhenius-like form
_k_ ( _T_ ) = α ( _T_ /300 K) [β] exp(−γ/ _T_ ) to the calculated reaction rates.


Reaction α β γ
(cm [3] s [−][1] ) (K)
SH ~~[+]~~ + H 2 (v=1) → H 2 S ~~[+]~~ + H 4.97e-11 0 1973.4 _[a]_
SH [+] + H 2 (v=2) → H 2 S [+] + H 5.31e-10 -0.17 0 _[a]_
SH [+] + H 2 (v=3) → H 2 S [+] + H 9.40e-10 -0.16 0 _[a]_

SH [+] + H → S [+] + H 2 1.86e-10 -0.41 27.3 _[b]_

SH ~~[+]~~ + _e_ [−] → S + H 2.00e-07 -0.50 _c_

H 2 S ~~[+]~~ + H → SH ~~[+]~~ + H 2 6.15e-10 -0.34 0 _[a]_

S + H 2 (v=2) → SH + H ∼8.6e-13 ∼2.3 ∼2500 _[a]_
S + H 2 (v=3) → SH + H ∼1.7e-12 ∼2.0 ∼1500 _[a]_

SH + H → S + H 2 5.7e-13 2.48 1600 _[a]_ [,][†]

7.7e-14 0.39 −1.3 _[a]_ [,][†]

S [+] + H 2 (v=2) → SH [+] + H 2.88e-10 -0.15 42.9 _[b]_

S [+] + H 2 (v=3) → SH [+] + H 9.03e-10 -0.11 26.2 _[b]_

S [+] + H 2 (v=4) → SH [+] + H 1.30e-09 -0.04 40.8 _[b]_

S [+] + H 2 (v=5) → SH [+] + H 1.21e-09 0.09 34.5 _[b]_


**Notes.** [(] _[a]_ [)] This work. [(] _[b]_ [)] From Zanchet et al. (2019). [(] _[c]_ [)] From Prasad &
Huntress (1980). [†] Total rate is the sum of the two expressions.


tion through reaction (4) ( S + H 2 ) are considerably smaller than
for reactions (1) and (2), and show an energy barrier even for
H 2 (v = 2) and H 2 (v = 3) . We anticipate that this reaction is not a
relevant formation route for SH.

In FUV-illuminated environments, collisions with H atoms
are very important because they compete with electron recombinations in destroying molecular ions, and also they contribute
to their excitation. An important result of our calculations is that
the destruction rate of H 2 S [+] (SH [+] ) in reactions with H atoms
are a factor of ≥ 3.5 ( ≥ 1.7 ) faster (at _T_ k ≤ 200 K ) than those
previously used in astrochemical models (Millar et al. 1986) .
Conversely, we find that destruction of SH in reactions with H
atoms (Appendix B) is slower than previously assumed.


**6.** **PDR models of S-bearing hydrides**



**Fig. 9.** Minimum energy paths for reactions (1), (2), and (3). Points correspond to RCCSD(T)-F12a calculations and lines to fits ( Appendix A ).
The reaction coordinate, _s_, is defined independently for each path. The
geometries of each species at _s_ =0 are different.


Table 1 summarizes the updated reaction rate coefficients that we
will include later in our PDR models.
The H 2 S [+] formation rate through reaction (2) with H 2 (v = 0)
is very slow. For H 2 (v = 1), the rate constant increases at
≈ 500 K, corresponding to the opening of the H 2 S [+] + H threshold. For H 2 ( v = 2) and H 2 ( v = 3), the reaction rate is much
faster, close to the Langevin limit (see Appendix A.2 ). However,
our estimated vibrational-state specific rates for SH forma


We now investigate the chemistry of S-bearing hydrides and the
effect of the new reaction rates in PDR models adapted to the
Orion Bar conditions. In this analysis we used version 1.5.4. of
the Meudon PDR code (Le Petit et al. 2006; Bron et al. 2014).
Following our previous studies, we model the Orion Bar as a
stationary PDR at constant thermal-pressure (i.e., with density
and temperature gradients). When compared to time-dependent
hydrodynamic PDR models (e.g., Hosokawa & Inutsuka 2006;
Bron et al. 2018; Kirsanova & Wiebe 2019), stationary isobaric models seem a good description of the most exposed and
compressed gas layers of the PDR, from _A_ _V_ ≈ 0.5 to ≈ 5 mag
(Goicoechea et al. 2016; Joblin et al. 2018).
In our models, the FUV radiation field incident at the PDR
edge is _G_ 0 = 2 × 10 [4] (e.g., Marconi et al. 1998) . We adopted an
extinction to color-index ratio, _R_ _V_ = _A_ _V_ / _E_ _B_ − _V_, of 5.5 (Joblin
et al. 2018), consistent with the flatter extinction curve observed in Orion (Lee 1968; Cardelli et al. 1989). This choice
implies slightly more penetration of FUV radiation into the cloud
(e.g., Goicoechea & Le Bourlot 2007) . The main input parameters and elemental abundances of these PDR models are summarized in Table 2. Figure 10 shows the resulting H 2, H, and
electron density profiles, as well as the _T_ k and _T_ d gradients.


Article number, page 9 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted



**Table 2.** Main parameters used in the PDR models of the Orion Bar.


Model parameter Value Note
FUV illumination, _G_ 0 2×10 [4] Habing ( _a_ )
Total depth _A_ V 10 mag
Thermal pressure _P_ th / _k_ 2×10 [8] cm [−][3] K
Density _n_ H = _n_ (H) + 2 _n_ (H 2 ) _n_ H = _P_ th / _kT_ k Varying
Cosmic Ray ζ CR 10 [−][16] H 2 s [−][1] ( _b_ )
_R_ V = _A_ V / _E_ B−V 5.5 Orion _[c]_

_M_ gas / _M_ dust 100 Local ISM
Abundance O / H 3.2×10 [−][4]

Abundance C / H 1.4×10 [−][4] Orion _[d]_

Abundance S / H 1.4×10 [−][5] Solar _[e]_


**Notes.** _[a]_ Marconi et al. (1998). _[b]_ Indriolo et al. (2015). _[c]_ Cardelli et al.
(1989). _[d]_ Sofia et al. (2004). _[e]_ Asplund et al. (2009).


**Fig.** **10.** Structure of an isobaric PDR representing the most FUVirradiated gas layers of the Orion Bar (see Table 2 for the adopted
parameters). This plot shows the H 2, H, and electron density profiles
(left axis scale), and the gas and dust temperatures (right axis scale).


Our chemical network is that of the Meudon code updated
with the new reaction rates listed in Table 1. This network includes
updated photoreaction rates from Heays et al. (2017). To increase
the accuracy of our abundance predictions, we included the explicit integration of wavelength-dependent SH, SH [+], and H 2 S
photodissociation cross sections ( σ diss ), as well as SH and H 2 S
photoionization cross sections ( σ ion ). These cross sections are
shown in Fig C.1 of the Appendix. The integration is performed
over the specific FUV radiation field at each position of the PDR.
In particular, we took σ ion (SH) from Hrodmarsson et al. (2019)
and σ diss (H 2 S) from Zhou et al. (2020), both determined in laboratory experiments. Figure 11 summarizes the relevant chemical
network that leads to the formation of S-bearing hydrides and
that we discuss in the following sections.


_6.1._ _Pure gas-phase PDR model results_


Figure 12 shows results of the “new gas-phase” model using
the reaction rates in Table 1. The continuous curves display the
predicted fractional abundance profiles as a function of cloud
depth in magnitudes of visual extinction ( _A_ _V_ ). The dashed curves
are for a model that uses the standard thermal rates previously
adopted in the literature (see, e.g., Neufeld et al. 2015) . As noted
by Zanchet et al. (2013a, 2019), the inclusion of H 2 (v ≥ 2) state

Article number, page 10 of 25





















**Fig. 11.** Main gas and grain reactions leading to the formation of sulfur
hydrides. Red arrows represent endoergic reactions (endothermicity
given in units of K). Dashed arrows are uncertain radiative associations
(see Sect. A.3), γ stands for a FUV photon, and “s-” for solid.


dependent quantum rates for reaction (1) enhances the formation
of SH [+] in a narrow layer at the edge of the PDR ( _A_ _V_ ≃ 0 to 2 mag) .
This agrees with the morphology of the SH [+] emission revealed
by ALMA images (Fig. 3). For H 2 (v = 2), the reaction rate enhancement with respect to the thermal rate ∆ _k_ = _k_ 2 ( _T_ )/ _k_ 0 ( _T_ )
(see discussion by Agúndez et al. 2010) is about 4 × 10 [8] at
_T_ k = 500 K (Millar et al. 1986). Indeed, when the fractional
abundance of H 2 ( v = 2) with respect to H 2 ( v = 0), defined as
_f_ 2 = _n_ (H 2 v = 2)/ _n_ (H 2 v = 0), exceeds a few times 10 [−][9], meaning
∆ _k_ - _f_ 2 - 1, reaction (1) with H 2 ( v ≥ 2) dominates SH [+] formation. This reaction enhancement takes place only at the edge of
the PDR, where FUV-pumped H 2 ( v ≥ 2) molecules are abundant
enough (gray dashed curves in Fig. 12) and drive the formation
of SH [+] . The resulting SH [+] column density increases by an order
of magnitude compared to models that use the thermal rate.
In this isobaric model, the SH [+] abundance peak occurs
at _A_ _V_ ≃ 0.7 mag, where the gas density has increased from
_n_ H ≃ 6×10 [4] cm [−][3] at the PDR edge (the IF) to ∼ 5 × 10 [5] cm [−][3] (at
the DF). At this point, SH [+] destruction is dominated by recombination with electrons and by reactive collisions with H atoms.
This implies _D_ (SH [+] ) [s [−][1] ] ∼ _n_ _e_ _k_ _e_ ≃ _n_ H _k_ H ≫ _n_ (H 2 v≥ 2) _k_ 2, as we
assumed in the single-slab SH [+] excitation models ( Sec. 4.1 ).
Therefore, only a small fraction of SH [+] molecules further react with H 2 ( v ≥ 2) to form H 2 S [+] . The resulting low H 2 S [+] abundances limit the formation of abundant SH from dissociative
recombinations of H 2 S [+] (recall that we estimated that reaction
S + H 2 ( v ≥ 2) → SH + H is very slow). The SH abundance peak is
shifted deeper inside the cloud, at about _A_ _V_ ≃ 1.8 mag, where SH
forms by dissociative recombination of H 2 S [+] and it is destroyed
by FUV photons and reactions with H atoms. In these gas-phase
models the H 2 S abundance peaks even deeper inside the PDR, at
A _V_ ≃ 5 mag, where it forms by recombinations of H 2 S [+] and H 3 S [+]
with electrons as well as by charge exchange S + H 2 S [+] . However, the new rate of reaction H 2 S [+] + H is higher than assumed
in the past, so the new models predict lower H 2 S [+] abundances at
intermediate PDR depths (thus, less H 3 S [+] and H 2 S; see Fig. 12).
The SH column density predicted by the new gas-phase
model is below the upper limit determined from SOFIA. However,
the predicted H 2 S column density is much lower than the value
we derive from observations (Table 3) and the predicted H 2 S line
intensities are too faint (see Sect. 6.4).
Because the cross sections of the different H 2 S photodissociation channels have different wavelength dependences (Zhou et al.
2020), the H 2 S and SH abundances between _A_ _V_ ≈ 2 and 6 mag

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


**Table 3.** Column density predictions from different PDR models (up to _A_ _V_ = 10 mag) and estimated values from observations (single-slab approach).


log _N_ (cm [−][2] )
_Type of PDR model_ _[a]_ SH [+] SH H 2 S H 2 S [+] H 3 S [+]

Standard gas-phase 11.0 _[a]_ –12.2 _[b]_ 11.4 _[a]_ –12.5 _[b]_ 11.3 _[a]_ –12.4 _[b]_ 9.9 _[a]_ –11.1 _[b]_ 7.8 _[a]_ –9.0 _[b]_

New gas-phase (Table 1) 12.1 _[a]_ –13.2 _[b]_ 11.4 _[a]_ –12.5 _[b]_ 10.6 _[a]_ –11.7 _[b]_ 9.9 _[a]_ –11.0 _[b]_ 7.7 _[a]_ –8.9 _[b]_

Gas-grain (low _E_ b, ϵ=1%) 12.0 _[a]_ –13.2 _[b]_ 13.2 _[a]_ –14.4 _[b]_ 12.9 _[a]_ –14.1 _[b]_ 9.6 _[a]_ –10.7 _[b]_ 10.1 _[a]_ –11.2 _[b]_

Gas-grain (high _E_ b, ϵ=1%) 12.0 _[a]_ –13.1 _[b]_ 13.6 _[a]_ –14.8 _[b]_ 13.7 _[b]_ –14.8 _[b]_ 9.9 _[b]_ –11.0 _[b]_ 10.8 _[b]_ –12.0 _[b]_


Estimated from observations ∼13.1 <13.8 ∼14.4 – < 10.7


**Notes.** _[a]_ Column densities for a face-on PDR. _[b]_ Edge-on PDR with a tilt angle α = 4 _[o]_, leading to the maximum expected geometrical enhancement.



**Fig. 12.** Pure gas-phase PDR models of the Orion Bar. Continuous curves
show fractional abundances as a function of cloud depth, in logarithm
scale to better display the irradiated edge of the PDR, using the new
reaction rates listed in Table 1 . The gray dotted curve shows _f_ 2, the
fraction of H 2 that is in vibrationally excited levels v ≥ 2 (right axis
scale). Dashed curves are for a model using standard reaction rates.


are sensitive to the specific shape of the FUV radiation field (determined by line blanketing, dust absorption, and grain scattering ;
e.g., Goicoechea & Le Bourlot 2007). Still, we checked that
using steeper extinction curves does not increase H 2 S column
density any closer to the observed levels. This disagreement between the observationally inferred _N_ (H 2 S) column density and
the predictions of gas-phase PDR models is even worse [7] if one
considers the uncertain rates of radiative association reactions
S [+] + H 2 → H 2 S [+] + _h_ ν and SH [+] + H 2 → H 3 S [+] + _h_ ν included in the
new gas-phase model. For the latter reaction, the main problem is that the electronic states of the reactants do not correlate
with the [1] _A_ 1 ground electronic state of the activated complex
H 3 S [+][∗] (denoted by ∗). Instead, H 3 S [+][∗] forms in an excited triplet
state ( [3] _A_ ). Herbst et al. (1989) proposed that a spin-flip followed
by a radiative association can occur in interstellar conditions


7 Older gas-phase PDR models previously predicted low H 2 S
column densities (Jansen et al. 1995; Sternberg & Dalgarno 1995).



and form H 3 S [+][∗] ( _X_ [1] _A_ 1 ) (Millar & Herbst 1990) . In Appendix A.3,
we give arguments against this mechanism. For similar reasons,
Prasad & Huntress (1982) avoided to include the S [+] + H 2 radiative association in their models. Removing these reactions in pure
gas-phase models drastically decreases the H 2 S [+] and H 3 S [+] abundances, and thus those of SH and H 2 S (by a factor of ∼ 100 in these
models). The alternative H 2 S [+] formation route through reaction
SH [+] + H 2 (v = 2) is only efficient at the PDR surface ( _A_ _V_ < 1 mag ).
This is due to the large H 2 ( v = 2) fractional abundances, _f_ 2 - 10 [−][6]
at _T_ _k_ - 500 K, required to enhance the H 2 S [+] production. Therefore, and contrary to S [+] destruction, reaction of SH [+] with H 2
is not the dominant destruction pathway for SH [+] . Only deeper
inside the PDR, reactions of S with H [+] 3 [produce small abundances]
of SH [+] and H 2 S [+], but the hydrogenation of H _n_ S [+] ions is not
efficient and limits the gas-phase production H 2 S.


_6.2._ _Grain surface formation of solid H_ 2 _S_


Similarly to the formation of water ice (s-H 2 O) on grains
(e.g., Hollenbach et al. 2009, 2012), the formation of H 2 S may
be dominated by grain surface reactions followed by desorption back to the gas (e.g., Charnley 1997) . Indeed, water vapor is
relatively abundant in the Bar ( _N_ (H 2 O) ≈ 10 [15] cm [−][2] ; Choi et al.
2014; Putaud et al. 2019) and large-scale maps show that the H 2 O
abundance peaks close to cloud surfaces (Melnick et al. 2020).
To investigate the s-H 2 S formation on grains, we updated the
chemical model by allowing S atoms to deplete onto grains as
the gas temperature drops inside the molecular cloud (for the
basic grain chemistry formalism, see, Hollenbach et al. 2009).
The timescale of this process ( τ gr, S ) goes as _x_ (S) [−][1] _n_ [−] H [1] _[T]_ [ −] k [1][/][2],
where _x_ (S) is the abundance of neutral sulfur atoms with respect
to H nuclei. In a PDR, the abundance of H atoms is typically
higher than that of S atoms [8] and H atoms stick on grains more
frequently than S atoms unless _x_ (H) < _x_ (S)·0.18 . An adsorbed H
atom ( s-H ) is weakly bound, mobile, and can diffuse throughout the grain surface until it finds an adsorbed S atom ( s-S ). If
the timescale for a grain to be hit by a H atom ( τ gr, H ) is shorter
that the timescale for a s-S atom to photodesorb ( τ photdes, S ) or
sublimate ( τ subl, S ) then reaction of s-H with s-S will proceed
and form a s-SH radical roughly upon “collision” and without energy barriers (e.g., Tielens & Hagen 1982; Tielens 2010) .
Likewise, if τ gr, H < τ photdes, SH and τ gr, H < τ subl, SH, a newly adsorbed s-H atom can diffuse, find a grain site with an s-SH radical
and react without barriers to form s-H 2 S . In these surface processes, a significant amount of S is ultimately transferred to s-H 2 S


8 We only consider the depletion of neutral S atoms. S + ions are expected to be more abundant than S atoms at the edge of the Orion Bar
( _A_ _V_ ≲ 2 mag) where _T_ k and _T_ d are too high, and the FUV radiation field
too strong, to allow the formation of abundant grain mantles.


Article number, page 11 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


**Table 4.** Adopted binding energies and photodesorption yields.


Species _E_ b / _k_ Yield
(K) (FUV photon) [−][1]

S 1100 _[a]_ /2600 _[b]_ 10 [−][4]

SH 1500 _[a]_ /2700 _[b]_ 10 [−][4]

H 2 S 2700 _[b]_ [,] _[c]_ 1.2×10 [−][3] [g] (as H 2 S)
CO 1300 _[d]_ 3×10 [−][3] _[h]_


O 1800 _[e]_ 10 [−][4] _[h]_

O 2 1200 _[d]_ 10 [−][3] _[h]_

OH 4600 _[a]_ 10 [−][3] _[h]_

H 2 O 4800 _[f]_ 10 [−][3] _[h]_ (as H 2 O)
2×10 [−][3] _[h]_ (as OH)


**Notes.** _[a]_ Hasegawa & Herbst (1993). _[b]_ Wakelam et al. (2017). _[c]_ Collings
et al. (2004). _[d]_ Minissale et al. (2016). _[e]_ He et al. (2015). _[f]_ Sandford &
Allamandola (1988). [g] Fuente et al. (2017) _[h]_ See, Hollenbach et al. (2009).



**Fig. 13.** Representative timescales relevant to the formation of s-H 2 S and
s-H 2 O as well as their freeze-out depths. _Upper panel_ : The continuous
black curve is the timescale for a grain to be hit by an H atom. Once in
the grain surface, the H atom diffuses and can react with an adsorbed
S atom to form s-SH . The dashed magenta curves show the timescale
for thermal desorption of an s-S atom ( _E_ b / _k_ (S) = 1100 K left curve, and
2600 K right curve) and of an s-O atom (blue curve; _E_ b / _k_ (O) = 1800 K ).
The gray dotted curve is the photodesorption timescale of s-S . At _G_ 0
values where the continuous line is below the dashed and dotted lines,
s-O and s-S atoms remain on grain surfaces sufficiently long to combine
with an adsorbed H atom and form s-OH and s-SH (and then s-H 2 O and
s-H 2 S ). These timescales are for _n_ H = 10 [5] cm [−][3] and _n_ (H) = 100 cm [−][3] .
_Bottom panel_ : Freeze-out depth at which most O and S are incorporated
as s-H 2 O and s-H 2 S (assuming no chemical desorption and _T_ k = _T_ d ).


(e.g., Vidal et al. 2017), which can subsequently desorb: thermally,
by FUV photons, or by cosmic rays. In addition, laboratory experiments show that the excess energy of certain exothermic
surface reactions can promote the direct desorption of the product
(Minissale et al. 2016) . In particular, reaction s-H + s-SH directly
desorbs H 2 S with a maximum efficiency of ∼ 60 % (as observed
in experiments, Oba et al. 2018). Due to the high flux of FUV
photons in PDRs, chemical desorption may not always compete
with photodesorption. However, it can be a dominant process inside molecular clouds (Garrod et al. 2007; Esplugues et al. 2016;
Vidal et al. 2017; Navarro-Almaida et al. 2020).
The photodesorption timescale of an ice mantle is proportional to _Y_ [−][1] _G_ [−] 0 [1] [exp (][+] _[b A]_ _[V]_ [)] [,] [where] _[Y]_ [is] [the] [photodesorption]
yield (the number of desorbed atoms or molecules per incident
photon) and _b_ is a dust-related FUV field absorption factor. The
timescale for mantle sublimation (thermal desorption) goes as
ν ice [−][1] [exp (][+] _[E]_ [b] [ /] _[ k T]_ [d] [)] [,] [where] [ν] [ice] [is] [the] [characteristic] [vibrational]
frequency of the solid lattice, _T_ d is the dust grain temperature,
and _E_ b / _k_ is the adsorption binding energy of the species (in K).
Binding energies play a crucial role in model predictions because they determine the freezing temperatures and sublimation
timescales. Table 4 lists the _E_ b / _k_ and _Y_ values considered here.


Article number, page 12 of 25



Representative timescales of the basic grain processes described above are summarized in the upper panel of Fig. 13.
In this plot, _T_ _d_ is a characteristic dust temperature inside the
PDR, _T_ _d_ = (3·10 [4] + 2·10 [3] _G_ [1] 0 [.][2] [)] [0][.][2] [,] [taken] [from] [Hollenbach] [et] [al.]
(2009). In the upper panel, the continuous black curve is the
timescale for a grain to be hit by an H atom ( τ gr, H ). The dashed
magenta curves show the timescale for thermal desorption of
an s-S atom ( τ subl, S ) (left curve for _E_ b / _k_ (S) = 1100 K and right
curve for _E_ b / _k_ (S) = 2600 K ), and the same for an s-O atom (blue
curve). The gray dotted curve is the timescale for s-S atom photodesorption ( τ photodes, S ) at _A_ _V_ = 5 mag. At _G_ 0 strengths where the
continuous line is below the dashed and dotted lines, an adsorbed
s-S atom remains on the grain surface sufficiently long to react
with a diffusing s-H atom, form s-SH, and ultimately s-H 2 S.
Figure 13 shows that, if one takes _E_ b / _k_ (S) = 1100 K (the
most common value in the literature; Hasegawa & Herbst 1993),
the formation of s-H 2 S is possible inside clouds illuminated by
modest FUV fields, when grains are sufficiently cold ( _T_ d < 22 K ).
However, recent calculations of s-S atoms adsorbed on water ice
surfaces suggest higher binding energies ( ∼ 2600 K ; Wakelam
et al. 2017). This would imply that S atoms freeze at higher _T_ d
( ≲ 50 K) and that s-H 2 S mantles form in more strongly illuminated PDRs (the observed _T_ d at the edge of the Bar is ≃ 50 K and
decreases to ≃35 K behind the PDR; see, Arab et al. 2012).
The freeze-out depth for sulfur in a PDR, the _A_ _V_ at which
most sulfur is incorporated as S-bearing solids ( s-H 2 S in our simple model) can be estimated by equating τ gr, S and τ photdes, H 2 S .
This implicitly assumes the H 2 S chemical desorption does not
dominate in FUV-irradiated regions, which is in line with the particularly large FUV absorption cross section of s-H 2 S measured
in laboratory experiments (Cruz-Diaz et al. 2014). With these assumptions, the lower panel of Fig. 13 shows the predicted s-H 2 S
and s-H 2 O freeze-out depths. Owing to the lower abundance and
higher atomic mass of sulfur atoms (i.e., grains are hit slower
by S atoms than by O atoms), the H 2 S freeze-out depth appears
slightly deeper than that of water ice . For the FUV-illumination
conditions in the Bar, the freeze-out depth of sulfur is expected
at _A_ _V_ ≳ 6 mag . This implies that photodesorption of s-H 2 S can
produce enhanced abundances of gaseous H 2 S at _A_ _V_ < 6 mag.
FUV-irradiation and thermal desorption of H 2 S ice mantles
have been studied in the laboratory (e.g., Cruz-Diaz et al. 2014;
Jiménez-Escobar & Muñoz Caro 2011). These experiments show
that pure s-H 2 S ices thermally desorb around 82 K, and at higher

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


Grain, **high** _**E**_ **b** Grain, **low** _**E**_ **b**







**Fig. 14.** Gas-grain PDR models leading to the formation of s-H 2 S (shown as black curves). Continuous colored curves show gas-phase fractional
abundances as a function of depth into the cloud. ϵ refers to the efficiency of the chemical desorption reaction s-H + s-H 2 S → SH + H 2 (see text).
_Left panel_ : Gas-grain high _E_ b model (high adsorption binding energies for S and SH, see Table 4). _Right panel_ : Low _E_ b model.



temperatures for H 2 S–H 2 O ice mixtures. These experiments
determine a photodesorption yield of _Y_ H 2 S ∼ 1.2×10 [−][3] molecules
per FUV photon (see also Fuente et al. 2017). Regarding
surface grain chemistry, experiments show that reaction
s-H + s-SH → s-H 2 S is exothermic (Oba et al. 2018), whereas
reaction s-H + s-H 2 S, although it has an activation energy
barrier of ∼ 1500 K, it may directly desorb gaseous SH. Finally,
reaction s-SH + s-SH → s-H 2 S 2 may trigger the formation of
doubly sulfuretted species, but it requires mobile s-SH radicals
(e.g., Jiménez-Escobar & Muñoz Caro 2011; Fuente et al. 2017) .
Here we will only consider surface reactions with mobile s-H.


_6.3._ _Gas-grain PDR model results_


Here we show PDR model results in which we add a simple network of gas-grain reactions for a small number of S-bearing
(S, SH, and H 2 S) and O-bearing (O, OH, H 2 O, O 2, and CO)
species. These species can adsorb on grains as temperatures drop,
photodesorb by FUV photons (stellar and secondary), desorb
by direct impact of cosmic-rays, or sublimate at a given PDR
depth (depending on _T_ d and on their _E_ b ). Grain size distributions
( _n_ gr ∝ _a_ [−][3][.][5], where _a_ is the grain radius) and gas-grain reactions
are treated within the Meudon code formalism (see, Le Petit et al.
2006; Goicoechea & Le Bourlot 2007; Le Bourlot et al. 2012;
Bron et al. 2014). As grain surface chemistry reactions we include
s-H + s-X → s-XH and s-H + s-XH → s-H 2 X, where s-X refers to
s-S and s-O . In addition, we add the direct chemical desorption reaction s-H + s-SH → H 2 S with an efficiency of 50 % per reactive
event, and also tested different efficiencies ( ϵ ) for the chemical
desorption process s-H + s-H 2 S → SH + H 2 .
In our models we compute the relevant gas-grain timescales
and atomic abundances at every depth _A_ _V_ of the PDR. If the
timescale for a grain to be struck by an H atom ( τ gr, H ) is shorter
than the timescales to sublimate or to photodesorb an s-X atom or
a s-XH molecule; and if H atoms stick on grains more frequently
than X atoms, we simply assume these surface reactions proceed
instantaneously. At large _A_ _V_, larger than the freeze-out depth, this
grain chemistry builds abundant s-H 2 O and s-H 2 S ice mantles.
Figure 14 shows results of two types of gas-grain models. The
only difference between them is the adopted adsorption binding



energies for s-S and s-SH . Left panel is for a “high _E_ b ” model
and right panel is for a “low _E_ b ” model (see Table 4). We note
that these models do not include the gas-phase radiative association reactions S [+] + H 2 → H 2 S [+] + _h_ ν and SH [+] + H 2 → H 3 S [+] + _h_ ν ;
although their effect is smaller than in pure gas-phase models.


The chemistry of the most exposed PDR surface layers
( _A_ _V_ ≲ 2 mag) is the same to that of the gas-phase models discussed in Sect. 6.1. Photodesorption keeps dust grains free of ice
mantles, and fast gas-phase ion-neutral reactions, photoreactions,
and reactions with FUV-pumped H 2 drive the chemistry. The resulting SH [+] abundance profile is nearly identical and there is no
need to invoke depletion of elemental sulfur from the gas-phase
to explain the observed SH [+] emission (see Fig. 15). Beyond these
first PDR irradiated layers, the chemistry does change because
the formation of s-H 2 S on grains and subsequent desorption alters
the chemistry of the other S-bearing hydrides.


In model high _E_ b, S atoms start to freeze out closer to the
PDR edge ( _T_ d < 50 K) . Because of the increasing densities and
decreasing temperatures, the s-H 2 S abundance with respect to H
nuclei reaches ∼ 10 [−][6] at _A_ _V_ ≃ 4 mag. In model low _E_ b, this level
of s-H 2 S abundance is only reached beyond an _A_ _V_ of 7 mag. At
lower _A_ _V_, the formation of s-H 2 S on bare grains and subsequent
photodesorption produces more H 2 S than pure-gas phase models
independently of whether H 2 S chemical desorption is included
or not. In these intermediate PDR layers, at _A_ _V_ ≃ 2-7 mag for the
strong irradiation conditions in the Bar, the flux of FUV photons
drives much of the chemistry, desorbing grain mantles, preventing
complete freeze out, and dissociating the gas-phase products.


There are two H 2 S abundance peaks at _A_ _V_ ≃ 4 and 7 mag . The
H 2 S abundance in these “photodesorption peaks” depends on
the amount of s-H 2 S mantles formed on grains and on the balance between s-H 2 S photodesorption and H 2 S photodissociation
(which now becomes the major source of SH). The enhanced H 2 S
abundance modifies the chemistry of H 2 S [+] and H 3 S [+] as well:
H 2 S photoionization (with a threshold at ∼ 10.4 eV) becomes the
dominant source of H 2 S [+] at _A_ _V_ ≃ 4 mag because the H 2 ( v ≥ 2)
abundance is too low to make reaction (2) competitive. Besides,
reactions of H 2 S with abundant molecular ions such as HCO [+],
H [+]
3 [, and H] [3] [O] [+] [ dominate the H] [3] [S] [+] [ production.]


Article number, page 13 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


**Fig. 15.** Line intensity predictions for different isobaric PDR models. Calculations were carried out in a multi-slab Monte Carlo code (Sect. 4)
that uses the output of the PDR model. Blue stars show the line intensities observed toward the Bar (corrected by beam dilution). _Left panel_ : SH [+]
emission models for PDRs of different _P_ th values and α = 5 _[o]_ . _Right panel_ : SH and H 2 S (adopting an OTP ratio of 3) emission from: high _E_ b (magenta
squares), low _E_ b (gray triangles), and gas-phase (cyan circles) PDR models, all with _P_ th / _k_ = 2 × 10 [8] K cm [−][3] . Upper limit intensity predictions are for
a PDR with an inclination angle of α = 5 _[o]_ with respect to a edge-on geometry. Lower limit intensities refer to a face-on PDR model.



Our gas-grain models predict that other S-bearing molecules,
such as SO 2 and SO, can be the major sulfur reservoirs at these
intermediate PDR depths. However, their abundances strongly depend on those of O 2 and OH through reactions S + O 2 → SO + O
and SO + OH → SO 2 + H (see e.g., Sternberg & Dalgarno 1995;
Fuente et al. 2016, 2019). These reactions link the chemistry of Sand O-bearing neutral molecules (Prasad & Huntress 1982) and
are an important sink of S atoms at _A_ _V_ ≳ 5 mag . However, while
large column densities of OH have been detected in the Orion Bar
( ≳ 10 [15] cm [−][2] ; Goicoechea et al. 2011), O 2 remains undetected
despite deep searches (Melnick et al. 2012). Furthermore, the
inferred upper limit _N_ (O 2 ) columns are below the expectations of
PDR models (Hollenbach et al. 2009). This discrepancy likely implies that these gas-grain models miss details of the grain surface
chemistry leading to O 2 (for other environments and modeling
approaches see, e.g., Ioppolo et al. 2008; Taquet et al. 2016). Here
we will not discuss SO 2, SO, or O 2 further.
At large cloud depths, _A_ _V_ ≳ 8 mag, the FUV flux is largely
attenuated, temperatures drop, the chemistry becomes slower, and
other chemical processes dominate. The H 2 S abundance is controlled by the chemical desorption reaction s-H + s-SH → H 2 S .
This process keeps a floor of detectable H 2 S abundances ( - 10 [−][9] )
in regions shielded from stellar FUV radiation. In addition, and
although not energetically favorable, the chemical desorption
s-H + s-H 2 S → SH + H 2 enhances the SH production at large _A_ _V_
(the enhancement depends on the desorption efficiency ϵ ), which
in turn boosts the abundances of other S-bearing species, including that of neutral S atoms.
The H 2 S abundances predicted by the high _E_ b model reproduce the H 2 S line intensities observed in the Bar (Sect. 6.4) . In
this model s-H 2 S becomes the main sulfur reservoir. However,
we stress that here we do not consider the formation of more
complex S-bearing ices such as s-OCS, s-H 2 S 2, s-S _n_, s-SO 2 or
s-HSO (Jiménez-Escobar & Muñoz Caro 2011; Vidal et al. 2017;
Laas & Caselli 2019). Together with our steady-state solution of
the chemistry, this implies that our predictions are not precise
deep inside the PDR. However, we recall that our observations


Article number, page 14 of 25



refer to the edge of the Bar, so it is not plausible that the model
conditions at _A_ _V_ ≳ 8 mag represent the line of sight we observe.
Model low _E_ b produces less H 2 S in the PDR layers below
_A_ _V_ ≲ 8 mag because S atoms do not freeze until the dust temperature drops deep inside the PDR. Even beyond these layers, thermal desorption of s-S maintains higher abundances of S atoms
at large depths. Indeed, model low _E_ b predicts that the major
sulfur reservoir deep inside the cloud are gas-phase S atoms.
This agrees with recent chemical models of cold dark clouds
(Vidal et al. 2017; Navarro-Almaida et al. 2020).


_6.4._ _Line intensity comparison and H_ 2 _S ortho-to-para ratio_


We now specifically compare the SH [+], SH, and H 2 S line intensities implied by the different PDR models with the intensities
observed toward the DF position of the Bar. We used the output
of the PDR models – _T_ k, _T_ d, _n_ (H 2 ), _n_ (H), _n_ _e_, _n_ (SH [+] ), _n_ (SH), and
_n_ (H 2 S) profiles from _A_ _V_ = 0 to 10 mag – as input for a multi-slab
Monte Carlo model of their line excitation, including formation
pumping (formalism presented in Sect. 4) and radiative transfer.
As the Orion Bar is not a perfectly edge-on, this comparison requires a knowledge of the tilt angle ( α ) with respect to a pure
edge-on PDR. Different studies suggest α of ≈ 5 _[o]_ (e.g., Jansen
et al. 1995; Melnick et al. 2012; Andree-Labsch et al. 2017). This
inclination implies an increase in line-of-sight column density,
compared to a face-on PDR, by a geometrical factor (sin α) [−][1] . It
also means that optically thin lines are limb-brightened.
The left panel of Fig. 15 shows SH [+] line intensity predictions for isobaric PDR models of different _P_ th values (leading
to different _T_ k and _n_ H profiles). Since the bulk of the SH [+] emission arises from the PDR edge ( _A_ _V_ ≃ 0 to 2 mag) all models
(gas-phase or gas-grain) give similar results. The best fit is for
_P_ th ≃ (1–2)×10 [8] cm [−][3] K and α ≃ 5 _[o]_ . These high pressures, at least
close to the DF, agree with those inferred from ALMA images of
HCO [+] ( _J_ = 4-3) emission (Goicoechea et al. 2016), Herschel observations of high- _J_ CO lines (Joblin et al. 2018), and IRAM 30 m
detections of carbon recombination lines (Cuadrado et al. 2019).

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


**Fig.** **16.** Constant density gas-grain PDR models using the high _E_ b chemical network and undepleted sulfur elemental abundances.
_Left panel_ : Effects of changing the FUV radiation field. _Right panel_ : Effects of varying the gas density.



Right panel of Fig. 15 shows SH and H 2 S line emission
predictions for the high _E_ b gas-grain model (magenta squares),
low _E_ b gas-grain model (gray triangles), and a pure gas-phase
model (cyan circles). For each model, the upper limit intensities
refer to radiative transfer calculations with an inclination angle
α = 5 _[o]_ . The lower intensity limits refer to a face-on PDR. Gasphase models largely underestimate the observed H 2 S intensities.
Model low _E_ b produces higher H 2 S columns and brighter H 2 S
lines, but still below the observed levels (by up to a factor of ten).
Model high _E_ b provides a good agreement with observations; the
two possible inclinations bracket the observed intensities, and it
should be considered as the reference model of the Bar. It is also
consistent with the observational SH upper limits.
Our observations and models provide a (line-of-sight)
_N_ ( _o_ -H 2 S)/ _N_ ( _p_ -H 2 S) OTP ratio of 2.9 ± 0.3, consistent with
the (gas-phase) high-temperature statistical equilibrium value.
However, the cold “nuclear-spin-temperatures” ( _T_ spin ≪ _T_ k ; see
definition in eq. D.1 ) implied by the low water vapor OTP ratios
observed in some sources ( < 2.5 ) have been associated with the
temperature of the ice mantles where H 2 O molecules might have
formed (i.e., _T_ spin ≃ _T_ d ; Mumma et al. 1987; Lis et al. 2013) . In
the case of H 2 S, our derived OTP ratio toward the DF position
implies any _T_ spin above 30 ±10 K (see Fig. D.1). Hence, this temperature might be also compatible with s-H 2 S formation [9] in warm
grains if _T_ spin ≃ _T_ d upon formation is preserved in the gas-phase
after photodesorption (e.g., Guzmán et al. 2013). Interestingly,
the H 2 O OTP ratio derived from observations of the Orion Bar is
2.8 ± 0.1 (Putaud et al. 2019) and implies _T_ spin (H 2 O) = 35 ± 2 K .
This value is compatible with _T_ spin (H 2 S) and might reflect the
similar _T_ d of the PDR layers where most s-H 2 O and s-H 2 S form
and photodesorb. Nevertheless, laboratory experiments have chal

9 Crockett et al. (2014) inferred _N_ ( _o_ -H 2 S)/ _N_ ( _p_ -H 2 S) = 2.5 ± 0.8 in the
hot core of Orion KL using LTE rotational digrams. However, they
favored an OTP ratio of 1.7 ± 0.8 based on the column density ratio
of selected pairs of rotational levels with similar energies. This latter
OTP ratio implies _T_ spin (H 2 S) ≃ 12 K (Fig. D.1), perhaps related to much
colder dust grains than in PDRs or to colder gas conditions just before the
hot core phase; so that reactive collisions did not have time to establish
the statistical equilibrium value. We note that the observed OTP ratios of
H 2 CO, H 2 CS, and H 2 CCO in the Bar are also ∼ 3 (Cuadrado et al. 2017).



lenged this _T_ spin ≃ _T_ d association, at least for s-H 2 O : cold water
ice surfaces, at 10 K, photodesorb H 2 O molecules with an OTP
ratio of ∼ 3 (Hama et al. 2016). Follow up observations of _p_ -H 2 S
lines across the Bar will allow us to study possible variations of
the OTP ratio as _G_ 0 diminishes and grains get colder.


_6.5._ _Generalization to different G_ 0 _and n_ H _conditions_


In this section we generalize our results to a broader range of
gas densities and FUV illumination conditions (i.e., to clouds
with different _G_ 0 / _n_ H ratios). We run several PDR models using the high _E_ b gas-grain chemistry. The main difference compared to the Orion Bar models is that here we model constant density clouds with standard interstellar grain properties
( _R_ _V_ = 3.1). Figure 16 (left panel) shows models of clouds with
constant _n_ H = 10 [4] cm [−][3] and varying FUV radiation fields, while
Fig. 16 (right panel) show models of constant FUV illumination ( _G_ 0 = 100) and varying gas densities [10] . The main result of
this study is the similar gas-phase H 2 S column density (a few
10 [14] cm [−][2] up to _A_ _V_ = 10 ) and H 2 S abundance peak (a few 10 [−][8]
close to the FUV-irradiated cloud edge) predicted by these models nearly irrespective of _G_ 0 and _n_ H . A similar conclusion was
reached previously for water vapor in FUV-illuminated clouds
(Hollenbach et al. 2009, 2012) . Increasing _G_ 0 shifts the position
of the H 2 S abundance peak to larger _A_ _V_ until the rate of S atoms
sticking on grains balances the H 2 S photodissociation rate (the
dominant H 2 S destruction mechanism except in shielded gas;
see also Fig.13). Since s-H 2 S photodesorption and H 2 S photodissociation rates depend on _G_ 0, the peak H 2 S abundance in the
PDR is roughly the same independently of _G_ 0 . On the other
hand, the formation rate of s-H 2 S mantles depends on the product _n_ (S) _n_ gr ∝ _n_ [2] H [, whereas the H] [2] [S photodesorption rate depends]
on _n_ gr ∝ _n_ H . Hence, the H 2 S abundance peak moves toward the
cloud surface for denser PDRs (like the Orion Bar). The exact
abundance value depends on the adopted grain-size distribution
and on the H 2 S photodesorption yield (which is well constrained
by experiments; see, Cruz-Diaz et al. 2014; Fuente et al. 2017).


10 In these models we consider undepleted [S/H] abundances and only
the chemical desorption s-H + s-SH → H 2 S (with a 50 % efficiency).


Article number, page 15 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted



The role of chemical desorption increases and can dominate
beyond the photodesorption peak as the flux of stellar FUV photons is attenuated. Here we do not carry out an exhaustive study
of this mechanism, which is hard to model in full detail because
its efficiency decreases considerably with the properties of grain
surfaces (bare vs. icy; see e.g., Minissale & Dulieu 2014). In our
models, and depending on ζ CR, photodesorption by secondary
FUV photons can also be important in cloud interiors. These
processes limit the conversion of most of the sulfur reservoir into
S-bearing ices and increase the abundance of other gas-phase
species deep inside clouds, notably S atoms and H 2 S molecules.
The H 2 S abundance in shielded gas depends on the
destruction rate by gas-phase reactions different than photodissociation, in particular H 2 S reactions with H [+] 3 [. The H] [+] 3 [abundance]
increases with ζ CR and decreases with the electron density. Figure 16 ( _right_ ) shows models of constant _G_ 0 and constant ζ CR
in which the H 2 S abundance at large depths increases with decreasing density (more penetration of FUV photons, more ionization, more electrons, less H [+] 3 [). The lowest gas density model,]
_n_ H = 10 [3] cm [−][3], shows the highest H 2 S abundance at large _A_ _V_ .
Because S freeze-out is less efficient at low densities, the lowdensity model shows higher gas-phase S abundances at large
depths, making atomic S a dominant gas-phase sulfur reservoir.
Unfortunately, direct observation of atomic S in cold gas is complicated, which makes it difficult to benchmark this prediction.
In warm PDRs, in addition to S radio recombination lines
(e.g., Smirnov et al. 1995), the [3] _P_ fine-structure lines of atomic
sulfur, the [S i] 25, 56 µm lines, can be interesting diagnostics of
gas physical conditions and of [S/H] abundances. Unfortunately,
the low sensitivity of previous infrared telescopes was not sufficient to detect the [S i] 25 µ m line ( ∆ _E_ 12 = 570 K ) in the Orion
Bar (Rosenthal et al. 2000) ; although it is detected in protostellar
outflows (e.g., Neufeld et al. 2009; Goicoechea et al. 2012). Moreover, the [3] _P_ 2 - [1] _D_ 2 forbidden line of atomic sulfur at 1.082 µ m can
be an interesting tracer of the ionization and dissociation fronts
in PDRs. Some of these lines will be accesible to high-angularresolution and high sensitivity observations with _JWST_ .


6.5.1. The origin of H 2 S emission in other environments


Irrespective of _n_ H and _G_ 0, grain surface formation of s-H 2 S and
photodesorption back to the gas-phase lead to H 2 S column densities of a few 10 [14] cm [−][2] in PDRs. This is in agrement with the observed column in the Bar ( _G_ 0 ≈ 10 [4] ) as well as at the mildly illuminated rims of TMC-1 and Barnard 1b clouds ( _G_ 0 ≈ 10; NavarroAlmaida et al. 2020). The inferred H 2 S abundance in the shielded
interior of these dark clouds ( _A_ _V_ - 10 mag ) drops to a few 10 [−][9],
but the species clearly does not disappear from the gas ( _N_ (H 2 S)
of a few 10 [13] cm [−][2] ; Navarro-Almaida et al. 2020). Interestingly,
neither in the Bar the H 2 S line emission at ∼ 168 GHz decreases
much behind the PDR (Fig. 1) even if the flux of FUV photons is
largely attenuated compared to the irradiated PDR edge.
Despite oxygen is ∼ 25 times more abundant than sulfur, the
H 2 O to H 2 S column density ratio in the Orion Bar PDR is only
about ∼ 5. This similarity must also reflect the higher abundances
of CO compared to CS. Furthermore, the H 2 S column density
in cold cores is strikingly similar to that of water vapor (Caselli
et al. 2010, 2012). This coincidence points to a more efficient desorption mechanism of s-H 2 S compared to s-H 2 O in gas shielded
from stellar FUV photons. Navarro-Almaida et al. (2020) argues
that chemical desorption is able to reproduce the observed H 2 S
abundance floor if the efficiency of this process diminishes as ice
grain mantles get thicker inside cold dense cores.


Article number, page 16 of 25



Turning back to warmer star-forming environments, our predicted H 2 S abundance in FUV-illuminated gas is comparable
to that observed toward many hot cores ( ∼10 [−][9] -10 [−][8] ; van der
Tak et al. 2003; Herpin et al. 2009). In these massive protostellar environments, thermal desorption of icy mantles, suddenly
heated to _T_ d ≳ 100 K by the luminosity of the embedded massive
protostar, drives the H 2 S production. Early in their evolution,
young hot cores ( ≲ 10 [4] yr) can show even higher abundances
of recently desorbed H 2 S (before further chemical processing
takes place in the gas-phase; e.g., Charnley 1997; Hatchell et al.
1998; Jiménez-Serra et al. 2012; Esplugues et al. 2014). Indeed,

Crockett et al. (2014) reports a gas-phase H 2 S abundance of several 10 [−][6] toward the hot core in Orion KL. This high value likely
reflects the minimum s-H 2 S abundance locked as s-H 2 S mantles
just before thermal desorption. In addition, the H 2 S abundance in
the Orion Bar is only slightly lower than that inferred in protostellar outflows (several 10 [−][8] ) . In these regions, fast shocks erode and
sputter the grain mantles, releasing a large fraction of their molecular content and activating a high-temperature gas-phase chemistry that quickly reprocesses the gas (e.g., Holdship et al. 2019) .
All in all, it seems reasonable to conclude that everywhere s-H 2 S
grain mantles form, or already formed in a previous evolutionary
stage, emission lines from gas-phase H 2 S will be detectable.
In terms of its detectability with single-dish telescopes, H 2 S
rotational lines are bright in hot cores ( _T_ peak, 168 GHz ≃ 30 K in
Orion KL but ≃ 1-3 K toward most hot cores; Tercero et al. 2010;
van der Tak et al. 2003; Herpin et al. 2009), in strongly irradiated
PDRs ( ≃ 6 K, this work), and in lower-illumination PDRs such as
the Horsehead ( ≃ 1 K ; Rivière-Marichalar et al. 2019). The H 2 S
emission is fainter toward cold dark clouds ( ≃ 0.2 K in TMC-1 ;
Navarro-Almaida et al. 2020) and protostellar outflows ( ≃ 0.6 K
in L1157; Holdship et al. 2019). These line intensity differences
are mostly produced by different gas physical conditions and not
by enormous changes of the H 2 S abundance.
Finally, H 2 S is also detected outside the Milky Way (firstly by
Heikkilä et al. 1999). Lacking enough spatial-resolution it is more
difficult to determine the origin of the extragalactic H 2 S emission.
The derived abundances in starburst galaxies such as NGC 253
( ∼ 10 [−][9] ; Martín et al. 2006) might be interpreted as arising from a
collection of spatially unresolved hot cores (Martín et al. 2011) .
However, hot cores have low filling factors at star-forming cloud
scales. Our study suggests that much of this emission can arise
from (the most common) extended molecular gas illuminated by
stellar FUV radiation (e.g., Goicoechea et al. 2019).


**7.** **Summary and conclusions**


We carried out a self-consistent observational and modeling study
of the chemistry of S-bearing hydrides in FUV-illuminated gas .
We obtained the following results:
– ALMA images of the Orion Bar show that SH [+] is confined to
narrow gas layers of the PDR edge, close to the H 2 dissociation
front. Pointed observations carried out with the IRAM 30m
telescope show bright H [32] 2 [S,] [H] [34] 2 [S,] [H] [33] 2 [S] [emission] [toward] [the]
PDR (but no H 3 S [+], a key gas precursor of H 2 S) as well as behind
the Bar, where the flux of FUV photons is largely attenuated.
SOFIA observations provide tight limits to the SH emission.
– The SH [+] line emission arises from a high-pressure gas component, _P_ th ≃ (1–2)×10 [8] cm [−][3] K, where SH [+] ions are destroyed
by reactive collisions with H atoms and electrons (as most H _n_ S [+]
ions do). We derive _N_ (SH [+] ) ≃ 10 [13] cm [−][2] and an abundance peak
of several ∼ 10 [−][9] . H 2 S shows larger column densities toward
the PDR, _N_ (H 2 S) = _N_ ( _o_ -H 2 S) + _N_ ( _p_ -H 2 S) ≃ 2.5×10 [14] cm [−][2] .
Our tentative detection of SH translates into an upper limit

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry



column density ratio _N_ (SH)/ _N_ (H 2 S) of < 0.2-0.6, already
lower than the ratio of 1.1-3.0 observed in low-density diffuse
molecular clouds (Neufeld et al. 2015) . This implies an enhanced
H 2 S production mechanism in FUV-illuminated dense gas.
– All gas-phase reactions X + H 2 (v=0) → XH + H (with X = S [+],
S, SH [+], or H 2 S [+] ) are highly endoergic. While reaction of
FUV-pumped H 2 ( v ≥ 2) molecules with S [+] ions becomes
exoergic and explains the observed levels of SH [+], further
reactions of H 2 ( v ≥ 2) with SH [+] or with neutral S atoms, both
reactions studied here through _ab initio_ quantum calculations, do
not form enough H 2 S [+] or H 3 S [+] to ultimately produce abundant
H 2 S. In particular, pure gas-phase models underestimate the
H 2 S column density observed in the Orion Bar by more than
two orders of magnitude. This implies that these models miss
the main H 2 S formation route. The disagreement is even worse
as we favor, after considering the potential energy surfaces of
the H 2 S [+][∗] and H 3 S [+][∗] complexes, that the radiative associations
S [+] + H 2 → H 2 S [+] + _h_ ν and SH [+] + H 2 → H 3 S [+] + _h_ ν may actually
not occur or possess slower rates than considered in the literature.
– To overcome these bottlenecks, we built PDR models that
include a simple network of gas-grain and grain surface reactions.
The higher binding energies of S and SH suggested by recent
studies imply that bare grains start to grow s-H 2 S mantles not
far from the illuminated edges of molecular clouds. Indeed, the
observed _N_ (H 2 S) in the Orion Bar can only be explained by the
freeze-out of S atoms, grain surface formation of s-H 2 S mantles,
and subsequent photodesorption back to the gas phase. The
inferred H 2 S OTP ratio of 2.9 ± 0.3 (equivalent to _T_ spin ≥ 30 K)
is compatible with the high-temperature statistical ratio as well
as with warm grain surface formation if _T_ spin ≃ _T_ d and if _T_ spin is
preserved in the gas-phase after desorption.
– Comparing observations with chemical and excitation models,
we conclude that the SH [+] -emitting layers at the edge of the
Orion Bar ( _A_ _V_ < 2 mag) are charaterized by no or very little
depletion of sulfur from the gas-phase. At intermediate PDR
depths ( _A_ _V_ < 8 mag) the observed H 2 S column densities do not
require depletion of elemental (cosmic) sulfur abundances either.
– We conclude that everywhere s-H 2 S grain mantles form (or
formed) gas-phase H 2 S will be present in detectable amounts.
Independently of _n_ H and _G_ 0, FUV-illuminated clouds produce
roughly the same H 2 S column density (a few 10 [14] cm [−][2] ) and
H 2 S peak abundances (a few 10 [−][8] ). This agrees with the H 2 S
column densities derived in the Orion Bar and at the edges
of mildly illuminated clouds. Deep inside molecular clouds
( _A_ _V_ - 8 mag), H 2 S still forms by direct chemical desorption and
photodesorption by secondary FUV photons. These processes
alter the abundances of other S-bearing species and makes
difficult to predict the dominant sulfur reservoir in cloud interiors.


In this study we focused on S-bearing hydrides. Still, many
subtle details remain to be fully understood: radiative associations, electron recombinations, and formation of multiply sulfuretted molecules. For example, the low-temperature
(T k < 1000 K) rates of the radiative and dielectronic recombination of S [+] used in PDR models may still be not accurate
enough (Badnell 1991). In addition, the main ice-mantle sulfur reservoirs are not fully constrained observationally. Thus,
some of the narrative may be subject to speculation. Similarly,
reactions of S [+] with abundant organic molecules desorbed from
grains (such as s-H 2 CO, not considered in our study) may contribute to enhance the H 2 S [+] abundance through gas-phase reactions (e.g., S [+] + H 2 CO → H 2 S [+] + CO; Prasad & Huntress 1982) .
Future observations of the abundance and freeze out depths of
the key ice carriers with _JWST_ will clearly help in these fronts.



_Acknowledgements._ We warmly thank Prof. György Lendvay for interesting
discussions and for sharing the codes related to their S( [3] _P_ ) + H 2 ( [1] Σ [+] g [,v)]
PES. We thank Paul Dagdigian, François Lique, and Alexandre Faure for
sharing their H 2 S–H 2, SH [+] –H, and SH [+] –e [−] inelastic collisional rate coefficients and for interesting discussions in Grenoble and Salamanca. We thank
Helgi Hrodmarsson for sending his experimental SH photoionization cross
section in tabulated format. We finally thank our referee, John H. Black,
for encouraging and insightful suggestions. This paper makes use of the
ALMA data ADS/JAO.ALMA#2012.1.00352.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), and NSC and ASIAA (Taiwan), in cooperation
with the Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO, and NAOJ. It also includes IRAM 30 m telescope observations. IRAM is supported by INSU/CNRS (France), MPG (Germany), and
IGN (Spain). We thank the staff at the IRAM 30m telescope and the work of
the USRA and NASA staff of the Armstrong Flight Research Center in Palmdale and of the Ames Research Center in Mountain View (California), and the
Deutsches SOFIA Institut. We thank the Spanish MICIU for funding support
under grants AYA2016-75066-C2-2-P, AYA2017-85111-P, FIS2017-83473-C2
PID2019-106110GB-I00, and PID2019-106235GB-I00 and the French-Spanish
collaborative project PICS (PIC2017FR). We finally acknowledge computing
time at Finisterrae (CESGA) under RES grant ACCT-2019-3-0004.


**References**


Aguado, A., Barragan, P., Prosmiti, R., et al. 2010, J. Chem. Phys., 133, 024306
Aguado, A. & Paniagua, M. 1992, J. Chem. Phys., 96, 1265
Aguado, A., Tablero, C., & Paniagua, M. 2001, Comput. Phys. Comm., 134, 97
Agúndez, M., Goicoechea, J. R., Cernicharo, J., Faure, A., & Roueff, E. 2010,
ApJ, 713, 662
Agúndez, M. & Wakelam, V. 2013, Chemical Reviews, 113, 8710
Allers, K. N., Jaffe, D. T., Lacy, J. H., Draine, B. T., & Richter, M. J. 2005, ApJ,
630, 368
Anders, E. & Grevesse, N. 1989, Geochim. Cosmochim. Acta, 53, 197
Andree-Labsch, S., Ossenkopf-Okada, V., & Röllig, M. 2017, A&A, 598, A2
Anicich, V. G. 2003, JPL Publication 03-19, 1-1194
Arab, H., Abergel, A., Habart, E., et al. 2012, A&A, 541, A19
Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481
Azzam, A. A. A., Yurchenko, S. N., Tennyson, J., Martin-Drumel, M.-A., & Pirali, O. 2013, J. Quant. Spectr. Rad. Transf., 130, 341
Badnell, N. R. 1991, ApJ, 379, 356
Bally, J. 2008, Overview of the Orion Complex, ed. B. Reipurth, 459
Bañares, L., Aoiz, F. J., Honvault, P., Bussery-Honvault, B., & Launay, J.-M.
2003, J. Chem. Phys., 118, 565
Bañares, L., Aoiz, F. J., Honvault, P., & Launay, J.-M. 2004, J. Phys. Chem., 108,
1616
Black, J. H. 1998, Faraday Discussions, 109, 257
Bonnet, L. & Rayez, J.-C. 1997, Chem. Phys. Lett., 277, 183
Bonnet, L. & Rayez, J.-C. 2004, Chem. Phys. Lett., 397, 106
Brittain, A., Coolbroth, K., & Boogert, A. 2020, in American Astronomical Society Meeting Abstracts, Vol. 236, American Astronomical Society Meeting
Abstracts #236, 247.08
Bron, E., Agúndez, M., Goicoechea, J. R., & Cernicharo, J. 2018, ArXiv e-prints
Bron, E., Le Bourlot, J., & Le Petit, F. 2014, A&A, 569, A100
Buckinghan, A. D. 1967, Adv. Chem. Phys., 12, 107
Burton, M. G., Hollenbach, D. J., & Tielens, A. G. G. M. 1990, ApJ, 365, 620
Calmonte, U., Altwegg, K., Balsiger, H., et al. 2016, MNRAS, 462, S253
Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245
Caselli, P., Keto, E., Bergin, E. A., et al. 2012, ApJ, 759, L37
Caselli, P., Keto, E., Pagani, L., et al. 2010, A&A, 521, L29
Charnley, S. B. 1997, ApJ, 481, 396
Choi, Y., van der Tak, F. F. S., Bergin, E. A., & Plume, R. 2014, A&A, 572, L10
Collings, M. P., Anderson, M. A., Chen, R., et al. 2004, MNRAS, 354, 1133
Crockett, N. R., Bergin, E. A., Neill, J. L., et al. 2014, ApJ, 781, 114
Cruz-Diaz, G. A., Muñoz Caro, G. M., Chen, Y. J., & Yih, T. S. 2014, A&A, 562,
A119
Cuadrado, S., Goicoechea, J. R., Cernicharo, J., et al. 2017, A&A, 603, A124
Cuadrado, S., Goicoechea, J. R., Pilleri, P., et al. 2015, A&A, 575, A82
Cuadrado, S., Goicoechea, J. R., Roncero, O., et al. 2016, A&A, 596, L1
Cuadrado, S., Salas, P., Goicoechea, J. R., et al. 2019, A&A, 625, L3
Dagdigian, P. J. 2019, MNRAS, 487, 3427
Dagdigian, P. J. 2019, J. Chem. Phys., 150, 084308
Dagdigian, P. J. 2020, MNRAS, 494, 5239
Dartois, E. 2005, Space Sci. Rev., 119, 293
Davidson, E. R. 1975, J. Comp. Phys., 17, 87
de Graauw, T., Helmich, F. P., Phillips, T. G., et al. 2010, A&A, 518, L6
Desrousseaux, B., Lique, F., Goicoechea, J. R., Quintas-Sánchez, E., & Dawes,
R. 2021, A&A, 645, A8


Article number, page 17 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted



Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016,
Journal of Molecular Spectroscopy, 327, 95
Esplugues, G. B., Cazaux, S., Meijerink, R., Spaans, M., & Caselli, P. 2016,
A&A, 591, A52
Esplugues, G. B., Viti, S., Goicoechea, J. R., & Cernicharo, J. 2014, A&A, 567,
A95
Farah, K., Muller-Plathe, F., & Bohm, M. C. 2012, Chem. Phys. Chem., 13, 1127
Faure, A., Halvick, P., Stoecklin, T., et al. 2017, MNRAS, 469, 612
Freeman, A. & Williams, D. A. 1982, Ap&SS, 83, 417
Fuente, A., Cernicharo, J., Roueff, E., et al. 2016, A&A, 593, A94
Fuente, A., Goicoechea, J. R., Pety, J., et al. 2017, ApJ, 851, L49
Fuente, A., Navarro, D. G., Caselli, P., et al. 2019, A&A, 624, A105
Fuente, A., Rodrıguez-Franco, A., Garcıa-Burillo, S., Martın-Pintado, J., &
Black, J. H. 2003, A&A, 406, 899
Garrod, R. T., Wakelam, V., & Herbst, E. 2007, A&A, 467, 1103
Genzel, R. & Stutzki, J. 1989, ARA&A, 27, 41
Gerin, M., de Luca, M., Black, J., et al. 2010, A&A, 518, L110
Gerin, M., Neufeld, D. A., & Goicoechea, J. R. 2016, ARA&A, 54, 181
Gibb, E. L., Whittet, D. C. B., Boogert, A. C. A., & Tielens, A. G. G. M. 2004,
ApJS, 151, 35
Godard, B. & Cernicharo, J. 2013, A&A, 550, A8
Godard, B., Falgarone, E., Gerin, M., et al. 2012, A&A, 540, A87
Godard, B., Falgarone, E., & Pineau des Forêts, G. 2014, A&A, 570, A27
Goicoechea, J. R., Cernicharo, J., Karska, A., et al. 2012, A&A, 548, A77
Goicoechea, J. R., Cuadrado, S., Pety, J., et al. 2017, A&A, 601, L9
Goicoechea, J. R., Joblin, C., Contursi, A., et al. 2011, A&A, 530, L16
Goicoechea, J. R. & Le Bourlot, J. 2007, A&A, 467, 1
Goicoechea, J. R., Pabst, C. H. M., Kabanovic, S., et al. 2020, A&A, 639, A1
Goicoechea, J. R., Pety, J., Cuadrado, S., et al. 2016, Nature, 537, 207
Goicoechea, J. R., Pety, J., Gerin, M., Hily-Blant, P., & Le Bourlot, J. 2009,
A&A, 498, 771
Goicoechea, J. R., Pety, J., Gerin, M., et al. 2006, A&A, 456, 565
Goicoechea, J. R., Santa-Maria, M. G., Bron, E., et al. 2019, A&A, 622, A91
Gómez-Carrasco, S. & Roncero, O. 2006, J. Chem. Phys., 125, 054102
Graedel, T. E., Langer, W. D., & Frerking, M. A. 1982, ApJS, 48, 321
Grozdanov, T. P. & Solov’ev, E. A. 1982, J. Phys. B, 15, 1195
Guzmán, V. V., Goicoechea, J. R., Pety, J., et al. 2013, A&A, 560, A73
Habart, E., Dartois, E., Abergel, A., et al. 2010, A&A, 518, L116
Habing, H. J. 1968, Bull. Astron. Inst. Netherlands, 19, 421
Hama, T., Kouchi, A., & Watanabe, N. 2016, Science, 351, 65
Hamilton, J. R., Faure, A., & Tennyson, J. 2018, MNRAS, 476, 2931
Hasegawa, T. I. & Herbst, E. 1993, MNRAS, 261, 83
Hatchell, J., Thompson, M. A., Millar, T. J., & MacDonald, G. H. 1998, A&A,
338, 713
He, J., Shi, J., Hopkins, T., Vidali, G., & Kaufman, M. J. 2015, ApJ, 801, 120
Heays, A. N., Bosman, A. D., & van Dishoeck, E. F. 2017, A&A, 602, A105
Heikkilä, A., Johansson, L. E. B., & Olofsson, H. 1999, A&A, 344, 817
Herbst, E., DeFrees, D. J., & Koch, W. 1989, Mon. Not. R. Astyr. Soc., 237, 1057
Herpin, F., Marseille, M., Wakelam, V., Bontemps, S., & Lis, D. C. 2009, A&A,
504, 853
Heyminck, S., Graf, U. U., Güsten, R., et al. 2012, A&A, 542, L1
Hogerheijde, M. R., Jansen, D. J., & van Dishoeck, E. F. 1995, A&A, 294, 792
Holdship, J., Jimenez-Serra, I., Viti, S., et al. 2019, ApJ, 878, 64
Hollenbach, D., Kaufman, M. J., Bergin, E. A., & Melnick, G. J. 2009, ApJ, 690,
1497
Hollenbach, D., Kaufman, M. J., Neufeld, D., Wolfire, M., & Goicoechea, J. R.
2012, ApJ, 754, 105
Hollenbach, D. J. & Tielens, A. G. G. M. 1997, ARA&A, 35, 179
Hosokawa, T. & Inutsuka, S.-i. 2006, ApJ, 646, 240
Howk, J. C., Sembach, K. R., & Savage, B. D. 2006, ApJ, 637, 333
Hrodmarsson, H. R., Garcia, G. A., Nahon, L., Loison, J.-C., & Gans, B. 2019,
Physical Chemistry Chemical Physics (Incorporating Faraday Transactions),
21, 25907
Indriolo, N., Neufeld, D. A., Gerin, M., et al. 2015, ApJ, 800, 40
Ioppolo, S., Cuppen, H. M., Romanzin, C., van Dishoeck, E. F., & Linnartz, H.
2008, ApJ, 686, 1474
Jansen, D. J., Spaans, M., Hogerheijde, M. R., & van Dishoeck, E. F. 1995, A&A,
303, 541
Jiménez-Escobar, A. & Muñoz Caro, G. M. 2011, A&A, 536, A91
Jiménez-Serra, I., Zhang, Q., Viti, S., Martín-Pintado, J., & de Wit, W. J. 2012,
ApJ, 753, 34
Joblin, C., Bron, E., Pinto, C., et al. 2018, A&A, 615, A129
Johnson, B. R. 1987, J. Chem. Phys., 86, 1445
Kaplan, K. F., Dinerstein, H. L., Oh, H., et al. 2017, ApJ, 838, 152
Karplus, M., Porter, R. N., & Sharma, R. D. 1965, J. Chem. Phys., 43, 3259
Kirsanova, M. S. & Wiebe, D. S. 2019, MNRAS, 486, 2525
Klisch, E., Klaus, T., Belov, S. P., et al. 1996, ApJ, 473, 1118
Kłos, J., Lique, F., & Alexander, M. H. 2009, Chemical Physics Letters, 476, 135
Knizia, G., Adler, T. B., & Werner, H. J. 2009, J. Chem. Phys., 130, 054104
Laas, J. C. & Caselli, P. 2019, A&A, 624, A108


Article number, page 18 of 25



Le Bourlot, J., Le Petit, F., Pinto, C., Roueff, E., & Roy, F. 2012, A&A, 541, A76
Le Petit, F., Nehmé, C., Le Bourlot, J., & Roueff, E. 2006, ApJS, 164, 506
Lee, T. A. 1968, ApJ, 152, 913
Leurini, S., Rolffs, R., Thorwirth, S., et al. 2006, A&A, 454, L47
Levine, R. D. & Bernstein, R. B. 1987, Molecular Reaction Dynamics and Chemical Reactivity (Oxford University Press)
Lique, F., Zanchet, A., Bulut, N., Goicoechea, J. R., & Roncero, O. 2020, A&A,
638, A72
Lis, D. C., Bergin, E. A., Schilke, P., & van Dishoeck, E. F. 2013, Journal of
Physical Chemistry A, 117, 9661
Lucas, R. & Liszt, H. S. 2002, A&A, 384, 1054
Maiti, B., Schatz, G. C., & Lendvay, G. 2004, Journal of Physical Chemistry A,
108, 8772
Marconi, A., Testi, L., Natta, A., & Walmsley, C. M. 1998, A&A, 330, 696
Martín, S., Krips, M., Martín-Pintado, J., et al. 2011, A&A, 527, A36
Martín, S., Mauersberger, R., Martín-Pintado, J., Henkel, C., & García-Burillo,
S. 2006, ApJS, 164, 450
Martin-Drumel, M. A., Eliet, S., Pirali, O., et al. 2012, Chemical Physics Letters,
550, 8
Melnick, G. J., Tolls, V., Goldsmith, P. F., et al. 2012, ApJ, 752, 26
Melnick, G. J., Tolls, V., Snell, R. L., et al. 2020, ApJ, 892, 22
Menten, K. M., Wyrowski, F., Belloche, A., et al. 2011, A&A, 525, A77
Millar, T. J., Adams, N. G., Smith, D., Lindinger, W., & Villinger, H. 1986, MNRAS, 221, 673
Millar, T. J. & Herbst, E. 1990, Astron. Astrophys., 231, 466
Millar, T. J. & Herbst, E. 1990, A&A, 231, 466
Minissale, M. & Dulieu, F. 2014, J. Chem. Phys., 141, 014304
Minissale, M., Dulieu, F., Cazaux, S., & Hocuk, S. 2016, A&A, 585, A24
Mumma, M. J., Weaver, H. A., & Larson, H. P. 1987, A&A, 187, 419
Nagy, T. & Lendvay, G. 2017, J. Phys. Chem. Lett., 8, 4621
Nagy, Z., Choi, Y., Ossenkopf-Okada, V., et al. 2017, A&A, 599, A22
Nagy, Z., Van der Tak, F. F. S., Ossenkopf, V., et al. 2013, A&A, 550, A96
Navarro-Almaida, D., Le Gal, R., Fuente, A., et al. 2020, A&A, 637, A39
Neufeld, D. A., Falgarone, E., Gerin, M., et al. 2012, A&A, 542, L6
Neufeld, D. A., Godard, B., Gerin, M., et al. 2015, A&A, 577, A49
Neufeld, D. A., Goicoechea, J. R., Sonnentrucker, P., et al. 2010, A&A, 521, L10
Neufeld, D. A., Nisini, B., Giannini, T., et al. 2009, ApJ, 706, 170
Oba, Y., Tomaru, T., Lamberts, T., Kouchi, A., & Watanabe, N. 2018, Nature
Astronomy, 2, 228
O’Dell, C. R. 2001, ARA&A, 39, 99
Pabst, C., Higgins, R., Goicoechea, J. R., et al. 2019, Nature, 565, 618
Pabst, C. H. M., Goicoechea, J. R., Teyssier, D., et al. 2020, A&A, 639, A2
Palumbo, M. E., Geballe, T. R., & Tielens, A. G. G. M. 1997, ApJ, 479, 839
Pankonin, V. & Walmsley, C. M. 1978, A&A, 64, 333
Parikka, A., Habart, E., Bernard-Salas, J., et al. 2017, A&A, 599, A20
Pellegrini, E. W., Baldwin, J. A., Ferland, G. J., Shaw, G., & Heathcote, S. 2009,
ApJ, 693, 285
Peterson, K. A., Adler, T. B., & Werner, H. J. 2008, J. Chem. Phys., 128, 084102
Pineau des Forets, G., Flower, D. R., Hartquist, T. W., & Dalgarno, A. 1986,
MNRAS, 220, 801
Prasad, S. S. & Huntress, W. T., J. 1980, ApJS, 43, 1
Prasad, S. S. & Huntress, W. T., J. 1982, ApJ, 260, 590
Putaud, T., Michaut, X., Le Petit, F., Roueff, E., & Lis, D. C. 2019, A&A, 632,
A8
Qu, C. & Bowman, J. M. 2016, J. Phys. Chem. A, 120, 4988
Rivière-Marichalar, P., Fuente, A., Goicoechea, J. R., et al. 2019, A&A, 628,
A16
Roelfsema, P. R., Helmich, F. P., Teyssier, D., et al. 2012, A&A, 537, A17
Roncero, O., Zanchet, A., & Aguado, A. 2018, Phys. Chem. Chem. Phys., 20,
25951
Rosenthal, D., Bertoldi, F., & Drapatz, S. 2000, A&A, 356, 705
Sandford, S. A. & Allamandola, L. J. 1988, Icarus, 76, 201
Sanz-Sanz, C., Roncero, O., Paniagua, M., & Aguado, A. 2013, J. Chem. Phys.,
139, 184302
Shiozaki, T. & Werner, H.-J. 2013, Mol. Phys., 111, 607, mRCI-F12
Smirnov, G. T., Sorochenko, R. L., & Walmsley, C. M. 1995, A&A, 300, 923
Smith, R. G. 1991, MNRAS, 249, 172
Sofia, U. J., Lauroesch, J. T., Meyer, D. M., & Cartledge, S. I. B. 2004, ApJ, 605,
272
Stecher, T. P. & Williams, D. A. 1972, ApJ, 177, L141
Sternberg, A. & Dalgarno, A. 1995, ApJS, 99, 565
Stoerzer, H., Stutzki, J., & Sternberg, A. 1995, A&A, 296, L9
Stowe, G. F., Schultz, R. H., Wright, C. A., & Armentrout, P. B. 1990, Int. J.
Mass Spectrom. Ion Proc., 100, 377
Tablero, C., Aguado, A., & Paniagua, M. 2001, Comput. Phys. Comm., 140, 412
Taquet, V., Furuya, K., Walsh, C., & van Dishoeck, E. F. 2016, MNRAS, 462,
S99
Tercero, B., Cernicharo, J., Pardo, J. R., & Goicoechea, J. R. 2010, A&A, 517,
A96

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


Tieftrunk, A., Pineau des Forets, G., Schilke, P., & Walmsley, C. M. 1994, A&A,
289, 579
Tielens, A. G. G. M. 2010, The Physics and Chemistry of the Interstellar Medium
Tielens, A. G. G. M. & Hagen, W. 1982, A&A, 114, 245
Tielens, A. G. G. M. & Hollenbach, D. 1985, ApJ, 291, 722
Tielens, A. G. G. M., Meixner, M. M., van der Werf, P. P., et al. 1993, Science,
262, 86
Turner, B. E. 1996, ApJ, 468, 694
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck,
E. F. 2007, A&A, 468, 627
van der Tak, F. F. S., Boonman, A. M. S., Braakman, R., & van Dishoeck, E. F.
2003, A&A, 412, 133
van der Tak, F. F. S., Nagy, Z., Ossenkopf, V., et al. 2013, A&A, 560, A95
van der Werf, P. P., Goss, W. M., & O’Dell, C. R. 2013, ApJ, 762, 101
van der Werf, P. P., Stutzki, J., Sternberg, A., & Krabbe, A. 1996, A&A, 313, 633
van der Wiel, M. H. D., van der Tak, F. F. S., Ossenkopf, V., et al. 2009, A&A,
498, 161
van Dishoeck, E. F. 2004, ARA&A, 42, 119
Velilla, L., Lepetit, B., Aguado, A., Beswick, J., & Paniagua, M. 2008, J. Chem.
Phys., 129, 084307
Vidal, T. H. G., Loison, J.-C., Jaziri, A. Y., et al. 2017, MNRAS, 469, 435
Wakelam, V., Loison, J. C., Mereau, R., & Ruaud, M. 2017, Molecular Astrophysics, 6, 22
Walmsley, C. M., Natta, A., Oliva, E., & Testi, L. 2000, A&A, 364, 301
Werner, H. J. & Knowles, P. J. 1988a, J. Chem. Phys., 89, 5803
Werner, H. J. & Knowles, P. J. 1988b, Chem. Phys. Lett., 145, 514
Werner, H.-J., Knowles, P. J., Knizia, G., Manby, F. R., & Schütz, M. 2012,
WIREs Comput Mol Sci, 2, 242
Wyrowski, F., Schilke, P., Hofner, P., & Walmsley, C. M. 1997, ApJ, 487, L171
Yamamura, I., Kawaguchi, K., & Ridgway, S. T. 2000, ApJ, 528, L33
Young, E. T., Becklin, E. E., Marcum, P. M., et al. 2012, ApJ, 749, L17
Zanchet, A., Agúndez, M., Herrero, V. J., Aguado, A., & Roncero, O. 2013a, AJ,
146, 125
Zanchet, A., del Mazo, P., Aguado, A., et al. 2018, PCCP, 20, 5415
Zanchet, A., Godard, B., Bulut, N., et al. 2013b, ApJ, 766, 80
Zanchet, A., Lique, F., Roncero, O., Goicoechea, J. R., & Bulut, N. 2019, A&A,
626, A103
Zanchet, A., Roncero, O., González-Lezana, T., et al. 2009, Journal of Physical
Chemistry A, 113, 14488
Zhou, J., Zhao, Y., Hansen, C. S., et al. 2020, Nature Communications, 11, 1547



Article number, page 19 of 25

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


**Appendix A:** **H** **2** **S** [+] **formation and destruction**



In this Appendix we give details about how we calculated the H 2
vibrational-state-dependent rates of reaction (2) and of the reverse
reaction, the destruction of H 2 S [+] ( [2] _A_ [′] ) by reactive collisons with
H ( [2] _S_ ) atoms (summarized in Fig. A.1).
We first built a full dimensional potential energy surface (PES)
of the triplet H 3 S [+] ( [3] _A_ ) system by fitting more than 150,000
_ab initio_ points, including the long range interactions in the reactants and products channels. The main topological features of the
PES are summarized in the minimum energy path between reactants and products (see middle panel of Fig. 9). These _ab initio_
points were calculated with an explicitly correlated restricted
coupled cluster including a single, double, and (perturbatively)
triple excitations (RCCSD(T)-F12a) method (Knizia et al. 2009).
The analytical fit has a overall rms error of ≃ 0.01 eV (Fig. A.2).
Appendix A.1 provides more details.
Reaction (2) is endothermic by 0.672 eV, and the PES of the
triplet state shows two shallow wells in the H 2 + SH [+] entrance
channel (named [3] _W_ 1 _a_ and [3] _W_ 1 _b_, with a depth of ≃ 0.118 eV) and
another one near the H + H 2 S [+] products (named [3] _W_ 2, with a
depth of 0.08 eV). Between the reactants and products wells there
is a saddle point, with an energy of 0.601 eV. This saddle point,
slightly below the products, has a geometry similar to [3] _W_ 2 in
which the H–H distance is strongly elongated compared to that of
H 2 . These features are also present in the maximum multiplicity
PES of reactions H 2 + S [+] ( [4] _S_ ) and H 2 + H 2 S [+] ( [2] _A_ ) (see Fig. 9).
We determine the state-dependent rates of reaction (2) and of the
reverse reaction using a quasi-classical trajectory (QCT) method
on our ground triplet PES. We provide more details on how the
reactive cross sections for fixed collision energies were calculated
in Appendix. A.2.
The formation rate of H 2 S [+] from H 2 (v = 0) is very slow. For
H 2 ( v = 1), the rate constant significantly increases at ≈ 500 K,
corresponding with the opening of the H 2 S [+] + H threshold. At
this point, it is important to consider the zero-point energy (ZPE)
of the products (see next section for details). For H 2 ( v = 2) and
H 2 ( v = 3), reaction rates are faster, close to the Langevin limit.
Finally, the H 2 S [+] destruction rate constant is very similar to that
of its formation from H 2 ( v = 2). In Appendix A.3 we provide
more information about the destruction of H _n_ S [+] ions through
radiative association and spin flip mechanisms.


_Appendix A.1:_ _Ab initio calculations and PES_


Dagdigian (2019) presented a PES for the SH [+] -H 2 system that
includes 4-dimensions and is based on RCCSD(T)-F12a _ab initio_
calculations. This PES was used to study SH [+] –H 2 inelastic collisions using a rigid rotor approach in which the two diatomic
molecules are kept fixed at their equilibrium distances. However,
in order to study the reactivity of the collision, the two diatomic
distances have to be included to account for the breaking and
formation of new bonds.
Reaction (2) corresponds to a triplet state H 3 S [+] ( [3] _A_ ) . The
H 2 S [+] ( [2] _A_ [′] ) + H ( [2] _S_ ) products can form a triplet and a singlet
state. The triplet state can lead to the destruction of H 2 S [+] through
reaction with H atoms. The singlet state, however, produces very
excited states of the reactants. Thus, it only leads to inelastic
collisions but not not to the destruction of H 2 S [+] ( [2] _A_ [′] ). In consequence, here we only consider the ground triplet electronic
state of the system. In addition, the H [+] 3 [+][ S (] [3] _[P]_ [)] [ channel is about]
2.4 eV above the H 2 + SH [+] asymptote, and will not be included
in the present study.


Article number, page 20 of 25



10 [-9]


10 [-10]


10 [-11]











10 [-12]

100 500 900 1300


Temperature (K)


**Fig. A.1.** Calculated rate constants as a function of temperature (for translation and rotation) for SH [+] (v = 0, _j_ = 0) + H 2 (v = 1, 2, 3, _j_ = 0) and
H 2 S [+] (v = 0, _j_ = 0) + H reactions (lavender) using ZPE corrected QCT
method. Dotted curves are fits of the form _k_ ( _T_ ) = α ( _T_ /300) [β] exp( −γ/ _T_ ).
Rate coefficients are listed in Table 1.



0.025


0.020


0.015


0.010


0.005


0.000











140000


120000


100000


80000


60000


40000


20000


0



0 0.5 1 1.5 2 2.5


Energy (eV)


**Fig. A.2.** Rms error as a function of total energy, showing the number of
_ab initio_ points used to evaluate the error in the PES calculation. Arrows
indicate selected critical points in the PES and provide an estimate of
the error in each region. TS means transition state.


In order to study the regions where several electronic states
intersect, we performed a explicitly correlated internally contracted multireference configuration interaction (ic-MRCI-F12)
calculation (Shiozaki & Werner 2013; Werner & Knowles
1988a,b) including the Davidson correction ( icMRCI-F12+Q ;

Davidson 1975). The ic-MRCI-F12 calculations were carried out
using state-averaged complete active space self-consistent field
(SA-CASSCF) orbitals with all the CAS configurations as the
reference configuration state functions. We used a triple zeta correlation consistent basis set for explicitly correlated wave functions
( cc-pVTZ-F12 ; Peterson et al. 2008). In order to avoid orbital
flipping between core and valence orbitals. SA-CASSCF calcula

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry



tions with three lowest triplet states were carried out including
the core and valence orbitals as active space (18 electrons in 11
orbitals). For the ic-MRCI-F12 calculation, the core orbitals was
kept doubly occupied, resulting in about 2 . 5 × 10 [6] (9 × 10 [7] ) contracted (uncontracted) configurations. All _ab initio_ calculations
were performed with MOLPRO (Werner et al. 2012).
Our ic-MRCI-F12 calculations show that the crossings with
electronic excited states are 2 eV above the energy of the reactants. The energy interval below 2 eV is enough to study
reaction 2 . In these low-energy regions, RCCSD(T)-F12a calculations were also performed. They are in good agreement with
the ic-MRCI-F12 results and the t 1 diagnostic is always below
0.03. This allows us to conclude that for energies below 2 eV, the
RCCSD(T)-F12a method performs well, presents a simple convergence, and being size consistent, is well adapted to the present
case. This method is the same one employed in the inelastic
collision calculations by Dagdigian (2019).
We performed extensive RCCSD(T)-F12a calculations in all
accessible regions to properly describe the six-dimensional phase
space. 150000 _ab initio_ points were fitted to a multidimensional
analytic function, that generates the six-dimensional PES represented as


_H_ = _H_ _[diab]_ + _H_ _[MB]_ (A.1)


(Aguado et al. 2010; Sanz-Sanz et al. 2013; Zanchet et al. 2018;
Roncero et al. 2018), where _H_ _[diab]_ is an electronic diabatic matrix
in which each diagonal matrix element describes a rearrangement
channel – six in this case, three equivalent for SH [+] + H 2 channels,
and three equivalent for H 2 S [+] + H fragments (we omitted the
H [+] 3 [+][ S] [channel)] [–] [as] [an] [extension] [of] [the] [reactive] [force] [field]
approach (Farah et al. 2012). In each diagonal term, the molecular
fragments (SH [+], H 2 and H 2 S [+] ) are described by 2 or 3 body fits
(Aguado & Paniagua 1992), and the interaction among them
is described by a sum of atom-atom terms plus the long range
interaction. The non diagonal terms of _H_ _[diab]_ are described as
previously (Zanchet et al. 2018; Roncero et al. 2018) and the
parameters are fitted to approximately describe the saddle points
along the minimum energy path in the right geometry.
In the reactants channel, the leading long range interaction
SH [+] ( _X_ [3] Σ [−] ) + H 2 ( _X_ [1] Σ [+] g [) corresponds to charge-quadrupole and]
charge-induced dipole interactions (Buckinghan 1967):


_V_ charge( **r** _HH_, **R** ) = Θ 2 ( _r_ _HH_ ) _P_ 2 (cos θ 2 ) _R_ [−][3]


1
− [1] �α ∥ ( _r_ _HH_ ) − α ⊥ ( _r_ _HH_ )� _P_ 2 (cos θ 2 ) _R_ [−][4] (A.2)
� 2 [α] [0] [(] _[r]_ _[HH]_ [)][ +] 3 �


and the dipole-quadrupole interactions (Buckinghan 1967):


_V_ dipole( **r** _S H_, **r** _HH_, **R** ) = 3µ 1 ( _r_ _S H_ )Θ 2 ( _r_ _HH_ )

× �cos θ 1 _P_ 2 (cos θ 2 ) + sin θ 1 sin θ 2 cos θ 2 cos φ� _R_ −4, (A.3)


where Θ 2 ( _r_ _HH_ ) is the cuadrupole moment of H 2 ( _X_ [1] Σ [+] g [),] [ α] [0] [(] _[r]_ _[HH]_ [),]
α ∥ ( _r_ _HH_ ), and α ⊥ ( _r_ _HH_ ) are the average, parallel, and perpendicular polarizabilities of H 2 ( _X_ [1] Σ [+] g [), respectively, and] [ µ] [1] [(] _[r]_ _[S H]_ [) is the]
dipole moment of SH [+] ( _X_ [3] Σ [−] ). _P_ 2 ( cos θ ) represents the Legendre polynomial of degree 2. The dependence of the molecular
properties of H 2 with the interatomic distance _r_ _HH_ is obtained
from Velilla et al. (2008). The dipole moment of SH [+] depends
on the origin of coordinates. Since SH [+] ( _X_ [3] Σ [−] ) dissociates in
S [+] ( [4] _S_ ) + H ( [2] _S_ ), we select the origin of coordinates in the _S_ atom,
so that the dipole moment tends to zero when R goes to infinity.
In the products channel, the long range interaction
H 2 S [+] ( _X_ [2] _A_ [′′] ) + H ( [2] _S_ ) corresponds to the isotropic charge


**Table A.1.** RCCSD(T)-F12a and fit stationary points on the PES.


Stationary point Geometry Energy/cm [−][1] Energy/eV
Reactants SH ~~[+]~~ + H 2 0.0 0.0
Minimum 1 SH [+] − H 2 −950.2 −0.1178
TS12 SH [+] - · H 2 −579.5 −0.0719
Minimum 2 SH [+] − H 2 −937.9 −0.1163
TS13 SH [+] - · H ·· H 4843.9 0.6006
Minimum 3 H 2 S [+] − H 4766.5 0.5910
Products H 2 S [+] + H 5422.3 0.6723


**Table A.2.** _E_ v of reactants and products, and adiabatic switching energies
for the QCT initial conditions.


System(vibration) Exact _E_ v (eV) AS energy (eV)
H 2 (v = 0) 0.270 0.269
H 2 (v = 1) 0.786 0.785
H 2 (v = 2) 1.272 1.272
H 2 (v = 3) 1.735 1.730
SH [+] (v = 0) 0.157 0.157
H 2 S [+] (v = 0) 0.389 0.388


induced dipole and charge-induced quadrupole dispersion terms



These long range terms diverge at _R_ =0. To avoid this behavior,
we replace _R_ by R:


R = _R_ + _R_ 0 _e_ [−][(] _[R]_ [−] _[R]_ _[e]_ [)] with _R_ 0 = 10 bohr.


In Eq. (A.1), _H_ _[MB]_ is the many-body term, which is described
by permutationaly invariant polynomials following the method
of Aguado an collaborators (Aguado & Paniagua 1992; Tablero
et al. 2001; Aguado et al. 2001). This many-body term improves
the accuracy of the PES, especially in the region of the reaction
barriers (as shown in Fig. 9). Features of the stationary points are
listed in Table A.1.


_Appendix A.2:_ _Determination of reactive collision rates_


We studied the reaction dynamics using a quasi-classical trajectory (QCT) method with the code miQCT (Zanchet et al. 2018;
Roncero et al. 2018). In this method, the initial vibrational energy of the reactants is included using the adiabatic switching
method (AS) (Grozdanov & Solov’ev 1982; Johnson 1987; Qu
& Bowman 2016; Nagy & Lendvay 2017). Energies are listed
in Table A.2. The initial distance between the center-of-mass
of the reactants ( H 2 + SH [+] or H 2 S [+] + H ) is set to 85 bohr, and
the initial impact parameter is set randomly within a disk, the
radius of which is set according to a capture model (Levine &
Bernstein 1987) using the corresponding long-range interaction.
The orientation among the two reactants is set randomly.
A first exploration of the reaction dynamics is done at
fixed collision energy, for H 2 (v = 0, 1, 2, 3) + SH [+] (v = 0) and
H + H 2 S [+] (v = 0), and the reactive cross section is calculated as in
Karplus et al. (1965)


σ v _j_ ( _E_ ) = π _b_ [2] _max_ _[P]_ _[r]_ [(] _[E]_ [)] with _P_ _r_ ( _E_ ) = _[N]_ _[r]_, (A.4)

_N_ _tot_


Article number, page 21 of 25




[9]

4 _[R]_ [−][4] [ −] [15] 4



_V_ disp( _R_ ) = − [9]



4 _[R]_ [−][6] [.]

10000


1000


100


10


1


0.1


0.01









_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


15


10


5



0.001

|H 2(v=3) + SH+<br>H 2(v=2) + SH+<br>H 2(v=1) + SH+<br>H 2(v=0) + SH+<br>H 2S+(0,0,0)+H|Col2|
|---|---|
|H2(v=3) + SH+<br>H2(v=2) + SH+<br>H2(v=1) + SH+<br>H2(v=0) + SH+<br>H2S+(0,0,0)+H||
|H2(v=3) + SH+<br>H2(v=2) + SH+<br>H2(v=1) + SH+<br>H2(v=0) + SH+<br>H2S+(0,0,0)+H||
|H2(v=3) + SH+<br>H2(v=2) + SH+<br>H2(v=1) + SH+<br>H2(v=0) + SH+<br>H2S+(0,0,0)+H||
|H2(v=3) + SH+<br>H2(v=2) + SH+<br>H2(v=1) + SH+<br>H2(v=0) + SH+<br>H2S+(0,0,0)+H||
|H2(v=3) + SH+<br>H2(v=2) + SH+<br>H2(v=1) + SH+<br>H2(v=0) + SH+<br>H2S+(0,0,0)+H||


0.1 1 10 100 1000


Collision energy (meV)


**Fig.** **A.3.** Reaction cross section (in bohr [2] ) as a function of collision
energy (in meV) for the SH [+] (v = 0, _j_ = 0) + H 2 (v = 1, 2, 3, _j_ = 0) and
H 2 S [+] (v = 0, _j_ =0) + H collisions. Filled symbols are obtained counting
all trajectories leading to products, while open symbols correspond to
the ZPE corrected ones.


where _N_ _t_ is the maximum number of trajectories with initial impact parameter lower than _b_ _max_, the maximum impact parameter
for which the reaction takes place, and _N_ _r_ is the number of trajectories leading to products. Fig. A.2 shows results for _N_ _t_ - 20000
and all energies and initial reactant and vibrational states.
For the SH [+] (v = 0, _j_ = 0) + H 2 (v, _j_ = 0) reaction there is a
strong dependence on the initial vibrational state. For H 2 ( v = 0),
there is nearly no reactive event, and only at 1 eV there are some
reactive trajectories. For H 2 ( v = 2 and 3), however, the reaction
shows a relatively large cross section, that decreases with increasing collision energy, as expected for exoergic reactions. Energies
below 10-100 meV are dominated by long range interactions,
leading to an increase in the maximum impact parameter, _b_ _max_,
consistent with the variation of the cross section.

Reaction SH [+] (v = 0, _j_ = 0) + H 2 (v = 1, _j_ = 0) shows an unexpected behavior that deserves some discussion. At energies below
40 meV, the cross section is large and decreases with increasing
energy. In the 40-200 meV range, the reactive cross section drops
to zero, showing a threshold at 200 meV that is consistent with
the endothermicity of the reaction.
In order to analyze the reaction mechanism for H 2 ( v = 1)
below 40 meV, we carried out an extensive analysis of the trajectories. A typical one is presented in Fig. A.4 for 10 meV. The
H 2 and SH [+] reactants are attracted to each other by long range
interactions, until they get trapped in the [3] _W_ 1 wells, as it is shown
by the evolution of _R_, the distance between center-of-mass of the
two molecules. The trapping lasts for 8 ps, thus allowing several
collisions between H 2 and SH [+] and permitting the energy transfer
between them. The H 2 molecule ultimately breaks, and leaves
SH [+] with less vibrational energy. This can be inferred from the
decrease in the amplitudes of the SH [+] distance. The energy of the
H 2 S [+] product is below the ZPE (see Table A.2). This is a clear
indication of ZPE leakage in the QCT method, due to the energy
transfer promoted by the long-lived collision complex.
Several methods exist that correct the ZPE leakage. One is
the gaussian binning (Bonnet & Rayez 1997, 2004; Bañares et al.
2003, 2004). Here we have applied a simplification of this method,


Article number, page 22 of 25



0

0 2 4 6 8 10 12 14


time (ps)


**Fig. A.4.** H-H, SH [+] and _R_ distances (in bohr) versus time (in ps), for
a typical reactive trajectory for the SH [+] (v = 0, _j_ = 0) + H 2 (v = 1, _j_ =0)
collision at 10 meV.


which assigns a weight (w) for each trajectory as


1 for _E_ v _ib_      - _ZPE_
w =, (A.5)
� _e_ [−][γ][(] _[E]_ [v] _[ib]_ [−] _[ZPE]_ [)] [2] for _E_ v _ib_ < _ZPE_


where _E_ v _ib_ is the vibrational energy of reactants (adding those
of H 2 and SH [+] ) or H 2 S [+] products at the end of each trajectory.
These new weights are used to calculate _N_ _r_ and N _tot_ in Eq. A.4.
ZPE-corrected results are shown in Fig. A.3 with open symbols.
This plot shows that all values are nearly the same as those calculated simply by counting trajectories as an integer (as done in the
normal binning method; see filled symbols in Fig. A.3). The only
exception is the case of SH [+] + H 2 (v = 1) below 400 meV, which
becomes zero when considering the ZPE of fragments at the end
of the trajectories.
The reaction thermal rate in specific initial vibrational state of
reactants are calculated running a minimum of 10 [5] trajectories per
temperature, with fixed vibrational states of reactants, assuming a
Boltzmann distribution over translational and rotational degrees
of freedom, and following the ZPE-corrected method as:



_k_ v ( _T_ ) =



8 _k_ _B_ _T_

π _b_ [2] _max_ [(] _[T]_ [)] _P_ _r_ ( _T_ ). (A.6)

~~�~~ πµ



The results of these calculations are shown in Fig. A.1.


_Appendix A.3:_ _On the radiative associations of H_ _n_ _S_ [+]


Herbst et al. (1989) and Millar & Herbst (1990) proposed that the
radiative association H _n_ S [+] + H 2 → H _n_ +1 S [+] + _h_ ν is viable process at low gas temperatures. Although this chemical route is
widely used in astrochemical models, here we question the viability of this process. The lower multiplicity (L) PESs of H 2 S [+] ( [2] _A_ [′′] )
and H 3 S [+] ( [1] _A_ ) are L = 1/2 and 0 respectively. These are shown in
Fig. 9, together with the minimum multiplicity electronic state
of H 4 S [+] (bottom panel). This state does not have a deep well or
any higher multiplicity state that could connect to higher states
of reactants and products.
For of H 3 S [+] formation through radiative association, this process assumes that a H 3 S [+] ( [3] _A_ ) [∗] complex forms in a triplet state, the

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry



high spin state H considered here. According to our calculations,
such a complex is formed after low-energy H 2 (v = 0, 1) + SH [+]
reactions (below 40 meV). The complex is formed in the [3] _W_ 1
well, corresponding to geometries very far from those of the low
spin well, the [1] _W_ well. Therefore, a radiative spin flip and decay
through phosphorescence is not possible. Herbst et al. (1989)
proposed a second step, in which the spin flips from the triplet
to the singlet state, followed by a radiative association, finally
leading to the H 3 S [+] ( [1] _A_ ) product.
The origin of the spin flip must be the spin-orbit couplings,
very relevant for S-bearing species, that favor the spin transition
when singlet and triplet states are close in energy. Using the PESs
calculated here, the lowest crossing region is at ≃ 0.25 eV, very
close to that of H 2 ( v = 0). At low temperatures, the H 3 S [+] ( [3] _A_ ) [∗]
complex formed by H 2 (v = 0) + SH [+] reactions might allow a
transition between the two electronic states with different spin.
However, the spin flip probability is proportional to the square of
the overlap |⟨H 3 S [+] ( [3] _A_ ) [∗] | H 3 S [+] ( [1] _A_ ) [∗] ⟩| [2] . This probability is very
small because the two wells, [3] _W_ 1 and [1] _W_ 1, correspond to very
different geometries. In consequence, we conclude that this radiative association mechanism must be negligible, especially at
the high gas temperatures of PDR edges where the H 3 S [+] ( [3] _A_ ) [∗]
complex is not formed.
As an alternative, a spin flip in a direct collision (not forming a H 3 S [+] ( [3] _A_ ) [∗] complex) may be more efficient and should be
further investigated. Indeed, experimental measurements of the
S [+] ( [4] _S_ ) + H 2 (v = 0) cross section show a maximum at about 1 eV
of collisional energy attributed to spin-orbit transitions leading to
spin flip (Stowe et al. 1990).


**Appendix B:** **Reaction** **S (** **[3]** **P)** + **H** **2** **(** _**v**_ **)** ⇄ **SH** + **H**


This reaction involves open shell reactants, S ( [3] _P_ ), and products,
SH ( [2] Π) . Neglecting spin flipping, there are three states that correlate to S( [3] _P_ ), two of them connect to the SH ( [2] Π). These two electronic states are of [3] _A_ [′] and [3] _A_ [′′] symmetry, and have been studied
in detail by Maiti et al. (2004). Here we use the adiabatic PES calculated by Maiti et al. (2004). Reaction S + H 2 → SH + H is endothermic by ≃ 1.02 eV (without zero-point energy corrections),
very similar to the endothermicity of reaction S [+] + H 2 → SH [+] + H
(Zanchet et al. 2013a, 2019). The main difference is the presence
of a barrier, of ≃ 78 meV ( ≃ 905 K ) with respect to the SH + H
asymptote.
We performed quantum wave packet calculations for the reactions S + H 2 (v = 2, 3, _j_ =0) and SH (v = 0, _j_ =0) + H . We used
MADWAVE3 (Gómez-Carrasco & Roncero 2006; Zanchet et al.
2009) to calculate the reaction probabilities for the initial vibrational state of the diatomic reactant (in the ground state rotational
state, _j_ = 0). We employed the usual partial wave expansion to
calculate the reaction cross section. We calculated only few total
angular momenta of the triatomic system, _J_ = 0, 10 and 20 . The
other _J_ needed in the partial wave expansion were obtained using
the _J_ -shifting-interpolation method (see Zanchet et al. 2013a).
The initial-state-specific rate constants are obtained by numerical
integration of the cross section using a Boltzmann distribution
(Zanchet et al. 2013a). The resulting reaction rate constants are
shown in Figs. B.1 and B.2. The numerical values of the rate constants are fitted to the usual analytical Arrhenius-like expresion
(shown as dotted curves). We note that the shoulder in the rate
constants of reaction SH (v=0) + H requires two functions in the
temperature range of 200-800 K . Rate coefficients are tabulated
in Table 1.



10 [-12]


10 [-13]


100 500 900 1300


Temperature (K)


**Fig. B.2.** Calculated rate constants as a function of temperature for reaction SH (v=0) + H → S + H 2 . The best fit to the calculated rate requires
two Arrhenius-like expressions (one for low temperatures and one for
high temperatures). Rate coefficients of these fits are listed in Table 1.


Article number, page 23 of 25



10 [-11]


10 [-12]





10 [-13]

100 500 900 1300


Temperature (K)


**Fig.** **B.1.** Calculated rate constants as a function of temperature for
reaction S( [3] _P_ ) + H 2 (v) → SH + H . Dotted curves are fits of the form
_k_ ( _T_ ) = α ( _T_ /300) [β] exp(−γ/ _T_ ). Rate coefficients are listed in Table 1.


10 [-11]

_A&A proofs:_ manuscript no. aa_sulfur_bar_accepted


**Appendix C:** **SH and H** **2** **S photoionization and**
**photodissociation cross sections**


Figure C.1 shows the experimental SH and H 2 S photoionization
and photodissociation cross sections (cm [−][2] ) used in our PDR
models. We integrate these cross sections over the specific FUV
radiation field at each _A_ _V_ depth of the PDR to obtain the specific
photoionization and photodissociation rates (s [−][1] ).


**Fig. D.1.** OTP ratio of H 2 S as a function of spin temperature (eq. D.1).


**Fig.** **C.1.** Photoionization and photodissociation cross sections.
_Top panel_ : σ ion (SH) (blue curve from laboratory experiments by Hrodmarsson et al. 2019). The pink curve is σ diss (SH) (Heays et al. 2017, and
references therein). _Bottom panel_ : σ ion (H 2 S) (blue curve) and σ diss (H 2 S)
(gray and pink curves; from Zhou et al. 2020).


**Appendix D:** **H** **2** **S ortho-to-para ratio and** _**T**_ **spin**


The OTP ratio is sometimes related to a nuclear-spin-temperature
( _T_ spin, e.g., Mumma et al. 1987) defined, for H 2 O or H 2 S, as:


[�] [(2] _[J]_ [ +][ 1) exp(][−] _[E]_ _[o]_ [(] _[J]_ [)][/] _[T]_ [spin] [)]
OTP = [3] � (2 _J_ + 1) exp(− _E_ _p_ ( _J_ )/ _T_ spin ) . (D.1)


Here, _E_ _o_ ( _J_ ) and _E_ _p_ ( _J_ ) are the energies (in Kelvin) of _o_ -H 2 S and
_p_ -H 2 S rotational levels (with the two ground rotational states
separated by ∆ _E_ = 19.8 K). Figure D.1 shows the OTP ratio of the
two H 2 S nuclear spin isomers as a function of _T_ spin . The OTP ratio
we infer toward the DF position of the Bar, 2.9 ± 0.3, is consistent
with the statistical ratio of 3/1, and implies _T_ spin ≥ 30 ± 10 K.


**Appendix E:** **Line parameters of IRAM 30m, ALMA,**
**and SOFIA observations**


Article number, page 24 of 25

Goicoechea et al.: Bottlenecks to interstellar sulfur chemistry


**Table E.1.** Parameters of H 2 S and H [34] 2 [S lines detected with the IRAM 30 m telescope toward three positions of the Orion Bar.]



Position Species Transition Frequency _E_ u /k _A_ ul _S_ ul g u



_T_ mb dv v LSR ∆v _T_ mb
�



_J_ _K_ a, _K_ c [GHz] [K] [s [−][1] ] [K km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [K]

(+10, −10) _o_ -H 2 S 1 1,0 – 1 0,1 168.763 8.1 2.68 × 10 [−][5] 1.5 3 18.32 (0.01) 10.5 (0.1) 2.5 (0.1) 7.03

_o_ -H [34] 2 [S] 1 1,0 – 1 0,1 167.911 8.1 2.62 × 10 [−][5] 1.5 3 1.22 (0.01) 10.5 (0.1) 2.0 (0.1) 0.57

_p_ -H 2 S 2 2,0 – 2 1,1 216.710 84.0 4.87 × 10 [−][5] 2.2 5 0.35 (0.01) 10.4 (0.1) 2.1 (0.1) 0.16

(+30, −30) _o_ -H 2 S 1 1,0 – 1 0,1 168.763 8.1 2.68 × 10 [−][5] 1.5 3 17.16 (0.02) 10.3 (0.1) 2.4 (0.1) 6.85

_o_ -H [34] 2 [S] 1 1,0 – 1 0,1 167.911 8.1 2.62 × 10 [−][5] 1.5 3 1.28 (0.01) 10.4 (0.1) 1.9 (0.1) 0.63

(+35, −55) _o_ -H 2 S 1 1,0 – 1 0,1 168.763 8.1 2.68 × 10 [−][5] 1.5 3 3.57 (0.02) 9.6 (0.1) 3.1 (0.1) 1.08

_o_ -H [34] 2 [S] 1 1,0 – 1 0,1 167.911 8.1 2.62 × 10 [−][5] 1.5 3 0.18 (0.02) 9.8 (0.1) 2.7 (0.3) 0.06


**Notes.** Parentheses indicate the uncertainty obtained by the Gaussian fitting programme.


**Table E.2.** Parameters of SH [+] targeted with ALMA toward the DF position.



Position Species Transition Frequency _E_ u /k _A_ ul



_T_ mb dv v LSR ∆v _T_ mb
�




[GHz] [K] [s [−][1] ] [K km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [K]


(+10, −10) SH [+] _N_ _J_ =1 0 -0 1 _F_ =1/2-1/2 345.858 16.6 1.14×10 [−][4] 0.36 _[a]_ (0.03) 10.7 (0.2) 2.7 (0.3) 0.12

SH [+] _N_ _J_ =1 0 -0 1 _F_ =1/2-3/2 _[b]_ 345.944 16.6 2.28×10 [−][4] 0.70 _[a]_ (0.03) 10.4 (0.1) 2.5 (0.1) 0.26


**Notes.** _[a]_ Integrated over a 5 [′′] aperture to increase the S/N of the line profiles. _[b]_ Line integrated intensity map shown in Fig. 3.


**Table E.3.** Parameters of SH lines (neglecting HFS) targeted with SOFIA toward the DF position.



Position Species Transition Frequency _E_ u /k _A_ ul



_T_ mb dv v LSR ∆v _T_ mb
�




[GHz] [K] [s [−][1] ] [K km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [K]

(+10, −10) SH 2 Π 3/2 _J_ =5/2 + –3/2 − 1382.911 66.4 4.72 × 10 [−][3] <1.11 _[a]_ (0.20) 12.1 _[a]_ (0.8) 7.9 _[a]_ (1.3) 0.16

SH 2 Π 3/2 _J_ =5/2 − –3/2 + 1383.242 66.4 4.72 × 10 [−][3] <0.34 (0.12) 11.7 (0.5) 2.3 (0.8) 0.14


**Notes.** _[a]_ Uncertain fit.


Article number, page 25 of 25


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "Search for SH 2Π_3/2 lines at ~1383 GHz (project 07_0115).",
  "failed_quote": "We finally used the GREAT receiver (Heyminck et al. 2012) on board the Stratospheric Observatory For Infrared Astronomy (SOFIA; Young et al. 2012) to search for the lowestenergy rotational lines of SH"
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Solve statistical equilibrium and nonlocal radiative transfer with a Monte Carlo code including chemical formation pumping and destruction rates, dust continuum radiation, and inelastic collisions with H2, H, and e-.",
  "failed_quote": "In这些cases, a proper treatment of the molecule excitation requires including chemical formation and destruction rates in the statistical equilibrium equations (d n i / d t = 0) that determine the level populations"
 }
]
```
