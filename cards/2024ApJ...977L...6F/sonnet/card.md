# The Impact of Shear on Disk Galaxy Star Formation Rates

`2024ApJ...977L...6F` | The Astrophysical Journal Letters 2024 | first author: Fortune-Bashee, Xena | arXiv: 2409.07622 | DOI: 10.3847/2041-8213/ad91a3

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does the star formation efficiency per orbital time depend on orbital shear (beta) as predicted by the shear-driven GMC collision model, eps_orb proportional to (1-0.7 beta)?  
  > "we test a prediction of the shear-driven GMC collision model that $\epsilon_\mathrm{orb}\propto(1-0.7\beta)$" (abstract)
- Target **49 PHANGS-ALMA galaxies (NGC 4321 shown as example)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: azimuthal averages in 500 pc-wide radial bins  
  > "reported as azimuthal averages in 500 pc-wide radial bins across each galaxy" (Method)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **WISE and ground-based Halpha**: SFR surface density from Halpha plus WISE 22 micron  
  > "Values of $\Sigma_\mathrm{SFR}$ were derived by combining ground-based H$\alpha$ narrow-band and WISE 22 $\mu$m imaging data" (Method)
- Other facility **THINGS, VIVA, VLA-HERACLES, PHANGS-VLA**: HI 21 cm data for Sigma_atom  
  > "including THINGS (cite: Walter_etal_2008), VIVA (cite: Chung_etal_2009), VLA–HERACLES (cite: leroy_etal_2012), and PHANGS–VLA (PI: D. Utomo)" (Method)
- External data: Machine-readable tables of Sigma_SFR, Sigma_mol, Sigma_atom, Omega, beta in 500 pc radial bins  
  > "We extract these measurements from machine-readable tables (cite: Sun_etal_2022)" (Method) [from Sun et al. 2022 (cite: Sun_etal_2022)]
- External data: Bar footprint definitions  
  > "annuli that do and do not overlap with the footprint of a stellar bar, (cite: Querejeta_etal_2021)" (4.2 Impact of a Bar on Star Formation) [from (cite: Querejeta_etal_2021)]
- External data: Rotation curves and v_circ from CO kinematics  
  > "$v_\mathrm{circ}$ and $\beta$ were based on CO kinematics (cite: Lang_etal_2020)" (Method) [from (cite: Lang_etal_2020)]

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

- Derivation of Sigma_SFR, Sigma_mol, Sigma_atom, v_circ and beta  
  > "refer readers to (cite: Sun_etal_2022) for more details" (Method) [from (cite: Sun_etal_2022)]
- Sigma_SFR calibration  
  > "following the calibration by (cite: Belfiore_etal_2023)" (Method) [from (cite: Belfiore_etal_2023)]
- beta<=0.5 fit range and galaxy-normalized efficiency method  
  > "This choice, following (cite: Suwannajak_etal_2014), avoids the regime where $\beta$ is no longer significantly smaller than unity" (Footnote 2) [from (cite: Suwannajak_etal_2014)]

### Not stated but needed to reproduce (our reading)

- Fitting method, likelihood and uncertainty estimation for alpha_CC
- How binned-median uncertainties were computed
- Exact galaxy list and the 32-galaxy HI subsample
- Version of the Sun et al. 2022 tables
- Treatment of the inner-kpc exclusion in detail

## Analysis recipe

1. **Assemble radial-bin measurements**: Take Sigma_SFR, Sigma_gas, Sigma_mol, Omega, beta from published tables; compute eps_orb = Sigma_SFR t_orb / Sigma_gas  
  > "We derive $\epsilon_\mathrm{orb}$ and $\beta$ for each radial bin in each galaxy" (Method)
   - assumption: Metallicity-dependent CO-to-H2 conversion factor  
  > "using a metallicity-dependent CO-to-H$_2$ conversion factor (cite: Sun_etal_2020a; Sun_etal_2020b)" (Method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Bin by beta and fit shear law**: Median eps_orb in beta bins of width 0.05, excluding bins with <10 points; fit eps_orb0(1-alpha_CC beta) for beta<=0.5  
  > "We evaluate median values of $\epsilon_\mathrm{orb}$ in bins of uniform width $\Delta\beta=0.05$, excluding bins with $<10$ data points." (3.1 Impact of Shear on Star Formation)
   - fitting: _not stated_
   - validation: Insensitive to bin width; consistent with non-parametric reconstruction; repeated excluding inner 1 kpc and with galaxy-normalized efficiencies  
  > "These fit parameters are insensitive to choices of bin width in $\beta$ and consistent with alternative, non-parametric methods for reconstructing the median trends." (3.1 Impact of Shear on Star Formation)
3. **Compare barred and non-barred annuli**: Split annuli by overlap with bar footprint; compare median eps_orb and refit  
  > "we divide the measurements into two subsamples, i.e., annuli that do and do not overlap with the footprint of a stellar bar" (4.2 Impact of a Bar on Star Formation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **NumPy** : listed in software section  
  > "`NumPy` (cite: NumPy_2020), `Matplotlib` (cite: Matplotlib_2007), `astropy` (cite: Astropy_2013; Astropy_2018; Astropy_2022)" (Software)
- **Matplotlib** : listed in software section  
  > "`NumPy` (cite: NumPy_2020), `Matplotlib` (cite: Matplotlib_2007), `astropy` (cite: Astropy_2013; Astropy_2018; Astropy_2022)" (Software)
- **astropy** : listed in software section  
  > "`NumPy` (cite: NumPy_2020), `Matplotlib` (cite: Matplotlib_2007), `astropy` (cite: Astropy_2013; Astropy_2018; Astropy_2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CC (total gas, 32 galaxies) | 0.76 | 0.16 | dimensionless | 2 | $\epsilon_\mathrm{orb,\,0}=0.045\pm0.002$ and $\alpha_\mathrm{CC}=0.76\pm0.16$ |
| alpha_CC excluding inner 1 kpc | 0.73 | 0.21 | dimensionless | 2 | $\epsilon_\mathrm{orb,\,0}=0.045\pm0.002$ and $\alpha_\mathrm{CC}=0.73\pm0.21$ |
| alpha_CC* (galaxy-normalized) | 0.80 | 0.15 | dimensionless | 2 | derive $\alpha_\mathrm{CC}^*=0.80\pm0.15$ |
| alpha_CC,mol (49 galaxies) | 1.08 | 0.23 | dimensionless | 2 | $\epsilon_\mathrm{orb,\,mol,\,0}=0.088\pm0.005$ and $\alpha_\mathrm{CC,\,mol}=1.08\pm0.23$ |
| Median eps_orb barred | 0.0324 | 0.0017 | dimensionless | 3 | The barred sample has $\overline{\epsilon_\mathrm{orb}}=0.0324\pm0.0017$ and the non-barred has $\overline{\epsilon_\mathrm{orb}}=0.0375\pm0.0015$. |
| Median eps_orb non-barred | 0.0375 | 0.0015 | dimensionless | 3 | The barred sample has $\overline{\epsilon_\mathrm{orb}}=0.0324\pm0.0017$ and the non-barred has $\overline{\epsilon_\mathrm{orb}}=0.0375\pm0.0015$. |

## Qualitative findings

- eps_orb declines with increasing beta, consistent with shear-driven GMC collision theory  
  > "We conclude there is a significant trend detected of declining $\epsilon_\mathrm{orb}$ with increasing $\beta$" (3.1 Impact of Shear on Star Formation)

## Claim tuples

- H: SFE per orbit follows (1-0.7 beta) as predicted by shear-driven GMC collisions | E: Fit eps_orb vs beta in binned medians over annuli of PHANGS galaxies | R: alpha_CC=0.76±0.16 | F: Data consistent with the shear-driven GMC collision prediction | **supported**
- H: A bar changes SFE per orbit | E: Compare barred and non-barred annuli | R: Barred median is 0.86 of non-barred; shear predicts 0.79 | F: Reduction attributable to lower shear in barred regions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability as rate-limiting step predicts the opposite trend  
  > "Such a trend is the opposite of that expected if growth of gravitational instabilities is the rate-limiting step for galactic disk star formation" (4 Summary and Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic biases affect barred and non-barred samples differently  
  > "There are also known systematic biases (cite: Lang_etal_2020; Sun_etal_2023) that impact the barred and non-barred samples differently." (4.2 Impact of a Bar on Star Formation)
- Caveat (inferred, ours): Fit method and error treatment unspecified
- Caveat (inferred, ours): Binned medians of correlated annuli within galaxies may not be independent
- Caveat (inferred, ours): Result depends on the CO-to-H2 conversion prescription
- Caveat (inferred, ours): Prediction valid only for beta<=0.5, which limits the dynamic range

## Reproducibility

- Data public (paper): Uses published machine-readable tables from Sun et al. 2022  
  > "We extract these measurements from machine-readable tables (cite: Sun_etal_2022)" (Method)
- Products in archive: _not stated_
- Missing: Fitting code and procedure
- Missing: Exact table version and galaxy lists
- Data volume (inferred): <1 GB (derived tables only)
- Score (inferred): 3/5, Simple analysis on public tables, but fitting details are unstated.
- Rediscovery candidate: yes, Public derived tables, simple binned fit, numeric results; fit details must be inferred.

## Links

- Method: Sun et al. 2022 (cite: Sun_etal_2022) (Source of measurements and derivations)
- Method: Suwannajak, Tan & Leroy 2014 (cite: Suwannajak_etal_2014) (Earlier analysis method followed)
- Companion: Leroy et al. 2021 (cite: Leroy_etal_2021a) (PHANGS-ALMA CO(2-1) survey)
- Related: PHANGS-ALMA
- Related: PHANGS-VLA
- Related: THINGS
- Related: VIVA
- Related: HERACLES

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 22,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
