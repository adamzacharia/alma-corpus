# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026A%26A...709A.173M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMAGAL VIII. Early phases of triggered star formation in source AG286.0716$-$1.8229

Several theoretical and observational studies have shown that new waves of triggered star-formation can be induced by the feedback from newly formed massive protostars, due to the expansion of H ii regions.

We used the millimeter dust continuum data of the ALMAGAL survey and the Anderson et al. 2014 catalog of H ii regions to search for signatures of possible triggered star formation at its onset, and selected one ALMAGAL source for ALMA follow-up observations.

For this study we selected the source AG286.0716$-$1.8229, in which six cores were detected at a resolution of $\sim7600$ au, but only two at a higher resolution. The 4 cores not detected at higher resolution are prestellar core candidates. We used archival data from the SARAO Meerkat Galactic Plane Survey and Rapid Askap Continuum Survey to confirm whether an H ii region is present in the field. We observed the source with with ALMA in Band 4, covering the emission of DCO$^+$(2$-$1), N$_2$D$^+$(2$-$1), DCN (2$-$1), and CH$_3$CCH (9–8), to infer from the chemical composition and temperature estimates whether these cores are in an early phase of the star-formation process, which allows us to classify them as prestellar core. The new Band 4 continuum image revealed additional three cores outside of the ALMAGAL field of view, for a total of 9 cores in the region, 8 of which are located along an arch of radius $\sim0.75$ pc. We also used the continuum and molecular emission to estimate the mass of these cores, to determine whether they are gravitationally bound or transient objects.

We have derived a spectral index between –0.14 and –0.4, in the frequency range of 0.8–1.6 GHz for the candidateH ii region, which is consistent with optically thin free-free emission. The H ii region spatially coincides (as projected on the plane of the sky) with the position of one of the cores, which in the new ALMA Band 4 observations does not have a compact morphology. The N$_2$D$^+$and DCO$^+$emission peaks at the position of three out of four prestellar core candidates, and the overall emission in both the line and the continuum, which extends outside of the FOV of the ALMAGAL observations, reveals a clear arched shape centered at the H ii region. We were able to estimate the gas temperature of only the most evolved core, using the CH$_3$CCH emission. The resulting value of $39\pm5$ K is also an upper limit for the other cores. Using plausible temperature ranges for each core, based on the information from chemical tracers and the dust continuum, we derived mass ranges for the cores ($\sim2-16\,$M$_{\odot}$) as well as ranges for the virial parameter ($\sim0.3-5$). All the cores along the arch have virial parameters consistent with bound objects, with only one exception.

Comparing the typical separation and mass of the cores with those expected in the case of the collect and collapse scenario and with the thermal Jean length and mass, the best agreement is found with the characteristic scales in the case of triggered star formation. The same methodology can be applied to further ALMAGAL sources to identify optimal targets to study a larger sample of prestellar cores in an environment affected by the presence of an H ii region.

# Introduction

The formation of OB stars has a deep impact on the environment in which they are born, since they ionize their surrounding medium and create H ii regions. The expansion of these H ii regions could trigger a new wave of star-formation. During the expansion of the ionizing front, previously diffuse homogeneous material can be collected, compressed, and it then collapses due to gravity (cite: elmegreen1977). Alternatively, the expanding H ii regions can compress preexisting inhomogeneous materials containing dense structures, making them reach the condition for their collapse (cite: bertoldi1989), or a combination of the two effects could be at work (cite: walch2015).\
The triggering effect of H ii regions for new star-formation has been predicted by numerical simulations (cite: hosokawa2005; dale2007), and confirmed in various observational cases (cite: zavagno2006; zavagno2007; zavagno2010; deharveng2008; fontani2012; Liu2015; palmeirim2017; zhou2020; sharma2022). However, the majority of the observational studies analyzed evolved H ii regions and looked at the distribution of already formed young stellar objects (YSOs) or the CO emission (cite: elia2007VelaD; thompson2012; kendrew2012), while only a few cases analyzed young star-forming material using higher density tracers (cite: fontani2012; tackenberg2013; kendrew2016; palmeirim2017; Zhang2024ATOMS; kim2025). The details of this triggered star formation, and the possible differences between star formation triggered by the presence of an H ii regions and the scenario without feedback from already formed massive stellar objects, have not been fully explored, especially at the onset of the process. Our goal is to investigate the early stage of the process in the two scenario.\
For this reason, we used the ALMA evolutionary study of high-mass protocluster formation in the GALaxy (ALMAGAL) survey (cite: ALMAGAL1) to search for sites of the early phase of triggered star-formation. ALMAGAL observed more than 1000 high-mass clumps in different environments in our Galaxy, and at different evolutionary stages with the Atacama Large Millimeter/Submillimeter Array (ALMA) in Band 6, down to a resolution of $\sim1000\,$au (cite: ALMAGAL2; ALMAGAL3). To search for cores in the earliest evolutionary stage, we compared the continuum emission of the ALMAGAL field at the full resolution of $\sim1000\,$au[^1] and at an intermediate resolution of $\sim5000\,$au[^2] (see Section 2.1 and (cite: ALMAGAL2) for more details). Comparing the two sets of images it is possible that a compact source in the maps at $\sim 5000\,$au is not identified above the noise limits in the $\sim1000\,$au if the radial profile of the source is flat, like in the case of prestellar cores (cite: caselli2019flat). In such a case, the same flux will be spread over a larger number of smaller beams in the full resolution image, and can be undetected. This will not happen for more evolved cores that will have a peaked radial profile structure. Therefore, to search for candidate prestellar cores we looked for compact sources detected at $\sim5000\,$au, but not matched with any core at $\sim1000\,$au, which we refer to hereafter as disappearing cores. Moreover, to have good candidates for this pilot study we searched for H ii regions or candidate H ii regions in the ALMAGAL fields in the catalog of (cite: anderson2014) closer than 1 pc to one or more disappearing cores. These disappearing cores are candidates prestellar cores in regions influenced by the presence of a possible H ii region.\
Among the $\sim$1000 regions in ALMAGAL, we identified AG286.0716$-$1.8229  as a very promising region to study the presence of very early stage dense cores in the vicinity of an expanding H ii region, which has four disappearing cores as will be shown in detail in Section 3. The aim of this study is to confirm the nature of the disappearing cores as bound objects in a pristine phase of the star-formation process, and investigate the scenario of triggered star-formation in the source using new observations in ALMA Band 4 of deuterated molecular species and continuum archival data at centimeter wavelength. In fact, in the early stages of star formation in regions with temperature below 20 K and density above $\sim10^5\,$cm$^{-3}$ the deuteration process takes place (cite: caselli2012; fontanideuteration; fontani2014timescale). This process leads to a significant enhancement of the abundance of several deuterated species. Some of the species affected are DCO$^+$and N$_2$D$^+$, included in our observations. Once this scenario is tested, the method could be expanded to other regions to improve the statistics on these objects and have a base to evaluate systemic differences between the star-formation process in the presence of H ii regions and non-triggered star formation, from the time of their onset.\
In Section 2 we present the dataset of the observations; in Section 3 we analyze the continuum emission in different bands and the line emission from new ALMA Band 4 observations; in Section 4 we discuss the results; in Section 5 we discussed whether the formation of the cores analyzed is really triggered by the presence of an H ii region; in Section 6 we summarize our main results.

![image](all_continuum_images.png)\
![image](all_continuum_images_withboxesnew.png)

# Observations

+:-------------------+:----------:+:---------:+:-----:+:------:+
| name               | instrument | frequency | beam           |
+--------------------+------------+-----------+-------+--------+
|                    |            | \[GHz\]   | \["\] | \[au\] |
+--------------------+------------+-----------+-------+--------+
| ALMA Band 4        | ALMA       | 150       | 0.70  | 6000   |
+--------------------+------------+-----------+-------+--------+
| ALMAGAL 7M+TM2     | ALMA       | 219       | 0.89  | 7600   |
+--------------------+------------+-----------+-------+--------+
| ALMAGAL 7M+TM2+TM1 | ALMA       | 219       | 0.17  | 1400   |
+--------------------+------------+-----------+-------+--------+
| SMGPS              | Meerkat    | 0.9-1.6   | 8     | 70000  |
+--------------------+------------+-----------+-------+--------+
| RACS               | ASKAP      | 0.88      | 24    | 200000 |
+--------------------+------------+-----------+-------+--------+
|                    |            | 1.35-1.65 | 10    | 86000  |
+--------------------+------------+-----------+-------+--------+

Table [\[tab:listdata\]](#tab:listdata) gives a small summary of the dataset analyzed in Section 3 and described more in details in the following subsections.

## ALMA Band 4 Observations

Our new observations were carried out with ALMA the 16th of August 2024 in configuration C-4 (Project 2023.1.01386.S, PI C. Mininni). The source AG286.0716$-$1.8229 has coordinates $l=286.0716^{\circ}$ and $b=-1.8229^{\circ}$, and an heliocentric distance of 8.5 kpc (cite: ALMAGAL1). The source has been observed with elevation between $\sim45^{\circ}$ and $\sim53^{\circ}$ for a total of $\sim3.2\,$hrs on source. The sources selected for the phase and water vapor radiometer calibrations were J1032–5917 and J1019–6047.\
The continuum and cubes analyzed in this paper are the products of the standard pipeline and imaging (version 2023.1.0.124, (cite: hunter2023)) provided by ALMA using CASA version 6.5.4.9 (cite: casa2022) using a robust value of 0.5. The linear resolution of the observations is of 0.83"$\times$0.59" ($\sim6000\,$au) and the maximum recoverable scale is 7.5" ($\sim0.3$ pc), while the FOV is of 58.4". We observed the source AG286.0716$-$1.8229 in four spectral windows in Band 4, centered around the emission lines of DCO$^+$(2$-$1) (144.077 GHz), N$_2$D$^+$(2$-$1) (154.217 GHz), DCN (2$-$1) (144.828 GHz), and CH$_3$CCH 9-8 ($K=0$: 153.817 GHz). Each spectral window has a bandwidth of 117.19 MHz and a spectral resolution of 0.098 MHz ($\sim$0.2 km s$^{-1}$).

## ALMA Band 6 Observations

The observations in ALMA Band 6 are part of the ALMAGAL large program (project code: 2019.1.00195.L in Cycle 7; P.I. Molinari, Schilke, Battersby, Ho; (cite: ALMAGAL1; ALMAGAL2)) that was observed between October 2019 and July 2022. The target name in ALMA archive (internal ID) for source AG286.0716$-$1.8229  is 646390. To achieve the requested linear resolution without losing information on diffuse material at the clump scale, each target was observed with the 7-m array (hereafter 7M) and with two configurations of the main ALMA array. AG286.0716$-$1.8229  was observed in configurations C-3 (TM2) and C-6 (TM1). The ALMAGAL team developed a dedicated pipeline to obtain the final cubes, using joint deconvolution of the various configurations observed, and that includes self-calibration for the most intense sources. A detailed description of the data reduction, together with a quality assessment of the final products, is presented in (cite: ALMAGAL2). The ALMAGAL pipeline produced continuum maps and cubes obtained by the joint deconvolution of *7m* and *tm2* data only (hereafter *7m+tm2*), which reach a linear resolution of $\sim7600\,$au ($\sim0.89$"), and of all the available configurations (hereafter *7m+tm2+tm1*) that reach the maximum resolution of $\sim1400\,$au ($\sim0.17$") for source AG286.0716$-$1.8229. The resolution reached for the images and cubes of AG286.0716$-$1.8229  is worse than the typical average resolution in the ALMAGAL sample ($\sim5000$ au and $\sim1000\,$au), since this is one of the farthest sources in the sample at 8.5 kpc heliocentric distance. The diameter of the field of view (FOV) of the observations is 35.4" (down to the 30% primary beam response).\
The spectral setup of the observations covers four spectral windows in total: two spectral windows with a 1.9 GHz bandwidth and a spectral resolution of 0.98 MHz ($\sim1.3\,$km s$^{-1}$) centered at 217.8 GHz and 220.0 GHz, and two higher resolution spectral windows with a 0.47 GHz bandwidth and spectral resolution of 0.24 MHz ($\sim0.3\,$km s$^{-1}$) centered at 218.3 GHz and 220.6 GHz, respectively. The spectral frequency ranges observed include the frequency of emission of SiO $(5-4)$ transition, with rest frequency of 217.105 GHz.

![](fig2_irac_meerkat.png)

![](spectral_index_with150GHz.png)

## Archival data

We collected the continuum emission of AG286.0716$-$1.8229  in the infrared and at centimeter wavelength from surveys in the literature. We obtained the emission at 3.6 and 4.5$\,\mu$m from the Deep GLIMPSE survey observed by *Spitzer* Infrared Array Camera (IRAC) (cite: deepGlimpse) with $\sim2$" resolution. No data for the coordinates of source AG286.0716$-$1.8229  were available at 5.8 and 8.0$\,\mu$m from the NASA/IPAC Infrared Science Archive (IRSA). We recover the emission at 23 cm for this source from both the SARAO MeerKAT Galactic Plane Survey (SMGPS; (cite: goedhart2024))[^3] with an angular resolution of 8" and the Rapid ASKAP Continuum Survey (RACS; (cite: rascI; rasc0.880GHz; RASC1.3GHz; RASC1.7GHz) ) with angular resolution of 24" at 0.88 GHz and $\sim10"$ at 1.35 and 1.65 GHz.

# Analysis

## Millimeter continuum emission

In Figure [1](#fig:3continuum) we show 150 GHz continuum emission from the ALMA Band 4 data (*left*) and the 219 GHz continuum emission from the ALMAGAL *7m+tm2* and *7m+tm2+tm1* data (*center* and *right*, respectively). (cite: ALMAGAL3) and Coletta et al. in prep. used the algorithm CuTEx (cite: cutexmolinari2011; cutexsoftware) to identify the compact sources inside the ALMAGAL continuum 7M+TM2 and 7M+TM2+TM1 images. CuTEx identifies compact sources as maxima of curvature in maps by analyzing their second derivatives. This method allows an easier identification of compact sources, which stand out in the curvature images, while diffuse and background emission is strongly dampened. Once the peaks in the curvature maps are identified, they are fitted (in the original map) with 2D elliptical Gaussians plus a background that can be of first or second order polynomial[^4], in order to obtain the positions and sizes of the sources (semi-major axis $\theta_A$, semi-minor axis $\theta_B$, and position angle) and the integrated flux (background subtracted). We use the identification numbers defined by CuTEx on the ALMAGAL continuum 7M+TM2, already shown in [1](#fig:3continuum), to identify the various sources throughout this work. CuTEx identified six sources at $\sim 7600$ au resolution, but only four at $\sim 1400$ au resolution (cite: ALMAGAL3), three of which are subfragments of the source #4 in the 7600 au data. Therefore, there are four compact sources identified in the 7600 au resolution image that have no counterparts in the 1400 au resolution image in the 219 GHz continuum data. These are core #1, #2, #5, and #6. These sources are prestellar core candidates, without a centrally peaked structure yet, as it will be discussed in Sect. [4.1](#sec:radialprofile). This is supported by the fact that the integrated fluxes of cores #2,#5, and #6 are larger than or comparable to the integrated flux density of core #3 (see Table [\[tab:massvirial\]](#tab:massvirial)).\
The 150 GHz continuum data (*left panel*) shows an emission overall similar to that of the 219 GHz 7M+TM2 data. However, the emission of core #1 is not as bright as the rest of the cores and it is not compact, while from the CuTEx algorithm extraction we performed on this continuum image the compact core #5 is resolved into two cores, due to the better angular resolution. Moreover, this new dataset has a larger FOV than the ALMAGAL data, which reveals the presence of further emission. Considering this newly observed area it is evident that the compact cores are located on an arch shaped region centered close to the position of core #1. The radius of this arch is $\sim$18.0" which corresponds to $\sim$0.75 pc at the distance of AG286.0716$-$1.8229. There are three new cores identified along the arch outside the ALMAGAL FOV, which are been labeled as core #7, #8, and #9, respectively (see Fig. [1](#fig:3continuum)). In Table [\[tab:massvirial\]](#tab:massvirial) we report the coordinates, the integrated flux densities of the cores, and their mean radius r, as derived from CuTEx ($r=d \tan\theta$, where $\theta=\sqrt{\theta_A \theta_B}$ and $d=8.5\,$kpc is the source distance) of cores from #2 to #9.\
In the last column of Table [\[tab:massvirial\]](#tab:massvirial) we report the average column density of each core. All the cores show similar values, therefore the "disappearing" nature of some of them is not related to their average density. Moreover, this ensures that the molecular emission that we will discuss in Sect. 3.3 is not biased (e.g. the density of the core is not above the critical density of the line observed) by the different density in different cores.

![image](Mom0_DCO+_N2D+_DCN_images.png)\
![image](Mom0_DCO+_N2D+_DCN_boxes.png)

+:--------------:+:--------------:+:--------------:+:--------------:+:---------------:+:--------------:+:---------------:+:---------------:+:-----------------------:+:--------------------:+
|                |                |                |                |                 |                |                 |                 |                         |                      |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| ID             | l              | b              | $F_{\rm{INT}}$ | $r$             | $T$            | $M$             | $FWHM$          | $\alpha_{\mathrm{vir}}$ | $n$(H$_2$)           |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
|                | \[$^{\circ}$\] | \[$^{\circ}$\] | \[mJy\]        | \[10$^{3}$ AU\] | \[K\]          | \[M$_{\odot}$\] | \[km s$^{-1}$\] |                         | \[10$^6$ cm$^{-3}$\] |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| *cores identified in ALMAGAL 7MTM2 continuum: disappearing*                                                                                                                               |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 2              | 286.07362      | -1.821405      | 1.8            | 4.7             | 10-20          | 3.1-8.3         | 1.2             | 0.8-2.2                 | 0.9-2.4              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 5              | 286.06904      | -1.821022      | 3.6            | 5.9             | 10-20          | 6.2-16.6        | 0.97            | 0.3-0.9                 | 0.9-2.4              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 6              | 286.06992      | -1.820381      | 2.6            | 4.7             | 10-20          | 4.5-12.2        | 1.1             | 0.5-1.3                 | 1.3-3.5              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| *cores identified in ALMAGAL 7MTM2 continuum: not disappearing*                                                                                                                           |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 3              | 286.07318      | -1.821122      | 1.9            | 3.8             | 20-30          | 1.9-3.2         | 1.2             | 1.7-2.8                 | 1.0-1.8              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 4              | 286.07154      | -1.820783      | 10.6           | 4.9             | $39\pm5$       | 8.2             | 1.8             | 2.0                     | 2.1                  |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| *new cores identified in ALMA Band 4 continuum*                                                                                                                                           |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 7              | 286.06613      | -1.823351      | 0.48           | 3.5             | 20-30          | 1.9-3.1         | 1.7             | 3.3-5.3                 | 1.4-2.2              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 8              | 286.06620      | -1.823540      | 1.5            | 5.0             | 20-30          | 6.1-9.7         | 1.7             | 1.5-2.4                 | 1.5-2.4              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+
| 9              | 286.06559      | -1.825501      | 0.9            | 3.8             | 20-30          | 3.6-5.8         | 0.7             | 0.3-0.5                 | 3.2-2.0              |
+----------------+----------------+----------------+----------------+-----------------+----------------+-----------------+-----------------+-------------------------+----------------------+

**Notes:** the integrated flux density $F_{\rm{INT}}$ for cores #2 to #6 is at 219 GHz, while for the remaining cores is at 150 GHz. The FWHM is the mean value of those of detected species on the cores.

## Centimeter continuum emission

In Fig. [2](#allbands) we show the continuum emission of this region at 23 cm from SMGPS, with superimposed the contours of continuum emission from ALMA observations at 150 GHz. The center of the arched emission is consistent with the position of bright radio emission. The position of the peak of the 23 cm emission matches within 3" with the position of a candidate H ii region from the catalog of (cite: anderson2014), which used the morphology seen in the emission in WISE bands to identify H ii regions, together with radio emission and line emission. The source was classified as *candidate* due to a lack of data from radio recombination lines (RRL) to confirm the presence of ionized material.\
We collected all the available archival data in the literature to build the most complete radio spectral energy distribution (SED) of this source, that encompass core #1 identified in the continuum images of ALMA Band 4 and 6. Using the data-cube with the emission in different sub-bands for SMGPS, and the emission at the three wavelengths of RACS we were able to construct the SED between 0.88 GHz and 1.65 GHz. The source is point-like, as a preliminary 2D Gaussian fit performed in Cube Analysis and Rendering Tool for Astronomy (CARTA, (cite: CARTA)) matches the angular resolution of the data. We then perform aperture photometry using a circular aperture of 2 times the resolution of the data ($\sim$20"). The SED in the available range shows a flat profile (see Fig. [3](#spectral_index)). The spectral index $\alpha$ (assuming $S_{\nu}\propto\nu^{\alpha}$) from the fit of the data is $-0.4\pm0.4$, mostly driven by the point at 1.65 GHz from SMGPS, while the flux density from RACS data at the same frequency is consistent with a $-0.1\pm0.4$ spectral index. The spectral index values and their error have been derived with a Monte Carlo Markov Chain linear fit to the points between 0.8 GHz and 1.6 GHz, using 100 walkers and 500 steps. Both values of $\alpha$ are consistent with optically thin free-free emission, as seen from $\alpha$ values derived in the same range from known H ii regions using SMGPS from (cite: goedhart2024). We included in the SED also the flux densities inside the region of emission at 23 cm in the two ALMA Bands that are dominated by the dust emission, which correspond to what we previously defined as core #1. We calculated the spectral index between the point at 150 GHz and at 220 GHz, first removing the contribution from free-free emission extrapolated from the two possible fits of the first part of the SED. The range of the spectral index is then between 2.7 (assuming $\alpha =$-$0.43$ for the free-free emission) and 4.2 (assuming $\alpha =$-$0.14$ for the free-free emission), which corresponds to the emission of dust along the same line-of-sight of the emission of the H ii region. The value of the exponent of the power-law of dust emissivity $\beta$ (with $\beta=\alpha-2$ in the Rayleigh-Jeans regime) for this source is in the range of 0.7-2.2. These values are consistent with typical values found in the ISM (cite: Planck_abergel2014). The commonly used value of $\beta\sim1.7-2$ corresponds to grain distribution with sizes between 100  Å and 0.3 $\mu$m (cite: Weingartner2001), while larger grains result in lower values of $\beta$, reaching values below 1 for grain sizes above 1 mm (cite: cacciapuoti2023). However, given the more diffuse morphology of core #1 from its 150 GHz emission, we do not consider it to be a compact core and we exclude it from further analysis to determine whether this is a prestellar core.\
The number of Lyman continuum photons emitted by the ionizing source and that generate the H ii region can be calculated using the radio flux density, following the relation given by (cite: matsakis1976): $$\begin{equation}
    N_{Ly } = 7.5\times10^{46}\,\Biggl(\frac{S_{\nu}}{\rm{Jy}}\Biggr)\,\Biggl(\frac{D}{\rm{kpc}}\Biggr)^{2}\,\Biggl(\frac{\nu}{\rm{GHz}}\Biggr)^{0.1}\,\Biggl(\frac{T_e}{\rm{10^4\,K}}\Biggr)^{-0.45}\, \mathrm{phot.\,s^{-1}}\,,
\end{equation}$$ where $S_\nu$ is the flux density of the source at frequency $\nu$, $D$ is the distance of the source, and $T_e$ is the electron temperature. (cite: balser2011) provided a relation between $T_e$ and the galactocentric distance of a source, that estimated at the galactocentric distance of AG286.0716$-$1.8229   ($\sim10\,$kpc) gives a value of $T_e\sim 9000\,$K. Given the presence of some scatter in the relation, we considered a range of $T_e=8000-10000\,$K. Considering the flux density from the average continuum map of SMGPS to be 10.5 mJy at 1.36 GHz, and using the source distance of 8.5 kpc the rate of ionizing photon is in the range $5.9-6.5\times10^{46}$ photons s$^{-1}$, corresponding to a star of spectral type B0.5 (cite: panagia1973).

+:------------------------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+:---------------:+
|                                |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
|                                | DCO$^+$(2–1)                                        | N$_2$D$^+$(2–1)                                     | DCN (2–1)                                           | CH$_3$CCH (9–8)                                     |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 2-4 (lr)5-7 (lr)8-10 (lr)11-13 | det             | peak            | FWHM            | det             | peak            | FWHM            | det             | peak            | FWHM            | det             | peak            | FWHM            |
|                                |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |
| ID                             |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |                 |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
|                                |                 |                 | \[km/s\]        |                 |                 | \[km/s\]        |                 |                 | \[km/s\]        |                 |                 | \[km/s\]        |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| *cores identified in ALMAGAL 7MTM2 continuum: disappearing*                                                                                                                                                                                            |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 2                              | Y               | Y               | $1.11\pm0.04$   | Y               | Y               | $1.22\pm0.07$   | Y               | Y               | $1.3\pm0.1$     | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 5                              | Y               | Y               | $0.97\pm0.04$   | Y               | Y               | $1.01\pm0.05$   | Y               | Y               | $0.93\pm0.07$   | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 6                              | Y               | Y               | $0.97\pm0.05$   | Y               | Y               | $1.07\pm0.06$   | Y               | Y               | $1.09\pm0.08$   | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| *cores identified in ALMAGAL 7MTM2 continuum: not disappearing*                                                                                                                                                                                        |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 3                              | Y               | N               | $1.13\pm0.06$   | N               | N               | \-              | Y               | Y               | $1.23\pm0.12$   | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 4                              | Y               | N               | $1.53\pm0.13$   | N               | N               | \-              | Y               | Y               | $2.1\pm0.12$    | Y               | Y               | $1.9\pm0.1$     |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| *cores identified in ALMA Band 4 continuum outside the ALMAGAL FOV*                                                                                                                                                                                    |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 7                              | Y               | N               | $1.73\pm0.12$   | Y               | N               | $1.8\pm0.3$     | Y               | Y               | $1.66\pm0.16$   | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 8                              | Y               | N               | $1.58\pm0.13$   | Y               | N               | $1.7\pm0.3$     | Y               | Y               | $1.67\pm0.12$   | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+
| 9                              | Y               | N               | $0.70\pm0.06$   | N               | N               | \-              | N               | N               | \-              | N               | N               | \-              |
+--------------------------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+-----------------+

**Notes**: det: Y if the transition is detected at S/N\>5 in the spectra averaged on the core; peak: Y if the emission from the moment-0 map has a peaked morphology inside the area of the core. We do not took into consideration the hyperfine splitting of the deuterated species, so the FWHM values reported are upper limits.

![image](Mom1_DCO+_N2D+_DCN_images.png) ![image](FWHMfit_DCO+_N2D+_DCN_images.png)

## Molecular emission

Figure [4](#Mom0) shows the integrated intensity (moment-0) maps of DCO$^+$ (2$-$1) (*upper left*), N$_2$D$^+$ (2$-$1) (*upper center*), and DCN (2$-$1) (*upper right*) emission. The moments have been created using a velocity range defined pixel-by-pixel. We created the mask used for the moments integration following these steps: 1) we calculated the root mean squared ($\sigma$) of the cube for each pixel, using the first 500 channels of the cubes, which were determined to be free of any emission; 2) we created a first mask of the cube to include the voxels of emission above 5$\sigma$; 3) we created a second mask to include the voxels of two consecutive channels with emission above 2$\sigma$; 4) we eliminated from the mask in step 3 all the voxels that do not include a previous voxel above 5$\sigma$, i.e. defined in the mask in point 2; 5) we enlarge the mask obtained from point 4 of $0.25\times$FWHM of the beam in the spatial directions and of two channels at the beginning and at the end of the range of integration in the spectral direction, to include possible faint emission at the tail of the line profile. The mask obtained in step 5 is the final mask that we used to create the moments. As a last step, from the spectral rms and the number of channels of integration of each pixel, we constructed a map of the moment-0 rms, and blanked from the moment maps the pixels where the moment-0 signal-to-noise ratio (S/N) was below 3.\
Moreover, we extracted averaged spectra towards the cores (see Figs. [10](#fig:detection) and [11](#fig:detection2)) and we report the detection at S/N\>5 of the transitions observed in ALMA Band 4 in Table [\[tab:moleculardetection\]](#tab:moleculardetection). From Fig. [4](#Mom0), the emission of DCO$^+$(*top row of the lower panel*) is bright and compact towards the disappearing cores #2, #5, and #6, while even if still present does not peak or shows enhancement towards cores #3, #4, #7, #8, and #9. An enhancement and peak morphology is seen for N$_2$D$^+$(*middle row of the lower panel*) towards cores #2, #5, and #6; in the remaining cores it is detected from the spectra and moment-0 maps only towards cores #7 and #8, but without a peaked morphology. Conversely, the emission of DCN (*bottom row of the lower panel*) shows a bright peaked emission towards the position of core #4. However, DCN is detected toward the majority of other cores. Its morphology always shows a peak inside the area of the cores, often offset from the center of the cores, or with two peaks.\
As for the continuum, the molecular emission in ALMA Band 4 revealed the presence of material outside the continuum cores with other spots in which the emission is enhanced in those molecular species both outside and inside the ALMAGAL FOV. Those could also be the positions of further prestellar cores, better revealed by the molecular emission, as seen in two star-forming regions with H$_2$D$^+$ by (cite: redaelli2021). Table [\[tab:moleculardetection\]](#tab:moleculardetection) gives a summary of where the different molecular species shows a peaked emission.\
We also report in Fig. [5](#Mom1-2) the velocity of the gas along the line of sight and the full-width at half maximum (FWHM) of the line using DCO$^+$(2$-$1) which shows the most widespread emission in the region. In the moment-1 map we identify a velocity gradient along the radial direction centered on the H ii region position, signature of an expanding shell. Similar gradients have been found in other shell around ultra compact H ii (UC H ii) regions and H ii regions (cite: fontani2012; wang2016). Cores are located at the position where the velocities match the median of the velocity gradient, with the exception of core #1. The FWHM of the DCO$^+$ (2$-$1) is narrow, with values between 0.6 and 1.5 km s$^{-1}$ in the largest part of the region, with the exception of core #4 where it reaches values up to $\sim2$ km s$^{-1}$.\
To further investigate the presence of an expanding shell or collision between the medium outside the shell and the ionizing front that potentially triggered new star formation, we report in Fig. [6](#pvplot) the position-velocity (PV) plots of the DCO$^+$(2$-$1) emission along cuts at the positions of the cores in the radial direction, i.e. along the direction that connects each core with the center of the H ii region. For cores #4, #7, #8, and #9 there is not bright enough emission coincident with the center of the cut, i.e. the peak position of the core, as already seen in the moment-0 map. For the other cores we observe a radial velocity gradient, which in the case of cores #5 and #6 has a breaking point at their position. As stated above, the radial velocity gradient is likely the signature of an expanding shell, while the breaks in the gradient in the p-v plot resemble those showed in Fig. 5 of (cite: arce2011) at the interface between the expanding bubble and the material surrounding it.\
The CH$_3$CCH (9-8) emission has only been detected towards core #4, with the transitions $K=0$, and 1 clearly detected above 5 sigma, and two other transitions marginally detected. We extracted an average spectrum towards this core, and used the Spectral Line Identification and Modelling (SLIM) tool of the MAdrid Data CUBe Analysis package (MADCUBA (cite: MADCUBA)) to perform a line fitting. To analyze CH$_3$CCH we selected the Cologne Database for Molecular Spectroscopy catalog (CDMS, (cite: cdms))[^5], and used SLIM to generate synthetic spectra under the assumption of local thermodynamic equilibrium (LTE). SLIM allows to fit the spectrum using non-linear least-squares LTE fit to the data using the Levenberg–Marquardt algorithm, comparing the modeled spectra with the observed one. The free parameters fitted by the LTE model are the molecular column density ($N$), excitation temperature ($T_{\rm{ex}}$), central velocity of the line emission, and FWHM of the Gaussian line profiles. The resulting best fit to the spectrum is shown in Fig. [7](#fig:ch3cch)). The derived temperature is of $T_{\rm{ex}}=39\pm5\,$K, while the column density of this species is $N=(2.1\pm 0.2)\times10^{14}$ cm$^{-2}$.\
Lastly, to investigate the possible presence of outflows, we created the moment-0 and moment-1 maps of SiO $(5-4)$ transition, using the 7M+TM2 cubes of the ALMAGAL project. These are shown in Appendix in Fig. [13](#fig:SiO). Among the cores inside the ALMAGAL FOV, only the core #4 is associated to SiO emission, which shows a velocity gradient in the North East-South West direction.

![](DCO+_pvplot_radial_longer.png)

![](fit_CH3CCH_core4.png)

# Discussion

## Radial profile of continuum emission

We used the continuum emission in ALMA Band 6 *7m+tm2* data to construct the radial profile of emission of the cores from #1 to #6, and then compare the profiles of disappearing and not-disappearing ones. For every core from #1 to #6 we cut a region around the core in which by visual evaluation the emission is not affected by the presence of nearby cores. Each core has been identified as an ellipse with a specific center position (x$_0$, y$_0$), position angle (PA), semi-major to semi-minor axis ratio ($\theta_{A}/\theta_{B}$), and semi-major axis from the algorithm CuTEx. Using the four parameters x$_0$, y$_0$, PA, and $\theta_{A}/\theta_{B}$ fixed to the value defined by CuTEx for the core, it is possible to assign to each pixel of the core the semi-major axis (that we refer to as the profiles radius) of the ellipse passing through that pixel. We then create bins of distance and obtain the mean value of intensity and the standard deviation in the bin. The profiles obtained are shown in the upper panel of Fig [8](#fig:radialprof).\
The radial profile of all the disappearing cores except core #6 are shallower than those of cores #3 and #4, which have been detected also in the ALMAGAL data. This confirms our initial guess that the disappearing cores have a less peaked density profile.\
To further characterize this difference, in the lower panel of the same figure, we plot the radial profile of emission of known profile density distributions, alongside the profiles of core #1, #4, and #5 for reference. Specifically, we plotted the emission from the radial profile of a singular isothermal sphere (cite: shu1987), $\rho(r)\propto r^{-2}$, and of a Bonnor-Ebert sphere (cite: ebert1955Z; Bonnor1956) characterized by a central flat profile up to a radius close to the critical value $R_0$ and by a decrease with $r^{-2}$ for $r\gg R_0$. We approximated the Bonnor-Ebert sphere using the analytic radial profile $\rho(r)\propto (1+(r/R_0)^{\alpha})^{-1}$, with $\alpha=2$ (see e.g. (cite: fischera2014)) and using three different values of $R_0$: 500 au, 1500 au, and 2000 au. Assuming that the cores are isothermal and that the dust properties are not varying with the radius (i.e. $\kappa_{\nu}(r)=\rm{const.}$), the radial profile of the flux density emitted is given by the convolution of the surface density profile $\Sigma(R)$ with a gaussian profile with FWHM the size of the beam of the ALMA Band6 *7m+tm2* data, where $R$ is the radial coordinate on the plane of the sky. $\Sigma(R)$ is derived integrating the density profile $\rho(r)$ along the line of sight (x direction, $r^2 = R^2+x^2$ ): $$\begin{equation}
    \Sigma(R) \propto \int_{-\infty}^{+\infty}{\rho(\sqrt{x^2+R^2})dx} \propto \int_{R}^{+\infty}{\frac{2\rho(r)r}{\sqrt{r^2-R^2}}dr}\,.
\end{equation}$$ From the visual comparison of the flux density expected by the assumed density profiles with the observed profiles, those of cores #3, #4, and #6 are consistent with Bonnor-Ebert profiles with a central flattening of $\sim500\,$au, while the profiles of cores #2 and #5 are better reproduces by Bonnor-Ebert spheres with a central flattening over a larger area, up to a radius of 1500-2000 au. Values up to $\sim1500\,$au for the radius of the central flat region in prestellar cores have been already observed in the literature, e.g. in the prestellar core L1544 (cite: caselli2019). The profile of core #1 is flatter than the ones expected by all these models.

![](mean_radial_profile.png)

## Evolutionary stages of the cores from chemistry

The enhancement in the abundance of N$_2$D$^+$and DCO$^+$is associated with early stages of star formation, where the freeze-out of the CO onto dust grains at densities above $10^5\,$cm$^{-3}$ and temperatures below 20 K removes the main destruction pathways of the H$_2$D$^+$ ion, and starts the deuteration process (cite: millardeuteration; caselli2012; fontanideuteration). This is not the case for DCN which is often found to be more abundant in warmer gas, thanks to chemical pathways efficient at higher temperature (cite: millardeuteration; roueff2007; parise2009; gieser2021; cunningham2023DCN).\
(cite: fontanideuteration) show that deuterium fractionation from N$_2$H$^+$ is extremely sensitive to gas temperature, and high-mass starless cores with warmer temperatures (above 20 K) have a drop of one order of magnitude in the D/H ratio. The extreme dependence on gas temperature is also evident in the models presented in (cite: fontani2014timescale), which shows that after the temperature increases above 20 K the D/H ratio drops after just $\sim10^2$ yrs for N$_2$H$^+$ and after $\sim10^4$ yrs for HNC. The timescale of the drop of the D/H ratio for DCO$^+$is similar to that of N$_2$D$^+$($\sim100$ yrs), as it is possible to see in Fig. [12](#dcodrop) in Appendix. The plot shows the result of the same model run in (cite: fontani2014timescale) for a density of 10$^{5}$ cm$^{-3}$ (private communication with K. Furuya and F. Fontani).\
We indeed found that three out of four disappearing cores (#2, #5, and #6) show bright and compact emission of DCO$^+$(2$-$1) and N$_2$D$^+$(2$-$1). Since the enhancement of abundance of these species due to deuterium fractionation fades quickly with the onset of star-formation and the subsequent rise in temperature above 20 K, we confirm that these are prestellar cores in a region of clustered star-formation. This is further supported by the shallower radial profiles showed for all these cores, with the exception of core #6. Moreover, none of these cores is associated with SiO $(5-4)$ emission, an outflow tracer, as shown in Fig. [13](#fig:SiO).\
The lack of peaked emission in DCO$^+$and N$_2$D$^+$towards both cores #3 and #4, indicates that these cores have a higher temperature. Moreover, these two sources have a more peaked radial profile since they are detected in the continuum as compact sources in ALMAGAL 7M+TM2+TM1, and as showed in Sect. [4.1](#sec:radialprofile). Core #4 also shows bright and peaked emission of DCN, whose production is more effective in warmer gas, of CH$_3$CCH, which is a complex organic molecule, also associated with more evolved stages of the star-formation process (cite: herbstvandishoeck2009; molinarich3cch; sabatini2021), and of SiO, and outflow tracer. For this core we used the detected emission of CH$_3$CCH (9-8) to derive a temperature of $39\pm5\,$K. To summarize the information from the molecular emission towards core #4, DCO$^+$and N$_2$D$^+$, tracers of early stages of star formation, are not enhanced towards this source, while there is bright emission of DCN, CH$_3$CCH, and SiO which emission requires more evolved stages with higher temperatures, not seen in any other core. Therefore, we conclude that core #4 is the most chemically evolved and we assume that the temperature in the rest of the cores along the arch is lower than towards core #4. The cores #7, #8, and #9 do not have peaked emission in DCO$^+$(2$-$1) or N$_2$D$^+$(2$-$1), but cores #7 and #8 have been detected with a peaked morphology in DCN (2$-$1). For these reasons, we consider them and core #3 as in an intermediate evolutionary stage between that of cores #2, #5, and #6, and that of the most evolved core in our sample, namely core #4. Based on this, we assign a plausible range of temperatures between 10 K and 20 K to cores #2, #5, and #6, and a warmer range between 20 K and 30 K to cores #3, #7, #8, and #9.

+:----------------------------------------------:+:-----------:+:---------------------:+:-----------:+:---------------------:+:-----------:+:---------------------:+:-----------:+:---------------------:+:-----------:+:---------------------:+:-----------:+
|                                                |             |                       |             |                       |             |                       |             |                       |             |                       |             |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| #2-#3                                                        | #3-#4                               | #4-#6                               | #6-#5                               | #5-#8                               | #8-#9                               |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| 1-2 (lr)3-4 (lr)5-6 (lr)7-8 (lr)9-10 (lr)11-12 | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      |
|                                                |             |                       |             |                       |             |                       |             |                       |             |                       |             |
| \[$\ensuremath{''}$\]                          |             |                       |             |                       |             |                       |             |                       |             |                       |             |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| *projected*                                                                                                                                                                                                                                                |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| 1.9                                            | 0.08        | 6.1                   | 0.25        | 6.0                   | 0.25        | 3.9                   | 0.16        | 13.5                  | 0.56        | 7.3                   | 0.30        |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| *deprojected*                                                                                                                                                                                                                                              |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| 2.4                                            | 0.10        | 7.8                   | 0.32        | 7.6                   | 0.32        | 5.0                   | 0.21        | 17.1                  | 0.71        | 9.3                   | 0.39        |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
|                                                |             |                       |             |                       |             |                       |             |                       |             |                       |             |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
|                                                |             | min                                 | max                                 | mean                                | median                              | std                                 |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| 3-4 (lr)5-6 (lr)7-8 (lr)9-10 (lr)11-12         |             | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      | \[$\ensuremath{''}$\] | \[pc\]      |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| *projected*                                                  | 1.9                   | 0.08        | 13.5                  | 0.56        | 6.5                   | 0.27        | 6.1                   | 0.25        | 3.9                   | 0.16        |
+--------------------------------------------------------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
| *deprojected*                                                | 2.4                   | 0.10        | 17.1                  | 0.71        | 8.2                   | 0.34        | 7.7                   | 0.32        | 5.0                   | 0.20        |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+
|                                                |             |                       |             |                       |             |                       |             |                       |             |                       |             |
+------------------------------------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+-----------------------+-------------+

\
**Notes**: Upper part: projected and deprojected (using the factor 4/$\pi$) angular and linear separations between cores along the arch. Lower part: minimum, maximum, mean, median, and standard deviation of the values reported in the upper part of the table.

## Mass estimates and virial parameter

To estimate the core masses we use the equation: $$\begin{equation}
    M = \frac{100 \,F_{\rm{INT}}\, D^2}{B_{\nu}(T)\kappa_{\nu}},
\end{equation}$$ where $F_{\rm{INT}}$ is the integrated flux density derived from CuTEx at 219 GHz for cores from #2 to #6 and at 150 GHz for cores #7 to #9, $D$ is the distance of the source, $B_\nu(T)$ is the Planck function either at 219 GHz or 150 GHz for the core dust temperature $T$, the factor 100 is the usually assumed gas-to-dust ratio, and $\kappa_{\nu}$ is the dust mass absorption coefficient, assumed to be 0.9 cm$^2$ g$^{-1}$ at 219 GHz as in (cite: ALMAGAL3), and scaled with a $\beta$ of 1.7 to derive the dust opacity coefficient at 150 GHz, following the relation: $$\begin{equation*}
    \kappa_{150} = \kappa_{219}\,\Biggl( \frac{150\,\rm{GHz}}{219\,\rm{GHz}}\Biggr) ^\beta\,.
\end{equation*}$$ For core #4 we used as dust temperature the temperature estimated from the fit of CH$_3$CCH, assuming that gas and dust are coupled. For the other cores, under the same assumption, we use the ranges of temperature defined in section 4.2. We derived the mass ranges for those temperature ranges, and we listed them in Table [\[tab:massvirial\]](#tab:massvirial). For these calculation we have used the usually adopted gas-to-dust ratio of 100, but as highlighted by the work of (cite: giannetti2017) this ratio reaches higher values in the outer Galaxy, even though the data show large scatter. In particular, at the galactocentric distance of AG286.0716$-$1.8229  ($\sim10$ kpc) the gas-to-dust ratio from the relation found in (cite: giannetti2017) would be of $\sim200$. Thus, these masses could be underestimated up to a factor two from the uncertainties on this parameter.\
In Table [\[tab:massvirial\]](#tab:massvirial) we also list an average FWHM from fits to all the molecular lines detected on the cores (listed in Table [\[tab:moleculardetection\]](#tab:moleculardetection)), obtained with a Gaussian fit of the mean spectrum over the size of each core. The fit to derive the FWHM for the three deuterated species reported in Table [\[tab:moleculardetection\]](#tab:moleculardetection) does not take into account the hyperfine splitting of the lines, therefore these are upper limits of the value of FWHM. We did not considered the hyperfine splitting because only in a few cases more transitions other than the main were detected in the spectrum, thus making the results of the fit including the hyperfine splitting not well constrained. With these information we can derive the virial parameter of the cores, $\alpha_{\rm{vir}}$, defined as (cite: bertoldi1992): $$\begin{equation}
\alpha_{\rm{vir}} = \frac{2\,E_{\rm{kin}}}{E_{\rm{grav}}} = \frac{5\,\sigma^2\,r}{G\,M}\,,
\end{equation}$$ where $E_{\rm{kin}}$ and $E_{\rm{grav}}$ are the kinetic and gravitational potential energy of the cores, while $\sigma$ is the velocity dispersion, related to the FWHM by $\sigma=\mathrm{FWHM}/2.35$. The values are reported in Table [\[tab:massvirial\]](#tab:massvirial) and vary between 0.3 and 2.4, for all cores except core #7 which has a virial parameter larger than 3. Despite the large ranges due to uncertainties in the temperature and therefore mass of the cores, all the cores except core #7 are consistent with bound objects ($\alpha_{\rm{vir}}<2$, e.g. (cite: kauffmann2013) ), not only cores #3 and #4 that already have a central condensation at $\sim1400\,$au. Moreover, as stated above, the FWHM and therefore $\sigma$ for most of the cores are upper limits of the real value, since we did not take into account the hyperfine splitting, while the masses could be lower limits if the real gas-to-dust ratio in the region is above 100. Therefore the values of $\alpha_{\rm{vir}}$ reported here are also upper limits.

# Triggered star-formation?

The presence of an H ii region in our FOV and the location of the cores on an arched-shaped region centered at the H ii region does not ensure that these cores are the result of triggered star formation, as found by (cite: Zhang2024ATOMS). In the case of source AG286.0716$-$1.8229, we also see from Fig. [2](#allbands) that there is a gap between the 23 cm emission and the dust and gas arched structure, with no evidence of a photodissociation region (PDR), such as a bright rim in the images of IRAC band 1 at 3.6 $\mu$m (see Fig. D.1) due to the emission of polycyclic aromatic hydrocarbons (PAHs), while the data from IRAC band 3 and 4 are not available and other typical molecular tracers of PDRs (cite: kim2020) are not present in our data. One possibility is that the H ii region is more extended than the region emitting at 23 cm (cite: kim&koo2001; kurtz2002), but the outer part of the H ii is not efficiently emitting, due to possible lower values of the electron density or electron temperature. Another possibility is that the region is shaped not only by the H ii region, but also by the presence of stellar winds (cite: kim2025).\
In both cases, to test if the formation of these cores is triggered we compare the scale of fragmentation and the typical mass of fragments along the arch with the value expected in the case of a shell fragmentation as prescribed by the collect and collapse process. The formulae to calculate these parameters have been derived by (cite: whitworth1994shell): $$\begin{equation}
\lambda_{\rm{shell}} \sim 0.83\, \Big( \frac{c_s}{0.2 \rm{km/s}} \Big)^{18/11}\, \Big( \frac{N_{\rm{Ly}}}{10^{49} \rm{s^{-1}}} \Big)^{-1/11}\, \Big( \frac{n_0}{10^{3} \rm{cm^{-3}}} \Big)^{-5/11}\,\mathrm{pc}\,,
\end{equation}$$ $$\begin{equation}
M_{\rm{shell}} \sim 23\, \Big( \frac{c_s}{0.2 \rm{km/s}} \Big)^{40/11}\, \Big( \frac{N_{\rm{Ly}}}{10^{49} \rm{s^{-1}}} \Big)^{-1/11}\, \Big( \frac{n_0}{10^{3} \rm{cm^{-3}}} \Big)^{-5/11}\,\mathrm{M_{\odot}}\,,
\end{equation}$$ $$\begin{equation}
R_{\rm{shell}} \sim 5.8\, \Big( \frac{c_s}{0.2 \rm{km/s}} \Big)^{4/11}\, \Big( \frac{N_{\rm{Ly}}}{10^{49} \rm{s^{-1}}} \Big)^{1/11}\, \Big( \frac{n_0}{10^{3} \rm{cm^{-3}}} \Big)^{-6/11}\,\mathrm{pc}\,,
\end{equation}$$ $$\begin{equation}
t_{\rm{shell}} \sim 1.56\, \Big( \frac{c_s}{0.2 \rm{km/s}} \Big)^{7/11}\, \Big( \frac{N_{\rm{Ly}}}{10^{49} \rm{s^{-1}}} \Big)^{-1/11}\, \Big( \frac{n_0}{10^{3} \rm{cm^{-3}}} \Big)^{-5/11}\, \mathrm{yr}\,,
\end{equation}$$ where $\lambda_{\rm{shell}}$, $M_{\rm{shell}}$, $R_{\rm{shell}}$, and $t_{\rm{shell}}$ are the characteristic scale of fragmentation, the characteristic mass of the fragments, and the radius of the shell at the time of fragmentation $t_{\rm{shell}}$, respectively.\
The only quantities needed to derive these parameters are the rate of ionizing photons $N_{\rm{Ly}}\sim 6.2\times10^{46}$phot. s$^{-1}$, as derived in Sect. 3.2, the isothermal sound speed for the shell $c_s$, and the initial density of the material swept by the expanding H ii region, $n_0$, assuming that the mean density at clump scale observed is a good estimate of its initial value before the expansion of the H ii region. We used the values derived from the Herschel infrared Galactic Plane Survey (Hi-Gal) (cite: elia2021), i.e. from the fit of the infrared SED at clump scale ($\sim$1 pc), for the temperature of the clump, its mass, and radius to derive the best estimate of $c_s$ and $n_0$. Those are 0.2 km s$^{-1}$ and 5.1$\times10^4$cm$^{-3}$, respectively. Using these values, and assuming a 10% error for all the three parameters in Eq.s (5)-(8), we find $\lambda_{\rm{shell}}\sim 0.22\pm0.05$ pc, $M_{\rm{shell}}\sim6\pm3$ M$_{\odot}$, $R_{\rm{shell}}\sim0.43\pm0.04$ pc, and $t_{\rm{shell}}\sim0.42\pm0.05$ Myr.\
We list the separation of all the bound cores along the arch (i.e. all except core #7) in Table [\[tab:separation\]](#tab:separation). The median values in AG286.0716$-$1.8229  is $0.25\pm0.15$ pc. However, this is a lower limit of the separation, assuming that all the cores are perfectly aligned on the plane of the sky. For a couple of randomly oriented sources in 3d, the average deprojection factor is 4/$\pi$ (see (cite: schisano2025)). The mean deprojected value is $0.34\pm0.19$. We consider this value an upper limit for the mean separation, since from the disposition of the cores on a circular arch it is likely that the 3d structure is not randomly oriented, and the 3d separations do not have large contribution in the direction perpendicular to the plane of the sky. Both the deprojected and the observed mean separation of the cores are compatible within the error to that expected from the collect and collapse scenario, with the deprojected value being a factor $\sim 1.5$ larger than the estimate for the model. The mean mass of the cores considering both the upper limits and the lower limits reported in Table [\[tab:massvirial\]](#tab:massvirial) is $6\pm4$ M$_{\odot}$. Therefore they are also compatible with the characteristic mass $M_{\rm{shell}}\sim6$ M$_{\odot}$, while $R_{\rm{shell}}\sim0.4$ pc is smaller than the radius of the arc of 0.75 pc, but within a factor 2.\
Assuming the same values of $c_s$ and $N_{\rm{Ly}}$, a radius of $\sim0.75\,$pc from Eq. (7) corresponds to a value of the initial volume density before the expansion of the H ii region $n_0\sim2\times10^4\,$cm$^{-3}$, only a factor $\sim2.5$ smaller than the value evaluated by (cite: elia2021) for the current mean density of the clump. Using this new value of $n_0$ the estimates from Eq.s (5), (6), and (8) would be $\lambda_{\rm{shell}}\sim 0.34\pm0.08$ pc, $M_{\rm{shell}}\sim9\pm4$ M$_{\odot}$, and $t_{\rm{shell}}\sim0.67\pm0.08$ Myr. The fragmentation scale and the typical mass of the fragments would still be compatible with the median values observed within their errors, differing of a factor $\sim1.1$ and $\sim1.5$ from the observed values respectively.\
We compare the mean separation and mass of the fragments also with the thermal Jeans length and the thermal Jeans mass, using the properties at clump level. These have been derived by (cite: schisano2025) to be 0.10 pc and 1.7 M$_{\odot}$, with an error of 0.01 pc and 0.4 M$_{\odot}$ respectively assuming a 10% error on the two parameters involved in their calculation, i.e. the volume density and the temperature of the gas, as seen in Eq.s (B.2) and (B.3) of (cite: schisano2025).\
The thermal Jeans length is a factor 2.5 lower than the mean observed separation, and a factor 3.4 lower than the mean deprojected separation and not compatible within the errors. The thermal Jeans mass is a factor $\sim3.5$ lower than the mean of the masses observed. The thermal Jeans mass is marginally compatible within the error with the mean mass from observations (upper limit from the model: $1.7+0.4=2.1\,\mathrm{M}_{\odot}$; lower limit of the mean of the mass estimated $6-4=2\,\mathrm{M}_{\odot}$). Nevertheless, as discussed in Sect. [4.3](#sect:mass) the dust-to-gas ratio in this region could be higher than 100, leading to higher estimates of the masses observed.\
Figure [9](#fig:results) summarizes the comparison between observations and models, showing that the observed separations and masses for the cores in AG286.0716$-$1.8229  are in agreement with predictions from the collect and collapse models.

![](recap_models.png)

# Conclusions

To study the nature of the disappearing cores, i.e. cores identified as compact sources in the ALMAGAL 7M+TM2 continuum at $\sim5000$ au (7600 au for AG286.0716$-$1.8229) with no counterpart in the ALMAGAL 7M+TM2+TM1 continuum at $\sim1000$ au (1400 au for AG286.0716$-$1.8229), we collected archival continuum centimeter and infrared data and new molecular line observations of the source AG286.0716$-$1.8229, which is associated with a candidate H ii region from the catalog of (cite: anderson2014). Here we summarize the main results of our work:

- We built the radial profiles of the emission of the cores in the ALMAGAL FOV and confirmed that the profiles of the disappearing cores are shallower than those of cores #3 and #4, except core #6. This core has a profile similar to those of core #3 and #4, which are detected also in the higher resolution ALMAGAL images. The flux density radial profiles are compatible with the flux density expected for Bonnor-Ebert density profiles, with a larger inner flat region for the disappearing cores.

- From the analysis of the radial profiles and of the emission of DCO$^+$(2$-$1), N$_2$D$^+$(2$-$1), and SiO $(5-4)$ we confirm that cores #2, #5, and #6 (i.e. 3 out of 4 disappearing cores) are young prestellar objects. The other disappearing core, core #1, does not have a compact morphology when observed in ALMA Band 4, and it likely corresponds to material dispersed by the expansion of the H ii region or the relic of the dust envelope around the ionizing star.

- From the $\sim$23 cm radio continuum emission we inferred the spectral index between 0.8 GHz and 1.6 GHz, which is consistent with the flat index of optically thin free-free emission ($\alpha\sim-0.1$ to $-0.4$). We therefore confirmed the presence of a H ii region in this source. We derived a rate of ionizing photons $N_{\rm{Ly}}\sim6.2\times10^{46}$ photons s$^{-1}$, which corresponds to a B0.5 star.

- The continuum emission in ALMA Bands 4 and 6 revealed a distribution of cores along an arched shaped region of radius $\sim0.75$ pc centered close to the peak of the 23 cm radio continuum emission.

- From the chemical characterization of the cores we derived a evolution sequence among the cores and assigned a range of gas and dust temperatures. Only towards the most evolved core #4 we were able to derive a precise measurement of the temperature (39$\pm$5 K), thanks to the detection of CH$_3$CCH.

- The virial parameter derived for all the cores in the arched structure is consistent with bound objects, with the exception of core #7.

- We compared the separations of the cores along the arch structure and their typical masses with the characteristic separation and mass derived in the collect and collapse scenario and with the thermal Jeans length and mass. The best agreement is found with the characteristic scales in the case of triggered star formation.

This study confirmed that disappearing cores are good prestellar cores candidates. The presence of several of these cores in the ALMAGAL sample will allow us to increase the statistics and study how these early stages are affected by the feedback of already formed massive stars.

# Acknowledgements

The authors thank K. Furuya for the plot that shows the result for DCO$^+$of the D/H drop after the temperature increase in the model presented in Fontani et al. 2014. The authors thanks the referee for their insightful comments. C.M. and the INAF-IAPS team acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 program through the ECOGAL Synergy grant (ID 855130). CM acknowledges funding from INAF Mini Grants RSN2 2024 "Zodyac" CUP C83C25000340005. RK acknowledges financial support via the Heisenberg Research Grant funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under grant no. KU 2849/9, project no. 445783058. Part of this research was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration (80NM0018D0004). D.C.L. acknowledges financial support from the National Aeronautics and Space Administration (NASA) Astrophysics Data Analysis Program (ADAP). L.B. gratefully acknowledges support by the ANID BASAL project FB210003. A.S-M. acknowledges support from the PID2023-146675NB grant funded by MCIN/AEI/10.13039/501100011033, and by the programme Unidad de Excelencia Marı́a de Maeztu CEX2020-001058-M, as well as support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR. RSK acknowledges financial support from the ERC via Synergy Grant “ECOGAL” (project ID 855130) and from the German Excellence Strategy via the Heidelberg Cluster “STRUCTURES” (EXC 2181 - 390900948). In addition RSK is grateful for funding from the German BMWE in project “MAINN” (funding ID 50OO2206), and from DFG and ANR for project “STARCLUSTERS” (funding ID KL 1358/22-1). This paper makes use of the following ALMA data: project code 2019.1.00195.L and 2023.1.01386.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

77 natexlab

(ref: anderson2014) Anderson, L. D., Bania, T. M., Balser, D. S., et al. 2014, ApJS, 212, 1

(ref: arce2011) Arce, H. G., Borkin, M. A., Goodman, A. A., Pineda, J. E., & Beaumont, C. N. 2011, ApJ, 742, 105

(ref: balser2011) Balser, D. S., Rood, R. T., Bania, T. M., & Anderson, L. D. 2011, ApJ, 738, 27

(ref: bertoldi1989) Bertoldi, F. 1989, ApJ, 346, 735

(ref: bertoldi1992) Bertoldi, F. & McKee, C. F. 1992, ApJ, 395, 140

(ref: Bonnor1956) Bonnor, W. B. 1956, MNRAS, 116, 351

(ref: ch3cch_1) Burrell, P. M., Bjarnov, E., & Schwendeman, R. H. 1980, Journal of Molecular Spectroscopy, 82, 193

(ref: cacciapuoti2023) Cacciapuoti, L., Macias, E., Maury, A. J., et al. 2023, A&A, 676, A4

(ref: casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: caselli2012) Caselli, P. & Ceccarelli, C. 2012, A&ARv, 20, 56

(ref: caselli2019flat) Caselli, P., Pineda, J. E., Zhao, B., et al. 2019a, ApJ, 874, 89

(ref: caselli2019) Caselli, P., Pineda, J. E., Zhao, B., et al. 2019b, ApJ, 874, 89

(ref: ch3cch_4) Cazzoli, G. & Puzzarini, C. 2008, A&A, 487, 1197

(ref: ALMAGAL3) Coletta, A., Molinari, S., Schisano, E., et al. 2025, A&A, 696, A151

(ref: cunningham2023DCN) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, A&A, 678, A194

(ref: dale2007) Dale, J. E., Bonnell, I. A., & Whitworth, A. P. 2007, MNRAS, 375, 1291

(ref: deharveng2008) Deharveng, L., Lefloch, B., Kurtz, S., et al. 2008, A&A, 482, 585

(ref: RASC1.7GHz) Duchesne, S., Ross, K., Thomson, A. J. M., et al. 2025, PASA, 42, 38

(ref: RASC1.3GHz) Duchesne, S. W., Grundy, J. A., Heald, G. H., et al. 2024, PASA, 41, e003

(ref: ebert1955Z) Ebert, R. 1955, ZAp, 37, 217

(ref: elia2007VelaD) Elia, D., Massi, F., Strafella, F., et al. 2007, ApJ, 655, 316

(ref: elia2021) Elia, D., Merello, M., Molinari, S., et al. 2021, MNRAS, 504, 2742

(ref: elmegreen1977) Elmegreen, B. G. & Lada, C. J. 1977, ApJ, 214, 725

(ref: cdms) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: fischera2014) Fischera, J. 2014, A&A, 571, A95

(ref: fontani2012) Fontani, F., Palau, A., Busquet, G., et al. 2012, MNRAS, 423, 1691

(ref: fontanideuteration) Fontani, F., Palau, A., Caselli, P., et al. 2011, A&A, 529, L7

(ref: fontani2014timescale) Fontani, F., Sakai, T., Furuya, K., et al. 2014, MNRAS, 440, 448

(ref: giannetti2017) Giannetti, A., Leurini, S., König, C., et al. 2017, A&A, 606, L12

(ref: gieser2021) Gieser, C., Beuther, H., Semenov, D., et al. 2021, A&A, 648, A66

(ref: goedhart2024) Goedhart, S., Cotton, W. D., Camilo, F., et al. 2024, MNRAS, 531, 649

(ref: rasc0.880GHz) Hale, C. L., McConnell, D., Thomson, A. J. M., et al. 2021, PASA, 38, e058

(ref: herbstvandishoeck2009) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: hosokawa2005) Hosokawa, T. & Inutsuka, S.-i. 2005, ApJ, 623, 917

(ref: hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., & et al. 2023, Publications of the Astronomical Society of the Pacific, 135, 074501

(ref: kauffmann2013) Kauffmann, J., Pillai, T., & Goldsmith, P. F. 2013, ApJ, 779, 185

(ref: kendrew2016) Kendrew, S., Beuther, H., Simpson, R., et al. 2016, ApJ, 825, 142

(ref: kendrew2012) Kendrew, S., Simpson, R., Bressert, E., et al. 2012, ApJ, 755, 71

(ref: kim&koo2001) Kim, K.-T. & Koo, B.-C. 2001, ApJ, 549, 979

(ref: kim2025) Kim, W.-J., Beuther, H., Wyrowski, F., et al. 2025, A&A, 694, A30

(ref: kim2020) Kim, W.-J., Wyrowski, F., Urquhart, J. S., et al. 2020, A&A, 644, A160

(ref: kurtz2002) Kurtz, S. 2002, in Astronomical Society of the Pacific Conference Series, Vol. 267, Hot Star Workshop III: The Earliest Phases of Massive Star Birth, ed. P. Crowther, 81

(ref: Liu2015) Liu, H.-L., Wu, Y., Li, J., et al. 2015, ApJ, 798, 30

(ref: MADCUBA) Martı́n, S., Martı́n-Pintado, J., Blanco-Sánchez, C., et al. 2019, A&A, 631, A159

(ref: matsakis1976) Matsakis, D. N., Evans, II, N. J., Sato, T., & Zuckerman, B. 1976, AJ, 81, 172

(ref: rascI) McConnell, D., Hale, C. L., Lenc, E., et al. 2020, PASA, 37, e048

(ref: millardeuteration) Millar, T. J., Bennett, A., & Herbst, E. 1989, ApJ, 340, 906

(ref: molinarich3cch) Molinari, S., Merello, M., Elia, D., et al. 2016, ApJL, 826, L8

(ref: ALMAGAL1) Molinari, S., Schilke, P., Battersby, C., et al. 2025, A&A, 696, A149

(ref: cutexmolinari2011) Molinari, S., Schisano, E., Faustini, F., et al. 2011, A&A, 530, A133

(ref: cutexsoftware) Molinari, S., Schisano, E., Faustini, F., et al. 2017, CUTEX: CUrvature Thresholding EXtractor, Astrophysics Source Code Library, record ascl:1708.018

(ref: ch3cch_3) Müller, H. S. P., Pracna, P., & Horneman, V.-M. 2002, Journal of Molecular Spectroscopy, 216, 397

(ref: ch3cch_2) Müller, H. S. P., Thorwirth, S., Bizzocchi, L., & Winnewisser, G. 2000, Zeitschrift Naturforschung Teil A, 55, 491

(ref: palmeirim2017) Palmeirim, P., Zavagno, A., Elia, D., et al. 2017, A&A, 605, A35

(ref: panagia1973) Panagia, N. 1973, AJ, 78, 929

(ref: parise2009) Parise, B., Leurini, S., Schilke, P., et al. 2009, A&A, 508, 737

(ref: Planck_abergel2014) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2014, A&A, 571, A11

(ref: redaelli2021) Redaelli, E., Bovino, S., Giannetti, A., et al. 2021, A&A, 650, A202

(ref: roueff2007) Roueff, E., Parise, B., & Herbst, E. 2007, A&A, 464, 245

(ref: sabatini2021) Sabatini, G., Bovino, S., Giannetti, A., et al. 2021, A&A, 652, A71

(ref: ALMAGAL2) Sánchez-Monge, Á., Brogan, C. L., Hunter, T. R., et al. 2025, A&A, 696, A150

(ref: schisano2025) Schisano, E., Molinari, S., Coletta, A., et al. 2025, arXiv e-prints, arXiv:2512.05914

(ref: sharma2022) Sharma, T., Chen, W. P., Panwar, N., Sun, Y., & Gao, Y. 2022, ApJ, 928, 17

(ref: shu1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23

(ref: tackenberg2013) Tackenberg, J., Beuther, H., Plume, R., et al. 2013, A&A, 550, A116

(ref: thompson2012) Thompson, M. A., Urquhart, J. S., Moore, T. J. T., & Morgan, L. K. 2012, MNRAS, 421, 408

(ref: walch2015) Walch, S., Whitworth, A. P., Bisbas, T. G., Hubber, D. A., & Wünsch, R. 2015, MNRAS, 452, 2794

(ref: CARTA) Wang, K. ., Comrie, A., Harris, P., et al. 2020, in Astronomical Society of the Pacific Conference Series, Vol. 527, Astronomical Data Analysis Software and Systems XXIX, ed. R. Pizzo, E. R. Deul, J. D. Mol, J. de Plaa, & H. Verkouter, 213

(ref: wang2016) Wang, Y., Audard, M., Fontani, F., et al. 2016, A&A, 587, A69

(ref: Weingartner2001) Weingartner, J. C. & Draine, B. T. 2001, ApJ, 548, 296

(ref: deepGlimpse) Whitney, B., Benjamin, R., Churchwell, E., et al. 2011, Deep GLIMPSE: Exploring the Far Side of the Galaxy, Spitzer Proposal ID #80074

(ref: whitworth1994shell) Whitworth, A. P., Bhattal, A. S., Chapman, S. J., Disney, M. J., & Turner, J. A. 1994, MNRAS, 268, 291

(ref: zavagno2006) Zavagno, A., Deharveng, L., Comerón, F., et al. 2006, A&A, 446, 171

(ref: zavagno2007) Zavagno, A., Pomarès, M., Deharveng, L., et al. 2007, A&A, 472, 835

(ref: zavagno2010) Zavagno, A., Russeil, D., Motte, F., et al. 2010, A&A, 518, L81

(ref: Zhang2024ATOMS) Zhang, S., Liu, T., Wang, K., et al. 2024, MNRAS, 535, 1364

(ref: zhou2020) Zhou, J., Zhou, D., Esimbek, J., et al. 2020, ApJ, 897, 74

# Spectra averaged on the cores

For each cores detected in the ALMA data towards AG286.0716$-$1.8229, we extracted the average spectra for N$_2$D$^+$(2–1), DCO$^+$(2–1), DCN (2–1), and CH$_3$CCH (9–8). These are shown in Fig. [10](#fig:detection) and [11](#fig:detection2).

![image](spectra_with_fit_core_2_paper.png)\
![image](spectra_with_fit_core_3_paper.png)\
![image](spectra_with_fit_core_4_paper.png)\
![image](spectra_with_fit_core_5_paper.png)\
![image](spectra_with_fit_core_6_paper.png) ![image](spectra_with_fit_core_7_paper.png)\

![image](spectra_with_fit_core_8_paper.png)\
![image](spectra_with_fit_core_9_paper.png)\

# D/H ratio drop timescale for DCO$^+$

In Fig. [12](#dcodrop) we show the results of the model by (cite: fontani2014timescale) in the case of a density of 10$^{5}$ cm$^{-3}$ (private communication with F. Fontani and K. Furuya).

![](dh_dens5.pdf)

# SiO moment maps

We created the moment-0 and moment-1 maps of SiO (5-4) in the ALMAGAL dataset using the same methodology described in Sect. 3.3. These are shown in Fig. [13](#fig:SiO)

![](SiO_images.png)

# IRAC emission

![](fig2_irac_meerkat.png)

[^1]: this is the typical value for the whole ALMAGAL sample. For source AG286.0716$-$1.8229  it is 1400 au.

[^2]: this is the typical value for the whole ALMAGAL sample. For source AG286.0716$-$1.8229  it is 7600 au.

[^3]: https://archive-gw-1.kat.ac.za/public/repository/10.48479/3wfd-e270/index.html

[^4]: The best order for the background is automatically assessed by CuTEx.

[^5]: The entry of CDMS for CH$_3$CCH is based on the following works: (cite: ch3cch_1; ch3cch_2; ch3cch_3; ch3cch_4).

</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[2].what.evidence[1]",
  "value": "CuTEx compact source extraction on ALMAGAL 219 GHz continuum and dust mass absorption coefficient kappa_219 = 0.9 cm^2 g^-1",
  "failed_quote": "$\\kappa_{\nu}$ is the dust mass absorption coefficient, assumed to be 0.9 cm$^2$ g$^{-1}$ at 219 GHz as in (cite: ALMAGAL3), and scaled with a $\beta$ of 1.7 to derive the dust opacity coefficient at 150 GHz"
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "r = d tan(theta) where theta = sqrt(theta_A * theta_B)",
  "failed_quote": "In Table [tab:massvirial] we report the coordinates, the integrated flux densities of the cores, and their mean radius r, as derived from CuTEx ($r=d \tan\theta$, where $\theta=\\sqrt{\theta_A \theta_B}$ and $d=8.5\\,$kpc is the source distance) of cores from #2 to #9."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "S_nu proportional to nu^alpha; Rayleigh-Jeans regime beta = alpha - 2",
  "failed_quote": "The spectral index $\\alpha$ (assuming $S_{\nu}\\propto\nu^{\\alpha}$) from the fit of the data is $-0.4\\pm0.4$"
 },
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Compute pixel-by-pixel rms from first 500 channels; build 3D mask requiring >5 sigma seed voxels connected to two consecutive channels >2 sigma, expanded by 0.25x beam FWHM spatially and 2 channels spectrally; blank moment-0 pixels with S/N < 3; extract radial PV cuts of DCO+(2-1) and core-averaged spectra with Gaussian fits for FWHM.",
  "failed_quote": "In Table [tab:massvirial] we also list an average FWHM from fits to all the molecular lines detected on the cores (listed in Table [tab:moleculardetection]), obtained with a Gaussian fit of the mean spectrum over the size of each core."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "500 emission-free channels for rms; 5 sigma seed threshold; 2 consecutive channels > 2 sigma; expanded by 0.25*FWHM spatially and 2 channels spectrally; moment-0 blanked at S/N < 3; spectral detection threshold S/N > 5",
  "failed_quote": "Moreover, we extracted averaged spectra towards the cores (see Figs. 10 and 11) and we report the detection at S/N>5 of the transitions observed in ALMA Band 4 in Table [tab:moleculardetection]."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Gaussian fit to core-averaged spectra",
  "failed_quote": "In Table [tab:massvirial] we also list an average FWHM from fits to all the molecular lines detected on the cores (listed in Table [tab:moleculardetection]), obtained with a Gaussian fit of the mean spectrum over the size of each core."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Cores are isothermal and dust properties do not vary with radius (kappa_nu(r) = const.)",
  "failed_quote": "Assuming that the cores are isothermal and that the dust properties are not varying with the radius (i.e. $\\kappa_{\nu}(r)=\rm{const.}$), the radial profile of the flux density emitted is given by the convolution of the surface density profile $\\Sigma(R)$"
 },
 {
  "path": "analysis_steps[5].method.evidence[0]",
  "value": "Assign temperature ranges to cores based on chemical evolutionary stage, compute optically thin dust masses from CuTEx integrated fluxes at 219 GHz (cores #2-#6) and 150 GHz (cores #7-#9), and compute virial parameters alpha_vir from core radii, masses, and mean molecular line FWHMs.",
  "failed_quote": "where $F_{\rm{INT}}$ is the integrated flux density derived from CuTEx at 219 GHz for cores from #2 to #6 and at 150 GHz for cores #7 to #9, $D$ is the distance of the source, $B_\nu(T)$ is the Planck function"
 },
 {
  "path": "analysis_steps[5].key_parameters[1].evidence[0]",
  "value": "kappa_219 = 0.9 cm^2 g^-1, beta = 1.7, gas-to-dust ratio = 100, D = 8.5 kpc, sigma = FWHM / 2.35",
  "failed_quote": "the factor 100 is the usually assumed gas-to-dust ratio, and $\\kappa_{\nu}$ is the dust mass absorption coefficient, assumed to be 0.9 cm$^2$ g$^{-1}$ at 219 GHz as in (cite: ALMAGAL3), and scaled with a $\beta$ of 1.7"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Candidate H II region radio spectral index alpha (with SMGPS 1.65 GHz point) = -0.4 dimensionless",
  "failed_quote": "The spectral index $\\alpha$ (assuming $S_{\nu}\\propto\nu^{\\alpha}$) from the fit of the data is $-0.4\\pm0.4$, mostly driven by the point at 1.65 GHz from SMGPS, while the flux density from RACS data at the same frequency is consistent with a $-0.1\\pm0.4$ spectral index."
 },
 {
  "path": "results_numeric[29].evidence[0]",
  "value": "Mean observed core mass = 6 M_sun",
  "failed_quote": "The mean mass of the cores considering both the upper limits and the lower limits reported in Table [tab:massvirial] is $6\\pm4$ M$_{\\odot}$."
 }
]
```
