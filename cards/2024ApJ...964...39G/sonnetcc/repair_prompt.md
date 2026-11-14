# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964...39G\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# UNCOVER spectroscopy confirms a surprising ubiquity of AGN in red galaxies at $z>5$

## Abstract

$JWST$ is revealing a new population of dust-reddened broad-line active galactic nuclei (AGN) at redshifts $z\gtrsim5$. Here we present deep NIRSpec/Prism spectroscopy from the Cycle 1 Treasury program UNCOVER of 17 AGN candidates selected to be compact, with red continua in the rest-frame optical but with blue slopes in the UV. From NIRCam photometry alone, they could have been dominated by dusty star formation or AGN. Here we show that the majority of the compact red sources in UNCOVER are dust-reddened AGN: 60% show definitive evidence for broad-line H$\alpha$ with FWHM$>2000$ km/s, for 20% current data are inconclusive, and $20\%$ are brown dwarf stars. We propose an updated photometric criterion to select red $z>5$ AGN that excludes brown dwarfs and is expected to yield $>80\%$ AGN. Remarkably, among all $z_{\rm phot}>5$ galaxies with F277W$-$F444W$>1$ in UNCOVER at least $33\%$ are AGN regardless of compactness, climbing to at least $80$% AGN for sources with F277W$-$F444W$>1.6$. The confirmed AGN have black hole masses of $10^7-10^9$ $M_{\odot}$. While their UV-luminosities ($-16>M_{\rm UV}>-20$ AB mag) are low compared to UV-selected AGN at these epochs, consistent with percent-level scattered AGN light or low levels of unobscured star formation, the inferred bolometric luminosities are typical of $10^7-10^9$ $M_{\odot}$ black holes radiating at $\sim 10-40\%$ of Eddington. The number densities are surprisingly high at $\sim10^{-5}$ Mpc$^{-3}$ mag$^{-1}$, 100 times more common than the faintest UV-selected quasars, while accounting for $\sim1\%$ of the UV-selected galaxies. While their UV-faintness suggest they may not contribute strongly to reionization, their ubiquity poses challenges to models of black hole growth.

[^1]

# Introduction

Over the past decade, large-area surveys have discovered hundreds of UV-luminous active galactic nuclei (AGN) at $z>5$ (cite: Mortlock:2011; Banados:2018; Fan:2019; Wang:2021; Harikane:2022; Fan:2023). Unlike lower redshifts, the number densities of UV-selected AGN at $z>5$ are not strongly luminosity dependent for $M_{\rm UV}$ fainter than $\sim -25$ mag (cite: Matsuoka:2018; Matsuoka:2023), while the galaxy LF rises steeply, so that UV-selected AGN fainter than about $M_{\rm UV} \approx -25$ mag make up $<0.1$% of the galaxy population at high redshift. Determining whether or not black hole growth is preceding or lagging galaxy growth at these epochs has important implications for the seeding and co-evolution of black holes and galaxies (cite: VolonteriReines:2016; Dayal:2019; Inayoshi:2020; Greene:2020; Zhang:2023), for the sources of reionization (cite: Madau:2015; Dayal:2020; Trebitsch:2023), and potentially for the sources of gravitational waves (cite: AmaraSeoane:2023; Somalwar:2023).

With the advent of the James Webb Space Telescope (cite: Gardner:2023), we have begun to identify the heretofore missing UV-faint AGN. They have been discovered through broad Balmer lines (cite: Kocevski:2023; Harikane:2023; Oesch:2023; Larson:2023; Ubler:2023; Barro:2023; Matthee:2023; Maiolino:2023), from color and morphology (cite: Onoue:2023; Ono:2022; Furtak:2022; Endsley:2022; Hainline:2023; Leung:2023; Yang:2023), and from X-ray emission (cite: Bogdan:2023; Goulding:2023). The number densities of these $JWST$-selected sources is roughly a few percent of the galaxy population, and while they are UV faint, their implied bolometric luminosities span a broad range ($L_{\rm bol} \sim 10^{43}-10^{46}$ erg/s), implying a wide range of $M_{\rm BH}$$\sim 10^6-10^9$ $M_{\odot}$.

An interesting sub-component of the $JWST$-selected AGN population are quite red (e.g., F2777$-$F444W\>1) (cite: Fujimoto:2022; Furtak:2022). For instance, (cite: Matthee:2023) spectroscopically identified a sample of broad-line AGN that all appear as “little red dots” with steep red continua in the rest-frame optical (cite: Kocevski:2023). Other $JWST$+broad-line selected samples show large red fractions of 10-20% (cite: Harikane:2023; Maiolino:2023). At $z<2$, reddened broad-line AGN are known (cite: Glikman:2012; Banerji:2015), but these particular spectral energy distributions, with both a steep red optical continuum and an additional UV component are quite rare (cite: Noboriguchi:2019).

What has not been clear to date is whether a photometrically selected sample of compact red sources with a significant UV component are dominated by AGN as well, or whether they may be powered by star formation (cite: Barro:2023; Akins:2023; Maiolino:2023). Recently, we (cite: Labbe:2023uncover) published a large photometric sample of compact red sources from the Cycle 1 $JWST$ program UNCOVER (cite: Bezanson:2022). We have now obtained follow-up NIRSpec spectroscopy for 15 of the 40 galaxies presented in L23. Here, we explore the nature of the sample, and show that our selection indeed provides a very high yield of $z>4$ AGN.

We present the UNCOVER data in §[2](#sec:data), and review the photometric selection in §[3](#sec:sample). The spectroscopic analysis, and in particular the identification of broad H$\alpha$ emission lines, is presented in §[4](#sec:findbroad). Throughout, we assume a concordance cosmology with H$_0$=70, $\Omega_{\Lambda} = 0.7$, $\Omega_{M} = 0.3$ (cite: Hinshaw:2013).

# Data, Sample, and Spectroscopic Follow-up

In this section we briefly describe the UNCOVER survey (cite: Bezanson:2022) and the MSA/PRISM spectroscopy and reductions [2.2](#sec:prism). Many exciting results have already come from the PRISM spectroscopy of the compact red sources, including a triply-imaged $z=7$ AGN (cite: Furtak:2023nature), a broad-line AGN at z=8.5 (cite: Kokorev:2023; Fujimoto:2023overdense), and three brown dwarfs which can show similar SEDs as red AGN (cite: Langeroodi:2023; Burgasser:2023). We have also reported two $z>12$ galaxies (cite: Wang:2023highz), and some of the faintest known targets in the epoch of reionization (cite: Atek:2023eor).

## UNCOVER Photometry

Our search is performed using the *JWST* Cycle 1 Treasury program Ultradeep NIRSpec and NIRCam ObserVations before the Epoch of Reionization (cite: Bezanson:2022). UNCOVER imaging was completed in November 2022, comprising ultradeep ($29-30$ AB mag) imaging over 45 arcmin$^2$ in the galaxy cluster Abell 2744. This well-studied Frontier Field cluster (cite: Lotz:2017) at $z=0.308$ has one of the largest high-magnification areas of known clusters, and thus made an excellent target for deep (4-6 hours per filter) imaging across seven NIRCam filters (F115W, F150W, F200W, F277W, F356W, F410M, F444W). The nominal depth of $\sim 30$ mag can comfortably reach sources as faint as 31.5 mag with the help of magnification. Photometric catalogs (cite: Weaver:2023) including existing *HST* data have been made available to the public, and the lens model is also publicly available (cite: Furtak:2022b_SLmodel). The initial selection of objects is based on the UNCOVER Data Release DR1 images and catalogs (cite: Weaver:2023).

(cite: Fujimoto:2023) present deep ALMA 1.2 mm continuum imaging in Abell 2744. A wider, deeper 1.2 mm map of the full NIRCam UNCOVER area was newly obtained in Cycle 9 (#2022.1.00073.S; S. Fujimoto in prep),

reaching continuum r.m.s. sensitivity of $33 \rm{\mu Jy}$ in the deepest areas. Prior-based photometry is extracted for all sources by measuring the ALMA flux in the natural resolution map (beam $\approx0.7-0.8\ensuremath{''}$) at the NIRCam positions.

The UNCOVER region additionally has full coverage with high spatial resolution X-ray imaging using the *Chandra* ACIS-I detector, which upon completion will be at $\sim$2.3 Ms depth (PI:A.Bogdan). This X-ray data has already identified the highest-redshift X-ray AGN to date, UHZ-1, spectroscopically confirmed at $z=10.1$ (cite: Bogdan:2023; Goulding:2023). There is also deep Jansky Very Large Array data from program 22A-017 (PI Murphy) that may provide complementary radio imaging.

![image](target_color.pdf) ![image](zspec_zphot.pdf)

## PRISM Spectroscopy and Reductions

### MSA Observational Setup

All 17 spectroscopic targets were observed with the Micro-Shutter Assembly (MSA) follow-up program of the UNCOVER $JWST$ field Abell 2744 (cite: Bezanson:2022). The UNCOVER NIRSpec/PRISM observations were taken over 7 MSA configurations. These observations employed a 2-POINT-WITH-NIRCam-SIZE2 dither pattern and a 3 shutter slit-let nod pattern at an aperture angle of $\sim 44$ degrees. The observational design for the photometric component is described in detail in (cite: Bezanson:2022), the catalog is described by (cite: Weaver:2023), the photometric redshifts are explored in some depth by (cite: Wang:2023), and the spectroscopic experimental design and reductions are explained by Price et al. (2023, in prep).

### NIRSpec/PRISM Data Reduction

The data reduction is performed with `msaexp` (cite: Brammer:22), beginning from the level 2 products downloaded from MAST[^2]. `msaexp` then corrects for 1/f noise, masks snowballs, and removes the bias frame-by-frame. The $JWST$ reduction pipeline is used to apply WCS, to identify each slit, and then to perform flat-fielding and to apply photometric correction. 2D slits are extracted and drizzled onto a common grid to make vertically shifted and stacked 2D spectra, to which a local background subtraction is applied. The optimal extraction uses a Gaussian model on the collapsed spectrum with a free center and width (cite: Horne:1986). To flux calibrate the spectra, the single-mask extracted 1D spectra are convolved with the broad/medium band filters, and then we compare to the total photometry ((cite: Weaver:2023)), and model the wavelength dependent linear correction with a first order polynomial. Reduced data will be presented in Price et al. (2023, in prep).

## Gravitational magnification

Throughout this study we use the latest version (`v1.1`) of the (cite: Furtak:2022b_SLmodel) strong lensing model of Abell 2744[^3]. The parametric strong lensing model was constructed with an updated version of the (cite: Zitrin:2015) parameteric method (cite: Pascale:2022; Furtak:2022b_SLmodel) and includes 421 cluster member galaxies and five smooth cluster-scale dark matter halos. The `v1.1` has been updated with 5 new multiple image systems and and additional spectroscopic redshifts (cite: Bergamini:2023_GLASS), and is thus constrained with 141 multiple images belonging to 48 sources across the several main clumps of the cluster. The final lens plane image reproduction error is $\Delta_{\mathrm{RMS}}=0.51\ensuremath{''}$. We compute magnifications and their uncertainties for our sample at each object’s position and spectroscopic redshift.

# Photometric and Spectroscopic Sample

First, we briefly review the basic properties of the photometrically selected AGN sample (§[3.1](#sec:parent), L23), then we summarize the objects targeted for MSA/PRISM spectroscopy.

## Sample of Red Compact Sources

We build the photometric sample of AGN candidates in a number of key steps. First we select compact and red sources, with the following color and morphology cuts. With $SNR(\rm{F444W}) > 14 \ \& \ m_{\rm F444W} < 27.7$ mag within a 0.32$''$ aperture, we select sources that are (*red1* $\vert$ *red2* ) & *compact*, where

$${\it red1} = (\rm{F115W-F150W} < 0.8) \, \land$$ $$(\rm{F200W-F277W} > 0.7) \, \land$$ $$(\rm{F200W-F356W} > 1.0) \,$$

$${\it red2} = (\rm{F150W-F200W} < 0.8)  \, \land$$ $$(\rm{F277W-F356W} > 0.7) \, \land$$ $$(\rm{F277W-F444W} > 1.0) \,$$

And: $${\it compact} = f_{\rm{F444W}}(0.4\ensuremath{''}) / f_{\rm{F444W}}(0.2\ensuremath{''}) < 1.7$$

for $f_{\rm{F444W}}(0.4\ensuremath{''})$ measured within a 0.4$''$ diameter aperture. This initial sample comprises 40 sources, the “compact red” sample. We show the full selection in Figure [1](#fig:target); the main difference between $red1$ and $red2$ is that $red2$ favors higher redshift galaxies owing to the redder filters used. The $red2$ sample accounts for $58\%$ of the photometric sample and has been the focus for spectroscopic follow-up, representing $82\%$ of spectroscopic targets.

For context, L23 color criteria, specifically $red2$, to select the compact red sample are similar to those used by (cite: Labbe:2023) to select “v-shaped” SEDs as candidates for massive galaxies at similar epochs, with an important distinction. The $red2$ applies a more stringent set of cuts to ensure that the sources are point-source dominated and show two red consecutive colors in the LW NIRCam filters, thus favoring sources with red continuum slopes rather than contribution of emission lines or a continuum break. Overlap betweent the samples is discussed in §5.

As a final step, L23 identified a “clean” sample of 17 objects keeping only sources where two-dimensional image fitting in F356W indicated $<$50% of the light residing in an extended component and where spectral energy distribution (SED) fitting indicated the broad-band SEDs could not be fit without an AGN component.

In nearly all cases, the highest priority targets are those with deep ALMA limits, because in these cases we can effectively rule out dusty star formation as the origin of the red continuum, unless we were to invoke much hotter dust than is seen at these (or any) redshift. However, only 3/20 targets with ALMA coverage favored SED solutions without an AGN component, so we will assume that the NIRCam color selected sample is largely representative of the SED selected sample. We will discuss the AGN yield under different cuts in §[5](#sec:yield).

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| MSAID | RA | Dec | $z_{\rm spec}$ | $\mu$ | $\mu_{\rm low}$ | $\mu_{\rm high}$ | F444W | 277-444 | 277-356 | Flg | MSA | T$_{\rm exp}$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) | \(12\) | \(13\) |
| 2008 | 3.592423 | $-$30.432828 | 6.74$\pm$0.00 | 1.69 | 1.68 | 1.72 | 27.3 | 1.39 | 1.06 | 0 | 1 | 2.7 |
| 4286 | 3.619202 | $-$30.423270 | 5.84$\pm$0.00 | 1.62 | 1.61 | 1.64 | 24.8 | 2.03 | 1.19 | 0 | 2 | 2.7 |
| 10686 | 3.550838 | $-$30.406598 | 5.05$\pm$0.00 | 1.44 | 1.45 | 1.47 | 24.3 | 1.05 | 0.49 | 1 | 1 | 2.7 |
| 13123$^a$ | 3.579829 | $-$30.401570 | 7.04$\pm$0.00 | 6.15 | 5.96 | 6.69 | 25.0 | 2.66 | 1.89 | 1 | 2,3,5,6,7 | 17.4 |
| 13821 | 3.620607 | $-$30.399951 | 6.34$\pm$0.00 | 1.59 | 1.57 | 1.61 | 25.0 | 2.33 | 1.40 | 1 | 1 | 2.7 |
| 15383$^a$ | 3.583534 | $-$30.396678 | 7.04$\pm$0.00 | 7.29 | 5.78 | 7.30 | 25.3 | 2.45 | 1.71 | 1 | 2,3,6 | 9.9 |
| 16594$^a$ | 3.597203 | $-$30.394330 | 7.04$\pm$0.00 | 3.55 | 3.38 | 3.70 | 26.3 | 1.97 | 1.26 | 1 | 1,5,6,7 | 14.7 |
| 20466 | 3.640409 | $-$30.386437 | 8.50$\pm$0.00 | 1.33 | 1.31 | 1.34 | 26.2 | 1.92 | 0.72 | 1 | 2 | 2.7 |
| 23608 | 3.542815 | $-$30.380646 | 5.80$\pm$0.00 | 2.07 | 2.07 | 2.13 | 24.9 | 0.79 | 0.88 | 0 | 3 | 2.7 |
| 28876 | 3.569596 | $-$30.373222 | 7.04$\pm$0.00 | 2.70 | 2.60 | 2.73 | 26.8 | 2.10 | 1.49 | 1 | 1,4 | 6.4 |
| 32265 | 3.537530 | $-$30.370168 | 0.00$\pm$0.00 | ... | ... | ... | 27.3 | 0.97 | 0.68 | 1 | 3,5,6,7 | 14.7 |
| 33437 | 3.546419 | $-$30.366245 | 0.00$\pm$0.00 | ... | ... | ... | 27.0 | 2.06 | 0.97 | 1 | 3,5,6,7 | 14.7 |
| 35488 | 3.578984 | $-$30.362598 | 6.26$\pm$0.00 | 3.38 | 3.14 | 3.74 | 24.5 | 0.83 | 0.99 | 0 | 1 | 2.7 |
| 38108 | 3.530009 | $-$30.358013 | 4.96$\pm$0.00 | 1.59 | 1.58 | 1.62 | 24.7 | 1.06 | 0.83 | 1 | 4 | 3.7 |
| 39243 | 3.513894 | $-$30.356024 | 0.00$\pm$0.00 | ... | ... | ... | 25.6 | 3.63 | 1.53 | 1 | 4 | 3.7 |
| 41225 | 3.533994 | $-$30.353308 | 6.76$\pm$0.00 | 1.50 | 1.49 | 1.53 | 25.9 | 1.13 | 0.71 | 1 | 4 | 3.7 |
| 45924 | 3.584758 | $-$30.343630 | 4.46$\pm$0.00 | 1.59 | 1.58 | 1.65 | 22.1 | 0.54 | 0.94 | 1 | 4,5,6,7 | 15.7 |

:  Sample

Table notes: Table of objects that satisfy $(red1 \vert red2)$ and $compact$. $a$ are the three images of the multiply-imaged red AGN presented in (cite: Furtak:2022; Furtak:2023nature). Column (1): MSA ID. Column (2): R.A. Column (3): Dec. Column (4): Spectroscopic redshifts Column (5): Total magnification ($\mu$) based on the `v1.1` UNCOVER strong lensing model (see section [2.3](#sec:SL)). Column (6): Magnification 68% low value. Column (7): Magnification 68% high value. Column (8): F444W mag. Column (9): F277W-F444W color (mag). Column (10): F277W-F356W color (mag). Column (11): Flag for the high-priority photometric sample. Column (12): MSA number (1-7). Column (13): Total exposure time (h).

## Spectroscopic sample

In designing the MSA PRISM masks, we prioritized observing the compact red sources from L23. We obtained spectra for most (75%) of the highest-priority targets, as is shown in Figure [1](#fig:target).

![](SpecLineFit.pdf)

![](SpecLineFitMaybe.pdf)

# Spectral Analysis

We targeted with the NIRSpec/PRISM 17 sources that were photometrically identified in the UNCOVER photometry (L23). Of these, 14 are extragalactic sources and three turn out to be cool brown dwarfs (cite: Burgasser:2023). Three of the extragalactic sources are confirmed as multiply lensed images of the same source, A2744-QSO1 (cite: Furtak:2022; Furtak:2023nature), leaving 12 unique non-stellar sources. All have redshifts $4.5<z_{\rm spec}<8.5$. Overall the photometric redshifts were accurate (Fig. [1](#fig:target)), with a median offset in $\delta z$/(1+z) of $\langle z \rangle =0.008$ and $\sigma_{MAD}=0.03$, but for some objects the redshift was underestimated (cite: Kokorev:2023), due to degeneracy between redshifts where \[OIII\] or H$\alpha$ are in the F410M or F444W band.

The main goal of this paper is to determine the nature of these sources. Based on their unique properties – detected UV continuum, red optical continuum, ALMA-undetected, and spatially compact – we proposed based on an SED fitting that the sources are likely to be AGN. We now ask whether the spectra provide evidence for an accreting black hole. The main evidence we will present is in the form of broad Balmer lines, which has long been an accepted signature of gas orbiting the central black hole in the broad-line region (cite: Osterbrock:1977).

## Line fitting

From our broad wavelength coverage, from $1-5 \, \ensuremath{\mu}m$, we cover from Ly$\alpha$ to Balmer lines at $4.5 < z < 8.5$. The spectra are very rich, albeit at relatively low ($R = 100-500$) dispersion. In this section, we will focus only on fitting the strong optical emission lines H$\beta$, \[O III\]$\lambda\lambda 4959, \, 5007$, H$\alpha$, \[N II\]$\lambda\lambda 6584, 6548$. Note that because H$\alpha$ falls at the reddest end of the spectrum, we have enough spectral resolution to model the \[N II\] lines separately from H$\alpha$.

In all cases we model the narrow forbidden lines with a single velocity width, and the ratios of the \[O III\] and \[N II\]doublets are fixed to $\sim 3$. We model the continuum as a power-law, normalized at 5100Å. We then perform two different fits to the H$\beta$+\[O III\]+H$\alpha$+\[N II\]complex. In all fits, the radial velocities of all lines are tied together. First, we perform a *narrow-line* only fit, where all the lines are fixed to the same velocity width, with a flat broad prior on the width up to 800 km/s. Then we perform a *two-component* fit with a narrow and broad component to the Balmer lines. In this fit, all narrow lines are fixed in velocity width and fit over a narrow prior range (50-150 km/s). The ratio of narrow H$\alpha$/H$\beta$ flux is fit over a prior range of 3-20 ($A_V \sim 0-5$) under the assumption of case B recombination (cite: Osterbrock:1989). Broad H$\beta$ and H$\alpha$ fluxes are fitted independently, and the width of H$\alpha$ is constrained to fall within a factor of two of H$\beta$. In the first fit we constrain eight free parameters (including a power-law continuum) and in the second model we add four additional free parameters.

Each model is then forward modeled through the instrument before calculating the likelihood. We use the predicted pre-launch instrumental broadening from JDOX (cite: Jakobsen:2022), but because our targets are by definition point sources, the resolution is considerably better than the nominal resolution for a uniformly illuminated slit (cite: deGraaff2023). On the other hand, the rectification and combination of the spectra results in additional broadening due to the relatively large pixel size compared to the instrument point spread function. We therefore increase the nominal resolution by a conservative, uniform factor of 1.3, but caution that we then neglect any wavelength-dependence of the correction factor to the line spread function. The effect on the inferred broad-line widths is negligible, but the inferred widths for the narrow-line components suffer from a systematic uncertainty. For the fitting, we define a variable wavelength grid that oversamples the native resolution by a factor of four, convolve the model with the instrumental broadening, and then resample onto the wavelength grid while preserving flux.

The full set of narrow-only and two-component fits are presented in Figures [2](#fig:specbroad) and [3](#fig:specmaybe), continuum fits are presented in Table [2](#table:continuum), and broad H$\alpha$ parameters are presented in Table [3](#table:thefits). To explore the impact of the degeneracy between broad and narrow lines, we perform an additional two-component fit in which we fix the Balmer decrement to fall between H$\alpha$/H$\beta = 4-6$, corresponding to the continuum-derived $A_V \approx 1.5$ mag as is seen in our more conservative continuum fits (§[4.4](#sec:reddening)). We find that in all cases but one, the derived H$\alpha$ width agrees within 5-10% of our fiducial fits. In the case of MSAID23608, which has a very strong narrow-line component, the broad H$\alpha$ width decreases to 1500 km/s. Thus, we are confident that overall, our broad-line widths are robust to degeneracy with the narrow components.

|  |  |  |  |  |  |  |
|:---|:---|---:|:---|:---|:--:|:--:|
| MSAID | $\alpha_{\rm opt}$ | $\beta_{\rm UV}$ | $A_{\rm V, 0.45}$ | $A_{\rm V, fit}$ | $L_{5100, c}$ | $L_{\rm 5100, H\alpha}$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| 2008 | 1.4$\pm$0.3 | $-$1.9$\pm$0.3 | 2.1$\pm$0.5 | 2.4$\pm$3.0 | 43.5 | 43.7 |
| 4286 | 0.9$\pm$0.1 | $-$1.6$\pm$0.1 | 1.3$\pm$0.2 | 2.7$\pm$0.2 | 44.6 | 44.7 |
| 10686 | 0.4$\pm$0.3 | $-$1.6$\pm$0.1 | 2.0$\pm$1.1 | 3.2$\pm$0.2 | 44.9 | 44.3 |
| 13123$^a$ | 1.2$\pm$0.3 | $-1.4 \pm 0.1$ | $3 \pm 0.5$ | ... | 44.4 | 43.8 |
| 13821 | 1.0$\pm$0.3 | $-$1.2$\pm$0.1 | 1.1$\pm$0.3 | 1.7$\pm$0.2 | 44.2 | 44.5 |
| 20466$^b$ | 0.5$\pm$0.3 | $-$0.7$\pm$0.2 | $2.1^{+1.1}_{-1}$ | $1.9 \pm 0.2$ | 44.5 | 44.9 |
| 23608 | 0.0$\pm$0.1 | $-$1.5$\pm$0.1 | 0.1$\pm$0.1 | 1.9$\pm$0.7 | 43.5 | 43.5 |
| 28876 | 1.0$\pm$0.2 | $-$2.1$\pm$0.1 | 1.4$\pm$0.1 | 2.9$\pm$1.2 | 44.1 | 43.9 |
| 35488 | 0.1$\pm$0.2 | $-$2.3$\pm$0.1 | 0.3$\pm$0.5 | 2.0$\pm$0.3 | 44.2 | 44.1 |
| 38108 | 0.5$\pm$0.1 | $-$1.9$\pm$0.1 | 0.8$\pm$0.2 | 3.3$\pm$0.2 | 44.7 | 44.7 |
| 41225 | 0.3$\pm$0.1 | $-$1.7$\pm$0.1 | 1.0$\pm$0.2 | 3.9$\pm$0.1 | 45.0 | 44.7 |
| 45924 | 0.5$\pm$0.1 | 0.0$\pm$0.1 | 1.6$\pm$0.3 | 1.1$\pm$0.9 | 44.9 | 45.3 |

: Continuum Fits

Table notes: Table of continuum measurements from the PRISM spectroscopy. $^a$ is the highest S/N spectrum of the triply-imaged object from (cite: Furtak:2023nature). The $A_V$ is derived from the Balmer decrement for this source. $^b$ is the $z=8.5$ broad-line AGN discussed by (cite: Kokorev:2023); in this case the $A_V$ measurements are derived from the Balmer decrement and a full spectral fit respectively, while $L_{5100}$ in Col. (7) is derived from H$\beta$ assuming a ratio of H$\alpha$/H$\beta = 3.5$. Column (1): MSA ID. Column (2): Optical slope $f_{\lambda} \propto \lambda^{\alpha}$, fitted redward of 4400Å. Column (3): UV slope $f_{\lambda} \propto \lambda^{\beta}$, fitted blueward of 3000Å. Column (4): $A_{\rm V}$ (mag) estimated from the continuum slope assuming an intrinsic AGN power-law slope of $\alpha_{\rm opt} = 0.45$ and an SMC reddening law. Column (5): $A_{\rm V}$ (mag) estimated from the continuum slope assuming an intrinsic AGN power-law slope as fitted to the UV component of the spectrum and an SMC reddening law. Column (6): Demagnified and dereddened luminosity at 5100Å (erg/s) as estimated from the measured continuum and the $A_{\rm V}$ from Column (5). Column (7): Demagnified and dereddened luminosity at 5100Å (erg/s) as estimated from the measured H$\alpha$ luminosity and the $A_{\rm V}$ from Column (5).

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| MSAID | FWHM$_n$ | FWHM$_{\rm two}$ | $f_{\rm two}$ | $\chi^2_n$ | $\chi^2_{\rm two}$ | $L_{\rm H\alpha}$ | $M_{\rm BH}$ | $L_{\rm bol}$ |  |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) |  |  |  |  |
| 2008 | 650$\pm$100 | 1200$\pm$430 | 1.4$\pm$0.3 | 94 | 94 | ... | ... | ... |  |  |  |  |
| 4286 | 800$\pm$10 | 2900$\pm$1040 | 13.7$\pm$0.4 | 807 | 361 | 43.4 | 8.0$\pm$0.3 | 45.4$\pm$0.3 |  |  |  |  |
| 10686 | 60$\pm$10 | 4900$\pm$1570 | 5.5$\pm$1.6 | 332 | 296 | ... | ... | ... |  |  |  |  |
| 13123$^a$ | ... | 2670$\pm$170 | 5.0$\pm$0.45 | ... | ... | 42.7 | 7.3$\pm$0.2 | 45.0$\pm$0.1 |  |  |  |  |
| 13821 | 790$\pm$10 | 3100$\pm$710 | 17.4$\pm$0.8 | 461 | 248 | 43.3 | 8.1$\pm$0.2 | 45.4$\pm$0.2 |  |  |  |  |
| 20466$^b$ | 203$\pm$154 | 3439$\pm$413 | 2.3$\pm$0.2 | 4817 | 410 | 43.8 | 8.17$\pm$0.42 | 45.8$^{+0.3}_{-0.1}$ |  |  |  |  |
| 23608 | 70$\pm$10 | 2900$\pm$340 | 2.4$\pm$0.2 | 409 | 341 | 42.3 | 7.5$\pm$0.2 | 44.2$\pm$0.4 |  |  |  |  |
| 28876 | 650$\pm$70 | 1800$\pm$650 | 2.2$\pm$0.4 | 265 | 265 | ... | ... | ... |  |  |  |  |
| 35488 | 90$\pm$10 | 1900$\pm$210 | 10.9$\pm$2.1 | 1123 | 976 | 42.8 | 7.4$\pm$0.2 | 44.8$\pm$0.4 |  |  |  |  |
| 38108 | 800$\pm$10 | 4100$\pm$1980 | 14.3$\pm$0.5 | 671 | 215 | 43.4 | 8.4$\pm$0.5 | 45.3$\pm$0.5 |  |  |  |  |
| 41225 | 510$\pm$30 | 2000$\pm$600 | 4.7$\pm$0.3 | 539 | 435 | 43.5 | 7.7$\pm$0.4 | 45.3$\pm$0.5 |  |  |  |  |
| 45924 | 70$\pm$10 | 4500$\pm$40 | 383.4$\pm$0.4 | 1621505 | 90681 | 44.0 | 8.9$\pm$0.1 | 46.4$\pm$0.2 |  |  |  |  |

: H$\alpha$ fits

Table notes: Table of H$\alpha$ measurement from the PRISM spectroscopy. $a$ is the highest S/N spectrum of the triply-imaged object from (cite: Furtak:2023nature), while $b$ is the $z=8.5$ broad-line AGN from (cite: Kokorev:2023). Column (1): MSA ID. Column (2): FWHM (H$\alpha$), narrow-only fit (km/s). Column (3): FWHM (H$\alpha$), two-component broad fit (km/s). (b) is measured from H$\beta$ (cite: Kokorev:2023). Column (4): Observed H$\alpha$ flux, two-component broad fit ($10^{-18}$ erg/s/cm$^2$). (b) is measured from H$\beta$ (cite: Kokorev:2023). Column (5): $\chi^2$ (narrow-only). Column (6): $\chi^2$ (two-component). Column (7): De-magnified and dereddened H$\alpha$ luminosity (erg/s), using $A_{V, fit}$ from Table [2](#table:continuum). Only definite broad-line objects have H$\alpha$ luminosities listed. Column (8): Black hole mass, using H$\alpha$ linewidth and luminosity. Errors account linewidth errors and two reddening values. Maybe sources have no $M_{\rm BH}$ listed. Column (9): Log of the bolometric luminosity (erg/s), estimated from the H$\alpha$ luminosity. Errors account for two reddening values and uncertainty in the bolometric correction.

## Identifying Broad Balmer Lines

Two targets (A2744-QSO1 and MSAID20466) have previously been identified as robust broad-line AGN (cite: Furtak:2023nature; Kokorev:2023). We here examine the remaining 10 objects, after removing the three brown dwarfs. The majority of our targets have $z<7$, meaning that H$\alpha$ falls fully in the spectrum. Given the significant dust reddening, we focus exclusively on identifying broad H$\alpha$, since given the typical Balmer decrements of $\sim 5-10$, we have substantially higher signal-to-noise in H$\alpha$ than H$\beta$.

To determine which sources have broad lines, we apply the following three criteria. First, we insist that the fit improvement in $\chi^2$ be better than $3 \sigma$ ($\Delta \chi^2 > 11.5$ for four additional degrees of freedom) between the narrow-only and two-component fit (MSAID2008 and MSAID35488 are removed at this step). Second, we require that the two-component broad H$\alpha$ have FWHM$>2000$ km/s. We choose 2000 km/s as a conservative limit, compared to the bimodality at 1200 km/s identified by (cite: Hao:2005). Finally, we remove any object with $<5 \sigma$ detection of a broad line, where $\sigma$ is measured as the 68% distribution from the nested sampling (MSAID10686 is removed at this step). All objects have $>5 \sigma$ narrow \[O III\] and H$\alpha$ detections. The “unconfirmed black hole” targets could show evidence of broad emission lines with higher spectral resolution (and in one case complete coverage of H$\alpha$). Specifically, many very significant but weak broad lines have been identified in higher-resolution $JWST$ spectroscopy (cite: Larson:2023; Harikane:2023; Maiolino:2023). We could not identify such lines in our data, and so we retain a label of unconfirmed for the remaining three objects. We do not report broad-line fluxes or black-hole masses for the unconfirmed targets.

Another question is whether the broad lines might arise from outflows, rather than the broad-line region of the AGN. It is true that outflows of $\sim 2000$ km/s have been seen in narrow permitted and forbidden lines in very luminous (and reddened) AGN at $z \sim 2$ (cite: Zakamska:2016). However, while we do not have robust measurements of the narrow-line widths, we know that they are $<500$ km/s, so that the broad permitted lines almost certainly arise from the broad-line region.

## Other Emission Lines

We do not present exhaustive fits of other UV emission lines in this work. However, we did perform a search for the forbidden line \[Ne V\]$\lambda 3426$. This line is widely accepted as a likely indicator of AGN activity, given the ionization potential of 95 eV, although it has been attributed to Wolf-Rayet stars and/or shocks in various situations (cite: Abel:2008; Izotov:2012; Leung:2021). We only find compelling evidence for \[Ne V\] in source 45924, which is already a very strong AGN candidate by virtue of the broad-line width of FWHM(H$\alpha$)$= 4000$ km/s. Since \[Ne V\] is typically $0.02-0.2$ the strength of \[O III\], and considering the strong reddening, this non-detection is not surprising (cite: Netzer:1990). We also attempt to decompose the \[O III\]$~\lambda 4363$ and H$\gamma$ emission lines, which may also provide corroborating evidence for excitation by an AGN (cite: Baskin:2005; Binette:2022). However, given our spectral resolution, we do not achieve robust decompositions for any of the unconfirmed AGN candidates.

## Balmer decrement and continuum slopes

By selection, our targets contain steep red continua. With the spectra, we have good constraints on both the UV and optical slopes, which we will denote as $\beta_{\rm UV}, f_{\lambda} \propto{\lambda^{\beta}}$ ($\lambda < 3000$ Å) and $\alpha_{\rm opt}, f_{\lambda} \propto{\lambda^{\alpha}}$ ($\lambda > 4000$ Å). For the definitive and unconfirmed broad-line sources, we find $\langle \beta_{\rm UV} \rangle = -1.5 \pm 0.7$ and $\langle \beta_{\rm UV} \rangle = -1.9 \pm 0.2$ respectively. The unconfirmed AGN candidates are bluer in the rest-UV than the average AGN in our sample, but all the targets are on the redder end of what is seen for F444W selected galaxies with $4<z<7$ (cite: Bouwens:2016; Bhatawdekar:2021; Topping:2023; Nanayakkara:2023). The optical slopes are by construction quite red, with $\langle \alpha_{\rm opt} \rangle = 0.5 \pm 0.3$, $\langle \alpha_{\rm opt} \rangle = 0.9 \pm 0.4$ for AGN and unconfirmed samples respectively (Table [2](#table:continuum)).

We now try to estimate the dust reddening. Nominally, we measure the Balmer decrement from the narrow Balmer line fits (ranging from 4-15), implying $A_V \sim 1-5$. Because of the degeneracy with the broad Balmer lines, the Balmer decrements are not well constrained in general. Small changes in the broad-line fits can lead to large fluctuations in the Balmer decrements. Note that we do not trust broad-line Balmer decrements, since self-absorption in the broad-line region can also change the H$\alpha$ to H$\beta$ ratio (cite: Korista:2004). We thus base our reddening estimates on the continuum slopes.

We fit the UV and optical sides of the spectra separately to derive $\beta_{\rm UV}$ and $\alpha_{\rm opt}$ as power-laws in $f_{\lambda}$. To derive the dust reddening, we must assume an intrinsic (unreddened) spectral shape. All of our determinations of $A_V$ are under the assumption that the red continuum is dominated by AGN light (see §[6](#sec:lrd)). We take two AGN models. First, we use the Sloan Digital Sky Survey (cite: York:2000) composite AGN templates from (cite: VandenBerk:2001). The composite slope has $\beta_{\rm UV} = -1.5$ in the UV. The UV slope of the SDSS template is consistent with many other works (cite: Davis:2007), and seems to hold over a wide range of redshift (cite: Temple:2021). The SDSS template then has a break to $\alpha_{\rm opt} = 0.45$ in the rest-frame optical at $\lambda \gtrsim 4000$Å. The redder slope could be an intrinsic spectral change, or the impact of galaxy light redward of the 4000Å break, which is hard to determine robustly. Hence, we fit the SDSS-QSO template independently to each spectrum in the range $\lambda < 3500$Å and $\lambda > 4300$Å (to avoid the observed break seen in several of the spectra). In each case we allow a free extinction parameter characterized by the SMC reddening curve (cite: Gordon:2003).

We also perform a second more agnostic fit in which we fit the rest-frame UV slope directly assuming $F_{\lambda} \propto \lambda^{\beta}$, and then assume this empirical slope holds over the full spectral range. In the case that the UV emission arises from scattered light, a single spectral slope should describe the scattered and intrinsic slopes. We allow for an additional two free parameters, an $A_{\rm V}$ affecting an SMC-like reddened $F_{\lambda}$ component to describe the red end of the spectra, and a zero-reddening scattered light fraction ($f_{\rm scatt}$) that describes the rest-frame UV portion of the final model such that $f_{\lambda{\rm, model}} = f_{\rm scatt}F_{\lambda{\rm ,UV}}$.

The reddening derived from the SDSS template is tabulated as $A_{\rm V, 0.45}$ due to the rest-frame optical slope of the composite spectrum. The agnostic empirical fit is denoted as $A_{\rm V, fit}$ because we fit directly for $\beta$. These two reddening values thus bracket a reasonable range of reddening levels, and are presented in Table [2](#table:continuum).

We find that although the flux level in the UV is suppressed compared to the standard AGN template, the UV slopes are very similar to the unreddened UV slope of the SDSS AGN template ($\langle \beta_{\rm UV} \rangle = -1.5 \pm 0.7$). The rest-optical slopes are more variable. In §[6.1](#sec:uvorigin), we will discuss the origin of the UV emission.

# High fraction of AGN in red photometric samples

Our NIRSpec/PRISM spectra confirm the AGN hypothesis for a majority of the objects photometrically selected in L23. With the spectra in hand, we can explore the demographics of red sources at high redshift, as well as devise refined photometric selection criteria for future searches.

![](select.png)

## Yield and Contaminants

Of the 17 targets from L23 with UNCOVER PRISM spectra, 11 have unambiguous evidence for broad emission lines, including three which are multiple images of the same target (cite: Furtak:2023nature). Three targets do not show clear evidence for broad emission lines, and a further three are brown dwarfs (cite: Burgasser:2023). Therefore 11/17 $= 65\%$ of the sample are confirmed as broad line AGN. Accounting for multiplicity, the confirmed AGN fraction among the targetted extragalactic objects in our sample is 9/12 $= 75\%$, but we note AGN activity is not strongly ruled out in the remaining galaxies, so the true fraction could be as high as $100\%$.

One obvious contaminant are brown dwarf stars. A simple color cut, excluding all sources bluer than F115W$-$F200W$< -0.5$ (blue box in Figure [4](#fig:newsample)), would remove the majority of brown dwarfs from high-z galaxy selections in high-latitude deep fields (cite: Langeroodi:2023). Based on the simulations from (cite: Burgasser:2023) in the UNCOVER area we expect $\sim$ 5 low-metallicity halo brown dwarfs, expected to have the bluest F150W$-$F200W colors, as can be seen from model tracks in Figure [4](#fig:newsample). Some contaminants at redder colors would remain: $\sim 2$ metal-rich brown dwarfs that reside in the Galactic thin disk are expected. The higher metallicity brown dwarfs in the thin disk should be bright, F444 $< 24$ mag, since the limited vertical scale height of the disk will limit these brown dwarfs to be within a few hundred pc. A more refined filter could possibly be defined from a larger model and/or template sample. Upcoming medium-band data (GO-4111; PI W. Suess) will allow for even cleaner identification of brown dwarfs (cite: Hainline:2023bd).

## Updated Photometric Selections of High Redshift Galaxies and AGN

Here we define updated NIRCam-only criteria to the selections of (cite: Labbe:2023uncover; Labbe:2023). Specifically, we start with the same $SNR(F444W) > 14 \ \& \ m_{F444W} < 27.7$ mag cuts as before. Then, we define a “v-shape” color selection to mimic that of (cite: Labbe:2023), designed to find candidate massive high-redshift galaxies:

$${\it v-shape}$$ $$(-0.5 < \rm{F115W-F200W} < 1.0) \ \land$$ $$(\rm{F277W-F444W} > 1.0)$$

The main difference with respect to (cite: Labbe:2023) is using $\rm{F115W-F200W}$ rather than $\rm{F150W-F200W}$, and a blue limit to facilitate removing brown dwarfs. In addition, since we lack deep ACS coverage, we forego the *HST*/ACS optical nondetection criterion, thereby extending the selection towards lower redshift $z\sim5$. This selection produces 31 unique sources in UNCOVER and is both effective and complete at identifying high-redshift galaxies with red rest-frame optical colors. The median $<z>=6.9 \pm 1.0$ and 28/31 = $90\%$ sources have $z_{phot}>5$ (see Figure [4](#fig:newsample)). In total 15 sources were targeted with UNCOVER PRISM spectroscopy, 11 presented in this paper and a further 4 presented in Price et al. (in preparation), all are at $5 < z < 8.5$. Only one source with F277W$-$F444W$>1$ at $z>5$ does not satisfy the v-shape selection.

Remarkably, with this color selection alone, at least 29% of the objects are spectroscopically identified AGN, corresponding to about one-third of all F277W$-$F444W$>1$ at $z>5$. We expect there are many non-active galaxies in the sample as well. Most of the (cite: Labbe:2023) objects found in the CEERS field are spatially resolved in the rest-UV, with densities similar to the cores of present-day ellipticals (cite: Baggen:2023). Out of 4 galaxies with spectroscopy in that sample, one was found to be a red broad line AGN (cite: Kocevski:2023). Cycle 2 spectroscopy (program JWST-GO-4106, PI Nelson) will determine what fraction of these color-selected but spatially-resolved objects show evidence for AGN activity.

To select red AGN more specifically in a similar fashion to the $red2$ selection of L23, we add an additional red color and compactness criterion compared to the v-shape criterion:

$${\it compact \ red}$$ $$(-0.5 < \rm{F115W-F200W} < 1.0) \ \land$$ $$(\rm{F277W-F444W} > 1.0)   \ \land$$ $$(\rm{F277W-F356W} > 0.7) \,   \ \land$$ $${\it compact} = f_{\rm{F444W}}(0.4\ensuremath{''}) / f_{\rm{F444W}}(0.2\ensuremath{''}) < 1.5$$

where the additional $\rm{F277W-F356W}>$ 0.7 facilitates selecting SEDs with red continuum slopes, rather than breaks or emission lines (Figure [4](#fig:newsample), top right), and the compactness criterion helps to target point-source dominated sources (Figure [4](#fig:newsample), bottom left). These extra cuts remove roughly 50% of the $v-shape$ targets. The main differences compared to L23 are the $\rm{F115W-F200W} > -0.5$ brown dwarf removal and a slightly more stringent $compact$ cut than in L23.

Amongst this more stringent AGN-focused selection, we find at least 75% are AGN. The AGN fraction is a function of F277W$-$F444W color (Figure [5](#fig:agnfraction)). The majority of the broader sample of $v-shape$ galaxies have $1 < \rm{F277W-F444W} < 1.6$. Therefore, an alternative high yield selection of AGN can be made by selecting on F277W$-$F444W$>1.6$. In this situation, $>$80% of the galaxies are AGN, while $>90$% of the compact red galaxies are AGN (cite: Barro:2023).

In short, among $z>5$ galaxies with red colors ($-0.5<$F115W–F200W$<1.0$, F277W–F444W$>1$), at least one third are AGN. Making more stringent compactness and color criteria, or simply cutting at F277W–F444W$>1.6$, can yield an 80-90% AGN fraction.

![](agn_hist.pdf)

# The Nature of the ‘Little Red Dots’

Now focusing exclusively on the confirmed broad-line AGN, we explore their properties, including SEDs, luminosity functions, and black holes masses.

## Origin of the Continuum

![](model_4286.png)

The compact red objects were photometrically selected not only to have a red continuum in the rest-frame optical, but also detectable UV emission. From a template fit to the photometry alone, we came to the conclusion that the red continuum was most likely dominated by reddened AGN light. With the spectra, we now ask whether it is possible to distinguish the origin of the rest-frame optical and UV continua more directly. We demonstrate the different methods of modeling the spectra with one example in Figure [6](#fig:uvfit). We will defer full SED modeling to a future work, as that will require exploiting both the continua and the emission lines.

In the rest-frame optical, we immediately see that the observed red slopes are continuum-dominated, not arising from high-EW emission lines (cite: Furtak:2022; Endsley:2023). The rest-frame optical slopes are consistent with a reddened AGN template or dusty star-formation, as was concluded from the photometric fitting. However, the broad emission lines provide an additional clue. We can calculate the expected continuum given the observed H$\alpha$ luminosity (cite: GreeneHo:2005) and a measurement of reddening. We can also directly calculate the observed continuum. The two should match.[^4] We include the two $L_{5100}$ values, based on the continuum and H$\alpha$ but using the same $A_{\rm V, fit}$, in Table [2](#table:continuum). While the H$\alpha$-derived values tend to be a bit higher, they agree within a factor of two, suggesting that the broad H$\alpha$ equivalent widths are comparable to the low-redshift SDSS calibration sample from (cite: GreeneHo:2005). The equivalent widths from pure star formation are much higher for dusty massive galaxies at lower redshift (cite: Fumagalli:2012; Whitaker:2014). Given the detection of broad H$\alpha$ and the AGN-like ratios of H$\alpha$ to continuum, we conclude that the rest-frame optical is AGN dominated.

The dominant component from the AGN is the red continuum, and given the $A_V = 1-3$ that we infer, we could not detect that component in the UV (see Fig. [6](#fig:uvfit)). Instead, we must invoke a second component, which is brighter than the pure reddened AGN spectrum, but still only a few percent of an unreddened (blue) AGN. The two possible origins for this second UV-emitting component are either star formation from the host or some small fraction of the photons from the accretion disk, whether via scattering or direct leakage. Unfortunately, we cannot make a concrete determination of the origin of the UV based on the spectral slopes alone. The rest-frame UV slopes are quite consistent with the observed slopes of blue AGN with $A_V \approx 0$, and in some cases there are likely broad UV lines. With higher resolution data this would be a smoking gun of AGN light dominating the UV. Alternatively, they could be consistent with the redder end of $4<z<7$ galaxies (cite: Bouwens:2016; Bhatawdekar:2021), particularly those selected at F444W (cite: Nanayakkara:2023; Topping:2023).

To explore the UV origin further, we can ask what UV luminosities we would expect given the intrinsic $L_{5100}$ luminosities. We bracket the range of reasonable $A_V$ using the two assumed intrinsic AGN slopes, and over that range we find that the observed $L_{3000}$ is 1-3% percent or 10-20% of percent of the expected intrinsic $L_{3000}$, depending on whether we assume $\alpha_{\rm opt, intrinsic} = \beta_{\rm UV, measured}$ or $\alpha_{\rm opt, intrinsic} = 0.45$ respectively. The former can easily be explained by a scattered (or directly transmitted) AGN component, while 10-20% fractions are likely too high for pure AGN scattering (cite: Liu:2009). In such cases, we would favor a star-formation contribution to the UV. We choose not to fit the UV alone, since it has limited sensitivity to the stellar mass, but naively converting the $M_{1450}$ measurements to star-formation rates, and assuming that all the UV arises from star-formation, we find rates of $\langle {\rm SFR} \rangle = 1.5$ $M_{\odot}$/yr. In terms of $L_{\rm H \alpha}$, we would expect 10-1000 times less H$\alpha$ luminosity for this star formation rate than what we measure in the broad lines. On the other hand, this level of star formation seems both plausible and challenging to rule out from other measurements. In principle, the UV emission lines could distinguish the UV origins; higher resolution data are needed for this purpose.

Overall, we conclude that the rest-frame optical continuum is dominated by a dusty broad-line AGN continuum, and that more work is needed to definitively determine the origin of the UV emission. Finally, we also note that two objects, MSAID45924 and the triply-imaged A2744-QSO1 (MSAID13123 in this work) both have rather extraordinary spectral breaks that are not easily modeled with any AGN template. We leave to future work a more exhaustive fitting of the continuum, to attempt to understand the nature of their extreme breaks.

![image](lf4z6SPEC.pdf) ![image](lf5z7SPEC.pdf)

## Luminosity Functions

+-------------------+---------+----------------------------------------------------------------+
| $M_{\mathrm{UV}}$ | $N$     | $\phi(M_{\mathrm{UV}})~[\mathrm{Mpc}^{-3}\,\mathrm{mag}^{-1}]$ |
+:=================:+:=======:+:==============================================================:+
| $z\sim5-6$ *sample*                                                                          |
+-------------------+---------+----------------------------------------------------------------+
| $-$19.5           | $3$     | $(3.0\pm0.6)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+
| $-$19.0           | $2$     | $(2.1\pm0.7)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+
| $-$18.5           | $2$     | $(2.1\pm0.8)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+
| $z\sim7-8$ *sample*                                                                          |
+-------------------+---------+----------------------------------------------------------------+
| $-$19.0           | $1$     | $(1.3\pm0.5)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+
| $-$18.0           | $2$     | $(2.6\pm0.7)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+
| $-$17.0           | $2$     | $(4.0\pm1.0)\times10^{-5}$                                     |
+-------------------+---------+----------------------------------------------------------------+

: Rest-frame UV luminosity functions of our sample of red AGN. The UV luminosity bins have widths of 0.5 magnitudes.

+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $\log(L_{\mathrm{bol}}/\mathrm{erg}\,\mathrm{s}^{-1})$ | $N$     | $\phi(L_{\mathrm{bol}})~[\mathrm{Mpc}^{-3}\,\mathrm{dex}^{-1}]$ |
+:======================================================:+:=======:+:===============================================================:+
| $z\sim5-6$ *sample*                                                                                                                |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $44.0$                                                 | $1$     | $(1.0\pm0.4)\times10^{-5}$                                      |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $45.0$                                                 | $4$     | $(4.2\pm0.7)\times10^{-5}$                                      |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $46.0$                                                 | $1$     | $(1.0\pm0.6)\times10^{-5}$                                      |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $z\sim7-8$ *sample*                                                                                                                |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $45.0$                                                 | $2$     | $(2.6\pm0.5)\times10^{-5}$                                      |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+
| $46.0$                                                 | $1$     | $(1.3\pm0.5)\times10^{-5}$                                      |
+--------------------------------------------------------+---------+-----------------------------------------------------------------+

: Bolometric luminosity functions of our sample of red AGN. The bins have widths of 1 dex.

![image](lf4z6LBOLpratika.pdf) ![image](lf6z8LBOLpratika.pdf)

We now compute the rest-frame UV luminosity function of red AGN at high-redshifts based on the spectroscopic sample alone. Since Abell 2744 is a strong lensing field, the lensing distortion needs to be taken into account when computing the volume of each luminosity bin. To calculate the volumes, we follow the forward-modeling method used in the *Hubble Frontier Fields* by (cite: Atek:2018): The sample completeness is assessed with a series of completeness simulations in which we populate the source plane with mock red AGN using the L23 SED, normalizing it to random UV luminosities and redshifts. These are then deflected into the lens plane with the deflection maps of the UNCOVER strong lensing model (see section [2.3](#sec:SL)) and added into the mosaics on which we re-run the detection routines and assess the fraction of recovered sources to derive the selection function $f(z, M_{\mathrm{UV}})$. Note that the details of our completeness simulation methods will be published in Chemerynska et al. (in prep.). The selection function is used to weight the co-moving volume element which is then integrated over the source plane area of sufficient magnification required to detect each object in all bands given the UNCOVER mosaic depths (see equation 2 in (cite: Atek:2018)) to obtain the effective volume probed by UNCOVER. Note that since the UNCOVER source detection is performed in the stacked LW bands (cite: Weaver:2023) where the compact red objects are the brightest, our sample is complete down to $M_{\mathrm{UV}}\sim-16$ mag and objects brighter than $M_{\mathrm{UV}}\sim-17$ mag do not necessarily need to be magnified in order to be detected given the UNCOVER depths listed in (cite: Weaver:2023). Our sample is binned in UV luminosity bins of 0.5 magnitude width. The number count uncertainties are derived by drawing $10^4$ random luminosities from each object’s $M_{\mathrm{UV}}$ error distribution and re-binning the luminosity function each time to allow objects to change luminosity bin. The uncertainty in magnification is taken into account in the computation of the UV luminosity uncertainties.

The resulting UV luminosity functions in the two redshift bins are presented in Table [4](#tab:UV_LF) and Fig. [7](#fig:UVLF). As established above, the spectroscopic sample represents a conservative but fairly accurate proxy for the true luminosity function of the reddened broad-line AGN. We confirm the result from L23 that the number densities of these red-selected AGN are higher by roughly two orders of magnitude compared to the UV-selected AGN at similar magnitudes. The number density we find is also comparable to what has been inferred for other moderate-luminosity red AGN samples at $z \approx 5$ (cite: Kocevski:2023; Barro:2023; Matthee:2023), and accounts for $\sim 10-20\%$ of the general broad-line AGN population as selected with $JWST$ (cite: Harikane:2023; Maiolino:2023). The spectroscopically-identified samples rely on higher-resolution NIRSpec data, which is inclusive of AGN with narrower lines and systems where the AGN does not necessarily dominate the total light output.

We have tried to emphasize that the UV light is a small fraction of the total luminosity due to the large reddening values and has an unknown origin in either scattered or transmitted AGN light or low-level unobscured star formation. Thus, while useful to put our targets into context, the UV luminosity function does not truly describe the physical properties of the AGN in this sample. For this reason, we also present a bolometric luminosity function in Table [5](#tab:Lbol_LF) and Figure [8](#fig:LFbol). Since the derivation of completeness as a function of bolometric luminosity is not straightforward and would require detailed SED-modeling in the completeness simulations, we here use the fact that our sample is mostly complete in UV luminosity (see above) to approximate the effective volume for the bolometric luminosity function by assuming the maximum $M_{\mathrm{UV}}$-completeness derived above in each $L_{\mathrm{bol}}$-bin (of width 1 dex) and no magnification, i.e. the effective volume element is integrated over the whole UNCOVER source plane area of $\sim27\,\mathrm{arcmin}^2$ (cite: Furtak:2022b_SLmodel; Atek:2023). While this is a reasonable approximation given the properties of our sample, the thus derived bolometric luminosity function remains a lower limit. The lower luminosity bins in particular are probably underestimated since these would be more sensitive to magnification.

To guide our interpretation, we also calculate “maximal" black hole bolometric luminosity functions using a combination of high and low-redshift observations. We start by using the Sheth-Tormen halo mass function (cite: sheth-tormen2002) at $z \sim 4-7$. Each halo is assumed to contain a gas mass that is linked to the halo mass through the cosmological ratio such that $M_g = (\Omega_b/\Omega_m)M_h$. The total stellar mass in any halo is assumed to scale with the gas mass as $M_* = \epsilon_* M_g$. Matching to the evolving observed stellar mass function at $z \sim 4-7$ requires a star formation efficiency that evolves as $\epsilon_*= fn(z) = 0.15-0.03(z-6)$ at these redshifts (cite: dayal2023). For each halo, we then use two sets of observed relations linking the black hole and stellar mass at $z \sim 0$ from (cite: reinesvolonteri2015): our “high” black-hole mass model uses $M_{BH} = 1.4M_* - 6.45$, valid for high stellar mass ellipticals. The “low” black-hole model on the other hand uses $M_{BH} = 1.05M_* - 4.1$, valid for moderate-luminosity AGN in low-mass halos. Based on previous theoretical works (cite: bower2017; dayal2019) that find suppressed Eddington accretion rate for black holes in halos below $10^{11}M_\ensuremath{\odot}$, we limit the Eddington accretion rate to $7.5\times 10^{-5}$ for such halos; higher mass halos are allowed to accrete at the Eddington rate in order to obtain the bolometric luminosity function shown in Fig. [8](#fig:LFbol).

We can already draw some interesting conclusions from these bolometric luminosity function lower limits. First, we see the full range of $L_{\rm bol}$ spanned by the sample is quite broad, $10^{44} - 10^{47}$ erg/s, corresponding to Eddington-limited accretion onto black holes with $M_{\rm BH}$$\sim 10^6-10^9$ $M_{\odot}$, most of the supermassive black hole population. We also see that the number density of sources at the bright end is approaching the maximal number of accreting black holes. In other words, we are finding an unexpectedly large number of relatively luminous black holes (cite: Furtak:2023nature; Kokorev:2023; Pacucci:2023).

## Black Hole Masses

We follow (cite: GreeneHo:2005), as updated by (cite: reinesetal2013), to calculate BH mass based on the luminosity $L_{\rm H\alpha}$ and velocity FWHM(H$\alpha$) of the broad H$\alpha$ line. These single-epoch BH mass estimates (cite: Shen:2019) are based on assuming that the BLR acts as a dynamical tracer of the BH (cite: Pancoast:2014). The size of the BLR is estimated from the AGN luminosity (cite: bentzetal2013), and then assuming virial equilibrium, the dynamical mass scales as $M_{\rm BH}$$\propto \rm{FWHM_{H\alpha}^2 R}$. Of course, we do not know that the BLR is in virial equilibrium, nor do we know whether we probe the velocity field at a comparable radius as the BLR “size” we estimate from the luminosity (cite: krolik2001; Linzer:2022).

The black hole masses are plotted against the UV luminosities and the H$\alpha$-inferred bolometric luminosities in Figure [9](#fig:mbhlbol). We compare the sources both to luminous UV-selected quasars from the review of (cite: Fan:2023) and from recent moderate-luminosity broad-line AGN discovered with $JWST$ (cite: Kocevski:2023; Harikane:2023; Barro:2023; Matthee:2023). Our sources are on the massive end of the broad-line AGN found in deep $JWST$ fields, but barely reach the low end of the BH mass and luminosity seen in the rare UV-selected sources. However, their UV luminosities are 4-5 magnitudes lower than the UV-selected AGN at comparable $M_{\rm BH}$. This difference is very likely due to dust obscuration. As shown on the right hand side, when we use the broad emission lines to estimate the bolometric luminosity, we find much more agreement in luminosity range at a given $M_{\rm BH}$.

It is worth noting MSAID45924. This galaxy is the brightest in the sample (F444W$=22$ mag) and stands out for its high SNR and black hole mass of $M_{\rm BH}$$\approx 10^9$ $M_{\odot}$. The object warrants bespoke analysis that is beyond the scope of this work.

![image](mbh_muv_UNCOVER0906.pdf) ![image](mbh_lbol_UNCOVER0906.pdf)

# Discussion and Summary

In this work, we present NIRSpec/PRISM spectroscopic follow-up of 15 red, compact sources selected in the UNCOVER+Abell 2744 field. The majority of these targets are confirmed to be AGN with $z>4.5$. The UV/optical SEDs have a characteristic steep red continuum towards the rest-frame optical but also a non-negligible UV component. The rest-frame optical is consistent with a reddened ($A_V \sim 1.5$) broad-line AGN. The UV slopes are well fit as unobscured AGN in slope, but suppressed by $\sim 100$ times relative to an un-reddened source. From the available low-resolution spectroscopy and broad-band SED data, we cannot rule out that the UV component is due to moderately reddened star formation at the level of a few solar masses per year in the host. AGN with similar shapes (cite: Noboriguchi:2023) are known at all redshifts (cite: Veilleux:2016; Pan:2021; Glikman:2012; Banerji:2015; Hamann:2017; Assef:2018). However, at $z<3$, these reddened sources with a UV excess are rare; (cite: Noboriguchi:2019) estimate that of all the dust-obscured galaxies, only 1% have a UV excess.

$JWST$ is uncovering a surprisingly high number density of red AGN at $z>5$ (cite: Harikane:2023; Barro:2023; Matthee:2023). This high number density is unexpected compared to UV-selected sources, which have measured number densities nearly 100 times lower at their faintest UV luminosities (cite: Matsuoka:2018; Matsuoka:2023), although nominally the densities are similar to some X-ray selections (cite: Giallongo:2019). Additionally, the compact red AGN account for a large fraction of all red-selected sources with $JWST$. After applying simple color cuts designed to select massive galaxies (cite: Labbe:2023), our spectra imply that at least one-third of the selected objects will be AGN. This number rises to nearly 100% for the reddest tail of galaxies (F277$-$F444W$>1.6$), and is also $>80\%$ when we apply a compactness criterion and enforce a red power-law continuum.

An obvious additional question is the possible role of these sources in reionization. Depending on the (poorly understood) number densities and accretion rates of black holes compared to star forming galaxies at the faint-end of the UV LF, they could either have made a minimal contribution (cite: hassan2018; dayal2020; trebitsch2021; Finkelstein:2022) or dominate the photon budget for reionization (cite: Madau:2015; grazian2018). Furthermore, current models of black hole and galaxy evolution underpredict the number densities of vigorously accreting black holes (cite: Furtak:2023nature). We see this directly in our bolometric luminosity functions, where at the highest luminosities we can only match the number densities if we assume that *every* black hole is accreting at its Eddington luminosity.

It is in principle possible that the occupation fraction approaches unity at high mass. Since we must posit continuous black hole growth at early times to explain the AGN that we are finding (cite: Bogdan:2023; Kokorev:2023), perhaps nature has a way to grow black holes at such high rates. Another possibility is that the black holes outgrow their galaxies dramatically at early times, such that the number densities of available halos is much higher than we assume and the occupation fraction is lowered. We also measure extreme black hole to galaxy ratios in many sources (cite: Izumi:2019; Furtak:2023nature). Finally, we could alleviate the high occupation fractions if we allow sources to exceed their Eddington luminosities. Given the unusual properties of the SEDs of the red AGN, perhaps we are detecting the signature of super-Eddington accretion.

Regardless, we cannot get away from the high number density of black holes at $z>5$. There are a few ways to imagine growing enough black hole mass density this early. Black hole seeds could form heavy ($M_{\rm BH}$$\sim 10^4$ $M_{\odot}$) as in direct collapse models (cite: brommloeb2003; loebrasio1994; lodatonatarajan2006; begelman2008; visbaletal2014; Habouzit:2016) or in dense star clusters (cite: portegieszwartetal2002; mapelli2016; omukai2008; schleicher2022; Natarajan:2021). With heavy seeds, it is easier to grow the black hole more rapidly than the galaxy, but most models cannot make high number densities of heavy seeds (cite: dayal2019; Inayoshi:2022). Alternatively, all of the black holes could start as light seeds (cite: fryeretal2001; brommlarson2004; madaurees2001), but then grow at super-Eddington rates to make the high mass density of black holes (cite: alexandernatarajan2014). Some super-Eddington accretion is favored by the semi-empirical model TRIDENT (cite: Zhang:2023model), that uses halo trees to jointly model galaxy and black hole growth. At the same time, detailed magneto hydrodynamical simulations do find viable super-Eddington accretion flows (cite: Jiang:2019). Super-eddington accretion may also explain some of the SED properties of the compact red sources, in particular the apparently low X-ray luminosities (cite: Matthee:2023; Furtak:2023nature) and even possibly the red continuum if the inner accretion flow grows optically thick but leaves an outer disk. Finally, super-Eddington accretion would alleviate the tension with our “maximal” model, but producing more luminosity for a given black hole.

One other complication may come from mergers. At low redshifts, reddened broad-line AGN seem to preferentially reside in merging hosts (cite: Urrutia:2008). If the red sources presented here were also dominated by merging hosts, then perhaps the merging system may be harder to detect than an undisturbed galaxy, due to variable extinction and perhaps a significant low surface brightness component. There could also be two AGN powering the objects in some cases in principle. Notionally, the number densities of major mergers at $z \sim 6$ could be high enough to match the number density of the compact red sources. Taking an empirically motivated merger timescale of $\sim 0.5$ Gyr and a merger volume density of $\sim 3-5 \times 10^{-5}$ Mpc$^{-3}$ Gyr$^{-1}$ for $M_* \approx 10^9-10^{10}$ $M_{\odot}$ galaxies from empirical halo modeling (cite: Oleary:2021), we estimate $\sim 2 \times 10^{-5}$ Mpc$^{-3}$ mergers at $5<z<6$. Plausibly then there could be a relationship between the AGN triggering, merging, and the observed reddening. As was seen in (cite: Matthee:2023), the compact red sources also appear to be clustered with each other. (cite: Fujimoto:2023overdense) highlights a potential overdensity hinted from a compact red AGN and a UV-bright object found together in the same giant ionized bubble with a radius of $7.69\pm0.18$ proper Mpc at $z=8.5$. Perhaps this excess clustering could be related to a merger origin for these sources.

There are many additional puzzles raised by the ’little red dots’, including their apparent clustering, their unique SEDs (characteristic red optical continuum, an additional UV component, and lack of X-ray emission), and their apparent lack of a significant host galaxy component. These red broad-line AGN apparently constitute a sizable $10-20\%$ fraction of broad-line AGN at $z>5$, as well as a sizable fraction of red galaxies at the same epoch. They are an important part of the story of black hole growth at early times.

# Acknowledgments

J.E.G. and A.D.G acknowledge support from NSF/AAG grant# 1007094, and J.E.G. also acknowledges support from NSF/AAG grant \# 1007052. A.Z. acknowledges support by Grant No. 2020750 from the United States-Israel Binational Science Foundation (BSF) and Grant No. 2109066 from the United States National Science Foundation (NSF), and by the Ministry of Science & Technology of Israel. The Cosmic Dawn Center is funded by the Danish National Research Foundation (DNRF) under grant #140. This work has received funding from the Swiss State Secretariat for Education, Research and Innovation (SERI) under contract number MB22.00072, as well as from the Swiss National Science Foundation (SNSF) through project grant 200020_207349. PD acknowledges support from the NWO grant 016.VIDI.189.162 (“ODIN") and from the European Commission’s and University of Groningen’s CO-FUND Rosalind Franklin program. K.G. and T.N. acknowledge support from Australian Research Council Laureate Fellowship FL180100060. H.A. and IC acknowledge support from CNES, focused on the $JWST$ mission, and the Programme National Cosmology and Galaxies (PNCG) of CNRS/INSU with INP and IN2P3, co-funded by CEA and CNES. RPN acknowledges funding from $JWST$ programs GO-1933 and GO-2279. Support for this work was provided by NASA through the NASA Hubble Fellowship grant HST-HF2-51515.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. The research of CCW is supported by NOIRLab, which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the National Science Foundation. A.J.B. acknowledges funding support from NASA/ADAP grant 21-ADAP21-0187. Support for this work was provided by The Brinson Foundation through a Brinson Prize Fellowship grant. RPN acknowledges support for this work provided by NASA through the NASA Hubble Fellowship grant HST-HF2-51515.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. CP thanks Marsha and Ralph Schilling for generous support of this research.

natexlab

(ref: Abel:2008) Abel, N. P., & Satyapal, S. 2008, ApJ, 678, 686, doi: [`10.1086/529013`](http://doi.org/10.1086/529013)

(ref: Akins:2023) Akins, H. B., Casey, C. M., Allen, N., et al. 2023, arXiv e-prints, arXiv:2304.12347, doi: [`10.48550/arXiv.2304.12347`](http://doi.org/10.48550/arXiv.2304.12347)

(ref: Akiyama:2018) Akiyama, M., He, W., Ikeda, H., et al. 2018, PASJ, 70, S34, doi: [`10.1093/pasj/psx091`](http://doi.org/10.1093/pasj/psx091)

(ref: alexandernatarajan2014) Alexander, T., & Natarajan, P. 2014, Science, 345, 1330, doi: [`10.1126/science.1251053`](http://doi.org/10.1126/science.1251053)

(ref: AmaraSeoane:2023) Amaro-Seoane, P., Andrews, J., Arca Sedda, M., et al. 2023, Living Reviews in Relativity, 26, 2, doi: [`10.1007/s41114-022-00041-y`](http://doi.org/10.1007/s41114-022-00041-y)

(ref: Assef:2018) Assef, R. J., Stern, D., Noirot, G., et al. 2018, ApJS, 234, 23, doi: [`10.3847/1538-4365/aaa00a`](http://doi.org/10.3847/1538-4365/aaa00a)

(ref: Atek:2018) Atek, H., Richard, J., Kneib, J.-P., & Schaerer, D. 2018, MNRAS, 479, 5184, doi: [`10.1093/mnras/sty1820`](http://doi.org/10.1093/mnras/sty1820)

(ref: Atek:2023eor) Atek, H., Labbé, I., Furtak, L. J., et al. 2023a, arXiv e-prints, arXiv:2308.08540, doi: [`10.48550/arXiv.2308.08540`](http://doi.org/10.48550/arXiv.2308.08540)

(ref: Atek:2023) Atek, H., Chemerynska, I., Wang, B., et al. 2023b, arXiv e-prints, arXiv:2305.01793, doi: [`10.48550/arXiv.2305.01793`](http://doi.org/10.48550/arXiv.2305.01793)

(ref: Banados:2018) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473, doi: [`10.1038/nature25180`](http://doi.org/10.1038/nature25180)

(ref: Baggen:2023) Baggen, J. F. W., van Dokkum, P., Labbe, I., et al. 2023, arXiv e-prints, arXiv:2305.17162, doi: [`10.48550/arXiv.2305.17162`](http://doi.org/10.48550/arXiv.2305.17162)

(ref: Banerji:2015) Banerji, M., Alaghband-Zadeh, S., Hewett, P. C., & McMahon, R. G. 2015, MNRAS, 447, 3368, doi: [`10.1093/mnras/stu2649`](http://doi.org/10.1093/mnras/stu2649)

(ref: Barro:2023) Barro, G., Perez-Gonzalez, P. G., Kocevski, D. D., et al. 2023, arXiv e-prints, arXiv:2305.14418, doi: [`10.48550/arXiv.2305.14418`](http://doi.org/10.48550/arXiv.2305.14418)

(ref: Baskin:2005) Baskin, A., & Laor, A. 2005, MNRAS, 358, 1043, doi: [`10.1111/j.1365-2966.2005.08841.x`](http://doi.org/10.1111/j.1365-2966.2005.08841.x)

(ref: begelman2008) Begelman, M. C., Rossi, E. M., & Armitage, P. J. 2008, MNRAS, 387, 1649, doi: [`10.1111/j.1365-2966.2008.13344.x`](http://doi.org/10.1111/j.1365-2966.2008.13344.x)

(ref: bentzetal2013) Bentz, M. C., Denney, K. D., Grier, C. J., et al. 2013, ApJ, 767, 149, doi: [`10.1088/0004-637X/767/2/149`](http://doi.org/10.1088/0004-637X/767/2/149)

(ref: Bergamini:2023_GLASS) Bergamini, P., Acebron, A., Grillo, C., et al. 2023, ApJ, 952, 84, doi: [`10.3847/1538-4357/acd643`](http://doi.org/10.3847/1538-4357/acd643)

(ref: Bezanson:2022) Bezanson, R., Labbe, I., Whitaker, K. E., et al. 2022, arXiv e-prints, arXiv:2212.04026, doi: [`10.48550/arXiv.2212.04026`](http://doi.org/10.48550/arXiv.2212.04026)

(ref: Bhatawdekar:2021) Bhatawdekar, R., & Conselice, C. J. 2021, ApJ, 909, 144, doi: [`10.3847/1538-4357/abdd3f`](http://doi.org/10.3847/1538-4357/abdd3f)

(ref: Binette:2022) Binette, L., Villar Martı́n, M., Magris C., G., et al. 2022, , 58, 133, doi: [`10.22201/ia.01851101p.2022.58.01.11`](http://doi.org/10.22201/ia.01851101p.2022.58.01.11)

(ref: Bogdan:2023) Bogdan, A., Goulding, A., Natarajan, P., et al. 2023, arXiv e-prints, arXiv:2305.15458, doi: [`10.48550/arXiv.2305.15458`](http://doi.org/10.48550/arXiv.2305.15458)

(ref: Bouwens:2017) Bouwens, R. J., Oesch, P. A., Illingworth, G. D., Ellis, R. S., & Stefanon, M. 2017, ApJ, 843, 129, doi: [`10.3847/1538-4357/aa70a4`](http://doi.org/10.3847/1538-4357/aa70a4)

(ref: Bouwens:2016) Bouwens, R. J., Aravena, M., Decarli, R., et al. 2016, ApJ, 833, 72, doi: [`10.3847/1538-4357/833/1/72`](http://doi.org/10.3847/1538-4357/833/1/72)

(ref: bower2017) Bower, R. G., Schaye, J., Frenk, C. S., et al. 2017, MNRAS, 465, 32, doi: [`10.1093/mnras/stw2735`](http://doi.org/10.1093/mnras/stw2735)

(ref: Brammer:22) Brammer, G. 2022, msaexp: NIRSpec analyis tools, 0.3.4, Zenodo, Zenodo, doi: [`10.5281/zenodo.7299500`](http://doi.org/10.5281/zenodo.7299500)

(ref: brommlarson2004) Bromm, V., & Larson, R. B. 2004, ARA&A, 42, 79, doi: [`10.1146/annurev.astro.42.053102.134034`](http://doi.org/10.1146/annurev.astro.42.053102.134034)

(ref: brommloeb2003) Bromm, V., & Loeb, A. 2003, ApJ, 596, 34, doi: [`10.1086/377529`](http://doi.org/10.1086/377529)

(ref: Burgasser:2023) Burgasser, A. J., Gerasimov, R., Bezanson, R., et al. 2023, arXiv e-prints, arXiv:2308.12107. [`https://arxiv.org/abs/2308.12107`](https://arxiv.org/abs/2308.12107)

(ref: Carnall:2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: Carnall:2019) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2019, MNRAS, 490, 417, doi: [`10.1093/mnras/stz2544`](http://doi.org/10.1093/mnras/stz2544)

(ref: Croom:2002) Croom, S. M., Rhook, K., Corbett, E. A., et al. 2002, MNRAS, 337, 275, doi: [`10.1046/j.1365-8711.2002.05910.x`](http://doi.org/10.1046/j.1365-8711.2002.05910.x)

(ref: Davis:2007) Davis, S. W., Woo, J.-H., & Blaes, O. M. 2007, ApJ, 668, 682, doi: [`10.1086/521393`](http://doi.org/10.1086/521393)

(ref: dayal2023) Dayal, P., & Giri, S. K. 2023, arXiv e-prints, arXiv:2303.14239, doi: [`10.48550/arXiv.2303.14239`](http://doi.org/10.48550/arXiv.2303.14239)

(ref: Dayal:2019) Dayal, P., Rossi, E. M., Shiralilou, B., et al. 2019a, MNRAS, 486, 2336, doi: [`10.1093/mnras/stz897`](http://doi.org/10.1093/mnras/stz897)

(ref: dayal2019) —. 2019b, MNRAS, 486, 2336, doi: [`10.1093/mnras/stz897`](http://doi.org/10.1093/mnras/stz897)

(ref: Dayal:2020) Dayal, P., Volonteri, M., Choudhury, T. R., et al. 2020a, MNRAS, 495, 3065, doi: [`10.1093/mnras/staa1138`](http://doi.org/10.1093/mnras/staa1138)

(ref: dayal2020) —. 2020b, MNRAS, 495, 3065, doi: [`10.1093/mnras/staa1138`](http://doi.org/10.1093/mnras/staa1138)

(ref: deGraaff2023) de Graaff, A., Rix, H.-W., Carniani, S., et al. 2023, arXiv e-prints, arXiv:2308.09742, doi: [`10.48550/arXiv.2308.09742`](http://doi.org/10.48550/arXiv.2308.09742)

(ref: Endsley:2022) Endsley, R., Stark, D. P., Whitler, L., et al. 2022, arXiv e-prints, arXiv:2208.14999, doi: [`10.48550/arXiv.2208.14999`](http://doi.org/10.48550/arXiv.2208.14999)

(ref: Endsley:2023) Endsley, R., Stark, D. P., Lyu, J., et al. 2023, MNRAS, 520, 4609, doi: [`10.1093/mnras/stad266`](http://doi.org/10.1093/mnras/stad266)

(ref: Fan:2023) Fan, X., Banados, E., & Simcoe, R. A. 2022, arXiv e-prints, arXiv:2212.06907, doi: [`10.48550/arXiv.2212.06907`](http://doi.org/10.48550/arXiv.2212.06907)

(ref: Fan:2019) Fan, X., Wang, F., Yang, J., et al. 2019, ApJL, 870, L11, doi: [`10.3847/2041-8213/aaeffe`](http://doi.org/10.3847/2041-8213/aaeffe)

(ref: Finkelstein:2022) Finkelstein, S. L., & Bagley, M. B. 2022, ApJ, 938, 25, doi: [`10.3847/1538-4357/ac89eb`](http://doi.org/10.3847/1538-4357/ac89eb)

(ref: fryeretal2001) Fryer, C. L., Woosley, S. E., & Heger, A. 2001, ApJ, 550, 372, doi: [`10.1086/319719`](http://doi.org/10.1086/319719)

(ref: Fujimoto:2022) Fujimoto, S., Brammer, G. B., Watson, D., et al. 2022, Nature, 604, 261, doi: [`10.1038/s41586-022-04454-1`](http://doi.org/10.1038/s41586-022-04454-1)

(ref: Fujimoto:2023overdense) Fujimoto, S., Wang, B., Weaver, J., et al. 2023a, arXiv e-prints, arXiv:2308.11609, doi: [`10.48550/arXiv.2308.11609`](http://doi.org/10.48550/arXiv.2308.11609)

(ref: Fujimoto:2023) Fujimoto, S., Kohno, K., Ouchi, M., et al. 2023b, arXiv e-prints, arXiv:2303.01658, doi: [`10.48550/arXiv.2303.01658`](http://doi.org/10.48550/arXiv.2303.01658)

(ref: Fumagalli:2012) Fumagalli, M., Patel, S. G., Franx, M., et al. 2012, ApJL, 757, L22, doi: [`10.1088/2041-8205/757/2/L22`](http://doi.org/10.1088/2041-8205/757/2/L22)

(ref: Furtak:2022) Furtak, L. J., Zitrin, A., Plat, A., et al. 2023a, ApJ, 952, 142, doi: [`10.3847/1538-4357/acdc9d`](http://doi.org/10.3847/1538-4357/acdc9d)

(ref: Furtak:2023nature) Furtak, L. J., Labbé, I., Zitrin, A., et al. 2023b, arXiv e-prints, arXiv:2308.05735, doi: [`10.48550/arXiv.2308.05735`](http://doi.org/10.48550/arXiv.2308.05735)

(ref: Furtak:2022b_SLmodel) Furtak, L. J., Zitrin, A., Weaver, J. R., et al. 2023c, MNRAS, 523, 4568, doi: [`10.1093/mnras/stad1627`](http://doi.org/10.1093/mnras/stad1627)

(ref: Gardner:2023) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001, doi: [`10.1088/1538-3873/acd1b5`](http://doi.org/10.1088/1538-3873/acd1b5)

(ref: Giallongo:2019) Giallongo, E., Grazian, A., Fiore, F., et al. 2019, ApJ, 884, 19, doi: [`10.3847/1538-4357/ab39e1`](http://doi.org/10.3847/1538-4357/ab39e1)

(ref: Glikman:2012) Glikman, E., Urrutia, T., Lacy, M., et al. 2012, ApJ, 757, 51, doi: [`10.1088/0004-637X/757/1/51`](http://doi.org/10.1088/0004-637X/757/1/51)

(ref: Gordon:2003) Gordon, K. D., Clayton, G. C., Misselt, K. A., Landolt, A. U., & Wolff, M. J. 2003, ApJ, 594, 279, doi: [`10.1086/376774`](http://doi.org/10.1086/376774)

(ref: Goulding:2023) Goulding, A. D., Greene, J. E., Setton, D. J., et al. 2023, arXiv e-prints, arXiv:2308.02750, doi: [`10.48550/arXiv.2308.02750`](http://doi.org/10.48550/arXiv.2308.02750)

(ref: grazian2018) Grazian, A., Giallongo, E., Boutsia, K., et al. 2018, A&A, 613, A44, doi: [`10.1051/0004-6361/201732385`](http://doi.org/10.1051/0004-6361/201732385)

(ref: GreeneHo:2005) Greene, J. E., & Ho, L. C. 2005, ApJ, 630, 122, doi: [`10.1086/431897`](http://doi.org/10.1086/431897)

(ref: Greene:2020) Greene, J. E., Strader, J., & Ho, L. C. 2020, ARA&A, 58, 257, doi: [`10.1146/annurev-astro-032620-021835`](http://doi.org/10.1146/annurev-astro-032620-021835)

(ref: Habouzit:2016) Habouzit, M., Volonteri, M., Latif, M., Dubois, Y., & Peirani, S. 2016, MNRAS, 463, 529, doi: [`10.1093/mnras/stw1924`](http://doi.org/10.1093/mnras/stw1924)

(ref: Hainline:2023) Hainline, K. N., Johnson, B. D., Robertson, B., et al. 2023a, arXiv e-prints, arXiv:2306.02468, doi: [`10.48550/arXiv.2306.02468`](http://doi.org/10.48550/arXiv.2306.02468)

(ref: Hainline:2023bd) Hainline, K. N., Helton, J. M., Johnson, B. D., et al. 2023b, arXiv e-prints, arXiv:2309.03250, doi: [`10.48550/arXiv.2309.03250`](http://doi.org/10.48550/arXiv.2309.03250)

(ref: Hamann:2017) Hamann, F., Zakamska, N. L., Ross, N., et al. 2017, MNRAS, 464, 3431, doi: [`10.1093/mnras/stw2387`](http://doi.org/10.1093/mnras/stw2387)

(ref: Hao:2005) Hao, L., Strauss, M. A., Tremonti, C. A., et al. 2005, AJ, 129, 1783, doi: [`10.1086/428485`](http://doi.org/10.1086/428485)

(ref: Harikane:2022) Harikane, Y., Ono, Y., Ouchi, M., et al. 2022, ApJS, 259, 20, doi: [`10.3847/1538-4365/ac3dfc`](http://doi.org/10.3847/1538-4365/ac3dfc)

(ref: Harikane:2023) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, arXiv e-prints, arXiv:2303.11946, doi: [`10.48550/arXiv.2303.11946`](http://doi.org/10.48550/arXiv.2303.11946)

(ref: hassan2018) Hassan, S., Davé, R., Mitra, S., et al. 2018, MNRAS, 473, 227, doi: [`10.1093/mnras/stx2194`](http://doi.org/10.1093/mnras/stx2194)

(ref: Hinshaw:2013) Hinshaw, G., Larson, D., Komatsu, E., et al. 2013, ApJS, 208, 19, doi: [`10.1088/0067-0049/208/2/19`](http://doi.org/10.1088/0067-0049/208/2/19)

(ref: Horne:1986) Horne, K. 1986, PASP, 98, 609, doi: [`10.1086/131801`](http://doi.org/10.1086/131801)

(ref: Inayoshi:2022) Inayoshi, K., Onoue, M., Sugahara, Y., Inoue, A. K., & Ho, L. C. 2022, ApJL, 931, L25, doi: [`10.3847/2041-8213/ac6f01`](http://doi.org/10.3847/2041-8213/ac6f01)

(ref: Inayoshi:2020) Inayoshi, K., Visbal, E., & Haiman, Z. 2020, ARA&A, 58, 27, doi: [`10.1146/annurev-astro-120419-014455`](http://doi.org/10.1146/annurev-astro-120419-014455)

(ref: Izotov:2012) Izotov, Y. I., Thuan, T. X., & Privon, G. 2012, MNRAS, 427, 1229, doi: [`10.1111/j.1365-2966.2012.22051.x`](http://doi.org/10.1111/j.1365-2966.2012.22051.x)

(ref: Izumi:2019) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: Jakobsen:2022) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80, doi: [`10.1051/0004-6361/202142663`](http://doi.org/10.1051/0004-6361/202142663)

(ref: Jiang:2019) Jiang, Y.-F., Stone, J. M., & Davis, S. W. 2019, ApJ, 880, 67, doi: [`10.3847/1538-4357/ab29ff`](http://doi.org/10.3847/1538-4357/ab29ff)

(ref: Kocevski:2023) Kocevski, D. D., Onoue, M., Inayoshi, K., et al. 2023, arXiv e-prints, arXiv:2302.00012, doi: [`10.48550/arXiv.2302.00012`](http://doi.org/10.48550/arXiv.2302.00012)

(ref: Kokorev:2023) Kokorev, V., Fujimoto, S., Labbe, I., et al. 2023, arXiv e-prints, arXiv:2308.11610, doi: [`10.48550/arXiv.2308.11610`](http://doi.org/10.48550/arXiv.2308.11610)

(ref: Korista:2004) Korista, K. T., & Goad, M. R. 2004, ApJ, 606, 749, doi: [`10.1086/383193`](http://doi.org/10.1086/383193)

(ref: krolik2001) Krolik, J. H. 2001, ApJ, 551, 72, doi: [`10.1086/320091`](http://doi.org/10.1086/320091)

(ref: Labbe:2023uncover) Labbé, I., Greene, J. E., Bezanson, R., et al. 2023a, arXiv e-prints, arXiv:2306.07320, doi: [`10.48550/arXiv.2306.07320`](http://doi.org/10.48550/arXiv.2306.07320)

(ref: Labbe:2023) Labbé, I., van Dokkum, P., Nelson, E., et al. 2023b, Nature, 616, 266, doi: [`10.1038/s41586-023-05786-2`](http://doi.org/10.1038/s41586-023-05786-2)

(ref: Langeroodi:2023) Langeroodi, D., Hjorth, J., & Zhang, Z. 2023, arXiv e-prints, arXiv:2308.10900, doi: [`10.48550/arXiv.2308.10900`](http://doi.org/10.48550/arXiv.2308.10900)

(ref: Larson:2023) Larson, R. L., Finkelstein, S. L., Kocevski, D. D., et al. 2023, arXiv e-prints, arXiv:2303.08918, doi: [`10.48550/arXiv.2303.08918`](http://doi.org/10.48550/arXiv.2303.08918)

(ref: Leung:2021) Leung, G. C. K., Coil, A. L., Rupke, D. S. N., & Perrotta, S. 2021, ApJ, 914, 17, doi: [`10.3847/1538-4357/abf4da`](http://doi.org/10.3847/1538-4357/abf4da)

(ref: Leung:2023) Leung, G. C. K., Bagley, M. B., Finkelstein, S. L., et al. 2023, arXiv e-prints, arXiv:2306.06244. [`https://arxiv.org/abs/2306.06244`](https://arxiv.org/abs/2306.06244)

(ref: Linzer:2022) Linzer, N. B., Goulding, A. D., Greene, J. E., & Hickox, R. C. 2022, ApJ, 937, 65, doi: [`10.3847/1538-4357/ac8d5c`](http://doi.org/10.3847/1538-4357/ac8d5c)

(ref: Liu:2009) Liu, X., Zakamska, N. L., Greene, J. E., et al. 2009, ApJ, 702, 1098, doi: [`10.1088/0004-637X/702/2/1098`](http://doi.org/10.1088/0004-637X/702/2/1098)

(ref: lodatonatarajan2006) Lodato, G., & Natarajan, P. 2006, MNRAS, 371, 1813, doi: [`10.1111/j.1365-2966.2006.10801.x`](http://doi.org/10.1111/j.1365-2966.2006.10801.x)

(ref: loebrasio1994) Loeb, A., & Rasio, F. A. 1994, ApJ, 432, 52, doi: [`10.1086/174548`](http://doi.org/10.1086/174548)

(ref: Lotz:2017) Lotz, J. M., Koekemoer, A., Coe, D., et al. 2017, ApJ, 837, 97, doi: [`10.3847/1538-4357/837/1/97`](http://doi.org/10.3847/1538-4357/837/1/97)

(ref: Madau:2015) Madau, P., & Haardt, F. 2015, ApJL, 813, L8, doi: [`10.1088/2041-8205/813/1/L8`](http://doi.org/10.1088/2041-8205/813/1/L8)

(ref: madaurees2001) Madau, P., & Rees, M. J. 2001, ApJL, 551, L27, doi: [`10.1086/319848`](http://doi.org/10.1086/319848)

(ref: Maiolino:2023) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2308.01230, doi: [`10.48550/arXiv.2308.01230`](http://doi.org/10.48550/arXiv.2308.01230)

(ref: mapelli2016) Mapelli, M. 2016, MNRAS, 459, 3432, doi: [`10.1093/mnras/stw869`](http://doi.org/10.1093/mnras/stw869)

(ref: Matsuoka:2018) Matsuoka, Y., Strauss, M. A., Kashikawa, N., et al. 2018, ApJ, 869, 150, doi: [`10.3847/1538-4357/aaee7a`](http://doi.org/10.3847/1538-4357/aaee7a)

(ref: Matsuoka:2023) Matsuoka, Y., Onoue, M., Iwasawa, K., et al. 2023, arXiv e-prints, arXiv:2305.11225, doi: [`10.48550/arXiv.2305.11225`](http://doi.org/10.48550/arXiv.2305.11225)

(ref: Matthee:2023) Matthee, J., Naidu, R. P., Brammer, G., et al. 2023, arXiv e-prints, arXiv:2306.05448, doi: [`10.48550/arXiv.2306.05448`](http://doi.org/10.48550/arXiv.2306.05448)

(ref: 2021ApJ...915..120M) Meisner, A. M., Schneider, A. C., Burgasser, A. J., et al. 2021, ApJ, 915, 120, doi: [`10.3847/1538-4357/ac013c`](http://doi.org/10.3847/1538-4357/ac013c)

(ref: Mortlock:2011) Mortlock, D. J., Warren, S. J., Venemans, B. P., et al. 2011, Nature, 474, 616, doi: [`10.1038/nature10159`](http://doi.org/10.1038/nature10159)

(ref: Nanayakkara:2023) Nanayakkara, T., Glazebrook, K., Jacobs, C., et al. 2023, ApJL, 947, L26, doi: [`10.3847/2041-8213/acbfb9`](http://doi.org/10.3847/2041-8213/acbfb9)

(ref: Natarajan:2021) Natarajan, P. 2021, MNRAS, 501, 1413, doi: [`10.1093/mnras/staa3724`](http://doi.org/10.1093/mnras/staa3724)

(ref: Netzer:1990) Netzer, H. 1990, in Active Galactic Nuclei, ed. R. D. Blandford, H. Netzer, L. Woltjer, T. J. L. Courvoisier, & M. Mayor, 57–160

(ref: Noboriguchi:2023) Noboriguchi, A., Inoue, A. K., Nagao, T., Toba, Y., & Misawa, T. 2023, arXiv e-prints, arXiv:2309.00955, doi: [`10.48550/arXiv.2309.00955`](http://doi.org/10.48550/arXiv.2309.00955)

(ref: Noboriguchi:2019) Noboriguchi, A., Nagao, T., Toba, Y., et al. 2019, ApJ, 876, 132, doi: [`10.3847/1538-4357/ab1754`](http://doi.org/10.3847/1538-4357/ab1754)

(ref: Oesch:2023) Oesch, P. A., Brammer, G., Naidu, R. P., et al. 2023, arXiv e-prints, arXiv:2304.02026, doi: [`10.48550/arXiv.2304.02026`](http://doi.org/10.48550/arXiv.2304.02026)

(ref: Oleary:2021) O’Leary, J. A., Moster, B. P., Naab, T., & Somerville, R. S. 2021, MNRAS, 501, 3215, doi: [`10.1093/mnras/staa3746`](http://doi.org/10.1093/mnras/staa3746)

(ref: omukai2008) Omukai, K., Schneider, R., & Haiman, Z. 2008, ApJ, 686, 801, doi: [`10.1086/591636`](http://doi.org/10.1086/591636)

(ref: Ono:2022) Ono, Y., Harikane, Y., Ouchi, M., et al. 2022, arXiv e-prints, arXiv:2208.13582, doi: [`10.48550/arXiv.2208.13582`](http://doi.org/10.48550/arXiv.2208.13582)

(ref: Onoue:2023) Onoue, M., Inayoshi, K., Ding, X., et al. 2023, ApJL, 942, L17, doi: [`10.3847/2041-8213/aca9d3`](http://doi.org/10.3847/2041-8213/aca9d3)

(ref: Osterbrock:1977) Osterbrock, D. E. 1977, ApJ, 215, 733, doi: [`10.1086/155407`](http://doi.org/10.1086/155407)

(ref: Osterbrock:1989) —. 1989, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Pacucci:2023) Pacucci, F., Nguyen, B., Carniani, S., Maiolino, R., & Fan, X. 2023, arXiv e-prints, arXiv:2308.12331, doi: [`10.48550/arXiv.2308.12331`](http://doi.org/10.48550/arXiv.2308.12331)

(ref: Pan:2021) Pan, X., Zhou, H., Yang, C., et al. 2021, ApJ, 912, 118, doi: [`10.3847/1538-4357/abf148`](http://doi.org/10.3847/1538-4357/abf148)

(ref: Pancoast:2014) Pancoast, A., Brewer, B. J., Treu, T., et al. 2014, MNRAS, 445, 3073, doi: [`10.1093/mnras/stu1419`](http://doi.org/10.1093/mnras/stu1419)

(ref: Pascale:2022) Pascale, M., Frye, B. L., Diego, J., et al. 2022, ApJL, 938, L6, doi: [`10.3847/2041-8213/ac9316`](http://doi.org/10.3847/2041-8213/ac9316)

(ref: portegieszwartetal2002) Portegies Zwart, S. F., & McMillan, S. L. W. 2002, ApJ, 576, 899, doi: [`10.1086/341798`](http://doi.org/10.1086/341798)

(ref: reinesetal2013) Reines, A. E., Greene, J. E., & Geha, M. 2013, ApJ, 775, 116, doi: [`10.1088/0004-637X/775/2/116`](http://doi.org/10.1088/0004-637X/775/2/116)

(ref: reinesvolonteri2015) Reines, A. E., & Volonteri, M. 2015, ApJ, 813, 82, doi: [`10.1088/0004-637X/813/2/82`](http://doi.org/10.1088/0004-637X/813/2/82)

(ref: schleicher2022) Schleicher, D. R. G., Reinoso, B., Latif, M., et al. 2022, MNRAS, 512, 6192, doi: [`10.1093/mnras/stac926`](http://doi.org/10.1093/mnras/stac926)

(ref: Shen:2020) Shen, X., Hopkins, P. F., Faucher-Giguère, C.-A., et al. 2020, MNRAS, 495, 3252, doi: [`10.1093/mnras/staa1381`](http://doi.org/10.1093/mnras/staa1381)

(ref: Shen:2019) Shen, Y., Wu, J., Jiang, L., et al. 2019, ApJ, 873, 35, doi: [`10.3847/1538-4357/ab03d9`](http://doi.org/10.3847/1538-4357/ab03d9)

(ref: sheth-tormen2002) Sheth, R. K., & Tormen, G. 2002, Monthly Notices of the Royal Astronomical Society, 329, 61

(ref: Somalwar:2023) Somalwar, J. J., & Ravi, V. 2023, arXiv e-prints, arXiv:2306.00898, doi: [`10.48550/arXiv.2306.00898`](http://doi.org/10.48550/arXiv.2306.00898)

(ref: Stern:2012a) Stern, J., & Laor, A. 2012, MNRAS, 423, 600, doi: [`10.1111/j.1365-2966.2012.20901.x`](http://doi.org/10.1111/j.1365-2966.2012.20901.x)

(ref: Temple:2021) Temple, M. J., Hewett, P. C., & Banerji, M. 2021, MNRAS, 508, 737, doi: [`10.1093/mnras/stab2586`](http://doi.org/10.1093/mnras/stab2586)

(ref: Topping:2023) Topping, M. W., Stark, D. P., Endsley, R., et al. 2023, arXiv e-prints, arXiv:2307.08835, doi: [`10.48550/arXiv.2307.08835`](http://doi.org/10.48550/arXiv.2307.08835)

(ref: Trebitsch:2023) Trebitsch, M., Hutter, A., Dayal, P., et al. 2023, MNRAS, 518, 3576, doi: [`10.1093/mnras/stac2138`](http://doi.org/10.1093/mnras/stac2138)

(ref: trebitsch2021) Trebitsch, M., Dubois, Y., Volonteri, M., et al. 2021, A&A, 653, A154, doi: [`10.1051/0004-6361/202037698`](http://doi.org/10.1051/0004-6361/202037698)

(ref: Ubler:2023) Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2302.06647, doi: [`10.48550/arXiv.2302.06647`](http://doi.org/10.48550/arXiv.2302.06647)

(ref: Urrutia:2008) Urrutia, T., Lacy, M., & Becker, R. H. 2008, ApJ, 674, 80, doi: [`10.1086/523959`](http://doi.org/10.1086/523959)

(ref: VandenBerk:2001) Vanden Berk, D. E., Richards, G. T., Bauer, A., et al. 2001, AJ, 122, 549, doi: [`10.1086/321167`](http://doi.org/10.1086/321167)

(ref: Veilleux:2016) Veilleux, S., Meléndez, M., Tripp, T. M., Hamann, F., & Rupke, D. S. N. 2016, ApJ, 825, 42, doi: [`10.3847/0004-637X/825/1/42`](http://doi.org/10.3847/0004-637X/825/1/42)

(ref: visbaletal2014) Visbal, E., Haiman, Z., & Bryan, G. L. 2014, MNRAS, 445, 1056, doi: [`10.1093/mnras/stu1794`](http://doi.org/10.1093/mnras/stu1794)

(ref: VolonteriReines:2016) Volonteri, M., & Reines, A. E. 2016, ApJL, 820, L6, doi: [`10.3847/2041-8205/820/1/L6`](http://doi.org/10.3847/2041-8205/820/1/L6)

(ref: Wang:2023highz) Wang, B., Fujimoto, S., Labbe, I., et al. 2023a, arXiv e-prints, arXiv:2308.03745, doi: [`10.48550/arXiv.2308.03745`](http://doi.org/10.48550/arXiv.2308.03745)

(ref: Wang:2023) Wang, B., Leja, J., Bezanson, R., et al. 2023b, ApJL, 944, L58, doi: [`10.3847/2041-8213/acba99`](http://doi.org/10.3847/2041-8213/acba99)

(ref: Wang:2021) Wang, F., Fan, X., Yang, J., et al. 2021, ApJ, 908, 53, doi: [`10.3847/1538-4357/abcc5e`](http://doi.org/10.3847/1538-4357/abcc5e)

(ref: Weaver:2023) Weaver, J. R., Cutler, S. E., Pan, R., et al. 2023, arXiv e-prints, arXiv:2301.02671, doi: [`10.48550/arXiv.2301.02671`](http://doi.org/10.48550/arXiv.2301.02671)

(ref: Whitaker:2014) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104, doi: [`10.1088/0004-637X/795/2/104`](http://doi.org/10.1088/0004-637X/795/2/104)

(ref: Yang:2023) Yang, G., Caputi, K. I., Papovich, C., et al. 2023, arXiv e-prints, arXiv:2303.11736, doi: [`10.48550/arXiv.2303.11736`](http://doi.org/10.48550/arXiv.2303.11736)

(ref: York:2000) York, D. G., Adelman, J., Anderson, John E., J., et al. 2000, AJ, 120, 1579, doi: [`10.1086/301513`](http://doi.org/10.1086/301513)

(ref: Zakamska:2016) Zakamska, N. L., Hamann, F., Pâris, I., et al. 2016, MNRAS, 459, 3144, doi: [`10.1093/mnras/stw718`](http://doi.org/10.1093/mnras/stw718)

(ref: Zhang:2023) Zhang, H., Behroozi, P., Volonteri, M., et al. 2023a, arXiv e-prints, arXiv:2303.08150, doi: [`10.48550/arXiv.2303.08150`](http://doi.org/10.48550/arXiv.2303.08150)

(ref: Zhang:2023model) —. 2023b, MNRAS, 518, 2123, doi: [`10.1093/mnras/stac2633`](http://doi.org/10.1093/mnras/stac2633)

(ref: Zitrin:2015) Zitrin, A., Fabris, A., Merten, J., et al. 2015, ApJ, 801, 44, doi: [`10.1088/0004-637X/801/1/44`](http://doi.org/10.1088/0004-637X/801/1/44)

[^1]: Brinson Prize Fellow

[^2]: Available from: <http://dx.doi.org/10.17909/8k5c-xr27>

[^3]: The `v1.1` lensing maps are publicly available at <https://jwst-uncover.github.io/DR1.html#LensingMaps>

[^4]: Comparing to the (cite: GreeneHo:2005) relation is a bit easier than looking at the H$\alpha$ equivalent width distribution directly, since there may be subtle trends between line equivalent widths and luminosity (cite: Croom:2002; Stern:2012a) that are fitted for directly by Greene & Ho.

</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Parent compact red photometric sample (40 sources; 17 clean sample) used for target selection",
  "failed_quote": "This initial sample comprises 40 sources, the compact red sample."
 }
]
```
