# The Coupled Physical Structure of Gas and Dust in the IM Lup Protoplanetary Disk

`2016ApJ...832..110C` | The Astrophysical Journal 2016 | first author: Cleeves, L. Ilsedore | arXiv: 1610.00715 | DOI: 10.3847/0004-637X/832/2/110

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How are the gas (CO) and dust distributed in the IM Lup disk, and what do they imply for disk temperature, CO abundance, optical depth and the external UV field?  
  > "We investigate how the spatially distinct dust and gas components affect the observed tracers and inferred physical properties, including disk temperatures, UV irradiation, and CO abundances." (1. INTRODUCTION)
- Target **IM Lup (Sz 82)**: coordinates _not stated_; z/distance 161 ± 10 pc  
  > "at a distance of d = 161 ± 10 pc (Gaia Collaboration et al. 2016)" (1. INTRODUCTION); distance from Gaia Collaboration et al. 2016  
  > "at a distance of d = 161 ± 10 pc (Gaia Collaboration et al. 2016)" (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00226.S
- bands: Band 6 and Band 7  
  > "carried out with the Atacama Large Millimeter/Submillimeter Array (ALMA) at Bands 6 and 7 targeting lines of CO and its isotopologues" (2.1 Data Reduction)
- frequencies and spectral setup: Band 6: 13 SPWs, 12 with 0.061 MHz channels and 59 MHz bandwidth, one 0.122 MHz/469 MHz; Band 7: line SPWs 0.244 MHz channels, continuum SPW 15.625 MHz channels  
  > "had 0.061 MHz channels and bandwidths of 59 MHz. The thirteenth had a channel size of 0.122 MHz and a bandwidth of 469 MHz." (2.1 Data Reduction); "The line-targeted spectral windows had channel widths of 0.244 MHz." (2.1 Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6: 20-650 m (31 antennae); Band 7: 28-646 m (34 antennae)  
  > "Thirty-one 12-m antennae were used, with baselines spanning 20 to 650 meters." (2.1 Data Reduction); "with 24 minutes on source and 28 − 646 meter baselines across 34 antennae" (2.1 Data Reduction)
- angular resolution: Band 7 continuum beam 0.37"x0.29"; Band 6 continuum 0.54"x0.40"  
  > "Continuum 875 µm 0 ′′ . 37 × 0 ′′ . 29 (47 . 0 ◦ )" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6: 21 min; Band 7: 24 min  
  > "with 21 minutes of on source integration" (2.1 Data Reduction)
- observing dates: Band 6: 2014 July 7; Band 7: 2014 June 8  
  > "The Band 7 data were observed 2014 June 8" (2.1 Data Reduction)
- pi or archival as stated: Band 6 PI Oberg; Band 7 PI Cleeves  
  > "project code ADS/JAO.ALMA#2013.00694; PI: Cleeves" (2.1 Data Reduction)
- Line: 13CO J=3-2 (330.588 GHz)
- Line: C18O J=3-2 (329.331 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: HC18O+ J=4-3 (not stated)
- Other facility **Swift UVOT**: UVM2 fluxes of IM Lup and TW Hya to normalize the stellar FUV spectrum  
  > "Both sources have been observed by Swift using the broadband UVM2 filter (PI: Cleeves)" (3.2 Radiation Field and Gas Temperature Estimates)
- Other facility **Hipparcos**: _not stated_
- External data: IM Lup SED compiled (2MASS, Spitzer, SMA, optical)  
  > "we compare the model to the observed values compiled by Pinte et al. (2008), to which we have added a 6.8 mm observation from Lommen et al. (2010)" (3.1) [from Pinte et al. 2008; Lommen et al. 2010]
- External data: X-ray luminosity 4.3e30 erg/s  
  > "an X-ray luminosity of 4.3 × 10 [30] erg s − 1 (G¨unther et al. 2010)" (3.2) [from Günther et al. 2010]
- External data: Distance 161 pc  
  > "d = 161 ± 10 pc (Gaia Collaboration et al. 2016)" (1. INTRODUCTION) [from Gaia Collaboration et al. 2016]

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA/NAASC staff (Band 6) and with staff-provided scripts (Band 7), plus one round of phase self-cal  
  > "The 2013.1.00226 observations were calibrated by ALMA/NAASC staff" (2.1 Data Reduction); "We calibrated the observations using the scripts provided by the ALMA/NAASC staff" (2.1 Data Reduction)
- casa version: CASA 4.4.0 (Band 6), 4.5.0 (Band 7)  
  > "using CASA 4.5.0" (2.1 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used for the flux calibration." (2.1 Data Reduction)
- flux scale uncertainty: 15%  
  > "combined with 15% calibration uncertainty" (Table 1)
- self calibration: One round of phase self-cal; solint 6 s (Band 6), 30.25 s (Band 7)  
  > "One round of phase selfcalibration was applied with solution intervals of 30.25 seconds using CASA 4.5.0." (2.1 Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "moment 0 maps made using Briggs weighting (robust parameter of 0.5) with multi-scale clean" (2.2 Observed Features)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0.03", 0.3", 0.9"  
  > "multi-scale clean (with scales of 0 ′′ . 03, 0 ′′ . 3, and 0 ′′ . 9)" (2.2 Observed Features)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Re-imaged with uniform 0.6" restoring beam for line ratios; 0.4" for 13CO/C18O 3-2 ratio  
  > "we have re-imaged the lines with a uniform restoring beam of 0 ′′ . 6" (4.4)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk structure parameterization (self-similar surface density)  
  > "The general form of the physical structure follows Andrews et al. (2011)" (3.1) [from Andrews et al. (2011)]
- Gas temperature from fitting function calibrated to thermochemical models  
  > "The gas temperature is estimated using the total FUV field and local gas density following the procedure described in Cleeves et al. (2015)." (3.2) [from Cleeves et al. (2015); Bruderer (2013)]
- Chemical code and network  
  > "We use the chemical code of Fogel et al. (2011) with updates as described in Cleeves et al. (2014)" (3.3) [from Fogel et al. (2011); Cleeves et al. (2014)]
- External radiation treatment  
  > "Following the procedure in Cleeves (2016), we compute the absorption optical depth to each location" (3.2) [from Cleeves (2016); Cleeves et al. (2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean thresholds, cell size, image size and masks
- Flux correction/bootstrap details and weights from statwt settings
- Full grid of best-fit parameter uncertainties; fitting was by eye, so no objective criterion
- TORUS and LIME setup details (photon numbers, grid) and chemical code availability
- Stellar FUV spectral template details and scaling procedure
- Whether archive products can reproduce the self-calibrated data exactly

## Analysis recipe

1. **Image continuum and CO lines**: Briggs-weighted multiscale CLEAN; moment 0 maps and disk-integrated spectra  
  > "Figure 1 presents moment 0 maps made using Briggs weighting (robust parameter of 0.5) with multi-scale clean" (2.2 Observed Features)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk geometry and stellar mass**: Gaussian fit to Band 7 continuum for PA and inclination; PV diagram for stellar mass  
  > "we measure a disk position angle of 144 ± 3 ◦ and an inclination of i = 48 ± 3 ◦ (deconvolved from the beam) using the Gaussian fitting tool in CASA viewer" (2.2 Observed Features)
   - software: CASA
   - assumption: distance 161 pc  
  > "Assuming an i = 48 ± 3 ◦ and a distance of 161 pc" (2.2 Observed Features)
   - fitting: _not stated_
   - validation: Compared with Pinte et al. 2008 and Panic et al. 2009 inclinations  
  > "Our inclination is in agreement with the value derived by Pinte et al. (2008), 50 ◦" (2.2 Observed Features)
3. **Model dust and gas density/thermal structure**: Two-population dust (small/large grains) parametric disk with TORUS radiative equilibrium; compare 875 um visibilities (vis_sample) and SED  
  > "We compare the model directly in the visibility plane using the vis ~~s~~ ample package" (3.1)
   - software: TORUS, vis_sample, CASA statwt
   - parameter: MRN size distribution, 0.005 um min, max 1 um and 1 mm; 80% silicates + 20% graphite  
  > "minimum grain size of 0.005 µm and a maximum grain size of 1 µm and 1 mm for the small and large grains" (3.1)
   - assumption: global gas-to-dust ratio 100; Teff 3900 K, R* 2.5 Rsun, M* 1 Msun  
  > "The disk-integrated mass in gas is calculated assuming a global gas to dust mass ratio of 100" (3.1)
   - fitting: Favored model chosen by eye comparison to SED and visibilities  
  > "we have compared the model SED and 875 µm visibilities to the observations by eye" (4.1)
   - validation: 1.3 mm visibilities not fit and used as a test  
  > "We did not fit directly to the 1.3 mm visibilities, which enables us to use them as a test of the model structure." (4.1)
4. **Compute UV/X-ray fields and gas temperature**: Monte Carlo radiative transfer of stellar FUV/X-ray plus external G0 = 1,2,4,8,16; gas temperature fitting function  
  > "We explore models with G0 values of 1, 2, 4, 8, and 16." (3.2)
   - software: Bethell & Bergin 2011 code, HEAsoft uvotsource
   - assumption: TW Hya FUV spectral shape scaled by ~1.1 to IM Lup  
  > "IM Lup is a factor of ∼ 1 . 1 brighter at 2246 ˚A." (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute time-dependent CO chemistry**: 2D time-dependent chemical network (6284 reactions, 665 species) with position-dependent dust surface area  
  > "The reaction network includes 6284 reactions and 665 species (Cleeves et al. 2014)." (3.3)
   - software: Fogel et al. 2011 chemical code
   - assumption: molecular-cloud-like initial abundances (Table 2), 1 Myr age  
  > "The chemical models are initialized with “molecular cloud-like” initial conditions." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Simulate lines and fit CO reduction and G0**: LIME non-LTE line RT, chi2 in visibility plane over grid of fCO (0.01-1.0) and G0; line ratio and radial profile comparison  
  > "We examine models with six different values of f CO, 0.01, 0.05, 0.1, 0.2, 0.5, and 1.0 (no reduction)." (4.4)
   - software: LIME v1.6, LAMDA database
   - parameter: turbulent width 100 m/s; 16O/18O = 540, 12C/13C = 70; central 5 channels of 12CO excluded  
  > "a fixed turbulent broadening width of 100 m s − 1" (3.4)
   - assumption: fixed inclination and PA from continuum  
  > "The disk distance and inclination/position angle are fixed to that derived from the continuum." (3.4)
   - fitting: chi2 grid in real and imaginary visibilities over channels detected >3 sigma  
  > "takes into account both real and imaginary visibilities over all channels where the line was detected at greater than 3 σ in the integrated spectrum" (4.4)
   - validation: Same best fit recovered without continuum subtraction  
  > "The same best fit solution, CO reduction of 20 and G 0 ≤ 4, is recovered if models and data are compared without continuum subtraction" (4.4)
7. **Independent estimate of external G0 from Hipparcos stars**: Sum blackbody UV flux from 23,315 O, B, A stars within 1 kpc with assumed UV extinction  
  > "The final catalogue contains 23,315 local O, B and A-type stars." (Appendix A)
   - software: astropy coordinates
   - assumption: constant line-of-sight A_UV 0-3 mag/kpc; blackbody emission  
  > "We also assume for simplicity that the stars emit as blackbodies at their catalogue identified effective temperature." (Appendix A)
   - fitting: _not stated_
   - validation: Compared to CO-derived G0  
  > "The Hipparcos estimated external G 0 is between 2 . 9 − 4 . 5, which is consistent with our estimate from the CO observations." (5.4)

## Software

- **CASA** 4.4.0 / 4.5.0: calibration, self-cal, statwt, imaging, Gaussian fits, PV diagram  
  > "phase self-calibration with solutions calculated for each integration (6s) in CASA (McMullin et al. 2007) version 4.4.0" (2.1 Data Reduction)
- **TORUS** : dust density and thermal structure, synthetic SED/images  
  > "The disk gas and dust density and dust thermal structure models are computed using the code TORUS" (3.1)
- **vis_sample** : sampling models at observed uv points  
  > "We compare the model directly in the visibility plane using the vis ~~s~~ ample package" (3.1)
- **LIME** v1.6: non-LTE line radiative transfer  
  > "we compute line intensities using the non-LTE line radiative transfer code LIME v1.6" (3.4)
- **HEAsoft uvotsource** : Swift UVM2 photometry  
  > "Using the Swift UVOT data products and the uvotsource routine in HEAsoft" (3.2)
- **astropy** : 3D stellar positions in Hipparcos G0 calculation  
  > "with the astropy coordinates package" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass | 1.7e-3 | within 25% | Msun | 3 | The total dust mass is 1 . 7 × 10 − 3 M ⊙ |
| Gas mass (gas/dust=100) | 0.17 | not stated | Msun | 3 | corresponds to a gas mass of 0.17 M ⊙ |
| Large-grain disk truncation radius | 313 | 15 | AU | 3 | large grain disk is outwardly truncated at 313 ± 15 AU |
| Disk inclination | 48 | 3 | deg | 2 | an inclination of i = 48 ± 3 ◦ |
| Position angle | 144 | 3 | deg | 2 | position angle of 144 ± 3 ◦ |
| Stellar mass from 13CO rotation | 1.0 | 0.2 | Msun | 2 | consistent with a 1 . 0 ± 0 . 2 M ⊙ star |
| External radiation field from CO | G0 ≤ 4 | not stated | Habing | 6 | we find G 0 ≤ 4 based on the global line fluxes and the line ratio profiles |
| CO reduction (underabundance) | factor 20 (5% of ISM) | not stated | dimensionless | 6 | we find that CO is under-abundant by a factor of 20 based on all CO data |
| Hipparcos external G0 | 2.9-4.5 | not stated | Habing | 7 | The Hipparcos estimated external G 0 is between 2 . 9 − 4 . 5 |
| Disk scale height at 100 AU | 12 | not stated | AU | 3 | our estimate of the scale height at 100 AU is 12 AU |
| Inner disk component mass | 0.035 | not stated | Msun | 3 | The resulting inner disk component contains 0.035 M ⊙ or about 20% of the total disk mass. |
| Band 7 continuum flux | 0.59 | 0.09 | Jy | 1 | 0 . 59 ± 0 . 09 Jy |
| 12CO detected radius | 970 | not stated | AU | 1 | The 12 CO is detected out to a radius of 970 AU |

## Qualitative findings

- Inner continuum is optically thick and likely vertically extended, causing the CO isotopologue emission hole  
  > "We find that the dust in the inner disk is sufficiently optically thick to hide line emission." (6. SUMMARY)
- Tentative ring-like continuum breaks near 150 and 250 AU; diffuse 12CO halo  
  > "there are intriguing breaks present in the observed deprojected Band 7 continuum brightness profile near 0 ′′ . 95 (150 AU) and 1 ′′ . 55 (250 AU)" (5.6)

## Claim tuples

- H: Dust depletion in the outer disk allows CO to persist in gas to large radii | E: Coupled dust/gas/chemistry model compared with ALMA CO lines | R: CO detected to 970 AU while mm continuum truncated at 313 AU; model reproduces CO with fCO ~0.05 | F: Reduced dust exposes the outer disk to radiation and slows freeze-out | **supported**
- H: The external radiation field is low | E: Grid of G0 values compared to line fluxes and ratios; Hipparcos census | R: G0 ≤ 4; Hipparcos 2.9-4.5 | F: Consistent with local stellar population | **supported**
- H: CO is depleted or the disk is gas-poor | E: fCO grid | R: CO under-abundant by factor of 20; C18O prefers ≳2x more reduction | F: Early carbon depletion, or gas-to-dust ratio of 5; hints of isotope-selective photodissociation | **partially**
- H: Inner CO deficit is due to dust opacity blocking | E: Optical depth estimates and 10x dust test in inner 50 AU | R: Extra dust deepens the hole to the observed range | F: mm grains are optically thick and vertically lofted in the inner disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Chemical model rather than parametric CO because of extended CO beyond dissociation boundary  
  > "Our departure from this modeling approach is primarily motivated by the presence of extended CO picked up in the sensitive ALMA images." (3.3)
- Alternative: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass assumes gas-to-dust 100 with no independent gas tracer such as HD  
  > "we simply assume that the gas mass is 100 times more massive than the dust mass as we do not have an independent constraint for the gas mass" (3.1)
- Limitation (authors): Inner disk poorly constrained at resolution limit  
  > "the properties of the bright inner disk are less well constrained" (4.1)
- Caveat (inferred, ours): Best-fit model chosen by eye without uncertainties on most parameters
- Caveat (inferred, ours): Degeneracy between CO abundance and gas mass
- Caveat (inferred, ours): Simplified opacity and no isotopologue chemistry
- Caveat (inferred, ours): Single distance and fixed stellar parameters

## Reproducibility

- Data public (paper): ALMA data cited by project code; Swift public archive data  
  > "We acknowledge the use of public data from the Swift data archive." (Acknowledgements)
- Products in archive: _not stated_
- Code: vis_sample available on github  
  > "which is publicly available on github" (3.1)
- Missing: Parameter fitting is by eye, not reproducible algorithmically
- Missing: Chemical code and thermal fitting not released
- Missing: Imaging parameters beyond robust and scales
- Data volume (inferred): ~10-50 GB for two ALMA datasets
- Score (inferred): 3/5, ALMA data are public and many parameters tabulated, but the multi-code model chain and by-eye fitting are hard to replicate.
- Rediscovery candidate: no, Main results depend on a complex bespoke model chain with by-eye fits.

## Links

- Method: Andrews et al. 2011 (disk structure parameterization)
- Method: Cleeves et al. 2014 (chemical network)
- Method: Cleeves 2016 (external radiation treatment)
- Companion: Öberg et al. 2015 (earlier C18O and DCO+ data on IM Lup)
- Related: Lupus ALMA survey (Ansdell et al. 2016)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00694.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 60,
  "rate": 0.645
 },
 "evidence_ok": true
}
```
