# First JVLA Radio Observation on PDS 70

`2024ApJ...972..163L` | The Astrophysical Journal 2024 | first author: Liu, Hauyu Baobab | arXiv: 2406.19843 | DOI: 10.3847/1538-4357/ad5dab

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What emission mechanisms dominate the 10-48 GHz SED of PDS 70 (grown dust, free-free, or spinning nanometer-sized dust)?  
  > "Section 4 discusses our hypotheses of the dominant emission mechanisms at 18–48 GHz." (4 Discussion)
- Target **PDS 70**: coordinates RA 14 08 10.150, Dec -41 23 52.5 (J2000; JVLA pointing center)  
  > "at $\sim$113 pc distance ((cite: Gaia_2023))" (1 Introduction); "The pointing and phase referencing centers were R.A. (J2000)$=$14$^{\mbox{\scriptsize s}}$08$^{\mbox{\scriptsize m}}$10.150$''$" (2.1 JVLA); z/distance ~113 pc  
  > "at $\sim$113 pc distance ((cite: Gaia_2023))" (1 Introduction); "The pointing and phase referencing centers were R.A. (J2000)$=$14$^{\mbox{\scriptsize s}}$08$^{\mbox{\scriptsize m}}$10.150$''$" (2.1 JVLA); distance from Gaia (Gaia Collaboration 2023)  
  > "at $\sim$113 pc distance ((cite: Gaia_2023))" (1 Introduction); "The pointing and phase referencing centers were R.A. (J2000)$=$14$^{\mbox{\scriptsize s}}$08$^{\mbox{\scriptsize m}}$10.150$''$" (2.1 JVLA)

## Data provenance

- ALMA projects: 2022.1.01477.S
- bands: ALMA Bands 3 and 4; JVLA X, K, Ka, Q  
  > "We have carried out the ALMA Bands 3 (89.6–93.4 GHz/101.6–105.4 GHz) and 4 (137.0–138.9 GHz/149.0–152.9 GHz) standard FDM continuum observations" (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA C43-5; JVLA D (K, Q), DnC (Ka), moving array (X)  
  > "in the C43-5 array configuration" (2.2 ALMA); "The K and Q bands observations were carried out in the most compact (D) array configuration." (2.1 JVLA)
- baselines: _not stated_
- angular resolution: ALMA B3 0.49''x0.45''; B4 0.43''x0.33''  
  > "0.49$''$$\times$0.45$''$; $-$30$^{\circ}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: ALMA rms 18 uJy/beam (B3), 44 uJy/beam (B4)  
  > "0.43$''$$\times$0.33$''$; 44$^{\circ}$                                               | 44" (Table 1)
- time on source: _not stated_
- observing dates: ALMA 2023-Mar-25/26; JVLA 2019 Nov to 2020 Jan  
  > "2023-Mar-26 | 3" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **JVLA**: X, K, Ka, Q band continuum (project 19B-023)  
  > "in 2019 (Project code: 19B-023, PI: Hauyu Baobab Liu)" (2.1 JVLA)
- External data: DSHARP-default dust opacity table and SED equations  
  > "we quoted the DSHARP-default opacity and the Equations (10)–(20) presented in (cite: Birnstiel2018ApJ...869L..45B)" (7.1 Grown dust) [from (cite: Birnstiel2018ApJ...869L..45B)]
- External data: Spinning dust empirical SED formula  
  > "We quote Equation (15) of (cite: Hoang2018ApJ...862..116H) to represent the SED of the spinning nanometer-sized dust particles." (7.3 Spinning nanometer-sized dust) [from (cite: Hoang2018ApJ...862..116H)]

## Processing

### Calibration

- pipeline or manual: Manual calibration  
  > "We manually calibrated the ALMA data following the standard strategy" (2.2 ALMA)
- casa version: CASA 6.4.1  
  > "using CASA 6.4.1" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C286 (JVLA); J1427-4206 (ALMA)  
  > "3C286/3C286/J1427-4206" (Table 1)
- flux scale uncertainty: 5% nominal for ALMA  
  > "nominally assuming a 5% absolute flux error" (Table 2)
- self calibration: gain-phase self-calibration on ALMA data  
  > "In addition, we performed gain-phase self-calibration." (2.2 ALMA)

### Imaging

- task: CASA tclean, mfs nterms=1  
  > "We performed multi-frequency synthesis (mfs; nterms$=$1) imaging ((cite: Rau2011A&A...532A..71R)) using the CASA `tclean` task." (2.1 JVLA)
- deconvolver: _not stated_
- weighting robust: Briggs Robust = 2.0  
  > "We adopted the Briggs Robust$=$2.0 weighting to minimize the RMS noises in Jy beam$^{-1}$ units." (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum made by binning line-free channels  
  > "We produced continuum data by binning the line-free channels." (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Cell size, image size, masks and clean thresholds
- Line-free channels for ALMA
- Self-calibration solution intervals
- ALMA flux calibrator flux values
- Procedure for visibility 2D Gaussian fitting (software, fixed parameters)
- Dust model fiducial inclination and how the fit was chosen (done by eye)

## Analysis recipe

1. **Calibrate and image JVLA and ALMA continuum**: Manual CASA calibration, tclean mfs imaging with Briggs robust 2  
  > "We manually calibrated the JVLA data following the standard strategy (see below) using the Common Astronomy Software Applications" (2.1 JVLA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities**: JVLA: peak intensity (lower limit) and 2D Gaussian fit in visibility domain (upper limit); ALMA: integrate inner 4'' square  
  > "We compared two methods for measuring flux densities from the JVLA images: (i) reading the peak intensities in the image domain, and (ii) performing 2D Gaussian fittings in the visibility domain." (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Varying ALMA square region changes flux by less than 5%  
  > "varying the location and shape of the square region does not change the obtained flux density by more than the nominal 5% absolute flux errors we quoted." (3 Results)
3. **Compare SED with dust, free-free and spinning-dust models**: Eddington-Barbier dust slab SED with DSHARP opacities; free-free slab; empirical spinning dust formula; models adjusted to match data  
  > "we adopted $a_{\mbox{\scriptsize max}}=$1.5 mm as a working hypothesis" (4.1.1)
   - parameter: amax=1.5 mm; Sigma_dust=5.0 g cm^-2; Omega=2e-12 sr; q=3.5; amin=1e-4 mm  
  > "were chosen to be 5.0 g cm$^{-2}$ and 2$\cdot$10$^{-12}$ Sr, respectively" (4.1.1)
   - parameter: Spinning dust: nu_pk=21 GHz, F_sd,0=0.07 mJy  
  > "We adopted $\nu_{pk}=$21 GHz and $F_{sd,0}=$0.07 mJy." (7.3)
   - assumption: Dust temperature 20 K  
  > "We assumed a 20 K mean dust temperature" (4.1.1)
   - fitting: Not a formal fit; parameters chosen by hand  
  > "To match the observed $\gtrsim$30 GHz SED, in the fiducial model, the dust column density ($\Sigma_{\mbox{\scriptsize dust}}$) and solid angle ($\Omega$) were chosen to be 5.0 g cm$^{-2}$ and 2$\cdot$10$^{-12}$ Sr" (Discussion: Emission at ≳30 GHz)
   - validation: Check against ALMA 97.5/145 GHz fluxes and spectral indices  
  > "the flux densities at 97.5 GHz and 145 GHz will immediately exceed what have been measured in the ALMA observations" (4.1.1)

## Software

- **CASA** 6.4.1: Calibration and tclean imaging  
  > "(CASA 6.4.1; (cite: McMullin2007ASPC..376..127M))" (2.1 JVLA)
- **astropy** : listed in software  
  > "astropy (cite: 2013A&A...558A..33A; astropy2018AJ....156..123A; astropy2022ApJ...935..167A), Numpy (cite: VanDerWalt2011)," (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 33–44 GHz | 5 | ±1 | dimensionless | 3 | The spectral indices ($\alpha$) are 5$\pm$1 and 0.6$\pm$0.2 at 33–44 GHz and 22–33 GHz, respectively. |
| Spectral index 22–33 GHz | 0.6 | ±0.2 | dimensionless | 3 | 0.6$\pm$0.2 at 33–44 GHz and 22–33 GHz |
| Lower limit spectral index 10–22 GHz | 1.7 | not stated | dimensionless | 3 | we derived a lower limit of the 10–22 GHz spectral index to be 1.7 |
| ALMA 97.5 GHz flux density | 4.1 | 0.2 | mJy | 2 | 97.5 GHz           / 4.1$\pm$0.2$^{c}$ |
| ALMA 145 GHz flux density | 15 | 0.75 | mJy | 2 | 145 GHz            / 15$\pm$0.75$^{c}$ |
| JVLA 22 GHz flux density (Nov 17, Gaussian fit) | 122 | 16 | uJy | 2 | 18–26 GHz (Nov.17) / 110$\pm$16         / 122$\pm$16 |
| JVLA 33 GHz flux density (Gaussian fit) | 148 | 23 | uJy | 2 | 29–37 GHz          / 105$\pm$23         / 148$\pm$23 |
| JVLA 44 GHz flux density (Gaussian fit) | 665 | 100 | uJy | 2 | 40–48 GHz          / 393$\pm$100        / 665$\pm$100 |
| Grown dust mass in fiducial model | ~180 | not stated | Earth masses | 3 | The overall dust mass in this grown dust component is $\sim$180 $M_{\oplus}$ |

## Qualitative findings

- ALMA Band 3/4 images show an azimuthally asymmetric ring with a bright northwest crescent  
  > "showing a bright crescent in the northwest" (3 Results)

## Claim tuples

- H: Is the >30 GHz emission grown-dust thermal emission? | E: Compare SED with DSHARP dust slab models | R: 33–44 GHz index 5±1 fit with amax~1.5 mm | F: Optically thin grown dust with amax >~1 mm dominates at 33–44 GHz | **supported**
- H: Can free-free emission alone explain 22–33 GHz? | E: Compare with free-free models and X band non-detection | R: Low index plus X-band upper limit is hard to match | F: Spinning nanometer dust likely dominates at 22–33 GHz, with possible free-free contribution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free-free only rejected; radio variability considered unlikely  
  > "Due to these reasons, we disfavor interpreting the $\lesssim$30 GHz emission only with free-free emission." (4.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Q band hard to calibrate and marginal; detailed spinning-dust model beyond scope  
  > "Usually, the JVLA Q band (40–48 GHz) observations are the most difficult to calibrate." (4.1.1)
- Caveat (inferred, ours): SED models tuned by hand with no formal fit or uncertainties
- Caveat (inferred, ours): Unresolved JVLA sources with poor beams (shadowing); Q band marginal
- Caveat (inferred, ours): Low significance of the key detections

## Reproducibility

- Data public (paper): ALMA project code given; JVLA project 19B-023  
  > "(Project code: 19B-023, PI: Hauyu Baobab Liu)" (2.1 JVLA)
- Products in archive: _not stated_
- Missing: Image parameters, masks, self-cal details
- Missing: Model code not released
- Data volume (inferred): ~50-100 GB (ALMA) plus JVLA ~ tens of GB
- Score (inferred): 3/5, Data identified and workflow outlined, but many imaging details missing and the SED modelling is manual.
- Rediscovery candidate: no, Recipe lacks details and model tuning is ad hoc.

## Links

- Method: (cite: Birnstiel2018ApJ...869L..45B) (dust SED and opacity model)
- Method: (cite: Hoang2018ApJ...862..116H) (spinning dust formula)
- Companion: (cite: Benisty2021ApJ...916L...2B) (ALMA high-frequency images of PDS 70 ring and crescent)
- Related: JVLA 19B-023

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 63,
  "stated": 35,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
