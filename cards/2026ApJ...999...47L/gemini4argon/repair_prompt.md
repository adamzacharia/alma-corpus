# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ...999...47L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey: 5$\sigma$ Source Catalog and Redshift Distribution

## Abstract

One of the greatest challenges in galaxy evolution over the last decade has been constraining the prevalence of heavily dust-obscured galaxies in the early Universe. At $z>3$, these galaxies are increasingly rare, and difficult to identify as they are interspersed among the more numerous dust-obscured galaxy population at $z=1-3$, making efforts to secure confident spectroscopic redshifts expensive, and sometimes unsuccessful. In this work, we present the Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey – a 2 mm blank-field survey in the COSMOS-Web field, and the largest ever ALMA blank-field survey to-date covering 577 arcmin$^2$. Ex-MORA is an expansion of the MORA survey designed to identify primarily $z>3$ dusty, star-forming galaxies while simultaneously filtering out the more numerous $z<3$ population by leveraging the very negative $K$-correction at observed-frame 2 mm. We identify 37 significant ($>$ 5$\sigma$) sources, 33 of which are robust thermal dust emitters. We measure a median redshift of $\langle z \rangle = 3.6^{+0.1}_{-0.2}$, with two-thirds of the sample at $z>3$, and just under half at $z>4$, demonstrating the overall success of the 2 mm–selection technique. We find an integrated $z>3$ volume density of Ex-MORA sources of $\sim1-3\times10^{-5}$ Mpc$^{-3}$, consistent with other surveys of infrared luminous galaxies at similar epochs. We also find that techniques using rest-frame optical emission (or lack thereof) to identify $z>3$ heavily dust-obscured galaxies miss at least half of Ex-MORA galaxies. This supports the idea that the dusty galaxy population is heterogeneous, and that synergies across several major observatories spanning multiple energy regimes are critical to understanding their formation and evolution at $z>3$.

# Introduction

Dusty, star-forming galaxies (DSFGs) are a class of extraordinarily infrared luminous (L$_\mathrm{IR} > 10^{12}$ L$_\odot$) galaxies that are most abundant during the peak of stellar growth in the Universe (cite: Smail1997; Blain2002; casey2014dusty). At the peak of their population prevalence, DSFGs – also known as submillimeter galaxies – are believed to be the most massive (M$_\star \sim 10^{11}$ M$_\odot$) and most prolific star-forming galaxies, with star formation rates (SFRs) exceeding hundreds of solar masses per year (cite: casey2014dusty; hodgeanddacunha). Understanding this extreme population is critical for constraining many areas of astrophysics, including extreme stellar feedback and outflow models (cite: Hayward2021; Heintz2022; Bassini2023), rapid metal enrichment of the cosmos (cite: madau14; Shen2022; Birkin2023), the formation of the first massive quiescent galaxies (cite: toft14; Valentino2020; Long2023), and the collapse of dark matter halos in overdense environments at high-$z$ (cite: hickox2012; casey16; lewis18; Long2020; Lim2021). This is why, over the last two decades, it has become increasingly important to chart the prevalence, properties, and progression of DSFGs across cosmic time.

There is still mystery, however, surrounding the true abundance of luminous DSFGs in the first 2 Gyr of the cosmos, with up to two orders of magnitude in discrepancy across various studies at $z\gtrsim3$ (cite: Long2023; Valentino2023). This is largely because identifying $z>3$ DSFGs is difficult: their extreme dust-obscuration makes their starlight faint, or perhaps entirely undetectable (cite: walter12; Williams2019; Manning2022; McKinney2023b; Gentile2024), at rest-frame ultraviolet and optical wavelengths such that the typical emission lines used to secure redshifts of star-forming galaxies are attenuated beyond detection (cite: Herard-Demanche2023; Xiao2023). Photometric redshift estimates based on the shapes of their far-IR/sub-millimeter spectral energy distributions (SEDs) are highly uncertain and often span a wide range of potential redshifts ($z\sim1-12$) due to temperature-redshift degeneracies (cite: Casey2020); and far-IR spectroscopic scans are expensive as they often require integration times on the order of $\sim1.5-3$ hrs *per target* due to smaller fields of view, instrument sensitivity limitations, and the need to cover a wide spectral range (e.g. (cite: Gentile2024b), though gravitationally lensed sources can instead take mere minutes, (cite: Reuter2020)).

(cite: Casey2018a; Casey2018b) developed a backward galaxy evolution model of DSFGs based on empirical data that demonstrated how – with the appropriate depths – long wavelength observations ($\lambda_\mathrm{observed} \sim 2-3$ mm) can be an efficient way to detect DSFGs at $z>3$, while simultaneously filtering out the more numerous $z<3$ DSFG population. Early results leveraging this method prove promising, with several 2 mm (cite: Magnelli2019; Casey2021; Cooper2022; Cowie2023) and 3 mm (cite: zavala18; Williams2019) programs identifying high fractions of $z>3$ DSFGs in comparison to surveys at $\lambda_\mathrm{observed} \lesssim 1$ mm. This is the basis for the original Mapping Obscuration to Reionization with ALMA (MORA) Survey (cite: Zavala2021; Casey2021), a contiguous blank-field mapping survey at 2 mm in the Cosmic Evolution Survey (COSMOS) field (cite: Capak2007; Koekemoer2007; Scoville2007). The original survey covered 184 arcmin$^2$ and discovered 12 robust sources, with over 70% of the sample estimated to lie at $z>3$.

![](exmora_map.pdf)

![](noise_char.pdf)

In this Paper, we present an update to the original MORA Survey: the *extended* or Ex-MORA Survey. Ex-MORA is a factor of $\sim3\times$ larger than the original MORA survey, covering a total of 0.16 deg$^2$ over the COSMOS-Web Cycle 1 JWST Survey area (cite: cosmos-web). In Section [2](#sec:EM survey), we present the survey design, reduction, and map characteristics. In Section [3](#sec:sample selection), we present the 2 mm-bright sources detected at $\ge5\sigma$ in this survey, and their respective redshifts. Then, in Section [4](#sec:results), we present results on the cumulative number density of 2 mm sources, their redshift distributions, and highlight some interesting sample outliers, then provide our conclusions in Section [5](#sec:conclusions). Where relevant, we assume a standard $\Lambda$CDM cosmology with *Planck*-measured parameters (cite: PlanckCollaboration2020), with H$_0 = 67.4$ km s$^{-1}$ Mpc$^{-1}$, and a Chabrier initial mass function (cite: chabrier).

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| SB Name | R.A. | Dec | PWV | On Source Time | rms | Synth. Beam Size |
|  |  |  | \(mm\) | (min) | ($\mu$Jy beam$^{-1}$) |  |
| POS-01 | 10:00:48.8 | $+$02:22:30.0 | 0.91 | 37.95 | 87 | $1.71\ensuremath{''} \times 1.43\ensuremath{''}$ |
| POS-02 | 10:00:46.6 | $+$02:22:30.0 | 1.49 | 37.95 | 89 | $1.59\ensuremath{''} \times 1.44\ensuremath{''}$ |
| POS-04 | 10:00:42.1 | $+$02:22:30.0 | 1.03 | 37.97 | 91 | $1.78\ensuremath{''} \times 1.47\ensuremath{''}$ |
| POS-05 | 10:00:39.9 | $+$02:22:30.0 | 1.37 | 37.98 | 85 | $1.65\ensuremath{''} \times 1.40\ensuremath{''}$ |
| POS-06 | 10:00:37.7 | $+$02:22:30.0 | 1.28 | 37.97 | 94 | $1.82\ensuremath{''} \times 1.35\ensuremath{''}$ |
| POS-07 | 10:00:35.4 | $+$02:22:30.0 | 1.21 | 37.97 | 91 | $1.64\ensuremath{''} \times 1.43\ensuremath{''}$ |
| POS-08 | 10:00:33.2 | $+$02:22:30.0 | 1.43 | 38.00 | 112 | $2.06\ensuremath{''} \times 1.28\ensuremath{''}$ |
| POS-09 | 10:00:31.0 | $+$02:22:30.0 | 1.49 | 38.00 | 93 | $1.99\ensuremath{''} \times 1.28\ensuremath{''}$ |
| POS-16 | 10:00:15.4 | $+$02:22:30.0 | 0.87 | 37.98 | 78 | $1.65\ensuremath{''} \times 1.40\ensuremath{''}$ |
| POS-19 | 10:00:08.7 | $+$02:22:30.0 | 1.30 | 38.00 | 83 | $1.78\ensuremath{''} \times 1.37\ensuremath{''}$ |
| POS-21 | 10:00:04.2 | $+$02:22:30.0 | 1.37 | 37.98 | 89 | $1.64\ensuremath{''} \times 1.52\ensuremath{''}$ |
| EPOS-02 | 09:59:39.3 | $+$02:31:22.3 | 0.97 | 35.28 | 86 | $1.75\ensuremath{''} \times 1.49\ensuremath{''}$ |
| EPOS-03 | 09:59:38.1 | $+$02:29:12.9 | 1.45 | 39.85 | 88 | $1.95\ensuremath{''} \times 1.39\ensuremath{''}$ |
| EPOS-04 | 09:59:38.0 | $+$02:27:14.8 | 1.47 | 39.82 | 87 | $1.74\ensuremath{''} \times 1.46\ensuremath{''}$ |
| EPOS-05 | 09:59:38.5 | $+$02:25:20.1 | 1.48 | 37.72 | 90 | $1.64\ensuremath{''} \times 1.51\ensuremath{''}$ |
| EPOS-06 | 09:59:38.0 | $+$02:23:33.0 | 0.65 | 39.83 | 87 | $1.92\ensuremath{''} \times 1.39\ensuremath{''}$ |
| EPOS-07 | 09:59:38.0 | $+$02:21:37.1 | 0.61 | 39.82 | 84 | $1.69\ensuremath{''} \times 1.48\ensuremath{''}$ |
| EPOS-08 | 09:59:38.0 | $+$02:19:41.2 | 1.47 | 39.83 | 89 | $1.72\ensuremath{''} \times 1.37\ensuremath{''}$ |
| EPOS-09 | 09:59:38.0 | $+$02:17:45.2 | 0.69 | 39.85 | 90 | $1.91\ensuremath{''} \times 1.30\ensuremath{''}$ |
| EPOS-10 | 09:59:38.0 | $+$02:15:49.3 | 1.01 | 39.85 | 87 | $1.66\ensuremath{''} \times 1.52\ensuremath{''}$ |
| EPOS-11 | 09:59:38.0 | $+$02:13:53.4 | 1.58 | 39.83 | 94 | $1.76\ensuremath{''} \times 1.48\ensuremath{''}$ |
| EPOS-12 | 09:59:38.0 | $+$02:11:57.5 | 0.66 | 39.83 | 86 | $1.59\ensuremath{''} \times 1.43\ensuremath{''}$ |
| EPOS-14 | 09:59:57.5 | $+$02:31:35.8 | 0.39 | 39.83 | 79 | $2.28\ensuremath{''} \times 2.03\ensuremath{''}$ |
| EPOS-15 | 09:59:57.5 | $+$02:26:46.0 | 0.56 | 39.87 | 80 | $1.58\ensuremath{''} \times 1.41\ensuremath{''}$ |
| EPOS-17 | 09:59:57.5 | $+$02:16:56.7 | 1.82 | 39.83 | 105 | $2.16\ensuremath{''} \times 1.29\ensuremath{''}$ |
| EPOS-18 | 09:59:57.5 | $+$02:12:07.0 | 0.84 | 39.82 | 85 | $1.74\ensuremath{''} \times 1.34\ensuremath{''}$ |
| EPOS-19 | 10:00:12.4 | $+$02:09:55.9 | 1.02 | 38.75 | 94 | $1.72\ensuremath{''} \times 1.36\ensuremath{''}$ |
| EPOS-20 | 10:00:40.5 | $+$02:10:01.6 | 1.76 | 39.82 | 94 | $1.77\ensuremath{''} \times 1.37\ensuremath{''}$ |
| EPOS-21 | 10:00:58.7 | $+$02:11:09.0 | 0.60 | 38.22 | 84 | $1.64\ensuremath{''} \times 1.51\ensuremath{''}$ |
| EPOS-23 | 10:00:57.7 | $+$02:18:01.7 | 1.65 | 39.85 | 88 | $1.59\ensuremath{''} \times 1.44\ensuremath{''}$ |
| EPOS-24 | 10:00:57.8 | $+$02:21:27.2 | 1.48 | 39.33 | 111 | $1.57\ensuremath{''} \times 1.42\ensuremath{''}$ |
| EPOS-25 | 10:00:57.8 | $+$02:24:52.8 | 1.55 | 39.85 | 91 | $1.93\ensuremath{''} \times 1.34\ensuremath{''}$ |
| EPOS-26 | 10:00:57.8 | $+$02:28:18.5 | 0.97 | 39.28 | 89 | $2.03\ensuremath{''} \times 1.45\ensuremath{''}$ |
| OG MORA | ... | ... | ... | ... | $60-90$ | $1.83\ensuremath{''} \times 1.43\ensuremath{''}$ |
| Combined Mosaic | ... | ... | ... | ... | $50-260$ | $1.68\ensuremath{''}\times1.44\ensuremath{''}$ |

: Ex-MORA Survey Observation Characteristics

# The Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey

The Ex-MORA Survey (ALMA Project Code 2021.1.00225.S, PI: C.M. Casey) is an extension to the MORA survey presented in (cite: Zavala2021) and (cite: Casey2021). This updated survey was designed to extend the original MORA 2 mm blank-field coverage of the COSMOS-Web field (cite: cosmos-web) from 0.05 deg$^2$ to a contiguous 0.2 deg$^2$. Though A-rated, the project was only partially observed, resulting in a large, contiguous mosaic of $\sim$ 577 arcmin$^2$ or 0.16 deg$^2$ centered on $\alpha \approx$ 10:00:15, $\delta \approx$ +02:21:32 (shown in Figure [1](#fig:mora-map)). This is roughly a factor of three larger than the original MORA survey area (which is subsumed in the Ex-MORA map), covering roughly a third of the COSMOS-Web field. The deepest portion of the mosaic has an rms of $\sigma_\mathrm{2\,mm} = 51$ $\mu$Jy beam$^{-1}$, with $\sim$90% of the map ($\sim$ 510 arcmin$^2$) at or below the proposed map depth of 90 $\mu$Jy beam$^{-1}$ (Figure [1](#fig:mora-map)).

Observations took place during ALMA Cycle 8, from April 2022 to January 2023 in a nominal C43-2 configuration in band 4 centered on a 147 GHz local oscillator frequency tuning. We note that the original MORA survey was proposed to be observed over two different tunings (one centered on 147 GHz and one on 139 GHz) to optimize potential detections of emission lines at $z\sim2.5$; though original MORA was not completed, and most of the observed SBs were centered on 147 GHz. Thus, Ex-MORA was requested at only the one 147 GHz tuning in order to reduce overheads and to enable efficient mosaicking with original MORA survey. The 33 Ex-MORA scheduling blocks (SBs) were spatially distributed in a similar fashion as the original MORA survey. The unfinished SBs from the original MORA survey take the form of elongated “breadstick” mosaics of $\sim149$ pointings, and each of those pointings are 19.3$''$ offset in R.A. Newly designed Ex-MORA SBs are more square in their on-sky shape, and distributed around the perimeter of MORA, but fully aligned with the original MORA grid (following Nyquist spacing). The average phase center of each SB is reported in Table [\[table:obs\]](#table:obs), along with individual noise and precipitable water vapor (PWV) properties of each SB.

The mosaic was reduced and imaged in the same manner as presented in and , including the following key parameters: we imaged these data using natural weighting, with a robust value $=2$ to optimize source signal-to-noise ratios, set the cell / pixel size to 0.3 arcseconds (which is well below the synthesized beam size, see below), and averaged the maps over time bins of 10s. Observations were taken under an average and favorable precipitable water vapor of 1.10 mm. There are a total of 4851 individual pointings in the Ex-MORA mosaic; with $142-150$ pointings per SB and an average of 22 seconds per pointing, this combines to a total of 29.4 hrs (including overheads and calibrations). Measurement sets for the individual SBs were concatenated together using the CASA `concat` command, then reduced collectively as a mosaic. The combined mosaic has a typical synthesized beam size of $\theta_\mathrm{FWHM} \approx 1.68\ensuremath{''} \times 1.44\ensuremath{''}$, which is similar to the average beam sizes across individual SBs (see Table [\[table:obs\]](#table:obs)). This beam size translates to physical scales of $\sim 13 \times 11$ kpc at $z=3$, which is well beyond the observed physical extent of dust emission in galaxies at these epochs (cite: hodge16; Gillman2023). Thus, it is unlikely that sources are resolved out of the map, or spatially resolved in general. Therefore, we adopt source positions and flux densities corresponding to the point of their peak signal-to-noise by identifying all of the $>$5$\sigma$ pixels using a “region grow” algorithm (cite: Casey2018b; Cooper2022). As shown in Figure [2](#fig:noise), the SNRs of the map pixels are well represented by a standard normal centered about zero with $\sigma = 1$, above which positive source peaks diverge from the distribution, demonstrating that the SNR $\ge5$ $\sigma$ threshold is an ideal threshold for low source contamination.

A series of thorough tests on survey completeness, false detection rates, and flux boosting effects were carried out in . We repeat these tests and calculate the corresponding corrections in the same fashion, and summarize briefly here. To quantify the false detection rate, we create mock noise maps that are the same size as the Ex-MORA map, with Gaussian noise distributed randomly. We then convolve this map with the average synthesized beam listed above, and re-normalize the convolved map to a standard normal distribution to represent a pure noise (source–free) map. We then count the number of serendipitous peaks at or above 5$\sigma$ significance. We repeat this process 100 times, and calculate an average of $0.7^{+0.7}_{-0.5}$ of false detections in the Ex-MORA map, with an average SNR of $5.3\pm 0.2$. This is in good agreement with estimates in and , as well as our own catalog for which we identify one likely spurious source at the same SNR as the false detection estimates (see next Section). Survey completeness is calculated by inserting artificial sources at random positions around the mosaic, then using the same peak finding algorithm to recover them. This process is repeated 100 times, calculating the ratio between recovered and inserted sources on each iteration. We calculate the average completeness as a function of SNR, finding $\sim80\%$ survey completeness for sources with SNRs $\ge 6\sigma$, while sources at $5-6\sigma$ are most affected with source completeness estimated at $\sim50-70$%. We use these same simulations to estimate flux-boosting effects by taking the ratio of the input and recovered flux, and find these effects to be minimal ($\sim5\%$). These corrections are folded into the resulting on-sky number density calculation, as described in Section [4.1](#sec:onskydens).

# The 2 mm Selected Sample

In this section, we describe the Ex-MORA source catalog, and the ancillary data used to identify source counterparts and estimate their respective redshifts. The goal of this work is to update statistics on the efficiency of the 2 mm selection technique in identifying $z\gtrsim3$ massive, dust-obscured galaxies. Detailed analysis of the physical properties, morphologies, and environments of these sources will be presented in forthcoming papers.

## Ancillary Data

The Ex-MORA Survey benefits from complete coverage with the COSMOS-Web Survey (GO #1727, PIs: Casey & Kartaltepe; (cite: cosmos-web)), a 255 hr imaging program with contiguous coverage over 0.54 deg$^2$ in four JWST NIRCam filters (F115W, F150W, F277W, and F444W), and parallel MIRI imaging in the F770W band. Details on the survey design can be found in (cite: cosmos-web), and details on data reduction will be described in full in M. Franco et al. (2024, *in prep.*). In summary, JWST NIRCam data for the epoch used in this analysis are reduced with the JWST Calibration Pipeline version 1.12.1 (cite: Bushouse2023), with CRDS pmap-1170, corresponding to NIRCam instrument mapping imap-0273. We implement additional custom modifications used in other ERS and Cycle 1 surveys (cite: Bagley2023), including subtraction of 1/$f$ and background noise. NIRCam images achieve a 30 mas/pixel resolution, with astrometry aligned to the COSMOS2020 catalog (cite: Weaver2022), which is anchored to Gaia-EDR3.

We also include a wealth of ground and space-based optical/near-IR data from the COSMOS2020 catalog (cite: Weaver2022). In brief, this includes *Hubble*/F814W imaging (cite: Koekemoer2007), the *Spitzer* Cosmic Dawn Survey (cite: EuclidCollaboration2022), Subaru Telescope Hyper Suprime-Cam (HSC) imaging (cite: Aihara2022), and UltraVISTA imaging (cite: McCracken2012).

The COSMOS field also contains surveys across X-ray, millimeter, and radio wavelengths. Millimeter and submillimeter data includes SCUBA-2 maps at 850 $\mu$m (cite: Simpson2019), and archival ALMA datasets collated in the A3COSMOS project (cite: Liu2018). These data are primarily used to refine the dust spectral energy distribution (SED) models and accompanying photo-$z$s. X-ray and radio data are primarily used to discern the presence of powerful active galactic nuclei (AGN), and to quantify whether AGN emission contributes to the 2 mm flux and/or the galaxy’s multiwavelength SED. For these analyses, we use data from the Chandra COSMOS-Legacy program (cite: Civano2016), the VLA-COSMOS 3 GHz Large Project (cite: Smolcic2017), and the MeerKAT MIGHTEE-COSMOS 1.28 GHz survey (cite: Heywood2022).

## NIRCam Photometry

The NIRCam counterparts to our 2mm-selected sources have resolved morphologies that can be challenging to optimally recover with standard photometric methods using circular or elliptical apertures. We tested measuring multi-wavelength aperture fluxes with `SE/SE++` (cite: setractor) and found the flux densities to be inconsistent between ground-based (e.g. UltraVISTA) and JWST NIRCam data above 1$\sigma_\mathrm{ground}$. In light of these challenges, we measure fluxes using `diver` (McKinney et al. in prep.), an empirically-motivated photometry tool built to preserve the resolution of JWST when measuring PSF-matched multi-wavelength photometry. We now briefly summarize the methodology of `diver` below.

For each of our sources `diver` proceeds through the following: First, we make $50^{\prime\prime}\times50^{\prime\prime}$ cutouts around the target in the science image and error/weight image from which a flux will be measured.

Next, we create a segmentation map using `photutils` (cite: photutils) from the NIRCam/F444W map, and in some cases include an additional de-blending step to isolate the source from its neighbors. We adopt the arbitrarily shaped segmentation boundary (down to an SNR-per-pixel of 3) of the source as an aperture through which to measure all multi-wavelength photometry. We measure the flux through this aperture in every image and, for lower resolution data (e.g. ground-based and *Spitzer* IRAC data), multiply by a PSF correction factor that accounts for the flux loss due to aperture corrections. We measure flux uncertainties from the local background summed in quadrature with the shot noise, readout noise, and dark current noise all bootstrapped from the error/weight maps using the arbitrarily shaped aperture to faithfully capture the noise scaling per pixel.

The JWST NIRCam (F115W, F150W, F277W, and F444W) fluxes and flux errors measured with `diver` are generally consistent with the aperture fluxes from `SE/SE++` within $1\sigma_{\rm diver}$, but not within $1\sigma_{\rm SE/SE++}\ll\sigma_{\rm diver}$. Most notably, the multi-wavelength fluxes from `diver` are far more consistent between ground-based and JWST data given the expected shape of the rising SEDs into the near-infrared.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | Original Name | R.A. | Dec | S/N$_\mathrm{2\,mm}$ | 2 mm Flux Density | z$_\mathrm{spec}^\dagger$ | z$_\mathrm{phot}$ |
|  |  | (deg) | (deg) |  | ($\mu$Jy) |  |  |
| eMORA.0 | MORA-0 | 10:00:15.62 | $+$02:15:49.14 | 19.8 | 1023 $\pm$ 52 | 4.596 | 4.4 $_{-0.2}^{+0.2}$ |
| eMORA.1 |  | 09:59:57.28 | $+$02:27:30.54 | 18.8 | 1133 $\pm$ 60 | 4.618 | 1.0 $_{-0.1}^{+0.1}$ |
| eMORA.2 | MORA-3 | 10:00:08.05 | $+$02:26:12.24 | 17.2 | 1157 $\pm$ 67 | 4.630 | 3.4 $_{-0.1}^{+0.1}$ |
| eMORA.3 |  | 09:59:42.85 | $+$02:29:38.32 | 13.9 | 924 $\pm$ 66 | 4.340 | 4.4 $_{-0.1}^{+0.1}$ |
| eMORA.4 | MORA-2 | 10:00:10.15 | $+$02:13:34.74 | 8.8 | 523 $\pm$ 59 | 3.254$^\mathrm{c}$ | 7.6 $_{-0.3}^{+0.3}$ |
| eMORA.5$^\mathrm{a}$ | MORA-10 | 10:00:16.58 | $+$02:26:38.04 | 8.2 | 467 $\pm$ 57 | 2.470 | 7.0 $_{-0.2}^{+0.5}$ |
| eMORA.6 |  | 09:59:35.34 | $+$02:22:36.51 | 8.2 | 501 $\pm$ 61 |  | 3.8 $_{-0.7}^{+0.6}$ |
| eMORA.7 | MORA-1 | 10:00:19.74 | $+$02:32:03.84 | 7.6 | 706 $\pm$ 93 | 3.340$^\mathrm{c}$ | 4.5 $_{-0.9}^{+0.7}$ |
| eMORA.8 |  | 09:59:48.89 | $+$02:27:50.93 | 7.3 | 472 $\pm$ 65 |  | 4.4 $_{-1.7}^{+1.4}$ |
| eMORA.9 |  | 09:59:33.44 | $+$02:23:47.00 | 7.2 | 444 $\pm$ 61 |  | 2.5 $_{-0.2}^{+0.2}$ |
| eMORA.10 |  | 10:00:56.95 | $+$02:20:17.30 | 6.9 | 432 $\pm$ 63 | 2.494 | 2.6 $_{-0.2}^{+0.2}$ |
| eMORA.11 | MORA-4 | 10:00:26.37 | $+$02:15:28.14 | 6.6 | 568 $\pm$ 86 | 5.850 | 5.9 $_{-2.0}^{+1.2}$ |
| eMORA.12 | MORA-6 | 10:00:28.71 | $+$02:32:03.54 | 6.6 | 621 $\pm$ 94 | 3.410$^\mathrm{c}$ | 3.4 $_{-0.1}^{+0.1}$ |
| eMORA.13 | MORA-5 | 10:00:24.15 | $+$02:20:05.64 | 6.4 | 579 $\pm$ 90 |  | 2.6 $_{-1.0}^{+1.6}$ |
| eMORA.14 |  | 10:00:33.32 | $+$02:26:02.03 | 6.4 | 505 $\pm$ 79 | 2.510 | 2.5 $_{-0.1}^{+0.1}$ |
| eMORA.15$^\mathrm{a}$ |  | 09:59:37.41 | $+$02:23:47.31 | 6.2 | 382 $\pm$ 61 | 0.741 | 0.7 $_{-0.1}^{+0.1}$ |
| eMORA.16 |  | 10:01:02.30 | $+$02:22:33.79 | 6.2 | 397 $\pm$ 64 | 3.717 | 3.4 $_{-0.1}^{+0.1}$ |
| eMORA.17 |  | 10:01:02.04 | $+$02:28:36.49 | 6.1 | 418 $\pm$ 68 |  | 3.9 $_{-1.0}^{+2.5}$ |
| eMORA.18 |  | 09:59:29.22 | $+$02:12:44.30 | 6.1 | 375 $\pm$ 61 |  | 2.5 $_{-0.1}^{+0.1}$ |
| eMORA.19 |  | 09:59:38.97 | $+$02:21:26.61 | 6.1 | 370 $\pm$ 61 |  | 4.2 $_{-0.3}^{+0.3}$ |
| eMORA.20 |  | 10:00:15.90 | $+$02:24:46.14 | 6.0 | 318 $\pm$ 53 |  | 5.2 $_{-0.7}^{+0.7}$ |
| eMORA.21 | MORA-7 | 10:00:11.58 | $+$02:15:05.34 | 6.0 | 370 $\pm$ 61 |  | 2.9 $_{-0.3}^{+0.2}$ |
| eMORA.22 |  | 10:01:03.16 | $+$02:21:42.49 | 6.0 | 378 $\pm$ 64 |  | 4.7 $_{-0.1}^{+0.1}$ |
| eMORA.23 |  | 09:59:31.16 | $+$02:14:33.50 | 5.9 | 412 $\pm$ 70 |  | 4.2 $_{-0.6}^{+0.7}$ |
| eMORA.24 |  | 09:59:57.09 | $+$02:11:36.53 | 5.8 | 354 $\pm$ 61 | 2.411$^\mathrm{c}$ | 2.3 $_{-0.2}^{+0.2}$ |
| eMORA.25 |  | 09:59:45.62 | $+$02:11:26.62 | 5.7 | 345 $\pm$ 61 |  | 4.7 $_{-0.1}^{+0.1}$ |
| eMORA.26 | MORA-8 | 10:00:25.29 | $+$02:18:46.14 | 5.6 | 491 $\pm$ 87 | 2.280 | 2.2 $_{-0.1}^{+0.1}$ |
| eMORA.27 |  | 10:00:47.10 | $+$02:10:16.42 | 5.6 | 379 $\pm$ 68 | 5.050 | 4.0 $_{-0.6}^{+0.6}$ |
| eMORA.28 | MORA-9 | 10:00:17.30 | $+$02:27:15.84 | 5.5 | 345 $\pm$ 63 |  | 4.6 $_{-1.2}^{+1.3}$ |
| eMORA.29 |  | 10:00:09.83 | $+$02:16:49.74 | 5.4 | 325 $\pm$ 60 |  | 4.7 $_{-0.5}^{+1.0}$ |
| eMORA.30 |  | 09:59:29.78 | $+$02:27:39.80 | 5.4 | 348 $\pm$ 65 |  | 3.1 $_{-1.3}^{+1.8}$ |
| eMORA.31$^\mathrm{b}$ |  | 09:59:23.28 | $+$02:19:45.18 | 5.3 | 815 $\pm$ 154 |  | – |
| eMORA.32 |  | 09:59:43.65 | $+$02:13:40.12 | 5.2 | 345 $\pm$ 67 |  | 2.6 $_{-0.2}^{+0.2}$ |
| eMORA.33 |  | 10:00:08.97 | $+$02:20:26.64 | 5.1 | 318 $\pm$ 62 |  | 2.5 $_{-0.1}^{+0.2}$ |
| eMORA.34 |  | 10:00:41.34 | $+$02:30:29.93 | 5.1 | 322 $\pm$ 64 | 0.700 | 0.7 $_{-0.1}^{+0.1}$ |
| eMORA.35 |  | 09:59:44.03 | $+$02:21:08.92 | 5.0 | 304 $\pm$ 60 |  | 5.7 $_{-1.5}^{+1.3}$ |
| eMORA.36$^\mathrm{a}$ |  | 09:59:24.03 | $+$02:27:08.28 | 5.0 | 454 $\pm$ 91 | 0.710 | 0.7 $_{-0.1}^{+0.1}$ |

: Ex-MORA $\ge$5$\sigma$ Sources

Table notes: $^{}$ The $\ge$5$\sigma$ sources identified in the Ex-MORA Survey. Spectroscopic redshifts (if available) are listed in the $z_\mathrm{spec}$ column, while photo-$z$s (estimated via BAGPIPES or the COSMOS2020 catalog) are listed with their 68% confidence intervals in the $z_\mathrm{phot}$ column. When available, spectroscopic redshifts are used over photometric redshifts. $^{\dagger}$ All spectroscopic redshifts are compiled in Khostovan et al. (in prep), with the original surveys as follows. Rest-frame optical / UV redshifts are from (cite: Lilly2007; Trump2007; Kriek2015; Stott2016; Nanayakkara2016; Marsan2017; Hasinger2018; Wisnioski2019); Vanderhoof et al. (in prep); Kartaltepe et al. (in prep); and Capak et al. (in prep). CO-derived redshifts are from (cite: Yun2015; Jin2019; Casey2019; Jimenez-Andrade2020; Chen2022); and Chen et al. (in prep). $^{a}$ These sources have significant synchrotron emission without which they would not be detected in this survey. $^{b}$ This source is likely spurious, see Section [3](#sec:sample selection). $^{c}$ The spec-$z$s for these sources are based off single CO line detections (with additional supporting information from their photo-$z$ probability distributions, see Appendix Section [7.1](#sec:degenerate-z)).

## Source Selection

As mentioned in Section [2](#sec:EM survey), we adopt source positions and flux densities corresponding to the point of their peak signal-to-noise using a “region grow” algorithm for peaks at or above 5$\sigma$ significance. Overall, 37 sources are identified in the combined Ex-MORA map at or above 5$\sigma$ significance, with 11 of the original 13 MORA sources recovered . One of the missing original sources (MORA-12) was already believed to be spurious due to lack of detection at any other wavelengths and proximity to the edge of the original maps . In the combined Ex-MORA mosaic, the rms at the edges of the original MORA map – where MORA-12 was discovered – are improved. In this new mosaic, MORA-12 disappears entirely, thus confirming its nature as a false object. The other original MORA source (MORA-11) is recovered with an SNR of 4.9$\sigma$ and therefore just misses the 5$\sigma$ threshold for inclusion in this work.[^1] We report source coordinates, relevant flux densities, and estimated and/or spectroscopic redshifts for the 37 sources detected at $\ge5\sigma$ in Table [\[table:sources\]](#table:sources). Sources are numbered in inverse order according to their 2 mm SNRs, with eMORA.0 having the highest SNR across the sample.

Of the 37 sources, 36 ($\sim97\%$) are detected at wavelengths $\lambda_\mathrm{observed}<8\,\mu m$ and 31 ($\sim84\%$) are detected with SCUBA-2 at 850 $\mu$m. All sources are detected at minimum in the F444W band, with the exception of one source – eMORA.31. This source is also not detected in any *Spitzer* IRAC bands nor SCUBA-2 imaging, has no ancillary ALMA or radio detections, and is on the edge of the map in a noisy region; thus, we believe this source likely a positive noise fluctuation. We remove eMORA.31 from the analyses in this work, though keep it listed in the Table for posterity.

In , MORA-10 (herein eMORA.5) had reported synchotron emission significant enough to boost the 2 mm emission such that without this component, this source would not meet the detection threshold of the survey. Using data from the VLA-COSMOS and MIGHTEE-COSMOS surveys, we find that $23/36$ sources have detections at both the 1.28 GHz and 3 GHz frequencies. Using these detections, we calculate synchrotron slopes and extend this to the 2 mm wavelength. We find that most sources ($n=20$, or $\sim87$ %) have estimated sub-percent levels of synchrotron emission in the 2 mm band. Two out of the three remaining sources are previously identified $z\sim0.7$ AGN (cite: Trump2007), while the third is the spectroscopically confirmed $z=2.57$ MORA-10/eMORA.5 source previously discussed in , and spectroscopically confirmed in (cite: Kriek2015). None of these three sources would meet our survey thresholds without significant boosts ($\gtrsim 40\%$ of total 2 mm flux) from their synchrotron emission. The two $z<1$ radio-boosted sources are also undetected in the SCUBA-2 maps, suggesting that the synchrotron emission is from AGN activity rather than star formation processes. Given that only a small fraction ($n=2/33$, or $<10\%$) of dust-luminous Ex-MORA galaxies lack submillimeter detections, we conclude that 2 mm follow up on SCUBA-2 sources may prove an efficient filter for high-$z$ dust-obscured systems, as suggested in (cite: Cooper2022) and (cite: Cowie2023).

As in and , we remove the three synchrotron-boosted sources for our statistical analyses of dust continuum emitters, and note that our results presented in Section [4](#sec:results) do not change significantly if these sources were included.

## Source Redshifts

Of the 36 bona fide sources presented herein, 18 have spectroscopic redshifts established in the literature, with 10 at $z_\mathrm{spec}>3$. These spectroscopic redshifts are compiled from several catalogs across multiple wavelengths, with the majority compiled in Khostovan et al. (in prep). This includes the following original surveys: rest-frame optical / UV redshifts are from (cite: Lilly2007; Trump2007; Kriek2015; Stott2016; Nanayakkara2016; Marsan2017; Hasinger2018; Wisnioski2019); Vanderhoof et al. (in prep); Kartaltepe et al. (in prep); and Capak et al. (in prep); CO-derived redshifts are from (cite: Yun2015; Jin2019; Casey2019; Jimenez-Andrade2020; Chen2022); and Chen et al. (in prep). A handful of sources have spectroscopic redshifts based on a single CO transition line, meaning their interpretation could be uncertain. We discuss how we address each of these sources individually in Appendix Section [7.1](#sec:degenerate-z).

For the majority of the remaining sources, we use photometric redshifts derived via the BAGPIPES SED-fitting code (cite: Carnall2018) using all of the available UV-to-near-IR data (which now includes JWST data in addition to the data in COSMOS2020). We allow the stellar mass to vary between $10^{6-13}$ M$_\odot$, and the stellar metallicity from $10^{-3}$ to $10^{0.4}$, both with log-uniform priors. We adopt a non-parametric star-formation history (SFH) model, with five bins in age (fixed bin edges at 10, 30, 100, 300, and 600 Myr) and a constant star-formation history in each bin. We adopt the “continuity prior,” to explicitly weigh against significant SFR changes between adjacent bins and avoid overfitting the data (cite: Leja2019). We include nebular emission, and allow the ionization parameter $\log U$ to vary from –3 to –1. Dust attenuation is included following a (cite: calzetti00) attenuation law with $A_V$ allowed to vary from $0$ to $6$ with a uniform prior.

For a six sources, BAGPIPES either failed to produce a fit, or produced an unphysical solution for their photo-$z$. We address these sources individually in Appendix Section [7.2](#sec:deg-photo-z).

We compare the calculated photo-$z$s to spectroscopic redshifts for the 18 available sources in Figure [4](#fig:z_relations) and find good agreement, with a normalized median absolute deviation (cite: Brammer2008) of $\sigma_\mathrm{NMAD} = 0.04$. We quantify the catastrophic outlier fraction as the fraction of galaxies with $|z_\mathrm{phot} - z_\mathrm{spec}| \ge (5\times\sigma_\mathrm{NMAD})(1+z_\mathrm{spec})$ (cite: Weaver2024), and find that less than a third of the photo-$z$s are 5$\sigma_\mathrm{NMAD}$ away from the one-to-one relation. We also compare newly derived redshifts to those derived in the COSMOS2020 catalog (when available) and find the majority of source redshift estimates are also in similarly good agreement.

# Results & Discussion

In the following Section, we report statistics on the Ex-MORA sample redshift and 2 mm flux density distributions. We do not include eMORA.31 (the likely spurious source), nor the three synchrotron emitters from these analyses as the primary goal of this work is to survey thermal dust emission at 2 mm. Still, we stress that the results agree within 1$\sigma$ uncertainty even if these sources are included.

![](mora_2mm_skydensity.png)

## 2 mm Cumulative Number Density

The cumulative number density is defined as the on-sky surface density of sources above a certain flux density threshold, per square degree. We derive the cumulative number density in a similar fashion as presented in using the 5$\sigma$ source catalog and corresponding completeness and contamination uncertainties, as described at the end of our Section [2](#sec:EM survey). We describe this process briefly here. Firstly, we estimate the contribution of a source to the cumulative number density through the following equation: $$\begin{equation}
    \eta_i(S_i,\sigma_i) = \frac{1-f_\mathrm{cont}(\sigma_i)}{\zeta(S_i)A_\mathrm{eff}}
\end{equation}$$ for a source with a given deboosted flux density, $S_i$, and SNR, $\sigma_i$; $f_\mathrm{cont}(\sigma_i)$ is the contamination fraction for the measured SNR ($\sigma_i$); $\zeta(S_i)$ is the corresponding completeness for the flux density, and $A_\mathrm{eff}$ is the area of the Ex-MORA map (577 arcmin$^2$). Cumulative number counts are calculated as $N(>S) = \Sigma_i\eta_i(S_i,\sigma_i)$.

In order to propagate flux, completeness, and contamination uncertainties into the cumulative number densities, we generate a Monte Carlo simulation. For each iteration, we model individual source flux densities as a Gaussian distribution, setting the dispersion equal to the measured uncertainty. We sample the respective distribution for each individual source and recalculate the SNR given the local noise around that source. We then use this SNR to sample the contamination fraction (which was generated as a function of SNR, as described in Section [2](#sec:EM survey), and modeled as Gaussians). Each individual source in each iteration also has its own completeness estimates, based on the artificial source injection simulations mentioned in Section [2](#sec:EM survey) and . We repeat this process $10^3$ times, each time calculating the resulting cumulative number density and corresponding Poisson noise over flux density bins of size 100 $\mu$Jy. We then calculate the mean, 16th and 84th percentiles, and average Poisson noise in each flux density bin. The resulting cumulative number density is shown in Figure [3](#fig:skydens), and reported in Table [\[table:no_dens\]](#table:no_dens). We repeat the above processes while including the four removed sources and find that the differences between cumulative number densities is not significant, and within uncertainty of the ‘cleaned’ cumulative number density. These are also presented in Table [\[table:no_dens\]](#table:no_dens).

In Figure [3](#fig:skydens), we compare our results to existing 2 mm number counts from blank-field surveys across the literature: the 31 arcmin$^2$ and 250 arcmin$^2$ GISMO/IRAM surveys reported in (cite: Staguhn2014) and (cite: Magnelli2019), respectively; the 1010 arcmin$^2$ COSMOS portion of the IRAM NIKA2 Cosmological Legacy Survey (cite: Bing2023); the number counts from the original MORA survey in ; and predictions from the SHARK (cite: Lagos2020) and SIDES (cite: Bethermin2017) cosmological simulations. On average, all literature estimates are greater than those we calculate by a factor of $2-3$, with the exception of the NIKA2-CLS COSMOS estimates which are $7-8\times$ higher than our estimates. The NIKA2-CLS cumulative number densities shown in Figure [3](#fig:skydens) are the *source* counts, not the galaxy counts. Due to the large beam size of single-dish NIKA2 at 2 mm ($18$ ”), true galaxy sources are expected to blend together (cite: Bethermin2017). We apply the “source-to-galaxy counts correction factor” derived for this survey in (cite: Bing2023) and find that our estimates are in more agreement, within a factor of $\sim2$, which is similar to the other estimates reported in the literature. Finally, we note that the SHARK semi-analytical model is roughly successful (within uncertainty) in predicting number densities at $S_\mathrm{2\,mm} \gtrsim 800\,\mu$Jy, but then over-predicts the faint end by $\sim2-3\sigma$; while the SIDES model performs in an opposite manner, better modeling the observed cumulative number densities at $S_\mathrm{2\,mm} \lesssim 700\,\mu$Jy, but not quite meeting the bright end. We also note that SHARK produces overall more 2 mm luminous sources per Mpc$^3$ than SIDES (and Ex-MORA), which likely produces the systemic offset between the two simulations. As mentioned in , some of the differences in alignment with the observations may driven by intrinsic differences in the redshift distributions of the 2 mm population. For example, for sources with $S_\mathrm{2\,mm} >= 300$ $\mu$Jy (like Ex-MORA), both simulations produce average redshifts around $\sim3.2$, which is slightly lower than our survey results ($\sim3.6$). SIDES predicts that higher redshifts correlate with higher 2 mm fluxes (which may be supported by the Ex-MORA sample, see Figure [4](#fig:z_relations) and Section [4.2](#sec:zdist)), and therefore Ex-MORA’s slightly higher redshift distribution may drive divergence from the SIDES model at the bright end.

We note a distinct difference between the number density shapes / distributions between Ex-MORA and the original MORA survey . By eye, the MORA cumulative number densities appear to follow a Schechter function, while the Ex-MORA cumulative number densities appear more like a double Schechter function, as Ex-MORA has an apparent comparative deficit in sources with flux densities between $400-800\,\mu$Jy (though the surveys only differ beyond 1$\sigma$ uncertainty at $400-600\,\mu$Jy). We tested whether these differences could be driven by potential variances in data reduction techniques, beam sizes, and/or weather, and find no significant changes in our resulting sample size / cumulative number density. It is possible that completeness corrections for sources at $S_\mathrm{2\,mm} \lesssim 700\,\mu$Jy in the original MORA survey were somewhat overestimated as MORA had overall poorer rms (with only $\sim60\%$ of the map with an rms of $90\,\mu$Jy beam$^{-1}$ or less, versus 90% for the Ex-MORA map; see Fig. [2](#fig:noise)), resulting in low source recovery for fainter sources in the source injection simulations. Ex-MORA, being both deeper and wider, had only significant completeness corrections for sources with flux densities $\lesssim 450\,\mu$Jy, which corresponds to the $5\sigma$ threshold for a map with rms ($\sigma$) $=90\,\mu$Jy beam$^{-1}$. For MORA, the corresponding 90$\%$ rms is $\sim156\,\mu$Jy beam$^{-1}$, setting the 5$\sigma$ threshold at 780 $\mu$Jy, which is near where we begin to see the departure between survey results as the completeness corrections in MORA become significant ($>10\%$). Both surveys estimate the same number of sources at the faintest end (within uncertainty), where $S_\mathrm{2\,mm} \sim 300\,\mu$Jy, which at $5\sigma$ corresponds to an rms of 60 $\mu$Jy beam$^{-1}$. While the rms varies over both maps and Ex-MORA is generally deeper, both Ex-MORA and MORA have a small fraction of the map at or below an rms of 60 $\mu$Jy beam$^{-1}$ ($\sim2-6\%$), which means that the completeness corrections for sources near this flux density are likely similar across both surveys.

c \| ccc \| ccc & 3cAll Sources & 3cCleaned Sample\
$S_\mathrm{2\,mm}$ & $N(>S)$ & $-\delta\,N$ & $+\delta\,N$ & $N(>S)$ & $-\delta\,N$ & $+\delta\,N$\
(mJy) & (deg$^{-2}$) & (deg$^{-2}$) & (deg$^{-2}$) & (deg$^{-2}$) & (deg$^{-2}$) & (deg$^{-2}$)\
& 365 & 42 & 41 & 325 & 36 & 38\
0.40 & 152 & 17 & 16 & 134 & 16 & 15\
0.50 & 79 & 13 & 13 & 72 & 13 & 12\
0.60 & 47 & 7 & 7 & 39 & 7 & 6\
0.70 & 40 & 7 & 7 & 32 & 6 & 6\
0.80 & 32 & 6 & 6 & 25 & 5 & 5\
0.90 & 25 & 5 & 5 & 25 & 5 & 5\
1.00 & 16 & 8 & 7 & 16 & 8 & 7\
1.10 & 13 & 4 & 3 & 13 & 4 & 3\
1.20 & 6 & 3 & 3 & 6 & 3 & 3

Table notes: $^{}$ The ‘Cleaned Sample’ corresponds to Figure [3](#fig:skydens) and represents estimates with the spurious source (eMORA.31) and significant synchrotron emitters (eMORA.5, eMORA.15, and eMORA.36) removed.

![image](spec_v_photo.png) ![image](2mm_v_z.png) ![image](ratio_v_z.png) ![image](cdf_nz.png)

## Redshift Distribution of 2 mm Sources

In Figure [4](#fig:z_relations), we present the cumulative distribution function (CDF) of Ex-MORA sources. We calculate the CDF over 10$^3$ iterations. For each instance, we sample from each source’s redshift probability distribution function, *p(z)*, for galaxies with photo-$z$s, while galaxies with spec-$z$s are treated as delta functions. We then calculate the mean CDF and 68% confidence interval from the 10$^3$ CDFs generated in the 10$^3$ iterations.

Based on the CDF, we find that 95$^{+2}_{-1}$% of 2 mm selected sources are at $z>2$, 66$^{+3}_{-3}$% at $z>3$, and 43$^{+4}_{-4}$% at $z>4$. This means that most 2 mm selected sources are likely at $z>3$, and nearly *half* are likely at $z>4$. We sample from the CDF and corresponding uncertainties to measure a median redshift of $\langle z \rangle = 3.6^{+0.1}_{-0.2}$ which is remarkably equivalent to the estimate derived in over a smaller area using less sensitive OIR data. This average is higher than the smaller and shallower GISMO/IRAM 2 mm Survey in (cite: Staguhn2014), but is in more agreement with the average found in the corresponding follow up survey that is $\sim8\times$ larger in area than the original (cite: Magnelli2019), with $\langle z \rangle  = 3.9$.

In Figure [4](#fig:z_relations), we also show redshift CDFs from the (cite: Casey2018a; Casey2018b) theoretical models representing a ‘dust-poor’ versus ‘dust-rich’ early Universe. In this scenario, a ‘dust-poor’ early Universe is one without intense, dusty starbursts (with obscured SFRs $> 100$ M$_\odot$ yr$^{-1}$), *not* an early Universe devoid of galaxies with significant fractions of obscured star-formation (cite: fudamoto20; Algera2023). The models are generated by sampling over a simulated 2 mm survey of the same on-sky area as Ex-MORA. While the Ex-MORA survey is successful at identifying primarily $z>3$ IR luminous galaxies, the results are still consistent with – and even markedly below – the ‘dust-poor’ model. This means that the number density of heavily obscured, starbursting galaxies at high-$z$ should decrease with increasing redshift at $z>3$, and that the cosmic star formation rate density may be less dominated by extreme systems of obscured star formation during these epochs. The former implication is demonstrated in Section [4.3](#sec:nodens), while the latter will be presented in a forthcoming paper. Combining cumulative number densities from the original MORA survey with 1.2 mm and 3 mm number counts from the literature, generated an independent prediction for the cumulative redshift distribution of 2 mm selected sources[^2], predicting roughly twice the number of $z>3$ sources than what we measure, even though their predictions are also consistent with a ‘dust-poor’ early Universe. They estimated that the evolution of the characteristic number density of IR luminous galaxies $\Phi_\star \propto (1+z)^{\psi}$ is steeply declining at $z\gtrsim2$, with $\psi = -6.5^{+0.8}_{-1.8}$. Given that Ex-MORA produces even fewer 2 mm luminous galaxies at $z>3$ than expected based on the model in , it is likely that $\Phi_\star$ is declining at an even more rapid rate, with $\psi < -6.5$. Future work using Ex-MORA to constrain the evolution of the IR luminosity function parameters at higher detail will be forthcoming.

We also explore the relationship between source redshifts and their 2 mm flux densities, as well as their ratios between 850 $\mu$m and 2 mm flux densities, in Figure [4](#fig:z_relations). This latter ratio was shown to potentially correlate with source redshifts such that lower ratios correspond to higher redshifts as the 850 $\mu$m and 2 mm bands begin mutually probing the peak of dust emission (cite: Casey2021; Cooper2022). As seen in Casey et al. and Cooper et al., both relationships show potential for correlation such that higher redshift sources are on average brighter at 2 mm, and have lower $S_\mathrm{850\,\mu m}/S_\mathrm{2\,mm}$ ratios. This appears particularly true for most of the spectroscopically confirmed sources in the Ex-MORA sample. However, when considering sources with photometrically derived redshifts, both of these trends appear to wash out. Future followup spectroscopic surveys over larger samples will prove fruitful in ascertaining whether these values are truly correlated with galaxy redshifts at $z\gtrsim3$.

## Volume Density of 2 mm Sources at $z\gtrsim3$

The large contiguous area of the Ex-MORA survey, combined with rich ancillary data (including JWST imaging) and a well defined flux threshold, enables strong constraints on high-$z$ DSFG volume densities. In Figure [5](#fig:vol_dens), we present the volume density of Ex-MORA sources over $z=0-8$ alongside estimates collated from the literature using a variety of DSFG samples (cite: michalowski17; Williams2019; Lagos2020; Valentino2020; Manning2022; Chen2022). We calculate our estimates using the same method presented in Section [4.2](#sec:zdist) in volumes encompassed by redshift bins of size $\delta z = 1$ over the Ex-MORA survey area. We add in quadrature cosmic variance, $\sigma_\mathrm{CV}$, over the various redshift bins following the prescription in McKinney et al. (in prep) using the standard assumptions and cookbook presented in (cite: Moster2011). We note that $\sigma_\mathrm{CV}$ dominates the volume density uncertainties for 2 mm-luminous sources at $z>2$. The resulting calculations and corresponding uncertainties are presented in Table [\[table:voldens\]](#table:voldens).

Current volume density estimates of submillimeter-luminous DSFGs at $z\gtrsim3$ are in tension by a factor of $\sim100$, ranging from $\sim 3 \times 10^{-5}$ Mpc$^{-3}$ (cite: Williams2019) to $\sim 4 \times 10^{-7}$ Mpc$^{-3}$ (cite: Valentino2020; Valentino2023). In this sample, we derive a roughly steady volume density of 2 mm -bright galaxies from $z=2$ to 5 of $\sim4-5 \times 10^{-6}$ Mpc$^{-3}$. This estimate agrees well with estimates derived from hundreds of SCUBA-2 selected DSFGs in (cite: michalowski17), but is slightly higher (specifically at $z>3$) than the (duty cycle corrected) volume densities reported in (cite: Chen2022), though the latter study at present has a much smaller sample size. We also compare to the SHARK (cite: Lagos2020) and SIDES (cite: Bethermin2017) cosmological models by only including sources with $S_\mathrm{2\,mm} > 300$ $\mu$Jy (the lower flux density threshold of our sample). Despite general success in modeling the bright end of the 2 mm cumulative number density, both models over predict the abundance of 2 mm sources across $z\sim2-4$ by roughly a factor of 3; however, the models do exhibit a similar rate of population decrease from $z=4$ to $z=7$, and are in more agreement with the observed number densities at $z>4$.

![](vol_dens.png)

| Redshift  | log$_\mathrm{10}$($n$/Mpc$^{-3}$) | $\sigma_\mathrm{CV}$ |     |     |
|:---------:|:---------------------------------:|:--------------------:|:---:|:---:|
| $0< z <1$ |         $-5.80 \pm 0.03$          |         0.09         |     |     |
| $1< z <2$ |         $-6.57 \pm 0.56$          |         0.09         |     |     |
| $2< z <3$ |         $-5.32 \pm 0.04$          |         0.13         |     |     |
| $3< z <4$ |         $-5.42 \pm 0.07$          |         0.20         |     |     |
| $4< z <5$ |         $-5.32 \pm 0.07$          |         0.31         |     |     |
| $5< z <6$ |         $-5.55 \pm 0.12$          |         0.46         |     |     |
| $6< z <7$ |         $-6.04 \pm 0.28$          |         0.64         |     |     |

: Ex-MORA 2 mm Volume Densities

## Other High-$z$ Red Selection Techniques

In recent years, several new techniques were developed to efficiently select $z>3$ dusty galaxies, with a special focus on sources with faint or no emission at optical/near-IR (OIR) wavelengths. These “OIR-dark” galaxies are believed to live predominantly at high redshifts ($z>3$), contribute significantly to the cosmic star formation rate density ($\sim 10-50\%$), and serve as a primary parent population for the first massive quiescent galaxies at $z\sim3-5$ (cite: Wang2019; Talia2021; Manning2022; Enia2022; Barrufet2023; Xiao2023b; Xiao2023; vanderVlugt2023). It is important to note, however, that each of these methods selects different populations of dusty galaxies (cite: Talia2021), with variations over average star formation rates, stellar masses, and redshifts. In the following, we apply some of these techniques to the Ex-MORA sample to understand how this population may or may not be included in such studies.

We first apply the radio $+$ OIR-dark selection technique defined in (cite: Gentile2024). This selection technique requires that galaxies have 3 GHz flux densities $>12.65\,\mu$Jy and do not have a detection in COSMOS2020 (cite: Weaver2022); the reddest band used for source detection in COSMOS2020 is the UltraVISTA $K_s$ filter ($\lambda \sim 2.2$ $\mu$m) with a 3$\sigma$ limiting depth at m$_\mathrm{AB} \sim 25.5$. We find that $22/36$ ($\sim60\%$) sources have sufficiently bright 3 GHz emission ($>12.65$ $\mu$Jy) to pass the first selection criterion, though three sources are known AGN and thus should be removed from this sample. Out of the remaining 19 Ex-MORA galaxies, only three sources are sufficiently faint to have no counterpart in the COSMOS2020 catalog. If we instead use the $F277W$ band as a proxy for the $K_s$-band (with thee 3$\sigma$ magnitude limit mentioned above), we only recover one source with the other two becoming slightly too bright to be captured.

We next apply the OIR-dark selection technique defined in (cite: Wang2019) but updated using JWST NIRCam filters (cite: Barrufet2023; Gottumukkala2024). The OIR-dark selection technique, when used with JWST bands, requires F150W$-$F444W  $> 2.1$ and a faint or non-detection in the F150W band ($m_{F150W} > 25$). We find that a little under half ($n=14/33$) of Ex-MORA sources would be captured with this technique. Of the sources not captured: most have sufficiently red F150W$-$F444W colors to meet the first criterion (F150W$-$F444W $> 2.1$), but their F150W magnitudes are too bright ($< 25$ mag). We note that *all* of the sources captured by this technique are undetected in the F150W band; given the observational depths of the F150W band in the COSMOS-Web survey (cite: cosmos-web), it is likely that that these sources are truly “dark”. Sources without $F150W$ detections have an average redshift of $z\sim 4.4$, while those with $F150W$ detections sit near $z\sim 3.3$ (though these averages are at the edge of 1$\sigma$ uncertainty of one another).

Combined, it seems that these opt/NIR and radio selection techniques capture roughly $10-40$% of all 2 mm-bright sources, supporting the idea that the heavily dust obscured population is quite heterogeneous. The population densities derived using these methods are similar to our estimates when considering all Ex-MORA sources at $z>3$ (cite: Talia2021; Xiao2023), yet there is little to no overlap between sources identified via these three methods. This is particularly troubling as it implies that up to two-thirds of the $z>3$ dusty galaxy population is missed when using only one of these selection techniques (cite: Algera2023; Zimmerman2024). If confirmed, the consequences of such biases are wide-sweeping, affecting theories and estimates on early and rapid metal enrichment of the ISM, the dust-obscured component of the cosmic star formation rate density, and early massive quiescent galaxy progenitor populations. This also implies that compiling the most complete samples of dusty, star forming galaxies at high-$z$ requires a combination of observations across several energy regimes, further solidifying how synergies between major observing facilities such as JWST and ALMA are critical to this aim.

# Summary & Conclusions

We have presented the Ex-MORA Survey, the largest ALMA blank-field map covering 577 arcmin$^2$ at 2 mm. This work is an expansion on the original MORA survey presented in and . We detect 37 sources above $5\sigma$ significance, one of which is likely a false-positive, and three of which likely have 2 mm fluxes boosted significantly by synchrotron emission, leaving a total of 33 robust detections from predominantly thermal dust emission. All bona fide sources are detected at minimum in the NIRCam $F444W$ band.

Through a combination of spectroscopic and photometric redshifts spanning $z\sim2-6$, we estimate a median redshift of $\langle z \rangle  = 3.6^{+0.1}_{-0.2}$. Two-thirds of the sample are estimated at $z>3$, and just under half of the sample is estimated at $z>4$. We estimate the volume density of Ex-MORA sources and measure a decrease in the population from $z\sim4$ to $z\sim7$, with an integrated volume density of $\sim1-3\times10^{-5}$ Mpc$^{-3}$ at $z>3$. In upcoming work, we will present the physical properties of individual Ex-MORA sources and explore them in the context of galaxy evolution paradigms.

While the Ex-MORA survey is successful at identifying a strong sample of primarily $z>3$ IR luminous galaxies, the results are still consistent with the ‘dust poor’ early Universe model presented in (cite: Casey2018a). At face value, this implies that searches for high-$z$ heavily dust-obscured galaxies will become more difficult with increasing redshift as these sources are incredibly rare (cite: Zavala2018Nature; Marrone2018; Akins2023; Hygate2023). In this work, we find that other techniques developed to discover $z>3$ dusty galaxies (cite: Wang2019; Talia2021; Barrufet2023; Gottumukkala2024) capture as much as 40% and as little as 10% of the Ex-MORA galaxy sample. These findings support the idea that multiple modes of selection across multiple wavelengths and energy regimes are necessary for a complete census of the high-$z$ dusty galaxy population, and that synergistic efforts with observatories such as JWST, ALMA, and the VLA will continue to be critical to these efforts.

# Acknowledgements

We honor the invaluable labor of the maintenance and clerical staff at our institutions, whose contributions make our scientific discoveries a reality. This work was developed and written in central Texas on the lands of the Tonkawa, Comanche, and Apache people. Learn more about the history and present life of Austin’s Indigeous peoples at <https://www.kut.org/texas/2022-03-31/where-have-austins-indigenous-people-gone>.

ASL thanks Charlie and Patrick Long for the love, support, and precious moments baking in the sun together. ASL would also like to thank the good people at NRAO Charlottesville for their help in staging and reducing this data, for sharing remote computing resources, for the ALMA Ambassador Program, and for the Visitor Support Program. Specifically, thank you to G. Privon, S. Wood, and L. Barcos-Munoz. ASL would also like to thank the LUMA, VanguardSTEM, Black in Astro, and AAS CSMA organizations for providing community and support, with special thanks to A. Harriot, G. Ezeka, M. Sgouros, K. Klass, R. McNair, L. Valencia, A. Walker, N. Cabrera Salazar, and J. Gonzalez Quiles.

ASL and SMM acknowledge support for this work provided by NASA through the NASA Hubble Fellowship Program grant #HST-HF2-51511 and #HST-HF2-51484, awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. JH acknowledges support from the ERC Consolidator Grant 101088676 (“VOYAJ”). JAZ acknowledges funding from JSPS KAKENHI grant number KG23K13150. FG acknowledges the support from grant PRIN MIUR 2017-20173ML3WW_001 ‘Opening the ALMA window on the cosmic evolution of gas, stars, and supermassive black holes.’ ET acknowledges support from ANID Basal program FB210003 (CATA) and FONDECYT Regular 1190818 and 1200495. JBC acknowledges funding from the JWST Arizona/Steward Postdoc in Early galaxies and Reionization (JASPER) Scholar contract at the University of Arizona. AWSM acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC) through grant reference number RGPIN-2021-03046. MA acknowledges support from the ANID BASAL project FB210003

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based \[in part\] on observations made with the NASA/ESA/CSA JWST. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program JWST #1727 and #1837. Some of the data presented in this paper are available on the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations can be accessed via doi:10.17909/qhb4-fy92 and doi:10.17909/T94S3X. This work made use of Astropy:[^3] a community-developed core Python package and an ecosystem of tools and resources for astronomy (cite: astropy:2013; astropy:2018; astropy:2022).

natexlab

(ref: Aihara2022) Aihara, H., AlSayyad, Y., Ando, M., et al. 2022, PASJ, 74, 247, doi: [`10.1093/pasj/psab122`](http://doi.org/10.1093/pasj/psab122)

(ref: Akins2023) Akins, H. B., Casey, C. M., Allen, N., et al. 2023, ApJ, 956, 61, doi: [`10.3847/1538-4357/acef21`](http://doi.org/10.3847/1538-4357/acef21)

(ref: Algera2023) Algera, H. S. B., Inami, H., Oesch, P. A., et al. 2023, MNRAS, 518, 6142, doi: [`10.1093/mnras/stac3195`](http://doi.org/10.1093/mnras/stac3195)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bagley2023) Bagley, M. B., Finkelstein, S. L., Koekemoer, A. M., et al. 2023, ApJL, 946, L12, doi: [`10.3847/2041-8213/acbb08`](http://doi.org/10.3847/2041-8213/acbb08)

(ref: Barrufet2023) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449, doi: [`10.1093/mnras/stad947`](http://doi.org/10.1093/mnras/stad947)

(ref: Bassini2023) Bassini, L., Feldmann, R., Gensior, J., et al. 2023, MNRAS, 525, 5388, doi: [`10.1093/mnras/stad2617`](http://doi.org/10.1093/mnras/stad2617)

(ref: setractor) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: Bethermin2017) Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89, doi: [`10.1051/0004-6361/201730866`](http://doi.org/10.1051/0004-6361/201730866)

(ref: Bing2023) Bing, L., Béthermin, M., Lagache, G., et al. 2023, A&A, 677, A66, doi: [`10.1051/0004-6361/202346579`](http://doi.org/10.1051/0004-6361/202346579)

(ref: Birkin2023) Birkin, J. E., Hutchison, T. A., Welch, B., et al. 2023, ApJ, 958, 64, doi: [`10.3847/1538-4357/acf712`](http://doi.org/10.3847/1538-4357/acf712)

(ref: Blain2002) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: Bowler2017) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2017, MNRAS, 466, 3612, doi: [`10.1093/mnras/stw3296`](http://doi.org/10.1093/mnras/stw3296)

(ref: photutils) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2023, astropy/photutils: 1.8.0, 1.8.0, Zenodo, doi: [`10.5281/zenodo.7946442`](http://doi.org/10.5281/zenodo.7946442)

(ref: Brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503, doi: [`10.1086/591786`](http://doi.org/10.1086/591786)

(ref: Burnham2021) Burnham, A. D., Casey, C. M., Zavala, J. A., et al. 2021, ApJ, 910, 89, doi: [`10.3847/1538-4357/abe401`](http://doi.org/10.3847/1538-4357/abe401)

(ref: Bushouse2023) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2023, JWST Calibration Pipeline, 1.12.1, Zenodo, doi: [`10.5281/zenodo.8380331`](http://doi.org/10.5281/zenodo.8380331)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Capak2007) Capak, P., Aussel, H., Ajiki, M., et al. 2007, ApJS, 172, 99, doi: [`10.1086/519081`](http://doi.org/10.1086/519081)

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: casey16) Casey, C. M. 2016, ApJ, 824, 36, doi: [`10.3847/0004-637X/824/1/36`](http://doi.org/10.3847/0004-637X/824/1/36)

(ref: Casey2020) —. 2020, ApJ, 900, 68, doi: [`10.3847/1538-4357/aba528`](http://doi.org/10.3847/1538-4357/aba528)

(ref: Casey2018a) Casey, C. M., Hodge, J., Zavala, J. A., et al. 2018a, ApJ, 862, 78, doi: [`10.3847/1538-4357/aacd11`](http://doi.org/10.3847/1538-4357/aacd11)

(ref: casey2014dusty) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Physics Reports, 541, 45

(ref: Casey2018b) Casey, C. M., Zavala, J. A., Spilker, J., et al. 2018b, ApJ, 862, 77, doi: [`10.3847/1538-4357/aac82d`](http://doi.org/10.3847/1538-4357/aac82d)

(ref: Casey2019) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55, doi: [`10.3847/1538-4357/ab52ff`](http://doi.org/10.3847/1538-4357/ab52ff)

(ref: Casey2021) Casey, C. M., Zavala, J. A., Manning, S. M., et al. 2021, ApJ, 923, 215, doi: [`10.3847/1538-4357/ac2eb4`](http://doi.org/10.3847/1538-4357/ac2eb4)

(ref: cosmos-web) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31, doi: [`10.3847/1538-4357/acc2bc`](http://doi.org/10.3847/1538-4357/acc2bc)

(ref: chabrier) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chen2022) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159, doi: [`10.3847/1538-4357/ac61df`](http://doi.org/10.3847/1538-4357/ac61df)

(ref: Civano2016) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62, doi: [`10.3847/0004-637X/819/1/62`](http://doi.org/10.3847/0004-637X/819/1/62)

(ref: Cooper2022) Cooper, O. R., Casey, C. M., Zavala, J. A., et al. 2022, ApJ, 930, 32, doi: [`10.3847/1538-4357/ac616d`](http://doi.org/10.3847/1538-4357/ac616d)

(ref: Cowie2023) Cowie, L. L., Barger, A. J., & Bauer, F. E. 2023, ApJ, 952, 28, doi: [`10.3847/1538-4357/acd763`](http://doi.org/10.3847/1538-4357/acd763)

(ref: Enia2022) Enia, A., Talia, M., Pozzi, F., et al. 2022, ApJ, 927, 204, doi: [`10.3847/1538-4357/ac51ca`](http://doi.org/10.3847/1538-4357/ac51ca)

(ref: EuclidCollaboration2022) Euclid Collaboration, Moneti, A., McCracken, H. J., et al. 2022, A&A, 658, A126, doi: [`10.1051/0004-6361/202142361`](http://doi.org/10.1051/0004-6361/202142361)

(ref: fudamoto20) Fudamoto, Y., Oesch, P. A., Magnelli, B., et al. 2020, MNRAS, 491, 4724, doi: [`10.1093/mnras/stz3248`](http://doi.org/10.1093/mnras/stz3248)

(ref: Gentile2024) Gentile, F., Talia, M., Behiri, M., et al. 2024a, ApJ, 962, 26, doi: [`10.3847/1538-4357/ad1519`](http://doi.org/10.3847/1538-4357/ad1519)

(ref: Gentile2024b) Gentile, F., Talia, M., Daddi, E., et al. 2024b, arXiv e-prints, arXiv:2402.05994, doi: [`10.48550/arXiv.2402.05994`](http://doi.org/10.48550/arXiv.2402.05994)

(ref: Gillman2023) Gillman, S., Gullberg, B., Brammer, G., et al. 2023, A&A, 676, A26, doi: [`10.1051/0004-6361/202346531`](http://doi.org/10.1051/0004-6361/202346531)

(ref: Gottumukkala2024) Gottumukkala, R., Barrufet, L., Oesch, P. A., et al. 2024, MNRAS, doi: [`10.1093/mnras/stae754`](http://doi.org/10.1093/mnras/stae754)

(ref: Hasinger2018) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77, doi: [`10.3847/1538-4357/aabacf`](http://doi.org/10.3847/1538-4357/aabacf)

(ref: Hayward2021) Hayward, C. C., Sparre, M., Chapman, S. C., et al. 2021, MNRAS, 502, 2922, doi: [`10.1093/mnras/stab246`](http://doi.org/10.1093/mnras/stab246)

(ref: Heintz2022) Heintz, E., & Zweibel, E. G. 2022, ApJ, 941, 78, doi: [`10.3847/1538-4357/ac9e9e`](http://doi.org/10.3847/1538-4357/ac9e9e)

(ref: Herard-Demanche2023) Herard-Demanche, T., Bouwens, R. J., Oesch, P. A., et al. 2023, arXiv e-prints, arXiv:2309.04525, doi: [`10.48550/arXiv.2309.04525`](http://doi.org/10.48550/arXiv.2309.04525)

(ref: Heywood2022) Heywood, I., Jarvis, M. J., Hale, C. L., et al. 2022, MNRAS, 509, 2150, doi: [`10.1093/mnras/stab3021`](http://doi.org/10.1093/mnras/stab3021)

(ref: hickox2012) Hickox, R. C., Wardlow, J. L., Smail, I., et al. 2012, MNRAS, 421, 284, doi: [`10.1111/j.1365-2966.2011.20303.x`](http://doi.org/10.1111/j.1365-2966.2011.20303.x)

(ref: hodgeanddacunha) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: hodge16) Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, ApJ, 833, 103, doi: [`10.3847/1538-4357/833/1/103`](http://doi.org/10.3847/1538-4357/833/1/103)

(ref: Hygate2023) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775, doi: [`10.1093/mnras/stad1212`](http://doi.org/10.1093/mnras/stad1212)

(ref: Jimenez-Andrade2020) Jiménez-Andrade, E. F., Zavala, J. A., Magnelli, B., et al. 2020, ApJ, 890, 171, doi: [`10.3847/1538-4357/ab6dec`](http://doi.org/10.3847/1538-4357/ab6dec)

(ref: Jin2019) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144, doi: [`10.3847/1538-4357/ab55d6`](http://doi.org/10.3847/1538-4357/ab55d6)

(ref: Jin2024) Jin, S., Sillassen, N. B., Hodge, J., et al. 2024, arXiv e-prints, arXiv:2407.07585, doi: [`10.48550/arXiv.2407.07585`](http://doi.org/10.48550/arXiv.2407.07585)

(ref: Koekemoer2007) Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196, doi: [`10.1086/520086`](http://doi.org/10.1086/520086)

(ref: Kriek2015) Kriek, M., Shapley, A. E., Reddy, N. A., et al. 2015, ApJS, 218, 15, doi: [`10.1088/0067-0049/218/2/15`](http://doi.org/10.1088/0067-0049/218/2/15)

(ref: Lagos2020) Lagos, C. d. P., da Cunha, E., Robotham, A. S. G., et al. 2020, MNRAS, 499, 1948, doi: [`10.1093/mnras/staa2861`](http://doi.org/10.1093/mnras/staa2861)

(ref: Leja2019) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3, doi: [`10.3847/1538-4357/ab133c`](http://doi.org/10.3847/1538-4357/ab133c)

(ref: lewis18) Lewis, A. J. R., Ivison, R. J., Best, P. N., et al. 2018, ApJ, 862, 96, doi: [`10.3847/1538-4357/aacc25`](http://doi.org/10.3847/1538-4357/aacc25)

(ref: Lilly2007) Lilly, S. J., Le Fèvre, O., Renzini, A., et al. 2007, ApJS, 172, 70, doi: [`10.1086/516589`](http://doi.org/10.1086/516589)

(ref: Lim2021) Lim, S., Scott, D., Babul, A., et al. 2021, MNRAS, 501, 1803, doi: [`10.1093/mnras/staa3693`](http://doi.org/10.1093/mnras/staa3693)

(ref: Liu2018) Liu, F. S., Jia, M., Yesuf, H. M., et al. 2018, ApJ, 860, 60, doi: [`10.3847/1538-4357/aac20d`](http://doi.org/10.3847/1538-4357/aac20d)

(ref: Long2023) Long, A. S., Casey, C. M., del P. Lagos, C., et al. 2023, ApJ, 953, 11, doi: [`10.3847/1538-4357/acddde`](http://doi.org/10.3847/1538-4357/acddde)

(ref: Long2020) Long, A. S., Cooray, A., Ma, J., et al. 2020, ApJ, 898, 133, doi: [`10.3847/1538-4357/ab9d1f`](http://doi.org/10.3847/1538-4357/ab9d1f)

(ref: Long2024) Long, A. S., Antwi-Danso, J., Lambrides, E. L., et al. 2024, ApJ, 970, 68, doi: [`10.3847/1538-4357/ad4cea`](http://doi.org/10.3847/1538-4357/ad4cea)

(ref: madau14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magnelli2019) Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877, 45, doi: [`10.3847/1538-4357/ab1912`](http://doi.org/10.3847/1538-4357/ab1912)

(ref: Manning2022) Manning, S. M., Casey, C. M., Zavala, J. A., et al. 2022, ApJ, 925, 23, doi: [`10.3847/1538-4357/ac366a`](http://doi.org/10.3847/1538-4357/ac366a)

(ref: Marrone2018) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51, doi: [`10.1038/nature24629`](http://doi.org/10.1038/nature24629)

(ref: Marsan2017) Marsan, Z. C., Marchesini, D., Brammer, G. B., et al. 2017, ApJ, 842, 21, doi: [`10.3847/1538-4357/aa7206`](http://doi.org/10.3847/1538-4357/aa7206)

(ref: McCracken2012) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: McKinney2023b) McKinney, J., Manning, S. M., Cooper, O. R., et al. 2023, ApJ, 956, 72, doi: [`10.3847/1538-4357/acf614`](http://doi.org/10.3847/1538-4357/acf614)

(ref: michalowski17) Michałowski, M. J., Dunlop, J. S., Koprowski, M. P., et al. 2017, MNRAS, 469, 492, doi: [`10.1093/mnras/stx861`](http://doi.org/10.1093/mnras/stx861)

(ref: Moster2011) Moster, B. P., Somerville, R. S., Newman, J. A., & Rix, H.-W. 2011, ApJ, 731, 113, doi: [`10.1088/0004-637X/731/2/113`](http://doi.org/10.1088/0004-637X/731/2/113)

(ref: Nanayakkara2016) Nanayakkara, T., Glazebrook, K., Kacprzak, G. G., et al. 2016, ApJ, 828, 21, doi: [`10.3847/0004-637X/828/1/21`](http://doi.org/10.3847/0004-637X/828/1/21)

(ref: oliver2012herschel) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614, doi: [`10.1111/j.1365-2966.2012.20912.x`](http://doi.org/10.1111/j.1365-2966.2012.20912.x)

(ref: PlanckCollaboration2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Reuter2020) Reuter, C., Vieira, J. D., Spilker, J. S., et al. 2020, ApJ, 902, 78, doi: [`10.3847/1538-4357/abb599`](http://doi.org/10.3847/1538-4357/abb599)

(ref: Scoville2007) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1, doi: [`10.1086/516585`](http://doi.org/10.1086/516585)

(ref: Shen2022) Shen, X., Vogelsberger, M., Nelson, D., et al. 2022, MNRAS, 510, 5560, doi: [`10.1093/mnras/stab3794`](http://doi.org/10.1093/mnras/stab3794)

(ref: Simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43, doi: [`10.3847/1538-4357/ab23ff`](http://doi.org/10.3847/1538-4357/ab23ff)

(ref: Smail1997) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1, doi: [`10.1051/0004-6361/201628704`](http://doi.org/10.1051/0004-6361/201628704)

(ref: Staguhn2014) Staguhn, J. G., Kovács, A., Arendt, R. G., et al. 2014, ApJ, 790, 77, doi: [`10.1088/0004-637X/790/1/77`](http://doi.org/10.1088/0004-637X/790/1/77)

(ref: Stott2016) Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888, doi: [`10.1093/mnras/stw129`](http://doi.org/10.1093/mnras/stw129)

(ref: Talia2021) Talia, M., Cimatti, A., Giulietti, M., et al. 2021, ApJ, 909, 23, doi: [`10.3847/1538-4357/abd6e3`](http://doi.org/10.3847/1538-4357/abd6e3)

(ref: toft14) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68, doi: [`10.1088/0004-637X/782/2/68`](http://doi.org/10.1088/0004-637X/782/2/68)

(ref: Trump2007) Trump, J. R., Impey, C. D., McCarthy, P. J., et al. 2007, ApJS, 172, 383, doi: [`10.1086/516578`](http://doi.org/10.1086/516578)

(ref: Valentino2020) Valentino, F., Tanaka, M., Davidzon, I., et al. 2020, ApJ, 889, 93, doi: [`10.3847/1538-4357/ab64dc`](http://doi.org/10.3847/1538-4357/ab64dc)

(ref: Valentino2023) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, arXiv e-prints, arXiv:2302.10936, doi: [`10.48550/arXiv.2302.10936`](http://doi.org/10.48550/arXiv.2302.10936)

(ref: vanderVlugt2023) van der Vlugt, D., Hodge, J. A., Jin, S., et al. 2023, ApJ, 951, 131, doi: [`10.3847/1538-4357/acd549`](http://doi.org/10.3847/1538-4357/acd549)

(ref: walter12) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233, doi: [`10.1038/nature11073`](http://doi.org/10.1038/nature11073)

(ref: Wang2019) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211, doi: [`10.1038/s41586-019-1452-4`](http://doi.org/10.1038/s41586-019-1452-4)

(ref: Weaver2022) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11, doi: [`10.3847/1538-4365/ac3078`](http://doi.org/10.3847/1538-4365/ac3078)

(ref: Weaver2024) Weaver, J. R., Cutler, S. E., Pan, R., et al. 2024, ApJS, 270, 7, doi: [`10.3847/1538-4365/ad07e0`](http://doi.org/10.3847/1538-4365/ad07e0)

(ref: Williams2019) Williams, C. C., Labbe, I., Spilker, J., et al. 2019, ApJ, 884, 154, doi: [`10.3847/1538-4357/ab44aa`](http://doi.org/10.3847/1538-4357/ab44aa)

(ref: Wisnioski2019) Wisnioski, E., Förster Schreiber, N. M., Fossati, M., et al. 2019, ApJ, 886, 124, doi: [`10.3847/1538-4357/ab4db8`](http://doi.org/10.3847/1538-4357/ab4db8)

(ref: Xiao2023b) Xiao, M., Oesch, P., Elbaz, D., et al. 2023a, arXiv e-prints, arXiv:2309.02492, doi: [`10.48550/arXiv.2309.02492`](http://doi.org/10.48550/arXiv.2309.02492)

(ref: Xiao2023) Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023b, A&A, 672, A18, doi: [`10.1051/0004-6361/202245100`](http://doi.org/10.1051/0004-6361/202245100)

(ref: Yun2015) Yun, M. S., Aretxaga, I., Gurwell, M. A., et al. 2015, MNRAS, 454, 3485, doi: [`10.1093/mnras/stv1963`](http://doi.org/10.1093/mnras/stv1963)

(ref: zavala18) Zavala, J. A., Casey, C. M., da Cunha, E., et al. 2018a, ApJ, 869, 71, doi: [`10.3847/1538-4357/aaecd2`](http://doi.org/10.3847/1538-4357/aaecd2)

(ref: Zavala2018Nature) Zavala, J. A., Montaña, A., Hughes, D. H., et al. 2018b, Nature Astronomy, 2, 56, doi: [`10.1038/s41550-017-0297-8`](http://doi.org/10.1038/s41550-017-0297-8)

(ref: Zavala2021) Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165, doi: [`10.3847/1538-4357/abdb27`](http://doi.org/10.3847/1538-4357/abdb27)

(ref: Zimmerman2024) Zimmerman, D. T., Narayanan, D., Whitaker, K. E., & Davè, R. 2024, arXiv e-prints, arXiv:2401.06719, doi: [`10.48550/arXiv.2401.06719`](http://doi.org/10.48550/arXiv.2401.06719)

# Individual Source Redshift Solutions

## Approaching Degenerate Source Spectroscopic Redshifts

A handful of Ex-MORA sources have spectroscopic redshifts generated from a single CO emission line. Without a second line detection (from e.g. a higher or lower $J-$transition, \[C I\] or \[C II\]), interpretation of the corresponding spectroscopic redshift is degenerate across discrete redshift values (cite: Jin2024). We discuss the handful of sources for which this degeneracy is possible, and how we decided which redshift to report.

For two objects (eMORA.7 and eMORA.12), the detected line is attributed to a CO (3-2) transition line, placing these sources at $z \sim 2.31$ and 2.26, respectively. However, given the spectral coverage of the observations (ALMA band 3 only, PID:2019.1.01600.S and 2021.1.00246.S), it is possible to have a single line detection also at CO (4-3), which would place these objects instead at $z \sim 3.34$ and 3.41, respectively. Indeed, the photometric redshifts developed in this work support a $z>3$ solution for both of these sources, and agrees with the CO(4-3) redshift within 1$\sigma$ uncertainty and $\int_{3}^{\infty}$ p(z) $>85\%$. Thus, for these two sources, we adopt the $z\sim3.4$ solutions in this work.

Another source (eMORA.24) is similar to the above two sources (a single detection reported as CO(3-2) and a corresponding $z<3$ redshift estimate in Chen et al. (in prep)), however the photo-$z$ estimates strongly agree with the predicted spectroscopic redshift at $z=2.411$ within 1$\sigma$ (and $\int_{3}^{\infty}$ p(z) $<5\%$). For this source, we adopt the reported spectroscopic redshift of 2.411.

Finally, one source (eMORA.4) has a single line detection attributed to CO(4-3) with a corresponding redshift of $z=3.254$. The estimated photo-$z$ from this work is high, at $z\sim7.6$. If true, this would require a CO(8-7) emission line *and* have a much higher likelihood of detecting multiple $J$-transition lines because (a) the distance between rest-frame wavelengths of CO emission lines becomes smaller with increasing $J$-transitions; and (b) emission line brightness increases with increasing $J$-transitions. Thus, we reject the high-$z$ photometrically-derived solution and adopt its redshift as $z=3.254$.

## Photometric Redshifts Solutions for Unique Sources

Three sources (eMORA.6, eMORA.20, and eMORA.28) are estimated to live at $z\sim1.5$, according to the BAGPIPES fit. If true, this would make these sources near HyLIRGS (L$_\mathrm{IR} \sim 10^{13}$ M$_\odot$) and therefore significantly detected in *Herschel* SPIRE bands, with $S_\mathrm{850\,\mu m} \gtrsim 50$ mJy (cite: casey2014dusty). All three sources are not detected above 1$\sigma$ significance in the existing *Herschel* maps (cite: oliver2012herschel), and therefore we reject these solutions. For eMORA.6 and eMORA.28, we adopt the estimate reported in the COSMOS2020 catalog, which sits at $z>3$ for both sources. eMORA.20 was not captured in the original COSMOS2020 catalog as it is faint / invisible at $\lambda_\mathrm{obs} < 2$ $\mu$m (though still visible in the K$_s$-band). Therefore it does not have a redshift estimate in COSMOS2020. For this source, we instead run the CIGALE energy-balance SED and photo-$z$ fitting software with a parameterization following (cite: Long2024) and find a solution of $z_\mathrm{phot}\sim5.5$.

Finally, three sources are estimated at $z\sim7$ according to their BAGPIPES fits (eMORA.21, eMORA.23, and eMORA.32). However, upon inspection, two of these sources (eMORA.21 and eMORA.32) have large effective radii in their $F444W$ images ($r_e \sim 1-2''$). This would correspond to physical sizes on the order of $\sim5-11$ kpc at $z\sim7$, which is significantly larger ($2-10\times$) than the measured sizes of star forming galaxies at such early epochs (cite: Bowler2017), and more in agreement with the sizes of dusty galaxies around Cosmic Noon (cite: Burnham2021). BAGPIPES completely failed to fit eMORA.23, despite outputting a redshift estimate and corresponding galaxy properties. For all three sources, we adopt the estimates reported in the COSMOS2020 catalog, which sit at $z>2$.

[^1]: The extracted flux density for this source from the Ex-MORA map is well within uncertainty of the previous measurement (original $S_\mathrm{2\,mm} = 356\pm69\,\mu$Jy vs. new $S_\mathrm{2\,mm} = 334\pm68\,\mu$Jy), and therefore the discrepancy is not likely an issue with the data reduction and measurement process, but instead likely due to boosting from a coincident noise fluctuation.

[^2]: We note that, while uses MORA number counts to generate their predictions, the combination of other wavelengths and the methods employed therein make their predictions independent from those derived from direct source characterization, as done in this work. See for more details.

[^3]: http://www.astropy.org

</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1.68'' x 1.44''",
  "failed_quote": "The combined mosaic has a typical synthesized beam size of $\\theta_\\mathrm{FWHM} \\approx 1.68\\ensuremath{''} \\times 1.44\\ensuremath{''}$, which is similar to the average beam sizes across individual SBs (see Table [table:obs])."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "1.68'' x 1.44''",
  "failed_quote": "The combined mosaic has a typical synthesized beam size of $\\theta_\\mathrm{FWHM} \\approx 1.68\\ensuremath{''} \\times 1.44\\ensuremath{''}$, which is similar to the average beam sizes across individual SBs (see Table [table:obs])."
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "Observed-frame 2 mm observations leverage a very negative K-correction to efficiently detect z > 3 DSFGs while filtering out the more numerous z < 3 DSFG population; overlapping with the COSMOS-Web JWST field provides deep NIRCam imaging to identify counterparts.",
  "failed_quote": "Requesting at only the one 147 GHz tuning in order to reduce overheads and to enable efficient mosaicking with original MORA survey."
 }
]
```
