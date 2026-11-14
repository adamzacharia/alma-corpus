# ALMaQUEST. IV. The ALMA-MaNGA QUEnching and STar Formation (ALMaQUEST) Survey

`2020ApJ...903..145L` | The Astrophysical Journal 2020 | first author: Lin, Lihwai | arXiv: 2010.01751 | DOI: 10.3847/1538-4357/abba3a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies
- Question: How does sSFR depend on molecular gas fraction versus star formation efficiency, globally and at kpc scales, in MaNGA galaxies spanning starburst, main-sequence and green valley  
  > "The aim of the ALMaQUEST survey is to investigate the dependence of star formation activity on the cold molecular gas content at kpc scales in nearby galaxies." (abstract)
- Target **46 ALMaQUEST galaxies (MaNGA DR15)**: coordinates RA/Dec per galaxy in Table 1 (e.g. 7815-12705: 318.990448, 9.543076 deg)  
  > "| 7815-12705 | 318.990448 | 9.543076 | 0.029550 | 0.0591 |" (Table 1); z/distance MaNGA redshifts 0.018-0.132 (Table 1)  
  > "| 7815-12705 | 318.990448 | 9.543076 | 0.029550 | 0.0591 |" (Table 1); distance from MaNGA redshift  
  > "| 7815-12705 | 318.990448 | 9.543076 | 0.029550 | 0.0591 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S, 2018.1.00541.S
- bands: Band 3  
  > "were carried out with ALMA during Cycle 3, 5, and 6 using the Band 3 receiver." (2.3 ALMA Observations)
- frequencies and spectral setup: one high-resolution SPW (~10 km/s) on CO(1-0); 1-3 low-resolution SPWs (~90 km/s) for continuum  
  > "Our spectral setup includes one high-resolution spectral window ($\sim$ 10 ${\rm km~s^{-1}}$ ) targeting $^{12}$CO(1-0), and one to three low-resolution spectral window(s)" (2.3 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2  
  > "The observations were taken in the C43-2 configuration (synthesized beam FWHM $\sim$ 2.5$\ensuremath{''}$), thus matching the MaNGA resolution." (2.3 ALMA Observations)
- baselines: _not stated_
- angular resolution: native 1.6''-2.8''; final 2.5''x2.5''  
  > "The resultant native effective beamsize for each target ranges from 1.6$\ensuremath{''}$ to 2.8$\ensuremath{''}$." (2.3 ALMA Observations)
- max recoverable scale: ~23'' (~14 kpc)  
  > "The largest structure that we expect to be sensitive to is about 23$\ensuremath{''}$ ($\sim$14 kpc)." (2.3 ALMA Observations)
- sensitivity: rms ~0.2-2 mJy/beam per 11 km/s channel  
  > "The final cubes have channel widths of 11 km s$^{-1}$ and rms noise ($\sigma_\mathrm{rms}$) of $\sim$ 0.2 – 2 mJy beam$^{-1}$." (2.3 ALMA Observations)
- time on source: 0.2 to 2.5 hours  
  > "On-target integration time varies from 0.2 to 2.5 hours" (2.3 ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 1-0 (115.271204 GHz)
- Other facility **MaNGA (SDSS 2.5m)**: optical IFS, Sigma_*, Halpha SFR, metallicity via PIPE3D DR15  
  > "Measurements of the $\Sigma_{*}$  and emission-line fluxes are taken from the public PIPE3D data products" (2.2 MaNGA Data)
- Other facility **GBT HI-MaNGA / ALFALFA**: single-dish HI masses for 33 galaxies  
  > "Among the 46 ALMaQUEST galaxies, 26 and 7 galaxies are included in the $\rm H\textsc{i}$-MaNGA and ALFALFA samples, respectively." (2.4 GBT HI Observations)
- External data: xCOLD GASS comparison sample (offset 0.26 dex Chabrier to Salpeter)  
  > "An offset of 0.26 dex has been added to the xCOLD GASS SFR and $\rm~M_{*}$ measurements to account for the conversion from the Chabrier to the Salpeter IMF." (3.1) [from (cite: sai17)]
- External data: PIPE3D global SFR and M* value-added catalog  
  > "The global measurements of SFR and $\rm~M_{*}$ are taken from the PIPE3D (cite: san16a; san16b) value-added catalog (cite: san18)" (2.1 Sample Selection) [from (cite: san16a; san16b; san18)]
- External data: HI-MaNGA DR2 and ALFALFA catalog HI data  
  > "we use the $\rm H\textsc{i}$  data from both the second data release of $\rm H\textsc{i}$-MaNGA (D. Stark et al. in prep.) and the ALFALFA catalog (cite: hay18)." (2.4 GBT HI Observations) [from (cite: mas19; hay18)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were calibrated using the ALMA data reduction software CASA version 4.5 or 5.4 (cite: mcm07) and standard ALMA pipeline" (2.3 ALMA Observations)
- casa version: CASA 4.5 or 5.4 (4.5 for 7977-12705, 7977-3704, 7977-9101)  
  > "7977-12705, 7977-3704, and 7977-9101 were calibrated with CASA version 4.5 because they were observed in an earlier cycle." (footnote 3)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: typically 5-10% in Band 3  
  > "The systematic flux uncertainty associated with the calibration is typically 5 – 10% in Band 3." (2.3 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "The task CLEAN was employed to clean the continuum-subtracted data down to 1$\sigma$ and produce spectral line data cubes" (2.3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of 0.5." (2.3 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.5''  
  > "adopted a user-specified pixel size (0.5$\ensuremath{''}$) and restoring beamsize (2.5$\ensuremath{''}$ $\times$ 2.5$\ensuremath{''}$)" (2.3 ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in visibility domain  
  > "Continuum is subtracted from the data in the visibility domain." (2.3 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.5'' x 2.5'' restoring beam  
  > "adopted a user-specified pixel size (0.5$\ensuremath{''}$) and restoring beamsize (2.5$\ensuremath{''}$ $\times$ 2.5$\ensuremath{''}$)" (2.3 ALMA Observations)
- final rms: ~0.2-2 mJy/beam  
  > "rms noise ($\sigma_\mathrm{rms}$) of $\sim$ 0.2 – 2 mJy beam$^{-1}$" (2.3 ALMA Observations)

### Inherited from earlier work

- HI-MaNGA observing and reduction details  
  > "Complete details can be found in (cite: mas19) which we briefly summarize here." (2.4 GBT HI Observations) [from (cite: mas19)]
- Starburst selection criterion  
  > "show elevated SFR relative to the control sample within 0.5 $R_{e}$  by at least 50 percent (cite: ell20a)" (2.1 Sample Selection) [from (cite: ell20a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum spectral windows used for continuum subtraction
- Velocity ranges chosen by hand for moment-0 maps per galaxy
- tclean/CLEAN image size, masking, and deconvolver
- Exact conversion of CO flux to L'CO and treatment of line brightness (R21 not needed but redshift/distance used)
- Per-galaxy CASA version assignment beyond three listed
- Spaxel S/N cuts for CO in resolved analysis
- Distances used for HI masses

## Analysis recipe

1. **Image CO cubes and moment maps**: Clean continuum-subtracted data with Briggs weighting, re-image to 2.5'' beam and 0.5'' pixels; moments with IMMOMENTS  
  > "The 0th – 2nd moment maps (0th: integrated intensity, 1st: intensity-weighted velocity field, and 2nd: intensity-weighted velocity dispersion) were constructed by using the task IMMOMENTS in CASA." (2.3 ALMA Observations)
   - software: CASA
   - parameter: 4 sigma clipping for velocity and dispersion maps; no clipping for moment 0  
  > "Data in this velocity range were also used to generate velocity field and dispersion maps, with a 4$\sigma$ clipping applied to avoid noise contamination." (2.3 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 mass and global quantities**: Sum CO flux, SFR and M* within 1.5 Re (star-forming [SII] BPT spaxels for SFR) and MaNGA bundle; compute sSFR, SFE, fH2  
  > "These integrated quantities are estimated in two ways: 1) By summing up the measured values over the area enclosed by 1.5 $R_{e}$  and 2) by summing over the areas within the MaNGA bundles." (2.5 Global Measurements)
   - assumption: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; Salpeter IMF  
  > "adopting a constant conversion factor ($\alpha_{\mathrm{CO}}$) of 4.35 $\rm M_{\odot}$(K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: bol13)" (2.5 Global Measurements)
   - fitting: _not stated_
   - validation: Repeated with metallicity-dependent alpha_CO (Sun+20; Narayanan+12) and alternative SFR spaxel selections  
  > "the varying $\alpha_{\mathrm{CO}}$ does not affect any trends in the global results presented in this section." (3.1)
3. **Correlation of sSFR with SFE, fH2, HI ratios**: Kendall tau correlation analysis  
  > "The Kendall correlation analysis for the ALMaQUEST sample shows that the correlation between sSFR and SFE ($\tau$ = 0.67) is slightly stronger" (3.1)
   - fitting: _not stated_
   - validation: Excluded lowest-SFE point; tau changes 0.67 to 0.66  
  > "We find that the $\tau$ value only slightly decreases from 0.67 to 0.66 in this case" (3.1)
4. **Spaxel-level distributions**: Histograms of sSFR, fH2, SFE on star-forming spaxels per galaxy  
  > "we plot the histograms of sSFR, $f_{\rm H_{2}}$  and SFE computed on a spaxel-by-spaxel basis for the star-forming spaxels of 46 ALMaQUEST galaxies" (3.3)
   - fitting: _not stated_
   - validation: Repeated with varying alpha_CO; offsets <0.14 dex  
  > "While there is a systematic offset ($<$ 0.14 dex) in the resulted SFE and $f_{\rm H_{2}}$" (3.3)

## Software

- **CASA** 4.5 or 5.4: calibration, CLEAN imaging, IMMOMENTS  
  > "CASA version 4.5 or 5.4 (cite: mcm07)" (2.3 ALMA Observations)
- **PIPE3D** : MaNGA stellar mass, SFR, emission-line measurements  
  > "Measurements of the $\Sigma_{*}$  and emission-line fluxes are taken from the public PIPE3D data products" (2.2 MaNGA Data)
- **GBTIDL** : HI-MaNGA data reduction  
  > "are reduced (including RFI flagging, smoothing, and baseline removal) using GBTIDL." (2.4 GBT HI Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Kendall tau sSFR vs SFE | 0.67 | not stated | dimensionless | 3 | the correlation between sSFR and SFE ($\tau$ = 0.67) |
| Kendall tau sSFR vs fH2 | 0.54 | not stated | dimensionless | 3 | that between sSFR and $f_{\rm H_{2}}$ ($\tau$ = 0.54) |
| Kendall tau, all spaxels case | 0.56 | not stated | dimensionless | 3 | A moderate correlation ($\tau$ = 0.56) with high significance |
| Kendall tau, [NII] BPT: sSFR-SFE / sSFR-fH2 | 0.78 / 0.49 | not stated | dimensionless | 3 | a stronger correlation strength ($\tau$ = 0.78) is found in the sSFR vs. SFE relation, with respect to the sSFR vs. $f_{\rm H_{2}}$ relation ($\tau$ = 0.49) |
| Max difference in global H2 mass with varying alpha_CO | 0.27 dex (mean ~0.05 and ~0.14 dex for methods 1 and 2) | not stated | dex | 2 | can be as large as 0.27 dex with an average value of $\sim 0.05$ and $\sim 0.14$ dex in method 1 and method 2, respectively |
| HI detections among 33 galaxies with HI data | 18 | not stated | galaxies | 0 | of which 18 are detected in $\rm H\textsc{i}$  with S/N \> 5 |

## Qualitative findings

- Within galaxies SFE and fH2 vary by 1-2 dex; Halpha does not always trace CO  
  > "all of these quantities show a large spread (typically spanning 1-2 orders of magnitude within a galaxy)" (3.3)

## Claim tuples

- H: Is sSFR driven by SFE or by molecular gas fraction? | E: Kendall correlations of aperture-matched sSFR with SFE and fH2 for 46 galaxies | R: tau=0.67 (SFE) vs 0.54 (fH2) | F: Both contribute; SFE slightly stronger | **supported**
- H: Does atomic gas drive sSFR more than molecular gas? | E: Correlations of sSFR with MHI/M* and MH2/MHI for 33 galaxies | R: weaker than SFE or fH2 | F: sSFR more linked to molecular gas, with caution due to small sample | **partially**
- H: Are SFE and fH2 uniform within galaxies? | E: Spaxel-level histograms and maps | R: 1-2 dex spread within galaxies, robust to alpha_CO | F: Resolved observations are essential | **supported**

## Reasoning

- Why this data: Integration time set to give CO S/N>3 for >50% of spaxels with Halpha S/N>3, based on pilot  
  > "is set to have a S/N (CO) greater than 3 for more than 50% of spaxels with S/N (H$\alpha$) \> 3." (2.3 ALMA Observations)
- Why this method: _not stated_
- Alternative: Metallicity- and intensity-dependent alpha_CO tested; trends unchanged  
  > "we also consider two types of varying $\alpha_{\mathrm{CO}}$" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Small HI sample limits conclusions  
  > "our results should be taken with caution given that the current ALMaQUEST $\rm H\textsc{i}$  sample size is still limited." (3.2)
- Caveat (inferred, ours): Constant alpha_CO may bias SFE/fH2 especially in starbursts
- Caveat (inferred, ours): No error treatment on Kendall tau
- Caveat (inferred, ours): CO-detected selection biases low-sSFR sample
- Caveat (inferred, ours): Aperture area mismatch with xCOLD GASS

## Reproducibility

- Data public (paper): Survey webpage given; ALMA programs listed  
  > "Key information and characteristics of the ALMaQUEST survey can be found in the ALMaQUEST webpage: http://arc.phys.uvic.ca/$\sim$almaquest/." (2.1 Sample Selection)
- Products in archive: _not stated_
- Missing: Moment-0 velocity ranges
- Missing: Line-free channels
- Missing: Imaging masks and image size
- Data volume (inferred): ~100-300 GB for four programs (46 Band 3 single-pointing datasets)
- Score (inferred): 6/5, Data public and tables give numbers, but imaging details sparse.
- Rediscovery candidate: yes, Public ALMA and MaNGA data; Tables 2-3 and Kendall tau values give numeric answer keys.

## Links

- Method: (cite: lin17) (Pilot study defining the setup)
- Method: (cite: mas19) (HI-MaNGA details)
- Companion: (cite: ell20a) (Starburst central SFE)
- Companion: (cite: ell20b) (rSFMS scatter)
- Companion: (cite: lin19b) (Resolved scaling relations)
- Related: MaNGA
- Related: xCOLD GASS
- Related: EDGE-CALIFA
- Related: PHANGS
- Related: HI-MaNGA
- Related: ALFALFA

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 44,
  "rate": 0.629
 },
 "evidence_ok": true
}
```
