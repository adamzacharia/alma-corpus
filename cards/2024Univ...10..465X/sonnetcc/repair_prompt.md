# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024Univ...10..465X\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Introduction

Among the over 5000 exoplanets discovered to date, only less than 30 are directly imaged (e.g., (cite: currie23)). While indirect exoplanet detection methods (i.e., radial velocity, transiting) contribute to the majority of the detected exoplanets, these methods are subject to stellar activities (e.g., (cite: lovis10; zhu21)) and thus could only detect exoplanets for ${\gtrsim}1$ Gyr-old stars. In comparison, directly imaged planets are around young systems that could be ${\lesssim}10$ Myr old (e.g., (cite: keppler18; haffert19)). The difference in the mass-period distribution of detected exoplanets in systems with different evolutionary stages (e.g., (cite: bae18)) calls for more directly imaged exoplanets to complement our understanding of planetary system evolution.

While existing high-contrast imaging surveys of exoplanets over the past decade have low detection rates for exoplanets (e.g., (cite: nielsen20; vigan21)), targeted campaigns are becoming more successful in imaging stellar and planetary companions at high contrast (e.g., (cite: bohn20; franson23; currie23b; matthews24)). However, targeted campaigns infer planetary existence based on stellar signal deviations (e.g., astrometry, radial velocity), and this could require decades of monitoring of stars. Around young stars that were not monitored due to increased stellar activities, young planets can gravitationally interact with their birthplaces—the protoplanetary disks, and leave observable subsignatures (e.g., spirals, gaps) on these surrounding environments (e.g., (cite: dong17; dong15planet; bae16)). With some assumptions, we can infer planetary existence—and even their mass, location, and orbit – based on substructures created by planet-disk interaction (e.g., (cite: dong15planet; bae16; teague18)).

Among the planet-induced subsignatures, a pair of nearly symmetric spiral arms can be driven by a single $5$–$10M_{\rm Jup}$ companion on a wide orbit (cite: dong15planet; bae16; dong18). With the capabilities of the current generation of high-contrast imagers, the age, mass, and orbits of these planets make them the best targets for planet imaging (cite: bae18). In fact, based on the co-motion between an M-star and a spiral, Ref. (cite: xie23) validated the theory of companion-driven spirals. This provides both theoretical and observational support to locate spiral-arm-driving planets based on spiral motion measurements (cite: ren20).

The current generation of high-contrast imagers has resolved nearly two dozen spiral arm systems in the past decade (e.g., (cite: benisty15; wagner15; shuai22)). With polarized light observations offering the best quality images for morphological analysis (e.g., (cite: monnier19)), we can obtain precise motion for the spiral arms with images spanning ${\sim}5$-yr or mor (e.g., (cite: ren20; xie21)). The measured motion rate (i.e., angular speed) allows us to distinguish the leading motion and thus formation mechanisms for spiral arms (cite: dong18; ren20). Specifically, if a spiral is driven by a companion, it is expected to rotate entirely as a rigid body at an identical rate as the driver. This thus allows the prediction of the orbit of these hidden planetary drivers (e.g., (cite: ren20; xie21; ren23v1247; safonov22)) for follow-up targeted imaging efforts (e.g., (cite: wagner19; cugno24)). However, despite the validated theory of companion-disk interaction (i.e., HD 100453: (cite: xie23)), none of the planetary driver candidates have been confirmed.

Spiral motion rates can guide targeted high-contrast imaging to further find and characterize the spiral-arm-driving planets. This requires accurate and precise spiral motion rates to guide observation design for high-contrast imaging. To best characterize the motion rates, we need to observe the spirals at different temporal epochs, ideally with identical data quality (e.g., wavelength, instrument setup, exposure time) (cite: ren20). Among existing spiral arm systems, e.g., (cite: shuai22), only one system has derived motion rates consistent with being driven by a single planet (cite: ren20). While there is an ongoing survey to re-observe known spiral systems and characterize their motion (cite: ren23v1247), it is necessary to explore the stability of the preliminary spiral motion rates using observations with longer temporal separations.

With an estimated age of $12_{-6}^{+4}$ Myr and stellar mass of $1.6\pm0.1M_\odot$ (cite: garufi18), the SAO 206462 (i.e., HD 135344 B) system is located at $135.0\pm0.4$ pc (cite: GaiaDR3). The scattered light asymmetry in 2009 *Hubble Space Telescope* near-infrared imaging observations in Ref. (cite: grady09) was resolved to be two spiral arms from ground-based high-contrast imaging (cite: muto12; garufi13). Based on the morphology of the spirals, they can be explained by different mechanisms. On the one hand, they can be excited by two individual planets: $0\hbox{$.\!\!^{\prime\prime}$}39$ and $0\hbox{$.\!\!^{\prime\prime}$}9$ (or $53$ au and $120$ au) (cite: muto12), or two planets at $21$ au and $23$ au (if they are inside the scattered light cavity) or at $95$ au and $162$ au (if they are exterior to) (cite: stolker16b). On the other hand, they can be driven by a single planet at $100$–$120$ au (cite: bae16; dong17). Alternatively, gravitationally unstable protoplanetary disks can also generate a pair of spirals (cite: dong15gi). What is more, spirals in protoplanetary disks can also be excited by recent stellar flybys (cite: cuello19), yet for SAO 206462 this has been ruled out using the stellar location and motion rates from *Gaia* DR3 (cite: shuai22).

While the attempts in explaining the spiral morphology in scattered light provided inconclusive results, tracking the motion of the spirals can dynamically test leading spiral formation mechanisms (cite: ren20; xie23). The motion rates of the SAO 206462 spirals were constrained using observations with a $1$-yr separation, which ruled out gravitational instability mechanism for the spirals (cite: xie21). While the motion rates helped investigate the nature of a candidate (cite: cugno24), the $1$-yr separation still resulted in two possible planetary explanations: the two spirals can be either driven by one single planet at ${\sim}90$ au, or two individual planets at ${\sim}120$ au and ${\sim}50$ au. In the former scenario, a $5$–$15M_{\rm Jup}$ planet, e.g., (cite: bae16) would be ideal for targeted high-contrast imaging using the current generation of instruments. In the latter scenario, the planets can be ${\lesssim}0.5M_{\rm Jup}$ (cite: muto12; stolker16b) which is best accessible only with next-generation instruments expected later in this decade, e.g., (cite: currie23). Here with the Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS, PI: C. Ginski; (cite: destinys1)) survey, we re-observed SAO 206462 in 2022 to establish a $7$ yr temporal separation. With the observations, we here characterize the motion of the two spirals, and guide follow-up targeted high-contrast imaging on the spiral-arm-driving planet(s).

# Observation and Data Reduction

We collected SAO 206462 observations at three epochs (i.e., in 2015, 2016, and 2022) that span $7$ yr for spiral motion analysis. All observations were carried out using the infrared dual-band imager and spectrograph (IRDIS; (cite: dohlen08)) on the SPHERE instrument (cite: beuzit19) at the Very Large Telescope (VLT). The observations were under the dual-beam polarimetric imaging (DPI; (cite: irdap2)) mode to help reveal the SAO 206262 spiral arms in polarized light. To establish the longest temporal separation of high-quality data for analysis, and reduce the possibility that wavelength-dependent imaging manifests spurious spiral motion, all the SAO 206462 observations for analysis here are in $J$-band (1.245 μm).

observations, we chose the 3 May 2015 (under ESO program 095.C-0273) and 4 May 2016 (under ESO program 097.C-0885) observations identified by (cite: xie21) to have the best image quality for spiral morphology determination and motion analysis. In the 1 h 42 m observation block in 2015, there were 50 exposures, and each exposure had 3 integrations of 32 s, totaling 4800s on-target time. In the 1 h 58 m observation block in 2016, there were 92 exposures, and each exposure had 2 integrations of 32 s, totaling 5888s of on-target time.

We observed SAO 206462 using VLT/SPHERE/IRDIS in $J$-band DPI mode under ESO program 1104.C-0415 in the DESTINYS survey ((cite: destinys1), PI: C. Ginski). The observation on UT 30 March 2022 was from UT 04:18:45 to UT 05:09:47. Among this 0 h 51 m observation block, we had 64 exposures, and each exposure had 1 integration of 32 s, totaling 2048s on-target time.

We reduced the three IRDIS DPI datasets using the `IRDAP` pipeline from Ref. (cite: irdap2) that was modified by Ref. (cite: ren23). To prepare the datasets for analysis, `IRDAP` performs alignment, bad pixel correction, and sky background subtraction. It then processes the datasets using polarimetric differential imaging (PDI). By adopting the default `IRDAP` reduction parameters, we use median-combined output $\mathcal{Q}_\phi$ images with stellar polarization removed for spiral motion analysis, see Figure [1](#fig1). These $\mathcal{Q}_\phi$ images trace the surfaces of the SAO 206462 protoplanetary disk, e.g., (cite: monnier19) for spiral morphology and motion analysis, e.g., (cite: ren20).

![](fig1.pdf)

On protoplanetary disk surfaces, the intensity of incident starlight decreases as $r^{-2}$ with $r$ being the stellocentric distance. As a result, the light scattered by dust particles in the disk – when observed by our telescope – reduces intensity accordingly. For spiral morphology and motion analysis, we rescaled the brightnesses of the $\mathcal{Q}_\phi$ images by multiplying them with a $r^2$ map – assuming a $16\hbox{$.\!\!^\circ$}7$ inclination from face-on and a $61\hbox{$.\!\!^\circ$}9$ position angle for the major axis of the disk (cite: bohn22) – to obtain the $r^2$-scaled maps (normalized at $0\hbox{$.\!\!^{\prime\prime}$}5$) in Figure [1](#fig1).

# Results and Discussion

## Results

We followed Ref. (cite: ren20) to combine the three epochs of SAO 206462 observations for spiral arm location and motion analysis. Given the low disk inclination, we assumed an infinitely thin disk for subsequent analysis in Section [3.1](#sec-result).

First, for each arm, we obtained the radial locations of the spiral peaks at different epochs, e.g., (cite: ren23v1247). We transformed the $r^2$-scaled maps in Figure [1](#fig1) to polar coordinates. For each angular location, which is defined as a clockwise separation from the major axis of the disk, we fit a normal distribution to obtain the peak and its associated error on the spiral radial profile. With a $1^\circ$ angular step, we present the peaks and their errors in Figure [2](#fig-motion).

![](fig-motion_two_axis.pdf)

Second, for the peaks, we use $p$-degree polynomials ($p\in\mathbb{N}$), $$r = \sum_{i=0}^{p} c_i \theta^i,$$ to simultaneously derive the spiral morphological parameters and its pattern motion, see Figure [2](#fig-motion). For each arm at the three epochs, we followed Ref. (cite: ren20) to fit an identical but angularly offset polynomial to obtain the best-fit in Figure [2](#fig-motion) using dummy variables; the best-fit offset will be the angular rotation among the epochs. Following Ref. (cite: ren23v1247), the polynomial fitting uncertainty will be propagated with three epochs of $0\hbox{$.\!\!^\circ$}08$ SPHERE true north pointing uncertainty in Ref. (cite: maire16) and three epochs of SPHERE astrometric uncertainty of $0\hbox{$.\!\!^\circ$}16$. The astrometric accuracy of SPHERE/IRDIS is $\sim$2 mas ($\sim$0.16 pixels; (cite: Zurlo2014)), thus translating into $0\hbox{$.\!\!^\circ$}16$ in polar coordinates.

Third, we obtained the spiral motion rates under two planet-driven scenarios in Ref. (cite: ren20), and positive rotation rates correspond to clockwise rotation here. On the one hand, we fit the two spirals independently. For S1, the best-fit motion is $-0\hbox{$.\!\!^\circ$}84\pm0\hbox{$.\!\!^\circ$}05$ yr$^{-1}$ with $\chi_{v}^{2}$ of 3.49 using a $6$-degree polynomial; for S2, it is $-0\hbox{$.\!\!^\circ$}87\pm0\hbox{$.\!\!^\circ$}05$ yr$^{-1}$ with $\chi_{v}^{2}$ of 1.83 using a $8$-degree polynomial. The spiral motions of S1 and S2 are consistent within $1\sigma$, suggesting that they are driven by a single driver. On the other hand, we fit the two spirals simultaneously, and the best-fit motion rate is $$\begin{equation}
\label{rate}
\omega = -0\hbox{$.\!\!^\circ$}85\pm0\hbox{$.\!\!^\circ$}05~{\rm yr}^{-1} 
\end{equation}$$ for two $7$-degree polynomials with $\chi_{v}^{2}$ of 2.67, see the lines in Figure [2](#fig-motion). For the motion of the two spirals, we do not further test gravitational instability (e.g., (cite: Lodato2005)) as the spiral formation mechanism, since it has been confidently ruled out with the study on $1$-yr separation for SAO 206462 (cite: xie21). Although the disk images have intensity variations possibly due to inner disk shadowing (cite: bohn22), motion measurements using different parts of the disk (i.e., S1, S2, and two arms combined) are consistent with each other, indicating the limited impact of the intensity variation in the motion measurement of SAO 206462.

## Discussion

### Implications

For the double-spiral driver in SAO 206462, its orbital period is $$\begin{equation}
    T = 424 \pm 25~{\rm yr}
\end{equation}$$ from Equation [\[rate\]](#rate) assuming a circular orbit. The corresponding stellocentric radius is $66\pm3$ au (i.e, $0\hbox{$.\!\!^{\prime\prime}$}49\pm0\hbox{$.\!\!^{\prime\prime}$}02$) for a $1.6\pm0.1M_\odot$ star, see the circular orbit in Figure [3](#fig-orbit). In comparison with direct imaging candidates, our data suggest that the *James Webb Space Telescope* (*JWST*)/NIRCam candidate in Ref. (cite: cugno24) is not driving the two spirals at ${>}5\sigma$.

The predicted driver orbit coincided with the disk gap observed in the thermal emission and a filament structure that connects two rings, see Figure [3](#fig-orbit). The orbit of the spiral driver agrees with the disk gap, which indicates the possibility of a companion driving spirals while carving a millimeter gap, similar to the case of V1247 Ori (cite: ren23v1247). The filament observed in Ref. (cite: casassus21) is located at ($\Delta$RA, $\Delta$dec) = $(-0\hbox{$.\!\!^{\prime\prime}$}276, -0\hbox{$.\!\!^{\prime\prime}$}378)$, or $0\hbox{$.\!\!^{\prime\prime}$}47$ from the star (Figure [3](#fig-orbit)). This suggests that the filament coincides with the orbit of the spiral-driving protoplanet in Figure [3](#fig-orbit) that drives the two spirals simultaneously. In combination with the orbit derived from spiral motion, the disk gap, and the dust filament, we can predict the possible location of the hidden protoplanet that creates those features.

![image](fig-orbit.pdf) ![image](fig-orbit_alma.pdf)

While this protoplanet is currently not detected, the existence of dust particles causing significant extinction in near-infrared wavelengths makes it more challenging to image this spiral-arm-driving protoplanet. To image this spiral-arm-driving companion, high spectral resolution observations using single-mode fibers (e.g., KPIC; (cite: delorme21) and HiRISE; (cite: Vigan2024)) might help confirm the existence of this protoplanet by directly probing its atmospheric compositions, e.g., (cite: delorme21). However, these observations would need high-precision locations for the protoplanet within the effective response of a single mode fiber, making it challenging to efficiently schedule the observations unless with multiple pointing attempts.

### Disk Flaring

Disk flaring will affect the deprojection of the observed disk $r^2$-scaled map and thus affect the measurements of spiral arm location and motion analysis, especially for disks with high inclinations (i.e., ${>}30^\circ$; (cite: xie23)). In Section [3.1](#sec-result), we assumed a thin disk because of the low disk inclination of SAO 206462. To examine the impact of disk flaring on motion measurement for SAO 206462, we adopted a disk model of $h=0.048\times d^{1.15}$ from Ref. (cite: Andrews2011), where $h$ represents the disk scale height and $d$ is the distance in cylindrical coordinates. Then we deprojected the disk surface map and performed the same measurements as in Section [3.1](#sec-result). If we fit the two spirals simultaneously, the best-fit motion is $-0\hbox{$.\!\!^\circ$}82\pm0\hbox{$.\!\!^\circ$}05$ yr$^{-1}$ with $\chi_{v}^{2}$ of 2.89 using a $6$-degree polynomial. If we fit the two spirals independently, the best-fit motions for S1 and S2 arms are $-0\hbox{$.\!\!^\circ$}80\pm0\hbox{$.\!\!^\circ$}05$ yr$^{-1}$ and $-0\hbox{$.\!\!^\circ$}92\pm0\hbox{$.\!\!^\circ$}05$ yr$^{-1}$ with $\chi_{v}^{2}$ of 1.89 and 3.85, respectively.

After considering the disk flaring, the spiral motions of S1 and S2 are still consistent within $1.3\sigma$. In fact, if the two spirals are independently driven by two planets, the orbits for the spiral arm motion rate would be $69\pm3$ au for S1, and $62\pm3$ au for S2. While the two planets are mathematically close to each other, they are not under low order mean motion resonance, which would make the system unstable, e.g., (cite: wang18), consistent with the single driver scenario where two spirals have the same pattern motion as in Section [3.1](#sec-result).

### Limitations

While the study using $1$-yr separation in Ref. (cite: xie21) was able to rule out the gravitational instability induced motion, the companion-driven rates still had large uncertainties, raising the question of whether the two spirals are driven by a single or two individual drivers. In fact, spiral motion studies have been assuming independent azimuthal angles in Figure [2](#fig-motion), e.g., (cite: ren20; xie21), and thus it is necessary to take into account the correlation among adjacent pixels. Before such studies are available, we can still use this short-then-long epoch approach to investigate the uncertainties in a physically motivated way.

# Conclusions

With three epochs of observations for the SAO 206462 (i.e., HD 135344 B) protoplanetary disk hosting two spiral arms in near-infrared scattered light, we have measured the $7$ yr motion of the two spirals. For a $1.6\pm0.1M_\odot$ star and assuming a circular orbit, the obtained $\omega = -0\hbox{$.\!\!^\circ$}85\pm0\hbox{$.\!\!^\circ$}05~{\rm yr}^{-1}$ rotation rate corresponds to a hidden planet at $66\pm3$ au, consistent with the disk gap in ALMA dust-continuum observations. For a star located at $135.0\pm0.4$ pc, it corresponds to an angular separation of $0\hbox{$.\!\!^{\prime\prime}$}49\pm0\hbox{$.\!\!^{\prime\prime}$}02$ from the star.

The dust filament in millimeter observations in Ref. (cite: casassus21) coincides with the orbit of the spiral-arm-driving planet, see Figure [3](#fig-orbit). If that filament is at the exact or approximate location of a forming giant protoplanet, that planet could be responsible for driving the two spiral arms and carving the disk gap in SAO 206462.

With Ref. (cite: xie23) validating the companion-disk interaction theory for an M star exciting spiral arms in the HD 100453 system, now we have two double-spiraled systems suggesting a single planetary driver for both MWC 758 from (cite: ren20) and SAO 206462 from this study. Given that spiral-arm-driving giant protoplanets have not been confirmed with direct imaging, and with the demonstrated sensitivity of *JWST* (cite: carter23), these planets are ideal targets for current space-based exoplanet imaging since they can minimize the contamination of dust signals from protoplanetary disks using multi-wavelength imaging observations.

# Acknowledgments

We thank Valentin Christiaens for discussion. Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programmes 095.C-0273, 097.C-0885, and 1104.C-0415. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01066.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). For this Special Issue “New Insights into High-Energy Astrophysics, Galaxies, and Cosmology–Celebrating the 10th Anniversary of the Re-establishment of the Department of Astronomy at Xiamen University (2012–2022)” of *Universe*, B.B.R., C.X., and C.-Y.X. are Class of 2013, 2016, and 2022 alumni from Xiamen University, respectively. We are grateful for the education, trainings, and resources received during our undergraduate studies.

-0cm

999

(ref: currie23) Currie, T.; Biller, B.; Lagrange, A.; Marois, C.; Guyon, O.; Nielsen, E.L.; Bonnefoy, M.; De Rosa, R.J. . *arXiv* **2023**, arXiv:2205.05696. <https://doi.org/10.48550/arXiv.2205.05696>.

(ref: lovis10) Lovis, C.; Fischer, D. . In *Exoplanets*; Seager, S., Ed.; University of Arizona Press: Tucson, AZ, USA, 2010; pp. 27–53.

(ref: zhu21) Zhu, W.; Dong, S. . **2021**, *59*, 291–336. <https://doi.org/10.1146/annurev-astro-112420-020055>.

(ref: keppler18) Keppler, M.; Benisty, M.; Müller, A.; Henning, T.; van Boekel, R.; Cantalloube, F.; Ginski, C.; van Holstein, R.G.; Maire, A.L.; Pohl, A.; et al. . **2018**, *617*, A44. <https://doi.org/10.1051/0004-6361/201832957>.

(ref: haffert19) Haffert, S.Y.; Bohn, A.J.; de Boer, J.; Snellen, I.A.G.; Brinchmann, J.; Girard, J.H.; Keller, C.U.; Bacon, R. . **2019**, *3*, 749–754. <https://doi.org/10.1038/s41550-019-0780-5>.

(ref: bae18) Bae, J.; Pinilla, P.; Birnstiel, T. . **2018**, *864*, L26. <https://doi.org/10.3847/2041-8213/aadd51>.

(ref: nielsen20) Nielsen, E.L.; De Rosa, R.J.; Wang, J.J.; Sahlmann, J.; Kalas, P.; Duchêne, G.; Rameau, J.; Marley, M.S.; Saumon, D.; Macintosh, B.; et al. . **2020**, *159*, 71. <https://doi.org/10.3847/1538-3881/ab5b92>.

(ref: vigan21) Vigan, A.; Fontanive, C.; Meyer, M.; Biller, B.; Bonavita, M.; Feldt, M.; Desidera, S.; Marleau, G.D.; Emsenhuber, A.; Galicher, R.; et al. . **2021**, *651*, A72. <https://doi.org/10.1051/0004-6361/202038107>.

(ref: bohn20) Bohn, A.J.; Kenworthy, M.A.; Ginski, C.; Rieder, S.; Mamajek, E.E.; Meshkat, T.; Pecaut, M.J.; Reggiani, M.; de Boer, J.; Keller, C.U.; et al. . **2020**, *898*, L16. <https://doi.org/10.3847/2041-8213/aba27e>.

(ref: franson23) Franson, K.; Bowler, B.P.; Zhou, Y.; Pearce, T.D.; Bardalez Gagliuffi, D.C.; Biddle, L.I.; Brandt, T.D.; Crepp, J.R.; Dupuy, T.J.; Faherty, J.; et al. . **2023**, *950*, L19. <https://doi.org/10.3847/2041-8213/acd6f6>.

(ref: currie23b) Currie, T.; Brandt, G.M.; Brandt, T.D.; Lacy, B.; Burrows, A.; Guyon, O.; Tamura, M.; Liu, R.Y.; Sagynbayeva, S.; Tobin, T.; et al. . **2023**, *380*, 198–203. <https://doi.org/10.1126/science.abo6192>.

(ref: matthews24) Matthews, E.C.; Carter, A.L.; Pathak, P.; Morley, C.V.; Phillips, M.W.; Krishanth, P.M.S.; Feng, F.; Bonse, M.J.; Boogaard, L.A.; Burt, J.A.; et al. . **2024**, *633*, 789. .

(ref: dong17) Dong, R.; Fung, J. **2017**, *835*, 146. <https://doi.org/10.3847/1538-4357/835/2/146>.

(ref: dong15planet) Dong, R.; Zhu, Z.; Rafikov, R.R.; Stone, J.M. . **2015**, *809*, L5. <https://doi.org/10.1088/2041-8205/809/1/L5>.

(ref: bae16) Bae, J.; Zhu, Z.; Hartmann, L. **2016**, *819*, 134. <https://doi.org/10.3847/0004-637X/819/2/134>.

(ref: teague18) Teague, R.; Bae, J.; Bergin, E.A.; Birnstiel, T.; Foreman-Mackey, D. . **2018**, *860*, L12. <https://doi.org/10.3847/2041-8213/aac6d7>.

(ref: dong18) Dong, R.; Najita, J.R.; Brittain, S. **2018**, *862*, 103. <https://doi.org/10.3847/1538-4357/aaccfc>.

(ref: xie23) Xie, C.; Ren, B.B.; Dong, R.; Choquet, É.; Vigan, A.; Gonzalez, J.F.; Wagner, K.; Fang, T.; Ubeira-Gabellini, M.G. . **2023**, *675*, L1. <https://doi.org/10.1051/0004-6361/202346305>.

(ref: ren20) Ren, B.; Dong, R.; van Holstein, R.G.; Ruffio, J.B.; Calvin, B.A.; Girard, J.H.; Benisty, M.; Boccaletti, A.; Esposito, T.M.; Choquet, É.; et al. Dynamical Evidence of a Spiral Arm-driving Planet in the MWC 758 Protoplanetary Disk. **2020**, *898*, L38. <https://doi.org/10.3847/2041-8213/aba43e>.

(ref: benisty15) Benisty, M.; Juhasz, A.; Boccaletti, A.; Avenhaus, H.; Milli, J.; Thalmann, C.; Dominik, C.; Pinilla, P.; Buenzli, E.; Pohl, A.; et al. . **2015**, *578*, L6. <https://doi.org/10.1051/0004-6361/201526011>.

(ref: wagner15) Wagner, K.; Apai, D.; Kasper, M.; Robberto, M. . **2015**, *813*, L2. <https://doi.org/10.1088/2041-8205/813/1/L2>.

(ref: shuai22) Shuai, L.; Ren, B.B.; Dong, R.; Zhou, X.; Pueyo, L.; De Rosa, R.J.; Fang, T.; Mawet, D. . **2022**, *263*, 31. <https://doi.org/10.3847/1538-4365/ac98fd>.

(ref: monnier19) Monnier, J.D.; Harries, T.J.; Bae, J.; Setterholm, B.R.; Laws, A.; Aarnio, A.; Adams, F.C.; Andrews, S.; Calvet, N.; Espaillat, C.; et al. . **2019**, *872*, 122. <https://doi.org/10.3847/1538-4357/aafe87>.

(ref: xie21) Xie, C.; Ren, B.; Dong, R.; Pueyo, L.; Ruffio, J.B.; Fang, T.; Mawet, D.; Stolker, T. . **2021**, *906*, L9. <https://doi.org/10.3847/2041-8213/abd241>.

(ref: ren23v1247) Ren, B.B.; Xie, C.; Benisty, M.; Dong, R.; Bae, J.; Stolker, T.; van Holstein, R.G.; Debes, J.H.; Garufi, A.; Ginski, C.; et al. . **2024**, *681*, L2. <https://doi.org/10.1051/0004-6361/202348114>.

(ref: safonov22) Safonov, B.S.; Strakhov, I.A.; Goliguzova, M.V.; Voziakova, O.V. . **2022**, *163*, 31. <https://doi.org/10.3847/1538-3881/ac36cb>.

(ref: wagner19) Wagner, K.; Stone, J.M.; Spalding, E.; Apai, D.; Dong, R.; Ertel, S.; Leisenring, J.; Webster, R. **2019**, *882*, 20. <https://doi.org/10.3847/1538-4357/ab32ea>.

(ref: cugno24) Cugno, G.; Leisenring, J.; Wagner, K.R.; Mullin, C.; Dong, R.; Greene, T.; Johnstone, D.; Meyer, M.R.; Wolff, S.G.; Beichman, C.; et al. . **2024**, *167*, 182. <https://doi.org/10.3847/1538-3881/ad1ffc>.

(ref: garufi18) Garufi, A.; Benisty, M.; Pinilla, P.; Tazzari, M.; Dominik, C.; Ginski, C.; Henning, T.; Kral, Q.; Langlois, M.; Ménard, F.; et al. . **2018**, *620*, A94. <https://doi.org/10.1051/0004-6361/201833872>.

(ref: GaiaDR3) Vallenari, A.; Brown, A.G.A.; Prusti, T.; de Bruijne, J.H.J.; Arenou, F.; Babusiaux, C.; Biermann, M.; Creevey, O.L.; Ducourant, C.; et al. Gaia Data Release 3. Summ. Content Surv. Prop. *Astron. Astrophys.* **2023**, *674*, A1. <https://doi.org/10.1051/0004-6361/202243940>.

(ref: grady09) Grady, C.A.; Schneider, G.; Sitko, M.L.; Williger, G.M.; Hamaguchi, K.; Brittain, S.D.; Ablordeppey, K.; Apai, D.; Beerman, L.; Carpenter, W.J.; et al. . **2009**, *699*, 1822–1842. .

(ref: muto12) Muto, T.; Grady, C.A.; Hashimoto, J.; Fukagawa, M.; Hornbeck, J.B.; Sitko, M.; Russell, R.; Werren, C.; Curé, M.; Currie, T.; et al. . **2012**, *748*, L22. <https://doi.org/10.1088/2041-8205/748/2/L22>.

(ref: garufi13) Garufi, A.; Quanz, S.P.; Avenhaus, H.; Buenzli, E.; Dominik, C.; Meru, F.; Meyer, M.R.; Pinilla, P.; Schmid, H.M.; Wolf, S. . **2013**, *560*, A105. <https://doi.org/10.1051/0004-6361/201322429>.

(ref: stolker16b) Stolker, T.; Dominik, C.; Avenhaus, H.; Min, M.; de Boer, J.; Ginski, C.; Schmid, H.M.; Juhasz, A.; Bazzon, A.; Waters, L.B.F.M.; et al. . **2016**, *595*, A113. <https://doi.org/10.1051/0004-6361/201528039>.

(ref: dong15gi) Dong, R.; Hall, C.; Rice, K.; Chiang, E. . **2015**, *812*, L32. <https://doi.org/10.1088/2041-8205/812/2/L32>.

(ref: cuello19) Cuello, N.; Dipierro, G.; Mentiplay, D.; Price, D.J.; Pinte, C.; Cuadra, J.; Laibe, G.; Ménard, F.; Poblete, P.P.; Montesinos, M. . **2019**, *483*, 4114–4139. <https://doi.org/10.1093/mnras/sty3325>.

(ref: destinys1) Ginski, C.; Ménard, F.; Rab, C.; Mamajek, E.E.; van Holstein, R.G.; Benisty, M.; Manara, C.F.; Asensio Torres, R.; Bohn, A.; Birnstiel, T.; et al. . **2020**, *642*, A119. <https://doi.org/10.1051/0004-6361/202038383>.

(ref: dohlen08) Dohlen, K.; Langlois, M.; Saisse, M.; Hill, L.; Origne, A.; Jacquet, M.; Fabron, C.; Blanc, J.C.; Llored, M.; Carle, M.; et al. . In *Proceedings Volume 7014, Ground-based and Airborne Instrumentation for Astronomy II*; McLean, I.S., Casali, M.M., Eds.; Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series; SPIE: Bellingham, WA, USA, 2008; Volume 7014, p. 70143L. .

(ref: beuzit19) Beuzit, J.L.; Vigan, A.; Mouillet, D.; Dohlen, K.; Gratton, R.; Boccaletti, A.; Sauvage, J.F.; Schmid, H.M.; Langlois, M.; Petit, C.; et al. . **2019**, *631*, A155. <https://doi.org/10.1051/0004-6361/201935251>.

(ref: irdap2) van Holstein, R.G.; Girard, J.H.; de Boer, J.; Snik, F.; Milli, J.; Stam, D.M.; Ginski, C.; Mouillet, D.; Wahhaj, Z.; Schmid, H.M.; et al. . **2020**, *633*, A64. <https://doi.org/10.1051/0004-6361/201834996>.

(ref: stolker17) Stolker, T.; Sitko, M.; Lazareff, B.; Benisty, M.; Dominik, C.; Waters, R.; Min, M.; Perez, S.; Milli, J.; Garufi, A.; et al. . **2017**, *849*, 143.<https://doi.org/10.3847/1538-4357/aa886a>.

(ref: ren23) Ren, B.B.; Benisty, M.; Ginski, C.; Tazaki, R.; Wallack, N.L.; Milli, J.; Garufi, A.; Bae, J.; Facchini, S.; Ménard, F.; et al. . **2023**, *680*, A114. <https://doi.org/10.1051/0004-6361/202347353>.

(ref: bohn22) Bohn, A.J.; Benisty, M.; Perraut, K.; van der Marel, N.; Wölfer, L.; van Dishoeck, E.F.; Facchini, S.; Manara, C.F.; Teague, R.; Francis, L.; et al. . **2022**, *658*, A183. <https://doi.org/10.1051/0004-6361/202142070>.

(ref: maire16) Maire, A.L.; Langlois, M.; Dohlen, K.; Lagrange, A.M.; Gratton, R.; Chauvin, G.; Desidera, S.; Girard, J.H.; Milli, J.; Vigan, A.; et al. . In *Proceedings Volume 9908, Ground-Based and Airborne Instrumentation for Astronomy VI*; Evans, C.J., Simard, L., Takami, H., Eds.; Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series; SPIE: Bellingham, WA, USA, 2016; Volume 9908, p. 990834. <https://doi.org/10.1117/12.2233013>.

(ref: Zurlo2014) Zurlo, A.; Vigan, A.; Mesa, D.; Gratton, R.; Moutou, C.; Langlois, M.; Claudi, R.U.; Pueyo, L.; Boccaletti, A.; Baruffolo, A.; et al. . **2014**, *572*, A85. <https://doi.org/10.1051/0004-6361/201424204>.

(ref: Lodato2005) Lodato, G.; Rice, W.K.M. . **2005**, *358*, 1489–1500. <https://doi.org/10.1111/j.1365-2966.2005.08875.x>.

(ref: casassus21) Casassus, S.; Christiaens, V.; Cárcamo, M.; Pérez, S.; Weber, P.; Ercolano, B.; van der Marel, N.; Pinte, C.; Dong, R.; Baruteau, C.; et al. . **2021**, *507*, 3789–3809. <https://doi.org/10.1093/mnras/stab2359>.

(ref: delorme21) Delorme, J.R.; Jovanovic, N.; Echeverri, D.; Mawet, D.; Kent Wallace, J.; Bartos, R.D.; Cetre, S.; Wizinowich, P.; Ragland, S.; Lilley, S.; et al. . **2021**, *7*, 035006. <https://doi.org/10.1117/1.JATIS.7.3.035006>.

(ref: Vigan2024) Vigan, A.; El Morsy, M.; Lopez, M.; Otten, G.P.P.L.; Garcia, J.; Costes, J.; Muslimov, E.; Viret, A.; Charles, Y.; Zins, G.; et al. . **2024**, *682*, A16. <https://doi.org/10.1051/0004-6361/202348019>.

(ref: Andrews2011) Andrews, S.M.; Wilner, D.J.; Espaillat, C.; Hughes, A.M.; Dullemond, C.P.; McClure, M.K.; Qi, C.; Brown, J.M. . **2011**, *732*, 42. <https://doi.org/10.1088/0004-637X/732/1/42>.

(ref: wang18) Wang, J.J.; Graham, J.R.; Dawson, R.; Fabrycky, D.; De Rosa, R.J.; Pueyo, L.; Konopacky, Q.; Macintosh, B.; Marois, C.; Chiang, E.; et al. . **2018**, *156*, 192. <https://doi.org/10.3847/1538-3881/aae150>.

(ref: carter23) Carter, A.L.; Hinkley, S.; Kammerer, J.; Skemer, A.; Biller, B.A.; Leisenring, J.M.; Millar-Blanchaer, M.A.; Petrus, S.; Stone, J.M.; Ward-Duong, K.; et al. . **2023**, *951*, L20. <https://doi.org/10.3847/2041-8213/acd93e>.

</paper>

## Items to check

```json
[
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The predicted driver orbit coincides with the ALMA-observed disk gap and with the dust filament",
  "failed_quote": "This suggests that the filament coincides with the orbit of the spiral-arm-driving protoplanet"
 }
]
```
