# An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: The Far-infrared/Radio Correlation for High-redshift Dusty Star-forming Galaxies

`2020ApJ...903..138A` | The Astrophysical Journal 2020 | first author: Algera, H. S. B. | arXiv: 2009.06647 | DOI: 10.3847/1538-4357/abb77b

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Does the far-infrared/radio correlation (q_IR) of ALMA-selected 870 um SMGs, including radio-undetected ones via stacking, differ from the local correlation or evolve with redshift and physical properties?  
  > "We quantify the far-infrared/radio correlation through parameter" (abstract); "In this section, we set out to constrain whether there is any redshift-evolution in the far-infrared/radio correlation for the AS2UDS sub-millimeter galaxies." ((A lack of) Redshift Evolution in the FIRRC)
- Target **AS2UDS sample of 706 ALMA-detected SMGs in the UKIDSS/UDS field**: coordinates _not stated_; z/distance median z = 2.62 (+0.06/-0.04) for the full AS2UDS sample  
  > "Overall, 706/708 SMGs fall within the 1.4-GHz radio footprint covering the UDS field." (Radio Observations); "compared to $\langle z \rangle = 2.62_{-0.04}^{+0.06}$ for the full sample of AS2UDS SMGs (cite: dudzeviciute2019)." (Radio Properties of AS2UDS); "In total, 44 AS2UDS SMGs have a measured spectroscopic redshift." (SMG Redshifts and Physical Properties); distance from mostly photometric redshifts from SED fitting by (cite: dudzeviciute2019); 44 SMGs have spectroscopic redshifts  
  > "Overall, 706/708 SMGs fall within the 1.4-GHz radio footprint covering the UDS field." (Radio Observations); "compared to $\langle z \rangle = 2.62_{-0.04}^{+0.06}$ for the full sample of AS2UDS SMGs (cite: dudzeviciute2019)." (Radio Properties of AS2UDS); "In total, 44 AS2UDS SMGs have a measured spectroscopic redshift." (SMG Redshifts and Physical Properties)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S
- bands: Band 7 (344 GHz, 870 um)  
  > "targeted with ALMA observations in Band 7 ($344\,$GHz or $870\,\mu$m) across four different Cycles (1, 3, 4, 5)." (Submillimeter Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam varies 0.15''-0.5''; images homogenized to 0.5'' FWHM for source detection  
  > "the beam size of the data varies between $0.15\ensuremath{''}-0.5\ensuremath{''}$, though for source detection all images were homogenized to $0.5\ensuremath{''}$ FWHM." (Submillimeter Observations)
- max recoverable scale: _not stated_
- sensitivity: catalog of 708 SMGs at >=4.3 sigma (S870 > 0.9 mJy), false-positive rate 2%  
  > "The final sub-millimeter catalog contains 708 SMGs detected at $\geq4.3\sigma$ ($S_{870} > 0.9\,$mJy), with an estimated false-positive rate of 2%." (Submillimeter Observations)
- time on source: _not stated_
- observing dates: across ALMA Cycles 1, 3, 4, 5  
  > "across four different Cycles (1, 3, 4, 5)." (Submillimeter Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA 1.4 GHz**: deep 1.4 GHz mosaic (14 pointings, ~160 hr, RMS 7-10 uJy/beam, beam 1.8'' x 1.6'') giving radio flux densities for the SMGs  
  > "the 1.4-GHz image consists of a 14-pointing mosaic, for a total integration time of $\sim160\,$hr, across multiple VLA configurations." (Radio Observations); "The final root-mean-square (RMS) noise in the map is nearly uniform, reaching $7\,\mu\text{Jy}\,\text{beam}^{-1}$ in the image centre, up to $10\,\mu\text{Jy}\,\text{beam}^{-1}$ near the mosaic edges." (Radio Observations)
- Other facility **GMRT 610 MHz**: 610 MHz three-pointing mosaic (12 hr per pointing, RMS 45-80 uJy/beam, beam 6.1'' x 5.1'') used for spectral indices  
  > "The UDS field has further been targeted at 610 MHz by the Giant Metre-Wave Telescope (GMRT) during 2006 February 3-6 and December 5-10." (Radio Observations); "the GMRT image comprises a three-pointing mosaic, with each pointing accounting for 12 hr of observing time." (Radio Observations)
- Other facility **SCUBA-2 (S2CLS)**: parent 850 um single-dish survey of 0.96 deg^2 used to select ALMA targets  
  > "The parent single-dish sub-millimeter survey spans an area of $0.96\,\text{deg}^2$, to a median depth of $\sigma_{850} = 0.88\,$mJy beam$^{-1}$." (Submillimeter Observations)
- Other facility **UKIDSS DR11, Spitzer, Herschel and other multi-wavelength imaging**: optical/near-IR/mid-IR/far-IR photometry used by (cite: dudzeviciute2019) for redshifts and L_FIR  
  > "The multi-wavelength coverage of the UDS field, as well as the association of counterparts to the SMG sample, is described in detail in (cite: dudzeviciute2019)" (Additional Multi-wavelength Data)
- Other facility **Chandra X-UDS**: X-ray imaging covering about one-third of the SMGs, used for AGN diagnostics  
  > "only one-third of the AS2UDS SMGs lie within the footprint of the available" (SMG Redshifts and Physical Properties)
- External data: ALMA 870 um SMG catalog and survey data reduction (AS2UDS)  
  > "Further details of the survey strategy and data reduction are presented in (cite: stach2019)." (Submillimeter Observations) [from (cite: stach2019)]
- External data: 1.4 GHz flux densities (bandwidth-smearing corrected) for the AS2UDS sources  
  > "are provided for the AS2UDS sources by (cite: dudzeviciute2019)." (Radio Observations) [from (cite: dudzeviciute2019)]
- External data: Photometric redshifts, far-infrared luminosities, SFRs, stellar and dust masses from SED fitting  
  > "The redshift distributions, as well as numerous other physical properties of the AS2UDS SMGs, have been investigated by (cite: dudzeviciute2019)." (SMG Redshifts and Physical Properties) [from (cite: dudzeviciute2019); SED code (cite: dacunha2008; dacunha2015; battisti2019)]
- External data: Effective 870 um radii for a subset of SMGs (153 with robust sizes)  
  > "the latter of which was calculated for a subset of submm-bright AS2UDS sources by (cite: gullberg2019)." (Correlations with Physical Properties) [from (cite: gullberg2019)]
- External data: GMRT 610 MHz data reduction and imaging  
  > "Details of the data reduction and imaging are provided in (cite: ibar2009)." (Radio Observations) [from (cite: ibar2009)]
- External data: Local FIRRC normalization q_IR = 2.64 +/- 0.02  
  > "This value is lower than what is found for local, typically less strongly star-forming galaxies of $q_\text{IR} = 2.64 \pm 0.02$ (cite: bell2003)." (Radio Properties of AS2UDS) [from (cite: bell2003)]
- External data: ALESS comparison sample q_IR = 2.35 +/- 0.04 (full sample, with stacking)  
  > "they find a typical $q_\text{IR}$ across the full ALESS sample of $q_\text{IR} = 2.35 \pm 0.04$." (Previous Studies of the FIRRC) [from (cite: thomson2014)]
- External data: VLBI COSMOS survey results used for AGN-fraction argument (f_AGN = 0.70 at S_VLA <~ 1 mJy)  
  > "we adopt a value of $f_\text{AGN} = 0.70$, which is typical for their sample at $S_\text{VLA} \lesssim 1$mJy." (The FIRRC in Radio-selected Samples) [from (cite: herreraruiz2017)]
- Simulation/model as data: Mock-source insertion into the 1.4 GHz map for stacking tests (power-law counts slope -2, N=30-100, 40% resolved, 0.30'' position offsets)  
  > "whereby we insert faint (i.e., including flux densities well below the detection limit) mock sources into the UDS 1.4 GHz map, stack them, and compare both the inserted and recovered flux densities" (Stacking)
- Simulation/model as data: Analytic cosmic-ray cooling-time model for ULIRGs and SMGs (synchrotron, inverse Compton, ionization, bremsstrahlung) giving f_syn(z) and q_IR(z)  
  > "Parameter $f_\text{syn}$ is fully determined, under our simplifying assumptions, by the magnetic field strength, ISM density, physical size, far-infrared luminosity and redshift of any given source." (SMGs Compared to Local ULIRGs)

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
- final beam: 0.5'' FWHM (all ALMA images homogenized for source detection)  
  > "though for source detection all images were homogenized to $0.5\ensuremath{''}$ FWHM." (Submillimeter Observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA survey strategy and data reduction  
  > "Further details of the survey strategy and data reduction are presented in (cite: stach2019)." (Submillimeter Observations) [from (cite: stach2019)]
- 1.4 GHz VLA observations described elsewhere (in prep.)  
  > "These observations will be fully described in Arumugam et al. (in prep.)" (Radio Observations) [from Arumugam et al. (in prep.); (cite: thomson2019); (cite: dudzeviciute2019)]
- 610 MHz reduction and imaging  
  > "Details of the data reduction and imaging are provided in (cite: ibar2009)." (Radio Observations) [from (cite: ibar2009)]
- SED fitting, photometric redshifts, deblended Herschel photometry and L_FIR  
  > "Further details of the analysis, including an extensive description of calibration and testing, are provided in (cite: dudzeviciute2019)." (SMG Redshifts and Physical Properties); "(cite: dudzeviciute2019) deblended the data following (cite: swinbank2014)" (Additional Multi-wavelength Data) [from (cite: dudzeviciute2019); (cite: swinbank2014)]
- Radio-excess AGN threshold choice  
  > "with sources below this threshold being defined as a radio-excess AGN (following e.g., (cite: delmoro2013))." (AGN in AS2UDS) [from (cite: delmoro2013)]
- Definition of q_IR  
  > "Following e.g., (cite: condon1991b; bell2003; magnelli2015; calistrorivera2017), we define it as:" (Radio Properties of AS2UDS) [from (cite: condon1991b; bell2003; magnelli2015; calistrorivera2017)]
- Luminosity-limited sample definition  
  > "Secondly, we follow (cite: dudzeviciute2019) and focus on the 133 SMGs" (Radio Properties of AS2UDS) [from (cite: dudzeviciute2019)]
- Empty-region stacking for background and RMS  
  > "to create an “empty” stack indicative of the background and typical RMS-value (following e.g., (cite: decarli2014))." (Radio Stacking) [from (cite: decarli2014)]
- Deconvolved source sizes used to judge which sources are resolved  
  > "based on their deconvolved source sizes (following (cite: thomson2019))." (Stacking) [from (cite: thomson2019)]

### Not stated but needed to reproduce (our reading)

- Name and version of the source-extraction code used for stacked flux densities (only cited as mohanrafferty2015) and its fitting settings
- Name/version and priors of the SED-fitting code (cited only) and the resulting per-source L_FIR, z, SFR tables
- The 1.4 GHz VLA map and its bandwidth-smearing correction (Arumugam et al. in prep.)
- Exact redshift and L_FIR/SFR/M_star/M_dust/T_dust/R_eff bin edges for each stack
- Number of sources per stacked bin and how the five redshift bins were chosen
- Fitting method (likelihood, weighting) for gamma and beta slopes
- ALMA calibration/imaging parameters (all deferred to Stach et al. 2019)
- Numeric n_ISM and other benchmark inputs are only in Table; the f_syn model code is not provided

## Analysis recipe

1. **Cross-match ALMA SMGs to radio catalogs**: Positional cross-matching of AS2UDS positions to 1.4 GHz (>=4 sigma) and 610 MHz (4 sigma) catalogs  
  > "In total, 273 out of the 706 SMGs in the 1.4-GHz coverage of AS2UDS (39%) can be cross-matched to a radio counterpart detected at" (Radio Properties of AS2UDS)
   - parameter: 1.4 GHz matching radius 1.6'', false positives 1%  
  > "within a matching radius of $1.6\ensuremath{''}$" (Radio Properties of AS2UDS)
   - parameter: 610 MHz matching radius 2.0''  
  > "based on a cross-matching radius of $2.0\ensuremath{''}$." (Radio Properties of AS2UDS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive 610-1400 MHz spectral indices**: Direct alpha for 45 two-band detections; median stack of 1.4-GHz-only sources in both maps; fixed alpha = -0.80 adopted for 1.4-GHz-only SMGs  
  > "we median stack all AS2UDS SMGs detected solely at 1.4 GHz in both radio maps (225 sources within both the VLA and GMRT footprints)." (Radio Properties of AS2UDS); "we will therefore adopt a fixed $\alpha=-0.80$ for all AS2UDS SMGs detected only in the 1.4-GHz map." (Radio Properties of AS2UDS)
   - parameter: lower limits use 4x local RMS as 610 MHz upper limit  
  > "These limits were calculated by adopting four times the local RMS noise at the position of the radio source as an upper limit on the GMRT flux density." (Radio Properties of AS2UDS)
   - assumption: largest angular scale ~120'' so no diffuse emission missed  
  > "we do not expect to miss any diffuse emission at 1.4 GHz." (Radio Properties of AS2UDS)
   - fitting: _not stated_
   - validation: stacked alpha = -0.81 consistent with the two-band median  
  > "This value is consistent with the median spectral index obtained for the AS2UDS subsample having two radio detections" (Radio Properties of AS2UDS)
3. **Compute L_1.4 and q_IR**: K-corrected rest-frame 1.4 GHz luminosity L_1.4 = 4 pi D_L^2 S_1.4 / (1+z)^(1+alpha); q_IR = log10(L_FIR/3.75e12 W) - log10(L_1.4); upper limits at 4x local RMS with alpha = -0.80 for undetected  
  > "For SMGs without a radio counterpart, we adopt $4\times$ the local RMS-noise in the 1.4 GHz map and a fixed spectral index of $\alpha=-0.80$ in order to calculate the corresponding upper limit on the radio luminosity." (Radio Properties of AS2UDS)
   - parameter: L_FIR integrated over 8-1000 um from the SED fits  
  > "are determined in the wavelength range $8-1000\,\mu$m, and allow us to define the parameter" (Radio Properties of AS2UDS)
   - parameter: analysis samples: 659 SMGs at 1.5<=z<=4.0 (full) and 133 SMGs (luminosity-limited, L_FIR 4-7e12 Lsun with a SPIRE detection)  
  > "totalling 659 sources (93% of the entire AS2UDS sample)" (Radio Properties of AS2UDS)
   - assumption: flat LCDM, Omega_m = 0.30, Omega_Lambda = 0.70, H0 = 70 km/s/Mpc  
  > "we adopt a flat $\Lambda$-Cold Dark Matter cosmology, with $\Omega_\text{m} = 0.30$, $\Omega_\Lambda = 0.70$ and $H_0 = 70\,\text{km}\,\text{s}^{-1}\,\text{Mpc}^{-1}$." (Introduction)
   - fitting: _not stated_
   - validation: Changing alpha to the 16th/84th percentile changes L_1.4 by ~1.5x  
  > "leads to a typical difference of a factor of $1.5\times$ in the rest-frame 1.4-GHz radio luminosity." (Radio Properties of AS2UDS)
4. **Identify and remove radio-excess AGN**: Fixed threshold q_IR <= 1.55 flags radio-excess AGN  
  > "We identify AGN based on a fixed threshold of $q_\text{IR} \leq 1.55$, with sources below this threshold being defined as a radio-excess AGN" (AGN in AS2UDS)
   - parameter: threshold chosen so sources >~5x radio-brighter than the median FIRRC are flagged  
  > "are identified as radio-excess AGN." (AGN in AS2UDS)
   - fitting: _not stated_
   - validation: Other cuts and a redshift-dependent threshold tried; FIRRC insensitive to threshold  
  > "we find that the far-infrared/radio correlation for AS2UDS is insensitive to the particular threshold we adopt" (AGN in AS2UDS)
5. **Stack radio-undetected plus detected SMGs in bins**: Median stack of 51x51 pixel (18''x18'') cutouts at ALMA positions in 1.4 GHz (and 610 MHz) maps, plus empty-region stacks; source finder gives integrated flux (1.4 GHz) or peak flux (610 MHz)  
  > "we create cutouts of $51\times51$ pixels ($18''\times18''$) from the 1.4 GHz radio map, centered on the precise ALMA positions of the AS2UDS sources." (Radio Stacking); "We average these cutouts together by taking the median value across each pixel." (Radio Stacking)
   - software: source-extraction code of (cite: mohanrafferty2015)
   - parameter: stacks required to have SNR >~ 10  
  > "We ensure the stacks are all of sufficient signal-to-noise ($\text{SNR}\gtrsim10$)" (Results)
   - assumption: median stacking preferred over mean; clipped-mean gives the same results  
  > "We have verified, however, that our results are unchanged when adopting a clipped-mean stacking procedure" (Stacking)
   - fitting: Gaussian-fit integrated flux densities from the source finder; 100 bootstrap resamples with replacement for uncertainties  
  > "we perform a bootstrap analysis, whereby we repeat the procedure described above 100 times." (Radio Stacking)
   - validation: RMS drops as 1/sqrt(N); mock stacking shows integrated flux unbiased at SNR>~10 (Delta q_IR = -0.05 +/- 0.08)  
  > "We have verified that the RMS is reduced following a typical $1/\sqrt{N}$-behaviour" (Radio Stacking); "However, in the SNR-range achieved for AS2UDS, we find $\Delta q_\text{IR} = -0.05 \pm 0.08$ for the integrated flux density." (Stacking)
6. **Fit redshift evolution of q_IR**: Fit q_IR(z) proportional to (1+z)^gamma to radio-detected SMGs and to stacks in redshift bins (AGN removed)  
  > "we fit a function of the form $q_\text{IR}(z) \propto (1+z)^\gamma$" ((A lack of) Redshift Evolution in the FIRRC)
   - parameter: five redshift bins for the luminosity-limited stacks; bins sized to keep SNR>~10  
  > "As a result, the higher redshift bins contain a larger number of sources than the low-redshift ones, to compensate for the negative radio $K$-correction." ((A lack of) Redshift Evolution in the FIRRC)
   - fitting: _not stated_
   - validation: Equal-number-per-bin binning gives consistent results  
  > "simply adopting bins with an equal number of sources gives consistent results in all cases." ((A lack of) Redshift Evolution in the FIRRC)
7. **Test q_IR against physical properties**: Stack in bins of L_FIR, SFR, M_star, M_dust, T_dust and R_eff after removing AGN, then fit linear slope beta  
  > "we perform a stacking analysis by dividing our SMG sample into distinct bins for the aforementioned physical parameters, after the removal of radio AGN." (Correlations with Physical Properties)
   - fitting: linear fit through stacked points  
  > "A linear fit through the stacked datapoints indicates a slope of $\beta = 0.16 \pm 0.10$" (Correlations with Physical Properties)
   - validation: _not stated_
8. **Model SMG vs ULIRG offset with cosmic-ray cooling**: Compute f_syn from synchrotron, inverse Compton, ionization and bremsstrahlung cooling times; q_IR(z) = 2.64 + log10(f_syn^ULIRG / f_syn^SMG(z))  
  > "The fraction of cosmic ray energy that is emitted via synchrotron radiation can then be written as" (SMGs Compared to Local ULIRGs)
   - parameter: B = 1.0 mG for both SMGs and ULIRGs; R_eff = 1.0 kpc (SMG), 250 pc (ULIRG); log L_IR 12.5 (SMG), 12.0 (ULIRG)  
  > "we adopt equal magnetic field strengths of $B=1.0\,$mG for SMGs and ULIRGs" (SMGs Compared to Local ULIRGs); "we adopt a typical effective radius for the dust emission in SMGs of $1.0\,$kpc" (SMGs Compared to Local ULIRGs)
   - assumption: All star formation dust-obscured; same cosmic-ray loss processes dominate in both populations; SMG population non-evolving  
  > "we will assume that all star formation is dust-obscured in both populations, and that the same physical processes for cosmic ray energy loss dominate." (SMGs Compared to Local ULIRGs)
   - fitting: _not stated_
   - validation: benchmark model recovers SMG normalization and slight gamma ~ -0.05, marginally consistent with data  
  > "It is clear that our benchmark model recovers the correct normalization of the FIRRC for SMGs." (SMGs Compared to Local ULIRGs)

## Software

- **source finder of (cite: mohanrafferty2015) (name not given in the text)** : source detection in the 610 MHz mosaic and peak/integrated/aperture flux densities of stacks  
  > "to obtain peak, integrated, and aperture flux densities." (Radio Stacking); "Source detection was performed using" (Radio Observations)
- **SED-fitting code of (cite: dacunha2008; dacunha2015; battisti2019) (name not given in the text)** : UV-to-radio SED fits for photometric redshifts, L_FIR and physical properties (applied by Dudzeviciute et al.)  
  > "which is designed to fit the full UV-to-radio SED of star-forming galaxies." (SMG Redshifts and Physical Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMGs with 1.4 GHz detection (>=4 sigma) out of 706 | 273 (39%) | not stated | count | 1 | In total, 273 out of the 706 SMGs in the 1.4-GHz coverage of AS2UDS (39%) can be cross-matched to a radio counterpart detected at |
| SMGs also detected at 610 MHz | 45 | not stated | count | 1 | We additionally detect 45 SMGs down to a $4\sigma$ threshold in the shallower 610 MHz observations. |
| median 610-1400 MHz spectral index (two-band detections) | -0.77 | +0.05/-0.03 | dimensionless | 2 | We find a typical spectral index between 610 and 1400 MHz of $\alpha = -0.77_{-0.03}^{+0.05}$ |
| stacked 610-1400 MHz spectral index of 1.4-GHz-only sources | -0.81 | +0.20/-0.23 | dimensionless | 2 | The typical stacked $610-1400\,$MHz spectral index is then found to be $\alpha = -0.81_{-0.23}^{+0.20}$. |
| median q_IR of radio-detected SMGs | 2.10 | 0.02 | dimensionless | 3 | For the full radio-detected subsample, we find a median $q_\text{IR} = 2.10 \pm 0.02$. |
| radio-excess AGN in full sample | 12 (1.8 +/- 0.5 % of SMGs) | 0.5 percentage points | count | 4 | we find 12 radio-excess AGN within the full AS2UDS sample; Overall, $1.8 \pm 0.5 \%$ of SMGs therefore hosts a radio-excess AGN |
| mean stacked q_IR, full AS2UDS sample | 2.20 | 0.03 | dimensionless | 5 | For the full AS2UDS sample, we find a mean $q_\text{IR,full} = 2.20 \pm 0.03$, where the error represents the bootstrapped variation among the stacks. |
| mean stacked q_IR, luminosity-limited sample | 2.26 | 0.02 | dimensionless | 5 | For the luminosity-limited sample, we find a similar value of $q_\text{IR,lum} = 2.26 \pm 0.02$, although across only five redshift bins. |
| offset of SMG FIRRC from local correlation | 0.44 | 0.04 | dex | 5 | the FIRRC for our AS2UDS SMGs is offset from the local correlation for star-forming galaxies by $0.44\pm0.04\,$dex (a factor of $2.8\pm0.2$) |
| gamma, radio-detected full sample | -0.01 | 0.03 | dimensionless | 6 | we find a lack of redshift-evolution, with a best fit solution of $\gamma_\text{full} = -0.01\pm0.03$. |
| gamma, radio-detected luminosity-limited sample | -0.26 | 0.06 | dimensionless | 6 | we do find an apparent evolution, and measure $\gamma_\text{lum} = -0.26 \pm 0.06$. |
| gamma from stacks (full; luminosity-limited) | 0.02; -0.02 | 0.06; 0.16 | dimensionless | 6 | with the full sample following a trend given by $\gamma_\text{full} = 0.02 \pm 0.06$, and the luminosity-limited sample having a best fit of $\gamma_\text{lum} = -0.02 \pm 0.16$. |
| 3 sigma upper limit on redshift evolution over 1.5<=z<=4.0 | <= 0.08 | not stated | dex | 6 | (a $3\sigma$ upper limit of $\leq 0.08\,$dex across this $\sim3\,$Gyr period) |
| slope of q_IR vs L_FIR (stacks) | 0.16 | 0.10 | dimensionless | 7 | A linear fit through the stacked datapoints indicates a slope of $\beta = 0.16 \pm 0.10$ |
| slope of q_IR vs SFR (stacks) | 0.07 | 0.10 | dimensionless | 7 | no correlation between $q_\text{IR}$ and star-formation rate exists (slope of $\beta = 0.07 \pm 0.10$) |
| integrated-to-peak flux ratio of 1.4 GHz stacks | 1.64 | 0.08 | dimensionless | 5 | while the real data indicate a much higher value of $S_\text{int} / S_\text{peak} = 1.64 \pm 0.08$. |
| mock-stack Delta q_IR using integrated flux | -0.05 | 0.08 | dex | 5 | we find $\Delta q_\text{IR} = -0.05 \pm 0.08$ for the integrated flux density. |
| median log L_FIR with / without mid-IR power law | 12.54 / 12.33 | +0.07/-0.04 ; +0.02/-0.03 | log10 Lsun | 0 | We find the median $8-1000\,\mu$m luminosity to be $\log_{10} L_\mathrm{FIR} = 12.54_{-0.04}^{+0.07}\,L_\odot$ and $\log_{10} L_\mathrm{FIR} = 12.33_{-0.03}^{+0.02}\,L_\odot$ for sources with and without a mid-infrared power-law, respectively. |
| implied SMG magnetic field strength | ~0.2 | not stated | mG | 8 | this implies that SMGs likely have magnetic fields of $B\sim0.2\,$mG |

## Qualitative findings

- No q_IR trend with L_FIR, SFR, M_star, M_dust, T_dust or R_eff at 2 sigma or greater  
  > "None of the six parameters explored show any hint of a correlation with $q_\text{IR}$ at a $2\sigma$ or greater level." (Correlations with Physical Properties)
- Radio-selected samples show q_IR evolution while the submm-selected AS2UDS does not; AGN contamination alone is judged insufficient to explain this  
  > "Overall, an enhanced AGN contribution at high-redshift alone is therefore unlikely to fully account for the observed evolution in the FIRRC seen in radio surveys" (The FIRRC in Radio-selected Samples)

## Claim tuples

- H: Is the FIRRC of submm-selected SMGs offset from the local correlation once radio-undetected SMGs are included? | E: Median stacking of radio-detected and undetected AS2UDS SMGs in redshift bins in the 1.4 GHz map, converting to q_IR | R: q_IR = 2.20 +/- 0.03 versus local 2.64, an offset of 0.44 +/- 0.04 dex | F: SMGs lie below the local correlation for normal star-forming galaxies and ULIRGs | **supported**
- H: Does q_IR evolve with redshift for SMGs between z = 1.5 and 4? | E: Fit (1+z)^gamma to detected sources and to stacks in redshift bins | R: gamma = 0.02 +/- 0.06 (full stacks) and -0.02 +/- 0.16 (luminosity-limited stacks); detected luminosity-limited sample gives -0.26 +/- 0.06 attributed to selection | F: No redshift evolution after accounting for radio non-detections | **supported**
- H: Does q_IR depend on SMG physical properties? | E: Stack in bins of L_FIR, SFR, M_star, M_dust, T_dust, R_eff and fit slopes | R: All slopes consistent with zero, e.g. beta = 0.16 +/- 0.10 for L_FIR | F: The FIRRC is robust across the sampled property range | **supported**
- H: Can radio AGN explain the offset or the lack of evolution? | E: Radio-excess threshold q_IR <= 1.55, plus VLBI-based AGN-fraction argument | R: 12 radio-excess AGN (1.8 +/- 0.5 %); stacked offset persists | F: The offset is attributed to strong magnetic fields (B >~ 0.2 mG), high ISM density and secondary cosmic rays rather than AGN | **supported**
- H: Why do local ULIRGs follow the local FIRRC while SMGs are offset? | E: Cosmic-ray cooling-time model with benchmark B, n_ISM, size and L_IR for ULIRGs and SMGs | R: Benchmark model recovers SMG normalization and a nearly flat q_IR(z) | F: ULIRG compactness and higher ISM density explain the different correlation | **partially**

## Reasoning

- Why this data: A homogeneously selected, far-infrared-based SMG sample avoids radio selection bias and reduces AGN contamination  
  > "The cleanest way of studying any evolution in the FIRRC is therefore to start from a sample where the selection is well understood, and where radio AGN are less of a complicating factor." (Introduction)
- Why this method: Stacking is used to include the majority of SMGs not individually detected in the radio  
  > "In this work, we employ a stacking technique in order to obtain a census of the typical radio properties of the AS2UDS sample." (Radio Stacking)
- Alternative: Peak flux densities rejected for 1.4 GHz stacks in favour of integrated fluxes (peak underestimates by 0.74 +/- 0.11 and biases q_IR by 0.13 +/- 0.06)  
  > "As such, total fluxes from Gaussian fits constitute a better measurement of the true radio flux of the AS2UDS SMGs than peak flux densities." (Stacking)
- Alternative: Mean stacking and other AGN thresholds (including redshift-dependent) considered; median and fixed threshold adopted  
  > "We have further investigated adopting other possible thresholds for identifying radio-excess sources" (AGN in AS2UDS); "In this work, we adopt the latter, as the median is considerably less affected by outliers in the underlying distribution of flux densities" (Stacking)
- How they decided it was enough: Bins require stacked SNR >~ 10 so integrated fluxes are reliable  
  > "We ensure the stacks are all of sufficient signal-to-noise ($\text{SNR}\gtrsim10$), such that reliable integrated flux measurements can be made" ((A lack of) Redshift Evolution in the FIRRC)
- Limitation (authors): The SED-fitting code does not allow for an AGN contribution, so FIR luminosity may be slightly boosted for mid-IR power-law sources  
  > "We caution that does not allow for any contribution from an AGN to the overall SED." (SMG Redshifts and Physical Properties)
- Limitation (authors): Spectral indices are lacking for most of the radio sample, so a fixed alpha = -0.80 is used  
  > "which is the lack of available spectral indices for the majority of our radio sample." ((A lack of) Redshift Evolution in the FIRRC)
- Limitation (authors): Radio-detected median q_IR is biased toward radio-bright sources  
  > "However, this median value for AS2UDS is biased towards radio-bright sources as a result of selection." (The FIRRC for SMGs)
- Caveat (inferred, ours): Stacked integrated fluxes depend on an unnamed source finder and on mock-source tests described only in outline
- Caveat (inferred, ours): Stack bin definitions and uncertainty propagation of L_FIR and photometric z are not given
- Caveat (inferred, ours): Fixed alpha = -0.80 for most sources can shift q_IR by up to ~0.2 dex at z=3
- Caveat (inferred, ours): Cosmic-ray model uses unconstrained B and n_ISM, so the physical interpretation is degenerate
- Caveat (inferred, ours): Results depend heavily on SED-derived L_FIR and photometric redshifts from another paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced 1.4 GHz VLA mosaic and 610 MHz GMRT map
- Missing: AS2UDS ALMA catalog with SED-derived z and L_FIR (from Stach et al. 2019 and Dudzeviciute et al. 2020)
- Missing: Bin definitions, stacking and fitting code, mock-source code
- Missing: Value of ISM densities and full cooling model implementation
- Data volume (inferred): Mainly catalogs and two radio mosaics (tens of GB); ALMA visibilities not re-reduced here
- Score (inferred): 2/5, Numeric results are given, but the radio maps, SED-derived tables, source finder settings and bin definitions rely on in-prep or other papers and no code is released
- Rediscovery candidate: no, The paper does not state that the data are public and key inputs (VLA map, per-source L_FIR) come from unpublished or other-paper products

## Links

- Method: (cite: stach2019) (ALMA AS2UDS survey strategy, data reduction and catalog)
- Method: (cite: dudzeviciute2019) (SED fitting, redshifts, L_FIR and radio flux densities for AS2UDS)
- Method: (cite: ibar2009) (GMRT 610 MHz data reduction and imaging)
- Method: (cite: mohanrafferty2015) (source-extraction code used for radio detection and stacked fluxes)
- Method: (cite: thomson2019) (1.4 GHz VLA summary, source-size method and spectral-break modelling)
- Companion: (cite: algera2020) (Radio-selected FIRRC analysis with similar AGN conclusions)
- Companion: (cite: thomson2014) (ALESS FIRRC comparison sample)
- Related: AS2UDS
- Related: S2CLS
- Related: ALESS
- Related: X-UDS
- Related: VLA-COSMOS

## Checks

```json
{
 "quotes": 117,
 "quotes_ok": 117,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 73,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
