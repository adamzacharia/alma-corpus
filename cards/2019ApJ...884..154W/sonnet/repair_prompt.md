# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...884..154W\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Discovery of a dark, massive, ALMA-only galaxy at $z\sim5-6$ in a tiny 3-millimeter survey

## Abstract

We report the serendipitous detection of two 3 mm continuum sources found in deep ALMA Band 3 observations to study intermediate redshift galaxies in the COSMOS field. One is near a foreground galaxy at 1.3$''$, but is a previously unknown dust-obscured star-forming galaxy (DSFG) at probable $z_{CO}=3.329$, illustrating the risk of misidentifying shorter wavelength counterparts. The optical-to-mm spectral energy distribution (SED) favors a grey $\lambda^{-0.4}$ attenuation curve and results in significantly larger stellar mass and SFR compared to a Calzetti starburst law, suggesting caution when relating progenitors and descendants based on these quantities. The other source is missing from all previous optical/near-infrared/sub-mm/radio catalogs (“ALMA-only”), and remains undetected even in stacked ultradeep optical ($>29.6$ AB) and near-infrared ($>27.9$ AB) images. Using the ALMA position as a prior reveals faint $SNR\sim3$ measurements in stacked IRAC 3.6+4.5, ultradeep SCUBA2 850$\mu$m, and VLA 3GHz, indicating the source is real. The SED is robustly reproduced by a massive $M^*=10^{10.8}$M$_\odot$ and $M_{gas}=10^{11}$M$_\odot$, highly obscured $A_V\sim4$, star forming $SFR\sim300$ M$_{\odot}$yr$^{-1}$ galaxy at redshift $z=5.5\pm$1.1. The ultrasmall 8 arcmin$^{2}$ survey area implies a large yet uncertain contribution to the cosmic star formation rate density CSFRD(z=5) $\sim0.9\times10^{-2}$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$, comparable to all ultraviolet-selected galaxies combined. These results indicate the existence of a prominent population of DSFGs at $z>4$, below the typical detection limit of bright galaxies found in single-dish sub-mm surveys, but with larger space densities $\sim3 \times 10^{-5}$ Mpc$^{-3}$, higher duty cycles $50-100\%$, contributing more to the CSFRD, and potentially dominating the high-mass galaxy stellar mass function.

# Introduction

In past decades, single dish sub-millimeter surveys have identified populations of massive, dusty star-forming galaxies at $z>1$ (cite: Casey2014). While these galaxies are rare even at Cosmic Noon ($1<z<3$) when the star-formation activity in the Universe peaks, their contribution to the cosmic star-formation rate density (CSFRD) equals that of all optical and near-infrared selected galaxies combined (cite: MadauDickinson2014). However, at $z>3$ the situation is much less certain. A tail of sub-millimeter selected galaxies have been confirmed beyond $z>4$, but they trace only the very tip of the star-formation rate (SFR) distribution at early times (cite: Cooray2014; Strandet2017; Marrone2018). The total contribution of dust-obscured star-formation, and therefore the census of star-formation in the early Universe, is unknown. Despite the strongly negative k-correction allowing sources to be found to $z=10$, the overwhelming majority of (sub)-mm selected galaxies continue to be confirmed at $z<3$ with Atacama Large Millimeter/submillimeter Array (ALMA) spectroscopy (cite: Danielson2017; Brisbin2017). While some dusty galaxies have been discovered beyond $z>5$ through gravitational lensing (cite: Spilker2016; Zavala2018Nat), the lensing correction and selection effects make it challenging to establish their contribution to the CSFRD. Progress is hampered by the limited sensitivity and low spatial resolution of single-dish sub-mm observations and the difficulty of associating detections with counterparts in the optical-NIR. Ultradeep SCUBA surveys over moderate $\sim100$ arcmin$^2$ are now pushing into the range of “normal” star formation rates (several 100 M$_\odot$/yr, main sequence galaxies) (cite: Koprowski2016; Cowie2017; Cowie2018) and extending to $z>4$, but the analysis is often limited by the ability to identify counterparts at other wavelengths and derive accurate redshifts.

ALMA has opened an avenue to address this issue through surveys at superior sensitivity and spatial resolution. ALMA deep fields at $\sim$1 mm (cite: Dunlop2017; Aravena2016a) have probed to extremely deep flux limits over small areas ($<5$ arcmin$^2$). Progress has still been limited likely because dust obscured star formation preferentially occurs in massive galaxies (cite: Whitaker2017), which are clustered and relatively rare ($\sim$0.1 arcmin$^{-2}$ at $\log(M/M_\odot)>$10.8 and $z\sim4$; (cite: Davidzon2017)). Wider (10’s arcmin$^2$) and shallower ($\sim$100-200$\mu$Jy) ALMA surveys at $\sim$1mm (cite: Hatsukade2018; Franco2018) are now approaching large enough areas to identify tentative massive candidates at $z>4$ (cite: Yamaguchi2019).

A promising development is to select at longer wavelengths ($>2$ mm), which optimizes the selection to dusty star formation at redshift $z>4$ (cite: Bethermin2015b; Casey2018b). However, the current state-of-the-art ALMA Spectroscopic Survey (ASPECS) at 3-mm (cite: GonzalezLopez2019), still only covered $\sim5$ arcmin$^{2}$, and identified 6 continuum sources, all at $z<3$. Larger archival studies of ALMA 3 mm observations to find high-redshift candidates report some spectroscopic confirmations, but like the 1-mm redshift distribution, the majority lie at $z<3$ (cite: Zavala2018_3mm).

Recent advances with IRAM/GISMO provide evidence that $2$mm surveys favor selecting higher-redshift sources (cite: Magnelli2019), although counterpart identification continues to be problematic due to large beam sizes. Overall, the number of strong candidates for dust-obscured sources at $z>4$ remains small and as a result, the contribution of dust-obscured star formation in the early universe is poorly constrained.

![](fig1.pdf)

![](fig2.pdf)

![](fig3.pdf)

Here we report the serendipitous discovery of 2 previously unknown sources in deep ALMA 3-mm observations in the COSMOS field, and assess the implications for dust obscured star formation at $z>3$. We assume a $\Lambda$CDM cosmology with H$_0$=70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_M$ = 0.3, $\Omega_\Lambda$ = 0.7, and a (cite: Kroupa2001) initial mass function (IMF).

# Methods

## ALMA millimeter interferometry

The ALMA observations are part of a program targeting CO(2-1) line emission in $z\sim1.5$ galaxies (2018.1.01739.S, PI: Williams; 2015.1.00853.S, PI: Bezanson) in the COSMOS field. The data presented here include ALMA maps of five galaxies, and results on these targets are presented elsewhere ((cite: Bezanson2019)). In one of these pointings we identified two serendipitous continuum sources, unrelated to the original target, which we will describe now in detail.

ALMA Band 3 observations were carried out in two observing blocks on 2018 December 23 and 24 under program 2018.1.01739.S (PI: Williams). One 1.875 GHz spectral window was centered at the sky frequency (94.92 GHz) with 7.8 MHz ($\sim$24 km s$^{-1}$) channelization. Three additional 1.875 GHz bandwidth spectral windows were placed at sky frequencies 96.8, 106.9, and 108.8 GHz for continuum observations, each with 15.6 MHz channelization. A total of 43 antennas were active reaching maximum baselines of 500m, for an angular resolution of $\sim$2 arcsec (synthesized beam major axis = 2.2”, minor axis = 1.7” under natural weighting). The total time on-source was 97 min.

The data were reduced using the standard ALMA Cycle 6 pipeline, and no problems with the pipeline calibration were found. The imaged data reach a continuum sensitivity of 5.7$\mu$Jy/beam at 101.9 GHz, and a typical line sensitivity of 55-65$\mu$Jy/beam per 100 km s$^{-1}$ channel. We imaged the data using natural weighting, creating a 101 GHz continuum image of the field from all four spectral windows. We imaged the data using 0.2” pixels and created a 500$\times$500 pixel image, yielding images 100” on a side. Given the ALMA primary beam at this frequency ($\sim$57” FWHM), these images extend to approximately the 0.05 response point of the primary beam.

## ALMA source detection

Interferometric maps without correction for the primary beam response have uniform, normally-distributed noise properties across the field, and source detection significance is straightforward to measure from such maps. Two blind 3 mm continuum sources were apparent in this map, located 24.6” and 38.2” from the phase center, corresponding to primary beam response levels of 0.57 and 0.29, respectively. Each source is detected at a peak signal-to-noise ratio of $\sim8$; the probability of finding a Gaussian noise fluctuation of this magnitude given the number of independent beams in the images is exceedingly low ($<10^{-9}$). Both sources thus are real. The 3 mm flux densities of these sources, corrected for the primary beam response, are 155 $\pm$ 20 $\mu$Jy and 75 $\pm$ 10, hereafter referred to as $3MM$-1 and $3MM$-2, respectively. Neither source is spatially resolved, based on a comparison of the peak pixel values and the integrated flux densities.

After finding both continuum sources in the combined map, we re-imaged the upper and lower sidebands of the data separately in order to determine the spectral index of each source at these frequencies. Thermal dust emission on the Rayleigh-Jeans tail has a very steep power-law index with $S_\nu \propto \nu^{2+\beta}$ and $\beta \sim 1.5-2$, while non-thermal synchrotron emission typically exhibits a negative spectral index, $S_\nu \propto \nu^{-0.8}$. Given their respective frequencies, we expect dust emission to be $\sim50-60$% brighter in the upper sideband than the lower. We find spectral indices for both continuum sources in excellent agreement with the expectation for thermal dust emission.

We also re-imaged the data of both sidebands to search for blindly-detected emission lines in each of the two continuum sources, using channel widths ranging from 100-400 km s$^{-1}$. $3MM$-2 contains a serendipitous emission line centered at 106.5 GHz, with an integrated flux density of 0.66 $\pm$ 0.1 Jy km s$^{-1}$. The spectrum is shown in Figure [2](#fig:CO43). A Gaussian fit indicates in a width of $630\pm 70$ km/s. Assuming the line is a transition of carbon monoxide, the possible redshifts are $z=$\[0.08, 1.16, 2.25, 3.33, 4.41, 5.49\]. We find no significant emission lines in the spectrum of $3MM$-1, and no evidence for a line at the same frequency of $3MM$-2. A Gaussian fit restricted to the same frequency and width results in an integrated flux density of $0.17 \pm 0.2$ Jy km s$^{-1}$, indicating no evidence for a line at that location.

Both $3MM$-1 and $3MM$-2 were also contained within the field-of-view of an additional ALMA Band 3 program, 2015.1.00861.S. Both sources were again far out in the primary beam of these data, at approximately the 0.25 and 0.1 response points, respectively. These data are described in more detail in (cite: Silverman2018), and have non-overlapping frequency coverage with our own data. We downloaded and imaged these data following the same procedure as for our own data. The new images reach a continuum sensitivity at phase center of 10$\mu$Jy/beam at 93.5GHz and a line sensitivity of 120-170$\mu$Jy/beam per 100 km s$^{-1}$ channel, approximately a factor of two higher than in our data. Neither source is detected in continuum in these data, and were not expected to be detected given the sensitivity, effective frequency, and position of our sources within the ALMA primary beam. We additionally searched these data for blindly-detected CO lines as in our own data, but found no significant emission lines. The limited (primary beam-corrected) sensitivity of these data preclude us from drawing strong conclusions about the redshifts of either source.

For convenience, we define an equivalent survey area as the total area across all five ALMA maps at which a source with the same $S_{\footnotesize{\textrm{3mm}}}$ as $3MM$-1 would be detected at $>5\sigma$. Taking into account the small variations in the central frequency of each map (tuned to the specific redshift of the target $z\sim$1.5 galaxies), which change the primary beam response shape and the detection threshold (25-31$\mu$Jy) due to the steep spectral index of dust emission, we derive a total survey area of 8.0 arcmin$^{2}$ to 155$\mu$Jy ($5\sigma$ limit).

## Multi-wavelength photometry

$3MM$-1 has extremely deep coverage at all optical-to-sub-mm wavelengths, yet it has no counterpart within a radius of 3.3 arcseconds in the deepest published multiwavelength catalogs in COSMOS to date, from $0.6-1100\mu$m (cite: Laigle2016; Muzzin2013; Aretxaga2011; Geach2017; Hurley2017; LeFloch2009) or $3-1.4$ GHz (cite: Schinnerer2010; Smolcic2017). The astrometry of multi-wavelength catalogs in COSMOS are excellent owing to the registration between VLA observations (cite: Schinnerer2007), ground-based optical and space-based facilities, with an astrometric accuracy of 5 milli-arcseconds (cite: Koekemoer2007). Similar astrometric accuracy was found between ALMA and COSMOS multiwavelength datasets (cite: Schreiber2017). There is no apparent flux at optical-to-Spitzer/IRAC wavelengths at the ALMA position (Figure [1](#cutout)). $3MM$-2 is also missing from these catalogs, likely because it is blended with a bright neighboring galaxy $\sim1.3\ensuremath{''}$ to its north with photometric redshift 0.95 (see Figure [1](#cutout)), but appears detected in $Ks$ and IRAC. It is possible that the ALMA source is simply a highly obscured region in the low-redshift galaxy, which can be ruled out by spatially deblended SED analysis. We therefore proceeded to perform deblended photometry on both ALMA positions using the following data sets.

### Optical, near-infrared, and Spitzer/IRAC

The optical data consists of the Subaru/Suprime-Cam $B_j$, $V_j$, $g^+$, $r^+$, $i^+$ and $z^+$-imaging (cite: Taniguchi2007), with $5\sigma$ limits of $\sim25-27.4$ mag in $1.2\ensuremath{''}$ apertures, and Subaru HyperSuprimeCam (HSC) $g$, $r$, $i$, $z$ and $y$ ((cite: Aihara2018a; Aihara2018b)) imaging ($\sim25-26.8$ mag, $5\sigma$). Ultradeep NIR coverage is provided by the 4th data release of the UltraVISTA survey  (cite: Mccracken2012), thanks to mosaics in the $Y$, $J$, $H$ and $K_s$ filters to $\sim25$ mag (AB, $5\sigma$). Remarkably, the coverage in the $K_\mathrm{s}$ band from DR4 is $\sim0.9$ mag deeper than from DR3, allowing us to place strong constraints on the flux density of $3MM$-1 at NIR wavelengths. Stacked images were constructed using the optical imaging $0.4-0.8$ micron and in the near-infrared imaging $0.9-1.6$ micron. We use *Spitzer*/IRAC $3.6\mu$m and $4.5\mu$m mosaics that combine data from the S-COSMOS ((cite: Sanders2007)) and the *Spitzer* Large Area Survey with HSC (SPLASH, PI: Capak) programs ($\sim24.5$ mag, $5\sigma$ in $1.8\ensuremath{''}$ apertures), and the $5.8\mu$m and $8.0\mu$m from the S-COSMOS program ($\sim20.7$ mag, $5\sigma$ in $1.8\ensuremath{''}$ apertures).

We measured flux densities for $3MM$-1 in the optical and UltraVISTA bands in $1.2\ensuremath{''}$-diameter apertures after subtracting the neighbors using MOPHONGO ((cite: Labbe2013; Labbe2015)). This procedure carefully models the light profiles of the sources using a higher resolution image as a prior, minimizing potential contamination by bright nearby objects (see Figure [3](#deblend)). In our analysis we adopted the HSC $z$-band image as prior for $3MM$-1 as it provides the best compromise between depth and resolution and the F814W-band image for $3MM$-2, given the nearby bright neighbor at $\sim1.3\ensuremath{''}$ distance. Because of the broader PSF, we adopted $1.8\ensuremath{''}$ apertures for our estimates in the IRAC bands. Total flux densities were then estimated from the spatial profile and the relevant PSF-correction kernel.

### Far-infrared to submillimeter

Far-infrared and sub-millimeter *Herschel* fluxes were measured for both galaxies by simultaneously fitting Gaussian profiles at fixed prior locations in the *Herschel* images specified by the ALMA locations and augmented by the MIPS positions of all neighboring objects from the S-COSMOS data (cite: Sanders2007; LeFloch2009). The FWHM of the Gaussians were 7.7, 12" (PACS 100, 160$\mu$m) and 18, 25 and 37" (SPIRE 250, 350, 500$\mu$m), respectively. Uncertainties were computed by fitting gaussians at random locations within a 2 arcmin radius and computing the rms. Flux calibration was performed by comparing to the 24$\mu$m prior catalog of *Herschel* DR4 (cite: Oliver2012; Hurley2017). Comparison of the measured SPIRE fluxes with those published showed a scatter of 30%; this was added in quadrature to the flux uncertainties for those bands. The correction is minor considering the signal to noise ratio of $\lesssim1$ of the SPIRE fluxes. For SPIRE 500$\mu$m only, the flux of a neighboring $z_{spec}=1.45$ galaxy 5” to the south was subtracted separately prior to deblending, using its predicted IR emission based on the infrared SED of (cite: Wuyts2011) and its SFR$_{24,IR}$=65 M$_\odot$/yr.

The procedure for measuring photometry at 850$\mu$m follows that of *Herschel*/PACS and SPIRE (250 and 350$\mu$m) using the ALMA and MIPS positions as priors. The sources lie in a region of shallower ($\sigma_{850}\sim$3 mJy/beam) coverage in the inhomogenous SCUBA-2 Cosmology Legacy Survey (cite: Geach2017) and are undetected in this map. We therefore use the state-of-the-art S2COSMOS observations (Simpson priv. comm.), which achieved a $\sigma_{850}\sim1.2$mJy over the entire field (Simpson et al. in prep).

### Radio VLA 3Ghz and 1.4 Ghz

Neither source has a counterpart in either the VLA 3 GHz 5$\sigma$ source catalog (cite: Smolcic2017) or the 1.4 GHz deep survey 5$\sigma$ source catalog (cite: Schinnerer2010). Photometry on the 3GHz map using the ALMA position as prior reveals 9.98$\pm$2.39 $\mu$Jy/beam (4$\sigma$) point source for $3MM$-1, below the detection limit of the (cite: Smolcic2017) catalog. Blindly detected sources at this flux density have a high probability ($>$50%) of being spurious (cite: Smolcic2017), therefore requiring the ALMA prior in order to be considered real. $3MM$-2 shows no significant flux to 3$\sigma$ limits of $\sim7\mu$Jy/beam. Within 10 arcmin$^2$, the 1.4 GHz map has rms $\sim$17 $\mu$Jy/beam and no significant flux ($>3\sigma$) is detected from either galaxy.

## Spectral Energy Distribution Modeling

The deep photometry from $\lambda=0.4-3000\mu$m places strong constraints on the SEDs and allows us to model their stellar populations and redshift. It should be noted that even if a source is not formally detected ($>3\sigma$) at most wavelengths, absence of flux can still provide useful constraints, in particular on the redshift. All fitting is performed in linear fluxes and uncertainties and no upper limits are enforced on measurements with low SNR.

We use the Bayesian Analysis of Galaxies for Physical Inference and Parameter EStimation (BAGPIPES) code (cite: Carnall2018), which assumes the stellar population synthesis models of (cite: Bruzual2003) and implements nebular emission lines following the methodology of (cite: Byler2017) using the CLOUDY photoionization code (cite: Ferland2017). We select the flexible dust absorption model of (cite: Charlot2000), with the exponent of the effective absorption $\propto\lambda^{-n}$ as a free parameter and adopt the (cite: DraineLi2007) dust emission model under the assumption of energy balance, such that dust-absorbed light is re-radiated in the far-infrared. All stellar populations have this effective absorption, while the youngest stars (defined as those with age $<10$Myr) have an extra factor of attenuation applied ($\eta$) to account for dusty birthclouds.

The dust emission model is parameterized using the starlight intensity $U$ incident on the dust (translating into a distribution of dust temperatures), the amount of PAH emission, and the fraction of dust at the coldest temperature. We further assume a delayed exponential star-formation history with $\tau$ and age left free and metallicities ranging from $0.2-2.5 Z_\odot$. For each parameter, uniform, diffuse priors are assumed (see Table [\[tab:sedfit\]](#tab:sedfit)). In general, we do not expect to constrain most free parameters, but we will marginalize over those and limit the discussion to the more important parameters including redshift, stellar mass, and SFR. Where relevant, we will also quote results based on assumptions often used in the literature, such as assuming a fixed (cite: Calzetti2000) dust attenuation model.

![](fig4.pdf)

# Results

The photometry for both galaxies is presented in the Appendix (Table [\[tab:phot\]](#tab:phot)).

## $3MM$-1

$3MM$-1 is undetected ($<3\sigma$) in any individual optical ($>27$AB), near-infrared ($>25.2$), and Spitzer/IRAC ($>25.2$) bands, and remains undetected in the stacked ultradeep optical ($>29.6$ AB) and near-IR ($>27.9$ AB) data ($1\sigma$ limits). The source is faintly detected (25.2 AB $\sim3\sigma$) in deep stacked IRAC 3.6+4.5 observations, indicating the source is likely real with extremely red colors. Owing to the shallower depth, the source is undetected in deep Spitzer/MIPS 24 micron and *Herschel* PACS+SPIRE $160-500$ micron. The flux measured with SCUBA is $S_{850}$=3.5$\pm$1.1 mJy ($SNR=3.1$). This flux density is fainter than the depth typically achieved by deep single dish sub-mm surveys (cite: Weiss2009; Aretxaga2011; Geach2017; Cowie2017) at robust detection thresholds ($\gtrsim4\sigma$). The observed SED is shown in Figure [4](#sed) (left panel). For clarity, photometry with S/N $<$ 1 are indicated with arrows at the 1$\sigma$ rms level, and S/N $>$ 1 with 1$\sigma$ errorbars. The deep non-detections at all wavelengths between $24-500\mu$m and the extreme flux ratios ($S_{24}/S_{850}<4\times10^{-3}$, $S_{24}/S_{3mm}<9\times10^{-2}$, $S_{4.5}/S_{850}<9\times10^{-5}$, $S_{4.5}/S_{3mm}<2\times10^{-3}$, see e.g., (cite: Cowie2018; Yamaguchi2019)), demand that dust peak is highly redshifted $z>4$.

Fitting stellar population models, we find the observations are well reproduced by a massive $10^{10.8\pm0.4}$M$_\odot$, star forming $SFR=309^{+241}_{-149}$M$_\odot$/yr, highly obscured $A_V\sim4^{+1.4}_{-1.0}$ galaxy at very high redshift $z\sim5.5^{+1.2}_{-1.1}$. The SED fitting results are shown in Figure [4](#sed) and the posterior values and priors are listed in Table [\[tab:sedfit\]](#tab:sedfit). The posterior distributions of all parameters are presented in Figure [7](#fig:pdf1). Adopting a classical Calzetti dust law would increase the stellar mass, SFR, and redshift by 60%, 10%, and 5% respectively. These changes are within the uncertainties, so we elect to adopt our more conservative values measured assuming (cite: Charlot2000) as fiducial. We also experimented with fitting only the mid-infrared to sub-millimeter SED, finding the same results. In all cases, the solutions require the galaxy to be at high redshift, with $z>4.1$ at 90% confidence and a total infrared luminosity $L_{IR}=4\times10^{12}L_\odot$ (based on integrating the median posterior spectrum). Adopting an SED typical for the most obscured $A_V>3.5$ SMGs (cite: daCunha2015) produces similar redshift and LIR, as does adopting the Arp 220 SED. Converting to SFR using the (cite: Kennicutt2012) conversion, which does not implicitly assume a SFH, results in a larger estimated SFR$=540$M$_\odot$/yr, but consistent within the 1$\sigma$ uncertainties from SED fitting.

![](fig5.pdf)

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Parameter | $3MM$-1$^a$ | $3MM$-2 | $3MM$-2 | Range (uniform prior) |  |
| Attenuation Curve | CF00 | CF00 | Calzetti |  |  |
| Coordinates | 10:02:36.82 +02:08:40.60 | 10:02:36.30 +2:08:49.55 |  |  |  |
| Redshift | 5.5 $^{+ 1.2 }_{- 1.1 }$ | z$_{CO}$=3.329 | z$_{CO}$=3.329 | (0.0, 10.0) |  |
| SFR \[M$_{\odot}$ yr$^{-1}$\] | 309 $^{+ 241 }_{- 149 }$ | 247 $^{+ 77 }_{- 76 }$ | 112 $^{+ 27 }_{- 38 }$ |  |  |
| Log$_{10}$ Stellar Mass \[M$_{\odot}$\] | 10.8 $^{+ 0.4 }_{- 0.4 }$ | 11.1 $^{+ 0.2 }_{- 0.2 }$ | 10.2 $^{+ 0.2 }_{- 0.2 }$ | (6.0, 14.0) |  |
| Mass-weighted age \[Gyr\] | 0.2 $^{+ 0.1 }_{- 0.1 }$ | 0.5 $^{+ 0.1 }_{- 0.2 }$ | 0.1 $^{+ 0.2 }_{- 0.1 }$ |  |  |
| A$_V$ | 4.0 $^{+ 1.4 }_{- 1.0 }$ | 2.7 $^{+ 0.3 }_{- 0.3 }$ | 1.4 $^{+ 0.1 }_{- 0.1 }$ | (0.0, 10.0) |  |
| $\eta^c$ | 2.0 $^{+ 0.6 }_{- 0.6 }$ | 2.1 $^{+ 0.6 }_{- 0.8 }$ | 2.5 $^{+ 0.3 }_{- 0.5 }$ | (1, 3.0) |  |
| Umin$^d$ | 13.0 $^{+ 7.7 }_{- 7.3 }$ | 7.6 $^{+ 6.3 }_{- 4.0 }$ | 4.8 $^{+ 3.4 }_{- 2.4 }$ | (1, 25.0) |  |
| gamma$^e$ | 0.5 $^{+ 0.3 }_{- 0.3 }$ | 0.5 $^{+ 0.3 }_{- 0.3 }$ | 0.5 $^{+ 0.3 }_{- 0.3 }$ | (0.01, 0.99) |  |
| n$^f$ | 0.9 $^{+ 0.6 }_{- 0.4 }$ | 0.4 $^{+ 0.1 }_{- 0.1 }$ | \- | (0.1, 2.0) |  |
| qpah$^g$ | 2.3 $^{+ 1.1 }_{- 1.1 }$ | 3.3 $^{+ 0.5 }_{- 1.0 }$ | 3.0 $^{+ 0.7 }_{- 1.1 }$ | (0.5, 4.0) |  |
| Log$_{10}$ LIR$^h$ \[L$_{\odot}$\] | 12.6 | 12.4 | 12.1 |  |  |
| Gas mass \[M$_{\odot}$\] | 0.5-1.5 $\times 10^{11}$ | $4-9\times10^{10}$ |  |  |  |

: Stellar Population Properties of 3-mm continuum sources

Table notes: $^{a}$ Fitting priors are uniform with the range as defined in last column. $^{b}$ Redshift prior is a gaussian matching the redshift evolution at $z>4$ cumulative halo mass function as described in Section [2.4](#sec:sed) $^{c}$ Multiplicative factor producing extra attenuation for young stars $^{d}$ Starlight intensity on dust grains, related to dust temperature as T$_{dust}\propto U^{1/6}$ (cite: DraineLi2007) $^{e}$ Fraction of stars at Umin $^{f}$ Power-law slope of the dust extinction law (for (cite: Charlot2000)) $^{g}$ PAH mass fraction $^{h}$ Total infrared luminosity (8-1000$\mu$m) in units from integrating the median posterior spectrum in Figure [4](#sed).

Calculating redshift using the radio-to-submm spectral index method (using 850$\mu$m and the upper limit on 1.4GHz) implies a lower limit to the photometric redshift of $\sim$4.7 (cite: CarilliYun1999). We note that this is very similar to the massive dusty galaxy HDF850.1 which had a redshift 4.1 according to this relation (cite: Dunlop2004), and was later spectroscopically confirmed at z=5.2 (cite: Walter2012). The SED of $3MM$-1 is very similar to that of HDF850.1; scaling its best-fit SED to the 850$\mu$m and 3-mm fluxes of $3MM$-1 predicts its observed 3 GHz radio flux of 10$\mu$m (Figure [5](#fig:hdf850)).

The observed 3 GHz radio flux ($4\sigma$) is in excess of that expected from empirical SED templates for obscured star-forming galaxies (cite: daCunha2015) and recent calibrations of the redshift-dependent ratio of total infrared luminosity to rest-frame 1.4 GHz luminosity density (cite: Delhaize2017; Tisanic2019). For typical assumptions of the radio spectral slope $S_{\nu}\propto\nu^{-0.8}$ (dashed line in Figure [4](#sed)), the radio emission of $3MM$-1 is a factor of $\sim6\pm 1.5$ higher than expectations for star-formation, in excess of the commonly adopted $\times$3 threshold for AGN activity (cite: Daddi2009). No evidence for redshift evolution in the spectral slope, or dependence on sSFR or distance from the main sequence has been reported (cite: Magnelli2015).

The radio excess therefore indicates plausible evidence for presence of an AGN. We note that no X-ray counterpart exists within 5” (cite: Civano2016), although this is not surprising given the high-redshift of $3MM$-1. Given the possible presence of an AGN, it is worth noting that inferred parameters from SED fitting could be biased by AGN emission, in particular in the mid-infrared (cite: Leja2018). Therefore, we investigate any possible contamination using the empirical AGN-dominated template published by (cite: Kirkpatrick2015). We use their mid-infrared template based on galaxies with the largest mid-infrared luminosity contribution from AGN emission scaled to the 24$\mu$m flux of $3MM$-1  and subtract the predicted AGN contribution from the observed SED. This represents the maximum AGN contribution that could be accommodated by the data without violating the observed photometry. We then re-measure the SED fitted parameters. Subtracting this empirical AGN template reduces the SFR by $\sim$15%, well within the uncertainty, but does not change the inferred stellar mass significantly. We conclude that any AGN contribution does not significantly impact our SED-fitting results.

Finally, the 3-mm flux density enables an estimate of the molecular gas mass for $3MM$-1 following the calibration of sub-mm flux to gas mass (cite: Scoville2016). Exploring the range of the photometric redshift PDF, and typical assumptions about the dust emissivity, temperature, and dust-to-gas ratio, we find that $3MM$-1 likely has M$_{\rm{gas}}\sim0.5-1.5 \times 10^{11}$ M$_{\odot}$. This is independent evidence that the galaxy is massive, with a high inferred gas fraction ($\sim$60%).

## $3MM$-2

$3MM$-2 is optically faint, but detected in $K_{s,AB}=24.2$ and relatively bright in IRAC $\sim23$ mag, with red optical-to-IRAC colors. There is an apparent break between the $J_s$ and $H$-band, consistent with a Balmer/4000Å break at $z\sim3$. The source is undetected at $24-870$ micron, but with less extreme flux ratios ($S_{24}/S_{3mm}<3.5\times10^{-1}$, $S_{4.5}/S_{3mm}<3\times10^{-2}$) compared to $3MM$-1, indicating a lower redshift.

We follow the same procedure as before to fit the SED, finding a well-constrained photometric redshift of $z=3.3\pm0.2$ (99% probability between $2.7 < z < 3.7$), ruling out that this source is simply a highly obscured region in the nearby $z=0.95$ foreground galaxy to the north. Considering the CO emission line detection (consistent with redshifts 2.25, 3.33, and 4.41), we determine the line is likely CO($4-3$) at $z=3.329$, in agreement with the best-fit photometric redshift. Fixing the redshift to the spectroscopic redshift, the observations are best reproduced with a massive $10^{11.1}$M$_\odot$, star forming $SFR=250$ M$_\odot$/yr, highly obscured $A_V\sim2.7$ galaxy. Using the (cite: Kennicutt1998; Kennicutt2012) conversion from LIR to SFR yields $\sim375$ M$_{\odot}$ yr$^{-1}$. The derived gas mass using the CO(4-3) line flux (assuming the average CO excitation from (cite: Bothwell2013)) is in the range $\sim1-4\times10^{11}$ M$_{\odot}$, given the factor of four scatter in measured excitation for high-redshift dust obscured galaxies (cite: Narayanan2014). The 3 mm derived gas mass is $4-9\times10^{10}$ M$_{\odot}$. Both estimates indicate gas fractions in the range $30-70$%. The SED properties for $3MM$-2 are listed in Table [\[tab:sedfit\]](#tab:sedfit), the SED fit is shown in Figure [4](#sed), and posterior distributions for the parameters are presented in Figure [8](#fig:pdf2).

The best-fit power law index for the (cite: Charlot2000) dust model is $n=0.4\pm0.1$, flatter than the $n=0.7$ appropriate for typical nearby starburst galaxies. The flat spectral index means that the attenuation curve is “greyer” than a Calzetti attenuation law (cite: Chevallard2013) resulting in larger attenuation for the same amount of reddening $E(B-V)=0.3$. The assumed attenuation model can have a large impact on the derived stellar mass. If instead of a flexible attenuation model a classical Calzetti starburst law is assumed then the fits result in a factor $8^{+7.1}_{-3.9}$ lower stellar mass ($10^{10.2}$ M$_\odot$) and factor $2.2\pm0.7\times$ lower SFR (same answer if the infrared-to-mm constraints are also removed). The large difference in stellar mass is remarkable. The reason is that the steeper reddening curve of Calzetti reproduces the data with an intrinsically blue, young, low M/L ratio stellar population, driving the lower masses. The (cite: Charlot2000) model requires an older, redder, higher M/L population, while also implying larger attenuation at all wavelengths, including the near-infrared. We note that these results all assume energy balance and a parametric delayed$-\tau$ SFH. We explore the dependence on SFH by also fitting the SED with PROSPECTOR (cite: Leja2017), which is capable of fitting a non-parametric SFH in logarithmic bins of age (cite: Leja2019). These fits produce qualitatively similar results, with Calzetti yielding $\sim2\times$ lower SFR and stellar mass.

An independent estimate of mass can be derived by estimating the dynamical mass from the 630 km/s width of the CO emission line at 106.5 GHz (Figure [2](#fig:CO43)). Following the procedure used by (cite: Wang2013), we compute $V_{circ} = 0.75  FWHM(CO)/sin(i)$ and $M_{dyn}=1.16 \times 10^{5} V_{circ}^2 D$, where we note that inclination angle $i$ and disk diameter D (in kpc) are unknown. Adopting the mean size $R_e=3^{+1.8}_{-0.9}$ kpc expected for massive 10$^{11}$M$_\odot$ star forming galaxies at $z=3$ (cite: vanderWel2014), we find M$_{dyn}sin^2(i) = 1.5^{+1.0}_{-0.5}\times10^{11}$M$_\odot$. Assuming a disk geometry with an inclination angle of $i=45^{\circ}$ would imply M$_{dyn}\sim3\times10^{11}$M$_\odot$. Overall, the high dynamical mass appears to agree better with the high stellar mass inferred from (cite: Charlot2000) dust model with flat $n$ than with the Calzetti-based stellar mass, but the large uncertainties in dynamical and stellar mass prevents firmer conclusions.

## Redshifts

Given the close $r\sim15''$ separation on the sky of the two ALMA sources we consider the possibility that they are at the same redshift. The redshift of $3MM$-2 ($z=3.329$) is strongly disfavored for $3MM$-1 (1% probability $z<3.3$). Alternatively, our identification of $z_{CO(4-3)}=3.329$ for $3MM$-2 is erroneous and the galaxy is at $z_{CO(5-4)}=4.41$, more consistent with $3MM$-1. This is unlikely based on the SED fit of $3MM$-2, which is well constrained by the presence of both a Lyman Break and Balmer break. We find no significant emission line ($SNR>3$) in the spectrum of $3MM$-1 which suggests it is unlikely at $3.20 < z < 3.35$ and $3.72 < z < 3.90$. A Gaussian fit to the spectrum of $3MM$-1 at fixed $106.5$ GHz indicates $SNR=0.8$, providing no evidence for $3MM$-1 and $3MM$-2 occupying the same dark matter halo (DMH). Additionally, we scan the nearby velocity space in case both galaxies are in a large scale structure filament, but we find no emission line $SNR>2$ within $\Delta v=\pm2000$km/s. Finally, we consider the odds of finding two 3-mm sources within $r\sim15''$ on the sky. Using the 3-mm number counts of (cite: Zavala2018_3mm), we simulate uniformly random distributions of two sources which indicates an $\sim10$% chance of finding a $75\mu$Jy source within $r<15''$ of a $155\mu$Jy source. These odds are low, but not negligible. Overall, there is no conclusive evidence that the two sources are at the same redshift. We therefore proceed and take the $z_{phot}=5.5\pm1.1$ for $3MM$-1 at face value.

# Discussion

## Implications from full optical-to-mm spectrum SED fitting

We consider the SED fitting analysis using a stellar population model with self-consistent dust absorption and emission under the assumption of energy balance and constrained by high quality optical-to-millimeter observations. In the case of the $z\sim5.5$ source $3MM$-1, which lacks strong detections at any wavelength other than 3 mm, it is remarkable that the Bayesian posterior probability distributions for key parameters such as redshift, stellar mass, dust attenuation and star-formation rate are as constrained as they are (see Table [\[tab:sedfit\]](#tab:sedfit) and Figure [7](#fig:pdf1)). Closer inspection indicates that the results are mostly driven by the combination of the high SNR ALMA measurement with deep photometric limits in the short wavelength infrared (*Spitzer*/MIPS and *Herschel*/PACS $100-160\mu$m), which demand that the dust emission peak is highly redshifted ($z>4$) and the SFR is high. It is likely that the uncertainties on the stellar mass and other stellar population parameters are underestimated, because of the tight prior imposed by the parametric SFH (cite: Carnall2019; Leja2019). We note that our choice of a rising SFH produces a relatively conservative (lower) estimate of stellar mass compared to constant or declining SFH.

There is accumulating evidence that the attenuation law in very dusty galaxies can be flatter than Calzetti (cite: Salmon2016; Leja2017; Salim2018), possibly caused by a more uniformly mixed geometry of both old and young stars with dust (cite: Narayanan2018). The flat inferred attenuation law $\lambda^{-0.4}$ for $3MM$-2 is not surprising in that regard. It is notable and sobering however that modeling the optical-to-millimeter with a classical Calzetti starburst law instead (keeping everything else the same) results in significantly lower SFR and stellar mass ($10^{10.2}$), in apparent tension with the high dynamical mass ($1.5-3\times10^{11}$M$_\odot$). Detailed analyses of ULIRGs at $z\sim2$ with photometric constraints on far-infrared dust emission (cite: LoFaro2017) also found that stellar masses inferred using a Calzetti law are systematically lower because of the smaller amount of reddening at near-infrared wavelengths. Clearly, caution should be exercised when applying a single locally-calibrated attenuation law at high redshift. Overall, the results highlight the need for deep (sub-)mm measurements to determine bolometric luminosities and provide high-redshift empirical constraints on the dust law/energy balance (cite: Hodge2016).

For the remainder of the paper we emphasize discussing the implications of the ALMA-only source $3MM$-1, which likely represents a population that is absent from all current optical-IRAC selected galaxy studies, is below the nominal detection threshold of deep single-dish sub-mm surveys, and therefore deserves more scrutiny.

## Number counts

A recent unbiased ALMA 3 mm archival search for continuum sources over 130 independent pointings (cite: Zavala2018_3mm) enabled the first 3 mm number counts. For archival searches, however, detection limits and effective search area are necessarily very inhomogeneous due to the strong variation of the ALMA primary beam response, complicating a straightforward comparison of results. Restricting the comparison to $3MM$-1, we use their best-fit powerlaw to the cumulative number counts, which considers effective selection area and incompleteness, predicting one source brighter than S$_{3\textrm{mm}}>155\mu$Jy per $16^{+16}_{-8}$ arcmin$^2$. This is consistent with our finding one source in our effective survey area of 8 arcmin$^2$ (see $\S$[2.2](#sec:almadet)).

We note that given the estimated stellar mass of $\sim 10^{10.8}$M$_\odot$ at z=5.5, we expect $3MM$-1 to occupy a massive DMH ($\sim 10^{12}$M$_\odot$) and to be strongly clustered. While our results are dominated by Poissonian uncertainties, this may imply that the uncertainties in published number counts are underestimates. Clustering may affect source counts from studies over very small areas such as the ASPECS 4.6 arcmin$^{2}$ survey in the HUDF (cite: GonzalezLopez2019), and even the counts in the multiple pointings of (cite: Zavala2018_3mm), as these observations were generally targeting moderately-sized deep fields (COSMOS, CDFS, UDS). Clustering effects may be exacerbated by the fact that dust obscuration preferentially occurs in massive galaxies (cite: Whitaker2017). We note that our results are unlikely to be biased by the original primary targets, which were all at low redshift ($z\sim1.5$). Clearly, larger blind surveys are needed to constrain number densities at the bright end.

## Unbiased ALMA 3 mm selection of high-redshift galaxies

Simulations of dust obscured galaxies in the early universe predict $3$ mm continuum selection optimizes the sensitivity to DSFGs at redshift $z>4$ (cite: Casey2018b). Current evidence is still mixed: continuum detected faint galaxies in the small ultradeep ALMA ASPECS field are at average $\bar{z}=2.3$ (cite: GonzalezLopez2019), while limited ground-based spectroscopic evidence for sources found in wider-area archival data indicates $\bar{z}=3.1$ (cite: Zavala2018_3mm). Note, however, that the luminosity of the sources and volume covered could impact the redshift selection function (cite: Strandet2016; Brisbin2017), and follow up ground-based spectroscopy in the optical and near-IR is possibly biased against highly obscured sources at $z>3$, due to the faintness of Lyman-alpha, nebular optical lines and lack of wavelength coverage $>2.4$ micron. Overall, the redshifts of the two continuum sources in this study, a probable $z_{CO}=3.329$ (based on a single CO line and congruous $z_{phot}=3.25\pm0.15$) and $z_{phot}=5.5\pm1.1$ ($\bar{z}=4.4$), are consistent with 3 mm favoring higher redshifts than the $\bar{z}=2.2$ typical for $870\mu$m-selected galaxies (cite: Simpson2014).

A challenge in determining the selection function is the difficulty in identifying counterparts and determining redshifts. Neither of our two 3 mm sources had counterparts in previous deep optical-to-radio selected catalogs, raising some concern for analyses where this is a critical step (e.g., photometric redshifts or spectroscopic follow up in optical/NIR). This is particularly problematic for single-dish sub-mm observations, due to the large beam size, but here we find it challenging even with the high spatial resolution $FWHM=2''$ and accurate astrometry offered by ALMA. In the case of $3MM$-2 the source is very close to a bright foreground galaxy (1.3” to the North), which was initially mistaken as the counterpart. The optical/NIR faintness and low resolution of the Spitzer/IRAC data caused it to be missing or blended in existing multiwavelength catalogs. In the case of $3MM$-1 the combination of high redshift and high obscuration resulted in it being extremely faint and undetected at all optical-infrared wavelengths. It is therefore possible that the identification of the highest redshift galaxies in existing (sub-)mm selected samples is still incomplete. In addition, obtaining spectroscopic redshifts in the optical/NIR is unfeasible for the faintest sources. ALMA spectral scans targeting CO and \[CII\] are likely the only recourse until other facilities (e.g., JWST/NIRSpec, LMT Redshift Search Receiver) become available.

![](fig6.pdf)

## Comparison to other “dark" galaxies

The observed SED of $3MM$-1 is different from that of other optical/near-IR/IRAC-faint populations.

The ALESS survey identified 9 IRAC-faint SMGs to 1 magnitude brighter IRAC limits (cite: Simpson2014), but these sources were much brighter in the far-infrared (peaking at $250-350$ micron to $\sim10$mJy), with a significantly bluer dust peak consistent with $z\sim2-3$. Such an infrared SED is ruled out by our observations. $3MM$-1 is fainter at all wavelengths than the so-called H/K$-$dropout galaxies (cite: Wang2016; Schreiber2017; Caputi2012), which are generally selected on $H-4.5$ color, $>10\times$ brighter in IRAC, and estimated to be at lower redshift $\bar{z}=3.7$.

More recently, SCUBA surveys have been carried out to unprecedented depth over CANDELS fields (cite: Koprowski2017; Cowie2017; Cowie2018; zavala2017). Such surveys are deep enough to discover $S_{870}=2-4$ mJy objects like $3MM$-1 at $z>4$. Indeed, the deepest SCUBA surveys have reported sub-mm selected objects that are likely at $z>4$ and that are either extremely faint at optical-IRAC and MIPS wavelengths (cite: Cowie2018) or likely initially misidentified and determined to be at high redshift based on the long wavelength IR SED (cite: Koprowski2016). With optical-IRAC magnitudes in the range $29-25$ AB, no MIPS detection, and only a marginal 3 Ghz radio detection, $3MM$-1-like objects would have likely defied secure identification, and its probable $z=5-6$ redshift could have only been determined from the IR SED.

More similar are recently reported ALMA 1.2 mm selected sources from the ASAGAO survey (cite: Yamaguchi2019) in GOODS-S. These sources also lack obvious counterparts at shorter wavelength, show extremely small $S_{4.5}/S_{1.2mm}$ and $S_{24}/S_{850}$ flux ratios (indicative of high redshift), but are generally fainter $S_{1.2mm}=0.44-0.8$ mJy than $3MM$-1 ($S_{1.2mm}\sim2.3$). Additional candidates that lack deep multi-wavelength ancillary data may exist outside legacy fields (cite: Wardlow2018).

## Contribution to CSFRD

The fact that $3MM$-1 was identified in a survey of such small area suggests that similar galaxies are common in the early Universe. Using the effective area of 8 arcmin$^2$ as derived in §[2.2](#sec:almadet), our finding implies a source density of $0.13^{+0.30}_{-0.10}$ arcmin$^{-2}$, an order of magnitude higher than the rare sub-mm selected starbursts at $z>4$ ($0.01-0.02$ arcmin$^{-2}$; e.g. (cite: Danielson2017; Marrone2018)). If our results are representative, galaxies like $3MM$-1 could represent the “iceberg under the tip" of the known extreme dust-obscured star-forming galaxies in the early Universe.

To estimate the space densities and contribution to the CSFRD requires estimating a selection volume, which is difficult as we do not know the expected properties or true abundance of DSFGs at $z>4$. Instead, we derive a simple estimate based on the derived properties of $3MM$-1. Encouraged by the strong redshift constraints from the long wavelength photometry, we set the lower bound of the selection volume to the lower 10th percentile redshift probability ($z>4.1$). The upper bound is chosen to be the redshift beyond which we expect only 0.1 halos of sufficient mass based on the cumulative halo mass function. Using the halo mass function calculator HMF published by (cite: Murray2013) and assuming the halo mass function of (cite: Behroozi2013) and a high $30\%$ baryon conversion into stars and (converting M$^*$=$10^{10.8}$M$_\odot$ into a conservative M$_{halo}$ $\sim10^{12}$M$_\odot$) we compute this upper bound to be $z=5.7$.

Using this selection volume we determine a space density of $2.9^{+6.5}_{-2.4}\times10^{-5}$ Mpc$^{-3}$. We find that the contribution to the CSFRD by $3MM$-1 is $\rho_{\small \textrm{SFR}}$ $0.9^{+2.0}_{-0.7}\times10^{-2}$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ (converted to a (cite: Chabrier2003) IMF for comparison with literature measurements). Assuming instead the cumulative space density of massive halos ($>$10$^{12}$) at $z\sim5$ using the (cite: Behroozi2013) halo function, produces a very similar $\rho_{\small\textrm{SFR}}$ $0.6\times10^{-2}$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ for our derived SFR.

With only a single object, the Poissonian uncertainty is large and dominant (cite: Gehrels1986). Cosmic variance is only on the order of $\sim$30% based on the calculator by (cite: Trenti2008), and is therefore not further included. No completeness corrections are applied, because the true distribution is unknown. Figure [6](#sfrd) shows comparisons to various results at $0<z<10$ from literature that report dust-uncorrected UV-derived SFR and the dust-obscured SFR (IR to millimeter derived).

The contribution of $3MM$-1 is higher than inferred for the two near-infrared dark ALMA 1.2 mm sources in (cite: Yamaguchi2019), mostly owing to their smaller implied total infrared luminosities. This study does not report formal uncertainties or derive redshifts, which prohibits a more quantitative comparison. Bright SMGs beyond $z>4$ contribute $\sim1\times10^{-3}$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ (cite: Swinbank2014; Michalowski2017), about an order or magnitude lower than our best estimate. Results from fainter SMGs found in the deepest SCUBA surveys, with luminosities similar to $3MM$-1 (cite: Koprowski2017; Cowie2018) show a declining contribution at $2 < z < 5$, consistent with our estimates.

Interestingly, if $3MM$-1 is representative, a population with similar properties could contribute as much to the CSFRD as all known ultraviolet-selected galaxies at similar redshifts combined. This could even imply that dust-obscured star-formation continues to dominate the cosmic star-formation history beyond $z>4$ where current infrared-to-mm measurements are incomplete.

## Contribution to Stellar mass density

The high stellar mass $10^{10.8}$ M$_\odot$ and large space density $\sim3\times10^{-5}$ Mpc$^{-3}$ of $3MM$-1 imply a considerable cosmic stellar mass density (CSMD) in similar objects at $z\sim5$: $\rho^*=1.9^{+4.4}_{-1.5} \times 10^6$ M$_\odot$Mpc$^{-3}$, higher than reported for bright (S$_{850}> 4$ mJy) sub-mm galaxies (cite: Michalowski2017). Comparing to the estimate of the CSMD based on HST-selected galaxies $\rho^*(z=5)=6.3\times 10^6$M$_\odot$Mpc$^{-3}$ (cite: Song2016), suggests that they could contribute a significant fraction ($22^{+25}_{-16}$%) to the total and perhaps even dominate the high-mass end. The high-mass end of the galaxy stellar mass function at high redshift $z>4$ is still uncertain and susceptible to biases. Current estimates for the number density of $\sim10^{10.8}$ M$_\odot$ galaxies at $z\sim5$ are $1-5\times10^{-5}$ Mpc$^{-3}$dex$^{-1}$ (cite: Duncan2014; Grazian2015; Song2016; Davidzon2017; Stefanon2017_900nm), comparable to the space density derived for our ALMA-only galaxy $3MM$-1. Given that optical-IRAC dark galaxies are missing from these previous studies, it is therefore possible that about half the stellar mass density in high-mass galaxies at $z\sim5$ remains unaccounted for.

## Implications for the formation of massive galaxies

Bright sub-millimeter-selected galaxies at $z>3$ with SFR$\gtrsim$1000 M$_{\odot}$yr$^{-1}$ are often hypothesized as progenitors of massive $z\sim2$ quiescent galaxies (cite: Toft2014; Spilker2018sci). More recently, massive quiescent galaxies have been spectroscopically confirmed at $3<z<4$ (cite: Glazebrook2017; Schreiber2018qg), but finding their progenitors at even earlier times is challenging. Generally, UV-selected galaxies at $z>4$ are presumed not abundant, massive, and star forming enough to produce the population of the earliest known massive quiescent galaxies with N$\sim3-5\times10^{-5}$ Mpc$^{-3}$ and Log (M/M$_\odot)\gtrsim10.6$ (cite: Straatman2014). Bright ($> 4$ mJy) sub-millimeter galaxies are a possible avenue, but it is difficult to establish a conclusive connection. Estimated SMG number densities at $z>4$ are low and uncertain $\sim0.1-3\times10^{-6}$ Mpc$^{-3}$ (cite: Ivison2016; Michalowski2017; Jin2018). While their high SFRs indicate they will rapidly form massive galaxies, the modest inferred gas masses indicate gas depletion timescales on the order of $10-100$ Myr (cite: Aravena2016a; Spilker2018sci), and large duty cycle corrections are needed to make up for the low number densities.

The inferred space densities and stellar mass of $3MM$-1 on the other hand are already as large as those reported for the population of early quiescent galaxies at $3<z<4$ (cite: Straatman2014; Nayyeri2014). The large $\sim10^{11}M_\odot$ gas mass and modest SFR indicates much longer depletion timescales ($\sim200-500$ Myr), half the age of the Universe at this epoch, and implies a $\sim50-100$% duty cycle for our adopted $4\lesssim z \lesssim6$ selection window. $3MM$-1 could therefore represent a more gradual path for massive galaxy growth compared to a rapid and bursty formation as has been found in some bright merger-induced SMGs (cite: Pavesi2018; Marrone2018). Overall, our results provide evidence for the existence of a sustained growth mode for massive galaxies in the early Universe.

Finally, the large systematic difference in SFR and stellar mass in particular depending on the assumed attenuation model for $3MM$-2 suggests exercising caution when relating progenitors and descendants galaxies. Often such links are determined based on the capability of a progenitor population to produce adequate numbers of sufficiently massive galaxies at later times (cite: Straatman2014; Toft2014; Williams2014; Williams2015), or by the assumption that the rank-order on stellar mass can be reliably determined (cite: Brammer2011; Behroozi2013cnd; Leja2013). Such determinations could be more uncertain than has been accounted for if the derived stellar masses of individual galaxies are off by factors of $\sim8$ (see §3.2). This is a particular concern at high redshift $z>3$, where very few galaxies have high enough SNR (sub-)mm observations for meaningful constraints on the dust attenuation model. These results are obviously based on only a single galaxy and larger samples with full optical-to-mm photometry are needed to determine the scatter in stellar mass.

## Future ALMA and JWST observations

The dark nature of the $3MM$-1, non-detection in very deep stacked optical and near-IR data and the faint IRAC fluxes, suggests a prominent population of DSFGs at $z>4$. The high inferred redshift may point to the efficacy of blind surveys at $2-3$ mm to find the earliest dusty star forming galaxies (cite: Bethermin2015b; Casey2018b). These galaxies are below the classical detection limit ($>4$ mJy) of bright galaxies found in single-dish sub-mm surveys. Deep 2 mm single-dish and wider $1-3$ mm ALMA (sub)-mm surveys are only just starting to push into this territory at very high redshift (cite: Magnelli2019; Yamaguchi2019). Until the launch of the *James Webb Space Telescope* (*JWST*), ALMA alone can find and study these galaxies.

Wide-area unbiased ALMA surveys covering 100’s of arcmin$^2$ are necessary to further constrain their prominence in the early universe. Such surveys are feasible at $2-3$ mm with ALMA because of the relatively large size of the primary ALMA beam and the exquisite sensitivity to high redshift star forming galaxies even in short integration times (cite: Casey2019). To date, none of the ALMA-only galaxies found has been spectroscopically confirmed, but spectral line scans for CO and in particular \[CII\] are efficient and feasible with ALMA. Future surveys with *JWST* will enable systematic studies of large samples of faint SMG galaxies. Large legacy surveys such as the *JWST* Advanced Deep Extragalactic Survey (JADES) will likely characterize $\sim15-30$ galaxies similar to $3MM$-1 (based on expected number densities from this work and (cite: Zavala2018_3mm), and observations described in (cite: Williams2018)). *JWST* will have the capability to measure stellar population properties and redshifts, and in combination with ALMA far-infrared constraints, will enable a detailed investigation into the star-formation, dust, and stellar population properties of massive galaxies in the early Universe.

# Acknowledgments

We are grateful to James Simpson for making part of S2COSMOS available for our analysis in advance of publication. We thank Jorge Zavala, Peter Behroozi and Pieter van Dokkum for helpful discussions. C.C.W. acknowledges support from the National Science Foundation Astronomy and Astrophysics Fellowship grant AST-1701546. J.L. is supported by an NSF Astronomy and Astrophysics Postdoctoral Fellowship under award AST-1701487. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2018.1.01739.S, ADS/JAO.ALMA #2015.1.00853.S, ADS/JAO.ALMA #2015.1.00861.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

Here we present supplemental observational details for $3MM$-1 and $3MM$-2. In Table [\[tab:phot\]](#tab:phot), we present the deblended photometry (measurements and 1$\sigma$ uncertainties) based on the ALMA priors for the two 3-mm sources that are used in the SED fitting analysis presented in Section [2.4](#sec:sed). In Figures [7](#fig:pdf1) and [8](#fig:pdf2) we present the posterior probability distributions for the galaxy properties of both sources measured using the Bayesian SED fitting with BAGPIPES.

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Band | $3MM$-1 flux density | RMS | $3MM$-2 flux density | RMS |
|  | \[$\mu$Jy\] |  | \[$\mu$Jy\] |  |
| SUBARU B | \[ -1.3E-02 \] | 7.8E-03 | – | – |
| HSC g | \[ 3.6E-03 \] | 1.5E-02 | \[ 2.3E-02 \] | 1.1E-02 |
| SUBARU V | \[ -7.6E-03 \] | 1.8E-02 | – | – |
| HSC r | \[ -1.2E-02 \] | 1.4E-02 | 9.3E-02 | 9.7E-03 |
| SUBARU rp | \[ 1.2E-03 \] | 1.7E-02 | – | – |
| SUBARU ip | \[ 2.0E-03 \] | 2.6E-02 | – | – |
| HSC i | \[ -1.0E-02 \] | 2.1E-02 | 1.2E-01 | 1.5E-02 |
| HSC z | \[ 1.2E-02 \] | 3.0E-02 | 1.3E-01 | 2.4E-02 |
| SUBARU zp | \[ -1.5E-01 \] | 6.5E-02 | – | – |
| HSC Y | \[ 2.2E-02 \] | 7.4E-02 | \[ 4.9E-02 \] | 5.8E-02 |
| UltraVISTA Y | \[ 9.7E-03 \] | 8.9E-02 | \[ 1.6E-01 \] | 8.2E-02 |
| UltraVISTA J | \[ -1.1E-01 \] | 1.0E-01 | \[ 2.0E-01 \] | 8.9E-02 |
| UltraVISTA H | \[ -5.9E-02 \] | 1.3E-01 | 6.3E-01 | 1.1E-01 |
| UltraVISTA Ks | \[ 1.2E-01 \] | 8.8E-02 | 8.4E-01 | 8.7E-02 |
| *Spitzer/IRAC 3.6$\mu$m* | \[ 3.2E-01 \] | 1.2E-01 | 1.7E+00 | 9.2E-02 |
| *Spitzer/IRAC 4.5$\mu$m* | \[ 3.2E-01 \] | 1.3E-01 | 3.0E+00 | 9.9E-02 |
| *Spitzer/IRAC 5.8$\mu$m* | \[ 5.2E+00 \] | 3.3E+00 | 8.8E+00 | 2.2E+00 |
| *Spitzer/IRAC 8$\mu$m* | \[ 6.0E+00 \] | 4.1E+00 | \[ 7.7E+00 \] | 2.9E+00 |
| *Spiter/MIPS 24$\mu$m* | \[ 1.1E+01 \] | 1.5E+01 | \[ 2.6E+01 \] | 1.5E+01 |
| *Herschel/PACS 100$\mu$m* | \[ 7.1E+02 \] | 1.4E+03 | \[ 1.5E+02 \] | 1.4E+03 |
| *Herschel/PACS 160$\mu$m* | \[ -2.4E+03 \] | 3.2E+03 | \[ -1.9E+03 \] | 3.2E+03 |
| *Herschel/SPIRE 250$\mu$m* | \[ 3.7E+03 \] | 3.9E+03 | \[ 1.0E+03 \] | 3.9E+03 |
| *Herschel/SPIRE 350$\mu$m* | \[ 4.3E+03 \] | 4.9E+03 | \[ -5.0E+02 \] | 4.9E+03 |
| *Herschel/SPIRE 500$\mu$m* | \[ 5.5E+03 \] | 5.8E+03 | \[ 4.4E+03 \] | 5.8E+03 |
| SCUBA2 850$\mu$m | 3.5E+03 | 1.1E+03 | \[ 4.0E+02 \] | 1.1E+03 |
| ALMA 3mm | 1.6E+02 | 2.2E+01 | 7.5E+01 | 1.0E+01 |
| VLA 3 GHz | 1.0E+01 | 2.4E+00 | \[ 3.9E+00 \] | 2.4E+00 |
| VLA 1.4 GHz | \[ 1.7E+01 \] | 1.7E+01 | \[ 4.0E+01 \] | 1.7E+01 |

: ALMA prior-based deblended photometry

Table notes: Subaru optical photometry for $3MM$-2 are not measured owing to cosmetic defects in the mosaics that cross the location of the source. Photometric upper limits as indicated by downward arrows in Figure [4](#sed) are at the RMS values of photometric points in this table where S/N$<$1. Non-significant photometric points (with SNR$<3$) are indicated with brackets.

![](fig7.png)

![](fig8.png)

natexlab

(ref: Aihara2018a) Aihara, H., Arimoto, N., Armstrong, R., et al. 2018a, PASJ, 70, S4, doi: [`10.1093/pasj/psx066`](http://doi.org/10.1093/pasj/psx066)

(ref: Aihara2018b) Aihara, H., Armstrong, R., Bickerton, S., et al. 2018b, PASJ, 70, S8, doi: [`10.1093/pasj/psx081`](http://doi.org/10.1093/pasj/psx081)

(ref: Aravena2016a) Aravena, M., Decarli, R., Walter, F., et al. 2016, ApJ, 833, 68, doi: [`10.3847/1538-4357/833/1/68`](http://doi.org/10.3847/1538-4357/833/1/68)

(ref: Aretxaga2011) Aretxaga, I., Wilson, G. W., Aguilar, E., et al. 2011, MNRAS, 415, 3831, doi: [`10.1111/j.1365-2966.2011.18989.x`](http://doi.org/10.1111/j.1365-2966.2011.18989.x)

(ref: Behroozi2013cnd) Behroozi, P. S., Marchesini, D., Wechsler, R. H., et al. 2013a, ApJ, 777, L10, doi: [`10.1088/2041-8205/777/1/L10`](http://doi.org/10.1088/2041-8205/777/1/L10)

(ref: Behroozi2013) Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013b, ApJ, 770, 57, doi: [`10.1088/0004-637X/770/1/57`](http://doi.org/10.1088/0004-637X/770/1/57)

(ref: Bethermin2015b) Béthermin, M., De Breuck, C., Sargent, M., & Daddi, E. 2015, A&A, 576, L9, doi: [`10.1051/0004-6361/201525718`](http://doi.org/10.1051/0004-6361/201525718)

(ref: Bezanson2019) Bezanson, R., Spilker, J., Williams, C. C., et al. 2019, ApJL, 873, L19, doi: [`10.3847/2041-8213/ab0c9c`](http://doi.org/10.3847/2041-8213/ab0c9c)

(ref: Bothwell2013) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047, doi: [`10.1093/mnras/sts562`](http://doi.org/10.1093/mnras/sts562)

(ref: Bouwens2016LF) Bouwens, R. J., Oesch, P. A., Labbé, I., et al. 2016, ApJ, 830, 67, doi: [`10.3847/0004-637X/830/2/67`](http://doi.org/10.3847/0004-637X/830/2/67)

(ref: Brammer2011) Brammer, G. B., Whitaker, K. E., van Dokkum, P. G., et al. 2011, ApJ, 739, 24, doi: [`10.1088/0004-637X/739/1/24`](http://doi.org/10.1088/0004-637X/739/1/24)

(ref: Brisbin2017) Brisbin, D., Miettinen, O., Aravena, M., et al. 2017, A&A, 608, A15, doi: [`10.1051/0004-6361/201730558`](http://doi.org/10.1051/0004-6361/201730558)

(ref: Bruzual2003) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Byler2017) Byler, N., Dalcanton, J. J., Conroy, C., & Johnson, B. D. 2017, ApJ, 840, 44, doi: [`10.3847/1538-4357/aa6c66`](http://doi.org/10.3847/1538-4357/aa6c66)

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Caputi2012) Caputi, K. I., Dunlop, J. S., McLure, R. J., et al. 2012, ApJL, 750, L20, doi: [`10.1088/2041-8205/750/1/L20`](http://doi.org/10.1088/2041-8205/750/1/L20)

(ref: CarilliYun1999) Carilli, C. L., & Yun, M. S. 1999, ApJL, 513, L13, doi: [`10.1086/311909`](http://doi.org/10.1086/311909)

(ref: Carnall2019) Carnall, A. C., Leja, J., Johnson, B. D., et al. 2019, ApJ, 873, 44, doi: [`10.3847/1538-4357/ab04a2`](http://doi.org/10.3847/1538-4357/ab04a2)

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: Casey2018b) Casey, C. M., Hodge, J., Zavala, J. A., et al. 2018, ApJ, 862, 78, doi: [`10.3847/1538-4357/aacd11`](http://doi.org/10.3847/1538-4357/aacd11)

(ref: Casey2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Casey2019) Casey, C. M., Capak, P., Staguhn, J., et al. 2019, arXiv e-prints. [`https://arxiv.org/abs/1903.05634`](https://arxiv.org/abs/1903.05634)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Charlot2000) Charlot, S., & Fall, M. 2000, ApJ, 539, 718, doi: [`10.1086/309250`](http://doi.org/10.1086/309250)

(ref: Chevallard2013) Chevallard, J., Charlot, S., Wandelt, B., & Wild, V. 2013, MNRAS, 432, 2061, doi: [`10.1093/mnras/stt523`](http://doi.org/10.1093/mnras/stt523)

(ref: Civano2016) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62, doi: [`10.3847/0004-637X/819/1/62`](http://doi.org/10.3847/0004-637X/819/1/62)

(ref: Cooray2014) Cooray, A., Calanog, J., Wardlow, J. L., et al. 2014, ApJ, 790, 40, doi: [`10.1088/0004-637X/790/1/40`](http://doi.org/10.1088/0004-637X/790/1/40)

(ref: Cowie2017) Cowie, L. L., Barger, A. J., Hsu, L.-Y., et al. 2017, The Astrophysical Journal, 837, 139, doi: [`10.3847/1538-4357/aa60bb`](http://doi.org/10.3847/1538-4357/aa60bb)

(ref: Cowie2018) Cowie, L. L., González-López, J., Barger, A. J., et al. 2018, ApJ, 865, 106, doi: [`10.3847/1538-4357/aadc63`](http://doi.org/10.3847/1538-4357/aadc63)

(ref: daCunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: Daddi2009) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, ApJ, 694, 1517, doi: [`10.1088/0004-637X/694/2/1517`](http://doi.org/10.1088/0004-637X/694/2/1517)

(ref: Danielson2017) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2017, ApJ, 840, 78, doi: [`10.3847/1538-4357/aa6caf`](http://doi.org/10.3847/1538-4357/aa6caf)

(ref: Davidzon2017) Davidzon, I., Ilbert, O., Laigle, C., et al. 2017, A&A, 605, A70, doi: [`10.1051/0004-6361/201730419`](http://doi.org/10.1051/0004-6361/201730419)

(ref: Delhaize2017) Delhaize, J., Smolčić, V., Delvecchio, I., et al. 2017, A&A, 602, A4, doi: [`10.1051/0004-6361/201629430`](http://doi.org/10.1051/0004-6361/201629430)

(ref: DraineLi2007) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: Duncan2014) Duncan, K., Conselice, C. J., Mortlock, A., et al. 2014, MNRAS, 444, 2960, doi: [`10.1093/mnras/stu1622`](http://doi.org/10.1093/mnras/stu1622)

(ref: Dunlop2004) Dunlop, J. S., McLure, R. J., Yamada, T., et al. 2004, MNRAS, 350, 769, doi: [`10.1111/j.1365-2966.2004.07700.x`](http://doi.org/10.1111/j.1365-2966.2004.07700.x)

(ref: Dunlop2017) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: Ferland2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385. [`https://arxiv.org/abs/1705.10877`](https://arxiv.org/abs/1705.10877)

(ref: Finkelstein2015) Finkelstein, S. L., Ryan, Jr., R. E., Papovich, C., et al. 2015, ApJ, 810, 71, doi: [`10.1088/0004-637X/810/1/71`](http://doi.org/10.1088/0004-637X/810/1/71)

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: Geach2017) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789, doi: [`10.1093/mnras/stw2721`](http://doi.org/10.1093/mnras/stw2721)

(ref: Gehrels1986) Gehrels, N. 1986, ApJ, 303, 336, doi: [`10.1086/164079`](http://doi.org/10.1086/164079)

(ref: Glazebrook2017) Glazebrook, K., Schreiber, C., Labbé, I., et al. 2017, Nature, 544, 71, doi: [`10.1038/nature21680`](http://doi.org/10.1038/nature21680)

(ref: GonzalezLopez2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, arXiv e-prints, arXiv:1903.09161. [`https://arxiv.org/abs/1903.09161`](https://arxiv.org/abs/1903.09161)

(ref: Grazian2015) Grazian, A., Fontana, A., Santini, P., et al. 2015, A&A, 575, A96, doi: [`10.1051/0004-6361/201424750`](http://doi.org/10.1051/0004-6361/201424750)

(ref: Hatsukade2018) Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ, 70, 105, doi: [`10.1093/pasj/psy104`](http://doi.org/10.1093/pasj/psy104)

(ref: Hodge2016) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Hurley2017) Hurley, P. D., Oliver, S., Betancourt, M., et al. 2017, MNRAS, 464, 885, doi: [`10.1093/mnras/stw2375`](http://doi.org/10.1093/mnras/stw2375)

(ref: Ivison2016) Ivison, R. J., Lewis, A. J. R., Weiss, A., et al. 2016, ApJ, 832, 78, doi: [`10.3847/0004-637X/832/1/78`](http://doi.org/10.3847/0004-637X/832/1/78)

(ref: Jin2018) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56, doi: [`10.3847/1538-4357/aad4af`](http://doi.org/10.3847/1538-4357/aad4af)

(ref: Kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Kennicutt1998) Kennicutt, Jr., R. C. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Kirkpatrick2015) Kirkpatrick, A., Pope, A., Sajina, A., et al. 2015, ApJ, 814, 9, doi: [`10.1088/0004-637X/814/1/9`](http://doi.org/10.1088/0004-637X/814/1/9)

(ref: Koekemoer2007) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196, doi: [`10.1086/520086`](http://doi.org/10.1086/520086)

(ref: Koprowski2017) Koprowski, M. P., Dunlop, J. S., Michałowski, M. J., et al. 2017, MNRAS, 471, 4155, doi: [`10.1093/mnras/stx1843`](http://doi.org/10.1093/mnras/stx1843)

(ref: Koprowski2016) —. 2016, MNRAS, 458, 4321, doi: [`10.1093/mnras/stw564`](http://doi.org/10.1093/mnras/stw564)

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Labbe2013) Labbé, I., Oesch, P. A., Bouwens, R. J., et al. 2013, ApJL, 777, L19, doi: [`10.1088/2041-8205/777/2/L19`](http://doi.org/10.1088/2041-8205/777/2/L19)

(ref: Labbe2015) Labbé, I., Oesch, P. A., Illingworth, G. D., et al. 2015, ApJS, 221, 23, doi: [`10.1088/0067-0049/221/2/23`](http://doi.org/10.1088/0067-0049/221/2/23)

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24, doi: [`10.3847/0067-0049/224/2/24`](http://doi.org/10.3847/0067-0049/224/2/24)

(ref: LeFloch2009) Le Floc’h, E., Aussel, H., Ilbert, O., et al. 2009, ApJ, 703, 222, doi: [`10.1088/0004-637X/703/1/222`](http://doi.org/10.1088/0004-637X/703/1/222)

(ref: Leja2019) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3, doi: [`10.3847/1538-4357/ab133c`](http://doi.org/10.3847/1538-4357/ab133c)

(ref: Leja2018) Leja, J., Johnson, B. D., Conroy, C., & van Dokkum, P. 2018, ApJ, 854, 62, doi: [`10.3847/1538-4357/aaa8db`](http://doi.org/10.3847/1538-4357/aaa8db)

(ref: Leja2017) Leja, J., Johnson, B. D., Conroy, C., van Dokkum, P. G., & Byler, N. 2017, ApJ, 837, 170, doi: [`10.3847/1538-4357/aa5ffe`](http://doi.org/10.3847/1538-4357/aa5ffe)

(ref: Leja2013) Leja, J., van Dokkum, P., & Franx, M. 2013, ApJ, 766, 33, doi: [`10.1088/0004-637X/766/1/33`](http://doi.org/10.1088/0004-637X/766/1/33)

(ref: Liu2018) Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172, doi: [`10.3847/1538-4357/aaa600`](http://doi.org/10.3847/1538-4357/aaa600)

(ref: LoFaro2017) Lo Faro, B., Buat, V., Roehlly, Y., et al. 2017, MNRAS, 472, 1372, doi: [`10.1093/mnras/stx1901`](http://doi.org/10.1093/mnras/stx1901)

(ref: MadauDickinson2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magnelli2015) Magnelli, B., Ivison, R. J., Lutz, D., et al. 2015, A&A, 573, A45, doi: [`10.1051/0004-6361/201424937`](http://doi.org/10.1051/0004-6361/201424937)

(ref: Magnelli2019) Magnelli, B., Karim, A., Staguhn, J., et al. 2019, arXiv e-prints. [`https://arxiv.org/abs/1904.10006`](https://arxiv.org/abs/1904.10006)

(ref: Marrone2018) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51, doi: [`10.1038/nature24629`](http://doi.org/10.1038/nature24629)

(ref: Mccracken2012) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: McLeod2016) McLeod, D. J., McLure, R. J., & Dunlop, J. S. 2016, MNRAS, 459, 3812, doi: [`10.1093/mnras/stw904`](http://doi.org/10.1093/mnras/stw904)

(ref: Michalowski2017) Michałowski, M. J., Dunlop, J. S., Koprowski, M. P., et al. 2017, MNRAS, 469, 492, doi: [`10.1093/mnras/stx861`](http://doi.org/10.1093/mnras/stx861)

(ref: Murray2013) Murray, S. G., Power, C., & Robotham, A. S. G. 2013, MNRAS, 434, L61, doi: [`10.1093/mnrasl/slt079`](http://doi.org/10.1093/mnrasl/slt079)

(ref: Muzzin2013) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJS, 206, 8, doi: [`10.1088/0067-0049/206/1/8`](http://doi.org/10.1088/0067-0049/206/1/8)

(ref: Narayanan2018) Narayanan, D., Conroy, C., Davé, R., Johnson, B. D., & Popping, G. 2018, ApJ, 869, 70, doi: [`10.3847/1538-4357/aaed25`](http://doi.org/10.3847/1538-4357/aaed25)

(ref: Narayanan2014) Narayanan, D., & Krumholz, M. R. 2014, MNRAS, 442, 1411, doi: [`10.1093/mnras/stu834`](http://doi.org/10.1093/mnras/stu834)

(ref: Nayyeri2014) Nayyeri, H., Mobasher, B., Hemmati, S., et al. 2014, ApJ, 794, 68, doi: [`10.1088/0004-637X/794/1/68`](http://doi.org/10.1088/0004-637X/794/1/68)

(ref: Oesch2018) Oesch, P. A., Bouwens, R. J., Illingworth, G. D., Labbé, I., & Stefanon, M. 2018, ApJ, 855, 105, doi: [`10.3847/1538-4357/aab03f`](http://doi.org/10.3847/1538-4357/aab03f)

(ref: Oliver2012) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614, doi: [`10.1111/j.1365-2966.2012.20912.x`](http://doi.org/10.1111/j.1365-2966.2012.20912.x)

(ref: Pavesi2018) Pavesi, R., Riechers, D. A., Sharon, C. E., et al. 2018, ApJ, 861, 43, doi: [`10.3847/1538-4357/aac6b6`](http://doi.org/10.3847/1538-4357/aac6b6)

(ref: Salim2018) Salim, S., Boquien, M., & Lee, J. C. 2018, ApJ, 859, 11, doi: [`10.3847/1538-4357/aabf3c`](http://doi.org/10.3847/1538-4357/aabf3c)

(ref: Salmon2016) Salmon, B., Papovich, C., Long, J., et al. 2016, ApJ, 827, 20, doi: [`10.3847/0004-637X/827/1/20`](http://doi.org/10.3847/0004-637X/827/1/20)

(ref: Sanders2007) Sanders, D. B., Salvato, M., Aussel, H., et al. 2007, ApJS, 172, 86, doi: [`10.1086/517885`](http://doi.org/10.1086/517885)

(ref: Schinnerer2007) Schinnerer, E., Smolčić, V., Carilli, C. L., et al. 2007, ApJS, 172, 46, doi: [`10.1086/516587`](http://doi.org/10.1086/516587)

(ref: Schinnerer2010) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384, doi: [`10.1088/0067-0049/188/2/384`](http://doi.org/10.1088/0067-0049/188/2/384)

(ref: Schreiber2017) Schreiber, C., Pannella, M., Leiton, R., et al. 2017, A&A, 599, A134, doi: [`10.1051/0004-6361/201629155`](http://doi.org/10.1051/0004-6361/201629155)

(ref: Schreiber2018qg) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85, doi: [`10.1051/0004-6361/201833070`](http://doi.org/10.1051/0004-6361/201833070)

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Serjeant2014) Serjeant, S., & Marchetti, L. 2014, MNRAS, 443, 3118, doi: [`10.1093/mnras/stu1266`](http://doi.org/10.1093/mnras/stu1266)

(ref: Silverman2018) Silverman, J. D., Rujopakarn, W., Daddi, E., et al. 2018, ApJ, 867, 92, doi: [`10.3847/1538-4357/aae25e`](http://doi.org/10.3847/1538-4357/aae25e)

(ref: Simpson2014) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125, doi: [`10.1088/0004-637X/788/2/125`](http://doi.org/10.1088/0004-637X/788/2/125)

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1, doi: [`10.1051/0004-6361/201628704`](http://doi.org/10.1051/0004-6361/201628704)

(ref: Song2016) Song, M., Finkelstein, S. L., Ashby, M. L. N., et al. 2016, ApJ, 825, 5, doi: [`10.3847/0004-637X/825/1/5`](http://doi.org/10.3847/0004-637X/825/1/5)

(ref: Spilker2016) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112, doi: [`10.3847/0004-637X/826/2/112`](http://doi.org/10.3847/0004-637X/826/2/112)

(ref: Spilker2018sci) Spilker, J. S., Aravena, M., Béthermin, M., et al. 2018, Science, 361, 1016, doi: [`10.1126/science.aap8900`](http://doi.org/10.1126/science.aap8900)

(ref: Stefanon2017_900nm) Stefanon, M., Bouwens, R. J., Labbé, I., et al. 2017, ApJ, 843, 36, doi: [`10.3847/1538-4357/aa72d8`](http://doi.org/10.3847/1538-4357/aa72d8)

(ref: Straatman2014) Straatman, C. M. S., Labbé, I., Spitler, L. R., et al. 2014, ApJL, 783, L14, doi: [`10.1088/2041-8205/783/1/L14`](http://doi.org/10.1088/2041-8205/783/1/L14)

(ref: Strandet2016) Strandet, M. L., Weiss, A., Vieira, J. D., et al. 2016, ApJ, 822, 80, doi: [`10.3847/0004-637X/822/2/80`](http://doi.org/10.3847/0004-637X/822/2/80)

(ref: Strandet2017) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15, doi: [`10.3847/2041-8213/aa74b0`](http://doi.org/10.3847/2041-8213/aa74b0)

(ref: Swinbank2014) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267, doi: [`10.1093/mnras/stt2273`](http://doi.org/10.1093/mnras/stt2273)

(ref: Taniguchi2007) Taniguchi, Y., Scoville, N., Murayama, T., et al. 2007, ApJS, 172, 9, doi: [`10.1086/516596`](http://doi.org/10.1086/516596)

(ref: Tisanic2019) Tisanić, K., Smolčić, V., Delhaize, J., et al. 2019, A&A, 621, A139, doi: [`10.1051/0004-6361/201834002`](http://doi.org/10.1051/0004-6361/201834002)

(ref: Toft2014) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: Trenti2008) Trenti, M., & Stiavelli, M. 2008, ApJ, 676, 767, doi: [`10.1086/528674`](http://doi.org/10.1086/528674)

(ref: vanderWel2014) van der Wel, A., Franx, M., van Dokkum, P. G., et al. 2014, ApJ, 788, 28, doi: [`10.1088/0004-637X/788/1/28`](http://doi.org/10.1088/0004-637X/788/1/28)

(ref: Walter2012) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233, doi: [`10.1038/nature11073`](http://doi.org/10.1038/nature11073)

(ref: Wang2013) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: Wang2016) Wang, T., Elbaz, D., Schreiber, C., et al. 2016, ApJ, 816, 84, doi: [`10.3847/0004-637X/816/2/84`](http://doi.org/10.3847/0004-637X/816/2/84)

(ref: Wardlow2018) Wardlow, J. L., Simpson, J. M., Smail, I., et al. 2018, MNRAS, 479, 3879, doi: [`10.1093/mnras/sty1526`](http://doi.org/10.1093/mnras/sty1526)

(ref: Weiss2009) Weiß, A., Kovács, A., Coppin, K., et al. 2009, ApJ, 707, 1201, doi: [`10.1088/0004-637X/707/2/1201`](http://doi.org/10.1088/0004-637X/707/2/1201)

(ref: Whitaker2017) Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208, doi: [`10.3847/1538-4357/aa94ce`](http://doi.org/10.3847/1538-4357/aa94ce)

(ref: Williams2014) Williams, C. C., Giavalisco, M., Cassata, P., et al. 2014, ApJ, 780, 1, doi: [`10.1088/0004-637X/780/1/1`](http://doi.org/10.1088/0004-637X/780/1/1)

(ref: Williams2015) Williams, C. C., Giavalisco, M., Lee, B., et al. 2015, ApJ, 800, 21, doi: [`10.1088/0004-637X/800/1/21`](http://doi.org/10.1088/0004-637X/800/1/21)

(ref: Williams2018) Williams, C. C., Curtis-Lake, E., Hainline, K. N., et al. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1802.05272`](https://arxiv.org/abs/1802.05272)

(ref: Wuyts2011) Wuyts, S., Förster Schreiber, N. M., Lutz, D., et al. 2011, ApJ, 738, 106, doi: [`10.1088/0004-637X/738/1/106`](http://doi.org/10.1088/0004-637X/738/1/106)

(ref: Yamaguchi2019) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, arXiv e-prints. [`https://arxiv.org/abs/1903.02744`](https://arxiv.org/abs/1903.02744)

(ref: Zavala2018_3mm) Zavala, J. A., Casey, C. M., da Cunha, E., et al. 2018a, ApJ, 869, 71, doi: [`10.3847/1538-4357/aaecd2`](http://doi.org/10.3847/1538-4357/aaecd2)

(ref: zavala2017) Zavala, J. A., Aretxaga, I., Geach, J. E., et al. 2017, MNRAS, 464, 3369, doi: [`10.1093/mnras/stw2630`](http://doi.org/10.1093/mnras/stw2630)

(ref: Zavala2018Nat) Zavala, J. A., Montaña, A., Hughes, D. H., et al. 2018b, Nature Astronomy, 2, 56, doi: [`10.1038/s41550-017-0297-8`](http://doi.org/10.1038/s41550-017-0297-8)

</paper>

## Items to check

```json
[
 {
  "path": "science.targets[1].coordinates.evidence[0]",
  "value": "10:02:36.30 +2:08:49.55",
  "failed_quote": "Coordinates | 10:02:36.30 +2:08:49.55"
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "z_CO = 3.329 (probable CO(4-3))",
  "failed_quote": "Coordinates | 10:02:36.30 +2:08:49.55"
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "single CO line at 106.5 GHz plus SED photometric redshift",
  "failed_quote": "Coordinates | 10:02:36.30 +2:08:49.55"
 }
]
```
