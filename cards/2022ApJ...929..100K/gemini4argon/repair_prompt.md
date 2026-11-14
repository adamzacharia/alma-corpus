# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022ApJ...929..100K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Multi-wavelength and Multi-CO View of The Minor Merger Driven Star Formation in the Nearby LIRG NGC 3110

## Abstract

We present Atacama Large Millimeter/submillimeter Array observations of multiple $^{12}$CO, $^{13}$CO, and C$^{18}$O lines and 2.9 mm and 1.3 mm continuum emission toward the nearby interacting luminous infrared galaxy NGC 3110, supplemented with similar spatial resolution H$\alpha$, 1.4 GHz continuum, and $K$-band data. We estimate the typical CO-to-H$_2$ conversion factor of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ within the disk using LTE-based and dust-based H$_2$ column densities, and measure the 1-kpc scale surface densities of star formation rate ($\Sigma_{\rm SFR}$), super star clusters ($\Sigma_{\rm SSC}$), molecular gas mass, and star formation efficiency (SFE) toward the entire gas disk. These parameters show a peak at the southern part of the southern spiral arm (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$), which is likely attributed to the on-going tidal interaction with the companion galaxy MCG-01-26-013, as well as toward the circumnuclear region. We also find that thermal free-free emission contributes to a significant fraction of the millimeter continuum emission at the southern peak position. Those measurements imply that the peak of the southern arm is an active and young star-forming region, whereas the central part of NGC 3110 is a site of long-continued star formation. We suggest that, during the early stage of the galaxy-galaxy interaction with large mass ratio that in NGC 3110, fragmentation along the main galaxy’s arms is an important driver of merger-induced star formation and massive gas inflow results in dusty nuclear starbursts.

# Introduction

Studying star formation processes in various galaxies provides us critical information to unveil how galaxies are formed and evolved in time and thus to investigate the origin of the Hubble sequence (cite: Hubble26; Kennicutt98a). When two galaxies approach each other, they exert tidal forces and change their morphology. In the case of gas-rich galaxies, large-scale inflow supplies molecular gas to the central regions, resulting in the burst of nuclear star formation (cite: Barnes92; Mihos96). On the other hand, recent observational and theoretical works have revealed that, at the early-to-mid stage of the interaction, the merger-driven star formation is more dominated by gas fragmentation across the progenitor’s disks (cite: Teyssier10; Elmegreen17; Pettitt17; Tomicic18), or in a filamentary structure between the progenitors (cite: Saitoh09; Iono13; Saito15; Kaneko18).

In order to improve our understanding of the non-linear response of gas during a collision, we require high quality millimeter/submillimeter molecular line data which can trace the distribution and kinematics of cold molecular gas, the reservoir for future star formation. For nearby galaxies, low-$J$ $^{12}$CO, $^{13}$CO, and C$^{18}$O lines ($n$ $\simeq$ 10$^2$-10$^3$ cm$^{-3}$) are usually employed to trace the total column density and the response of H$_2$ gas to violent merger events. The optically-thin $^{13}$CO and C$^{18}$O lines are rather important to constrain physical properties of the diffuse molecular ISM.

![](fig_irac.png)

A gas-rich nearby interacting galaxy NGC 3110 ($D_{\rm L}$ = 69.4 Mpc; 1$''$ = 325 pc), which is classified as a nearby luminous infrared galaxy (LIRG) ($L_{\rm IR}$ = 10$^{11.1}$ $L_{\odot}$; (cite: Armus09)), is one of the best targets to study starbursts in early-stage interactions (Figure [1](#fig:irac)), because of its uniqueness as well as rich multi-wavelength observations and detailed simulations reproducing its interacting nature in the literature (e.g., (cite: Espada18)). It consists of a central bar-like north-south elongation and a pair of asymmetric arms extending from the center, which are considered to be due to the tidal interaction with a companion galaxy MCG-01-26-013 located $\sim$38 kpc southwest from the center of NGC 3110 (cite: Espada18). A recent near-IR survey (cite: Randriamanakoto13; Randriamanakoto15; Randriamanakoto17) reported the detection of more than 280 super star cluster (SSC) candidates across the disk, implying that NGC 3110 is one of the SSC-richest LIRGs in the low-redshift Universe. These SSCs, gravitationaly bound objects, are young and massive star clusters likely to form in strong starbursts and during galaxy-galaxy merging process (cite: Whitmore99; Randriamanakoto19). Given its uniqueness and active star formation, studying NGC 3110 can provide valuable information for understanding how starbursts are triggered in early-stage mergers.

Another unique feature of this galaxy is the bright H$\alpha$ blob at the southern edge of the southern tidal arm (cite: Hattori04). (cite: Espada18) mapped $^{12}$CO($2\text{--}1$) with $\sim$1-kpc spatial resolution, and found an asymmetric gas distribution with a strong concentration around the nucleus, which coincide with the H$\alpha$ structures. They found that the average star formation efficiency (SFE) in the spiral arms is $\sim$0.5dex higher than that in the circumnuclear region, implying that off-centered starbursts are triggered in early stages of the merger. They also carried out hydrodynamical minor merger simulations in order to reproduce the morphological characteristics (e.g., rotation curve) seen in their $^{12}$CO($2\text{--}1$) map and H$\alpha$ map. They concluded that the prominent asymmetric two-armed structures in NGC 3110 is formed at $\sim$150 Myr after the closest approach, and the system is experiencing one of the highest star formation rate (SFR) episodes as a result of the fly-by interaction with the minor companion galaxy.

Most of previous extragalactic molecular gas studies including NGC 3110 assumed a single $^{12}$CO luminosity to H$_2$ gas mass conversion factor ($\alpha_{\rm CO}$), which is likely to spatially vary among and within galaxies (cite: Bolatto13; Sandstrom13), to derive the H$_2$ gas mass surface density and some relevant quantities such as SFE. In order to better understand the missing properties of molecular gas, including $\alpha_{\rm CO}$, and the relation to star formation in merging galaxies, we have conducted multi-CO ALMA observations toward NGC 3110.

This paper is organized as follows: the ALMA observations, the data reduction, and the photometry method are summarized in Section [2](#sec:data) and results are briefly summarized in Section [3](#sec:results). We describe how we derive the physical properties, e.g., H$_2$ gas mass, kinetic temperature, extinction-corrected SFR, and SSC number density, in Section [4](#sec:derive). We discuss the star formation properties of NGC 3110 and their relation to the interaction event using the derived quantities (Section [5](#sec:discussion)), and then summarize and conclude this Paper in Section [6](#sec:summary). We have adopted H$_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_m$ = 0.3, and $\Omega_{\Delta}$ = 0.7 throughout this Paper.

# Observations and Data Reduction

## ALMA Observations

Observations of $^{12}$CO and its isotopologues toward NGC 3110 were carried out during the ALMA cycle 2 period (ID: 2013.1.01172.S). We set four spectral setups whose upper sideband were tuned to $^{12}$CO or $^{13}$CO. The main targeted lines are $J$ = 1–0 (Band 3) and 2–1 (Band 6) transitions of $^{12}$CO, $^{13}$CO, and C$^{18}$O. All data were obtained during 2014–2015. The single-sideband system temperature at Band 3 and Band 6 are 40–155 K and 65–135 K, respectively. The assigned antenna configurations for the Band 3 and Band 6 observations had 29–41 and 35–38 12 m antennas with the projected baseline length between 15–558 m and 15–348 m, respectively. Each tuning had four spectral windows (spws) to cover both sidebands. All spws had a bandwidth of 1.875 GHz with 7.812 MHz resolution. We used 3 pointings to cover all gaseous structures found in the $^{12}$CO($2\text{--}1$) image taken by the Submillimeter Array (cite: Espada10; Espada18), although one pointing is enough for the Band 3 observations. All observation setups are summarized in Table [1](#table_obs).

## Data Reduction

Data calibration and imaging were done using the Common Astronomy Software Applications package (`CASA`) version 4.2.2 (cite: McMullin07). When we reconstructed a $^{12}$CO($2\text{--}1$) image cube using the visibility data delivered from the observatory, we saw periodical linear patterns along one direction which were different from thermal noise structure. Thus, we carefully checked the visibility data and then flagged some data points whose amplitude deviated from the average value around a given baseline length. This additional flagging, as a result, suppressed the periodic patterns. We adopt this flagging reduction scheme to all ALMA data sets shown in this paper.

Images were reconstructed with the natural $uv$ (robustness parameter = 2.0) weighting and the velocity resolution of 20 or 40 km s$^{-1}$ depending on the achieved signal-to-noise ratio of the targeted lines. Continuum emission was subtracted in the $uv$ domain by fitting the line-free channels in both upper sideband and lower sideband with a first order polynomial function. The line-free channels were used to make a continuum image using the multi-frequency synthesis method. We used the CASA task `tclean` in multi-scale mode to make use of the multiscale CLEAN deconvolution algorithm (cite: Cornwell08). All imaging properties for detected molecular lines including sensitivity and beam size are listed in Table [2](#table_line). Throughout this paper, we adopt the typical systematic errors on the absolute flux calibration of 5% and 10% for the Band 3 and Band 6 data, respectively (cite: Lundgren13).

Before making line intensity ratio maps, we flagged the $uv$ range below 10 k$\lambda$, so that the maximum recoverable scale (MRS) of each ALMA image is the same. The MRS definition we used in this paper is, $$\begin{equation}
{\rm MRS} \approx 0.6\frac{\lambda_{\rm obs}}{L_{\rm min}},
\end{equation}$$ where $\lambda_{\rm obs}$ is the observed wavelength and $L_{\rm min}$ is the minimum projected baseline length (cite: Lundgren13). The minimum $uv$ distance is determined by the configuration of the $^{12}$CO($2\text{--}1$) observations. Since the truncated $uv$ range at 10 k$\lambda$ corresponds to the MRS of $\sim$10.7$''$ (3.5 kpc), we do not consider the missing flux effect on structures smaller than 10.7$''$. However, we caution that our $^{12}$CO($1\text{--}0$) data miss some extended emission (recovered flux $=$ 77 $\pm$ 15 %) compared to single dish measurement (395 $\pm$ 79 Jy km s$^{-1}$; (cite: Sanders91)), which may affect our measurements on 3.0$''$ apertures, although fainter line data tend to be less affected. The aperture size is smaller than the MRS (described in Section [2.4](#sec:photometry)). We made all maps and flux measurements after correcting for the primary beam attenuation. Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution. We note that we use the original (i.e., untruncated) data for the gas mass measurement in this paper, although for all works requiring any line ratio we use the truncated data.

After imaging, we created moment maps following the steps described here: (1) clip the $^{12}$CO($1\text{--}0$) datacube at 3$\sigma$ (see Table [2](#table_line)), (2) convert the clipped cube to a 1/0 mask, (3) expand the mask by convolving by 2.0$''$ beam, and (4) collapse the datacubes after applying the expanded mask with 2.5$\sigma$ clipping for the $^{12}$CO data and 1.5$\sigma$ for the other fainter data. This procedure allows us to include faint structures neighboring strong structures, as well as exclude patchy faint structures which are likely artifacts.

![](fig_showline.png)

## Ancillary Data

In addition to the ALMA data, we use the H$\alpha$ map obtained with Okayama Astrophysical Observatory (OAO) 188 cm telescope. The observations and data reduction are described in detail in (cite: Hattori04). The reported spatial resolution is 1.35$''$, which is similar to the ALMA resolution. We also download the 1.4 GHz radio continuum map taken by Karl G. Jansky Very Large Array (VLA) from VLA Data Archive[^1]. These maps are used to construct an extinction-corrected SFR map (see Section [4](#sec:derive)). Furthermore, we use a high-quality $K$-band map obtained by Very Large Telescope (VLT) (see (cite: Randriamanakoto13) for details of the data), which provides the spatial distribution of SSCs.

## Nyquist-sampled Aperture Photometry

In order to decrease the number of correlated data points and to unify the flux measurement method among images taken with different telescopes, a hexagonal Nyquist sampling (aperture diameter $=$ 3.0$''$, aperture separation $=$ 1.5$''$) was performed on all data taken by ALMA and complementary data from the OAO (H$\alpha$), VLT ($K$-band), and VLA (radio continuum) observations. In addition, the hexagonal gridding is one of the popular ways to analyze spatially-resolved extragalactic systems (cite: Sandstrom13; denBrok21). The Nyquist-sampled data points with flux stronger than 3$\sigma$ will be used to derive physical parameters (Section [4](#sec:derive)) and to reconstruct physical parameter images.

We converted the observed integrated line flux density, $S\Delta v$ (Jy beam$^{-1}$ km s$^{-1}$) to integrated line intensity, $I$ (K km s$^{-1}$) using this conversion factor, $\beta$, $$\begin{equation}
\frac{\beta}{\rm Jy\:beam^{-1}\:K^{-1}} = 1.222 \times 10^6\left(\frac{\theta_{\rm maj}\theta_{\rm min}}{\rm arcsec^2}\right)^{-2}\left(\frac{\nu_{\rm obs}}{\rm GHz}\right)^{-2},
\end{equation}$$ where $\theta_{\rm maj}$ and $\theta_{\rm min}$ are the FWHM sizes in the major and minor axis of the synthesized beam, respectively, and $\nu_{\rm obs}$ is the observed frequency.

The integrated line intensity per aperture, $I_{\rm area}$, was calculated by, $$\begin{equation}
\frac{I_{\rm area}}{\rm K\:km\:s^{-1}} = \frac{\sum_{i}^{N_{\rm px,area}}I_{\rm px,i}}{N_{\rm px,area}},
\end{equation}$$ where $I_{\rm px,i}$ is the integrated line intensity at $i$-th pixel (K km s$^{-1}$), $N_{\rm px,area}$ is the number of pixels within the 3.0$''$ aperture. $I_{\rm px,i}$ is same as $\beta(S\Delta v)_{\rm px,i}$, where $(S\Delta v)_{\rm px,i}$ is the observed line flux density at $i$-th pixel in Jy beam$^{-1}$ km s$^{-1}$ unit. When calculating the ALMA and VLA continuum brightness temperatures per apertures, one just needs to replace $I_{\rm area}$, $I_{\rm px,i}$, $(S\Delta v)_{\rm px,i}$ with $T_{\rm b,area}$ (K), $T_{\rm b,px,i}$ (K), $(S_{\nu_{\rm obs}})_{\rm px,i}$ (Jy beam$^{-1}$), respectively.

The statistical noise (i.e., sensitivity) per aperture, $\sigma_{\rm stat}(I_{\rm area})$, was calculated by the following equation (cite: Hainline04), $$\begin{equation}
\frac{\sigma_{\rm stat}(I_{\rm area})}{\rm K\:km\:s^{-1}} = \beta\sigma_{\rm ch}V_{\rm ch}\sqrt{N_{\rm ch}},
\end{equation}$$ where $\sigma_{\rm ch}$ is the median single-channel rms per pixel (Jy beam$^{-1}$), $V_{\rm ch}$ is the velocity width of a channel, and $N_{\rm ch}$ is the number of channels integrated over. For the continuum data, we used, $$\begin{equation}
\frac{\sigma_{\rm stat}(T_{\rm b,area})}{\rm K} = \beta\sigma_{\rm rms},
\end{equation}$$ where $\sigma_{\rm rms}$ is the median rms per pixel.

When we consider the systematic error of the absolute flux calibration, $\sigma_{\rm sys}$, as well as $\sigma_{\rm stat}$, we combined both errors using the equation below, $$\begin{equation}
\sigma_{\rm tot} = \sqrt{\sigma_{\rm stat}^2 + \sigma_{\rm sys}^2},
\end{equation}$$ where we assume that both errors are independent. Note that all the maps shown in this paper are clipped based on $\sigma_{\rm stat}$, whereas the error bars in all the plots are calculated based on $\sigma_{\rm tot}$.

Hereafter, integrated flux density and integrated intensity of a certain line, for example $^{12}$CO($1\text{--}0$), will be written as $S_{\rm CO(1-0)}\Delta v$ and $I_{\rm CO(1-0)}$, respectively.

The line luminosity per aperture can be calculated from, $$\begin{equation}
\frac{L'_{\rm line}}{\rm K\:km\:s^{-1}\:pc^2} = 3.25 \times 10^7S_{\rm line}\Delta v\:\nu_{\rm obs}^{-2}D_{\rm L}^{2}(1 + z)^{-3},
\end{equation}$$ where $D_{\rm L}$ is the luminosity distance ($=$ 69.4 Mpc), and $z$ is the redshift (cite: Solomon05). In this paper, the $^{12}$CO($1\text{--}0$) luminosity is used to calculate $\alpha_{\rm CO}$.

![](fig_showcont.png)

# Results

Figure [2](#fig:showline) shows the integrated intensity and intensity-weighted velocity maps of the $^{12}$CO, $^{13}$CO, and C$^{18}$O lines. We confirm a bright central north-south bar-like elongated structure, a northern shorter arm and a southern longer arm in all the $^{12}$CO, $^{13}$CO, and C$^{18}$O lines, which were previously identified by Submillimeter Array observations (cite: Espada10; Espada18). Moreover, diffuse flocculent components filling in the inter-arm regions are also identified in $^{12}$CO, which coincide with the diffuse, clumpy H$\alpha$ components (cite: Hattori04). The $^{12}$CO velocity fields show rotating disk-like signature with a “S"-shape non-circular motion, indicating the presence of inflow motions and/or a warped disk as seen in other galaxies (cite: Espada12; Saito17b).

Both the $^{13}$CO and C$^{18}$O images coincide with strong features in the $^{12}$CO images. Similar to the asymmetric spiral structures seen in the H$\alpha$, SSC, and CO maps (cite: Espada18), we found a remarkably thin, long southern arm and an isolated blob at the south part of the northern arm in those isotopologue lines. We note that C$^{18}$O($1\text{--}0$), which is also covered by one of our tunings, was marginally detected only around the very center, and thus we do not utilize this line in this paper.

## Band 3 and 6 Continuum Emission

We detected 2.9 mm (Band 3) and 1.3 mm (Band 6) continuum emission toward the central bar-like structure and some parts of the arms in NGC 3110 (Figure [3](#fig_contin)). For normal star-forming galaxies without strong AGN signature, the 1.3 mm continuum emission is mostly dominated by thermal dust emission whereas thermal free-free emission dominates the 2.9 mm continuum emission with minor contribution from non-thermal synchrotron emission (cite: Condon92; Saito16). We will discuss the physical origin of the emission based on the spectral index in Section [4](#sec:derive).

## Line Intensity Ratios

Here we present line ratios made from some combinations of the observed CO lines which are sensitive to galactic scale physical properties of molecular gas ISM. The notations of intensity ratios are defined as,

$$\begin{eqnarray}
^{X}R_{J_uJ_l/J'_uJ'_l} &\equiv& \frac{I_{X(J_u-J_l)}}{I_{X(J'_u-J'_l)}} \\
^{X/Y}R_{J_uJ_l} &\equiv& \frac{I_{X(J_u-J_l)}}{I_{Y(J_u-J_l)}} \nonumber
\end{eqnarray}$$ where the first indicates a ratio of different transitions for the main molecule or its isotopologue, and the second indicates a ratio of different isotopes for the same line transition. The spatial distributions of the $J$ $=$ 2–1/$J$ $=$ 1–0 ratios, $^{\rm 12}R_{21/10}$ and $^{\rm 13}R_{21/10}$, are shown in Figure [4](#fig_ratio) top. The $^{\rm 12}R_{21/10}$ shows a smooth distribution over the entire arms and bar-like elongation ($\sim$0.8 on average). The $^{\rm 13}R_{21/10}$ peaks at the center ($\sim$1.0) with lower values at the ends of the elongation ($\sim$0.7) and the southern arm ($\sim$0.4). The spatial distributions of the $^{12}$CO/$^{13}$CO ratios, $^{\rm 12/13}R_{10}$ and $^{\rm 12/13}R_{21}$, are shown in Figure [4](#fig_ratio) bottom. Unlike the $^{\rm 12}R_{21/10}$ and $^{\rm 13}R_{21/10}$ distributions, $^{\rm 12/13}R_{21}$ shows lower value ($\sim$10) at the nuclear region, higher values ($\sim$30) toward $\sim$5$''$$\:$ east and west from the nucleus, and then lower values again at the tip of the southern arm (Figure [4](#fig_ratio) bottom). $^{\rm 12/13}R_{10}$ also shows a similar trend although the low signal-to-noise ratio is insufficient. Those spatial variations can be clearly seen in the radial profiles in Figure [5](#fig_radial_ratio).

![](fig_showratio.png)

# Derivation of Physical Parameters

In this Section, we describe how we derive $\alpha_{\rm CO}$, spectral index between 1.3 mm and 2.9 mm, extinction-corrected SFR, and the number density of SSC based on the data taken by using the Nyquist-sampled 3.0$''$ apertures. The derived parameters are visualized in Figure [6](#fig_Nyquist).

## Non-LTE Calculation using RADEX

We used the non-local thermodynamic equilibrium (LTE) radiative transfer code `RADEX` (cite: vanderTak07) and compare with the observed line ratios. We derived the physical conditions of molecular gas, assuming a single-phase ISM (i.e., the gas physics can be represented by a single set of the excitation parameters), an expanding sphere geometry ($dv$ $=$ 100 km s$^{-1}$), the cosmic microwave background temperature ($T_{\rm bg}$ = $T_{\rm CMB}$ $=$ 2.73K), and \[CO\]/\[H$_2$\] ($=$ 3 $\times$ 10$^{-4}$) and \[CO\]/\[$^{13}$CO\] ($=$ 70) abundances which are same as those applied for the LTE calculation described later. The upper state energies and the Einstein coefficients were taken from the *Leiden Atomic and Molecular Database* (cite: Schoier05). We made model grids within a range of the gas kinetic temperature ($T_{\rm kin}$) $=$ 5-205 K, the gas volume density ($n_{\rm H_2}$) $=$ 10$^{2.0}$-10$^{7.0}$ cm$^{-3}$, and H$_2$ gas column densities ($N_{\rm H_2}$) $=$ 10$^{22.0}$-10$^{22.5}$ cm$^{-2}$. After deriving best-fit values at each aperture via a $\chi^2$ minimization, we made Nyquist-sampled $T_{\rm kin}$ and $n_{\rm H_2}$ images as shown in Figures [6](#fig_Nyquist) top-left and top-center. We regard the 90% confidence area in the parameter space as the uncertainty of the derived $T_{\rm kin}$ and $n_{\rm H_2}$ following the standard way (cite: Sliwa14).

## The CO-to-H$_2$ Conversion Factor

For extragalactic objects, the $^{12}$CO($1\text{--}0$) and $^{12}$CO($2\text{--}1$) lines are popular and well calibrated as H$_2$ gas mass tracers (cite: Bolatto13). This is mainly because the sensitivity of the radio instruments is not enough to detect optically-thin low density molecular gas tracers. Recent high-sensitivity interferometric studies provided several ways to calibrate $\alpha_{\rm CO}$: gas mass measured by kinematics (cite: Downes&Solomon98), gas-to-dust ratio (cite: Sandstrom13), and radiative transfer analysis with multiple molecular lines (cite: Sliwa17).

In this paper, we estimate H$_2$ gas mass ($M_{\rm H_2}$) with two different methods and then compare with $L'_{\rm CO(1-0)}$.

![](fig_radial.png)

### LTE Mass Derivation

One reliable way to estimate $M_{\rm H_2}$ is to utilize optically-thin molecular gas tracers. In this paper, we observed two transitions of $^{13}$CO, which are usually thought to be optically-thin, in order to solve the radiative transfer equation. Multiple transition data allow us to directly estimate the excitation temperature ($T_{\rm ex}$) and the column density of the molecule assuming LTE, resulting in accurate molecular gas mass ($M_{\rm LTE}$). Since the number of apertures with detection of both $^{13}$CO transitions higher than 3$\sigma$ is less than 20 (mostly around the nuclear region and the southern arm), we first determine the typical $T_{\rm ex}$ for those $\lesssim$20 apertures and then assume a single $T_{\rm ex}$ in order to derive the column density for much more apertures. Here we employ the following equation:

$$\begin{eqnarray}
\label{eqn_rot}
\frac{I_{\rm ^{13}CO}}{\rm K\:km\:s^{-1}} &=& \frac{8\pi S\mu_0^2\nu N_{\rm ^{13}CO}}{3kQ(T_{\rm rot})}\left\{1 - \frac{\exp(h\nu/kT_{\rm rot}) - 1}{\exp(h\nu/kT_{\rm bg}) - 1}\right\}\nonumber \\
&&\times\exp\left(-\frac{E_{\rm u}}{kT_{\rm rot}}\right),
\end{eqnarray}$$ where $S$, $\mu_0$, $\nu$, $N_{\rm ^{13}CO}$, $k$, Q($T_{\rm rot}$), $T_{\rm rot}$, $h$, $T_{\rm bg}$, and $E_{\rm u}$ are line strength, dipole moment, transition frequency, total column density of $^{13}$CO, the Boltzmann constant, the partition function, rotation temperature which is the same as $T_{\rm ex}$, the Planck constant, the cosmic microwave background temperature, and upper state energy, respectively (e.g., (cite: Goldsmith99; Watanabe14; Nakajima18)). We took the transition parameters necessary for calculating the equation from Splatalogue[^2] and the *Cologne Database for Molecular Spectroscopy* (cite: Muller01; Muller05).

The median and average $T_{\rm rot}$ are 15.1 K and 15.4 K, respectively. Thus we substituted $T_{\rm rot}$ $=$ 15 K for the equation [\[eqn_rot\]](#eqn_rot) in order to estimate $N_{\rm ^{13}CO}$ for all apertures with $^{13}$CO($2\text{--}1$) detection. Then, $M_{\rm LTE}$ is derived by using this equation: $$\begin{equation}
\frac{M_{\rm LTE}}{M_{\odot}} = 1.36\frac{N_{\rm ^{13}CO}}{\rm [^{13}CO]/[H_2]}\:m_{\rm H_2}A_{\rm aperture},
\end{equation}$$ where $m_{\rm H_2}$ is the mass of the hydrogen molecule, $A_{\rm aperture}$ is the area of the apertures, and \[$^{13}$CO\]/\[H$_2$\] is the $^{13}$CO abundance relative to H$_2$. Here we assumed \[$^{13}$CO\]/\[H$_2$\] $=$ 4.3 $\times$ 10$^{-6}$, that is similar to the standard value observed in Galactic warm, star-forming molecular clouds (\[$^{12}$CO\]/\[$^{13}$CO\] $=$ 70, \[$^{12}$CO\]/\[H$_2$\] $=$ 3.0 $\times$ 10$^{-4}$; e.g., (cite: Blake87; Lacy94)). These are commonly used values in (U)LIRG studies (cite: Sliwa14). In order to accurately constrain the abundance ratios in NGC 3110, we need a more sophisticated modeling with increasing the number of input maps and their quality. We multiply by 1.36 to account for the Helium abundance relative to hydrogen. The derived 16$^{th}$–50$^{th}$–84$^{th}$ percentiles of $\alpha_{\rm LTE}$ ($=$ $M_{\rm LTE}$/$L'_{\rm CO(1-0)}$) are 1.30–1.69–2.21 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$. The radial distribution of the derived $\alpha_{\rm LTE}$ with $T_{\rm rot}$ $=$ 15 K is shown as the red data points in Figure [7](#fig_alpha) left. The spatial distribution is also shown in Figure [6](#fig_Nyquist) bottom-left.

Here we also derived $\alpha_{\rm LTE}$ using $T_{\rm kin}$ ($=$ $\alpha_{\rm LTE}$($T_{\rm kin}$)) derived in Section [4.1](#radex), instead of the fixed $T_{\rm rot}$, based on a reasonable assumption that CO excitation is entirely dominated by collision with H$_2$. However, low temperature and low density gas are not usually in thermal equilibrium, so that we expect $T_{\rm rot}$ $<$ $T_{\rm kin}$. Thus, $\alpha_{\rm LTE}$($T_{\rm kin}$) give the upper limit. Indeed, we confirmed that $\alpha_{\rm LTE}$($T_{\rm kin}$) are $\gtrsim$2 times larger than $\alpha_{\rm LTE}$($T_{\rm rot}$).

![](fig_showhex.png)

![](fig_aco.png)

### ISM Mass Derivation

One of the other methods to estimate the molecular gas mass is to utilize the Rayleigh-Jeans part of the thermal dust continuum emission as described by (cite: Scoville16). We derived molecular ISM masses ($M_{\rm ISM}$) from the 1.3 mm dust continuum emission using the following equation; $$\begin{eqnarray}
\frac{M_{\rm ISM}}{10^{10} M_{\odot}} &=& 1.78\:S_{\rm\nu_{obs}}(1 + z)^{-4.8}\left(\frac{\nu_{\rm obs}}{\nu_{\rm 850\mu m}}\right)^{-3.8}\left(\frac{D_{\rm L}}{\rm Gpc}\right)^2 \nonumber\\
&\times& \left(\frac{6.7 \times 10^{19}}{\alpha_{\rm 850}}\right)\frac{\Gamma_0}{\Gamma_{\rm RJ}},
\end{eqnarray}$$ where $S_{\rm\nu_{obs}}$ is the observed continuum flux, $\nu_{\rm 850\mu m}$ is 353 GHz, $\nu_{\rm obs}$ is the observed frequency (= 235 GHz), $\alpha_{\rm 850}$ is the calibration constant corresponding to 6.7 $\times$ 10$^{19}$ erg s$^{-1}$ Hz$^{-1}$ $M_{\odot}^{-1}$ introduced by (cite: Scoville16), and $\Gamma_{\rm RJ}$ and $\Gamma_{\rm 0}$ is given by, $$\begin{eqnarray}
\Gamma_{\rm RJ}(T_{\rm d}, \nu_{\rm obs}, z) &=& \frac{h\nu_{\rm obs}(1 + z)/kT_{\rm d}}{e^{h\nu_{\rm obs}(1 + z)/kT_{\rm d}} - 1} \\
\Gamma_{\rm 0} &=& \Gamma_{\rm RJ}(T_{\rm d}, \nu_{\rm 850\mu m}, 0)
\end{eqnarray}$$ where $T_{\rm d}$ is the dust temperature. Here, we adopt $T_{\rm d}$ $=$ $T_{\rm rot}$ (= 15 K) in order to estimate $\alpha_{\rm ISM}$ (= $M_{\rm ISM}$/$L'_{\rm CO(1-0)}$), based on the empirical relationship between molecular gas condition and dust heating (cite: Koda20; Liu21).

The radial $\alpha_{\rm ISM}$ distributions as well as $\alpha_{\rm LTE}$ are shown in Figure [7](#fig_alpha) left. The derived 16$^{th}$–50$^{th}$–84$^{th}$ percentiles of $\alpha_{\rm ISM}$ are 1.08–1.48–2.26 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$.

### Appropriate $\alpha_{\rm CO}$ for NGC 3110

We found the two methods show a non-monotonic trend (i.e., decreasing then increasing). However, we assume a flat $\alpha_{\rm CO}$ hereafter, as the $\alpha_{\rm CO}$ assumption (e.g., varying or constant) does not affect the discussion of this paper (see Appendix [7](#App1)). The assumed flat $\alpha_{\rm CO}$ distribution is consistent with spatially-resolved $\alpha_{\rm CO}$ values for other nearby spirals (cite: Sandstrom13) and a LIRG NGC 1614 (cite: Saito17b). Figure [7](#fig_alpha) (right) shows the histogram of $\alpha_{\rm ISM}$($T_{\rm rot}$) with a best-fit Gaussian (peak $=$ 1.73 and dispersion $=$ 0.48). In this paper, we adopt a fixed $\alpha_{\rm CO}$ of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ when measuring gas masses. Note that this $\alpha_{\rm CO}$ value is consistent with values derived for other (U)LIRGs (cite: Sliwa17).

The increasing $\alpha_{\rm LTE}$ trend around the central kpc of NGC 3110 is opposite to the trend found around the center of nearby galaxies (cite: Sandstrom13; Saito17b). We explain that this increasing trend is due to the assumed constant $T_{\rm rot}$. According to equation [\[eqn_rot\]](#eqn_rot), two times higher $T_{\rm rot}$ results in $\lesssim$0.5dex lower $N_{\rm ^{13}CO}$. Thus, the $\alpha_{\rm LTE}$ trend will be flattened or even inversed if we are able to measure $T_{\rm rot}$ at each aperture. Although one of our original motivations to observe multiple transitions is to study the temperature effect on the gas mass measurements around the galaxy centers, the signal-to-noise ratios of our $^{13}$CO($1\text{--}0$) map is insufficient to measure the spatial $T_{\rm rot}$ distribution.

## Spectral Index: Two Thermal Components

The millimeter/submillimeter part of the spectral energy distribution of a star-forming galaxy is known to be dominated by nonthermal (synchrotron) and thermal (free-free and cold dust) emission (cite: Condon92). Especially, the two thermal components are more important at the higher frequency regime ($\gtrsim$100 GHz), because the steep negative spectral index of the nonthermal continuum ($\alpha$ $\sim$ $-$0.8) makes it weaker than the other two ($\alpha$ $\sim$ $-$0.1 and 2-4 for free-free and dust, respectively). Based on our Band 3 and Band 6 data, we can roughly study the continuum property using the following equation:

$$\begin{equation}
\alpha_{\nu_2}^{\nu_1} = \log_{\frac{\nu_1}{\nu_2}}\frac{S_{\nu_1}}{S_{\nu_2}}
\end{equation}$$ where $\nu_i$ is the observed frequency, and $S_{\nu_i}$ is the observed flux at $\nu_i$. The derived spectral index image is shown in Figure [6](#fig_Nyquist) top-right. We found the central part of NGC 3110 is dominated by the steep dust emission, although the southern tip of the southern arm shows relatively low spectral index ($\gtrsim$0.4), implying non-negligible contribution from the free-free emission (i.e., H II regions containing ionizing stars).

## SFR Derivation and Extinction Correction

Here we calculate the other important physical parameter, SFR based on previous H$\alpha$ data taken by OAO (cite: Hattori04) and archival 1.4 GHz continuum.

In order to estimate extinction-corrected H$\alpha$ luminosity ($L({\rm H_{\alpha}})_{\rm corr}$), we used the prescription described by (cite: Kennicutt09), $$\begin{equation}
\frac{L({\rm H_{\alpha}})_{\rm corr}}{\rm erg\:s^{-1}} = L({\rm H_{\alpha}})_{\rm obs} + 0.39 \times 10^{13}L(\rm 1.4GHz),
\end{equation}$$ where $L({\rm H_{\alpha}})_{\rm obs}$ is the observed H$\alpha$ luminosity in erg s$^{-1}$ unit and $L(\rm 1.4GHz)$ is the observed 1.4 GHz radio continuum luminosity in erg s$^{-1}$ Hz$^{-1}$ unit. Then, we measure extinction-corrected SFR at each aperture using the following equation (see (cite: Kennicutt12) for a review), $$\begin{equation}
\frac{\rm SFR}{\rm M_{\odot}\:yr^{-1}} = \frac{L({\rm H_{\alpha}})_{\rm corr}}{10^{41.27}}.
\end{equation}$$ The derived total SFR from the extinction-corrected H$\alpha$ data (i.e., summed over all independent apertures) is $\sim$18 $M_{\odot}$ yr$^{-1}$(Figure [6](#fig_Nyquist) middle-left).

We caution that the employed extinction-correction prescription is based on the global measurements (see (cite: Kennicutt09)), and therefore our spatially-resolved SFRs are uncertain. However, we confirmed that the measured total SFR is in agreement with values derived in the literature: (cite: U12) derived $\sim$24 $M_{\odot}$ yr$^{-1}$ based on the IR SED, and (cite: Espada18) derived 19.7 $M_{\odot}$ yr$^{-1}$ and 21.2 $M_{\odot}$ yr$^{-1}$ based on H$\alpha$+24 $\mu$m and 24 $\mu$m, respectively. In addition, the global trend seen in the Kennicutt-Schmidt (KS) relation (see next Section) is also consistent with the relation described in (cite: Espada18) (although the scatter is larger in our KS relation, which is clearly seen in data points with the deprojected distance from 3 to 6.5 kpc). After these double-checking, we decided to use this prescription in this paper. Constructing an accurate SFR map at high angular resolution comparable to the ALMA resolution is beyond the scope of this paper, but a necessary step to further understanding the star formation activities in NGC 3110.

![](fig_scatter.png)

## Kennicutt-Schmidt Relation

We plot the ($\sim$1 kpc-scale) NGC 3110 data points on the Kennicutt-Schmidt $\Sigma_{\rm SFR}$ - $\Sigma_{\rm H_2}$ relation (cite: Kennicutt98b) as shown in Figure [8](#fig_sfe) top-left. Note that if adopting variable $\alpha_{\rm LTE}$ the KS relation does not qualitatively change, and even the difference between the circumnuclear region and the arms becomes larger; i.e., the central part of this galaxy shows higher densities, and SFE ($=$ $\Sigma_{\rm SFR}$/$\Sigma_{\rm H_2}$) is high 7-8 kpc away from the nucleus. The SFE map using a fixed $\alpha_{\rm CO}$ is shown in Figure [6](#fig_Nyquist) middle-right. The highest SFE can be found inside the red circle around the southern tip of the southern arm.

Comparing with similar resolution ($\sim$0.75 kpc) data for local non-interacting spiral galaxies (cite: Bigiel08), NGC 3110 shows comparable or higher $\Sigma_{\rm SFR}$ and $\Sigma_{\rm H_2}$ than spiral galaxies with highest $\Sigma_{\rm SFR}$ ($\lesssim$1 $M_{\odot}$ kpc$^{-2}$ yr$^{-1}$) and $\Sigma_{\rm H_2}$ ($\lesssim$10$^{2.5}$ $M_{\odot}$ pc$^{-2}$) even though NGC 3110 is an early stage of interaction. The SFEs of NGC 3110 range from 10$^{-8}$ to 10$^{-9}$ yr$^{-1}$, which is higher than that of spiral galaxies ($\sim$5 $\times$ 10$^{-10}$ yr$^{-1}$). Especially, at the southern tip of the southern arm (hereafter region “A"; a red circle in Figure [6](#fig_Nyquist)), the SFE is $\sim$10$^{-8}$ yr$^{-1}$, which is $\sim$4 times higher than the average SFE around the nuclear region. Our SFE values are consistent with previous SFE values (cite: Espada18) if we use the same $\alpha_{\rm CO}$ they assumed (i.e., 4.3 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$instead of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$).

We note that the prescriptions to derive SFR are different among this study and other papers introduced in this Section; far-ultraviolet and 24$\mu$m in (cite: Bigiel08), H$\alpha$ and 24$\mu$m in (cite: Espada18), and H$\alpha$ and radio continuum in this study. This introduces systematic uncertainties in the absolute values, and thus hereafter we focus on our own data.

# Discussion

## Star Formation at the Tip of the Southern Arm

The southern tip of the southern arm, region “A", shows the highest SFE among the NGC 3110 data points, which is an unusual feature for spiral galaxies which typically show highest SFE around the center (cite: Leroy08). Here we try to characterize the physical properties of the highest SFE region.

One of the intriguing features seen in the region “A" is the shallow spectral index between 1.3 mm and 2.9 mm. In Figure [8](#fig_sfe) top-right, we plot the SFE against the spectral index. The data points with the deprojected radius $<$ 3 kpc (yellow to red color) tend to distribute around the spectral index $\sim$1–3, indicating dusty star formation at the central region of NGC 3110. In contrast to the center, the outer part, especially the region “A", shows much lower spectral index ($\sim$0.5), implying that 2.9 mm continuum from the region “A" is likely to be significantly contaminated by the free-free emission from ionized gas by young massive stars (typical age $\lesssim$ 10 Myr; (cite: Kennicutt12)). Such ionized gas can be also traced by H$\alpha$ emission, which is used to derive the SFE. Considering that infrared continuum emission (3-1100 $\mu$m) is a good tracer of star formation with the age $\lesssim$ 100 Myr (cite: Kennicutt12), the trend seen in Figure [8](#fig_sfe) top-right tells us the dominant age of the star-forming regions. Thus, the region “A" is likely to be an active and young star-forming region in the disk of NGC 3110, whereas the central part of NGC 3110 is a site of more dusty, long-continued star formation. We note that the discussion of the spectral index in the region “A" is based on a single data point as shown in the top-right panel of Figure [8](#fig_sfe). Although the S/N ratio is sufficient to safely conclude the relatively lower spectral index in the region “A", higher accuracy continuum observations are required to better constrain age differences.

We plot SFE against $\Sigma_{\rm SSC}$ in Figure [8](#fig_sfe) bottom, showing no clear correlation between them. However, it has a tendency that the inner regions (i.e., redder points) show relatively lower SFE ($\gtrsim$10$^9$ yr$^{-1}$) but higher $\Sigma_{\rm SSC}$ ($\sim$10 kpc$^{-2}$). Since the typical age of SSCs is thought to be 10-100 Myr (cite: Randriamanakoto15), the trend seen in Figure [8](#fig_sfe) bottom supports the idea that region “A" is younger massive star-forming region compared with those around the center.

## Early Stage Minor Merger as a Trigger of Wide-spread Star Formation

The relative age difference between the star-forming regions around the central region and region “A" is an important clue to understand the physical origin of the kpc-scale star formation in the disk of NGC 3110. Numerical simulations suggested that tidal interaction between large mass ratio galaxies enhances both a long-lived $m =$ 2 bar and transient asymmetric arms (cite: Iono04; Cox08; Pettitt18). (cite: Espada18) reproduced the morphological characteristics of NGC 3110 using hydrodynamical simulations, and found that NGC 3110 might be experiencing one of the highest SFR epoch during the merger history before coalescence. The typical SSC age is comparable or shorter than the timescale of the merger-induced asymmetric arms in NGC 3110 reproduced by this simulation, which is consistent with the picture that the star-forming region in the region “A" is triggered by tidal interaction. The star-forming regions triggered on the tidally-induced transient arms show clumpy structures in the simulations as we saw in the CO isotope images of NGC 3110 (Figure [2](#fig:showline)). Based on those morphological similarities between NGC 3110 and numerical minor merger simulations, we suggest that the on-going interaction with the smaller companion galaxy MCG-01-26-013 triggers an active, young star-forming region (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$) at the southern tip of the southern arm in NGC 3110. The elevated star-forming activities seen in the center of NGC 3110 might be due to merger-driven tidal torques leading to rapid, large-scale gas inflow.

# Summary

We present $\sim$1.0$''$ resolution ALMA Band 3 and Band 6 observations of the rotational transitions of CO and its isotopologues and continuum emission in the nearby interacting LIRG NGC 3110. NGC 3110 has an asymmetric two-armed spirals and a bar-like structure, both of which are likely to be enhanced during the early stage galaxy merger interaction as suggested by previous molecular gas observations and numerical simulations (cite: Espada18; Pettitt18). Combining our new ALMA datasets with previous H$\alpha$ and 1.4 GHz continuum data, we find that the highest SFE region is located at the southern tip of the southern spiral arm (region “A"). The region “A" is characterized with (1) lower spectral index between 1.3 mm and 2.9 mm ($\lesssim$0.5), i.e., a dominant contribution from free-free emission, (2) high number density of super star clusters ($\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$), and (3) relatively active star formation (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$ and $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$). Those observational evidences support the idea that the region “A" is active, young star-forming region found in NGC 3110. With the strong similarities of the observed gas and star formation properties with numerical minor merger simulations, we suggest that the on-going interaction with a companion galaxy MCG-01-26-013 is the main driver of the star formation at the region “A" as well as the central starburst activities.

To further investigate the physical properties and the origin of the star-forming regions in the disk of NGC 3110, it is essential to understand giant molecular cloud properties, i.e., a site of star formation, which can be addressed by current long baseline capability of ALMA.

Y.K., T.S., and other authors thank ALMA staff for their kind support. This work was supported by the ALMA Japan Research Grant of NAOJ Chile Observatory, NAOJ-ALMA-0114. DE acknowledges support from a Beatriz Galindo senior fellowship (BG20/00224) from the Spanish Ministry of Science and Innovation. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.0.01172.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This NVAS image was produced as part of the NRAO VLA Archive Survey, (c) AUI/NRAO. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. This work is based in part on observations made with the *Spitzer* Space Telescope, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

# Software

`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)

natexlab

(ref: Armus09) Armus, L., Mazzarella, J. M., Evans, A. S., et al. 2009, PASP, 121, 559, doi: [`10.1086/600092`](http://doi.org/10.1086/600092)

(ref: Astropy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Barnes92) Barnes, J. E., & Hernquist, L. 1992, ARA&A, 30, 705, doi: [`10.1146/annurev.aa.30.090192.003421`](http://doi.org/10.1146/annurev.aa.30.090192.003421)

(ref: Bigiel08) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846, doi: [`10.1088/0004-6256/136/6/2846`](http://doi.org/10.1088/0004-6256/136/6/2846)

(ref: Blake87) Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621, doi: [`10.1086/165165`](http://doi.org/10.1086/165165)

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Condon92) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Cornwell08) Cornwell, T. J. 2008, IEEE Journal of Selected Topics in Signal Processing, 2, 793, doi: [`10.1109/JSTSP.2008.2006388`](http://doi.org/10.1109/JSTSP.2008.2006388)

(ref: Cox08) Cox, T. J., Jonsson, P., Somerville, R. S., Primack, J. R., & Dekel, A. 2008, MNRAS, 384, 386, doi: [`10.1111/j.1365-2966.2007.12730.x`](http://doi.org/10.1111/j.1365-2966.2007.12730.x)

(ref: denBrok21) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221, doi: [`10.1093/mnras/stab859`](http://doi.org/10.1093/mnras/stab859)

(ref: Downes&Solomon98) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: Elmegreen17) Elmegreen, D. M., Elmegreen, B. G., Kaufman, M., et al. 2017, ApJ, 841, 43, doi: [`10.3847/1538-4357/aa6ba5`](http://doi.org/10.3847/1538-4357/aa6ba5)

(ref: Espada12) Espada, D., Matsushita, S., Peck, A. B., et al. 2012, ApJL, 756, L10, doi: [`10.1088/2041-8205/756/1/L10`](http://doi.org/10.1088/2041-8205/756/1/L10)

(ref: Espada10) Espada, D., Martin, S., Hsieh, P. Y., et al. 2010, in Galaxies and their Masks, ed. D. L. Block, K. C. Freeman, & I. Puerari, 97, doi: [`10.1007/978-1-4419-7317-7_7`](http://doi.org/10.1007/978-1-4419-7317-7_7)

(ref: Espada18) Espada, D., Martin, S., Verley, S., et al. 2018, ApJ, 866, 77, doi: [`10.3847/1538-4357/aae07e`](http://doi.org/10.3847/1538-4357/aae07e)

(ref: Goldsmith99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209, doi: [`10.1086/307195`](http://doi.org/10.1086/307195)

(ref: Hainline04) Hainline, L. J., Scoville, N. Z., Yun, M. S., et al. 2004, ApJ, 609, 61, doi: [`10.1086/420920`](http://doi.org/10.1086/420920)

(ref: Hattori04) Hattori, T., Yoshida, M., Ohtani, H., et al. 2004, AJ, 127, 736, doi: [`10.1086/381060`](http://doi.org/10.1086/381060)

(ref: Hubble26) Hubble, E. P. 1926, ApJ, 64, 321, doi: [`10.1086/143018`](http://doi.org/10.1086/143018)

(ref: Hunter07) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Iono04) Iono, D., Yun, M. S., & Mihos, J. C. 2004, ApJ, 616, 199, doi: [`10.1086/424797`](http://doi.org/10.1086/424797)

(ref: Iono13) Iono, D., Saito, T., Yun, M. S., et al. 2013, PASJ, 65, L7, doi: [`10.1093/pasj/65.3.L7`](http://doi.org/10.1093/pasj/65.3.L7)

(ref: Kaneko18) Kaneko, H., Kuno, N., & Saitoh, T. R. 2018, ApJL, 860, L14, doi: [`10.3847/2041-8213/aac895`](http://doi.org/10.3847/2041-8213/aac895)

(ref: Kennicutt98a) Kennicutt, Robert C., J. 1998a, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: Kennicutt98b) —. 1998b, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Kennicutt09) Kennicutt, Robert C., J., Hao, C.-N., Calzetti, D., et al. 2009, ApJ, 703, 1672, doi: [`10.1088/0004-637X/703/2/1672`](http://doi.org/10.1088/0004-637X/703/2/1672)

(ref: Kennicutt12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Koda20) Koda, J., Sawada, T., Sakamoto, K., et al. 2020, ApJL, 890, L10, doi: [`10.3847/2041-8213/ab70b7`](http://doi.org/10.3847/2041-8213/ab70b7)

(ref: Lacy94) Lacy, J. H., Knacke, R., Geballe, T. R., & Tokunaga, A. T. 1994, ApJL, 428, L69, doi: [`10.1086/187395`](http://doi.org/10.1086/187395)

(ref: Leroy08) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782, doi: [`10.1088/0004-6256/136/6/2782`](http://doi.org/10.1088/0004-6256/136/6/2782)

(ref: Liu21) Liu, D., Daddi, E., Schinnerer, E., et al. 2021, ApJ, 909, 56, doi: [`10.3847/1538-4357/abd801`](http://doi.org/10.3847/1538-4357/abd801)

(ref: Lundgren13) Lundgren, A. 2013, ALMA Cycle 2 Technical Handbook Version 1.1, ALMA. <https://arc.iram.fr/documents/cycle2/alma-technical-handbook.pdf>

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mihos96) Mihos, J. C., & Hernquist, L. 1996, ApJ, 464, 641, doi: [`10.1086/177353`](http://doi.org/10.1086/177353)

(ref: Muller05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: Muller01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: Nakajima18) Nakajima, T., Takano, S., Kohno, K., Harada, N., & Herbst, E. 2018, PASJ, 70, 7, doi: [`10.1093/pasj/psx153`](http://doi.org/10.1093/pasj/psx153)

(ref: Oliphant06) Oliphant, T. 2006, NumPy: A guide to NumPy, USA: Trelgol Publishing. <http://www.numpy.org/>

(ref: Pettitt17) Pettitt, A. R., Tasker, E. J., Wadsley, J. W., Keller, B. W., & Benincasa, S. M. 2017, MNRAS, 468, 4189, doi: [`10.1093/mnras/stx736`](http://doi.org/10.1093/mnras/stx736)

(ref: Pettitt18) Pettitt, A. R., & Wadsley, J. W. 2018, MNRAS, 474, 5645, doi: [`10.1093/mnras/stx3129`](http://doi.org/10.1093/mnras/stx3129)

(ref: Randriamanakoto15) Randriamanakoto, Z. 2015, PhD thesis, Department of Astronomy, University of Cape Town, Private Bag X3, Rondebosch 7701, South Africa

(ref: Randriamanakoto17) Randriamanakoto, Z., & Väisänen, P. 2017, in Formation, Evolution, and Survival of Massive Star Clusters, ed. C. Charbonnel & A. Nota, Vol. 316, 70–76, doi: [`10.1017/S1743921315010510`](http://doi.org/10.1017/S1743921315010510)

(ref: Randriamanakoto13) Randriamanakoto, Z., Väisänen, P., Ryder, S., et al. 2013, MNRAS, 431, 554, doi: [`10.1093/mnras/stt185`](http://doi.org/10.1093/mnras/stt185)

(ref: Randriamanakoto19) Randriamanakoto, Z., Väisänen, P., Ryder, S. D., & Ranaivomanana, P. 2019, MNRAS, 482, 2530, doi: [`10.1093/mnras/sty2837`](http://doi.org/10.1093/mnras/sty2837)

(ref: Saito15) Saito, T., Iono, D., Yun, M. S., et al. 2015, ApJ, 803, 60, doi: [`10.1088/0004-637X/803/2/60`](http://doi.org/10.1088/0004-637X/803/2/60)

(ref: Saito16) Saito, T., Iono, D., Xu, C. K., et al. 2016, PASJ, 68, 20, doi: [`10.1093/pasj/psv136`](http://doi.org/10.1093/pasj/psv136)

(ref: Saito17b) —. 2017, ApJ, 835, 174, doi: [`10.3847/1538-4357/835/2/174`](http://doi.org/10.3847/1538-4357/835/2/174)

(ref: Saitoh09) Saitoh, T. R., Daisaka, H., Kokubo, E., et al. 2009, PASJ, 61, 481, doi: [`10.1093/pasj/61.3.481`](http://doi.org/10.1093/pasj/61.3.481)

(ref: Sanders91) Sanders, D. B., Scoville, N. Z., & Soifer, B. T. 1991, ApJ, 370, 158, doi: [`10.1086/169800`](http://doi.org/10.1086/169800)

(ref: Sandstrom13) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Schoier05) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: Scoville16) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Sliwa14) Sliwa, K., Wilson, C. D., Iono, D., Peck, A., & Matsushita, S. 2014, ApJL, 796, L15, doi: [`10.1088/2041-8205/796/1/L15`](http://doi.org/10.1088/2041-8205/796/1/L15)

(ref: Sliwa17) Sliwa, K., Wilson, C. D., Matsushita, S., et al. 2017, ApJ, 840, 8, doi: [`10.3847/1538-4357/aa689b`](http://doi.org/10.3847/1538-4357/aa689b)

(ref: Solomon05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: Teyssier10) Teyssier, R., Chapon, D., & Bournaud, F. 2010, ApJL, 720, L149, doi: [`10.1088/2041-8205/720/2/L149`](http://doi.org/10.1088/2041-8205/720/2/L149)

(ref: Tomicic18) Tomičić, N., Hughes, A., Kreckel, K., et al. 2018, ApJL, 869, L38, doi: [`10.3847/2041-8213/aaf810`](http://doi.org/10.3847/2041-8213/aaf810)

(ref: U12) U, V., Sanders, D. B., Mazzarella, J. M., et al. 2012, ApJS, 203, 9, doi: [`10.1088/0067-0049/203/1/9`](http://doi.org/10.1088/0067-0049/203/1/9)

(ref: vanderTak07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: Virtanen20) Virtanen, P., Gommers, R., Oliphant, T., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Watanabe14) Watanabe, Y., Sakai, N., Sorai, K., & Yamamoto, S. 2014, ApJ, 788, 4, doi: [`10.1088/0004-637X/788/1/4`](http://doi.org/10.1088/0004-637X/788/1/4)

(ref: Whitmore99) Whitmore, B. C., Zhang, Q., Leitherer, C., et al. 1999, AJ, 118, 1551, doi: [`10.1086/301041`](http://doi.org/10.1086/301041)

+------+--------------+---------------------------------------------+---------------+---------------------+-----------------+-------------------------------------+---+---+
| Band | UT Date      | Configuration                               | $T_{\rm sys}$ | Spectral Window     | $t_{\rm integ}$ | Calibrator                          |   |   |
+:=====+:=============+:======:+:=============:+:==================:+:=============:+:========:+:========:+:===============:+:=========:+:==========:+:==========:+:=:+:=:+
| 3-5  |              | FoV    | $N_{\rm ant}$ | $L_{\rm baseline}$ |               | USB      | LSB      |                 | Flux      | Bandpass   | Phase      |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
|      |              | ($''$) |               | \(m\)              | \(K\)         | (GHz)    | (GHz)    | (min.)          |           |            |            |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
| B3   | 2014 Jun. 28 | 57.2   | 29            | 19–639             | 40–70         | 107.529  | 95.669   | 26.6            | Ceres     | J1058+0133 | J1008+0621 |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
| B3   | 2015 Mar. 9  | 54.7   | 30            | 15–328             | 55–155        | 112.487  | 100.414  | 28.1            | Ganymede  | J1058+0133 | J1011-0423 |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
| B3   | 2015 May. 16 | 54.7   | 41            | 21–558             | 40–100        | 112.480  | 100.406  | 23.0            | J1058+015 | J1058+0133 | J1011-0423 |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
| B6   | 2014 Dec. 8  | 28.6   | 35            | 15–349             | 65–115        | 229.970  | 215.805  | 17.5$\times$3   | Ganymede  | J1037-2934 | J1011-0423 |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+
| B6   | 2014 Dec. 10 | 27.3   | 38            | 15–349             | 65–135        | 242.443  | 227.702  | 14.7$\times$3   | Callisto  | J1037-2934 | J1011-0423 |   |   |
+------+--------------+--------+---------------+--------------------+---------------+----------+----------+-----------------+-----------+------------+------------+---+---+

: Log of ALMA Observations

Table notes: Column 3-5: FoV, $N_{\rm ant}$, and $L_{\rm baseline}$ are the FWHM of the ALMA primary beam, number of 12 m antennas, and projected baseline length of the assigned configuration, respectively. Column 7-8: Central frequency of the two continuous spws in upper and lower sidebands (USB and LSB). Column 9: Total integration time on NGC 3110. The Band 6 observations have three pointing fields due to the small FoV. Column 10-12: Assigned calibrators.

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | $\nu_{\rm obs}$ | $E_{\rm u}$/k | $uv$-weight | Beam Size (P.A.) | $V_{\rm ch}$ | $\sigma_{\rm ch}$ | $S_{\rm line}\Delta v$ |  |  |  |  |  |
|  | (GHz) | \(K\) |  | ($''$ ($^\circ$)) | (km s$^{-1}$) | (mJy beam$^{-1}$) | (Jy km s$^{-1}$) |  |  |  |  |  |
| $^{12}$CO ($J$ = 1–0) | 113.360 | 5.5 | natural | 1.81 $\times$ 1.43 ($-$82) | 20 | 1.2 | 303.34 $\pm$ 1.91 |  |  |  |  |  |
| $^{12}$CO ($J$ = 2–1) | 226.716 | 16.6 | natural | 1.68 $\times$ 0.93 (+74) | 20 | 1.2 | 854.84 $\pm$ 1.83 |  |  |  |  |  |
| $^{13}$CO ($J$ = 1–0) | 108.374 | 5.3 | natural | 1.16 $\times$ 1.14 ($-$32) | 20 | 1.1 | 10.08 $\pm$ 0.69 |  |  |  |  |  |
| $^{13}$CO ($J$ = 2–1) | 216.744 | 15.9 | natural | 1.59 $\times$ 0.93 (+80) | 20 | 0.7 | 38.01 $\pm$ 0.57 |  |  |  |  |  |
| C$^{18}$O ($J$ = 2–1) | 215.920 | 15.8 | natural | 1.59 $\times$ 0.93 (+80) | 40 | 0.4 | 7.59 $\pm$ 0.25 |  |  |  |  |  |

: Line and Imaging Properties

Table notes: Column 6: Velocity resolution of the data cube. Column 7: Noise rms per channel per pixel in the data which have velocity resolution of $\Delta v$. Column 8: Total integrated intensity. All the measurements are done after convolving the synthesized beam to 2.0$''$. We only consider the statistical error here.

# Scatter plots with varying $\alpha_{\rm CO}$

We show the scatter plots including the KS relation, SFE vs. spectral index, and SFE vs SSC density in Figure [8](#fig_sfe). The molecular gas masses are derived assuming a constant $\alpha_{\rm CO}$ of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (see Section [4.2.3](#alpha)). In order to discuss how these plots change when we apply the spatially varying $\alpha_{\rm CO}$, we reconstruct these with $\alpha_{\rm LTE}$($T_{\rm rot}$) in Figure [9](#fig_appendix). The number of data points decrease compared to Figure [8](#fig_sfe), as the $\alpha_{\rm LTE}$($T_{\rm rot}$) estimate is limited for $^{13}$CO($2\text{--}1$)-detected apertures. However, we confirm that the varying $\alpha_{\rm CO}$ does not strongly affect the trends of the region “A" discussed in the main text. Thus, both the constant and varying $\alpha_{\rm CO}$ measurements lead to the same conclusions of this paper.

![](fig_appendix1.png)

[^1]: <https://archive.nrao.edu/archive>

[^2]: http://www.cv.nrao.edu/php/splat/

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Estimate H2 gas masses via two independent methods: (1) LTE calculation from optically-thin 13CO transitions assuming fixed T_rot = 15 K, and (2) Rayleigh-Jeans 1.3 mm dust continuum emission following Scoville et al. (2016). Compare both with L'_CO(1-0) to determine alpha_CO.",
  "failed_quote": "Thus we substituted $T_{\\rm rot}$ $=$ 15 K for the equation [eqn_rot] in order to estimate $N_{\\rm ^{13}CO}$ for all apertures with $^{13}$CO($2\\text{--}1$) detection."
 }
]
```
