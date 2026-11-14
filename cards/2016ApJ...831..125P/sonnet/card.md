# A Steeper than Linear Disk Mass-Stellar Mass Scaling Relation

`2016ApJ...831..125P` | The Astrophysical Journal 2016 | first author: Pascucci, I. | arXiv: 1608.03621 | DOI: 10.3847/0004-637X/831/2/125

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How does dust disk mass scale with stellar mass in Chamaeleon I, and does the relation differ among Taurus, Lupus, Cha I and Upper Sco?  
  > "we show that the 1-3 Myr-old regions of Taurus, Lupus, and Chamaeleon I share the same $M_{\rm dust}-M_*$ relation, while the 10 Myr-old Upper Sco association has a steeper relation." (abstract)
- Target **Chamaeleon I disk population (93 objects)**: coordinates _not stated_; z/distance 160 pc  
  > "Assuming an average distance of 160 pc to the Chamaeleon I star-forming region (cite: luhman08)" (2 The Chamaeleon I sample); distance from Luhman 2008  
  > "Assuming an average distance of 160 pc to the Chamaeleon I star-forming region (cite: luhman08)" (2 The Chamaeleon I sample)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (887 um, 338 GHz)  
  > "All observations were obtained in Band 7 with a spatial resolution of $0.7''\times0.5''$" (3 Observations and data reduction)
- frequencies and spectral setup: three continuum basebands of 5.6 GHz centered at 330.0, 341.1, 343.0 GHz; fourth baseband split in two 0.1 GHz sub-bands at 329.3 and 330.6 GHz for C18O and 13CO (3-2)  
  > "three continuum basebands of 5.6 GHz aggregated bandwidth centered at 330.0, 341.1, and 343.0 GHz for an average frequency of 338 GHz (887 $\mu$m)" (3 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m antennas (37 in 2014, 39 in 2015)  
  > "2014 May 1-3 | 37 | 17-558 | 0.6" (Table 2)
- configurations: _not stated_
- baselines: 17-558 m (2014); 21-556 m (2015)  
  > "2015 May 18-19 | 39 | 21-556 | 0.6" (Table 2)
- angular resolution: 0.7'' x 0.5''  
  > "with a spatial resolution of $0.7''\times0.5''$" (3 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Requested 1σ rms 1 mJy/beam (Hot) and 0.2 mJy/beam (Cool); achieved median 0.99 and 0.23 mJy/beam  
  > "found a median of 0.99 and 0.23 mJy/beam for the *Hot* and *Cool* samples" (3 Observations and data reduction)
- time on source: _not stated_
- observing dates: 2014 May 1-3 (54 sources) and 2015 May 18-19 (39 sources)  
  > "ALMA Cycle 2 campaign on 2014 May 1-3 UTC (54 sources) and on 2015 May 18-19 UTC (39 sources)" (3 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: C18O 3-2 (not stated)
- Line: 13CO 3-2 (not stated)
- Other facility **VLT X-Shooter**: spectra giving stellar parameters for 89 of 93 targets  
  > "our group has obtained VLT X-Shooter spectra for 89 out of 93 of our ALMA Chamaeleon I targets" (2 The Chamaeleon I sample)
- Other facility **Spitzer, WISE, 2MASS**: photometry for SED classification  
  > "Our modeling included optical, 2MASS, Spitzer, WISE, and, when available, Herschel and mm photometry." (2 The Chamaeleon I sample)
- External data: Taurus SMA fluxes and stellar properties re-analyzed for comparison  
  > "The Taurus star-forming region has been covered with the SMA at a lower sensitivity (cite: andrews13)" (6.1) [from (cite: andrews13)]
- External data: Lupus ALMA fluxes  
  > "The disk populations of the Chamaeleon I (this paper), Lupus (cite: ansdell16), and Upper Sco (cite: bare16) regions have been probed with ALMA in Band 7" (6.1) [from (cite: ansdell16)]
- External data: Upper Sco ALMA fluxes  
  > "For Upper Sco we only consider disks classified as ’Full’ and ’Transitional’ in Table 1 of (cite: bare16)" (6.1) [from (cite: bare16)]
- External data: Stellar Teff and L from X-Shooter spectra  
  > "Effective temperatures and luminosities for our ALMA Chamaeleon I sample are taken from (cite: manara14; manara16a; manara16c) and (cite: luhman07; luhman08)" (2.1 Stellar mass estimates) [from (cite: manara14; manara16a; manara16c; luhman07; luhman08)]
- Simulation/model as data: Baraffe et al. 2015 and Feiden 2016 pre-main-sequence evolutionary tracks used for stellar masses  
  > "We use the (cite: baraffe15) tracks for all objects with effective temperatures $\le$3,900 K (M dwarfs) and switch to the (cite: feiden16) tracks for hotter stars" (2.1 Stellar mass estimates)
- Simulation/model as data: Krijt et al. 2016 Lagrangian dust evolution code used to simulate growth, drift, fragmentation  
  > "we use the Lagrangian code developed by (cite: krijt16) and simulate the evolution of dust disk grains" (6.2)

## Processing

### Calibration

- pipeline or manual: Reduction scripts provided by NA ALMA Science Center, re-run  
  > "The initial reduction scripts were provided by the North American ALMA Science Center and included phase, bandpass, and flux calibration." (3 Observations and data reduction)
- casa version: CASA 4.3.1 (calibration); CASA v4.4 (imaging)  
  > "We re-ran the scripts using CASA 4.3.1." (3 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (Hot); Ganymede and J1107-448 (Cool SBs)  
  > "We used Pallas as the flux calibrator for the *Hot* sample SBs, Ganymede for the first *Cool* sample SB, and the quasar J1107-448 for the second *Cool* sample SB." (3 Observations and data reduction)
- flux scale uncertainty: 10% adopted (SBs agree within 5% Hot, 8% Cool)  
  > "we adopt a conservative 1$\sigma$ uncertainty of 10% on the absolute flux scale." (3 Observations and data reduction)
- self calibration: Phase then amplitude+phase self-cal on 12 bright sources, 3 cycles with shallow cleaning to ~5x then ~3x median rms  
  > "We repeated the cycle of cleaning and phase calibration a second time starting from the new image and by applying a deeper cleaning, down to about 3 times the median rms" (3 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for dirty images; Briggs robust 0 for self-cal images  
  > "Dirty continuum images were created from the calibrated visibilities using CASA v4.4 and natural weighting" (3 Observations and data reduction); "we produced an image with Briggs robust weighting parameter of zero and cell size 0.075$''$" (3 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.075'' (self-cal images)  
  > "Briggs robust weighting parameter of zero and cell size 0.075$''$" (3 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: median 0.99 mJy/beam (Hot), 0.23 mJy/beam (Cool)  
  > "found a median of 0.99 and 0.23 mJy/beam for the *Hot* and *Cool* samples" (3 Observations and data reduction)

### Inherited from earlier work

- Self-calibration procedure for bright sources  
  > "followed the steps suggested by the North American ALMA Science Center for the brightest of our targets" (3 Observations and data reduction) [from North American ALMA Science Center]
- Bayesian stellar mass/age inference  
  > "Following (cite: andrews13), we adopt a Bayesian inference approach to assign a stellar mass, an age, and associated uncertainties" (2.1 Stellar mass estimates) [from (cite: andrews13)]
- Dust opacity 2.3 cm2/g at 230 GHz with nu^0.4  
  > "the same as in (cite: andrews13) for Taurus and (cite: carpenter14) for Upper Sco" (5 Dust disk masses) [from (cite: andrews13; carpenter14)]
- Tdust = 25 K (L*/Lsun)^0.25 prescription  
  > "$T_{\rm dust}=25$K$\times (L_*/L_\ensuremath{\odot})^{0.25}$" (5 Dust disk masses) [from (cite: andrews13)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, masks, thresholds and the exact cleaning for the deconvolved images of the two cavity sources
- Exact uv ranges/weights in uvmodelfit
- Priors/chain settings of linmix_err
- Which sources used which SB flux scaling in detail
- Full Krijt model setup beyond listed parameters (stellar T, L, time grid)
- Lupus/Upper Sco stellar masses and fluxes tabulated for re-analysis
- ALMA project code not printed

## Analysis recipe

1. **Derive stellar masses and ages**: Bayesian likelihood on Teff and L* against Baraffe15 and Feiden16 grids; peak of marginalized PDFs  
  > "The best fit mass and age are the peaks of these functions and the uncertainties are the values that encompass 68% of the area under the functions." (2.1 Stellar mass estimates)
   - parameter: sigma log Teff 0.02 (earlier than M3), 0.01 (later); sigma log L 0.1; age grid 0.5-50 Myr  
  > "The uncertainty in log($T_{*}$) is assumed to be 0.02 for SpTy earlier than M3 and 0.01 for later SpTy while the uncertainty in log($L_{*}$) is taken to be 0.1" (2.1 Stellar mass estimates)
   - assumption: Uniform priors on model parameters  
  > "we compute a conditional likelihood function, assuming uniform priors on the model parameters" (2.1 Stellar mass estimates)
   - fitting: _not stated_
   - validation: Also repeated with Luhman07 Teff and L  
  > "we also compute stellar masses using the effective temperatures and luminosities in (cite: luhman07)" (4 Results)
2. **Measure continuum flux densities and resolution**: Fit visibilities with elliptical Gaussian; point-source model if FWHM/uncertainty<2; image-based 3σ flux for ring sources; point source fit with fixed offsets for non-detections  
  > "First, we fit all of our 66 detections with an elliptical Gaussian using the *uvmodelfit* task in CASA." (4 Results)
   - software: CASA uvmodelfit
   - parameter: Upper limits = 3 times the flux uncertainty  
  > "we calculate upper limits for sources that are not detected as 3 times the uncertainty on $F_\nu$" (4 Results)
   - fitting: Parameter uncertainties scaled to give reduced chi2 of 1  
  > "we scale the uncertainties on the fitted parameters by the factor needed to produce a reduced $\chi^2$ of 1" (4 Results)
   - validation: Visibility vs uv-distance plots compared with models  
  > "we compare the best fit model (solid line) to the real component of the observed visibilities (filled circles) as a function of projected baseline length" (4 Results)
3. **Convert flux to dust mass**: Isothermal optically thin: log Mdust = log Fnu + 2 log d - log kappa - log B(Tdust); two Tdust cases  
  > "we compute dust disk masses for two extreme cases: a) a constant $T_{\rm dust}$ fixed to 20 K" (5 Dust disk masses)
   - parameter: kappa = 2.3 cm2/g at 230 GHz, nu^0.4; d = 160 pc  
  > "We adopt a dust opacity of 2.3 cm$^2$ g$^{-1}$ at 230 GHz with a frequency dependence of $\nu^{0.4}$" (5 Dust disk masses)
   - assumption: Tdust = 20 K or 25 K (L/Lsun)^0.25; no 10 K floor  
  > "We have decided not to apply this plateau in our study" (5 Dust disk masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit flux/dust mass versus stellar mass**: Bayesian linear regression with censoring and intrinsic scatter (linmix_err), compared with fitexy, mpfitexy, censReg, cenken  
  > "we can determine the best fit using the Bayesian method developed by (cite: kelly07) that properly accounts for the measurement uncertainties, non-detections, and intrinsic scatter." (4 Results)
   - software: linmix_err, fitexy, mpfitexy, censReg, cenken
   - parameter: Mass error = half of 68% range; ±0.1 dex for fixed-isochrone sources  
  > "For the 10 sources where we had to fix the isochrone we use the median uncertainty in log($M_*$) of $\pm0.1$ dex." (4 Results)
   - fitting: MCMC for slope/intercept uncertainty, Gaussian errors  
  > "A Markov chain Monte Carlo method is used to compute the uncertainties on the slope and intercept." (Appendix)
   - validation: Other regression methods recover same slope; sensitivity degraded to Taurus level  
  > "The fact that they all provide the same slope and intercept within the quoted uncertainties (Table 5) again confirms" (Appendix)
5. **Compare regions self-consistently**: Re-derive stellar masses with same tracks for Taurus, Lupus, Upper Sco; refit; generalized Wilcoxon test with censoring  
  > "By performing a generalized Wilcoxon test with the cendiff command in the NADA R package" (6.1)
   - software: NADA R package (cendiff)
   - fitting: _not stated_
   - validation: _not stated_
6. **Model dust evolution**: Lagrangian growth/drift/fragmentation simulations for 0.2 and 2 Msun stars  
  > "simulate the evolution of dust disk grains subject to: a) growth and fragmentation; b) growth and radial drift; and c) growth, radial drift, and fragmentation." (6.2)
   - software: Krijt et al. 2016 code
   - parameter: disk 2-200 AU, index -1.5, dust-to-gas 0.01, mass 1% of M*, alpha=0.01, vfrag 3 m/s, porosity 30%  
  > "the turbulence is characterized by $\alpha=0.01$ (cite: ss73), the fragmentation velocity is 3 m/s, and the grain porosity is constant at 30%" (6.2)
   - fitting: _not stated_
   - validation: Compared qualitatively to observed steepening  
  > "the more realistic case of growth, radial drift, and fragmentation (black dotted line and symbols) shows a behavior consistent with the observations" (6.2 On the evolving disk-stellar mass scaling relation)

## Software

- **CASA** 4.3.1 / 4.4: calibration, imaging, self-calibration, uvmodelfit  
  > "The ALMA data were calibrated using the CASA software package." (3 Observations and data reduction)
- **linmix_err** : Bayesian regression with censoring  
  > "The one utilized throughout the paper is the linmix_err routine (IDL version) written by (cite: kelly07)" (Appendix)
- **NADA R package** : generalized Wilcoxon test (cendiff)  
  > "with the cendiff command in the NADA R package" (6.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detected disks | 66 of 93 | not stated | disks | 2 | We detect thermal dust emission from 66 out of 93 disks, spatially resolve 34 of them |
| Fmm-M* slope | 1.9 | 0.2 | dimensionless | 4 | log($F_{\rm mm}$/mJy)=1.9($\pm0.2$)$\times$log($M_*/M_\ensuremath{\odot}$)+1.6($\pm0.1$) |
| Mdust-M* slope, constant Tdust | 1.9 | 0.2 | dimensionless | 4 | log($M_{\rm dust}/M_\Earth$)=1.9($\pm0.2$)$\times$log($M_*/M_\ensuremath{\odot}$)+1.1($\pm0.1$) for a constant $T_{\rm dust}$ |
| Mdust-M* slope, Tdust scaling with L* | 1.3 | 0.2 | dimensionless | 4 | log($M_{\rm dust}/M_\Earth$)=1.3($\pm0.2$)$\times$log($M_*/M_\ensuremath{\odot}$)+1.1($\pm0.1$) for $T_{\rm dust}$ decreasing with stellar luminosity |
| Dispersion about relation | 0.8 | 0.1 | dex | 4 | The standard deviation (hereafter, dispersion) about the regression is 0.8$\pm 0.1$ dex |
| Upper Sco Mdust-M* slope (T20) | 2.7 | 0.4 | dimensionless | 5 | Upper Sco / 10 / 2.7(0.4) / 0.9(0.2) / 1.9(0.4) / 0.8(0.2) / 0.7(0.1) |
| Wilcoxon p, Cha I vs Upper Sco | 0.0001% | not stated | percent | 5 | but different from that of Upper Sco (p=0.0001%) |

## Qualitative findings

- Models suggest outer disks are fragmentation-limited; drift then removes dust faster around lower-mass stars  
  > "the comparison between models and observations suggests that the maximum grain size in the outer disk is fragmentation-limited, rather than drift-limited." (6.2)

## Claim tuples

- H: Is the Mdust-M* relation in Cha I steeper than linear? | E: Regress Fmm and Mdust on M* with censored Bayesian fit | R: Slopes 1.9 (constant T) and 1.3 (T~L^0.25) | F: Relation is steeper than linear | **supported**
- H: Do Taurus, Lupus, Cha I share a relation while Upper Sco differs? | E: Self-consistent re-analysis and Wilcoxon tests | R: Cha I indistinguishable from Taurus and Lupus, different from Upper Sco | F: Same relation at 1-3 Myr; steeper in Upper Sco | **supported**
- H: What process steepens the relation with time? | E: Dust evolution models | R: Only growth+drift+fragmentation reproduces faster fading around low-mass stars | F: Fragmentation-limited regime favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Bayesian regression chosen to handle upper limits, measurement errors and intrinsic scatter  
  > "properly accounts for the measurement uncertainties, non-detections, and intrinsic scatter" (4 Results)
- Alternative: 10 K temperature floor rejected because outer disks can be colder  
  > "continuum radiative transfer models show that the interstellar radiation field has a negligible effect on the dust disk temperature and outer disks can be colder than 10 K" (5 Dust disk masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity and temperature uncertain; steepness depends on how disk size scales with stellar mass  
  > "quantifying the steepness of the $M_{\rm dust} - M_*$ relation will require measuring how dust disk sizes scale with stellar masses." (5 Dust disk masses)
- Caveat (inferred, ours): Dust mass conversion depends heavily on assumed opacity and temperature
- Caveat (inferred, ours): Sample incomplete in substellar regime
- Caveat (inferred, ours): Comparison with other regions relies on heterogeneous surveys (SMA Taurus lower sensitivity)
- Caveat (inferred, ours): Lupus intercept depends on private-communication correction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code not printed
- Missing: Other-region data tables not provided
- Missing: Exact clean parameters
- Data volume (inferred): tens of GB (two Cycle 2 Band 7 datasets, 93 targets)
- Score (inferred): 3/5, Data public-likely and flux method clear, but multi-region comparison and imaging details are not fully specified.
- Rediscovery candidate: no, Project code and key inputs from other surveys not stated in the paper; tabulated fluxes aid partial reproduction.

## Links

- Method: (cite: kelly07) (Bayesian censored regression)
- Method: (cite: andrews13) (mass inference and dust mass prescription)
- Companion: (cite: ansdell16) (Lupus ALMA survey)
- Companion: (cite: bare16) (Upper Sco ALMA survey)
- Companion: (cite: manara16a) (X-Shooter stellar properties)
- Related: Lupus ALMA survey
- Related: Upper Sco ALMA survey
- Related: Taurus SMA survey

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00437.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 56,
  "rate": 0.651
 },
 "evidence_ok": true
}
```
