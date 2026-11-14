# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964..146F\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  JWST and ALMA Multiple-Line Study in and around a Galaxy at $z=8.496$:\
Optical to FIR Line Ratios and the Onset of an Outflow Promoting Ionizing Photon Escape

## Abstract

We present ALMA deep spectroscopy for a lensed galaxy at $z_{\rm spec}=8.496$ with $\log(M_{\rm star}/M_{\odot})\sim7.8$ whose optical nebular lines and stellar continuum are detected by *JWST*/NIRSpec and NIRCam Early Release Observations in SMACS0723. Our ALMA spectrum shows \[O iii\]88 $\mu$m and \[C ii\]158 $\mu$m line detections at $4.0\sigma$ and $4.5\sigma$, respectively. The redshift and position of the \[O iii\] line coincide with those of the *JWST* source, while the \[C ii\] line is blue-shifted by 90 km s$^{-1}$ with a spatial offset of $0.5\ensuremath{''}$ ($\approx0.5$ kpc in source plane) from the centroid of the *JWST* source. The NIRCam F444W image, including \[O iii\]$\lambda$5007 and H$\beta$ line emission, spatially extends beyond the stellar components by a factor of $>8$. This indicates that the $z=8.5$ galaxy has already experienced strong outflows as traced by extended \[O iii\]$¥lambda$5007 and offset \[C ii\] emission, which would promote ionizing photon escape and facilitate reionization. With careful slit-loss corrections and removals of emission spatially outside the galaxy, we evaluate the \[O iii\]88$\mu$m/$\lambda$5007 line ratio, and derive the electron density $n_{\rm e}$ by photoionization modeling to be $220^{+230}_{-130}$ cm$^{-3}$, which is comparable with those of $z\sim2$–3 galaxies. We estimate an \[O iii\]88$\mu$m/\[C ii\]158$\mu$m line ratio in the galaxy of $>4$, as high as those of known $z\sim$6–9 galaxies. This high \[O iii\]88 $\mu$m/\[C ii\]158 $\mu$m line ratio is generally explained by the high $n_{\rm e}$ as well as the low metallicity ($Z_{\rm gas}/Z_{\odot}=0.04^{+0.02}_{-0.02}$), high ionization parameter ($\log U > -2.27$), and low carbon-to-oxygen abundance ratio ($\log$(C/O) $=[-0.52:-0.24]$) obtained from the *JWST*/NIRSpec data; further \[C ii\] follow-up observations will constrain the covering fraction of photodissociation regions.

# Introduction

Studying early systems in the Epoch of Reionization (EoR; $z\gtrsim6$) is key to understanding fundamental cosmological questions such as the development of large-scale structure, the processes of cosmic reionization, and the first galaxy formation in the universe. In the last decades, deep *Hubble Space Telescope* (*HST*) surveys provided thousands of EoR galaxies and initial characterization of their stellar component, in terms of un-obscured star formation and sizes in the rest-frame ultra-violet (UV) wavelengths (cite: ellis2013; bouwens2015; finkelstein2015; oesch2016).

The Atacama Large Millimeter/submillimeter Array (ALMA) offers a unique rest-frame far-infrared (FIR) window on EoR galaxies to characterize the dust and gas properties of their interstellar media (ISMs), where the major cooling lines (e.g., \[C ii\] 158$\mu$m, \[O iii\] 88$\mu$m) and underlying dust continuum are probes of key mechanisms in the ISM such as disk rotation (cite: smit2018; rizzo2020), gravitational instability (cite: tadaki2018), formation of the bulge, disk, and spiral arms (cite: tsukui2021; lelli2021), galaxy mergers (cite: lefevre2020), outflows (cite: spilker2018), and dust-obscured star-forming activities (cite: bowler2022; inami2022), which strongly complements rest-UV studies with *HST*. Since elements produced in stars are returned to the ISM, the metal gas properties traced by the fine-structure lines, with their different ionization potentials and critical densities, provide powerful probes on the star-formation history and related physical conditions of the ISM, such as the temperature, density, ionization, and metal enrichment (cite: maiolino2019).

Previous ALMA observations have also raised questions about what causes large diversity in EoR galaxies and the difference from local galaxies. Early deep ALMA \[C ii\] spectroscopy of some EoR galaxies has shown low $L_{\rm [CII]}$/SFR values (cite: ota2014; knudsen2016), suggesting that they have characteristic ISM conditions such as high ionization parameter, low metallicity, or low gas density (cite: ferrara2019). However, recent ALMA observations detected dust continuum (cite: watson2015; inami2022) and bright \[C ii\] lines (cite: bouwens2022), pointing to a $L_{\rm [CII]}$/SFR relation similar to that of local main-sequence galaxies (cite: schaerer2020) and even low-mass sub-$L^{\star}$ galaxies at $z\gtrsim6$ (cite: fujimoto2021; molyneux2022). Moreover, while ALMA observations of EoR galaxies have also shown high $L_{\rm [OIII]}$/$L_{\rm [CII]}$ ratios (cite: inoue2016; harikane2020; carniani2020; witstok2022) that are comparable or even higher than local dwarf galaxies (cite: cormier2015), the main driver for the high ratios is still under debate (cite: harikane2020; vallini2021; katz2022; witstok2022). While promising, past *HST* and ALMA results have yet to provide a clear picture of the ISM physics in EoR galaxies.

To understand ISM physics, one of the key quantities is the gas-phase metallicity ($Z_{\rm gas}$), which is a direct probe of chemical enrichment and, thus, the evolutionary stage of galaxies. The flux of each metal line is determined by the abundance of that element and its emissivity (cite: aller1984). Therefore, we can accurately estimate the abundance once we measure the emissivity based on the electron temperature $T_{\rm e}$, i.e., the so-called *direct method* (cite: pilyugin2005; andrews2013). However, since the direct method requires the detection of very faint auroral lines (e.g., \[O iii\]$\lambda$4363), this has until recently only been possible for a handful of sources up to $z\sim3$ (cite: christensen2012; kojima2017; sanders2020).

Our observational landscape has been revolutionized by the advent of *JWST*. As part of the Early Release observation (ERO) programs of *JWST*, deep NIRSpec multi shutter array (MSA) observations have been performed towards the massive lensing cluster SMACSJ0723, successfully detecting multiple nebular emission lines in the rest-frame UV to optical wavelengths and determining spectroscopic redshifts for distant lensed galaxies out to $z=8.496$ (cite: carnall2022; schaerer2022; trump2022; curti2022). Remarkably, the deep NIRSpec spectra also show the detection of the auroral line \[O iii\]$\lambda$4363, enabling the first direct temperature $T_{\rm e}$ method estimates at such high redshifts (cite: schaerer2022; trump2022; curti2022). With the powerful *JWST* and ALMA combination, we are finally in a position to fully reveal how the elements of galaxies – gas, stellar, and dust – interplay with each other and what governs the growth of galaxies in the infant Universe.

In this paper, we present ALMA deep follow-up of two major coolant lines, \[C ii\] 158$\mu$m and \[O iii\] 88$\mu$m, and underlying continuum for the lensed galaxy at $z=8.496$, whose warm ISM properties are best characterized by the latest deep *JWST* observations, including the \[O iii\]$\lambda$4363 line. This is the first FIR characterization of an EoR galaxy with a robust metallicity measurement via the *direct method*, setting the benchmark to understand and interpret previous results from ALMA EoR galaxy studies over the last decade and providing a timely, unique reference for future follow-up of EoR galaxies in the coming decade.

The structure of this paper is as follows. In Section 2, we describe the observations and the data processing of both *JWST* and ALMA. Section 3 outlines the analyses related to the mass model for the lensing cluster, measurements of flux, size, and morphology, and the optical–mm SED fitting. In Section 4, we present the results from the multiple-line studies and discuss the physical origins of these results. A summary of this study is presented in Section 5. Throughout this paper, we assume a flat universe with $\Omega_{\rm m} =$ 0.3, $\Omega_\Lambda =$ 0.7, $H_0 =$ 70 km s$^{-1}$ Mpc$^{-1}$, and the Chabrier initial mass function (cite: chabrier2003). We adopt an angular scale of $1''=4.63$ kpc for the target redshift at $z=8.496$. We take the cosmic microwave background (CMB) effect into account and correct the flux measurements at submm and mm bands, following the recipe presented by (cite: dacunha2013) (see also e.g., (cite: pallottini2015; zhang2016; lagache2018)).

# Observations & Data Processing

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target line | Band | $\lambda_{\rm cent}$ | Obs Date | Baseline | $N_{\rm ant}$ | $T_{\rm int}$ | PWV | beam | $\sigma_{\rm line}$ | $\sigma_{\rm cont}$ |  |
|  |  | ($\mu$m) | (YYYY-MM-DD) | \(m\) |  | (min) | \(mm\) | ($''\times''$) | ($\mu$Jy/beam) | ($\mu$Jy/beam) |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |  |
|  158 $\mu$m | 5 | 1540 | 2022-10-17 | 15.1–629.3 (C3) | 44 | 85.7 | 0.5 | $1.35\times1.25$ | 225 | 11.6 |  |
|  88 $\mu$m | 7 | 854 | 2022-10-14 | 15.1–629.3 (C3) | 44 | 99.8 | 0.4 | $0.71\times0.58$ | 420 | 20.9 |  |

![](ALMA_CII-OIII_comb_v5.pdf)

## SMACS J0723.3-7327

The target field, SMACS J0723.3-7327 (hereafter SM0723), is a massive galaxy cluster at $z=0.390$ ($07^{h}23^{m}13.3^{s}$, $-73^{d}27^{m}25^{s}$), initially discovered via the Sunyaev-Zel’dovich effect in the Planck survey (cite: planck2011). The galaxy cluster mass is estimated to be $M_{200} = 8.4\times10^{14}M_{\odot}$. SM0723 was observed as part of the *HST* Reionization Lensing Cluster Survey (RELICS, #GO-14096, PI: D. Coe, (cite: coe2019)) treasury program and the subsequent *Spitzer* S-RELICS program (#12005, PI: M. Bradac).

## ALMA

ALMA Band 5 and Band 7 follow-up observations of \[C ii\] and \[O iii\] spectroscopy were carried out on October 17th and 14th 2022, respectively, as a Cycle 8 DDT program (#2022.A.00022.S, PI: S. Fujimoto). The target was a strongly lensed star-forming galaxy, ID4590, spectroscopically confirmed at $z=8.496$ with the robust detection of rest-frame optical emission lines including the \[O iii\]$\lambda$4363 line (cite: carnall2022; schaerer2022; trump2022; curti2022). Both observations used the Frequency Division Mode, and baseline ranges 15–457 m in the C-3 configuration. The mean precipitable water vapour (PWV) was 0.5 mm and 0.4 mm, and the on-source integration times were 85.7 mins and 99.8 mins in Band 5 and Band 7, respectively. J0519-4546 was observed as a flux and bandpass calibrator in both observations, while the phase calibration was performed with J0601-7036 and J0635-7516 in Band 5 and Band 7 observations, respectively.

The ALMA data were reduced and calibrated with the Common Astronomy Software Applications package version 6.4.1.12 (CASA; (cite: casa2022)) with the pipeline script in the standard manner. We imaged the calibrated visibilities using natural weighting, a pixel scale of $0.05\ensuremath{''}$, and a primary beam limit down to 0.2 by running the CASA task tclean. For cubes, we adopted spectral channel bins of 20, 30, and 40 km s$^{-1}$ and performed the CLEAN algorithm. We confirmed the results unchanged much ($<$10 %) in the following analyses via the choice of the spectral resolutions, and we used 20 km/s resolution cubes in the following analyses. For continuum maps, the tclean routines were executed down to the 1$\sigma$ level with a maximum iteration number of 100,000 in the automask mode (cite: kepley2020). We mask the central $\pm120$ km s$^{-1}$ channels to avoid contamination from the \[C ii\] and \[O iii\] lines in the continuum map. The natural weighted images, which maximize the S/N, resulted in the full-width-half-maximum (FWHM) size of the synthesized beam of $1.35\ensuremath{''}\times1.25\ensuremath{''}$ and $0.71\ensuremath{''}\times0.58\ensuremath{''}$ with $1\sigma$ sensitivities for the continuum (line in a 20 km s$^{-1}$ channel) of 11.6 (225) $\mu$Jy beam$^{-1}$ and 20.9 (420) $\mu$Jy beam$^{-1}$ in Band 5 and Band 7, respectively. Figure [1](#fig:alma) shows the reduced continuum maps and the line cubes for both ALMA Band 5 and Band 7. We summarize the data properties of the continuum maps and the line cubes in Table [\[tab:obs_summary\]](#tab:obs_summary).

## JWST

As part of the *JWST* ERO (#ERO-2736; (cite: pontoppidan2022)), SM0723 was observed with *JWST*/NIRCam, NIRSpec, MIRI, and NIRISS in June 2022. In the NIRCam and MIRI observations, six (F090W, F150W, F200W, F277W, F356W, F444W) and four (F770W, F1000W, F1500W, F1800W) different filters were used with $\sim$7540 sec and $\sim$5600 sec exposure per filter, reaching 5$\sigma$ limiting magnitudes of $\sim$29.4–30.0 AB and $\sim$23–26.3 AB, respectively (cite: pontoppidan2022).

For NIRCam and MIRI, we use publicly available reduced and calibrated imaging products via the `grizli` pipeline.[^1] The detailed calibration and reduction procedures will be presented in Brammer et al. (in prep.) (see also, e.g., (cite: bradley2022; fujimoto2022b)). Briefly, the *JWST* pipeline calibrated level-2 NIRCam imaging products were retrieved and processed with the `grizli` pipeline (cite: brammer2021; brammer2023), where the photometric zero-point correction was applied, including other corrections for “snowballs”[^2], “wisps”[^3], and detector variations.[^4] We include a systematic error of 10% on the observed flux values in the following analyses as a conservative measure in the same manner as other recent NIRCam studies (cite: naidu2022; finkelstein2023), while the derived photometric zeropoints are consistent with those derived by other teams for *JWST* ERS programs (cite: boyer2022; nardiello2022). The fully-calibrated images in each filter were aligned with the GAIA DR3 catalog (cite: gaia2021), co-added, and drizzled at a 20 mas and 40 mas pixel scale for the short-wavelength (SW: F090W, F150W, F200W) and long-wavelength (LW: F277W, F356W, F444W) NIRCam band images, respectively. For the produced maps, we also additionally correct the proper motion effects of the GAIA sources. In the Appendix, we show the residual astrometric offsets of the GAIA sources. We confirm the residual astrometric offset with respect to the GAIA DR3 frame is close to zero with the uncertainty of $\sim$10–20 mas. All the MIRI images (F770W, F1000W, F1500W, F1800W) are aligned, co-added, and drizzled at 40 mas pixel scale in the same manner. Existing multi-wavelength WFC3 archival imaging from *HST* was also processed with `grizli`, being aligned, co-added, and drizzled at 40 mas pixel scale in the same manner (see also (cite: kokorev2022)). We include all MIRI and *HST*/F105W, F125W, F140W, and F160W data in our analysis. Given the existence of nearby objects (Section [3.4](#sec:morph)), we adopt $0.36\ensuremath{''}$-diameter aperture photometry which is corrected to the total flux measurement by `MAG_AUTO`. We also correct for the Galactic dust reddening in the target direction. The *JWST* and *HST* photometry used in this paper are summarized in the Appendix.

For NIRSpec, there are several studies applying the latest reduction and calibration ((cite: heintz2022c); (cite: nakajima2023)), compared to previous studies (cite: schaerer2022; curti2022; trump2022; brinchmann2022; arellano2022). In our paper, we use results from (cite: nakajima2023) due to requirements of specific parameter sets for the photoionization model analysis in Section [4.5](#sec:oiii-cii_ratio) that are self-consistently derived in (cite: nakajima2023). We confirm that the measurements and the derived physical parameters are generally consistent with the previous studies within the errors (cite: schaerer2022; curti2022; trump2022; brinchmann2022; arellano2022) as well as the similarly latest calibration and reduction efforts presented in (cite: heintz2022c). Briefly, the NIRSpec 1D spectra are re-created by using four of the six exposures after removing one with no signal and another with a noisy 2D spectrum around H$\gamma$+\[O iii\]$\lambda 4363$. Some improvements are also implemented, including the background residual subtractions, hot pixel removals, optimal 1D extractions, as well as flux calibrations by referring to the standard star observations taken during commissioning.

Using the improved NIRSpec spectrum, Nakajima et al. confirm the rest-frame UV and optical emission line detection at $z=8.496$ from ID4590, including \[O iii\]$\lambda5007,4959$, \[O iii\]$\lambda4363$, H$\beta$, H$\gamma$, H$\delta$, and C iii\]$\lambda\lambda1907,1909$, and evaluate their relative line fluxes after applying a slit-loss correction[^5]. On the other hand, Nakajima et al. find that the \[O ii\]3727 doublet is not clearly detected in every nod and visit, and they place a conservative 3$\sigma$ upper limit, which provides a lower limit for the ionization parameter $\log$(U)$>-2.27$ based on (cite: kewley2002). The electron temperature and the gas-phase oxygen abundance are estimated to be $T_{\rm [OIII]}=(2.08\pm0.34)\times10^{4}$ K and 12+$\log$(O/H) = $7.26\pm0.18$ (equal to $0.04\pm0.02\,Z_{\odot}$ by assuming the solar metallicity of 12+$\log$(O/H)=8.69) via the direct $T_{\rm e}$ method (cite: pilyugin2012) by assuming a negligible contribution from O$^{+}$/H$^{+}$ ($<0.05$ dex at $3\sigma$; (cite: nakajima2023)). The lower and upper boundaries of the C/O abundance are also estimated to be $\log$(C/O) = $[-0.52:-0.24]$ (cite: isobe2023b). These physical parameters are derived including the dust correction based on the best-fit $E(B-V)$ value in this paper (Section [3.6](#sec:full_sed)).

| Target line | \[O iii\]88$\mu$m | \[C ii\]158$\mu$m |
|:--:|:--:|:--:|
| R.A. | 07:23:26.242 | 07:23:26.243 |
| Dec. | $-73$:26:56.824 | $-73$:26:56.514 |
| S/N$_{\rm line}$ | 4.0 | 4.5 |
| Frequency center \[GHz\] | $357.305\pm0.034$ | $200.203\pm0.010$ |
| $z_{\rm line}$ | $8.4963\pm0.0009$ | $8.4931\pm0.0005$ |
| Line width \[km s$^{-1}$\] | $136\pm67$ | 118 $\pm$ 36 |
| Line intensity \[Jy km s$^{-1}$\] | $0.113\pm0.033^{\sharp}$ | $0.094\pm0.027^{\dagger}$ |
| Line luminosity \[$\times10^{8}\,L_{\odot}$\] | $3.12\pm0.89^{\sharp}$ | $1.45\pm0.32^{\dagger}$ |
| Continuum \[$\mu$Jy\] | $\,\,<41.8$ (0.85 mm) | $<23.2$ (1.54 mm) |

: Observed FIR properties of ID4590 with ALMA

$\sharp$ We add a possible uncertainty by 20% due to the velocity-integration range for the \[O iii\] line (see text).\
$\dagger$ Given the spatial and velocity offsets of the \[C ii\] line, we place a 3$\sigma$ upper limit of $L_{\rm [CII]} < 6.0\times10^{7}\,L_{\odot}$ at the galaxy position from the residual map of imfit.

![](RGB_cii+oiii_v10.pdf)

# Data analysis

## Mass Model

Several mass models are publicly available in SM0723, including those developed by using Lenstool (cite: jullo2007) and Glafic (cite: oguri2010) with the *HST* data from the RELICS team (cite: coe2019)[^6]. More models have been constructed for SM0723 with the *JWST* ERO data, using Lenstool (cite: mahler2022; caminha2022), the light-traces-mass approach (LTM; (cite: broadhurst2005; zitrin2009; zitrin2015)) presented in (cite: pascale2022), and an updated version of Glafic (cite: oguri2021b) presented in (cite: harikane2022b).

In this paper, we use the latest Glafic model. The magnification factor for ID4590 is estimated to be $\mu=8.69$, which is consistent with the latest Lenstool model prediction ($\mu\sim9$) based on the *JWST* ERO and the latest MUSE data (cite: caminha2022). We define the systematic uncertainty due to the choice of the mass model by $$\begin{eqnarray}
\Delta\mu\equiv \frac{|\mu_{\rm glafic} - \mu_{\rm other}|}{\mu_{\rm glafic}}, 
\end{eqnarray}$$ where $\mu_{\rm glafic}$ and $\mu_{\rm other}$ indicate the magnification factor evaluated by the updated version of Glafic and other models, respectively. Among the mass models constructed with the *JWST* ERO data, the $\Delta\mu$ value is estimated to be $\sim$15–30% for ID4590. In the following analyses when we correct for the gravitationally lensing effect on ID4590, we use $\mu=8.69$ and add a systematic uncertainty from the mass models of 30%. When correcting physical values for lensing, we do not account for differential magnification in the following analysis, as we confirm it to be much less than the above systematic uncertainty across the positions in the galaxy. However, when we discuss the intrinsic morphology and size (Section [3.3](#sec:size) and [3.4](#sec:morph)), we do consider the difference between the radial ($\mu_{\rm rad.}$) and tangential ($\mu_{\rm tang.}$) magnifications that are estimated to be $\mu_{\rm rad.}=1.37$ and $\mu_{\rm tang.}=6.35$ with position angle (PA) in East of North of $-39.5$ deg.

## Continuum & Line Measurements

In the top panels of Figure [1](#fig:alma), we show the $6''\times6''$ continuum maps of ALMA Band 7 (left) and Band 5 (right). In both bands, we find that the relevant pixels show negative counts. We assume that the emission is unresolved in the continuum maps with the current ALMA beam ($\sim0.7\ensuremath{''}$–$1.3\ensuremath{''}$) and place 2$\sigma$ upper limits of 41.8 $\mu$Jy beam$^{-1}$ and 23.2 $\mu$Jy beam$^{-1}$ in Band 7 and Band 5, respectively, based on the standard deviation of the maps.

In the bottom panels of Figure [1](#fig:alma), we also present the line spectra for the \[O iii\]88$\mu$m (left) and \[C ii\]158$\mu$m lines (right). In the spectra, we identify positive signals in several consecutive channels at around 357.3 GHz and 200.2 GHz in Band 7 and Band 5, respectively, that are both consistent with the expected frequencies of the \[O iii\]88$\mu$m and \[C ii\]158$\mu$m lines based on the source redshift spectroscopically determined by NIRSpec. In the top panels, we show the velocity-integrated (moment 0) maps by using these line-detected channels that are highlighted by the yellow shades in the bottom spectra. In the moment 0 maps, we find that the S/N in the peak pixel shows 4.0 and 4.1 for the \[O iii\] and \[C ii\] lines, respectively. The latter is spatially resolved, especially in the Northwest to Southeast direction, where the S/N increases to 4.5 with a $2.0\ensuremath{''}$-diameter aperture. On the other hand, \[O iii\] line is compact and not spatially resolved with the current beam size and data depth. Note that the \[O iii\] line shows a potential double peak profile, which is typical among rotation-supported systems with inclinations (cite: kohandel2019), while the other possibility is that the noise fluctuation skews the line profile from a single Gaussian. We confirm that removing the three channels around the secondary peak ($\simeq$357.45 GHz) from the integration range for the mom 0 map provides the same peak S/N of 4.0. This suggests that the significance level of the \[O iii\] line detection is not unchanged regardless of whether it is truly the double peak profile or not.

From a single Gaussian fit in the spectra, we estimate the frequency center and the line redshifts as $z_{\rm [OIII]88}=8.4963 \pm 0.0009$ and $z_{\rm [CII]}=8.4931 \pm 0.0005$ with the line width of FWHM$_{\rm [OIII]88}=137\pm67$ km s$^{-1}$ and FWHM$_{\rm [CII]}=$ $118\pm36$ km s$^{-1}$. The redshift of \[O iii\]88$\mu$m is in excellent agreement with the source redshift determined by NIRSpec, while the \[C ii\] line appears blue-shifted by $\sim90$ km s$^{-1}$ beyond the errors. The line widths are consistent with each other within the errors.

Given a possibility that the chance projection of the noise fluctuation (cite: kaasinen2022) causes the \[C ii\] velocity offset, we quantify its probability in our \[C ii\] line identification by running a blind line search algorithm of Findclump implemented in a Python library of Interferopy (cite: interferopy) for observational radio–mm interferometry data analysis[^7]. We use a 20-km $^{-1}$ channel width cube of Band 5 and adopt the spatial tolerance of $1.2\ensuremath{''}$ (= beam size) and the frequency tolerance of 100 MHz ($\sim$150 km s$^{-1}$) to match the detection in the cube. We find that $\sim180$ line features are identified with similar or higher S/N in the entire data cube within a 20$''$-radius circular area and 274 channels, which is equal to 259793 independent beams in the cube. Given that the 200.2 GHz line is identified within the spatial and frequency tolerances from the expectations of the target, we estimate the chance projection of the random noise is 0.07% (= 180 / 259793 $\times$ 1), indicating that the purity of the line detection is $>99.9\%$. Therefore, we conclude that \[C ii\] line identification is unlikely explained by the noise fluctuation, and its velocity and spatial offsets are real. The reason for the blue-shifted \[C ii\] would be differential distributions of the multi-phase gases and their associated kinematics (cite: pallottini2019; arata2020; kohandel2020; katz2022; akins2022; valentino2022); the rest-frame optical emission lines observed with NIRSpec and the \[O iii\]88$\mu$m line originate from the ionized gas, while the \[C ii\]158$\mu$m line mostly arises in the photodissociation regions (PDRs). The \[C ii\] peak position shows a spatial offset from the *JWST* source position by $\sim 0.5\ensuremath{''}$ beyond the uncertainty of its positional accuracy (Section [3.4](#sec:morph)), which also supports the differential distributions of these multi-phase gases.

With a 2$''$-diameter aperture in the moment 0 maps, we measure the line intensities and convert them to the \[C ii\] line luminosity of $L_{\rm [CII]}=(1.45\pm0.32)\times10^{8}\,L_{\odot}$ in the observed frame (i.e., no lens correction). Given its spatial and velocity offsets, we also place a $3\sigma$ upper limit at the galaxy position of $< 6.0\times10^{7}\,L_{\odot}$ by taking the line width from \[O iii\] line. From its compact morphology of \[O iii\] 88$\mu$m, we assume that \[O iii\] is spatially unresolved and infer the \[O iii\] line luminosity of $L_{\rm [OIII]}=(3.12\pm0.76)\times10^{8}\,L_{\odot}$ from the peak pixel count. Note that this \[O iii\] line flux estimate decreases by $\sim20\%$ if we remove the three channels around the secondary peak from the integration range when generating the moment 0 map. We thus add a systematic uncertainty of 20% for the \[O iii\] line flux estimate in the following analyses. We summarize these continuum and line properties in Table [1](#tab:fir_prop).

## Sizes

We also measure the spatial sizes of \[C ii\]158$\mu$m and \[O iii\]88$\mu$m lines with ALMA as well as the rest-frame UV and optical continuum with *JWST*/NIRCam. In both data, we measure the sizes in the image plane.

First, for the \[C ii\] and \[O iii\] lines, we perform CASA imfit task to apply the 2D elliptical Gaussian fitting. We do not fix any parameters in the fitting. We obtain the best-fit FWHM of $1.90\ensuremath{''}\pm0.82\ensuremath{''}$ and $0.99\ensuremath{''}\pm0.57\ensuremath{''}$ in the major and minor axis, respectively, for the \[C ii\] line. Although we cannot exclude the possibility that these best-fit sizes are affected by the noise fluctuation with the current S/N, we confirm that no significant positive/negative signals remain in the residual map. On the other hand, the imfit output suggests that \[O iii\] is not spatially resolved. We subtract the ALMA synthesized beam profile re-scaled to the \[O iii\] peak count from the observed \[O iii\] map and confirm that no significant positive/negative signals remain in the residual map. We thus place a $2\sigma$ upper limit of FWHM $<0.31\ensuremath{''}$ based on the limit of the reliable size measurement with interferometric data according to the data sensitivity and the beam size (cite: marti2012). The trend of the larger \[C ii\] line size than that of the \[O iii\] line is consistent with recent ALMA observation results for galaxies at similar redshifts (cite: carniani2020; akins2022; witstok2022). We list the circularized effective radii [^8] of the \[C ii\] and \[O iii\] lines in Table [2](#tab:property). The observed, best-fit model and residual maps are summarized in the Appendix.

Second, for the rest-frame UV and optical continuum, we use the NIRCam/F150W and F356W maps, respectively, that are not affected by strong emission line contributions. We conduct a 2D Sérsic profile fitting with galfit (cite: peng2010). The pixel of the F356W map is rebinned to a pixel scale of $0.02\ensuremath{''}$, which is the same pixel scale as the F150W map. We use NIRCam PSFs for the ERO data of SM0723 publicly available[^9], which are generated from the `WebbPSF` model and drizzled to a grid of $0.02\ensuremath{''}$ in the same manner as the mosaic maps in the `grizli` pipeline. Note that these PSFs are generated with the latest version of `WebbPSF`, including the correction of the optical path difference[^10], where it mitigates the potential difference from the empirical PSFs (cite: ono2022). In the F150W fit for the rest-frame UV continuum, we do not fix any parameters, while we adopt the initial parameter set based on the lensing distortion with the axis ratio of $\mu_{\rm rad.}/\mu_{\rm tang.}=0.22$ and the PA of $-39.5$ deg. We obtain the best-fit effective radius of $r_{\rm e}=3.6\pm0.5$ pixel ($=0.33\pm0.05$ kpc) in the major axis with the axis ratio of $0.57\pm0.09$. The best-fit axis ratio exceeds the prediction from the lensing distortion ($=0.22$), indicating that ID4590 is well resolved in the radial magnification axis. We also obtain the PA of $-38\pm10$ deg, which is consistent with the lensing distortion ($=-39.5$). This supports the strong magnification factor in ID4590 of $8.69$ ($=\mu_{\rm rad.}\times\mu_{\rm tang.}$) and suggests that the observed rest-frame UV morphology is mostly dominated by the lensing distortion. In the F356W fit for the rest-frame optical continuum, we fix the best-fit axis ratio, PA, and Seŕsic index from the F150W results, given the worse spatial resolution than that of F150W. We obtain the best-fit $r_{\rm e}$ of $3.9\pm0.2$ pixel ($=0.36\pm0.02$ kpc) in the major axis. Given the best-fit axis ratio of $0.57\pm0.09$, we list the circularized $r_{\rm e}$ values for these stellar continua also in Table [2](#tab:property). The observed, best-fit model, and residual maps for these NIRCam results are also summarized in the Appendix.

## Morphology

In Figure [2](#fig:nircam), we compare the spatial distribution of each emission from ID4590. The left panel shows the \[C ii\]158$\mu$m and \[O iii\]88$\mu$m line contours overlaid on the $6''\times6''$ RGB color image with NIRCam filters. The middle and right panels display zoom-in ($1.5\ensuremath{''}\times1.5\ensuremath{''}$ ) F150W image (middle) and RGB color image (right) with NIRCam filters of F150W, F356W, and F444W, where the first two filters trace the rest-frame UV and optical continuum, while the last filter includes the \[O iii\]5007 and H$\beta$ lines in addition to the underlying rest-frame optical continuum. For the RGB images, the maps are PSF-matched to the F444W filter, and the white and cyan contours in the right panel represent the flux distribution in the F444W and F150W filters, respectively. The green and black crosses indicate the peak position of the \[C ii\]158$\mu$m line and the F444W emission, where the bar sizes of the cross are equal to the uncertainty of the positional accuracy based on its beam size and S/N[^11]. The yellow arrows in the middle panel denote the radial ($\mu_{\rm rad.}$) and tangential magnifications ($\mu_{\rm tang.}$) to understand the distortion of ID4590 due to the lensing effect. To investigate faint tails of the emission, we additionally subtract the local background in all NIRCam filters by evaluating the median pixel count in a black field near from ID4590.

We find that the peak position of the \[O iii\]88$\mu$m is consistent with the *JWST* source position of ID4590, while the \[C ii\]158$\mu$m has an offset of $\sim0.5\ensuremath{''}$ beyond the uncertainty of the positional accuracy. In the source-plane reconstruction of the *JWST* and \[C ii\] source positions, we find that the intrinsic offset decreases down to $\sim0.1\ensuremath{''}$, which is equal to $\sim0.5$ kpc. Because of the significantly low probability of the chance projection of the noise (Section [3.2](#sec:alma_measurement)), the spatial offset in \[C ii\] indicates that physical origins of the emission is associated with ID4590, while it arises outside the galaxy (cite: maiolino2015; carniani2017). We further discuss the physical origins of the \[C ii\] offset in Section [4.4](#sec:extended).

We also find that the emission in the F444W filter is extended more than the rest-frame UV and optical continuum observed in F150W and F356W filters. We interpret this extended emission attributed to strong emission lines of \[O iii\]5007 and H$\beta$ from ID4590, implying that a powerful mechanism of forming the extended ionized gas structure is taking place. Note that there are two nearby objects towards the East with offsets of $\simeq0.4\ensuremath{''}$ and $\simeq0.8\ensuremath{''}$. We run the SED fitting code `EAZY` (cite: brammer2008) for these two nearby objects with the available *JWST*/NIRCam, MIRI, and *HST* photometry in the public `grizli` catalog (Section [2.3](#sec:jwst)) by using the default template set of `tweak_fsps_QSF_12_v3`. The results suggest the photometric redshifts of $z_{\rm phot}=8.45^{+0.29}_{-0.28}$ and $z_{\rm phot}=0.37^{+0.11}_{-0.10}$ each from the nearest. Therefore, the nearest object might be a companion galaxy associated with ID4590. However, if the presence of nearby objects is the cause of the extended structure, the same structure should also be observed in the other NIRCam filters, which is not the case. Besides, the structure is also extended towards South $\sim$ Southeast, where no rest-frame UV continuum is identified. Furthermore, the PSF size of the NIRCam/F444W filter is $\sim0.15\ensuremath{''}$, where the emission should be individually resolved if the extended ionized gas is caused by individual further faint satellites. We thus conclude that this diffuse, extended structure in the F444W filter is hardly explained either by these two nearby objects or further faint satellites. The structure extends to $\sim0.5\ensuremath{''}$ towards the Southeast most. Given the circularized rest-frame optical effective radius of $0.059\ensuremath{''}\pm0.010\ensuremath{''}$ (Section [3.3](#sec:size)), the structure extends out to $\sim8$ times more than the stellar distribution of the galaxy. If we take the differential magnification effects into account, the structure is aligned to the radial magnification axis ($\mu_{\rm rad.}=1.37$), indicating that the intrinsic physical distance after the lens correction is $\sim1.7$ kpc. For the same direction, the rest-frame optical effective radius after the lens correction is estimated to be $0.11 \pm 0.03$ kpc. These results suggest that the ionized gas distribution over the effective radius of the stellar distribution even increases to a factor of $\sim$15. The relative ratio of $>8$ is well beyond the diffused ionized gas (DIG) structure observed among local galaxies ($\sim$10% of the galaxy size; see e.g., (cite: rossa2003b)). We further discuss the physical origins of the extended ionized gas in Section [4.4](#sec:extended).

By comparing the total flux correction factors in F356W and F444W filters (Section [2.3](#sec:jwst)), we find that the extended component in F444W contributes to the total flux measurement by $\sim8$%. In the following analyses when studying the same emitting regions[^12], we remove this 8% contribution of the extended ionized gas to the total flux measurement in the F444W filter. With the same motivation for analyses that assume the emission originated from the same regions, we also use the 3$\sigma$ upper limit for the \[C ii\] luminosity at the galaxy position imfit (Section [3.2](#sec:alma_measurement)).

## FIR SED

![](MBB_v4.pdf)

From the upper limits of the dust continuum both in Band 5 and Band 7, we attempt to constrain the FIR SED of ID4590. Recent FIR SED studies for high-$z$ dusty star-forming galaxies at $z\sim1$–4, including *Herschel* and ALMA photometry, suggest the typical dust temperature of $T_{\rm d}\sim30$ K (cite: swinbank2014; sun2022). For UV-selected galaxy populations such as Lyman-break galaxies (LBGs) at $z\sim4$–7, ALMA multiple band observations show a higher dust temperature distribution typically ranging from $\sim$40 K even out to $\sim$80 K (cite: faisst2020b; bakx2020; akins2022; witstok2022), where several analytical models have been developed and well reproduced the observation results, including the potential redshift evolution of $T_{\rm d}$ (cite: inoue2020; fudamoto2022a; sommovigo2022).

Because of the limited constraints due to lack of the detection in both ALMA Bands, we assume the single modified black body (MBB) for the FIR SED of ID4590. We adopt a fiducial $T_{\rm d}$ estimate of 60 K based on the extrapolation of the best-fit redshift evolution model of $T_{\rm d}$ following the decrease of the gas depletion time scale ($t_{\rm depl}$) derived in (cite: sommovigo2022), while we include the uncertainty of $T_{\rm d}$ by 30 K given the $T_{\rm d}$ distribution so far observed in high-$z$ LBGs with ALMA. We fix dust spectral index $\beta_{\rm d}$ at a typical value of 1.8 (cite: chapin2009; planck2011) and take the CMB temperature effect (cite: dacunha2013) into account in the MBB model.

In Figure [3](#fig:fir_sed), we show three MBB models with $T_{\rm d}=30$ K, 60 K, and 90 K normalized to the upper limit of Band 7. The inset labels show the derived IR luminosity $L_{\rm IR}$, integrated over 8–1000 $\mu$m, and the dust mass $M_{\rm dust}$, with the dust opacity coefficient of $\kappa_{\nu}=5.1(\nu/\nu_{250\mu{\rm m}})^{\beta_{\rm d}}$. In the observed frame (i.e. no lens correction), we obtain the upper limits of $\log(L_{\rm IR}/L_{\odot})<11.2$ and $\log(M_{\rm dust}/M_{\odot})<6.0$ with the fiducial $T_{\rm d}$ value of 60 K. This indicates that ID4590 has the observed-frame dust-obscured SFR of SFR$_{\rm IR}<16\,M_{\odot}$ yr$^{-1}$. The FIR SED properties are summarized in Table [2](#tab:property).

![](NIRCam_full_SED_ID4590_v2.pdf)

## Full SED analysis and physical properties

| Name | ID4590  |
|:---|:--:|
| R.A. | 07:23:26.255 |
| Dec. | $-73$:26:57.041 |
| $z_{\rm spec}$ | 8.496 |
| $\mu^{\dagger}$ | 8.69 |
| SFR $\times\mu$ \[$M_{\odot}$ yr$^{-1}$\] | 26$^{+9}_{-4}$ |
| $M_{\rm star}\times\mu$ \[$10^{8}\, M_{\odot}$\] | 5.3$^{+5.6}_{-2.6}$ |
| $L_{\rm UV}\times\mu$ \[10$^{10}$ $L_{\odot}$\] | $2.8\pm0.3$ |
| $\beta_{\rm UV}$ | $-1.70\pm0.07$ |
| $E(B-V)$ | $0.16\pm0.03$ |
| $L_{\rm IR}^{\dagger\dagger}\times\mu$ \[$10^{11}\,L_{\odot}$\] | $<1.6$ |
| $M_{\rm dust}^{\dagger\dagger}\times\mu$ \[$10^{6}\,M_{\odot}$\] | $<1.0$ |
| $M_{\rm gas}\times\mu$ \[$10^{9}\,M_{\odot}$\] | $7\pm3^{a}$ |
| $r_{\rm e, UV}^{\natural}\times \sqrt{\mu}$ \[arcsec\] | $0.056\pm0.012$ |
| $r_{\rm e, opt}^{\natural}\times \sqrt{\mu}$ \[arcsec\] | $0.059\pm0.010$ |
| $r_{\rm e, [CII]158}^{\natural}\times \sqrt{\mu}$ \[arcsec\] | $0.69 \pm0.42$ |
| $r_{\rm e, [OIII]88}^{\natural}\times \sqrt{\mu}$ \[arcsec\] | $< 0.16$ |
| $n_{\rm e}$ \[cm$^{-3}$\] | 220$^{+230}_{-130}$ |
| $T_{\rm e}$ \[10$^{4}$ K\] | $2.08\pm0.34^{b}$ |
| 12 + $\log$(O/H) | $7.26 \pm 0.18^{b}$ |
| $\log(U)$ | $>-2.27^{b}$ |
| $\log$(C/O) | $[-0.52:-0.24]^{c}$ |

: Physical properties of ID4590 in the image plane

$\dagger$ From the mass model with Glafic ((cite: oguri2010; oguri2021b)) using the *JWST* ERO data presented in (cite: harikane2022b). For the lens corrected values, we add a systematic uncertainty of 30% throughout the paper (Section [3.1](#sec:model)).\
${\dagger\dagger}$ Based on the single MBB with $T_{\rm d}=60$ K and $\beta_{\rm d}=1.8$ without the energy balance, where a $T_{\rm d}$ difference by $\pm30$ K changes the estimates by $\sim\pm$0.5–1.0 dex (see also Figure [3](#fig:fir_sed)).\
$\natural$ Circularized effective radius. The best-fit axis ratio is $0.57\pm0.09$.\
$a$ (cite: heintz2022c)\
$b$ (cite: nakajima2023)\
$c$ (cite: isobe2023b)

Figure [4](#fig:full_sed) shows the *JWST* and ALMA image cutouts, including the segmentation map (top), and the optical–mm photometry in the observed frame (i.e. no lens correction) measured with *HST*, *JWST*, and ALMA for ID4590 (bottom). A significant flux enhancement is observed in the F444W filter (rest-frame $\sim$4000–5000${\rm \AA}$). Some remarkably massive early galaxy candidates have been reported at $z\sim7$–11 whose SED shape shows a secondary peak, likely because of the strong Balmer break in the NIRCam LW filters (cite: labbe2022). However, the secondary peak might be explained by contributions from strong emission lines of \[O iii\]$\lambda$5007+H$\beta$ (cite: endsley2022b), where the lack of the longer wavelength data challenges drawing a definitive conclusion. In contrast, the presence of the MIRI photometry in ID4590 shows the flux enhancement only occurs in the F444W filter, which helps conclude that the flux enhancement in the F444W filter is caused by strong \[O iii\]+H$\beta$ emission lines, rather than a large stellar mass. Such strong contributions of the \[O iii\]+H$\beta$ lines also agree with the extended morphology observed in the F444W filter, which is interpreted as the presence of the extended ionized gas emission (Section [3.4](#sec:morph)).

To perform a panchromatic characterization of ID4590, we perform SED fitting to the optical–mm photometry using cigale (cite: burgarella2005; noll2009; boquien2019). While we examine the FIR SED in Section [3.5](#sec:fir_sed), the SED modelling with cigale allows us to take the energy balance between the dust absorption and re-emission into account, which is complementary with the independent FIR SED analysis. The fitting was performed similarly as in (cite: fujimoto2022b), and we summarize the details of the fitting and parameter ranges used in the fitting in the Appendix.

In the bottom panel of Figure [4](#fig:full_sed), the blue curve shows the best-fit SED, where the brown curve highlights the re-emission of the dust in the rest-frame FIR wavelength based on the (cite: casey2012) model. The inset panel shows the zoom-in spectrum of the best-fit SED at $\sim$1–9 $\mu$m. Our best-fit SED reproduces the observed photometry, including the flux enhancement in the F444W filter with the reduced $\chi^{2}$ value of 0.99. We obtain the best-fit values of SFR = 26$^{+9}_{-4}\,M_{\odot}$ yr$^{-1}$, $M_{\rm star}=5.3^{+5.6}_{-2.6}\times10^{8}\, M_{\odot}$, UV continuum slope $\beta_{\rm UV}=-1.70\pm0.07$, and $E(B-V)=0.16\pm0.03$ in the observed-frame (i.e. no lens correction), respectively, that are generally consistent with previous NIRcam and/or NIRspec based measurements (cite: carnall2022; schaerer2022; tacchella2022), as well as an independent NIRCam and NIRISS based measurements in the separated paper of (cite: heintz2022c). The $\log(L_{\rm IR}/L_{\odot})$ value is estimated to be $11.2$, which is consistent with the upper limit obtained from the independent FIR SED analysis (Section [3.5](#sec:fir_sed)). This indicates that the current non-detection of the dust continuum with ALMA does not violate the energy balance with the SMC dust attenuation curve, while the $\beta_{\rm UV}$ and $E(B-V)$ values suggest that ID4590 is a certainly dust-attenuated system, in contrast to very blue galaxies observed in recent *JWST* observations at similar redshifts (cite: nanayakkara2022; furtak2022; cullen2022; topping2022b; finkelstein2023; atek2022; fujimoto2022b; robertson2022). Note that we confirm that the SED outputs are unchanged beyond 5–10% with and without the ALMA upper limits in the above SED fitting with cigale. We further examine the dust and the obscured properties of ID4590 in Section [4.3](#sec:irx) and discuss the potential underlying physical mechanisms in Section [4.4](#sec:extended).

Because several Balmer emission lines are detected in ID4590 with NIRSpec, we compare our best-fit $E(B-V)$ with the measurement from the Balmer decrement. The line flux measurements from the latest NIRSpec reduction and calibration (Section [2.3](#sec:jwst)) yield $E(B-V)=0.07^{+0.10}_{-0.07}$ and $0.24^{+0.07}_{-0.07}$ from H$\gamma$/H$\beta$ and H$\delta$/H$\beta$, respectively, by assuming the SMC dust attenuation law. Our SED-based estimate falls between those estimates from the Balmer decrement approach, suggesting the general consistency between the photometry- and spectroscopic-based approaches. However, caution remains in the different $E(B-V)$ suggested between H$\gamma$/H$\beta$ and H$\delta$/H$\beta$, where the difference can change the H$\beta$-based SFR estimate (cite: kennicutt2012) by a factor of $\sim$3 after the dust correction. We confirm that similarly different $E(B-V)$ values are obtained by assuming other dust attenuation laws (e.g., LMC, (cite: calzetti2000)), and thus the difference is unlikely caused by an improper choice of the dust attenuation law. We speculate that it is caused by the difficulty of the optimal wavelength-dependent slit-loss correction for each emission, taking their potential differential distributions. We thus use the SED-based physical properties in the following analysis.

We note that (cite: clara2022b) discuss the potential underestimate of $M_{\rm star}$ by $\sim$0.5–1 dex in the spatially-integrated SED analysis, compared to the sum of the spatially-resolved SED analysis, especially in strong optical emission line systems [^13]. However, we confirm that our $M_{\rm star}$ estimate is consistent with the results from the spatially-resolved SED analysis in (cite: clara2022b), owing to the additional constraints from the MIRI bands (cite: bisigello2019; papovich2023).

![](ne_comb_v6.pdf)

# Results & Discussions

## Electron density at $z=8.5$ via \[O iii\]88$\mu$m/\[O iii\]$\lambda$5007

Owing to the same species and ionized state with different critical densities, the line ratio of \[O iii\]88$\mu$m/\[O iii\]$\lambda$5007 is regulated by the electron density $n_{\rm e}$ and temperature $T_{\rm e}$. In the left panel of Figure [5](#fig:ratio), we show the line ratio of \[O iii\]88$\mu$m/\[O iii\]$\lambda$5007 as a function of $T_{\rm e}$ with different assumptions for the electron density $n_{\rm e}$, drawn by using the nebular emission code `PyNeb`[^14]. The relations show monotonic decreasing functions towards the increase of $T_{\rm e}$ or $n_{\rm e}$. This indicates that we can evaluate $n_{\rm e}$ with a secure $T_{\rm e}$ measurement (or vice versa – evaluate $T_{\rm e}$ with a secure $n_{\rm e}$ measurement).

The NIRSpec observations successfully detect the multiple nebular emission lines from ID4590 in rest-frame UV to optical wavelength, including \[O iii\]$\lambda$5007 and \[O iii\]$\lambda$4363, which provides us with the robust measure of $T_{\rm e}$ (e.g., (cite: schaerer2022; curti2022; trump2022); (cite: heintz2022c); (cite: nakajima2023)). In conjunction with the secure $T_{\rm e}$ measurement and our ALMA measurements (Section [3.2](#sec:alma_measurement)), we derive the \[O iii\]88$\mu$m/$\lambda$5007 line ratio for ID4590, and the red circle in the left panel of Figure [5](#fig:ratio) shows the relation. Based on the 1$\sigma$ uncertainties, we evaluate $n_{\rm e}=220^{+230}_{-130}$ cm$^{-3}$.

The $n_{\rm e}$ value has been typically measured by using density-sensitive line ratios such as \[S ii\]6716/6731, \[O ii\]3729/3726, and C iii\]1907/1909 (cite: kewley2019). Previous spectroscopic surveys have found the presence of the redshift evolution of $n_{\rm e}$: the typical $n_{\rm e}$ in local galaxies has increased from $n_{\rm e}\simeq30$ cm$^{-3}$ at $z\sim0$ (cite: herrera-camus2016) to $n_{\rm e}\simeq$100–200 cm$^{-3}$ at $z\sim1.5$ (cite: kaasinen2017; kashino2017), and to $n_{\rm e}\simeq$ 200–300 cm$^{-3}$ at $z\sim2$–3 (cite: steidel2014; sanders2016; davies2021).

Because of the required high spectral resolution and subsequently high sensitivity to resolve those rest-frame UV and optical doublet lines, the results have been generally limited at $z\lesssim3$, while recent rest-frame FIR observations have been exploring the $n_{\rm e}$ measurement even out to the EoR. By using a FIR fine-structure line ratio of \[O iii\]52$\mu$m and \[O iii\]88$\mu$m detected with ALMA, (cite: killi2022) estimate $n_{\rm e}<260$ cm$^{-3}$ in a dusty lensed star-forming galaxy at $z=7.13$, A1689-zD1 (cite: watson2015). Our measurement of a high electron density provides a new determination of $n_{\rm e}$ at EoR and is consistent with the results in A1689-zD1. For several $z\sim6$–9 galaxies with the \[O iii\]88$\mu$m and \[C ii\]158$\mu$m line measurements, (cite: vallini2021) show that their gas density $n_{\rm gas}$ generally fall within $\simeq100$–1000 cm$^{-3}$ by advancing analytical models for these FIR emission lines (cite: ferrara2019; vallini2020). Although systematic uncertainties remain in this approach due to the C/O abundance and the different emitting regions of the \[O iii\] and \[C ii\] lines that suggest $n_{\rm e}$ and $n_{\rm gas}$ are not identical, these $n_{\rm gas}$ measurements at similar redshift also in line with our $n_{\rm e}$ measurement for ID4590. Our measurement is also broadly consistent with recent NIRSpec measurements for $z\sim4-9$ galaxies using the \[O ii\] doublet (cite: isobe2023). In contrast, (cite: stark2017) use the C iii\] doublet and estimate $n_{\rm e}=9100^{+12200}_{-7800}$ cm$^{-3}$ in EGS-zs8-1, a UV-luminous star-forming galaxy at $z=7.73$, which is much higher than those of our and recent measurements with the \[O iii\]88$\mu$m line.

In the right panel of Figure [5](#fig:ratio), we summarize the $n_{\rm e}$ measurement as a function of redshift. The $n_{\rm e}$ value of ID4590 is similar to $z\sim2$–3 star-forming galaxies. This might suggest that the physical mechanisms responsible for driving the high $n_{\rm e}$ values observed at $z\sim$2–3 initially took place in the EoR, and there was a little redshift evolution between $z=8.5$ and $z\sim$2–3, albeit the diversity observed with EGS-zs8-1. However, this redshift trend strongly depends on the galaxy types selected, and similarly high $n_{\rm e}$ measurements ($\simeq400$ cm$^{-3}$) are also obtained in compact star-forming galaxies at $z\sim0.3$–0.4 (cite: guseva2020). Moreover, given the similar high ionization potentials between C iii\] and \[O iii\]88$\mu$m emission lines, but much lower critical density of \[O iii\]88$\mu$m ($\sim500$ cm$^{-3}$), the different $n_{\rm e}$ results between the C iii\] and \[O iii\]88$\mu$m measurements might indicate these emission lines generally arise from different regions with different $n_{\rm e}$ values, where we are witnessing the differential $n_{\rm e}$ distributions inside H ii regions. The upcoming *JWST*/NIRSpec observations in the high-resolution spectrograph mode ($R\sim2700$) will sufficiently resolve the rest-frame UV and optical doublet lines, statistically evaluate $n_{\rm e}$ based on a mass-complete sample, verify the presence of its redshift evolution and/or differential $n_{\rm e}$ distributions traced by different emission lines, and determine what key mechanisms regulate $n_{\rm e}$ out to the EoR.

![](SFR-Lline_v7a.pdf)

![](SFR-Lline_v7b.pdf)

## SFR–$L_{\rm [CII]}$, $L_{\rm [OIII]}$, and $L_{\rm [OIII}/L_{\rm [CII]}$ Relations

In Figure [6](#fig:sfr_line) and [7](#fig:sfr_line2), we present $L_{\rm [CII]}$, $L_{\rm [OIII]}$, and $L_{\rm [OIII]}/L_{\rm [CII]}$ as a function of SFR for ID4590. We show the results after the lens correction, where the systematic uncertainty of 30% for the magnification factor (Section [3.1](#sec:model)) is propagated in the error bars. In SFR–$L_{\rm [CII]}$ (SFR–$L_{\rm [OIII]}/L_{\rm [CII]}$) relation, we also show the $3\sigma$ upper limit (lower limit) for $L_{\rm [CII]}$ ($L_{\rm [OIII]}/L_{\rm [CII]}$) at the *JWST* source position, given its spatial offset (Section [3.4](#sec:morph)), and separate the results inside and outside the galaxy with filled and open circles, respectively. For comparison, we also present compilations of recent ALMA results for $z\sim6$–9 galaxies in literature (cite: harikane2020; fujimoto2021) with black squares, and local dwarf galaxy results with the gas-phase metallicity ($Z_{\rm gas}$) measurements (cite: delooze2014; cormier2015) with color circles. The color scale is equal to 12+$\log$(O/H) denoted in the color bar, except for the $z\sim6$–9 galaxy results whose $Z_{\rm gas}$ values have not been constrained. The average relation for the local dwarf galaxies is shown in the dashed black line with the 1$\sigma$ range in the grey shade. In all relations, ID4590 are generally consistent with the results estimated in other $z\sim6$–9 galaxies. In addition, ID4590 explores the faint-end of the $z\sim$6–9 galaxy results, owing to the aid of the gravitational lensing effect. Therefore, ID4590 is a faint, thus abundant, and representative early galaxy with physical properties similar to other galaxies so far observed with ALMA at similar redshifts. This indicates that ID4590 is a unique laboratory to study what regulates the FIR major coolant lines of \[C ii\]158$\mu$m and \[O iii\]88$\mu$m in EoR galaxies.

In the SFR–$L_{\rm [CII]}$ relation, we find that ID4590 falls below the typical relation of the local dwarf galaxies in both results obtained inside and outside the galaxy. Among the local dwarf galaxies, there are two galaxies of IZw18 and SBS0335-052 whose $Z_{\rm gas}$ measurements are similarly low as ID4590 (12+$\log$(O/H) $\simeq$ 7.1–7.3). We confirm that the $\log(L_{\rm [CII]}$/SFR) ratio inside the galaxy shows $<6.3$, which is consistent with these two very metal-poor local galaxies ($\sim5.7$). This might indicate that the low \[C ii\] line emissivity of ID4590 is explained by the low $Z_{\rm gas}$ ISM condition (cite: vallini2015), while there are also other key factors which reduce the \[C ii\] emissivity such as high ionization parameter or low gas density (see Section [1](#sec:intro)). In fact, ID4590 shows strong \[O iii\]$\lambda$5007+H$\beta$ emission (Section [3.6](#sec:full_sed)), which generally represents recent young bursty stellar populations (cite: topping2022; witstok2022), where the high ionization parameter, as a result, might be a more critical driver. The \[C ii\] emission outside the galaxy shows $\log(L_{\rm [CII]}$/SFR)$\sim6.7$, being higher than these very metal-poor local galaxies but still lower than the typical relation. This might be explained by a huge amount of gas around ID4590 which efficiently uses all the photons to boost the \[C ii\] emission eventually. With an analytical model, (cite: ferrara2019) predict that the surface density of \[C ii\] luminosity becomes almost constant around $\Sigma_{\rm [CII]}\approx10^{6}-10^{7}\,L_{\odot}$ yr$^{-1}$ kpc$^{-1}$ at a high SFR surface density regime of $\Sigma_{\rm SFR}\gtrsim10\,M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ with a linear scale dependence on the gas density, regardless of $Z_{\rm gas}$ in 0.1–1.0 $Z_{\odot}$ (see eq. 42 in (cite: ferrara2019)). Based on our size and full SED analyses in Section [3](#sec:analysis), ID4590 indeed shows $\Sigma_{\rm [CII]}\simeq2\times10^{6}\,L_{\odot}$ yr$^{-1}$ kpc$^{-2}$ with $\Sigma_{\rm SFR}\simeq100\,M_{\odot}$ yr$^{-1}$ kpc$^{-2}$, which agrees with the prediction from the analytical model. For more discussions related to the rich gas aspect around ID4590, we refer the reader to a separate paper by (cite: heintz2022c).

In the SFR–$L_{\rm [OIII]}$ relation, we find that ID4590 is consistent with the local relation within the errors but likely falls slightly below it. This would also be explained by the low \[O iii\] line emissivity with low $Z_{\rm gas}$ values (cite: popping2022), which is also shown in the monotonic decreasing function in the \[O iii\]88/\[O iii\]$\lambda$5007–$T_{\rm e}$ relation, regardless of $n_{\rm e}$ (Figure [5](#fig:ratio)). In fact, the slightly low $\log(L_{\rm [OIII]}$/SFR) ratio of ID4590 is consistent with those of the two very metal-poor local galaxies of IZw18 and SBS0335-052 ($\sim6.5$) within the errors. We also confirm that the SFR-$L_{\rm [OIII]}$ relation of ID4590 is consistent with the serra zoom-in simulation results (cite: pallottini2022; kohandel2022) for galaxies whose $\log(U)$ values are similar to that of ID4590 ($\log(U)>-2.27$; Section [2.3](#sec:jwst)).

In the SFR–$L_{\rm [OIII]}/L_{\rm [CII]}$ relation, we find that ID4590 shows higher $L_{\rm [OIII]}/L_{\rm [CII]}$ ratios both inside and outside the galaxies than the local relation. In particular, the lower limit of $>4$ obtained inside the galaxy is similarly high to other $z\sim6$–9 galaxies so far observed (cite: harikane2020; witstok2022). We discuss the physical origins of the high \[O iii\]/\[C ii\]line ratio in Section [4.5](#sec:oiii-cii_ratio).

## IRX-$\beta$ relation

![](IRX-beta_v4.pdf)

Figure [8](#fig:irx) presents the infrared excess ($L_{\rm IR}/L_{\rm UV}\equiv$ IRX) and the UV continuum slope $\beta_{\rm UV}$ relation of ID4590. Although we adopt the fiducial value of $T_{\rm d}=60$ K in Section [3.5](#sec:fir_sed), here we show two extreme cases for ID4590, with $T_{\rm d}=$30 K and 90 K, by assuming the potential uncertainty of $\Delta T_{\rm d}=\pm30$ K. For comparison, we also show the relations based on several dust attenuation laws (cite: reddy2018; calzetti2000), a semi-analytical model of SHARK[^15] for galaxies at $z\sim8$ (cite: lagos2020), and the recent measurements for $z\sim$4–7 star-forming galaxies observed in the ALPINE (cite: lefevre2020) and REBELS surveys (cite: bouwens2021) taken from (cite: fudamoto2021) and (cite: inami2022), respectively. While several Balmer emission lines are detected in ID4590, we note that concluding which dust attenuation law fits the best with ID4590 is still challenging with their current S/N and the potential difficulty of the proper aperture correction for each Balmer emission (Section [3.6](#sec:full_sed)).

In Figure [8](#fig:irx), ID4590 falls in a moderately red UV color regime, where the dust continuum is detected from the previous ALMA observations for the $z\sim$ 4–7 galaxies. If ID4590 has a relatively low $T_{\rm d}$ ($\sim$30–40 K) and follows a dust attenuation law similar to (cite: calzetti2000) or SMC in (cite: reddy2018), the upper limit suggests that the dust continuum should be detected from ID4590 with the current ALMA depth[^16]. This indicates that ID4590 has a $T_{\rm d}$ value higher than $\sim$30–40 K or an SMC-like steep dust attenuation law with the intrinsic UV continuum slope of $\beta_{\rm UV,0}\simeq-2.3$ (cite: meurer1999; mclure2018). Given the low dust content implied from the low metallicity of ID4590 from the NIRSpec results (Section [2.3](#sec:jwst)) and the high $\Sigma_{\rm SFR}$ from the compact rest-frame UV size (Section [3.3](#sec:size)), the dust is efficiently heated at a given UV field (cite: behrens2018; sommovigo2022; sommovigo2022b), and the former high $T_{\rm d}$ scenario might be plausible. We also find that the semi-analytical model of SHARK predicts the IRX–$\beta_{\rm UV}$ relation even lower than the SMC relation for the simulated galaxies with similar redshift and $M_{\rm star}$ as ID4590, the non-detection of the dust could be simply because of the difference of the dust attenuation law between local and high-$z$ galaxies.

Future ALMA high-frequency follow-up observations (e.g., Band 8, 9, and 10) will confirm or rule out the high $T_{\rm d}$ scenario in ID4590. Furthermore, the detection of the rest-frame UV–optical continuum and/or multiple high-significance detection of Balmer and Paschen emission lines in upcoming *JWST*/NIRSpec and MIRI observations will help us to directly constrain the dust attenuation curve in high-redshift galaxies, including ID4590.

## Onset of outflow at $z>8.5$, facilitating reionization

In Figure [2](#fig:nircam), we find the spatial offset of \[C ii\] from the *JWST* source position (Section [3.4](#sec:morph)). The spatial offset suggests the presence of the accreting/satellite gas clump(s) (cite: maiolino2015) or the extended \[C ii\] gas beyond the stellar distribution (cite: fujimoto2019; fujimoto2020b; ginolfi2020; carniani2020; herrera-camus2021; akins2022; lambert2022), tracing the diffuse neutral hydrogen (cite: heintz2021; heintz2022). The \[C ii\] size measurement result, almost $\sim10$ times larger than the stellar distribution of ID4590 (Section [3.3](#sec:size)), supports the latter scenario of the presence of the extended \[C ii\] gas. Although we cannot rule out the possibility that the noise fluctuation makes the \[C ii\] morphology look extended with the current S/N, it is worth mentioning that similarly extended \[C ii\] morphology with spatial offsets have also been observed in other galaxies at $z\sim7$–9 (cite: carniani2020). The other possibility could be nearby faint, dusty objects (cite: fujimoto2016; fujimoto2022) emitting \[C ii\] (cite: romano2020; fudamoto2022). However, no counterparts are identified down to a 3$\sigma$ upper limit in F150W of $\sim$32.5 mag (with $0.2\ensuremath{''}$-diameter; (cite: harikane2022b)) after the lens correction, which corresponds to SFR $\approx0.05\,M_{\odot}$ yr$^{-1}$ at $z=8.5$ (cite: kennicutt2012). Similarly, no counterparts in F444W place a $3\sigma$ upper limit of $M_{\rm star}\lesssim1\times10^{6}\,M_{\odot}$ by scaling the best-fit SED of ID4590. A pixel-based SED analysis in (cite: clara2022b) shows the gradient of the dust obscuration decreasing towards the \[C ii\]-emitting region, which also supports the absence of the counterparts at the \[C ii\] peak position.

Whichever the \[C ii\]-emitting gas is compact clump(s) diffuse & extended, these results suggest that the carbon in the gas is illuminated not by local star-forming activities, but by i) the ionizing photon escaped from inside the galaxy, ii) shock heating of the outflowing gas, or iii) a cooling process of the hot outflowing gas (cite: fujimoto2019; fujimoto2020b; pizzati2020; akins2022). In Figure [6](#fig:sfr_line), we find that the $L_{\rm [CII]}$/SFR ratio of this \[C ii\] emission outside of galaxy is consistent with other local dwarf galaxies whose $Z_{\rm gas}$ values are similarly low as ID4590 (IZw18 and SBS0335-052). This suggests that the input energy from i) is enough to explain the observed $L_{\rm [CII]}$. In fact, the high ionization parameter of $\log(U)\gtrsim-2$ observed in ID4590 is in line with the scenario of i).

In Figure [2](#fig:nircam), we also find the extended ionized gas (\[O iii\]$\lambda$5007, H$\beta$) structure in the deep NIRCam/F444W filter (Section [3.4](#sec:morph)). Similar to the \[C ii\] emission, no NIRCam counterparts are identified in the extended ionized gas regions. In addition, the extended ionized gas regions are also not matched with the direction of the high dust obscuration gradient, which denies the possibility that the obscured star-forming regions cause the extended ionized emission. Based on the size measurement results in the image plane (Section [3.3](#sec:size)) and the different radial and tangential magnifications (see middle panel of Figure [2](#fig:nircam)), the ionized \[O iii\]$\lambda$5007+H$\beta$ structure extends out to $>8$ times more than the effective radius of the stellar distribution of ID4590 (Section [3.4](#sec:morph)). Same as \[C ii\], i)–iii) are the possible physical origins of the extended ionized gas emission. Interestingly, from the center of ID4590, the regions of the extended ionized gas distribution ($\sim$Southeastern) and the peak position of the \[C ii\] emission ($\sim$Northern) are in different directions. This might indicate that the differential distributions of the nebular parameters, such as $n_{\rm e}$, $Z_{\rm gas}$, $\log(U)$, and C/O abundance cause these differential distributions, even if the same physical process is taking place, either of i)—iii). The different morphology between \[O iii\]8̃8$\mu$m and \[O iii\]5007+H$\beta$ might also be attributed to the differential distributions of the nebular parameters, although the insufficient depth in the ALMA 88$\mu$m map could be another plausible cause.

Importantly, regardless of the true physical processes to give rise to an offset-\[C ii\] and extended \[O iii\]$\lambda$5007+H$\beta$ gas emission, the presence of the metal-enriched gas away from the galaxy is strong evidence of past and/or ongoing outflow activities already taking place in a low-mass ($M_{\rm star}=6\times10^{7}\,M_{\odot}$), metal-poor ($Z=0.04Z_{\odot}$) nascent galaxy at $z=8.496$. The presence of the extended carbon gas structure, so-called \[C ii\] Halo, has been reported around more massive ($M_{\rm star}>10^{9}$–10$^{10}\,M_{\odot}$) star-forming galaxies at $z=4-7$ (cite: fujimoto2019; fujimoto2020b; ginolfi2020; herrera-camus2021; akins2022; lambert2022), which is challenging to the current cosmological galaxy formation models ((cite: fujimoto2019); see also e.g., (cite: pizzati2020; arata2020; katz2022)). Our results in ID4590 provide new insight that such metal enrichment beyond the galaxy ISM scale starts to occur even in the very early phase of the galaxy assembly just $\sim$580 Myr after the Big Bang, which is likely linked to the origin of the \[C ii\] halo at a later epoch of the Universe.

Another important fact is that the presence of diffuse extended ionized gas around ID4590 directly indicates the high filling factor of the ionized gas, where the ionizing photons escaping from the galaxy may contribute to the Reionization. After the lens correction, ID4590 is $\sim5\times$ fainter than the characteristic UV luminosity of the UV luminosity function (UVLF) at $z\sim9$ ($M^{*}_{\rm UV}=-19.6$ mag; e.g., (cite: harikane2022b)). Once we confirm the high escape fraction of the ionizing photons from faint, low-mass galaxies, probably related to the onset of the outflow from the early stage of the galaxy assembly, it also provides us with a new insight into the process of the Reionization, in contrast to the scenario that huge ionized bubbles are formed around UV-bright galaxies ($M_{\rm UV}\lesssim-22$) at similar redshifts (cite: mason2018). The significantly low metallicity of ID4590, falling below the $z\sim8$ mass–metallicity relations predicted from current galaxy formation models (cite: curti2022), despite the dust obscuration in ID4590 ($\beta=-1.7\pm0.07$), may suggest that dust obscuration occurs in a part of the galaxy with a very low dust content. This may also be caused by the past or ongoing outflow activities (cite: ferrara2022; ziparo2022) that carry the dust away from the galaxy and make it diffuse, cold, and undetectable in the observations (cite: akins2022), while the dust in regions that are not invested by the outflow, or that are shielded by Giant Molecular Clouds, could survive (see also (cite: martinez-gonzalez2019; nath2022)). This small amount of surviving dust may be responsible for a certain amount of dust obscuration. In any case, the low dust content in the galaxy is also helpful for ionizing photons to escape from the system.

Note that diffuse ionized gases (DIGs) have been observed in local galaxies, from inter-arm regions (cite: zurita2000) to areas above the galactic mid-plane out to 1–2 kpc scales (cite: rossa2000). However, even in the latter case, the sizes of these DIGs are only about $\sim10$% relative to the size of the host galaxy (cite: rossa2003b). In contrast, the extended ionized gas structure around ID4590 is well beyond the central galaxy size (Section [3.4](#sec:morph)). Therefore, the physical origins of the extended ionized gas structure around ID4590 are likely different from those of the DIGs in the local Universe.

Another note is that we do not find evidence of the ongoing outflow via the broad-wing feature in the NIRSpec spectrum. However, the slit of the NIRSpec MSA is aligned perpendicular to the extended ionized gas structure (See the white rectangle in Figure [2](#fig:nircam)), which might be the reason for the absence of the broad-wing feature in the current NIRSpec spectrum.

![](comp_CLOUDY_v9.pdf)

## Physical origins of the high \[OIII\]88$\mu$m/\[CII\]158$\mu$m ratio

Previous ALMA observations reported the detections of the luminous \[O iii\]88$\mu$m line from star-forming galaxies at $z\sim$ 6–9, showing their \[O iii\]88$\mu$m/\[C ii\]158$\mu$m line ratio of $\gtrsim3$–10 that are higher than local dwarf galaxies and/or local Luminous Infrared Galaxies (LIRGs) with similar SFRs (cite: inoue2016; harikane2020; witstok2022). The origin of such high ratios is still unclear. Major solutions that have been argued include a) observational bias (cite: carniani2020), b) low C/O abundance ratio (cite: katz2022), c) low covering fraction of PDRs[^17] $C_{\rm PDR}$ (cite: cormier2015; harikane2020), and d) the characteristic ISM parameters in early galaxies such as the high ionization parameter (cite: katz2017; harikane2020) probably caused by recent strong bursts of star-formation (cite: ferrara2019; arata2020; vallini2021; witstok2022; sugahara2022) and/or low stellar-to-gaseous metallicity ratio (cite: sugahara2022).

In Section [6](#fig:sfr_line), we find that ID4590 also shows a similarly high \[O iii\]88$\mu$m/\[C ii\]158$\mu$m line ratio of $>4$ at the galaxy position. In addition to the accurate measures of $Z_{\rm gas}$ and $n_{\rm e}$ (Section [4.1](#sec:line_ratio)), the deep NIRSpec observations also cover the \[O ii\]3729 and C iii\]1909 emission lines from ID4590, which allow us to constrain the ionization parameter $\log(U)$ (e.g., (cite: schaerer2022; curti2022; brinchmann2022; trump2022); (cite: heintz2022c); (cite: nakajima2023)) and the C/O abundance in ID4590 (e.g., (cite: arellano2022); (cite: isobe2023b)). This indicates that we can investigate the physical origins of the high \[O iii\]88$\mu$m/\[C ii\]158$\mu$m line ratio, taking the possible solutions of b) and d) into account via the actual observed measurements for ID4590. Besides, the spatial offset of the \[C ii\] line (Section [3.4](#sec:morph)) allows us to separate the emission arising inside and outside the galaxy and fairly compare the line ratio, also managing the observational bias of point a). Therefore, with this best optical–mm characterization of an early galaxy owing to the joint *JWST* and ALMA analysis, we are ready to address the physical origins of the high \[C ii\]/\[O iii\] and verify whether the remaining possible solution of c) is critical or other solutions can answer already.

In Figure [9](#fig:cloudy), we show the $L_{\rm [OIII]}/$SFR and $L_{\rm [CII]}/$SFR relation of ID4590. Given the purpose of the analysis, we use the \[C ii\] results at the galaxy position. For comparison, we also present the relations from observations (left panel) and the predictions from the photoionization model with cloudy (right panel) drawn in the same manner as (cite: harikane2020) (see also (cite: sugahara2022)), where the possible shifts on the plane by b), c), and d) are presented with black arrows (cite: harikane2020). We also show the magenta-shaded region that corresponds to the possible space for ID4590 calculated by Cloudy with our fiducial estimates of $Z_{\rm gas}/Z_{\odot}=0.04\pm0.02$, $n_{\rm e}=220^{+230}_{-130}$ cm$^{-3}$, $\log(U)>-2.27$, and $\log$(C/O)=$[-0.52:-0.26]$. Following (cite: harikane2020), we use the SFR value based on the dust-corrected H$\alpha$ luminosity estimated from NIRSpec (Section [2.3](#sec:jwst)), instead of the SED-based value, for this analysis.

In the left panel, we find that ID4590 shows the $L_{\rm [OIII]}$/SFR ratio much higher than local LIRGs, falling on the high \[O iii\]/\[C ii\] line ratio regime similar to other $z\sim6$–9 galaxies. We also find that several metal-poor galaxies (12+$\log(O/H)\lesssim8.0$) among the local dwarf galaxies are located in the similarly high \[O iii\]/\[C ii\] line ratio regime to these $z\sim6$–9 galaxies. This may suggest that the ISM conditions of these $z\sim6$–9 galaxies are similar to those of the local metal-poor galaxies, while an important note is that these local metal-poor galaxies have much lower SFRs than these $z\sim6$–9 galaxies by $\sim$1–2 orders of magnitudes.

In the right panel, we find that the observed $L_{\rm [OIII]}$/SFR and $L_{\rm [CII]}$/SFR relation of ID4590 is consistent with the magenta-shaded region within the errors. This indicates that the \[C ii\] and \[O iii\] emissivities at a given input energy in ID4590 are generally explained by the combination of high $\log(U)$, high $n_{\rm e}$, low $Z_{\rm gas}$, and low $\log$(C/O). Therefore, the physical origin of the high \[O iii\]/\[C ii\] ratio observed among $z\sim6$–9 galaxies may be sufficiently explained by b) and d).

As discussed in (cite: harikane2020), another possible origin of c) – the low $C_{\rm PDR}$ – could also be the additional reason to boost the \[O iii\]/\[C ii\] ratio. As indicated in the black arrow, this effect makes the data points horizontally to move to the left in Figure [9](#fig:cloudy) (i.e., towards low \[C ii\]/SFR). Because the current $\log(U)$ estimate provides the upper limit alone, the possible parameter space of ID4590 extends to the low $L_{\rm [CII]}$/SFR regime, where we cannot disentangle the contributions from $\log(U)$ and $C_{\rm PDR}$. Once the upper boundary of $\log(U)$ is constrained, the lower limit of the $L_{\rm [CII]}$/SFR ratio in the possible parameter space will be determined, where the additional $C_{\rm PDR}$ contribution will be evaluated if the observed $L_{\rm [CII]}$/SFR upper limit is lower than the possible parameter space. With future deep \[C ii\] follow providing a much more stringent upper limit or the faint detection of \[C ii\], we may be able to investigate further the additional contribution from $C_{\rm PDR}$.

# Summary

In this paper, we present the ALMA Band 7 and Band 5 deep spectroscopy for the two major coolant FIR lines of \[O iii\]88 $\mu$m and \[C ii\]158 $\mu$m from ID4590, a metal-poor, low-mass, strongly lensed sub-$L^{*}$ galaxy at $z=8.496$, whose warm interstellar medium and stellar properties have been the best characterized with the *JWST* Early Release Observations (ERO) for the SMACS0723 field. The *JWST* ERO observations include the deep imaging with NIRCam and MIRI at $\sim$1–20 $\mu$m as well as deep spectroscopy with NIRSpec at $\sim$2–5 $\mu$m which detects multiple rest-frame optical emission lines, including \[O iii\]$\lambda$4363 line, and provides us with the robust measure of the gas-phase metallicity via the *direct* temperature method for the first time at $z\gtrsim3$. Combining these rich *JWST* data with *HST* and ALMA, the high-spatial-resolution, homogeneous data set from optical to mm wavelengths enables us to perform a panchromatic characterization of an early galaxy in and out, which sets the benchmark for synergetic studies of ALMA and *JWST* in the coming decades. The main findings of this paper are summarized as follows:

1.  We detect both \[C ii\]158$\mu$m and \[O iii\]88$\mu$m lines at 4.0$\sigma$ and 4.5$\sigma$ levels, respectively. The redshift and the spatial position of the \[O iii\] line exactly coincide with those of the *JWST* source. On the other hand, the \[C ii\] line is blue-shifted by 90 km $^{-1}$ and has a spatial offset by $\sim0.5\ensuremath{''}$ ($\approx0.5$ kpc in source plane) beyond the errors, where the chance projection of the noise fluctuation is very unlikely ($\sim0.07$%) from a blind line search analysis in the same data cube. This indicates that \[C ii\] velocity and spatial offsets are real and associated with some physical mechanisms of ID4590.

2.  We evaluate the sizes of \[C ii\], \[O iii\], rest-frame UV, and rest-frame optical continuum by using ALMA and *JWST*/NIRCam images. With the 2D profile fitting in the image plane, we obtain the best-fit circularized effective radii of $0.69\ensuremath{''}\pm0.42\ensuremath{''}$, $0.056\ensuremath{''}\pm0.012\ensuremath{''}$, and $0.059\ensuremath{''}\pm0.010\ensuremath{''}$ for \[C ii\], rest-frame UV, and rest-frame optical continuum, respectively. The \[O iii\] line is not spatially resolved with the current resolution and sensitivity, and we place its upper limit of $0.16\ensuremath{''}$. We find that the position angle estimated in the F150W filter shows an excellent agreement with the lensing distortion predicted from the mass model, validating the high magnification of $\mu=8.69$ in ID4590. The extended \[C ii\] distribution relative to the stellar continuum is reminiscent of the \[C ii\] Halo reported in recent ALMA studies, while we cannot exclude the possibility that the \[C ii\] size estimate is affected by the noise fluctuation with the current S/N.

3.  The dust continuum is not detected in neither Band 7 or Band 5, and we place 2$\sigma$ upper limits of 41.8 $\mu$Jy and 23.2 $\mu$Jy at 0.85 mm and 1.54 mm, respectively. By assuming a single modified black body with the dust temperature $T_{\rm d}=60$ K and the dust spectral index of $\beta_{\rm d}=1.8$, we estimate the upper limits of infrared luminosity over 8–1000 $\mu$m of $L_{\rm IR}<1.8\times10^{10}\,L_{\odot}$ and the dust mass of $M_{\rm dust}<1.2\times10^{5}\,M_{\odot}$ after the lens correction, while a different $T_{\rm d}$ assumption by $\pm30$ K changes these constraints by $\sim\pm$0.5–1.0 dex. The upper limit of infrared excess (IRX$\equiv L_{\rm IR}/L_{\rm UV}$) in ID4590 suggests that $T_{\rm d}$ is higher than $30$–40 K or that steep dust attenuation laws similar to SMC are favored.

4.  The NIRCam/F444W filter, including the contributions from \[O iii\]$\lambda$5007 and H$\beta$ emission lines, shows an extended structure where the rest-frame UV and optical continuum are invisible and the 3$\sigma$ upper limit in the rest-frame UV continuum after the lens correction are placed at 32.5 mag ($\approx0.05\, M_{\odot}$ yr$^{-1}$). Given the high-spatial-resolution of the F444W filter ($\sim0.15\ensuremath{''}$), the smooth morphology of the extended structure is the direct evidence of the presence of the extended, diffuse ionized gas structure around ID4590. The structure extends towards the radial magnification axis out to $\sim0.5\ensuremath{''}$. After the lens correction, this corresponds to $\sim1.7$ kpc and at least eight times larger than the rest-frame optical effective radius of ID4590.

5.  We perform the optical–mm SED analysis with *HST*, JWST/NIRCam+MIRI, and ALMA photometry. We exclude the emission outside of the galaxy observed in the F444W filter, and the remaining contribution of the strong emission lines of \[O iii\]$\lambda$5007+H$\beta$ and the stellar continuum is well separated by the rich filter sets of NIRCam and MIRI. After the lens correction, we estimate the stellar mass of $M_{\rm star}=6\times10^{7}\,M_{\odot}$, the total star-formation of SFR $=3\,M_{\odot}$ yr$^{-1}$, UV continuum slope of $\beta_{\rm UV}=-1.7$, suggesting that ID4590 is a low-mass, but a little dust attenuated galaxy, in contrast to very blue galaxies ($\beta_{\rm UV}<-2.0$) that have been observed in recent *JWST* observations at similar redshifts.

6.  Regardless of the ongoing physical mechanisms, past outflow activities are required to make the surrounding pristine gas of ID4590 metal-enriched and produce the \[C ii\] offset and the extended ionized gas structure traced by \[O iii\]$\lambda$5007+H$\beta$. This would also help produce high ionizing photon escape from ID4590 and contribute to reionization at $z>8.5$.

7.  With careful slit-loss correction and the separation of the emission inside and outside of the galaxy, we evaluate the electron density of $n_{\rm e}=220^{+230}_{-130}$ cm$^{-3}$ via the \[O iii\]88$\mu$m/\[O iii\]$\lambda$5007 line ratio. This is much higher than that of local galaxies ($n_{\rm e}\simeq30$ cm$^{-3}$), but consistent with $z\sim2$–3 galaxies ($n_{\rm e}\simeq200-300$ cm$^{-3}$). This is also consistent with the upper limit of $n_{\rm e}<260$ cm$^{-3}$ obtained in a lensed dusty galaxy at $z=7.13$.

8.  We examine relations between the line luminosities of \[C ii\]158$\mu$m, \[O iii\]88$\mu$m, and SFR. ID4590 shows $L_{\rm [CII]}$–SFR and $L_{\rm [OIII]}$–SFR relations generally consistent with other $z\sim6$–9 galaxies and explores the faint-end of the relations, owing to the aid of the lensing support. The $L_{\rm [CII]}$/SFR ratio of ID4590 falls below the typical relation estimated among the local dwarf galaxies beyond the errors. Still, it is consistent with similarly metal-poor local galaxies of IZw18 and SBS0335-052. The same result is obtained in the SFR–$L_{\rm [OIII]}$ relation, while the relation of ID4590 is still consistent with the typical range of the local dwarf galaxies within the errors. ID4590 shows a $L_{\rm [OIII]}/L_{\rm [CII]}$ ratio of $>4$, which is also as high as other $z\sim$6–9 galaxies, falling above the typical relation of the local dwarf galaxies in the SFR–$L_{\rm [OIII]}/L_{\rm [CII]}$ relation.

9.  We investigate the physical origins of the high $L_{\rm [OIII]}/L_{\rm [CII]}$ ratio with the photoionization model of Cloudy. The $L_{\rm [OIII]}$/SFR–$L_{\rm [CII]}$/SFR relation of ID4590 is generally reproduced by the high $n_{\rm e}$, low gas-phase metallicity ($Z_{\rm gas}/Z_{\odot}=0.04$), high ionization parameter ($\log(U)>-2.27$), and low carbon-to-oxygen abundance ratio $\log$(C/O)$=[-0.52:-0.24]$ obtained from the *JWST*/NIRSpec data. While the other potential mechanism of the low covering fraction of the photodissociation region is not constrained by the current data, it will be achieved by further deep ALMA \[C ii\] follow-up.

We thank the anonymous referee for constructive comments and suggestions. We also thank Catherine Vlahakis and Holly Sheets for their kind support in the processing of the ALMA data, despite the unusual circumstances due to the cyberattack. We are grateful to Pablo Albalo Halo for sharing deep insights into the NIRSpec data analysis and to Caitlin Casey, Steven Finkelstein, and Daniel Stark for helpful discussions for this paper. This paper makes use of the ALMA data: ADS/JAO. ALMA #2022.A.00022.S. ALMA is a partnership of the ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, AUI/NRAO, and NAOJ. This work is based on observations and archival data made with the *Spitzer Space Telescope*, which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA, along with archival data from the NASA/ESA *Hubble Space Telescope*. This research also made use of the NASA/IPAC Infrared Science Archive (IRSA), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration. The Early Release Observations[^18] and associated materials were developed, executed, and compiled by the ERO production team: Hannah Braun, Claire Blome, Matthew Brown, Margaret Carruthers, Dan Coe, Joseph DePasquale, Nestor Espinoza, Macarena Garcia Marin, Karl Gordon, Alaina Henry, Leah Hustak, Andi James, Ann Jenkins, Anton Koekemoer, Stephanie LaMassa, David Law, Alexandra Lockwood, Amaya Moro-Martin, Susan Mullally, Alyssa Pagan, Dani Player, Klaus Pontoppidan, Charles Proffitt, Christine Pulliam, Leah Ramsay, Swara Ravindranath, Neill Reid, Massimo Robberto, Elena Sabbi, Leonardo Ubeda. The EROs were also made possible by the foundational efforts and support from the JWST instruments, STScI planning and scheduling, and Data Management teams. This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 847523 ‘INTERACTIONS’ and from NASA through the NASA Hubble Fellowship grant HST-HF2-51505.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. The project leading to this publication has received support from ORP, that is funded by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 \[ORP\]. F.S. acknowledges support from the NRAO Student Observing Support (SOS) award SOSPA7-022. The Cosmic Dawn Center is funded by the Danish National Research Foundation under grant No. 140. K. Kohno acknowledges the support by JSPS KAKENHI Grant Number 17H06130 and the NAOJ ALMA Scientific Research Grant Number 2017-06B. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Software

casa (v6.4.1; (cite: casa2022)), `grizli` (cite: brammer2023), `EAZY`, (cite: brammer2008), `PyNeb` (cite: shaw1998) `CLOUDY`, (cite: ferland2017), `Interferopy`, (cite: boogaard2021), and `CIGALE` (cite: boquien2019) .

# Accuracy of the astrometry of *JWST* and *HST* maps from grizli

In Figure [10](#fig:astrometry), we show the residual spatial offsets of the Right ascension ($\Delta$R.A.) and Declination ($\Delta$Dec.) for the GAIA sources. We evaluate the residual offsets by running the source extractor (cite: bertin1996) on the *JWST* and *HST* maps produced by the `grizli` pipeline and being corrected for the proper motion effect of the GAIA sources, and comparing with those from the GAIA DR3 catalogs. We confirm that the average offset shows an excellent agreement with zero and the standard deviation in R.A and Dec. of $0.01\ensuremath{''}$ and $0.02\ensuremath{''}$, respectively. We regard these standard deviations as the positional uncertainty of the *JWST* sources in Figure [2](#fig:nircam).

![](offset_gaia_v1.pdf)

# CIGALE parameters for the full SED fit

We assume a delayed star-formation history (SFH): SFR($t$) $\propto t/\tau^{2}$ exp$(-t/\tau)$ with stellar models from (cite: bruzual2003) and an exponential recent burst implemented in the `sfhdeleyed` module. We use the `dustatt_modified_starburst` module for the dust attenuation, where the nebular emission (continuum + lines) are attenuated with a screen model and an SMC extinction curve (cite: pei1992). During the SED fitting, the same $E(B-V)$ is used between stellar and nebular emission. Finally, the dust emission is re-emitted in the infrared with (cite: casey2012) models. We fix $\beta_{\rm d}=1.8$ and the mid-infrared power-law slope $\alpha_{\rm d}=2.0$ and adopt the $T_{\rm d}$ range of 30–90 K. Because no evidence of the presence of AGN has been reported, we do not include an AGN component in the model. We list the modules and the parameter ranges used in the fitting in Table [\[Tab.CIGALE.Ph2\]](#Tab.CIGALE.Ph2). In the fitting, we use the photometry with the $1\sigma$ error also for the measurements below the $2\sigma$ upper limits. To avoid the lens model uncertainty, we perform the SED fitting with the optical–mm photometry without the lens correction.

|  | **Symbol** | **Range** |
|:---|:---|:---|
|  |  |  |
|  |  |  |
| e-folding time scale of the delayed SFH | $\tau_{main}$ \[Myr\] | , 250, 500, 1000 |
| Age of the main population | Age$_{main}$\[Myr\] | log values in \[1: 3.3\] |
| Burst | f$_{burst}$ | , 0.10, 0.15, 0.25 |
|  |  |  |
|  |  |  |
| SSP |  | BC03 |
| Initial mass function | IMF | Chabrier |
| Metallicity | Z | , 0.004, 0.02 |
|  |  |  |
|  |  |  |
| Ionization parameter | logU |  |
| Line width \[km/s\] | — |  |
| Gas-phase Metallicity | zgas | , 0.004, 0.02 |
| Electron density | ne |  |
|  |  |  |
|  |  |  |
| Color excess for both the old and young stellar populations | E_BV_lines | log values in \[$-3$: 1.3\] |
| Reduction factor to apply on E_BV_lines to compute E(B-V)s the stellar continuum attenuation | E_BV_factor |  |
| Bump amplitude | uv_bump_amplitude |  |
| Power law slope | power law_slope |  |
| Extinction law to use for attenuating the emission lines flux | Ext_law_emission_lines | SMC |
| Ratio of total to selective extinction, A_V / E(B-V) | Rv |  |
|  |  |  |
|  |  |  |
| Dust temperature | temperature | log values in \[1.5:1.95\] |
| Dust emissivity index | beta |  |
| Mid-infrared power law slope | alpha |  |
|  |  |  |
|  |  |  |

# HST/NIRcam/MIRI photometry of ID4590

We summarize the optical–mm photometry used in this paper in Table [3](#tab:photometry).

|    Filter    |      Flux (nJy)      |
|:------------:|:--------------------:|
|  HST/F105W   |    $-4.7\pm12.3$     |
|  HST/F125W   |    $44.5\pm13.8$     |
|  HST/F140W   |    $60.5\pm11.9$     |
|  HST/F160W   |    $61.7\pm14.7$     |
| NIRCam/F090W |    $-12.0\pm3.9$     |
| NIRCam/F115W |     $22.7\pm8.2$     |
| NIRCam/F150W |     $60.7\pm6.6$     |
| NIRCam/F200W |     $66.9\pm7.0$     |
| NIRCam/F277W |     $69.0\pm7.1$     |
| NIRCam/F356W |     $71.3\pm7.3$     |
| NIRCam/F444W |    $145.2\pm14.7$    |
|  MIRI/F770W  |    $92.2\pm38.0$     |
| MIRI/F1000W  |    $111.2\pm72.0$    |
| MIRI/F1500W  |   $314.1\pm234.4$    |
| MIRI/F1800W  |   $263.9\pm464.6$    |
|  ALMA/Band7  | $<41800\, (2\sigma)$ |
|  ALMA/Band5  | $<23200\, (2\sigma)$ |

: NIR–mm photometry of ID4590 used in this paper

# Size measurements

In Figure [11](#fig:size), we summarize the observed, the best-fit model, and the residual maps from the best-fit size measurements for the \[C ii\], \[O iii\], rest-frame UV and optical continuum emission using the ALMA and *JWST*/NIRcam. The methods are described in Section [3.3](#sec:size). We confirm that significant positive and negative pixels remain in the residual maps.

![](size_comb_v2.pdf)

natexlab

(ref: akins2022) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64

(ref: aller1984) Aller, L. H. 1984, Physics of thermal gaseous nebulae, doi:10.1007/978-94-010-9639-3

(ref: andrews2013) Andrews, B. H., & Martini, P. 2013, ApJ, 765, 140

(ref: arata2020) Arata, S., Yajima, H., Nagamine, K., Abe, M., & Khochfar, S. 2020, arXiv e-prints, arXiv:2001.01853

(ref: arellano2022) Arellano-Córdova, K. Z., Berg, D. A., Chisholm, J., et al. 2022, arXiv e-prints, arXiv:2208.02562

(ref: atek2022) Atek, H., Shuntov, M., Furtak, L. J., et al. 2022, arXiv e-prints, arXiv:2207.12338

(ref: bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294

(ref: behrens2018) Behrens, C., Pallottini, A., Ferrara, A., Gallerani, S., & Vallini, L. 2018, MNRAS, 477, 552

(ref: bertin1996) Bertin, E., & Arnouts, S. 1996, A&A, 117, 393

(ref: bisigello2019) Bisigello, L., Caputi, K. I., Colina, L., et al. 2019, ApJS, 243, 27

(ref: interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021a, Interferopy: analysing datacubes from radio-to-submm observations, doi:10.5281/ZENODO.5775603

(ref: boogaard2021) —. 2021b, Interferopy: analysing datacubes from radio-to-submm observations, doi:10.5281/ZENODO.5775603

(ref: boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: bouwens2022) Bouwens, R. J., Illingworth, G. D., Ellis, R. S., Oesch, P. A., & Stefanon, M. 2022, arXiv e-prints, arXiv:2205.11526

(ref: bouwens2015) Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 803, 34

(ref: bouwens2021) Bouwens, R. J., Smit, R., Schouws, S., et al. 2021, arXiv e-prints, arXiv:2106.13719

(ref: bowler2022) Bowler, R. A. A., Cullen, F., McLure, R. J., Dunlop, J. S., & Avison, A. 2022, MNRAS, 510, 5088

(ref: boyer2022) Boyer, M. L., Anderson, J., Gennaro, M., et al. 2022, Research Notes of the American Astronomical Society, 6, 191

(ref: bradley2022) Bradley, L. D., Coe, D., Brammer, G., et al. 2022, arXiv e-prints, arXiv:2210.01777

(ref: brammer2023) Brammer, G. 2023, grizli, please cite this software using these metadata., doi:10.5281/zenodo.7767790

(ref: brammer2021) Brammer, G., & Matharu, J. 2021, gbrammer/grizli: Release 2021, Zenodo, doi:10.5281/zenodo.5012699

(ref: brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: brinchmann2022) Brinchmann, J. 2022, arXiv e-prints, arXiv:2208.07467

(ref: broadhurst2005) Broadhurst, T., Takada, M., Umetsu, K., et al. 2005, ApJ, 619, L143

(ref: bruzual2003) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000

(ref: burgarella2005) Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, MNRAS, 360, 1413

(ref: calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: caminha2022) Caminha, G. B., Suyu, S. H., Mercurio, A., et al. 2022, A&A, 666, L9

(ref: carnall2022) Carnall, A. C., Begley, R., McLeod, D. J., et al. 2023, MNRAS, 518, L45

(ref: carniani2017) Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605, A42

(ref: carniani2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136

(ref: casey2012) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: chapin2009) Chapin, E. L., Pope, A., Scott, D., et al. 2009, MNRAS, 398, 1793

(ref: charlot2000) Charlot, S., & Fall, S. M. 2000, ApJ, 539, 718

(ref: christensen2012) Christensen, L., Laursen, P., Richard, J., et al. 2012, MNRAS, 427, 1973

(ref: coe2019) Coe, D., Salmon, B., Bradač, M., et al. 2019, ApJ, 884, 85

(ref: cormier2015) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2015, Astronomy and Astrophysics, 578, A53

(ref: cullen2022) Cullen, F., McLure, R. J., McLeod, D. J., et al. 2022, arXiv e-prints, arXiv:2208.04914

(ref: curti2022) Curti, M., D’Eugenio, F., Carniani, S., et al. 2022, arXiv e-prints, arXiv:2207.12375

(ref: dacunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: dale2014) Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, ApJ, 784, 83

(ref: davies2021) Davies, R. L., Förster Schreiber, N. M., Genzel, R., et al. 2021, ApJ, 909, 78

(ref: delooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: diaz-santos2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: ellis2013) Ellis, R. S., McLure, R. J., Dunlop, J. S., et al. 2013, ApJ, 763, L7

(ref: endsley2022b) Endsley, R., Stark, D. P., Lyu, J., et al. 2022, arXiv e-prints, arXiv:2206.00018

(ref: faisst2020b) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, arXiv:2005.07716

(ref: ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385

(ref: ferrara2022) Ferrara, A., Pallottini, A., & Dayal, P. 2022, arXiv e-prints, arXiv:2208.00720

(ref: ferrara2019) Ferrara, A., Vallini, L., Pallottini, A., et al. 2019, MNRAS, 489, 1

(ref: finkelstein2015) Finkelstein, S. L., Ryan, Russell E., J., Papovich, C., et al. 2015, ApJ, 810, 71

(ref: finkelstein2023) Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJ, 946, L13

(ref: fudamoto2022a) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2022a, arXiv e-prints, arXiv:2206.01879

(ref: fudamoto2022) —. 2022b, ApJ, 938, L24

(ref: fudamoto2020) Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, A&A, 643, A4

(ref: fudamoto2021) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: fujimoto2016) Fujimoto, S., Ouchi, M., Ono, Y., et al. 2016, ApJS, 222, 1

(ref: fujimoto2019) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107

(ref: fujimoto2020b) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: fujimoto2021) Fujimoto, S., Oguri, M., Brammer, G., et al. 2021, ApJ, 911, 99

(ref: fujimoto2022) Fujimoto, S., Brammer, G. B., Watson, D., et al. 2022, Nature, 604, 261

(ref: fujimoto2022b) Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023, ApJ, 955, 130

(ref: furtak2022) Furtak, L. J., Shuntov, M., Atek, H., et al. 2022, arXiv e-prints, arXiv:2208.05473

(ref: gaia2021) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1

(ref: clara2022b) Giménez-Arteaga, C., Oesch, P. A., Brammer, G. B., et al. 2023, ApJ, 948, 126

(ref: ginolfi2020) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90

(ref: guseva2020) Guseva, N. G., Izotov, Y. I., Schaerer, D., et al. 2020, MNRAS, 497, 4293

(ref: harikane2020) Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93

(ref: harikane2022b) Harikane, Y., Inoue, A. K., Mawatari, K., et al. 2022, ApJ, 929, 1

(ref: heintz2021) Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021, ApJ, 922, 147

(ref: heintz2022) Heintz, K. E., Oesch, P. A., Aravena, M., et al. 2022, ApJ, 934, L27

(ref: heintz2022c) Heintz, K. E., Giménez-Arteaga, C., Fujimoto, S., et al. 2023, ApJ, 944, L30

(ref: herrera-camus2016) Herrera-Camus, R., Bolatto, A., Smith, J. D., et al. 2016, ApJ, 826, 175

(ref: herrera-camus2021) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31

(ref: howell2010) Howell, J. H., Armus, L., Mazzarella, J. M., et al. 2010, ApJ, 715, 572

(ref: inami2022) Inami, H., Algera, H. S. B., Schouws, S., et al. 2022, MNRAS, 515, 3126

(ref: inoue2020) Inoue, A. K., Hashimoto, T., Chihara, H., & Koike, C. 2020, MNRAS, 495, 1577

(ref: inoue2016) Inoue, A. K., Tamura, Y., Matsuo, H., et al. 2016, Science, 352, 1559

(ref: isobe2023) Isobe, Y., Ouchi, M., Nakajima, K., et al. 2023a, ApJ, 956, 139

(ref: isobe2023b) Isobe, Y., Ouchi, M., Tominaga, N., et al. 2023b, ApJ, 959, 100

(ref: jullo2007) Jullo, E., Kneib, J. P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447

(ref: kaasinen2017) Kaasinen, M., Bian, F., Groves, B., Kewley, L. J., & Gupta, A. 2017, MNRAS, 465, 3220

(ref: kaasinen2022) Kaasinen, M., van Marrewijk, J., Popping, G., et al. 2022, arXiv e-prints, arXiv:2210.03754

(ref: kashino2017) Kashino, D., Silverman, J. D., Sanders, D., et al. 2017, ApJ, 835, 88

(ref: katz2017) Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS, 468, 4831

(ref: katz2022) Katz, H., Rosdahl, J., Kimm, T., et al. 2022, MNRAS, 510, 5603

(ref: kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

(ref: kepley2020) Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, PASP, 132, 024505

(ref: kewley2002) Kewley, L. J., & Dopita, M. A. 2002, ApJS, 142, 35

(ref: kewley2019) Kewley, L. J., Nicholls, D. C., Sutherland, R., et al. 2019, ApJ, 880, 16

(ref: killi2022) Killi, M., Watson, D., Fujimoto, S., et al. 2022, arXiv e-prints, arXiv:2211.01424

(ref: knudsen2016) Knudsen, K. K., Richard, J., Kneib, J.-P., et al. 2016, MNRAS, 462, L6

(ref: kohandel2022) Kohandel, M., Ferrara, A., Pallottini, A., et al. 2022, arXiv e-prints, arXiv:2212.02519

(ref: kohandel2020) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2020, MNRAS, arXiv:2009.05049

(ref: kohandel2019) —. 2019, MNRAS, 487, 3007

(ref: kojima2017) Kojima, T., Ouchi, M., Nakajima, K., et al. 2017, PASJ, 69, 44

(ref: kokorev2022) Kokorev, V., Brammer, G., Fujimoto, S., et al. 2022, ApJS, 263, 38

(ref: labbe2022) Labbe, I., van Dokkum, P., Nelson, E., et al. 2022, arXiv e-prints, arXiv:2207.12446

(ref: lagache2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: lagos2020) Lagos, C. d. P., da Cunha, E., Robotham, A. S. G., et al. 2020, MNRAS, 499, 1948

(ref: lambert2022) Lambert, T. S., Posses, A., Aravena, M., et al. 2022, MNRAS, arXiv:2210.10023

(ref: lefevre2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: lelli2021) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713

(ref: mahler2022) Mahler, G., Jauzac, M., Richard, J., et al. 2022, arXiv e-prints, arXiv:2207.07101

(ref: maiolino2019) Maiolino, R., & Mannucci, F. 2019, A&ARv, 27, 3

(ref: maiolino2015) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: marti2012) Martı́-Vidal, I., Pérez-Torres, M. A., & Lobanov, A. P. 2012, A&A, 541, A135

(ref: martinez-gonzalez2019) Martı́nez-González, S., Wünsch, R., Silich, S., et al. 2019, ApJ, 887, 198

(ref: mason2018) Mason, C. A., Treu, T., Dijkstra, M., et al. 2018, ApJ, 856, 2

(ref: mclure2018) McLure, R. J., Dunlop, J. S., Cullen, F., et al. 2018, MNRAS, 476, 3991

(ref: meurer1999) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: molyneux2022) Molyneux, S. J., Smit, R., Schaerer, D., et al. 2022, MNRAS, 512, 535

(ref: naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJ, 940, L14

(ref: nakajima2023) Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269, 33

(ref: nanayakkara2022) Nanayakkara, T., Glazebrook, K., Jacobs, C., et al. 2022, arXiv e-prints, arXiv:2207.13860

(ref: nardiello2022) Nardiello, D., Bedin, L. R., Burgasser, A., et al. 2022, MNRAS, 517, 484

(ref: nath2022) Nath, B. B., Vasiliev, E. O., Drozdov, S. A., & Shchekinov, Y. A. 2022, arXiv e-prints, arXiv:2211.12378

(ref: noll2009) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793

(ref: oesch2016) Oesch, P. A., Brammer, G., van Dokkum, P. G., et al. 2016, ApJ, 819, 129

(ref: oguri2010) Oguri, M. 2010, PASJ, 62, 1017

(ref: oguri2021b) —. 2021, PASP, 133, 074504

(ref: ono2022) Ono, Y., Harikane, Y., Ouchi, M., et al. 2022, arXiv e-prints, arXiv:2208.13582

(ref: ota2014) Ota, K., Walter, F., Ohta, K., et al. 2014, ApJ, 792, 34

(ref: pallottini2015) Pallottini, A., Gallerani, S., Ferrara, A., et al. 2015, MNRAS, 453, 1898

(ref: pallottini2019) Pallottini, A., Ferrara, A., Decataldo, D., et al. 2019, MNRAS, 487, 1689

(ref: pallottini2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621

(ref: papovich2023) Papovich, C., Cole, J. W., Yang, G., et al. 2023, ApJ, 949, L18

(ref: pascale2022) Pascale, M., Frye, B. L., Diego, J., et al. 2022, ApJ, 938, L6

(ref: pei1992) Pei, Y. C. 1992, ApJ, 395, 130

(ref: peng2010) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139, 2097

(ref: pilyugin2005) Pilyugin, L. S., & Thuan, T. X. 2005, ApJ, 631, 231

(ref: pilyugin2012) Pilyugin, L. S., Vı́lchez, J. M., Mattsson, L., & Thuan, T. X. 2012, MNRAS, 421, 1624

(ref: pizzati2020) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, arXiv e-prints, arXiv:2001.10547

(ref: planck2011) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2011, A&A, 536, A21

(ref: pontoppidan2022) Pontoppidan, K., Blome, C., Braun, H., et al. 2022, arXiv e-prints, arXiv:2207.13067

(ref: popping2022) Popping, G. 2022, arXiv e-prints, arXiv:2208.13072

(ref: reddy2018) Reddy, N. A., Oesch, P. A., Bouwens, R. J., et al. 2018, ApJ, 853, 56

(ref: rizzo2020) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: robertson2022) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2022, arXiv e-prints, arXiv:2212.04480

(ref: romano2020) Romano, M., Cassata, P., Morselli, L., et al. 2020, MNRAS, 496, 875

(ref: rossa2000) Rossa, J., & Dettmar, R. J. 2000, A&A, 359, 433

(ref: rossa2003b) —. 2003, A&A, 406, 505

(ref: sanders2016) Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ, 816, 23

(ref: sanders2020) Sanders, R. L., Shapley, A. E., Reddy, N. A., et al. 2020, MNRAS, 491, 1427

(ref: schaerer2022) Schaerer, D., Marques-Chaves, R., Oesch, P., et al. 2022, arXiv e-prints, arXiv:2207.10034

(ref: schaerer2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: shaw1998) Shaw, R. A., de La Pena, M. D., Katsanis, R. M., & Williams, R. E. 1998, in Astronomical Society of the Pacific Conference Series, Vol. 145, Astronomical Data Analysis Software and Systems VII, ed. R. Albrecht, R. N. Hook, & H. A. Bushouse, 192

(ref: smit2018) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178

(ref: sommovigo2022b) Sommovigo, L., Ferrara, A., Carniani, S., et al. 2022a, MNRAS, 517, 5930

(ref: sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022b, MNRAS, 513, 3122

(ref: spilker2018) Spilker, J. S., Aravena, M., Béthermin, M., et al. 2018, Science, 361, 1016

(ref: stark2017) Stark, D. P., Ellis, R. S., Charlot, S., et al. 2017, MNRAS, 464, 469

(ref: steidel2014) Steidel, C. C., Rudie, G. C., Strom, A. L., et al. 2014, ApJ, 795, 165

(ref: stott2016) Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888

(ref: sugahara2022) Sugahara, Y., Inoue, A. K., Fudamoto, Y., et al. 2022, ApJ, 935, 119

(ref: sun2022) Sun, F., Egami, E., Fujimoto, S., et al. 2022, arXiv e-prints, arXiv:2204.07187

(ref: swinbank2014) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267

(ref: tacchella2022) Tacchella, S., Johnson, B. D., Robertson, B. E., et al. 2022, arXiv e-prints, arXiv:2208.03281

(ref: tadaki2018) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613

(ref: casa2022) THE CASA TEAM, Bean, B., Bhatnagar, S., et al. 2022, arXiv e-prints, arXiv:2210.02276

(ref: topping2022b) Topping, M. W., Stark, D. P., Endsley, R., et al. 2022a, arXiv e-prints, arXiv:2208.01610

(ref: topping2022) —. 2022b, MNRAS, 516, 975

(ref: trump2022) Trump, J. R., Arrabal Haro, P., Simons, R. C., et al. 2022, arXiv e-prints, arXiv:2207.12388

(ref: tsukui2021) Tsukui, T., & Iguchi, S. 2021, Science, 372, 1201

(ref: valentino2022) Valentino, F., Brammer, G., Fujimoto, S., et al. 2022, ApJ, 929, L9

(ref: vallini2020) Vallini, L., Ferrara, A., Pallottini, A., Carniani, S., & Gallerani, S. 2020, MNRAS, 495, L22

(ref: vallini2021) —. 2021, MNRAS, 505, 5543

(ref: vallini2015) Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36

(ref: watson2015) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327

(ref: witstok2022) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: zhang2016) Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al. 2016, Royal Society Open Science, 3, 160025

(ref: ziparo2022) Ziparo, F., Ferrara, A., Sommovigo, L., & Kohandel, M. 2022, arXiv e-prints, arXiv:2209.06840

(ref: zitrin2009) Zitrin, A., Broadhurst, T., Umetsu, K., et al. 2009, MNRAS, 396, 1985

(ref: zitrin2015) Zitrin, A., Fabris, A., Merten, J., et al. 2015, ApJ, 801, 44

(ref: zurita2000) Zurita, A., Rozas, M., & Beckman, J. E. 2000, A&A, 363, 9

[^1]: <https://s3.amazonaws.com/grizli-v2/JwstMosaics/v4/index.html>

[^2]: [https://jwst-docs.stsci.edu/data-artifacts-and-features/
    snowballs-artifact](https://jwst-docs.stsci.edu/data-artifacts-and-features/
    snowballs-artifact)

[^3]: [https://jwst-docs.stsci.edu/jwst-near-infrared-camera/
    nircam-features-and-caveats/nircam-claws-and-wisps](https://jwst-docs.stsci.edu/jwst-near-infrared-camera/
    nircam-features-and-caveats/nircam-claws-and-wisps)

[^4]: [
    https://github.com/gbrammer/grizli/pull/107](
    https://github.com/gbrammer/grizli/pull/107)

[^5]: The slit-loss is corrected by convolving and integrating the 1D spectrum with the filter response of F444W to match it with the total magnitude of the NIRCam photometry, which is derived with a $0.3\ensuremath{''}$-diameter circular aperture and the corresponding aperture correction.

[^6]: <https://archive.stsci.edu/prepds/relics/>

[^7]: <https://interferopy.readthedocs.io/en/latest/index.html>

[^8]: The effective radius is almost FWHM / 2.0 in Gaussian.

[^9]: [
    https://github.com/gbrammer/grizli-psf-library
    ](
    https://github.com/gbrammer/grizli-psf-library
    )

[^10]: [
    https://webbpsf.readthedocs.io/en/latest/jwst_measured_opds.html
    ](
    https://webbpsf.readthedocs.io/en/latest/jwst_measured_opds.html
    )

[^11]: The positional accuracy of ALMA (pos$_{\rm acc}$) can be approximated by the relationship of $\theta_{\rm beam}$ / SNR / 0.9, where SNR is the signal-to-noise ratio of the image target peak (<https://help.almascience.org/kb/articles/what-is-the-absolute-astrometric-accuracy-of-alma>).

[^12]: We correct the 8% contribution from the extended region in the full SED analysis (Section [3.6](#sec:full_sed)). By assuming that \[O iii\]5007 emission also has the same flux contribution from the extended region, we apply the same correction to the \[O iii\]88$\mu$m/\[O iii\]5007 line ratio analysis (Section [4.1](#sec:line_ratio)).

[^13]: This is because the young bursty stellar populations, causing the strong optical emission lines, dominate the emission in the spatially-integrated photometry, hiding the possible presence of underlying older stellar populations, and yield extremely young ages ($<10$ Myr) and therefore lower masses in the SED fit.

[^14]: [
    http://research.iac.es/proyecto/PyNeb//](
    http://research.iac.es/proyecto/PyNeb//)

[^15]: The dust extinction and re-emission are modeled with (cite: charlot2000) and the templates of (cite: dale2014), respectively, while the final IRX–$\beta_{\rm UV}$ relation is also regulated by dust surface density, $Z_{\rm gas}$, $M_{\rm gas}$, and galaxy structure.

[^16]: In the energy balance between the dust attenuation and re-emission, a lower $T_{\rm d}$ makes the FIR SED peak wavelength longer at a given $L_{\rm IR}$, where the ALMA sensitivity limit may reach the FIR SED peak at some point.

[^17]: This is equal to the high filling factor of the ionized gas relative to dense PDRs.

[^18]: <https://www.stsci.edu/jwst/science-execution/approved-programs/webb-first-image-observations>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Results unchanged within 10% for 20, 30, 40 km/s channel choices",
  "failed_quote": "We confirm the results unchanged much ($<$10 %) in the following analyses via the choice of the spectral resolutions"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "2D Gaussian / Sersic least-squares fits; priors not stated",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[5].fitting.evidence[0]",
  "value": "No fit; MBB scaled to upper limit",
  "failed_quote": "(no quote given)"
 }
]
```
