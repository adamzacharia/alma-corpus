# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.510.3734D\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# A High-Resolution Investigation of the Multi-Phase ISM in a Galaxy during the First Two Billion Years

[^1]: E-mail: simon.dye@nottingham.ac.uk

# Abstract

We have carried out the first spatially-resolved investigation of the multi-phase interstellar medium (ISM) at high redshift, using the $z=4.24$ strongly-lensed sub-millimetre galaxy H-ATLASJ142413.9$+$022303 (ID141). We present high-resolution (down to $\sim$350 pc) ALMA observations in dust continuum emission and in the CO(7-6), $\rm H_2O (2_{1,1} - 2_{0,2})$, \[ C i \] (1-0) and \[ C i \] (2-1) lines, the latter two allowing us to spatially resolve the cool phase of the ISM for the first time. Our modelling of the kinematics reveals that the system appears to be dominated by a rotationally-supported gas disk with evidence of a nearby perturber. We find that the \[ C i \] (1-0) line has a very different distribution to the other lines, showing the existence of a reservoir of cool gas that might have been missed in studies of other galaxies. We have estimated the mass of the ISM using four different tracers, always obtaining an estimate in the range $\rm 3.2-3.8 \times 10^{11}\ M_{\odot}$, significantly higher than our dynamical mass estimate of $\rm 0.8-1.3 \times 10^{11}\ M_{\odot}$. We suggest that this conflict and other similar conflicts reported in the literature is because the gas-to-tracer ratios are $\simeq$4 times lower than the Galactic values used to calibrate the ISM in high-redshift galaxies. We demonstrate that this could result from a top-heavy initial mass function and strong chemical evolution. Using a variety of quantitative indicators, we show that, extreme though it is at $z=4.24$, ID141 will likely join the population of quiescent galaxies that appears in the Universe at $z\sim 3$.

galaxies: ISM – galaxies: kinematics and dynamics – galaxies: star formation – submillimetre: galaxies – gravitational lensing: strong

# Introduction

Sub-millimetre galaxies (SMGs) are among the brightest objects observed at far-infrared (far-IR) and sub-millimetre (submm) wavelengths in the early universe. SMGs are typically highly optically-obscured by dust that originates from low/intermediate mass stars and supernovae (cite: rowlands2014) in regions undergoing extreme rates of star formation. These stellar nurseries are most abundant at redshifts around $z=2-4$ when the Universe was most rapidly forming the galaxies and clusters we see around us today. SMGs have therefore become a valuable probe of the physics of the growth of these structures, particularly at the more massive end of the galaxy mass function (cite: casey2014; hodge2020).

The most extreme SMGs are those discovered in the wide-area surveys carried out with *Herschel* (cite: negrello2017; bakx2018), the South Pole Telescope (cite: vieira2013; reuter2020) and *Planck* (cite: canameras2015), including ones that have star-formation rates many thousands of solar masses per year, which have been found out to a redshift of $\sim6$ (cite: fudamoto2017). An obvious question is, what do these extreme objects evolve into at more recent epochs? In particular, do these galaxies evolve into the population of quiescent galaxies that appear in the Universe at $z \sim 3$? (cite: glazebrook2017; girelli2019; valentino2020; forrest2020a; forrest2020b; merlin2019).

These huge star-formation rates must be fueled by large amounts of gas and many studies have found that SMGs house substantial molecular gas reservoirs of masses generally in the range $10^{10}-10^{11}\,{\rm M}_\odot$ (cite: ivison2011; bothwell2013; huynh2017; dye2018; kaasinen2019). The bulk constituent of this gas, molecular hydrogen, is not rotationally excited at the typical temperatures in the molecular phase in galaxies. As such, investigations have been forced to use tracers, either dust or a variety of molecular and atomic species, thus requiring knowledge of the gas-to-tracer ratio. There is a complex hierarchy of calibrations but most of the values assumed for these ratios are ultimately based on observations in the Milky Way, the only place where it is possible to measure both the luminosity in the tracer and the mass of the underlying gas (cite: dunne2021a).

As for galaxies in the nearby Universe, the most frequently used tracer of the molecular phase of the ISM, because it has so many bright spectral lines in atmospheric windows, is the CO molecule (cite: tacconi2018; birkin2021). As a tracer of the underlying gas, CO has some well known disadvantages (cite: bolatto2013), in particular the fact that the J=1-0 line, the best for tracing the coldest gas, is optically thick. In addition, observations with *Fermi* (cite: abdo2010), *Planck* (cite: planck2011) and *Herschel* (cite: pineda2013) all suggest that approximately one third of the molecular gas in the Galaxy does not emit CO, probably because of photo-dissociation of the CO molecule (cite: planck2011). For high-resolution studies of the ISM in high-redshift galaxies there is the additional problem that the Atacama Large Millimetre Array (ALMA) is only able to observe the higher-excitation CO lines, making it possible that these studies have missed much of the gas (although lower-frequency ALMA bands will become available in the near future).

The other bright molecular lines in high-redshift galaxies are those of the water molecule, which have been used to observe both SMGs (cite: omont2013; spilker2014; yang2016; jarugula2019) and AGN (cite: vanderwerf2011). The water lines are excited by far-IR photons (compared to collisional excitations of CO by H$_2$), explaining the correlation between line luminosity and far-infrared luminosity over three orders of magnitude (cite: yang2013). The water lines are therefore probably more useful as a tracer of star formation than the ISM (cite: jarugula2019).

Arguably the best tracers of the molecular phase of the ISM in high-redshift galaxies are the fine-structure lines of atomic carbon, despite being generally fainter. The \[ C i \] ($^3P_1-^3P_0$) and \[ C i \] ($^3P_2-^3P_1$) lines have similar excitation temperatures and critical densities to the low-J CO lines, but they are optically thin and they are emitted in all molecular regions including CO-dark regions (cite: papadop2004; papadop2004b; dunne2021a).

The high-resolution configurations of ALMA, plus the magnification (often greater than a factor of 10) provided by gravitational lensing, have huge potential for investigating the physical conditions in the ISM in galaxies in the early Universe. This potential has been demonstrated quite dramatically using observations of the gravitationally-lensed SMG SDP81 that were carried out in the Science Verification Phase of the ALMA long baselines (cite: vlahakis2014). After being corrected for gravitational lens distortion, the reconstructed spectral-line and continuum images had a resolution of $\sim$50 pc (cite: dye2015; rybak2015a; rybak2015b). The images revealed a smoothly-rotating but clumpy disk, with a Toomre Q-parameter suggesting that the disk is in a state of collapse. The resolution, approximately the size of a giant molecular cloud, made it possible to compare the Larson relations for the clumps with those in the Milky Way (cite: swinbank2015).

The drawback of the observations of SDP81, however, is that they were in high-J CO lines, making it uncertain whether a cool molecular phase had been missed; it is possible that these high-J CO clumps simply trace regions in the disk where the gas is particularly warm rather than genuine agglomerations of gas. In addition, at the redshift of SDP81, several spectral lines do not fall within atmospherically-transparent windows. To circumvent these shortfalls, we have therefore embarked on a second high-resolution study of the ISM using a galaxy at a redshift such that all of the key spectral lines are visible to ALMA.

One of the brightest strongly-lensed SMGs, H-ATLAS J$142413.9+022303$, hereafter referred to as ’ID141’ following its label assigned by (cite: cox2011) was discovered in the *Herschel* Astrophysical Terrahertz Large-Area Survey (cite: eales2010; cox2011; negrello2017). ID141 is not only bright because it is strongly-lensed but also because it is intrinsically very luminous. After correction for the lens magnification factor of $\sim 6$, the star-formation rate in ID141, estimated from the bolometric luminosity of the dust (cite: kroupa2003), is $\rm \simeq 2400\ M_{\odot}\ yr^{-1}$, five times higher than SDP81. With a redshift of $z=4.24$ (cite: cox2011), ID141 is also one of the most distant strongly-lensed SMGs. At this redshift, both \[ C i \] lines, the bright \[ C ii \]  line at 158 $\mu$m, multiple CO lines (including the CO(1-0) line in the near future) and water lines, and many other lines are visible to ALMA.

As a result of its interest, ID141 has been observed many times in the submillimetre/millimetre wavebands (cite: cox2011; bussmann2012; bussmann2013; omont2013; dye2018; cheng2020). Lens modelling by (cite: dye2018) and (cite: enia2018) revealed evidence of a disturbed morphology in the reconstructed continuum emission of the source (see also (cite: bussmann2012) who showed that significant image residuals remain after subtracting the best fit lensed image of a single smooth source). A relatively high level of ionisation in the source was inferred from a high far-IR luminosity to gas mass ratio measured by (cite: cox2011). This, along with very large line widths of $\sim 800$ km s$^{-1}$ observed in CO emission led the authors to suggest the SMG is a merger, like most other SMGs (cite: engel2010).

In this paper, we present high-resolution ($\sim 0.1$ arcsec) ALMA observations of ID141 in bands 3 and 4, complementing the ALMA band 7 observations presented in D18. The new observations cover the emission lines CO(7-6), $\rm H_2O (2_{1,1} - 2_{0,2})$, \[ C i \] ($^3P_2-^3P_1$) and \[ C i \] ($^3P_1-^3P_0$), which have for the first time made it possible to carry out a high-resolution investigation of the ISM in a high-redshift galaxy that includes both the warm and the cool gas. The spectral-line observations have also allowed us to make a detailed kinematic analysis of this system, in particular addressing the question of whether ID141 is a merger.

One of the key findings of this paper is that the dynamical mass of ID141 is approximately four times lower than the gas mass inferred from Galactic gas-to-tracer ratios. SMGs with inferred gas masses that are equal to or larger than their dynamical mass have been reported in the literature for over a decade (cite: Tacconi2008; hodge2012; bothwell2013). More recently, there has been an acceleration in the prevalence of such conflicting systems (cite: dye2015; yang2017; rivera2018; neeleman2020; mizukoshi2021). A common approach to reconcile these anomalies is to reduce the conversion factor (based on local Universe observations) that scales CO line intensity to total gas mass. In this work, we find that four different tracers yield the same excessive gas mass. It is unlikely that all four tracer conversion factors would need to be scaled by the same amount and so we have sought a more natural explanation in the form of a chemical evolution model which solves the discrepancy between the gas mass and dynamical mass in ID141.

The layout of this paper is as follows. In Section [2](#sec_data) we describe the acquisition and the reduction of the ALMA data. Section [3](#sec_lens) presents our lens modelling and source reconstruction. Section [4](#sec_src) describes our investigation of the basic properties of the source, including the kinematic modelling and estimates of the mass of the ISM in the galaxy made five different ways. We discuss our findings in Section [\[sec_discussion\]](#sec_discussion) and introduce a chemical evolution model of ID141. Section [\[sec_summary\]](#sec_summary) is a summary of both our basic observational results and inferences from these results. Throughout this work, we have adopted the flat cosmological model with parameters $h=0.678$, $\Omega_{\rm m}=0.308$ and $\Omega_\Lambda=0.692$ (cite: planck2016).

# Data Acquisition and Processing

The ALMA data analysed in this paper were acquired under two separate ALMA programmes. The first, 2016.1.00450.S, obtained band 4 spectral imaging on 20th August 2017 in four spectral windows (SPWs) centred on the frequencies 141.2, 143.1, 153.3 and 154.9 GHz, each with bandwidths of approximately 2 GHz. The total on-source integration time was 2360s using 44 12m antennas giving a spatial resolution of 0.15 arcsec, a maximum recoverable scale of 2.1 arcsec and a sensitivity of 0.34 mJy beam$^{-1}$ assuming 10 km s$^{-1}$ channels.

The second programme, 2017.1.00029.S, obtained band 3 spectral imaging on the 14th and 16th of November 2017 when 46 and 44 12m antennas were used respectively. Combining the measurement sets from both dates, the resulting images have a spatial resolution of 0.11 arcsec, a maximum recoverable scale of 2.0 arcsec and a sensitivity of 0.56 mJy beam$^{-1}$ assuming 10 km s$^{-1}$ channels. These observations were again carried out in four SPWs with central frequencies of 93.9, 95.8, 105.8 and 107.7 GHz with bandwidths of $\sim$2 GHz and with a total on-source integration time of 3560s. This configuration of SPWs was chosen specifically to target the emission lines of CO, H$_2$O and \[ C i \] (see below). Table [1](#tab_alma_obs) gives more specific details on the spectral set up.

| Band | $\nu_{\rm cent}$ (GHz) | BW (MHz) | $N_{\rm chan}$ |
|:----:|:----------------------:|:--------:|:--------------:|
|  3   |          93.9          |   1875   |      3840      |
|  3   |          95.8          |   2000   |      128       |
|  3   |         105.8          |   1875   |      3840      |
|  3   |         107.7          |   2000   |      128       |
|  4   |         141.2          |   2000   |      128       |
|  4   |         143.1          |   2000   |      128       |
|  4   |         153.3          |   1875   |      3840      |
|  4   |         154.9          |   1875   |      3840      |

: Configuration of ALMA used for spectral imaging of ID141. The table lists the central frequency, $\nu_{\rm cent}$, the band width, BW, and the number of channels, $N_{\rm chan}$, for each spectral window.

Calibration of both the band 3 and band 4 data was carried out using the scripts provided by the ALMA science archive using version 5.1.1 for band 3 and version 4.7.2 for band 4 of the Common Astronomy Software Applications (`CASA`) software package (cite: mcmullin2007). Bandpass and phase calibration was provided via the calibrators J1337-1257 and J1410+0203 respectively.

For band 3, the two measurement sets (MSs) were independently calibrated and then combined into one MS using `CASA`. We manually verified that no erroneous visibilities remained after calibration using `CASA`’s `plotms` tool. All observed images of ID141 displayed in this paper were produced by cleaning these MSs using `CASA` with natural weighting and a pixel scale of 0.024 arcsec. To isolate emission lines (see Section [2.1](#sec_obslines)), we used the `uvcontsub` tool within `CASA` for each SPW to fit a linear spectrum to channels not containing line emission and then subtract this fit from the full visibility data. A separate set of visibilities was created for analysis of the continuum emission by excluding channels containing line emission.

In addition to the band 3 and 4 ALMA data detailed above, we have also used the ALMA band 7 data acquired under the ALMA programme 2013.1.00358.S and analysed by D18 (see Fig. [1](#cont_images)). The observations in this programme amount to a total on-source integration time of 151s within four spectral windows spanning 336 to 352 GHz. The spectral windows contain no detectable emission lines and so we use the resulting 0.12 arcsec resolution continuum image solely for the purposes of morphological comparison of the reconstructed lensed SMG. We refer the reader to D18 for further details regarding these observations. Upon re-cleaning this dataset, we identified an error made in D18 such that the flux was over-estimated by approximately 30 per cent. The updated flux measured from the lensed image is $91\pm 5$ mJy.

## Emission lines

![](figures/cont_images.pdf)

![](figures/line_images.pdf)

We identified four emission lines: H$_2$O($2_{1,1}-2_{0,2}$) ($\nu_{\rm rest}=752.033$ GHz), CO(7-6) ($\nu_{\rm rest}=806.652$ GHz), \[ C i \] ($^3P_2-^3P_1$) ($\nu_{\rm rest}=809.342$ GHz, referred to as \[ C i \] (2-1) hereafter) and \[ C i \] ($^3P_1-^3P_0$) ($\nu_{\rm rest}=492.161$ GHz, referred to as \[ C i \] (1-0) hereafter). Observed images of these lines are shown in Fig. [2](#line_images) and the corresponding observed lensed line profiles (measured within a mask determined by selecting significant pixels) are shown in Fig. [3](#lines).

Table [2](#tab_zsource) lists the four line fluxes measured in the observed (i.e. lensed) images. The CO(7-6), \[ C i \] (1-0) and \[ C i \] (2-1) lines were also detected by (cite: cox2011). The line flux measured for the \[ C i \] (1-0) line measured by (cite: cox2011) is consistent with our measurement, but the Cox et al. fluxes of the other two lines are nearly a factor of two lower than those measured by ALMA. Although the discrepancies are larger than expected, the errors quoted in (cite: cox2011) do not include any uncertainty due to continuum subtraction which are large enough to eliminate any significant disagreement (R. Neri, private communication).

![](figures/lines.pdf)

Fig. [3](#lines) also shows the emission lines determined from the reconstructed source plane emission (see Section [3.2](#sec_srcpix)). In this case, we extracted the line emission from the source plane region that, according to the lens model, maps to the image plane mask used to determine the image plane emission. It is clear from the three lines with the highest signal-to-noise ratio (SNR), i.e. H$_2$O, CO(7-6) and \[ C i \] (2-1), that emission lines extracted from the image have slightly stronger flux at negative velocities whereas the reverse is true in the lines extracted from the source plane. Our lensing model confirms that this is due to differential magnification; the region of the source responsible for the emission of the negative side of the lines lies closer to the lens caustic where the magnification is higher.

Taking the median observed frequency of each of the H$_2$O, CO(7-6) and \[ C i \] (2-1) lines measured from the reconstructed source and calculating the mean of these weighted by their SNR results in an inferred source redshift of $z=4.24417\pm0.00003$ (see Table [2](#tab_zsource) - note that we did not include the \[ C i \] (1-0) line in this measurement due to its significantly lower SNR). This measurement is consistent with the redshift of $z=4.243\pm0.001$ determined by (cite: cox2011).

| Line | $\nu_{\rm rest}$ (GHz) | $\nu_{\rm obs}$(GHz) | $z_{\rm inferred}$ | flux (Jy km s$^{-1}$) |
|:--:|:--:|:--:|:--:|:--:|
| H$_2$O | 752.033 | 143.403 | 4.24419 | $4.1\pm 0.4$ |
| CO(7-6) | 806.652 | 153.820 | 4.24413 | $11.4\pm 1.1$ |
| \[ C i \] (2-1) | 809.342 | 154.332 | 4.24416 | $6.2\pm 0.8$ |
| \[ C i \] (1-0) | 492.161 | 93.8479 | (4.24424) | $3.1 \pm 0.4$ |

: Emission lines detected in the band 3 and band 4 ALMA data. The rest-frame frequencies, $\nu_{\rm rest}$, are measured from the reconstructed source cubes and therefore eliminate differential magnification of the emission lines. The SNR-weighted mean of the redshifts implied by the H$_2$O, CO(7-6) and \[ C i \] (2-1) lines is $z=4.24417\pm0.00003$. The final column gives the line flux in the observed (i.e. lensed) image.

# Lens modelling

To recover an undistorted image of the lensed SMG, we applied the modelling process of D18. Using a given model for the distribution of mass in the foreground lensing galaxy, this process reconstructs a pixelised map of the source surface brightness (cite: warren2003). In this paper, we modelled solely the interferometric visibilities. The process works by computing a set of model visibilities from the lensed image of each source pixel. We computed these visibilities using `uvmodel` contained within the `MIRIAD` software suite (cite: sault2011). The linear combination of the sets of model visibilities that best fits the observed visibilities then recovers the source surface brightness distribution for a given lens model. The lens model is optimised iteratively, repeating the linear inversion with every iteration of the lens model. In this work, lens model optimisation was performed with `NeuralNest` (cite: moss2020) which uses a neural network to generate highly efficient proposals for Markov Chain Monte Carlo sampling.

## Lens Model

Following the lens modelling in D18, we used an elliptical power-law density profile for the foreground lens, using the form given by (cite: kassiola1993) which has a surface mass density $$\begin{equation}
\kappa=\kappa_0\,({\tilde r}/{\rm 1kpc})^{1-\alpha} \, .
\end{equation}$$ where $\kappa_0$ is the normalisation surface mass density and $\alpha$ is the power-law index of the volume mass density profile. The elliptical radial co-ordinate, $\tilde r$, is defined in terms of the Euclidean co-ordinates, $(x.y)$ relative to the ellipse centre, and the elongation, $\epsilon$ (i.e., the ratio of semi-major to semi-minor axis length), by $\tilde{r}^2 = x^2 + y^2 / \epsilon^2$. The orientation of the semi-major axis, $\theta$ is measured east of north and the co-ordinates of the centre of the lens in the image plane are $(x_c,y_c)$. Initial lens modeling tests with a model including external shear were attempted but it was found that negligible shear was required in the best fit model. This agrees with the findings of D18 and hence a parameterisation of external shear was not included in the final lens model which comprised six parameters in total. We also tried a lens model comprising two separate mass components as used by (cite: bussmann2012) and as in D18, we found no significant improvement in the fit compared to a single ellipsoidal power-law. Although the two models give rise to a difference in the total source plane magnification of approximately 5 per cent, this is negligible in comparison to the errors on the intrinsic source properties we derive (see Section [\[sec_ism_vs_gas_mass\]](#sec_ism_vs_gas_mass) for further discussion). Additionally, the two models yield almost identical source morphology and kinematical properties.

To determine our optimal lens model, we simultaneously fitted the visibilities from all four SPWs in the band 4 continuum data from this paper and the band 7 visibilities from D18. Combining bands and including the continuum in this way maximises the signal-to-noise ratio (SNR) to give the best possible lens model. We used the band 7 visibilities as presented in D18 but we time-averaged the more numerous band 4 visibilities into bins of 20 s to improve computational efficiency. We found that the size of this temporal bin can be changed by a factor of several without making any noticeable difference to the reconstructed lens model or source. We obtained a model that improves upon the model presented in D18 when applied solely to the band 7 visibilities. We attribute this to a combination of the new optimisation strategy (i.e., `NeuralNest`) used in this work and the complicated parameter space that results from randomising the source plane pixelisation (see Section [3.2](#sec_srcpix)).

The parameters of our best-fit lens model are: $\kappa_0=(0.60\pm0.01)\times 10^{10}{\rm M}_\odot\,{\rm kpc}^{-2}$, $\epsilon=1.14\pm0.02$, $\theta=(96\pm2)^\circ$, $\alpha=2.01\pm0.03$. Comparing against the model in D18, there are two significant changes; the elongation has increased from 1.07 to 1.14 and the lens orientation has increased from 85$^\circ$ to 96$^\circ$ east of north. The source structure qualitatively looks very similar (see Fig. [1](#cont_images)) but the total magnification of the source continuum has fallen from 6.4 to 6.1 in band 7. The Einstein radius of $0.97\pm0.04$ arcsec remains the same.

## Source Reconstruction

We reconstructed the lensed source on a $0.8 \times 0.8$ arcsec source plane consisting of 400 Voronoi pixels formed using the method described in D18. The Voronoi tessellation is formed within the source plane region traced by mapping the region enclosed within an annular mask applied to the ring images as can be seen in Figs. [1](#cont_images) and [2](#line_images). When optimising the lens model, we computed seven randomisations of the source plane pixelisation for each trial set of lens model parameters and returned the median likelihood of these seven randomisations to `NeuralNest`. This alleviates the effect reported in (cite: nightingale2018) whereby lens model optimisation can occasionally stagnate when exceptionally good pixelisations occur by chance.

When reconstructing source cubes, we extracted the set of visibilities for each channel and applied the best-fit lens model determined in Section [3.1](#sec_lensmodel). We reconstructed the visibilities corresponding to each slice of each cube 50 times, randomising over source plane pixelisations every time. All 50 random Voronoi pixelisations were then individually binned onto a fine grid of $100 \times 100$ square pixels across the source plane and their mean computed to arrive at the final source reconstruction for a given cube slice.

The reconstruction scheme applied to cube slices results in an effective point spread function (PSF) that varies with lens magnification and therefore with position in the source plane. To quantify the resolution of our reconstructions, we computed the spatial variation of this PSF in the following way. First, we generated a set of model visibilities of a lensed image of a point source created using the best fit lens model. These visibilities were obtained using `MIRIAD`’s `uvmodel` task which evaluates them at the same uv co-ordinates as the observed visibilities. We then applied our reconstruction method, including averaging the 50 random Voronoi source planes as described above to arrive at a reconstructed point source. This procedure was repeated for a grid of $3 \times 3$ point source positions in the source plane (arranged to cover the actual observed source light) and the resulting superposition of these recovered point sources is shown in Fig. [4](#src_psf). The dimensions of the PSFs obtained in this way for band 3 and 4 are very similar and these are $0.17\times0.10$ arcsec, $0.08\times0.05$ arcsec and $0.12\times0.08$ arcsec, in the south-eastern, north-western and middle of the source respectively where the dimensions quoted are full widths at half maximum (FWHM) along the major and minor axes. At the source redshift (where 1 arcsec corresponds to a physical scale of 6.90 kpc), the smallest physical scale we are able to probe is therefore approximately 350 pc. The median resolution across the source, computed as the geometric mean of the PSF FWHMs, is approximately 550 pc.

![](figures/source_psf.pdf)

To determine the unlensed continuum flux of ID141, for each band, we applied the source reconstruction method to the emission line-subtracted visibilities obtained as outlined in section [2](#sec_data). The reconstructed source continuum in bands 3, 4 and 7 is shown in Fig. [1](#cont_images). Note that the same morphological features seen in the band 7 continuum source shown in this figure are also seen in D18, despite the different lens model and the different source pixelisation scheme. The quantitative difference is a 5 per cent reduction in magnification compared to D18 which results in a visually imperceptible increase in the linear scale of the source shown in Fig. [1](#cont_images) of 2–3 per cent. To determine the unlensed fluxes of the four identified emission lines, we reconstructed the source using the visibilities containing line emission, for each line. These are shown in Fig. [2](#line_images).

With the source reconstructed in this way, the flux was then measured in the source plane aperture that maps to the image plane annulus for both the continua and emission lines. Line fluxes are given in Table [\[tab_line_measurements\]](#tab_line_measurements) and the continuum fluxes measured in this way are $0.26\pm0.04$ mJy, $1.16\pm0.14$ mJy and $14.9\pm0.8$ mJy in band 3, 4 and 7 respectively. The continuum and line magnifications were computed in more restricted apertures. We formed an image-plane mask by selecting all pixels with a significance of at least $3\sigma$ and then mapped this to the source plane. Magnifications were then determined as the ratio of the image flux to source flux in these apertures. Table [4](#tab_magns) lists the magnifications obtained in this way for the emission lines and band 3, 4 and 7 continua.

|                   |     |     |     |
|:-----------------:|:---:|:---:|:---:|
|       Band:       |  3  |  4  |  7  |
| $\mu_{\rm tot}$ : | 5.5 | 5.9 | 6.1 |

: Total lens magnifications, $\mu_{\rm tot}$ of the continuum in bands 3, 4 and 7 and the emission lines identified in the ALMA data.

|                   |         |        |                 |                 |
|:-----------------:|:-------:|:------:|:---------------:|:---------------:|
|       Line:       | CO(7-6) | H$_2$O | \[ C i \] (2-1) | \[ C i \] (1-0) |
| $\mu_{\rm tot}$ : |   6.2   |  5.8   |       6.3       |       5.6       |

: Total lens magnifications, $\mu_{\rm tot}$ of the continuum in bands 3, 4 and 7 and the emission lines identified in the ALMA data.

# The properties of the lensed source

In this section we give consideration to the reconstructed morphology of ID141, its spectral energy distribution (SED) including the inferred quantities of dust mass, dust temperature and star formation rate and the gas mass of the ISM. Section [\[sec_srckin\]](#sec_srckin) presents our kinematical analysis. We discuss the implications of these results in Section [\[sec_discussion\]](#sec_discussion).

## Source Morphology

The reconstructed emission line images of ID141 in Fig. [2](#line_images) show clear morphological differences to the reconstructed continuum emission in Fig. [1](#cont_images). Qualitatively, the line emission is more irregular than the continuum emission. This is partly an effect of the lower SNR of the reconstructed line flux but not entirely; the lensed emission line images in the leftmost column of Fig. [2](#line_images) clearly have higher noise than the lensed continuum images in Fig. [1](#cont_images) but many of the clumpy features seen in the reconstructed line images in the rightmost column of Fig. [2](#line_images) are multiply-imaged in the observed ring and can be seen at different wavelengths.

One particularly striking feature is an offset in the peak emission seen in the \[ C i \] (1-0) line relative to the other lines and relative to the continuum emission. This is apparent in both the reconstructed source and the lensed image. The bottom-left panel of Fig. [2](#line_images) illustrates this offset by over-plotting contours of the band 3 continuum flux on the line emission map. Since \[ C i \] (1-0) has a lower excitation temperature than the other lines, this suggests the presence of cooler gas in the southern parts of the galaxy. We return to this point in Section [4.3](#sec_tempgrad).

## Far-IR Spectral Energy Distribution

Fig. [5](#sed) plots measurements of the continuum flux of ID141 at different rest-frame wavelengths. The filled points are taken from D18 but reduced by 5 per cent to account for the updated lens magnification and from (cite: cheng2020). We also updated the 850 $\mu$m flux originally taken from (cite: bakx2018) with the flux of 90 mJy following (cite: bakx2020). The new band 3 and 4 continuum fluxes are shown in this figure with empty circles.

![](figures/SED.pdf)

Following D18, we fitted the rest-frame photometry with a modified black-body SED (referred to hereafter as the ’optically thick SED’ ) comprising a single dust temperature component as well as an optically thin SED with two dust temperature components. This is an over-simplistic treatment of the expected continuous range of dust temperatures which we incorporate in later SED fitting (see Section [\[sec_stellar_mass\]](#sec_stellar_mass)). Nevertheless, these two simple SED models provide a good estimate of the range of possible dust masses. We measured the dust mass predicted by each SED using the method described in (cite: dunne2011). For this, we took the observed ALMA 880 $\mu$m flux density of $91\pm5$ mJy from the band 7 data and a dust mass absorption coefficient at the corresponding rest-frame wavelength, 168 $\mu$m, of 1.7 m$^2$kg$^{-1}$ from (cite: james2002). Both SEDs were fitted with a fixed emissivity index of 2.0 (cite: smith2013).

We allowed the temperature and normalisation of both components to vary in the fit for the optically thin SED giving four degrees of freedom. For the optically thick SED, temperature, normalisation and the 100 $\mu$m-opacity, $\tau_{100}$, were varied in the fit, giving three degrees of freedom. The best-fit parameters are $T_{\rm warm}=60\pm 6$ K and $T_{\rm cold}=34\pm 3$ K with a ratio of cold-to-warm dust mass of $74\pm13$ for the optically thin SED. For the optically thick SED, we found $T=57\pm 1$ K and $\tau_{100}=4.8$. The predicted dust masses are $(1.4\pm 0.3)\times 10^9$ M$_\odot$ and $(7.4\pm 0.8)\times 10^8$ M$_\odot$ for the optically thin and optically thick SEDs respectively.

Integrating these SEDs from 8-1000 $\mu$m gives a far-IR luminosity, $L_{\rm FIR}$, of $1.6\times10^{13}$ L$_\odot$ and $1.5\times10^{13}$ L$_\odot$ for the optically thin and thick SEDs respectively. These values are consistent with (cite: cox2011) once corrected for lens magnification and places ID141 in the category of hyper-luminous infra-red galaxies (cite: rowanrobinson2000). Taking the mean of these luminosities and converting it to a star formation rate (SFR) according to the prescription given by (cite: kennicutt2012), which uses the initial mass function given by (cite: kroupa2003), gives a value of $2400\pm500$ M$_\odot$yr$^{-1}$.

This is consistent with the SFR calculated in D18 but is 5 per cent higher due to the 5 per cent reduction in magnification of the new lens model. As discussed in D18, given its dust mass, this places ID141 significantly above the range of SFRs for $z<0.5$ H-ATLAS galaxies and in the upper envelop of high redshift SMGs (cite: rowlands2014).

## The Temperature Distribution in the ISM

There is a significant offset of the peak emission seen in the \[ C i \] (1-0) line compared to the peak of emission seen in the other three lines. Initially concerned that this may simply be the result of an offset in the world co-ordinate system between the band 3 data (where the \[ C i \] (1-0) line is located) and band 4 data, we confirmed that the continuum images between both bands align perfectly. Indeed, the \[ C i \] (1-0) emission is offset significantly from the band 3 continuum (see Fig. [2](#line_images)) and this is clearly apparent in both the reconstructed source and the lensed image. The offset between the \[ C i \] (1-0) emission and the \[ C i \] (2-1) immediately suggests the temperature of the ISM is varying across the galaxy.

The advantages of the \[ C i \] lines for tracing the cool ISM over the traditional CO method has become increasingly recognised in the last few years (cite: papadop2004; dunne2021a). The \[ C i \] lines have similar excitation temperatures and critical densities to the low-J CO lines, but their advantages over the CO lines are that the \[ C i \] lines are mostly optically thin and atomic carbon is present everywhere in the molecular phase (cite: papadop2004). In contrast, a significant and variable fraction of the molecular phase in galaxies appears to contain no CO, presumably because of photo-dissociation (cite: abdo2010; pineda2013; planck2011; bigiel2020; dunne2021a).

![](figures/temperature.pdf)

![](figures/mass_fraction.pdf)

Since the \[ C i \] lines are optically thin, it is reasonably straightforward to use the ratio of the \[ C i \] (2-1) and \[ C i \] (1-0) lines to investigate the variation of the temperature in the ISM. Therefore, we divided the \[ C i \] (2-1) and \[ C i \] (1-0) source images in Fig. [2](#line_images) into a stack of five slices running east-west, each 0.2 arcsec long and 0.08 arcsec wide, with the stack positioned to cover the main \[ C i \] emission. We calculated the ratio of the luminosity (cite: solomon2005) of the two lines, $R=L'(2-1)/L'(1-0)$, in each of these slices. Assuming local thermodynamic equilibrium, we then converted the line ratio into an excitation temperature using T$_{\rm ex}=38.8{\rm K}/\ln(2.11/R_{\rm CI})$ (cite: stutzki1997).

Fig. [6](#temperature) shows the variation of temperature in the stacked slices moving northwards across ID141. A $\simeq 2.5 \sigma$ increase in temperature is seen rising from $\simeq$40 K in the three southern bins to $\gtrsim 100$ K in the two northern bins. This trend is in accord with the other images in Fig. [2](#line_images) because the water line and the CO(7-6) line also peak in the north, and both lines are likely to be from high-temperature gas (cite: papadop2012; liu2017). The excitation temperature of the galaxy as a whole, estimated from the global fluxes for the \[ C i \] lines (Table [\[tab_line_measurements\]](#tab_line_measurements)) and the equation above, is 33 K. To put this into context, in the sample of 49 galaxies of Dunne et al. (*in preparation*), ID141 would rank as the fifth highest \[ C i \] excitation temperature.

The mass of the molecular phase of the ISM is proportional to $L'(\mbox{[\,C\,{\sc i}\,}]\,(1-0))/Q_{10}$, where $Q_{10}$ is the partition function for the \[ C i \] (1-0) line (cite: solomon2005), which depends on the excitation temperature. Fig. [7](#gas_mass_slices) shows the fraction of the molecular mass in each of our five slices calculated from the \[ C i \] (1-0) flux and our estimate of the excitation temperature in each slice, based on the assumption of local thermodynamic equilibrium. This demonstrates that although the gas is much hotter in the north, most of the mass of the molecular phase is in the colder gas to the south.

## First Estimates of the Mass of the ISM

Any estimate of the mass of the molecular ISM in a galaxy other than our own requires the use of an ISM tracer such as CO molecules or dust. This in turn requires an estimate of the constant of proportionality (the calibration factor) between the luminosity of the tracer and the mass of the ISM. In this section, we estimate the mass of the ISM in ID141 using four different tracers and five different methods. The uncertainties quoted on the ISM mass estimates include the flux uncertainty and the uncertainty of the conversion factors used.

### The gas mass from CO

We have two measurements of CO lines, a CO(7-6) line luminosity which has been corrected by the lensing model derived in this paper, and a CO(1-0) line luminosity which has not been corrected for lensing because the observations did not have high enough resolution (Dunne et al. *in preparation*). Since most of the work on calibrating the CO method has used the CO(1-0) line and since the ratio of high-J to low-J line flux has a large dispersion (cite: canameras2018), we have estimated the gas mass from the CO(1-0) measurement.

The total CO(1-0) line flux is $0.61\pm 0.09$ Jy km s$^{-1}$ (Dunne et al. *in preparation*). We have corrected this using the magnification factor of 5.5 derived for band 3. (cite: dunne2021a) have derived the CO(1-0) calibration factor from a sample of H-ATLAS galaxies with $z \sim 0.35$ with ALMA measurements of CO(1-0), \[ C i \] (1-0) and the continuum dust emission. By combining the measurements, they derive calibration factors for three methods of estimating the mass of molecular hydrogen. All three of these methods scale linearly with the mean gas-to-dust ratio (GDR) in the Universe, which they assume is 135, similar to the estimates of the value in the Milky Way. They derive a calibration factor $\alpha_{\rm CO}= 3.0\pm0.5\,$M$_{\odot}$ (K km s$^{-1}$pc$^2$)$^{-1}$. Using this value and including a factor of 1.36 to allow for the elements other than hydrogen gives an estimate of the mass of the ISM of $(3.3\pm0.7) \times 10^{11}$M$_{\odot}$ (Table [5](#tab_gas_mass)). This mass is also consistent with (cite: cox2011) after correcting for lens magnification and using the value of $\alpha_{\rm CO}$ adopted above.

### The gas mass from \[CI\]

A major problem with using the CO molecule as a tracer of the ISM is the mounting evidence that a significant fraction of the molecular phase of the ISM does not contain any CO molecules, probably as the result of photo-dissociation. For example, there is evidence from *Fermi* (cite: abdo2010), *Planck* (cite: planck2011) and *Herschel* (cite: pineda2013) that roughly one third of the molecular gas in the Milky Way does not contain any CO. There is also increasing evidence that the fraction of CO-dark molecular gas varies from galaxy to galaxy (cite: bigiel2020; dunne2021a). The \[ C i \] (1-0) line is an attractive alternative to CO because it does not suffer from the problem of photo-dissociation, is optically thin, and has a similar critical density and excitation temperature to CO (cite: papadop2004; geach2012; tomassetti2014; bourne2019). We have estimated the gas mass from the line flux of the \[ C i \] ($\rm ^3P_1 - ^3P_0$) transition, corrected with our lensing model (Table [\[tab_line_measurements\]](#tab_line_measurements)). Using their calibration sample (see above), (cite: dunne2021a) have derived a value for the \[ C i \] calibration factor of $\rm \alpha_{[CI]} = 18.8\ M_{\odot} (K\ km\ s^{-1} pc^2)^{-1}$. The excitation function for the line ($Q_{10}$) varies only weakly with temperature (cite: dunne2021a) and so we have used this calibration factor rather than trying to make any correction to it using our estimate of the temperature from the ratio of the two \[CI\] lines (Section 4.3). We estimate that the mass of the ISM in ID141, including all elements, is $(3.8 \pm 0.8)\times10^{11}$ M$_\odot$ (Table [5](#tab_gas_mass)).

### The gas mass from \[CII\]

There is a strong correlation between the luminosity of the fine-structure line of \[ C ii \] at 158 $\mu$m and the mass of molecular gas in the ISM (cite: zanella2018). Zanella et al. derive a \[ C ii \] to $H_2$ conversion ratio of $\alpha_{\rm CII} \simeq 30$ M$_{\odot}/$L$_{\odot}$. We do not have a high-resolution map of the \[ C ii \] line and therefore no specifically-derived lensing model for it. Instead, we simply used the global line flux given by (cite: cox2011), corrected it for the magnification factor of 5.9 we measured for the dust continuum emission in band 4, the closest in wavelength to the \[ C ii \] line, and then applied the calibration factor of Zanella et al. We obtained a total gas mass of $(3.2\pm0.6)\times10^{11}$ M$_\odot$ (Table [5](#tab_gas_mass)).

### The gas mass from dust emission

Many studies have made the case that dust grains are a better way of tracing the ISM than the CO molecule (cite: eales2012; scoville2014; scoville2016; scoville2017). Some of the advantages are that the dust grains do not suffer photo-dissociation like CO molecules, the dust emission is optically thin, and the relationship between the calibration factor and metallicity appears to be simpler (cite: eales2012; eales2018). We used the calibration factor between dust luminosity at 850 $\mu$m and ISM mass derived by (cite: scoville2016): $$\begin{equation}
{\rm \alpha_{850 \mu m} = <L_{\nu}/M_{ISM} > 6.7 \pm 1.7 \times 10^{19} ergs\,s^{-1}\,Hz^{-1} {\rm M}_\odot^{-1}} \, .
\end{equation}$$

We used the global flux density measured by (cite: cox2011) at 3290 $\mu$m of $1.2\pm0.1$ mJy, which makes it the closest flux measurement in rest-frame wavelength (628 $\mu$m) to the wavelength used in the calibration factor above, minimising the uncertainty in extrapolating over wavelength. We estimated the luminosity at rest-frame 850 $\mu$m, using a dust temperature of 25K and an emissivity index of ($\beta=1.8$), the same values used by (cite: scoville2016). We then calculated the ISM mass using the magnification factor of 5.5 derived from our band 3 lensing model and the calibration factor above, obtaining a total ISM mass of $(3.6\pm0.7) \times 10^{11}$ M$_{\odot}$ (Table [5](#tab_gas_mass)).

### Combining Three Methods

(cite: dunne2021a) have used several samples of calibration galaxies to derive an optimal technique for estimating the calibration factors ($\alpha_{\rm CO}$, $\alpha_{[CI]}$, $\alpha_{\rm dust}$) for an individual galaxy and for producing a best estimate of the ISM mass in the galaxy that uses all three. After correcting for lens magnification, using this technique on ID141 gives an estimate of the ISM mass of $(3.6\pm0.7) \times 10^{11}$ M$_\odot$ (Table [5](#tab_gas_mass)).

### Results

Table 5 lists the ISM mass estimates from the five different methods. We note a few important points. One caveat is that we could have used the lower value of $\alpha_{\rm CO}$ that has been claimed for ultra-luminous infrared galaxies. This would lower the ISM mass estimated from CO by a factor of a few, although there are now some compelling arguments that the claim that ultra-luminous infrared galaxies have a different $\alpha_{\rm CO}$ than other galaxies is incorrect (cite: scoville2016). A second caveat is that the only estimate in which the observations of the tracer have been corrected for gravitational lensing from the observations themselves is the estimate from the \[ C i \] (1-0) line. For every other estimate, we have corrected the tracer using a total magnification value derived at some other wavelength. There is therefore the possibility of differential magnification (cite: serjeant2012; omont2013). However, the similarity between the line profiles measured in the image plane and those in the source plane, together with the similarity of the seven magnification values presented in Table [4](#tab_magns) (from four line images and three continuum images), indicate that this is only a minor effect. We have quantified a typical size of the effect by computing the magnification factor of a source that has twice the diameter of the band 3 source shown in Fig. [1](#cont_images), finding this to be only 3 per cent lower than the original magnification. Another important point is that all ISM estimates are only for the molecular phase of the ISM because of the way the methods are calibrated. Finally, (cite: daCunha2013) and (cite: Zhang2016) have shown that the effect of the cosmic microwave background radiation will make it more difficult to detect the full extent of the ISM in high-redshift galaxies, with this effect depending on the frequency of the observations.

The mass estimates lie between $3.2 \times 10^{11}$ M$_{\odot}$ and $3.8 \times 10^{11}$ M$_{\odot}$, which are very large values and suggest we are unlikely to be missing much of the ISM. The agreement between the values is also quite remarkable considering that four of the methods use different tracers of the ISM and we are observing the galaxy only 1.5 billion years after the Big Bang. However, none of the methods are truly independent of each other because they are all calibrated from observations of the Milky Way. We discuss this further in Section [\[sec_ism_vs_gas_mass\]](#sec_ism_vs_gas_mass).

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| Line | $\nu_{\rm obs}$ | Line Flux | L | L$'$ | Reference |
|  | (GHz) | (Jy km s$^{-1}$) | $(10^9 {\rm L}_\odot)$ | ($10^{10}$ K km s$^{-1}$ pc$^2$) |  |
| CO(1-0) | 21.991 | $0.111\pm0.016$ | $0.0040\pm0.0007$ | $8.0\pm1.6$ | Dunne et al. *in preparation* |
| CO(7-6) | 153.876 | $1.84\pm0.31$ | $0.45\pm0.07$ | $2.7\pm0.5$ | this paper |
| $\rm \mbox{[\,C\,{\sc i}\,}]\,(^3P_2 - ^3P_1)$ | 154.339 | $0.98\pm0.19$ | $0.224\pm0.045$ | $1.3\pm0.2$ | this paper |
| $\rm \mbox{[\,C\,{\sc i}\,}]\,(^3P_1 - ^3P_0)$ | 93.870 | $0.55\pm0.10$ | $0.076\pm0.014$ | $2.0\pm0.4$ | this paper |
| $\rm \mbox{[\,C\,{\sc ii}\,}]\,(^3P_{3/2} - ^2P_{1/2})$ | 362.45 | $18.1\pm 2.9$ | $10.4\pm1.7$ | $4.8\pm0.8$ | (cite: cox2011) |
| H$_2$O | 143.436 | $0.70\pm0.14$ | $0.16\pm0.03$ | $1.14\pm0.23$ | this paper |

| Method | ISM mass ($10^{11}$M$_{\odot}$) | Calibration reference |
|:---|:--:|:---|
| CO(1-0) | $\rm 3.3\pm0.7$ | (cite: dunne2021a) |
| \[ C i \] (1-0) | $\rm 3.8\pm0.8$ | (cite: dunne2021a) |
| \[ C ii \] 158 $\mu$m | $\rm 3.2\pm0.7$ | (cite: zanella2018) |
| dust | $\rm 3.6\pm0.7$ | (cite: scoville2016) |
| CO/\[ C i \] /dust | $\rm 3.6\pm0.7$ | (cite: dunne2021a) |

: Gas mass estimates determined from five different methods (see main text for details).

[^1]: E-mail: simon.dye@nottingham.ac.uk

## The stellar mass

An additional means of establishing the evolutionary stage of a galaxy is by measuring its mass in stars. We return to the theme of stellar mass in Section [1.3](#sec_chem_evol) where we consider a chemical evolution model for ID141, but in this section, we outline our estimation of stellar mass of ID141 from photometry following the procedure outlined in (cite: hopwood2011). The key ingredient is the mid-IR source flux density which we have determined using Spitzer Space Telescope observations (proposal ID. 80156) acquired with the Infra Red Array Camera (IRAC) as described below.

To begin, we measured the surface brightness profiles of the lensing mass from the $K_{\rm s}$-band data presented in (cite: bussmann2012) using `GALFIT` (cite: peng2002). As (cite: bussmann2012) found, subtracting the `GALFIT` model light profiles from the observed $K_{\rm s}$-band image showed negligible residual lens light and no evidence of the lensed source image. We then used these profiles to construct model IRAC 3.6 $\mu$m and 4.5 $\mu$m surface brightness profiles and subtracted these from the IRAC images to leave residuals resembling the ALMA image (see Fig. [\[irac_resids\]](#irac_resids)). We repeated this removal procedure for three other galaxies selected to have similar morphology and flux in the IRAC data and found only negligible residuals. This demonstrates that an accurate IRAC PSF was obtained and that the near-IR traces the mid-IR well in these three systems, although we are unable to rule out the possibility of there being a mis-match in the specific case of the lensing mass in ID141. A final measure of the lensed source IRAC flux was then extracted from an annulus surrounding the observed residual flux (see Fig. [\[irac_resids\]](#irac_resids)) resulting in fluxes of $8.7\pm2.2 \, \mu$Jy and $8.1\pm1.8 \, \mu$Jy at 3.6 $\mu$m and 4.5 $\mu$m respectively. The errors here do not include any uncertainty arising from lens light removal.

In the final part of the process, following (cite: hopwood2011), we used version 2 of the SED fitting code `MAGPHYS` (cite: battisti2020; dacunha2008) and supplied this with the two IRAC fluxes as described above, a limiting $K_{\rm s}$-band flux, the far-IR fluxes as described in Section [\[sec_sed\]](#sec_sed) and Wide-field Infrared Survey Explorer fluxes at 12 $\mu$m and 22 $\mu$m (cite: lang2016). We refer the reader to Section [\[sec_app1\]](#sec_app1) for further details.

To de-magnify the quantities output by `MAGPHYS`, we assumed a magnification of 5.8, equal to the mean of the continuum magnifications given in Table [\[tab_magns\]](#tab_magns). In addition, since `MAGPHYS` assumes a Chabrier initial mass function (cite: chabrier2003), we scaled the stellar mass, dust mass and SFR output by `MAGPHYS` by a factor of 1.41 for comparison with the values determined in Section [\[sec_sed\]](#sec_sed). This factor of 1.41 was determined from the scalings derived in (cite: madau2014). The resulting stellar mass is M$_\star = 4.8^{+2.5}_{-2.3} \times 10^{11}$ M$_\odot$. In addition to stellar mass, `MAGPHYS` also gives a dust mass of $1.8\pm0.3 \times 10^9$ M$_\odot$ and a SFR of $2100\pm500$ M$_\odot$ yr$^{-1}$. The $1\sigma$ errors quoted are taken from the distributions output by `MAGPHYS` (see Appendix [\[sec_app1\]](#sec_app1) for more details). These results are consistent with those obtained in Section [\[sec_sed\]](#sec_sed) based on our own SED derived from solely the far-IR photometry.

## The kinematics of the source

The double-peaked nature of our highest SNR emission line profile, the H$_2$O line, shown in Fig. [\[lines\]](#lines) suggests that either the source is a rotating disk-like system with a prominent outer ring (cite: stewart2014), or that it is composed of two or more individual merging components.

To better understand the dynamical characteristics of the source, we investigated the spatial extent of the kinematics using the kinematic modelling code $^{\mathrm{3D}}$`Barolo` (cite: teodoro2015). Instead of fitting a kinematical model to the 2D velocity field, this code fits directly to the full datacube. This avoids the effect of artificial flattening of velocity fields due to inadequate spatial resolution and allows for the fitting of additional galaxy properties (i.e., velocity dispersion, disk scale height, brightness profile).

### The kinematical model

First, we identified the signal in the data cube by using the ‘SEARCH’ routine of $^{\mathrm{3D}}$`Barolo`, which is based on the `DUCHAMP` source finder (cite: whit12). In short, this routine automatically identifies the noise level of the data cube, searches each channel for spaxels that are above a user-provided SNR (here 3.5$\sigma$), creates a mask by extrapolating outwards to a second user-provided S/N threshold (here 2.0$\sigma$), and combines overlapping masks in different channels into discrete ‘sources’. All sources that are too spectrally thin (i.e., possessing only one channel) or spatially compact (i.e., smaller than the synthesized beam of the data cube) are rejected. This final three-dimensional mask contains all significant emission, while excluding noise peaks that would be included using a flat S/N threshold.

With the signal identified, we next performed a preliminary analysis of the masked data cube in order to produce physically motivated estimates for further dynamical fitting. The `CASA` toolkit task `image.moments` was applied to the masked cubes to create maps of integrated intensity (zeroth-moment), line-of-sight velocity (first-moment), and velocity dispersion (second-moment). The zeroth-moment map was fitted with a two-dimensional Gaussian using the `CASA` toolkit task `image.fitcomponents`, resulting in a central position, morphological position angle, and FWHM of the minor and major axes. The initial estimate of the rotational velocity at this central position was then extracted from the first-moment map.

Before performing the fitting, it is crucial to determine the size of each ring, as well as the maximum radius of the model. In order to avoid over-resolving the data, we adopted a minimum ring width of a factor of 0.4 times the FWHM of the minor axis of the restoring beam. The factor of 0.4 here is comparable to factors used in other similar works (e.g., (cite: tali18; fan19)). Similarly, we adopted a maximum model radius of a factor of 0.8 times the FWHM of the major axis of the 2D Gaussian fitted to the zeroth-moment map. The factor of 0.8 is the largest value that does not return non-physical results at large radii.

With these initial parameters and estimates in hand, we engaged the `3DFIT` routine of $^{\mathrm{3D}}$`Barolo` to fit the masked data cube with a tilted ring model comprising a series of concentric rings which each rotate with an independent velocity. The number of rings and ring width were determined as detailed in the previous paragraph, while the model center was fixed to the central position based on the 2D Gaussian fitted to the zeroth-moment map. We assumed a thin disk (i.e., $z_o=0.01$ arcsec). This routine begins by populating a model physical space (i.e., X, Y, Z) with gas clumps, so that these initial estimates of galaxy properties are replicated. This physical space is then translated into an observed-space data cube (i.e., RA, Dec, velocity), and the variable galaxy properties (i.e., rotational velocity, velocity dispersion, inclination, position angle, and systemic velocity) are perturbed until a minimum residual is met. This process is repeated for each ring, after which most variables are averaged, and the fitting process is repeated with a smaller number of variables (i.e., rotational velocity and velocity dispersion). This process results in best-fit values of each parameter and a model data cube that may be compared to the original data cube on a pixel-by-pixel basis.

The normalisation of the flux density within each ring can be either ‘local’, meaning that the integral along the spectral axis of a given model pixel in the ring must match that of the corresponding datacube pixel or, ‘azimuthal’, whereby the model is normalised to the azimuthally-averaged flux in each ring. Local normalisation allows for non-axially symmetric distributions of emission across the disk that can bias fitting of azimuthally-averaged fits. In this work, we have used both normalisation types for comparison.

We applied $^{\mathrm{3D}}$`Barolo` to the two emission lines with the highest SNR, namely the CO(7-6) and H$_2$O lines.

### The results of the kinematic model

By applying this tilted ring fitting code to the CO(7-6) and H$_2$O data cubes, we found good fits (as seen in the comparisons of Fig. [1](#12plots)). This implies that ID141 is a strongly rotation-dominated disk, a fact that is also apparent from the rotation curves shown in Fig. [2](#RCVD). The resulting dynamical masses and galaxy properties are listed in Table [\[bbout\]](#bbout) and show close agreement with each other, regardless of the line or normalization employed (local or azimuthal). Comparing these dynamical mass estimates with our ISM mass estimates in the preceding section, we find a very significant discrepancy to the extent that the ISM masses are a factor of approximately four times those of the dynamical mass estimates. We discuss possible remedies for this disparity in Section [1](#sec_discussion).

One of the strengths of three-dimensional dynamical characterization is the ability to compare the data and best-fit model on a pixel-by-pixel basis. Inspecting Fig. [1](#12plots), it is clear that both CO and H$_2$O are poorly fit by models using azimuthal averaging (note the strong residuals in zeroth-moment maps and spectra). However, the velocity fields, velocity dispersion maps, and general shape of each position-velocity diagram are well-reproduced. This raises an interesting issue: the kinematics of the galaxy are well-fit by a rotating disk, but the distribution of emission (i.e., morphology) is not. This feature will be discussed in Section [1.1](#1or2) where we consider the possibility of ID141 being a merger of two or more galaxies.

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | Normalization | Size | $\mathrm{i_M}$ | $\mathrm{i_K}$ | $\mathrm{PA_M}$ | $\mathrm{PA_K}$ | $\mathrm{M_{dyn} (10^{10} M_{\odot})}$ |
|  |  | (arcsec $\times$ arcsec) | ($^{\circ}$) | ($^{\circ}$) | ($^{\circ}$) | ($^{\circ}$) |  |
| H$_2$O | Local | $(0.36\pm0.06)\times(0.23\pm0.05)$ | $50\pm12$ | $61\pm11$ | $66\pm17$ | $96\pm10$ | $6.9\pm1.8$ |
| H$_2$O | Azimuthal | $-$ | $-$ | $57\pm12$ | $-$ | $103\pm5$ | $8.1\pm2.4$ |
| CO | Local | $(0.39\pm0.05)\times(0.33\pm0.04)$ | $33\pm16$ | $54\pm10$ | $80\pm31$ | $95\pm6$ | $7.7\pm1.7$ |
| CO | Azimuthal | $-$ | $-$ | $65\pm9$ | $0$ | $96\pm7$ | $8.6\pm2.0$ |

![](GarethFigures/full.png)

![image](GarethFigures/co_full_L_RCVD.png) ![image](GarethFigures/h2o_full_L_RCVD.png) ![image](GarethFigures/co_full_A_RCVD.png) ![image](GarethFigures/h2o_full_A_RCVD.png)

# Discussion

## One galaxy or several?

While the strong emission lines in this paper (i.e., CO and H$_2$O) are well-fit by $^{\mathrm{3D}}$`Barolo` (see Section [0.2.2](#bbres)) and return similar dynamical masses, the source morphologies are complex, resulting in imperfect fits. One key piece of information in interpreting this issue is the lack of symmetry between the velocity field structure to the north and south. While the velocity field to the north is a continuation of the central gradient, it extends to the east, and lacks a strong southern counterpart. When combined with the strong line emission and the H$_2$O dispersion peak in the northern region, this raises the possibility that the northern emission is not an extension of ID141, but a separate galaxy.

To investigate this possibility, we masked the northern section of the CO and H$_2$O data cubes, and fitted this “main” galaxy using $^{\mathrm{3D}}$`Barolo`. In each case, we assumed azimuthal normalization and the same model central position as in the unmasked data cubes. The fit to these masked data significantly improve upon the azimuthal fit to the unmasked data with a disk-like model, as shown in Fig [3](#main12).

Next, we took the best-fit models of these masked CO and H$_2$O data cubes and subtracted them from the unmasked data cube (`CASA` task `immath`) to isolate the signal to the north (hereafter referred to as the ‘secondary’). As seen in the lower row of Fig. [3](#main12), the secondary signal shows a continuous velocity gradient. The corresponding dynamical mass of this secondary is $(3.9\pm0.9)\times 10^{10}$ M$_\odot$ and when added to the dynamical mass of the main galaxy, increases the total dynamical mass by approximately 50 per cent compared to the single-galaxy model. The secondary exhibits an offset velocity dispersion peak and two separate components in each zeroth-moment map. Because of these properties, $^{\mathrm{3D}}$`Barolo` returns a poor fit using azimuthal normalization, and a better but still unsatisfactory fit using local normalization (which we also show in Fig. [3](#main12)). While $^{\mathrm{3D}}$`Barolo` is able to reproduce the brightness distribution and overall velocity gradient of each data cube, the significant residuals in each moment map and position-velocity diagram suggest that this secondary source is not a single, well-ordered rotating galaxy.

![](GarethFigures/split.png)

Taking these findings into account, there are three obvious possibilities for the nature of ID141:

1.  The system may simply be a single rotating disk. In this case, the asymmetry to the north would be a minor disturbance.

2.  The source to the north may be a separate, rotating galaxy that is closely associated to ID141. This is supported by the continuous velocity gradients shown in the unmasked data cube (see Fig. [1](#12plots)) and reasonable fits to the H$_2$O emission from the ‘main’ and ‘secondary’ sources (see right column of Fig. [3](#main12)).

3.  Because the ‘secondary’ source shows two kinematically-separated clumps in both CO and H$_2$O emission, it is conceivable that the ID141 system is composed of three significant clumps: the main galaxy, a source to the north that is strong in CO emission, and a third source to the northeast that is strong in H$_2$O emission.

Due to the diversity in observed continuum (Fig, [\[cont_images\]](#cont_images)) and line (Fig. [\[line_images\]](#line_images)) morphologies, we are unable to ascertain which of these scenarios, if any[^2], is the most likely without further observations although most bright SMGs are known to comprise mergers (cite: engel2010).

## Why do the ISM mass estimates agree so well and why are they greater than the total mass?

The five gas masses derived in Section [\[sec_gasmass\]](#sec_gasmass) (see Table [\[tab_gas_mass\]](#tab_gas_mass)) have a remarkably small range of $(3.2-3.8) \times 10^{11}$ M$_\odot$, especially since four of the methods use different tracers. They are also remarkably larger than the total mass estimated from the kinematics of the galaxy; both application of $^{\mathrm{3D}}$`Barolo` and a simple estimate from $v^2r/G$ with velocity $v=430$ km s$^{-1}$ and radius $r=2$ kpc give a dynamical mass of $\sim 0.8 \times 10^{11}$ M$_\odot$. We first consider possible observational explanations of the mass discrepancy and then suggest an astrophysical explanation of both points.

One possible explanation for the mass discrepancy is that the lens model and therefore the lens magnification is incorrect. In this case, the derived intrinsic source properties will be systematically biased. We can estimate the extent to which such an error will propagate into the ratio of gas mass to dynamical mass. Regarding the gas mass, since $M_g\propto L_{\rm int} \propto L_{\rm obs}/\mu$, where $L_{\rm int}$ and $L_{\rm obs}$ are the intrinsic and observed (i.e., lensed) line luminosities, the gas mass scales inversely proportionally with magnification. Under the assumption of circular orbits used by $^{\mathrm{3D}}$`Barolo`, the dynamical mass scales as $M_{\rm dyn} \propto v_c^2 r_{\rm int}$, where $v_c$ is the circular velocity and $r_{\rm int}$ is some intrinsic physical length scale. Since the observed $v_c$ is invariant under lensing and the intrinsic physical length scales as $r_{\rm int} \propto r_{\rm obs}/\sqrt{\mu}$, the dynamical mass scales with magnification as $M_{\rm dyn} \propto \mu^{-1/2}$ and so $M_g / M_{\rm dyn} \propto \mu^{-1/2}$. Therefore, the magnification we have obtained from our lens modelling would have to be underestimated by a factor of 16 to obtain a gas mass that is equal to the dynamical mass.

Although the statistical uncertainties we quote are orders of magnitude beneath this, larger errors can arise if the lens model we have adopted is not a faithful representation of the true lensing mass. As previously stated, changing our lens model by adding an additional mass profile to match a possible second lensing galaxy only modifies the magnification by approximately 5 per cent. An alternative is to use a mass profile that does not follow a power law. (cite: Schneider2013) present an example of a composite lens model comprising two significantly different density profiles with a resulting magnification that differs from the power-law model by 40 per cent but still broadly reproduces the observed lensed images. Even this rather extreme example is over an order of magnitude beneath the size of shift required to reconcile our dynamical and gas mass estimates.

Another possible explanation for the discrepancy is that the total (dynamical) mass has been estimated from the CO (7-6) and water lines while the ISM estimates have been obtained from observations of the continuum and different spectral lines. The \[ C i \] (1-0) line, which is probably the best tracer of the cool ISM but which is too weak for us to perform a full kinematic analysis, does have a different spatial distribution from the lines used to investigate the kinematics (Fig. [\[line_images\]](#line_images)). However, the velocity extent of all three lines is very similar (Fig. [\[lines\]](#lines)) and since the kinematic analysis extends out to a similar radius to the \[ C i \] (1-0) emission (Fig. [\[lines\]](#lines)), it is unlikely that our estimate of the total mass is too low. A related issue that has been argued in the literature (cite: daCunha2013; Zhang2016) is that the mass estimates of high-redshift galaxies may be too low because the increasing energy density in the cosmic microwave background with redshift makes it increasingly hard to detect extended gas. This is unlikely to remedy such a large discrepancy because, to first order, this effect simultaneously reduces our measurements of the total mass (by causing an under-estimation of dynamical radius) and the ISM mass.

An additional concern to consider is in the kinematic analysis from Section [1.1](#1or2). We were ultimately unable to confirm that ID141 is a single rotating disk rather than several galaxies. The strongly-lensed SMG SMM J02399-0136, initially identified as a large disk galaxy (cite: genzel2003) and subsequently resolved into a complex system of several components (cite: ivison2010) is an example of why caution must be taken. Nevertheless, in the case of ID141, this is unlikely to explain the large discrepancy. If we consider option (ii) in Section [1.1](#1or2), that ID141 consists of two rotating disks, this gives the largest of our dynamical mass estimates of $1.3 \times 10^{11}$ M$_\odot$ which is still significantly short of explaining the discrepancy.

Finally, we note that the discrepancy becomes even worse if we include stellar mass. Our estimate is that the stellar mass in this system is M$_\star = 4.8^{+2.5}_{-2.3} \times 10^{11}$ M$_\odot$, which in itself is greater than the dynamical mass. However, the uncertainty on this measurement is high and furthermore, does not include any uncertainty arising from removal of the lens light.

We now consider a possible astrophysical solution, which might also partly explain the surprising agreement between the mass estimates made with four different tracers, a solution which arises because none of the methods is really independent. The dust method of (cite: scoville2016) is calibrated using CO(1-0) measurements of galaxies and is based on the CO(1-0) calibration factor derived for giant molecular clouds in the Milky Way; the calibration factor for \[ C ii \] (cite: zanella2018) is based on dust measurements, which are again ultimately based on the CO(1-0) calibration factor from galactic giant molecular clouds; and all of the calibration factors discussed in (cite: dunne2021a) are based on the assumption that the GDR is the same as in the Milky Way. All the methods are ultimately benchmarked to the same astrophysical source, for the obvious reason that it is only in the Milky Way (and to a much lesser extent in galaxies in the Local Group) where it is possible to make the direct measurements of the ISM masses that are needed to calibrate the tracer methods.

A possible solution is if the calibration factors for ID141 are very different to the Galactic ones. To explain the agreement observed between the different mass estimates, all of the gas-to-tracer ratios would have to be $\simeq$4 times lower than in the Milky Way. Since all of the tracers are composed of heavy elements, the most direct way to bring some insight to the problem is with a chemical evolution model.

## Chemical Evolution in the Epoch of Galaxy Formation

In this section, we describe the results of a chemical evolution model we have constructed to investigate the likely evolution of the interstellar dust, gas and stellar mass of ID141. The details of this model can be found in Appendix [\[app_chem_evol\]](#app_chem_evol). We have used this model to investigate the evolution of the GDR. Although we have not modelled the evolution of the other tracers (gas-to-CO etc.), it is likely that the results will be very similar since all of the tracers must depend on the abundances of the metals in the galaxy. The similarity of the ISM estimates for four different tracers provides strong circumstantial evidence in support of this.

In the model, which is an extension of the model in (cite: DeVis2017b), the galaxy starts as a cloud of gas with no heavy elements that is gradually converted into stars. The model incorporates gas flowing in to the galaxy via accretion from the cosmic web and out from it via stellar feedback and active galactic nuclei. Dust is produced by stars, both asymptotic giant branch stars and supernovae, and grain growth and it is destroyed by astration, supernova shocks and outflows.

We considered two star formation histories, one with continuous star formation starting at some formation redshift, $z_{\rm f}$, and a second where we are currently observing 40 per cent of the way through a burst lasting $200\rm \,Myr$[^3]. Hereafter, we refer to these as the ‘conSF’ and the ‘SB’ model.

To account for possible variations in the IMF (Appendix [\[app_chem_evol\]](#app_chem_evol)), we used three functions that span most of the range of IMFs considered in the literature, namely a Salpeter IMF (cite: Salpeter1955), the Chabrier IMF (cite: chabrier2003) and the more top-heavy IMF proposed by (cite: Zhang2018), required to explain isotope ratios at high redshifts[^4]. In Section [\[sec_sed\]](#sec_sed) we estimated a SFR for ID141 from its far-infrared luminosity of 2400 $\pm$ 500 M$_\odot {\rm yr^{-1}}$, based on the assumption of an IMF from (cite: kroupa2003). If we instead use the IMFs considered here, we obtain an SFR of 2800, 1800 and 1300 M$_\odot {\rm yr^{-1}}$ for the Salpeter, Chabrier and top-heavy IMF. In our model we set $z_{\rm f} = 4.8$, $5.5$ and $7$ respectively (the higher observed current-day SFRs for the Salpeter and Chabrier IMFs leads to a more rapid conversion of gas into stars, and so their star formation needs to begin later). The parameters of each model have been chosen so that at the redshift of ID141 ($z = 4.24$) the SFR predicted by the model is similar to the SFR estimated for ID141 from its far-infrared luminosity.

[^1]: E-mail: simon.dye@nottingham.ac.uk

[^2]: The strong water emission may also be indicative of an Eddington-limited starburst in which case the complex morphology may, in part, be an outflow. See (cite: vanderwerf2011) for example

[^3]: The duration of high-$z$ starbursts are thought to range from 50-250 Myr, e.g. (cite: Danielson2017); typical duty cycles of high-redshift SMGs are thought to range from 40-100 Myr (cite: Coppin2008; Toft2014; Narayanan2015).

[^4]: Note that the so-called top heavy IMF in this work is different to the top heavy IMF evoked by (cite: baugh2005) to explain number counts of bursty submillimetre galaxies (Appendix [\[app_chem_evol\]](#app_chem_evol)).

For the conSF star formation model, we assume a SFR that follows the Kennicutt-Schmidt law (cite: Kennicutt1998), i.e., $\psi(t) = \epsilon M_g^k(t)$ where $\epsilon$ is the star formation efficiency, $M_g$ is the total gas mass and $k$ is set to unity. $\epsilon$ is estimated using $\psi = \epsilon M_g/t_{\rm dyn}$ where $t_{\rm dyn}$ is the dynamical (free-fall) timescale $t_{\rm dyn} = \sqrt{r^3/2GM}$ (cite: Walter2009; Swinbank2010) and $\psi$ is the observed SFR (see also Appendix [\[app_chem_evol\]](#app_chem_evol)). Given an effective galaxy radius of 1.4 kpc (measured from the reconstructed source continuum) and an observed ISM mass of $3.5\times 10^{11}$ M$_{\odot}$, the maximum SFE is 1 per cent for the Salpeter IMF. If we instead assume that the true ISM mass must be less than this (because of the limit from the dynamical mass) and set the ISM mass equal to the dynamical mass of the one-disk model ($M_{\rm dyn}\simeq0.8\times10^{11}$ M$_\odot$), the range of maximum SFE obtained is 5 and 2 per cent for the Salpeter and top-heavy IMFs respectively. Although ID141 is one of the most extreme objects in the universe in terms of its SFR, both estimates of SFE suggest that it is not forming stars at a significantly more efficient rate than normal systems. The SFE is similar to other high redshift SMGs (cite: Swinbank2010; Riechers2013) but an order of magnitude lower than the $z=6.4$ hyper-starburst from (cite: Walter2009). Using the current observed level of SFR and assuming that $M_g \approx M_{\rm dyn}$ when the galaxy started forming stars, the gas reservoir would be exhausted within 40 Myr for a Salpeter IMF if there is no additional replenishment of gas via mergers or inflows.

In Table [\[tab:model\]](#tab:model), we compare the model outputs predicted at the redshift of ID141 of $z=4.24$. The Salpeter IMF models produce lower dust masses (since there are fewer high mass stars producing metals and dust and there is more gas being locked up in stellar remnants) and higher stellar masses than the Chabrier and top heavy IMF models. The resulting gas fractions are also lower, indicative of a much later evolutionary stage. (cite: Dave2011) predict gas fractions of $\sim 0.4$ at $z=4$ for a current day halo mass of $M_h(z=0) = 10^{14}\,M_{\odot}$. This is larger than the Salpeter IMF results but more in line with the results from the starburst, top heavy IMF model. The total baryonic mass ($M_g +M_*$) predicted by the conSF models is $\sim 5$ times larger than the observed dynamical mass of ID141, though the starburst models predict a more comparable mass ($\sim 1-3\times$).

|  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| Model | $f_g$ | SFR | $M_g$ | $M_\star$ | $M_{\rm tot}$ | $Z$ | $M_d$ | GDR |
|  |  | $({\rm M_\odot yr}^{-1})$ | $(10^{11}{\rm M}_{\odot})$ | $(10^{11}{\rm M}_{\odot})$ | $( 10^{11}{\rm M}_{\odot})$ |  | $(10^{9}{\rm M}_{\odot})$ |  |
| **Continuous (conSF)** |  |  |  |  |  |  |  |  |
| Top Heavy | 0.24 | 1336 | 1.16 | 3.66 | 4.83 | 0.06 | 4.10 | 28 |
| Chabrier | 0.20 | 1754 | 1.14 | 4.61 | 5.91 | 0.03 | 1.65 | 69 |
| Salpeter | 0.23 | 2790 | 1.30 | 4.39 | 5.69 | 0.02 | 1.30 | 100 |
| **Starburst (SB)** |  |  |  |  |  |  |  |  |
| Top Heavy | 0.50 | 1300 | 0.79 | 0.80 | 1.60 | 0.04 | 1.84 | 43 |
| Chabrier | 0.25 | 1800 | 0.48 | 1.41 | 2.71 | 0.03 | 0.71 | 68 |
| Salpeter | 0.15 | 2800 | 0.41 | 2.39 | 2.80 | 0.02 | 0.51 | 80 |

### Evolution of the Gas to Dust Ratio

In Fig. [1](#fig:GDR) we show the evolution of the model GDR as a ratio of the Milky Way GDR, $(M_g/M_d)_{\rm model}/(M_g/M_d)_{\rm MW}$, for each model plotted against $f_g=M_g/(M_g+M_\star)$, the fraction of baryonic mass that is gas. For clarity, we only show and discuss the results for the Salpeter and top heavy IMFs as the results assuming a Chabrier IMF sits mid-way between the two. The shaded area around each line shows the effect of changing the parameter governing the rate of dust grain growth in the dense clouds (Appendix [\[app_chem_evol\]](#app_chem_evol)) from 700 to 15,000, where the former value is appropriate for the Milky Way today and the latter indicates extremely rapid grain growth (cite: Mattsson2012; Asano2013; DeVis2017b). The GDR is high at high gas fractions because the abundance of metals (and therefore dust) is still low. The GDR decreases as the gas is converted into stars and as dust is formed in stellar winds, supernovae and, after reaching some critical metallicity, via grain growth.

We have assumed a value for the GDR ratio of the Milky Way that is appropriate for the (cite: scoville2016) calibration used in Section [\[sec:gas_dust_scov\]](#sec:gas_dust_scov) to convert dust mass and submm continuum luminosity to gas mass. We have estimated this by assuming $\beta=1.8$, $T_{\rm d}=25\,\rm K$, $\kappa_{850} = 0.077\,\rm m^2\,kg^{-1}$ (cite: james2002), and $\kappa_{\rm ISM} = 4.8\times 10^{-4}\rm \,m^2\,kg^{-1}$ (cite: scoville2014). Since the models account for the total gas, whereas the calibration of dust-to-gas ($\alpha_{850}$) provided by Scoville et al. is for the molecular component only, we follow (cite: scoville2014) and assume that there are roughly equal amounts of Hi and $\rm H_2$. We also account for Helium. This gives a GDR for the Milky Way of 160 given the assumed $\kappa_{850}$ (a factor of $\sim$1.2 higher than that assumed in (cite: dunne2021a)). Table 7 shows that, for all models, the GDR reached by redshift 4.24 is $<160$ (i.e., the ratio of the model GDR to the Milky Way GDR is less than unity), suggesting *it is not appropriate to assume a Milky Way calibration when estimating gas masses from the dust emission in SMGs like ID141.* Such low GDRs have been measured in other high redshift SMGs (cite: berta2021; yang2017).

Fig. [1](#fig:GDR) also shows that the GDR can vary by over an order of magnitude during the SMG phase of a galaxy. Therefore it is also dangerous to assume a constant value for the GDR when estimating the ISM mass from the submm continuum emission. However, we can use the model to our advantage: the results in Fig. [1](#fig:GDR) provide a way to use the model itself to estimate the true GDR, and thus the mass of the ISM. We can also use it to probe how far through ID141 is in its conversion of gas into stars i.e., its evolutionary phase. Defining $M_{g}({\rm obs})$ to be the ISM mass we have estimated on the assumption of the Galactic GDR, the true ISM mass, including the contribution of the atomic gas, is given by: $$\begin{equation}
    M_{g}({\rm true}) = M_{g}({\rm obs}) \dfrac{(M_g/M_d)_{\rm model}}{(M_g/M_d)_{\rm MW}}\, .
\end{equation}$$

The total mass of the model galaxy is then given by: $$\begin{equation}
    M_{\rm true,tot} =\dfrac{M_{g}({\rm true})}{f_g}.
    \label{eq:mtrue_tot}
\end{equation}$$

We have made the assumption that there is no contribution from dark matter (cite: genzel2017), but if there is a contribution from dark matter it will strengthen the conclusions below.

We show the evolution of $M_{\rm true,tot}$ in Fig. [1](#fig:GDR) as dashed lines. The shaded horizontal region indicates where the total baryonic mass (gas plus stars) is consistent with the dynamical mass ($M_g + M_\star \leq M_{\rm dyn}$) within the uncertainty, defined as 3 $\sigma$.

We can immediately draw the following conclusions:

1.  it is only possible to make the masses consistent if the IMF is top-heavy, adding to the evidence from isotopic abundances (cite: Zhang2018) that the IMF is different in high-redshift star-forming galaxies.

2.  It is possible to make the masses consistent when the galaxy is roughly halfway through its evolution ($f_g \sim 0.5$). Although it is often assumed that galaxies like ID141 must have very high gas fractions, the discrepancy between the mass estimates gets rapidly worse above $f_g \sim 0.6$.

We also notice that the true total mass calculated using Eq. [\[eq:mtrue_tot\]](#eq:mtrue_tot) overestimates $M_{\rm dyn}$ in comparison to the model $M_{\rm tot}$ when assuming a Salpeter IMF. This is due to a combination of the faster consumption of gas due to the higher SFR and the lower dust masses formed per stellar population with a Salpeter IMF. For example, to reach a total mass $\lesssim 1\times 10^{11}\,\rm M_{\odot}$ using Eq. [\[eq:mtrue_tot\]](#eq:mtrue_tot), the conSF Salpeter model would require a ${\rm GDR} / f_{\rm g} \lesssim 50$, or alternatively, for a galaxy with $f_{\rm g} < 0.5$, a GDR of $\lesssim 25$ is needed. Such low GDRs are not reached in the Salpeter IMF models.

Although the conSF top heavy IMF appears to result in Eqn. [\[eq:mtrue_tot\]](#eq:mtrue_tot) producing a total mass within the shaded region, this is misleading. The variation of the GDR ratio with $f_g$ from this model is low enough that scaling the observed gas mass produces a true total mass from Eqn. [\[eq:mtrue_tot\]](#eq:mtrue_tot) that lies below the dynamical mass limit (in the shaded region). However, with the continuous SF model, such low GDRs can only be produced in a model that has already consumed a lot of its gas and built up a large reservoir of stars, hence violating the mass criteria we are trying to satisfy ($M_{\rm tot}$ (conSF, top heavy) $> 4\times 10^{11}\,\rm M_{\odot}$ in Table [\[tab:model\]](#tab:model)).

Finally, we note that if we increase the amount of gas accreted in the model, although this would increase the gas fraction, it would also increase both the GDR and the stellar mass, hence would not solve this issue.

![image](figures/ID141_paperfast.png) ![image](figures/ID141_paperstarburst.png)

### Metallicity Evolution

The low GDRs we predict for ID141 imply these galaxies will reach supersolar metallicities by $z=4.24$ (where $Z=M_{\rm metals}/M_g = 1.5 - 4.4\,Z_{\odot}$[^2], Table [\[tab:model\]](#tab:model)) depending on the assumed IMF and SFH. To check if such high metallicities are expected in these galaxies, we next compare the evolution of the gas-to-dust ratios (Fig. [1](#fig:GDR)) with metallicity in Fig. [2](#fig:metals). We convert the model oxygen abundance using $12 + {\rm log(O/H)} = 12 + {\rm log(X_{\rm O}/X_g)}$ where $X_{\rm O} = M_{\rm O}/16$ and $X_g = M_g/1.32$. In these units, the metallicity reached by the model assuming a top-heavy IMF is $12 + {\rm log(O/H)}=9.33$ and $9.16$ for the constant SF and starburst respectively.

Local GDR-$Z$ scaling relations from *Herschel* surveys, e.g. (cite: remyruyer2014; devis2019), are shown in Fig. [2](#fig:metals). These relationships imply values of $12+{\rm log(O/H)}$ that are consistent with the predicted model GDRs of 25-50 for ID141. At the same metallicity as the SB model with a top heavy IMF, the (cite: remyruyer2014) relationships predict GDRs ranging from 28-55. The properties of local galaxies from the DustPedia sample of (cite: devis2019) also reach low gas-to-dust ratios, but at lower metallicities than those predicted for ID141 (Fig. [2](#fig:metals)). This sample is made up mostly of late type galaxies, with stellar masses $>10^{8}\,M_{\odot}$ making up only 4 per cent.

We also show the relationship from (cite: santini2014) derived by combining observed dust masses of galaxies out to $z=2.5$ with metallicities derived from the stellar mass-SFR-metallicity relationship of (cite: mannucci2010). Although a number of mass-metallicity relations exist in the literature (eg (cite: bothwell2013; peng2015), (cite: maiolino2019) and references therein) we caution here that there are very few studies carried out at high enough stellar mass, at redshifts $>3$, and with SFRs $>100\,\rm M_{\odot}\,yr^{-1}$, making it difficult to apply these relationships to ID141.

What we can say, is that if we assume that ID141 will shortly turn into a massive quiescent early-type galaxy with very little future evolution, then our models predict high mass galaxies with super solar metallicities $\sim 1.3-3 \,Z_{\odot}$ at present day. This is in agreement with observations of massive ellipticals in the local universe ((cite: gallazzi2005; peng2015), see also (cite: maiolino2019), their Fig. 12).

![image](figures/ID141_paper_ref_Zfast.png) ![image](figures/ID141_paper_ref_Zstarburst.png)

## Broader Implications of Low Gas-to-Dust Ratios

[^1]: E-mail: simon.dye@nottingham.ac.uk

[^2]: Solar metallicity taken from (cite: asplund2009).

The conflict between dynamical mass and ISM mass when estimating the latter using CO has been previously reported in the literature (cite: Tacconi2008; hodge2012; bothwell2013; rivera2018). A common conclusion is to reduce the CO conversion factor, $\alpha_{\rm CO} \simeq 1$ (cite: boogaard2021). However, even with this low value, the tension between the dynamical mass and the ISM mass is sometimes still seen, requiring an additional explanation (cite: bothwell2013). Low values of $\alpha_{\rm CO}$ seemed plausible given the evidence for a low value in low-redshift Ultraluminous Infrared Galalaxies (ULIRGs) (cite: downes1998). More recently, this evidence has weakened (cite: papadop2012a; papadop2012b), which makes the low $\alpha_{\rm CO}$ explanation of the mass tension given in these previous studies less likely. The advantage of this work is that we have used four different tracers of the ISM: \[ C i \] , \[ C ii \] , dust and CO. Therefore, although we might resolve the tension in our ISM estimate from the CO tracer by reducing $\alpha_{\rm CO}$ by a factor of $\sim 4$, we would also have to reduce the three other calibration factors by the same amount.

Given the quite startling agreement between the ISM mass estimates for ID141, which has been noticed for other galaxies (cite: dye2015), it seems more natural to assume that the true explanation of the mass discrepancy is due to chemical evolution rather than the assumption that the physical conditions in the ISM are producing a low value of $\alpha_{\rm CO}$. The former naturally explains why the calibration factors for all four gas tracers are lower in ID141.

This may seem counter-intuitive at first since galaxies in the first few billion years might be expected to have higher GDRs than in low-redshift galaxies because there has been less time for heavy elements to form (cite: peroux2020). There is one strong argument why, in this situation, common sense is probably wrong. All the high-redshift galaxies observed have been found because they contain a lot of dust or because they already contain a large mass of stars (cite: scoville2014; scoville2017; tacconi2018; millard2020), and so there is a strong selection effect that will mean that samples of high-redshift galaxies are likely to contain galaxies in which the stellar mass or dust mass is already high. The simplest closed-box models for the formation of dust ((cite: eales1996), (cite: Dunne2003)), for example, predict that the dust mass in a galaxy is at a peak when $f_g \sim 0.5$, and thus the galaxies in a sample compiled from a submm continuum survey are likely to have high dust masses and to have already turned much of their gas into stars.

If our conclusion that the gas-to-tracer ratio is $\simeq$4 times lower than in the Milky Way is true for high redshift galaxies in general, it would have a dramatic effect on our assessment of their evolutionary states, reducing all ISM mass estimates by a factor of 4. However, the variation in the GDR seen in our chemical-evolution model (Fig. [\[fig:GDR\]](#fig:GDR)) shows that calibrating all the tracers using ID141 would be just as risky as using the Galactic calibrations. The indication from Fig. [\[fig:GDR\]](#fig:GDR) is that there is no perfect calibration, and it is better to think of a gas-to-tracer ratio as being a new useful tool for assessing the evolutionary state of a galaxy.

## How quickly will ID141 become a quiescent galaxy?

In this section, we consider the evolution of ID141 itself. In particular, we examine whether the evolution might be fast enough for it to join the population of quiescent galaxies that is seen at $z \sim 3$ (cite: glazebrook2017; girelli2019; valentino2020; forrest2020a; forrest2020b; merlin2019). For reference, the time interval between the two redshifts is $\rm 7.2 \times 10^8\ yr$.

To begin addressing this question, we turn to our kinematic analysis (Section [\[sec_srckin\]](#sec_srckin)) which shows evidence for a large rotating disk, with possibly one or two additional merging systems. Since high-redshift galaxies are often separated into two classes - disks or mergers - the kinematics of ID141 suggest that both are often going on at the same time. The escape velocity of the system is given by: $$\begin{equation}
v_{\rm esc} = \sqrt{\frac{2 G M}{R}}.
\end{equation}$$ Given a dynamical mass of $\rm 1.3 \times 10^{11}\ M_{\odot}$ and a radius of 1.4 kpc, the escape velocity is $\rm \sim 910\ km\ s^{-1}$. This is similar to the velocity range of the system (Fig. [\[lines\]](#lines)), which suggests that most of the material we see is destined to end up in a single galaxy.

There are two other observational results that are relevant to the dynamical evolution of the system. First, the \[ C i \] (1-0) image (Fig. [\[cont_images\]](#cont_images)), which likely gives us the most unbiased view of the gas, shows that the gas is divided into a number of clumps. The existence of clumps in cleaned interferometric data needs to be treated with care (cite: ivison2020) since there are observational effects that can lead to them being falsely identified. However, when clumps are multiply-imaged in a strong lensing system such as ID141, these observational effects are mitigated. A particularly striking example of this is in the system SDP81 which unequivocally shows multiply-imaged clumps in high resolution, high signal-to-noise ALMA data (cite: dye2015).

Clumps are expected to migrate into the centre of the galaxy through dynamical friction on a timescale given by (cite: genzel2011): $$\begin{equation}
t_{\rm inspiral} \simeq \left( \frac{v_c}{\sigma_0} \right)^2 t_{\rm dyn}\, ,
\end{equation}$$ where $\sigma_0$ is the velocity dispersion and $v_c$ is the circular velocity. The ratio of $v_c$ and $\sigma_0$ is $\simeq$ 10, giving a migration timescale of $t_{\rm inspiral} \simeq 100 t_{\rm dyn} \simeq 2.3\times10^8\ {\rm yr}$.

Alternatively, we can consider the dynamical evolution of the system by calculating the Toomre Q-parameter (cite: toomre1964), which quantifies the stability of rotating, thin symmetric disks against gravitational collapse (cite: toomre1964). For a flat rotation curve, the Q-parameter is given by (cite: genzel2011): $$\begin{equation}
Q_{\rm gas} =  \sqrt{2} \, \frac{\sigma_0}{v_c} \, 
\frac{M_{\rm tot}}{M_{\rm gas}}\, .
\end{equation}$$ Using the results of our chemical evolution model, we assume $M_{\rm gas}/M_{\rm tot} \simeq 0.5$. With this value of the mass ratio, the results from the kinematical modelling of the CO line (Fig. [\[RCVD\]](#RCVD) - left panels) imply that $Q\simeq$0.6 in the central few hundred parsecs of the galaxy, falling to a lower value beyond a radius of 1 kpc. The results from the kinematical modelling of the H$_2$O line (Fig. [\[RCVD\]](#RCVD) - right panels) imply much lower values of $Q_{\rm gas}$. Our results therefore show that the gas disk is unstable. We reached the same conclusion for the disk of the other gravitationally-lensed *Herschel* source that has been observed at high resolution with ALMA, SDP81.

All of these results show that the dynamic evolution of ID141 is very fast and suggest that it could easily turn into a single fairly undisturbed galaxy by $z \sim 3$.

[^1]: E-mail: simon.dye@nottingham.ac.uk

Turning now to the evolution of ID141’s gas, the only chemical evolution models that produce galaxies consistent with the tight mass limits are those with a top-heavy IMF and a starburst (Table [\[tab:model\]](#tab:model)). The conSF model has a gas mass and star-formation rate at $z = 4.24$ of $1.16 \times 10^{11}$ M$_{\odot}$ and $1336$ M$_{\odot}\ \rm yr^{-1}$ respectively, but the model predicts a stellar mass greater than the dynamical mass limit. However, if we assume that the galaxy continues to form stars at the same rate, and that the galaxy accretes no fresh gas, the gas will be consumed in $\simeq 9\times 10^7\ {\rm yr}$. If we perform the same calculation with the SB model, we obtain a timescale of $\simeq 6 \times 10^7\ {\rm yr}$.

In conclusion, both the dynamics and the other properties of ID141 are consistent with the idea that, although it is an extreme system at $z=4.24$, by a redshift of $z \sim 3$ it will have evolved into a single, fairly undisturbed galaxy, containing little gas.

# Conclusions

ID141 is a gravitationally-lensed hyper-luminous SMG at a redshift of 4.24 with a star-formation rate of 2400 $\rm M_{\odot}\ yr^{-1}$, making it an extreme example of an already extreme class. The system was chosen as a target for a comprehensive high-resolution investigation of the phases of the ISM in high-redshift galaxies because at its redshift, the key ISM spectral lines fall in the ALMA bands. In this paper we have presented high-resolution observations in the \[ C i \] (1-0) line, the \[ C i \] (2-1) line, the CO(7-6) line and the $\rm H_2O (2_{1,1} - 2_{0,2})$ lines. After the lensing reconstruction, the images in the source plane reach down to a resolution of $\rm \simeq350\ pc$. In this section, we outline the observational results and our inferences from these results.

Our observational results are:

1.  The gas is distributed over a region of $\simeq 3$ kpc. The \[ C i \] (1-0) emission is offset by $\simeq 1$ kpc from the other lines, including the \[ C i \] (2-1) line. This shows that the galaxy contains a large reservoir of cool gas that is missed by the other spectral lines that we have observed with ALMA, although the estimates of the ISM mass from the \[ C i \] (1-0) and CO(1-0) lines are remarkably similar (see below).

2.  We have used the ratio of the \[ C i \] (2-1) and \[ C i \] (1-0) lines to measure the variation in excitation temperature over the galaxy. We find that the temperature increases from $T_{\rm ex} \sim 40$K where the \[ C i \] (1-0) emission peaks to $T_{\rm ex} \gtrsim 100$K where the CO and water lines are at a peak.

3.  The gas disk appears to be broken into clumps.

4.  We have used the CO and water lines to carry out a kinematic analysis of the galaxy. We find strong evidence of a rotating system but cannot distinguish between there being a single rotating galaxy or there also being one or two additional galaxies. Our estimate of the dynamical mass depends on which of these scenarios we choose, but our estimates lie in the range $0.8-1.3 \times 10^{11}$ M$_{\odot}$.

5.  We have estimated the ISM mass in the galaxy five ways: (1) from the \[ C i \] (1-0); (2) from the dust continuum emission: (3) from a measurement of the global CO(1-0) flux; (4) from a measurement of the global flux in the \[ C ii \] 158-$\mu$m line; (5) from a method that combines (1), (2) and (3). Our mass estimates lie in the range $\rm 3.2-3.8 \times 10^{11}$ M$_{\odot}$.

6.  After subtracting the lens from a *Spitzer* image, we estimate that the stellar mass of ID141 is M$_\star = 4.8^{+2.5}_{-2.3} \times 10^{11}$ M$_\odot$.

[^1]: E-mail: simon.dye@nottingham.ac.uk

From these basic observational results we make the following inferences:

1.  All five of our ISM estimates are very similar and are substantially larger than the dynamical mass of the system (without even considering the stellar mass and any dark matter). Inconsistencies like this have been observed before and have always been attributed to a low value of $\alpha_{\rm CO}$, which is then attributed to physical conditions in the ISM of an SMG probably being different from the Milky Way. This can not be the explanation in ID141 because we are using four different tracers, each of which will be affected by different physical conditions in the ISM in different ways. The similarity of the ISM mass estimates using the four different tracers suggests that chemical evolution could explain the mass discrepancy because the abundances of all the tracers will depend on the abundances of heavy elements in the galaxy.

2.  We have used a chemical evolution model to show that the GDR does change substantially during the evolution of an SMG. It can reach values much lower than the Milky Way value as long as the IMF is top-heavy in SMGs for which there is now good evidence from spectroscopy of molecules containing rare isotopes (cite: Zhang2018).

3.  Although there is a complex web of calibrations, all estimates of the ISM masses in high-redshift galaxies are ultimately calibrated in the Milky Way. Our conclusion that the gas-to-tracer ratio for four different tracers is four times lower than in the Milky Way puts all these estimates into doubt. On a positive note, we suggest that the gas-to-tracer ratio may be a useful new tool for assessing the evolutionary state of a galaxy.

4.  We have used ID141 to test whether extreme SMGs like this might evolve into the population of quiescent galaxies that is seen at $z \sim 3$. Several indicators (the Toomre Q-parameter, the inspiral time for the clumps, and the escape velocity system of the system) suggest that ID141 should be a single, fairly undisturbed galaxy by $z \sim 3$. The depletion time for the gas also implies that, on the assumption of no gas infall, the galaxy will be devoid of gas by this redshift. Therefore, extreme though it is at $z=4.2$, it seems plausible that ID141 will evolve into an unexceptional galaxy by $z \sim 3$.

# Acknowledgements

SD is supported by a UK Science and Technology Facilities Council (STFC) Rutherford Fellowship. SAE and MWLS acknowledge support from STFC. GCJ acknowledges ERC Advanced Grant 695671 “QUENCH” and support by the STFC. HLG, LD and MWLS acknowledge support from the European Research Council in the form of Consolidator Grant 647939 CosmicDust. EB and EMC acknowledge support by Padua University grants DOR1885254/18, DOR1935272/19, and DOR2013080/20 and by MIUR grant PRIN 2017 20173ML3WW-001. HD acknowledges financial support from the Spanish Ministry of Science, Innovation and Universities (MICIU) under the 2014 Ramón y Cajal program RYC-2014-15686 and from the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEI-MCINN) under grant (La evolución de los cíumulos de galaxias desde el amanecer hasta el mediodía cósmico) with reference (PID2019-105776GB-I00/DOI:10.13039/501100011033).This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00358.S, ADS/JAO.ALMA #2016.1.00450.S and ADS/JAO.ALMA #2017.1.00029.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. In addition, publications from NA authors must include the standard NRAO acknowledgement: The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

[^1]: E-mail: simon.dye@nottingham.ac.uk

# Data Availability

[^1]: E-mail: simon.dye@nottingham.ac.uk

All data presented in this paper can be obtained from the ALMA science archive under the project IDs 2013.1.00358.S, 2016.1.00450.S and 2017.1.00029.S.

[^1]: E-mail: simon.dye@nottingham.ac.uk

</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "Fluxes at 12 um and 22 um for MAGPHYS SED fitting",
  "failed_quote": "In the final part of the process, following (cite: hopwood2011), we used version 2 of the SED fitting code `MAGPHYS` (cite: battisti2020; dacunha2008) and supplied this with the two IRAC fluxes as described above, a limiting $K_{\\rm s}$-band flux, the far-IR fluxes as described in Section [sec_sed] and Wide-field Infrared Survey Explorer fluxes at 12 $\\mu$m and 22 $\\mu$m (cite: lang2016)."
 },
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Compared results against full multi-wavelength MAGPHYS SED fitting",
  "failed_quote": "These results are consistent with those obtained in Section [sec_sed] based on our own SED derived from solely the far-IR photometry."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "De-magnification factor mu = 5.8; IMF scaling factor = 1.41",
  "failed_quote": "To de-magnify the quantities output by `MAGPHYS`, we assumed a magnification of 5.8, equal to the mean of the continuum magnifications given in Table [tab_magns]."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[1]",
  "value": "De-magnification factor mu = 5.8; IMF scaling factor = 1.41",
  "failed_quote": "In addition, since `MAGPHYS` assumes a Chabrier initial mass function (cite: chabrier2003), we scaled the stellar mass, dust mass and SFR output by `MAGPHYS` by a factor of 1.41 for comparison with the values determined in Section [sec_sed]."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Near-IR Ks-band morphology traces mid-IR lens light; Chabrier (2003) IMF in MAGPHYS scaled by 1.41 to Kroupa (2003) IMF",
  "failed_quote": "In addition, since `MAGPHYS` assumes a Chabrier initial mass function (cite: chabrier2003), we scaled the stellar mass, dust mass and SFR output by `MAGPHYS` by a factor of 1.41 for comparison with the values determined in Section [sec_sed]."
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "MAGPHYS v2 SED fitting outputting parameter probability distributions",
  "failed_quote": "The $1\\sigma$ errors quoted are taken from the distributions output by `MAGPHYS` (see Appendix [sec_app1] for more details)."
 },
 {
  "path": "analysis_steps[6].key_parameters[0].evidence[1]",
  "value": "z_f = 4.8 (Salpeter), 5.5 (Chabrier), 7 (top-heavy); SB burst duration = 200 Myr observed at 40%; grain growth parameter = 700 to 15,000; effective radius = 1.4 kpc; v_c / sigma_0 = 10",
  "failed_quote": "The shaded area around each line shows the effect of changing the parameter governing the rate of dust grain growth in the dense clouds (Appendix [app_chem_evol]) from 700 to 15,000"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Unlensed continuum flux density (Band 3) = 0.26 mJy",
  "failed_quote": "Line fluxes are given in Table [tab_line_measurements] and the continuum fluxes measured in this way are $0.26\\pm0.04$ mJy, $1.16\\pm0.14$ mJy and $14.9\\pm0.8$ mJy in band 3, 4 and 7 respectively."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Unlensed continuum flux density (Band 4) = 1.16 mJy",
  "failed_quote": "Line fluxes are given in Table [tab_line_measurements] and the continuum fluxes measured in this way are $0.26\\pm0.04$ mJy, $1.16\\pm0.14$ mJy and $14.9\\pm0.8$ mJy in band 3, 4 and 7 respectively."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Unlensed continuum flux density (Band 7) = 14.9 mJy",
  "failed_quote": "Line fluxes are given in Table [tab_line_measurements] and the continuum fluxes measured in this way are $0.26\\pm0.04$ mJy, $1.16\\pm0.14$ mJy and $14.9\\pm0.8$ mJy in band 3, 4 and 7 respectively."
 },
 {
  "path": "results_numeric[24].evidence[0]",
  "value": "Global [CI] excitation temperature = 33 K",
  "failed_quote": "The excitation temperature of the galaxy as a whole, estimated from the global fluxes for the \\[ C i \\] lines (Table [tab_line_measurements]) and the equation above, is 33 K."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "The kinematics of ID141 are dominated by a rotationally-supported unstable gas disk (Q_gas <= 0.6), with asymmetric northern emission that may be a minor disturbance, a second merging disk, or two additional clumps.",
  "failed_quote": "With this value of the mass ratio, the results from the kinematical modelling of the CO line (Fig. [RCVD] - left panels) imply that $Q\\simeq$0.6 in the central few hundred parsecs of the galaxy, falling to a lower value beyond a radius of 1 kpc."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The system is dominated by a rotationally-supported gas disk, but existing data cannot definitively distinguish between a single disturbed disk, two closely associated rotating galaxies, or three clumps.",
  "failed_quote": "Due to the diversity in observed continuum (Fig, [cont_images]) and line (Fig. [line_images]) morphologies, we are unable to ascertain which of these scenarios, if any, is the most likely without further observations"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[1]",
  "value": "Explanation of gas-to-dynamical mass discrepancy via lens magnification error, CMB dimming, or missing extended kinematics (rejected because magnification would need to be off by a factor of 16, CMB reduces both radii and luminosities, and [CI](1-0) has similar velocity and radial extent)",
  "failed_quote": "However, the velocity extent of all three lines is very similar (Fig. [lines]) and since the kinematic analysis extends out to a similar radius to the \\[ C i \\] (1-0) emission (Fig. [lines]), it is unlikely that our estimate of the total mass is too low."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[0]",
  "value": "[CI](1-0) has too low SNR for a full 3D kinematic analysis, so dynamical masses rely on CO(7-6) and H2O which have different spatial distributions than [CI](1-0).",
  "failed_quote": "The \\[ C i \\] (1-0) line, which is probably the best tracer of the cool ISM but which is too weak for us to perform a full kinematic analysis, does have a different spatial distribution from the lines used to investigate the kinematics (Fig. [line_images])."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "Cannot definitively distinguish between a single disturbed rotating disk, two merging disks, or three clumps from the current observations.",
  "failed_quote": "Due to the diversity in observed continuum (Fig, [cont_images]) and line (Fig. [line_images]) morphologies, we are unable to ascertain which of these scenarios, if any, is the most likely without further observations"
 }
]
```
