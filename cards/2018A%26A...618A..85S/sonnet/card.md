# Near infrared spectroscopy and star-formation histories of 3 ≤ z ≤ 4 quiescent galaxies

`2018A&A...618A..85S` | Astronomy and Astrophysics 2018 | first author: Schreiber, C. | arXiv: 1807.02523 | DOI: 10.1051/0004-6361/201833070

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Are UVJ-selected z>3 massive quiescent galaxies truly quiescent (purity/completeness), and what are their number densities and star-formation histories compared with galaxy formation models?  
  > "Using this sample, we derived statistics on the completeness and purity of the $UVJ$ color selection at $z>3$, and used this information to derive updated number densities and star formation histories for QGs at these early epochs, to compare them against models." (1 Introduction)
- Target **24 UVJ-selected quiescent galaxy candidates at 3<z<4 (ZFOURGE/3DHST; e.g. ZF-COS-20115)**: coordinates Table gives RA/Dec in degrees per galaxy (e.g. ZF-COS-20115: 150.06149, 2.3787093)  
  > "ZF-COS-20115 | 150.06149 | 2.3787093" (Table 1); "The photometric redshifts ranged from $z_{\rm phot}=2.89$ up to $3.91$" (4.1 Observed sample); z/distance z_phot 2.89-3.91; z_spec up to 3.715  
  > "ZF-COS-20115 | 150.06149 | 2.3787093" (Table 1); "The photometric redshifts ranged from $z_{\rm phot}=2.89$ up to $3.91$" (4.1 Observed sample); distance from EAzY photometric redshifts; MOSFIRE spectroscopic redshifts via slinefit  
  > "ZF-COS-20115 | 150.06149 | 2.3787093" (Table 1); "The photometric redshifts ranged from $z_{\rm phot}=2.89$ up to $3.91$" (4.1 Observed sample)

## Data provenance

- ALMA projects: 2013.1.01292.S, 2015.A.00026.S, 2015.1.01528.S, 2015.1.01074.S, 2015.1.01495.S, 2012.1.00307.S, 2012.1.00869.S, 2013.1.00151.S, 2015.1.00379.S, 2013.1.00118.S
- bands: Band 7 (all nine galaxies), Band 8 for ZF-COS-20115; Band 6 for some extra ZFOURGE galaxies  
  > "nine galaxies were observed, all in Band 7 except ZF-COS-20115 which was also observed in Band 8." (2.6 Archival ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.2'' (FWHM) for parts of 2015.1.01528.S and 2015.1.01074.S  
  > "Parts of the programs 2015.1.01528.S and 2015.1.01074.S were observed at high resolution (FWHM of $0.2\ensuremath{''}$)" (2.6 Archival ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: detection limit typically 0.8 mJy (Band 7) and 0.2 mJy (Band 6)  
  > "The detection limit is typically $0.8$ and $0.2\,{\rm mJy}$ in Band 7 and 6, respectively" (6.3.1 Removing dusty SFGs)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from several programs  
  > "We cross matched our sample of quiescent galaxies with the ALMA archive" (2.6 Archival ALMA observations)
- Other facility **Keck-MOSFIRE**: H- and K-band NIR spectra of 24 quiescent candidates (main data set)  
  > "The quiescent galaxies studied in this paper were observed by four separate MOSFIRE programs comprising 10 different masks" (2.3 MOSFIRE masks and runs)
- Other facility **ZFOURGE / 3DHST catalogs**: Parent photometric catalogs for sample selection  
  > "The galaxies were selected either from the ZFOURGE or 3DHST catalogs" (2.1 Parent catalogs)
- External data: ALMA flux (non-detection, de-blended) and photometry of ZF-COS-20115  
  > "For ZF-COS-20115 we used the flux reported in (cite: schreiber2018), after de-blending it from its dusty neighbor, resulting in a non-detection." (2.6 Archival ALMA observations) [from (cite: schreiber2018)]
- External data: MERAXES SAM number density and z=3.5 snapshot SFHs (private communication)  
  > "their model predicts a number densities of quiescent galaxies of $1.1\times10^{-5}\,{\rm Mpc}^{-3}$ at $z=3.5$ (Y. Qin, private communication)" (7.1) [from (cite: qin2017-a; qin2017)]
- Simulation/model as data: Henriques 2015 SAM light cone, Illustris, MUFASA and MERAXES used for comparison  
  > "We downloaded the first $3.14{\rm deg}^2$ light cone of the (cite: henriques2015) SAM" (7.1)

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
- uv taper: re-reduced with taper to 0.4'' and 0.7'' resolution (2015.1.01528.S and 2015.1.01074.S)  
  > "we re-reduced the images from these two programs with a tapering to $0.4\ensuremath{''}$ and $0.7\ensuremath{''}$ resolution, respectively" (2.6 Archival ALMA observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes measured on primary-beam-corrected images  
  > "We measured the peak fluxes of all galaxies on the primary-beam-corrected ALMA images" (2.6 Archival ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: about 0.3 mJy RMS for tapered images  
  > "reasonable sensitivity of about $0.3\,{\rm mJy}$ RMS" (2.6 Archival ALMA observations)

### Inherited from earlier work

- uvmodelfit flux measurement for extended sources  
  > "we used their integrated flux as measured from $(u,v)$ plane fitting using `uvmodelfit` (as in (cite: schreiber2017))" (2.6 Archival ALMA observations) [from (cite: schreiber2017)]
- FAST++ setup and SFH model  
  > "using FAST++[^3] v1.2 with the same setup as in (cite: schreiber2018)" (2.2) [from (cite: schreiber2018)]
- MOSFIRE pipeline reduction  
  > "The reduction of the raw frames into 2D spectra was performed using the MOSFIRE pipeline as in (cite: nanayakkara2016)." (2.5 Reduction of the spectra) [from (cite: nanayakkara2016)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration/CASA version and whether archive products or re-calibration used
- imaging parameters (weighting, robust, cell, size) for ALMA images
- which archival ALMA EBs/spectral windows used and the 3 sigma flux table for the 46 covered ZFOURGE galaxies
- IDs of galaxies per ALMA program in the number-density analysis
- conversion from ALMA flux to L_IR beyond cited template

## Analysis recipe

1. **Measure ALMA fluxes of quiescent candidates**: Peak flux on primary-beam-corrected images, noise from pixel RMS in 5'' annulus; uvmodelfit for extended sources  
  > "determined the associated uncertainties from the pixel RMS within a $5\ensuremath{''}$ diameter annulus around the source." (2.6 Archival ALMA observations)
   - software: uvmodelfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert ALMA fluxes to L_IR/SFR and constrain SED fit**: L_IR from dust templates at average T_dust(z) used to constrain attenuation in FAST++; stacked weighted flux  
  > "we computed its $L_{\rm IR}$ using the dust templates from (cite: schreiber2018-a), assuming the average dust temperature at the redshift of each galaxy" (5.1 Modeling)
   - software: FAST++
   - assumption: T_dust ~ 40 K at z~3.5  
  > "e.g, $T_{\rm dust}\sim40\,{\rm K}$ at $z\sim3.5$" (5.1 Modeling)
   - fitting: _not stated_
   - validation: _not stated_
3. **Use ALMA detection rates to remove dusty SFGs and quantify contamination of young/dusty quiescent samples**: Cross-match 130 ZFOURGE galaxies with ALMA archive; detection >3 sigma excludes quiescence  
  > "Of the $130$ massive galaxies in ZFOURGE, $46$ were observed with ALMA, and $22$ were detected at more than $3\sigma$ significance." (6.3.1 Removing dusty SFGs)
   - assumption: detection limit corresponds to L_IR ~1e12 Lsun or SFR >~100 Msun/yr  
  > "equivalent to an $L_{\rm IR}$ detection limit of about $10^{12}\,L_\odot$" (6.3.1 Removing dusty SFGs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **uvmodelfit** : integrated flux of extended ALMA sources  
  > "integrated flux as measured from $(u,v)$ plane fitting using `uvmodelfit`" (2.6 Archival ALMA observations)
- **FAST++** v1.2: SED fitting for stellar masses, SFRs, SFHs  
  > "Stellar masses and ${\rm SFR}$s were re-computed using FAST++[^3] v1.2" (2.2)
- **EAzY** : photometric redshifts and rest-frame colors  
  > "Photometric redshifts and rest-frame colors were obtained with the latest version of EAzY" (2.2)
- **slinefit** : spectroscopic redshifts and line fluxes  
  > "The spectra were analyzed with `slinefit`[^4] to measure the spectroscopic redshifts." (3.1)
- **MOSFIRE pipeline** : 2D spectra reduction  
  > "The reduction of the raw frames into 2D spectra was performed using the MOSFIRE pipeline" (2.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked ALMA flux of remaining quiescent galaxies | 0.07 | 0.11 | mJy | 1 | the stacked ALMA flux of the remaining galaxies is $0.07\pm0.11\,{\rm mJy}$ |
| Stacked ALMA-derived SFR | 11 | 17 | Msun/yr | 2 | Stacking the ALMA-derived $L_{\rm IR}$ for these galaxies leads to ${\rm SFR}=11\pm17\,M_\odot/{\rm yr}$ |
| ALMA detection rate UVJ-quiescent | 8% (1/12) | not stated | dimensionless | 3 | the detection rate for $UVJ$-quiescent galaxies is particularly low ($8\%$, 1/12) |
| ALMA detection rate dusty-quiescent | 67% (4/6) | not stated | dimensionless | 3 | dusty-quiescent galaxies have a detection rate of $67\%$ (4/6) |
| UVJ contamination rate at 3<z<4 | 21% | not stated | dimensionless | 0 | this implies that $21\%$ of the galaxies initially classified as $UVJ$-quiescent were spurious |
| Number density of UVJ-quiescent galaxies (M>3e10, 3<z<4) | 1.4e-5 | 0.3e-5 | Mpc^-3 | 0 | a number density of $(1.4\pm0.3)\times10^{-5}\,{\rm Mpc}^{-3}$ |
| Combined low-sSFR number density | 2.0e-5 | 0.3e-5 | Mpc^-3 | 0 | a space density of $(2.0\pm0.3)\times10^{-5}\,{\rm Mpc}^{-3}$ |
| Average t_quench | 330 | 30 | Myr | 0 | the average $t_{\rm quench}$ is $330\pm30\,{\rm Myr}$ |

## Qualitative findings

- ALMA non-detections of nearly all UVJ-quiescent galaxies rule out strong dust-obscured starbursts; dusty-quiescent (red, below-threshold) galaxies are mostly ALMA detected and unreliable.  
  > "From this we conclude that the vast majority of the dusty-quiescent galaxies are not robustly quiescent." (6.3.1)

## Claim tuples

- H: UVJ selection yields genuinely quiescent galaxies at z>3 | E: MOSFIRE spectroscopy plus SED modeling and archival ALMA of 24 candidates | R: ~20% contamination from interlopers and high-EW [OIII] emitters; ALMA stack non-detection | F: UVJ selection is efficient with ~80% purity | **supported**
- H: Models reproduce the observed number density of z>3 quiescent galaxies | E: Compared with SAMs and hydro simulations | R: All but MERAXES one to two orders of magnitude too low; MERAXES factor two low | F: Quenching/formation too late in models | **supported**

## Reasoning

- Why this data: Archival ALMA used to identify dusty star-forming interlopers among candidates.  
  > "We first use archival ALMA data to identify dust-obscured star-forming galaxies" (6.3.1)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA coverage covers only part of the sample; contamination must be statistically extrapolated.  
  > "We statistically take this into account later for the eight galaxies lacking ALMA coverage." (6.3.1)
- Caveat (inferred, ours): ALMA is a minor component; detection depends on heterogeneous archival depths
- Caveat (inferred, ours): assumed 20% ALMA detection rate for uncovered galaxies
- Caveat (inferred, ours): small sample statistics

## Reproducibility

- Data public (paper): ALMA data from the public archive; MOSFIRE tables at CDS  
  > "We cross matched our sample of quiescent galaxies with the ALMA archive" (2.6 Archival ALMA observations)
- Products in archive: _not stated_
- Code: FAST++ and slinefit are on GitHub; phy++ library  
  > "<https://github.com/cschreib/slinefit>" (footnote 4)
- Missing: ALMA reduction details
- Missing: private-communication model outputs (MERAXES, MUFASA)
- Missing: MOSFIRE raw data access
- Data volume (inferred): ~100s GB for ALMA archival EBs across 10 projects; plus MOSFIRE data
- Score (inferred): 3/5, ALMA part is small and processing is lightly described; the main results depend on MOSFIRE and SED modeling.
- Rediscovery candidate: no, ALMA processing details missing and main results rely on non-ALMA data and private model outputs.

## Links

- Method: (cite: schreiber2017) (ALMA program 2013.1.01292.S and uvmodelfit flux method)
- Companion: (cite: glazebrook2017) (First MOSFIRE confirmation of z~3.7 QG)
- Companion: (cite: schreiber2018) (ZF-COS-20115 ALMA de-blending, SFH method)
- Related: ZFOURGE
- Related: 3D-HST
- Related: CANDELS
- Related: MOSDEF
- Related: MOSEL

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
