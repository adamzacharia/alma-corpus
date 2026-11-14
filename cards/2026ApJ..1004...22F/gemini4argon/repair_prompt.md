# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1004...22F\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version May 26, 2026
Typeset using L [A] TEX **twocolumn** style in AASTeX7.0.1


**The** **ALPINE-CRISTAL-JWST** **Survey:**
**The** **Fast** **Metal** **Enrichment** **of** **Massive** **Galaxies** **at** _z_ _∼_ 5


Andreas [L.](http://orcid.org/0000-0002-9382-9832) Faisst, [Lun-Jun](http://orcid.org/0009-0004-1270-2373) Liu, Yohan [Dubois](http://orcid.org/0000-0003-0225-6387), Yurina [Nakazato](http://orcid.org/0000-0002-0984-7713), Omima [Osman](http://orcid.org/0009-0001-5733-8307),
Andrea [Pallottini](http://orcid.org/0000-0002-7129-5761), Livia [Vallini](http://orcid.org/0000-0002-3258-3672), Seiji [Fujimoto](http://orcid.org/0000-0001-7201-5066), Bahram [Mobasher](http://orcid.org/0000-0001-5846-4404), Wuji [Wang](http://orcid.org/0000-0002-7964-6749), [Yu-Heng](http://orcid.org/0000-0001-8792-3091) Lin,
Ricardo [O.](http://orcid.org/0000-0001-5758-1000) Amor´ın, Manuel [Aravena](http://orcid.org/0000-0002-6290-3198), R. J. [Assef](http://orcid.org/0000-0002-9508-3667), Andrew J. Battisti, Matthieu [B´ethermin](http://orcid.org/0000-0002-3915-2015),
M´ed´eric [Boquien](http://orcid.org/0000-0003-0946-6176), Paolo [Cassata](http://orcid.org/0000-0002-6716-4400), Elisabete [da](http://orcid.org/0000-0001-9759-4797) Cunha, [Poulomi](http://orcid.org/0009-0007-7842-9930) Dam, Gabriella [de](http://orcid.org/0000-0002-6220-9104) Lucia,
Ilse De [Looze](http://orcid.org/0000-0001-9419-6355), Miroslava [Dessauges-Zavadsky](http://orcid.org/0000-0003-0348-2917), Andrea [Ferrara](http://orcid.org/0000-0002-9400-7312), Kyle [Finner](http://orcid.org/0000-0002-4462-0709), Fabio [Fontanot](http://orcid.org/0000-0003-4744-0188),
Michele [Ginolfi](http://orcid.org/0000-0002-9122-1700), Diego A. [G´omez-Espinoza](http://orcid.org/0009-0008-1835-7557), Carlotta [Gruppioni](http://orcid.org/0000-0002-5836-4056), Nicol [Guti´errez-Vera](http://orcid.org/0009-0005-8932-7783), Ali [Hadi](http://orcid.org/0009-0003-3097-6733),
Rodrigo [Herrera-Camus](http://orcid.org/0000-0002-2775-0595), Michaela [Hirschmann](http://orcid.org/0000-0002-3301-3321), [Eduardo](http://orcid.org/0009-0008-9801-2224) Ibar, Hanae [Inami](http://orcid.org/0000-0003-4268-0393),
Jeyhan S. [Kartaltepe](http://orcid.org/0000-0001-9187-3605), Anton M. [Koekemoer](http://orcid.org/0000-0002-6610-2048), Mahsa [Kohandel](http://orcid.org/0000-0003-1041-7865), Lilian [L.](http://orcid.org/0000-0001-7457-4371) Lee, Yuan Li,
Juan [Molina](http://orcid.org/0000-0002-8136-8127), Ambra [Nanni](http://orcid.org/0000-0001-6652-1069), Desika [Narayanan](http://orcid.org/0000-0002-7064-4309), [Francesca](http://orcid.org/0000-0002-7412-647X) Pozzi, Monica [Relano](http://orcid.org/0000-0003-1682-1148),
Michael [Romano](http://orcid.org/0000-0002-9948-3916), David B. [Sanders](http://orcid.org/0000-0002-1233-9998), John D. [Silverman](http://orcid.org/0000-0002-0000-6977), Laura [Sommovigo](http://orcid.org/0000-0002-2906-2200), Justin [Spilker](http://orcid.org/0000-0003-3256-5615),
Akiyoshi [Tsujita](http://orcid.org/0000-0002-0498-5041), Hannah [Ubler](http://orcid.org/0000-0003-4891-0794) [¨], Keerthi [Vasan](http://orcid.org/0000-0002-2645-679X) G.C., Enrico [Veraldi](http://orcid.org/0009-0007-1304-7771), Vincente [Villanueva](http://orcid.org/0000-0002-5877-379X),

Lizhi [Xie](http://orcid.org/0000-0003-3864-068X) And Gianni [Zamorani](http://orcid.org/0000-0002-2318-301X)


(Affiliations can be found after the references)


ABSTRACT


We present the stellar mass-metallicity relation (MZR) and mass-metallicity-star formation relation
(“fundamental metallicity relation”; FMR) of 18 massive (log(M _⋆_ _/_ M _⊙_ ) = 9 _._ 5 _−_ 11) main-sequence
galaxies at _z_ _∼_ 5 from the ALPINE-CRISTAL-JWST sample. This sample complements recent studies by JWST at up to two orders of magnitude lower stellar masses. The metallicities are derived
using strong optical lines, and verified by temperature-based oxygen abundance measurements for five
galaxies for which faint auroral lines are detected. We find that the metal abundance evolves, on
average, from 40% to 60% solar between _z_ _∼_ 5 and cosmic noon ( _z_ _∼_ 2) at the massive end of the
MZR, suggesting already significant metal enrichment at early times. The FMR at _z_ = 5 exhibits a
5 _×_ larger scatter (preferentially to lower metallicities) compared the local FMR relation. This scatter
can be explained by a bursty star formation and the direct build-up of metals in early galaxies as well
as differences in age and outflow efficiencies. Capitalizing on all available samples, we find that the
observed MZR and FMR over three orders of stellar mass is generally in good agreement with results
from cosmological simulation, although some underestimate the metal enrichment at low stellar masses.
This may be due to too efficient metal-rich outflows. We show that the ALPINE-CRISTAL-JWST
galaxies likely joined the current FMR at _z_ _∼_ 10 and will evolve into massive (log(M _⋆_ _/_ M _⊙_ ) _∼_ 11 _._ 4)
galaxies with super-solar metallicities by _z_ = 0.


_Keywords:_ Galaxy [Formation](http://astrothesaurus.org/uat/595) (595) — Galaxy [Evolution](http://astrothesaurus.org/uat/594) (594) — High-Redshift Galaxies (734) —

Metallicity (1031) — Galaxy Structure (622) — Surveys (1671)



1. INTRODUCTION


Metallicity, the relative abundance of heavy elements
to hydrogen, is a fundamental observable in studying the
evolution of galaxies (B. M. Tinsley 1980; B. E. J. Pagel
1997; R. Maiolino & F. Mannucci 2019). Its role, to constrain the mass assembly of galaxies and the feedback
process due to infall and outflow of gas, is widely used to


Corresponding author: Andreas L. Faisst



study the chemical enrichment of galaxies. The stellar
mass vs. metallicity relation (MZR) of galaxies observed
in the local universe shows the tight correlation of gasphase metallicity increasing with the stellar mass (C. A.
Tremonti et al. 2004; F. Mannucci et al. 2010; D. A.
Berg et al. 2012; B. H. Andrews & P. Martini 2013; S. F.
S´anchez et al. 2017; M. Curti et al. 2020). Advances in
near-infrared (near-IR) spectroscopy have allowed measurements of rest-frame optical line ratio diagnostics of
the metallicity of galaxies at higher redshifts. Using statistically large samples, independent studies have shown

2


that, in general, the metal abundance at a given stellar mass decreases with increasing redshift (R. Maiolino
et al. 2008; D. Kashino et al. 2017; R. Maiolino & F.
Mannucci 2019; R. L. Sanders et al. 2021; C. Papovich
et al. 2022; A. L. Strom et al. 2022). The MOSDEF
(M. Kriek et al. 2015) and KBSS (G. C. Rudie et al.
2012; C. C. Steidel et al. 2014) surveys performed extensive observations of the MZR to _z_ _∼_ 3, confirming
the evolution of this relation with look-back time (R. L.
Sanders et al. 2018; A. L. Strom et al. 2017). The evolution and scatter in the mass-metallicity relation with
redshift has strong implications towards the formation
and subsequent metal enrichment of galaxies and the
process of stellar evolution at earlier times.
Observations by the James Webb Space Telescope
(JWST) have now given access to rest-frame optical diagnostic lines at the reionization epoch ( _z_ _∼_ 5 _−_ 7),
allowing the observation of the MZR to the highest redshifts (K. Nakajima et al. 2023; M. Curti et al. 2024; A.
Marszewski et al. 2024; T. Morishita et al. 2024; L. E.
Rowland et al. 2025; A. Sarkar et al. 2025). This enables
the study of the metal enrichment process undergone by
pristine gas and the infall process in the inter-stellar
medium (ISM) of early galaxies.
A serious challenge for such studies was the lack
of reliable calibration for metallicity measurements at
high redshifts. Previous studies assumed local calibration with no significant evolution with cosmic time.
This assumption directly affect the reliability of the
mass-metallicity relation at _z_ _>_ 3. In a recent study,
R. L. Sanders et al. (2024) performed a calibration between rest-frame optical line ratios and metallicities in
the redshift range _z_ _∼_ 2 _−_ 9 using a method based
on the electron temperature ( _T_ _e_ ) measurement. This
technique utilizes optical emission line ratios involving
faint auroral lines, using transitions resulting from different upper energy levels (e.g., [O III ] 4363 /[O III ] 5007
or [O II ] 7322 _,_ 7332 /[O II ] 3727 ratios). The estimated _T_ _e_
can then be used to convert dust-corrected flux ratios
of ionic Oxygen lines to Hydrogen recombination lines
(e.g., [O III ]/H _β_ and [O II ]/H _β_ ) [1] into O/H abundance
ratios to construct metallicity calibration by fitting functional forms to the relation between different line ratios
and O/H (M. Pettini & B. E. J. Pagel 2004; T. Nagao
et al. 2006; R. Maiolino et al. 2008; M. Curti et al. 2020).
This calibration procedure needs measurement of various rest-frame optical lines – [O III ] 4363, [O III ], [O II ],
H _β_, [O II ] 7322 _,_ 7332 – of galaxies at high redshifts. Before JWST, it has therefore been difficult to implement


1 In the following, we define [O III ] _≡_ [O III ] 5007 and

[O II ] _≡_ [O II ] 3727+3730 .



this technique at high redshifts due to inaccessibility of
rest-frame optical lines and the faintness of such auroral
lines. Now, all of these lines are accessible up to _z_ _∼_ 6
simultaneously, hence allowing a consistent metallicity
measurement across the past 12 billion years.
Extending the dimensionality of the MZR by the star
formation rate (SFR) led to the recognition of the fundamental metallicity relation (FMR) at low redshifts (e.g.,
S. L. Ellison et al. 2008; F. Mannucci et al. 2010) which
was soon explained by (semi-) analytical models (e.g.,
R. Dav´e et al. 2012; P. Dayal et al. 2013; S. J. Lilly
et al. 2013; R. Feldmann 2015; G. De Lucia et al. 2020).
While this relation is now well established out to _z_ _∼_ 3
(e.g., E. P´erez-Montero et al. 2013; E. Wuyts et al. 2014;
K. Yabe et al. 2014; H. J. Zahid et al. 2014b,a; S. Salim
et al. 2015; R. L. Sanders et al. 2015; Y. Guo et al.
2016; M. Onodera et al. 2016; D. Kashino et al. 2017; F.
Cullen et al. 2019; R. L. Sanders et al. 2021; A. Henry
et al. 2021; M. W. Topping et al. 2021), although some
works suggest no evidence of an FMR at _z_ = 2 _−_ 3 (e.g.,
C. C. Steidel et al. 2014; N. A. Korhonen Cuestas et al.
2025), only recently with JWST has it been measured
at higher redshifts. These data, importantly only focusing on low-mass galaxies, suggest an evolution of the
FMR compared to the local relation (e.g., M. Curti et al.
2024; G. Roberts-Borsani et al. 2024; C. L. Pollock et al.
2026; D. Scholte et al. 2025; A. Sarkar et al. 2025; T. M.
Stanton et al. 2026).
Current JWST observations referenced above have derived the MZR at stellar masses of log(M _⋆_ _/_ M _⊙_ ) ≲ 9 _._ 5
at high redshifts. The relation (and its evolution) for
more massive galaxies in the early Universe are still unknown. This is mainly because such galaxies are rare
and not covered by deep pencil-beam surveys (for example a 5 _×_ 10 [10] M _⊙_ galaxy is ten times rarer than a
10 [9] M _⊙_ galaxy, M. Shuntov et al. 2025). Similarly, the
question of a possible evolution of the FMR across the
full mass range from 10 [7] _−_ 10 [11] M _⊙_ at high redshifts is
not answered. Tracing the MZR and FMR, thus the
metal enrichment, in massive galaxies is an important
tracer of galaxy growth and, in relation to lower stellar
masses, holds valuable information on the overall evolution of galaxies.
In this work, we present constraints on the MZR and
FMR at _z_ _∼_ 5 from galaxies of the ALPINE-CRISTALJWST survey (A. L. Faisst et al. 2026; S. Fujimoto et al.
2025). This survey provides JWST/NIRSpec IFU observations for a sample of 18 main-sequence galaxies at the
end of the epoch of reionization (EoR) at _z_ = 4 _−_ 6.
Notably, all galaxies also have ALMA observations of

[C II ] 158 _µ_ m and far-IR continuum at comparable resolution to JWST spectroscopy to jointly study the stars,

3



**Table** **1.** Summary of physical properties of the ALPINE-CRISTAL-JWST galaxy sample.


Name _z_ opt M _∗a_ SFR _[b]_ Age _[c]_ 12 + log(O _/_ H) _d_ T(O [+] ) T(O [++] ) _n_ _e_
(10 [9] M _⊙_ ) (M _⊙_ yr _[−]_ [1] ) (Myr) (strong line) ( _T_ _e_ –based) ( _×_ 10 [4] K) ( _×_ 10 [4] K) (cm _[−]_ [3] )
DC-417567 5.666 10 _._ 0 [+0] _−_ 0 _[.]_ _._ [3] 3 72 [+42] _−_ 27 105 [+100] _−_ 56 8 _._ 04 [+0] _−_ 0 _[.]_ _._ [02] 02 7 _._ 96 [+0] _−_ 0 _[.]_ _._ [28] 14 15 [+17] _−_ 4 16 [+2] _−_ 2 2268 [+2636] _−_ 912
DC-494763 5.233 9 _._ 5 [+0] _−_ 0 _[.]_ _._ [4] 4 28 [+36] _−_ 16 175 [+352] _−_ 119 8 _._ 29 [+0] _−_ 0 _[.]_ _._ [02] 02 – – 15 [+5] _−_ 3 –
DC-519281 5.575 9 _._ 8 [+0] _−_ 0 _[.]_ _._ [4] 4 32 [+35] _−_ 17 324 [+331] _−_ 194 7 _._ 99 [+0] _−_ 0 _[.]_ _._ [08] 08 – – – 637 [+1430] _−_ 321
DC-536534 5.689 10 _._ 4 [+0] _−_ 0 _[.]_ _._ [3] 3 62 [+64] _−_ 31 456 [+275] _−_ 224 8 _._ 10 [+0] _−_ 0 _[.]_ _._ [04] 05 – 14 [+6] _−_ 3 18 [+2] _−_ 3 –
DC-630594 4.440 9 _._ 7 [+0] _−_ 0 _[.]_ _._ [3] 3 37 [+39] _−_ 19 186 [+227] _−_ 88 8 _._ 40 [+0] _−_ 0 _[.]_ _._ [04] 04 7 _._ 99 [+0] _−_ 0 _[.]_ _._ [29] 19 17 [+8] _−_ 3 15 [+3] _−_ 3 185 [+246] _−_ 116
DC-683613 5.541 10 _._ 2 [+0] _−_ 0 _[.]_ _._ [3] 3 68 [+67] _−_ 34 274 [+271] _−_ 159 8 _._ 49 [+0] _−_ 0 _[.]_ _._ [03] 05 – 19 [+14] _−_ 4 – 547 [+411] _−_ 262
DC-709575 4.412 9 _._ 5 [+0] _−_ 0 _[.]_ _._ [4] 4 28 [+39] _−_ 16 190 [+302] _−_ 95 8 _._ 27 [+0] _−_ 0 _[.]_ _._ [02] 03 8 _._ 01 [+0] _−_ 0 _[.]_ _._ [34] 20 13 [+4] _−_ 3 18 [+3] _−_ 2 484 [+685] _−_ 238
DC-742174 5.636 9 _._ 5 [+0] _−_ 0 _[.]_ _._ [4] 4 15 [+16] _−_ 8 354 [+338] _−_ 215 7 _._ 84 [+0] _−_ 0 _[.]_ _._ [05] 05 – – – –
DC-842313 4.552 10 _._ 6 [+0] _−_ 0 _[.]_ _._ [5] 5 204 [+918] _−_ 167 394 [+250] _−_ 221 8 _._ 48 [+0] _−_ 0 _[.]_ _._ [03] 05 8 _._ 49 [+0] _−_ 0 _[.]_ _._ [37] 27 11 [+3] _−_ 2 13 [+9] _−_ 0 154 [+122] _−_ 87
DC-848185 5.294 10 _._ 3 [+0] _−_ 0 _[.]_ _._ [3] 3 178 [+290] _−_ 110 98 [+52] _−_ 48 8 _._ 28 [+0] _−_ 0 _[.]_ _._ [02] 03 8 _._ 06 [+0] _−_ 0 _[.]_ _._ [22] 22 15 [+3] _−_ 3 14 [+4] _−_ 2 388 [+153] _−_ 147
DC-873321 5.154 10 _._ 0 [+0] _−_ 0 _[.]_ _._ [3] 3 78 [+64] _−_ 35 112 [+84] _−_ 63 8 _._ 11 [+0] _−_ 0 _[.]_ _._ [06] 07 – 15 [+9] _−_ 3 – 613 [+307] _−_ 291
DC-873756 4.545 10 _._ 5 [+0] _−_ 0 _[.]_ _._ [1] 1 115 [+76] _−_ 46 550 [+317] _−_ 169 8 _._ 68 [+0] _−_ 0 _[.]_ _._ [58] 88 – – – –
VC-5100541407 4.563 10 _._ 1 [+0] _−_ 0 _[.]_ _._ [3] 3 42 [+50] _−_ 23 400 [+427] _−_ 239 8 _._ 21 [+0] _−_ 0 _[.]_ _._ [24] 40 – – – –
VC-5100822662 4.520 10 _._ 2 [+0] _−_ 0 _[.]_ _._ [3] 3 78 [+48] _−_ 30 237 [+196] _−_ 122 8 _._ 33 [+0] _−_ 0 _[.]_ _._ [04] 04 – – 15 [+4] _−_ 3 299 [+174] _−_ 194
VC-5100994794 4.580 9 _._ 6 [+0] _−_ 0 _[.]_ _._ [3] 3 32 [+51] _−_ 20 193 [+252] _−_ 95 8 _._ 41 [+0] _−_ 0 _[.]_ _._ [04] 05 – 15 [+6] _−_ 3 – 1153 [+289] _−_ 411
VC-5101218326 4.573 10 _._ 9 [+0] _−_ 0 _[.]_ _._ [3] 3 562 [+534] _−_ 274 646 [+97] _−_ 275 8 _._ 36 [+0] _−_ 0 _[.]_ _._ [34] 30 – – – –
VC-5101244930 4.581 9 _._ 7 [+0] _−_ 0 _[.]_ _._ [3] 3 28 [+20] _−_ 12 183 [+365] _−_ 88 8 _._ 24 [+0] _−_ 0 _[.]_ _._ [10] 13 – 17 [+15] _−_ 4 – –
VC-5110377875 4.550 10 _._ 2 [+0] _−_ 0 _[.]_ _._ [2] 2 99 [+75] _−_ 43 161 [+127] _−_ 108 8 _._ 41 [+0] _−_ 0 _[.]_ _._ [08] 09 – 13 [+13] _−_ 3 – 924 [+767] _−_ 525


Note— _[a]_ Stellar masses are derived in I. Mitsuhashi et al. (2024).
_b_ SFRs represent the total UV+FIR luminosities derived in A. L. Faisst et al. (2026).
_c_ Ages (light-weighted) are derived in A. L. Faisst et al. (2020).
_d_ Metal abundance uncertainties include uncertainties from calibrations and line flux measurements, derived from extensive
Monte-Carlo samplings. However, uncertainties due the dust attenuation corrections are not included.



gas, and dust at this epoch. The galaxies are massive
at log(M _⋆_ _/_ M _⊙_ ) _>_ 9 _._ 5, thus complement the samples at
lower stellar masses observed by other JWST surveys.
We investigate their scatter on the MZR and their location on the FMR in relation to theoretical models to

characterize the fast build-up of metals at these early

times.

This paper is organized as follows: In Section 2, we
describe the sample and outline the measurement of the
metal abundances (with more details in Appendix A).
In Section 3, we present the observed MZR and FMR at
_z_ _∼_ 5, which we then study in the light of a simple analytical model and cosmological simulations in Section 4.
Throughout this work, we assume a ΛCDM cosmology
with _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1], Ω Λ = 0 _._ 7, and Ω m = 0 _._ 3
and magnitudes are given in the AB system (J. B. Oke
1974). We use a Chabrier initial mass function (IMF; G.
Chabrier 2003) calibration for stellar masses and SFRs.


2. DATA & MEASUREMENTS


2.1. _The_ _ALPINE-CRISTAL-JWST_ _Sample_


This work is based on the 18 of the ALPINE
CRISTAL-JWST survey. The survey, including science
goals and basic measurements, is described in its entirety



in A. L. Faisst et al. (2026). The JWST/NIRSpec IFU
data reduction and spatially resolved metallicity measurements are described in S. Fujimoto et al. (2025).
Here, we give a brief overview of the sample and the

survey.
The ALPINE-CRISTAL-JWST survey targeted 18
main-sequence galaxies at 4 _._ 4 _<_ _z_ _<_ 5 _._ 9 ( _⟨z⟩∼_ 5) from
the ALMA-ALPINE program ([C II ] 158 _µ_ m and 158 _µ_ m
dust continuum observations at 0 _._ 7 _[′′]_ spatial resolution;
O. Le F`evre et al. 2020; M. B´ethermin et al. 2020;
A. L. Faisst et al. 2020) at log(M _⋆_ _/_ M _⊙_ ) _∼_ 9 _._ 5 _−_ 11 _._ 0
and SFR _∼_ 10 _−_ 700 M _⊙_ yr _[−]_ [1] with rest-frame optical JWST/NIRSpec IFU observations (#3045; PI:
Faisst) at 0 _._ 15 _[′′]_ spatial resolution in G235M/F170LP
and G395M/F290LP ( _R_ _∼_ 1000). As part of the selection process, all galaxies have HST rest-frame ultraviolet (UV) imaging, JWST/NIRCam rest-frame optical
imaging (COSMOS-Web program; C. M. Casey et al.
2022), and additional higher resolution ALMA observations of the [C II ] 158 _µ_ m line and the 158 _µ_ m dust
continuum at 0 _._ 3 _[′′]_ spatial resolution from the ALMACRISTAL survey (R. Herrera-Camus et al. 2025). All
galaxies reside in the COSMOS field (N. Scoville et al.

4


2007; A. M. Koekemoer et al. 2007), which provides a
wealth of ancillary data.
Although none of our targets can be unambiguosly
defined as AGN based on the BTP diagram (J. A.
Baldwin et al. 1981), one of them ( _DC-873756_ ) shows
strong [N II ] emission, making it a potential BPT candidate AGN. In addition, other six targets ( _DC-417567_,
_DC-519281_, _DC-536534_, _DC-683613_, _DC-848185_, and
_DC-873321_ ) are potential type 1 AGN due to broad
( _>_ 500 km _/_ s) H _α_ emission (W. Ren et al. 2025).
Some physical parameters are summarized in Table 1
(more can be found in A. L. Faisst et al. 2026). The
stellar masses adopted in this work are derived in I. Mitsuhashi et al. (2024) using the `CIGALE` code (M. Boquien
et al. 2019; D. Burgarella et al. 2005). The SFRs are derived from the total UV+far-IR emission (A. L. Faisst
et al. 2026). The galaxy ages (light weighted) are taken
from A. L. Faisst et al. (2020) and are derived using
`LePhare` (S. Arnouts et al. 1999; O. Ilbert et al. 2006).
Four galaxies are not far-IR detected and we use the
SED-fitting results from I. Mitsuhashi et al. (2024) to
measure their SFR. H _α_ -based SFRs extinction-corrected

with Balmer decrement are derived using the J. Kennicutt (1998) relation (converted to a G. Chabrier (2003)
IMF).
The ALPINE-CRISTAL-JWST survey provides the
best-studied _z_ _∼_ 5 main-sequence galaxy sample at
log(M _/_ M _⊙_ ) = 9 _._ 5 _−_ 11 _._ 0 at 1 _−_ 2 kpc resolution to date.
It is a benchmark in the study of galaxy evolution in
the post-EoR era — the connection between primordial
galaxy formation in the EoR and mature galaxy evolu
tion at cosmic noon.


2.2. _Metallicity_ _Measurement_


From the new JWST/NIRSpec spectroscopy, we measured spatially integrated oxygen abundances (“metallicity”, defined as _Z_ _≡_ 12+log(O _/_ H)) of the 18 galaxies
using strong optical emission lines with applied _T_ _e_ calibration from R. L. Sanders et al. (2024). These strong
lines are detected for all individual galaxies. The metallicity measurements are detailed in A. L. Faisst et al.
(2026) and summarized in Table 1 and in the following
we give an overview. In Appendix A, we additionally
compare different strong-line metallicity calibrators as
well as compare these measurement to direct metallicity
measurements from fainter auroral lines for a subsample
of five galaxies.
The measurement of the strong-line metallicities is
based on the dust-corrected optical lines fluxes of [O II ],
H _β_, and [O III ] to derive oxygen abundances (see review on metallicity measurements in L. J. Kewley et al.
2019). All emission lines are extracted from the spec


tral cubes in a mask defined by the region of the 3 _σ_
JWST/NIRCam rest-frame optical continuum flux ( _i.e._
tracing the stellar mass). But note the results do not
depend significantly on the exact spatial outline. We do
not use H _α_ and [N II ] in the case of contamination by
an AGN (W. Ren et al. 2025) and the blending of the
two lines in the medium resolution spectra. Dust correction was applied via the Balmer decrement (H _α_ /H _β_ )
assuming case B recombination. Due to the coverage
with both the G235M and G395M grating, the same
lines could be used for all galaxies in the sample. We
use the metallicity parameterization and calibration by
R. L. Sanders et al. (2024), which we found to lead to
consistent metallicities as the parameterization by R.
Maiolino et al. (2008) and M. Hirschmann et al. (2023)
(Figure A.1, Appendix A).
The strong-line metallicity measurements were also
compared to direct _T_ _e_ -based measurements derived from
fainter auroral lines ([O III ] 4363 and [O III ] 7322 _,_ 7332 ) for
a subset of five galaxies. For these galaxies, we find
consistent metallicity measurement from the strong-line
method an the _T_ _e_ method (see Appendix A for details).
As mentioned previously, six of the ALPINECRISTAL-JWST galaxies are potential type 1 AGN
candidates. However, as they do not seem to exhibit
unusual line ratios typical for BPT AGN, we do not
think that their possible AGN activity has a significant
effect on the metallicity measurement.


3. THE MASS- _Z_ -SFR RELATION OF MASSIVE

MAIN-SEQUENCE GALAXIES AT _Z_ _∼_ 5


The build-up of metals directly relates to the buildup of stellar mass over the lifetime of galaxies. However, second-order deviations from such a relation provide important insights into changes of metal production due to different processes such as star formation
efficiency, outflows, inflows, and other physical events
(e.g., supernovae or changes in the IMF). With JWST,
it has now become possible to constrain the metal content of galaxies close to the EoR at _z_ = 6. So far,
JWST provided such measurements for low-mass systems, generally well below log(M _⋆_ _/_ M _⊙_ ) = 9 _._ 5. The
ALPINE-CRISTAL-JWST survey provides a sample of
more massive _z_ _∼_ 5 galaxies that complements these
other measurements and extends the relation between

stellar mass, SFR, and metallicity to the massive end to
log(M _⋆_ _/_ M _⊙_ ) = 11 at _z_ _∼_ 5.


3.1. _The_ _Mass-Metallicity_ _Relation_ _(MZR)_


Figure 1 shows the resulting MZR for the ALPINECRISTAL-JWST sample (large circles and type 1 AGN
candidates indicated in gray) as well as a comparison to

5



z
2.5 3 4 5 6 78



100%


80%


60%


40%


30%







8.8


8.6


8.4


8.2



9.0


8.5


8.0


7.5


7.0













8.0













3.0 2.5 2.0 1.5 1.0 0 ~~.~~ 5

t univ [Gyr]



**Figure** **1.** _Left_ _and_ _Middle:_ Comparison of the MZR of the ALPINE-CRISTAL-JWST sample (open large circles; type 1
broad-line AGN candidates from W. Ren et al. (2025) are indicated in gray) to samples at _z_ _<_ 4 ( _left_ ) and _z_ _>_ 4 (right) from
the literature (C. C. Steidel et al. 2014; R. L. Sanders et al. 2015; K. Nakajima et al. 2023; T. Morishita et al. 2024; M. Curti
et al. 2023; J. Scholtz et al. 2025; R. L. Sanders et al. 2024; T. M. Stanton et al. 2024; R. L. Sanders et al. 2025; A. Sarkar
et al. 2025; L. E. Rowland et al. 2025; T. M. Stanton et al. 2026). The relations from R. Maiolino et al. (2008) are indicated
as lines as indicated in the legend. Metal abundances in percent of solar are shown as horizontal dashed lines. The best fit to
the _z_ = 4 _−_ 6 samples is indicated as dashed line ( _middle_ panel) with parameters listed in Table 2. _Right:_ Metal abundance
evolution from cosmic noon to cosmic dawn at the fixed stellar mass range of the ALPINE-CRISTAL-JWST sample. Faint
symbols with dashed errorbars (at _z_ _>_ 4) are derived by extrapolating the MZR to the ALPINE-CRISTAL-JWST stellar mass

range.



the MZR at lower redshifts. The measured abundances
of our sample range from 7 _._ 7 _−_ 8 _._ 5 in 12+log(O _/_ H), corresponding to 10 _−_ 70% of solar metallicity [2] . The left
panel of Figure 1 show the comparison of the ALPINECRISTAL-JWST sample to samples at _z_ = 2 _−_ 4 from
various literature (R. Maiolino et al. 2008; C. C. Steidel et al. 2014; R. L. Sanders et al. 2015; T. Morishita
et al. 2024; K. Nakajima et al. 2023; M. Curti et al. 2023;
J. Scholtz et al. 2025; R. L. Sanders et al. 2024, 2025;
T. M. Stanton et al. 2024, 2026). The middle panel
shows the comparison to similar and higher redshifts
(out to _z_ _∼_ 10) from similar literature and additionally
including A. Sarkar et al. (2025) and the REBELS-IFU
survey (L. E. Rowland et al. 2025). These measurements
use calibrations consistent with our work and we there
fore do not expect significant systematics. A comparison
to cosmological simulations and analytical models is be
discussed in Section 4.4.

The ALPINE-CRISTAL-JWST galaxies lie at the
high-mass end of the distribution of JWST-measured
metal abundances, thus ideally complementing existing
JWST studies at lower masses. Their metal abundances

compare reasonably well in extrapolation with the abundances of these lower-mass galaxies; they are generally


2 We assume here a solar value of 12 + log(O _/_ H) = 8 _._ 69 (C.
Allende Prieto et al. 2001), however, note that this value could
be higher (M. Bergemann et al. 2021).



about 0 _._ 5 dex more metal enriched compared to galaxies at log(M _⋆_ _/_ M _⊙_ ) _<_ 9. In the right panel of Figure 1
we show the evolution of metal abundance as a function of time (or redshift) at a _fixed_ stellar mass comparable to the ALPINE-CRISTAL-JWST sample. We
note that only samples at _z_ _<_ 4 cover a similar stellar
mass range. For the comparison to literature samples
at _z_ _>_ 4, we extrapolated their metal abundances to
the stellar mass of the ALPINE-CRISTAL-JWST sample assuming a power-law fit (these measurements are
distinguished by dashed error bars). From this panel we
see that the metal abundances at a fixed stellar mass
increased on average from 40% to 60% of solar from
_z_ = 5 to cosmic noon (about a 50% increase over two
billion years). In the previous only 500 million years
(from _z_ _∼_ 8 to _z_ = 5), a similar increase in metals at
fixed stellar mass is observed, indicating a fast metal
enrichment at earlier times. The fast metal enrichment

at early cosmic times is further discussed in Section 4.
The thick black dashed line in the middle panel
of Figure 1 shows a fit using the `scipy.optimize`
_Python_ package to all available data at _z_ = 4 _−_ 6
and log(M _⋆_ _/_ M _⊙_ ) = 7 _._ 5 _−_ 11 _._ 0 including the ALPINECRISTAL-JWST sample: [3]


12+log(O _/_ H) = _B_ (log( _M_ _⋆_ _/_ M _⊙_ ) _−_ log( _M_ 0 )) [2] + _A,_ (1)


3 We adopt here a common functional form as in R. Maiolino
et al. (2008).

6


**Table** **2.** Fit to mass–metallicity relation (MZR; Figure 1)
using all current data at _z_ = 4 _−_ 6. Functional form:
12 + log(O _/_ H) = _B_ (log(M _∗_ _/_ M _⊙_ ) _−_ log( _M_ 0 )) [2] + _A_


log( _M_ 0 ) A B

15 _._ 25 _±_ 7 _._ 41 8 _._ 82 _±_ 0 _._ 97 _−_ 0 _._ 02 _±_ 0 _._ 02


Note—Data included from: This work
(ALPINE-CRISTAL-JWST; A. L. Faisst et al. 2026); C. C.
Steidel et al. (2014); R. L. Sanders et al. (2015); K.
Nakajima et al. (2023); T. Morishita et al. (2024); M. Curti
et al. (2023); J. Scholtz et al. (2025); R. L. Sanders et al.

(2024); T. M. Stanton et al. (2024); R. L. Sanders et al.
(2025); A. Sarkar et al. (2025); L. E. Rowland et al. (2025);

T. M. Stanton et al. (2026)


with best-fit parameters given in Table 2.


3.2. _The_ _Fundamental_ _Metallicity_ _Relation_ _(FMR)_


In addition to the MZR it is known that galaxies also
follow a similar relation between stellar mass, metallicity, and SFR (the so-called “fundamental metallicity
relation” or FMR, e.g., S. L. Ellison et al. 2008; M. A.
Lara-L´opez et al. 2010; F. Mannucci et al. 2010; B. H.
Andrews & P. Martini 2013; M. Curti et al. 2020). This
fundamental relation, specifically the anti-correlation
between metallicity and SFR, has also been identified in
analytical models and numerical simulations (R. Dav´e
et al. 2012; P. Dayal et al. 2013; S. J. Lilly et al. 2013;
R. Feldmann 2015; G. De Lucia et al. 2020). They
support the idea of reducing the metal abundances in
the ISM due to the infall of pristine/metal-poor gas,
which is related to an increased star formation. This

three-dimensional relation has been well studied out to
_z_ = 2 _−_ 3 (e.g., C. C. Steidel et al. 2014; E. Wuyts et al.
2014; K. Yabe et al. 2014; H. J. Zahid et al. 2014b,a; S.
Salim et al. 2015; R. L. Sanders et al. 2015; Y. Guo et al.
2016; M. Onodera et al. 2016; D. Kashino et al. 2017; F.
Cullen et al. 2019; R. L. Sanders et al. 2021; A. Henry
et al. 2021; M. W. Topping et al. 2021; N. A. Korhonen
Cuestas et al. 2025), however, no comprehensive studies
at higher redshifts covering the full mass range of galaxies have been undertaken (see recent compilation in C. L.
Pollock et al. 2026; T. M. Stanton et al. 2026). Here we
combine the massive ALPINE-CRISTAL-JWST sample
with measurements at lower masses from the literature

to test for the first time the universality of a FMR at

_z_ _∼_ 5.

The left panel in Figure 2 shows that the _z_ _∼_ 5 data
does roughly follow the expectations of an FMR, however with some scatter (discussed in Section 4.2). Specifically, this figure shows our new measurements from the
ALPINE-CRISTAL-JWST sample at _z_ _∼_ 5 together
with data points from SDSS at _z_ _∼_ 0 (K. N. Abazajian



et al. 2009; S. Alam et al. 2015) and FMOS at _z_ _∼_ 1 _._ 6
(J. D. Silverman et al. 2015; D. Kashino et al. 2017).
The lines show the common _equilibrium_ gas-regulator
(“bathtub”) models from S. J. Lilly et al. (2013) (see also
C. Maier et al. 2014; A. Dekel & N. Mandelker 2014; R.
Feldmann 2015; M. Onodera et al. 2016) calibrated by
D. Kashino et al. (2017) to the _z_ = 0 data from SDSS.
In this model, the equilibrium metallicity depends on
stellar mass and SFR as follows:


_Z_ eq = _Z_ in +

_y_


_,_

1 + _λ_ (1 _−_ _R_ ) _[−]_ [1] + _ϵ_ _[−]_ out [1] �(1 + _β −_ _b_ ) _×_ [SFR] _M_ _⋆_ _[−]_ [0] _[.]_ [15] �

(2)


where _Z_ in is the metallicity of the inflowing gas, _y_ is
the metal yield [4], _R_ is the fraction of mass returned to

_a_

the ISM, _λ_ = _λ_ 0 _×_ � 10 [10] _M_ _⋆_ M _⊙_ � is the mass-loading fac


tor, _ϵ_ out = _ϵ_ out _,_ 0 _×_ � 10 [10] _M_ _⋆_ M _⊙_



_b_
is the star formation ef�



ficiency (e.g., 1 _/_ Gyr), and _β_ = _−_ 0 _._ 25 is the slope of
the relation between stellar mass and specific SFR. For
consistency, we assume here the same values as in D.
Kashino et al. (2013); _Z_ in = 0, log( _y_ ) = 9 _._ 09, _R_ = 0 _._ 27,
( _λ_ 0 _, a_ ) = (0 _._ 38 _, −_ 0 _._ 61), and ( _ϵ_ out _,_ 0 _, b_ ) = (0 _._ 53 _,_ 0 _._ 48). For
the derivation of the subtraction _−_ 0 _._ 15, see equation 40
in S. J. Lilly et al. (2013). Both our analytical model and
data points are color-coded by stellar mass in the same
color scale. The colors of the ALPINE-CRISTAL-JWST
galaxies and the equilibrium model curves (notably calibrated to the _z_ = 0 sample) agree well, suggesting that
galaxies at _z_ _∼_ 5 follow a similar FMR as local galaxies,
however with a larger scatter as discussed in Section 4.2.
The right panel in Figure 2 visualizes the above in
more detail by showing an angled slice through the FMR
by defining _µ ≡_ log(M _⋆_ ) _−µ_ 0 _×_ log(SFR) where _µ_ 0 = 0 _._ 66
based on a fit to galaxies at _z_ = 0 (B. H. Andrews
& P. Martini 2013). The fundamentality in the FMR
comes from the fact that _µ_ 0 minimizes the scatter of
the FMR with respect to the MZR ( _i.e._ _µ_ 0 = 0). The
ALPINE-CRISTAL-JWST galaxies are shown as large
symbols together with literature data in two redshift
bins at _z_ = 4 _−_ 6 and _z_ _>_ 6 (K. Nakajima et al. 2023;
M. Curti et al. 2024; T. Morishita et al. 2024; A. Sarkar
et al. 2025; K. E. Heintz et al. 2025; L. E. Rowland
et al. 2025). Note that we find a tentative trend of
type 1 AGN candidate host galaxies to show a lower


4 Here, the yield is non-dimensional and defined as the mass of
metals returned to the ISM per unit mass that is locked up in
long-lived stars, _i.e._ (1 _−_ _R_ ) times the mass of stars formed;
see S. J. Lilly et al. (2013).

7



9.2


9.0


8.8


8.6


8.4


8.2


8.0


7.8



log(M/M )


9.0 9.5 10.0 10.5 11.0


~~z = 0 (SDSS)~~


z = 1.6 (FMOS)


~~z = 5~~ ~~(ALPINE)~~


1 0 1 2 3


log(SFR / [M yr 1 ])



ALPINE (z 5)


AGN Candidates
(Ren et al. 2025)


**1** **mean**

**(z** **=** **4** **6)**


A. &. M (2013)
Curti+ (2020)


z = 0 (A. & M. 2013)
z = 4 6 (Various)
z > 6 (Various)
z = 6.5 7.5 (REBELS)


7 8 9 10


= log(M/M ) 0.66 × log(SFR/[M yr 1 ])



9.0


8.5


8.0


7.5


7.0



**Figure** **2.** The stellar mass, metallicity, and SFR relation (“fundamental metallicity relation”, FMR). _Left:_ Data are shown
at _z_ = 0 from SDSS (small circles), at _z_ _∼_ 2 from the FMOS survey (large squares; J. D. Silverman et al. 2015; D. Kashino
et al. 2017), and from the ALPINE-CRISTAL-JWST survey at _z_ _∼_ 5 (large circles; this work). The data are compared to
an equilibrium gas-regulator model (see Equation 2) from S. J. Lilly et al. (2013) (see also C. Maier et al. 2014; M. Onodera
et al. 2016), calibrated by D. Kashino et al. (2017) to the SDSS _z_ = 0 measurements (colored lines). The symbols and lines are
color-coded by stellar mass on the same scale. _Right:_ The collapsed FMR assuming _µ_ 0 = 0 _._ 66 (B. H. Andrews & P. Martini
2013). The ALPINE-CRISTAL-JWST sample at _z_ _∼_ 5 is shown as large circles (type 1 AGN candidates from W. Ren et al.
2025 indicated in gray). Other literature data are shown at _z_ = 4 _−_ 6 and _z_ _>_ 6 (K. Nakajima et al. 2023; M. Curti et al. 2024;
T. Morishita et al. 2024; A. Sarkar et al. 2025; K. E. Heintz et al. 2025) as well as from the REBELS-IFU survey (L. E. Rowland
et al. 2025). The small blue points are data at _z_ = 0 (B. H. Andrews & P. Martini 2013) with the corresponding fit shown as
dashed gray line. The dot-dashed gray line shows the _z_ = 0 parameterization by M. Curti et al. (2020). The gray band shows
the 1 _σ_ percentiles of the literature and ALPINE-CRISTAL-JWST data at _z_ = 4 _−_ 6.



metallicity, however this claim needs to be confirmed
with larger samples.
Of interest is the comparison to the local FMR parameterized as 12 + log(O _/_ H) = 0 _._ 43 _µ_ + 4 _._ 56 by B. H.
Andrews & P. Martini (2013) (dashed line, right panel
of Figure 2). To first order galaxies at _z_ = 4 _−_ 6 follow
this local relation well but to second order the data suggest a scatter and offset towards lower metallicity at a
given _µ_ . This indicates an evolving FMR compared to
_z_ = 0. Although in broad agreement, we note that the
recent study by M. Curti et al. (2024) finds a larger offset and scatter, hence a stronger evolution of the FMR.
This is due to a different calibration of the local FMR
— indeed, the evolution is stronger if the local parameterization by M. Curti et al. (2020) (dot-dashed line) [5]

is used. However, the result at high stellar masses (also
showing a downward scatter in the FMR) is independent
on the assumption of the _z_ = 0 FMR relation.
Finally, the downward scatter relative to the _z_ = 0
FMR relation suggests a negative offset in the FMR to

5 Note that M. Curti et al. (2020) derives a _µ_ 0 = 0 _._ 65 for the
high sSFR SDSS sample, which is in agreement with the value
adopted here (0 _._ 66) derived by B. H. Andrews & P. Martini
(2013). For consistency, we use 0 _._ 66 in this work.



wards the early universe. A similar trend was also found
by other literature (M. Curti et al. 2024; T. M. Stanton
et al. 2026; C. L. Pollock et al. 2026). However, we point
out that the data also suggest an asymmetric scatter to
the mean FMR relation at _z_ = 5, which is further discussed in Section 4.3.


4. DISCUSSION


In the previous section, we have reported on the MZR
(Figure 1) as well as the FMR (Figure 2) at _z_ _∼_ 5 for
massive galaxies in the ALPINE-CRISTAL-JWST sample. The data show that there is only a slight evolution
in the metal abundance from the EoR to cosmic noon at
a given stellar mass (Figure 1) and in addition galaxies
at _z_ _∼_ 5 lie to first order on a similar FMR as galaxies
at _z_ = 0 and _z_ _∼_ 1 _._ 6 (Figure 2). This indicates a fast
build-up of metals at early times and subsequent steady
main-sequence enrichment to the local universe. However, to second order there are differences to the average low-redshift galaxy population: there is a significant
scatter (and offset) in the MZR and FMR specifically towards low metallicities at a given stellar mass compared
to the local relations. In the following, we investigate the
MZR and FMR scatter and compare the observations to
a simple analytical model and cosmological simulations.

8



10 [2]

10 [0]

10 2

10 4

10 6


10 [11]

10 [9]

10 [7]

10 [5]

10 [3]

10 [1]





_M_ _⋆_ ( _t_ ) = _M_ _⋆_ ( _t −_ ∆ _t_ ) + _M_ [˙] _⋆_ ( _t_ ) ∆ _t,_

SFR( _t_ ) _≡_ _M_ [˙] _⋆_ ( _t_ ) = _[M]_ [g][as] [(] _[t]_ [)]

_⟨t_ depl _⟩_ _[,]_


_M_ gas ( _t_ ) = _M_ gas ( _t −_ ∆ _t_ ) + _M_ ˙ gas _,_ in ∆ _t,_
� �



(3)



|Col1|Col2|Col3|Col4|SN|Col6|eII|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||AGB|AGB||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||C|N<br>O|N<br>O||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|0|50||10|0<br>t [|15<br> M|0<br> yrs|200<br>250<br> ]|200<br>250<br> ]|200<br>250<br> ]|200<br>250<br> ]|200<br>250<br> ]|


**Figure** **3.** Illustration of the metal build-up from our simple
analytical model. We assume a starburst forming 5 _×_ 10 [9] M _⊙_
within 100 Myr at a rate of 50 M _⊙_ yr _[−]_ [1] (hatched area). _Top:_
Instantaneous metal ejection rate ( _M_ [˙] ej _,_ Z ) over time from
type II SNe and AGB stars for carbon (dashed), nitrogen
(dotted), oxygen (solid), and their sum (thick solid). _Bot-_
_tom:_ Cumulative ejected metal mass over time.


4.1. _The_ _Fast_ _Build-up_ _of_ _Metals_ _in_ _the_ _View_ _of_ _a_
_Simple_ _Analytical_ _Model_


We start by implementing a simple analytical model,
whose details can be reviewed in R. Feldmann (2015)
as well as the related papers (S. J. Lilly et al. 2013;
H. J. Zahid et al. 2014a; R. Dav´e et al. 2012). In brief,
galaxies are treated as semi-closed boxes allowing the
inflow and outflow of gas, thereby following simple continuity equations. The star formation is regulated by
a star formation efficiency (or depletion time), and the
metal and dust evolution is coupled to star formation by
empirical yields and modified by the inflow and outflow
(e.g., through feedback from stellar winds and Supernovae) of gas. Thus the evolution of a galaxy through
cosmic time is overall described by a given gas accretion
rate ( _M_ [˙] gas _,_ in ), the metallicity of the infalling gas (given
by _r_ Z ), outflow rate (mass-loading factor,the per-cent fraction to the ISM metal-to-gas _ϵ_ out _≡_ _M_ SFR˙ out [), and] ratio;

star formation efficiency (SFE) or gas depletion time
( _t_ depl _∝_ SFE _[−]_ [1] ). Note that these parameters may be
dependent on time, stellar mass, and star formation.
For our simple demonstration purpose (and to minimize
the number of variables) we treat the accretion rate and
depletion time as time-independent constant factors as
there are no observational indications of a strong evolution at early cosmic times (e.g., N. Scoville et al. 2023).
However, the mass-loading factor _ϵ_ out, which controls
the slope of the mass-metallicity relation, is dependent
on stellar mass and redshift as discussed below.

We derive the stellar mass, SFR, gas and dust mass
empirically by running the model forward in time,
thereby computing these parameters in every time step



_M_ Z ( _t_ ) = _M_ Z ( _t −_ ∆ _t_ ) + _M_ [˙] Z ( _t_ ) ∆ _t._


The core of this calculation is the computation of the
total metal mass ( _M_ Z ) via the effective metal enrichment
of the ISM, which can be written as



where _M_ ˙ ej _,_ Z is the total metal ejection rate, _R_ = 0 _._ 46
(M. R. Krumholz & A. Dekel 2012; R. Feldmann 2015),
and _ζ_ _≡_ _MM_ gasZ (( _tt_ )) [is] [the] [metal-to-gas] [mass] [ratio] [of] [the]
ISM. In other words, the metal production rate is altered by the lock-up of metals in the stars, the outflow of metal-rich gas, and the inflow of gas (which may
be metal enriched or metal poor). The oxygen abundance metallicity is then computed as 12 + log(O _/_ H) =
8 _._ 69 + log( _ζ /_ 0 _._ 014) (C. Allende Prieto et al. 2001; R.
Feldmann 2015) using the calibration _Z_ _⊙_ _∼_ 0 _._ 014 (M.
Asplund et al. 2009).
For deriving the mass-loading factor (which is dependent on stellar mass and redshift), we use the results
from the EAGLE cosmological simulation (J. Schaye
et al. 2015; R. A. Crain et al. 2015), specifically from
the work by P. D. Mitchell et al. (2020, figure 3), which
we parameterized analytically by a double power-law as
described in Appendix B. This parameterization is consistent with the one by A. L. Muratov et al. (2015) based
on the FIRE simulation (P. F. Hopkins et al. 2014).
While previous studies have assumed a constant yield
for the production of metals, we adopt here more realistic metallicity ejection rates into the ISM. Specifically, we used the mass-dependent metal yields computed for Asymptotic Giant Branch (AGB) stars and
type II Supernovae (SNe) from F. Dell’Agli et al. (2019)
and M. Limongi & A. Chieffi (2018), respectively, to
obtain the mass ejection rates ( _M_ [˙] ej _,_ Z ) into the ISM for
carbon, nitrogen, and oxygen as a function of time for
a given star formation history (SFH) and IMF [6] . We include stars in the range of 1 _−_ 7 M _⊙_ for AGB yields
and 7 _−_ 120 M _⊙_ for SNe II yields [7] and use their mass

6 In the end, we assume to sum of these elements to contribute
to metallicity.
7 Note that cores of stars more massive than 40 M _⊙_ may collapse to form black holes resulting in less metal output into



˙ ˙ ˙
_M_ Z ( _t_ ) = _M_ ej _,_ Z ( _t_ ) _−_ _ζ_ (1 _−_ _R_ ) _M_ _⋆_ ( _t_ )

(4)
_−_ _ζ ϵ_ out ( _M_ _⋆_ _, t_ ) _M_ [˙] _⋆_ ( _t_ ) + _r_ Z _ζ_ _M_ [˙] gas _,_ in _,_

|90 Model<br>. ALPINE(z 5)<br>88 Literature (z = 4 6)<br>.<br>86 2+log(O/H)<br>.<br>84<br>.<br>82<br>.|Col2|Col3|Col4|
|---|---|---|---|
|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|||
|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|5)<br> (z = 4<br>6)||
|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|~~8~~.~~2~~<br>8.4<br>8.6<br>8.8<br>9.0<br>2 + log(O/H)<br>Model<br>ALPINE (z<br>5)<br>Literature (z = 4<br>6)|<br>||
|1|~~8.~~0<br>8~~.~~5<br><br>7~~.6~~<br>~~7~~.~~8~~<br>8.0<br>|~~8.~~0<br>8~~.~~5<br><br>7~~.6~~<br>~~7~~.~~8~~<br>8.0<br>|~~8.~~0<br>8~~.~~5<br><br>7~~.6~~<br>~~7~~.~~8~~<br>8.0<br>|


**Figure** **4.** The MZR reproduced by our analytical model
at _z_ _∼_ 5 (see Section 4.1 for details). Model galaxies are color-coded by their age. ALPINE-CRISTAL-JWST galaxies
are shown as large symbols with same color code and other
literature data are shown as gray squares (see also Figure 1).
Our model captures well the range of observations and visualizes the fast metal enrichment. The upper envelope of the
MZR is set by maximally old model galaxies (red). The observed galaxy ages correlate well with the model ages. The
three gray swaths show model track ranges for two different outflow efficiencies including the nominal mass-loading
factor from P. D. Mitchell et al. (2020). Lower outflow efficiencies increase the metal content at a given stellar mass.
The width of the swaths shows a range in the metallicity of
the inflowing gas from metal free ( _r_ Z = 0) to 50% ( _r_ Z = 0 _._ 5)
of the metallicity of the ISM gas.


dependent lifetimes given in L. Portinari et al. (1998).
Figure 3 shows the immediate mass ejection rate into
the ISM (top panel) and the cumulative total ejected
metal mass (bottom panel) as a function of time based
on this model. In this educational example, we assumed
a simple SFH in the form of a starburst with constant
SFR over ∆ _t_ = 100 Myr (hatched area) and a total produced stellar mass of 5 _×_ 10 [9] M _⊙_ (no SFR before or after
burst). It is evident that type II SNe contribute the bulk
of metals early on within _∼_ 150 Myrs after the start of
the burst. AGB stars (at lower masses) contribute most
of the ejecta at _>_ 100 Myrs [8] .
This simple analytical model successfully reproduces
the observed star-forming main sequence at _z_ _∼_ 5 (e.g.,


the ISM. However, limiting our calculation to this mass limit
has a negligible impact on the following results.
8 Note that carbon yields in the most massive stars can be negative as the surface chemistry of these objects is mostly determined by hot bottom burning, which destroys carbon in the
envelope. This causes the drop in the total metal abundance
at _∼_ 150 Myrs after the onset of star formation.



9


Y. Khusanova et al. 2021) and lower redshifts, assuming reasonable average values of _t_ depl = 5 _×_ 10 [8] yr (e.g.,
M. _M_ ˙ gas Dessauges-Zavadsky _,_ in = 100 M _⊙_ yr _[−]_ [1] (e.g.,et al.N.2020Scoville) andetaccretional. 2023rates).
Figure 4 shows the resulting MZR of our model at
_z_ _∼_ 5 (hexagonal bins). The model output is colorcoded by the age of the stellar population between
50 Myrs (blue) and 900 Myrs (red). The data from the
ALPINE-CRISTAL-JWST sample are shown as large
circles color-coded by age [9] on the same color scale.
Other data from the literature at _z_ = 4 _−_ 6 are shown as

gray squares. This simple analytical model with realistic
metal yields is able to reproduce the parameter space of
observations on the MZR at _z_ _∼_ 5 (Figure 4). In fact,
our model also reproduces the FMR. Importantly, it is
also broadly consistent with most of the observed ages of
the ALPINE-CRISTAL-JWST galaxies (shown at same
color scale in Figure 4). We note that the measurement
of ages comes with large uncertainties (factors of two
or more), which could explain some of the discrepancies
between the observed and model ages. Furthermore, the
SED-fit ages may be younger as they capture commonly
the age since the last significant starburst, while the ages
output by our model are the times since first star formation. The upper boundary of the MZR is given in our
model by the maximal age of a galaxy at _z_ _∼_ 5, hence
maximal cumulative metal abundance produced by our
model. The model reemphasizes the fast metal buildup; metallicities of 12 + log (O _/_ H) _∼_ 8 _._ 3 (the median
at 3 _×_ 10 [9] M _⊙_ ) are reached after only 200 Myrs of star
formation.

In addition, we can investigate the impact of gas inflows and the mass loading factor on the results. The
three gray swaths in Figure 4 show our analytical model
with three different mass-loading implementations: the
nominal _ϵ_ out as well as two adjustment; 0 _._ 5 _× ϵ_ out and
2 _×_ _ϵ_ out . (Note that this is equivalent to _ϵ_ SN = 0 _._ 5
and 2 in A. Pallottini et al. 2025.) The width of the
swaths shows a range of relative metal enrichment of
the infalling gas from pristine (0%) to 50% of the ISM
metallicity. As shown in W. Wang et al. (2026), the
CGM around the ALPINE-CRISTAL-JWST galaxies is
already significantly metal enriched, therefore some recycling of the already metal-enriched gas is expected.
We find that the nominal _ϵ_ out derived from the EAGLE
(or FIRE-2) simulation underpredicts the metal abundance. Instead, a factor of two decreased outflow efficiency (or mass-loading factor) puts our model in better
agreement with the observed MZR. Interestingly, such


9 The ages are derived from SED fitting assuming delayed _τ_ models, see A. L. Faisst et al. (2020) and A. Tsujita et al. (2026).

10


a weaker outflow efficiency (lower mass-loading factor)
is also more consistent with the measured mass-loading
factors ( _ϵ_ out _∼_ 1 at log(M _/_ M _⊙_ ) _∼_ 10) of the ALPINECRISTAL galaxies (M. Ginolfi et al. 2020; J. E. Birkin
et al. 2025) as shown in Figure B.3 in Appendix B. These
findings are consistent with A. Pallottini et al. (2025),
which suggests a reduction of the outflow efficiency by
a factor of two-thirds ( _ϵ_ SN _∼_ 0 _._ 3). Observationally, the
effect of outflows is difficult to constrain, as it depends
on various physical quantities such as star formation,
outflow velocity, or density of the ISM, which may all
depend on redshift (e.g., R. L. Davies et al. 2019).
In summary, our simple analytical model describes
well the overall MZR at _z_ _∼_ 5 of low-mass JWST
detected and massive ALPINE-CRISTAL-JWST galaxies. The range of observed metallicities at a given stellar mass (hence the MZR scatter) can, to first order, be
explained by a mix of different stellar population ages,
outflow efficiencies (mass-loading factors), and the metal
enrichment of infalling gas. Notably, metals build up
quickly to the observed levels within _<_ 200 Myrs since
the onset of star formation. To reproduce the most
metal-poor systems, either very young ( _≪_ 200 Myrs)
stellar populations or efficient metal-rich mass outflows
(Figure 4) need to be assumed. Specifically, due to
the fast build-up of metals, any previous metals need
to be removed in order to observe a galaxy as metalpoor. This can be achieved by strong outflows or the
accretion of pristine gas. In addition, metal poor systems could be associated with under-dense environments
(isolating the galaxies from growth through gas inflows),
such as suspected for a recently found metal-poor system _AMORE6_ at _z_ = 5 _._ 7 (T. Morishita et al. 2025).
The most metal-rich systems are either old or have significantly less efficient outflows. Future, more detailed,
observations of outflow rates from optical emission lines
and the large-scale structure of the surrounding environment of these galaxies may help to distinguish these
processes. In Section 4.2 we will further study the effect
of a stochastic SFH, which may cause galaxies to scatter
to lower metallicity.
Finally, we note that the observed metallicities are
spatially integrated (consistent with the output of our
analytical model). Spatially resolved metal abundances
may show additional large variations. For example,
pockets of recent star formation driven by pristine
gas inflow may have lower-than-average metallicities (J.
S´anchez Almeida et al. 2014, 2015). This is also further
discussed in S. Fujimoto et al. (2025) and F. Lopez et al.
(2025, in prep).



**Table** **3.** Scatter of the FMR measured at a given _µ_ (and
_µ_ 0 ) at different redshifts.


_z_ _σ_ FMR _σ_ ˆ FMR _†_ _µ_ 0 Reference
(dex) (dex)
_z_ _∼_ 0 0 _._ 02 _<_ 0 _._ 02 0 _._ 22 (1)
0 _._ 03 _<_ 0 _._ 03 0 _._ 55 (2)
_z_ _∼_ 2 _._ 3 0 _._ 16 0 _._ 06 0 _._ 60 (3)
_z_ _∼_ 3 _._ 3 0 _._ 22 0 _._ 06 0 _._ 60 (3)

_z_ _∼_ 5 0 _._ 24 0 _._ 13 0 _._ 66 _[⋆]_ This work

0 _._ 22 0 _._ 10 0 _._ 22 This work


Note— References: (1) F. Mannucci et al. (2010); (2) M.
Curti et al. (2020); (3) R. L. Sanders et al. (2021).

_†_ FMR scatter deconvolved by measurement uncertainties.

_⋆_
Consistent with _µ_ 0 = 0 _._ 65 obtained by M. Curti et al.

(2024).


4.2. _Scatter_ _of_ _the_ _FMR_ _and_ _its_ _Universality_


As shown in the right panel of Figure 2, there is significant scatter in the FMR especially at lower stellar
masses. For a _µ_ 0 = 0 _._ 66 (B. H. Andrews & P. Martini
2013), we measure a scatter of _σ_ FMR _∼_ 0 _._ 24 dex based
on the data at _z_ = 4 _−_ 6. Similar to F. Mannucci et al.
(2010), we have additionally tried to minimize the FMR
scatter by choosing an optimal _µ_ 0 . We found that _µ_ 0 =
0 _._ 22 decreases the scatter to _σ_ FMR _∼_ 0 _._ 22 dex, which is
negligibly smaller than for _µ_ 0 = 0 _._ 66. The value of the
scatter is consistent with M. Curti et al. (2024) at similar redshifts. We therefore use _µ_ 0 = 0 _._ 66 in the following
to be consistent with other studies (B. H. Andrews & P.
Martini 2013; M. Curti et al. 2020). The intrinsic FMR

ˆ
scatter is _σ_ FMR = ~~�~~ _σ_ FMR [2] _[−]_ _[σ]_ meas [2] _[∼]_ [0] _[.]_ [10] _[ −]_ [0] _[.]_ [13 dex,]
for _µ_ 0 = 0 _._ 22 _−_ 0 _._ 66 and assuming a conservative uncertainty in the metallicity measurement of _σ_ meas = 0 _._ 2 dex
(M. Curti et al. 2024). This is a factor of five larger than

ˆ
the scatter measured at _z_ = 0, _σ_ FMR _,_ 0 ≲ _σ_ FMR _,_ 0 = 0 _._ 02
(F. Mannucci et al. 2010), and also significantly larger

ˆ
than at _z_ _∼_ 2 _−_ 3, _σ_ FMR _∼_ 0 _._ 06 (R. L. Sanders et al.
2021). Note that the latter finds that _µ_ 0 = 0 _._ 60 minimizes the scatter for sample at _z_ = 2 _._ 3 and _z_ = 3 _._ 3.
Measurements of the FMR scatter at different redshifts
are summarized in Table 3. As mentioned previously,
the large scatter in the FMR at _z_ = 5 cannot be minimized by adjusting _µ_ 0 . Furthermore, the scatter is similar to the scatter of the MZR (corresponding to _µ_ 0 = 0).
This questions the existence of a _fundamental_ metallicity relation at _z_ = 5, which has also been discussed in
previous works (e.g., C. C. Steidel et al. 2014; N. A. Korhonen Cuestas et al. 2025). The “non-reducible” scatter of the MZR when including star formation as a third
parameter therefore hints towards a difference compared
to lower redshifts samples — for example a bursty star

formation or early metal build up — which is explored
in the next section.


4.3. _Can_ _a_ _Bursty_ _Star_ _Formation_ _Explain_ _the_ _Scatter_
_of_ _the_ _FMR?_


It is now well established that star formation is

stochastic and bursty especially for galaxies at high redshifts and low stellar masses (e.g., G. Sun et al. 2025;
A. L. Faisst & T. Morishita 2024; R. Endsley et al. 2024;
R. Navarro-Carrera et al. 2024; L. Ciesla et al. 2024;
J. B. Mu˜noz et al. 2023; X. Shen et al. 2023; Y. Asada
et al. 2023; V. Mehta et al. 2023; A. L. Faisst et al.
2019; N. Emami et al. 2019; N. Caplar & S. Tacchella
2019; D. R. Weisz et al. 2012). This stochasticity may
be driven by the outflow of gas through SNe feedback
(specifically at low stellar masses), changes in gas accretion, and gas compaction and depletion events (e.g.,
C.-A. Faucher-Gigu`ere 2018).
We further tested this scenario by directly using
a stochastic SFH in our analytical model described
in Section 4.1. Note that at this point, the model
does not assume an equilibrium state anymore (contrary to the common “gas regulator” or “bathtub”
model), but we directly compute the metal enrichment
for an arbitrarily changing SFH. We adopt a stochastic
(bursty) SFH as described in A. L. Faisst & T. Morishita (2024) and based on the mathematical prescription by N. Caplar & S. Tacchella (2019). Specifically,
we use the `DELightcurveSimulation` Python package [10]

(S. D. Connolly 2016), which is based on the D. Emmanoulopoulos et al. (2013) light-curve simulation algorithm. We assume a generalized power spectrum density
(PSD, with a slope _α_ PSD = 2; A. L. Faisst & T. Morishita 2024). The stochastic SFH is parameterized by a
burstiness amplitude ( _σ_ MS ; _i.e._ the amplitude distance
from the main-sequence in dex) and a correlation time
( _τ_ break ; _i.e._ roughly the ∆ _t_ between amplitude peaks).
We simulated SFHs with _σ_ MS = 0 _._ 1, 0 _._ 3, and 0 _._ 6 dex
and _τ_ break = 5, 50, and 200 Myrs. The latter is expected
from simulations such as SPHINX [20] (J. Rosdahl et al.
2018, 2022; H. Katz et al. 2022; A. L. Faisst & T. Morishita 2024).
The resulting scatter of the FMR from this model as
well as other analytical models (see Section 4.4) is compared to the observed scatter (ˆ _σ_ FMR ) in Figure 5. An increased burstiness amplitude increases the FMR scatter,
but we do not find a significant dependency on _τ_ break except for the largest _σ_ MS, where a shorter correlation time
causes larger scatter. The scatter is largest at low stellar
masses (corresponding to early times in a galaxy’s evo

10 [https://github.com/samconnolly/DELightcurveSimulation](https://github.com/samconnolly/DELightcurveSimulation)



11


lution and low _µ_ ) and decreases towards higher stellar
masses. Furthermore, increased burstiness causes a _neg-_
_ative_ (downward) scatter on the FMR similar to observational findings. The increased (downward) scatter could
be explained as follows: as the galaxies are young and
pristine, small variations in metal abundances (caused
by star formation burstiness and almost instantaneous
SNe dust production) can be observed causing the observed scatter. Further infall of pristine gas may lower
the gas-phase metal abundance temporarily. As the
galaxies evolve, they become more metal enriched, producing metals more steadily (e.g., through older AGB
stars). Local fluctuations in metal enrichment due to
SNe metal production will be below the sensitivity limit
of current observations, thus the overall observed scatter is reduced. We note that in our simple model the
burstiness is constant with stellar mass (in reality, more
massive galaxies are expected to be less bursty, e.g. D. R.
Weisz et al. 2012; N. Emami et al. 2019). The reduction of the observed scatter can therefore be explained
purely due to the metal build-up (decreasing the contrast with respect to small metal abundance fluctuations) and the importance of more smooth metal production mechanisms (AGB metal production vs. SNe
metal production). We find that a burstiness amplitude
of _σ_ MS = 0 _._ 6 dex can reproduce the observed scatter (deconvolved by measurement errors) well at high redshifts.
However, a lower amplitude ( _≪_ 0 _._ 3 dex) would be sufficient to explain the FMR scatter of low redshift galaxies.
Our findings are consistent with a study by A. Pallottini et al. (2025), which shows, using a similar model,
that the scatter of the MZR significantly depends on
the burstiness of star formation. Furthermore, studies
at low redshifts suggest extremely metal poor galaxies
to be dispersion dominated and gas rich, suggesting they
are dominated by bursts and gas inflow (e.g., Y. Isobe
et al. 2023).
We conclude that the scatter of the FMR at low metallicities (hence specifically low stellar masses) may be due
to a bursty star formation history. Similar to observations, our bursty model suggests an asymmetric and negative FMR scatter. At later times, however, burstiness
does not have a significant impact on the total observed
metallicity. This may explain the smaller FMR scatter
at low redshifts compared to higher redshifts. Furthermore, metal mixing may play a role.


4.4. _Comparison_ _to_ _Simulations_ _and_ _other_ _Analytical_
_Models_


Our simple analytical model described in the previous sections reproduces well the observations at _z_ _∼_ 5
of the FMR and MZR. Furthermore, we showed that

12



0.4


0.2


0.0


0.2


0.4


0.4


0.2


0.0


0.2


0.4


0.4


0.2


0.0


0.2


0.4









|Col1|MS =|0.1 dex|Col4|Col5|Col6|= 5 Myr|Col8|
|---|---|---|---|---|---|---|---|
||MS ~~=~~|~~ 0.1 dex~~|||brea<br>brea<br>|k = 5 Myr<br>k = 50 Myr<br>||
||||||~~brea~~|~~k = 200 My~~|~~ r~~|
|||||||||
||||||**Observ**|**ations (z** **=** **5**|**)**|
||||||Liu et<br> <br>**Observ**|al. (2024)<br> <br>**ations (z** **=** **0**|<br>**)**|
||||||Pallott|ini et al. (202|5)|
|||||||||
||MS ~~=~~|~~ 0.3 dex~~|||brea<br>brea<br>|k = 5 Myr<br>k = 50 Myr<br>||
||||||~~brea~~|~~k = 200 My~~|~~ r~~|
|||||||||
||||||**Observ**|**ations (z** **=** **5**|**)**|
||||||Liu et<br> <br>**Observ**|al. (2024)<br> <br>**ations (z** **=** **0**|<br>**)**|
||||||Pallott|ini et al. (202|5)|
|||||||||
||MS ~~=~~|~~ 0.6 dex~~|||brea<br>brea<br>|k = 5 Myr<br>k = 50 Myr<br>||
||||||~~brea~~|~~k = 200 My~~|~~ r~~|
|||||||||
||||||**Observ**|**ations (z** **=** **5**|**)**|
||||||Liu et<br> <br>**Observ**|al. (2024)<br> <br>**ations (z** **=** **0**|<br>**)**|
||||||Pallott|ini et al. (202|5)|
|7.0<br>= l|7.0<br>= l|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|7.5<br>8.0<br>8.5<br>9.0<br>9.5<br>10.<br> og(M/M<br>)<br>0.66 × log(SFR/[M<br>yr<br>1])|


**Figure 5.** Scatter of the FMR as a function of _µ_ for different
assumption of burstiness of the SFH. The SFH is described
by a burstiness amplitude ( _σ_ MS, different panels) and a correlation timescale ( _τ_ break, shades of blue). The observed FMR
scatter (deconvolved by measurement errors) at _z_ _∼_ 5 and
_z_ = 0 is shown in light and dark gray, respectively. We also
show the scatter derived from the analytical models from
L.-J. Liu et al. (2024) (long-dashed line) and A. Pallottini
et al. (2025) (dotted line).


the _asymmetric_ scatter in the FMR can be naturally explained by a stochastic star formation history. However,
our simple model only provides limited predictions. For
example, the burstiness of star formation is connected
to (or originates from) other physical processes such as
gas outflows and star formation efficiencies or change in
the gas inflows. In this section, we therefore compare
the observations to predictions from cosmological simulations that include realistic feedback, outflow, inflow,
and mass assembly.
Figure 6 shows the observations at _z_ _∼_ 4 _−_ 6 (black
dots and circles) compared to various cosmological simulations and analytical models which are listed in the
following.


SERRA _Zoom-In_ _Simulation_ — The SERRA simulations are a set of zoom-in high-resolution (1 _._ 2 _×_ 10 [4] M _⊙_,
_≃_ 25 pc at _z_ = 7 _._ 7) cosmological simulations including non-equilibrium chemistry and on-the-fly radiative
transfer (A. Pallottini et al. 2022). The masses of the
galaxies range approximately between 10 [7] _−_ 5 _×_ 10 [9] M _⊙_ .
Generally, the SERRA galaxies reproduce well the ob


served population in the mass range 10 [8] _−_ 10 [9] M _⊙_, but
they slightly overpredict and underpredict the metal
abundances at lower and higher stellar masses, respectively (left panel, blue contours). The underprediction of
metals in massive galaxies may be tied to the stochasticity of the SERRA galaxies as discussed in A. Pallottini
et al. (2025). The overprediction at lower masses could
be due to weak feedback (c.f. L.-J. Liu et al. 2026).


FIRE-2 _Zoom-In_ _Simulation_ — FIRE-2 is a suite of

cosmological zoom-in simulations including the implementation of realistic stellar and radiation feedback and
winds (P. F. Hopkins et al. 2014, 2018; X. Ma et al.
2018a,b, 2019; P. F. Hopkins et al. 2023). The particle
resolution is 100 _−_ 7000 M _⊙_ and the masses of the galaxies range from 10 [6] _−_ 10 [10] M _⊙_ at _z_ _∼_ 5. The MZR derived in A. Marszewski et al. (2024) (see also X. Ma et al.
2016) compares well to observations, although it slightly
underpredicts the metal abundances at _<_ 10 [8] M _⊙_ (left
panel, orange contours).


NewHorizon _Zoom-in_ _Simulation_ — The NewHorizon project (Y. Dubois et al. 2021) performs a highresolution zoom-in simulation extracted from the parent simulation Horizon-AGN ((142 Mpc) [3] ; Y. Dubois
et al. 2014) in a box size of (16 Mpc) [3] and a resolution
of up to 34 pc. These simulations are generally in good
agreement with the observed MZR at stellar masses of
_<_ 10 [9] M _⊙_ (left panel, green contours). However, the
scatter is narrow and the sample size at higher stellar
masses is small, both likely due to the small volume
probed by the simulation.


FirstLight _Zoom-in_ _Simulation_ — FirstLight is a

suite of multi-object zoom-in simulations including in
total 430 galaxies (D. Ceverino et al. 2017). The simulations are assorted in four different volumes from 10 to
80 Mpc _/_ h with different mass resolutions. To match the
massive _M_ _∗_ _∼_ 10 [10] _[−]_ [11] M _⊙_ ALPINE-CRISTAL galaxies
at _z_ _∼_ 5, we make use of the two largest box sizes (40 and
80 cMpc _/_ h; Y. Nakazato et al. 2023; D. Ceverino et al.
2026) with dark matter mass resolutions of 8 _×_ 10 [4] and
6 _×_ 10 [8] _M_ _⊙_, respectively, and maximal spatial resolutions of 17 and 35 pc, respectively. These simulations are
in good agreement with the ALPINE-CRISTAL-JWST
observations (left panel, purple contours).


DUSTY-GAEA _Simulation_ — DUSTY-GAEA is a

modified version of the state-of-the-art semi-analytic
GAlaxy Evolution and Assembly (GAEA; G. De Lucia et al. 2014; M. Hirschmann et al. 2016; L. Xie et al.
2020; F. Fontanot et al. 2020; G. De Lucia et al. 2024)
model, where a dust physical prescription is included in
a self-consistent manner (O. Osman et al. 2025). The

13


**Figure** **6.** Comparison of the observed MZR at _z_ _∼_ 5 (black circles, see also Figure 1) with various simulations. For better
visibility, we show three panels focusing on different simulations. _Left:_ The different contours show results from SERRA (blue;
A. Pallottini et al. 2022), FIRE-2 (orange; X. Ma et al. 2016; A. Marszewski et al. 2024), NewHorizon (green; Y. Dubois
et al. 2021), and FirstLight (purple; D. Ceverino et al. 2017; Y. Nakazato et al. 2023; D. Ceverino et al. 2026). _Middle:_ The
different areas show results from DUSTY-GAEA (pink forward line-hatched; O. Osman et al. 2025), SPHINX [20] (green dotted;
J. Rosdahl et al. 2018, 2022; H. Katz et al. 2023), IllustrisTNG ( _z_ = 4 _−_ 6; gold shaded; M. Hirschmann et al. 2023), and
THESAN-ZOOM (salmon shaded; R. Kannan et al. 2025). _Right:_ Results from different analytical models are shown including
L. Pantoni et al. (2019) (teal shaded), A. Pallottini et al. (2025) (purple dotted), and L.-J. Liu et al. (2024) (gray shaded).



DUSTY-GAEA model is run on the Millennium (V.
Springel et al. 2005) and Millennium II (M. BoylanKolchin et al. 2009) merger trees to cover the wide range
of the stellar mass (log(M _/_ M _⊙_ ) _>_ 7) on the MZR plane.
This model describes well the observed MZR (middle
panel, pink forward-hatched).


SPHINX [20] _Simulation_ — The SPHINX [20] is a full box

cosmological radiation hydrodynamics simulation optimized to simulate cosmic reionization and the multi
phase ISM of high- _z_ galaxies to provide statistical samples of galaxies similar to those currently being observed
by JWST (J. Rosdahl et al. 2018, 2022; H. Katz et al.
2023). The metallicity measurement are taken from
the current data release described in H. Katz et al.
(2023). These simulations generally underpredict the
metal abundances of _z_ _∼_ 5 galaxies (middle panel, green
dotted) and occupy a similar parameter space as the
FIRE-2 galaxies in terms of stellar mass and metallicity.


IllustrisTNG _Simulation_ — IllustrisTNG is

a suite of large volume, cosmological, gravomagnetohydrodynamical simulations, covering 302 _._ 6 [3],
106 _._ 5 [3], and 51 _._ 7 [3] cMpc [3], respectively, and particle resolutions between 10 [4] _−_ 10 [7] M _⊙_ (F. Marinacci et al. 2018;
J. P. Naiman et al. 2018; D. Nelson et al. 2018, 2019;
V. Springel et al. 2018; A. Pillepich et al. 2018, 2019).
We compare the observations to the resulting MZR for



stellar masses of 10 [8] _−_ 10 [11] M _⊙_ from M. Hirschmann
et al. (2023), who derived accurate optical emission line
for the simulated galaxies in post-processing (middle
panel, yellow shaded). The predicted metal abundances
reproduce well the observations.


THESAN-ZOOM _Zoom-In_ _Simulation_ — This is a zoomin to the cosmological simulation THESAN-1 (R. Kannan et al. 2022; A. Smith et al. 2022; E. Garaldi et al.
2022) at a baryonic mass and spatial resolution of
142 M _⊙_ and _∼_ 17 cpc, respectively. It includes selfconsistently the effects of supernova feedback, radiation
fields, dust physics, and low temperature cooling via
molecular hydrogen (F. Marinacci et al. 2019; R. Kannan et al. 2020, 2021). We use the MZR prediction presented in R. Kannan et al. (2025) and find a good agreement with the observed relation (middle panel, salmon
shaded). However, we notice that the spread in metallicity is significantly narrower than that observed.


_L. Pantoni et al. (2019) Analytical Model_ — Similar to our
model, this analytical model self-consistently describes
the spatially averaged time evolution of the gas, stellar, metal, and dust contents (see also A. Lapi et al.
2020), based on the model by A. Lapi et al. (2017). It
is thought to better represent high- _z_ galaxies and progenitors of early type galaxies compared to constant gas
inflow models. It reproduces well the overall metal abun

14


dances, however, it slightly overestimates the metallicity
of the most massive galaxies (right panel, teal shaded).


_A._ _Pallottini_ _et_ _al._ _(2025)_ _Analytical_ _Model_ — This minimal physical model, directly tied to the dark matter
halo growth, is similar in general to the one used in this
work. The model has adjustable SNe delay, feedback,
and variable accretion rate to simulate an oscillating,
bursty SFH. Here we use the model “weak feedback and
modulated accretion”, which reproduces the observed
MZR well (right panel, purple dotted). As shown in
Figure 5, this model leads to a similar scatter in the
FMR as our stochastic SFH model assuming _σ_ MS scatter between 0 _._ 3 _−_ 0 _._ 6 dex and recovers well the observed
FMR scatter at _z_ _∼_ 5 (however, it slightly overpredicts
the FMR scatter at the lowest stellar masses). Note that
the scatter reported here from A. Pallottini et al. (2025)
is the maximal range of models (not the 1 _σ_ value). Importantly, a decreasing trend of FMR scatter with stellar
mass is reported as well by this model.


_L.-J._ _Liu_ _et_ _al._ _(2024)_ _Analytical_ _Model_ — This physically motivated analytical model takes a similar approach as A. Pallottini et al. (2025). It implements a
modulated SFH as a result of delayed injection of supernova feedback (S. R. Furlanetto & J. Mirocha 2022)
in a self-regulated disk model as the basis for describing galaxy-scale star formation (see also C.-A. FaucherGigu`ere et al. 2013; C.-A. Faucher-Gigu`ere 2018). It
self-consistently models the gas, stellar, metal contents,
and line emissions that trace the star formation. Adopting the scenario with galactic wind driven by reduced
supernova feedback (smaller mass-loading factor), this
model matches the measured MZR (right panel, gray
shaded) and is broadly consistent with the observed 1 _σ_
scatter of the FMR derived from our stochastic SFH
model (Figure 5). However, the scatter of metallicity
predicted by this model is larger than observed at stellar
mass of _<_ 10 [8] _M_ _⊙_ . This can be induced by the burstiness in low-mass galaxies whose shallow gravitational
potentials are unlikely to prevent metal contents from
being evacuated by feedback-driven outflows.


We note that most simulations reproduce the scatter of the observe metal abundances at a given stellar
mass. This shows that the scatter in the MZR is dom
inated by physical processes and not measurement uncertainties (see also Section 4.1). The reason that some
cosmological simulations underpredict the metal abundances could be due to limited volume coverage to simulate galaxies that have above-average metal enrichment
(e.g., fast evolving galaxies). For example, the FIRE2 simulation covers _∼_ (43 cMpc) [3] and the SPHINX [20]

simulation covers _∼_ (20 cMpc) [3], which are both signif


icantly smaller volumes than covered by observations
( _∼_ (100 cMpc) [3] ). This may be connected to failing to
reproduce the significant ALMA far-infrared [O III ] 88 _µ_ m
emission in two _z_ _>_ 12 galaxies (see discussion in S.
Yang et al. 2025). However, other differences such as
the implementation of feedback, radiative heating and
cooling, or chemical models may also change the resulting metal enrichment. Lastly, observational constraints
may still hinder the detection of low-metallicity galaxies
at high redshifts. This could be mitigated by observing
lensed high-redshift galaxies (e.g., B. Welch et al. 2025;
L. Christensen et al. 2012a,b; E. Vanzella et al. 2023).


4.5. _The_ _progenitors_ _and_ _descendants_ _of_ _the_ _ALPINE_
_galaxies_


We use the DUSTY-GAEA simulation model (O. Osman et al. 2025) to characterize the evolutionary path
of the ALPINE-CRISTAL-JWST galaxies on the MZR
and FMR plane. We chose DUSTY-GAEA because it
is able to reproduce well the metal abundances over the
full stellar mass range of galaxies at _z_ _∼_ 5 (Figure 6) as
well as lower redshifts (F. Fontanot et al. 2024).
We chose _∼_ 2400 representative galaxies in the
DUSTY-GAEA model that cover the range of
metallicity (12 + log(O _/_ H) = 7 _._ 8 _−_ 8 _._ 7), SFR
(log(SFR _/_ [M _⊙_ yr _[−]_ [1] ]) = 1 _._ 2 _−_ 2 _._ 3), and stellar mass
(10 [9] _[.]_ [5] _−_ 10 [10] _[.]_ [9] M _⊙_ ) of the ALPINE-CRISTAL-JWST
sample. We then trace the galaxies backward and forward in time by following their merger trees. We use
both Millennium (V. Springel et al. 2005) and Millennium II (M. Boylan-Kolchin et al. 2009) merger trees to
cover the wide range of the stellar mass (log(M _/_ M _⊙_ ) _>_
7).
The left panel of Figure 7 shows the MZR including observations at _z_ = 4 _−_ 6 (ALPINE-CRISTALJWST galaxies indicated with large black symbols).
The simulated DUSTY-GAEA tracks of the ALPINE
CRISTAL-JWST progenitor galaxies are indicated as
red lines from redshifts _z_ = 15 to _z_ = 5 (indicated by
red dots). The blue line shows the tracks of the descendants from _z_ = 5 to _z_ = 0 (indicated by blue dots). The
red/blue cloud shows the range of galaxy model progenitors/descendants marginalized over all those simulated
galaxies. The tracks themselves connect the median values at a given redshift snapshot. The progenitors of
the ALPINE-CRISTAL-JWST galaxies follow a slightly
sloped MZR to _z_ _∼_ 10 ( _∼_ 700 Myrs in the past) after
which there are indications that the relation drops off
more steeply to lower metallicities (note that the time
difference from _z_ = 10 to _z_ = 15 is only _∼_ 250 Myrs).
One caveat is that the Millennium simulation only
sparsely populates the regime at _z_ _>_ 9. We there

15



**ALPINE** **(z** **5)**


z = 0

z = 4 6

z > 6

Milky Way


7 8 9 10 11


= log(M/M ) 0.66 × log(SFR/[M yr 1 ])



9.5


9.0


8.5


8.0


7.5


7.0


6.5



~~**ALPINE**~~ ~~**(z**~~ ~~**5)**~~


z = 4 6

z > 6

Milky Way



Maiolino et al. (2008)



z = 0.07

z = 0.7



z = 2.2

z = 3.5



9.5


9.0


8.5


8.0


7.5


7.0


6.5



7 8 9 10 11 12


log(M/M )



**Figure 7.** Tracks of simulated DUSTY-GAEA model progenitors (red) and descendants (blue) of the ALPINE-CRISTAL-JWST
sample. _Left:_ The MZR with observations at _z_ = 4 _−_ 6 (gray squares) and _z_ _>_ 6 (solid dark gray squares) as well as our Milky
Way ( _§_ ) indicated. The ALPINE-CRISTAL-JWST sample is indicated with large black circles. The MZR parameterizations
from R. Maiolino et al. (2008) at different redshifts are indicated as thin lines. The DUSTY-GAEA models (matched to the
ALPINE-CRISTAL-JWST galaxies in metallicity, SFR, and stellar mass) are shown in red ranging from _z_ = 5 to _z_ = 15
(∆ _t_ = 1 Gyr, redshifts indicated by red dots) and blue from _z_ = 5 to _z_ = 0. The red/blue cloud shows the possible range of
progenitor/descendant tracks. _Right:_ Same as left panel, but showing the FMR. The local FMR (B. H. Andrews & P. Martini
2013) is shown as dashed line. The 1 _σ_ and 3 _σ_ scatter of the _z_ = 4 _−_ 6 observations around this local relation are shown as light
and dark gray bands, respectively.



fore compared the progenitor tracks to _∼_ 400 galaxies
from the Planck Millennium simulation ( `PMILL` ; C. M.
Baugh et al. 2019). This _N_ -body simulation is updated
with the recent Planck cosmology ( Planck Collaboration et al. 2014) and supports a higher resolution and
better time sampling at high redshifts than the Millennium simulation. Making use of this increased sampling
we found a slightly less steep metallicity evolution beyond _z_ = 9, but overall consistent with the previous
results.

The comparison to simulations emphasizes the fast
build-up of metals at early times before flattening off
to join a more mature main-sequence evolution of metals over time, characterized by the local FMR. Note
that this is consistent with our simple analytical model
(Figure 6), showing younger galaxies at lower metallicity at a given stellar mass. Furthermore, such a
transition has been discussed in D. Burgarella et al.
(2025), suggesting a possible shift in the mechanism
of metal and dust production around a critical metallicity of 12 + log (O _/_ H) _∼_ 7 _._ 6 from being dominated
by stellar-dust production (mainly from SNe) to grain
growth through gas-dust accretion in the ISM.
This early build-up of metals is further visualized on
the FMR (right panel, Figure 7). The progenitors of the
ALPINE-CRISTAL-JWST galaxies start to “fall off”
the local relation around _z_ _∼_ 10 as they have a significantly ( _>_ 3 _σ_, indicated by the gray bands) lower metal


licity at a given _µ_ compared to the _z_ = 4 _−_ 6 observed
population and the local relation. This suggests that
the ALPINE-CRISTAL-JWST progenitors join the fundamental metallicity relation to proceed, after a rapid
build-up of metals, with more mature metal build-up.
Again, we note that for the Millennium simulation,
only 22 snapshots were saved at redshift _>_ 5. Therefore
our statements about the rapid growth of metals at early
times should be interpreted with caution. Nevertheless,
from preliminary work based on simulations with a much
larger number of snapshots (such as `PMILL` ), results are
qualitatively similar to those shown and discussed here.
We will address this more explicitly in a forthcoming
work (O. Osman et al. 2025).
Based on the DUSTY-GAEA models, the _z_ _→_ 0
descendants of the ALPINE-CRISTAL-JWST sample
galaxies are massive (log(M _⋆_ _/_ M _⊙_ ) _∼_ 11 _._ 4) with (supersolar) metallicities of 12 + log(O _/_ H) _∼_ 9. The descendants follow well the expected FMR until _z_ _∼_ 2. After
that, they become quiescent and their SFR drops from
_∼_ 60 M _⊙_ yr _[−]_ [1] ( _z_ = 2) to _∼_ 2 M _⊙_ yr _[−]_ [1] at _z_ = 0. At
that point they leave the FMR of star-forming galaxies
as shown on the right panel of Figure 7.
As comparison, we also show the approximate location of our own Milky Way in Figure 7. The total stellar mass (6 _._ 08 _±_ 1 _._ 14 _×_ 10 [10] M _⊙_ ) is taken from
T. C. Licquia & J. A. Newman (2015) and the SFR
(2 _._ 0 _±_ 0 _._ 7 M _⊙_ yr _[−]_ [1] ) from D. Elia et al. (2022). The Milky

16











**Figure** **8.** Sketch of the early metal enrichment of galaxies. Gas (yellow), metals (blue), and areas of active star formation
(red) are indicated. Metal enrichment is indicated as blue arcs and gas inflow as yellow streams. The inset figures show the
current location and scatter (red) of the galaxy at a given time on the FMR. Young galaxies experience fast metal enrichment
with large scatter on MZR and FMR due to stochastic star formation caused by variable gas inflows and outflows. Older galaxies
continue to have bursty star formation but with damped MZR/FMR scatter due to past metal enrichment.



Way’s gas-metallicity is less constrained due to different
calibrations and radial dependence. Here we assumed
12 + log(O _/_ H) _∼_ 8 _._ 75 (S. Daflon & K. Cunha 2004;
L. S. Pilyugin et al. 2006; M. Moll´a et al. 2019). The
descendants of the ALPINE-CRISTAL-JWST galaxies
are predicted to be five times more massive and have
_∼_ 0 _._ 2 dex higher oxygen abundances. However, we note
most of the metals at _z_ _<_ 1 are bound in stars, which
would mean that the actual ISM metallicities of the simulated ALPINE _z_ = 0 galaxies are lower (C. P´eroux &
J. C. Howk 2020).
In conclusion, the simulations show a consistent picture in which the ALPINE-CRISTAL-JWST galaxies
build up their metals quickly in the first _∼_ 200 Myrs
before joining the local fundamental relation around
_z_ = 10. Figure 8 summarizes the results from this paper
in a schematics. We now observe the mature evolution

of the metal abundances, moving towards solar metallicity at the highest masses at _z_ = 5. This evolution
continues down to _z_ = 0. In other words, to witness the
early build-up of metals, galaxies at _z_ _>_ 10 need to be
observed, or alternatively much younger galaxies at later
times. The first attempts to find these very metal-poor



systems at high redshifts are already underway (e.g., E.
Vanzella et al. 2023; M. Nishigaki et al. 2023; F. Cullen
et al. 2025; C. J. Willott et al. 2025; K. Nakajima et al.
2025; T. Y.-Y. Hsiao et al. 2025; T. Morishita et al. 2025;
J. Sui et al. 2026), complementing findings of extremely
metal-poor galaxies at low redshifts (e.g., Y. Shi et al.
2014; P. Senchyna et al. 2019; Y. I. Izotov et al. 2018,
2019; T. Kojima et al. 2020; S. A. Pustilnik et al. 2020,
2021; I. H. Laseter et al. 2022; Y. Isobe et al. 2023; I. D.
Karachentsev et al. 2023; J. A. Breneman et al. 2025).


5. SUMMARY & CONCLUSIONS


We have used the ALPINE-CRISTAL-JWST survey
data to investigate the spatially integrated metal enrichment of 18 massive (log(M _⋆_ _/_ M _⊙_ ) = 9 _._ 5 _−_ 11) galaxies at
_z_ _∼_ 5. This sample is complementary to previous studies of JWST-observed samples that probe lower stellar
masses, hence allows insights into the metal enrichment
of the massive early galaxies. The metallicities are derived using the strong-line method (A. L. Faisst et al.
2026) applying the R. L. Sanders et al. (2024) calibration. We find good agreement with _T_ _e_ -based metallicity
estimates for five galaxies for which such measurements

are possible. The _T_ _e_ values vary at _∼_ 1 _−_ 2 _×_ 10 [4] K and
electron densities are between _n_ _e_ = 200 _−_ 1000 cm _[−]_ [3]

with an average of 400 cm _[−]_ [3] . The main observational
findings of our study are the following:


  - Corroborating on the full stellar mass range of
samples from the literature and from the ALPINECRISTAL-JWST sample, we found a relatively
shallow mass-metallicity relation at _z_ _∼_ 5 (Equation 1). This suggests a significant (and fast) metal
enrichment even at low stellar masses. Overall,
massive _z_ = 5 galaxies increase their metal abundance from _∼_ 40% to _∼_ 60% to cosmic noon at
fixed stellar mass (Figure 1).


  - Galaxies at _z_ _∼_ 5 are to first order consistent with
the local FMR. To second order, the _z_ _∼_ 5 FMR
shows a downward scatter in metallicity at a fixed
stellar mass (or _µ_ ) compared to the local relation
(Figure 2). This could indicate the early phases of
metal enrichment.


  - We find the intrinsic scatter of the FMR at _z_ _∼_ 5
to be approximately five times larger compared to
the local FMR (Figure 5 and Table 3).


We investigated these findings further in the light of
a simple analytical model. Our model is similar to previous “gas-regulator” prescriptions (e.g. S. J. Lilly et al.
2013; R. Feldmann 2015), however, instead of using a
constant yield, we have implemented a metal enrichment based on more realistic metal yields of type II SNe
and AGB stars (Figure 3). Furthermore, we use stellar
mass and redshift-dependent mass-loading factors derived from the EAGLE simulation. Comparing the observations across the full mass range to this analytical
model as well as to the latest cosmological simulations
we further conclude:


  - Our analytical model reproduces well the observed
MZR assuming reasonable values for the gas depletion times, gas accretion rates, and the metallicity of infalling gas. However, we find that a
_∼_ 2 _×_ lower outflow efficiency ( _i.e._ lower massloading factor) than found by the EAGLE and
FIRE simulations is preferred to reproduce the
MZR at _z_ = 5 (Figure 4).


  - Our model suggests a fast metal enrichment. The
observed metallicities at _z_ = 5 can be reached

in less than 200 Myrs. Furthermore, the range of
metallicities _at_ _a_ _given_ _stellar_ _mass_ is set by the
stellar population age, the metallicity of inflowing gas, and outflow efficiency (mass-loading factor) (Figure 4). Due to the fast metal enrichment,



17


metal-poor systems need either very efficient outflows ( _>_ 2 _×_ more efficient that simulations predict) or pristine gas inflows.


  - The observed scatter of the FMR at a give stellar
mass or ( _µ_ ) can be explained naturally by a bursty
star formation (Figure 5). Less scatter is expected
for more metal-rich galaxies, which can explain the
5 _×_ lower scatter in the local FMR.


  - Cosmological simulations generally reproduce the
observed MZR, however, they tend to underpredict the metal enrichment of low-mass
(log(M _/_ M _⊙_ ) _<_ 8 _._ 5) galaxies (Figure 6). This may
be because of the lack of simulated volume or dark

matter halo resolution, or too slow enrichment of
metals over time or too efficient outflows.


  - The DUSTY-GAEA simulation (which fits the
observed MZR well at all stellar masses) suggests
that the ALPINE-CRISTAL-JWST galaxies build
up their metal abundance quickly at _z_ = 15 _−_ 10,
and then joined the observed _z_ = 5 FMR (Figure 7). The galaxies will then enrich further with
metals to reach super-solar values at stellar masses
of log(M _/_ M _⊙_ ) _>_ 11 _._ 4 (5 _×_ more massive than our
Milky Way). They will leave the FMR relation at
_z_ = 2 when star formation starts to get quenched.


Overall, galaxies at _z_ _∼_ 5 are already significantly
metal enriched at all stellar masses. The difference in
metal-enrichment at a given stellar mass can be explaind
by the evolutionary age of the galaxies but also by differences in outflow efficiency and the metallicity of the
accreted gas. The scatter in both the MZR and FMR
can be reproduced by a stochastic SFH, but only at low
masses at the onset of metal enrichment. Figure 8 summarizes these conclusions.

The outflow efficiency plays an important role in reproducing the observed MZR at _z_ _∼_ 5 as well as the
observed [C II ] halos surrounding galaxies at the same
epoch (e.g., S. Fujimoto et al. 2019). As discussed in
our work and in A. Pallottini et al. (2025), the outflows
in simulations may be too efficient in removing metalrich gas, causing an underestimation of the MZR. At the
same time, lowering the outflow efficiency to fit the MZR
may result in simulations not reproducing the extended

[C II ] halos (e.g., L.-J. Liu et al. 2026; W. Wang et al.
2026). Now, with more statistical data available, resolving this discrepancy may become an interesting topic in
the near future.

18


ACKNOWLEDGMENTS


This work is based in part on observations made with
the NASA/ESA/CSA _James_ _Webb_ Space Telescope. The
JWST and HST data presented in this article were

obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. These observations are associated with programs,
HST-GO-13641 ( doi: [10.17909/xne1-7v26),](https://doi.org/10.17909/xne1-7v26) JWST-GO01727 ( doi: [10.17909/ph8h-qf05),](https://doi.org/10.17909/ph8h-qf05) JWST-GO-03045 (
doi: [10.17909/cqds-qc81),](https://doi.org/10.17909/cqds-qc81) and JWST-GO-04265 ( [doi:](https://doi.org/10.17909/wac6-9741)
[10.17909/wac6-9741).](https://doi.org/10.17909/wac6-9741) This research has made use of the
NASA/IPAC Infrared Science Archive (IRSA), which is
funded by the National Aeronautics and Space Adminis
tration and operated by the California Institute of Tech
nology. The following dataset was used from IRSA: [doi:](https://doi.org/10.26131/IRSA178)
[10.26131/IRSA178.](https://doi.org/10.26131/IRSA178) Support for program JWST-GO-03045
was provided by NASA through a grant from the Space

Telescope Science Institute, which is operated by the Associ
ation of Universities for Research in Astronomy, Inc., under

NASA contract NAS 5-03127. This paper makes use of the
following ALMA data: ADS/JAO.ALMA#2017.1.00428.L,
#2019.1.00226.S, #2022.1.01118.S, and #2021.1.00280.L.
ALMA is a partnership of ESO (representing its member
states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The
Joint ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. This work made use of Astropy: [11] a community
developed core Python package and an ecosystem of tools
and resources for astronomy ( Astropy Collaboration et al.
2013, 2018, 2022). ALF thanks Jennifer Tan for proofreading the manuscript. AF is partly supported by the
ERC Advanced Grant INTERSTELLAR H2020/740120,
and by grant NSF PHY-2309135 to the Kavli Institute for

Theoretical Physics. AN acknowledge support from the
Narodowe Centrum Nauki (NCN), Poland, through the
SONATA BIS grant UMO-2020/38/E/ST9/00077. CG acknowledges support from the ASI-INAF agreement n. 2025
6-HH.0. DBS gratefully acknowledges support from NSF

Grant 2407752. DGE acknowledges support from ANID
BECAS/DOCTORADO NACIONAL/2024-21251071. EdC
acknowledges support from the Australian Research Council

through project DP240100589. EI gratefully acknowledge

financial support from ANID - MILENIO - NCN2024 ~~1~~ 12
and ANID FONDECYT Regular 1221846. HU acknowledges [¨]
funding by the European Union (ERC APEX, 101164796).
Views and opinions expressed are however those of the

authors only and do not necessarily reflect those of the

European Union or the European Research Council Execu

11 http://www.astropy.org



tive Agency. Neither the European Union nor the granting

authority can be held responsible for them. IDL acknowledges funding from the European Research Council (ERC)

under the European Union’s Horizon 2020 research and
innovation program DustOrigin (ERC-2019-StG-851622),
from the Belgian Science Policy Office (BELSPO) through
the PRODEX project “JWST/MIRI Science exploitation”
(C4000142239) and from the Flemish Fund for Scientific
Research (FWO-Vlaanderen) through the research project
G0A1523N. JM gratefully acknowledges support from ANID

MILENIO NCN2024 ~~1~~ 12. JS is supported by JSPS KAKENHI (JP22H01262). KVGC was supported by NASA
through the STScI grants JWST-GO-04265 and JWST-GO
03777 LV acknowledges support from the INAF Minigrant

“RISE: Resolving the ISM and Star formation in the Epoch
of Reionization” (PI: Vallini, Ob. Fu. 1.05.24.07.01). NGV
acknowledges scholarship from ANID BECAS/Doctorado
Nacional/2023-21231942 MA is supported by FONDECYT
grant number 1252054, and gratefully acknowledges support

from ANID Basal Project FB210003 and ANID MILENIO

NCN2024 ~~1~~ 12. MB gratefully acknowledges support from

the ANID BASAL project FB210003. This work was sup
ported by the French government through the France 2030

investment plan managed by the National Research Agency
(ANR), as part of the Initiative of Excellence of Univer
sit´e Cˆote d’Azur under reference number ANR-15-IDEX-01.

MR acknowledges support from project PID2023-150178NBI00 financed by MCIU/AEI/10.13039/501100011033,
and by FEDER, UE. RA acknowledges financial sup
port from projects PID2023-147386NB-I00 funded by
MCIN/AEI/10.13039/501100011033 and by ERDF/EU and
the Severo Ochoa grant CEX2021-001131-S to the IAA
CSIC. RJA was supported by FONDECYT grant number

1231718 and by the ANID BASAL project FB210003. SF

acknowledges support from NASA through the NASA Hub
ble Fellowship grant HST-HF2-51505.001-A awarded by the

Space Telescope Science Institute, which is operated by the

Association of Universities for Research in Astronomy, Incor
porated, under NASA contract NAS5-26555. VV acknowl
edges support from the ANID BASAL project FB210003

and from ANID MILENIO NCN2024 ~~1~~ 12.


_Facilities:_ HST(ACS), HST(WFC3/IR),
JWST(NIRCam), JWST(NIRSpec), ALMA


_Software:_ `Astropy` ( Astropy Collaboration et al.
2013, 2018), `PyNeb` (V. Luridiana et al. 2015)

19


APPENDIX


A. DETAILS ON METALLICITY CALCULATIONS


The left panel of Figure A.1 compares oxygen abundances based on the calibration from R. L. Sanders et al. (2024)
with the one of R. Maiolino et al. (2008) (see also T. Nagao et al. 2006). We do not find significant differences between
these calibrations within the uncertainties of the measurements. The same holds for the calibration by M. Hirschmann
et al. (2023), which is similar to the one from R. L. Sanders et al. (2024) that is used here.
In some cases, we are able to compare the strong line metallicity measurements to the oxygen abundances independently derived from fainter optical auroral lines (the “ _T_ _e_ method”, see review on metallicity measurements in L. J.
Kewley et al. 2019). These lines are only detected in a handful of galaxies; however, their detections allows an independent comparison to the metal abundances based on the strong line method. We derived the oxygen abundances
using the _getTemDen_ module of the `PyNeb` Python package (V. Luridiana et al. 2015) from the electron temperatures
( _T_ _e_ (O [+] ) and _T_ _e_ (O [++] )) and the electron density ( _n_ _e_ ) by following these steps.


1. We derived _T_ _e_ (O [++] ) from the [O III ] 4363 /[O III ] 5007 line ratio. For this we assumed _n_ _e_ = 400 cm _[−]_ [3], however,
the exact value is not important as this measurement is independent of _n_ _e_ (middle panel, Figure A.2).


2. We derived _n_ _e_ using the [S II ] 6732 /[S II ] 6718 line ratio, assuming an electron temperature of 2 _×_ 10 [4] K (again, this
assumption is not critical as the dependence on electron temperature is weak, see right panel of Figure A.2).


3. We used the derived electron density to compute _T_ _e_ (O [+] ) using the line ratio ([O II ] 7322 +[O II ] 7332 )/[O II ] 3727
(left panel, Figure A.2).



4. Finally, using the _getIonAbundance_ module of `PyNeb`, we computed the oxygen abundances [O] [+]




[+] [O] [++]

H [and] H



Finally, using the _getIonAbundance_ module of `PyNeb`, we computed the oxygen abundances H [and] H from

the [O II ] 3727 /H _β_ and ([O III ] 5007 + [O III ] 4959 )/H _β_ line ratios and the above measured electron temperatures
( _T_ _e_ (O [+] ) and _T_ _e_ (O [++] )) and electron density _n_ _e_ .



Note that we neglect higher ionization species in this calculation as they are not expected to significantly contribute
to the total abundance.



9.0


8.5


8.0










|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||~~ ailable~~|~~ ailable~~|
||||~~noTe av~~|~~noTe av~~|~~noTe av~~|~~noTe av~~|
||||Te availa|Te availa|ble||
||||Te availa|Te availa|ble||


|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||
|||Te ava|ilable|ilable|
|||Te ava|ilable||



**Figure** **A.1.** _Left:_ Comparison of metallicity calculations based on the strong-line parameterizations from R. Maiolino et al.
(2008) (and T. Nagao et al. 2006) and R. L. Sanders et al. (2024). Filled symbols indicate the five galaxies with robust electron
temperature measurements. _Right:_ Comparison of metallicity calculations based on the strong-line method (using calibration
by R. L. Sanders et al. 2024) and the direct _T_ _e_ method measured from these data. This measurement is only available for five
galaxies (filled symbols). In both panels, the light and dark gray bands show deviations of 50% and a factor of two ( _∼_ 0 _._ 3 dex),
respectively.

20



|Col1|n = 100 c|cm 3|Col4|Col5|n|= 100 cm|3|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|A|ne = 100<br>ne = 400<br>~~n~~e~~ = 3000~~<br>LPINE (z =|cm<br>3<br> cm<br>3<br>~~ cm~~<br>3<br>  5)<br>s<br>||1.00<br>1.25<br>1.50<br>1.75<br>2.00<br>Te(O+ + ) [×104 K]|n<br>n<br>~~n~~|e = 100 cm<br>e = 400 cm<br>e ~~= 3000 cm~~|3<br>3<br> <br>~~3~~|3<br>3<br> <br>~~3~~|3<br>3<br> <br>~~3~~||||
||<br>detection<br>and limits<br>~~robust~~|<br>detection<br>and limits<br>~~robust~~|<br>detection<br>and limits<br>~~robust~~|<br>detection<br>and limits<br>~~robust~~|||||||||
||||||||||||||


2.00 1.75 1.50 1.25

log ~~(~~ [OIII][OII] 50074363 [)]



10 [3]


10 [2]



3


2


1



2.00 1.75 1.50 1.25

log ( [OII][OII] 7322, 73323727 )





|T|T = 1×104 K|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|T<br>T<br>T|e = 1×104 K<br>e = 2×104 K<br>e = 3×104 K|e = 1×104 K<br>e = 2×104 K<br>e = 3×104 K||||
|||||||
|||||||


0.1 0.0 0.1 0.2

log ~~(~~ [SII][SII] 67186732 [)]



**Figure** **A.2.** Relation between line ratios, electron temperatures, and electron density derived from `PyNeb` (blue) including
the measurements of the ALPINE-CRISTAL-JWST targets (symbols). The five galaxies indicated in red have the most robust
_T_ _e_ -based metallicity measurements (see also Figure A.1).


In summary, we find electron temperatures of 1 _−_ 2 _×_ 10 [4] K and electron densities of 100 _−_ 1000 cm _[−]_ [3] ( _⟨n_ _e_ _⟩∼_
400 cm _[−]_ [3] ). These values are consistent with other measurements performed by JWST on galaxies of similar mass,
SFR, and redshift (e.g. from the _AURORA_ survey; M. W. Topping et al. 2025). The uncertainty in these parameters
and the derived metal abundances are substantial due to the low signal-to-noise ratio of the auroral lines. We therefore
only considered galaxies to have robust _T_ _e_ -based metallicity measurements if they have a robust ( _<_ 50% uncertainty)
detection of the [O III ] 4363, [O II ] 7322, and [O II ] 7332 lines. The five galaxies that pass this criteria are indicated in
red in Figure A.2; _DC-417567_, _DC-630594_, _DC-709575_, _DC-842313_, and _DC-873321_ . The right panel of Figure A.1
shows a comparison of the _T_ _e_ and strong-line based metallicity measurements for these five galaxies. We find a good
agreement between these independent measurements within the uncertainties, suggesting that our strong-line metal
abundance estimates are reasonable.


B. DETAILS ON MASS-LOADING FACTOR



The outflow properties, specifically the mass-loading factor ( _ϵ_ out ), is closely linked to the evolution of galaxies.
In our model, the outflow of metal-rich gas significantly affects the overall predicted metallicity. Importantly, the
mass-dependence of _ϵ_ out relates to the steepness of the MZR.
Here, we use the characterization of _ϵ_ out ( _M, z_ ) as found in the EAGLE simulation (J. Schaye et al. 2015; R. A.
Crain et al. 2015), specifically as presented in figure 3 of P. D. Mitchell et al. (2020). To be able to use this result in
our model, we derived an analytical representation in the form of a double power-law as follows:

_M_ ˙ wind _,_ ISM
� ˙ � _≡_ _ϵ_ out = _ξ_ _[−]_ [1] ( _M_ _⋆_ _, z_ ) _,_ (B1)

_M_ _⋆_
� �


with


_ϕ_ _[∗]_ ( _z_ )
_ξ_ ( _M_ _⋆_ _, z_ ) = 10 [(] _[δ]_ [+1)] _[×]_ [(log(] _[M]_ _[s]_ _[tar]_ [)] _[−M]_ [)] + 10 [(] _[γ]_ [+1)] _[×]_ [(log(] _[M]_ _[s]_ _[tar]_ [)] _[−M]_ [)] _[,]_ (B2)


where we define _ϕ_ _[∗]_ ( _z_ ) = 10 [1] _[.]_ [1] _[−]_ [(1+] _[z]_ [)] [0] _[.]_ [09], _M_ ( _z_ ) = 8 _._ 2+(1+ _z_ ) [0] _[.]_ [29], _δ_ ( _z_ ) = _−_ 0 _._ 4 _−_ (1+ _z_ ) [0] _[.]_ [02], and _γ_ ( _z_ ) = 0 _._ 05 _−_ (1+ _z_ ) [0] _[.]_ [01] .
We find that this parameterization gives consistent results to A. L. Muratov et al. (2015), which is based on the
FIRE simulation (P. F. Hopkins et al. 2014).
Figure B.3 compares this theoretical mass-loading factor to observations. The red hatched region shows the approximate area of the observed mass-loading factors of the ALPINE galaxies (M. Ginolfi et al. 2020; J. E. Birkin et al.
2025). The blue circles show the location of local starburst from T. M. Heckman et al. (2015) and the turquoise star
denotes the measurement for _HZ4_ at _z_ _∼_ 5 from R. Herrera-Camus et al. (2021). Most of the local starbursts as well as
_HZ4_ are consistent with the nominal mass-loading factor derived from the EAGLE simulation. However, the ALPINE
galaxies are more consistent with an outflow efficiency reduced by a factor of two. Interestingly, such a reduction of

21


#### 1.2 1.0 0.8 0.6 0.4 0.2 0.0 0.2 0.4






|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|EAGL|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||~~EAGL~~|~~EAGL~~|~~EAGL~~|~~E Simulation:~~||
||||||||||||||||<br>out(M)|z = 5<br>1<br>~~×~~<br>~~(M)|~~||
||||||||||||||||<br>out(M)|z = 5<br>1<br>~~×~~<br>~~(M)|~~||
||||||||||||||||<br>out(M)|z = 5<br>1<br>~~×~~<br>~~(M)|~~||
||||||||||||||||<br>out(M)|z = 5<br>1<br>~~×~~<br>~~(M)|~~||
||||||||||||||||2 <br>outz = 5||
||||||||||||||||||
||||||||||||||||||
||||||||||||||**Other S**<br>**ASTR**|**Other S**<br>**ASTR**|** imulations:**<br>**AEUS (Ucci+23)**||
||||||||||||||**Other S**<br>**ASTR**|**Other S**<br>**ASTR**|** imulations:**<br>**AEUS (Ucci+23)**||
||||||||||||||**Other S**<br>**ASTR**|**Other S**<br>**ASTR**|** imulations:**<br>**AEUS (Ucci+23)**||
||||||||||||||**Other S**<br>**ASTR**|**Other S**<br>**ASTR**|** imulations:**<br>**AEUS (Ucci+23)**||
|||||||||||||**FIRE-**|**FIRE-**|**FIRE-**|**2 (Pandya+21)**||
|||||||||||||**FIRE-**|**FIRE-**|**FIRE-**|**2 (Pandya+21)**||
|||||||||||||**FIRE-**|**FIRE-**|**FIRE-**|||
|||||||||||||**FIRE-**|**FIRE-**|**FIRE-**|||
||||||||||||||||||
||||ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~||
||||ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~|ALPINE (z<br>5)<br>~~(Ginolfi+20)~~||||||||
||||HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|+21)|||||||||
||||HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|+21)|||||||||
||||HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|+21)|||||||||
||||HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|HZ4 (z<br>5)<br>(Herrera-Camus|+21)|||||||||
||||Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~||||||||||
||||Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~||||||||||
||||Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~||||||||||
||||Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~|Local Starbursts<br>(Heckman+15)<br>~~CRISTAL (z~~<br>~~5)~~||||||||||
||||<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|.5)|||||||||
||||<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|.5)|||||||||
||||<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|.5)|||||||||
||||<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|<br><br>(Birkin+25)<br>UC-10646 (z<br>8<br>|.5)|||||||||
||||~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~||||||||||
||||~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~|~~(Algera+25)~~||||||||||
||||||||||||||||||


#### 8 9 10 11 12

### log(M/M )

**Figure** **B.3.** Parameterization of the mass-loading factor _ϵ_ out (Equation B1) derived by the EAGLE simulation (figure 3; P. D.
Mitchell et al. 2020). The light gray curve show the nominal outflow efficiency from EAGLE. The dark gray curve shows a
two-times reduced outflow efficiency. Also shown are results from the ASTRAEUS (green dashed line; G. Ucci et al. 2023) and
FIRE-2 (orange line; V. Pandya et al. 2021). We compare this to observations at _z_ _∼_ 5 of the ALPINE sample (red hatched
square; M. Ginolfi et al. 2020), CRISTAL (purple diamond; J. E. Birkin et al. 2025), and _HZ4_ (turquoise star; R. Herrera-Camus
et al. 2021), as well as local starbursts (blue circles; T. M. Heckman et al. 2015) and a _z_ _∼_ 8 _._ 5 galaxy (pink hexagon; H. S. B.
Algera et al. 2025). Note that the ALPINE sample is more consistent with a reduced outflow efficiency, which is also preferred
to reproduce the MZR (Figure 4).


the outflow efficiency is also preferred to reproduce the MZR of _z_ _∼_ 5 galaxies (Figure 4). This has also been noticed
in A. Pallottini et al. (2025) and S. Carniani et al. (2024). We note that the simulated mass-loading factors may be
inferred differently compared to the observations which could cause this discrepancy (e.g., E. Pizzati et al. 2020; S.
Carniani et al. 2024).


REFERENCES



Abazajian, K. N., Adelman-McCarthy, J. K., Ag¨ueros,


M. A., et al. 2009, ApJS, 182, 543,


doi: [10.1088/0067-0049/182/2/543](http://doi.org/10.1088/0067-0049/182/2/543)


Alam, S., Albareti, F. D., Allende Prieto, C., et al. 2015,


ApJS, 219, 12, doi: [10.1088/0067-0049/219/1/12](http://doi.org/10.1088/0067-0049/219/1/12)


Algera, H. S. B., Weaver, J. R., Bakx, T. J. L. C., et al.


2025, arXiv e-prints, arXiv:2512.14486,


doi: [10.48550/arXiv.2512.14486](http://doi.org/10.48550/arXiv.2512.14486)


Allende Prieto, C., Lambert, D. L., & Asplund, M. 2001,


ApJL, 556, L63, doi: [10.1086/322874](http://doi.org/10.1086/322874)



Andrews, B. H., & Martini, P. 2013, ApJ, 765, 140,


doi: [10.1088/0004-637X/765/2/140](http://doi.org/10.1088/0004-637X/765/2/140)


Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999,


MNRAS, 310, 540, doi: [10.1046/j.1365-8711.1999.02978.x](http://doi.org/10.1046/j.1365-8711.1999.02978.x)


Asada, Y., Sawicki, M., Abraham, R., et al. 2023, arXiv


e-prints, arXiv:2310.02314,


doi: [10.48550/arXiv.2310.02314](http://doi.org/10.48550/arXiv.2310.02314)


Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009,


ARA&A, 47, 481,


doi: [10.1146/annurev.astro.46.060407.145222](http://doi.org/10.1146/annurev.astro.46.060407.145222)

22


Astropy Collaboration, Robitaille, T. P., Tollerud, E. J.,

et al. 2013, A&A, 558, A33,

doi: [10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)

Astropy Collaboration, Price-Whelan, A. M., Sip˝ocz, B. M.,
et al. 2018, AJ, 156, 123, doi: [10.3847/1538-3881/aabc4f](http://doi.org/10.3847/1538-3881/aabc4f)

Astropy Collaboration, Price-Whelan, A. M., Lim, P. L.,
et al. 2022, ApJ, 935, 167, doi: [10.3847/1538-4357/ac7c74](http://doi.org/10.3847/1538-4357/ac7c74)

Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981,

PASP, 93, 5, doi: [10.1086/130766](http://doi.org/10.1086/130766)

Baugh, C. M., Gonzalez-Perez, V., Lagos, C. D. P., et al.
2019, MNRAS, 483, 4922, doi: [10.1093/mnras/sty3427](http://doi.org/10.1093/mnras/sty3427)

Berg, D. A., Skillman, E. D., Marble, A. R., et al. 2012,
ApJ, 754, 98, doi: [10.1088/0004-637X/754/2/98](http://doi.org/10.1088/0004-637X/754/2/98)

Bergemann, M., Hoppe, R., Semenova, E., et al. 2021,
MNRAS, 508, 2236, doi: [10.1093/mnras/stab2160](http://doi.org/10.1093/mnras/stab2160)

B´ethermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020,

A&A, 643, A2, doi: [10.1051/0004-6361/202037649](http://doi.org/10.1051/0004-6361/202037649)

Birkin, J. E., Spilker, J. S., Herrera-Camus, R., et al. 2025,

ApJ, 985, 243, doi: [10.3847/1538-4357/adced3](http://doi.org/10.3847/1538-4357/adced3)

Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A,
622, A103, doi: [10.1051/0004-6361/201834156](http://doi.org/10.1051/0004-6361/201834156)

Boylan-Kolchin, M., Springel, V., White, S. D. M., Jenkins,

A., & Lemson, G. 2009, MNRAS, 398, 1150,

doi: [10.1111/j.1365-2966.2009.15191.x](http://doi.org/10.1111/j.1365-2966.2009.15191.x)

Breneman, J. A., McQuinn, K. B. W., Menchaca, A., et al.

2025, ApJ, 991, 191, doi: [10.3847/1538-4357/adf84b](http://doi.org/10.3847/1538-4357/adf84b)

Burgarella, D., Buat, V., & Iglesias-P´aramo, J. 2005,

MNRAS, 360, 1413,

doi: [10.1111/j.1365-2966.2005.09131.x](http://doi.org/10.1111/j.1365-2966.2005.09131.x)

Burgarella, D., Buat, V., Theul´e, P., et al. 2025, A&A, 699,
A336, doi: [10.1051/0004-6361/202554231](http://doi.org/10.1051/0004-6361/202554231)

Caplar, N., & Tacchella, S. 2019, MNRAS, 487, 3845,

doi: [10.1093/mnras/stz1449](http://doi.org/10.1093/mnras/stz1449)

Carniani, S., Venturi, G., Parlanti, E., et al. 2024, A&A,

685, A99, doi: [10.1051/0004-6361/202347230](http://doi.org/10.1051/0004-6361/202347230)

Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2022,

arXiv e-prints, arXiv:2211.07865,

doi: [10.48550/arXiv.2211.07865](http://doi.org/10.48550/arXiv.2211.07865)

Ceverino, D., Glover, S. C. O., & Klessen, R. S. 2017,

MNRAS, 470, 2791, doi: [10.1093/mnras/stx1386](http://doi.org/10.1093/mnras/stx1386)

Ceverino, D., Nakazato, Y., Yoshida, N., et al. 2026, arXiv

e-prints, arXiv:2603.05045,

doi: [10.48550/arXiv.2603.05045](http://doi.org/10.48550/arXiv.2603.05045)
Chabrier, G. 2003, PASP, 115, 763, doi: [10.1086/376392](http://doi.org/10.1086/376392)

Christensen, L., Laursen, P., Richard, J., et al. 2012a,

MNRAS, 427, 1973,

doi: [10.1111/j.1365-2966.2012.22007.x](http://doi.org/10.1111/j.1365-2966.2012.22007.x)

Christensen, L., Richard, J., Hjorth, J., et al. 2012b,

MNRAS, 427, 1953,

doi: [10.1111/j.1365-2966.2012.22006.x](http://doi.org/10.1111/j.1365-2966.2012.22006.x)



Ciesla, L., Elbaz, D., Ilbert, O., et al. 2024, A&A, 686,

A128, doi: [10.1051/0004-6361/202348091](http://doi.org/10.1051/0004-6361/202348091)


Connolly, S. D. 2016, DELightcurveSimulation: Light curve

simulation code,, Astrophysics Source Code Library,

record ascl:1602.012 [http://ascl.net/1602.012](http://ascl.net/1602.012)


Crain, R. A., Schaye, J., Bower, R. G., et al. 2015,

MNRAS, 450, 1937, doi: [10.1093/mnras/stv725](http://doi.org/10.1093/mnras/stv725)


Cullen, F., McLure, R. J., Dunlop, J. S., et al. 2019,

MNRAS, 487, 2038, doi: [10.1093/mnras/stz1402](http://doi.org/10.1093/mnras/stz1402)


Cullen, F., Carnall, A. C., Scholte, D., et al. 2025, MNRAS,

540, 2176, doi: [10.1093/mnras/staf838](http://doi.org/10.1093/mnras/staf838)


Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020,

MNRAS, 491, 944, doi: [10.1093/mnras/stz2910](http://doi.org/10.1093/mnras/stz2910)


Curti, M., D’Eugenio, F., Carniani, S., et al. 2023,

MNRAS, 518, 425, doi: [10.1093/mnras/stac2737](http://doi.org/10.1093/mnras/stac2737)


Curti, M., Maiolino, R., Curtis-Lake, E., et al. 2024, A&A,

684, A75, doi: [10.1051/0004-6361/202346698](http://doi.org/10.1051/0004-6361/202346698)


Daflon, S., & Cunha, K. 2004, ApJ, 617, 1115,

doi: [10.1086/425607](http://doi.org/10.1086/425607)


Dav´e, R., Finlator, K., & Oppenheimer, B. D. 2012,

MNRAS, 421, 98, doi: [10.1111/j.1365-2966.2011.20148.x](http://doi.org/10.1111/j.1365-2966.2011.20148.x)

Davies, R. L., F¨orster Schreiber, N. M., Ubler, [¨] H., et al.

2019, ApJ, 873, 122, doi: [10.3847/1538-4357/ab06f1](http://doi.org/10.3847/1538-4357/ab06f1)


Dayal, P., Ferrara, A., & Dunlop, J. S. 2013, MNRAS, 430,

2891, doi: [10.1093/mnras/stt083](http://doi.org/10.1093/mnras/stt083)


De Lucia, G., Fontanot, F., Xie, L., & Hirschmann, M.

2024, A&A, 687, A68, doi: [10.1051/0004-6361/202349045](http://doi.org/10.1051/0004-6361/202349045)


De Lucia, G., Tornatore, L., Frenk, C. S., et al. 2014,

MNRAS, 445, 970, doi: [10.1093/mnras/stu1752](http://doi.org/10.1093/mnras/stu1752)


De Lucia, G., Xie, L., Fontanot, F., & Hirschmann, M.

2020, MNRAS, 498, 3215, doi: [10.1093/mnras/staa2556](http://doi.org/10.1093/mnras/staa2556)


Dekel, A., & Mandelker, N. 2014, MNRAS, 444, 2071,

doi: [10.1093/mnras/stu1427](http://doi.org/10.1093/mnras/stu1427)


Dell’Agli, F., Valiante, R., Kamath, D., Ventura, P., &

Garc´ıa-Hern´andez, D. A. 2019, MNRAS, 486, 4738,

doi: [10.1093/mnras/stz1164](http://doi.org/10.1093/mnras/stz1164)


Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020,

A&A, 643, A5, doi: [10.1051/0004-6361/202038231](http://doi.org/10.1051/0004-6361/202038231)


Dubois, Y., Volonteri, M., & Silk, J. 2014, MNRAS, 440,

1590, doi: [10.1093/mnras/stu373](http://doi.org/10.1093/mnras/stu373)


Dubois, Y., Beckmann, R., Bournaud, F., et al. 2021, A&A,

651, A109, doi: [10.1051/0004-6361/202039429](http://doi.org/10.1051/0004-6361/202039429)


Elia, D., Molinari, S., Schisano, E., et al. 2022, ApJ, 941,

162, doi: [10.3847/1538-4357/aca27d](http://doi.org/10.3847/1538-4357/aca27d)


Ellison, S. L., Patton, D. R., Simard, L., & McConnachie,

A. W. 2008, AJ, 135, 1877,

doi: [10.1088/0004-6256/135/5/1877](http://doi.org/10.1088/0004-6256/135/5/1877)


Emami, N., Siana, B., Weisz, D. R., et al. 2019, ApJ, 881,

71, doi: [10.3847/1538-4357/ab211a](http://doi.org/10.3847/1538-4357/ab211a)

Emmanoulopoulos, D., McHardy, I. M., & Papadakis, I. E.

2013, MNRAS, 433, 907, doi: [10.1093/mnras/stt764](http://doi.org/10.1093/mnras/stt764)


Endsley, R., Chisholm, J., Stark, D. P., Topping, M. W., &

Whitler, L. 2024, arXiv e-prints, arXiv:2410.01905,

doi: [10.48550/arXiv.2410.01905](http://doi.org/10.48550/arXiv.2410.01905)


Faisst, A. L., Capak, P. L., Emami, N., Tacchella, S., &

Larson, K. L. 2019, ApJ, 884, 133,

doi: [10.3847/1538-4357/ab425b](http://doi.org/10.3847/1538-4357/ab425b)


Faisst, A. L., & Morishita, T. 2024, ApJ, 971, 47,

doi: [10.3847/1538-4357/ad58e2](http://doi.org/10.3847/1538-4357/ad58e2)


Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020,

ApJS, 247, 61, doi: [10.3847/1538-4365/ab7ccd](http://doi.org/10.3847/1538-4365/ab7ccd)


Faisst, A. L., Fujimoto, S., Tsujita, A., et al. 2026, ApJS,

282, 19, doi: [10.3847/1538-4365/ae0928](http://doi.org/10.3847/1538-4365/ae0928)


Faucher-Gigu`ere, C.-A. 2018, MNRAS, 473, 3717,

doi: [10.1093/mnras/stx2595](http://doi.org/10.1093/mnras/stx2595)


Faucher-Gigu`ere, C.-A., Quataert, E., & Hopkins, P. F.

2013, MNRAS, 433, 1970, doi: [10.1093/mnras/stt866](http://doi.org/10.1093/mnras/stt866)


Feldmann, R. 2015, MNRAS, 449, 3274,

doi: [10.1093/mnras/stv552](http://doi.org/10.1093/mnras/stv552)


Fontanot, F., De Lucia, G., Hirschmann, M., et al. 2020,

MNRAS, 496, 3943, doi: [10.1093/mnras/staa1716](http://doi.org/10.1093/mnras/staa1716)


Fontanot, F., La Barbera, F., De Lucia, G., et al. 2024,

A&A, 686, A302, doi: [10.1051/0004-6361/202348688](http://doi.org/10.1051/0004-6361/202348688)


Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887,

107, doi: [10.3847/1538-4357/ab480f](http://doi.org/10.3847/1538-4357/ab480f)


Fujimoto, S., Faisst, A. L., Tsujita, A., et al. 2025, arXiv

e-prints, arXiv:2510.16116,

doi: [10.48550/arXiv.2510.16116](http://doi.org/10.48550/arXiv.2510.16116)


Furlanetto, S. R., & Mirocha, J. 2022, MNRAS, 511, 3895,

doi: [10.1093/mnras/stac310](http://doi.org/10.1093/mnras/stac310)


Garaldi, E., Kannan, R., Smith, A., et al. 2022, MNRAS,

512, 4909, doi: [10.1093/mnras/stac257](http://doi.org/10.1093/mnras/stac257)


Ginolfi, M., Jones, G. C., B´ethermin, M., et al. 2020, A&A,

633, A90, doi: [10.1051/0004-6361/201936872](http://doi.org/10.1051/0004-6361/201936872)


Guo, Y., Koo, D. C., Lu, Y., et al. 2016, ApJ, 822, 103,

doi: [10.3847/0004-637X/822/2/103](http://doi.org/10.3847/0004-637X/822/2/103)


Heckman, T. M., Alexandroff, R. M., Borthakur, S.,

Overzier, R., & Leitherer, C. 2015, ApJ, 809, 147,

doi: [10.1088/0004-637X/809/2/147](http://doi.org/10.1088/0004-637X/809/2/147)


Heintz, K. E., Brammer, G. B., Watson, D., et al. 2025,

A&A, 693, A60, doi: [10.1051/0004-6361/202450243](http://doi.org/10.1051/0004-6361/202450243)


Henry, A., Rafelski, M., Sunnquist, B., et al. 2021, ApJ,

919, 143, doi: [10.3847/1538-4357/ac1105](http://doi.org/10.3847/1538-4357/ac1105)


Herrera-Camus, R., F¨orster Schreiber, N., Genzel, R., et al.

2021, A&A, 649, A31, doi: [10.1051/0004-6361/202039704](http://doi.org/10.1051/0004-6361/202039704)


Herrera-Camus, R., Gonz´alez-L´opez, J., F¨orster Schreiber,

N., et al. 2025, arXiv e-prints, arXiv:2505.06340,

doi: [10.48550/arXiv.2505.06340](http://doi.org/10.48550/arXiv.2505.06340)



23


Hirschmann, M., Charlot, S., & Somerville, R. S. 2023,

MNRAS, 526, 3504, doi: [10.1093/mnras/stad2745](http://doi.org/10.1093/mnras/stad2745)


Hirschmann, M., De Lucia, G., & Fontanot, F. 2016,

MNRAS, 461, 1760, doi: [10.1093/mnras/stw1318](http://doi.org/10.1093/mnras/stw1318)


Hopkins, P. F., Kereˇs, D., O˜norbe, J., et al. 2014, MNRAS,

445, 581, doi: [10.1093/mnras/stu1738](http://doi.org/10.1093/mnras/stu1738)


Hopkins, P. F., Wetzel, A., Kereˇs, D., et al. 2018, MNRAS,

480, 800, doi: [10.1093/mnras/sty1690](http://doi.org/10.1093/mnras/sty1690)


Hopkins, P. F., Wetzel, A., Wheeler, C., et al. 2023,

MNRAS, 519, 3154, doi: [10.1093/mnras/stac3489](http://doi.org/10.1093/mnras/stac3489)


Hsiao, T. Y.-Y., Sun, F., Lin, X., et al. 2025, arXiv e-prints,

arXiv:2505.03873, doi: [10.48550/arXiv.2505.03873](http://doi.org/10.48550/arXiv.2505.03873)


Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A,

457, 841, doi: [10.1051/0004-6361:20065138](http://doi.org/10.1051/0004-6361:20065138)


Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023, ApJ, 951,

102, doi: [10.3847/1538-4357/accc87](http://doi.org/10.3847/1538-4357/accc87)


Izotov, Y. I., Thuan, T. X., & Guseva, N. G. 2019,

MNRAS, 483, 5491, doi: [10.1093/mnras/sty3472](http://doi.org/10.1093/mnras/sty3472)


Izotov, Y. I., Thuan, T. X., Guseva, N. G., & Liss, S. E.

2018, MNRAS, 473, 1956, doi: [10.1093/mnras/stx2478](http://doi.org/10.1093/mnras/stx2478)


Kannan, R., Garaldi, E., Smith, A., et al. 2022, MNRAS,

511, 4005, doi: [10.1093/mnras/stab3710](http://doi.org/10.1093/mnras/stab3710)


Kannan, R., Marinacci, F., Vogelsberger, M., et al. 2020,

MNRAS, 499, 5732, doi: [10.1093/mnras/staa3249](http://doi.org/10.1093/mnras/staa3249)


Kannan, R., Vogelsberger, M., Marinacci, F., et al. 2021,

MNRAS, 503, 336, doi: [10.1093/mnras/stab416](http://doi.org/10.1093/mnras/stab416)


Kannan, R., Puchwein, E., Smith, A., et al. 2025, arXiv

e-prints, arXiv:2502.20437,

doi: [10.48550/arXiv.2502.20437](http://doi.org/10.48550/arXiv.2502.20437)


Karachentsev, I. D., Makarova, L. N., Koribalski, B. S.,

et al. 2023, MNRAS, 518, 5893,

doi: [10.1093/mnras/stac3284](http://doi.org/10.1093/mnras/stac3284)


Kashino, D., Silverman, J. D., Rodighiero, G., et al. 2013,

ApJL, 777, L8, doi: [10.1088/2041-8205/777/1/L8](http://doi.org/10.1088/2041-8205/777/1/L8)


Kashino, D., Silverman, J. D., Sanders, D., et al. 2017,

ApJ, 835, 88, doi: [10.3847/1538-4357/835/1/88](http://doi.org/10.3847/1538-4357/835/1/88)


Katz, H., Liu, S., Kimm, T., et al. 2022, arXiv e-prints,

arXiv:2211.04626, doi: [10.48550/arXiv.2211.04626](http://doi.org/10.48550/arXiv.2211.04626)


Katz, H., Rosdahl, J., Kimm, T., et al. 2023, arXiv e-prints,

arXiv:2309.03269, doi: [10.48550/arXiv.2309.03269](http://doi.org/10.48550/arXiv.2309.03269)


Kennicutt, Robert C., J. 1998, ApJ, 498, 541,

doi: [10.1086/305588](http://doi.org/10.1086/305588)


Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019,

ARA&A, 57, 511,

doi: [10.1146/annurev-astro-081817-051832](http://doi.org/10.1146/annurev-astro-081817-051832)


Khusanova, Y., Bethermin, M., Le F`evre, O., et al. 2021,

A&A, 649, A152, doi: [10.1051/0004-6361/202038944](http://doi.org/10.1051/0004-6361/202038944)


Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007,

ApJS, 172, 196, doi: [10.1086/520086](http://doi.org/10.1086/520086)

24


Kojima, T., Ouchi, M., Rauch, M., et al. 2020, ApJ, 898,

142, doi: [10.3847/1538-4357/aba047](http://doi.org/10.3847/1538-4357/aba047)


Korhonen Cuestas, N. A., Strom, A. L., Miller, T. B., et al.

2025, arXiv e-prints, arXiv:2503.10800,

doi: [10.48550/arXiv.2503.10800](http://doi.org/10.48550/arXiv.2503.10800)


Kriek, M., Shapley, A. E., Reddy, N. A., et al. 2015, ApJS,

218, 15, doi: [10.1088/0067-0049/218/2/15](http://doi.org/10.1088/0067-0049/218/2/15)


Krumholz, M. R., & Dekel, A. 2012, ApJ, 753, 16,

doi: [10.1088/0004-637X/753/1/16](http://doi.org/10.1088/0004-637X/753/1/16)


Lapi, A., Mancuso, C., Celotti, A., & Danese, L. 2017, ApJ,

835, 37, doi: [10.3847/1538-4357/835/1/37](http://doi.org/10.3847/1538-4357/835/1/37)


Lapi, A., Pantoni, L., Boco, L., & Danese, L. 2020, ApJ,

897, 81, doi: [10.3847/1538-4357/ab9812](http://doi.org/10.3847/1538-4357/ab9812)


Lara-L´opez, M. A., Cepa, J., Bongiovanni, A., et al. 2010,

A&A, 521, L53, doi: [10.1051/0004-6361/201014803](http://doi.org/10.1051/0004-6361/201014803)


Laseter, I. H., Barger, A. J., Cowie, L. L., & Taylor, A. J.

2022, ApJ, 935, 150, doi: [10.3847/1538-4357/ac81c7](http://doi.org/10.3847/1538-4357/ac81c7)


Le F`evre, O., B´ethermin, M., Faisst, A., et al. 2020, A&A,

643, A1, doi: [10.1051/0004-6361/201936965](http://doi.org/10.1051/0004-6361/201936965)


Licquia, T. C., & Newman, J. A. 2015, ApJ, 806, 96,

doi: [10.1088/0004-637X/806/1/96](http://doi.org/10.1088/0004-637X/806/1/96)


Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng,

Y. 2013, ApJ, 772, 119,

doi: [10.1088/0004-637X/772/2/119](http://doi.org/10.1088/0004-637X/772/2/119)


Limongi, M., & Chieffi, A. 2018, ApJS, 237, 13,

doi: [10.3847/1538-4365/aacb24](http://doi.org/10.3847/1538-4365/aacb24)


Liu, L.-J., Sun, G., Chang, T.-C., Furlanetto, S. R., &

Bradford, C. M. 2024, ApJ, 974, 175,

doi: [10.3847/1538-4357/ad73d5](http://doi.org/10.3847/1538-4357/ad73d5)


Liu, L.-J., Sun, G., Faisst, A. L., Faucher-Gigu`ere, C.-A., &

Lidz, A. 2026, arXiv e-prints, arXiv:2601.00959,

doi: [10.48550/arXiv.2601.00959](http://doi.org/10.48550/arXiv.2601.00959)


Lopez, F., X, X., & et al. 2025, in prep, ApJ


Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A,

573, A42, doi: [10.1051/0004-6361/201323152](http://doi.org/10.1051/0004-6361/201323152)


Ma, X., Hopkins, P. F., Faucher-Gigu`ere, C.-A., et al. 2016,

MNRAS, 456, 2140, doi: [10.1093/mnras/stv2659](http://doi.org/10.1093/mnras/stv2659)


Ma, X., Hopkins, P. F., Boylan-Kolchin, M., et al. 2018a,

MNRAS, 477, 219, doi: [10.1093/mnras/sty684](http://doi.org/10.1093/mnras/sty684)


Ma, X., Hopkins, P. F., Garrison-Kimmel, S., et al. 2018b,

MNRAS, 478, 1694, doi: [10.1093/mnras/sty1024](http://doi.org/10.1093/mnras/sty1024)


Ma, X., Hayward, C. C., Casey, C. M., et al. 2019,

MNRAS, 487, 1844, doi: [10.1093/mnras/stz1324](http://doi.org/10.1093/mnras/stz1324)


Maier, C., Lilly, S. J., Ziegler, B. L., et al. 2014, ApJ, 792,

3, doi: [10.1088/0004-637X/792/1/3](http://doi.org/10.1088/0004-637X/792/1/3)


Maiolino, R., & Mannucci, F. 2019, A&A Rv, 27, 3,

doi: [10.1007/s00159-018-0112-2](http://doi.org/10.1007/s00159-018-0112-2)


Maiolino, R., Nagao, T., Grazian, A., et al. 2008, A&A,

488, 463, doi: [10.1051/0004-6361:200809678](http://doi.org/10.1051/0004-6361:200809678)



Mannucci, F., Cresci, G., Maiolino, R., Marconi, A., &

Gnerucci, A. 2010, MNRAS, 408, 2115,

doi: [10.1111/j.1365-2966.2010.17291.x](http://doi.org/10.1111/j.1365-2966.2010.17291.x)


Marinacci, F., Sales, L. V., Vogelsberger, M., Torrey, P., &

Springel, V. 2019, MNRAS, 489, 4233,

doi: [10.1093/mnras/stz2391](http://doi.org/10.1093/mnras/stz2391)


Marinacci, F., Vogelsberger, M., Pakmor, R., et al. 2018,

MNRAS, 480, 5113, doi: [10.1093/mnras/sty2206](http://doi.org/10.1093/mnras/sty2206)


Marszewski, A., Sun, G., Faucher-Gigu`ere, C.-A., Hayward,

C. C., & Feldmann, R. 2024, ApJL, 967, L41,

doi: [10.3847/2041-8213/ad4cee](http://doi.org/10.3847/2041-8213/ad4cee)


Mehta, V., Teplitz, H. I., Scarlata, C., et al. 2023, ApJ,

952, 133, doi: [10.3847/1538-4357/acd9cf](http://doi.org/10.3847/1538-4357/acd9cf)


Mitchell, P. D., Schaye, J., Bower, R. G., & Crain, R. A.

2020, MNRAS, 494, 3971, doi: [10.1093/mnras/staa938](http://doi.org/10.1093/mnras/staa938)


Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2024, A&A,

690, A197, doi: [10.1051/0004-6361/202348782](http://doi.org/10.1051/0004-6361/202348782)

Moll´a, M., D´ıaz, A. [´] I., Cavichia, O., et al. 2019, MNRAS,

482, 3071, doi: [10.1093/mnras/sty2877](http://doi.org/10.1093/mnras/sty2877)


Morishita, T., Liu, Z., Stiavelli, M., et al. 2025, arXiv

e-prints, arXiv:2507.10521,

doi: [10.48550/arXiv.2507.10521](http://doi.org/10.48550/arXiv.2507.10521)


Morishita, T., Stiavelli, M., Grillo, C., et al. 2024, ApJ,

971, 43, doi: [10.3847/1538-4357/ad5290](http://doi.org/10.3847/1538-4357/ad5290)


Mu˜noz, J. B., Mirocha, J., Furlanetto, S., & Sabti, N. 2023,

MNRAS, 526, L47, doi: [10.1093/mnrasl/slad115](http://doi.org/10.1093/mnrasl/slad115)


Muratov, A. L., Kereˇs, D., Faucher-Gigu`ere, C.-A., et al.

2015, MNRAS, 454, 2691, doi: [10.1093/mnras/stv2126](http://doi.org/10.1093/mnras/stv2126)


Nagao, T., Maiolino, R., & Marconi, A. 2006, A&A, 459,

85, doi: [10.1051/0004-6361:20065216](http://doi.org/10.1051/0004-6361:20065216)


Naiman, J. P., Pillepich, A., Springel, V., et al. 2018,

MNRAS, 477, 1206, doi: [10.1093/mnras/sty618](http://doi.org/10.1093/mnras/sty618)


Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269,

33, doi: [10.3847/1538-4365/acd556](http://doi.org/10.3847/1538-4365/acd556)


Nakajima, K., Ouchi, M., Harikane, Y., et al. 2025, arXiv

e-prints, arXiv:2506.11846,

doi: [10.48550/arXiv.2506.11846](http://doi.org/10.48550/arXiv.2506.11846)


Nakazato, Y., Yoshida, N., & Ceverino, D. 2023, ApJ, 953,

140, doi: [10.3847/1538-4357/ace25a](http://doi.org/10.3847/1538-4357/ace25a)


Navarro-Carrera, R., Rinaldi, P., Caputi, K. I., et al. 2024,

arXiv e-prints, arXiv:2410.23249,

doi: [10.48550/arXiv.2410.23249](http://doi.org/10.48550/arXiv.2410.23249)


Nelson, D., Pillepich, A., Springel, V., et al. 2018, MNRAS,

475, 624, doi: [10.1093/mnras/stx3040](http://doi.org/10.1093/mnras/stx3040)


Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS,

490, 3234, doi: [10.1093/mnras/stz2306](http://doi.org/10.1093/mnras/stz2306)


Nishigaki, M., Ouchi, M., Nakajima, K., et al. 2023, ApJ,

952, 11, doi: [10.3847/1538-4357/accf14](http://doi.org/10.3847/1538-4357/accf14)


Oke, J. B. 1974, ApJS, 27, 21, doi: [10.1086/190287](http://doi.org/10.1086/190287)

Onodera, M., Carollo, C. M., Lilly, S., et al. 2016, ApJ,
822, 42, doi: [10.3847/0004-637X/822/1/42](http://doi.org/10.3847/0004-637X/822/1/42)

Osman, O., De Lucia, G., Fontanot, F., Xie, L., &

Hirschmann, M. 2025, arXiv e-prints, arXiv:2512.15902,

doi: [10.48550/arXiv.2512.15902](http://doi.org/10.48550/arXiv.2512.15902)

Pagel, B. E. J. 1997, Nucleosynthesis and Chemical

Evolution of Galaxies

Pallottini, A., Ferrara, A., Gallerani, S., et al. 2025, A&A,

699, A6, doi: [10.1051/0004-6361/202451742](http://doi.org/10.1051/0004-6361/202451742)

Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022,

MNRAS, 513, 5621, doi: [10.1093/mnras/stac1281](http://doi.org/10.1093/mnras/stac1281)

Pandya, V., Fielding, D. B., Angl´es-Alc´azar, D., et al. 2021,
MNRAS, 508, 2979, doi: [10.1093/mnras/stab2714](http://doi.org/10.1093/mnras/stab2714)

Pantoni, L., Lapi, A., Massardi, M., Goswami, S., &

Danese, L. 2019, ApJ, 880, 129,

doi: [10.3847/1538-4357/ab2adc](http://doi.org/10.3847/1538-4357/ab2adc)

Papovich, C., Simons, R. C., Estrada-Carpenter, V., et al.

2022, ApJ, 937, 22, doi: [10.3847/1538-4357/ac8058](http://doi.org/10.3847/1538-4357/ac8058)

P´erez-Montero, E., Contini, T., Lamareille, F., et al. 2013,

A&A, 549, A25, doi: [10.1051/0004-6361/201220070](http://doi.org/10.1051/0004-6361/201220070)

P´eroux, C., & Howk, J. C. 2020, ARA&A, 58, 363,

doi: [10.1146/annurev-astro-021820-120014](http://doi.org/10.1146/annurev-astro-021820-120014)

Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59,
doi: [10.1111/j.1365-2966.2004.07591.x](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

Pillepich, A., Nelson, D., Hernquist, L., et al. 2018,

MNRAS, 475, 648, doi: [10.1093/mnras/stx3112](http://doi.org/10.1093/mnras/stx3112)

Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS,
490, 3196, doi: [10.1093/mnras/stz2338](http://doi.org/10.1093/mnras/stz2338)

Pilyugin, L. S., Thuan, T. X., & V´ılchez, J. M. 2006,

MNRAS, 367, 1139,

doi: [10.1111/j.1365-2966.2006.10033.x](http://doi.org/10.1111/j.1365-2966.2006.10033.x)

Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, MNRAS,

495, 160, doi: [10.1093/mnras/staa1163](http://doi.org/10.1093/mnras/staa1163)

Planck Collaboration, Ade, P. A. R., Aghanim, N., et al.
2014, A&A, 571, A16, doi: [10.1051/0004-6361/201321591](http://doi.org/10.1051/0004-6361/201321591)

Pollock, C. L., Gottumukkala, R., Heintz, K. E., et al. 2026,

A&A, 708, A203, doi: [10.1051/0004-6361/202556032](http://doi.org/10.1051/0004-6361/202556032)

Portinari, L., Chiosi, C., & Bressan, A. 1998, A&A, 334,

505, doi: [10.48550/arXiv.astro-ph/9711337](http://doi.org/10.48550/arXiv.astro-ph/9711337)

Pustilnik, S. A., Egorova, E. S., Kniazev, A. Y., et al. 2021,
MNRAS, 507, 944, doi: [10.1093/mnras/stab2084](http://doi.org/10.1093/mnras/stab2084)

Pustilnik, S. A., Kniazev, A. Y., Perepelitsyna, Y. A., &

Egorova, E. S. 2020, MNRAS, 493, 830,
doi: [10.1093/mnras/staa215](http://doi.org/10.1093/mnras/staa215)

Ren, W., Silverman, J. D., Faisst, A. L., et al. 2025,

MNRAS, 544, 211, doi: [10.1093/mnras/staf1709](http://doi.org/10.1093/mnras/staf1709)

Roberts-Borsani, G., Treu, T., Shapley, A., et al. 2024,
ApJ, 976, 193, doi: [10.3847/1538-4357/ad85d3](http://doi.org/10.3847/1538-4357/ad85d3)

Rosdahl, J., Katz, H., Blaizot, J., et al. 2018, MNRAS, 479,

994, doi: [10.1093/mnras/sty1655](http://doi.org/10.1093/mnras/sty1655)



25


Rosdahl, J., Blaizot, J., Katz, H., et al. 2022, MNRAS, 515,

2386, doi: [10.1093/mnras/stac1942](http://doi.org/10.1093/mnras/stac1942)


Rowland, L. E., Stefanon, M., Bouwens, R., et al. 2025,

arXiv e-prints, arXiv:2501.10559,

doi: [10.48550/arXiv.2501.10559](http://doi.org/10.48550/arXiv.2501.10559)


Rudie, G. C., Steidel, C. C., Trainor, R. F., et al. 2012,

ApJ, 750, 67, doi: [10.1088/0004-637X/750/1/67](http://doi.org/10.1088/0004-637X/750/1/67)


Salim, S., Lee, J. C., Dav´e, R., & Dickinson, M. 2015, ApJ,

808, 25, doi: [10.1088/0004-637X/808/1/25](http://doi.org/10.1088/0004-637X/808/1/25)


S´anchez, S. F., Barrera-Ballesteros, J. K.,

S´anchez-Menguiano, L., et al. 2017, MNRAS, 469, 2121,

doi: [10.1093/mnras/stx808](http://doi.org/10.1093/mnras/stx808)


S´anchez Almeida, J., Morales-Luis, A. B., Mu˜noz-Tu˜n´on,

C., et al. 2014, ApJ, 783, 45,

doi: [10.1088/0004-637X/783/1/45](http://doi.org/10.1088/0004-637X/783/1/45)


S´anchez Almeida, J., Elmegreen, B. G., Mu˜noz-Tu˜n´on, C.,

et al. 2015, ApJL, 810, L15,

doi: [10.1088/2041-8205/810/2/L15](http://doi.org/10.1088/2041-8205/810/2/L15)


Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy,

N. A., & Brammer, G. B. 2024, ApJ, 962, 24,

doi: [10.3847/1538-4357/ad15fc](http://doi.org/10.3847/1538-4357/ad15fc)


Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2015, ApJ,

799, 138, doi: [10.1088/0004-637X/799/2/138](http://doi.org/10.1088/0004-637X/799/2/138)


Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2018, ApJ,

858, 99, doi: [10.3847/1538-4357/aabcbd](http://doi.org/10.3847/1538-4357/aabcbd)


Sanders, R. L., Shapley, A. E., Jones, T., et al. 2021, ApJ,

914, 19, doi: [10.3847/1538-4357/abf4c1](http://doi.org/10.3847/1538-4357/abf4c1)


Sanders, R. L., Shapley, A. E., Topping, M. W., et al. 2025,

arXiv e-prints, arXiv:2508.10099,

doi: [10.48550/arXiv.2508.10099](http://doi.org/10.48550/arXiv.2508.10099)


Sarkar, A., Chakraborty, P., Vogelsberger, M., et al. 2025,

ApJ, 978, 136, doi: [10.3847/1538-4357/ad8f32](http://doi.org/10.3847/1538-4357/ad8f32)


Schaye, J., Crain, R. A., Bower, R. G., et al. 2015,

MNRAS, 446, 521, doi: [10.1093/mnras/stu2058](http://doi.org/10.1093/mnras/stu2058)


Scholte, D., Cullen, F., Carnall, A. C., et al. 2025, MNRAS,

540, 1800, doi: [10.1093/mnras/staf834](http://doi.org/10.1093/mnras/staf834)


Scholtz, J., Maiolino, R., D’Eugenio, F., et al. 2025, A&A,

697, A175, doi: [10.1051/0004-6361/202348804](http://doi.org/10.1051/0004-6361/202348804)


Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172,

1, doi: [10.1086/516585](http://doi.org/10.1086/516585)


Scoville, N., Faisst, A., Weaver, J., et al. 2023, ApJ, 943,

82, doi: [10.3847/1538-4357/aca1bc](http://doi.org/10.3847/1538-4357/aca1bc)


Senchyna, P., Stark, D. P., Chevallard, J., et al. 2019,

MNRAS, 488, 3492, doi: [10.1093/mnras/stz1907](http://doi.org/10.1093/mnras/stz1907)


Shen, X., Vogelsberger, M., Boylan-Kolchin, M., Tacchella,

S., & Kannan, R. 2023, MNRAS, 525, 3254,

doi: [10.1093/mnras/stad2508](http://doi.org/10.1093/mnras/stad2508)


Shi, Y., Armus, L., Helou, G., et al. 2014, Nature, 514, 335,

doi: [10.1038/nature13820](http://doi.org/10.1038/nature13820)

26


Shuntov, M., Ilbert, O., Toft, S., et al. 2025, A&A, 695,

A20, doi: [10.1051/0004-6361/202452570](http://doi.org/10.1051/0004-6361/202452570)

Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015,
ApJL, 812, L23, doi: [10.1088/2041-8205/812/2/L23](http://doi.org/10.1088/2041-8205/812/2/L23)

Smith, A., Kannan, R., Garaldi, E., et al. 2022, MNRAS,

512, 3243, doi: [10.1093/mnras/stac713](http://doi.org/10.1093/mnras/stac713)

Springel, V., White, S. D. M., Jenkins, A., et al. 2005,
Nature, 435, 629, doi: [10.1038/nature03597](http://doi.org/10.1038/nature03597)

Springel, V., Pakmor, R., Pillepich, A., et al. 2018,
MNRAS, 475, 676, doi: [10.1093/mnras/stx3304](http://doi.org/10.1093/mnras/stx3304)

Stanton, T. M., Cullen, F., McLure, R. J., et al. 2024,

MNRAS, 532, 3102, doi: [10.1093/mnras/stae1705](http://doi.org/10.1093/mnras/stae1705)

Stanton, T. M., Cullen, F., Carnall, A. C., et al. 2026,

MNRAS, doi: [10.1093/mnras/stag449](http://doi.org/10.1093/mnras/stag449)

Steidel, C. C., Rudie, G. C., Strom, A. L., et al. 2014, ApJ,

795, 165, doi: [10.1088/0004-637X/795/2/165](http://doi.org/10.1088/0004-637X/795/2/165)

Strom, A. L., Rudie, G. C., Steidel, C. C., & Trainor, R. F.

2022, ApJ, 925, 116, doi: [10.3847/1538-4357/ac38a3](http://doi.org/10.3847/1538-4357/ac38a3)

Strom, A. L., Steidel, C. C., Rudie, G. C., et al. 2017, ApJ,

836, 164, doi: [10.3847/1538-4357/836/2/164](http://doi.org/10.3847/1538-4357/836/2/164)

Sui, J., Zou, H., Scholte, D., et al. 2026, arXiv e-prints,

arXiv:2603.05934, doi: [10.48550/arXiv.2603.05934](http://doi.org/10.48550/arXiv.2603.05934)

Sun, G., Mu˜noz, J. B., Mirocha, J., & Faucher-Gigu`ere,

C.-A. 2025, JCAP, 2025, 034,

doi: [10.1088/1475-7516/2025/04/034](http://doi.org/10.1088/1475-7516/2025/04/034)

Tinsley, B. M. 1980, FCPh, 5, 287,
doi: [10.48550/arXiv.2203.02041](http://doi.org/10.48550/arXiv.2203.02041)

Topping, M. W., Shapley, A. E., Sanders, R. L., et al. 2021,
MNRAS, 506, 1237, doi: [10.1093/mnras/stab1793](http://doi.org/10.1093/mnras/stab1793)

Topping, M. W., Sanders, R. L., Shapley, A. E., et al. 2025,
MNRAS, 541, 1707, doi: [10.1093/mnras/staf903](http://doi.org/10.1093/mnras/staf903)



Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al.

2004, ApJ, 613, 898, doi: [10.1086/423264](http://doi.org/10.1086/423264)


Tsujita, A., Fujimoto, S., Faisst, A., et al. 2026, ApJ, 997,

319, doi: [10.3847/1538-4357/ae22d8](http://doi.org/10.3847/1538-4357/ae22d8)


Ucci, G., Dayal, P., Hutter, A., et al. 2023, MNRAS, 518,

3557, doi: [10.1093/mnras/stac2654](http://doi.org/10.1093/mnras/stac2654)


Vanzella, E., Loiacono, F., Bergamini, P., et al. 2023, A&A,

678, A173, doi: [10.1051/0004-6361/202346981](http://doi.org/10.1051/0004-6361/202346981)


Wang, W., Faisst, A. L., Finner, K., et al. 2026, arXiv

e-prints, arXiv:2602.20241,

doi: [10.48550/arXiv.2602.20241](http://doi.org/10.48550/arXiv.2602.20241)


Weisz, D. R., Johnson, B. D., Johnson, L. C., et al. 2012,

ApJ, 744, 44, doi: [10.1088/0004-637X/744/1/44](http://doi.org/10.1088/0004-637X/744/1/44)


Welch, B., Rivera-Thorsen, T. E., Rigby, J. R., et al. 2025,

ApJ, 980, 33, doi: [10.3847/1538-4357/ada76c](http://doi.org/10.3847/1538-4357/ada76c)


Willott, C. J., Asada, Y., Iyer, K. G., et al. 2025, ApJ, 988,

26, doi: [10.3847/1538-4357/addf49](http://doi.org/10.3847/1538-4357/addf49)


Wuyts, E., Kurk, J., F¨orster Schreiber, N. M., et al. 2014,

ApJL, 789, L40, doi: [10.1088/2041-8205/789/2/L40](http://doi.org/10.1088/2041-8205/789/2/L40)


Xie, L., De Lucia, G., Hirschmann, M., & Fontanot, F.

2020, MNRAS, 498, 4327, doi: [10.1093/mnras/staa2370](http://doi.org/10.1093/mnras/staa2370)


Yabe, K., Ohta, K., Iwamuro, F., et al. 2014, MNRAS, 437,

3647, doi: [10.1093/mnras/stt2185](http://doi.org/10.1093/mnras/stt2185)


Yang, S., Lidz, A., Li, H., et al. 2025, arXiv e-prints,

arXiv:2504.18006, doi: [10.48550/arXiv.2504.18006](http://doi.org/10.48550/arXiv.2504.18006)


Zahid, H. J., Dima, G. I., Kudritzki, R.-P., et al. 2014a,

ApJ, 791, 130, doi: [10.1088/0004-637X/791/2/130](http://doi.org/10.1088/0004-637X/791/2/130)


Zahid, H. J., Kashino, D., Silverman, J. D., et al. 2014b,

ApJ, 792, 75, doi: [10.1088/0004-637X/792/1/75](http://doi.org/10.1088/0004-637X/792/1/75)

**All** **Authors** **and** **Affiliations**


Andreas [L.](http://orcid.org/0000-0002-9382-9832) Faisst, [1] [Lun-Jun](http://orcid.org/0009-0004-1270-2373) Liu, [2] Yohan [Dubois](http://orcid.org/0000-0003-0225-6387), [3] Yurina [Nakazato](http://orcid.org/0000-0002-0984-7713), [4, 5] Omima [Osman](http://orcid.org/0009-0001-5733-8307), [6, 7]

Andrea [Pallottini](http://orcid.org/0000-0002-7129-5761), [8] Livia [Vallini](http://orcid.org/0000-0002-3258-3672), [9] Seiji [Fujimoto](http://orcid.org/0000-0001-7201-5066), [10, 11] Bahram [Mobasher](http://orcid.org/0000-0001-5846-4404), [12] Wuji [Wang](http://orcid.org/0000-0002-7964-6749), [1]

[Yu-Heng](http://orcid.org/0000-0001-8792-3091) Lin, [1] Ricardo [O.](http://orcid.org/0000-0001-5758-1000) Amor´ın, [13, 14] Manuel [Aravena](http://orcid.org/0000-0002-6290-3198), [15, 16] R. J. [Assef](http://orcid.org/0000-0002-9508-3667), [15]

Andrew J. Battisti, [17, 18, 19] Matthieu [B´ethermin](http://orcid.org/0000-0002-3915-2015), [20] M´ed´eric [Boquien](http://orcid.org/0000-0003-0946-6176), [21] Paolo [Cassata](http://orcid.org/0000-0002-6716-4400), [22, 23]

Elisabete [da](http://orcid.org/0000-0001-9759-4797) Cunha, [17, 19] [Poulomi](http://orcid.org/0009-0007-7842-9930) Dam, [22] Gabriella [de](http://orcid.org/0000-0002-6220-9104) Lucia, [6, 24] Ilse De [Looze](http://orcid.org/0000-0001-9419-6355), [25]

Miroslava [Dessauges-Zavadsky](http://orcid.org/0000-0003-0348-2917), [26] Andrea [Ferrara](http://orcid.org/0000-0002-9400-7312), [27] Kyle [Finner](http://orcid.org/0000-0002-4462-0709), [1] Fabio [Fontanot](http://orcid.org/0000-0003-4744-0188), [6, 24]

Michele [Ginolfi](http://orcid.org/0000-0002-9122-1700), [28, 29] Diego A. [G´omez-Espinoza](http://orcid.org/0009-0008-1835-7557), [30] Carlotta [Gruppioni](http://orcid.org/0000-0002-5836-4056), [9]

Nicol [Guti´errez-Vera](http://orcid.org/0009-0005-8932-7783), [31, 16] Ali [Hadi](http://orcid.org/0009-0003-3097-6733), [12] Rodrigo [Herrera-Camus](http://orcid.org/0000-0002-2775-0595), [31, 16] Michaela [Hirschmann](http://orcid.org/0000-0002-3301-3321), [32]

[Eduardo](http://orcid.org/0009-0008-9801-2224) Ibar, [30, 16] Hanae [Inami](http://orcid.org/0000-0003-4268-0393), [33] Jeyhan S. [Kartaltepe](http://orcid.org/0000-0001-9187-3605), [34] Anton M. [Koekemoer](http://orcid.org/0000-0002-6610-2048), [35]

Mahsa [Kohandel](http://orcid.org/0000-0003-1041-7865), [27] Lilian [L.](http://orcid.org/0000-0001-7457-4371) Lee, [36] Yuan Li, [37] Juan [Molina](http://orcid.org/0000-0002-8136-8127), [30, 16] Ambra [Nanni](http://orcid.org/0000-0001-6652-1069), [38, 39]

Desika [Narayanan](http://orcid.org/0000-0002-7064-4309), [40, 41] [Francesca](http://orcid.org/0000-0002-7412-647X) Pozzi, [42, 9] Monica [Relano](http://orcid.org/0000-0003-1682-1148), [43, 44] Michael [Romano](http://orcid.org/0000-0002-9948-3916), [45, 23]

David B. [Sanders](http://orcid.org/0000-0002-1233-9998), [46] John D. [Silverman](http://orcid.org/0000-0002-0000-6977), [47, 48, 49, 50] Laura [Sommovigo](http://orcid.org/0000-0002-2906-2200), [4] Justin [Spilker](http://orcid.org/0000-0003-3256-5615), [37]

Akiyoshi [Tsujita](http://orcid.org/0000-0002-0498-5041), [51] Hannah [Ubler](http://orcid.org/0000-0003-4891-0794) [¨], [36] Keerthi [Vasan](http://orcid.org/0000-0002-2645-679X) G.C., [52] Enrico [Veraldi](http://orcid.org/0009-0007-1304-7771), [53]

Vincente [Villanueva](http://orcid.org/0000-0002-5877-379X), [31] Lizhi [Xie](http://orcid.org/0000-0003-3864-068X) 54 And Gianni [Zamorani](http://orcid.org/0000-0002-2318-301X) 9


(Affiliations can be found after the references)


1 _IPAC,_ _California_ _Institute_ _of_ _Technology,_ _1200_ _E._ _California_ _Blvd._ _Pasadena,_ _CA_ _91125,_ _USA_
2 _Physics_ _Department,_ _California_ _Institute_ _of_ _Technology,_ _1200_ _E_ _California_ _Blvd,_ _Pasadena,_ _CA_ _91125,_ _USA_
3 _Institut_ _d’Astrophysique_ _de_ _Paris,_ _UMR_ _7095,_ _CNRS,_ _Sorbonne_ _Universit´e,_ _98_ _bis_ _boulevard_ _Arago,_ _75014_ _Paris,_ _France_
4 _Center_ _for_ _Computational_ _Astrophysics,_ _Flatiron_ _Institute,_ _162_ _5th_ _Avenue,_ _New_ _York,_ _NY_ _10010,_ _USA_
5 _Department_ _of_ _Physics,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
6 _INAF_ _-_ _Astronomical_ _Observatory_ _of_ _Trieste,_ _via_ _G.B._ _Tiepolo_ _11,_ _I-34143_ _Trieste,_ _Italy_
7 _University_ _of_ _Khartoum_ _-_ _Department_ _of_ _Physics,_ _Al-Gamaa_ _Ave,_ _11115_ _Khartoum,_ _Sudan_
8 _Dipartimento_ _di_ _Fisica_ _“Enrico_ _Fermi”,_ _Universit´a_ _di_ _Pisa,_ _Largo_ _Bruno_ _Pontecorvo_ _3,_ _Pisa_ _I-56127,_ _Italy_
9 _INAF_ _–_ _Osservatorio_ _di_ _Astrofisica_ _e_ _Scienza_ _dello_ _Spazio_ _di_ _Bologna,_ _Via_ _Gobetti_ _93/3,_ _40129_ _Bologna,_ _Italy_
10 _Department_ _of_ _Astronomy,_ _The_ _University_ _of_ _Texas_ _at_ _Austin,_ _Austin,_ _TX_ _78712,_ _USA_
11 _David_ _A._ _Dunlap_ _Department_ _of_ _Astronomy_ _and_ _Astrophysics,_ _University_ _of_ _Toronto,_ _50_ _St._ _George_ _Street,_ _Toronto,_ _Ontario,_ _M5S_
_3H4,_ _Canada_
12 _Department_ _of_ _Physics_ _and_ _Astronomy,_ _University_ _of_ _California,_ _Riverside,_ _900_ _University_ _Avenue,_ _Riverside,_ _CA_ _92521,_ _USA_
13 _Instituto_ _de_ _Investigaci`on_ _Multidisciplinar_ _en_ _Ciencia_ _y_ _Tecnolog´ıa,_ _Universidad_ _de_ _La_ _Serena,_ _Ra´ul_ _Bitr´an_ _1305,_ _La_ _Serena,_ _Chile_
14 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _La_ _Serena,_ _Av._ _Juan_ _Cisternas_ _1200_ _Norte,_ _La_ _Serena,_ _Chile_
15 _Instituto_ _de_ _Estudios_ _Astrof´ısicos,_ _Facultad_ _de_ _Ingenier´ıa_ _y_ _Ciencias,_ _Universidad_ _Diego_ _Portales,_ _Av._ _Ej´ercito_ _Libertador_ _441,_
_Santiago_ _8370191,_ _Chile_
16 _Millenium_ _Nucleus_ _for_ _Galaxies_ _(MINGAL),_ _Av._ _Ej´ercito_ _441,_ _Santiago_ _8370191,_ _Chile_
17 _International_ _Centre_ _for_ _Radio_ _Astronomy_ _Research_ _(ICRAR),_ _The_ _University_ _of_ _Western_ _Australia,_ _M468,_ _35_ _Stirling_ _Highway,_
_Crawley,_ _WA_ _6009,_ _Australia_
18 _Research_ _School_ _of_ _Astronomy_ _and_ _Astrophysics,_ _Australian_ _National_ _University,_ _Cotter_ _Road,_ _Weston_ _Creek,_ _ACT_ _2611,_ _Australia_
19 _ARC_ _Center_ _of_ _Excellence_ _for_ _All_ _Sky_ _Astrophysics_ _in_ _3_ _Dimensions_ _(ASTRO_ _3D),_ _Australia_
20 _Universit´e_ _de_ _Strasbourg,_ _CNRS,_ _Observatoire_ _astronomique_ _de_ _Strasbourg,_ _UMR_ _7550,_ _67000_ _Strasbourg,_ _France_
21 _Universit´e_ _Cˆote_ _d’Azur,_ _Observatoire_ _de_ _la_ _Cˆote_ _d’Azur,_ _CNRS,_ _Laboratoire_ _Lagrange,_ _06000,_ _Nice,_ _France_
22 _Dipartimento_ _di_ _Fisica_ _e_ _Astronomia_ _Galileo_ _Galilei_ _Universit`a_ _degli_ _Studi_ _di_ _Padova,_ _Vicolo_ _dell’Osservatorio_ _3,_ _35122_ _Padova_ _Italy_
23 _INAF_ _-_ _Osservatorio_ _Astronomico_ _di_ _Padova,_ _Vicolo_ _dell’Osservatorio_ _5,_ _I-35122,_ _Padova,_ _Italy_
24 _IFPU_ _-_ _Institute_ _for_ _Fundamental_ _Physics_ _of_ _the_ _Universe,_ _via_ _Beirut_ _2,_ _34151,_ _Trieste,_ _Italy_
25 _Sterrenkundig_ _Observatorium,_ _Ghent_ _University,_ _Krijgslaan_ _281_ _-_ _S9,_ _B-9000_ _Gent,_ _Belgium_
26 _Observatoire_ _de_ _Gen`eve,_ _Universit´e_ _de_ _Gen`eve,_ _Chemin_ _Pegasi_ _51,_ _1290_ _Versoix,_ _Switzerland_
27 _Scuola_ _Normale_ _Superiore,_ _Piazza_ _dei_ _Cavalieri_ _7,_ _I-56126_ _Pisa,_ _Italy_
28 _Universit`a_ _di_ _Firenze,_ _Dipartimento_ _di_ _Fisica_ _e_ _Astronomia,_ _via_ _G._ _Sansone_ _1,_ _50019_ _Sesto_ _Fiorentino,_ _Florence,_ _Italy_
29 _INAF_ _—_ _Arcetri_ _Astrophysical_ _Observatory,_ _Largo_ _E._ _Fermi_ _5,_ _I-50125,_ _Florence,_ _Italy_
30 _Instituto_ _de_ _F´ısica_ _y_ _Astronom´ıa,_ _Universidad_ _de_ _Valpara´ıso,_ _Avda._ _Gran_ _Breta˜na_ _1111,_ _Valpara´ıso,_ _Chile_
31 _Departamento_ _de_ _Astronom´ıa,_ _Universidad_ _de_ _Concepci´on,_ _Barrio_ _Universitario,_ _Concepci´on,_ _Chile_
32 _Institute_ _of_ _Physics,_ _Laboratory_ _for_ _galaxy_ _evolution,_ _EPFL,_ _Observatoire_ _de_ _Sauverny,_ _Chemin_ _Pegasi_ _51,_ _1290_ _Versoix,_ _Switzerland_
33 _Hiroshima_ _Astrophysical_ _Science_ _Center,_ _Hiroshima_ _University,_ _1-3-1_ _Kagamiyama,_ _Higashi-Hiroshima,_ _Hiroshima_ _739-8526,_ _Japan_
34 _Laboratory_ _for_ _Multiwavelength_ _Astrophysics,_ _School_ _of_ _Physics_ _and_ _Astronomy,_ _Rochester_ _Institute_ _of_ _Technology,_ _84_ _Lomb_ _Memorial_
_Drive,_ _Rochester,_ _NY_ _14623,_ _USA_

28


35 _Space_ _Telescope_ _Science_ _Institute,_ _3700_ _San_ _Martin_ _Dr.,_ _Baltimore,_ _MD_ _21218,_ _USA_
36 _Max-Planck-Institute_ _f¨ur_ _extratarrestrische_ _Physik,_ _Giessenbachstrasse_ _1,_ _85748_ _Garching,_ _Germany_
37 _Department_ _of_ _Physics_ _and_ _Astronomy_ _and_ _George_ _P._ _and_ _Cynthia_ _Woods_ _Mitchell_ _Institute_ _for_ _Fundamental_ _Physics_ _and_ _Astronomy,_
_Texas_ _A&M_ _University,_ _4242_
38 _National_ _Centre_ _for_ _Nuclear_ _Research,_ _ul._ _Pasteura_ _7,_ _02-093_ _Warsaw,_ _Poland_
39 _INAF_ _-_ _Osservatorio_ _astronomico_ _d’Abruzzo,_ _Via_ _Maggini_ _SNC,_ _64100,_ _Teramo,_ _Italy_
40 _Department_ _of_ _Astronomy,_ _University_ _of_ _Florida,_ _211_ _Bryant_ _Space_ _Sciences_ _Center,_ _Gainesville,_ _FL_ _32611,_ _USA_
41 _Cosmic_ _Dawn_ _Center_ _(DAWN),_ _Copenhagen,_ _Denmark_
42 _Dipartimento_ _di_ _Fisica_ _e_ _Astronomia_ _“Augusto_ _Righi”,_ _Alma_ _Mater_ _Studiorum,_ _Universi´a_ _di_ _Bologna,_ _Via_ _Gobetti_ _93/2,_ _40129_
_Bologna,_ _Italy_
43 _Dept._ _F´ısica_ _Te´orica_ _y_ _del_ _Cosmos,_ _Campus_ _de_ _Fuentenueva,_ _Edificio_ _Mecenas,_ _Universidad_ _de_ _Granada,_ _E-18071,_ _Granada,_ _Spain_
44 _Instituto_ _Universitario_ _Carlos_ _I_ _de_ _F´ısica_ _Te´orica_ _y_ _Computacional,_ _Universidad_ _de_ _Granada,_ _18071,_ _Granada,_ _Spain_
45 _Max-Planck-Institut_ _f¨ur_ _Radioastronomie,_ _Auf_ _dem_ _H¨ugel_ _69,_ _53121_ _Bonn,_ _Germany_
46 _Institute_ _for_ _Astronomy,_ _University_ _of_ _Hawaii,_ _2680_ _Woodlawn_ _Drive,_ _Honolulu,_ _HI_ _96822,_ _USA_
47 _Kavli_ _Institute_ _for_ _the_ _Physics_ _and_ _Mathematics_ _of_ _the_ _Universe_ _(Kavli_ _IPMU,_ _WPI),_ _UTIAS,_ _Tokyo_ _Institutes_ _for_ _Advanced_ _Study,_
_University_ _of_ _Tokyo,_ _Chiba,_ _277-8583,_ _Japan_
48 _Department_ _of_ _Astronomy,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _7-3-1_ _Hongo,_ _Bunkyo,_ _Tokyo_ _113-0033,_ _Japan_
49 _Center_ _for_ _Data-Driven_ _Discovery,_ _Kavli_ _IPMU_ _(WPI),_ _UTIAS,_ _The_ _University_ _of_ _Tokyo,_ _Kashiwa,_ _Chiba_ _277-8583,_ _Japan_
50 _Center_ _for_ _Astrophysical_ _Sciences,_ _Department_ _of_ _Physics_ _&_ _Astronomy,_ _Johns_ _Hopkins_ _University,_ _Baltimore,_ _MD_ _21218,_ _USA_
51 _Institute_ _of_ _Astronomy,_ _Graduate_ _School_ _of_ _Science,_ _The_ _University_ _of_ _Tokyo,_ _2-21-1_ _Osawa,_ _Mitaka,_ _Tokyo_ _181-0015,_ _Japan_
52 _The_ _Observatories_ _of_ _the_ _Carnegie_ _Institution_ _for_ _Science,_ _813_ _Santa_ _Barbara_ _Street,_ _Pasadena,_ _CA_ _91101,_ _USA_
53 _Scuola_ _Internazionale_ _Superiore_ _Studi_ _Avanzati_ _(SISSA),_ _Physics_ _Area,_ _Via_ _Bonomea_ _265,_ _34136_ _Trieste,_ _Italy_
54 _Tianjin_ _Normal_ _University,_ _Binshuixidao_ _393,_ _300387,_ _Tianjin,_ _China_


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[1]",
  "value": "paper type: multi_facility_alma_minor",
  "failed_quote": "Notably, all galaxies also have ALMA observations of [C II ] 158 _µ_ m and far-IR continuum at comparable resolution to JWST spectroscopy to jointly study the stars, gas, and dust at this epoch."
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "[C II]",
  "failed_quote": "Notably, all galaxies also have ALMA observations of [C II ] 158 _µ_ m and far-IR continuum at comparable resolution to JWST spectroscopy to jointly study the stars, gas, and dust at this epoch."
 },
 {
  "path": "data.simulations_or_models_as_data[5].evidence[1]",
  "value": "DUSTY-GAEA semi-analytic model run on Millennium, Millennium II, and Planck Millennium (PMILL) merger trees",
  "failed_quote": "We therefore compared the progenitor tracks to _∼_ 400 galaxies from the Planck Millennium simulation ( `PMILL` ; C. M. Baugh et al. 2019)."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Integrate continuity equations forward in time with AGB and Type II SNe yields, EAGLE-derived mass-loading factors, and stochastic SFHs generated with DELightcurveSimulation; compare MZR/FMR with cosmological simulations and trace progenitors/descendants in DUSTY-GAEA.",
  "failed_quote": "Specifically, we use the `DELightcurveSimulation` Python package (S. D. Connolly 2016), which is based on the D. Emmanoulopoulos et al. (2013) light-curve simulation algorithm."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "t_depl = 5 x 10^8 yr, Mdot_gas,in = 100 Msun yr^-1, R = 0.46, r_Z = 0 to 0.5",
  "failed_quote": "assuming reasonable average values of _t_ depl = 5 _×_ 10 [8] yr (e.g., M. Dessauges-Zavadsky et al. 2020) and accretion rates _M_ ˙ gas _,_ in = 100 M _⊙_ yr _[−]_ [1] (e.g., N. Scoville et al. 2023)."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[1]",
  "value": "Z_sun ~ 0.014, AGB yields for 1-7 Msun (Dell'Agli et al. 2019), SNe II yields for 7-120 Msun (Limongi & Chieffi 2018)",
  "failed_quote": "We include stars in the range of 1 _−_ 7 M _⊙_ for AGB yields and 7 _−_ 120 M _⊙_ for SNe II yields and use their mass dependent lifetimes given in L. Portinari et al. (1998)."
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Compared analytical model ages with observed SED-fit ages and compared DUSTY-GAEA Millennium merger tree tracks with higher-resolution Planck Millennium (PMILL) simulation.",
  "failed_quote": "We therefore compared the progenitor tracks to _∼_ 400 galaxies from the Planck Millennium simulation ( `PMILL` ; C. M. Baugh et al. 2019)."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "General astronomy tools and utilities",
  "failed_quote": "This work made use of Astropy: a community developed core Python package and an ecosystem of tools and resources for astronomy ( Astropy Collaboration et al. 2013, 2018, 2022)."
 },
 {
  "path": "software[3].used_for.evidence[0]",
  "value": "Simulating stochastic (bursty) star formation histories",
  "failed_quote": "Specifically, we use the `DELightcurveSimulation` Python package (S. D. Connolly 2016), which is based on the D. Emmanoulopoulos et al. (2013) light-curve simulation algorithm."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "While z ~ 5 galaxies roughly follow the local FMR to first order, the 5x larger, non-reducible downward scatter challenges the universality of a tight equilibrium FMR at z = 5.",
  "failed_quote": "The intrinsic FMR scatter is _σ_ FMR = _σ_ FMR [2] _[−]_ _[σ]_ meas [2] _[∼]_ [0] _[.]_ [10] _[ −]_ [0] _[.]_ [13 dex,] for _µ_ 0 = 0 _._ 22 _−_ 0 _._ 66"
 }
]
```
