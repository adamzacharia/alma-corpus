# Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies

`2015ApJ...811..124S` | The Astrophysical Journal 2015 | first author: Spilker, J. S. | arXiv: 1508.07369 | DOI: 10.1088/0004-637X/811/2/124

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the sizes, structure and kinematics of the cool molecular gas (low-J CO) versus dust in two lensed SPT DSFGs, and what do they imply for alpha_CO and the star formation relation?  
  > "We use the ATCA CO observations and comparable resolution Atacama Large Millimeter/submillimeter Array dust continuum imaging of the same objects to constrain the CO-H$_2$ conversion factor with three different procedures" (abstract)
- Target **SPT0346-52**: coordinates _not stated_; z/distance z=5.66  
  > "SPT-S J034640-5204.9 (SPT0346-52), at $z=5.66$, is among the highest-redshift DSFGs known." (1 Introduction); distance from _not stated_
- Target **SPT0538-50**: coordinates _not stated_; z/distance z=2.78  
  > "SPT-S J053816-5030.8 (SPT0538-50), at $z=2.78$, is representative of the typical DSFG population in redshift, 870 $\mu\rm{m}$ flux density, and dust temperature." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00957.S, 2011.0.00958.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA 870 um: ~0.5" in extended configuration (~1.5" in earlier data)  
  > "These new data were taken in an extended array configuration available in ALMA Cycle 0, and reach $\sim$0.5” resolution." (3 Lens Modeling)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: CO(1-0), CO(2-1), CO(3-2) and 3.3 mm continuum imaging (primary data)  
  > "Table [1](#tab:obstable) summarizes the ATCA observations of CO lines in SPT0346-52 and SPT0538-50." (2 Observations)
- External data: Dust photometry for SPT0346-52 used for dust SED fitting  
  > "We determine the dust masses of SPT0346-52 and SPT0538-50 by fitting to the photometry given in (cite: weiss13) and (cite: bothwell13b), respectively." (5.2.1 Gas-to-Dust Ratio) [from (cite: weiss13)]
- External data: Stellar mass of SPT0538-50 (3.3 +/- 1.5 x 10^10 Msun)  
  > "The stellar mass of SPT0538-50 has been estimated by (cite: bothwell13b) as $3.3 \pm 1.5 \times 10^{10}$ $\rm{M}_\odot$" (5.2.2 Dynamical Constraints) [from (cite: bothwell13b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 7 mm: PKS1934-638 (most tracks); 3 mm: Uranus  
  > "For most tracks, the quasar PKS1934-638 was observed for flux calibration" (2.1 ATCA Observations: 7 mm Band); "while Uranus was observed for flux calibration" (2.2 ATCA Observations: 3 mm Band)
- flux scale uncertainty: 7 mm within 10%; 3 mm ~15%  
  > "Repeated observations of amplitude calibration sources indicate that the absolute flux scale is accurate to within 10%." (2.1 ATCA Observations: 7 mm Band); "The absolute flux scale at 3 mm is expected to be accurate to within $\sim$15%" (2.2 ATCA Observations: 3 mm Band)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "were combined and inverted using natural weighting." (2.1 ATCA Observations: 7 mm Band)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 3 mm CO(3-2) data continuum-subtracted  
  > "The data were continuum-subtracted and imaged using natural weighting to maximize sensitivity to weak emission" (2.2 ATCA Observations: 3 mm Band)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: H75/H214, 1.5 km and 6 km configurations combined  
  > "The three array configurations provide good $uv$ coverage on baselines from $\sim$100 m – 6 km, and were combined" (2.1 ATCA Observations: 7 mm Band)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modeling procedure (SIE lens, visibility-space Bayesian MCMC)  
  > "Our lens modeling procedure follows that described by (cite: hezaveh13)." (3 Lens Modeling) [from (cite: hezaveh13)]
- Updated 870 um lens models to be presented elsewhere  
  > "while the updated 870 $\mu\rm{m}$ lens models will be presented in full in Spilker et al., *in prep*." (3 Lens Modeling) [from Spilker et al., in prep.]

### Not stated but needed to reproduce (our reading)

- MCMC sampler, priors, chain length and convergence criteria
- Calibration software and versions (ATCA/ALMA reduction packages)
- Best-fit lens parameters fixed from ALMA models
- Line-free channels and continuum subtraction details
- MAGPHYS fit configuration
- Stellar mass upper limit for SPT0346-52 (Ma et al. in prep.)

## Analysis recipe

1. **Image ATCA CO data**: Combine array configurations, natural weighting, channel maps  
  > "The three array configurations provide good $uv$ coverage on baselines from $\sim$100 m – 6 km, and were combined and inverted using natural weighting." (2.1 ATCA Observations: 7 mm Band)
   - fitting: _not stated_
   - validation: Noise normalized by differencing successive visibility pairs  
  > "We ensure proper normalization of the noise levels of each dataset by differencing successive pairs of visibilities on the same baseline and polarization." (2.1 ATCA Observations: 7 mm Band)
2. **Visibility-plane lens modeling of CO and continuum**: Gaussian source-plane components per velocity channel lensed with fixed ALMA-derived SIE lens, fit to visibilities  
  > "we fit lensing models directly to the measured visibilities. As in (cite: hezaveh13), we use a Bayesian Markov Chain Monte Carlo (MCMC) fitting procedure." (3 Lens Modeling)
   - parameter: Each Gaussian has up to four free parameters: centroid, flux, size  
  > "Each profile has up to four free parameters, namely, the two-dimensional centroid of the source and its intrinsic flux and size." (3 Lens Modeling)
   - assumption: Lens parameters fixed to ALMA best fit  
  > "so we use the best-fit lens properties derived from the ALMA continuum data to model the source-plane in the ATCA CO data." (3 Lens Modeling)
   - fitting: MCMC with chi^2 metric  
  > "using the $\chi^2$ metric to determine the quality of the fit." (3 Lens Modeling)
   - validation: Residuals consistent with noise; alternative channelizations tested  
  > "We have modeled alternative channelizations of the data, with velocity bins ranging from 100–400 $\rm{km\,s}^{-1}$" (4.1 SPT0346-52)
3. **Derive alpha_CO by three methods**: Gas-to-dust ratio (MAGPHYS dust mass), dynamical mass, and Narayanan et al. CO surface density formula  
  > "we are presented with the opportunity to constrain the conversion factor between CO luminosity and molecular gas mass, $\alpha_{\rm{CO}}$, through multiple means." (5.2 The CO-H2 Conversion Factor)
   - software: MAGPHYS
   - assumption: kappa_870=0.077, delta_GDR=72, solar metallicity, gamma=1, 25% dark matter, CO(2-1) thermalized  
  > "we adopt the average $\delta_{\rm{GDR}}$ determined by (cite: sandstrom13) in a large sample of local star-forming galaxies with approximately solar metallicities, $\ensuremath{\delta_{\rm{GDR}}}= 72$" (5.2.1 Gas-to-Dust Ratio)
   - fitting: _not stated_
   - validation: Agreement among three methods  
  > "The three methods show reasonably good agreement with each other" (5.2.4 Summary of CO–H$_2$ Conversion Factor Measurements)

## Software

- **MAGPHYS** : dust SED fitting to derive dust masses  
  > "we adopt the dust models implemented in MAGPHYS (cite: dacunha08)" (5.2.1 Gas-to-Dust Ratio)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO SPT0346-52 (gas-to-dust) | 2.2 | 0.6 | Msun pc^-2 (K km/s)^-1 | 3 | yields a measurement of $\ensuremath{\alpha_{\rm{CO}}}= 2.2\pm0.6$ for SPT0346-52 |
| alpha_CO SPT0538-50 blue (gas-to-dust) | 1.7 | 0.4 | Msun pc^-2 (K km/s)^-1 | 3 | yielding $\ensuremath{\alpha_{\rm{CO}}}= 1.7\pm0.4$ |
| alpha_CO SPT0538-50 (dynamical) | 1.4 | 0.8 | Msun pc^-2 (K km/s)^-1 | 3 | this yields $\alpha_{\rm{CO}}$$= 1.4 \pm 0.8$ |
| alpha_CO SPT0346-52 (dynamical) | 0.9 | 0.5 | Msun pc^-2 (K km/s)^-1 | 3 | we adopt $\ensuremath{\alpha_{\rm{CO}}}= 0.9 \pm 0.5$ |
| alpha_CO SPT0346-52 (Sigma_CO) | 0.78 | 0.11 | Msun pc^-2 (K km/s)^-1 | 3 | we average the values of $\alpha_{\rm{CO}}$ determined for each modeled channel to find a value of $\ensuremath{\alpha_{\rm{CO}}}= 0.78\pm0.11$ |
| alpha_CO SPT0538-50 (Sigma_CO) | 1.4 | 0.2 | Msun pc^-2 (K km/s)^-1 | 3 | yielding $\ensuremath{\alpha_{\rm{CO}}}= 1.4 \pm 0.2$ |
| SPT0538-50 CO(3-2)/CO(1-0) brightness temperature ratio | ~0.6 | not stated | dimensionless | 2 | implies a CO brightness temperature ratio of $r_{31} \sim 0.6$ |
| SPT0346-52 dust mass | 2.1e9 | 0.3e9 | Msun | 3 | This yields dust masses of $2.1\pm0.3 \times 10^9$ $\rm{M}_\odot$ for SPT0346-52 |

## Qualitative findings

- Low-J CO has larger half-light radius than 870 um dust in both sources; differential magnification up to ~50%  
  > "finding that the cold molecular gas as traced by low-$J$ CO always has a larger half-light radius than the 870 $\mu\rm{m}$ dust continuum emission." (abstract)

## Claim tuples

- H: Cold gas is more extended than dust | E: Lens model CO and ALMA continuum sizes | R: CO(1-0)/(2-1) radii exceed dust radii; CO(3-2) similar to dust | F: Star formation occurs in compact regions within larger gas reservoirs | **supported**
- H: SPT0538-50 is a merger | E: CO(3-2) lens modeling of two velocity components | R: Velocity components map to the two dust components | F: Merger confirmed | **supported**
- H: alpha_CO is low in these DSFGs | E: Three methods | R: Averages 1.3 and 1.5 | F: Consistent with rapidly star-forming systems | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic uncertainties in alpha_CO ~100% per method  
  > "The uncertainty in these estimates is dominated by systematic, rather than statistical, errors of $\sim$100% for each method." (5.2.4 Summary of CO–H$_2$ Conversion Factor Measurements)
- Caveat (inferred, ours): Single Gaussian source model is simplistic
- Caveat (inferred, ours): Few channels limit kinematic conclusions
- Caveat (inferred, ours): Solar metallicity assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Lens model code and MCMC settings
- Missing: Updated ALMA lens models (in prep.)
- Missing: Reduction details
- Data volume (inferred): ATCA and ALMA Cycle 0 visibilities, tens of GB
- Score (inferred): 3/5, Data identified but lens-modeling code and settings are not given.
- Rediscovery candidate: no, Custom lens modeling code and key inputs are not available.

## Links

- Method: (cite: hezaveh13) (Lens modeling procedure and ALMA data)
- Companion: (cite: aravena13) (Earlier ATCA compact-array CO observations)
- Related: South Pole Telescope DSFG sample

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 27,
  "rate": 0.409
 },
 "evidence_ok": true
}
```
