# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025NatAs...9.1326S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## Solar C / O ratio in planet-forming gas at 1 au in a highly irradiated disk.

Ilane Schroetter [1*], Olivier Bern´e [1], Emeric Bron [2], Felipe Alarcon [3],
Paul Amiot [1], Edwin A. Bergin [3], Christiaan Boersma [4],
Jan Cami [5,] [6,] [7], Gavin A. L. Coleman [8], Emmanuel Dartois [9],
Asuncion Fuente [10], Javier R. Goicoechea [11], Emilie Habart [12],
Thomas J. Haworth [8], Christine Joblin [1], Franck Le Petit [2],
Takashi Onaka [13], Els Peeters [5,] [6,] [7], Markus R¨olling [14],
Alexander G. G. M. Tielens [15,] [16], Marion Zannese [12]


1* Institut de Recherche en Astrophysique et Plan´etologie, Universit´e de
Toulouse, CNRS, CNES, 9 Av. du colonel Roche, Toulouse Cedex 4,
31028, France.
2 Laboratoire d’Etudes du Rayonnement et de la Mati`ere, Observatoire
de Paris, Universit´e Paris Science et Lettres, Centre National de la
Recherche Scientifique, Sorbonne Universit´es, F-92190 Meudon, France.
3 Department of Astronomy, University of Michigan, Ann Arbor, MI
48109, USA.
4 NASA Ames Research Center, Moffett Field, CA 94035-1000, USA.
5 Department of Physics & Astronomy, The University of Western
Ontario, London ON N6A 3K7, Canada.
6 Institute for Earth and Space Exploration, The University of Western
Ontario, London ON N6A 3K7, Canada.
7 Carl Sagan Center, Search for ExtraTerrestrial Intelligence Institute,
Mountain View, CA 94043, USA.
8 Astronomy Unit, School of Physics and Astronomy, Queen Mary
University of London, London E1 4NS, UK.
9 Institut des Sciences Mol´eculaires d’Orsay, Universit´e Paris-Saclay,
Centre National de la Recherche Scientifique, 91405 Orsay, France.
10 Centro de Astrobiolog´ıa (CAB), CSIC-INTA, Ctra. de Ajalvir, km 4,
Torrej´on de Ardoz, 28850 Madrid, Spain.
11 Instituto de F´ısica Fundamental (Consejo Superior de Investigacion
Cientifica), 28006, Madrid, Spain.


1

12 Institut d’Astrophysique Spatiale, Universit´e Paris-Saclay, Centre
National de la Recherche Scientifique, 91405 Orsay, France.
13 Department of Astronomy, Graduate School of Science, The
University of Tokyo, Tokyo 113-0033, Japan.
14 Physikalischer Verein – Gesellschaft f¨ur Bildung und Wissenschaft,
Robert-Mayer-Str. 2, 60325 Frankfurt, Germany.
15 Astronomy Department, University of Maryland, College Park, MD
20742, USA.
16 Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA
Leiden, The Netherlands.


**Abstract**


The chemical composition of exoplanets is thought to be influenced by the composition of the disks in which they form. JWST observations have unveiled a
variety of species in numerous nearby disks, showing significant variations in the
C/O abundance ratio. However, little is known about the composition and C/O
ratio of disks around young stars in clusters exposed to strong ultraviolet (UV)
radiation from nearby massive stars, which are representative of the environments where most planetary systems form, including ours. We present JWST
spectroscopy of d203-504, a young 0.7 **M** _**⊙**_ star in the Orion Nebula with a 30
au disk irradiated by nearby massive stars. These observations reveal spectroscopic signatures of CO, H 2 O, CH 3 [+] [,] [and] [PAHs.] Water and CO are detected
in absorption in the inner disk ( _**r**_ ≲ **1** au), where the estimated gas-phase C/O
ratio is 0.48, consistent with the Solar value and that of the Orion Nebula. In
contrast, CH 3 [+] and PAHs are found in the extended surface layers of the disk.
These results suggest that gas in the inner disk is chemically shielded from UV
radiation while the surface layers of the disk experience UV-induced chemistry,
potentially depleting their carbon content.


Understanding how exoplanets form and acquire their chemical composition is a
central question in contemporary astrophysics. These processes take place in protoplanetary disks of gas and dust around young stars, where complex physical and
chemical interactions set the initial conditions for planet formation and potential
habitability.
JWST [1] is currently transforming our knowledge of the chemical inventory in
the planet-forming regions of protoplanetary disks around nearby isolated low-mass
stars [2–4]. Observations have revealed a diverse and widespread presence of midinfrared emission from neutral species, including H 2 O, HCN, CH 4, and C 2 H 2, [5–10].
Whether the chemical composition of those disks is dominated by H 2 O or hydrocarbon
emissions is thought to be driven by the time evolution of the C/O ratio in the inner


2

disk, which is a key parameter for the chemistry of exoplanets [11]. The prevailing
scenario derived from JWST (and earlier Spitzer) observations, supported by models

[12], suggests an evolutionary sequence: initially, icy pebble drift delivers oxygen to
the inner disk through the sublimation of H 2 O at the snowline, reducing the C/O ratio
relative to the initial value of the parent molecular cloud. Subsequently, the C/O ratio
is expected to increase again. This can be explained either by carbon-rich grains and
polycyclic aromatic hydrocarbons (PAHs) drifting inward and re-enriching the gas in
carbon at the soot-line [3, 10]; or through viscous transport of carbon-rich gas towards
the inner disk [12]. The timing of this sequence depends on the dust drift timescale
and rate of viscous evolution in the disk, the latter which progresses faster around
low-mass stars compared to solar-type stars [12].
While studies of isolated disks are key to understanding disk chemistry and its link
to exoplanet compositions, most low-mass stars form in stellar groups that include
massive stars [13]. These massive stars ( _M_ star _≥_ 8 _M_ _⊙_ ) emit strong ultraviolet (UV)
radiation, including ionizing extreme ultraviolet (EUV; _E_ _>_ 13 _._ 6 eV) and dissociating far ultraviolet (FUV; 6 _,_ eV _<_ _E_ _<_ 13 _._ 6 _,_ eV) photons. As a result, the majority
of planets likely form under conditions influenced by pervasive UV radiation, which
can significantly affect star and planet formation [14]. This scenario is relevant to the
Solar System itself, which likely formed in the vicinity of massive stars [15–17]. Despite
the expected importance of UV radiation in typical star-forming environments, relatively few studies have focused on its impact on the chemical inventory during planet
formation [18–21].
Theoretical models have long suggested that strong external UV radiation can
significantly alter disk chemistry [22–25]. This has been confirmed by recent JWST
observations of the protoplanetary disk d203-506 in the Orion Nebula Cluster (ONC),
which is exposed to a strong external FUV radiation field of _G_ 0 = (2 _−_ 4) _×_ 10 [4] [27]
( _G_ 0 = 1 corresponds to the standard interstellar radiation field defined by [26]) . Vibrational emission of FUV-pumped H 2 detected with JWST-NIRSpec [28] highlights the
significant role of FUV photons in gas heating, as seen in photodissociation regions
(PDRs) with JWST (see e.g., [29]). This warm H 2 drives the formation of reactive
species like CH [+], leading to the production of CH 3 [+] [,] [a] [key] [molecular] [ion] [indicative] [of]
active organic gas-phase chemistry triggered by FUV radiation [30]. Additionally, the
detection of highly rotationally excited OH implies efficient H 2 O destruction by UV
photons, consistent with the absence of H 2 O in the spectrum of d203-506 [31]. Emission from Polycyclic Aromatic Hydrocarbons (PAHs), observed in this disk’s JWST
spectrum [28], further supports the influence of FUV-driven chemistry, and contrasts
with isolated disks, where PAHs are rarely observed [3, 32]. These findings suggest
that UV radiation plays a crucial role in shaping disk chemistry and, consequently,
the chemical inheritance passed to forming planets.
However, several limitations remain. The current understanding is based on a single, edge-on disk (d203-506), restricting observations to the extended disk surface and
preventing direct assessment of inner disk chemistry, including the C/O ratio. Observations of the XUE1 disk in the massive star-forming region NGC 6357 [33] show
molecular emission lines resembling those of isolated disks, including H 2 O, suggesting


3

20









































































20



























|1e114 2 3 4|5 6 7 8 9 10 11 12|13 14 15 16|17 18 19 2|
|---|---|---|---|
|Mg II<br>4.4<br>4.6<br>6<br>7 1e<br>15<br>b)|[Ar II]<br>[Ar III]<br>[Ne II]<br>[Ne III]<br>2.5<br>2.6<br>2.7<br>2.8<br>8<br>9<br>1e<br>15<br>H2O<br>a)<br>4.8<br>5.0<br>5.2<br>CO<br>7.1<br>3.2<br>3.4<br>1e<br>15<br>CH +<br>3<br>c)|[Ar II]<br>[Ar III]<br>[Ne II]<br>[Ne III]<br>2.5<br>2.6<br>2.7<br>2.8<br>8<br>9<br>1e<br>15<br>H2O<br>a)<br>4.8<br>5.0<br>5.2<br>CO<br>7.1<br>3.2<br>3.4<br>1e<br>15<br>CH +<br>3<br>c)|[S III]<br>H I<br>H2<br>He I<br>7.2<br>7.3|
|1<br>2<br>3<br>4|5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>2<br>Wavelength ( m)|5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>2<br>Wavelength ( m)|5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>2<br>Wavelength ( m)|


**Fig.** **1** JWST NIRSpec/IFU and MIRI/MRS combined spectrum of the d203-504 proplyd. The
vertical lines indicate the position of HI (dashed), He I (dotted) and H 2 (continuous) emission lines.
Fine structure lines of atoms are labeled directly on the figure. Three close-up views are displayed
in framed insets: water absorption at 2.7 µm in blue ( a)), CO absorption and emission at 4.7 µm in
purple ( b)) and CH 3 [+] emission at 7.2 µm in orange ( c)). Emission bands from PAHs are highlighted
in green.


limited UV influence. [20] have also shown that there is no clear signpost of externally UV-driven chemistry in the ALMA spectra of irradiated disks in the outskirts
of the Orion Nebula, where the FUV field is ≲ 10 [3] _G_ 0 . Recent models also indicate
that the inner disk’s C/O ratio may remain unaffected by external UV-driven photoevaporation [34]. These discrepancies suggest that the effects of UV radiation on disk
chemistry are complex, potentially varying between inner and outer disk regions. To
address these uncertainties, we turn to another externally UV-irradiated protoplanetary disk in Orion, d203-504, observed with JWST using both NIRSpec and MIRI
instruments (program id #1288).

### **Results**


The d203-504 (2MASS J05352025-0525037) protoplanetary disk is located in the Orion
Nebula, a few arcseconds southeast of the ionization front of the Orion Bar [35] and
_≈_ 1 _._ 7 _[′′]_ to the north of the protoplanetary disk d203-506 [36] (see Figure Extended
Data 1). Based on the geometry of the ionization front, d203-504 is predominantly
irradiated by the B star _θ_ [2] Ori A [36, 37], which is situated at a projected distance of
0.077 pc (40 _[′′]_ ) to the northeast. Taking the projected separation from the UV sources,
Haworth et al. [38] estimate the upper limit of the FUV radiation field received by


4

d203-504 is _G_ 0 = 8 _×_ 10 [4] in units of the Habing [26] field. Using recent observation
with the MUSE instrument on the VLT, the authors also derived the velocity of a
jet seen in [Fe ii] emission, associated with the Herbig Haro object HH 519 [36], being
typically 130 km s _[−]_ [1] . The central star is estimated to be a type K5.5 with a mass of
0.72 M _⊙_ [39, 40]. Parameters for d203-504 are summarized in Table 1.
Using the MUSE data presented in [38], we derive a disk size ( _r_ _d_ = 31 au) and
inclination ( _i ≥_ 54 _[◦]_ ) as shown in the Methods. d203-504 has also been observed with
ALMA (PI J. Champion) together with d203-506 [28]. d203-504 is detected only in the
continuum at 344 GHz (Figure Extended Data 2), from which we derive an estimated
disk mass of _M_ _d_ = 1 _._ 3 _−_ 5 _._ 6 M Jup (see Methods).


**Table** **1** Summary of d203-504 disk main properties


Parameter Value(s) Origin
_D_ Distance 390 pc 3
_T_ _⋆_ Stellar type, temp. K5.5, 4160 K 2
_r_ _⋆_ Stellar radius 0.7 R _⊙_ 2
_M_ _⋆_ Central star mass 0.72 M _⊙_ 2
_V_ sys Systemic velocity 25 km s _[−]_ [1] 1
_G_ 0 Radiation field ≲ 8 _×_ 10 [4] 1
_MMV_ ˙˙ JetPEacc PhotoevaporationAccretionJet velocityrate rate 2 _._ 5 _−_ 8.27 _×._ 130910 _×_ _[−]_ 10km [9] M _[−]_ s _⊙_ [7] _[−]_ M [1] yr _⊙_ _[−]_ yr [1] _[−]_ [1] 1,2,414
_r_ _d_ Disk radius 31 au (0.08 _[′′]_ ) 4
_E_ _d_ Disk thickness 46 au (0.12 _[′′]_ ) 4
_i_ Disk inclination ≳ 54 _[◦]_ 4
_F_ 344 Dust flux at 344 GHz 7.4 mJy 4
_M_ disk Disk mass 1.3–5.6 M Jup 4


1: [38], 2: [40], 3: [41], 4: this work.


d203-504 was observed as part of the JWST early release science program
PDRs4All [42] with NIRCam [43], MIRI MRS [44] and NIRSpec IFU [45]. Those
observations are presented in [27], [46, 47], and [29], respectively. In Figure 1,
we present the background subtracted combined NIRSpec-MIRI spectrum of this
source (see Methods). This spectrum is characterized by a strong near-infrared
continuum. This continuum is well fitted by a 1180 K blackbody, with a luminosity
_L_ NIR = 0 _._ 13 L _⊙_ (see Methods). This near-infrared excess is most likely related
to viscous heating˙ linked to accretion. The derived luminosity corresponds to an
accretion rate of _M_ acc = 8 _._ 2 _×_ 10 _[−]_ [9] M _⊙_ yr _[−]_ [1], typical for young T-Tauri stars [48].
Emission from the characteristic bands of PAHs are well detected at 3.3, 6.2, 7.7, 8.6,
11.2, 12.7 µm as well as several other fainter bands, also seen in the Orion Bar with
JWST [47]. We note that this PAH emission clearly arises from the disk, as there is
a strong excess in emission in all PAH bands with respect to the background nebula
(see Figure Extended Data 3). A broad feature between 7 and 13 µm, corresponding
to the emission of hot silicate grains, is also present (this feature is best seen in the
spectrum presented in Figure Extended Data 4). In addition to these dust-related
features, numerous atomic and molecular lines are present (Figure 1). These include
fine structure lines from atoms and atomic ions, recombination lines of H and He,


5

and molecular hydrogen lines. The full list of lines and assignments is provided in
Tables Extended Data 1 and Extended Data 2. We also detect spectroscopic signatures from several molecules, with NIRSpec: H 2 O _v_ = 1 _→_ 0 _, ν_ 1 _, ν_ 2 symmetrical and
asymmetrical stretching, in absorption, between 2.5 and 2.9 µm (to our knowledge,
this is the first time these near IR H 2 O bands are detected in protoplanetary disks
as they are very difficult to observe from the ground); CO _v_ = 1 _→_ 0, _v_ = 2 _→_ 1 in
emission and absorption around 4.4 – 5 µm. In addition, we tentatively detect several
OH and CH [+] lines (see Figure Extended Data 5). With MIRI, we detect the CH 3 [+] _[ν]_ 2 [+]
out-of-plane and _ν_ 4 [+] [in-plane] [dyad] [modes] [[][30][,] [49][]] [near] [7.2] [µ][m.] [Finally,] [we] [note] [that]
HCN, C 2 H 2 or CO 2 emission signatures that are commonly detected in isolated disks
are not seen in d203-504. The molecular detections, and non-detections, reported here
bring an additional piece to the puzzle of chemistry in externally irradiated disks. In
the following, we address the origin of the spectral signatures seen in emission and in
absorption in d203-504.


We first focus on the strongest detections observed in emission arising from the
UV-irradiated neutral layer at the disk surface, that is CH 3 [+] [,] [H] 2 [,] [and] [PAHs.] [CO] [is]
also detected in emission, but the broad emission profiles suggest that this emanates
from the outflow or wind rather than the disk itself (see Methods). CH 3 [+] emission
has recently been detected in the d203-506 externally irradiated disk [30], the isolated
disk TW Hya [4], and the Orion Bar PDR [50]. This cornerstone cation is attested to
be formed through a chemical reaction sequence initiated by the reaction of C [+] and
vibrationally excited H 2 by FUV radiation [50]. CH 3 [+] is thus a chemical marker of
FUV driven chemistry. We model the emission of CH 3 [+] (see Methods) and find an
excitation temperature of _T_ ex = 1000 _±_ 100 K, slightly higher but close to that found
in d203-506 ( _T_ ex = 660 _±_ 80 K by [49]) and for the Orion Bar (1250 _±_ 250 K, [50]).
The column density of CH 3 [+] [is] _[N]_ CH [+] 3 [=] [4] _[ ×]_ [ 10] [13] [cm] _[−]_ [2] [(see] [Methods).] [This] [is] [higher]
than the value reported by [49] for d203-506 ( _N_ CH +3 [= 5] _[ ×]_ [ 10] [11] [cm] _[−]_ [2] [),] [however] [these]
latter authors considered a beam averaged value whereas we use the physical size
of the disk (see Methods). In Figure 2, we present the extracted PAH spectrum of
d203-504 (see Methods) and compare it to the Orion Bar atomic PDR zone [47]. The
two spectra are very similar, indicating that PAHs in d203-504 have a composition
close to that of the Orion Nebula. Following the analysis of [28], we use the observed
H 2 fluxes (Table Extended Data 3) in the detected ro-vibrational lines coupled with
the Meudon PDR code [51] to derive the physical conditions in the PDR on the
disk surface (see Methods). The best fit model is shown in Figure 2c, and yields a
gas temperature _T_ gas = 1240 K, a hydrogen˙ number density _n_ H = 3 _._ 1 _×_ 10 [7] cm _[−]_ [3],
and a photoevaporation mass-loss rate _M_ PE = 7 _._ 9 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1], slightly higher
than earlier indirect estimates under the˙ assumption of photoionization equilibrium
( _M_ [˙] PE = 2 _._ 5 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1], [40] and _M_ PE = 3 _._ 1 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] ). Overall, CH 3 [+] [,]
H 2, and PAH emissions are clear indications of active photochemistry taking place
in the _n_ H _∼_ 10 [7] cm _[−]_ [3] PDR formed at the surface of the disk by irradiation from
external FUV photons.


6

6


4


2


0


3


2


1


0


1


2


3



6 8 10 12 14
Wavelength ( m)



b) c)

1e 16



10 3


10 4


10 5







7.00 7.05 7.10 7.15 7.20 7.25 7.30 7.35
Wavelength ( m)


**Fig.** **2** Analysis of PAH, CH 3 [+] and H 2 emissions in d203-504. a) Continuum subtracted PAH
spectrum ( _F_ PAH ( _λ_ ), see Methods) in arbitrary units, for d203-504 (gray) and the Orion Bar PDR
(green). b) Continuum subtracted spectrum of d203-504 ( _F_ obs ( _λ_ ) _−_ _F_ cont ( _λ_ ), see Methods) in the
spectral region of CH 3 [+] emission, in dark gray and the best fit model in blue. c) Comparison between
the observed (blue) and modeled (orange) H 2 line intensities using the Meudon PDR model. Error
bars represent a total uncertainty of 50% used in the minimization to obtain the best fit model.
The instrumental uncertainties are smaller than the point size and given in Table Extended Data 4.
Notations of H 2 transitions on the x-axis are abbreviated. The corresponding quantum levels are
given in Table Extended Data 3.


We then model the absorption in the _v_ = 1 _→_ 0 and _v_ = 2 _→_ 1 vibrational
bands of CO, as well as the _v_ = 1 _→_ 0, _ν_ 1, and _ν_ 2 bands of H 2 O, observed against
the bright infrared continuum, using a simple slab model at local thermodynamical
equilibrium (see Methods). The best-fit models, shown in Figure 3, yield excitation
temperatures of _T_ H 2 O = 850 _±_ 250 K and _T_ CO = 1150 _±_ 350 K, with column densities
of _N_ H 2 O = (9 _±_ 1) _×_ 10 [17] cm _[−]_ [2] and _N_ CO = (8 _±_ 1) _×_ 10 [17] cm _[−]_ [2] . The high temperatures
( _T_ ex _∼_ 1000 K) combined with the absorption seen against the hot ( _T_ NIR = 1180 K)
inner disk emission at a similar temperature indicate that H 2 O and CO originate in
the inner disk. In addition, we show in the Methods, and Figure Extended Data 6
that the absorption of water in the _ν_ 2 bending mode supports this interpretation as
well. The column densities derived for H 2 O and CO are also compatible with those
found in the inner disks of isolated young stars (e.g. [52, 53]). These molecules must be
slightly cooler than the dust to produce absorption. The hot dust continuum is emitted
from a region with an outer radius of _r_ out = 0 _._ 047 au (Methods). Assuming a radial
temperature profile for the dust, _T_ _d_ ( _r_ ) = _T_ NIR ( _r/r_ out ) _[−]_ [3] _[/]_ [4] [54], and a water freeze-out
temperature of 150 K implies that the water snowline is located at _r_ snow = 0 _._ 73 au.


7

Therefore, the observed water absorption arises from within this radius. The inner
disk column densities of H 2 O and CO are derived from absorption, and thus do not
depend on an emitting surface area (Eq. 8). The absence of other spectral signatures
in absorption, indicates these molecules are likely the main carriers of carbon and
oxygen. In addition, the excitation temperature for the two species are compatible
within errors, suggesting they are located in the same region. Therefore, we can derive
an estimate of the C/O ratio in the inner disk using C/O= _N_ CO _/_ ( _N_ CO + _N_ H 2 O ) =
0 _._ 47 _±_ 0 _._ 07, consistent with the Solar value of 0 _._ 51 _±_ 0 _._ 06 [55], and the value derived
for the Orion Nebula, 0 _._ 52 _±_ 0 _._ 18 [56].


0.2


0.1


0.0





0.1


0.4


0.2


0.0


0.2


0.4




|a)|Col2|
|---|---|
|NH2O = 9.1 ± 1.4 ×1017 cm<br>2<br>TH2O = 850 ± 250 K|H2O <br>obs<br>Model<br>abs|








|2.5 2.6 NH2O = 9.1 ± 1.4 ×1017 cm 2 TH2O = 850 ± 250 K|2.7 2.8 2.9 H2O obs Model abs|
|---|---|
|b)||
|NCO = 8.1 ± 1.0 ×1017 cm<br>2<br>TCO = 1150 ± 350 K|CO<br>obs<br>Model<br>abs|



4.4 4.5 4.6 4.7 4.8 4.9 5.0
Wavelength ( m)


**Fig.** **3** Optical depth spectra of water and carbon monoxide absorption in the inner disk of d203504. a) Water absorption optical depth spectrum derived from the observations ( _τ_ obs, see Methods),
in black, and best fit model ( _τ_ abs ) shown in negative, in blue. b) Carbon monoxide absorption optical
depth spectrum derived from the observations, and best fit model in blue. The gray areas correspond
to regions of contamination by strong atomic lines where the data has been excluded from the fit.
Column densities and temperatures obtained with the best fit models are indicated.

### **Discussion**


The analysis of the molecular emission and absorption observed with JWST in the
spectrum of d203-504 points to the existence of two distinct chemical regions in the
disk, as depicted in Figure 4. H 2 O and CO observed absorptions originate from the
inner disk ( _r_ ≲ 1 au), while CH 3 [+] [,] [H] 2 [,] [and] [PAH] [emissions] [originate] [from] [the] [PDR]
at the base of the FUV driven photoevaporation flow extending to the outer disk
( _r_ ≳ 1 au).
In the inner disk, within the snowline, water is present in the gas phase. The
presence of large column densities of gas phase H 2 O in the inner disk, together with
the absence of OH emission, implies that water is not photodissociated by UV, and
thus shielded from UV radiation in these dense regions of the disk [57, 58]. This
indicates that the inner disk chemistry (in the sense of the chemical reactions that


8

occur) is not directly affected by the external FUV radiation, and instead driven by
ice sublimation at the surface of viscously heated dust, as observed in isolated disks

[3, 4, 7, 59]. The detection of water in absorption in d203-504, as opposed to its absence
in d203-506, likely arises from d203-504’s geometry having a favorable vewing angle. In
contrast, d203-506 is almost perfectly edge-on, causing the disk to obscure the warm
dust emission and any associated water absorption from the inner regions.
The C/O ratio (0.48) and absence of hydrocarbons (e.g. C 2 H 2, HCN) in the inner
disk indicates the gas is oxygen rich, with a value close to Solar and to the ISM of the
Orion Nebula. This value can be interpreted in the context of the recent models of

[34], which predict the evolution of the C/O ratio in the inner regions of an externally
irradiated disk. According to these models, a Solar C/O ratio in the inner disk is
compatible only with two cases: either a very young ( _<_ 1 Myr) disk that has not
evolved viscously yet, or a more evolved disk ( ≳ 2 Myrs) where some carbon reenrichment of the inner disk has already occurred. The first scenario is compatible
with the expected young age of the Orion Nebula Cluster ( _∼_ 1Myr [60]) and the fact
that highly irradiated disks like d203-504 are unlikely˙ to live more than a million
years. With a photoevaporation mass-loss rate _M_ PE _∼_ 3 _×_ 10 _[−]_ [7] M _⊙_ yr _[−]_ [1] and a disk
mass _M_ d _<_ 6M Jup, the disk depletion time scale is only 20,000 years. This scenario
is also compatible with the presence of PAHs indicating recent inheritance from the
ISM (whereas PAHs are rarely found in more evolved isolated disks [32]). The second
scenario implies that the disk has been shielded from external UV radiation at an
earlier point in time, and also that the Orion Nebula is somewhat older (a few Myrs,

[61]). In any case the C/O ratio in the inner disk of d203-504 is consistent with that
of a young, isolated, viscously evolving disk around a Solar-type star.
The upper layers of the d203-504 disk, extending to its outer edge ( _r_ d = 31 au)
and observed in emission with JWST, are strongly influenced by UV radiation. In
these regions, a PDR is formed, where chemistry is driven by ionized carbon and
FUV–pumped H 2 . This results in the formation of reactive species such as CH [+] and
CH 3 [+] [30, 62], while water is photodissociated into OH radicals [31]. PAHs are also
present in this PDR, exhibiting emission properties similar to those observed in the
Orion Bar (Figure 2). This similarity suggests a common origin, with PAHs in d203504 either inherited from the parent nebula during disk formation—potentially locked
in ices or larger grains and later released by FUV-driven photo-chemical processing

[63, 64]—or formed in situ via gas-phase reactions in the PDR [65]. PAHs are simultaneously subject to UV-induced processing (e.g., removal of labile aliphatic CH bonds

[66]) and destruction via photodissociation [67, 68] or reactions with oxygen [69]. An
important question is how this surface-layer photochemistry influences the disk midplane, where planets form. The observed species in the PDR are embedded in hot
gas that escapes the disk’s gravitational potential in a photoevaporative flow. Unless
vertical mixing driven by turbulence is particularly efficient [70], these species will be
lost in the wind rather than incorporated into the midplane. However, in the scenario
where vertical mixing is efficient, Lange et al. [71] proposed that PAHs could evolve
through a processing cycle during which they mix into the UV depleted layers where
they collide, leading to sticking and eventually freeze out on dust grains. Small clusters
of PAHs whould desorb while the large ones would remain on the grains. Repetitions of


9

**Fig.** **4** Chemical structure in the solar-type d203-504 Proplyd. a) Sketch of the inner disk (≲ 1 au),
composed of hot dust grains and water vapor heated by accretion processes. This heating sets the
position of the snowline, that is, the radius at which the water vapor can freeze-out on dust grains,
at _r_ _∼_ 0 _._ 7 au (vertical dashed line). b) Sketch of the outer disk (≳ 1 au). The surface layers host a
photodissociation region with photo-chemistry involving CH [+], CH 3 [+] [,] [OH] [and] [PAHs] [driven] [by] [the]
FUV photons from nearby massive stars. This PDR triggers mass-loss by photoevaporation.


this cycle would lead to depletion of gas-phase PAHs while large clusters would remain
on dust grains. In Figure 5, we compare the fraction of the derived cosmic carbon
abundance locked in PAHs in d203-504 ( _f_ _C_ [PAH] = 2 _._ 9 _×_ 10 _[−]_ [3], see Methods) with that
of the ISM and the Solar System. The observed trend suggests a progressive depletion
of PAHs over time, consistent with their destruction at the disk surface. This implies
that a reduced fraction of PAHs compared to the ISM are incorporated into the solids
of planetary systems exposed to strong UV. PAHs represent a potentially significant


10

carbon reservoir, traditionally thought to contribute to the gas-phase carbon at the
“soot line” in protoplanetary disks, fueling a rich organic chemistry [3, 10, 72, 73].
However, in disks like d203-504, where PAHs are destroyed at the surface, the soot line
may be suppressed (which is also compatible with the absence of small hydrocarbons
discussed hereabove and might be an indirect effect of external UV on the inner disk).
This selective loss of PAHs while oxygen-rich grains remain gravitationally bound suggests that externally UV-irradiated disks are likely to remain oxygen-rich. The loss
of PAHs also reduces UV opacity and photoelectric heating efficiency in the PDR,
potentially altering gas heating, chemistry, and photoevaporation dynamics [74].
To fully understand the impact of UV irradiation on the chemical composition
of planet-forming material, future efforts must couple dynamical and photo-chemical
models of irradiated disks with extensive observational surveys of externally illuminated disks in various star-forming regions.


10 2



10 3







**Fig.** **5** Fraction of the available cosmic carbon abundance locked in PAHs. Those fractions are
measured at different times of the stellar evolution (from older to more recent, left to right). The
Orion Bar and NGC 7023 are photodissociation region in star-forming regions. HST10 is a proplyd in
Orion, situated closer to the Trapezium cluster with respect to d203-504 with _G_ 0 _∼_ 2 _×_ 10 [5] . Ryugu
is a type C asteroid and is used as an approximation for the Solar System. See Methods for details
on the derivation of PAH abundances presented in this figure.

### **Correspondence**


Correspondance and request for materials should be addressed to Ilane Schroetter,
ilane.schroetter@gmail.com.


11

### **Methods**

**MUSE** **observations** **of** **d203-504**


The MUSE observations used in this paper are described in details in [38]. Left panel of
Figure Extended Data 1 shows composite image of both d203-506 (lower left) and d203504 (top right) systems created using those data. d203-504 shows a clear ionization
front in H _α_, faint jets in [Fe ii] and the disk in [CI]. Right panel of Figure Extended
Data 1 shows the same field of view but with JWST/NIRCam observations. On this
panel, d203-504 is saturated. The [CI] emission line is a tracer of the disk surface

[40, 62, 75]. We thus fit a 2D Gaussian to this emission and obtain a disk radius _r_ _d_ _∼_ 31
au (0.08 _[′′]_ at 390 pc), corresponding to the semi-major axis divided by two, and a disk
thickness _E_ d _∼_ 46 au (0.12 _[′′]_ ), corresponding to the semi-minor axis. In addition, we
can obtain an estimate of the lower limit for the disk inclination _i_ (the inclination
convention here is to be 0 _[◦]_ for an face-on disk and 90 _[◦]_ for edge-on configuration),
following the method of [28]. That is, _i_ ≳ 90 _−_ arctan( 2r [E] [d] d [),] [yielding] _[i]_ [≳] [54] _[◦]_ [.] [This]

estimation is in agreement with the jet being tilted by at least 45 _[◦]_ [38].


**ALMA** **observations** **of** **d203-504**


The ALMA data and associated data reduction used in this paper was presented
in details in [76]. In Figure Extended Data 2 we show the 344 GHz ALMA dust
continuum emission map of d203-506 and d203-504. We extract a flux for d203-504
_F_ 344 = 7 _._ 4 mJy using a 2D Gaussian fit. The disk, however, is not resolved in the
ALMA observations and thus cannot provide with another estimate of the disk size.
Following the method presented in [77] (see also [76]) we derive a disk mass range
of 1.3–5.6 M Jup using this flux. This range of values stems from the uncertainties on
the value of the _κ_ _ν_ parameter, the dust grain opacity, and the optical depth of the
emission at 344 GHz. This is explained in details in [76]. We also note that d203504 is present in the VLA catalog of [78] and has a peak intensity of 0.1886 mJy at
their reference frequency of 6.1 GHz. However, the 344 GHz ALMA data has a peak
intensity of _∼_ 3 _._ 0 mJy and is peaked at the disk position, not at the ionization front.
Thus the ALMA 344 GHz emission must be largely dominated by the thermal dust
rather than free-free emission.


**JWST** **observations** **and** **data** **reduction.**


Observations were performed with the JWST-NIRSpec and JWST-MIRI-MRS Integral Field Units (IFUs) as part of the PDRs4All ERS program [42]. They were
reduced using the JWST pipeline version 1.10.2 with calibration reference data
system (CRDS) context file jwst ~~1~~ 084.pmap. Data cubes are a combination of 9
pointings, forming a mosaic spanning across the Orion Bar. The detailed data reduction together with a general analysis of line emissions are described in [29] and [3, 47]
for NIRSpec-IFU and MIRI MRS, respectively. To extract the d203-504 spectrum,
we first take a circular aperture of 0.40 _[′′]_ radius centered on d203-504 coordinates
(right ascension (RA)=5:35:20.268 and declination (DEC)=-05:25:03.992), which we


12

call “ON”. Then, in order to subtract the background emission from the nebula,
we extract a spectrum of similar aperture (0.365 _[′′]_ ) at coordinates RA=5:35:20.370
and DEC=-05:25:04.97 where no obvious object can be detected(we note that this
background spectrum, for consistency, is extracted using the same aperture and position as used by [30] and [76]). We call this position “OFF”. The “ON” and “OFF”
spectra are shown in Figure Extended Data 3. Finally the d203-504 spectrum _F_ obs ( _λ_ )
is obtained by subtracting “OFF” from “ON” which is shown in Figure 1.


**Details** **on** **line** **identification.**


Lines from atomic ions and H 2 in the JWST spectrum of d203-504 (Figure 1) are identified using the line list provided by the PDRs4All ERS [team(http://hebergement.](http://hebergement.u-psud.fr/edartois/jwst_line_list.html)
[u-psud.fr/edartois/jwst](http://hebergement.u-psud.fr/edartois/jwst_line_list.html) ~~l~~ ine ~~l~~ ist.html) and benchmarked on the Orion Bar spectroscopic data [3, 29]. Numerous strong H i emission lines (from 4 _→_ 20 to 14 _→_ 43) are
detected as well as several ionic lines including Mg ii, [Ar ii], [Ar iii], [Ne ii], [Ne iii],

[S ii], [Si iii], [Fe ii] and [Fe iii]. For H 2, we detect the _v_ = 0 _→_ 0, _v_ = 1 _→_ 0, _v_ = 1 _→_ 1,
_v_ = 2 _→_ 0, _v_ = 2 _→_ 1, _v_ = 3 _→_ 2, _v_ = 3 _→_ 1, _v_ = 4 _→_ 3 and _v_ = 4 _→_ 2 transitions
in emission. Table Extended Data 1 lists the strongest atomic and H 2 lines detected
and their corresponding intensities. Each detected emission line is fitted using a Gaussian with a FWHM corresponding to the instrument PSF plus a linear continuum. We
integrate the result of the Gaussian fit to derive the intensity


**Stellar,** **dust** **and** **PAH** **continuum** **emission**


We model the continuum flux of d203-504 observed in the NIRSpec and MIRI ranges
using the sum of the emissions from the star _F_ _⋆_, near-infrared emission from the inner
disk, _F_ NIR, and mid-infrared emission from the outer disk, _F_ MIR :


_F_ cont ( _λ_ ) = _F_ _⋆_ ( _λ_ ) + _F_ NIR ( _λ_ ) + _F_ MIR ( _λ_ ) _,_ (1)


where

_F_ _⋆_ ( _λ_ ) = [4] _[π]_ _[r]_ _⋆_ [2] _B_ ( _λ, T_ _⋆_ ) _e_ _[−][τ]_ [1] _[µm]_ _,_ (2)
_d_ [2]

[(] _[r]_ out [2] _[−]_ _[r]_ in [2] [)]
_F_ NIR ( _λ_ ) = _[π]_ _B_ ( _λ, T_ NIR ) _e_ _[−][τ]_ [3] _[µm]_ _,_ (3)
_d_ [2]

_F_ MIR ( _λ_ ) = � _B_ ( _λ, T_ MIR _[i]_ [) +] _[ AIB]_ [(] _[λ]_ [)] _[.]_ (4)


_i_

In the above equations, _B_ is the Planck function, _r_ _⋆_ is the radius of the star, and
the stellar temperature _T_ _⋆_ = 4160 K [40]. _T_ NIR is the dust temperature in the inner
disk. _r_ in is the inner radius of the disk, determined by the sublimation radius of the

_L_ _⋆_
dust, that is, _r_ in = 0 _._ 07 � _L_ _⊙_ [= 0] _[.]_ [037] [au] [following] [[][54][].] _[r]_ [out] [is] [the] [outer] [radius] [of] [the]

hot inner disk. _T_ MIR _[i]_ [are] [the] [mid-infrared] [dust] [emission] [temperatures,] [and] _[AIB]_ [(] _[λ]_ [)]
stands for the emission from the aromatic infrared bands of PAHs, modelled using a
collection of Gaussians as described in detail in [79]. The exponential factors in Eqs. 2
and 3 are a correction for the line of sight extinction, with _τ_ 1 _µm_ and _τ_ 3 _µm_ the optical


13

depths at 1 and 3 _µ_ m, respectively. The values of _τ_ 1 _µm_ and _τ_ 3 _µm_ are computed using
the extinction curve from [80] with Rv = 5.5, for a visual line of sight extinction
towards the star _A_ _V_ = 3 as derived from [40] for d203-504. This yields _τ_ 1 _µm_ = 4 _._ 8
and _τ_ 3 _µm_ = 0 _._ 25. Figure Supplementary 1 shows the fit of _F_ cont ( _λ_ ) to the observed
spectrum _F_ obs ( _λ_ ). The fit results provide the values of _T_ NIR = 1180K, _r_ out = 0 _._ 047
au.to anTheaccretionnear infraredrate _M_ ˙luminosity acc = 2 _r_ _⋆_ _L_ is NIR _L/_ NIR ( _GM_ = _⋆_ � ) = 8 _F_ NIR _._ 2( _×λ_ ) 10 _dλ_ _[−]_ = 0 [9] M _._ 13 _⊙_ _/_ yr. _L_ _⊙_ . This corresponds


**d203-504** **disk** **PAH** **spectrum**


In Figure Extended Data 3 we present the MIRI ON and OFF spectra of d203-504. We
fit both continua in these spectra using a collection of black bodies with the PAHTAT

[79] tool. We subtract these continua to the ON and OFF spectra so that they contain
only the ON and OFF PAH emissions. We then subtract the OFF PAH emission to
the ON PAH emission (Figure Extended Data 3). This yields the disk PAH emission
(Figure Extended Data 3). The disk PAH emission is presented in Figure 2 together
with the continuum subtracted Orion Bar spectrum which was obtained with the same
method, applied to the template spectrum “Atomic PDR” of [47].


**Carbon** **fraction** **locked** **in** **PAHs**


To derive the abundance of PAHs in d203-504, expressed as the fraction of carbon
locked in PAHs _f_ _C_ [PAH] we follow the method presented in [81] (Eq. 1), relying on the
8.6 µm PAH intensity, _I_ 8 _._ 6 :


_I_ 8 _._ 6 = _ϵ_ 8 _._ 6 _f_ C [PAH] [C] _[G]_ [0] _[,]_ (5)

[H] _[N]_ [H]


where _f_ _C_ _[P AH]_ is the fraction of elemental carbon locked in PAHs, _N_ H is the column
density of hydrogen atoms in the line of sight, [ [[] _H_ _[C]_ []] ] [is] [the] [abundance] [of] [carbon] [relative]

to hydrogen atoms (1 _._ 6 _×_ 10 _[−]_ [4] ), and _ϵ_ 8 _._ 6 is the PAH emissivity at 8.6 µm, with
_ϵ_ 8 _._ 6 = 4 _._ 5 _×_ 10 _[−]_ [18] MJy/sr/cm _[−]_ [2] / _G_ 0 [81]. Using the extracted PAH spectrum _F_ PAH ( _λ_ ),
we derive an intensity _I_ 8 _._ 6 = _F_ PAH (8 _._ 6 _µm_ ) = 862 MJy _/_ sr. Using _G_ 0 = 8 _×_ 10 [4] and
_N_ H = 5 _._ 5 _×_ 10 [21] cm _[−]_ [2] as in [81], we compute a value _f_ _C_ [PAH] = 2 _._ 9 _×_ 10 _[−]_ [3] .
The abundance for HST 10 is taken from [81], _f_ _C_ [PAH] = 8 _._ 0 _×_ 10 _[−]_ [4] . The abundance
for Orion Bar is from [82] ( _f_ _C_ [PAH] = 3 _._ 7 _×_ 10 _[−]_ [2] ) and for NGC 7023 ( _f_ _C_ [PAH] = 3 _._ 2 _×_ 10 _[−]_ [2] )
from [83].
The abundance in the asteroid Ryugu is computed using the result from the
Hayabusa mission. From [84] (Figure 2), we obtain a concentration of 70 nmol/g for
C 16 H 10 (Pyerene + Fluoranthene). From [85] (Figure 6), we obtain a signal of 11576
counts for condensed aromatics with over 30 C atoms ( _N_ C _>_ 30), which are interstellar PAH candidates, whereas the ion signal for C 16 H 10 is 14535 counts. Therefore, the
abundance of large _N_ C _>_ 30 PAHs can be estimated by 70 _×_ 11576 _/_ 14535 = 56 nmol/g.
The averaged molar mass of large condensed PAHs (C 38 H 16 ) is 472 g/mole. Therefore,
the mass fraction of large PAHs is estimated to be 56 _×_ 10 _[−]_ [9] _×_ 472 = 2 _._ 6 _×_ 10 _[−]_ [5] . The


14

total carbon abundance in Ryugu is 4.6 % of the total mass [86], thus the fraction of
carbon locked in PAHs in Ryugu is derived to be _f_ _C_ [PAH] = 5 _._ 7 _×_ 10 _[−]_ [4] .


**Fit** **of** **rovibrational** **H** **2** **lines** **with** **the** **Meudon** **code**


17 lines of molecular hydrogen are detected towards d203-504. Their intensities are
reported in Table Extended Data 3. In order to determine the physical conditions of
the H 2 emitting gas, we use the Meudon PDR code [87] to fit these intensities. We
used a grid of constant density PDR models produced with the Meudon PDR code
(version 7.0, publicly available at [pdr.obspm.fr),](https://pdr.obspm.fr/pdr_download.html) with extinction properties typical
of dense molecular gas as used in [27] for the Orion Bar (Rv = 5.5, NH/E(B-V) =
1.6 _×_ 10 [22] cm _[−]_ [2] ), an extinction curve using the fit of [89] for HD38087, and a power-law
grain size distribution extending from 3 nm to 0.3 microns (the model grid is publicly
available at [app.ism.obspm.fr/ismdb).](https://app.ism.obspm.fr/ismdb/) [28] have shown for a similar analysis that the
use of larger grains does not affect strongly the results. We account for geometrical
effects (beam dilution, inclination of PDR surface with respect to the line of sight and
to the direction of irradiation) by adding a single geometrical scaling parameter alpha
applied to all H 2 line intensities, as all detected H 2 lines are expected to be optically
thin. We restrict our search of a best fitting model to _G_ 0 values between 2 _×_ 10 [4] and
8 _×_ 10 [4] to account for the previous constraint provided by [38], and to values of the
geometrical scaling factor alpha between 0.1 and 10, as more extreme values would
correspond to unlikely geometries. The range of gas densities explored goes from 1 _×_ 10 [1]

to 1 _×_ 10 [10] cm-3. The best fitting model has a gas density n _H_ = 3.1 _×_ 10 [7] cm-3, a _G_ 0
= 2 _×_ 10 [4] and a geometrical scaling factor alpha = 0.1.


**Photoevaporation** **mass** **loss** **rate**


˙
Following [76], we compute the photoevaporation mass-loss rate using _M_ PE =

_S_ PE _µ_ _m_ H _n_ H _c_ _s_, with _c_ S _≡_ ~~�~~ 7 _/µ_ 5 _km_ B _T_ Hgas =3.3 km s _[−]_ [1], where _k_ B is the Boltzmann con
stant, _m_ H is the mass of hydrogen and _µ_ is the ratio of total mass over hydrogen mass
of interstellar gas ( _µ_ = 1 _._ 4 [80]). The emitting photoevaporation surface area _S_ PE is
computed using an ellipsoid [76]:



_S_ PE = 2 _πr_ _d_ [2] [+] _[π]_ [(] _[E]_ _[d]_ _[/]_ [2][)] [2]



(6)
1 _−_ _e_ _[,]_




_[d]_ _[/]_ [2][)]

ln [1 +] _[ e]_
_e_ 1 _−_ _e_



thiswhereyieldsthe ellipticity _M_ ˙ PE = 7 _._ 9 _e ×_ = 10 ~~�~~ _[−]_ 1 [7] _−_ M( _⊙_ _E_ yr _d_ _/_ _[−]_ 2) [1][2] . _/r_ _d_ [2] [.] [With] [the] [parameters] [reported] [in] [Table] [1][,]


**H** **2** **O,** **CO,** **CH** **3** **[+]** **[absorption]** **[and]** **[emission]** **[modeling]**


**Analytical** **models**


To model H 2 O, CO, CH 3 [+] [features] [observed] [in] [the] [data,] [we] [utilize] [slab] [models.] [To] [fit]
the flux of d203-504 in spectral regions with molecular emission we use:


_F_ mod _[em]_ [(] _[λ]_ [) =] _[ S][ ×][ B]_ [(] _[λ, T]_ [ex] [)(1] _[ −]_ _[e]_ _[−][τ]_ [ em] [(] _[λ,T]_ [ex] [)] [) +] _[ F]_ [NIR] [(] _[λ]_ [) +] _[ F]_ [MIR] [(] _[λ]_ [)] _[,]_ (7)


15

where _S_ is the area of the emitting surface, _B_ _λ,T_ the Planck function and _τ_ [em] ( _λ_ ) is
the molecular emission optical depth. _F_ _⋆_ and _F_ NIR, _F_ MIR are defined in Eqs. 2, 3, 4,
respectively. For the absorption, we use:


_F_ mod [abs] [(] _[λ]_ [) = (] _[F]_ _[⋆]_ [(] _[λ]_ [) +] _[ F]_ [NIR] [(] _[λ]_ [))] _[ ×][ e]_ _[−][τ]_ [ abs] [(] _[λ,T]_ [ex] [)] [ +] _[ F]_ [MIR] [(] _[λ]_ [)] _[,]_ (8)


where _τ_ [abs] ( _λ, T_ ex ) is the molecular absorption optical depth and _T_ ex is the excitation temperature. In this case, since the molecules are seen in absorption, the fitting
procedure is thus independent of the emitting surface area. We note that only the
near infrared component of dust emission ( _F_ NIR ) is absorbed in this model. This is
motivated by tests on H 2 O absorption: the best-fit models for the _v_ = 1 _→_ 0 _, ν_ 1 _, ν_ 2
stretching modes show excess absorption in the _ν_ 2 rovibrational band in the MIRI
spectrum when both _F_ NIR and _F_ MIR contribute to the background for absorption
(Figure Extended Data 6). This confirms that water absorbs only the near infrared
emission from the inner hot disk. The optical depths (emission and absorption) are
defined by _τ_ ( _λ, T_ ex ) = _σ_ ( _λ, T_ ex ) _× N_ with _σ_ ( _λ, T_ ex ) the molecular cross section for an
excitation temperature _T_ ex, and _N_ the species’ column density. For H 2 O and CO we
use the cross sections from the ExoMol database [90]. For CH 3 [+] [we] [rely on] [the] [spec-]
troscopic constants provided by [49]. We use the pgopher software [91] to directly
compute the cross section assuming a Boltzmann distribution to calculate the population in the upper state and no population in the lower state. For each molecule,
_σ_ ( _λ, T_ ex ) is convolved with a Gaussian line profile whose full width half maximum
(FWHM) is the sum of the instrumental line spread function (derived using a Gaussian fit on narrow emission lines, which typically gives a FWHM of _≈_ 120 km s _[−]_ [1] .)
and the line Doppler broadening ∆ _V_ expressed in velocity space. In addition, the
cross section is shifted in wavelength in order to account for the Doppler shift of the
emitting/absorbing gas with respect to its vacuum rest wavelength. This shift _V_ is
given here with respect to the systemic velocity _V_ sys = 25 km s _[−]_ [1] (see Sect. 2.1 in

[38]). _V_ and ∆ _V_ are results of the fitting procedure and are thus not expected to have
preferred values. All models are optically thin, thus the surface _S_ in equation 7 and
associated column densities are degenerate and cannot be constrained independently.
Thus, for the emissions, the column densities are computed assuming a realistic surface. For CH 3 [+] [we consider extended emission from the photodissociation region at the]
disk surface formed by external far-UV photons from _θ_ [2] Ori A. This case is similar to
the emission observed in d203-506 [76]. Thus, we use _S_ = _πr_ d [2] [.] [For] [the] [CO] [emission,]
since the origin is not precisely known, we use this same value for _S_ .


**Fitting** **procedure**


The models of Eqs. 7 for the emission and 8 for the absorption, are fitted to the
observations. To do this, we compute a grid of models _F_ mod ( _λ_ ), with varying values
of _T_ ex and _N_ . We then compute the residuals _R_ = ~~�~~ _F_ obs [2] _[−]_ _[F]_ [ 2] mod [as] [a] [function] [of]
these two parameters. Figure Supplementary 2 shows an example of the variation of
the residuals as a function of _T_ ex and _N_ for the case of H 2 O and CO absorptions. The
minimum of the residuals provides the best fit model. The uncertainties on _T_ ex and _N_
correspond the values for these parameters found 10% above the minimum residual.


16

The resulting values of _T_ ex and _N_ for all species are presented in Table Extended
Data 4. Hereafter we describe in more details how the fits were performed for specific
spectral signatures.
For the CO emission fits, the model is fit in spectral regions where there is no CO
absorption and only emission (Figure Supplementary 3). This is made possible by the
fact that emission occurs at higher excitation temperatures, and thus, the edges of
the P and R branches of the CO ro-vibrational spectrum are more extended than the
lower temperature absorption. This yields _T_ CO _,_ em = 2050 K with a column density of
_N_ CO _,_ em = 4 _._ 4 _×_ 10 [11] cm _[−]_ [2] . CO emission lines are the only ones that require _V_ = _̸_ 0
and ∆ _V_ = _̸_ 0 (see Table. Extended Data 4). The fact that _V_ = _̸_ 0 suggests an outflow
origin for this emission.
For CO absorption, the model is fit in the NIRSpec range (4.38 _−_ 5.02 µm). We
first subtract the CO emission model (see above) to ease the fitting of the absorption.
For H 2 O absorption, the model is fit in the NIRSpec range (2.45 _−_ 2.91 µm). The
best fit models for H 2 O and CO absorption obtained using the procedure relying
on residuals (see above) are shown in Figure 3. In this figure, we present the model
optical depth ( _τ_ [abs] ( _λ, T_ ex )) and the observationally derived optical depths, that is :
_τ_ [obs] = _log_ ( _F_ obs ( _λ_ ) _/F_ NIR ( _λ_ )), where _F_ obs ( _λ_ ) is the observed spectrum. This best fit
corresponds to _T_ H2O =850 _±_ 250 K and _T_ CO =1150 _±_ 350 K with column densities of
_N_ H2O = 9 _._ 1 _±_ 1 _._ 4 _×_ 10 [17] cm _[−]_ [2] and _N_ CO = 0 _._ 8 _±_ 0 _._ 1 _×_ 10 [18] cm _[−]_ [2] .
For CH 3 [+] emission, the model is fit in the MIRI range (7.0 _−_ 7.35 µm) using the
same approach as described above. The best fit is shown in Figure 2 and gives _T_ =
1000 _±_ 100 K and _N_ = 4 _._ 0 _×_ 10 [13] cm _[−]_ [2] .


**Modeling** **of** **water** **absorption** **in** **the** **MIRI** **range**


Using the column density and temperature for water derived from the fit of the NIRSpec data (see above), we compute the predicted spectrum in the MIRI range. We
consider two cases:


- case 1: the absorption occurs against the stellar and the near infrared emission from
dust in the inner disk (as described by Eq. 8);

- case 2: the absorption occurs against the whole infrared continuum emission, that
is :
_F_ mod ( _λ_ ) = ( _F_ _⋆_ ( _λ_ ) + _F_ NIR ( _λ_ ) + _F_ MIR ( _λ_ )) _× e_ _[−][τ]_ [ abs] [(] _[λ,T]_ [ex] [)] _._ (9)


The resulting models for these two cases are shown in Figure Extended Data 6 in
the MIRI range, near 6.7 µm. It can be seen in this figure that the model for the case
2 produces absorption features which are much stronger than observed, while case 1
agrees better with observations. This provides an additional confirmation that water
absorption originates from the the inner disk.

### **Data Availability**


The JWST data presented in this paper is publicly available through the MAST online
archive [(http://mast.stsci.edu)](http://mast.stsci.edu) using the PID 1288.


17

### **Code Availability**

The JWST pipeline used to produce the final data products presented in this article
[is available at https://github.com/spacetelescope/jwst. The code used in this study is](https://github.com/spacetelescope/jwst)
available from the corresponding author on reasonable request.

### **Acknowledgments**


This work is based [in part] on observations made with the NASA/ESA/CSA James
Webb Space Telescope. The data were obtained from the Mikulski Archive for Space
Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS
5-03127 for JWST. These observations are associated with programs #1288. IS, OB
are funded by the Centre National d’Etudes Spatiales (CNES) through the APR program. This research received funding from the program ANR-22-EXOR-0001 Origins
of the Institut National des Sciences de l’Univers, CNRS. We thank R. Le Gal for
her comments on the manuscript. TJH acknowledges funding from a Royal Society
Dorothy Hodgkin Fellowship and UKRI guaranteed funding for a Horizon Europe
ERC consolidator grant (EP/Y024710/1). JRG thanks the Spanish MCINN for funding support under grant PID2023-146667NB-I00. This project is co-funded by the
European Union (ERC, SUL4LIFE, grant agreement No 101096293). AF also thanks
project PID2022-137980NB-I00 funded by the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF
A way of making Europe”. TO acknowledges the support by the Japan Society for the
Promotion of Science (JSPS) KAKENHI Grant Number JP24K07087. CB is grateful for an appointment at NASA Ames Research Center through the San Jos´e State
University Research Foundation (80NSSC22M0107). We thank the referees for their
comments and suggestions, which helped to improve the clarity of the manuscript.

### **Author Contribution Statement**


I.S. and O.B. wrote the manuscript with significant input from E.B.. I.S. did the line
analysis with support from O.B.. I.S., A.C., R.C., A.S., B.T., F.A., D.V.P. reduced
the data. E.H., E.P., and O.B. planned and co-led the ERS PDRs4All program. O.B.,
E.B, F.,A., P.A., E.A.B, C.B, J.C., G.A.L.C., E.D., A.F., J.R.G., E.H., T.J.H., C.J.,
F.L.P., T.O., E.P., M.R., A.G.G.M.T. and M.Z. contributed to the observing program
with JWST. All authors participated in either the development and testing of the
MIRI-MRS or NIRSpec instruments and their data reduction, in the discussion of the
results, and/or commented on the manuscript.

### **Competing Interest Statement**


The authors declare no competing interests.

### **Tables**


18

**Table** **Extended** **Data** **1** Detected

emission lines and their intensities


Species Wavelength Intensity
(1) (2) (3)
H i 1.0052 7.3092 _×_ 10 _[−]_ [4]

H 2 1.0054 3.3239 _×_ 10 _[−]_ [4]

[S ii] 1.0289 1.6407 _×_ 10 _[−]_ [4]

[S ii] 1.0323 2.2115 _×_ 10 _[−]_ [4]

[S ii] 1.0339 1.5751 _×_ 10 _[−]_ [4]

[S ii] 1.0373 7.2280 _×_ 10 _[−]_ [5]

He i 1.0832 60.299 _×_ 10 _[−]_ [4]

H 2 1.0838 28.379 _×_ 10 _[−]_ [4]

H i 1.0941 17.987 _×_ 10 _[−]_ [4]

He i 1.2788 8.2167 _×_ 10 _[−]_ [5]

H i 1.2821 29.607 _×_ 10 _[−]_ [4]

H 2 1.2823 13.536 _×_ 10 _[−]_ [4]

O i 1.3168 6.8693 _×_ 10 _[−]_ [5]

He i 1.4486 5.1291 _×_ 10 _[−]_ [5]

H 2 1.4591 6.0641 _×_ 10 _[−]_ [5]

H i 1.5345 6.6678 _×_ 10 _[−]_ [5]

H i 1.5443 5.1240 _×_ 10 _[−]_ [5]

H i 1.5560 6.8D6 _×_ 10 _[−]_ [5]

H i 1.5704 8.2517 _×_ 10 _[−]_ [5]

H i 1.5884 8.8201 _×_ 10 _[−]_ [5]

H i 1.6113 1.6521 _×_ 10 _[−]_ [4]

H i 1.6411 1.6898 _×_ 10 _[−]_ [4]

[Fe ii] 1.6440 7.6064 _×_ 10 _[−]_ [5]

H i 1.6811 2.0592 _×_ 10 _[−]_ [4]

He i 1.7006 5.6076 _×_ 10 _[−]_ [5]

H 2 1.7364 8.3027 _×_ 10 _[−]_ [5]

H i 1.7366 1.0473 _×_ 10 _[−]_ [4]

H 2 1.7369 1.0487 _×_ 10 _[−]_ [4]

H i 1.8179 2.8084 _×_ 10 _[−]_ [4]

H 2 1.8182 7.3514 _×_ 10 _[−]_ [5]

He i 1.8690 2.6438 _×_ 10 _[−]_ [4]

He i 1.8702 1.0561 _×_ 10 _[−]_ [4]

H i 1.8756 89.846 _×_ 10 _[−]_ [4]

H i 1.9450 4.9110 _×_ 10 _[−]_ [4]

He i 2.0586 5.9400 _×_ 10 _[−]_ [4]

H 2 2.1218 7.1025 _×_ 10 _[−]_ [5]

H i 2.1661 8.1658 _×_ 10 _[−]_ [4]

H 2 2.3397 8.9336 _×_ 10 _[−]_ [5]

H 2 2.4065 1.5008 _×_ 10 _[−]_ [4]

He i 2.4127 5.8390 _×_ 10 _[−]_ [5]

H 2 2.4135 9.0322 _×_ 10 _[−]_ [5]

H i 2.4163 9.9279 _×_ 10 _[−]_ [5]

H 2 2.4208 5.7382 _×_ 10 _[−]_ [5]

H 2 2.4296 5.4590 _×_ 10 _[−]_ [5]


(1) Species name; (2) Emission line wavelength (µm), from the PDRs4All line list;
(3) Line intensity (erg s _[−]_ [1] cm _[−]_ [2] sr _[−]_ [1] ).


1

**Table** **Extended** **Data** **2** Table

Extended 1, continued.


Specie Wavelength Intensity
(1) (2) (3)
H i 2.4313 1.1551 _×_ 10 _[−]_ [4]

H 2 2.4354 5.5206 _×_ 10 _[−]_ [5]

H 2 2.4374 7.3335 _×_ 10 _[−]_ [5]

H 2 2.4428 6.4722 _×_ 10 _[−]_ [5]

H i 2.4490 5.2216 _×_ 10 _[−]_ [5]

H 2 2.4547 5.9707 _×_ 10 _[−]_ [5]

H i 2.6126 1.0249 _×_ 10 _[−]_ [4]

He i 2.6241 1.13415 _×_ 10 _[−]_ [4]

He i 2.6259 14.625 _×_ 10 _[−]_ [4]

H 2 2.6268 1.3713 _×_ 10 _[−]_ [4]

H i 2.6751 9.0793 _×_ 10 _[−]_ [5]

H i 2.7582 1.5352 _×_ 10 _[−]_ [4]

H i 2.8729 1.5189 _×_ 10 _[−]_ [4]

H i 3.0392 1.7567 _×_ 10 _[−]_ [4]

H i 3.2969 2.3034 _×_ 10 _[−]_ [4]

H 2 3.2981 7.0150 _×_ 10 _[−]_ [5]

H i 3.7405 3.7225 _×_ 10 _[−]_ [4]

He i 4.0490 9.8952 _×_ 10 _[−]_ [5]

H i 4.0522 21.880 _×_ 10 _[−]_ [4]

H 2 4.0540 3.0313 _×_ 10 _[−]_ [4]

[Fe ii] 4.0763 1.1952 _×_ 10 _[−]_ [4]

H 2 4.0806 9.0220 _×_ 10 _[−]_ [5]

[Fe ii] 4.0819 1.0560 _×_ 10 _[−]_ [4]

[Fe ii] 4.1149 5.2802 _×_ 10 _[−]_ [5]

He i 4.1227 5.4020 _×_ 10 _[−]_ [5]

H i 4.3764 7.5432 _×_ 10 _[−]_ [5]

H i 4.6537 5.4738 _×_ 10 _[−]_ [4]

H 2 4.6557 9.6589 _×_ 10 _[−]_ [5]

H i 4.6725 1.2686 _×_ 10 _[−]_ [4]

H i 5.0913 5.9017 _×_ 10 _[−]_ [5]

H i 5.1286 1.5268 _×_ 10 _[−]_ [4]

[Fe ii] 5.3401 7.7037 _×_ 10 _[−]_ [5]

H 2 5.5111 7.8753 _×_ 10 _[−]_ [5]

H i 5.9082 1.8906 _×_ 10 _[−]_ [4]

H 2 6.9095 1.8656 _×_ 10 _[−]_ [4]

[Ar ii] 6.9852 4.7226 _×_ 10 _[−]_ [4]

H i 7.4598 7.1026 _×_ 10 _[−]_ [4]

H i 7.5024 1.7393 _×_ 10 _[−]_ [4]

H i 7.5081 7.2068 _×_ 10 _[−]_ [5]

H 2 8.0250 8.7383 _×_ 10 _[−]_ [5]

H i 8.7600 5.6647 _×_ 10 _[−]_ [5]

[Ar iii] 8.9913 38.084 _×_ 10 _[−]_ [4]

H 2 9.6649 1.1071 _×_ 10 _[−]_ [4]

H i 10.503 5.5302 _×_ 10 _[−]_ [5]

[S iv] 10.510 4.2879 _×_ 10 _[−]_ [4]

[Ni ii] 10.682 6.1122 _×_ 10 _[−]_ [5]

He i 10.799 5.6502 _×_ 10 _[−]_ [5]

H i 10.803 5.7912 _×_ 10 _[−]_ [5]

H i 11.308 9.5396 _×_ 10 _[−]_ [5]

H i 12.371 1.7725 _×_ 10 _[−]_ [4]

[Ne ii] 12.813 134.94 _×_ 10 _[−]_ [4]

[Ne iii] 15.555 1.5734 _×_ 10 _[−]_ [4]

[S iii] 18.713 22.196 _×_ 10 _[−]_ [4]

[Ar iii] 21.829 6.2053 _×_ 10 _[−]_ [5]

[Fe iii] 22.925 7.1886 _×_ 10 _[−]_ [5]
2

**Table** **Extended** **Data** **3** H 2 lines detection properties


Transition Wavelength Intensity ( _×_ 10 _[−]_ [5] )
(1) (2) (3)
_v_ = 0 _→_ 0 ( _J_ = 3 _→_ 1) 17.034 4.865
_v_ = 0 _→_ 0 ( _J_ = 4 _→_ 2) 12.278 3.383
_v_ = 0 _→_ 0 ( _J_ = 5 _→_ 3) 9.6649 11.07
_v_ = 0 _→_ 0 ( _J_ = 6 _→_ 4) 8.0250 8.738
_v_ = 0 _→_ 0 ( _J_ = 7 _→_ 5) 6.9095 18.65
_v_ = 0 _→_ 0 ( _J_ = 8 _→_ 6) 6.1085 2.978
_v_ = 0 _→_ 0 ( _J_ = 9 _→_ 7) 5.5111 7.875
_v_ = 0 _→_ 0 ( _J_ = 10 _→_ 8) 5.0531 2.414
_v_ = 1 _→_ 0 ( _J_ = 2 _→_ 4) 3.0038 2.640
_v_ = 1 _→_ 0 ( _J_ = 2 _→_ 0) 2.2232 2.917
_v_ = 1 _→_ 0 ( _J_ = 3 _→_ 5) 3.2349 2.959
_v_ = 1 _→_ 0 ( _J_ = 3 _→_ 1) 2.1218 7.102
_v_ = 1 _→_ 0 ( _J_ = 4 _→_ 4) 2.4374 7.333
_v_ = 1 _→_ 0 ( _J_ = 4 _→_ 2) 2.0337 3.184
_v_ = 1 _→_ 0 ( _J_ = 5 _→_ 5) 2.4547 5.970
_v_ = 1 _→_ 0 ( _J_ = 5 _→_ 3) 1.9575 6.180
_v_ = 1 _→_ 0 ( _J_ = 7 _→_ 5) 1.8357 2.008


(1) H 2 transition label; (2) Emission line wavelength (µm), from

[92]; (3) Line intensity (erg s _[−]_ [1] cm _[−]_ [2] sr _[−]_ [1] ).


3

**Table** **Extended** **Data** **4** Derived Physical Properties of Considered Species.


ID Detection _T_ ex _N_ ∆ _V_ _V_
(1) (2) (3) (4) (5) (6)
H 2 O abs 850 _±_ 250 9.1 _±_ 1 _._ 4 _×_ 10 [17] 0 0
CO abs 1150 _±_ 350 0.8 _±_ 0 _._ 1 _×_ 10 [18] 0 0
CH 3 [+] em 1000 _±_ 100 4.0 _±_ 0 _._ 8 _×_ 10 [13] 0 0
CO em 2050 _±_ 100 4.4 _±_ 0 _._ 9 _×_ 10 [11] 80 -25


(1) Species; (2) Detected in emission (em) or in absorption (abs); (3) Excitation
temperature (in K); (4) Column density (cm _[−]_ [2] ), see details in the text on the assumptions
for the size of the emitting surface in the case of emission; (5) Line Doppler broadening (in
km s _[−]_ [1] ); (6) Doppler shift with respect to systemic velocity of d203-504 (25 km s _[−]_ [1] )


4

### **Figure Legends/Captions**

Figure 1: JWST NIRSpec/IFU and MIRI/MRS combined spectrum of the d203-504
proplyd. The vertical lines indicate the position of HI (dashed), He I (dotted) and H 2
(continuous) emission lines. Fine structure lines of atoms are labeled directly on the
figure. Three close-up views are displayed in framed insets: water absorption at 2.7 µm
in blue ( a)), CO absorption and emission at 4.7 µm in purple ( b)) and CH 3 [+] [emis-]
sion at 7.2 µm in orange ( c)). Emission bands from PAHs are highlighted in green.


Figure 2: Analysis of PAH, CH 3 [+] and H 2 emissions in d203-504. a) Continuum
subtracted PAH spectrum ( _F_ PAH ( _λ_ ), see Methods) in arbitrary units, for d203-504
(gray) and the Orion Bar PDR (green). b) Continuum subtracted spectrum of
d203-504 ( _F_ obs ( _λ_ ) _−_ _F_ cont ( _λ_ ), see Methods) in the spectral region of CH 3 [+] emission,
in dark gray and the best fit model in blue. c) Comparison between the observed
(blue) and modeled (orange) H 2 line intensities using the Meudon PDR model. Error
bars represent a total uncertainty of 50% used in the minimization to obtain the best
fit model. The instrumental uncertainties are smaller than the point size and given
in Table Extended Data 4. Notations of H 2 transitions on the x-axis are abbreviated.
The corresponding quantum levels are given in Table Extended Data 3.


Figure 3: Optical depth spectra of water and carbon monoxide absorption in the
inner disk of d203-504. a) Water absorption optical depth spectrum derived from the
observations ( _τ_ obs, see Methods), in black, and best fit model ( _τ_ abs ) shown in negative, in blue. b) Carbon monoxide absorption optical depth spectrum derived from
the observations, and best fit model in blue. The gray areas correspond to regions of
contamination by strong atomic lines where the data has been excluded from the fit.
Column densities and temperatures obtained with the best fit models are indicated.


Figure 4: Chemical structure in the solar-type d203-504 Proplyd. a) Sketch of the
inner disk ( ≲ 1 au), composed of hot dust grains and water vapor heated by accretion
processes. This heating sets the position of the snowline, that is, the radius at which
the water vapor can freeze-out on dust grains, at _r_ _∼_ 0 _._ 7 au (vertical dashed line). b)
Sketch of the outer disk ( ≳ 1 au). The surface layers host a photodissociation region
with photo-chemistry involving CH [+], CH 3 [+] [,] [OH] [and] [PAHs] [driven] [by] [the] [FUV] [pho-]
tons from nearby massive stars. This PDR triggers mass-loss by photoevaporation.


Figure 5: Fraction of the available cosmic carbon abundance locked in PAHs. Those
fractions are measured at different times of the stellar evolution (from older to more
recent, left to right). The Orion Bar and NGC 7023 are photodissociation region in
star-forming regions. HST10 is a proplyd in Orion, situated closer to the Trapezium
cluster with respect to d203-504 with _G_ 0 _∼_ 2 _×_ 10 [5] . Ryugu is a type C asteroid and
is used as an approximation for the Solar System. See Methods for details on the
derivation of PAH abundances presented in this figure.


5

### **References**


[1] Gardner, J. P. _et_ _al._ The james webb space telescope mission. _Publications_ _of_ _the_
_Astronomical_ _Society_ _of_ _the_ _Pacific_ 135, 068001 (2023).


[2] Kamp, I. _et_ _al._ The chemical inventory of the inner regions of planet-forming
disks–the jwst/minds program. _Faraday_ _discussions_ 245, 112–137 (2023).


[3] van Dishoeck, E. F. _et_ _al._ The diverse chemistry of protoplanetary disks as
revealed by JWST. _Faraday_ _Discussions_ 245, 52–79 (2023).


[4] Henning, T. _et_ _al._ Minds: The jwst miri mid-infrared disk survey. _Publications_
_of_ _the_ _Astronomical_ _Society_ _of_ _the_ _Pacific_ 136, 054302 (2024).


[5] Grant, S. L. _et al._ Minds. the detection of 13co2 with jwst-miri indicates abundant
co2 in a protoplanetary disk. _The_ _Astrophysical_ _Journal_ _Letters_ 947, L6 (2023).


[6] Tabone, B. _et_ _al._ A rich hydrocarbon chemistry and high C to O ratio in the
inner disk around a very low-mass star. _Nature_ _Astronomy_ 7, 805–814 (2023).


[7] K´osp´al, A. [´] _et_ _al._ Jwst/miri spectroscopy of the disk of the young eruptive star
ex lup in quiescence. _The_ _Astrophysical_ _Journal_ _Letters_ 945, L7 (2023).


[8] Perotti, G. _et_ _al._ Water in the terrestrial planet-forming zone of the PDS 70 disk.
_Nature_ 620, 516–520 (2023).


[9] Pontoppidan, K. M. _et_ _al._ High-contrast jwst-miri spectroscopy of planet-forming
disks for the jdisc survey. _The_ _Astrophysical_ _Journal_ 963, 158 (2024).


[10] Colmenares, M. J. _et_ _al._ Jwst/miri detection of a carbon-rich chemistry in a solar
nebula analog. _The_ _Astrophysical_ _Journal_ (977, 1732024).


[11] Madhusudhan, N. C/o ratio as a dimension for characterizing exoplanetary
atmospheres. _The_ _Astrophysical_ _Journal_ 758, 36 (2012).


[12] Mah, J., Bitsch, B., Pascucci, I. & Henning, T. Close-in ice lines and the superstellar c/o ratio in discs around very low-mass stars. _Astronomy_ _&_ _Astrophysics_
677, L7 (2023).


[13] Lada, C. J. & Lada, E. A. Embedded clusters in molecular clouds. _Annual Review_
_of_ _Astronomy_ _&_ _Astrophysics_ 41, 57–115 (2003).


[14] Winter, A. J. & Haworth, T. J. The external photoevaporation of planet-forming
discs. _European_ _Physical_ _Journal_ _Plus_ 137, 1132 (2022).


[15] Adams, F. C. The birth environment of the solar system. _Annual_ _Review_ _of_
_Astronomy_ _&_ _Astrophysics_ 48, 47–85 (2010).


6

[16] Bergin, E. A., Alexander, C., Drozdovskaya, M., Gounelle, M. & Pfalzner, S.
Interstellar heritage and the birth environment of the solar system. _“Comets III”,_
_University_ _of_ _Arizona_ _Press,_ _3_ (2024).


[17] Desch, S. & Miret-Roig, N. The sun’s birth environment: Context for meteoritics.
_Space_ _Science_ _Reviews_ 220, 76 (2024).


[18] Terada, H. _et_ _al._ Adaptive Optics Observations of 3 _µ_ m Water Ice in Silhouette
Disks in the Orion Nebula Cluster and M43. _The_ _Astronomical_ _Journal_ 144, 175
(2012).


[19] Boyden, R. D. & Eisner, J. A. Chemical Modeling of Orion Nebula Cluster Disks:
Evidence for Massive, Compact Gas Disks with Interstellar Gas-to-dust Ratios.
_The_ _Astrophysical_ _Journal_ 947, 7 (2023).


[20] D´ıaz-Berr´ıos, J. K. _et_ _al._ Chemistry in externally fuv-irradiated disks in the
outskirts of the orion nebula cluster. _The_ _Astrophysical_ _Journal_ 969, 165 (2024).


[21] Ballering, N. P. _et_ _al._ Water Ice in the Edge-on Orion Silhouette Disk 114–426
from JWST NIRCam Images. _The_ _Astrophysical_ _Journal_ 979, 110 (2025).


[22] Walsh, C., Millar, T. & Nomura, H. Molecular line emission from a protoplanetary
disk irradiated externally by a nearby massive star. _The_ _Astrophysical_ _Journal_
_Letters_ 766, L23 (2013).


[23] Champion, J. _et_ _al._ Herschel survey and modelling of externally-illuminated
photoevaporating protoplanetary disks. _Astronomy_ _&_ _Astrophysics_ 604, A69
(2017).


[24] Gross, R. E. & Cleeves, L. I. Modeling the Impact of Moderate External UV
Irradiation on Disk Chemistry. _The_ _Astrophysical_ _Journal_ 980, 189 (2025).


[25] Keyte, L. & Haworth, T. J. Impact of photoevaporative winds in chemical models of externally irradiated protoplanetary discs. _Monthly_ _Notices_ _of_ _the_ _Royal_
_Astronomical_ _Society_ 537, 598–616 (2025).


[26] Habing, H. J. The interstellar radiation density between 912 A and 2400 A. _Bull._
_Astr._ _Inst._ _Netherlands_ 19, 421 (1968).


[27] Habart, E. _et_ _al._ Pdrs4all-ii. jwst’s nir and mir imaging view of the orion nebula.
_Astronomy_ _&_ _Astrophysics_ 685, A73 (2024).


[28] Bern´e, O. _et_ _al._ A far-ultraviolet–driven photoevaporation flow observed in a
protoplanetary disk. _Science_ 383, 988–992 (2024).


[29] Peeters, E. _et_ _al._ Pdrs4all-iii. jwst’s nir spectroscopic view of the orion bar.
_Astronomy_ _&_ _Astrophysics_ 685, A74 (2024).


7

[30] Bern´e, O. _et_ _al._ Formation of the methyl cation by photochemistry in a
protoplanetary disk. _Nature_ 621, 56–59 (2023).


[31] Zannese, M. _et al._ OH as a probe of the warm-water cycle in planet-forming disks.
_Nature_ _Astronomy_ 8, 577–586 (2024).


[32] Geers, V. C. _et_ _al._ Spatially extended polycyclic aromatic hydrocarbons in circumstellar disks around T Tauri and Herbig Ae stars. _Astronomy_ _&_ _Astrophysics_
476, 279–289 (2007).


[33] Ram´ırez-Tannus, M. C. _et_ _al._ XUE: Molecular Inventory in the Inner Region of
an Extremely Irradiated Protoplanetary Disk. _The_ _Astrophysical_ _Journal_ _Letters_
958, L30 (2023).


[34] Ndugu, N., Bitsch, B. & Lena, L. J. How external photoevaporation changes the
inner disc’s chemical composition. _Astronomy_ _&_ _Astrophysics_ 691, A32(2024).


[35] O’dell, C. R. & Wen, Z. Postrefurbishment Mission Hubble Space Telescope
Images of the Core of the Orion Nebula: Proplyds, Herbig-Haro Objects, and
Measurements of a Circumstellar Disk. _The_ _Astrophysical_ _Journal_ 436, 194
(1994).


[36] Bally, J., O’Dell, C. & McCaughrean, M. J. Disks, microjets, windblown bubbles,
and outflows in the orion nebula. _The_ _Astronomical_ _Journal_ 119, 2919 (2000).


[37] O’Dell, C. R., Kollatschny, W. & Ferland, G. J. Which Stars Are Ionizing the
Orion Nebula? _The_ _Astrophysical_ _Journal_ 837, 151 (2017).


[38] Haworth, T. J. _et_ _al._ The vlt muse nfm view of outflows and externally photoevaporating discs near the orion bar. _Monthly_ _Notices_ _of_ _the_ _Royal_ _Astronomical_
_Society_ 525, 4129–4142 (2023).


[39] Fang, M., Kim, J. S., Pascucci, I. & Apai, D. An Improved Hertzsprung-Russell
Diagram for the Orion Trapezium Cluster. _The_ _Astrophysical_ _Journal_ 908, 49
(2021).


[40] Aru, M.-L. _et al._ Kaleidoscope of irradiated disks: MUSE observations of proplyds
in the Orion Nebula Cluster. I. Sample presentation and ionization front sizes.
_Astronomy_ _&_ _Astrophysics_ 687, A93 (2024).


[41] Apell´aniz, J. M. _et_ _al._ The villafranca catalog of galactic ob groups-ii. from gaia
dr2 to edr3 and ten new systems with o stars. _Astronomy_ _&_ _Astrophysics_ 657,
A131 (2022).


[42] Bern´e, O. _et_ _al._ PDRs4All: A JWST early release science program on radiative
feedback from massive stars. _Publications_ _of_ _the_ _Astronomical_ _Society_ _of_ _the_
_Pacific_ 134, 054301 (2022).


8

[43] Rieke, M. J. _et_ _al._ Performance of nircam on jwst in flight. _Publications_ _of_ _the_
_Astronomical_ _Society_ _of_ _the_ _Pacific_ 135, 028001 (2023).


[44] Wells, M. _et_ _al._ The Mid-Infrared Instrument for the James Webb Space
Telescope, VI: The Medium Resolution Spectrometer. _Publications_ _of_ _the_
_Astronomical_ _Society_ _of_ _the_ _Pacific_ 127, 646 (2015).


[45] B¨oker, T. _et_ _al._ The Near-Infrared Spectrograph (NIRSpec) on the James Webb
Space Telescope. III. Integral-field spectroscopy. _Astronomy_ _&_ _Astrophysics_ 661,
A82 (2022).


[46] Van De Putte, D. _et_ _al._ Pdrs4all viii: Mid-ir emission line inventory of the orion
bar. _Astronomy_ _&_ _Astrophysics_ 687, A86 (2024).


[47] Chown, R. _et al._ Pdrs4all-iv. an embarrassment of riches: Aromatic infrared bands
in the orion bar. _Astronomy_ _&_ _Astrophysics_ 685, A75 (2024).


[48] Rigliaco, E., Pascucci, I., Gorti, U., Edwards, S. & Hollenbach, D. Understanding
the origin of the [o i] low-velocity component from t tauri stars. _The Astrophysical_
_Journal_ 772, 60 (2013).


[49] Changala, P. B. _et_ _al._ Astronomical ch3+ rovibrational assignments-a combined theoretical and experimental study validating observational findings in the
d203-506 uv-irradiated protoplanetary disk. _Astronomy_ _&_ _Astrophysics_ 680, A19
(2023).


[50] Zannese, M. _et_ _al._ PDRs4All XI. Detection of infrared CH [+] and CH 3 [+] rovibrational emission in the Orion Bar and disk d203-506: evidence of chemical pumping.
_Astronomy_ _&_ _Astrophysics_ 696, A99 (2025).


[51] Le Petit, F., Nehm´e, C., Le Bourlot, J. & Roueff, E. A Model for Atomic and
Molecular Interstellar Gas: The Meudon PDR Code. _Astrophys. J. S._ 164, 506–529
(2006).


[52] Salyk, C. _et_ _al._ H 2 O and OH Gas in the Terrestrial Planet-forming Zones of
Protoplanetary Disks. _The_ _Astrophysical_ _Journal_ _Letters_ 676, L49 (2008).


[53] Banzatti, A. _et_ _al._ Scanning Disk Rings and Winds in CO at 0.01-10 au: A Highresolution M-band Spectroscopy Survey with IRTF-iSHELL. _The_ _Astronomical_
_Journal_ 163, 174 (2022).


[54] Facchini, S., Birnstiel, T., Bruderer, S. & van Dishoeck, E. F. Different dust and
gas radial extents in protoplanetary disks: consistent models of grain growth and
co emission. _Astronomy_ _&_ _Astrophysics_ 605, A16 (2017).


[55] Bergemann, M. _et_ _al._ Solar oxygen abundance. _Monthly_ _Notices_ _of_ _the_ _Royal_
_Astronomical_ _Society_ 508, 2236–2253 (2021).


9

[56] Cartledge, S. I., Meyer, D. M., Lauroesch, J. & Sofia, U. Space telescope imaging spectrograph observations of interstellar oxygen and krypton in translucent
clouds. _The_ _Astrophysical_ _Journal_ 562, 394 (2001).


[57] Bethell, T. & Bergin, E. Formation and survival of water vapor in the terrestrial
planet–forming region. _Science_ 326, 1675–1677 (2009).


[58] Duval, S. E., Bosman, A. D. & Bergin, E. A. Water shielding in the terrestrial planet-forming zone: Implication for inner disk organics. _The_ _Astrophysical_
_Journal_ _Letters_ 934, L25 (2022).


[59] Banzatti, A. _et_ _al._ The Kinematics and Excitation of Infrared Water Vapor
Emission from Planet-forming Disks: Results from Spectrally Resolved Surveys
and Guidelines for JWST Spectra. _The_ _Astronomical_ _Journal_ 165, 72 (2023).


[60] Hillenbrand, L. A. On the Stellar Population and Star-Forming History of the
Orion Nebula Cluster. _The_ _Astronomical_ _Journal_ 113, 1733–1768 (1997).


[61] Fajrin, M., Armstrong, J. J., Tan, J. C., Farias, J. P. & Eyer, L. Low-mass
runaways from the orion nebula cluster–kinematic age constraints on star cluster
formation. _Monthly_ _Notices_ _of_ _the_ _Royal_ _Astronomical_ _Society_ 537, 1320–1333
(2025).


[62] Goicoechea, J. R. _et_ _al._ PDRs4All: X. ALMA and JWST detection of neutral
carbon in the externally irradiated disk d203-506: Undepleted gas-phase carbon.
_Astronomy_ _&_ _Astrophysics_ 689, L4 (2024).


[63] Bern´e, O. _et_ _al._ Analysis of the emission of very small dust particles from
Spitzer spectro-imagery data using blind signal separation methods. _Astronomy_
_&_ _Astrophysics_ 469, 575–586 (2007).


[64] Bouwman, J., Mattioda, A., Linnartz, H. & Allamandola, L. Photochemistry of
polycyclic aromatic hydrocarbons in cosmic water ice-i. mid-ir spectroscopy and
photoproducts. _Astronomy_ _&_ _Astrophysics_ 525, A93 (2011).


[65] Cox, N. L. J., Pilleri, P., Bern´e, O., Cernicharo, J. & Joblin, C. Polycyclic aromatic
hydrocarbons and molecular hydrogen in oxygen-rich planetary nebulae: the case
of NGC 6720. _Monthly_ _Notices_ _of_ _the_ _Royal_ _Astronomical_ _Society_ 456, L89–L93
(2016).


[66] Marciniak, A., Joblin, C., Mulas, G., Mundlapati, V. R. & Bonnamy, A. Photodissociation of aliphatic pah derivatives under relevant astrophysical conditions.
_Astronomy_ _&_ _Astrophysics_ 652, A42 (2021).


[67] Montillaud, J., Joblin, C. & Toublanc, D. Evolution of polycyclic aromatic
hydrocarbons in photodissociation regions: Hydrogenation and charge states.
_Astronomy_ _&_ _Astrophysics_ 552, A15 (2013).


10

[68] Andrews, H., Candian, A. & Tielens, A. G. G. M. Hydrogenation and dehydrogenation of interstellar PAHs: Spectral characteristics and H 2 formation.
_Astronomy_ _&_ _Astrophysics_ 595, A23 (2016).


[69] Lee, J.-E., Bergin, E. A. & Nomura, H. The solar nebula on fire: A solution to
the carbon deficit in the inner solar system. _The_ _Astrophysical_ _Journal_ _Letters_
710, L21 (2010).


[70] Semenov, D. _et_ _al._ Chemistry in disks-IV. Benchmarking gas-grain chemical
models with surface reactions. _Astronomy_ _&_ _Astrophysics_ 522, A42 (2010).


[71] Lange, K., Dominik, C. & Tielens, A. G. G. M. Turbulent processing of PAHs in
protoplanetary discs. Coagulation and freeze-out leading to depletion of gas-phase
PAHs. _Astronomy_ _&_ _Astrophysics_ 674, A200 (2023).


[72] Kress, M. E., Tielens, A. G. & Frenklach, M. The ‘soot line’: Destruction of
presolar polycyclic aromatic hydrocarbons in the terrestrial planet-forming region
of disks. _Advances_ _in_ _Space_ _Research_ 46, 44–49 (2010).


[73] Li, J., Bergin, E. A., Blake, G. A., Ciesla, F. J. & Hirschmann, M. M. Earth’s
carbon deficit caused by early loss through irreversible sublimation. _Science_
_Advances_ 7, eabd3632 (2021).


[74] Facchini, S., Clarke, C. J. & Bisbas, T. G. External photoevaporation of protoplanetary discs in sparse stellar groups: the impact of dust growth. _Monthly_
_Notices_ _of_ _the_ _Royal_ _Astronomical_ _Society_ 457, 3593–3610 (2016).


[75] Aru, M.-L. _et_ _al._ A tell-tale tracer for externally irradiated protoplanetary disks:
comparing the [ci] 8727 a line and alma observations in proplyds. _Astronomy_ _&_
_Astrophysics_ 692, A137 (2024).


[76] Bern´e, O. _et_ _al._ A far-ultraviolet–driven photoevaporation flow observed in a
protoplanetary disk. _Science_ 383, 988–992 (2024).


[77] Mann, R. K. _et_ _al._ Alma observations of the orion proplyds. _The_ _Astrophysical_
_Journal_ 784, 82 (2014).


[78] Forbrich, J. _et_ _al._ The population of compact radio sources in the orion nebula
cluster. _The_ _Astrophysical_ _Journal_ 822, 93 (2016).


[79] Foschino, S., Bern´e, O. & Joblin, C. Learning mid-IR emission spectra of
polycyclic aromatic hydrocarbon populations from observations. _Astronomy_ _&_
_Astrophysics_ 632, A84 (2019).


[80] Draine, B. T. _Physics_ _of_ _the_ _Interstellar_ _and_ _Intergalactic_ _Medium_ (2011).


[81] Vicente, S. _et_ _al._ Polycyclic aromatic hydrocarbon emission in the proplyd hst10:
What is the mechanism behind photoevaporation? _The_ _Astrophysical_ _Journal_


11

_Letters_ 765, L38 (2013).


[82] Tielens, A. G. G. M. _The_ _Physics_ _and_ _Chemistry_ _of_ _the_ _Interstellar_ _Medium_
(2005).


[83] Bern´e, O. & Tielens, A. G. G. M. Formation of buckminsterfullerene (C60) in
interstellar space. _Proceedings_ _of_ _the_ _National_ _Academy_ _of_ _Sciences_ 109, 401–406
(2012).


[84] Aponte, J. C. _et_ _al._ Pahs, hydrocarbons, and dimethylsulfides in asteroid ryugu
samples a0106 and c0107 and the orgueil (ci1) meteorite. _Earth,_ _Planets_ _and_
_Space_ 75, 28 (2023).


[85] Sabbah, H., Quitt´e, G., Demyk, K. & Joblin, C. First direct detection of
large polycyclic aromatic hydrocarbons on asteroid (162173) ryugu samples: An
interstellar heritage. _Natural_ _Sciences_ e20240010 (2024).


[86] Yokoyama, T. _et_ _al._ Samples returned from the asteroid ryugu are similar to
ivuna-type carbonaceous meteorites. _Science_ 379, eabn7850 (2022).


[87] Le Petit, F., Nehme, C., Le Bourlot, J. & Roueff, E. A Model for Atomic and
Molecular Interstellar Gas: The Meudon PDR Code. _The_ _Astrophysical_ _Journals_
164, 506–529 (2006).


[88] Joblin, C. _et_ _al._ Structure of photodissociation fronts in star-forming regions
revealed by Herschel observations of high-J CO emission lines. _Astronomy_ _&_
_Astrophysics_ 615, A129 (2018).


[89] Fitzpatrick, E. L. & Massa, D. An Analysis of the Shapes of Ultraviolet Extinction
Curves. I. The 2175 Angstrom Bump. _The Astrophysical Journal_ 307, 286 (1986).


[90] Tennyson, J. _et_ _al._ The ExoMol database: Molecular line lists for exoplanet and
other hot atmospheres. _Journal_ _of_ _Molecular_ _Spectroscopy_ 327, 73–94 (2016).


[91] Western, C. M. PGOPHER: A program for simulating rotational, vibrational
and electronic spectra. _J._ _Quant._ _Spectrosc._ _Radiat._ _Transf._ 186, 221–242 (2017).


[92] Roueff, E. _et_ _al._ The full infrared spectrum of molecular hydrogen. _Astronomy_
_&_ _Astrophysics_ 630, A58 (2019).


12

### **Extended data**

MUSE NFM



0.5


0


-0.5


-1


-1.5



-1 -0.5 0 0.5 1
x (arcsec)







0.5


0


-0.5


-1


-1.5



NIRCam F210M


-1 -0.5 0 0.5 1
x (arcsec)



**Fig.** **Extended** **Data** **1** MUSE and NIRCam images of d203-504 environment. _Left:_ MUSE NFM
composite image of both d203-506 (bottom left) and d203-504 (top). Red: the [C i]( _λ_ 8727 _A_ [˚] ) map
showing disk contributions from both d203-506 and d203-504 objects. Green: the [Fe ii] ( _λ_ 8617 _A_ [˚] )
map corresponding to jets from both objects. Blue: the H _α_ emission map showing the ionization
fronts (only d203-504 appears to have one). The glow on the top right corresponds to the Orion Bar
ionization front. _Right:_ JWST NIRCam image of the same system from the F210M filter.


13

0.5


0


-0.5


-1


-1.5


-2





0.0030


0.0025


0.0020


0.0015


0.0010


0.0005



0.0000


-1.5 -1 -0.5 0 0.5
x (arcsec)


**Fig.** **Extended** **Data** **2** ALMA 344 GHz emission map of d203-506 and d203-504. Values are given
in Jy _/_ beam and the coordinates are givens as offsets in arcseconds with respect to the position of
d203-504 (RA=5:35:20.268; DEC=-05:25:03.992).


14

1e 14



1.75


1.50


1.25


1.00


0.75


0.50


0.25





0.00
6 8 10 12 14

1e 14



1.4


1.2


1.0


0.8


0.6


0.4


0.2


0.0





6 8 10 12 14
Wavelength ( m)


**Fig.** **Extended** **Data** **3** ON and OFF extracted spectra and PAH emission. Top panel: Observed
spectrum of d203-504 (the “ON” position) in black and the “OFF” position in blue. Fitted continuums
are shown in dotted black lines. Bottom panel: continuum subtracted spectrum of d203-504, “ON”
and “OFF” positions in black and blue, respectively, and the disk PAH emission in green.


15

10 [4]


10 [3]


10 [2]














|Col1|Col2|
|---|---|
|[S III]<br>[Ar II]<br>[Ar III]<br>[Ne II]<br>[Ne III]<br>[Fe<br>H2O<br>CO<br>CH +<br>3<br>Silicate<br>Silicate<br>PAHs|[S III]<br>[Ar II]<br>[Ar III]<br>[Ne II]<br>[Ne III]<br>[Fe<br>H2O<br>CO<br>CH +<br>3<br>Silicate<br>Silicate<br>PAHs|



10 [0] 10 [1]

Wavelength ( m)


**Fig.** **Extended** **Data** **4** JWST NIRSpec/IFU and MIRI/MRS combined spectrum of the d203-504
proplyd. The vertical lines indicate the position of HI (dashed), He I (dotted) and H 2 (continuous)
emission lines. Fine structure lines of atoms are labeled directly on the figure. This spectrum is in
units of MJy/sr to emphasize the silicate emissions highlighted in green.








4.30 4.32 4.34
Wavelength ( m)



3.04 3.06


1e 15


4.12 4.14
Wavelength ( m)



7.7


7.6


7.5


7.4


6.8


6.6


6.4


6.2



1e 15


1e 15





2.97 2.98



7.8


7.6


7.4


7.2



1e 15


7.6


7.4


3.12 3.14


6.4 [1e] 15


6.2


6.0


5.8


4.24 4.26
Wavelength ( m)



7.8


7.6


7.4


6.6


6.4


6.2


6.0







7.0


6.8


6.6


6.4



4.00 4.02
Wavelength ( m)



**Fig.** **Extended** **Data** **5** OH and CH [+] emission. Zooms on d203-504 NIRSpec spectrum, represented
in black on both panels. On the upper panels, positions of OH emission lines are shown in blue and
on the lower panels, positions of CH [+] emission lines are shown in red.


16

1e 15



4.0


3.8


3.6


3.4


3.2


3.0


2.8





6.50 6.55 6.60 6.65 6.70 6.75 6.80 6.85
Wavelength ( m)


**Fig.** **Extended** **Data** **6** MIRI water absorption models. Spectroscopic models ( _F_ mod ( _λ_ )) of d203504 using Eq. 8 (blue) and Eq. 9 (red). Observed spectrum ( _F_ obs ( _λ_ )) is in black.


17

1.2


1.0


0.8


0.6


0.4


0.2


0.0

|1e 14|Col2|Col3|
|---|---|---|
||||
|2|4<br>6<br>8<br>10<br>12<br>Wavelength ( m)|4<br>6<br>8<br>10<br>12<br>Wavelength ( m)|



**Fig.** **Supplementary** **1** Modelled continuum for d203-504 observed spectrum. Observed spectrum
of d203-504 ( _F_ obs ( _λ_ ), gray). Modelled continuum and PAH emission ( _F_ cont ( _λ_ ), red), which is the sum
of the stellar _F_ _⋆_ ( _λ_ ) (orange), _F_ NIR ( _λ_ ) (blue) and _F_ MIR ( _λ_ ) (green).


18

|Col1|H2O|
|---|---|
||TH2O = 850 ± 250 K|
||TH2O = 850 ± 250 K|



500 1000 1500 2000 2500 3000
Temperature (K)


1.4


1.2


1.0

|TC|Col2|Col3|×1017cm 2|
|---|---|---|---|
|TC|TC|O = 8.1 ± 1.0|×1017 cm<br>2|
|TC|TC|||



0.6 0.8 1.0 1.2
Column density (cm 2 ) 1e18



CO



0.725


0.700


0.675


0.650


0.625


0.600


0.725


0.700


0.675


0.650


0.625


0.600



500 1000 1500 2000 2500 3000
Temperature (K)



1.6


1.4


1.2


1.0







1.0 1.5 2.0 2.5
Column density (cm 2 ) 1e18



**Fig.** **Supplementary** **2** Residuals (root mean square error) of the fits of H 2 O and CO models to
the observed spectra. The top row represents the temperature residuals for H 2 O (left) and CO (right).
The bottom row shows the residuals for column densities of H 2 O (left) and CO (right). Best models
are indicated with the red point. vertical lines indicate the 10% uncertainties of each best model.


19

4


3


2


1


0


1


2


3


5.00 5.02 5.04 5.06 5.08 5.10 5.12 5.14
Wavelength ( m)


**Fig.** **Supplementary** **3** Continuum subtracted spectrum of d203-504 in the spectral region of CO
emission. Data are in black and the inverted model in blue.


20


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Spectroscopic cross sections and constants for H2O, CO, and CH3+",
  "failed_quote": "For H 2 O and CO we use the cross sections from the ExoMol database [90]. For CH 3 + we rely on the spectroscopic constants provided by [49]."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Extract ON spectrum in 0.40 arcsec radius circular aperture on d203-504, subtract OFF background spectrum from 0.365 arcsec aperture, and fit Gaussian + linear continuum to atomic and H2 emission lines",
  "failed_quote": "To extract the d203-504 spectrum, we first take a circular aperture of 0.40 _′′_ radius centered on d203-504 coordinates (right ascension (RA)=5:35:20.268 and declination (DEC)=-05:25:03.992), which we call “ON”."
 }
]
```
