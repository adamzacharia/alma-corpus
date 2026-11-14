# SPT0346-52: Negligible AGN Activity in a Compact, Hyper-starburst Galaxy at z = 5.7

`2016ApJ...832..114M` | The Astrophysical Journal 2016 | first author: Ma, Jingzhe | arXiv: 1609.08553 | DOI: 10.3847/0004-637X/832/2/114

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Does an AGN contribute appreciably to the IR luminosity and the extreme SFR surface density of SPT0346-52?  
  > "The central question is whether this high luminosity surface density arises solely from intense star formation, or if there is an obscured active galactic nucleus (AGN)." (Introduction)
- Target **SPT0346-52 (SPT-S J034640-5204.9)**: coordinates 03:46:40 -52:04.9 (from name only)  
  > "SPT-S J034640-5204.9 (hereafter SPT0346-52) at $z$ = 5.656, among the highest-redshift DSFGs known." (Introduction); "magnified by the foreground lensing galaxy (at $z$ $\sim$ 1.1) a factor of 5.6 $\pm$ 0.1" (Introduction); z/distance z = 5.656  
  > "SPT-S J034640-5204.9 (hereafter SPT0346-52) at $z$ = 5.656, among the highest-redshift DSFGs known." (Introduction); "magnified by the foreground lensing galaxy (at $z$ $\sim$ 1.1) a factor of 5.6 $\pm$ 0.1" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Chandra net 49.52 ks; ATCA 3960 s at 5.5 and 9.0 GHz, 4068 s at 2.1 GHz  
  > "The net exposure time for the observation is 49.52 ks." (2.1 Chandra X-ray data); "observed with ATCA for 3960s at 5.5 and 9.0 GHz and 4068s at 2.1 GHz" (2.2 ATCA radio data)
- observing dates: Chandra 2015 July 29; ATCA 2012 January 25  
  > "SPT0346-52 was observed with the Advanced CCD Imaging Spectrometer (ACIS; (cite: Garmire2003)) on board *Chandra* on 2015 July 29." (2.1 Chandra X-ray data); "on 2012 January 25 in the 6A array configuration using the CABB in the 1M-0.5k mode" (2.2 ATCA radio data)
- pi or archival as stated: _not stated_
- Other facility **Chandra ACIS-S**: X-ray upper limit  
  > "The source was placed at the aim point of the back-illuminated ACIS-S3 chip." (2.1 Chandra X-ray data)
- Other facility **ATCA**: Radio continuum upper limits at 2.1, 5.5, 9.0 GHz  
  > "The continuum was not detected in any band" (2.2 ATCA radio data)
- Other facility **HST, Spitzer, Herschel, APEX, SPT**: Near-IR to mm photometry used in SED fitting  
  > "Previous near-IR to far-IR photometric data are summarized in Table [1](#tab:summary)." (2 Observations)
- External data: Lens model: magnification 5.6, intrinsic size R_eff 0.61 kpc, from ALMA 870 um imaging  
  > "Our lens model obtained from ALMA 870 $\ensuremath{\mu}m$ imaging shows that SPT0346-52 is magnified by the foreground lensing galaxy" (Introduction) [from (cite: Hezaveh2013; Spilker2016)]
- External data: L_IR and SFR from SED fitting; photometry  
  > "Multi-band spectral energy distribution (SED) fitting gives an intrinsic infrared (IR; 8-1000${\ensuremath{\mu}m}$) luminosity $L_{\rm IR}$ of (3.6 $\pm$ 0.3) $\times$ 10$^{13}$ $L_{\odot}$" (Introduction) [from (cite: Ma2015)]
- External data: R = 1.8 kpc and M_tot = 1.5e11 Msun from resolved CO imaging  
  > "derived in a spatially resolved CO imaging study by (cite: Spilker2015)" (3.3 Theoretical Expectations) [from (cite: Spilker2015)]
- External data: CO(2-1) v_FWHM = 613 km/s  
  > "measured from the low-J CO(2-1) line; (cite: Aravena2016)" (3.3 Theoretical Expectations) [from (cite: Aravena2016)]

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

- ATCA data reduction  
  > "The data was reduced in the same manner as in (cite: Aravena2013)." (2.2 ATCA radio data) [from (cite: Aravena2013)]
- Gamma_eff fixed to 1.4  
  > "Instead, $\Gamma_{\rm eff}$ is fixed to 1.4 following (cite: Xue2011) and (cite: Wang2013)." (2.1 Chandra X-ray data) [from (cite: Xue2011); (cite: Wang2013)]

### Not stated but needed to reproduce (our reading)

- CIGALE parameter grids and priors
- Which ALMA data were used for the lens model (not processed here)
- Chandra source position used for aperture centre

## Analysis recipe

1. **X-ray upper limit**: CIAO srcflux/aprates Bayesian upper limit in 1.75'' aperture, background from 78 random apertures  
  > "The background counts were estimated by placing 78 circular apertures with the same size at random positions in the field." (2.1 Chandra X-ray data)
   - software: CIAO, Sherpa
   - parameter: Gamma_int = 1.8; intrinsic NH 2.3e23 cm^-2  
  > "We assume $\Gamma_{\rm int}$ = 1.8, a typical value for AGNs." (2.1 Chandra X-ray data)
   - assumption: No differential magnification between FIR and X-ray  
  > "assuming there is no differential magnification between the FIR (i.e., ALMA) and the X-ray emission" (2.1 Chandra X-ray data)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting with AGN component**: CIGALE PYTHON with delayed-tau SFH, Bruzual & Charlot, Dale2014 IR, Fritz2006 AGN  
  > "We use a combination of (cite: Dale2014) IR models accounting for the dust emission from the stellar component and (cite: Fritz2006) AGN templates." (3.2 SED fitting)
   - software: CIGALE
   - assumption: Chabrier IMF  
  > "We adopt a (cite: Chabrier2003) IMF" (3.2 SED fitting)
   - fitting: Bayesian posterior; best fit by minimal reduced chi2  
  > "Parameters are analyzed under a Bayesian approach generating a posterior probability distribution function." (3.2 SED fitting)
   - validation: Compared to Lx/LFIR estimate  
  > "This is consistent with the estimation from the $L_{\rm X}$/$L_{\rm FIR}$ ratio" (3.2 SED fitting)
3. **Maximum starburst comparison**: Tacconi2006 SFR_max and Sigma_SFR_max to derive epsilon and f_g  
  > "Following (cite: Tacconi2006), the maximum ("Schmidt-law") SFR can be written as" (3.3 Theoretical Expectations)
   - assumption: SFR = 1.0e-10 L_IR (Kennicutt, Chabrier IMF); gas fraction 0.3-0.8  
  > "SFR = 1.0 $\times$ 10$^{-10}$ $L_{\rm IR}$ ($L_{\odot}$)" (footnote 1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIAO** 4.7: Chandra reprocessing and flux limits  
  > "We reprocessed the data with the *Chandra* Interactive Analysis of Observations (CIAO; version 4.7) tool $chandra\_repro$." (2.1 Chandra X-ray data)
- **Sherpa** : absorption models for unabsorbed flux  
  > "We run simulations adopting Sherpa (cite: Freeman2001) models" (2.1 Chandra X-ray data)
- **CIGALE PYTHON** : SED fitting with AGN  
  > "Now we employ CIGALE PYTHON (cite: Roehlly2014)" (3.2 SED fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Full-band 3sigma flux upper limit | 6.0e-15 | not stated | erg cm^-2 s^-1 | 1 | 3 $\sigma$ upper limit of 6.0 $\times$ 10$^{-15}$ ergs cm$^{-2}$ s$^{-1}$ |
| Lx/LFIR upper limit | 0.0038 | not stated | dimensionless | 1 | The X-ray to FIR ratio upper limit for SPT0346-52 is 0.0038 |
| AGN fractional contribution to FIR (X-ray) | at most 8% | not stated | percent | 1 | the AGN fractional contribution to the FIR luminosity is estimated to be at most 8% |
| AGN contribution from SED fit | at most ~20% | not stated | percent | 2 | the AGN component contributes at most $\sim$20% to the total IR luminosity |
| Star formation efficiency epsilon | 0.3-0.7 | not stated | dimensionless | 3 | to derive $\epsilon$, which turns out to be in the range of 0.3-0.7 |
| Observed Sigma_SFR | 1540 | 130 | Msun/yr/kpc^2 | 3 | The observed $\Sigma_{\rm SFR}$ = 1540 $\pm$ 130 |

## Qualitative findings

- ATCA radio upper limits consistent with FIR-radio correlation; no AGN indication  
  > "The ATCA radio continuum upper limits are also consistent with the FIR-to-radio correlation for star-forming galaxies" (abstract)

## Claim tuples

- H: An AGN contributes appreciably to the IR luminosity | E: Chandra upper limit, Lx/LFIR, SED fitting with AGN, ATCA limits | R: Lx/LFIR < 0.0038; AGN <=8% (X-ray), <=20% (SED) | F: IR emission is almost solely star formation | **supported**
- H: High Sigma_SFR is explained by star formation efficiency and gas fraction | E: Maximum starburst framework | R: epsilon 0.3-0.7 for f_g 0.3-0.8 | F: Requires very high efficiency and/or gas fraction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): High absorption, X-ray variability or differential magnification could weaken the limit; Compton-thick AGN cannot be excluded  
  > "we also cannot exclude Compton thick AGN by $L_{\rm FIR}$-$L_{\rm X}$ alone" (3.1)
- Caveat (inferred, ours): Gamma and NH assumed from other samples
- Caveat (inferred, ours): Single-source upper limits only

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CIGALE configuration
- Missing: ALMA lens model details
- Data volume (inferred): small (Chandra ~ tens of MB; ALMA part not reprocessed)
- Score (inferred): 3/5, ALMA only supporting; Chandra recipe fairly clear but SED setup incomplete.
- Rediscovery candidate: no, Main results rely on Chandra/ATCA and prior literature, not ALMA reprocessing.

## Links

- Method: (cite: Roehlly2014) (CIGALE PYTHON)
- Companion: (cite: Ma2015) (SED and photometry of SPT0346-52)
- Companion: (cite: Spilker2015) (resolved CO imaging, lens model)
- Related: SPT survey
- Related: ALESS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00958.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 28,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
