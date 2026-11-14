# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.511.1303V\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## Abstract

We present $10$ main-sequence *ALPINE* galaxies ($\log(M/{M}_{\odot})=  9.2-11.1$ and ${\rm SFR}=23-190\,{\rm M_{\odot}\,yr^{-1}}$) at $z\sim4.5$ with optical \[O ii\] measurements from *Keck*/MOSFIRE spectroscopy and *Subaru*/MOIRCS narrow-band imaging. This is the largest such multi-wavelength sample at these redshifts, combining various measurements in the ultra-violet, optical, and far-infrared including \[C ii\]$_{158{\rm \mu m}}$ line emission and dust continuum from ALMA and H$\alpha$ emission from *Spitzer* photometry. For the first time, this unique sample allows us to analyse the relation between \[O ii\] and total star-formation rate (SFR) and the interstellar medium (ISM) properties via \[O ii\]/\[C ii\] and \[O ii\]/H$\alpha$ luminosity ratios at $z\sim4.5$. The \[O ii\]$-$SFR relation at $z\sim4.5$ cannot be described using standard local descriptions, but is consistent with a metal-dependent relation assuming metallicities around $50\%$ solar. To explain the measured dust-corrected luminosity ratios of $\log(L_{\rm [OII]}/L_{\rm [CII]}) \sim 0.98^{+0.21}_{-0.22}$ and $\log(L_{\rm [OII]}/L_{\rm H\alpha}) \sim -0.22^{+0.13}_{-0.15}$ for our sample, ionisation parameters $\log(U)< -2$ and electron densities $\log(\rm n_e / {\rm [cm^{-3}]}) \sim 2.5-3$ are required. The former is consistent with galaxies at $z\sim2-3$, however lower than at $z>6$. The latter may be slightly higher than expected given the galaxies’ specific SFR. The analysis of this pilot sample suggests that typical $\log(M/{\rm M_{\odot}}) > 9$ galaxies at $z\sim4.5$ to have broadly similar ISM properties as their descendants at $z\sim2$ and suggest a strong evolution of ISM properties since the Epoch of Reionisation at $z>6$.

galaxies: high-redshift – galaxies: evolution – galaxies: ISM

# Introduction

Observing and understanding the interstellar medium (ISM) of galaxies is a key to understanding galaxy formation and evolution across cosmic time. Next to the far-infrared providing insights into the abundance of dust and gas, the rest-frame optical emission lines build an important basis to study the ISM. Specifically, these lines are sensitive to the instantaneous star formation, metal content of the gas, hydrogen densities, and ionisation rates among a variety of other key parameters.

During the recent years, substantial progress have been made in understanding the ISM properties of galaxies at $z=2-3$ through large spectroscopic survey such as the *Keck Baryonic Structure Survey* (cite: STEIDEL14) or the *MOSFIRE Deep Evolution Field* (MOSDEF) survey (cite: KRIEK15). Among others, one goal of such surveys is to pinpoint the properties of the ISM via three key parameters: the gas-phase metallicity, the electron density $n$ (in ${\rm cm^{-3}}$), and the dimensionless ionisation parameter $U$[^2]. Through simultaneous analysis of multiple optical emission lines, it has been found that these parameters significantly evolve between $z=2$ and local galaxies, yet there is still some debate on the reasons for this change (cite: STEIDEL14; STROM17; SANDERS16; MASTERS16). The evolution of ISM properties questions the reliability (or validity) of commonly used relations that have been calibrated to local galaxies. One of those is the relation between \[O ii\] emission and star formation rate (SFR) as calibrated to local starburst galaxies (cite: KENNICUTT98). Similar to H$\alpha$, \[O ii\] is related to the current star formation in galaxies. However, as a forbidden line, the excitation of oxygen is sensitive to the abundances and ionisation state of the gas and not directly coupled to the ionisation radiation of young stars. The relation is therefore expected to change significantly as a function of these properties and hence likely redshift (cite: KEWLEY04).

This motivates the interesting question of how the ISM changes at early cosmic times and whether common local relations are still valid at high redshifts. The latter is important to quantify, as more measurements of optical lines will be provided soon by the *James Webb Space Telescope* (JWST). Of specific interest is the redshift range $z=4-6$. This epoch is fundamental to study the chemical and structural evolution of galaxies as it connects primordial galaxy formation during the Epoch of Reionisation at $z>6$ with mature galaxy evolution at the peak of cosmic SFR density at $z=2-3$. A large number of galaxies in this redshift range have been robustly identified via Ly$\alpha$ emission and ultra-violet (UV) absorption lines thanks to large spectroscopic surveys (cite: LEFEVRE15; HASINGER18) and are extensively studied in the UV. Unfortunately, current facilities only allow the observation of one strong optical line (the \[O ii\] doublet at rest-frame $3726\text{\normalfont\AA}$ and $3729\text{\normalfont\AA}$) at these redshifts, thus studies with multiple optical lines as the ones mentioned above are not possible. So far, \[O ii\] has only been observed in $4$ galaxies at $z=4-5$, with three of them lensed (cite: SWINBANK07; SWINBANK09; TRONCOSO14; SHAPLEY17). In (cite: SHAPLEY17), the \[O ii\] as well as the detection of \[Ne iii\]$_{\rm 3869}$ has been used to obtain the first direct measurement of the gas-phase metallicity at $z\sim4.5$ via optical lines. However, further determinations of the ISM properties of these galaxies have not been possible due to the lack of other emission lines.

In this paper, we investigate for the first time the ISM properties of high-$z$ galaxy population via the currently largest sample of $10$ typical main-sequence galaxies at $z\sim4.5$ with optical \[O ii\] emission measurements. We mitigate the lack of optical emission lines by entering the far-infrared and in addition use spectral information from the rest-frame UV. Specifically, we are combining measurements of

- rest-UV absorption lines (obtained from *Keck*/DEIMOS spectroscopy).

- optical emission of \[O ii\] (obtained from *Subaru*/MOIRCS narrow-band imaging and *Keck*/MOSFIRE spectroscopy) and H$\alpha$ (obtained from *Spitzer*/IRAC colours), and

- singly ionised Carbon (\[C ii\]$_{158{\rm \mu m}}$ at $158\,{\rm \mu m}$, hereafter denoted as \[C ii\]) and $150\,{\rm \mu m}$ dust continuum from ALMA.

The galaxies, located in the *COSMOS* field (cite: SCOVILLE07), are all part of the *ALPINE* survey (cite: ALPINE_BETHERMIN19; ALPINE_FAISST20; ALPINE_LEFEVRE20), which currently provides the largest multi-wavelength post-reionisation dataset with observations from UV to far-infrared. Thanks to the indirect measurement of metallicity from UV absorption lines as well as additional emission lines such as H$\alpha$ and \[C ii\], we can derive strong constraints on key ISM parameters such as metallicity, electron density, and ionisation parameter. Furthermore, the knowledge of the total SFR of the galaxies enables a first calibration of the relation between \[O ii\] and SFR at $z\sim4.5$.

This paper is organised as follows: In Section [2](#sec:sampledata) we present the spectroscopic and narrow-band observations of \[O ii\], constraints on the metal content from rest-UV absorption lines, and the measurement of H$\alpha$ emission from *Spitzer*. In the following section, we discuss the relation between total SFR and \[O ii\] emission (Section [3.1](#sec:discussionSFR)) and the \[O ii\]/\[C ii\] and \[O ii\]/H$\alpha$ luminosity ratio in the context of the ISM properties of our galaxies (Section [3.2](#sec:discussioncloudy)). We conclude in Section [4](#sec:end).

Throughout this work, we assume a $\Lambda$CDM cosmology with $H_0 = 70\,{\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_\Lambda = 0.70$, and $\Omega_{\rm m} = 0.30$. All magnitudes are given in the AB system (cite: OKE74) and stellar masses and SFRs are normalised to a (cite: CHABRIER03) initial mass function (IMF) unless noted otherwise.

# Sample and Data

The $10$ galaxies at $z\sim4.5$ reside in the *Cosmic Evolution Survey* (cite: SCOVILLE07) field and are a subset of the *ALPINE* survey (cite: ALPINE_BETHERMIN19; ALPINE_FAISST20; ALPINE_LEFEVRE20), which covers in total $118$ galaxies in COSMOS and the *Extended Chandra Deep Field South* (cite: GROGIN11; GIACCONI02). The galaxies are covered by a wealth of observations at rest-frame UV (obtained by ground-based telescopes and the Hubble space telescope), optical (obtained by the *Spitzer* space telescope), and far-infrared (obtained by ALMA) wavelengths. The measurement of the $\sim150\,{\rm \mu m}$ dust continuum and \[C ii\] line are detailed in (cite: ALPINE_BETHERMIN19). Physical properties including stellar mass, SFR, dust attenuation (E(B-V)), and UV continuum slope ($\beta$) are derived from the rest-frame UV to optical photometry by using the spectral energy distribution (SED) fitting code `LePhare` (cite: ARNOUTS99; ILBERT06). (cite: BRUZUALCHARLOT03) composite stellar population models of different ages, metallicities, star-formation histories, and dust attenuation are assumed for the fitting as described in detail in (cite: ALPINE_FAISST20). The galaxies are typical galaxies for their cosmic times and lie on the expected $z\sim4.5$ main-sequence (Figure [1](#fig:mainsequence)). The total SFR in this case is computed from the UV and far-infrared continuum or alternatively from the \[C ii\]$-$SFR relation (cite: ALPINE_SCHAERER20), which was derived from the IRX$-\beta$ relation for galaxies without far-infrared continuum detection (cite: ALPINE_FUDAMOTO20). The measurements coincide closely with two parameterisations of the main-sequence at $z\sim4.5$ from (cite: SPEAGLE14) and (cite: SCHREIBER15). The latter is extrapolated from *Herschel* observations at $z\sim3.5$.

## A Unique Sample of $z\sim4.5$ Galaxies with \[O ii\] Measurements

In this study, we present the largest galaxy sample with \[O ii\] measurement at $z\sim4.5$. For one of the $10$ galaxies, we obtain the \[O ii\] measurement from spectroscopy while for the others \[O ii\] is obtained from narrow-band photometry. In the following, we detail the measurements in both cases.

![](figures/mass_sfr.pdf)

![](figures/slit_layout_CII.pdf)

### *DC_881725*: Spectroscopic \[O ii\] Measurement at $z=4.58$

*DC_881725*  was observed at rest-frame optical wavelengths with the Multi-Object Spectrometer for Infrared Exploration (cite: MCLEAN10; MCLEAN12) on the *Keck* I telescope. This galaxy was originally a filler target part of a *MOSFIRE* program to observe a $z\sim2.2$ overdensity (PI: Nick Scoville). Hence the galaxy was basically randomly picked from the *ALPINE* sample with the only requirement of having an \[O ii\] flux (cite: KENNICUTT98) that is bright enough to be detected by the parent observations. The observations cover the optical \[O ii\] doublet at rest-frame wavelengths of $3726\,{\rm \text{\normalfont\AA}}$ and $3729\,{\rm \text{\normalfont\AA}}$. This is the first main-sequence galaxy at $z\sim4.5$ with spectroscopic \[O ii\] measurement as well as observations of the far-infrared \[C ii\] line emission and continuum at rest-frame $150\,{\rm \mu m}$.

The observations with *MOSFIRE* were carried out on 2019 January 14 in $K$-band ($1.93 - 2.40\,{\rm \mu m}$) under clear sky conditions with an average seeing of 0.4$\ensuremath{''}$ and airmass of $1.1-1.2$. The galaxy was observed in MCSD mode with 16 reads, ABBA dither pattern, and a slit width of $0.7\ensuremath{''}$ for a total on-target exposure time of $1.2\,{\rm h}$ ($24\times 3\,{\rm min}$). The resolution of the spectrum corresponds to $R\sim 3600$, which would allow us theoretically to barely resolve the \[O ii\] doublet if it were at higher signal-to-noise. Figure [2](#fig:slit) shows *DC_881725* in the Hubble ACS/F814W COSMOS mosaics (cite: KOEKEMOER07) (convolved to match the resolution of the ground-based seeing at the time of the *Keck* observations) with the *MOSFIRE* slit overlaid. The far-infrared and \[C ii\] emission observed with ALMA are superimposed as contours. The lower panel shows the two-dimensional spectrum and the window used to extract the one-dimensional spectrum.

The data was reduced and wavelength calibrated using the current MOSFIRE data reduction pipeline[^3]. Sky lines were used by the pipeline to perform a wavelength calibration. The absolute flux calibration of the spectrum is detailed in Appendix [5](#sec:absolutecalibration). In brief, a magnitude $17$ standard star from the 2MASS star catalogue was included in the mask to derive a wavelength-dependent absolute flux calibration of the extracted one-dimensional spectrum.

The one-dimensional spectrum of *DC_881725* is extracted in a spatial window of $6$ pixels (corresponding to $1.08\ensuremath{''}$ at a pixel scale of $0.18\ensuremath{''}/{\rm px}$) around the centre of the identified \[O ii\] emission line. The extracted spectrum in $\rm e^{-}\,s^{-1}$ is converted to $\rm erg\,s^{-1}\,cm^{-2}\,\text{\normalfont\AA}^{-1}$ using the wavelength dependent normalisation described in Appendix [5](#sec:absolutecalibration). The extracted spectrum is shown in Figure [3](#fig:OIIgaussian) (blue dashed line) around the expected location of the \[O ii\] doublet.

The \[O ii\] line flux is derived by fitting a single Gaussian with variable mean, $\sigma$, and total flux to the one-dimensional spectrum (Figure [3](#fig:OIIgaussian), black solid line). We also tried to fit a double Gaussian to account for the doublet nature of the line. However, given the low signal-to-noise and resolution, no robust fit was obtained. The uncertainties of the total flux are determined using $500$ Monte Carlo samples for each of which the fluxes are changed according to their uncertainties (assumed Gaussian) obtained from the variance of the spectrum. We find a total \[O ii\] line flux of $3.00^{+0.47}_{-0.46}\times 10^{-17}\,{\rm erg\,s^{-1}\,cm^{-1}\,\text{\normalfont\AA}^{-1} }$ and measure an \[O ii\] redshift of z$_{[O ii]}~=~4.5793$. The latter matches closely the redshift determined from \[C ii\] ($\sim123\pm30\,{\rm km\,s^{-1}}$ blue-shifted w.r.t. \[O ii\]) but is significantly red-shifted with respect to Ly$\alpha$ by $328\pm30\,{\rm km\,s^{-1}}$.[^4] These quantities as well as the \[O ii\] luminosity, L$_{[O ii]}$, are listed in Table [\[tab:keckproperties\]](#tab:keckproperties) along with other properties measured from the ancillary data.

![](figures/OII_w_gaussian.pdf)

### \[O ii\] Measurements from Narrow-Band Imaging

We complement *DC_881725* with $9$ additional galaxies at $z\sim4.5$ which have \[O ii\] luminosities derived from narrow-band imaging taken with the Multi-Object Infrared Camera and Spectrograph (cite: Ichikawa2006; Suzuki2008) on the *Subaru* Telescope. The observations were part of the *Charting Cluster Construction with VUDS* (cite: LEFEVRE15) *and ORELSE* (cite: Lubin2009) survey (cite: Lemaux20; Shen21). In brief, the $9$ *ALPINE* galaxies fall in the footprint of three pointings targeting the massive proto-cluster *PCl J1001+0220* at $z\sim4.57$ (cite: Lemaux2018) and its surrounding in the COSMOS field. Similar to *DC_881725*, they are therefore randomly selected from the *ALPINE* sample but without imposed restrictions on the \[O ii\] flux. The $9$ galaxies may be part of the proto-cluster structure, however, as shown by studies at lower redshifts (cite: DARVISH15), we do not expect significant differences in their properties compared to field galaxies.

The observations were executed between February 2 2020 and January 31 2021, using NB2071 ($2.043-2.097\,{\rm \mu m}$) and NB2083 ($2.056-2.110\,{\rm \mu m}$) narrow-band filters, under seeing that ranged from $\sim0.4-0.8\ensuremath{''}$ and conditions that varied from light cirrus to photometric. The total effective integration time across all three pointings and two filters was approximately $18$ hours, which was split into $150{\rm s}$ individual exposures. A standard circular dither pattern with a set of 10 dithers was adopted.

All raw data were reduced with the IRAF based reduction pipeline MCSRED2 (cite: Tanaka2011), which performed flat-fielding, masking objects, and sky subtraction. Astrometry calibration was performed by SCAMP (cite: Bertin2006) for every individual exposure. For each filter and chip, a final narrow-band image was stacked using SWARP (cite: Bertin2002). The $5\sigma$ limiting magnitudes of the images have a median of $23.1\,{\rm mag}$ and in a range of $22.7-23.3\,{\rm mag}$, where $\sigma$ is measured from the flux scatter of randomly distributed $2\ensuremath{''}$ aperture. Note that some exposures were shallower due to the filter wheel occultation. Finally, photometric calibration was performed to the *Ks*$-$band image from the UltraVISTA DR4 (cite: McCracken2012) by selecting a set of bright but unsaturated point sources as the reference stars.

For the source detection and extraction on each narrow-band image, SEXTRACTOR (cite: Bertin1996) was used in dual-image mode using the much deeper ($24.8\,{\rm mag}$ at $5\sigma$) *Ks*$-$band image as the detection image.[^5] The point-spread functions (PSFs) of the narrow-band images were degraded to match the *Ks*-band image. In details, the PSFs for the narrow-band and *Ks*-image were derived using the PSFEX code (cite: Bertin2011). Subsequently, the PHOTUTIL package with a Split Cosine Bell window was used to generate a matching kernel between two PSFs. The uncertainties on the fluxes estimated by SEXTRACTOR were scaled to account for correlated pixel noise following the method of (cite: pelliccia2021).

The following system of two equations involving the narrow-band and the underlying *Ks*-band photometry was solved for the continuum ($f^{\lambda}_{\rm cont}$) and \[O ii\] line flux ($f^{\lambda}_{\rm line}$) at wavelength $\lambda$ of the \[O ii\] line (cite: Hu2019): $$\begin{equation}
 \label{eq_oii}
\bar{f}^{\rm \lambda}_{\rm NB/Ks} = \frac{\int\left(f^{\lambda}_{\rm line} + f^{\lambda}_{\rm cont}\right) T^{\lambda}_{\rm NB/Ks} d\lambda}{\int T^{\lambda}_{\rm NB/Ks} d\lambda}.
\end{equation}$$

In the above equation, $\bar{f}^{\lambda}_{\rm NB}$ and $\bar{f}^{\lambda}_{\rm Ks}$ denote the detected flux densities in each narrow-band and the *Ks*-band, and $T^{\lambda}_{\rm NB}$ and $T^{\lambda}_{\rm Ks}$ are the corresponding filter transmission functions. In the calculation, we assumed an \[O ii\] line profile resembling a $\delta$-function in each narrow-band filter and a flat continuum profile. As the observed line width of the \[O ii\] doublet ($29.01_{-4.64}^{+5.33}$Å, see Figure [3](#fig:OIIgaussian)) is much narrower than the width of the narrow-band filter ($\sim 270\,{\rm \text{\normalfont\AA}}$), so the \[O ii\] line profile does not affect the result of this calculation. The uncertainties of the \[O ii\] fluxes were obtained using Monte-Carlo iterations for each of which the narrow-band and *Ks*-band fluxes were drawn from a Gaussian distribution with a width corresponding to their associated uncertainties. The \[O ii\] flux uncertainty is then defined as the 16$^{\rm th}$ and 84$^{\rm th}$ quantiles of the resulting \[O ii\] flux distribution. Finally, an inverse-variance weighting scheme was adopted to combine fluxes obtained from the two narrow-band filters, with weights defined as $W_i = T_i^2 / \sigma_i^2$, where $T_i$ is the narrow-band transmission curve at the \[C ii\] redshift and $\sigma_i$ is the narrow-band flux uncertainty.

Table [\[tab:narrowbandproperties\]](#tab:narrowbandproperties) lists the measured \[O ii\] luminosities as well as other properties derived from the ancillary data for these $9$ galaxies.

## Estimate of Metal-Enrichment from Rest-Frame UV Absorption Lines

Commonly, the gas-phase metal content of galaxies is measured by flux ratios of bright optical lines such as \[O ii\], \[O iii\], and H$\alpha$ (cite: PETTINI04; MAIOLINO19). Recently, thanks to ALMA, also far-infrared emission lines such as \[N ii\]$_{205{\rm \mu m}}$, \[O ii\]$_{88{\rm \mu m}}$, and \[C ii\] are used to estimate the gas-phase metal content of high-redshift galaxies (cite: VALLINI21; YANGLIDZ20; JONESTUCKER20; PAVESI19; CROXALL17). The former are not accessible at these redshifts currently (except \[O ii\]), while the latter are not available for our galaxies as their observations are costly (except \[C ii\]) or only possible for galaxies at $z>6$ (in the case of \[O ii\]$_{88{\rm \mu m}}$).

Nonetheless, we can estimate the metal content of our galaxies from the exquisite rest-frame UV spectra in an indirect way. Specifically, the strength, i.e., equivalent-width (EW; note that EWs of absorption lines are defined positive), of rest-frame UV absorption lines correlates with metal content (cite: LEITHERER11). This correlation has different origins including the evolutionary stage of stellar populations, metal-dependent winds impacting the width of absorption lines, or dust extinction. The technique has already been applied to similar main-sequence galaxies at $z\sim4-6$ (cite: FAISST16b; ANDO07) and has been tested empirically at lower redshifts (cite: FAISST16b). The S/N of individual rest-UV spectra of our galaxies is too low to estimate their metal content. We therefore perform median stacking the $10$ spectra before we compute the EWs of several absorption complexes around Si iii ($\sim 1300\,{\rm \text{\normalfont\AA}}$), C ii ($\sim 1335\,{\rm \text{\normalfont\AA}}$), Si iv ($\sim 1400\,{\rm \text{\normalfont\AA}}$), and C iv ($\sim 1550\,{\rm \text{\normalfont\AA}}$). The uncertainties are computed via Monte-Carlo iterations including the spectral variances. We then use the relations between absorption line EW and metallicity as calibrated via galaxies in the local universe as well as $z\sim2$ and $z\sim3$ in (cite: FAISST16b).

![image](figures/full_stack.pdf)\
![image](figures/EW_metallicity.pdf)

The stacked spectrum and the results from this analysis are shown in Figure [4](#fig:metallicity). The blue horizontal swaths show the measured EWs of each absorption complex with uncertainty and the grey swaths show the calibration derived in (cite: FAISST16b). Looking at the individual absorption complexes suggests average metallicites between $10\%$ and $50\%$ of solar, except for Si iii, which is consistent with solar metallicity. We note that even for the stack the S/N is relatively low, which is likely the cause for the apparent differences between the individual absorption complexes. Combining the probability distribution functions of all absorption complexes, we find an average metallicity of $12+\log{(\rm O/H}) = 8.41^{+0.31}_{-0.54}$. This corresponds to roughly $\sim50\%$ of the solar metallicity[^6]. Such values are consistent with the expected metallicity based on the stellar masses of our galaxies at these redshifts (cite: FAISST16b; ANDO07).

## Photometric Measurement of H$\alpha$ from *Spitzer*

The coverage of our galaxies by *Spitzer* allows us to photometrically estimate their H$\alpha$ emissions via the \[$3.6\,{\rm \mu m}$\]$-$\[$4.5\,{\rm \mu m}$\] colours. This method has been successfully used by several studies very early on (cite: SHIM11; STARK13; MARMOLQUERALTO16; RASAPPU16) and it is shown to result in photometric H$\alpha$ measurements that are statistically consistent with spectroscopy (cite: FAISST16a). The detailed derivation of this measurement for the *ALPINE* galaxies is described in (cite: ALPINE_FAISST20). The luminosities are corrected for dust in the same way as \[O ii\]. As an additional check, we compare our H$\alpha$ measurement to the *EL-COSMOS* catalogue (cite: SAITO20), which contains H$\alpha$ emission line predictions from SED fitting for all galaxies from the (cite: LAIGLE16) COSMOS catalogue. We find good agreement within a factor of $2-5$ (see Appendix [6](#sec:elcosmos)). We find a similar agreement when comparing the \[O ii\] luminosities provided in the *EL-COSMOS* catalogue to our spectroscopic and narrow-band imaging measurements, which verifies the reliability of the catalogue.

# Discussion

![image](figures/fig5_hist_colormatch_bnl_ticks.pdf) ![image](figures/sfr_loii_finalnov15.pdf)

## The \[O ii\]$-$SFR relation at $z\sim4.5$

We first investigate whether the local relation between \[O ii\] emission and total star formation is still valid at $z\sim4.5$. For this we make use of our multi-wavelength measurements of the total SFR from UV and far-infrared data.

### Total SFRs Derived from UV$+$Far-Infrared Continuum and \[C ii\] Emission

In order to relate \[O ii\] emission to total star formation, we have to provide measurements of the latter that are as robust as possible. Our sample allows us to do this via the combination of measurement of UV and far-infrared continuum as well as \[C ii\] emission.

For galaxies detected in far-infrared continuum ($5$ out of $10$), we compute the total SFR as the sum of UV and dust obscured star formation. Specifically, we make use of the relations detailed in (cite: KENNICUTT98) (cite: KENNICUTT21), $$\begin{equation}
\label{eq:uv}
    {\rm SFR_{UV}\,(M_{\odot}\,yr^{-1})} = 0.79 \times 10^{-28} L_{\rm \nu} ({\rm erg\,s^{-1}\,Hz^{-1}})
\end{equation}$$ and $$\begin{equation}
\label{eq:fir}
    {\rm SFR_{IR}\,(M_{\odot}\,yr^{-1})} = 2.54 \times 10^{-44} L_{\rm IR} ({\rm erg\,s^{-1}}).
\end{equation}$$ These SFR values have already been converted from a (cite: SALPETER55) to a (cite: CHABRIER03) IMF by division of a factor of $1.77$ (in linear scale). For details on the derivation of the UV and far-infrared luminosity we refer to (cite: ALPINE_FAISST20) and (cite: ALPINE_BETHERMIN19), respectively. Note that the derivation of $L_{\rm IR}$ depends strongly on the shape of the far-infrared SED, with specifically the dust temperature playing an important role (cite: FAISST17b). Here, we make use of the stacked far-infrared SED derived from Herschel, SCUBA, and ALMA photometry of $z=4-6$ galaxies in COSMOS with similar SFR and stellar masses as the *ALPINE* galaxies (cite: ALPINE_BETHERMIN19). The dust temperature of this stack is $43\pm5\,{\rm K}$, which is consistent with the individual dust temperatures measured for $4$ *ALPINE* galaxies with sufficient far-infrared coverage from ALMA (cite: FAISST20b).

For the remaining five galaxies without far-infrared continuum detection, we use the relation between \[C ii\] line emission and total SFR as presented by (cite: ALPINE_SCHAERER20), $$\begin{equation}
\label{eq:cii}
    \log({\rm SFR_{[CII]}/ [M_{\odot}\,yr^{-1}]}) = \frac{\log({\rm L_{[CII]} / L_{\odot}}) - 6.61}{1.17}.
\end{equation}$$ The above relation is based on total SFRs of all *ALPINE* galaxies (with limits from \[C ii\] non-detection properly taken into account). For galaxies without far-infrared detection, the IRX$-\beta$ relation (cite: ALPINE_FUDAMOTO20) is used to derive their far-infrared luminosities and total SFRs.

The total SFR for the $9$ narrow-band detected galaxies are listed in Table [\[tab:narrowbandproperties\]](#tab:narrowbandproperties). The total SFRs of *DC_881725* derived from UV and far-infrared as well as \[C ii\] for comparison are listed in Table [1](#tab:sfrs). Note that the \[C ii\] and far-infrared (if available) derived SFRs are very comparable as the former have been calibrated by the latter in (cite: ALPINE_SCHAERER20).

We can also compare different \[C ii\]$-$SFR relations derived in (cite: DELOOZE14) with our total SFRs derived for the $5$ galaxies with far-infrared continuum detection. These relations have been calibrated using low-metallicity dwarfs ($12+\log({\rm O/H}) \sim 7.1-8.4$), starbursts (and H ii regions), galaxies with an active galactic nucleus (AGN), ultra-luminous infrared galaxies (ULIRGs), and high-redshift galaxies (mostly at $z\sim1-3$). We find that *(i)* the \[C ii\]$-$SFR relation of local metal-poor dwarfs underestimates the total SFR by $0.43\pm0.13\,{\rm dex}$, while *(ii)* the relation derived from ULIRGs overestimates the total SFRs by $0.77\pm0.15\,{\rm dex}$. The other calibrations are roughly consistent with our derived values within $1\sigma$ uncertainties. Similar results are found for the remaining $5$ galaxies with SFRs derived from \[C ii\] using the (cite: ALPINE_SCHAERER20) relation. This SFR comparison suggests that our galaxies are not comparable to either local low-metallicity dwarfs or local ULIRGs. This is not surprising as rest-frame UV absorption line spectroscopy suggests that our galaxies are rather metal enriched (see Section [2.2](#sec:metallicity)). Furthermore, their far-infrared luminosities are about an order of magnitude lower than those of local ULIRGs included in (cite: DELOOZE14) ($L_{\rm IR} \sim 3\times 10^{12}\,{\rm L_{\odot}}$). Table [1](#tab:sfrs) shows a detailed list of SFRs derived by the different \[C ii\]$-$SFR relations for the example of *DC_881725*.

### The \[O ii\]$-$SFR relation at $z\sim4.5$

With measured robust total SFRs for our galaxies, we can now relate these values to the \[O ii\] emission.

The left panels of Figure [5](#fig:sfr_oii) show the histograms of the $L_{{\rm OII}}/L_{{\rm IR}}$ and $L_{{\rm OII}}/L_{{\rm CII}}$ luminosity ratios. We find observed median ratios of $\log(L_{\rm [OII]}/L_{\rm [CII]}) ~=~0.39^{+0.35}_{-0.32}$ and $\log(L_{\rm [OII]}/L_{\rm IR})=-2.45^{+0.23}_{-0.09}$. The corresponding dust-corrected ratios are $\log(L_{\rm [OII]}/L_{\rm [CII]}) ~=~0.98^{+0.21}_{-0.22}$ and $\log(L_{\rm [OII]}/L_{\rm IR})=~-1.64^{+0.23}_{-0.13}$, respectively.

With \[O ii\] being an optical line, it has to be corrected for the effect of dust attenuation. We compute \[O ii\] dust correction factors using the stellar continuum dust attenuation $E_{s}{(B-V)}$ values via $$\begin{equation}
    f_{\rm corr} = 10^{0.4  E_{s}{(B-V)} k_{\lambda}/f},
\end{equation}$$ where $k_{\rm \lambda}$ is the reddening curve with $\lambda=3727\,{\rm \text{\normalfont\AA}}$ and we assume a differential dust attenuation factor between stellar continuum and nebular emission of $f=0.44$ (cite: CALZETTI00)[^7]. The $E_{s}{(B-V)}$ values are estimated by the following procedure. For galaxies that are detected in far-infrared continuum, we used their IRX ratio ($\equiv \log(L_{\rm IR}/L_{\rm UV})$) to estimate the dust attenuation at rest-frame $1600\,{\rm \text{\normalfont\AA}}$ ($A_{\rm 1600}$) via the relation given in (cite: HAO11)[^8], $$\begin{equation}
\label{eq:a1600}
    A_{\rm 1600} = 2.5 \log(1 + 0.46 \times 10^{\rm IRX}).
\end{equation}$$ The nebular $E(B-V)$ values, $E_{n}{(B-V)}$, are then estimated using the relation $A_{\rm 1600} = 4.39 \times  E_{n}{(B-V)}$ (cite: CALZETTI00). Other parameterisations (cite: REDDY15) lead to values that are different by less than $20\%$. For galaxies that are not detected in far-infrared continuum, we derive the stellar $E_{s}{(B-V)}$ values from the UV continuum photometry. Specifically, we explore the values from SED fitting directly as well as derived from the UV continuum slope ($\beta$) using the dust parameterisations by (cite: CALZETTI00) and (cite: REDDY15). As an additional comparison, we also derive IRX values directly from the $\beta$ slopes using the IRX$-\beta$ relation fit for *ALPINE* galaxies at $z\sim4.5$ in (cite: ALPINE_FUDAMOTO20). We find that all four methods agree within $0.05\,{\rm mag}$, which results in $<30\%$ differences in the dust factors for \[O ii\]. All in all, we find \[O ii\] dust attenuation factors (linear) between $1-5$, except in one case where we find a value of $f_{\rm corr}\sim10$. The different $k_{\rm \lambda}$ parameterisations used above result in variations of $<40\%$ (leading to uncertainties of $<0.14\,{\rm dex}$ in \[O ii\] luminosity). The differential dust attenuation between nebular emission and stellar continuum is by far the largest contribution to the total uncertainty. There is observational evidence that the $f-$factor of $z>2$ galaxies is closer to $0.7$ than the locally measured value of $0.44$ (cite: KASHINO17; FAISST19b; RODRIGUEZMUNOZ21). In the case of $f=0.7$, the dust attenuation factors would decrease by a factor of $1.5$ ($0.18\,{\rm dex}$ change in luminosity) on average for our sample.

Finally, the right panel of Figure [5](#fig:sfr_oii) relates the observed (solid symbols) and intrinsic (dust-corrected, empty symbols) \[O ii\] luminosities to the total star formation (as described in Section [3.1.1](#sec:discussionTotalSFR)). The far-infrared detected galaxies (dust correction from the IRX ratio) are shown as triangles, the remaining galaxies are shown as circles. *DC_881725* is denoted with a star and the median of the dust-corrected \[O ii\] luminosity and total SFR is marked as a purple cross. The measurement uncertainties in \[O ii\] luminosities are large compared to the measurement uncertainties in total SFR (on the order of $0.1\,{\rm dex}$). However, we expect systematic errors in the total SFRs to be a factor of $2-3$ larger given the uncertainties in the relation between \[C ii\] and SFR.

Along with our data, we show different parameterisations of the \[O ii\]$-$SFR relation from the literature. We include the original relation by (cite: KENNICUTT98)[^9], $$\begin{equation}
\label{eq:oii_K98}
    {\rm SFR_{[O ii]}^{\rm K98}\,(M_{\odot}\,yr^{-1})} = (0.79 \pm 0.23) \times 10^{-41} L_{\rm [OII]} ({\rm erg\,s^{-1}}),
\end{equation}$$ as well as an updated version provided by equation 4 in (cite: KEWLEY04)[^10] $$\begin{equation}
\label{eq:oii_K04}
    {\rm SFR_{[O ii]}^{\rm K04}\,(M_{\odot}\,yr^{-1})} = (3.72 \pm 0.93) \times 10^{-42} L_{\rm [OII]} ({\rm erg\,s^{-1}}).
\end{equation}$$ As pointed out by these authors, this relation may depend significantly on the gas-phase metallicity of the galaxies. We therefore also show their theoretical relations for solar, half-solar, and one-fifth solar metallicity obtained by equation 10 in (cite: KEWLEY04)[^11] $$\begin{equation}
\label{eq:oii_K04_met}
    {\rm SFR_{[O ii]}^{\rm K04}}(Z)\,{\rm (M_{\odot}\,yr^{-1})} = \frac{4.46 \times 10^{-42} L_{\rm [OII]} ({\rm erg\,s^{-1}})}{(-1.75\pm0.25)[\log({\rm O/H})+12] + (16.73\pm2.23)}.
\end{equation}$$

We find that the original (cite: KENNICUTT98) relation would significantly overestimate \[O ii\]-derived SFRs by factors of $3-5$ if applied to *dust-corrected* \[O ii\] luminosities. Note that the relation in Equation [\[eq:oii_K98\]](#eq:oii_K98) required dust corrections of \[O ii\] at the H$\alpha$ rest-frame wavelength (cite: KENNICUTT98). However, at the dust attenuation values of our galaxies, this would reduce the dust correction factors by less than $40\%$ (and similarly the overestimation), hence cannot account for the discrepancy. A much better estimate of the total SFR is provided by the updated and metal-dependent \[O ii\]$-$SFR relations by (cite: KEWLEY04) (detailed numbers for the case of *DC_881725* are listed in Table [1](#tab:sfrs)). The large uncertainties, mainly due to the unknown differential dust attenuation factors but also the uncertain total SFR, do not allow us to distinguish relations for different metallicities at significance. As shown by the purple cross denoting the median value of the dust corrected \[O ii\] luminosities and total SFRs, sub-solar metallicities are the most likely choice but solar metallicites cannot be excluded given the combination of measurement and systematic uncertainties. Also, note that an increase of the $f-$factor from local $0.44$ to $\sim0.7$ would reduce the dust correction for the \[O ii\] luminosity by $<0.2\,{\rm dex}$ (see above), which would keep our observations consistent with the (cite: KEWLEY04) relation at sub-solar metallicity.

![](figures/cloudy_plotsv2.pdf)

## Constraints on ISM Properties from CLOUDY Analysis

In this section, we compare the $\log(L_{\rm [OII]}/L_{\rm [CII]})$ and $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratios from measurements presented in Sections [2.1](#sec:oii_measurements) and [2.3](#sec:ha_measurements) to theoretical values obtained by CLOUDY (cite: FERLAND17) to study key parameters of the ISM of our galaxies.

For the CLOUDY simulation, we assume gas with plain-parallel geometry including Orion-type grains as well as Polycyclic Aromatic Hydrocarbons (PAHs). We ran models for gas clouds with electron densities of $\log(n_{\rm H}/{\rm cm^{-3}})\,=\,[0.5,2]$, gas-phase metallicities of $Z=[0.1,0.5,1.0]\,{\rm Z_{\odot}}$, and ionisation parameters between $-3.0 < \log(U) < -0.5$ in steps of $0.5\,{\rm dex}$. The stopping criteria of the simulation is crucial, especially for computing the \[C ii\] emission, which can originate from low-density warm ISM. We use a stopping point at $A_{\rm v}=100\,{\rm mag}$ and we found that lower values such as $A_{\rm v}=10\,{\rm mag}$ do not have a significant impact on the our results. We also investigated the dependence of our results on different star formation histories for the underlying stellar population. For this, we assumed three different simple models: *(A)* a starburst with an age of $100\,{\rm Myr}$; *(B)* a constant star formation history; *(C)* the best-fit SED of *DC_881725*. The first two are produced by the BPASS v2.0 models (cite: ELDRIDGE17; STANWAY18), assume $10\%$ solar stellar metallicity, and include binary-star evolution. The latter is derived from broad-band photometry using CIGALE (cite: BURGARELLA05; NOLL09; BOQUIEN19). The results are shown in Figure [6](#fig:CLOUDY). The panel labels indicate the assumption of the underlying stellar population (*A*, *B*, or *C*, respectively). The left and right columns show the result for $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ and $\log(L_{\rm [OII]}/L_{\rm [CII]})$, respectively. In the following, we compare the models to the observations in more detail.

### The $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratio

Let us first have a look at the $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratio. As seen on the left panels in Figure [6](#fig:CLOUDY), this ratio shows a strong negative correlation with the ionisation parameter (radiation pressure) $U$, however is largely independent of the electron density and the changes with metallicity are small compared to the accuracy of our observations. Thus the $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratio allows us to put constraints on the ionisation parameter $U$. The trends are slightly flatter for a constant star formation history or using the best-fit SED. However, overall the impact of the three different star formation histories is negligible at the current accuracy of our measurements.

The observed median dust-corrected $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ ratio ($-0.22_{-0.15}^{+0.13}$) and population scatter is indicated as black line with grey area, respectively. Note that we are only using $7$ out of the $10$ galaxies whose *Spitzer* photometry is not contaminated by nearby sources. *Spitzer*-derived H$\alpha$ luminosities are mainly uncertain because of the unknown dust correction (specifically the unknown $f-$factor). However, the \[O ii\] to H$\alpha$ luminosity ratio is expected to be rather stable as the \[O ii\] and H$\alpha$ lines are affected by dust in a similar way (and have likely similar $f-$factors). For example, a change in $f$ from $0.44$ to $0.7$ affects the luminosity ratio by less than $0.1\,{\rm dex}$, which is smaller than sample scatter and measurement uncertainties. Different reddening curves contribute even less to the uncertainties.

Comparing our observations to the CLOUDY models, we find that low ionisation parameters ($\log(U) < -2$ or $\log(q / {\rm cm\,s^{-1}}) < 8.5$)[^12] are favored independent of the assumed electron density and metallicity. Such ionisation parameter values are very consistent with typical measurements at $z=2-3$ (via the \[O iii\]/\[O ii\] line ratio) finding $\log(U) \sim -2.5$ or $\log(q / {\rm cm\,s^{-1}}) \sim 8$ (cite: NAKAJIMA14; SANDERS16; SANDERS20). On the other hand, studies at $z>6$ suggest $\log(U) \sim -1.7$, which would indicate an increase in ionisation parameter in the Epoch of Reionisation (cite: STARK14; STARK15; HUTCHISON19; HARIKANE20). Note that observations of local H ii regions suggest an upper cut-off due to radiation confinement of $\log(U)~\sim~-1$ (cite: YEH12).

### The $\log(L_{\rm [OII]}/L_{\rm [CII]})$ luminosity ratio

Next, we focus on the $\log(L_{\rm [OII]}/L_{\rm [CII]})$ luminosity ratio. The models from CLOUDY are shown in the right panels of Figure [6](#fig:CLOUDY). Increasing ionisation parameter as well as increasing electron density result in a higher luminosity ratio. On the other hand, more metal enriched environments are expected to have lower $\log(L_{\rm [OII]}/L_{\rm [CII]})$ ratios. The trends are not significantly affected by the different assumptions on the underlying stellar population.

The black and grey horizontal lines show the measured ratios for *DC_881725* and the $9$ narrow-band detected galaxies, respectively. The \[O ii\] luminosities have been corrected for dust attenuation using the methods described in Section [3.1.2](#sec:discussionOIISFR). We find a log-ratio of $1.11_{-0.08}^{+0.08}$ for *DC_881725*  and a median ratio of $0.98^{+0.21}_{-0.22}$ for all $10$ galaxies. Note that the true stellar reddening curve plays a sub-dominant role in this rather quantitative analysis.

The models show that the intrinsic $\log(L_{\rm [OII]}/L_{\rm [CII]})$ luminosity ratio is significantly degenerate with metallicity, ionisation parameter, and electron density. From Section [3.2.1](#sec:oiiha) we expect an ionisation parameter $\log(U) < -2$. Metallicity seems to have the least impact on the luminosity ratio assuming a reasonable range between $10\%$ solar and solar metallicity. An analysis of the rest-frame UV absorption line strengths (see Section [2.2](#sec:metallicity)) suggests that our galaxies have $\sim50\%$ of the solar gas-phase metal enrichment on average. Fixing the metallicity to half-solar is therefore a reasonable assumption. Within these assumptions our measurements would argue for electron densities of $\log(n/{\rm [cm^{-3}]}) \sim 2.5-3$,

Typical electron densities are measured to be around $100-200\,{\rm cm^{-3}}$ in galaxies with similar rates of star formation at $z\sim2$. This is about a factor of $5-10$ higher than observed on average in local galaxies (cite: STEIDEL14; MASTERS14; SANDERS16; DAVIES21). However, as pointed out by (cite: KAASINEN17) (cite: SHIMAKAWA15; DAVIES21), the electron density is positively correlated with (specific) SFR, hence the higher $\log(n)$ found in high-$z$ galaxies are likely due to a higher normalization of the main-sequence (i.e., higher average SFR). In line with this, it was found that $\log(n)$ does not significantly evolve with redshift for SFR-matched samples. Taking the measurements in (cite: DAVIES21) at face value suggests at least $\log(n/{\rm cm^{-3}}) \sim 2.5$ ($300\,{\rm cm^{-3}}$) for the average specific SFR of our sample ($\sim0.9\,{\rm Gyr^{-1}}$) according to $z\sim2$ galaxies. Our measurements ($\log(n/{\rm [cm^{-3}]}) \sim 2.5-3$) are generally consistent with these expectations *given their high SFRs*, although at the high end. Lower electron densities (e.g., $\sim100-200\,{\rm cm^{-3}}$, typical at $z\sim2$) would indicate ionisation parameters of $\log(U) \gtrsim -1.7$, which is clearly inconsistent with our measured $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratio.

Combining the results of this section with Section [3.2.1](#sec:oiiha), we conclude that our $z\sim4.5$ galaxies have ionisation parameters $\log(U) <  -2$ and electron densities $\log(n/{\rm [cm^{-3}]}) \sim 2.5-3.0$. While the former is consistent with measurements in galaxies at $z=2-3$, the latter is consistent with or slightly higher than the expected electron densities given the SFRs of our galaxies and the relation between $\log(n)$ and star formation measured in lower redshift galaxies. Significantly higher ionisation parameters are suggested for galaxies in the Epoch of Reionisation at $z>6$, which would argue for a fast evolution of the ISM properties at times earlier than $z\sim4.5$. Furthermore, we find that these typical main-sequence galaxies are much less extreme than sub-millimetre galaxies at similar redshifts showing electron densities of $\log(n/{\rm [cm^{-3}]}) = 4$ or more (cite: BOTHWELL17; DEBREUCK19).

We note that nine of the galaxies lie in a greater structure associated with a proto-cluster at $z\sim4.57$ (cite: Lemaux2018). It is possible that the proto-cluster environment has altered their properties in some way that could be relevant for this study. For example, (cite: DARVISH15) argues for a lower electron density in galaxies residing in dense environments ($\Sigma/\Sigma_{\rm mean} > 4$) based on a comprehensive study of an over dense region at $z\sim0.5$. The translation of this result to (less) over-dense regions at $z\sim5$ and hence the impact of the environment on the properties of our galaxies remains unclear. As far as we can tell, the nine galaxies have statistically indistinguishable properties with respect to the other *ALPINE* (hence field) galaxies using the metrics that we are able to compare (e.g., Figure [1](#fig:mainsequence)). As such, it is at least likely that any effect of environment on the ISM is subtle at best.

### Caveats

Several other parameters could change the modeled line ratios. Here, we investigate the impact of the stellar metallicity of the stellar population producing the incident spectrum as well as the geometrical covering factor.

First, we ran the simulation with a covering factor of $0.1$ instead of $1$ and found that it does not have a significant impact ($<0.05\,{\rm dex}$) on either line ratio. Second, we implemented a solar stellar metallicity (instead of $10\%$ solar) for the incident spectrum produced by the BPASS models. We find that this increases both $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ and $\log(L_{\rm [OII]}/L_{\rm [CII]})$ ratios by $0.15\,{\rm dex}$. This seems to be because a factor $8$ decrease in \[O ii\], which is over-balanced by a factor $11$ and $12$ decrease in H$\alpha$ and \[C ii\], respectively.

An increase in the $\log(L_{\rm [OII]}/L_{\rm [CII]})$ luminosity ratio would slightly reduce the likelihood of high electron densities for a given ionisation parameter. And increased $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ ratio would further allow slightly higher ionisation parameters (especially if assuming a gas-phase metallicity of $50\%$ solar). All in all, a higher stellar metallicity would argue for $\sim 0.2-0.3\,{\rm dex}$ higher ionisation parameters and roughly the same amount lower electron densities, making our galaxies consistent with their counterparts at $z\sim2-3$ with similar star formation properties.

Finally, our simple model assumes that the galaxy is a single H ii region. More complicated “multi-sector” models could be investigated, however, we do not think that given the uncertainties in our (photometric) measurements of \[O ii\] and H$\alpha$ this would improve the robustness of our results.

# Conclusions

We have assembled the best-studied sample of main-sequence galaxies at $z\sim4.5$ to date, to investigate key parameters of the ISM as well as the relation between \[O ii\] and total SFR of galaxies in the early Universe right after the Epoch of Reionisation.

The $10$ main-sequence galaxies at $z\sim4.5$ have measurements of rest-frame UV absorption lines, optical \[O ii\] (from spectroscopy and narrow-band imaging) and H$\alpha$ emission (from *Spitzer*), as well as far-infrared observations of \[C ii\] and dust continuum from ALMA. We use the total SFRs derived from \[C ii\] emission as well as far-infrared continuum to calibrate the relation between SFR and \[O ii\] emission for the first time at these redshifts (Section [3.1](#sec:discussionSFR)). Furthermore, we constrain key parameters of their ISM (metallicity, electron density, ionisation parameter) via the UV absorption lines and \[O ii\]/\[C ii\] and \[O ii\]/H$\alpha$ luminosity ratios, which we compare to CLOUDY simulations (Sections [2.2](#sec:metallicity) and [3.2](#sec:discussioncloudy)). Our findings can be summarised as follows:

- The relation between dust-corrected \[O ii\] luminosities and total SFR is best described by sub-solar metallicity models from (cite: KEWLEY04). For the median of our sample, we find a total SFR of $53.57^{+23.48}_{-31.30}\,{\rm M_{\odot}\,yr^{-1}}$ and $\log(L_{\rm [OII]} / {\rm L_{\odot}}) = 9.88^{+0.29}_{-0.51}$. The original (cite: KENNICUTT98) \[O ii\]$-$SFR relation would overestimate the SFR by a factor of $\sim3$ (Section [3.1.2](#sec:discussionOIISFR)).

- By comparing the $\log(L_{\rm [OII]}/L_{\rm [CII]})$ and $\log(L_{\rm [OII]}/L_{\rm H\alpha})$ luminosity ratio to CLOUDY models, we find that our galaxies have ionisation parameters $\log(U) < -2$ and electron densities of $\log(n/[{\rm cm^3}]) \sim 2.5-3$. The former is consistent with $z\sim2-3$ galaxies, the latter may be slightly higher than expected based on our galaxies’ specific SFR. However, these results depend on the input parameters for the CLOUDY simulation. Specifically, increasing the stellar metallicity of the incident spectrum from $10\%$ solar to solar would make our observations more consistent with electron densities measured in $z=2-3$ galaxies.

All in all, we find that the ISM properties of this representative sample of $z\sim4.5$ galaxies are similar to their descendants at $z\sim2-3$ when matched by their specific SFRs. There are indications that the ionisation parameter of more primordial galaxies in the Epoch of Reionisation at $z>6$ is increased (cite: HARIKANE20) compared to our findings. This suggests a rapid evolution of the ISM in the few $100\,{\rm Myrs}$ spanning these epochs. The relation between \[O ii\] emission and SFR is consistent if assuming a gas-phase metallicity of $\sim50\%$ solar, which is in line with the estimates from rest-frame UV absorption spectroscopy. This result is an important step towards using optical emission lines as total SFR indicators in the era of JWST.

In this work, we demonstrated the necessity the combination of data from many facilities covering the rest-frame UV to far-infrared to decipher the physical properties of high-redshift galaxies. Although this is the largest and best-studied sample of typical $z\sim4.5$ galaxies to-date, larger samples with similar multi-wavelength observations are crucial for a better statistical study of the dependence of the reported parameters on other galaxy properties. Larger surveys with current facilities (e.g., *Keck*) and later JWST will provide these samples.

+:-----------------------------:+:--------------------------------------:+:-----------------------:+:-----------------------------:+:-----------------------:+:---------------:+:-----------------------------:+:-----------------------------:+:------------------:+:----------------------:+:---------------:+:-----------------------------:+
| **Broad-band**                                                                                                                                             | **ALMA**                                                                        | ***Keck*/DEIMOS**                           | ***Keck*/MOSFIRE**                              |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+---------------------------------------------+-------------------------------------------------+
| —————————————————————————                                                                                                                                  | ——————————————–                                                                 | —————————                                   | —————————                                       |
+-------------------------------+----------------------------------------+-------------------------+-------------------------------+-------------------------+-----------------+-------------------------------+-------------------------------+--------------------+------------------------+-----------------+-------------------------------+
| $\log({\rm M_*})$             | $\rm SFR_{\rm SED}$                    | $\rm E(B-V)_{SED}$      | $\rm \log(L_{UV})$            | $\beta$                 | $z_{\rm [CII]}$ | $\log(\rm L_{IR})$            | $\log(\rm L_{[CII]})$         | $z_{\rm Ly\alpha}$ | EW(Ly$\rm \alpha$)     | $z_{\rm [OII]}$ | $\log(\rm L_{[OII]})$         |
+-------------------------------+----------------------------------------+-------------------------+-------------------------------+-------------------------+-----------------+-------------------------------+-------------------------------+--------------------+------------------------+-----------------+-------------------------------+
| $\left[\rm{M_{\odot}}\right]$ | $\left[\rm{M_{\odot}\,yr^{-1}}\right]$ | $\left[\rm{mag}\right]$ | $\left[\rm{L_{\odot}}\right]$ |                         |                 | $\left[\rm{L_{\odot}}\right]$ | $\left[\rm{L_{\odot}}\right]$ |                    | \[Å\]                  |                 | $\left[\rm{L_{\odot}}\right]$ |
+-------------------------------+----------------------------------------+-------------------------+-------------------------------+-------------------------+-----------------+-------------------------------+-------------------------------+--------------------+------------------------+-----------------+-------------------------------+
| 9.96$^{+0.16}_{-0.11}$        | 88.0$^{+61.1}_{-43.3}$                 | 0.25$^{+0.05}_{-0.05}$  | 10.97$^{+0.06}_{-0.06}$       | -1.20$^{+0.42}_{-0.18}$ | 4.5777          | 11.67$^{+0.10}_{-0.13}$       | 8.84$^{+0.04}_{-0.04}$        | 4.5854             | 57.4$^{+18.0}_{-18.0}$ | 4.5793          | 9.22$^{+0.05}_{-0.06}$        |
+-------------------------------+----------------------------------------+-------------------------+-------------------------------+-------------------------+-----------------+-------------------------------+-------------------------------+--------------------+------------------------+-----------------+-------------------------------+

\

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | z$_{\rm [CII]}$ | log(L$_{\rm {OII}}$) | log(L$_{\rm{[CII]}}$) | log(L$_{\rm FIR}$) | log(M) | SFR$_{\rm [CII]}$ | SFR$_{\rm FIR}$ | SFR$_{\rm UV}$ |
|  |  | $\left[\rm{L_{\odot}}\right]$ | $\left[\rm{L_{\odot}}\right]$ | $\left[\rm{L_{\odot}}\right]$ | $\left[\rm{M_{\odot}}\right]$ | $\left[\rm{M_{\odot}\,yr^{-1}}\right]$ | $\left[\rm{M_{\odot}\,yr^{-1}}\right]$ | $\left[\rm{M_{\odot}\,yr^{-1}}\right]$ |
| DC_665626 | 4.5830 | 9.36$^{+0.08}_{-0.09}$ | 8.21$^{+0.10}_{-0.13}$ | – | 9.21$^{+0.16}_{-0.18}$ | 23.15$^{+1.22}_{-1.30}$ | – | 5.77$^{+1.24}_{-1.23}$ |
| DC_680104 | 4.5320 | 9.51$^{+0.10}_{-0.13}$ | 8.74$^{+0.12}_{-0.16}$ | – | 9.23$^{+0.18}_{-0.12}$ | 66.30$^{+1.25}_{-1.36}$ | – | 14.55$^{+1.12}_{-1.10}$ |
| VC_5100969402 | 4.5869 | 9.34$^{+0.08}_{-0.10}$ | 8.72$^{+0.04}_{-0.05}$ | 11.65$^{+0.11}_{-0.16}$ | 10.00$^{+0.14}_{-0.12}$ | 63.42$^{+1.09}_{-1.10}$ | 43.23$^{+13.06}_{-13.06}$ | 12.50$^{+1.14}_{-1.13}$ |
| VC_5100994794 | 4.5783 | 9.14$^{+0.11}_{-0.15}$ | 8.75$^{+0.04}_{-0.04}$ | 11.20$^{+0.12}_{-0.16}$ | 9.73$^{+0.13}_{-0.15}$ | 66.93$^{+1.08}_{-1.09}$ | 15.50$^{+4.71}_{-4.71}$ | 10.69$^{+1.19}_{-1.23}$ |
| VC_5101209780 | 4.5700 | 8.99$^{+0.30}_{-0.38}$ | 8.86$^{+0.08}_{-0.10}$ | 11.62$^{+0.13}_{-0.19}$ | 10.05$^{+0.12}_{-0.12}$ | 84.45$^{+1.18}_{-1.23}$ | 40.65$^{+14.64}_{-14.64}$ | 22.07$^{+1.09}_{-1.10}$ |
| VC_5101210235 | 4.5733 | 9.06$^{+0.16}_{-0.30}$ | 8.35$^{+0.11}_{-0.14}$ | – | 9.78$^{+0.15}_{-0.12}$ | 30.71$^{+1.24}_{-1.33}$ | – | 24.08$^{+1.08}_{-1.07}$ |
| VC_5101218326 | 4.5678 | 9.32$^{+0.08}_{-0.10}$ | 9.26$^{+0.02}_{-0.02}$ | 11.79$^{+0.07}_{-0.08}$ | 11.01$^{+0.05}_{-0.07}$ | 184.45$^{+1.04}_{-1.04}$ | 60.38$^{+10.30}_{-10.30}$ | 27.94$^{+1.06}_{-1.07}$ |
| VC_5101244930 | 4.5769 | 9.09$^{+0.30}_{-0.19}$ | 8.70$^{+0.08}_{-0.10}$ | – | 9.67$^{+0.13}_{-0.16}$ | 61.73$^{+1.18}_{-1.23}$ | – | 17.45$^{+1.12}_{-1.12}$ |
| VC_5110377875 | 4.5441 | 9.21$^{+0.18}_{-0.32}$ | 9.23$^{+0.03}_{-0.03}$ | – | 10.17$^{+0.21}_{-0.12}$ | 174.87$^{+1.05}_{-1.06}$ | – | 24.67$^{+1.09}_{-1.08}$ |

\

**Notes:** The UV SFRs have not been corrected for dust attenuation. \[C ii\] SFRs derived using the (cite: ALPINE_SCHAERER20) relation (see Section [3.1.1](#sec:discussionTotalSFR)). Far-infrared SFRs derived using the (cite: KENNICUTT98) relation.

+:----------------------------------+:--------------------:+:---------------------:+:----------------------:+:--------------------:+
|                                   | **SFR $[\rm M_{\astrosun}\,yr^{-1}]$**                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------+
|                                   | ———————————————————–                                                                         |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| Reference                         | \[O ii\]             | \[C ii\]              | IR                     | UV                   |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| **K98**                           | 50.0$^{+6.7}_{-6.1}$ |                       | 46.0$^{+11.9}_{-11.9}$ | 13.3$^{+2.0}_{-1.8}$ |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| **K04**$^\dagger$                 |                      |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- no met. dep.                   | 23.6$^{+3.2}_{-2.7}$ |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- solar                          | 18.6$^{+2.5}_{-2.3}$ |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- half-solar                     | 13.8$^{+1.9}_{-1.7}$ |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- $1/5^{\rm th}$-solar           | 10.3$^{+1.4}_{-1.5}$ |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| **L14**                           |                      |                       |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- metal-poor dwarfs              |                      | 22.0$^{+1.6}_{-1.6}$  |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- starburst                      |                      | 59.9$^{+5.5}_{-5.5}$  |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- AGN                            |                      | 73.0$^{+6.0}_{-6.1}$  |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- high-$z$                       |                      | 80.9$^{+8.9}_{-8.7}$  |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| \- ULIRGs                         |                      | 360.7$^{+4.3}_{-4.3}$ |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| **S20**                           |                      | 64.1$^{+6.2}_{-5.7}$  |                        |                      |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+
| dust correction factor$^\ddagger$ | 5.2 (4.3)            | $-$                   | $-$                    | 3.4 (3.5)            |
+-----------------------------------+----------------------+-----------------------+------------------------+----------------------+

: Summary of SFRs measured from \[O ii\]  and ancillary *ALPINE* data available for *DC_881725*. Note that SFRs from UV and optical indicators have not been corrected for dust attenuation.

\

$^\dagger$ The first value is derived using their equation 4. The other values are derived for different gas-phase metallicities and their equation 10.

$^\ddagger$ Dust correction factor for \[O ii\] and UV continuum emission assuming a reddening curve from (cite: CALZETTI00) and (cite: REDDY15) (in parenthesis), respectively (see text for more details). The \[O ii\] correction factor assumes a differential dust attenuation $f=0.44$. For $f=0.7$, decrease the value by a factor of $1.8$.

**References:** K98 $-$ (cite: KENNICUTT98); K04 $-$ (cite: KEWLEY04); L14 $-$ (cite: DELOOZE14); S20 $-$ (cite: ALPINE_SCHAERER20).

# Acknowledgements

We thank Yuichi Harikane for the helpful inputs on running CLOUDY and the anonymous referee for the comments which improved this manuscript. We also thank Behnam Darvish and Nick Scoville for letting us add *DC_881725* to their *MOSFIRE* mask. G.C.J. acknowledges ERC Advanced Grant 695671 “QUENCH” and support by the Science and Technology Facilities Council (STFC). This work made use of v2.2.1 of the Binary Population and Spectral Synthesis (BPASS) models as described in (cite: ELDRIDGE17) and (cite: STANWAY18).

This work was supported by the Programme National Cosmology et Galaxies (PNCG) of CNRS/INSU with INP and IN2P3, co-funded by CEA and CNES.

This paper uses data obtained with the ALMA Observatory, under Large Program *2017.1.00428.L*. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This work is based on observations and archival data made with the *Spitzer Space Telescope*, which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

Some of the material presented in this paper is based upon work supported by the National Science Foundation under Grant No. 1908422.

MT acknowledges the support from grant PRIN MIUR 2017 20173ML3WW 001.

Furthermore, this work is based on data from the W. M. Keck Observatory and the Subaru Telescope. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Mauna Kea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain.

Based on data products from observations made with ESO Telescopes at the La Silla Paranal Observatory under ESO programme ID 179.A-2005 and on data products produced by CALET and the Cambridge Astronomy Survey Unit on behalf of the UltraVISTA consortium.

Finally, we would also like to recognize the contributions from all of the members of the COSMOS Team who helped in obtaining and reducing the large amount of multi-wavelength data that are now publicly available through IRSA at <http://irsa.ipac.caltech.edu/Missions/cosmos.html>.

# Data Availability

The data underlying this article will be shared on reasonable request to the corresponding author.

# Absolute Flux Calibration of the *MOSFIRE* Spectrum

For the absolute calibration of the *MOSFIRE* spectrum, we use a $17^{\rm th}$ magnitude standard star from the 2MASS star catalogue, which was included for this purpose in the mask. The one-dimensional spectrum of the star is extracted within $10\,{\rm pixels}$ ($1.8\ensuremath{''}$) around the centre of the continuum emission on the two-dimensional spectrum in ${\rm e^{-}/s}$. The wavelength-dependent calibration is then derived by comparing the observed spectrum with models of different stellar spectral types.

In detail, we use the spectra from the (cite: PICKLES98) stellar model library, which offers a wide range in spectral types from O to M and covers a wavelength from $0.115-2.5\,{\rm \mu m}$ in steps of $5\,{\rm \text{\normalfont\AA}}$. This is sufficiently red to match the *MOSFIRE* $K-$band. We find that the spectrum at $>2\,{\rm \mu m}$ only changes slowly as a function of stellar type, hence we only focus on a coarse grid including O5 V, B3 V, A5 V, F5 V, G5 V, K5 V, and M5 V type stars. The model spectrum of each of these is normalised to the UltraVista $K-$band flux of the observed 2MASS star, obtained from the *COSMOS2015* catalogue (cite: LAIGLE16; MCCRACKEN12). A wavelength-dependent conversion from units of $\rm e^{-}\,s^{-1}$ to $\rm erg\,s^{-1}\,cm^{-2}\,\text{\normalfont\AA}^{-1}$ is then derived by comparing the normalised model spectrum to the observed spectrum of the 2MASS star. The resulting normalisations are shown in Figure [7](#fig:normalization). The arrow indicates the wavelength of \[O ii\]. The computed normalization is within $5\%$ for all spectral types except the coolest M-dwarf. By comparing the $K-$band normalised stellar spectra to the UltraVISTA $Y$, $J$, and $H$ photometry, we find that our standard star fits best a G$-$type star. We therefore use the G5 V normalisation through out the paper.

![](figures/normalization_startypes.pdf)

# Comparison of Optical Emission Line Measurements to *EL-COSMOS*

We derived the H$\alpha$ luminosities for our $10$ galaxies from their *Spitzer* \[$3.6\,{\rm \mu m}$\]$-$\[$4.5\,{\rm \mu m}$\] colours (see (cite: ALPINE_FAISST20) and (cite: FAISST16a) for a detailed description of the methods used). Here we compare our measurement to the recent *EL-COSMOS* catalogue (cite: SAITO20), which provides predictions of the intrinsic (dust-corrected) \[O ii\] and H$\alpha$ optical lines from SED fitting calibrated to spectroscopic measurements for all galaxies in the (cite: LAIGLE16) *COSMOS2015* catalogue. Our luminosity measurements have been dust corrected using the method described in the this paper. Figure [8](#fig:elcosmos) shows the result of the comparison. *EL-COSMOS* agrees very well with our narrow-band and spectroscopic \[O ii\] measurements. Comparing the H$\alpha$ measurements, we find a good agreement within a factor of $2$. Note that we marked galaxies that have uncertain H$\alpha$ measurements due to contaminated *Spitzer* photometry (cite: ALPINE_FAISST20).

![](figures/L_comparison_ELCOSMOS.pdf)

[^1]: E-mail: bxv3026@rit.edu

[^2]: The ionisation parameter is essentially the ratio of ionising photon density to hydrogen. It is also a measure for the radiation pressure feedback, as it reflects the radiation-to-gas-pressure ratio (cite: YEH12).

[^3]: <https://keck-datareductionpipelines.github.io/MosfireDRP/>

[^4]: The velocity shifts quoted assume equal flux of the two blended \[O ii\] lines. We estimate an uncertainty of $\pm30\,{\rm km\,s^{-1}}$ assuming \[O ii\]$_{\rm \lambda 3729}$/\[O ii\]$_{\rm \lambda 3726}$ ratios between $0.35$ and $1.5$, corresponding to the high and low electron density regime (cite: OSTERBROCK74).

[^5]: We set detection parameters of `DETECT_MINAREA` $=5$, `DETECT_THRESH` $=1.5$, and `ANALYSIS_THRESH` $=1.5$. The latter two are relative ($\sigma$) thresholds.

[^6]: We assume a solar oxygen abundance of ${\rm \log(O/H)+12} = 8.76$ according to the “galactic concordance abundances” (cite: NIEVA12; NICHOLLS17), which is close to the primordial solar abundance (cite: ASPLUND09).

[^7]: The “$f-$factor” is the differential dust attenuation between nebular emission and stellar continuum and is defined as $f = {E_{s}(B-V)}/{E_{n}(B-V)}$.

[^8]: Note that this parameterization is consistent with earlier derivations (cite: BUAT05; BURGARELLA05; KONG04; MEURER99).

[^9]: Converted to a (cite: CHABRIER03) IMF.

[^10]: Converted to a (cite: CHABRIER03) IMF.

[^11]: Converted to a (cite: CHABRIER03) IMF.

[^12]: Note that $U = q/c$, where $c=3\times10^{10}\,{\rm cm\,s^{-1}}$ is the speed of light.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[2]",
  "value": "Reduce Keck/MOSFIRE K-band data, calibrate wavelength with sky lines, perform absolute flux calibration using a 2MASS standard star matched to a Pickles G5 V model normalized to UltraVISTA K-band, extract 1D spectrum in a 6-pixel spatial window, and fit a single Gaussian to the [O II] line.",
  "failed_quote": "The [O ii] line flux is derived by fitting a single Gaussian with variable mean, $\\sigma$, and total flux to the one-dimensional spectrum (Figure 3, black solid line)."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "Single Gaussian fit with variable mean, sigma, and total flux; uncertainties from 500 Monte Carlo realisations",
  "failed_quote": "The [O ii] line flux is derived by fitting a single Gaussian with variable mean, $\\sigma$, and total flux to the one-dimensional spectrum (Figure 3, black solid line)."
 }
]
```
