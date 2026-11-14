# MIRACLE: I. Unveiling the multi-phase, multi-scale physical properties of the active galaxy NGC 424 with MIRI, MUSE, and ALMA

`2025A&A...701A.113M` | Astronomy and Astrophysics 2025 | first author: Marconcini, C. | arXiv: 2503.21921 | DOI: 10.1051/0004-6361/202554797

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the multi-phase (ionised, warm and cold molecular) gas kinematics, dynamical mass and outflow properties in the circumnuclear region of the Seyfert II galaxy NGC 424?  
  > "We present the analysis of the multi-phase gas properties in the Seyfert II galaxy NGC 424, using spatially resolved spectroscopic data from JWST/MIRI, part of the Mid-InfraRed Activity of Circumnuclear Line Emission (MIRACLE) program, as well as VLT/MUSE and ALMA." (abstract)
- Target **NGC 424**: coordinates _not stated_; z/distance z = 0.01175 ± 0.00006, D = 51 Mpc  
  > "NGC 424 is a nearby heavily obscured Seyfert-II galaxy (z = 0.01175 $\pm$ 0.00006[^2], D = 51 Mpc, 1$\sim$ 230 pc)" (1 Introduction); distance from redshift fitted from integrated MUSE spectrum  
  > "NGC 424 is a nearby heavily obscured Seyfert-II galaxy (z = 0.01175 $\pm$ 0.00006[^2], D = 51 Mpc, 1$\sim$ 230 pc)" (1 Introduction)

## Data provenance

- ALMA projects: 2021.1.01150.S
- bands: Band 6, 12-m array  
  > "archival ALMA 12-m array band 6 observations from program 2021.1.01150.S (P.I. A. Rojas)" (2.3 ALMA)
- frequencies and spectral setup: spectral window [226.91, 228.79] GHz covering CO(2-1) at 230.538 GHz rest-frame  
  > "covering the observed spectral window of \[226.91, 228.79\] GHz which allowed us to trace the CO (2-1) emission at 230.538 GHz rest-frame" (2.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: two configurations, beam sizes 0.2 and 1 arcsec  
  > "This program includes observations with two configurations, with beam sizes of 0.2 and 1, respectively." (2.3 ALMA)
- baselines: _not stated_
- angular resolution: beam 0.48 x 0.44, PA 1 deg (~110 pc)  
  > "to achieve a $\sim$110 pc resolution (beam size FWHM 0.48$\times$ 0.44, beam PA = 1$^{\circ}$)" (2.3 ALMA)
- max recoverable scale: 11.4 arcsec (FOV 38 arcsec)  
  > "the FOV is 38 in diameter, with the largest recoverable scale of 11.4." (2.3 ALMA)
- sensitivity: rms 0.94 mJy/beam per channel  
  > "an rms of 0.94 mJy/beam per channel" (2.3 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, P.I. A. Rojas  
  > "archival ALMA 12-m array band 6 observations from program 2021.1.01150.S (P.I. A. Rojas)" (2.3 ALMA)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **JWST/MIRI MRS**: New MIRACLE data: H2 S(1), [NeIII], [NeV] mid-IR IFU cubes  
  > "The JWST/MIRI observations of NGC 424 are part of the GO Cycle 3 MIRACLE program 6138." (2.1 JWST/MIRI)
- Other facility **VLT/MUSE**: Archival optical IFU cube (ID 095.B-0934), [OIII] and Halpha  
  > "NGC 424 IFS archival data obtained with MUSE (ID: 095.B-0934, P.I. S. Juneau)" (2.2 MUSE)
- External data: Previous MUSE outflow estimates for NGC 424 (mass outflow rate 26.3 Msun/yr), used for comparison  
  > "They found an average outflow velocity of 814 $\pm$ 70 $\mathrm{km\,s^{-1}}$ and a mass outflow rate of 26.3 $\pm$ 1.3 $\mathrm{M_\odot}$ yr$^{-1}$." (1 Introduction) [from Kakkad2022]
- External data: NFW dark matter scale length r0 = 8.1 ± 0.7 kpc (Milky Way value)  
  > "we assumed a characteristic scale length of r$_0$ = 8.1 $\pm$ 0.7 kpc as recently found by (cite: Lin2019) for the Milky Way" (4.2 Rotation curve fitting and dynamical mass) [from (cite: Lin2019)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v6.1.1  
  > "the Common Astronomy Software Applications (CASA) package version v6.1.1" (2.3 ALMA)
- pipeline version: _not stated_
- archive products used as is: calibrated measurement sets requested from the European ARC  
  > "We requested the calibrated measurement sets from the European ALMA Regional Centre (cite: Hatziminaoglou2015)." (2.3 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The data were cleaned using the CASA task TCLEAN CASA task using a BRIGGS weighting scheme with ROBUST = 0.5" (2.3 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using a BRIGGS weighting scheme with ROBUST = 0.5" (2.3 ALMA)
- uv taper: _not stated_
- cell size: 90 mas  
  > "a pixel size of 90 mas" (2.3 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: constant continuum from line-free channels in the uv plane  
  > "we subtracted a constant continuum level estimated from the emission line free channels in the *uv* plane" (2.3 ALMA)
- line free channels: spectral windows [226.91, 228.79] GHz and [229.29, 231.27] GHz  
  > "The continuum was subtracted using the line free spectral channels in the spectral windows \[226.91, 228.79\] GHz and \[229.29, 231.27\] GHz" (2.3 ALMA)
- primary beam correction: _not stated_
- array combination: two measurement sets (two configurations) combined  
  > "We combined the two measurement sets to obtain the best compromise in terms of spatial resolution and sensitivity." (2.3 ALMA)
- smoothing: _not stated_
- final beam: 0.48 x 0.44, PA 1 deg  
  > "beam size FWHM 0.48$\times$ 0.44, beam PA = 1$^{\circ}$" (2.3 ALMA)
- final rms: 0.94 mJy/beam per channel, ~5 km/s channels  
  > "spectral channel width of $\sim$ 5 km s$^{-1}$, a pixel size of 90 mas, and an rms of 0.94 mJy/beam per channel" (2.3 ALMA)

### Inherited from earlier work

- MOKA3D 3D kinematic modelling tool and outflow energetics method  
  > "we used our tool $\mathrm{MOKA^{3D}}$(Modeling Outflows and Kinematics of AGN in 3D), presented in (cite: Marconcini2023)" (4.1 Multi-phase 3D disc kinematic model) [from (cite: Marconcini2023)]
- Gaussian-fit routine (Voronoi binning, KS test for number of components) follows earlier work  
  > "using a fiducial *p-value* of 0.8 (cite: Marasco2020)" (3.1 JWST/MIRI MRS emission line fitting) [from (cite: Marasco2020)]

### Not stated but needed to reproduce (our reading)

- CASA channel selection/velocity range and mask, clean threshold, and number of iterations for tclean
- Which two ALMA execution blocks/configurations were combined and the fluxscale/self-calibration status
- Exact CASA task used to combine the measurement sets and whether primary-beam correction was applied
- Details of the single-Gaussian fit to CO(2-1) per spaxel (initial guesses, spatial binning or smoothing, S/N threshold)
- MOKA3D fitting algorithm, priors and likelihood
- Sampler for the dynamical mass fit

## Analysis recipe

1. **Image CO(2-1) cube**: Combine two ALMA configurations, subtract uv continuum, tclean with Briggs weighting  
  > "The data were cleaned using the CASA task TCLEAN CASA task using a BRIGGS weighting scheme with ROBUST = 0.5" (2.3 ALMA)
   - software: CASA
   - parameter: robust = 0.5; pixel 90 mas; ~5 km/s channels  
  > "a pixel size of 90 mas, and an rms of 0.94 mJy/beam per channel" (2.3 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CO(2-1) line profile per spaxel**: Single Gaussian fit per spaxel, tested with chi2 and Kolmogorov-Smirnov test  
  > "a single Gaussian was sufficient to reproduce the line profile in each spaxel based on the $\chi^2$ and the Kolmogorov-Smirnoff test" (3.3 ALMA emission line fitting)
   - software: MPFIT
   - fitting: _not stated_
   - validation: chi2 and KS test  
  > "based on the $\chi^2$ and the Kolmogorov-Smirnoff test" (3.3 ALMA emission line fitting)
3. **Model disc rotation curve**: MOKA3D thin-disc multi-shell fit of rotation velocity, inclination and dispersion fixed after a single-shell fit  
  > "We initially fitted a single-shell model to the entire disc to derive global best-fit estimates of the circular velocity, disc inclination, and intrinsic velocity dispersion." (4.1 Multi-phase 3D disc kinematic model)
   - software: MOKA3D
   - parameter: PA fixed at 28 deg; 20 shells for CO(2-1)  
  > "N$_{shell}$ & N & 9 & 9 & 8 & 20" (Table moka_disc_fit)
   - assumption: thin disc with height smaller than PSF; shell width = PSF FWHM  
  > "we adopted a thin-disc geometry with a height smaller than the spatial PSF." (4.1 Multi-phase 3D disc kinematic model)
   - fitting: _not stated_
   - validation: Position angle checked against PaFit  
  > "we also checked that our measured value for the disc position angle from MUSE data is consistent with the values estimated with the *PaFit* python package" (4.1 Multi-phase 3D disc kinematic model)
4. **Fit dynamical mass from combined rotation curve**: Freeman exponential disc plus NFW halo fit to the rotation curve  
  > "fit the dynamical mass ($M_{dyn}$), the baryonic mass scale radius ($R_D$) and the dark matter characteristic velocity $v_h$" (4.2 Rotation curve fitting and dynamical mass)
   - assumption: NFW r0 = 8.1 kpc fixed  
  > "we assumed a characteristic scale length of r$_0$ = 8.1 $\pm$ 0.7 kpc" (4.2 Rotation curve fitting and dynamical mass)
   - fitting: Uncertainties at 16th and 84th percentiles; sampler not stated  
  > "Uncertainties on the derived parameters are evaluated at the 16th and 84th percentiles." (4.2 Rotation curve fitting and dynamical mass)
   - validation: _not stated_
5. **Search for cold molecular outflow and upper limit on mass**: PVDs along major/minor axes, channel maps, RMS in high-velocity channels converted to molecular gas mass  
  > "we estimate a 1 $\sigma$ molecular gas mass upper limit of 3.3 $\times$ 10$^{6}$ $\mathrm{M_\odot}$" (4.7 Cold and warm molecular phases)
   - parameter: 0.8 arcsec slit; 250-500 km/s high-velocity regions; aperture radius ~0.45 arcsec  
  > "we extracted the spectrum from a circular region centred on the nucleus and with a radius equal to the ALMA FWHM (i.e., $\sim$ 0.45)" (4.7 Cold and warm molecular phases)
   - assumption: R21 = 0.7; alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1  
  > "assuming a CO (2-1) to CO (1-0) luminosity ratio of R$_{21}$ = 0.7 (cite: Leroy2009; Sandstrom2013)" (4.7 Cold and warm molecular phases)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v6.1.1: Reduction and imaging of ALMA data  
  > "To reduce and analyse the data we used the Common Astronomy Software Applications (CASA) package version v6.1.1" (2.3 ALMA)
- **MOKA3D** : 3D kinematic modelling of disc and outflows  
  > "To model the multi-phase disc properties we used our tool $\mathrm{MOKA^{3D}}$" (4.1 Multi-phase 3D disc kinematic model)
- **MPFIT** : Gaussian emission-line fitting per spaxel  
  > "We used the MPFIT fitting tool (cite: Markwardt2009) to fit the emission lines in each spaxel." (3.1 JWST/MIRI MRS emission line fitting)
- **pPXF** : Continuum fitting of MIRI and MUSE spectra  
  > "The stellar continuum fit is performed with the pPXF tool" (3.2 MUSE emission line fitting)
- **WebbPSF** v.1.4.0: MIRI PSF modelling  
  > "we downloaded the MIRI MRS PSF model cube using the *WebbPSF* tool v.1.4.0" (7 MIRI/MRS PSF modeling)
- **PaFit** : Check of kinematic position angle  
  > "*PaFit* python package (cite: Krajnovic2006)" (4.1 Multi-phase 3D disc kinematic model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass | 1.09e10 | 0.08e10 | Msun | 4 | $M_{dyn}$ = 1.09 $\pm$ 0.08 $\times$ 10$^{10}$ $\mathrm{M_\odot}$, $R_D$ = 0.48 $\pm$ 0.02 kpc |
| Disc scale radius R_D | 0.48 | 0.02 | kpc | 4 | $R_D$ = 0.48 $\pm$ 0.02 kpc |
| Dark matter characteristic velocity v_h | 593 | 35 | km/s | 4 | $v_h$ = 593 $\pm$ 35 $\mathrm{km\,s^{-1}}$ |
| CO(2-1) disc inclination | 58 | 4 | deg | 3 | $\beta$ & Y & 55 $\pm$ 4 & 65 $\pm$ 9 & 58 $\pm$ 4 & 60 $\pm$ 9 |
| Cold molecular outflow mass 1-sigma upper limit | 3.3e6 | not stated | Msun | 5 | we estimate a 1 $\sigma$ molecular gas mass upper limit of 3.3 $\times$ 10$^{6}$ $\mathrm{M_\odot}$ |

## Qualitative findings

- No evidence of cold or warm molecular outflows; CO(2-1) and H2 are consistent with pure rotation.  
  > "here confirms the pure rotating nature of the cold molecular phase in NGC 424" (4.7 Cold and warm molecular phases)
- Velocity dispersion enhanced along the minor axis in all gas phases, perpendicular to the ionised outflow.  
  > "show an elongated enhancement of gas velocity dispersion along the disc minor axis" (4.6 Enhanced velocity dispersion along the galaxy minor axis)

## Claim tuples

- H: Is there a cold molecular outflow in NGC 424? | E: PVDs, channel maps and high-velocity RMS of ALMA CO(2-1) | R: No emission in high-velocity channels; mass upper limit 3.3e6 Msun | F: No cold molecular outflow detected | **supported**
- H: Can multi-phase rotation curves yield the dynamical mass? | E: MOKA3D disc fits to MIRI, ALMA, MUSE, then Freeman+NFW fit | R: Mdyn = 1.09e10 Msun, R_D = 0.48 kpc | F: Consistent rotation curve across phases from pc to ~5 kpc | **supported**
- H: The ionised outflow causes enhanced dispersion along the minor axis | E: Compared 3D outflow modelling with dispersion maps | R: Dispersion enhancement perpendicular to outflow, no clear radio jet | F: Outflow may play a key role | **partially**

## Reasoning

- Why this data: Cold molecular phase traced by archival ALMA CO(2-1) to complete the multi-phase view.  
  > "To investigate the cold molecular gas phase in NGC 424 we analysed archival ALMA 12-m array band 6 observations" (2.3 ALMA)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observations cover only ~5 kpc, so DM density and scale length cannot be constrained simultaneously.  
  > "we cannot properly constrain simultaneously the dark matter characteristic density and length" (4.2 Rotation curve fitting and dynamical mass)
- Caveat (inferred, ours): Dark matter scale length borrowed from the Milky Way
- Caveat (inferred, ours): Inclination and dispersion fixed across the disc, possibly degenerate with rotation velocity
- Caveat (inferred, ours): Interpretation of the dispersion enhancement as outflow-driven is not tested quantitatively

## Reproducibility

- Data public (paper): ALMA data archival; calibrated MS requested from European ARC  
  > "We requested the calibrated measurement sets from the European ALMA Regional Centre (cite: Hatziminaoglou2015)." (2.3 ALMA)
- Products in archive: _not stated_
- Missing: MOKA3D code and fitting details (Marconcini et al. 2025 in press)
- Missing: tclean masks, thresholds and channel selection
- Missing: Per-spaxel CO fit settings
- Data volume (inferred): ~5-20 GB for the ALMA measurement sets
- Score (inferred): 4/5, ALMA role is minor; imaging is partly specified but the kinematic modelling code and fit details are incomplete.
- Rediscovery candidate: no, ALMA is a minor component and the central modelling relies on MOKA3D and JWST/MUSE data.

## Links

- Method: (cite: Marconcini2023) (MOKA3D kinematic model and outflow energetics)
- Related: MIRACLE (JWST program 6138)
- Related: MAGNUM

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 79,
  "stated": 51,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
