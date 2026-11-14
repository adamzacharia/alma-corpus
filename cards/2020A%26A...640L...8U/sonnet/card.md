# ALMA Deep Field in SSA22. A near-infrared-dark submillimeter galaxy at z = 4.0

`2020A&A...640L...8U` | Astronomy and Astrophysics 2020 | first author: Umehata, Hideki | arXiv: 2007.09887 | DOI: 10.1051/0004-6361/202038146

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the spectroscopic redshift and physical nature (stellar mass, SFR, ISM, gas content) of the near-infrared-dark ALMA-selected galaxy ADF22.A2, and is it a progenitor of quiescent galaxies?  
  > "In this letter, we report a secure redshift identification of a near-infrared-dark galaxy discovered by an ALMA deep survey." (Introduction)
- Target **ADF22.A2**: coordinates RA 22 17 36.11, Dec 00 17 36.70 (ICRS)  
  > "RA (ALMA, ICRS)      |        22 17 36.11" (Table 1); "Dec. (ALMA, ICRS)     |        00 17 36.70" (Table 1); z/distance z = 3.9913 ± 0.0008  
  > "RA (ALMA, ICRS)      |        22 17 36.11" (Table 1); "Dec. (ALMA, ICRS)     |        00 17 36.70" (Table 1); distance from CO(4-3) and [CI](1-0) lines in this work  
  > "RA (ALMA, ICRS)      |        22 17 36.11" (Table 1); "Dec. (ALMA, ICRS)     |        00 17 36.70" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00212.S, 2016.1.00543.S, 2017.1.00602.S, 2013.1.00162.S
- bands: Band 3 (two set-ups); Band 6 (1.1 mm) from earlier work  
  > "Band 3 observations of ADF22.A2 were performed at two frequency set-ups." (2 Observations)
- frequencies and spectral setup: 84.1–87.8 and 96.1–99.8 GHz (2015.1.00212.S, 2016.1.00543.S); 91.4–95.2 and 103.4–107.2 GHz (2017.1.00602.S)  
  > "at 84.1–87.8 GHz and 96.1–99.8 GHz" (2 Observations); "at 91.4–95.2 GHz and 103.4–107.2 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 36–45  
  > "Observations were carried out with 43-45 usable 12 m antennas" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Continuum beam 0.90 x 0.71 arcsec; tapered cubes ~1.3 arcsec  
  > "which have the synthesized beam $0^{\prime\prime}.90 \times 0^{\prime\prime}.71$ (P.A.$=-74$ deg)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS 44 uJy/beam  
  > "a typical root mean square (RMS) noise of 44 $\mu$Jy beam$^{-1}$" (2 Observations)
- time on source: 13.9 hours (13-point mosaic); 263 min for 2017.1.00602.S  
  > "These resulted in the total on-source time of 13.9 hours for a 13-point mosaic" (2 Observations); "The total on-source time was 263 min." (2 Observations)
- observing dates: 2016 Jul 21–Aug 19, 2017 May 7–Jul 4; 2018 Jan 18–20  
  > "between 2016 July 21 and 2016 August 19, and the latter one was between 2017 May 7 and 2017 July 4" (2 Observations)
- pi or archival as stated: PI Umehata (2015.1.00212.S, 2016.1.00543.S); PI Hayatsu (2017.1.00602.S)  
  > "project 2017.1.00602.S (PI. N. H. Hayatsu)" (2 Observations)
- Line: CO 4-3 (461.041 GHz)
- Line: [CI] 1-0 (492.160 GHz)
- Other facility **Subaru Suprime-Cam/MOIRCS, Spitzer IRAC, Herschel SPIRE, SCUBA2, JVLA**: Optical-to-radio photometry for SED fitting  
  > "We also use data taken by SPIRE ((cite: 2016MNRAS.460.3861K)), SCUBA2 ((cite: 2017MNRAS.465.1789G)), and JVLA ((cite: 2017ApJ...850..178A))." (Table 1 notes)
- External data: ALMA 1.1 mm flux density 2.02±0.02 mJy and band 6 photometry  
  > "with a flux density of $S_{\rm 1.1~mm}=2.02\pm0.02$ mJy ((cite: 2017ApJ...835...98U))" (2 Observations) [from (cite: 2017ApJ...835...98U)]
- External data: Optical-NIR and IRAC photometry compilation  
  > "MegaCam $U$-band, Suprime-Cam $B, V, R, i^{\prime},z^{\prime}$-band, MOIRCS $J, H, Ks$-band, and IRAC data are summarized in (cite: 2014MNRAS.440.3462U)." (Table 1 notes) [from (cite: 2014MNRAS.440.3462U)]
- External data: Averaged z>3 SMG SED templates and catalogs for comparison  
  > "averaged SEDs, which were derived for $z>3$ SMGs in the UDS field using the same code, magphys" (3.2) [from (cite: 2020MNRAS.tmp.1074D)]
- Simulation/model as data: PDR model grids of Kaufman et al. used for density and UV field  
  > "on the basis of the PDR model of (cite: 1999ApJ...527..795K) and (cite: 2006ApJ...644..283K)" (4 Discussion)

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "The data were processed using the standard casa pipeline." (2 Observations)
- casa version: 4.7.0, 4.7.2, 5.1.0, 5.4.0  
  > "versions 4.7.0, 4.7.2, 5.1.0, and 5.4.0" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas, J2148+0657, J2232+1143, Titan; J2148+0657 for 2017.1.00602.S  
  > "To set the absolute flux scale, Pallas, J2148+0657, J2232+1143 and Titan were observed." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The calibrated visibility data were used for imaging with the casa task tclean." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uvtaper for dirty cubes, ~1.3 arcsec beam; none for CO(4-3) spw and continuum  
  > "We created dirty cubes with a 100 km s$^{-1}$ velocity bin, applying uvtaper, which yields the synthesized beam sizes of $\approx 1^{\prime\prime}.3$." (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: cleaning down to 2 sigma for identified lines  
  > "For the identified lines, cleaning was done down to $2\sigma$." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum made from line-free channels (channels not listed)  
  > "A band 3 continuum map was also created using line-free channels without tapering" (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.90 x 0.71 arcsec, PA -74 deg (continuum)  
  > "which have the synthesized beam $0^{\prime\prime}.90 \times 0^{\prime\prime}.71$ (P.A.$=-74$ deg)" (2 Observations)
- final rms: 44 uJy/beam (continuum)  
  > "a typical root mean square (RMS) noise of 44 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Optical-NIR aperture photometry method  
  > "we measured flux densities at the optical to near-infrared through aperture photometries in the same manner as is reported in (cite: 2014MNRAS.440.3462U)" (3.2) [from (cite: 2014MNRAS.440.3462U)]
- SPIRE deblending  
  > "The SPIRE fluxes were also deblended in same manner as in (cite: 2014MNRAS.438.1267S)." (3.2) [from (cite: 2014MNRAS.438.1267S)]
- First Band 3 setup data described earlier  
  > "at 84.1–87.8 GHz and 96.1–99.8 GHz ((cite: 2019Sci...366...97U))" (2 Observations) [from (cite: 2019Sci...366...97U)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- Weighting/robust, uvtaper value, cell and image size
- Aperture correction details for line fluxes
- Aperture/extraction region for spectra
- Which CASA version applied to which dataset
- MAGPHYS priors, high-z library details and fitting setup
- PDR model fitting procedure
- Which project 2013.1.00162.S contributed (band 6 data)

## Analysis recipe

1. **Image Band 3 cubes and continuum**: tclean dirty cubes (100 km/s bins, uvtaper) to find lines; clean to 2 sigma; untapered CO(4-3) cube and continuum  
  > "We created dirty cubes with a 100 km s$^{-1}$ velocity bin, applying uvtaper" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line redshift and fluxes**: One-component Gaussian fit to spectra at integrated-map centroid; imfit cross-check; aperture correction  
  > "The redshift was determined from a one-component Gaussian profile fitting to the CO(4-3) spectra" (3.1)
   - software: CASA imfit
   - fitting: Gaussian profile  
  > "The redshift was determined from a one-component Gaussian profile fitting to the CO(4-3) spectra" (Results: Line detections and spectroscopic redshift)
   - validation: imfit flux 16% larger; [CI] redshift consistent  
  > "We also measured the CO(4-3) flux on the integrated emission map using the casa task imfit to find a slightly (16%) larger value." (3.1)
3. **Deblend IRAC photometry**: GALFIT with two point sources and sky  
  > "We fit the region around ADF22.A2 using three components, including two point sources and the sky." (Appendix)
   - software: GALFIT
   - fitting: _not stated_
   - validation: fluxes exceed 3 sigma point-source limits  
  > "These measurements exceed the 3$\sigma$ detection limits for a point source" (Appendix)
4. **SED fit for M*, LIR, SFR, dust mass**: MAGPHYS high-z extension on multi-band photometry  
  > "we applied the high-redshift extension of the SED-fitting algorithm magphys" (3.2)
   - software: MAGPHYS
   - assumption: Chabrier IMF; CMB effect on continuum not considered  
  > "We adopted a Chabrier IMF ((cite: 2003PASP..115..763C))" (3.2)
   - fitting: median and 68% intervals  
  > "The fitting yields median values and 68% confidence intervals for the stellar mass" (Results: Stellar mass, IR luminosity, and SFR)
   - validation: compared with z>3 SMG average SEDs  
  > "A large fraction of the ADF22.A2 photometry is also explainable by the template, which indicates that ADF22.A2 may have similar characteristics as the other SMGs at $z>3$." (Results: Stellar mass, IR luminosity, and SFR)
5. **Derive molecular gas mass**: [CI]-based (optically thin), CO(4-3)-based and dust-based estimates; [CI] adopted  
  > "In this paper, we use the \[C i\]-based gas mass in the following discussion." (3.3)
   - assumption: X_[CI]=3e-5, A10=7.93e-8 s^-1, Q10=0.6; r43/10=0.41, alpha_CO=1.0; dust-to-gas 120  
  > "Here we adopt $X_{\rm [CI]}=3\times10^{-5}$" (3.3)
   - fitting: _not stated_
   - validation: three methods consistent  
  > "Thus estimates using the three methods are consistent." (3.3)
6. **Constrain ISM with PDR models**: Compare line ratios with Kaufman PDR models; CO luminosity doubled for optical depth  
  > "We increase the observed CO luminosity by a factor of two to incorporate this effect." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0, 4.7.2, 5.1.0, 5.4.0: reduction, tclean imaging, imfit  
  > "The calibrated visibility data were used for imaging with the casa task tclean." (2 Observations)
- **MAGPHYS** : SED fitting  
  > "we applied the high-redshift extension of the SED-fitting algorithm magphys" (3.2)
- **GALFIT** : IRAC deblending  
  > "we measured the flux density using galfit" (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectroscopic redshift | 3.9913 | ±0.0008 | dimensionless | 2 | unambiguous redshift of $z_{\rm spec}=3.9913\pm0.0008$ |
| CO(4-3) line flux | 0.56 | ±0.09 | Jy km/s | 2 | $I_{\rm CO(4-3)}=0.56\pm 0.09$ Jy km s$^{-1}$ |
| [CI](1-0) line flux | 0.24 | ±0.06 | Jy km/s | 2 | $I_{\rm [CI](1-0)}=0.24\pm 0.06$ Jy km s$^{-1}$ |
| 3 mm continuum flux | 59.2 | ±9.3 | uJy | 1 | $S_{\rm 3.13mm}=59.2\pm9.3$ $\mu$Jy |
| Stellar mass | 1.1e11 | +1.3/-0.6 e11 | Msun | 4 | $M_*=1.1_{-0.6}^{+1.3}$ $\times10^{11} M_\odot$ |
| SFR | 430 | +230/-150 | Msun/yr | 4 | $430_{-150}^{+230}$ $M_\odot$ yr$^{-1}$ |
| L_IR(8-1000um) | 5.5e12 | +3.0/-1.7 e12 | Lsun | 4 | $L_{\rm IR:8-1000 \mu m}=5.5_{-1.7}^{+3.0}$ $\times10^{12}$ $L_\odot$ |
| M(H2) from [CI] | 5.9e10 | ±1.5e10 | Msun | 5 | $M (H_2)^{\rm [CI]}=(5.9\pm1.5)\times10^{10}$ $M_\odot$ |
| M(H2) from CO(4-3) | 5.4e10 | ±1.2e10 | Msun | 5 | $M (H_2)^{\rm CO(4-3)}=(5.4\pm1.2)\times10^{10}$ $M_\odot$ |
| Dust mass | 4.3e8 | ±0.9e8 | Msun | 4 | $M_{\rm d}=4.3\pm0.9\times10^8$ $M_\odot$ |
| PDR gas density | 5.6e4 | +4.6/-2.5 e4 | cm^-3 | 6 | $n=(5.6_{-2.5}^{+4.6})\times10^4$ cm$^{-3}$ |
| Depletion time | 0.1-0.2 | not stated | Gyr | 5 | $\tau_{\rm dep}=M_{\rm gas}/SFR\approx0.1-0.2$ Gyr |

## Qualitative findings

- ADF22.A2 lies near or above the z~4 main sequence and has ISM line ratios similar to bright SMGs.  
  > "The consistency of the line ratios suggests that these characteristics" (4 Discussion)

## Claim tuples

- H: Can ADF22.A2's redshift be determined from mm lines? | E: Band 3 line scan | R: CO(4-3) and [CI](1-0) detected, z=3.9913±0.0008 | F: Secure redshift obtained | **supported**
- H: Is ADF22.A2 a massive star-forming galaxy? | E: MAGPHYS SED fit | R: M*~1.1e11 Msun, SFR~430 Msun/yr | F: Massive, star-forming galaxy | **supported**
- H: Are NIR-dark ALMA galaxies progenitors of quiescent galaxies at z>~3? | E: gas fraction and depletion time | R: fgas~35%, tau_dep 0.1-0.2 Gyr | F: Consistent with progenitors of quiescent galaxies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large SED uncertainties from limited photometry; CMB effects not considered  
  > "We note that the relatively large uncertainties principally arose due to the limited number of available photometry points." (3.2)
- Caveat (inferred, ours): Single source; conclusions on population are extrapolated
- Caveat (inferred, ours): Gas mass depends on assumed X_[CI], Q10
- Caveat (inferred, ours): No CMB correction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MAGPHYS setup
- Missing: Aperture corrections
- Missing: Band 6 data handling
- Data volume (inferred): ~100–300 GB raw for Band 3 mosaic plus tapered/untapered cubes
- Score (inferred): 3/5, Data from archive projects and main steps described, but many imaging and fitting details missing.
- Rediscovery candidate: no, Recipe lacks key parameters and requires external multiband photometry.

## Links

- Method: (cite: 2008MNRAS.388.1595D) (MAGPHYS SED fitting)
- Method: (cite: 2004ApJ...615L..29P) ([CI] gas mass formula)
- Companion: (cite: 2017ApJ...835...98U) (ADF22 1.1 mm survey data)
- Companion: (cite: 2019Sci...366...97U) (Band 3 data set and redshifts of ADF22A sources)
- Related: ADF22
- Related: ALESS

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
