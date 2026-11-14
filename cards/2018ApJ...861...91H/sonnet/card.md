# ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527

`2018ApJ...861...91H` | The Astrophysical Journal 2018 | first author: Harris, Robert J. | arXiv: 1805.08792 | DOI: 10.3847/1538-4357/aac6ec

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What mechanism produces the 872 um polarized dust emission in young protostellar disks (VLA 1623, L1527): magnetically aligned grains, self-scattering, or radiative-flux alignment?  
  > "To further understand the origin of the polarized disk emission, we have obtained high-resolution ($\sim 0.1\ensuremath{''}$), high-sensitivity ($\sigma \lesssim 0.2-0.5$ mJy) polarimetric observations of two young Class 0 systems" (Introduction)
- Target **VLA 1623**: coordinates VLA 1623B: 16:26:26.3066, -24:24:30.694 (J2000, Table 2)  
  > "VLA 1623, $d\sim 137$ pc, (cite: or17)" (Introduction); z/distance d ~ 137 pc  
  > "VLA 1623, $d\sim 137$ pc, (cite: or17)" (Introduction); distance from Ortiz-Leon et al. 2017  
  > "VLA 1623, $d\sim 137$ pc, (cite: or17)" (Introduction)
- Target **L1527**: coordinates 04:29:53.8753, +26.03.09.511 (J2000, Table 2)  
  > "L1527, $d\sim 145$ pc, (cite: lo07)" (Introduction); z/distance d ~ 145 pc  
  > "L1527, $d\sim 145$ pc, (cite: lo07)" (Introduction); distance from Loinard et al. 2007  
  > "L1527, $d\sim 145$ pc, (cite: lo07)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00084.S
- bands: Band 7 (872 um), LO 343.5 GHz  
  > "The ALMA observations were conducted at Band 7, with the local oscillator set to $\nu_{LO} = 343.5$ GHz" (2 Observations)
- frequencies and spectral setup: 4 spws of 2 GHz, 64 channels of 31.25 MHz each, full polarization  
  > "Each spectral window was divided into 64 channels of 31.25 MHz apiece, yielding a total bandwidth per spectral window of 2 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA 1623: C40-5; L1527: C40-6  
  > "Observations of VLA 1623 were conducted in the ALMA configuration C40-5 with baselines ranging from 14 meters to 1.45 km" (2 Observations)
- baselines: 14 m-1.45 km (VLA 1623); 21 m-3.14 km (L1527)  
  > "with baselines ranging from 21 m to 3.14 km" (2 Observations)
- angular resolution: ~0.12-0.2 arcsec  
  > "high-resolution ($\sim0.12\ensuremath{''}-0.2\ensuremath{''}$)" (abstract)
- max recoverable scale: ~2.3 arcsec (VLA 1623); ~1.4 arcsec (L1527)  
  > "an estimated maximum recoverable scale of $\sim 2.3\ensuremath{''}$" (2 Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 21 August 2016 (VLA 1623); 12 September 2016 (L1527)  
  > "were conducted on 21 August 2016 (for VLA 1623) and 12 September 2016 (for L1527)" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **ALMA Band 6 (Sadavoy et al. 2018)**: 1.3 mm polarization and continuum for comparison and spectral index  
  > "The polarization strength and morphology of the A and B sources are consistent with those found by (cite: sa18) at Band 6" (3 Results)
- External data: ALMA 1.3 mm continuum of VLA 1623 used for proper motion  
  > "By combining the data from ALMA 1.3 mm continuum observations from (cite: mu13) with ours" (4.2 Structure of the VLA 1623 System) [from Murillo et al. 2013 (cite: mu13)]
- External data: L1527 disk temperature profile from CO isotopologues  
  > "the radial temperature profile of the disk of L1527 has been estimated from observations of optically thick $^{13}$CO($J=2-1$) and C$^{18}$O($J=2-1$) emission" (4.1 Polarization of the disk emission) [from van 't Hoff et al. 2018 (cite: van18)]

## Processing

### Calibration

- pipeline or manual: Manual reduction by NRAO analysts  
  > "These observations were reduced manually by analysts at the National Radio Astronomy Observatory (NRAO), using the Common Astronomy Software Applications (CASA) package" (2 Observations)
- casa version: CASA 4.7.0  
  > "version 4.7.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (2.885 Jy, alpha -0.15) for VLA 1623; J0510+1800 (2.238 Jy at 343.425 GHz, alpha -0.2) for L1527  
  > "The assumed flux density for J0510+1800 at 343.425 GHz was 2.238 Jy with a spectral index of -0.2, while that for J1517-2422 was 2.885 Jy with a spectral index of -0.15." (2 Observations)
- flux scale uncertainty: 10%  
  > "The overall amplitude calibration uncertainty at Band 7 for ALMA is estimated at 10%." (2 Observations)
- self calibration: Phase-only, antenna-based, solint ~6 s  
  > "we performed a phase-only self-calibration on them, solving for the antenna-based phases every $\sim 6$ seconds" (2 Observations)

### Imaging

- task: clean with beammode='clarkStokes', all four Stokes  
  > "using the `clean` task with `beammode=‘clarkStokes’` to ensure optimal deconvolution in all four Stokes parameters" (2 Observations)
- deconvolver: multiscale clean  
  > "using the `multiscale` parameter to ensure that both large- and small-scale emission were properly deconvolved" (2 Observations)
- weighting robust: Natural (both); Briggs robust = -2 for VLA 1623  
  > "a Briggs-weighted image with robust = -2 (i.e., close to uniform weighting)" (2 Observations)
- uv taper: 100 klambda Gaussian taper for CB disk flux fit  
  > "we smoothed the residual data with a Gaussian taper of half-width $100$k$\lambda$, imaged it, and used `imfit` to fit the disk" (3 Results)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to VLA 1623 (~20%), not to L1527  
  > "Due to its proximity to the pointing center, no primary beam correction was applied to the L1527 images." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: L1527 0.23x0.14 (PA -3.9); VLA 1623 natural 0.20x0.17 (PA 57.1); Briggs 0.14x0.12 (PA 29.8)  
  > "| VLA 1623AB | Briggs    | 0.14   | 0.12   | 29.8      | 0.19  | 0.053 | 0.057 | 0.054 | 0.036 |" (Table 1)
- final rms: sigma_I 0.17-0.55 mJy/beam; sigma_QU ~0.03-0.08  
  > "| L1527      | natural   | 0.23   | 0.14   | -3.9      | 0.17  | 0.036 | 0.031 | 0.032 | 0.023 |" (Table 1)

### Inherited from earlier work

- Polarization-angle averaging and KS/AD tests against uniform distribution follow Cox et al. 2018  
  > "we follow (cite: co18) and compute the polarized-intensity weighted average" (3 Results) [from (cite: co18)]

### Not stated but needed to reproduce (our reading)

- multiscale scale values
- clean thresholds and masks
- self-calibration iterations and whether applied before polarization calibration
- cell and image sizes
- how Band 6 and Band 7 data were matched for the spectral index
- proper motion fitting method
- how minor axis PAs were derived for each source
- line-free handling not needed; continuum spw flagging not stated

## Analysis recipe

1. **Image Stokes I,Q,U,V**: clean in four Stokes with multiscale after phase-only self-cal; natural and Briggs weightings  
  > "The data were imaged in all four Stokes parameters in CASA 4.7.0 using the `clean` task" (2 Observations)
   - software: CASA
   - parameter: robust = -2 for high-resolution VLA 1623 image  
  > "a Briggs-weighted image with robust = -2" (2 Observations)
   - fitting: _not stated_
   - validation: Compared polarization morphology with Band 6 data of Sadavoy et al. 2018  
  > "the polarization morphology of VLA1623AB matches well that found at Band 6 by (cite: sa18)" (2 Observations)
2. **Make PI, PA and fraction maps**: immath: PI=sqrt(Q^2+U^2), debiased; masked below 5 sigma in PI and 3 sigma in I  
  > "Each of the PI, PA, and polarization fraction maps was masked below 5$\sigma$ in PI." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure source sizes and fluxes**: image-plane elliptical Gaussian fits deconvolved from beam, in I and PI; CB disk by subtracting Aa/Ab model from visibilities, tapering and fitting  
  > "These properties are determined from image-plane fitting of elliptical Gaussians to each of the objects in the VLA 1623 and L1527 maps" (3 Results)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
4. **Test polarization angle vs disk minor axis**: PI-weighted mean angle within 0.1 arcsec of PI peak; KS and Anderson-Darling tests vs uniform offsets  
  > "we compared the distribution of angular offsets $|\theta-\psi|$ to that of a uniform distribution of angular offsets using both the Kolmogorov-Smirnov and Anderson-Darling tests" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate optical depth and disk stability**: Brightness temperature from peak surface brightness compared with kinetic temperature; Toomre Q for the circumbinary disk from optically thin mass  
  > "The peak brightness temperatures associated with VLA 1623Aa, Ab, and B are $\sim$ 60-70 K, while that associated with L1527 is $\sim$ 45 K." (4.1 Polarization of the disk emission)
   - assumption: kappa = 10 (nu/1 THz)^beta cm2/g, beta=1, gas-to-dust 100, Td = 30 K, central mass 0.15 Msun  
  > "Assuming a gas-to-dust mass ratio of 100:1, we find that the total opacity is 0.034 cm$^2$/g. We assume $T_d = 30$ K" (4.3 Formation of the VLA 1623AabB System)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration, imaging (clean), immath, imfit  
  > "CASA (v4.7.0; (cite: mc07)), Matplotlib" (Software)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Matplotlib** : plotting  
  > "CASA (v4.7.0; (cite: mc07)), Matplotlib" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index of VLA 1623A and B | 2.30 | 0.45 | dimensionless | 5 | is approximately $\alpha \sim 2.30 \pm 0.45$ assuming a 10% absolute calibration uncertainty at each of the two bands |
| VLA 1623CBdisk flux density | ~1 | 1096 +/- 46 mJy (Table 2 fit) | Jy | 3 | We find that the material has a flux density of $\sim$ 1 Jy and an extent of roughly $2.2\ensuremath{''} \times 1.2\ensuremath{''}$. |
| Polarization angle offset probability from uniform | P <~ 2e-4 | not stated | dimensionless | 4 | $P \lesssim 2 \times 10^{-4}$ |
| Peak brightness temperature VLA 1623Aa,Ab,B / L1527 | 60-70 / 45 | not stated | K | 5 | $\sim$ 60-70 K, while that associated with L1527 is $\sim$ 45 K |
| Aa-Ab separation | 0.21 (~30 au) | not stated | arcsec | 3 | ($\rho = 0.21\ensuremath{''} \sim 30$ au) |
| Toomre Q of circumbinary disk at 85 au | ~1.8 | not stated | dimensionless | 5 | the value of the $Q$ parameter is $\sim$ 1.8 at a distance of 85 au |
| Circumbinary disk mass | ~0.03 | not stated | Msun | 5 | $M_d \sim 0.03$ M~$\odot$~ |
| Proper motion of VLA 1623W (RA, Dec) | -14.9, -23.4 | 7, 7 | mas/yr | 0 | $\mu_{\alpha}\cos \delta &=& -14.9 \pm 7 \textrm{ mas yr}^{-1}\\ |
| Polarization angle of L1527 minus minor axis | 6.5 | 0.8 | degrees | 4 | / L1527 / 98.3 $\pm$ 0.6 / 91.8 $\pm$ 0.6 / 6.5 $\pm$ 0.8 / |

## Qualitative findings

- Polarization angle in each compact source is uniform and nearly parallel to the disk minor axis.  
  > "The polarization angle of the emission is uniform across each protostellar source and nearly coincides with each disk’s minor axis." (abstract)
- VLA 1623A is resolved into a proto-binary inside a cavity of the circumbinary disk.  
  > "We spatially resolve VLA 1623A into two sources, VLA 1623Aa and VLA 1623Ab, separated by $\sim30$ au" (abstract)

## Claim tuples

- H: Is self-scattering responsible for disk-scale 872 um polarization? | E: Compare polarization angle vs minor axis, PI-I peak offsets, and brightness temperature across five sources | R: Angles aligned with minor axis; 20-40 mas offsets between PI and I peaks; tau >~ 1 | F: Self-scattering likely dominates polarization in these systems | **supported**
- H: Is grain alignment by radiative flux responsible? | E: Check polarization morphology in edge-on disks | R: Polarization is maximal near disk center and uniform | F: Evidence against radiative flux alignment | **supported**
- H: Is VLA 1623A a binary within a circumbinary disk? | E: Briggs robust=-2 imaging and Gaussian fitting | R: Two components separated by 0.21 arcsec within a cavity | F: Proto-binary inside a circumbinary Keplerian disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiative-flux alignment rejected; poloidal-field optically thick alignment remains plausible for VLA 1623Aa/Ab/B  
  > "though optically thick emission from grains aligned with a poloidal field is another plausible origin" (4.1 Polarization of the disk emission)
- How they decided it was enough: _not stated_
- Limitation (authors): VLA 1623 sources lie outside the inner 1/3 of the primary beam where polarimetry is considered reliable.  
  > "This places both sources outside the inner $\sim$ 1/3 of the primary beam full-width at half-max" (2 Observations)
- Limitation (authors): CB disk size may be a lower limit due to maximum recoverable scale.  
  > "We note that this size may be a lower limit, as the estimated maximum angular scale recoverable by these observations is $\sim 2.3\ensuremath{''}$." (3 Results)
- Caveat (inferred, ours): Off-axis polarization calibration relies on a private communication
- Caveat (inferred, ours): Only five compact sources, so statistical test is small-sample
- Caveat (inferred, ours): Optical depth inferred from brightness temperature with assumed kinetic temperatures
- Caveat (inferred, ours): No radiative transfer modeling of scattering vs alignment

## Reproducibility

- Data public (paper): Project code given; archival data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00084.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: multiscale scales, cell/image size, clean thresholds
- Missing: exact Band 6 data matching for spectral index and proper motion
- Missing: Minor axis PA derivation
- Data volume (inferred): ~50-100 GB raw for two executions
- Score (inferred): 3/5, Public data and a standard CASA recipe, but key clean parameters are missing.
- Rediscovery candidate: yes, Public data, recipe mostly specified, numeric results (fluxes, angles, offsets) available.

## Links

- Method: Cox et al. 2018 (cite: co18) (Polarization angle averaging and statistical tests)
- Companion: Sadavoy et al. 2018 (cite: sa18) (Band 6 polarization of VLA 1623)
- Related: VANDAM survey

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 47,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
