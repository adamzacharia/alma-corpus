# AGN feedback on molecular gas reservoirs in quasars at z   2.4

`2017A&A...605A.105C` | Astronomy and Astrophysics 2017 | first author: Carniani, S. | arXiv: 1706.08987 | DOI: 10.1051/0004-6361/201730672

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is molecular gas depleted or absent in the regions of quasar host galaxies swept by fast ionised outflows, as expected if AGN feedback quenches star formation?  
  > "compare the spatial distribution of the molecular gas with that of the fast-outflowing ionised gas" (Introduction)
- Target **LBQS0109+0213**: coordinates 01:12:16.99 +02:29:47.7 (J2000)  
  > "| LBQS0109 | 2.35 | 01:12:16.99 | +02:29:47.7 |" (Table 1); z/distance z = 2.35  
  > "| LBQS0109 | 2.35 | 01:12:16.99 | +02:29:47.7 |" (Table 1); distance from narrow [OIII] (Carniani 2015a)  
  > "| LBQS0109 | 2.35 | 01:12:16.99 | +02:29:47.7 |" (Table 1)
- Target **2QZJ002830.4-281706**: coordinates 00:28:30.42 -28:17:05.4 (J2000)  
  > "| 2QZJ0028 | 2.40 | 00:28:30.42 | -28:17:05.4 |" (Table 1); z/distance z = 2.40  
  > "| 2QZJ0028 | 2.40 | 00:28:30.42 | -28:17:05.4 |" (Table 1); distance from narrow [OIII] (Carniani 2015a)  
  > "| 2QZJ0028 | 2.40 | 00:28:30.42 | -28:17:05.4 |" (Table 1)
- Target **[HB89] 0329-385**: coordinates 03:31:06.41 -38:24:04.6 (J2000)  
  > "| HB8903 | 2.44 | 03:31:06.41 | -38:24:04.6 |" (Table 1); z/distance z = 2.44  
  > "| HB8903 | 2.44 | 03:31:06.41 | -38:24:04.6 |" (Table 1); distance from narrow [OIII] (Carniani 2015a)  
  > "| HB8903 | 2.44 | 03:31:06.41 | -38:24:04.6 |" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (~100 GHz, ~3 mm)  
  > "were observed at the Band 3 frequencies ($\sim100$ GHz, corresponding to $\lambda\sim3$ mm)" (3 Observations)
- frequencies and spectral setup: 4 spws of ~1.875 GHz, 7.5 GHz total, 1.9 MHz channels (~5.7 km/s); one spw on CO(3-2) at 103.2, 101.6, 100.5 GHz  
  > "have a total bandwidth of 7.5 GHz divided into four spectral windows of $\sim1.875$ GHz with a channel width of 1.9 MHz" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: semi-compact, max baseline ~1.5 km  
  > "The antennas were distributed in a semi-compact configuration with a maximum baseline length of $\sim 1.5$ km." (3 Observations)
- baselines: _not stated_
- angular resolution: ~0.6'' (beam ~0.6''x0.5'' in cubes)  
  > "with a beam size of about 0.6$''$$\times$0.5$''$" (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum 12 uJy/beam (first two), 18 uJy/beam (HB8903); cubes 240-280 uJy/beam per 30 km/s  
  > "1$\sigma$ sensitivity of 240-280 $\mu$Jy/beam per spectral bin of 30 km/s" (3 Observations)
- time on source: ~40 min, 40-44 12-m antennas  
  > "The on-source time was about 40 minutes with 40-44 12-m antennas for all sources." (3 Observations)
- observing dates: July 2015 to July 2016  
  > "between July 2015 and July 2016" (3 Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.8 GHz)
- Other facility **SINFONI/VLT**: H and K band IFU data of [OIII] and Halpha outflow and star formation maps  
  > "we have observed the three QSOs in the H (1.45-1.85 $\mu$m) and K (1.95-2.45 $\mu$m) bands" (2 Sample selection)
- Other facility **SDSS and 2MASS**: astrometric reference positions  
  > "consistent with the Sloan-Digital-Sky-Survey (SDSS) and Two-Micron-All-Sky-Survey (2MASS) positions" (3 Observations)
- External data: [OIII] outflow properties and Halpha SFRs and redshifts of targets  
  > "SFR estimated from ${\rm H\alpha}$ emission (cite: Carniani:2016)" (Table 1) [from (cite: Carniani:2015a; Carniani:2016)]
- External data: Black hole masses  
  > "Black hole masses from (cite: Shemmer:2004) and (cite: Williams:2016)" (Table 1) [from (cite: Shemmer:2004; Williams:2016)]
- External data: 8.4 GHz radio luminosity of LBQS0109  
  > "at 8.4 GHz (cite: Hooper:1995) measured with the Very Large Array" (4 LBQS0109) [from (cite: Hooper:1995)]
- External data: Gas-SFR relations for MS and starburst galaxies  
  > "best-fit relations by (cite: Sargent:2014) between molecular gas mass and SFR" (7 Lack of molecular gas) [from (cite: Sargent:2014)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; pipeline vs manual not stated  
  > "The data were calibrated using the CASA software version v4.5.2" (3 Observations)
- casa version: CASA 4.5.2  
  > "The data were calibrated using the CASA software version v4.5.2" (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and J0238+166  
  > "Ceres and J0238+166 were used as flux calibrators" (3 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "All final images were reconstructed by using the CASA task clean." (3 Observations)
- deconvolver: _not stated_
- weighting robust: continuum natural; cubes briggs robust = 0.5  
  > "weighting = briggs and robust = 0.5" (3 Observations)
- uv taper: _not stated_
- cell size: 0.1''  
  > "a spatial scale per pixel of 0.1$''$" (3 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub UV-plane model on line-free channels  
  > "using the uvcontsub task" (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Redshifts, outflow properties, spectro-astrometry and SFR from earlier SINFONI work  
  > "inferred by using the spectro-astrometric method described in (cite: Carniani:2015a)" (Table 1) [from (cite: Carniani:2015a)]
- Dust mass formula  
  > "Following (cite: Palau:2013), the equation can be simply rewritten as" (4 LBQS0109) [from (cite: Palau:2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub
- Clean masks, thresholds and iterations
- Flux scale uncertainty and self-calibration
- Aperture definitions for line flux and spectra
- Phase calibrator for 2QZJ0028 vs HB8903 assignment ambiguous
- SINFONI data not described in public form
- Conversion details from Jy km/s to L' and Mgas

## Analysis recipe

1. **Image continuum and cubes**: clean on line-free channels (natural) and continuum-subtracted cubes (briggs 0.5, 30 km/s)  
  > "Continuum images at 3 mm were obtained using the line-free channels of the four spectral windows." (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: astrometry checked against SDSS/2MASS within ~0.1''  
  > "within the astrometric uncertainty of about 0.1$''$" (3 Observations)
2. **Measure continuum size and flux**: 2D elliptical Gaussian fit to visibilities  
  > "fitting a 2D elliptical Gaussian profile to the visibility data in CASA by using the uvmodelfit task" (3 Observations)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive dust masses**: optically thin dust mass from 3 mm flux  
  > "we have adopted the optically thin approximation for our unobscured QSO" (4 LBQS0109)
   - assumption: Td=40-60 K, beta=2.0, kappa=0.45 (nu/250GHz)^beta cm2/g, continuum all dust  
  > "We adopt a $\kappa_\nu$ = ${\rm 0.45\times(\nu/250 GHz)^\beta \ cm^2 g^{-1}}$ with a fixed emissivity index $\beta=2.0$." (4 LBQS0109)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure CO(3-2) line and gas mass**: single Gaussian fit to spectrum, integrated flux in >2 sigma region, convert to L'CO and Mgas with r31 and alpha_CO; 3 sigma upper limits for non-detections assuming FWHM 400 km/s  
  > "derived from a single Gaussian fit, are $400\pm60$ km/s" (4 LBQS0109)
   - software: CASA
   - assumption: r31=1.0+-0.5; alpha_CO = 0.8 and 4  
  > "r$_{31}$$=1.0\pm0.5$" (4.1 Molecular and stellar mass estimates)
   - fitting: _not stated_
   - validation: CO redshift and width compared with narrow [OIII] and Halpha  
  > "The agreement strongly indicates that most of the CO emission is tracing molecular gas in the host galaxy." (4 LBQS0109)
5. **Compare CO with SINFONI outflow maps and test reality of 2QZJ0028 blueshifted feature**: overlay maps; blind search of positive vs negative line peaks  
  > "We extracted 16 positive and 10 negative emission line with a level of confidence higher 5$\sigma$." (Reliability)
   - fitting: _not stated_
   - validation: positive vs negative peak counts  
  > "We extracted 16 positive and 10 negative emission line with a level of confidence higher 5$\sigma$." (Reliability of the CO(3-2) line detection in 2QZJ0028.)

## Software

- **CASA** 4.5.2: calibration, clean, uvcontsub, uvmodelfit  
  > "The data were calibrated using the CASA software version v4.5.2" (3 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| LBQS0109 CO(3-2) integrated flux | 0.34 | 0.03 | Jy km/s | 4 | S$_{\rm CO(3-2)} \Delta v$ \[Jy km/s\]$^{c}$ / $0.34\pm0.03$ |
| LBQS0109 CO(3-2) FWHM | 400 | 60 | km/s | 4 | are $400\pm60$ km/s |
| LBQS0109 z_CO(3-2) | 2.3558 | 0.0005 | dimensionless | 4 | $z_{\rm CO(3-2)} = 2.3558\pm0.0005$ |
| LBQS0109 Mgas (alpha_CO=4) | 4.0e10 | 2.4e10 | Msun | 4 | M$_{\rm gas}$($\alpha_{\rm CO}$=4) \[$10^{10}$ $\mathrm{M}_{\odot}$\]$^{c,d}$ / $4.0\pm2.4$ |
| 2QZJ0028 CO(3-2) flux upper limit (3 sigma) | <0.09 | not stated | Jy km/s | 4 | 3$\sigma$ upper limit on the CO(3-2) integrated line flux of 0.09 Jy km/s |
| HB8903 3 mm continuum flux | 5.738 | 0.018 | mJy | 2 | $5.738\pm0.018$ mJy |
| 2QZJ0028 blueshifted CO flux | 0.12 | 0.02 | Jy km/s | 4 | $0.12\pm0.02$ |

## Qualitative findings

- LBQS0109 CO is faint or absent along the ionised outflow direction and resembles the narrow [OIII] star formation distribution.  
  > "Both emission lines are faint or absent along the direction of the ionised outflow, while they are clearly visible in the other regions." (4.2 Morphology of the CO(3-2) emission)
- Serendipitous sources suggest the QSOs lie in overdense regions.  
  > "The detections of these seredentipitous sources in our ALMA observations suggest that the three QSOs are located in a overdensity." (8 Overdensity)

## Claim tuples

- H: Outflows remove molecular gas where they sweep the host | E: Compare ALMA CO(3-2) maps with SINFONI outflow maps in LBQS0109 | R: CO faint or absent along outflow direction | F: Outflow is removing molecular gas and quenching SF in that region | **partially**
- H: A molecular outflow is present in 2QZJ0028 | E: Search for CO offset from systemic velocity | R: Tentative CO at about -2000 km/s, S/N=5.2, co-located with ionised outflow | F: Possible molecular outflow clump, needs confirmation | **partially**
- H: QSO hosts have low gas content relative to MS galaxies | E: Mgas versus SFR compared with Sargent 2014 relations | R: All three below the MS relation extrapolation for alpha_CO=0.8 | F: Low gas mass consistent with SMGs and QSOs; depletion times short | **partially**
- H: QSOs reside in overdensities | E: Serendipitous continuum and line sources compared with number counts | R: Six companions within ~160 kpc | F: QSOs likely in overdense systems | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimetre CO avoids dust extinction affecting optical SF tracers.  
  > "observations at (sub-)millimetre wavelengths are crucial to definitely establish whether star formation is inhibited by fast outflows" (Introduction)
- Alternative: Blueshifted CO in 2QZJ0028 could be a merging companion, but SINFONI shows no merger signature.  
  > "An alternative interpretation to the outflow scenario could be that the detected blue-shifted CO emission is associated with a merging companion galaxy." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevents pixel-by-pixel kinematics; deeper data needed.  
  > "we cannot perform a detailed pixel-by-pixel kinematic analysis because of the low S/N of the data" (4 LBQS0109)
- Caveat (inferred, ours): alpha_CO and r31 are unconstrained, so gas masses uncertain by large factors
- Caveat (inferred, ours): 2QZJ0028 detection is marginal (5 sigma, few peaks) and at risk of being noise
- Caveat (inferred, ours): Single-object CO morphology with a beam-elongated structure may be affected by beam shape
- Caveat (inferred, ours): Companion redshifts unconfirmed, overdensity inferred assuming CO(3-2)

## Reproducibility

- Data public (paper): Data retrievable from ALMA archive  
  > "which can be retrieved from the ALMA data archive" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel selection and masks
- Missing: SINFONI datacubes and earlier outflow maps
- Missing: Aperture definitions for line fluxes
- Data volume (inferred): ~50-100 GB raw for 3 EBs-sets; cubes small
- Score (inferred): 3/5, Public data and standard CASA steps, but key imaging settings and apertures unstated and SINFONI comparison needs external data.
- Rediscovery candidate: no, Key imaging and extraction details missing and the main claims rely on SINFONI comparison.

## Links

- Method: (cite: Palau:2013) (dust mass formula)
- Method: (cite: Carniani:2015a) (spectro-astrometric outflow method)
- Companion: (cite: Carniani:2016) (Halpha/[OIII] star formation and SINFONI data)
- Companion: (cite: Cano-Diaz:2012) (SINFONI outflow quenching result)
- Related: SINFONI QSO sample of Shemmer/Netzer 2004

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00965.S"
 ],
 "codes_printed_but_missing": [
  "2013.0.00965.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
