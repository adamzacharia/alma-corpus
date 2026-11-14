# GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment

`2025A&A...700A.165B` | Astronomy and Astrophysics 2025 | first author: Buzzo, Maria Luisa | arXiv: 2506.19994 | DOI: 10.1051/0004-6361/202555616

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How much molecular (CO) and neutral (HI) gas does the ultra-diffuse galaxy GAMA 526784 contain, and could a nearby companion have shaped its star formation and star clusters?  
  > "We analyse low- and high-resolution CO observations to place constraints on the molecular gas content of the galaxy, compare them with HI data, and examine the star formation efficiency of GAMA 526784." (abstract)
- Target **GAMA 526784**: coordinates _not stated_; z/distance z = 0.0091; D_L = 40 Mpc  
  > "GAMA 526784 ($z = 0.0091$)" (Results and Discussion); "where $D_L=40$ Mpc is the luminosity distance." (Analysis); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00898.S
- bands: Band 3  
  > "using ALMA’s Band 3 during Cycle 8" (2.1 ALMA Observations)
- frequencies and spectral setup: native resolution 10.255 km/s (low-res), 1.282 km/s (high-res)  
  > "The native spectral resolutions of the observations are 10.255 km s$^{-1}$ for the low-resolution data and 1.282 km s$^{-1}$ for the high-resolution data." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 7m (ACA) low-resolution; 12m high-resolution  
  > "was observed for 3 hours with the 7m array" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 15.8'' x 9.9'' (low-res); 0.74'' x 0.56'' (high-res)  
  > "For the high-resolution data, the beam sizes are FWHM = $0.74'' \times 0.56''$." (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 1.0 mJy/beam (low-res), 9 uJy/beam (high-res)  
  > "reaching sensitivities of 1.0 mJy beam$^{-1}$ and 9 $\mu$Jy beam$^{-1}$, respectively" (2.1 ALMA Observations)
- time on source: 3.01 h (7M), 6.45 h (12M)  
  > "Exposure time (hours)             | 3.01                  | 6.45" (Table 1)
- observing dates: Nov-Dec 2021 (low-res); Nov 2021-Jul 2022 (high-res)  
  > "Observations were conducted between November and December 2021 for the low-resolution data and between November 2021 and July 2022 for the high-resolution data." (2.1 ALMA Observations)
- pi or archival as stated: PI A. Zanella, Cycle 8  
  > "(PI: A. Zanella, Project ID: 2021.1.00898.S)" (2.1 ALMA Observations)
- Line: CO J=1-0 (115.271202 GHz)
- Other facility **GBT**: HI 21 cm spectrum (L-band, VEGAS), project GBT24B-319  
  > "GBT observations of GAMA 526784 were conducted on September 29, 2024, under project ID GBT24B-319." (2.2 Green Bank Telescope Observations)
- Other facility **Subaru HSC**: grizy imaging of the putative companion  
  > "stellar mass estimation through SED fitting using the five *grizy* HSC filters" (Environment)
- External data: Gas-phase metallicity 12+log(O/H)=8.3  
  > "Assuming a global gas-phase metallicity of $12 + \log(\mathrm{O}/\mathrm{H}) = 8.3$ (cite: Marino_13)" (Molecular Gas Mass) [from (cite: Marino_13)]
- External data: Main-sequence sSFR relation  
  > "star formation main sequence (SFR–$M_\star$ relation) of (cite: Whitaker_12)" (Molecular Gas Mass) [from (cite: Whitaker_12)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline with CASA  
  > "The data were reduced using the standard ALMA pipeline with the `CASA` software (cite: McMullin_07)." (2.1 ALMA Observations)
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
- continuum subtraction: continuum map from full spectral range excluding channels where CO(1-0) expected  
  > "excluding the channels where CO($1-0$) emission was expected based on the galaxy’s redshift" (Continuum Emission)
- line free channels: _not stated_
- primary beam correction: applied  
  > "All data has been corrected for primary beam attenuation." (4.1 CO(1-0) Emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO line map and uv-plane PSF-fitting method  
  > "We adopted the method used by (cite: Zanella_23) and (cite: Zanella_18)." (CO(1-0) Emission) [from (cite: Zanella_23); (cite: Zanella_18)]
- HI dynamical mass approach  
  > "using the approach of (cite: Spekkens_18)" (HI Mass Calculation) [from (cite: Spekkens_18)]
- Companion data reduction and SED fitting identical to Paper I  
  > "are identical to those used for GAMA 526784" (Environment) [from Paper I (Buzzo et al. 2025)]

### Not stated but needed to reproduce (our reading)

- Star cluster positions (from Paper I) and the optical centre used for the PSF fit
- Which spectral windows or channels define the continuum
- Conversion details from flux upper limit to L'CO and gas mass (line width, brightness-temperature ratio)
- GBT baseline order, smoothing width and flux scale
- Calibration and flagging details of the pipeline

## Analysis recipe

1. **uv-plane CO spectrum and averaged map**: Fit a point-source (PSF) model in the uv-plane at fixed optical centre per channel; average channels around the expected CO frequency  
  > "we extracted the CO spectrum by applying the Fourier Transform of a PSF model and looked for a detection around the expected frequency" (CO(1-0) Emission)
   - software: GILDAS, CASA
   - parameter: Low-res: +-30 km/s (three channels each side); high-res: 10 km/s width  
  > "allowing for a velocity width of 30 km s$^{-1}$ up and down, i.e. three channels at each side" (CO(1-0) Emission)
   - assumption: Galaxy unresolved at ACA resolution; GMCs co-spatial with star clusters and unresolved  
  > "GMCs are unresolved at the resolution of our observations and fitting them as point sources" (CO(1-0) Emission)
   - fitting: _not stated_
   - validation: Image-plane inspection gave the same non-detection  
  > "we also inspected the imaging and arrived at the same conclusions, i.e. no CO detection" (CO(1-0) Emission)
2. **derive H2 mass upper limits**: 5 sigma flux limits converted to L'CO and M_H2 with metallicity-dependent alpha_CO (Accurso+17); MW alpha_CO for comparison  
  > "we primarily adopt a metallicity-dependent CO-to-H$_2$ conversion factor" (Molecular Gas Mass)
   - parameter: 12+log(O/H)=8.3; alpha_CO,met=17.01; alpha_CO,MW=4.36  
  > "the recovered $\alpha_{\rm CO,met} = 17.01 M_\odot\, (\mathrm{K\, km\, s^{-1}\, pc^2})^{-1}$" (Molecular Gas Mass)
   - assumption: alpha_CO scatter 0.165 dex  
  > "\log \alpha_{\rm CO} (\pm 0.165\, {\rm dex})" (Molecular Gas Mass)
   - fitting: _not stated_
   - validation: _not stated_
3. **HI mass and dynamical mass from GBT**: M_HI=2.36e5 D_L^2 S_HI; W50 gives V_rot and M_dyn within 3Re  
  > "M_{\rm HI} = 2.36 \times 10^5 \times D_L^2 \times S_{\rm HI}\, M_{\odot}" (HI Mass Calculation)
   - software: GBTIDL
   - parameter: D_L=40 Mpc; q0=0.2; b/a=0.52; Re=2.5 kpc  
  > "with $R_e = 2.5$ kpc" (HI Mass Calculation)
   - assumption: HI extends to 3 Re; W50 = 2 Vrot sin i  
  > "we assume that the HI gas distribution extends out to three effective radii" (HI Mass Calculation)
   - fitting: _not stated_
   - validation: V_rot consistent with ionised gas rotation amplitude  
  > "This value is consistent with the ionised gas rotation amplitude" (HI Mass Calculation)

## Software

- **CASA** : ALMA pipeline reduction  
  > "The data were reduced using the standard ALMA pipeline with the `CASA` software" (2.1 ALMA Observations)
- **GILDAS** : uv-plane analysis  
  > "analysed in the uv-plane using `GILDAS`" (2.1 ALMA Observations)
- **GBTIDL** : GBT reduction with getps  
  > "The data were reduced using the standard GBTIDL routine `getps`" (2.2 Green Bank Telescope Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) 5 sigma flux upper limit, galaxy | <=5.80 | not stated | uJy | 1 | / GAMA 526784 / $\leq$5.80 / |
| M_H2 5 sigma upper limit (metallicity alpha_CO) | log(M_H2/Msun) <~ 7.6 | not stated | log Msun | 2 | $\log(M_{\rm H_2}/M_{\odot}) \lesssim 7.6 |
| HI integrated flux | 1.26 | 0.13 | Jy km/s | 3 | $S_{\rm HI}=1.26\pm0.13$ Jy km s$^{-1}$ |
| HI mass | log M_HI = 8.7 | 0.9 | log Msun | 3 | $\log(M_{\rm HI}/M_{\odot}) = 8.7 \pm 0.9$ |
| W50 | 105 | not stated | km/s | 3 | $W_{50}=105$ km s$^{-1}$ |
| V_rot | 59.3 | 5.9 | km/s | 3 | $V_{\rm rot} = 59.3 \pm 5.9$ km s$^{-1}$ |
| dynamical mass within 3Re | log M_dyn = 10.0 | 1.0 | log Msun | 3 | $\log(M_{\rm dyn}^{3R_e}/M_{\odot}) = 10.0 \pm 1.0$ |
| M_HI/M_star | 2.88 | not stated | dimensionless | 3 | $M_{HI}/M_{\star} = 2.88$ |

## Qualitative findings

- No CO(1-0) or continuum detected at the galaxy or any star cluster position  
  > "The continuum was not detected neither in the low- or the high-resolution data" (Continuum Emission)

## Claim tuples

- H: Does GAMA 526784 host CO-traceable molecular gas? | E: uv-plane PSF fits to ACA and 12m cubes | R: no CO detected; M_H2 5sigma < ~10^7.6 Msun | F: Gas-rich in HI but CO-faint; explained by CO-dark H2, delayed HI-to-H2 conversion or turbulence | **supported**
- H: A nearby companion triggered the star clusters | E: HSC photometry and GBT HI | R: companion at ~48 kpc with similar colours aligned with cluster string; no second HI line | F: possible association, not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane analysis is preferable for compact, unresolved, low-SNR sources  
  > "For compact, unresolved, low-SNR sources such as ours, uv-plane analysis is therefore preferable" (2.1 ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Current data cannot distinguish between scenarios  
  > "Current data cannot definitively distinguish between these scenarios." (Environment)
- Caveat (inferred, ours): Only upper limits; conclusions depend strongly on assumed alpha_CO and metallicity
- Caveat (inferred, ours): Companion redshift unconfirmed
- Caveat (inferred, ours): HI mass uncertainty of 0.9 dex looks inconsistent with the quoted flux error

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Cluster positions from Paper I
- Missing: GILDAS fitting scripts
- Missing: GBT reduction parameters
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Data are likely archival and the method is simple, but many processing details are unstated.
- Rediscovery candidate: no, Result is non-detection upper limits and key inputs are unstated.

## Links

- Method: (cite: Zanella_23) (CO uv-plane method)
- Method: (cite: Accurso_17) (metallicity-dependent alpha_CO)
- Companion: (cite: Buzzo_25c) (Paper I: optical imaging and IFS of GAMA 526784)
- Related: PHANGS
- Related: GBT24B-319

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
