# How to Fuel an AGN: Mapping Circumnuclear Gas in NGC 6240 with ALMA

`2019ApJ...885L..21M` | The Astrophysical Journal Letters 2019 | first author: Medling, Anne M. | arXiv: 1910.12967 | DOI: 10.3847/2041-8213/ab4db7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How much molecular gas lies within the resolution limit of the dynamical black hole mass measurements of the two NGC 6240 nuclei, and does it explain their overmassive black holes?  
  > "We test for the presence of such gas near the two black holes in NGC 6240 using long-baseline ALMA Band 6 observations" (abstract)
- Target **NGC 6240**: coordinates _not stated_; z/distance physical scale 490 pc/arcsec (H0=70, Om=0.28, OL=0.72)  
  > "The physical scale is thus 490 pc arcsec$^{-1}$" (Introduction); "separated by 735 pc" (Introduction); distance from Ned Wright's Cosmology Calculator (Wright06)  
  > "The physical scale is thus 490 pc arcsec$^{-1}$" (Introduction); "separated by 735 pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00370.S, 2015.1.00003.S
- bands: Band 6  
  > "We use long-baseline Band 6 imaging of CO(2-1) from ALMA" (2 Mapping CO(2-1) with ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: five array configurations  
  > "span five different array configurations with baselines ranging from 15.1 to 14,969 m" (2 Mapping CO(2-1) with ALMA)
- baselines: 15.1 to 14,969 m  
  > "span five different array configurations with baselines ranging from 15.1 to 14,969 m" (2 Mapping CO(2-1) with ALMA)
- angular resolution: 0.06'' x 0.03'' (30 pc x 15 pc)  
  > "The final spatial resolution of the dataset is 0.06$''$ $\times$ 0.03$''$ (30 pc $\times$ 15 pc)." (2 Mapping CO(2-1) with ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 44.5 minutes  
  > "for a total time on source of 44.5 minutes" (2 Mapping CO(2-1) with ALMA)
- observing dates: 2016 and 2017  
  > "These observations from 2016 and 2017 span five different array configurations" (2 Mapping CO(2-1) with ALMA)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **Keck OSIRIS (LGS AO)**: Original stellar-kinematic black hole mass measurements (Medling15_bh)  
  > "The original OSIRIS adaptive optics integral field spectroscopy used to measure the black hole masses by (cite: Medling15_bh)" (3.3 Interpreting the Central Gas Masses)
- Other facility **MERLIN/VLA**: Radio fluxes used to estimate synchrotron contribution  
  > "scaling the MERLIN 5 GHz central beam flux from (cite: Beswick01)" (3.2 Measuring the Central Gas Mass Profiles)
- External data: alpha_CO(2-1)=1.83±0.97 from alpha_CO(1-0)=2.3±1.2 and r21=1.26±0.14 in central 2'' box  
  > "We use the luminosities measured in their central box (2$''$ $\times$ 2$''$, which contains both black holes)" (3.2 Measuring the Central Gas Mass Profiles) [from (cite: cicone18)]
- External data: Continuum flux to H2 mass calibration (25 K, scaled to 100 K)  
  > "We use the calibrated relation between continuum flux density and H$_2$ mass of (cite: Scoville16)" (3.2 Measuring the Central Gas Mass Profiles) [from (cite: Scoville16)]
- External data: MERLIN 5 GHz central beam flux for synchrotron estimate  
  > "scaling the MERLIN 5 GHz central beam flux from (cite: Beswick01)" (3.2 Measuring the Central Gas Mass Profiles) [from (cite: Beswick01)]
- External data: Bolometric luminosities 2.6e44 and 8e44 erg/s (north, south)  
  > "found intrinsic bolometric luminosities of 2.6 $\times10^{44}$ erg s$^{-1}$ and 8 $\times10^{44}$ erg s$^{-1}$ for the north and south nuclei" (3.3 Accretion Rates) [from (cite: Puccetti16)]
- External data: Original dynamical black hole masses  
  > "placing the north black hole at $>$8.8$\times10^{8}$ M$_{\ensuremath{\odot}}$ and the south in the range (8.7-20) $\times10^{8}$ M$_{\ensuremath{\odot}}$" (Introduction) [from (cite: medling11; Medling15_bh)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline with WVR-based scaling and additional self-calibration  
  > "We reduced the data according to the standard ALMA data pipeline process[^2] with scaling according to measurements of ALMA’s water vapor radiometers (cite: Maud17) and additional self-calibration steps." (2 Mapping CO(2-1) with ALMA)
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
- final beam: 0.06'' x 0.03''  
  > "The final spatial resolution of the dataset is 0.06$''$ $\times$ 0.03$''$ (30 pc $\times$ 15 pc)." (2 Mapping CO(2-1) with ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Full data reduction details  
  > "Full details of the reduction can be found in Treister et al. (2019, submitted)." (2 Mapping CO(2-1) with ALMA) [from Treister et al. (2019, submitted)]
- Dust temperature 100 K assumption, following Arp 220 nuclei  
  > "we scale the relation linearly to a mass-weighted dust temperature of 100 K, following the assumption made in Arp 220’s nuclear regions on similar scales (cite: Scoville15)" (3.2 Measuring the Central Gas Mass Profiles) [from (cite: Scoville15)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell size, deconvolver, masks) for the high-resolution cube
- Continuum frequency/bandwidth and line-free channels
- CO(2-1) velocity range for flux integration
- Exact aperture shape and center positions for each nucleus
- Self-calibration solution intervals
- Conversion formula and constants for continuum to mass
- Error propagation for corrected BH masses

## Analysis recipe

1. **Image CO(2-1) and continuum**: Pipeline reduction with WVR scaling and self-calibration, high-resolution cube  
  > "We reduced the data according to the standard ALMA data pipeline process[^2]" (2 Mapping CO(2-1) with ALMA)
   - fitting: _not stated_
   - validation: Compared to cubes without longest baselines (natural and robust=1); fluxes change by 3-20%  
  > "our high-resolution flux densities in the smallest apertures change by 3-20%" (2 Mapping CO(2-1) with ALMA)
2. **Subtract synchrotron from continuum**: Scale MERLIN 5 GHz flux with spectral index nu^-1.06  
  > "using a spectral index of $\nu^{-1.06}$ based on peak emission obtained from the Very Large Array (VLA) at 8.4 GHz (cite: Carral90) and 15 GHz (cite: Colbert94)" (3.2 Measuring the Central Gas Mass Profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive enclosed gas mass profiles**: CO(2-1) luminosity with alpha_CO(2-1)=1.83; continuum with Scoville16 scaled to 100 K; 38 pc aperture  
  > "We therefore set 38 pc as our aperture in Figure [2](#massprofiles) to calculate the gas masses contaminating the original OSIRIS measurements" (3.3 Interpreting the Central Gas Masses)
   - assumption: Mass-weighted dust temperature 100 K  
  > "we scale the relation linearly to a mass-weighted dust temperature of 100 K" (3.2 Measuring the Central Gas Mass Profiles)
   - fitting: _not stated_
   - validation: Two independent mass estimates compared; difference taken as systematic error  
  > "these two mass estimates only differ by a factor of a few, so we propagate both estimates through our calculations" (3.2 Measuring the Central Gas Mass Profiles)
4. **Correct BH masses and compute depletion times**: Subtract gas mass from dynamical mass; accretion rate from L=eta Mdot c^2 with eta=10%  
  > "Using L$=\eta$ $\dot{\text{M}}$ c$^{2}$ and assuming an energy efficiency $\eta$ of 10%" (3.4 Accretion Rates)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| North gas mass (continuum) | 9.8e7 | 0.7e7 | Msun | 3 | We find $9.8 \pm 0.7 \times10^{7}$ M$_{\ensuremath{\odot}}$ of gas (from the continuum emission) |
| North gas mass (CO) | 4.2e7 | 2.3e7 | Msun | 3 | $4.2 \pm 2.3 \times10^{7}$ M$_{\ensuremath{\odot}}$ of gas (from the CO emission) |
| South gas mass (continuum) | 7.7e8 | 0.5e8 | Msun | 3 | $7.7 \pm 0.5 \times10^{8}$ M$_{\ensuremath{\odot}}$ of gas (from the continuum emission) |
| South gas mass (CO) | 1.2e8 | 0.7e8 | Msun | 3 | $1.2 \pm 0.7 \times10^{8}$ M$_{\ensuremath{\odot}}$ of gas (from the CO emission) |
| Gas fraction of BH dynamical mass (north; south) | 5-11%; 6-89% | not stated | percent | 4 | 5%-11% (6%-89%) of the original dynamical mass measurement of the north (south) black hole is actually contamination by gas |
| Depletion timescales (north; south) | ~2 Gyr; ~5 Gyr | not stated | Gyr | 4 | the depletion timescales are therefore roughly 2 Gyr for the north and 5 Gyr for the south |

## Qualitative findings

- CO(2-1) follows a clumpy ribbon between nuclei, while continuum peaks on the nuclei  
  > "The CO(2-1) emission, on the other hand, follows a clumpy ribbon between the nuclei and gives little clue to the locations of the nuclei." (2)

## Claim tuples

- H: Nuclear molecular gas inflates dynamical BH masses in NGC 6240 | E: Measure gas mass within 38 pc of each nucleus from ALMA CO(2-1) and continuum | R: South: 6-89% of mass is gas; north: 5-11% | F: South BH mass brought onto scaling relations; north remains overmassive | **supported**
- H: Gas near BHs can fuel AGN on tens of pc scales | E: Compare gas masses with accretion rates | R: Depletion timescales of 2-5 Gyr | F: Substantial central gas challenges Bondi-type prescriptions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Longest-baseline data have poorer phase stability so flux may be lost; masses conservative  
  > "we expect our flux measurements to be low and thus our masses conservative" (2)
- Limitation (authors): CO flux measured in projection, so CO masses may be upper limits  
  > "one might consider the CO-implied mass measurement an upper limit" (3.2)
- Caveat (inferred, ours): Dust temperature 100 K and alpha_CO are assumed uniformly, with large systematic uncertainty
- Caveat (inferred, ours): Gas in projection may not be circumnuclear
- Caveat (inferred, ours): Continuum and CO masses differ by up to a factor of ~6 in the south

## Reproducibility

- Data public (paper): Programs cited by code; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00370.S and" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Reduction details are in Treister et al. 2019 (submitted)
- Missing: Imaging and aperture parameters
- Data volume (inferred): ~100s GB to ~1 TB for five configurations of Band 6 data
- Score (inferred): 3/5, Data are identifiable and the mass method is simple, but imaging and reduction details are deferred to another paper.
- Rediscovery candidate: no, Reduction details are deferred to a companion paper and many analysis settings are unstated.

## Links

- Method: Treister et al. 2019, submitted (Full ALMA reduction)
- Method: (cite: Scoville16) (Continuum-to-gas-mass calibration)
- Method: (cite: cicone18) (alpha_CO for NGC 6240)
- Companion: Treister et al. 2019, submitted (Detailed CO analysis)
- Companion: (cite: Medling15_bh) (Original dynamical BH masses)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
