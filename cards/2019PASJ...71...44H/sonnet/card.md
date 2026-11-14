# Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud

`2019PASJ...71...44H` | Publications of the Astronomical Society of Japan 2019 | first author: Harada, Ryohei | arXiv: 1901.08250 | DOI: 10.1093/pasj/psz011

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: What are the distribution and basic physical properties of the natal gas around high-mass YSOs in isolated environments in the LMC?  
  > "The aim of this study is to characterize the distribution and basic properties of the natal gas associated with high-mass young stellar objects (YSOs) in isolated environments in the Large Magellanic Cloud (LMC)." (abstract)
- Target **10 isolated high-mass YSOs in the LMC (Targets 1-10)**: coordinates _not stated_; z/distance ~50 kpc  
  > "The Large Magellanic Cloud (LMC) is located close to us ($\sim$$\;$50$\>$kpc; (cite: Schaefer08); (cite: de Grijs14))" (Introduction); distance from Schaefer08; de Grijs14  
  > "The Large Magellanic Cloud (LMC) is located close to us ($\sim$$\;$50$\>$kpc; (cite: Schaefer08); (cite: de Grijs14))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00287.S
- bands: Band 3 and Band 6, Cycle 2  
  > "We carried out ALMA Cycle 2 Band 3 (86–116 GHz) and Band 6 (211–275 GHz) observations toward 10 isolated YSOs" (ALMA observations)
- frequencies and spectral setup: 61 kHz resolution, 1920 channels (0.17 km/s Band 3, 0.08 km/s Band 6); H40alpha at 976 kHz  
  > "with a frequency resolution of 61$\;$kHz, corresponding to velocity resolutions of $\sim\;$0.17$\;$km$\,$s$^{-1}$ for Band 3 and $\sim\;$0.08$\;$km$\,$s$^{-1}$ for Band 6, both with 1920 channels." (ALMA observations)
- continuum bandwidth: 1875 MHz  
  > "We also observed the continuum emission with the wider bandwidth of 1875$\;$MHz." (ALMA observations)
- arrays: 12 m array, ACA 7 m and TP for Band 6; 12 m for Band 3  
  > "For the Band 6 data, we combined the 12$\>$m array, 7$\>$m array, and TP array data to recover the extended emission" (ALMA observations)
- configurations: _not stated_
- baselines: Band 6: 13-392 m; Band 3: 13-247 m; ACA 8-36 m  
  > "the projected baseline length of the 12$\>$m array ranges from 13$\>$m to 392$\>$m." (ALMA observations)
- angular resolution: _not stated_
- max recoverable scale: ~26 arcsec (~6.2 pc) for Band 3  
  > "the maximum recoverable scale of $\sim$$\;$$\timeform{26"}$, corresponding to $\sim$$\;$6.2$\>$pc" (ALMA observations)
- sensitivity: measured at common velocity resolution of 0.2 km/s  
  > "The sensitivities are measured at a common velocity resolution of 0.2 km$\,$s$^{-1}$." (ALMA observations)
- time on source: _not stated_
- observing dates: Band 6 June 2014 and September 2015; Band 3 December 2014  
  > "The ALMA Band 6 observations were carried out in June 2014 and September 2015." (ALMA observations)
- pi or archival as stated: _not stated_
- Line: 13CO J=1-0 (not stated)
- Line: 12CO J=2-1 (not stated)
- Line: CS J=2-1 (not stated)
- Line: H40alpha RRL (not stated)
- Other facility **Mopra**: CO pointed and mapping observations used for sample selection  
  > "A further set of single-pointing CO observations with the Mopra Telescope" (Source selection and observations)
- Other facility **NANTEN**: 12CO(1-0) survey for selection  
  > "NANTEN survey (half-power beam width, HPBW $\sim\;$$\timeform{2'.6}$, (cite: Fukui08))" (Source selection and observations)
- Other facility **Spitzer/Herschel**: YSO catalog and SED photometry  
  > "the spectral energy distribution (SED) fitter for the available photometry data including *Spitzer* and *Herschel* fluxes" (Source selection and observations)
- External data: HI column densities at YSO positions  
  > "Col.(3): H$\;$i column densities at the YSO positions (cite: Kim03)." (Source selection and observations) [from Kim03]
- External data: Dust temperatures from graybody fits  
  > "which is consistent with the dust temperatures derived by (cite: Seale14)" (Excitation analyses using multiple transitions) [from Seale14]

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
- array combination: 12 m + 7 m + TP combined for Band 6 (except Target 9 TP)  
  > "except for Target 9, toward which we have no TP array observations due to the failed observations." (ALMA observations)
- smoothing: Spectra measured at 1.9x1.1 arcsec (12CO, 13CO 2-1) and 3.2x2.4 arcsec (13CO 1-0, CS)  
  > "The spectra are measured at the angular resolution of $\timeform{1".9}$$\;$$\times$$\;$$\timeform{1".1}$ for $^{12}$CO, $^{13}$CO ($J$ = 2–1)" (LTE mass)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Abundance ratios [12CO/H2]=1.6e-5 and [12CO/13CO]=50  
  > "We used the same abundance ratios of \[$^{12}$CO/H$_2$\] and \[$^{12}$CO/$^{13}$CO\] as (cite: Mizuno10) for their N159 study in the LMC" (LTE mass) [from Mizuno10]
- Virial mass procedure  
  > "using the procedure described by (cite: Fujii14)" (Virial mass) [from Fujii14]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging pipeline
- tclean weighting, robust, cell and image size
- line-free channels and continuum subtraction
- exact beam sizes per target (in table not reproduced)
- LVG code and grid parameters
- target coordinates
- noise threshold values (sigma) used for the clump masks

## Analysis recipe

1. **LTE clump mass**: 13CO(1-0) optical depth and column density under LTE, converted to H2 mass within 3 sigma 13CO(2-1) region  
  > "we defined a clump as the region where the integrated intensity of $^{13}$CO ($J$ = 2–1) emission is stronger than the 3$\sigma$ level" (LTE mass)
   - parameter: Tex = 20 K  
  > "The excitation temperatures, $T_{\mathrm{ex}}$, was assumed to be 20$\;$K" (LTE mass)
   - assumption: distance 50 kpc; 12CO/H2=1.6e-5; 12CO/13CO=50  
  > "$D$ is the distance to the object of 50$\>$kpc" (LTE mass)
   - fitting: _not stated_
   - validation: _not stated_
2. **Virial mass and ratio**: Mvir = 190 dV^2 R_deconv, virial ratio = Mvir/MLTE  
  > "assuming the clumps are spherical with density profiles of $\rho$ $\propto$ $r^{-1}$" (Virial mass)
   - fitting: single Gaussian fit to 13CO(1-0) spectrum for linewidth  
  > "Linewidth (FWHM) derived by a single Gaussian fitting to $^{13}$CO ($J$ = 1–0) spectrum at the intensity peak." (LTE mass)
   - validation: _not stated_
3. **LVG excitation analysis**: LVG analysis of CO lines for Tkin and n(H2)  
  > "we performed a large velocity gradient analysis (LVG analysis; (cite: Goldreich74); (cite: Scoville74)) for our CO line observations." (Excitation analyses using multiple transitions)
   - parameter: dv/dr = 2 km/s/pc  
  > "we adopt $dv/dr$ = 2 from the typical size and linewidth of the clumps" (Excitation analyses using multiple transitions)
   - fitting: _not stated_
   - validation: compared with dust temperatures from Seale14 and virial densities  
  > "These values are roughly consistent with the densities derived from the excitation analysis" (Photodissociation of CO)
4. **Star formation efficiency**: SFE = Mecl/(Mecl+Mcloud), with Mecl from the mmax-Mecl relation  
  > "SFE = \frac{M_{\mathrm{ecl}}}{M_{\mathrm{ecl}} + M_{\mathrm{cloud}}}" (Star Formation Efficiency)
   - assumption: Weidner13 mmax-Mecl relation  
  > "the masses of the star cluster associated with the isolated high-mass YSOs range from 110 to 310$\;$$M_{\odot}$" (Star Formation Efficiency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SED fitter with YSO model grid (Robitaille)** : YSO masses and luminosities  
  > "we used the YSO model grid of (, ) and the spectral energy distribution (SED) fitter" (Source selection and observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clump LTE mass range | 2.8e2 to 6.5e3 | not stated | Msun | 1 | The masses of the clouds range from 2.8$\;$$\times$$\;$10$^2$ to 6.5$\;$$\times$$\;$10$^3$$\;$$M_{\odot}$ |
| Virial ratio range | 0.6 to 2.7 | not stated | dimensionless | 2 | The virial ratio of the clumps associated with the isolated high-mass YSOs range from 0.6 to 2.7 |
| H2 density range (LVG) | 5.4-8.8e3 | not stated | cm^-3 | 3 | The density is in the range of 5.4–8.8$\;$$\times$$\;$10$^3$$\;$cm$^{-3}$ |
| Kinetic temperature range | 19-30 | not stated | K | 3 | the kinetic temperatures are 19–30 K |
| Star formation efficiency range | 4 to 43 | not stated | % | 4 | they range from 4 to 43% |

## Qualitative findings

- Target 8 shows a blue-shifted outflow wing and is likely the youngest source  
  > "there is a clear sign of blue-shifted velocity wing due to a molecular outflow" (Velocity structure of associated molecular clouds)

## Claim tuples

- H: Isolated high-mass YSOs form in compact natal clouds | E: ALMA CO mapping of 10 YSOs | R: All targets have compact clouds of 300-6000 Msun, radii 0.5-2 pc | F: High-mass YSOs form in compact low-mass clumps | **supported**
- H: Star formation is efficient in these clumps | E: SFE from mmax-Mecl cluster mass and LTE gas mass | R: SFE 4-43% | F: Efficient star formation, as an upper limit | **supported**
- H: Cloud interaction triggers star formation | E: Velocity channel maps | R: Targets 5 and 6 show filaments with different velocities | F: Possible interaction for two targets only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Linewidth enhancement from outflow momentum rejected as insufficient; pre-existing turbulence favored  
  > "there is a high possibility that the high-mass YSOs were formed in the turbulent clump region prior to the star formation" (Enhancement of velocity width toward YSOs)
- How they decided it was enough: _not stated_
- Limitation (authors): SFE is an upper limit; CO-dark gas possible  
  > "We note that this SFE is an upper limit because a part of the natal clouds may have been already dissipated away" (Star Formation Efficiency)
- Caveat (inferred, ours): Fixed Tex=20 K and LMC abundance ratios drive the masses
- Caveat (inferred, ours): Cluster mass inferred from a relation, not measured
- Caveat (inferred, ours): Small sample of 10

## Reproducibility

- Data public (paper): ALMA project 2013.1.00287.S cited  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2013.1.00287.S." (Summary)
- Products in archive: _not stated_
- Missing: CASA imaging parameters
- Missing: LVG code details
- Missing: target coordinates and tables
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Data public and the equations are given, but processing settings and the LVG code are not.
- Rediscovery candidate: no, Imaging and LVG details are missing.

## Links

- Method: Fujii14 (virial mass procedure)
- Method: Weidner13 (mmax-Mecl relation)
- Companion: Stephens17 (HST observations of Target 9)
- Related: SAGE
- Related: NANTEN
- Related: MAGMA

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
