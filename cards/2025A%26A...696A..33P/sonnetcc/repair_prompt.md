# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A..33P\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The MUSE Ultra Deep Field (MUDF)

# Introduction

Absorption lines identified in quasar spectra are excellent tracers of cosmic gas structures across a wide range of redshift and matter overdensities. Sensitive measurements of low-column-density gas against bright quasars have extensively mapped the redshift distribution of neutral and ionized hydrogen as well as that of metals inside the intergalactic medium (IGM) and around galaxies, within the circumgalactic medium (CGM), from the epoch of reionization to present days (see, e.g., (cite: Oppenheimer+2012; Tumlinson+2017), and (cite: Peroux+2020) for a review).

To date, advances in instrumentation, particularly with integral field spectrographs (IFSs), have enabled a direct view of hydrogen and metal-enriched gas external to the galaxy interstellar medium (ISM) in emission (cite: Hennawi+2013; Borisova+2016; Cantalupo+2017; Umehata+2019; Bacon+2021; Leclercq+2022; Dutta+2024b; Tornotti+2024). However, these studies are limited to the IGM and CGM densest portions, typically at close separations from galaxies. Therefore, absorption spectroscopy in quasar fields remains a crucial way to unravel the connection between the galaxy physical properties (e.g., stellar mass, star-formation rate, morphology) and those processes that regulate galaxy formation and evolution (e.g., gas accretion and outflows) within their larger-scale environment (cite: Weiner+2009; Chen+2010a; Chen+2010b; Steidel+2010; Zabl+2019; Dutta+2020; Galbiati+2023; Schroetter+2024).

At observed optical wavelengths, recent works in a wide range of redshifts, from $z\approx 0.5$ to $z\approx 4.5$, revealed a clear clustering of metal absorption lines, such as Mg II and C IV absorbers (cite: Dutta+2021; Banerjee+2023; Galbiati+2023; Galbiati+2024), or strong hydrogen absorbers, i.e., the Lyman limit systems (LLSs) and damped Ly$\alpha$ absorbers (cite: Fumagalli+2016; Lofthouse+2023) around star-forming galaxies. These dense and complete spectroscopic surveys highlighted the importance of the galaxy environment in shaping the gas distribution at all redshifts, with a clear excess of cool/warm gas seen in absorption near group galaxies compared to isolated ones. With the clustering of multiple galaxies near absorption systems, a more complex picture emerges, where at least a fraction of the absorbers are probing the gas-rich cosmic structures within which galaxies reside.

At longer wavelengths, surveys in the (sub-)millimeter, especially with the Atacama Large Millimeter Array (ALMA), provided a complementary view of the dusty and gas-rich galaxies associated with absorption line systems in quasar fields. Following the first detection of \[C\]$_{\rm 158\,\mu m}$, line and dust-continuum emission from galaxies associated with $z\approx 4$ DLAs (cite: Neeleman+2017), systematic searches of molecular lines at $z\approx 0.5-2.5$ in the proximity of high-column density H I systems show that the highest-metallicity DLAs are associated with the most massive galaxies (cite: Moller+2018; Kanekar+2018; Kanekar+2020; Neeleman+2018; Neeleman+2019; Kaur+2022; Kaur+2022b). As in the case of optical searches, (sub-)millimeter observations uncover a wide range of environments, from more isolated galaxies to groups.

Based on the above results, multiple tracers are needed to complement our view of the gas distribution around cosmic structures populated by galaxies. Indeed, efforts to combine galaxy observations in quasar fields across wavelengths, especially with the Multi Unit Spectroscopic Explorer (cite: Bacon+2010) at the Very Large Telescope (VLT) and ALMA, are multiplying (cite: Klitsch+2018; Peroux+2019; Szakacs+2021). These combined observations reveal examples of groups composed of optically selected galaxies and dusty or molecular-rich galaxies near strong hydrogen absorbers (cite: Fynbo+2018; Klitsch+2018; Klitsch+2019), particularly LLSs and DLAs. Conversely, multi-wavelength searches for galaxies associated with metal lines have been explored less (cite: Kashino+2023). However, results similar to those of LLSs and DLAs are expected. For instance, the search of Ly$\alpha$ emitting galaxies near Mg II absorbers with MUSE reveals an unexpected lack of detections near high-equivalent width absorbers at $z\approx 3-4$, perhaps hinting at the presence of an unseen dusty galaxy population (cite: Galbiati+2024).

Following this line of inquiry, in this paper, we present new ALMA observations of the MUSE Ultra Deep Field (cite: Lusso+2019; Fossati+2019; Revalski+2023), a unique set of multiwavelength imaging and wide-field spectroscopic observations (from UV to near IR) at exceptional depths within a $2\times 2$ arcmin$^2$ field hosting two bright $z\approx 3.22$ quasars (Q2139-4433 and Q2139-4434, hereafter QSO-NW and QSO-SE, respectively), which we use to map in absorption gaseous cosmic structures at $z\lesssim 3.22$. In this paper, we extend the MUDF dataset to longer wavelengths by mapping the 1.2-mm dust continuum with ALMA band 6 and spectral scans in band 3 to target the rotational transitions of carbon monoxide CO. With these data, we study the association of dusty and gas-rich galaxies with metal absorbers detected in the MUDF volume without preselection on the absorber properties. Comparisons with detections at optical and near-infrared (NIR) wavelengths, reaching the dwarf galaxy regime, are also presented to build a complete view of the galaxy environment surrounding absorbers.

This paper is structured as follows: in Sect. [2](#sect:data-red) we present the acquired data and illustrate the data processing. In Sect. [3](#sect:ancillary_datasets), we describe the ancillary datasets used in this work. We devote Sect. [4](#sect:source_extraction) to analyzing the data, extracting the sources, and measuring the flux continuum and line luminosities. In Sect. [5](#sect:results_discussion), we discuss the properties of our galaxy sample in connection with those of the surrounding gas detected in absorption along the quasar sightlines. Finally, in Sect. [6](#sect:summary_conclusions) we summarize the results and draw our conclusions. In this work, we assume a standard $\Lambda$ cold dark matter cosmology with $H_0 = 67.7\,{\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_{\rm m} = 0.310$, and $\Omega_\Lambda = 1 - \Omega_{\rm m}$ from (cite: PlanckColl+2020). We use AB magnitude and adopt $3\sigma$ limits when not stated otherwise.

![](figs/mos+singles_pointing_hst_muse_mask.pdf)

![](figs/sens_scans_v2.pdf)

# ALMA observations and data reduction

## Description of observations

In this work, we use ALMA band 6 mosaic observations from the program 2021.1.00285.S (Cycle 8, PI: M. Fumagalli), along with three ALMA band 3 spectral scans toward individual sources within the sky region covered by the band 6 mosaic (program ID: 2023.1.00461.S, Cycle 10, PI: A. Pensabene). The latter observations were designed to accurately measure the redshift of sources lacking robust spectroscopic constraints from MUSE (see Sect. [4.4](#ssect:hst_counterparts)). In what follows, we describe the acquisition and processing of the data.

The ALMA band 6 mosaic has been designed to cover the central part of the MUDF, where the MUSE observations achieve the maximum depth (cite: Tornotti+2024). The mosaic consists of 53 Nyquist-sampled pointings, each with a half-power beam width (HPBW) of $\approx24\rlap{.}{\ensuremath{''}}25$ at the reference frequency of $240.10\,{\rm GHz}$, resulting in a covered rectangular sky area of $\approx1\rlap{.}{\ensuremath{'}}9\times1\rlap{.}{\ensuremath{'}}6$ (Fig. [1](#fig:pb_pointings)). Observations were carried out in frequency division mode (FDM). The spectral tuning is composed of four $1.875\,{\rm GHz}$-wide spectral windows (SPWs) centered at frequencies $254.498\,{\rm GHz}$, and $257.998\,{\rm GHz}$ in the upper sideband (USB), and $240.102\,{\rm GHz}$ and $243.102\,{\rm GHz}$ in the lower sideband (LSB), respectively. The total effective bandwidth of the spectral setup is $7.5\,{\rm GHz}$ centered at wavelength $1.2\,{\rm mm}$. Observations were subdivided into five execution blocks (EBs) carried out during the period from May 28 to June 3, 2022 employing 41 to 44 12-m antennas with baselines ranging between $15.1- 783.5\,{\rm m}$ yielding a naturally-weighted synthesized beam FWHM of $0\rlap{.}{\ensuremath{''}}55\times0\rlap{.}{\ensuremath{''}}51$, and were conducted with a mean precipitable water vapor (PWV) of $0.3 - 1\,{\rm mm}$. The total on-source integration time was $\simeq 5.86\,{\rm h}$ achieving a sensitivity of $26\,{\rm \mu Jy\,beam^{-1}}$ over the total bandwidth. The native spectral resolution is $\simeq 7.8\,{\rm MHz}$, corresponding to $\simeq 9.5\,{\rm km\,s^{-1}}$ at the reference frequency of $240.1\,{\rm GHz}$. The J2126-4605 and J2258-2758 were used as phase and flux calibrators during observations.

The ALMA band 3 observations consist of three single-pointing spectral scans centered on three sources revealed in the band 6 mosaic (see, Fig. [1](#fig:pb_pointings)) to target their CO(3–2) line (rest-frame frequency $\nu_{\rm rest}=461.041\,{\rm GHz}$) in the redshift range $z\simeq 2-3$. The frequency setups were tuned based on the photometric redshift probability distributions (pointing to the redshift range $1.8\lesssim z \lesssim 2.8$) obtained from multiwavelength photometry available for galaxies in the MUDF (cite: Revalski+2023) using the EAZY code (cite: Brammer+2008). Observations were carried out in FDM employing five frequency tunings with two adjacent $1.875\,{\rm GHz}$-wide SPWs per sideband designed to cover the spectral range $86.25 - 115.80\,{\rm GHz}$ contiguously. The total effective bandwidth is $29.55\,{\rm GHz}$. Each frequency tuning was observed in two EBs, and executed between January 18th and March 4th 2024, employing 40 to 45 12-m antennas with baselines ranging in $15.1-483.9\,{\rm m}$ and a mean ${\rm PWV}=2.7-7.1\,{\rm mm}$. The $uv$ coverage of these observations yields to a naturally-weighted synthesized beam size of $2\rlap{.}{\ensuremath{''}}5\times2\rlap{.}{\ensuremath{''}}3$ at the reference frequency of $101\,{\rm GHz}$. The total on-source observing time was $8.1\,{\rm h}$. Data were acquired with a native spectral resolution of $1.95\,{\rm MHz}$, corresponding to $\simeq5.8\,{\rm km\,s^{-1}}$ at $101\,{\rm GHz}$. The sensitivity achieved in the final dataset varies along with frequency due to the variation in atmospheric absorption and weather conditions across the EBs (Fig. [2](#fig:sens_scans)) and has a median value of $0.20\,{\rm mJy\,beam^{-1}}$ over $33.7\,{\rm MHz}$, or $\simeq 100\,{\rm km\,s^{-1}}$ at $101\,{\rm GHz}$. Fig. [1](#fig:pb_pointings) shows the footprints of the ALMA observations presented in this work, the pointing design, and the response of the primary beam (PB) of the band 6 mosaic. In Fig. [2](#fig:sens_scans), we show the spectral coverage of the acquired band 3 spectral scans and the sensitivity variation along the frequency range.

## Data calibration and imaging

We calibrated the data using the Common Astronomy Software Application (cite: McMullin+2007; Hunter+2023) by running the calibration pipeline `scriptForPI` provided with the raw measurement set using the CASA pipeline versions 6.2.1 and 6.5.4 for band 6 and 3 data, respectively. No self-calibration was performed on the datasets. We imaged band 6 visibilities by using the CASA task `tclean`. We first obtained a “dirty” continuum image by performing the Fourier transform of the visibilities (`niter=0`) using the multi-frequency synthesis mode (`specmode = “mfs”`) and adopting a natural weighting scheme to maximize the sensitivity per beam. In this procedure, we set “mosaic” as the gridding convolution function and put the phase center at the coordinates ICRS 21:42:24.4658 $-$44:19:53.007. We used a pixel scale of $0\rlap{.}{\ensuremath{''}}08$ to achieve the Nyquist sampling of the longest baselines. Similarly, we obtained “dirty” band 6 data cubes of the LSB and USB with $25\,{\rm km\,s^{-1}}$ channel width. Additionally, in order to improve the surface brightness sensitivity for faint extended emission, we obtained continuum image by applying a Gaussian taper in the $uv$ plane with ${\rm FWHM}_{uv}=90\,{\rm k}\lambda$ and setting the pixel size to $0\rlap{.}{\ensuremath{''}}4$, yielding a synthesized beam FWHM of $2\rlap{.}{\ensuremath{''}}19\times2\rlap{.}{\ensuremath{''}}39$. The “dirty” data preserve the intrinsic properties of the noise, and we used that to perform a blind search of continuum and line emitters in the field (see Sect. [4](#sect:source_extraction)). We finally obtained “cleaned” continuum images and cubes by applying the cleaning algorithm down to $2\sigma$, placing circular masks of $2\rlap{.}{\ensuremath{''}}0$ diameter around sources extracted with $S/N>5$.

We imaged the ALMA band 3 pointings by obtaining “dirty” cubes of the combined dataset, including all the SPWs using `tclean` with `niter=0` and the “natural” weighting scheme of the visibilities. We set the pixel scale at $0\rlap{.}{\ensuremath{''}}3$ and the channel width at $100\,{\rm km\,s^{-1}}$ at the reference frequency of $101\,{\rm GHz}$, which is expected to maximize the $S/N$ per channel while resolving the line profile. In such datasets, sources are located at the phase center and appear faint and spatially unresolved and no bright continuum emitters are found in the cubes. For these reasons, the cleaning of cubes is not required.

# Ancillary multi-wavelength observations

In this study, we use the catalog of MUDF galaxies from (cite: Revalski+2023), which provides deep photometry and high-confidence redshifts constrained with HST and MUSE spectroscopy, to associate optical counterparts to the sources identified by ALMA. This field benefits from extremely deep MUSE observations (ESO PID 1100.A-0528, PI: M. Fumagalli) with an integration time of $\approx$142 hours in wide field mode and with extended wavelength coverage ($4600-9350\,\text{\AA}$, and spectral resolution $R\approx2000-4000$). We refer to (cite: Fossati+2019) for detailed descriptions of the survey design and the data reduction.

The MUDF survey is specifically designed to study the connection between gas and galaxies across cosmic time and thus also includes high-resolution ($R\approx40,000$) spectra of the two quasars (QSO-SE and QSO-NW with $r$-band magnitude 17.9 and 20.5, respectively) to probe the IGM and CGM in absorption (cite: Beckett+2024). The quasar spectra were obtained using the Ultraviolet and Visual Echelle Spectrograph (UVES, (cite: Dekker+2000)) at the VLT (PIDs: 65.O-0299, 68.A-0216, 69.A-0204, and 102.A-0194, PI: V. D’Odorico) and cover the wavelength range $4100-9000\,\text{\AA}$ with a $S/N$ per pixel of $\approx25$ and $\approx10$ for the bright and faint quasar, respectively.

In HST Cycle 26, we also collected 90 orbits of WFC3/F140W imaging and WFC3/IR G141 grism spectroscopy (PID 15637, PI: M. Rafelski & M. Fumagalli), providing a deep and extensive sampling of the galaxy spectral energy distributions (SEDs) from UV to NIR wavelengths (cite: Revalski+2024). Custom calibration of HST observations is described by (cite: Revalski+2023) together with a complete list of additional optical and near-UV (NUV) photometry[^3].

## Catalog of HST-selected galaxies

Galaxies detected in the deep WFC3/F140W image are included in a catalog that is $50\%$ complete at $27.6\rm\,mag$ and covers the entire area observed with MUSE, as described by (cite: Revalski+2023). To all the detected galaxies, a spectroscopic redshift is assigned together with a quality flag (see table 5 in (cite: Revalski+2023)), depending on the presence of high $S/N$ lines in their spectra. The spectral fitting process used to identify and fit emission lines across a wide range of wavelengths, from UV to NIR, is detailed in (cite: Revalski+2024). A high-quality redshift (redshift quality flag $\geq3$) was assigned to $25\%$ of the sources with spectral coverage. The physical properties of these galaxies, such as stellar mass ($M_{\star}$) and star formation rate (SFR), are obtained by fitting the multiwavelength photometry and the MUSE spectra simultaneously, as described in (cite: Fossati+2018) , to which we refer for full details about the method. Finally, we distinguished between isolated galaxies and those residing in groups. To this end, we applied a friends-of-friends algorithm to identify galaxies belonging to a group as all the sources that are not isolated within $\pm 500\,{\rm km\,s^{-1}}$ along the line of sight (cite: Fossati+2019). Overall, we found that $\approx86\%$ of the galaxies reside in 23 different groups across the redshift range $z=1-3$, with five groups with more than five galaxies, and two with more than 15 members.

## Catalog of quasar absorbers

The detailed procedure used to identify the absorption line systems in the spectra of the two quasars, as well as the complete list of the transitions and their properties, is illustrated in table 1 of (cite: Beckett+2024), and is only briefly summarized below. The spectra are normalized by fitting a cubic spline to the continuum redward to the Ly$\alpha$ emission of the quasars by using the ESPRESSO data analysis software (cite: Cupani+2016). The spectra are then visually inspected to identify absorption line systems such as Mg I, Mg II, Fe II, Al II, Al III, C IV and Si IV. All these lines are then fitted using the Bayesian code Monte Carlo Absorption Line Fitter (MC-ALF, (cite: Longobardi+2023)) and decomposed into the minimum number of Voigt profiles required to reproduce the observed flux. The Doppler parameter, column density, and redshift of each Voigt component are the free parameters of the fit. Additional filler components account for blends with absorption features arising from different ions at different redshifts. We finally assign the redshift of the component with the largest column density to each absorber. The resulting sample includes 22 absorption systems in the QSO-SE sightline, and nine systems in the QSO-NW sightline. Only one absorption system is detected in both the sightlines at $z\approx0.88$ (see, table 1 in (cite: Beckett+2024)). Multiple ions are often detected at the redshift of each system.

# Extraction and characterization of ALMA sources

We performed a source search in the “dirty” ALMA band 6 continuum mosaic image using the Python-based code LineSeeker[^4]. The complete details of the codes and performances are described in (cite: Gonzalez-Lopez+2017; Gonzalez-Lopez+2019). Here, we summarize the basic characteristics and operation of the algorithm.

LineSeeker has been designed to perform a blind search of line emitters in large data cubes from (sub-)millimeter surveys such as the ALMA Spectroscopic Survey in the *Hubble* Ultra Deep Field (cite: Decarli+2019c; Gonzalez-Lopez+2019; Gonzalez-Lopez+2020), but can be equivalently employed to search sources in 2D continuum images. The code searches for the line emitter in the cube by adopting a matched filter approach. LineSeeker convolves the data cube along the spectral axis with a Gaussian kernel with a range of input widths set based on a typical linewidth. For each convolution iteration, the code finds all the voxels above a given $S/N$ threshold. The noise is estimated in the convolved cube through $5\sigma$-clipped statistics, and the signal is measured from the peak flux density per beam. The sources are extracted by grouping connected voxels using the Density-Based Spatial Clustering of Application with Noise algorithm (cite: Ester+1996)[^5]. Then, the final list of sources is drawn by cross-matching the source catalogs obtained from different convolution kernels and selecting the maximum $S/N$. For each identified candidate, LineSeeker estimates the probability of false positive detection by performing the source search on the negative cube. Since any negative peak in a (sub-)millimeter extragalactic survey is expected to be result of noise, the ratio between positive and negative detection distributions is used to estimate the fidelity (or reliability) of source candidates as a function of $S/N$ as $$\begin{equation}
 F(S/N)=1-\frac{N_{\rm neg}(S/N)}{N_{\rm pos}(S/N)}, 
\end{equation}$$ where $N_{\rm neg}$ and $N_{\rm pos}$ are the number of negative and positive detections at a given $S/N$. The cumulative distribution of negative detections is then modeled assuming Gaussian-distributed noise by using a function of the form $N[1-{\rm erf}(S/N/\sqrt{2}\,\sigma)$, where erf is the error function, and $N$, $\sigma$ are free parameters. The best-fit model is finally used to estimate $F(S/N)$ for all positive source candidates. The search of continuum sources in 2D images can be performed similarly with LineSeeker by skipping the convolution steps.

[TABLE]

Table notes: High-fidelity ($F\ge90\%$) candidate list extracted via blind search using LineSeeker. $^{(1)}$Identifier of ALMA 1.2-mm continuum-selected candidates. $^{(2)}$Right Ascension (ICRS). $^{(3)}$Declination (ICRS). $^{(4)}$Flux density extracted from the source peak pixel in the $1.2\,{\rm mm}$ tapered continuum image. $^{(5)}$Signal-to-noise ratio. $^{(6)}$Fidelity and its uncertainties estimated by LineSeeker using negative detections. All sources have a NIR counterpart, as revealed in *HST* / WFC3 F140W image, therefore, the actual fidelity should be considered $F=1$. $^{(7)}$High-confidence redshift measurement from MUSE spectroscopic data. $^{(\dagger)}$Tentative redshift estimate measured from low-quality MUSE spectrum. $^{(8)}$Redshift measurement derived from emission line detected with ALMA (see, also, Table [1](#tbl:co32_line)). $^{(9)}$Emission line detected in either ALMA band 6 data cube or band 3 spectral scans. $^{(10)}$Apparent AB magnitude in *HST*/WFC3 F140W filter. All reported uncertainties correspond to $1\sigma$.

## Continuum-selected sources in the 1.2-mm image

We selected source candidates in the ALMA band 6 mosaic by running LineSeeker on the untapered “dirty” continuum image, excluding the region below $50\%$ of the maximum PB response, where the low telescope sensitivity increases the probability of selecting spurious sources. The “dirty” data are preferred over the “cleaned” ones, since the former preserves the intrinsic properties of the noise. Furthermore, we input the “dirty” image into LineSeeker without correcting for the PB response, thus preserving the spatial homogeneity of the noise across the field-of-view (FoV). With LineSeeker we extracted all the detections above $S/N>3$ and selected the source candidates with $F\ge 90\%$, corresponding to $S/N\ge 5.0$. We recovered a total of seven 1.2-mm continuum-selected candidates (labeled C1 to C7), including the host galaxy of the QSO-SE (C2). We report the location of these sources in Fig.[1](#fig:pb_pointings) and their characteristics in Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand). We performed similar search on the tapered band 6 continuum image, which is more sensitive to faint extended emission, and found consistent result.

To further investigate the reliability of faint candidates, we complemented the search for continuum sources by cross-matching the catalog of galaxies detected in the HST/WFC3 F140W image (see Sect. [3.1](#ssect:hst_cat)) with the sources selected by LineSeeker with fidelity values within $20\%\le F <90\%$. To this purpose, we search HST counterparts around the sky position of ALMA continuum sources within a separation limit of $0\rlap{.}{\ensuremath{''}}5$, comparable to the beam size of the 1.2-mm continuum untapered image, and found no associations. For the goal of this study, we therefore include in our fiducial sample of ALMA continuum sources only the high-fidelity candidates selected as previously described. For all of these sources, we found associations in the HST catalog as described in Sect [4.4](#ssect:hst_counterparts).

We evaluated the completeness of our ALMA band 6 survey by injecting artificial point-like sources at random locations in the untapered dirty 1.2-mm continuum image. Then, we computed the rate of recovered sources by running LineSeeker and searching for candidates with $F\ge90\%$ encompassed within $0\rlap{.}{\ensuremath{''}}275$ from the injected position, corresponding to half of the beam major axis. We repeated the simulation by injecting $20$ sources simultaneously into the image and repeating this procedure for different values of flux density in the range $[2 , 10]\times{\rm RMS}$. We finally iterated the entire simulation $30$ times to achieve good statistics. As a result, we find that our source search is complete to $\approx90\%$ at $S/N\approx7.5$. During the simulation, we also evaluated the effect of flux boosting (cite: Hogg+1998; Scott+2002; Coppin+2006) on the recovered sources, and we determined that it is negligible at $S/N \gtrsim 5$. Thus, we do not correct the measured fluxes of our source sample for this effect.

## Line emitters in band 6 data cubes

The band 6 data cubes cover multiple molecular and atomic lines which enter the LSB and USB at different redshifts. In particular, for $z<3.5$ the carbon monoxide CO transitions are covered by our frequency setup from the CO(3–2) at $z\simeq 0.45$ in the USB, to the CO(9–8) at $z\simeq 3.34$[^6], while the fine-structure lines of the atomic carbon \[C\]$_{\rm 609, 369\,\mu m}$ are observable from $z\approx0.9$ up to $2.38$.

To complete the source search in the field, we employed LineSeeker to detect line emitters in the cubes blindly. Similarly to the search for continuum emitters (see Sect. [4.1](#ssect:cont_selected_sources)), we restricted the source extractions to the survey area with PB response $\ge 50\%$, and we run the line-search algorithm on both LSB and USB cubes using a Gaussian kernel with width ranging from 1 to 18 channels, which is adequate to match the typical linewidths of ${\rm FWHM}\sim 50-1000\,{\rm km\,s^{-1}}$ observed in high-redshift galaxies (cite: Birkin+2021). We extracted all line-emitting candidates with $S/N\ge 3.0$ and then selected those with $F\ge90\%$. As a result, we identified one line emission in the spectrum of the C6 source, which we already identified through its continuum at 1.2 mm (see Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand)). This source has a robust spectroscopic redshift of $z=1.05413$ measured with the MUSE data (see Sect. [4.4](#ssect:hst_counterparts)) that allowed us to identify the line as \[C\]$_{\rm 609\,\mu m}$. We measured the line flux by fitting the spectrum extracted from the source peak pixel (see, Sect. [4.5](#ssect:source_fluxes)), and obtained $F_{\rm [CI]609\,\mu m}=0.36\pm0.10\,{\rm Jy\,beam^{-1}\,km\,s^{-1}}$. The source redshift we estimated with this line is consistent with the one measured from the MUSE spectrum. The visual inspection of ALMA band 6 spectra at the location of all the 1.2-mm continuum-selected sources did not reveal additional emission lines, consistently with the spectroscopic redshift measurements of the sources.

Finally, we complemented our line search by cross-matching the HST catalog of galaxies with the source catalog of line-emitting candidates delivered by LineSeeker following the same approach described in Sect. [4.1](#ssect:cont_selected_sources). This procedure did not reveal additional line emitters.

## Source detection in band 3 spectral scans

We analyzed ALMA band 3 spectral scans targeting sources C1, C3, and C4. We inspected the spectra at the center of the pointing around the nominal locations of the continuum detections revealed at 1.2 mm in the ALMA mosaic (see Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand)). The CO(3–2) line, which is identified based on the posterior distributions of the source photometric redshift[^7], is detected in all three sources, which appear spatially unresolved given the low angular resolution of these ALMA observations (see Sect. [2](#sect:data-red)).

We ran LineSeeker on band 3 "dirty" cubes and continuum images similarly to what described in Sects. [4.1](#ssect:cont_selected_sources) and  [4.2](#ssect:line_selected_sources) for band 6 data. The search for line emitters within the cubes reveal the CO(4–3) line of the QSO-SE (C2) which is redshifted in the ALMA band 3 at $z\approx3.22$. The analysis of this detection is beyond the scope of this work. Additionally, we performed visual inspection of the band 3 spectra in the location of secure continuum sources selected in the ALMA band 6 mosaic, and found no evident emission lines. Finally, in the 3-mm continuum images we did not find neither high-fidelity source candidates, nor HST counterparts associated to the low-fidelity ones.

## HST counterparts of ALMA continuum sources

In Fig. [3](#fig:counterparts), we show postage stamps of the seven ALMA continuum-selected sources and their NIR and optical/NUV counterparts in the field. As also described in Sect. [4.1](#ssect:cont_selected_sources), we cross-matched all the sources detected in the continuum at 1.2 mm with ALMA with the catalog of HST-selected galaxies. Within a projected separation of $0\rlap{.}{\ensuremath{''}}5$ in the sky, we found an unambiguous counterpart for all ALMA detections, except for C5. By visually inspecting the HST/WFC3 F140W image of this source, we found that the peak of the ALMA continuum appears to correspond to a faint and compact source located southeast relative to an extended object. Interestingly, the 1.2-mm continuum emission seems to be spatially associated with diffuse emission revealed by HST around the extended galaxy, which suggests irregular morphology, possibly due to the interaction with the nearby compact source. Alternatively, gravitational lensing may represent a viable explanation to the observed emission. However, given the limited $S/N$ of the ALMA data, we cannot confidently assess the nature of this emission. The angular resolution of MUSE observations is insufficient for adequately deblending the spectra of these two closely spaced sources (see, Fig. [3](#fig:counterparts)). By inspecting the MUSE spectrum extracted at the location of the galaxies, we assigned to both the sources a low-quality redshift estimate of $z\approx 2.4723$ on the basis of only the tentative detection of C IV $\lambda\lambda1548, 1550$ absorption line feature. Future deep spectroscopic observations using, for example, JWST, are needed to shed light on the characteristics of this system.

A high-quality spectroscopic redshift is constrained from the MUSE spectra for C2, C6, and C7. The remaining ones (i.e., C1, C3, and C4), which are also the faintest in the F140W filter among the counterparts (see, Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand)), do not have a secure redshift measurement from MUSE or HST grism spectra. The redshifts of the latter, are accurately measured from the CO(3–2) lines detected in the band 3 spectral scans as previously described in Sect. [4.3](#ssect:search_spectral_scans).

![](figs/cont_counterparts_all6.pdf)

![](figs/spectra.pdf)

## Source fluxes and luminosities

All seven ALMA-selected sources detected in the continuum at 1.2 mm appear, at best, marginally resolved. To maximize the recovered signal, we estimated their flux density in the $\sim2{\ensuremath{''}}$ tapered image through a single-pixel measurement of the continuum source flux peak that we then rescaled for the PB response at the corresponding location. We then applied the same PB rescaling to the RMS (in ${\rm mJy\,beam^{-1}}$) measured on the 1.2-mm continuum image to estimate the $1\sigma$ uncertainty on $F_{1.2\,{\rm mm}}$. We report these quantities in Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand).

We measured the CO(3–2) line flux of C1, C3, and C4 detected in the band 3 cubes by fitting the spectra extracted from the source peak employing a single Gaussian plus a constant to model the line and the continuum. We then estimated the best-fit model parameters and uncertainties from the posterior probability distributions obtained through the Python Markov chain Monte Carlo (MCMC) ensemble sampler `emcee` package (cite: Foreman+2013), assuming box-like priors based on a visual inspection of the data. We finally derived the line luminosities as (cite: Solomon+1997):

$$\begin{align}
\label{eq:lum}
L_{\rm CO} [L_{\astrosun}] =&  1.04\times 10^{-3}\,S\Delta\varv\,\nu_{\rm obs}\,D_L^2, \\
\label{eq:lum_prime}
L'_{\rm CO} [{\rm K\,km\,s^{-1}\,pc^2}] =& 3.25\times10^7\,S\Delta\varv\,\frac{D_L^2}{(1+z)^3\,\nu_{\rm obs}^2,}
\end{align}$$

where $S\Delta\varv$ is the velocity-integrated line flux in ${\rm Jy\,km\,s^{-1}}$, $\nu_{\rm obs}$ is the observed central frequency of the line in GHz, $z$ is the source redshift measured from the centroid of the CO line, and $D_L$ is the luminosity distance in Mpc. The relation between Eq. ([\[eq:lum\]](#eq:lum)) and ([\[eq:lum_prime\]](#eq:lum_prime)) is $L_{\rm CO}=3\times10^{-11}\,\nu_{\rm rest}^3\,L_{\rm CO}'$, where $\nu_{\rm rest}$ is the line rest frequency in GHz. In Fig. [4](#fig:spectra), we show the spectra and the best-fit models and report the line measurements in Table [1](#tbl:co32_line).

| ID$_{\rm 1.2mm}\,^{(1)}$ | C1 | C3 | C4 |
|:---|:--:|:--:|:--:|
| 1-4 $z_{\rm CO}\,^{(2)}$ | $2.2529^{+0.0003}_{-0.0003}$ | $2.2954^{+0.0005}_{-0.0005}$ | $2.3676^{+0.0003}_{-0.0003}$ |
| $S\Delta\varv\,^{(3)}\,({\rm Jy\,beam^{-1}\,km\,s^{-1}})$ | $0.63^{+0.06}_{-0.06}$ | $0.24^{+0.06}_{-0.06}$ | $0.23^{+0.04}_{-0.04}$ |
| ${\rm FWHM}\,^{(4)}\,({\rm km\,s^{-1}})$ | $510^{+50}_{-50}$ | $330^{+120}_{-80}$ | $320^{+50}_{-40}$ |
| $L_{\rm CO}\,^{(5)}\,(10^{7}\,L_{\astrosun})$ | $2.3^{+0.2}_{-0.2}$ | $0.9^{+0.2}_{-0.2}$ | $0.95^{+0.14}_{-0.14}$ |
| $L'_{\rm CO}\,^{(6)}\,({\rm 10^{10}\,K\,km\,s^{-1}\,pc^2})$ | $1.77^{+0.17}_{-0.17}$ | $0.70^{+0.18}_{-0.18}$ | $0.72^{+0.11}_{-0.10}$ |

: ALMA CO(3–2) line emitter.

Table notes: Derived properties from the CO(3–2) line. $^{(1)}$Identifier of ALMA 1.2-mm continuum-selected galaxies. $^{(2)}$Redshift estimate for the CO(3–2) line. All reported uncertainties correspond to $1\sigma$ confidence interval as derived from the 16th and 84th percentile of the posterior probability distribution. $^{(3)}$Velocity-integrated line flux. $^{(4)}$Full Width at Half Maximum of the line. $^{(5,6)}$Line luminosities as derived from Eq. ([\[eq:lum\]](#eq:lum)) and ([\[eq:lum_prime\]](#eq:lum_prime)).

# Linking galaxies to absorbers in multiwavelength datasets

Absorption studies toward background quasars typically target galaxies in their rest-frame optical/UV. So far, (sub-)millimeter studies (e.g., with ALMA) have focused on specific classes of absorbers, such as high-column-density DLAs (cite: Neeleman+2017; Kanekar+2018; Kaur+2022; Kaur+2022b). However, little is known about the contribution of dusty and gas-rich galaxies to the cosmic metal enrichment across different epochs of the Universe from untargeted observations (cite: Dudzeviciute+2021). In this work, we capitalize on our blind ALMA survey to study the association between cosmic gas traced by quasar absorption systems in the MUDF, and galaxies detected at millimeter wavelengths in their dust continuum.

![](figs/abs_lines_v3_reordered.pdf)

## Gas-galaxy association rate

With accurate redshift measurements ($\Delta\varv\lesssim 60\,{\rm km\,s^{-1}}$) of our ALMA-selected galaxies from either MUSE spectra or ALMA CO(3–2) line (see Sect. [4.4](#ssect:hst_counterparts),  [4.5](#ssect:source_fluxes)), we matched these galaxies with the absorbers in velocity space in either of the quasar sightlines (see, Sect. [3.2](#ssect:qso_absorbers)). Following the approach typically adopted in the literature for optical studies (cite: Dutta+2021; Schroetter+2021; Galbiati+2023; Beckett+2024), we link the absorbing gas with galaxies by searching for association within $\left | \Delta\varv \right |\le 500\,{\rm km\,s^{-1}}$ with respect to the absorbers. We report our results in Fig. [5](#fig:abs_line). We found that $100\%$ of our ALMA-selected galaxies – for which robust spectroscopic redshifts are available – are unambiguously associated with metal absorbers. This detection rate decreases to $\ge85\%$ when considering the uncertainties related to source C5 (see Sect. [4.4](#ssect:hst_counterparts) for details). Indeed, if we adopt the tentative redshift of C5 measured from the low-quality MUSE spectrum ($z\approx 2.47$), we find no connected absorbers for this source. For comparison, we found that only $\approx 25\%$ of all spectroscopically confirmed HST-selected galaxies with $\log M_\star/M_{\astrosun}\ge 8$ are associated with absorbers, increasing to $\approx 45\%$ considering galaxies with $\log M_\star/M_{\astrosun}\ge 10$. Therefore, the association rate for galaxies selected in their rest-frame optical/UV is much lower than that observed for on-average more massive galaxies selected with ALMA in their dust continuum (see, Sect [5.2](#ssect:gal_prop)).

Interestingly, we note that three out of the six sources (i.e., C1, C3, C4) for which we find a robust association to absorbers would have been missed if only relying on MUSE and HST identifications. Indeed, such sources are the faintest among the NIR/optical counterparts (see Table [\[tbl:1.2mm_cand\]](#tbl:1.2mm_cand)) and lie in the MUSE redshift desert. This implies that studies limited to optical wavelengths may miss a significant fraction of the galaxy population around metal absorbers, as also highlighted in previous works (cite: Neeleman+2017; Neeleman+2018; Neeleman+2019; Fynbo+2018; Galbiati+2024). Moreover, as the case of C4 exemplifies, ALMA is critical to identify the only galaxy we can associate with the QSO-NW absorber at $z=2.368$, as no other galaxies were previously known at this redshift through MUSE and HST (see, Fig. [5](#fig:abs_line)).

We evaluated the number density of our ALMA-selected galaxies by computing the completeness-corrected 1.2-mm number counts and found that these are consistent with that derived in blank field from ASPECS (cite: Gonzalez-Lopez+2020). In light of the above considerations, we conclude that, since obscured massive galaxies selected with ALMA have sufficient number density to be relevant in absorption line studies, blind (sub-)millimeter follow-ups of optical/NIR surveys are thus essential in providing the most complete view of the galaxy population residing around absorbers.

## Properties of the ALMA galaxies around absorbers

In Fig. [6](#fig:main_seq), we compare the stellar mass and SFR of the dusty galaxies detected with ALMA (see Appendix [7](#app:sed) for full details) to the rest of the optical/UV-selected galaxy population in the MUDF and the sample of submillimeter galaxies (SMG) from (cite: Dudzeviciute+2020) at $z\sim 1-2.5$. The ALMA sources lie at the high-mass end of the stellar mass function at those redshifts and are among the most massive members of the groups in which they reside (see Sect. [5.3](#ssect:groups)). On the other hand, our ALMA galaxies appear to be less massive, but within in the scatter of the population of coeval SMGs, lying on the asymptotic part of the main sequence at $z\simeq 1-2$ (cite: Popesso+2023), although close to the starburst region.

![](figs/main_seq_del_exp.pdf)

Using our measurements of the galaxy flux density at 1.2 mm on the Rayleigh-Jeans tail of the dust SED, we provide rough estimates of the dust masses ($M_{\rm dust}$) of ALMA continuum-selected galaxies (excluding C5 for which we do not have reliable redshift measurement, and C2 that is the QSO-SE). By following a typical approach adopted in (sub-)millimeter studies of high-$z$ galaxies (cite: Casey+2012; Riechers+2013; Faisst+2020), we employ a single modified black-body emission assuming a characteristic dust temperature of $T_{\rm dust}=32\,{\rm K}$, and emissivity index $\beta=1.8$ typical of SMGs (cite: Dudzeviciute+2020), and we find values in the range $\log\,(M_{\rm dust}/M_{\astrosun})\simeq 8.0-8.6$. Using the same assumptions, we find a lower value of $\log\,(M_{\rm dust}/M_{\astrosun})\simeq 7.8$ for C7, which appears to be more similar to typical main-sequence galaxies. By integrating the black-body models we computed the IR luminosities and converted them to ${\rm SFR}_{\rm IR}$ using the calibration from (cite: Murphy+2011), and find values in the range $\log\,({\rm SFR}_{\rm IR}/M_{\astrosun}\,{\rm yr^{-1}})\simeq1.6-2.4$, comparable to those we derived from galaxy SED modeling (see Table [2](#tbl:sed_fit)).

From the CO(3–2) emission line in C1, C3, C4, and the \[C\]$_{\rm 609\,\mu m}$ line detected in C6 (see, Sect. [4.2](#ssect:line_selected_sources)), we derive estimates of galaxy molecular gas fractions. For C1, C3, and C4 we adopt a CO(3–2)-to-CO(1–0) conversion factor of $r_{31}=0.80\pm0.14$ from (cite: Boogaard+2020) and a range of $\alpha_{\rm CO}$. At the lower end, we use a value of $0.8\,M_{\astrosun}/({\rm K\,km\,s^{-1}\,pc^2)}$, typical of SGMs and quasar hosts (cite: Downes+1998). At the upper end, we adopt $4.3\,M_{\astrosun}/({\rm K\,km\,s^{-1}\,pc^2)}$ as measured in giant molecular clouds in the Milky Way (cite: Bolatto+2013; CarilliWalter2013). For C6, we first derive atomic carbon mass from equation 2 in (cite: Weiss+2005) and we convert it to molecular gas mass by assuming a C-to-H$_2$ abundance ratio of $X{\rm [CI]}/X{\rm [H_2]}=M_{\rm CI}/(6M_{\rm H_2})=(8.4\pm3.5)\times10^{-5}$, as derived by (cite: Walter+2011) for a sample of $z\sim 2-3$ FIR-bright sources. By employing such recipes, we find $f_{\rm gas}=M_{\rm H_2}/(M_{\rm H_2}+M_\star)=51^{+14}_{-17}\%$, $24^{+15}_{-10}\%$, $20^{+12}_{-9}\%$, and $65^{+10}_{-12}\%$ for C1, C3, C4, and C6 respectively. These values are scattered in the typical range observed in both main-sequence galaxies and ULIRGs/SMGs at $z\gtrsim1$ (cite: Tacconi+2018; Birkin+2021). Interestingly, we note that C1 and C6 exhibit high values of the gas fraction and also live in rich groups (see, Sect. [5.3](#ssect:groups)). This fact might suggest that efficient gas accretion is in place in these structures.

## The link between the large-scale galaxy environment and the absorbing gas

In Sect. [3.1](#ssect:hst_cat), we found that many HST-selected sources do not live in isolation but are associated with galaxy groups instead. In Fig. [7](#fig:hst_groups), we show that four (out of six) of our dusty galaxies (i.e., C1, C3, C6, and C7) detected with ALMA actually live in such overdense regions[^8]. This is also evident from Fig. [5](#fig:abs_line), in which multiple galaxies selected in HST are found to be associated with the same absorbers as those identified around ALMA galaxies. The high association rate between galaxies in groups and absorbers has also been found in previous works (cite: Nielsen+2018; Dutta+2020; Hamanowicz+2020; Lofthouse+2023; Qu+2023), suggesting that the large-scale environment plays a significant role in shaping the absorption properties. Indeed, these absorbers exhibit multiple components and are observed to be strong, showing typical rest-frame equivalent widths of ${\rm EW}_{\rm CIV} \gtrsim 0.3\,\AA{}$, ${\rm EW}_{\rm MgII}\gtrsim 1\,\AA{}$, and with complex kinematics. In particular, we note that dust-mass-selected sources living in groups of more than two galaxies (i.e., C1, C3, and C6) are associated to absorbers exhibiting high column density of $N_{\rm AlII,\,MgII}\apprge 10^{16}\,{\rm cm^{-2}}$, while C4, and C7 show significantly lower values of $N_{\rm CIV,\,MgII}\simeq 10^{13}-10^{14}\,{\rm cm^{-2}}$. Other works which studied quasar absorption around galaxy groups at different redshifts reported similar evidence (cite: Lan+2014; Fossati+2019; Dutta+2021; Nelson+2021; Galbiati+2023; Galbiati+2024).

We now turn to investigate the 3D separation between galaxies and the associated gas structures. The dusty galaxies selected with ALMA are more aligned in redshift space with the center of absorption features than the other connected galaxies. In particular, we find that C1 and C6, which are embedded in rich groups, are located in correspondence of the $50\%$ of the optical depth ($\tau_{50}$) of the associated absorbers (see, Fig. [5](#fig:abs_line)). Similarly, despite living in less overdense regions, we find that the remaining ALMA galaxies (i.e., C3, C4, and C7) lie within $100\,{\rm km\,s^{-1}}$ from $\tau_{50}$. This fact, in combination with their massive nature (see, Sect. [5.2](#ssect:gal_prop)), suggests that these galaxies sit close to the center of the potential well of their large-scale structures. While our ALMA-selected galaxies show preferential alignment with the quasar absorbers along the line of sight, this is not necessarily the case if we consider the sky-projected distances from the location of the quasars. The impact parameters are typically large, of the order of $\sim 200-400\,{\rm kpc}$ (see, Fig. [7](#fig:hst_groups)), compared to the other galaxies associated to the absorbers. Therefore, while (sub-)millimeter observations are critical to gain a complete view of the galaxy population and possibly the group potential well, our findings suggest that the absorbing gas may not be located in the inner CGM of the dusty galaxies but is still retained within a few virial radii[^9]. In this regard, massive dusty galaxies appear to be more tracers of the large scale structure than the actual hosts of the absorbers. However, we caution that this may also be a consequence of the low number density of these galaxies. More SMG-QSO pairs at small separations are needed to statistically assess our conclusions. We note that only one out of six detections, that is the source C3, lies both close to the center of the associated absorber in redshift space and at low impact parameter ($R=43\,{\rm kpc}$) from QSO-NW sightline, which points to a significant contribution from the CGM of this galaxy to the observed absorption profile. However, given that C3 belongs to a compact system of three sources all located within $100\,{\rm kpc}$, we cannot exclude that hydrodynamical and gravitational interactions may play an important role in shaping the properties of the surrounding gas (cite: Gunn+1972; Merritt+1983; Boselli+2006; Klitsch+2019).

![](figs/hst_groups_arrow_bar_2.pdf)

In light of the aforementioned considerations, the observed absorption profiles associated to groups could potentially arise from the superposition of the halos of multiple galaxies located around the massive sources identified with ALMA (cite: Bordoloi+2011; Nielsen+2018; Dutta+2020). Therefore, one might expect the strength of the absorption to correlate with the projected galaxy surface density (cite: Galbiati+2024). To test this hypothesis, we centered on the sky position and redshift of ALMA galaxies C1, C3, C6 and C7, and count the number of HST-selected sources within a velocity window of $\left | \Delta\varv \right |\le 250\,{\rm km\,s^{-1}}$ (chosen based on the broadest absorption system, see Fig. [5](#fig:abs_line)), and encompassed radius corresponding to the impact parameter from the QSO. We then divide the number of galaxies by the projected area corrected for the coverage of the MUSE FoV. In Fig. [8](#fig:sigma_ew), we report such galaxy surface density against the EW of the associated absorbers[^10]. As a result, we find a hint of positive correlation[^11], which is consistent with the scenario proposed above. In order to show the potential correlation, we fit the data with a linear model by employing the Python MCMC ensemble sampler `emcee` package (cite: Foreman+2013) adopting a Poisson maximum likelihood estimator and flat priors on the free parameters. In Fig. [8](#fig:sigma_ew), we report the best fit and $1\sigma$ confidence interval. However, we note that our analysis relies on a handful of sources and therefore is limited by the low statistics. Hence, surveys tailored to probe a broader range of galaxy overdensities around absorbers are required to draw more firm conclusions.

![](figs/sigma_ew_fit.pdf)

# Summary & Conclusions

In this work, we presented an ALMA blind dust continuum and molecular gas survey around the sightlines of the $z\approx3.22$ quasar pair in the MUDF. By combining our (sub-)millimeter observations with available multiwavelength data from NIR to UV, we investigated the role of the dusty galaxy population in association to the intervening gas structures revealed in absorption in the quasar spectra. Below, we summarize our main findings:

- We identified a robust sample of seven sources detected at 1.2-mm in their dust continuum with ALMA. We determined their spectroscopic redshift from either the inspection of their MUSE spectra or via the CO(3–2) line detected with ALMA band 3 spectral scans.

- We found that the dust-selected galaxies and metal absorbers are associated within $500\rm\,km\,s^{-1}$. This implies that at least $\ge 85\%$ of the dusty galaxies uncovered with ALMA are unambiguously linked to multiple absorption features arising from metal ions and observed in either of the quasar sigthlines. This association rate is significantly higher than in previous surveys at NIR–UV wavelengths.

- By combining multiband photometry and information about dust and molecular gas gathered from our (sub-)millimeter data, we investigated the nature of the ALMA-selected galaxies by performing SED modeling. As a result, most of these galaxies appear massive ($M_{\star}\simeq 10^{10.2-10.7}\,M_{\astrosun}$), highly star forming (${\rm SFR}\simeq 10^{1.2-2.0}\,M_{\astrosun}\,{\rm yr^{-1}}$), and exhibit high dust and molecular gas content ($M_{\rm dust}\simeq 10^{7.8-8.6}\,M_{\astrosun}$, $f_{\rm H2}\simeq 20 - 65\%$), resembling typical SMGs at similar redshifts.

- We discovered that a large fraction of ALMA-selected sources (4/6) live in galaxy groups in which they are among the most massive members. While the associated absorbers show complex kinematics, our galaxies are better aligned with the center of the absorption features than the other galaxies previously identified in the optical. This may suggest that these massive and dust-obscured galaxies sit close to the center of the gravitational potential well of their large-scale structures. However, the impact parameters of the ALMA galaxies are typically large, $\sim 200-400\,{\rm kpc}$, indicating that absorption probed by the QSO sightlines might originate within a few virial radii.

This study highlights the crucial role of (sub-)millimeter surveys to obtain a complete census of the galaxy population around metal enriched cosmic gas structures revealing the presence of massive and dust-obscured galaxies. However, further efforts are needed to understand which processes are responsible for distributing metals into the IGM and how different galaxy populations contribute to the metal enrichment across the cosmic time. Furthermore, denser surveys are required to statistically investigate in absorption the properties of the inner CGM gas at the interface with the ISM of dusty galaxies.

# Acknowledgements

This paper uses the following ALMA data: ADS/JAO.ALMA#2021.1.00285.S, ADS/JAO.ALMA#2023.1.00461.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Based on observations with the NASA/ESA Hubble Space Telescope obtained from the MAST Data Archive at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. Support for program Nos. 15637 and 15968 was provided through a grant from the STScI under NASA contract NAS5-26555. These observations are associated with program Nos. 6631, 15637, and 15968. The MUSE portion of this project has received funding from the European Research Council (ERC) under the European Union Horizon 2020 research and innovation program (grant agreement No. 757535) and by Fondazione Cariplo (grant No.2018-2329). This project was supported by the ERC Consolidator Grant 864361 (CosmicWeb) and by Fondazione Cariplo grant no. 2018-2329, 2020-0902. IRS acknowledges support from STFC (ST/X001075/1). This research made use of Astropy[^12], a community-developed core Python package for Astronomy (cite: AstropyI; AstropyII; AstropyIII), NumPy (cite: Numpy), SciPy (cite: Scipy), Matplotlib (cite: Matplotlib).

112 natexlab

(ref: AstropyIII) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: AstropyII) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: AstropyI) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Bacon+2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508

(ref: Bacon+2021) Bacon, R., Mary, D., Garel, T., et al. 2021, A&A, 647, A107

(ref: Banerjee+2023) Banerjee, E., Muzahid, S., Schaye, J., Johnson, S. D., & Cantalupo, S. 2023, MNRAS, 524, 5148

(ref: Beckett+2024) Beckett, A., Rafelski, M., Revalski, M., et al. 2024, arXiv e-prints, arXiv:2408.11914

(ref: Birkin+2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926

(ref: Bolatto+2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Boogaard+2020) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: Bordoloi+2011) Bordoloi, R., Lilly, S. J., Knobel, C., et al. 2011, ApJ, 743, 10

(ref: Borisova+2016) Borisova, E., Cantalupo, S., Lilly, S. J., et al. 2016, ApJ, 831, 39

(ref: Boselli+2006) Boselli, A. & Gavazzi, G. 2006, PASP, 118, 517

(ref: Brammer+2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: Bruzual+2003) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Byler+2018) Byler, N., Dalcanton, J. J., Conroy, C., et al. 2018, ApJ, 863, 14

(ref: Calzetti+2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Cantalupo+2017) Cantalupo, S. 2017, in Astrophysics and Space Science Library, Vol. 430, Gas Accretion onto Galaxies, ed. A. Fox & R. Davé, 195

(ref: CarilliWalter2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Casey+2012) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chen+2010a) Chen, H.-W., Helsby, J. E., Gauthier, J.-R., et al. 2010a, ApJ, 714, 1521

(ref: Chen+2010b) Chen, H.-W., Wild, V., Tinker, J. L., et al. 2010b, ApJL, 724, L176

(ref: Coppin+2006) Coppin, K., Chapin, E. L., Mortier, A. M. J., et al. 2006, MNRAS, 372, 1621

(ref: Cupani+2016) Cupani, G., D’Odorico, V., Cristiani, S., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9913, Software and Cyberinfrastructure for Astronomy IV, ed. G. Chiozzi & J. C. Guzman, 99131T

(ref: Dale+2014) Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, ApJ, 784, 83

(ref: Decarli+2019c) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: Dekker+2000) Dekker, H., D’Odorico, S., Kaufer, A., Delabre, B., & Kotzlowski, H. 2000, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4008, Optical and IR Telescope Instrumentation and Detectors, ed. M. Iye & A. F. Moorwood, 534–545

(ref: Downes+1998) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: Dudzeviciute+2021) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2021, MNRAS, 500, 942

(ref: Dudzeviciute+2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828

(ref: Dutta+2021) Dutta, R., Fumagalli, M., Fossati, M., et al. 2021, MNRAS, 508, 4573

(ref: Dutta+2020) Dutta, R., Fumagalli, M., Fossati, M., et al. 2020, MNRAS, 499, 5022

(ref: Dutta+2024b) Dutta, R., Fumagalli, M., Fossati, M., et al. 2024, arXiv e-prints, arXiv:2409.02182

(ref: Ester+1996) Ester, M., Kriegel, H.-P., Sander, J., & Xu, X. 1996, in Second International Conference on Knowledge Discovery and Data Mining (KDD’96). Proceedings of a conference held August 2-4, 226–331

(ref: Faisst+2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: Foreman+2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306

(ref: Fossati+2019b) Fossati, M., Fumagalli, M., Gavazzi, G., et al. 2019a, MNRAS, 484, 2212

(ref: Fossati+2019) Fossati, M., Fumagalli, M., Lofthouse, E. K., et al. 2019b, MNRAS, 490, 1451

(ref: Fossati+2018) Fossati, M., Mendel, J. T., Boselli, A., & et al. 2018, A&A, 614

(ref: Fumagalli+2016) Fumagalli, M., O’Meara, J. M., & Prochaska, J. X. 2016, MNRAS, 455, 4100

(ref: Fynbo+2018) Fynbo, J. P. U., Heintz, K. E., Neeleman, M., et al. 2018, MNRAS, 479, 2126

(ref: Galbiati+2024) Galbiati, M., Dutta, R., Fumagalli, M., Fossati, M., & Cantalupo, S. 2024, A&A, 690, A7

(ref: Galbiati+2023) Galbiati, M., Fumagalli, M., Fossati, M., et al. 2023, MNRAS, 524, 3474

(ref: Gehrels1986) Gehrels, N. 1986, ApJ, 303, 336

(ref: Gonzalez-Lopez+2017) González-López, J., Bauer, F. E., Romero-Cañizales, C., et al. 2017, A&A, 597, A41

(ref: Gonzalez-Lopez+2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: Gonzalez-Lopez+2020) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91

(ref: Gunn+1972) Gunn, J. E. & Gott, J. Richard, I. 1972, ApJ, 176, 1

(ref: Hamanowicz+2020) Hamanowicz, A., Péroux, C., Zwaan, M. A., et al. 2020, MNRAS, 492, 2347

(ref: Numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Hennawi+2013) Hennawi, J. F. & Prochaska, J. X. 2013, ApJ, 766, 58

(ref: Hickox+2012) Hickox, R. C., Wardlow, J. L., Smail, I., et al. 2012, MNRAS, 421, 284

(ref: Hogg+1998) Hogg, D. W. & Turner, E. L. 1998, PASP, 110, 727

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science Engineering, 9, 90

(ref: Hunter+2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023a, PASP, 135, 074501

(ref: Hunter+2023b) Hunter, T. R., Petry, D., Barkats, D., Corder, S., & Indebetouw, R. 2023b, analysisUtils

(ref: Kanekar+2018) Kanekar, N., Prochaska, J. X., Christensen, L., et al. 2018, ApJL, 856, L23

(ref: Kanekar+2020) Kanekar, N., Prochaska, J. X., Neeleman, M., et al. 2020, ApJL, 901, L5

(ref: Kashino+2023) Kashino, D., Lilly, S. J., Simcoe, R. A., et al. 2023, Nature, 617, 261

(ref: Kaur+2022) Kaur, B., Kanekar, N., Rafelski, M., et al. 2022a, ApJL, 933, L42

(ref: Kaur+2022b) Kaur, B., Kanekar, N., Revalski, M., et al. 2022b, ApJ, 934, 87

(ref: Klitsch+2018) Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2018, MNRAS, 475, 492

(ref: Klitsch+2019) Klitsch, A., Zwaan, M. A., Péroux, C., et al. 2019, MNRAS, 482, L65

(ref: Lan+2014) Lan, T.-W., Ménard, B., & Zhu, G. 2014, ApJ, 795, 31

(ref: Leclercq+2022) Leclercq, F., Verhamme, A., Epinat, B., et al. 2022, A&A, 663, A11

(ref: Lim+2020) Lim, C.-F., Chen, C.-C., Smail, I., et al. 2020, ApJ, 895, 104

(ref: Lofthouse+2023) Lofthouse, E. K., Fumagalli, M., Fossati, M., et al. 2023, MNRAS, 518, 305

(ref: Longobardi+2023) Longobardi, A., Fossati, M., Fumagalli, M., et al. 2023, RAS Techniques and Instruments, 2, 470

(ref: Lusso+2019) Lusso, E., Fumagalli, M., Fossati, M., et al. 2019, MNRAS, 485, L62

(ref: McMullin+2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Data Analysis Software and Systems XVI, Vol. 376, 127

(ref: Merritt+1983) Merritt, D. 1983, ApJ, 264, 24

(ref: Moller+2018) Møller, P., Christensen, L., Zwaan, M. A., et al. 2018, MNRAS, 474, 4039

(ref: Moster+2010) Moster, B. P., Somerville, R. S., Maulbetsch, C., et al. 2010, ApJ, 710, 903

(ref: Murphy+2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: Neeleman+2019) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10

(ref: Neeleman+2018) Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2018, ApJL, 856, L12

(ref: Neeleman+2017) Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2017, Science, 355, 1285

(ref: Nelson+2021) Nelson, D., Byrohl, C., Peroux, C., Rubin, K. H. R., & Burchett, J. N. 2021, MNRAS, 507, 4445

(ref: Nielsen+2018) Nielsen, N. M., Kacprzak, G. G., Pointon, S. K., Churchill, C. W., & Murphy, M. T. 2018, ApJ, 869, 153

(ref: Oppenheimer+2012) Oppenheimer, B. D., Davé, R., Katz, N., Kollmeier, J. A., & Weinberg, D. H. 2012, MNRAS, 420, 829

(ref: Pacifici+2023) Pacifici, C., Iyer, K. G., Mobasher, B., et al. 2023, ApJ, 944, 141

(ref: Pavesi+2018) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: Pedregosa+2011) Pedregosa, F., Varoquaux, G., Gramfort, A., et al. 2011, Journal of Machine Learning Research, 12, 2825

(ref: Peroux+2020) Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363

(ref: Peroux+2019) Péroux, C., Zwaan, M. A., Klitsch, A., et al. 2019, MNRAS, 485, 1595

(ref: PlanckColl+2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Popesso+2023) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526

(ref: Qu+2023) Qu, Z., Chen, H.-W., Rudie, G. C., et al. 2023, MNRAS, 524, 512

(ref: Revalski+2023) Revalski, M., Rafelski, M., Fumagalli, M., et al. 2023, ApJS, 265, 40

(ref: Revalski+2024) Revalski, M., Rafelski, M., Henry, A., et al. 2024, ApJ, 966, 228

(ref: Riechers+2013) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Sanchez+2022) Sánchez, S. F., Barrera-Ballesteros, J. K., Lacerda, E., et al. 2022, ApJS, 262, 36

(ref: Schroetter+2021) Schroetter, I., Bouché, N. F., Zabl, J., et al. 2021, MNRAS, 506, 1355

(ref: Schroetter+2024) Schroetter, I., Bouché, N. F., Zabl, J., et al. 2024, A&A, 687, A39

(ref: Scott+2002) Scott, S. E., Fox, M. J., Dunlop, J. S., et al. 2002, MNRAS, 331, 817

(ref: Solomon+1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144

(ref: Spearman1904) Spearman, C. 1904, The American Journal of Psychology, 15, 72

(ref: Stach+2021) Stach, S. M., Smail, I., Amvrosiadis, A., et al. 2021, MNRAS, 504, 172

(ref: Steidel+2010) Steidel, C. C., Erb, D. K., Shapley, A. E., et al. 2010, ApJ, 717, 289

(ref: Szakacs+2021) Szakacs, R., Péroux, C., Zwaan, M., et al. 2021, MNRAS, 505, 4746

(ref: Tacconi+2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tornotti+2024) Tornotti, D., Fumagalli, M., Fossati, M., et al. 2024, arXiv e-prints, arXiv:2406.17035

(ref: Tumlinson+2017) Tumlinson, J., Peeples, M. S., & Werk, J. K. 2017, ARA&A, 55, 389

(ref: Umehata+2019) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: Scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Walter+2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: Walter+2011) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, ApJ, 730, 18

(ref: Weiner+2009) Weiner, B. J., Coil, A. L., Prochaska, J. X., et al. 2009, ApJ, 692, 187

(ref: Weiss+2005) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25

(ref: Wilkinson+2017) Wilkinson, A., Almaini, O., Chen, C.-C., et al. 2017, MNRAS, 464, 1380

(ref: Zabl+2019) Zabl, J., Bouché, N. F., Schroetter, I., et al. 2019, MNRAS, 485, 1961

# Spectral Energy Distribution of the ALMA-selected galaxies

We derived properties of our ALMA-selected galaxies with secure photometric measurements (i.e., excluding C2 that is QSO-SE, and C5; see Sect. [4.4](#ssect:hst_counterparts)), such as $M_{\star}$, SFR, and visual extinction ($A_{\rm V}$) by performing simultaneous fit of multiwavelength photometry and MUSE spectra. The photometry includes custom MUSE top-hat filters, covering $4750\,\AA$ to $9300\,\AA$ (as described in table 2 in (cite: Fossati+2019)), multiple UV to NIR HST filters (WFC3/F140W, F125W, and WFPC2/F450W, F702W, see (cite: Revalski+2023)), VLT/HAWK-I Ks filter (cite: Revalski+2024), and 1.2-mm flux from ALMA band 6 observations.

We used the Monte Carlo Spectro-Photometric Fitter (MC-SPF, (cite: Fossati+2018; Fossati+2019b)) code. We built a grid of stellar spectra based on the updated version of the (cite: Bruzual+2003) high-resolution models at $40\%$ solar metallicity, assuming a (cite: Chabrier2003) initial mass function and a delayed exponentially declining star formation history[^13]. We scaled a grid of nebular emission lines models from (cite: Byler+2018) to the number of Lyman continuum photons from the stellar models, converted it into flux at the redshift of the galaxies and then added to templates. To include the effect of dust attenuation on both the stellar continuum and the nebular emission lines, we assumed the double attenuation law from (cite: Calzetti+2000), which accounts for extra extinction of the young stars compared to those older than $10\,{\rm Myr}$. During the fitting procedure, we impose an energy balance between the UV flux from young stars that is absorbed by dust grains and re-emitted at FIR wavelengths. We used the dust emission model from (cite: Dale+2014). We report best-fit results from SED modeling in Fig. [9](#fig:gal_seds) and Table [2](#tbl:sed_fit).

![](figs/gal_seds_final_tdust.pdf)

|  |  |  |  |
|:---|:--:|:--:|:--:|
| ID$_{\rm 1.2mm}\,^{(1)}$ | ${\rm log} \,M_{\star}\,^{(2)}$ | ${\rm \log SFR}\,^{(3)}$ | $A_V\,^{(4)}$ |
|  | ($M_{\astrosun}$) | ($M_{\astrosun}\,{\rm yr^{-1}}$) | (mag) |
| 1-4 C1 | $10.7\pm0.2$ | $1.8\pm0.3$ | $1.86\pm0.18$ |
| C3 | $10.8\pm0.2$ | $1.8\pm0.3$ | $1.77\pm0.08$ |
| C4 | $10.9\pm0.2$ | $2.0\pm0.3$ | $1.99\pm0.06$ |
| C6 | $10.6\pm0.2$ | $1.9\pm0.3$ | $3.25\pm0.14$ |
| C7 | $10.2\pm0.2$ | $1.2\pm0.3$ | $0.58\pm0.02$ |

: Results from SED fitting of the ALMA-selected galaxies.

Table notes: $^{(1)}$Identifier of ALMA 1.2-mm continuum-selected galaxies. $^{(2)}$Logarithm of the stellar mass. $^{(3)}$Logarithm of the star-formation rate. $^{(4)}$Visual extinction. Statistical uncertainties on measurements are estimated from the 16th and 84th percentiles of the parameter posterior probability distribution. Uncertainties on $M_\star$ and SFR are reported after adding in quadrature 0.3 and 0.2 dex, respectively, to account for systematics (cite: Pacifici+2023; Beckett+2024).

[^1]:

[^2]: ; second author with equal contribution.

[^3]: The final products can be retrieved as High Level Science Products (HLSPs) at `doi:`[10.17909/81fp-2g44](https://doi.org/10.17909/81fp-2g44), together with the default data files at `doi:`[10.17909/q67p-ym16](https://doi.org/10.17909/q67p-ym16) from the Mikulski Archive for Space Telescopes (MAST). The dedicated page to the MUDF program is available at <https://archive.stsci.edu/hlsp/mudf>.

[^4]: The code is publicly available at [https:// github.com/jigonzal/LineSeeker](https:// github.com/jigonzal/LineSeeker). Other similar source-finding codes are available in the literature, such as FindClumps (cite: Walter+2016) or MF3D (cite: Pavesi+2018), which differ mainly in details about the adopted spectral filter function. However, comparisons between codes have yielded very similar results (cite: Gonzalez-Lopez+2019).

[^5]: This algorithm is included within the Python package Scikit-learn (cite: Pedregosa+2011).

[^6]: Higher-$J$ CO transitions are covered for $z>3.5$ by our ALMA band 6 spectral tunings.

[^7]: We derived photometric redshifts of C1, C3 and C4 from multiband photometry as detailed in Sect. [2](#sect:data-red), obtaining $z_{\rm phot} = 2.21\pm0.19$, $2.51\pm0.07$, $2.44\pm0.17$, respectively, where nominal values and uncertainties are computed from the expected value and variance of the photo-$z$ posteriors.

[^8]: From the total stellar mass of the groups we estimated the dark matter halo masses of the systems in which ALMA galaxies reside by employing the stellar-to-halo mass relation from (cite: Moster+2010), and obtain an average halo mass of $\sim 10^{13}\,M_{\astrosun}$. This is comparable to previous estimates of the halo mass of SMGs at $z>1$ from clustering analysis (cite: Hickox+2012; Wilkinson+2017; Lim+2020; Stach+2021).

[^9]: The virial radius for a halo mass of $10^{13}\,M_{\astrosun}$, typical of the ALMA-selected galaxies (cite: Stach+2021) according to (cite: Moster+2010), is $\approx310$ and $220\,{\rm kpc}$ at $z=1$ and 2, respectively.

[^10]: We used Mg II for C1, C6, and C7, and Al II for C3, since we have no Mg II detection for this source. These are chosen as they have similar $f_{\rm osc}\lambda_{\rm rest}^{2}$, where $f_{\rm osc}$ is the oscillator strength, and $\lambda_{\rm rest}^{2}$ is the rest-frame wavelength of the transitions. However, we caution that due to the differences in the relative abundances, at fixed EW different ions do not trace the same gas density.

[^11]: The Spearman’s rank correlation test (cite: Spearman1904) yields a degree of monotonic correlation of $\rho=0.8$ with a $p$-value $0.1$, indicating that a positive correlation is in place at $80\%$ confidence level.

[^12]: <http://www.astropy.org>

[^13]: The set of models is publicly available at <http://www.bruzual.org/CB19/>. A detailed description is provided in appendix A of (cite: Sanchez+2022).

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Run LineSeeker on the untapered dirty 1.2-mm continuum image (PB response >= 50%, no PB correction), extract S/N>3 detections, keep fidelity F >= 90% (S/N >= 5.0); fidelity from negative-peak statistics",
  "failed_quote": "the ratio between positive and negative detections distributions is used to estimate the fidelity (or reliability) of source candidates"
 }
]
```
