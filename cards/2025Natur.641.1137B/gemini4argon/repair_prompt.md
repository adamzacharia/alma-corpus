# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025Natur.641.1137B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## Quasar radiation transforms the gas in a merging companion galaxy

Sergei Balashev [1*] **[†]**, Pasquier Noterdaeme [2,3*] **[†]**, Neeraj Gupta [4],
Jens-Kristian Krogager [3,5], Francoise Combes [6], Sebastián López [7],
Patrick Petitjean [2], Alain Omont [2], Raghunathan Srianand [4],
Rodrigo Cuellar [7]


1 Department of Theoretical Astrophysics, Ioffe Institute, Politechnicheskaya
ul., 26, Saint-Peterburg, 194021, Russia.
2 Institut d’Astrophysique de Paris, CNRS-SU, UMR 7095, 98bis bd Arago,
75014 Paris, France.
3 French-Chilean Laboratory for Astronomy, IRL 3386, CNRS and Universidad
de Chile, Casilla 36-D, Santiago, Chile.
4 Inter-University Centre for Astronomy and Astrophysics, Post Bag 4,
Ganeshkhind, 411 007, Pune, India.
5 Centre de Recherche Astrophysique de Lyon, UMR 5574, Université Lyon I,
ENS de Lyon, CNRS, F-69230 Saint-Genis-Laval, Lyon, France.
6 Collège de France, PSL University, Sorbonne University, CNRS, LERMA,
Observatoire de Paris, 61 avenue de l’Observatoire, 75014, Paris, France.
7 Departamento de Astronomía, Universidad de Chile, Casilla 36-D, Santiago,
Chile.


*Corresponding author(s). E-mail(s): s.balashev@gmail.com;
noterdaeme@iap.fr;

**†** These authors contributed equally to this work.


**Quasars,** **powered** **by** **gas** **accretion** **onto** **supermassive** **black** **holes,** **[1,2]** **rank** **among** **the**
**most energetic objects of the Universe.** **[3,4]** **While they are thought to be ignited by galaxy**
**mergers** **[5,6,7,8,9,10,11]** **and affect the surrounding gas,** **[12,13,14,15]** **observational constraints**
**on** **both** **processes** **remain** **scarce.** **[16,17,18]** **Here** **we** **unveil** **a** **major** **merging** **system** **at**
**redshift** _𝑧_ ≈ 2 _._ 7 **, and demonstrate that radiation from the quasar in one galaxy directly**
**alters the gas properties in the other galaxy. Our findings reveal that the galaxies, with**


1

**centroids** **separated** **by** **only** **a** **few** **kiloparsecs** **and** **approaching** **each** **other** **at** **speed**
≈ 550 **km s** [−][1] **,** **are** **massive,** **form** **stars,** **and** **contain** **a** **substantial** **molecular** **mass.** **Yet,**
**dusty molecular gas seen in absorption against the quasar nucleus is highly excited and**
**confined** **within** **cloudlets** **with** **densities** ∼ 10 [5] **-** 10 [6] **cm** [−][3] **and** **sizes** _<_ **0.02** **pc,** **several**
**orders** **of** **magnitude** **more** **compact** **than** **those** **observed** **in** **intervening** **(non-quasar)**
**environments.** **This** **is** **also** **approximately** **10** [5] **times** **smaller** **than** **currently** **resolvable**
**through** **molecular-line** **emission** **at** **high** **redshifts.** **We** **infer** **that,** **wherever** **exposed** **to**
**the quasar radiation, molecular gas is disrupted, leaving behind surviving dense clouds**
**too** **small** **to** **give** **birth** **to** **new** **stars.** **Our** **results** **not** **only** **underscore** **the** **role** **of** **major**
**galaxy mergers in triggering quasar activity, but also reveal localized negative feedback**
**as a profound alteration of internal gas structure which likely hampers star formation.**


We combine unique millimeter and optical observations of the quasar
J 012555.11−012925.00 to investigate its galactic environment and directly assess the impact
of its intense radiation on the physical state and small-scale structure of the molecular gas
observed in absorption. [19] In Fig. 1, we show that even though the optical image (a) is dominated by the overwhelming quasar light, a careful subtraction of the quasar’s point spread
function reveals the presence of a companion galaxy and a structure extending around over
more than 20 kpc in visible light (b). Our high spatial resolution ALMA observations of the
dense molecular component (d) reveal that the centroids of the two galaxies –quasar host and
companion– are separated by only ∼0.7 arcsec on the plane of the sky, that is, a physical projected distance of about 5 kpc at redshift _𝑧_ syst = 2 _._ 6618. The companion galaxy has a slightly
higher apparent redshift than the quasar host-galaxy, with a line-of-sight velocity relative to
the quasar, obtained from the CO(7-6) emission lines, of about 550 km s [−][1] (e, f and g).
The use of different slit orientations during X-shooter observations allowed us to extract
both the quasar (PA=0 [◦] and PA=90 [◦] ) and the companion galaxy (PA=90 [◦] ) optical spectra.
A key observation is the presence of strong absorptions by ionised, neutral and molecular
gas in the quasar spectrum, at the redshift of the companion galaxy (as shown in panel g in
Fig. 1 and in Fig. 2). The companion galaxy must therefore be situated in the foreground,
showing that the objects are also approaching each other, indicating a merging scenario. In
addition, the absorption lines conveniently remove the otherwise outshining light from the
quasar central engine, acting like a coronagraph which reveals emission from the host galaxy
at various wavelengths. This is seen as a spatially resolved residual in the trough of saturated
metal and molecular hydrogen absorption lines (see Methods). Remarkably, the damped Ly_𝛼_ absorption due to neutral gas from the companion galaxy enables the detection of Ly- _𝛼_
emission extending from the location of the quasar host to that of the companion galaxy (in
both spatial and velocity spaces, panel c in Fig. 1). This implies the presence of gas spread
over several tens of kpc, an expected characteristic of merging systems, where material is
stretched by tidal forces generated by strong gravitational interactions between the galaxies.
In order to infer the main properties of both galaxies we modelled their spectral energy
distribution using constraints on the ultraviolet (UV), optical and mm emission, see Fig. 3.
We found that the companion and quasar host galaxies are both massive, with stellar masses
close to 10 [11] _𝑀_ ⊙, indicative of a major event (as opposed to minor merger when one galaxy is
much more massive than the other one). This might have enhanced the star-formation activity
in the companion galaxy, located above the main-sequence of galaxies at this redshift. [20] The
molecular masses derived from the CO emission lines are of the order of 10 [10] _𝑀_ ⊙ for both


2

ALMA CO(7-6) integrated emission map



Subaru HSC _g_ -band









21°28'50" 48" RA 46" 44"


Subaru HSC _g_ -band, quasar subtracted





















21°28'50" 48" RA 46" 44"


Ly _α_ from X-shooter 2d spectrum

|Col1|Col2|
|---|---|
|PA=90o||



3 2 1 0 −1 −2 −3

Spatial offset [arcsec]



















200 0 −200 −400 −600

Velocity relative to reference redshift z=2.6618 [km s [−1] ]



**Fig. 1** : **Optical and millimeter observations of the quasar-host companion-galaxy system.**
**a**, The Subaru HSC _𝑔_ -band image is dominated by the emission from the quasar but the
companion galaxy is clearly seen ∼ 1 arcsec to the East, after subtraction of the quasar point
spread function ( **b** ). Contours from the ALMA CO(7-6) emission map (blue and red) are
superimposed, as well as the layout of the X-shooter slits. **d**, The integrated CO(7-6) emission
with ALMA, with contours from 5 with 20 mJy beam [−][1] km s [−][1] step. The hatch ellipse depicts
the beam size, the white cross represents the centroid of g-band emission from HSC. **e**, **f**, The
velocity maps at the location of the companion and the quasar host, respectively. **c**, The 2D Xshooter spectrum with slit position angle=90 [◦], where the quasar light is naturally suppressed
by strong absorption by H i gas, providing direct access to the extended Ly- _𝛼_ emission from
merging galaxies. The red dotted and blue dashed lines denote the centroids of the ALMA CO
emission of the companion and quasar host galaxies, respectively, in both spatial and velocity
space, with the stripes indicating their velocity spread. **g**, The CO and CI integrated velocity
profiles with the absorption profiles of metal lines in the 1D X-shooter spectrum of the quasar.
The error bars represent the 1 _𝜎_ standard deviation of the flux measurements.


3

**Table 1** : **Main properties of the merging galaxies.**


Quantity Companion galaxy Quasar host galaxy


redshift 2 _._ 663 ± 0 _._ 001 2 _._ 656 ± 0 _._ 001


approaching velocity ∼ 550 km s [−][1]


projected distance ∼ 5 kpc


log _𝑀_ SMBH / _𝑀_ ⊙ – 8 _._ 3 ± 0 _._ 4

log _𝑀_ ∗ / _𝑀_ ⊙ 10 _._ 84 [+] − [0] 0 _[.]_ _._ [12] 12 10 _._ 7 [+] − [0] 0 _[.]_ _._ [3] 3
log _𝑀_ H 2 / _𝑀_ ⊙ 10 _._ 00 [+] − [0] 0 _[.]_ _._ [05] 05 9 _._ 74 [+] − [0] 0 _[.]_ _._ [07] 09
log _𝑀_ dust / _𝑀_ ⊙ 8 _._ 2 [+] − [0] 0 _[.]_ _._ [5] 3 _<_ 8 _._ 5

SFR [ _𝑀_ ⊙ yr [−][1] ] 250 [+] − [60] 50 ≳ 24 [+] − [17] 11


the companion galaxy and that hosting the quasar. We also constrained the mass of the super
massive black hole (SMBH) that powers the quasar to be about 10 [8] _𝑀_ ⊙ from the emission line
width and continuum measurements. Given the (5 − 10) × 10 [46] erg s [−][1] luminosity, the quasar
must be actively accreting matter and radiating at the Eddington limit. The main properties of
the galaxies and the quasar are summarized in Table 1.
Towards the quasar, we measure the total column density of atomic hydrogen _𝑁_ (H i) ≈
10 [21] _[.]_ [8] cm [−][2] (50 M ⊙ pc [−][2] ). This high value, which falls in the upper range expected for most
high-redshift galaxies (such as those probed by intervening systems) even given the small
impact parameter, [21,22,23,24] may arise from material stretched by tidal forces during galaxy
interactions. Moreover, low-ionisation metal absorption lines (see Fig. 2) indicate that the
neutral gas is kinematically distributed over ∼ 400 km s [−][1] (roughly coinciding with the velocity
dispersion of the CO profile, see panel g of Fig. 1) and has a metallicity which is about one
tenth of the Solar value, i.e. consistent with modest chemical enrichment in the companion
- as opposed to high enrichment expected in the quasar’s host. [25] The high velocity spread,
especially given the metallicity, [26] indicates disturbed kinematics, as expected if arising from
a merging system.
The absorbing gas also presents one of the highest H 2 column densities ( _𝑁_ (H 2 ) ≈
10 [21] _[.]_ [2] cm [−][2] ) ever directly detected in quasar spectra, [27,28] distributed across two main velocity
components. But the true exceptional nature of the H 2 gas is to be appreciated in its excitation
diagram, shown in Fig. 4: the molecular gas presents unusual population of H 2 vibrationalrotational levels, with excitation temperatures far exceeding those typically observed in our
Galaxy or intervening systems. [29,30] Notably, we detect, for the first time in absorption at high
redshift, lines from the first excited vibrational state, with energy levels at _𝐸_ ≳ 4000 cm [−][3] .
The excitation observed here is even stronger than what is seen in photo-dissociation regions
very close to bright, recently formed stars. [31]

Modelling the excitation of H 2 with the `Meudon` `PDR` code, we infer the UV field to be
about a thousand times stronger than the average Milky-Way field. Comparing the quasar
luminosity with the derived incident UV flux constrains the absorbing gas to be within at most
a few kpc from the quasar (right panel of Fig. 4), similar to the transverse distance between
the host and companion galaxy, in line with the merging scenario.
In addition, the presence and the excitation of H 2 constrains the gas density to be _𝑛_ H ∼
10 [5] − 10 [6] cm [−][3] . This very high number density is supported by the high excitation of neutral
carbon in three fine-structure levels and is further confirmed by the tentative detection of CO


4

**Fig. 2** : **Absorption lines in the spectrum of the quasar J 012555.11** − **012925.00.**
Selected portions of the 1D VLT/X-shooter spectrum of the quasar around absorption lines
(marked by text labels) from gas within the galaxy system are shown in black, with error
bars representing the 1 _𝜎_ standard deviation of the flux measurements. The absorption models
and their associated uncertainties are colored red, violet, green, and gray (representing total
absorption, H 2 -bearing components, and other components, respectively). The blue shaded
region in ( **a** ) indicates the reconstructed quasar continuum. The horizontal lines with vertical
ticks in **b** and **c** indicate the position of individual H 2 absorption lines from different vibrational
bands marked with text labels on the left. The host galaxy emission is seen as faint residual
emission (green) that is not fully absorbed in lines from the merging galaxy system but
remains affected by intervening Lyman- _𝛼_ forest lines from the intergalactic medium, which is
structured on much larger scales.


absorption, which also requires high density to remain detectable under a strong UV field.
The high density and measured column density imply that the molecular clouds are very
compact, with sizes, _𝐿_ ≈ _𝑁_ / _𝑛_ H (assuming constant density) of less than 0.02 pc. Remarkably,
the molecular clouds are then smaller than the expected light beam from the quasar emission
line regions, covering only the even much smaller accretion disc. This is independently
confirmed by differential dust-reddening between the quasar continuum emission and the
emission line regions. The presence of dust around a luminous quasar is also consistent with
galaxy interactions. [34,35]

The inferred cloud densities are several orders of magnitude higher than those in intervening H 2 -bearing systems (i.e. far from the quasar), where values _𝑛_ H ∼ 10 [2] cm [−][3] are usually
seen. Under normal conditions, cloud densities follow a continuous log-normal distribution, [36] implying that low-density molecular clouds ∼ 10 [2] cm [−][3] should outnumber those with
_𝑛>_ 10 [5] cm [−][3] by several orders of magnitude. While we detect high-density molecular clouds,
we find no evidence of lower-density ones. This, combined with the high incident UV flux,
indicates that the bulk of the diffuse molecular gas exposed to the quasar radiation has been


5

3


2







1


0









1


0





4000 6000 8000 10000 12000 14000 16000 18000
Observed wavelength [Å]


**Fig. 3** : **Spectral energy distribution of the companion and quasar-host galaxies.**
**a**, companion. **b**, quasar-host. The data (black line and colored points) are shown together with
the model fit (red and blue shaded regions). The error bars represent 0.683 credible intervals
and the standard error of the mean in panels **a** and **b**, respectively. The top panel also indicates
the HSC photometric data in g and r bands obtained after PSF subtraction of the quasar.
The vertical gray stripes indicate the telluric absorptions. **c, d** The mm-range constrained by
ALMA data.



photo-dissociated (within timescales of several years for the constrained UV flux), and only
the high density regions survived the intense radiation field.
We further note that while the interception of one molecular cloud by the quasar line of
sight is enforced by our selection on the presence of molecular hydrogen absorption lines, [19]

the detection of a second cloud (we detect H 2 in two distinct velocity components separated
by ∼60 km s [−][1] ) suggests that the total surface covering factor cannot be extremely small. On
the other hand, the low average reddening of the background quasar’s emission line regions
disfavors a high covering fraction of dusty gas over this area. Overall, the volume filling factor
of the molecular gas in the region exposed to the quasar radiation should hence be at most of
the order of _𝑟_ / _𝐿_, where _𝑟_ is the size of a molecular cloud and _𝐿_ is the kpc-scale path-length
across the absorbing galaxy. We infer that the region exposed to the UV radiation from the
accretion disk, i.e. a few kpc across at this distance from the quasar, is very clumpy with dense
molecular gas surviving in no more than 10 [−][5] of the volume. This in line with the growing
observational and theoretical evidence that different gas phases in different environments may
actually follow a fog-like structure, [37] being confined within cloudlets much smaller than the
overall extent of the medium. [38] In our case, the surviving clumps have masses _<_ 0 _._ 1 _𝑀_ ⊙ so that
they cannot form stars, when the remaining of the companion galaxy, outside the anisotropic
quasar radiation field, forms stars at a high pace.
Our findings reveal that we are not only observing an ongoing major merger event, supporting such mechanism as important feeding mechanism for quasars, but also, for the first


6

20


19


18


17


16


15


14


13


12

















**Fig. 4** : **H** 2 **excitation diagram and physical conditions in H** 2 **-bearing medium.**
**a,** The population of H 2 ro-vibrational levels (circles for the zero vibrational level and squares
for the first vibrational level) as a function of the energy of these levels. The values observed
towards J 012555.11−012925.00 (purple and green for two velocity components) are compared
to the excitation seen in intervening systems (grey) [29] and to an extreme excitation case in a
Galactic system towards a runaway O star (orange). [31] The error bars represent 0.683 credible
intervals. The purple and green solid lines represent the best fit models of H 2 excitation with
`Meudon` `PDR` code. **b,** The constraints on the number density, n, of the absorbing molecular
gas and its distance, d, from the quasar, derived from modelling the observed H 2 excitation
using the `Meudon` `PDR` code (green and violet solid lines). The solid contours represent 0.683
credible interval of the 2d posterior distribution. The panel also includes constraints from C i
levels (green dashed line), CO abundance (red dotted line), and the HI/H 2 transition (gray
dashed-dotted line). The 1D marginalized constraints are shown along the top and right axes
of **b** . For comparison, distributions in intervening quasar absorption systems [32] and in the
Magellanic Clouds [33] are shown as gray and orange histograms, respectively.


time, documenting dramatic feedback effects on the internal structure of the gas at unprecedented scales – 10 [5] times smaller than directly resolvable through emission studies at high
redshifts. Specifically, we have shown that the gas within this system is being transformed
into a highly clumpy medium wherever exposed to the intense UV radiation powered by the
actively accreting supermassive black hole. This quasar disrupts the molecular gas in a manner
analogous to the impact of newborn stars on their parent molecular clouds.

### **References**


1 Antonucci, R. Unified models for active galactic nuclei and quasars. _Annu. Rev. Astron._
_Astrophys._ **31**, 473–521 (1993).


2 Netzer, H. Revisiting the Unified Model of Active Galactic Nuclei. _Annu._ _Rev._ _Astron._
_Astrophys._ **53**, 365–408 (2015).


7

3 Wu, X.-B. _et_ _al._ An ultraluminous quasar with a twelve-billion-solar-mass black hole at
redshift 6.30. _Nature_ **518**, 512–515 (2015).


4 Wolf, C. _et al._ The accretion of a solar mass per day by a 17-billion solar mass black hole.
_Nature Astronomy_ **8**, 520–529 (2024).


5 Volonteri, M., Haardt, F. & Madau, P. The Assembly and Merging History of Supermassive
Black Holes in Hierarchical Models of Galaxy Formation. _Astrophys._ _J._ **582**, 559–573
(2003).


6 Hopkins, P. F., Hernquist, L., Cox, T. J. & Kereš, D. A Cosmological Framework for the
Co-Evolution of Quasars, Supermassive Black Holes, and Elliptical Galaxies. I. Galaxy
Mergers and Quasar Activity. _Astrophys. J. Suppl. Ser._ **175**, 356–389 (2008).


7 Ellison, S. L., Patton, D. R., Mendel, J. T. & Scudder, J. M. Galaxy pairs in the Sloan
Digital Sky Survey - IV. Interactions trigger active galactic nuclei. _Mon._ _Not. R. Astron._
_Soc._ **418**, 2043–2053 (2011).


8 Trakhtenbrot, B. _et al._ ALMA Observations Show Major Mergers Among the Host Galaxies
of Fast-growing, High-redshift Supermassive Black Holes. _Astrophys. J._ **836**, 8 (2017).


9 Decarli, R. _et al._ Rapidly star-forming galaxies adjacent to quasars at redshifts exceeding
6. _Nature_ **545**, 457–461 (2017).


10 Goulding, A. D. _et_ _al._ Galaxy interactions trigger rapid black hole growth: An unprecedented view from the Hyper Suprime-Cam survey. _Publ._ _Astron._ _Soc._ _Jpn_ **70**, S37
(2018).


11 Fogasy, J., Knudsen, K. K., Drouart, G., Lagos, C. D. P. & Fan, L. SMM J04135+10277: a
distant QSO-starburst system caught by ALMA. _Mon. Not. R. Astron. Soc._ **493**, 3744–3756
(2020).


12 Hopkins, P. F. & Elvis, M. Quasar feedback: more bang for your buck. _Mon. Not. R. Astron._
_Soc._ **401**, 7–14 (2010).


13 Dubois, Y. _et_ _al._ The HORIZON-AGN simulation: morphological diversity of galaxies
promoted by AGN feedback. _Mon. Not. R. Astron. Soc._ **463**, 3948–3964 (2016).


14 Pontzen, A. _et al._ How to quench a galaxy. _Mon. Not. R. Astron. Soc._ **465**, 547–558 (2017).


15 Moiseev, A. V. & Smirnova, A. A. Ionizing Spotlight of Active Galactic Nucleus. _Galaxies_
**11**, 118 (2023).


16 Fabian, A. C. Observational Evidence of Active Galactic Nuclei Feedback. _Annu._ _Rev._
_Astron. Astrophys._ **50**, 455–489 (2012).


17 Hirschmann, M., Somerville, R. S., Naab, T. & Burkert, A. Origin of the antihierarchical
growth of black holes. _Mon. Not. R. Astron. Soc._ **426**, 237–257 (2012).


8

18 Tang, S. _et_ _al._ Morphological asymmetries of quasar host galaxies with Subaru Hyper
Suprime-Cam. _Mon. Not. R. Astron. Soc._ **521**, 5272–5297 (2023).


19 Noterdaeme, P. _et al._ Proximate molecular quasar absorbers. Excess of damped H 2 systems
at z _𝑎𝑏𝑠_ ≈ z _𝑄𝑆𝑂_ in SDSS DR14. _Astron. Astrophys._ **627**, A32 (2019).


20 Popesso, P. _et al._ The main sequence of star-forming galaxies across cosmic times. _Mon._
_Not. R. Astron. Soc._ **519**, 1526–1544 (2023).


21 Rahmati, A. & Schaye, J. Predictions for the relation between strong HI absorbers and
galaxies at redshift 3. _Mon. Not. R. Astron. Soc._ **438**, 529–547 (2014).


22 Noterdaeme, P. _et al._ A connection between extremely strong damped Lyman- _𝛼_ systems
and Lyman- _𝛼_ emitting galaxies at small impact parameters. _Astron. Astrophys._ **566**, A24
(2014).


23 Krogager, J. K., Møller, P., Fynbo, J. P. U. & Noterdaeme, P. Consensus report on 25 yr
of searches for damped Ly _𝛼_ galaxies in emission: confirming their metallicity-luminosity
relation at z ≳ 2. _Mon. Not. R. Astron. Soc._ **469**, 2959–2981 (2017).


24 Krogager, J.-K. _et al._ High-redshift damped Ly _𝛼_ absorbing galaxy model reproducing the
N _𝐻𝐼_ - Z distribution. _Mon. Not. R. Astron. Soc._ **495**, 3014–3021 (2020).


25 Di Matteo, T., Croft, R. A. C., Springel, V. & Hernquist, L. The Cosmological Evolution
of Metal Enrichment in Quasar Host Galaxies. _Astrophys. J._ **610**, 80–92 (2004).


26 Ledoux, C., Petitjean, P., Fynbo, J. P. U., Møller, P. & Srianand, R. Velocity-metallicity
correlation for high-z DLA galaxies: evidence of a mass-metallicity relation? _Astron._
_Astrophys._ **457**, 71–78 (2006).


27 Balashev, S. A. _et al._ CO-dark molecular gas at high redshift: very large H 2 content and
high pressure in a low-metallicity damped Lyman alpha system. _Mon. Not. R. Astron. Soc._
**470**, 2890–2910 (2017).


28 Ranjan, A. _et al._ Molecular gas and star formation in an absorption-selected galaxy: Hitting
the bull’s eye at z ≃ 2.46. _Astron. Astrophys._ **618**, A184 (2018).


29 Balashev, S. A. _et al._ X-shooter observations of strong H 2 -bearing DLAs at high redshift.
_Mon. Not. R. Astron. Soc._ **490**, 2668–2678 (2019).


30 Shull, J. M., Danforth, C. W. & Anderson, K. L. A Far Ultraviolet Spectroscopic Explorer
Survey of Interstellar Molecular Hydrogen in the Galactic Disk. _Astrophys._ _J._ **911**, 55
(2021).


31 Boissé, P. _et al._ A far UV study of interstellar gas towards HD 34078: High excitation H 2
and small scale structure. _Astron. Astrophys._ **429**, 509–523 (2005).


32 Balashev, S. A. & Noterdaeme, P. Molecular hydrogen in absorption at high redshifts.


9

_Experimental Astronomy_ **55**, 223–239 (2023).


33 Kosenko, D. N., Balashev, S. A. & Klimenko, V. V. Cold diffuse interstellar medium of
Magellanic Clouds: II. Physical conditions from excitation of C I and H 2 . _Mon._ _Not._ _R._
_Astron. Soc._ **528**, 5065–5079 (2024).


34 Urrutia, T., Lacy, M. & Becker, R. H. Evidence for Quasar Activity Triggered by Galaxy
Mergers in HST Observations of Dust-reddened Quasars. _Astrophys. J._ **674**, 80–96 (2008).


35 Glikman, E. _et al._ Major Mergers Host the Most-luminous Red Quasars at z ~2: A Hubble
Space Telescope WFC3/IR Study. _Astrophys. J._ **806**, 218 (2015).


36 Hennebelle, P. & Falgarone, E. Turbulent molecular clouds. _Astron. Astrophys. Rev._ **20**,
55 (2012).


37 McCourt, M., Oh, S. P., O’Leary, R. & Madigan, A.-M. A characteristic scale for cold
gas. _Mon. Not. R. Astron. Soc._ **473**, 5407–5431 (2018).


38 Arav, N., Barlow, T. A., Laor, A. & Blandford, R. D. Keck high-resolution spectroscopy
of MRK 335: constraints on the number of emitting clouds in the broad-line region. _Mon._
_Not. R. Astron. Soc._ **288**, 1015–1021 (1997).


10

### **Methods**

Throughout this work, we use AB magnitudes [39] and a standard ΛCDM cosmology with
H 0 = 70 km s [−][1] Mpc [−][1], Ω Λ = 0 _._ 7, and Ω _𝑚_ = 0 _._ 3.


**Observations**


We performed UV-to-NIR spectroscopy of J 012555.11−012925.00 with X-shooter on the
Very Large Telescope at Paranal, obtaining five (three and two) ≈ 1 hour exposures with two
different orientations of position angle PA=90 [◦] and 0 [◦], respectively. Observations and data
reduction down to the 2D spectrum are described in the survey paper. [40] Here, we constructed
the skyline solution with a two-degree polynomial fit along the spatial axis, avoiding the quasar
and companion galaxy traces (∼ 0 _._ 7 arcsec above the quasar) as well as the edges of the 2D
spectrum. For each exposure, we then extracted the one-dimensional quasar spectrum using
a Moffat profile, whose parameters (central position and width) were obtained over a large
wavelength range while masking cosmic rays and regions containing light from the companion
galaxy. Finally, we rescaled and combined all exposures from the different X-shooter arms
into a single quasar spectrum.
We obtained ALMA band 3 and band 6 data through project 2022.1.01792.S, see Supplementary Table 1. Typically, 42 - 44 antennas participated in observations, and both the
parallel hand correlations were recorded. For band 3, the correlator setup allowed four spectral windows (SPWs) labelled as 23, 25, 27 and 29, centered at 108.794, 94.812, 96.806
and 106.868 GHz, respectively. The SPW 23 with a bandwidth of 2 GHz divided into 128
frequency channels was used to map the radio continuum. The other three SPWs covering
1.875 GHz with 480 channels were tuned to search for redshifted CO(3-2), HCO [+] and CS
spectral lines. For band 6, four spectral windows, i.e., SPW 21, 23, 25 and 27 were centered
at 232.652, 234.569, 218.401 and 220.506 GHz, respectively. The SPWs 21 - 23 and 25 - 27
covered 2 GHz and 1.875 GHz split into 128 and 240 frequency channels, respectively. The
main objective was to detect redshifted CO(7-6) and C i(2-1) associated with the quasar in
SPW 27. ALMA data were processed using the ALMA pipeline following standard procedures and `robust` `=` `0.5` weighting of visibilities. [41] The spectral line cubes properties are
summarized in Extended Data Table 1.


**Global properties of the galaxies**


We derived the main global properties of the quasar host and companion galaxies using
emission constraints from our X-shooter and ALMA data, supplemented with Subaru Hyper
Suprime Cam (HSC) deep imaging.


**Broad-band photometry**


We retrieved deep _𝑟_ and _𝑔_ band images of the field from the Hyper Suprime-Cam Legacy
Archive 2016 [42] (Extended Data Fig. 1). We fitted them with the Galfit package [43] using a
model consisting of a Point Spread Function (PSF) source (representing the quasar), a sky
background, and two additional Sérsic profiles with index = 1.0, with free position, effective
radius, axis ratio, and orientation. We obtain _𝑔_ = 23 _._ 41 ± 0 _._ 05 and _𝑟_ = 23 _._ 16 ± 0 _._ 04 for the


11

main Sérsic source, east of the quasar emission. The second, fainter Sérsic component has
_𝑔_ = 24 _._ 74 ± 0 _._ 07 and _𝑟_ = 26 _._ 2 ± 0 _._ 9 and extends southwest.


**X-shooter spectrum of the companion galaxy**


The companion galaxy’s emission is located above the quasar trace in the 2D spectra taken
with position angle PA=90 [◦] . To disentangle this faint emission from that of the quasar, we
rebinned each exposure onto a coarser grid corresponding to 200 pixels (40 Å) for UVB and
VIS arms, and 800 pixels (480 Å) for the NIR arm due to sky contamination and weaker fluxes
in this region. This was done by subtracting the sky model, summing the 2D spectrum along
the spectral axis in each bin, while removing pixels impacted by cosmic rays and strong sky
lines. We then fitted the observed collapsed profiles using two Moffat functions (determined
by peak position, width, and normalization), representing the quasar and companion galaxy
(Extended Data Fig. 2). We followed Bayesian inference by sampling the model parameters
using a Python implementation of an affine invariant Monte-Carlo Markov Chain (MCMC)
sampler [44] within the `emcee` package. [45] For normalization parameters, we used flat priors. For
the position and width along the spatial axis, we used Gaussian priors centered at 0” and the
seeing value for the quasar component. For the companion galaxy component, our priors are
based on the results from the broad-band image fitting: the position is taken to be 0.55" from
the quasar and the width is taken as the quadratic sum of the unresolved quasar component
(i.e. the seeing measured at each wavelength) plus the 0.9"-width derived from Galfit. The
derived Moffat profiles were used to compute and correct for slit losses at each wavelength,
considering the slit widths of 1.0, 0.9 and 1.2" for UVB, VIS and NIR arms, respectively.
The companion spectrum shown in the top panel of Fig. 3 was then obtained by combining
the three individual exposures using the inverse-variance weighted mean. The photometric
points obtained using PSF extraction from HSC Subaru imaging are consistent with this

spectrum.


**The quasar host galaxy as residual emission in saturated absorption lines**


We constrained the quasar host galaxy emission from residual light in the dark troughs of
heavily saturated absorption lines (Ly _𝛼_, Si ii 1260 Å, O i 1302 Å, C ii 1334 Å, Al ii 1260 Å and
series of H 2 and Fe ii lines) in the quasar spectrum. The 2D spectrum (Extended Data Fig. 3)
shows that this residual emission is aligned with the unresolved quasar trace and remains
similar regardless of the position angle, indicating that it comes mainly from the quasar host
galaxy, covered by both slit positions, not from the companion galaxy (covered by the slit at
PA=90 [◦] but not at PA=0 [◦] ). Residual emission is also seen in the blue part of the spectrum, as a
non-zero level in saturated H 2 absorption lines. However, this emission is absent in the troughs
of strong Ly _𝛼_ forest lines, which fully absorb light from the background objects (quasar,
host and companion galaxies) due to their origin in large-scale intergalactic structures. This
confirms that the residual flux in the _𝑧_ = 2 _._ 66 lines is real and not a data reduction artifact.
The constraints on the quasar host galaxy spectrum (bottom panel of Fig. 3) were derived by
combining all five exposures, each extracted using a Moffat profile along the quasar trace to
minimize any contribution from the companion galaxy.


12

**Millimetre line and continuum emission**


The ALMA cubes were blindly searched for line emission using the H i Source Finding
Application `SOFIA` `v2.0` . [46,47] We set `SOFIA` to subtract the residual continuum and use the
smooth+clip (S+C) algorithm with a combination of spatial and spectral kernels matched to
the expected signal size in a given band. We set the threshold to 3.5 _𝜎_ for detection. For the
moment 1 and 2 maps, we used only those pixels where the signal was detected at 1.5 times
the local rms value. We detect CO(3-2), CO(7-6) and even C i(2-1) line emission from the
companion galaxy (see Fig. 1 and Extended Data Fig. 4). The quasar is detected only in CO(76) line emission (shown in Fig. 1). The integrated line fluxes estimates (including 3 _𝜎_ upper
limits for nondetections) from the moment-0 maps are provided in Extended Data Table 1. For
CO line ratio map of the companion galaxy (shown in Extended Data Fig. 4), we smoothed
the CO(7-6) map to the lower resolution of CO(3-2) map.
We also examined continuum images for radio emission associated with the galaxy and
the quasar. In band 3, no continuum emission is detected in the multiband radio continuum
image at 101.9 GHz made using all four SPWs with `robust` `=` `0.5` weighting (see panel
(e) in Extended Data Fig. 4). The synthesized beam and the rms noise are 0 _._ 177 [′′] × 0 _._ 141 [′′]

and 8.3 _𝜇_ Jy beam [−][1], respectively. We adopt a 3 _𝜎_ upper limit of 25 _𝜇_ Jy for the quasar and the
companion galaxy. The band 6 multiband image at 226.5 GHz with an rms of 14.8 _𝜇_ Jy beam [−][1]

exhibits radio emission (panel (d) in Extended Data Fig. 4) with flux densities of 420 _𝜇_ Jy and
220 _𝜇_ Jy at the positions of the galaxy and the quasar, respectively. However, the corresponding
emission is not consistently detected in images from individual SPWs with rms noise of
∼25 _𝜇_ Jy beam [−][1] . Based on measurements in SPWs 21, 23 and 25 of band 6, we adopt
continuum flux densities at ≈ 226 GHz to be 330±30 _𝜇_ Jy and _<_ 180 uJy for companion and
host galaxies, respectively.


**Spectrophotometric modelling of the galaxies**


We used the `bagpipes` code [48] to fit the photometry data from Subaru, the ALMA constraints
on the mm-emission continuum, and the spectral energy distribution (SED) obtained from
X-shooter for both the companion and host galaxies. We assumed a double power law star formation history (SFH) model [49] and standard dust extinction law. [50] We treated the metallicity as
a free parameter, recognizing that it could differ between the central regions of the companion
galaxy and that along the quasar line of sight where we had the prior from absorption lines. We
assumed a stellar birth cloud lifetime of 10 Myr and a velocity dispersion of 500 km s [−][1] . While
we considered nebular emission to fit emission lines (Ly _𝛼_ and C III] lines are prominent in the
companion galaxy spectrum), we acknowledge that these could be impacted by the large characteristic bin size and potential quasar contribution. For dust emission from the companion
galaxy, given the likely subsolar metallicity, we allowed variations in _𝑈_ min (the lower cutoff of
the starlight intensity distribution) and _𝛾_ (the fraction of dust heated by starlight). [51] We used
Gaussian priors on the redshift and metallicity from the CO(7-6) emission and the absorption
line analysis, respectively. Uniform priors were applied to the star-formation law slope (in decimal scale) and in log-scale for other parameters. The parameters and their constraints, derived
from the posterior probability function using nested sampling within the bagpipes code, are
presented in Extended Data Table 2. While some parameters are not well constrained, due to
limited observational data, others, like stellar mass and extinction, are precisely determined.


13

**Mass estimates**


**Molecular gas.** The observed CO line fluxes correspond to luminosities [52] _𝐿_ CO ′ [= (2] _[.]_ [5] [±] [0] _[.]_ [3),]
(9 _._ 7 ± 1 _._ 2), and (1 _._ 4 ± 0 _._ 3) ×10 [9] K km s [−][1] pc [2] for CO(7-6) and CO(3-2) lines in the companion galaxy, and CO(7-6) line in the quasar host galaxy, respectively. These are converted into
′
molecular masses using _𝑀_ H 2 = _𝛼𝐿_ CO [(] _[𝐽]_ [−(] _[𝐽]_ [−] [1][))/] _[𝑟]_ _[𝐽]_ [1] [, where] _[ 𝛼]_ [is the CO(1-0) to H] [2] [ conver-]
sion factor and _𝑟_ _𝐽_ 1 is the (J-(J-1)) to (1-0) CO line ratio. Assuming [53] _𝑟_ 31 = 0 _._ 8 and _𝑟_ 71 = 0 _._ 2
we obtain _𝑀_ H 2 = (1 _._ 0 ± 0 _._ 1) × 10 [10] _𝑀_ ⊙ (companion) and _𝑀_ H 2 = (5 _._ 5 ± 0 _._ 1) × 10 [9] _𝑀_ ⊙ (host),
adopting _𝛼_ = 0 _._ 8 _𝑀_ ⊙ (K km s [−][1] pc [2] ) [−][1] as suggested by measurements in AGN, mergers and
starburst environments. [54,55,56,57]


**Dust.** The dust masses are estimated from the observed ALMA band 6 fluxes, assuming a
gray body spectrum with dust opacity ∝ _𝜈_ _[𝛽]_ and _𝛽_ = 0 _._ 7 (consistent with the relative fluxes of
ALMA bands 3 and 6), and a dust temperature range of 20 to 60 K, yielding (1 − 5) × 10 [8] _𝑀_ ⊙
for the companion and _<_ 3 × 10 [8] _𝑀_ ⊙ for the host galaxy, respectively.


**SMBH.** The mass of the SMBH powering J 012555.11−012925.00 is estimated from the
widths of the C iv (FWHM=3830 ± 30 km s [−][1] ) and H _𝛽_ (FWHM=2730 ± 30 km s [−][1] ) emission
lines together with continuum measurements. Correcting for dust reddening, we measure
fluxes of 2 _._ 5 and 0 _._ 3 × 10 [−][17] erg cm [−][2] s [−][1] Å [−][1] at 1350 and 5100 Å, respectively, translating to
log _𝜆𝐿_ _𝜆_ /(erg s [−][1] ) = 45 _._ 9 and 45 _._ 5. This yields log _𝑀_ SMBH / _𝑀_ ⊙ = 8 _._ 3 ± 0 _._ 4 (from C iv) and
8.0±0.4 (from H _𝛽_ ) using standard scaling relations. [58] These values align with the _𝑀_ SMBH _𝜎_ ∗ relation, [59] where the buldge velocity dispersion _𝜎_ ∗ ≃ 200 km s [−][1], is estimated from the
stellar mass _𝑀_ ∗ ≃ 5 × 10 [10] _𝑀_ ⊙ obtained above. [60] The estimated SMBH mass corresponds to
an Eddington luminosity _𝐿_ edd of a few times 10 [46] erg s [−][1], close to the bolometric luminosity
of the quasar, obtained from the flux at 1450 Å and scaling relations, [61] indicating that the
SMBH is accreting close to its Eddington limit.


**Absorbing gas analysis**


**Differential dust extinction**


−
The spectrum of J 012555.11 012925.00 appears clearly reddened compared to the X-shooter
composite quasar spectrum, [62] as shown in Extended Data Fig. 5. Following the quasar pair
method, [29,63,64,65,66] the best matching is obtained by reddening the composite with an Small
Magellanic Cloud (SMC) like extinction curve [67] and visual extinction _𝐴_ V ≈ 0 _._ 20 ± 0 _._ 10.
However, this significantly underpredicts the emission lines, Si IV, C III] and C IV, suggesting a
differential reddening between the continuum and the emission lines. Combining the reddened
continuum with unreddened emission lines from the composite provides a much better match,
indicating that dust is mostly confined in small clouds that cover the accretion disc but not the
larger emission line regions. We further note that while the heights of the emission lines are
now well reproduced, the observed lines are narrower than in the composite (see inlay panels
in Extended Data Fig. 5). This is again consistent with the differential reddening, as the wings
of the emission lines (i.e. the broad emission component) are produced in a small region with
high kinematics closer to the accretion disc, while the core of the lines (the narrow emission)
are produced over larger areas further from the central engine. Similar patchy dust obscuration


14

has also been invoked to explain the unusual line shapes observed in extremely red quasars [68]

and in some AGNs in the local Universe. [69]


**Line profile fitting method**


We modelled the absorption lines using multi-component Voigt profile fitting using `spectro`
package. The model parameters were constrained following a Bayesian approach to derive
the posterior distribution function using the affine invariant MCMC sampler. [44] We report
constraints on the model parameters using maximum a posteriori probability and 0.683 highest
posterior density estimates of the 1D marginalized probability distribution function. Priors
were set using uniform distributions for parameters such as redshifts ( _𝑧_ ), Doppler parameters
( _𝑏_ ), and logarithm of the column densities (log _𝑁_ ), unless otherwise specified. The model was
compared to data via the likelihood function, focusing on visually selected spectral regions
that are free from blends, cosmic-ray or skyline residuals. We assumed Gaussian-distributed
uncertainties around central pixel values, with dispersion given by the flux uncertainty.
Remarkably, most saturated absorption lines at _𝑧_ = 2 _._ 66 do not reach the zero level,
indicating partial coverage of the emission source by the absorbing medium. A partial coverage
factor, _𝐶_ _𝑓_, was then included in the model. [70] To reduce the number of free parameters, a
single _𝐶_ _𝑓_ value was assumed for all components at all wavelengths, as supported by the nearly
constant residual emission across wavelengths.


**Neutral hydrogen**


The total H i column density is determined by fitting the Ly- _𝛼_ absorption profile together
with the unabsorbed continuum, initially estimated using the reddened quasar composite and
adjusted with an 11th order Chebyshev polynomial. The pixels corresponding to residual Ly _𝛼_
emission (mainly within 4430–4460 Å) were excluded from the fit. We obtained log _𝑁_ (HI) =
21 _._ 911 [+] − [0] 0 _[.]_ _._ [016] 014 [at] _[ 𝑧]_ [=][ 2] _[.]_ [66347] [+] − [0] 0 _[.]_ _._ [00024] 00027 [and a zero-level flux level 7] _[.]_ [8] [+] − [0] 0 _[.]_ _._ [5] 2 [×][10] [19] [ erg cm] [−][2] [ s] [−][1] [ Å] [−][1] [,]
seen as residual emission at ∼ 4460 − 4490 Å in Extended Data Fig. 3.


**Molecular hydrogen**


The unabsorbed continuum over H 2 lines was re-constructed by eye using B-spline interpolation and guided by the reddened composite quasar spectrum. A two-component model
(components _𝐴_ and _𝐵_ ) was necessary to fit the absorption lines (see lines around 4084 Å and
3930 Å). We tied Doppler parameters ( _𝑏_ ) for _𝐽_ = 0 and 1 rotational levels, assuming that
they trace the bulk of the cloud and are co-spatial. Higher rotational levels were allowed different _𝑏_ -values, constrained to increase with rotational level [71,72,73] using a penalty function
added to the likelihood. [74,75] We also penalized non-physical models where _𝑇_ _𝑗, 𝑗_ +2 _> 𝑇_ _𝑗_ +2 _, 𝑗_ +4,
considering the ortho- and para- H 2 independently. The fit to H 2 is shown in Extended Data
Fig. 6 and constraints on the model parameters are summarized in Supplementary Table 2. We
found the the total column density is log _𝑁_ (H 2 ) = 21 _._ 19 [+] − [0] 0 _[.]_ _._ [02] 01 [. The levels] _[ 𝐽]_ [=][ 0 and 1 provide]
estimates of the kinetic temperatures _𝑇_ _𝑘_ ≈ _𝑇_ 01 = 320 [+] − [40] 20 [K and 300] [+] − [20] 20 [K for components] _[𝐴]_
and _𝐵_, respectively.


15

**Metal lines**


The absorption profile of metal lines extends over ∼ 400 km s [−][1] (see Fig. 2) We fitted the data
using an 18-component model, with Doppler parameters tied between different low-ionization
metals for each component, i.e. implicitly assuming turbulence-dominated broadening. The
unabsorbed continuum was locally reconstructed over each absorption line through B-spline
interpolation using the surrounding unabsorbed spectral regions. We used Gaussian prior on
the Doppler parameter with mean 6 km s [−][1] and dispersion 2 km s [−][1], in agreement with typical
values measured in high-resolution studies. The fit results are reported in Supplementary
Table 3 and 4. We obtain the average metallicity from the ratio of the total column density of the
volatile element zinc to that of the total hydrogen column density _𝑁_ tot (H) = N(H i) + 2N(H 2 ),
giving log _𝑍_ / _𝑍_ ⊙ = −0 _._ 92 ± 0 _._ 03 (respective to Solar [76] ).


**Neutral carbon**


We fitted the C i absorption lines from the fine structure levels of the ground electronic state
using a six-component model, identifying two prominent major components aligning with
the H 2 -bearing components. This association is consistent with findings in typical H 2 -bearing
DLAs. [77] The detection of C i in components without H 2 also indicates the presence of the
relatively dense neutral gas. [78] We tied the Doppler parameters of the three fine-structure
levels for each component, as these are typically co-spatial within the cloud. Consequently,
we also tied the column densities of the C i levels using a one-zone model, assuming radiative
pumping [27] and collisional excitation by H 2 or H i, and Helium. [79,80,81] We used temperature
priors from H 2 whenever detected and a flat prior otherwise. We accounted for excitation by the
Cosmic Microwave Background, using the expected temperature _𝑇_ CMB ( _𝑧_ ) = (1 + _𝑧_ ) × 2 _._ 725 ≈
10 K at _𝑧_ = 2 _._ 662. We used Gaussian priors with a mean of 6 km s [−][1] and dispersion of 2 km s [−][1]

on Doppler parameters. The fit to C i fine-structure levels is shown in Extended Data Fig. 7
with interval estimates on the model parameters in Supplementary Table 5.


**CO absorption**


We tentatively detect CO absorption in A − X bands (1-0), (3-0), (4-0), (6-0) and (7-0) at
_𝑧_ = 2 _._ 66. Since lines from individual rotational levels within each band are not resolved, we
fitted the band profiles assuming the rotational population follows a Boltzman distribution,
setting the prior on the kinetic temperature to be log _𝑇_ [K] = 2±0 _._ 3, in between the temperature
obtained from the ortho-para ratio of H 2 and the typical values in CO-bearing medium. We
used a two-component model with priors on the Doppler parameters _𝑏_ = 3 ± 1 km s [−][1] and
redshifts fixed to those from H 2 absorption lines, obtaining log _𝑁_ (CO) _<_ 13 _._ 6 and 13 _._ 99 [+] − [0] 0 _[.]_ _._ [15] 09
in components A and B, respectively. In Extended Data Fig. 8 we compare the stack of
observed CO bands to that of the synthetic profiles. [77]


**Physical conditions in the absorbing gas**


**Constraints from H** **2** **excitation.** We used the `Meudon` `PDR` code (version 1.5.4) [82] to model
the column densities of H 2 in various rotational-vibrational levels. We considered a constantdensity medium with 0.1 Solar metallicity, exposed to UV radiation from the quasar on one
side. [74] Other parameters were: cosmic ray ionization rate 10 [−][16] s [−][1] per H 2 molecule, LMC


16

extinction curve with _𝑅_ _𝑉_ = 2 _._ 6, standart MRN dust size distribution with dust-to-gas mass
ratio of 0.01 and turbulent velocity of 2 km s [−][1] . We note that these additional parameters have
little effect on the H 2 excitation and thermal balance in the UV-dominated regime. The default
Mathis field was scaled to mimic the quasar UV radiation at a given distance _𝑑_ . The choice
of the overall shape of the radiation field does not affect the results since photoexcitation and
photodissociation of H 2 involve the wavelength region ∼ 1100−910 Å, where both Mathis and
typical AGN fields are approximately flat. We constructed a two-dimensional grid of models
in the number density–distance ( _𝑛_ − _𝑑_ ) plane, trimming each model to match the observed total
H 2 column density. [83,33] We computed each model’s likelihood using the observed column
densities in the various excitation levels. The resulting parameter estimates are shown in Fig. 4.
These were obtained using Bayesian approach assuming derived likelihood and flat priors on
_𝑑_ and _𝑛_ in log space to emulate a wide distribution.


**Constraints from CO/H** **2** **.** We obtained constraints on the physical conditions from the total
observed CO and H 2 column densities in component _𝐵_ using the same grid of models. Taken
as face value, the presence of CO suggests slightly larger number densities than derived from
the excitation of H 2 in component _𝐵_ . This could result from the cloud having higher densities
in the central regions, where CO is more easily formed.


**Constraints from C** i **fine structure.** The C i line profile fit directly constrains the physical
conditions, as we used an excitation model to link the population of the fine-structure levels.
Because the excitation of the fine-structure levels are close to the ratio of statistical weights, C i
provides lower and upper limits on the number density and distance to the AGN, respectively,
as highlighted in Fig. 4.


**Constraints** **from** **H** i **/H** **2** **.** Based on the analytical theory of the H i/H 2 transition, [84,85] we
can only obtain a limit in the _𝑛_ − UV, [19] as it is not feasible to determine the fraction of the
total H i column density associated with the H 2 components. Nonetheless, this limit agrees
with the other constraints.


**Data** **Availability.** The Subaru imaging data are available on the `Hyper` `Suprime-Cam`
`Legacy` `Archive` ( `HSCLA` ; [https://hscla.mtk.nao.ac.jp/).](https://hscla.mtk.nao.ac.jp/) VLT spectroscopic data were collected at the European Southern Observatory under ESO programme 105.203L (PI: P.
Noterdaeme) and publicly available through the ESO science archive at [https://archive.eso.](https://archive.eso.org/cms.html)
[org/cms.html.](https://archive.eso.org/cms.html) ALMA data collected under program ID 2022.1.01792.S (PI: S. López) are
[publicly available at ALMA science archive at https://almascience.eso.org/aq/.](https://almascience.eso.org/aq/)


**Code** **Availability.** Astropy, [86] Bagpipes, [48] Galfit, [43] Matplotlib, [87] NumPy, [88] Photutils, [89]

SciPy, [90] SOFIA, [46,47] Emcee, [45] `spectro` [https://github.com/balashev/spectro](https://github.com/balashev/spectro) `Meudon` `PDR`
[https://pdr.obspm.fr/](https://pdr.obspm.fr/)

### **References**


39 Oke, J. B. & Gunn, J. E. Secondary standard stars for absolute spectrophotometry. _Astrophys._
_J._ **266**, 713–717 (1983).


40 Noterdaeme, P. _et_ _al._ Proximate molecular quasar absorbers. Chemical enrichment and
kinematics of the neutral gas. _Astron. Astrophys._ **673**, A89 (2023).


17

41 Hunter, T. R. _et al._ The ALMA Interferometric Pipeline Heuristics. _Publ. Astron. Soc. Pac._
**135**, 074501 (2023).


42 Tanaka, M. _et al._ Hyper Suprime-Cam Legacy Archive. _Publ. Astron. Soc. Jpn_ **73**, 735–746
(2021).


43 Peng, C. Y., Ho, L. C., Impey, C. D. & Rix, H.-W. Detailed Decomposition of Galaxy
Images. II. Beyond Axisymmetric Models. _Astron. J._ **139**, 2097–2129 (2010).


44 Goodman, J. & Weare, J. Ensemble samplers with affine invariance. _Communications in_
_Applied Mathematics and Computational Science_ **5**, 65–80 (2010).


45 Foreman-Mackey, D., Hogg, D. W., Lang, D. & Goodman, J. emcee: The mcmc hammer.
_PASP_ **125**, 306–312 (2013).


46
Serra, P. _et_ _al._ SOFIA: a flexible source finder for 3D spectral line data. _Mon._ _Not._ _R._
_Astron. Soc._ **448**, 1922–1929 (2015).


47 Westmeier, T. _et al._ SOFIA 2 - an automated, parallel H I source finding pipeline for the
WALLABY survey. _Mon. Not. R. Astron. Soc._ **506**, 3962–3976 (2021).


48 Carnall, A. C., McLure, R. J., Dunlop, J. S. & Davé, R. Inferring the star formation
histories of massive quiescent galaxies with BAGPIPES: evidence for multiple quenching
mechanisms. _Mon. Not. R. Astron. Soc._ **480**, 4379–4401 (2018).


49 Carnall, A. C. _et al._ How to Measure Galaxy Star Formation Histories. I. Parametric Models.
_Astrophys. J._ **873**, 44 (2019).


50 Calzetti, D. _et_ _al._ The Dust Content and Opacity of Actively Star-forming Galaxies.
_Astrophys. J._ **533**, 682–695 (2000).


51 Draine, B. T. & Li, A. Infrared Emission from Interstellar Dust. IV. The Silicate-GraphitePAH Model in the Post-Spitzer Era. _Astrophys. J._ **657**, 810–837 (2007).


52 Solomon, P. M. & Vanden Bout, P. A. Molecular Gas at High Redshift. _Annu. Rev. Astron._
_Astrophys._ **43**, 677–725 (2005).


53 Boogaard, L. A. _et al._ The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field:
CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3. _Astrophys. J._ **902**,
109 (2020).


54 Carilli, C. L. & Walter, F. Cool Gas in High-Redshift Galaxies. _Annu._ _Rev._ _Astron._
_Astrophys._ **51**, 105–161 (2013).


55 Bolatto, A. D., Wolfire, M. & Leroy, A. K. The CO-to-H 2 Conversion Factor. _Annu. Rev._
_Astron. Astrophys._ **51**, 207–268 (2013).


56 Sargent, M. T. _et al._ Regularity Underlying Complexity: A Redshift-independent Description


18

of the Continuous Variation of Galaxy-scale Molecular Gas Properties in the Mass-star
Formation Rate Plane. _Astrophys. J._ **793**, 19 (2014).


57 Calistro Rivera, G. _et_ _al._ Resolving the ISM at the Peak of Cosmic Star Formation with
ALMA: The Distribution of CO and Dust Continuum in z ∼ 2.5 Submillimeter Galaxies.

_Astrophys. J._ **863**, 56 (2018).


58 Vestergaard, M. & Peterson, B. M. Determining Central Black Hole Masses in Distant Active
Galaxies and Quasars. II. Improved Optical and UV Scaling Relationships. _Astrophys._ _J._
**641**, 689–709 (2006).


59 Kormendy, J. & Ho, L. C. Coevolution (Or Not) of Supermassive Black Holes and Host
Galaxies. _Annu. Rev. Astron. Astrophys._ **51**, 511–653 (2013).


60 Zahid, H. J., Geller, M. J., Fabricant, D. G. & Hwang, H. S. The Scaling of Stellar Mass
and Central Stellar Velocity Dispersion for Quiescent Galaxies at z<0.7. _Astrophys. J._ **832**,
203 (2016).


61 Runnoe, J. C., Brotherton, M. S. & Shang, Z. Updating quasar bolometric luminosity
corrections. _Mon. Not. R. Astron. Soc._ **422**, 478–493 (2012).


62 Selsing, J., Fynbo, J. P. U., Christensen, L. & Krogager, J. K. An X-Shooter composite of
bright 1 < z < 2 quasars from UV to infrared. _Astron. Astrophys._ **585**, A87 (2016).


63 Wang, J., Hall, P. B., Ge, J., Li, A. & Schneider, D. P. Detections of the 2175 Å Dust Feature
at 1 _._ 4 _<_ _𝑧<_ 1 _._ 5 from the Sloan Digital Sky Survey. _Astrophys. J._ **609**, 589–596 (2004).


64 Srianand, R., Gupta, N., Petitjean, P., Noterdaeme, P. & Saikia, D. J. Detection of the 2175
Å extinction feature and 21-cm absorption in two MgII systems at z ~1.3. _Mon._ _Not._ _R._
_Astron. Soc._ **391**, L69–L73 (2008).


65 Zhang, S. _et al._ Seven Broad Absorption Line Quasars With Excess Broadband Absorption
Near 2250 Å. _Astrophys. J._ **802**, 92 (2015).


66 Noterdaeme, P. _et_ _al._ Discovery of a Perseus-like cloud in the early Universe. H I-toH 2 transition, carbon monoxide and small dust grains at z _𝑎𝑏𝑠_ ≈ 2.53 towards the quasar
J0000+0048. _Astron. Astrophys._ **597**, A82 (2017).


67 Gordon, K. D., Clayton, G. C., Misselt, K. A., Land olt, A. U. & Wolff, M. J. A Quantitative
Comparison of the Small Magellanic Cloud, Large Magellanic Cloud, and Milky Way
Ultraviolet to Near-Infrared Extinction Curves. _Astrophys. J._ **594**, 279–293 (2003).


68 Hamann, F. _et al._ Extremely red quasars in BOSS. _Mon. Not. R. Astron. Soc._ **464**, 3431–3463
(2017).


69 Veilleux, S. _et al._ The Surprising Absence of Absorption in the Far-ultraviolet Spectrum of
Mrk 231. _Astrophys. J._ **764**, 15 (2013).


19

70 Bergeron, J. & Boissé, P. Extent and structure of intervening absorbers from absorption
lines redshifted on quasar emission lines. _Astron. Astrophys._ **604**, A37 (2017).


71 Lacour, S. _et_ _al._ Velocity Dispersion of the High Rotational Levels of H 2 . _Astrophys._ _J._
**627**, 251–262 (2005).


72 Noterdaeme, P. _et_ _al._ Excitation mechanisms in newly discovered H_2-bearing damped
Lyman- _𝛼_ clouds: systems with low molecular fractions. _Astron. Astrophys._ **474**, 393–407
(2007).


73 Balashev, S. A., Varshalovich, D. A. & Ivanchik, A. V. Directional radiation and photodissociation regions in molecular hydrogen clouds. _Astronomy_ _Letters_ **35**, 150–166
(2009).


74 Noterdaeme, P. _et al._ Down-the-barrel observations of a multi-phase quasar outflow at high
redshift. VLT/X-shooter spectroscopy of the proximate molecular absorber at z = 2.631
towards SDSS J001514+184212. _Astron. Astrophys._ **646**, A108 (2021).


75 Kosenko, D. N. _et_ _al._ HD molecules at high redshift: cosmic ray ionization rate in the
diffuse interstellar medium. _Mon. Not. R. Astron. Soc._ **505**, 3810–3822 (2021).


76 Asplund, M., Grevesse, N., Sauval, A. J. & Scott, P. The Chemical Composition of the Sun.
_Annu. Rev. Astron. Astrophys._ **47**, 481–522 (2009).


77 Noterdaeme, P. _et_ _al._ Spotting high-z molecular absorbers using neutral carbon. Results
from a complete spectroscopic survey with the VLT. _Astron. Astrophys._ **612**, A58 (2018).


78 Balashev, S. A. & Kosenko, D. N. Neutral carbon in diffuse interstellar medium: abundance
matching with H 2 for damped Lyman alpha systems at high redshifts. _Mon. Not. R. Astron._
_Soc._ **527**, 12109–12119 (2024).


79 Schroder, K., Staemmler, V., Smith, M. D., Flower, D. R. & Jaquet, R. Excitation of the
fine-structure transitions of C in collisions with ortho- and para-H 2 . _Journal of Physics B_
_Atomic Molecular Physics_ **24**, 2487–2502 (1991).


80 Abrahamsson, E., Krems, R. V. & Dalgarno, A. Fine-Structure Excitation of O I and C I by
Impact with Atomic Hydrogen. _Astrophys. J._ **654**, 1171–1174 (2007).


81 Staemmler, V. & Flower, D. R. Excitation of the C(2p 2 _._ 3 P _𝑗_ ) fine structure states in collisions
with He(1s [2] [1] S 0 ). _Journal of Physics B Atomic Molecular Physics_ **24**, 2343–2351 (1991).


82 Le Petit, F., Nehmé, C., Le Bourlot, J. & Roueff, E. A Model for Atomic and Molecular
Interstellar Gas: The Meudon PDR Code. _Astrophys. J. Suppl. Ser._ **164**, 506–529 (2006).


83 Klimenko, V. V. & Balashev, S. A. Physical conditions in the diffuse interstellar medium
of local and high-redshift galaxies: measurements based on the excitation of H 2 rotational
and C I fine-structure levels. _Mon. Not. R. Astron. Soc._ **498**, 1531–1549 (2020).


20

84
Sternberg, A., Le Petit, F., Roueff, E. & Le Bourlot, J. H I-to-H 2 Transitions and H I Column
Densities in Galaxy Star-forming Regions. _Astrophys. J._ **790**, 10 (2014).


85 Bialy, S. & Sternberg, A. Analytic H I-to-H 2 Photodissociation Transition Profiles.
_Astrophys. J._ **822**, 83 (2016).


86 Astropy Collaboration _et al._ The Astropy Project: Sustaining and Growing a Communityoriented Open-source Project and the Latest Major Release (v5.0) of the Core Package.
_Astrophys. J._ **935**, 167 (2022).


87 Hunter, J. D. Matplotlib: A 2D Graphics Environment. _Computing_ _in_ _Science_ _and_
_Engineering_ **9**, 90–95 (2007).


88 Harris, C. R. _et al._ Array programming with NumPy. _Nature_ **585**, 357–362 (2020).


89 Bradley, L. _et al._ astropy/photutils: 1.12.0 (2024).


90 Virtanen, P. _et_ _al._ SciPy 1.0: fundamental algorithms for scientific computing in Python.
_Nature Methods_ **17**, 261–272 (2020).


**Acknowledgments.** SB is supported by RSF grant 23-12-00166 and thanks IAP for hospitality where part of this work was done. The research leading to these results received
support from the French _Agence Nationale de la Recherche_ under ANR grant 17-CE31-001101/project “HIH2” (PI Noterdaeme). NG acknowledges NRAO for generous financial support
for the sabbatical visit at Socorro during which a part of this work was done.


**Author Contributions.** S.A.B. and P.N. led the analysis and wrote the manuscript. S.A.B.
modeled the physical conditions. P.N. designed the optical observations. N.G. performed the
analysis of the ALMA data. J.-K.K. reduced the X-shooter data, with post-processing by R.C.
F.C., S.L. and A.O. contributed to the ALMA observing proposal. P.P. and R.S. contributed to
the VLT proposal. All authors contributed to the text and aided the interpretation of the results.


**Author** **Information.** Correspondence and requests for materials should be addressed to
Sergei Balashev. The authors declare no competing interests.


21

**Extended Data Table 1** : **Details of ALMA spectral line cubes and detected line emission.**


Band SPW Target line _𝜈_ _𝑟𝑒𝑠𝑡_ Beam _[𝑎]_ Res. _[𝑏]_ rms _[𝑐]_ Line flux _[𝑑]_

[GHz] [km s [−][1] ] [mJy× [Jy km s [−][1] ]

beam [−][1] ] Companion Quasar


3 25 CO(3-2) 345.7960 0 _._ 210 [′′] × 0 _._ 166 [′′], −51 _._ 5 [◦] 12.4 0.29 0.271 ± 0.034 _<_ 0.10


” 27 HCO+(4-3) 356.7343 0 _._ 207 [′′] × 0 _._ 161 [′′], −51 _._ 1 [◦] 12.0 0.29 _<_ 0.10 _<_ 0.10


” 29 CS(8-7) 391.8468 0 _._ 190 [′′] × 0 _._ 150 [′′], −52 _._ 0 [◦] 10.9 0.32 _<_ 0.10 _<_ 0.10


6 27 CO(7-6) 806.6518 0 _._ 121 [′′] × 0 _._ 101 [′′], +72 _._ 4 [◦] 10.6 0.37 0.383 ± 0.044 0.207 ± 0.039


” ” C i(2-1) 809.3420 ” ” ” 0.170 ± 0.036 _<_ 0.12


_𝑎_ Spatial resolution i.e., the synthesized beam in terms of major and minor axis, and position angle. _𝑏_ Spectral
resolution in the quasar frame. _[𝑐]_ Spectral rms. _[𝑑]_ For non-detections 3 _𝜎_ upper limits estimated assuming a line
FWHM of 100 km s [−][1] .

### **Extended Data**


**Extended** **Data** **Fig.** **1** : **Hyper** **Suprime-Cam** **deep** **images** **of** **the** **field** **around**

−
**J 012555.11** **012925.00. a, e**, the original image. **b, f**, quasar’s point spread function (PSF)
subtracted image. **c, g**, model of additional sources. **d, h**, residuals. The top and bottom panels
correspond to _𝑔_ and _𝑟_ filters, respectively. The blue circle in each panel denotes the full width
at half maximum (FWHM) of the PSF. The white cross and circle indicate the position of the
quasar and the FWHM of the point spread function, respectively.


22

**Extended** **Data** **Fig.** **2** : **Spatial** **profile** **of** **the** **2D** **X-shooter** **spectrum** **of**
**J 012555.11** − **012925.00.** The data (black lines with error bars) is shown here collapsed into
three **a, b, c**, wavelength regions (indicated in the top right corner). The spatial profile is modeled by the sum (green) of two Moffat profiles, corresponding to the quasar (blue) and the
companion galaxy (red). The error bars indicate the standard deviation of the collapsed flux,
while the colored stripes represent the 0.683 credible interval of the models.


**Extended** **Data Table** **2** : **Spectral** **energy distribution** **fitting** **of the** **com-**
**panion and quasar host galaxy with** bagpipes **.**


parameter description prior posterior


Companion galaxy Host galaxy


z redshift Gaussian from CO 2 _._ 663 ± 0 _._ 001 2 _._ 656 ± 0 _._ 001


log _𝑀_ ∗ _,_ [ _𝑀_ ⊙ ] stellar mass log10 10 _._ 84 [+] − [0] 0 _[.]_ _._ [12] 12 10 _._ 7 [+] − [0] 0 _[.]_ _._ [3] 3
_𝛼_ dpl falling SFH slope uniform _<_ 0 _._ 1 −0 _._ 8 [+] − [0] 0 _[.]_ _._ [8] 8
_𝛽_ dpl rising SFH slope uniform _>_ 1 _._ 5 −2 _.._ 3

_𝜏_ dpl [Gyr] SFR peak time log10 2 _._ 2 [+] − [0] 0 _[.]_ _._ [1] 2 0 _._ 5 _.._ 2


_𝑍_ metallicity Gaussian and log10 _<_ 0 _._ 9 0 _._ 8 _.._ 2 _._ 1

A V extinction log10 1 _._ 2 [+] − [0] 0 _[.]_ _._ [1] 1 0 _._ 7 [+] − [0] 0 _[.]_ _._ [2] 3

_𝑈_ min dust parameter log10 _>_ 3 _._ 2 _>_ 1 _._ 3


_𝛾_ dust parameter log10 _>_ 0 _._ 9 _>_ 0 _._ 3


log _𝑈_ ionization parameter uniform _<_ −3 _._ 3 _>_ −2 _._ 4


Derived quantities:

SFR [M ⊙ yr [−][1] ] current star-formation rate 250 [+] − [60] 50 24 [+] − [17] 11


23

**Extended** **Data** **Fig.** **3** : **Spectral** **regions** **around** **C** ii **1334 Å** **and** **Ly** _𝛼_ **lines** **at** _𝑧_ = 2 _._ 622 **.**
**a**, **b**, **c**, C ii 1334 Å line. **d**, **e**, **f**, Ly _𝛼_ line. The strong C ii and Ly _𝛼_ absorption suppress light
from the quasar’s central engine, acting like a coronagraph which reveals the ∼10 times fainter
emission from the host galaxy as residual emission in the absorption trough. **a**, **d**, the portions
of the 1D X-shooter spectrum extracted along the quasar trace, with cyan and blue dashed
lines indicating the zero flux level and the average line flux residual, respectively. The error
bars represent the standard deviation of the measured flux. **b**, **e**, the 2D X-shooter spectrum
(smoothed for illustration purposes) of the same spectral regions. **c**, **f**, the spatial profiles
integrated along the dispersion axis, with the blue histogram corresponding to regions within
the saturated lines (black dashed boxes in **b**, **e** ), while the red filled histogram correspond to
the continuum emission. This faint emission clearly extends beyond the point spread function,
in agreement with an origin in an extended object. In **e**, the blob at _𝜆_ ∼ 4430 − 4465 Å
corresponds to the extended Ly _𝛼_ emission seen in the bottom of the extremely strong Ly _𝛼_
absorption line. The red dotted and blue dashed lines denote the centroids of the ALMA CO
emission of the companion and quasar host galaxies, respectively in both spatial and velocity
space, with the stripe indicating their velocity spread.


24

**Extended** **Data** **Fig.** **4** : **Line** **and** **continuum** **ALMA** **images** **of** **the** **field** **around**
**J 012555.11** − **012925.00.** **a**, **b**, **c**, The integrated emission of CO(3-2) and C i(2-1) lines,
together with CO(7-6)/(3-2) line ratios, respectively, centered on the companion galaxy. **d**, **e**,
ALMA band 6 and 3 wideband continuum images, respectively. The gray contours indicate
the CO(7-6) emission shown in Fig. 1. The green hatch ellipses in each panel represent the
synthesized beam.


25

**Extended Data Fig. 5** : **A full view of the X-shooter spectrum of J 012555.11** − **012925.00.**
The black, purple, green lines show respectively the observed spectrum, the quasar composite
spectrum from [62] and the same composite reddened by an SMC-like extinction law with
_𝐴_ V = 0 _._ 2 at z=2.66. The blue line depicts the continuum component of the quasar spectrum
(i.e. removing emission lines) reddened by the same extinction. The red spectrum is the sum
of the reddened continuum and the unreddened emission lines and clearly reproduces much
better the emission lines redwards of Ly- _𝛼_ . This indicates that the continuum light from the
quasar accretion disc passes through dusty gas, while light from the emission line regions
is almost unaffected, implying that dust is confined in much smaller regions. **b**, **c** indicate
zoom-in on the spectral region around C iv and C iii] emission lines. The position of metal
absorption lines associated with the proximate DLA are marked by grey ticks and labels.


26

2.0


1.5


1.0


0.5


0.0


2.0


1.5


1.0


0.5


0.0



(a)


L 3-0: 7

L 2-0: 5 6 6 7 7



~~+2~~ ~~_σ_~~


~~−2~~ ~~_σ_~~



L 1-0: 0 1 12 2 3 3 4 4 5 5 6 6 7

L 0-0: 0 1 12 23 34 45



0. ~~9170~~ [+] ~~−~~ ~~[0]~~ ~~0.0047~~ ~~[.][0]~~ [020]


4000 4010 4020 4030 4040 4050 4060 4070 4080 4090 4100


(b)


L 5-0: 7 7



~~+2~~ ~~_σ_~~


~~−2~~ ~~_σ_~~



L 4-0: 4 5 5 6 6 7 7

L 3-0: 0 1 1 2 2 3 3 4 4 5 5 6 6 7

L 2-0: 0 1 1 2 2 3 3 4 4 5


~~0.9170~~ ~~[+]~~ ~~−~~ [0.0] 0. ~~0047~~ [0] ~~[2]~~ [0]



3880 3890 3900 3910 3920 3930 3940 3950 3960 3970 3980 3990



(c)



~~+2~~ ~~_σ_~~


~~−2~~ ~~_σ_~~



2.0



L ~~7~~ -0: 6 7 7

L 6-0: 4 5 5 6 6 7 7

1.5 L 5-0: 0 1 1 2 2 3 3 4 4 5 5 6 6


L 4-0: 0 1 1 2 2 3 3 4


1.0


0.5


~~0.9170~~ ~~[+]~~ ~~−~~ [0.0020] ~~0~~ . ~~0047~~

0.0


3790 3800 3810 3820 3830 3840 3850 3860 3870 3880



2.0


1.5



(d)


~~L~~ ~~10-0:~~ ~~6~~ ~~7~~ ~~7~~

L 9-0: 4 5 5 6 6 7 7



~~+2~~ ~~_σ_~~


~~−2~~ ~~_σ_~~



L 8-0: 0 1 1 2 2 3 3 4 4 5 5 6
L 7-0: 0 1 1 2 2 3 ~~3~~



W 1-0: 6 7 7
W 0-0: 10 2 1 3 2 4 2 3 5 3 4 6 4 5


1.0


0.5


~~0.91~~ 70 ~~[+]~~ ~~−~~ [0] ~~0~~ ~~[.]~~ . ~~[0]~~ ~~0~~ [0] 047 [20]

0.0


36 ~~7~~ 0 3680 3690 3700 3710 3720 3730
Observed wavelength [Å]

**Extended** **Data** **Fig.** **6** : **Fit** **to** **the** **line** **profiles** **of** **H** 2 **lines** **associated** **with** **the** **proxi-**
**mate absorber at** _𝑧_ = 2 _._ 662 **towards J 012555.11** − **012925.00.** The black lines represent the
observed normalized spectrum, with the error bars representing the standard deviation. The
green, violet, and red stripes indicate the profiles of H 2 components _𝐴_, _𝐵_, and the total profile,
respectively. Black and green dashed horizontal lines at the bottom of each panel show the
zero flux level and partial coverage, respectively. Blue step-like lines at the top of each panel
display the residuals, with horizontal lines representing −2 _𝜎_, 0, and 2 _𝜎_ levels. Red horizontal segments identify the band (Lyman/Werner, vibrational level of upper and lower state) as
well as main rotational levels (numbers above ticks, only shown for component _𝐴_ for clarity).
Note that lines from low rotational levels in the L2-0 band (around 3950 Å) are blended with
the strong Ly _𝛼_ line from intervening H i at _𝑧_ = 2 _._ 25, identified through its associated metal
transitions.


27

**Extended Data Fig. 7** : **Fit to the C** i **absorption line profiles associated with the proximate**
**absorber** **at** _𝑧_ ≈ 2 _._ 662 **towards** **J 012555.11** − **012925.00.** The graphical elements are the
same as in Extended Data Fig. 6 with profiles of additional components shown by gray lines.
Each profile contains absorption from three fine-structure levels of the ground state.



~~(b)~~


CO A-X 2-0


5410 5415 5420


~~(e)~~


CO A-X 6-0

5010 Wavelength [Å] 5015



~~(c)~~


CO A-X 3-0


5300 5305 5310


~~(f)~~


CO A-X 7-0


4920 4925 4930



~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~


~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~



~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~


~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~



1.2


1.0



~~(a)~~



CO A-X 1-0

0.8 5530 5535 5540


1.2 ~~(d)~~


1.0


CO A-X 4-0

0.8 5195 5200 5205


(g)


1. ~~0~~



~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~


~~+2~~ ~~_σ_~~

~~−2~~ ~~_σ_~~



0.9



fit stack spectrum stack



−600 −500 −400 −300 −200 −100 0 100 200 300 400 500 600 700 800 900
~~Velocity offset [km s~~ ~~[−1]~~ ~~]~~


**Extended** **Data** **Fig.** **8** : **Possible** **detection** **of** **CO** **absorption** **lines** **at** _𝑧_ = 2 _._ 662 **in** **the**
**proximate absorber towards J 012555.11** − **012925.00. a** - **f**, The fit to individual CO bands.
The black line show the observed spectrum, while the green, blue and red lines represent
the two individual components and total line profiles. **g**, The stack of the observed spectrum
(black) and total profile model (red).


28


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "UV-to-NIR slit spectroscopy of the quasar and companion galaxy at PA=90 deg and PA=0 deg (ESO programme 105.203L).",
  "failed_quote": "VLT spectroscopic data were collected at the European Southern Observatory under ESO programme 105.203L (PI: P. Noterdaeme) and publicly available through the ESO science archive at https://archive.eso.org/cms.html."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Converted CO(7-6) and CO(3-2) line luminosities L'_CO into M_H2; estimated dust masses from ALMA Band 6 continuum assuming a gray body spectrum; estimated SMBH mass from C IV and H-beta emission line FWHMs and reddening-corrected continuum luminosities at 1350 A and 5100 A.",
  "failed_quote": "These are converted into molecular masses using 𝑀H2 = 𝛼𝐿′CO(𝐽−(𝐽−1))/𝑟𝐽1, where 𝛼 is the CO(1-0) to H2 conversion factor and 𝑟𝐽1 is the (J-(J-1)) to (1-0) CO line ratio."
 },
 {
  "path": "analysis_steps[5].key_parameters[0].evidence[0]",
  "value": "Metallicity = 0.1 Solar; cosmic ray ionization rate = 10^-16 s^-1 per H2; LMC extinction curve with R_V = 2.6; MRN dust size distribution; dust-to-gas mass ratio = 0.01; turbulent velocity = 2 km s^-1.",
  "failed_quote": "We considered a constant-density medium with 0.1 Solar metallicity, exposed to UV radiation from the quasar on one side. [74] Other parameters were: cosmic ray ionization rate 10−16 s−1 per H2 molecule, LMC extinction curve with 𝑅𝑉 = 2.6, standart MRN dust size distribution with dust-to-gas mass ratio of 0.01 and turbulent velocity of 2 km s−1."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Diffuse molecular gas exposed to the quasar radiation is photo-dissociated, leaving behind only compact (< 0.02 pc), dense (10^5 - 10^6 cm^-3), low-mass (< 0.1 M_sun) cloudlets with a volume filling factor <= 10^-5 that are too small to form stars.",
  "failed_quote": "While we detect high-density molecular clouds, we find no evidence of lower-density ones. This, combined with the high incident UV flux, indicates that the bulk of the diffuse molecular gas exposed to the quasar radiation has been photo-dissociated (within timescales of several years for the constrained UV flux), and only the high density regions survived the intense radiation field."
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Publicly available in the ALMA Science Archive (2022.1.01792.S), ESO Science Archive (105.203L), and Hyper Suprime-Cam Legacy Archive (HSCLA).",
  "failed_quote": "The Subaru imaging data are available on the Hyper Suprime-Cam Legacy Archive (HSCLA; https://hscla.mtk.nao.ac.jp/). VLT spectroscopic data were collected at the European Southern Observatory under ESO programme 105.203L (PI: P. Noterdaeme) and publicly available through the ESO science archive at https://archive.eso.org/cms.html. ALMA data collected under program ID 2022.1.01792.S (PI: S. López) are publicly available at ALMA science archive at https://almascience.eso.org/aq/."
 }
]
```
