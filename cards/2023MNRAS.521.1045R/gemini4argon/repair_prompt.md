# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.521.1045R\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Regular rotation and low turbulence in a diverse sample of *z* $\sim$ 4.5 galaxies observed with ALMA

[^1]: E-mail: romanoliveira@astro.rug.nl

# Abstract

The discovery of galaxies with regularly rotating discs at redshifts $\geq$ 4 has been a puzzling challenge to galaxy formation models that tend to predict chaotic gas kinematics in the early Universe as a consequence of gas accretion, mergers and efficient feedback. In this work, we investigated the kinematics of five highly resolved galaxies at *z* $\sim$ 4.5 observed with ALMA in the \[CII\] 158 $\mu$m emission line. The sample is diverse: AzTEC1 (starburst galaxy), BRI1335-0417 (starburst and quasar host galaxy), J081740 (normal star-forming galaxy) and SGP38326 (two starburst galaxies in a group). The five galaxies show velocity gradients, but four were found to be rotating discs while the remaining, AzTEC1, is likely a merger. We studied the gas kinematics of the discs using $^{\text{3D}}$`BAROLO` and found that they rotate with maximum rotation velocities between 198 and 562 km s$^{-1}$ while the gas velocity dispersions, averaged across the discs, are between 49 and 75 km s$^{-1}$. The rotation curves are generally flat and the galaxies have ratios of ordered-to-random motion ($V/\sigma$) between 2.7 and 9.8. We present `CANNUBI`, an algorithm for fitting the disc geometry of rotating discs in 3D emission-line observations prior to modelling the kinematics, with which we find indications that these discs may have thicknesses of the order of 1 kpc. This study shows that early disc formation with a clear dominance of rotation with respect to turbulent motions is present across a variety of galaxy types.

galaxies: evolution – galaxies: high-redshift – galaxies: kinematics and dynamics – submillimetre: galaxies

# Introduction

The Atacama Large Millimiter/submillimetre Array (ALMA) has been fundamental for the exploration of the high-*z* Universe in the past decade (cite: hodge20). Through the observation of \[CII\] 158 $\mu$m emission at *z* $> 4$, the study of cold gas kinematics has opened a new window in our understanding of galaxy formation in the early Universe (cite: carilli&walter13). Recent observations show numerous kinematically-cold disc galaxies with ratios of rotation-to-random motion ($V/\sigma$) as high as 10, some of them with bulges or spiral arms when the Universe was no older than 1.5 billion years (cite: hodge12; sharda19; neeleman20; rizzo20; lelli21; fraternali21; rizzo21; tsukui21).

Meanwhile, state-of-the-art cosmological simulations struggle to reproduce these observations, as gas discs with $V/\sigma \geq 3$ usually form at *z* $\leq$ 2 (cite: simons17; pillepich19). The current theoretical framework of galaxy evolution predicts that the early stages of galaxy formation are chaotic and dominated by violent gas accretion and frequent mergers (cite: dekel09; somerville15). Furthermore, the interstellar medium (ISM) of galaxies is also expected to be significantly affected by feedback processes from either supernovae or an active galactic nucleus (AGN) which heat and eject the gas from the galaxy, therefore increasing the turbulent motions (cite: biernacki18; nelson19; hayward17). The effects of stellar feedback on the ISM should become especially important for high-*z* starburst galaxies, that can reach star formation rates (SFR) of the order of a thousand solar masses per year, posing difficulties in maintaining stable gas discs over large periods of time (cite: nelson19).

Recent efforts to bridge the tension between observations and theory have been carried out. (cite: kretschmer22) found an example of a simulated cold gas disc at *z* $\sim$ 3.5 with V/$\sigma$ similar to the observed values. However, such a disc lasts for only 5 orbital periods and returns to a highly disturbed state after only 400 Myr. In contrast, (cite: tamfal22) showed with a cosmological, N-body hydrodynamical simulation that a present-day Milky Way-type galaxy can form a thin stellar disc as early as *z* $=8$ that remains kinematically cold. Similarly, (cite: kohandel20) presented simulated galaxies at *z* = 6 $-$ 8 with V/$\sigma \sim 7$ and velocity dispersions in the range of 23 $-$ 38 km s$^{-1}$. Finally, some studies suggested that the formation and survival of a disc may depend on the mass of the dark matter hosting the galaxy with a threshold of $2\times10^{11}$ M$_{\odot}$, however, there is a lack of observations of low mass galaxies at high-*z* to validate this hypothesis (cite: dekel20; gurvich22).

Furthermore, the cosmic evolution of gas velocity dispersion in galaxies is still largely unconstrained. Determining the velocity dispersion of discs across cosmic time and the presence of regular rotation is essential to link early discs with their evolved counterparts in the Local Universe. The general expectation from cosmological simulations and *z* $\gtrsim 3$ observations is that velocity dispersions increase up to $\sim$ 100 km s$^{-1}$ at *z* $> 4$ (cite: uebler19; pillepich19), considerably larger than current observations indicate (cite: sharda19; neeleman20; rizzo20; lelli21; fraternali21; rizzo21; tsukui21). A precise quantification of such dispersions is essential to identify the mechanisms that drive gas turbulence in different stages of galaxy evolution. While some studies find that gravitational instabilities are necessary (cite: krumholz18; uebler19), some other studies find that the relatively low turbulence found in high-*z* galaxies can be driven by stellar feedback with no need of additional sources (cite: rizzo21; fraternali21). Although, given that most of the highly-resolved dynamically cold disc galaxies observed at *z* $>4$ are massive dusty star-forming galaxies, the broad picture of how the disc turbulence is regulated in typical main-sequence and/or low-mass galaxies remains uncertain.

The main challenges of analysing the kinematics of galaxies at *z* $\geq 4$ are the relatively low angular resolution obtained in observations compared to the small angular size of the galaxies and the low signal-to-noise ratio (SNR) due to cosmological dimming. A powerful way of circumventing these problems is to observe high-*z* galaxies in the \[CII\] fine-structure transition at 158 $\mu$m, which is a major gas coolant that traces multiple phases of the ISM due to its low ionisation potential (cite: gullberg15; tarantino21; ramospadilla21). \[CII\] is the brightest fine-structure line in star-forming galaxies and it is practically unaffected by the cosmic microwave background attenuation (cite: lagache18). Since (cite: capak15) showed that \[CII\] is abundant in early galaxies and more extended than the dust and CO emission (cite: gullberg18; tadaki19), \[CII\] has been fundamental to study the ISM and dynamics of high-*z* galaxies. In galaxies at *z* = $4 - 5$, the effective radii of the \[CII\] distributions typically vary in the range 0.3" to 1.1", which translates to about $2 - 7$ kpc (cite: gullberg18; fujimoto20; lefevre20).

To be able to measure the shape of a rotation curve and a reliable value of the gas velocity dispersion, it is imperative to have at least a few independent resolution elements across the major axis of the disc. Thus, even for the most extended galaxies an angular resolution of at least 0.3" is necessary.

To elucidate some of the above questions, we have obtained accurate \[CII\] kinematic measurements of a sample of *z* $\sim$ 4.5 galaxies with the 3D tilted-ring kinematic modelling tool $^{\text{3D}}$`BAROLO` (cite: diteodoro15).

We used publicly available high-resolution \[CII\] data, some of which have been presented before, but, together they have not been systematically studied with a methodology that is non-parametric, corrected for beam smearing and in 3D. This paper focuses on the presentation of the data and the kinematic modelling.

A following paper will undertake the dynamical modelling analysis, the local disc stability (cite: toomre64) and a study on the origin of the gas turbulence. This paper is structured as follows: in Section [2](#sec:data), we present the sample selection and data reduction. In Section [3](#sec:methods), we present the methodology for the 3D kinematic modelling and the disc geometry modelling. In Section [4](#sec:results), we show our main results: the geometry of the galaxies and the kinematic properties derived. In Section [\[sec:discussion\]](#sec:discussion) we interpret our findings within the context of previous works. In Section [\[sec:conclusions\]](#sec:conclusions) we summarise our main findings and implications. Throughout the paper, we adopt a $\Lambda$CDM cosmology with Hubble constant $H_0$ = 67.7 km/s/Mpc, matter density $\Omega_{\text{m}}$ = 0.31 and vacuum energy $\Omega_{\lambda}$ = 0.69, from the 2018 Planck results (cite: planck20).

# Data

To compile our sample of highly spatially resolved galaxies, we searched the ALMA archive for public datasets with \[CII\] 158 $\mu$m line emission. Our selection criteria were the following: observations with angular resolution $<0.3$"; spectral resolution $<30$ km s$^{-1}$; redshift of the galaxy in the range of *z* $= 4-5$. This is a particularly interesting redshift range as it lies in between the Epoch of Reionisation and cosmic noon, two pivotal points in galaxy evolution. Furthermore, this redshift range has the benefits of: having the redshifted \[CII\] 158 $\mu$m emission-line conveniently placed at an atmospheric window covered by ALMA; being beyond the cosmic peak of angular diameter distance, which allows for better spatial resolution than objects at cosmic noon; and having lower cosmological dimming than at higher *z* (cite: carilli&walter13). We avoided selecting galaxies in massive proto-clusters as they may have a more evolved dynamics than typical *z* $\sim 4.5$ galaxies and we avoided lensed sources as they require a different analysis as the one in (cite: rizzo18; rizzo20; rizzo21). To perform this search we used the tool `astroquery` (cite: ginsburg19) and cross-referenced it with the NED database to obtain an estimate of the redshift. The above criteria resulted in four publicly available datasets.

+:-----------------------------+:-----------:+:------------:+:------:+:--------------:+:-------------:+:--------------------:+:-----------:+:---------------------:+:--------:+:-:+:-:+
| ID                           | RA          | DEC          | *z*    | Physical Scale | Channel width | \[CII\] Beam         | \[CII\] RMS | I$_{\textrm{[CII]}}$  | int time |   |   |
|                              |             |              |        +----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
|                              |             |              |        | (kpc/")        | (km s$^{-1}$) | (")                  | (mJy/beam)  | (Jy km s$^{-1}$)      | \(s\)    |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
| AzTEC 1 $^{\mathrm{a}}$      | 09:59:42.86 | +02:29:38.18 | 4.3419 | 6.86           | 30            | 0.15 $\times$ 0.13   | 0.41        | 25.5 $^{+1.0}_{-1.2}$ | 1935     |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
| BRI1335-0417 $^{\mathrm{b}}$ | 13:38:03.42 | -04:32:34.98 | 4.4071 | 6.82           | 15            | 0.20 $\times$ 0.17   | 0.43        | 38.8 $^{+1.2}_{-0.9}$ | 3629     |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
| J081740 $^{\mathrm{c}}$      | 08:17:40.87 | +13:51:38.23 | 4.2603 | 6.92           | 26            | 0.24 $\times$ 0.16   | 0.35        | 6.5 $^{+0.4}_{-0.6}$  | 5988     |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
| SGP38326-1 $^{\mathrm{d}}$   | 00:03:07.23 | -33:02:50.61 | 4.4238 | 6.80           | 26            | 0.18 $\times$ 0.16\* | 0.19        | 7.9 $^{+0.4}_{-0.5}$  | 16844    |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+
| SGP38326-2 $^{\mathrm{d}}$   | 00:03:07.12 | -33:02:51.15 | 4.4274 | 6.80           | 26            | 0.18 $\times$ 0.16\* | 0.19        | 1.9 $^{+0.1}_{-0.1}$  | 16844    |   |   |
+------------------------------+-------------+--------------+--------+----------------+---------------+----------------------+-------------+-----------------------+----------+---+---+

Angular resolution achieved with `tclean`/`uvtaper` set to 0.1".

ALMA project number: $^{\mathrm{a}}$ 2017.1.00127.S (PI: Iono); $^{\mathrm{b}}$ 2017.1.00394.S (PI: González López); $^{\mathrm{c}}$ 2017.1.01052.S (PI: Neeleman); $^{\mathrm{d}}$ 2015.1.00330.S (PI: Riechers), 2018.1.00001.S (PI: Oteo).

In Table [\[tab:data\]](#tab:data), we present the properties of the \[CII\] line emission and datasets of our galaxy sample. In Table [1](#tab:masses), we present the SFRs and molecular gas masses as previously reported in the literature for these objects.

We estimate the gas masses based on high transition CO luminosities reported in the literature as referenced in Table [1](#tab:masses). For AzTEC 1, BRI1335-0417, SGP38326 (both galaxies), we use the J $= 4-3$, $2-1$ and $5-4$ transitions from (cite: yun15; jones16; oteo16), respectively. We estimate the the L’$_{\textrm{CO(J=1-0)}}$ using the line ratios from (cite: carilli&walter13) and we assume an $\alpha_{\textrm{CO}}$ of 0.8 M$_{\odot} (\textrm{K km s}^{-1} \textrm{pc}^2)^{-1}$ to estimate the molecular gas masses. For J081740, a normal star-forming galaxy, we follow the assumptions from (cite: neeleman20) and report the gas mass obtained with a line ratio of 0.81 (between J $=2-1$ and J $=1-0$) and an $\alpha_{\textrm{CO}}$ of 3 M$_{\odot} (\textrm{K km s}^{-1} \textrm{pc}^2)^{-1}$, appropriate for a normal (non-starburst) high-*z* star-forming galaxy.

As for the SFRs, we normalise them all to the initial mass function (IMF) of (cite: chabrier03) according to (cite: madau&dickinson14).

| ID | SFR (M$_{\odot}$ yr$^{-1}$) | M$_{\mathrm{H_2}}$ (M$_\odot$) | References |
|:---|:--:|:--:|:--:|
| AzTEC 1 | $1240 \pm 230$ | $1.4 \pm 0.2 \times 10^{11}$ | 1 |
| BRI1335-0417 | $5100 \pm 1500$ | $1.0 \pm 0.1 \times 10^{11}$ | 2, 3 |
| J081740 | $166 \hspace{1mm} ^{+344}_{-103}$ | $8.8 \pm 2.6 \times 10^{10}$ | 4 |
| SGP38326-1 | $\sim1830$ | $\sim1.9 \times 10^{11}$ | 5 |
| SGP38326-2 | $\sim882$ | $\sim7.6 \times 10^{10}$ | 5 |

: Star formation rates and gas masses of the sample as previously reported in the literature. The SFR are normalised to a Chabrier IMF (cite: chabrier03). In the case of BRI1335-0417 the references 2 and 3 are for the SFR and gas mass, respectively.

1\. (cite: yun15); 2. (cite: lu18); 3. (cite: jones16);\
4. (cite: neeleman20); 5. (cite: oteo16).

Here we summarise the main properties of each galaxy:

- AzTEC 1\
  A sub-millimetre galaxy characterised by a clumpy dust continuum (cite: iono16). It has a SFR of $\sim$1300 M$_{\odot}$ yr$^{-1}$ and an estimated stellar mass of $\sim10^{11}$M$_{\odot}$, derived from fitting the spectral energy distribution (SED) over the range of rest-frame UV to radio wavelengths (cite: yun15). It was observed in multiple tracers with ALMA, such as CO(J=4-3), \[NII\] 205 $\mu$m and \[OIII\] 88 $\mu$m in addition to the \[CII\] 158 $\mu$m, analysed in this paper. The L$_{\text{[OIII]}}$/L$_{\text{[NII]}}$ suggests a chemically evolved system with a gas metallicity of 0.7-1.0 Z$_{\odot}$ (cite: tadaki19). The high-resolution \[CII\] dataset of AzTEC1, used in this paper, was previously analysed by (cite: tadaki20) with GalPaK$^{\mathrm{3D}}$, a parametric kinematic modelling tool for 3D data (cite: bouche15). They found a rotating disc with velocity dispersion of $\sim$ 70 km s$^{-1}$ and reported the presence of non-corotating gas components which they interpreted as an infall that is taking place perpendicularly to the disc.

- BRI1335-0417\
  An infrared hyperluminous quasar host galaxy selected by the Automated Plate Measuring (APM) optical survey for high-*z* quasars (cite: irwin91). It was one of the first CO detections at *z* $>$ 4, observed in the CO(J=5-4) line with IRAM (cite: guilloteau97), later also observed in \[CII\] with the APEX telescope (cite: wagg10) and with ALMA at high-resolution. Recently, using the \[CII\] emission, (cite: tsukui21) found a structure suggestive of the presence of spiral arms together with the dynamical evidence of a massive bulge in the centre. CO(J=7-6) and \[NII\] observations showed the existence of a possible outflow (cite: lu18). BRI1335-0417 is an extreme starburst with a SFR estimated to be around 5000 M$_{\odot}$ yr$^{-1}$. (cite: wagg14) found this estimate via SED fitting, which may, however, be biased by the presence of an AGN. Later, (cite: lu18) found a similar estimate with a method based on the luminosity of the CO(J=7-6) emission that is supposed to be independent of the presence of an AGN because it is insensitive to AGN heating (cite: lu17). The high-resolution \[CII\] dataset of BRI1335-0417, used in this paper, was previously analysed by (cite: tsukui21) with the KinMS package, a parametric kinematic modelling tool for 3D data (cite: davis20; davis13). They reported a velocity dispersion of $\sim$ 70 km s$^{-1}$ in the outer parts of the galaxy.

- J081740\
  A galaxy first identified as a damped Lyman alpha system in the spectrum of a background quasar (cite: neeleman17). Because this selection method is not biased towards objects brighter in the submillimetre, it is the only non-starburst galaxy in this sample. With a SFR of only 177 M$_{\odot}$ yr$^{-1}$, which is likely representative of more typical star-forming galaxies at *z* $\sim$ 4. The high-resolution \[CII\] dataset of J081740, used here, was previously analysed by (cite: neeleman20) with QubeFit, a parametric kinematic modelling tool for 3D data (cite: neeleman20qubefit). They showed the presence of a rotating disc with a velocity dispersion of $\sim$ 80 km s$^{-1}$.

- SGP38326\
  A pair of starbursts with a combined SFR of around 4500 M$_{\odot}$ yr$^{-1}$, here we refer to the more massive galaxy as SGP38326-1 and the companion as SGP38326-2. Detection in $^{12}$CO(J=5-4) showed an elongated emission connecting the two galaxies which could be interpreted as a molecular gas bridge among them suggesting an ongoing interaction (cite: oteo16). However, dust was not detected along this region and there appear to be no signs of stripped material in the \[CII\] emission (cite: oteo16). This system is considered one of the best examples of high-redshift starburst galaxies that can be the progenitor of massive elliptical galaxies at lower redshifts (cite: valentino20; toft14). A lower-resolution \[CII\] observation was analysed by (cite: oteo16), where they fit the observed velocity field with a simple dynamical model.

Since we selected galaxies based solely on the high quality of the data available we are analysing the kinematic properties of a diverse set of systems: starburst galaxies isolated and in a group, a quasar host galaxy and a normal star-forming galaxy.

## Data Reduction and Imaging

After retrieving the raw data from the ALMA archive, we carried out the data reduction using the Common Astronomy Software Applications (CASA) (cite: mcmullin07). This was done in two steps: 1) calibration of the visibilities and 2) imaging of the line emission datacubes and dust continuum maps.

In the first step, we calibrated the visibility data to obtain measurement sets in which we could begin the imaging procedure. For that, we used the original calibration scripts with the same CASA version in which the data had been taken. This process was straightforward for the sources AzTEC1, BRI1335-0417 and J081740. However, for SGP38326 we combined two separate high-resolution observations to achieve a higher SNR (Project IDs: 2018.1.00001.S and 2015.1.00330.S). We used the task `split` to average both datasets to a similar channel width and, subsequently, we used the task `concat` to concatenate the datasets to a unique measurement set used for the imaging. We only used the frequency range common to both datasets.

In the second step, the imaging procedure was done using the CASA version 5.6.1-8 and we started by first producing a dirty cube in which we identified the velocity channels containing line emission. To obtain a continuum map, we first produced a dirty continuum image of the line-free channels using the task `tclean` in the Multi Frequency Synthesis (MFS) mode to estimate the root mean square (RMS) of the noise in the continuum map. Subsequently, we produced the final clean continuum map using `tclean` in MFS mode and cleaning down to 3 times the RMS noise of the dirty image for the sources AzTEC1, BRI1335-0417 and J081740. In the case of SGP38326 group, we chose to clean it further towards 1.5 times the RMS noise of the dirty image so we could probe fainter substructures that may be present in the data.

To obtain a line-emission datacube, we first created a continuum-free measurement set using the task `uvcontsub` with a linear fit for the sources AzTEC1, BRI1335-0417 and J081740. Similarly to the continuum map, we first created a dirty line-emission cube using `tclean` in the ’cube’ mode to find the RMS noise level per velocity channel and then produced a final line-emission cube cleaned down to 3 times the RMS noise.

For SGP38326, we followed a slightly different procedure: since it is a complex system with many continuum sources, we avoided using `uvcontsub` to subtract the continuum. We created a dirty cube of the continuum and line emission of the system with `tclean` to estimate the RMS noise per velocity channel, we then created a clean cube of the continuum and line emission cleaning it down to 1.5 times the RMS noise of the dirty cube. To extract the final line-emission cube and continuum map we used the task `imcontsub` that removes the continuum from the cube in the image space rather than in the uv space. For this specific dataset, we also used `uvtapering` in `tclean` to taper the spatial resolution to 0.1" to maintain a suitable SNR while slightly compromising the maximum possible angular resolution of the dataset.

During the imaging process, we produced emission-line cubes with Briggs weighting (cite: briggs95) with a robust parameter of 2 for the sources AzTEC1, J081740 and SGP38326 which is equivalent to a natural weighting. For BRI1335-0417, since the SNR is high enough, we chose a robust parameter of 0.5 to achieve a slightly better spatial resolution. As for the dust continuum maps, we also used a robust parameter of 2 for the sources J081740 and SGP383260, although, AzTEC1 and BRI1335-0417 are bright enough sources that we could use a robust parameter of 0.5 to achieve a better spatial resolution. Finally, we chose cell sizes that are within 5 to 8 times smaller than the beam size: 0.02"/px for AzTEC1 and SGP38326; and 0.03"/px for BRI1335-0417 and J081740.

Our choices for the weighting schemes and channel widths were motivated to obtain an average SNR of at least 4 per velocity channel in at least 10 channels of the data cubes. We define the SNR of the line emission as the ratio between the average of the masked \[CII\] line intensity per pixel in each velocity channel and the RMS noise. This is the masking used in the kinematic modelling that we describe in more detail in Sections [3.1](#sec:barolo) and  [4.1](#sec:presentation).

# Methodology

## Modelling the disc kinematics with $^{\text{3D}}$`BAROLO`

$^{\text{3D}}$`BAROLO` is an algorithm that estimates the best-fit parameters of a rotating disc that reproduce the emission in the observed emission-line datacubes (cite: diteodoro15). $^{\text{3D}}$`BAROLO` minimises the residuals between the observations and the mock datacubes produced with 3D tilted-ring models and convolved to the same resolution of the observations. Therefore, it accounts for the effect of beam smearing (cite: bosma78; begeman87), which is very important for retrieving robust measurements of velocity dispersions and rotation velocities at the relatively low angular resolution of the present data.

For the fits, we assume that the emission is tracing circular motions and that there are no large-scale radial or vertical motions, e.g. inflows/outflows, although we discuss this further in Section [4.3](#sec:kin) where we also note that some galaxies present some distortions that could be interpreted as non-circular motions.

Before performing the 3D modelling, we mask the data by performing a source detection in 3D. This masking procedure is handled in $^{\text{3D}}$`BAROLO` by the task `SEARCH` with two parameters: `SNRCUT` a primary cut the emission at a chosen SNR level; and `GROWTHCUT` a secondary SNR boundary that limits the growth of the mask. The input disc geometry parameters are explained in the Section [3.2](#subsec:CANNUBI).

Moreover, we strive to not oversample the rotation curves thus we keep the number of modelled tilted rings as close as possible to the real number of resolution elements in the data with a separation close to the angular resolution. As a consequence all our measured rotation velocities and velocity dispersions in a galaxy can be considered independent. The $^{\text{3D}}$`BAROLO` parameters used for the kinematic fits are given in Table [\[tab:BBpar\]](#tab:BBpar), Appendix [\[app:kinpar\]](#app:kinpar). In Section [4](#sec:results), we present the best-fit kinematic models for the sample.

## Estimating the disc geometry

Modelling the kinematics of a rotating disc with $^{\text{3D}}$`BAROLO` requires a set of geometric parameters for input. To reduce the number of free parameters in the kinematic fitting we derive the geometric parameters beforehand using `CANNUBI`[^2], a Markov Chain Monte Carlo (MCMC) python routine for estimating the disc geometry of galaxies.

`CANNUBI` uses `emcee` (cite: mackey13) to minimise the data against resolution-matched 3D tilted-ring models of rotating discs generated with $^{\text{3D}}$`BAROLO`. `CANNUBI` estimates the coordinates of the centre of the disc, its radial extent, its disc thickness (Z0) and the position angle (PA) and inclination angle. The minimisation is done on the total flux map of the galaxy or in 3D using the full data cube. The latter can be useful to overcome the degeneracy between inclination and thickness as the data cube holds more information on the geometry, however, it is much more computationally demanding as the code has to perform a full kinematic fit at every iteration. In this work we present tests done on the total flux map of mock galaxies. For more information on `CANNUBI` we refer the reader to the description linked in the Data Availability section.

Of all the geometric parameters measured with `CANNUBI`, the accurate determination of the disc inclination is key to a successful kinematic model, since it affects the correction from line-of-sight to rotation velocities. Inclinations of gaseous galaxy discs are often derived assuming a razor-thin disc and therefore that the shape of the emission on the sky is fully due to the orientation of an intrinsically round disc. In this case, the axis ratio is a direct measurement of the cosine of the inclination angle.

Another common assumption of disc thickness is to consider an inclination angle of $\cos^2 i = ((b/a)^2-q_0^2)/(1-q_0^2)$, where *a* and *b* are the semi-major and semi-minor axes, respectively. The disc thickness is taken into account in the parameter $q_0$ with a typical assumed value of $q_0 = 0.2$ for *z* $\approx 2$ galaxies (cite: forster18; swinbank17; weijmans14).

To obtain the fiducial kinematic models we discuss in Section [4](#sec:results), we used `CANNUBI` to estimate the disc inclination of the galaxies by assuming razor-thin discs.

However, due to high velocity dispersions, it is reasonable to expect that high-*z* galaxies have non-negligible thickness, which can lead us to underestimate the disc inclinations (cite: iorio17). `CANNUBI` can potentially be used for measuring the thickness as shown by our tests on mock galaxies in Section [3.2.2](#sec:CANNUBI). However, mock galaxies have idealised rotating discs that behave much more predictably than real galaxies. Given the quality of the present data we are not fully confident that we can determine the disc thickness in our galaxies reliably. Thus, we prefer to discuss our estimates in terms of uncertainty in our kinematic models in Section [\[sec:discthick\]](#sec:discthick). It is important to note that if the thickness of the discs is smaller than the resolution of the data ($\sim$ 1 kpc), assuming zero thickness or a few hundred parsec would make no significant difference in our final geometrical and kinematic parameters.

### Creating a sample of mock galaxies

To verify that `CANNUBI` can return reliable estimations of the inclinations and, to some extent, also the disc thickness, we performed a test run with mock data. We use a sample of 48 mock galaxies produced with the task `GALMOD` within $^{\text{3D}}$`BAROLO` that were created with a combination of several properties in the range of our real data.`GALMOD` creates mock models by populating a 3D space with gas clouds assuming circular orbits within a tilted ring model. We use a radial exponential surface density profile for the emitting gas and a Gaussian vertical density profile. We assume an empirical function for the rotation curve that is described by the following expression:

$$\begin{equation}
    V_{\mathrm{rot}}(R) = V_{\mathrm{t}} \hspace{2mm} \dfrac{\left(1 + \dfrac{R_{\mathrm{t}}}{R}\right)^{\beta}}{\left[1 + \left(\dfrac{R_{\mathrm{t}}}{R}\right)^{\xi}\right]^{\frac{1}{\xi}}}.
\end{equation}$$

This function is described in (cite: rizzo18) and in (cite: courteau97). We chose the following numerical values for the parameters: $V_t=250$ km s$^{-1}$ for the velocity scale; $R_t=1$ kpc for the turnover radius between the central rising part and the outer part of the rotation curve; $\beta=0.4$ that is related to the behaviour at large radii and $\xi=2.5$ that specifies the sharpness of the turnover at small radii. These return a rising rotation curve in the centre and an external rotation curve that flattens with rotation velocity of 250 km s$^{-1}$. We assume a constant velocity dispersion of 50 km s$^{-1}$. We convolved the mock data with a synthetic beam to achieve 3 and 5 resolution elements per galaxy side with a galaxy radius of 3 kpc.

Moreover, we added random noise, convolved to the same resolution as the model, to achieve an average SNR per velocity channel of 3 and 5. The definition we use for SNR can be found in Section [2.1](#sec:datared).

We choose all these values to obtain mocks similar to the ALMA data we are analysing, i.e. with SNR between 4 and 5.5 and 3 to 5 independent resolution elements. To make sure that we can properly estimate the inclination of the data we use a large range of inclinations: from 30 to 70 degrees. For the disc thickness we also probe a large range of possible values with a conservative choice for the largest possible thickness: from 0 to 1.6 kpc (constant with radius), in which the latter value would mean a disc as thick as half of its radial extent. A summary of the properties used to create the sample of mock galaxies with a combination of all of these parameters can be found in Table [2](#tab:mock).

| Parameter                           | Value            | Unit          |
|:------------------------------------|:-----------------|:--------------|
| N Sample                            | 48               |               |
| Resolution elements per galaxy side | 3, 5             |               |
| SNR                                 | 3, 5             |               |
| Galaxy radius                       | 3                | kpc           |
| Rotation velocity                   | 250              | km s${^{-1}}$ |
| Velocity dispersion                 | 50               | km s${^{-1}}$ |
| Inclination                         | 30, 50, 70       | degrees       |
| Disc thickness                      | 0, 0.2, 0.8, 1.6 | kpc           |

: Properties of the mock galaxies used to test `CANNUBI`.

With `CANNUBI` we run an MCMC exploration on the total flux map of the galactic centre, radial extension, inclination and thickness with 20 walkers until convergence on all mock galaxies, which is enough to probe the parameter space of these mock discs. The convergence is estimated using the autocorrelation times of the parameters as explained in (cite: goodman10). We analyse these results in the following Section comparing them to the input values.

### Results on the mock data

To validate the performance of `CANNUBI`, we show in Figure [1](#fig:alb_inc_mock) the comparison between the input and recovered inclinations and disc thickness of the mock galaxies. We show the results over the three values of input inclinations and over the four values of input disc thickness and we show the average errors of each group of inclination and disc thickness as an errorbar.

The galactic centres of the mock galaxies are recovered on average within 1 pixel from the true centre and the disc extent is recovered on average within 0.1 kpc of the true extent. Here we concentrate on the recovered values of the inclination angle and the disc thickness.

We find that, on average, `CANNUBI` recovers the correct inclination within the errors for all groups of inclination: 29$^\circ \pm 7$, 45$^\circ \pm 5$ and 65$^\circ \pm 7$ for input inclinations of 30$^\circ$, 50$^\circ$ and 70$^\circ$, respectively.

The performance is slightly affected by the thickness of the discs, in which thicker input discs tend to have higher errors of up to 12$^\circ$, while the average errors for razor-thin discs are around 3$^\circ$.

The errors could change slightly depending on other factors that we are not exploring in this simple test, such as different velocity curves and surface brightness profiles.

![](albeisa.pdf)

Furthermore, in Figure [1](#fig:alb_inc_mock) we can identify two main situations to be careful of: low-inclination discs and/or very thick discs. In the case of low-inclination discs, the disc thickness estimation can be overestimated as we reach the boundaries of the parameter space, although this is a marginal effect of about 0.1 kpc and it does not affect much the inclination estimates. In the case of very thick discs, the disc thickness is reasonably recovered at the cost of considerably underestimating the inclination, particularly for highly inclined discs (as seen in the outliers in the top panel of Figure [1](#fig:alb_inc_mock)).

This is due to the fact that the shape of the total intensity map is significantly affected by the disc thickness. In the case of very thick discs, we did a preliminary investigation with `CANNUBI` in the full cube mode: in this setting we are minimising the disc geometry models over all the velocity channels instead of the total intensity map. Such a test showed promising results for the thickest discs, however, since it is very computationally intense we could not run it for all the mocks.

We would also like to note that, when the input is a zero thickness disc, we recover a thickness value that is slightly higher than zero. This is due to the fact that here we give the mean of the posterior distributions and that we do not probe regions of negative thickness. As a result, the mean and best-fit value do not fully match, although the distributions still peak at the true value.

Other than that, the disc inclination is, in general, well recovered and, therefore, we can conclude that `CANNUBI` satisfactorily constrains the inclination of mock galaxies within 30$^{\circ}$ to 70$^{\circ}$ and with disc thickness up to a quarter of the extent of the galaxies.

In the particular case of zero thickness, which we use for our galaxy sample (Section [4.2.1](#sec:disc)), the experiments with the mock galaxies show an excellent recovery of the inclinations with errors of about 3$^{\circ}$.

# Results

## Presentation of the data

In Figure [2](#fig:data), we present the dust continuum and \[CII\] total intensity maps of all the galaxies in our sample. The \[CII\] total intensity maps were produced using $^{\text{3D}}$`BAROLO`, by collapsing the velocity range of the emission within the `SEARCH`-masked cube. We used the `SNRCUT` and `GROWTHCUT` parameters given in Table [\[app:kinpar\]](#app:kinpar). Since the noise level of the mask-integrated emission map is different than the channel noise level and no longer uniform, we calculated a pseudo 4$\sigma$-contour ($\sigma_{\mathrm{pc}}$) as explained in Appendix [\[app:ps\]](#app:ps). This is done for visualisation purposes and to ensure that the emission within this mask is real. The flux levels corresponding to the pseudo 4$\sigma$-contours are 1.7, 1.1, 1.4, 0.4 and 0.4 mJy km s$^{-1}$ for AzTEC1, BRI1335-0417, J081740, SGP38326-1 and SGP38326-2, respectively. They are shown as the outermost cyan contours in Figure [2](#fig:data), while the inner contours follow levels of flux above the pseudo 4$\sigma$-contour in powers of 4: $\sigma_{\mathrm{pc}}$, 4$\sigma_{\mathrm{pc}}$ and 16$\sigma_{\mathrm{pc}}$. We note that in the specific case of AzTEC1, there is some extended emission to the north and south with an unclear origin (e.g, cleaning artefacts, outflows).

Additionally, we also display the data cube channel maps in Appendix [\[app:cm\]](#app:cm).

![](data.pdf)

In the system SGP38326, we are only analysing the two main galaxies that are well resolved. However, we also report the discovery of \[CII\] emission in two other companions in the system: SGP38326-3 and SGP38326-4, they are shown in Figure [3](#fig:sgp). The dust emission of SGP38326-3 was previously reported in (cite: oteo16), however, the \[CII\] emission was not detected. We estimated the \[CII\] flux of SGP38326-3 and SGP38326-4 to be 0.35 and 0.16 Jy km s$^{-1}$, respectively, and we did not detect dust continuum in SGP38326-4 down to 0.06 mJy/beam, which is the value of the average noise in the image. Both SGP38326-3 and SGP38326-4 are at an angular distance of about $\sim$2.0" or about 14 kpc in projection from the main galaxy SGP38326-1. SGP38326-3 and SGP38326-4 are at $\sim$600 km s$^{-1}$ and $\sim$800 km s$^{-1}$ spectral distance from the systemic redshift of SGP38326-1, respectively, as measured from the central velocity of both systems. In spite of these \[CII\] emitters being initially discovered by visual inspection, we have also used the 3D source finder in $^{\text{3D}}$`BAROLO` and confirmed their presence. We recover the four objects using `SNRCUT` of 3.5 and a `GROWTHCUT` of 3.

![](sgp_system.pdf)

## Kinematic modelling setup

In this Section, we describe the setup we used in $^{\text{3D}}$`BAROLO` for the kinematic modelling of the sample alongside our assumptions made regarding the initial parameters for the geometry and kinematics.

### Disc geometry

Following the mock data tests we conducted in Section [3.2.2](#sec:CANNUBI), we used `CANNUBI` to estimate the disc geometry of the galaxies in our sample considering a razor thin disc for our fiducial kinematic models. We report the retrieved radial extent, inclination and morphological PA in Table [3](#tab:geometricdata) and the corner plots can be found in Appendix [\[app:cannubicorner\]](#app:cannubicorner). The possible effects of non-zero thickness in the kinematics are discussed in Section [\[sec:discthick\]](#sec:discthick).

In Table [3](#tab:geometricdata), we make a distinction between morphological and kinematic PAs: the morphological PA was estimated from the \[CII\] total flux map with `CANNUBI`, while the kinematic PA was obtained with $^{\text{3D}}$`BAROLO`. $^{\text{3D}}$`BAROLO` initially obtains the first guess of the PA by finding the line that goes through the galactic centre and maximises the velocity gradient across the velocity field. Then to derive the final kinematic PA, we ran $^{\text{3D}}$`BAROLO` with a second fitting stage with a parameter regularisation keeping all other parameters fixed, except `VROT`, `VDISP` and `PA`. For the PA regularisation we chose a 0th order polynomial interpolation.

In an ideal scenario of a purely rotating disc, both PAs should coincide within the uncertainties. A large misalignment between morphological and kinematic position angles could be evidence that the velocity gradient is not due to a rotating disc but instead indicates the presence of interacting systems or outflow motions (cite: krajnovic06). For the galaxies BRI1335-0417, J081740, SGP38326-1 and SGP38326-2 the misalignments are compatible within about 2$\sigma$. The misalignments for these galaxies are smaller than 15$^{\circ}$, except for SGP38326-2 that has a misalignment of 36$^{\circ}$ although it has larger errors associated with it. For AzTEC1 the two values differ considerably outside the uncertainties, by 38$^{\circ}$. This could be due to the presence of a bright region offset by $\sim$ 200 km s$^{-1}$ from the central velocity that shifts the orientation of the total flux map in a different direction in the outer region. This region can be seen in the residual channel maps (see second panel, third row of Figure [\[fig:cmA\]](#fig:cmA)). We investigated this further in Section [\[sec:pvsplit\]](#sec:pvsplit), where we found other indications that AzTEC1 is likely an interacting system.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| ID | Radial extent | PA$_{\textrm{morph}}$ | PA$_{\textrm{kin}}$ | Inclination |
|  | (kpc) | (deg) | (deg) | (deg) |
| AzTEC1 | $4.4 \hspace{0.5mm} \pm \hspace{0.5mm} 0.1$ | $251 \hspace{1mm} ^{+8}_{-8}$ | $289 \hspace{1mm} ^{+2}_{-2}$ | $39 \hspace{1mm} ^{+5}_{-6}$ |
| BRI1335-0417 | $5.8 \hspace{0.5mm} \pm \hspace{0.5mm} 0.1$ | $8   \hspace{1mm} ^{+7}_{-7}$ | $10  \hspace{1mm} ^{+9}_{-9}$ | $42 \hspace{1mm} ^{+3}_{-4}$ |
| J081740 | $4.4 \hspace{0.5mm} \pm \hspace{0.5mm} 0.1$ | $86  \hspace{1mm} ^{+6}_{-6}$ | $99  \hspace{1mm} ^{+1}_{-1}$ | $43 \hspace{1mm} ^{+3}_{-5}$ |
| SGP38326-1 | $4.1 \hspace{0.5mm} \pm \hspace{0.5mm} 0.1$ | $71  \hspace{1mm} ^{+9}_{-9}$ | \*$86  \hspace{1mm} ^{+5}_{-5}$ | $42 \hspace{1mm} ^{+5}_{-6}$ |
| SGP38326-2 | $2.5 \hspace{0.5mm} \pm \hspace{0.5mm} 0.1$ | $83  \hspace{1mm} ^{+18}_{-18}$ | $119 \hspace{1mm} ^{+8}_{-8}$ | $41 \hspace{1mm} ^{+10}_{-14}$ |

: Geometric parameters of the sample estimated with `CANNUBI` under the assumption of a thin disc and minimising over the total flux map. PA$_{\textrm{morph}}$ is the morphological position angle from the total map and PA$_{\textrm{kin}}$ is the kinematic position angle from the velocity gradient, the latter was estimated using $^{\text{3D}}$`BAROLO`.

We note that, for SGP38326-1, we let the PA free in the kinematic modelling and it ranges from 88$^{\circ}$ in the innermost ring to 71$^{\circ}$ in the outermost (as explained in Section [\[sec:SGP1\]](#sec:SGP1)).

### Input parameters

In the kinematic modelling setup, we used an azimuthal normalisation of the surface density and kept the rotation velocity and velocity dispersion parameters free and all other parameters fixed with the exception of the PA for SGP388326-1, as explained in Section [\[sec:SGP1\]](#sec:SGP1). For the masking we used the `SEARCH` task to obtain a tight mask around the emission without any smoothing, the parameters `SNRCUT` and `GROWTHCUT` used are given in Table [\[tab:BBpar\]](#tab:BBpar). We used the systemic redshift determined by $^{\text{3D}}$`BAROLO` which is estimated as the central frequency in the global line profile.

With respect to the geometric parameters, we used the galactic centre obtained with `CANNUBI` which we slightly adjusted in some cases by visually inspecting the velocity field map and the position-velocity (p-v) diagrams (by less than 2 pixels, i.e. significantly within the resolution of the data). The galactic centre coordinates obtained are reported in Table [\[tab:data\]](#tab:data).

Similarly, we slightly adjusted the values of the radial separation between the rings to better correspond to the emission seen in the p-v diagrams, the parameters for the number of rings (`NRADII`) and radial separation (`RADSEP`) are given in Table [\[tab:BBpar\]](#tab:BBpar).

The disc PA is fixed to the kinematic PA to ensure that we cross the region of the highest line-of-sight velocities in the disc, see Table [3](#tab:geometricdata).

We set the disc thickness to an infinitely thin disc and fix the inclination to the one estimated by `CANNUBI`, see Table [3](#tab:geometricdata).

During the fit, we kept the PA fixed across the disc, except for SGP38326-1 as explained in Section [\[sec:SGP1\]](#sec:SGP1). For all galaxies, we fitted the kinematics using both sides of the rotation curve, except for BRI1335-0417 as explained in Section [\[sec:bri\]](#sec:bri).

## Kinematic models

In this Section, we show and describe the best-fit kinematic models for each galaxy.

In Figure [4](#fig:kinmod), we show the velocity fields of the data and the velocity fields extracted from the 3D tilted-ring model in the first and second rows, respectively. These maps were masked with the same pseudo 4$\sigma$-contour from Figure [2](#fig:data).

The rotating disc best-fit models were obtained with $^{\text{3D}}$`BAROLO` using the parameters displayed in Table [\[tab:BBpar\]](#tab:BBpar).

In the second row, we show the outer contour of the axis-symmetric model obtained with `CANNUBI` (in orange), as described in Section [4.2.1](#sec:disc), alongside the outer contour of the model map produced by $^{\text{3D}}$`BAROLO` (in black). The geometry of the two models differ as we favoured the kinematic position angles over the morphological ones for the kinematic fitting. Both are usually very similar for the galaxies, with the notable exception of AzTEC1, as discussed in Section [4.2.1](#sec:disc).

Each of the modelled rings are represented by the white circles along the major axis of the velocity fields.

In the third and fourth rows, we present the p-v diagrams along the major and minor axes, respectively. We show the data emission in gray scale and blue contours following levels of 2$\sigma_{\mathrm{[CII]}}$, 4$\sigma_{\mathrm{[CII]}}$, 8$\sigma_{\mathrm{[CII]}}$ and 16$\sigma_{\mathrm{[CII]}}$. The negative emission is shown as gray contours at $-2\sigma_{\mathrm{[CII]}}$. We show the model contours in red following the same levels.

Now, we detail what can be seen in these maps for each individual galaxy:

![](kinmodels.pdf)

### AzTEC1

The velocity field and major axis p-v of AzTEC1 show a gradient that the model reproduces reasonably well with a nearly flat velocity distribution. It can be seen that the emission in the approaching side of the galaxy flattens more than the receding side, indicating a kinematic asymmetry. As for the minor axis there is a significant emission outside the model contours which tends to broaden the model as $^{\text{3D}}$`BAROLO` attempts to fit it by increasing the velocity dispersion of the model rotating disc.

Another evident feature is that the velocity field of the data in Figure [4](#fig:kinmod) is distorted in the bottom region along the minor axis: it contains a large amount of gas at a velocity around -200 km s$^{-1}$ that bends the iso-velocity contours, including the black contour that traces the central velocity. This region does not affect the rotation curve seen in the p-v of the major axis, however, it can be seen in Figure [4](#fig:kinmod) as an intense region of emission in the bottom left quadrant of the minor axis p-v that cannot be reproduced with the rotating disc model. Moreover, it can also be seen in the residuals of the channel maps in Figure [\[fig:cmA\]](#fig:cmA).

Comparing the two disc geometries shown in the first and second row of Figure [4](#fig:kinmod), we can clearly see the misalignment between the morphological PA and the kinematic PA. In the velocity field it is clear that the velocity gradient does not follow the same direction as the elongation of the \[CII\] total intensity map. Therefore, the morphological PA would not be appropriate to derive the kinematics of the disc as the region with highest line-of-sight velocities would be missed.

[^1]: E-mail: romanoliveira@astro.rug.nl

[^2]: Available at: <https://www.filippofraternali.com/cannubi>

All of these features are indications of a rather disturbed kinematics. In Section [0.1](#sec:pvsplit) we will see that AzTEC1 is likely an interacting system and we will therefore not use our rotating disc model in the further analysis.

### BRI1335-0417

The velocity field and major axis p-v of BRI1335-0417 show the velocity rising in the central parts and decreasing and flattening in the external parts. The line profiles are very broad and they extend in the "forbidden" regions located, in this case, in the upper left and, especially, the lower right quadrants of the p-v. These regions of the diagram are characterised as forbidden since a purely rotating disc cannot populate them. Gas emission in these regions signify deviation from circular motions, e.g., show indications of vertical/radial motions due to inflows/outflows and mergers. The large amount of "forbidden" emission could even be due to the presence of a bar in the central regions of the galaxy, follow-up information on the stellar morphology would be needed to confirm this hypothesis. Similarly to AzTEC1, the broadness of the emission and the emission in the "forbidden" regions can only be reproduced in our best-fit rotating disc model by increasing the velocity dispersion. This may drive an overestimation of the velocity dispersion at some radii.

We also note a feature close to the centre and most evident in the receding side at high velocities. There is a steep rise of the emission in the centre and an absence of such emission at intermediate/outer radii. This excess of emission in the inner regions can be due to an outflow, with velocities up to 400 km s$^{-1}$. See also the residuals of the channel maps in Figure [\[fig:cmB\]](#fig:cmB).

This feature is asymmetric and cannot be reproduced by an axis-symmetric rotating disc model. Therefore, for our fiducial model we prefer to fit the data on the approaching side only to ensure that we are accurately probing the rotation curve.

In the minor axis p-v there is some emission outside of the model, but the most noteworthy feature is an horizontal twist which could further corroborate the need for radial motions in the model. We tried to fit the kinematics with a free PA, but we found that it does not improve the model significantly.

### J081740

The velocity field and major axis p-v of J081740 show that the emission is less broad in velocity than the previous two cases, indicating that it has lower velocity dispersion. The model contours generally agree with the data contours and reproduces most of the emission without any obvious features. The velocity rises in the centre and flattens out quickly. There is also a tail of emission in the upper left quadrant at lower velocity that may indicate the presence of extraplanar gas (cite: marasco19; fraternali02). However it is uncertain whether it is a real feature or due to background noise.

In the minor axis p-v the model reproduces the data well. There is a bright feature in the upper left quadrant that can also be seen in the 54 km s$^{-1}$ velocity channel in the fifth panel in the residuals of the channel maps in Figure [\[fig:cmJ\]](#fig:cmJ). This is not part of the rotating disc and could be due to disturbances driven by a minor merger or gas accretion. However, the bulk of the emission is well described by a rotating disc model. This region can also be seen affecting the lower region of the velocity field in the first row of Figure [\[fig:kinmod\]](#fig:kinmod) by distorting the central velocity contour.

### SGP38326-1

The velocity field and major axis p-v of SGP38326-1 show a very clear velocity gradient with the highest line-of-sight velocity of the sample reaching 380 km s$^{-1}$. It has a rising velocity that flattens in the external regions. The kinematic model reproduces most of the bright emission of the galaxy except for a few interesting features. In the upper left quadrant there is a fainter high receding velocity region that is partially interpreted as high velocity dispersion by the best-fit model, but could be due to a widespread outflow, alike the galactic fountain gas or extraplanar gas seen in local galaxies (cite: fraternali06; boomsma08).

In the lower right quadrant there is another similar structure that forms a southeast tail in the velocity field that is in the direction of the companion galaxy SGP38326-2 and could be evidence of a tidal interaction between the two galaxies. Both these features can be seen as residuals in the channel maps in Figure [\[fig:cmS1\]](#fig:cmS1). Another interesting feature is that the iso-velocity contours in the velocity field are distorted in the central regions as seen in Figure [\[fig:kinmod\]](#fig:kinmod).

This could indicate the presence of a warp that we modelled by leaving the PA free in $^{\text{3D}}$`BAROLO`. We found that the PA ranges from 71$^{\circ}$ in the outermost ring up to 88$^{\circ}$ in the innermost ring. In Figure [\[fig:kinmod\]](#fig:kinmod), we use the PA of the innermost ring to represent the geometry of the kinematic model. We note that the outermost PA coincides with the morphological PA obtained with `CANNUBI` as seen in Table [\[tab:geometricdata\]](#tab:geometricdata).

Such warped disc has a very similar kinematics to the model with constant PA, but given the lower residuals, we consider it as our fiducial model. We note that such distortions could also be due to the presence of radial motions and distinguishing between these two scenarios is difficult (cite: diteodoro21).

### SGP38326-2

The velocity field and major axis p-v of SGP38326-2 show the velocity rising and flattening, like the other galaxies. The kinematic model reproduces most of the emission and no major external features can be seen.

Although the major axis p-v seems like a very well behaved rotating disc, it is important to note that this galaxy might be undergoing a tidal interaction with SGP38326-1 which makes the kinematic fit more challenging.

In the minor axis, the data contours differ significantly from the model. There are two bright regions in the upper left quadrant that are not reproduced by the rotating disc model. This feature is not exceptional to SGP38326-1, however it could be related to the interaction between SGP38326-1 and SGP38326-2, which is visible in Figure [\[fig:sgp\]](#fig:sgp).

## Mergers or rotating discs?

Before we analyse the kinematic models of the galaxies in our sample, we verify the possibility that the velocity gradients that we are observing might be caused by interactions or mergers rather than the presence of a rotating disc. For this, we use the PVsplit diagram, which is a new 3D kinematic classification method to identify the dynamical state of galaxies with the typical resolutions of high-*z* emission-line observations (cite: rizzo22). Unlike other methods, it is based on the analysis of p-v diagrams instead of the moment 1 and 2 maps. It relies on three parameters: `Pmajor`, `PV` and `PR`. `Pmajor` quantifies the asymmetries of emission along the major axis p-v diagram relative to the horizontal axis, defining the systemic velocity or redshift. The `PV` and `PR` parameters quantify the asymmetries related to the peak of the emission (brightest pixels only) along the major axis p-v diagram. The `PV` is the asymmetry over the velocity axis and the `PR` is the asymmetry over the radial axis.

![](pvsplit_3d.pdf)

We perform this analysis on the galaxies and we plot the results in Figure [1](#fig:pvsplit). We compare our galaxies with simulated galaxies known to be mergers or discs taken from (cite: rizzo22). These are ALMA mock observations of galaxies from the `SERRA` simulation (cite: pallottini22). We also show nine randomly selected local disc galaxies from the WHISP survey (cite: vanderhulst01). From the same survey we show nine mergers, minor and major, that have been classified as mergers by both the presence of companions in the datacubes (cite: swaters02; noordermeer05) and HI morphology (cite: holwerda11). Since this is a 3-dimensional analysis, we show the best projection of the PVsplit plane in which we can see the division between the disc galaxies and the mergers. From Figure [1](#fig:pvsplit), it is visible that the two populations occupy different regions in the PVsplit. We highlight this by showing the best-dividing plane for classifying discs and mergers defined by the following equation:

$$\begin{equation}
    -0.63 P_{\mathrm{major}} - 0.27 P_{\mathrm{V}} + 2.78 P_{\mathrm{R}} - 2.72 = 0.
\end{equation}$$

The best-dividing plane was obtained by applying the support-vector machine method with a linear kernel, as implemented in the `sklearn` library (cite: cortes95; scikit-learn). This method maximises the distance between the two pre-classified samples from each other.

All of our galaxies, except for AzTEC1, are located on the disc side of the distribution. J081740 and SGP38326-1 are close to the boundary but AzTEC1 is located significantly closer to the region populated by merging systems. This is another feature that can support the finding that AzTEC1 could be a merger alongside the large difference in the morphological and kinematic position angles. In the following analyses of the kinematic properties of the galaxies, we discard the kinematic modelling of AzTEC1 from our sample.

## Rotation velocities and velocity dispersions

In Table [\[tab:vel\]](#tab:vel), we display the rotation velocities, velocity dispersions and the V/$\sigma$ ratios for the disc galaxies BRI1335-0417, J081740 SGP38326-1 and SGP38326-2. We report two types of rotation velocities: the maximum rotation velocity (V$_{\mathrm{rot,max}}$) of each rotation curve and the external rotation velocity (V$_{\mathrm{rot,ext}}$). Similarly, we report two values for the velocity dispersion: the mean velocity dispersion across the disc ($\bar{\sigma}$) and the external velocity dispersion ($\sigma_{\mathrm{ext}}$). For the external rotation velocities and velocity dispersions, we average the last two resolution-independent points of the rotation curve and of the velocity dispersion profile, respectively. We note that here we are reporting the rotation velocities, not the circular velocities, thus, these rotation curves should not be used to retrieve dynamical models. These rotation velocities will be corrected for pressure support (cite: iorio17) in the following paper where we will analyse the dynamics in detail.

| ID | V$_{\textrm{rot,max}}$ | V$_{\textrm{rot,ext}}$ | $\bar{\sigma}$ | $\sigma_{\textrm{ext}}$ | V$_{\textrm{max}}/\bar{\sigma}$ | V$_{\textrm{rot,ext}}/\sigma_{\mathrm{ext}}$ |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| BRI1335-0417 | 198$^{+17}_{-16}$ | 125$^{+27}_{-26}$ | 75$^{+10}_{-10}$ | 57$^{+11}_{-11}$ | 2.7 $\pm$ 0.4 | 2.2 $\pm$ 0.6 |
| J081740 | 277$^{+40}_{-38}$ | 249$^{+50}_{-53}$ | 50$^{+13}_{-13}$ | 33$^{+13}_{-13}$ | 5.5 $\pm$ 1.7 | 7.6 $\pm$ 3.4 |
| SGP38326-1 | 562$^{+24}_{-26}$ | 548$^{+61}_{-71}$ | 58$^{+12}_{-12}$ | 46$^{+11}_{-9}$ | 9.8 $\pm$ 2.0 | 11.8 $\pm$ 2.9 |
| SGP38326-2 | 417$^{+51}_{-66}$ | 409$^{+39}_{-48}$ | 49$^{+16}_{-14}$ | 40$^{+13}_{-11}$ | 8.3 $\pm$ 2.8 | 10.2 $\pm$ 3.2 |

In Figure [2](#fig:rotcur), we show the rotation curves and the velocity dispersion profiles along the radial extent of the galaxies. We see that the galaxies have typically flat rotation curves and declining velocity dispersion profiles. Essentially, all values of velocity dispersions are below 100 km s$^{-1}$.

![](rotcurv.pdf)

To analyse these results, we choose to focus on two values in Figure [3](#fig:sigma): $\bar{\sigma}$ and V$_{\mathrm{rot,max}}/\bar{\sigma}$. The average velocity dispersion ($\bar{\sigma}$) provides insight into the overall turbulence across the disc and the ratio of maximum rotation velocity and the average dispersion (V$_{\mathrm{rot,max}}/\bar{\sigma}$) can tell us about how much dynamical support is due to ordered or turbulent motions. In Figure [3](#fig:sigma), we show the trends of the dispersion velocities of this sample in comparison with an expanded sample of other galaxies in the literature at a similar redshift, observed in \[CII\] or CO, well-resolved and analysed with a 3D kinematic methodology. We remind the reader that a 3D methodology is necessary in order to fully correct for beam smearing effects in low-resolution data.

We see that our sample is similar to other galaxies with dynamically cold discs at similar redshift (cite: hodge12; rizzo20; rizzo21; lelli21).

We note that there are other works at this redshift range that we do not compare in Figure [3](#fig:sigma) due to poor angular resolution (cite: jones21; fraternali21), due to a 2D kinematic analysis (cite: carniani13; jones17).

Additionally, other works outside our redshift range have analysed the kinematics of other sources with indications of rotating discs both in star-forming galaxies (cite: smit18; herreracamus22; tokuoka22) and in quasar host galaxies (cite: neeleman21; pensabene20; yue21; shao22).

Additionally, we can see a significant evolution in velocity dispersions when compared to HI and CO measurements of Local Universe spiral galaxies (cite: bacchini19; bacchini20). We choose to show the data from (cite: bacchini19) and (cite: bacchini20) given that they are also analysed with $^{\text{3D}}$`BAROLO`, although they are in agreement with other studies at low redshift, e.g., (cite: narayan02; tamburro09).

Furthermore, this is in line with the trends seem at lower redshift (cite: uebler19), but our values for the velocity dispersion are typically lower than found in some intermediate redshift galaxies observed in cold gas (cite: kaasinen20) or ionised gas (cite: turner17).

We note that the \[CII\] line emission traces different gas phases (cite: wolfire22). However, the velocity dispersions of these three tracers are observed to be similar in nearby galaxies, in particular \[CII\] agrees well with the CO distribution and linewidths (cite: deblok16).

In Figure [3](#fig:sigma), we see that most galaxies of our sample and the extended sample have dynamically cold discs, comparable to the ones found in the Local Universe and systematically above the theoretical expectations (cite: dekel14; zolotov15; hayward17; pillepich19), although it is clear that our high V/$\sigma$ values are largely driven by the fast rotations. The high V/$\sigma$ and relatively low $\sigma$ are consistent, instead, with recent predictions obtained using zoom-in simulations on *z* $\gtrsim 6$ main-sequence galaxies (cite: kohandel20; tamfal22). The only exception is the quasar host galaxy BRI1335-0417, which is the only galaxy in marginal agreement with the model expectations. In the following Section, we further discuss the interpretations of the kinematic models shown here.

![](vsigma_z.pdf)

# Discussion

## Gas kinematics at *z* $\sim$ 4.5

In the previous Section, we have presented the ALMA \[CII\] 158 $\mu$m datasets of five galaxies at *z* $\sim$ 4.5 and the results of the kinematic models obtained with $^{\text{3D}}$`BAROLO`. The sample is very diverse: AzTEC1 is a starburst galaxy, BRI1335-0417 is a starburst and quasar host galaxy, J081740 is a normal star-forming galaxy and SGP38326-1 and SGP38326-2 are starburst galaxies part of a group.

In this Section, we discuss the comparison with previous works, the reliability of our results as well as how do these galaxies fit into the context of other kinematically cold discs at *z* $\sim$ 4.5.

#### AzTEC1

Previous studies of AzTEC1 found a velocity gradient in the velocity fields as traced by CO(J=4-3), \[CII\] 158 $\mu$m and \[NII\] 205 $\mu$m emission. With `GalPak3D` (cite: bouche15), it was found that that the velocity gradient in the \[CII\] 158 $\mu$m is consistent with a rotating disc model with a V/$\sigma \sim 2.5$ (cite: tadaki19; tadaki18). However, many off-centre clumps and non-corotating regions have been found in AzTEC1 in the gas and dust emission (cite: iono16; tadaki20), including the clump that we mention in Section [\[sec:aztec\]](#sec:aztec). The latter was identified by (cite: tadaki20) as a non-corotating inflow of gas, likely a gas rich minor merger.

When also taking into account the misalignment of the morphological and kinematic PA identified in Section [\[sec:disc\]](#sec:disc) and the position in the PVsplit diagram in Figure [1](#fig:pvsplit), we find that AzTEC1 is likely a spatially unresolved interacting system or merger and thus the velocity difference between the two interacting galaxies can contribute to the observed velocity gradient. For this reason we do not show values of V and $\sigma$ in Figure [2](#fig:rotcur) and Table [\[tab:vel\]](#tab:vel) as it may not reliably trace the dynamical information of an underlying rotating disc.

The merger can also be an explanation for the high \[CII\] flux and SFR. Given that the dataset analysed in this work has an integration time of only 30 min with ALMA, it is possible that deeper observations at higher angular resolution can solve this issue. Furthermore, future observations with the James Webb Space Telescope (JWST) could also provide insights into the nature of AzTEC1 and, perhaps, confirm the merger scenario.

#### BRI1335-0417

As mentioned in Section [\[sec:data\]](#sec:data), a recent study of BRI1335-0417 analysing the CO(J=7-6) emission found evidence of a bipolar central outflow up to $\sim$600 km s$^{-1}$ that can be associated with the quasar (cite: lu18). In the \[CII\] 158 $\mu$m emission we find a feature that can be a match to the feature seen in (cite: lu18). The presence of this high-velocity feature in the centre of the galaxy may be driving an overestimation of the velocity dispersion at inner radii, as seen in the velocity dispersion profile in Figure [2](#fig:rotcur). Regardless, the average velocity dispersion across the disc is 75 $\pm$ 10 km s$^{-1}$ in spite of the intense SFR of 5$\times 10^3$M$_{\odot}$ yr$^{-1}$. The rotation velocity was found to be 198$^{+17}_{-16}$ km s$^{-1}$, consistent with the dynamical model obtained by (cite: tsukui21) using `KinMS` (cite: davis13). Therefore, BRI1335-0417 has a V/$\sigma$ of 2.7. Making it the rotationally supported disc with the lowest V/$\sigma$ among our sample and the other galaxies at similar redshift shown in Figure [3](#fig:sigma). Despite the low V/$\sigma$ it shows a rather undisturbed disc in the PVsplit analysis.

#### J081740

Previous kinematic analysis of J081740 found that it has a rotation velocity of 272$^{+52}_{-13}$ km $s^{-1}$ and a velocity dispersion of 80$^{+4}_{-11}$ km $s^{-1}$ obtained with `Qubefit` by (cite: neeleman20) and a rotation velocity of $250 \pm 15$ km $s^{-1}$ and a velocity dispersion of $34 \pm 11$ km $s^{-1}$ also obtained with $^{\text{3D}}$`BAROLO` by (cite: jones21). In this paper, we find a maximum rotation velocity of 277$^{+40}_{-38}$ km $s^{-1}$ and average velocity dispersion across the disc of 50$^{+13}_{-13}$ km $s^{-1}$. Therefore, our results are in between the previous two estimates, although the velocity dispersion is closer to the results in (cite: jones21). There is a general compatibility within 1-$\sigma$ errors, except for the velocity dispersion found in (cite: neeleman20). The differences in the estimations are likely due to the differences in the imaging of the datacube, assumptions between `Qubefit` and $^{\text{3D}}$`BAROLO` as well as the different parameters used for the masking and geometry. We estimate a V/$\sigma$ of 5.5, in line with other highly-resolved disc galaxies and higher than the models predict. This is an interesting result, as J081740 is the galaxy with the lowest star formation rate among the galaxies analysed at similar redshift, and likely the closest to the star-forming main sequence. This can only be confirmed with an estimate of the stellar mass and could suggest that also main-sequence galaxies at *z* $\sim 4.5$ host cold rotating discs. As the other galaxies in our sample, we also see non-rotating features that can indicate a minor merger or inflow/outflow as discussed in Section [\[sec:kin\]](#sec:kin).

#### SGP38326-1 and SGP38326-2

In (cite: oteo16) it was found that the CO emission (traced by CO(J=4-3) and CO(J=5-4)) forms a bridge in between the two main galaxies, however, no \[CII\] bridge was found. The dataset we used is considerably deeper and, although, we cannot observe a bridge in the \[CII\] emission of the two galaxies, we can see a non-corotating feature in SGP38326-1 and SGP38326-2 that could be evidence of a \[CII\] tidal tail or connection between the galaxies, adding to the evidence of an interaction.

Regardless of these features, we identify two rotating discs with maximum rotation velocities of 562 $^{+24}_{-26}$ km s$^{-1}$ and 417$^{+51}_{-60}$ km s$^{-1}$ and average velocity dispersions of 58 $^{+12}_{-12}$ km s$^{-1}$ and 49$^{+16}_{-14}$ km s$^{-1}$ for SGP38326-1 and SGP38326-2, respectively. This means they have with V$/\sigma$ of 9.8 and 8.3, similar to the other rotating discs at *z* $\sim$ 4.5.

[^1]: E-mail: romanoliveira@astro.rug.nl

The newly discovered \[CII\] emission of SGP38326-3 and SGP38326-4 shown in Figure [\[fig:sgp\]](#fig:sgp) indicates that this might be a rich group, possibly the early stages of a proto-cluster. Deeper observations and over a larger bandwidth could find more companions.

The general picture that we obtain is that rotating gas discs with V$/\sigma \gtrsim 5$ are common among many different types of galaxies at *z* $\sim$ 4.5. This is in line with early JWST results that show significantly higher disc fractions than previously expected at high-*z* and that disc galaxies are the dominant morphology up to *z* = 6 (cite: ferreira22; robertson23).

In all five galaxies in our sample, there are non-corotating regions which can be indications of gas accretion or outflows.

The average velocity dispersions across the discs of our sample range between 50 km s$^{-1}$ and 75 km s$^{-1}$. BRI1335-0417 has a slightly higher velocity dispersion than other galaxies, albeit compatible within 1-$\sigma$ errors, which leads to a V$/\sigma$ marginally compatible with theoretical expectations (cite: pillepich19).

The different V/$\sigma$ value can be due to the fact that we are comparing submillimetre galaxies (cite: rizzo20; lelli21; rizzo21) with a quasar host galaxy, in the latter high tubulent motions can be driven by the AGN feedback.

BRI1335-0417 shows extensive emission in the "forbidden" regions of the major axis p-v. These features are usually dynamical evidence of the presence of bars in local galaxies and could be later confirmed by observations of the stellar component of the galaxies with JWST, but they can also be evidence of strong non-circular (likely outflow) motions. We also observe some distortions in the iso-velocities of SGP38326-1 that can indicate radial motions or a warp.

Finally, we stress the challenges of deriving reliable kinematic parameters in high-*z* galaxies. The typical limitations in SNR and spatial resolution of observations of high-*z* galaxies can bias the interpretation of the kinematics. In (cite: rizzo22), it was shown using mock data obtained from hydrodynamical simulations that, depending on the methodology, discs can be completely misclassified as mergers or dispersion dominated systems, while up to 50% of mergers can be misclassified as discs.

Therefore, the presence of velocity gradients is not sufficient to classify a system as a disc.

## Disc thickness

Finally, in this Section we discuss the fact that all the galaxies analysed here have inclinations close to $\sim$42$^{\circ}$, well below 60$^{\circ}$ which is the expected median inclination of a sample composed of galaxies with random inclinations (cite: romanowsky12). A possible bias that could favour the selection of low-inclination galaxies in line-emission observations is the fact that high-inclination galaxies have their emission spread out over a wider velocity range when compared to low-inclination galaxies with the same line flux (cite: kohandel19). This bias is expected to be important in the case of faint sources close to the detection limit and might indeed influence J081740 and SGP36326-2 but not SGP3626-1 and BRI1335-0417 given that the latter are on the bright end of the \[CII\] flux distribution of non-lensed sources at *z* $\sim 4$. Naturally, due to the small sample size, the galaxies may just coincidentally have similar inclinations, however, it could also be that we are systematically underestimating their inclinations due to our thin disc assumption.

To investigate how important the effect of disc thickness is in our kinematic modelling, we attempted a direct determination of the disc thickness with `CANNUBI`. As discussed in Section [\[sec:CANNUBI\]](#sec:CANNUBI), for thick discs the best approach is to run `CANNUBI` over the full data cube to better discern the degeneracy between inclination and disc thickness. So we run `CANNUBI` on the galaxies keeping the PA fixed to the morphological PA and leaving the inclination and disc thickness (constant with radius) free. Our results are the following: for BRI1335-0417 we obtain a disc thickness of 1.6 $\pm$ 0.1 kpc with a disc inclination of $58^{+8}_{-5}$ degrees; for J081740 we obtain a disc thickness of 1.3 $\pm$ 0.1 kpc with a disc inclination of $69^{+11}_{-7}$ degrees; for SGP38326-1 we obtain a disc thickness of 1.2 $\pm$ 0.2 kpc with a disc inclination of $56^{+13}_{-9}$ degrees; for SGP38326-2 we obtain a disc thickness of 0.5 $\pm$ 0.1 kpc with a disc inclination of $44^{+3}_{-4}$ degrees.

Thus, considering the thickness, the inclinations are slightly increased and closer to 60$^{\circ}$ while the disc thickness are of the order of 1 kpc for all galaxies. Interestingly, the thickness of 1 kpc found for our sample are consistent with the typical scale heights of the thick discs in the Local universe, such as the Milky Way (cite: li17; bland-hawthorn16A). This might indicate that thick stellar discs can be formed locally from the thick gas disc in the early stages of galaxy formation (cite: brook04). However, the reliability of these results needs to be checked in particular using mock data derived from simulated galaxies, an investigation that we leave to future works.

Despite the open questions outlined above, it is important to quantify the impact of thickness on the kinematics. The inclinations retrieved simultaneously with the disc thickness represent an increase of 15 degrees in the average inclination of the sample. We have then rerun $^{\text{3D}}$`BAROLO` fixing the inclinations and thicknesses to the values reported above for the individual galaxies and obtained new best-fit rotations and velocity dispersions. This resulted in an average decrease of 10% in the maximum rotation velocity of the galaxies, while the changes in the velocity dispersion are within the errors and the rotation curves retained the same shape.

An important caveat here is that the ring by ring approach used in $^{\text{3D}}$`BAROLO` is not ideal to perform fits where the thickness of the discs is larger than the spatial resolution of the observations, as it happens in particular in the case of BRI1335-0417. However, even considering a velocity correction based only on the change in inclination with a simple ratio between the $\sin$ of the inclinations, the highest impact would be to reduce the rotation velocity and V/$\sigma$ of J081740 by 20% and less than that for the other galaxies.

Overall our general results that the discs of these galaxies are cold and the V/$\sigma$ values are significantly larger than model predictions remain unchanged. Finally, we note that in Figure [\[fig:rotcur\]](#fig:rotcur), we show only errors related to the kinematic fitting. However, for the upcoming dynamical modelling we will also take into account the systematic uncertainties due to the impact of the thickness on the inclination.

# Conclusions

The purpose of this study was to further understand the dynamics of discs in the early Universe. We presented high-resolution ALMA observations, at scales in the range of 0.9 to 1.2 kpc, of the \[CII\] 158 $\mu$m emission line of five galaxies at *z* $\sim$ 4.5.

We derived robust kinematic parameters, namely rotation velocities and velocity dispersions at various galactocentric radii for each of the four galaxies using $^{\text{3D}}$`BAROLO`. This methodology properly accounts for beam smearing effects.

We determined the disc geometry of the galaxies including an attempt at directly measuring their disc thickness.

The main results of this paper are summarised below:

1.  Of the five galaxies we find that four of them have rotationally supported discs (BRI1335-0417, J081740, SGP38326-1 and SGP38326-2) and one of them is likely a close interaction or a merger that is spatially unresolved (AzTEC1). Together with other high-resolution galaxy observations at the same redshift range, we confirm that discs are already in place at *z* $\sim$ 4.

2.  The rotating disc galaxies at *z* $\sim$ 4.5 have flat rotation curves with maximum rotation velocities ranging between 198 and 562 km s$^{-1}$ and velocity dispersions averaged across the discs ranging between 50 and 75 km s$^{-1}$. The ratios of rotation-to-random motions (V/$\sigma$) are 2.7, 5.5, 9.8 and 8.3 for BRI1335-0417, J081740, SGP38326-1 and SGP38326-2, respectively. These V/$\sigma$ values are significantly outside the predictions of current models, with the exception of BRI1335-0417 that is in marginal agreement with expectations.

3.  In spite of the presence of regularly rotating discs, we found that non-circular motions are ubiquitous among the galaxies in our sample. These features can be evidence of interactions or gas inflow/outflow. In BRI1335-0417, an outflow is likely responsible for the high \[CII\] velocities observed close to the galactic centre, while the interpretation of other features require more investigation.

4.  We discover \[CII\] emission in a third and fourth galaxy in the SGP38326 system and we find evidence that the two main galaxies might be tidally interacting, as shown in \[CII\], which was not clear from previous works with shallower and lower resolution data.

Although it is hard to create a statistical picture of the kinematics at high-*z* due to the lack of highly resolved observations of large samples of galaxies, this study shows that rotating discs can be common occurrences at *z* $\sim$ 4.5 in spite of the existence of several complex features in their kinematics.

For our kinematic analysis, we used the standard approach of assuming razor-thin discs or, more realistically, a disc thickness that is significantly lower than the resolution of the data. However, we also made the first attempt towards an estimate of their thickness and found values of the order of 1 kpc.

In a follow-up study we will cover the origin of turbulence (e.g., due to stellar feedback or gravitational instabilities), the mass decomposition of the rotation curves obtained in this work and investigate the location of these galaxies in scaling relations.

[^1]: E-mail: romanoliveira@astro.rug.nl

# Acknowledgements

We thank the anonymous referee for their careful and valuable feedback. FRO and FF acknowledge support from The Dutch Research Council (NWO) through the Klein-1 Grant code OCEN2.KLEIN.088. FR acknowledges support from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 847523 ‘INTERACTIONS’ and the Cosmic Dawn Center that is funded by the Danish National Research Foundation under grant No. 140. We acknowledge extensive assistance from Allegro, the European ALMA Regional Center node in the Netherlands. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration. This work makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00330.S, ADS/JAO.ALMA#2017.1.00127.S, #2017.1.00394.S, #2017.1.01052.S, #2018.1.00001.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile.

[^1]: E-mail: romanoliveira@astro.rug.nl

# Data Availability

The data underlying this article are public and available in the ALMA Science Archive, at <https://almascience.nrao.edu/asax/>. The clean datacubes, parameter files and outputs of $^{\text{3D}}$`BAROLO` are available in the Zenodo (DOI:10.5281/zenodo.7543961). $^{\text{3D}}$`BAROLO` is available at <http://editeodoro.github.io/Bbarolo/>. `CANNUBI` is available at <https://www.filippofraternali.com/cannubi>.

[^1]: E-mail: romanoliveira@astro.rug.nl

# Kinematic model parameters

In Table [\[tab:BBpar\]](#tab:BBpar), we present the parameters used in $^{\text{3D}}$`BAROLO` to obtain the kinematic models shown in Section [\[sec:kin\]](#sec:kin).

We note that the velocity channels of AzTEC1 and BRI1335-0417 can be considered fully independent since the native spectral resolution of these data are much higher than the channel widths chosen for the datacubes. This is not the case for the datasets of J081740 and SGP38326, in which we have to consider a spectral resolution 1.21 times the velocity channel width (see Section 5.5.2 of the ALMA Cycle 9 Technical Handbook). This affects the `LINEAR` parameter used in $^{\text{3D}}$`BAROLO` which is FWHM/2.355 for AzTEC1 and BRI1335-0417 and 1.21 $\times$ FWHM/2.355 for J081740 and SGP38326, where FWHM is the channel width as given in Table [\[tab:data\]](#tab:data).

[^1]: E-mail: romanoliveira@astro.rug.nl

|           | AzTEC1 | BRI1335-0417 | J081740 | SGP38326-1 | SGP38326-2 |
|:----------|:------:|:------------:|:-------:|:----------:|:----------:|
| X0        |   82   |      46      |   51    |     51     |     44     |
| Y0        |   76   |      49      |   52    |     46     |     49     |
| RADSEP    |  0.11  |     0.15     |  0.13   |    0.13    |    0.12    |
| NRADII    |   4    |      5       |    4    |     5      |     3      |
| INC       |   39   |      42      |   43    |     42     |     41     |
| PA        |  289   |      10      |   99    |    free    |    119     |
| Z0        |   0    |      0       |    0    |     0      |     0      |
| GROWTHCUT |  2.5   |     2.5      |   2.5   |    2.0     |    3.0     |
| SNRCUT    |  3.5   |     3.0      |   3.5   |    3.0     |    3.5     |
| LINEAR    |  0.43  |     0.43     |  0.51   |    0.51    |    0.51    |
| SIDE      |  both  | approaching  |  both   |    both    |    both    |

# Pseudo Contour Method

In Figures [\[fig:data\]](#fig:data) and [\[fig:kinmod\]](#fig:kinmod) we masked the emission with a pseudo 4$\sigma$-contour for better visualisation as it ensures that the emission within the mask is likely real. The pseudo contour method explained here is required primarily because the number of collapsed channels in the total intensity map is not constant across the map. To determine the pseudo 4$\sigma$-contour ($\sigma_{\textrm{pc}}$), we used `CANNUBI` that follows a similar procedure to (cite: verheijen01). The software first obtains a 3D mask using $^{\text{3D}}$`BAROLO` by smoothing the datacubes and performing a 3D search of the object. All pixels outside of the mask are set to zero and all the channels containing emission were added to build the integrated emission map. The noise per pixel ($\sigma_{\mathrm{tot}}$) in this map is determined as:

$$\begin{equation}
\label{eq:pseudo}
    \sigma_{\textrm{tot}} = \sqrt{N} \sigma_{\mathrm{[CII]}},
\end{equation}$$

where $N$ is number of channels inside the mask that contributed to that pixel and $\sigma_{\mathrm{[CII]}}$ is the noise per channel (see Table [\[tab:data\]](#tab:data)). This allows CANNUBI to create a SNR map. Then the pseudo NT$\sigma$-contour is calculated by selecting all the pixels in this map with $\textrm{SNR}_{\textrm{tot}}$ values in the interval:

$$\begin{equation}
\label{eq:NT}
    0.95 \times \textrm{NT} < \textrm{SNR}_{\textrm{tot}} < 1.05 \times \textrm{NT},
\end{equation}$$

where NT, "Noise Times", is an arbitrary level in the SNR map. We choose the value of NT = 4 for all the galaxies, which defines a pseudo 4$\sigma$-contour in the SNR map and secures that any emission inside it is likely real and part of the system. Finally, CANNUBI calcutes the average value of the pixels in the total intensity map corresponding to those identified by Equation [\[eq:NT\]](#eq:NT). This is the pseudo 4$\sigma$ flux value. We use this flux to determine the mask used in Figure [\[fig:data\]](#fig:data).

[^1]: E-mail: romanoliveira@astro.rug.nl

It is important to note that `CANNUBI` derives the desired pseudo $\sigma$-contour level utilising the 0th moment maps produced by $^{\text{3D}}$`BAROLO`, which may have different units depending on the software version. Here, we report the \[CII\] intensity in Figure [\[fig:data\]](#fig:data) and the pseudo 4$\sigma$-contours in Section [\[sec:presentation\]](#sec:presentation) in units of Jy km s$^{-1}$, which is native to the version 1.6.1 of $^{\text{3D}}$`BAROLO` used in this work.

# Channel Maps

In Figures  [1](#fig:cmA) -  [5](#fig:cmS2), we show representative channel maps of the \[CII\] emission of each galaxy in our sample alongside the best-fit kinematic model obtained with $^{\text{3D}}$`BAROLO` that we describe in Section [\[sec:kin\]](#sec:kin). We show three rows of panels, from top to bottom, respectively, the data, the model and the residuals. We show the data in blue contours for the positive emission and gray for the negative emission. The model is shown in red contours. The contours follow the emission intensity according to $2\sigma_{\mathrm{[CII]}}, 4\sigma_{\mathrm{[CII]}}, 8\sigma_{\mathrm{[CII]}}$ and $16\sigma_{\mathrm{[CII]}}$, the negative contours are at $-2\sigma_{\mathrm{[CII]}}$. For the $\sigma_{\mathrm{[CII]}}$ values see Table [\[tab:data\]](#tab:data).

![](chanmap_aztec.pdf)

![](chanmap_bri.pdf)

![](chanmap_j0817.pdf)

![](chanmap_sgp1.pdf)

![](chanmap_sgp2.pdf)

# `CANNUBI` Corner Plots

In Figures [6](#fig:cpA) -  [11](#fig:cpS2), we show the posterior distributions obtained by applying `CANNUBI` on our sample of *z* $\sim 4.5$ galaxies.

![](cannubi_AzTEC1.jpg)

![](cannubi_BRI1335.jpg)

![](cannubi_ALMA_J081740.86+135138.2.jpg)

![](cannubi_SGP38326-1.jpg)

![](cannubi_SGP38326-2.jpg)

[^1]: E-mail: romanoliveira@astro.rug.nl

</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "CO(J=4-3), CO(J=2-1), and CO(J=5-4) luminosities and SFRs for AzTEC1, BRI1335-0417, J081740, and SGP38326",
  "failed_quote": "1. (cite: yun15); 2. (cite: lu18); 3. (cite: jones16); 4. (cite: neeleman20); 5. (cite: oteo16)."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Fit 3D tilted-ring models to the masked [CII] datacubes using 3DBAROLO with azimuthal surface density normalisation; derive kinematic PA using 2-stage regularisation (0th-order polynomial), then fix geometry (X0, Y0, INC, Z0=0, PA=PA_kin, except free PA for SGP38326-1) and fit VROT and VDISP in independent radial rings; repeat fit with thick-disc INC and Z0 values to assess systematic uncertainty",
  "failed_quote": "In the kinematic modelling setup, we used an azimuthal normalisation of the surface density and kept the rotation velocity and velocity dispersion parameters free and all other parameters fixed with the exception of the PA for SGP388326-1, as explained in Section [sec:SGP1]."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Circular orbits with no large-scale radial or vertical motions; razor-thin disc (Z0 = 0) for fiducial fit; azimuthal surface density normalisation",
  "failed_quote": "In the kinematic modelling setup, we used an azimuthal normalisation of the surface density and kept the rotation velocity and velocity dispersion parameters free and all other parameters fixed with the exception of the PA for SGP388326-1, as explained in Section [sec:SGP1]."
 },
 {
  "path": "analysis_steps[4].validation.evidence[1]",
  "value": "Visual comparison of data vs model velocity fields, major/minor axis p-v diagrams, and channel map residuals; test sensitivity to disc thickness",
  "failed_quote": "In Figures 1 - 5, we show representative channel maps of the [CII] emission of each galaxy in our sample alongside the best-fit kinematic model obtained with $^{\\text{3D}}$`BAROLO` that we describe in Section [sec:kin]."
 },
 {
  "path": "software[2].used_for.evidence[2]",
  "value": "3D source finding/masking (SEARCH), mock galaxy generation (GALMOD), 0th moment map generation, and 3D tilted-ring kinematic modelling",
  "failed_quote": "Here, we report the [CII] intensity in Figure [fig:data] and the pseudo 4$\\sigma$-contours in Section [sec:presentation] in units of Jy km s$^{-1}$, which is native to the version 1.6.1 of $^{\\text{3D}}$`BAROLO` used in this work."
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "Discovery of [CII] emission in two companion galaxies (SGP38326-3 and SGP38326-4) at ~14 kpc projected distance from SGP38326-1, indicating a rich group or early proto-cluster",
  "failed_quote": "The newly discovered [CII] emission of SGP38326-3 and SGP38326-4 shown in Figure [fig:sgp] indicates that this might be a rich group, possibly the early stages of a proto-cluster."
 }
]
```
