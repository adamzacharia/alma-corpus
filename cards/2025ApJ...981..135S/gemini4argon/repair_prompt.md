# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...981..135S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Abstract

We present JWST NIRCam imaging of B14-65666 (“Big Three Dragons”), a bright Lyman-break galaxy system ($M_\text{UV}=-22.5$ mag) at $z=7.15$. The high angular resolution of NIRCam reveals the complex morphology of two galaxy components: galaxy E has a compact core (E-core), surrounded by diffuse, extended, rest-frame optical emission, which is likely to be tidal tails; and galaxy W has a clumpy and elongated morphology with a blue UV slope ($\ensuremath{\beta_\text{UV}}=-2.2\pm0.1$). The flux excess, F356W$-$F444W, peaks at the E-core ($1.05^{+0.08}_{-0.09}$ mag), tracing the presence of strong \[O iii\]$\lambda\lambda$4960,5008 Å emission. ALMA archival data show that the bluer galaxy W is brighter in dust continua than the redder galaxy E, while the tails are bright in \[O iii\] 88 $\mathrm{\mu m}$. The UV/optical and sub-mm SED fitting confirms that B14-65666 is a major merger in a starburst phase as derived from the stellar mass ratio (3:1 to 2:1) and the star-formation rate, $\simeq1$ dex higher than the star-formation main sequence at the same redshift. The galaxy E is a dusty ($A_\text{V}=1.2\pm0.1$ mag) starburst with a possible high dust temperature ($\ge63\mbox{--}68$ K). The galaxy W would have a low dust temperature ($\le27\mbox{--}33$ K) or patchy stellar-and-dust geometry, as suggested from the infrared excess (IRX) and $\beta_\text{UV}$ diagram. The high optical-to-FIR \[O iii\] line ratio of the E-core shows its lower gas-phase metallicity ($\simeq0.2\mbox{--}0.4$ $Z_\text{\(\odot\)}$) than the galaxy W. These results agree with a scenario where major mergers disturb morphology and induce nuclear dusty starbursts triggered by less-enriched inflows. B14-65666 shows a picture of complex stellar buildup processes during major mergers in the epoch of reionization.

# Introduction

Galaxy mergers are a fundamental process to build up the stellar content through galaxy evolution. Gravitational perturbations by galaxy interactions can strongly disturb the morpho-kinematics, which is characterized by tidal tails and large velocity dispersion. It is theoretically predicted that such perturbation promotes gas accretion from outskirts into the central parts of galaxies that can trigger nuclear star formation (cite: Mihos.J:1994a; Mihos.J:1996a; Barnes.J:1996a). In observations of local galaxies, the star-formation rate ($\mathrm{SFR}$) of interacting galaxies increases as projected pair separation decreases to within several tens kpc (cite: Barton.E:2000a). This $\mathrm{SFR}$ enhancement is particularly notable in collisions of galaxies with similar stellar masses (cite: Ellison.S:2008a). The gas accretion associated with mergers can also induce an observed reduction in the gas-phase metallicity at a fixed mass or luminosity (cite: Kewley.L:2006a; Ellison.S:2008a). Even after the coalescence phase, the major mergers are expected to cause energetic events in the subsequent evolution of the merged galaxies, such as luminous infrared starbursts, rapid black hole growths, and the appearance of quasars (cite: Hopkins:2008a).

At high redshifts, major mergers are predicted to play a more important role in the evolutionary path because the merger rate theoretically increases with increasing redshift by $\propto (1 + z)^{2\mbox{--}3}$ (cite: Fakhouri.O:2008a; Rodriguez-Gomez.V:2015a). This increase is consistent with observed major merger fractions at $z\sim0\mbox{--}5$ (cite: Man.A:2016a; Ventou.E:2017a) when the redshift-dependent merger timescale is taken into account (cite: Qu.Y:2017a; Snyder.G:2017a; Romano.M:2021a). Recently, rest-frame ultraviolet (UV) images (cite: Ribeiro.B:2017a; Duncan.K:2019a; Shibuya.T:2022a) and \[C ii\] 158 $\mathrm{\mu m}$ data cubes (cite: Romano.M:2021a) were able to explore the merger fractions up to $z \sim 5\mbox{--}7$. Although the measured fractions are yet to be converged and depend strongly on galaxy masses, the high merger fraction, $20\mbox{--}80$% at $z\sim5\mbox{--}7$, supports a large number of galaxies that experience major mergers in the early Universe. In terms of the stellar mass assembly, contributions of major mergers are suggested to be comparable to in-situ star formation at $z > 3$ (cite: Duncan.K:2019a; Romano.M:2021a; Duan.Q:2024a). While cosmological zoom-in simulations also support the SFR enhancement by gas-rich mergers at $z > 5$ (cite: Ceverino.D:2018a), the effect of mergers on star formation appears to reduce strongly from the local Universe to $z\sim1\mbox{--}3$ (cite: Silva.A:2018a; Shah.E:2022a).

High angular resolution is key to pushing up the redshift frontier of merger studies. Merging systems at $z\gtrsim5$ are reported from observations of Hubble Space Telescope (HST), James Webb Space Telescope (cite: Gardner.J:2023a), and Atacama Large Millimeter/sub-millimeter Array (ALMA), which have both high angular resolutions and highest sensitivities that can resolve high-redshift galaxies. For example, dusty systems at $z\sim4\mbox{--}7$ corresponding to hyper/ultra luminous infrared galaxies (ULIRGs) sometimes show signatures of galaxy mergers (cite: Oteo.I:2016a; Marrone.D:2018a; Hygate.A:2023a; Bik.A:2024a). Triple mergers have also been observed, such as a dust-free, luminous $\mathrm{Ly\alpha}$ emitter at $z = 6.6$ (cite: Ouchi:2013a) and the \[C ii\]-bright galaxy at $z = 4.6$ (cite: Jones.G:2020a). JWST has recently updated the most distant major merger by spectroscopically confirming a triply-lensed galaxy at $z = 10.17$ that has clumps with different dust attenuation (cite: Hsiao.T:2023a; Hsiao.T:2023b). For a statistical study, JWST has shown that galaxy interactions significantly contribute to the bursty star-formation and strong emission lines in low-mass galaxies at $z\sim5\mbox{--}6$ (cite: Asada.Y:2024a). However, few merging galaxies are observed and detected with multiple bands in both UV and far-infrared (FIR), limiting our ability to interpret the complete properties of distant merging systems.

Multi-wavelength, high angular-resolution observations are essential to examine the complex properties of stars, gas, and dust through UV-to-FIR spectral energy distributions (SEDs) of resolved galaxy components. Red colors of high-redshift galaxies are generally tied with dust attenuation similar to local star-forming galaxies (cite: Bowler.R:2022a), but some galaxies exhibit spatially patchy geometry of UV, line, and dust emission (cite: Tamura.Y:2023b; Colina.L:2023a). This complexity as well as undetermined dust attenuation curves at high redshift strengthens the importance of multi-wavelength observations. Under these circumstances, combinations of JWST and ALMA observations offer valuable constraints on SEDs of spatially resolved galaxies. JWST near-infrared observations uncover resolved stellar and gaseous properties of galaxies even at $z > 6$ (cite: Gimenez-Arteaga.C:2023a; Abdurrouf:2023a). Dust detections with (multiple) ALMA bands help break the degeneracy between the star-formation age and dust attenuation by constraining the dust temperature and FIR $\mathrm{SFR}$ (cite: Bakx.T:2021a; Alvarez-Marquez.J:2023a; Li.J:2024a; Crespo-Gomez.A:2024a). Moreover, these combinations allow us to estimate nebular properties of the interstellar media with optical-to-FIR emission line ratios (cite: Fujimoto.S:2024b; Stiavelli.M:2023a). Thus, the synergy between JWST and ALMA effectively works in revealing the complex properties of merging galaxies during the epoch of reionization (EoR).

This paper presents new observations of a bright merging galaxy system at $z = 7.15$, B14-65666, also known as the Big Three Dragons (cite: Hashimoto.T:2019a), with the Near Infrared Camera (cite: Rieke.M:2023a) on board JWST. These observations were conducted as part of the RIOJA project: “the Reionization and the ISM/Stellar Origins with JWST and ALMA” (cite: Alvarez-Marquez.J:2021b; Hashimoto.T:2023c). Combining ALMA ancillary data with the NIRCam images, we investigate stellar, gaseous, and dusty properties in morphology and star formation of B14-65666. This paper is organized as follows. Section [2.2](#sec:observational-data) describes NIRCam and ancillary data, and reduction processes. Section [3](#sec:analyses) explains analysis tools including image analyses, SED fitting, and photoionization models. Section [\[sec:results\]](#sec:results) presents results about morphology, comparison with ALMA data, and SED fitting. Section [\[sec:discussion\]](#sec:discussion) discusses relations between UV and FIR photometry, a metallicity distribution, and our interpretations about B14-65666. Finally, Section [\[sec:summary\]](#sec:summary) summarizes our conclusions. Throughout this paper, we use the AB magnitude system (cite: Oke.J:1983a) and the flat $\Lambda$CDM cosmology ($\Omega_\mathrm{M} = 0.310$ and $h = H_0/[100\ \mathrm{km\ s^{-1}\ Mpc^{-1}}] = 0.677$; (cite: Planck-Collaboration:2020a)). At $z = 7.15$, $1$ arcsec corresponds to $5.27$ kpc.

# Observations

## Summary of Previous Observations of B14-65666

B14-65666 was first identified as a Lyman-break galaxy from the UltraVISTA survey (cite: Bowler.R:2012a; Bowler.R:2014a). Its UV absolute magnitude of $M_\text{UV} = -22.5$ mag is four times brighter than the characteristic value at $z = 7$ (cite: Finkelstein.S:2015b; Bouwens.R:2021b). Multi-wavelength follow-up observations were conducted to detect the $\mathrm{Ly\alpha}$ emission line (cite: Furusawa.H:2016a), the UV continuum with high-spatial resolution (cite: Bowler.R:2017a), the \[O iii\] 88 $\mathrm{\mu m}$ and \[C ii\] 158 $\mathrm{\mu m}$ emission lines (cite: Hashimoto.T:2019a), and dust continua at 88, 122, and 158 $\mathrm{\mu m}$ (cite: Bowler.R:2018a; Hashimoto.T:2019a; Sugahara.Y:2021a). From the dust continua, the infrared luminosity is estimated to be $\log{L_\text{IR}/L_{\ensuremath{\odot}}} = 11.6^{+0.6}_{-0.3}$ at the dust emissivity of $\beta_\text{d} = 2.0$ (cite: Sugahara.Y:2021a). The galaxy was also observed by ALMA Bands 3 and 7, but it remained undetected in CO(6-5), CO(7-6), \[C i\](2-1) (cite: Hashimoto.T:2023b) and \[N ii\] 122 $\mathrm{\mu m}$ (cite: Sugahara.Y:2021a). The systemic redshift was determined from the \[O iii\] and \[C ii\] emission lines to be $z = 7.1520\pm0.0003$ (cite: Hashimoto.T:2019a). These observations do not provide any evidences towards the presence of an active galactic nucleus (AGN) in the B14-65666 system.

We use our new NIRCam data and the ancillary data to investigate detailed merger properties during EoR.

## JWST and ALMA Observations and Data Reductions

The NIRCam images of B14-65666 were taken on Dec. 20, 2022 with a total exposure time of $644$ s in F200W and F277W, $730$ s in F115W and F356W, and $1675$ s in F150W and F444W. The F115W, F200W, F277W, and F356W observations adopted the BRIGHT1 readout pattern with eight or nine groups and one integration; the F150W and F444W observations adopted the SHALLOW4 with eight groups one integration. All the exposures were four times dithered using the INTRAMODULEBOX pattern. In the RIOJA project, the NIRCam filters were selected such as to trace the continuum emission over the entire $1$–$5$ $\mathrm{\mu m}$ wavelength range with mostly avoiding the contamination by the main optical emission lines. Given the spectroscopic redshift of $z = 7.1520$, the short wavelength channels of F115W, F150W, and F200W correspond to the rest-frame ultraviolet ($1400\mbox{--}2500$ Å). The F277W and F356W bands cover the stellar continua on both sides of the Balmer break without any contamination of strong optical emission lines. The F444W band includes the $\mathrm{H\beta}$ and \[O iii\]$\lambda\lambda$4960,5008 Å emission lines as well as underlying stellar continuum.

The data were reduced using our custom pipeline based on the JWST calibration pipeline version 1.9.4 (cite: Bushouse.H:2023a) under CRDS context jwst_1041.pmap. Our additional reduction steps are: (1) snowballs and wisps removal as described in (cite: Bagley.M:2023a) and (2) background homogenization (including $1/f$-noise subtraction) applied in (cite: Perez-Gonzalez.P:2023b). The pixel scales of the final products for all the filters are set to $0.03$ arcsec$/$pixel. The measured angular resolution and $5\sigma$ depths of the NIRCam filters are listed in Table [1](#tb:size). We note that although the HST image has a comparable depth to the NIRCam ones, we did not use it in this study to avoid a potential systematics among the telescope.

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Band | $\lambda_\text{rest}$ | PSF FWHM | $5\sigma$ Depth |
|  |  | \[arcsec\] |  |
| NIRCam/F115W | $1416$ Å | $0.060$ | $23.3$ $\mathrm{nJy}$ |
| NIRCam/F150W | $1841$ Å | $0.067$ | $7.7$ $\mathrm{nJy}$ |
| NIRCam/F200W | $2441$ Å | $0.076$ | $23.5$ $\mathrm{nJy}$ |
| NIRCam/F277W | $3418$ Å | $0.13$ | $20.4$ $\mathrm{nJy}$ |
| NIRCam/F356W | $4371$ Å | $0.15$ | $19.5$ $\mathrm{nJy}$ |
| NIRCam/F444W | $5424$ Å | $0.16$ | $15.4$ $\mathrm{nJy}$ |
| ALMA/Band8 | $88.84$ $\mathrm{\mu m}$ | $0.39\times0.36$ | $141$ $\mathrm{\mu Jy\ beam^{-1}}$ |
| ALMA/Band7 | $122.6$ $\mathrm{\mu m}$ | $1.17\times0.98$ | $45.5$ $\mathrm{\mu Jy\ beam^{-1}}$ |
| ALMA/Band6 | $158.7$ $\mathrm{\mu m}$ | $0.28\times0.20$ | $42.3$ $\mathrm{\mu Jy\ beam^{-1}}$ |

: Summary of NIRCam and ALMA observations.

Table notes: The rest-frame wavelengths, $\lambda_\text{rest}$, are converted from the pivot wavelengths for NIRCam. The $5\sigma$ depths are computed within $2\times$PSF-FWHM diameter apertures for NIRCam and with a peak rms for ALMA.

The ALMA data used in this work were presented in previous studies. ALMA Bands 6 and 8 data were taken in Cycles 4 (ID 2016.1.00954.S, PI: A. K. Inoue) and 5 (ID 2017.1.00190.S, PI: A. K. Inoue) to target the \[C ii\] 158 $\mathrm{\mu m}$ and \[O iii\] 88 $\mathrm{\mu m}$ emission lines (cite: Hashimoto.T:2019a). ALMA Band 7 data were taken in Cycle 7 (ID: 2019.1.01491.S, PI: A. K. Inoue) to target the \[N ii\] 122 $\mathrm{\mu m}$ emission line (cite: Sugahara.Y:2021a). In all the observations, one of the four spectral windows was placed to observe the targeted lines while the others were for the underlying dust continua. The raw data were reduced with standard scripts on Common Astronomy Software Applications (cite: CASA-Team:2022a). \[O iii\] and \[C ii\] emission-line maps (i.e., moment-0 maps) were created by integrating wavelength ranges of $\simeq600$ $\mathrm{km\ s^{-1}}$ around the line centers after the continuum subtraction (cite: Hashimoto.T:2019a). Dust continuum maps were created using channels that are unaffected by the emission lines. The synthesized beam FWHM is $0.29\ensuremath{''}\times0.23\ensuremath{''}$, $1.15\ensuremath{''}\times0.97\ensuremath{''}$, and $0.39\ensuremath{''}\times0.37\ensuremath{''}$ in Bands 6, 7, and 8 observations with the natural weighting. More information on the observations and data reduction is described in the references above. We did not use ALMA Band 3 data (cite: Hashimoto.T:2023b) in this study because neither continuum nor lines were detected and they do not give strong constraints on the FIR SED. The beam sizes and $5\sigma$ depths for the peak $\text{S}/\text{N}$ of the ALMA observations are listed in Table [1](#tb:size).

Astrometry of the NIRCam images were corrected with stars in the field of view (FoV). In the NIRCam FoV, there exist three stars listed on the Gaia DR3 main catalog (cite: Gaia-Collaboration:2016a; Gaia-Collaboration:2023a). We aligned the NIRCam images to the three Gaia stars, and then we corrected small offsets between the NIRCam images using faint stars. The astrometric uncertainties of the NIRCam images are $< 0.015\ensuremath{''}$. The peak positional accuracy of ALMA data, which can be estimated from the beam size and peak $\text{S}/\text{N}$[^1], is $\sim0.03\ensuremath{''}$ for \[C ii\] 158 $\mathrm{\mu m}$ and \[O iii\] 88 $\mathrm{\mu m}$ line maps and $\sim0.06\ensuremath{''}$ for dust continuum maps at $158$ and $88$ $\mathrm{\mu m}$. As these estimates for the ALMA data are based on an equation for compact sources, the accuracy may be worse for extended sources like B14-65666.

# Analyses

## Image analyses

When comparing different bands of the NIRCam images pixel by pixel, we matched the point spread functions (PSFs) of the images to that of the F444W image by kernel convolution. We constructed effective PSFs following the (cite: Anderson.J:2000a) and (cite: Anderson.J:2016a) methods using `photutils` (cite: Bradley.L:2023a), which construct empirical models by fitting pixel values in images of stars detected with `IRAFStarFinder`. Then, we homogenized the PSFs of the NIRCam images using kernels created by `PyPHER` (cite: Boucaud.A:2016a). We have checked that the PSF homogenization works well using faint stars in FoVs. Finally, the image pixels were resampled using `reproject` to match the F444W image pixels. When comparing the NIRCam and ALMA \[O iii\] images, the PSFs of the NIRCam images are homogenized to the synthesized clean beam (i.e., two-dimensional Gaussian) of the ALMA images following the same procedure. The ALMA image pixels are resampled to match the F444W image pixels.

Photometry was performed with fixed apertures on the PSF-homogenized images and aperture correction was not applied. We chose a circular aperture of $1.8\ensuremath{''}$ in diameter to measure the total photometry of B14-65666, which sufficiently recover all the fluxes according to curve-of-growth plots of the flux density. Because B14-65666 has a complex structure with several components and diffuse emission (see Section [\[sec:results\]](#sec:results) and Figure [\[fig:nircam\]](#fig:nircam)), smaller apertures are used to measure the photometry of these individual components (see Figure [\[fig:o3\]](#fig:o3)). The local sky background computed in an annulus from $0.95\ensuremath{''}$ to $1.95\ensuremath{''}$ were subtracted before the photometry measurements. The photometric uncertainties were estimated from random aperture photometry. We scattered the apertures over the images around B14-65666 where bright objects are masked and we computed the uncertainties as the standard deviation of the aperture-photometry distributions. In addition, the absolute flux uncertainty was included in the photometric uncertainties as a conservative value of $5$% (cite: Rigby.J:2023a)[^2].

## SED fitting

[^1]: Equation (10.7) in ALMA Cycle 10 Technical Handbook: <https://almascience.nao.ac.jp/documents-and-tools/cycle10/alma-technical-handbook>

[^2]: See also “NIRCam Imaging Calibration Status” in JWST User Documentation for the current photometric calibration: <https://jwst-docs.stsci.edu>

We performed SED fitting to the NIRCam photometry using Bayesian Analysis of Galaxies for Physical Inference and Parameter EStimation (cite: Carnall.A:2018a). We tested SED fitting with and without ALMA fluxes to see changes in obtained best-fit parameters. The ALMA \[O iii\] 88 $\mathrm{\mu m}$ line and continuum fluxes were taken from (cite: Hashimoto.T:2019a). We note that these ALMA fluxes were measured by fitting two Gaussian components to the line and continuum maps, which differs from the aperture photometry for the NIRCam images. The redshift is fixed at $z = 7.1520$ in the fitting.

The fitting parameters are the star-formation age $t_\text{SF}$, the stellar mass $M_{*}$, the ionization parameter $U$, the *V*-band dust attenuation $A_\text{V}$, the stellar metallicity $Z_{*}$, and the mass of an old stellar component $M_\text{old}$. The star-formation history of B14-65666 is simply assumed to be constant for $t_\text{SF}$ down to $z = 7.1520$. We also tested different star-formation histories, but the fitting results were insensitive to different star-formation histories (Appendix [\[sec:A1\]](#sec:A1)), because B14-65666 is dominated by a young bursty star formation of $\sim10$ Myr timescale. The gas-phase metallicity is assumed to be identical to the stellar metallicity. The ionization parameter $U$ controls nebular emission-line ratios, which is implemented using a photoionization code CLOUDY (cite: Ferland:1998a; Ferland.G:2017a). The hydrogen density in the CLOUDY models is fixed to be $n_\text{H} = 100$ $\mathrm{cm^{-3}}$ in `Bagpipes`. The dust attenuation curve follows the (cite: Calzetti:2000) law. In addition, considering that B14-65666 is a major merger, stellar components older than recent starbursts should exist. To constrain the mass of the old stellar components, we added another constant star formation lasting for $500$ Myr, from $600$ Myr ago to $100$ Myr ago with respect to $z = 7.15$, which does not strongly contribute to UV continuum and emission-line fluxes. This selected star-formation timescale is arbitrary, but changes of this timescale do not affect our conclusion. The stellar metallicity of the old components is fixed to $\ensuremath{Z_\text{star}}= 0.5$ $Z_\text{\(\odot\)}$ (cite: Asplund.M:2021a) to reduce the number of free parameters, but we checked that results do not vary significantly with the assumed $Z_\text{star}$ value. The best-fit parameters are computed as the median of the posterior distributions. The $1\sigma$ fitting uncertainties are evaluated from the $16$ and $84$ percentiles of the posterior distributions.

For FIR SED, we added fitting parameters of the minimum stellar intensity $\mathcal{U}_\mathrm{min}$ and the fraction $\gamma$ of the dust mass heated by $\mathcal{U} > \ensuremath{\mathcal{U}_\mathrm{min}}$. `Bagpipes` has adopted the (cite: Draine.B:2007a) dust emission models. Instead of the originally adopted ones, we used the updated version (cite: Draine.B:2014a) implemented in the `CIGALE` SED fitting code (cite: Boquien.M:2019a), which allows up to $\ensuremath{\mathcal{U}_\mathrm{min}}= 50$. The model parameters other than $\mathcal{U}_\mathrm{min}$ and $\gamma$ were fixed: the power-law index of the stellar intensity $\alpha_\mathcal{U} = 2$, the maximum stellar intensity $\mathcal{U}_\text{max} = 10^7$, and the PAH mass fraction $q_\text{PAH} = 2.5$%. The former two fixed parameters are appropriate to reproduce high-redshift galaxies (cite: Burgarella.D:2022b) as well as nearby galaxies (cite: Draine.B:2014a) and the latter $q_\text{PAH}$ was fixed because our observations are insensitive to mid-IR wavelengths. We note that while we added two fitting parameters for the FIR SED, dust continua are constrained at only $2\mbox{--}3$ bands. Thus, adding ALMA dust continua in the SED fitting is not quite effective to constrain the stellar properties better (as shown in Section [\[sec:result-sed-fitting\]](#sec:result-sed-fitting)), but it helps estimate the dust temperature necessary for the energy balance between dust attenuation and emission.

For input stellar models, the Binary Population and Spectral Synthesis code (cite: Eldridge.J:2017a) version 2.3 (cite: Byrne.C:2022a) was used. `BPASS` includes effects of binary populations, which are important to reproduce strong \[O iii\] emission lines observed at high redshift (cite: Sugahara.Y:2022a). Specifically, the version 2.3 implements high $\alpha/\text{Fe}$ cases, reflecting abundance patterns found at $z \gtrsim 2$ dominated by core-collapse supernovae (cite: Steidel:2014; Steidel:2016). This enhancement of $\alpha$ elements is also key to reproducing \[O iii\] emission line strengths and hard UV spectral slopes at high redshift (cite: Shapley.A:2019a; Sugahara.Y:2022a). We used the case of $\varDelta \log(\alpha/\text{Fe}) = +0.6$, where the oxygen abundance is almost the solar value $12 + \log\ensuremath{\text{O}/\text{H}}= 8.69$ (cite: Asplund.M:2021a) at $Z = 0.02$ (cite: Byrne.C:2022a). The adopted initial mass function (IMF) is a (cite: Kroupa:2001) IMF in the mass range from $0.1$ to $300$ $\mathrm{M_\ensuremath{\odot}}$. Their choice of the upper mass limit leads to a 45% higher ionizing flux and stronger hydrogen recombination lines than a choice of an upper limit of $100$ $\mathrm{M_\ensuremath{\odot}}$ (cite: Stanway.E:2016a). The nebular-continuum and emission-line models are generated based on these stellar models.

## Photoionization models with CLOUDY

In our emission-line modeling, we used a photoionization code CLOUDY version 17.02 (cite: Ferland:1998a; Ferland.G:2017a). We note that our setup is more flexible than the one used in the `Bagpipes` SED fitting, by including an additional free parameter of $n_\text{H}$. We assumed a plane-parallel geometry under the constant pressure and elemental and dust-grain abundances in the H ii regions that are stored in CLOUDY. For the helium abundance, we simply added stellar yields to Big Bang nucleosynthesis as a function of the gas-phase metallicity (cite: Groves.B:2004a). The input ionizing spectra were constructed from the `BPASS` version 2.3 and the stellar metallicity is assumed to be identical to the gas-phase metallicity. The star-formation history is set to be a $10$-Myr constant star formation. Adopted variable parameters are the ionization parameter $U$ and hydrogen density $n_\text{H}$ at the illuminated surface, and the gas-phase metallicity $Z_\text{gas}$. The calculations stop at the edge of the H ii region where the electron fraction is $10^{-2}$. The output emission-line fluxes are normalized by the $\mathrm{H\beta}$ line fluxes.

# Results

## Morphology, Colors, and Optical \[O iii\] Line Map

B14-65666 consists of two bright components: galaxies E (east) and W (west), which were referred to as the clumps A and B in (cite: Hashimoto.T:2019a), respectively. (cite: Hashimoto.T:2019a) reported that these two galaxies have similar UV, IR, \[O iii\] 88 $\mathrm{\mu m}$, and \[C ii\] 158 $\mathrm{\mu m}$ luminosities within a factor of two and their line-of-sight velocity separation is $\simeq200$ $\mathrm{km\ s^{-1}}$. For these reasons, B14-65666 is thought to be a major merger at $z = 7.1520$. The NIRCam observations provide us with morphological evidences for the scenario of the major merger. Figure [1](#fig:nircam) shows the NIRCam-band color image and the individual images in the six NIRCam filters of the two galaxies of B14-65666. The two galaxies are apparently separated in the rest-frame optical wavelengths, ruling out a scenario that the two bright components are star-forming regions in a rotating stellar disk.

The NIRCam imaging clearly illustrates that the galaxies E and W have different morphology. The galaxy E has a bright compact core. This compact core is unresolved even in the F115W image, which has the highest angular resolution in the images used in this work. Under an assumption that the core of the galaxy E has an exponential surface brightness profile, the deconvolved effective radius in F115W is $r_\text{e} < 0.016$ arcsec ($85$ pc) at the $2\sigma$ significance limit. This core effective radius is smaller than the average effective radii ($0.7\mbox{--}1$ kpc at rest-frame optical) of observed and simulated galaxies at $M_{*}\sim10^9$ $\mathrm{M_\ensuremath{\odot}}$ at $z = 7$ (cite: Costantin.L:2023a; Ormerod.K:2024a).

In contrast, the galaxy W is elongated from southeast to northwest. This feature is seen in all the NIRCam images and its length is $\simeq 0.3$ arcsec ($1.5$ kpc). Such elongated morphology look like tidal tails and it is often observed under tidal effect like major mergers in the local Universe (cite: Borne.K:2000a; Garcia-Marin.M:2009a). In addition, the F115W and F150W images suggest a clumpy internal structure of the galaxy W, which may consist of three clumps. These compactness and clumpiness of B14-65666 agree with rest-frame UV clumps in bright high-redshift galaxies revealed by recent JWST observations (cite: Treu.T:2023a; Trussler.J:2023a; Marques-Chaves.R:2024a) and numerical simulations (cite: Mandelker.N:2017a; Ceverino.D:2023a; Nakazato.Y:2024a).

In addition to the compact and clumpy structure, the NIRCam images have identified some extended emission around the galaxy E. This emission is clearly seen in the F444W image and consists of two diffuse sub-components north and south-east of the galaxy E (Figure [1](#fig:nircam)). Actually, the spatially extended components were already suggested in the HST F140W image (cite: Bowler.R:2017a) and the \[O iii\] 88 $\mathrm{\mu m}$ line map (cite: Hashimoto.T:2019a), but they were not explicitly reported in the literature due to low $\text{S}/\text{N}$. In the NIRCam imaging, the diffuse components are confirmed at $\ensuremath{ \text{S}/\text{N}}> 6$ in the F277W, F356W, and F444W bands and they are also suggested at lower significance levels ($\ensuremath{ \text{S}/\text{N}}\simeq 1\mbox{--}2$) in the F150W and F200W images. The F444W bandpass includes $\mathrm{H\beta}$ and \[O iii\]$\lambda\lambda$4960,5008 emission lines. The F277W bandpass samples shorter wavelengths than the Balmer break, at which the stellar continuum by old stars becomes faint. Therefore, these multiple band detections imply that the diffuse sub-components are bright in young stellar continuum or nebular emission (e.g., the \[O iii\] and \[O ii\]$\lambda\lambda$3727,3730 Å lines and nebular continuum). Given that B14-65666 is a major merging system, we assumed that they are likely to be tidal tails stripped from the galaxies (cite: Garcia-Marin.M:2009a).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Aperture | F115W | F150W | F200W | F277W | F356W | F444W | Band8$^{\dagger}$ | Band7$^{\dagger\dagger}$ | Band6$^{\dagger}$ | \[OIII\]88$^{\dagger}$ |
|  | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{\mu Jy}$\] | \[$\mathrm{Jy~km~s^{-1}}$\] |
| Total | $0.374\pm0.100$ | $0.447\pm0.043$ | $0.429\pm0.112$ | $0.661\pm0.047$ | $0.705\pm0.046$ | $1.346\pm0.070$ | $470\pm128$ | $218\pm19$ | $130\pm25$ | $1.50\pm0.18$ |
| E | $0.159\pm0.060$ | $0.162\pm0.023$ | $0.261\pm0.051$ | $0.343\pm0.027$ | $0.355\pm0.024$ | $0.773\pm0.040$ | $208\pm83$ | \- | $41\pm23$ | $0.92\pm0.14$ |
| W | $0.225\pm0.045$ | $0.298\pm0.019$ | $0.187\pm0.040$ | $0.298\pm0.022$ | $0.305\pm0.020$ | $0.496\pm0.026$ | $246\pm73$ | \- | $87\pm26$ | $0.57\pm0.09$ |
| E-core | $0.107\pm0.022$ | $0.128\pm0.008$ | $0.163\pm0.018$ | $0.180\pm0.011$ | $0.167\pm0.010$ | $0.440\pm0.022$ | \- | \- | \- | \- |
| W-core | $0.203\pm0.023$ | $0.232\pm0.013$ | $0.186\pm0.019$ | $0.215\pm0.013$ | $0.220\pm0.012$ | $0.349\pm0.018$ | \- | \- | \- | \- |
| N-tail | $0.042\pm0.025$ | $0.016\pm0.007$ | $0.042\pm0.020$ | $0.057\pm0.009$ | $0.080\pm0.009$ | $0.116\pm0.008$ | \- | \- | \- | \- |
| S-tail | $-0.005\pm0.038$ | $0.014\pm0.011$ | $0.050\pm0.033$ | $0.091\pm0.014$ | $0.091\pm0.011$ | $0.161\pm0.011$ | \- | \- | \- | \- |

: NIRCam photometry and ALMA measurements of B14-65666 components.

Table notes: $^{\dagger}$(cite: Hashimoto.T:2019a), $^{\dagger\dagger}$(cite: Sugahara.Y:2021a)

Table [\[tb:photometry\]](#tb:photometry) lists measured photometry of the total and the galaxies E and W. The table also lists photometry of the tails (N-tail and S-tail) and the cores of the galaxies E and W (E-core and W-core). The applied apertures are shown in the left panel of Figure [\[fig:o3\]](#fig:o3). Our measurements of the total photometry are consistent with the values on the COSMOS2020 catalog (cite: Weaver.J:2022a). The F115W magnitudes of the galaxies E and W are measured to be $25.9^{+0.5}_{-0.3}$ and $25.5^{+0.2}_{-0.2}$ mag, respectively, corresponding to $M_\text{UV} = -21.1^{+0.5}_{-0.3}$ and $-21.5^{+0.2}_{-0.2}$ mag. These magnitudes are similar to and brighter than the characteristic magnitude, $M^{*}_\text{UV} \simeq -21.0$ mag, of the UV luminosity function at $z\sim7$ (cite: Finkelstein.S:2015b; Bouwens.R:2021b). From UV to optical wavelengths, the galaxy E has a redder color than the galaxy W. The tails largely contribute this red color of the galaxy E, as shown in Figure [\[fig:nircam\]](#fig:nircam). This color difference suggests that the galaxies E and W have different stellar and dust properties.

The middle panel of Figure [\[fig:o3\]](#fig:o3) shows the optical \[O iii\] line map, which indicates strong \[O iii\] emission at the cores. The E-core and W-core exhibit integrated \[O iii\] fluxes of $(4.3 \pm 0.4) \times10^{-17}$ and $(2.0 \pm 0.3) \times10^{-17}$ $\mathrm{erg\ s^{-1}\ cm^{-2}}$, respectively. Being regarded as a proxy of star formation, this strong \[O iii\] emission indicates nuclear starbursts likely induced by the galaxy interaction, as seen in major mergers in the local Universe (cite: Ellison.S:2008a). The right panel of Figure [\[fig:o3\]](#fig:o3) shows a map of the rest-frame \[O iii\] equivalent width ($\text{EW}_{0}$). The E-core and W-core exhibit $\text{EW}_{0}([\mbox{O\,{\sc iii}}]) \sim 2050\pm290$ and $740\pm170$ Å, respectively, which are at the higher end of the distribution of \[O iii\] emitters at $z = 5\mbox{--}7$ (cite: Matthee.J:2023a; Boyett.K:2024a). In the tails, the \[O iii\] fluxes are detected at the $3\mbox{--}4\sigma$ significance levels, although this value may be overestimated because their red color may reflect their red optical continuum slopes, which is different from our assumption. The obtained \[O iii\] fluxes and equivalent widths are listed in Table [\[tb:properties\]](#tb:properties).

## NIRCam and ALMA imaging: Stellar versus dust distribution

The combination of the new NIRCam images with archival high angular-resolution ($< 0.4\ensuremath{''}$) ALMA data provides us with an unique opportunity to investigate the detailed stellar, ionized, and dust structure in an interacting system at $z > 7$. Figure [\[fig:alma\]](#fig:alma) compares the NIRCam image, and ALMA line and dust maps. The NIRCam image is a composite of all the bands, except for F444W, to exhibit the stellar continuum. All the ALMA detections overlap the positions of the galaxies E and W, showing no spatial offsets between the UV-to-optical and FIR dust and line emission. The \[C ii\] 158 $\mathrm{\mu m}$ and \[O iii\] 88 $\mathrm{\mu m}$ emission lines in the galaxy E are $1\mbox{--}1.5$ times as bright as those in the galaxy W (cite: Hashimoto.T:2019a). This trend is qualitatively the same as the one seen in our \[O iii\]$\lambda\lambda$4960,5008 line map (Table [1](#tb:properties)). In contrast to the emission lines, the dust emission at $88$ and $158$ $\mathrm{\mu m}$ is brighter in the galaxy W than in the galaxy E (cite: Hashimoto.T:2019a)[^1]. This dust spatial distribution might indicate that the galaxy W experiences dustier star-formation than the galaxy E. As denoted in Section [\[sec:result-morphology\]](#sec:result-morphology), however, the galaxy W presents a bluer UV color than the galaxy E, which is inconsistent with a previous finding that dust emission tend to be accompanied with red components in $z > 6$ galaxies (cite: Bowler.R:2022a). We will come back to this point in Section [\[sec:irx-beta\]](#sec:irx-beta).

The tails are detected only in the \[O iii\] 88 $\mathrm{\mu m}$ line map, whereas they appear neither in the \[C ii\] 158 $\mathrm{\mu m}$ line map nor in the dust maps. NIRCam detects the tails in the stacked continuum image, generated using the bands from F115W to F356W, and the \[O iii\]$\lambda\lambda$4960,5008 line map. However, the tails are faint in the rest-frame UV filters (e.g., F150W), indicating red continuum slope from UV to optical. The presence of continuum and line emission implies that the tails are actively forming stars, but the red continuum slope and the no emission of dust continua suggest a complex nature of the tails.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Components | Aperture diameter | Flux(\[O iii\]) | EW$_{0}([\mbox{O\,{\sc iii}}])$ | SFR$_{0}$ | sSFR$_{0}$ | SFR$_\text{10Myr}$ | $\beta_\text{UV}$ |
|  | \[$\mathrm{arcsec^{2}}$\] | \[$\mathrm{10^{-17}\,erg\,s^{-1}\,cm^{-2}}$\] | \[$\mathrm{\mathring{A}}$\] | \[$\mathrm{M_{\odot}\,yr^{-1}}$\] | \[$\mathrm{Gyr^{-1}}$\] | \[$\mathrm{M_{\odot}\,yr^{-1}}$\] |  |
| Total | $1.8 \times1.8$ | $10.1\pm1.3$ | $1140\pm220$ | $225^{+71}_{-56}$ | $52^{+56}_{-28}$ | $207^{+65}_{-51}$ | $-1.57^{+0.11}_{-0.13}$ |
| E | $1.4 \times0.80$ | $6.6\pm0.7$ | $1480\pm260$ | $178^{+52}_{-39}$ | $53^{+26}_{-20}$ | $178^{+50}_{-39}$ | $-1.18^{+0.15}_{-0.16}$ |
| W | $1.1 \times0.66$ | $2.6\pm0.4$ | $750\pm170$ | $37^{+12}_{-8}$ | $23^{+15}_{-11}$ | $37^{+12}_{-8}$ | $-2.19^{+0.11}_{-0.09}$ |
| E-core | $0.44 \times0.44$ | $4.3\pm0.4$ | $2050\pm290$ | $180^{+113}_{-58}$ | $506^{+253}_{-182}$ | $34^{+13}_{-9}$ | $-1.78^{+0.11}_{-0.13}$ |
| W-core | $0.44\times0.44$ | $2.0\pm0.3$ | $740\pm170$ | $29^{+13}_{-7}$ | $27^{+28}_{-12}$ | $29^{+14}_{-6}$ | $-2.24^{+0.13}_{-0.10}$ |
| N-tail | $0.70\times0.40$ | $0.6\pm0.2$ | $580\pm260$ | \- | \- | \- | \- |
| S-tail | $1.0\times0.50$ | $1.1\pm0.2$ | $960\pm340$ | \- | \- | \- | \- |

: Observed and Physical Properties of Components.

Table notes: The flux(\[O iii\]) and EW$_{0}([\mbox{O\,{\sc iii}}])$ are the line fluxes and rest-frame equivalent widths derived from the optical \[O iii\]$\lambda\lambda$4960,5008 line map (Figure [\[fig:o3\]](#fig:o3)) within the component apertures. SFR$_{0}$ is the instant star-formation rate ($\ensuremath{\mathrm{SFR}}_0 = M_{*}/t_\text{SF}$) and SFR$_\text{10Myr}$ is the star-formation rate averaged in 10 Myr, that is, $\ensuremath{\mathrm{SFR}}_\text{10Myr} = M_* (< 10\ \text{Myr})/10\ \text{Myr}$. The specific SFR$_{0}$ is defined as $1/t_\text{SF}$. $\beta_\text{UV}$ is the UV spectral slope.

## SED fitting of total and resolved components

[^1]: The peak position of the $158$ $\mathrm{\mu m}$ dust emission is shifted to the east of the galaxy W beyond the ideal astrometric uncertainty (Section [\[sec:observational-data\]](#sec:observational-data)). The origin of this shift is unclear, but it might be ALMA astrometric uncertainties poorer than the ideal one.

We performed SED fitting combining the NIRCam and ALMA datasets for the entire system and the resolved galaxy components of B14-65666. The apertures for each component is illustrated in the left panel of Figure [\[fig:o3\]](#fig:o3) and the NIRCam and ALMA fluxes used in the SED fitting are summarized in Table [\[tb:photometry\]](#tb:photometry). The best-fit SEDs and measured physical parameters are presented in Figure [\[fig:sed\]](#fig:sed) and Table [1](#tb:sed), respectively. The best-fit parameters are given as $2\sigma$ upper/lower limits when the peak of the posterior distributions is near the edge of the parameter boundaries (see Appendix [3](#sec:A1)).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Components | $t_\mathrm{SF}$ | $\log{M_*}$ | $A_\mathrm{V}$ | $\log U$ | $Z_{*}$ | $\log{M_\mathrm{old}}$ | $\mathcal{U_\mathrm{min}}$ | $\gamma$ |
|  | \[$\mathrm{Myr}$\] | \[$\mathrm{\log M_{\odot}}$\] | \[$\mathrm{mag}$$\mathrm{\left( \mathrm{AB} \right)}$\] |  | \[$\mathrm{Z_{\odot}}$\] | \[$\mathrm{\log M_{\odot}}$\] |  |  |
| NIRCam + ALMA data$^{\(\dagger\)}$ |  |  |  |  |  |  |  |  |
|  Total | $35^{+20}_{-12}$ | $9.78^{+0.16}_{-0.18}$ | $0.78^{+0.07}_{-0.06}$ | $-2.09^{+0.58}_{-0.34}$ | $0.21^{+0.05}_{-0.04}$ | $<9.59$ | $>10.45$ | $0.88^{+0.07}_{-0.07}$ |
| E | $<93$ | $9.55^{+0.19}_{-0.20}$ | $0.98^{+0.08}_{-0.07}$ | $-2.06^{+0.61}_{-0.34}$ | $0.19^{+0.04}_{-0.04}$ | $<9.55$ | $>16.33$ | $>0.83$ |
| W | $22^{+13}_{-8}$ | $9.09^{+0.16}_{-0.18}$ | $0.46^{+0.08}_{-0.06}$ | $-1.95^{+0.54}_{-0.39}$ | $0.32^{+0.06}_{-0.05}$ | $<8.95$ | $>7.61$ | $<0.80$ |
| Only NIRCam data$^{\(\natural\)}$ |  |  |  |  |  |  |  |  |
| Total | $18^{+21}_{-9}$ | $9.61^{+0.25}_{-0.27}$ | $0.86^{+0.11}_{-0.11}$ | $-2.14^{+0.47}_{-0.34}$ | $0.26^{+0.09}_{-0.08}$ | $<9.68$ | \- | \- |
| E | $<53$ | $9.51^{+0.17}_{-0.14}$ | $1.21^{+0.13}_{-0.14}$ | $-2.19^{+0.42}_{-0.30}$ | $0.28^{+0.09}_{-0.08}$ | $<9.28$ | \- | \- |
| W | $42^{+39}_{-17}$ | $9.22^{+0.17}_{-0.17}$ | $0.34^{+0.12}_{-0.09}$ | $-2.08^{+0.54}_{-0.37}$ | $0.24^{+0.09}_{-0.08}$ | $<8.95$ | \- | \- |
| E-core | $<5$ | $8.53^{+0.15}_{-0.13}$ | $0.72^{+0.15}_{-0.14}$ | $-1.82^{+0.49}_{-0.29}$ | $0.33^{+0.11}_{-0.10}$ | $<8.87$ | \- | \- |
| W-core | $35^{+29}_{-18}$ | $9.02^{+0.19}_{-0.20}$ | $0.30^{+0.14}_{-0.10}$ | $-1.99^{+0.67}_{-0.38}$ | $0.26^{+0.10}_{-0.10}$ | $<8.89$ | \- | \- |

: Results of the SED fitting.

Table notes: The fitting parameters are described in Section [\[sec:sed-fitting\]](#sec:sed-fitting). The best-fit values and $1\sigma$ uncertainties are computed from a 50 percentile and 16 and 84 percentiles of the posterior distributions, respectively. The upper and lower limits are the $2\sigma$ limits, that is, 97.5 and 2.5 percentiles of the posterior distributions, respectively. $^{\dagger}$ The results for the NIRCam and ALMA photometry. $^{\natural}$ The results only for the NIRCam photometry. The dust emission parameters $\mathcal{U_\text{min}}$ and $\gamma$ are not used in the fits.

### Entire Merging System

The SED fit to the integrated flux supports that the B14-65666 system is a young starburst, regardless of whether including the ALMA data. In the case without the ALMA data, the star-formation age and the stellar mass are $t_\text{SF} = 20^{+20}_{-10}$ Myr and $\log M_{*}/M_{\ensuremath{\odot}} = 9.6^{+0.3}_{-0.3}$, and then, instant star-formation rate is $\ensuremath{\mathrm{SFR}}_0 = M_{*}/t_\text{SF} = 230^{+70}_{-60}$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$. The ionization parameter is $\log U = -2.1^{+0.5}_{-0.3}$. This young starburst with the high ionization parameter gives rise to strong \[O iii\] emission lines that can explain the F444W excess. The relatively red stellar continuum even with the young starburst is attributed to the dust attenuation of $A_{V} = 0.86^{+0.1}_{-0.1}$ mag. The old stellar component is constrained to be $\log M_{*}/M_{\ensuremath{\odot}} < 9.7$ at the $2\sigma$ upper limit, which contributes the estimated continuum at F444W by up to $10$%. This upper limit is comparable to the stellar mass formed by the present star-formation. Thus, the starburst induced by the major merger formed a stellar mass comparable to or higher than the old stellar mass built before the on-going merger.

The SED fitting including the dust continua shows higher $\mathcal{U}_\mathrm{min}$ and $\gamma$ values than those of nearby galaxies (cite: Draine.B:2007a). Such high $\mathcal{U}_\mathrm{min}$ and $\gamma$ were also obtained for UV-selected galaxies at $z > 4.5$ (cite: Burgarella.D:2022b), indicating the necessity of high dust temperature to explain the FIR dust emission in high-redshift galaxies. The characteristic dust temperature[^1], derived from Equation (33) in (cite: Draine.B:2007a) and Equation (13) in (cite: Draine.B:2014a), is $T_\text{d, char} \simeq 18 \langle \mathcal{U} \rangle ^{1/6}\,\text{K} = 48^{+2}_{-3}$ K, which is consistent with the dust temperature obtained from the modified blackbody fitting (cite: Sugahara.Y:2021a). Although including the ALMA data slightly decreases the uncertainties of the best-fit dust attenuation and stellar metallicity, the changes in the best-fit stellar properties are insignificant.

Previous analyses of the entire properties of B14-65666 yielded stellar masses that are less than one-third of the one presented in this work (cite: Bowler.R:2018a; Hashimoto.T:2019a). On the other hand, the instant $\ensuremath{\mathrm{SFR}}_0$ that they obtained are consistent with our estimate (cite: Hashimoto.T:2019a). The stellar mass discrepancy is because of the differences on the IRAC and NIRCam photometry, where IRAC flux densities were $1.5\mbox{--}2$ times as low as the NIRCam flux densities at $3.6$ and $4.4$ $\mathrm{\mu m}$. We note again that our new photometry agrees with that in the COSMOS2020 catalog, which is also higher than the previous photometry at $3.6$ $\mathrm{\mu m}$ and $4.5$ $\mathrm{\mu m}$.

### Resolved components

The high angular resolution of the NIRCam imaging enables us to perform the SED fitting to each of the galaxy components. Figure [\[fig:sed\]](#fig:sed) makes it clear that the galaxies E and W have different colors in the rest-frame UV-to-optical wavelengths. In the cases without the ALMA data, they are inferred as the young starbursts with ages of $< 53$ Myr and $40^{+40}_{-20}$ Myr, respectively, similar to the total. The $\ensuremath{\mathrm{SFR}}_{10 \text{Myr}}\ ( = M_{*}( < 10\, \text{Myr})/10\, \text{Myr})$ of the galaxy E ($180^{+50}_{-40}$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$) is $\simeq4$ times as high as that of the galaxy W ($40^{+10}_{-10}$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$). Moreover, the galaxy E is expected to have $\gtrsim0.5$ mag stronger dust attenuation than the galaxy W. These results reflect a dusty, bursty phase of the galaxy E, which is also supported by the strong F444W excess, i.e., the highest \[O iii\] line strength at the core of the galaxy E (Section [\[sec:result-morphology\]](#sec:result-morphology)). In the SED fitting including the ALMA data, the \[O iii\] 88 $\mathrm{\mu m}$ emission line fluxes help more strictly constrain the metallicity of the galaxies; the galaxy E exhibits a lower stellar metallicity than the galaxy W while they have a similar metallicity in the SED fitting without the ALMA data. These metallicity constraints originate from better constraints on the gas-phase metallicity by the optical-to-FIR \[O iii\] line ratios. Both of the galaxies show small Balmer jumps (or inverse Balmer break), a flux excess at wavelengths shorter than $4000$ Å caused by the nebular continuum, which is especially strong for the galaxy E. The contribution of this nebular continuum and \[O ii\]$\lambda\lambda$3727,3730 emission lines help to boost the F277W flux at a level similar to that of the F356W filter. The sum of the stellar masses of the galaxies is $\log M_{*} / M_{\ensuremath{\odot}} \simeq 9.68$, which is comparable to the stellar mass derived from the total photometry. We note that the old stellar component ($M_\text{old}$), which is frequently missed in modeling only with young starburst populations (cite: Roberts-Borsani.G:2020b; Gimenez-Arteaga.C:2023a), may contribute up to a factor of two to the total stellar mass as discussed in the previous section. Finally, the stellar-mass ratio of the galaxies E and W is estimated to be 3:1 to 2:1. This mass ratio is comparable to the dynamical mass ratio of the galaxy E ($5.7\pm1.6\times10^{10}$ $\mathrm{M_\ensuremath{\odot}}$) to the galaxy W ($3.1\pm1.1\times10^{10}$ $\mathrm{M_\ensuremath{\odot}}$) that are inferred from the \[O iii\] 88 $\mathrm{\mu m}$ line widths on the assumption of the virial theorem (cite: Hashimoto.T:2019a). Thus, this study has revealed that B14-65666 is surely a major merger in terms of the stellar mass ratio of the galaxies, while previous studies identified it from the luminosity ratio.

In the FIR SED, it is notable that the galaxies E and W have different peaks of the dust continua. The NIRCam and ALMA observations have shown that the galaxy E has redder UV spectral slope while the galaxy W exhibits higher dust-continuum flux densities. The SED fitting explains these observations with a difference of the dust temperatures. In particular, the galaxy E requires so high $\mathcal{U}_\mathrm{min}$ and $\gamma$ that their probability distribution functions reach the maximum values of their permitted parameter ranges. The characteristic dust temperatures are $T_\text{d, char} = 50^{+1}_{-2}$ and $40^{+4}_{-3}$ K for the galaxies E and W, respectively. We will further discuss relations between the UV and FIR light in Section [1.1](#sec:irx-beta).

For finer resolved analyses, we divided the system into the cores of the galaxies and the tails in the galaxy E. We did not include the ALMA data in these SED fittings, which have relatively lower angular resolution. The panel (c) of Figure [\[fig:sed\]](#fig:sed) depicts the observed SED and best-fit spectra for the E-core and W-core. The W-core has a similar SED shape to the galaxy W and is $10\mbox{--}30$% fainter than it; this similarity means that the W-core is dominant in the SED of the galaxy W. On the other hand, the E-core is twice as faint as the galaxy E at the long wavelength channels. The obtained best-fit age is very young, $< 5$ Myr, at the $2\sigma$ upper limit and the stellar mass is $\simeq1.0$ dex lower than that of the galaxy E. As shown in the panels (b) and (c), there are a $> 0.4$ dex difference in the best-fit stellar continua at wavelengths longer than the Balmer jump. These differences indicate that the red tails strongly affect the SED of the galaxy E at the rest-frame optical wavelengths. One possible scenario to interpret this result might be that the galaxy E is composed of the dusty compact starbursts at the nucleus and the older stars in the tails which dominate the stellar mass. However, the non-detections in the F115W, F150W, and F200W bands of the tails make it challenging to understand the origin of their red color by solving the degeneracy between the old stellar populations, dust attenuation, and strong emission lines (Figure [\[fig:sed\]](#fig:sed)). Detailed properties of the tails will be estimated by including emission lines taken in approved JWST NIRSpec and MIRI observations.

# Discussion

## IRX–$\beta_\text{UV}$ relation

The NIRCam and ALMA data presented so far have demonstrated the complex stellar and ISM structure of the system B14-65666.

While the galaxy W is bluer than the galaxy E in the rest-frame UV (Figure [\[fig:sed\]](#fig:sed)), it exhibits brighter dust emission (Figure [\[fig:alma\]](#fig:alma)). This originates from different properties of star formation and dust attenuation between the galaxies E and W. The SED fitting in Section [\[sec:result-sed-fitting\]](#sec:result-sed-fitting) has suggested the different dust temperature as the origin, but there are other physical mechanisms including assumptions of the dust attenuation curve.

We investigate the relation between the infrared excess ($\text{IRX} = L_\text{IR}/L_\text{UV}$) and the UV spectral slope $\beta_\text{UV}$ to study whether the discrepancy between the UV colors and dust emission is due to the dust attenuation curve. We computed the monochromatic rest-frame UV luminosity $L_\text{UV}$ and $\beta_\text{UV}$ from the best-fit SED models derived without the ALMA data. The UV luminosity was computed from the UV continuum as $L_\text{UV} = \lambda L_{\lambda}$ at $\lambda = 1600$ Å. The UV slope was obtained by linear fitting to the UV continuum within the wavelength windows proposed by (cite: Calzetti.D:1994a). The measurement uncertainties were propagated from the fitting uncertainties; we measured values from the 500 SED models derived from the parameter posterior distributions and estimated uncertainties from the measurement distribution. The IR luminosity $L_\text{IR}$ was taken from (cite: Hashimoto.T:2019a), who estimated it by the modified blackbody fitting under the assumption of the dust temperature of $T_\text{d} = 48$ K and the dust emissivity of $\beta_\text{d} = 2.0$. This assumed dust temperature agrees with the characteristic dust temperature $T_\text{d, char}$ of the entire system that has been derived in the SED fitting.

The obtained IRX values of the entire system (total) and both of the galaxies are similar, $\log \text{IRX} \simeq 0.7$. However, the $\beta_\text{UV}$ values range from $\ensuremath{\beta_\text{UV}}= -2.2$ (galaxy W) to $-1.2$ (galaxy E). The UV slope $\beta_\text{UV}$ depends on stellar and dust properties including age, dust composition, and the stellar-and-dust geometry. Therefore, the variation in $\beta_\text{UV}$ at a given IRX supports a spatial variation of stellar and dust properties between the components.

Previously (cite: Bowler.R:2022a) measured the IRX and $\beta_\text{UV}$ values for B14-65666. In Figure [1](#fig:irxb), we plotted their data points after correcting the IRX values for $T_\text{d} = 48$ K and $\beta_\text{d} = 2.0$. Compared with their values, our measurements are systematically redder in $\beta_\text{UV}$. Although the origin of the systematics is unclear, the $\beta_\text{UV}$ difference would be caused by different spatial resolution. (cite: Bowler.R:2022a) used UltraVISTA images with the spatial resolutions of $\sim 0.7\ensuremath{''}$, much coarser than those of our NIRCam images, and they resolved objects with `TPHOT` (cite: Merlin.E:2015a) based on an HST image. Thus, unexpected systematics may be included in their rest-frame UV photometry. This comparison underlines the power of high resolution for spatially resolved studies.

The IRX–$\beta_\text{UV}$ relations are connected with attenuation curves under the energy balance between absorption and re-radiation by dust (cite: Meurer.G:1999a). Canonical relations are parameterized with attenuation curves, for example, for local starbursts (cite: Meurer.G:1999a; Overzier.R:2011a; Takeuchi.T:2012a) and for the Small Magellanic Cloud (cite: Prevot.M:1984a; Gordon.K:2003a). For high-redshift galaxies, the intrinsic UV slope, $\beta_\text{UV,0}$, is bluer than that for the local starbursts (cite: Reddy.N:2018a) due to the young ages, low stellar metallicities, and binary interactions (cite: Steidel:2014; Steidel:2016), although the nebular continuum emission could make it redder. We checked $\beta_\text{UV,0}$ of our best-fit intrinsic SED curves before dust reddening and found that it ranges from $\ensuremath{\beta_\text{UV,0}}= -2.6$ to $-2.55$, which is bluer than $-2.23$ used in (cite: Meurer.G:1999a). For simplicity we use $\ensuremath{\beta_\text{UV,0}}= -2.62$ (cite: Reddy.N:2018a) as a fiducial value at high redshift.

Figure [1](#fig:irxb) compares the measurements for B14-65666 and various IRX–$\beta_\text{UV}$ relations. The total is in a good agreement with the widely-used canonical relation, the (cite: Meurer.G:1999a) relation, modified to $\ensuremath{\beta_\text{UV,0}}= -2.62$. From this result, (1) the agreement with the Meurer relation supports our assumption of using the (cite: Calzetti:2000) attenuation curve in the SED fitting and (2) $\ensuremath{\beta_\text{UV,0}}= -2.62$ supports lower stellar metallicity and younger ages of B14-65666 than those of local starbursts (cite: Meurer.G:1999a; Overzier.R:2011a; Takeuchi.T:2012a). The galaxies E and W are, however, not consistent with the $\beta_\text{UV,0}$-modified Meurer relation. The galaxies E and W exhibit lower and higher IRX than the relation at their $\beta_\text{UV}$, respectively. Deviations from the canonical IRX-$\beta_\text{UV}$ relations arise from several physical processes (cite: Popping.G:2017a). For the galaxy E, the low IRX value would be explained by hypotheses that the galaxy E has higher dust temperatures of $T_\text{d} \ge 63\mbox{--}68$ K in the modified blackbody, as suggested by the SED fitting (Section [0.0.2](#sec:resolved-components)); or that the galaxy E exhibits a steeper SMC-like dust attenuation curve than the (cite: Calzetti:2000) one. Alternatively, the measurement of $\beta_\text{UV}$ based on the SED fitting may be affected by the red tails. If we assume that the measured dust emission only arises from the E-core, the E-core is located on the $\beta_\text{UV,0}$-modified Meurer relation on the IRX–$\beta_\text{UV}$ diagram. For the galaxy W, hypotheses to explain the IRX values are a low dust temperature of $T_\text{d} \le 27\mbox{--}33$ K, which qualitatively agrees with the SED-fitting result; or the patchy stellar-and-dust geometry unresolved even with NIRCam and ALMA ($\lesssim 0.2\mbox{--}1.5$ kpc), which produces flatter dust-attenuation curves resulting in high IRX at blue $\beta_\text{UV}$. The patchy stellar-and-dust geometry has been already found in a Lyman-break galaxy at $z = 8.31$ (cite: Tamura.Y:2023b) and supported by the FirstLight simulations, where complex stellar-and-dust geometry produces high IRX (cite: Mushtaq.M:2023a). In any scenarios, or in a combination of several scenarios, our rest-frame UV and FIR observations have highlighted the different dust properties between the galaxies E and W.

B14-65666 and most other $z\gtrsim7$ galaxies (cite: Hashimoto.T:2019a; Bowler.R:2022a) are distributed between the Meurer relations with $\ensuremath{\beta_\text{UV,0}}= -2.23$ (black thin line in Figure [1](#fig:irxb)) and $-2.62$ (black thick line). From this distribution, (cite: Hashimoto.T:2019a) and (cite: Bowler.R:2022a) concluded that dust-detected galaxies at $z\gtrsim7$ follow the (cite: Calzetti:2000) attenuation curve. The apparent IRX dispersion would be explained by a combination of a $\beta_\text{UV,0}$ variation (i.e., a variation of stellar age and metallicity) and patchy stellar-and-dust geometry (cite: Reddy.N:2018a). We note that their IRX is corrected for $T_\text{d}$ and $\beta_\text{d}$ used in this study and that their $\beta_\text{UV}$ was derived from photometry, which is different from our method. These results are consistent with stacking analyses of Lyman-break galaxies at $z\sim3$ (cite: Alvarez-Marquez.J:2016a; Alvarez-Marquez.J:2019b; Bowler.R:2024a), but seem to be inconsistent with steeper attenuation curves favored in stacking analyses of UV-selected galaxies at $z\sim2$ (cite: Reddy.N:2018a) and $z\sim4.5$ and $5.5$ (cite: Fudamoto.Y:2020a). However, some literature galaxies in Figure [1](#fig:irxb) have stringent IRX upper limits below the canonical relations at high $\beta_\text{UV}$ and the IRX estimates significantly depend on the assumptions of $T_\text{d}$ and $\beta_\text{d}$ and how to measure $\beta_\text{UV}$. The “standard” IRX–$\beta_\text{UV}$ relation at high redshift is still under debate.

## \[O iii\] Line Ratio: Insights into Gas-phase Metallicity

NIRCam images have identified a flux excess in the F444W band interpreted as a strong \[O iii\]$\lambda\lambda$4960,5008 emission. The ALMA Band 8 has detected the \[O iii\] 88 $\mathrm{\mu m}$ emission. Due to the large difference in their excitation energy, the ratio of the optical to FIR \[O iii\] emission lines is sensitive to the physical conditions (electron density and temperature) of the ionized emitting gas (cite: Osterbrock.D:2006a). This line ratio also depends on the gas-phase metallicity under the assumptions of photoionization models (cite: Nakazato.Y:2023a). Thus, a combination of the NIRCam images and ALMA moment-0 map provides us with insights into spatial distributions of gas-phase metallicity.

We created a line-ratio map by taking a ratio of the optical \[O iii\]$\lambda\lambda$4960,5008 emission-line map to the FIR \[O iii\] 88 $\mathrm{\mu m}$ image. The optical \[O iii\] line map was created as in Section [\[sec:result-morphology\]](#sec:result-morphology), but here the F356W and F444W images were corrected for the dust attenuation before creating the line map. We corrected flux densities within the apertures E ($A_\text{V} = 1.2$ mag), W ($0.34$ mag), and E-core ($0.72$ mag) so that the flux density recovered in each aperture agreed with the best-fit $A_\text{V}$ value obtained in the SED fitting. The created attenuation-corrected optical line map was convolved to match the angular resolution of the ALMA synthesized beam ($0.38\ensuremath{''}$). The map area is limited to the region where both lines are detected at more than 1$\sigma$ level and it corresponds to $3\mbox{--}4$ beam solid angle.

The top panel of Figure [2](#fig:o3ratio) illustrates the optical-to-FIR \[O iii\] line-ratio map. The line ratio at the peak of the \[O iii\] 88 $\mathrm{\mu m}$ surface brightness is $\simeq7.8$, and $10.6\pm1.9$ for the integrated flux, where the error does not include the uncertainty of $A_\text{V}$. The figure shows the spatial variation of the line ratio over the galaxies, which suggests a variation of the electron temperature and/or electron density in the galaxies E and W. At the peak positions of the E-core and W-core, the \[O iii\] line ratios are $9.2$ and $5.6$, respectively. The highest line ratios are seen in the S-tail; however, these high values are based on the assumed strong dust correction and include large uncertainties.

To be more quantitative, we used CLOUDY to explore nebular parameters that reproduce the obtained \[O iii\] line ratios. In our photoionization models, the \[O iii\] line ratio depends on nebular parameters: the gas-phase metallicity $Z_\text{gas}$, ionization parameter $U$, and hydrogen density $n_\text{H}$. As the F356W band includes weak emission lines, which are also subtracted from F444W flux, we corrected the model \[O iii\]$\lambda\lambda$4960,5008 line fluxes by subtracting expected $\mathrm{H\gamma}$ and $\mathrm{H\delta}$ line fluxes. The bottom panel of Figure [2](#fig:o3ratio) shows optical-to-FIR \[O iii\] line ratios as a function of the nebular parameters. The illustrated model lines depend on $Z_\text{gas}$ and $U$; low gas-phase metallicity and high ionization parameter increase the electron temperature of the ionized gas, leading to strong \[O iii\]$\lambda\lambda$4960,5008 lines with respect to \[O iii\] 88 $\mathrm{\mu m}$ line. Instead of $n_\text{H}$ at the illuminated surface, we used the averaged electron density $n_\text{e}$ for the $x$-axis that was computed from the modeled \[O iii\] 52 and 88 $\mathrm{\mu m}$ line ratios at the electron temperature of $1.2\times10^{4}$ K using PyNeb (cite: Luridiana.V:2015a).

The estimated gas-phase metallicity is $\ensuremath{Z_\text{gas}}\sim 0.2\mbox{--}0.4$ $Z_\text{\(\odot\)}$ for the total, at an assumed electron density of $n_\text{e} \sim 200\mbox{--}400$ $\mathrm{cm^{-3}}$, which is a typical estimate from optical-to-FIR \[O iii\] line ratios at high redshift (cite: Stiavelli.M:2023a; Fujimoto.S:2024b). Using the line ratios at the peak positions of the E-core and W-core, the E-core exhibits a lower gas-phase metallicity of $Z\sim 0.2\mbox{--}0.4$ $Z_\text{\(\odot\)}$ than the W-core ($> 0.4$ $Z_\text{\(\odot\)}$). These results are consistent with conclusions of the previous studies using the \[O iii\] 88 $\mathrm{\mu m}$ emission line that B14-65666 has sub-solar metallicity but not extremely low at $< 0.1$ $Z_\text{\(\odot\)}$ (cite: Hashimoto.T:2019a; Jones.T:2020a; Yang.S:2020a). The estimated values here are slightly higher than the metallicities derived from the SED fitting to the NIRCam and ALMA data, reflecting the assumed hydrogen (i.e., electron) density of $n_\text{H} = 100$ $\mathrm{cm^{-3}}$ in `Bagpipes`. We note that adopting higher electron densities of $n_\text{e} \sim 600$ $\mathrm{cm^{-3}}$, which is derived from optical emission lines (cite: Abdurrouf:2024a), results in higher $Z_\text{gas}$. In terms of the electron density, the optical-to-FIR \[O iii\] line ratios disagree with the presence of a high electron density gas ($n_\text{e} > 10^4$ $\mathrm{cm^{-3}}$), which have been traced by high-ionization UV emission lines in some high-redshift galaxies (cite: Senchyna.P:2023a; Marques-Chaves.R:2024a), under the assumption that galaxies in the EoR would have sub-solar metallicity.

## Overall scenario for B14-65666 system

The NIRCam and ALMA observations have shed light on the morphology and physical properties of B14-65666 in the EoR. We analyzed the rest-frame optical and FIR data to show the complex morphology of the merging galaxies: the galaxy E is composed of the compact core with faint dust emission and the diffuse red tails; the galaxy W presents an elongated and clumpy morphology with bright dust emission. These clumpy, elongated structures and diffuse emission like tidal tails are reproduced in the simulations of high redshift galaxies (cite: Nakazato.Y:2024a). Furthermore, the galaxy W may exhibit patchy stellar-and-dust geometry that is not resolved in our observations. These results indicate that B14-65666 is experiencing strong tidal forces accompanied with a merger, disturbing the entire morphology of the system and each of the galaxies involved in the process.

The projected separation of the galaxies E and W is $d\simeq4$ kpc and their line-of-sight velocity difference is $v\simeq200$ $\mathrm{km\ s^{-1}}$ (cite: Hashimoto.T:2019a). Although this is the first-order estimate, the timescale elapsed from the previous passage is estimated to be $d/v\simeq20$ Myr, which is comparable to the star-formation age inferred from the SED fitting. This merging timescale is feasible because it is shorter than the expected merger observability timescale of $180$ Myr at $z = 7.15$ (cite: Snyder.G:2017a). This consistency supports that the gravitational interactions have driven the star formation in the B14-65666 after the first (or second) passage.

Major mergers would promote gas accretion by removing the angular momentum from disk gas, triggering starbursts at the cores of the galaxies (cite: Mihos.J:1994a). B14-65666 shows signatures of nuclear dusty starbursts, including strong optical \[O iii\] emission, strong dust attenuation, and high $\mathrm{SFR}$. These nuclear dusty starbursts have indeed enhanced the star-forming activity of B14-65666. The instant $\ensuremath{\mathrm{SFR}}_0$ of $230$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$ is $\simeq1$ dex higher than the star-formation main sequence at $\log M_{*}/\ensuremath{\mathrm{M_\ensuremath{\odot}}}= 9.7$ and $z\sim7$ (cite: Popesso.P:2023a). The merger-induced star-formation at high redshift is consistent with a finding in the FirstLight simulations that bursty star-formation is induced by gas-rich mergers at $z > 5$ (cite: Ceverino.D:2018a). While many observations demonstrate that major mergers enhance $\mathrm{SFR}$ in the local Universe (cite: Ellison.S:2008a), the $\mathrm{SFR}$ enhancement is reported to be inefficient at $z > 1$ (cite: Silva.A:2018a; Shah.E:2022a). B14-65666 is a clear example experiencing enhanced star formation at higher redshift.

In particular, the E-core experiences a compact, centrally concentrated, strong starburst. Given $r_\text{e} < 85$ pc of the E-core in the F115W image and $\ensuremath{\mathrm{SFR}}_0$ values in Table [\[tb:properties\]](#tb:properties), the $\ensuremath{\mathrm{SFR}}_0$ surface density of the E-core is $\Sigma_{\ensuremath{\mathrm{SFR}}, 0}\gtrsim4\times10^3$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}\ kpc^{-2}}$, which is comparable to IR $\mathrm{SFR}$ surface densities of local ULIRGs or obscured AGN (cite: Pereira-Santaella.M:2021a). We expect that this compact starburst is caused by a significant gas accretion to the E-core. The high $\Sigma_{\ensuremath{\mathrm{SFR}}, 0}$ is also consistent with the expected high dust temperature of the E-core (cite: Liang.L:2019a). We note that star-formation timescale of the E-core ($< 5$ Myr) is much shorter than those of ULIRGs, as $\mathrm{SFR}$ of ULIRGs are derived from the FIR luminosity (i.e., $\sim100$ Myr). Although the molecular gas mass is highly uncertain for B14-65666 (cite: Hashimoto.T:2023b), the high $\Sigma_{\ensuremath{\mathrm{SFR}}, 0}$ would lead to short gas depletion time of $< 10$ Myr in the range of molecular gas mass surface densities of local starbursts (cite: Hodge.J:2015a; Pereira-Santaella.M:2021a). In addition, the high $\Sigma_{\ensuremath{\mathrm{SFR}}, 0}$ and s$\ensuremath{\mathrm{SFR}}_0$ of the E-core suggest that the radiation pressure is high enough to launch galactic outflows (cite: Pereira-Santaella.M:2021a; Ferrara.A:2023a), which lead to negative feedback, therefore reducing or even quenching the star formation (cite: Hopkins:2012). There might also exist an AGN in the compact E-core, which would be consistent with its high surface brightness and high dust temperature. In such a case, the E-core star-formation history will be affected by additional negative feedback by AGN. Thus, the compact dusty starburst at the E-core may cease within several tens Myr.

The gas-phase metallicity for the entire system is estimated to be $\simeq 0.2$ $Z_\text{\(\odot\)}$ from the SED fitting, and these estimates are supported by the optical-to-FIR \[O iii\] emission line ratio. B14-65666 is on the average mass-metallicity relation at $z = 4\mbox{--}9$ (cite: Nakajima.K:2023a; Curti.M:2023a), but given its high $\mathrm{SFR}$, it would not be on the fundamental metallicity plane (cite: Andrews.B:2013a). Our analyses also show that the galaxy E has lower metallicity than the galaxy W, which is consistent with a scenario where a strong accretion of less-enriched gas dilutes the pre-existing gas at the galaxy center (cite: Kewley.L:2006a). At $\ensuremath{Z_\text{gas}}\simeq0.2$ $Z_\text{\(\odot\)}$, an ionization parameter estimated by (cite: Sugahara.Y:2021a) using the \[O iii\] 88 $\mathrm{\mu m}$ and \[C ii\] 158 $\mathrm{\mu m}$ lines is $\log U \simeq - 2.0$, which is consistent with the SED fitting results. In other words, high \[O iii\]$/$\[C ii\] ratio of B14-65666 can be naturally explained by the high ionization parameter (cite: Hashimoto.T:2019a; Harikane.Y:2020b). The \[N ii\] 122 $\mathrm{\mu m}$ non-detection is also easily explained by the high ionization parameter where most of the nitrogen are in the doubly ionized phase (cite: Sugahara.Y:2021a).

Finally, we mention some limitations of our observations. Although we have revealed many properties of the cores of the galaxies, less properties are constrained for the tails. This is mainly because it is difficult to solve the degeneracy in physics that can explain their red SED, dust non-detections, and detection of \[O iii\] 88 $\mathrm{\mu m}$ emission, with different angular resolutions of the NIRCam and ALMA. We expected that the extended diffuse emission originates from the tidal tails produced by the major merger, but we did not reject other possibilities like ionized gas outflows (cite: Yuma.S:2019a) and offset old stellar populations (cite: Colina.L:2023a). Approved MIRI and NIRSpec IFU spectroscopy and ALMA high angular-resolution observations will give a hint to properties of the tails. To reach statistical conclusions, a large sample of major mergers at high redshift is necessary. It is unclear whether B14-65666 is representative of major mergers at this redshift. Nevertheless, our results suggest that the major merger, which is an abundant population at high redshift (cite: Rodriguez-Gomez.V:2015a; Duncan.K:2019a; Romano.M:2021a), makes significant contributions to galaxy mass assembly in the early Universe. B14-65666 is still an important target that provides us with detailed distributions of stellar, gaseous, and dust populations during major mergers.

# Conclusions

In this paper, we present JWST NIRCam observations of the UV-bright ($M_\text{UV} = -22.5$ mag) Lyman-break galaxy system B14-65666 at $z = 7.1520$, also known as Big Three Dragons. The NIRCam filters are selected to sample the rest-frame UV wavelengths, the Balmer break clean of strong optical emission lines, and the rest-frame optical wavelengths ($\sim5000$ Å) including $\mathrm{H\beta}$ and \[O iii\] emission lines. Additionally, rich ancillary ALMA data trace the \[O iii\] 88 $\mathrm{\mu m}$ and \[C ii\] 158 $\mathrm{\mu m}$ emission lines and underlying dust continua. The high angular resolution of these NIRCam and ALMA observations enables spatially resolved analyses at the rest-frame UV, optical, and FIR wavelengths of B14-65666, a bright major merger in the EoR.

B14-65666 consists of two galaxy components, E and W, and diffuse emission surrounding the galaxy E. The galaxy E is red (UV spectral slope $\ensuremath{\beta_\text{UV}}= -1.2$) and has a compact core (E-core) with an effective radius of $r_\text{e} < 0.016$ arcsec ($85$ pc) at the rest-frame $1400$ Å. The galaxy W is blue ($\ensuremath{\beta_\text{UV}}= -2.2$) and elongated to $\simeq 0.3$ arcsec ($1.5$ kpc) with clumpy morphology in the rest-frame UV wavelengths. Surprisingly, in contrast to their colors, the blue galaxy W is brighter than the red galaxy E in the dust continua at $88$ and $158$ $\mathrm{\mu m}$. The core of the galaxy E (E-core) is surrounded by diffuse extended emission, which is only detected in the long NIRCam wavelength channels and is also bright in \[O iii\] 88 $\mathrm{\mu m}$. We assume that this extended emission is likely to be the tidal tails created by the gravitational interactions. Both of the galaxies E and W show the F444W flux excesses over the F356W fluxes ($0.84^{+0.09}_{-0.10}$ and $0.53^{+0.09}_{-0.10}$ mag, respectively), indicating the strong \[O iii\]$\lambda\lambda$4960,5008 emission lines. The \[O iii\] line map estimated from the F356W$-$F444W color traces strong \[O iii\] emission at the E-core and W-core, with the rest-frame equivalent widths of $\text{EW}_0 \simeq 2000$ and $750$ Å, respectively. These results show that the major merger has disturbed the morphology of the galaxies and induced the nuclear dusty starbursts.

The SED fitting shows that B14-65666 has a total stellar mass of $\log M_{*}/\ensuremath{\mathrm{M_\ensuremath{\odot}}}= 9.8\pm0.2$ and $\ensuremath{\mathrm{SFR}}_\text{10Myr}$ of $\simeq 230^{+70}_{-60}$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$. These merger-induced starbursts would build young stellar masses comparable to or heavier than the underlying old stellar components. The stellar-mass ratio of the galaxies E and W spans from 3:1 to 2:1, which confirms the fact that B14-65666 is a major merger in terms of the stellar-mass ratio. The galaxy E experiences young starbursts with $\ensuremath{\mathrm{SFR}}_\text{10Myr} = 180^{+50}_{-40}$ $\mathrm{M_\ensuremath{\odot}\ yr^{-1}}$ at ages of $< 53$ Myr, supported by the high optical \[O iii\] emission. The red color of the galaxy E is explained by the strong dust attenuation of $A_\text{V} = 1.2\pm0.1$ mag, in opposite to the galaxy W, which has blue color and $A_\text{V} = 0.3\pm0.1$ mag. Including ALMA data, the SED fitting explains the red color and faint dust continua of the galaxy E by the scenario that the galaxy E exhibits higher dust temperature than the galaxy W.

As combinations of optical and FIR data, we investigate the IRX-$\beta_\text{UV}$ diagram and the optical-to-FIR \[O iii\] line ratios. The entire system is consistent with the $\beta_\text{UV,0}$-modified Meurer relation, supporting the Calzetti attenuation law. The galaxies E and W, however, deviate from the relation; this deviation can be explained by different stellar and dust properties: variations of the dust attenuation law, patchy stellar-and-dust geometry, different dust temperature, and possible effects of the tails. From the estimated \[O iii\]$\lambda\lambda$4960,5008 map and the \[O iii\] 88 $\mathrm{\mu m}$ moment-0 maps, we draw the optical-to-FIR \[O iii\] line ratio map. This map illustrates gradual spatial variation in the \[O iii\] line ratio, implying spatial variation in the electron temperature and electron density. From the \[O iii\] line ratios, the gas-phase metallicity of the entire galaxy is estimated to be $\ensuremath{Z_\text{gas}}\sim 0.2\mbox{--}0.4$ $Z_\text{\(\odot\)}$ by photoionization models under the assumption of the electron density of $\sim200\mbox{--}400$ $\mathrm{cm^{-3}}$. The E-core shows higher \[O iii\] line ratio than the W-core, indicating lower gas-phase metallicity in the E-core.

In summary, our results support a scenario where B14-65666 is a major merger that gravitationally disturbs the morphology and experiences nuclear dusty starbursts likely triggered by less-enriched gas inflows, after the first (or second) passage. Although the galaxies E and W have similar UV magnitude, they exhibit different stellar, gaseous, and dust properties and morphology. The starbursts have indeed enhanced the star-formation activity compared with main-sequence star-forming galaxies at the same redshift. B14-65666 is an important object that provides us with opportunities to investigate complex stellar buildup processes during major mergers, which are abundant at high redshifts, during the EoR.

We thank Rebecca Bowler for helpful discussions on B14-65666. We wish to thank the anonymous referee for valuable comments to improve our manuscript. This research is supported by NAOJ ALMA Scientific Research Grant number 2020-16B. This paper is a part of the outcome of research performed under a Waseda University Grant for Special Research Projects (Project number: 2024C-478). JAM, ACG, and LC acknowledge support by grant PIB2021-127718NB-100 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”. TH was supported by Leading Initiative for Excellent Young Researchers, MEXT, Japan (HJH02007) and by JSPS KAKENHI Grant Number 22H01258. KM, YN, and YT acknowledge financial support from JSPS through KAKENHI grant Number 20K14516, 23KJ0728, and 22H04939, respectively. CBP acknowledges support by grant CM21_CAB_M2_01 from the Program “Garantı́a Juvenı́l” from the “Comunidad de Madrid” 2021. MPS acknowledges support from grant RYC2021-033094-I funded by MCIN/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. The JWST data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via . STScI is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5–26555. Support to MAST for these data is provided by the NASA Office of Space Science via grant NAG5–7584 and by other grants and contracts. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00954.S, ADS/JAO.ALMA#2017.1.00190.S, and ADS/JAO.ALMA#2019.1.01491.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement. The *Gaia* data are retrieved from the JVO portal (<http://jvo.nao.ac.jp/portal>) operated by the NAOJ. This research has made use of NASA’s Astrophysics Data System.

# Software

NumPy (cite: Harris.C:2020a), SciPy (cite: Virtanen.P:2020a), IPython (cite: Perez.F:2007a), Matplotlib (cite: Hunter.J:2007a), Astropy (cite: Astropy-Collaboration:2013a; Astropy-Collaboration:2018a; Astropy-Collaboration:2022a)

natexlab

(ref: Abdurrouf:2023a) Abdurro’uf, Coe, D., Jung, I., et al. 2023, ApJ, 945, 117, doi: [`10.3847/1538-4357/acba06`](http://doi.org/10.3847/1538-4357/acba06)

(ref: Abdurrouf:2024a) Abdurro’uf, Larson, R. L., Coe, D., et al. 2024, ApJ, 973, 47, doi: [`10.3847/1538-4357/ad6001`](http://doi.org/10.3847/1538-4357/ad6001)

(ref: Alvarez-Marquez.J:2019b) Álvarez-Márquez, J., Burgarella, D., Buat, V., Ilbert, O., & Pérez-González, P. G. 2019, A&A, 630, A153, doi: [`10.1051/0004-6361/201935719`](http://doi.org/10.1051/0004-6361/201935719)

(ref: Alvarez-Marquez.J:2016a) Álvarez-Márquez, J., Burgarella, D., Heinis, S., et al. 2016, A&A, 587, A122, doi: [`10.1051/0004-6361/201527190`](http://doi.org/10.1051/0004-6361/201527190)

(ref: Alvarez-Marquez.J:2021b) Alvarez-Marquez, J., Hashimoto, T., Arribas, S., et al. 2021, ALMA \[OIII\]88um Emitters. Signpost of Early Stellar Buildup and Reionization in the Universe, JWST Proposal. Cycle 1, ID. #1840

(ref: Alvarez-Marquez.J:2023a) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105, doi: [`10.1051/0004-6361/202245400`](http://doi.org/10.1051/0004-6361/202245400)

(ref: Anderson.J:2016a) Anderson, J. 2016, Empirical Models for the WFC3/IR PSF, Instrument Science Report WFC3 2016-12, 42 pages

(ref: Anderson.J:2000a) Anderson, J., & King, I. R. 2000, PASP, 112, 1360, doi: [`10.1086/316632`](http://doi.org/10.1086/316632)

(ref: Andrews.B:2013a) Andrews, B. H., & Martini, P. 2013, ApJ, 765, 140, doi: [`10.1088/0004-637X/765/2/140`](http://doi.org/10.1088/0004-637X/765/2/140)

(ref: Asada.Y:2024a) Asada, Y., Sawicki, M., Abraham, R., et al. 2024, MNRAS, 527, 11372, doi: [`10.1093/mnras/stad3902`](http://doi.org/10.1093/mnras/stad3902)

(ref: Asplund.M:2021a) Asplund, M., Amarsi, A. M., & Grevesse, N. 2021, A&A, 653, A141, doi: [`10.1051/0004-6361/202140445`](http://doi.org/10.1051/0004-6361/202140445)

(ref: Astropy-Collaboration:2013a) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy-Collaboration:2018a) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy-Collaboration:2022a) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bagley.M:2023a) Bagley, M. B., Finkelstein, S. L., Koekemoer, A. M., et al. 2023, ApJL, 946, L12, doi: [`10.3847/2041-8213/acbb08`](http://doi.org/10.3847/2041-8213/acbb08)

(ref: Bakx.T:2021a) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58, doi: [`10.1093/mnrasl/slab104`](http://doi.org/10.1093/mnrasl/slab104)

(ref: Barnes.J:1996a) Barnes, J. E., & Hernquist, L. 1996, ApJ, 471, 115, doi: [`10.1086/177957`](http://doi.org/10.1086/177957)

(ref: Barton.E:2000a) Barton, E. J., Geller, M. J., & Kenyon, S. J. 2000, ApJ, 530, 660, doi: [`10.1086/308392`](http://doi.org/10.1086/308392)

(ref: Bik.A:2024a) Bik, A., Álvarez-Márquez, J., Colina, L., et al. 2024, A&A, 686, A3, doi: [`10.1051/0004-6361/202348845`](http://doi.org/10.1051/0004-6361/202348845)

(ref: Boquien.M:2019a) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: Borne.K:2000a) Borne, K. D., Bushouse, H., Lucas, R. A., & Colina, L. 2000, ApJL, 529, L77, doi: [`10.1086/312461`](http://doi.org/10.1086/312461)

(ref: Boucaud.A:2016a) Boucaud, A., Bocchio, M., Abergel, A., et al. 2016, A&A, 596, A63, doi: [`10.1051/0004-6361/201629080`](http://doi.org/10.1051/0004-6361/201629080)

(ref: Bouwens.R:2021b) Bouwens, R. J., Oesch, P. A., Stefanon, M., et al. 2021, AJ, 162, 47, doi: [`10.3847/1538-3881/abf83e`](http://doi.org/10.3847/1538-3881/abf83e)

(ref: Bowler.R:2018a) Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2018, MNRAS, 481, 1631, doi: [`10.1093/mnras/sty2368`](http://doi.org/10.1093/mnras/sty2368)

(ref: Bowler.R:2022a) Bowler, R. A. A., Cullen, F., McLure, R. J., Dunlop, J. S., & Avison, A. 2022, MNRAS, 510, 5088, doi: [`10.1093/mnras/stab3744`](http://doi.org/10.1093/mnras/stab3744)

(ref: Bowler.R:2017a) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2017, MNRAS, 466, 3612, doi: [`10.1093/mnras/stw3296`](http://doi.org/10.1093/mnras/stw3296)

(ref: Bowler.R:2012a) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., et al. 2012, MNRAS, 426, 2772, doi: [`10.1111/j.1365-2966.2012.21904.x`](http://doi.org/10.1111/j.1365-2966.2012.21904.x)

(ref: Bowler.R:2014a) —. 2014, MNRAS, 440, 2810, doi: [`10.1093/mnras/stu449`](http://doi.org/10.1093/mnras/stu449)

(ref: Bowler.R:2024a) Bowler, R. A. A., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 5808, doi: [`10.1093/mnras/stad3578`](http://doi.org/10.1093/mnras/stad3578)

(ref: Boyett.K:2024a) Boyett, K., Bunker, A. J., Curtis-Lake, E., et al. 2024, arXiv e-prints, arXiv:2401.16934, doi: [`10.48550/arXiv.2401.16934`](http://doi.org/10.48550/arXiv.2401.16934)

(ref: Bradley.L:2023a) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2023, astropy/photutils: 1.10.0, 1.10.0, Zenodo, doi: [`10.5281/zenodo.596036`](http://doi.org/10.5281/zenodo.596036)

(ref: Burgarella.D:2022b) Burgarella, D., Bogdanoska, J., Nanni, A., et al. 2022, A&A, 664, A73, doi: [`10.1051/0004-6361/202142554`](http://doi.org/10.1051/0004-6361/202142554)

(ref: Bushouse.H:2023a) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023, JWST Calibration Pipeline v1.9.4, 1.9.5, Zenodo, Zenodo, doi: [`10.5281/zenodo.7692609`](http://doi.org/10.5281/zenodo.7692609)

(ref: Byrne.C:2022a) Byrne, C. M., Stanway, E. R., Eldridge, J. J., McSwiney, L., & Townsend, O. T. 2022, MNRAS, 512, 5329, doi: [`10.1093/mnras/stac807`](http://doi.org/10.1093/mnras/stac807)

(ref: Calzetti:2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Calzetti.D:1994a) Calzetti, D., Kinney, A. L., & Storchi-Bergmann, T. 1994, ApJ, 429, 582, doi: [`10.1086/174346`](http://doi.org/10.1086/174346)

(ref: Carnall.A:2018a) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: CASA-Team:2022a) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Ceverino.D:2018a) Ceverino, D., Klessen, R. S., & Glover, S. C. O. 2018, MNRAS, 480, 4842, doi: [`10.1093/mnras/sty2124`](http://doi.org/10.1093/mnras/sty2124)

(ref: Ceverino.D:2023a) Ceverino, D., Mandelker, N., Snyder, G. F., et al. 2023, MNRAS, 522, 3912, doi: [`10.1093/mnras/stad1255`](http://doi.org/10.1093/mnras/stad1255)

(ref: Colina.L:2023a) Colina, L., Crespo Gómez, A., Álvarez-Márquez, J., et al. 2023, A&A, 673, L6, doi: [`10.1051/0004-6361/202346535`](http://doi.org/10.1051/0004-6361/202346535)

(ref: Costantin.L:2023a) Costantin, L., Pérez-González, P. G., Vega-Ferrero, J., et al. 2023, ApJ, 946, 71, doi: [`10.3847/1538-4357/acb926`](http://doi.org/10.3847/1538-4357/acb926)

(ref: Crespo-Gomez.A:2024a) Crespo Gómez, A., Colina, L., Álvarez-Márquez, J., et al. 2024, arXiv e-prints, arXiv:2402.18672, doi: [`10.48550/arXiv.2402.18672`](http://doi.org/10.48550/arXiv.2402.18672)

(ref: Curti.M:2023a) Curti, M., Maiolino, R., Carniani, S., et al. 2023, arXiv e-prints, arXiv:2304.08516. [`https://arxiv.org/abs/2304.08516`](https://arxiv.org/abs/2304.08516)

(ref: Draine.B:2007a) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: Draine.B:2014a) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172, doi: [`10.1088/0004-637X/780/2/172`](http://doi.org/10.1088/0004-637X/780/2/172)

(ref: Duan.Q:2024a) Duan, Q., Conselice, C. J., Li, Q., et al. 2024, arXiv e-prints, arXiv:2407.09472, doi: [`10.48550/arXiv.2407.09472`](http://doi.org/10.48550/arXiv.2407.09472)

(ref: Duncan.K:2019a) Duncan, K., Conselice, C. J., Mundy, C., et al. 2019, ApJ, 876, 110, doi: [`10.3847/1538-4357/ab148a`](http://doi.org/10.3847/1538-4357/ab148a)

(ref: Eldridge.J:2017a) Eldridge, J. J., Stanway, E. R., Xiao, L., et al. 2017, PASA, 34, e058, doi: [`10.1017/pasa.2017.51`](http://doi.org/10.1017/pasa.2017.51)

(ref: Ellison.S:2008a) Ellison, S. L., Patton, D. R., Simard, L., & McConnachie, A. W. 2008, AJ, 135, 1877, doi: [`10.1088/0004-6256/135/5/1877`](http://doi.org/10.1088/0004-6256/135/5/1877)

(ref: Fakhouri.O:2008a) Fakhouri, O., & Ma, C.-P. 2008, MNRAS, 386, 577, doi: [`10.1111/j.1365-2966.2008.13075.x`](http://doi.org/10.1111/j.1365-2966.2008.13075.x)

(ref: Ferland:1998a) Ferland, G. J., Korista, K. T., Verner, D. A., et al. 1998, PASP, 110, 761, doi: [`10.1086/316190`](http://doi.org/10.1086/316190)

(ref: Ferland.G:2017a) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385. [`https://arxiv.org/abs/1705.10877`](https://arxiv.org/abs/1705.10877)

(ref: Ferrara.A:2023a) Ferrara, A. 2023, arXiv e-prints, arXiv:2310.12197, doi: [`10.48550/arXiv.2310.12197`](http://doi.org/10.48550/arXiv.2310.12197)

(ref: Finkelstein.S:2015b) Finkelstein, S. L., Ryan, Jr., R. E., Papovich, C., et al. 2015, ApJ, 810, 71, doi: [`10.1088/0004-637X/810/1/71`](http://doi.org/10.1088/0004-637X/810/1/71)

(ref: Fudamoto.Y:2020a) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, A&A, 643, A4, doi: [`10.1051/0004-6361/202038163`](http://doi.org/10.1051/0004-6361/202038163)

(ref: Fujimoto.S:2024b) Fujimoto, S., Ouchi, M., Nakajima, K., et al. 2024, ApJ, 964, 146, doi: [`10.3847/1538-4357/ad235c`](http://doi.org/10.3847/1538-4357/ad235c)

(ref: Furusawa.H:2016a) Furusawa, H., Kashikawa, N., Kobayashi, M. A. R., et al. 2016, ApJ, 822, 46, doi: [`10.3847/0004-637X/822/1/46`](http://doi.org/10.3847/0004-637X/822/1/46)

(ref: Gaia-Collaboration:2016a) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: Gaia-Collaboration:2023a) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: Garcia-Marin.M:2009a) Garcı́a-Marı́n, M., Colina, L., Arribas, S., & Monreal-Ibero, A. 2009, A&A, 505, 1319, doi: [`10.1051/0004-6361/200811324`](http://doi.org/10.1051/0004-6361/200811324)

(ref: Gardner.J:2023a) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001, doi: [`10.1088/1538-3873/acd1b5`](http://doi.org/10.1088/1538-3873/acd1b5)

(ref: Gimenez-Arteaga.C:2023a) Giménez-Arteaga, C., Oesch, P. A., Brammer, G. B., et al. 2023, ApJ, 948, 126, doi: [`10.3847/1538-4357/acc5ea`](http://doi.org/10.3847/1538-4357/acc5ea)

(ref: Gordon.K:2003a) Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt, A. U., & Wolff, M. J. 2003, ApJ, 594, 279, doi: [`10.1086/376774`](http://doi.org/10.1086/376774)

(ref: Groves.B:2004a) Groves, B. A., Dopita, M. A., & Sutherland, R. S. 2004, ApJS, 153, 9, doi: [`10.1086/421113`](http://doi.org/10.1086/421113)

(ref: Harikane.Y:2020b) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93, doi: [`10.3847/1538-4357/ab94bd`](http://doi.org/10.3847/1538-4357/ab94bd)

(ref: Harris.C:2020a) Harris, C. R., Jarrod Millman, K., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hashimoto.T:2019a) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: Hashimoto.T:2023c) Hashimoto, T., Álvarez-Márquez, J., Fudamoto, Y., et al. 2023a, ApJL, 955, L2, doi: [`10.3847/2041-8213/acf57c`](http://doi.org/10.3847/2041-8213/acf57c)

(ref: Hashimoto.T:2023b) Hashimoto, T., Inoue, A. K., Sugahara, Y., et al. 2023b, ApJ, 952, 48, doi: [`10.3847/1538-4357/acdd5c`](http://doi.org/10.3847/1538-4357/acdd5c)

(ref: Hodge.J:2015a) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, L18, doi: [`10.1088/2041-8205/798/1/L18`](http://doi.org/10.1088/2041-8205/798/1/L18)

(ref: Hopkins:2008a) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: Hopkins:2012) Hopkins, P. F., Quataert, E., & Murray, N. 2012, MNRAS, 421, 3522, doi: [`10.1111/j.1365-2966.2012.20593.x`](http://doi.org/10.1111/j.1365-2966.2012.20593.x)

(ref: Hsiao.T:2023a) Hsiao, T. Y.-Y., Coe, D., Abdurro’uf, et al. 2023a, ApJL, 949, L34, doi: [`10.3847/2041-8213/acc94b`](http://doi.org/10.3847/2041-8213/acc94b)

(ref: Hsiao.T:2023b) Hsiao, T. Y.-Y., Abdurro’uf, Coe, D., et al. 2023b, arXiv e-prints, arXiv:2305.03042, doi: [`10.48550/arXiv.2305.03042`](http://doi.org/10.48550/arXiv.2305.03042)

(ref: Hunter.J:2007a) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Hygate.A:2023a) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775, doi: [`10.1093/mnras/stad1212`](http://doi.org/10.1093/mnras/stad1212)

(ref: Jones.G:2020a) Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020a, MNRAS, 491, L18, doi: [`10.1093/mnrasl/slz154`](http://doi.org/10.1093/mnrasl/slz154)

(ref: Jones.T:2020a) Jones, T., Sanders, R., Roberts-Borsani, G., et al. 2020b, ApJ, 903, 150, doi: [`10.3847/1538-4357/abb943`](http://doi.org/10.3847/1538-4357/abb943)

(ref: Kewley.L:2006a) Kewley, L. J., Geller, M. J., & Barton, E. J. 2006, AJ, 131, 2004, doi: [`10.1086/500295`](http://doi.org/10.1086/500295)

(ref: Kroupa:2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Li.J:2024a) Li, J., Da Cunha, E., González-López, J., et al. 2024, ApJ, 976, 70, doi: [`10.3847/1538-4357/ad7fee`](http://doi.org/10.3847/1538-4357/ad7fee)

(ref: Liang.L:2019a) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397, doi: [`10.1093/mnras/stz2134`](http://doi.org/10.1093/mnras/stz2134)

(ref: Luridiana.V:2015a) Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A, 573, A42, doi: [`10.1051/0004-6361/201323152`](http://doi.org/10.1051/0004-6361/201323152)

(ref: Man.A:2016a) Man, A. W. S., Zirm, A. W., & Toft, S. 2016, ApJ, 830, 89, doi: [`10.3847/0004-637X/830/2/89`](http://doi.org/10.3847/0004-637X/830/2/89)

(ref: Mandelker.N:2017a) Mandelker, N., Dekel, A., Ceverino, D., et al. 2017, MNRAS, 464, 635, doi: [`10.1093/mnras/stw2358`](http://doi.org/10.1093/mnras/stw2358)

(ref: Marques-Chaves.R:2024a) Marques-Chaves, R., Schaerer, D., Kuruvanthodi, A., et al. 2024, A&A, 681, A30, doi: [`10.1051/0004-6361/202347411`](http://doi.org/10.1051/0004-6361/202347411)

(ref: Marrone.D:2018a) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51, doi: [`10.1038/nature24629`](http://doi.org/10.1038/nature24629)

(ref: Matthee.J:2023a) Matthee, J., Mackenzie, R., Simcoe, R. A., et al. 2023, ApJ, 950, 67, doi: [`10.3847/1538-4357/acc846`](http://doi.org/10.3847/1538-4357/acc846)

(ref: Merlin.E:2015a) Merlin, E., Fontana, A., Ferguson, H. C., et al. 2015, A&A, 582, A15, doi: [`10.1051/0004-6361/201526471`](http://doi.org/10.1051/0004-6361/201526471)

(ref: Meurer.G:1999a) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64, doi: [`10.1086/307523`](http://doi.org/10.1086/307523)

(ref: Mihos.J:1994a) Mihos, J. C., & Hernquist, L. 1994, ApJL, 425, L13, doi: [`10.1086/187299`](http://doi.org/10.1086/187299)

(ref: Mihos.J:1996a) —. 1996, ApJ, 464, 641, doi: [`10.1086/177353`](http://doi.org/10.1086/177353)

(ref: Mushtaq.M:2023a) Mushtaq, M., Ceverino, D., Klessen, R. S., Reissl, S., & Puttasiddappa, P. H. 2023, MNRAS, 525, 4976, doi: [`10.1093/mnras/stad2602`](http://doi.org/10.1093/mnras/stad2602)

(ref: Nakajima.K:2023a) Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269, 33, doi: [`10.3847/1538-4365/acd556`](http://doi.org/10.3847/1538-4365/acd556)

(ref: Nakazato.Y:2024a) Nakazato, Y., Ceverino, D., & Yoshida, N. 2024, arXiv e-prints, arXiv:2402.08911, doi: [`10.48550/arXiv.2402.08911`](http://doi.org/10.48550/arXiv.2402.08911)

(ref: Nakazato.Y:2023a) Nakazato, Y., Yoshida, N., & Ceverino, D. 2023, ApJ, 953, 140, doi: [`10.3847/1538-4357/ace25a`](http://doi.org/10.3847/1538-4357/ace25a)

(ref: Oke.J:1983a) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713, doi: [`10.1086/160817`](http://doi.org/10.1086/160817)

(ref: Ormerod.K:2024a) Ormerod, K., Conselice, C. J., Adams, N. J., et al. 2024, MNRAS, 527, 6110, doi: [`10.1093/mnras/stad3597`](http://doi.org/10.1093/mnras/stad3597)

(ref: Osterbrock.D:2006a) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Oteo.I:2016a) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34, doi: [`10.3847/0004-637X/827/1/34`](http://doi.org/10.3847/0004-637X/827/1/34)

(ref: Ouchi:2013a) Ouchi, M., Ellis, R., Ono, Y., et al. 2013, ApJ, 778, 102, doi: [`10.1088/0004-637X/778/2/102`](http://doi.org/10.1088/0004-637X/778/2/102)

(ref: Overzier.R:2011a) Overzier, R. A., Heckman, T. M., Wang, J., et al. 2011, ApJL, 726, L7, doi: [`10.1088/2041-8205/726/1/L7`](http://doi.org/10.1088/2041-8205/726/1/L7)

(ref: Pereira-Santaella.M:2021a) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2021, A&A, 651, A42, doi: [`10.1051/0004-6361/202140955`](http://doi.org/10.1051/0004-6361/202140955)

(ref: Perez.F:2007a) Perez, F., & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: Perez-Gonzalez.P:2023b) Pérez-González, P. G., Barro, G., Annunziatella, M., et al. 2023, ApJL, 946, L16, doi: [`10.3847/2041-8213/acb3a5`](http://doi.org/10.3847/2041-8213/acb3a5)

(ref: Planck-Collaboration:2020a) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Popesso.P:2023a) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526, doi: [`10.1093/mnras/stac3214`](http://doi.org/10.1093/mnras/stac3214)

(ref: Popping.G:2017a) Popping, G., Puglisi, A., & Norman, C. A. 2017, MNRAS, 472, 2315, doi: [`10.1093/mnras/stx2202`](http://doi.org/10.1093/mnras/stx2202)

(ref: Prevot.M:1984a) Prevot, M. L., Lequeux, J., Maurice, E., Prevot, L., & Rocca-Volmerange, B. 1984, A&A, 132, 389

(ref: Qu.Y:2017a) Qu, Y., Helly, J. C., Bower, R. G., et al. 2017, MNRAS, 464, 1659, doi: [`10.1093/mnras/stw2437`](http://doi.org/10.1093/mnras/stw2437)

(ref: Reddy.N:2018a) Reddy, N. A., Oesch, P. A., Bouwens, R. J., et al. 2018, ApJ, 853, 56, doi: [`10.3847/1538-4357/aaa3e7`](http://doi.org/10.3847/1538-4357/aaa3e7)

(ref: Ribeiro.B:2017a) Ribeiro, B., Le Fèvre, O., Cassata, P., et al. 2017, A&A, 608, A16, doi: [`10.1051/0004-6361/201630057`](http://doi.org/10.1051/0004-6361/201630057)

(ref: Rieke.M:2023a) Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, PASP, 135, 028001, doi: [`10.1088/1538-3873/acac53`](http://doi.org/10.1088/1538-3873/acac53)

(ref: Rigby.J:2023a) Rigby, J., Perrin, M., McElwain, M., et al. 2023, PASP, 135, 048001, doi: [`10.1088/1538-3873/acb293`](http://doi.org/10.1088/1538-3873/acb293)

(ref: Roberts-Borsani.G:2020b) Roberts-Borsani, G. W., Ellis, R. S., & Laporte, N. 2020, MNRAS, 497, 3440, doi: [`10.1093/mnras/staa2085`](http://doi.org/10.1093/mnras/staa2085)

(ref: Rodriguez-Gomez.V:2015a) Rodriguez-Gomez, V., Genel, S., Vogelsberger, M., et al. 2015, MNRAS, 449, 49, doi: [`10.1093/mnras/stv264`](http://doi.org/10.1093/mnras/stv264)

(ref: Romano.M:2021a) Romano, M., Cassata, P., Morselli, L., et al. 2021, A&A, 653, A111, doi: [`10.1051/0004-6361/202141306`](http://doi.org/10.1051/0004-6361/202141306)

(ref: Senchyna.P:2023a) Senchyna, P., Plat, A., Stark, D. P., & Rudie, G. C. 2023, arXiv e-prints, arXiv:2303.04179, doi: [`10.48550/arXiv.2303.04179`](http://doi.org/10.48550/arXiv.2303.04179)

(ref: Shah.E:2022a) Shah, E. A., Kartaltepe, J. S., Magagnoli, C. T., et al. 2022, ApJ, 940, 4, doi: [`10.3847/1538-4357/ac96eb`](http://doi.org/10.3847/1538-4357/ac96eb)

(ref: Shapley.A:2019a) Shapley, A. E., Sanders, R. L., Shao, P., et al. 2019, ApJL, 881, L35, doi: [`10.3847/2041-8213/ab385a`](http://doi.org/10.3847/2041-8213/ab385a)

(ref: Shibuya.T:2022a) Shibuya, T., Miura, N., Iwadate, K., et al. 2022, PASJ, 74, 73, doi: [`10.1093/pasj/psab111`](http://doi.org/10.1093/pasj/psab111)

(ref: Silva.A:2018a) Silva, A., Marchesini, D., Silverman, J. D., et al. 2018, ApJ, 868, 46, doi: [`10.3847/1538-4357/aae847`](http://doi.org/10.3847/1538-4357/aae847)

(ref: Snyder.G:2017a) Snyder, G. F., Lotz, J. M., Rodriguez-Gomez, V., et al. 2017, MNRAS, 468, 207, doi: [`10.1093/mnras/stx487`](http://doi.org/10.1093/mnras/stx487)

(ref: Stanway.E:2016a) Stanway, E. R., Eldridge, J. J., & Becker, G. D. 2016, MNRAS, 456, 485, doi: [`10.1093/mnras/stv2661`](http://doi.org/10.1093/mnras/stv2661)

(ref: Steidel:2016) Steidel, C. C., Strom, A. L., Pettini, M., et al. 2016, ApJ, 826, 159, doi: [`10.3847/0004-637X/826/2/159`](http://doi.org/10.3847/0004-637X/826/2/159)

(ref: Steidel:2014) Steidel, C. C., Rudie, G. C., Strom, A. L., et al. 2014, ApJ, 795, 165, doi: [`10.1088/0004-637X/795/2/165`](http://doi.org/10.1088/0004-637X/795/2/165)

(ref: Stiavelli.M:2023a) Stiavelli, M., Morishita, T., Chiaberge, M., et al. 2023, ApJL, 957, L18, doi: [`10.3847/2041-8213/ad0159`](http://doi.org/10.3847/2041-8213/ad0159)

(ref: Sugahara.Y:2022a) Sugahara, Y., Inoue, A. K., Fudamoto, Y., et al. 2022, ApJ, 935, 119, doi: [`10.3847/1538-4357/ac7fed`](http://doi.org/10.3847/1538-4357/ac7fed)

(ref: Sugahara.Y:2021a) Sugahara, Y., Inoue, A. K., Hashimoto, T., et al. 2021, ApJ, 923, 5, doi: [`10.3847/1538-4357/ac2a36`](http://doi.org/10.3847/1538-4357/ac2a36)

(ref: Takeuchi.T:2012a) Takeuchi, T. T., Yuan, F.-T., Ikeyama, A., Murata, K. L., & Inoue, A. K. 2012, ApJ, 755, 144, doi: [`10.1088/0004-637X/755/2/144`](http://doi.org/10.1088/0004-637X/755/2/144)

(ref: Tamura.Y:2023b) Tamura, Y., C. Bakx, T. J. L., Inoue, A. K., et al. 2023, ApJ, 952, 9, doi: [`10.3847/1538-4357/acd637`](http://doi.org/10.3847/1538-4357/acd637)

(ref: Treu.T:2023a) Treu, T., Calabrò, A., Castellano, M., et al. 2023, ApJL, 942, L28, doi: [`10.3847/2041-8213/ac9283`](http://doi.org/10.3847/2041-8213/ac9283)

(ref: Trussler.J:2023a) Trussler, J. A. A., Adams, N. J., Conselice, C. J., et al. 2023, MNRAS, 523, 3423, doi: [`10.1093/mnras/stad1629`](http://doi.org/10.1093/mnras/stad1629)

(ref: Ventou.E:2017a) Ventou, E., Contini, T., Bouché, N., et al. 2017, A&A, 608, A9, doi: [`10.1051/0004-6361/201731586`](http://doi.org/10.1051/0004-6361/201731586)

(ref: Virtanen.P:2020a) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Weaver.J:2022a) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11, doi: [`10.3847/1538-4365/ac3078`](http://doi.org/10.3847/1538-4365/ac3078)

(ref: Yang.S:2020a) Yang, S., & Lidz, A. 2020, MNRAS, 499, 3417, doi: [`10.1093/mnras/staa3000`](http://doi.org/10.1093/mnras/staa3000)

(ref: Yuma.S:2019a) Yuma, S., Ouchi, M., Fujimoto, S., Kojima, T., & Sugahara, Y. 2019, ApJ, 882, 17, doi: [`10.3847/1538-4357/ab2f87`](http://doi.org/10.3847/1538-4357/ab2f87)

# Supplements for the SED fitting

Table [2](#tb:range) shows ranges of the free parameters in the SED fitting, explained in Sec [\[sec:sed-fitting\]](#sec:sed-fitting). `Bagpipes` receives these ranges as limits of the uniform prior distributions and performs the nested sampling to generate the posterior distribution of the parameters. Figure [3](#fig:corner) shows a corner plot of an obtained posterior distribution in fitting to the total photometry including the ALMA data.

Table [3](#tb:sedsfh) shows results for fitting to the total photometry obtained with different parametric starformation histories: constant (fiducial), delayed $\tau$, and exponential decreasing histories. The last row shows the fitting with the constant starformation history but without the old stellar component (i.e., without a parameter $M_\text{old}$). All the starformation histories give the comparable results because B14-65666 exhibits bursty starformation within a short timescale of $\sim10$ Myr.

| Parameters | Ranges |  |
|:---|:--:|:--:|
| $t_\text{SF} / \text{Myr}$ | \[$1.0$, $300.0$\] |  |
| $\mathrm{\log M_{ * } / M_{\ensuremath{\odot}}}$ | \[$1.0$, $15.0$\] |  |
| $A_\text{V} /$ mag | \[$0.0$, $2.0$\] |  |
| $\log U$ | \[$-4.0$, $-0.5$\] |  |
| $Z_{*} / Z_{\ensuremath{\odot}}$ | \[$0.01$, $2.00$\] |  |
| $\mathrm{\log M_\text{ old } / M_{\ensuremath{\odot}}}$ | \[$1.0$, $15.0$\] |  |
| $\ensuremath{\mathcal{U}_\mathrm{min}}$ | \[$0.1$, $50.0$\] |  |
| $\gamma$ | \[$0.001$, $1.0$\] |  |

: Parameter ranges used in the SED fitting.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Components | $\tau$ | $t_\mathrm{SF}$ | $\log{M_*}$ | $A_\mathrm{V}$ | $\log U$ | $Z_{*}$ | $\log{M_\mathrm{old}}$ |
|  | \[$\mathrm{Myr}$\] | \[$\mathrm{Myr}$\] | \[$\mathrm{\log M_{\odot}}$\] | \[$\mathrm{mag}$$\mathrm{\left( \mathrm{AB} \right)}$\] |  | \[$\mathrm{Z_{\odot}}$\] | \[$\mathrm{\log M_{\odot}}$\] |
| Constant | \- | $24^{+21}_{-9}$ | $9.75^{+0.18}_{-0.20}$ | $0.87^{+0.13}_{-0.11}$ | $-2.07^{+0.50}_{-0.35}$ | $0.26^{+0.10}_{-0.07}$ | $<9.65$ |
| Delayed $\tau$ | $185^{+73}_{-93}$ | $29^{+29}_{-14}$ | $9.62^{+0.23}_{-0.19}$ | $0.88^{+0.14}_{-0.12}$ | $-2.08^{+0.57}_{-0.34}$ | $0.28^{+0.10}_{-0.10}$ | $<9.61$ |
| Exponential | $191^{+72}_{-93}$ | $19^{+13}_{-8}$ | $9.69^{+0.17}_{-0.23}$ | $0.89^{+0.13}_{-0.12}$ | $-2.04^{+0.46}_{-0.38}$ | $0.27^{+0.09}_{-0.09}$ | $<9.42$ |
| Constant (without old) | \- | $15^{+17}_{-9}$ | $9.60^{+0.25}_{-0.29}$ | $0.90^{+0.17}_{-0.16}$ | $-2.07^{+0.65}_{-0.36}$ | $0.28^{+0.12}_{-0.11}$ | \- |

: Results of the SED fitting with differnt star-formation histories and setups.

Table notes: The results of the “Constant” starformation history (top) is the same as the “Total” with only NIRCam data in Table [1](#tb:sed). The slight differences between them originate from the numerical uncertainties in the Monte Carlo computations.

[^1]: Within the given fitting parameter ranges of $\mathcal{U}_\mathrm{min}$ and $\gamma$, the maximum characteristic temperature is $52.4$ K.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Tested constant, delayed-tau, exponential, and no-old-component SFHs in Appendix and confirmed results are insensitive to SFH choice",
  "failed_quote": "We also tested different star-formation histories, but the fitting results were insensitive to different star-formation histories (Appendix [sec:A1]), because B14-65666 is dominated by a young bursty star formation of \\sim10 Myr timescale."
 },
 {
  "path": "results_numeric[25].evidence[0]",
  "value": "Instant SFR surface density Sigma_SFR,0 of E-core = >= 4x10^3 M_sun yr^-1 kpc^-2",
  "failed_quote": "Given r_\\text{e} < 85 pc of the E-core in the F115W image and \\ensuremath{\\mathrm{SFR}}_0 values in Table [tb:properties], the \\ensuremath{\\mathrm{SFR}}_0 surface density of the E-core is \\Sigma_{\\ensuremath{\\mathrm{SFR}}, 0}\\gtrsim4\\times10^3 \\mathrm{M_\\ensuremath{\\odot}\\ yr^{-1}\\ kpc^{-2}}, which is comparable to IR \\mathrm{SFR} surface densities of local ULIRGs or obscured AGN (cite: Pereira-Santaella.M:2021a)."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[1]",
  "value": "The 158 um dust continuum peak is shifted east of galaxy W beyond ideal astrometric uncertainty, possibly due to poorer ALMA astrometric accuracy for extended sources.",
  "failed_quote": "The peak position of the 158 \\mathrm{\\mu m} dust emission is shifted to the east of the galaxy W beyond the ideal astrometric uncertainty (Section [sec:observational-data]). The origin of this shift is unclear, but it might be ALMA astrometric uncertainties poorer than the ideal one."
 }
]
```
