# Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity

`2019MNRAS.485.2092C` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Coogan, R. T. | arXiv: 1901.06390 | DOI: 10.1093/mnras/stz409

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: How do molecular gas, dust and star formation relate in sub-solar metallicity galaxies at z~2, and how do alpha_CO and G/D depend on metallicity?  
  > "to investigate how molecular gas, dust and star-formation relate in low-metallicity galaxies at the peak epoch of star-formation" (abstract)
- Target **Cl J1449+0856 sub-solar metallicity galaxies (V568, V580, V422, V510, V105)**: coordinates e.g. V568 RA 222.30242 deg, Dec 8.93874 deg  
  > "a sample of sub-solar metallicity galaxies in the cluster Cl J1449+0856 at z=1.99" (Introduction); "V568 | 222.30242 | 8.93874 | 1.987$\pm$0.001" (Table 1); z/distance z=1.99 (cluster); individual z_opt 1.987-2.001  
  > "a sample of sub-solar metallicity galaxies in the cluster Cl J1449+0856 at z=1.99" (Introduction); "V568 | 222.30242 | 8.93874 | 1.987$\pm$0.001" (Table 1); distance from MOIRCS spectroscopic redshifts (V15); cluster from Gobat et al. 2011  
  > "a sample of sub-solar metallicity galaxies in the cluster Cl J1449+0856 at z=1.99" (Introduction); "V568 | 222.30242 | 8.93874 | 1.987$\pm$0.001" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00885.S, 2015.1.01355.S
- bands: ALMA Band 4 (CO[4-3], 2mm), Band 7 (870um); VLA Ka-band (CO[1-0])  
  > "CO[4-3] line and 2mm continuum fluxes were derived from ALMA band 4 data, CO[1-0] line fluxes from VLA Ka-band observations" (Sample Selection and Main Data Sets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams 1.19"x0.96" (CO4-3), 0.70"x0.64" (CO1-0), 1.19"x0.96" (2mm), 1.41"x0.62" (870um)  
  > "beams of 1.19"$\times$0.96" and 1.41"$\times$0.62" for 2mm and 870$\ensuremath{\mu}m$ respectively" (2.2 CO spectroscopy and dust continuum measurements)
- max recoverable scale: _not stated_
- sensitivity: Band 4 core continuum RMS 8 uJy/beam; outskirts 24 uJy/beam; VLA Ka 3 uJy/beam  
  > "a deeper, core observation (continuum root-mean-squared (RMS) noise 8$\micro$Jy/beam), and a shallower pointing (continuum RMS 24$\micro$Jy/beam)" (2.2 CO spectroscopy and dust continuum measurements)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Line: CO 1-0 (not stated)
- Other facility **VLA**: CO[1-0] observations (Ka-band, program 12A-188)  
  > "This paper also makes use of JVLA program 12A-188." (Acknowledgements)
- Other facility **Subaru/MOIRCS**: NIR spectra for metallicities, redshifts, Halpha SFRs  
  > "These observations primarily measured the [NII]6548, [NII]6583, [OIII]5007 and H$\alpha$ emission lines" (2.1 MOIRCS observations)
- External data: Stellar masses and SFRs from SED fitting  
  > "We take stellar masses and SFRs for our sample as derived by (cite: ref:V.Strazzullo2016)" (2.3 SED fitting and star formation rates) [from (cite: ref:V.Strazzullo2016)]
- External data: Literature SFR-L'CO compilation and KS relation  
  > "together with literature data compiled by (cite: ref:M.Sargent2014) and containing MS galaxies at 0$<$z$<$3" (4.1) [from (cite: ref:M.Sargent2014)]
- External data: z=2 MS IR-to-submm SED shape and L_IR/Md=125  
  > "we assume the shape of the z=2 IR-to-sub-mm MS SED from (cite: ref:G.Magdis2012)" (3.3 Dust continuum emission) [from (cite: ref:G.Magdis2012)]

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
- continuum subtraction: 2mm continuum measured in uv-plane after collapsing line-free spectral windows  
  > "2mm continuum fluxes were measured in the uv-plane, after collapsing the data over the line-free spectral windows." (2.2 CO spectroscopy and dust continuum measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA and VLA data and reduction  
  > "we use the ALMA and VLA data described in (cite: ref:R.Coogan2018a)" (Sample Selection and Main Data Sets) [from (cite: ref:R.Coogan2018a)]
- MOIRCS observations, reduction and metallicity procedure  
  > "for which the observations and data reduction are described in detail in V15" (2.1 MOIRCS observations) [from Valentino et al. 2015 (V15)]

### Not stated but needed to reproduce (our reading)

- Calibration details, CASA version, imaging parameters (weighting, cleaning) for ALMA/VLA data (deferred to Coogan 2018)
- Spectral channel widths and line-free channel selection
- Exact SFE prescription parameters and Sargent 2014 equation 5 values
- GILDAS uv_fit settings and neighbour source models
- GALFIT setup for 870um mosaic

## Analysis recipe

1. **Derive metallicities**: N2 diagnostic with PP04 calibration on MOIRCS spectra; stacked via simultaneous Gaussian fit and Monte Carlo resampling  
  > "We derive oxygen abundances with the N2 = log$_{10}$([NII]6583/H$\alpha$) diagnostic and the (cite: ref:M.Pettini2004) calibration" (3.1 Gas phase metallicity measurements)
   - parameter: [NII] ratio fixed to 3.05; 1000 Monte Carlo stacked spectra  
  > "the ratio of the line fluxes between the two [NII] lines must be equal to 3.05" (3.1 Gas phase metallicity measurements)
   - fitting: _not stated_
   - validation: Jackknife; O3N2 comparison  
  > "We verified through a jackknifing analysis that our results are not heavily biased by individual galaxies" (3.1 Gas phase metallicity measurements)
2. **Measure CO line fluxes and stack**: Point-source fits in uv plane at optical positions, visibilities collapsed over Halpha-derived 90% flux width; weighted mean stack  
  > "Line fluxes were measured directly in the uv-visibility plane with the GILDAS task `uv_fit`." (2.2 CO spectroscopy and dust continuum measurements)
   - software: GILDAS
   - parameter: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels  
  > "calculate the stacked line fluxes over the mean FWZP linewidth of the individual galaxies, $\Delta$v=753$\pm$22kms$^{-1}$" (3.2)
   - assumption: Galaxies unresolved (PSF response)  
  > "all spectra were extracted assuming a point spread function (PSF) response" (2.2 CO spectroscopy and dust continuum measurements)
   - fitting: _not stated_
   - validation: MCMC redshift displacement and linewidth resampling show negligible effect  
  > "The effect of this on the output stacked line fluxes is negligible." (3.2)
3. **Measure continuum, dust masses and stack**: 870um fluxes with GALFIT on dirty images; 2mm in uv plane; flux converted to Md with Magdis template; weighted combination; image-plane stack of dust mass maps  
  > "All of these individual dust maps were then stacked in the image plane, by performing a weighted co-add of the images at each pixel position." (3.3 Dust continuum emission)
   - software: GALFIT, GILDAS
   - parameter: <U>=22; L_IR/Md factor 125; 0.15 dex systematic  
  > "our assumed value of $\langle$U$\rangle$=22" (3.3 Dust continuum emission)
   - assumption: Dust temperature as in z=2 MS template  
  > "As we cannot constrain the temperature of the dust with these data" (3.3 Dust continuum emission)
   - fitting: _not stated_
   - validation: CASA, GILDAS and GALFIT fluxes previously verified consistent  
  > "continuum fluxes measured with Common Astronomy Software Applications" (2.2 CO spectroscopy and dust continuum measurements)
4. **Derive gas masses, alpha_CO and G/D limits**: Mmol = SFR/SFE with integrated KS law (Sargent 2014 eq. 5); alpha_CO = Mmol/L'CO; G/D ~ Mmol/Md; log-slope fits against metallicity on normalised scale  
  > "we assume that SFE increases smoothly with distance above the MS" (3.4 Molecular gas masses)
   - parameter: Metallicities normalised to MW-mass z~0 galaxy (Mstar=5.7e10)  
  > "We normalise all metallicities by the metallicity Z$_{M_{\star}(MW, z=0)}$ of a z$\sim$0 Milky-Way-like galaxy" (4.2)
   - assumption: Gas dominated by molecular gas at z=2  
  > "the gas phase in our galaxies at z=2 is dominated by molecular gas" (4.2.2)
   - fitting: Linear fit between literature median and stacked limit  
  > "We perform a linear fit between the median $\alpha_{\rm CO}$ and metallicity of the z$>$1 galaxies" (4.2.1)
   - validation: Jackknife on V580  
  > "We verify through jackknife analysis that this stacked G/D ratio is not strongly driven by the G/D of V580." (4.2.2)

## Software

- **GILDAS** : uv_fit line flux measurements and source modelling  
  > "Line fluxes were measured directly in the uv-visibility plane with the GILDAS[^1] task `uv_fit`." (2.2 CO spectroscopy and dust continuum measurements)
- **GALFIT** : 870um continuum flux extraction and source removal  
  > "Continuum fluxes in the 870$\ensuremath{\mu}m$ map were extracted using the software GALFIT" (2.2 CO spectroscopy and dust continuum measurements)
- **CASA** : cross-check of continuum flux consistency  
  > "continuum fluxes measured with Common Astronomy Software Applications (cite: ref:J.P.McMullin2007), GILDAS and GALFIT" (2.2 CO spectroscopy and dust continuum measurements)
- **FAST** : SED fitting for masses/SFRs (from Strazzullo 2016)  
  > "using Fitting and Assessment of Synthetic Templates (cite: ref:M.Kriek2009) spectral energy distribution (SED) modelling" (2.3 SED fitting and star formation rates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked metallicity | 8.34 | ±0.13 | 12+log(O/H) PP04 N2 | 1 | We find a weighted-average, stacked metallicity value Z=8.34$\pm$0.13. |
| Stacked CO[4-3] flux | <47 | 3 sigma limit | mJy km/s | 2 | We therefore place a 3$\sigma$ upper limit on the stacked CO[4-3] line flux of $<$47mJy kms$^{-1}$ |
| Stacked CO[1-0] flux | <20 | 3 sigma limit | mJy km/s | 2 | In the stacked CO[1-0] spectrum, we find a 3$\sigma$ upper limit of $<$20mJy kms$^{-1}$. |
| Stacked dust mass | <7.4e7 | 3 sigma limit | Msun | 3 | M$_{d}<$7.4$\times$10$^{7}$ M$_{\odot}$ |
| alpha_CO slope vs metallicity | <-0.8 | lower limit | dimensionless | 4 | We find a lower limit on the dependence with metallicity of $Z^{-0.8}$ |
| G/D slope vs metallicity | <-2.2 | lower limit | dimensionless | 4 | We find a lower limit on the slope between our stacked G/D limit and the median (cite: ref:A.Saintonge2013) value of -2.2 |
| Stacked alpha_CO relative to MW | >2.4 | lower limit | factor | 4 | our stacked $\alpha_{\rm CO}$ limit lies a factor $>$2.4 above the MW value $\alpha_{\rm CO}$=4.4 |

## Qualitative findings

- No individual CO or dust detections despite expected detection of most galaxies at solar enrichment.  
  > "we would expect to detect the CO[4-3] and CO[1-0] emission at $\geq$3$\sigma$ from 4/5 of our galaxies" (4)

## Claim tuples

- H: Low-metallicity z=2 galaxies show a CO deficit in low- and high-J CO | E: Stacked CO[1-0] and CO[4-3] limits on SFR-L'CO planes | R: Stack lies >0.5-0.7 dex below expectation | F: Low metallicity suppresses both low- and high-density molecular gas tracers | **supported**
- H: G/D and alpha_CO depend steeply on metallicity at z~2 | E: Limits on alpha_CO and G/D vs normalised metallicity | R: gamma_G/D<-2.2, gamma_alphaCO<-0.8 | F: Consistent with local relations; favours steep/double power-law G/D | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SFR timescale effect or enhanced SFE as origin of CO offset, rejected via Halpha vs UV SFRs and L'CO[5-4] comparison  
  > "The clear offset of the stacked data in both panels of Fig. [4] is therefore unlikely to be driven by timescale effects" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses rely on assumed MS SFE; effect of MS offset cannot be dissected with five galaxies  
  > "the effect of main-sequence offset on ISM scaling relations cannot be dissected with the number of galaxies studied in this paper" (4.2.2)
- Caveat (inferred, ours): Gas masses derived from SFR via assumed SFE, so alpha_CO and G/D limits are model-dependent
- Caveat (inferred, ours): Only upper limits on metallicity for four galaxies
- Caveat (inferred, ours): Dust temperature assumed from template
- Caveat (inferred, ours): Five galaxies in one cluster environment

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduction details in Coogan 2018a
- Missing: Exact SFE/KS parametrisation values
- Missing: MOIRCS spectra
- Data volume (inferred): Tens of GB for ALMA Band 4 and 7 raw data plus VLA data
- Score (inferred): 3/5, ALMA data are archival but processing is deferred to a companion paper and several settings are missing; results are numeric limits.
- Rediscovery candidate: no, Recipe incomplete (calibration inherited, VLA and MOIRCS data needed) and results are mostly upper limits.

## Links

- Method: (cite: ref:F.Valentino2015) (MOIRCS metallicity procedure)
- Companion: (cite: ref:R.Coogan2018a) (ALMA/VLA data description and reduction)
- Related: JVLA program 12A-188

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 38,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
