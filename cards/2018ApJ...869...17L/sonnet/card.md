# Gaps and Rings in an ALMA Survey of Disks in the Taurus Star-forming Region

`2018ApJ...869...17L` | The Astrophysical Journal 2018 | first author: Long, Feng | arXiv: 1810.06044 | DOI: 10.3847/1538-4357/aae8e1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the properties and likely origins (planets vs condensation fronts) of dust gaps and rings in 12 Taurus disks with substructure from an unbiased high-resolution ALMA 1.33 mm survey?  
  > "Rings are the most frequently revealed substructure in ALMA dust observations of protoplanetary disks, but their origin is still hotly debated." (abstract)
- Target **12 Taurus disks (CIDA 9, IP Tau, RY Tau, UZ Tau E, DS Tau, FT Tau, MWC 480, DN Tau, GO Tau, IQ Tau, DL Tau, CI Tau)**: coordinates _not stated_; z/distance 127-171 pc (Table 2)  
  > "The distance for each target is adopted from the Gaia DR2 parallax" (Table 2 notes); distance from Gaia DR2 parallax  
  > "The distance for each target is adopted from the Gaia DR2 parallax" (Table 2 notes)

## Data provenance

- ALMA projects: 2016.1.01164.S
- bands: Band 6 (1.33 mm)  
  > "observed 32 disks in the Taurus star-forming region in Band 6 (1.33 mm)" (2.1 Observations and Data Reduction)
- frequencies and spectral setup: Two continuum basebands centered at 218 and 233 GHz, 1.875 GHz bandwidth each; mean 225.5 GHz; two other windows cover CO isotopologues (not used)  
  > "Two basebands were setup for continuum observations, centered at 218 and 233 GHz with bandwidths of 1.875 GHz." (2.1 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-3697 m (15-2780 kλ), 45-47 12-m antennas  
  > "using 45-47 12-m antennas on baselines of 21$\sim$3697 m (15$\sim$2780 k$\lambda$)" (2.1 Observations and Data Reduction)
- angular resolution: ~0.12'' (typical beam 0.14''x0.11'')  
  > "resulting in a typical beam size of $0.14''\times0.11''$, and a median continuum rms of 0.05 mJy beam$^{-1}$" (2.1 Observations and Data Reduction)
- max recoverable scale: ~1.3'' (~180 au)  
  > "These observations are not sensitive to emission larger than $\sim 1.3''$" (2.1 Observations and Data Reduction)
- sensitivity: median continuum rms 0.05 mJy/beam  
  > "a median continuum rms of 0.05 mJy beam$^{-1}$" (2.1 Observations and Data Reduction)
- time on source: ~4 min per target for bright group; ~10 min per target for other groups  
  > "On-source integration times were $\sim$4 min per target for one group with relatively bright disks and $\sim$10 min per target for the other three groups." (2.1 Observations and Data Reduction)
- observing dates: late August to early September 2017  
  > "All observations were obtained from late August to early September 2017" (2.1 Observations and Data Reduction)
- pi or archival as stated: Cycle 4 program, PI Herczeg  
  > "Our ALMA Cycle 4 program (ID: 2016.1.01164.S; PI: Herczeg)" (2.1 Observations and Data Reduction)
- Other facility **Gaia DR2**: Parallax distances to targets  
  > "The distance for each target is adopted from the Gaia DR2 parallax" (Table 2 notes)
- External data: Pre-ALMA 1.33 mm fluxes for Taurus disks (comparison; fluxes for the other 20 disks in dust mass plot)  
  > "adopted from (cite: andrews2013) for the other Taurus members" (4.1 Source Properties) [from (cite: andrews2013)]
- External data: Spectral types and stellar luminosities (updated to Gaia distances)  
  > "Spectral type and stellar luminosity are adopted from the listed references ((cite: herczeg2014) and Liu et al. submitted)" (Table 2 notes) [from (cite: herczeg2014); Liu et al. submitted]
- External data: Condensation temperatures for N2, CO and clathrate ice  
  > "The condensation temperatures, adopted from (cite: zhang2015)" (4.3.2 Condensation Fronts) [from (cite: zhang2015)]
- Simulation/model as data: Rosotti et al. 2016 hydrodynamic simulation diagnostic (ring-gap separation vs planet mass) used to infer planet masses  
  > "An alternative way to estimate the mass of a planet associated with the gap is by linking the diagnostic of the gap-ring distance to hydrodynamic simulations (cite: rosotti2016)." (4.3.1 Planet-disk Interactions)

## Processing

### Calibration

- pipeline or manual: ALMA-provided data reduction scripts in CASA  
  > "Following the data reduction scripts provided by ALMA, the atmospheric phase noise was first reduced using water vapor radiometer measurements." (2.1 Observations and Data Reduction)
- casa version: CASA 5.1.1  
  > "The ALMA data were calibrated using the Common Astronomy Software Applications (CASA) package (cite: McMullin2007), version 5.1.1." (2.1 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 or J1107-4449 depending on group  
  > "J0510+1800 | J0510+1800 | J0512+2927" (Table 1)
- flux scale uncertainty: ~10%  
  > "we estimate an absolute flux calibration uncertainty of $\sim$10%." (2.1 Observations and Data Reduction)
- self calibration: S/N≳100: three phase rounds + one amplitude; S/N<100: one phase + one amplitude; S/N<30: none; stopped when no S/N improvement  
  > "For targets with initial signal-to-noise ratio (S/N) $\ensuremath{\gtrsim}$100 in the image, we applied three rounds of phase (down to the integration time) and one round of amplitude self-calibration." (2.1 Observations and Data Reduction)

### Imaging

- task: CASA TCLEAN  
  > "Continuum images were then created from the calibrated visibilities with CASA task TCLEAN." (2.1 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +0.5  
  > "The final continuum images were produced with Briggs weighting and a robust parameter of +0.5 in TCLEAN" (2.1 Observations and Data Reduction)
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
- final beam: typical 0.14''x0.11''  
  > "resulting in a typical beam size of $0.14''\times0.11''$" (2.1 Observations and Data Reduction)
- final rms: median 0.05 mJy/beam  
  > "a median continuum rms of 0.05 mJy beam$^{-1}$" (2.1 Observations and Data Reduction)

### Inherited from earlier work

- Stellar masses computed with same method as Pascucci et al. 2016  
  > "Stellar masses are re-calculated with the stellar luminosity and effective temperature listed here using the same method in (cite: pascucci2016)." (Table 2 notes) [from (cite: pascucci2016)]
- R_eff defined as radius enclosing 90% of flux  
  > "is defined here as the radius where 90% of the total flux is encircled (cite: tripathi2017)" (3.2.2 mm Flux and Dust Disk Size) [from (cite: tripathi2017)]
- RADMC-3D temperature model setup follows Liu et al. 2018  
  > "The details about the model setup can be found in Liu et al. (2018)." (Footnote 9) [from Liu et al. (2018)]
- Dust opacity and optically thin mass formula  
  > "The dust masses are estimated from the 1.33 mm continuum flux density (e.g., (cite: beckwith1990))" (4.1 Source Properties) [from (cite: beckwith1990)]

### Not stated but needed to reproduce (our reading)

- Which spectral channels/line-free channels were used for continuum
- Image size, cell size, clean threshold, masking and deconvolver for TCLEAN
- Self-calibration solution intervals for amplitude and the per-target number of rounds
- Prior ranges for ring/Gaussian amplitudes, locations and widths in the MCMC
- Initial guesses for each disk's model components
- Details of the uv-data averaging/binning for the Galario fits
- Gap-ring pair selection details for the well-resolved criteria
- Flux uncertainty on dust masses and distance uncertainty treatment
- Details of the RADMC-3D setup beyond footnote (dust composition, grain sizes)

## Analysis recipe

1. **Calibrate and self-calibrate, image continuum**: CASA pipeline-script calibration, phase and amplitude self-calibration, TCLEAN imaging  
  > "Continuum images were then created from the calibrated visibilities with CASA task TCLEAN." (2.1 Observations and Data Reduction)
   - software: CASA
   - parameter: Briggs robust +0.5  
  > "Briggs weighting and a robust parameter of +0.5 in TCLEAN" (2.1 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: S/N checked after each self-cal round  
  > "After each round of self-calibration, we checked the image S/N" (2.1 Observations and Data Reduction)
2. **Select disks with substructure**: Fit elliptical Gaussian with IMFIT for major axis; inspect radial profile; reduced chi2 of Gaussian fit to radial profile within central 1.5''; highest chi2 chosen  
  > "The disks selected for this paper have the largest $\chi^2$ values." (2.2 Sample Selection)
   - software: CASA IMFIT
   - fitting: _not stated_
   - validation: Twelve of 32 disks selected; choice of twelve described as somewhat arbitrary  
  > "The choice to focus on twelve sources is somewhat arbitrary" (2.2 Sample Selection)
3. **Fit visibilities with axisymmetric radial intensity models**: Central Gaussian or exponentially tapered power-law plus radial Gaussian rings; Fourier transformed with Galario; MCMC fit with emcee  
  > "The model visibilities are then created by Fourier transforming the disk model intensity profile using the publicly available code *Galario* (cite: tazzari2018)." (3.1 Modeling Procedure)
   - software: Galario, emcee, CASA IMFIT
   - parameter: 100 walkers, 5000 steps, burn-in ~2000; second run 5000 more steps; posterior from last 1000 steps; radial grid 0.0001''-4'' step 0.001''  
  > "with 100 walkers and 5000 steps for each walker. The burn-in phase for convergence is typically $\sim$2000 steps." (3.1 Modeling Procedure)
   - parameter: Uniform priors: ±20 deg for i and PA, ±0.5 arcsec for offsets  
  > "Prior ranges are set as $\pm$20 deg for $i$ and PA, and $\pm$0.5 arcsec for the position offsets." (3.1 Modeling Procedure)
   - assumption: Axisymmetry  
  > "Axisymmetry is assumed, since high-contrast asymmetries in the dust emission are not seen" (3.1 Modeling Procedure)
   - fitting: emcee MCMC; median and 16th-84th percentile  
  > "The statistical uncertainty for each parameter is estimated as the interval from the 16th to the 84th percentile." (3.1 Modeling Procedure)
   - validation: Compare visibility profiles, images, radial cuts; add ring or tapered power-law if symmetric residuals ≳5-10σ  
  > "If significant symmetrical residuals ($\gtrsim5-10\sigma$) are present, we either include an additional Gaussian ring component or replace the central Gaussian profile with a tapered power-law." (3.1 Modeling Procedure)
4. **Derive flux, R_eff, gap and ring properties**: Integrate best-fit profile; R_eff at 90% flux; gap location at local minimum; gap width full width at half depth; contrast ratio ring peak/gap; uncertainties from 100 chain samples  
  > "The gap width is defined as the full width at half depth" (4.2 Properties of Gaps and Rings)
   - fitting: _not stated_
   - validation: Fluxes compared with pre-ALMA measurements  
  > "our flux measurements at 1.33 mm are consistent with pre-ALMA interferometry measurements" (3.2.2 mm Flux and Dust Disk Size)
5. **Dust masses**: Optically thin M_dust = D^2 F / (kappa B(T))  
  > "with a dust opacity $\kappa_\nu=2.3\,\rm{cm}^2\,\rm{g}^{-1} \times (\nu/230\,\rm{GHz})^{0.4}$" (4.1 Source Properties)
   - assumption: T_dust = 20 K, optically thin, kappa=2.3 cm2/g (nu/230GHz)^0.4  
  > "a Planck function $B_\nu(T_{\rm dust})$ for a dust temperature of 20 K for each disk at distance $D$, assuming the dust is optically thin" (4.1 Source Properties)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare gaps with planet-disk interaction expectations**: Normalized ring-gap distance vs gap location and stellar mass; planet mass via 4 R_Hill and Rosotti et al. 2016 diagnostic  
  > "If we simply assume that the gap radius corresponds to 4 $R_{\rm Hill}$ (cite: dodson-Robinson2011), most of our gaps are related to planets with mass of 0.1–0.5 $M_{\rm J}$" (4.3.1 Planet-disk Interactions)
   - assumption: alpha=1e-4 or 1e-2; simulations for 1 Msun star rescaled by mass ratio  
  > "When the turbulence parameter (cite: shakura1973) is assumed to be $\alpha=10^{-4}$" (4.3.1 Planet-disk Interactions)
   - fitting: _not stated_
   - validation: Compared to CI Tau hydrodynamic modeling of Clarke et al. 2018  
  > "consistent with our simple estimation here" (Footnote 7)
7. **Compare gap locations with ice lines**: Midplane temperature from Kenyon & Hartmann irradiated flared disk; ice line radii for N2, CO, clathrate; RADMC-3D check  
  > "where the flaring angle $\phi_{\mathrm{inc}}$ is assumed to be 0.05 (cite: dullemond2004)" (4.3.2 Condensation Fronts)
   - software: RADMC-3D
   - parameter: N2 12-15 K, CO 23-28 K, clathrate CO+N2 41-46 K  
  > "N$_2$ (12-15 K), CO (23-28 K), and clathrate hydrated CO and N$_2$ (41-46 K)" (4.3.2 Condensation Fronts)
   - assumption: flaring angle 0.05; photospheric luminosity only  
  > "we use only the photospheric luminosity rather than the total luminosity" (Footnote 8)
   - fitting: _not stated_
   - validation: RADMC-3D models give similar temperature profiles beyond 20 au except RY Tau  
  > "yields temperature profiles that are similar to analytic solutions" (4.3.2 Condensation Fronts)

## Software

- **CASA** 5.1.1: Calibration, TCLEAN imaging, IMFIT  
  > "CASA (v5.1.1; (cite: McMullin2007))" (Software)
- **Galario** : Fourier transform of model profiles to visibilities  
  > "using the publicly available code *Galario* (cite: tazzari2018)" (3.1 Modeling Procedure)
- **emcee** : MCMC fitting of visibilities  
  > "is later performed with the *emcee*[^1] package (cite: Foreman-Mackey2013)" (3.1 Modeling Procedure)
- **RADMC-3D** : Midplane temperature profiles  
  > "we use the RADMC-3D code (cite: dullemond2012) to run radiative transfer models" (Footnote 9)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Typical beam size | 0.14x0.11 | not stated | arcsec | 1 | a typical beam size of $0.14''\times0.11''$ |
| MWC 480 total 1.33 mm flux | 267.76 | +0.18/-0.21 | mJy | 4 | / MWC 480 / 267.76$_{-0.21}^{+0.18}$ / 104.97$_{-0.16}^{+0.16}$ / |
| CI Tau effective radius | 173.8 | +0.47/-0.32 | au | 4 | / CI Tau / 142.4$_{-0.24}^{+0.15}$ / 173.8$_{-0.32}^{+0.47}$ / |
| RY Tau flux | 210.39 | +0.09/-0.1 | mJy | 4 | / RY Tau / 210.39$_{-0.1}^{+0.09}$ / 60.8$_{-0.13}^{+0.0}$ / |
| Number of gap-ring pairs analyzed | 19 | not stated | dimensionless | 4 | We analyze a total of 19 gap and ring pairs |
| Gap locations range | 10-120 | not stated | au | 4 | gaps are located from 10 to 120 au with no preferred distance |
| Normalized gap-ring distance | 0.2-0.3 | not stated | dimensionless | 6 | The normalized gap-ring distance is typically 0.2–0.3 |
| Planet mass for alpha=1e-4 at diagnostic 0.25 | ~15 (0.05 MJ) | not stated | M_earth | 6 | the diagnostic of 0.25 corresponds to a planet mass $\sim$ 15 M$_\oplus$ (0.05 M$_{\rm J}$) |
| Gaps near ice lines | 5 near CO; 2 near clathrate CO+N2; 1 near N2; 7 unrelated | not stated | count | 7 | The other seven gaps are unrelated to any of the ice lines we consider here. |

## Qualitative findings

- Axisymmetric rings and gaps are common; spirals and high-contrast azimuthal asymmetries are not detected  
  > "While axisymmetric rings and gaps are common within our sample, spiral patterns and high contrast azimuthal asymmetries are not detected." (abstract)
- Disks with multiple rings tend to be more massive and more extended  
  > "Disks with multiple rings tend to be more massive and more extended." (abstract)

## Claim tuples

- H: Gaps are opened by embedded planets | E: Compare gap/ring location, width, contrast and separations with planet-disk interaction expectations | R: Normalized ring-gap separations 0.2-0.3; low contrast in most pairs; planet masses ~0.05-0.5 MJ | F: Most gaps consistent with low-mass planets (super-Earths/Neptunes) with low turbulence alpha=1e-4 | **partially**
- H: Condensation fronts universally create gaps and rings | E: Compare gap locations with CO and N2 ice line radii from a temperature profile | R: Only about 8 of 15 considered gaps lie near an ice line | F: Condensation fronts are not a universal mechanism | **supported**
- H: Substructures depend on stellar and disk properties | E: Place disks in M*-Mdust plane; compare ring multiplicity with Mdust and Reff | R: Substructures across wide stellar mass and brightness; multi-ring disks brighter and larger | F: Substructure is widespread; multiple rings link to massive extended disks | **supported**

## Reasoning

- Why this data: Survey designed to be unbiased with respect to previous substructure detections and cover a wide range of brightness  
  > "designed to cover a wide range of sub-mm brightness and to be unbiased to previously known substructures" (abstract)
- Why this method: Fitting in the Fourier plane to precisely quantify morphology  
  > "our analysis is performed in the Fourier plane by comparing the observed visibilities to synthetic visibilities computed from a model intensity profile" (3.1 Modeling Procedure)
- Alternative: Nuker profile instead of an extra Gaussian ring for outer disk gave consistent results  
  > "we test with a Nuker profile, which could produce an asymmetric ring (cite: tripathi2017)." (Footnote 2)
- How they decided it was enough: _not stated_
- Limitation (authors): Formal errors on fit parameters likely underestimated  
  > "suggest that the formal errors listed in Table 3 are likely underestimated" (3.2.1 Best-Fit Models)
- Limitation (authors): Dust mass uncertainties ignore temperature and optical depth  
  > "do not take into account the differences in dust temperature and dust optical depth" (4.1 Source Properties)
- Limitation (authors): Model fails to reproduce amplitude of azimuthal asymmetries  
  > "our model fail to accurately reproduce the amplitude of the substructure component" (3.2 Modeling Results)
- Caveat (inferred, ours): Planet masses depend strongly on assumed alpha and simulations for 1 Msun star
- Caveat (inferred, ours): Most gaps are unresolved, so widths and contrasts are beam-limited
- Caveat (inferred, ours): Sample of 12 selected by chi2 with an arbitrary cut; selection effects in statistics
- Caveat (inferred, ours): Ice-line comparison depends on analytic temperature profile and condensation temperatures
- Caveat (inferred, ours): Gaussian ring parametrization imposes shape choices

## Reproducibility

- Data public (paper): Project ID listed; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: 2016.1.01164.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full TCLEAN parameters and self-cal solints
- Missing: MCMC initial guesses and ring priors per disk
- Missing: Full-sample paper details for selection
- Missing: RADMC-3D setup details
- Data volume (inferred): ~100-300 GB raw for 4 execution groups (several MS files); calibrated continuum visibilities much smaller
- Score (inferred): 6/5, Public data and well-described fitting approach with named tools, but imaging and per-disk fit details missing.
- Rediscovery candidate: yes, Data are public, the visibility-fitting recipe is largely specified, and results are numeric (Table 3 and 4).

## Links

- Method: (cite: tazzari2018) (Galario code for visibility modeling)
- Method: (cite: Foreman-Mackey2013) (emcee sampler)
- Method: (cite: rosotti2016) (Planet mass diagnostic from gap-ring separation)
- Companion: Liu et al. (2018) (Radiative transfer modeling of MWC 480)
- Companion: (cite: clarke2018) (Higher-resolution ALMA study of CI Tau gaps)
- Companion: Long et al. in prep (Full sample of 32 disks)
- Related: ALMA Cycle 4 Taurus survey of 32 disks (2016.1.01164.S)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 91,
  "stated": 65,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
