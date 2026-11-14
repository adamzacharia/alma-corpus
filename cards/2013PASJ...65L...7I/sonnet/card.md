# Active Galactic Nucleus and Extended Starbursts in a Midstage Merger VV 114

`2013PASJ...65L...7I` | Publications of the Astronomical Society of Japan 2013 | first author: Iono, Daisuke | arXiv: 1305.4535 | DOI: 10.1093/pasj/65.3.L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: Where is the dense gas (HCN/HCO+ 4-3) distributed in the mid-stage merger VV114, and does it reveal an AGN and star formation activity?  
  > "with the primary goal to study the distribution of dense gas during the critical stage when the two gas rich galaxies collide and merge." (Introduction)
- Target **VV114**: coordinates _not stated_; z/distance D = 86 Mpc  
  > "located at D = 86 Mpc ($1\ensuremath{''} = 0.4$ kpc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00467.S
- bands: Band 7 (HCN/HCO+ 4-3 near 355 GHz)  
  > "The HCN (4–3) ($\nu_{rest} = 354.505$ GHz) and HCO$^+$(4–3) ($\nu_{rest} = 356.734$ GHz)" (ALMA Observations)
- frequencies and spectral setup: 0.488 MHz resolution for the line spectral window  
  > "The digital correlator was configured with 0.488 MHz resolution for the spectral window that contains the emission lines." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 extended configuration  
  > "during the Cycle 0 program of ALMA using the extended configuration" (ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.5" x 0.4" (PA 52 deg)  
  > "a synthesized beam size of $0.5\ensuremath{''} \times 0.4\ensuremath{''}$ (PA = 52 degrees)" (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 86 minutes  
  > "The total on source time was 86 minutes." (ALMA Observations)
- observing dates: June 1–3, 2012  
  > "obtained on June 1 – 3, 2012" (ALMA Observations)
- pi or archival as stated: _not stated_
- Line: HCN 4-3 (354.505 GHz)
- Line: HCO+ 4-3 (356.734 GHz)
- Other facility **VLA archive**: 8.5 GHz radio continuum image  
  > "using the the archival 8.5 GHz radio continuum image obtained from the VLA archive" (Dense Gas and AGN /Starburst Activity)
- Other facility **Nobeyama Millimeter Array**: HCN and HCO+ (1-0) maps  
  > "J=1–0 (taken at the Nobeyama Millimeter Array; (cite: imanishi07))" (Distribution of HCN (4–3) and HCO$^+$(4–3))
- External data: HCN (1-0) = 7 Jy km/s  
  > "HCN (1–0) = 7 Jy km s$^{-1}$ (cite: imanishi07)" (Dense Gas and AGN /Starburst Activity) [from (cite: imanishi07)]
- External data: Pa-alpha star formation map  
  > "We compare the distribution of the HCO$^+$(4–3) and star formation activity traced in Pa$\alpha$ line in Figure 4." (Extended Dense Gas Filament) [from not stated]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: delivered calibrated data product used  
  > "We used the delivered calibrated data product and CLEANed the image down to 1.5 sigma" (ALMA Observations)
- flux calibrator: Uranus (flux), J1924-292 (bandpass), J0132-169 (gain)  
  > "Absolute flux calibration was performed using Uranus, J1924-292 was used for bandpass calibration" (ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust=0.5  
  > "The rms noise level was 0.9 mJy beam$^{-1}$ for the robust=0.5 maps." (ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: using all line-free channels  
  > "The continuum was subtracted using all of the line-free channels in the bandpass." (ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 30 km/s channels; convolved to NMA beam 7.5"x5.5" for comparison  
  > "Channel maps with 30 km s$^{-1}$ velocity resolution were made" (ALMA Observations)
- final beam: _not stated_
- final rms: 0.9 mJy/beam  
  > "The rms noise level was 0.9 mJy beam$^{-1}$" (ALMA Observations)

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges
- Cell and image size
- Clean mask and deconvolver
- CASA version
- Flux scale uncertainty
- Integration velocity range and clump identification method
- RADEX input details such as linewidth and column density
- Pa-alpha data source

## Analysis recipe

1. **Image line cubes**: CLEAN to 1.5 sigma on delivered calibrated data, 30 km/s channels, continuum subtracted  
  > "CLEANed the image down to 1.5 sigma using the ALMA data reduction package CASA." (ALMA Observations)
   - software: CASA
   - parameter: robust=0.5  
  > "for the robust=0.5 maps" (ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Dynamical mass limit for E0**: M_dyn = r sigma^2/G from line width and beam size, inclination 90 deg  
  > "We derive the upper limit to the dynamical mass by using $M_{\rm dyn} = r \sigma^2/G$ (assuming an inclination of 90 degrees for simplicity)" (Dense Gas and AGN /Starburst Activity)
   - fitting: Gaussian fits to E0 spectra  
  > "Gaussian fits to the HCO$^+$(4–3) and HCN (4–3) spectra at E0" (Dense Gas and AGN /Starburst Activity)
   - validation: _not stated_
3. **Dense gas mass of E0**: Gao & Solomon 2004 conversion factor with HCN(4-3)/(1-0)=0.63  
  > "we estimate the dense gas mass of the E0 component adopting the conversion factor provided in (cite: gao04)" (Dense Gas and AGN /Starburst Activity)
   - assumption: HCN emission optically thick  
  > "Since the HCN emission is generally believed to be optically thick" (Dense Gas and AGN /Starburst Activity)
   - fitting: _not stated_
   - validation: _not stated_
4. **Global gas conditions**: RADEX modeling of total HCO+ and HCN (4-3)/(1-0) ratios  
  > "comparing the total integrated HCO$^+$(4–3)/(1–0) and HCN(4–3)/(1–0) ratios to the results from radiative transfer modeling (RADEX; (cite: vandertak07))" (Extended Dense Gas Filament)
   - software: RADEX
   - assumption: [HCO+]/[H2]=1.0e-9; [HCN]/[HCO+]=0.1 to 1  
  > "assuming abundance ratios of \[HCO$^+$\]/\[H$_2$\] = $1.0 \times 10^{-9}$ (cite: irvine87) and \[HCN\]/\[HCO$^+$\] = 0.1 to 1" (Extended Dense Gas Filament)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "CLEANed the image down to 1.5 sigma using the ALMA data reduction package CASA." (ALMA Observations)
- **RADEX** : radiative transfer modeling of line ratios  
  > "radiative transfer modeling (RADEX; (cite: vandertak07))" (Extended Dense Gas Filament)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCO+(4-3) total integrated intensity | 15.3 | 0.4 | Jy km/s | 1 | $15.3 \pm 0.4$ Jy km s$^{-1}$ and $4.4 \pm 0.2$ Jy km s$^{-1}$ |
| HCN(4-3) total integrated intensity | 4.4 | 0.2 | Jy km/s | 1 | $15.3 \pm 0.4$ Jy km s$^{-1}$ and $4.4 \pm 0.2$ Jy km s$^{-1}$ |
| E0 HCN/HCO+ (4-3) flux ratio | 1.6 | not stated | dimensionless | 1 | HCN (4–3)/HCO$^+$(4–3) = 1.6 |
| E0 HCN dispersion | 123 | not stated | km/s | 2 | peak = 9.0 mJy, $\sigma = 123$ km s$^{-1}$ (for HCN (4–3)) |
| E0 dynamical mass upper limit | 4e8 | not stated | Msun | 2 | estimated from the line-width and the beam size is $\lesssim 4 \times 10^8$ M$_{\odot}$ |
| E0 dense gas mass | 8.1e6 | not stated | Msun | 3 | dense gas mass of $\sim 8.1 \times 10^6$ M$_{\odot}$ |
| HCN(4-3)/(1-0) ratio at E0 | 0.63 | not stated | dimensionless | 3 | we derive HCN(4–3)/(1–0) = 0.63 |
| Mean clump size E1-E5, W0-W3 | 230 | 70 | pc | 1 | is $230 \pm 70$ pc |
| 350 GHz/8.5 GHz flux ratio at E0 | 1.2 | 0.1 | dimensionless | 1 | The ratio is $1.2 \pm 0.1$ for E0 |
| RADEX gas density | 1e5 - 1e6 | not stated | cm^-3 | 4 | $n_{\rm H_2} = 10^5$ – $10^6$ cm$^{-3}$ and T = 30 – 500 K |

## Qualitative findings

- HCN(4-3) is seen only near the eastern nucleus, while HCO+(4-3) is extended with at least 10 peaks.  
  > "the HCO$^+$(4–3) emission is more extended and has at least 10 peaks in the integrated intensity map." (Distribution of HCN (4–3) and HCO$^+$(4–3))

## Claim tuples

- H: The eastern nucleus E0 hosts a buried AGN | E: Compare HCN and HCO+ (4-3) line strengths and widths at E0 | R: HCN/HCO+ = 1.6, HCN broader (FWHM 290 km/s), unresolved <200 pc | F: Dense gas around an obscured AGN is suggested, but the 350 GHz/8.5 GHz ratio argues against it | **partially**
- H: Dense gas traces the merger-triggered star formation | E: Compare HCO+(4-3) clumps with Pa-alpha | R: Clumps of ~230 pc and ~1e6 Msun, separated by ~600 pc, generally coincide with Pa-alpha peaks | F: A 3-4 kpc dense gas filament traces active star formation | **supported**
- H: Global gas is moderately dense | E: RADEX modeling of 4-3/1-0 ratios | R: n_H2 = 1e5-1e6 cm^-3, T = 30-500 K | F: Moderately dense gas on average | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Averages ignore differing spatial distribution of the 4-3 and 1-0 transitions; ALMA misses flux.  
  > "these are average quantities which are derived without considering the difference in the spatial distribution between the J=4–3 and 1–0 transitions" (Extended Dense Gas Filament)
- Caveat (inferred, ours): E0 AGN claim rests on a single line ratio and is contradicted by the radio ratio
- Caveat (inferred, ours): Ratios mix different beams and missing flux
- Caveat (inferred, ours): RADEX temperature unconstrained
- Caveat (inferred, ours): Short letter with little methodological detail

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "ADS/JAO.ALMA#2011.0.00467.S" (Summary and Future Prospects)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Clump definition and integration limits
- Missing: RADEX setup
- Missing: Pa-alpha and NMA data
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public Cycle 0 data and simple analysis, but imaging and modeling details are sparse.
- Rediscovery candidate: yes, Data are in the archive, and the main results are numeric integrated fluxes and line widths. Imaging is simple, though some settings are missing.

## Links

- Method: (cite: gao04) (HCN dense gas mass conversion)
- Method: (cite: vandertak07) (RADEX)
- Companion: Saito et al. in prep (CO and chemical analysis of VV114)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
