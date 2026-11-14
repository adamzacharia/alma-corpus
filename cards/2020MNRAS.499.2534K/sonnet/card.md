# Resolved star formation in the metal-poor star-forming region Magellanic Bridge C

`2020MNRAS.499.2534K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Kalari, Venu M. | arXiv: 2009.11868 | DOI: 10.1093/mnras/staa2963

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do molecular clumps, YSOs and PMS stars in the metal-poor Magellanic Bridge region MB-C compare with Galactic counterparts?  
  > "In our study, we focus on the properties and morphologies of the molecular clouds and young forming stars in MB-C." (1 Introduction)
- Target **Magellanic Bridge C (MB-C)**: coordinates clumps near RA 01h56m-01h57m, Dec -74d15'-17'  
  > "The distance to that cluster is adopted as the distance to MB -C in this paper." (1 Introduction); "located 59 kpc away in the Magellanic Bridge" (abstract); z/distance 59 kpc  
  > "The distance to that cluster is adopted as the distance to MB -C in this paper." (1 Introduction); "located 59 kpc away in the Magellanic Bridge" (abstract); distance from distance of cluster NGC 796 (Kalari et al. 2018a)  
  > "The distance to that cluster is adopted as the distance to MB -C in this paper." (1 Introduction); "located 59 kpc away in the Magellanic Bridge" (abstract)

## Data provenance

- ALMA projects: 2015.1.1013.S
- bands: Band 3 (84–116 GHz)  
  > "using the Band 3 receiver (84–116 GHz)" (2.1 Observations)
- frequencies and spectral setup: spectral resolution 0.5 km/s; FoV 4.1' x 2.6'  
  > "a spectral resolution of 0.5 km s$^{-1}$" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m antennas  
  > "The source was mapped with ALMA 12-m antennas" (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.6" x 3.3" (~0.9 pc)  
  > "at a beam size of 3.6$\ensuremath{''} \times$3.3$\ensuremath{''}$ ($\sim$0.9 pc at the distance to MB-C)" (2.1 Observations)
- max recoverable scale: 25.4"  
  > "the maximum recoverable scale (MRS) is 25.4$\ensuremath{''}$" (2.1 Observations)
- sensitivity: 0.027 Jy/beam (0.21 K) average rms  
  > "is 0.027 Jy beam$^{-1}$ (0.21 K)" (2.1 Observations)
- time on source: _not stated_
- observing dates: 2016 January 22  
  > "on 2016 January 22" (2.1 Observations)
- pi or archival as stated: PI M. Rubio program  
  > "ALMA Program 2015.1.1013.S (PI: M. Rubio)" (2.1 Observations)
- Line: CO J=1-0 (not stated)
- Other facility **Spitzer (IRAC, MIPS; SAGE-SMC)**: 3.6-24 micron photometry for YSO SED fitting  
  > "The data was taken as part of the *Spitzer* legacy program SAGE-SMC" (3.1 Data)
- Other facility **SOAR/SAM**: r', i', Halpha adaptive-optics imaging for PMS stars  
  > "The MB-C region was observed using the SAM (SOAR Adaptive Optics module) imager" (4.1 Adaptive optics optical observations)
- Other facility **Herschel**: 500/350/250 micron image for filament  
  > "we simply overplot YSOs and PMS candidates on the 500$\mu$m/350$\mu$m/250$\mu$m *Herschel* *rgb* image of MB -C (Seale et al. 2014)" (5.2)
- Other facility **NANTEN**: single-dish CO luminosity for comparison  
  > "with the luminosity of the region reported by Mizuno et al. (2006) using NANTEN single-dish observations" (2.2)
- External data: NANTEN I_CO of 140 mK km/s and X_CO 1.4e21 for the Bridge  
  > "using the reported $I_{\text{CO}}$ of 140 mK km s$^{-1}$ by Mizuno et al. (2006)" (2.2) [from Mizuno et al. (2006)]
- External data: YSO model grid  
  > "The observed SEDs are fit against the Robitaille (2017) model grid of young stellar objects" (3.2 YSO SED fitting) [from Robitaille (2017)]
- External data: Isochrones and mass tracks  
  > "we utilise the Bressan et al. (2012) single star isochrones and tracks" (4.3) [from Bressan et al. (2012)]

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

- SOAR photometry methodology and main-sequence colours  
  > "Following the same methodology of Kalari et al. (2018a), we detected sources, computed their photometry in the instrumental system" (4.1) [from Kalari et al. (2018a)]
- Halpha EW formula  
  > "following Kalari 2019" (4.2) [from Kalari 2019]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging steps (weighting, cleaning, masks)
- Whether archive or reprocessed products were used
- Exact CPROPS parameters beyond 4 sigma mask and edge threshold
- Rest frequency and moment-map velocity limits details

## Analysis recipe

1. **Identify CO clumps and measure properties**: CPROPS with modified CLUMPFIND (/ECLUMP) decomposition; moment method with sensitivity extrapolation and deconvolution  
  > "we use the modified CLUMPFIND algorithm (setting the keyword /ECLUMP) to apply the decomposition process on the CO distribution." (2.2 Clump identification and analysis)
   - software: CPROPS, CASA
   - parameter: mask above 4 sigma_rms, edge threshold 2.0–1.5 sigma  
  > "emission above 4$\sigma_{\rm rms}$ and edge threshold of about 2.0–1.5$\sigma$" (2.2 Clump identification and analysis)
   - assumption: Virial mass for spherical cloud with 1/r density profile; distance 59 kpc  
  > "assuming a spherical cloud with a 1/$r$ density profile (MacLaren, Richardson & Wolfendale 1988)" (2.3 Clump parameters)
   - fitting: _not stated_
   - validation: Compared ALMA CO luminosity with NANTEN: 58% recovered  
  > "Thus, 58 per cent of NANTEN observed luminosity is recovered by ALMA" (2.2)
2. **Estimate X_CO**: Least-squares fit of virial mass versus CO luminosity  
  > "the mean value for these clumps determined by a least squares fit to the data is around 5.5.$\pm$4.6" (2.5)
   - fitting: least squares  
  > "we find that the mean value for these clumps determined by a least squares fit to the data is around 5.5.$\pm$4.6" (Variations in the X_CO factor)
   - validation: _not stated_
3. **YSO SED fitting**: Fit Spitzer+optical SEDs to Robitaille (2017) models; select model set by chi2<=chi_best+3  
  > "the number of best fit models in each model set is calculated according to $\chi^2\leq\chi_{\rm{best}}+3$" (3.2)
   - software: SEDFitter
   - parameter: distance 59 kpc; A_V 0–20 mag; Weingartner & Draine SMC bar law; >=5 fluxes  
  > "The interstellar extinction range is between $A_V$ of 0.0 to 20 mag" (3.2)
   - fitting: Robitaille et al. 2007 fitting algorithm  
  > "The observed SEDs are fit against the Robitaille (2017) model grid of young stellar objects using the Robitalle et al. (2007) fitting algorithm." (YSO SED fitting)
   - validation: Compared to higher resolution optical imaging and Chen et al. 2014  
  > "Hence, we examine mIR imaging against higher resolution optical imaging (described in Section 4) shown in Fig. [12](#thumbnails) for each source to check for contamination." (Caveats of the SED models)
4. **Identify accreting PMS stars and derive mass/age**: r-Halpha excess gives EW; selection by Barrado y Navascues & Martin criteria; masses/ages from CMD with Bressan isochrones at 1/5 Zsun, A_V=0.5  
  > "We homogeneously select accreting PMS candidate stars from the sample of stars having measured EW$_{\rm{H}\alpha}$" (4.2)
   - software: STARFINDER, IRAF
   - assumption: Metallicity 1/5 Zsun; mean A_V = 0.5 mag  
  > "we assume for the remainder of our work a metallicity of 1/5 $Z_{\odot}$ to be representative for the region." (Introduction)
   - fitting: _not stated_
   - validation: Tested shifts in extinction (A_V 1, 2.5) and metallicity (1/2, 1/10 Zsun)  
  > "we recompute the stellar parameters (mass, age) after introducing mean shift in the assumed extinction by $A_V$=1, and 2.5 mag" (4.5)

## Software

- **CASA** : data reduction  
  > "The data was reduced using the Common Astronomy Software Application (CASA; McMullin et al. 2007)." (2.1)
- **CPROPS** : clump properties  
  > "the CPROPS algorithm of Rosolowsky & Leroy (2006) is utilised to compute their properties" (2.2)
- **STARFINDER** : optical PSF photometry  
  > "we employed the STARFINDER package of Diolaiti, Bendinelli & Bonaccini (2000)" (4.1)
- **SEDFitter** : YSO SED fitting  
  > "the SEDFitter Python utility" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clumps | 12 | not stated | dimensionless | 1 | Twelve clumps in MB-C having signal-to-noise greater than 13 at the peak are detected. |
| Fraction of NANTEN luminosity recovered | 58 | not stated | per cent | 1 | Thus, 58 per cent of NANTEN observed luminosity is recovered by ALMA |
| X_CO | 5.5e20 | 4.6e20 | cm^-2 (K km/s)^-1 | 2 | around 5.5.$\pm$4.6 $\times$ 10$^{20}$ cm$^{-2}$(K km s$^{-1}$)$^{-1}$ |
| Clump surface density range | 12–200 | not stated | Msun pc^-2 | 1 | The surface densities of these clumps range between 12–200 $M_{\odot}$pc$^{-2}$ |
| Mean A_V from optical TCD | 0.5 | 0.07 | mag | 4 | We corrected for a mean absolute extinction $A_V$ of 0.5$\pm$0.07 mag |
| Number of PMS candidates | 11 | not stated | dimensionless | 4 | In total, eleven stars are selected on this basis. |

## Qualitative findings

- Clump properties and YSO/PMS morphologies resemble Galactic ones; extinction towards YSOs is lower  
  > "YSO candidates in MB -C have lower extinction than their Galactic counterparts." (abstract)

## Claim tuples

- H: MB-C clumps are similar to Galactic clumps | E: CPROPS clump properties compared with Larson-type relations | R: clumps follow the Galactic M_vir–L_CO relation, marginally bound | F: clumps resemble Galactic clumps | **supported**
- H: Young and older PMS stars are spatially separated | E: ages compared with filament and clumps | R: younger stars along filament, older scattered | F: suggests spatial structure similar to Milky Way, but age errors limit conclusions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mid-IR resolution blends sources; ages and masses uncertain  
  > "we caution the reader that the final characterisation of the YSOs while accurate, might not provide a precise estimate of their properties" (3.1)
- Caveat (inferred, ours): Only one pointing with no total-power correction
- Caveat (inferred, ours): Virial masses depend on assumed density profile and low resolution
- Caveat (inferred, ours): Small-number statistics for YSOs/PMS

## Reproducibility

- Data public (paper): Public archives  
  > "The datasets were derived from sources in the public domain: ALMA science archive" (Data availability)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: CPROPS settings detail
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear clump analysis but ALMA processing details missing.
- Rediscovery candidate: yes, Public data, numeric clump table, CPROPS recipe stated.

## Links

- Method: Rosolowsky & Leroy (2006) (CPROPS algorithm)
- Method: Robitaille (2017) (YSO model grid and selection)
- Companion: Kalari et al. 2018a (SOAR observations and NGC 796 distance)
- Related: SAGE-SMC
- Related: Herschel HERITAGE

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.1013.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.01013.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
