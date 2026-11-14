# Mapping Metallicity Variations across Nearby Galaxy Disks

`2019ApJ...887...80K` | The Astrophysical Journal 2019 | first author: Kreckel, K. | arXiv: 1910.07190 | DOI: 10.3847/1538-4357/ab5115

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: How does gas-phase metallicity vary within galaxy disks (after removing radial gradients), and how do HII-region metallicity offsets relate to local ISM conditions and spiral structure?  
  > "After removing the first order radial gradients present in each galaxy, we look at the statistics of the metallicity offset ($\Delta$O/H) and explore azimuthal variations." (abstract)
- Target **NGC 628, NGC 1087, NGC 1672, NGC 2835, NGC 3627, NGC 4254, NGC 4535, IC 5332**: coordinates _not stated_; z/distance 9.77-16.8 Mpc (Table 1)  
  > "| NGC 0628 | $9.77\pm0.82$ | Sc | 10.2 | 0.26 | 20.9 | 8.7 | 5.0 | 1.0 | 47 | 1277 | 96 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA main array (compact configuration), 7-m array and total power  
  > "we observed each target with ALMA’s main array in a compact configuration and with the 7-m arrray and single dish (“total power”) telescope." (2.3 Ancillary data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO cubes ≈1''-2''; ≈7'' for 7-m data  
  > "The combination of these observations yield CO line data cubes with resolution $\approx 1''{-}2''$ and sensitivity to emission on all spatial scales." (2.3 Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey (PI E. Schinnerer)  
  > "the CO (2-1) line from the PHANGS-ALMA survey (PI E. Schinnerer)" (2.3 Ancillary data)
- Line: CO 2-1 (not stated)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: Optical IFU cubes used for HII region spectra, line fluxes and metallicities  
  > "We use the MUSE spectrograph (cite: Bacon2010) at the VLT to mosaic the central star-forming disks of eight nearby spiral galaxies" (2.1 Observations)
- Other facility **GALEX**: FUV images for Halpha-to-FUV ratios  
  > "FUV emission was observed by the Galaxy Evolution Explorer (GALEX) satellite, with all maps taken from the GALEX archive" (2.3 Ancillary data)
- External data: Galaxy parameters (distance, mass, SFR, PA, inclination)  
  > "The galaxy parameters are adopted from the z0mgs (z=0 multiwavelength galaxy survey; Leroy, Sandstrom et al. ApJS accepted) database" (Table 1) [from z0mgs, Leroy, Sandstrom et al.]
- External data: Typical GMC mass in NGC 628 (5.8e5 Msun)  
  > "the typical GMC mass in NGC 628; (cite: Kreckel2018)" (5.1 Localized enrichment within galaxy disks) [from (cite: Kreckel2018)]

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
- smoothing: CO moment maps at 1'' for local measurements; low-resolution 7-m moment 0 maps (~7'', ~500 pc) for large-scale CO  
  > "When computing the general distribution of molecular gas, we use a low resolution, high completeness version of the moment 0 maps created at this lower resolution of the 7-m data." (2.3 Ancillary data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PHANGS-ALMA sample selection, observations and data reduction  
  > "The sample selection, observations, and data reduction for PHANGS-ALMA are described in A. K. Leroy et al. (in preparation)." (2.3 Ancillary data) [from A. K. Leroy et al. (in preparation)]
- CO maps for six targets published earlier  
  > "Maps for six of our eight targets have appeared before (cite: Sun2018; Kreckel2018; Utomo2018)" (2.3 Ancillary data) [from (cite: Sun2018; Kreckel2018; Utomo2018)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters for PHANGS-ALMA cubes
- Exact CO moment-map masking and noise thresholds
- Which ALMA project maps to which galaxy
- Conversion of CO intensity to surface density, if any
- HIIphot parameters per galaxy

## Analysis recipe

1. **Build HII region catalog**: Halpha maps from LZIFU, HIIphot masks, integrated spectra fit with GANDALF/pPXF, then quality/BPT cuts  
  > "H$\alpha$ emission line maps are analyzed with HIIphot (cite: Thilker2000), which has been designed to morphologically isolate HII regions from diffuse ionized gas" (HII region catalogs)
   - software: LZIFU, HIIphot, GANDALF, pPXF
   - parameter: S/N>5 for strong lines  
  > "A S/N $>$5 is required for all strong emission lines used to infer the metallicity" (2.2 HII region catalogs)
   - fitting: _not stated_
   - validation: Repeat with 1'' circular apertures; agreement within 0.01 dex for 84%  
  > "agree with those calculated from the HII region catalogs within 0.01 dex for 84% of the sample" (2.2 HII region catalogs)
2. **Derive metallicity and radial gradients**: Pilyugin & Grebel 2016 S-calibration; linear fit to radial gradient excluding inner 0.1 R25; residuals DeltaO/H  
  > "We exclude the inner 0.1R$_{25}$ when performing our fit" (3.2 Radial metallicity gradients)
   - fitting: first order linear fit including flux errors  
  > "We perform a first order linear fit to the radial gradient" (3.2 Radial metallicity gradients)
   - validation: Compared with N2S2 (D16) prescription and IZI  
  > "The reported trends and corrleations also do not change qualitatively when using the Bayesian inference code IZI" (3.1 Strong line metallicities)
3. **Compare DeltaO/H outliers with local conditions including CO**: Split into typical/enhanced/reduced (1 sigma); KS tests and Spearman correlations of six parameters including CO integrated intensity and line width at 1''  
  > "We split the sample of HII regions into those with (a) typical metallicities (-1$\sigma$ $<$ $\Delta$O/H$<$ 1$\sigma$)" (4.2 Physical conditions of regions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **LZIFU** : Fit stellar templates and emission lines to produce maps  
  > "All data cubes are processed using the IDL toolkit LZIFU (cite: Ho2016)" (2.1 Observations)
- **HIIphot** : Identify HII regions  
  > "H$\alpha$ emission line maps are analyzed with HIIphot (cite: Thilker2000)" (HII region catalogs)
- **GANDALF** : Fit emission lines and stellar continuum  
  > "These integrated region spectra are then fit with GANDALF" (2.2 HII region catalogs)
- **pPXF** : Stellar continuum fitting  
  > "stellar continuum (using pPXF - Penalized Pixel-Fitting" (2.2 HII region catalogs)
- **IZI** : Bayesian metallicity/ionization parameter check  
  > "the Bayesian inference code IZI (cite: Blanc2015)" (3.1 Strong line metallicities)
- **Topcat** : Data analysis  
  > "Data analysis made use of Topcat (cite: Taylor2005)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of HII regions | 7138 | not stated | regions | 1 | identifing a total of 7138 HII regions |
| Scatter about radial gradient | 0.03-0.05 | not stated | dex | 2 | All galaxies show small (0.03-0.05 dex) systematic scatter after accounting for the radial trends. |
| Spearman rho DeltaO/H vs [SIII]/[SII] | 0.63 | not stated | dimensionless | 3 | We observe a stronger correlation ($\rho$=0.63) for the sample as a whole |
| Spearman rho DeltaO/H vs Halpha luminosity | 0.34 | not stated | dimensionless | 3 | with a Spearman’s rank correlation coefficient ($\rho$) of 0.34 and high statistical significance (p$<$0.001) |

## Qualitative findings

- Enhanced-abundance regions sit at higher CO integrated intensity  
  > "HII regions with enhanced abundances are at locations where we measure higher CO integrated intensity" (4.2 Physical conditions of regions)

## Claim tuples

- H: Metallicity offsets correlate with local ISM conditions | E: Compare DeltaO/H outliers with ionization parameter, Halpha/FUV, CO, E(B-V), velocity dispersion | R: Enhanced regions have high ionization parameter, younger clusters, higher CO; reduced regions have higher Halpha dispersion | F: Recent star formation locally enriches ISM; mixing dilutes | **supported**
- H: Spiral arms organise metallicity variations | E: Azimuthal maps of DeltaO/H | R: Subtle variations in half the sample | F: Not always cleanly tied to spiral pattern | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Results depend on metallicity prescription  
  > "the trends we report are heavily dependent on the choice of metallicity prescription used" (5.4 Physical interpretation of line ratios)
- Caveat (inferred, ours): CO-ionized gas offsets limit physical link
- Caveat (inferred, ours): DIG not corrected in main analysis

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: PHANGS-ALMA data reduction details (Leroy et al. in prep)
- Missing: HIIphot settings
- Missing: Full HII region table online only
- Data volume (inferred): ~tens of GB for MUSE cubes plus CO products
- Score (inferred): 3/5, ALMA is ancillary; main data is MUSE; recipe partly specified.
- Rediscovery candidate: no, ALMA role minor and processing deferred to unpublished paper.

## Links

- Method: Pilyugin & Grebel 2016 (S-calibration metallicity prescription)
- Companion: Kreckel et al. 2018 (NGC 628 CO and MUSE)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 27,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
