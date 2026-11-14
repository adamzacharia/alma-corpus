# ATOMIUM: halide molecules around the S-type AGB star W Aquilae

`2021A&A...655A..80D` | Astronomy and Astrophysics 2021 | first author: Danilovich, T. | arXiv: 2109.04747 | DOI: 10.1051/0004-6361/202141757

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the abundances and spatial distributions of AlCl and AlF around the S-type AGB star W Aql, and of HCl and HF from PACS, and what do they imply for chemistry and F/Cl enrichment?  
  > "We aim to determine the abundances of AlCl and AlF from rotational lines, which have been observed for the first time towards an S-type AGB star." (abstract)
- Target **W Aql**: coordinates _not stated_; z/distance 395 pc (Gaia EDR3: 374 ± 22 pc)  
  > "we use the distance for W Aql obtained by (cite: Danilovich2014) of 395 pc, which was found using a period-luminosity relation." (4.1 Radiative transfer model); distance from Danilovich et al. 2014 period-luminosity relation  
  > "we use the distance for W Aql obtained by (cite: Danilovich2014) of 395 pc, which was found using a period-luminosity relation." (4.1 Radiative transfer model)

## Data provenance

- ALMA projects: 2018.1.00659.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact, mid and extended arrays combined  
  > "These three datasets were combined to produce more sensitive data cubes to allow us to examine the observations in more detail." (2 ALMA observations of AlCl and AlF)
- baselines: _not stated_
- angular resolution: compact 1.11"x0.88" at 262.2 GHz; mid 0.374"x0.250"; extended 0.024"x0.021"; combined 32x30 mas (AlCl), 150x130 mas (AlF)  
  > "We found the most useful combined data to have angular resolution of $32\times30$ mas for AlCl and $150\times130$ mas for AlF." (2 ALMA observations of AlCl and AlF)
- max recoverable scale: 8.9" compact, 3.9" mid, 0.4" extended  
  > "mid (angular resolution $0.374\ensuremath{''}\times0.250\ensuremath{''}$ and MRS = 3.9$''$)" (2 ALMA observations of AlCl and AlF)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ATOMIUM large programme, PI L. Decin  
  > "As part of the ATOMIUM[^4] programme (2018.1.00659.L, PI: L. Decin)" (2 ALMA observations of AlCl and AlF)
- Line: Al35Cl v=0 J=18-17 (262.219 GHz)
- Line: Al37Cl v=0 J=16-15 (227.643 GHz)
- Line: AlF v=0 J=7-6 (230.794 GHz)
- Other facility **Herschel/PACS**: Spectra of HCl and HF lines towards W Aql and chi Cyg  
  > "We searched the PACS spectrum of W Aql (cite: Nicolaes2018) and found evidence of H$^{35}$Cl and H$^{37}$Cl emission in the $J=3\to2$ and $J=4\to3$ lines." (3.2 HCl and HF)
- External data: Circumstellar parameters of W Aql (distance, temperature, velocity law, dust, kinetic temperature)  
  > "For this study, we use the circumstellar parameters derived by (cite: Danilovich2014), including the assumption of silicate dust, and include the adjusted mass-loss rate found by (cite: Ramstedt2017)." (4.1 Radiative transfer model) [from (cite: Danilovich2014; Ramstedt2017)]
- External data: Line data from CDMS and ExoMol (Yousefi2018 AlCl/AlF radiative data)  
  > "we obtained the level and radiative information from the ExoMol database[^6] (cite: Tennyson2016) and the collisional rates from a variety of sources" (4.2 Molecular data) [from (cite: Tennyson2016; Yousefi2018)]
- External data: PACS spectrum of W Aql  
  > "We searched the PACS spectrum of W Aql (cite: Nicolaes2018)" (3.2 HCl and HF) [from (cite: Nicolaes2018)]

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
- uv taper: 0.2" taper for AlF measurement  
  > "For AlF the measurement was done for data that had been combined with a taper of 0.2$''$" (2 ALMA observations of AlCl and AlF)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: compact, mid, extended datasets combined  
  > "These three datasets were combined to produce more sensitive data cubes" (2 ALMA observations of AlCl and AlF)
- smoothing: AlF channels averaged to ~2.5 km/s (AlCl ~1.1 km/s)  
  > "we average channels to give a lower velocity resolution of $\sim2.5~\mathrm{km\,s}^{-1}$ (compared with $\sim1.1~\mathrm{km\,s}^{-1}$ for AlCl)" (2 ALMA observations of AlCl and AlF)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and combination of the three configurations  
  > "three configurations of ALMA, which we will refer to as the compact" (2 ALMA observations of AlCl and AlF) [from (cite: Decin2020)]
- Velocity profile, dust treatment, circumstellar parameters  
  > "The same velocity profile[^5] is used here as in (cite: Danilovich2014)" (4.1 Radiative transfer model) [from (cite: Danilovich2014)]
- Chemical kinetics model and RATE12 network  
  > "We use the one-dimensional chemical kinetics model of (cite: Van-de-Sande2018b), and the publicly available gas-phase only RATE12 reaction network" (4.3 Radial distribution of HCl and HF from chemical modelling) [from (cite: Van-de-Sande2018b; McElroy2013)]

### Not stated but needed to reproduce (our reading)

- Calibration and combination procedure, CASA version and weighting/robust values
- Cell size, image size and continuum subtraction details
- Noise levels of the combined cubes
- The ALI code is not named or released
- Details of the chi-square fitting procedure and grid steps

## Analysis recipe

1. **Measure line properties**: Gaussian fits for central velocities; zeroth moment maps with 2 sigma contours for extents; spectra from circular apertures; azimuthally averaged radial profiles  
  > "The central velocities were found by fitting Gaussian profiles to spectra extracted from the combined cubes." (2 ALMA observations of AlCl and AlF)
   - parameter: 2 sigma contours binned with at least 10 samples per bin  
  > "we binned and averaged the values with at least 10 samples per bin, corresponding to angular ranges of $\geq 60^\circ$." (2 ALMA observations of AlCl and AlF)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer modelling of AlCl and AlF**: Spherically symmetric accelerated lambda iteration non-LTE model fit to spectra and radial profiles with step-function abundance profiles  
  > "we use a spherically symmetric model and the accelerated lambda iteration method (cite: Rybicki1991)" (4.1 Radiative transfer model)
   - software: ALI code
   - parameter: Distance 395 pc, Mdot 3e-6 Msun/yr, v_inf 16.5 km/s  
  > "| Mass-loss rate, $\dot{M}$ | $3\times 10^{-6}\;\mathrm{M}_\odot~\mathrm{ yr}^{-1}$ |" (Table 2)
   - assumption: AlCl modelled dust-free with 700 K blackbody IR field; AlF with silicate dust; H2 ortho-to-para 3; SiS-H2 rates as stand-in for AlCl  
  > "we run a dust-free model for AlCl but include an additional infrared radiation field, based on a blackbody with a temperature of 700 K" (4.1 Radiative transfer model)
   - fitting: chi2 minimisation primarily on radial profiles  
  > "when $\chi^2$ statistics are calculated primarily from the radial profiles" (5.4 Model uncertainties)
   - validation: Compared to spectra and radial profiles; amorphous carbon dust test for AlF  
  > "Hence, we also tested an AlF model with amorphous carbon dust (cite: Suh2000) in place of silicate dust." (5.2 AlF)
3. **HCl and HF abundances from PACS**: Scale chemical-model radial abundance profile until RT model matches PACS lines without overpredicting non-detections  
  > "we find the best fitting model by scaling the radial abundance distribution until the model lines best reproduce the observed data." (4.3 Radial distribution of HCl and HF from chemical modelling)
   - software: RATE12 chemical model
   - parameter: H35Cl/H37Cl fixed to 2.4  
  > "We also fixed the H$^{35}$Cl/H$^{37}$Cl abundance ratio to 2.4" (5.3.1 HCl)
   - fitting: _not stated_
   - validation: _not stated_
4. **Chemistry of AlF and AlCl**: Extend chemical network with Al reactions, rates from G4 and MESMER RRKM calculations, compare rates with expansion rate  
  > "we extended the Rate12 chemical model by including reactions describing the chemistry of aluminium" (6.5 Chemistry of AlCl and AlF)
   - software: Gaussian 16, MESMER
   - fitting: _not stated_
   - validation: Transition state heights adjusted within 6 kJ/mol to match observations  
  > "The rate coefficients for R1 to R6 were adjusted by varying the heights of the transition states within the expected uncertainty of the G4 level of theory (6 kJ mol$^{-1}$)" (11 Supplementary information)

## Software

- **MOLSCAT** : AlF-H2 collisional rate calculations  
  > "All these computations are done using the MOLSCAT package (cite: Hutson2012)." (9.2 AlF)
- **MESMER** : Rate coefficient estimation  
  > "The Master Equation Solver for Multi-Energy well Reactions (MESMER) program (cite: Glowacki2012) was then used to estimate rate coefficients." (11 Supplementary information)
- **Gaussian 16** Revision B.01: G4 energetics  
  > "calculated using the very accurate G4 method within the Gaussian suite of programs (cite: Frisch2016)" (6.5 Chemistry of AlCl and AlF)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Al35Cl abundance inner / outer | 8.5e-8 / 1.7e-7 | formal ~20% | relative to H2 | 2 | had an inner abundance $f_0=8.5\times 10^{-8}$, relative to $\mathrm{H}_2$, from the stellar surface out to $R_\mathrm{step}=1.4\times 10^{14}$ cm |
| Al37Cl abundance | 7e-8 | not stated | relative to H2 | 2 | we find the best model to have a constant abundance of $7\times 10^{-8}$ relative to $\mathrm{H}_2$. |
| AlF abundance inner / outer | 1e-7 / 4e-8 | formal ~5% | relative to H2 | 2 | we find the best model with an abundance of $f_0=1\times 10^{-7}$ relative to $\mathrm{H}_2$ in the inner region |
| HF abundance upper limit | <=1e-8 | not stated | relative to H2 | 3 | We find an upper limit on the HF abundance of $\leq1\times 10^{-8}$ relative to $\mathrm{H}_2$. |
| 35Cl/37Cl from AlCl, outer | 2.4 | not stated | dimensionless | 2 | in the outer region we find it is twice as high: Al$^{35}$Cl/Al$^{37}$Cl $=2.4$ |
| Average LSR velocity | -23.1 | 0.9 | km/s | 1 | we find an average LSR velocity of $-23.1\pm0.9~\mathrm{km\,s}^{-1}$ |

## Qualitative findings

- AlCl is clumpy and confined within 0.1" of the star; AlF extends to 0.2-0.6".  
  > "AlCl is found in clumps very close to the star, with emission confined within 0.1$''$ of the star." (abstract)

## Claim tuples

- H: Do halides AlCl and AlF exist around an S-type AGB star and where are they? | E: Imaged ALMA lines of AlCl and AlF in W Aql | R: AlCl within 0.1"; AlF out to 0.6" | F: First detection of AlCl and AlF towards an S-type star | **supported**
- H: Has F been synthesised and dredged up in W Aql? | E: Compared AlF (+HF) abundance with solar F | R: AlF abundance 1e-7 exceeds solar F 7.2e-8 | F: F is dredged up and ejected | **supported**
- H: Can gas-phase chemistry explain AlCl and AlF distributions? | E: Extended chemical kinetics model with Al reactions | R: AlF abundance reproduced inside 3e15 cm but not its disappearance; AlCl drop not reproduced | F: AlF likely removed by clustering; AlCl depletion unexplained | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: NaCl detections claimed by De Beck & Olofsson 2020 reassigned to 30SiO v=4 and H13CN  
  > "we identify it as the 260.2248 GHz line of H$^{13}$CN" (3.1 NaCl and KCl)
- How they decided it was enough: _not stated_
- Limitation (authors): 1D model cannot account for 3D asymmetry; true uncertainties much larger than formal ones  
  > "This means that our actual uncertainties are much larger than the formal uncertainties and cannot easily be quantified." (5.4 Model uncertainties)
- Caveat (inferred, ours): Spherical models applied to clumpy asymmetric emission
- Caveat (inferred, ours): HCl/HF from unresolved PACS lines with blends; abundance profile shape assumed from chemistry model
- Caveat (inferred, ours): Collisional rates for AlCl borrowed from SiS-H2
- Caveat (inferred, ours): Inner-wind density extrapolated, possibly an order of magnitude too low

## Reproducibility

- Data public (paper): ALMA data acknowledged as ADS/JAO.ALMA#2018.1.00659.L  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00659.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Combined cube imaging parameters
- Missing: ALI code
- Missing: Fit grids and chi2 details
- Data volume (inferred): Large (hundreds of GB for three ATOMIUM configurations of one source, if raw)
- Score (inferred): 3/5, Models and parameters are well described, but the imaging/calibration of combined data is inherited and the RT code is not public.
- Rediscovery candidate: no, Imaging recipe for combined cubes is not given and modelling uses unreleased code.

## Links

- Method: (cite: Decin2020) (ATOMIUM observations and data combination)
- Method: (cite: Danilovich2014) (W Aql circumstellar model)
- Method: (cite: Van-de-Sande2018b) (Chemical kinetics outflow model)
- Companion: (cite: Gottlieb2021) (ATOMIUM W Aql line survey)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 35,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
