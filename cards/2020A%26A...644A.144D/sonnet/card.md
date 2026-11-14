# In pursuit of giants. I. The evolution of the dust-to-stellar mass ratio in distant dusty galaxies

`2020A&A...644A.144D` | Astronomy and Astrophysics 2020 | first author: Donevski, D. | arXiv: 2008.09995 | DOI: 10.1051/0004-6361/202038405

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: How does the dust-to-stellar mass ratio of ALMA-detected dusty star-forming galaxies evolve with redshift, stellar mass, sSFR and position relative to the main sequence, and how do models of dusty galaxy formation compare?  
  > "How the $M_{\rm dust}$/$M_{\rm \star}$ evolves with cosmic time and position of the galaxy with respect to the main-sequence?" (Introduction)
- Target **300 ALMA-detected DSFGs in the COSMOS field (HELP catalogue)**: coordinates see Table 3 (RA/Dec in degrees)  
  > "The full redshift distribution extends over a wide range ($0.5<z<5.25$)" (Data and sample selection); z/distance 0.5<z<5.25; 73 spectroscopic, remainder photometric  
  > "The full redshift distribution extends over a wide range ($0.5<z<5.25$)" (Data and sample selection); distance from public spec-z; photo-z from Duncan et al. 2018 Bayesian combination  
  > "The full redshift distribution extends over a wide range ($0.5<z<5.25$)" (Data and sample selection)

## Data provenance

- ALMA projects: 2011.0.00064.S, 2016.1.00735.S
- bands: Band 6 (1.1mm, 121 sources) or Band 7 (870 um, 207 sources)  
  > "either in Band 6 (1.1mm, 121 source) or Band 7 (870 $\mu$m, 207 sources)" (Data and sample selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel (HELP, XID+)**: deblended MIPS/PACS/SPIRE FIR fluxes  
  > "the MIPS ($24\mu$m), PACS (100, 160$\mu$m) and SPIRE fluxes (250, 350 and 500 $\mu$m) are assigned to each source with use of probabilistic de-blending method `XID+`" (Data and sample selection)
- Other facility **Subaru, HSC, VISTA, IRAC**: optical-NIR photometry  
  > "The optical to NIR data come from Subaru Suprime-Cam (6 bands), HSC ($Y$-band), VISTA ($J, H, K_{s}$ bands) and IRAC (4 bands)." (Data and sample selection)
- External data: ALMA fluxes from the A3COSMOS database  
  > "We adopt fluxes available within the ALMA archive ($\mathrm{A^{3}COSMOS}$, see (cite: liu19a) for more details)." (Data and sample selection) [from Liu et al. 2019a (cite: liu19a)]
- External data: ALMA dust continuum sizes from uv-visibility exponential-disk fits  
  > "we adopt ALMA dust continuum sizes obtained through homogeneous $\mathit{uv}$-visibility size analyses with the exponential disk model ($n = 1$" (6 The role of compact dusty star-formation) [from (cite: fujimoto17)]
- Simulation/model as data: SIMBA simulation, Pantoni et al. 2019 analytic model, and Bethermin et al. 2017 phenomenological model compared with data  
  > "Cosmological galaxy formation simulation with self-consistent dust growth and feedback (SIMBA, (cite: simba)); **(II)** Analytical model of (cite: pantoni19)" (5.1 Models)

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

- SED-fitting setup and mock-catalogue systematics test follow earlier work  
  > "then follow the approach implemented by (cite: malek19) to ensure that our SED fitting procedure does not introduce significant systematics" (3.2 Statistical properties) [from (cite: malek19)]
- Rest-frame IR size measurement procedure  
  > "see (cite: fujimoto17) for the detailed description of the procedure" (6 The role of compact dusty star-formation) [from (cite: fujimoto17)]
- Starburst threshold Delta_MS>=4  
  > "We assume the galaxy is a starburst if $\Delta_{\rm MS}\geq4$ (e.g. (cite: elbaz17))" (3.2 Statistical properties) [from (cite: elbaz17)]

### Not stated but needed to reproduce (our reading)

- No ALMA calibration or imaging details; the paper relies on A3COSMOS fluxes
- Exact A3COSMOS catalogue version and cross-match radius
- CIGALE version
- Which of the listed ALMA projects were used for sizes
- Exact scaling-relation implementations for gas mass and metallicity

## Analysis recipe

1. **Assemble sample**: Cross-match HELP deblended multiwavelength catalogue with A3COSMOS ALMA detections; require S/N>=3 in 5 mid-IR to sub-mm bands and S/N>=5 in 10 optical-NIR bands  
  > "we require source detections with $\rm S/N\geq3$ in at least 5 photometric bands in the mid-IR-to-FIR/sub-mm range" (Data and sample selection)
   - software: XID+
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting**: CIGALE with BC03 stellar population (delayed plus burst SFH), Charlot & Fall attenuation, Draine et al. 2014 dust emission, and Fritz AGN templates  
  > "We choose to perform the modelling of galaxies' IR SEDs with the physically motivated, dust emission library of (cite: draine14)" (3 Panchromatic SED modelling)
   - software: CIGALE
   - parameter: Chabrier IMF, solar metallicity 0.02, attenuation slopes -0.7, gamma=0.02, alpha=2.0  
  > "| slope BC | -0.7 |  | Power law slope of BC attenuation |" (Table 1)
   - fitting: Likelihood-weighted mean and standard deviation of the PDF  
  > "the output value is the likelihood-weighted mean of the PDF (and consequently, the associated error is likelihood-weighted standard deviation)" (3.1 Tools: CIGALE)
   - validation: Mock catalogues; reduced chi2<10; >75% of sources within +-0.1 offset  
  > "for each physical parameter we find that more than $75\%$ of sources lie within the mean offset of $\pm0.1$" (Appendix A)
3. **Classify MS vs starburst**: Delta_MS relative to the Speagle et al. 2014 main sequence; SB if >=4; sources with f_AGN>20% removed  
  > "We infer that our sample contains 242 MS DSFGs ($81\%$ of the total) and 58 SB DSFGs ($19\%$ of the total)." (3.2 Statistical properties)
   - fitting: _not stated_
   - validation: Tested the Schreiber 2015 MS; no significant change  
  > "find that the choice of adopted MS does not significantly impact the statistics of our MS and SB DSFGs" (Footnote 3)
4. **Model Mdust/Mstar evolution**: Mdust/Mstar ∝ (Mgas/Mstar) x Zgas using gas scaling relations (Scoville17, Tacconi18, Liu19b) and MZR/BMR (Hunt16, Genzel15, Bethermin15)  
  > "The equation unveils that the evolution of $M_{\rm dust}/M_{\star}$ depends on the evolution of molecular gas mass ratio and gas-phase metallicity" (4.4)
   - assumption: Gas is mostly molecular; dust-to-gas ratio scales with metallicity  
  > "This is a fair assumption if one considers that rising ISM pressure to high-$z$'s would induce negligible contribution of atomic hydrogen" (4.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with models**: Apply the same Mstar and sSFR cuts and MS/SB split to SIMBA, P19 and B17 catalogues  
  > "we impose the same range of modelled $M_{\star}$ and $\rm sSFR$ as in our observations" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** : SED fitting for Mstar, Mdust, LIR, SFR, f_AGN  
  > "As a main tool we adopt the newest release of Code Investigating GALaxy Emission" (3.1 Tools: CIGALE)
- **XID+** : deblending Herschel/Spitzer fluxes  
  > "The code `XID+` de-blends confusion limited maps with use of positional and redshift information" (Data and sample selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Mdust/Mstar, MS DSFGs | 0.006 | +0.004/-0.003 | dimensionless | 2 | $M_{\rm dust}/M_{\star}=0.006^{+0.004}_{-0.003}$ for MS DSFGs |
| Median Mdust/Mstar, SB DSFGs | 0.017 | +0.010/-0.006 | dimensionless | 2 | $M_{\rm dust}/M_{\star}=0.017^{+0.010}_{-0.006}$ for SB DSFGs |
| Median Mdust | 7.33e8 | +5.2e8/-3.4e8 | Msun | 2 | we find the median of $M_{\rm dust}=7.33^{5.2}_{-3.4}\times10^{8}M_{\odot}$ |
| Median gas fraction, MS and SB | 0.44 (MS), 0.75 (SB) | 0.09 each | dimensionless | 4 | $f_{\rm gas}=0.44\pm 0.09$ and $f_{\rm gas}=0.75\pm 0.09$ for MS and SB DSFGs, respectively |
| Sample sizes MS / SB | 242 / 58 | not stated | sources | 3 | 242 MS DSFGs ($81\%$ of the total) and 58 SB DSFGs |

## Qualitative findings

- Mdust/Mstar rises to z~2 then flattens; anti-correlated with Mstar up to z~5  
  > "In both galaxy populations $M_{\rm dust}$/$M_{\rm \star}$ increases until $z\sim2$ followed by a roughly flat trend towards higher redshifts" (abstract)

## Claim tuples

- H: Mdust/Mstar differs between MS and SB DSFGs and evolves with z | E: SED fitting of 300 ALMA-detected COSMOS DSFGs, binned by redshift | R: SB have 3-4x higher Mdust/Mstar; both rise to z~2 then flatten | F: Mdust/Mstar separates MS and SB galaxies across redshift | **supported**
- H: Cosmological simulation SIMBA reproduces observed Mdust/Mstar | E: Compare SIMBA, P19 and B17 predictions with data | R: SIMBA matches MS but underpredicts SB by factor 3-6; B17 and P19 agree | F: SIMBA needs faster dust growth/higher metallicity in starbursts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thick dust model gives 2-3x lower Mdust in highest-mass bin; DL14 optically thin masses kept for consistency  
  > "For the sake of consistency, we thus keep our DL14-based $M_{\rm dust}$ for the rest of the paper." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample incomplete at fixed stellar mass because sources were preselected for ALMA follow-up  
  > "We note that our sample is incomplete at fixed $M_{\star}$, since most of sources were preselected for the purpose of ALMA follow-ups." (5.2)
- Caveat (inferred, ours): Mostly photometric redshifts; heterogeneous ALMA selection
- Caveat (inferred, ours): Gas masses and metallicities come from scaling relations, not measured
- Caveat (inferred, ours): Mdust depends on optically thin DL14 assumption

## Reproducibility

- Data public (paper): Public ALMA archive and HELP catalogues; source table given  
  > "the wealth of multi-wavelength data complemented to several hundreds of galaxies that exist in public ALMA archive" (Data and sample selection)
- Products in archive: _not stated_
- Missing: ALMA data processing not described
- Missing: CIGALE version and complete configuration
- Missing: Model catalogue versions
- Data volume (inferred): Low (catalogue-level fluxes); raw ALMA data not needed
- Score (inferred): 3/5, Catalogue and SED parameters are largely specified and a source table is published, but ALMA reduction, CIGALE version and gas/metallicity implementation details are missing.
- Rediscovery candidate: no, Results depend on A3COSMOS/HELP catalogues and multiple external models, with incomplete recipe details.

## Links

- Method: Boquien et al. 2019 (cite: cigale19) (CIGALE code)
- Method: Liu et al. 2019a (cite: liu19a) (A3COSMOS ALMA photometry)
- Method: Małek et al. 2018 (cite: malek19) (SED fitting setup and HELP)
- Companion: Donevski et al., Paper II, in prep. (Mechanisms producing high dust/gas densities)
- Related: HELP
- Related: A3COSMOS
- Related: COSMOS

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00097.S",
  "2011.0.00539.S",
  "2011.0.00742.S",
  "2012.1.00076.S",
  "2012.1.00523.S",
  "2012.1.00536.S",
  "2012.1.00919.S",
  "2012.1.00952.S",
  "2012.1.00978.S",
  "2013.1.00884.S",
  "2013.1.00914.S",
  "2015.1.00568.S",
  "2015.1.00664.S",
  "2015.1.00853.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.00928.S",
  "2015.1.01074.S",
  "2015.A.00026.S",
  "2016.1.00478.S",
  "2016.1.00624.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00539.S",
  "2011.0.00742.S",
  "2012.1.00076.S",
  "2012.1.00323.S",
  "2012.1.00523.S",
  "2012.1.00536.S",
  "2012.1.00919.S",
  "2012.1.00952.S",
  "2012.1.00978.S",
  "2013.1.00914.S",
  "2015.1.00137.S",
  "2015.1.00568.S",
  "2015.1.00664.S",
  "2015.1.00704.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.00928.S",
  "2015.1.01074.S",
  "2015.1.01590.S",
  "2015.A.00026.S",
  "2016.1.00478.S",
  "2016.1.00624.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 29,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
