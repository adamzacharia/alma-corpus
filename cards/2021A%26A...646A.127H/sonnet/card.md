# Multiwavelength dissection of a massive heavily dust-obscured galaxy and its blue companion at z∼2

`2021A&A...646A.127H` | Astronomy and Astrophysics 2021 | first author: Hamed, M. | arXiv: 2101.07724 | DOI: 10.1051/0004-6361/202039577

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is the ultra-massive dusty galaxy Astarte quenching or has it always been on the main sequence, using SED modelling and its ALMA CO(3-2) gas mass?  
  > "probe the gas mass of Astarte with its ALMA CO emission, to investigate whether this ultra-massive galaxy is quenching or not, and whether it has always been on the MS of star-forming galaxies." (abstract)
- Target **Astarte (COSMOS2015 647980)**: coordinates _not stated_; z/distance z_CO = 2.154 (z_phot = 2.153)  
  > "z$_{phot} = 2.153$" (Table 1); "implying $z_{CO(3-2)} = 2.154$" (3.1.1 Line extraction); distance from ALMA CO(3-2) line; photometric z from COSMOS2015  
  > "z$_{phot} = 2.153$" (Table 1); "implying $z_{CO(3-2)} = 2.154$" (3.1.1 Line extraction)
- Target **Adonis (COSMOS2015 648299)**: coordinates _not stated_; z/distance z_spec = 2.140  
  > "z$_{spec} = 2.140$" (Table 1); distance from zCOSMOS spectroscopic redshift  
  > "z$_{spec} = 2.140$" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00914.S
- bands: Band 3 (2.7 mm)  
  > "Astarte was observed at 2.7 mm with ALMA (band 3)" (2.2 ALMA observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.78'' x 0.56''  
  > "The achieved synthesized beam size is $0.78\ensuremath{''} \times 0.56\ensuremath{''}$" (2.2 ALMA observation)
- max recoverable scale: _not stated_
- sensitivity: rms 0.47 mJy/beam km/s per channel; 3-sigma continuum limit 0.117 mJy  
  > "the rms is 0.47 mJy beam$^{-1}$ km s$^{-1}$ per channel" (2.2 ALMA observation); "measured a 3-$\sigma$ upper limit from the map of 0.117 mJy" (3.1.1 Line extraction)
- time on source: 45 minutes  
  > "with a time-on-source of 45 minutes using 32 antennas" (2.2 ALMA observation)
- observing dates: 5 September 2015, cycle 2  
  > "on September the $5^{th}$ of 2015, cycle-2 (P.I. M.Béthermin)" (2.2 ALMA observation)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Other facility **Herschel PACS/SPIRE, Spitzer IRAC/MIPS, Subaru, CFHT, VISTA, HST, VLA 3 GHz**: UV to radio photometry for SED fitting  
  > "Table 1 presents a summary of the available photometric data from different instruments of the two galaxies." (2.1 NUV-IR observations)
- External data: COSMOS2015 catalog photometry and photometric redshift  
  > "with original COSMOS2015 catalog (cite: laigle16) IDs: 647980 and 648299" (1 Introduction) [from (cite: laigle16)]
- External data: VLA 3 GHz radio continuum  
  > "The radio continuum of Astarte is tentatively detected with the Karl G. Jansky Very Large Array (VLA) in the S band at $\nu=$3 GHz (cite: Smolcic2017)." (2.1 NUV-IR observations) [from (cite: Smolcic2017)]
- External data: CO excitation ratio r31=0.42±0.07 (lowest 0.27±0.07)  
  > "We use $r_{31}=0.42\pm0.07$, which is the average ratio found for $z=1.5$ SFGs by (cite: Daddi2015)." (3.1.3 Deriving the molecular gas mass) [from (cite: Daddi2015)]
- External data: zCOSMOS spectroscopic redshift 2.140  
  > "found z$_{spec}=2.140$" (2 Observations) [from (cite: Lilly2009)]

## Processing

### Calibration

- pipeline or manual: CASA used for flagging and reduction of visibilities  
  > "We use the Common Astronomy Software Applications package and pipeline (CASA) v5.4" (2.2 ALMA observation)
- casa version: CASA v5.4  
  > "(CASA) v5.4" (2.2 ALMA observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "The deconvolution was performed with the CLEAN algorithm using natural weighting for an optimal S/N." (2.2 ALMA observation)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting for an optimal S/N" (2.2 ALMA observation)
- uv taper: _not stated_
- cell size: 0.1''  
  > "the cell size was set to $0.1\ensuremath{''}$" (2.2 ALMA observation)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: not needed; no significant continuum  
  > "showed a non-significant continuum emission of the spectrum therefore its subtraction was not needed" (2.2 ALMA observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.78'' x 0.56''  
  > "The achieved synthesized beam size is $0.78\ensuremath{''} \times 0.56\ensuremath{''}$" (2.2 ALMA observation)
- final rms: _not stated_

### Inherited from earlier work

- Star formation history parametrisation  
  > "We use the SFH proposed by (cite: Ciesla17)" (3.2.2 Stellar component) [from (cite: Ciesla17)]
- Decoupling of stellar continuum from IR emission  
  > "we follow the method used in (cite: buat2019) by dissecting the stellar continuum and the IR emission apart" (3.2.5 SED fitting results) [from (cite: buat2019)]
- Dynamical mass method  
  > "we use the method described in (cite: Bothwell13) to estimate the dynamical mass of Astarte" (3.1.4 Dynamical mass) [from (cite: Bothwell13)]

### Not stated but needed to reproduce (our reading)

- Which spectral window and channels used for the line and for the continuum map
- Disk radius R used for the dynamical mass (CO size ~74 kpc seems inconsistent)
- CIGALE version and exact module set/priors
- Channel range summed for the moment-0 map
- Self-calibration and flux calibrator not stated

## Analysis recipe

1. **Image ALMA band 3 cube**: CASA reduction, CLEAN with natural weighting, 0.1'' cells, no continuum subtraction  
  > "The deconvolution was performed with the CLEAN algorithm using natural weighting for an optimal S/N." (2.2 ALMA observation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract CO(3-2) line and flux**: Gaussian fit to spectrum; moment-0 map with 2D Gaussian fit used for adopted flux  
  > "The emission line was extracted by fitting a Gaussian over the profile." (3.1.1 Line extraction); "Hereafter, we use the flux from the moment-0 map, which takes this account." (3.1.2 Line integrated flux and luminosity)
   - fitting: Gaussian fit to line profile  
  > "The goodness of the Gaussian fit was verified with a $\chi^2$ test" (3.1.1 Line extraction)
   - validation: chi2 test; compared spectrum and moment-0 fluxes (1.2 sigma difference)  
  > "There is 1.2 $\sigma$ significant difference between the intensities derived by each methods." (3.1.2 Line integrated flux and luminosity)
3. **Derive line luminosity and H2 mass**: Solomon 1997 L' formula; r31 to CO(1-0); M_H2 = alpha_CO L'  
  > "$$M_{H_2} = \alpha_{CO}\ L^{\prime}_{CO(1-0)}$$" (3.1.3 Deriving the molecular gas mass)
   - assumption: r31=0.42±0.07 (or 0.27±0.07); alpha_CO=0.8 or 4.36  
  > "we use two conversion factors: $\alpha_{CO}=0.8$ and a galactic conversion factor of $\alpha_{CO}=4.36$." (3.1.3 Deriving the molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dynamical mass**: M_dyn = 4e4 dV^2 R / sin^2 i for rotating disk, i=57.3 deg  
  > "For a random inclination of $\langle i \rangle = 57.3^{\circ}$ (cite: Law2009)" (3.1.4 Dynamical mass)
   - assumption: rotating disk origin of line  
  > "Assuming that a rotating disk is the origin of the detected line" (3.1.4 Dynamical mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **SED fitting for SFR, M*, Ldust**: CIGALE with BC03, Ciesla17 SFH, Draine&Li 2014 dust, synchrotron, three attenuation laws (C00, CF00, LF17); model choice by BIC  
  > "We use the SED modeling code CIGALE (cite: Boquien19) to derive the physical properties of our sources." (3.2.1 The SED modeling)
   - software: CIGALE
   - assumption: Chabrier IMF, solar-like metallicity (Z=0.02)  
  > "Metallicity" (Table 3)
   - fitting: CIGALE grid with Bayesian analysis; model comparison by BIC  
  > "we employ the Bayesian information criterion (BIC), defined as the $\chi^2 + k\ln{n}$" (3.2.3 Attenuation laws)
   - validation: chi2, reduced chi2 and BIC compared among laws; stellar-only vs IR-only fits  
  > "Comparison between the quality of fits of Astarte and Adonis produced with CIGALE with the three attenuation laws." (Table 3)

## Software

- **CASA** 5.4: flagging, reduction and imaging  
  > "for flagging and to reduce the visibility data" (2.2 ALMA observation)
- **CIGALE** : SED fitting  
  > "We use the SED modeling code CIGALE" (3.2.1 The SED modeling)
- **LePhare** : initial SFR and mass estimates  
  > "as estimated initially using LePhare" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) FWHM | 152.74 | 33.21 | km/s | 2 | 152.74$\pm$33.21 km s$^{-1}$ |
| I_CO(3-2) moment-0 | 0.328 | 0.047 | Jy km/s | 2 | $0.328\pm0.047$ |
| L'_CO(3-2) | 8.508e9 | 1.219e9 | K km/s pc^2 | 3 | $8.508\pm1.219$ |
| M_H2 (alpha=0.8) | 1.62e10 | 0.47e10 | Msun | 3 | $$M_{H_2 (\alpha=0.8)} = (1.62\pm0.47) \times 10^{10}\ M_{\odot}.$$ |
| M_H2 (alpha=4.36) | 8.85e10 | 2.57e10 | Msun | 3 | $M_{H_2} = (8.85\pm2.57)\times 10^{10}\ M_{\odot}$ |
| Astarte SFR | 395 | 20 | Msun/yr | 5 | $395\pm20$ |
| Astarte stellar mass | 3.74e11 | 0.19e11 | Msun | 5 | $(3.74\pm0.19)\times10^{11}$ |
| Astarte depletion time | 0.22 | 0.07 | Gyr | 5 | a rather small depletion time of $0.22\pm0.07$ Gyrs |
| M_dyn | 1.11e11 | 0.23e11 | Msun | 4 | (1.11 $\pm$0.23) $\times 10^{11}\,$M$_{\odot}$ |

## Qualitative findings

- Astarte is a MS galaxy and Adonis a strong starburst (~10x MS)  
  > "Adonis lies on 10$\times$MS qualifying it to be a strong starburst" (4 Discussion)

## Claim tuples

- H: Astarte is quenching after a starburst | E: SED fitting plus ALMA CO(3-2) gas mass | R: Low gas fraction and short depletion time 0.22±0.07 Gyr on the MS | F: Astarte may be quenching through the MS following a starburst | **partially**
- H: Derived stellar mass depends on attenuation law | E: Fit with C00, CF00, LF17 | R: SFR similar; M* ~1e11 (C00) vs ~4e11 (shallow law) | F: Stellar mass is sensitive to the attenuation law | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Super-deblended JCMT 850 um fluxes not used due to high uncertainties  
  > "We refrain from using these super-deblended fluxes due to the high uncertainties" (2.1 NUV-IR observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot exclude a faint diffuse larger-scale CO component given data depth  
  > "we cannot formally exclude another faint and diffuse component at larger scale considering the depth of our data" (3.1.2 Line integrated flux and luminosity)
- Caveat (inferred, ours): CO detected at only S/N~5 in the brightest channel
- Caveat (inferred, ours): Gas mass depends strongly on assumed alpha_CO and r31
- Caveat (inferred, ours): Single-line, low-resolution data; the 74 kpc CO size seems implausible
- Caveat (inferred, ours): Conclusion on quenching is speculative

## Reproducibility

- Data public (paper): ALMA project 2013.1.00914.S acknowledged  
  > "ADS/JAO.ALMA#2013.1.00914.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Spectral window and channel selection
- Missing: CIGALE version and full priors
- Missing: Disk radius used for M_dyn
- Data volume (inferred): ~5-20 GB raw for one Cycle-2 band 3 execution
- Score (inferred): 3/5, Public data and moderate recipe, but some imaging and fitting details missing.
- Rediscovery candidate: yes, Public archival data with numeric CO flux and luminosity results from a simple recipe.

## Links

- Method: (cite: Boquien19) (CIGALE)
- Method: (cite: Ciesla17) (SFH model)
- Companion: (cite: buat2019) (stellar vs IR decoupling method)
- Related: COSMOS
- Related: PEP survey
- Related: zCOSMOS

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
