# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...917...99Y\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA Observations of the Sub-kpc Structure of the Host Galaxy of a $z=6.5$ Lensed Quasar: A Rotationally-Supported Hyper-Starburst System at the Epoch of Reionization

## Abstract

We report ALMA observations of the dust continuum and \[C ii\] emission of the host galaxy of J0439+1634, a gravitationally lensed quasar at $z=6.5$. Gravitational lensing boosts the source-plane resolution to $\sim0.15\ensuremath{''}$ $(\sim0.8\text{ kpc})$. The lensing model derived from the ALMA data is consistent with the fiducial model in (cite: fan19) based on *HST* imaging. The host galaxy of J0439+1634 can be well-fitted by a Sérsic profile consistent with an exponential disk, both in the far-infrared (FIR) continuum and the \[C ii\] emission. The overall magnification is $4.53\pm0.05$ for the continuum and $3.44\pm0.05$ for the \[C ii\] line. The host galaxy of J0439+1634 is a compact ultra-luminous infrared galaxy, with a total star formation rate (SFR) of $1.56\times10^{3}M_\odot/\text{year}$ after correcting for lensing and an effective radius of $0.74$ kpc. The resolved regions in J0439+1634 follow the “\[C ii\] deficit," where the \[C ii\]-to-FIR ratio decreases with FIR surface brightness. The reconstructed velocity field of J0439+1634 appears to be rotation-like. The maximum line-of-sight rotation velocity of 130 km/s at a radius of 2 kpc. However, our data cannot be fit by an axisymmetric thin rotating disk, and the inclination of the rotation axis, $i$, remains unconstrained. We estimate the dynamical mass of the host galaxy to be $7.9\sin^{-2}(i)\times10^{9}M_\odot$. J0439+1634 is likely to have a high gas-mass fraction and an oversized SMBH compared to local relations. The SFR of J0439+1634 reaches the maximum possible values, and the SFR surface density is close to the highest value seen in any star-forming galaxy currently known in the universe.

# Introduction

In the past two decades, more than 200 quasars at $z>6$ have been discovered (cite: matsuoka16; matsuoka18a; matsuoka2018b; matsuoka19; venemans13; venemans15; yang19a; yang20; wang17; wang19a; jiang16; banados16; banados18).

Studies of the quasar host galaxies provide crucial knowledge about the co-evolution of supermassive black holes (SMBHs) with their host galaxies and environment in the early universe. Detecting the host galaxies of high-redshift quasars is challenging at rest-frame ultraviolet to near-infrared wavelengths, where the emission from the central quasar overwhelms the host galaxy (cite: mechtley12; marshall20). As such, information about quasar host galaxies is mostly from the far-infrared (FIR) and sub-millimeter (sub-mm) regime (cite: riechers09; wangran08; wangran10; venemans12). The dust continuum and atomic and molecular emission lines (for example, the \[C ii\] fine structure line and CO rotational lines) contain a wealth of information about the interstellar medium (ISM), including the dust mass and temperature (cite: beelen06; Schreiber18), the atomic and molecular gas mass (cite: weib05; bolatto13), and the gas-phase metallicity (cite: rigopoulou18). Spatially resolved line emission also directly probes the gas-phase kinematics of quasar host galaxies and provides the only current way to measure their dynamical masses (cite: walter09). The total-infrared (TIR) luminosity is widely used to estimate the star formation rate (SFR) (cite: murphy11), assuming that the cool dust in the quasar host is dominantly heated by star formation (cite: beelen06; leipski14).

With unprecedented sensitivity and resolving power, the Atacama Large Millimeter/Submillimeter Array (ALMA) has greatly improved our understanding of high-redshift quasars.

To date, several tens of quasars at $z>6$ have been observed by ALMA, including about 15 at $z>6.5$. These observations led to an overall picture of the high-redshift quasar population: most of the high-redshift quasars are hosted by infrared-luminous, gas rich galaxies (cite: decarli18; venemans18; wang19b; shao19), indicating active star formation $(\text{SFR}\gtrsim10^2M_\odot\text{ yr}^{-1})$. The kinematics of the bright \[C ii\] emission line constrains the dynamical masses of quasar host galaxies. Compared to the local $M_\text{BH}-M_\text{host}$ relation (cite: kh13), SMBHs in quasars at $z\gtrsim6$ are oversized (cite: venemans16; decarli18; wangran19). While SMBHs might grow earlier than their hosts at high redshift, this difference may be a result of selection effects, i.e., current quasar surveys are biased toward luminous quasars, which have massive SMBHs (cite: willott15; izumi19).

At $z>6$, quasar host galaxies usually have sizes of $\sim2 - 4\text{ kpc}$ (cite: decarli18), although they can be as compact as $\sim1\text{ kpc}$ (cite: venemans17). Most ALMA observations of high-redshift quasars use beam sizes of $\gtrsim 0.3\ensuremath{''}$, which marginally resolve these quasar host galaxies. These hosts have a variety of morphologies, ranging from a regular Gaussian profile (cite: shao17; venemans18) to highly irregular, indicating an on-going merging system (cite: banados19; neeleman19). In a recent study, (cite: venemans19) reported 400-pc resolution imaging of a quasar host galaxy at redshift 6.6, which shows complex structures of dust continuum and \[C ii\] emission, including cavities with sizes of $\sim 0.5 \text{ kpc}$. The authors propose that these cavities might be relevant to the energy output of the central active galactic nucleus (AGN). Sub-kpc resolution is thus necessary to the investigation of the structures in high-redshift quasars and to the understanding of SMBH-host coevolution.

Gravitational lensing acts as a natural telescope, significantly enhancing the angular resolution and the sensitivity of observations (cite: hezaveh16; litke19; inoue20; cheng20; spilker20). In (cite: fan19), we reported the discovery of a gravitationally lensed quasar at $z=6.51$, J043947.08+163415.7 (hereafter J0439+1634). High-resolution images taken by *Hubble Space Telescope* (*HST*) reveal the multiple images of the quasar generated by gravitational lensing. The lensing model based on *HST* data suggests that J0439+1634 is a naked-cusp lens with three images, with a total magnification of $51.3\pm1.4$. J0439+1634 is the only known lensed quasar at $z>5$ to date and provides an excellent chance to study a high-redshift quasar in enhanced spatial resolution due to its large lensing magnification.

Here we report the sub-mm continuum and \[C ii\] $158~\mu\text{m}$ emission line of J0439+1634 observed by ALMA at a resolution of $\sim 0.3\ensuremath{''}$. With the help of lensing, we reach a physical resolution of $\sim0.8 \text{ kpc}$.

We describe our data in Section [2](#sec:data). In Section [3](#sec:lensing), we describe the measurement of the dust continuum and \[C ii\] emission line, including the lens modeling and the reconstruction of the velocity field. We present the physical properties of J0439+1634 in Section [4](#sec:physical) and discuss their implications for the evolutionary state of the quasar host galaxy in Section [5](#sec:discuss). We summarize this paper in Section [6](#sec:conclude). Throughout this paper, we use a $\Lambda$CDM universe with $H_0=70 \text{ km s}^{-1}\text{Mpc}^{-1}$, $\Omega_\text{M}=0.3$, and $\Omega_\Lambda=0.7$.

# Data

J0439+1634 was observed in ALMA Band 6 under configuration C43-5 in October 2018. The configuration contains 48 12-m antennas, which has a maximum baseline of 1.24 km. We tuned the four 1.875 GHz-wide spectral windows (SPWs) at 238.593 GHz, 236.718 GHz, 252.206 GHz, and 253.894 GHz with channel widths of 15.625 MHz, 15.625 MHz, 7.8125 MHz, and 7.8125 MHz, respectively. The \[C ii\] emission line falls in the third SPW. The on-source exposure time is 99 minutes. We use J0510+1800 as the bandpass calibrator and J0440+1437 as the phase calibrator. The C43-5 observations are a part of Program 2018.1.00566.S, which aims at a mapping the dust continuum and \[C ii\] emission line to a spatial resolution of $0.03\ensuremath{''}$. The high-resolution observation with configuration C43-8 is not completed at the time of this paper’s writing.

![image](cont.pdf) ![image](mom0.pdf) ![image](mom1.pdf) ![image](mom2.pdf)

We reduce the ALMA data using the Common Astronomy Software Applications (CASA) version 5.6.1 (cite: casa). We use the task UVCONTSUB [^1] to fit a linear function to the line-free channels, which models the continuum, and subtract the continuum model to obtain the line-only visibility. We then use the continuum data to perform phase self-calibration and apply the self-calibration model to the line-only data. We clean the continuum and line data with the CASA task TCLEAN using Briggs weighting, setting robust $=0.5$. The synthesized beam has a size of $0.31\ensuremath{''}\times0.27\ensuremath{''}$ and a position angle of $39.4$ degrees. Figure [1](#fig:clean) shows the cleaned image of the dust continuum and the zeroth, first, and second moments of the \[C ii\] emission. J0439+1634 is clearly resolved as an arc-like shape, which is typical for lensed galaxies. The zeroth moment (integrated flux) of the \[C ii\] line is more extended than the continuum flux. The first moment (mean velocity map) shows ordered motion.

We extract the continuum and \[C ii\] fluxes of J0439+1634 with a $2.0\ensuremath{''}$ diameter aperture, which gives $S_\text{245 GHz}=16.0\pm0.1 \text{ mJy}$ for the continuum and $F_\text{[C\,{\sc ii}]}=14.5\pm0.2\text{ Jy km s}^{-1}$ for the integrated \[C ii\] flux. We also fit a Gaussian profile to the \[C ii\] line using the CASA task SPECFIT. The \[C ii\] line is centered at $252.7744\pm0.0011$ GHz with an FWHM of $270.0\pm2.8 \text{ km s}^{-1}$, which gives a redshift $z_\text{[C\,{\sc ii}]}=6.51871\pm0.00003$. In the rest of the paper, we set 252.7744 GHz as the rest frequency for \[C ii\]. Figure [2](#fig:ciiprofile) shows the extracted \[C ii\] line profile, which is well-fitted by a Gaussian function and shows no evidence for an excess redshifted or blueshifted component.

![](ciiprofile.pdf)

# Lensing Model

We use VISILENS (cite: spilker16) to model the visibility of J0439+1634. VISILENS is a parameterized lens modeling tool for interferometry data. In short, VISILENS models the $uv-$plane response of a lens system and obtains the posterior distributions of model parameters using Markov Chain Monte Carlo (MCMC).

+:--------------------------------+------------------------:+-----------------:+-----------------:+-----------------------------:+-----------------:+-----------------:+
|                                 | Default$^{1}$                                                 | ALMA only                                                          |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| Parameters                      | lens                    | Continuum        | \[C ii\]         | lens                         | Continuum        | \[C ii\]         |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| Redshift                        | \[0.67\]                | \[6.5187\]       | \[6.5187\]       | \[0.67\]                     | \[6.5187\]       | \[6.5187\]       |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $\Delta \text{RA} ~('')$ $^{2}$ | $0.459\pm0.002$         | $0.236\pm0.003$  | $0.235\pm0.002$  | $0.409\pm0.004$              | $0.222\pm0.005$  | $0.220\pm0.005$  |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $\Delta \text{Dec} ~('')$       | $-0.050\pm0.001$        | $-0.019\pm0.001$ | $-0.017\pm0.001$ | $-0.058\pm0.002$             | $-0.019\pm0.003$ | $-0.017\pm0.003$ |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| Mass $(M_\odot)$ $^{3}$         | \[$2.06\times10^{10}$\] | \-               | \-               | $(1.95\pm0.03)\times10^{10}$ | \-               | \-               |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $e$ $^{4}$                      | \[0.65\]                | $0.409\pm0.011$  | $0.376\pm0.020$  | $0.641\pm0.007$              | $0.362\pm0.016$  | $0.347\pm0.021$  |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| PA (deg) $^{5}$                 | \[94.58\]               | $-6.9\pm1.2$     | $-0.6\pm1.7$     | $99.75\pm0.34$               | $4.9\pm1.5$      | $3.4\pm2.2$      |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| Flux $^{6}$                     | \-                      | $3.46\pm0.04$    | $4.15\pm0.10$    | \-                           | $3.18\pm0.07$    | $4.16\pm0.10$    |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $R_\text{eff} ~('')$ $^{7}$     | \-                      | $0.136\pm0.002$  | $0.233\pm0.006$  | \-                           | $0.131\pm0.002$  | $0.235\pm0.007$  |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $n$ $^{8}$                      | \-                      | $1.71\pm0.06$    | $0.82\pm0.05$    | \-                           | $1.58\pm0.05$    | $0.91\pm0.05$    |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+
| $\mu$ $^{9}$                    | \-                      | $4.53\pm0.05$    | $3.44\pm 0.05$   | \-                           | $4.90\pm0.10$    | $3.45\pm 0.05$   |
+---------------------------------+-------------------------+------------------+------------------+------------------------------+------------------+------------------+

: Lens model parameters

Table notes: The quantities in the square brackets are fixed. For the lens galaxy, (cite: fan19) use Einstein radius instead of mass. Here we follow the convention in VISILENS. The redshift and the mass of the lens galaxy are degenerate, and the lens parameters in this table gives the same lensing model as (cite: fan19). Besides, note that the uncertainties only include statistical errors, and do not take into account the systematic errors introduced by the model choice (see Section [3.5](#subsec:systematics) for more discussion). $^{1}$ In the default model, the parameters of the lens galaxy, except its position, are fixed to the fiducial model in (cite: fan19). $^{2}$ $\Delta \text{RA}$ and $\Delta \text{Dec}$ are relative to the phase center. $^{3}$ Mass of the lens galaxy. $^{4}$ Ellipticity of the lens or source. $^{5}$ Position angle (from north to east) of the lens or source. $\text{PA}=0$ means that the major axis lies east-to-west. $^{6}$ The source flux, in mJy for the continuum and in Jy km s$^{-1}$ for the \[C ii\] line. $^{7}$ The half-light radius. $^{8}$ The Sérsic index. $^{9}$ The flux magnification.

## Building the Lensing Model

(cite: fan19) built the lensing model of J0439+1634 based on the *HST* image, where they used a singular isothermal ellipsoid (cite: sie) to describe the mass distribution of the lens galaxy. In their fiducial model, the lensing galaxy has a high ellipticity $(e=0.65)$, lies at the west side of the quasar, and generates three quasar images. The position, the ellipticity, and the position angle of the modeled lens galaxy are consistent with the observed *HST* optical image.

The *HST* images have spatial resolution of $\sim 0.075\ensuremath{''}$, which is several times better than the current ALMA data. We thus adopt the lens mass distribution from the fiducial model in (cite: fan19). Specifically, we use an SIE to describe the lens galaxy. The Einstein radius, ellipticity, and position angle of the SIE are fixed to the values in the fiducial *HST* model, while the position of the lens is left free, which accounts for any pointing offsets between *HST* and ALMA. Because the continuum has a higher signal-to-noise ratio (SNR), we first fit the continuum to obtain the best-fit lens position, then apply the lens position when fitting the \[C ii\] emission. We use a Sérsic profile to describe the source, both for the continuum and the \[C ii\] line emission. This model is referred to as the default model in this paper.

For comparison, we also build an alternative model, hereafter referred as the “ALMA-only" model, in which we leave all parameters free when fitting the ALMA data and do not use any information from the *HST* observations. Again, we use an SIE to describe the lens galaxy and a Sérsic profile to describe the source emission, both for the continuum and the \[C ii\] line. We first fit the continuum to obtain the best-fit values of the lens parameters, then apply these values when fitting the \[C ii\] line.

Figure [3](#fig:lensmodel) shows the fitting result of the default model, and Figure [4](#fig:testmodel) illustrates the ALMA-only model. Table [\[tbl:lensparams\]](#tbl:lensparams) summarizes the best-fit parameters for both models.

Despite tiny differences in details, the two models give the same overall lensing structure.

Because the *HST* images have better resolution, we use the default model to derive the properties of J0439+1634 from this point on. We will discuss the systematic errors introduced by the choice of the model in Section [3.5](#subsec:systematics).

![image](J0439_continuum_SIE_1ser_correct_panels.pdf) ![image](J0439_line_rotser_w600_allflux_correct_panels.pdf)

![image](J0439_continuum_SIE_1ser_test_panels.pdf) ![image](J0439_lin_w600_allflux_test_panels.pdf)

In addition to the fiducial model, (cite: fan19) raise two alternative models, in which the lens mass distribution differs significantly from the fiducial model and produces either double or quadruple quasar images. See Figure 4 in (cite: fan19) for more information. The alternative models do not provide suitable fits to the ALMA data. We conclude that the fiducial *HST* model has the correct lensing configuration.

## Dust Continuum

The upper panel of Figure [3](#fig:lensmodel) shows the best-fit dust continuum in the default model. As described in Section [3.1](#subsec:lensgalaxy), in the default model, we fix the deflector galaxy mass distribution to the fiducial model in (cite: fan19) which is based on *HST* imaging, and fit the quasar host galaxy emission in ALMA data as a Sérsic profile. The dirty images are generated with natural weighting to enhance the SNR. The dust continuum of J0439+1634 can be well-fitted by a single Sérsic profile, with a reduced $\chi^2=1.035$. The best-fit Sérsic index is $1.71\pm0.06$ and the half-light radius is $0.136\ensuremath{''}\pm0.002\ensuremath{''}$ ($0.74\pm0.01$ kpc), suggesting a compact, exponential-disk-like profile. (See Section [4.1](#subsec:contcii) for further discussion.) The overall magnification is $4.53\pm0.05$ when averaged over the entire galaxy. Compared to the fiducial *HST* model, the position of the optical quasar deviates from the continuum center by $0.014\ensuremath{''}$. The typical astrometric error for ALMA is about 5% of the resolution, which translates to $\sim0.015\ensuremath{''}$ given a beam size of $\sim 0.3\ensuremath{''}$ (cite: almatech). The positions of the optical quasar and the host galaxy are thus consistent.

The residual map shows some statistically significant structures. The peak of these structures is $4.9\%$ of the peak in the observed dirty image. We expect such features given that we use a simple SIE + Sérsic model and the SNR of the data is high (with natural weighting, the peak SNR in the dirty image is $\sim600$). When we add a Gaussian profile to the source model, where we allow the Gaussian profile to have negative flux, the flux of the Gaussian profile converges to zero within the error. We thus argue that the structures in the residual image cannot be explained by a single bump or void in the source galaxy. The structures might result from an over-simplification of the lens and source model.

## Integrated \[C ii\] Flux

The lower panel of Figure [3](#fig:lensmodel) shows the best-fit result of the \[C ii\] emission in the default model, and Table [\[tbl:lensparams\]](#tbl:lensparams) shows the parameters of \[C ii\] line observations. The reduced $\chi^2$ of the best-fit model is $1.014$.

The best-fit \[C ii\] emission has a Sérsic index of $0.82\pm0.05$, consistent with an exponential $(n=1)$ profile, and a half-light radius of $0.233\ensuremath{''}\pm 0.006\ensuremath{''}$ $(1.27\pm0.03 \text{ kpc})$. The position and the ellipticity of the integrated \[C ii\] emission are consistent with those of the dust continuum within $2\sigma$, while the \[C ii\] line has a smaller Sérsic index and larger half-light radius. This difference suggests that the \[C ii\] line is more diffuse than the dust, as shown in the clean images. The overall magnification of the \[C ii\] emission is $3.44\pm0.05$, which is smaller than that of the dust continuum, mainly because the \[C ii\] profile is more diffused.

Similar to the continuum, a Sérsic profile captures the major features of the \[C ii\] emission. The residual image of the \[C ii\] emission is similar to the continuum residual. The peak in the residual is $8.1\%$ of the peak in the dirty image.

## \[C ii\] Kinematics

Figure [1](#fig:clean) suggests that the host galaxy of J0439+1634 has an ordered, rotation-like velocity field. We thus fit the \[C ii\] emission using an axisymmetric rotating thin disk, following the method described in (cite: neeleman19). In short, we set up parameterized models for the flux distribution, the mean velocity field, and the velocity dispersion field. We then use VISILENS to calculate the lensed \[C ii\] emission and the $uv-$plane response in each velocity channel. We obtain the best-fit model parameters by minimizing the residual of the visibility in all channels. To keep maximum flexibility, we do not constrain the parameters using the Sérsic model for the integrated \[C ii\] flux. We assume a Sérsic profile for the flux distribution and apply various forms for the rotation curve and the velocity dispersion profile. However, all of these models return large residuals and unphysical best-fit parameters. We thus conclude that J0439+1634 cannot be described by an axisymmetric rotating thin disk.

The main reason for the poor fit is the apparent misalignment between the major axis of the flux distribution and the velocity gradient. For an axisymmetric rotation disk, the major axis and the velocity gradient should be in the same direction. In contrast, the major axis of the flux distribution of J0439+1634 is roughly aligned east-to-west (Figure [3](#fig:lensmodel), right panel), while the velocity gradient is roughly north-to-south (Figure [1](#fig:clean)). To further investigate this problem, we estimate the source-plane flux distribution using a simple inverse ray-tracing method. Specifically, we reconstruct the source (i.e., un-lensed) data cube on a grid with a pixel size of $0.04\ensuremath{''}$. Using the overall \[C ii\] magnification $\mu_\text{[C\,{\sc ii}]}=3.44$, we estimate the average source-plane resolution to be $\sim\sqrt{0.31\ensuremath{''}\times0.27\ensuremath{''}}/\sqrt{3.44}=0.156\ensuremath{''}$ for the \[C ii\] emission. A pixel size of $0.04\ensuremath{''}$ gives a super-Nyquist sampling, which helps to resolve the regions with higher magnification than the average value. We then trace all the pixels in the image-plane data cube (i.e., the clean image) to the source plane according to the default lensing model. If more than one image-plane pixels are traced to the same source-plane pixel, these image pixels are averaged. This simple method captures the main features of the quasar host galaxy without expensive pixelized lensing reconstruction.

![](moments.pdf)

We generate source-plane moment maps using the reconstructed data cube. When calculating the first and the second moments, we only include pixels that have integrated flux SNR larger than $10$.

Figure [5](#fig:reconstruct) shows the reconstructed moments, which confirm the overall picture of J0439+1634: a regular profile for the integrated emission (moment 0) and a rotation-like mean velocity field (moment 1). The major axis of moment 0 is significantly offset from the velocity gradient in the moment 1 map, confirming the argument we made with the lensed image. Another hint is the structures in the moment 2 map. For a rotating thin disk, we expect a peak at the center of the moment 2 map due to the beam smearing effect where the line-of-sight velocity gradient is large. This peak is not seen in Figure [5](#fig:reconstruct); instead, the moment 2 map has complex structures, which indicate complicated velocity field in the host galaxy.

The lower-right corner of the reconstructed moment 0 map illustrates the output when we perform the inverse ray-tracing analysis to an image-plane beam located at the image-plane flux peak. This “reconstructed" beam is a rough estimate of the beam shape on the source plane.

The source-plane beam has a size of $0.26\ensuremath{''}\times0.09\ensuremath{''}$, which further illustrates that a source-plane pixel size of $0.04\ensuremath{''}$ is appropriate.

Note that the blue and red wings in the moment 1 map are located outside of the caustics, which means that they are not multiply-imaged. For these areas, the effect of gravitational lensing on the observations is equivalent to shrinking the beam size and applying some image distortions. As such, the inverse ray-tracing reconstruction can capture the structure of the velocity field, especially in the blue and red wings. In Figure [6](#fig:pvplot), we illustrate the position-velocity plot of J0439+1634, generated using the reconstructed moment 0 and moment 1. We extract the velocities along the black line, which connects the pixels with the maximum and minimum moment 1 value (i.e., the red and blue peaks). The position-velocity plot clearly shows a rotation-like feature. The velocity rises at $r\lesssim1\text{ kpc}$ and flattens beyond this radius. The maximum rotation velocity is roughly $v_\text{max}\sin(i)=130\text{ km s}^{-1}$ where $i$ is the inclination angle of the rotation axis, and the velocity is measured out to $r_\text{max}=2\text{ kpc}$.

In addition to the rotation-like feature, the position-velocity plot contains another component with low velocity $(|v|\lesssim50\text{ km s}^{-1}, \text{marked by the yellow box})$. We mark pixels that contribute to this feature with black dots in the moment 1 map in Figure [6](#fig:pvplot). These pixels either lie inside the caustics, which means that they are multiply imaged, and have complicated lens-mapping function, or have low signal and large errors. The simple inverse ray-tracing method will fail for these areas, and this component is likely an artifact. If it is physical, it might reflect some complex structures in the host galaxy, which can be resolved in the upcoming high-resolution ALMA observations. Possible scenarios include minor mergers and clumpy star-formation regions. In any case, this structure only contributes $\sim10\%$ of the total flux, and the rotation-like feature dominates the velocity field.

J0439+1634 has a rotation-like velocity field, but cannot be described by an axisymmetric rotating thin disk. It is likely that the \[C ii\] emission is not axisymmetric and/or that the host galaxy has a thick geometry. Both cases are common for high-redshift sgalaxies (cite: pensabene20; fsw20). Specifically, many star-forming galaxies at $z\gtrsim2$ have velocity dispersion $\sigma\gtrsim45 \text{ km s}^{-1}$ and show thick geometry (cite: fsw20). For J0439+1634, we can estimate its velocity dispersion using the regions where the rotation curve has flattened. The moment 2 map suggests that these regions have $\sigma\sim70 \text{ km s}^{-1}$, which means that a thick geometry is likely.

Fitting a non-axisymmetric model and/or a thick disk model requires high spatial resolution, and our data cannot put a strong constraint on these models. In future work, we will perform pixelized lensing reconstruction and detailed dynamical modeling once the high-resolution ALMA observations are carried out (Project 2018.1.00566.S, PI: Fan).

![](pvplot.pdf)

## Systematic Uncertainties

We first consider the systematic errors in the fluxes and sizes of the continuum and the \[C ii\] emission. The main source of systematic errors is that the SIE + Sérsic lensing model is over-simplified. As a result, there are positive clumps in the residual images in Figure [3](#fig:lensmodel). The flux of the clumps is much smaller than the the flux calibration error and is negligible in the error analysis. Properly modeling the structures in the residual images requires expensive pixelized modeling of the source flux and the lens mass (cite: hezaveh16), which is beyond the scope of this paper.

We then consider the systematic uncertainties in the source-plane reconstruction in Section [3.4](#subsec:kinematics). The major uncertainty is the beam-smearing effect. The source-plane resolution is $\sim0.15\ensuremath{''}$ $(\sim0.8\text{ kpc})$. In this study, we focus on the maximum rotation velocity rather than detailed velocity field structure. Beam-smearing effects have little influence on our main result, because (1) the blue and red peaks are only singly imaged, and (2) the rotation velocity flattens at $r\gtrsim 1 \text{ kpc}$, so the central, low-velocity area does not influence the edge at $r_\text{max}=2\text{ kpc}$ where we measure the maximum velocity. Similar methods have been adopted by recent studies to measure the rotation velocity of lensed galaxies (cite: cheng20).

# Physical Properties of J0439+1634

## Dust Continuum and \[C ii\] Emission

The host galaxy of J0439+1634 has a regular Sérsic profile, both for the continuum and \[C ii\] emission. The Sérsic index is close to one, which suggests that J0439+1634 is more similar to an exponential disk than a de-Vaucouleurs bulge with $n=4$. The \[C ii\] line profile is also well-described by a single-peaked Gaussian profile, with no excess of blueshifted or redshifted components. The smooth structures in the moment maps and the position-velocity plot disfavor the scenario of a close, on-going major merger. In addition, no other objects are detected within the ALMA field of view $(\sim12'')$. These results suggest that J0439+1634 is not an on-going major merger and does not exhibit significant outflow features in the \[C ii\] velocity field. However, it is possible that J0439+1634 is a minor merger or a remnant of a recent major merger.

(cite: yang19) measure the far-infrared (FIR) to centimeter-wavelength spectral energy distribution (SED), as well as the CO, \[C i\], \[C ii\], \[O i\], and $\text{H}_2\text{O}$ emission lines of J0439+1634. Their NOrthern Extended Millimeter Array (NOEMA) observation gives $z_\text{[C\,{\sc ii}]}=6.5188\pm0.0002$, $F_\text{[C\,{\sc ii}]}=11.7\pm0.8\text{ Jy km s}^{-1}$, $\text{FWHM}_\text{[C\,{\sc ii}]} = 328.1\pm18.0 \text{ km s}^{-1}$, and $S_\text{239 GHz}=14.0\pm0.1 \text{ mJy}$. The typical flux calibration uncertainty is $\sim 15\%$ for NOEMA and $\sim 10\%$ for ALMA. The continuum and \[C ii\] line fluxes reported in Section [2](#sec:data) are consistent with those in (cite: yang19). The difference in the FWHM of the \[C ii\] line is about 3$\sigma$.

Based on these measurements, (cite: yang19) calculate the infrared luminosities, emission line luminosities, star formation rate, dust mass, and gas mass without correcting for the lensing magnification. We refer the reader to (cite: yang19) for the details of how these properties are calculated. In this work, with spatially resolved ALMA images, we calculate the de-lensed values of these quantities. For \[C ii\]-based quantities, we apply the magnification of \[C ii\] emission, $\mu_\text{[C\,{\sc ii}]}=3.44$; for FIR-based quantities, we apply the continuum magnification, $\mu_\text{cont}=4.53$. In addition, we apply the continuum magnification to the CO-based molecular gas mass, assuming that the dust continuum traces the molecular gas. The results are listed in Table [\[tbl:physical\]](#tbl:physical). Similar to other high-redshift quasars (cite: walter09; decarli18; wang19b), J0439+1634 is hosted by a gas-rich ultra luminous infrared galaxy (ULIRG) with intense star formation activity, with a TIR luminosity of $\sim10^{13}L_\odot$.

| \[C ii\]-Based Properties |  |
|:---|---:|
| $L_\text{[C\,{\sc ii}]} (L_\odot)$ | $(3.5\pm0.3)\times10^9$ |
| $L'_\text{[C\,{\sc ii}]} (\text{K km s}^{-1}\text{pc}^{2})$ | $(1.7\pm0.1)\times10^{10}$ |
| $M_{\text{C}^+}(M_\odot)$ | ($1.1\pm0.1)\times10^7$ |
| $\text{SFR}_\text{{[C\,{\sc ii}]}} (M_\odot\text{ year}^{-1})$ | $\sim233\sim1398$ |
| Other properties |  |
| $L_\text{FIR} (L_\odot)$ | $(7.5\pm0.4)\times10^{12}$ |
| $L_\text{TIR} (L_\odot)$ | $(1.06\pm0.04)\times10^{13}$ |
| $\text{SFR}_\text{TIR} (M_\odot\text{ year}^{-1})$ | $1.56\times10^3$ |
| $M_\text{dust}(M_\odot)$ | $4.9\pm0.2\times10^8$ |
| $M_{\text{H}_2,\text{CO}}(M_\odot)$ | $1.19\times10^{10}$ |

: De-lensed Physical Properties of J0439+1634

Table notes: These values are calculated according to Table 1 in (cite: yang19). We apply $\mu=\mu(\text{[C\,{\sc ii}]})=3.44$ for \[C ii\]-based quantities and $\mu=\mu(\text{continuum})=4.53$ for the other quantities. FIR luminosity includes flux in rest-frame $42.5-122.5~\mu$m, and TIR luminosity includes flux in rest-frame $8-1000~\mu$m. The uncertainties only reflect statistical errors.

One interesting aspect of the \[C ii\] emission is the so-called “\[C ii\] deficit." In systems with high FIR surface brightness (cite: diaz-santos17; hc18), the \[C ii\]-to-FIR ratio decreases with $\Sigma_\text{FIR}$. This relation has been observed in many different systems, including nebulae in the Milky Way (cite: goicoechea15), local luminous infrared galaxies (LIRGs) and ULIRGs (cite: diaz-santos13), high-redshift submillimeter galaxies (SMGs) (cite: oteo16; spilker16; litke19) and quasars (cite: decarli18; neeleman19). The underlying mechanism of the \[C ii\] deficit might be complex. Some plausible scenarios include: (1) In regions with higher surface density, most carbon atoms are in the form of CO molecules rather than $\text{C}^+$ ions (cite: narayanan17); (2) \[C ii\] might become optically thick at high surface density (cite: luhman98); (3) Large FIR surface brightness indicates strong dust absorption of the UV radiation, which is the main heating source of \[C ii\] emission (cite: hc18); (4) \[C ii\] emission might be saturated in warm gas (cite: mo16).

With spatially resolved data, we can investigate the \[C ii\] deficit in different regions of J0439+1634. Using the continuum and \[C ii\] model in Figure [3](#fig:lensmodel), we measure the \[C ii\] and FIR flux of J0439+1634 in four regions. The $n^\text{th}$ region is defined as $n\times R_\text{eff}<R<(n+1)\times R_\text{eff}$, where $n=0,1,2,3$, and $R_\text{eff}=0.136\ensuremath{''}$ is the half-light radius of the continuum emission. All regions have the same center, ellipticity, and position angle as the continuum emission. The widths of the rings are close to the average source-plane resolution of $0.15\ensuremath{''}$.

The flux calibration error ($\sim15\%$) is the dominant source of uncertainty, and we ignore other uncertainties.

Figure [7](#fig:ciifir) illustrates the position of J0439+1634 on the \[C ii\]$/$FIR$-\Sigma_\text{FIR}$ plot. We include $z\gtrsim6$ quasars from the literature for comparison. Specifically, three quasars from (cite: shao17) and (cite: wangran19) have spatially resolved measurements.

We also include LIRGs from the Great Observatories All-sky LIRG Survey (GOALS) sample (cite: diaz-santos13), SMGs at $4.5<z<6.5$ (cite: riechers13; neri14; gullberg18), and resolved regions of a gravitationally lensed SMG at $z=5.7$, SPT0346 (cite: litke19). Similar to other objects with high-resolution data, different regions in J0439+1634 tightly follow the \[C ii\] deficit. Our result thus suggests that the \[C ii\] deficit is related to physical processes on $\lesssim1 \text{ kpc}$ scales, i.e., it reflects the properties of the local ISM rather than the entire galaxy.

![](ciideficit.pdf)

## Host Galaxy Dynamics

Using the maximum line-of-sight velocity $v_\text{max}\sin(i) = 130 \text{ km s}^{-1}$ and the corresponding radius $r_\text{max}=2\text{ kpc}$, we estimate the dynamical mass within $r_\text{max}$ for J0439+1634, $M_\text{dyn}\sin^2(i)=7.9\times10^{9}M_\odot$. We report in Table [\[tbl:physical\]](#tbl:physical) the $\text{H}_2$ mass of J0439+1634, $M_{\text{H}_2,\text{CO}}(M_\odot)=1.19\times10^{10} M_\odot$, which gives a gas-mass fraction of $1.5\times\sin^2(i)$. The gas-mass fraction is high except for very low inclinations.

Although the host galaxy of J0439+1634 has a regular shape and a rotation-like velocity field, we show in Section [3.4](#subsec:kinematics) that this galaxy is not an axisymmetric thin disk. Plausible scenarios include (1) the emission in the galaxy is not axisymmetric, which can happen when the star-forming regions are not evenly distributed on the disk, or (2) the host galaxy has a “thick" geometry (e.g., a spheroid) and is not a thin disk. The upcoming high-resolution ALMA data will reveal small-scale structures that might distinguish these models. Here we briefly discuss the implications of the thick disk model, since the moment 2 map indicates that a thick geometry is likely (Section [3.4](#subsec:kinematics)).

A thick disk with a large velocity dispersion has a non-negligible turbulent pressure gradient which needs to be considered when estimating the dynamical mass. Following the discussion in (cite: fsw20), we estimate the circular velocity of the host galaxy, $v_c$: $$\begin{equation}
    v_c^2=v_\text{max}^2+2\sigma^2\times(r/R_d)
\end{equation}$$ which is related to the dynamical mass by $M_\text{dyn}(r)=v_c^2r/G$, where $R_d$ is the scaling radius of the exponential disk (i.e., $I(r)\propto e^{-r/R_d}$). Applying $v_\text{max} = 130/\sin(i) \text{ km s}^{-1}$, $r=2 \text{ kpc}$, $\sigma=70 \text{ km s}^{-1}$ and $R_d=0.8$ kpc according to the best-fit \[C ii\] model in Section [3.3](#subsec:CIIsersic) yields $$\begin{equation}
    v_c^2=\left[\frac{130 \text{ km/s}}{\sin(i)}\right]^2 + (160\text{ km/s})^2
\end{equation}$$ which suggests that, in the thick-disk model, the contribution of velocity dispersion is significant. However, the velocity dispersion should be taken as an upper limit given the beam smearing effect. It is hard to correct the beam smearing effect under the current resolution; as such, we still use $M_\text{dyn}\sin^2(i)=7.9\times10^{9}M_\odot$ in the rest of this paper. This result illustrates the need of careful modeling with high-resolution data when measuring the dynamical mass of high-redshift quasar host galaxies.

(cite: pensabene20) analyzes the archival ALMA data of 32 quasars to model their kinematics, where ten quasars at $z>5.7$ are found to have rotation-like velocity fields. Among these ten quasars, three have a significantly misaligned flux major axis and velocity gradient. This result suggests that complicated kinematics are common in high-redshift quasars and that high-resolution observations are crucial to understanding high-redshift quasar host galaxies.

# A Maximum Starburst System With Oversized Black Hole at Cosmic Dawn

## A Maximum Star Forming Rotating System

Our analysis shows that the host galaxy of J0439+1634 is a compact ULIRG with vigorous star formation. Assuming that the dust continuum traces the SFR surface density (SFRD), we estimate the SFRD within the continuum half-light radius

to be $\Sigma_\text{SFR}\approx800 M_\odot\text{ year}^{-1}\text{ kpc}^{-2}$. Such a high $\Sigma_\text{SFR}$ is close to the highest SFRD values seen in the universe (cite: walter09) and approaches the Eddington-limit of star formation (cite: thompson05). In addition, we estimate the maximum SFR proposed by (cite: elmergreen99), where the gas is assumed to collapse on a free-fall timescale, $t_\text{ff}=\sqrt{2R^3/GM}=1.06\sin(i)\times10^7$ year. The maximum possible SFR is $\epsilon M_\text{gas}/t_\text{ff}$, where $\epsilon$ is the efficiency of gas turning into stars. This argument suggests that J0439+1634 has a maximum possible SFR of $\epsilon\sin^{-1}(i) \times 1.12\times 10^3 M_\odot \text{ year}^{-1}$ within a radius of $R<2 \text{ kpc}$. For any reasonable inclination angle $(i\gtrsim5^\circ)$, a high star formation efficiency is required $(\epsilon\gtrsim0.1)$. Our analysis suggests that J0439+1634 is forming stars at the maximum possible rate.

The rich gas reservoir and the vigorous star formation of J0439+1634 could be a remnant of a recent major merger or strong cold gas inflow (cite: dekel09).

The major merger remnant scenario is promising because it provides a natural explanation to the misalignment between the major axis and the velocity gradient, i.e., the star-formation regions are not yet evenly distributed in the rotating disk. Under the current resolution, small-scale structures will get smoothed out, and the flux distribution mimics a Sérsic profile. Upcoming high-resolution ALMA data could reveal these possible structures.

## SMBH-Host Co-evolution

(cite: fan19) measures the SMBH mass of J0439+1634 to be $M_\text{BH}=(4.29\pm 0.60)\times10^8M_\odot$, which gives $M_\text{BH}/M_\text{dyn}=0.055\sin^2(i)$. Assuming J0439+1634 follows the local relation in (cite: kh13) yields $M_\text{BH}/M_\text{host}=0.005$. A face-on rotation model with inclination $i=17^{\circ}$ moves J0439+1634 onto the local $M_\text{BH}-M_\text{host}$ relation, and a fiducial inclination angle of $i=60^\circ$ yields $M_\text{BH}/M_\text{host}=0.04$. This result is similar to that in many high-redshift quasars (cite: venemans17; decarli18; wang19b), which have $M_\text{BH}/M_\text{host}$ several times higher than the local relation.

With the SMBH mass and the observed central velocity dispersion, we estimate the size of the SMBH’s sphere of influence: $$\begin{equation}
    r_h=\frac{GM_\text{BH}}{\sigma^2}.
\end{equation}$$ Both the image-plane moment 2 (Figure [1](#fig:clean)) and the reconstructed source-plane moment 2 (Figure [5](#fig:reconstruct)) show roughly constant velocity dispersion across the galaxy. We thus adopt the median value of the source-plane moment 2 map, $\sigma_\text{med}=94 \text{ km s}^{-1}$, which gives $r_h = 0.18 \text{ kpc}$. The most extended configuration of ALMA delivers a resolution of $\sim0.02\ensuremath{''}$. For the region near the SMBH, we apply the magnification of the optical quasar from (cite: fan19), $\mu_\text{quasar}=51.3$. An image-plane resolution of $0.02\ensuremath{''}$ thus corresponds to a source-plane resolution of $\sim2.8\text{ mas}$ $(\sim 16 \text{ pc})$. Thus, high-resolution ALMA observations will allow us to sample the SMBH’s sphere of influence well and to measure the mass of the SMBH directly via gas kinematics.

Direct measurement of SMBH mass has been possible only at low-redshift (cite: kh13). For most high-redshift quasars, SMBH masses are measured based on the empirical relation between the continuum luminosity and the broad line region size (cite: vp06), which has only been calibrated at $z\lesssim2$.

J0439+1634 thus provides a unique opportunity to calibrate the SMBH mass measurement at high redshift.

# Conclusions

We present ALMA observations of a gravitationally lensed quasar at $z=6.52$, J0439+1634. We model the dust-continuum, the \[C ii\] emission, and the velocity field of the host galaxy. Our main conclusions are:

1.  The ALMA observations demonstrate that the three-image fiducial model in (cite: fan19) based on *HST* observations of the quasar is correct, ruling out the alternative models considered in (cite: fan19) . The default lensing model gives an overall magnification of $4.53\pm0.05$ and $3.44\pm0.05$ for the continuum and \[C ii\] emission of the host galaxy, respectively. The average source-plane resolution is $\sim0.15\ensuremath{''}$ $(\sim0.8 \text{ kpc})$.

2.  J0439+1634 is a compact ULIRG well-described by a compact Sérsic profile. The Sérsic index is close to one for both the continuum and \[C ii\] emission. The resolved regions in J0439+1634 follow the “\[C ii\] deficit," suggesting that the deficit is related to the sub-kpc properties of the ISM.

3.  J0439+1634 has a rotation-like velocity field, but it cannot be well described as an axisymmetric rotating thin disk. The maximum line-of-sight rotation velocity is $v_\text{max}\sin(i)=130\text{ km s}^{-1}$, with the inclination angle $i$ unconstrained. The dynamical mass within $2\text{ kpc}$ is $7.9\times10^{9}\sin^{-2}(i)M_\odot$. J0439+1634 is likely a gas-rich galaxy with a high gas-mass fraction.

4.  J0439+1634 is forming stars at the maximum possible rate. The star-formation rate surface density of J0439+1634 approaches the largest value seen in the universe and the Eddington limit.

5.  The SMBH-to-dynamical mass ratio of J0439+1634 is $0.055 \times \sin^2(i)$, which suggests that J0439+1634 is likely to host an oversized SMBH compared to local relations. The size of the sphere of influence is $0.18 \text{ kpc}$. The most extended configuration of ALMA will resolve the sphere of influence and allow us to measure the SMBH mass directly using the gas kinematics.

Our lensing model incorporates the major features of J0439+1634 detected under low resolution ALMA data. Future high-resolution ALMA observations with higher-resolution, combined with pixelized lens modeling, will reveal more detailed structures in the foreground lens and quasar host galaxy. Specifically, as discussed in Section [5.2](#subsec:coev), the resolution around the SMBH will reach $\sim16 \text{ pc}$ within the SMBH sphere of influence. The power of gravitational lensing makes J0439+1634 a valuable object for a case study, which will provide crucial and previously inaccessible information about the coevolution of SMBHs and their hosts at $z>6$.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00566.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co- operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. MY, JY and XF acknowledges supports by NSF grants AST 15-15115 and AST 19-08284. MY acknowledges support from NRAO Student Observing Support (SOS) award SOSPA6-002. FW thanks the support provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51448.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Incorporated, under NASA contract NAS5-26555. JS acknowledge the support provided by NASA through the NASA Hubble Fellowship grants #HST-HF2-51446 awarded by the Space Telescope Science Institute. KCL acknowledges support from the US NSF under grants AST-1715213 and AST-1716127 and from the US NSF NRAO under grant SOSPA5-001. RW acknowledges the supports from the National Science Foundation of China (NSFC) grants No.11721303, 11991052, and the National Key Program for Science and Technology Research and Development (grant 2016YFA0400703). CK acknowledges support from US NSF grant AST-1716585. BPV acknowledges funding through the ERC Advanced Grant 740246 (Cosmic Gas).

# Facilities

ALMA

# Software

VISILENS

natexlab

(ref: banados16) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11, doi: [`10.3847/0067-0049/227/1/11`](http://doi.org/10.3847/0067-0049/227/1/11)

(ref: banados18) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473, doi: [`10.1038/nature25180`](http://doi.org/10.1038/nature25180)

(ref: banados19) Bañados, E., Novak, M., Neeleman, M., et al. 2019, ApJL, 881, L23, doi: [`10.3847/2041-8213/ab3659`](http://doi.org/10.3847/2041-8213/ab3659)

(ref: beelen06) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694, doi: [`10.1086/500636`](http://doi.org/10.1086/500636)

(ref: bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: cheng20) Cheng, C., Cao, X., Lu, N., et al. 2020, ApJ, 898, 33, doi: [`10.3847/1538-4357/ab980b`](http://doi.org/10.3847/1538-4357/ab980b)

(ref: almatech) Cortes, P. C., Remijan, A., Biggs, A., et al. 2020, ALMA Technical Handbook, ALMA Doc. 8.4, ver. 1.0. <https://almascience.nrao.edu/documents-and-tools/cycle8/alma-technical-handbook>

(ref: decarli18) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: dekel09) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451, doi: [`10.1038/nature07648`](http://doi.org/10.1038/nature07648)

(ref: diaz-santos13) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: diaz-santos17) —. 2017, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: elmergreen99) Elmegreen, B. G. 1999, ApJ, 517, 103, doi: [`10.1086/307200`](http://doi.org/10.1086/307200)

(ref: fan19) Fan, X., Wang, F., Yang, J., et al. 2019, ApJL, 870, L11, doi: [`10.3847/2041-8213/aaeffe`](http://doi.org/10.3847/2041-8213/aaeffe)

(ref: fsw20) Förster Schreiber, N. M., & Wuyts, S. 2020, ARA&A, 58, 661, doi: [`10.1146/annurev-astro-032620-021910`](http://doi.org/10.1146/annurev-astro-032620-021910)

(ref: goicoechea15) Goicoechea, J. R., Teyssier, D., Etxaluze, M., et al. 2015, ApJ, 812, 75, doi: [`10.1088/0004-637X/812/1/75`](http://doi.org/10.1088/0004-637X/812/1/75)

(ref: gullberg18) Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ, 859, 12, doi: [`10.3847/1538-4357/aabe8c`](http://doi.org/10.3847/1538-4357/aabe8c)

(ref: hc18) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94, doi: [`10.3847/1538-4357/aac0f6`](http://doi.org/10.3847/1538-4357/aac0f6)

(ref: hezaveh16) Hezaveh, Y. D., Dalal, N., Marrone, D. P., et al. 2016, ApJ, 823, 37, doi: [`10.3847/0004-637X/823/1/37`](http://doi.org/10.3847/0004-637X/823/1/37)

(ref: inoue20) Inoue, K. T., Matsushita, S., Nakanishi, K., & Minezaki, T. 2020, ApJL, 892, L18, doi: [`10.3847/2041-8213/ab7b7e`](http://doi.org/10.3847/2041-8213/ab7b7e)

(ref: izumi18) Izumi, T., Onoue, M., Shirakata, H., et al. 2018, PASJ, 70, 36, doi: [`10.1093/pasj/psy026`](http://doi.org/10.1093/pasj/psy026)

(ref: izumi19) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: jiang16) Jiang, L., McGreer, I. D., Fan, X., et al. 2016, ApJ, 833, 222, doi: [`10.3847/1538-4357/833/2/222`](http://doi.org/10.3847/1538-4357/833/2/222)

(ref: sie) Kormann, R., Schneider, P., & Bartelmann, M. 1994, A&A, 284, 285

(ref: kh13) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: leipski14) Leipski, C., Meisenheimer, K., Walter, F., et al. 2014, ApJ, 785, 154, doi: [`10.1088/0004-637X/785/2/154`](http://doi.org/10.1088/0004-637X/785/2/154)

(ref: litke19) Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ, 870, 80, doi: [`10.3847/1538-4357/aaf057`](http://doi.org/10.3847/1538-4357/aaf057)

(ref: luhman98) Luhman, M. L., Satyapal, S., Fischer, J., et al. 1998, ApJL, 504, L11, doi: [`10.1086/311562`](http://doi.org/10.1086/311562)

(ref: marshall20) Marshall, M. A., Mechtley, M., Windhorst, R. A., et al. 2020, arXiv e-prints, arXiv:2007.13859. [`https://arxiv.org/abs/2007.13859`](https://arxiv.org/abs/2007.13859)

(ref: matsuoka16) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2016, ApJ, 828, 26, doi: [`10.3847/0004-637X/828/1/26`](http://doi.org/10.3847/0004-637X/828/1/26)

(ref: matsuoka18a) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2018a, ApJS, 237, 5, doi: [`10.3847/1538-4365/aac724`](http://doi.org/10.3847/1538-4365/aac724)

(ref: matsuoka2018b) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2018b, PASJ, 70, S35, doi: [`10.1093/pasj/psx046`](http://doi.org/10.1093/pasj/psx046)

(ref: matsuoka19) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2019, ApJ, 883, 183, doi: [`10.3847/1538-4357/ab3c60`](http://doi.org/10.3847/1538-4357/ab3c60)

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mechtley12) Mechtley, M., Windhorst, R. A., Ryan, R. E., et al. 2012, ApJL, 756, L38, doi: [`10.1088/2041-8205/756/2/L38`](http://doi.org/10.1088/2041-8205/756/2/L38)

(ref: mo16) Muñoz, J. A., & Oh, S. P. 2016, MNRAS, 463, 2085, doi: [`10.1093/mnras/stw2102`](http://doi.org/10.1093/mnras/stw2102)

(ref: murphy11) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: narayanan17) Narayanan, D., & Krumholz, M. R. 2017, MNRAS, 467, 50, doi: [`10.1093/mnras/stw3218`](http://doi.org/10.1093/mnras/stw3218)

(ref: neeleman19) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: neri14) Neri, R., Downes, D., Cox, P., & Walter, F. 2014, A&A, 562, A35, doi: [`10.1051/0004-6361/201322528`](http://doi.org/10.1051/0004-6361/201322528)

(ref: oteo16) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34, doi: [`10.3847/0004-637X/827/1/34`](http://doi.org/10.3847/0004-637X/827/1/34)

(ref: pensabene20) Pensabene, A., Carniani, S., Perna, M., et al. 2020, A&A, 637, A84, doi: [`10.1051/0004-6361/201936634`](http://doi.org/10.1051/0004-6361/201936634)

(ref: riechers09) Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ, 703, 1338, doi: [`10.1088/0004-637X/703/2/1338`](http://doi.org/10.1088/0004-637X/703/2/1338)

(ref: riechers13) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: rigopoulou18) Rigopoulou, D., Pereira-Santaella, M., Magdis, G. E., et al. 2018, MNRAS, 473, 20, doi: [`10.1093/mnras/stx2311`](http://doi.org/10.1093/mnras/stx2311)

(ref: Schreiber18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: shao17) Shao, Y., Wang, R., Jones, G. C., et al. 2017, ApJ, 845, 138, doi: [`10.3847/1538-4357/aa826c`](http://doi.org/10.3847/1538-4357/aa826c)

(ref: shao19) Shao, Y., Wang, R., Carilli, C. L., et al. 2019, ApJ, 876, 99, doi: [`10.3847/1538-4357/ab133d`](http://doi.org/10.3847/1538-4357/ab133d)

(ref: spilker16) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112, doi: [`10.3847/0004-637X/826/2/112`](http://doi.org/10.3847/0004-637X/826/2/112)

(ref: spilker20) Spilker, J. S., Phadke, K. A., Aravena, M., et al. 2020, ApJ, 905, 85, doi: [`10.3847/1538-4357/abc47f`](http://doi.org/10.3847/1538-4357/abc47f)

(ref: thompson05) Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167, doi: [`10.1086/431923`](http://doi.org/10.1086/431923)

(ref: venemans19) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30, doi: [`10.3847/2041-8213/ab11cc`](http://doi.org/10.3847/2041-8213/ab11cc)

(ref: venemans16) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37, doi: [`10.3847/0004-637X/816/1/37`](http://doi.org/10.3847/0004-637X/816/1/37)

(ref: venemans12) Venemans, B. P., McMahon, R. G., Walter, F., et al. 2012, ApJL, 751, L25, doi: [`10.1088/2041-8205/751/2/L25`](http://doi.org/10.1088/2041-8205/751/2/L25)

(ref: venemans13) Venemans, B. P., Findlay, J. R., Sutherland, W. J., et al. 2013, ApJ, 779, 24, doi: [`10.1088/0004-637X/779/1/24`](http://doi.org/10.1088/0004-637X/779/1/24)

(ref: venemans15) Venemans, B. P., Bañados, E., Decarli, R., et al. 2015, ApJL, 801, L11, doi: [`10.1088/2041-8205/801/1/L11`](http://doi.org/10.1088/2041-8205/801/1/L11)

(ref: venemans17) Venemans, B. P., Walter, F., Decarli, R., et al. 2017, ApJ, 837, 146, doi: [`10.3847/1538-4357/aa62ac`](http://doi.org/10.3847/1538-4357/aa62ac)

(ref: venemans18) Venemans, B. P., Decarli, R., Walter, F., et al. 2018, ApJ, 866, 159, doi: [`10.3847/1538-4357/aadf35`](http://doi.org/10.3847/1538-4357/aadf35)

(ref: venemans20) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: vp06) Vestergaard, M., & Peterson, B. M. 2006, ApJ, 641, 689, doi: [`10.1086/500572`](http://doi.org/10.1086/500572)

(ref: walter09) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699, doi: [`10.1038/nature07681`](http://doi.org/10.1038/nature07681)

(ref: wang19b) Wang, F., Wang, R., Fan, X., et al. 2019a, ApJ, 880, 2, doi: [`10.3847/1538-4357/ab2717`](http://doi.org/10.3847/1538-4357/ab2717)

(ref: wang17) Wang, F., Fan, X., Yang, J., et al. 2017, ApJ, 839, 27, doi: [`10.3847/1538-4357/aa689f`](http://doi.org/10.3847/1538-4357/aa689f)

(ref: wang19a) Wang, F., Yang, J., Fan, X., et al. 2019b, ApJ, 884, 30, doi: [`10.3847/1538-4357/ab2be5`](http://doi.org/10.3847/1538-4357/ab2be5)

(ref: wangran08) Wang, R., Carilli, C. L., Wagg, J., et al. 2008, ApJ, 687, 848, doi: [`10.1086/591076`](http://doi.org/10.1086/591076)

(ref: wangran10) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699, doi: [`10.1088/0004-637X/714/1/699`](http://doi.org/10.1088/0004-637X/714/1/699)

(ref: wangran13) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: wangran19) Wang, R., Shao, Y., Carilli, C. L., et al. 2019c, ApJ, 887, 40, doi: [`10.3847/1538-4357/ab4d4b`](http://doi.org/10.3847/1538-4357/ab4d4b)

(ref: weib05) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25, doi: [`10.1051/0004-6361:200400085`](http://doi.org/10.1051/0004-6361:200400085)

(ref: willott15) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123, doi: [`10.1088/0004-637X/801/2/123`](http://doi.org/10.1088/0004-637X/801/2/123)

(ref: yang19a) Yang, J., Wang, F., Fan, X., et al. 2019a, AJ, 157, 236, doi: [`10.3847/1538-3881/ab1be1`](http://doi.org/10.3847/1538-3881/ab1be1)

(ref: yang19) Yang, J., Venemans, B., Wang, F., et al. 2019b, ApJ, 880, 153, doi: [`10.3847/1538-4357/ab2a02`](http://doi.org/10.3847/1538-4357/ab2a02)

(ref: yang20) Yang, J., Wang, F., Fan, X., et al. 2020, ApJL, 897, L14, doi: [`10.3847/2041-8213/ab9c26`](http://doi.org/10.3847/2041-8213/ab9c26)

[^1]: This step is completed prior to the release of CASA version 5.6.1, and we use CASA version 5.4.0 when running UVCONTSUB.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Comparison with NOEMA measurements from (cite: yang19)",
  "failed_quote": "The continuum and [C ii] line fluxes reported in Section 2 are consistent with those in (cite: yang19)."
 },
 {
  "path": "analysis_steps[4].method.evidence[1]",
  "value": "Correct apparent luminosities, SFR, dust mass, and gas mass from (cite: yang19) using derived continuum and [C II] magnifications. Measure [C II]/FIR vs Sigma_FIR in 4 concentric elliptical rings of width R_eff. Compute dynamical mass from v_max sin(i) and r_max, and evaluate SMBH sphere of influence.",
  "failed_quote": "Using the continuum and [C ii] model in Figure 3, we measure the [C ii] and FIR flux of J0439+1634 in four regions. The $n^\\text{th}$ region is defined as $n\\times R_\\text{eff}<R<(n+1)\\times R_\\text{eff}$, where $n=0,1,2,3$, and $R_\\text{eff}=0.136\\ensuremath{''}$ is the half-light radius of the continuum emission."
 }
]
```
