# The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback

`2019A&A...628A.118B` | Astronomy and Astrophysics 2019 | first author: Bischetti, M. | arXiv: 1903.10528 | DOI: 10.1051/0004-6361/201935524

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Does the hyper-luminous radio-quiet QSO PDS 456, which hosts a powerful UFO, have a kpc-scale molecular outflow, and what are its energetics relative to energy-conserving expansion?  
  > "In order to study the interplay between UFOs and large-scale outflows in the still little explored high-$L_{\rm Bol}$ regime, we have targeted with ALMA the QSO PDS 456" (Introduction)
- Target **PDS 456**: coordinates RA 17:28:19.79, Dec -14:15:55.86 (CO(3-2) peak)  
  > "the most luminous, radio-quiet AGN ($L_{\rm Bol}$ $\sim10^{47}$ erg s$^{-1}$) in the local Universe at $z\simeq0.18$" (Introduction); "The peak of the CO(3$-$2) emission is located at RA (17:28:19.79 $\pm$ 0.01), Dec (-14:15:55.86 $\pm$ 0.01)" (Results); z/distance z_CO = 0.1850±0.0001; ~3.1 kpc/arcsec  
  > "the most luminous, radio-quiet AGN ($L_{\rm Bol}$ $\sim10^{47}$ erg s$^{-1}$) in the local Universe at $z\simeq0.18$" (Introduction); "The peak of the CO(3$-$2) emission is located at RA (17:28:19.79 $\pm$ 0.01), Dec (-14:15:55.86 $\pm$ 0.01)" (Results); distance from CO(3-2) line peak from this work; cosmology H0=69.6, Om=0.286, OL=0.714  
  > "the most luminous, radio-quiet AGN ($L_{\rm Bol}$ $\sim10^{47}$ erg s$^{-1}$) in the local Universe at $z\simeq0.18$" (Introduction); "The peak of the CO(3$-$2) emission is located at RA (17:28:19.79 $\pm$ 0.01), Dec (-14:15:55.86 $\pm$ 0.01)" (Results)

## Data provenance

- ALMA projects: 2016.1.01156.S
- bands: Band 7  
  > "We used the ALMA band 7 receiver and the frequency division mode of the ALMA correlator" (ALMA observation and data reduction)
- frequencies and spectral setup: four 1.875 GHz spws, 31.25 MHz (~30 km/s) resolution; spw0 at 292 GHz for CO(3-2), spw1 adjacent with ~300 MHz overlap, other sideband ~280 GHz  
  > "providing us with four spectral windows of 1.875 GHz width and a spectral resolution of 31.25 MHz ($\sim30$ km s$^{-1}$)" (ALMA observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, max projected baseline ~1.1 km  
  > "The ALMA array was arranged in C40-5 configuration, with a maximum projected baseline of $\sim1.1$ km." (ALMA observation and data reduction)
- baselines: _not stated_
- angular resolution: 0.23x0.29 arcsec natural weighting; 0.16x0.19 arcsec with robust -0.5  
  > "The final beam size of the observation is ($0.23\times0.29$) arcsec$^2$ at position angle $\rm PA= -70$ deg." (ALMA observation and data reduction)
- max recoverable scale: 2.2 arcsec (~6.6 kpc)  
  > "the largest recoverable scale is $2.2$ arcsec ($\sim$6.6 kpc)" (Results)
- sensitivity: 0.083 mJy/beam per 30 km/s channel (natural); continuum rms 9.6 uJy/beam  
  > "The 1$\sigma$ rms in the final cube is $\sim 0.083$ mJy beam$^{-1}$ for a channel width of 30 km s$^{-1}$." (ALMA observation and data reduction)
- time on source: 4.1 hours  
  > "performed on 5 May 2017 for a 4.1 hours on-source integration time" (ALMA observation and data reduction)
- observing dates: 5 May 2017  
  > "performed on 5 May 2017 for a 4.1 hours on-source integration time" (ALMA observation and data reduction)
- pi or archival as stated: Cycle 4 PI observation (P.I. E. Piconcelli)  
  > "project 2016.1.01156.S, P.I. E. Piconcelli" (ALMA observation and data reduction)
- Line: CO 3-2 (345.796 GHz)
- Line: H13CN 4-3 (345.34 GHz)
- External data: CO(1-0) flux density (OVRO) used for line ratios and total gas mass  
  > "computed by using the $S_{\rm 1-0}$ flux density reported by Y04" (Results) [from Yun et al. 2004 (cite: Yun04)]
- External data: Compilation of molecular and ionised AGN outflows for scaling relations  
  > "a compilation of molecular and ionised AGN-driven outflows from (cite: Fiore17)" (Discussion) [from (cite: Fiore17)]
- External data: [FeII] redshift z=0.1837  
  > "$z_{\rm [FeII]} = 0.1837\pm0.0003$ derived from the \[FeII\] emission line in the near-IR spectrum (cite: Simpson99)" (Results) [from (cite: Simpson99)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline mode with default observatory calibrators  
  > "calibrated by using the CASA 4.7.2 software (cite: McMullin07) in the pipeline mode and the default calibrators provided by the Observatory" (ALMA observation and data reduction)
- casa version: CASA 4.7.2  
  > "calibrated by using the CASA 4.7.2 software" (ALMA observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J173302-130445 (band 7 flux 1.12±0.06 Jy), flux and phase calibrator  
  > "flux and phase calibrator J173302$-$130445 (band 7 flux 1.12$\pm$0.06 Jy)" (ALMA observation and data reduction)
- flux scale uncertainty: better than 10%  
  > "The absolute flux accuracy is better than 10%." (ALMA observation and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Hogbom with interactive per-channel masks  
  > "We preferred the Hogbom algorithm and the application of interactive cleaning masks for each channel and cleaning iteration." (ALMA observation and data reduction)
- weighting robust: natural weighting; briggs robust b=-0.5 for high-resolution cube  
  > "We chose a natural weighting, a cleaning threshold equal to the rms per channel" (ALMA observation and data reduction)
- uv taper: _not stated_
- cell size: 0.04 arcsec  
  > "a pixel size of 0.04 arcsec" (ALMA observation and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: zero-order model fit in the UV plane to spw0+spw1 continuum channels  
  > "we fitted a zero order model in the UV plane to the continuum channels ($|v|>1000$ km s$^{-1}$ from the peak of the CO(3$-$2) emission line)" (ALMA observation and data reduction)
- line free channels: |v|>1000 km/s from the CO(3-2) peak  
  > "continuum channels ($|v|>1000$ km s$^{-1}$ from the peak of the CO(3$-$2) emission line)" (ALMA observation and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.23x0.29 arcsec PA -70 deg (cube); 0.24x0.30 (continuum); 0.16x0.19 (robust -0.5)  
  > "we obtain a continuum map with synthetic beam of ($0.24\times0.30$) arcsec$^2$" (ALMA observation and data reduction)
- final rms: 0.083 mJy/beam (30 km/s); 0.16 mJy/beam for robust -0.5 cube  
  > "a rms sensitivity of $\sim 0.16$ mJy beam$^{-1}$ for a 30 km s$^{-1}$ channel width" (ALMA observation and data reduction)

### Inherited from earlier work

- alpha_CO=0.8 and adopting same factor for extended outflow  
  > "Similarly to (cite: HerreraCamus19), we adopt the same conversion factor also for the extended outflow." (Discussion) [from (cite: HerreraCamus19)]
- Outflow compilation values recomputed following Eq. B.2  
  > "all values have been recomputed from the tabulated data according to the same assumptions, following Eq. B.2 by (cite: Fiore17)" (Discussion) [from (cite: Fiore17)]
- v_rot and dynamical mass relations  
  > "$v_{\rm rot}=1.3\times\Delta v_{\rm blue-red}/(2$sin$i)\sim280$ km s$^{-1}$ (cite: Tacconi13)" (Results) [from (cite: Tacconi13); (cite: Wang13); (cite: Bischetti18)]

### Not stated but needed to reproduce (our reading)

- Clean mask definitions and iteration counts
- Pipeline version and exact flagging
- Priors, optimiser and initial guesses for the Gaussian pixel-by-pixel decomposition
- 3DBarolo parameter settings (ring widths, fit options)
- Method for deriving v98 and clump selection details
- Fitting method for the parabolic scaling relations
- SFR from SED fit (Vignali in prep.) is not reproducible
- Exact L'CO1-0 value and conversion assumptions

## Analysis recipe

1. **Continuum subtraction and imaging**: UV-plane zero-order continuum fit to spw0+spw1, subtraction, Hogbom cleaning with interactive masks  
  > "We subtracted this fit from the global visibilities and created continuum-subtracted CO(3$-$2) visibilities." (ALMA observation and data reduction)
   - software: CASA
   - parameter: natural weighting, 0.04 arcsec pixel, 30 km/s channels  
  > "a pixel size of 0.04 arcsec and a spectral resolution of $\sim30$ km s$^{-1}$" (ALMA observation and data reduction)
   - assumption: intrinsic QSO continuum variation across spw0/spw1 less than 1%  
  > "the intrinsic QSO continuum variation across spw0 and spw1 is expected to be less than 1%" (ALMA observation and data reduction)
   - fitting: _not stated_
   - validation: first-order polynomial did not significantly change results  
  > "A first order polynomial fit to the continuum emission did not significantly change our results." (ALMA observation and data reduction)
2. **Global CO(3-2) spectrum and sizes**: Single-Gaussian fit to spectrum from 1 arcsec radius; 2D Gaussian fits in image plane  
  > "By fitting the line with a single Gaussian component, we measure a peak flux density S$_{\rm 3-2} = 63.6 \pm 0.7$ mJy" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extended outflow clumps mass and outflow rate**: Integrate >3 sigma emission in 4 contiguous channels over -1000 to -250 km/s; Mdot=M v98/R  
  > "obtained by integrating the emission detected at $>3\sigma$ in each 30 km s$^{-1}$ spectral channel, for at least four contiguous channels" (Extended outflow)
   - assumption: alpha_CO = 0.8 Msun (K km/s pc^2)^-1; L'CO3-2/L'CO1-0 from systemic emission  
  > "a luminosity-to-gas-mass conversion factor $\alpha_{\rm CO} = 0.8$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (Extended outflow)
   - fitting: multiple Gaussian components per clump spectrum  
  > "We model the spectrum of each extended clump with multiple Gaussian components" (Extended outflow)
   - validation: _not stated_
4. **Disk kinematics and dynamical mass**: 3D tilted-ring fit excluding inner 0.15 arcsec; Mdyn from vrot and size  
  > "We fit a 3D tilted-ring model with $^{\rm 3D}$BAROLO (cite: DiTeodoro15) to the data to provide a zero order description of the kinematics." (Central outflow)
   - software: 3DBarolo
   - fitting: _not stated_
   - validation: inclination consistent with that from axis ratio; second Mdyn relation gives comparable value  
  > "A comparable value, i.e. $M_{\rm dyn}(i = 25\ \rm deg) \sim 1.2\times10^{10}$ $M_\odot$" (Central outflow)
5. **Central outflow spectral decomposition**: Pixel-by-pixel decomposition in -500 to +600 km/s with four Gaussians (two disk, one outflow sigma>90 km/s, H13CN at +390 km/s); plus Gaussian for high-velocity blue component; mass-conserving spherical/biconical geometry multiplies Mdot by 3  
  > "we use a pixel-by-pixel spectral decomposition in the range $v\in[-500,+600]$ km s$^{-1}$ with a combination of four Gaussian components" (Central outflow)
   - parameter: H13CN region v in [310,560] km/s excluded  
  > "we exclude the spectral region in the range $v\in[310,560]$ km s$^{-1}$" (Central outflow)
   - assumption: uniform density, constant velocity flow to R~1.2 kpc  
  > "spherically/biconically symmetric, mass-conserving flow with constant velocity and uniform density up to $R\sim1.2$ kpc" (Central outflow)
   - fitting: _not stated_
   - validation: decomposition without outflow component accounts for at most ~50% of residuals  
  > "is able to account for at most $\sim$50% of these residuals" (Central outflow)
6. **Scaling relations with L_Bol**: Fit parabolic function to molecular and ionised outflow rates of a literature compilation including PDS 456; derive momentum boost relation  
  > "we fit the molecular data with a parabolic function defined as:" (Discussion)
   - parameter: v_mol~1000 km/s, k~2  
  > "we assume $v_{\rm mol}\sim1000$ km s$^{-1}$ and $k\sim2$ (cite: Fiore17)" (Discussion)
   - fitting: _not stated_
   - validation: scatter as rms of data about relation (0.37 dex molecular, 0.91 dex ionised)  
  > "with an associated scatter of $\sim0.37$ dex, computed as the rms of the molecular data points with respect to the relation" (Discussion)

## Software

- **CASA** 4.7.2: pipeline calibration, UV continuum fit, imaging  
  > "calibrated by using the CASA 4.7.2 software (cite: McMullin07) in the pipeline mode" (ALMA observation and data reduction)
- **3DBarolo** : 3D tilted-ring kinematic model  
  > "We fit a 3D tilted-ring model with $^{\rm 3D}$BAROLO (cite: DiTeodoro15)" (Central outflow)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) peak flux density | 63.6 | 0.7 | mJy | 2 | S$_{\rm 3-2} = 63.6 \pm 0.7$ mJy and a FWHM $= 160\pm30$ km s$^{-1}$ |
| CO(3-2) integrated intensity | 10.6 | 0.2 | Jy km/s | 2 | S$\Delta$v$_{\rm 3-2} = 10.6 \pm 0.2$ Jy km s$^{-1}$ |
| CO redshift | 0.1850 | 0.0001 | dimensionless | 2 | $z_{\rm CO} = 0.1850\pm0.0001$ |
| 340 GHz continuum flux density | 0.69 | 0.02 | mJy | 1 | a flux density of $0.69\pm0.02$ mJy |
| Inclination | 25 | 10 | deg | 4 | This results into an inclination $i=25\pm10$ deg |
| Dynamical mass | ~1.0e10 | not stated | Msun | 4 | $M_{\rm dyn}={Dv_{\rm rot}^2/2G}\sim1.0\times10^{10}$ $M_\odot$ |
| Total outflow mass | 2.5e8 | [1.6-2.8]e8 | Msun | 5 | $2.5[1.6-2.8]$ |
| Total molecular mass outflow rate | 290 | [180-760] | Msun/yr | 5 | $290[180-760]$ |
| Extended outflow Mdot | 50 | [45-55] | Msun/yr | 3 | $50[45-55]$ |
| Momentum boost Pmol/Prad | 0.36 | not stated | dimensionless | 5 | The ratio $\dot{P}_{\rm mol}$/$\dot{P}_{\rm rad}$ $\sim0.36$ |
| Depletion timescale | ~8 | not stated | Myr | 5 | depletion timescale $\tau_{\rm dep} = M_{\rm mol}^{\rm out}/\dot{M}_{\rm mol}\sim8$ Myr |
| Molecular parabolic fit parameters | alpha=-0.11, beta=0.80, gamma=1.78, L0=10^44.03 erg/s | scatter 0.37 dex | dimensionless | 6 | $\alpha_{\rm mol} = -0.11$, $\beta_{\rm mol} = 0.80$, $\gamma_{\rm mol} = 1.78$ and $L_{\rm 0, mol}=10^{44.03}$ erg s$^{-1}$ |

## Qualitative findings

- First molecular outflow in a radio-quiet, non-lensed QSO at L_Bol ≳1e47 erg/s, clumpy and extending to ~5 kpc  
  > "The molecular outflow discovered in PDS 456 is the first reported for a radio quiet, non-lensed QSO" (Discussion)

## Claim tuples

- H: PDS 456 hosts a kpc-scale molecular outflow | E: Band 7 CO(3-2) cube analysis with spectral decomposition and clump identification | R: Blue wing to -1000 km/s, clumps to ~5 kpc, total M_out ~2.5e8 Msun, Mdot ~290 Msun/yr | F: A molecular outflow is detected, weak for such a luminous QSO | **supported**
- H: UFO-driven energy-conserving expansion explains the outflow | E: Compare Pmol/Prad with energy-conserving expectations, including empirical ionised correction | R: Pmol/Prad ~0.36, far below expected | F: Energy-conserving model fails unless ionised outflow is huge or gas leaks; radiation pressure on dust may contribute | **partially**
- H: The outflow can quench star formation | E: Compare tau_dep to gas depletion time from SFR | R: tau_dep ~8 Myr, 4-10 times shorter than tau_SF | F: Potential quenching in short time | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Hogbom with interactive masks chosen after comparing cleaning procedures  
  > "We investigated different cleaning procedures to produce the continuum-subtracted cube of CO(3$-$2)." (ALMA observation and data reduction)
- Alternative: Clark clean increases negative artefacts; non-interactive cleaning leaves positive residuals  
  > "non-interactive cleaning (without masks) results in positive residuals at the location of the QSO" (ALMA observation and data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses depend strongly on alpha_CO; large uncertainties on tau_dep and tau_SF  
  > "We note that the estimate of the molecular gas masses strongly depends on the assumption on $\alpha_{\rm CO}$." (Discussion)
- Caveat (inferred, ours): Central outflow relies on a Gaussian decomposition that may be degenerate with disk and H13CN
- Caveat (inferred, ours): Mdot geometry assumption changes central rate by a factor of 3
- Caveat (inferred, ours): alpha_CO uncertain by factor ~2.5
- Caveat (inferred, ours): Scaling fits from heterogeneous literature sample, fit method unspecified

## Reproducibility

- Data public (paper): Archive project cited; public status not explicitly stated  
  > "This paper makes use of the ALMA data from project ADS/JAO.ALMA#2016.1.01156.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Decomposition priors and fitting code
- Missing: Literature compilation values for scaling fits
- Missing: SFR from unpublished SED fit
- Data volume (inferred): ~20-50 GB raw single-EB Band 7 dataset
- Score (inferred): 3/5, Imaging recipe is mostly stated, but spectral decomposition, clump selection and scaling fit details are incomplete.
- Rediscovery candidate: no, Key outflow results rely on unspecified fitting and non-reproducible literature compilations.

## Links

- Method: Di Teodoro & Fraternali 2015 (cite: DiTeodoro15) (3DBarolo)
- Method: Fiore et al. 2017 (cite: Fiore17) (outflow energetics recipe)
- Companion: Piconcelli et al. 2019 in prep. (galaxy overdensity around PDS 456)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 54,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
