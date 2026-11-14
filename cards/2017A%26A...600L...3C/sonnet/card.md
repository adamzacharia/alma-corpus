# Planck's dusty GEMS. III. A massive lensing galaxy with a bottom-heavy stellar initial mass function at z = 1.5

`2017A&A...600L...3C` | Astronomy and Astrophysics 2017 | first author: Cañameras, R. | arXiv: 1703.02984 | DOI: 10.1051/0004-6361/201630359

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, other
- Question: What are the mass and stellar IMF of a lensing galaxy at z=1.525 that magnifies the Planck-selected submillimeter galaxy 'the Ruby'?  
  > "We focus on the optical and near-infrared properties, including the spectroscopic redshift of the foreground source and the lensing model, and discuss the stellar mass and mass-to-light ratio" (1 Introduction)
- Target **G244.8+54.9 (the Ruby), lens at z=1.525, source at z=3.0**: coordinates alpha=163.47138 deg, delta=5.938551 deg (lens model reference position)  
  > "from the reference position at $\alpha=163.47138^\circ$ and $\delta=5.938551^\circ$, respectively." (4 Lens modeling and source reconstruction); "at a common redshift $z=1.525\,{\pm}\,0.001$" (3 Spectroscopic redshift with VLT/X-Shooter); z/distance lens z=1.525; source z=3.0 (D_L=11.3 Gpc for lens)  
  > "from the reference position at $\alpha=163.47138^\circ$ and $\delta=5.938551^\circ$, respectively." (4 Lens modeling and source reconstruction); "at a common redshift $z=1.525\,{\pm}\,0.001$" (3 Spectroscopic redshift with VLT/X-Shooter); distance from X-Shooter spectroscopy (Halpha, [NII]) for lens  
  > "from the reference position at $\alpha=163.47138^\circ$ and $\delta=5.938551^\circ$, respectively." (4 Lens modeling and source reconstruction); "at a common redshift $z=1.525\,{\pm}\,0.001$" (3 Spectroscopic redshift with VLT/X-Shooter)

## Data provenance

- ALMA projects: 2015.1.01518.S
- bands: Band 3, CO(4-3) and dust continuum  
  > "high-resolution observations of CO $J\,{=}\,4\,{\rightarrow}\,3$ and dust continuum obtained with ALMA in band 3 (program 2015.1.01518S, PI Nesvadba)" (2 Morphology in the near-infrared and millimeter)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.14" x 0.06" beam  
  > "ALMA CO($4{\rightarrow}3$) flux map at $0.14\ensuremath{''}\times0.06\ensuremath{''}$ beam size" (4 Lens modeling and source reconstruction)
- max recoverable scale: _not stated_
- sensitivity: 0.14 mJy rms at 3 mm continuum  
  > "upper limit on the dust continuum at 3 mm from our ALMA data (C17) of 0.14 mJy rms" (5 A massive lensing galaxy at z=1.5)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=4-3 (not stated)
- Other facility **VLT/FORS2**: V, R, I optical imaging  
  > "using FORS2 through the $V$-, $R$-, and $I$-band filters at 1$''$ seeing" (2 Morphology in the near-infrared and millimeter)
- Other facility **VLT/HAWK-I**: J and K imaging  
  > "With HAWK-I we observed the Ruby on 12 May 2013 with 0.4$''$ seeing" (2 Morphology in the near-infrared and millimeter)
- Other facility **HST/WFC3**: F110W and F160W imaging  
  > "Wide-Field Camera 3 on the *Hubble* Space Telescope in the F110W and F160W bands (program 14223, PI Frye)" (2 Morphology in the near-infrared and millimeter)
- Other facility **VLT/X-Shooter**: spectroscopic redshift of lens  
  > "We obtained VLT/X-Shooter spectroscopy from 390 to 2500 nm through DDT program 295.A-5017" (3 Spectroscopic redshift with VLT/X-Shooter)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed ALMA data properties and background source analysis, including 3 mm continuum limit  
  > "These data will be discussed in detail in forthcoming papers (C17; Frye et al. 2017, in prep.)." (2 Morphology in the near-infrared and millimeter) [from Cañameras et al. 2017, submitted (C17)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (weighting, cell size)
- Observing dates, array configuration, spectral setup and integration time of ALMA data
- Exact image positions of the six arclets and the image-family association
- Prior ranges for LENSTOOL parameters
- Photometry values used in SED fit

## Analysis recipe

1. **Lens model from ALMA CO(4-3) arclets**: LENSTOOL Bayesian MCMC fit of a PIEMD to peak positions of arclets; 10 image-family associations tested, converging model adopted  
  > "We therefore tested 10 plausible associations of individual arclets into image families and adopted the single model that converges and places all images at positions matching those observed." (4 Lens modeling and source reconstruction)
   - software: LENSTOOL
   - parameter: r_core=0.15 kpc, r_cut=100 kpc fixed  
  > "We therefore choose to fix $r_{\rm core}=0.15\,$kpc (cite: limousin07b; richard14), and $r_{\rm cut}=100\,$kpc (cite: brainerd96)" (4 Lens modeling and source reconstruction)
   - fitting: MCMC; free: centroid, sigma_PIEMD, ellipticity, PA; 4000 MCMC iterations for magnification map  
  > "We compute a mean magnification map and uncertainties for each pixel using 4000 MCMC iterations." (4 Lens modeling and source reconstruction)
   - validation: rms offset of images 0.07", about half the beam; varying core/cutoff changes mass <10%  
  > "The rms of the offsets between observed and reconstructed images is 0.07$''$, which is about half the ALMA beam." (4 Lens modeling and source reconstruction)
2. **Enclosed lensing mass within Einstein radius**: Mass from mean radial profile of PIEMD following Limousin et al. 2005  
  > "Following (cite: limousin05), we derive the mass of the deflector of the Ruby from the mean radial profile of the PIEMD" (5 A massive lensing galaxy at z=1.5)
   - software: LENSTOOL
   - fitting: _not stated_
   - validation: _not stated_
3. **Stellar mass from SED fit**: Fit I, F110W, F160W, K photometry with exponentially declining SFH models; F160W surface-brightness profile used to check contamination  
  > "to fit the photometry of the deflector in the $I$, F110W, F160W, and $K$ band with an exponentially declining star formation history with $\tau=20$–200 Myr" (5 A massive lensing galaxy at z=1.5)
   - software: Bruzual & Charlot 2003 models
   - assumption: solar metallicity, Chabrier IMF, Calzetti extinction law  
  > "with solar metallicity, as is common for massive galaxies, a (cite: chabrier03) IMF, and the (cite: calzetti94) extinction law" (5 A massive lensing galaxy at z=1.5)
   - fitting: models with chi2<5 retained  
  > "models within the above range of star formation histories fitting our SED with $\chi^2<5$ result in stellar masses of 2–$2.5" (5 A massive lensing galaxy at z=1.5)
   - validation: _not stated_
4. **Compare stellar and lensing mass to constrain IMF**: Compare M_stellar with M_lens, neglecting gas (<~1e9 Msun) and small dark matter fraction  
  > "This suggests $M_{\rm stellar}\simeq M_{\rm lens}$, which is the case for a Salpeter IMF, whereas a Chabrier IMF underpredicts the lensing mass by about a factor of 2." (6 Evidence for a bottom-heavy IMF)
   - assumption: dark matter at most 10% within 6-7 kpc; gas-to-dust ratio 40-100  
  > "dark matter contributes at most 10 % to the total mass out to 6–7 kpc" (6 Evidence for a bottom-heavy IMF)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **LENSTOOL** : Bayesian strong lens modelling  
  > "We use `LENSTOOL` (cite: jullo07) to model the strong gravitational lensing toward the Ruby." (4 Lens modeling and source reconstruction)
- **SWARP and SCAMP** : astrometric alignment and image construction  
  > "We used SWARP and SCAMP (cite: bertin10a; bertin10b) to align individual frames relative to each other" (2 Morphology in the near-infrared and millimeter)
- **ESO X-Shooter pipeline** : reduction of X-Shooter spectra  
  > "Data were reduced with the ESO X-Shooter pipeline in the standard way" (3 Spectroscopic redshift with VLT/X-Shooter)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Enclosed lensing mass within Einstein radius | 3.70e11 | 0.35e11 | Msun | 2 | $M_{\rm aper}(\theta_{\rm E}) = (3.70 \pm 0.35)
\times 10^{11}\,{\rm M}_{\odot}$ |
| Einstein radius | 0.72 arcsec (6.2 kpc) | 0.06 arcsec / 0.5 kpc | arcsec | 2 | $\theta_{\rm E} =
0.72\ensuremath{''} \pm 0.06\ensuremath{''}$, corresponding to $(6.2 \pm 0.5)\,$kpc |
| PIEMD velocity dispersion | 260.6 | not stated | km/s | 1 | velocity dispersion $\sigma_{\rm PIEMD}=260.6\,{\rm km}\,{\rm s}^{-1}$ |
| Stellar mass (Chabrier IMF) | 2-2.5e11 | not stated | Msun | 3 | result in stellar masses of 2–$2.5
\times 10^{11}\,{\rm M}_\odot$ |
| Sersic index of deflector | 1.15 | 0.29 | dimensionless | 3 | Sersic index of $1.15\pm0.29$ |

## Qualitative findings

- Lens is a massive galaxy at z=1.525 with a faint AGN signature and an IMF consistent with Salpeter rather than Chabrier  
  > "This suggests $M_{\rm stellar}\simeq M_{\rm lens}$, which is the case for a Salpeter IMF" (6 Evidence for a bottom-heavy IMF)

## Claim tuples

- H: The z=1.5 lensing galaxy has a bottom-heavy IMF | E: Compare lensing mass from ALMA-based lens model with SED stellar mass for Chabrier and Salpeter IMFs | R: Lensing mass 3.7e11 Msun; Chabrier stellar mass 2-2.5e11; Salpeter 1.7 times higher | F: Salpeter-like bottom-heavy IMF favored | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: IMFs with M/L much greater than Salpeter ruled out as they would exceed the lensing mass  
  > "We also ruled out the IMFs with average mass-to-light ratios that are much greater than Salpeter" (6 Evidence for a bottom-heavy IMF)
- How they decided it was enough: _not stated_
- Limitation (authors): Image family association is difficult as velocities overlap  
  > "since the velocities partially overlap, identifying image families unambiguously remains difficult" (4 Lens modeling and source reconstruction)
- Caveat (inferred, ours): Dark matter fraction and gas mass assumed, not measured
- Caveat (inferred, ours): Single lens model with fixed core and cutoff radii; no systematic uncertainty from SED degeneracies in stellar mass
- Caveat (inferred, ours): Possible faint AGN contribution not modelled in SED

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging details and arclet positions
- Missing: Photometry tables
- Missing: Lens model priors and input files
- Data volume (inferred): ~10-50 GB for ALMA Band 3 data; HST and VLT data additional
- Score (inferred): 3/5, ALMA data are used only for arclet positions, with processing deferred to C17; the lens model is described qualitatively.
- Rediscovery candidate: no, ALMA processing and the model inputs are not given in this paper.

## Links

- Method: Jullo et al. 2007 (cite: jullo07) (LENSTOOL lens modelling)
- Companion: Cañameras et al. 2017, submitted (C17) (ALMA data and background source properties)
- Related: Planck's Dusty GEMS

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 69,
  "stated": 28,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
