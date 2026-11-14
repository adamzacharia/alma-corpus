# The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. IV. Phosphorus-bearing molecules and their relation to shock tracers

`2024A&A...682A..74F` | Astronomy and Astrophysics 2024 | first author: Fontani, F. | arXiv: 2311.13367 | DOI: 10.1051/0004-6361/202348219

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Are P-bearing molecules (PN, PO) in the hot molecular core G31.41+0.31 associated with shock tracers (SiO, SO, SO2, SiS), and what does this say about P chemistry?  
  > "We study P-bearing molecules, as well as some shock tracers, towards one of the chemically richest hot molecular core, G31.41+0.31" (abstract)
- Target **G31.41+0.31**: coordinates RA(J2000)=18h47m34.312s, Dec(J2000)=-01d12m45.9s (pointing centre)  
  > "located at heliocentric distance of 3.75 kpc (Immer et al. (cite: Immer19)" (Introduction); "The pointing centre of the observations is R.A.(J2000)=18$^{\rm h}$47$^{\rm m}$34.$^{\prime\prime}$312 and Dec.(J2000)=$-$01$^{\circ}$12$^{\prime}$45.$^{\prime\prime}$9." (Observations and data reduction); z/distance 3.75 kpc  
  > "located at heliocentric distance of 3.75 kpc (Immer et al. (cite: Immer19)" (Introduction); "The pointing centre of the observations is R.A.(J2000)=18$^{\rm h}$47$^{\rm m}$34.$^{\prime\prime}$312 and Dec.(J2000)=$-$01$^{\circ}$12$^{\prime}$45.$^{\prime\prime}$9." (Observations and data reduction); distance from Immer et al. 2019  
  > "located at heliocentric distance of 3.75 kpc (Immer et al. (cite: Immer19)" (Introduction); "The pointing centre of the observations is R.A.(J2000)=18$^{\rm h}$47$^{\rm m}$34.$^{\prime\prime}$312 and Dec.(J2000)=$-$01$^{\circ}$12$^{\prime}$45.$^{\prime\prime}$9." (Observations and data reduction)

## Data provenance

- ALMA projects: 2017.1.00501.S, 2013.1.00489.S
- bands: Band 3, 84.05-115.91 GHz  
  > "obtaining an unbiased spectral survey in Band 3 from 84.05 GHz up to 115.91 GHz" (Observations and data reduction)
- frequencies and spectral setup: 0.49 MHz channels, ~1.6 km/s at 90 GHz  
  > "The frequency resolution is 0.49 MHz, corresponding to a velocity resolution of $\sim$1.6 km s$^{-1}$ at 90 GHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.2 arcsec (~4500 au)  
  > "The final angular resolution is 1.$^{\prime\prime}$2 ($\sim$4500 au)." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 5, P.I. M.T. Beltrán  
  > "project 2017.1.00501.S, P.I.: M.T. Beltrán" (Observations and data reduction)
- Line: PN N=2-1 (93.9782-93.9823 GHz (hyperfine))
- Line: PO J=5/2-3/2, Omega=1/2 (4 lines) (108.9984-109.2812 GHz)
- Line: SiO J=2-1 (86.8470 GHz)
- Line: SiS J=5-4, 6-5 (90.7716, 108.9243 GHz)
- Line: SO several (86.0940-109.2522 GHz)
- Line: SO2 3(1,3)-2(0,2), 16(2,14)-15(3,13), 10(1,9)-10(0,10) (104.0294-104.2393 GHz)
- Other facility **ALMA Band 6 SiO J=5-4 (Beltrán et al. 2018)**: High-resolution SiO J=5-4 wing maps (~0.22 arcsec)  
  > "we show the maps of the high-velocity wings of the SiO $J=5-4$ line published in (cite: Beltran18)." (3.1.1 PN, PO and SiO)
- External data: Spectroscopic parameters from CDMS  
  > "All parameters are taken from the Cologne Database for Molecular Spectroscopy" (Table 1) [from Endres et al. 2016 (cite: Endres16)]
- External data: Solar isotopic ratios 28Si/29Si=19.7 and 32SO/34SO=22.5  
  > "The reference Solar values for $^{28}$Si/$^{29}$Si and $^{32}$SO/$^{34}$SO are 19.7 (cite: AeG89) and 22.5 (cite: Lodders03), respectively." (3.3.3 Opacity of SiO and SO lines) [from Anders & Grevesse 1989; Lodders 2003]
- External data: Outflow orientation and driving sources  
  > "The orientation of the six outflows in the region and the position of their driving sources has been recently improved with ALMA" (3.1.1 PN, PO and SiO) [from Beltrán et al. 2022 (cite: Beltran22)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5%  
  > "The uncertainty on the flux calibration is $\sim 5\%$." (Observations and data reduction)
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
- smoothing: PO spectrum in region 2 smoothed in velocity by factor 2  
  > "The spectrum towards this position was smoothed in velocity by a factor 2 to increase the sensitivity." (3.2.2 Tentative detection of PO)
- final beam: 1.2 arcsec  
  > "The final angular resolution is 1.$^{\prime\prime}$2 ($\sim$4500 au)." (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction (calibration, baseline subtraction, cleaning, line identification)  
  > "For more details on the data reduction (calibration, baseline subtraction, cleaning and line identification) we refer to (cite: Mininni20)." (Observations and data reduction) [from Mininni et al. 2020 (cite: Mininni20)]
- Flux-to-brightness-temperature conversion  
  > "The conversion from flux density units to temperature units has been performed using Eq.(1) in (cite: Fontani21)" (3.2.1 Main isotopologues) [from Fontani et al. 2021 (cite: Fontani21)]
- Opacity estimation in madcuba  
  > "madcuba estimates the line opacities as explained in (cite: Martin19)" (3.3.3 Opacity of SiO and SO lines) [from Martín et al. 2019 (cite: Martin19)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, clean threshold)
- Continuum subtraction and line-free channels
- Array configurations, baselines, time on source, observing dates
- How the extraction regions 1 and 2 were defined (aperture size/shape)
- Role of project 2013.1.00489.S
- Details of the Fig.1 moment-map procedure

## Analysis recipe

1. **Integrated intensity maps**: Integrate PN, SiO and other lines over 85.7-105.8 km/s; compare morphology and pixel-by-pixel ratios  
  > "map of PN $J=2-1$ (panel (a)) integrated in the velocity range with emission above $3\sigma$ rms, namely 85.7–105.8 km s$^{-1}$" (3.1.1 PN, PO and SiO)
   - software: madcuba
   - fitting: _not stated_
   - validation: Compared with SiO J=5-4 high resolution maps  
  > "In panel (d) of Fig. [1](#fig:PN-integ) we show the maps of the high-velocity wings of the SiO $J=5-4$ line published in (cite: Beltran18)." (3.1.1 PN, PO and SiO)
2. **Extract spectra at regions 1, 2 and hot core**: Spectra in brightness temperature from the two PN peaks and the 20 sigma 3 mm continuum contour  
  > "We chose the 3 mm continuum contour at 20$\sigma$ rms to disentangle the emission of the hot core from that of the ultracompact Hii region" (3.1.1 PN, PO and SiO)
   - software: madcuba
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE fits for column densities and Tex**: SLIM AUTOFIT of multiple transitions for SO, 34SO, SO2, SiS, SiO; free V, FWHM, Tex, Ntot, fixed filling beam  
  > "Through its AUTOFIT function, SLIM produces the synthetic spectrum that best matches the data assuming LTE." (3.3.1 SO, 34SO, SO2, SiS, and SiO)
   - software: madcuba
   - assumption: Emission fills the beam (theta_S fixed)  
  > "we can safely assume that the emission fills the telescope beam" (3.3.1 SO, 34SO, SO2, SiS, and SiO)
   - fitting: LTE AUTOFIT; some Tex fixed (34SO region 1 at 58 K)  
  > "For $^{34}$SO, in region "1" the fit converged leaving $V$, $FWHM$, and $N_{\rm tot}$ free, but we had to fix $T_{\rm ex}$. The best-fit $T_{\rm ex}$ obtained by visual inspection is 58 K." (3.3.1 SO, 34SO, SO2, SiS, and SiO)
   - validation: _not stated_
4. **PN and PO column densities**: Fit PN at Tex range from other tracers (26-75 K region 1, 12-30 K region 2); PO fitted with PN Tex, FWHM, V; upper limit in region 1  
  > "we derive the best-fit in a range of $T_{\rm ex}$ based on the minimum and maximum values obtained from the other tracers." (3.3.2 PN and PO)
   - software: madcuba
   - fitting: LTE  
  > "We used madcuba to fit simultaneously the four transitions. The fitting method, which assumes local thermodynamic equilibrium (LTE) conditions" (3.2.2 Tentative detection of PO)
   - validation: Hyperfine-included fit gives consistent FWHM  
  > "derived in all cases FWHMs slightly smaller but consistent within the errors with the values obtained neglecting it." (3.3.2 PN and PO)
5. **Opacity check**: Compare madcuba tau with isotopologue intensity ratios (28SiO/29SiO, 32SO/34SO)  
  > "the intensity ratio between the $^{28}$SiO and the $^{29}$SiO lines is $^{28}$SiO/$^{29}$SiO$\sim 8$ in region "1" and $^{28}$SiO/$^{29}$SiO$\sim 20$ in region "2"." (3.3.3 Opacity of SiO and SO lines)
   - software: madcuba
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **madcuba** : Spectral analysis, LTE fitting (SLIM/AUTOFIT)  
  > "The spectral analysis has been performed with the MAdrid Data CUBe Analysis (madcuba" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PN Ntot region 1 (Tex=26 K) | 1.3e13 | 0.1e13 | cm^-2 | 4 | /  / PN / 9.7(0.9) / 94.8(0.4) / $1.3(0.1)\times 10^{13}$ / 26 / 0.01 / |
| PN Ntot region 2 (Tex=12 K) | 1.5e13 | 0.1e13 | cm^-2 | 4 | / PN / 11.7(1.2) / 94.2(0.5) / $1.5(0.1)\times 10^{13}$ / 12 / 0.01 / |
| SiO Ntot region 1 | 3.6e14 | 0.1e14 | cm^-2 | 3 | / SiO / 12.6(0.4) / 95.1(0.2) / $3.6(0.1)\times 10^{14}$ / 26.4(0.2) / 0.9 / |
| SiO Ntot region 2 | 1.8e14 | 0.2e14 | cm^-2 | 3 | / SiO / 11.5(0.6) / 93.0(0.3) / $1.8(0.2)\times 10^{14}$ / 11.6(0.6) / 0.7 / |
| PO/PN region 2 | ~0.6-0.9 | not stated | dimensionless | 4 | the PO/PN ratio in region "2", where PO is tentatively detected, is $\sim 0.6-0.9$ |
| PO integrated-line S/N region 2 | ~6 | not stated | dimensionless | 4 | we obtain a signal-to-noise ratio of $\sim 6$. |

## Qualitative findings

- PN emission is tightly associated with SiO and absent in the hot core, implying shock chemistry origin  
  > "Our study firmly confirms previous observational evidence that PN emission is tightly associated with SiO and it is likely a product of shock-chemistry" (abstract)

## Claim tuples

- H: PN is associated with shocks traced by SiO rather than hot core chemistry | E: Compare PN, SiO, S-bearing maps and spectra | R: PN and SiO similar in morphology and profile; PN undetected in hot core | F: PN is a product of shock chemistry | **supported**
- H: Column density ratios to PN differ between regions | E: LTE fits in regions 1 and 2 | R: SiO/PN constant; SO/PN, SiS/PN, SO2/PN decrease by ~an order of magnitude | F: SiO and PN share a common origin | **supported**
- H: PO/PN ratio consistent with pure shock models | E: Tentative PO fit in region 2 | R: PO/PN ~0.6-0.9 | F: In line with pure shock models | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PH3 as main P carrier in the hot core rejected since PN and PO not clearly detected there  
  > "hence PH$_3$ does not seem to be the main P-carrier here." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single PN transition so Tex unconstrained; blending of SiS, PO, 29SiO lines in region 1; PO only tentative  
  > "For PN, we cannot derive $T_{\rm ex}$ from the data since we have only one transition." (3.3.2 PN and PO)
- Caveat (inferred, ours): PN Ntot depends on assumed Tex from other species
- Caveat (inferred, ours): LTE and beam-filling assumed
- Caveat (inferred, ours): Region definitions not specified
- Caveat (inferred, ours): Line blending in region 1 limits comparisons

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from ALMA project 2017.1.00501.S, acknowledged as used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.00489.S and ADS/JAO.ALMA$\#$2017.1.00501.S." (Acknowledgements)
- Missing: Calibration and imaging details (in Mininni et al. 2020)
- Missing: Region extraction apertures
- Missing: Exact madcuba version and fit settings
- Data volume (inferred): ~100-300 GB (Band 3 spectral survey, mosaic)
- Score (inferred): 3/5, Public data and a clear LTE fitting recipe, but reduction and extraction details are deferred to another paper.
- Rediscovery candidate: no, Processing details are inherited from Mininni et al. 2020 and region definitions are not given.

## Links

- Method: Mininni et al. 2020 (cite: Mininni20) (GUAPOS data reduction and source description)
- Method: Martín et al. 2019 (cite: Martin19) (madcuba software)
- Companion: López-Gallifa et al. 2023 (cite: LopezGallifa23) (Excitation analysis of hot core species in GUAPOS)
- Companion: Mininni et al. 2023 (cite: Mininni23) (GUAPOS COM analysis)
- Related: GUAPOS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 33,
  "rate": 0.471
 },
 "evidence_ok": true
}
```
