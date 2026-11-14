# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...678A.116A\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Tracing obscured galaxy build-up at high redshift using deep radio surveys

A fundamental question of extra-galactic astronomy that is yet to be fully understood, concerns the evolution of the star formation rate (SFR) and supermassive black hole (SMBH) activity with cosmic time, as well as their interplay and how it impacts galaxy evolution. A primary focus that could shed more light on these questions is the study of merging systems, comprising highly star-forming galaxies (SFGs) and active galactic nuclei (AGN) at the earliest stages of galactic formation. However, considering the challenges associated with identifying these objects, it is essential to explore complementary selection methods across multiple wavelengths.

The primary objective of this study is to conduct a comprehensive analysis of a sample of high-redshift ($z>3$) far-infrared (far-IR) and radio-emitting galaxies in the highest possible spatial resolution. The aim is to study the properties of this population, such as their morphological characteristics, and to explore the interplay of SFR and SMBH activity at this epoch.

In order to select the galactic population of our interest, we employed two selection criteria that have frequently been used as separate methods in the literature. In more detail, we selected galaxies that present relatively compact radio morphologies at 1.4 GHz (i.e. an angular size smaller than 10 arcsec) as well as a far-IR spectrum that peaks in flux at $\lambda \geq 350 \, \mu m$ (i.e. $flux_{350\mu m}>flux_{250\mu m}$). For these selection criteria, we used the COSMOS and ECDF-S fields, two of the most extensively observed astronomical fields currently available, which provide high spectral and spatial resolution at a multi-wavelength scale. By accepting only galaxies that satisfied these selection criteria, we derived a sample of eight galaxies that were identified either photometrically or spectroscopically at $z>3$ from literature studies and by our team.

A thorough investigation of available optical, near-IR, and millimetre (mm) imaging reveals a possible merging scenario in five out of eight cases in our sample. Additionally, available multi-wavelength photometry strongly suggests active star formation at the $10^3 \, M_{\odot}/yr$ level in massive systems (stellar masses of $M_{\star}\sim 10^{11} \, M_{\odot}$) co-hosting an active SMBH.

Comparison of these results with previous studies, suggests that our selection method preferentially identifies galaxies hosting an active SMBH, as well as a strong SFG component, resulting in high SFR and IR luminosity. An additional examination of the efficacy of the radio and far-IR selection criteria provides further support for their combined application in selecting co-evolving AGN and star formation activity at high redshift. In this regard, future use of these selection criteria on radio and far-IR/mm observations of statistically larger galaxy samples is of high interest.

# Introduction

One of the main challenges in the field of extra-galactic astronomy is understanding how the star formation rate density (SFRD - $M_{\odot}/yr/Mpc^3$) evolves with redshift (cite: 2017ApJ...840...39M; 2018ApJ...855..105O; 2020ARA&A..58..157T). While we have accurate estimates of the SFRD at intermediate redshifts ($1<z<3$) using various selection methods from deep multi-wavelength data (cite: 2020A&A...643A...8G; 2017A&A...602A...5N; 2018ApJ...854...73I; 2017MNRAS.466..861D) that agree with results from hydrodynamical simulations (cite: 2018MNRAS.473.4077P; 2018IAUS..333..228L), uncertainties regarding higher redshifts ($z>3$) still remain (cite: 2019ApJ...877...45M; 2020A&A...643A...8G). For instance, studies of UV-selected galaxy samples (cite: 2016MNRAS.459.3812M; 2018ApJ...854...73I) estimate a steep decline in the SFRD at $z>3$, while other works employing far-IR radio selection criteria (cite: 2013ApJ...779...32V; 2016MNRAS.461.1100R; 2017A&A...602A...5N; 2022MNRAS.509.4291M) or gamma-ray-burst-selected samples (cite: 2008ApJ...683L...5Y; 2009ApJ...705L.104K) suggest a flatter behaviour.

These uncertainties may originate from our current instrumentational limitations, including low sensitivity, coarse spatial resolution, and coverage of small parts of the sky, which hinder our ability to properly characterise distant objects and obtain a statistically unbiased sample at higher redshifts. For instance, observations based on telescopes such as the *Herschel* Space Observatory (cite: 2010A&A...518L...1P) or the Submillimetre Common-User Bolometer Array (cite: 2013MNRAS.430.2513H) are bound to limit the redshift detection to $z_{\rm max} \sim 4$ (cite: 2018A&A...614A..33D), and to uncover only the very bright end of the far-IR luminosity function (cite: 2013MNRAS.432...23G; 2021A&A...648A...8W). On the other hand, more sensitive telescopes, such as the Atacama Large Millimeter/submillimeter Array (cite: 2019clrp.2020...19W) or the Northern Extended Millimeter Array (cite: 2016ITTST...6..223C) are limited to smaller areas. Thereby, these telescopes provide fewer objects (cite: 2017MNRAS.466..861D; 2020ApJS..247...61F; 2021ApJ...923..215C) and reveal a fainter star-forming galaxy (SFG) population (cite: 2021MNRAS.507.3998P). Nevertheless, recent studies using the capabilities of both single telescopes and interferometers have pushed the limits of our current understanding regarding the star formation (SF) history, exposing a mm dusty galaxy population at $z>3$ (cite: 2018A&A...614A..33D; 2019ApJ...878...73Y; 2020A&A...643A...8G).

Another aspect of our current limitations regarding the accurate estimation of the SFRD at high redshifts might be hidden in the selection criteria that are currently used to detect SFGs. Various methods have been employed over the years in order to detect this galaxy population (cite: 2013MNRAS.432...23G; 2015ApJ...811..140B), however, the bulk of the research is focused on the detection of Lyman-break galaxies in the rest frame UV and the application of dust-correction low-redshift empirical relations for the derivation of their star formation rates (cite: 2015ApJ...811..140B; 2018ApJ...855..105O). These relations might not be necessarily valid at $z>3,$ where the SFG population remains uncertain. Alternatively, recent studies using sensitive far-IR or mm telescopes (cite: 2020A&A...643A...8G) or radio surveys (cite: 2021ApJ...909...23T; 2022ApJ...927..204E) aim to reveal a an SFG population that has so far remained undetected in the optical/UV bands, which is estimated to significantly contribute to the SFRD at $z>3$ (cite: 2020A&A...643A...8G). In order to obtain accurate SFR estimates, these studies separate the SFG from the AGN population (cite: 2017A&A...602A.123L; 2020A&A...643A...8G) by removing the AGN contribution from the IR luminosity. However, this approach can introduce a bias in the sample. Interestingly, results from the recent surveys of the *James Webb* Space Telescope (*JWST)* (cite: 2023ApJS..265....5H; 2023arXiv230112825N; 2023ApJ...946L..16P; 2023MNRAS.518L..19R) reveal a dusty-galaxy population like this at even higher redshifts (i.e. $z>6$) that have not been explored before.

Previous studies, such as the work by (cite: 2019ApJ...876..110D), indicated that the galaxy pair and merging ratio increases with redshift (from $\sim 5 \, \%$ at $z<1$ to $\sim 40 \,\%$ at $z>3$ and for $M_{\star}>10^{10.3}\, M_{\odot}$). Therefore, in this work, we question the strategy of removing AGN-contaminated radio sources from selected samples as this approach may overlook merging systems in which the AGN emission conceals an additional SFG population that could significantly contribute to the SFRD at high redshifts. Such galaxies could be detected from the identification of far-IR bright *Herschel* galaxies along with a radio emission. Even though these selection criteria might favour sources with cold gas and negative k-correction, their application to fields with deep coverage (cite: cosmos_paper) along with photometric data and high spatial resolution information from telescopes such as the *Hubble* Space Telescope (HST) and ALMA could potentially reveal a population of SFGs that would be omitted by the current selection criteria because of the AGN contribution of a neighbour galaxy.

In an attempt to explore new techniques to assist radio surveys reaching $z>3$, we present a complementary study combining the radio selection and far-IR peak spectrum criteria (cite: 2022MNRAS.516.5471Y). Furthermore, we suggest that at $z \sim 3-4$, a substantial amount of star formation occurs that is hardly revealed from optical or near-IR surveys, and which is consequently excluded by the current selection methods due to the AGN contribution in the system. In more detail, we explore a sample of $z>3$ far-IR radio-emitting galaxies, detected in the COSMOS and ECDF-S fields, that might uncover interacting systems and merging galaxies with a substantial contribution of an AGN component, along with the presence of high star formation activity. If radio emission can help to pinpoint this important ‘missing’ SF component, upcoming radio surveys, such as the Evolutionary Map of the Universe (EMU) survey (cite: norris; 2021PASA...38...46N) as well as novel selection criteria in the radio (cite: 2021ApJ...909...23T; 2022ApJ...927..204E) could become even more important to our understanding of the SFRD at $z>3$.

The paper is structured as follows: in Sect. 2 we present the method and criteria that were employed in the selection of the original sample and the subsequent reduction of the sample to the high-redshift far-IR radio candidates. Section 3 briefly highlights the photometric and spectroscopic properties of the sample, along with the results obtained from various properties of the entire sample. In Sect. 4 we compare our work with previous studies and provide a brief discussion of the results, emphasising the importance of the merging population for SFRD estimations. Finally, we provide the conclusions of this study in Sect. 5 and discuss future prospects regarding our method. Throughout this paper, we assume a $\Lambda$-CDM cosmology using $H_{\rm 0}=70 \, kms^{-1}Mpc^{-1}$, $\Omega_{\rm m} = 0.3$, and $\Omega_{\rm \Lambda} = 0.7$.

# Sample selection

![]({cosmos_ecdfs}.png)

For our selection, we examined two of the most deeply explored extra-galactic fields that were observed under the projects Extended *Chandra* Deep Field-South (cite: 2005ApJS..161...21L) and Cosmic Evolution Survey (cite: cosmos_paper). In past years, these two fields have been extensively observed in a wide range of electromagnetic frequencies, ranging from X-rays to radio waves. Radio data were obtained from both fields at 1.4 GHz with the VLA (cite: 2010ApJS..188..384S; smolcic17; 2013ApJS..205...13M) at an angular resolution of $\sim 2.5''$.\
The far-IR wavelength regime, which is necessary for our selection, is available through the *Herschel* Multi-tiered Extragalactic Survey (cite: hermes). This survey covered a total of 380 $deg^2$ using the two main instruments on board *Herschel* , namely the Spectral and Photometric Imaging Receiver (cite: 2010A&A...518L...3G; 2010A&A...518L...5N) and the Photodetector Array Camera and Spectrometer (cite: 2010A&A...518L...2P). The ECDFS and COSMOS fields are also included in the covered area of HerMES, comprising a total of $\sim 2 \, deg^2$. Previous studies using HerMES data have demonstrated the efficient use of *Herschel*’s far-IR fluxes for detecting high-redshift ($z>3$) dusty galaxies. For instance, (cite: 2014ApJ...780...75D) employed simple criteria for the increasing fluxes for the 250, 350, and 500 $\mu m$ bands, which is indicative of a far-IR peak at longer (redshifted) $> 350 \, \mu m$ wavelengths, revealing a dusty SF galaxy population with a mean redshift distribution of $<z>\sim 4.7$.\
To identify potential high-redshift hybrid AGN-SFG systems, we conducted a cross-match analysis between the VLA COSMOS and ECDF-S 1.4 GHz catalogues with those of HerMES, applying a maximum separation of 18 arcsec (motivated by the beam size of *Herschel* at 250 $\mu m$ of 18.1 arcsec). The resulting cross-matched sample contained 2292 sources for COSMOS, and for the ECDF-S field is provided 769 sources. This sample was further reduced by considering robust radio sources (signal-to-noise ratio; S/N\>5) without an indication for extended or multicomponent radio emission (cite: 2005ApJS..161...21L; cosmos_paper). To ensure the correspondence between radio and far-IR emission, we excluded from the sample sources that present multiple radio detections within one *Herschel* beam. Furthermore, only sources with 250, 350, and 500 $\mu m$ flux errors smaller than 50 $\%$ were accepted, which ensured that the shape of the far-IR emission was properly determined. This selection method resulted in 219 and 93 sources for COSMOS and ECDF-S, respectively.\
Furthermore, motivated by the efficacy of studies such as (cite: 2014ApJ...780...75D) and (cite: 2018A&A...614A..33D) in selecting high-$z$ dusty SF galaxies, we adopted a similar method to identify sources with $f_{350 \rm \mu m}/f_{250 \rm \mu m}>1$, which would translate into a potential $z > 3$ redshift. This selection method resulted in a sample of 53 and 30 galaxies (see Fig. [1](#cosmos_ecdfs)) for the COSMOS and ECDF-S fields, respectively. The radio 1.4 GHz and far-IR ($250 \, \mu m$) images of each of these sources were visually inspected in order to secure the robustness of the matching process and identify potentially uncertain or confused radio/far-IR detections. We confirmed that all 83 selected sources display compact morphologies both in the radio and in the FIR, and that the detected counterparts are robust, with average separations between the radio and far-IR detections below $\sim 2$ arcsec.

## High-redshift candidates

Application of these far-IR criteria resulted in a sample of $53+30=83$ sources from both fields for which we retrieved possible photometric or spectroscopic identifications from the literature. For this exploration, we consulted Simbad (cite: 2000A&AS..143....9W), the NED[^2] online search tools, and the Cosmos2015 (cite: Laigle16) online catalogue[^3], retrieving redshift values from sources that are within 2 arcsec of our candidates.\
From this analysis, we found 18 sources in the ECDF-S and 19 sources in the COSMOS field with spectroscopic redshift determination. Five of these radio sources present a spectroscopic redshift of $z_{\rm spec}>3$, namely J033140.1-275631 (cite: 2015ApJ...815..129S), J100028.71+023203.7 (cite: 2018ApJ...858...77H), \[LBX2017\] 214 (cite: 2012A&A...546A..84I), COSMOSVLA J100256.53+021158.4 (cite: 2014A&A...563A..54P), and \[DSS2017\] 554 (cite: 2017ApJ...840...78D). The reported spectroscopic redshifts of the two highest- $z$ sources, however, are not reliable. For instance, the candidate with the highest redshift, found in the ECDF-S, reveals contradicting spectroscopic measurements. More specifically, the $z_{\rm spec}=5.137$ value (cite: 2015ApJ...815..129S) contradicts (cite: 2012MNRAS.427..520C) and (cite: 2017ApJ...840...78D), who estimated a lower spectroscopic value of $z_{\rm spec}= 1.617$ (with spectra from optical and far-IR wavelengths) for this candidate. Because a high-redshift nature of this source cannot be excluded, we further explored its available spectra. This investigation indicated that the emission line responsible for the $z_{\rm spec}$=5.137 solution can be also interpreted as an emission line at $z_{\rm spec}$=1.617, which further supports the notion for the intermediate-redshift solution derived in the literature. Therefore, we considered this source as an intermediate-redshift galaxy and did not explore it further.\

![](hist_z_all_4.png)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source name | Abbreviation | RA | DEC | $f_{\rm 1.4GHz}$ | $f_{\rm 250}$ | $f_{\rm 350}$ | $f_{\rm 500}$ |
| – | – | \[*deg*\] | \[*deg*\] | \[*mJy*\] | \[*mJy*\] | \[*mJy*\] | \[*mJy*\] |
| CVLA J100256.53+021158.4 | CVLA1002 | 150.73553 | 2.19963 | $0.104 \pm 0.020$ | $37.0 \pm 3.4$ | $39.7 \pm 6.6$ | $25.1 \pm 5.1$ |
| ALESS J033152.49-280319.1 | ALESS14 | 52.96871 | -28.05531 | $0.103 \pm 0.016$ | $13.0 \pm 6.2$ | $27.7 \pm 3.9$ | $26.7 \pm 4.5$ |
| CVLA J100004.81+023045.2 | CVLA1000 | 150.0200 | 2.51255 | $0.096 \pm 0.015$ | $25.1 \pm 6.3$ | $27.8 \pm 6.6$ | $23.1 \pm 5.3$ |
| CVLA J095845.94+024329.2 | CVLA958 | 149.69144 | 2.72479 | $0.095 \pm 0.018$ | $27.4 \pm 6.3$ | $27.7 \pm 6.6$ | $28.7 \pm 5.4$ |
| CVLA J100233.16+020626.5 | CVLA100 | 150.63817 | 2.10736 | $0.088 \pm 0.015$ | $22.3 \pm 6.3$ | $24.0 \pm 6.6$ | $17.5 \pm 5.3$ |
| CVLA J100028.75+023203.5 | CVLA028 | 150.11958 | 2.53438 | $0.057 \pm 0.015$ | $28.6 \pm 6.3$ | $36.7 \pm 6.6$ | $29.3 \pm 5.2$ |
| ALESS J033211.34-275211.9 | ALESS33 | 53.04738 | -27.87003 | $0.043 \pm 0.012$ | $18.6 \pm 6.2$ | $25.6 \pm 3.9$ | $25.4 \pm 4.7$ |
| $[$DSS2017$]$ 554 | ECDFS544 | 53.42108 | -27.92731 | $0.042 \pm 0.014$ | $24.5 \pm 3.4$ | $27.0 \pm 3.9$ | $23.8 \pm 3.9$ |

Likewise, for J100028.71, inspection of its DEIMOS 10k survey spectrum (cite: 2018ApJ...858...77H) revealed a very low S/N spectrum without an obvious line detection that could explain the $z=4.76$ indication. We assumed an erroneous redshift estimate caused by a possible false-positive of the automated feature recognition from the DEIMOS survey. This source is however kept in this work as a high-redshift source, prompted by a photometric redshift determination of $z_{\rm phot}\sim 3.2$ by (cite: 2015A&A...577A..29M). Inspection of the remaining three sources with a spectroscopic redshift higher than 3 revealed that the emission lines used to determine the redshifts of these sources have either a high S/N (i.e. S/N$>10$) or are denoted with a secure spectroscopic quality flag. This means that these measurements are accurate.\
Our search identifies 12 sources in the ECDF-S field and 34 sources in the COSMOS field based on photometric redshifts from the literature. These results are depicted in Fig. [2](#hist_z), where the histograms for the redshifts of each survey and the total values are plotted with different colours. This figure reveals that our selection favours radio sources around $z\sim 2$ with a distribution that extends to higher redshifts. Four sources of this sample in the COSMOS field have photometric redshifts (identified in the Cosmos2015 catalogue) of $z>3$ (i.e. COSMOSVLA J100233.16+020626.5 with $z_{\rm phot}$=3.016, COSMOSVLA J095845.94+024329.2 with $z_{\rm phot}$=3.172, COSMOSVLA J100028.75+023203.5 with $z_{\rm phot}$=3.175, and COSMOSVLA J100004.81+023045.2 with $z_{\rm phot}$=3.76). Similarly, in the ECDF-S sample, we identified one source with $z_{\rm phot}$\>3, namely ALESS J033152.49-280319.1 (cite: 2011MNRAS.415.1479W). These five high-redshift candidates, along with the three sources with a spectroscopic redshift above 3, are presented along with their 1.4 GHz and far-IR HerMES flux densities in Table [\[radio_sources_table_2\]](#radio_sources_table_2).\
We are particularly interested in sources with the highest redshifts. We therefore decided to further investigate the five sources for which the photo-$z$ indicates a $z>3$ nature. Follow-up observations of these sources aimed to improve the redshift determination (for the photometric redshift estimates), and a more detailed analysis of their properties was initiated, using mm observatories from the northern and southern hemispheres (for the COSMOS and ECDF-S fields, respectively), the first results of which are described in the following section.\
The comparison of our acquired spectroscopic/photometric redshift values for our sample with the corresponding values from alternative photometric catalogues in the literature is a valuable exercise. This comparison is presented in more detail in Appendix [6](#appA) and indicates that the COSMOS and the ECDF-S fields do not contain additional candidates at $z>3$ that our analysis could have miss-identified at lower $z$, and the $z>3$ nature of the five sources with photo-$z$ considered here is confirmed. Therefore, we are more confident that the sources that are presented in the following sections are the only ones with $z_{\rm phot,spec}>3$ that could be selected with our selection criteria from the two fields of study.

# Results

To characterise the morphological and physical properties of the eight high-redshift galaxies under investigation, a detailed examination of the available photometric and spectroscopic data from the literature was conducted. Simultaneously, follow-up observations were initiated, in particular, using millimetre facilities. The results are described below.

During this analysis, a spectral energy distribution (SED) fitting analysis was performed for each galaxy in the sample using CIGALE (cite: cigale1; cigale2). The resulting fits yield two values for each modelled physical property of a galaxy (e.g. stellar mass and redshift), one corresponding to the best-fit solution and another that is derived through a Bayesian statistical analysis. In the following text, we refer to the best-fit values when presenting the sample, while the Bayesian-derived estimates along with their corresponding uncertainties are introduced in Table [\[table2\]](#table2). The images of the eight sources for four different photometric bands (optical, near-IR, radio, and mm wavelengths) are presented in Fig. [4](#figure3). For each wavelength regime, the observations with the highest available spatial resolution were selected.

## SED fitting results

The SED fitting analysis was conducted using the CIGALE software, employing consistent input models and parameters for the entire sample. The data fluxes from the Cosmos2015 catalogue were used in the analysis, while the radio information as well as any nebular emission component were not taken into consideration. For the sources that have been identified spectroscopically in the literature (i.e. CVLA1002, CVLA958, ALESS33, and ECDFS544), the redshift input was fixed to the corresponding spectroscopic value. From the remaining galaxies, ALESS14 and CVLA1000, the redshifts were fixed to the photometric values retrieved from the literature, while for CVLA100 and CVLA028, the best-fitting SED was selected by introducing $\Delta z=0.1$ intervals. The resulting fits, along with the model parameters used in this analysis, are presented in Fig. [3](#all_photometry) and Table [\[CIGALE_models\]](#CIGALE_models).

To probe the significance of the AGN contribution, we applied the same fitting strategy using CIGALE without the AGN component. The updated SED fits revealed that for sources that initially required a lower AGN contribution (e.g. CVLA1000), the $\chi^2$ values changed marginally by approximately $\sim 10 \%$. On the other hand, for galaxies such as CVLA100, which presents a substantial AGN contribution, no accurate SED fit could be provided without an AGN component ($\Delta \chi^2 > 3$). Consequently, this exercise demonstrates the necessity of incorporating an AGN component in the SED fit for five out of eight sources, generally leading to improved fits as compared to those obtained without an AGN component.

![image]({CVLA1002_best_model}.png) ![image]({ALESS014_best_model}.png)

![image]({CVLA1000_best_model}.png) ![image]({CVLA-958_best_model}.png)

![image]({CVLA-100_best_model}.png) ![image]({CVLA028_best_model}.png)

![image]({ALESS33_best_model}.png) ![image]({ECDFS544_best_model}.png)

+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| Type                | Model name            | Reference                  | Parameters used                                       |
+:===================:+:=====================:+:==========================:+:=====================================================:+
| |                |  | sfhdelayed            | (cite: sfhdelayed)         | |                                               |     |
| |:--------------:|  |                       |                            | |:---------------------------------------------:|     |
| | Star formation |  |                       |                            | |  age$\_$main = 1000, 2500, 4500, 6000, 8000   |     |
| |    history     |  |                       |                            | |            tau$\_$burst = 10000.0             |     |
|                     |                       |                            | |        age$\_$burst = 10, 50, 80, 110         |     |
|                     |                       |                            | | f$\_$burst = 0.001, 0.01, 0.03, 0.1, 0.2, 0.3 |     |
|                     |                       |                            | |      sfr$\_$A = 10.0,100.0,1000.0,3000.0      |     |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| Stellar emission    | bc03                  | (cite: bc03)               | |                           |                         |
|                     |                       |                            | |:-------------------------:|                         |
|                     |                       |                            | |     imf = 1(Chabrier)     |                         |
|                     |                       |                            | | metallicity = 0.0001,0.02 |                         |
|                     |                       |                            | |  separation$\_$age = 10   |                         |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| Dust attenuation    | dustatt$\_$2powerlaws | (cite: dustatt_2powerlaws) | |                                                   | |
|                     |                       |                            | |:-------------------------------------------------:| |
|                     |                       |                            | | Av$\_$BC = 0.3, 0.8, 1.2, 1.7, 2.3, 2.8, 3.3, 3.8 | |
|                     |                       |                            | |                slope$\_$BC = -0.7                 | |
|                     |                       |                            | |  BC$\_$to$\_$ISM$\_$factor = 0.3, 0.5, 0.8, 1.0   | |
|                     |                       |                            | |                slope$\_$ISM = -0.7                | |
|                     |                       |                            | |              filters = V$\_$B90, FUV              | |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| |                 | | lyc$\_$absorption     | (cite: lyc_absorption)     | |                          |                          |
| |:---------------:| |                       |                            | |:------------------------:|                          |
| | Lyman Continuum | |                       |                            | | $\rm f_{esc}$ = 0.0,0.5  |                          |
| |     escape      | |                       |                            | | $\rm f_{dust}$ = 0.0,0.5 |                          |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| Dust emission       | dl2014                | (cite: dale2014)           | |                             |                       |
|                     |                       |                            | |:---------------------------:|                       |
|                     |                       |                            | | qpah = 0.47, 1.12, 2.5, 3.9 |                       |
|                     |                       |                            | |   umin = 5.0, 10.0, 25.0    |                       |
|                     |                       |                            | |         alpha = 2.0         |                       |
|                     |                       |                            | |      gamma = 0.02,0.9       |                       |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| AGN                 | fritz2006             | (cite: fritz2006)          | |                                        |            |
|                     |                       |                            | |:--------------------------------------:|            |
|                     |                       |                            | |            r$\_$ratio=60.0             |            |
|                     |                       |                            | |              tau=1.0,6.0               |            |
|                     |                       |                            | |               beta=-0.5                |            |
|                     |                       |                            | |         opening$\_$angle=100.0         |            |
|                     |                       |                            | |               psy=0.001                |            |
|                     |                       |                            | | fracAGN$_{escape}$=0.0,0.1,0.2,0.6,0.8 |            |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+
| Redshift            | redshifting           | (cite: redshifting)        | redshift=0.01-7.5 (or fixed)                          |
+---------------------+-----------------------+----------------------------+-------------------------------------------------------+

## Sample presentation

### COSMOSVLA J100256.53+021158.4

The COSMOS field deep multi-wavelength data provide the opportunity of examining the structure of this source, which appears to be composed of two galaxies: an optically bright quasar, and a fainter millimetre source (see the top left panel of Fig. [4](#figure3)). Spectroscopic data from the BOSS survey (cite: 2016MNRAS.455.1553R) secured the detection of the Ly-$\alpha$ emission line at a redshift of $z=3.503 \pm 0.0007$. Because the BOSS capabilities cannot resolve the two sources in study here, this archival spectrum corresponds to both galaxies. However, considering that the main source (i.e. the quasar) is the brightest galaxy at optical wavelengths, we assume that the emission line and subsequently derived redshift correspond to this source.\
Furthermore, inspection of the 3 GHz data reveals that the quasar causes most of the radio flux density emitted from this system with a value of $f_{\rm3GHz-QSO}=0.052 \pm 0.02 \, mJy$ ($\sim 80 \, \%$ of the total), while the second source has a flux density of $f_{\rm3GHz-2^{nd} source}=0.013 \pm 0.009 \,mJy$. When we assume a typical radio spectral index of 0.8 for both sources[^4], the corresponding radio flux density at 1.4 GHz is equal to $f_{\rm 1.4GHz-QSO}=0.1 \pm 0.04 \, mJy$ and $f_{\rm 1.4GHz-2^{nd} source}=0.024 \pm 0.017 \, mJy$. Therefore, if both galaxies are located at $z \sim 3.5$ and the detected radio emission was generated solely from SF, the corresponding SFR (cite: 2003ApJ...586..794B) would be $SFR_{\rm radio-QSO}=4246 \pm 1633 \, M_{\odot}/yr$ and $SFR_{\rm radio-2^{nd} source}=1061 \pm 735 \, M_{\odot}/yr$ for the quasar and SFG, respectively ($SFR_{\rm radio-total}=5307 \pm 1790 \, M_{\odot}/yr$). According to (cite: 2017A&A...602A.123L), this system of galaxies has a total stellar mass of $log(M_{\star}/M_{\odot})=11.69 \pm 0.01$ and $SFR_{\rm IR-total}$ of 1549 $M_{\odot}/yr$. The latter value is derived from the far-IR flux integrated at the position of the quasar and is rather close to our SED-fitting, best-derived SFR estimate of 1721 $M_{\odot}/yr$. Curiously, this value is similar to the value derived from the radio for the second source in the system (i.e. $SFR_{\rm radio}-2^{nd} source$). This is compatible with a system with a powerful quasar and a companion where most of the SF is taking place, and where no AGN is detected.\
It has to be noted that for most bands, we cannot separate the brightness contribution from each of the two sources because of the sub-arcsec separation and the insufficient angular resolution of telescopes such as *Spitzer*. The SED fit was therefore performed using only total fluxes. A separation of the SED fitting analysis for the two sources would be non-trivial and would yield high uncertainties in the fluxes of each source. In the X-ray regime, COSMOS has been observed both with *XMM-Newton* (cite: Cappelluti) and the *Chandra* X-ray Observatory (cite: 2009ApJ..184..158E; 2016ApJ...819...62C), reaching flux limits of $f_{\rm 0.5-2 keV}\sim 1.7 \cdot 10^{-15} \, erg/s/cm^2$ and $f_{\rm 0.5-2 keV}\sim 2.7 \cdot 10^{-16} \, erg/s/cm^2$, respectively. The source CVLA1002 has been observed and detected by the *Chandra* COSMOS survey with a flux of $f_{\rm 2-10keV}=6.67 \cdot 10^{-15}\, erg/s/cm^2$ (cite: 2016ApJ...817...34M).

### ALESS J033152.49-280319.1

Based on the current photometric data, this source seems to be a single galaxy, and according to the SED photometric analysis by (cite: 2015ApJ...806..110D), it has a photometric redshift of $z \sim 3.38$, an $SFR_{\rm IR}$ of 1202 $M_{\odot}/yr,$ and a stellar mass of $10^{10.96} \, M_{\odot}$. For our photometric analysis, which takes the possibility of an AGN component into account, the estimated best SFR value has a similar value of $SFR_{\rm IR}= 1188$   $M_{\odot}/yr$. Assuming that the galaxy is located at $z=3.38$ and its radio emission is solely due to star formation, the corresponding SFR from the radio emission would be equal to $SFR_{\rm radio}\sim 4213 \pm 757 \, M_{\odot}/yr$. A comparison between this value and the value derived from our SED fitting analysis or by (cite: 2015ApJ...806..110D) suggests that the source hosts intense SF, and an accreting SMBH explains the clear radio excess that is observed. The X-ray energies have been observed in the CDF-S field with *XMM-Newton* and the *Chandra* observatories (cite: 2013A&A...555A..42R; 2017ApJ..228....2L) in deep surveys, resulting in sensitivities of $6.6 \cdot 10^{-16} \, erg/s/cm^2$ and $2.7 \cdot 10^{-17} \, erg/s/cm^2$ at 2-10 keV, respectively. However, ALESS14 is not detected in any of these surveys, supporting the view that if an AGN exists, it contributes mostly to the radio emission, and at a much lower level at X-ray and optical/IR wavelengths. This was also suggested by the $\sim 20 \%$ AGN contribution to the IR emission from our CIGALE SED fit.

### COSMOSVLA J100004.81+023045.2

According to the HELP catalogues (cite: 2021MNRAS.507..129S), this source is located at a redshift of 3.43 with an $SFR_{\rm IR}$ of 1519 $M_{\odot}/yr$, while our SED fitting analysis predicts a lower $SFR_{\rm IR}$ of 690 $M_{\odot}/yr$. Based on the SED fitting results, modelling of the IR emission of CVLA1000 requires an AGN contribution. According to the Cosmos2015 and Cosmos2020 (cite: 2022ApJS..258...11W) catalogues, the photometric redshifts are 3.26 and 3.62, respectively. When we accept an average redshift value of $\sim 3.3$ for this source, then according to its radio flux density of $f_{\rm 1.4GHz}=0.096 \, mJy,$ the $SFR_{\rm radio}$ should be $\sim 3723 \, M_{\odot}/yr$, which in comparison with the previous estimate from the IR emission strongly suggests an active SMBH at the centre of this galaxy.\
Due to its morphology in the near-IR, radio, and mm wavelengths, this source could be classified as a group of galaxies (see the third row of Fig. [4](#figure3)), however, catalogues with large samples of galaxies (i.e. Cosmos2015 and Cosmos2020) identify this galaxy as a single source due to the lack of resolution. With a radial extent of $\sim 1.146$ arcsec, measured at the 1.6 $\mu m$ - NICMOS data, and a scaling factor of $7.524 \, kpc/''$ (at $z=3.3$), the actual size of this galaxy can be estimated as $\sim 8.6\, kpc$. This value is compatible with an ultra-compact dwarf galaxy (cite: 2021MNRAS.505.3192R), however, the images reveal a source that resembles a disk rather than a spherical object. Inspection of all the available images cannot exclude the possibility of a merging system, considering that the NICMOS data depict a structure that could resemble a complex of galaxies. No detection in the X-ray bands is reported in the literature for this galaxy.

![](all4.png)

### COSMOSVLA J095845.94+024329.2

Source CVLA958 was recently spectroscopically observed by our team with the Institut de Radioastronomie Millimetrique (IRAM) 30m antenna (project code: 227-19; for more details regarding these observations, see Appendix [7](#appC)). Unfortunately, its mm faint nature prevented us from acquiring a secure redshift determination with the IRAM telescope. According to Cosmos2015, the photometric redshift of this galaxy is $z=3.172$, while our photometric analysis suggests a minimum of $\chi^2$ at 3.21. The latter redshift solution agrees with the only line that is detected from recent ALMA archival spectra (project code: 2019.1.01600.S). The detected emission line at $\sim 110.5 \, GHz$ has a full width at half maximum of $\sim$0.4 GHz ($\sim 70.4\, km/s$), possibly indicating a merging system or an orderly rotating spiral galaxy (cite: 2022ApJ...929..159C). The recent work by (cite: 2021MNRAS.501.3926B) also identified the emission line as due to the CO4-3 rotational transition at band 3 of ALMA, locating this source at $z=3.1755$. According to our photometric SED fitting analysis, this source has a stellar mass of $10^{11.07}\, M_{\odot}$, an SFR of 1177 $M_{\odot}/yr,$ and a significant AGN contribution. Considering the measured flux density at 1.4 GHz of 90 $\mu Jy$, we estimate that its $SFR_{\rm radio}$ (assuming that its radio emission comes purely from star formation) should be $\sim 3376 \, M_{\odot}/yr$. This value is significantly higher than the value determined from the SED fitting (see Table [\[table2\]](#table2) for further details), supporting the presence of an AGN in this source as well. CVLA958 is not detected in any available dataset in the X-ray wavelengths.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | Redshift$^{(1)}$ | Stellar Mass | $\rm SFR_{IR}$ | $\rm SFR_{radio}$ | AGN $^{(2)}$ | $\rm L_{1.4GHz}$ | $\rm L_{IR}$ $^{(3)}$ | $q_{TIR}^{(4)}$ |
| – | – | \[$M_{\odot}$\] | \[$M_{\odot}/yr$\] | \[$M_{\odot}/yr$\] | \[$\%$\] | \[$10^{24} W/Hz$\] | \[$10^{39} W$\] | – |
| CVLA1002 | $3.503 \pm 0.001^{(s)}$ | $11.62 \pm 0.44$ | $2496 \pm 1266$ | $5307 \pm 1790$ | $41 \pm 22$ | $8.34 \pm 1.60$ | $3.15 \pm 0.01$ | $2.00 \pm 0.08$ |
| ALESS14 | $3.380 \pm 0.25^{(p)}$ | $11.07 \pm 0.85$ | $1123 \pm 142$ | $4213 \pm 757$ | $20 \pm 1$ | $7.63 \pm 1.37$ | $2.19\pm 0.20$ | $1.88\pm 0.09$ |
| CVLA1000 | $3.430 \pm 0.32^{(p)}$ | $12.13 \pm 1.30$ | $711 \pm 40$ | $4057 \pm 792$ | $10 \pm 2$ | $7.35 \pm 1.44$ | $2.15\pm 0.25$ | $1.89\pm 0.10$ |
| CVLA958 | $3.175 \pm 0.001^{(s)}$ | $11.19 \pm 0.44$ | $1225 \pm 546$ | 3382$\pm 641$ | $20 \pm 4$ | $6.13 \pm 1.16$ | $0.58\pm 0.02$ | $1.40\pm 0.11$ |
| CVLA100 | $3.290 \pm 0.39^{(p)}$ | $10.36 \pm 0.52$ | $528 \pm 96$ | $3391 \pm 781$ | $60 \pm 3$ | $6.14 \pm 1.41$ | $1.98\pm 0.32$ | $1.93\pm 0.10$ |
| CVLA028 | $3.270 \pm 0.24^{(p)}$ | $11.13 \pm 0.30$ | $1565 \pm 753$ | $2167 \pm 602$ | $3 \pm 7$ | $3.92 \pm 1.09$ | $2.52\pm 0.22$ | $2.23\pm 0.13$ |
| ALESS33 | $3.694\pm 0.001^{(s)}$ | $11.27 \pm 0.81$ | $978 \pm 113$ | $2140 \pm 597$ | $10 \pm 1$ | $3.88 \pm 1.08$ | $2.20\pm 0.01$ | $2.18\pm 0.12$ |
| ECDFS544 | $3.199\pm 0.001^{(s)}$ | $11.42 \pm 0.80$ | $1083 \pm 470$ | $1520 \pm 507$ | $20 \pm 3$ | $2.75 \pm 0.92$ | $2.01\pm 0.01$ | $2.29\pm 0.15$ |

$^{(1)}$(s): spectroscopic redshift; (p): photometric redshift (accepting the solution with the lowest $\chi^2$ or the best available in the literature), $^{(2)}$: the AGN percentage (Bayesian values) is estimated by our CIGALE fitting and corresponds to the same wavelength range in which the dust luminosity of each source was estimated, $^{(3)}$ this infrared luminosity corresponds to the wavelength range 42-122 $\mu$m (rest frame), $^{(4)}$ according to equation 5 by (cite: 2022ApJ...927..204E): $\rm q_{TIR}=log(L_{IR}/3.75 \cdot 10^{12})-logL_{1.4GHz}$

### COSMOSVLA J100233.16+020626.5

The source CVLA100 seems to be a single galaxy as well. Our photometric analysis places this source at a redshift of $z_{\rm phot}\sim 3.3$. This result agrees with the estimates of other photometric catalogues (cite: Laigle16; 2022ApJS..258...11W). ALMA spectroscopic data acquired by our team (project code: 2017.1.01713.S; see Appendix [7](#appC) for more details) reveal an emission line at $\sim 107.3 \, GHz$, which corresponds to the CO(4-3) emission line with the galaxy located at $z=3.29$. For the derived physical properties of this source, our SED fitting analysis indicates a stellar mass of $10^{10.27} \, M_{\odot}$, an SFR of 566 $M_{\odot}/yr,$ and an AGN fraction of 60 $\%$. Application of equation 6 by (cite: 2003ApJ...586..794B) provides us with an estimate of the $SFR_{\rm radio}$ of 2760 $M_{\odot}/yr$. The SED fitting models for this redshift suggest an SFR of $\sim 500 \, M_{\odot}/yr$, which could mean that the observed 1.4 GHz radio flux cannot be obtained solely from SF, but by a combination of star emission and AGN activity (see Table [\[table2\]](#table2) for additional information). Similarly to CVLA958, this source is not detected at any high-energy band.

### COSMOSVLA J100028.75+023203.5

As mentioned in the previous section, this source (which seems to be a single galaxy) has a spectroscopic redshift of 4.76 (cite: 2018ApJ...858...77H), however, inspection of the DEIMOS spectrum does not reveal a secure emission line (i.e. the Ly-$\alpha$ line, according to the authors). No further spectroscopic data are available in the literature. Our own photometric SED fitting analysis suggests a redshift of 3.27, which is consistent with the redshift provided by the HELP database and (cite: 2015A&A...577A..29M). When we assume this photo-$z$ to be the true redshift of this galaxy, our SED fit analysis proposes a stellar mass of $10^{10.74} \, M_{\odot}/yr$, an SFR of 2554 $M_{\odot}/yr,$ and no AGN contribution. The derived SFR from the radio emission of this galaxy (i.e. 2166 $M_{\odot}/yr$) further supports the argument that no radio emission is added by SMBH activity. This result establishes CVLA028 as the only galaxy in our sample without an indication of an AGN by the SED fit or radio excess. Although this galaxy has been observed by both *XMM-Newton* and *Chandra*, the images at all bands reveal no clear detection.

### ALESS J033211.34-275211.9

This source is recognised in the literature as an X-ray AGN with faint radio emission. Photometric analysis from various deep surveys (cite: 2020MNRAS.492.1887G) reveals a redshift of $z\sim 3.7$, while ALMA spectroscopic data (cite: 2021MNRAS.501.3926B) show two clear emission lines (namely the CO4-3 and \[CI\] lines at $\sim 98.22\, GHz$ and $\sim 104.85\, GHz$, respectively). This secures the galaxy at $z=3.694$. Assuming that this spectroscopic redshift and that a radio flux density of $0.043 \, mJy$ solely originate from star formation, the corresponding SFR is $\sim 1884 \, M_{\odot}/yr$. However, according to (cite: 2020MNRAS.492.1887G), following the SED fitting method using CIGALE, this galaxy is a type II AGN with a stellar mass of $\sim 10^{11.3}\, M_{\odot}$, an SFR of $\sim 31 \, M_{\odot}/yr$ (our CIGALE SED fitting analysis suggests a higher value of 1194 $M_{\odot}/yr$), and an AGN fraction of 72 $\%$ (our analysis proposes a lower value of 10 $\%$ ). The source detected in the HST image (see Fig. [4](#figure3)), which is rather close to the ALMA detection ($\sim 0.5 \, arcsec$), seems to cause the radio and IR emission (cite: 2011MNRAS.415.1479W). Therefore, this source could be a complex system of at least two galaxies possibly interacting, with the presence of a radio-quiet AGN and an SFG. Even though ALESS33 is not detected in any of the X-ray surveys, another source lies at a distance of $\sim 2$ arcsec (cite: 2013A&A...555A..42R) that seems to be an X-ray bright AGN with a flux of $f_{\rm 2-10keV}=6.26 \cdot 10^{-15} erg/s/cm^2$ and no counterparts. This X-ray source was spectroscopically identified by (cite: 2013A&A...555A..42R) at $z=3.74 \pm 0.06$, meaning that it could be part of a merging system along with the sub-millimetre and radio galaxy identified with the source ALESS33.

### \[DSS2017\] 554

This source is present in the VIMOS spectroscopic survey presented by (cite: 2017ApJ...840...78D) with a spectroscopic redshift of 3.1988, which was used in this work as a fixed value for the subsequent SED fitting analysis. This galaxy is placed at the outskirts of the ECD-S field, meaning that it was not selected in the photometric analysis by (cite: 2020MNRAS.492.1887G). Inspection of the VST Optical Imaging of the CDFS and ES1 (cite: 2016heas.confE..26V) data for this source in bands r, g, and i (see the bottom row of Fig. [4](#figure3)) suggests the possibility of multiple components. These observations might signify a merging or interacting system. The predicted SFR derived solely from the radio emission is 1520 $M_{\odot}/yr$, while our SED fitting analysis suggests a value of 1162 $M_{\odot}/yr$ and an AGN contribution of $20\%$ . No clear detection has been reported regarding the possible X-ray nature of this source.

# Discussion

![]({help_result}.png)

We have examined a sample of eight high-redshift dusty galaxies with an AGN component (3 \< $z_{\rm spec,phot}$ \< 4). The selection process involved using the 1.4 GHz VLA radio catalogues from the COSMOS and ECDF-S fields in combination with the far-IR peak criterion ($f_{350 \rm \mu m}/f_{250 \rm \mu m}>1$) using the HerMES survey. Moreover, a compact morphology was considered as an additional criterion. In the following paragraphs, we assess the efficacy of these criteria in selecting these sources. Furthermore, we provide a comparison between the derived properties of our sample with those obtained in previous studies, focusing on similar redshift ranges.

## Validity of the selection criteria

While the compactness criterion merely serves as a method for avoiding local extended galaxies, the far-IR and radio criteria have been employed extensively in the past in the study of the distant Universe. For instance, (cite: 2010A&A...518L...9A) demonstrated that the redshift of a source tends to increase for galaxies that satisfy the criteria $f_{350 \rm \mu m}/f_{250 \rm \mu m}>1$ and $f_{500 \rm \mu m}/f_{350 \rm \mu m}>1$. These results are expected, considering that the far-IR emission of an SED traces the dust content of a galaxy, and more specifically, its blackbody radiation, which is shifted to higher wavelengths with increasing redshift. However, this emission is affected by the temperature of the dust as well, which consequently introduces a degeneracy that is non-trivial to break. Another point of attention is the sensitivity of the *Herschel* surveys, which are inherently biased towards the detection of the brightest dust-rich far-IR galaxies.\
In order to evaluate this argument and selection method further, we employed the HELP catalogue, which contains far-IR observational data (i.e. 15747 *Herschel* detected galaxies) along with SED fitting results from CIGALE (cite: 2018A&A...620A..50M). The galaxies from this catalogue are presented in the left panel of Fig. [5](#criteria_test), in which the blue and orange histograms correspond to the sources that follow the criterion $f_{350 \rm \mu m}/f_{250 \rm \mu m}<1$ and $f_{350 \rm \mu m}/f_{250 \rm \mu m}>1$, respectively. As anticipated, galaxies that adhere to the far-IR criterion are situated at higher redshifts on average. Interestingly, based on the CIGALE fits, a higher percentage (i.e. $\sim 45 \%$) of the galaxies that follow the $f_{350 \rm \mu m}/f_{250 \rm \mu m}\geq 1$ criterion exhibit SFRs of $SFR>10^2 \, M_{\odot}/yr$. In contrast, for the rest of the sources, a smaller percentage ($\sim 22 \%$) demonstrates high SFR values like this.\
A similar exercise was repeated for the radio criterion by estimating the AGN fraction and dust mass, derived from the CIGALE fits, for each galaxy. Because the HELP catalogues do not consider the radio emission in their fits, we cross-matched this catalogue with Cosmos2015, which includes the 1.4 GHz VLA data. The results of this analysis are displayed in the right panel of Fig. [5](#criteria_test), which shows histograms of the dust mass. The shape and mean values of these histograms indicate that the radio selection criterion does not guarantee the preferential selection of highly dusty SFGs. However, upon examining galaxies at redshifts above 3, it becomes evident that the radio selection method identifies a higher proportion of sources (i.e. $\sim 22 \pm 9 \%$) with a substantial AGN fraction (i.e. $AGN_{\rm frac}>40 \%$) compared to cases without detected radio emission ($\sim 15 \pm 4\%$).\
While this percentage difference may not be statistically significant, the combination of the two far-IR and radio selection methods still provides motivation for their application in identifying high-redshift SFGs with an AGN component. The detailed analysis of the eight sources in this sample has reinforced these findings and encourages their application in large-scale surveys, such as EMU.

## Comparison with previous work

Overall, our sample has a mean redshift of $<z_{\rm}>=3.37 \pm 0.16$, an average stellar mass of $<log(M_{\rm \star}/M_{\odot})>= 11.27 \pm 0.47$, $<L_{\rm IR,42-122\mu m}>=2.1 \pm 0.67 \cdot 10^{39} \, W$ (total IR luminosity of $<L_{\rm IR,8-1000\mu m}>=3.9 \pm 0.84 \cdot 10^{39} \, W \sim 10^{13}\, L_{\odot}$), $<L_{1.4GHz}>=5.77\pm 1.9 \cdot  10^{24} \,W/Hz,$ and a mean star formation rate (derived from the $42-122 \, \mu m$ rest-frame IR luminosity of each source) of $<SFR_{\rm IR}> 1213 \pm 567\, M_{\odot}/yr$. This average SFR is consistent with previous results that reported an increasing SFR at higher redshift. For instance, (cite: 2016MNRAS.461.1100R) and (cite: 2022A&A...668A..54G) showed that *Herschel*-detected samples of hyper-luminous infrared galaxies (HLIRGs; $L \sim 10^{12}-10^{13}\, L_{\odot}$) at $z>3$ have SFR values ranging between $\sim 1000-10000 \, M_{\odot}/yr$. Therefore, the inclusion of the 500 $\mu m$ emission in our selection criteria naturally provides us with the high bright tail of the SFR distribution at these redshifts. Similarly, (cite: 2019A&A...624A..98W) reported that the selection of *Herschel* galaxies above $z>3$ revealed dusty SFR galaxies with infrared luminosities of $\sim 10^{12}-10^{13} \, L_{\odot}$, similar to the derived values of our sample.\
Furthermore, for 87.5 $\%$ of the sources in our sample (seven out of eight), an AGN is indicated either by the radio excess or by the mid-IR signature obtained from the best SED fit. Although the morphology of these sources still remains uncertain, five out of eight (63 $\%$) might consist of multiple galaxies, with significant levels of both SF and AGN activity. In comparison, (cite: 2021A&A...654A.117G) and (cite: 2021A&A...648A...8W), who analysed a sample of HLIRGs selected using data from *Herschel* and the Deep Fields of the LOFAR Two-metre Sky Survey (cite: 2017A&A...598A.104S). described an AGN contamination of 34-64 $\%$ (using six different models to fit the AGN component) for galaxies at the redshift range $3<z<4$. These values, although model dependent, seem to be lower than the AGN contribution of our sample, which can be attributed to the fact that the LOTSS survey reaches sensitivities of 20-30 $\mu Jy/beam$ at 150 MHz. When we assume a typical radio synchrotron slope, this value translates into a lower flux density value at 1.4 GHz than the COSMOS-VLA sensitivity (i.e. 7 $\mu Jy/beam$). Therefore, it seems that by selecting radio sources from a deeper radio survey, the authors revealed a population of SF galaxies that receive contributions from AGN less frequently. However, it is important to emphasise that a comparison of our results with studies involving larger sample sizes should be approached with caution, considering the limited statistics that our data provides.\

![]({last_plot}.png)

Additionally, (cite: 2022ApJ...927..204E) reported a negligible percentage of AGN for the entire sample ($0<z<6$), which was selected using deep radio 1.4 GHz observations from the GOODS-N field (sensitivity of 2.2 $\mu Jy$). This can be perceived with the parameter $\rm q_{TIR}=log(L_{IR}/3.75 \cdot 10^{12})-logL_{1.4GHz}$, which is commonly used as an indicator of the presence of AGN contribution to the radio emission. Figure [6](#last_figure) depicts the $q_{TIR}$ values for our sample and those of (cite: 2022ApJ...927..204E), demonstrating the AGN contamination in the radio emission in most of our galaxies. In more detail, 62.5 $\%$ of the sources in our sample have lower values of $q_{\rm TIR}$ than the grey region of the plot (which denotes the average redshift-dependent $q_{\rm TIR}$). These statistics do not fully match the number of 87.5 $\%$ of AGN contamination that was derived from the SED fitting and described earlier in the text. However, this discrepancy might originate from the low AGN contribution and uncertainties in the measurements of the radio and infrared fluxes of the SED of some galaxies. In contrast, the sample by (cite: 2022ApJ...927..204E) for the redshift bin of $3<z<4$ indicates an AGN contamination of 37.5 $\%$ . This difference can be attributed to the fact that in their selection criteria, they did not require the far-IR emission (or better, far-IR peak spectrum) that we employed. As a result, only 38.4 $\%$ of their total sample has a 500 $\mu m$ *Herschel* detection.\
Another comparison can be conducted with the $q_{TIR}$ relation derived by (cite: 2021A&A...647A.123D) and presents a mass-dependent and almost redshift-independent equation (i.e. $q_{TIR}(M_{\star},z)=(2.646\pm 0.024)(1+z)^{-0.023\pm0.008}-(logM_{\star}/M_{\odot}-10)(0.148\pm0.013)$). According to this relation, all of the galaxies in our sample satisfy the criterion, placing them below the mean of the SFR population. However, none of the sources in our sample follows the relation $log(L_{1.4GHz}/SFR_{IR})=21.984 \times (1+z)^{0.013}$ that was derived earlier by (cite: 2017A&A...602A...3D) and corresponds to the $3 \sigma$ deviation from the peak distribution of the ratio of $L_{\rm 1.4 GHz}$ and $SFR_{\rm IR}$ as a function of redshift.\
In the same manner, (cite: 2017A&A...602A...5N), which selected sources from the VLA 3GHz survey without a far-IR emission requirement, similarly presented the trend of a lower contamination of AGN (23 $\%$ and 47 $\%$ of the total sample and $3<z<4$ redshift bin, respectively) than in our sample. This comparison favours the inclusion of the criterion of a far-IR rising spectrum to the radio emission when AGN at high redshifts are to be identified and studied. In contrast, an interesting comparison can be performed with studies such as that by (cite: 2015MNRAS.453.1079B), in which the authors presented a sample with galactic properties similar to those of our galaxies. This sample was derived from the radio 1.4 GHz ECDF-S catalogues (6 $\mu Jy$ sensitivity) with the addition of the *Herschel* detection in all sources at the redshift bin of interest (i.e. $z=3-4$). Fifteen of the 28 galaxies presented in this redshift range were categorised as radio-quiet (RQ) AGN while one as a radio-loud (RL) AGN, totalling 16 galaxies, or an AGN contamination of 73 $\%$ . This value is close to the value derived from our sample, which further supports the necessity of including the far-IR criterion to detect high-$z$ AGN. Additionally, the right panel of Fig. [6](#last_figure) shows that our galaxies fall in the RQ region of their work, even though our estimates indicate that at least two of our sources should have a significant AGN contribution.\
In this sense, our selection method might provide an increased probability for the detection of dusty galaxies at high-$z$ that present high SFRs with an additional AGN component, with weak radio emission, as part of a merging system. Additionally, our galaxies seem to be a more extreme group of interacting systems, having brighter IR and radio luminosities as well as stellar masses and SFRs as compared, for instance, to the work by (cite: 2021ApJ...909...23T). This outcome might originate from the fact that their sample, once again, did not require a far-IR *Herschel* detection and was originally derived from the 3 GHz - COSMOS survey, which has a higher detection limit than the VLA-1.4 GHz-COSMOS survey we employed. Nevertheless, (cite: 2017A&A...602A...5N) also explored the same field at 3 GHz and reached the same flux density sensitivity (rms of 2.3 $\mu Jy$), from which they achieved more AGN detections. The main difference lies in their selection criteria, with the latter work requiring an optical/near-IR counterpart, while (cite: 2021ApJ...909...23T) excluded these sources. The selection of radio sources with a far-IR peak spectrum and an optical counterpart might therefore reveal merging systems that at high $z$, present high SFRs ($\sim 10^3 \, M_{\odot}/yr$) and an AGN counterpart in most cases.\
Nevertheless, selecting galaxies that are considered as extreme in terms of mass and luminosity will naturally limit the study to a rare sample, hence to a reduced number of selected sources. This infrequency, along with the complexity of the adopted selection method, will unavoidably provide a less accurate estimation of the SFRD at $z>3$, which can be only considered as a lower limit (cite: 1980ApJ...235..694A), and for our study, this is equal to $SFRD>8 \cdot 10^{-3}\, M_{\odot}/yr/Mpc^3$. However, these selection criteria might be quite powerful in the aforementioned identification and in studying the interplay between AGN and SF activity at high redshift, especially with their application to the upcoming next-generation radio surveys (e.g. the EMU survey) and current/future observational data from mm facilities (cite: 2023arXiv230507054B).

# Conclusions

In this work, we present the exploration of a sample of a high-redshift ($3<z<4$) radio galaxy population that was selected with the criterion of a rising far-IR spectrum (i.e. $f_{350\mu m}>f_{250\mu m}$) along with the detection of non-extended (\<10 arcsec) radio emission at 1.4 GHz. The aim behind this selection method was to investigate the potential of combining these two criteria in identifying high-redshift dusty SFGs that are contaminated by an AGN and might be ‘hidden’ by other selection methods. A population like this, due to its extremity and low occurrence, might not contribute significantly to the SFRD of the Universe, but it can provide us with further insight into the interplay between SMBHs and SF activity at high $z$.

In order to explore the morphology of our sample and its physical characteristics in depth, we took advantage of the multi-wavelength deep data available in the literature from the COSMOS and ECDF-S fields. These data sets enabled us to identify that five out of eight galaxies in our sample might consist of more than one galaxy with possible interaction/merging. It has to be noted that the low angular extent of these galaxies did not permit confirmation of this statement due to the spatial resolution of the current instrumentation. Nevertheless, future observations with telescopes such as the *James Webb* Space Telescope (*JWST*) may provide further insights into this argument. Furthermore, we determined the presence of an AGN component in seven out of eight of these sources, which in most cases represents a weak radio emission, identifying these sources as radio-quiet AGN. An additional highly star-forming component seems to be present in all cases, with a typical SFR of $\sim 10^3 \, M_{\odot}/yr$.

We have demonstrated that the combination of the far-IR and radio emission criteria is highly efficient in selecting merging systems at $3<z<4$, typically with the presence of a radio-quiet AGN and a highly SFG. With upcoming wide radio surveys (e.g. the Evolutionary Map of the Universe, EMU) and next-generation telescopes such as the SKA, these results motivate further exploration of alternative selection methods. In order to advance the study of systems similar to those in our sample, particularly during the epoch of reionisation (EoR), sources with a mm rise in flux in combination with deep radio surveys might further be studued. A possible rising mm spectrum profile, which could be explored for faint individual sources using interferometric facilities (e.g. ALMA and NOEMA) and single-dish instruments (e.g. the NIKA2 camera of the IRAM 30m antenna, or the ToLTEC of the Large Millimeter Telescope) targeting a brighter population from larger surveys could assist in the identification of the redshifted dust component of SFGs at $z>6$. Similarly, the morphology of these galaxies could be further understood with infrared facilities, including the *JWST*.

# Acknowledgements

This work was supported by Fundação para a Ciência e a Tecnologia (FCT) through the research grants PTDC/FIS-AST/29245/2017, 1220UID/FIS/04434/2019, UIDB/04434/2020, and UIDP/04434/2020. C.P. acknowledges support from DL 57/2016 (P2460) from the ‘Departamento de Física, Faculdade de Ciências da Universidade de Lisboa’. This paper makes use of ALMA data. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan); together with NRC (Canada), MOST, and ASIAA (Taiwan); and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This research made extensive use of core PYTHON packages for Astronomy as well as TOPCAT. We thank the anonymous referee for all the valuable comments, which improved the quality of the paper.

102 natexlab

(ref: 2010A&A...518L...9A) Amblard, A., Cooray, A., Serra, P., et al. 2010, A&A, 518, L9

(ref: 1980ApJ...235..694A) Avni, Y. & Bahcall, J. N. 1980, ApJ, 235, 694

(ref: 2003ApJ...586..794B) Bell, E. F. 2003, ApJ, 586, 794

(ref: 2023arXiv230507054B) Bing, L., Béthermin, M., Lagache, G., et al. 2023, arXiv e-prints, arXiv:2305.07054

(ref: 2021MNRAS.501.3926B) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926

(ref: 2015MNRAS.453.1079B) Bonzini, M., Mainieri, V., Padovani, P., et al. 2015, MNRAS, 453, 1079

(ref: 2015ApJ...811..140B) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 811, 140

(ref: bc03) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Cappelluti) Cappelluti, N., Brusa, M., Hasinger, G., et al. 2009, A&A, 497, 635

(ref: 2012A&A...538A..89C) Carter, M., Lazareff, B., Maier, D., et al. 2012, A&A, 538, A89

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: 2021ApJ...923..215C) Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215

(ref: dustatt_2powerlaws) Charlot, S. & Fall, S. M. 2000, ApJ, 539, 718

(ref: 2022ApJ...929..159C) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159

(ref: 2016ITTST...6..223C) Chenu, J.-Y., Navarrini, A., Bortolotti, Y., et al. 2016, IEEE Transactions on Terahertz Science and Technology, 6, 223

(ref: sfhdelayed) Ciesla, L., Elbaz, D., & Fensch, J. 2017, A&A, 608, A41

(ref: 2016ApJ...819...62C) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62

(ref: 2012MNRAS.427..520C) Coppin, K. E. K., Danielson, A. L. R., Geach, J. E., et al. 2012, MNRAS, 427, 520

(ref: 2015ApJ...806..110D) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: dale2014) Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, ApJ, 784, 83

(ref: 2017ApJ...840...78D) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2017, ApJ, 840, 78

(ref: 2017A&A...602A...4D) Delhaize, J., Smolčić, V., Delvecchio, I., et al. 2017, A&A, 602, A4

(ref: 2021A&A...647A.123D) Delvecchio, I., Daddi, E., Sargent, M. T., et al. 2021, A&A, 647, A123

(ref: 2017A&A...602A...3D) Delvecchio, I., Smolčić, V., Zamorani, G., et al. 2017, A&A, 602, A3

(ref: 2018A&A...614A..33D) Donevski, D., Buat, V., Boone, F., et al. 2018, A&A, 614, A33

(ref: 2014ApJ...780...75D) Dowell, C. D., Conley, A., Glenn, J., et al. 2014, ApJ, 780, 75

(ref: 2019ApJ...876..110D) Duncan, K., Conselice, C. J., Mundy, C., et al. 2019, ApJ, 876, 110

(ref: 2017MNRAS.466..861D) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: 2009ApJ..184..158E) Elvis, M., Civano, F., Vignali, C., et al. 2009, ApJ, 184, 158

(ref: 2022ApJ...927..204E) Enia, A., Talia, M., Pozzi, F., et al. 2022, ApJ, 927, 204

(ref: 2020ApJS..247...61F) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: fritz2006) Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, MNRAS, 366, 767

(ref: 2021A&A...654A.117G) Gao, F., Wang, L., Efstathiou, A., et al. 2021, A&A, 654, A117

(ref: 2022A&A...668A..54G) Gao, F., Wang, L., Ramos Padilla, A. F., et al. 2022, A&A, 668, A54

(ref: 2010A&A...518L...3G) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3

(ref: 2020A&A...643A...8G) Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, A&A, 643, A8

(ref: 2013MNRAS.432...23G) Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, MNRAS, 432, 23

(ref: 2020MNRAS.492.1887G) Guo, X., Gu, Q., Ding, N., Contini, E., & Chen, Y. 2020, MNRAS, 492, 1887

(ref: 2023ApJS..265....5H) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5

(ref: 2018ApJ...858...77H) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77

(ref: 2013MNRAS.430.2513H) Holland, W. S., Bintley, D., Chapin, E. L., et al. 2013, MNRAS, 430, 2513

(ref: lyc_absorption) Inoue, A. K. 2011, MNRAS, 415, 2920

(ref: 2018ApJ...854...73I) Ishigaki, M., Kawamata, R., Ouchi, M., et al. 2018, ApJ, 854, 73

(ref: 2012A&A...546A..84I) Iwasawa, K., Gilli, R., Vignali, C., et al. 2012, APP, 546, A84

(ref: 2009ApJ...705L.104K) Kistler, M. D., Yüksel, H., Beacom, J. F., Hopkins, A. M., & Wyithe, J. S. B. 2009, ApJL, 705, L104

(ref: 2012A&A...542L...3K) Klein, B., Hochgürtel, S., Krämer, I., et al. 2012, A&A, 542, L3

(ref: 2008stt..conf..192K) Klein, B., Krämer, I., Hochgürtel, S., et al. 2008, in Ninteenth International Symposium on Space Terahertz Technology, ed. W. Wild, 192

(ref: 2009stt..conf..199K) Klein, B., Krämer, I., Hochgürtel, S., et al. 2009, in Twentieth International Symposium on Space Terahertz Technology, ed. E. Bryerton, A. Kerr, & A. Lichtenberger, 199

(ref: 2018IAUS..333..228L) Lagache, G. 2018, in Peering towards Cosmic Dawn, ed. V. Jelić & T. van der Hulst, Vol. 333, 228–233

(ref: Laigle16) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJ, 224, 24

(ref: 2017A&A...602A.123L) Lanzuisi, G., Delvecchio, I., Berta, S., et al. 2017, A&A, 602, A123

(ref: 2005ApJS..161...21L) Lehmer, B. D., Brandt, W. N., Alexander, D. M., et al. 2005, APJS, 161, 21

(ref: 2017ApJ..228....2L) Luo, B., Brandt, W. N., Xue, Y. Q., et al. 2017, ApJ, 228, 2

(ref: 2017ApJ...840...39M) Madau, P. & Fragos, T. 2017, ApJ, 840, 39

(ref: 2019ApJ...877...45M) Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877, 45

(ref: 2022MNRAS.509.4291M) Malefahlo, E. D., Jarvis, M. J., Santos, M. G., et al. 2022, MNRAS, 509, 4291

(ref: 2018A&A...620A..50M) Małek, K., Buat, V., Roehlly, Y., et al. 2018, A&A, 620, A50

(ref: 2016ApJ...817...34M) Marchesi, S., Civano, F., Elvis, M., et al. 2016, ApJ, 817, 34

(ref: 2016MNRAS.459.3812M) McLeod, D. J., McLure, R. J., & Dunlop, J. S. 2016, MNRAS, 459, 3812

(ref: redshifting) Meiksin, A. 2006, MNRAS, 365, 807

(ref: 2015A&A...577A..29M) Miettinen, O., Smolčić, V., Novak, M., et al. 2015, A&A, 577, A29

(ref: 2013ApJS..205...13M) Miller, N. A., Bonzini, M., Fomalont, E. B., et al. 2013, APJS, 205, 13

(ref: 2013ApJS..206....8M) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJS, 206, 8

(ref: 2023arXiv230112825N) Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, arXiv e-prints, arXiv:2301.12825

(ref: 2010A&A...518L...5N) Nguyen, H. T., Schulz, B., Levenson, L., et al. 2010, A&A, 518, L5

(ref: cigale1) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793

(ref: norris) Norris, R. P. 2009, in Panoramic Radio Astronomy: Wide-field 1-2 GHz Research on Galaxy Evolution, 33

(ref: 2021PASA...38...46N) Norris, R. P., Marvil, J., Collier, J. D., et al. 2021, PASA, 38, e046

(ref: 2017A&A...602A...5N) Novak, M., Smolčić, V., Delhaize, J., et al. 2017, A&A, 602, A5

(ref: 2018ApJ...855..105O) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018, ApJ, 855, 105

(ref: hermes) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614

(ref: 2021MNRAS.507.3998P) Pantoni, L., Massardi, M., Lapi, A., et al. 2021, MNRAS, 507, 3998

(ref: 2014A&A...563A..54P) Pâris, I., Petitjean, P., Aubourg, É., et al. 2014, AAP, 563, A54

(ref: 2023ApJ...946L..16P) Pérez-González, P. G., Barro, G., Annunziatella, M., et al. 2023, ApJL, 946, L16

(ref: 2010A&A...518L...1P) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1

(ref: 2018MNRAS.473.4077P) Pillepich, A., Springel, V., Nelson, D., et al. 2018, MNRAS, 473, 4077

(ref: 2010A&A...518L...2P) Poglitsch, A., Waelkens, C., Geis, N., et al. 2010, A&A, 518, L2

(ref: 2013A&A...555A..42R) Ranalli, P., Comastri, A., Vignali, C., et al. 2013, A&A, 555, A42

(ref: 2016MNRAS.455.1553R) Reid, B., Ho, S., Padmanabhan, N., et al. 2016, MNRAS, 455, 1553

(ref: 2023MNRAS.518L..19R) Rodighiero, G., Bisigello, L., Iani, E., et al. 2023, MNRAS, 518, L19

(ref: 2021MNRAS.505.3192R) Rodriguez, F., Montero-Dorta, A. D., Angulo, R. E., Artale, M. C., & Merchán, M. 2021, MNRAS, 505, 3192

(ref: 2016MNRAS.461.1100R) Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100

(ref: 2010ApJS..188..384S) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, APJS, 188, 384

(ref: cosmos_paper) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJ, 172, 1

(ref: cigale2) Serra, P., Amblard, A., Temi, P., et al. 2011, ApJ, 740, 22

(ref: 2017A&A...598A.104S) Shimwell, T. W., Röttgering, H. J. A., Best, P. N., et al. 2017, A&A, 598, A104

(ref: 2021MNRAS.507..129S) Shirley, R., Duncan, K., Campos Varillas, M. C., et al. 2021, MNRAS, 507, 129

(ref: smolcic17) Smolčić, V., Novak, M., Delvecchio, I., et al. 2017, A&A, 602, A6

(ref: 2015ApJ...815..129S) Suh, H., Hasinger, G., Steinhardt, C., Silverman, J. D., & Schramm, M. 2015, ApJ, 815, 129

(ref: 2020ARA&A..58..157T) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: 2021ApJ...909...23T) Talia, M., Cimatti, A., Giulietti, M., et al. 2021, ApJ, 909, 23

(ref: 2016heas.confE..26V) Vaccari, M., Covone, G., Radovich, M., et al. 2016, in The 4th Annual Conference on High Energy Astrophysics in Southern Africa (HEASA 2016), 26

(ref: 2013ApJ...779...32V) Viero, M. P., Moncelsi, L., Quadri, R. F., et al. 2013, ApJ, 779, 32

(ref: 2021A&A...648A...8W) Wang, L., Gao, F., Best, P. N., et al. 2021, A&A, 648, A8

(ref: 2019A&A...624A..98W) Wang, L., Pearson, W. J., Cowley, W., et al. 2019, A&A, 624, A98

(ref: 2011MNRAS.415.1479W) Wardlow, J. L., Smail, I., Coppin, K. E. K., et al. 2011, MNRAS, 415, 1479

(ref: 2022ApJS..258...11W) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11

(ref: 2000A&AS..143....9W) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, A&As, 143, 9

(ref: 2019clrp.2020...19W) Wilson, C., Dong, R., di Francesco, J., et al. 2019, in Canadian Long Range Plan for Astronony and Astrophysics White Papers, Vol. 2020, 19

(ref: 2019ApJ...878...73Y) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73

(ref: 2022MNRAS.516.5471Y) Yan, H., Ling, C., & Ma, Z. 2022, MNRAS, 516, 5471

(ref: 2008ApJ...683L...5Y) Yüksel, H., Kistler, M. D., Beacom, J. F., & Hopkins, A. M. 2008, ApJL, 683, L5

# Comparison of the retrieved $z$ with photometric catalogues

In this appendix, we present a comparison between the redshift values estimated by various photometric catalogues and our analysis, as described above. In more detail, the catalogues consist of the Cosmos2015 (cite: Laigle16), the Cosmos2020 (cite: 2022ApJS..258...11W) and the HELP catalogues (cite: 2021MNRAS.507..129S). The redshift values derived from these catalogues are compared with the values that our team acquired from the literature and from the IRAM/ALMA observations of the aforementioned two targets (i.e. CVLA958 and CVLA100; see Sect. [3](#results)). For the cross match between catalogues, a radius of 1 arcsec was employed in order to ensure that each source from the catalogues corresponded to the correct source from our sample. The results of these comparisons are presented in Fig. [7](#z_comparison).

In our findings, certain sources exhibit lower redshift values in the catalogues than in the present study. These differences can be attributed to the low S/N of the photometric points that were used in the SED fitting. Furthermore, the authors of these catalogues may not have individually examined each source due to the extensive volume of data. For example, the source with coordinates (Ra, Dec)=(150.02005417, 2.51254722) is depicted in the Cosmos2020 comparison plots (see Fig. [7](#z_comparison)) with a redshift of $z=2.48$, derived from the EAZY SED fit ($\chi^2$ of $\sim 15$). However, our work adopts a redshift value of 3.46 obtained from the Lephare SED fit solution for the same source. This choice was made due to the lower $\chi^2$ values obtained from both the literature Lephare analysis ($\chi^2 = 3.76$) and our own CIGALE fits ($\chi^2 = 2.24$).

Additionally, this figure shows that according to Cosmos2015, two galaxies that were identified by our search as $z<3$ sources have a higher photometric redshift value. In more detail, the sources are identified as UVISTADR1 J100131.33+020325.2 and UVISTADR1 J100114.75+023516.3 and have a $z_{\rm phot,cosmos2015}$ of 3.152 and 3.007, respectively. However, the more detailed photometric analysis by (cite: 2013ApJS..206....8M) proposed lower values for both sources of $\sim 1.8$ and $\sim 2.7$, respectively. Similarly, for the cosmos2020-Farmer method, a source named UVISTADR1 J095834.49+015504.9 was estimated to be at $z_{\rm phot,cosmos2020,EAZY}\sim 3.1$, however, (cite: 2013ApJS..206....8M) reported a lower value of $\sim 2.5$. The latter redshift results can be further supported by the redshift estimate by Lephare cosmos2020 of $z_{\rm phot,cosmos2020,Lephare}\sim 2.2$. These discrepancies between various photometric catalogues can mainly be attributed to the faint nature of these sources and to the subsequent low fit quality of their SED. Finally, according to the HELP catalogue, no further source could be added to our $z>3$ sample.

![image]({plot_cosmos2015}.png) ![image]({plot_cosmos2022_classic}.png)

![image]({plot_cosmos2022_farmer}.png) ![image]({plot_help}.png)

# Spectroscopic follow-up of CVLA958 and CVLA100

Because of the uncertainty of the high-redshift nature of CVLA958 and CVLA100, these sources were originally included in a follow-up spectroscopic study by our team with the aim to understand their nature and potentially employ this knowledge to detect galaxies at higher redshifts. In this appendix, we present the retrieved spectroscopic data for these two galaxies, bearing in mind the redshift solution of $z \sim 3$ that the current photometric analysis indicated. The original idea of the spectra acquired with the Institute Radio Astronomie Millimétrique (IRAM) 30m antenna and the ALMA telescopes was the detection of two possible CO emission lines that would constrain the redshift of each galaxy.

## IRAM observations

The IRAM[^5] institute is composed of two facilities, namely the interferometer NOrthern Extended Millimeter Array (cite: 2016ITTST...6..223C) and a single-dish telescope with a diameter of 30m, located in the Sierra Nevada, Spain. The adopted strategy to retrieve the millimetre spectrum of our galaxies was to scan the 3 mm band with the spectral line receiver Eight MIxer Receiver (cite: 2012A&A...538A..89C) of the 30m antenna, along with the Fast Fourier Transform Spectrometers (cite: 2012A&A...542L...3K) and Wideband Line Multiple Autocorrelator (WILMA[^6]) backends (in parallel) at the wavelength range of 73-117 GHz (band E0/E090). Given the possible AGN nature of the targeted sources, the CO spectral line energy distribution will likely peak at mid-J transitions (e.g. for the frequency range of band E0, the CO J=4-3 line could be at $z\sim 2.7-5$ and the CO J=5-4 line at $z\sim 3.7-6.5$). The expected redshift span for this candidate is $z \geq 3$, and therefore, the 3 mm spectral range provides an excellent trade-off of weather versus line detection to search for ideally two emission lines required to determine the source redshift. Nevertheless, in the following analysis, only the data from the FTS units were investigated since they provide a higher spectral resolution than WILMA, which is necessary to resolve faint emission lines.

The project code is 227-19, and the observations were initially scheduled for 19-24 December 2019. However, considering that the weather conditions were not appropriate to observe for the full length of our original allocated time, additional observing time was provided during 21-23 March 2020, 12-14 May 2020, and finally, 14-17 July 2020. Out of a total of 103 hours provided for this source, only $\sim 8$ hours of observations generated spectra with acceptable quality to be considered in the assembly of the final spectrum. The rest of the observing time was lost due to instrumentation malfunctions and weather conditions (strong wind and high water vapour).

The final spectrum of CVLA958 was constructed using only data from the last three days of observations (i.e. 21, 22, and 23 December 2019). We further inspected the histograms of the opacity of the clouds ($\tau$), rms random noise temperature ($T_{\rm rms}$), and receiver and system temperature ($T_{\rm rec}$ and $T_{\rm sys}$, respectively) from these observations in order to exclude possible outliers in the scans. After removing these outliers and correcting for the platforming issue (cite: 2008stt..conf..192K; 2009stt..conf..199K), we generated the final spectrum for the 3 mm band, depicted in the left panel of Fig. [8](#total_spectrum_cvla958). In this plot, the total spectrum (blue line) and its filtered version for a Gaussian filter of $50 \, km/s$ (orange line) are presented, and the colours are denoted in the legend. The full applied FTS configuration is also shown, as is the location of the CO lines, accepting the recent spectroscopic redshift value of 3.1755 by (cite: 2021MNRAS.501.3926B) (dashed red lines). The figure clearly shows that no secure line can be attributed to any feature because the S/N does not permit this determination.\
The high-redshift candidate CVLA100 was also observed by our team with the IRAM 30m antenna as part of the project 198-16 and during the time period of 23-27 March 2017. In these observations, we also scanned the E0 band of EMIR (frequency range of 73–117 GHz) using the FTS200 backend. Additional time was allocated for our source, and observations were conducted remotely on $26^{\rm }$ May 2107, aiming at the 2 mm spectral window. Similarly, with the acquired spectrum of CVLA958, no secure emission line could be detected for CVLA100. In order to further test possible lines that are not apparent with visual inspection, we developed a simple convolution algorithm to search for emission from CO lines at a given redshift. Essentially, the approach of this code is to sum the observed spectra at the positions where a CO detection was expected at a given redshift, and subsequently vary the redshift in steps of 0.01. Application of this analysis, presents no emission line detection, considering that the resulting values for specific redshifts ranging from $z=0$ to $z=6$ do not deviate significantly from zero.

![image](4_nights_raw_data_E0_PlatfCorrectIRAMscript_base1_srcCVLA-958_no_setup1_1b_nobin_spectrum_3.png) ![image](cvla100_only_alma_100.png)

## ALMA observations

No emission was detected in the IRAM spectrum for CVLA100, our team decided to secure additional observing time for the same candidate using the ALMA telescope. More specifically, the source was observed with multiple tunings in bands 3 (84-116 GHz) and 4 (125-163 GHz) in various configurations (longest baselines from 300 m to 1400 m), under the project code 2017.1.01713.S. With acceptable weather conditions (water vapour of $\leq 3\, mm$ at all times; wind at $\sim 3 \, m/s$), our observations achieved a mean angular resolution of $\sim$1 arcsec and a mean continuum sensitivity of $\sim$0.2 mJy after 4.1 hours at band 3 and 1.4 hours of integration time at band 4. By analysing the spectrum, extracted using the CASA software (cite: 2022PASP..134k4501C), we detected a feature at 107.3 GHz which, considering the numerous CO emission lines, assisted in constraining the redshift of the source. One plausible solution indicates that this feature corresponds to the redshifted CO(4-3) emission line at $z=3.3$. This proposed redshift possibility closely agrees with the suggested solution of $z=3.15$ obtained from our photometric analysis and the referenced literature catalogues (i.e. HELP, Cosmos2015, and cosmos2020).

[^1]: samarant@iram.es

[^2]: <https://ned.ipac.caltech.edu>

[^3]: [https://irsa.ipac.caltech.edu](https://irsa.ipac.caltech.edu/cgi-bin/Gator/nph-scan?projshort=COSMOS)

[^4]: $S_{\nu} \propto \nu^{-\alpha}$, where $S_{\nu}$ corresponds to the flux density, $\nu$ is the frequency, and $\alpha$ is the radio spectral index, which is 0.8 for pure radio synchrotron emission.

[^5]: <https://www.iram-institute.org>

[^6]: <https://www.iram.fr/IRAMFR/TA/backend/veleta/wilma/index.htm>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "sfhdelayed, bc03 (Chabrier IMF), dustatt_2powerlaws, lyc_absorption, dl2014, fritz2006 AGN model, delta_z = 0.1 for photo-z fitting",
  "failed_quote": "| Stellar emission | bc03 | (cite: bc03) | | | | | imf = 1(Chabrier) |"
 }
]
```
