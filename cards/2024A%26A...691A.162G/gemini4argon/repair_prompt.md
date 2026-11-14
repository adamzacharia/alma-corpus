# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A.162G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. draft ©ESO 2024
September 10, 2024

## **The Galaxy Activity, Torus, and Outflow Survey (GATOS). V:** **Unveiling PAH survival and resilience in the circumnuclear regions** **of AGN with JWST**


I. García-Bernete [1][,][ 2,][⋆], D. Rigopoulou [2][,][ 3], F. R. Donnan [2], A. Alonso-Herrero [1], M. Pereira-Santella [4], T. Shimizu [5], R.
Davies [5], P. F. Roche [2], S. García-Burillo [6], A. Labiano [1][,][ 7], L. Hermosa Muñoz [1], L. Zhang [8], A. Audibert [9][,][ 10], E.
Bellocchi [11][,][ 12], A. Bunker [2], F. Combes [13], D. Delaney [14], D. Esparza-Arredondo [9][,][ 10], P. Gandhi [15], O. González-Martín [16],
S.F. Hönig [15], M. Imanishi [17][,][ 18], E. K. S. Hicks [14][,][ 8], L. Fuller [8], M. Leist, [8], N. A. Levenson [19], E. Lopez-Rodriguez [20], C.
Packham [8][,][ 17], C. Ramos Almeida [9][,][ 10], C. Ricci [21], M. Stalevski [22][,][ 23], M. Villar Martín [24] and M. J. Ward [25]


_(A_ ffi _liations can be found after the references)_


**ABSTRACT**


We analyze _JWST_ MIRI/MRS observations of the infrared Polycyclic Aromatic Hydrocarbon (PAH) bands in the nuclear (∼0.4 [′′] at 11 µm; ∼75 pc)
and circumnuclear regions (inner ∼kpc) of local Active Galactic Nuclei (AGN) from the Galactic Activity, Torus and Outflow Survey (GATOS).
In this work, we examine the PAH properties in the circumnuclear regions of AGN and the projected direction of AGN-outflows, and compare
them to those in star-forming regions and the innermost regions of AGN. This study employs 4.9-28.1 µm sub-arcsecond angular resolution data
to investigate the properties of PAH in three nearby sources (D L ∼30-40 Mpc). Our findings align with previous JWST studies, showing that the
central regions of AGN show a larger fraction of neutral PAH molecules (i.e. elevated 11.3/6.2 and 11.3/7.7 µm PAH ratios) compared to starforming galaxies. We find that the AGN might affect not only the PAH population in the innermost region but also in the extended regions up to

∼
kpc scales. By comparing our observations to PAH diagnostic diagrams, we find that, in general, regions located in the projected direction of the
AGN-outflow occupy similar positions on the PAH diagnostic diagrams as those of the innermost regions of AGN. Star-forming regions that are
not affected by the AGN in these galaxies share the same part of the diagram as Star-forming galaxies. We examine the potential of the PAH-H 2
diagram to disentangle AGN versus star-forming activity. Our results suggest that in Seyfert-like AGN, illumination and feedback from the AGN
might affect the PAH population at nuclear and kpc scales, in particular, the ionization state of the PAH grains. However, PAH molecular sizes are
rather similar. The carriers of the ionized PAH bands (6.2 and 7.7 µm) are less resilience than those of neutral PAH bands (11.3 µm), which might
be particularly important for strongly AGN-host coupled systems. Therefore, caution must be applied when using PAH bands as star-formation
rate indicators in these systems even at kpc scales, with the ionized ones being more affected by the AGN.


**Key words.** galaxies: active - galaxies: nuclei – galaxies: Seyfert – techniques: spectroscopic – techniques: high angular resolution.



**1.** **Introduction**


The impact of the energy released by Active Galactic Nuclei
(AGN) in their surrounding environment has been proposed as
a key mechanism for regulating star formation (SF) in their host
galaxies. AGN feedback is needed in cosmological simulations
to reproduce the observed number of massive galaxies through
the quenching of star formation (e.g., Croton et al. 2006; Bongiorno et al. 2016). A significant fraction of AGN positive and/or
negative feedback occurs at circumnuclear scales (inner hundreds of pc) in local active galaxies, where large amounts of dust
and gas are located, surrounding the AGN (Antonucci 1993).
ALMA observations detected the molecular dusty torus in several nearby AGN and showed that it is part of the galaxy gas flow
cycle (e.g. García-Burillo et al. 2016, 2019, 2021, 2024; AlonsoHerrero et al. 2018; Imanishi et al. 2018, 2020 and references
therein).
The dust surrounding the central engine absorbs a significant
part of the AGN radiation and then reprocesses it to emerge in
the infrared (IR; e.g. Pier & Krolik 1992). In these dusty environments, optical wavelengths are also heavily affected by dust
obscuration making the IR an ideal spectral range to investigate
the inner regions of AGN (see Ramos Almeida & Ricci 2017


⋆ E-mail: igbernete@gmail.com



for a review). Luminous quasi-stellar objects (QSOs; log L bol

[erg s [−][1] ]≳10 [46] ) are the most powerful AGN, but their key coupling mechanisms remain generally spatially unresolved, except
for nearby sources (e.g. Jarvis et al. 2021, Ramos Almeida et al.
2022). Mid-IR subarcsecond angular observations (<0.5 [′′] ) of local AGN (at distances of ∼tens of Mpc) enable us to probe their
nuclear/circumnuclear regions (inner ∼100 pc scales). There is
also evidence that the circumnuclear dusty material observed in
local AGN is not different in properties such as temperature to
those in distant and luminous QSOs (e.g. Bosman et al. 2023).
Therefore, the study of local AGN also contribute to our better
understanding of distant AGN.


Polycyclic aromatic hydrocarbons (PAHs) are particles at the
smaller end of the interstellar medium (ISM) dust distribution.
PAHs are ubiquitous in local sources (see e.g. Li 2020 for a
review), but also in high-z galaxies (e.g. Spilker et al. 2023).
PAH molecules and dust grains play a key role by catalysing
and enriching the ISM with organic molecules, and in the photoelectric heating of the ISM (Tielens 2005, 2021). These PAH
molecules absorb a significant fraction of UV/optical photons
from (mainly) young stars (e.g. Peeters, Spoon & Tielens 2004),
and partially from old stars when present (e.g. Kaneda et al.
2008; Li & Draine 2002; Zhang & Ho 2023a; Ogle et al. 2024),
resulting in their excitation. The excited PAH molecules pro

Article number, page 1 of 21

_A&A proofs:_ manuscript no. draft



duce IR features (the brightest bands are 3.3, 6.2, 7.7, 8.6, 11.3,
12.7, and 17.0 µm; e.g. Tielens 2008) through vibrational relaxation (e.g. Draine & Li 2007). Thus, PAH features are considered excellent tracers of the star formation activity in starforming galaxies (e.g. Rigopoulou et al. 1999; Peeters, Spoon &
Tielens 2004), but also in AGN (e.g. Diamond-Stanic & Rieke
2012). The 3.3, 11.3, 12.7 and 17 µm bands are attributed to
neutral PAH molecules, whereas 6.2 and 7.7 µm bands originate
mostly from ionized PAH molecules (e.g. Allamandola, Tielens
& Barker 1989; Draine & Li 2001; Draine et al. 2021). Using
10-m class ground-based telescopes and N-band (7.5-13µm) observations, nuclear 11.3 µm PAH emission (few tens of pc) has
been detected in local AGN (e.g. Hönig et al. 2010; GonzálezMartín et al. 2013; Sales et al. 2013; Alonso-Herrero et al. 2014,
2016; Esquej et al. 2014; Ramos Almeida et al. 2014, 2023;
Ruschel-Dutra et al. 2014; García-Bernete et al. 2015, 2019,
2022c; Martínez-Paredes et al. 2015, 2019; Jensen et al. 2017;
Esparza-Arredondo et al. 2018). However, these works were limited to the 11.3 µm PAH feature due to limited wavelength coverage and sensitivity of ground-based mid-IR observation making
impossible to study the effect of AGN on the properties of the
PAH molecules.

Previous observations also show lower equivalent widths
of all the PAH bands in AGN compared to those observed in
star-forming galaxies (e.g. Alonso-Herrero et al. 2014; GarcíaBernete et al. 2017, 2022b). Therefore, it has been proposed that
PAH features appear to be diluted by the strong AGN continuum
(e.g. Alonso-Herrero et al. 2014; Ramos Almeida et al. 2014),
that PAH molecules are destroyed by the hard radiation field of
the AGN (e.g. Roche et al. 1991; Voit 1992; Siebenmorgen et al.
2004; García-Bernete et al. 2015; Ramos Almeida et al. 2023),
or the lack of star-formation activity toward the center of AGN
(e.g. Esparza-Arredondo et al. 2018). Using ground-based Nband observations of the type-2 QSO Mrk 477, Ramos Almeida
et al. (2023) reported the non-detection of PAH features in the
central ∼400 pc of the galaxy. Recently, it has been proposed
that ionized PAH molecules are preferentially destroyed in AGN
of moderate luminosity (log L bol [erg s [−][1] ]<10 [45][.][5] ), while neutral PAHs are more resilient (e.g. García-Bernete et al. 2022a,d
and references therein). This is likely related to the fact that the
charge distribution within the ionized PAH molecules may affect the strength of its carbon skeleton structure [1] . Ionized PAH
molecules have less stable carbon skeletons as a consequence of
the increased internal Coulomb forces due the gain or lose of
electrons in the molecular system (e.g. Leach 1986; Voit 1992).

To establish the ability of PAHs to trace star-formation activity in these harsh environments, it is essential to understand their
molecular properties. However, there is limited knowledge on
the effect of hardness of the radiation field, outflows and shocks
on these molecules (e.g. Smith et al. 2007a; Diamond-Stanic
& Rieke 2010; García-Bernete et al. 2022a,d; Zhang, Ho, & Li
2022). The relative variations between PAH features indicate different physical conditions (see e.g. Li 2020 for a review). Recent
works have already shown the potential of _James_ _Webb_ Space
Telescope (JWST; Gardner et al. 2023)/Mid-Infrared Instrument
(MIRI; Rieke et al. 2015; Wright et al. 2015) Medium Resolution Spectrograph (MRS) to study the properties and composition of PAHs and dusty material in the innermost region of AGN
(e.g. García-Bernete et al. 2022d, 2024a,b; Lai et al. 2022, 2023;
Donnan et al. 2023, 2024; Zhang & Ho 2023b). Using PAH band


1 Hereafter we will use the term carbon skeleton structure as the back
bone of the PAH molecule.


Article number, page 2 of 21



ratios, these works also showed that AGN have a significant impact on the PAH properties in the inner ∼100 pc.
Previous spatially resolved _Spitzer_ PAH properties maps of
the superwind in M 82 found that the PAH population might
favour larger molecules probably resulting from preferential destruction of smaller PAHs by X-rays and/or shocks (e.g. Beirão
et al. 2015; Li 2020). JWST/MRS observations of NGC 7469
show tentative evidence that the PAH population in its outflow
regions might be affected by the AGN, having a larger faction
of neutral PAH molecules (García-Bernete et al. 2022d). However, the orientation of its nuclear outflow and the weak geometrical coupling between the AGN outflow and the host are not
favourable for a definitive study.
In this paper, we report the first detailed characterization of
the PAH properties in the outflow regions of three local AGN
(NGC 5506, NGC 5728 and NGC 7172) with D L <40 Mpc. In
particular, we examine the PAH survival conditions in the circumnuclear regions of AGN with sources showing different degrees of coupling between its outflow and host galaxy disk.
We also compare the observed PAH ratios with model grids
(Rigopoulou et al. 2021, 2024). Our results indicate that PAH
depletion of the less resilient hydrocarbon populations (ionized
ones) may occur in Seyfert-like AGN even at kiloparsec scales.
The paper is organized as follows. Sections 2 and 3 describe
the targets selection, observations and data reduction. Section 4
gives an overview of the distribution of the molecular and ionized gas, and the hardness of the radiation field present in the
circumnuclear region. In Section 5 we study the impact of in
AGN-outflows on PAH molecules, and explore the potential of
the PAH bands as a tool for tracing AGN feedback. Finally, in
Section 6 we summarize the main conclusions of this work.


**2.** **Targets and observations**


The galaxies studied here are part of the Galactic Activity,
[Torus, and Outflow Survey (GATOS; García-Burillo et al. 2021;](https://gatos.myportfolio.com/)
Alonso-Herrero et al. 2021; García-Bernete et al. 2024a), whose
main goal is to understand the properties of the dusty molecular tori and their connection to their host galaxies in local AGN.
The parent sample is selected from the 70th Month _Swift_ /BAT
AGN catalog, which is flux-limited in the ultra-hard 14–195 keV
X-rays band (Baumgartner et al. 2013). We refer the reader to
García-Burillo et al. (2021) for details on the GATOS sample
selection from the parent sample. The present study employs
MIRI/MRS and ALMA observations of a sub-sample of obscured type 1.9/2 AGN from the GATOS sample. These data are
part of the JWST Cycle 1 GO proposal ID 1670 (PI: T. Shimizu
and R. Davies). García-Bernete et al. (2024a) presented a first
analysis of these observations, primarily focusing on dirty water ices and silicate features. The molecular gas and ionized
phases of the outflow of NGC 5728 and NGC 7172 are studied in detail in Davies et al. 2024 and Hermosa Muñoz et al.
2024. The subsample selected for this pilot study cover two
orders of magnitude in the observed ionized outflow rate on
∼150 pc scales (∼0.005-0.21 M ⊙ yr [−][1] ). AGN bolometric luminosity and distances are rather similar (see Table 1). The targets have been selected to have different degrees of outflowhost galaxy coupling from very strong to weak (see e.g. Fig.
4 in Ramos Almeida et al. 2022). For instance, NGC 5728 has
strong coupling (i _disk_ ∼40 [◦] and i _bicone_ ∼49 [◦] ; Shimizu et al. 2019)
while NGC 5606 (i _disk_ ∼ 76 [◦] and i _bicone_ ∼10 [◦] ; Fischer et al. 2013)
and NGC 7172 have relatively weaker ones. Although there is
no NLR modelling for NGC 7172, the fitted value of the inclination for the molecular gas disk is i _disk_ ∼88 [◦] (Alonso Herrero

García-Bernete et al.: PAH survival and resilience in AGN-outflows


Name AGN D L log _M_ [˙] _out_ log N [X] H [−][ray] log L [X] Bol [−][ray] i _disk_ i _cone_ AGN-host
type (Mpc) (M ⊙ yr [−][1] ) (cm [−][2] ) (erg s [−][1] ) (deg) (deg) coupling
NGC 5506 1.9 27 0.210 22.4 44.31 76 10 Relatively weak
NGC 5728 1.9 39 0.090 24.2 44.23 40 49 Strong
NGC 7172 2 37 0.005 22.9 44.23 88 ... Relatively weak
**Table 1.** Main properties of the AGN used in this work. The spectral types were taken from Véron-Cetty & Véron (2006). The luminosity distance
and spatial scale were calculated using a cosmology with H 0 =70 km s [−][1] Mpc [−][1], Ω _m_ =0.3, and Ω Λ =0.7. The ionized mass outflow rates are from
Davies et al. (2020). The intrinsic L 14−195 keV and N [X] H [−][ray] were taken from Ricci et al. (2017). Bolometric luminosities are obtained from the
14-195 keV X-ray intrinsic luminosities by multiplying by a factor of 7.42 as in García-Bernete et al. (2019). The inclinations of the disk and
ionization cones are from Fischer et al. (2013), Shimizu et al. (2019) and Alonso Herrero et al. (2023).



et al. 2023), although the galaxy on a larger scale appears to be
at a lower inclination, and the ionized outflow is perpendicular
to the disk (e.g. Hermosa Muñoz et al. 2024). Even if the geometrical coupling is relatively weak compared to NGC 5728,
signatures of AGN feedback has been found in NGC 5506 and
NGC 7172 (see e.g. Alonso Herrero et al. 2023; Esposito et al.
2024; Hermosa Muñoz et al. 2024 for further details). For our
targets, we assume that the NLR (i.e., ionization cones) are cospatial with the main AGN ionized outflow, which is a reasonable assumption given that outflow signatures (i.e., high velocity
and velocity dispersion) have been reported in the NLR region
of these sources in individual studies (Fischer et al. 2013; Durré
& Mould 2018; Shimizu et al. 2019; Alonso Herrero et al. 2023;
Esposito et al. 2024; Davies et al. 2024; Hermosa Muñoz et al.
2024). The main properties of the galaxies studied here are summarized in Table 1. See Appendix C for further information on
the individual objects.


**3.** **Data reduction**


_3.1._ _JWST/MIRI-MRS integral field spectroscopy_


We used mid-IR (4.9-28.1 µm) MIRI MRS integral-field spectroscopy data. The MRS has a spectral resolution of R∼3700–
1300 (Labiano et al. 2021) and comprises four wavelength channels: ch1 (4.9–7.65 µm), ch2 (7.51–11.71 µm), ch3 (11.55–
18.02 µm), and ch4 (17.71–28.1 µm). These channels are further subdivided into three sub-bands (short, medium, and long).
The field of view is larger for longer wavelengths: ch1 (3 [′′] . 2 ×
3 [′′] . 7), ch2 (4 [′′] . 0 × 4 [′′] . 7), ch3 (5 [′′] . 2 × 6 [′′] . 1), and ch4 (6 [′′] . 6 × 7 [′′] . 6).
The spaxel size is ranging from 0 [′′] . 13 to 0 [′′] . 35. We refer to Rieke
et al. (2015) and Wright et al. (2015) for further details (see
also Argyriou et al. 2023). We primarily followed the standard
MRS pipeline procedure (e.g., Labiano et al. 2016 and references
therein) to reduce the data using the pipeline release 1.11.4 and
the calibration context 1130. Some hot and cold pixels are not
identified by the current pipeline version, so we added an extra
step before creating the data cubes to mask them. The data reduction is described in detail in García-Bernete et al. (2022d, 2024a)
and Pereira-Santaella et al. (2022). The nuclear spectra from the
different sub-channels were extracted assuming they are point
sources (∼0.4 [′′] at 11 µm, see García-Bernete et al. 2024a for further details).


_3.2._ _ALMA data_


Observations of the CO(3–2) emission line at 345.796 GHz
emission line for the GATOS sample were obtained using
ALMA band 7. We refer the reader to García-Burillo et
al. (2021) for further details on the ALMA data. The data
were obtained as part of programmes #2017.1.00082.S (PI:



S. García-Burillo), #2018.1.00113.S (PI: S. García-Burillo)
and #2019.1.00618.S (PI: A. Alonso-Herrero). For this work,
we used the fully reduced CO(3–2) maps of NGC 5506 and
NGC 7172 from García-Burillo et al. (2021) and Alonso Herrero
et al. (2023). The ALMA CO(3–2) data for NGC 5728 were obtained in the compact configuration of the array (C43-4). In total
two tracks were observed using observations on February 27 and
29, 2020. We used a single pointing with a field-of-view (FoV)
of 17 [′′] . The data were processed using the standard pipeline
data reduction routine and CASA (version 5.6.1-8; McMullin et
al. 2007). The continuum in each of the four spectral windows
was identified and subtracted by the pipeline before imaging the
CO(3–2) line.


**4.** **Mid-infrared circumnuclear emission**


_4.1._ _Distribution of the circumnuclear molecular and ionized_

_gas_


To study the distribution of the circumnuclear molecular and ionized gas, we produce emission features maps using a local continuum and 3σ signal-to-noise cut [2] . For the emission lines, we
use the ALUCINE tool (Peralta de Arriba et al. 2023) with a single Gaussian fit spaxel-by-spaxel covering the entire cube. In the
case of the broad PAH features, we first fitted a local continuum
that we then subtracted from the observed spectra and integrated
the residual data in a spectral range centred in the peak of the
bands. We used the 6.0 to 6.5 µm and 11.05–11.6 µm for the 6.2
and 11.3 µm PAH features, respectively (see García-Bernete et
al. 2022d for further details). We follow the same methodology
as presented in Hernán-Caballero & Hatziminaoglou (2011). We
also degrade maps to the coarser angular resolution when comparing directly (e.g. ratio maps). To do so, we first convolve the
higher angular resolution maps with a Gaussian to match the size
of the PSF star at the wavelength of the lower angular resolution map. In particular, we employed observations of calibration

−
point sources (HD-163466 and IRAS 05248 7007, Program IDs
1050 and 1049, PIs: B. Vandenbussche and M. Migo Mueller)
to measure the FWHM of the PSF for each spectral channel.
Then, we resample the pixel size of the shorter wavelength map
to match that of longer wavelength one for each pair.
In Fig. 1, we show the 11.3 µm PAH feature (top panels)
and H 2 0-0 S(1) 17.03 µm (bottom panels) intensity map for
NGC 5728, NGC 7172 and NGC 5506 (from left to right panels).
In general, the 11.3 µm PAH maps reveal a good correspondence
with the morphology of the cold molecular gas (black contours
in Fig. 1) traced by ALMA CO (3-2). Performing a spaxel by
spaxel analysis, NGC 5506 and NGC 7172 show a tight correlation between the 11.3 µm PAH band and CO (3-2) emission (see


2
We use the continuum to estimate the AGN position for each subchannel.


Article number, page 3 of 21

_A&A proofs:_ manuscript no. draft


**Fig.** **1.** JWST/MRS emission line maps. From left to right panels: NGC 5506, NCG 5728 and NGC 7172. Top panels: 11.3 µm PAH feature
intensity map. Central panels: H 2 S(1) at 17.03 µm intensity map. Bottom panels: [Ne II] 12.81 µm intensity map. The black contours are the
CO(3-2) emission from ALMA on a logarithmic scale. The first and last contours lie at 3σ and the peak flux, respectively. North is up and east
is to the left, and offsets are measured relative to the AGN. Orange solid circle and white ellipse correspond to the JWST and ALMA beams,
respectively.



Table 2). For NGC 5728, there is also a remarkably good agreement between the CO(3-2) molecular gas and the 11.3µm PAH
emission in the inner circumnuclear structure. However, within
various circumnuclear regions of NGC 5728, cold and warm
molecular gas emission is present in zones where the emission


Article number, page 4 of 21



of PAHs and low ionization potential (IP) lines such as [Ne II] is
weak (see central bottom panel of Fig. 1; see also Davies et al.
2024). PAH emission might be also excited by the ISM radiation
field from old stars (e.g. Kaneda et al. 2008; Ogle et al. 2024),
however, the observed weak [Ne II] emission (see bottom panels

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig.** **2.** JWST/MRS emission line maps. From left to right panels: NGC 5506, NCG 5728 and NGC 7172. Top panels: [S IV] 10.51 µm intensity map. Magenta solid lines represent the radio jet axis (from Thean et al. 2000; Kinney et al. 2000; Shimizu et al. 2019). Bottom panels:

[Fe II] 5.34 µm intensity map. The black contours are the CO(3-2) emission from ALMA (same as in Fig. 1). North is up and east is to the left, and
offsets are measured relative to the AGN. Orange solid circle and white ellipse correspond to the JWST and ALMA beams, respectively.



of Fig. 1) suggests that in these regions there are cold molecular
gas clumps which are not (yet) actively forming stars.

Although there is a good relationship between CO(3-2) cold
molecular gas and the 11.3µm PAH emission in the central region of NGC 5728, these are not well correlated when considering the entire FoV (see Table 2). Similarly, the H 2 0-0 S(1) warm
molecular gas and the 11.3µm PAH emission show a poor correlation in NGC 5728, while these are tight for NGC 5506 and
NGC 7172 (see Table 2).

The cold molecular gas from ALMA and the warm phase
traced by the H 2 0-0 S(1) show an excellent correlation in the
three galaxies studied here (see Table 2; see also Davies et al.
2024 for a comparison with CO(2-1) for NGC 5728). However,
some H 2 0-0 S(1) excess with respect to the cold molecular gas
emission can be found in the same direction of the ionization
cones, which is probably related to shocks in the outflow direction (e.g. Kristensen et al. 2023 and references therein).

The ionization cone region as probed by the high-excitation
line emission ([S IV] 10.51 µm; top panels of Fig. 2) extends out
to ∼1 kpc in NGC 5728, and at least hundreds of pc in NGC 5506
and NGC 7172 (also Esposito et al. 2024, Hermosa Muñoz et al.
2024, Zhang et al. 2024, Delaney, in prep). NGC 5728 shows



Galaxy PAH 11.3 µm PAH 11.3 µm H 2 S(1)
vs. H 2 S(1) vs. CO (3-2) vs. CO (3-2)
**NGC 5506** **0.79** (249) 0.61 (311) **0.76** (1049)
NGC 5728 0.36 (1725) 0.24 (1424) **0.79** (1393)
**NGC 7172** **0.73** (630) **0.88** (818) **0.87** (1014)
**Table** **2.** Pearson’s correlation coefficients. Values in parentheses correspond to the number of spaxels considered in the correlation. In bold
we indicate relatively strong correlations (i.e. ρ >0.7).


extended [S IV] 10.51 µm emission, which is in agreement with
previous works (e.g. Shimizu et al. 2019; Davies et al. 2024
and references therein). NGC 7172 and NGC 5506 show a more
compact [S IV] emission as probed by the FoV of the observations, but still elongated in the direction of the ionized outflow
of these sources (e.g. Fischer et al. 2013; Alonso Herrero et al.
2023; Esposito et al. 2024; Hermosa Muñoz et al. 2024). Furthermore, two (NGC 5728 & NGC 7172) of the three galaxies
have radio emission with the same orientation as the ionized
cone (see Fig. 2; also Appendix C for further details on the individual objects). The position angle of the extended radio emission in NGC 5506 is ∼70 [◦] (Schmitt et al. 2001), which has a


Article number, page 5 of 21

_A&A proofs:_ manuscript no. draft


**Fig. 3.** JWST/MRS spatially resolved maps. From left to right panels: NGC 5506, NCG 5728 and NGC 7172. Top panels: Hardness of the radiation
field maps traced by the [Ne III]/[Ne II] ratios. The color-coded contours correspond to the average [Ne III]/[Ne II] ratios found in QSO (black
line), Sy1 (blue line), Sy2 (red line), LINER (green line) and Hii (magenta line) regions reported in Pereira-Santaella et al. (2010). Bottom
panels: 11.3/6.2 PAH ratio maps. Dark green contours correspond to the 11.3 µm PAH emission. The first contour is at 3σ and the last contour
at 1.5×10 [−][15] erg s [−][1] cm [−][2] . Color-coded circles correspond to the nuclear PAH ratios. The central regions correspond to the 11.3/6.2 PAH ratios
measured in the nuclear spectra. For NGC 7172, the black circle represent the non-detection of nuclear PAH for this source (see Section 5.1 for
further details). North is up and east is to the left, and offsets are measured relative to the AGN.



similar morphology to that of the [S IV] map presented in Fig.
2. Depending on the geometrical coupling, these relatively low
luminosity radio jets can inject additional mechanical energy to
the ISM of the galaxy disks (e.g. Combes et al. 2013; GarcíaBurillo et al. 2014; Morganti et al. 2015; Bellocchi et al. 2019;
García-Bernete et al. 2021; Venturi et al. 2021; Peralta de Arriba
et al. 2023; Audibert et al. 2023, Ogle et al. 2024, Speranza et
al. 2024). The [Fe II] 5.34 µm intensity maps (bottom panels of
Fig. 2) are a good tracer of shock and star-forming activity (e.g.
Spinoglio, Andreani & Malkan 2002; Allen et al. 2008). These
maps show that shocks are likely operating in the outer edges of
the ionization cones in NGC 5728 and NGC 5506, where [Fe II]
emission is detected beyond the central cold molecular gas emission. However, the similar morphology of the circumnuclear
cold molecular gas and [Fe II] emission in NGC 7172 suggests
that the [Fe II] emission in this source could be mainly related to
star-forming activity. However, this might be not the case in the
nuclear region where [Fe II] emission is strong while there is a
deficit of CO (3-2).


Article number, page 6 of 21



_4.2._ _Hardness of the radiation field_


There is evidence that AGN might have a significant impact on
the PAH molecules located in their nuclear regions (e.g. GarcíaBernete et al. 2022d and references therein). Thus, it is important to better understand the effect of the radiation fields on these
molecules. The [Ne III] 15.55 µm/[Ne II] 12.81 µm ratio is a reliable indicator of the hardness of the radiation field in the surroundings of massive young stars (e.g. Thornley et al. 2000).
This ratio can be also used in AGN (e.g. Groves, Dopita &
Sutherland 2006; Pereira-Santaella et al. 2010; García-Bernete
et al. 2022a), however, low ionization potential emission lines
such as [Ne II] can be significantly contaminated by the X-RayDominated Regions in AGN (e.g. García-Bernete et al. 2017;
Pereira-Santaella et al. 2017). Thus, as a sanity check, we also
use other ratios using higher IP lines such as [Ne V] and we advance that find similar results.
Top panels of Fig. 3 shows the spatially resolved

[Ne III]/[Ne II] ratio maps of NGC 5728, NGC 7172 and
NGC 5506 (from left to right panel). As expected, these maps

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig. 4.** JWST/MRS [S IV] 10.51 µm velocity dispersion maps. From left to right panels: NGC 5506, NCG 5728 and NGC 7172. The black contours
are the CO(3-2) emission from ALMA (same as in Fig. 1). North is up and east is to the left, and offsets are measured relative to the AGN. Orange
solid circle and white ellipse correspond to the JWST and ALMA beams, respectively.



show a good correspondence between the location of the ionization cone and the higher values of the [Ne III]/[Ne II] ratio map.
Lower values of this ratio (associated with star-forming activity;
magenta contour in top panels of Fig. 3) are found in the galaxy
disk of NGC 7172 (see Hermosa Muñoz et al. 2024 for a detailed discussion) and NGC 5506 and in three regions in the starforming ring of NGC 5728 (see top left panel of Fig. 3). Interestingly, although the majority of the high [Ne III]/[Ne II] value
spaxels of NGC 5728 are mainly located along the main outflow
axis, it has also high [Ne III]/[Ne II] values in the perpendicular direction to the jet [3] . This perpendicular region also shows
high-velocity dispersion values in high ionization potential lines
(e.g. [S IV], [Ne III], [Ne V] 14.32 µm, 24.32 µm and warm H 2
lines; see Fig. 4, also Davies et al. 2024). Previous studies observed a similar high-velocity dispersion structure perpendicular
to the direction of the outflow in the presence of a geometrically
coupled radio jet (e.g. Ogle et al. 2024), as demonstrated by using ionized gas traced by optical lines (Venturi et al. 2021) and
cold molecular gas from ALMA (Audibert et al. 2023). This has
been also found in a sample of low-ionization nuclear emissionline region galaxies (LINERs) with no radio jet (e.g. Hermosa
Muñoz et al. 2024). A number of possibilities could account
for this high-velocity dispersion enhancement: (1) Jet-induced
acceleration of gas out of the disc plane (e.g. Audibert et al.
2023; Venturi et al. 2021); (2) Outflowing torus (e.g. AlonsoHerrero et al. 2018); (3) Broad AGN-outflows, which might be
potentially resembling a spherical bubble. Beam smearing could
also affect the velocity dispersion, however this velocity dispersion enhancement is also detected in the ALMA observations
of NGC 5728 (see e.g. Fig. 3 of Shimizu et al. 2019). Given
the geometrical coupling of the jet and the host galaxy disk in
NGC 5728, the first scenario is most likely, although a detailed
kinematic analysis is needed to confirm this. We refer the reader
to Davies et al. (2024) for further discussion on the outflow of
this galaxy.


3 We note that Venturi et al. 2021 also reported AGN-dominated
LINER-like excitation in the perpendicular direction to the jet in some
local AGN using the optical BPT diagram.



**5.** **PAH bands as a tool for tracing AGN feedback**


There is consensus that the stretching and bending vibrations
involving the C-H and C-C bonds produce the observed PAH
bands (e.g. Li 2020 for a review). In particular, ionized PAH
molecules are responsible for 6–9 µm features, whereas the 3.3,
11.3 and 17 µm features originate in neutral PAH molecules
(e.g. Allamandola, Tielens & Barker 1989; Draine & Li 2007;
Draine et al. 2021). Therefore, the ratios between the 11.3 µm
feature and those related to the charged PAHs (i.e. 6.2 or 7.7 µm
features) have been proposed as a good indicator of the PAH
ionization fraction (e.g. Draine & Li 2001, 2007; Draine et al.
2021; Rigopoulou et al. 2021). The ionization potential of PAH
molecules is small (∼few eV; e.g. Wenzel et al. 2020). Previous works using Spitzer/IRS data found that AGN-dominated
galaxies have an average 11.3/6.2 PAH ratio of ∼2, whereas starforming galaxies have an average ratio of 1 (García-Bernete et
al. 2022a). This trend has also been found in the central region of
AGN with high angular resolution JWST observations of nearby
sources (e.g. García-Bernete et al. 2022d). This indicates that the
central region of AGN might contain a larger fraction of neutral
PAH molecules compared to star-forming regions. However, investigating a larger sample is needed to firmly confirm this trend.


Here, we investigate how the PAH ionization fraction
changes spatially in the JWST/MRS FoV for the three galaxies. In bottom panels of Fig. 3, we present the spatially resolved
11.3/6.2 PAH maps. These plots show that the fraction of neutral
PAH molecules is similar in the star-forming ring of NGC 5728
compared to those of the inner circumnuclear region (i.e. the
minispiral region, which is extended in the same direction as the
dusty torus; see Alonso-Herrero et al. 2018). The map also reveals regions where the neutral PAHs generally dominate along
the projected direction of the outflow (Fig. 3). While this effect is
evident for NGC 5728 in Fig. 3, it is not as clear for the other two
sources (i.e. NGC 5506 and NGC 7172). This is likely explained
by the faint 6.2 µm PAH emission present in the projected direction of their outflows. Thus, extractions in a larger aperture
to increase the signal-to-noise ratio in the faint emission are
needed to confirm the larger fraction of neutral PAH molecules
in these regions (see Section 5.1). There is a larger fraction of
ionized PAHs (low 11.3/6.2 PAH ratio values) in the “normal”


Article number, page 7 of 21

_A&A proofs:_ manuscript no. draft


**Fig.** **5.** PAH diagnostic diagram: relative strengths of the 6.2, 7.7, and 11.3 µm PAH features. Left panel: Nuclear regions of AGN versus starforming regions. Filled squares correspond to the nuclear regions of NGC 5728 (purple square) and NGC 5506 (red square). We also plot the
nuclear regions of NGC 6552 (blue square), NGC 7319 (black upper limit) and NGC 7469 (magenta square) from García-Bernete et al. (2022d).
Right panel: Outflow regions of AGN versus star-forming regions. The red, purple and green circles correspond to average PAH ratios of the
outflow regions of NGC 5506, NGC 5728 and NGC 7172, respectively. The purple triangle represents the average value of star-forming regions of
NGC 5728 that are affected by the AGN according to their [Ne III]/[Ne II] ratio. For comparison, we plot PDR-like values from the Orion bar (open
brown diamond; see Appendix B for details). The grey shaded region denotes the average location of star-forming galaxies from García-Bernete
et al. (2022a) using _Spitzer_ /IRS data and black and magenta filled stars correspond to the average value of star-forming regions of NGC 3256
(from Rigopoulou et al. 2024) and NGC 7469 (from García-Bernete et al. 2022d). Filled stars correspond to the average star-forming regions of
NGC 5728 (purple star), NGC 7172 (green star) and NGC 5506 (red star). The grey grid corresponds to neutral PAHs ranging from small PAHs
(N C =20; right side of the grid) to large PAH molecules (N C =400; left side of the grid). Dashed grey lines correspond to intermediate numbers of
carbons. The orange grid corresponds to 70% of ionised PAH molecules for the same number of carbons as the neutral grid. Dotted orange lines
correspond to intermediate numbers of carbons. In Fig. A.4 we show this plot with all the individual regions, and in Tables A.1, A.2 and A.3 we
list the measured PAH fluxes.



star-forming regions of NGC 7172 (bottom central panel of Fig.
3) and NGC 5506 (bottom right panel of Fig. 3) when compared
to the circumnuclear emission of NGC 5728. The galaxy disks of
NGC 5506 and NGC 7172 exhibit a similar 11.3/6.2 PAH ratio
to the typical value found in star-forming galaxies (≲1; GarcíaBernete et al. 2022a). This is consistent with the JWST/MRS observations of NGC 7469 (García-Bernete et al. 2022d; Zhang &
Ho 2023b) and of a sample of luminous IR galaxies (Rigopoulou
et al. 2024), where star-forming regions shows low 11.3/6.2 PAH
ratios (≲1; see right bottom panel of Fig. 1 in García-Bernete et
al. 2022d). Conversely, the extended emission of NGC 5728 exhibits larger values of the 11.3/6.2 PAH ratio, resembling those
typically found in AGN-dominated systems (García-Bernete et
al. 2022a,d). In addition, the SF-like 11.3/6.2 PAH ratios found
in the disk of NGC 5506 and NGC 7172 are in agreement with
the relatively low hardness of the radiation field present in these
regions (see top panels of Fig. 3).

The larger fraction of neutral PAH molecules present in the
extended emission galaxy disk and projected direction of the outflow of NGC 5728 could be related with the depletion of ionized
PAH molecules (García-Bernete et al. 2022a,d) due to the hard
radiation field present in the FoV probed by the MRS (see also
BPT diagram in Shimizu et al. 2019.

Given the nearly face-on geometry of NGC 5728, we cannot
rule out the possibility that UV radiation emitted by an evolved
stellar population in the bulge might contribute to exciting PAH
molecules (e.g. Kaneda et al. 2008; Ogle et al. 2024). Indeed,
a large fraction of neutral PAHs are found in regions with rela

Article number, page 8 of 21



tively soft radiation fields, similar to those observed in the bulges
of galaxies (Kaneda et al. 2008). However, stellar population
analyses in local AGN generally show a significant young (630 Myr) stellar population present within the central few hundred parsecs (see e.g. Burtscher et al. 2021, which include two
of our targets in their study [NGC 5728 and NGC 7172]). Thus,
it is unlikely that an evolved stellar population is significantly
contributing to the 11.3µm PAH emission observed in our targets.
Differences in the PAH ratios might be challenging to identify when using spatially resolved analyses, due to the limited
signal-to-noise of the PAH bands. Thus, in Section 5.1 we extract spectra from various targeted regions that significantly increase the signal-to-noise ratio to search for differences in the
PAH properties.


_5.1._ _PAH properties in the projected direction of_
_AGN-outflows_


We compare the relative strengths of the observed PAH bands of
AGN- and SF-dominated regions with model grids generated using theoretically computed PAH spectra based on Density Functional Theory (Rigopoulou et al. 2021). In particular, we examine the 6.2/7.7 and 11.3/7.7 µm PAH ratios, which are sensitive
to the molecular size and ionization stage of PAH molecules, respectively. We refer the reader to Rigopoulou et al. (2021) for
more details on how these theoretical spectra and grids are constructed.

García-Bernete et al.: PAH survival and resilience in AGN-outflows



To do so, we extracted the JWST/MRS spectra from the nuclear regions of the three sources studied here. We note that the
nuclear spectrum of NGC 7172 is strongly dominated by the
continuum and shows no PAH emission (see Fig. 1 of GarcíaBernete et al. 2024a, also Hermosa Muñoz et al. 2024) and,
thus, its nuclear region is not included in Fig. 5. The high extinction values together with the strong continuum might dilute
and attenuate the nuclear PAH emission from the nuclear region,
which might be connected to the dust lane present in NGC 7172
(see Appendix C). To investigate similarities and differences in
the PAH properties between nuclear regions, and the projected
direction of the outflow and star-forming zones, we selected a
number of circumnuclear regions in the three targets (see Appendix A for further details on the extracted apertures). In Tables
A.1 and A.2 we list the measured PAH fluxes in this work.
Left panel of Figure 5 shows that the nuclear regions (filled
squares) of AGN tend to have large 11.3/7.7 µm PAH ratios (and
similarly for the 11.3/6.2 µm PAH ratio) compared to “normal”
SF regions. This suggests that in the nuclear regions of AGN,
the PAH emission originates in neutral PAH molecules with little variation of the molecular sizes [4] . Our findings show the same
trend than in previous works, which also include type 1 and 2
AGN, using JWST/MRS observations (e.g. García-Bernete et al.
2022d). More recently, using JWST observations of local luminous infrared galaxies, Rigopoulou et al. (2024) also find that
SF-regions have a larger fraction of ionized PAH molecules compared to that of AGN.
There are some scatter in the PAH band ratios for the nuclear regions of AGN (see left panel of Figure 5), indicating that
the mean PAH properties might slightly differ from source to
source. However, the nuclear regions of AGN favour larger fractions of neutral PAH molecules compared with star-forming regions (filled stars). Furthermore, SF-dominated regions tend to
cluster in a narrower part of the diagram where the location of
star-forming galaxies using integrated values from Spitzer/IRS
lie (García-Bernete et al. 2022a; grey area in Fig. 5). However,
PAH molecular sizes traced by 6.2/7.7 µm PAH ratio are rather
similar.

Star-forming regions located along the projected direction
of the outflow of NGC 5728 (i.e. SF2, SF3, SF4, SF5, SF6,
SF7, SF9 and SF10 in Fig. A.1; average value represented by
a purple filled triangle in Fig. 5, right) show larger values of the
11.3/7.7 µm PAH ratio than in “normal” SF regions. We also find
high 11.3/7.7 µm PAH ratios in the projected direction of the outflow of NGC 5728 (i.e. Out1, Out2 and Out3 in Fig. A.1) and in
the perpendicular region of the jet (high-velocity dispersion region; i.e. D1 and D2 in Fig. A.1). This high-velocity dispersion
region has been interpreted as lateral turbulence caused by the jet
interacting with the host galaxy (e.g. Venturi et al. 2021). Consequently, the elevated 11.3/7.7 µm (and 11.3/6.2 µm) PAH ratio
observed in this region is consistent with this interpretation. The
average value of the regions located in the projected direction of
the outflow of NGC 5728 is represented by a purple filled circle in Fig. 5 (see also Fig. A.1). For NGC 5506 and NGC 7172,
we extracted regions along the projected direction of the outflow
(indicated by red and green circles in Fig. 5; see also Fig. A.1).
We find high values of the 11.3/7.7 µm PAH ratio in NGC 5506
(filled red circle in Fig. 5 and NGC 7172 (filled green circle in
Fig. 5). These regions are also located where the AGN feedback
appears to be stronger in these galaxies (e.g. Fischer et al. 2013;
Thomas et al. 2017; Davies et al. 2020; Alonso Herrero et al.


4 PAH molecular sizes are estimated by using the 6.2/7.7 µm PAH ratio.



2023; Esposito et al. 2024; Hermosa Muñoz et al. 2024; Zhang
et al. 2024).
However, star-forming regions of NGC 5506 (Disk1 and
Disk2 apertures in Fig. A.1), NGC 5728 (i.e. SF1, SF8, SF11
and SF12 in Fig. A.1) and NGC 7172 (Disk1 and Disk2 apertures in Fig. A.1) are consistent with PAH ratios typically found
in star-forming galaxies (see Fig. A.1). The outflow is located
behind the disk for the southern region of NGC 5506 and the
northern region of NGC 7172 and, thus, they exhibit PAH ratios
that broadly resemble those of typical star-forming regions (see
Appendix A for further details). The hardness of the radiation
field is generally higher in the regions with elevated 11.3/7.7 µm
PAH ratio (also for the 11.3/6.2 µm PAH ratio; see Fig. 3). These
results are in agreement with the previously observed trend of a
larger fraction of neutral PAHs being present in the harsh environment of the active nuclei.

For comparison, in Fig. 5 we also show the PAH ratios of
the strongly illuminated photodissociation region (PDR) Orion
Bar (open brown diamonds; see Appendix B). We use the extracted regions on the JWST/MIRI MRS observations presented
in Peeters et al. (2023) (see also Chown et al. 2023, Habart et al.
2023, Pasquini et al. 2023 and Elyajouri et al. 2024). The atomic
PDR and dissociation fronts (DF1, DF2, DF3; see Fig. 1 of
Peeters et al. 2023) show values which are broadly in agreement
with the values found for SF-regions in galaxies [5] . However, the
closest H ii region (projected distance of ∼0.224 pc; Peeters et al.
2023) to the main source of ionizing radiation and winds (i.e the
O7V-type star θ [1] Ori C) have PAH ratios indicating a large fraction of neutral molecules, similar to those observed in the harsh
environments of AGN.

The geometry of the AGN ionized outflow (and radio jet)
with respect to the host galaxy disk (i.e. coupling) is key for understanding AGN feedback (e.g. Ramos Almeida et al. 2022 and
references therein). Under the assumption that the majority of
the PAH molecules are located in the galaxy disk, geometrical
coupling between the outflow/jet and host galaxy might play a
key role in explaining the effect of the AGN outflow/radio jet in
PAH molecules. Recently, using JWST observations, Donnan,
Rigopoulou, & García-Bernete (2024) have found that PAHs
are kinematically influenced by the AGN-driven outflow in the
type 1 AGN, NGC 7469. As mentioned above, the geometry derived from NLR modelling (see Section 2 and Appendix C) indicates that the AGN ionized outflow and the radio jet might
be strongly impacting the galaxy disk in the case of NGC 5728
(see Fig. C.1 in Appendix C) while the geometrical coupling is
relatively weak in NGC 7172 and NGC 5506 (e.g. Fischer et al.
2013; Alonso Herrero et al. 2023; Davies et al. 2024; Esposito
et al. 2024; Hermosa Muñoz et al. 2024). We further explore the
properties of the PAH population in regions showing hard radiation fields (see Fig. 3), which is co-spatial with the projected
direction of the outflow of NGC 5728 (see Davies et al. 2024).
In general, selected regions in projected direction of the outflow
have elevated 11.3/7.7 (and 11.3/6.2) PAH and [Ne III]/[Ne II]
ratios as found in AGN-dominated environments (see also Fig.
3).
Based on the 6.2/7.7 µm PAH ratios, we find that all extracted
regions typically fall within the range of PAH sizes (i.e. number
of carbon; N _c_ ) covered by the grid (20<N _c_ <400). The only ex

5 Note that the spectra of the Orion bar are extracted in regions with
a sub-pc physical resolution regions, as opposed to scales of approximately hundreds of pc in the circumnuclear region for the galaxies studied here. This might explain the slightly different PAH ratios observed
in the Orion bar compared to the star-forming regions.


Article number, page 9 of 21

_A&A proofs:_ manuscript no. draft



ceptions are the nuclear regions of NGC 5506 and NGC 5728,
which are located in a region favouring larger PAH molecules
(see e.g. Kerkeni et al. 2022). However, the 6.2 and 7.7 µm PAH
features in these two nuclei are extremely weak and, thus, we
consider the 6.2/7.7 µm PAH ratio of NGC 5506 and NGC 5728
as lower limits.
Our findings indicate that regions located in the projected direction of the outflow of the AGN presented here generally have
a larger fraction of neutral PAH molecules compared to “normal”
SF regions. This is consistent with the tentative evidence found
in the nuclear outflow of NGC 7469 using JWST/MRS data (e.g.
García-Bernete et al. 2022d) and in the outflow of the starburst
M 82 using Spitzer/IRS data (Beirão et al. 2015). The fraction of
ionized PAHs in the disk regions of NGC 5506 and NGC 7172
(and regions with low [Ne III]/[Ne II] values in NGC 5728) are
in agreement with those measured in star-forming dominated regions. The larger fraction of neutral PAH molecules (11.3/7.7
and 11.3/6.2 µm PAH ratios) in the nuclear regions of AGN and
the projected direction of their outflows suggests that the AGN
is affecting the PAH emission in these regions. This could be
explained by the potential destruction of the ionized molecules,
which are less resilient than neutral ones to harsh radiation fields
and shocks (see e.g. García-Bernete et al. 2022d; Li et al. 2022).
The ionization of PAH molecules produces electronic rearrangement and structural changes in the system inducing repulsive
forces within the molecule that might end in a "Coulomb explosion" (Leach 1986; Voit 1992). Previous laboratory works
have found that for the small PAH molecule naphthalene (C 10 H 8 )
Coulomb explosions are important when exposed to >40 eV
photons (Leach 1989). As previously noted, we cannot rule out
that an evolved stellar population in the bulge of NGC 5728
might also contribute to exciting neutral PAH molecules (e.g.
Kaneda et al. 2008; Ogle et al. 2024). However, stellar population analyses does not seem to favour this scenario in NGC 5728
(see e.g. Burtscher et al. 2021). We remark that new observations of local AGN with _JWST_ will allow for enlarging the sample, which will be crucial for obtaining definitive conclusions
and for enhancing the statistical significance of the findings presented here.


_5.2._ _PAH-H_ 2 _diagram_


As discussed above the 11.3/6.2 PAH ratio traces AGNdominated regions. Here, we further investigate other ratios involving one of the most AGN affected PAH bands covered by
MIRI/MRS (i.e. the 6.2µm PAH feature). Together with hard Xrays, high IP lines are powerful tools for unveiling AGN activity.
However, recent JWST NIR-to-MIR observations of a deeply
embedded AGN showed non-detection of high IP (>100 eV)
lines (e.g. García-Bernete et al. 2024b). Furthermore, even ultrahard X-ray (14-195 keV) Swift/BAT observations are missing a
significant fraction of highly absorbed type 2 sources (e.g. Ricci
et al. 2015; Mateos et al. 2017; García-Bernete et al. 2019). It
is thus crucial to search for alternative tracers of AGN. Our targets with similar bolometric luminosity, and different hydrogen
column densities (see Table 1) and ranging from strong to weak
AGN-host coupling allow us to test the diagnostic power of these

tracers.
We investigate the relation of the 6.2µm PAH/H 2 0-0 S(1) ratio. H 2 rotational lines originate in warm molecular gas and are
excited by UV fluoresence and gas heating by collisional excitation (e.g. Kaufman, Wolfire, & Hollenbach 2006). Therefore,
the H 2 emission depends on the amount of warm molecular gas
present, but also on the UV heating and the possible presence of


Article number, page 10 of 21



**Fig.** **6.** Relationship between the 11.3/6.2 PAH ratio and 6.2 µm PAH
feature relative to H 2 S(1) for all the spaxels of the three targets. Blue,
green, and red circles represent values where the 6.2 µm PAH/H 2 S(1)
ratio is greater than 12 (SF-dominated), between 12 and 5, and less than
5 (AGN-dominated), respectively. Squares represent the median value
of each category. Squares, circles and hourglasses symbols correspond
to NGC 5506, NGC 5728 and NGC 7172. The dashed vertical lines represent the average values of star-forming galaxies, AGN and relatively
powerful radio galaxies from Spitzer/IRS observations (Ogle et al. 2010
and García-Bernete et al. 2022a).


turbulence and shocks (e.g. Kristensen et al. 2023 and references
therein). Using Spitzer/IRS data, Ogle et al. (2010) found that
PAH/H 2 is smaller in jet-powered molecular hydrogen emission
galaxies (MOHEGs) with strong jet-ISM interaction compared
with “normal” star-forming galaxies (factor ∼300; see also Nesvadba et al. 2010). The average 11.3/6.2 PAH ratio (∼3) reported
by Ogle et al. (2010) for relatively powerful radio galaxies [6] is
larger than that of AGN [7] (∼2; García-Bernete et al. 2022a). Similarly, Labiano et al. (2013, 2014) also found that the 7.7 µm PAH
band is weaker than the 11.3 µm PAH feature in relatively powerful radio galaxies [8] . Therefore, 6.2µm PAH/H 2 is expected to be
small in AGN with strong host-outflow/jet coupling. Recently,
JWST/MRS observations have revealed enhanced emission from
warm and hot H 2 in NGC 7319 (Pereira-Santaella et al. 2022),
which hosts a low-power radio jet and has extremely faint PAH
emission (García-Bernete et al. 2022d).
In Fig. 6 we present all the spaxels for the three galaxies
at the angular resolution of the H 2 0-0 S(1) maps. Fig. 6 shows
a relationship between the 11.3/6.2 PAH ratio and the 6.2µm
PAH/H 2 0-0 S(1) ratio. This relation is in part driven by the
6.2µm PAH feature, which is strongly affected by the AGN,
but also by the enhancement of H 2 in AGN shocked regions.
We select regions that are AGN-dominated (red circles) and
SF-dominated (blue circles) in Fig. 6. To do so, we use 6.2µm
PAH/H 2 0-0 S(1)<5 and 6.2µm PAH/H 2 0-0 S(1)>12, respectively. To define these values, we compare the 6.2µm PAH/H 2 00 S(1) ratio map with the spatially resolved [Ne III]/[Ne II] maps


6
Hereafter, we use the terms relatively powerful radio galaxies and
MOHEGs interchangeably.
7 We note that both samples were fitted using PAHFIT (Smith et al.
2007a).
8 Note that the sources studied in Labiano et al. (2013, 2014) are reactivated powerful radio sources, and their radio jets may strongly affect
the ISM of the galaxy.

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig. 7.** JWST/MRS 6.2µm PAH/H 2 S(1) ratio maps. From left to right panels: NGC 5506, NGC 5728 and NCG 7172. Maps are color-coded following the criteria in Fig. 6. SF-, AGN-dominated and intermediate regions are shown in blue, red and green, respectively. North is up and east is
to the left, and offsets are measured relative to the AGN.


**Fig. 8.** JWST/MRS 11.3µm PAH/H 2 S(1) ratio maps. From left to right panels: NGC 5506, NGC 5728 and NCG 7172. North is up and east is to
the left, and offsets are measured relative to the AGN.



(see Figs. 3 and 7). As this is a visual criterion, we also included a third classification as intermediate values (5<6.2µm
PAH/H 2 0-0 S(1)<12). The AGN-dominated limit is estimated
by using the average value of the 6.2µm PAH/H 2 0-0 S(1) of
those spaxels with [Ne III]/[Ne II] ratios greater than that found
for Sy1 in Pereira-Santaella et al. (2010) (see top panels of Fig.
3). The 6.2µm PAH/H 2 0-0 S(1) ratio map of the three targets
studied in this work, color-coded with these criteria, is shown
in Fig. 7. Intermediate values of the 6.2µm PAH/H 2 0-0 S(1) ratio are also found for NGC 7172 where the MIR ionized outflow of this galaxy is detected (see Hermosa Muñoz et al. 2024
for further discussion on the outflow of this galaxy). NGC 5728
has the largest area of AGN-dominated spaxels (red colour),
likely related with the fact that this galaxy shows the strongest
outflow/jet-host galaxy coupling of the sources studied here. Furthermore, SF-dominated regions are also revealed in the starforming ring of NGC 5728 and the disk regions of NGC 7172
and NGC 5506 (see Fig. 7). This is in good correspondence with
the hardness of the radiation field shown in top panels of Fig. 3.
Ogle et al. (2024) show a similar plot for M 58 to that presented



in Fig. 6 but using the 11.3µm PAH band. Thus, as a sanity
check, we also examine the relation of the 11.3 µm PAH/H 2 00 S(1) ratio (see Fig. 8) and we find a similar results when using
the 11.3 µm or 6.2 µm PAH.
Finally, we find that PAH/[Ar II] and PAH/[Ne II] ratios are
lower in shock-dominated regions, while this ratio increases in
locations where star-forming activity is significant. This together
with the results form PAH/H 2 diagnostic suggests that shocks
could play a significant role in the PAH-affected regions of
AGNs (see also Zhang et al. (2024b) for a pilot study examining the potential impact of shocks on PAHs).


**6.** **Summary and conclusions**


We presented a _JWST_ MIRI/MRS study of the IR PAH bands of
the nuclear (∼0.4 [′′] at 11 µm; ∼75 pc) and circumnuclear regions
of local AGN from the Galactic Activity, Torus and Outflow
Survey (GATOS). In particular, this work investigated the PAH
properties in AGN-dominated regions along the projected direc

Article number, page 11 of 21

_A&A proofs:_ manuscript no. draft



tion of the outflow to compare them with those in star-forming
regions and the AGN nuclei. Our main results are as follows:


1. We find that nuclear regions of intermediate luminosity
AGN (i.e. Seyfert galaxies) tend to have a larger fraction
of neutral molecules (i.e. elevated 11.3/6.2 or 11.3/7.7
PAH ratios), showing the same trend as in previous works
also using JWST/MRS observations (García-Bernete et al.
2022d).


2. We find that, even in Seyfert-like AGN, illumination and
feedback from the AGN might affect the PAH population
at kpc scales. In particular, the fraction of ionized PAH
molecules is low in the outflow zone compared with that of
star-forming regions. This result could be explained by the
preferential destruction of ionized PAH molecules (i.e. the
carriers of the ionized PAH bands; 6.2 and 7.7 µm) in hard
enviroments such as those find in the circumnuclear regions
of AGN. However, PAH molecular sizes are rather similar.


3. We find similar trends for integrated PAH/H 2 ratios using
high angular resolution spatially resolved maps. In particular, we find that values of the 6.2 µm PAH/H 2 0-0 S(1)>12
correspond to SF-dominated regions, while those regions
with 6.2 µm PAH/H 2 0-0 S(1)<5 are AGN-dominated. The
AGN-dominated limit is estimated by using a standard
hardness of the radiation field tracer ([Ne III]/[Ne II] ratios).


All of these results suggest that both AGN feedback and
hard AGN radiation fields present in Seyfert-like AGN, such
as those studied in this work, can have a significant impact on
the PAH population. This seems to be particularly important for
strongly AGN-host and jet coupled systems, for which the effects on the PAH molecules located in the disk could be maximal (e.g. NGC 5728). The carriers of the ionized PAH bands (6.2
and 7.7 µm) are less resilient than those of neutral PAH bands
(e.g. 11.3 µm). Thus, caution must be applied when using PAH
bands as star-formation rate indicators in these systems. Furthermore, PAH bands together with H 2 and low IP emission lines
allow to disentangle AGN feedback from star-forming activity.
This might be especially important for sources where high ionization potential lines are undetected. Future observations of local obscured nuclei using the unprecedented spatial resolution
and sensitivity afforded by the James Webb Space Telescope,
will be able to test the potential diagnostic power of the PAH-H 2
classification diagram in buried sources.


_Acknowledgements._ IGB is supported by the Programa Atracción de Talento
Investigador “César Nombela” via grant 2023-T1/TEC-29030 funded by the
Community of Madrid. IGB and DR acknowledge support from STFC through
grants ST/S000488/1 and ST/W000903/1. We acknowledge support from ESA
through the ESA Space Science Faculty Visitor scheme - Funding reference
ESA-SCI-SC-LE-212. AAH, LHM, and MVM acknowledge support from
grant PID2021-124665NB-I00 funded by MCIN/AEI/10.13039/501100011033
and by ERDF A way of making Europe. MPS acknowledges support from
grant RYC2021-033094-I funded by MCIN/AEI/10.13039/501100011033
and the European Union NextGenerationEU/PRTR. SGB acknowledges
support from the Spanish grant PID2022-138560NB-I00, funded by
MCIN/AEI/10.13039/501100011033/FEDER, EU. AJB acknowledges
funding support from the "FirstGalaxies" Grant from the European Research
Council (ERC) under the European Union’s Horizon 2020 research and
innovation pogram (Grant agreement No. 789056). E.B. acknowledges the
María Zambrano program of the Spanish Ministerio de Universidades funded
by the Next Generation European Union and is also partly supported by grant
RTI2018-096188-B-I00 funded by the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033. D.D.,
E.K.S.H., M.T.L., C.P. and L.Z. acknowledge grant support from the Space
Telescope Science Institute (ID: JWST-GO-01670.007-A). OG-M acknowledges


Article number, page 12 of 21



support from PAPIIT UNAM IN109123 and to the Ciencia de Frontera project
CF-2023-G-100 from CONHACYT. AA, DEA and CRA acknowledge funding
from the State Research Agency (AEI-MCINN) of the Spanish Ministry of
Science and Innovation under the grant “Tracking active galactic nuclei feedback
from parsec to kiloparsec scales”, with reference PID2022-141105NB-I00.
CR acknowledges support from Fondecyt Regular grant 1230345 and ANID
BASAL project FB210003. MS acknowledges support by the Ministry of
Science, Technological Development and Innovation of the Republic of
Serbia (MSTDIRS) through contract no. 451-03-66/2024-03/200002 with the
Astronomical Observatory (Belgrade).The authors acknowledge the ERS team
PDRs4All (Program ID: 1228; P.I. O. N. Berné) for developing their observing
program with a zero–exclusive–access period. The authors are extremely
grateful to the JWST helpdesk for their constant and enthusiastic support.
Finally, we thank the anonymous referee for their useful comments.


This work is based on observations made with the NASA/ESA/CSA
James Webb Space Telescope. The data were obtained from the Mikulski
Archive for Space Telescopes at the Space Telescope Science Institute, which
is operated by the Association of Universities for Research in Astronomy, Inc.,
under NASA contract NAS 5-03127 for JWST; and from the European JWST
archive (eJWST) operated by the ESAC Science Data Centre (ESDC) of the
European Space Agency. These observations are associated with programs
#1049, #1050, #1228 and #1670. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2017.1.00082.S, ADS/JAO.ALMA#2018.1.00113.S,
ADS/JAO.ALMA#2019.1.00618.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea),
in cooperation with the Republic of Chile. The Joint ALMA Observatory is
operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy
Observatory is a facility of the National Science Foundation operated under
cooperative agreement by Associated Universities, Inc.


**References**


Allamandola L. J., Tielens A. G. G. M., Barker J. R., 1989, ApJS, 71, 733
Allen M. G., Groves B. A., Dopita M. A., Sutherland R. S., Kewley L. J., 2008,
ApJS, 178, 20. doi:10.1086/589652
Alonso Herrero A., García-Burillo S., Pereira-Santaella M., Shimizu T., Combes
F., Hicks E. K. S., Davies R., et al., 2023, A&A, 675, A88. doi:10.1051/00046361/202346074
Alonso-Herrero A., García-Burillo S., Hönig S. F., García-Bernete I., Ramos
Almeida C., González-Martín O., López-Rodríguez E., et al., 2021, A&A,
652, A99. doi:10.1051/0004-6361/202141219
Alonso-Herrero A., Pereira-Santaella M., Rigopoulou D., García-Bernete I.,
García-Burillo S., Domínguez-Fernández A. J., Combes F., et al., 2020, A&A,
639, A43. doi:10.1051/0004-6361/202037642
Alonso-Herrero A., Pereira-Santaella M., García-Burillo S., Davies R. I.,
Combes F., Asmus D., Bunker A., et al., 2018, ApJ, 859, 144.
doi:10.3847/1538-4357/aabe30
Alonso-Herrero A., Esquej P., Roche P. F., Ramos Almeida C., GonzálezMartín O., Packham C., Levenson N. A., et al., 2016, MNRAS, 455, 563.
doi:10.1093/mnras/stv2342
Alonso-Herrero A., Ramos Almeida C., Esquej P., Roche P. F., Hernán-Caballero
A., Hönig S. F., González-Martín O., et al., 2014, MNRAS, 443, 2766.
doi:10.1093/mnras/stu1293
Antonucci R., 1993, ARA&A, 31, 473
Argyriou I., Glasse A., Law D. R., Labiano A., Álvarez-Márquez J., Patapis P., Kavanagh P. J., et al., 2023, A&A, 675, A111. doi:10.1051/00046361/202346489
Argyriou I., Wells M., Glasse A., Lee D., Royer P., Vandenbussche B., Malumuth
E., et al., 2020, A&A, 641, A150. doi:10.1051/0004-6361/202037535
Arribas S., Mediavilla E., 1993, ApJ, 410, 552. doi:10.1086/172774
Audibert A., Ramos Almeida C., García-Burillo S., Combes F., Bischetti
M., Meenakshi M., Mukherjee D., et al., 2023, A&A, 671, L12.
doi:10.1051/0004-6361/202345964
Baumgartner W. H., Tueller J., Markwardt C. B., Skinner G. K., Barthelmy S.,
Mushotzky R. F., Evans P. A., et al., 2013, ApJS, 207, 19. doi:10.1088/00670049/207/2/19
Bauschlicher C. W., Ricca A., Boersma C., Allamandola L. J., 2018, ApJS, 234,
32. doi:10.3847/1538-4365/aaa019
Beirão P., Armus L., Lehnert M. D., Guillard P., Heckman T., Draine B., Hollenbach D., et al., 2015, MNRAS, 451, 2640. doi:10.1093/mnras/stv1101
Bellocchi E., Villar Martín M., Cabrera-Lavers A., Emonts B., 2019, A&A, 626,
A89. doi:10.1051/0004-6361/201935270
Bilton L. E., 2016, MsT, 77. doi:10.5281/zenodo.164202
Bongiorno A., Schulze A., Merloni A., Zamorani G., Ilbert O., La Franca F.,
Peng Y., et al., 2016, A&A, 588, A78. doi:10.1051/0004-6361/201527436

García-Bernete et al.: PAH survival and resilience in AGN-outflows



Bosman S. E. I., Álvarez-Márquez J., Colina L., Walter F., Alonso-Herrero
A., Ward M. J., Östlin G., et al., 2023, arXiv, arXiv:2307.14414.
doi:10.48550/arXiv.2307.14414
Burtscher L., Davies R. I., Shimizu T. T., Riffel R., Rosario D. J., Hicks E. K. S.,
Lin M.-Y., et al., 2021, A&A, 654, A132. doi:10.1051/0004-6361/202140593
Chown R., Sidhu A., Peeters E., Tielens A. G. G. M., Cami J., Berné O., Habart
E., et al., 2023, arXiv, arXiv:2308.16733. doi:10.48550/arXiv.2308.16733
Combes F., García-Burillo S., Casasola V., Hunt L., Krips M., Baker A. J., Boone
F., et al., 2013, A&A, 558, A124. doi:10.1051/0004-6361/201322288
Croton D. J., Springel V., White S. D. M., De Lucia G., Frenk C. S., Gao L., Jenkins A., et al., 2006, MNRAS, 365, 11. doi:10.1111/j.1365-2966.2005.09675.x
Diamond-Stanic A. M., Rieke G. H., 2010, ApJ, 724, 140
Davies R., Baron D., Shimizu T., Netzer H., Burtscher L., de Zeeuw P. T., Genzel
R., et al., 2020, MNRAS, 498, 4150. doi:10.1093/mnras/staa2413
Davies R., Shimizu T., Pereira-Santaella M., Alonso-Herrero A., Audibert A., Bellocchi E., Boorman P., et al., 2024, arXiv, arXiv:2406.17072.
doi:10.48550/arXiv.2406.17072
Diamond-Stanic A. M., Rieke G. H., 2010, ApJ, 724, 140
Diamond-Stanic A. M., Rieke G. H., 2012, ApJ, 746, 168
Donnan F. R., García-Bernete I., Rigopoulou D., Pereira-Santaella M., AlonsoHerrero A., Roche P. F., Hernán-Caballero A., et al., 2023, MNRAS, 519,
3691. doi:10.1093/mnras/stac3729
Donnan F. R., García-Bernete I., Rigopoulou D., Pereira-Santaella
M., Roche P. F., Alonso-Herrero A., 2024, MNRAS, 529, 1386.
doi:10.1093/mnras/stae612
Donnan F. R., Rigopoulou D., García-Bernete I., 2024, MNRAS, 532, L75.
doi:10.1093/mnrasl/slae050
Draine B. T., Li A., Hensley B. S., Hunt L. K., Sandstrom K., Smith J.-D. T.,
2021, ApJ, 917, 3. doi:10.3847/1538-4357/abff51
Draine B. T., Li A., 2007, ApJ, 657, 810. doi:10.1086/511055
Draine B. T., Li A., 2001, ApJ, 551, 807
Durré M., Mould J., 2018, ApJ, 867, 149. doi:10.3847/1538-4357/aae68e
Elyajouri M., Ysard N., Abergel A., Habart E., Verstraete L., Jones A., Juvela
M., et al., 2024, arXiv, arXiv:2401.01221. doi:10.48550/arXiv.2401.01221
Esparza-Arredondo D., González-Martín O., Dultzin D., Alonso-Herrero A.,
Ramos Almeida C., Díaz-Santos T., García-Bernete I., et al., 2018, ApJ, 859,
124. doi:10.3847/1538-4357/aabcbc
Esquej P., et al., 2014, ApJ, 780, 86
Esquej P., Alonso-Herrero A., González-Martín O., Hönig S. F., HernánCaballero A., Roche P., Ramos Almeida C., et al., 2014, ApJ, 780, 86.
doi:10.1088/0004-637X/780/1/86
Esposito F., et al, 2024, A&A, in press.
Ferland G. J. et al., 2013, Rev. Mex. Astron. Astrofis., 49, 137.
Fischer T. C., Crenshaw D. M., Kraemer S. B., Schmitt H. R., 2013, ApJS, 209,
1. doi:10.1088/0067-0049/209/1/1
Gallimore J. F., et al., 2010, ApJS, 187, 172
Gardner J. P., Mather J. C., Abbott R., Abell J. S., Abernathy M., Abney
F. E., Abraham J. G., et al., 2023, PASP, 135, 068001. doi:10.1088/15383873/acd1b5
García-Bernete I., Pereira-Santaella M., González-Alfonso E., Rigopoulou
D., Efstathiou A., Donnan F. R., Thatte N., 2024b, A&A, 682, L5.
doi:10.1051/0004-6361/202348744
García-Bernete I., Alonso-Herrero A., Rigopoulou D., Pereira-Santaella M.,
Shimizu T., Davies R., Donnan F. R., et al., 2024a, A&A, 681, L7.
doi:10.1051/0004-6361/202348266
García-Bernete I., Rigopoulou D., Alonso-Herrero A., Donnan F. R., Roche
P. F., Pereira-Santaella M., Labiano A., et al., 2022d, A&A, 666, L5.
doi:10.1051/0004-6361/202244806
García-Bernete I., González-Martín O., Ramos Almeida C., Alonso-Herrero A.,
Martínez-Paredes M., Ward M. J., Roche P. F., et al., 2022, A&A, 667, A140.
doi:10.1051/0004-6361/202244230
García-Bernete I., Rigopoulou D., Aalto S., Spoon H. W. W., HernánCaballero A., Efstathiou A., Roche P. F., et al., 2022b, A&A, 663, A46.
doi:10.1051/0004-6361/202142749
García-Bernete I., Rigopoulou D., et al., 2022a, MNRAS, 509, 4256.
García-Bernete I., Alonso-Herrero A., García-Burillo S., Pereira-Santaella M.,
García-Lorenzo B., Carrera F. J., Rigopoulou D., et al., 2021, A&A, 645,
A21. doi:10.1051/0004-6361/202038256
García-Bernete I., Ramos Almeida C., Alonso-Herrero A., Ward M. J., AcostaPulido J. A., Pereira-Santaella M., Hernán-Caballero A., et al., 2019, MNRAS, 486, 4917. doi:10.1093/mnras/stz1003
García-Bernete I., Ramos Almeida C., Landt H., Ward M. J., Balokovi´c M.,
Acosta-Pulido J. A., 2017, MNRAS, 469, 110
García-Bernete I., et al., 2015, MNRAS, 449, 1309
García-Burillo S., Hicks E. K. S., Alonso-Herrero A., Pereira-Santaella
M., Usero A., Querejeta M., González-Martin O., et al., 2024, arXiv,
arXiv:2406.11398. doi:10.48550/arXiv.2406.11398



García-Burillo S., Alonso-Herrero A., Ramos Almeida C., González-Martín
O., Combes F., Usero A., Hönig S., et al., 2021, A&A, 652, A98.
doi:10.1051/0004-6361/202141075
García-Burillo S., Combes F., Ramos Almeida C., Usero A., Alonso-Herrero
A., Hunt L. K., Rouan D., et al., 2019, A&A, 632, A61. doi:10.1051/00046361/201936606
García-Burillo S., Combes F., Ramos Almeida C., Usero A., Krips M., AlonsoHerrero A., Aalto S., et al., 2016, ApJL, 823, L12. doi:10.3847/20418205/823/1/L12
García-Burillo S., Combes F., Usero A., Aalto S., Krips M., Viti S.,
Alonso-Herrero A., et al., 2014, A&A, 567, A125. doi:10.1051/00046361/201423843
González-Martín O., Rodríguez-Espinosa J. M., Díaz-Santos T., Packham C.,
Alonso-Herrero A., Esquej P., Ramos Almeida C., et al., 2013, A&A, 553,
A35. doi:10.1051/0004-6361/201220382
Groves B., Dopita M., Sutherland R., 2006, A&A, 458, 405
Habart E., Peeters E., Berné O., Trahin B., Canin A., Chown R., Sidhu A., et al.,
2023, arXiv, arXiv:2308.16732. doi:10.48550/arXiv.2308.16732
Hernán-Caballero A., Hatziminaoglou E., 2011, MNRAS, 414, 500.
doi:10.1111/j.1365-2966.2011.18413.x
Hermosa Muñoz L., Alonso-Herrero A., Pereira-Santaella M., García-Bernete
I., García-Burillo S., García-Lorenzo B., Davies R., et al., 2024, arXiv,
arXiv:2407.15807. doi:10.48550/arXiv.2407.15807
Hermosa Muñoz L., Cazzoli S., Márquez I., Masegosa J., Chamorro-Cazorla
M., Gil de Paz A., Castillo-Morales Á., et al., 2024, A&A, 683, A43.
doi:10.1051/0004-6361/202347675
Hernandez S., Jones L., Smith L. J., Togi A., Aloisi A., Blair W. P., Hirschauer
A. S., et al., 2023, ApJ, 948, 124. doi:10.3847/1538-4357/acc837
Hönig S. F., Kishimoto M., Gandhi P., Smette A., Asmus D., Duschl W., Polletta
M., et al., 2010, A&A, 515, A23. doi:10.1051/0004-6361/200913742
Imanishi M., Nguyen D. D., Wada K., Hagiwara Y., Iguchi S., Izumi T.,
Kawakatu N., et al., 2020, ApJ, 902, 99. doi:10.3847/1538-4357/abaf50
Imanishi M., Nakanishi K., Izumi T., Wada K., 2018, ApJL, 853, L25.
doi:10.3847/2041-8213/aaa8df
Jarvis M. E., Harrison C. M., Mainieri V., Alexander D. M., Arrigoni Battaia F., Calistro Rivera G., Circosta C., et al., 2021, MNRAS, 503, 1780.
doi:10.1093/mnras/stab549
Jensen J. J., Hönig S. F., Rakshit S., Alonso-Herrero A., Asmus D., Gandhi P.,
Kishimoto M., et al., 2017, MNRAS, 470, 3071. doi:10.1093/mnras/stx1447
Kaneda H., Onaka T., Sakon I., Kitayama T., Okada Y., Suzuki T., 2008, ApJ,
684, 270. doi:10.1086/590243
Kaufman M. J., Wolfire M. G., Hollenbach D. J., 2006, ApJ, 644, 283.
doi:10.1086/503596
Kerkeni B., García-Bernete I., Rigopoulou D., Tew D. P., Roche P. F., Clary
D. C., 2022, MNRAS, 513, 3663. doi:10.1093/mnras/stac976
Kinney A. L., Schmitt H. R., Clarke C. J., Pringle J. E., Ulvestad J. S., Antonucci
R. R. J., 2000, ApJ, 537, 152. doi:10.1086/309016
Kristensen L. E., Godard B., Guillard P., Gusdorf A., Pineau des Forêts G., 2023,
A&A, 675, A86. doi:10.1051/0004-6361/202346254
Labiano A., Argyriou I., Álvarez-Márquez J., Glasse A., Glauser A., Patapis P.,
Law D., et al., 2021, A&A, 656, A57. doi:10.1051/0004-6361/202140614
Labiano A., Azzollini R., Bailey J., Beard S., Dicken D., García-Marín M., Geers
V., et al., 2016, SPIE, 9910, 99102W. doi:10.1117/12.2232554
Labiano A., García-Burillo S., Combes F., Usero A., Soria-Ruiz R., Piqueras
López J., Fuente A., et al., 2014, A&A, 564, A128. doi:10.1051/00046361/201323123
Labiano A., García-Burillo S., Combes F., Usero A., Soria-Ruiz R., Tremblay
G., Neri R., et al., 2013, A&A, 549, A58. doi:10.1051/0004-6361/201220118
Lai T. S.-Y., Armus L., U V., Díaz-Santos T., Larson K. L., Evans A., Malkan
M. A., et al., 2022, ApJL, 941, L36. doi:10.3847/2041-8213/ac9ebf
Lai T. S.-Y., Armus L., Bianchin M., Díaz-Santos T., Linden S. T., Privon G. C.,
Inami H., et al., 2023, ApJL, 957, L26. doi:10.3847/2041-8213/ad0387
Leach S., 1986, JESRP, 41, 427
Leach S., Eland J. H. D., and Price S. D., The Journal of Physical Chemistry,
1989, 93, 22, 7575-7583. DOI: 10.1021/j100359a013
Li Y., Li M., Yang T., Wang Y., Jia S., Liu X., Xu Z., 2022, CP, 553, 111358.
doi:10.1016/j.chemphys.2021.111358
Li A., 2020, NatAs, 4, 339
Li A., Draine B. T., 2002, ApJ, 572, 232. doi:10.1086/340285
Maloney P. R., Hollenbach D. J., Tielens A. G. G. M., 1996, ApJ, 466, 561.
doi:10.1086/177532
Martínez-Paredes M., Alonso-Herrero A., Aretxaga I., Ramos Almeida C.,
Hernán-Caballero A., González-Martín O., Pereira-Santaella M., et al., 2015,
MNRAS, 454, 3577. doi:10.1093/mnras/stv2134
Martínez-Paredes M., Aretxaga I., González-Martín O., Alonso-Herrero A., Levenson N. A., Ramos Almeida C., López-Rodríguez E., 2019, ApJ, 871, 190.
doi:10.3847/1538-4357/aafa18


Article number, page 13 of 21

_A&A proofs:_ manuscript no. draft



Mateos S., Carrera F. J., Barcons X., Alonso-Herrero A., Hernán-Caballero A.,
Page M., Ramos Almeida C., et al., 2017, ApJL, 841, L18. doi:10.3847/20418213/aa7268
McMullin J. P., Waters B., Schiebel D., et al., 2007, ASPC, 376, 127.
Morganti R., Oosterloo T., Oonk J. B. R., Frieswijk W., Tadhunter C., 2015,
A&A, 580, A1. doi:10.1051/0004-6361/201525860
Nagar N. M., Oliva E., Marconi A., Maiolino R., 2002, A&A, 391, L21.
doi:10.1051/0004-6361:20021039
Nesvadba N. P. H., Boulanger F., Salomé P., Guillard P., Lehnert M. D.,
Ogle P., Appleton P., et al., 2010, A&A, 521, A65. doi:10.1051/00046361/200913333
Ogle P. M., López I. E., Reynaldi V., Togi A., Rich R. M., Román J., Caceres O.,
et al., 2024, ApJ, 962, 196. doi:10.3847/1538-4357/ad1242
Ogle P., Boulanger F., Guillard P., Evans D. A., Antonucci R., Appleton P. N., Nesvadba N., et al., 2010, ApJ, 724, 1193. doi:10.1088/0004637X/724/2/1193
Pasquini S., Peeters E., Schefter B., Khan B., Sidhu A., Chown R., Cami J., et
al., 2023, arXiv, arXiv:2311.01163. doi:10.48550/arXiv.2311.01163
Peeters E., Habart E., Berne O., Sidhu A., Chown R., Van De Putte D., Trahin
B., et al., 2023, arXiv, arXiv:2310.08720. doi:10.48550/arXiv.2310.08720
Peeters E., Spoon H. W. W., Tielens A. G. G. M., 2004, ApJ, 613, 986
Peeters E., Hony S., Van Kerckhoven C., Tielens A. G. G. M., Allamandola L. J., Hudgins D. M., Bauschlicher C. W., 2002, A&A, 390, 1089.
doi:10.1051/0004-6361:20020773
Peralta de Arriba L., Alonso-Herrero A., García-Burillo S., García-Bernete I.,
Villar-Martín M., García-Lorenzo B., Davies R., et al., 2023, A&A, 675, A58.
doi:10.1051/0004-6361/202245408
Pereira-Santaella M., Álvarez-Márquez J., García-Bernete I., Labiano A., Colina L., Alonso-Herrero A., Bellocchi E., et al., 2022, A&A, 665, L11.
doi:10.1051/0004-6361/202244725
Pereira-Santaella M., Rigopoulou D., Farrah D., Lebouteiller V., Li J., 2017,
MNRAS, 470, 1218. doi:10.1093/mnras/stx1284
Pereira-Santaella M., Diamond-Stanic A. M., Alonso-Herrero A., Rieke G. H.,
2010, ApJ, 725, 2270
Pier E. A., Krolik J. H., 1992, ApJ, 401, 99. doi:10.1086/172042
Ramos Almeida C., Esparza-Arredondo D., González-Martín O., García-Bernete
I., Pereira-Santaella M., Alonso-Herrero A., Acosta-Pulido J. A., et al., 2023,
A&A, 669, L5. doi:10.1051/0004-6361/202245409
Ramos Almeida C., Bischetti M., García-Burillo S., Alonso-Herrero A.,
Audibert A., Cicone C., Feruglio C., et al., 2022, A&A, 658, A155.
doi:10.1051/0004-6361/202141906
Ramos Almeida C., Ricci C., 2017, NatAs, 1, 679
Ramos Almeida C., et al., 2014, MNRAS, 445, 1130
Ricci C., Ueda Y., Koss M. J., Trakhtenbrot B., Bauer F. E., Gandhi P., 2015,
ApJL, 815, L13. doi:10.1088/2041-8205/815/1/L13
Ricci C., et al., 2017, ApJS, 233, 17
Rieke G. H., Wright G. S., Böker T., Bouwman J., Colina L., Glasse A., Gordon
K. D., et al., 2015, PASP, 127, 584. doi:10.1086/682252
Rigby J., Perrin M., McElwain M., Kimble R., Friedman S., Lallo M., Doyon R.,
et al., 2023, PASP, 135, 048001. doi:10.1088/1538-3873/acb293
Rigopoulou D., Donnan F. R., García-Bernete I., Pereira-Santaella M., AlonsoHerrero A., Davies R., Hunt L. K., et al., 2024, arXiv, arXiv:2406.11415.
doi:10.48550/arXiv.2406.11415
Rigopoulou D., Barale M., Clary D. C., Shan X., Alonso-Herrero
A., García-Bernete I., Hunt L., et al., 2021, MNRAS, 504, 5287.
doi:10.1093/mnras/stab959
Rigopoulou D., Spoon, H.W.W, Genzel R., Lutz, D., Moorwood A. F. M., Tran,
Q.D., 1999, AJ, 118, 2625
Roche P. F., Aitken D. K., Smith C. H., Ward M. J., 1991, MNRAS, 248, 606
Ruschel-Dutra D., Pastoriza M., Riffel R., Sales D. A., Winge C., 2014, MNRAS,
438, 3434. doi:10.1093/mnras/stt2448
Sales D. A., Pastoriza M. G., Riffel R., Winge C., 2013, MNRAS, 429, 2634.
doi:10.1093/mnras/sts542
Schmitt H. R., Ulvestad J. S., Antonucci R. R. J., Kinney A. L., 2001, ApJS, 132,
199. doi:10.1086/318957
Schommer R. A., Caldwell N., Wilson A. S., Baldwin J. A., Phillips M. M.,
Williams T. B., Turtle A. J., 1988, ApJ, 324, 154. doi:10.1086/165887
Shimizu T. T., Davies R. I., Lutz D., Burtscher L., Lin M., Baron D., Davies
R. L., et al., 2019, MNRAS, 490, 5860. doi:10.1093/mnras/stz2802
Siebenmorgen R., et al., 2004, A&A, 414, 123
Smaji´c S., Fischer S., Zuther J., Eckart A., 2012, A&A, 544, A105.
doi:10.1051/0004-6361/201118256
Smith J. D. T., et al., 2007a, ApJ, 656, 770
Speranza G., Ramos Almeida C., Acosta-Pulido J. A., Audibert A., Holden L. R.,
Tadhunter C. N., Lapi A., et al., 2024, A&A, 681, A63. doi:10.1051/00046361/202347715
Spilker J. S., Phadke K. A., Aravena M., Archipley M., Bayliss M. B., Birkin
J. E., Béthermin M., et al., 2023, Natur, 618, 708. doi:10.1038/s41586-02305998-6


Article number, page 14 of 21



Spinoglio L., Andreani P., Malkan M. A., 2002, ApJ, 572, 105
Thean A., Pedlar A., Kukula M. J., Baum S. A., O’Dea C. P., 2000, MNRAS,
314, 573. doi:10.1046/j.1365-8711.2000.03401.x
Thomas A. D., Dopita M. A., Shastri P., Davies R., Hampton E., Kewley L.,
Banfield J., et al., 2017, ApJS, 232, 11. doi:10.3847/1538-4365/aa855a
Thornley M. D., Schreiber N. M. F., Lutz D., Genzel R., Spoon H. W. W., Kunze
D., Sternberg A., 2000, ApJ, 539, 641
Tielens A., 2021, moas.book. doi:10.1017/9781316718490
Tielens A. G. G. M., 2008, ARA&A, 46, 289.
doi:10.1146/annurev.astro.46.060407.145211
Tielens A. G. G. M., 2005, pcim.book
Venturi G., Cresci G., Marconi A., Mingozzi M., Nardini E., Carniani S., Mannucci F., et al., 2021, A&A, 648, A17. doi:10.1051/0004-6361/202039869
Véron-Cetty M.-P., Véron P., 2006, A&A, 455, 773
Voit G. M., 1992, MNRAS, 258, 841
Wells M., Pel J.-W., Glasse A., Wright G. S., Aitink-Kroes G., Azzollini R.,
Beard S., et al., 2015, PASP, 127, 646. doi:10.1086/682281
M., Pel, J.-W., Glasse, A., et al. 2015, PASP, 127, 646
Wenzel G., Joblin C., Giuliani A., Rodriguez Castillo S., Mulas G., Ji M., Sabbah
H., et al., 2020, A&A, 641, A98. doi:10.1051/0004-6361/202038139
Wilson A. S., Braatz J. A., Heckman T. M., Krolik J. H., Miley G. K., 1993,
ApJL, 419, L61. doi:10.1086/187137
Wilson A. S., Baldwin J. A., Ulvestad J. S., 1985, ApJ, 291, 627.
doi:10.1086/163103
Wright, G. S., Wright, D., Goodson, G. B., et al. 2015, PASP, 127, 595
Wu Y., Helou G., Armus L., Cormier D., Shi Y., Dale D., Dasyra K., et al., 2010,
ApJ, 723, 895
Zhang L., García-Bernete I., et al., 2024b, ApJ, submitted.
Zhang L., et al., 2024, ApJ, in press.
Zhang L., Ho L. C., 2023b, ApJL, 953, L9. doi:10.3847/2041-8213/acea73
Zhang L., Ho L. C., 2023a, ApJ, 943, 60. doi:10.3847/1538-4357/acab60
Zhang L., Ho L. C., Li A., 2022, ApJ, 939, 22. doi:10.3847/1538-4357/ac930f


1 Centro de Astrobiología (CAB), CSIC-INTA, Camino Bajo del
Castillo s/n, E-28692, Villanueva de la Cañada, Madrid, Spain
2 Department of Physics, University of Oxford, Keble Road, Oxford
OX1 3RH, UK
3 School of Sciences, European University Cyprus, Diogenes street,
Engomi, 1516 Nicosia, Cyprus
4 Instituto de Física Fundamental, CSIC, Calle Serrano 123, 28006
Madrid, Spain
5 Max-Planck-Institut fur extraterrestrische Physik, Postfach 1312,
D-85741 Garching, Germany
6 Observatorio Astronómico Nacional (OAN-IGN)-Observatorio de
Madrid, Alfonso XII, 3, 28014, Madrid, Spain
7 Telespazio UK for the European Space Agency (ESA), ESAC, Camino
Bajo del Castillo s/n, 28692 Villanueva de la Cañada, Spain
8 Department of Physics and Astronomy, The University of Texas at
San Antonio, 1 UTSA Circle, San Antonio, Texas, 78249-0600, USA
9 Instituto de Astrofísica de Canarias, Calle Vía Láctea, s/n, E-38205
La Laguna, Tenerife, Spain
10 Departamento de Astrofísica, Universidad de La Laguna, E-38206
La Laguna, Tenerife, Spain
11 Departmento de Física de la Tierra y Astrofísica, Fac. de CC Físicas,
Universidad Complutense de Madrid, 28040 Madrid, Spain
12 Instituto de Física de Partículas y del Cosmos IPARCOS, Fac. CC
Físicas, Universidad Complutense de Madrid, 28040 Madrid, Spain
13 LERMA, Observatoire de Paris, Collège de France, PSL University,
CNRS, Sorbonne University, Paris
14 Department of Physics and Astronomy, University of Alaska
Anchorage, Anchorage, AK 99508-4664, USA
15 School of Physics & Astronomy, University of Southampton, Highfield, Southampton SO171BJ, UK
16 Instituto de Radioastronomía and Astrofísica (IRyA-UNAM), 3-72
(Xangari), 8701, Morelia, Mexico
17 National Astronomical Observatory of Japan, National Institutes of
Natural Sciences (NINS), 2-21-1 Osawa, Mitaka, Tokyo 181-8588,
Japan
18 Department of Astronomy, School of Science, The Graduate University for Advanced Studies, SOKENDAI, Mitaka, Tokyo 181-8588,
Japan
19 Space Telescope Science Institute, 3700 San Martin Drive, Baltimore,
Maryland 21218, USA

García-Bernete et al.: PAH survival and resilience in AGN-outflows


20 Kavli Institute for Particle Astrophysics & Cosmology (KIPAC),
Stanford University, Stanford, CA 94305, USA
21 Instituto de Estudios Astrofísicos, Facultad de Ingeniería y Ciencias,
Universidad Diego Portales, Avenida Ejercito Libertador 441, Santiago,
Chile
22 Astronomical Observatory, Volgina 7, 11060 Belgrade, Serbia
23 Sterrenkundig Observatorium, Universiteit Gent, Krijgslaan 281-S9,
Gent B-9000, Belgium
24 Centro de Astrobiología (CAB), CSIC-INTA, Ctra. de Ajalvir, km 4,
28850 Torrejón de Ardoz, Madrid, Spain
25 Centre for Extragalactic Astronomy, Durham University, South Road,
Durham DH1 3LE, UK



Article number, page 15 of 21

_A&A proofs:_ manuscript no. draft



**Appendix A:** **Mid-IR modelling and aperture**
**selection**


We extracted the JWST/MRS spectra from the nuclear regions of
the three sources studied here following the same method as in
García-Bernete et al. (2024a). In addition, we selected a number
of circumnuclear regions in the three targets to investigate similarities and differences in the PAH properties between nuclear
regions, and outflow and star-forming zones. For the extended
emission, we use apertures ranging of 1 [′′] . 0 and 1 [′′] . 5 diameter (see
Fig. A.1).
To fit the mid-IR continuum and in particular the PAH emission features of star-forming regions we use a modified version
of PAHFIT (Smith et al. 2007a) to work with the higher spectral
resolution JWST data (Donnan et al. 2023). However, PAHFIT
does not produce successful fits for the nuclear regions of the
sources studied here due to the complexity of the dust continuum and the high levels of extinction present. Therefore, we use
a novel technique using a differential extinction model (i.e. the
strength of extinction varies with wavelength) which probes different layers of the dust and produces satisfactory fits to deeply
obscured sources (Donnan et al. 2024). We note that the newly
developed model is in agreement with PAHFIT for relatively unobscured sources as star-forming regions. We refer the reader to
Donnan et al. (2024) for a full description of the model. The fits
for the nuclear regions of NGC 5506 and NGC 5728 are shown
in Fig. A.2. In Fig. A.3 we show an example of a fit for a SFdominated region. In Tables A.1, A.2 and A.3, we list the fluxes
of the MIR PAH features for the nuclei, circumnuclear regions
and Orion Bar, respectively.
We selected a number of circumnuclear regions in
NGC 5506, NGC 5728 and NGC 7172. Considering the morphology of the circumnuclear emission of the sources (see Section 4), we chose regions including emission along the SF ring
(1 [′′] diameter extraction apertures), the outflow (1.5 [′′] diameter extraction apertures) and high-velocity dispersion region (perpendicular to the jet; 1.5 [′′] diameter extraction apertures) and galaxy
disks of NGC 5506 and NGC 7172 (1.5 [′′] diameter extraction
apertures). Given the geometry of NGC 5506 and NGC 7172
(e.g. Esposito et al. 2024; Hermosa Muñoz et al. 2024), the
outflow is located behind the disk for the southern region
of NGC 5506 (Disk3) and the northern region of NGC 7172
(Disk3). Therefore, these regions show values of their PAH ratios similar to those of the disk. In Fig. A.4 we present the same
PAH diagram as in Fig. 5 but including all the individual regions.


**Appendix B:** **Orion Bar**


For comparison, we also include in our analysis observations of
the Orion Bar, which have been already presented in Chown et
al. (2023), Habart et al. (2023), Peeters et al. (2023), Pasquini et
al. (2023) and Elyajouri et al. (2024)). This was observed was
taken using _JWST_ as part of the Director’s Discretionary Early
Release Science (ERS) Program ID: 1228 (P.I. O. N. Berné). The
extracted spectra consist of a H ii, an atomic PDR and three regions of dissociation fronts (DF1, DF2, DF3) (see e.g. Fig. 1 of
Peeters et al. 2023). In particular, we use the fully reduced version of the spectra presented in Chown et al. (2023), which are
publicly available in webpage [9] of the ERS team PDRs4All. Using these spectra, we measured the PAH ratios (see Table A.3
using the same method as in Appendix A.


9 https://pdrs4all.org/seps/


Article number, page 16 of 21



**Appendix C:** **Notes on individual objects**


_Appendix C.1:_ _NGC 5728_


NGC 5728 is a type 2 AGN also classified as Compton thick
AGN (Véron-Cetty & Véron 2006). It has a circumnuclear stellar ring (∼800 pc; e.g., Schommer et al. 1988; Durré & Mould
2018; Shimizu et al. 2019 and references therein) and large stellar bar (∼11 Kpc; Schommer et al. 1988; Durré & Mould 2018).
NGC 5728 also presents ionization cones detected in [O III]
and Hα (∼1.5 kpc; PA∼120) at both sizes of the nucleus (e.g.,
Schommer et al. 1988; Arribas & Mediavilla 1993; Wilson et al.
1993; Durré & Mould 2018; Shimizu et al. 2019). In the same
orientation, 6 and 20 cm radio observations show a compact radio core with one-sided which is related to the emission of a
radio jet (Schommer et al. 1988; Durré & Mould 2018). Figure
C.1 shows a sketch summarising the geometry model derived by
Shimizu et al. (2019). Note that the position angle of the cone
has been updated to that used in Davies et al. (2024) (i.e. position angle of -60 [◦] with an opening angle of ±30 [◦] . The 3D scheme
show the strong geometrical coupling between the AGN outflow
(and jet) and the host galaxy disk.
NGC 5728 has a star-foming ring of ∼1 kpc size, showing
several bright [Ne II] clumps (see Davies et al. 2024). The high
ionization potential (e.g. [Ne V] and [S V]) emission line maps
show the prominent ionization cones in the galaxy (see Fig. 2).
This region coincides with outflow located in the SE to NW direction (see Fig. 2; also Durré & Mould 2018; Shimizu et al.
2019). We also note that MIRI/MRS velocity dispersion maps of

[Ne III], [Ne V] and [S V] reveal a high-velocity dispersion region in an almost perpendicular region of the main axis of the
outflow (see Fig. 4; also Davies et al. 2024). Durré & Mould
(2018) has also proposed the presence of a nuclear bar in the
optical ratios. The [Fe II] intensity map shows the presence of
shocks operating in the ionization cones orientation (see Fig. 2).


_Appendix C.2:_ _NGC 5506_


NGC 5506 is classified as a narrow-line Sy 1 or type 2 AGN (see
Nagar et al. 2002 for further discussion). Moreover, the host
galaxy disk is close to edge-on (i _disk_ ∼ 76 [◦] ; Fischer et al. 2013)
and, thus, dust in the galaxy disk might be responsible for a significant part of the nuclear obscuration. The NLR bicone emission extends over few kpc and is elongated in the north-south direction (Wilson, Baldwin, & Ulvestad 1985; Fischer et al. 2013).
VLA radio observations show a compact nucleus and a radio jet
is extended along PA∼70 [◦] and i∼82 [◦] (Kinney et al. 2000). In
Fischer et al. (2013) (their Fig. 21), the authors showed the geometry of NGC 5506 derived from the NLR modeling (similarly
as in Fig. C.1).


_Appendix C.3:_ _NGC 7172_


NGC 7172 hosts a type 2 AGN with a prominent dust lane (e.g.
Smaji´c et al. 2012 and references therein). A two-sided ionization cones with broad opening angle (∼120 [◦] ) is detected by using optical integral field spectroscopy (e.g., Thomas et al. 2017).
ALMA CO(3-2) observations showed the presence of a cold
molecular gas ring (∼500-700 pc), which is not only rotating
but also outflowing (e.g., Alonso Herrero et al. 2023). VLA observations detected a nuclear point-like emission and faint radio
emission elongated to the northeast and southwest of the nucleus
(e.g., Thean et al. 2000). This faint radio emission located in the
same orientation as the ionized cone, which suggest that might

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig. A.1.** Maps showing the selected apertures. From left to right panels: NGC 5506, NCG 5728 and NGC 7172. Top panels: 6.2 µm PAH feature
intensity map. The white contours are the 11.3 µm PAH emission on a logarithmic scale (same values as in bottom panels of Fig. 3). Bottom panels:

[Ne II] 12.81 µm intensity map. North is up and east is to the left, and offsets are measured relative to the AGN. Black circles correspond with the
extracted apertures.


Galaxy PAHλ6.2µm PAHλ7.7µm PAHλ8.6µm PAHλ11.3µm PAHλ17.0µm
(1) (2) (3) (4) (5) (6)
NGC 5506 <13.5 88.30 0.13 49.53 <84.70

NGC 5728 <3.47 26.82 1.22 12.32 <19.63

NGC 7172 ... ... .... .... ....
**Table A.1.** Nuclear PAH measurements. Fluxes and errors are in units of 10 [−][14] erg s [−][1] cm [−][2] .


be related with a low power radio jet (e.g. Alonso Herrero et al.
2023).


Article number, page 17 of 21

_A&A proofs:_ manuscript no. draft


Region PAHλ6.2µm PAHλ7.7µm PAHλ8.6µm PAHλ11.3µm PAHλ12.7µm PAHλ17.0µm
(1) (2) (3) (4) (5) (6) (7)
NGC 5728-SF1 5.65 17.66 3.90 5.33 3.59 2.12

NGC 5728-SF2 1.61 2.72 0.54 2.09 1.35 0.97

NGC 5728-SF3 1.28 4.48 0.97 3.85 2.44 1.70

NGC 5728-SF4 4.16 11.18 2.12 4.32 2.80 2.10

NGC 5728-SF5 4.56 14.67 2.93 5.94 3.81 2.39

NGC 5728-SF6 2.46 7.36 1.36 3.85 2.52 1.43

NGC 5728-SF7 1.91 6.41 1.46 3.36 1.87 1.49

NGC 5728-SF8 2.41 8.79 1.70 2.80 2.61 1.93

NGC 5728-SF9 1.99 5.97 1.38 4.02 2.25 1.83

NGC 5728-SF10 1.94 5.49 1.18 2.86 1.99 1.02

NGC 5728-SF11 2.50 8.63 1.97 2.73 2.06 1.30

NGC 5728-SF12 3.71 13.13 2.83 4.61 3.51 1.91

NGC 5728-D1 2.68 6.82 1.84 3.38 2.31 3.62

NGC 5728-D2 2.24 7.26 1.46 4.34 2.62 2.42

NGC 5728-Out1 1.82 5.16 1.10 3.57 2.19 1.76

NGC 5728-Out2 2.08 7.56 1.53 4.54 2.78 3.38

NGC 5728-Out3 3.80 9.83 2.09 5.41 3.14 2.25

NGC 5506-Disk1 54.85 214.01 54.65 53.37 31.77 20.35

NGC 5506-Disk2 45.80 194.97 41.07 57.03 45.37 19.79

NGC 5506-Disk3 4.11 19.53 5.33 5.45 15.13 8.84

NGC 5506-Out 4.82 27.47 7.11 13.38 17.99 4.06

NGC 7172-Disk1 42.56 204.19 23.89 57.62 39.74 11.40

NGC 7172-Disk2 34.76 172.98 22.45 50.80 40.38 17.48

NGC 7172-Disk3 13.62 58.86 8.33 20.16 9.43 3.01

NGC 7172-Out 7.79 46.91 5.15 29.53 12.39 1.39
**Table A.2.** Circumnuclear PAH measurements. Fluxes are in units of 10 [−][14] erg s [−][1] cm [−][2] .


Region 6.2/7.7 µm 11.3/7.7 µm Ref.
PAH ratio PAH ratio
(1) (2) (3) (4)
Orion H ii region 0.35±0.05 0.63±0.05 This work
(d=0.224 pc to θ [1] Ori C)
Orion atomic PDR 0.34±0.05 0.31±0.03 This work

Orion dissociation front 1 0.38±0.07 0.29±0.03 This work

Orion dissociation front 2 0.37±0.06 0.35±0.04 This work

Orion dissociation front 3 0.33±0.04 0.33±0.03 This work

NGC 6552 (AGN) 0.22±0.03 0.43±0.05 García-Bernete et al. 2022d
NGC 7319 (AGN) [0.22-0.31] <1.75 García-Bernete et al. 2022d
NGC 7469 (AGN) 0.31±0.04 0.53±0.05 García-Bernete et al. 2022d
Average SF regions of NGC 3256 0.30±0.02 0.29±0.02 Rigopoulou et al. 2024
Average SF-ring of NGC 7469 0.29±0.06 0.23±0.05 García-Bernete et al. 2022d
**Table A.3.** PAH ratios of Orion from the measurements described in Appendix B.


Article number, page 18 of 21

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig. A.3.** Example of the mid-IR spectral modelling of a SF-dominated
region of NGC 5728. The JWST/MRS rest-frame spectra and model fits
correspond to the black and red solid lines. We show the continuum
(brown solid lines) and the fitted PAH features (orange solid lines).


**Fig. A.2.** Mid-IR spectral modelling of the nuclear regions of NGC 5506
(top panel) and NGC 5728 (bottom panel). The JWST/MRS rest-frame
spectra and model fits correspond to the black and red solid lines. We
show the continuum (brown solid lines) and the fitted PAH features (orange solid lines). Note that NGC 7172 does not show nuclear PAH emission and, thus, it is not included in this plot.


Article number, page 19 of 21

_A&A proofs:_ manuscript no. draft


**Fig. A.4.** Same as Fig. 5, but including all the individual regions. In Tables A.1, A.2 and A.3 we list the measured PAH fluxes.


Article number, page 20 of 21

García-Bernete et al.: PAH survival and resilience in AGN-outflows


**Fig.** **C.1.** 3D scheme for the geometry of NGC 5728 derived from the
NLR modeling by Shimizu et al. (2019). Note that the position angle
of the cone has been updated to that used in Davies et al. (2024). The
bicone indicates the AGN outflow (blue and redshifted velocities). The
green line represents the jet axis. The purple line correspond to the perpendicular direction of the jet-axis (i.e. high velocity dispersion region
in Fig. 4). North is up and east is left.



Article number, page 21 of 21


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Compute Pearson's correlation coefficients spaxel-by-spaxel between 11.3 µm PAH, H2 0-0 S(1) 17.03 µm, and ALMA CO(3–2) intensity maps.",
  "failed_quote": "Performing a spaxel by spaxel analysis, NGC 5506 and NGC 7172 show a tight correlation between the 11.3 µm PAH band and CO (3-2) emission (see Table 2)."
 }
]
```
