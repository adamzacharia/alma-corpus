# UNCOVER Spectroscopy Confirms the Surprising Ubiquity of Active Galactic Nuclei in Red Sources at z &gt; 5

`2024ApJ...964...39G` | The Astrophysical Journal 2024 | first author: Greene, Jenny E. | arXiv: 2309.05714 | DOI: 10.3847/1538-4357/ad1e5f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are photometrically selected compact red sources at z>5 (red optical, blue UV) dominated by dust-reddened broad-line AGN or by dusty star formation?  
  > "What has not been clear to date is whether a photometrically selected sample of compact red sources with a significant UV component are dominated by AGN as well, or whether they may be powered by star formation" (1 Introduction); "The main goal of this paper is to determine the nature of these sources." (4 Spectral Analysis)
- Target **Abell 2744 UNCOVER field (lensing cluster)**: coordinates _not stated_; z/distance z=0.308  
  > "This well-studied Frontier Field cluster (cite: Lotz:2017) at $z=0.308$ has one of the largest high-magnification areas of known clusters" (2.1 UNCOVER Photometry); distance from cite: Lotz:2017 (as the Frontier Field cluster reference)  
  > "This well-studied Frontier Field cluster (cite: Lotz:2017) at $z=0.308$ has one of the largest high-magnification areas of known clusters" (2.1 UNCOVER Photometry)
- Target **17 compact red AGN candidates with NIRSpec/PRISM spectra (MSA IDs in Table 1; 12 unique non-stellar sources plus 3 brown dwarfs)**: coordinates RA/Dec per source given in Table 1  
  > "All have redshifts $4.5<z_{\rm spec}<8.5$." (4 Spectral Analysis); z/distance 4.5<z_spec<8.5  
  > "All have redshifts $4.5<z_{\rm spec}<8.5$." (4 Spectral Analysis); distance from NIRSpec/PRISM spectroscopic redshifts  
  > "All have redshifts $4.5<z_{\rm spec}<8.5$." (4 Spectral Analysis)

## Data provenance

- ALMA projects: 2022.1.00073.S
- bands: 1.2 mm continuum map covering the full NIRCam UNCOVER area  
  > "A wider, deeper 1.2 mm map of the full NIRCam UNCOVER area was newly obtained in Cycle 9 (#2022.1.00073.S; S. Fujimoto in prep)," (2.1 UNCOVER Photometry)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: natural resolution map, beam ~0.7-0.8 arcsec  
  > "by measuring the ALMA flux in the natural resolution map (beam $\approx0.7-0.8\ensuremath{''}$) at the NIRCam positions." (2.1 UNCOVER Photometry)
- max recoverable scale: _not stated_
- sensitivity: continuum r.m.s. 33 uJy in the deepest areas  
  > "reaching continuum r.m.s. sensitivity of $33 \rm{\mu Jy}$ in the deepest areas." (2.1 UNCOVER Photometry)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Newly obtained in Cycle 9, described as S. Fujimoto in prep; an earlier ALMA 1.2 mm map in Abell 2744 is from Fujimoto et al.  
  > "present deep ALMA 1.2 mm continuum imaging in Abell 2744." (2.1 UNCOVER Photometry); "was newly obtained in Cycle 9 (#2022.1.00073.S; S. Fujimoto in prep)," (2.1 UNCOVER Photometry)
- Other facility **JWST NIRCam (UNCOVER imaging)**: Ultradeep imaging in seven filters (F115W-F444W) used for the photometric selection of compact red sources  
  > "across seven NIRCam filters (F115W, F150W, F200W, F277W, F356W, F410M, F444W)." (2.1 UNCOVER Photometry)
- Other facility **JWST NIRSpec/PRISM MSA**: Spectroscopy of the 17 targets (7 MSA configurations), used for line fits, redshifts and black hole masses  
  > "The UNCOVER NIRSpec/PRISM observations were taken over 7 MSA configurations." (2.2.1 MSA Observational Setup)
- Other facility **Chandra ACIS-I**: X-ray imaging of the UNCOVER region, mentioned as context  
  > "The UNCOVER region additionally has full coverage with high spatial resolution X-ray imaging using the *Chandra* ACIS-I detector" (2.1 UNCOVER Photometry)
- Other facility **VLA (program 22A-017)**: Jansky Very Large Array data that may provide complementary radio imaging  
  > "There is also deep Jansky Very Large Array data from program 22A-017 (PI Murphy) that may provide complementary radio imaging." (2.1 UNCOVER Photometry)
- External data: UNCOVER DR1 photometric catalogs (incl. HST) used for initial selection and flux calibration of spectra  
  > "The initial selection of objects is based on the UNCOVER Data Release DR1 images and catalogs" (2.1 UNCOVER Photometry) [from (cite: Weaver:2023)]
- External data: Strong lensing model v1.1 of Abell 2744 used for magnifications  
  > "includes 421 cluster member galaxies and five smooth cluster-scale dark matter halos." (2.3 Gravitational magnification) [from (cite: Furtak:2022b_SLmodel)]
- External data: Parent compact red photometric sample (40 sources; 17 clean sample) used for target selection  
  > "This initial sample comprises 40 sources, the “compact red” sample." (Sample of Red Compact Sources) [from (cite: Labbe:2023uncover) (L23)]
- External data: SDSS composite AGN template used as intrinsic spectral shape for A_V estimates  
  > "First, we use the Sloan Digital Sky Survey (cite: York:2000) composite AGN templates from (cite: VandenBerk:2001)." (4.4 Balmer decrement and continuum slopes) [from (cite: VandenBerk:2001)]
- External data: Brown dwarf identification of three targets  
  > "Of these, 14 are extragalactic sources and three turn out to be cool brown dwarfs (cite: Burgasser:2023)." (4 Spectral Analysis) [from (cite: Burgasser:2023)]
- External data: Pre-launch instrumental broadening used for line-spread function  
  > "We use the predicted pre-launch instrumental broadening from JDOX (cite: Jakobsen:2022)" (4.1 Line fitting) [from (cite: Jakobsen:2022)]
- External data: Halpha-based BH mass and L5100 relations  
  > "We follow (cite: GreeneHo:2005), as updated by (cite: reinesetal2013), to calculate BH mass" (6.3 Black Hole Masses) [from (cite: GreeneHo:2005; reinesetal2013)]
- External data: Previously published broad-line AGN spectra and measurements (A2744-QSO1 and MSAID20466)  
  > "Two targets (A2744-QSO1 and MSAID20466) have previously been identified as robust broad-line AGN" (4.3 Identifying Broad Balmer Lines) [from (cite: Furtak:2023nature; Kokorev:2023)]
- Simulation/model as data: Maximal black hole bolometric luminosity function built from Sheth-Tormen halo mass function, a star formation efficiency evolving as 0.15-0.03(z-6), and z~0 BH-stellar mass relations  
  > "We start by using the Sheth-Tormen halo mass function (cite: sheth-tormen2002) at $z \sim 4-7$." (6.2 Luminosity Functions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Photometric selection of compact red sources (colour and compactness cuts, clean 17-source sample) taken from the earlier UNCOVER photometric paper  
  > "First, we briefly review the basic properties of the photometrically selected AGN sample" (3 Photometric and Spectroscopic Sample) [from L23 (cite: Labbe:2023uncover)]
- ALMA 1.2 mm map processing and photometry details are deferred to a paper in preparation  
  > "(#2022.1.00073.S; S. Fujimoto in prep)," (2.1 UNCOVER Photometry) [from S. Fujimoto in prep]
- Spectroscopic experimental design, reductions and reduced data deferred to a paper in preparation  
  > "the spectroscopic experimental design and reductions are explained by Price et al. (2023, in prep)." (2.2.1 MSA Observational Setup) [from Price et al. (2023, in prep)]
- Completeness simulation methods for the luminosity function deferred to a paper in preparation  
  > "Note that the details of our completeness simulation methods will be published in Chemerynska et al. (in prep.)." (6.2 Luminosity Functions) [from Chemerynska et al. (in prep.)]
- Forward-modeling volume calculation for the lensed luminosity function  
  > "we follow the forward-modeling method used in the *Hubble Frontier Fields* by (cite: Atek:2018)" (6.2 Luminosity Functions) [from (cite: Atek:2018)]

### Not stated but needed to reproduce (our reading)

- ALMA 1.2 mm calibration, imaging (weighting, robust, cell size), CASA version and noise-map construction are not given; only the 33 uJy rms and 0.7-0.8 arcsec beam are stated
- Which targets have ALMA coverage and their individual ALMA flux or upper limits are not tabulated
- Nested sampling code, priors on broad-line width and flux, and number of live points are not named
- Exact flux-calibration polynomial coefficients and the msaexp parameter settings are not given
- Bolometric correction used to convert L_Halpha to L_bol is not stated in the text
- Completeness simulation inputs (UV luminosity and redshift ranges, number of mock sources) are deferred to a paper in prep
- MSA slitlet extraction details and reduced spectra are deferred to Price et al. in prep

## Analysis recipe

1. **reduce NIRSpec/PRISM MSA spectra**: msaexp starting from level 2 products, 1/f noise correction, snowball masking, bias removal; JWST pipeline for WCS, slit identification, flat-fielding; 2D slits drizzled and stacked; local background subtraction; optimal Gaussian extraction  
  > "beginning from the level 2 products downloaded from MAST" (2.2.2 NIRSpec/PRISM Data Reduction); "The optimal extraction uses a Gaussian model on the collapsed spectrum with a free center and width (cite: Horne:1986)." (2.2.2 NIRSpec/PRISM Data Reduction)
   - software: msaexp, JWST reduction pipeline
   - parameter: Flux calibration: single-mask 1D spectra convolved with broad/medium band filters, compared to total photometry, with a first order polynomial wavelength-dependent correction  
  > "To flux calibrate the spectra, the single-mask extracted 1D spectra are convolved with the broad/medium band filters, and then we compare to the total photometry" (2.2.2 NIRSpec/PRISM Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit narrow-only and two-component emission-line models**: Fit Hbeta+[OIII]+Halpha+[NII] complex with a power-law continuum normalised at 5100 A; narrow-line-only fit and a narrow+broad Balmer component fit; models forward modelled through instrument broadening before the likelihood  
  > "We model the continuum as a power-law, normalized at 5100Å." (4.1 Line fitting); "Each model is then forward modeled through the instrument before calculating the likelihood." (4.1 Line fitting)
   - parameter: Narrow-line-only fit: all lines fixed to the same velocity width with a flat broad prior up to 800 km/s  
  > "where all the lines are fixed to the same velocity width, with a flat broad prior on the width up to 800 km/s." (4.1 Line fitting)
   - parameter: Two-component fit: narrow lines fixed in width over 50-150 km/s; narrow Halpha/Hbeta prior range 3-20  
  > "The ratio of narrow H$\alpha$/H$\beta$ flux is fit over a prior range of 3-20 ($A_V \sim 0-5$) under the assumption of case B recombination" (4.1 Line fitting)
   - parameter: Instrumental resolution increased by a uniform factor of 1.3; model grid oversamples native resolution by factor of four  
  > "We therefore increase the nominal resolution by a conservative, uniform factor of 1.3" (4.1 Line fitting); "we define a variable wavelength grid that oversamples the native resolution by a factor of four" (4.1 Line fitting)
   - assumption: Radial velocities of all lines tied together; broad Halpha width constrained within a factor of two of Hbeta; case B recombination  
  > "In all fits, the radial velocities of all lines are tied together." (4.1 Line fitting); "the width of H$\alpha$ is constrained to fall within a factor of two of H$\beta$." (4.1 Line fitting)
   - fitting: Likelihood-based fit with eight free parameters in the narrow-only model plus four more in the two-component model; nested sampling is referred to for uncertainties  
  > "In the first fit we constrain eight free parameters (including a power-law continuum) and in the second model we add four additional free parameters." (4.1 Line fitting); "where $\sigma$ is measured as the 68% distribution from the nested sampling" (4.3 Identifying Broad Balmer Lines)
   - validation: Additional two-component fit with Halpha/Hbeta fixed to 4-6; broad Halpha widths agree within 5-10% in all but one case  
  > "We find that in all cases but one, the derived H$\alpha$ width agrees within 5-10% of our fiducial fits." (4.1 Line fitting)
3. **classify objects as broad-line AGN**: Apply three criteria: chi2 improvement over narrow-only, broad Halpha FWHM above 2000 km/s, and broad-line detection above 5 sigma  
  > "we insist that the fit improvement in $\chi^2$ be better than $3 \sigma$ ($\Delta \chi^2 > 11.5$ for four additional degrees of freedom)" (4.3 Identifying Broad Balmer Lines); "Second, we require that the two-component broad H$\alpha$ have FWHM$>2000$ km/s." (4.3 Identifying Broad Balmer Lines)
   - parameter: Final criterion: remove any object with less than 5 sigma broad-line detection  
  > "Finally, we remove any object with $<5 \sigma$ detection of a broad line" (4.3 Identifying Broad Balmer Lines)
   - assumption: 2000 km/s is a conservative limit compared to the 1200 km/s bimodality  
  > "We choose 2000 km/s as a conservative limit, compared to the bimodality at 1200 km/s identified by (cite: Hao:2005)." (4.3 Identifying Broad Balmer Lines)
   - fitting: _not stated_
   - validation: Outflow origin of broad lines judged unlikely because narrow lines are narrower than 500 km/s  
  > "we know that they are $<500$ km/s, so that the broad permitted lines almost certainly arise from the broad-line region." (4.3 Identifying Broad Balmer Lines)
4. **measure continuum slopes and dust reddening**: Fit UV and optical sides separately as power laws in f_lambda; derive A_V from the SDSS composite template (A_V,0.45) and from an empirical UV-slope fit with a scattered light fraction (A_V,fit), both with an SMC reddening law  
  > "We fit the UV and optical sides of the spectra separately to derive $\beta_{\rm UV}$ and $\alpha_{\rm opt}$ as power-laws in $f_{\lambda}$." (4.4 Balmer decrement and continuum slopes); "In each case we allow a free extinction parameter characterized by the SMC reddening curve (cite: Gordon:2003)." (4.4 Balmer decrement and continuum slopes)
   - parameter: SDSS template fit to lambda<3500 A and lambda>4300 A  
  > "each spectrum in the range $\lambda < 3500$Å and $\lambda > 4300$Å" (4.4 Balmer decrement and continuum slopes)
   - assumption: Red continuum assumed dominated by AGN light; intrinsic optical slope 0.45 for A_V,0.45  
  > "All of our determinations of $A_V$ are under the assumption that the red continuum is dominated by AGN light" (4.4 Balmer decrement and continuum slopes); "estimated from the continuum slope assuming an intrinsic AGN power-law slope of $\alpha_{\rm opt} = 0.45$ and an SMC reddening law" (Table 2)
   - fitting: _not stated_
   - validation: The two A_V values bracket a reasonable range; Halpha-derived L5100 compared with continuum L5100, agreeing within a factor of two  
  > "These two reddening values thus bracket a reasonable range of reddening levels" (4.4 Balmer decrement and continuum slopes); "they agree within a factor of two" (6.1 Origin of the Continuum)
5. **derive black hole masses and bolometric luminosities**: Single-epoch virial BH mass from broad Halpha luminosity and FWHM following Greene and Ho as updated by Reines et al.; BLR size from AGN luminosity  
  > "We follow (cite: GreeneHo:2005), as updated by (cite: reinesetal2013), to calculate BH mass based on the luminosity $L_{\rm H\alpha}$ and velocity FWHM(H$\alpha$) of the broad H$\alpha$ line." (6.3 Black Hole Masses)
   - assumption: BLR assumed a virial dynamical tracer; virial equilibrium acknowledged as unverified  
  > "Of course, we do not know that the BLR is in virial equilibrium" (6.3 Black Hole Masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **compute UV and bolometric luminosity functions**: Forward-modelled completeness with mock red AGN deflected through the lens model, selection function weights the comoving volume integrated over the sufficiently magnified source plane; 0.5 mag UV bins and 1 dex L_bol bins; Poisson-like uncertainties from 10^4 resampled luminosities  
  > "The selection function is used to weight the co-moving volume element which is then integrated over the source plane area of sufficient magnification required to detect each object in all bands given the UNCOVER mosaic depths" (6.2 Luminosity Functions); "The number count uncertainties are derived by drawing $10^4$ random luminosities" (6.2 Luminosity Functions)
   - assumption: Concordance cosmology H0=70, Omega_Lambda=0.7, Omega_M=0.3; bolometric LF assumes maximum UV completeness and no magnification (lower limit)  
  > "we assume a concordance cosmology with H$_0$=70, $\Omega_{\Lambda} = 0.7$, $\Omega_{M} = 0.3$" (1 Introduction); "the thus derived bolometric luminosity function remains a lower limit." (6.2 Luminosity Functions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **msaexp** 0.3.4: NIRSpec MSA data reduction from level 2 products  
  > "beginning from the level 2 products downloaded from MAST" (2.2.2 NIRSpec/PRISM Data Reduction); "msaexp: NIRSpec analyis tools, 0.3.4" (References)
- **JWST reduction pipeline** : WCS, slit identification, flat-fielding and photometric correction  
  > "to identify each slit, and then to perform flat-fielding and to apply photometric correction." (2.2.2 NIRSpec/PRISM Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of compact red UNCOVER sources with definitive broad-line Halpha (FWHM>2000 km/s) | 60% | not stated | percent | 3 | 60% show definitive evidence for broad-line H$\alpha$ with FWHM$>2000$ km/s |
| Confirmed broad-line AGN among 17 targets | 11/17 = 65% | not stated | percent | 3 | Therefore 11/17 $= 65\%$ of the sample are confirmed as broad line AGN. |
| Confirmed AGN fraction among unique extragalactic targets | 9/12 = 75% | could be as high as 100% | percent | 3 | the confirmed AGN fraction among the targetted extragalactic objects in our sample is 9/12 $= 75\%$ |
| AGN fraction among z_phot>5 galaxies with F277W-F444W>1 in UNCOVER | at least 33%, rising to at least 80% for F277W-F444W>1.6 | lower limits | percent | 3 | at least $33\%$ are AGN regardless of compactness, climbing to at least $80$% AGN for sources with F277W$-$F444W$>1.6$ |
| Mean UV slope beta_UV (definitive broad-line sources) | -1.5 | 0.7 | dimensionless | 4 | For the definitive and unconfirmed broad-line sources, we find $\langle \beta_{\rm UV} \rangle = -1.5 \pm 0.7$ and $\langle \beta_{\rm UV} \rangle = -1.9 \pm 0.2$ respectively. |
| Mean optical slope alpha_opt (AGN sample) | 0.5 | 0.3 | dimensionless | 4 | $\langle \alpha_{\rm opt} \rangle = 0.5 \pm 0.3$, $\langle \alpha_{\rm opt} \rangle = 0.9 \pm 0.4$ for AGN and unconfirmed samples respectively |
| Black hole masses of confirmed AGN | 10^7-10^9 | not stated | Msun | 5 | The confirmed AGN have black hole masses of $10^7-10^9$ $M_{\odot}$. |
| Eddington ratio range | ~10-40% | not stated | percent of Eddington | 5 | radiating at $\sim 10-40\%$ of Eddington |
| Number density of the red AGN | ~1e-5 | not stated | Mpc^-3 mag^-1 | 6 | The number densities are surprisingly high at $\sim10^{-5}$ Mpc$^{-3}$ mag$^{-1}$ |
| Black hole mass of MSAID45924 | ~1e9 | not stated | Msun | 5 | stands out for its high SNR and black hole mass of $M_{\rm BH}$$\approx 10^9$ $M_{\odot}$. |
| Implied star formation rate if all UV arises from star formation | 1.5 | not stated | Msun/yr | 4 | we find rates of $\langle {\rm SFR} \rangle = 1.5$ $M_{\odot}$/yr. |
| ALMA 1.2 mm continuum rms in deepest areas | 33 | not stated | uJy | 0 | reaching continuum r.m.s. sensitivity of $33 \rm{\mu Jy}$ in the deepest areas. |
| Targets with ALMA coverage that favoured SED solutions without an AGN component | 3/20 | not stated | dimensionless | 0 | only 3/20 targets with ALMA coverage favored SED solutions without an AGN component |

## Qualitative findings

- The rest-frame optical continuum is dominated by a dusty broad-line AGN, while the origin of the UV light (scattered AGN light or low-level star formation) remains undetermined  
  > "Overall, we conclude that the rest-frame optical continuum is dominated by a dusty broad-line AGN continuum, and that more work is needed to definitively determine the origin of the UV emission." (6.1 Origin of the Continuum)
- Number densities of red AGN exceed UV-selected AGN at similar magnitudes by roughly two orders of magnitude  
  > "We confirm the result from L23 that the number densities of these red-selected AGN are higher by roughly two orders of magnitude compared to the UV-selected AGN at similar magnitudes." (6.2 Luminosity Functions)

## Claim tuples

- H: The compact red z>5 sources are dominated by AGN rather than dusty star formation | E: NIRSpec/PRISM spectroscopy of 17 UNCOVER-selected sources with line fitting and broad Halpha criteria | R: 11/17 (9/12 unique extragalactic) show broad Halpha with FWHM>2000 km/s; 3 are brown dwarfs; 3 inconclusive | F: The majority of compact red sources are dust-reddened broad-line AGN | **supported**
- H: A refined NIRCam colour selection yields a high AGN fraction while excluding brown dwarfs | E: Define v-shape and compact red cuts with F115W-F200W>-0.5 and F277W-F356W>0.7, and count spectroscopically confirmed AGN | R: At least 75% AGN in the compact red selection and at least 33% in the v-shape selection | F: Updated photometric criteria select red z>5 AGN with high yield | **supported**
- H: The UV component of the red AGN arises from scattered AGN light or star formation | E: Compare observed L3000 with expectations from L5100 for two assumed intrinsic slopes | R: Observed L3000 is 1-3% or 10-20% of expected, depending on the assumed intrinsic slope | F: The UV origin cannot be determined from spectral slopes alone | **partially**
- H: The red AGN number density is high relative to UV-selected AGN and challenges black hole growth models | E: Lensing-corrected UV and bolometric luminosity functions from the spectroscopic sample compared with a maximal halo-based model | R: Densities of ~1e-5 Mpc^-3 mag^-1, ~100 times the faintest UV-selected quasars; bright-end density approaches the maximal number of accreting black holes | F: Models require very high occupation fractions or super-Eddington growth | **supported**

## Reasoning

- Why this data: Targets with deep ALMA limits were prioritised because ALMA non-detections effectively rule out dusty star formation as the origin of the red continuum  
  > "In nearly all cases, the highest priority targets are those with deep ALMA limits, because in these cases we can effectively rule out dusty star formation as the origin of the red continuum" (3.1 Sample of Red Compact Sources)
- Why this method: Focus on broad Halpha because of higher signal-to-noise than Hbeta given the dust reddening  
  > "we focus exclusively on identifying broad H$\alpha$, since given the typical Balmer decrements of $\sim 5-10$, we have substantially higher signal-to-noise in H$\alpha$ than H$\beta$." (4.3 Identifying Broad Balmer Lines)
- Alternative: Outflows as the origin of the broad lines were considered and rejected because narrow lines are narrower than 500 km/s  
  > "Another question is whether the broad lines might arise from outflows, rather than the broad-line region of the AGN." (4.3 Identifying Broad Balmer Lines)
- Alternative: Broad-line Balmer decrements were not trusted because of self-absorption in the broad-line region; reddening taken from continuum slopes instead  
  > "We thus base our reddening estimates on the continuum slopes." (4.4 Balmer decrement and continuum slopes)
- How they decided it was enough: _not stated_
- Limitation (authors): Balmer decrements are poorly constrained because of degeneracy with broad lines  
  > "Because of the degeneracy with the broad Balmer lines, the Balmer decrements are not well constrained in general." (4.4 Balmer decrement and continuum slopes)
- Limitation (authors): Bolometric luminosity function is a lower limit  
  > "the thus derived bolometric luminosity function remains a lower limit." (6.2 Luminosity Functions)
- Limitation (authors): Narrow-line widths have systematic uncertainty from the uniform LSF correction  
  > "the inferred widths for the narrow-line components suffer from a systematic uncertainty." (4.1 Line fitting)
- Limitation (authors): Virial equilibrium of the BLR is assumed, not known  
  > "Of course, we do not know that the BLR is in virial equilibrium" (6.3 Black Hole Masses)
- Caveat (inferred, ours): ALMA is used only as a prior-based photometry constraint; the ALMA reduction is not described here and no per-source ALMA fluxes are given
- Caveat (inferred, ours): Low spectral resolution (R=100-500) limits separation of broad and narrow components; classification depends on a 2000 km/s cut
- Caveat (inferred, ours): Bolometric correction and BH mass calibration (local relations) are applied at z>5 without independent checks
- Caveat (inferred, ours): Only 12 unique non-stellar sources, so luminosity function bins hold 1-4 objects each

## Reproducibility

- Data public (paper): UNCOVER photometric catalogs and the lens model are public; MAST level 2 NIRSpec data are used  
  > "have been made available to the public, and the lens model is also publicly available" (2.1 UNCOVER Photometry); "beginning from the level 2 products downloaded from MAST" (2.2.2 NIRSpec/PRISM Data Reduction)
- Products in archive: _not stated_
- Missing: ALMA 1.2 mm reduction and flux extraction (paper in prep by S. Fujimoto)
- Missing: Reduced PRISM spectra and slitlet extraction details (Price et al. in prep)
- Missing: Completeness simulation details (Chemerynska et al. in prep)
- Missing: Fitting code, priors in full, and the nested sampler used
- Missing: Per-source ALMA measurements and bolometric correction
- Data volume (inferred): ALMA 1.2 mm map is small (tens of GB at most); the JWST NIRSpec level 2 products are the bulk of the data
- Score (inferred): 2/5, JWST data and catalogs are public, but ALMA processing, spectral reductions, completeness simulations and fitting code are deferred to papers in preparation or not given, and the ALMA role is minor.
- Rediscovery candidate: no, ALMA plays only a minor photometric role and key reduction and simulation steps are deferred to unpublished papers, so the recipe is not complete.

## Links

- Method: (cite: Bezanson:2022) (UNCOVER survey design and photometric component)
- Method: (cite: Weaver:2023) (UNCOVER photometric catalog)
- Method: (cite: Furtak:2022b_SLmodel) (Strong lensing model of Abell 2744)
- Method: (cite: Brammer:22) (msaexp NIRSpec reduction tools)
- Companion: (cite: Labbe:2023uncover) (Parent photometric sample of compact red sources (L23))
- Companion: (cite: Fujimoto:2023) (Earlier deep ALMA 1.2 mm continuum imaging in Abell 2744)
- Companion: (cite: Furtak:2023nature) (Triply-imaged z=7 AGN A2744-QSO1)
- Companion: (cite: Burgasser:2023) (Brown dwarfs among UNCOVER targets)
- Related: UNCOVER (JWST Cycle 1 Treasury)
- Related: ALMA Cycle 9 1.2 mm map of Abell 2744 (2022.1.00073.S)

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 62,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
