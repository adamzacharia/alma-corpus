# Evolution of the infrared luminosity function and its corresponding dust-obscured star formation rate density out to z ∼ 6

`2026A&A...706A.345K` | Astronomy and Astrophysics 2026 | first author: Koprowski, M. P. | arXiv: 2509.12922 | DOI: 10.1051/0004-6361/202557505

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: Derive the evolution of the infrared luminosity function (including its faint-end slope) out to z~6 and the corresponding dust-obscured star formation rate density, combining stacked Herschel/JCMT faint-end data with the ALMA AS2UDS bright end  
  > "The aim of this study is to add to the existing knowledge by deriving the evolution of the IR LF, including its faint-end slope" (Introduction)
- Target **UKIDSS UDS field (S2CLS SCUBA-2 map, AS2UDS ALMA follow-up)**: coordinates _not stated_; z/distance photometric redshifts from Dudzeviciute_2020; LF bins 1.2<z<5.7  
  > "The original SCUBA-2 map encompasses an area of 0.96 square degrees" (2 Data); distance from magphys photometric redshifts adopted from (cite: Dudzeviciute_2020)  
  > "The original SCUBA-2 map encompasses an area of 0.96 square degrees" (2 Data)
- Target **COSMOS field (optical/near-IR catalogs used for faint-end stacking)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 7 (870 um), AS2UDS  
  > "In summary, all 716 SCUBA-2 sources were observed using ALMA Band 7 during Cycles 1, 3, 4, and 5." (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: maps tapered to 0.5 arcsec for source detection  
  > "All the maps were tapered to 0.5 arcsec for source detection purposes" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: AS2UDS complete at S870 >~ 4 mJy (from 60,000 simulated ALMA observations); sources with sigma_870 > 4.3  
  > "Based on 60,000 simulated ALMA observations, the sample was found to be complete at $S_{870} \gtrsim 4$ mJy." (2 Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Uses the published AS2UDS ALMA catalog and Dudzeviciute et al. 2020 photometry; ALMA reduction not redone here  
  > "A detailed description of the ALMA observations and data reduction and the construction of the catalog can be found in (cite: Stach_2019)." (2 Data)
- Other facility **Herschel (HerMES, PEP; SPIRE and PACS)**: 100-500 um maps for stacking the faint end and SPIRE detections for the bright-end sample  
  > "where *Herschel* maps at 100, 160, 250, 350, and 500 ${\rm \mu m}$ were utilized" (2 Data)
- Other facility **JCMT SCUBA-2 (S2CLS)**: 850 um Rayleigh-Jeans constraint for stacking, and parent sample/completeness/FDR for the bright end  
  > "we also include the data collected as part of the SCUBA-2 Cosmology Legacy Survey (S2CLS; (cite: Geach_2017))." (2 Data)
- External data: Stacked faint-end L_IR values and L_IR-M* relation inputs, plus the optical/near-IR mass-complete catalogs  
  > "The stacking procedure was performed by (cite: Koprowski_2024), and we adopted their results in this work" (3.1.1 Faint end) [from (cite: Koprowski_2024); catalogs (cite: McLeod_2021)]
- External data: AS2UDS photometric redshifts and FIR luminosities  
  > "The associated photometric redshifts and FIR luminosities for all AS2UDS sources were adopted from (cite: Dudzeviciute_2020)." (2 Data) [from (cite: Dudzeviciute_2020)]
- External data: SCUBA-2 source completeness w_i and false detection rate FDR  
  > "while the false detection rate (FDR) and the completeness, $w_i$, are from the original SCUBA-2 survey (cite: Geach_2017)" (3.1.2 Bright end) [from (cite: Geach_2017)]
- External data: AS2UDS ALMA catalog (708 sources) and its completeness  
  > "with the resulting AS2UDS catalog consisting of 708 individual ALMA-identified submillimeter galaxies" (2 Data) [from (cite: Stach_2019)]

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
- uv taper: 0.5 arcsec taper for source detection (AS2UDS)  
  > "All the maps were tapered to 0.5 arcsec for source detection purposes" (2 Data)
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

- ALMA observations, data reduction and catalog construction  
  > "A detailed description of the ALMA observations and data reduction and the construction of the catalog can be found in (cite: Stach_2019)." (2 Data) [from (cite: Stach_2019)]
- Stacking procedure and stacked L_IR values for the faint end  
  > "The stacking procedure was performed by (cite: Koprowski_2024), and we adopted their results in this work" (3.1.1 Faint end) [from (cite: Koprowski_2024)]
- Photometric redshifts, L_IR and dust temperatures (magphys and modified blackbody, beta = 1.8)  
  > "The corresponding dust temperatures were found by (cite: Dudzeviciute_2020) using magphys and the modified blackbody curve" (2 Data) [from (cite: Dudzeviciute_2020)]
- a1 fixed at 0.0 in the Phi_star redshift evolution  
  > "with $a_1$ fixed at 0.0 following (cite: Casey_2018)." (3.1.3 IR LF functional form) [from (cite: Casey_2018)]
- LIR to SFR conversion constant  
  > "To find the star formation rate density, we then followed (cite: Kennicutt_1998):" (3.2 Cosmic star formation history) [from (cite: Kennicutt_1998)]

### Not stated but needed to reproduce (our reading)

- AS2UDS ALMA calibration, imaging parameters and CASA versions (only in Stach et al. 2019)
- Exact AS2UDS catalog flux, redshift, L_IR and SPIRE-detection flags per source (Dudzeviciute et al. 2020 tables)
- Per-source S2CLS completeness w_i and FDR values
- Stacked faint-end L_IR values and number counts are given only in the appendix table; the stacking pipeline itself lives in Koprowski et al. 2024
- Comoving volume V_i definition per source (survey area and redshift limits for 1/Vmax) not spelled out
- Initial guesses/bounds for the nonlinear least-squares fits and the parameter a1 of the Phi_star law is only said to be fixed at 0.0
- Luminosity-bin handling for the 'inf' lower errors in the bright-end table

## Analysis recipe

1. **Adopt stacked faint-end L_IR in stellar-mass and redshift bins**: Stacked optical/near-IR star-forming galaxies in Herschel and JCMT maps using stellar mass as a proxy for L_IR; results adopted from Koprowski et al. 2024  
  > "The stacking procedure was performed by (cite: Koprowski_2024), and we adopted their results in this work" (3.1.1 Faint end)
   - parameter: redshift bin edges [0.45, 0.6, 0.75, 1.0, 1.2, 1.6, 2.2, 3.2, 5.7]  
  > "(with the corresponding redshift bins of \[0.45, 0.6, 0.75, 1.0, 1.2, 1.6, 2.2, 3.2, 5.7\])" (3.1.1 Faint end)
   - assumption: Star-forming sample only; quiescent and starburst galaxies excluded (starbursts covered by the ALMA bright end)  
  > "our assessment of the faint end of the IR luminosity function in effect excludes both quiescent and starburst galaxies" (3.1.1 Faint end)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the L_IR-M* relation**: Fit the Lee et al. 2015 functional form L_IR = L_max/(1+(M*/M0)^-gamma) with gamma = 1 and exponential redshift evolution of the log parameters, to the stacked data  
  > "with the slope, $\gamma$, set to one." (3.1.1 Faint end); "Eq. [\[eq:lir\]](#eq:lir) was fit to the stacked data (Table [\[tab:lir\]](#tab:lir)) using nonlinear least square fitting." (3.1.1 Faint end)
   - assumption: log of free parameters evolve exponentially with redshift  
  > "the most accurate fits to the $L_{\rm IR}$-$M_\ast$ relation are produced when the logarithm of the free parameters of Eq. [\[eq:lir\]](#eq:lir) are assumed to follow an exponential evolution with redshift" (3.1.1 Faint end)
   - fitting: nonlinear least squares  
  > "using nonlinear least square fitting." (3.1.1 Faint end)
   - validation: _not stated_
3. **Compute the faint-end IR LF**: 1/Vmax method applied to z-M* bins below the bending mass M0, with L_IR from the best-fit relation; errors from bootstrapping the mass-complete catalog 1000 times  
  > "a standard $1/V_{\rm max}$ method (cite: Schmidt_1968) was used" (3.1.1 Faint end); "The process was repeated 1000 times, and the uncertainties on the number of sources in each $z$-$M_\ast$ bin were taken to be the standard deviation of the resulting simulated values." (3.1.1 Faint end)
   - parameter: redshift bins [1.2, 1.6, 2.2, 3.2, 5.7]; mass bin width 0.25 dex  
  > "we limited our analysis to the redshift bins of \[1.2, 1.6, 2.2, 3.2, 5.7\]" (3.1.1 Faint end)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute the bright-end IR LF from AS2UDS**: Select ALMA S870 > 4 mJy sources with at least one SPIRE detection; 1/Vmax with FDR and completeness w_i from S2CLS; Monte Carlo resampling of z and L_IR for errors  
  > "We therefore required our sample to be 870${\rm \mu m}$ flux complete ($S_{870}>4$ mJy) and have at least one SPIRE detection." (3.1.2 Bright end); "we conducted Monte Carlo simulations in which redshifts and infrared luminosities were randomly sampled from normal distributions" (3.1.2 Bright end)
   - parameter: L_IR completeness limit log(L_IR/Lsun) = 12.5 at z<1.6, rising to 12.75 and 13.00 at z<3.2 and <5.7  
  > "we arrived at the conservative IR luminosity completeness limit of ${\rm log}(L_{\rm IR}/{\rm L_\odot})=12.5$ at $z<1.6$, respectively rising to 12.75 and 13.00 at $z<3.2$ and $<5.7$" (3.1.2 Bright end)
   - assumption: Dust temperature 37.3 K (upper 68th percentile) with the modified blackbody (beta = 1.8) to set the L_IR limit  
  > "with the 870 ${\rm \mu m}$ flux of 4 mJy and the dust temperature of 37.3 K (upper 68th percentile)" (3.1.2 Bright end)
   - fitting: _not stated_
   - validation: Compared with Dudzeviciute et al. 2020 bright end (similar; differences attributed to binning and completeness corrections)  
  > "We note that our derived form of the bright end of the IR LF closely resembles that presented in (cite: Dudzeviciute_2020)." (3.1.2 Bright end)
5. **Fit the Schechter function and its redshift evolution**: Fit faint+bright data in each redshift bin with a Schechter function with alpha fixed at -0.26 (from the 1.2<=z<1.6 bin); then fit Phi_star and L_star evolution laws  
  > "with $\alpha$ set to $-0.26$ and using the nonlinear least squares analysis with the errors estimated from the corresponding covariance matrix" (3.1.3 IR LF functional form)
   - parameter: alpha fitted in the two lowest bins: -0.26 +/- 0.11 and -0.23 +/- 0.18; -0.26 adopted at all redshifts  
  > "finding $\alpha=-0.26\pm 0.11$ and $-0.23\pm 0.18$, respectively" (3.1.3 IR LF functional form)
   - assumption: alpha constant at all redshifts  
  > "we adopted a more accurate $1.2\leq z < 1.6$ value of $-0.26$ at all redshift bins" (3.1.3 IR LF functional form)
   - fitting: nonlinear least squares, errors from covariance matrix  
  > "using the nonlinear least squares analysis with the errors estimated from the corresponding covariance matrix" (3.1.3 IR LF functional form)
   - validation: Appendix: modified Schechter fits give consistent rho_SFR when alpha and sigma are free  
  > "are in an excellent agreement with the classical Schechter fits adopted in this work" (Modified-Schechter fits)
6. **Integrate the LF to rho_IR and rho_SFR**: Integrate Schechter function over 8.0<log(L_IR/Lsun)<14.0 and convert with Kennicutt (1998) K_IR = 1.73e-10 x 0.63 (Salpeter to Chabrier); errors from 1000 Monte Carlo realizations refitting the Schechter function  
  > "we integrate Equation [\[eq:rhoir\]](#eq:rhoir) between $8.0<{\rm log}(L_{\rm IR}/{\rm L_\odot})<14.0$" (3.2 Cosmic star formation history); "an additional multiplicative factor of 0.63 to convert from a Salpeter to a Chabrier IMF" (3.2 Cosmic star formation history); "in each of the 1000 realizations, the IR luminosities and their corresponding IR LF values listed in Tables" (3.2 Cosmic star formation history)
   - parameter: K_IR = 1.73e-10 Msun/yr/Lsun  
  > "with $\mathcal{K}_{\rm IR}=1.73\times 10^{-10}\,{\rm M_\odot\, year^{-1}\,L_\odot^{-1}}$" (3.2 Cosmic star formation history)
   - assumption: Cosmology H0=70, Om=0.3, OL=0.7; Chabrier IMF  
  > "we assume a flat cold dark matter cosmology with $H_0=70\,{\rm km\, s^{-1}\, Mpc^{-1}}$, $\Omega_m=0.3$, and $\Omega_\Lambda=0.7$" (Introduction)
   - fitting: best-fit Schechter refit in each of 1000 realizations  
  > "In each of the realizations, the best-fit Schechter function was found" (3.2 Cosmic star formation history)
   - validation: Compared with literature rho_SFR (Dunlop 2017, Wang 2019, Magnelli 2024, Liu 2025 agree; Rowan 2016 and Gruppioni 2020 higher)  
  > "It can be seen that the numbers found in this work are in a good agreement with those determined in" (3.2 Cosmic star formation history)

## Software

- **magphys** : Photometric redshifts and IR luminosities of AS2UDS sources (done by Dudzeviciute et al. 2020, adopted here)  
  > "Photometric redshifts as well as IR luminosities were found using the updated magphys spectral energy distribution modeling code" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Faint-end slope alpha, 1.2<=z<1.6 | -0.26 | 0.11 | dimensionless | 5 | finding $\alpha=-0.26\pm 0.11$ and $-0.23\pm 0.18$, respectively |
| Faint-end slope alpha, 1.6<=z<2.2 | -0.23 | 0.18 | dimensionless | 5 | finding $\alpha=-0.26\pm 0.11$ and $-0.23\pm 0.18$, respectively |
| log Phi_star at z=1.44 | -2.98 | 0.10 | log(Mpc^-3 dex^-1) | 5 | $-2.98\pm 0.10$ |
| log L_star at z=1.44 | 11.93 | 0.05 | log(Lsun) | 5 | $11.93\pm 0.05$ |
| log Phi_star at z=4.14 | -4.23 | 0.16 | log(Mpc^-3 dex^-1) | 5 | $-4.23\pm 0.16$ |
| log L_star at z=4.14 | 12.55 | 0.06 | log(Lsun) | 5 | $12.55\pm 0.06$ |
| Phi_star,0 in Phi_star(z) law | 1.22e-3 | 0.20e-3 | Mpc^-3 dex^-1 | 5 | (1.22\pm 0.20) \times 10^{-3} |
| z0 in Phi_star(z) law | 2.24 | 0.23 | dimensionless | 5 | 2.24\pm 0.23 |
| a2 in Phi_star(z) law | 4.95 | 0.73 | dimensionless | 5 | 4.95\pm 0.73 |
| L_star(z) normalisation b1 | 5.26e11 | 0.30e11 | Lsun | 5 | (5.26\pm 0.30) \times 10^{11} |
| L_star(z) exponent b2 | 1.38 | 0.07 | dimensionless | 5 | 1.38 \pm 0.07 |
| log rho_SFR at z=1.44 | -1.04 | 0.07 | log(Msun yr^-1 Mpc^-3) | 6 | $-1.04\pm 0.07$ |
| log rho_SFR at z=1.88 | -0.98 | 0.08 | log(Msun yr^-1 Mpc^-3) | 6 | $-0.98\pm 0.08$ |
| log rho_SFR at z=2.59 | -1.07 | 0.09 | log(Msun yr^-1 Mpc^-3) | 6 | $-1.07\pm 0.09$ |
| log rho_SFR at z=4.14 | -1.71 | 0.13 | log(Msun yr^-1 Mpc^-3) | 6 | $-1.71\pm 0.13$ |
| Modified Schechter sigma (alpha and sigma free) | 0.31 | not stated | dimensionless | 5 | with the best-fit values of $\alpha=-0.26$ and $\sigma=0.31$ |

## Qualitative findings

- The IR LF places the results in a dust-poor early-Universe scenario, with IR sources dominating rho_SFR out to z~4  
  > "placing our results in a dust-poor early Universe regime, where the IR sources seem to dominate the star formation rate density at least out to $z\sim 4$" (3.2 Cosmic star formation history)
- rho_SFR peaks at z~2 and declines to z~6, well below Madau & Dickinson 2014 at high z  
  > "The resulting $\rho_{\rm SFR}$ peaks at $z\simeq 2$ and later declines with redshift from $z\sim 2$ out to $z\sim 6$" (4 Summary)

## Claim tuples

- H: What is the faint-end slope of the IR LF at z>1 when the faint end is constrained by stacking? | E: Stacked mass-complete samples in Herschel/JCMT maps, converted to L_IR via the L_IR-M* relation, 1/Vmax, Schechter fit | R: alpha = -0.26 +/- 0.11 (1.2<=z<1.6) and -0.23 +/- 0.18 (1.6<=z<2.2) | F: Shallow faint-end slope, adopted at all redshifts | **supported**
- H: How do Phi_star and L_star evolve with redshift? | E: Schechter fits at four redshift bins and fitted evolution laws | R: Phi_star declines steeply (~z^-4.95) and L_star rises as z^1.38 | F: Phi_star evolution close to the dust-poor model of Casey et al. 2018; L_star evolution supports downsizing | **supported**
- H: Is the high-redshift IR luminosity density as high as in earlier Herschel and ALMA-selected studies? | E: Compare the new LF and rho_SFR with literature | R: rho_SFR agrees with Dunlop 2017, Wang 2019, Magnelli 2024, Liu 2025, lower than Traina 2024, Fujimoto 2024, Sun 2025, much lower than Rowan 2016 and Gruppioni 2020 | F: Fewer bright IR sources than some prior works; differences attributed to resolution, blending and inhomogeneous samples | **supported**
- H: Does the early Universe follow a dust-rich or dust-poor scenario? | E: Integrate LFs to rho_SFR and compare with the Casey et al. 2018 scenario bounds | R: rho_SFR follows the dust-poor regime | F: IR sources dominate star formation out to z~4 | **supported**

## Reasoning

- Why this data: High-resolution ALMA follow-up allows robust optical counterpart identification for the bright end  
  > "The main advantage of the ALMA data is the high resolution of the observations, which allow for robust optical counterpart identification." (3.1.2 Bright end)
- Why this method: Stacking with stellar mass as an IR luminosity proxy reaches the faint galaxies that direct IR surveys miss  
  > "we adopted an indirect approach, where the faint-end portion of the LF is determined through stacking of the optically selected mass-complete sample of star-forming galaxies" (Introduction)
- Alternative: Modified Schechter function (Saunders 1990) fits tested in an appendix; fixing alpha=-0.2 and sigma=0.5 gave poor fits at the two lowest redshift bins  
  > "It can be seen that fixing $\alpha$ and $\sigma$ at $z\ll1$ values produces very poor fits at two lowest redshift bins" (Modified-Schechter fits)
- How they decided it was enough: _not stated_
- Limitation (authors): The 850 um selection may miss low-dust-mass, high-dust-temperature sources, even after completeness corrections  
  > "the 850 ${\rm \mu m}$ selection of this work will potentially miss low-dust mass, high-dust temperature sources" (3.1.3 IR LF functional form)
- Caveat (inferred, ours): Faint end depends entirely on the L_IR-M* main-sequence relation and the stacking of Koprowski et al. 2024; no independent check of scatter or starbursts at the faint end
- Caveat (inferred, ours): Alpha is measured only at z<2.2 and assumed constant to z~6
- Caveat (inferred, ours): Only four redshift bins have both faint and bright data; the bright end uses a single field (UDS), so cosmic variance is not discussed
- Caveat (inferred, ours): Conservative T_d = 37.3 K completeness limit means the bright-end bins are limited to log L_IR >= 12.5-13.0, leaving a gap between faint-end and bright-end data
- Caveat (inferred, ours): rho_SFR integrated down to log L_IR = 8 relies on extrapolation of the Schechter form

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public AS2UDS catalog tables with S870, z, L_IR and SPIRE flags (in Stach 2019 and Dudzeviciute 2020)
- Missing: S2CLS completeness and FDR per source (Geach 2017)
- Missing: Per-bin comoving volumes for 1/Vmax
- Missing: Stacked faint-end values are given in the appendix table, but the underlying UDS/COSMOS catalogs (McLeod 2021) are needed for the bootstrap errors
- Missing: No code released
- Data volume (inferred): Small (<1 GB): catalogs and tables only; no ALMA visibility processing
- Score (inferred): 3/5, Paper gives full equations, bin edges, Monte Carlo and bootstrap recipe and numeric results, and the faint-end stacks in a table, but the bright-end inputs come from other papers' catalogs and several details (volumes, fit initial values) are not stated.
- Rediscovery candidate: no, The ALMA input is a published catalog from earlier papers and the paper does not state data availability or give per-source inputs, so the full chain cannot be redone from the paper alone.

## Links

- Method: (cite: Koprowski_2024) (Stacking procedure and L_IR-M* relation used for the faint end)
- Method: (cite: Stach_2019) (AS2UDS ALMA observations, reduction and catalog)
- Method: (cite: Dudzeviciute_2020) (Photometric redshifts, L_IR and dust temperatures for AS2UDS sources)
- Method: (cite: Geach_2017) (S2CLS SCUBA-2 survey, completeness and FDR)
- Companion: (cite: Casey_2018) (Dust-rich and dust-poor scenarios used for comparison)
- Related: AS2UDS
- Related: S2CLS
- Related: HerMES
- Related: PEP
- Related: UKIDSS UDS
- Related: COSMOS

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00090.S",
  "2015.1.01528.S",
  "2016.1.00434.S",
  "2017.1.01492.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 48,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
