# Do Circumnuclear Dense Gas Disks Drive Mass Accretion onto Supermassive Black Holes?

`2016ApJ...827...81I` | The Astrophysical Journal 2016 | first author: Izumi, Takuma | arXiv: 1606.04115 | DOI: 10.3847/0004-637X/827/1/81

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is the mass of dense molecular gas (from HCN(1-0)) in ~100 pc circumnuclear disks correlated with the black hole mass accretion rate in Seyfert galaxies, and does the scale of the gas matter?  
  > "We present a positive correlation between the mass of dense molecular gas ($M_{\rm dense}$) of $\sim$ 100 pc scale circumnuclear disks (CNDs) and the black hole mass accretion rate" (abstract)
- Target **NGC 4579**: coordinates phase center (12h37m43.6s, +11d49m02.0s) J2000  
  > "NGC 4579 (luminosity distance = 21.7 Mpc) was observed with ALMA on 2014 April 25 with 37 antennas" (A. Archival data of NGC 4579); z/distance luminosity distance 21.7 Mpc  
  > "NGC 4579 (luminosity distance = 21.7 Mpc) was observed with ALMA on 2014 April 25 with 37 antennas" (A. Archival data of NGC 4579); distance from _not stated_
- Target **NGC 1097**: coordinates _not stated_; z/distance D_L = 18.2 Mpc  
  > "ALMA (NGC 1097[^2]: (cite: 2015A&A...573A.116M)" (2.2 Interferometric data); distance from _not stated_
- Target **NGC 7469**: coordinates _not stated_; z/distance D_L = 70.8 Mpc  
  > "NGC 7469[^4]: T. Izumi et al. in preparation" (2.2 Interferometric data); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00108.S, 2012.1.00165.S, 2012.1.00456.S
- bands: _not stated_
- frequencies and spectral setup: HCN(1-0) in LSB, USB for continuum, ~7.5 GHz total; 488.281 kHz channels binned by 30 to 50 km/s  
  > "Both side bands in total covered $\sim$7.5 GHz width." (A. Archival data of NGC 4579); "we binned 30 channels to achieve 50 km s$^{-1}$ resolution" (A. Archival data of NGC 4579)
- continuum bandwidth: _not stated_
- arrays: NGC 4579: 37 antennas, single pointing  
  > "observed with ALMA on 2014 April 25 with 37 antennas" (A. Archival data of NGC 4579)
- configurations: _not stated_
- baselines: 16.4 m to 558.2 m (NGC 4579)  
  > "Baseline lengths range from 16.4 m to 558.2 m." (A. Archival data of NGC 4579)
- angular resolution: 1.96" x 1.83" (207 x 193 pc), PA -37.75 deg  
  > "The achieved synthesized beam was 1$''$.96 $\times$ 1$''$.83 (207 pc $\times$ 193 pc) with P.A. = $-$37.75$^\circ$." (A. Archival data of NGC 4579)
- max recoverable scale: _not stated_
- sensitivity: channel rms ~0.70 mJy/beam; continuum rms 0.20 mJy/beam  
  > "The rms noise in the channel map was $\sim$0.70 mJy beam$^{-1}$ after the primary beam correction" (A. Archival data of NGC 4579)
- time on source: ~0.2 hr (NGC 4579)  
  > "The total on-source time was $\sim$0.2 hr" (A. Archival data of NGC 4579)
- observing dates: 2014 April 25 (NGC 4579)  
  > "was observed with ALMA on 2014 April 25" (A. Archival data of NGC 4579)
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (88.631 GHz)
- Other facility **PdBI**: HCN(1-0) fluxes for NGC 2273, 3227, 4051, 6951, 3079, 5033  
  > "Plateau de Bure Interferometer = PdBI (NGC 2273, NGC 3227, NGC 4051, and NGC 6951" (2.2 Interferometric data)
- Other facility **NMA**: HCN(1-0) for NGC 1068  
  > "the Nobeyama Millimeter Array = NMA (NGC 1068: (cite: 2008Ap&SS.313..279K))" (2.2 Interferometric data)
- Other facility **Single-dish telescopes (IRAM 30m, SEST, OSO, NRAO 12m, FCRAO, NRO 45m)**: HCN(1-0) fluxes for SD sample  
  > "29$\ensuremath{''}$ (IRAM 30 m), 57$\ensuremath{''}$ (SEST), 44$\ensuremath{''}$ (OSO)" (2.3 Single-dish data)
- External data: HCN(1-0) fluxes for most IT and all SD sample galaxies  
  > "For each AGN from the literature, we used the line flux/luminosity listed in the reference" (2.2 Interferometric data) [from (cite: 2012MNRAS.424.1963S), (cite: 2016MNRAS.458.1375L), (cite: 2008Ap&SS.313..279K), (cite: 2015A&A...573A.116M)]
- External data: HCN-to-dense gas conversion factor X_HCN = 10 Msun (K km/s pc^2)^-1 with 0.30 dex uncertainty  
  > "we adopt $X_{\rm HCN}$ = 10 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ throughout this work" (2.2.2 Mass of dense molecular gas) [from (cite: 2008ApJ...677..262K)]
- External data: Bolometric correction from 2-10 keV luminosity  
  > "The bolometric correction of (cite: 2004MNRAS.351..169M) was applied to the $L_{\rm 2-10 keV}$." (2.2.4 Bolometric luminosity and mass accretion rate) [from (cite: 2004MNRAS.351..169M)]
- External data: Circumnuclear SFR from 11.3 um PAH  
  > "This SFR was estimated with the 11.3 $\mu$m PAH emission ((cite: 2012ApJ...746..168D; 2014ApJ...780...86E))" (Comparison with observations) [from (cite: 2012ApJ...746..168D; 2014ApJ...780...86E)]
- External data: H2 1-0 S(1) disk sizes and kinematics for r_out  
  > "we assume that they are identical to the HWHM of the H$_2$ $1-0$ S(1) emission disks ((cite: 2009ApJ...696..448H))" (Comparison with observations) [from (cite: 2009ApJ...696..448H)]

## Processing

### Calibration

- pipeline or manual: standard manner reduction from raw archive data  
  > "in standard manners. The raw visibility data was extracted from the ALMA archive" (A. Archival data of NGC 4579)
- casa version: CASA 4.2 (4.2.2 in main text)  
  > "The reduction and calibration of the data were conducted with CASA version 4.2" (A. Archival data of NGC 4579)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (flux), J1229+0203 (bandpass), J1239+0730 (phase)  
  > "The bandpass, phase, and absolute flux were calibrated with J1229+0203, J1239+0730, and Ceres, respectively." (A. Archival data of NGC 4579)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The HCN($1-0$) data cube was reconstructed with the CASA task `CLEAN` (gain = 0.1, threshold = 0.5 mJy, weighting = natural)." (A. Archival data of NGC 4579)
- deconvolver: _not stated_
- weighting robust: natural  
  > "gain = 0.1, threshold = 0.5 mJy, weighting = natural" (A. Archival data of NGC 4579)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted in the uv plane  
  > "was subtracted in the $uv$ plane before making the line map" (A. Archival data of NGC 4579)
- line free channels: _not stated_
- primary beam correction: applied to channel map  
  > "The rms noise in the channel map was $\sim$0.70 mJy beam$^{-1}$ after the primary beam correction" (A. Archival data of NGC 4579)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.96" x 1.83", PA -37.75 deg  
  > "The achieved synthesized beam was 1$''$.96 $\times$ 1$''$.83 (207 pc $\times$ 193 pc)" (A. Archival data of NGC 4579)
- final rms: ~0.70 mJy/beam per 50 km/s channel  
  > "The rms noise in the channel map was $\sim$0.70 mJy beam$^{-1}$" (A. Archival data of NGC 4579)

### Inherited from earlier work

- Data analysis of other IT-sample HCN(1-0) data (PdBI, NMA, ALMA NGC 1097 and NGC 7469) deferred to the references  
  > "We guide a reader for the detailed data analysis to those references." (2.2 Interferometric data) [from (cite: 2012MNRAS.424.1963S); (cite: 2016MNRAS.458.1375L); (cite: 2008Ap&SS.313..279K); (cite: 2015A&A...573A.116M); T. Izumi et al. in preparation]
- SN-driven accretion model equation and fiducial parameters  
  > "the model-simulated fiducial values of $\mu_{\rm SN} = 10^{-3}$ $M^{-1}_\odot$ and $\alpha_{\rm SN} \sim 1$ are used" (Comparison with observations) [from (cite: 2008ApJ...681...73K); (cite: 2002ApJ...566L..21W)]
- Regression method linmix_err  
  > "we applied the linear regression method developed by (cite: 2007ApJ...665.1489K)" (3 Regression analysis) [from (cite: 2007ApJ...665.1489K)]

### Not stated but needed to reproduce (our reading)

- Velocity ranges for moment-0 integration for NGC 4579 and NGC 7469
- Line-free channels and continuum selection for NGC 4579 and NGC 7469
- Image size and cell size for NGC 4579 cube
- NGC 7469 ALMA data processing (unpublished)
- linmix_err random seed and convergence checks
- How upper limits were handled in the Spearman correlation
- Exact references for SFR and wind rates per source (numbered refs not resolved)
- Treatment of the 29th SD source count (N=29 vs 32 total)

## Analysis recipe

1. **measure HCN(1-0) line fluxes**: Zeroth-moment maps of continuum-subtracted cubes for NGC 4579 (MIRIAD MOMENT) and NGC 7469 (CASA immoments), no clipping; literature fluxes otherwise  
  > "we measured $S\Delta v$ in a zeroth moment map, which was computed with the CASA task `immoments` without any clipping" (2.2.1 Line luminosity of HCN(1-0))
   - software: CASA, MIRIAD
   - parameter: NGC 4579 nuclear moment-0 = 0.437±0.126 Jy beam^-1 km s^-1  
  > "The moment-0 value at the nucleus (0.437$\pm$0.126 Jy beam$^{-1}$ km s$^{-1}$) was used" (A. Archival data of NGC 4579)
   - fitting: _not stated_
   - validation: RMS measured in line-free areas  
  > "The RMS noises for these maps were measured in areas free of HCN($1-0$) emissions." (2.2.1 Line luminosity of HCN(1-0))
2. **compute L'_HCN and M_dense**: L'_HCN = 3.25e7 S dv nu^-2 D_L^2 (1+z)^-1; M_dense = X_HCN L'_HCN  
  > "we adopt $X_{\rm HCN}$ = 10 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ throughout this work" (2.2.2 Mass of dense molecular gas)
   - assumption: Virialized, non-shadowing clouds; H0=70, Om=0.3, OL=0.7  
  > "Assuming that the HCN($1-0$) emission is emanating from an ensemble of virialized, non-shadowing (in space and velocity) clouds" (2.2.2 Mass of dense molecular gas)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive black hole accretion rate**: L_Bol from L_2-10keV with Marconi+04 correction (O IV for NGC 6951); Mdot_BH = 0.15 (0.1/eta)(L_Bol/1e45)  
  > "where $\eta = 0.1$ is a typical value for mass-to-energy conversion efficiency in the local universe" (2.2.4 Bolometric luminosity and mass accretion rate)
   - parameter: L_Bol uncertainty 0.42 dex  
  > "Adding these in quadrature, 0.42 dex uncertainty was set for $L_{\rm Bol}$." (2.2.4 Bolometric luminosity and mass accretion rate)
   - assumption: eta = 0.1 fixed for all  
  > "Any uncertainty accompanying this relationship was not taken into account." (2.2.4 Bolometric luminosity and mass accretion rate)
   - fitting: _not stated_
   - validation: _not stated_
4. **regression of M_dense vs Mdot_BH**: Bayesian linmix_err with errors in both axes and upper limits; K=1 Gaussian; Spearman via r_correlate  
  > "we instead used $K = 1$, considering the small numbers of samples." (3 Regression analysis)
   - software: linmix_err (IDL), r_correlate (IDL)
   - parameter: 3e4 MCMC draws, Metropolis-Hastings; posterior mode and 68% range  
  > "We used $3 \times 10^4$ random draws returned by the MCMC sampler with the Metropolis-Hastings algorithm." (3 Regression analysis)
   - fitting: log zeta = alpha + beta log xi + eps, Gaussian intrinsic scatter, mixture-of-Gaussians prior on x  
  > "models the prior distribution of the independent variable using a weighted mixture of $K$-Gaussians" (3 Regression analysis)
   - validation: IT vs SD comparison; KS test of AGN property distributions  
  > "returned marginal (or even high) $p$-values, which were (0.33, 0.75, 0.75) for ($L_{\rm Bol}$, $M_{\rm BH}$, $\lambda_{\rm Edd}$)" (2.4 Comments on the AGN sample)
5. **compare with SN-driven accretion model**: Reduced Kawakatu & Wada equation for uniform disk; r_in,eff = max[r_X, r_Q]; Mdot_acc compared to Mdot_BH and Mdot_BH+Mdot_wind for four sources  
  > "Using these two radii, we regard the *effective* innermost radius as $r_{\rm in,eff} = {\rm max}[r_{\rm X}, r_{\rm Q}]$." (Comparison with observations)
   - parameter: n_H2 = 1e6 cm^-3, log(Hx/nH) = -27.5, c_s ~1 km/s, Toomre Q=1  
  > "A gas volume density of $n_{\rm H_2} = 10^6$ cm$^{-3}$" (Comparison with observations)
   - assumption: Dense gas uniformly distributed in CND; r_out = HWHM of H2 1-0 S(1) disk; uncertainty set by M_dense/M_BH  
  > "we simply assume that the dense gas is uniformly distributed within a CND" (Comparison with observations)
   - fitting: _not stated_
   - validation: Compared with Mdot_BH and nuclear mass flow  
  > "both NGC 7469 and NGC 4051 show good agreement of $\dot{M}_{\rm CND} \sim \dot{M}_{\rm nuclear}$" (Other components of the mass budget$-$gaseous outflow)

## Software

- **CASA** 4.2.2 (main text); 4.2 (appendix): Reduction, CLEAN imaging, immoments for NGC 4579 and NGC 7469  
  > "analyzed further with the Common Astronomy Software Applications (CASA ver. 4.2.2" (2.2 Interferometric data)
- **MIRIAD** : MOMENT map and spectrum of NGC 4579 cube  
  > "We further analyzed this line cube with `MIRIAD`" (A. Archival data of NGC 4579)
- **linmix_err** : Bayesian linear regression (IDL Astronomy Library)  
  > "The procedure for the analysis is available from the IDL Astronomy User’s Library [^8] as `linmix_err`." (3 Regression analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_dense-Mdot_BH slope beta, IT sample | 1.41 | +0.70/-0.56 | dimensionless | 4 | / IT-sample / 220 pc / 10 / $-13.45^{+3.90}_{-5.25}$ / $1.41^{+0.70}_{-0.56}$ / $0.52^{+0.34}_{-0.29}$ / $>$0.77 / 0.033 / |
| Intrinsic scatter, IT sample | 0.52 | +0.34/-0.29 | dex | 4 | the IT sample showed a smaller scatter ($\sigma_{\rm int} = 0.52^{+0.34}_{-0.29}$ dex) |
| Intrinsic scatter, SD sample | 1.19 | +0.18/-0.21 | dex | 4 | than the SD sample ($\sigma_{\rm int} = 1.19^{+0.18}_{-0.21}$ and $\rho = 0.35^{+0.18}_{-0.24}$) |
| Null-hypothesis probability, IT sample | 0.033 | not stated | dimensionless | 4 | the canonical null-hypothesis probability returned by `r_correlate` (0.033) |
| log M_dense NGC 4579 | 6.93 | 0.33 | log Msun | 2 | / NGC 4579        / 6.93$\pm$0.33         / -3.56$\pm$0.42           / |
| log Mdot_acc NGC 7469 | -1.20 | 0.30 | log Msun/yr | 5 | / NGC 7469 / 30.8 / 2.2 / 0.84 / 1.19/260 / 2 / 6.0$\times$10$^{-9}$ / -1.20$\pm$0.30 / -1.22 / 5 / |

## Qualitative findings

- CND-scale dense gas correlates with Mdot_BH more tightly than galaxy-scale gas  
  > "the $M_{\rm dense}-\dot{M}_{\rm BH}$ correlation was tighter for CND-scale gas than for the gas on kpc or larger scales" (abstract)

## Claim tuples

- H: Dense gas mass in CNDs correlates with black hole accretion rate | E: Linmix regression of M_dense (HCN) vs Mdot_BH for 10 interferometric Seyferts | R: Positive slope 1.41, rho>0.77, p=0.033 | F: More dense gas in CND corresponds to a more active AGN, equivalent to the SFR-Mdot_BH correlation | **supported**
- H: The correlation depends on spatial scale | E: Compared IT (220 pc) and SD (5.5 kpc) samples | R: Scatter 0.52 vs 1.19 dex; rho >0.77 vs 0.35 | F: CND-scale gas matters for fueling, kpc-scale does not | **partially**
- H: SN-driven turbulent accretion explains CND accretion | E: Computed Mdot_acc for four sources and compared to Mdot_BH and Mdot_BH+Mdot_wind | R: Mdot_BH is ~10% or less of Mdot_acc in NGC 1097 and NGC 4051; Mdot_acc ~ Mdot_nuclear in NGC 4051 and NGC 7469 | F: Tentatively consistent with mass flow balance | **partially**

## Reasoning

- Why this data: HCN(1-0) traces dense gas, the site of star formation, with less foreground contamination than CO  
  > "the HCN($1-0$) emission emanates selectively from dense molecular gas where stars are born" (2.1 Line selection)
- Why this method: linmix_err handles errors on both axes, upper limits and intrinsic scatter  
  > "This is a Bayesian-based algorithm that can handle errors on both axes, upper limits on the dependent variable, and the intrinsic scatter." (3 Regression analysis)
- Alternative: Mass loss from evolved stars noted as an alternative not tested  
  > "Note that there are other scenarios that also support a direct AGN$-$starburst connection, such as *mass loss from evolved stars*" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Small, inhomogeneous samples; tentative results; fixed eta and uncertainties not fully included  
  > "our results are tentative due to the small sample size, and are based on simplified assumptions" (Other components of the mass budget$-$gaseous outflow)
- Limitation (authors): Most CNDs unresolved so Sigma_dense not measured  
  > "most of the CNDs are not resolved spatially at the HCN($1-0$) emission line, so we cannot measure $\Sigma_{\rm dense}$ directly" (Comparison with observations)
- Caveat (inferred, ours): Sample of 10 with heterogeneous apertures; aperture correlates with luminosity so scale comparison is confounded
- Caveat (inferred, ours): Fixed eta=0.1 and X_HCN over five orders of Eddington ratio
- Caveat (inferred, ours): Spearman significance for IT sample is marginal (p=0.033) and 4-object model test is anecdotal
- Caveat (inferred, ours): Distance confounds in luminosity-luminosity relations not addressed

## Reproducibility

- Data public (paper): NGC 4579 raw data obtained from the ALMA archive  
  > "The raw visibility data was extracted from the ALMA archive" (A. Archival data of NGC 4579)
- Products in archive: _not stated_
- Missing: Moment-0 integration velocity ranges
- Missing: NGC 7469 ALMA analysis (in preparation)
- Missing: Numeric table references for SFR and winds
- Missing: Full literature HCN fluxes must be re-taken from cited papers
- Data volume (inferred): <10 GB for the ALMA parts (two small archival datasets); the rest is tabular
- Score (inferred): 5/5, Regression and tables are fully given and reproducible from tabulated values, but ALMA processing is minimal and the data are mostly literature compilations.
- Rediscovery candidate: no, ALMA role is minor and key inputs come from literature tables; the regression could be redone but not the ALMA analysis.

## Links

- Method: (cite: 2007ApJ...665.1489K) (linmix_err Bayesian regression)
- Method: (cite: 2008ApJ...681...73K) (SN-driven accretion model)
- Companion: (cite: 2015A&A...573A.116M) (ALMA HCN data for NGC 1097)
- Companion: (cite: 2012ApJ...746..168D) (SFR-Mdot_BH correlation)
- Related: Revised Shapley-Ames catalog

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 58,
  "rate": 0.652
 },
 "evidence_ok": true
}
```
