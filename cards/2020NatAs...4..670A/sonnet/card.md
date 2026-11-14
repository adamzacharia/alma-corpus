# Infalling gas in a Lyman-α blob

`2020NatAs...4..670A` | Nature Astronomy 2020 | first author: Ao, Yiping | arXiv: 2003.06099 | DOI: 10.1038/s41550-020-1033-3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there kinematic evidence for infalling gas in the Lyα blob LAB6, from the Lyα line profile relative to the systemic velocity set by ALMA CO and [CI] lines?  
  > "Here we analyse the gas kinematics within an LAB providing rare observational evidence for infalling gas." (abstract)
- Target **LAB6 (LAB6.1, LAB6.2) in the Francis cluster J2143-4423**: coordinates _not stated_; z/distance z = 2.3691±0.0004 (CO); later quoted 2.3796±0.0004  
  > "toward one LAB, LAB6, in the Francis cluster (J2143$-$4423)(cite: Francis1996; Ao2015; Palunas2004)" (Main text); "The CO J=$-$6 line indicates a redshift of 2.3691$\pm$0.0004." (Main text); distance from CO and [CI] submm lines from ALMA  
  > "toward one LAB, LAB6, in the Francis cluster (J2143$-$4423)(cite: Francis1996; Ao2015; Palunas2004)" (Main text); "The CO J=$-$6 line indicates a redshift of 2.3691$\pm$0.0004." (Main text)

## Data provenance

- ALMA projects: 2015.1.00952.S
- bands: _not stated_
- frequencies and spectral setup: FDM at 238.76 GHz (LSB); TDM at 254.51 GHz (USB)  
  > "in the Frequency Division Mode (FDM) at the central frequency of 238.76 GHz in the lower sideband and in the Time Division Mode (TDM) at the central frequency of 254.51 GHz in the upper sideband" (Methods, ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 36 12 m antennas  
  > "The observations were carried out on 2016 May 7th with 36 12 meter antennas and baselines between 16.5 and 629 m." (Methods, ALMA observations)
- configurations: _not stated_
- baselines: 16.5 to 629 m  
  > "baselines between 16.5 and 629 m" (Methods, ALMA observations)
- angular resolution: 0.64"x0.51", PA 9 deg  
  > "The achieved synthesised beamsize (full-width at half maximum, FWHM) is 0.64$^{\prime\prime}\times$0.51$^{\prime\prime}$ with a position angle of 9 degrees east of north." (Methods, ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 40 μJy/beam  
  > "The continuum maps have an rms noise level of 40 $\mu$Jy/beam." (Methods, ALMA observations)
- time on source: 25 minutes  
  > "The total on-source observing time was 25 minutes." (Methods, ALMA observations)
- observing dates: 2016 May 7  
  > "The observations were carried out on 2016 May 7th" (Methods, ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=7-6 (printed as J=-6) (not stated)
- Other facility **VLT/X-shooter**: Lyα spectrum of LAB6 (UVB arm)  
  > "Note that only the UVB arm covering the Ly$\alpha$ spectroscopic data is presented in this paper." (Methods, VLT/X-shooter observations)
- Other facility **VLT/HAWK-I**: J and Ks near-IR photometry  
  > "Broadband filters, J band at 1.258 $\mu$m and Ks band at 2.146 $\mu$m, were used for the observations." (Methods, Near- to mid-infrared data)
- Other facility **Spitzer IRAC**: 3.6-8.0 μm photometry  
  > "Mid-infrared data were obtained using the *Spitzer* Infrared Array Camera (IRAC) at 3.6, 4.5, 5.8 and 8.0 $\mu$m(cite: Colbert2011)." (Methods, Near- to mid-infrared data)
- External data: Herschel-based SED model, total FIR luminosity and dust mass of LAB6  
  > "The dust mass from the SED model(cite: Ao2015) is (2.1$\pm$0.5)$\times$10$^{8}$M$\rm_\odot$ after rescaling" (Methods, Molecular gas mass) [from (cite: Ao2015)]
- External data: Total Lyα luminosity of the whole LAB  
  > "which is about 10% of the total luminosity in the whole LAB(cite: Palunas2004)" (Methods, VLT/X-shooter) [from (cite: Palunas2004)]
- External data: Compilation of Lyα shell-model spectra used for interpolation  
  > "based on interpolating a compilation of Ly$\alpha$ spectra(cite: Gronke2015) from the shell model" (Methods, Shell model fit) [from (cite: Gronke2015)]

## Processing

### Calibration

- pipeline or manual: CASA, standard manner  
  > "The data were reduced with the Common Astronomy Software Application (CASA) package in a standard manner." (Methods, ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas originally; phase calibrator J2139-4235 rescaled using bandpass calibrator J2056-4714 flux interpolated from ALMA catalog  
  > "Therefore, the flux density of the phase/gain calibrator J2139-4235 has been re-scaled using the flux of the bandpass calibrator interpolated with the measurements in the ALMA catalog." (Methods, ALMA observations)
- flux scale uncertainty: _not stated_
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
- primary beam correction: primary beam ~24" at 246.6 GHz (only size stated)  
  > "The primary beam size is about 24$^{\prime\prime}$ at the central frequency of 246.6 GHz." (Methods, ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.64"x0.51", PA 9 deg  
  > "The achieved synthesised beamsize (full-width at half maximum, FWHM) is 0.64$^{\prime\prime}\times$0.51$^{\prime\prime}$" (Methods, ALMA observations)
- final rms: 40 μJy/beam (continuum)  
  > "The continuum maps have an rms noise level of 40 $\mu$Jy/beam." (Methods, ALMA observations)

### Inherited from earlier work

- SED model, FIR luminosity and dust mass of LAB6  
  > "predicted value of 2.43 mJy by the SED model of LAB6(cite: Ao2015)" (Methods, Molecular gas mass) [from (cite: Ao2015)]
- Spitzer IRAC data reduction  
  > "The details of the data reductions can be found in the literature(cite: Colbert2011)." (Methods, Near- to mid-infrared data) [from (cite: Colbert2011)]
- Reverse of expanding shell model  
  > "This is the reverse version of the expanding shell model(cite: Verhamme2006)" (Methods, Shell model fit) [from (cite: Verhamme2006)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size
- Continuum-free channels and line-subtraction details
- Channel width and moment-map clipping thresholds
- Rest frequencies and exact CO transition
- MCMC sampler, priors and chain settings for shell fit
- Bagpipes priors and star formation history model
- Exact CASA version
- Inconsistent redshifts (2.3691 vs 2.3796) not reconciled

## Analysis recipe

1. **Measure continuum and line fluxes**: Imaging of ALMA data and CASA IMFIT for continuum source flux densities  
  > "The flux densities of the detected sources were measured with the CASA task IMFIT." (Methods, ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **SED modelling of stellar properties**: Bagpipes fit to HAWK-I and IRAC photometry with redshift fixed to 2.3691  
  > "To constrain the physical properties, we fixed the redshift to 2.3691" (Methods, Near- to mid-infrared)
   - software: Bagpipes
   - assumption: 15% error per IRAC band for calibration  
  > "a 15% error bar is adopted for each IRAC band to account for the calibration uncertainty" (Table)
   - fitting: _not stated_
   - validation: Photometric redshift consistent with submm lines  
  > "the photometric redshift derived from Bagpipes is 2.53$_{-0.38}^{+0.33}$, consistent with that determined from the submm lines" (Methods)
3. **Derive SFR, molecular gas and dust mass**: SFR from L_FIR (Kennicutt) and CO line luminosity (Lu2015), averaged; gas mass from CO with line ratio and X_CO  
  > "From the mean value of the SFRs from the above two methods, the derived SFR of LAB6.1 is approximately 1100 M$_{\odot}$ yr$^{-1}$" (Methods, Molecular gas mass)
   - assumption: L_CO(7-6)/L_CO(1-0)=0.24; ULIRG X_CO (Downes1998)  
  > "Assuming a line ratio of 0.24 for $L_{\rm CO(7-6)}$/$L_{\rm CO(1-0)}$(cite: Carilli2013; Yang2017)" (Methods)
   - assumption: LAB6.1 fraction of FIR luminosity follows 1.2 mm continuum  
  > "the fractional contribution from LAB6.1 follows that of the 1.2 mm continuum" (Methods)
   - fitting: _not stated_
   - validation: SFR consistent with SED fitting  
  > "which is consistent with the value derived with the near- and mid-infrared SED fitting" (Methods)
4. **Fit Lyα profile with contracting shell model**: MCMC fit of three-parameter infalling shell (V, T, N_HI) interpolating Gronke2015 spectra  
  > "A Markov Chain Monte Carlo calculation is performed to constrain the parameters, based on interpolating a compilation of Ly$\alpha$ spectra(cite: Gronke2015) from the shell model." (Methods, Shell model fit)
   - assumption: Infalling gas uniformly in a thin shell; radius ~8 kpc  
  > "infalling gas is uniformly located in a thin shell of neutral gas" (Methods)
   - fitting: MCMC; chi2=53.5 for 74 dof  
  > "with $\chi^2 =53.5$ for 74 degrees of freedom" (Methods)
   - validation: chi2 acceptable, no over-fitting; model misses flux near v=0  
  > "it misses the Ly$\alpha$ flux near $v=0$ in the red peak, which implies that a uniform shell model is over-simplified" (Methods)

## Software

- **CASA** : Data reduction and IMFIT flux measurement  
  > "The flux densities of the detected sources were measured with the CASA task IMFIT." (Methods)
- **Bagpipes** : SED modelling  
  > "we constrain the physical properties of the host galaxy from SED modeling with near- to mid-infrared data" (Methods)
- **reflex X-shooter pipeline** 2.9.1: X-shooter data reduction  
  > "The data reduction has been performed using the **reflex** X-shooter pipeline 2.9.1(cite: Freudling2013)." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| LAB6.1 1.2 mm flux density | 1.57 | 0.11 | mJy | 1 | with a flux density of 1.57$\pm$0.11 mJy |
| LAB6.2 flux density | 1.60 | 0.24 | mJy | 1 | detected with a flux density of 1.60$\pm$0.24 mJy |
| CO redshift of LAB6.1 | 2.3691 | 0.0004 | dimensionless | 1 | The CO J=$-$6 line indicates a redshift of 2.3691$\pm$0.0004. |
| Shell infall velocity (model 1) | -33.8 | +3.2/-3.1 | km/s | 4 | $V=-33.8^{+3.2}_{-3.1} {\rm \thinspace km\thinspace s^{-1}}$ |
| Gas inflow rate | 1.7 | not stated | Msun/yr | 4 | The gas inflow rate is then about $1.7{{\rm M}_{\odot} }\thinspace {\rm yr}^{-1}$. |
| Molecular gas mass | 2.2e10 | 1.1e10 | Msun | 3 | we find a molecular gas mass of (2.2$\pm$1.1)$\times$10$^{10}$M$\rm_\odot$ |
| SFR of LAB6.1 | ~1100 | not stated | Msun/yr | 3 | the derived SFR of LAB6.1 is approximately 1100 M$_{\odot}$ yr$^{-1}$ |
| Stellar mass log | 11.00 | +0.08/-0.14 | log Msun | 2 | log(M$_{\rm stellar}$/M$_{\odot}$) = 11.00$^{+0.08}_{-0.14}$ |

## Qualitative findings

- Lyα is blue-skewed, offset ~-150 km/s from CO systemic velocity, indicating infalling gas  
  > "the profile of the observed Ly$\alpha$ line appears to be blue-skewed" (Main text)

## Claim tuples

- H: Gas is infalling onto the central galaxy of LAB6 | E: Compare X-shooter Lyα profile to ALMA CO/[CI] systemic velocity; fit shell model | R: Lyα blue-skewed, peak ~-150 km/s; shell infall V≈-34 km/s | F: Direct kinematic evidence of infall, not necessarily cooling radiation | **supported**
- H: Infall is important for feeding the galaxy | E: Shell mass and dynamical time | R: Inflow rate 1.7 Msun/yr vs SFR 1100 | F: Infall negligible by mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Galactic fountain (fallback) vs cold streams as origin of infalling gas  
  > "it is possible that the gas was ejected earlier as part of the galactic wind from the central region and is falling back" (Main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Uniform shell model over-simplified; results rough estimate  
  > "The above modelling result should be taken as a rough estimate." (Methods)
- Caveat (inferred, ours): Redshift inconsistency 2.3691 vs 2.3796 (and z=2.38 field) unexplained
- Caveat (inferred, ours): Single object, low-S/N red peak
- Caveat (inferred, ours): Flux rescaling of calibrator is ad hoc
- Caveat (inferred, ours): Shell model does not separate cooling from scattering

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MCMC details
- Missing: Bagpipes configuration
- Missing: X-shooter extraction details
- Data volume (inferred): ~5-10 GB
- Score (inferred): 3/5, ALMA data identified and processing outlined, but imaging and fitting settings are largely missing.
- Rediscovery candidate: no, Imaging recipe incomplete and key result relies on X-shooter data and a custom shell fit.

## Links

- Method: (cite: Gronke2015) (Shell model spectra grid)
- Method: (cite: Carnall2018) (Bagpipes)
- Companion: (cite: Ao2015) (Earlier Herschel SED study of LAB6)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
