# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies

`2020ApJ...901...79A` | The Astrophysical Journal 2020 | first author: Aravena, Manuel | arXiv: 2006.04284 | DOI: 10.3847/1538-4357/ab99a2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the physical properties (stellar mass, SFR, redshift, main-sequence offset, gas content) of the faint dusty galaxies detected in the ASPECS 1.2 mm map, and how do they relate to scaling relations and the cosmic molecular gas budget?  
  > "we present the physical properties of the faint dusty sources detected in the sensitive ASPECS 1.2 mm continuum map using the wealth of ancillary multiwavelength data available in the HUDF." (Introduction)
- Target **Hubble Ultra Deep Field / XDF (ASPECS LP field)**: coordinates _not stated_; z/distance sources at 0.5<z<5; median z=1.85  
  > "extending the covered area of the HUDF to 4.6 arcmin$^2$, roughly comprising the Hubble eXtremely Deep Field (XDF)" (Introduction); distance from spectroscopic redshifts (MUSE, ASPECS CO, 3D-HST) and photometric redshifts from 3D-HST  
  > "extending the covered area of the HUDF to 4.6 arcmin$^2$, roughly comprising the Hubble eXtremely Deep Field (XDF)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.2 mm continuum); Band 3 results from earlier papers  
  > "ALMA band 6 observations were obtained during Cycles 4 and 5 under excellent to good weather conditions" (ALMA observations)
- frequencies and spectral setup: eight frequency tunings covering 212.0-272.0 GHz, no gaps  
  > "Band 6 was scanned using eight frequency tunings, covering 212.0-272.0 GHz with no overlap or gaps between individual spectral windows." (ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1 and C43-2; 85-point mosaic  
  > "The observations were performed using the C43-1 and C43-2 arrays" (ALMA observations)
- baselines: _not stated_
- angular resolution: 1.53'' x 1.08'' at 242 GHz (natural); 2.37'' x 2.05'' (tapered)  
  > "leading to an angular resolution of $1.53''\times 1.08''$ at the center of the band 6 scan (242 GHz)" (ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 9.3 uJy/beam (natural); 11.3 uJy/beam (tapered)  
  > "This yielded an image reaching down to a noise level of 9.3$\mu$Jy beam$^{-1}$." (ALMA observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (ACS/WFC3, HUDF09/HUDF12/CANDELS)**: optical/NIR photometry and counterparts  
  > "the ASPECS LP field benefits from the deepest observations obtained with the Hubble Space Telescope (HST) Advanced Camera for Surveys (ACS) and Wide Field Camera 3 (WFC3)" (Ancillary data)
- Other facility **VLT/MUSE**: spectroscopic redshifts  
  > "The MUSE spectroscopic survey provides spectroscopic redshifts for optically faint galaxies" (Ancillary data)
- Other facility **Spitzer and Herschel**: IRAC/MIPS and PACS/SPIRE photometry  
  > "This includes Spitzer Infrared Array Camera (IRAC) and Multiband Imaging Photometer (MIPS) imaging, as well as by the Herschel PACS and SPIRE photometry" (Ancillary data)
- External data: 1.2 mm source catalog, fidelity and completeness  
  > "Details about the 1mm continuum source extraction, fidelity, and completeness analysis, as well as source catalog are described in (cite: gonzalezlopez20)." (Main sample) [from (cite: gonzalezlopez20)]
- External data: CO line ratios r21, r31, r41  
  > "for galaxies at $z=1.0-1.6$, we use $r_{21}=0.83\pm0.12$, $r_{31}=0.58\pm0.10$ and $r_{41}=0.30\pm0.08$" (Comparison of the various molecular gas mass estimates) [from (cite: boogaard20)]
- External data: PHIBSS1/2 compilation for comparison  
  > "These provide stellar masses, SFRs, and molecular gas masses (from dust and CO observations) for a large sample of 1444 massive star-forming galaxies from $z=0$ to 4" (ISM properties) [from (cite: tacconi13; tacconi18; freundlich19; liu19)]
- External data: Master photometric/spectroscopic catalog (>30 bands, ~7000 galaxies)  
  > "we created a master photometric and spectroscopic catalog of the XDF region as detailed in (cite: decarli19)" (Ancillary data) [from (cite: decarli19)]

## Processing

### Calibration

- pipeline or manual: standard observatory procedures  
  > "Calibration was performed via standard observatory procedures with passband and phase calibration determined from nearby quasars" (ALMA observations)
- casa version: CASA v5.1.1 (calibration) and v5.4.0-70 (imaging)  
  > "Calibration and imaging were done using the Common Astronomy Software Application package (CASA) versions v5.1.1 and v5.4.0-70, respectively." (ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: within ±10%  
  > "should be accurate within $\pm10\%$" (ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, mosaic mode  
  > "inverted the visibilities using the CASA task TCLEAN using natural weighting and mosaic mode" (ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "inverted the visibilities using the CASA task TCLEAN using natural weighting and mosaic mode" (ALMA observations)
- uv taper: tapered map with 2.37''x2.05'' resolution  
  > "A second version of the 1.2 mm map was obtained by tapering the visibilities" (ALMA observations)
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
- final rms: 9.3 uJy/beam natural; 11.3 uJy/beam tapered  
  > "with a noise level of 11.3$\mu$Jy beam$^{-1}$" (ALMA observations)

### Inherited from earlier work

- Survey setup, data reduction, source extraction, fidelity, prior-based selection  
  > "The ASPECS LP survey setup and data reduction steps are described in (cite: gonzalezlopez20), (cite: walter16) and (cite: aravena16b)." (ALMA observations) [from (cite: gonzalezlopez20); (cite: walter16); (cite: aravena16b)]
- Gas-to-dust ratio 200 for consistency with ASPECS series  
  > "For consistency with previous studies in the ASPECS series (cite: aravena16b; aravena19; boogaard19; decarli19), we fix $\delta_{\rm GDR}=200$" (ISM molecular gas masses) [from (cite: aravena16b; aravena19; boogaard19; decarli19)]
- Molecular gas budget approach  
  > "We here follow the same approach introduced in (cite: aravena19) and compute the fraction of $\rho_{\rm H2}$ contributed by galaxies within, above and below the MS" (Molecular gas budget) [from (cite: aravena19)]
- MS prescription  
  > "using a prescription for its location as a function of redshift and stellar mass from (cite: schreiber15)" (Location in stellar mass vs. SFR plane) [from (cite: schreiber15)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, cell size, image size and masking for the continuum map
- ALMA execution blocks and calibrators
- Exact photometry catalog inputs and MAGPHYS priors/library settings
- Exact rho_H2 values used from Decarli19 per redshift bin
- Observing dates and times on source

## Analysis recipe

1. **Make 1.2 mm continuum maps**: Collapse frequency axis in uv-plane, tclean natural weighting mosaic, plus tapered version  
  > "we collapsed along the frequency axis in the uv-plane and inverted the visibilities using the CASA task TCLEAN using natural weighting and mosaic mode" (ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources and compute fidelity**: LineSeeker on pixels with S/N>2 grouped with DBSCAN; fidelity f=1-Nneg/Npos  
  > "Source extraction was performed simultaneously in the natural and tapered weighted images, using the LineSeeker code by searching for all pixels with signal-to-noise ratio (S/N) $>2$" (Main sample)
   - software: LineSeeker, DBSCAN
   - parameter: fidelity >0.5 for main sample; 50% fidelity at S/N=4.3  
  > "For reference, a fidelity of 50% is achieved at S/N$=4.3$." (Main sample)
   - fitting: _not stated_
   - validation: negative-detection counts used for fidelity  
  > "The fidelity $f$ for each of the extracted sources was computed based on the number of positive ($N_{\rm pos}$) and negative ($N_{\rm neg}$) detections at a given S/N value, with $f=1-N_{\rm neg}/N_{\rm pos}$." (Results, Main sample)
3. **Match optical/IR counterparts and build prior-based sample**: Match within 1'' of HST sources with chance probability P<5%; prior sample to fidelity 50% using F160W<27 optical or Herschel priors  
  > "We identified these optical counterparts within a $1''$ radius from the 1.2 mm position (cite: gonzalezlopez20) with an additional requirement that the probability of chance association $P=1-\mathrm{exp}(-n d^2)$, is less than 5%." (Optical)
   - fitting: _not stated_
   - validation: expected spurious matches: 1-2 (main), ~1 (prior)  
  > "Based on this, we expect one to two sources to be a spurious association." (Optical)
4. **SED fitting for stellar mass, SFR, dust mass, LIR**: MAGPHYS high-z extension with 26 filters plus ALMA 1.2/3 mm and Herschel PACS for detections  
  > "we fit their SED using the high-redshift extension of MAGPHYS (cite: dacunha08; dacunha15)" (SED fitting and derivation of properties)
   - software: MAGPHYS
   - parameter: 0.1 dex added in quadrature to MAGPHYS uncertainties  
  > "we have added in quadrature a 0.1 dex uncertainty to all the MAGPHYS parameters derived." (SED fitting and derivation of properties)
   - assumption: two-component graybody, emissivity indices 1.5 (warm) and 2.0 (cold)  
  > "MAGPHYS assumes a two-component graybody approximation, with dust emissivity indexes of 1.5 and 2.0 for the warm and cold components, respectively." (SED fitting and derivation of properties)
   - fitting: MAGPHYS template library fitting  
  > "For all galaxies in the HUDF, we fit their SED using the high-redshift extension of MAGPHYS (cite: dacunha08; dacunha15)." (Results, SED fitting and derivation of properties)
   - validation: compared with PROSPECTOR (0.1-0.2 dex) and EAGLE tests  
  > "we find that these parameters are precise to within $\sim$0.1-0.2 dex in the stellar-mass range explored in this study." (SED fitting and derivation of properties)
5. **Offset from the main sequence**: Delta_MS = log(sSFR/sSFR_MS(z,M*)); within ±0.4 dex = MS  
  > "We define the boundaries of the main sequence to be within $\pm0.4$ dex from the prescription curves given by (cite: schreiber15)." (Location in stellar mass vs. SFR plane)
   - assumption: Schreiber+15 MS; Speagle+14 gives consistent results  
  > "we first used the (different) MS prescription from (cite: speagle14), and found consistent results" (Footnote)
   - fitting: _not stated_
   - validation: alternative MS prescription  
  > "we first used the (different) MS prescription from (cite: speagle14), and found consistent results when compared to those obtained with the adopted MS prescription" (Footnote 1)
6. **Molecular gas masses**: M_mol,SED = delta_GDR * M_d; compared with RJ-continuum and CO-based estimates  
  > "we used this $M_{\rm d}$ estimate along with an assumption of the molecular gas-to-dust ratio ($\delta_{\rm GDR}$) to compute the molecular gas mass as $M_{\rm mol, SED}=\delta_{\rm GDR} M_{\rm d}$." (ISM molecular gas masses)
   - software: MAGPHYS
   - assumption: delta_GDR=200; alpha_CO=3.6 for CO; RJ method T_d=25 K, beta=1.8, alpha_CO=6.5  
  > "it is assumed to be fixed at $T_{\rm d}=25$ K" (Comparison of the various molecular gas mass estimates)
   - fitting: _not stated_
   - validation: three estimators and metallicity-dependent prescriptions agree within uncertainties  
  > "we find that there is overall good agreement between the various methods to compute the molecular gas masses, supporting our choice for the MAGPHYS SED method." (Comparison)
7. **Scaling relations and gas budget**: Compute t_dep, mu_mol vs Delta_MS and z; sum gas masses per MS class in three z bins and divide by rho_H2(z) x Volume from ASPECS  
  > "added up the derived dust-based, molecular gas masses for all galaxies in each redshift bin and galaxy type." (Molecular gas budget)
   - parameter: z bins 0.4-1.0, 1.0-2.0, 2.0-3.0  
  > "three redshift bins $z=0.4-1.0, 1.0-2.0$ and $2.0-3.0$" (Molecular gas budget)
   - fitting: _not stated_
   - validation: uncertainties: quadrature sum of gas mass errors and binomial statistics  
  > "the statistical uncertainty, which follows a binomial distribution" (Molecular gas budget)

## Software

- **CASA** v5.1.1 (calibration), v5.4.0-70 (imaging): calibration and imaging  
  > "Calibration and imaging were done using the Common Astronomy Software Application package (CASA) versions v5.1.1 and v5.4.0-70, respectively." (ALMA observations)
- **LineSeeker** : source extraction in continuum maps  
  > "using the LineSeeker code by searching for all pixels with signal-to-noise ratio (S/N) $>2$" (Main sample)
- **DBSCAN** : grouping pixels into sources  
  > "grouping them into single sources using the DBSCAN algorithm" (Main sample)
- **MAGPHYS** high-redshift extension: SED fitting  
  > "we fit their SED using the high-redshift extension of MAGPHYS (cite: dacunha08; dacunha15)" (SED fitting and derivation of properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2 mm map rms | 9.3 | not stated | uJy/beam | 1 | The ASPECS 1.2 mm continuum map yields an unprecedented rms level of $9.3\mu$Jy beam$^{-1}$ |
| Median stellar mass (main sample) | 4.8e10 | IQR (2.4-11.7)e10 | Msun | 4 | we find a median stellar mass of $4.8\times10^{10} M_\ensuremath{\odot}$, with an interquartile range of $(2.4-11.7)\times10^{10}\ M_\ensuremath{\odot}$ |
| Median SFR (main sample) | 33 (text); 30 (abstract) | IQR 19-51 | Msun/yr | 4 | a median SFR of $33\ M_\ensuremath{\odot}$ yr$^{-1}$, with an interquartile range of $19-51\ M_\ensuremath{\odot}$ yr$^{-1}$ |
| Median redshift (main sample) | 1.85 | IQR 1.10-2.57 | dimensionless | 3 | the main sample of ASPECS 1.2 mm continuum galaxies has a median redshift of 1.85 with an interquartile range of $1.10-2.57$ |
| Median redshift (secondary sample) | 1.10 | IQR 0.77-1.72 | dimensionless | 3 | yielding a median redshift of 1.10 and an interquartile range of $0.77-1.72$ |
| Fraction within MS (main) | 59% | ±13% | percent | 5 | $59\%\pm13\%$ (19 out of the 32) of galaxies from the main sample lie within $\pm0.4$ dex from the MS |
| Fraction above / below MS (main) | 6% / 34% | ±4% / ±9% | percent | 5 | $6\%\pm4\%$ (2 out of 32) and $34\%\pm9\%$ (11 out of 32) of the ASPECS 1.2 mm galaxies are located above and below the MS |
| Median Delta_MS (main sample) | -0.30 | IQR width 0.51 dex | dex | 5 | show $\Delta_{\rm MS}$ median and interquartile range width values of -0.30 and 0.51 dex |
| Typical depletion timescale z=1-3 | 0.7 | not stated | Gyr | 7 | yields a typical $t_{\rm dep}\sim0.7$ Gyr in the redshift range $z=1-3$ |
| mu_mol for Delta_MS<-0.5 | ~0.1-0.2 | not stated | dimensionless | 7 | those galaxies with $\Delta_{\rm MS}<-0.5$ show molecular-gas-to-stellar-mass ratios of $\sim0.1-0.2$ |
| Contribution of all galaxies to rho_H2 | almost 100% at z<2, 80% at z~2.5 | not stated | percent | 7 | corresponds to almost 100% at $z<2.0$ decreasing to 80% at $z\sim2.5$ |

## Qualitative findings

- Faint ASPECS dusty galaxies lie systematically below the nominal MS with a wider distribution than field galaxies  
  > "These values indicate that ASPECS 1.2 mm galaxies are systematically below the nominal MS prescription, with a wider distribution" (Location in stellar mass vs. SFR plane)

## Claim tuples

- H: Faint dusty galaxies have lower redshifts than SMGs from shallow wide surveys | E: Compared redshift distribution with GOODS-S and AS2UDS samples | R: Median z=1.85 vs 2.92 and 2.61 | F: Faint DSFGs have significantly lower redshifts | **supported**
- H: A significant fraction of faint dusty galaxies lies off the MS | E: Delta_MS from MAGPHYS SFR and M* vs Schreiber+15 | R: 59% within, 6% above, 34% below | F: Below-MS galaxies are a non-negligible gas-rich population | **supported**
- H: ASPECS galaxies follow established gas scaling relations | E: Compared t_dep and mu_mol vs z, Delta_MS with PHIBSS and Tacconi/Liu relations | R: t_dep~0.7 Gyr at z=1-3; mu_mol rises ~5x z=0.5 to 3 | F: Consistent with standard scaling relations | **supported**
- H: The MS class dominating cosmic molecular gas changes with redshift | E: Summed dust-based gas mass by class in z bins relative to rho_H2 | R: MS ~60%; above-MS ~20% to ~0%; below-MS ~5% to ~40% from z~2.5 to z<1 | F: MS dominates at all z; below-MS contribution rises toward low z | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Fixed delta_GDR=200 SED-based masses chosen for consistency with earlier ASPECS studies  
  > "For consistency with previous studies in the ASPECS series (cite: aravena16b; aravena19; boogaard19; decarli19), we fix $\delta_{\rm GDR}=200$" (ISM molecular gas masses)
- Alternative: Metallicity-dependent delta_GDR and alpha_CO, RJ and CO-based masses give consistent results  
  > "Using either this later approach or any of the other methods yields molecular gas estimates that are well within the uncertainties" (ISM molecular gas masses)
- How they decided it was enough: _not stated_
- Limitation (authors): MAGPHYS stellar masses may be systematically underestimated; small source numbers may drive redshift trend  
  > "This pattern, however, could be produced by the low number of ASPECS 1.2 mm sources." (Location in stellar mass vs. SFR plane)
- Caveat (inferred, ours): Median SFR and stellar mass differ between abstract, text and conclusions (30 vs 33; 4.8 vs 4.3e10)
- Caveat (inferred, ours): Small field (~5 arcmin2) so cosmic variance affects the gas budget
- Caveat (inferred, ours): MS offsets depend on MAGPHYS stellar masses and Schreiber MS
- Caveat (inferred, ours): Gas masses depend on fixed delta_GDR=200 and Herschel-limited dust SEDs

## Reproducibility

- Data public (paper): ALMA data code 2016.1.00324 acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: 2016.1.00324." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Catalogs and photometry compiled in Decarli+19 and Gonzalez-Lopez+20
- Missing: MAGPHYS configuration details
- Missing: Imaging parameters (cell, size, clean threshold)
- Data volume (inferred): Large (~hundreds of GB raw for the 85-pointing mosaic); catalog-level reproduction needs far less
- Score (inferred): 3/5, Analysis relies on catalogs and measurements from companion papers, and the paper gives few imaging parameters; derived tables are given.
- Rediscovery candidate: no, Main results depend on inherited catalogs, MAGPHYS fits and external photometry not provided here.

## Links

- Method: (cite: gonzalezlopez20) (1.2 mm continuum source extraction, fidelity, catalog)
- Method: (cite: dacunha15) (high-z MAGPHYS)
- Method: (cite: aravena19) (gas budget approach)
- Companion: (cite: decarli19) (rho_H2 and master catalog)
- Companion: (cite: boogaard20) (CO line ratios)
- Companion: (cite: gonzalezlopez19) (band 3 CO line search)
- Related: ASPECS pilot
- Related: HUDF/XDF
- Related: MUSE HUDF survey
- Related: PHIBSS1/2
- Related: 3D-HST

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00324.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 55,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
