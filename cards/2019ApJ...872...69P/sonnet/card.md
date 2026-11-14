# AGN Torus Detectability at Submillimeter Wavelengths: What to Expect from ALMA Continuum Data

`2019ApJ...872...69P` | The Astrophysical Journal 2019 | first author: Pasetto, Alice | arXiv: 1901.02280 | DOI: 10.3847/1538-4357/aafa20

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can the dusty AGN torus be detected at sub-mm wavelengths with ALMA continuum data, given contamination by synchrotron jet emission?  
  > "It is the aim of this paper to study the detectability of extended emission associated to AGN dusty structure at sub-mm wavelengths using ALMA." (1 Introduction)
- Target **NGC 1052**: coordinates 02:41:04.798 –08:15:20.75 (J2000)  
  > "NGC 1052 | 02:41:04.798  –08:15:20.75 | 20.6" (Table 1 (targets)); z/distance 20.6 Mpc; z=0.005  
  > "NGC 1052 | 02:41:04.798  –08:15:20.75 | 20.6" (Table 1 (targets)); distance from NED redshift-independent average distance  
  > "NGC 1052 | 02:41:04.798  –08:15:20.75 | 20.6" (Table 1 (targets))
- Target **NGC 1068**: coordinates 02:42:40.711 –00:00:47.81 (J2000)  
  > "NGC 1068 | 02:42:40.711  –00:00:47.81 | 10.6" (Table 1 (targets)); z/distance 10.6 Mpc; z=0.002  
  > "NGC 1068 | 02:42:40.711  –00:00:47.81 | 10.6" (Table 1 (targets)); distance from NED redshift-independent  
  > "NGC 1068 | 02:42:40.711  –00:00:47.81 | 10.6" (Table 1 (targets))
- Target **NGC 3516**: coordinates 11:06:47.490 +72:34:06.88 (J2000)  
  > "NGC 3516 | 11:06:47.490  +72:34:06.88 | 51.5" (Table 1 (targets)); z/distance 51.5 Mpc; z=0.012  
  > "NGC 3516 | 11:06:47.490  +72:34:06.88 | 51.5" (Table 1 (targets)); distance from NED redshift-independent  
  > "NGC 3516 | 11:06:47.490  +72:34:06.88 | 51.5" (Table 1 (targets))
- Target **I Zw 1**: coordinates 00:53:34.940 +12:41:36.20 (J2000)  
  > "I Zw 1   | 00:53:34.940  +12:41:36.20 | 240.7" (Table 1 (targets)); z/distance 240.7 Mpc; z=0.059  
  > "I Zw 1   | 00:53:34.940  +12:41:36.20 | 240.7" (Table 1 (targets)); distance from z from (cite: Ho2009)  
  > "I Zw 1   | 00:53:34.940  +12:41:36.20 | 240.7" (Table 1 (targets))

## Data provenance

- ALMA projects: 2012.1.00034.S, 2013.1.00055.S, 2013.1.00221.S, 2013.1.01151.S, 2013.1.01225.S, 2015.1.00591.S, 2015.1.00989.S, 2016.1.00232.S
- bands: Archival ALMA continuum from ~93 to 694 GHz (Bands 3-9); theory at 100, 353, 666 GHz  
  > "the monochromatic luminosities at 100 GHz (3000 $\rm{\mu m}$, ALMA band 3), 353 GHz (850 $\rm{\mu m}$, ALMA band 7), and 666 GHz (450 $\rm{\mu m}$, ALMA band 9) for the sub-mm wavelengths" (Torus detection with ALMA through theoretical predictions)
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
- pi or archival as stated: Archival ALMA products  
  > "In the sub-mm window, we collected data from the ALMA archive." (3.2.2 Radio cm and sub-mm data)
- Other facility **JVLA**: A-configuration cm radio continuum from archive/literature  
  > "We obtained the A-configuration radio data from the JVLA data archive or literature." (3.2.2 Radio cm and sub-mm data)
- Other facility **Spitzer/IRS (CASSIS)**: mid-IR nuclear spectra  
  > "we used the high and low-resolution *Spitzer*/IRS spectral data from the CASSIS[^3] catalog" (3.2.1 Mid-IR data)
- Other facility **Gemini T-ReCS**: N and Q band data for NGC 1068  
  > "we used the N and Q bands data from the Thermal-Region Camera Spectrograph" (3.2.1 Mid-IR data)
- Other facility **CARMA**: 100 GHz flux for NGC 3516  
  > "we used the Combined Array for Research in Millimeter-wave Astronomy (CARMA) data published by (cite: Behar2018) for the source NGC 3516" (3.2.2 Radio cm and sub-mm data)
- Other facility **JCMT**: 374 and 666 GHz fluxes for I Zw1  
  > "the James Clerk Maxwell Telescope (JCMT) data published by (cite: Hughes1993) for the source I Zw1" (3.2.2 Radio cm and sub-mm data)
- External data: Mid-IR to X-ray relation for 12 micron nuclear luminosity  
  > "The most updated version of this relation is presented by (cite: Asmus15) using a sample of 152 nearby AGN" (2.1 Torus contribution) [from (cite: Asmus15)]
- External data: Clumpy torus SED library  
  > "We then compute the expected $\rm{F_{\nu}^{\lambda}/F_{12\mu m}}$ using the SEDs of clumpy torus model produced by (cite: Nenkova08B)." (2.1 Torus contribution) [from (cite: Nenkova08B)]
- External data: Radio fundamental plane relation  
  > "(cite: Bonchi13) measured a fundamental plane for the largest AGN-only sample for which radio, X-ray and K-band luminosity information exists." (2.2 Jet contribution) [from (cite: Bonchi13)]
- External data: Smooth torus SED library used for mid-IR fits  
  > "Thus, we used the smooth dusty model reported by (cite: Fritz06) hereinafter" (3.3.1 Mid-infrared spectral fit) [from (cite: Fritz06)]
- External data: CARMA 100 GHz flux of NGC 3516  
  > "(8) from (cite: Behar2018)" (Table 3 note) [from (cite: Behar2018)]
- External data: JCMT fluxes of I Zw1  
  > "(11) from (cite: Hughes1993)" (Table 3 note) [from (cite: Hughes1993)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.2 (for JVLA data)  
  > "version 5.1.2" (3.2.2 Radio cm and sub-mm data)
- pipeline version: _not stated_
- archive products used as is: ALMA archive continuum Stokes I maps used  
  > "ALMA continuum flux densities have been collected analyzing the products continuum Stokes I maps available for each projects at the ALMA archive web page" (3.2.2 Radio cm and sub-mm data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean for JVLA; ALMA archive maps used  
  > "From the calibrated data, Stokes I images were made for all the targets at each band running the CASA *clean* task." (3.2.2 Radio cm and sub-mm data)
- deconvolver: _not stated_
- weighting robust: JVLA: robust 0 or uniform weighting  
  > "we performed the cleaning using *robust 0* or *uniform* weighting" (3.2.2 Radio cm and sub-mm data)
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

- NGC 1068 694 GHz ALMA flux is taken from earlier paper (S1 component)  
  > "(\*) flux density from (cite: Garcia-Burillo16): at the resolution 0.07$^{^{\prime\prime}\;}$ $\times$ 0.05$^{^{\prime\prime}\;}$" (Table 3 note) [from (cite: Garcia-Burillo16)]
- I Zw1 252 GHz flux from earlier paper  
  > "(10) from (cite: Imanishi2016b)" (Table 3 note) [from (cite: Imanishi2016b)]

### Not stated but needed to reproduce (our reading)

- ALMA flux extraction details (Gaussian fit region, per-project calibration versions, archive product versions)
- Torus parameter grid sampling and distributions used for the Monte Carlo histograms
- xspec model-table conversion details (deferred to Esparza-Arredondo et al. in prep.)
- Exact ALMA exposure-time-calculator inputs (configuration, PWV, bandwidth)
- Line-free/continuum channel selection for archive products

## Analysis recipe

1. **Predict torus flux ratio at sub-mm**: Scale 12um flux from X-ray via Asmus15 relation; use Nenkova08B clumpy SEDs for F_sub-mm/F_12um, linear extrapolation beyond 1000 um  
  > "We linearly extrapolate the SEDs above 1000$\rm{\mu m}$ to estimate the expected flux at 3000$\rm{\mu m}$ (i.e. band 3 at 100 GHz)." (2.1 Torus contribution)
   - fitting: _not stated_
   - validation: _not stated_
2. **Predict jet flux ratio at sub-mm**: Extrapolate Bonchi13 fundamental plane to 100, 353, 666 GHz with alpha in [-0.5,-0.7], L_X 1e42-1e46, MBH 1e6-1e9  
  > "spectral indexes for local AGN (cite: Condon2002; Sadler2014) of $\alpha$=\[–0.5,–0.7\], X-ray luminosity of L$\rm{_{[2-10keV]}}$=\[10$^{42}$,10$^{46}$\] erg s$^{-1}$" (2.2 Jet contribution)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare to ALMA sensitivity**: Compare predicted torus/jet fluxes for F12um=150 mJy and 10 Jy against ETC rms for 1 and 10 h  
  > "according to the exposure time calculator, considering one hour (on-source) observing time using the most sensitive ALMA configuration and the full bandwidth" (2.3 Detectability)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit mid-IR spectra**: Fit Spitzer/T-ReCS spectra with Fritz06 smooth torus tables in xspec  
  > "We converted these SED libraries to multi-parametric models within the spectral fitting tool xspec." (3.3.1)
   - software: xspec, HEASOFT
   - fitting: chi-square; errors from xspec error tool at 99% confidence  
  > "the errors were calculated using the $\mathrm{error}$ tool[^10] in xspec with a 99% confidence" (3.3.1)
   - validation: Compared five dust models; Fritz06 chosen with Delta chi2/dof<0.1  
  > "providing an equally good fit **($\rm{\Delta \chi^2 / dof < 0.1}$)**" (3.3.1)
5. **Fit cm radio spectra**: Power law, single SSA or two SSA components fit to cm data; best by lowest reduced chi2  
  > "For each source, we selected the best model according to the lowest statistical reduced chi-squared test ($\rm{\chi^{2}}$/*dof*) value." (3.3.2)
   - software: python curvefit
   - fitting: least squares with alpha_thick=2.5  
  > "$\rm{\alpha_{thick}}$=2.5 and $\rm{\alpha_{thin}}$, respectively" (3.3.2)
   - validation: _not stated_
6. **Extrapolate torus+jet to sub-mm and compare with ALMA fluxes**: Sum extrapolated fits and compare with ALMA/CARMA/JCMT data  
  > "Both fits have been extrapolated in the sub-mm window and the sum of the two components are shown as black straight lines." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.2: JVLA calibration and clean imaging  
  > "JVLA archival data have been calibrated using the data-reduction package CASA" (3.2.2)
- **xspec** : Fitting mid-IR spectra with torus model tables  
  > "xspec is a command-driven, interactive, spectral-fitting program within the HEASOFT[^7] software." (3.3.1)
- **HEASOFT flx2xsp** : Convert Spitzer spectra to xspec PHA format  
  > "We also converted the mid-IR *Spitzer* spectrum into xspec format using flx2xsp task within HEASOFT." (3.3.1)
- **RedCan** : Processing T-ReCS data  
  > "T-ReCS data were processed using the pipeline RedCan" (3.2.1)
- **BayesClumpy** : Earlier I Zw1 SED fit by other authors  
  > "fitting the SED to Clumpy models using BayesClumpy" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median torus log(F/F_X) at 666 GHz | -4.6 | 10-90%: -5.84 to -3.31 | dimensionless | 1 | 666GHz/450$\rm{\mu m}$  / $-$4.6 \[$-$5.84, $-$3.31\] |
| Median jet log(F/F_X) at 666 GHz | -6.06 | 10-90%: -7.51 to -4.61 | dimensionless | 2 | 666GHz/450$\rm{\mu m}$  / $-$6.06 \[$-$7.51, $-$4.61\] |
| Median torus contribution fraction at 666 GHz | 96.2 | range 5.5-99.9 | % | 3 | 96.2 \[5.5, 99.9\] |
| ALMA 1h rms at 100/353/666 GHz | 12 / 85 / 260 | not stated | uJy | 3 | are $\sim$12, $\sim$85, and $\sim$260 $\mu$Jy at 100 GHz/3000 $\rm{\mu m}$, 353 GHz/850 $\rm{\mu m}$, and 666 GHz/450 $\rm{\mu m}$, respectively |
| NGC 1068 radio PL spectral index | -1.07 | 0.01 | dimensionless | 5 | NGC 1068 / PL / $\rm{-1.07\pm0.01}$ |
| I Zw1 radio PL spectral index | -0.65 | 0.04 | dimensionless | 5 | I Zw1 / PL / $\rm{-0.65\pm0.04}$ |
| I Zw1 torus outer radius | ~8.1 | not stated | pc | 4 | $R_{out}$    / $\sim$0.4               / $\sim$2.3    / $\sim$2.9              / $\sim$8.1 |

## Qualitative findings

- NGC 1052 sub-mm emission is jet dominated; for other sources neither torus nor jet explains the sub-mm flux; I Zw1 is the most promising torus candidate but unresolvable  
  > "The radio jet of NGC 1052 dominates over the torus in the sub-mm range. In all the other cases, neither the torus or the jet can explain the sub-mm emission." (5 Summary)

## Claim tuples

- H: Which tori are detectable at sub-mm with ALMA | E: Scaling-relation + clumpy model predictions vs ALMA rms | R: Highest torus contribution at 666 GHz; 1 mJy torus detectable in 1h at 353 GHz or 10h at 666 GHz | F: Only bright, large, dense tori are detectable, with possible jet contamination | **supported**
- H: Observed sub-mm fluxes of four AGN are explained by torus plus jet | E: Combine mid-IR smooth-model and radio fits and extrapolate | R: Only NGC 1052 explained (jet); others under-predicted by factors ~3, 8, 100 | F: I Zw1 is the best torus candidate; SED analysis with radio data is needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Smooth Fritz06 model chosen as simplest baseline not needing a stellar component  
  > "is the simplest baseline model that satisfactory describes the data" (3.3.1)
- Alternative: Five dusty models tested; others need extra stellar component  
  > "For the others, a stellar component[^9] is needed to account for the short wavelengths (below 10$\rm{\mu m}$)." (3.3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Fundamental plane is a rough jet estimator; large ALMA beams may overestimate fluxes  
  > "the fundamental plane is a rough estimator of the sub-mm contribution of the jet" (4 Discussion)
- Caveat (inferred, ours): ALMA fluxes taken from heterogeneous archival maps with beams up to several arcsec, mixing in extended emission
- Caveat (inferred, ours): Non-simultaneous, variable radio/sub-mm data
- Caveat (inferred, ours): Fits for NGC 1068 require unlinked parameters, so extrapolation is unreliable
- Caveat (inferred, ours): No MC details for theory histograms

## Reproducibility

- Data public (paper): ALMA and JVLA archival data  
  > "We obtained the A-configuration radio data from the JVLA data archive or literature." (3.2.2)
- Products in archive: _not stated_
- Missing: Model parameter sampling for theory histograms
- Missing: ALMA flux extraction procedure details
- Missing: Companion paper on xspec table conversion (in prep.)
- Data volume (inferred): ~tens of GB (8 archival ALMA projects, using pipeline continuum products)
- Score (inferred): 3/5, Data are public and the recipe is mostly described, but several details are missing and ALMA is only a flux source.
- Rediscovery candidate: no, ALMA role is minor and key steps (flux extraction, model sampling) are underspecified.

## Links

- Method: (cite: Nenkova08B) (Clumpy torus SEDs)
- Method: (cite: Fritz06) (Smooth torus models)
- Method: (cite: Bonchi13) (Fundamental plane)
- Companion: (cite: Garcia-Burillo16) (NGC 1068 Band 9 torus claim)
- Companion: (cite: Izumi17) (NGC 1097 sub-mm jet variability)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 51,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
