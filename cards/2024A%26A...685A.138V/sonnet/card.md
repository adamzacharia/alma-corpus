# The cold interstellar medium of a normal sub-L<SUP>⋆</SUP> galaxy at the end of reionization

`2024A&A...685A.138V` | Astronomy and Astrophysics 2024 | first author: Valentino, F. | arXiv: 2402.17845 | DOI: 10.1051/0004-6361/202348128

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the dust and cold gas properties (dust mass, temperature, obscured SFR, gas mass, dust-to-gas ratio) of a lensed sub-L* galaxy at z=6.07, and how do they compare with literature and models?  
  > "Our primary objective is to start exploring a new portion of the cold gas and dust parameter space at intrinsic low stellar masses, star formation rates (SFRs), and metallicities." (1 Introduction)
- Target **z6.3 and arc lensed images of a z=6.07 galaxy behind RXJ0600-2007**: coordinates z6.3: 06:00:09.55, -20:08:11.26; arc: 06:00:09.13, -20:08:26.49  
  > "| R.A. \[h:m:s\] | 06:00:09.55 | 06:00:09.13 |" (Table 1); "| $z_{\rm spec}$ | $6.0719$ | $6.0736$ |" (Table 1); z/distance z=6.0719 (z6.3), 6.0736 (arc)  
  > "| R.A. \[h:m:s\] | 06:00:09.55 | 06:00:09.13 |" (Table 1); "| $z_{\rm spec}$ | $6.0719$ | $6.0736$ |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00247.S, 2021.1.00055.S, 2022.1.00195.S, 2021.1.00181.S
- bands: Bands 3, 5, 6, 7, 8  
  > "We thus followed up its lensed images in Bands 3, 5, 6, 7, and 8" (2.2 ALMA multiwavelength observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6 in C5 and C2, combined  
  > "Band 6 were obtained in C5 ($t_{\rm int} = 1.8$ hr on target per source, $0.35\ensuremath{''} \times 0.29\ensuremath{''}$ beam) and C2" (Table 2 notes)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~3" for Band 6 in C5  
  > "the maximum recoverable scale for Band 6 in C5 is of $\sim3$"" (3.1)
- sensitivity: Continuum rms 41 uJy/beam (Band 3) to 2458 uJy/beam (Band 8)  
  > "| Band 8 | 0.6 | 478.8 | 88 | 2458 | $0.65 \times 0.57$ | 1, 2 |" (Table 2)
- time on source: ~60 hours total; Band 3 13.3 hr  
  > "With the latter we accumulated approximately $\sim$60 hours of observations" (1 Introduction); "| Band 3 | 13.3 | 100.5 | 370 | 41 | $1.55 \times 1.27$ | 4 |" (Table 2)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C I] 3P2-3P1 (809.34 GHz)
- Line: CO 7-6 (806.65 GHz)
- Other facility **JWST NIRCam/NIRSpec IFU**: Imaging (F115W-F444W) and G395H IFU spectroscopy for stellar mass, metallicity, Halpha  
  > "The imaging was taken with the F115W, F150W, F277W, F356W, and F444W filters." (2.3 Ancillary datasets)
- Other facility **HST and Spitzer**: UV to near-IR photometry  
  > "It thus benefits from ample UV to near-IR photometric coverage with the HST and *Spitzer*." (2.3 Ancillary datasets)
- Other facility **Herschel/SPIRE**: Upper limits on FIR photometry  
  > "together with available upper limits on *Herschel* photometry (de-blended and extracted as described in (cite: sun_2022))" (3.1)
- External data: Lensing magnifications, [CII] luminosity, dynamical mass, effective radius  
  > "$\ddag$ From \[C II\] observations in F21." (Table 1 notes) [from Fujimoto et al. 2021 (cite: fujimoto_2021)]
- External data: Herschel/SPIRE upper limits  
  > "*Herschel*/SPIRE from (cite: sun_2022)." (Table 2 notes) [from (cite: sun_2022)]
- External data: Metallicity 12+log(O/H)=8.11 from NIRSpec, and spectra  
  > "integrating the measurements of the ionized line emissions in the NIRSpec spectrum (cite: fujimoto_2024)" (3.4) [from (cite: fujimoto_2024)]
- External data: Literature compilation of CO(7-6), [CI], L_IR, M_dust for comparison  
  > "The samples include those already described in (cite: valentino_2020c), expanded to more recent results" (Appendix 7) [from (cite: valentino_2020c) and others]

## Processing

### Calibration

- pipeline or manual: Standard pipeline script  
  > "using the Common Astronomy Software Applications (CASA) package version 6.2.1.7 ((cite: mcmullin_2007)) with the standard pipeline script." (2.2)
- casa version: CASA 6.2.1.7  
  > "using the Common Astronomy Software Applications (CASA) package version 6.2.1.7" (2.2)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN, continuum from line-free spectral windows, cleaned to 2 sigma  
  > "TCLEAN was used to produce the continuum maps averaging all channels in the spectral windows not dominated by bright lines" (2.2); "The TCLEAN routines were executed down to the $2\sigma$ level." (2.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final natural-weighted map has synthesized beams and continuum sensitivities listed in Table" (2.2)
- uv taper: _not stated_
- cell size: approximately ten times smaller than the beam size  
  > "We chose a pixel scale approximately ten times smaller than the beam size" (2.2)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not needed; images within inner primary beam  
  > "Therefore, a correction for the primary beam was not needed." (3.1)
- array combination: Band 6 C2 and C5 combined with CASA  
  > "We thus combined these datasets with CASA for our final measurements" (3.1)
- smoothing: common channel bin of 40 km/s  
  > "adopted a common spectral channel bin of $40$ km s$^{-1}$" (2.2)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of individual ALMA programs and data reduction  
  > "More details about the individual ALMA programs and the data reduction can be found in (cite: fujimoto_2024)." (2.2) [from (cite: fujimoto_2024)]
- JWST data reduction steps  
  > "The data reduction is performed following the same steps described in (cite: valentino_2023)." (2.3) [from (cite: valentino_2023)]
- JWST photometry SED modeling with BAGPIPES  
  > "We modeled the JWST photometry as described in detail in the companion paper by (cite: gimenez-arteaga_2024)" (3.4) [from (cite: gimenez-arteaga_2024)]
- MERCURIUS priors adopted from Witstok et al.  
  > "we adopted their same priors." (3.3) [from (cite: witstok_2023)]

### Not stated but needed to reproduce (our reading)

- Line-free channels/spectral windows used for continuum
- Primary beam / uv range details and robust-weighting of final maps (beam in Table only; appendix mentions briggs 2.0 in figure files)
- Exact SEP detection parameters
- MERCURIUS sampler settings
- Lensing models/magnifications are taken from F21 but not reproduced
- Exact aperture geometry

## Analysis recipe

1. **Image continuum and measure aperture photometry**: TCLEAN continuum maps; SEP elliptical Kron apertures fixed to Band 7 122 um; uncertainties from rms scaled by independent beams  
  > "in every band we fixed our fiducial aperture to that retrieved for Band 7 in the $122$ $\mu$m rest frame" (3.1)
   - software: CASA, SEP
   - fitting: _not stated_
   - validation: Compared with CASA IMFIT single Gaussian fits and C2 vs C5 Band 6  
  > "we counterchecked our aperture photometry against modeling of the emission with the task IMFIT in CASA and single Gaussians profiles." (3.1)
2. **Extract Band 3 spectra and set line upper limits**: Spectra in same apertures, 3-sigma limit I=3 rms sqrt(dv Delta v) with Delta v=180 km/s, dv=40 km/s, 3-sigma clipping  
  > "we obtain $3\sigma$ upper limits on the line fluxes as $I_{\rm line}=3\times \mathrm{rms} \sqrt{\Delta v\,dv}$" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model FIR SED for Mdust, Tdust, LIR**: Bayesian MERCURIUS optically thin modified blackbody with CMB effect; gamma prior on Tdust (a=1.5), Gaussian prior beta 1.8+-0.25  
  > "for $\beta$, we imposed a Gaussian prior centered at $1.8$ and with a standard deviation of $0.25$." (3.3)
   - software: MERCURIUS
   - assumption: kappa0 = 8.94 cm2/g at 1900 GHz  
  > "$\kappa_0 = 8.94\,\mathrm{cm^{2}\,g^{-1}}$ at $\nu_0=1900\,\mathrm{GHz}$" (3.3)
   - fitting: Bayesian posterior, median and 16-84%  
  > "expressed as the median value and the 16-84% of their posterior distributions" (Table 1 notes)
   - validation: Alternative fixed beta=1.5, 2, flat beta prior, self-consistent optical depth  
  > "We also attempted alternative models at fixed $\beta=1.5, 2$" (3.3)
4. **Stellar mass and metallicity from JWST**: BAGPIPES with BC03, CLOUDY, Calzetti, double power-law SFH; direct-method metallicity from NIRSpec  
  > "We adopted (cite: bruzual_2003) single stellar population models" (3.4)
   - software: BAGPIPES, CLOUDY
   - fitting: Uniform priors A_V=0-3, Z=0-Zsun, M=1e5-1e11 Msun  
  > "We imposed uniform priors on the attenuation ($A_{V}=0-3$), metallicity ($Z=0-Z_\odot$), formed stellar mass ($M=10^5-10^{11}\,M_\odot$)." (3.4)
   - validation: _not stated_
5. **Derive gas masses and dust-to-gas ratio**: [CI] upper limit via Papadopoulos & Greve; [CII] calibrations; dynamical mass  
  > "We converted the \[C I\]$(^3P_2\,-\, ^{3}P_1)$ upper limit to $M_{\rm gas}$ as (cite: papadopoulos-greve_2004)" (4.2)
   - parameter: Q21=0.05-0.4  
  > "we considered $Q_{21}=[0.05-0.4]$, the range expected for $T_{\rm dust}\sim50$ K" (4.2)
   - assumption: X_[CI] ~1.5e-5 scaled linearly to ~25% Zsun  
  > "assumed that it scales linearly with metallicity to our $\sim25$% $Z_{\odot}$ estimate from NIRSpec" (4.2)
   - fitting: _not stated_
   - validation: Compared with dynamical mass limit  
  > "The upper limits from \[C I\]$(^3P_2\,-\, ^{3}P_1)$ are consistent with the dynamical estimate" (4.2)
6. **Derive SFRs, obscured fraction and dust yield**: SFR(IR), SFR(FUV), SFR(Halpha) from Murphy+11 calibrations; CO(7-6)-LIR relation; f_IR; SNe yield from Michalowski  
  > "$\mathrm{log(SFR(IR)} / M_\odot\, \mathrm{yr}^{-1}) = \mathrm{log}(L_{\rm IR} / \mathrm{erg\, s^{-1}}) - 43.41$" (4.3)
   - assumption: Chabrier IMF  
  > "we adopt a (cite: chabrier_2003) initial mass function (IMF)" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1.7: Reduction, TCLEAN imaging, IMFIT  
  > "package version 6.2.1.7" (2.2)
- **SEP** : Source detection and apertures  
  > "SEP (cite: barbary_2016), to detect the centroid, orientation, and ellipticity of the apertures" (3.1)
- **MERCURIUS** : FIR SED modeling  
  > "We modeled the ALMA and *Herschel* photometry using the Bayesian code MERCURIUS" (3.3)
- **BAGPIPES** : JWST SED modeling  
  > "then we modeled the emission with BAGPIPES" (3.4)
- **CLOUDY** : Emission line grids  
  > "a grid of CLOUDY (cite: ferland_2017) emission line grids" (3.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass z6.3 (magnified) | 0.4e8 | +0.4/-0.2 e8 | Msun | 3 | / $\mu M_{\rm dust}$ \[$M_\odot$\] / $0.4^{+0.4}_{-0.2} \times 10^{8}$ |
| Tdust z6.3 | 50 | +20/-13 | K | 3 | / $T_{\rm dust}$ \[K\] / $50^{+20}_{-13}$ / $37^{+11}_{-7}$ / |
| Tdust arc | 37 | +11/-7 | K | 3 | / $T_{\rm dust}$ \[K\] / $50^{+20}_{-13}$ / $37^{+11}_{-7}$ / |
| muSFR(IR) z6.3 | 164 | +334/-95 | Msun/yr | 6 | / $\mu$SFR(IR) \[$M_{\odot}$ yr$^{-1}$\] / $164^{+334}_{-95}$ / $111^{+96}_{-37}$ / |
| f_IR z6.3 | 0.76 | +0.14/-0.18 | dimensionless | 6 | $f_{\rm IR} = \mathrm{SFR(IR) / (SFR(IR)+SFR(FUV))} = 0.76^{+0.14}_{-0.18}$ |
| f_dust | 0.002 | +0.003/-0.001 | dimensionless | 6 | $f_{\rm dust}=0.002^{+0.003}_{-0.001}$ |
| SNe dust yield | 0.19 | +0.24/-0.10 | Msun | 6 | $y_{\rm SNe}=f_{\rm dust}\times 84 = 0.19^{+0.24}_{-0.10}$ |
| muMgas([CI]) upper limit | <(0.1-1.0)e10 | not stated | Msun | 5 | $\mu M_{\rm gas} < (0.1 - 1.0)\times10^{10}$ $M_{\odot}$ |
| muSFR(IR) from CO(7-6) limit z6.3 | <53 | not stated | Msun/yr | 6 | $3\sigma$ upper limit on $\mu$SFR(IR, CO(7-6))$<53$ $M_{\odot}$ yr$^{-1}$ |

## Qualitative findings

- No CO(7-6) or [CI] detection; galaxy consistent with LIR-L' trends of IR galaxies  
  > "We do not detect any line emissions." (3.2)

## Claim tuples

- H: Does the sub-L* galaxy host detectable dust and obscured star formation? | E: Multi-band ALMA continuum photometry and FIR SED fit | R: Detected at six wavelengths; Mdust and Tdust constrained | F: Dust and obscured SF present at low mass and metallicity | **supported**
- H: Can SNe explain the dust mass? | E: Compute f_dust and yield | R: y_SNe=0.19 Msun | F: SNe production sufficient without AGB | **supported**
- H: Is the dust-to-gas ratio consistent with models? | E: Gas masses from [CI], [CII], dynamics | R: delta_DGR ~1e-3 | F: Consistent with literature relations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fixed beta=1.5, 2, flat beta prior and self-consistent optical depth gave consistent results  
  > "The results are overall consistent with the free parameter fit." (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Tdust poorly constrained; systematics dominate Mdust and Mstar  
  > "we are at a stage where systematic errors totally dominate the uncertainties on $M_{\rm dust}$ and $M_{\star}$ from observations" (4.5)
- Caveat (inferred, ours): Single object; no Tdust constraint near SED peak
- Caveat (inferred, ours): Gas mass relies on unknown excitation and C abundance
- Caveat (inferred, ours): Dependence on lensing model from F21

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fujimoto et al. 2024 reduction details
- Missing: Lensing models
- Missing: Line-free channel selection
- Missing: MERCURIUS configuration
- Data volume (inferred): ~100s GB raw for 4 programs
- Score (inferred): 3/5, ALMA data and most steps described, but key details deferred to companion papers
- Rediscovery candidate: no, Recipe depends on companion-paper details and unpublished lensing/JWST inputs.

## Links

- Method: (cite: witstok_2023) (MERCURIUS SED fitting and priors)
- Method: (cite: fujimoto_2024) (ALMA data reduction details)
- Companion: (cite: gimenez-arteaga_2024) (JWST photometry analysis)
- Companion: (cite: fujimoto_2021) (Discovery, lensing and [CII] analysis)
- Related: ALMA Lensing Cluster Survey (ALCS)
- Related: REBELS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2021.0.00055.S",
  "2021.0.00181.S",
  "2021.0.00247.S",
  "2022.0.00195.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
