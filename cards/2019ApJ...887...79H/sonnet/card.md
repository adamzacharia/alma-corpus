# The Interaction between the Supernova Remnant W41 and the Filamentary Infrared Dark Cloud G23.33-0.30

`2019ApJ...887...79H` | The Astrophysical Journal 2019 | first author: Hogge, Taylor G. | arXiv: 1910.13070 | DOI: 10.3847/1538-4357/ab5180

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: Are the narrow NH3(3,3) lines and broad line widths in the IRDC filament G23.33-0.30 caused by a large-scale shock, possibly from SNR W41?  
  > "To confirm the suspected NH$_3$(3,3) maser emission, determine its excitation conditions, and investigate the nature of the broad NH$_3$ line widths, we have performed followup observations of G23.33-0.30" (Introduction)
- Target **G23.33-0.30**: coordinates l~23.32 deg, b~-0.30 deg (from maser and core positions)  
  > "We adopted $D=4.59^{+0.38}_{-0.33}$ kpc, the parallax distance to the high-mass star-forming region G23.01-0.41 that also resides within GMC 23.0-0.4" (4.3 Virial Analysis); z/distance 4.59 (+0.38/-0.33) kpc  
  > "We adopted $D=4.59^{+0.38}_{-0.33}$ kpc, the parallax distance to the high-mass star-forming region G23.01-0.41 that also resides within GMC 23.0-0.4" (4.3 Virial Analysis); distance from maser parallax distance to G23.01-0.41 (Brunthaler et al. 2009)  
  > "We adopted $D=4.59^{+0.38}_{-0.33}$ kpc, the parallax distance to the high-mass star-forming region G23.01-0.41 that also resides within GMC 23.0-0.4" (4.3 Virial Analysis)

## Data provenance

- ALMA projects: 2016.1.01345.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (7 m) for SiO(5-4), CS(5-4), 1.3 mm continuum  
  > "We observed G23.33-0.30 with the ACA using three pointings and five 50 min execution blocks in two spectral setups." (2.2 ACA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SiO 7.2x4.5 arcsec; CS 6.0x4.2 arcsec; continuum 6.6x4.0 and 6.4x4.1 arcsec  
  > "SiO(5-4) | 217.10498 | 0.8 | $7.2 \times 4.5$ | 689 | 0.34 | 20.2" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: ACA rms: SiO 20.2, CS 22.9 mJy/beam per channel; continuum 3.7 and 4.3 mJy/beam  
  > "CS(5-4) | 244.93556 | 0.7 | $6.0 \times 4.2$ | 261 | 0.29 | 22.9" (Table 2)
- time on source: _not stated_
- observing dates: 2017 Jul 10-13 (SiO) and 2017 Jul 8 (CS)  
  > "ACA | 2017 Jul 10-13 | SiO(5-4) | 217.10498" (Table 2)
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (217.10498 GHz)
- Line: CS 5-4 (244.93556 GHz)
- Other facility **VLA**: NH3(1,1)-(6,6) D-array and NH3(3,3) A-array data; masers and thermal NH3  
  > "we present Karl G. Jansky Very Large Array (VLA) observations of the NH$_3$(1,1) through (6,6) inversion lines" (Introduction)
- Other facility **SMA**: 13CO(2-1), C18O(2-1) and 1.3 mm continuum for cores and virial analysis  
  > "Submillimeter Array[^1] (SMA) observations of $^{13}$CO(2-1), C$^{18}$O(2-1), and 1.3 mm continuum" (Introduction)
- Other facility **Herschel**: dust temperature and filament mass  
  > "we analyzed *Herschel* sub-mm data (cite: 2010PASP..122..314M) using a single temperature graybody model" (4.3 Virial Analysis)
- External data: Parallax distance 4.59 kpc to G23.01-0.41  
  > "We adopted $D=4.59^{+0.38}_{-0.33}$ kpc, the parallax distance to the high-mass star-forming region G23.01-0.41" (4.3 Virial Analysis) [from (cite: 2009ApJ...693..424B)]
- External data: A-array VLA NH3(3,3) data of G23.33-0.30  
  > "G23.33-0.30 was also recently observed by (cite: KS) using the VLA in the A array configuration" (2.1 VLA Observations) [from (cite: KS)]

## Processing

### Calibration

- pipeline or manual: ACA data calibrated by ALMA pipeline  
  > "The ACA data were calibrated by the ALMA data reduction pipeline and imaged using CASA 4.7.2." (2.2 ACA Observations)
- casa version: CASA 4.7.2 (imaging)  
  > "The ACA data were calibrated by the ALMA data reduction pipeline and imaged using CASA 4.7.2." (2.2 ACA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (setup 1), J1751+0939 (setup 2)  
  > "For the first spectral setup we performed the flux calibration using observations of J1733-1304 and for the second spectral setup we used observations of J1751+0939." (2.2 ACA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "We carried out imaging using CASA’s `tclean` algorithm with Briggs weighting and the robustness parameter set to 0.5." (2.2 ACA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We carried out imaging using CASA’s `tclean` algorithm with Briggs weighting and the robustness parameter set to 0.5." (2.2 ACA Observations)
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

- NH3 LTE modeling methods  
  > "Using the NH$_3$ modeling methods described by (cite: 2018ApJS..237...27H), we employed a PySpecKit (cite: 2011ascl.soft09001G) LTE NH$_3$ model" (4.2 Thermal NH3 Emission) [from (cite: 2018ApJS..237...27H)]
- Herschel graybody dust temperature and mass methods  
  > "using a single temperature graybody model and the methods and assumptions described by (cite: 2015ApJ...815..130G)" (4.3 Virial Analysis) [from (cite: 2015ApJ...815..130G)]

### Not stated but needed to reproduce (our reading)

- ACA cell size, image size, masks, cleaning threshold and deconvolver
- Continuum-subtraction and line-free channels
- Number of tclean iterations and spectral binning
- Primary-beam correction details
- ACA flux scale uncertainty
- Whether ACA data were combined with SMA or other arrays
- MCMC priors and walker settings for emcee fits

## Analysis recipe

1. **Fit maser positions and fluxes**: Gaussian line fits to cubes then beam-model fits to amplitude maps with emcee  
  > "We used the Python Markov Chain Monte Carlo (MCMC) fitting package `emcee` (cite: 2013PASP..125..306F) to fit both the narrow line emission in the data cube and the resulting maps of the line amplitudes." (4.1 NH3(3,3) Maser Emission)
   - software: emcee
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive NH3 Trot, sigma, VLSR**: PySpecKit LTE NH3 model fit to (1,1),(2,2) and (4,4),(5,5)  
  > "we only fit pixels that had NH$_3$(2,2) integrated intensities greater than 10 mJy beam$^{-1}$ km s$^{-1}$" (4.2 Thermal NH3 Emission)
   - software: PySpecKit
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit core sizes and fluxes from SMA continuum**: two elliptical Gaussians convolved with beam via MCMC  
  > "we modeled the SMA continuum emission as the superposition of two elliptical Gaussians convolved with the SMA synthesized beam" (4.3 Virial Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive core mass and virial parameter**: Hildebrand mass equation and MacLaren virial mass from 13CO sigma  
  > "We assumed $\mathbb{R}=100$ and $\kappa_{1.3 \ \rm{mm}} = 0.9 \ \rm{cm}^2 \ \rm{g}^{-1}$" (4.3 Virial Analysis)
   - assumption: gas-to-dust 100, kappa 0.9 cm2/g, Tdust 18±2 K, n=1.8, D=4.59 kpc, 30% uncertainty on R and kappa  
  > "We assumed that $n=1.8$, the average value for the radial density profile index found by (cite: 2009ApJ...696..268Z) in IRDC cores." (4.3 Virial Analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (ACA imaging); 5.1.1-5 (VLA): ACA imaging with tclean; VLA calibration and imaging  
  > "The ACA data were calibrated by the ALMA data reduction pipeline and imaged using CASA 4.7.2." (2.2 ACA Observations)
- **emcee** : maser and core fits  
  > "We used the Python Markov Chain Monte Carlo (MCMC) fitting package `emcee` (cite: 2013PASP..125..306F)" (4.1 NH3(3,3) Maser Emission)
- **PySpecKit** : LTE NH3 model fits  
  > "we employed a PySpecKit (cite: 2011ascl.soft09001G) LTE NH$_3$ model" (4.2 Thermal NH3 Emission)
- **MIRIAD** 4.3.8: SMA imaging  
  > "We imaged the data with MIRIAD 4.3.8 using MIRIAD’s `clean` algorithm" (2.3 SMA Observations)
- **RADEX** : non-LTE NH3 maser and ratio models  
  > "Figure [9](#fig:radex_maser) shows a non-LTE RADEX (cite: 2007A&A...468..627V) plot" (5.1 Evidence of a Large-Scale Shock)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core mass MM1 | 9.9 | ±4.7 | Msun | 4 | $M$ (M$_{\odot}$) / $9.9\pm4.7$ / $7.2\pm3.4$ / $6.7\pm3.2$ |
| Virial parameter MM3 | 3.9 | ±1.9 | dimensionless | 4 | $\alpha$ / $<3.7$ / $<9.2$ / $3.9\pm1.9$ |
| Maser 1 flux | 1.312 | ±0.086 | Jy | 1 | $I_{\nu}$ (Jy) / $1.312\pm0.086$ / $0.562\pm0.049$ / $0.453\pm0.033$ / $0.078 \pm 0.001$ |
| Filament mass | 600 | not stated | Msun | 0 | We calculated a gas mass of $M\sim600$ M$_{\odot}$ for the $\sim 3\times0.2$ pc portion of G23.33-0.30 |

## Qualitative findings

- Extended SiO(5-4) emission indicates a large-scale shock rather than protostellar outflows  
  > "Since protostellar outflows cannot account for such extended SiO emission, it is more likely that a large-scale shock from a SNR is responsible." (5.1 Evidence of a Large-Scale Shock)

## Claim tuples

- H: The narrow NH3(3,3) lines are masers | E: VLA A and D array imaging and brightness temperature fits | R: Three masers have brightness temperature >>Tgas; fourth is 17 K | F: Four NH3(3,3) masers, the fourth tentative | **supported**
- H: A SNR shock, not protostellar outflows, drives the filament kinematics | E: ACA SiO and CS, NH3 kinematics and Trot | R: Widespread SiO, velocity discontinuity, hotter and more turbulent blueshifted gas | F: Shock likely from W41 | **partially**
- H: The embedded cores can collapse | E: Virial analysis of SMA continuum cores | R: alpha = 4-9 | F: Cores unlikely to collapse | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: HII regions and protostellar outflows considered and disfavored as turbulence/shock sources  
  > "Consequently, G23.33-0.30’s high levels of turbulence are most likely the result of a SNR-MC interaction." (5.2 W41’s SNR-MC Interaction with GMC G23.0-0.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Crowded line of sight and ambiguous impact geometry  
  > "A caveat to this interpretation is that W41 lies near the plane of the Galaxy, so the line of sight towards the SNR is crowded with molecular clouds at various velocities" (5.2 W41’s SNR-MC Interaction with GMC G23.0-0.4)
- Caveat (inferred, ours): ALMA ACA data are only used qualitatively for kinematics
- Caveat (inferred, ours): SNR association is speculative
- Caveat (inferred, ours): Virial analysis relies on 13CO sigma from SMA and assumed 18 K from coarse Herschel data

## Reproducibility

- Data public (paper): ALMA project listed in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2016.1.01345.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ACA imaging parameters
- Missing: VLA and SMA data are not ALMA and need separate access
- Missing: A-array data from an unpublished thesis
- Data volume (inferred): ACA ~ tens of GB raw; VLA/SMA additional
- Score (inferred): 2/5, ALMA role is minor and imaging details are sparse; key results rely on VLA and SMA.
- Rediscovery candidate: no, ALMA contributes only qualitative SiO/CS maps; numeric results come from VLA and SMA data.

## Links

- Method: (cite: 2018ApJS..237...27H) (NH3 modeling methods)
- Method: (cite: 2015ApJ...815..130G) (Herschel dust temperature and mass methods)
- Companion: (cite: KS) (VLA A-array observations)
- Related: RAMPS
- Related: HOPS
- Related: GRS
- Related: MAGPIS

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 34,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
