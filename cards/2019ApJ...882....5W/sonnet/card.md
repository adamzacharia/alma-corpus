# The Kennicutt-Schmidt Law and Gas Scale Height in Luminous and Ultraluminous Infrared Galaxies

`2019ApJ...882....5W` | The Astrophysical Journal 2019 | first author: Wilson, Christine D. | arXiv: 1907.05432 | DOI: 10.3847/1538-4357/ab31f3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the resolved Kennicutt-Schmidt slope at high gas surface density in U/LIRGs, and what do velocity dispersion and surface density imply for the gas scale height, free-fall time and star formation efficiency?  
  > "The purpose of this paper is to examine more closely the KS relation in the starburst regime and to estimate the disk thickness from the observed molecular gas velocity dispersion and surface density." (Introduction)
- Target **IRAS 17208-0014**: coordinates _not stated_; z/distance 182 Mpc  
  > "| IRAS 17208-0014 | 182 | 1.3 | 0.5 | 0.05 | 0.18 | 397 |" (Table 1); distance from _not stated_
- Target **Arp 220**: coordinates _not stated_; z/distance 79 Mpc  
  > "| Arp 220 | 79 | 1.1 | 0.95$\times$0.60 | 0.10 | 0.18 | 345 |" (Table 1); distance from _not stated_
- Target **IRAS 13120-5453**: coordinates _not stated_; z/distance 134 Mpc  
  > "| IRAS 13120-5453 | 134 | 3.4 | 1.1 | 0.08 | 0.14 | 650 |" (Table 1); distance from _not stated_
- Target **NGC 3256**: coordinates _not stated_; z/distance 44 Mpc  
  > "| NGC 3256 | 44 | 5.2 | 2.2 | 0.05 | 0.12 | 512 |" (Table 1); distance from _not stated_
- Target **NGC 7469**: coordinates _not stated_; z/distance 66 Mpc  
  > "| NGC 7469 | 66 | 1.6 | 0.95 | 0.015 | 0.043 | 418 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00525.S, 2012.1.00165.S, 2013.1.00218.S, 2013.1.00379.S, 2015.1.00167.S, 2015.1.00287.S, 2015.1.00993.S, 2016.1.00140.S
- bands: _not stated_
- frequencies and spectral setup: CO J=1-0 line plus 93-106 GHz continuum  
  > "thermal emission from dust can also contribute to the 93-106 GHz emission" (The K-S relation at high surface densities)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam FWHM 0.5" to 2.2" (Table 1)  
  > "| NGC 3256 | 44 | 5.2 | 2.2 | 0.05 | 0.12 | 512 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: sigma_cont 0.015-0.10 mJy/beam; sigma_CO 0.043-0.18 mJy/beam km/s  
  > "| NGC 7469 | 66 | 1.6 | 0.95 | 0.015 | 0.043 | 418 |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- External data: CO-to-H2 conversion factor for U/LIRGs  
  > "We adopt the U/LIRG value for the CO-to-H$_2$ conversion factor (cite: downes1998)" (3.1) [from (cite: downes1998)]
- External data: Thermal-only radio SFR calibration  
  > "We therefore calculate the star formation rate surface density, $\Sigma_{\rm SFR}$, using the thermal-only formula from (cite: murphy2011)." (3.1) [from (cite: murphy2011)]
- External data: Arp 220 western nucleus dust contribution of 40%  
  > "the western nucleus of Arp 220, where the dust contributes 40% of the flux (cite: sakamoto2017)" (3.1) [from (cite: sakamoto2017)]

## Processing

### Calibration

- pipeline or manual: Archive calibration scripts with original CASA version  
  > "the raw uv-data were calibrated using the scripts retrieved from the archive and the CASA version used in the original calibration" (Observations and data processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% absolute calibration  
  > "included both the 5% absolute calibration uncertainty and the statistical measurement uncertainty" (Observations and data processing)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5; channel width 20 km/s (26.4 NGC 3256, 40 Arp 220)  
  > "Cleaned image cubes were made using Briggs weighting with robust=0.5 and channel widths of 20 km s$^{-1}$" (Observations and data processing)
- uv taper: common minimum uv cutoff and taper to match beams for three galaxies  
  > "a common minimum uv-distance cutoff was used for both datasets and a taper was applied to roughly match the resulting beams" (Observations and data processing)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, using line-free channels  
  > "Continuum subtraction was performed on the uv-data using line-free channels." (Observations and data processing)
- line free channels: _not stated_
- primary beam correction: applied to CO moment 0 and continuum  
  > "The primary beam correction was applied to the CO integrated intensity and continuum images." (Observations and data processing)
- array combination: _not stated_
- smoothing: continuum and cube smoothed to identical resolution  
  > "the continuum image and line cube were smoothed to have identical resolution" (Observations and data processing)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed image processing  
  > "More details of the image processing are given in (cite: wilson2019)." (Observations and data processing) [from (cite: wilson2019)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges per galaxy
- Clean threshold, mask, cell and image sizes
- Taper values and uv cutoff
- Which project code maps to which galaxy
- Spectral setup details
- Dust-correction inputs for each galaxy
- Radio-SFR formula frequency and temperature details per pixel
- Exact velocity range for moment maps

## Analysis recipe

1. **Make cubes and continuum images**: Clean cubes (Briggs robust 0.5), uv continuum subtraction, matched-resolution continuum, smoothing  
  > "Cleaned image cubes were made using Briggs weighting with robust=0.5" (Observations and data processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and rebinning**: Moment 0 and 2 with 3 and 4 sigma cutoffs, rebin to beam size, keep S/N>4 pixels  
  > "Only binned pixels with a signal-to-noise greater than 4 in all three images are included in our analysis below." (Observations and data processing)
   - software: CASA
   - fitting: _not stated_
   - validation: Beam smearing tested on IRAS 13120; sigma_v overestimated by at most 20%  
  > "we estimate that the velocity dispersion in a typical pixel is overestimated by at most 20%" (Observations and data processing)
3. **Sigma_mol and Sigma_SFR**: CO to Sigma_mol with Downes & Solomon factor and helium; dust-corrected 93-106 GHz continuum to thermal-only SFR  
  > "$\Sigma_{\rm mol} = 1.36 \Sigma_{\rm H_2} = 1.088 I_{\rm CO(1-0)}$" (3.1)
   - assumption: Constant X_CO; no inclination correction; NGC 7469 nucleus excluded  
  > "We make no correction for the (poorly constrained) inclination of these disturbed systems" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit KS relation**: Double power law with free break, bootstrapped 10000 times  
  > "We fit the relation with a double power law using the Astropy Modeling package with the break point location as a free parameter, and bootstrapped 10000 times" (3.1)
   - software: astropy
   - fitting: Bootstrap, 10000 resamples  
  > "bootstrapped 10000 times to get the fit parameters and uncertainties" (3.1)
   - validation: Single power law fit gives nearly identical slope  
  > "A single power law fit to all of the data yields a nearly identical slope" (3.1)
5. **Scale height and timescales**: H = 0.5 sigma_v^2/(pi G Sigma_mol); rho_mid = Sigma/(2H); t_ff, t_dep, eps_ff per pixel  
  > "H \simeq 0.5 {{\sigma_v^2}\over {\pi G \Sigma_{\rm mol}}}" (3.2)
   - assumption: alpha+beta~0.3, Sigma_gas/Sigma_total~0.5, g_galaxy/g~0.05-0.2  
  > "we follow the suggestion in (cite: kim15) that $\beta+\alpha\sim0.3$" (3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.0 to 5.4 (original CASA versions for calibration): Calibration, imaging, moment maps  
  > "All further processing was carried out in CASA versions 5.0 to 5.4." (Observations and data processing)
- **astropy** : Double power law fitting (Astropy Modeling)  
  > "using the Astropy Modeling package" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| High-density KS slope | 1.74 | +0.09/-0.07 | dimensionless | 4 | We find a slope of $1.74^{+0.09}_{\rm -0.07}$ in the high surface density regime |
| Single power law KS slope | 1.73 | +0.08/-0.07 | dimensionless | 4 | ($1.73^{+0.08}_{\rm -0.07}$) |
| Mean H range | 150 +/- 15 pc (NGC 7469) to 190 +/- 20 pc (NGC 3256) | 15-20 pc | pc | 5 | The mean values range from $150 \pm 15$ pc in NGC 7469 to $190 \pm 20$ pc in NGC 3256. |
| Mean eps_ff | 5-7% | not stated | dimensionless | 5 | roughly constant with mean values of 5-7% in each of the 5 galaxies |
| Velocity dispersion range | 30-160 | not stated | km/s | 2 | The velocity dispersions range from 30 km s$^{-1}$ to 160 km s$^{-1}$ |

## Qualitative findings

- Observed constant H and sigma_v rising ~Sigma^0.5 conflict with feedback models predicting constant sigma_v.  
  > "are in tension with some feedback-driven models, which predict $\sigma_v$ to be more constant and $H$ to be more variable" (abstract)

## Claim tuples

- H: The KS relation in U/LIRGs is super-linear | E: Resolved fit of Sigma_SFR vs Sigma_mol in 5 galaxies | R: Slope 1.74 above 10^3 Msun/pc^2 | F: Steeper than linear | **supported**
- H: Gas scale height is roughly constant | E: H from sigma_v and Sigma_mol | R: H 150-190 pc over 1.5 dex | F: Midplane density scales linearly with Sigma, explaining the super-linear slope | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Variable X_CO (Narayanan 2012) would steepen the KS slope to 2.6, but constant X_CO adopted for comparison  
  > "Taking $y=1.74$ and $x=0.32$, the revised slope would be $2.6$." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): sigma_v overestimated by up to 20% from beam smearing and up to 12% from channelization  
  > "we estimate the effect is at most 12% for the narrowest lines in our data" (Observations and data processing)
- Caveat (inferred, ours): Constant X_CO strongly affects slopes
- Caveat (inferred, ours): Radio SFR calibration uncertain with dust absorption and AGN
- Caveat (inferred, ours): H formula assumptions are approximate
- Caveat (inferred, ours): Only 5 galaxies

## Reproducibility

- Data public (paper): Archival ALMA data; binned table provided  
  > "we searched the ALMA archive for U/LIRGs" (Observations and data processing)
- Products in archive: _not stated_
- Missing: Details deferred to Wilson et al. 2019 in prep
- Missing: Line-free channels and clean parameters
- Data volume (inferred): tens to hundreds of GB for raw data of 8 projects
- Score (inferred): 3/5, Public data and clear formulas, but imaging details are deferred to an unpublished paper.
- Rediscovery candidate: yes, Public archival data, explicit equations, numeric results.

## Links

- Method: (cite: wilson2019) (Detailed image processing)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 36,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
