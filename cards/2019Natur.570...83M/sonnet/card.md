# A cool accretion disk around the Galactic Centre black hole

`2019Natur.570...83M` | Nature 2019 | first author: Murchikova, Elena M. | arXiv: 1906.08289 | DOI: 10.1038/s41586-019-1242-z

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Is there a cool (10^4 K) ionized gas disk in the accretion flow of Sgr A* at 10-10^5 Schwarzschild radii, detectable in the H30alpha recombination line?  
  > "The other issue is the lack of model-independent probes of accretion flow at intermediate radii (between few and $\sim 10^5 R_\mathrm{s}$)" (abstract)
- Target **Sgr A***: coordinates RA 17:45:40.0359, DEC -29:00:28.169 (J2000)  
  > "Observations were centered on Sgr A\*: RA 17:45:40.0359, DEC -29:00:28.169 (J2000)." (Observations); "$D_\mathrm{H30\alpha} = 8.0$ kpc" (Velocity Integrated Line Flux and Volume Emission Measure.); z/distance 8 kpc  
  > "Observations were centered on Sgr A\*: RA 17:45:40.0359, DEC -29:00:28.169 (J2000)." (Observations); "$D_\mathrm{H30\alpha} = 8.0$ kpc" (Velocity Integrated Line Flux and Volume Emission Measure.); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00311.S
- bands: Band 6  
  > "They were conducted in receiver Band 6; the correlator was configured in the time division mode (TDM) with 4 spectrometers." (Observations)
- frequencies and spectral setup: 4 TDM spectral windows, 1875 MHz each, 31.25 MHz channels; line windows at 231.058 and 232.608 GHz (overlapping); continuum windows at 217.801 and 215.801 GHz  
  > "we overlapped two spectral windows centred at 231.058 GHz and 232.608 GHz (Supplementary Fig. 1). The remaining two spectral windows centred at 217.801 and 215.801 GHz were used to image the SgrA\* continuum." (Observations)
- continuum bandwidth: _not stated_
- arrays: 43 12m antennas  
  > "The data were taken with 43 12m antennas" (Observations)
- configurations: C40-5 (mostly) and one execution in C36-2/3  
  > "The observations were done primarily in ALMA configuration C40-5 with baselines up to 1.1 km and one execution was done in configuration C36-2/3 with baselines up to 460 m." (Observations)
- baselines: _not stated_
- angular resolution: 0.29 x 0.22 arcsec^2, PA = 6 deg  
  > "The synthesized beam size was $0.29 \times 0.22 \, \mathrm{arcsec}^2$ with PA$=6$ degrees." (Observations)
- max recoverable scale: ~3.4 arcsec (C40-5), ~10.7 arcsec (C36-2/3)  
  > "For the C40-5 telescope configuration, good flux recovery is expected out to scales of $\sim$ 3.4 arcsec and for C36-2/3 it is expected up to $\sim$ 10.7 arcsec." (Observations)
- sensitivity: 0.3 mJy/beam per 40 km/s channel  
  > "The 1$\sigma$ (rms) sensitivity was 0.3 mJy beam$^{-1}$ in each 40 km s$^{-1}$ channel." (Observations)
- time on source: 1.6 hours on target (5.1 hours total)  
  > "The integration time on target was 1.6 hours." (Observations)
- observing dates: April and August 2016  
  > "obtained in April and August, 2016" (Observations)
- pi or archival as stated: _not stated_
- Line: H H30alpha (n=31->30) (231.9 GHz)
- Other facility **VLT/Keck near-IR Br-gamma limit (A. Ciurlo et al., in prep.)**: Br gamma limit S<0.1 mJy within 0.3 arcsec of Sgr A*, used to constrain amplification  
  > "Galactic Centre observations by A. Ciurlo et al (in prep.), which sets an approximate limit $S_\mathrm{Br \gamma}< 0.1$ mJy" (main text)
- Other facility **ALMA Cycle 4 data**: Independent check; similar line recovered, flux 10% larger  
  > "The integrated line flux was larger by $10 \%$ compare to the Cycle 3 data presented here." (Reliability)
- External data: H30alpha and Br gamma emissivities  
  > "The emissivity of H$30\alpha,$ $\epsilon_{\textrm{H}30\alpha } (T,n),$ is tabulated for uniform media of constant density with no background radiation (cite: Storey.Hummer95)." (main text) [from (cite: Storey.Hummer95)]
- External data: K-band extinction A_K=2.46  
  > "Here $A_{K}=2.46$ is the extinction toward the Galactic Centre at the frequency of $\mathrm{Br \gamma}$ (cite: Witzel18)" (main text) [from (cite: Witzel18)]
- External data: Black hole mass 4e6 Msun  
  > "$M_\mathrm{SgrA*} \simeq 4 \times 10^6 M_{\odot}$ resides at the centre of our galaxy (cite: Boehle16; Gravity18)" (main text) [from (cite: Boehle16; Gravity18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data re-reduced after delivery  
  > "Following delivery of data products, the data were re-reduced and imaged using the Common Astronomy Software Applications package (CASA)." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: none, to preserve astrometry  
  > "We did not perform self-calibration to preserve astrometry." (Observations)

### Imaging

- task: TCLEAN  
  > "clean the image with the CASA task TCLEAN" (Continuum Subtraction)
- deconvolver: _not stated_
- weighting robust: Robust = 0.5  
  > "The images were produced with the parameter Robust = 0.5." (Continuum Subtraction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction per spectral window with iteratively identified line-free channels; then spectral window alignment by subtracting a line a*nu+b  
  > "Secondly, we performed u-v continuum subtraction using the identified channels, imaged the data again, and marked the channels with weak line features" (Continuum Subtraction)
- line free channels: chosen within <1 arcsec of Sgr A*, requiring residual slope <30 mJy across the window; actual list not given  
  > "we identified the reasonable list of the line-free channels only within $<1$ arcsec around Sgr A\*." (Continuum Subtraction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- BLR-like disk spectral modelling method  
  > "we can model the geometry and dynamics of the gas emission using a method applied to the optical H$\beta$ broad emission line (cite: Pancoast14a; Pancoast18)." (BLR-like Ensemble of Clouds. Modelling.) [from (cite: Pancoast14a; Pancoast18)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel lists per spectral window
- CASA version
- Pipeline/calibration details and flux calibrator choice per execution
- Aperture center and shape used for the spectrum
- Cell size, image size, deconvolver, masks, and clean threshold
- Line/continuum image weighting beyond robust 0.5
- CARAMEL model priors, sampler and fit settings (code proprietary)
- Details of Br gamma limit derivation (in prep.)

## Analysis recipe

1. **Continuum subtraction and spectral window alignment**: Iterative uv continuum subtraction per spw using line-free channels, tclean imaging, alignment of overlapping channels  
  > "When steps one through three are performed correctly in each spectral window the resulting continuum subtracted spectra will be aligned" (Continuum Subtraction)
   - software: CASA
   - parameter: Robust = 0.5; residual slope <30 mJy  
  > "slopes of no more than $< 30$ mJy over the width of the spectral window after the u-v continuum subtraction" (Continuum Subtraction)
   - fitting: _not stated_
   - validation: Variations from different line-free sets <=7%; independent executions, calibrator source and Cycle 4 data checked  
  > "The variations in the value of each point in the resulting line spectra were $\leq 7\%.$" (Continuum Subtraction)
2. **Extract spectrum and velocity-integrated line flux, map red/blue emission**: Spectrum integrated in 0.63x0.51 arcsec aperture; integral under line gives 3.8 Jy km/s  
  > "The spectrum is integrated within an aperture of $0.63 \times 0.51 \, \mathrm{arcsec}^2.$" (main text)
   - software: CASA, Python
   - fitting: _not stated_
   - validation: Larger apertures add no flux; emission outside <10%  
  > "Emission outside of this region, if any, is $<10\%$ of that inside." (Estimation of Uncertainties)
3. **Derive emission measure, amplification factor, disk density, mass, accretion rate**: Recombination-line emissivity relation with Storey & Hummer emissivity; amplification from Br gamma limit; Shakura-Sunyaev uniform disk and BLR-like cloudlet models  
  > "we obtain the effective volume emission measure of the ionized hydrogen in the disk" (main text)
   - software: Mathematica
   - parameter: T=1e4 K, emissivity 1.25e-31 erg/s cm^3, D=8 kpc, Rmax=0.23 arcsec, Rmin=0.07 arcsec  
  > "an isothermal disk at $T=10^4~\mathrm{K}$ with an outer radius $R_\mathrm{max} = 0.23$ arcsec and an inner radius $R_\mathrm{min} = 0.07$ arcsec" (Disk of a uniform density)
   - assumption: Alpha = 0.1, chi = 1 (uniform disk) or 1/4 (cloudlets), cloudlet radius r = 1e-3 Rmax  
  > "Here we used $r=10^{-3} R_\mathrm{max} = 9 \mu \mathrm{pc}$ as a characteristic size of cloudlets" (BLR-like Ensemble of Clouds.)
   - fitting: _not stated_
   - validation: Ionization equilibrium check against Sgr A* plus Wolf-Rayet star ionizing flux  
  > "Thus we conclude that the ionizing photon flux required to keep the disk ionized is a collective effect of Sgr A\* and nearby orbiting stars." (Ionization Equilibrium)
4. **Model the line spectrum with a BLR-like disk**: CARAMEL fit of the H30alpha spectrum, BH mass 4e6 Msun, outer radius <10 light days  
  > "The model assumes an ionizing photon source located at the location of SgrA\*, an outer radius of emission less than 10 light days (corresponding to the spectrum aperture), and a black hole mass of $4.0 \times 10^6 {M_\odot}$." (BLR-like Ensemble of Clouds. Modelling.)
   - software: CARAMEL
   - fitting: _not stated_
   - validation: Results consistent even if BH mass free or larger outer radius  
  > "a result that is consistently inferred even if the black hole mass is left as a free model parameter or the outer radius of emission is larger than 10 light days" (BLR-like Ensemble of Clouds. Modelling.)

## Software

- **CASA** : Data re-reduction, imaging, uv continuum subtraction, tclean  
  > "the data were re-reduced and imaged using the Common Astronomy Software Applications package (CASA)" (Observations)
- **CARAMEL** : Modelling the line spectrum with a BLR-like disk  
  > "we used the proprietary Code for AGN Reverberation and Modeling of Emission Lines (CARAMEL, (cite: Pancoast14a))" (Data availability statement)
- **Python/astropy/Mathematica** : Analysis and plotting  
  > "We use astropy, python and Mathematica for plotting and data analysis." (Data availability statement)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity-integrated H30alpha flux | 3.8 | about 20% per point plus 10% from alignment | Jy km/s | 2 | From $S \Delta V_{H30\alpha}=3.8 \, \textrm{Jy} \, \textrm{km} \, \textrm{s}^{-1},$ |
| Full line width | 2200 | not stated | km/s | 2 | with a full velocity width of $2,200 \, \mathrm{km \, s^{-1}}$ (Fig. 1a) |
| Effective volume emission measure | 1.8e60 | not stated | cm^-3 | 3 | \mathscr{M}{\mathrm{EM}}  = 1.8 \times 10^{60} \, \textrm{cm}^{-3}. |
| Amplification factor M | >=80 | not stated | dimensionless | 3 | The relation above implies that H30$\alpha$ has to be amplified by a factor $\mathscr{M}\gtrsim 80.$ |
| Uniform-disk accretion rate | 2.7e-10 | not stated | Msun/yr | 3 | \dot{M} (R_\mathrm{mean} )= 2.7 \times 10^{-10} |
| Uniform-disk mass | 1.0e-4 | not stated | Msun | 3 | M= 1.0 \times 10^{-4} |
| Position angle of line of nodes | 64 | not stated | degrees | 2 | The position angle of the line of nodes is 64 degrees north through east. |
| Ionizing photon rate Q0 | 4.6e45 | not stated | s^-1 | 3 | Q_0 =4.6 \times 10^{45}  \left( \frac{\mathscr{M}}{100}\right)^{-1} \,\mathrm{s^{-1}} |

## Qualitative findings

- Double-peaked H30alpha emission with red side NE and blue side SW, consistent with a rotating 1e4 K disk with a central hole  
  > "The red-shifted side is displaced to the north-east, while the blue-shifted side is displaced to the south-west." (abstract)

## Claim tuples

- H: A cool ionized disk exists within ~2e4 R_Sch of Sgr A* | E: ALMA Band 6 imaging of H30alpha with continuum subtraction at 1:2000 line-to-continuum ratio | R: Double-peaked line, 2200 km/s wide, offsets of 0.11 arcsec | F: Rotating ~1e4 K disk detected | **supported**
- H: The disk mass and accretion rate can be constrained | E: Emission measure with maser amplification from Br gamma limit | R: Mass 1e-4 to 1e-5 Msun; Mdot ~2.7e-10 Msun/yr (uniform) | F: Tenuous disk, requires replenishment on >~120 yr | **partially**

## Reasoning

- Why this data: H30alpha chosen because it is free from strong molecular emission  
  > "This line was selected because it is free from strong molecular emission" (main text)
- Why this method: _not stated_
- Alternative: Bipolar outflow disfavoured but not excluded  
  > "This scenario is disfavored in our modelling, however it cannot be completely ruled out." (BLR-like Ensemble of Clouds. Modelling.)
- How they decided it was enough: _not stated_
- Limitation (authors): Line could be unlucky combination of molecular lines or foreground absorption  
  > "the possibility remains that the double-peaked line profile we see is an unlucky combination of molecular lines or is partially due to a foreground absorption" (main text)
- Caveat (inferred, ours): Continuum subtraction on 1:2000 contrast with ad hoc channel selection
- Caveat (inferred, ours): Amplification M>=80 rests on unpublished Br gamma limit
- Caveat (inferred, ours): Disk model parameters assume values not constrained by data
- Caveat (inferred, ours): Cycle 3 spectrum of marginal significance with narrow window coverage

## Reproducibility

- Data public (paper): Publicly available on ALMA archive  
  > "The data is publicly available on ALMA archive." (Data availability statement)
- Products in archive: _not stated_
- Code: CARAMEL not released  
  > "therefore we are not releasing the code with this paper." (Data availability statement)
- Missing: Line-free channel list
- Missing: CASA version and imaging parameters
- Missing: CARAMEL code
- Missing: Br gamma limit details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and the general recipe are given, but critical continuum-subtraction channel choices and the proprietary model are missing.
- Rediscovery candidate: no, Key subtraction settings missing and result sensitive to the subtraction.

## Links

- Method: (cite: Pancoast14a) (CARAMEL BLR modelling code)
- Companion: (cite: Gillessen18) (G2 drag force/density constraint)
- Related: ALMA Cycle 4 and Cycle 5 Sgr A* H30alpha observations

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 44,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
