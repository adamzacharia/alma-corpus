# Spitzer Catalog of Herschel-selected Ultrared Dusty Star-forming Galaxies

`2019ApJS..244...30M` | The Astrophysical Journal Supplement Series 2019 | first author: Ma, Jingzhe | arXiv: 1908.08043 | DOI: 10.3847/1538-4365/ab4194

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the stellar, dust and star-formation properties of Herschel-selected ultrared DSFGs (from Spitzer/IRAC plus multiwavelength SED fitting), and can they account for the progenitors of massive quiescent galaxies at z~3?  
  > "we conclude that our ultrared sample cannot account for the majority of the star-forming progenitors of the massive, quiescent galaxies found in infrared surveys." (abstract)
- Target **300 Herschel ultrared DSFGs from H-ATLAS and HeLMS (63 with high-resolution data)**: coordinates _not stated_; z/distance median z = 3.3 (magphys photo-z, unlensed sample)  
  > "These include all the H-ATLAS sources in (cite: Ivison2016) and additional 31 sources from Ivison et al. in prep., and 161 HeLMS sources (with a flux density cut $S_{500}$ $>$ 64 mJy) from (cite: Asboth2016)." (Figure 1 caption); distance from magphys+photo-z SED fitting; spectroscopic redshifts where available  
  > "These include all the H-ATLAS sources in (cite: Ivison2016) and additional 31 sources from Ivison et al. in prep., and 161 HeLMS sources (with a flux density cut $S_{500}$ $>$ 64 mJy) from (cite: Asboth2016)." (Figure 1 caption)

## Data provenance

- ALMA projects: 2013.1.00001.S, 2016.1.00139.S, 2013.1.00499.S
- bands: ALMA 870 um continuum (Oteo2017); ALMA 3 mm (Fudamoto2017)  
  > "presented the high-resolution ($\sim$ 0.12$\ensuremath{''}$) ALMA continuum imaging at 870 $\ensuremath{\mu}m$" (2.4.1 Continuum data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.12'' (870 um); 0.6-1.2'' (3 mm ALMA)  
  > "The synthesized FWHM beam sizes are 1-1.5$\ensuremath{''}$ for NOEMA and 0.6-1.2$\ensuremath{''}$ for ALMA." (2.4.1 Continuum data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PIs R.J. Ivison (870 um) and A. Conley (3 mm)  
  > "(PI: R.J. Ivison; PIDs: 2013.1.00001.S, 2016.1.00139.S)" (2.4.1 Continuum data)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 um imaging of 300 sources (PID 13042)  
  > "A total of 300 *Herschel* ultrared sources were followed up by the *Spitzer* snapshot imaging program PID 13042 (PI: A. Cooray) using IRAC" (2.2 Spitzer observations)
- Other facility **Herschel/SPIRE**: 250/350/500 um photometry and selection  
  > "The *Herschel*/SPIRE photometry of these sources at 250, 350, and 500 $\ensuremath{\mu}m$ are shown in Table" (2.1)
- Other facility **SCUBA-2/LABOCA**: 850/870 um photometry  
  > "A total of 261 out of the 300 *Spitzer* follow-up sources have SCUBA-2/LABOCA data" (2.3)
- Other facility **NOEMA and SMA**: high-resolution positions and mm photometry  
  > "Five HeLMS ultrared sources (HELMS_RED_1, 2, 4, 10, 13) were observed with SMA at 1.1 mm in the compact array configuration" (2.4.1 Continuum data)
- External data: ALMA 870 um fluxes, sizes and lensing classification  
  > "23 of them are gravitationally lensed sources with clear lensing signatures like rings or arcs as shown in (cite: Oteo2017)" (3) [from (cite: Oteo2017)]
- External data: FIR photometric redshifts and SCUBA-2/LABOCA fluxes  
  > "We adopt the peak-value photometry and photometric redshifts from both works" (2.3) [from (cite: Ivison2016); (cite: Duivenvoorden2018)]
- External data: ALESS comparison magphys results  
  > "The average (mean) SED of the ALESS DSFGs from (cite: daCunha2015) is also overlaid for comparison." (4.4) [from (cite: daCunha2015)]

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

- ALMA/NOEMA 3 mm data and spectral scans  
  > "at 3 mm as described in detail in (cite: Fudamoto2017)" (2.4.1 Continuum data) [from (cite: Fudamoto2017)]
- Same magphys SED code for comparison with ALESS  
  > "we use the same SED code, i.e., the updated version of magphys as in (cite: daCunha2015) and (cite: Danielson2017)" (4 SED fitting) [from (cite: daCunha2015); (cite: Danielson2017)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details are not given (inherited from Oteo2017)
- magphys prior and parameter grid details and run settings
- Procedure for lensed/unlensed classification beyond morphology
- Photometric uncertainty treatment and upper-limit handling in magphys
- XID+ prior settings

## Analysis recipe

1. **IRAC photometry**: SExtractor in dual-image mode on co-added 3.6+4.5 um detection image, MAG_AUTO  
  > "We use SExtractor (version 2.8.6; (cite: Bertin1996)) in dual-image mode to perform source detection and photometry." (2.2)
   - software: SExtractor, MOPEX
   - fitting: _not stated_
   - validation: astrometry compared to 2MASS  
  > "we compared the positions of bright IRAC sources with their 2MASS counterparts" (2.2)
2. **Deblend SPIRE fluxes of multiple components**: XID+ with interferometric positional priors  
  > "We use the probabilistic de-blender XID+ (cite: Hurley2017)" (3)
   - software: XID+
   - assumption: SCUBA-2/LABOCA flux split by ALMA 870 um ratios  
  > "The SCUBA-2 or LABOCA flux densities are split among sub-components assuming the same relative ratios" (3)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fitting of unlensed sample**: magphys+photo-z with redshift free; fixed-z version for single-component subsample; medians and 16-84th percentiles from posteriors  
  > "We take the median value as the best-fit parameter and the 16th or 84th percentile range as the $1\sigma$ uncertainty." (4 SED fitting)
   - software: magphys
   - assumption: Chabrier IMF; Lambda-CDM H0=70, Om=0.3  
  > "We use a (cite: Chabrier2003) initial mass function (IMF) and AB system magnitudes." (1)
   - fitting: _not stated_
   - validation: photo-z compared to 5 spec-z and FIR photo-z  
  > "We compare the photometric redshifts from magphys+photo-$z$ and FIR SED fitting with spectroscopic redshifts based on the 5 sources" (4.1)

## Software

- **magphys** : SED fitting  
  > "we use the same SED code, i.e., the updated version of magphys" (4)
- **SExtractor** 2.8.6: IRAC photometry  
  > "We use SExtractor (version 2.8.6; (cite: Bertin1996))" (2.2)
- **MOPEX** 18.5.0: IRAC mosaics  
  > "MOPEX (version 18.5.0; (cite: Makovoz2006))" (2.2)
- **XID+** : SPIRE deblending  
  > "We use the probabilistic de-blender XID+ (cite: Hurley2017)" (3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median stellar mass, unlensed ultrared | 3.7e11 | 0.2e11 | Msun | 3 | a median stellar mass of (3.7 $\pm$ 0.2) $\times$ 10$^{11}$ $M_{\odot}$ and a median SFR of 730 $\pm$ 30 $M_{\odot}$yr$^{-1}$ |
| Median SFR | 730 | 30 | Msun/yr | 3 | a median SFR of 730 $\pm$ 30 $M_{\odot}$yr$^{-1}$ |
| Median dust luminosity | 9.0e12 | 2.0e12 | Lsun | 3 | a median total dust luminosity of (9.0 $\pm$ 2.0) $\times$ 10$^{12}$ $L_{\odot}$ |
| Median dust mass | 2.8e9 | 0.6e9 | Msun | 3 | a dust mass of (2.8 $\pm$ 0.6) $\times$ 10$^9$ $M_{\odot}$ |
| Median photometric redshift (magphys) | 3.3 | +1.6/-1.0 (16-84%) | dimensionless | 3 | 3.3$^{+1.6}_{-1.0}$ |
| Unlensed fraction | 65% (41 of 63) | not stated | percent | 0 | 65% of the ultrared sources (41 out of 63) do not have clear signatures of lensing |
| Multiplicity rate | 27% (17 of 63) | not stated | percent | 0 | $\sim$ 27% (17 out of 63) *Herschel* ultrared sources are resolved into multiple components |

## Qualitative findings

- Ultrared DSFGs are more massive, more star-forming and dustier than ALESS DSFGs and lie on the high-mass end of the main sequence.  
  > "Nevertheless, they are all consistent with and at the high-mass end of the star-forming MS by (cite: Speagle2014)." (4.2)

## Claim tuples

- H: Ultrared DSFGs are the main star-forming progenitors of massive quiescent z~3 galaxies | E: Compare space density, SFRD and stellar mass density with ZFOURGE quiescent galaxies | R: SMD at z~5 about 2 orders of magnitude lower; max contribution to total SMD 1.7% | F: The ultrared sample cannot account for the majority of the progenitors | **supported**
- H: Ultrared DSFGs differ from z~2 DSFGs | E: magphys on unlensed sample versus ALESS | R: Higher M*, SFR, Ldust, Mdust and Av | F: Ultrared sample is more extreme | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Tdust is essentially prior-driven and not constrained by the data.  
  > "This narrow range is almost entirely driven by the prior distribution as shown in Figure 2, i.e., $T_{\rm dust}$ is basically not constrained by the data." (4.3)
- Caveat (inferred, ours): ALMA used only for positions and lensing classification; the SED results depend on SCUBA-2 fluxes, which are inconsistent with ALMA
- Caveat (inferred, ours): Small unlensed sample and lens-missing possibility bias fractions
- Caveat (inferred, ours): Photo-z validated on only 5 spec-z

## Reproducibility

- Data public (paper): Spitzer PID 13042 and ALMA data listed with project codes; catalog is provided  
  > "We have provided a catalog of all the cross-matched sources" (6)
- Products in archive: _not stated_
- Missing: magphys configuration
- Missing: ALMA reduction details
- Missing: SMD completeness and duty-cycle correction details
- Data volume (inferred): small for photometric catalog analysis (<~10 GB); ALMA reprocessing is unnecessary
- Score (inferred): 4/5, ALMA is auxiliary; the catalog and SED recipe are published but the settings are sparse.
- Rediscovery candidate: no, The main results rely on Spitzer, Herschel and SCUBA-2 photometry and a magphys setup that is not fully specified; ALMA plays a minor role.

## Links

- Method: (cite: Oteo2017) (ALMA 870 um data and lensing classification)
- Method: (cite: Battisti2019) (magphys+photo-z)
- Method: (cite: Fudamoto2017) (3 mm data and redshifts)
- Companion: (cite: Ivison2016) (H-ATLAS ultrared selection)
- Companion: (cite: Duivenvoorden2018) (HeLMS SCUBA-2 data)
- Related: H-ATLAS
- Related: HerMES/HeLMS
- Related: ALESS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00499.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
