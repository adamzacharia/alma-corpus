# From Nuclear to Circumgalactic: Zooming in on AGN-driven Outflows at z ∼ 2.2 with SINFONI

`2020ApJ...894...28D` | The Astrophysical Journal 2020 | first author: Davies, Rebecca L. | arXiv: 2004.02891 | DOI: 10.3847/1538-4357/ab86ad

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the spatially resolved properties and energetics of AGN-driven ionized outflows in three z~2.2 galaxies, and what impact do they have on their hosts and surroundings?  
  > "We use deep adaptive optics assisted integral field spectroscopy from SINFONI on the VLT to study the spatially resolved properties of ionized gas outflows driven by active galactic nuclei (AGN)" (abstract)
- Target **K20-ID5**: coordinates 03:32:31.4 -27:46:23.2  
  > "| K20-ID5 | 03:32:31.4 | -27:46:23.2 | 2.224 | 11.2 | 720 | 335 | UV + IR | 1.3 | 45.6 |" (Table 1); z/distance z = 2.224  
  > "| K20-ID5 | 03:32:31.4 | -27:46:23.2 | 2.224 | 11.2 | 720 | 335 | UV + IR | 1.3 | 45.6 |" (Table 1); distance from _not stated_
- Target **COS4-11337 / COS4-11363**: coordinates 10:00:28.70 +02:17:44.8 (COS4-11337)  
  > "| COS4-11337 | 10:00:28.70 | +02:17:44.8 | 2.096 | 11.3 | 450 | 395 | UV + IR | 0.8 | 46.2 |" (Table 1); z/distance z = 2.096 (11337); 2.097 (11363)  
  > "| COS4-11337 | 10:00:28.70 | +02:17:44.8 | 2.096 | 11.3 | 450 | 395 | UV + IR | 0.8 | 46.2 |" (Table 1); distance from _not stated_
- Target **J0901**: coordinates 09:01:22.4 +18:14:32.3  
  > "| J0901 | 09:01:22.4 | +18:14:32.3 | 2.259 | 11.2 | 780 | 200 | IR | 1.2 | 46.3 |" (Table 1); z/distance z = 2.259  
  > "| J0901 | 09:01:22.4 | +18:14:32.3 | 2.259 | 11.2 | 780 | 200 | IR | 1.2 | 46.3 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00228.S, 2016.1.00726.S
- bands: Band 4  
  > "was observed for 90 minutes in Band 4 as part of program 2016.1.00726.S (PI: A. Man)" (Redshift of COS4-11363)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.39" (COS4-11337/11363)  
  > "have a spatial resolution of 0.39” which is sufficient to resolve the two galaxies" (Redshift of COS4-11363)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 90 minutes (2016.1.00726.S)  
  > "was observed for 90 minutes in Band 4" (Redshift of COS4-11363)
- observing dates: _not stated_
- pi or archival as stated: Archival; PI A. Man (2016.1.00726.S), PI G. Popping (2015.1.00228.S)  
  > "We break the redshift degeneracy by utilising archival ALMA observations." (Redshift of COS4-11363)
- Line: CO 4-3 (not stated)
- Other facility **VLT/SINFONI (AO and seeing-limited)**: Primary K-band IFU data for Halpha/[NII] outflow analysis  
  > "We used the Laser Guide Star (LGS) Adaptive Optics (AO) mode (cite: Bonnet03), achieving spatial resolutions of 0.18-0.24” (FWHM)" (2 Sample and Observations)
- Other facility **VLT/KMOS**: Seeing-limited H and K band data  
  > "Our high resolution K band data are supplemented with seeing limited K band data, and H band data" (2 Sample and Observations)
- Other facility **LBT/LUCI**: H-band long-slit spectrum of J0901 for Balmer decrement  
  > "We also observed J0901 in the H band using the LUCI long slit spectrograph on the Large Binocular Telescope (LBT)" (2.3 J0901)
- Other facility **HST**: Archival imaging for lens model and SED fits  
  > "we rely on archival HST F814W (rest frame UV) and F160W (rest frame optical) images" (9.1 Lens Modelling with LENSTOOL)
- External data: 160um flux of J0901 for SFR  
  > "Using the 160$\mu$m flux measurement presented in (cite: Saintonge13) we derive a SFR of 200 M$_\odot$ yr$^{-1}$" (2.3 J0901) [from (cite: Saintonge13)]
- External data: Average electron density ~1000 cm-3 of outflowing gas  
  > "found that the average electron density of the outflowing material is $\sim$ 1000 cm$^{-3}$" (3.4 Mass Outflow Rate) [from (cite: NMFS19)]
- External data: COS4-11337 hard X-ray luminosity log(LX)=44.5  
  > "the hard X-ray luminosity (log(L$_X$/erg s$^{-1}$) = 44.5; (cite: Luo17))" (2.2 COS4-11337/COS4-11363) [from (cite: Luo17)]

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

- Nuclear spectrum extraction method  
  > "The method used to extract the nuclear spectra is described in detail in Section 2.5.1 of (cite: NMFS19)." (3.1 Isolating Emission Associated with Outflows) [from (cite: NMFS19)]
- SINFONI-AO data reduction  
  > "The reduction of the SINFONI-AO data is described in detail in (cite: NMFS18)." (2 Sample and Observations) [from (cite: NMFS18)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, CASA version and weighting for 2016.1.00726.S
- CO(4-3) line flux, channel width and 3 sigma upper-limit details
- Whether archive products were used as-is
- Rest frequency and moment/spectrum extraction aperture for CO(4-3)

## Analysis recipe

1. **Break redshift degeneracy of COS4-11363 with CO(4-3)**: Compare CO(4-3) spectrum at emission peak with expected positions for z=2.097 and z=2.107  
  > "The ALMA data clearly favour the $z$ = 2.097 scenario" (Redshift of COS4-11363)
   - fitting: _not stated_
   - validation: _not stated_
2. **Upper limit on molecular gas mass of COS4-11337**: 3 sigma CO(4-3) upper limit converted with CO(1-0)/CO(4-3)=2.4 and metallicity-dependent alpha_CO  
  > "we find a 3$\sigma$ upper limit on the gas mass of log(M$_{H_2}$/M$_\odot$) $<$ 9.9" (7.4)
   - assumption: CO(1-0)/CO(4-3) = 2.4; alpha_CO from Tacconi18  
  > "assuming CO(1-0)/CO(4-3) = 2.4, and the metallicity-dependent $\alpha_{CO}$ from (cite: Tacconi18)" (7.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **LENSTOOL** 7.0: Lens model of J0901 cluster  
  > "use version 7.0 of the parametric gravitational lens modelling code LENSTOOL" (9.1)
- **DYSMALPY** : Kinematic modelling of K20-ID5 velocity field  
  > "We model the velocity field using DYSMALPY, a python implementation of the dynamical fitting code DYSMAL" (4.1)
- **FAST** : SED fitting of J0901  
  > "fit the SED using the FAST code (cite: Kriek09)" (9.3 Stellar Mass)
- **Galfit** : Cluster member parameters  
  > "Galfit (cite: Peng02; CYPeng10) was applied to the HST I-band and H-band images" (9.1)
- **Flame** : LUCI data reduction  
  > "reduced independently using the Flame pipeline (cite: Belli18)" (2.3 J0901)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| K20-ID5 outflow velocity | 1410 | 56 | km/s | 0 | we measure an outflow velocity of 1410 $\pm$ 56 km s$^{-1}$ |
| K20-ID5 mass outflow rate | 262 | 76 | Msun/yr | 0 | we measure a mass outflow rate of 262 $\pm$ 76 M$_\odot$ yr$^{-1}$ |
| J0901 outflow radius | 470 | 70 | pc | 0 | The de-convolved Gaussian HWHM of the outflow emission is 470 $\pm$ 70 pc |
| COS4-11363 [NII]/Halpha | 2.6 | 0.4 | dimensionless | 0 | We measure an \[N II\]/H$\alpha$ ratio of 2.6 $\pm$ 0.4 |
| COS4-11337 molecular gas mass 3sigma upper limit | log(MH2/Msun) < 9.9 | not stated | dex | 2 | we find a 3$\sigma$ upper limit on the gas mass of log(M$_{H_2}$/M$_\odot$) $<$ 9.9 |

## Qualitative findings

- CO(4-3) detected near COS4-11363 at z=2.097, within 150 km/s of COS4-11337  
  > "We identified CO(4-3) emission at the location of COS4-11363 in archival ALMA data" (9 Summary)

## Claim tuples

- H: Is COS4-11363 at z=2.097 (dv<=150 km/s) or z=2.107 relative to COS4-11337? | E: Archival ALMA Band 4 CO(4-3) spectrum at COS4-11363 | R: CO(4-3) detected near the nucleus, favouring z=2.097 | F: Single SINFONI line is [NII]6583 and the pair is close in velocity | **supported**
- H: Do AGN outflows in K20-ID5 and COS4-11337 suppress instantaneous star formation? | E: Outflow energetics versus main sequence position | R: Galaxies lie on upper main-sequence envelope | F: No significant impact on instantaneous SF | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass outflow rates are lower limits since only the ionized phase is probed, and n_e is poorly constrained  
  > "are only lower limits" (7.3)
- Caveat (inferred, ours): ALMA used only for redshift and a CO upper limit, with no processing detail
- Caveat (inferred, ours): CO offset from HST centroid attributed to HST astrometry

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "We break the redshift degeneracy by utilising archival ALMA observations." (Redshift of COS4-11363)
- Products in archive: _not stated_
- Missing: ALMA reduction and imaging parameters
- Missing: CO(4-3) flux values
- Data volume (inferred): ~10-50 GB for ALMA raw data (two Band 4 projects)
- Score (inferred): 2/5, ALMA role is minor and processing is not described; the main results rely on SINFONI/KMOS data.
- Rediscovery candidate: no, ALMA part lacks a complete recipe and the main results are based on non-ALMA data.

## Links

- Method: (cite: NMFS19) (Nuclear spectrum extraction and outflow methods)
- Companion: (cite: Scholtz20) (Outflows in K20-ID5 and similar AGN at z~2)
- Related: SINS/zC-SINF
- Related: KMOS3D
- Related: 3D-HST

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
