# Pōniuā'ena: A Luminous z = 7.5 Quasar Hosting a 1.5 Billion Solar Mass Black Hole

`2020ApJ...897L..14Y` | The Astrophysical Journal Letters 2020 | first author: Yang, Jinyi | arXiv: 2006.13452 | DOI: 10.3847/2041-8213/ab9c26

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies, cosmology
- Question: Discover a z~7.5 quasar, measure its black hole mass, constrain early SMBH growth and the IGM neutral fraction, and get a [CII] systemic redshift and host properties with ALMA  
  > "Its discovery enables new measurements of a quasar Ly$\alpha$ damping wing and provides new constraints on the earliest SMBH growth." (Introduction)
- Target **J1007+2115 (Pōniuā‘ena)**: coordinates 10:07:58.26 +21:15:29.20 (J2000)  
  > "| R.A. (J2000) | 10:07:58.26 |" (Table 1); "| Decl. (J2000) | +21:15:29.20 |" (Table 1); "A Gaussian fit to the \[C II\] line yields a redshift of 7.5149$\pm$0.0004." (A 1.5 Billion Solar Mass Black Hole); z/distance z = 7.5149 ± 0.0004 ([CII])  
  > "| R.A. (J2000) | 10:07:58.26 |" (Table 1); "| Decl. (J2000) | +21:15:29.20 |" (Table 1); "A Gaussian fit to the \[C II\] line yields a redshift of 7.5149$\pm$0.0004." (A 1.5 Billion Solar Mass Black Hole); distance from [CII] Gaussian line fit from ALMA  
  > "| R.A. (J2000) | 10:07:58.26 |" (Table 1); "| Decl. (J2000) | +21:15:29.20 |" (Table 1); "A Gaussian fit to the \[C II\] line yields a redshift of 7.5149$\pm$0.0004." (A 1.5 Billion Solar Mass Black Hole)

## Data provenance

- ALMA projects: 2019.1.01025.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA configuration C43-4, Cycle 7  
  > "We observed J1007+2115 with ALMA (configuration C43-4, Cycle 7)" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.46" x 0.34" synthesized beam  
  > "The synthesized beam size is $0.46\ensuremath{''} \times 0.34\ensuremath{''}$" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.4 mJy/beam per 10 km/s channel  
  > "the final data cube reaches an rms noise level of 0.4 mJy beam$^{-1}$ per 10 km s$^{-1}$ channel" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- time on source: 15 min  
  > "The observations were taken in 2019 October with 15 min on-source integration time." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- observing dates: 2019 October  
  > "The observations were taken in 2019 October with 15 min on-source integration time." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine-structure line (not stated)
- Other facility **Gemini/GNIRS**: Discovery and high-quality NIR spectra (5.5 h on source)  
  > "we observed the quasar for 5.5 hours (on-source) with GNIRS and for 2.2 hours (on-source) with Keck/NIRES" (2.2 Near-infrared Spectroscopy)
- Other facility **Keck/NIRES**: NIR spectrum (2.2 h on source) used for the Mg II fit  
  > "we observed the quasar for 5.5 hours (on-source) with GNIRS and for 2.2 hours (on-source) with Keck/NIRES" (2.2 Near-infrared Spectroscopy)
- Other facility **Magellan/FIRE**: One-hour confirmation spectrum  
  > "A one-hour (on-source) observation with Magellan/FIRE was used further to confirm this new quasar" (2.2 Near-infrared Spectroscopy)
- Other facility **DECaLS, PS1, UHS, WISE**: Photometry used for quasar selection  
  > "J1007+2115 was selected in the area covered by the DESI Legacy Imaging Surveys (cite: dey19)" (2.1 Selection Method)
- External data: [CII]-SFR relation for high-z galaxies  
  > "Applying the relation between star formation rate (SFR) and $L_\mathrm{[CII]}$ for high-redshift ($z>0.5$) galaxies from (cite: delooze14)" (2.3 [C II]-based Redshift and Dust Continuum from ALMA) [from (cite: delooze14)]
- External data: Dust temperature 47 K and beta = 1.6 for the grey body  
  > "assuming an optically thin grey body with dust temperature $T_{d}$ = 47 K and emissivity index $\beta$ = 1.6 (cite: beelen06)" (2.3 [C II]-based Redshift and Dust Continuum from ALMA) [from (cite: beelen06)]
- External data: Local TIR-SFR scaling relation  
  > "The SFR$_{\rm TIR}$ is estimated as $\sim$ 700 $M_{\odot}$/yr by applying the local scaling relation from (cite: murphy11)." (2.3 [C II]-based Redshift and Dust Continuum from ALMA) [from (cite: murphy11)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The ALMA data were reduced with the CASA 5.4 pipeline (cite: mcmullin07)." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- casa version: CASA 5.4  
  > "The ALMA data were reduced with the CASA 5.4 pipeline (cite: mcmullin07)." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.46" x 0.34"  
  > "The synthesized beam size is $0.46\ensuremath{''} \times 0.34\ensuremath{''}$" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- final rms: 0.4 mJy/beam per 10 km/s channel  
  > "the final data cube reaches an rms noise level of 0.4 mJy beam$^{-1}$ per 10 km s$^{-1}$ channel" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)

### Inherited from earlier work

- Damping wing analysis procedure and PCA continuum model  
  > "we follow the procedures described in (cite: davies18a; davies18b)" (5 Constraint on the IGM Neutral Fraction) [from (cite: davies18a; davies18b)]
- Mock-spectra error estimation for line fits  
  > "created by randomly adding Gaussian noise at each pixel with its scale equal to the spectral error at that pixel (cite: shen19; wang20)" (4 A 1.5 Billion Solar Mass Black Hole) [from (cite: shen19; wang20)]

### Not stated but needed to reproduce (our reading)

- ALMA spectral windows, frequencies and channelization
- Flux, bandpass and phase calibrators and flux-scale uncertainty
- Imaging task, weighting/robust, cell and image size
- Continuum-subtraction and line-free channels
- Aperture or fitting method for the continuum flux and the [CII] line flux
- Conversion from line flux to L_[CII]
- Continuum-fit region and details of the Mg II/Fe II fit windows
- Exact 1/sqrt(2)-style CMB correction details for the grey body

## Analysis recipe

1. **Reduce ALMA data and image**: CASA 5.4 pipeline reduction; cube at 10 km/s channels  
  > "The ALMA data were reduced with the CASA 5.4 pipeline (cite: mcmullin07)." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [CII] redshift and line properties**: Gaussian fit to the [CII] line  
  > "A Gaussian fit to the \[C II\] line yields a redshift of 7.5149$\pm$0.0004." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
   - fitting: Gaussian profile  
  > "Gaussian fits of the C IV and Mg II emission lines are performed on the continuum-subtracted spectrum. A two-component Gaussian profile is used." (A 1.5 Billion Solar Mass Black Hole)
   - validation: _not stated_
3. **Derive SFR and IR luminosities**: [CII]-SFR relation; grey body FIR/TIR and TIR-SFR scaling  
  > "assuming an optically thin grey body with dust temperature $T_{d}$ = 47 K and emissivity index $\beta$ = 1.6 (cite: beelen06)" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
   - assumption: T_d = 47 K, beta = 1.6, CMB effect included  
  > "taking the effect of the cosmic microwave background (CMB) on the dust emission into account (cite: dacunha13)" (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
   - fitting: _not stated_
   - validation: _not stated_
4. **Black hole mass from the NIR spectrum**: Pseudo-continuum plus two-component Gaussian Mg II and C IV fits; M_BH from the Vestergaard & Osmer relation  
  > "We estimate the black mass based on the bolometric luminosity and the FWHM of the Mg II line by adopting the local empirical relation from (cite: vestergaard09)." (4 A 1.5 Billion Solar Mass Black Hole)
   - software: PypeIt
   - assumption: Bolometric correction 5.15  
  > "assuming a bolometric correction factor of 5.15 (cite: richards06)" (4 A 1.5 Billion Solar Mass Black Hole)
   - fitting: 100 mock spectra; 16th/84th percentiles  
  > "All uncertainties are then estimated based on the 16th and 84th percentile of the distribution." (4 A 1.5 Billion Solar Mass Black Hole)
   - validation: _not stated_
5. **IGM neutral fraction from damping wing**: PCA continuum prediction, hybrid reionization model, Bayesian inference marginalized over quasar lifetime  
  > "we set a broad $t_{\rm Q}$ range of $10^3\,{\rm yr}<t_{\rm Q}<10^8\,{\rm yr}$ with a flat log-uniform prior" (5 Constraint on the IGM Neutral Fraction)
   - fitting: Pseudo-likelihood on 500 km/s binned pixels; log-uniform t_Q prior  
  > "the pseudo-likelihood is defined as the product of individual flux PDFs of 500 km/s binned pixels" (5 Constraint on the IGM Neutral Fraction)
   - validation: Consistent with maximum pseudo-likelihood parameters; no intervening metal absorption found  
  > "No such absorption has been found in our current spectrum." (5 Constraint on the IGM Neutral Fraction)

## Software

- **CASA** 5.4: ALMA data reduction pipeline  
  > "The ALMA data were reduced with the CASA 5.4 pipeline (cite: mcmullin07)." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- **PypeIt** : Reduction of NIR spectra  
  > "All NIR spectra were reduced with the open-source Python-based spectroscopic data reduction pipeline `PypeIt`" (2.2 Near-infrared Spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] redshift | 7.5149 | 0.0004 | dimensionless | 2 | A Gaussian fit to the \[C II\] line yields a redshift of 7.5149$\pm$0.0004. |
| [CII] line flux | 1.2 | 0.1 | Jy km/s | 2 | We obtain a line flux of $F_\mathrm{[CII]}=1.2\pm0.1$ Jy km s$^{-1}$ |
| [CII] FWHM | 331.3 | 31.6 | km/s | 2 | an FWHM$_\mathrm{[CII]}=331.3\pm31.6$ km s$^{-1}$ |
| L_[CII] | 1.5e9 | 0.2e9 | L_sun | 2 | $L_\mathrm{[CII]}=(1.5\pm0.2)\times10^{9}$ $L_{\odot}$ |
| Continuum flux at 231.2 GHz | 1.2 | 0.03 | mJy | 2 | we measure 1.2$\pm$0.03 mJy at 231.2 GHz |
| L_FIR | 3.3e12 | 0.1e12 | L_sun | 3 | $L_{\rm FIR}$ = (3.3$\pm$0.1)$\times10^{12}$ $L_{\odot}$ |
| L_TIR | 4.7e12 | 0.1e12 | L_sun | 3 | $L_{\rm TIR}$ = (4.7$\pm$0.1)$\times10^{12}$ $L_{\odot}$ |
| SFR_[CII] | 80-520 | factor of ~2.5 systematic | Msun/yr | 3 | we obtain SFR$_\mathrm{[CII]}\sim80-520$ $M_\ensuremath{\odot}$ yr$^{-1}$ |
| SFR_TIR | ~700 | not stated | Msun/yr | 3 | The SFR$_{\rm TIR}$ is estimated as $\sim$ 700 $M_{\odot}$/yr |
| Black hole mass | 1.5e9 | 0.2e9 (excl. up to ~0.5 dex systematic) | Msun | 4 | The black hole mass is derived to be $M_{\rm BH}=(1.5\pm0.2)\times10^{9}$ $M_{\odot}$ |
| Mg II FWHM | 3247 | 188 | km/s | 4 | FWHM = $3247\pm188$ km s$^{-1}$ |
| Mean neutral fraction | 0.39 | +0.22/-0.13 | dimensionless | 5 | $\langle x\rm_{HI}\rangle=0.39^{+0.22}_{-0.13}$ |

## Qualitative findings

- Damping wing in J1007+2115 is much weaker than in the other three z>7 quasars, suggesting patchy reionization  
  > "It is evident that the damping wing absorption is much weaker in J1007+2115 compared to that in the other three $z>7$ quasars." (5 Constraint on the IGM Neutral Fraction)

## Claim tuples

- H: Does J1007+2115 host a more massive SMBH than J1342+0928, challenging growth models? | E: Mg II line and continuum fit of Gemini/Keck NIR spectra | R: M_BH=(1.5±0.2)e9 Msun, Eddington ratio ~1.1 | F: Requires a massive seed or super-Eddington/low-efficiency growth | **supported**
- H: Is the IGM at z=7.5 uniformly neutral? | E: Damping wing modelling of the Lyα profile | R: <x_HI>=0.39 (+0.22/-0.13), lower than the other sightlines | F: Suggests patchy reionization | **partially**
- H: Can ALMA give the systemic redshift and host SFR? | E: [CII] and continuum observation with ALMA | R: z=7.5149±0.0004, SFR_[CII] ~80-520 Msun/yr | F: Host is star-forming, similar to J1342+0928 | **supported**

## Reasoning

- Why this data: [CII] gives the most accurate systemic redshift of the quasar  
  > "The \[C II\] emission line provides the most accurate measurement of the quasar systemic redshift." (2.3 [C II]-based Redshift and Dust Continuum from ALMA)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Black hole mass uncertainty excludes scaling-relation systematics of up to ~0.5 dex  
  > "could be up to $\sim0.5$ dex" (4 A 1.5 Billion Solar Mass Black Hole)
- Limitation (authors): Large uncertainties and a broad PDF for x_HI prevent solid conclusions  
  > "it is difficult to draw solid conclusions because of the large uncertainties (and the broad PDF) on the value of $\langle x\rm_{HI}\rangle$" (5 Constraint on the IGM Neutral Fraction)
- Caveat (inferred, ours): Single sightline and a 2σ outlier cannot establish patchy reionization
- Caveat (inferred, ours): ALMA processing is only sketched; the unresolved source and 15 min depth limit host constraints
- Caveat (inferred, ours): Fixed T_d=47 K and beta=1.6 drive IR luminosities and SFR_TIR

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full ALMA imaging and line-fit details
- Missing: Unpublished Davies & Furlanetto simulations used in the IGM model
- Missing: Fe II/continuum fit windows
- Data volume (inferred): ~5-20 GB raw ALMA for one short Band 6 execution; NIR spectra are small
- Score (inferred): 3/5, The ALMA part is minimal in detail; the main results (M_BH, x_HI) rely on NIR spectra and an in-prep simulation model.
- Rediscovery candidate: no, ALMA recipe is sparse and the central results depend on non-ALMA data and unpublished models.

## Links

- Method: (cite: davies18a) (Damping wing / neutral fraction method)
- Method: (cite: davies18b) (PCA continuum model)
- Method: (cite: prochaska20) (PypeIt reduction)
- Companion: (cite: wang20) (Analogous z=7.0 quasar damping wing analysis)
- Companion: (cite: banados18) (J1342+0928 at z=7.54)
- Related: DESI Legacy Imaging Surveys
- Related: Pan-STARRS1
- Related: UKIRT Hemisphere Survey
- Related: WISE

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
