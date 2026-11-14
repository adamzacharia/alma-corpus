# ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at One-millimeter (ASAGAO): X-Ray AGN Properties of Millimeter-selected Galaxies

`2018ApJ...853...24U` | The Astrophysical Journal 2018 | first author: Ueda, Y. | arXiv: 1712.03350 | DOI: 10.3847/1538-4357/aa9f10

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the X-ray AGN properties (AGN fraction, LX/LIR, LX vs stellar mass) of millimeter-selected galaxies in GOODS-S, and what do they imply for galaxy-SMBH co-evolution?  
  > "In this paper, we investigate the X-ray AGN properties of millimeter galaxies detected in our survey and that by D17, utilizing the latest Chandra 7 Ms source catalog" (1 Introduction)
- Target **ASAGAO survey field in GOODS-S (12 sources) plus UDF sources of D17**: coordinates Source positions in Table 1 (e.g. ID 1: 03:32:28.51 -27:46:58.37)  
  > "ALMA band 6 (1.2 mm) observations of the $5' \times 5'$ ($\approx 26$ arcmin$^2$) area of the ASAGAO were conducted in September 2016" (2.1 Observations and Source Detection); z/distance Mostly z~2-3; adopted redshifts in Table 1 (0.523 to 5.0)  
  > "ALMA band 6 (1.2 mm) observations of the $5' \times 5'$ ($\approx 26$ arcmin$^2$) area of the ASAGAO were conducted in September 2016" (2.1 Observations and Source Detection); distance from ZFOURGE catalog (Straatman et al. 2016) or D17 spectroscopic/photometric redshifts  
  > "ALMA band 6 (1.2 mm) observations of the $5' \times 5'$ ($\approx 26$ arcmin$^2$) area of the ASAGAO were conducted in September 2016" (2.1 Observations and Source Detection)

## Data provenance

- ALMA projects: 2015.1.00098.S
- bands: Band 6 (1.2 mm)  
  > "ALMA band 6 (1.2 mm) observations of the $5' \times 5'$ ($\approx 26$ arcmin$^2$) area of the ASAGAO" (2.1 Observations and Source Detection)
- frequencies and spectral setup: Two tunings at 1.14 and 1.18 mm; 4 basebands each, 2000 MHz, 128 channels; 244–248, 253–257, 259–263, 268–272 GHz  
  > "Two frequency tunings were adopted centered at 1.14 mm and 1.18 mm to cover a wider frequency range, whose central wavelength was 1.16 mm." (2.1 Observations and Source Detection)
- continuum bandwidth: 16 GHz total  
  > "the total bandwidth was 16 GHz covering the 244–248 GHz, 253–257 GHz, 259–263 GHz, and 268–272 GHz frequency ranges" (2.1 Observations and Source Detection)
- arrays: _not stated_
- configurations: C40-6  
  > "conducted in September 2016 in the C40-6 array configuration for a total observing time of 45 hours" (2.1 Observations and Source Detection)
- baselines: _not stated_
- angular resolution: 0.94" x 0.67" after uv-taper  
  > "which gives the final synthesized beamsize of $0.94\ensuremath{''} \times 0.67\ensuremath{''}$" (2.1 Observations and Source Detection)
- max recoverable scale: _not stated_
- sensitivity: typical rms 89 uJy/beam  
  > "the typical rms noise level of 89 $\mu$Jy beam$^{-1}$" (2.1 Observations and Source Detection)
- time on source: 45 hours total observing time  
  > "for a total observing time of 45 hours" (2.1 Observations and Source Detection)
- observing dates: September 2016  
  > "were conducted in September 2016" (2.1 Observations and Source Detection)
- pi or archival as stated: PI K. Kohno, own team's data  
  > "Project code: 2015.1.00098.S, PI: K. Kohno" (2.1 Observations and Source Detection)
- Other facility **Chandra 7 Ms (CDFS)**: X-ray source catalog and images for counterparts, luminosities, stacking  
  > "We cross-match the ALMA source list with the Chandra 7 Ms source catalog of the CDFS (cite: luo17)" (3 Cross Matching with Chandra 7 Ms Catalog)
- Other facility **ZFOURGE**: Optical-NIR counterparts, redshifts, stellar masses  
  > "The ASAGAO sources are cross-matched against the ZFOURGE catalog (cite: str16)" (2.2 Definition of Our ALMA Sample)
- Other facility **Herschel PACS/SPIRE**: FIR photometry for IR luminosities  
  > "All of them are also detected in FIR bands (70–160 $\mu$m) with Herschel/PACS (cite: elb11)." (2.2 Definition of Our ALMA Sample)
- Other facility **Gaia DR1**: Astrometric offset correction  
  > "calibrated by the positions of stars in the Gaia Data Release 1 catalog (cite: gai16)" (2.2 Definition of Our ALMA Sample)
- External data: 1.3 mm UDF sources, fluxes, L_IR, stellar masses, redshifts  
  > "we also include fainter flux ALMA sources detected in the deep 1.3 mm image of the UDF" (2.2 Definition of Our ALMA Sample) [from Dunlop et al. 2017 (cite: dun17)]
- External data: ASPECS 1.2 mm fluxes  
  > "The 1.2 mm fluxes obtained by ASPECS are listed in the 6th column of Table 1" (2.2 Definition of Our ALMA Sample) [from (cite: ara16)]
- External data: ALESS-AGN sample properties  
  > "from (cite: wan13) for the ALESS-AGN sample (re-calibrated for a Chabrier IMF)" (4.1 Correlation between Star Formation Rate and Stellar Mass) [from (cite: wan13)]

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

- task: tclean in CASA  
  > "The maps were processed with the **CLEAN** algorithm with the task **tclean**" (2.1 Observations and Source Detection)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting, cell size of 0.15 arcsec, gridder of mosaic, specmode of muti-frequency synthesis, and nterms of 2." (2.1 Observations and Source Detection)
- uv taper: 160 kλ  
  > "we adopted a $uv$-taper of 160 k$\lambda$ to improve the surface brightness sensitivity" (2.1 Observations and Source Detection)
- cell size: 0.15 arcsec  
  > "natural weighting, cell size of 0.15 arcsec, gridder of mosaic, specmode of muti-frequency synthesis, and nterms of 2." (2.1 Observations and Source Detection)
- image size: _not stated_
- masking: Clean boxes at peak SN>5, cleaned to 2 sigma  
  > "Clean boxes were placed when a component with a peak signal-to-noise ratio (SN) above 5.0 is identified, and **CLEAN**ed down to a $2\sigma$ level." (2.1 Observations and Source Detection)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Detection on uncorrected image; fluxes corrected for primary beam  
  > "Source detection was conducted on the image before correcting for the primary beam attenuation." (2.1 Observations and Source Detection)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.94" x 0.67"  
  > "which gives the final synthesized beamsize of $0.94\ensuremath{''} \times 0.67\ensuremath{''}$" (2.1 Observations and Source Detection)
- final rms: 89 uJy/beam  
  > "the typical rms noise level of 89 $\mu$Jy beam$^{-1}$" (2.1 Observations and Source Detection)

### Inherited from earlier work

- Details of ALMA observations and data reduction  
  > "The details of the observations and data reduction are described in Hatsukade *et al.*  (in prep.), and here we briefly summarize them." (2.1 Observations and Source Detection) [from Hatsukade et al. (in prep.)]
- SED analysis details  
  > "Further details of the SED analysis are given in Yamaguchi et al. (in prep.)." (2.3 SED fitting and Infrared Luminosities) [from Yamaguchi et al. (in prep.)]
- AGN classification criteria  
  > "We adopt similar criteria proposed by (cite: wan13) to classify an X-ray detected object as an AGN" (3 Cross Matching with Chandra 7 Ms Catalog) [from (cite: wan13)]
- X-ray column density and luminosity recipe  
  > "Following the recipe described in (cite: ued03), we estimate the column density and intrinsic (de-absorbed) luminosity of each Chandra object." (3 Cross Matching with Chandra 7 Ms Catalog) [from (cite: ued03)]
- Cumulative AGN fraction method  
  > "Following (cite: wan13), we calculate the cumulative AGN fraction" (4.2 AGN Fraction) [from (cite: wan13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum image construction for tclean (e.g. which spectral windows, imaging weights confirmed)
- Calibrator and flux scale details and pipeline/CASA version
- Aegean source-finding parameters
- MAGPHYS priors and photometry set (deferred to Yamaguchi et al. in prep.)
- Final ASAGAO catalog processing (deferred to Hatsukade et al. in prep.)
- Chandra count-rate extraction and hardness-ratio fitting code details

## Analysis recipe

1. **Image ALMA data and detect sources**: tclean imaging with 160 klambda uv-taper; Aegean source finding at 5 sigma on pre-PB-correction image; elliptical Gaussian flux fit  
  > "The integrated flux density is calculated with elliptical Gaussian fitting." (2.1 Observations and Source Detection)
   - software: CASA, tclean, Aegean
   - parameter: peak SN threshold 5.0 sigma; 12 sources  
  > "We find 12 sources with a peak SN threshold of $5.0\sigma$" (2.1 Observations and Source Detection)
   - fitting: _not stated_
   - validation: No negative sources below -5 sigma  
  > "whereas no negative source with a peak SN $< -5.0\sigma$ is found" (2.1 Observations and Source Detection)
2. **Match ALMA sources to ZFOURGE counterparts**: Positional match within 0.2" after Gaia astrometric offset correction (up to 1" for extended)  
  > "We search for counterparts from the ZFOURGE catalog whose angular separation from the ALMA position is smaller than $0.2\ensuremath{''}$" (2.2 Definition of Our ALMA Sample)
   - fitting: _not stated_
   - validation: Chance probability ~0.004  
  > "the chance probability that an unrelated object falls within a radius of $0.2\ensuremath{''}$ is only $\approx$0.004" (2.2 Definition of Our ALMA Sample)
3. **Derive infrared luminosities via SED fitting**: MAGPHYS fit of 43 photometric points with redshift fixed  
  > "We use 43 optical-to-millimeter photometric data including the ALMA, ZFOURGE, and de-blended Herschel/SPIRE photometries" (2.3 SED fitting and Infrared Luminosities)
   - software: MAGPHYS
   - assumption: 20% AGN contribution subtracted for SFR; SFR = 1.09e-10 LIR (Chabrier IMF)  
  > "SFR/(${M_{\odot}}$ yr$^{-1}$) $=
1.09\times10^{-10} L_{\rm IR}/\mbox{${L_{\odot}}$}$" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared with D17 and Straatman values; consistent within 0.1–0.2 dex  
  > "are found to be consistent with the $L_{\rm IR}$ values in D17 (for IDs 3, 6, and 8) and in (cite: str16) within 0.1–0.2 dex in most cases" (2.3 SED fitting and Infrared Luminosities)
4. **Cross-match with Chandra 7 Ms and derive X-ray NH and LX**: Match within 3x combined positional error; hardness-ratio spectral model (cutoff power law plus reflection, Gamma=1.9); AGN classification with four criteria; CSTACK stacking of non-detections  
  > "X-ray counterparts are selected if the angular separation between the ALMA and Chandra sources is smaller than 3 times their combined $1\sigma$ positional error" (3 Cross Matching with Chandra 7 Ms Catalog)
   - software: CSTACK
   - parameter: Galactic NH = 8.8e19 cm^-2; Gamma fixed 1.9 if apparent Gamma<1.9  
  > "Galactic absorption, which is fixed at $N_{\rm H}$ = $8.8\times10^{19}$ cm$^{-2}$" (3 Cross Matching with Chandra 7 Ms Catalog)
   - fitting: _not stated_
   - validation: Spurious identification probability <0.01  
  > "The probability of spurious identification is negligibly small, $<$0.01" (3 Cross Matching with Chandra 7 Ms Catalog)
5. **Compute AGN fraction**: Cumulative AGN fraction sum(1/N_MG,i) above X-ray flux limits, Gehrels errors  
  > "we calculate the cumulative AGN fraction at $f_{\rm X} >
f_{\rm X, lim}$ as $\sum_{i=1}^{N} (1/N_{{\rm MG},i})$" (4.2 AGN Fraction)
   - fitting: _not stated_
   - validation: Same flux limit as ALESS gives ~25%, consistent with ALESS  
  > "the AGN fraction for the ASAGAO $z=1.5-3$ sample becomes $\sim$25%, consistent with the ALESS result" (4.2 AGN Fraction)
6. **Compare LX, LIR and stellar mass with co-evolution predictions**: Convert LX to accretion rate with kappa and eta; simultaneous-evolution relation SFR(1-R)=A*Mdot_BH; compare LX vs M* for Eddington ratios  
  > "If the galaxy-SMBH evolution is exactly simultaneous over cosmic time, we expect the relation" (4.4 Correlation between Infrared and X-ray Luminosities)
   - parameter: eta=0.05; kappa_0.5-8≈45; R=0.41; A_bul~200; A_tot~400  
  > "Here we adopt $\eta=0.05$" (4.4 Correlation between Infrared and X-ray Luminosities)
   - assumption: 20% of LIR is AGN bolometric luminosity  
  > "assuming that 20% of $L_{\rm IR}$ is the intrinsic AGN bolometric luminosity" (4.4 Correlation between Infrared and X-ray Luminosities)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and imaging  
  > "The data were reduced with Common Astronomy Software Applications (cite: mcmu07)." (2.1 Observations and Source Detection)
- **tclean** : CLEAN imaging  
  > "The maps were processed with the **CLEAN** algorithm with the task **tclean**" (2.1 Observations and Source Detection)
- **Aegean** : Source finding and flux measurement  
  > "The source and noise properties were estimated with the Aegean (cite: hanc12) source-finding algorithm." (2.1 Observations and Source Detection)
- **MAGPHYS** : SED fitting for IR luminosity  
  > "utilizing the MAGPHYS code (cite: dacunha2008; dacunha2015)" (2.3 SED fitting and Infrared Luminosities)
- **CSTACK** : Chandra stacking of undetected sources  
  > "We also perform stacking analysis of the 7 Ms Chandra images for these 9 sources with the CSTACK program" (3 Cross Matching with Chandra 7 Ms Catalog)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ASAGAO sources detected | 12 | not stated | sources | 1 | We find 12 sources with a peak SN threshold of $5.0\sigma$ |
| AGN fraction z=1.5-3 ULIRGs (log LIR 12-12.8) | 90 | +8/-19 | % | 5 | 90$^{+8}_{-19}$% and $57^{+23}_{-25}$% for the ultra/luminous infrared galaxies |
| AGN fraction z=1.5-3 LIRGs (log LIR 11.5-12) | 57 | +23/-25 | % | 5 | 90$^{+8}_{-19}$% and $57^{+23}_{-25}$% for the ultra/luminous infrared galaxies |
| X-ray detection rate of ALMA sample | 61 (14 of 23) | 10 | % | 4 | The X-ray detection rate of our ALMA sample is $61\pm10$% (14 out of 23) |
| AGN fraction in ASAGAO sample | 67 | +15/-19 | % | 5 | is $67^{+15}_{-19}$% at $f_{\rm X} > 5\times10^{-17}$ erg cm$^{-2}$ s$^{-1}$ (0.5–7 keV) |
| Bolometric correction kappa_0.5-8 | ≈45 | not stated | dimensionless | 6 | we find $\kappa_{0.5-8} \approx 45$ |
| Mean log LIR for log LX=42-43 | 12.15 | 0.08 | log Lsun | 6 | $12.15\pm0.08$ and $12.27\pm0.10$ |

## Qualitative findings

- About two thirds of z=1.5-3 X-ray AGN have LX/LIR below the simultaneous evolution value, so SF-dominant with relatively small SMBHs  
  > "The majority ($\sim$2/3) of the ALMA and/or Herschel detected X-ray AGNs at $z=1.5-3$ appear to be star-formation dominant populations" (abstract)

## Claim tuples

- H: Millimeter-selected galaxies at z=1.5-3 have high AGN fractions when probed with very deep X-ray data | E: Cross-match ASAGAO+UDF ALMA sources with Chandra 7 Ms and compute cumulative AGN fractions | R: 90% for ULIRGs, 57% for LIRGs | F: High AGN fractions revealed thanks to the deep X-ray limit | **supported**
- H: SMBH and stellar growth are simultaneous in individual galaxies | E: Compare LX vs LIR with simultaneous-evolution lines | R: Large scatter (>2 dex), bimodal LX/LIR distribution | F: Evolution not exactly simultaneous in individual galaxies | **supported**
- H: Black hole masses follow local MBH-M* relation | E: LX vs M* with assumed Eddington ratios | R: Most AGN near lambda_Edd=0.01 unless A~2000 | F: Many hosts have BH masses smaller than local relation expects | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Column density uncertainties are large; some AGN may be Compton-thick  
  > "We have to bear in mind, however, that the uncertainty in the column density is often quite large due to the limited photon statistics" (4.3 X-ray Absorption Properties)
- Caveat (inferred, ours): Small sample (25 sources) gives large errors on AGN fractions
- Caveat (inferred, ours): Conclusions on BH masses rely on assumed kappa, eta and Eddington ratio
- Caveat (inferred, ours): Photometric redshifts and uncertain NH
- Caveat (inferred, ours): Mixed 1.2 and 1.3 mm samples

## Reproducibility

- Data public (paper): Project code given and acknowledged ALMA data; Chandra catalog public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00098.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ASAGAO catalog details in Hatsukade et al. in prep.
- Missing: SED fit details in Yamaguchi et al. in prep.
- Missing: Chandra spectral fitting code
- Data volume (inferred): ~100-300 GB raw ALMA data; Chandra catalog small
- Score (inferred): 3/5, ALMA part is brief and deferred to in-prep papers, but the downstream catalog-based analysis and Table 1 allow partial reproduction.
- Rediscovery candidate: no, Key steps depend on unpublished companion papers and external catalogs.

## Links

- Method: Ueda et al. 2003 (cite: ued03) (X-ray NH and luminosity recipe)
- Method: Wang et al. 2013 (cite: wan13) (AGN criteria and cumulative fraction method)
- Companion: Hatsukade et al. (in prep.) (ASAGAO observations, reduction and catalog)
- Companion: Dunlop et al. 2017 (cite: dun17) (Deeper 1.3 mm UDF survey)
- Companion: Rujopakarn et al. in prep. (JVLA radio results)
- Related: ALESS
- Related: ASPECS
- Related: ZFOURGE
- Related: Chandra 7 Ms CDFS

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 85,
  "stated": 57,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
