# Magnetic fields at the onset of high-mass star formation

`2018A&A...614A..64B` | Astronomy and Astrophysics 2018 | first author: Beuther, H. | arXiv: 1802.00005 | DOI: 10.1051/0004-6361/201732378

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the magnetic field properties (morphology, strength, stability) at the earliest evolutionary stage of high-mass star formation in the starless region IRDC 18310-4?  
  > "We want to understand the magnetic field properties at the earliest evolutionary stages of high-mass star formation." (abstract)
- Target **IRDC 18310-4**: coordinates field 1: 18:33:39.4 -08:21:10.2; field 2: 18:33:39.4 -08:21:16.0 (J2000)  
  > "we selected the infrared dark cloud IRDC18310-4 located at an approximate distance of 4.9 kpc (cite: sridharan2005)" (Introduction); "for field 1 R.A. (J2000.0) 18:33:39.4, Dec. (J2000.0) -08:21:10.2" (Observations); z/distance 4.9 kpc  
  > "we selected the infrared dark cloud IRDC18310-4 located at an approximate distance of 4.9 kpc (cite: sridharan2005)" (Introduction); "for field 1 R.A. (J2000.0) 18:33:39.4, Dec. (J2000.0) -08:21:10.2" (Observations); distance from Sridharan et al. 2005  
  > "we selected the infrared dark cloud IRDC18310-4 located at an approximate distance of 4.9 kpc (cite: sridharan2005)" (Introduction); "for field 1 R.A. (J2000.0) 18:33:39.4, Dec. (J2000.0) -08:21:10.2" (Observations)

## Data provenance

- ALMA projects: 2015.1.00492.S
- bands: 1 mm band (1.3 mm), full polarization  
  > "The observations were conducted in the 1 mm band" (Observations)
- frequencies and spectral setup: LO 233 GHz; four 2 GHz basebands centered at 224, 226, 240, 242 GHz; channel width 31.25 MHz  
  > "The four basebands with 2 GHz bandwidth each were centered at 224, 226, 240 and 242 GHz. The channel width was 31.25 MHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-2, C36-3  
  > "Two slightly different array configurations were used (C36-2, C36-3)" (Observations)
- baselines: 15 to 704 m  
  > "with a total baseline range between 15 and 704 m" (Observations)
- angular resolution: 1.01'' x 0.83'' (PA 89 deg)  
  > "The synthesized beam of these images is $1.01''\times 0.83''$ (PA 89$^o$)." (Observations)
- max recoverable scale: ~11'' at 230 GHz (ALMA reported)  
  > "ALMA reports for the given configurations maximum recoverable scales of $\sim$11$''$ at 230 GHz" (Observations)
- sensitivity: 1sigma rms 0.15 mJy/beam (Stokes I), 6 uJy/beam (linear polarization)  
  > "The $1\sigma$ rms values of the Stokes I and the linear polarized image are 0.15 mJy beam$^{-1}$ and 6 $\mu$Jy beam$^{-1}$, respectively." (Observations)
- time on source: ~17.6 min per field per execution; eight executions  
  > "the on-source integration time for each observed field was $\sim$17.6 min per execution" (Observations)
- observing dates: June 17-20, 2016, four sessions  
  > "during four sessions between June 17 and June 20, 2016" (Observations)
- pi or archival as stated: _not stated_
- Other facility **IRAM 30m MAMBO**: 1.2 mm single-dish flux densities for missing-flux comparison  
  > "the single-dish 1.2 mm bolometer flux density measured with the MAMBO camera at the IRAM 30 m telescope (cite: beuther2002a)" (Results)
- Other facility **Plateau de Bure Interferometer**: previous 3 mm and 1 mm data, N2H+ line width, fragmentation  
  > "The region was studied with the Plateau de Bure Interferometer in the 3 mm and 1 mm band" (Introduction)
- External data: N2H+ line width ~0.3 km/s used for sigma_v  
  > "The one-dimensional velocity dispersion $\sigma_{v}$ is estimated from the width of the N$_2$H$^+$ line measured in this region (cite: beuther2015a)." (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method) [from (cite: beuther2015a)]
- External data: Average density n=10^6 cm^-3 and clump line width 1.5 km/s, single-dish column density 1.3e23 cm^-2  
  > "We estimate $\rho$ assuming an average number density $n=10^6$ cm$^{-3}$ (cite: beuther2013a)" (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method) [from (cite: beuther2013a)]
- External data: MAMBO 1.2 mm flux densities (132 mJy in 11'', ~410 mJy in primary beam)  
  > "within the inner $11''$ beam size is 132 mJy" (Results) [from (cite: beuther2002a)]

## Processing

### Calibration

- pipeline or manual: followed ALMA observatory provided procedures  
  > "For the calibration we followed the provided procedures from the ALMA observatory." (Observations)
- casa version: CASA 4.7  
  > "Calibration and imaging of the data was done in CASA version 4.7." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 or Titan (bandpass J1751+0939, gain J1912-0804, polarization J1743-0350)  
  > "the absolute flux was calibrated with J1733-1304 or Titan." (Observations)
- flux scale uncertainty: ~10%  
  > "The absolute flux uncertainty should be around 10%." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we imaged both datasets together in a mosaic mode with natural weighting and a small uv-taper on the longer baselines" (Observations)
- uv taper: small uv-taper on longer baselines (value not given)  
  > "a small uv-taper on the longer baselines to increase our signal-to-noise ratio" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two fields combined in a mosaic; all four spectral windows used  
  > "All four spectral windows were used for the imaging process." (Observations)
- smoothing: _not stated_
- final beam: 1.01'' x 0.83'' PA 89 deg  
  > "The synthesized beam of these images is $1.01''\times 0.83''$ (PA 89$^o$)." (Observations)
- final rms: 0.15 mJy/beam (I), 6 uJy/beam (linear pol)  
  > "The $1\sigma$ rms values of the Stokes I and the linear polarized image are 0.15 mJy beam$^{-1}$ and 6 $\mu$Jy beam$^{-1}$, respectively." (Observations)

### Inherited from earlier work

- Column density and mass calculation approach (optically thin dust)  
  > "following the approach already used in (cite: beuther2013a; beuther2015a) we can calculate the H$_2$ column densities" (Results) [from (cite: beuther2013a; beuther2015a)]
- DCF procedure  
  > "We calculate $B^{\rm{DCF}}_{\perp}$ using the procedure described in appendix D of (cite: planckXXXV)." (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method) [from (cite: planckXXXV)]
- Field-combination test using Q/U residuals  
  > "We conducted an additional test following the approach outlined in (cite: matthews2014)" (Observations) [from (cite: matthews2014)]
- Structure function analysis  
  > "Following (cite: hildebrand2009) and (cite: houde2009; houde2011), we can analyze the structure function" (4.2 Structure function) [from (cite: hildebrand2009; houde2009; houde2011)]
- Turbulent-to-magnetic energy ratio formula  
  > "Following (cite: girart2009) or (cite: beuther2010c), we can estimate the ratio of turbulent-to-magnetic energy as $\beta \sim 3(\sigma_{v}/\sigma_A)^2$." (4.3 Magnetic field implications) [from (cite: girart2009; beuther2010c)]

### Not stated but needed to reproduce (our reading)

- uv-taper value
- Pixel/image size and cell size
- Deconvolver, cleaning threshold and masks
- Polarization calibration details and debiasing of polarized intensity
- Pixel selection and SNR cuts for sigma_psi and structure function
- Source regions/apertures for each core
- Exact mean-field and error propagation for DCF
- Correction factor used in DCF (Planck procedure details)
- Which flux calibrator for which execution

## Analysis recipe

1. **Image Stokes I, Q, U and combine fields**: Mosaic of two fields, natural weighting with small uv-taper; consistency tested using Q/U residuals  
  > "we imaged both datasets together in a mosaic mode with natural weighting and a small uv-taper on the longer baselines" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared single-field and combined images and a residual mask at 3 sigma  
  > "showing again that the combination of the two fields is a valid approach" (Observations)
2. **Derive core masses and column densities**: Optically thin dust emission from 1.3 mm flux within 4 sigma contours  
  > "Assuming optically thin dust emission and following the approach already used in (cite: beuther2013a; beuther2015a) we can calculate the H$_2$ column densities" (Results)
   - assumption: T~15 K, gas-to-dust 150, kappa_1.3mm~0.9 cm2/g (Ossenkopf & Henning thin ice mantles, 1e6 cm-3)  
  > "With gas temperatures in this starless core around $\sim$15 K, a gas-to-dust mass ratio of 150 (cite: draine2011)" (Results)
   - fitting: _not stated_
   - validation: Accuracy estimated within a factor 2  
  > "we estimate the accuracy of the masses and column densities within a factor 2" (Results)
3. **Magnetic field strength via DCF**: B = sqrt(4 pi rho) sigma_v/sigma_psi with sigma_psi from Stokes Q and U  
  > "We estimate the values of the angular dispersion of the local magnetic field orientations directly from the Stokes $Q$ and $U$ by using" (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method)
   - parameter: n=1e6 cm-3, mu=2.8 m_p, sigma_v=0.13 km/s from N2H+ width 0.3 km/s  
  > "we get $\sigma_{v}\approx \Delta v(\rm{N_2H^+})/\sqrt{8\rm{ln}2}\approx 0.3\rm{km/s}/\sqrt{8\rm{ln}2}\approx 0.13$ km s$^{-1}$" (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method)
   - assumption: Same sigma_v and n for all sub-regions; frozen-in field, Alfven waves  
  > "we use the same value of $\sigma_{v}$ and $n$ for all three sub-regions" (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method)
   - fitting: _not stated_
   - validation: Considered order-of-magnitude estimates; formal errors from 4 sigma rms  
  > "should be considered as order-of-magnitude estimates" (4.1 Magnetic field strength via Davis-Chandrasekhar-Fermi method)
4. **Structure function analysis of polarization angles**: Fit square of S2(l) with b(l)+a2' l^2 for l>0.5'' and take intercept b(0) as angle dispersion  
  > "fitting the square of the structure function of polarization angles, $S_{2}(\ell)$, with a second-order polynomial, $S^{2}_{2}(\ell)=b(\ell)+a'_{2}\ell^{2}$" (4.2 Structure function)
   - parameter: fit for l>0.5''  
  > "in this case we chose to fit for $\ell>0.5''$" (4.2 Structure function)
   - fitting: second-order polynomial fit  
  > "fitting the square of the structure function of polarization angles, $S_{2}(\ell)$, with a second-order polynomial, $S^{2}_{2}(\ell)=b(\ell)+a'_{2}\ell^{2}$" (Structure function of the polarization orientation angles)
   - validation: Compared b(0) with sigma_psi from direct dispersion  
  > "lead to a value of $b(0)$ that is very close to the values of $\sigma_{\psi}$ estimated using Eq." (4.2 Structure function)
5. **Energy ratio and mass-to-flux ratio**: Alfven velocity, beta~3(sigma_v/sigma_A)^2, M/Phi=7.6e-24 N_H2/B in critical units  
  > "the mass-to-flux ratio $M/\Phi_B\approx 7.6\times 10^{-24}\frac{N_{\rm{H_2}}}{B}$" (4.3 Magnetic field implications)
   - assumption: Alfven velocity in plane of sky equals that along line of sight  
  > "we assume that the one-dimensional Alfven velocity in the plane of the sky is the same as that along the line of sight" (4.3 Magnetic field implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: Calibration and imaging  
  > "Calibration and imaging of the data was done in CASA version 4.7." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam | 1.01 x 0.83 (PA 89) | not stated | arcsec, deg | 1 | The synthesized beam of these images is $1.01''\times 0.83''$ (PA 89$^o$). |
| Core masses mm1-mm4 | 22.4, 9.6, 16.7, 4.5 | factor 2 | Msun | 2 | / mm1 / 4.9 / 19.4 / 5.7 / 22.4 / |
| B_DCF mm1, mm2, mm3 | 0.3, 0.6, 1.3 | 0.1, 0.2, 0.4 | mG | 3 | / mm2    /      9.8      /      0.6$\pm$0.2       /   8.8   /     0.6$\pm$0.2      / |
| B_SF mm1, mm2, mm3 | 3.7, 0.6, 1.7 | 1.3, 0.2, 0.6 | mG | 4 | / mm1    /     23.1      /      0.3$\pm$0.1       /   1.6   /     3.7$\pm$1.3      / |
| Turbulent-to-magnetic energy ratio beta | 0.18 (clump), 0.008 (cores) | not stated | dimensionless | 5 | turbulent-to-magnetic energy ratio of $\beta \approx 0.18$ whereas the lower $\sigma_{v}$ for the individual cores would result in $\beta \approx 0.008$ |
| Mass-to-flux ratio | ~0.5 (large scale), ~3.1 (ALMA column density) | not stated | critical units | 5 | one gets $M/\Phi_B\sim 3.1$ |
| Fraction of flux recovered | 20-50% | not stated | percent | 0 | approximately 20-50% of the total flux are recovered by our interferometer observations |

## Qualitative findings

- Polarized emission detected in all four cores with smooth, ordered angles and no polarization holes; polarization fraction typically 1-10%.  
  > "we find values typically between 1 and 10%" (Results)

## Claim tuples

- H: Is the magnetic field strong in this starless high-mass clump? | E: DCF and structure function on ALMA 1.3 mm polarization | R: B ~0.6-3.7 mG | F: Comparably large magnetic fields | **supported**
- H: Does turbulence contribute to stability? | E: Compare sigma_v with Alfven velocity | R: beta 0.008-0.18 | F: Magnetic energy dominates over turbulence | **supported**
- H: Is the region collapsing? | E: Mass-to-flux ratio | R: ~0.5 to ~3.1 depending on column density | F: Critical on large scales, collapsing on small scales | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Simplified 'magnetic Jeans fragmentation' cannot explain the observed fragmentation alone  
  > "such a simplified “magnetic Jeans fragmentation” picture cannot explain the observed data alone" (4.3 Magnetic field implications)
- How they decided it was enough: _not stated_
- Limitation (authors): Large-scale flux filtered out; polarization fractions are upper limits; DCF only order-of-magnitude  
  > "The latter high values should be considered as upper limits" (Results)
- Caveat (inferred, ours): Single source; DCF assumptions (uniform density, single sigma_v) are weak
- Caveat (inferred, ours): Missing short spacings bias polarization fraction and sigma_psi
- Caveat (inferred, ours): Mass-to-flux ratio sensitive to chosen column density and projection (no inclination correction)

## Reproducibility

- Data public (paper): ALMA project 2015.1.00492.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00492.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, taper, cleaning)
- Missing: Pixel selection for DCF and structure function
- Missing: Polarization calibration/debiasing details
- Data volume (inferred): ~50-100 GB raw, four sessions of polarization data
- Score (inferred): 5/5, Data public and methods described, but imaging and pixel selection details missing.
- Rediscovery candidate: yes, Public data, analysis steps and tabulated numeric results exist, though some settings are unstated.

## Links

- Method: Planck Collaboration 2016 (cite: planckXXXV) (DCF procedure)
- Method: Hildebrand et al. 2009 (cite: hildebrand2009) (structure function method)
- Method: Matthews et al. 2014 (cite: matthews2014) (Q/U residual test for combining fields)
- Companion: Beuther et al. 2015 (cite: beuther2015a) (previous PdBI study of the same region)
- Companion: Beuther et al. 2013 (cite: beuther2013a) (earlier study of the region)
- Related: TADPOL

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 52,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
