# WL 17: A Young Embedded Transition Disk

`2017ApJ...840L..12S` | The Astrophysical Journal Letters 2017 | first author: Sheehan, Patrick D. | arXiv: 1704.07916 | DOI: 10.3847/2041-8213/aa6df8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is WL 17 a young embedded Class I disk with a central hole, or an older Class II transition disk extincted by foreground material?  
  > "whether it is a young protostar still embedded in its natal envelope, which has cleared out a hole despite its young age, or whether it is an older, disk-only source" (Introduction)
- Target **WL 17**: coordinates _not stated_; z/distance 137 pc  
  > "WL 17 is a M3 protostar in the L1688 region of the $\rho$ Ophiuchus molecular cloud (cite: Doppmann2005), located a distance of 137 pc away (cite: OrtizLeon2017)." (Introduction); distance from Ortiz-León et al. 2017  
  > "WL 17 is a M3 protostar in the L1688 region of the $\rho$ Ophiuchus molecular cloud (cite: Doppmann2005), located a distance of 137 pc away (cite: OrtizLeon2017)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00761.S
- bands: Band 3  
  > "The observations were done with the Band 3 receivers" (2.1 ALMA)
- frequencies and spectral setup: four basebands centered at 90.5, 92.5, 102.5, 104.5 GHz, each 128 15.625 MHz channels  
  > "the four basebands were tuned for continuum observations centered at 90.5, 92.5, 102.5, 104.5 GHz, each with 128 15.625 MHz channels" (2.1 ALMA)
- continuum bandwidth: 8 GHz total  
  > "In all the observations had 8 GHz of total continuum bandwidth." (2.1 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 m – 15.3 km  
  > "with baselines ranging from 14 m – 15.3 km" (2.1 ALMA)
- angular resolution: 0.06" by 0.05", P.A. 81.9 deg  
  > "The resulting image has a beam of size 0.06" by 0.05" with a P.A. of 81.9$^{\circ}$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 36 uJy/beam  
  > "The rms of the image is 36 $\mu$Jy/beam." (2.1 ALMA)
- time on source: _not stated_
- observing dates: 31 October 2015 to 17 April 2016, three tracks  
  > "WL 17 was observed with ALMA in three tracks from 31 October 2015 to 17 April 2016" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **Spitzer (IRAC, MIPS, IRS via CASSIS)**: Mid-infrared photometry and IRS spectrum for the SED  
  > "The data includes *Spitzer* IRAC and MIPS photometry as well as fluxes from the literature at a range of wavelengths" (2.2 SED from the Literature)
- External data: Broadband SED photometry compiled from the literature  
  > "We compile a broadband spectral energy distribution (SED) for WL 17 from a thorough literature search." (2.2 SED from the Literature) [from Wilking1983; Lada1984; Greene1992; Andre1994; Strom1995; Barsony1997; Evans2009; Gutermuth2009; etc.]
- External data: Calibrated Spitzer IRS spectrum from CASSIS  
  > "We also include the the SL, SH, and LH calibrated Spitzer IRS spectrum from the CASSIS database in our SED" (2.2 SED from the Literature) [from (cite: Lebouteiller2011; Lebouteiller2015)]

## Processing

### Calibration

- pipeline or manual: standard CASA reduction with listed calibrators  
  > "We reduce the data in the standard way with the `CASA` software package and the calibrators listed in Table" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "we image the data by Fourier transforming the visibilities with the `CLEAN` routine" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We use Briggs weighting with a robust parameter of 0.5" (2.1 ALMA)
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
- final beam: 0.06" x 0.05", P.A. 81.9 deg  
  > "The resulting image has a beam of size 0.06" by 0.05" with a P.A. of 81.9$^{\circ}$." (2.1 ALMA)
- final rms: 36 uJy/beam  
  > "The rms of the image is 36 $\mu$Jy/beam." (2.1 ALMA)

### Inherited from earlier work

- Radiative transfer model setup and dust opacities  
  > "We give a brief description of the models here, but refer to (cite: Sheehan2014) for a more detailed account." (3 Results) [from (cite: Sheehan2014)]
- Envelope density profile  
  > "embed the disk in a rotating collapsing envelope (cite: Ulrich1976)" (3 Results) [from (cite: Ulrich1976)]
- Extinction law  
  > "using the (cite: McClure2009) extinction law" (3 Results) [from (cite: McClure2009)]

### Not stated but needed to reproduce (our reading)

- CASA version and flux calibrator details
- Self-calibration, cell size, image size, masking and clean threshold
- Which calibrator served which role per track
- Model fitting procedure/optimizer for the disk+extinction best fit and parameter priors/ranges
- Exact data used to compute visibility chi2 (binning, weights)
- Coordinates of WL 17
- Which code (RADMC-3D vs Hyperion) was used for which model

## Analysis recipe

1. **Calibrate and image ALMA 3 mm data**: Standard CASA calibration, CLEAN imaging with Briggs weighting  
  > "We use Briggs weighting with a robust parameter of 0.5" (2.1 ALMA)
   - software: CASA
   - parameter: robust = 0.5  
  > "We use Briggs weighting with a robust parameter of 0.5" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compile SED**: Literature photometry plus Spitzer IRS spectrum scaled by factor 3, 10% flux uncertainty, IRS sampled at 25 points; WISE excluded  
  > "We find that we need to scale the IRS spectrum by a factor of 3 to align it with the IRAC/MIPS photometry for the system." (2.2 SED from the Literature)
   - parameter: 10% uncertainty on all fluxes  
  > "we assume a 10% uncertainty on all flux measurements when computing $\chi^2$" (2.2 SED from the Literature)
   - fitting: _not stated_
   - validation: IRAC/MIPS fluxes independently reproduced by two groups  
  > "The IRAC and MIPS flux measurements were also independently reproduced by two different groups using separate datasets" (2.2 SED from the Literature)
3. **Fit disk+foreground extinction model to visibilities and SED**: Monte Carlo radiative transfer synthetic visibilities and SEDs compared with data in the un-averaged visibility plane  
  > "to produce synthetic visibilities and SEDs and attempt to match the data with the models" (3 Results)
   - software: RADMC-3D, Hyperion
   - parameter: Free: L*, Mdisk, alpha, beta, h0, Rgap, delta, Rdisk, inclination, PA, amax, A_K  
  > "$\alpha$, $\beta$, $h_0$, and the disk mass $M_{disk}$ are also left as free parameters, as are the inclination and position angle of the system." (3 Results)
   - assumption: M3 central star; distance 137 pc; McClure 2009 extinction law  
  > "Our model assumes a central protostar with a M3 spectral type (cite: Doppmann2005), although we allow the luminosity of the protostar, $L_*$, to vary." (3 Results)
   - fitting: best fit disk+extinction model; method not described  
  > "We show the best fit disk+extinction model in Figure [2](#fig:models)" (3 Results)
   - validation: chi2 for visibilities and SED  
  > "we have computed the $\chi^2$ value for each of the models listed in Table" (4 Discussion & Conclusion)
4. **Test disk+envelope model**: Add Ulrich rotating collapsing envelope, parameters adjusted by hand starting from disk+extinction disk parameters  
  > "These models were found by taking the disk+extinction model disk parameters, adding an envelope, and adjusting the parameters by hand to find models that produce better $\chi^2$ values." (3 Results)
   - software: RADMC-3D, Hyperion
   - parameter: Rc ~ Rdisk; envelope inner radius 0.1 AU  
  > "This makes the most sense physically if $R_c \sim R_{disk}$, so we provide this constraint to our modeling." (3 Results)
   - fitting: hand adjustment, no optimization  
  > "These models are not “best fits" because no optimization was done" (3 Results)
   - validation: chi2 comparison of visibilities and SED across models  
  > "Only the disk+envelope models can well reproduce both the visibilities and the broadband SED simultaneously." (4 Discussion & Conclusion)

## Software

- **CASA** : Data reduction and CLEAN imaging  
  > "We reduce the data in the standard way with the `CASA` software package" (2.1 ALMA)
- **RADMC-3D** : Monte Carlo radiative transfer models  
  > "Monte Carlo radiative transfer codes `RADMC-3D` and `Hyperion`" (3 Results)
- **Hyperion** : Monte Carlo radiative transfer models  
  > "Monte Carlo radiative transfer codes `RADMC-3D` and `Hyperion`" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cavity diameter | ~0.2 (27 AU across, ~13 AU radius) | not stated | arcsec | 1 | a hole measuring $\sim0.2''$ in diameter in the center |
| Central peak emission in hole | ~250 | not stated | uJy | 1 | Emission at the center of the hole peaks at $\sim~250$ $\mu$Jy |
| Disk+extinction chi2 SED | 325 | not stated | dimensionless | 3 | Disk+extinction / 6.2 / 0.06 / 11.6 / 22.7 / 0.11 / -0.24 / 1.0 / 0.02 / ... / ... / 28 / 82.4 / 0.3 / 4.2 / 1078 / 325 |
| Disk+envelope (green) chi2 SED | 112 | not stated | dimensionless | 4 | Disk+envelope (green) / 0.5 / 0.05 / 11.6 / 22.7 / 0.15 / 0.0 / 0.75 / 0.011 / $3\times10^{-5}$ / 25 / 28 / 82.4 / 10 / 0.5 / 1067 / 112 |
| Extinction required by disk+extinction model | A_K ~ 4 (A_V ~ 30) | not stated | mag | 3 | $A_K \sim 4$ ($A_V \sim 30$ for the (cite: McClure2009) extinction law) is needed to properly extinct the near-infrared SED. |

## Qualitative findings

- WL 17 is likely a young source still embedded in a remnant envelope; the foreground extinction scenario fails to fit the SED.  
  > "we suggest that WL 17 is a young source still embedded in the remnants of its natal envelope." (4 Discussion & Conclusion)

## Claim tuples

- H: WL 17 is a Class II transition disk extincted by foreground material | E: Fit disk+foreground-extinction RT model to ALMA 3 mm visibilities and SED | R: Visibilities fit well but SED chi2 325 and A_V ~30 needed, mid-IR under-predicted | F: Foreground extinction model is disfavored | **supported**
- H: WL 17 is an embedded disk with a hole | E: Disk+envelope RT models compared with visibilities and SED | R: Better SED chi2 (112-172) with similar visibility chi2 | F: WL 17 is a young embedded transition disk; envelope mass/radius degenerate | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Class II disk with foreground extinction rejected due to poor SED fit and high required A_V  
  > "Such high extinction seems unlikely to come from foreground extinction from nearby star forming regions." (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Envelope mass and radius are degenerate; data cannot distinguish compact low-mass from large massive envelopes  
  > "our modeling cannot well distinguish between compact low mass envelopes and larger and more massive envelopes." (3 Results)
- Caveat (inferred, ours): Disk+envelope models hand-tuned, not optimized, while disk+extinction was fit, so chi2 comparison is not like-for-like
- Caveat (inferred, ours): Visibility chi2 ~1070 indicates poor absolute fits
- Caveat (inferred, ours): IRS spectrum scaled by factor 3 ad hoc
- Caveat (inferred, ours): Hole origin not discriminated

## Reproducibility

- Data public (paper): ALMA project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00761.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version, imaging parameters, self-cal
- Missing: Model optimization details
- Missing: Full model parameter ranges
- Data volume (inferred): Large: three long-baseline Band 3 tracks, likely tens of GB raw
- Score (inferred): 3/5, Data identified and key model parameters tabulated, but calibration/imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete and model fitting is partly by hand with RT codes.

## Links

- Method: (cite: Sheehan2014) (Radiative transfer model and dust opacities)
- Companion: (cite: Sheehan2017b) (ALMA survey of embedded protostars in Ophiuchus (in prep))
- Related: ALMA survey of young embedded protostars in Ophiuchus

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 42,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
