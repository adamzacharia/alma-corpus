# Emergence of high-mass stars in complex fiber networks (EMERGE): III. Fiber networks in Orion

`2024A&A...690A.375S` | Astronomy and Astrophysics 2024 | first author: Socci, A. | arXiv: 2409.01321 | DOI: 10.1051/0004-6361/202449316

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How is the dense gas in seven low- to high-mass Orion star-forming regions organised into velocity-coherent fibers, and what are the fibers' masses, lengths, kinematics, virial state and link to star formation?  
  > "We aim to investigate the dense gas organisation prior to the formation of stars in a selected sample of regions within Orion." (abstract)
- Target **OMC-1, OMC-2, OMC-3, OMC-4 South, LDN 1641N (Orion A)**: coordinates _not stated_; z/distance 400 pc  
  > "| OMC-1 | Orion A | 400 | high- | Yes | Evolved | 36 | 423 | 0.09 | 2015.1.00669.S |" (Table 1); distance from _not stated_
- Target **NGC 2023, Flame Nebula (Orion B)**: coordinates _not stated_; z/distance 423 pc  
  > "| NGC 2023 | Orion B | 423 | low- | No | Young | 6 | 8 | 0.75 | 2019.1.00641.S |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00669.S, 2019.1.00641.S, 2013.1.00662.S
- bands: Band 3 (3 mm)  
  > "using ALMA observations at 3mm (Band 3; Proj.IDs: 2015.1.00669.S, 2019.1.00641.S)" (2 EMERGE Early ALMA Survey)
- frequencies and spectral setup: N2H+ (1-0), HNC (1-0), HC3N (10-9) plus 3mm continuum; delta V <= 0.15 km/s  
  > "all observed at high spectral resolution ($\delta V\leq 0.15$ km s$^{-1}$), with the addition of the 3mm-continuum" (2 EMERGE Early ALMA Survey)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: mosaics of 110-145 pointings each, ~200x600 arcsec2  
  > "All targets were observed using independent, large-scale ALMA mosaics, between 110 and 145 pointings each" (2 EMERGE Early ALMA Survey)
- baselines: _not stated_
- angular resolution: 4.5'' (~2000 au)  
  > "The entire EMERGE Early ALMA sample was homogeneously surveyed at a resolution of 4.5$''$" (2 EMERGE Early ALMA Survey)
- max recoverable scale: _not stated_
- sensitivity: sigma ~0.020 Jy/beam (~0.15 K) per channel  
  > "typical value of $\sigma\sim0.020$ Jy beam$^{-1}$, or $\sigma\sim0.15$ K after applying the Jy-to-K conversion" (8.1 Spectral fitting)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: N2H+ 1-0 (93.17 GHz)
- Other facility **IRAM-30m**: short-spacing data combined with ALMA; HCN/HNC maps for gas temperature  
  > "combined with additional low spatial resolution, IRAM-30m (single-dish) data, used as short-spacing information" (2 EMERGE Early ALMA Survey)
- Other facility **Herschel**: total column density maps (36'')  
  > "by *Herschel* FIR measurements (36$''$) of the total gas column density (cite: lombardi14)" (2 EMERGE Early ALMA Survey)
- External data: Catalogues of young stellar objects (protostars/disks)  
  > "ancillary catalogues of young stellar objects (cite: megeath12; furlan16; stutz13)" (2 EMERGE Early ALMA Survey) [from (cite: megeath12; furlan16; stutz13)]
- External data: Gas kinetic temperature calibration from HCN/HNC ratio against NH3  
  > "was calibrated against independent $T_\mathrm{K}$ measurements obtained with NH$_3$ by (cite: hacar20)" (3.2 Gas kinetic temperature) [from (cite: hacar20)]
- External data: N(H2)-I_T(N2H+) calibration relation  
  > "The correlation between $I_\mathrm{T}$(N$_2$H$^{+}$) and N(H$_2$) that is employed follows (cite: hacar18)" (3.3 Column density) [from (cite: hacar18)]

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
- array combination: ALMA + IRAM-30m via Model-Assisted Cleaning plus Feather (MACF)  
  > "reduced using the Model-Assisted Cleaning plus Feather (MACF) method, recovering $\gtrsim90\%$ of the emission detected in our single-dish data" (2 EMERGE Early ALMA Survey)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction, MACF, ancillary data description  
  > "We refer the reader to Paper I for a full description of both the new and ancillary data used here." (2 EMERGE Early ALMA Survey) [from Paper I (cite: hacar24)]
- HiFIVe algorithm and linking metric  
  > "The linking metric in the Position-Position-Velocity (PPV) plane is the same used by (cite: hacar18)" (9 Parameter exploration) [from (cite: hacar18)]
- N2H+ to N(H2) calibration (floor term dropped)  
  > "The correlation between $I_\mathrm{T}$(N$_2$H$^{+}$) and N(H$_2$) that is employed follows (cite: hacar18)" (3.3 Column density) [from (cite: hacar18), (cite: tafalla23)]
- Radial profile fitting details  
  > "A thorough discussion on these changes and on the parameters set in the routine to perform the fitting is given in the paper of this series which focuses on the radial profiles (Paper IV)." (8.4 FilChap) [from Paper IV (cite: socci24)]

### Not stated but needed to reproduce (our reading)

- Calibration and CASA/pipeline versions and MACF imaging parameters (all in Paper I)
- Exact HiFIVe code availability
- Protostar catalogue positions used for association
- Velocity integration ranges per cloud

## Analysis recipe

1. **Derive N(H2) maps**: Temperature-corrected N2H+ integrated intensity converted to N(H2) with the empirical relation, floor term then dropped  
  > "We therefore disregard the floor term in Eq. ([\[eq:caln2hp\]](#eq:caln2hp)) hereafter" (3.3 Column density)
   - parameter: N(H2)=67.4e21 I_T + 12e21 cm-2; 6.96 Jy/beam/K at 4.5''  
  > "using a standard conversion factor of 6.96 Jy beam $^{-1}$ K$^{-1}$ at a resolution of 4.5$''$" (2 EMERGE Early ALMA Survey)
   - assumption: TK constant within each 30'' IRAM-30m beam  
  > "We therefore assumed, as a first order approximation, $T_\mathrm{K}$ constant within each IRAM-30m beam" (3.3 Column density)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit N2H+ hyperfine spectra**: Supervised fits in groups of 5x5 spectra with CLASS hfs method; quality cuts on Vlsr, I, S/N>=3, linewidth  
  > "The fitting of the N$_2$H$^+$ (1$-$0) lines was carried out in groups of $5\times5$ spectra with supervised GILDAS/CLASS customised routines" (8.1 Spectral fitting)
   - software: GILDAS/CLASS
   - parameter: 2<=Vlsr<=15 km/s; I>2.5 K km/s; Tpeak>=3 sigma  
  > "(b) $I > 2.5~\rm{K~km~s}^{-1}$, a threshold which roughly corresponds to the floor term" (8.1 Spectral fitting)
   - fitting: hyperfine fit  
  > "The hyperfine structure of the line (cite: caselli95) was fitted accordingly using the `hfs` method (cite: pety05; gil13)" (Appendix 8.1 Spectral fitting)
   - validation: _not stated_
3. **Identify velocity-coherent fibers**: HiFIVe friends-of-friends in PPV over column density thresholds 20-120 Av step 20; Nmin=10  
  > "(i.e. \[20, 40, 60, 80, 100, 120\] A$_\mathrm{v}$)" (8.3 column density thresholds)
   - software: HiFIVe
   - parameter: linking 2 theta_beam spatially; Nmin=10; smooth=2  
  > "$2\times\theta_\mathrm{beam}$ in angular coordinates, corresponding to 10 points (`Nmin`) as minimum number of Friends to define a structure" (9 Parameter exploration)
   - fitting: _not stated_
   - validation: Compared with Hacar+2018 in OMC-1/2 and tested 17 alternative setups  
  > "different setups applied to all regions composing our survey produce results consistent one with the other and with the final setup chosen" (4 Systematic search)
4. **Fiber widths from radial profiles**: FilChap Gaussian fits to N(H2) radial profiles, no baseline subtraction  
  > "we opted for the Gaussian as fitting function within FilChap to carry out the analysis" (8.4 FilChap)
   - software: FilChap
   - fitting: Gaussian; chi2 test  
  > "we opted for the Gaussian as fitting function within FilChap to carry out the analysis. Although undoubtedly complex in both number of peaks and shape, an additional $\chi^2$ test on the sample of radial cuts suggests the Gaussian function to be the best fitting profile" (Appendix 8.4 New implementations: the integration of FilChap and radial profile fitting)
   - validation: _not stated_
5. **Fiber masses, line masses, kinematics, virial ratio**: Sum N(H2) over pixels for M; sigma_nt from linewidth minus thermal; m_vir=2 sigma_tot^2/G  
  > "$$m_{\rm{vir}} = \frac{2(c_{\rm{s}}(T_{\rm{K}})^2 + \sigma_{\rm{nt}}^2)}{G}=\frac{2\sigma_{\rm{tot}}^2}{G}.$$" (5.3 Line mass)
   - assumption: Factor of 3 omitted in m_vir (1D dispersion); mu_N2H+=29; inclination 45 deg for gradient estimates  
  > "We instead kept the estimate given by Eq. ([\[mvirial\]](#mvirial))" (5.3 Line mass)
   - fitting: _not stated_
   - validation: _not stated_
6. **Associate protostars and correlate fiber density with dense gas mass**: Star-forming fibers have protostars within one beam; linear fit of Sigma(fibers) vs M_tot  
  > "We identified the star-forming fibers in our sample as those structures with protostars enclosed within less than one $\theta_\mathrm{beam}$" (5.3 Line mass)
   - fitting: linear fit  
  > "This correlation reads as $\Sigma (fibers) \sim 0.26~M_\mathrm{tot}$ according to a linear fit to the data." (5.4 Fibers as the preferred organisation of the dense gas in clouds)
   - validation: _not stated_

## Software

- **GILDAS/CLASS** : hyperfine fitting of N2H+ spectra  
  > "supervised fitting of the spectra through customised GILDAS/CLASS routines" (4 Systematic search)
- **HiFIVe** : identify velocity-coherent fibers  
  > "applying the Hierarchical Friends-In-Velocity (HiFIVe) algorithm" (4 Systematic search)
- **FilChap** : radial profile fitting  
  > "with the publicly available routine FilChap" (4 Systematic search)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of fibers | 152 | not stated | count | 3 | we identified and characterised a total of 152 velocity-coherent fibers in our survey |
| Total dense gas mass | 1209 | not stated | Msun | 5 | / Sample       / 55319  / 57585     / 96        / 152    / 1209  |
| Median fiber length | 0.09 | not stated | pc | 3 | with a corresponding median value for the whole sample of 0.09 pc |
| Median FWHM | 0.05 | +0.02/-0.01 | pc | 4 | 0.05$^{+0.02}_{-0.01}$ |
| Median m/m_vir star-forming vs non-star-forming | ~1.1 vs ~0.55 | not stated | dimensionless | 6 | $\langle m/m_{\rm{vir}}\rangle\sim1.1$ (dotted line) for the star-forming fibers and $\langle m/m_{\rm{vir}}\rangle\sim0.55$ |
| Star-forming fibers | 50 fibers associated with 82 protostars | not stated | count | 6 | one third of the fibers in the survey (50) is star forming with two thirds of the protostars in our fields (82) associated to them |

## Qualitative findings

- Fibers have similar mass and length distributions and (trans-)sonic motions in all regions  
  > "the masses and lengths of these objects show similar distributions and consistent median values, as well as (trans-)sonic motions, in all of our targets" (abstract)

## Claim tuples

- H: Fibers are the preferred organisation of dense gas across low- to high-mass regions | E: HiFIVe on ~170,000 N2H+ spectra in seven Orion regions | R: 152 fibers, >95% of components in structures, similar M, L, sonic motions | F: Fibers are the common organisational unit | **supported**
- H: Star-forming fibers are closer to virial | E: Compared m/m_vir of fibers with and without protostars | R: median ~1.1 vs ~0.55 | F: Massive near-virial fibers host most protostars | **supported**
- H: Fiber surface density scales with dense gas mass | E: Linear fit of Sigma(fibers) to M_tot | R: Sigma ~0.26 M_tot within a factor of 2 | F: Fibers generated in constant proportion per unit dense gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Original Hacar+2018 column density thresholds [26,44,66] Av judged insufficient for the wider dynamic range  
  > "these thresholds cannot efficiently sample the whole column density range" (8.3)
- How they decided it was enough: _not stated_
- Limitation (authors): sigma_nt along line of sight only; 3D dispersion likely higher  
  > "acknowledging that the 3D velocity dispersion is likely higher than the one presented" (5.2)
- Caveat (inferred, ours): Fiber identification in PPV may not reflect true 3D structures
- Caveat (inferred, ours): Constant TK per 30'' beam adds artefacts to N(H2)
- Caveat (inferred, ours): Virial ratio omits factor of 3 and magnetic fields
- Caveat (inferred, ours): Linear correlation based on only seven points

## Reproducibility

- Data public (paper): Cubes released as DR2; results table on Zenodo  
  > "The ALMA+IRAM-30m N$_2$H$^+$ (1$-$0) cubes are instead available as Data Release 2 (DR2) on the following website" (Data availability)
- Products in archive: _not stated_
- Code: FilChap public; HiFIVe not stated as released  
  > "<https://github.com/astrosuri/filchap>" (8.4 FilChap)
- Missing: MACF cube production details (Paper I)
- Missing: HiFIVe code
- Missing: Protostar association catalogue
- Data volume (inferred): Large; seven mosaics, final cubes of several GB each
- Score (inferred): 3/5, Processed cubes are public and the analysis is described, but the reduction and HiFIVe code are inherited from other papers.
- Rediscovery candidate: no, Depends on the inherited reduction and HiFIVe code, which are not fully specified here.

## Links

- Method: (cite: hacar18) (HiFIVe and the N2H+ column density calibration)
- Method: (cite: bonanomi24) (MACF ALMA+IRAM-30m combination)
- Method: (cite: suri19) (FilChap)
- Companion: (cite: hacar24) (Paper I, survey and data)
- Companion: (cite: socci24) (Paper IV, radial profiles)
- Related: EMERGE
- Related: CARMA-NRO Orion Survey
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 41,
  "rate": 0.482
 },
 "evidence_ok": true
}
```
