# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...892..148S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Dynamical Equilibrium in the Molecular ISM in 28 Nearby Star-Forming Galaxies

## Abstract

We compare the observed turbulent pressure in molecular gas, $P_\mathrm{turb}$, to the required pressure for the interstellar gas to stay in equilibrium in the gravitational potential of a galaxy, $P_\mathrm{DE}$. To do this, we combine arcsecond resolution CO data from PHANGS-ALMA with multi-wavelength data that traces the atomic gas, stellar structure, and star formation rate (SFR) for 28 nearby star-forming galaxies. We find that $P_\mathrm{turb}$ correlates with, but almost always exceeds the estimated $P_\mathrm{DE}$ on kiloparsec scales. This indicates that the molecular gas is over-pressurized relative to the large-scale environment. We show that this over-pressurization can be explained by the clumpy nature of molecular gas; a revised estimate of $P_\mathrm{DE}$ on cloud scales, which accounts for molecular gas self-gravity, external gravity, and ambient pressure, agrees well with the observed $P_\mathrm{turb}$ in galaxy disks. We also find that molecular gas with cloud-scale ${P_\mathrm{turb}}\approx{P_\mathrm{DE}}\gtrsim{10^5\,k_\mathrm{B}\,\mathrm{K\,cm^{-3}}}$ in our sample is more likely to be self-gravitating, whereas gas at lower pressure appears more influenced by ambient pressure and/or external gravity. Furthermore, we show that the ratio between $P_\mathrm{turb}$ and the observed SFR surface density, $\Sigma_\mathrm{SFR}$, is compatible with stellar feedback-driven momentum injection in most cases, while a subset of the regions may show evidence of turbulence driven by additional sources. The correlation between $\Sigma_\mathrm{SFR}$ and kpc-scale $P_\mathrm{DE}$ in galaxy disks is consistent with the expectation from self-regulated star formation models. Finally, we confirm the empirical correlation between molecular-to-atomic gas ratio and kpc-scale $P_\mathrm{DE}$ reported in previous works.

# Introduction

Molecular clouds host a significant fraction of the molecular gas mass in the interstellar medium (ISM), and all star formation activity in galaxies. Understanding how the properties of molecular clouds change in response to the galactic environment is crucial for building a successful theory for star formation.

Early studies of giant molecular clouds (GMCs) in the Milky Way conjectured that they had “universal” properties, in the sense that all GMCs exist at the same surface density and follow the same size–linewidth scaling relation (cite: Larson_1981; Solomon_etal_1987). (cite: Bolatto_etal_2008) also reached a similar conclusion after studying a sample of GMCs in some of the nearest galaxies. However, subsequent observational studies have instead suggested that cloud properties may change systematically as a function of environment. In a careful re-analysis of the (cite: Solomon_etal_1987) Milky Way clouds, (cite: Heyer_etal_2009) demonstrated that Milky Way GMCs vary systematically in their surface density and size–linewidth parameter. This finding has been confirmed by more recent works analyzing GMCs in the Milky Way (cite: Rice_etal_2016; Miville-Deschenes_etal_2017; Colombo_etal_2019). Based on observations from the PdBI Arcsecond Whirlpool Survey (cite: Pety_etal_2013; Schinnerer_etal_2013), (cite: Hughes_etal_2013a), (cite: Hughes_etal_2013b), and (cite: Colombo_etal_2014a) showed strong variations in GMC properties within the inner $\sim4$ kpc of M51 and among M51, M33, and the Large Magellanic Cloud (LMC). Similar results were found by subsequent works studying GMCs in various types of galaxies in the local universe (cite: DonovanMeyer_etal_2013; Leroy_etal_2015; Rebolledo_etal_2015; Utomo_etal_2015; Freeman_etal_2017; Egusa_etal_2018; Hirota_etal_2018; Schruba_etal_2019).

In a comprehensive work studying molecular gas properties with uniform treatment across 15 nearby galaxies, (cite: Sun_etal_2018) showed that the cloud-scale surface density and velocity dispersion of molecular gas vary systematically both within and among galaxies. The correlation of these two quantities implies a narrow range of virial parameter and a wide spread in the internal turbulent pressure in molecular gas. Quantitatively, (cite: Sun_etal_2018) found the cloud-scale turbulent pressure of molecular gas to span $\sim 4{-}5$ orders of magnitude. An important next step for the field is to understand the physics that drive the changes in the turbulent gas pressure in different galactic environments.

One promising scenario is that the mean pressure in the ISM sets the internal pressure in molecular clouds. This idea has been considered in various forms to explain observed molecular cloud properties since early CO studies (cite: Keto_Myers_1986; Elmegreen_1989; Bertoldi_McKee_1992; Heyer_etal_2001; Oka_etal_2001; Rosolowsky_Blitz_2005). More recently, following the observations of (cite: Heyer_etal_2009), (cite: Field_etal_2011) presented a simple model for how the observed variations in the line width and surface density could be linked to pressure in the ambient medium. The work of (cite: Heyer_etal_2009) and (cite: Field_etal_2011) led to widespread appreciation of the potential role of external pressure and adoption of the size–linewidth–surface density parameter space as a crucial diagnostic of the link between molecular clouds and environment (cite: Hughes_etal_2013a; Johnson_etal_2015; Leroy_etal_2015; Utomo_etal_2015). The (cite: Field_etal_2011) formalism to consider clouds interacting with external pressure has also been revisited by subsequent works (cite: Meidt_2016; Schruba_etal_2019), and further generalized to include the effect of the external, galactic gravitational potential and in-plane gas motions (cite: Meidt_etal_2018; Meidt_etal_2019).

Expanding on the work of (cite: Field_etal_2011), (cite: Hughes_etal_2013a) estimated the ambient pressure in the ISM based on hydrostatic equilibrium, and made a synthetic, direct comparison of cloud internal pressure to the ambient pressure for GMCs in M51, M33, and the LMC. They observed a significant correlation between internal pressure and external pressure. Based on this finding, (cite: Hughes_etal_2013a) proposed that one can use the ambient pressure to predict the internal pressure in GMCs. This hypothesis is appealing because it allows one to predict GMC properties based on the large-scale mass distribution in a galaxy, which is readily available from low resolution observations or numerical simulations.

The (cite: Hughes_etal_2013a) hypothesis implies a deep connection between the properties of GMCs and the galaxy disks that they inhabit. In any long-lived, stable galaxy disk, we expect the mean pressure in the ISM to be set by the weight of the ISM in the galaxy’s gravitational potential (cite: Elmegreen_1989). If the internal pressure of GMCs is in turn set by this mean ISM pressure, then GMC properties result directly from the large-scale properties of the galaxy disk.

A natural next step to understand what sets molecular cloud properties is to compare GMC turbulent pressure to the mean ISM pressure across a range of galactic environments. If the results of (cite: Hughes_etal_2013a) apply generally, then the mean ISM pressure, which can be estimated from the large-scale disk structure, can be used to predict the properties of the local GMC population.

Furthermore, if the picture of (cite: Field_etal_2011) and related works holds, then individual GMCs exist in a state of balance between internal pressure, ambient pressure, self-gravity, and external potential. In this case, a version of dynamical equilibrium is reached – at least in a population-averaged sense – on cloud scales. In a recent observational study, (cite: Schruba_etal_2019) have shown that GMCs in the Milky Way and seven nearby galaxies indeed appear to achieve this equilibrium state when averaged over the population.

We seek to investigate whether the observed turbulent pressure in the molecular ISM can be explained by dynamical equilibrium considerations across multiple spatial scales, and to understand the interplay between internal pressure, ambient pressure, self-gravity, and the external potential in the molecular ISM in a wide range of galactic environments. Carrying out these cloud-scale tests requires a) sampling diverse environments across a well-selected and homogeneously observed galaxy sample, b) achieving sufficient angular resolution to reach cloud scales ($\lesssim$100 pc), and c) having the rich supporting multi-wavelength data needed to characterize the galactic environments in which molecular gas resides. Until now, the lack of a uniform set of sensitive, high resolution, wide-field maps of the molecular gas distribution across a large, diverse sample of galaxies has prevented such an investigation.

In this paper, we use data from the new PHANGS-ALMA survey[^1] (cite: Sun_etal_2018). The core data product from PHANGS-ALMA is $\sim 100$ pc resolution CO (2-1) mapping, which captures the “cloud-scale” properties of the molecular ISM. The PHANGS-ALMA galaxy sample also have rich supporting multi-wavelength data, including the atomic (HI) gas mass, stellar mass, and star formation rate estimates. We use these data to measure the cloud-scale turbulent pressure in the molecular gas, estimate the local mean ISM pressure, and compare them at multiple spatial scales.

As emphasized above, this paper builds on a number of previous works. Using a larger, more homogeneous sample, we aim to explain the observed variations in cloud-scale gas properties in (cite: Sun_etal_2018), to explicitly test the hypotheses of (cite: Field_etal_2011) and (cite: Hughes_etal_2013a), and to extend the consideration of some of the same topics covered by (cite: Schruba_etal_2019). Our calculation of the mean ISM pressure adapts from (cite: Elmegreen_1989) and many subsequent works (cite: Wong_Blitz_2002; Blitz_Rosolowsky_2004; Blitz_Rosolowsky_2006; Leroy_etal_2008). We particularly build on the dynamical equilibrium model developed by (cite: Ostriker_etal_2010) and (cite: Ostriker_Shetty_2011).

The structure of this paper is as follows. We describe our galaxy sample and data sources in Section [2](#sec:data), and data reduction methodology in Section [3](#sec:method). Then we provide detailed explanations of the key pressure estimates in Section [4](#sec:expectation). We present our main results in Section [5](#sec:result), and discuss their associated systematic uncertainties in Section [6](#sec:systematics). We further put them in the broader context of ISM evolution and star formation in Section [7](#sec:discussion). We summarize our findings in Section [8](#sec:summary).

# Data

|  |  |  |  |  |  |
|:---|:--:|---:|:--:|---:|---:|
| Galaxy | Dist. | Incl. | $\log M_\star$ | $R_\mathrm{e}$ | $R_\star$ |
|  | \[$\mathrm{Mpc}$\] | \[$\deg$\] | \[$\mbox{$\rm M_{\odot}$}$\] | \[$\ensuremath{''}$\] | \[$\ensuremath{''}$\] |
| NGC 628 | 9.77 | 8.7 | 10.24 | 89.1 | 69.3 |
| NGC 1087 | 14.4 | 40.5 |  | 31.9 | 26.4 |
| NGC 1300 | 26.1 | 31.8 | 10.85 | 69.2 | 62.3 |
| NGC 1792 | 12.8 | 64.7 | 10.34 | 49.8 | 33.3 |
| NGC 2903 | 8.47 | 67.0 | 10.42 | 77.9 | 54.9 |
| NGC 3351 | 10.0 | 45.1 | 10.34 | 62.5 | 58.0 |
| NGC 3511 | 9.95 | 75.0 |  | 66.3 | 37.9 |
| NGC 3521 | 11.2 | 69.0 | 10.79 | 65.7 | 39.1 |
| NGC 3627 | 10.6 | 56.5 | 10.70 | 64.5 | 54.0 |
| NGC 4293 | 16.0 | 65.0 | 10.46 | 51.4 | 50.1 |
| NGC 4298 | 16.8 | 59.6 | 10.09 | 36.3 | 26.2 |
| NGC 4321 | 15.2 | 39.1 | 10.69 | 73.9 | 61.1 |
| NGC 4424 | 16.4 | 58.2 |  | 31.9 | 27.6 |
| NGC 4457 | 15.6 | 17.4 | 10.43 | 14.9 | 45.4 |
| NGC 4496A | 14.9 | 55.3 |  | 42.4 | 31.1 |
| NGC 4535 | 15.8 | 42.1 | 10.51 | 79.8 | 57.0 |
| NGC 4536 | 15.2 | 64.8 | 10.27 | 40.2 | 50.7 |
| NGC 4540 | 16.8 | 38.3 |  | 21.5 | 15.3 |
| NGC 4571 | 14.9 | 31.9 | 10.05 | 48.6 | 35.2 |
| NGC 4689 | 16.8 | 39.0 | 10.25 | 48.5 | 35.9 |
| NGC 4694 | 16.8 | 60.7 |  | 18.7 | 31.9 |
| NGC 4731 | 12.4 | 64.0 |  | 79.0 | 73.5 |
| NGC 4781 | 15.3 | 56.4 |  | 32.8 | 25.5 |
| NGC 4826 | 4.36 | 58.6 | 10.21 | 68.2 | 56.2 |
| NGC 4951 | 12.0 | 70.5 |  | 25.9 | 16.1 |
| NGC 5042 | 12.6 | 51.4 |  | 43.2 | 35.9 |
| NGC 5068 | 5.16 | 27.0 |  | 81.1 | 59.7 |
| NGC 5134 | 18.5 | 22.7 | 10.32 | 23.2 | 23.2 |

: Galaxy Sample

Table notes: (2) Distance (from the Extragalactic Distance Database; (cite: Tully_etal_2009)); (3) inclination angle (cite: Lang_etal_2019); (4) logarithmic global stellar mass (from $z$0MGS; (cite: Leroy_etal_2019)); (5) effective radius (from PHANGS; A. K. Leroy et al., in preparation); (6) stellar disk scale length (from $\mathrm{S^4G}$; (cite: Salo_etal_2015));

We study 28 galaxies selected from the PHANGS-ALMA parent sample (A. K. Leroy et al., in preparation). All of these galaxies are nearby, massive, and actively forming stars (see Table [1](#tab:sample)). We select these targets because: (a) their PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$ data reach a linear resolution of 120 pc or better[^2] (in terms of beam full width half maximum, FWHM), and (b) they have a complete set of multi-wavelength supporting data, including new and archival HI 21 cm line maps, *Spitzer* IRAC 3.6 $\mu$m images, GALEX near-UV data, and WISE mid-IR data. Combined together, these data allow us to characterize molecular gas properties on cloud scales, and to put them in the context of their local ISM, star formation, and galactic stellar disk environment.

## Cloud-scale Resolution CO Data

We use PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$ data (internal release version 3.4) to trace molecular gas distribution and kinematics across the star-forming disks in all our sample galaxies (cite: Sun_etal_2018). These CO observations target the actively star-forming area in each of these galaxies, typically covering out to 5–15 kpc in galactic radius. They include data from both the 12-m array and the Morita Atacama Compact Array (ACA; consisting of the 7-m array and four 12-m total power antennas), and therefore should recover emission on all spatial scales. The 1$\sigma$ noise level in the data is $0.2\text{--}0.3$ K in a $2.5\,\mbox{$\rm km\,s^{-1}$}$ channel. The angular resolution (i.e., beam FWHM) ranges between $1.0\ensuremath{''}$–$1.8\ensuremath{''}$, corresponding to 25–120 pc linear resolution at the targets’ distances. This allows us to resolve the molecular gas distribution and kinematics at physical scales comparable to the typical size of GMCs (i.e., “cloud scales”).

To homogenize the CO data, we convolve all the data cubes to two different linear resolutions, 60 pc and 120 pc, whenever possible. This allows us to control for resolution-related systematics by comparing results derived at two different linear scales. All CO data in our sample can be matched to 120 pc resolution, whereas only a subset of them (6 galaxies) reach 60 pc.

We create CO line intensity ($I_\mathrm{CO}$; or moment-0) maps and line effective width[^3] ($\sigma_\mathrm{CO}$) maps from the matched resolution CO data cubes. We build these maps by analyzing only significant CO detections in the cube (selected by the “strict” signal masks as described in A. K. Leroy et al., in preparation). This strategy ensures high signal-to-noise in the derived CO line intensity and line width maps, but discards a fraction of CO flux existing at low signal-to-noise (cite: Sun_etal_2018). Below in Section [3.1](#sec:method:fCO), we quantify this effect by measuring a CO flux recovery fraction.

For more details regarding the CO data reduction, readers are referred to A. K. Leroy et al. (in preparation) and (cite: Sun_etal_2018).

## Kpc-scale Resolution Supporting Data

To measure the distribution of gas, stars, and star formation activity in each of our target galaxies, we assemble a multi-wavelength supporting dataset from a variety of sources. These supporting data typically have much coarser angular resolution than the PHANGS-ALMA CO data, corresponding to linear scales of hundreds to a thousand parsecs.

We use HI 21 cm emission data to trace the atomic gas distribution. We include new VLA data from the PHANGS-VLA project (covering 11 targets in our sample; PI: D. Utomo) and the EveryTHINGS project (NGC 4496A; PI: K. Sandstrom), as well as existing data from VIVA (cite: Chung_etal_2009), THINGS (cite: Walter_etal_2008), VLA observations associated with HERACLES (cite: Leroy_etal_2013a), and an individual ATCA observation (cite: Murugeshan_etal_2019). Most of these HI data have native angular resolution of $15\text{--}25\ensuremath{''}$, which corresponds to linear scales of $0.5\text{--}2$ kpc at the distances of the targets. Typical column density sensitivities are $0.5\text{--}2\times10^{20}\;\mathrm{cm}^{-2}$ at 3$\sigma$ after integrating over the $10\text{--}20\;\mbox{$\rm km\,s^{-1}$}$ line width.

We use *Spitzer* IRAC 3.6 $\mu$m data to trace the stellar mass distribution. These data come from the *Spitzer* Survey of Stellar Structure in Galaxies (cite: Sheth_etal_2010). For most targets in our sample, we use the ICA 3.6 $\mu$m maps (cite: Querejeta_etal_2015), for which the emission from dust has been subtracted. For the remaining three targets (NGC 4571, NGC 4689, and NGC 5134), we use the raw 3.6 $\mu$m maps as these galaxies have global $[3.6]-[4.5]$ colors compatible with old stellar population (cite: Querejeta_etal_2015). All these maps are masked to remove foreground stars. These data have a native angular resolution of $\sim2\ensuremath{''}$, which corresponds to linear scales of hundreds of parsecs for our targets.

We combine GALEX near-UV (NUV) data and WISE mid-IR (MIR) data to derive kpc-scale star formation rate (SFR) estimates. We use the post-processed GALEX NUV images and WISE band-3 images from the $z=0$ Multi-wavelength Galaxy Synthesis (cite: Leroy_etal_2019). These images are corrected for background, aligned for astrometry, and masked to remove foreground stars. Almost all targets in our sample have both GALEX and WISE coverage (except for NGC 4689, for which only WISE is available). We use the data at fixed angular resolution of $7.5\ensuremath{''}$, which corresponds to linear scales $\lesssim1$ kpc.

We homogenize the resolution of these supporting data to a common 1 kpc linear scale. As described above, most data have native resolutions better than 1 kpc, and thus can be directly convolved to this coarser resolution. For some of the HI data, however, the native resolution is coarser. As the resolution of these HI data is not crucial for our analysis (see discussion in Section [4.3](#sec:expectation:PDE-cloud)), we keep these data at their native resolution in the following analysis.

To complement these supporting data, we also convolve the PHANGS-ALMA CO data to 1 kpc resolution. This provides a tracer of the large-scale molecular gas distribution. The convolution is performed on the CO data cubes, and from these convolved cubes we derive a set of low resolution CO line intensity maps. This strategy takes advantage of the better surface brightness sensitivity at coarser resolution. In the resulting kpc-scale CO intensity maps, we detect emission at high signal-to-noise over almost every sightline, and expect to recover essentially all emission within the observation footprint.

Altogether, these data provide us with spatially resolved information about the (molecular and atomic) gas distribution, the stellar disk structure, and the local star formation rate, all of which are measured on a matched 1 kpc spatial scale.

# Methods

The PHANGS-ALMA CO data probe the molecular gas distribution and kinematics on 60–120 pc scales (cloud scales), whereas the multi-wavelength supporting data characterize the galactic environment on 1 kpc scale. We conduct a cross-spatial-scale analysis to bridge the gap between these two spatial scales. The methodology that we adopt here has been developed and used in a series of previous works (cite: Ossenkopf_MacLow_2002; Sandstrom_etal_2013; Leroy_etal_2013a; Leroy_etal_2016; Gallagher_etal_2018b; Utomo_etal_2018).

We first divide the PHANGS-ALMA CO observation footprint into hexagonal apertures. They form a hexagonal tiling in the plane of the sky, with a 1 kpc spacing (corresponding to $8''$–$40''$) between the centers of adjacent apertures. These kpc-sized, hexagonal apertures are the fundamental units of our analysis.

The key step of this cross-spatial-scale analysis is to characterize the statistics of the many independent cloud-scale measurements within each kpc-sized aperture. In this work, we use a CO intensity-weighted averaging scheme to quantify the ensemble average of a given cloud-scale measurement in each aperture. As an example, we calculate the ensemble average of CO line width $\sigma_\mathrm{CO}$ within a kpc-sized aperture $A$ via $$\begin{equation}
    \left<\sigma_\mathrm{CO,\,\theta pc}\right>_\mathrm{1kpc} = \frac{\int_A \sigma_\mathrm{CO,\,\theta pc}\, I_\mathrm{CO,\,\theta pc}\, \mathrm{d}S}{\int_A I_\mathrm{CO,\,\theta pc}\, \mathrm{d}S}~.
    \label{eq:average}
\end{equation}$$ Here $\sigma_\mathrm{CO,\,\theta pc}$ is the CO line width measured on $\theta=60$ pc and $120$ pc scales, $I_\mathrm{CO,\,\theta pc}$ is the line intensity measured on the same scale (i.e., the statistical “weight”). The “$\left<\right>_\mathrm{1kpc}$” symbol denotes a CO intensity-weighted average over the kpc-sized aperture.

This CO intensity-weighted averaging scheme preserves information on the gas distribution on cloud scales (cite: Leroy_etal_2016). By using CO line intensity (or equivalently CO flux, given a fixed beam size) as the statistical weight, it prevents the averaged value from being “diluted” by areas with no CO detections. As long as the CO flux detection fraction in an aperture remains reasonably high (which is the case within most apertures in our sample; see Section [3.1](#sec:method:fCO) below, and plots in Section [5](#sec:result)), the CO intensity-weighted average value does not suffer from a strong dilution effect. Conversely, due to the generally low area coverage fraction of CO detection in our data, a direct, area-weighted average would include many more non-detections than detections, and yield significantly diluted average values.

To supplement these ensemble averages of cloud-scale CO measurements, we include all the kpc-scale resolution supporting data into this analysis, by directly sampling these maps at the center of each hexagonal aperture. The matched 1 kpc spacing between the centers of adjacent apertures ensures that there is little correlation between measurements in adjacent apertures.

Our cross-spatial-scale analysis produces a rich multi-wavelength database for every target in our sample. This database has been used in a previous publication (cite: Herrera_etal_2019), and the current work uses it as the foundation for carrying out the calculations presented below in Section [4](#sec:expectation). The full database, as well as the correlations between the basic observables will be published in a companion paper (J. Sun et al., in preparation).

## CO Flux Recovery Fraction

As discussed above, for our CO intensity-weighted averaging scheme to work optimally, the CO observations should be sensitive enough to detect a significant fraction of CO flux at cloud-scale resolution in each aperture. This is indeed the case for the majority of the apertures in our sample (see below and plots in Section [5](#sec:result)). When this is not the case, however, the averaged values will suffer from larger uncertainties and reflect only properties of the brightest clouds.

To control for these effects due to the finite sensitivity of CO observations, we quantify a CO flux recovery fraction, $f_\mathrm{CO,\,\theta pc}$, within each 1 kpc aperture. We do this by comparing, within the footprint of each aperture, the total flux included in the 60–120 pc resolution CO line intensity map (i.e., within the “strict” signal masks, see Section [2.1](#sec:data:CO)) to the total flux in the corresponding CO data cube. We estimate the latter quantity by summing up the cube within a wide, high completeness signal mask (referred to as the “broad” mask in A. K. Leroy et al., in preparation).

Our calculation shows that for the majority ($\sim$70%) of the kpc-scale apertures in our sample, the CO flux recovery fraction on 120 pc scales, $f_\mathrm{CO,\,120pc}$, is higher than 50%. Since the CO intensity-weighted averages are calculated from only the *detected* emission, a recovery fraction of $f_\mathrm{CO}> 50\%$ means that the majority of the CO emission in that kpc-scale aperture is included in the averaging. First, this assures that the derived averages in these apertures have reasonably small statistical error ($\le\sqrt{2}$ times larger than the case of infinite sensitivity given homoscedastic individual measurements). Second, and most importantly, in the cases where the undetected molecular gas has systematically different properties than the detected, the intensity-weighted averages in these high $f_\mathrm{CO}$ apertures are also much less susceptible to systematic effects due to sampling biases.

Hereafter, when presenting results derived from this CO intensity-weighted averaging approach, we represent the data in darker/lighter colors to denote higher/lower $f_\mathrm{CO}$. Measurements shown in darker colors are thus more representative of the overall cloud population, whereas those shown in lighter colors only characterize the brightest clouds in the kpc-sized aperture.

## CO Flux from Various Morphological Regions

Our weighted averaging scheme is a way to quantify the mean molecular gas properties in each kpc-sized aperture. This kpc aperture size is large enough that the CO flux within each aperture might come from various morphological regions of a galaxy (e.g., bulges, bars). In this work, for each of the averaging apertures, we also keep track of the fractional CO flux contribution from different morphological regions.

In detail, we first identify areas covered by morphological structures like bulges and bars (when applicable) in every galaxy. To identify the bulge regions, we use the $\mathrm{S^4G}$ structural decomposition results presented by (cite: Salo_etal_2015). These results are based on two-dimensional structural decomposition of *Spitzer* IRAC 3.6 $\mu$m images with GALFIT3.0 (cite: Peng_etal_2010). To identify bar regions, we instead use results from the visual identification in (cite: Herrera-Endoqui_etal_2015), which have higher quality than the $\mathrm{S^4G}$ pipeline 4 results.

Within each kpc-sized aperture, we calculate the fractional contribution in the total CO flux from the bulge and bar regions. Whenever an aperture includes non-zero CO flux coming from bulge or bar regions, we classify it as a “bulge/bar” aperture[^4]. Otherwise, we classify it as a “disk” aperture. When presenting our results, we show measurements in bulge/bar apertures in orange colors, and those in disk apertures in blue colors.

## Converting Observables to Physical Quantities

We use the PHANGS-ALMA CO data and multi-wavelength supporting data to estimate physical properties of the molecular gas and its ambient galactic environment. Here we detail our methods to convert direct observables (e.g., CO intensity) into physical quantities (e.g., molecular gas surface density) in each kpc-sized aperture in our sample. Table [2](#tab:def) lists the key physical quantities we derive, including both average molecular cloud properties and environment characteristics. These physical quantities are the basis of all following calculations detailed in Section [4](#sec:expectation).

### Cloud-scale Molecular Gas Properties

Following (cite: Sun_etal_2018), we estimate cloud-scale molecular gas surface density ($\Sigma_\mathrm{mol,\,\theta pc}$) and velocity dispersion ($\sigma_\mathrm{mol,\,\theta pc}$) from the observed $\mathrm{CO}\,(2\text{--}1)$ line intensity ($I_\mathrm{CO,\,\theta pc}$) and effective width ($\sigma_\mathrm{CO,\,\theta pc}$), via $$\begin{align}
    \Sigma_\mathrm{mol,\,\theta pc}&= \frac{\alpha_\mathrm{CO}}{R_{21}}\,I_\mathrm{CO,\,\theta pc}~, \label{eq:Sigmol}\\
    \sigma_\mathrm{mol,\,\theta pc}&= \sigma_\mathrm{CO,\,\theta pc}~. \label{eq:sigmol}
\end{align}$$ In Equation [\[eq:Sigmol\]](#eq:Sigmol), $R_{21} = 0.7$ is the adopted $\mathrm{CO}\,(2\text{--}1)$ to $\mathrm{CO}\,(1\text{--}0)$ line ratio (cite: Leroy_etal_2013a; Saintonge_etal_2017), whereas $\alpha_\mathrm{CO}$ is a CO-to-H$_2$ conversion factor[^5], whose value varies aperture-by-aperture.

We adopt the following prescription to predict the values of $\alpha_\mathrm{CO}$ for each aperture in our sample. Similar to the calibration suggested by (cite: Accurso_etal_2017) and adopted in the xCOLD GASS survey (cite: Saintonge_etal_2017), we predict $\alpha_\mathrm{CO}$ via $$\begin{equation}
    \alpha_\mathrm{CO}= 4.35\,Z'^{-1.6}\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1}~.
\label{eq:alphaCO}
\end{equation}$$ Here $Z'$ is the local gas phase abundance normalized to the solar value appropriate for the (cite: Pettini_Pagel_2004) metallicity calibration \[$12+\mathrm{log\,(O/H)}=8.69$\].

Using Equation [\[eq:alphaCO\]](#eq:alphaCO) to predict $\alpha_\mathrm{CO}$ requires knowing $Z'$ for every kpc-sized aperture across our sample. However, metallicity measurements existing in the literature only cover a subset of our targets, and they are derived using heterogeneous calibration methods. To ensure a homogeneous coverage of the entire sample, we instead predict $Z'$ in a uniform, empirical way. Using a mass-metallicity relation reported by (cite: Sanchez_etal_2019), we first predict $Z'$ at one effective radius ($R_\mathrm{e}$) in each galaxy based on the galaxy global stellar mass (see Table [1](#tab:sample)). We then extend our prediction to cover the entire galaxy assuming a universal radial metallicity gradient of $-0.1\;\mathrm{dex}/R_\mathrm{e}$ (cite: Sanchez_etal_2014). Combining this locally predicted $Z'$ with Equation [\[eq:alphaCO\]](#eq:alphaCO), we have a predicted $\alpha_\mathrm{CO}$ value for every aperture in our sample.

Our choices on the prescriptions for predicting $Z'$ and $\alpha_\mathrm{CO}$ could affect many of the measured molecular gas properties in this work. To quantify the systematic effects associated with these choices, in Section [6.1](#sec:systematics:alphaCO) we consider three alternative $\alpha_\mathrm{CO}$ prescriptions, and compare the quantitative results with those derived based on our “fidual” prescriptions.

### Kpc-scale Environment Characteristics

In each kpc-sized aperture, we estimate the physical properties of the large-scale galactic environment from the multi-wavelength supporting data described above in Section [2.2](#sec:data:kpc).

- *Molecular Gas Surface Density:* We estimate the kpc-scale molecular gas surface density $\Sigma_\mathrm{mol,\,1kpc}$ from the $\mathrm{CO}\,(2\text{--}1)$ intensity $I_\mathrm{CO,\,1kpc}$, via $$\begin{equation}
      \Sigma_\mathrm{mol,\,1kpc}= \frac{\alpha_\mathrm{CO}}{R_{21}}\,I_\mathrm{CO,\,1kpc}\cos{i}~.
      \label{eq:Sigmolkpc}
  \end{equation}$$ This conversion is similar to Equation [\[eq:Sigmol\]](#eq:Sigmol), except that here we also add a “$\cos{i}$” term to correct for the projection effect due to galaxy inclination[^6] (see Table [1](#tab:sample)).

- *Atomic Gas Surface Density:* We estimate the kpc-scale atomic gas surface density $\Sigma_\mathrm{atom,\,1kpc}$ from the observed HI 21 cm line intensity $I_\mathrm{21cm,\,1kpc}$, via $$\begin{equation}
      \frac{\Sigma_\mathrm{atom,\,1kpc}}{\mbox{$\rm M_{\odot}\,pc^{-2}$}} = 1.97\times10^{-2}\;\frac{I_\mathrm{21cm,\,1kpc}}{\mbox{$\rm K\,km\,s^{-1}$}}\,\cos{i}~.
      \label{eq:Sigatomkpc}
  \end{equation}$$ This conversion includes the mass contribution from heavy elements.

- *Stellar Mass Surface Density:* We estimate the kpc-scale stellar mass surface density $\Sigma_\mathrm{\star,\,1kpc}$ from the (dust-corrected) 3.6 $\mu$m specific surface brightness $I_\mathrm{3.6,\,1kpc}$, via[^7] $$\begin{equation}
      \frac{\Sigma_\mathrm{\star,\,1kpc}}{\mbox{$\rm M_{\odot}\,pc^{-2}$}} = 3.3\times10^2\;\frac{I_\mathrm{3.6,\,1kpc}}{\mbox{$\rm MJy\,sr^{-1}$}}\,\cos{i}~.
      \label{eq:Sigstarkpc}
  \end{equation}$$ This conversion assumes a 3.6 $\mu$m mass-to-light ratio of $Y_{3.6} = 0.47\,M_\odot/L_\odot$ (cite: McGaugh_Schombert_2014).

- *SFR Surface Density:* We estimate the kpc-scale SFR surface density $\Sigma_\mathrm{SFR,\,1kpc}$ from the combined GALEX NUV and WISE 12 $\mu$m (band 3) data, following the calibration suggested by (cite: Leroy_etal_2019): $$\begin{align}
      \frac{\Sigma_\mathrm{SFR,\,1kpc}}{\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}}
      =&\, \left(8.9\times10^{-2}\;\frac{I_\mathrm{NUV,\,1kpc}}{\mbox{$\rm MJy\,sr^{-1}$}}\right. \nonumber\\
      &+ \left. 4.1\times10^{-3}\;\frac{I_\mathrm{12,\,1kpc}}{\mbox{$\rm MJy\,sr^{-1}$}}\right)\,\cos{i}~.
      \label{eq:SigSFRkpc}
  \end{align}$$ These prescriptions are broadly consistent with stellar initial mass functions suggested by (cite: Chabrier_2003) and (cite: Kroupa_Weidner_2003).

# Pressure Estimates

In this work, we test the hypothesis that dynamical equilibrium holds in the ISM. Given that molecular gas is usually found near the disk mid-plane (cite: Heyer_Dame_2015), it is interesting to compare a direct measurement of the internal pressure in the molecular gas to the predicted mid-plane pressure from dynamical equilibrium models. We use the term “dynamical equilibrium pressure” ($P_\mathrm{DE}$) to refer to the latter quantity throughout this work.

Estimating $P_\mathrm{DE}$ from observations is challenging. Many previous studies (cite: Blitz_Rosolowsky_2004; Blitz_Rosolowsky_2006; Leroy_etal_2008; Hughes_etal_2013a) treat the gas disk as a smooth, single-phase fluid, assuming no substructure below kpc scales (this is the typical resolution of HI surveys targeting nearby galaxies). In reality, turbulence, shocks, and gravitational instabilities create a rich multi-scale structure in the ISM. The cold and dense molecular phase, in particular, is highly structured on small scales, which leads to enhanced gas self-gravity in denser regions. As a result of this small-scale structure, the total weight of the ISM is higher than one would infer assuming a smooth disk geometry, and a greater pressure is needed to balance this weight. Estimates of $P_\mathrm{DE}$ that assume a smooth disk neglect this enhancement in gas self-gravity. While they might be able to reflect the mean pressure over a large portion of the ISM disk, these estimates of $P_\mathrm{DE}$ in many previous works represent only lower limits on the expected pressure within molecular clouds.

Building on these previous works, here we present estimates for $P_\mathrm{DE}$ that also take into account the presence of small-scale substructure in the molecular ISM. This is possible because of the new, high resolution PHANGS-ALMA CO maps. They allow us to estimate the weight of molecular gas in its local gravitational potential on cloud scales, which is the same spatial scale on which we measure molecular gas internal pressure. We then combine our estimate for the weight of molecular gas with the weight of the volume-filling atomic gas in the combined gas and stellar potential. This leads to a modified, cloud-scale equilibrium pressure, which accounts for both the dense, clumpy molecular phase and the diffuse, smooth atomic phase.

We note that similar approaches have been adopted to explain molecular cloud properties in the Milky Way (cite: Heyer_etal_2001; Field_etal_2011) and other galaxies (cite: Hughes_etal_2013a; Schruba_etal_2019). Most of these studies adopt a “bottom-up” approach. That is, they segment the observed CO emission into individual clouds, and consider pressure balance between the identified clouds and the large-scale galactic environment in order to explain the observed cloud properties. In this paper, we formulate an alternative, “top-down” approach. We consider all molecular gas in each kpc-size region, without employing any cloud identification algorithm (for an explicit comparison between our approach and a cloud-based approach, see Section [6.3](#sec:systematics:CPROPS)). We then attempt to explain the ensemble average of molecular gas properties on fixed spatial scales in the context of a dynamical equilibrium model.

Our “top-down” approach captures many of the same physics as cloud-centered approaches, i.e., the balance between internal pressure, ambient pressure, self-gravity, and external gravity. In addition, it is designed to robustly treat data with a wide range of physical resolutions, even when individual gas structures are not fully resolved or cleanly separated from one another. It also considers all detected emission, and so should yield highly reproducible results that characterize the behavior of the entire molecular gas reservoir.

In this section, we explain our methodology for estimating 1) the internal pressure in molecular gas, 2) the classic, kpc-scale dynamic equilibrium pressure, and 3) the modified, cloud-scale equilibrium pressure. These pressure estimates are also listed in Table [2](#tab:def).

## Internal Pressure in Molecular Gas

Internal pressure in molecular gas includes the contributions from thermal and turbulent motion, as well as magnetic fields. Observational evidence, including super-thermal CO line widths and the size–line width relation observed within GMCs, suggest that turbulent motion dominates over thermal motion on physical scales comparable to cloud sizes (cite: Larson_1981; Solomon_etal_1987; Heyer_Brunt_2004). Numerical simulations of the star-forming ISM on galactic scales also find that the magnetic term is subdominant, typically reaching only $\sim 50\%$ of the kinetic term in the effective gas pressure (cite: Kim_Ostriker_2017; Pakmor_etal_2017). Motivated by these findings, we assume in this work that turbulent motion represents the primary source of internal pressure in molecular gas, and treat all other contributions as sub-dominant. We do not differentiate between turbulent pressure and total internal pressure in molecular gas hereafter.

Turbulent pressure in molecular gas is commonly estimated from volume density and the observed (one-dimensional) velocity dispersion, under the assumption that turbulence is isotropic: $$\begin{align}
    P_\mathrm{turb}= \rho_\mathrm{mol}\, \sigma_\mathrm{turb,1D}^2~.
\end{align}$$

While one can use the observed velocity dispersion $\sigma_\mathrm{mol}$ along the line of sight as a proxy of $\sigma_\mathrm{turb,1D}$, $\rho_\mathrm{mol}$ is not usually directly observed. Here we convert cloud-scale molecular gas surface density, $\Sigma_\mathrm{mol}$, into volume density, $\rho_\mathrm{mol}$. To do this, we assume a constant density spherical cloud filling each beam, with the cloud diameter $D_\mathrm{cloud}$ equal to the beam FWHM[^8] (i.e., 60 or 120 pc, but see Section [6.3](#sec:systematics:CPROPS) for an alternative approach). The inferred turbulent pressure in molecular gas can then be expressed as $$\begin{align}
    P_\mathrm{turb}
    = \rho_\mathrm{mol} \sigma_\mathrm{mol}^2
    = \frac{6M_\mathrm{mol}}{\pi D_\mathrm{cloud}^3} \sigma_\mathrm{mol}^2
    = \frac{3 \Sigma_\mathrm{mol}\sigma_\mathrm{mol}^2}{2D_\mathrm{cloud}}~.
    \label{eq:Pturb}
\end{align}$$ Here $M_\mathrm{mol}=\Sigma_\mathrm{mol}\cdot(\pi D_\mathrm{cloud}^2/4)$ is the total molecular gas mass of the spherical cloud.

We average the estimated cloud-scale turbulent pressure across each kpc-sized region following the same CO flux weighting scheme described in Section [3](#sec:method): $$\begin{align}
    \left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}
    &= \frac{\int_A P_\mathrm{turb,\,\theta pc}\,I_\mathrm{CO,\,\theta pc}\,\mathrm{d}S}{\int_A I_\mathrm{CO,\,\theta pc}\,\mathrm{d}S} ~.
    \label{eq:Pturbavg}
\end{align}$$ This can be interpreted as the mass-weighted average turbulent pressure within each kpc-sized aperture $A$.

## Kpc-scale Dynamical Equilibrium Pressure

To compare with previous works, we first estimate the classic, kpc-scale dynamical equilibrium pressure, $P_\mathrm{DE,\,1kpc}$. We follow the same basic formalism that has been adopted, with some variations, in many previous works (cite: Spitzer_1942; Elmegreen_1989; Elmegreen_Parravano_1994; Wong_Blitz_2002; Blitz_Rosolowsky_2004; Blitz_Rosolowsky_2006; Leroy_etal_2008; Koyama_Ostriker_2009b; Ostriker_etal_2010; Kim_etal_2011; Ostriker_Shetty_2011; Shetty_Ostriker_2012; Hughes_etal_2013a; Kim_etal_2013; Kim_Ostriker_2015b; Benincasa_etal_2016; Herrera-Camus_etal_2017; Gallagher_etal_2018a; Fisher_etal_2019; Schruba_etal_2019).

This approach models the distribution of gas and stars in a galaxy disk as isothermal fluids in a plane-parallel geometry. For the calculation here, we assume that the (single component) gas disk scale height is much smaller than the stellar disk scale height. We also neglect gravity due to dark matter, as it represents only a minor component in the galactic environments we study here (i.e., the inner disks of relatively massive galaxies). In this case, we can express $P_\mathrm{DE}$ as: $$\begin{align}
    P_\mathrm{DE,\,1kpc}
    =&\; \frac{\pi G}{2}\,\Sigma_\mathrm{gas,\,1kpc}^2 \nonumber\\
    &+ \Sigma_\mathrm{gas,\,1kpc}\sqrt{2 G\rho_\mathrm{\star,\,1kpc}}\, \sigma_\mathrm{gas,\,z}~.
\label{eq:PDEkpc}
\end{align}$$ The first term is the weight of the ISM due to the self-gravity of the ISM disk (cite: Spitzer_1942; Elmegreen_1989). The second term is the weight of the ISM due to stellar gravity (cite: Spitzer_1942; Blitz_Rosolowsky_2004). $\Sigma_\mathrm{gas,\,1kpc}=\Sigma_\mathrm{mol,\,1kpc}+\Sigma_\mathrm{atom,\,1kpc}$ is the total gas surface density, $\rho_\mathrm{\star,\,1kpc}$ is stellar mass volume density near disk mid-plane, and $\sigma_\mathrm{gas,\,z}$ is the vertical gas velocity dispersion (a combination of turbulent, thermal, and magnetic terms).

Following (cite: Blitz_Rosolowsky_2006; Leroy_etal_2008; Ostriker_etal_2010), we estimate mid-plane stellar volume densities from the observed surface densities in each kpc-sized aperture: $$\begin{equation}
    \rho_\mathrm{\star,\,1kpc}
    = \frac{\Sigma_\mathrm{\star,\,1kpc}}{4H_\mathrm{\star}}
    = \frac{\Sigma_\mathrm{\star,\,1kpc}}{0.54R_\mathrm{\star}}~.
\label{eq:rhostarkpc}
\end{equation}$$ The first step assumes an isothermal density profile along the vertical direction (i.e., $\rho_*(z) \propto \mathop{\mathrm{sech}}^2[z/(2H_*)]$) with $H_\mathrm{\star}$ being the stellar disk scale height (cite: vanderKruit_1988). The second step assumes a fixed stellar disk flattening ratio $R_\mathrm{\star}/H_\mathrm{\star}= 7.3$ (cite: Kregel_etal_2002). Here $R_\mathrm{\star}$ is the radial scale length of the stellar disk, for which we adopt the value from the $\mathrm{S^4G}$ photometric decompositions of 3.6 $\mu$m images (cite: Salo_etal_2015).

For $\sigma_\mathrm{gas,\,z}$, we calculate the mass-weighted average velocity dispersion of molecular and atomic phases $$\begin{equation}
    \sigma_\mathrm{gas,\,z}
    = f_\mathrm{mol} \left<\sigma_\mathrm{mol,\,\theta pc}\right>_\mathrm{1kpc}+ (1-f_\mathrm{mol})\, \sigma_\mathrm{atom}~,
    \label{eq:siggasz}
\end{equation}$$ where $f_\mathrm{mol}=\Sigma_\mathrm{mol,\,1kpc}\,/\,(\Sigma_\mathrm{mol,\,1kpc}+\Sigma_\mathrm{atom,\,1kpc})$ is the fraction of gas mass in the molecular phase. We adopt a fixed atomic gas velocity dispersion $\sigma_\mathrm{atom}=10\;\mbox{$\rm km\,s^{-1}$}$ (cite: Leroy_etal_2008; Tamburro_etal_2009; Wilson_etal_2011; Caldu-Primo_etal_2013; Mogotsi_etal_2016).

Our adopted assumptions for the $\rho_\mathrm{\star,\,1kpc}$ and $\sigma_\mathrm{gas,\,z}$ estimation might introduce systematic biases in the derived $P_\mathrm{DE,\,1kpc}$. In Section [6.2](#sec:systematics:PDE), we estimate $P_\mathrm{DE,\,1kpc}$ by adopting two alternatives for estimating $\sigma_\mathrm{gas,\,z}$ and $\rho_\mathrm{\star,\,1kpc}$, and compare the results with our fiducial $P_\mathrm{DE,\,1kpc}$ estimates.

## Cloud-scale Dynamical Equilibrium Pressure

The classic, kpc-scale equilibrium pressure defined in Section [4.2](#sec:expectation:PDE-kpc) does not account for gas substructure within each kpc-sized aperture. For atomic gas, surface density fluctuations on sub-kpc scale are usually moderate (cite: Leroy_etal_2013a), so this issue is likely minor. For molecular gas, however, we expect strong clumping (cite: Leroy_etal_2013a). Therefore, gas self-gravity should be significantly enhanced in over-dense regions (e.g., in molecular clouds), and the required pressure in molecular gas to balance this enhanced gravity should exceed the classic, kpc-scale pressure estimates.

To account for this, we introduce a modified, cloud-scale dynamical equilibrium pressure, $\left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}$. Using the classic formulation as a starting point, we treat the clumpy molecular ISM and diffuse atomic ISM separately, allowing them to have different geometry (cite: Ostriker_etal_2010; Schruba_etal_2019). We offer a brief summary of this alternative formalism here, but leave a more detailed description of the derivation and adopted assumptions to Appendix [9](#apdx:formulation).

In this alternative formalism, we split the total cloud-scale equilibrium pressure into two parts: $$\begin{align}
    \left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}
    &= \left<\mathcal{W}_\mathrm{total,\,\theta pc}\right>_\mathrm{1kpc} \nonumber\\
    &= \left<\mathcal{W}_\mathrm{cloud,\,\theta pc}\right>_\mathrm{1kpc} + \mathcal{W}_\mathrm{atom,\,1kpc}~.
\label{eq:PDEavg}
\end{align}$$ The first part, $\left<\mathcal{W}_\mathrm{cloud,\,\theta pc}\right>_\mathrm{1kpc}$, corresponds to the weight of molecular gas, most of which resides in clumpy structures on cloud scales. For simplicity, we assume that all molecular gas is organized into spherical, cloud-like structures. The weight within each individual structure is due to 1) its own self-gravity, 2) the gravity of other molecular structures, and 3) the gravity of stars: $$\begin{align}
    \mathcal{W}_\mathrm{cloud,\,\theta pc} =&\, \mathcal{W}_\mathrm{cloud,\,\theta pc}^\mathrm{self} + \mathcal{W}_\mathrm{cloud,\,\theta pc}^\mathrm{ext-mol} + \mathcal{W}_\mathrm{cloud,\,\theta pc}^\mathrm{star} \nonumber\\
    =&\, \frac{3\pi}{8}G\Sigma_\mathrm{mol,\,\theta pc}^2 + \frac{\pi}{2}G\Sigma_\mathrm{mol,\,\theta pc}\Sigma_\mathrm{mol,\,1kpc}\nonumber\\
    &+ \frac{3\pi}{4}G\rho_\mathrm{\star,\,1kpc}\Sigma_\mathrm{mol,\,\theta pc}D_\mathrm{cloud}~.
    \label{eq:W_cloud}
\end{align}$$ Consistent with our estimation of turbulent pressure in Equation [\[eq:Pturb\]](#eq:Pturb), we also assume the cloud diameter $D_\mathrm{cloud}$ equals the beam FWHM here.

We then adopt the same averaging scheme used in Equation [\[eq:Pturbavg\]](#eq:Pturbavg) to estimate the (CO flux-weighted) average $\mathcal{W}_\mathrm{cloud,\,\theta pc}$ across each kpc-sized aperture: $$\begin{align}
    \left<\mathcal{W}_\mathrm{cloud,\,\theta pc}\right>_\mathrm{1kpc}
    &= \frac{\int_A \mathcal{W}_\mathrm{cloud,\,\theta pc}\, I_\mathrm{CO,\,\theta pc}\,\mathrm{d}S}{\int_A I_\mathrm{CO,\,\theta pc}\,\mathrm{d}S}~.
    \label{eq:W_cloud_avg}
\end{align}$$

The second term in Equation [\[eq:PDEavg\]](#eq:PDEavg), $\mathcal{W}_\mathrm{atom,\,1kpc}$, corresponds to the weight of the smooth extended layer of atomic gas. This weight is due to the gravity of all gas (both atomic and molecular phases) plus the stars, as felt by the atomic layer. Motivated by the relative smoothness of the atomic gas distribution and the coarser resolution of the HI data, we estimate this weight using only kpc-scale measurements, assuming uniform atomic gas surface density within each kpc-sized aperture: $$\begin{align}
    \mathcal{W}_\mathrm{atom,\,1kpc} =&\, \mathcal{W}_\mathrm{atom,\,1kpc}^\mathrm{self} + \mathcal{W}_\mathrm{atom,\,1kpc}^\mathrm{mol} + \mathcal{W}_\mathrm{atom,\,1kpc}^\mathrm{star} \nonumber\\
    =&\, \frac{\pi G}{2}\Sigma_\mathrm{atom,\,1kpc}^2 + \pi G\Sigma_\mathrm{atom,\,1kpc}\Sigma_\mathrm{mol,\,1kpc}\nonumber\\
    &+ \Sigma_\mathrm{atom,\,1kpc}\sqrt{2G\rho_\mathrm{\star,\,1kpc}}\,\sigma_\mathrm{atom}~.
\label{eq:W_atom}
\end{align}$$ Here we assume that the molecular gas disk is “sandwiched” by the atomic gas disk, and thus the second term above has a 2 times larger pre-factor than the first term (see Appendix [9](#apdx:formulation) for detailed derivation). We adopt $\sigma_\mathrm{atom}=10\;\mbox{$\rm km\,s^{-1}$}$, consistent with Section [4.2](#sec:expectation:PDE-kpc).

If vertical dynamical equilibrium holds across multiple spatial scales, we would expect molecular gas internal pressure on cloud scales to match the dynamical equilibrium pressure on the same scale. By comparing our measured $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ and best-estimate $\left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}$, we can test whether, in a statistical average sense, the molecular ISM in nearby, star-forming disk galaxies can be described by this model.

# Results

+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Quantity Definition                                                                                                    | Symbol                                                                            | Unit                                | Data Source                               |
+:=======================================================================================================================+:=================================================================================:+:===================================:+:=========================================:+
| Ensemble average of cloud-scale molecular gas properties (see §[3.3.1](#sec:method:phys:mol))                                                                                                                                                                                                |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (measured at $\theta=60$, 120 pc scale; averaged over each kpc-sized aperture; see §[3](#sec:method))                                                                                                                                                                                        |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average molecular gas surface density (Eq. [\[eq:average\]](#eq:average)&[\[eq:Sigmol\]](#eq:Sigmol))                  | $\left<\Sigma_\mathrm{mol,\,\theta pc}\right>_\mathrm{1kpc}$                      | $\rm M_{\odot}\,pc^{-2}$            | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average molecular gas velocity dispersion (Eq. [\[eq:average\]](#eq:average)&[\[eq:sigmol\]](#eq:sigmol))              | $\left<\sigma_\mathrm{mol,\,\theta pc}\right>_\mathrm{1kpc}$                      | $\rm km\,s^{-1}$                    | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| CO flux recovery fraction (§[3.1](#sec:method:fCO))                                                                    | $f_\mathrm{CO,\,\theta pc}$                                                       | \-                                  | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Environmental characteristics (see §[3.3.2](#sec:method:phys:kpc))                                                                                                                                                                                                                           |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| (measured at 1 kpc scale)                                                                                                                                                                                                                                                                    |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| kpc-scale molecular gas surface density (Eq. [\[eq:Sigmolkpc\]](#eq:Sigmolkpc))                                        | $\Sigma_\mathrm{mol,\,1kpc}$                                                      | $\rm M_{\odot}\,pc^{-2}$            | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| kpc-scale atomic gas surface density (Eq. [\[eq:Sigatomkpc\]](#eq:Sigatomkpc))                                         | $\Sigma_\mathrm{atom,\,1kpc}$                                                     | $\rm M_{\odot}\,pc^{-2}$            | PHANGS-VLA HI 21 cm, etc.                 |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| kpc-scale stellar mass surface density (Eq. [\[eq:Sigstarkpc\]](#eq:Sigstarkpc))                                       | $\Sigma_\mathrm{\star,\,1kpc}$                                                    | $\rm M_{\odot}\,pc^{-2}$            | $\mathrm{S^4G}$ IRAC 3.6 $\mu$m           |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| kpc-scale star formation rate surface density (Eq. [\[eq:SigSFRkpc\]](#eq:SigSFRkpc))                                  | $\Sigma_\mathrm{SFR,\,1kpc}$                                                      | $\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$  | z0MGS NUV+MIR                             |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Pressure estimates (see §[4](#sec:expectation))                                                                                                                                                                                                                                              |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average turbulent pressure in molecular gas (Eq. [\[eq:Pturb\]](#eq:Pturb)&[\[eq:Pturbavg\]](#eq:Pturbavg))            | $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$                          | $k_\mathrm{B}\rm\,K\,cm^{-3}$       | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| kpc-scale ISM equilibrium pressure (Eq. [\[eq:PDEkpc\]](#eq:PDEkpc)–[\[eq:siggasz\]](#eq:siggasz))                     | $P_\mathrm{DE,\,1kpc}$                                                            | $k_\mathrm{B}\rm\,K\,cm^{-3}$       | All combined                              |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average cloud-scale equilibrium pressure (Eq. [\[eq:PDEavg\]](#eq:PDEavg)–[\[eq:W_atom\]](#eq:W_atom))                 | $\left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}$                            | $k_\mathrm{B}\rm\,K\,cm^{-3}$       | All combined                              |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average weight of molecular clouds (Eq. [\[eq:W_cloud\]](#eq:W_cloud)&[\[eq:W_cloud_avg\]](#eq:W_cloud_avg))           | $\left<\mathcal{W}_\mathrm{cloud,\,\theta pc}\right>_\mathrm{1kpc}$               | $k_\mathrm{B}\rm\,K\,cm^{-3}$       | All combined                              |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+
| Average weight of clouds due to self-gravity (Eq. [\[eq:W_cloud\]](#eq:W_cloud)&[\[eq:W_cloud_avg\]](#eq:W_cloud_avg)) | $\left<\mathcal{W}^\mathrm{self}_\mathrm{cloud,\,\theta pc}\right>_\mathrm{1kpc}$ | $k_\mathrm{B}\rm\,K\,cm^{-3}$       | PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$  |
+------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+-------------------------------------+-------------------------------------------+

: List of Key Physical Properties

We measure cloud-scale molecular gas properties at two resolutions, 60 pc and 120 pc. Then we derive the CO intensity-weighted average properties in every kpc-sized aperture. In total, our analysis at 120 pc resolution covers 1,762 kpc-sized apertures in all 28 galaxies, whereas the analysis at 60 pc covers a subsample of 344 apertures in 6 galaxies. A collection of key measurements in our analysis are available in tabular form online (see Table [5](#tab:mrt) in Appendix [11](#apdx:mrt)).

We divide our kpc-scale apertures into “disk” apertures and “bulge/bar” apertures, according to the criterion described in Section [3](#sec:method). Our analysis at 120 (60) pc resolution covers 1,445 (294) apertures in which no CO flux originates from bulge or bar regions. When plotting our results, we represent these “disk” apertures in blue, and the “bulge/bar” apertures in orange.

## Turbulent Pressure versus Kpc-scale Dynamical Equilibrium Pressure

The top panels in Figure [1](#fig:Pturb-PDE-kpc) show the average molecular gas turbulent pressure $\left<P_\mathrm{turb,\,\theta pc}\right>$[^9] (see Section [4.1](#sec:expectation:Pturb)), measured on $\theta=60$ pc and $120$ pc scales, as a function of the kpc-scale dynamical equilibrium pressure, $P_\mathrm{DE,\,1kpc}$ (see Section [4.2](#sec:expectation:PDE-kpc)). Each data point corresponds to one kpc-sized aperture. Darker colors denote higher CO flux recovery fraction (see Section [3](#sec:method)), so the $\left<P_\mathrm{turb,\,\theta pc}\right>$ measurements are more representative of the bulk molecular gas population within the aperture.

At a physical scale of 120 pc, we see $\left<P_\mathrm{turb,\,120pc}\right>$ values spanning the range $10^4$–$10^7\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. The corresponding range in $P_\mathrm{DE,\,1kpc}$ is $10^3$–$10^6\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. For reference, the typical GMC internal pressure (i.e., $P_\mathrm{turb}$) in the Solar Neighborhood is $\sim10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ (cite: Blitz_1993), whereas the estimated local dynamical equilibrium pressure is $\sim10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ (cite: Elmegreen_1989). Typical GMC internal pressure in the Galactic Center or nearby galaxy centers is $\sim10^5$–$10^8\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ (cite: Oka_etal_2001; DonovanMeyer_etal_2013; Colombo_etal_2014a; Leroy_etal_2015; Walker_etal_2018; Sun_etal_2018; Schruba_etal_2019). Therefore, one may think of our data as spanning from “outer disk” conditions to galaxy centers.

At both 120 and 60 pc resolution, most data points lie above the equality line (solid black line). This suggests that the average internal pressure in molecular gas is usually higher than what is needed to support the weight of a smooth gas disk with its surface density equals the observed kpc-scale average value.

### Quantifying the Over-pressurization of the Molecular Gas

The pressure excess in the molecular gas is better quantified in the bottom panels in Figure [1](#fig:Pturb-PDE-kpc). There the $y$-axis shows the ratio between $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $P_\mathrm{DE,\,1kpc}$ (i.e., the over-pressurized factor). At 120 pc resolution, 90% of the disk sample shows over-pressurized molecular gas. The majority of the remaining 10% suffers from low CO recovery fraction, and thus we expect these data to be affected by sensitivity-related systematic effects. We find a median over-pressurized factor of 2.8, and a 1$\sigma$ range of 1.3–6.3 at this resolution. At 60 pc resolution, 99% of the disk sample indicates over-pressurized molecular gas. The median and 1$\sigma$ range of the over-pressurized factor is 6.0 and 3.1–12.1, respectively. The difference between the measurements at different resolutions is likely because at 60 pc resolution one can better resolve the denser substructures in molecular gas, which have higher internal pressure.

As mentioned in Section [4.3](#sec:expectation:PDE-cloud), we expect molecular gas to be over-pressurized relative to the expectations for a smooth disk. This is because a significant fraction of molecular gas lives in denser, small-scale substructures, where gravity is locally enhanced. The actual weight of the molecular gas clouds should therefore be higher than the estimation by assuming a smooth disk with the same overall surface density. Given that molecular gas is clumpy at any instant, this argument holds even in a time-averaged sense.

### Predicting Turbulent Pressure from Kpc-scale Equilibrium Pressure

$P_\mathrm{DE,\,1kpc}$ contains no information about the small-scale gas distribution, and thus tends to underestimate the true equilibrium pressure on cloud scales. However, calculating $P_\mathrm{DE,\,1kpc}$ only requires knowing the kpc-scale gas and stellar mass distribution, plus assumptions on the vertical gas velocity dispersion. This makes it possible to estimate $P_\mathrm{DE,\,1kpc}$ in low resolution observations of more distant galaxies, in low resolution numerical simulations, or even from analytic and semi-analytic models of galaxies. If the ISM in other environments follows the same $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$–$P_\mathrm{DE,\,1kpc}$ relation that we observe in Figure [1](#fig:Pturb-PDE-kpc), then one could use an estimated $P_\mathrm{DE,\,1kpc}$ to predict the turbulent pressure on cloud scales.

To make this prediction possible, we fit an empirical $\left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc}$–$P_\mathrm{DE,\,1kpc}$ scaling relation. This can be seen as a benchmark relation for the ISM in local star-forming disk galaxies. We derive this relation by fitting a power-law to all the disk measurements (blue circles in Figure [1](#fig:Pturb-PDE-kpc)), using the ordinary least square (OLS) method in logarithmic space, and treating $P_\mathrm{DE,\,1kpc}$ as the independent variable. This yields best-fit power-law relations (blue dashed lines in Figure [1](#fig:Pturb-PDE-kpc), top panels): $$\begin{align}
    \frac{\left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 3.2 \left(\frac{P_\mathrm{DE,\,1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.07}~, \nonumber\\
    \frac{\left<P_\mathrm{turb,\,60pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 9.0 \left(\frac{P_\mathrm{DE,\,1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.32}~.
    \label{eq:Pturbavg-PDEkpc}
\end{align}$$ We report the scatter around these best-fit relations, and the estimated statistical uncertainties on the fitting parameters in Table [3](#tab:fit).

We caution that Equation [\[eq:Pturbavg-PDEkpc\]](#eq:Pturbavg-PDEkpc) likely has a shallower slope than the actual $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$–$P_\mathrm{DE,\,1kpc}$ relation. This is largely due to the asymmetric data censoring on $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ and $P_\mathrm{DE,\,1kpc}$. The PHANGS-ALMA CO observations have higher surface brightness sensitivity at coarser spatial resolution (cite: Sun_etal_2018). This means that our cloud-scale measurements cannot probe as low molecular gas surface density as our kpc-scale measurements do, and our pressure estimates suffer from a similar censoring effect. The impact of this is even visible in the top left panel in Figure [1](#fig:Pturb-PDE-kpc): there are few data points with $\left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc} \lesssim 10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$, and those few measurements all suffer from low CO recovery fraction. Though not as easily discernible in the top right panel in Figure [1](#fig:Pturb-PDE-kpc), a similar censoring effect is also present at 60 pc resolution.

To quantify how this data censoring biases our empirical $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$–$P_\mathrm{DE,\,1kpc}$ fit, we calculate another version of the best-fit relation using the same OLS method, but only fitting data points with $P_\mathrm{DE,\,1kpc}> 2\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. The impact of the data censoring is much less prominent above this threshold, and thus we expect these fitting results to be less affected. With this fitting strategy, we have (dash-dotted lines in Figure [1](#fig:Pturb-PDE-kpc), top panels) $$\begin{align}
    \frac{\left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 4.0 \left(\frac{P_\mathrm{DE,\,1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.37}~, \nonumber\\
    \frac{\left<P_\mathrm{turb,\,60pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 10 \left(\frac{P_\mathrm{DE,\,1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.47}~.
    \label{eq:Pturbavg-PDEkpc-alt}
\end{align}$$ Again, we report statistical uncertainties and residual scatters in Table [3](#tab:fit).

For the purpose of predicting $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ from $P_\mathrm{DE,\,1kpc}$ in low resolution observations or simulations, we recommend to use Equation [\[eq:Pturbavg-PDEkpc-alt\]](#eq:Pturbavg-PDEkpc-alt) in the regime where $P_\mathrm{DE,\,1kpc}> 2\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. More sensitive observations are needed to pin down this $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$–$P_\mathrm{DE,\,1kpc}$ relation in lower pressure regimes.

## Turbulent Pressure versus Cloud-Scale Dynamical Equilibrium Pressure

In Section [5.1](#sec:result:PDE-kpc) we find that $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ exceeds $P_\mathrm{DE,\,1kpc}$ in almost all regions across our sample. Our hypothesis is that this reflects molecular gas clumping on small scales, which is left unaccounted for in the kpc-scale $P_\mathrm{DE}$ estimate. We directly test this hypothesis in Figure [2](#fig:Pturb-PDE-cloud), where we show the average molecular gas turbulent pressure $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ as a function of the cloud-scale dynamical equilibrium pressure $\left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}$ (as derived in Section [4.3](#sec:expectation:PDE-cloud)). This is a direct “apples to apples” comparison in the sense that both $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$ and $\left<P_\mathrm{DE,\,\theta pc}\right>_\mathrm{1kpc}$ are derived on the same $\theta = 60$ pc and $120$ pc physical scales.

We observe a tight, almost linear relation between $\left<P_\mathrm{turb,\,120pc}\right>$ and $\left<P_\mathrm{DE,\,120pc}\right>$ across more than three orders of magnitude. We find a similarly strong correlation on 60 pc scale, though with a slightly different normalization. Compared to Figure [1](#fig:Pturb-PDE-kpc), the observed distribution in Figure [2](#fig:Pturb-PDE-cloud) shows a relationship much closer to equality (as expected), and much less scatter around the relation as well.

Figure [2](#fig:Pturb-PDE-cloud) shows that: 1) the dynamical equilibrium model is able to predict the observed turbulent pressure in molecular gas based on the resolved gas and stellar mass distribution in galaxy disks; and 2) to correctly estimate equilibrium pressure within the more clumpy molecular component, it is crucial to account for small-scale density structures, which are only accessible in high spatial resolution observations.

### Differentiating Morphological Regions

In Figure [2](#fig:Pturb-PDE-cloud), we differentiate the measurements in galaxy disks (blue circles) from those in bulge and bar regions (orange diamonds). While most disk measurements fall around the equality line, many measurements in bulge or bar regions show systematically higher $\left<P_\mathrm{turb,\,\theta pc}\right>$. This likely reflects a stronger impact of large-scale dynamical processes on the ISM in these regions. As pointed out by (cite: Meidt_etal_2018; Meidt_etal_2019) and many others, the gravitational potential in galaxy bulges and bars often has a steeper gradient, and thus it could significantly perturb the gas motions even on $\sim$100 pc scales. In this case, the gas velocity field is strongly anisotropic, and the observed gas velocity dispersion along the line of sight is elevated by the projected in-plane motions. This could qualitatively explain the higher $\left<P_\mathrm{turb,\,\theta pc}\right>$ relative to $\left<P_\mathrm{DE,\,\theta pc}\right>$ in bulge and bar regions.

While the impact of large-scale dynamical processes on molecular gas properties is itself an interesting and important topic (cite: Kruijssen_Longmore_2013; Kruijssen_etal_2014; Meidt_etal_2018; Meidt_etal_2019; Sormani_etal_2019), further exploration in this direction is beyond the scope of this work. Hereafter, we only focus on measurements in disk regions, in which case the in-plane orbital motions play only a minor role. Future higher resolution observations targeting the central regions of these galaxies, paired with dynamical modelling exercises, will help resolve the remaining ambiguities.

### Quantifying the Turbulent Pressure–Equilibrium Pressure Relation on Cloud Scales

To get a quantitative description of the observed $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ relation, we fit a power-law to all disk measurements (blue dots). We weight each measurement by its corresponding CO recovery fraction $f_\mathrm{CO}$, and perform an OLS bisector fit (cite: Isobe_etal_1990) in logarithmic space. Combining all disk measurements, we find the following best-fit relations on 120 pc and 60 pc scales: $$\begin{align}
    \frac{\left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 0.77 \left(\frac{\left<P_\mathrm{DE,\,120pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.02}~, \nonumber\\
    \frac{\left<P_\mathrm{turb,\,60pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}
    =&\, 1.1 \left(\frac{\left<P_\mathrm{turb,\,60pc}\right>_\mathrm{1kpc}}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{0.95}~.
    \label{eq:Pturbavg-PDEavg}
\end{align}$$ The corresponding statistical uncertainties and residual scatters are reported in Table [3](#tab:fit).

Thanks to both our large sample size and the tightness of the $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ relation, the statistical errors on the best-fit parameters (as quoted in Equation [\[eq:Pturbavg-PDEavg\]](#eq:Pturbavg-PDEavg)) are very small. However, our estimates for $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $\left<P_\mathrm{DE,\,\theta pc}\right>$ do depend on several assumptions, including the CO-to-H$_2$ conversion factor, the geometry of the stellar disk, and the geometry of molecular gas structures on small scales. In Section [6](#sec:systematics), we investigate the systematic uncertainties associated with each of these assumptions.

The normalization of the best-fit $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ relation appears to be different (by a factor of 1.4) when estimated from data at different resolution (also see bottom panels in Figure [2](#fig:Pturb-PDE-cloud)). This can be partly attributed to the overall dependence of CO flux recovery fraction on resolution. As mentioned in Section [5.1](#sec:result:PDE-kpc), the sensitivity is often poorer at higher resolution, which means that only the brightest CO emission remains above the detection limit. For this reason, our estimated turbulent pressure at higher resolution suffers a stronger bias towards the brightest CO peaks, which trace high density, high pressure regions. This can qualitatively explain the mildly higher normalization of the $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ relation at 60 pc resolution.

|  |  |  |  |  |
|:---|:--:|:--:|---:|:--:|
| Relation | Figure/Equation | Slope | Offset along y-axis | Scatter along y-axis |
|  |  |  | at $10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ | around relation |
| $\left<P_\mathrm{turb,\,120pc}\right>$–$P_\mathrm{DE,\,1kpc}$ | Fig.[1](#fig:Pturb-PDE-kpc); Eq. [\[eq:Pturbavg-PDEkpc\]](#eq:Pturbavg-PDEkpc) | $1.07[\pm0.03]\ensuremath{^{*}}$ | $0.50[\pm0.02]\ensuremath{^{*}}$ dex | 0.36 dex |
| $\left<P_\mathrm{turb,\,120pc}\right>$–$P_\mathrm{DE,\,1kpc}$ (debias$^{$\dagger$}$) | Fig.[1](#fig:Pturb-PDE-kpc); Eq. [\[eq:Pturbavg-PDEkpc-alt\]](#eq:Pturbavg-PDEkpc-alt) | $1.37[\pm0.05]\ensuremath{^{*}}$ | $0.60[\pm0.02]\ensuremath{^{*}}$ dex | 0.32 dex |
| $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ | Fig.[2](#fig:Pturb-PDE-cloud); Eq. [\[eq:Pturbavg-PDEavg\]](#eq:Pturbavg-PDEavg) | $1.02[\pm0.01]\ensuremath{^{*}}$ | $-0.12[\pm0.01]\ensuremath{^{*}}$ dex | 0.17 dex |
| $\left<P_\mathrm{turb,\,60pc}\right>$–$P_\mathrm{DE,\,1kpc}$ | Fig.[1](#fig:Pturb-PDE-kpc); Eq. [\[eq:Pturbavg-PDEkpc\]](#eq:Pturbavg-PDEkpc) | $1.32[\pm0.06]\ensuremath{^{*}}$ | $0.96[\pm0.04]\ensuremath{^{*}}$ dex | 0.31 dex |
| $\left<P_\mathrm{turb,\,60pc}\right>$–$P_\mathrm{DE,\,1kpc}$ (debias$^{$\dagger$}$) | Fig.[1](#fig:Pturb-PDE-kpc); Eq. [\[eq:Pturbavg-PDEkpc-alt\]](#eq:Pturbavg-PDEkpc-alt) | $1.47[\pm0.09]\ensuremath{^{*}}$ | $1.00[\pm0.04]\ensuremath{^{*}}$ dex | 0.26 dex |
| $\left<P_\mathrm{turb,\,60pc}\right>$–$\left<P_\mathrm{DE,\,60pc}\right>$ | Fig.[2](#fig:Pturb-PDE-cloud); Eq. [\[eq:Pturbavg-PDEavg\]](#eq:Pturbavg-PDEavg) | $0.95[\pm0.02]\ensuremath{^{*}}$ | $0.06[\pm0.01]\ensuremath{^{*}}$ dex | 0.13 dex |

: Summary of the Best-fit Power-law Relations in Section [5](#sec:result)

Table notes: $^{*}$ All the quoted errors here are *statistical* errors estimated from bootstrapping. However, we expect *systematic* errors to dominate the total uncertainties on these parameters. See Section [6](#sec:systematics). $^{\dagger}$ These relations are derived in the range $P_\mathrm{DE}> 2\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. Caution should be used when extrapolating outside this range.

### Inferring the Dynamical State of Molecular Gas from the ISM Weight Budget

In our formulation (see Section [4.3](#sec:expectation:PDE-cloud) and Appendix [9](#apdx:formulation)), all the terms contributing to the cloud-scale equilibrium pressure $\left<P_\mathrm{DE,\,\theta pc}\right>$ can be grouped into three classes: (1) the weight of the cloud-scale molecular structures due to their self-gravity ($\mathcal{W}^\mathrm{self}_\mathrm{cloud}$; referred to as the “self-gravity term” hereafter); (2) the weight of these molecular structures due to the gravity associated with external material (including both $\mathcal{W}^\mathrm{ext\text{--}mol}_\mathrm{cloud}$ and $\mathcal{W}^\mathrm{star}_\mathrm{cloud}$; referred to as the “external gravity terms”); and (3) the weight of the ambient atomic ISM in the combined potential created by stars and gas ($\mathcal{W}_\mathrm{atom}$; the “ambient pressure term”). The relative importance of these terms offers clues on a key question: which factor plays a more prominent role in governing the dynamical state of molecular structures like GMCs — is it self-gravity, external gravity, or ambient pressure?

The top panels in Figure [3](#fig:frac-PDE) show the fractional contribution of the self-gravity term in the total $\left<P_\mathrm{DE}\right>$ estimate, as a function of dynamical equilibrium pressure estimated on 120 pc scale ($\left<P_\mathrm{DE,120pc}\right>$, top-left panel) and on kpc-scale ($P_\mathrm{DE,\,1kpc}$, top-right panel). We find that the self-gravity term typically accounts for $\sim$33–70% of the total $\left<P_\mathrm{DE}\right>$, and its fractional contribution exceeds $50\%$ in about half of our disk sample. In the other half of our disk sample, the combination of external gravity terms and ambient pressure term dominate the self-gravity term. In this case, the dynamical state of molecular structures like GMCs is strongly influenced by pressure in the ambient atomic ISM, and/or the gravitational potential created by stars and gas external to a given molecular structure.

The black lines and blue shaded regions in Figure [3](#fig:frac-PDE) represent the running median and 16–84% percentile trends. According to the trends shown in the top panels, the relative importance of the self-gravity term in the total ISM weight appears to increase with increasing $\left<P_\mathrm{DE,120pc}\right>$ (rank correlation coefficient $\rho=0.62$, corresponding $p$-value $\ll0.001$), while it correlates less well with $P_\mathrm{DE,\,1kpc}$ ($\rho=0.12$, $p\ll0.001$).

As discussed above, $\left<P_\mathrm{DE,120pc}\right>$ reflects the pressure *within* the molecular gas (as seen by its tight correlation with $\left<P_\mathrm{turb,\,\theta pc}\right>$), whereas $P_\mathrm{DE,\,1kpc}$ represents the pressure in the kpc-scale environment (when neglecting the substructure in the molecular gas). The observed trends in the top two panels in Figure [3](#fig:frac-PDE) can thus be interpreted as follows: across our sample, the dynamical state of cloud-scale molecular gas structures (hereafter “molecular structures”) is strongly related to their internal pressure. Structures with high internal pressure ($\gtrsim10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$) are more likely to be self-gravity-dominated, whereas those with low internal pressure are more likely to be external gravity- and/or ambient pressure-dominated. The large-scale environment pressure, however, offers less predicting power — the correlation is much less monotonic, and the chance of finding self-gravity-dominated molecular structures is about the same in low pressure environments as in high pressure environments within our sample.

The above discussion considers the relative importance of the self-gravity term in the total ISM weight budget. Alternatively, one could focus on the gravity felt by the molecular structures, and ask: “What fraction of the total weight of these structures ($\mathcal{W}_\mathrm{cloud,\,\theta pc}$; see Equation [\[eq:W_cloud\]](#eq:W_cloud)) is due to their self-gravity, as opposed to external gravity?” To address this question, we plot the fractional contribution of the self-gravity term to the total weight of the cloud-scale molecular structures in the bottom panels in Figure [3](#fig:frac-PDE). We find that the self-gravity term dominates the total internal weight of cloud-scale molecular structures in most (83%) of our disk sample. That is, in most cases, the observed molecular structures are dense enough to significantly alter the local gravitational potential. Moreover, in the cases when dynamical equilibrium holds and the ambient pressure is negligible, most of these molecular structures would be self-gravitating.

In the cases when self-gravity fails to outweigh external gravity, however, the molecular structures in question are likely not “significant” over-densities. We do not expect these molecular structures to be decoupled from large-scale dynamics, and if this remains the case, these structures might “dissolve” over roughly a galactic dynamical timescale. This picture is in line with recent findings by (cite: Chevance_etal_2020), that the lifetime of molecular clouds in some cases is driven by the timescales of galactic dynamical processes.

In the bottom panels of Figure [3](#fig:frac-PDE), the contribution of self-gravity to the total weight of molecular structures shows a positive correlation with $\left<P_\mathrm{DE,120pc}\right>$ (bottom-left; rank correlation coefficient $\rho=0.34$, corresponding $p$-value $\ll0.001$), and a very mild negative correlation with $P_\mathrm{DE,\,1kpc}$ (bottom-right; $\rho=-0.07$, $p=0.006$). These trends appear to indicate that molecular structures with high internal pressure and/or in low pressure environments are less likely to be external gravity-dominated.

We note that our estimates of the relative importance of molecular gas self-gravity may be biased by sensitivity and (spatial) resolution related effects. The finite sensitivity of the CO data might introduce a selection bias against low surface density molecular gas in low density, low pressure environments (see discussed in Section [5.1](#sec:result:PDE-kpc)). This selection bias offers a likely alternative explanation for the apparently high $\left<\mathcal{W}^\mathrm{self}_\mathrm{cloud,\,120pc}\right>/\left<P_\mathrm{DE,\,120pc}\right>$ and $\left<\mathcal{W}^\mathrm{self}_\mathrm{cloud,\,120pc}\right>/\left<\mathcal{W}_\mathrm{cloud,\,120pc}\right>$ ratios at the low $P_\mathrm{DE,\,1kpc}$ end (Figure [3](#fig:frac-PDE), right column).

On the other hand, the finite spatial resolution of the CO data means that we do not have access to the sub-beam density distribution of molecular gas. Our assumption of a uniform density sphere filling each beam could lead to under-estimations of $\Sigma_\mathrm{mol}$ and $\left<\mathcal{W}^\mathrm{self}_\mathrm{cloud,\,120pc}\right>$ if the actual sub-beam density distribution is strongly clumped. It is not trivial to predict how this bias would affect the trends we observe in Figure [3](#fig:frac-PDE), because it remains unclear how different cloud/environment properties affect the clumping of molecular gas below these scales. In the future, CO observations with higher sensitivity and higher spatial resolution targeting low pressure environments will help to eliminate these systematic effects.

### A Physical Picture of Molecular Gas Dynamics on Cloud Scales

The results shown in Figure [2](#fig:Pturb-PDE-cloud) and [3](#fig:frac-PDE) together lead to the following conclusions. In a typical star-forming disk environment, the observed turbulent pressure in molecular gas on 60–120 pc scales can be explained by dynamical equilibrium holding down to cloud scales. Molecular structures with high internal pressure ($\left<P_\mathrm{turb}\right>\approx\left<P_\mathrm{DE}\right>\gtrsim10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$) appear more dominated by self-gravity; structures with lower internal pressure appear more heavily influenced by ambient pressure and/or external gravity. We can find structures in either of these two regimes at any environment pressure in our sample.

These observations likely signal an important transition in the dynamical state of cloud-scale molecular structures — with increasing internal pressure and thus increasing pressure contrast against the environment, molecular structures shift from existing at the ambient ISM pressure and participating in the large-scale dynamical motions to being over-pressurized and confined by the enhanced self-gravity (cite: Field_etal_2011; Meidt_2016; Sun_etal_2018; Meidt_etal_2018; Meidt_etal_2019; Schruba_etal_2019). The difference in the range of molecular gas internal pressure and environment pressure probed by our sample allows us to cover both regimes in our analysis.

Our data suggest that dynamical equilibrium on cloud scales holds whether the weight of molecular structures is dominated by self-gravity or not. Our sample spans both types of regimes, and the $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ correlation appears to hold across the whole sample. This strongly supports (a) the idea that cloud-scale molecular structures do appear to exist in dynamical equilibrium (in a statistical averaged sense), and (b) that our formalism captures the relevant physics across the full range of physical conditions probed by our sample.

# Systematic Effects

+:------------------------------------+:----------------------------------------:+:--------------------------------------:+:-------------:+:------------:+:----------------------------------------:+:--------------------------------------------------------------------+
| Methodology Choice                  | 16, 50, 84% Percentiles of                                                        | Best-fit Power-law$^{*}$     | Residual Scatter in                      | Text/Figures                                                        |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
|                                     | $\log\left<P_\mathrm{turb,120pc}\right>$ | $\log\left<P_\mathrm{DE,120pc}\right>$ | Slope $\beta$ | Offset $A$   | $\log\left<P_\mathrm{turb,120pc}\right>$ |                                                                     |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| Fiducial method                     | (4.21, 4.69, 5.26)                       | (4.37, 4.82, 5.36)                     | 1.02          | -0.12 dex    | 0.17 dex                                 | §[5.2](#sec:result:Pturb-PDE-cloud); Fig. [2](#fig:Pturb-PDE-cloud) |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| Galactic $\alpha_\mathrm{CO}$ value | (4.12, 4.61, 5.22)                       | (4.27, 4.70, 5.28)                     | 1.01          | -0.09 dex    | 0.17 dex                                 | §[6.1](#sec:systematics:alphaCO); Fig. [5](#fig:Pturb-PDE-alphaCO)  |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| $\alpha_\mathrm{CO}$ prescription   | (4.46, 4.92, 5.41)                       | (4.72, 5.19, 5.62)                     | 1.08          | -0.26 dex    | 0.17 dex                                 | §[6.1](#sec:systematics:alphaCO); Fig. [5](#fig:Pturb-PDE-alphaCO)  |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| $\alpha_\mathrm{CO}$ prescription   | (4.55, 4.88, 5.29)                       | (4.87, 5.11, 5.41)                     | 1.34          | -0.26 dex    | 0.17 dex                                 | §[6.1](#sec:systematics:alphaCO); Fig. [5](#fig:Pturb-PDE-alphaCO)  |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| Flared stellar disk                 | (4.21, 4.69, 5.26)                       | (4.31, 4.77, 5.34)                     | 0.99          | -0.08 dex    | 0.17 dex                                 | §[6.2](#sec:systematics:PDE)                                        |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+
| Cloud statistics                    | (4.39, 4.79, 5.29)                       | (4.44, 4.80, 5.33)                     | 1.05          | -0.01 dex    | 0.27 dex                                 | §[6.3](#sec:systematics:CPROPS); Fig. [7](#fig:Pturb-PDE-CPROPS)b   |
+-------------------------------------+                                          |                                        |               |              |                                          |                                                                     |
| (fixed l.o.s. depth)                |                                          |                                        |               |              |                                          |                                                                     |
+-------------------------------------+------------------------------------------+----------------------------------------+---------------+--------------+------------------------------------------+---------------------------------------------------------------------+

: $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ Relations Derived from Various Approaches

Table notes: $^{*}$ Here the power-law parameters are defined as $\log_{10}\left(\frac{\left<P_\mathrm{turb,\,120pc}\right>}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right) = \beta\;\log_{10}\left(\frac{\left<P_\mathrm{DE,\,120pc}\right>}{10^5\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right) + A$. Across all rows, the amplitude of variations in the best-fit $\beta$ and $A$ values roughly reflect their systematic uncertainties. For a reference, the corresponding statistical errors are 0.01 for $\beta$, and 0.01 dex for $A$ (see Table [3](#tab:fit)).

Our analysis involves estimates of multiple physical quantities. Deriving these from observables requires making assumptions about, for example, how CO emission traces molecular gas mass (see Section [3](#sec:method)), or the geometry of the stellar disk (see Section [4.2](#sec:expectation:PDE-kpc)). In Section [6.1](#sec:systematics:alphaCO) we consider the impact of our adopted CO-to-H$_2$ conversion factor treatment. In Section [6.2](#sec:systematics:PDE) we vary some of the assumptions that enter into $P_\mathrm{DE}$, testing the effects of a different stellar disk geometry and a different gas velocity dispersion.

Another major methodological choice made in our analysis is that, rather than attempting to identify clouds using any segmentation algorithm, we derive cloud-scale gas properties directly from the observed CO intensity distribution by statistical analysis. In Section [6.3](#sec:systematics:CPROPS) we compare our method with an alternative method that relies on cloud segmentation.

To illustrate how these choices would impact our main results, in Table [4](#tab:systematic) we summarize the $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ relation derived from each alternative approach. Variations of the best-fit power-law slope and intercept among these results provide us with an estimate of the systematic uncertainties on them. The quoted 16, 50, 84% percentiles of $\left<P_\mathrm{turb,\,120pc}\right>$ and $\left<P_\mathrm{DE,\,120pc}\right>$ reveal how each approach impacts these two pressure estimates individually.

## CO-to-H~2~ Conversion Factor

In this work, we adopt a metallicity-dependent $\alpha_\mathrm{CO}$ prescription (see Section [3](#sec:method)), which is similar to the prescription suggested by (cite: Accurso_etal_2017). Quite a few alternative prescriptions exist in the literature (cite: Wolfire_etal_2010; Glover_MacLow_2011; Feldmann_etal_2012; Narayanan_etal_2012; Bolatto_etal_2013). However, none of these prescriptions provides a concrete, observationally tested estimate of $\alpha_\mathrm{CO}$ that simultaneously captures the effects of metallicity, radiation field, and gas dynamics.

Our choice of $\alpha_\mathrm{CO}$ prescription could affect our results. Both $\Sigma_\mathrm{mol}$ and $P_\mathrm{turb}$ are proportional to $\alpha_\mathrm{CO}$, and the molecular gas self-gravity term in $P_\mathrm{DE}$ is proportional to $\alpha_\mathrm{CO}^2$. To estimate the amount of systematic uncertainty associated with the choice of $\alpha_\mathrm{CO}$, we re-derive our key measurements using three alternative $\alpha_\mathrm{CO}$ prescriptions, and compare them with our fiducial prescription. The three alternative prescriptions are: 1) a constant, Galactic conversion factor, 2) a simulation-based $\alpha_\mathrm{CO}$ calibration suggested by (cite: Narayanan_etal_2012), and 3) an empirical $\alpha_\mathrm{CO}$ prescription suggested by (cite: Bolatto_etal_2013).

For the constant $\alpha_\mathrm{CO}$ prescription, we use the Galactic value suggested by : $$\begin{equation}
    \alpha_\mathrm{CO,\,MW} = 4.35\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1}~.
\label{eq:alphaCO_MW}
\end{equation}$$

For the prescription, we predict $\alpha_\mathrm{CO}$ in each kpc-sized aperture from the metallicity ($Z'$) and the flux-weighted CO intensity ($\left<I_\mathrm{CO(1-0)}\right>$), following their equation 11: $$\begin{align}
    \alpha_\mathrm{CO,\,N12} =&\; 8.5\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1} \times Z'^{-0.65} \times \nonumber\\
    & \mathrm{min}\left[1,\;1.7\times \left(\frac{\left<I_\mathrm{CO(1-0)}\right>}{\mbox{$\rm K\,km\,s^{-1}$}}\right)^{-0.32} \right]~.
\label{eq:alphaCO_N12}
\end{align}$$ We note that our implementation includes a factor of 1.36 correction for the mass of heavy elements, which was not included in the original prescription. The quantity $\left<I_\mathrm{CO(1-0)}\right>$ here is estimated from its $\mathrm{CO}\,(2\text{--}1)$ counterpart, $\left<I_\mathrm{CO(2-1),120pc}\right>$, assuming $R_{21}=0.7$.

For the prescription, we predict $\alpha_\mathrm{CO}$ from the metallicity ($Z'$), typical GMC surface density ($\Sigma_\mathrm{GMC}$), and kpc-scale total surface density of both gas and stars ($\Sigma_\mathrm{total}$), following their equation 31: $$\begin{align}
    \alpha_\mathrm{CO,\,B13} =&\; 2.9\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1} \times \nonumber\\
    &\exp\left(\frac{0.4}{Z'\,\Sigma_\mathrm{GMC}^\mathrm{100}}\right) \times \left(\Sigma_\mathrm{total}^\mathrm{100}\right)^{-\gamma}~, \label{eq:alphaCO_B13}\\
    &\text{with}\; \gamma =
    \begin{cases}
        0.5, & \text{if}\ \Sigma_\mathrm{total}^\mathrm{100} > 1 \\
        0. & \text{otherwise}
    \end{cases} \nonumber
\end{align}$$ Here $\Sigma_\mathrm{GMC}^\mathrm{100}$ and $\Sigma_\mathrm{total}^\mathrm{100}$ are the corresponding mass surface densities normalized to $100\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$. Because neither of them could be derived from our observations without knowing $\alpha_\mathrm{CO}$ *a priori*, we set $$\begin{align}
    \Sigma_\mathrm{GMC} &= \frac{\alpha_\mathrm{CO}}{R_{21}} \left<I_\mathrm{CO(2\text{--}1),\,120pc}\right>~, \label{eq:SigGMC}\\
    \Sigma_\mathrm{total} &= \frac{\alpha_\mathrm{CO}}{R_{21}}\, I_\mathrm{CO(2\text{--}1),\,1kpc} + \Sigma_\mathrm{HI,\,1kpc} + \Sigma_\mathrm{star,\,1kpc}~,
\end{align}$$ and then iteratively solve for $\alpha_\mathrm{CO}$ in each kpc-scale aperture. We note that this iterative approach does not guarantee convergence, and 1.5% of the apertures in our sample do not yield a good solution. We discard the measurements for these apertures from this part of the analysis.

Figure [4](#fig:alphaCO-PDF) shows the probability density functions (PDFs) of the predicted $\alpha_\mathrm{CO}$ across our sample for each of the four prescriptions. Our fiducial prescription leads to an $\alpha_\mathrm{CO}$ distribution that peaks around the Galactic value. This agreement is largely by construction, as the fiducial prescription itself is normalized to the Galactic conversion factor at Solar metallicity. The prescription predicts comparatively higher $\alpha_\mathrm{CO}$ values, with the distribution peaking at around $8.5\;\mbox{$\rm M_{\odot}\,pc^{-2}$}\,(\mbox{$\rm K\,km\,s^{-1}$})^{-1}$. This coincides with the “turning point” where the dependency on $\left<I_\mathrm{CO(1-0)}\right>$ switches off (see Equation [\[eq:alphaCO_N12\]](#eq:alphaCO_N12)). Therefore, the location of this peak is likely determined by the prescription itself rather than the input data. The prescription produces a much wider $\alpha_\mathrm{CO}$ distribution compared to the other two distributions. This is attributable to the exponential term in Equation [\[eq:alphaCO_B13\]](#eq:alphaCO_B13), which is a stronger dependence on metallicity than any of the other prescriptions. The prescription also tends to predict higher-than-Galactic $\alpha_\mathrm{CO}$ values. This is likely driven by the relatively low $\Sigma_\mathrm{GMC}$ values implied by Equation [\[eq:SigGMC\]](#eq:SigGMC) (the median value in our sample is $\Sigma_\mathrm{GMC} \approx 30\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$).

We demonstrate how our adopted $\alpha_\mathrm{CO}$ prescription affects our main conclusions in Figure [5](#fig:Pturb-PDE-alphaCO). We show four versions of the $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ relation, each of which corresponds to a different $\alpha_\mathrm{CO}$ prescription. In all four panels, the data clusters around the line of equality. This is because both $\left<P_\mathrm{turb,\,120pc}\right>$ and $\left<P_\mathrm{DE,\,120pc}\right>$ correlate positively with $\alpha_\mathrm{CO}$, and thus the choice of $\alpha_\mathrm{CO}$ prescription has less impact on their ratio. However, the choice of $\alpha_\mathrm{CO}$ prescription does have a more apparent impact on the absolute pressure values. As visible in Figure [5](#fig:Pturb-PDE-alphaCO), the and prescriptions both push the whole distribution towards higher values of both pressures (also see Table [4](#tab:systematic) for quantitative results showing this trend). This is exactly what we would expect from the $\alpha_\mathrm{CO}$ PDFs: predicts on average higher $\alpha_\mathrm{CO}$, and thus higher pressure. tends to predict higher $\alpha_\mathrm{CO}$ in disk regions, which pushes points near the low pressure end up to higher pressures.

For each prescription, we fit a power-law relation to all measurements from disk regions. We report the results in Table [4](#tab:systematic). All $\alpha_\mathrm{CO}$ prescriptions except yield almost linear $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ relations. The prescription instead leads to a super-linear slope of 1.34, with an estimated statistical uncertainty of $\sim$0.01. This is driven by the higher predicted $\alpha_\mathrm{CO}$ in low surface density and low metallicity environments.

In summary, adopting a different $\alpha_\mathrm{CO}$ prescription does not change the conclusion that the observed $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ distribution lies near the equality line. Adopting the prescription makes its slope significantly steeper than linear, while adopting the other three prescriptions all leads to nearly linear slopes. Adopting different prescriptions does significantly change the observed range of both pressures. These results illustrate the importance of quantifying $\alpha_\mathrm{CO}$ variations, and motivate future works to provide better constraints on the potential dependence of $\alpha_\mathrm{CO}$ on key physical properties, including metallicity, radiation field, gas (column) density and dynamics.

## Calculation of Equilibrium Pressure

Calculating $P_\mathrm{DE,\,1kpc}$ and $\left<P_\mathrm{DE,\,\theta pc}\right>$ requires knowing the three dimensional distribution of stars and gas in the galaxy disk. In Sections [4.2](#sec:expectation:PDE-kpc) and [4.3](#sec:expectation:PDE-cloud), we made a few assumptions to help us infer $P_\mathrm{DE,\,1kpc}$ and $\left<P_\mathrm{DE,\,\theta pc}\right>$ from the observed two dimensional projected quantities. In our fiducial approach, we assumed that a) the stellar disk scale height $H_\mathrm{\star}$ is proportional to the radial scale length $R_\mathrm{\star}$, and is not a function of galactocentric radius (i.e., flat stellar disk); and b) the mass-weighted ISM velocity dispersion is the relevant quantity that sets ISM disk scale height, which in turn sets $P_\mathrm{DE}$ near the disk mid-plane. The first assumption is partially motivated by the work by (cite: Kregel_etal_2002), and we provide more support for this assumption in Appendix [10](#apdx:flatratio). In this section, we explore the impact of modifying these two key assumptions.

*Adopted Stellar Disk Geometry:* The assumption of flat stellar disk geometry is widely used in previous works on stellar disk structure (cite: vanderKruit_Searle_1981; Yoachim_Dalcanton_2006; Comeron_etal_2012), and supported by a recent observational study of edge-on disk galaxies (cite: Comeron_etal_2011). We adopt this assumption as the fiducial choice in this paper (see Section [4.2](#sec:expectation:PDE-kpc)).

An alternative, commonly considered possibility is a flared disk geometry (cite: Yang_etal_2007; Ostriker_etal_2010). Here we consider this alternative scenario, and explore whether adopting this alternative affects our conclusion. For this purpose, we re-evaluate $\rho_\mathrm{\star}$ via $$\begin{equation}
    \rho_\mathrm{\star,\,1kpc}^\mathrm{flared} = \frac{\Sigma_\mathrm{\star,\,1kpc}}{0.54R_\mathrm{\star}}\;\exp{\left(1-\frac{r_\mathrm{gal}}{R_\mathrm{\star}}\right)}~.
\label{eq:rhostarkpc_flared}
\end{equation}$$ This assumes that the disk scale height flares exponentially at larger $r_\mathrm{gal}$, which is equivalent to assuming $H_\mathrm{\star}\propto \Sigma_\mathrm{\star}^{-1}$ (cite: Ostriker_etal_2010), and that $\Sigma_\mathrm{\star}$ drops exponentially as a function of $r_\mathrm{gal}$.

The top panel in Figure [6](#fig:PDE-variants) shows the fractional deviation in the $P_\mathrm{DE,\,1kpc}$ estimates, when assuming a flared disk shape instead of a flat shape, as a function of $P_\mathrm{DE,\,1kpc}$. We find that assuming a flared disk geometry mainly leads to lower $P_\mathrm{DE,\,1kpc}$ at the low pressure end. This trend makes sense given the structure of galaxy disks. Low $P_\mathrm{DE,\,1kpc}$ generally corresponds to large $r_\mathrm{gal}$, and the flared disk shape will imply lower $\rho_\mathrm{\star}$ in this regime. However, the amplitude of deviation in $P_\mathrm{DE,\,1kpc}$ is $\lesssim 0.2$ dex in most cases. This suggests that the deviation from a flat disk shape may lead to a factor of $\lesssim1.6$ uncertainty on our $P_\mathrm{DE,\,1kpc}$ estimates.

We also re-evaluate $\left<P_\mathrm{DE,\,120pc}\right>$ assuming a flared stellar disk geometry. The corresponding $\left<P_\mathrm{turb,\,120pc}\right>$–$\left<P_\mathrm{DE,\,120pc}\right>$ relation is quoted in Table [4](#tab:systematic). The changes in the 16, 50, 84% percentiles of $\left<P_\mathrm{DE}\right>$ show that the flared disk scenario gives lower $\left<P_\mathrm{DE}\right>$ estimates compared to the fiducial scenario, and that this deviation is more significant at the low pressure end. This leads to a slightly shallower slope (0.99) and a higher normalization ($-0.08$ dex at $10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$) for the $\left<P_\mathrm{turb}\right>$–$\left<P_\mathrm{DE}\right>$ relation. Nonetheless, the overall impact on the best-fit parameters is not large.

Therefore, the range of $P_\mathrm{DE}$ depends on our assumed stellar disk geometry, but the $\left<P_\mathrm{turb}\right>$–$\left<P_\mathrm{DE}\right>$ relation appears reasonably robust. In the near future, work using data from the Multi Unit Spectroscopic Explorer (MUSE; PI: E. Schinnerer) will provide direct measurements of the stellar velocity dispersion in a subset of our targets. This should help improve our knowledge of the three dimensional stellar disk structure in these targets.

*Adopted Gas Velocity Dispersion:* When calculating the kpc-scale equilibrium pressure in Section [4.2](#sec:expectation:PDE-kpc), we treat the entire ISM as a single component fluid. This motivates us to use the mass-weighted velocity dispersion combining atomic and molecular gas for estimating $P_\mathrm{DE,\,1kpc}$ (Equation [\[eq:siggasz\]](#eq:siggasz)). Many previous studies have instead adopted a fixed velocity dispersion of $\sigma_\mathrm{gas,z} \approx 8\text{--}11\;\mbox{$\rm km\,s^{-1}$}$ (cite: Blitz_Rosolowsky_2004; Blitz_Rosolowsky_2006; Leroy_etal_2008; Hughes_etal_2013a; Ostriker_etal_2010), which is about the mean observed value for atomic gas at moderate galactocentric radii in nearby galaxy disks (cite: Leroy_etal_2008; Tamburro_etal_2009; Caldu-Primo_etal_2013; Mogotsi_etal_2016).

We compare our approach with the fixed $\sigma_\mathrm{gas,z}$ approach, again by comparing their corresponding $P_\mathrm{DE,\,1kpc}$ estimates. As shown in the lower panel in Figure [6](#fig:PDE-variants), assuming a fixed $\sigma_\mathrm{gas,z}=10\;\mbox{$\rm km\,s^{-1}$}$ generally leads to higher $P_\mathrm{DE,\,1kpc}$ in disk regions relative to our fiducial estimates. This is because the observed molecular gas velocity dispersion at 60–120 pc scales is usually less than $10\rm\;km\,s^{-1}$ in the disk regions in our sample, and generally smaller at larger $r_\mathrm{gal}$ (or at low pressure). Nevertheless, the resulting deviation in $P_\mathrm{DE,\,1kpc}$ values is again within 0.2 dex in most cases.

We note that our $\left<P_\mathrm{DE,\,\theta pc}\right>$ estimates treat the molecular and atomic gas separately, and thus do not rely directly on the mass-weighted velocity dispersion (see Section [4.3](#sec:expectation:PDE-cloud)). Therefore, the discussion above does not apply to these cloud-scale estimates.

## Intensity Statistics versus Cloud Segmentation

In Sections [3](#sec:method) and [4](#sec:expectation), we adopt an approach that treats the gas in each pixel separately. This approach, which we refer to as the “pixel statistics approach,” preserves information from the smallest recoverable scale. We use this approach to derive mean cloud-scale gas properties (e.g., $\left<P_\mathrm{turb,\,\theta pc}\right>$) across our sample.

Another popular approach is to segment the observed gas distribution into regions that likely correspond to coherent physical objects. For example, many cloud segmentation algorithms (e.g., CLUMPFIND, (cite: Williams_etal_1994); CPROPS, (cite: Rosolowsky_Leroy_2006)) group individual voxels into cloud-like objects associated with local maxima. Using the voxels associated with each cloud, one can derive cloud size, velocity dispersion, and luminosity, as well as other higher order properties.

From such a cloud catalog, one can derive the mass-weighted mean pressure and similar quantities for clouds in each region of each galaxy. We refer to this segmentation-based calculation as the “cloud statistics” approach. The cloud statistics approach accesses the same physics as our pixel statistics measurements, but differs in two important ways. First, the cloud-based approach treats identified objects, rather than resolution elements, as the fundamental structural unit. Second, the cloud-based approach yields size measurements for each of these objects. Most of the cloud literature assumes spherical symmetry, i.e., the projected size of the objects on the sky is assumed to reflect the depth of the objects along the line of sight.

Our data allow both approaches. In this Section, we re-derive our key measurements using a cloud statistics approach, and then compare the results to those from our pixel statistics measurements.

We use the PHANGS-ALMA CPROPS cloud catalogs, which are derived from the same CO dataset that we use (E. Rosolowsky et al. in preparation; A. Hughes et al. in preparation). Similar to our calculations, these begin with a set of fixed, 120 pc physical resolution data. The algorithm identifies significant, independent local maxima and then associates emission with each maximum. Then it measures the size, CO luminosity, and line width associated with each cloud using moment methods, and corrects for biases due to finite sensitivity and resolution. We note that the PHANGS-ALMA CPROPS application uses the “seeded CLUMPFIND” assignment option in CPROPS. This assigns all significant emission to nearby local maxima, and so represents a hybrid between the default CPROPS assignment and the CLUMPFIND assignment schemes. Otherwise, the calculations, detailed in E. Rosolowsky et al. (in preparation), follow the original CPROPS approach.

Within each kpc-sized aperture, we derive the CO-flux-weighted average turbulent pressure and dynamical equilibrium pressure for all objects identified by CPROPS. To do this, we first write down the expressions for these two quantities using cloud mass, size, and velocity dispersion (i.e., the CPROPS counterparts of Equations [\[eq:Pturb\]](#eq:Pturb) & [\[eq:PDEavg\]](#eq:PDEavg)): $$\begin{align}
    \left<P_\mathrm{turb,\,CPROPS}\right>
    =&\, \left<\frac{3 M_\mathrm{cloud} \sigma_\mathrm{cloud}^2}{4\pi R_\mathrm{cloud}^3}\right>~, \label{eq:Pturb-CPROPS}\\
    \left<P_\mathrm{DE,\,CPROPS}\right>
    =&\, \left<\frac{3\,G M_\mathrm{cloud}^2}{8\pi R_\mathrm{cloud}^4}\right> \nonumber\\
    &+ \left<\frac{G M_\mathrm{cloud}}{2 R_\mathrm{cloud}^2}\right>\Sigma_\mathrm{mol,\,1kpc}\nonumber\\
    &+ \left<\frac{3\,G M_\mathrm{cloud}}{2 R_\mathrm{cloud}}\right>\rho_\mathrm{\star,\,1kpc}\nonumber\\
    &+ \mathcal{W}_\mathrm{atom,\,1kpc}~. \label{eq:PDE-CPROPS}
\end{align}$$ The “$\left<\right>$” symbol here denotes a CO-flux-weighted average over all CPROPS clouds that have their central coordinate inside the kpc-sized aperture in question.

When substituting the measured cloud parameters from CPROPS into Equations [\[eq:Pturb-CPROPS\]](#eq:Pturb-CPROPS) & [\[eq:PDE-CPROPS\]](#eq:PDE-CPROPS), we pay special attention to two caveats. First, we adopt the same metallicity dependent conversion factor for the cloud-based analysis as we do for the pixel statistics (see Section [3.3.1](#sec:method:phys:mol)). Second, the cloud radius quoted in the CPROPS catalogs is defined as 1.91 times the one-dimensional rms size calculated based on the object’s projected intensity distribution on the sky (i.e., following the (cite: Solomon_etal_1987) convention to account for clouds being centrally condensed). To enforce better consistency between the cloud and pixel measurements, we convert the radius quoted by CPROPS ($R_\mathrm{CPROPS}$) to the radius of a hypothesized, constant density spherical cloud via $$\begin{equation}
    R_\mathrm{cloud} = \sqrt{5}\;\frac{R_\mathrm{CPROPS}}{1.91} = 1.17\,R_\mathrm{CPROPS}~.
    \label{eq:R_CPROPS}
\end{equation}$$ Here the factor of $\sqrt{5}$ is the ratio between the radius of a spherical, constant density cloud and its projected rms size on the sky (cite: Rosolowsky_Leroy_2006).

Using the $\alpha_\mathrm{CO}$-corrected cloud mass, the adjusted radius, and the measured velocity dispersion, we derive estimates of $\left<P_\mathrm{turb,\,CPROPS}\right>$ and $\left<P_\mathrm{DE,\,CPROPS}\right>$ via Equations [\[eq:Pturb-CPROPS\]](#eq:Pturb-CPROPS) and [\[eq:PDE-CPROPS\]](#eq:PDE-CPROPS). The left panel in Figure [7](#fig:Pturb-PDE-CPROPS) shows the relation between these two quantities across our sample. We find that almost all data points lie below the equality line. That is, using the cloud statistics approach and assuming spherical symmetry for the objects, we find ubiquitously lower $\left<P_\mathrm{turb,\,CPROPS}\right>$ than $\left<P_\mathrm{DE,\,CPROPS}\right>$. On average, this offset is about 0.66 dex.

To understand this apparent discrepancy between the results from cloud statistics and from pixel statistics, we look into the actual measured sizes of the objects in the CPROPS catalogs. With Equation [\[eq:R_CPROPS\]](#eq:R_CPROPS) applied, the median value of estimated object diameters across PHANGS-ALMA is $\left<2R_\mathrm{cloud}\right> \approx 400$ pc, or about 3 times ($\sim$0.5 dex) larger than the beam size (which is 120 pc in this case).

These apparently large cloud sizes are not out of expectation. Just like many other segmentation algorithms designed to find “clumps,” CPROPS tends to recover structures with sizes comparable to or larger than the beam size. This effect has been long noticed, and discussed by many previous works (cite: Verschuur_1993; Hughes_etal_2013a; Leroy_etal_2016). These objects may be real physical structures (e.g., giant molecular associations or filaments). However, with such large sizes, the assumption of spherical symmetric is unlikely to hold since the $\sim 400$ pc diameters are much larger than the $\sim 100$ pc vertical FWHM of the Milky Way molecular gas disk (cite: Heyer_Dame_2015).

As an ad-hoc correction, we re-derive the values of $\left<P_\mathrm{turb,\,CPROPS}\right>$ and $\left<P_\mathrm{DE,\,CPROPS}\right>$ assuming a modified object geometry. We still use $R_\mathrm{cloud}$ as the projected size of the object on the sky, but now we assume the line of sight depth of the object to be $120$ pc. This matches the assumption used for the pixel statistics estimates. This effectively assumes a cylindrical geometry for the identified objects, with their projected shapes on the sky kept the same, but their depth fixed to a constant value. In practice, this means that we derive the cloud surface density via $\Sigma_\mathrm{cloud} = M_\mathrm{cloud}/(\pi R_\mathrm{cloud}^2)$, and use the cloud surface density, velocity dispersion, and a fixed $D_\mathrm{cloud}=120$ pc in Equations [\[eq:Pturb\]](#eq:Pturb), [\[eq:PDEavg\]](#eq:PDEavg), and [\[eq:W_cloud\]](#eq:W_cloud) to estimate $\left<P_\mathrm{turb,\,CPROPS}\right>$ and $\left<P_\mathrm{DE,\,CPROPS}\right>$.

The right panel in Figure [7](#fig:Pturb-PDE-CPROPS) shows the relation between the “corrected” $\left<P_\mathrm{turb,\,CPROPS}\right>$ and $\left<P_\mathrm{DE,\,CPROPS}\right>$ estimates. In contrast to the results shown in the left panel, we find much better agreement between these “corrected” pressure estimates. The best-fit power-law relation (see Table [4](#tab:systematic)) also becomes much more consistent with the results derived from the pixel statistics approach. These findings suggest that, compared to the spherical symmetry assumption, the assumption of a fixed 120 pc line-of-sight depth is a much better description of the actual geometry of the CPROPS identified objects in the PHANGS-ALMA CO maps.

In summary, the derived $\left<P_\mathrm{turb}\right>$–$\left<P_\mathrm{DE}\right>$ relation from the cloud statistics approach shows consistency with the pixel statistics results, provided that one adopts an appropriate assumption for the geometry of the identified objects. We also emphasize that, when analysing data with marginal spatial resolution, extra caution should be used when interpreting results of cloud identification algorithms like CPROPS.

# Discussion

In Section [5](#sec:result) we show that the prediction from the dynamical equilibrium model quantitatively matches the observed turbulent pressure within the molecular gas. Here we put this dynamical equilibrium consideration into the broader context of star formation and ISM evolution in galaxies.

Motivated by our findings that dynamical equilibrium seems to hold across spatial scales, an obvious next question is how the ISM and the molecular clouds within it maintain such an equilibrium state. What are the underlying mechanisms that regulate turbulent pressure in the ISM, and keep it at a level just enough to support the weight of the gas? Several possibilities have been suggested in the literature, including momentum injection due to stellar feedback (cite: Spitzer_1941b; Thompson_etal_2005; Ostriker_Shetty_2011; Faucher-Giguere_etal_2013) and/or gravitational instability (cite: Krumholz_Burkhart_2016; Ibanez-Mejia_etal_2017; Krumholz_etal_2018). In particular, the former mechanism has been proven successful in explaining many aspects of massive star-forming disks in the local Universe (cite: Leroy_etal_2008; Ostriker_etal_2010; Krumholz_etal_2018). In Section [7.1](#sec:discussion:SFR), we compare our new observations with the predictions from a family of feedback-regulated models developed by (cite: Ostriker_etal_2010) and (cite: Ostriker_Shetty_2011), and synthesized in (cite: Kim_etal_2011).

Beside its major role in regulating the intensity of star formation in galaxy disks, the pressure in the ISM might also affect the evolution of the ISM itself. It has long been suggested that the molecular-to-atomic gas ratio ($R_\mathrm{mol}\equiv\Sigma_\mathrm{mol}/\Sigma_\mathrm{atom}$) of the ISM is partly determined by the ambient ISM pressure (cite: Elmegreen_1993). Many observational works use the dynamical equilibrium pressure $P_\mathrm{DE}$ as a tracer of this ambient pressure, and indeed find a positive correlation between $R_\mathrm{mol}$ and $P_\mathrm{DE}$ (cite: Wong_Blitz_2002; Blitz_Rosolowsky_2006; Leroy_etal_2008). In Section [7.2](#sec:discussion:Rmol), we revisit this topic by characterizing this correlation in our sample, and comparing it to results in previous works (cite: Blitz_Rosolowsky_2006; Leroy_etal_2008).

## Link to the Self-regulated Star Formation Model

In the self-regulated star formation model of (cite: Ostriker_etal_2010; Ostriker_Shetty_2011), an actively star-forming disk is viewed as a (quasi-)steady state system. Stellar feedback of in the form of radiation, winds, and supernovae offsets (in a time-averaged sense) losses of energy and pressure due to cooling and turbulent dissipation. At the same time, pressure maintains (again, in a time-averaged sense) support for the gas against collapse in the gravitational field, balancing both gas self-gravity and external disk gravity. However, a small fraction of the interstellar gas can collapse and form stars locally in regions where support against gravity is insufficient. The result of this localized collapse is the star formation feedback that pressurizes the rest of the ISM, providing internal support. Although this is likely a violent process with alternating episodes of collapse and expansion (cite: Kruijssen_etal_2019b; Rahner_etal_2019; Schinnerer_etal_2019; Chevance_etal_2020), dynamical equilibrium is expected when considering the entire ISM across large spatial scales ($\gg$ typical size of GMCs and star-forming regions) and long time scale ($\gg$ typical lifetime of SF cycle). Numerical simulations indeed show that a well-defined quasi-steady state exists on spatial scales of order $\sim$1 kpc and timescales of a few hundred Myr, even though the star formation rate and the ISM properties strongly vary on short space- and time-scales (cite: Kim_Ostriker_2017; Semenov_etal_2017; Kim_Ostriker_2018; Orr_etal_2018; Semenov_etal_2018).

In this framework, turbulent pressure ($P_\mathrm{turb}$) and dynamical equilibrium pressure ($P_\mathrm{DE}$) are both closely related to a third variable — the local star formation rate surface density, $\Sigma_\mathrm{SFR}$. $P_\mathrm{turb}$ should be directly proportional to $\Sigma_\mathrm{SFR}$ given a fixed momentum injection per star formed (cite: Ostriker_Shetty_2011). Simultaneously, the equilibrium-state $\Sigma_\mathrm{SFR}$ is determined by requiring the sum of turbulent, thermal and magnetic pressures (individually proportional to $\Sigma_\mathrm{SFR}$ due to feedback) to balance $P_\mathrm{DE}$ (cite: Ostriker_etal_2010; Kim_etal_2011). Here we explore this scenario by showing the relationships between $P_\mathrm{turb}$ and $\Sigma_\mathrm{SFR}$, and between $\Sigma_\mathrm{SFR}$ and $P_\mathrm{DE}$.

### SFR Surface Density versus Turbulent Pressure

The left panel in Figure [8](#fig:SigSFR) shows the measured cloud-scale average turbulent pressure in molecular gas, $\left<P_\mathrm{turb,\,\theta pc}\right>_\mathrm{1kpc}$, as a function of the kpc-scale average SFR surface density, $\Sigma_\mathrm{SFR,\,1kpc}$. We observe strong correlation between these two quantities. For all measurements in disk regions (blue dots), we find a rank correlation coefficient of $\rho = 0.71$ (corresponding p-value $\ll0.001$).

In the case that the ISM pressure is feedback-driven, the ratio between ISM turbulent pressure and SFR surface density – where these are averages computed over the same area – reflects to the momentum injection per unit mass of stars formed, $p_\star/m_\star$, via $$\begin{equation}
    P_\mathrm{turb}= \frac{1}{4}\frac{p_\star}{m_\star}\,\Sigma_\mathrm{SFR}~.
\end{equation}$$ The pre-factor of $1/4$ assumes spherical expansion sites centered on the disk midplane and that the momentum flux to upper and lower halves of the ISM disk translates directly to ISM turbulent pressure (cite: Ostriker_Shetty_2011). While the above picture is idealized and should be modified by details of turbulent injection and dissipation, it quantitatively agrees with the measured relationship between $P_\mathrm{turb}$ and $\Sigma_\mathrm{SFR}$ in disk simulations of the star-forming multi-phase ISM (cite: Kim_etal_2013; Kim_Ostriker_2015b; Kim_Ostriker_2017).

The ratio $p_*/m_*$ is predicted to range between $10^3$–$10^4\;\mbox{$\rm km\,s^{-1}$}$ for supernova feedback, depending on the ISM properties, spatial and temporal clustering of supernovae, and energy losses due to interface mixing (cite: Iffrig_Hennebelle_2015; Kim_Ostriker_2015a; Martizzi_etal_2015; Walch_Naab_2015; Kim_etal_2017; El-Badry_etal_2019; Gentry_etal_2019). In Figure [8](#fig:SigSFR), we show the predicted $P_\mathrm{turb}$–$\Sigma_\mathrm{SFR}$ relation for a range of $p_\star/m_\star$ values (dotted lines). Our observed $\left<P_\mathrm{turb,\,120pc}\right>$–$\Sigma_\mathrm{SFR,\,1kpc}$ relation has a normalization that would correspond to a high momentum injection.

One possible explanation for this apparently high momentum injection rate is the clumping of the star formation distribution. Unlike $\left<P_\mathrm{turb,\,120pc}\right>$, which is estimated on 120 pc scales and then averaged over the kpc-scale aperture, our $\Sigma_\mathrm{SFR,\,1kpc}$ measurements are derived directly on kpc scale. Just like the molecular gas, we expect star formation to cluster on sub-kpc scales (cite: Grasha_etal_2018; Grasha_etal_2019; Schinnerer_etal_2019; Chevance_etal_2020). This will cause the $\Sigma_\mathrm{SFR,\,1kpc}$ values in Figure [8](#fig:SigSFR) to appear lower due to the inclusion of area without star formation, and thus it underestimates the actual SFR surface density relevant to feedback momentum injection.

To account for this issue, we introduce a dimensionless prefactor $C_\mathrm{fb}\gtrsim1$, which corrects for the artificial dilution of $\Sigma_\mathrm{SFR,\,1kpc}$ compared to $\Sigma_\mathrm{SFR,\,\theta pc}$. Then we have $$\begin{equation}
    \left<P_\mathrm{turb,\,120pc}\right>_\mathrm{1kpc} = C_\mathrm{fb}\,\frac{p_\star}{4m_\star}\,\Sigma_\mathrm{SFR,\,1kpc}~.
\end{equation}$$ The median value of $C_\mathrm{fb}\,p_\star/m_\star$ among the disk sample is $6.3\times10^3\;\mbox{$\rm km\,s^{-1}$}$, and its 16–84% percentile range is 0.73 dex.

A direct estimation of $C_\mathrm{fb}$ requires high resolution data tracing SFR on matched $\sim10\text{--}100$ pc scales. This is currently not available for our entire sample (cite: Kreckel_etal_2018; Schinnerer_etal_2019; Chevance_etal_2020). However, we can obtain a rough estimate of $C_\mathrm{fb}$ based on our high resolution CO data, if we assume that the clustering of star formation matches that of the molecular gas. Given a median area filling fraction of $\approx1/3$ in our CO data, we expect $C_\mathrm{fb} \approx 3$. In this case, most of the $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $\Sigma_\mathrm{SFR,\,1kpc}$ measurements in the disk sample are consistent with $p_\star/m_\star = 10^3\text{--}10^4\;\mbox{$\rm km\,s^{-1}$}$.

There are many caveats related to this approximate estimation of $C_\mathrm{fb}$. The spatial and temporal distribution of gas and star formation could change the amount of momentum injected into the gas, and the spatial scales on which most momentum is deposited also matters. Given these complications, a logical next step on this topic will be a detailed, multi-scale comparison between observations of gas and star formation at high resolution and numerical simulations with realistic feedback prescriptions.

An alternative explanation for the high $P_\mathrm{turb}/\Sigma_\mathrm{SFR}$ ratio measurements in Figure [8](#fig:SigSFR) (left panel) is that other turbulence driving mechanisms might also play a role, at least within a subset of our sample. For example, many measurements in bulge or bar regions show the highest $P_\mathrm{turb}$ at fixed $\Sigma_\mathrm{SFR}$ (orange symbols in Figure [8](#fig:SigSFR), left panel). While part of this can be explained by beam smearing effects, we also expect bar-induced radial inflow and the corresponding conversion of gravitational potential energy to be an additional source of turbulence in the ISM (cite: Binney_etal_1991; Sormani_etal_2015). More quantitative comparisons between our results and other turbulent driving mechanisms will be carried out in future works.

### Equilibrium Pressure versus SFR Surface Density

The right panel in Figure [8](#fig:SigSFR) shows kpc-scale SFR surface density, $\Sigma_\mathrm{SFR,\,1kpc}$, as a function of kpc-scale dynamical equilibrium pressure, $P_\mathrm{DE,\,1kpc}$. We find a strong correlation between the two quantities for all measurements in disk regions. This supports the idea that in steadily star-forming disks, the three dimensional star and gas distribution on kpc-scale largely determines the average SFR surface density on the same scale. In any part of the disk where the ISM weight is higher, the steady-state SFR must also increase for feedback to maintain the pressure that matches the dynamical equilibrium pressure.

To quantify this observed correlation, we derive a best-fit power-law relation for all disk measurements, using the OLS bisector method in logarithmic space: $$\begin{equation}
    \frac{\Sigma_\mathrm{SFR}}{10^{-3}\;\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}} = 3.2\, \left(\frac{P_\mathrm{DE}}{10^4\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{0.84}~.
    \label{eq:SigSFR-PDE}
\end{equation}$$ The rms scatter in $\Sigma_\mathrm{SFR}$ around this relation is 0.20 dex. The statistical errors estimated from bootstrapping are 0.01 for the slope and 0.01 dex for the normalization, but we expect systematic errors (on both $\Sigma_\mathrm{SFR,\,1kpc}$ and $P_\mathrm{DE,\,1kpc}$) to be a larger source of uncertainty on the fitting results.

The same correlation has been observed in various types of galaxies by many previous studies (cite: Leroy_etal_2008; Genzel_etal_2010; Ostriker_etal_2010; Ostriker_Shetty_2011; Herrera-Camus_etal_2017; Fisher_etal_2019). To put our measurements into context, we also include in Figure [8](#fig:SigSFR) two other datasets derived also from observations of nearby galaxies. (cite: Leroy_etal_2008) (brown crosses) measure this relation in a sample of 23 nearby galaxies, with each independent measurement representing one kpc-wide radial bin in a galaxy. (cite: Herrera-Camus_etal_2017) (green plus symbols) investigate the same relation in the HI dominated regions in 31 KINGFISH galaxies (cite: Kennicutt_etal_2011), treating each kpc-sized region independently.

These previous works adopted slightly different assumptions when deriving $P_\mathrm{DE}$ from observables. To make a fair comparison between our measurements and theirs, our $P_\mathrm{DE,\,1kpc}$ measurements shown in Figure [8](#fig:SigSFR) are instead derived by assuming $\sigma_\mathrm{gas,\,z}= 11\;\mbox{$\rm km\,s^{-1}$}$, following exactly the same prescription in (cite: Leroy_etal_2008) and (cite: Herrera-Camus_etal_2017) (also see Section [6.2](#sec:systematics:PDE)). We find overall consistency, but our measurements concentrate more towards the high $P_\mathrm{DE}$, high $\Sigma_\mathrm{SFR}$ end. This is because the PHANGS-ALMA CO observations primarily target the star-forming inner part of high mass disk galaxies, while the (cite: Herrera-Camus_etal_2017) sample focuses on the HI-dominated outer disks on purpose, and the (cite: Leroy_etal_2008) sample includes many dwarf galaxies.

In addition to previous observational results, we also show in Figure [8](#fig:SigSFR) the predicted $P_\mathrm{DE}$–$\Sigma_\mathrm{SFR}$ relation from a hydrodynamic simulation (cite: Kim_etal_2013): $$\begin{equation}
    \frac{\Sigma_\mathrm{SFR}}{10^{-3}\;\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}} = 1.8 \,\left(\frac{P_\mathrm{DE}}{10^4\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}}\right)^{1.13}~.
    \label{eq:SigSFR-PDE-Kim13}
\end{equation}$$ This relation has a steeper slope than our best-fit power-law relation (Equation [\[eq:SigSFR-PDE\]](#eq:SigSFR-PDE)), while it agrees with previous observations in the low $\Sigma_\mathrm{SFR}$ regime. We point out that the simulations in (cite: Kim_etal_2013) cover a $\Sigma_\mathrm{SFR}$ range from $10^{-4}$ to $10^{-2}\;\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}$, whereas our sample covers from $10^{-3}$ to $10^{-1}\;\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}$. The shallower slope found in our sample might then reflect some systematic change in the properties of the ISM in massive galaxies and inner disk environments, relative to the ISM in dwarf galaxies and/or outer disk environments.

A shallower $P_\mathrm{DE}$–$\Sigma_\mathrm{SFR}$ relation in high $\Sigma_\mathrm{SFR}$ environments is seen in several previous works. In the (cite: Leroy_etal_2008) sample, some hint of a shallower $\Sigma_\mathrm{SFR}$–$P_\mathrm{DE}$ relation is visible from the high $\Sigma_\mathrm{SFR}$ measurements. For a sample of local ultra luminous infra-red galaxies (ULIRGs) and high-redshift star-forming galaxies, (cite: Ostriker_Shetty_2011) found a $\Sigma_\mathrm{SFR}$–$P_\mathrm{DE}$ relation with a slope of 0.95 at $P_\mathrm{DE}> 10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$, which is closer to our result[^10]. More recently, (cite: Fisher_etal_2019) report a much shallower slope of 0.77 at $P_\mathrm{DE}\gtrsim 10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ for a sample of local turbulent disk galaxies[^11], which are believed to resemble typical star-forming galaxies at $z \sim 1\text{--}2$. Future studies on the ISM in more local ULIRGs and galaxy centers can provide better constraints on the slope of the $\Sigma_\mathrm{SFR}$–$P_\mathrm{DE}$ relation at the high $\Sigma_\mathrm{SFR}$ end, and potentially help unveil the physics regulating star formation in the “starburst” regime (cite: Thompson_etal_2005; Ostriker_Shetty_2011; Shetty_Ostriker_2012; Crocker_etal_2018; Krumholz_etal_2018).

## Link to the Molecular-to-Atomic Gas Ratio

Following early suggestions by (cite: Elmegreen_1989), the ISM dynamical equilibrium pressure has also been viewed as a determinant of the molecular/atomic phase balance in the ISM. In this scenario, $P_\mathrm{DE}$ relates closely to the molecular-to-atomic gas ratio, $R_\mathrm{mol}$, and thus influences the fraction of the ISM in the dense, star-forming phase. This idea has been tested by many subsequent works (cite: Wong_Blitz_2002; Blitz_Rosolowsky_2006; Leroy_etal_2008), and commonly adopted as a prescription for determining the molecular gas fraction in semi-analytic models of galaxy evolution (cite: Lagos_etal_2018). Here we report the observed scaling relation between molecular-to-atomic ratio and the ISM dynamical equilibrium pressure across our sample.

Following previous studies, we use the kpc-scale dynamical equilibrium pressure $P_\mathrm{DE,\,1kpc}$ to trace the average ambient pressure in the ISM. To allow a quantitative comparison with previous results, we again use the $P_\mathrm{DE,\,1kpc}$ values estimated by assuming a fixed $\sigma_\mathrm{gas,\,z}=11\,\mbox{$\rm km\,s^{-1}$}$ (similar to Section [7.1.2](#sec:discussion:SFR:PDE)). We determine the molecular-to-atomic gas ratio from the ratio of our measured molecular and atomic gas surface densities on kpc-scale: $$\begin{equation}
    R_\mathrm{mol,1kpc} \equiv \Sigma_\mathrm{mol,\,1kpc}/ \Sigma_\mathrm{atom,\,1kpc}~.
\end{equation}$$

We show the relation between $P_\mathrm{DE,\,1kpc}$ and $R_\mathrm{mol,1kpc}$ in Figure [9](#fig:Rmol-PDE). Our sample spans nearly two orders of magnitude in $R_\mathrm{mol,\,1kpc}$, with most measurements clustering around or above the atomic-to-molecular transition threshold (i.e., $R_\mathrm{mol,\,1kpc}=1$). We find a positive and statistically significant correlation between $R_\mathrm{mol,\,1kpc}$ and $P_\mathrm{DE,\,1kpc}$ across our whole sample (Spearman’s rank correlation coefficient $\rho=0.58$; corresponding p-value $\ll0.001$). This strong, positive correlation is qualitatively consistent with previous observations (cite: Wong_Blitz_2002; Blitz_Rosolowsky_2006; Leroy_etal_2008), even though the adopted CO-to-H$_2$ conversion factor, stellar mass-to-light ratio, and stellar disk geometry vary among studies.

We perform an OLS bisector fit on all our disk measurements over the range $0.1 < R_\mathrm{mol,\,1kpc} < 10$, following (cite: Leroy_etal_2008). This yields a best-fit power-law relation (blue solid line in Figure [9](#fig:Rmol-PDE)) of $$\begin{equation}
    R_\mathrm{mol,\,1kpc} = \left( \frac{P_\mathrm{DE,\,1kpc}}{2.1\times10^4\;\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}} \right)^{1.02}~.
    \label{eq:Rmol-PDE}
\end{equation}$$ The scatter in $R_\mathrm{mol,\,1kpc}$ around this relation is 0.36 dex. The formal statistical errors in the fit are small: 0.02 for the slope $\alpha$, and 0.01 dex for the threshold pressure $P_0=2.1\times10^4\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ (at which the ISM transitions from being predominantly atomic to molecular, or vice versa). However, when varying the choice of $\alpha_\mathrm{CO}$ prescriptions and other assumptions, the best-fit $\alpha$ and $P_0$ appear systematically uncertain by $\sim0.20$ and $\sim0.15$ dex, respectively. Given this level of systematic uncertainty, Equation [\[eq:Rmol-PDE\]](#eq:Rmol-PDE) quantitatively agrees with the $R_\mathrm{mol}$–$P_\mathrm{DE,\,1kpc}$ relations reported in previous works (cite: Wong_Blitz_2002; Blitz_Rosolowsky_2006; Leroy_etal_2008).

# Summary

For a sample of 28 nearby star-forming disk galaxies, we estimate the pressure needed to support the ISM against its own weight at a range of spatial scales, taking into account the combined gravity of all gas components and the stellar disk. We compare this estimated “dynamical equilibrium pressure” to the observed turbulent pressure in molecular gas. This tests the common hypothesis that the ISM in star-forming galaxy disks is in dynamical equilibrium.

For this purpose, we create a multi-wavelength dataset, which includes high resolution PHANGS-ALMA $\mathrm{CO}\,(2\text{--}1)$ imaging data (A. K. Leroy et al., in preparation) and GMC catalogs (E. Rosolowsky et al., in preparation; A. Hughes et al., in preparation), new and archival HI 21 cm data (D. Utomo et al., in preparation), processed *Spitzer* IRAC 3.6 $\mu$m data (cite: Querejeta_etal_2015), and combined GALEX near-UV and WISE mid-IR data (cite: Leroy_etal_2019). These data provide us with a comprehensive picture of the molecular gas distribution and kinematics on $\sim60$–$120$ pc scales (i.e., cloud scales), and the distribution of gas mass, stellar mass, and star formation rate on $\sim1$ kpc scale.

We divide the 28 galaxies in our sample into 1,762 independent, kpc-sized hexagonal regions, covering the PHANGS-ALMA CO footprint. In each kpc-sized region, we use the high resolution CO data to calculate the mass-weighted mean turbulent pressure in molecular gas, $\left<P_\mathrm{turb,\,\theta pc}\right>$ ($\theta=60$ and $120$ pc; see Section [4.1](#sec:expectation:Pturb)). We then compare $\left<P_\mathrm{turb,\,\theta pc}\right>$ to the required pressure to balance the weight of the ISM disk in the galaxy gravitational potential, a.k.a., the dynamical equilibrium pressure, $P_\mathrm{DE}$.

Building on earlier works (cite: Hughes_etal_2013a; Schruba_etal_2019), we compute two different measures of $P_\mathrm{DE}$. One measure, widely adopted in previous studies, represents the expected mean mid-plane ISM pressure averaged over all gas, and implicitly assumes no bound sub-structures. The other measure considered in this work represents the pressure expected within individual resolved molecular structures on 60–120 pc scales, allowing them to be self-gravitating.

The first estimate assumes uniform gas surface density within each kpc-sized aperture. This provides a measure of equilibrium pressure on kpc-scale, $P_\mathrm{DE,\,1kpc}$ (see Section [4.2](#sec:expectation:PDE-kpc)). With this measure, we find that:

1.  $P_\mathrm{DE,\,1kpc}$ ranges from $10^3$ to $10^6\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$ across our sample. This agrees well with previous estimates of the average ISM pressure in galaxy disks. The lower bound roughly corresponds to Solar Neighborhood-like environments, whereas the higher bound corresponds to conditions found in gas-rich galaxy centers.

2.  The mass-weighted turbulent pressure $\left<P_\mathrm{turb,\,\theta pc}\right>$ ranges from $10^4$ to $10^7\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$. $\left<P_\mathrm{turb,\,\theta pc}\right>$ correlates with $P_\mathrm{DE,\,1kpc}$, but it almost always exceeds the $P_\mathrm{DE,\,1kpc}$ estimate in the same region (Figure [1](#fig:Pturb-PDE-kpc)). At 120 pc scale, we measure an average $\left<P_\mathrm{turb,\,\theta pc}\right>/P_\mathrm{DE,\,1kpc}$ ratio of $\sim 2.8$ across our sample. That is, molecular gas appears highly over-pressurized compared to the mean $P_\mathrm{DE,\,1kpc}$ calculated assuming a *smooth* ISM distribution in each kpc-sized aperture.

3.  We fit a relation between $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $P_\mathrm{DE,\,1kpc}$ (Equation [\[eq:Pturbavg-PDEkpc-alt\]](#eq:Pturbavg-PDEkpc-alt)) that can be used to predict cloud-scale molecular gas properties from kpc-resolution observation of distant galaxies, from low resolution galaxy simulations, or from analytic or semi-analytic models of star-forming galaxy disks.

In reality, the molecular ISM is highly clumped, and self-gravity plays an important role in dynamical equilibrium. Indeed, the molecular gas distribution traced by PHANGS-ALMA on 60–120 pc scales does display this rich substructure. The presence of this substructure means that $P_\mathrm{DE,\,1kpc}$ under-estimates the required pressure for the clumpy molecular gas to achieve dynamical equilibrium, because it does not account for the enhancement of gas self-gravity in over-densities.

We thus introduce a formalism which explicitly incorporates knowledge about molecular gas clumping, and considers the self-gravity of the molecular gas, the external gravitational potential, and the pressure in the ambient ISM in a unified framework. This provides a measure of the equilibrium pressure on cloud scales, $\left<P_\mathrm{DE,\,\theta pc}\right>$ (see Section [4.3](#sec:expectation:PDE-cloud)).

Applying this formalism, we find that:

4.  Accounting for the enhanced gas self-gravity due to clumping at small scales, we estimate that the pressure needed to support the gas is $\left<P_\mathrm{DE,\,\theta pc}\right>=10^4$–$10^8\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$, systematically higher than the kpc-scale estimates of $P_\mathrm{DE,\,1kpc}$.

5.  $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $\left<P_\mathrm{DE,\,\theta pc}\right>$ are nearly equal across most regions in our sample (Figure [2](#fig:Pturb-PDE-cloud)). This is consistent with the idea that molecular clouds have internal pressures close to the value needed to balance the sum of their own internal weight and the weight of the ambient atomic gas.

6.  In our sample, the self-gravity of cloud-scale molecular gas structures accounts for $\sim 33-70\%$ of the total $\left<P_\mathrm{DE,\,\theta pc}\right>$. For the molecular gas at high internal pressure ($\gtrsim10^5\,\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}$), $\left<P_\mathrm{DE,\,\theta pc}\right>$ is more likely to be dominated by the self-gravity term. Gas at low internal pressure is more likely to be affected by ambient pressure and/or external gravity (Figure [3](#fig:frac-PDE)). However, we observe large scatter about this general trend, and we see examples for both scenarios across all environments.

We explore the systematic effects associated with key assumptions (Section [6](#sec:systematics)). We (1) vary the adopted CO-to-H$_2$ conversion factors in a reasonable range, (2) choose different assumptions for the stellar disk geometry and/or gas vertical velocity dispersion, and (3) adopt an alternative, cloud statistic approach utilizing the PHANGS-ALMA CPROPS cloud catalogs. We find that varying these assumptions changes the range of the derived pressure estimates, but does not affect our qualitative conclusion of a strong, nearly unity correlation between $\left<P_\mathrm{DE,\,\theta pc}\right>$ and $\left<P_\mathrm{turb,\,\theta pc}\right>$. Our quantitative measurements do show mild variations due to these systematic effects, which we report in Table [4](#tab:systematic).

Based on our analysis and tests of systematic effects, our most general conclusion is that:

7.  A close-to-unity $\left<P_\mathrm{turb,\,\theta pc}\right>$–$\left<P_\mathrm{DE,\,\theta pc}\right>$ relation holds across different physical regimes, and is robust against many systematic effects. In other words, the molecular gas in the disk regions of nearby, massive, star-forming galaxies does appear to be in or near a state of dynamical equilibrium.

Beside testing the assumption of dynamical equilibrium, we also investigate the driving mechanism of this equilibrium. We find that the observed kpc-scale SFR surface density $\Sigma_\mathrm{SFR}$ shows a strong correlation with both $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $P_\mathrm{DE,\,1kpc}$ (Figure [8](#fig:SigSFR)). The ratio between $\left<P_\mathrm{turb,\,\theta pc}\right>$ and $\Sigma_\mathrm{SFR,\,1kpc}$ is generally consistent with the expected range of momentum injection from supernova feedback, if one considers the clumping of star formation on small scales. The nearly linear relationship between $\Sigma_\mathrm{SFR,\,1kpc}$ and $P_\mathrm{DE,\,1kpc}$ is consistent with the feedback-regulated scenario, and in quantitative agreement with previous observational and theoretical studies where the parameter regimes overlap. We show that $P_\mathrm{DE,\,1kpc}$ correlates positively with the molecular to atomic ratio, $R_\mathrm{mol,\,1kpc}$ (Figure [9](#fig:Rmol-PDE)). The best-fit relation we find (Equation [\[eq:Rmol-PDE\]](#eq:Rmol-PDE)) is consistent with those reported in previous studies (cite: Blitz_Rosolowsky_2006; Leroy_etal_2008).

We publish the estimated $P_\mathrm{turb}$, $P_\mathrm{DE}$, $\Sigma_\mathrm{SFR}$, and $R_\mathrm{mol}$ across our full sample in machine-readable form (see Table [5](#tab:mrt) in Appendix [11](#apdx:mrt)). We encourage the use of this dataset as a benchmark for future observations and numerical simulations.

In the near future, it will be possible to extend these measurements from the disks of massive spiral galaxies to a wider set of environments. Sensitive CO observations targeting dwarf galaxies and the outer disks of spiral galaxies will reveal whether a similar equilibrium holds in the atomic gas- and/or external pressure-dominated regimes. A more careful treatment of in-plane motions and a better modeling of the three-dimensional distribution and kinematics of the stellar component will provide better understanding of dynamical equilibrium in early-type galaxies, galaxy bulges, and central regions.

# Acknowledgments

We thank the anonymous referee for helpful comments that improved the quality of the paper. J.S. would like to thank R. Herrera-Camus and C. Murugeshan for kindly sharing their data, and D. Fisher and T. A. Thompson for helpful discussions.

This work was carried out as part of the PHANGS collaboration. The work of J.S., A.K.L., and D.U. is partially supported by the National Science Foundation under Grants No. 1615105, 1615109, and 1653300. The work of E.C.O. was partly supported by NASA under ATP Grant NNX17AG26G. A.H., C.N.H., and J.P. acknowledge funding from the Programme National “Physique et Chimie du Milieu Interstellaire (PCMI)” of CNRS/INSU with INC/INP, co-funded by CEA and CNES, and from the “Programme National Cosmology et Galaxies (PNCG)” of CNRS/INSU with INP and IN2P3, co-funded by CEA and CNES. E.R. acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC), funding reference number RGPIN-2017-03987. E.S., C.F., and T.S. acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). J.M.D.K. and M.C. gratefully acknowledge funding from the Deutsche Forschungsgemeinschaft (DFG) through an Emmy Noether Research Group (grant number KR4801/1-1) and the DFG Sachbeihilfe (grant number KR4801/2-1). J.M.D.K. gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). F.B. acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 726384). S.C.O.G. acknowledges support by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) – Project-ID 138713538 – SFB 881 (“The Milky Way System”, sub-projects B01, B02, B08), and by the Heidelberg cluster of excellence EXC 2181-390900948 “STRUCTURES: A unifying approach to emergent phenomena in the physical world, mathematics, and complex data”, funded by the German Excellence Strategy. A.U. acknowledges support from the Spanish funding grants AYA2016-79006-P (MINECO/FEDER) and PGC2018-094671-B-I00 (MCIU/AEI/FEDER).

This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, and 2018.1.01321.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work is based in part on observations made with NSF’s Karl G. Jansky Very Large Array (Legacy ID: AS 1303, AS1387, AS1434, AU157). VLA is also operated by the National Radio Astronomy Observatory.

This work is based in part on observations made with the Australia Telescope Compact Array (ATCA). ATCA is part of the Australia Telescope National Facility, which is funded by the Australian Government for operation as a National Facility managed by CSIRO.

This work is based in part on observations made with the Spitzer Space Telescope, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

This work is based in part on observations made with the Galaxy Evolution Explorer (GALEX). GALEX is a NASA Small Explorer, whose mission was developed in cooperation with the Centre National d’Etudes Spatiales (CNES) of France and the Korean Ministry of Science and Technology. GALEX is operated for NASA by the California Institute of Technology under NASA contract NAS5-98034.

This publication makes use of data products from the Wide-field Infrared Survey Explorer (WISE), which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by the National Aeronautics and Space Administration.

We acknowledge the usage of the Extragalactic Distance Database[^12] (cite: Tully_etal_2009), the HyperLeda database[^13] (cite: Makarov_etal_2014), the NASA/IPAC Extragalactic Database[^14], and the SAO/NASA Astrophysics Data System[^15].

# Facilities

ALMA, VLA, ATCA, Spitzer, WISE, GALEX

# Software

`CASA` (cite: McMullin_etal_2007), `Astropy` (cite: AstropyCollaboration_etal_2013; AstropyCollaboration_etal_2018)

# Dynamical Equilibrium on Cloud Scales

In Section [4.3](#sec:expectation:PDE-cloud), we determine the cloud-scale dynamical equilibrium pressure in molecular gas, $\left<P_\mathrm{DE,\,\theta pc}\right>$, by adding up the weight of molecular clouds and the ambient atomic gas in the total gravitational potential. Here we provide a detailed derivation for each of the constituent terms included in this calculation.

As illustrated by Figure [10](#fig:model), we approximate the ISM in a galaxy disk as comprised of two components: 1) a thin, clumpy layer of molecular gas near the disk mid-plane, which includes many denser molecular clouds in it, and 2) a smooth, plane-parallel atomic gas outer layer “sandwiching” the molecular gas layer. We further assume that the vertical scale height of the molecular gas ($H_\mathrm{mol}$) and the atomic gas ($H_\mathrm{atom}$) are both much smaller than that of the stellar disk ($H_\mathrm{\star}$), with $H_\mathrm{mol}<H_\mathrm{atom}$. With this setup, we can consider an arbitrary molecular cloud in the molecular layer. To compute the equilibrium pressure at the center of the cloud, we first integrate the weight of the cloud from its center to its edge along the vertical direction, and then integrate the weight of the atomic gas above the cloud.

## The Weight of a Molecular Cloud

The weight of a cloud, $\mathcal{W}_\mathrm{cloud}$, includes three constituent parts: $$\begin{equation}
    \mathcal{W}_\mathrm{cloud} = \mathcal{W}_\mathrm{cloud}^\mathrm{self} + \mathcal{W}_\mathrm{cloud}^\mathrm{ext\text{-}mol} + \mathcal{W}_\mathrm{cloud}^\mathrm{star}~.
\end{equation}$$ These three terms represent the weights due to the cloud’s own self-gravity ($\mathcal{W}_\mathrm{cloud}^\mathrm{self}$), to the gravity of external molecular gas outside the cloud ($\mathcal{W}_\mathrm{cloud}^\mathrm{ext\text{-}mol}$), and to the gravity of stars ($\mathcal{W}_\mathrm{cloud}^\mathrm{star}$). By symmetry, the outer atomic gas layers exert no gravity on any structure in the molecular layer.

For the cloud self-gravity term, we integrate the weight of a sphere with radius $R_\mathrm{cloud}$ and constant density[^16] $\rho_\mathrm{cloud}$: $$\begin{align}
    \mathcal{W}_\mathrm{cloud}^\mathrm{self}
    &= \int_0^{R_\mathrm{cloud}} \rho_\mathrm{cloud} \frac{G\rho_\mathrm{cloud} (4/3)\pi r^3}{r^2}\,\mathrm{d}r \nonumber\\
    &= \frac{2\pi}{3}G\rho_\mathrm{cloud}^2 R_\mathrm{cloud}^2 \nonumber\\
    &= \frac{3\pi}{8}G\Sigma_\mathrm{cloud}^2~.
\end{align}$$ The last step re-expresses $\mathcal{W}_\mathrm{cloud}^\mathrm{self}$ in terms of the cloud surface density $\Sigma_\mathrm{cloud} \equiv M_\mathrm{cloud}/(\pi R_\mathrm{cloud}^2)=(4/3)\rho_\mathrm{cloud}R_\mathrm{cloud}$.

For the external molecular gas gravity term, we approximate the distribution of all the molecular gas outside the cloud as a slab centered at the disk mid-plane. This slab has constant volume density $\bar\rho_\mathrm{mol}$ anywhere outside the cloud, and has zero density within the extent of the cloud (i.e., it has a spherical “hole”). For simplicity, we further assume that the vertical half width of this slab is equal to the cloud radius, $H_\mathrm{mol}=R_\mathrm{cloud}$. The weight of the cloud due to the gravity of this component is thus: $$\begin{align}
    \mathcal{W}_\mathrm{cloud}^\mathrm{ext\text{-}mol}
    &= \mathcal{W}_\mathrm{cloud,slab} - \mathcal{W}_\mathrm{cloud,hole} \nonumber\\
    &= \int_0^{R_\mathrm{cloud}} \rho_\mathrm{cloud}\, (4\pi G \bar\rho_\mathrm{mol}z)\, \mathrm{d}z - \int_0^{R_\mathrm{cloud}} \rho_\mathrm{cloud} \frac{G\bar\rho_\mathrm{mol} (4/3)\pi r^3}{r^2}\, \mathrm{d}r \nonumber\\
    &= 2\pi G \bar\rho_\mathrm{mol} \rho_\mathrm{cloud} R_\mathrm{cloud}^2 - \frac{2\pi}{3} G \bar\rho_\mathrm{mol} \rho_\mathrm{cloud} R_\mathrm{cloud}^2 \nonumber\\
    &= \frac{4\pi}{3} G \bar\rho_\mathrm{mol} \rho_\mathrm{cloud} R_\mathrm{cloud}^2 \nonumber\\
    &= \frac{\pi}{2} G \bar\Sigma_\mathrm{mol} \Sigma_\mathrm{cloud}~.
\end{align}$$ The last step re-expresses $\mathcal{W}_\mathrm{cloud}^\mathrm{ext\text{-}mol}$ in terms of the cloud surface density $\Sigma_\mathrm{cloud}$ and the average surface density of the slab $\bar\Sigma_\mathrm{mol}=\bar\rho_\mathrm{mol}\,(2H_\mathrm{mol})=\bar\rho_\mathrm{mol}\,(2R_\mathrm{cloud})$.

For the stellar gravity term, given that $R_\mathrm{cloud} \ll H_\mathrm{\star}$, we treat the stellar disk as having a uniform density near the mid-plane, $\rho_\mathrm{\star}$. We thus have: $$\begin{align}
    \mathcal{W}_\mathrm{cloud}^\mathrm{star}
    &= \int_0^{R_\mathrm{cloud}} \rho_\mathrm{cloud}\, (4\pi G \rho_\mathrm{\star}z)\, \mathrm{d}z \nonumber\\
    &= 2\pi G \rho_\mathrm{\star}\rho_\mathrm{cloud} R_\mathrm{cloud}^2 \nonumber\\
    &= \frac{3\pi}{2}G \rho_\mathrm{\star}\Sigma_\mathrm{cloud} R_\mathrm{cloud}~.
\end{align}$$

## The Weight of the Outer Atomic Gas Layer

The weight of the atomic gas layer, $\mathcal{W}_\mathrm{atom}$, also consists of three parts: $$\begin{equation}
    \mathcal{W}_\mathrm{atom} = \mathcal{W}_\mathrm{atom}^\mathrm{self} + \mathcal{W}_\mathrm{atom}^\mathrm{mol} + \mathcal{W}_\mathrm{atom}^\mathrm{star}~.
\end{equation}$$ These terms represent the weights due to the atomic layer’s self-gravity ($\mathcal{W}_\mathrm{atom}^\mathrm{self}$), to the gravity of the inner molecular gas layer ($\mathcal{W}_\mathrm{atom}^\mathrm{mol}$), and to the gravity of stars ($\mathcal{W}_\mathrm{atom}^\mathrm{star}$). The calculation of the first and last terms is very similar to that of $P_\mathrm{DE,\,1kpc}$ in Section [4.2](#sec:expectation:PDE-kpc). We simply quote the results here: $$\begin{align}
    \mathcal{W}_\mathrm{atom}^\mathrm{self} &= \frac{\pi}{2}G \Sigma_\mathrm{atom}^2 \\
    \mathcal{W}_\mathrm{atom}^\mathrm{star} &= \Sigma_\mathrm{atom}\sqrt{2G\rho_\mathrm{\star}}\,\sigma_\mathrm{atom,\,z};
\end{align}$$ Note that the second expression adopts the assumption that $H_\mathrm{mol} \ll H_\mathrm{atom}$.

The molecular gravity term, however, is slightly different from the version in the $P_\mathrm{DE,\,1kpc}$ calculation. As the entire molecular gas inner layer is assumed to be “sandwiched” by the atomic gas outer layer in this calculation, the latter feels the full gravity of the former, such that: $$\begin{equation}
    \mathcal{W}_\mathrm{atom}^\mathrm{mol} = \pi G \bar\Sigma_\mathrm{mol} \Sigma_\mathrm{atom}~.
\end{equation}$$ In reality, the molecular and atomic medium (or at least the cold atomic phase) are often well mixed, so this estimate represents an upper limit for the true $\mathcal{W}_\mathrm{atom}^\mathrm{mol}$ value.

## The Total Weight

Combining all the above derivations together, we have: $$\begin{align}
    \mathcal{W}_\mathrm{total}
    =&\, \mathcal{W}_\mathrm{cloud} + \mathcal{W}_\mathrm{atom} \nonumber\\
    =&\, \Sigma_\mathrm{cloud} \left( \frac{3\pi}{8}G\Sigma_\mathrm{cloud} + \frac{\pi}{2}G \bar\Sigma_\mathrm{mol} + \frac{3\pi}{2}G \rho_\mathrm{\star}R_\mathrm{cloud} \right) \nonumber\\
    &+ \Sigma_\mathrm{atom} \left( \frac{\pi}{2}G\Sigma_\mathrm{atom} + \pi G \bar\Sigma_\mathrm{mol} + \sqrt{2G\rho_\mathrm{\star}}\,\sigma_\mathrm{atom,\,z} \right)~.
    \label{eq:W_total}
\end{align}$$ This gives the estimated total weight of a molecular cloud and the atomic gas above it in a galaxy disk, or equivalently, the required pressure in this molecular cloud to keep it under dynamical equilibrium.

# Stellar Disk Flattening Ratio

In this paper, we assume a constant stellar disk flattening ratio $R_\mathrm{\star}/H_\mathrm{\star}=7.3$ when estimating the stellar mass volume density near the disk mid-plane (see Section [4.2](#sec:expectation:PDE-kpc)). This value is suggested by (cite: Kregel_etal_2002), and has been widely adopted in recent studies on similar topics (cite: Leroy_etal_2008; Ostriker_etal_2010; Gallagher_etal_2018a).

(cite: Kregel_etal_2002) derived this average $R_\mathrm{\star}/H_\mathrm{\star}$ value from careful analysis of 34 nearby, edge-on galaxies. To provide an improved estimate with better statistics, here we do a similar calculation for a much larger sample of 313 edge-on galaxies selected from the $\mathrm{S^4G}$ sample (cite: Sheth_etal_2010).

We select 313 edge-on galaxies from the $\mathrm{S^4G}$ parent sample based on the structural decomposition results published by (cite: Salo_etal_2015). We pick galaxies in which (cite: Salo_etal_2015) fit the shape of an edge-on disk component (a.k.a., “edgedisk”) that accounts for at least 50% of the light of the galaxy. We then calculate disk flattening ratios based on the exponential scale length and scale height of this flux-dominating “edgedisk” component, using the measurement in their data table. Note that in their structural decomposition analysis, (cite: Salo_etal_2015) assumed exponential density profile along both the radial and vertical direction. This is different from the isothermal vertical density profile assumed in this work (see Section [4.2](#sec:expectation:PDE-kpc)). Rather than redoing their entire structural decomposition analysis, we instead use 0.5 times their (exponential) scale height values to approximate the scale height we would have measured assuming isothermal profile. This correction factor of 0.5 comes from the fact that the mid-plane stellar volume density is $\rho_\mathrm{\star}=\Sigma_\mathrm{\star}/4H_\mathrm{\star}$ for an isothermal profile, and $\rho_\mathrm{\star}=\Sigma_\mathrm{\star}/2H_\mathrm{\star}$ for an exponential profile (cite: vanderKruit_1988).

Figure [11](#fig:flattening_ratio) shows the histogram of $R_\mathrm{\star}/H_\mathrm{\star}$ measured from the 313 $\mathrm{S^4G}$ edge-on galaxies. We find that the median and 16–84% range of this distribution (black dot with an error bar) is $$\begin{equation}
    R_\mathrm{\star}/H_\mathrm{\star}=7.3^{+2.6}_{-1.9}~.
\end{equation}$$ This agrees perfectly with the $R_\mathrm{\star}/H_\mathrm{\star}=7.3$ value (blue dashed line) suggested by (cite: Kregel_etal_2002), and supports the appropriateness of adopting this $R_\mathrm{\star}/H_\mathrm{\star}$ value for nearby disk galaxies. The 16–84% range of this distribution can also be translated to a 1$\sigma$ scatter of 0.13 dex in logarithmic space. This is the corresponding systematic uncertainty associated with this fixed $R_\mathrm{\star}/H_\mathrm{\star}$ ratio in all derived quantities that depend linearly on it (e.g., $\rho_\mathrm{\star,\,1kpc}$).

# Table of Key Measurements

Table [5](#tab:mrt) presents a collection of the key measurements derived in this work. Due to the space limit, in the print version we only include measurements in 10 apertures in the galaxy NGC 628. The full data table, which includes all measurements across the entire sample, is available in the online journal.

The content of the individual columns is as follows. (1) `‘Galaxy’`: name of the host galaxy; (2) `‘inDisk’`: whether each row corresponds to a “disk” aperture (see Section [3.2](#sec:method:region)); (3) `‘fCO120pc’`: CO flux recovery fraction on 120 pc scale (see Section [3.1](#sec:method:fCO) and Figure [2](#fig:Pturb-PDE-cloud)a); (4) `‘Pturb120pc’`: turbulent pressure in the molecular gas, measured on 120 pc scale (see Section [4.1](#sec:expectation:Pturb) and Figure [2](#fig:Pturb-PDE-cloud)a); (5) `‘PDE120pc’`: dynamical equilibrium pressure estimated on 120 pc scales (see Section [4.3](#sec:expectation:PDE-cloud) and Figure [2](#fig:Pturb-PDE-cloud)a); (6) `‘fCO60pc’`: CO flux recovery fraction on 60 pc scales (see Section [3.1](#sec:method:fCO) and Figure [2](#fig:Pturb-PDE-cloud)b); (7) `‘Pturb60pc’`: turbulent pressure in the molecular gas, measured on 60 pc scales (see Section [4.1](#sec:expectation:Pturb) and Figure [2](#fig:Pturb-PDE-cloud)b); (8) `‘PDE60pc’`: dynamical equilibrium pressure estimated on 60 pc scales (see Section [4.3](#sec:expectation:PDE-cloud) and Figure [2](#fig:Pturb-PDE-cloud)b); (9) `‘PDEkpc’`: dynamical equilibrium pressure estimated on kpc scales (see Section [4.2](#sec:expectation:PDE-kpc) and Figure [1](#fig:Pturb-PDE-kpc)); (10) `‘PDEkpc11’`: dynamical equilibrium pressure estimated on kpc scales, assuming $\sigma_\mathrm{gas,\,z}=11\,\mbox{$\rm km\,s^{-1}$}$ (see Section [7.1.2](#sec:discussion:SFR:PDE), Figure [8](#fig:SigSFR)b and Figure [9](#fig:Rmol-PDE)); (11) `‘SigSFRkpc’`: star formation rate surface density estimated on kpc scales (see Section [3.3.2](#sec:method:phys:kpc) and Figure [8](#fig:SigSFR)); (12) `‘Rmolkpc’`: molecular-to-atomic gas ratio estimated on kpc scales (see Section [7.2](#sec:discussion:Rmol) and Figure [9](#fig:Rmol-PDE)).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| `Galaxy` | `inDisk` | `fCO120pc` | `Pturb120pc` | `PDE120pc` | `fCO60pc` | `Pturb60pc` | `PDE60pc` | `PDEkpc` | `PDEkpc11` | `SigSFRkpc` | `Rmolkpc` |
|  |  |  | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ |  | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ | $[\mbox{$k_\mathrm{B}\rm\,K\,cm^{-3}$}]$ | $[\mbox{$\rm M_{\odot}\,yr^{-1}\,kpc^{-2}$}]$ |  |
| NGC0628 | 0 | 0.983 | 8.131e+04 | 1.717e+05 | 0.919 | 1.545e+05 | 1.581e+05 | 6.593e+04 | 1.048e+05 | 1.903e-02 | 1.749e+01 |
| NGC0628 | 0 | 0.962 | 4.969e+04 | 1.017e+05 | 0.896 | 1.280e+05 | 1.255e+05 | 3.600e+04 | 6.047e+04 | 1.207e-02 | 9.148e+00 |
| NGC0628 | 0 | 0.925 | 5.763e+04 | 1.011e+05 | 0.861 | 1.298e+05 | 1.136e+05 | 4.345e+04 | 6.780e+04 | 1.288e-02 | 6.907e+00 |
| NGC0628 | 0 | 0.923 | 1.195e+05 | 1.489e+05 | 0.829 | 2.743e+05 | 1.959e+05 | 3.832e+04 | 5.569e+04 | 1.383e-02 | 7.988e+00 |
| NGC0628 | 0 | 0.922 | 8.926e+04 | 1.288e+05 | 0.838 | 1.778e+05 | 1.388e+05 | 3.792e+04 | 5.817e+04 | 1.156e-02 | 9.519e+00 |
| NGC0628 | 0 | 0.966 | 1.095e+05 | 1.460e+05 | 0.866 | 2.306e+05 | 1.768e+05 | 3.416e+04 | 5.070e+04 | 1.043e-02 | 8.183e+00 |
| NGC0628 | 0 | 0.869 | 4.755e+04 | 7.255e+04 | 0.721 | 9.907e+04 | 8.932e+04 | 3.018e+04 | 4.894e+04 | 1.113e-02 | 8.417e+00 |
| NGC0628 | 1 | 0.817 | 1.530e+04 | 2.377e+04 | 0.491 | 3.771e+04 | 2.922e+04 | 1.776e+04 | 3.061e+04 | 6.582e-03 | 5.322e+00 |
| NGC0628 | 1 | 0.812 | 1.451e+04 | 2.383e+04 | 0.500 | 3.025e+04 | 2.799e+04 | 2.136e+04 | 3.360e+04 | 7.466e-03 | 3.542e+00 |
| NGC0628 | 1 | 0.819 | 2.781e+04 | 4.654e+04 | 0.662 | 7.480e+04 | 6.645e+04 | 2.127e+04 | 3.508e+04 | 8.680e-03 | 4.681e+00 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

: Table of Key Measurements

Table notes: This table is available in its entirety in the [PHANGS CADC storage](https://www.canfar.net/storage/list/phangs/RELEASES/Sun_etal_2020).

natexlab

(ref: Accurso_etal_2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750, doi: [`10.1093/mnras/stx1556`](http://doi.org/10.1093/mnras/stx1556)

(ref: AstropyCollaboration_etal_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: AstropyCollaboration_etal_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Benincasa_etal_2016) Benincasa, S. M., Wadsley, J., Couchman, H. M. P., & Keller, B. W. 2016, MNRAS, 462, 3053, doi: [`10.1093/mnras/stw1741`](http://doi.org/10.1093/mnras/stw1741)

(ref: Bertoldi_McKee_1992) Bertoldi, F., & McKee, C. F. 1992, ApJ, 395, 140, doi: [`10.1086/171638`](http://doi.org/10.1086/171638)

(ref: Binney_etal_1991) Binney, J., Gerhard, O. E., Stark, A. A., Bally, J., & Uchida, K. I. 1991, MNRAS, 252, 210, doi: [`10.1093/mnras/252.2.210`](http://doi.org/10.1093/mnras/252.2.210)

(ref: Blitz_1993) Blitz, L. 1993, in Protostars and Planets III, 125–161. <http://adsabs.harvard.edu/abs/1993prpl.conf..125B>

(ref: Blitz_Rosolowsky_2004) Blitz, L., & Rosolowsky, E. 2004, ApJL, 612, L29, doi: [`10.1086/424661`](http://doi.org/10.1086/424661)

(ref: Blitz_Rosolowsky_2006) —. 2006, ApJ, 650, 933, doi: [`10.1086/505417`](http://doi.org/10.1086/505417)

(ref: Bolatto_etal_2008) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948, doi: [`10.1086/591513`](http://doi.org/10.1086/591513)

(ref: Bolatto_etal_2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Bolatto_etal_2011) Bolatto, A. D., Leroy, A. K., Jameson, K., et al. 2011, ApJ, 741, 12, doi: [`10.1088/0004-637X/741/1/12`](http://doi.org/10.1088/0004-637X/741/1/12)

(ref: Caldu-Primo_etal_2013) Caldú-Primo, A., Schruba, A., Walter, F., et al. 2013, AJ, 146, 150, doi: [`10.1088/0004-6256/146/6/150`](http://doi.org/10.1088/0004-6256/146/6/150)

(ref: Chabrier_2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chevance_etal_2020) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS accepted, doi: [`10.1093/mnras/stz3525`](http://doi.org/10.1093/mnras/stz3525)

(ref: Chung_etal_2009) Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B. 2009, AJ, 138, 1741, doi: [`10.1088/0004-6256/138/6/1741`](http://doi.org/10.1088/0004-6256/138/6/1741)

(ref: Colombo_etal_2014a) Colombo, D., Hughes, A., Schinnerer, E., et al. 2014, ApJ, 784, 3, doi: [`10.1088/0004-637X/784/1/3`](http://doi.org/10.1088/0004-637X/784/1/3)

(ref: Colombo_etal_2019) Colombo, D., Rosolowsky, E., Duarte-Cabral, A., et al. 2019, MNRAS, 483, 4291, doi: [`10.1093/mnras/sty3283`](http://doi.org/10.1093/mnras/sty3283)

(ref: Comeron_etal_2011) Comerón, S., Elmegreen, B. G., Knapen, J. H., et al. 2011, ApJ, 741, 28, doi: [`10.1088/0004-637X/741/1/28`](http://doi.org/10.1088/0004-637X/741/1/28)

(ref: Comeron_etal_2012) Comerón, S., Elmegreen, B. G., Salo, H., et al. 2012, ApJ, 759, 98, doi: [`10.1088/0004-637X/759/2/98`](http://doi.org/10.1088/0004-637X/759/2/98)

(ref: Crocker_etal_2018) Crocker, R. M., Krumholz, M. R., Thompson, T. A., & Clutterbuck, J. 2018, MNRAS, 478, 81, doi: [`10.1093/mnras/sty989`](http://doi.org/10.1093/mnras/sty989)

(ref: Crutcher_1999) Crutcher, R. M. 1999, ApJ, 520, 706, doi: [`10.1086/307483`](http://doi.org/10.1086/307483)

(ref: DonovanMeyer_etal_2013) Donovan Meyer, J., Koda, J., Momose, R., et al. 2013, ApJ, 772, 107, doi: [`10.1088/0004-637X/772/2/107`](http://doi.org/10.1088/0004-637X/772/2/107)

(ref: Egusa_etal_2018) Egusa, F., Hirota, A., Baba, J., & Muraoka, K. 2018, ApJ, 854, 90, doi: [`10.3847/1538-4357/aaa76d`](http://doi.org/10.3847/1538-4357/aaa76d)

(ref: El-Badry_etal_2019) El-Badry, K., Ostriker, E. C., Kim, C.-G., Quataert, E., & Weisz, D. R. 2019, MNRAS, 490, 1961, doi: [`10.1093/mnras/stz2773`](http://doi.org/10.1093/mnras/stz2773)

(ref: Elmegreen_1989) Elmegreen, B. G. 1989, ApJ, 338, 178, doi: [`10.1086/167192`](http://doi.org/10.1086/167192)

(ref: Elmegreen_1993) —. 1993, ApJ, 411, 170, doi: [`10.1086/172816`](http://doi.org/10.1086/172816)

(ref: Elmegreen_Parravano_1994) Elmegreen, B. G., & Parravano, A. 1994, ApJL, 435, L121, doi: [`10.1086/187609`](http://doi.org/10.1086/187609)

(ref: Falgarone_etal_2008) Falgarone, E., Troland, T. H., Crutcher, R. M., & Paubert, G. 2008, A&A, 487, 247, doi: [`10.1051/0004-6361:200809577`](http://doi.org/10.1051/0004-6361:200809577)

(ref: Faucher-Giguere_etal_2013) Faucher-Giguère, C.-A., Quataert, E., & Hopkins, P. F. 2013, MNRAS, 433, 1970, doi: [`10.1093/mnras/stt866`](http://doi.org/10.1093/mnras/stt866)

(ref: Feldmann_etal_2012) Feldmann, R., Gnedin, N. Y., & Kravtsov, A. V. 2012, ApJ, 747, 124, doi: [`10.1088/0004-637X/747/2/124`](http://doi.org/10.1088/0004-637X/747/2/124)

(ref: Field_etal_2011) Field, G. B., Blackman, E. G., & Keto, E. R. 2011, MNRAS, 416, 710, doi: [`10.1111/j.1365-2966.2011.19091.x`](http://doi.org/10.1111/j.1365-2966.2011.19091.x)

(ref: Fisher_etal_2019) Fisher, D. B., Bolatto, A. D., White, H., et al. 2019, ApJ, 870, 46, doi: [`10.3847/1538-4357/aaee8b`](http://doi.org/10.3847/1538-4357/aaee8b)

(ref: Freeman_etal_2017) Freeman, P., Rosolowsky, E., Kruijssen, J. M. D., Bastian, N., & Adamo, A. 2017, MNRAS, 468, 1769, doi: [`10.1093/mnras/stx499`](http://doi.org/10.1093/mnras/stx499)

(ref: Gallagher_etal_2018b) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018a, ApJL, 868, L38, doi: [`10.3847/2041-8213/aaf16a`](http://doi.org/10.3847/2041-8213/aaf16a)

(ref: Gallagher_etal_2018a) —. 2018b, ApJ, 858, 90, doi: [`10.3847/1538-4357/aabad8`](http://doi.org/10.3847/1538-4357/aabad8)

(ref: Gentry_etal_2019) Gentry, E. S., Krumholz, M. R., Madau, P., & Lupi, A. 2019, MNRAS, 483, 3647, doi: [`10.1093/mnras/sty3319`](http://doi.org/10.1093/mnras/sty3319)

(ref: Genzel_etal_2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: Glover_MacLow_2011) Glover, S. C. O., & Mac Low, M. M. 2011, MNRAS, 412, 337, doi: [`10.1111/j.1365-2966.2010.17907.x`](http://doi.org/10.1111/j.1365-2966.2010.17907.x)

(ref: Grasha_etal_2018) Grasha, K., Calzetti, D., Bittle, L., et al. 2018, MNRAS, 481, 1016, doi: [`10.1093/mnras/sty2154`](http://doi.org/10.1093/mnras/sty2154)

(ref: Grasha_etal_2019) Grasha, K., Calzetti, D., Adamo, A., et al. 2019, MNRAS, 483, 4707, doi: [`10.1093/mnras/sty3424`](http://doi.org/10.1093/mnras/sty3424)

(ref: Herrera_etal_2019) Herrera, C. N., Pety, J., Hughes, A., et al. 2019, A&A accepted. [`https://arxiv.org/abs/1910.14311`](https://arxiv.org/abs/1910.14311)

(ref: Herrera-Camus_etal_2017) Herrera-Camus, R., Bolatto, A., Wolfire, M., et al. 2017, ApJ, 835, 201, doi: [`10.3847/1538-4357/835/2/201`](http://doi.org/10.3847/1538-4357/835/2/201)

(ref: Herrera-Endoqui_etal_2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86, doi: [`10.1051/0004-6361/201526047`](http://doi.org/10.1051/0004-6361/201526047)

(ref: Heyer_Dame_2015) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583, doi: [`10.1146/annurev-astro-082214-122324`](http://doi.org/10.1146/annurev-astro-082214-122324)

(ref: Heyer_etal_2009) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092, doi: [`10.1088/0004-637X/699/2/1092`](http://doi.org/10.1088/0004-637X/699/2/1092)

(ref: Heyer_Brunt_2004) Heyer, M. H., & Brunt, C. M. 2004, ApJL, 615, L45, doi: [`10.1086/425978`](http://doi.org/10.1086/425978)

(ref: Heyer_etal_2001) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, ApJ, 551, 852, doi: [`10.1086/320218`](http://doi.org/10.1086/320218)

(ref: Hirota_etal_2018) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73, doi: [`10.1093/pasj/psy071`](http://doi.org/10.1093/pasj/psy071)

(ref: Hughes_etal_2013a) Hughes, A., Meidt, S. E., Colombo, D., et al. 2013a, ApJ, 779, 46, doi: [`10.1088/0004-637X/779/1/46`](http://doi.org/10.1088/0004-637X/779/1/46)

(ref: Hughes_etal_2013b) Hughes, A., Meidt, S. E., Schinnerer, E., et al. 2013b, ApJ, 779, 44, doi: [`10.1088/0004-637X/779/1/44`](http://doi.org/10.1088/0004-637X/779/1/44)

(ref: Ibanez-Mejia_etal_2017) Ibáñez-Mejı́a, J. C., Mac Low, M.-M., Klessen, R. S., & Baczynski, C. 2017, ApJ, 850, 62, doi: [`10.3847/1538-4357/aa93fe`](http://doi.org/10.3847/1538-4357/aa93fe)

(ref: Iffrig_Hennebelle_2015) Iffrig, O., & Hennebelle, P. 2015, A&A, 576, A95, doi: [`10.1051/0004-6361/201424556`](http://doi.org/10.1051/0004-6361/201424556)

(ref: Isobe_etal_1990) Isobe, T., Feigelson, E. D., Akritas, M. G., & Babu, G. J. 1990, ApJ, 364, 104, doi: [`10.1086/169390`](http://doi.org/10.1086/169390)

(ref: Johnson_etal_2015) Johnson, K. E., Leroy, A. K., Indebetouw, R., et al. 2015, ApJ, 806, 35, doi: [`10.1088/0004-637X/806/1/35`](http://doi.org/10.1088/0004-637X/806/1/35)

(ref: Kennicutt_etal_2011) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347, doi: [`10.1086/663818`](http://doi.org/10.1086/663818)

(ref: Keto_Myers_1986) Keto, E. R., & Myers, P. C. 1986, ApJ, 304, 466, doi: [`10.1086/164181`](http://doi.org/10.1086/164181)

(ref: Kim_etal_2011) Kim, C.-G., Kim, W.-T., & Ostriker, E. C. 2011, ApJ, 743, 25, doi: [`10.1088/0004-637X/743/1/25`](http://doi.org/10.1088/0004-637X/743/1/25)

(ref: Kim_Ostriker_2015b) Kim, C.-G., & Ostriker, E. C. 2015a, ApJ, 815, 67, doi: [`10.1088/0004-637X/815/1/67`](http://doi.org/10.1088/0004-637X/815/1/67)

(ref: Kim_Ostriker_2015a) —. 2015b, ApJ, 802, 99, doi: [`10.1088/0004-637X/802/2/99`](http://doi.org/10.1088/0004-637X/802/2/99)

(ref: Kim_Ostriker_2017) —. 2017, ApJ, 846, 133, doi: [`10.3847/1538-4357/aa8599`](http://doi.org/10.3847/1538-4357/aa8599)

(ref: Kim_Ostriker_2018) —. 2018, ApJ, 853, 173, doi: [`10.3847/1538-4357/aaa5ff`](http://doi.org/10.3847/1538-4357/aaa5ff)

(ref: Kim_etal_2013) Kim, C.-G., Ostriker, E. C., & Kim, W.-T. 2013, ApJ, 776, 1, doi: [`10.1088/0004-637X/776/1/1`](http://doi.org/10.1088/0004-637X/776/1/1)

(ref: Kim_etal_2017) Kim, C.-G., Ostriker, E. C., & Raileanu, R. 2017, ApJ, 834, 25, doi: [`10.3847/1538-4357/834/1/25`](http://doi.org/10.3847/1538-4357/834/1/25)

(ref: Koyama_Ostriker_2009b) Koyama, H., & Ostriker, E. C. 2009, ApJ, 693, 1346, doi: [`10.1088/0004-637X/693/2/1346`](http://doi.org/10.1088/0004-637X/693/2/1346)

(ref: Kreckel_etal_2018) Kreckel, K., Faesi, C., Kruijssen, J. M. D., et al. 2018, ApJL, 863, L21, doi: [`10.3847/2041-8213/aad77d`](http://doi.org/10.3847/2041-8213/aad77d)

(ref: Kregel_etal_2002) Kregel, M., van der Kruit, P. C., & de Grijs, R. 2002, MNRAS, 334, 646, doi: [`10.1046/j.1365-8711.2002.05556.x`](http://doi.org/10.1046/j.1365-8711.2002.05556.x)

(ref: Kroupa_Weidner_2003) Kroupa, P., & Weidner, C. 2003, ApJ, 598, 1076, doi: [`10.1086/379105`](http://doi.org/10.1086/379105)

(ref: Kruijssen_Longmore_2013) Kruijssen, J. M. D., & Longmore, S. N. 2013, MNRAS, 435, 2598, doi: [`10.1093/mnras/stt1634`](http://doi.org/10.1093/mnras/stt1634)

(ref: Kruijssen_etal_2014) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, MNRAS, 440, 3370, doi: [`10.1093/mnras/stu494`](http://doi.org/10.1093/mnras/stu494)

(ref: Kruijssen_etal_2019b) Kruijssen, J. M. D., Schruba, A., Chevance, M., et al. 2019, Nature, 569, 519, doi: [`10.1038/s41586-019-1194-3`](http://doi.org/10.1038/s41586-019-1194-3)

(ref: Krumholz_Burkhart_2016) Krumholz, M. R., & Burkhart, B. 2016, MNRAS, 458, 1671, doi: [`10.1093/mnras/stw434`](http://doi.org/10.1093/mnras/stw434)

(ref: Krumholz_etal_2018) Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS, 477, 2716, doi: [`10.1093/mnras/sty852`](http://doi.org/10.1093/mnras/sty852)

(ref: Lagos_etal_2018) Lagos, C. d. P., Tobar, R. J., Robotham, A. S. G., et al. 2018, MNRAS, 481, 3573, doi: [`10.1093/mnras/sty2440`](http://doi.org/10.1093/mnras/sty2440)

(ref: Lang_etal_2019) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2019, ApJ submitted

(ref: Larson_1981) Larson, R. B. 1981, MNRAS, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: Leroy_etal_2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782, doi: [`10.1088/0004-6256/136/6/2782`](http://doi.org/10.1088/0004-6256/136/6/2782)

(ref: Leroy_etal_2013a) Leroy, A. K., Lee, C., Schruba, A., et al. 2013, ApJL, 769, L12, doi: [`10.1088/2041-8205/769/1/L12`](http://doi.org/10.1088/2041-8205/769/1/L12)

(ref: Leroy_etal_2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25, doi: [`10.1088/0004-637X/801/1/25`](http://doi.org/10.1088/0004-637X/801/1/25)

(ref: Leroy_etal_2016) Leroy, A. K., Hughes, A., Schruba, A., et al. 2016, ApJ, 831, 16, doi: [`10.3847/0004-637X/831/1/16`](http://doi.org/10.3847/0004-637X/831/1/16)

(ref: Leroy_etal_2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24, doi: [`10.3847/1538-4365/ab3925`](http://doi.org/10.3847/1538-4365/ab3925)

(ref: Makarov_etal_2014) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13, doi: [`10.1051/0004-6361/201423496`](http://doi.org/10.1051/0004-6361/201423496)

(ref: Martizzi_etal_2015) Martizzi, D., Faucher-Giguère, C.-A., & Quataert, E. 2015, MNRAS, 450, 504, doi: [`10.1093/mnras/stv562`](http://doi.org/10.1093/mnras/stv562)

(ref: McGaugh_Schombert_2014) McGaugh, S. S., & Schombert, J. M. 2014, AJ, 148, 77, doi: [`10.1088/0004-6256/148/5/77`](http://doi.org/10.1088/0004-6256/148/5/77)

(ref: McMullin_etal_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Data Analysis Software and Systems XVI, 127. <http://adsabs.harvard.edu/abs/2007ASPC..376..127M>

(ref: Meidt_2016) Meidt, S. E. 2016, ApJ, 818, 69, doi: [`10.3847/0004-637X/818/1/69`](http://doi.org/10.3847/0004-637X/818/1/69)

(ref: Meidt_etal_2019) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2019, The Astrophysical Journal, submitted

(ref: Meidt_etal_2014) Meidt, S. E., Schinnerer, E., van de Ven, G., et al. 2014, ApJ, 788, 144, doi: [`10.1088/0004-637X/788/2/144`](http://doi.org/10.1088/0004-637X/788/2/144)

(ref: Meidt_etal_2018) Meidt, S. E., Leroy, A. K., Rosolowsky, E., et al. 2018, ApJ, 854, 100, doi: [`10.3847/1538-4357/aaa290`](http://doi.org/10.3847/1538-4357/aaa290)

(ref: Miville-Deschenes_etal_2017) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57, doi: [`10.3847/1538-4357/834/1/57`](http://doi.org/10.3847/1538-4357/834/1/57)

(ref: Mogotsi_etal_2016) Mogotsi, K. M., de Blok, W. J. G., Caldú-Primo, A., et al. 2016, AJ, 151, 15, doi: [`10.3847/0004-6256/151/1/15`](http://doi.org/10.3847/0004-6256/151/1/15)

(ref: Murugeshan_etal_2019) Murugeshan, C., Kilborn, V., Obreschkow, D., et al. 2019, MNRAS, 483, 2398, doi: [`10.1093/mnras/sty3265`](http://doi.org/10.1093/mnras/sty3265)

(ref: Narayanan_etal_2012) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127, doi: [`10.1111/j.1365-2966.2012.20536.x`](http://doi.org/10.1111/j.1365-2966.2012.20536.x)

(ref: Oka_etal_2001) Oka, T., Hasegawa, T., Sato, F., et al. 2001, ApJ, 562, 348, doi: [`10.1086/322976`](http://doi.org/10.1086/322976)

(ref: Orr_etal_2018) Orr, M. E., Hayward, C. C., Hopkins, P. F., et al. 2018, MNRAS, 478, 3653, doi: [`10.1093/mnras/sty1241`](http://doi.org/10.1093/mnras/sty1241)

(ref: Ossenkopf_MacLow_2002) Ossenkopf, V., & Mac Low, M. M. 2002, A&A, 390, 307, doi: [`10.1051/0004-6361:20020629`](http://doi.org/10.1051/0004-6361:20020629)

(ref: Ostriker_etal_2010) Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ, 721, 975, doi: [`10.1088/0004-637X/721/2/975`](http://doi.org/10.1088/0004-637X/721/2/975)

(ref: Ostriker_Shetty_2011) Ostriker, E. C., & Shetty, R. 2011, ApJ, 731, 41, doi: [`10.1088/0004-637X/731/1/41`](http://doi.org/10.1088/0004-637X/731/1/41)

(ref: Pakmor_etal_2017) Pakmor, R., Gómez, F. A., Grand , R. J. J., et al. 2017, MNRAS, 469, 3185, doi: [`10.1093/mnras/stx1074`](http://doi.org/10.1093/mnras/stx1074)

(ref: Peng_etal_2010) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2010, AJ, 139, 2097, doi: [`10.1088/0004-6256/139/6/2097`](http://doi.org/10.1088/0004-6256/139/6/2097)

(ref: Pettini_Pagel_2004) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59, doi: [`10.1111/j.1365-2966.2004.07591.x`](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

(ref: Pety_etal_2013) Pety, J., Schinnerer, E., Leroy, A. K., et al. 2013, ApJ, 779, 43, doi: [`10.1088/0004-637X/779/1/43`](http://doi.org/10.1088/0004-637X/779/1/43)

(ref: Querejeta_etal_2015) Querejeta, M., Meidt, S. E., Schinnerer, E., et al. 2015, ApJS, 219, 5, doi: [`10.1088/0067-0049/219/1/5`](http://doi.org/10.1088/0067-0049/219/1/5)

(ref: Rahner_etal_2019) Rahner, D., Pellegrini, E. W., Glover, S. C. O., & Klessen, R. S. 2019, MNRAS, 483, 2547, doi: [`10.1093/mnras/sty3295`](http://doi.org/10.1093/mnras/sty3295)

(ref: Rebolledo_etal_2015) Rebolledo, D., Wong, T., Xue, R., et al. 2015, ApJ, 808, 99, doi: [`10.1088/0004-637X/808/1/99`](http://doi.org/10.1088/0004-637X/808/1/99)

(ref: Rice_etal_2016) Rice, T. S., Goodman, A. A., Bergin, E. A., Beaumont, C., & Dame, T. M. 2016, ApJ, 822, 52, doi: [`10.3847/0004-637X/822/1/52`](http://doi.org/10.3847/0004-637X/822/1/52)

(ref: Rosolowsky_Blitz_2005) Rosolowsky, E., & Blitz, L. 2005, ApJ, 623, 826, doi: [`10.1086/428897`](http://doi.org/10.1086/428897)

(ref: Rosolowsky_Leroy_2006) Rosolowsky, E., & Leroy, A. 2006, PASP, 118, 590, doi: [`10.1086/502982`](http://doi.org/10.1086/502982)

(ref: Saintonge_etal_2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: Salo_etal_2015) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4, doi: [`10.1088/0067-0049/219/1/4`](http://doi.org/10.1088/0067-0049/219/1/4)

(ref: Sanchez_etal_2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, A&A, 563, A49, doi: [`10.1051/0004-6361/201322343`](http://doi.org/10.1051/0004-6361/201322343)

(ref: Sanchez_etal_2019) Sánchez, S. F., Barrera-Ballesteros, J. K., López-Cobá, C., et al. 2019, MNRAS, 484, 3042, doi: [`10.1093/mnras/stz019`](http://doi.org/10.1093/mnras/stz019)

(ref: Sandstrom_etal_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Schinnerer_etal_2013) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42, doi: [`10.1088/0004-637X/779/1/42`](http://doi.org/10.1088/0004-637X/779/1/42)

(ref: Schinnerer_etal_2019) Schinnerer, E., Hughes, A., Leroy, A., et al. 2019, ApJ, 887, 49, doi: [`10.3847/1538-4357/ab50c2`](http://doi.org/10.3847/1538-4357/ab50c2)

(ref: Schruba_etal_2019) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2, doi: [`10.3847/1538-4357/ab3a43`](http://doi.org/10.3847/1538-4357/ab3a43)

(ref: Semenov_etal_2017) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2017, ApJ, 845, 133, doi: [`10.3847/1538-4357/aa8096`](http://doi.org/10.3847/1538-4357/aa8096)

(ref: Semenov_etal_2018) —. 2018, ApJ, 861, 4, doi: [`10.3847/1538-4357/aac6eb`](http://doi.org/10.3847/1538-4357/aac6eb)

(ref: Sheth_etal_2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: Shetty_Ostriker_2012) Shetty, R., & Ostriker, E. C. 2012, ApJ, 754, 2, doi: [`10.1088/0004-637X/754/1/2`](http://doi.org/10.1088/0004-637X/754/1/2)

(ref: Solomon_etal_1987) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: Sormani_etal_2015) Sormani, M. C., Binney, J., & Magorrian, J. 2015, MNRAS, 449, 2421, doi: [`10.1093/mnras/stv441`](http://doi.org/10.1093/mnras/stv441)

(ref: Sormani_etal_2019) Sormani, M. C., Treß, R. G., Glover, S. C. O., et al. 2019, MNRAS, 488, 4663, doi: [`10.1093/mnras/stz2054`](http://doi.org/10.1093/mnras/stz2054)

(ref: Spitzer_1941b) Spitzer, Lyman, J. 1941, ApJ, 94, 232, doi: [`10.1086/144328`](http://doi.org/10.1086/144328)

(ref: Spitzer_1942) —. 1942, ApJ, 95, 329, doi: [`10.1086/144407`](http://doi.org/10.1086/144407)

(ref: Sun_etal_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: Tamburro_etal_2009) Tamburro, D., Rix, H. W., Leroy, A. K., et al. 2009, AJ, 137, 4424, doi: [`10.1088/0004-6256/137/5/4424`](http://doi.org/10.1088/0004-6256/137/5/4424)

(ref: Thompson_etal_2019) Thompson, K. L., Troland, T. H., & Heiles, C. 2019, ApJ, 884, 49, doi: [`10.3847/1538-4357/ab364e`](http://doi.org/10.3847/1538-4357/ab364e)

(ref: Thompson_etal_2005) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167, doi: [`10.1086/431923`](http://doi.org/10.1086/431923)

(ref: Troland_Crutcher_2008) Troland, T. H., & Crutcher, R. M. 2008, ApJ, 680, 457, doi: [`10.1086/587546`](http://doi.org/10.1086/587546)

(ref: Tully_etal_2009) Tully, R. B., Rizzi, L., Shaya, E. J., et al. 2009, AJ, 138, 323, doi: [`10.1088/0004-6256/138/2/323`](http://doi.org/10.1088/0004-6256/138/2/323)

(ref: Utomo_etal_2015) Utomo, D., Blitz, L., Davis, T., et al. 2015, ApJ, 803, 16, doi: [`10.1088/0004-637X/803/1/16`](http://doi.org/10.1088/0004-637X/803/1/16)

(ref: Utomo_etal_2018) Utomo, D., Sun, J., Leroy, A. K., et al. 2018, ApJL, 861, L18, doi: [`10.3847/2041-8213/aacf8f`](http://doi.org/10.3847/2041-8213/aacf8f)

(ref: vanderKruit_1988) van der Kruit, P. C. 1988, A&A, 192, 117. <http://adsabs.harvard.edu/abs/1988A%26A...192..117V>

(ref: vanderKruit_Searle_1981) van der Kruit, P. C., & Searle, L. 1981, A&A, 95, 105. <http://adsabs.harvard.edu/abs/1981A%26A....95..105V>

(ref: Verschuur_1993) Verschuur, G. L. 1993, AJ, 106, 2580, doi: [`10.1086/116827`](http://doi.org/10.1086/116827)

(ref: Walch_Naab_2015) Walch, S., & Naab, T. 2015, MNRAS, 451, 2757, doi: [`10.1093/mnras/stv1155`](http://doi.org/10.1093/mnras/stv1155)

(ref: Walker_etal_2018) Walker, D. L., Longmore, S. N., Zhang, Q., et al. 2018, MNRAS, 474, 2373, doi: [`10.1093/mnras/stx2898`](http://doi.org/10.1093/mnras/stx2898)

(ref: Walter_etal_2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563, doi: [`10.1088/0004-6256/136/6/2563`](http://doi.org/10.1088/0004-6256/136/6/2563)

(ref: Williams_etal_1994) Williams, J. P., de Geus, E. J., & Blitz, L. 1994, ApJ, 428, 693, doi: [`10.1086/174279`](http://doi.org/10.1086/174279)

(ref: Wilson_etal_2011) Wilson, C. D., Warren, B. E., Irwin, J., et al. 2011, MNRAS, 410, 1409, doi: [`10.1111/j.1365-2966.2010.17646.x`](http://doi.org/10.1111/j.1365-2966.2010.17646.x)

(ref: Wolfire_etal_2010) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: Wong_Blitz_2002) Wong, T., & Blitz, L. 2002, ApJ, 569, 157, doi: [`10.1086/339287`](http://doi.org/10.1086/339287)

(ref: Yang_etal_2007) Yang, C.-C., Gruendl, R. A., Chu, Y.-H., Mac Low, M.-M., & Fukui, Y. 2007, ApJ, 671, 374, doi: [`10.1086/522861`](http://doi.org/10.1086/522861)

(ref: Yoachim_Dalcanton_2006) Yoachim, P., & Dalcanton, J. J. 2006, AJ, 131, 226, doi: [`10.1086/497970`](http://doi.org/10.1086/497970)

[^1]: “*P*hysics at *H*igh *A*ngular resolution in *N*earby *G*alaxie*S* with *ALMA*”. For more information, see [www.phangs.org](www.phangs.org).

[^2]: This matches the lowest resolution level in (cite: Sun_etal_2018).

[^3]: This line width metric is also referred to as “equivalent width” in (cite: Heyer_etal_2001) and subsequent works. It is defined as $I_\mathrm{CO}/(\sqrt{2\pi}\,T_\mathrm{peak,CO})$, where $T_\mathrm{peak,CO}$ is the CO line peak temperature. See (cite: Sun_etal_2018) for more details.

[^4]: Using a non-zero threshold (e.g., 10%) would only change the number of “bulge/bar” apertures by a very small amount.

[^5]: Throughout this paper, we use the term “conversion factor” and the symbol $\alpha_\mathrm{CO}$ to refer to the ratio of molecular gas mass to $\mathrm{CO}\,(1\text{--}0)$ line luminosity (or equivalently, the ratio of mass surface density to line intensity). By definition, this includes the mass contribution from heavy elements.

[^6]: We do not apply this inclination correction in Equation [\[eq:Sigmol\]](#eq:Sigmol), because at 60–120 pc scales the geometry of molecular gas structure is no longer well approximated by a thin disk (cite: Sun_etal_2018).

[^7]: Note that this differs from the adopted conversion in (cite: Querejeta_etal_2015), which is based on a higher mass-to-light ratio of $Y_{3.6} = 0.6\,M_\odot/L_\odot$ (cite: Meidt_etal_2014). See discussions in (cite: Leroy_etal_2019).

[^8]: As stated by (cite: Sun_etal_2018), this is appropriate when the beam size is comparable to or smaller than the molecular disk scale height or the turbulence driving scale, and when the beam dilution effect is not strong.

[^9]: Given that there is only one averaging scale in this work (i.e., 1 kpc), we will use $\left<X\right>$ as a shorthand for $\left<X\right>_\mathrm{1kpc}$ hereafter.

[^10]: (cite: Ostriker_Shetty_2011) assume that the gas self-gravity term dominates in $P_\mathrm{DE}$, and that $\alpha_\mathrm{CO}\propto I_\mathrm{CO}^{-0.3}$

[^11]: The $P_\mathrm{DE}$ estimates in (cite: Fisher_etal_2019) assume a Galactic $\alpha_\mathrm{CO}$ and use the ionized gas velocity dispersion for $\sigma_\mathrm{gas,\,z}$. Newly obtained CO velocity dispersion for the same galaxies implies systematically lower $P_\mathrm{DE}$ (by $\sim$0.3 dex; D. Fisher, priv. comm.), but no significant change in the $\Sigma_\mathrm{SFR}\text{--}P_\mathrm{DE}$ relation slope.

[^12]: <http://edd.ifa.hawaii.edu/index.html>

[^13]: <http://leda.univ-lyon1.fr>

[^14]: <http://ned.ipac.caltech.edu>

[^15]: <http://www.adsabs.harvard.edu>

[^16]: Given our assumption that turbulent motions dominate the pressure budget inside molecular clouds, these clouds could still achieve an internal pressure-gravity balance by having a scale-dependent turbulent velocity field.

</paper>

## Items to check

```json
[
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Sensitivity censoring biases slope shallower; systematics dominate fit errors",
  "failed_quote": "We caution that Equation [\\ref{eq:Pturbavg-PDEkpc}] likely has a shallower slope than the actual $\\left<P_\\mathrm{turb,\\,\\theta pc}\\right>_\\mathrm{1kpc}$–$P_\\mathrm{DE,\\,1kpc}$ relation."
 }
]
```
