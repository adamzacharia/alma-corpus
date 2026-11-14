# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...887...80K\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Mapping metallicity variations across nearby galaxy disks

## Abstract

The distribution of metals within a galaxy traces the baryon cycle and the buildup of galactic disks, but the detailed gas phase metallicity distribution remains poorly sampled. We have determined the gas phase oxygen abundances for 7,138 HII regions across the disks of eight nearby galaxies using VLT/MUSE optical integral field spectroscopy as part of the PHANGS-MUSE survey. After removing the first order radial gradients present in each galaxy, we look at the statistics of the metallicity offset ($\Delta$O/H) and explore azimuthal variations. Across each galaxy, we find low ($\sigma$=0.03-0.05 dex) scatter at any given radius, indicative of efficient mixing. We compare physical parameters for those HII regions that are 1$\sigma$ outliers towards both enhanced and reduced abundances. Regions with enhanced abundances have high ionization parameter, higher H$\alpha$ luminosity, lower H$\alpha$ velocity dispersion, younger star clusters and associated molecular gas clouds show higher molecular gas densities. This indicates recent star formation has locally enriched the material. Regions with reduced abundances show increased H$\alpha$ velocity dispersions, suggestive of mixing introducing more pristine material. We observe subtle azimuthal variations in half of the sample, but can not always cleanly associate this with the spiral pattern. Regions with enhanced and reduced abundances are found distributed throughout the disk, and in half of our galaxies we can identify subsections of spiral arms with clearly associated metallicity gradients. This suggests spiral arms play a role in organizing and mixing the ISM.

# Introduction

The production and build up of heavy elements from stellar nucleosynthesis over cosmic time has resulted in pronounced radial trends in chemical abundances within galaxies. This is commonly constrained by measuring the current gas-phase oxygen abundance (metallicity) within HII regions (cite: Kennicutt1996). The predominantly negative radial trends in metallicity have been well established across large samples of galaxies (cite: Zaritsky1994; Sanchez2014; Kaplan2016; Belfiore2017; Poetrodjojo2018), tracing the inside-out growth of galaxy disks (cite: Boissier1999).

In addition to tracking feedback and pollution from massive stars into the interstellar medium (ISM), metals play a key role in the cooling of the ISM, and drive changes in fundamental local ISM properties (e.g., gas to dust ratio, HI-to-H$_2$ transition, CO-to-H$_2$ conversion factor). Understanding the degree of chemical homogeneity in star-forming galaxies is key to make use of stellar metallicities for Galactic archaeology, including chemical tagging studies and assessments of burstiness and accretion events.

This purely radial picture may be an oversimplification because spiral arms, bars, and stellar feedback drive mixing and gas flows. This has been theorized to happen through bar-driven radial mixing (cite: DiMatteo2013), spiral arm driven large-scale systematic streaming motions (cite: Grand2016; Sanchez-Menguiano2016), kiloparsec-scale mixing-induced dilution due to the spiral density waves passage (cite: Ho2017), thermal and gravitational instabilities (cite: Yang2012; Petit2015), and interstellar turbulence (cite: deAvillez2002; Krumholz2018). Many of these processes should affect azimuthal inhomogeneity in the gas-phase abundances, which could then impact the local physical conditions that regulate star formation.

With typically only 10-100 HII regions with measured abundances per galaxy (cite: Pilyugin2014), detailed exploration of azimuthal trends has been unfeasible for large samples of galaxies, and the detailed gas phase metallicity distribution remains poorly understood. With the introduction of new wide-field optical integral field unit (IFU) spectrographs, it has become possible to fully sample the gas-phase metallicity across galaxy disks. Large optical IFU projects that survey hundreds to thousands of galaxies (CALIFA - the Calar Alto Legacy Integral Field Area Survey, (cite: Sanchez2012); MaNGA - Mapping Nearby Galaxies at Apache Point Observatory , (cite: Bundy2015); SAMI- Sydney-AAO Multi-object Integral-field spectrograph, (cite: Bryant2015)) trade sample size for spatial resolution, achieving $\sim$kpc spatial resolution. While having the obvious advantage of large statistical samples, this can introduce undesirable systematic effects when inferring metallicity, as multiple ionization sources can contribute within a single resolution element (cite: Ho2018; Poetrodjojo2019).

Metallicity studies with optical IFU observations that isolate individual HII regions ($<$100 pc scales) have so far been limited to individual objects. These studies have produced conflicting results, with some showing no evidence for significant large-scale azimuthal variations in relation to the spiral pattern (cite: Kreckel2016), while other galaxies reveal clear enrichment patterns along spiral structures (cite: Sanchez-Menguiano2016; Vogt2017; Ho2017; Ho2018). Our Milky Way galaxy itself reveals tantalizing evidence for azimuthal metallicity variations (cite: Balser2011; Balser2015).

The Physics at High Angular resolution in Nearby GalaxieS (PHANGS) collaboration[^1] aims to understand the interplay of the small-scale physics of gas and star formation with galactic structure and galaxy evolution. To this end, we are collecting observations of the molecular gas, ionized gas and stellar populations within nearby (D$<$17 Mpc) moderately inclined star-forming disk galaxies. To constrain the local and large-scale metallicities of these galaxies, we have begun a large observing program employing the Very Large Telescope/Multi Unit Spectroscopic Explorer (VLT/MUSE) to mosaic the central disk of 18 galaxies with optical IFU observations (PI: Schinnerer). Combined with our pilot survey that targeted NGC 628 (cite: Kreckel2016; Kreckel2018), these 19 galaxies make up the PHANGS-MUSE survey.

We present here initial results from the PHANGS-MUSE survey using observations of the first eight completed galaxies. With $\sim$50 pc resolution across the central star-forming disks of these galaxies, our observations are well matched to the typical spatial scales of HII regions (10-200pc; (cite: Azimlu+2011)). Our MUSE observations can spatially isolate HII regions and, using multiple line diagnostics, distinguish photoionized regions from other ionizing sources (diffuse ionized gas, supernova remnants, planetary nebulae, shocks, outflows, and extended ionization from an active galactic nuclei). This combination of high spatial resolution with multiple line diagnostics mapped across the galaxy disks allows us to take a statistical approach to characterize metallicity variations across galaxy disks and relate these to the local physical conditions of the ISM.

Section [2](#sec:data) presents the data we use and describes the construction of our HII region catalogs. In Section [\[sec:strongline\]](#sec:strongline) we detail how we use emission lines to infer the physical conditions of HII regions, particularly the metallicity and ionization parameter. Section [4](#sec:results) presents our results on the trends in metallicity with local physical conditions, the subtle evidence we observe for azimuthal variations, and a brief discussion of the impact of bars on the metal distribution. Section [5](#sec:discussion) discusses the implications of our results and we conclude in Section [6](#sec:conclusion).

# Data

## Observations

We use the MUSE spectrograph (cite: Bacon2010) at the VLT to mosaic the central star-forming disks of eight nearby spiral galaxies (Table [1](#tab:sample)) as part of the PHANGS-MUSE large observing program (PI: Schinnerer). This powerful optical IFU provides a 1$'$ $\times$ 1$'$  field of view with 0.2$''$ pixels and a typical spectral resolution of $\sim$2.5Å  over the nominal wavelength range, covering 4800-9300Å. Our sample of eight galaxies includes observations of NGC 628, which have been described previously (cite: Kreckel2016; Kreckel2018). For our large program observations, each position was observed in four rotations, with two sky pointings, and a total on-source integration time of 43 minutes. For NGC 628 we used slightly different integration times (43-50 minutes). The center pointing for NGC 2835 was observed as part of the MUSE Atlas of Disks survey (MAD; (cite: Erroz-Ferrer2019)), with 60 minute exposure time. NGC 4254 and NGC 4535 were observed using the wide-field adaptive optics (AO) mode. We present here results using the first eight completed galaxies. Table [1](#tab:sample) summarises the main properties of the galaxy sample, the angular resolution achieved in the observations, the number of HII regions in each galaxy and the physical size of the survey area covered in the disk.

Angular resolution varies between galaxies from 0.5$''$ (for the AO mode) to 1.0$''$, and can vary slightly between fields (typically less than 0.2$''$) and as a function of wavelength (0.1$''$-0.2$''$ across the whole wavelength range). At the distances of our sample, this resolution corresponds to physical scales of 40–70 pc. As we integrate the spectrum over each entire HII region, the slight variations in seeing should not impact our results.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|---:|---:|---:|---:|:--:|:--:|:--:|---:|---:|
| Name | D | Type | Log$_{10}$(M$_*$) | Log$_{10}$(SFR) | PA$^{a}$ | i$^{b}$ | $\rm R_{25}$$^{c}$ | Angular | Physical | Number of | Survey |
|  |  |  |  |  |  |  |  | resolution | resolution | HII regions | Area |
|  | (Mpc) |  | (M$_\odot$) | (M$_\odot$ yr$^{-1}$) | (degrees) | (degrees) | (arcmin) | (arcsec) | (pc) |  | (kpc$^2$) |
| NGC 0628 | $9.77\pm0.82$ | Sc | 10.2 | 0.26 | 20.9 | 8.7 | 5.0 | 1.0 | 47 | 1277 | 96 |
| NGC 1087 | $14.4\pm4.8$ | SBc | 9.8 | 0.05 | 177.3 | 41.3 | 1.5 | 1.0 | 70 | 679 | 105 |
| NGC 1672 | $11.9\pm4.0$ | SBb (S) | 10.2 | 0.48 | 135.7 | 37.5 | 3.1 | 0.8 | 46 | 880 | 95 |
| NGC 2835 | $10.1\pm3.4$ | SBc | 9.6 | -0.08 | 1.6 | 47.8 | 3.2 | 0.9 | 44 | 699 | 60 |
| NGC 3627 | $10.6\pm0.9$ | SBb (S3) | 10.6 | 0.55 | 174.1 | 55.0 | 5.1 | 1.0 | 51 | 692 | 76 |
| NGC 4254 | $16.8\pm5.6$ | Sc | 10.5 | 0.74 | 67.7 | 37.8 | 2.5 | 0.7 | 57 | 1824 | 191 |
| NGC 4535 | $15.8\pm2.3$ | SBc | 10.4 | 0.35 | 179.8 | 40.7 | 4.1 | 0.5 | 38 | 864 | 126 |
| IC 5332 | $9.95\pm3.3$ | SBc | 9.6 | -0.31 | 74.7 | 24.0 | 3.0 | 0.8 | 39 | 223 | 42 |

: Key parameters of our galaxy sample

Table notes: The galaxy parameters are adopted from the z0mgs (z=0 multiwavelength galaxy survey; Leroy, Sandstrom et al. ApJS accepted) database (<https://github.com/akleroy/z0mgs>), where the original references can be found. R25 taken from HYPERLEDA. $^{a}$ Position angle $^{b}$ inclination $^{c}$ the galactic radius at 25 mag arcsec$^{-2}$

Observations are reduced using a pipeline built on esorex and developed by the PHANGS team.[^2] Between 5 and 12 MUSE pointings are observed per galaxy and each is reduced individually to produce a data cube. As observations were taken under mostly photometric conditions, no additional absolute flux calibration corrections are applied except for on NGC 628 (as described in (cite: Kreckel2017; Kreckel2018)). As all metallicity diagnostics are inferred from line ratios, our main results depend only on the relative flux calibration and are insensitive to the absolute flux calibration.

The relative astrometric solution across each MUSE field-of-view is excellent ($\sim$0.04$''$). A single additional absolute astrometric correction for each pointing is obtained by comparing the white light image with reference images. For the majority of our galaxies we used SDSS r-band images as our reference. For NGC1672 we used an R-band image acquired as part of the PHANGS H$\alpha$ imaging survey (Razza et al. in prep.) with astrometry determined from GAIA (cite: GAIA_DR2), while for NGC2835 and IC5332 we used respectively an R-band image coming from the Danish 1.54m telescope (cite: Larsen1999) with an astrometric solution determined by [astrometry.net](astrometry.net). For IC5332 we used an R-band image from the CTIO LVL optical survey (cite: Cook2014). To determine the astrometric solution, both the MUSE image and the reference image were analyzed with the IDL procedure ‘find’ (an adaptation of DAOPHOT) to identify point-like sources in the image. As our MUSE fields are entirely contained within the disk of the galaxy, these often do not correspond to stars but to unresolved star-forming knots within the disk. We then cross-matched these point sources, typically finding 5-20 matches per MUSE field, and applied the average offset. Typical shifts are 1-2$''$, and systematic uncertainties are estimated to be $\sim$0.2$''$, but are dependent on the absolute accuracy of the astrometric solution in the reference image.

In order to morphologically identify the HII regions by their H$\alpha$ line emission, we first produce maps covering the full field-of-view. All data cubes are processed using the IDL toolkit LZIFU (cite: Ho2016) to fit stellar spectral templates and extract emission line fluxes. The resulting emission line maps from all pointings are combined to produce full coverage emission line maps for each galaxy. Three color images are presented for all eight galaxies in an atlas (Appendix [7](#appendix:atlas), Figures [10](#fig:prettyfig) to [17](#fig:prettyfig_cont2)). We reach a typical 3$\sigma$ surface brightness sensitivity for H$\alpha$ of $1.5 \times 10^{-17}$ erg s$^{-1}$ cm$^{-2}$ arcsec$^{-2}$.

## HII region catalogs

H$\alpha$ emission line maps are analyzed with HIIphot (cite: Thilker2000), which has been designed to morphologically isolate HII regions from diffuse ionized gas, and provide a 2D mask that identifies separate regions within the map. After identifying ‘seeds’ for the HII region peaks, their boundaries are set by identifying where the slope of the H$\alpha$ surface brightness distribution meets a user-defined termination criteria. We have adjusted the settings of HIIphot to produce realistic HII region sizes and shapes across the eight galaxies in this sample, changing only the background surface brightness sensitivity level between galaxies. We then use the resulting mask to extract integrated spectra from the data cubes. As a check, we repeated our analysis using spectra extracted from a circular $1\ensuremath{''}$ diameter aperture centered at the position of each identified region. The derived line ratios and metallicities agree with those calculated from the HII region catalogs within 0.01 dex for 84% of the sample. Thus, the exact boundaries set and choice of tuning parameters for HIIphot have only a small effect.

These integrated region spectra are then fit with GANDALF (Gas AND Absorption Line Fitting; (cite: Sarzi2006)), which simultaneously fits the stellar continuum (using pPXF - Penalized Pixel-Fitting; (cite: Cappellari2004; Cappellari2017)) and the emission line fluxes (H$\beta$, \[OIII\] $\lambda$4959,5007, \[OI\]$\lambda$6300, H$\alpha$, \[NII\]$\lambda$6548,6583, \[SII\]$\lambda$6716,6731, \[SIII\]$\lambda$9069). Emission lines are fit without tying together the line centers or kinematics, in order to account for the varying spectral resolution. We fit the stellar continuum with stellar population models taken from the (cite: Tremonti2004) library of (cite: Bruzual2003) templates across a range of ages (5 Myr to 11 Gyr) and metallicities (Z = 0.004, 0.02 and 0.05). Our results do not change significantly if we use another stellar population model (e.g. MIUSCAT stellar population synthesis models; (cite: Vazdekis2012)). All line fluxes are corrected for extinction using the Balmer decrement to infer the reddening, assuming case B recombination and T$_{\rm e}$=10$^4$K, and apply the (cite: Fitzpatrick1999) extinction law assuming a value of R$_V$=3.1. This is relatively insensitive to the assumed electron temperature, with variations by a factor of two resulting in only $\sim$0.1 magnitude difference in the V-band extinction. Using a different extinction law (e.g. (cite: Cardelli1989)) does not significantly change our results.

We then employ a number of criteria to produce our HII region catalog:

1.  Any region within 5$''$  of the edge of the full mosaic is removed, to ensure the entire region is contained within the field of view. This excludes $\sim$7% of the regions.

2.  A S/N $>$5 is required for all strong emission lines used to infer the metallicity (H$\beta$, \[OIII\], H$\alpha$, \[NII\], \[SII\]), which excludes a further $\sim$5% of the regions.

3.  Two BPT (cite: Baldwin1981) emission line ratio diagnostics are employed to ensure the excitation is consistent with photoionization by massive stars (see Appendix [8](#appendix:bpt)). In the \[OIII\]/H$\beta$ vs. \[NII\]/H$\alpha$ diagnostic, we require regions to be consistent with the stringent empirical line (cite: Kauffmann2003). In the \[OIII\]/H$\beta$ vs. \[SII\]/H$\alpha$ diagnostic, we require regions to be consistent with the (cite: Kewley2001) line. These BPT diagnostics remove another 7% of the regions.

4.  While the above removes the majority of planetary nebulae and supernova remnants, we further remove regions (15 additional regions, $\sim$0.1% of the total catalog) with large ($>$100 km s$^{-1}$) velocity dispersion that are likely compact supernova remnants.

These cuts together remove a total of $\sim$10-20% of regions from each galaxy, with the remainder comprising our HII region catalogs (Table [2](#tab:catalog1)). We list the total number of HII regions identified for each galaxy (ranging from 200-2000) in Table [1](#tab:sample).

By eye, HIIphot does an excellent job of identifying HII regions (Figures [10](#fig:prettyfig) to [17](#fig:prettyfig_cont2)), isolating the individual H$\alpha$ peaks and segmenting clustered complexes into discrete HII regions. However, it is also apparent that in rare circumstances the termination criteria is not correctly met at the HII region boundary, which results in a small number of regions that grow to unphysical sizes of up to $>$200 pc ($<$1% of regions). This is particularly clear for some of the inter-arm HII regions (e.g. on the eastern side of NGC 628). Taking the area of the irregular mask defining each HII region, we infer a size corresponding to a circular radius that would encompass the same area. Looking at this HII region size distribution (Figure [1](#fig:lfn)), we see the expected power-law behavior (cite: Azimlu+2011) up to 120pc sizes, suggesting these unphysically large regions are not introducing a significant bias, and we retain these regions in our sample.

The extinction-corrected H$\alpha$ luminosity function for our full sample is presented in Figure [1](#fig:lfn), and shows the expected power law slope with a break at $\sim 10^{39}$ erg s$^{-1}$ (cite: Bradley2006). Based on our 5$\sigma$ H$\alpha$ sensitivity for 1$''$ diameter regions, we estimate typical completeness limits of L(H$\alpha$) $\simeq$ 4 $\times$ 10$^{37}$ erg s$^{-1}$, though they vary given the range in galaxy distances. This is roughly comparable to the ionizing flux produced by a single O5V star (cite: Schaerer1997). All galaxies are fairly face-on or only moderately inclined (i$<$55$^{\circ}$), and the typical V-band extinctions we infer are quite moderate (1.0$\pm$0.3 mag), so we do not expect that we are missing a significant fraction of bright HII regions.

All HII region positions, line fluxes, and associated uncertainties are tabulated in Table [2](#tab:catalog1). The full table is available online, with only a small sample shown here. Positions reflect the geometric center of each identified HII region, without any intensity weighting. The integrated H$\alpha$ luminosity and all emission line fluxes have been extinction corrected, as described above and are listed in the table in absolute flux units.

| parameter | unit |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| ID |  | ngc628_0001 | ngc628_0002 | ngc628_0003 |
| ra$^{a}$ | degrees | 24.175116 | 24.194861 | 24.170381 |
| dec$^{a}$ | degrees | 15.784356 | 15.788300 | 15.793022 |
| R/R$_{25}$ |  | 0.01 | 0.25 | 0.12 |
| E(B-V) | mag | 0.00$\pm$ 0.02 | 0.30$\pm$ 0.05 | 0.40$\pm$ 0.03 |
| L(H$\alpha$) | 1e36 erg s$^{-1}$ | 4.56$\pm$ 0.03 | 5.08$\pm$ 0.05 | 5.01$\pm$ 0.04 |
| H$\beta$ | 1e4 erg s$^{-1}$ cm$^{-2}$ | 1.68$\pm$ 0.16 | 1.55$\pm$ 0.37 | 1.54$\pm$ 0.22 |
| \[OIII\]$\lambda$5007 | 1e4 erg s$^{-1}$ cm$^{-2}$ | 0.69$\pm$ 0.08 | 1.00$\pm$ 0.25 | 0.32$\pm$ 0.08 |
| H$\alpha$ | 1e4 erg s$^{-1}$ cm$^{-2}$ | 3.99$\pm$ 0.21 | 4.45$\pm$ 0.54 | 4.39$\pm$ 0.33 |
| \[NII\]$\lambda$6583 | 1e4 erg s$^{-1}$ cm$^{-2}$ | 1.73$\pm$ 0.10 | 1.40$\pm$ 0.19 | 1.77$\pm$ 0.15 |
| \[SII\]$\lambda$6716 | 1e4 erg s$^{-1}$ cm$^{-2}$ | 0.69$\pm$ 0.05 | 1.04$\pm$ 0.13 | 0.64$\pm$ 0.05 |
| \[SII\]$\lambda$6731 | 1e3 erg s$^{-1}$ cm$^{-2}$ | 5.04$\pm$ 0.38 | 6.90$\pm$ 0.94 | 3.82$\pm$ 0.37 |
| \[SIII\]$\lambda$9069 | 1e3 erg s$^{-1}$ cm$^{-2}$ | 6.93$\pm$ 0.70 | 1.93$\pm$ 0.53 | 1.68$\pm$ 0.30 |
| 12+log(O/H) |  | 8.57$\pm$ 0.05 | 8.46$\pm$ 0.13 | 8.61$\pm$ 0.08 |

: HII region catalog (online only, example data for 3 regions)

Table notes: $^{a}$ J2000

## Ancillary data

We compare our MUSE results to spectroscopic imaging of the CO (2-1) line from the PHANGS-ALMA survey (PI E. Schinnerer). The sample selection, observations, and data reduction for PHANGS-ALMA are described in A. K. Leroy et al. (in preparation). Briefly, we observed each target with ALMA’s main array in a compact configuration and with the 7-m arrray and single dish (“total power”) telescope. The combination of these observations yield CO line data cubes with resolution $\approx 1''{-}2''$ and sensitivity to emission on all spatial scales. The standard PHANGS-ALMA products include integrated intensity (“moment 0”) maps, maps of the peak intensity (“$T_{\rm peak}$”) at any velocity along each line of sight, intensity-weighted mean intensity (“moment 1”) maps, and several line width estimates. Here we use the velocity dispersion estimated from the rms scatter of emission about the intensity-weighted mean velocity (i.e., the “moment 2” line width). Use of an alternate parameterization of the molecular gas line width does not significantly change our results. The kinematic measurements at high resolution require reasonable S/N, and so have limited coverage in IC 5332 and NGC 2835, which both have relatively low stellar mass and correspondingly weak CO emission. Maps for six of our eight targets have appeared before (cite: Sun2018; Kreckel2018; Utomo2018), and we refer the reader to those papers for additional visualizations and details.

The surface brightness sensitivity of the CO maps becomes higher at coarser resolution. At the $\approx 7''$ resolution of ALMA’s 7-m telescopes, we detect essentially all CO emission from all targets, including IC 5332 and NGC 2835. When computing the general distribution of molecular gas, we use a low resolution, high completeness version of the moment 0 maps created at this lower resolution of the 7-m data.

FUV emission was observed by the Galaxy Evolution Explorer (GALEX) satellite, with all maps taken from the GALEX archive using the longest exposure time available for each galaxy. Most are taken from guest investigator programs with 1.7-21 ksec exposures. NGC 1087 was observed as part of the Medium Imaging survey with a 3 ksec exposure, and NGC 1672 was observed as part of the Nearby Galaxy Survey (cite: GildePaz2007) with a 2.7 ksec exposure. Only NGC 2835 has a significantly shorter (100 second) exposure time from the All-Sky Imaging Survey. Images are used at the native 4.5$''$ angular resolution. FUV fluxes are extinction corrected based on the observed Balmer decrement assuming a (cite: Fitzpatrick1999) extinction law, including a factor of two decrease in the reddening E(B-V) assumed for the stellar UV emission in relation to the nebular H$\alpha$ emission (cite: Kreckel2013).

# HII region physical conditions

We present a sample of eight galaxies with unprecedented statistics, identifing a total of 7138 HII regions, with measurement of 200-2000 HII region metallicities per galaxy. We outline here our method for inferring the gas phase oxygen abundance (metallicity), and present the radial gradients observed within each galaxy.

## Strong line metallicities

There is a long standing debate in the literature regarding how best to calculate the gas phase oxygen abundances using only strong emission lines, where the HII region electron density and temperature cannot be directly measured. Empirical calibrations are determined by comparing different strong line ratios with metallicities calculated from faint auroral line detections, that are used to estimate the electron temperature and therefore ‘directly’ measure ionic abundances. This $T_\textrm{e}$ method is often viewed as the ‘gold standard’ for determining metallicity ((cite: Skillman1989; Garnett2002; Stasinska2007; Bresolin2007; Berg2015; McLeod2019); but see (cite: Blanc2019)). Alternately, theoretical calibrations are determined by comparing different strong line ratios with photoionization model grids. For the same datasets, systematic offsets of 0.2 dex are found between empirical and theoretical calibrations (cite: Kewley2008; Blanc2015). While we do detect auroral line emission in $\sim$20-50 HII regions per galaxy (Ho et al. in prep.), this is an order of magnitude fewer than the number of regions for which we can identify and measure strong line fluxes.

As our MUSE observations do not cover the \[OII\]$\lambda$3727 emission line, only a limited number of strong line prescriptions are available for determining the metallicity (see Appendix [9](#appendix:prescriptions)). All calculations in this paper adopt the empirical (cite: Pilyugin2016) S-calibration (Scal). It relies on the following three standard diagnostic line ratios:\
$N_2$ = $I_{\rm [N\,II] \lambda 6548+ \lambda 6584} /I_{{\rm H}\beta }$,\
$S_2$ = $I_{\rm [S\,II] \lambda 6717+ \lambda 6731} /I_{{\rm H}\beta }$,\
$R_3$ = $I_{{\rm [O\,III]} \lambda 4959+ \lambda 5007} /I_{{\rm H}\beta }$.\
Here we have measured only the stronger line in both the \[OIII\] and \[NII\] doublets and assume a fixed ratio of 3:1. The Scal prescription is defined separately over the upper and lower branches in log$N_{2}$, with almost all HII regions in our sample falling on the upper branch (log$N_{2} \ge -0.6$), as $$\begin{eqnarray}
\footnotesize
       \begin{array}{lll}
     {\rm 12+log(O/H)}  & = &   8.424 + 0.030 \, \log (R_{3}/S_{2}) + 0.751 \, \log N_{2}   \\  
                          & + &  (-0.349 + 0.182 \, \log (R_{3}/S_{2}) + 0.508 \log N_{2})   \\ 
                          & \times & \log S_{2}   \\ 
     \end{array}
\label{equation:ohsu}
\end{eqnarray}$$

and the lower branch (log$N_{2} \le -0.6$) is calculated as $$\begin{eqnarray}
\footnotesize
       \begin{array}{lll}
     {\rm 12+log(O/H)}  & = &   8.072 + 0.789 \, \log (R_{3}/S_{2}) + 0.726 \, \log N_{2}   \\  
                          & + &  (1.069 - 0.170 \, \log (R_{3}/S_{2}) + 0.022 \log N_{2})    \\ 
                          & \times & \log S_{2}   \\ 
     \end{array}
\label{equation:ohsl}
\end{eqnarray}$$

We prefer this metallicity calibration as it shows small intrinsic scatter versus the auroral line metallicities for the same regions. This is quoted to be $<$0.1 dex across the full metallicity range (cite: Pilyugin2016). A more recent investigation comparing metallicity calibrations reports systematic $\sim$0.17 dex scatter for this prescription, as good or better than all other tested calibrations, and similar to the best results achieved from a machine learning approach (cite: Ho+2019). Furthermore, Scal relies on a combination of three emission line ratios, an important improvement over past calibrations, which allows it to correct for dependencies with the ionization parameter (cite: Pilyugin2016). Finally, we find that this prescription systematically shows the smallest scatter (0.03-0.05 dex) around the radial metallicity gradient compared to alternate metallicity prescriptions (see Appendix [9](#appendix:prescriptions)). While this does not necessarily mean this method is the most accurate, we do not expect any method to imply a scatter lower than the true scatter. Some further discussion on this point is presented in Section [5.2](#sec:dis:azimuth). The Scal metallicity for each HII region is listed in Table [2](#tab:catalog1). Two-dimensional maps of the identified HII regions, each colored by the measured metallicity, are shown in Figures [10](#fig:prettyfig) to [17](#fig:prettyfig_cont2).

While a detailed exploration of the differences between empirical and theoretical metallicity calibrations is beyond the scope of this paper, we find very good qualitative agreement between the metallicity trends and correlations presented here with an analysis performed using the (cite: Dopita2016) photoionization model based N2S2 prescription. The reported trends and corrleations also do not change qualitatively when using the Bayesian inference code IZI (cite: Blanc2015) to derive the joint and marginalized posterior probability density functions for metallicity and ionization parameter given a set of observed line fluxes and an input photoionization model. This further increases our confidence in the robustness of the presented results. We do note that our results change qualitatively when using the (cite: Marino2013) O3N2 and N2 calibrations. However, because these use smaller dimensionality in the line ratios, we believe both of these alternative calibrations retain the degeneracy between metallicity and ionization parameter, enough to cloud the subtle trends presented here. Select results using additional calibrations are shown in Appendix [9](#appendix:prescriptions), along with a more detailed discussion of how results presented in this paper would change if the analysis was performed with an alternate calibration.

## Radial metallicity gradients

The rightmost panels in our atlas (Appendix [7](#appendix:atlas), Figures [10](#fig:prettyfig) to [17](#fig:prettyfig_cont2)) map the Scal metallicity of each HII region in each galaxy. These figures show clearly both the different mean metallicity between galaxies (linked to the mass-metallicity relation; (cite: Tremonti2004)), and also the known trend of metallicity decreasing with galactic radius. On top of this however, there appear to be higher-order trends with suggestive links to galactic features like bars and spiral arms.

We perform a first order linear fit to the radial gradient (Figure [2](#fig:gradients)). We include in the fit the determined errors for all line flux measurements, including the uncertainty in the flux measurements due to the uncertainty in our measurement of E(B-V). We exclude the inner 0.1R$_{25}$ when performing our fit, as it could be biased by nuclear ionization sources. We also calculate the running median in radial bins, and find very good agreement with our simple linear fit. Coefficients for radial gradients in each galaxy are shown in Figure [2](#fig:gradients) and tabulated in Appendix [9](#appendix:prescriptions) (Table [3](#tab:gradients)). All galaxies show small (0.03-0.05 dex) systematic scatter after accounting for the radial trends.

## Ionization Parameter

The structure of an HII region is set by the ionizing radiation provided by the central star(s) acting on the surrounding ISM. For the simplistic case of a spherically symmetric HII region that has achieved equilibrium, this balance can be parameterized in terms of the dimensionless ionization parameter, U = Q(H$^{0}$)/(4$\pi$R$^2$$n$$c$), where Q(H$^0$) is the number of hydrogen-ionizing photons (E $>$ 13.6 eV) emitted per second, R is the empty (wind-blown) radius, $n$ is the hydrogen density, and $c$ is the speed of light. Direct interpretation of this parameter is challenging, as there are degeneracies between the ionizing flux produced by a single very young star as opposed to a cluster of slightly older stars. Moreover, detailed studies of resolved HII regions reveal asymmetric and broken shells surrounding the ionizing sources (cite: Pellegrini2011; Pellegrini2012). Nonetheless, this parameter is still useful as it encodes information about the local physical conditions, with higher values typically indicating a stronger ionizing source or a lower ionized gas density.

Photoionization modeling has been used to constrain the ionization parameter through different diagnostic line ratios (cite: Kewley2002; Dors2011). \[OIII\]$\lambda$5007/(\[OII\]$\lambda$3726+\[OII\]$\lambda$3729) has frequently been used to constrain the ionization parameter, but has a strong dependence on metallicity. (\[SIII\]$\lambda$9069+\[SIII\]$\lambda$9532)/(\[SII\]$\lambda$6716+\[SII\]$\lambda$6731) also shows a positive correlation with ionization parameter, and is a much more direct diagnostic of the ionization parameter, with only a weak dependence on metallicity and no sensitivity to the ISM pressure between between 4 cm$^{-3}$ K $<$ log(P/k) $<$ 7 cm$^{-3}$ K. This makes \[SIII\]/\[SII\] the best ionization parameter diagnostic available in the optical, although the long wavelength \[SIII\]$\lambda$9069,9532 lines have not often been observed. With MUSE we observe the \[SIII\]$\lambda$9069 line flux, and for our calculations we assume the fixed theoretical line ratio of \[SIII\]$\lambda$9532/\[SIII\]$\lambda$9069 = 2.5 (cite: Vilchez1996), which is well determined from the transition probabilities. Figure [3](#fig:gradients_q) presents the radial gradients of \[SIII\]/\[SII\], tracing the radial ionization parameter gradient. All gradients are very close to being flat within the inner part of the galaxy disks, as also found in (cite: Poetrodjojo2018).

We choose in this paper to present results related to the ionization parameter directly in terms of the observed line ratios, and remind the reader that a positive linear correlation is expected between log(\[SIII\]/\[SII\]) and U. Various prescriptions (e.g. (cite: Kewley2002; Dors2011)) are available in the literature to convert a measured \[SIII\]/\[SII\] line ratio to a value for U (or q = U/c), however they differ by an order of magnitude.

## Diffuse ionized gas

The diffuse ionized gas (DIG) is seen in disk galaxies as an extended, relatively smooth background in emission line maps (cite: Zurita2000). The DIG contributes $\sim$40-60% of the total H$\alpha$ flux observed within any disk galaxy (cite: Ferguson1996; Zurita2000; Thilker2002; Oey2007; Chevance2019), and even at the location of individual HII regions has been shown to contribute at significant levels (20–80%, (cite: Kreckel2016)) that vary by local environment (e.g. arm/interarm). DIG is detected predominantly in the H$\alpha$, H$\beta$, \[NII\] and \[SII\] line maps, as these lines are strongly emitted in the low density, high temperature diffuse gas (cite: Haffner2009). One major advantage of the high physical resolution of the maps employed in this work is that we can spatially distinguish HII regions from the surrounding diffuse emission, which when blended over larger apertures has been shown to artificially flatten metallicity gradients (cite: Poetrodjojo2019). The emission line fluxes and H$\alpha$ luminosities reported here do not include any correction for the diffuse ionized gas background contributing to the integrated line flux, as seen in projection against any given HII region. A major goal of the PHANGS collaboration is to develop and compare spectroscopic, morphological, and hybrid estimators of the DIG. At this time, we lack such rigorous methods to identify the DIG, and we view imposing such a correction as premature. As such, we have chosen to exclude such a correction from our reported line fluxes and subsequent analysis as it would strongly depend on our choice of HII region boundary.

We estimate the effect this un-subtracted diffuse background could have on our inferred metallicities by using our emission line maps to measure the median line flux per pixel over an annular aperture surrounding each HII region in our masks. The aperture size is scaled corresponding to the observed HII region size, and is typically 0.6-2$''$ wide. Here we have masked any neighboring HII regions to ensure minimal contamination of our measurement. Our DIG flux fractions are consistent with those obtained through other methods (cite: Hygate2019; Chevance2019). As in (cite: Kreckel2016), we observe order of magnitude variations in DIG surface brightness across each disk at the locations of HII regions, with the most H$\alpha$ luminous HII regions showing lower fractional DIG contribution ($\sim$10-20%) compared to fainter HII regions, with contributions as high as $\sim$80%. For this calculation, we identify a subset of regions where the H$\alpha$ DIG background is 50% or less. For all emission lines we then subtract the estimated DIG level from our HII region line fluxes. We then use these DIG-subtracted line fluxes to calculate the metallicity as described in Section [3.1](#sec:metals). We find that subtracting the DIG emission would result in a slight ($\sim$0.02 dex) systematic increase in our inferred metallicities, and an increased systematic scatter (0.05-0.1 dex) across the sample. This increased scatter washes out some of the weaker azimuthal variations we see, but does not qualitatively change the strongest trends we observe in NGC 1672 and NGC 1087.

This diffuse background more strongly impacts our inferred ionization parameters via our measurement of the \[SIII\]/\[SII\] line ratios, as \[SIII\] is predominantly confined to the HII regions while \[SII\] is emitted strongly in the diffuse gas. Correcting for the DIG contribution to the \[SII\] line would result in a $\sim$70% increase in the \[SIII\]/\[SII\] line ratios but does not qualitatively change the trends described in the following sections.

# Results

## Trends with local physical conditions

Within each of our galaxies we observe a positive correlation between the metallicity and ionization parameter of the HII regions (Figure [4](#fig:q_z)), with an offset between different galaxies that is set by the difference in stellar mass of the systems. As the ionization parameter shows no radial gradient, this is not simply a result of correlated observables. Similarly, while many emission line diagnostics can be influenced by both the metallicity and the ionization parameter, we have selected a metallicity prescription that has been defined by carefully fitting a three dimensional parameter space of diagnostic line ratios in order to minimize the degeneracies.

This positive correlation conflicts with theoretical predictions, which state that as stellar atmospheres of massive O stars become cooler with increasing metallicity there will be enhanced line and wind blanketing, resulting in a negative correlation (cite: Massey2005). Most previous studies have found either negative correlations (cite: Bresolin1999; Nagao2006) or no correlation (cite: Kennicutt1996; Garnett1997; Dors2011; Poetrodjojo2018). However, they combined observations from different galaxies. Our analysis shows a clear trend within individual galaxies, that would be obscured when taken together if one studied only a few regions from each of several galaxies. A positive correlation has previously been observed in a sample of luminous infrared galaxies (cite: Dopita2014). These authors discuss this result mainly as a positive correlation between star formation rate surface density and ionization parameter, which they attribute to a difference in geometry. In this case, dense star-forming regions could contain inclusions of molecular clouds undergoing violent radiation pressure dominated photo-ablation close to the exciting stars, resulting in a positive correlation between star formation surface density and ionization parameter. See Section [5.1](#sec:dis:localprops) for further discussion on this.

To account for the metallicity offsets between galaxies introduced by the mass-metallicity relation, we subtract off the fitted radial metallicity gradients, and consider the residuals from the linear trend ($\Delta$O/H, measured in logarithmic units). Apparent from our visualization of the metallicities across the galaxy disks (Figures [10](#fig:prettyfig) to [17](#fig:prettyfig_cont2)) is the tendency for the more luminous (and more spatially extended) HII regions to be more enriched. The left panel of Figure [5](#fig:offsets) traces this trend directly, demonstrating that $\Delta$O/H  increases systematically as a function of HII region luminosity for all galaxies in our sample, with a Spearman’s rank correlation coefficient ($\rho$) of 0.34 and high statistical significance (p$<$0.001). In total, we see a 0.03 dex increase in metallicity for the most luminous (L$_{\rm H\alpha}$ $>$ 10$^{38.5}$ erg/s) regions.

Moreover, we observe a much tighter correlation between $\Delta$O/H  and ionization parameter (\[SIII\]/\[SII\]). We observe a stronger correlation ($\rho$=0.63) for the sample as a whole, as well as improved correlation compared to the trends for individual galaxies between 12+log(O/H) and ionization parameter (Figure [4](#fig:q_z)). This suggests the local physical conditions are very tightly linked to the localized enrichment of the ISM.

## Physical conditions of regions with enhanced and reduced abundances

We split the sample of HII regions into those with (a) typical metallicities (-1$\sigma$ $<$ $\Delta$O/H$<$ 1$\sigma$), (b) enhanced metallicity ($1\sigma$ $<$ $\Delta$O/H), and (c) reduced metallicity ($\Delta$O/H$<$ -1$\sigma$). In Figure [6](#fig:histos) we show how the distributions of six physical parameters differ between the three samples. For all parameters explored, we find that the distribution of HII regions with enriched/reduced metallicity is significantly different from the average sample. They show a Kolmogorov-Smirnov (KS) test probability value (p-value) less than 1e-6, allowing us to reject the null hypothesis that the two samples are drawn from the same distribution.

As shown in Figure [5](#fig:offsets), the clearest correlation we see is with ionization parameter (\[SIII\]/\[SII\]). As this traces the relative density of ionizing photons to the surrounding ISM gas density, we expect to find additional dependencies on the stellar cluster age and on the local gas properties. In general, we expect HII regions with younger, more massive star clusters and a denser surrounding medium to be characterized by higher ionization parameter values.

The H$\alpha$-to-FUV flux ratio has been shown to correlate with star cluster age (cite: Sanchez-Gil2011), with younger clusters having larger flux ratios. We use GALEX imaging to measure the FUV flux at the position of each HII region. In measuring the H$\alpha$ flux we have convolved the H$\alpha$ images to matched 4.5$''$ resolution. We find that the HII regions with enhanced metallicities tend towards higher extinction corrected H$\alpha$-to-FUV flux ratios (younger star cluster ages). A similar trend is seen if we instead use the equivalent width of H$\alpha$ as a tracer of star cluster age.

To probe the local ISM gas conditions, we use PHANGS-ALMA maps of the CO emission (Leroy et al. in prep.) at 1$''$  spatial resolution to measure the local molecular gas surface density. While the angular resolution is well matched to our MUSE observations, this molecular material is necessarily not co-located with the ionized gas of the HII region, and on our working $\sim$50 pc scales is likely associated with molecular clouds and associations neighboring the HII regions (see also (cite: Kreckel2018)), potentially representing the remnant of the cloud from which the HII region formed (cite: Chevance2019; Kruijssen2019). We find that the HII regions with enhanced abundances are at locations where we measure higher CO integrated intensity, indicating a higher molecular gas surface density compared to the HII regions with reduced abundances.

A change in the local ISM conditions is also seen when looking at the dust column along the line of sight (traced by the color excess, E(B-V)), which is generally thought to be well mixed with the gas. Here we find that the HII regions with enhanced metallicities see higher dust columns along the line of sight, consistent with the previously described association with higher CO integrated intensity, and implying higher gas surface densities. We note that this increased extinction is not enough to significantly bias our ability to detect enriched but low luminosity HII regions. Increased electron densities are also directly seen corresponding to the HII regions with enhanced metallicity by comparing the density sensitive line ratio \[SII\]$\lambda$6716/\[SII\]$\lambda$6731, though in most regions the ratio suggests electron densities at or below the low-density limit ($<$100 cm$^{-3}$).

The velocity dispersion in the H$\alpha$ line indicates the dynamical state of the ionized gas. In contrast to the HII regions with enhanced abundances, the HII regions with decreased abundances exhibit increased velocity dispersions (deconvolved from the instrumental resolution). This could indicate a difference in the large scale mixing acting on the ISM, which would be needed to introduce less enriched material. We also see a slight (2 km s$^{-1}$) average increase in line width in the molecular gas phase for the most enriched regions (not shown), suggestive of the ongoing impact of stellar feedback or association with more massive molecular clouds, but with less statistical significance (p-value of 0.002). This further suggests a (weak) local correlation between the H$\alpha$ luminosity and the molecular gas line width.

To explore the spatial distribution of HII regions with abnormal abundances, we show in an atlas (Appendix [10](#appendix;azimuthal), Figures [23](#fig:unwrap628) to [30](#fig:unwrap5332)) the azimuthal and spatial distribution of the metal offsets and the positions of these abnormal populations with respect to the $\sim 500$ pc scale bulk CO emission (as measured by ALMA) of each galaxy. Here, our deliberate choice of low resolution observations is designed to achieve high completeness in the integrated intensity. We use this CO map to trace the gas response to the underlying gravitational potential and other large scale hydrodynamical effects.

While the azimuthal trends of HII regions with reduced and enhanced abundances are discussed in more detail in the following section, we highlight here the difference between the spatial distribution of the two populations across the galaxy disks. Both populations are found across the full disks, but the HII regions with reduced abundances are slightly more clustered in their distribution. Future work will explore in more detail the statistical properties of the HII region metallicity distribution. Here we simply quantify this by calculating the average distance of the three nearest neighbors (n$_3$) of all HII regions with enhanced and reduced abundances. Computing this statistic using a larger number of neighbors shows similar trends but (naturally) larger clustering sizes. These trends are not dependent on the threshold we choose to separate the regions with enhanced and reduced abundances. As the enriched regions are only slightly larger on average in size than the total population (49 pc in radius compared to 45 pc), this cannot account for the systematic differences in clustering scale that we observe.

Figure [8](#fig:n3) (left) shows a large scatter across this measure, but most galaxies show clustering on $\sim$300 pc scales of the reduced metallicity regions while enhanced metallicity regions are more widely distributed (n$_3$ $\sim$ 400-600 pc; see also Figure [7](#fig:zoomaz)). This suggests a connection between clustering and mixing, where isolated young regions with a history of star formation have the chance to become enriched (cite: Ho2017; Ho2018). We further compare the clustering of the outliers in relation to the full HII region population (Figure [8](#fig:n3), right), relative to the average, and again find that the HII regions with enhanced metallicities are less clustered.

## Azimuthal Metallicity Variations

We find that the most enriched HII regions are distributed across the disk, and simple statistical approaches where we try comparing changes in $\Delta$O/H  with large scale environment (arm/interarm/bar), overdensities in stellar mass surface density, or dynamical tracers of the spiral pattern are inconclusive. For this paper, we simply present a few visualizations of how changes in $\Delta$O/H  are distributed spatially across the disk as an atlas in Appendix [10](#appendix;azimuthal) (Figures [23](#fig:unwrap628) to [30](#fig:unwrap5332)). These images demonstrate the wealth of information we now have, but also the complicated nature of disentangling the preliminary azimuthal trends we see from their complicated environmental dynamics that vary widely between galaxies due to differences in their disk structure.

To match the metallicity maps presented in Appendix [7](#appendix:atlas), we similarly take our HII region mask and paint on the measured $\Delta$O/H  corresponding to each HII region. NGC 628, NGC 1087, NGC 1672 and NGC 2835 all show regular azimuthal variations at select rings. Such clear trends are not necessarily seen at all radii. NGC 3627 shows large scale variations with much less regular patterns, but the remaining three galaxies show no obvious azimuthal trends. Subsections of the four galaxies showing the clearest signatures of azimuthal variations are highlighted in Figure [7](#fig:zoomaz). The morphology would suggest that this implies some correlation with the spiral structure, but when we compare the azimuthal metallicity variations with the total extinction-corrected H$\alpha$ luminosity around the azimuthal ring (tracing the spiral structure), the connection is not so clear.

Enriched regions on the spiral arm often form a relatively narrow ridge, implying that the total count of such regions is not high (in contrast to high numbers in a thicker ridge). This may partially explain why its not so easy to pick out trends when considering the population as a whole. This is particularly apparent in NGC 1087 and NGC 1672, but also to a lesser extent in NGC 628, NGC 2835, NGC 3627 and NGC 4535. The narrowness of this feature is in good agreement with the highly filamentary alignment of star-forming giant molecular clouds seen along spiral arms at high ($\sim$50 pc) spatial resolution in nearby galaxies (cite: Schinnerer2017; Kreckel2018; Kruijssen2019), and consistent with the association of the enriched regions with local conditions exhibiting high dust column and gas density (see Section [4.2](#sec:trends)). The regions with reduced abundances show a wider, more clustered distribution (see also Figure [8](#fig:n3)). They are often seen on the trailing side of the spiral arm (particularly on the eastern arm of NGC 1672). This is in very good agreement with the azimuthal variations identified by (cite: Ho2017; Ho2018).

In conclusion, we qualitatively identify half of our sample (NGC 628, NGC 1087, NGC 1672 and NGC 2835) as having azimuthal variations that are tenuously associated with the spiral pattern. The link to gas density can also be interpreted as indirect evidence for the influence of spiral arms, which tend to yield locally enhanced gas densities. Establishing more conclusively whether a correlation with the spiral pattern exists in a given galaxy will require an informed view of the dynamical structure specific to that disk.

# Discussion

In this first look at a sample of galaxies with thousands of spatially isolated ($<$100 pc scale) HII regions, we can begin to explore systematic trends and patterns in the abundance distributions.

## Localized enrichment within galaxy disks

We observe clear correlations between increased abundances relative to the radial trend ($\Delta$O/H) and the local physical conditions of the ISM (Figures [5](#fig:offsets) and [6](#fig:histos)). The most fundamental positive correlation arises from changes in the ionization parameter (traced here by \[SIII\]/\[SII\]), which tracks changes in the ionizing source, the ISM density and HII region geometry. Given how flat the radial ionization parameter gradient is (Figure [3](#fig:gradients_q)), the high degree of correlation (Spearman’s rank correlation coefficient ($\rho$) of 0.60) between $\Delta$O/H  and \[SIII\]/\[SII\] is quite striking.

Without removing the radial metallicity gradient, a trend between metallicity and ionization parameter is still apparent (Figure [4](#fig:q_z)). Here, each galaxy appears offset in metallicity due to the well established relation between stellar mass and metallicity (cite: Tremonti2004), and the correlation for any individual galaxy is weaker compared to the correlation within that galaxy when instead considering $\Delta$O/H. Given that previous work generally has compared HII region metallicities and ionization parameters by combining results from different galaxies with differing global metallicities (cite: Bresolin1999; Dors2011), it is not surprising that the trends we now identify within individual galaxies would be washed out.

A similar positive correlation between metallicity and ionization parameter was reported in (cite: Dopita2014) for their analysis of resolved regions within ten Luminous Infrared Galaxies (LIRGs). They observed similar trends between star formation rate and ionization parameter as well as between metallicity and ionization parameter, and argue that the trend arises as more active star-forming regions have a different distribution of molecular gas which favour higher ionization parameters. However, we are observing these trends within normal star-forming disk galaxies and, as we see in Figure [5](#fig:offsets), the observed trend is much weaker with the HII region H$\alpha$ luminosity, and the high metallicity outliers are not more strongly clustered (Figure [8](#fig:n3)). Also, while we do see that more enriched regions preferentially fall along the ridge of spiral arms in some regions of some galaxies, they are also found distributed throughout the disk, with no strong systematic trends with galaxy environment (see also Section [5.2](#sec:dis:azimuth)). This suggests another explanation is required.

As we show in Figure [6](#fig:histos), other local conditions correlate with the local changes in metallicity. Compared to the depleted regions, enriched regions have higher H$\alpha$-to-FUV flux ratios (indicating younger star cluster ages), higher E(B-V) (indicating more dust along the line of sight), and lower \[SII\]6716/\[SII\]6731 line ratios (indicating larger electron densities). They also show higher CO intensity (indicating higher molecular gas surface densities) and slightly larger CO line widths (indicating kinematic disturbance in the local ISM). We note that the ISM conditions inferred from the CO are on matched angular scales (1$''$ $\sim$ 50pc) but this material by nature does not co-exist with the ionized HII region, so making a direct link between the physics occurring in these two different ISM phases is not straightforward. The trends, however, are very interesting, as they might represent two different evolutionary phases of the same underlying star-forming region even if they are somewhat spatially offset (cite: kruijssen18).

As the HII region metallicity generally reflects the ISM abundances locally before it was illuminated by the newest generation of stars, these trends are suggestive of a star formation history that has locally enriched the ISM. Recent work has suggested that star-forming complexes can host extended continuous star formation histories spanning $\sim$10 Myr (cite: Ramachandran2018; Rahner2018). We see small systematic scatter in $\Delta$O/H, and HII regions with enhanced abundances typically show offsets of $\sim$0.05 dex. We perform a simple calculation to explore how much enrichment could be expected from a single generation of stars.

For a cloud of gas mass $M_{\rm g}=5.8\times$10$^5$ M$_\ensuremath{\odot}$ (the typical GMC mass in NGC 628; (cite: Kreckel2018)) and an integrated star formation efficiency per star formation event of $\epsilon$=0.05 (measured within the PHANGS sample; (cite: Chevance2019)), this would produce $M_{\rm *,produced}=M_{\rm g}$ $\times$ $\epsilon$ = 2.9$\times$10$^4$ M$_\ensuremath{\odot}$ of new stars. Then, given an oxygen yield of y$_o$ = 0.00313 (based on observations; (cite: Kudritzki2015)), when the massive stars die they return $M_{\rm O, produced}=M_{\rm *,produced}$ $\times$ y$_o$ = 91 M$_\ensuremath{\odot}$ of oxygen to the surrounding ISM. Assuming perfect mixing within the cloud, this gives an upper limit on how much extra oxygen (by mass) can be added in one generation. Converting this to the change in oxygen abundance, this corresponds to an increase in log(O/H) of $\sim$0.02 dex with each generation of star formation. However, the oxygen yield is quite uncertain, and taking a theoretically motivated, higher oxygen yield of y$_o$=0.04 (cite: Vincenzo2016) would result in an increase in log(O/H) of $\sim$0.18 dex. This demonstrates that the level of enrichment we report in this sample of eight galaxies is roughly consistent with what could be produced by a single generation of star formation.

We believe this is unlikely to be due to self-enrichment from a single burst of star formation, but could be consistent with an extended 5-10 Myr continuous star formation history. Typical supernova timescales (4 Myr; e.g. (cite: Leitherer2014)) and subsequent mixing timescales over $<$100 pc scales (2 Myr; (cite: deAvillez2002)) are roughly equivalent to the expected HII region lifetime (6-8 Myr; e.g. (cite: Kennicutt1998; Chevance2019)). Better constraints on the HII region ages are needed to distinguish these scenarios. Simulations indicate that larger scale ($\sim$kpc) mixing is relatively inefficient (taking 100-350 Myr; (cite: deAvillez2002; Roy1995)), making it plausible that subsequent generations of stars could form before mixing has finished.

## Subtle evidence for azimuthal variations

In all galaxies we observe a very small systematic scatter (0.03-0.05 dex) after subtracting the radial gradients. This scatter is generally smaller than the amplitude of the radial variation, which typically ranges from 0.1 to 0.3 dex over the radial range we observe. It has been previously shown that strong line methods systematically produce smaller scatter in their radial gradients than direct temperature methods (cite: Arellano-Cordova2016), but this very small systematic scatter with respect to the radial gradient is similar to what has been found using direct temperature methods to measure the metallicity in the Milky Way (cite: Esteban2018). It is, however, much smaller than what has been found with direct temperature methods for three nearby galaxies by the CHAOS project ($\sim$0.1 dex; (cite: Croxall2015; Berg2015; Croxall2016)) and in M33 (0.11 dex; (cite: Rosolowsky2008)).

We find azimuthal variations in half of the galaxies in our sample, but these trends are not always obviously associated with the spiral pattern. In all cases the azimuthal trends are more pronounced on only one spiral arm. In general, we find that HII regions with enhanced or reduced metallicity are located across the full disk. Because of this, we have failed to distinguish any systematic correlations between changes in $\Delta$O/H  and environmental parameters (arm/interarm masks, stellar mass surface density offset). This suggests that while the spiral pattern plays a role in organizing the ISM, it alone does not establish the azimuthal variations we observe, with changes also being driven by the strong correlations with the local physical conditions described in Section [5.1](#sec:dis:localprops).

NGC 1672 presents a particularly interesting case (Figure [7](#fig:zoomaz)), as the eastern arm shows a very clear ridge along the spiral arm with enhanced abundances. This appears very similar to the situation observed in the nearby galaxy NGC 1365 (cite: Ho2017), with its widely separated spiral pattern, for which those authors proposed a carousel model where enrichment can proceed slowly in small pockets as gas passes through the interarm region, with enrichment peaking at the spiral arm. Passage through the spiral arm then triggers large-scale mixing, introducing more pristine gas from the surroundings and hence systematically decreasing the abundances. NGC 6754 (cite: Sanchez-Menguiano2016) presents another case of azimuthal abundances attributed to the spiral pattern, however in this case the drop in abundances is attributed to radial streaming motions that introduce more pristine gas to decrease the abundances, with trends differing on the leading and trailing sides of the arm.

The azimuthal variations reported here present a more complicated picture. Half of our eight galaxies show azimuthal variations, though often the case is much clearer across one half of the galaxy. NGC 1087 and NGC 1672 clearly show enhanced abundances along the spiral arm, but one is more flocculent while the other has a strong bar and a more pronounced spiral pattern. They also show different distributions for the enhanced regions, with NGC 1672 exhibiting a narrow ($<$100 pc) ridge while NGC 1087 has a broader ($\sim$300 pc) enhanced region along the arm. NGC 628 and NGC 2835 show some regular azimuthal variations, but they do not correspond to the peaks in star formation. One significant difference between this study and previous work is our focus on the inner portions of the disk (R$<$0.5 R$_{25}$), whereas some recent theoretical work has suggested that azimuthal trends should be more pronounced in the outer disks near the corotation radius, where the relative velocity with respect to the pattern speed of the disk is close to zero (cite: Spitoni2019).

(cite: Sanchez-Menguiano2019) carried out a detailed investigation of the local relation between star formation rate and metallicity, where for both quantities a radial relation has been removed. They find systematic trends, that transition from a negative correlation at lower stellar masses to a positive correlation at higher stellar masses. While it is the case that the three most massive galaxies in our sample do not show azimuthal variations, the stellar masses for all galaxies in our sample do not range over more than an order of magnitude, so it is difficult to draw strong conclusions. Further progress could be made with more detailed dynamical models of each individual galaxy, but is beyond the scope of this paper.

## Barred galaxies with flat metallicity gradients

Stellar bars drive gas inflows (cite: Kormendy2004; Jogee2005), transporting metal-poor gas from the outer disk towards the galactic center. However, observations have presented conflicting evidence regarding whether or not barred spiral galaxies systematically exhibit flatter metallicity gradients (cite: Vila-Costas1992; Martin1994; Zaritsky1994; Dutil1999; Henry1999; Sanchez2014; Kaplan2016; Balser2011).

While an investigation of the connection between the metallicity gradients reported for this sample of eight galaxies and their morphological structure is beyond the scope of this work, flattened gradients are quite pronounced for three galaxies in our sample (NGC 1672, NGC 3627 and NGC 4535), particularly within the inner 0.1-0.3 R$_{25}$ (Figure [2](#fig:gradients)). All three of these show very strong stellar bars, which dominate the morphology over this inner radial range. NGC 3627 is also strongly interacting, and NGC 4535 is a member of the Virgo Cluster. Three other galaxies in our sample are also classified as barred (NGC 1087, NGC 2835 and IC 5332; Table [1](#tab:sample)), exhibiting weaker stellar bars, and show no obvious flattening of their metallicity gradients. We draw no conclusions in this work, but find the connection between bar strength and flattened radial gradients intriguing.

## Physical interpretation of line ratios

We interpret the trends observed as changes in metallicity, however in a practical sense what we are tracing is changes in the line ratios integrated across HII regions. The physical interpretations of these line ratio diagnostics are not straightforward, with many showing degeneracies between changes in metallicity and ionization parameter, and are expected to then correlate with variations in star/cluster age, ISM density and ISM pressure. Figure [9](#fig:q_z_photionmodel) explores how (cite: Levesque2010) photoionization models at fixed electron density ($n=100$ cm$^{-3}$) and ionization parameter ($q=2\times$10$^7$) do produce variations in \[SIII\]/\[SII\] as a function of both metallicity and stellar population age. Here we have taken the output line ratios from the “high” mass-loss tracks at three fixed metallicities (0.4, 1, and 2Z$_\odot$). Assuming an instantaneous burst of star formation, this age dependency can result in significant (factor of 3-5) changes in the predicted \[SIII\]/\[SII\] line ratio. Taking models with a continuous star formation history results in almost no change in \[SIII\]/\[SII\] with age.

More detailed photoionization and stellar population modeling, along with follow-up UV observations to constrain the stellar population age, are necessary to disentangle these effects. (cite: Shabani2018) found no dependence of star cluster age with distance to the spiral arm in two of the three nearby galaxies in their case study, including NGC 628, though their youngest age bin encompasses entirely this crucial 1-10 Myr regime. We note that the strong correlation between $\Delta$O/H  and \[SIII\]/\[SII\] persists even if we attempt to clean our sample of some of these population extremes. Omitting regions with young ages (high H$\alpha$-to-FUV), high electron density (low \[SII\]6716/\[SII\]6731), high dust column (high E(B-V)) or close to the galaxy center does not fundamentally change the observed trend. More work is needed to explore fully the interconnection of these parameters and the impact each could have on the metallicity prescriptions.

An important final caveat to our discussion is that the trends we report are heavily dependent on the choice of metallicity prescription used. Appendix [9](#appendix:prescriptions) explores this in more detail, but we emphasize here that our results are robustly reproduced if we instead use the (cite: Dopita2016) photo ionization model-based N2S2 prescription. Given that this second prescription takes a very different approach compared to the empirical (cite: Pilyugin2016) prescription employed in this work, and should exhibit different biases, this builds further confidence in our results.

# Conclusion

In the first results from the PHANGS-MUSE survey at $\sim$50 pc resolution we are able to cleanly separate individual HII regions within our optical IFU data cubes and measure line fluxes from a spectrum integrated over individual HII regions. By applying the (cite: Pilyugin2016) strong line prescription, we measure gas phase oxygen abundances for 7,138 HII regions across the disks of eight nearby galaxies. All galaxies are well fit by a simple linear metallicity gradient with small (0.03-0.05 dex) scatter.

Subtracting that radial trend, we compare physical parameters for those HII regions that have enhanced and reduced abundances. Regions with enhanced abundances have high ionization parameter, higher H$\alpha$ luminosity, younger star clusters and associated molecular gas clouds show high CO line intesnity. This indicates recent star formation, possibly the same that powers the HII regions, has locally enriched the material. Regions with reduced abundances show increased H$\alpha$ velocity dispersions, suggestive of mixing introducing more pristine material. We also identify a positive correlation between gas phase metallicity and ionization parameter, in conflict with theoretical predictions. Taken together, the trends we identify suggest the local physical conditions are tightly linked to the localized enrichment of the ISM.

We observe subtle evidence for systematic azimuthal variations in half of the sample, though often in only one half of the galaxy, and we cannot cleanly associate this with the spiral pattern in all cases. However, in NGC 1672 and NGC 1087 the strong correlations with spiral structure indicate that the spiral arms can play an important role in organizing and mixing the ISM. This presents a complicated picture of the interplay between galaxy dynamics and enrichment patterns, which we aim to more fully address in the future with the full PHANGS-MUSE sample.

# Acknowledgments

We thank the referee for helpful comments that improved this work.

K.K. gratefully acknowledges funding from the German Research Foundation (DFG) in the form of an Emmy Noether Research Group (grant number KR4598/2-1, PI Kreckel). B.G. gratefully acknowledges the support of the Australian Research Council as the recipient of a Future Fellowship (FT140101202). FS, ES, CF, PL, RMcE, and TS acknowledges funding from the European Research Council (ERC) under the European UnionÕs Horizon 2020 research and innovation programme (grant agreement No. 694343). M.C. and J.M.D.K. gratefully acknowledge funding from the Deutsche Forschungsgemeinschaft (DFG) through an Emmy Noether Research Group (grant number KR4801/1-1) and the DFG Sachbeihilfe (grant number KR4801/2-1). J.M.D.K. gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). E.R. acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference number RGPIN-2017-03987. S.C.O.G. acknowledges support from the DFG via SFB 881 “The Milky Way System” (sub-projects B1, B2 and B8) and also via Germany’s Excellence Strategy EXC-2181/1 - 390900948 (the Heidelberg STRUCTURES Excellence Cluster).J.P. and A.H. acknowledge funding from the Programme National “Physique et Chimie du Milieu Interstellaire” (PCMI) of CNRS/INSU with INC/INP, co-funded by CEA and CNES. FB acknowledge funding from the European Union’s Horizon 2020 research and innovation programme (grant agreement No 726384).

Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme IDs 094.C-0623(A), 098.C-0484(A), 1100.B-0651(A) and 1100.B-0651(B).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00650.S, ADS/JAO.ALMA#2015.1.00925.S, ADS/JAO.ALMA#2015.1.00956.S, ADS/JAO.ALMA#2017.1.00392.S,

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

Based on observations made with the NASA Galaxy Evolution Explorer. GALEX is operated for NASA by the California Institute of Technology under NASA contract NAS5-98034.

Data analysis made use of Topcat (cite: Taylor2005). This research has made use of NASA’s Astrophysics Data System. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration.

(ref: Arellano-Cordova2016) Arellano-Córdova, K. Z., Rodrı́guez, M., Mayya, Y. D., & Rosa-González, D. 2016, [MNRAS, 455, 2627](http://dx.doi.org/10.1093/mnras/stv2461)

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, [ARA&A, 47, 481](http://dx.doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: Azimlu+2011) Azimlu, M., Marciniak, R., & Barmby, P. 2011, [AJ, 142, 139](http://dx.doi.org/10.1088/0004-6256/142/4/139)

(ref: Bacon2010) Bacon, R., et al. 2010, [in Proc. SPIE, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III](http://dx.doi.org/10.1117/12.856027), 773508

(ref: Baldwin1981) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, [PASP, 93, 5](http://dx.doi.org/10.1086/130766)

(ref: Balser2011) Balser, D. S., Rood, R. T., Bania, T. M., & Anderson, L. D. 2011, [ApJ, 738, 27](http://dx.doi.org/10.1088/0004-637X/738/1/27)

(ref: Balser2015) Balser, D. S., Wenger, T. V., Anderson, L. D., & Bania, T. M. 2015, [ApJ, 806, 199](http://dx.doi.org/10.1088/0004-637X/806/2/199)

(ref: Belfiore2017) Belfiore, F., Maiolino, R., Tremonti, C., et al. 2017, [MNRAS, 469, 151](http://dx.doi.org/10.1093/mnras/stx789)

(ref: Berg2015) Berg, D. A., Skillman, E. D., Croxall, K. V., et al. 2015, [ApJ, 806, 16](http://dx.doi.org/10.1088/0004-637X/806/1/16)

(ref: Blanc2015) Blanc, G. A., Kewley, L., Vogt, F. P. A., & Dopita, M. A. 2015, [ApJ, 798, 99](http://dx.doi.org/10.1088/0004-637X/798/2/99)

(ref: Blanc2019) Blanc, G. A., Lu, Y., Benson, A., Katsianis, A., & Barraza, M. 2019, [ApJ, 877, 6](http://dx.doi.org/10.3847/1538-4357/ab16ec)

(ref: Boissier1999) Boissier, S., & Prantzos, N. 1999, [MNRAS, 307, 857](http://dx.doi.org/10.1046/j.1365-8711.1999.02699.x)

(ref: Bradley2006) Bradley, T. R., Knapen, J. H., Beckman, J. E., & Folkes, S. L. 2006, [A&A, 459, L13](http://dx.doi.org/10.1051/0004-6361:20066151)

(ref: Bresolin2007) Bresolin, F. 2007, [ApJ, 656, 186](http://dx.doi.org/10.1086/510380)

(ref: Bresolin1999) Bresolin, F., Kennicutt, Robert C., J., & Garnett, D. R. 1999, [ApJ, 510, 104](http://dx.doi.org/10.1086/306576)

(ref: Bruzual2003) Bruzual, G., & Charlot, S. 2003, [MNRAS, 344, 1000](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Bryant2015) Bryant, J. J., Owers, M. S., Robotham, A. S. G., et al. 2015, [MNRAS, 447, 2857](http://dx.doi.org/10.1093/mnras/stu2635)

(ref: Bundy2015) Bundy, K., Bershady, M. A., Law, D. R., et al. 2015, [ApJ, 798, 7](http://dx.doi.org/10.1088/0004-637X/798/1/7)

(ref: Cappellari2017) Cappellari, M. 2017, [MNRAS, 466, 798](http://dx.doi.org/10.1093/mnras/stw3020)

(ref: Cappellari2004) Cappellari, M., & Emsellem, E. 2004, [PASP, 116, 138](http://dx.doi.org/10.1086/381875)

(ref: Cardelli1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, [ApJ, 345, 245](http://dx.doi.org/10.1086/167900)

(ref: Chevance2019) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2019, MNRAS submitted

(ref: Cook2014) Cook, D. O., Dale, D. A., Johnson, B. D., et al. 2014, [MNRAS, 445, 881](http://dx.doi.org/10.1093/mnras/stu1580)

(ref: Croxall2015) Croxall, K. V., Pogge, R. W., Berg, D. A., Skillman, E. D., & Moustakas, J. 2015, [ApJ, 808, 42](http://dx.doi.org/10.1088/0004-637X/808/1/42)

(ref: Croxall2016) —. 2016, [ApJ, 830, 4](http://dx.doi.org/10.3847/0004-637X/830/1/4)

(ref: deAvillez2002) de Avillez, M. A., & Mac Low, M.-M. 2002, [ApJ, 581, 1047](http://dx.doi.org/10.1086/344256)

(ref: DiMatteo2013) Di Matteo, P., Haywood, M., Combes, F., Semelin, B., & Snaith, O. N. 2013, [A&A, 553, A102](http://dx.doi.org/10.1051/0004-6361/201220539)

(ref: Dopita2016) Dopita, M. A., Kewley, L. J., Sutherland, R. S., & Nicholls, D. C. 2016, [Ap&SS, 361, 61](http://dx.doi.org/10.1007/s10509-016-2657-8)

(ref: Dopita2014) Dopita, M. A., Rich, J., Vogt, F. P. A., et al. 2014, [Ap&SS, 350, 741](http://dx.doi.org/10.1007/s10509-013-1753-2)

(ref: Dors2011) Dors, Jr., O. L., Krabbe, A., Hägele, G. F., & Pérez-Montero, E. 2011, [MNRAS, 415, 3616](http://dx.doi.org/10.1111/j.1365-2966.2011.18978.x)

(ref: Dutil1999) Dutil, Y., & Roy, J.-R. 1999, [ApJ, 516, 62](http://dx.doi.org/10.1086/307100)

(ref: Erroz-Ferrer2019) Erroz-Ferrer, S., Carollo, C. M., den Brok, M., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz194), [arXiv:1901.04493](http://arxiv.org/abs/1901.04493)

(ref: Esteban2018) Esteban, C., & Garcı́a-Rojas, J. 2018, [MNRAS, 478, 2315](http://dx.doi.org/10.1093/mnras/sty1168)

(ref: Ferguson1996) Ferguson, A. M. N., Wyse, R. F. G., Gallagher, III, J. S., & Hunter, D. A. 1996, [AJ, 111, 2265](http://dx.doi.org/10.1086/117961)

(ref: Fitzpatrick1999) Fitzpatrick, E. L. 1999, [PASP, 111, 63](http://dx.doi.org/10.1086/316293)

(ref: GAIA_DR2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, [A&A, 616, A1](http://dx.doi.org/10.1051/0004-6361/201833051)

(ref: Garnett2002) Garnett, D. R. 2002, [ApJ, 581, 1019](http://dx.doi.org/10.1086/344301)

(ref: Garnett1997) Garnett, D. R., Shields, G. A., Skillman, E. D., Sagan, S. P., & Dufour, R. J. 1997, [ApJ, 489, 63](http://dx.doi.org/10.1086/304775)

(ref: GildePaz2007) Gil de Paz, A., Boissier, S., Madore, B. F., et al. 2007, [ApJS, 173, 185](http://dx.doi.org/10.1086/516636)

(ref: Grand2016) Grand, R. J. J., Springel, V., Kawata, D., et al. 2016, [MNRAS, 460, L94](http://dx.doi.org/10.1093/mnrasl/slw086)

(ref: Haffner2009) Haffner, L. M., Dettmar, R.-J., Beckman, J. E., et al. 2009, [Reviews of Modern Physics, 81, 969](http://dx.doi.org/10.1103/RevModPhys.81.969)

(ref: Henry1999) Henry, R. B. C., & Worthey, G. 1999, [PASP, 111, 919](http://dx.doi.org/10.1086/316403)

(ref: Ho+2019) Ho, I.-T. 2019, [MNRAS, 485, 3569](http://dx.doi.org/10.1093/mnras/stz649)

(ref: Ho2016) Ho, I.-T., Medling, A. M., Groves, B., et al. 2016, [Ap&SS, 361, 280](http://dx.doi.org/10.1007/s10509-016-2865-2)

(ref: Ho2017) Ho, I. T., Seibert, M., Meidt, S. E., et al. 2017, [ApJ, 846, 39](http://dx.doi.org/10.3847/1538-4357/aa8460)

(ref: Ho2018) Ho, I. T., Meidt, S. E., Kudritzki, R.-P., et al. 2018, [A&A, 618, A64](http://dx.doi.org/10.1051/0004-6361/201833262)

(ref: Hygate2019) Hygate, A. P. S., Kruijssen, J. M. D., Chevance, M., et al. 2019, MNRAS, 488, 2800

(ref: Jogee2005) Jogee, S., Scoville, N., & Kenney, J. D. P. 2005, [ApJ, 630, 837](http://dx.doi.org/10.1086/432106)

(ref: Kaplan2016) Kaplan, K. F., Jogee, S., Kewley, L., et al. 2016, [MNRAS, 462, 1642](http://dx.doi.org/10.1093/mnras/stw1422)

(ref: Kauffmann2003) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, [MNRAS, 346, 1055](http://dx.doi.org/10.1111/j.1365-2966.2003.07154.x)

(ref: Kennicutt1998) Kennicutt, Jr., R. C. 1998, [ARA&A, 36, 189](http://dx.doi.org/10.1146/annurev.astro.36.1.189)

(ref: Kennicutt1996) Kennicutt, Jr., R. C., & Garnett, D. R. 1996, [ApJ, 456, 504](http://dx.doi.org/10.1086/176675)

(ref: Kewley2002) Kewley, L. J., & Dopita, M. A. 2002, [ApJS, 142, 35](http://dx.doi.org/10.1086/341326)

(ref: Kewley2008) Kewley, L. J., & Ellison, S. L. 2008, [ApJ, 681, 1183](http://dx.doi.org/10.1086/587500)

(ref: Kewley2001) Kewley, L. J., Heisler, C. A., Dopita, M. A., & Lumsden, S. 2001, [ApJS, 132, 37](http://dx.doi.org/10.1086/318944)

(ref: Kormendy2004) Kormendy, J., & Kennicutt, Robert C., J. 2004, [ARA&A, 42, 603](http://dx.doi.org/10.1146/annurev.astro.42.053102.134024)

(ref: Kreckel2016) Kreckel, K., Blanc, G. A., Schinnerer, E., et al. 2016, [ApJ, 827, 103](http://dx.doi.org/10.3847/0004-637X/827/2/103)

(ref: Kreckel2017) Kreckel, K., Groves, B., Bigiel, F., et al. 2017, [ApJ, 834, 174](http://dx.doi.org/10.3847/1538-4357/834/2/174)

(ref: Kreckel2013) Kreckel, K., Groves, B., Schinnerer, E., et al. 2013, [ApJ, 771, 62](http://dx.doi.org/10.1088/0004-637X/771/1/62)

(ref: Kreckel2018) Kreckel, K., Faesi, C., Kruijssen, J. M. D., et al. 2018, [ApJL, 863, L21](http://dx.doi.org/10.3847/2041-8213/aad77d)

(ref: kruijssen18) Kruijssen, J. M. D., Schruba, A., Hygate, A. P. S., et al. 2018, MNRAS, 479, 1866

(ref: Kruijssen2019) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, [Nature, 569, 519](http://dx.doi.org/10.1038/s41586-019-1194-3)

(ref: Krumholz2018) Krumholz, M. R., & Ting, Y.-S. 2018, [MNRAS, 475, 2236](http://dx.doi.org/10.1093/mnras/stx3286)

(ref: Kudritzki2015) Kudritzki, R.-P., Ho, I. T., Schruba, A., et al. 2015, [MNRAS, 450, 342](http://dx.doi.org/10.1093/mnras/stv522)

(ref: Larsen1999) Larsen, S. S., & Richtler, T. 1999, A&A, 345, 59

(ref: Leitherer2014) Leitherer, C., Ekström, S., Meynet, G., et al. 2014, [ApJS, 212, 14](http://dx.doi.org/10.1088/0067-0049/212/1/14)

(ref: Levesque2010) Levesque, E. M., Kewley, L. J., & Larson, K. L. 2010, [AJ, 139, 712](http://dx.doi.org/10.1088/0004-6256/139/2/712)

(ref: Marino2013) Marino, R. A., Rosales-Ortega, F. F., Sánchez, S. F., et al. 2013, [A&A, 559, A114](http://dx.doi.org/10.1051/0004-6361/201321956)

(ref: Martin1994) Martin, P., & Roy, J.-R. 1994, [ApJ, 424, 599](http://dx.doi.org/10.1086/173917)

(ref: Massey2005) Massey, P., Puls, J., Pauldrach, A. W. A., et al. 2005, [ApJ, 627, 477](http://dx.doi.org/10.1086/430417)

(ref: McLeod2019) McLeod, A. F., Dale, J. E., Evans, C. J., et al. 2019, [MNRAS, 486, 5263](http://dx.doi.org/10.1093/mnras/sty2696)

(ref: Nagao2006) Nagao, T., Maiolino, R., & Marconi, A. 2006, [A&A, 459, 85](http://dx.doi.org/10.1051/0004-6361:20065216)

(ref: Oey2007) Oey, M. S., Meurer, G. R., Yelda, S., et al. 2007, [ApJ, 661, 801](http://dx.doi.org/10.1086/517867)

(ref: Pellegrini2011) Pellegrini, E. W., Baldwin, J. A., & Ferland, G. J. 2011, [ApJ, 738, 34](http://dx.doi.org/10.1088/0004-637X/738/1/34)

(ref: Pellegrini2012) Pellegrini, E. W., Oey, M. S., Winkler, P. F., et al. 2012, [ApJ, 755, 40](http://dx.doi.org/10.1088/0004-637X/755/1/40)

(ref: Petit2015) Petit, A. C., Krumholz, M. R., Goldbaum, N. J., & Forbes, J. C. 2015, [MNRAS, 449, 2588](http://dx.doi.org/10.1093/mnras/stv493)

(ref: Pilyugin2016) Pilyugin, L. S., & Grebel, E. K. 2016, [MNRAS, 457, 3678](http://dx.doi.org/10.1093/mnras/stw238)

(ref: Pilyugin2014) Pilyugin, L. S., Grebel, E. K., & Kniazev, A. Y. 2014, [AJ, 147, 131](http://dx.doi.org/10.1088/0004-6256/147/6/131)

(ref: Poetrodjojo2019) Poetrodjojo, H., D’Agostino, J. J., Groves, B., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz1241), [arXiv:1905.03251](http://arxiv.org/abs/1905.03251)

(ref: Poetrodjojo2018) Poetrodjojo, H., Groves, B., Kewley, L. J., et al. 2018, [MNRAS, 479, 5235](http://dx.doi.org/10.1093/mnras/sty1782)

(ref: Rahner2018) Rahner, D., Pellegrini, E. W., Glover, S. C. O., & Klessen, R. S. 2018, [MNRAS, 473, L11](http://dx.doi.org/10.1093/mnrasl/slx149)

(ref: Ramachandran2018) Ramachandran, V., Hamann, W. R., Hainich, R., et al. 2018, [A&A, 615, A40](http://dx.doi.org/10.1051/0004-6361/201832816)

(ref: Rosolowsky2008) Rosolowsky, E., & Simon, J. D. 2008, [ApJ, 675, 1213](http://dx.doi.org/10.1086/527407)

(ref: Roy1995) Roy, J. R., & Kunth, D. 1995, A&A, 294, 432

(ref: Sanchez2012) Sánchez, S. F., et al. 2012, [A&A, 538, A8](http://dx.doi.org/10.1051/0004-6361/201117353)

(ref: Sanchez2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, [A&A, 563, A49](http://dx.doi.org/10.1051/0004-6361/201322343)

(ref: Sanchez-Gil2011) Sánchez-Gil, M. C., Jones, D. H., Pérez, E., et al. 2011, [MNRAS, 415, 753](http://dx.doi.org/10.1111/j.1365-2966.2011.18759.x)

(ref: Sanchez-Menguiano2019) Sánchez-Menguiano, L., Sánchez Almeida, J., Muñoz-Tuñón, C., et al. 2019, arXiv e-prints, arXiv:1904.03930

(ref: Sanchez-Menguiano2016) Sánchez-Menguiano, L., Sánchez, S. F., Kawata, D., et al. 2016, [ApJL, 830, L40](http://dx.doi.org/10.3847/2041-8205/830/2/L40)

(ref: Sarzi2006) Sarzi, M., Falcón-Barroso, J., Davies, R. L., et al. 2006, [MNRAS, 366, 1151](http://dx.doi.org/10.1111/j.1365-2966.2005.09839.x)

(ref: Schaerer1997) Schaerer, D., & de Koter, A. 1997, A&A, 322, 598

(ref: Schinnerer2017) Schinnerer, E., Meidt, S. E., Colombo, D., et al. 2017, [ApJ, 836, 62](http://dx.doi.org/10.3847/1538-4357/836/1/62)

(ref: Shabani2018) Shabani, F., Grebel, E. K., Pasquali, A., et al. 2018, [MNRAS, 478, 3590](http://dx.doi.org/10.1093/mnras/sty1277)

(ref: Skillman1989) Skillman, E. D. 1989, [ApJ, 347, 883](http://dx.doi.org/10.1086/168179)

(ref: Spitoni2019) Spitoni, E., Cescutti, G., Minchev, I., et al. 2019, [A&A, 628, A38](http://dx.doi.org/10.1051/0004-6361/201834665)

(ref: Stasinska2007) Stasińska, G., Tenorio-Tagle, G., Rodrı́guez, M., & Henney, W. J. 2007, [A&A, 471, 193](http://dx.doi.org/10.1051/0004-6361:20065675)

(ref: Sun2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, [ApJ, 860, 172](http://dx.doi.org/10.3847/1538-4357/aac326)

(ref: Taylor2005) Taylor, M. B. 2005, in Astronomical Society of the Pacific Conference Series, Vol. 347, Astronomical Data Analysis Software and Systems XIV, ed. P. Shopbell, M. Britton, & R. Ebert, 29

(ref: Thilker2000) Thilker, D. A., Braun, R., & Walterbos, R. A. M. 2000, [AJ, 120, 3070](http://dx.doi.org/10.1086/316852)

(ref: Thilker2002) Thilker, D. A., Walterbos, R. A. M., Braun, R., & Hoopes, C. G. 2002, [AJ, 124, 3118](http://dx.doi.org/10.1086/344303)

(ref: Tremonti2004) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, [ApJ, 613, 898](http://dx.doi.org/10.1086/423264)

(ref: Utomo2018) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, [ApJL, 861, L18](http://dx.doi.org/10.3847/2041-8213/aacf8f)

(ref: Vazdekis2012) Vazdekis, A., Ricciardelli, E., Cenarro, A. J., et al. 2012, [MNRAS, 424, 157](http://dx.doi.org/10.1111/j.1365-2966.2012.21179.x)

(ref: Vila-Costas1992) Vila-Costas, M. B., & Edmunds, M. G. 1992, [MNRAS, 259, 121](http://dx.doi.org/10.1093/mnras/259.1.121)

(ref: Vilchez1996) Vilchez, J. M., & Esteban, C. 1996, [MNRAS, 280, 720](http://dx.doi.org/10.1093/mnras/280.3.720)

(ref: Vincenzo2016) Vincenzo, F., Matteucci, F., Belfiore, F., & Maiolino, R. 2016, [MNRAS, 455, 4183](http://dx.doi.org/10.1093/mnras/stv2598)

(ref: Vogt2017) Vogt, F. P. A., Pérez, E., Dopita, M. A., Verdes-Montenegro, L., & Borthakur, S. 2017, [A&A, 601, A61](http://dx.doi.org/10.1051/0004-6361/201629853)

(ref: Yang2012) Yang, C.-C., & Krumholz, M. 2012, [ApJ, 758, 48](http://dx.doi.org/10.1088/0004-637X/758/1/48)

(ref: Zaritsky1994) Zaritsky, D., Kennicutt, Jr., R. C., & Huchra, J. P. 1994, [ApJ, 420, 87](http://dx.doi.org/10.1086/173544)

(ref: Zurita2000) Zurita, A., Rozas, M., & Beckman, J. E. 2000, A&A, 363, 9

![image](f1a.pdf) ![image](f1b.pdf)

![](f2.png)

![](f3.png)

![](f4.pdf)

![](f5.pdf)

![image](f6a.png) ![image](f6b.png) ![image](f6c.png) ![image](f6d.png) ![image](f6e.png) ![image](f6f.png)

![](f7.pdf)

![image](f8a.pdf) ![image](f8b.pdf)

![image](f9a.pdf) ![image](f9b.pdf)

# Image Atlas

We present an atlas of images for each of the eight galaxies in our initial PHANGS-MUSE sample. All presented images are constructed from our MUSE data cubes, including the gri-band three color images. For all galaxies, corresponding images are at matched image stretch and scaling. Each figure shows the gri-band three color image (bottom left), overlaid emission line maps (red: H$\alpha$, green: \[OIII\], blue: \[SII\]; bottom right), H$\alpha$ emission (top left) and HII regions with their measured metallicities (top right).

![](ngc628_v5.jpg)

![](ngc1087_v5.jpg)

![](ngc1672_v5.jpg)

![](ngc2835_v5.jpg)

![](ngc3627_v5.jpg)

![](ngc4254_v5.jpg)

![](ngc4535_v5.jpg)

![](ic5332_v5.jpg)

# Excitation Diagnostic Diagrams

We show BPT (cite: Baldwin1981) diagnostic diagrams for all eight galaxies. In defining our HII region catalog (Section [2.2](#sec:hiireg)), we employ two BPT emission line ratio diagnostics to ensure the excitation is consistent with photoionization by massive stars. In the \[OIII\]/H$\beta$ vs. \[NII\]/H$\alpha$ diagnostic (Figure [18](#fig:bpt1)), we require regions to be consistent with the stringent empirical (cite: Kauffmann2003) line. In the \[OIII\]/H$\beta$ vs \[SII\]/H$\alpha$ diagnostic (Figure [19](#fig:bpt2)), we require regions to be consistent with the (cite: Kewley2001) line.

Each diagram shows all regions morphologically identified by HIIphot, and in grey we indicate HII regions which are excluded due to one of our rejection criteria listed in Section [2.2](#sec:hiireg).

![](f18.png)

![](f19.png)

# Metallicity Prescriptions

Strong line metallicity prescriptions produce well established differences in inferred metallicity and radial gradients in galaxies (cite: Kewley2008; Poetrodjojo2019). In Figure [20](#fig:gradients_appendix) we present best-fitting radial metallicity gradients using four different prescriptions. This includes the Scal (solid lines; (cite: Pilyugin2016)) prescription, which we have adopted in this work, as well as the (cite: Dopita2016) N2S2 (D16; dashed lines) photoionization model based prescription, which gives qualitatively similar results. For completeness and to facilitate consistent comparisons with the exisiting literature, we also include the commonly used empirical (cite: Marino2013) O3N2 (dotted lines) and N2 (dash-dot lines) prescriptions. As in Section [3.2](#sec:radgrad), each radial gradient is fit using all HII regions with radius above $0.1 {\rm R}_{25}$.

Finally, for further comparison with the results of photoionization models, we overplot each linear radial gradient on outputs from the Bayesian inference code IZI (cite: Blanc2015). This code uses a set of observed line fluxes combined with an input photoionization model to derive the joint and marginalized posterior probability density functions for metallicity and ionization parameter. Here, we have compared all our observed strong emission lines (\[OIII\], H$\beta$, \[NII\], H$\alpha$, \[SII\], \[SIII\]) with the (cite: Levesque2010) “high” mass-loss tracks assuming a constant star formation history over the past 6 Myr and a Salpeter IMF with a 100 M$_\odot$ upper cutoff. We then radially bin and sum the marginalized PDFs to produce a probabilistic metallicity gradient for each galaxy. All gradients across all different methods show relatively good agreement in slope, and systematically $\sim$0.2 dex lower values in all empirical calibrations compared to the photoionization based methods.

In Table [3](#tab:gradients) we list the coefficients of all radial gradient fits for each galaxies, using each of the four different metallicity prescriptions. R$_0$ is the y-intercept, and the gradient is given both in units of R$_{25}$ and in units of kpc. We further list the scatter with respect to the linear fit ($\sigma$(O/H)). Here, $\sigma$(O/H) reflects the standard deviation with respect to the linear radial gradient fit, whereas $\Delta$O/H is the residual for a given point from the fit. This scatter is systematically lower ($\sim$0.04 dex) in all empirical calibrations (Scal, O3N2, N2) compared to the N2S2 (D16) photoionization model based calibration ($\sim$0.09 dex).

While the radial gradients appear quite consistent across calibrations, and the scatter $\sigma$(O/H) is also similar between empirical calibrations, the different calibrations show very different trends between $\Delta$O/H  and L(H$\alpha$) and \[SIII\]/\[SII\] (a proxy for the ionization parameter). In Figure [21](#fig:offsets_appendix) we show this trend using each of the four prescriptions for each galaxy individually and for the entire sample. Both the Scal and N2S2 (D16) calibrations exhibit a positive correlation with both L(H$\alpha$) and \[SIII\]/\[SII\] that is discussed in this paper. On the other hand, O3N2 and N2 show a quite flat trend. However, because these are both using smaller dimensionallity in the line ratios, we believe both of these presciptions retain some of the degeneracy between metallicity and ionization parameter, enough to cloud the subtle trends presented here.

A final demonstration of the strong discrepancies between calibrations is shown in Figure [22](#fig:scatter). Here, we calculate $\Delta$O/H  for the same HII regions using different prescriptions, and compare the 1$\sigma$ outliers. Between the Scal and N2S2 (D16) calibrations we find a clear correlation, with 50-60% of outliers overlapping between the two calibrations. N2 (M13) shows poor agreement with Scal, with only $\sim$20% of the outliers agreeing between the samples. O3N2 shows no correlation with Scal, having $<$10% of the outliers overlapping. While both O3N2 and N2 quantitatively reproduce the radial metallicity gradient slope, they appear to be insensitive to much of the small scale physics related to small metallicity variations recovered by both the Scal and N2S2 (D16).

![](f20.pdf)

+----------+--------------------------------------------------------------+--------------------------------------------------------------+--------------------------------------------------------------+--------------------------------------------------------------+
|          | Scal                                                         | N2S2 (D16)                                                   | O3N2 (M13)                                                   | N2 (PP04)                                                    |
+:=========+:===========:+:===============:+:============:+:=============:+:===========:+:===============:+:============:+:=============:+:===========:+:===============:+:============:+:=============:+:===========:+:===============:+:============:+:=============:+
| 2-5 Name | R$_0$       | Gradient        | Gradient     | $\sigma$(O/H) | R$_0$       | Gradient        | Gradient     | $\sigma$(O/H) | R$_0$       | Gradient        | Gradient     | $\sigma$(O/H) | R$_0$       | Gradient        | Gradient     | $\sigma$(O/H) |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          |             | \[dex           | \[dex        | \[dex\]       |             | \[dex           | \[dex        | \[dex\]       |             | \[dex           | \[dex        | \[dex\]       |             | \[dex           | \[dex        | \[dex\]       |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          |             | R$_{25}^{-1}$\] | kpc$^{-1}$\] |               |             | R$_{25}^{-1}$\] | kpc$^{-1}$\] |               |             | R$_{25}^{-1}$\] | kpc$^{-1}$\] |               |             | R$_{25}^{-1}$\] | kpc$^{-1}$\] |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc628   | 8.556       | -0.191          | -0.0412      | 0.05          | 8.771       | -0.456          | -0.0913      | 0.11          | 8.611       | -0.164          | -0.0329      | 0.05          | 8.508       | -0.009          | -0.0018      | 0.04          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.005 | $\pm$ 0.018     | $\pm$ 0.0037 |               | $\pm$ 0.011 | $\pm$ 0.041     | $\pm$ 0.0082 |               | $\pm$ 0.005 | $\pm$ 0.017     | $\pm$ 0.0035 |               | $\pm$ 0.003 | $\pm$ 0.012     | $\pm$ 0.0025 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc1087  | 8.483       | -0.144          | -0.0994      | 0.03          | 8.580       | -0.251          | -0.1676      | 0.08          | 8.542       | -0.118          | -0.0784      | 0.04          | 8.526       | -0.102          | -0.0678      | 0.02          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.003 | $\pm$ 0.006     | $\pm$ 0.0048 |               | $\pm$ 0.009 | $\pm$ 0.017     | $\pm$ 0.0114 |               | $\pm$ 0.005 | $\pm$ 0.009     | $\pm$ 0.0061 |               | $\pm$ 0.003 | $\pm$ 0.005     | $\pm$ 0.0035 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc1672  | 8.563       | -0.056          | -0.0199      | 0.03          | 8.737       | -0.089          | -0.0287      | 0.10          | 8.571       | -0.074          | -0.0238      | 0.04          | 8.567       | -0.052          | -0.0169      | 0.03          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.003 | $\pm$ 0.007     | $\pm$ 0.0022 |               | $\pm$ 0.009 | $\pm$ 0.019     | $\pm$ 0.0062 |               | $\pm$ 0.004 | $\pm$ 0.009     | $\pm$ 0.0030 |               | $\pm$ 0.002 | $\pm$ 0.005     | $\pm$ 0.0017 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc2835  | 8.565       | -0.516          | -0.1586      | 0.04          | 8.734       | -0.907          | -0.2834      | 0.09          | 8.598       | -0.401          | -0.1253      | 0.06          | 8.567       | -0.319          | -0.0997      | 0.03          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.004 | $\pm$ 0.012     | $\pm$ 0.0038 |               | $\pm$ 0.010 | $\pm$ 0.027     | $\pm$ 0.0085 |               | $\pm$ 0.006 | $\pm$ 0.018     | $\pm$ 0.0056 |               | $\pm$ 0.003 | $\pm$ 0.009     | $\pm$ 0.0028 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc3627  | 8.528       | 0.056           | 0.0095       | 0.03          | 8.733       | 0.084           | 0.0164       | 0.07          | 8.571       | 0.108           | 0.0212       | 0.04          | 8.506       | 0.041           | 0.0080       | 0.03          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.004 | $\pm$ 0.016     | $\pm$ 0.0031 |               | $\pm$ 0.009 | $\pm$ 0.034     | $\pm$ 0.0066 |               | $\pm$ 0.005 | $\pm$ 0.019     | $\pm$ 0.0037 |               | $\pm$ 0.004 | $\pm$ 0.015     | $\pm$ 0.0029 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc4254  | 8.592       | -0.104          | -0.0425      | 0.03          | 8.873       | -0.241          | -0.0966      | 0.08          | 8.632       | -0.142          | -0.0568      | 0.04          | 8.513       | 0.000           | 0.0001       | 0.04          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.002 | $\pm$ 0.004     | $\pm$ 0.0019 |               | $\pm$ 0.004 | $\pm$ 0.011     | $\pm$ 0.0045 |               | $\pm$ 0.002 | $\pm$ 0.006     | $\pm$ 0.0022 |               | $\pm$ 0.002 | $\pm$ 0.005     | $\pm$ 0.0020 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ngc4535  | 8.579       | -0.091          | -0.0244      | 0.04          | 8.844       | -0.258          | -0.0628      | 0.09          | 8.626       | -0.082          | -0.0200      | 0.05          | 8.471       | 0.129           | 0.0314       | 0.04          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.006 | $\pm$ 0.018     | $\pm$ 0.0045 |               | $\pm$ 0.012 | $\pm$ 0.041     | $\pm$ 0.0100 |               | $\pm$ 0.006 | $\pm$ 0.021     | $\pm$ 0.0051 |               | $\pm$ 0.005 | $\pm$ 0.018     | $\pm$ 0.0043 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
| ic5332   | 8.514       | -0.401          | -0.1362      | 0.05          | 8.671       | -0.717          | -0.2391      | 0.11          | 8.574       | -0.251          | -0.0836      | 0.07          | 8.520       | -0.224          | -0.0746      | 0.03          |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+
|          | $\pm$ 0.010 | $\pm$ 0.035     | $\pm$ 0.0119 |               | $\pm$ 0.022 | $\pm$ 0.076     | $\pm$ 0.0255 |               | $\pm$ 0.014 | $\pm$ 0.049     | $\pm$ 0.0163 |               | $\pm$ 0.006 | $\pm$ 0.020     | $\pm$ 0.0065 |               |
+----------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+-------------+-----------------+--------------+---------------+

: Radial gradient fits (in appendix)

![image](f21a.pdf) ![image](f21b.pdf)

![](f22.pdf)

# Azimuthal Variations Atlas

For each galaxy, we present two visualizations of the complete spatial distribution of $\Delta$O/H. Removing any size or luminosity information, we take the position of each HII region and place it onto a polar projection, with the azimuthal angle on the x-axis and the natural log of the radius on the y-axis (upper-left panels).

Here we color code each region by $\Delta$O/H. In polar plots, spiral arms with fixed pitch angle appear as straight lines. As an alternate visualization (upper-right panels), we also take the individual measurements of $\Delta$O/H for each HII region (circles) and interpolate them onto a two dimensional surface using kriging and an exponential model. We mark an approximate spiral arm location by tracing the brightest star-forming regions along the arm by eye (overlaid in grey), though we note here this is very approximate and not sufficient for detailed environmental comparisons.

We mark in each of these images a ring at fixed radius, matched between both images, and show below the polar plot how $\Delta$O/H  varies azimuthally. These rings are $0.1 {\rm R}_{25}$ wide, and selected to be completely contained within the mask but demonstrating the strongest trend for azimuthal variations. To guide the eye, we overplot the median $\Delta$O/H measured in 30$^\circ$ wide bins, and color the positive and negative residuals with respect to $\Delta$O/H=0 (top left, middle panel). We compare this with the total extinction-corrected luminosity around the same azimuthal ring in matched 30$^\circ$ wide bins (top left, bottom panel).

As a final visualization, we also map the locations of the HII regions that are 1$\sigma$ outliers towards both enhanced and reduced abundances (bottom panels). We show these populations in relation to the $\sim$500pc scale bulk CO emission, roughly tracing the underlying gravitation potential and the spiral pattern.

Discussion of the trends identified within each galaxy and across the galaxy sample is contained in Sections [4.3](#sec:aztrends) and [5.2](#sec:dis:azimuth).

![image](unwrap_scal_ngc628_v3.pdf) ![image](ngc628_v5_offset.pdf) ![image](ngc628_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc1087_v3.pdf) ![image](ngc1087_v5_offset.pdf) ![image](ngc1087_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc1672_v3.pdf) ![image](ngc1672_v5_offset.pdf) ![image](ngc1672_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc2835_v3.pdf) ![image](ngc2835_v5_offset.pdf) ![image](ngc2835_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc3627_v3.pdf) ![image](ngc3627_v5_offset.pdf) ![image](ngc3627_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc4254_v3.pdf) ![image](ngc4254_v5_offset.pdf) ![image](ngc4254_lowmidhi_fixed_co.png)

![image](unwrap_scal_ngc4535_v3.pdf) ![image](ngc4535_v5_offset.pdf) ![image](ngc4535_lowmidhi_fixed_co.png)

![image](unwrap_scal_ic5332_v3.pdf) ![image](ic5332_v5_offset.pdf) ![image](ic5332_lowmidhi_fixed_co.png)

[^1]: <http://www.phangs.org>

[^2]: <https://github.com/emsellem/pymusepipe>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Halpha maps from LZIFU, HIIphot masks, integrated spectra fit with GANDALF/pPXF, then quality/BPT cuts",
  "failed_quote": "Halpha emission line maps are analyzed with HIIphot (cite: Thilker2000), which has been designed to morphologically isolate HII regions from diffuse ionized gas"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "Identify HII regions",
  "failed_quote": "Halpha emission line maps are analyzed with HIIphot (cite: Thilker2000)"
 }
]
```
