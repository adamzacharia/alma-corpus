# A Comparison of the Stellar, CO, and Dust-continuum Emission from Three Star-forming HUDF Galaxies at z ∼ 2

`2020ApJ...899...37K` | The Astrophysical Journal 2020 | first author: Kaasinen, Melanie | arXiv: 2007.03697 | DOI: 10.3847/1538-4357/aba438

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do the spatial extents (half-light radii) of stellar, CO and dust-continuum emission compare in three massive main-sequence-like HUDF galaxies at z~1.4-2.7, and are their kinematics rotation-dominated?  
  > "we test how the spatial extent (quantified by the half-light radii) of dust continuum, CO and rest-frame optical emission compare for three extended, MS galaxies at $z\sim 2$." (Introduction)
- Target **ALPS.1 / ALPS.2 / ALPS.3 (HUDF)**: coordinates RA/Dec partly given (e.g. :32:34.44, :46:59.8 for ALPS.1; hours/degrees truncated in the text)  
  > "| z$_\mathrm{CO}$ | $1.4140$ | $1.5504$ | $2.6961$ |" (Table 1); z/distance z_CO = 1.4140, 1.5504, 2.6961  
  > "| z$_\mathrm{CO}$ | $1.4140$ | $1.5504$ | $2.6961$ |" (Table 1); distance from CO redshifts; cosmology H0=70, OmegaM=0.3, OmegaL=0.7  
  > "| z$_\mathrm{CO}$ | $1.4140$ | $1.5504$ | $2.6961$ |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00173.S, 2016.1.00324.L, 2017.1.00270.S
- bands: Band 6 (1.3 mm) continuum and Band 3 CO  
  > "we use two sets of ALMA Band 3 (84-115 GHz; 2.6-3.6 mm) data." (2.3 CO Line (Band 3) Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ASPECS Band 6: C43-3; ASPECS Band 3: C40-3; ALPS Band 3: C43-5  
  > "These alma observations were conducted in the C43-5 configuration (minimum baseline of 15 m and maximum baseline of 2.5 km)." (2.3 CO Line (Band 3) Observations)
- baselines: _not stated_
- angular resolution: Band 6 beams 0.48-0.59 arcsec; CO beams 0.58-0.88 arcsec  
  > "| Beam FWHM ($''\times''$) | $0.59 \times 0.49$ | $0.56 \times 0.47$ | $0.48 \times 0.40$ |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALPS Band 3: Jan 4-11, 2018; ASPECS Band 6: Mar 10, 2017 to Jul 13, 2018  
  > "taken between January 4-11, 2018" (2.3 CO Line (Band 3) Observations)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (ALPS.1, 2), 3-2 (ALPS.3) (not stated)
- Other facility **HST/WFC3 F160W**: 1.6 micron stellar continuum images (XDF)  
  > "we rely on the hst/WFC3 F160W images from the XDF data release" (3.2 Stellar Masses and SFRs)
- External data: UV-NIR photometry for SED fitting  
  > "For the UV-NIR photometry we use the values from the (cite: 2013ApJS..207...24G) catalogue" (3.2 Stellar Masses and SFRs) [from (cite: 2013ApJS..207...24G)]
- External data: Axis ratios and position angles from F160W used as initial estimates  
  > "we use the axis ratios and position angles determined by (cite: 2012ApJS..203...24V) from the F160W images" (4.3 Measuring Galaxy Sizes) [from (cite: 2012ApJS..203...24V)]
- External data: CO(3-2)/CO(1-0) ratio r31 = 0.79 ± 0.21 for ALPS.3  
  > "we apply the measured luminosity ratio $r_\mathrm{31} = L_\mathrm{CO (3-2)}^{\prime}/L_\mathrm{CO(1-0)}^{\prime} = 0.79 \pm 0.21$" (3.1) [from (cite: Riechers_2020)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration scripts for CASA, no modifications  
  > "the standard pipeline produced $uv$-data products of high quality and was therefore used without additional modifications." (2.4 Data Reduction and Imaging)
- casa version: CASA 5.4.0 (concatenation and imaging)  
  > "The subsequent concatenating and imaging was carried out using casa version 5.4.0." (2.4 Data Reduction and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3 ALPS: bandpass J0522-3627, flux J0329-2357, phase J0342-3007  
  > "The Bandpass, flux and phase calibrators were J0522-3627, J0329-2357 and J0342-3007, respectively." (2.3)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with mosaic gridding  
  > "We jointly image the two sets of $uv$-data via casa’s `TCLEAN`, by applying the “mosaic” gridding option." (2.4.1)
- deconvolver: multiscale for moment-0 maps, scales up to 2 arcsec  
  > "applying the “multiscale” deconvolver (with a deconvolution scale of up to $2''$)" (2.4.2)
- weighting robust: Band 6: natural; CO: natural for ALPS.2 and 3, robust for ALPS.1 (Table 1 lists 0.5)  
  > "For the final images of ALPS.2 and 3 we use natural weighting, whereas for ALPS.1 we use robust weighting" (2.4.2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask 3 arcsec radius, clean to 2 sigma  
  > "clean to $2\sigma$, within a circular mask of $3''$ radius" (2.4.1)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub attempted; no continuum recovered, so redundant  
  > "recover no significant continuum emission, rendering this step redundant" (2.4.2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ASPECS LP and ALPS/Dunlop data combined in uv-plane; 4 of 32 ASPECS spws matching Dunlop  
  > "we select the four (out of 32) spectral windows from the ASPECS LP that match those of (cite: 2017MNRAS.466..861D)" (2.4.1)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Moment-0 velocity range defined by 99.99th percentile  
  > "(the 99.99th percentile range, as in (cite: 2019ApJ...882..136A))" (2.4.2) [from (cite: 2019ApJ...882..136A)]
- Flux measurement via residual scaling method  
  > "applying the residual scaling method (cite: 2019ApJ...881...63N)" (3.1) [from (cite: 2019ApJ...881...63N)]
- alpha_CO from Eq. 2 of Tacconi+2018; metallicity from Genzel+2015 Eq. 12a  
  > "We calculate the CO-to-molecular gas mass conversion factor, $\alpha_\mathrm{CO}$, according to the Equation (2) of (cite: 2018ApJ...853..179T)." (3.1) [from (cite: 2018ApJ...853..179T); (cite: 2015ApJ...800...20G)]
- Adapted MAGPHYS high-z SED fits  
  > "we apply the adaptation to the high-redshift extension of the code, developed by (cite: 2019ApJ...882...61B)." (3.2) [from (cite: 2019ApJ...882...61B)]

### Not stated but needed to reproduce (our reading)

- Robust values for the Band 3 images beyond the table weighting parameter, cell size and image size
- Exact spectral windows and channel ranges used for the CO moment-0 maps
- Line-free channel definitions
- Details of the SED fit priors and aperture photometry used
- Excitation ratio r21 values adopted for ALPS.1 and 2
- How the major-axis profiles and asymmetry were measured in detail
- Qubefit priors and number of MCMC steps

## Analysis recipe

1. **Image Band 6 continuum and Band 3 CO**: Pipeline-calibrated data concatenated and imaged with tclean (mosaic); moment-0 from single-channel image across line  
  > "we create a single-channel image over the extent of the line emission" (2.4.2)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared moment-0 maps with 50 and 100 km/s cube-derived maps  
  > "We compare these moment-0 maps to maps obtained from 50 and 100 $\ensuremath{\rm{km}\, \rm{s}^{-1}}$ data cubes" (2.4.2)
2. **Measure total flux densities, CO luminosities, gas and dust masses**: Residual-scaling flux in circular apertures; L'CO via Solomon+1992; molecular masses via metallicity-based alpha_CO; dust masses from optically thin MBB  
  > "we assume that the dust emission is optically thin and can be modeled by a modified blackbody" (3.1)
   - parameter: Apertures 1.5, 2, 1.5 arcsec for ALPS.1, 2, 3  
  > "circular apertures of $1{\ooalign{{$.$}\cr{$''$}}}5,~ 2''$ and $1{\ooalign{{$.$}\cr{$''$}}}5$ for ALPS.1, 2 and 3, respectively" (3.1)
   - assumption: T_dust = 25 K, beta = 1.8, kappa_850um = 0.77 cm^2/g, factor 1.36 for He  
  > "taking $\kappa_{{\nu}_{850 \mathrm{\mu m}}} = 0.77\, \mathrm{g^{-1}cm^2}$ (cite: 1984ApJ...285...89D) and $\beta=1.8$" (3.1)
   - fitting: _not stated_
   - validation: Compared to ASPECS LP and Dunlop+2017 flux densities  
  > "We compare the flux densities measured here (Table [2](#tab:derived_prop)) to those derived using the ASPECS LP data only." (3.1)
3. **SED fitting for stellar mass, SFR**: MAGPHYS high-z with Battisti+2019 adaptation (ALPS.1, 3) and AGN version (ALPS.2)  
  > "for ALPS.2 we apply the adapted version of that accounts for a contribution by AGN to the dust heating" (3.2)
   - software: MAGPHYS
   - assumption: Chabrier IMF; 0.3 dex uncertainty floor on M* and SFR  
  > "we adopt an uncertainty floor on the stellar masses and SFRs of $\pm\sim0.3$ dex" (3.2)
   - fitting: medians with 16th-84th percentiles  
  > "we quote the median values with uncertainties representing the 16th and 84th percentiles" (3.2)
   - validation: _not stated_
4. **Measure half-light radii**: Image-plane GALFIT Sersic fits in 4 arcsec region (n free for F160W, n=1 for CO/dust); uv-plane fits with uvmultifit and GILDAS uv_fit as cross-check; ALPS.3 upper limits from Gaussian deconvolution  
  > "We therefore keep the Sérsic index as a free parameter when fitting the F160W emission but fix the Sérsic index to match an exponential profile ($n=1$) for the CO and dust emission." (4.3.1)
   - software: GALFIT, uvmultifit, GILDAS
   - parameter: PA and inclination within ±10 deg, centres within ±0.2 arcsec of van der Wel values  
  > "constrain the source centres to vary by $\pm\, 0{\ooalign{{$.$}\cr{$''$}}}2$" (4.3.1)
   - fitting: GALFIT chi-square; uncertainties from fits to simulated maps  
  > "We therefore quote uncertainties based on the distribution of best-fit values for fits to simulated maps." (4.3.1)
   - validation: Simulated recovery tests; uv vs image-plane comparison  
  > "We perform multiple tests to check to what extent we can recover the source sizes" (4.3.1)
5. **Kinematic modelling and dynamical masses**: Qubefit thin exponential disk 3D model fit with MCMC to 50 km/s cubes; Mdyn = v^2 r/G within 2 r_1/2 and 6 r_d  
  > "The full parameter space is sampled via the Markov Chain Monte Carlo method" (5.2)
   - software: Qubefit
   - parameter: fit to 3 arcsec diameter regions  
  > "We fit the model cube to regions of 3$''$ diameter" (5.2)
   - assumption: thin disk, circular velocities only; 1.6 um traces stellar mass  
  > "We thereby assume that the 1.6 μm emission perfectly traces the stellar mass" (5.3)
   - fitting: chi^2 with bootstrapping for pixel correlation; priors not stated  
  > "takes into account the spatial correlation between pixels via a bootstrapping analysis" (5.2)
   - validation: Compared with 3D Barolo  
  > "consistent with the best-fit parameters inferred using the 3D modeling algorithm (cite: 2015MNRAS.451.3021D)" (5.2)

## Software

- **CASA** 5.4.0: calibration, concatenation, imaging  
  > "casa version 5.4.0" (2.4)
- **GALFIT** : 2D Sersic fits to F160W, CO and dust maps  
  > "Chien Peng (GALFIT)" (Acknowledgments)
- **uvmultifit** : uv-plane source fitting  
  > "Ivan Martí-Vidal (uvmultifit)" (Acknowledgments)
- **GILDAS** : uv-plane source fitting (uv_fit)  
  > "GILDAS (cite: 2013ascl.soft05010G)" (Software)
- **Qubefit** : 3D kinematic modelling  
  > "python-based kinematic modeling tool" (5.2)
- **MAGPHYS** : SED fitting (adapted versions)  
  > "two, adapted, versions of the high-redshift extension to the SED-fitting algorithm" (3.2)
- **3D Barolo** : cross-check of kinematic fits  
  > "Enrico di Teodoro (3D Barolo)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FIR luminosity ALPS.1 | 0.78e12 | 0.04e12 | Lsun | 3 | $(0.78\, \pm\, 0.04) \times 10^{12}$ |
| CO(3-2)/CO(1-0) ratio r31, ALPS.3 (literature) | 0.79 | 0.21 | dimensionless | 2 | $r_\mathrm{31} = L_\mathrm{CO (3-2)}^{\prime}/L_\mathrm{CO(1-0)}^{\prime} = 0.79 \pm 0.21$ |
| sSFR/sSFR_MS | 0.2-0.4 | not stated | dimensionless | 3 | sSFR/sSFR$_\mathrm{MS} = 0.2-0.4$ |
| ALPS.2 dynamical mass within 2 r_1/2^CO ~ 9.2 kpc | 2.7e11 | 0.3e11 | Msun | 5 | $(2.7\,\pm\, 0.3) \times 10^{11}\ensuremath{\rm{M}_{\odot}}$ within $2 r_\mathrm{1/2}^\mathrm{CO} \approx 9.2$  kpc |
| ALPS.2 vrot/sigma | 4.9 | 0.9 | dimensionless | 5 | $v_\mathrm{rot}/\sigma = 4.9\pm 0.9$ |
| ALPS.2 max rotation velocity | 355 | 14 | km/s | 5 | $355 \pm 14 \, \ensuremath{\rm{km}\, \rm{s}^{-1}}$ |
| Gas fraction Mmol/M* | 0.4-0.8 | not stated | dimensionless | 2 | $\mathrm{M_{mol}}/\ensuremath{\rm{M}_{*}}= 0.4-0.8$ |
| Gas-to-dust ratio | ~100-300 | not stated | dimensionless | 2 | $\mathrm{M_{mol}}/\mathrm{M_{dust}} \sim 100-300$ |

## Qualitative findings

- CO emission is at least 30% more compact than rest-frame optical in all three; dust is more compact for ALPS.1 and 3 but similar in extent for ALPS.2  
  > "for all three galaxies the CO emission appears $\gtrsim 30\%$ more compact than the stellar emission." (abstract)

## Claim tuples

- H: CO and dust are more compact than stars in MS galaxies at z~2 | E: Sersic fits to ALMA CO, 1.3 mm and HST F160W maps | R: CO >=30% smaller than F160W in all three; dust smaller in ALPS.1 and 3, similar in ALPS.2 | F: Gas and dust are generally more compact than stars, though one source shows extended dust | **supported**
- H: The galaxies are rotation-dominated disks | E: Qubefit 3D modelling and PV diagrams of CO | R: clear velocity gradients; high vrot/sigma | F: All three consistent with rotation-dominated disks | **supported**

## Reasoning

- Why this data: CO- and dust-bright sources with extended optical sizes selected from ASPECS LP, requiring CO brightness to resolve in ~5 h  
  > "We required the sources to be CO-bright in order to resolve their emission" (2.1)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N and resolution prevent multi-component decomposition and free Sersic index for CO/dust; sizes uncertain  
  > "does not allow us to decompose the data into multiple components" (6.1.1)
- Caveat (inferred, ours): Sizes depend on assumed n=1 and low S/N maps
- Caveat (inferred, ours): Visibility weighting between datasets changes sizes by up to 40%
- Caveat (inferred, ours): Small sample of three galaxies selected for extended optical morphology
- Caveat (inferred, ours): Stellar mass systematics (factor 2) from SED fits

## Reproducibility

- Data public (paper): Projects listed in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: 2012.1.00173.S, 2016.1.00324, 2016.1.00324.L" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact tclean parameters (cell, image size, spw/channel selection)
- Missing: SED fitting priors and modified MAGPHYS versions
- Missing: Qubefit priors and chain settings
- Data volume (inferred): Several hundred GB (three projects incl. large program mosaics)
- Score (inferred): 3/5, Data are archival/accessible and software named, but many imaging and fitting parameters are unspecified.
- Rediscovery candidate: no, Key settings missing and analysis relies on custom SED fits and external catalogs.

## Links

- Method: (cite: 2019ApJ...881...63N) (residual scaling flux method)
- Method: (cite: 2019ApJ...882...10N) (Qubefit)
- Method: (cite: 2019ApJ...882...61B) (adapted MAGPHYS)
- Companion: (cite: 2020arXiv200207199G) (ASPECS LP 1.2 mm continuum)
- Companion: (cite: 2019ApJ...882..139G) (ASPECS LP CO line search)
- Companion: (cite: 2017MNRAS.466..861D) (Band 6 HUDF data)
- Related: ASPECS Large Program
- Related: HUDF

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 54,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
