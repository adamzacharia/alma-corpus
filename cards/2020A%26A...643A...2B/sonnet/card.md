# The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties

`2020A&A...643A...2B` | Astronomy and Astrophysics 2020 | first author: Béthermin, M. | arXiv: 2002.00962 | DOI: 10.1051/0004-6361/202037649

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Process the ALPINE ALMA band-7 data into continuum and [CII] catalogs and derive basic dust and [CII] properties, number counts and redshift distribution of serendipitous continuum sources  
  > "In this paper, we present the task of processing the ALPINE data from the raw data to the catalogs and the immediate scientific results" (Introduction)
- Target **ALPINE sample (118 galaxies at 4.4<z<5.9 in COSMOS and CDFS)**: coordinates per-target RA/Dec listed in the pointing table (appendix)  
  > "The ALPINE sample contains sources from both the cosmic evolution survey (COSMOS) field and the *Chandra* deep field south (CDFS)." (2.1 Observations); "Our final sample contains 118 objects." (2.1 Observations); z/distance 4.4<z_spec<5.9  
  > "The ALPINE sample contains sources from both the cosmic evolution survey (COSMOS) field and the *Chandra* deep field south (CDFS)." (2.1 Observations); "Our final sample contains 118 objects." (2.1 Observations); distance from spectroscopic redshifts from optical ground-based observations  
  > "The ALPINE sample contains sources from both the cosmic evolution survey (COSMOS) field and the *Chandra* deep field south (CDFS)." (2.1 Observations); "Our final sample contains 118 objects." (2.1 Observations)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 (275–373 GHz)  
  > "In this redshift range, the \[CII\] line falls in the band 7 of ALMA (275 –373 GHz)." (2.1 Observations)
- frequencies and spectral setup: TDM, 31.250 MHz channels (25-35 km/s); two contiguous 1.875 GHz spws on [CII], two spws in other sideband for continuum  
  > "The \[CII\] lines of the targeted sources are covered by two contiguous spectral windows (1.875 GHz each), while we placed two remaining spectral windows in the other side band" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1 or C43-2 requested  
  > "we requested compact array configurations (C43-1 or C43-2) corresponding to a $>$0.7 arcsec resolution" (2.1 Observations)
- baselines: _not stated_
- angular resolution: mean beam 1.13" x 0.85"  
  > "The average beam size is 1.13"$\times$0.85"." (Conclusion)
- max recoverable scale: _not stated_
- sensitivity: continuum ~30 uJy RMS; [CII] 0.14 Jy km/s in 235 km/s  
  > "reached a typical sensitivity of 30 $\mu$Jy RMS in continuum and 0.14 Jy km/s for \[CII\] in a 235 km/s bandwidth" (Conclusion)
- time on source: 15-25 min per source; 61 SBs, 69.3 h including overheads  
  > "In total, we had 61 scheduling blocks (SBs) for a total of 69.3 h including overheads." (2.1 Observations)
- observing dates: 2018/05/08–2018/07/16 and 2018/08/20 (cycle 5); 2019/01/09–2019/01/11 (cycle 6)  
  > "They were observed between 2019/01/09 and 2019/01/11." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2-2P1/2 (158 um) (not stated)
- Other facility **Herschel (PEP, HerMES), AzTEC/ASTE, SCUBA2**: Single-dish maps used for stacking to derive the dust SED  
  > "We used the same *Herschel*[^6] (cite: Pilbratt2010) data from the PEP (cite: Lutz2011) and *HerMES* (cite: Oliver2012) surveys" (4.2 Mean stacked SEDs)
- Other facility **COSMOS/Davidzon2017 and Laigle2015 catalogs**: Photometric sample for stacking and counterparts of nontarget sources  
  > "we use the more recent COSMOS catalog of (cite: Davidzon2017) as input sample" (4.2 Mean stacked SEDs)
- External data: Ancillary properties (SFR, stellar mass, UV luminosity) of ALPINE targets  
  > "The far-UV luminosity, L$_{FUV}$, is provided by the ancillary ALPINE catalog presented in (cite: Faisst2020)." (7.5) [from (cite: Faisst2020)]
- External data: SED templates (Bethermin2017 adopted; Schreiber2018, Alvarez-Marquez2016 compared)  
  > "Since the $\chi^2$ of (cite: Bethermin2017) is marginally better, we decided to use this template." (4.3 SED template) [from (cite: Bethermin2017)]
- External data: Absolute CIB level used as reference  
  > "Their values are used as the reference CIB level in this paper." (5.4 Cosmic infrared background) [from (cite: Odegard2019)]
- Simulation/model as data: SIDES simulation and galaxy evolution models (Bethermin2017, Gruppioni, Casey2018) compared with redshift distribution and counts  
  > "we compare our measured distribution with the predictions of the simulated infrared dusty infrared sky (SIDES) simulation" (5.2)

## Processing

### Calibration

- pipeline or manual: Observatory CASA pipeline plus manual flagging of suspicious antennae  
  > "The data were initially calibrated at the observatory using the standard ALMA pipeline of the Common Astronomy Software Applications package (CASA) software" (2.2 Pipeline calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: For half of the observations no problems found and observatory-calibrated data used directly  
  > "For half of the observations, no problems were found and we used directly the data calibrated by the observatory pipeline." (2.2 Pipeline calibration)
- flux calibrator: _not stated_
- flux scale uncertainty: ~6% flux variability (13% outliers); 7.5% / 4% total from quasar monitoring  
  > "The typical 1-$\sigma$ uncertainty of the calibration thus is 7.5 % for J0522-3627 and J0854+2006 and 4 % for J1058+0133" (2.3 Flux calibrators)
- self calibration: _not stated_

### Imaging

- task: tclean (cubes), MFS for continuum  
  > "The datacube were imaged using the *tclean* CASA routine using 0.15 arcsec pixels" (2.4 Data cube imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The standard ALPINE products were produced using a natural weighting of the visibilities." (2.4 Data cube imaging)
- uv taper: 1.5 arcsec Gaussian taper for extended sources  
  > "We used a Gaussian 1.5-arcsec-diameter tapering." (2.5 Continuum imaging)
- cell size: 0.15 arcsec  
  > "using 0.15 arcsec pixels to well sample the synthesized beam" (2.4 Data cube imaging)
- image size: _not stated_
- masking: clean to 3 sigma_noise, iterated  
  > "The clean algorithm is run down to a flux threshold of 3 $\sigma_{\rm noise}$" (2.4 Data cube imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub order 0, line channels masked beyond 3 sigma_v of Gaussian fit  
  > "fitting a flat continuum model (order 0) to the visibilities" (2.4 Data cube imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: mean minor 0.85", major 1.13"  
  > "The average size of minor axis is 0.85 arcsec" (2.6 Achieved beam sizes)
- final rms: _not stated_

### Inherited from earlier work

- Stacking analysis procedure for the SED  
  > "Our new stacking analysis was performed using the exact same procedure as in (cite: Bethermin2015a)." (4.2) [from (cite: Bethermin2015a)]
- Lines found by customized finder; uv-plane size measurements and stacking details deferred to companion papers  
  > "However, uv-plane modeling is critical for size measurements and is presented in (cite: Fujimoto2020)." (3.6) [from (cite: Fujimoto2020)]
- [CII] luminosity formula  
  > "computed using the formula provided in (cite: Carilli2013)" (7.4) [from (cite: Carilli2013)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version used for pipeline and tclean
- Number of clean iterations/mask specifics, spectral cube channelization for final cubes
- Exact bootstrap settings for stacking and error bars
- Line-free channel ranges per source (only rule given)
- Exact catalog of manual spw fixes
- Details of uv-fit and stacking in unpublished companion papers

## Analysis recipe

1. **Calibrate and flag data**: Observatory pipeline re-run with fracspw=0.03125 and extra antenna flagging  
  > "It was solved by adding the *fracspw*=0.03125 option to the *hifa_flagdata* task before re-running the pipeline script from the observatory." (2.2)
   - software: CASA
   - fitting: _not stated_
   - validation: Quasar calibrator stability checked  
  > "We thus checked that the quasars used as secondary flux calibrators were reasonably stable across the ALPINE observations." (2.3)
2. **Image cubes, continuum and moment-0 maps**: tclean natural weighting, MFS continuum, uvcontsub, tapered maps  
  > "the continuum maps were produced using multi-frequency synthesis (MFS, (cite: Conway1990))" (2.5)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract continuum sources and set purity threshold**: Local maxima in S/N maps; purity from negative maps; 5 sigma in field, 3.5 sigma within 1 arcsec of targets  
  > "We reach a purity of 95 % for a S/N=3.5 cut." (3.1)
   - software: astropy
   - fitting: _not stated_
   - validation: Purity via positive/negative detections  
  > "We estimated the purity of the extracted sample as a function of the S/N by comparing the number of detections in the positive and the negative maps." (3.1)
4. **Measure continuum photometry**: Peak, 2D Gaussian fit, 3 arcsec aperture, 2-sigma clipped; 2D-fit adopted  
  > "We decided to use the 2D-fit photometry, because of the very small impact of the size on the deboosting correction to apply." (3.9)
   - software: astropy, photutils, GILDAS
   - fitting: Elliptical Gaussian in 3 arcsec box; Condon1997 errors  
  > "We use the formalism of (cite: Condon1997), who proposed a simplified formalism to propagate the uncertainties." (3.2)
   - validation: Methods compared; uv-plane fits for 9 targets; Monte Carlo injections  
  > "All our sources are compatible at 1 $\sigma$ with the one-to-one relation." (3.6)
5. **Completeness, flux boosting, effective area, number counts and CIB**: Inject Gaussian sources of 4 sizes and 18 fluxes (10 per pointing, 10 repeats); derive completeness, deboosting, effective area; counts as sum of 1/Omega_eff  
  > "We performed injections of sources using a grid of 4 different intrinsic sizes (FWHM = 0, 0.333, 0.666, and 1 arcsec) and 18 different nonprimary beam corrected flux densities" (3.7)
   - assumption: Fluxes converted to 850 um using z=2.5 main-sequence Bethermin2017 SED template  
  > "assuming the z=2.5 main-sequence spectral energy distribution (SED) template of the (cite: Bethermin2017) model" (3.10)
   - fitting: Power-law extrapolation to five faintest count points for CIB  
  > "We extrapolated the contribution of sources fainter than 0.35 mJy by fitting a power-law to the five faintest data points." (5.4)
   - validation: _not stated_
6. **Derive 158 um continuum to L_IR conversion via Herschel stacking**: Mean stacking of SFR>10 Msun/yr COSMOS sources at 4<z<5 and 5<z<6; fit templates with free normalization  
  > "We renormalized the templates to fit the data. This is the only free parameter in our analysis." (4.3)
   - assumption: Bethermin2017 template with no evolution above z~4 (<U>=50)  
  > "Above this redshift, no evolution is assumed ($\langle U \rangle$ = 50)." (4.3)
   - fitting: chi2 of templates; MBB with beta=1.8 shown for information  
  > "a modified blackbody with a fixed $\beta$ of 1.8, but a free amplitude and temperature" (4.3)
   - validation: Bootstrap errors  
  > "The uncertainties were derived using a bootstrap technique that takes into account both the photometric noise (instrumental and confusion) and the population variance." (4.2)
7. **Extract [CII] lines and catalog**: Running-average moment-0 cubes (2-40 channels) in 1" cylinder, S/N>3 peaks, Gaussian fit, iterate 2-sigma region spectra; 95% purity at S/N>3.56  
  > "We chose to cut our catalog at S/N$>$3.56 to be conservative." (6.2)
   - software: findclumps
   - fitting: Gaussian line profile for fcen and FWHM  
  > "we fit a Gaussian profile of the spectrum and computed central frequency (f$_{\rm cen}$) and FWHM" (6.1)
   - validation: Cross-check with findclumps (S/N 3.45)  
  > "we find a 95% purity limit for S/N=3.45 in the 1 arcsec central region" (6.2)
8. **Stack continuum by [CII] luminosity to get SFR-L[CII]**: Image-plane stacking in four L[CII] bins and z<5 / z>5, aperture photometry, SFR_tot=SFR_IR+SFR_UV  
  > "We then stacked the continuum of all the sources of a given luminosity bin in image space after masking the continuum nontarget detections." (7.5)
   - assumption: kappa_IR=1.02e-10, kappa_FUV=1.47e-10 Msun/yr/Lsun (Chabrier IMF)  
  > "their values are 1.02$\times$10$^{-10}$ M$_\odot$yr$^{-1}$L$_\odot^{-1}$ and 1.47$\times$10$^{-10}$ M$_\odot$yr$^{-1}$L$_\odot^{-1}$, respectively." (7.5)
   - fitting: _not stated_
   - validation: Bootstrap errors; mergers excluded as test  
  > "we tested if this excess could be caused by merging systems by excluding objects classified as merger (type=2)" (7.5)

## Software

- **CASA** : Pipeline calibration, tclean imaging, uvcontsub, uvmodelfit  
  > "The datacube were imaged using the *tclean* CASA routine" (2.4)
- **astropy / photutils** : Peak finding, Gaussian fits, aperture photometry  
  > "We used the routine from the *astropy photutils* package." (3.2)
- **GILDAS MAPPING** : uv-plane Gaussian fits  
  > "we used the GILDAS[^2] software package MAPPING" (3.6)
- **findclumps** : Independent line search for purity cross-check  
  > "We extracted the sources in the negative and the positive cubes using the *findclumps*" (6.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections of targets (S/N>3.5) | 23 of 118 | not stated | sources | 3 | We detected 23 of our 118 targets in continuum above 3.5 $\sigma$ threshold corresponding to a 95 % purity. |
| Nontarget continuum detections (>5 sigma) | 57 | not stated | sources | 3 | detected 57 nontarget additional continuum sources |
| [CII] detections | 75 of 118 | not stated | sources | 7 | We obtained 75 \[CII\] detections out of our 118 targets. |
| Mean redshift of nontarget sources | 2.5 | 0.2 | dimensionless | 0 | The mean redshift of our sample is z=2.5$\pm$0.2 (median = 2.3$\pm$0.3) |
| L_158um / L_IR | 0.093 | not stated | dimensionless | 6 | (L$_{158\,\mu m}$ = 0.093 L$_{\rm IR}$) |
| Median [CII] luminosity | 4.8e8 | 0.4e8 | Lsun | 7 | We found a median luminosity of $(4.8 \pm 0.4) \times 10^{8}$ L$_\odot$ |
| Median [CII] FWHM | 252 | 13 | km/s | 7 | a median FWHM of 252$\pm$13 km/s |
| CIB contribution of >0.35 mJy sources (full sample) | 0.093 | 0.013 | MJy/sr | 5 | 0.093$\pm$0.013 MJy/sr for the full sample and 0.054$\pm$0.009 MJy/sr for the secure sample |
| Total survey area (bright flux) | 24.92 | not stated | arcmin^2 | 5 | the effective surface area is the total area of all our pointings[^5] (24.92 arcmin$^{2}$) |

## Qualitative findings

- Number counts at 850 um show a slope break around 3 mJy; models are not discriminated  
  > "We identified a slope break in the counts around 3 mJy" (Conclusion)
- [CII]-optical redshift offsets up to 1000 km/s  
  > "We also observed significant offsets between the optical and \[CII\] redshifts (up to 1000 km/s)." (Conclusion)

## Claim tuples

- H: Can ALPINE reach its designed [CII] luminosity sensitivity? | E: Measured RMS on moment-0 maps vs frequency | R: Mean sensitivity follows constant-luminosity trend | F: Survey performance meets goal | **supported**
- H: What is the 158 um to L_IR conversion at z>4? | E: Herschel/SCUBA2/AzTEC stacking of COSMOS analogs and template fit | R: Bethermin2017 template fits best | F: Adopt L158=0.093 L_IR | **supported**
- H: Do stacked ALPINE data follow SFR-L[CII] relations? | E: Stack continuum in L[CII] bins | R: Within scatter, with mild [CII] excess at high L | F: Consistent with De Looze and Lagache relations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Photometry via multiple methods to allow Monte Carlo validation and robustness checks  
  > "These four measurements are made automatically to allow us to perform easily Monte Carlo simulations to validate them." (3.2)
- Alternative: Peak flux rejected for extended sources; modified blackbody rejected as it underestimates L_IR  
  > "a modified blackbody ($\nu^\beta \, B_\nu(\nu,T)$, where $B_\nu$ is a blackbody law) tends to underestimate the L$_{\rm IR}$ because of the very low emission in the mid-infrared" (4.3 SED template and conversion factors)
- How they decided it was enough: _not stated_
- Limitation (authors): Stacked-SED sample selection imperfect; conversion may be inaccurate for outliers  
  > "The derived conversion factors could thus be largely inaccurate for outliers with extreme dusty SEDs." (4.4 Caveats)
- Caveat (inferred, ours): Single-template L_IR conversion carries large SED systematics
- Caveat (inferred, ours): Purity from negative maps assumes symmetric noise
- Caveat (inferred, ours): Counts depend on photometric-redshift counterpart identification

## Reproducibility

- Data public (paper): ALPINE products publicly available  
  > "The ALPINE products are publicly available at <https://cesam.lam.fr/a2c2s/>." (Conclusion)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: CASA version
- Missing: Ancillary catalog values (Faisst2020)
- Missing: Stacking details (Khusanova in prep.)
- Data volume (inferred): ~3 TB raw data
- Score (inferred): 3/5, Public data and a detailed recipe, but the ancillary catalogs, CASA version and several steps deferred to companion papers or unpublished work.
- Rediscovery candidate: yes, Data are public, the recipe is largely specified, and the results are numeric (detection counts, medians, conversion factors).

## Links

- Method: (cite: Bethermin2015a) (Stacking procedure)
- Method: (cite: Condon1997) (Uncertainty propagation for Gaussian fits)
- Companion: (cite: Le_Fevre2019) (ALPINE survey goals and overview)
- Companion: (cite: Faisst2020) (Sample selection and ancillary properties)
- Companion: (cite: Fujimoto2020) (Sizes from uv-plane modeling)
- Companion: (cite: Schaerer2020) (SFR-[CII] relation analysis)
- Related: ASPECS
- Related: ALMA-GOODS
- Related: COSMOS
- Related: Capak2015 pilot sample

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
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
  "facts": 88,
  "stated": 61,
  "rate": 0.693
 },
 "evidence_ok": true
}
```
