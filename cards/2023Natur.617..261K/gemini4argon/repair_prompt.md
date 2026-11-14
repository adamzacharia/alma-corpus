# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023Natur.617..261K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Springer Nature 2021 L [A] TEX template

## Compact [C ii] emitters around a C iv absorption complex at redshift 5.7


Daichi Kashino [1,2*], Simon J. Lilly [3], Robert A.
Simcoe [4], Rongmon Bordoloi [5], Ruari Mackenzie [3], Jorryt
Matthee [3] and Anna-Christina Eilers [4]


1* Institute for Advanced Research, Nagoya University, Nagoya,
464-8601, Aichi, Japan.
2 Department of Physics, Nagoya University, Nagoya, 464-8602,
Aichi, Japan.
3 Department of Physics, ETH Z¨urich, Wolfgang-Pauli-Strasse 27,
Z¨urich, 8093, Switzerland.
4 MIT Kavli Institute for Astrophysics and Space Research, 77
Massachusetts Avenue, Cambridge, 02139, Massachusetts, USA.
5 Department of Physics, North Carolina State University,
Raleigh, 27695, North Carolina, USA.


*Corresponding author(s). E-mail(s):
kashino.daichi.v7@f.mail.nagoya-u.ac.jp;
Contributing authors: simon.lilly@phys.ethz.ch;
simcoe@space.mit.edu; rbordol@ncsu.edu; mruari@ethz.ch;

mattheej@phys.ethz.ch; eilers@mit.edu;


**Abstract**


The physical conditions of the circumgalactic medium are probed by
intervening absorption-line systems in the spectrum of background quasistellar objects out to the epoch of cosmic reionization [1–4]. A correlation
between the ionization state of the absorbing gas and the nature of
the nearby galaxies has been suggested by the sources detected either
in Ly _**α**_ or [C ii] 158 _**µ**_ m near to respectively highly-ionized and neutral absorbers [5, 6]. This is also likely linked to the global changes
in the incidence of absorption systems of different types and the process of cosmic reionization [7–12]. Here we report the detection of two

[C ii]-emitting galaxies at redshift _**z**_ _**≈**_ **5** _**.**_ **7** that are associated with a


1

Springer Nature 2021 L [A] TEX template


2 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


complex high-ionization C iv absorption system. These objects are part
of an overdensity of galaxies and have compact sizes ( _**<**_ **2** _**.**_ **4** kpc) and
narrow line widths ( **FWHM** _**≈**_ **62** – **64** **km** **s** _**[−]**_ **[1]** ). Hydrodynamic simulations predict that similar narrow [C ii] emission may arise from the
heating of small ( ≲ **3** **kpc** ) clumps of cold neutral medium or a compact photodissociation region [13, 14]. The lack of counterparts in the
rest-frame ultraviolet indicates severe obscuration of the sources that
are exciting the [C ii] emission. These results may suggest a connection
between the properties of the [C ii] emission, the rare overdensity of
galaxies and the unusual high ionization state of the gas in this region.


**Keywords:** Metal absorption systems, absorber host galaxies, intergalactic
medium

### **Main**


Two line emitters are detected within a mosaiced submilimeter observation
with Atacama Large Millimeter Array (ALMA) that covers a field of about
23 _[′′]_ (138 physical kpc at _z_ = 5 _._ 7) in radius centered on the position of QSO
J1030+0524 at redshift _z_ QSO = 6 _._ 308. We interpret these two emission lines to
be [C ii] 158 _µ_ m at redshifts close to a complex C iv absorption system that is
found with three distinct absorbers at _z_ abs = 5 _._ 7246, 5.7411, and 5.7443 in a
deep high-resolution spectrum of the QSO. These two sources were discovered
in blind line searches within a larger datacube that covers a circular survey
area of 23 _[′′]_ (138 physical kpc (pkpc) at _z_ = 5 _._ 7) and a total velocity interval
7380 km s _[−]_ [1], corresponding to _≈_ 76 comoving Mpc (cMpc). No other significant lines were detected. We estimated the reliability of these detections both
to be _>_ 95%. The probability for these two line sources to be unrelated CO
interlopers at low redshifts was calculated to be 1.5%, and this possibility is
further disfavored by other ancillary data in this region (see Methods).
The first source, referred to as [C ii]1030A, at _z_ [C ii] = 5 _._ 7354, has an impact
parameter to the quasar sightline [1] of 86 pkpc. The second source, [C ii]1030B,
at _z_ [C ii] = 5 _._ 7101 is at 109 pkpc (Fig 1a). These sources have the maximum
peak signal-to-noise ratios (S/N) of _>_ 6 _._ 0 when collapsing the emission line
channels over 66 km s _[−]_ [1] (Methods). The [C ii] moment-0 intensity maps of
these [C ii] sources are shown in Fig. 1b and c. Interestingly, these two sources
are not spatially resolved under the synthesized FWHM beam size of 0 _._ 35 _[′′]_,
putting a strong constraint on the FWHM size of the [C ii] sources to be
less than 2.4 pkpc. The spectra of these sources are shown in Figure 2a,b,
in comparison with the C iv absorption profiles in the continuum-normalized
spectrum of the QSO J1030+0524 (Fig. 2c; Methods). These ALMA spectra
are extracted within radius 0 _._ 24 _[′′]_ of the peak position. By fitting a simple
Gaussian profile, we estimate the FWHM line widths to be 64 _±_ 11 km s _[−]_ [1]


1 The transverse separation from the QSO line of sight at the redshift of the intervening system.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 3


([C ii]1030A) and 62 _±_ 11 km s _[−]_ [1] (B), and the velocity-integrated [C ii] flux
densities to be 0 _._ 174 _±_ 0 _._ 027 Jy km s _[−]_ [1] (A) and 0 _._ 276 _±_ 0 _._ 044 Jy km s _[−]_ [1] (B)
after correcting for the primary beam response (Methods). The two dotted
lines represent the four spectral channels, equivalent to a velocity width of
66 km s _[−]_ [1], used to create the moment-0 maps. The total [C ii] luminosity is
_L_ [C ii] = (1 _._ 61 _±_ 0 _._ 24) _×_ 10 [8] _L_ _⊙_ and (2 _._ 21 _±_ 0 _._ 36) _×_ 10 [8] _L_ _⊙_, respectively, for

[C ii]1030A and B. Figure 2d summarizes the kinematic structure of the [C ii]
sources relative to the absorption systems. The [C ii]1030A ( _z_ [C ii] = 5 _._ 7354)
has a velocity difference of ∆ _V_ = +485 km s _[−]_ [1] relative to the stronger
absorption system at _z_ abs = 5 _._ 7246. The [C ii]1030B ( _z_ [C ii] = 5 _._ 7101) is
at ∆ _V_ = _−_ 645 km s _[−]_ [1] . Note that [C ii]1030A has a velocity difference of
∆ _V_ = _−_ 250 km s _[−]_ [1] relative to its closest (and weakest) absorption system at
_z_ abs = 5 _._ 7411. The ALMA measurements (primary beam corrected values) of
the [C ii] sources are summarized in Table 1.
The impact parameters of these [C ii] sources are within the range seen
previously for associations between metal absorbers and (non [C ii]) galaxies at
lower redshifts [1, 15]. The velocity offsets are also comparable to the velocity
dispersion of proto-clusters identified at similar high redshifts [16] and for
companion [C ii] sources ( ≲ 100 pkpc) observed around _z_ _>_ 6 luminous quasars

[17]. A similar extent is also found in zoom-in simulations that follow the
formation of a massive proto-cluster at _z_ _∼_ 6 [18]. All these arguments support
a physical connection between the [C ii] sources and the C iv absorbing gas
through a common membership of some larger structure(s) that may enclose
all these systems, rather than the C iv absorption coming from gas falling into
or flowing out of these individual sources.
This statement is further strengthened by the locations of the four Lyman_α_ emitters (LAEs) that have been discovered in this region. Figures 1a and 2d
mark these LAEs (purple circles) detected within _±_ 1500 km s _[−]_ [1] of the C iv
absorbers with the Multi-Unit Spectroscopic Explore (MUSE) on the Very
Large Telescope (VLT) [5]. The two [C ii] sources and the four LAEs are all
quite distinct sources. Although one of the LAE (#4; _z_ = 5 _._ 758) has a small
separation of only 1 _._ 7 _[′′]_ from [C ii]1030A (equivalent to 10 pkpc), the redshift
difference between these two sources corresponds to more than 1000 km s _[−]_ [1]

suggesting that they are different objects. The typical impact parameter of the
galaxies found here, _∼_ 100 pkpc, is comparable to the possible most massive
halos of mass 10 [13] _M_ _⊙_ at this epoch. However, the radial velocity dispersion
of all six sources, _σ_ ( _v_ r ) = 830 _±_ 270 km s _[−]_ [1], is larger than expected for such
halos ( _∼_ 200 km s _[−]_ [1] ). Therefore, the system is unlikely to be virialized. The
discovery of the [C ii] sources has further strengthened this hypothesis.
These two sources are both characterized by compact sizes (FWHM diameter _<_ 2 _._ 4 pkpc) and narrow [C ii] emission line profiles (64 _±_ 11 km s _[−]_ [1] and
62 _±_ 11 km s _[−]_ [1] respectively for [C ii]1030A and B). These properties differ
from other high-redshift [C ii] emitters reported before, which tend to have a
major axis FWHM of _>_ 4 pkpc and a [C ii] line width FWHM of _>_ 200 km s _[−]_ [1]

[19–22]. Hydrodynamic simulations have suggested that the [C ii] emission can

Springer Nature 2021 L [A] TEX template


4 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


be dominated by a narrow (FWHM _<_ 100 km s _[−]_ [1] ) line peoduced by molecular clouds and photodissociation regions within a compact region ( _∼_ 2 pkpc)
of a galaxy [14, 23], or by small ( _∼_ 2 pkpc) clumps of cold neutral medium
(CNM) that displaced by several pkpc from the main body of a galaxy undergoing intense star formation [13]. Note that the contrast of emission from CNM
clumps may be substantially reduced as the cosmic microwave background
(CMB) radiation increases in temperature with redshift (the CMB is at 18.5 K
at _z_ = 5 _._ 7) so as to be similar to the excitation temperature of the emission

[14].
In both cases, the [C ii] emission is excited by FUV radiation from ongoing
star formation. Using an empirical relation between _L_ [C ii] and SFR, the measured _L_ [C ii] would correspond to a [C ii]-based SFR of SFR [C ii] = 14 _M_ _⊙_ yr _[−]_ [1]

([C ii]1030A) and 19 _M_ _⊙_ yr _[−]_ [1] (B), respectively, with an expected uncertainty
of a factor of 2 due to the scatter [24, 25]. Theoretical studies predict consistent
values for gas clouds of solar metallicity [14]. These sources were not detected
in a rest-frame FIR continuum, yielding only a loose 2 _σ_ upper limit to the IRbased SFR of _≈_ 30 _M_ _⊙_ yr _[−]_ [1], which is still consistent with the [C ii]-inferred
SFR.
For our claimed [C ii] sources, no significant counterparts have so far been
found either in the Ly _α_ emission line or in the rest-frame FUV continuum,
despite the availability of deep Hubble Space Telescope (HST) images and the
MUSE datacube. The lack of detection in an HST image ( _≈_ 9000A [˚] observed
or _≈_ 1350A [˚] in the rest-frame) gives a 2 _σ_ upper limit of _∼_ 59 nJy, which
corresponds at this redshift to a FUV-based SFR of _∼_ 2 _M_ _⊙_ yr _[−]_ [1] (methods),
considerably lower than the [C ii]-based SFRs. This therefore suggests that
the FUV emission from SFR at the required levels must have been severely
attenuated by dust, which would also explain the absence of Ly _α_ .
The absence of detectable FUV emission is also in some tension with the
“normal” [C ii] sources that have been detected at similar redshifts, which are
usually detected in rest-frame UV and Ly _α_ emission [26, 27], with typical UV
obscuration fractions _∼_ 40% [28]. A few other reports of narrow (FWHM =
50–90 km s _[−]_ [1] ) [C ii] sources at _z_ _>_ 6 have come from following up sources
that had already been detected in Ly _α_ and the FUV [29, 30].This difference
with the sources claimed here may be partially explained by the difference in
observing strategy: our own study was based on a blind search as against the
follow-up observations of previously detected FUV sources. However, heavy
obscuration may be at odds with the unusual spatial compactness and narrow
spectral width of the [C ii] sources, which suggest they are unlikely to be
mature massive systems, which are observed as FIR-bright dusty star-forming
galaxies at lower redshifts. Rather, they may represent a different population of
galaxies specific to the high-redshift universe. On the other hand, simulations
show that selective attenuation by dense dust clouds that embed young stellar
clusters may lead to absorption of most of the UV luminosity [31].
We cannot therefore yet make a conclusive statement about the nature of
these [C ii]-emitting sources. The threefold rarity of simultaneously having 1)

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 5


these unusual [C ii] sources, 2) a strong overdensity of galaxies, and 3) the rich
high ionization C iv absorption system (rare at these redshifts), however, suggests that there may be some connection between the observed [C ii] properties
and the unusual high-ionization conditions that are seen in this particular
region, which we are observing at the time that the cosmic reionization of the
Universe was approaching completion. Addressing this question will require
us to bridge between the rest-frame FUV and FIR views of the high redshift universe in order to unveil the stellar content and the star formation at

wavelengths that are much less affected by dust. Deep NIR observations with
JWST will soon enable us to clarify the origin of these unusual [C ii] lines and
the links between different physical processes occurring within this extreme
environment during the end stages of cosmic reionization.

### **References**


[1] Simcoe, R.A., Sargent, W.L.W., Rauch, M., Becker, G.: Observations of
Chemically Enriched QSO Absorbers near _z_ _∼_ 2 _._ 3 Galaxies: Galaxy Formation Feedback Signatures in the Intergalactic Medium. Astrophys. J.
**637**, 648–668 (2006)


[2] Prochaska, J.X., Wolfe, A.M., Howk, J.C., Gawiser, E., Burles, S.M.,
Cooke, J.: The UCSD/Keck Damped Ly _α_ Abundance Database: A
Decade of High-Resolution Spectroscopy. Astrophys. J. Supp. **171** (1),
29–60 (2007)


[3] Fox, A.J., Ledoux, C., Petitjean, P., Srianand, R.: C IV absorption in
damped and sub-damped Lyman- _α_ systems. Correlations with metallicity
and implications for galactic winds at z _≈_ 2-3. Astron. Astrophys. **473** (3),
791–803 (2007)


[4] Bordoloi, R., O’Meara, J.M., Sharon, K., Rigby, J.R., Cooke, J., Shaban,
A., Matuszewski, M., Rizzi, L., Doppmann, G., Martin, D.C., Moore,
A.M., Morrissey, P., Neill, J.D.: Resolving the H I in damped Lyman _α_
systems that power star formation. Nature **606** (7912), 59–63 (2022)


[5] D´ıaz, C.G., Ryan-Weber, E.V., Karman, W., Caputi, K.I., Salvadori, S.,
Crighton, N.H., Ouchi, M., Vanzella, E.: Faint LAEs near _z_ _>_ 4 _._ 7 C IV
absorbers revealed by MUSE. Mon. Not. R. Astron. Soc. **502** (2), 2645–
2663 (2021)


[6] Wu, Y., Cai, Z., Neeleman, M., Finlator, K., Zhang, S., Prochaska, J.X.,
Wang, R., Emonts, B.H.C., Fan, X., Keating, L.C., Wang, F., Yang, J.,
Hennawi, J.F., Wang, J.: A [C II] 158 _µ_ m emitter associated with an O
I absorber at the end of the reionization epoch. Nature Astronomy **5**,
1110–1117 (2021)

Springer Nature 2021 L [A] TEX template


6 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


[7] Becker, G.D., Sargent, W.L.W., Rauch, M., Simcoe, R.A.: Discovery
of Excess O I Absorption toward the z=6.42 QSO SDSS J1148+5251.
Astrophys. J. **640** (1), 69–80 (2006)


[8] Simcoe, R.A., Cooksey, K.L., Matejek, M., Burgasser, A.J., Bochanski,
J., Lovegrove, E., Bernstein, R.A., Pipher, J.L., Forrest, W.J., McMurtry,
C., Fan, X., O’Meara, J.: Constraints on the Universal C IV Mass Density
at _z_ _∼_ 6 from Early Infrared Spectra Obtained with the Magellan FIRE
Spectrograph. The Astrophysical Journal **743** (1), 21 (2011)


[9] Chen, S.-F.S., Simcoe, R.A., Torrey, P., Ba˜nados, E., Cooksey, K., Cooper,
T., Furesz, G., Matejek, M., Miller, D., Turner, M., Venemans, B., Decarli,
R., Farina, E.P., Mazzucchelli, C., Walter, F.: Mg II Absorption at
2 _<_ _z_ _<_ 7 with Magellan/Fire. III. Full Statistics of Absorption toward
100 High-redshift QSOs. Astrophys. J. **850**, 188 (2017)


[10] Codoreanu, A., Ryan-Weber, E.V., Garc´ıa, L.A., [´] Crighton, N.H.M.,
Becker, G., Pettini, M., Madau, P., Venemans, B.: The CGM and IGM at
_z_ _∼_ 5: metal budget and physical connection. Mon. Not. R. Astron. Soc.
**481** (4), 4940–4959 (2018)


[11] Cooper, T.J., Simcoe, R.A., Cooksey, K.L., Bordoloi, R., Miller, D.R.,
Furesz, G., Turner, M.L., Ba˜nados, E.: Heavy Element Absorption Systems at 5 _._ 0 _<_ _z_ _<_ 6 _._ 8: Metal-poor Neutral Gas and a Diminishing
Signature of Highly Ionized Circumgalactic Matter. Astrophys. J. **882** (2),
77 (2019)


[12] Becker, G.D., Pettini, M., Rafelski, M., D’Odorico, V., Boera, E., Christensen, L., Cupani, G., Ellison, S.L., Farina, E.P., Fumagalli, M., L´opez,
S., Neeleman, M., Ryan-Weber, E.V., Worseck, G.: The Evolution of
O I over 3 _._ 2 _<_ _z_ _<_ 6 _._ 5: Reionization of the Circumgalactic Medium.
Astrophys. J. **883** (2), 163 (2019)


[13] Vallini, L., Gallerani, S., Ferrara, A., Baek, S.: Far-infrared line emission
from high-redshift galaxies. Mon. Not. R. Astron. Soc. **433** (2), 1567–1572
(2013)


[14] Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., Yue, B.: On the [CII]SFR Relation in High Redshift Galaxies. Astrophys. J. **813** (1), 36 (2015)


[15] Dutta, R., Fumagalli, M., Fossati, M., Bielby, R.M., Stott, J.P., Lofthouse,
E.K., Cantalupo, S., Cullen, F., Crain, R.A., Tripp, T.M., Prochaska,
J.X., Arrigoni Battaia, F., Burchett, J.N., Fynbo, J.P.U., Murphy, M.T.,
Schaye, J., Tejos, N., Theuns, T.: Metal-enriched halo gas across galaxy
overdensities over the last 10 billion years. Mon. Not. R. Astron. Soc.
**508** (3), 4573–4599 (2021)

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 7


[16] Toshikawa, J., Malkan, M.A., Kashikawa, N., Overzier, R., Uchiyama, H.,
Ota, K., Ishikawa, S., Ito, K.: Discovery of Protoclusters at z _∼_ 3.7 and 4.9:
Embedded in Primordial Superclusters. Astrophys. J. **888** (2), 89 (2020)


[17] Venemans, B.P., Walter, F., Neeleman, M., Novak, M., Otter, J., Decarli,
R., Ba˜nados, E., Drake, A., Farina, E.P., Kaasinen, M., Mazzucchelli, C.,
Carilli, C., Fan, X., Rix, H.-W., Wang, R.: Kiloparsec-scale ALMA Imaging of [C II] and Dust Continuum Emission of 27 Quasar Host Galaxies
at z _∼_ 6. Astrophys. J. **904** (2), 130 (2020)


[18] Zana, T., Gallerani, S., Carniani, S., Vito, F., Ferrara, A., Lupi, A., Di
Mascia, F., Barai, P.: Enhanced star formation in z 6 quasar companions.
Mon. Not. R. Astron. Soc. **513** (2), 2118–2135 (2022)


[19] Aravena, M., Decarli, R., Walter, F., Bouwens, R., Oesch, P.A., Carilli,
C.L., Bauer, F.E., Da Cunha, E., Daddi, E., G´onzalez-L´opez, J., Ivison,
R.J., Riechers, D.A., Smail, I., Swinbank, A.M., Weiss, A., Anguita, T.,
Bacon, R., Bell, E., Bertoldi, F., Cortes, P., Cox, P., Hodge, J., Ibar, E.,
Inami, H., Infante, L., Karim, A., Magnelli, B., Ota, K., Popping, G., van
der Werf, P., Wagg, J., Fudamoto, Y.: The ALMA Spectroscopic Survey
in the Hubble Ultra Deep Field: Search for [CII] Line and Dust Emission
in 6 _< z_ _<_ 8 Galaxies. Astrophys. J. **833** (1), 71 (2016)


[20] Neeleman, M., Kanekar, N., Prochaska, J.X., Rafelski, M., Carilli, C.L.,
Wolfe, A.M.: [C II] 158- _µ_ m emission from the host galaxies of damped
Lyman-alpha systems. Science **355** (6331), 1285–1288 (2017)


[21] Fujimoto, S., Silverman, J.D., Bethermin, M., Ginolfi, M., Jones, G.C.,
Le F`evre, O., Dessauges-Zavadsky, M., Rujopakarn, W., Faisst, A.L.,
Fudamoto, Y., Cassata, P., Morselli, L., Maiolino, R., Schaerer, D., Capak,
P., Yan, L., Vallini, L., Toft, S., Loiacono, F., Zamorani, G., Talia, M.,
Narayanan, D., Hathi, N.P., Lemaux, B.C., Boquien, M., Amorin, R.,
Ibar, E., Koekemoer, A.M., M´endez-Hern´andez, H., Bardelli, S., Vergani,
D., Zucca, E., Romano, M., Cimatti, A.: The ALPINE-ALMA [C II]
Survey: Size of Individual Star-forming Galaxies at _z_ = 4–6 and Their
Extended Halo Structure. Astrophys. J. **900** (1), 1 (2020)


[22] Fudamoto, Y., Smit, R., Bowler, R.A.A., Oesch, P.A., Bouwens, R., Stefanon, M., Inami, H., Endsley, R., Gonzalez, V., Schouws, S., Stark,
D., Algera, H.S.B., Aravena, M., Barrufet, L., da Cunha, E., Dayal,
P., Ferrara, A., Graziani, L., Hodge, J.A., Hygate, A.P.S., Inoue, A.K.,
Nanayakkara, T., Pallottini, A., Pizzati, E., Schneider, R., Sommovigo,
L., Sugahara, Y., Topping, M., van der Werf, P., Bethermin, M., Cassata,
P., Dessauges-Zavadsky, M., Ibar, E., Faisst, A.L., Fujimoto, S., Ginolfi,
M., Hathi, N., Jones, G.C., Pozzi, F., Schaerer, D.: The ALMA REBELS
Survey: Average [C II] 158 _µ_ m Sizes of Star-forming Galaxies from z _∼_ 7

Springer Nature 2021 L [A] TEX template


8 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


to z _∼_ 4. Astrophys. J. **934** (2), 144 (2022)


[23] Olsen, K.P., Greve, T.R., Narayanan, D., Thompson, R., Toft, S., Brinch,
C.: Simulator of Galaxy Millimeter/Submillimeter Emission (S´ıGAME):
The [C ii]-SFR Relationship of Massive z = 2 Main Sequence Galaxies.
Astrophys. J. **814** (1), 76 (2015)


[24] De Looze, I., Cormier, D., Lebouteiller, V., Madden, S., Baes, M., Bendo,
G.J., Boquien, M., Boselli, A., Clements, D.L., Cortese, L., Cooray, A.,
Galametz, M., Galliano, F., Graci´a-Carpio, J., Isaak, K., Karczewski,
O.�L., Parkin, T.J., Pellegrini, E.W., R´emy-Ruyer, A., Spinoglio, L.,
Smith, M.W.L., Sturm, E.: The applicability of far-infrared fine-structure
lines as star formation rate tracers over wide ranges of metallicities and
galaxy types. Astron. Astrophys. **568**, 62 (2014)


[25] Schaerer, D., Ginolfi, M., B´ethermin, M., Fudamoto, Y., Oesch, P.A.,
Le F`evre, O., Faisst, A., Capak, P., Cassata, P., Silverman, J.D., Yan,
L., Jones, G.C., Amorin, R., Bardelli, S., Boquien, M., Cimatti, A.,
Dessauges-Zavadsky, M., Giavalisco, M., Hathi, N.P., Fujimoto, S., Ibar,
E., Koekemoer, A., Lagache, G., Lemaux, B.C., Loiacono, F., Maiolino,
R., Narayanan, D., Morselli, L., M´endez-Hern`andez, H., Pozzi, F., Riechers, D., Talia, M., Toft, S., Vallini, L., Vergani, D., Zamorani, G., Zucca,
E.: The ALPINE-ALMA [C II] survey. Little to no evolution in the [C
II]-SFR relation over the last 13 Gyr. Astron. Astrophys. **643**, 3 (2020)


[26] Carniani, S., Maiolino, R., Amorin, R., Pentericci, L., Pallottini, A.,
Ferrara, A., Willott, C.J., Smit, R., Matthee, J., Sobral, D., Santini,
P., Castellano, M., De Barros, S., Fontana, A., Grazian, A., Guaita,
L.: Kiloparsec-scale gaseous clumps and star formation at z = 5-7.
Mon. Not. R. Astron. Soc. **478** (1), 1170–1184 (2018)


[27] Le F`evre, O., B´ethermin, M., Faisst, A., Jones, G.C., Capak, P., Cassata, P., Silverman, J.D., Schaerer, D., Yan, L., Amorin, R., Bardelli,
S., Boquien, M., Cimatti, A., Dessauges-Zavadsky, M., Giavalisco, M.,
Hathi, N.P., Fudamoto, Y., Fujimoto, S., Ginolfi, M., Gruppioni, C., Hemmati, S., Ibar, E., Koekemoer, A., Khusanova, Y., Lagache, G., Lemaux,
B.C., Loiacono, F., Maiolino, R., Mancini, C., Narayanan, D., Morselli,
L., M´endez-Hern`andez, H., Oesch, P.A., Pozzi, F., Romano, M., Riechers,
D., Scoville, N., Talia, M., Tasca, L.A.M., Thomas, R., Toft, S., Vallini,
L., Vergani, D., Walter, F., Zamorani, G., Zucca, E.: The ALPINE-ALMA

[CII] survey. Survey strategy, observations, and sample properties of 118
star-forming galaxies at 4 _< z_ _<_ 6. Astron. Astrophys. **643**, 1 (2020)


[28] Fudamoto, Y., Oesch, P.A., Faisst, A., B´ethermin, M., Ginolfi, M., Khusanova, Y., Loiacono, F., Le F`evre, O., Capak, P., Schaerer, D., Silverman,
J.D., Cassata, P., Yan, L., Amorin, R., Bardelli, S., Boquien, M., Cimatti,

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 9


A., Dessauges-Zavadsky, M., Fujimoto, S., Gruppioni, C., Hathi, N.P.,
Ibar, E., Jones, G.C., Koekemoer, A.M., Lagache, G., Lemaux, B.C.,
Maiolino, R., Narayanan, D., Pozzi, F., Riechers, D.A., Rodighiero, G.,
Talia, M., Toft, S., Vallini, L., Vergani, D., Zamorani, G., Zucca, E.: The
ALPINE-ALMA [CII] survey. Dust attenuation properties and obscured
star formation at z _∼_ 4.4-5.8. Astron. Astrophys. **643**, 4 (2020)


[29] Pentericci, L., Carniani, S., Castellano, M., Fontana, A., Maiolino, R.,
Guaita, L., Vanzella, E., Grazian, A., Santini, P., Yan, H., Cristiani,
S., Conselice, C., Giavalisco, M., Hathi, N., Koekemoer, A.: Tracing the
Reionization Epoch with ALMA: [C II] Emission in z _∼_ 7 Galaxies.
Astrophys. J. **829** (1), 11 (2016)


[30] Bradaˇc, M., Garcia-Appadoo, D., Huang, K.-H., Vallini, L., Quinn Finney,
E., Hoag, A., Lemaux, B.C., Borello Schmidt, K., Treu, T., Carilli, C.,
Dijkstra, M., Ferrara, A., Fontana, A., Jones, T., Ryan, R., Wagg, J.,
Gonzalez, A.H.: ALMA [C II] 158 _µ_ m Detection of a Redshift 7 Lensed
Galaxy behind RXJ1347.1-1145. Astrophys. J. **836** (1), 2 (2017)


[31] Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S., Vallini,
L.: Dusty galaxies in the Epoch of Reionization: simulations.
Mon. Not. R. Astron. Soc. **477** (1), 552–565 (2018)

Springer Nature 2021 L [A] TEX template


10 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


**a**



80


60


40


20


0


−20


−40


80


60


40


20


0


−20


−40







5°25'20"


00"


24'40"


20"

















J2000 Right Ascension


**Fig.** **1** **ALMA** **observations** **of** **the** **two** **[C** ii **]** **sources. a**, the field of QSO J1030+0524.
The background is a composite color image of the field with the Hubble Space Telescope
images in the F775W, F850LP, andf F160W bands. The field-of-view of the ALMA observation is marked by the red line. The [C ii]-detected sources ([C ii]1030A and [C ii]1030B)
are marked by red squares. The large circles of the dotted lines denote the radii of 100 and
200 physical kpc from the central QSO. For comparison, the purple dots indicate the locations of four Ly _α_ -emitters (LAEs #1–4) found in the MUSE datacube whose field-of-view is
marked by the large square of the purple dashed line [5]. **b** and **c**, the [C ii] moment-0 maps
(3 _[′′]_ _×_ 3 _[′′]_ ) of [C ii]1030A and [C ii]1030B, respectively. The solid (dashed) contours mark positive (negative) steps of 1 _σ_ ( _≈_ 0 _._ 25 mJy km s _[−]_ [1] per beam) starting at 2 _σ_ ( _−_ 2 _σ_ ). The sizes
of the synthesized beams are indicated at the bottom left.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 11



3


2


1


0


−1


3


2


1


0


−1


1.5


1.0


0.5


0.0


200


100


0















−1000 −500 0 500 1000 1500 2000


Velocity relative to _z_ = 5.7246 [km/s]











5.70 5.71 5.72 5.73 5.74 5.75 5.76 5.77

Redshift


**Fig.** **2** **Emission** **and** **absorption** **spectra** **from** **the** **[C** ii **]** **sources** **and** **QSO**
**J1030** + **0524.** **a** and **b**, the ALMA spectra of the [C ii] 158 _µ_ m emission of the [C ii]1030A
and B, respectively. The gray shaded region indicates the 1 _σ_ noise. The red solid line shows
a single-Gaussian model fit to the data. The red dotted vertical lines mark the channel
intervals that were collapsed to generate the [C ii] moment-0 maps. The blue dashed vertical lines indicate the location of three absorbers. The origin of the velocity scale was chosen
to correspond to the strongest C iv absorption system at _z_ abs = 5 _._ 7246. **c**, the absorption
profiles of the C iv doublet in the continuum-normalized spectrum of the QSO J1030+0524.
The C iv doublet lines in the same system are connected. The velocity scale is applicable
to the bluer line (rest-frame 1548 [˚] A) of the doublet. The gray-dashed regions in the spectrum indicate the redder 1550 [˚] A) line. The brown line indicates the 1 _σ_ noise spectrum. **d**,
impact parameter versus redshift and radial velocity relative to the strongest C iv absorber
at _z_ abs = 5 _._ 7246. The _y_ = 0 line corresponds to the QSO sightline. The [C ii] sources are
highlighted by red stars and four MUSE LAEs are presented by purple dots.

Springer Nature 2021 L [A] TEX template


12 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


**Table** **1** **ALMA** **measurements** **for** **the** **two** **[C** ii **]** **sources.** The impact parameter is
the transverse separation from the QSO J1030+0524 sightline in physical kpc, ∆ _V_ is the
velocity shift relative to each of the three descrete C iv absorption components. The [C ii]
flux and luminosity are corrected for the primary beam response.


[C ii]1030A [C ii]1030B


J2000 Right Ascension 10 [h] 30 [m] 27 _._ 215 [s] 10 [h] 30 [m] 25 _._ 921 [s]

J2000 Declination +05 [d] 25 [m] 09 _._ 36 [s] +05 [d] 24 [m] 50 _._ 20 [s]

Impact parameter (pkpc) 86 109
Redshift 5.7354 5.7101
∆ _V_ relative to _z_ abs = 5 _._ 7246 (km s _[−]_ [1] ) +485 _−_ 645
∆ _V_ relative to _z_ abs = 5 _._ 7443 (km s _[−]_ [1] ) _−_ 392 _−_ 1518
∆ _V_ relative to _z_ abs = 5 _._ 7411 (km s _[−]_ [1] ) _−_ 250 _−_ 1377
FWHM spatial size (pkpc) _<_ 2 _._ 4 _<_ 2 _._ 4

[C ii] flux (Jy km s _[−]_ [1] ) 0 _._ 174 _±_ 0 _._ 027 0 _._ 276 _±_ 0 _._ 044
FWHM line width (km s _[−]_ [1] ) 64 _±_ 11 62 _±_ 11

[C ii] luminosity (10 [8] _L_ _⊙_ ) 1 _._ 61 _±_ 0 _._ 24 2 _._ 21 _±_ 0 _._ 36

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 13

### **Methods**


**Cosmology**


Throughout this paper, we adopted a flat Λ Cold Dark Matter cosmology with
Ω Λ = 0 _._ 69, Ω M = 0 _._ 31 and _H_ 0 = 67 _._ 7 km s _[−]_ [1] Mpc _[−]_ [1] [32] when calculating
physical parameters.


**ALMA** **observations** **and** **data** **reduction**


The ALMA observations reported here were carried out in 2018 September
(program ID: 2017.1.000621.S) with the array in a configuration of 43 12 m
antennas with baselines from 15–1397 m. The primary beam of the 12 m ALMA
antennas is _≈_ 45 _[′′]_ in diameter at _∼_ 260 GHz. The dataset used in this study
covers a mosaic of seven offset but overlapping pointings that together cover a
roughly circular field of _≈_ 0 _._ 46 arcmin [2] centered on the optical coordinate of
the background QSO J1030+0524 (10 [h] 30 [m] 27 [s] _._ 092, +05 _[◦]_ 24 _[′]_ 55 _._ 02 _[′′]_ ; [33]), with
41 min of total on-source integration. Extended Data Fig. 1 shows the mosaiced
field coverage, which is approximately a circular region of 23 _[′′]_ in radius, and
the resulting antenna response, which is 67% and 47%, respectively, at the
positions of [C ii]1030A and [C ii]1030B.
The datacubes are generated from four spectral windows (SPWs), each of
which has a band width of _≈_ 1 _._ 875 GHz. Of these, two SPWs are adjusted
to cover the three absorbers at _z_ abs = 5 _._ 7246 _,_ 5 _._ 7411 and 5 _._ 7443 in the

[C ii] 158 _µ_ m emission line, respectively, with a minimum overlap at 282 _._ 3 GHz
to yield a continuous frequency coverage of 280.5–284.0 GHz. The other two
SPWs cover other separate frequency ranges around 294 GHz, where there is no
corresponding absorption system seen in the quasar spectrum. Each SPW was
divided into 128 channels, each with a width of 15.6 MHz (16.6 km s _[−]_ [1] ), and
the instrumental velocity dispersion corresponds to 2 channels (33 km s _[−]_ [1] ).
The ALMA data was processed using the CASA [34] pipeline for ALMA
(version 5.4), using the standard calibration procedure. The final datacubes
and the continuum images were obtained using CASA `tclean` task with natural weighting to maximize sensitivity. In doing so, we adopted uvtaper (a
Gaussian taper on the weights of the _uv_ data) of 0 _×_ 220 mas and a position
angle (PA) 119 degree in order to circularize the synthesized beam as much
as possible. The resulting beam is 0 _._ 35 _[′′]_ in FWHM diameter. The continuum
image that collapses all the four SPWs has a 1 _σ_ sensitivity of 31 _µ_ Jy per beam.
For the moment-0 [C ii] maps, the four channels (62.5 MHz; _≈_ 66 km s _[−]_ [1] )
that cover the emission line were collapsed resulting in a 1 _σ_ sensitivity of
4 _._ 1 (4 _._ 2) mJy km s _[−]_ [1] per beam at the observed frequency of the [C ii]1030A
([C ii]1030B).


**Blind** **line** **search**


We employed the `findclumps` algorithm [35], implemented in the `interferopy`
package for Python [36], for our blind search for emission-line candidates.

Springer Nature 2021 L [A] TEX template


14 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


Briefly, `findclumps` performs a top-hat convolution to a datacube to generate
a set of collapsed images, and searches for peaks exceeding a certain S/N
threshold. Clumps that are detected with small offsets in spatial position and
frequency are cropped as duplicates, keeping the one with the highest S/N in
the final catalog. We ran the line search with frequency window sizes from 4
to 17 channels (corresponding to _≈_ 66–282 km s _[−]_ [1] ) and adopted the offset
thresholds of 1 _[′′]_ and 280 MHz (300 km s _[−]_ [1] ) for cropping duplicates.
To assess the significance of the detections, we performed the same line
search for (unphysical) negative peaks and computed the fidelity of the detections, which represents the probability that a positive line detection at a given
S/N is real, following the methods in the literature [35]. Extended Data Fig. 2
shows the number of positive and negative peak detections (upper panels) and
the fidelity (lower panel) as a function of S/N. Expressing the fidelity with an
error function, we found that 95% fidelity is reached as S _/_ N = 5 _._ 8–6 _._ 2, with
only small variations between the SPWs. We selected the two claimed [C ii]
sources ([C ii] 1030A and B), detected in four-channel collapsed images of two
SPWs, as the only sources that have _>_ 6 _σ_ significance and found that there
are no spurious negative signals at this 6 _._ 0 _σ_ level of significance. The fidelity of
the two [C ii] sources were computed to be 96% (A) and 99% (B) respectively.
For each of the three absorption systems, a velocity interval of _±_ 700 km s _[−]_ [1]

was taken as the relevant velocity range within which a source could be considered to be associated with the absorber. This yield a contiguous velocity
interval of 2280 km s _[−]_ [1], from _−_ 700 km s _[−]_ [1] of the lower- _z_ absorber’s redshift ( _z_ abs = 5 _._ 7246) to +700 km s _[−]_ [1] of the higher- _z_ absorber’s redshift
( _z_ abs = 5 _._ 7443), which cover all of the the two [C ii] sources and four LAEs
detected in the MUSE datacube. The small chance that the two most significant peaks, if actually spurious, both lie within this physically significant
region of association, boosts the fidelity values of the claimed [C ii] detections
to _>_ 99 _._ 9%.


**Reliability** **check** **of** **the** **detections**


We further examined the reliability of the two claimed sources by analysing
independent sub-sets of the data. We processed separately the two independent
XX and YY polarization correlations. The [C ii] intensity maps were generated
from the same emission line channels, and the one-dimensional spectra were
extracted from the same spaxels as the full analysis. As shown in Extended
Data Fig. 3, the line emission is always detected with consistent observed
fluxes at 4 _._ 2–4 _._ 7 _σ_ at the expected spatial position (within _<_ 0 _._ 2 _[′′]_ ) and at the
expected frequency in each of the two independent data sets.
Since the ALMA observations were in the form of a mosaic of seven offset but overlapping pointings, both the claimed sources in fact appear (at a
different location relative to the pointing center) in two independent pointings (Figure 1), and these pointings could therefore be reduced separately. The
moment-0 maps and the spectra, created in the same way as above, are shown

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 15


in Extended Data Fig. 3. The claimed sources were detected with consistent
fluxes at 3 _._ 4–5 _._ 3 _σ_ .
Finally, a similar test was also carried out using a temporal split of the
data stream into two equal segments. These two datasets may not strictly
be independent because the two observations exposures were made serially
without changes in the instrumental setups, but serves as a check whether
the signals come from random noise or not: it should be extremely rare that
spurious sources due to random noise are detected consistently in two different
exposures. Again, the line emission is consistently detected at the same spatial
positions and at the expected frequencies in both the first and second halves
of the data, at signal to noise ratios of between 3 _._ 9–4 _._ 9 _σ_ .
These tests all convincingly indicate that the detected lines are plausibly
real signals from astronomical sources and not random noise or other spurious
signals.


**Line** **identification**


We now address the question of whether the line emission is indeed the

[C ii] 158 _µ_ m emission line at the _z_ _≈_ 5 _._ 7 redshift of the C iv absorption system
or some other transition at lower redshift produced by unrelated foreground
objects (background sources can be safely neglected).
The most likely low-redshift interlopers would be CO(3–2) (at _z_ _≈_ 0 _._ 22) or
higher- _J_ CO emission ( _z_ _≈_ 0 _._ 63–2 _._ 3). Using published CO luminosity functions
for the redshift range between 0 and 6 [37], we estimated that the expected
number of CO sources within the whole datacube should be approximately 0.4
sources. In doing so, we considered CO transitions up to _J_ = 8–7 and used
the published Schechter luminosity function parameters derived for each CO
transition at the closest redshift. The luminosity function of CO(6–5) at _z_ = 2
was adopted also for CO(7–6) and CO(8–7) as no measurement is provided
for these highest transitions. We then considered the expected number of CO
sources that should be detected, at a line flux brighter or equal to the observed
flux of the (fainter) [C ii]1030A, and within the circular survey volume of radius
23 _[′′]_ and the frequency (redshift) interval corresponding to the whole ALMA
datacube composed of four SPWs. The results are summarized in Extended
Data Table 1.

The chance of finding two unrelated CO sources within the velocity range
of interest (across 2280 km s _[−]_ [1] around the absorption systems; see above)
is therefore of order (0 _._ 4 _×_ 2280 _/_ 7380) [2] _≈_ 1 _._ 5%, which we consider to be
very unlikely. Even if we ignore the expected number of CO sources and
consider only our observed number of two detected sources within the datacube, the chance that two unrelated emission lines are both found within the
limited velocity range of interest is still (2280 _/_ 7380) [2] _≈_ 9 _._ 5%. These probabilities therefore suggest that the two emission lines are indeed [C ii] emission
associated to this redshift range.
Non-detection of both sources in available deep HST images at _∼_ 9000 [˚] A
(see below) also argues against any interpretation that places these sources

Springer Nature 2021 L [A] TEX template


16 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


at low redshift ( _z_ ≲ 2). This is because, in that case, their stellar continuum
should be detectable. The non-detection is consistent with their lying at high
redshift ( _z_ ≳ 5) if their FUV and Lyman- _α_ emission is intrinsically faint or
obscured by dust. We therefore identify these two emission line signals as [C ii]
emission at _z_ _≈_ 5 _._ 7.


**The** **properties** **of** **the** **[C** ii **]** **sources**


We measured the line properties by fitting a simple Gaussian profile to the
observed one-dimensional spectra extracted from the spaxels enclosed within
0 _._ 24 _[′′]_ of the peak position of the [C ii] sources. The velocity-integrated [C ii]
line flux is measured to be 0 _._ 174 _±_ 0 _._ 027 Jy km s _[−]_ [1] ([C ii]1030A) and 0 _._ 276 _±_
0 _._ 044 Jy km s _[−]_ [1] (B), respectively, with the FWHM line width 64 _±_ 11 km s _[−]_ [1]

([C ii]1030A) and 62 _±_ 11 km s _[−]_ [1] (B). These fluxes are the values after correction for the primary beam response (67% and 47% at the positions of

[C ii]1030A and B, respectively), and for the _≈_ 20% loss falling outside the
aperture of 0 _._ 24 _[′′]_ in radius for extracting the spectra.
The corresponding [C ii] luminosity is _L_ [C ii] = (1 _._ 61 _±_ 0 _._ 24) _×_ 10 [8] _L_ _⊙_
and (2 _._ 21 _±_ 0 _._ 36) _×_ 10 [8] _L_ _⊙_, respectively, for [C ii]1030A and B. An empirical
conversion relation of SFR = _−_ 7 _._ 06 + 1 _._ 0 log 10 (L [C ii] _/L_ _⊙_ ) yields a [C ii]-based
SFR of SFR [C ii] = 14 _M_ _⊙_ yr _[−]_ [1] ([C ii]1030A) and 19 _M_ _⊙_ yr _[−]_ [1] (B), respectively,
with 0.3 dex uncertainty [24]. Although more recent studies inferred closely
consistent conversion relations using high-redshift [C ii] sources [25], the [C ii]
luminosity at fixed SFR is likely to drop when the metallicity is low ( _Z_ _<_
0 _._ 1–0 _._ 2 _Z_ _⊙_ ; [14, 30]). For a lower metallicity, the [C ii]-based SFR would be
even higher and thus requires even more dust obscuration, which is in turn at
odds with the low metallicity. Therefore, these [C ii] sources are likely to be
as metal rich as the levels of normal [C ii] sources detected at similar redshifts

[25, 38].
The ALMA datacubes cover the rest-frame FIR continuum at 1900 GHz

that traces the dust emission. The continuum maps of the sources are shown in
Extended Data Fig. 4. We found no detection of the continuum at the positions
of the [C ii] sources and inferred a 2 _σ_ upper limit of 106 _µ_ Jy ([C ii]1030A) and
158 _µ_ Jy (B). To convert this continuum flux to a total infrared luminosity
( _L_ IR ; 8–1000 _µm_ ), we adopted a conversion factor of _νL_ _ν_ _/L_ IR = 0 _._ 13 ( _ν_ =
1900 GHz) that was inferred using a template of the infrared spectral energy
distribution (SED) of _z_ _∼_ 4 galaxies [39]. The template is consistent with a
modified blackbody ( _S_ _ν_ _≈_ _ν_ _[β]_ _/_ (exp( _hν/kT_ dust ) _−_ 1)) with a fixed index _β_ = 1 _._ 8
and dust temperature _T_ dust = 41 K. This conversion resulted in a 2 _σ_ upper
limit of _L_ IR = 2 _._ 3 _×_ 10 [11] _L_ _⊙_ (A) and 3 _._ 3 _×_ 10 [11] _L_ _⊙_ (B). Finally, we converted
the _L_ IR to obscured SFR by adopting the relation (SFR IR ( _M_ _⊙_ yr _[−]_ [1] ) = 1 _._ 01 _×_
10 _[−]_ [10] _L_ IR ( _L_ _⊙_ )) [40] converted to a [41] initial mass function, and obtained
SFR IR _<_ 23 _M_ _⊙_ yr _[−]_ [1] (A) and _<_ 34 _M_ _⊙_ yr _[−]_ [1] (B) at 2 _σ_ . The 2 _σ_ lower limits of
_L_ [CII] _/L_ IR ratio, _>_ 7 _×_ 10 _[−]_ [4], is consistent with the observed values at similar
redshifts [25] with no evidence of the so-called [CII]-deficit.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 17


**Measurements** **of** **the** **absorption** **systems** **toward** **QSO**
**J1030+0524**


Our analysis uses revised measurements of the absorption systems at _z_ _≈_
5 _._ 7 toward QSO J1030+0524, using improved spectra obtained with both
VLT/XShooter [42] and the Folded-port InfraRed Echellette (FIRE) on Magellan [43]. Archival X-shooter data (acquired under ESO programme 084.A0360(A), 086.A-0162(A), 086.A-0574(A), and 087.A-0607(A)) were retrieved
from the ESO Science Archive Facility and reduced using the PypeIt spectroscopic reduction pipeline [44]. The XShooter exposures from different
programs were carefully and individually corrected for telluric absorption using
numerical atmospheric models and then optimally combined to maximize
signal-to-noise ratio. All exposures were obtained with a 0 _._ 9 _[′′]_ slit, resulting
in spectral resolution is _λ/_ ∆ _λ_ = 5300. FIRE expoures were acquired in April
2011 and reduced using the FIREHOSE pipeline [45]. All data used a 0 _._ 6 _[′′]_ slit
for spectral resolution _λ/_ ∆ _λ_ = 6000. The FIRE spectra were corrected for telluric absorption using observations of A0V standards and a modified version
of the xtellcor package [46, 47]
Because the absorption data span three instrument configurations
(XShooter Visible and NIR channels and FIRE), we have developed
absorption-line fitting routines that generate a single hierarchical physical
model of components and transitions, and then project that model onto
each instrument’s respective spectral data, convolving to each spectrogaph’s
appropriate resolution. The model vector is optimized to fit all instruments
simultaneously using a Markov-Chain Monte Carlo walker as implemented by
the emcee python package [48], to determine confidence intervals from the
posterior distribution. Prior to fitting absorption models, each spectrum was
normalized by a continuum iteratively determined by cubic spline fits with
outlier rejection.
For this particular absorption complex, we identified three distinct components of high-ionization gas with C iv and Si iv aligned in velocity space. The
adopted Voigt profile model constrains redshifts of the C iv and Si iv components to align in velocity. As seen in Extended Data Fig. 5, the C iv component
at _z_ abs = 5 _._ 7411 is a marginal identification with low statistical significance.
However, a firm Si iv detection is seen for all three components. Numerous
low-ionization species are also present at _z_ _∼_ 5 _._ 7; these are not shown and we
defer them to a later analysis as some low-ionization transitions are blended
with lower-redshift interloping absorbers.
Table 2 lists the Voigt profile median and [16%, 84%] confidence intervals
on the fit. It should be noted that XShooter and FIRE likely do not resolve
fine velocity structures, so the Doppler parameters _b_ in the fits may represent
a velocity dispersion among components that would be separated at higher
resolution, rather than the intrinsic width of a single component. However,
tests indicate that the total column densities of these fits are robust when
interpreted as a sum of the unresolved blend.

Springer Nature 2021 L [A] TEX template


18 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


**HST** **broadband** **imaging**


In the field of QSO J1030+0524, we carried out HST broadband imaging in
the F775W (mean wavelength _λ_ mean = 7731 [˚] A) and F160W ( _λ_ mean = 15436 [˚] A)
bands (program IDs 13303 and 15085). In the HST archival database, additional observations (program ID 9777) in F775W and F850LP ( _λ_ mean =
9080 [˚] A) are available. All the HST images were processed and co-added using
the DrizzlePac software [49].
These images were used to search for rest-frame ultraviolet counterparts of
the claimed [C ii] emitters. For sources at _z_ _≈_ 5 _._ 7, the F775W, F850LP, F160W
bands sample the rest-frame 1150 [˚] A (including the wavelength of Lyman- _α_ ),
1350 [˚] A, and 2300 [˚] A, respectively. The 3 _[′′]_ _×_ 3 _[′′]_ cutout images are shown in
Extended Data Fig. 6. No significant counterpart was found at the positions
of the [C ii] sources, yielding 2 _σ_ upper limits of 45 nJy (F775W), 59 nJy
(F850LP), and 31 nJy (F160W) for the aperture photometry in 0 _._ 7 _[′′]_ -diameter.
Here the standard deviation of the photometric flux is estimated by conducting
aperture photometry at random sky positions.
The rest-frame FUV flux traces unobscured star formation of a galaxy.
We converted the F850LP fluxes to the UV-based SFR UV adopting a relation
(SFR FUV ( _M_ _⊙_ yr _[−]_ [1] ) = 0 _._ 72 _×_ 10 _[−]_ [28] _L_ _ν_ (erg s _[−]_ [1] Hz _[−]_ [1] )) [40], yielding SFR UV _<_
2 _._ 4 _M_ _⊙_ yr _[−]_ [1] .


**MUSE** **observation**


We retrieved the archival data of the integral field spectroscopy in this field
taken with the MUSE on the VLT UT4 under ESO programme 095.A0714(A). The datacube covers a 1 _[′]_ _×_ 1 _[′]_ region centered at the position of
QSO J1030+0524 across the wavelength range of 4750–9350 [˚] A with the total
on-source exposure time of 6.4 hrs. The observations were carried out in the
WFM-NOAO-N mode in excellent seeing. The spatial FWHM is _≃_ 0 _._ 6 _[′′]_ measured on the “white light” image, constructed from collapsing the reduced
datacube over the full wavelength range.
The initial data reduction was carried out with the MUSE pipeline (v2.8.5,

[50]). With the pipeline we applied bias subtraction, flat fielding, wavelength
calibration and produced datacubes and pixel tables. The quality of the sky
subtraction in the pipeline reduced version is limited by flat fielding errors,
due to temperature fluctuations in the instrument. As a post-processing step,
we apply CubEx (see e.g. [51, 52]) to perform self-calibration to improve the
flat fielding and sky subtraction. MUSE datacubes often contain small shifts
( _<_ 2 _[′′]_ ) in the field center with respect to the astrometry solution in the header,
this is caused by the so-called “derotator wobble” [53]. In order to facilitate
matched spectroscopy for the ALMA detections in MUSE it was essential that
the astrometry be well calibrated. The MUSE field of view does not contain
any stars with Gaia astrometry, so instead we used the HST/ACS F755W
image as a bridge to propagate Gaia calibration to the MUSE.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 19


We used the MUSE datacube to search for counterparts of [C ii]1030A and
B in the Ly _α_ emission line within search radii of _≈_ 3 _[′′]_, or 20 pkpc, in position
and _±_ 500 km s _[−]_ [1] ) in velocity. No significant Ly _α_ emission was detected at
the expected positions and wavelengths for these [C ii] sources, yielding a 2 _σ_
upper limit of _≈_ 1 _×_ 10 _[−]_ [18] erg s _[−]_ [1] cm _[−]_ [2] on the observed Ly _α_ fluxes.

### **References**


[32] Planck Collaboration, Aghanim, N., Akrami, Y., Ashdown, M., Aumont,
J., Baccigalupi, C., Ballardini, M., Banday, A.J., Barreiro, R.B., Bartolo,
N., Basak, S., Battye, R., Benabed, K., Bernard, J.-P., Bersanelli, M.,
Bielewicz, P., Bock, J.J., Bond, J.R., Borrill, J., Bouchet, F.R., Boulanger,
F., Bucher, M., Burigana, C., Butler, R.C., Calabrese, E., Cardoso, J.F., Carron, J., Challinor, A., Chiang, H.C., Chluba, J., Colombo, L.P.L.,
Combet, C., Contreras, D., Crill, B.P., Cuttaia, F., de Bernardis, P., de
Zotti, G., Delabrouille, J., Delouis, J.-M., Di Valentino, E., Diego, J.M.,
Dor´e, O., Douspis, M., Ducout, A., Dupac, X., Dusini, S., Efstathiou, G.,
Elsner, F., Enßlin, T.A., Eriksen, H.K., Fantaye, Y., Farhang, M., Fergusson, J., Fernandez-Cobos, R., Finelli, F., Forastieri, F., Frailis, M.,
Fraisse, A.A., Franceschi, E., Frolov, A., Galeotta, S., Galli, S., Ganga,
K., G´enova-Santos, R.T., Gerbino, M., Ghosh, T., Gonz´alez-Nuevo, J.,
G´orski, K.M., Gratton, S., Gruppuso, A., Gudmundsson, J.E., Hamann,
J., Handley, W., Hansen, F.K., Herranz, D., Hildebrandt, S.R., Hivon, E.,
Huang, Z., Jaffe, A.H., Jones, W.C., Karakci, A., Keih¨anen, E., Keskitalo, R., Kiiveri, K., Kim, J., Kisner, T.S., Knox, L., Krachmalnicoff, N.,
Kunz, M., Kurki-Suonio, H., Lagache, G., Lamarre, J.-M., Lasenby, A.,
Lattanzi, M., Lawrence, C.R., Le Jeune, M., Lemos, P., Lesgourgues, J.,
Levrier, F., Lewis, A., Liguori, M., Lilje, P.B., Lilley, M., Lindholm, V.,
L´opez-Caniego, M., Lubin, P.M., Ma, Y.-Z., Mac´ıas-P´erez, J.F., Maggio,
G., Maino, D., Mandolesi, N., Mangilli, A., Marcos-Caballero, A., Maris,
M., Martin, P.G., Martinelli, M., Mart´ınez-Gonz´alez, E., Matarrese, S.,
Mauri, N., McEwen, J.D., Meinhold, P.R., Melchiorri, A., Mennella, A.,
Migliaccio, M., Millea, M., Mitra, S., Miville-Deschˆenes, M.-A., Molinari,
D., Montier, L., Morgante, G., Moss, A., Natoli, P., Nørgaard-Nielsen,
H.U., Pagano, L., Paoletti, D., Partridge, B., Patanchon, G., Peiris, H.V.,
Perrotta, F., Pettorino, V., Piacentini, F., Polastri, L., Polenta, G., Puget,
J.-L., Rachen, J.P., Reinecke, M., Remazeilles, M., Renzi, A., Rocha, G.,
Rosset, C., Roudier, G., Rubi˜no-Mart´ın, J.A., Ruiz-Granados, B., Salvati, L., Sandri, M., Savelainen, M., Scott, D., Shellard, E.P.S., Sirignano,
C., Sirri, G., Spencer, L.D., Sunyaev, R., Suur-Uski, A.-S., Tauber, J.A.,
Tavagnacco, D., Tenti, M., Toffolatti, L., Tomasi, M., Trombetti, T.,
Valenziano, L., Valiviita, J., Van Tent, B., Vibert, L., Vielva, P., Villa,
F., Vittorio, N., Wandelt, B.D., Wehus, I.K., White, M., White, S.D.M.,
Zacchei, A., Zonca, A.: Planck 2018 results. VI. Cosmological parameters.
Astron. Astrophys. **641**, 6 (2020)

Springer Nature 2021 L [A] TEX template


20 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


[33] Alam, S., Albareti, F.D., Allende Prieto, C., Anders, F., Anderson, S.F.,
Anderton, T., Andrews, B.H., Armengaud, E., Aubourg, E., [´] Bailey, S.,
Basu, S., Bautista, J.E., Beaton, R.L., Beers, T.C., Bender, C.F., Berlind,
A.A., Beutler, F., Bhardwaj, V., Bird, J.C., Bizyaev, D., Blake, C.H.,
Blanton, M.R., Blomqvist, M., Bochanski, J.J., Bolton, A.S., Bovy, J.,
Shelden Bradley, A., Brandt, W.N., Brauer, D.E., Brinkmann, J., Brown,
P.J., Brownstein, J.R., Burden, A., Burtin, E., Busca, N.G., Cai, Z.,
Capozzi, D., Carnero Rosell, A., Carr, M.A., Carrera, R., Chambers, K.C.,
Chaplin, W.J., Chen, Y.-C., Chiappini, C., Chojnowski, S.D., Chuang,
C.-H., Clerc, N., Comparat, J., Covey, K., Croft, R.A.C., Cuesta, A.J.,
Cunha, K., da Costa, L.N., Da Rio, N., Davenport, J.R.A., Dawson, K.S.,
De Lee, N., Delubac, T., Deshpande, R., Dhital, S., Dutra-Ferreira, L.,
Dwelly, T., Ealet, A., Ebelke, G.L., Edmondson, E.M., Eisenstein, D.J.,
Ellsworth, T., Elsworth, Y., Epstein, C.R., Eracleous, M., Escoffier, S.,
Esposito, M., Evans, M.L., Fan, X., Fern´andez-Alvar, E., Feuillet, D., Filiz
Ak, N., Finley, H., Finoguenov, A., Flaherty, K., Fleming, S.W., FontRibera, A., Foster, J., Frinchaboy, P.M., Galbraith-Frew, J.G., Garc´ıa,
R.A., Garc´ıa-Hern´andez, D.A., Garc´ıa P´erez, A.E., Gaulme, P., Ge, J.,
G´enova-Santos, R., Georgakakis, A., Ghezzi, L., Gillespie, B.A., Girardi,
L., Goddard, D., Gontcho, S.G.A., Gonz´alez Hern´andez, J.I., Grebel,
E.K., Green, P.J., Grieb, J.N., Grieves, N., Gunn, J.E., Guo, H., Harding, P., Hasselquist, S., Hawley, S.L., Hayden, M., Hearty, F.R., Hekker,
S., Ho, S., Hogg, D.W., Holley-Bockelmann, K., Holtzman, J.A., Honscheid, K., Huber, D., Huehnerhoff, J., Ivans, I.I., Jiang, L., Johnson,
J.A., Kinemuchi, K., Kirkby, D., Kitaura, F., Klaene, M.A., Knapp,
G.R., Kneib, J.-P., Koenig, X.P., Lam, C.R., Lan, T.-W., Lang, D., Laurent, P., Le Goff, J.-M., Leauthaud, A., Lee, K.-G., Lee, Y.S., Licquia,
T.C., Liu, J., Long, D.C., L´opez-Corredoira, M., Lorenzo-Oliveira, D.,
Lucatello, S., Lundgren, B., Lupton, R.H., Mack, I. Claude E., Mahadevan, S., Maia, M.A.G., Majewski, S.R., Malanushenko, E., Malanushenko,
V., Manchado, A., Manera, M., Mao, Q., Maraston, C., Marchwinski,
R.C., Margala, D., Martell, S.L., Martig, M., Masters, K.L., Mathur, S.,
McBride, C.K., McGehee, P.M., McGreer, I.D., McMahon, R.G., M´enard,
B., Menzel, M.-L., Merloni, A., M´esz´aros, S., Miller, A.A., MiraldaEscud´e, J., Miyatake, H., Montero-Dorta, A.D., More, S., Morganson, E.,
Morice-Atkinson, X., Morrison, H.L., Mosser, B., Muna, D., Myers, A.D.,
Nandra, K., Newman, J.A., Neyrinck, M., Nguyen, D.C., Nichol, R.C.,
Nidever, D.L., Noterdaeme, P., Nuza, S.E., O’Connell, J.E., O’Connell,
R.W., O’Connell, R., Ogando, R.L.C., Olmstead, M.D., Oravetz, A.E.,
Oravetz, D.J., Osumi, K., Owen, R., Padgett, D.L., Padmanabhan, N.,
Paegert, M., Palanque-Delabrouille, N., Pan, K., Parejko, J.K., Pˆaris, I.,
Park, C., Pattarakijwanich, P., Pellejero-Ibanez, M., Pepper, J., Percival, W.J., P´erez-Fournon, I., P´erez-R`afols, I., Petitjean, P., Pieri, M.M.,
Pinsonneault, M.H., Porto de Mello, G.F., Prada, F., Prakash, A., PriceWhelan, A.M., Protopapas, P., Raddick, M.J., Rahman, M., Reid, B.A.,

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 21


Rich, J., Rix, H.-W., Robin, A.C., Rockosi, C.M., Rodrigues, T.S.,
Rodr´ıguez-Torres, S., Roe, N.A., Ross, A.J., Ross, N.P., Rossi, G., Ruan,
J.J., Rubi˜no-Mart´ın, J.A., Rykoff, E.S., Salazar-Albornoz, S., Salvato, M.,
Samushia, L., S´anchez, A.G., Santiago, B., Sayres, C., Schiavon, R.P.,
Schlegel, D.J., Schmidt, S.J., Schneider, D.P., Schultheis, M., Schwope,
A.D., Sc´occola, C.G., Scott, C., Sellgren, K., Seo, H.-J., Serenelli, A.,
Shane, N., Shen, Y., Shetrone, M., Shu, Y., Silva Aguirre, V., Sivarani,
T., Skrutskie, M.F., Slosar, A., Smith, V.V., Sobreira, F., Souto, D., Stassun, K.G., Steinmetz, M., Stello, D., Strauss, M.A., Streblyanska, A.,
Suzuki, N., Swanson, M.E.C., Tan, J.C., Tayar, J., Terrien, R.C., Thakar,
A.R., Thomas, D., Thomas, N., Thompson, B.A., Tinker, J.L., Tojeiro,
R., Troup, N.W., Vargas-Maga˜na, M., Vazquez, J.A., Verde, L., Viel,
M., Vogt, N.P., Wake, D.A., Wang, J., Weaver, B.A., Weinberg, D.H.,
Weiner, B.J., White, M., Wilson, J.C., Wisniewski, J.P., Wood-Vasey,
W.M., Ye‘che, C., York, D.G., Zakamska, N.L., Zamora, O., Zasowski, G.,
Zehavi, I., Zhao, G.-B., Zheng, Z., Zhou, X., Zhou, Z., Zou, H., Zhu, G.:
The Eleventh and Twelfth Data Releases of the Sloan Digital Sky Survey:
Final Data from SDSS-III. Astrophys. J. Supp. **219** (1), 12 (2015)


[34] McMullin, J.P., Waters, B., Schiebel, D., Young, W., Golap, K.: CASA
Architecture and Applications. In: Shaw, R.A., Hill, F., Bell, D.J. (eds.)
Astronomical Data Analysis Software and Systems XVI. Astronomical
Society of the Pacific Conference Series, vol. 376, p. 127 (2007)


[35] Walter, F., Decarli, R., Aravena, M., Carilli, C., Bouwens, R., da Cunha,
E., Daddi, E., Ivison, R.J., Riechers, D., Smail, I., Swinbank, M., Weiss,
A., Anguita, T., Assef, R., Bacon, R., Bauer, F., Bell, E.F., Bertoldi, F.,
Chapman, S., Colina, L., Cortes, P.C., Cox, P., Dickinson, M., Elbaz, D.,
G´onzalez-L´opez, J., Ibar, E., Inami, H., Infante, L., Hodge, J., Karim, A.,
Le Fevre, O., Magnelli, B., Neri, R., Oesch, P., Ota, K., Popping, G., Rix,
H.-W., Sargent, M., Sheth, K., van der Wel, A., van der Werf, P., Wagg,
J.: ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey
Description. Astrophys. J. **833** (1), 67 (2016)


[36] Boogaard, L., Meyer, R.A., Novak, M.: Interferopy: analysing datacubes
from radio-to-submm observations. Zenodo (2021)


[37] Popping, G., van Kampen, E., Decarli, R., Spaans, M., Somerville, R.S.,
Trager, S.C.: Sub-mm emission line deep fields: CO and [C II] luminosity
functions out to z = 6. Mon. Not. R. Astron. Soc. **461** (1), 93–110 (2016)


[38] Ferrara, A., Sommovigo, L., Dayal, P., Pallottini, A., Bouwens, R.J., Gonzalez, V., Inami, H., Smit, R., Bowler, R.A.A., Endsley, R., Oesch, P.,
Schouws, S., Stark, D., Stefanon, M., Aravena, M., da Cunha, E., De
Looze, I., Fudamoto, Y., Graziani, L., Hodge, J., Riechers, D., Schneider, R., Algera, H.S.B., Barrufet, L., Hygate, A.P.S., Labb´e, I., Li, C.,

Springer Nature 2021 L [A] TEX template


22 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


Nanayakkara, T., Topping, M., van der Werf, P.: The ALMA REBELS
Survey. Epoch of Reionization giants: Properties of dusty galaxies at
_z_ _≈_ 7. Mon. Not. R. Astron. Soc. **512** (1), 58–72 (2022)


[39] B´ethermin, M., Fudamoto, Y., Ginolfi, M., Loiacono, F., Khusanova, Y.,
Capak, P.L., Cassata, P., Faisst, A., Le F`evre, O., Schaerer, D., Silverman, J.D., Yan, L., Amorin, R., Bardelli, S., Boquien, M., Cimatti, A.,
Davidzon, I., Dessauges-Zavadsky, M., Fujimoto, S., Gruppioni, C., Hathi,
N.P., Ibar, E., Jones, G.C., Koekemoer, A.M., Lagache, G., Lemaux, B.C.,
Moreau, C., Oesch, P.A., Pozzi, F., Riechers, D.A., Talia, M., Toft, S.,
Vallini, L., Vergani, D., Zamorani, G., Zucca, E.: The ALPINE-ALMA

[CII] survey: Data processing, catalogs, and statistical source properties.
Astron. Astrophys. **643**, 2 (2020)


[40] Madau, P., Dickinson, M.: Cosmic Star-Formation History. ARA&A **52**,
415–486 (2014)


[41] Chabrier, G.: Galactic Stellar and Substellar Initial Mass Function. PASP
**115**, 763–795 (2003)


[42] Vernet, J., Dekker, H., D’Odorico, S., Kaper, L., Kjaergaard, P., Hammer,
F., Randich, S., Zerbi, F., Groot, P.J., Hjorth, J., Guinouard, I., Navarro,
R., Adolfse, T., Albers, P.W., Amans, J.-P., Andersen, J.J., Andersen,
M.I., Binetruy, P., Bristow, P., Castillo, R., Chemla, F., Christensen, L.,
Conconi, P., Conzelmann, R., Dam, J., de Caprio, V., de Ugarte Postigo,
A., Delabre, B., di Marcantonio, P., Downing, M., Elswijk, E., Finger, G.,
Fischer, G., Flores, H., Fran¸cois, P., Goldoni, P., Guglielmi, L., Haigron,
R., Hanenburg, H., Hendriks, I., Horrobin, M., Horville, D., Jessen, N.C.,
Kerber, F., Kern, L., Kiekebusch, M., Kleszcz, P., Klougart, J., Kragt,
J., Larsen, H.H., Lizon, J.-L., Lucuix, C., Mainieri, V., Manuputy, R.,
Martayan, C., Mason, E., Mazzoleni, R., Michaelsen, N., Modigliani, A.,
Moehler, S., Møller, P., Norup Sørensen, A., Nørregaard, P., P´eroux, C.,
Patat, F., Pena, E., Pragt, J., Reinero, C., Rigal, F., Riva, M., Roelfsema, R., Royer, F., Sacco, G., Santin, P., Schoenmaker, T., Spano, P.,
Sweers, E., Ter Horst, R., Tintori, M., Tromp, N., van Dael, P., van der
Vliet, H., Venema, L., Vidali, M., Vinther, J., Vola, P., Winters, R., Wistisen, D., Wulterkens, G., Zacchei, A.: X-shooter, the new wide band
intermediate resolution spectrograph at the ESO Very Large Telescope.
Astron. Astrophys. **536**, 105 (2011)


[43] Simcoe, R.A., Burgasser, A.J., Schechter, P.L., Fishner, J., Bernstein,
R.A., Bigelow, B.C., Pipher, J.L., Forrest, W., McMurtry, C., Smith,
M.J., Bochanski, J.J.: FIRE: A Facility Class Near-Infrared Echelle
Spectrometer for the Magellan Telescopes. PASP **125** (925), 270 (2013)


[44] Prochaska, J., Hennawi, J., Westfall, K., Cooke, R., Wang, F., Hsyu, T.,

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 23


Davies, F., Farina, E., Pelliccia, D.: PypeIt: The Python Spectroscopic
Data Reduction Pipeline. The Journal of Open Source Software **5** (56),
2308 (2020)


[45] Gagn´e, J., Lambrides, E., Faherty, J.K., Simcoe, R.: FireHose ~~v~~ 2: Firehose
V2.0


[46] Vacca, W.D., Cushing, M.C., Rayner, J.T.: A Method of Correcting NearInfrared Spectra for Telluric Absorption. PASP **115** (805), 389–409 (2003)


[47] Cushing, M.C., Vacca, W.D., Rayner, J.T.: Spextool: A Spectral Extraction Package for SpeX, a 0.8-5.5 Micron Cross-Dispersed Spectrograph.
PASP **116** (818), 362–376 (2004)


[48] Foreman-Mackey, D., Hogg, D.W., Lang, D., Goodman, J.: emcee: The
MCMC Hammer. PASP **125**, 306–312 (2013)


[49] Hoffmann, S.L., Mack, J., Avila, R.J., Martlin, C., Bajaj, V., Cohen,
Y.: The DrizzlePac Handbook, Version 2.0, (Baltimore: Space Telescope
Science Institute). [https://hst-docs.stsci.edu/drizzpac](https://hst-docs.stsci.edu/drizzpac) (2021)


[50] Weilbacher, P.M., Palsa, R., Streicher, O., Bacon, R., Urrutia, T.,
Wisotzki, L., Conseil, S., Husemann, B., Jarno, A., Kelz, A., P´econtalRousset, A., Richard, J., Roth, M.M., Selman, F., Vernet, J.: The data
processing pipeline for the MUSE instrument. Astron. Astrophys. **641**,
28 (2020)


[51] Borisova, E., Cantalupo, S., Lilly, S.J., Marino, R.A., Gallego, S.G.,
Bacon, R., Blaizot, J., Bouch´e, N., Brinchmann, J., Carollo, C.M., Caruana, J., Finley, H., Herenz, E.C., Richard, J., Schaye, J., Straka, L.A.,
Turner, M.L., Urrutia, T., Verhamme, A., Wisotzki, L.: Ubiquitous Giant
Ly _α_ Nebulae around the Brightest Quasars at z _∼_ 3.5 Revealed with
MUSE. Astrophys. J. **831** (1), 39 (2016)


[52] Cantalupo, S., Pezzulli, G., Lilly, S.J., Marino, R.A., Gallego, S.G.,
Schaye, J., Bacon, R., Feltre, A., Kollatschny, W., Nanayakkara, T.,
Richard, J., Wendt, M., Wisotzki, L., Prochaska, J.X.: The large- and
small-scale properties of the intergalactic gas in the Slug Ly _α_ nebula
revealed by MUSE He II emission observations. Mon. Not. R. Astron. Soc.
**483** (4), 5188–5204 (2019)


[53] Bacon, R., Brinchmann, J., Richard, J., Contini, T., Drake, A., Franx, M.,
Tacchella, S., Vernet, J., Wisotzki, L., Blaizot, J., Bouch´e, N., Bouwens,
R., Cantalupo, S., Carollo, C.M., Carton, D., Caruana, J., Cl´ement,
B., Dreizler, S., Epinat, B., Guiderdoni, B., Herenz, C., Husser, T.-O.,
Kamann, S., Kerutt, J., Kollatschny, W., Krajnovic, D., Lilly, S., Martinsson, T., Michel-Dansac, L., Patricio, V., Schaye, J., Shirazi, M., Soto,

Springer Nature 2021 L [A] TEX template


24 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


K., Soucail, G., Steinmetz, M., Urrutia, T., Weilbacher, P., de Zeeuw, T.:
The MUSE 3D view of the Hubble Deep Field South. Astron. Astrophys.
**575**, 75 (2015)


**Data** **availability.** The ALMA, HST, and VLT data sets used in this work
[are publicly available, respectively, through the ALMA data archive at https://](https://almascience.nao.ac.jp/aq/)
[almascience.nao.ac.jp/aq/ (project code 2017.1.00621.S), the HST data archive](https://almascience.nao.ac.jp/aq/)
[at https://archive.stsci.edu/missions-and-data/hst (Proposal IDs 9777, 13303,](https://archive.stsci.edu/missions-and-data/hst)
and 15085), and the European Southern Observatory Science Archive at [http:](http://archive.eso.org)
[//archive.eso.org](http://archive.eso.org) (Programme ID 084.A-0360, 086.A-0162, 086.A-0574, and
087.A-0607, and 095.A-0714).


**Code availability.** The ALMA data was processed using the CASA pipeline
version 5.4, which is available at [https://casa.nrao.edu.](https://casa.nrao.edu) The `interferopy`
package that includes the `findclumps` source finding program is available
at [https://github.com/interferopy/interferopy.](https://github.com/interferopy/interferopy) The VLT/X-shooter spectral
data were reduced using the PypeIt package available at [https://github.com/](https://github.com/pypeit/PypeIt)
[pypeit/PypeIt.](https://github.com/pypeit/PypeIt) The Magellan FIRE spectral data ware reduced using the
FIREHOSE pipeline available at [https://wikis.mit.edu/confluence/display/](https://wikis.mit.edu/confluence/display/FIRE/FIRE+Data+Reduction)
[FIRE/FIRE+Data+Reduction and corrected using the xtellcor package avail-](https://wikis.mit.edu/confluence/display/FIRE/FIRE+Data+Reduction)
able at [http://irtfweb.ifa.hawaii.edu/](http://irtfweb.ifa.hawaii.edu/~spex/index.html) _[∼]_ spex/index.html. The DrizzlePac software used for the HST data reduction is available at [https://www.stsci.](https://www.stsci.edu/scientific-community/software/drizzlepac.html)
[edu/scientific-community/software/drizzlepac.html.](https://www.stsci.edu/scientific-community/software/drizzlepac.html) The reduction pipelines
of the VLT instruments are available at [https://www.eso.org/sci/software/](https://www.eso.org/sci/software/pipelines/)
[pipelines/.](https://www.eso.org/sci/software/pipelines/)


**Acknowledgments.** This work is based on the ALMA observation under
ADS/JAO.ALMA#2011.0.01234.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in
cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research makes use of observations
made with the NASA/ESA Hubble Space Telescope obtained from the Space
Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. This
paper includes data gathered with the 6.5 meter Magellan Telescopes located
at Las Campanas Observatory, Chile. Data analysis was in part carried out
on the Multi-wavelength Data Analysis System operated by the Astronomy
Data Center, NAOJ. We acknowledge support from JSPS KAKENHI Grant
Number JP21K13956.


**Author** **Contribution.** DK, SJL, RB, RAS discussed and planned the
ALMA program and the HST observations in the F775W band. RAS obtained
the HST observation in the F160W band. ACE and RAS analyzed the Xshooter and FIRE spectroscopic data of QSO J1030+0524. RM reduced and
calibrated the MUSE data. SJL, JM, RAS, RM, and ACE contributed to the
discussion of the presented results and the prepareation of the manuscript. DK
led the team, being principal investigator of the ALMA program, analyzed the

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 25


ALMA and ancillary data, wrote the main text and the Methods section, and
produced all figures and the table in the article.


**Conflict** **of** **interest/Competing** **interests.** The authors declare no
competing interests.

Springer Nature 2021 L [A] TEX template


26 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


1.0



5°25'15"


00"


24'45"


30"





10 [h] 30 [m] 28 [s] 27 [s] 26 [s]



0.9


0.8


0.7


0.6


0.5


0.4


0.3


0.2



J2000 Right Ascension


**Extended** **Data** **Fig.** **1** **Antenna** **response** **(primary** **beam)** **map** **of** **the** **mosaic**
**ALMA** **observation.** The response is normalized to one at the field center and survey
field is defined as the area of _≈_ 23 _[′′]_ in radius where the relative response is above 20%.
The primary beam size of the individual 7 pointings ( _r_ = 15 _[′′]_ ) that compose the mosaic
observation is shown by dotted-line circle with the pointing number from 1 to 7. The positions
of the two [C ii] sources ([C ii]1030A and B) are marked by red stars.



SPW [280.58-282.38 GHz]



SPW [292.42-294.22 GHz]

|[CII]1030A [CII]1030B|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||



4 5 6 7

S/N



SPW [294.42-296.22 GHz]


4 5 6 7

S/N



10 [3]


10 [2]


10 [1]


10 [0]


1.0


0.8


0.6


0.4


0.2


0.0



4 5 6 7

S/N





SPW [282.15-283.94 GHz]


4 5 6 7

S/N



**Extended** **Data** **Fig.** **2** **Fidelity** **in** **our** **line** **search.** Upper panels: number of positive
(blue) and negative (i.e., noise; red) peaks detected in the four ALMA datacubes (one column
for each). The frequency range of each SPW is denoted at the top. Lower panels: the fidelity
at given S/Ns with the model fit as an error function (solid red line).

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 27




[CII]1030A _z_ = 5.73544




[CII]1030B _z_ = 5.71011



3
2

1
0


3
2

1
0


3
2

1
0


3
2

1
0


3
2

1
0


3
2

1
0


3
2

1
0







−1



−1







−1



−1







−1



−1







−1



−1







−1



−1







−1



−1





4
3
2
1
0


4
3
2
1
0


4
3
2
1
0


4
3
2
1
0


4
3
2
1
0


4
3
2
1
0


4
3
2
1
0





−1


280.5 281.0 281.5 282.0


Observed frequency [GHz]



282.5 283.0 283.5 284.0


Observed frequency [GHz]



−1



**Extended** **Data** **Fig.** **3** **Reliability** **check** **of** **the** **[C** ii **]** **detection.** For each of

[C ii]1030A (left) and B (right), the spectra and the [C ii] moment-0 maps (2 _[′′]_ _×_ 2 _[′′]_ ) constructed in the reliability tests are compared to those from the full dataset that are shown in
the top row. The second and third rows show the results under only XX or YY polarization.
The forth and fifth rows show the results for the first and second half exposure time intervals. The sixth and seventh rows show the results from processing each of the two individual
ALMA pointings that cover the source position. In the spectral plots, the collapsed channel
window is shown by dotted vertical lines. In the [C ii] intensity maps, the solid (dashed) contours mark positive (negative) steps of 1 _σ_ r.m.s starting at 2 _σ_ ( _−_ 2 _σ_ ). All of these products
from partial dataset exhibit significant signals that coincident both spatially and spectrally
to those seen in the full data.

Springer Nature 2021 L [A] TEX template


28 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_




[CII]1030A


5°25'10"


09"


08"


10 [h] 30 [m] 27.30 [s] 27.25 [s] 27.20 [s] 27.15 [s]


J2000 Right Ascension



0.15


0.10


0.05


0.00


−0.05


−0.10


−0.15




[CII]1030B


5°24'51"


50"


49"


10 [h] 30 [m] 26.00 [s] 25.95 [s] 25.90 [s] 25.85 [s]


J2000 Right Ascension



0.15


0.10


0.05


0.00


−0.05


−0.10


−0.15



**Extended** **Data** **Fig.** **4** **Continuum** **maps.** Each image cutouts the 3 _[′′]_ _×_ 3 _[′′]_ region
centered at the position of [C ii]1030A (left panel) and B (right panel). The rest-frame
1900 GHz continuum intensity is shown by the color scale. The synthesized continuum beam
size is indicated by the white circle in the lower left corner.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 29


1.0


0.5


0.0


1.0


0.5


0.0


1.0


0.5


0.0


1.0


0.5


0.0


−1000 −500 0 500 1000 1500


Velocity relative to _z_ = 5.7246


**Extended** **Data** **Fig.** **5** **C** iv **and** **Si** iv **absorption** **systems** **at** _z_ abs _≈_ 5 _._ 7 **.** Each panel
corresponds to the transition labeled in the upper left. The black line shows the observed
spectrum of QSO J1030 while the light brown line denotes the standard deviation of the flux.
The blue lines indicate 50 random Voigt profiles sampled from the posterior distribution.
The origin of the velocity scale was chosen to correspond to the strongest absorption system
at _z_ abs = 5 _._ 7246, which is marked with the two other systems ( _z_ abs = 5 _._ 7411 and 5.7443)
in the blue dashed lines. The red vertical lines indicate the relative velocities of [C ii]1030A
and B.

Springer Nature 2021 L [A] TEX template


30 _[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_


ACS F775W ACS F850LP WFC3 F160W


ACS F775W ACS F850LP WFC3 F160W


**Extended** **Data** **Fig.** **6** **HST** **broadband** **images.** Each image cutouts the 3 _[′′]_ _×_ 3 _[′′]_

region centered at the position of the [C ii]1030A (upper row) and B (lower row). From left
to right, these images are F775W, F850LP, and F160W, respectively, which sample the restframe 1150 [˚] A, 1350 [˚] A, and 2300 [˚] A. No significant rest-frame UV counter part is detected
at the positions of the [C ii] emission.

Springer Nature 2021 L [A] TEX template


_[C_ ii _]-emitters_ _around_ _a_ _z_ _≈_ 5 _._ 7 _C_ iv _absorption_ _system_ 31


**Extended** **Data** **Table** **1** **Expected** **number** **counts** **of** **CO** **sources.** The frequency
is given in the rest-frame. The redshift and luminosity are calculated under the assumption
that the fainter line (A) detected in the ALMA data is each of the CO transition. The
expected number counts of unrelated CO sources at a line flux brighter or equal to the
observed flux are provided in the fourth column.


Transition frequency Redshift log _L_ CO _N_
(GHz) (Jy km s _[−]_ [1] Mpc [2] )


_J_ = 3–2 345.80 0.22 6.46 0.02

_J_ = 4–3 461.04 0.63 7.51 0.11

_J_ = 5–4 576.27 1.04 8.04 0.11

_J_ = 6–5 691.47 1.45 8.40 0.10

_J_ = 7–6 806.65 1.85 8.66 0.05

_J_ = 8–7 921.80 2.26 8.87 0.02


Total 0.40


**Extended** **Data** **Table** **2** **Absorption-line** **measurements.** The median and [16%,
84%] confidence intervals are given for each of the Voigt profile parameters. The second
and third columns present the column densities of C iv and Si iv. The fourth column is the
Dopper parameter _b_


Redshift log _N_ (C iv) [2] log _N_ (Si iv) [3] _b_ [4]

(cm _[−]_ [2] ) (cm _[−]_ [2] ) (km s _[−]_ [1] )


5.72457 [5.72455, 5.72460] [1] 14.55 [14.52, 14.63] 13.70 [13.68, 13.72] 40.6 [35.0, 42.6]
5.74106 [5.74102, 5.74110] 13.08 [12.68, 13.20] 13.26 [13.23, 13.29] 20.8 [7.0, 22.6]
5.74426 [5.74422, 5.74428] 13.81 [13.77, 13.85] 13.31 [13.28, 13.35] 23.0 [20.6, 30.6]


1 The median and [16%, 84%] confidence intervals are given for each of the Voigt profile
parameters.

2 The column density of C iv.

3 The column density of Si iv.

4 The Doppler parameter _b_ that is related to the kinetic temperature _T_ of the gas via _b_ =
~~�~~ 2 _kT/m_ p where _k_ is the Boltzmann constant and _m_ p is the proton mass.


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[0]",
  "value": "What are the properties and environment of galaxies associated with a complex high-ionization C IV absorption system at redshift z ≈ 5.7 toward QSO J1030+0524?",
  "failed_quote": "Here we report the detection of two [C ii]-emitting galaxies at redshift z ≈ 5 . 7 that are associated with a complex high-ionization C iv absorption system."
 },
 {
  "path": "data.pi_or_archival_as_stated.evidence[0]",
  "value": "PI observation (Daichi Kashino)",
  "failed_quote": "DK led the team, being principal investigator of the ALMA program, analyzed the ALMA and ancillary data"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Cross-checked against deep HST ~9000 Å images where low-z (z <= 2) stellar continuum would be detected, but is not.",
  "failed_quote": "Non-detection of both sources in available deep HST images at ∼ 9000 ˚ A (see below) also argues against any interpretation that places these sources at low redshift ( z ≲ 2)."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Single Gaussian profile fit to 1D extracted spectrum",
  "failed_quote": "By fitting a simple Gaussian profile, we estimate the FWHM line widths to be 64 ± 11 km s − 1 ([C ii]1030A) and 62 ± 11 km s − 1 (B)"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[1]",
  "value": "Low-redshift CO emission-line interlopers (CO(3-2) to CO(8-7) at z ≈ 0.22–2.3; rejected due to 1.5% probability and non-detection of stellar continuum in deep HST images).",
  "failed_quote": "Non-detection of both sources in available deep HST images at ∼ 9000 ˚ A (see below) also argues against any interpretation that places these sources at low redshift ( z ≲ 2)."
 }
]
```
