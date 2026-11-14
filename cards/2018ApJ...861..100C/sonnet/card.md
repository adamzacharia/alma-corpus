# An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Identifying Candidate z ∼ 4.5 [C II] Emitters

`2018ApJ...861..100C` | The Astrophysical Journal 2018 | first author: Cooke, E. A. | arXiv: 1805.05363 | DOI: 10.3847/1538-4357/aac6ba

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Can serendipitous [C II] emitters at z~4.4-4.7 be identified in the AS2UDS ALMA Band 7 data cubes, and what are their properties (sizes, dust temperatures, [C II] deficit, luminosity function)?  
  > "We aim to spectroscopically confirm \[C II\] emission line sources at $z\simeq4.5$ and thus determine their basic properties such as infrared luminosity and dust temperature" (1 Introduction)
- Target **AS2UDS SMGs in the SCUBA-2 UDS field (ten line emitters, e.g. AS2UDS.0002.1, 0051.0, 0104.0)**: coordinates e.g. AS2UDS.0002.1 02:18:24.24 -05:22:56.9 (J2000); others in Table 1  
  > "AS2UDS.0002.1   | 02:18:24.24 | $-$05:22:56.9 | 7.4$\pm$0.5 | 338.707         | 4.611$\pm$0.009" (Table 1); z/distance z_[CII] = 4.404-4.615 (median 4.45)  
  > "AS2UDS.0002.1   | 02:18:24.24 | $-$05:22:56.9 | 7.4$\pm$0.5 | 338.707         | 4.611$\pm$0.009" (Table 1); distance from [C II] line redshift from ALMA cubes  
  > "AS2UDS.0002.1   | 02:18:24.24 | $-$05:22:56.9 | 7.4$\pm$0.5 | 338.707         | 4.611$\pm$0.009" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01528.S, 2016.1.00434.S
- bands: Band 7 (870 um)  
  > "We observed all $716$ of these submillimeter sources with ALMA at $870$ $\mu$m in Band 7" (2.1 ALMA data)
- frequencies and spectral setup: 7.5 GHz total in two sidebands: 336-340 and 348-352 GHz; raw resolution ~13.5 km/s  
  > "our observations cover a total bandwidth of 7.5 GHz split into two sidebands: $336$–$340$ GHz and $348$–$352$ GHz" (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15-0.3 arcsec FWHM (natural weighting); tapered to 0.5 arcsec  
  > "The synthesised beam of our observations is $0.15$–$0.3$ arcsec full-width, half maximum (FWHM), adopting natural weighting." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 0.5" tapered continuum rms 0.25, 0.34, 0.23 mJy/beam for Cycles 1, 3, 4  
  > "average depths of $\sigma_{870\mu{\rm m}}=0.25,0.34$, and $0.23$ mJy beam$^{-1}$ for Cycle $1,3$, and $4$ data, respectively" (2.1 ALMA data)
- time on source: ~40 s per pointing; ~80-90 s for 120 pointings observed in Cycles 3 and 4  
  > "Each pointing was centred on the SCUBA-2 catalogue position and observed for a total of $\sim40$ s." (2.1 ALMA data)
- observing dates: 2013 November to 2017 May (Cycles 1, 3, 4)  
  > "The data were taken in the period 2013 November to 2017 May (Cycles $1$, $3$, and $4$)" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: C+ 2P3/2 -> 2P1/2 [C II] (157.74 um)
- Other facility **UKIDSS UDS DR11**: Optical-NIR-IRAC photometric catalogue for counterparts and photo-z  
  > "we match our sources to the UDS DR11 using a search radius of $0.6$ arcsec, giving a false-match rate of $3.5$ percent" (2.2 Multi-wavelength data)
- Other facility **Herschel PACS/SPIRE**: 100-500 um far-IR photometry (deblended and stacked)  
  > "at $100$ $\mu$m, $160$ $\mu$m, $250$ $\mu$m, $350$ $\mu$m, and $500$ $\mu$m" (2.2 Multi-wavelength data)
- Other facility **VLA UDS20 1.4 GHz**: Radio data, rms ~6 uJy/beam, also used as deblending priors  
  > "resulting in an rms noise of $\sim6\mu$Jy beam$^{-1}$ across the full field" (2.2 Multi-wavelength data)
- Other facility **SCUBA-2 S2CLS**: 850 um parent catalogue of 716 sources  
  > "detecting $716$ submillimeter sources above $4\sigma$, $S_{850}\simeq 3.6$ mJy" (2.1 ALMA data)
- External data: SMG far-IR SED/dust temperature comparison samples and Herschel deblending method/catalogues  
  > "For the deblending we follow the method described in (cite: Swinbank2014)." (2.2 Multi-wavelength data) [from (cite: Swinbank2014)]
- External data: Local [C II]/L_IR comparison galaxies  
  > "We compare our sample with local galaxies from (cite: GraciaCarpio2011; Herrera-Camus2018)." (3.3 [C II] deficit) [from (cite: GraciaCarpio2011; Herrera-Camus2018)]
- External data: Gas-to-dust ratio GDR=90±25  
  > "Adopting the value of $\text{GDR}=90\pm25$ from (cite: Magnelli2012a)" (3.6 Molecular and dynamical masses) [from (cite: Magnelli2012a)]
- Simulation/model as data: Model [C II] luminosity functions from Popping2016 and Lagache2018 and z=0 LF from Hemmati2017 compared with the measured LF  
  > "we compare to the $z=0$ \[C II\] luminosity function from (cite: Hemmati2017), the predicted $z=4$ luminosity function from (cite: Popping2016)" (3.7 [C II] luminosity function)

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

- task: Dirty (uncleaned) tapered cubes for line search; cleaned tapered continuum maps  
  > "We construct cleaned, tapered continuum maps and dirty, tapered data cubes." (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: ~400 klambda Gaussian taper to 0.5" FWHM  
  > "tapered to $0.5''$ FWHM resolution to match the continuum maps by applying a $\sim400$ k$\lambda$ Gaussian *uv* taper" (2.1 ALMA data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear fit to the continuum in each pixel's spectrum  
  > "These cubes were first continuum-subtracted by subtracting a linear fit to the continuum in the spectrum of each pixel" (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: [C II] fluxes corrected for ALMA primary beam  
  > "our measured \[C II\] fluxes (and hence luminosities) have been corrected for the ALMA primary beam" (3.3 [C II] deficit)
- array combination: _not stated_
- smoothing: Cubes velocity-binned to 50, 100, 200 km/s  
  > "we velocity-binned the $0.5''$ tapered, continuum-subtracted cubes to 50 km s$^{-1}$, 100 km s$^{-1}$, and 200 km s$^{-1}$ channels" (2.1 ALMA data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full data reduction, continuum catalogue and source identification  
  > "The full data reduction and catalogue will be presented in Stach et al. (in preparation)." (2.1 ALMA data) [from Stach et al. (in preparation)]
- Herschel SPIRE deblending method  
  > "For the deblending we follow the method described in (cite: Swinbank2014)." (2.2 Multi-wavelength data) [from (cite: Swinbank2014)]
- K-band Sersic fitting details  
  > "Further details of the UDS $K$-band Sérsic fitting can be found in (cite: Almaini2017) (cite: Lani2013)." (3.4 Sizes of [C II] emitters) [from (cite: Almaini2017); (cite: Lani2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details (deferred to Stach et al.)
- Cleaning parameters, weighting and image size for continuum maps
- Exact stacking procedure and Gaussian fit setup for size measurement
- Bootstrap details for SED stack
- Aperture sizes and line-free channel handling in continuum fits
- Completeness simulation details beyond 10^4 injected lines
- Prior list and catalogue for deblending

## Analysis recipe

1. **Build tapered continuum maps and select SMGs**: Cleaned 0.5" tapered continuum maps; sources with S/N>=4.3 in 0.5" aperture; false positive rate 2% from inverted maps  
  > "ALMA continuum sources were identified in the continuum maps as submillimeter sources with a signal-to-noise ratio ${\rm S/N}\ge4.3$ within a $0.5$ arcsec diameter aperture" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: Inverted maps  
  > "This S/N limit provides a two percent false positive rate, as determined by inverting the maps." (2.1 ALMA data)
2. **Search for line emitters at continuum positions**: Extract spectra at SMG positions in binned continuum-subtracted cubes, find S/N>=2 peaks, refit with Gaussian, apply integrated S/N cut for 10% false rate  
  > "we take an integrated S/N cut which varies depending upon the velocity binning with ${\rm S/N}=8.0$ for $50$ km s$^{-1}$ channels, ${\rm S/N}=7.5$ for $100$ km s$^{-1}$ channels and ${\rm S/N}=7.0$ for $200$ km s$^{-1}$ channels" (2.1 ALMA data)
   - software: CASA
   - fitting: Gaussian profile in 50 km/s channel spectrum  
  > "These were then refit in the 50 km s$^{-1}$ channel spectrum using a Gaussian profile" (2.1 ALMA data)
   - validation: Same procedure on inverted cubes gives empirical false positive rate  
  > "we calculate an empirical false positive rate by applying the same procedure to the inverted, velocity-binned, continuum-subtracted cubes" (2.1 ALMA data)
3. **Search for continuum-less line emitters**: Collapse 100 km/s slices stepped by 50 km/s, find >2 sigma peaks; compare with inverted cubes  
  > "we find no additional emission line sources within the ALMA pointings above a false positive rate of 50 percent" (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit far-IR SED for L_IR and T_d**: Modified blackbody to Herschel PACS/SPIRE/ALMA fluxes for individual sources and stacked Herschel images (bootstrap)  
  > "we fit a modified blackbody to the far-infrared photometry of each source from *Herschel* PACS, SPIRE and ALMA (cite: Swinbank2014), adopting a spectral index of $\beta=1.8$" (3.3 [C II] deficit)
   - parameter: beta = 1.8; stack assumes z=4.45  
  > "assuming the sources lie at $z=4.45$ (the median redshift of our sample)" (3.3 [C II] deficit)
   - assumption: beta=1.8  
  > "adopting a spectral index of $\beta=1.8$" (3.3 [C II] deficit)
   - fitting: _not stated_
   - validation: Simulated SEDs recover input T_d to 7%  
  > "$|T_{\rm d,in}-T_{\rm d,out}|/T_{\rm d,in}=0.07$ on average" (3.5 z~4.5 SMGs are warm)
5. **Measure continuum and [C II] sizes by stacking**: Stack six sources with 0.15" data, normalise to unit peak, 2D Gaussian fit, deconvolved circularised effective radii, bootstrap errors  
  > "Using a 2-dimensional Gaussian profile fit we measure circularised effective radii (deconvolved with the beam)" (3.4 Sizes of [C II] emitters)
   - parameter: [C II] images from within ±1 FWHM of line peak  
  > "\[C II\] images were constructed from the emission within $\pm1$ FWHM in frequency of the emission line peak" (3.4 Sizes of [C II] emitters)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dust, gas and dynamical masses**: M_d from S870 with kappa=0.077 m2/kg, beta=1.8; M_gas = GDR*M_d; M_dyn = v^2 r_e/(G sin^2 i)  
  > "Assuming the average value for randomly inclined galaxy disks $\langle$sin $i \rangle = 0.79$ (cite: Law2009)" (3.6 Molecular and dynamical masses)
   - assumption: GDR=90±25; <sin i>=0.79; 50% of gas within r_e  
  > "we assume the cold gas reservoir is similar in scale to the \[C II\] emission and so scale the gas mass by the fraction of \[C II\] emission within the effective radius: 50 percent" (3.6 Molecular and dynamical masses)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive [C II] luminosity function**: Seven SMGs with S870>=3.6 mJy in 1.2e6 Mpc^3, corrected for completeness from 10^4 injected lines  
  > "from inserting $10^4$ false emission lines into spectra where no lines were originally detected and re-running our emission line detection we determine the recovery rate" (3.7 [C II] luminosity function)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data processing, continuum maps and cubes  
  > "All data were processed using the Common Astronomy Software Application (cite: McMullin2007)." (2.1 ALMA data)
- **GALFIT/GALAPAGOS** : K-band Sersic size fits  
  > "using GALFIT/GALAPAGOS (cite: Galfit; Galapagos)" (3.4 Sizes of [C II] emitters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of candidate line emitters | 10 | 10% false detection rate | sources | 2 | We detect significant emission lines in ten SMGs above these limits. |
| Median [C II] FWHM | 370 | ±50 | km/s | 2 | with a median of $370\pm50$ km s$^{-1}$ |
| [C II] effective radius | 1.7 | +0.1/-0.2 | kpc | 5 | $1.0\pm0.1$ kpc and $1.7^{+0.1}_{-0.2}$ kpc at $z\sim4.5$ |
| Continuum effective radius | 1.0 | ±0.1 | kpc | 5 | $1.0\pm0.1$ kpc and $1.7^{+0.1}_{-0.2}$ kpc at $z\sim4.5$ |
| Stacked median dust temperature | 51 | ±4 | K | 4 | a median dust temperature of $T_{\rm d} = 51\pm4$ K |
| Stacked median L_IR | 1.0e13 | ±0.4e13 | Lsun | 4 | $L_{\text{IR}} = (1.0\pm0.4)\times10^{13}$ L$_{\odot}$ |
| Star-formation rate surface density | 130 | ±20 | Msun/yr/kpc^2 | 5 | star-formation rate surface density of $130\pm20$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Average dust mass | 1.6e8 | ±0.3e8 | Msun | 6 | $M_{\rm d} = (1.6\pm0.3) \times10^8$ M$_{\odot}$ |
| Dynamical mass | 2.1e10 | ±0.6e10 | Msun | 6 | $M_{\rm dyn} = (2.1\pm0.6)\times10^{10}$ M$_{\odot}$ |
| Gas fraction | 0.4 | ±0.2 | dimensionless | 6 | $f_{\rm gas} = 0.5 \times M_{\rm gas} / M_{\rm dyn} = 0.4\pm0.2$ |
| Space density of luminous SMGs at z=4.4-4.66 (lower limit) | >5e-6 | not stated | Mpc^-3 | 7 | we place a lower limit of $>5\times10^{-6}$ Mpc$^{-3}$ on the space density |

## Qualitative findings

- [C II] emission is more extended than rest-frame 160 um dust continuum.  
  > "This demonstrates that the \[C II\] emission is significantly more extended than the continuum emission in these $z=4.5$ galaxies" (3.4 Sizes of [C II] emitters)
- [C II] luminosity function at z~4.5 shows no strong evolution from z=0.  
  > "We find no evidence for any strong evolution of the \[C II\] luminosity function between $z=0$ and $z\sim4.5$" (3.7 [C II] luminosity function)

## Claim tuples

- H: Serendipitous [C II] emitters at z~4.5 can be found in AS2UDS cubes | E: Line search in 695 tapered cubes with 10% false rate | R: Ten emitters, two possibly high-J CO | F: At least eight likely [C II] at z=4.4-4.6 | **supported**
- H: [C II] is more extended than dust continuum | E: Stacking six high-resolution sources | R: 1.7 vs 1.0 kpc | F: [C II] more extended | **supported**
- H: z~4.5 SMGs have warmer dust than z~2 SMGs | E: Modified blackbody fits to Herschel+ALMA photometry | R: T_d=55±4 K median vs ~35 K | F: Warmer at higher L_IR | **supported**
- H: Models predict the z~4.5 [C II] LF | E: Compare measured LF with Popping2016 and Lagache2018 | R: Lagache overpredicts, Popping underpredicts | F: LF similar to z=0 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lines could be other species (high-J CO, [N II], [O I]); two sources judged possibly CO  
  > "Two have multi-wavelength properties that suggest they are lower-redshift CO emission." (3.1 Alternative emission lines)
- How they decided it was enough: _not stated_
- Limitation (authors): Line identities unconfirmed without additional lines; sample requires continuum detection so LF is a lower limit  
  > "with no additional detected lines we cannot confirm the identity of the line emission in any of these sources" (3.1 Alternative emission lines)
- Caveat (inferred, ours): Redshifts rely on a single line; line ID uncertain
- Caveat (inferred, ours): Small sample sizes for stacking and LF
- Caveat (inferred, ours): Possible lensing not corrected
- Caveat (inferred, ours): Single-aperture vs spectral extraction flux inconsistency (0.2-0.3 dex)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Archive links two project codes; the paper cites ADS/JAO data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01528.S, ADS/JAO.ALMA#2016.1.00434.S." (Acknowledgments)
- Missing: Stach et al. continuum catalogue (in preparation)
- Missing: UDS DR11 catalogue (in preparation)
- Missing: CASA imaging parameters
- Missing: Herschel prior catalogues
- Data volume (inferred): Large: ~700 Band 7 pointings across several cycles; hundreds of GB to ~1 TB raw
- Score (inferred): 3/5, Line-search method is clear but calibration, imaging parameters and catalogues rely on unpublished companion papers.
- Rediscovery candidate: no, Key inputs (source catalogue, imaging details) are deferred to in-preparation papers.

## Links

- Method: Swinbank et al. 2014 (cite: Swinbank2014) (Herschel deblending and SED fitting method)
- Companion: Stach et al. (in preparation) (AS2UDS data reduction and catalogue)
- Companion: Gullberg et al. 2018 (cite: Gullberg2018) (Independent confirmation of AS2UDS.0051.0 and [C II] sizes)
- Related: AS2UDS
- Related: SCUBA-2 Cosmology Legacy Survey
- Related: ALESS
- Related: UKIDSS UDS
- Related: UDS20

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 48,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
