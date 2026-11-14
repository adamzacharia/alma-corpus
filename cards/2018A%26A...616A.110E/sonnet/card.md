# Starbursts in and out of the star-formation main sequence

`2018A&A...616A.110E` | Astronomy and Astrophysics 2018 | first author: Elbaz, D. | arXiv: 1711.10047 | DOI: 10.1051/0004-6361/201732370

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How compact is dusty star formation in z~2 massive galaxies, and do starbursts exist within (as well as above) the star-formation main sequence?  
  > "can there be starbursts "hidden" within the MS?" (Introduction)
- Target **GS1-GS8 (GOODS-South Herschel ULIRGs)**: coordinates Table 1 (CANDELS coordinates, 3h32m, -27d)  
  > "It consists of eight $z$$\sim$2 ULIRGs (ultra-luminous infrared galaxies, L$_{\rm IR}$$\geq$10$^{12}$ L$_{\odot}$)" (Sample selection); z/distance z=1.619-3.240 (Table 2)  
  > "It consists of eight $z$$\sim$2 ULIRGs (ultra-luminous infrared galaxies, L$_{\rm IR}$$\geq$10$^{12}$ L$_{\odot}$)" (Sample selection); distance from spectroscopic for GS4-7, otherwise photometric (EAzY)  
  > "It consists of eight $z$$\sim$2 ULIRGs (ultra-luminous infrared galaxies, L$_{\rm IR}$$\geq$10$^{12}$ L$_{\odot}$)" (Sample selection)
- Target **UDF1-UDF16 (HUDF 1.3 mm sources)**: coordinates Table 1  
  > "We use here the 11 galaxies listed in Table 2 of (cite: rujopakarn16)" (Supplementary sample from the Hubble Ultra Deep Field); z/distance z=1.319-3.0  
  > "We use here the 11 galaxies listed in Table 2 of (cite: rujopakarn16)" (Supplementary sample from the Hubble Ultra Deep Field); distance from same redshifts as dunlop17 and rujopakarn16  
  > "We use here the 11 galaxies listed in Table 2 of (cite: rujopakarn16)" (Supplementary sample from the Hubble Ultra Deep Field)

## Data provenance

- ALMA projects: 2012.1.00983.S
- bands: Band 7 (345 GHz, 870 um) for GS; 1.3 mm for HUDF  
  > "in band 7 (345 GHz, 870$\mu$m) at an angular resolution of 0.2$''$" (ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 36 antennas  
  > "with a total of 36 antennas in band 7" (ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.2''x0.16'' beam (GS); 0.35'' (UDF)  
  > "ALMA synthesized beam of 0.2$''$$\times$0.16$''$" (ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: rms=40-70 uJy  
  > "The observed standard deviation of the noise spans $rms$=40-70 $\mu$Jy." (ALMA observations)
- time on source: 37-50 min per target  
  > "The integration time on each science target ranges from 37 to 50 minutes" (ALMA observations)
- observing dates: 2014 Aug 29 to Sep 1  
  > "which was observed from August 29 to September 1st, 2014" (Sample selection)
- pi or archival as stated: GS: own Cycle 1 program (PI R. Leiton); UDF: public data  
  > "complemented with 11 galaxies observed at 1.3 mm from public ALMA data in the Hubble Ultra-Deep Field" (Data)
- Other facility **Herschel**: PACS/SPIRE far-IR photometry and sample selection  
  > "All of the sources discussed in the present paper are detected with both *Herschel* photometers PACS and SPIRE with a S/N$>$3." (Dust, gas and stellar masses)
- Other facility **HST/CANDELS**: H-band morphology, sizes and optical astrometry  
  > "derived from the Sérsic fit to WFC3 $H$ band images by (cite: vanderwel12)" (Table 2 notes)
- Other facility **Chandra 7 Msec CDF-S**: X-ray luminosities for AGN classification  
  > "11 are detected in X-rays with the 7 Msec exposure of the *Chandra* Deep Field-*South* image (cite: luo17)" (Star formation compactness and AGN activity)
- External data: HUDF 1.3 mm fluxes, sizes and axis ratios for 11 galaxies  
  > "from (cite: rujopakarn16) for the UDF galaxies" (Table 2 notes) [from (cite: rujopakarn16); (cite: dunlop17)]
- External data: MS parametrization and median SFR  
  > "using the parametrization of the redshift evolution of the MS from (cite: schreiber15)" (Star formation rates) [from (cite: schreiber15)]
- External data: Local GOALS Herschel-PACS sizes  
  > "The sizes measured for these galaxies (as described in (cite: diazsantos17))" (Revised IR8-Sigma_IR relation) [from (cite: diazsantos17)]

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
- primary beam correction: final images corrected for primary beam  
  > "the final images were corrected for the primary beam, although all our targets are located at the center of the ALMA pointings" (Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Stellar mass method  
  > "Following (cite: pannella15), stellar masses were computed using a delayed exponentially declining star formation history" (Dust, gas and stellar masses) [from (cite: pannella15)]
- Gas-to-dust ratio vs metallicity  
  > "using Eq. [\[EQ:leroy\]] from (cite: leroy11)" (Dust, gas and stellar masses) [from (cite: leroy11)]
- Starburstiness definition  
  > "we will use a single parameter to quantify this distance to the MS called the "starburstiness" as in (cite: elbaz11)" (Star formation rates) [from (cite: elbaz11)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (robust, cleaning, uv range)
- uvmodelfit starting parameters
- CIGALE grid parameters
- Exact per-galaxy photometry catalog
- Calibration flux scale uncertainty

## Analysis recipe

1. **measure ALMA flux and size**: uvmodelfit 2D Gaussian in uv plane, cross-checked with GALFIT Gaussian and Sersic in image plane  
  > "Flux densities and sizes were both measured in the $uv$ plane, using the *uvmodelfit* code in CASA, and in the image plane using the *GALFIT* code" (Data reduction)
   - software: CASA, GALFIT
   - fitting: _not stated_
   - validation: uv and image sizes agree within 15%  
  > "agree within 15 %, with only a 5 % systematic difference" (Data reduction)
2. **SED fitting for L_IR, dust and stellar mass, AGN**: EAzY/FAST for stellar side, CIGALE with Draine&Li models for dust, decompIR for AGN subtraction  
  > "modeled using the IR emission spectra for dust heated by stellar light from (cite: draine07) by running the code CIGALE" (Dust, gas and stellar masses)
   - software: EAzY, FAST, CIGALE, decompIR
   - parameter: alpha=2, Umax=10^6  
  > "we fixed the slope of the distribution of intensities of the interstellar radiation field (ISRF, $U$), $\alpha$, to $\alpha$=2" (Dust, gas and stellar masses)
   - assumption: Salpeter IMF, Calzetti law, solar metallicity  
  > "We assumed a solar metallicity, a (cite: salpeter55) IMF and a (cite: calzetti00) attenuation law" (Dust, gas and stellar masses)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive gas mass and depletion time**: Gas-to-dust ratio from metallicity (Leroy11) with metallicity from Genzel12 mass-metallicity relation; tau_dep=Mgas/SFR  
  > "Metallicities for our $z$$\sim$2 sample of ALMA galaxies were inferred using the mass - metallicity relation" (Dust, gas and stellar masses)
   - assumption: local GDR-metallicity relation holds at all redshifts; M_Chabrier=M_Salpeter/1.7  
  > "hence assuming that this relation holds at all redshifts" (Dust, gas and stellar masses)
   - fitting: _not stated_
   - validation: compared with Tacconi18 trends  
  > "we do find that both our main sequence and starburst galaxies follow the global trends" (Gas fraction and depletion time)
4. **compute SFR, starburstiness and Sigma_IR**: SFR_tot=SFR_IR+SFR_UV (Kennicutt98, Daddi04); R_SB=SFR/SFR_MS (Schreiber15); Sigma_IR=(L_IR/2)/(pi R_circ^2)  
  > "SFR$_{\rm tot}$=SFR$_{\rm IR}$$+$SFR$_{\rm UV}$" (Star formation rates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and uvmodelfit  
  > "The data reduction was carried out with CASA" (Data reduction)
- **GALFIT** : image-plane size fits  
  > "in the image plane using the *GALFIT* code (cite: peng02)" (Data reduction)
- **CIGALE** : dust SED fitting  
  > "by running the code CIGALE" (Dust, gas and stellar masses)
- **EAzY** : photometric redshifts  
  > "photometric redshifts with the EAzY" (Dust, gas and stellar masses)
- **FAST** : stellar masses  
  > "stellar masses with the FAST" (Dust, gas and stellar masses)
- **decompIR** : AGN subtraction  
  > "We used the code *decompIR* by (cite: mullaney11) to subtract AGN contributions" (Dust, gas and stellar masses)
- **imfit** : Sersic modelling of neighbours for GS8 photometry  
  > "as single Sérsic profiles using `imfit` (cite: erwin15)" (Serendipitous detection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GS ALMA flux densities (870 um) | 1100-6420 | 40-140 uJy | uJy | 1 | / GS8 / 3.240 / 6420 $\pm$ 140 |
| median Sersic index of GS ALMA profiles | 1.27 | 0.48 | dimensionless | 1 | median Sérsic index is $n$=1.27$\pm$0.48 |
| R_H/R_ALMA size ratio | 1.45 | 1.0 | dimensionless | 1 | 1.45$\pm$1.0 times more compact than at 1.6 $\mu$m |
| GS8 photometric redshift of background galaxy | 3.24 | 0.20 | dimensionless | 0 | We found $z$$_{\rm phot}$=3.24$\pm$0.20 |
| local IR8-Sigma_IR scatter | 0.11 | not stated | dex | 0 | 68 % median absolute deviation (MAD) of only 0.11 $dex$ |
| depletion time of compact hidden starbursts | ~146 | not stated | Myr | 4 | ($\tau_{\rm dep}$$\sim$146 Myr) |
| AGN fraction at high Sigma_IR | 75% (6 of 8) | not stated | percent | 0 | 75 % of the galaxies with $\Sigma_{\rm IR}$$\geq$3$\times$10$^{11}$ L$_{\odot}$ kpc$^{-2}$ harbor an AGN (6 out of 8 galaxies) |

## Qualitative findings

- ALMA dust emission is compact and centrally concentrated, with no kpc clumps.  
  > "we find that the ALMA continuum emission is concentrated in a nuclear region, with no evidence for external clump contributions" (An ALMA view on kpc clumps)

## Claim tuples

- H: Starbursts can be hidden within the MS | E: Compare tau_dep, gas fraction and Sigma_IR of MS galaxies with starbursts | R: Four MS galaxies have tau_dep~150 Myr and Sigma_IR~1.5e12 | F: Compact starbursts hidden in the high-mass MS exist | **supported**
- H: SED-derived SFR is reliable for starbursts | E: Compare SFR_IR+SFR_UV with SFR_SED vs R_SB | R: Ratio rises roughly proportional to R_SB | F: SED-fitting underestimates SFR in starbursts due to UV-FIR offset | **supported**
- H: AGN link to compactness | E: X-ray AGN fraction vs Sigma_IR | R: 75% AGN at high Sigma_IR | F: Compact star formation associated with AGN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: GS8 ALMA emission attributed to foreground z=1.1 galaxy rejected due to unrealistic dust mass  
  > "Considering these unrealistic dust temperatures and masses" (Serendipitous detection)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased to M*>1e11; metallicity of starbursts may bias gas masses  
  > "our discussion on $z$$\sim$2 main sequence galaxies is limited to a stellar mass of $M_{\star}$$>$10$^{11}$ M$_{\odot}$" (Gas fraction and depletion time)
- Caveat (inferred, ours): Small sample (19)
- Caveat (inferred, ours): Gas masses rely on assumed GDR-metallicity relation
- Caveat (inferred, ours): AGN contamination of stellar masses (GS5)

## Reproducibility

- Data public (paper): GS data from ALMA project 2012.1.00983.S; HUDF data public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00983.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: CIGALE configuration
- Missing: multiwavelength photometry catalog
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data public and flux/size tables given, but processing and SED fitting settings are sparse.
- Rediscovery candidate: no, Key results depend on multi-wavelength SED fitting with unspecified settings.

## Links

- Method: (cite: schreiber15) (MS definition)
- Method: (cite: elbaz11) (IR8 and starburstiness)
- Companion: (cite: rujopakarn16) (HUDF ALMA sizes)
- Companion: (cite: dunlop17) (HUDF 1.3 mm survey)
- Related: GOODS-Herschel
- Related: CANDELS
- Related: ALMA HUDF survey

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
