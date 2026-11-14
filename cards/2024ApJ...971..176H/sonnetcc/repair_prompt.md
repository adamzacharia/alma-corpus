# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...971..176H\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Unraveling the Mystery of the Low CO-to-H$_2$ Conversion Factor in Starburst Galaxies: RADEX Modeling of the Antennae

## Abstract

CO emission has been widely used as a tracer of molecular gas mass. However, it is a long-standing issue to accurately constrain the CO-to-H$_2$ conversion factor ($\alpha_{\mathrm{CO}}$) that converts CO luminosity to molecular gas mass, especially in starburst galaxies. We present the first resolved $\alpha_{\mathrm{CO}}$ modeling results with multiple ALMA CO and $^{13}$CO transition observations at both giant molecular cloud (GMC) scale at 150 pc and kpc scale for one of the closest starburst mergers, the Antennae. By combining our CO modeling results and measurements of 350 GHz dust continuum, we find that most GMCs in the Antennae have $\alpha_{\mathrm{CO}}$ values $\sim$4 times smaller than the commonly adopted Milky Way value (4.3). We find $\alpha_{\mathrm{CO}}$ at GMC scales shows a strong dependence on CO intensity, $^{13}$CO/CO ratio and GMC velocity dispersion, which is consistent with various theoretical and simulation predictions. Specifically, we suggest that the $^{13}$CO/CO line ratio and the velocity dispersion can be used to infer $\alpha_{\mathrm{CO}}$ in starburst regions. By applying our modeled $\alpha_{\mathrm{CO}}$ in GMC analyses, we find that GMCs in the Antennae are less gravitationally bound than in normal spiral galaxies, which is more consistent with what is predicted by merger simulations. At kpc scale, we find that our modeled $\alpha_{\mathrm{CO}}$ values are smaller than the modeled $\alpha_{\mathrm{CO}}$ at GMC scale by 40%, which can be due to inclusion of a diffuse gas component with lower $\alpha_{\mathrm{CO}}$ values. We find a similar correlation of $\alpha_{\mathrm{CO}}$ and CO intensity at kpc scales to that at GMC scales.

# Introduction

The cold and dense molecular gas in the interstellar medium (ISM) is the direct fuel for current and future star formation. Measuring the amount and properties of the molecular gas is crucial for understanding star formation, the ISM, and their relations with galaxy evolution. Although H$_2$ is the dominant component of molecular gas, it is not normally observable due to the high excitation temperature ($T_{\mathrm{ex}}$) of its lines. Instead, the $^{12}$C${^{16}}$O $J$=1-0 line (hereafter CO $J$=1-0) is the most commonly used tracer for measuring the molecular gas mass. The CO-to-H2 conversion factor, $\alpha_{\mathrm{CO}}$ is commonly defined for the $J$ = 1-0 line as the ratio of total molecular gas to ($M_{\text{mol}}$ in M$_{\odot}$) to the CO $J$=1-0 luminosity ($L_{\mathrm{CO(1-0)}}$ in K km s$^{-1}$ pc$^2$), or equivalently, the ratio of molecular gas surface density ($\Sigma_{\mathrm{mol}}$ in M$_{\odot}$ pc$^{-2}$) to the CO $J$=1-0 intensity ($I_{\mathrm{CO(1-0)}}$ in K km s$^{-1}$): $$\begin{equation}
\alpha_{\mathrm{CO}} = \frac{M_{\text{mol}}}{L_{\mathrm{CO(1-0)}}} = \frac{\Sigma_{\text{mol}}}{I_{\mathrm{CO(1-0)}}} \left[\frac{\mathrm{M_{\odot}}}{\mathrm{K\ km\ s^{-1}\ pc^2}}\right]
\end{equation}$$ Given that CO is straightforward to observe, a concrete prescription for $\alpha_{\mathrm{CO}}$ as a function of local ISM properties has been a longstanding goal.

$\alpha_{\mathrm{CO}}$ was first calibrated for individual giant molecular clouds (GMCs) in our Milky Way based on virial methods (cite: solomon1987; scoville1987; scoville1989; maloney1990; young1991), optically thin tracers such as dust continuum (cite: boulanger1996; dame2001; planckcollaboration2011), CO isotopologue lines (cite: goldsmith2008) and gamma-ray observations (cite: strong1996; grenier2005; abdo2010). These studies have found a nearly constant $\alpha_{\mathrm{CO}}$ around 4.3 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ (cite: bolatto_co–h_2013) with scatter of 0.3 dex. However, $\alpha_{\mathrm{CO}}$ in the Central Molecular Zone (CMZ) can be 3 – 10 times lower than the average value (cite: bolatto_co–h_2013). Furthermore, extra-galactic observations have found systematic variations of up to one or two orders of magnitude across different galactic environments (cite: bolatto2008; donovanmeyer2012; rebolledo2012; sandstrom_co–h2_2013). This issue is further complicated by the fact that different calibration methods can lead to vastly discrepant estimates (cite: bolatto2003; leroy2011). Therefore, assuming a constant $\alpha_{\mathrm{CO}}$ can introduce systematic bias in calculating molecular gas mass, surface density and related quantities, such as molecular gas depletion time, the cloud free-fall time, the virial parameter and the turbulent pressure (cite: sun_molecular_2022; sun2023).

Theoretical models and simulations suggest that $\alpha_{\mathrm{CO}}$ can depend on both small-scale GMC properties, such as temperature, volume and surface density (cite: gong2020; hu2022), and kpc-scale environmental properties, such as metallicity, galactic disk surface density (cite: wolfire2010; narayanan2012; kazandjian2015; renaud_diversity_2019; hu2022). Recently, a lot of progress has been made in calibrating the metallicity dependence (cite: schruba2012; amorín2016; accurso2017), which has been applied to several studies of CO emission in nearby galaxies (cite: sun_molecular_2020; sun\_\_dynamical_2020; pessa2021; sun2023). However, we still lack a general prescription that incorporates all the related physical quantities at different scales.

In particular, $\alpha_{\mathrm{CO}}$ is poorly constrained in starburst systems, such as ultra/ luminous infrared galaxies (U/LIRGs). Early studies (cite: downes1993; bryant1996; bryant1999; solomon1997; downes_rotating_1998) find that $\alpha_{\mathrm{CO}}$ in U/LIRGs should be $\sim$ 4 times lower than the Milky Way value to give reasonable molecular gas mass values closer to dynamical mass estimates. Studies on a large sample of U/LIRGs using multi-CO line large velocity gradient (LVG) radiative transfer modeling (cite: solomon2005; downes_rotating_1998; papadopoulos_molecular_2012) find consistent average values around 1.1 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ (cite: downes_rotating_1998). Therefore, a discrete bimodal $\alpha_{\mathrm{CO}}$ prescription or a modified version accounting for the deviation from the star-forming main sequence (cite: magnelli2012; sargent_regularity_2014) is generally applied in observed normal spiral and starburst galaxies. However, there is likely a large galaxy-to-galaxy $\alpha_{\mathrm{CO}}$ variation for different U/LIRGs (cite: papadopoulos_molecular_2012; sliwa_extreme_2017; carleton2017a), which is not captured by those $\alpha_{\mathrm{CO}}$ prescriptions. This problem is further complicated by recent works using optically thin tracers (cite: dunne_dust_2022), which suggest a Milky-Way like $\alpha_{\mathrm{CO}}$ value for these U/LIRGs.

Besides galaxy-to-galaxy variation, theoretical works (cite: narayanan2012; bolatto_co–h_2013) also suggest that $\alpha_{\mathrm{CO}}$ could vary within galaxies depending on the local environment. (cite: narayanan_co-h2conversion_2011) suggest that the low $\alpha_{\mathrm{CO}}$ is caused by the increase in GMC temperature (cite: magnelli2012; olsen2016) and/or velocity dispersion (cite: papadopoulos_molecular_2012), which makes CO emission over-luminous. Recent galaxy merger observations (cite: papadopoulos_molecular_2012) and simulations (cite: bournaud2015) seem to favor the increase in velocity dispersion to play the major role. However, (cite: renaud_three_2019) show in their simulation that $\alpha_{\mathrm{CO}}$ is not a sole function of velocity dispersion and is also dependent on different merging stages.

In order to diagnose GMCs physical states and reasons for $\alpha_{\mathrm{CO}}$ variation, it is necessary to observe multiple CO and other molecular lines (specifically optically thin lines) at GMC resolution ($\sim$ 100 pc) to perform comprehensive LVG modeling. This approach has recently been implemented across several nearby galaxy centers (cite: teng2022; teng2023). However, due to the limited sensitivity and resolution of current instruments, most LVG studies on individual starburst mergers (cite: papadopoulos_molecular_2012; sliwa2012; sliwa2013; sliwa_around_2014; he2020) can only probe a limited number of gas-rich regions at kpc resolution, making it hard to extract any $\alpha_{\mathrm{CO}}$ dependence on GMC properties and local environments.

As one of the closest starburst mergers, NGC 4038/9 (the Antennae) is an ideal target for this study. At a distance of 22 Mpc (cite: schweizer2008), ALMA can readily resolve molecular gas at GMC scales. The total SFR of the Antennae is between 11 $\mathrm{M_{\odot} yr^{-1}}$(cite: bemis2019) and 20 $\mathrm{M_{\odot} yr^{-1}}$(cite: Chandar2017). The higher SFR value traced by H$\alpha$ is comparable to those of LIRGs, which suggests a starburst event that was just triggered recently several tens of Myr ago. As a typical major merger between two gas-rich galaxies, the Antennae has been well-studied in both simulations and observations. Most simulations (cite: karl2010; privon_dynamical_2013; renaud_diversity_2019) suggest that the Antennae has just passed its second pericentric passage $\sim$ 40 Myr ago. Its central region hosts the two progenitor nuclei, still separated by about 7 kpc (cite: zhang_antennae_2001). As a starburst merger, it also hosts a large number ($\sim$ 10$^4$) of young massive star clusters exceeding 10$^4$ M$_{\odot}$, with maximal mass reaching 10$^6$ M$_{\odot}$(cite: whitmore2014a; mok_mass_2020; he2022). The extreme number of YMCs will likely provide enough stellar feedback (cite: keller_superbubble_2014) to ultimately disperse the molecular gas and significantly reduce the $\alpha_{\mathrm{CO}}$ values (cite: renaud_diversity_2019).

In this paper, we perform LVG modeling on high-resolution ($\sim$ 150 pc) CO and $^{13}$CO molecular lines from ALMA observations of the Antennae to constrain the physical properties of the molecular gas and $\alpha_{\mathrm{CO}}$ at both GMC and kpc scales. In Section 2, we describe the observations and how we processed the data. In Section 3, we describe the RADEX modeling method that we used to derive gas physical quantities (e.g. temperature, volume density and CO column density) and $\alpha_{\mathrm{CO}}$. In Section 4, we present our modeled gas physical properties (e.g. kinetic temperature, volume density and CO column density) and their connection with different line ratios. In Section 5, we present our modeled $\alpha_{\mathrm{CO}}$ at GMC scale and compare its dependence on various GMC observational and physical quantities with theoretical, simulation and observational predictions. In Section 6, we apply our modeled $\alpha_{\mathrm{CO}}$ in calculation of GMC surface density and virial equilibrium states. In Section 7, we present modeled $\alpha_{\mathrm{CO}}$ at kpc scales and its comparison with $\alpha_{\mathrm{CO}}$ at GMC scales. We also explore the $\alpha_{\mathrm{CO}}$ dependence on kpc-scale gas properties (e.g. gas surface density, velocity dispersion and metallicity). The conclusions are summarized in Section 8.

# Observations and Data Processing

## ALMA Spectral Lines

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Data | Project | ALMA | Native | LAS | Velocity | RMS$_{\mathrm{native}}$ | RMS$_{\mathrm{150 pc}}$ |
| Type | ID | Band | Resolution |  | Resolution |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
| CO $J$=1-0 | 2018.1.00272.S | 3 | $0.84\ensuremath{''}$, 90 pc | $14.5\ensuremath{'}$, 93 kpc | 2.54 km s$^{-1}$ | 0.09 K | 0.05 K |
| CO $J$=2-1 | 2018.1.00272.S | 6 | $0.51\ensuremath{''}$, 54 pc | $6.9\ensuremath{'}$, 44 kpc | 2.54 km s$^{-1}$ | 0.24 K | 0.11 K |
| CO $J$=3-2 | 2021.1.00439.S | 7 | $0.67\ensuremath{''}$, 71 pc | $4.5\ensuremath{'}$, 29 kpc | 3.4 km s$^{-1}$ | 0.09 K | 0.04 K |
| $^{13}$CO $J$=1-0 | 2021.1.00439.S | 3 | $1.41\ensuremath{''}$, 150 pc | $15\ensuremath{'}$, 96 kpc | 2.7 km s$^{-1}$ | 0.04 K | 0.04 K |
| $^{13}$CO $J$=2-1 | 2018.1.00272.S | 6 | $0.71\ensuremath{''}$, 76 pc | $6.9\ensuremath{'}$, 44 kpc | 5.3 km s$^{-1}$ | 0.09 K | 0.05 K |
| continuum | 2021.1.00439.S | 7 | $0.65\ensuremath{''}$, 72 pc | $0.34\ensuremath{'}$, 2.2 kpc | – | 0.18 mJy/beam | 0.4 mJy/beam |

Columns: (1) CO spectral lines. (2) ALMA project ID. (3) ALMA observed frequency band. (4) Native resolution for the smallest round beam. (5) Largest angular scale. (6) Velocity resolution. (7) Noise of the image cubes at the native resolution. (8) Noise of the image cubes after smoothing to the resolution of 150 pc.

We use multiple CO lines (CO $J$=1-0, 2-1, 3-2 and $^{13}$CO $J$=1-0, 2-1) from the Atacama Large Millimeter/Submillimeter Array (ALMA) to determine the physical properties of the gas in the Antennae at 150 pc scale. We obtained ALMA Band 3, 6 and 7 observations from cycle 5 project 2018.1.00272.S and cycle 8 project 2021.00439.S to capture multiple CO and $^{13}$CO lines. A summary of the datasets is in Table [\[tab:line_table\]](#tab:line_table). For all five lines, we have observations from the 12 m-array used in both a compact and extended configuration, 7 m-array (ACA) and total power (TP) array to recover emission from $\sim$ 100 pc scale up to $\sim$ 50 kpc scale. The continuum does not have TP observations. Besides the lines listed in Table [\[tab:line_table\]](#tab:line_table), we also have C$^{18}$O $J$=1-0 and 2-1 detected in the same spectral tuning as $^{13}$CO $J$=1-0 and 2-1, respectively.

We calibrate the raw visibility data with the observatory-supplied calibration scripts and the appropriate version of the CASA pipeline. From the calibrated measurement sets, we extract and image a relevant subset of visibility data for each molecular line using a modified version of the PHANGS–ALMA imaging pipeline (cite: leroy2021). Before imaging the lines, we performed continuum subtraction by subtracting the 1st-order fit modeling on line-free channels. We then combine the 12m and 7m measurement sets together and perform the imaging. The imaging steps generally follow the PHANGS imaging scheme (cite: leroy2021).

For the weighting of the visibility data, we adopt the *Briggs* method with robustness parameter of 0.5. After the cleaning, we then feather the cleaned image product with TP data and apply the primary beam correction to get final image cubes for each line. We also smooth all the images to the smallest round beam. In the final step, we convert all the image cubes to units of Kelvin (K).

We then perform post-processing steps to homogenize all 5 CO lines. We smooth all five image cubes to the resolution of 150 pc (1.41 arcsec) and match all their spatial grids to the CO $J$=1-0 line. We then produced a set of moment maps and effective width ($\sigma_v$) maps for all five lines at this common resolution. Specifically, the effective width is measured as the ratio between integrated intensity (moment 0) and peak brightness temperature (moment 8) maps, which is $$\begin{equation}
\sigma_v = \frac{I}{\sqrt{2\pi}T_{\mathrm{peak}}}
\end{equation}$$ For a perfect Gaussian line profile, the effective width is identical to the traditionally used moment 2 measurements. We adopt this alternative method because it gives a more stable estimate of velocity dispersion within clouds, specifically if two or more clouds are along the same line of sight (cite: heyer2001; sun_cloud-scale_2018). To make moment maps, we start with generating masks adopting the scheme of the PHANGS-ALMA pipeline, which starts from a high-confidence mask including at least two consecutive channels with S/N above 5 and then expand the mask to include pixels with S/N above 2 for at least two consecutive channels. We run this scheme for each line and combine all the mask together to create a "combo" mask. We then apply this common "combo" mask to all the five line data cubes to make moment maps and their corresponding error maps. We also apply a S/N cut of 3 to the moment 0 maps of each line to exclude noisy pixels in weak line maps. In the final steps, we Nyquist-sample the moment 0 and effective width maps for all the lines to remove the spatial correlation between different pixels. Some representative moment maps are shown in Fig. [1](#fig:co10_moments) and [2](#fig:co_mom0).

In Section 7, we will also use the five CO and $^{13}$CO maps at a resolution of 1 kpc. We perform the same steps as described above to obtain the cubes and moment maps at this resolution.

## ALMA continuum

We also make the ALMA Band 7 continuum image in order to calculate the dust and gas mass. After the calibration of the Band 7 data, we use the PHANGS-ALMA pipeline (cite: leroy2021) to combine the 12m and 7m measurement sets and extract the line-free channels from the combined measurement set for the continuum imaging. We also collapse each spectral window into a single channel in order to speed up the continuum imaging process. We then use the `auto-multithresh` algorithm to clean the continuum data down to threshold of 2 $\times$ RMS (RMS of $\sim$ 0.18 mJy/beam). After imaging, we smooth the dust continuum map to the resolution of 150 pc and regrid the map to the nyquist-sampled CO images.

## Spitzer Data

We use the *Spitzer* 3.6 $\mu$m (Program 10136) and 4.5 $\mu$m (Program 61068) data to calculate the stellar mass surface density of the Antennae at kpc scale. We estimate the background level of each image by calculating the mean of an aperture drawn outside the galaxy and perform background subtraction. We reproject both images to match the pixel grids of the CO 150 pc resolution moment maps. We then calculate the stellar mass for each pixel with the equation (cite: eskew2012) $$\begin{equation}
M_{\star} = 10^{5.65} F_{3.6}^{2.85} F_{4.5}^{-1.85} (D/0.05)^2 \, [\mathrm{M_{\odot}}], 
\end{equation}$$ where $F_{3.6}$ and $F_{4.5}$ are the flux at 3.6 and 4.5 $\mu$m in Jy, respectively and $D$ is the luminosity distance in Mpc. We then calculate the stellar surface density by dividing by the pixel area using equation $$\begin{equation}
\Sigma_{\star} = M_{\star} / (150\ \text{pc})^2 \, [\mathrm{M_{\odot}\ pc^{-2}}]
\end{equation}$$ At the final step, we regrid our calculated stellar surface density map to the grid of 1 kpc resolution nyquist sampled CO $J$=1-0 moment 0 map.

# RADEX Modeling

## General Modeling Procedure

We adapt the code[^1] from (cite: teng2022) to perform non-LTE radiative transfer modeling for each pixel with all five CO and $^{13}$CO lines detected at 150 pc. We briefly summarize the code and our adaptation below (cite: teng2022; teng2023). This code runs RADEX (cite: van_der_tak_computer_2007) modeling, which assumes a homogeneous medium and uses radiative transfer equations based on the escape probability formalism to find a converged solution for the excitation temperature and level population for each molecular line transition. We adopt the one-component RADEX modeling to generate 5D grids of integrated line intensities for the five lines under combinations of varying H$_2$ volume density ($n$), kinetic temperature ($T_{\mathrm{kin}}$), CO column density ($N_{\mathrm{CO}}$), CO/$^{13}$CO abundance ratio ($X_{12/13}$) and beam filling factor ($\Phi_{\mathrm{bf}}$). Since RADEX modeling uses $N_{\mathrm{CO}}/\Delta v$ instead of $N_{\mathrm{CO}}$ alone, we instead sample CO column density per 15 km s$^{-1}$($N_{\mathrm{CO}} \times \frac{15 \mathrm{km s^{-1}}}{\Delta v}$). The 15 km s$^{-1}$ is the fiducial value used in (cite: teng2022; teng2023). Later we will rescale this value to the real CO column density based on the measured $\Delta v$ in the CO $J$=1-0 velocity dispersion map ($\Delta v = 2.35 \sigma_v$). In the modeling, we assume the same $\Phi_{\mathrm{bf}}$ for all 5 lines. We also assume the $[\mathrm{CO}]$/$[\mathrm{H}_2]$ abundance ratio ($x_{\mathrm{co}}$) of 3$\times 10^{-4}$. We will discuss our $x_{\mathrm{CO}}$ choice in Section [6.1](#subsec:dust_xco). Our input parameters are summarized in Table 2.

| Parameter | Range | Step |
|:--:|:--:|:--:|
| log ($n$) ($\mathrm{cm^{-3}}$) | 2 – 5.1 | 0.2 |
| log ($T_{\mathrm{kin}}$) (K) | 1 – 2.4 | 0.1 |
| log ($N_{\mathrm{CO}} \times \frac{15 \mathrm{km s^{-1}}}{\Delta v}$) (cm$^{-2}$) | 16 – 21 | 0.2 |
| $X_{12/13}$ | 10 – 400 | 10 |
| $\Phi_{\mathrm{bf}}$ | 0.05 – 1 | 0.05 |
| $[\mathrm{CO}]$/$[\mathrm{H}_2]$ | $3 \times 10^{-4}$ | – |

: RADEX Input Parameters

We then follow the Bayesian likelihood analyses in (cite: teng2022) to characterize the probability density function (PDF) for the five varying parameters (see detailed description in Appendix [9](#app:RADEX_stats)). From the derived 1D marginalized PDF, we can calculate the maximum likelihood (’1DMax’) and median values for each variable. For all the parameters except for $X_{12/13}$, we use the median as the solution. For $X_{12/13}$, due to the bimodal shape of the 1D PDF, we instead use the 1DMax value as the solution (see detailed discussion in Appendix [9](#app:RADEX_stats)).

## Modeling of the CO-to-H$_2$ conversion factor

The CO-to-H$_2$ conversion factor $\alpha_{\mathrm{CO}}$ is calculated (cite: teng2022) as $$\begin{equation}
\label{eq:alphaCO_def}
\begin{split}
\alpha_{\mathrm{CO}} &= \frac{\Sigma_{\text{mol}}}{I_{\mathrm{CO(1-0)}}} \left[\frac{\mathrm{M_{\odot}}}{\mathrm{K\ km\ s^{-1}}}\right] \\
&= \frac{1.36 m_{\mathrm{H_2}} N_{\mathrm{CO}} \Phi_{\mathrm{bf}}}{x_{\mathrm{co}} I_{\mathrm{CO(1-0)}}} \\
&= \frac{1}{4.5 \times 10^{19}} \frac{N_{\mathrm{CO}}[\mathrm{cm}^{-2}]\Phi_{\mathrm{bf}}}{x_{\mathrm{co}} I_{\mathrm{CO(1-0)}} [\mathrm{K\ km\ s^{-1}]}},    
\end{split}
\end{equation}$$ where $x_{\mathrm{co}}$ is the $[\mathrm{CO}]$/$[\mathrm{H}_2]$ abundance ratio. This equation includes the correction coefficient of 1.36 for the contribution of helium. This equation shows that the key modeling parameters to constrain $\alpha_{\mathrm{CO}}$ are the CO column density $N_{\mathrm{CO}}$, beam filling factor $\Phi_{\mathrm{bf}}$ and $[\mathrm{CO}]$/$[\mathrm{H}_2]$ abundance ratio.

We then follow the method in (cite: teng2022) and (cite: teng2023) to derive the posterior probability of $\alpha_{\mathrm{CO}}$ (see detailed description in Appendix [10](#app:alphaCO)). For the rest of the paper, we choose the median value of the posterior as our derived $\alpha_{\mathrm{CO}}$, and 16$^{\mathrm{th}}$ and 84$^{\mathrm{th}}$ percentile as the $\pm 1\sigma$ values. We also inspect the marginalized distribution of the five modeled variables and $\alpha_{\mathrm{CO}}$ and exclude pixels with unreliable modeling results (see detailed description in Appendix [10](#app:alphaCO)). After our selection procedure, we have 508 pixels with good RADEX model constraints.

Note that our derived $\alpha_{\mathrm{CO}}$ is dependent on our assumed $x_{\mathrm{CO}}$ value. The value we assume (3$\times 10^{-4}$) is commonly adopted for starburst systems (cite: sliwa2017). In Section [6.1](#subsec:dust_xco), we further justify our $x_{\mathrm{CO}}$ choice by comparing the CO $J$=1-0 emission with the dust continuum. For comparison with studies with a different $x_{\mathrm{CO}}$ assumption, we give the equation to scale our $\alpha_{\mathrm{CO}}$ value based on different $x_{\mathrm{CO}}$ choices, which is $$\begin{equation}
\alpha_{\mathrm{CO}}^{\mathrm{scaled}} = \frac{3 \times 10^{-4}}{x_{\mathrm{CO}}} \alpha_{\mathrm{CO}}^{\mathrm{derived}}
\end{equation}$$

# Gas Physical Properties at GMC scales

## Line Ratios

The CO $J$=3-2/1-0 and CO $J$=2-1/1-0 ratios are indicators of the CO excitation, which is directly related to the molecular gas temperature and/or volume density (cite: leroy2017). Fig. [4](#fig:co_ratio) shows the two ratio maps along with their dependencies on CO $J$=1-0 brightness temperature. We can see that the CO $J$=2-1/1-0 ratio is generally uniform with values close to 1 across the entire molecular gas detected regions. This ratio value is consistent with what is measured in starburst U/LIRGs (cite: montoyaarroyave2023). This uniformity requires both lines to be thermally excited in regions that are warm and optically thick, which is expected to be typical of environments in starburst systems (cite: sliwa2017). Simulations also predict that the low-J CO lines are mostly thermalized for typical starburst mergers (cite: bournaud2015). Since most GMC observations for starburst mergers (cite: brunetti_highly_2020; brunetti_extreme_2022) are done using the CO $J$=2-1 line due to its higher resolution and sensitivity, our study suggests that a typical starburst merger should have CO $J$=2-1/1-0 ratio values close to 1 instead of the commonly adopted 0.7 as seen in normal spiral galaxies (cite: leroy2021).

In contrast, the CO $J$=3-2/1-0 ratio increases as the CO $J$=1-0 intensity (or gas surface density) increases (Fig. [4](#fig:co_ratio), lower-right panel). This trend suggests that gas in these gas-concentrated regions is either denser and/or warmer than the rest of the regions. The average CO $J$=3-2/1-0 ratio is $\sim$ 0.4 – 0.7 (Fig. [4](#fig:co_ratio), lower right panel), which is also consistent with typical U/LIRGs (cite: montoyaarroyave2023) and the centers of normal spiral galaxies (cite: li2020; vlahakis2013), but significantly higher than those in normal spiral galaxies (cite: wilson2012; leroy2022). This suggests that gas conditions of the Antennae are similar to those of gas concentrated and starburst environments in galaxy centers and U/LIRGs. [^2]

$^{13}$CO/CO $J$=1-0 and $^{13}$CO/CO $J$=2-1 ratio maps (Fig. [5](#fig:13co_ratio)) can be used to probe the \[$^{13}$CO\]/\[CO\] abundance ratio and the optical depth (cite: jimenez-donaire_optical_2017). Due to CO being optically thick, it is hard to disentangle these factors without comprehensive LVG modeling. To demonstrate this degeneracy, we consider a simple case where both CO and $^{13}$CO lines are thermally excited to the kinetic temperature. Under the local thermal equilibrium (LTE) condition, we would expect the $^{13}$CO/CO line ratio to be $$\begin{equation}
\begin{split}
R_{\mathrm{^{13}CO/CO 1{-}0}} &= \frac{T^{\mathrm{peak}}_{\mathrm{^{13}CO 1{-}0}}}{T^{\mathrm{peak}}_{\mathrm{CO 1{-}0}}}\\
&= \frac{\Phi_{\mathrm{bf}} T_{\mathrm{kin}} \left[1-\exp(-\tau_{\mathrm{^{13}CO 1{-}0}})\right]}{\Phi_{\mathrm{bf}} T_{\mathrm{kin}} \left[1-\exp(-\tau_{\mathrm{CO 1{-}0}})\right]} \\
& \approx \tau_{\mathrm{^{13}CO 1{-}0}}, \ (\tau_{\mathrm{^{13}CO 1{-}0}} \ll 1 \ll \tau_{\mathrm{CO 1-0}} ) \\
&= \tau_{\mathrm{CO 1{-}0}} / X_{12/13}
\end{split}
\label{eq:R10_tau13}
\end{equation}$$ where we assume the $^{13}$CO $J$=1-0 optical depth can be simply expressed as the CO $J$=1-0 optical depth divided by the ${[\mathrm{CO}]/[^{13}\mathrm{CO}]}$ abundance ratio ($X_{12/13}$). Therefore, a higher $R_{\mathrm{^{13}CO/CO 1{-}0}}$ can be either due to higher CO optical depth (and hence higher column density) and/or lower $X_{12/13}$ abundance ratio. [^3]

Both $R_{\mathrm{^{13}CO/CO 1{-}0}}$ and $R_{\mathrm{^{13}CO/CO 2{-}1}}$ have values of $\sim$ 0.1, similar to the typical $R_{\mathrm{^{13}CO/CO 1{-}0}}$ ratio for normal spiral galaxies (cite: cormier_full-disc_2018). On the other hand, this ratio is much higher than the typical ratio of starburst U/LIRGs (cite: brown2019).

Since the Antennae has normal $^{13}$CO/CO line ratios but higher $X_{12/13}$ values ($\sim$ 200, Section [4.2](#subsec:results)) than normal spiral galaxies (cite: jimenez-donaire_optical_2017), it is possible the normal $^{13}$CO/CO ratio is due to the combined effect of high optical depth and high $X_{12/13}$ values in the Antennae. We note that the Antennae has comparable molecular gas mass but less total SFR than typical U/LIRGs (cite: brunetti_cloud-scale_2022), which might suggest that stellar feedback might not yet be effective to reduce the molecular gas optical depth in the Antennae.

## Modeling results and their connection to the line ratios

We show the maps of our derived physical quantities in Fig. [6](#fig:results_maps). We can see that most quantities show clear spatial variations among different regions. If we use the CO column density map as a guide, we can see that regions with higher gas surface densities, such as the two nuclei and the overlap region, generally have higher kinetic temperatures, beam filling factors and $[\mathrm{CO}]/[^{13}\mathrm{CO}]$ abundance ratios. On the other hand, the volume density distributions are more uniform throughout the entire galaxy[^4].

The kinetic temperature map looks similar to the CO $J$=3-2/1-0 ratio map. As previously discussed, the higher CO $J$=3-2/1-0 ratio could either be caused by higher temperature or density. Since the volume density does not have as much spatial variation as the kinetic temperature, it seems the major driver for the CO $J$=3-2/1-0 ratio variation is temperature.

The CO $J$=2-1/1-0 ratio map looks uniformly close to 1, which suggests both lines are thermalized, with the excitation temperature equal to the kinetic temperature. Fig. [7](#fig:LTE_test) shows that the excitation temperatures of the CO $J$=2-1 and 1-0 lines are a good match to the kinetic temperature, which further confirms they are thermalized. Simulations (cite: hu2022) suggest that for the CO $J$=1-0 and 2-1 lines, the LTE conditions are generally satisfied when kinetic temperature is above 10 K and volume density above 10$^3$ $\mathrm{cm^{-3}}$. As we can see from the temperature and volume density maps (Fig. [6](#fig:results_maps)), most regions satisfy this condition.

On the other hand, most $^{13}$CO $J$=1-0 emission is not thermally excited, with excitation temperature lower than the kinetic temperature. However, we expect that most regions should have volume density above the $^{13}$CO $J$=1-0 critical density (cite: jimenez-donaire_optical_2017) and will be thermally excited like CO $J$=1-0. However, our models assume $^{13}$CO $J$=1-0 has the same beam filling factor as the CO $J$=1-0 emission. In reality, $^{13}$CO $J$=1-0 might have smaller beam filling factor as it mostly comes from denser regions. In this case, we might overestimate the size and underestimate the actual excitation temperature of the $^{13}$CO $J$=1-0 emission.

As discussed in Section [4.1](#subsec:ratio), under LTE conditions, we would expect the $^{13}$CO/CO $J$=1-0 ratio to be equivalent to the $^{13}$CO $J$=1-0 optical depth. As shown in the lower-left panel of Fig. [7](#fig:LTE_test), when LTE conditions hold for $^{13}$CO $J$=1-0 ($T_{\mathrm{ex}}(\mathrm{^{13}CO 1-0}) \approx T_{\mathrm{ex}}(\mathrm{CO 1-0})$), we see a 1-to-1 correspondence between the ratio and the optical depth. However, most regions have subthermally excited $^{13}$CO $J$=1-0 emission according to our modeling, and the ratio in those regions is generally smaller than the actual $^{13}$CO $J$=1-0 optical depth. As discussed in Section [4.1](#subsec:ratio), the two major drivers for $^{13}$CO/CO $J$=1-0 ratio variation are the CO $J$=1-0 optical depth and $X_{12/13}$ abundance ratio. Since $^{13}$CO $J$=1-0 might not satisfy LTE conditions, we test if the $^{13}$CO/CO $J$=1-0 ratio is still affected by those two factors using our RADEX modeling results. As shown in bottom middle and left panel of Fig. [7](#fig:LTE_test), our RADEX modeling results suggest that $R_{\mathrm{^{13}CO/CO 1-0}}$ still has strong correlations with both quantities.

Fig. [6](#fig:results_maps) shows a clear spatial variation of $X_{12/13}$ that corresponds well with $T_{\mathrm{kin}}$ and $N_{\mathrm{CO}}$ variation. Regions with higher CO column density and kinetic temperature generally have higher $X_{12/13}$. In theory, the high $X_{12/13}$ value could be caused by starburst activity that generates large amounts of $^{12}\mathrm{C}$ at short timescales (cite: vigroux1976) by massive stars while $^{13}\mathrm{C}$ will only be released by intermediate-mass stars after $\sim$ 1 Gyr. This scenario is consistent with our expectation since regions with higher gas temperature and surface densities are generally where starburst events happen. In Section [4.1](#subsec:ratio), we also discussed the negative correlation between $R_{\mathrm{^{13}CO/CO 1-0}}$ and CO $J$=1-0 intensity. The low $R_{\mathrm{^{13}CO/CO 1-0}}$ in high surface density regions could be potentially due to high $X_{12/13}$ in these regions. We also find most regions have $X_{12/13}$ values between 100 – 300. This value is more similar to the $X_{12/13}$ in starburst mergers (cite: sliwa_pdbi_2017; sliwa2017) and significantly higher than that in the solar neighborhood and normal disk galaxies ($\sim$ 70) (cite: langer1990; milam2005). These high $X_{12/13}$ values are also consistent with the scenario that starburst events boost the $X_{12/13}$ ratio.

Finally, we note that our modeling results are limited to regions with $^{13}$CO $J$=1-0 and $J$=2-1 detections. The maps in Fig. [6](#fig:results_maps) show that most detections are in the two nuclei and the overlap regions. To expand our modeling to other regions with lower gas surface densities, we need $^{13}$CO observations, specifically $^{13}$CO $J$=2-1 observations, with better sensitivity. Alternatively, we can stack $^{13}$CO pixels based on CO $J$=1-0 brightness temperature to achieve a better S/N level for the CO faint regions.

# The CO-to-H$_2$ conversion factor at GMC scales

## Dependence on CO $J$=1-0 intensity

Various simulations (cite: narayanan2012) have proposed that the bimodal distribution of $\alpha_{\mathrm{CO}}$ across normal spiral galaxies and U/LIRGs can be accounted for by an $\alpha_{\mathrm{CO}}$ that is anti-correlated with CO $J$=1-0 intensity ($I_{\text{CO 1-0}}$) at kpc scales. Recent simulations (cite: gong2020; hu2022) have further pushed this dependence down to GMC spatial scales. Our study provides the first direct test of this dependence in starburst mergers. Fig. [8](#fig:alphaCO_Ico) shows a significant anti-correlation between $\alpha_{\mathrm{CO}}$ and $I_{\text{CO 1-0}}$. Our fit power-law relation is $$\begin{equation}
\log \alpha_{\mathrm{CO}} = 0.77 (\pm 0.04) - 0.3 (\pm 0.02) \log I_{\mathrm{CO 1-0}}
\end{equation}$$ The value in the brackets indicates the 1-$\sigma$ error for the fitted parameter. We can see that our power-law fit has almost the same slope as that predicted (slope of -0.32) in (cite: narayanan2012). On the other hand, the predictions from (cite: gong2020) and (cite: hu2022) give shallower slopes and tend to over-estimate $\alpha_{\mathrm{CO}}$ values. However, since the simulations of both (cite: gong2020) and (cite: hu2022) have a maximum $I_{\text{CO 1-0}}$ barely reaching 100 K km s$^{-1}$, their predictions are more applicable to the environment in normal spiral galaxies with much lower gas surface densities.

The simulation run in (cite: narayanan2012) is focused on the molecular gas in starburst mergers with similar environments as the Antennae. Despite similar slopes, the predicted $\alpha_{\mathrm{CO}}$ values based on the relation in (cite: narayanan2012) are higher than our $\alpha_{\mathrm{CO}}$ measurement by a factor of 1.7. It is possible that this difference is caused by different $x_{\mathrm{CO}}$ values adopted in (cite: narayanan2012). In their simulation, only part of the carbon is converted into CO molecules and the fraction depends on UV field strength, metallicity and optical extinction. In contrast, our models assume all the carbon is converted to CO, which gives a higher $x_{\mathrm{CO}}$ value, and hence lower $\alpha_{\mathrm{CO}}$ value. We further justify our $x_{\mathrm{CO}}$ choice in Section [6.1](#subsec:dust_xco). To test which $x_{\mathrm{CO}}$ prescription is true, we need to test the relation in (cite: narayanan2012) in a larger sample of U/LIRGs at cloud-scale resolution.

## Dependence on CO 1-0 optical depth and $^{13}$CO/CO ratio

Recent GMC LVG modeling in normal spiral galaxies (cite: teng2022; teng2023) suggests that $\alpha_{\mathrm{CO}}$ has a tight proportional correlation with the CO $J$=1-0 optical depth ($\tau_{\mathrm{CO 1-0}}$) when $\tau_{\mathrm{CO(1-0)}} > 1$. This relation is consistent with our LVG modeling expectation, for which $$\begin{equation}
\label{eq:optical_depth}
\tau_{\mathrm{CO 1-0}} \propto N_{\mathrm{CO}}/\Delta v   
\end{equation}$$ As shown in Section [4.1](#subsec:ratio), most CO $J$=1-0 emission is thermally excited, giving $$\begin{equation}
T_{\mathrm{peak}}  \approx \Phi_{\mathrm{bf}} T_{\mathrm{kin}} \left[1-\exp(-\tau_{\mathrm{CO 1-0}})\right]
\end{equation}$$ Substituting these two equations into Eq. [\[eq:alphaCO_def\]](#eq:alphaCO_def), we obtain $$\begin{equation}
\label{eq:alphaCO_tau}
\begin{split}
\alpha_{\mathrm{CO}} &= \frac{N_{\mathrm{CO}} \Phi_{\mathrm{bf}}}{x_{\mathrm{co}} I_{\mathrm{CO(1-0)}}} = \frac{N_{\mathrm{CO}} / \Delta v}{x_{\mathrm{co}} T_{\mathrm{peak}}} \Phi_{\mathrm{bf}}  \\
 & \propto \frac{\tau_{\mathrm{CO 1-0}}}{1-\exp(-\tau_{\mathrm{CO 1-0}})},  \quad (x_{\mathrm{CO}}, T_{\mathrm{kin}} = \mathrm{const})  \\
 & \propto \tau_{\mathrm{CO 1-0}},  \quad (\tau_{\mathrm{CO 1-0}} \gg 1) 
\end{split}
\end{equation}$$ The left panel of Fig. [9](#fig:alphaCO_tau) shows a tight linear correlation between $\alpha_{\mathrm{CO}}$ and $\tau_{\mathrm{CO 1-0}}$, consistent with this theoretical expectation. The red solid line is the proportional fit to the relation, which is $$\begin{equation}
\label{eq:alphaCO_tau}
\log \alpha_{\mathrm{CO}} = \log \tau_{\mathrm{CO 1-0}} - 1.05 (\pm 0.01) 
\end{equation}$$

In real observations, $\tau_{\mathrm{CO 1-0}}$ is hard to measure and generally requires multi-CO transition radiative transfer modeling. Various studies (cite: jimenez-donaire_optical_2017) have proposed to use the $^{13}$CO/CO line ratio ($R_{\mathrm{^{13}CO/CO}}$) to trace the optical depth of the optically thick CO $J$=1-0 line. Based on Eq. [\[eq:R10_tau13\]](#eq:R10_tau13), we would expect $R_{\mathrm{^{13}CO/CO 1{-}0}} \propto \tau_{\mathrm{CO 1-0}}$ if the $X_{12/13}$ abundance ratio is fixed. This scenario is also supported by (cite: teng2023), who found a strong correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{^{13}CO/CO}}$ based on J=2-1 lines across three barred galaxy centers. As shown in the right panel of Fig. [9](#fig:alphaCO_tau), we can see a strong correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{^{13}CO/CO 1{-}0}}$. This strong correlation suggests $R_{\mathrm{^{13}CO/CO 1{-}0}}$ is a good indicator of $\tau_{\mathrm{CO 1-0}}$ and hence can be used to infer $\alpha_{\mathrm{CO}}$. We fit a power-law function between these two quantities and have $$\begin{equation}
 \log \alpha_{\mathrm{CO}} = 0.85 (\pm 0.04) \log R_{\mathrm{^{13}CO/CO 1{-}0}} + 0.97 (\pm 0.04)     
\end{equation}$$ We can see that the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 1{-}0}}$ relation is still relatively close to linear as we expect. However, this relation is steeper than the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ relation obtained in (cite: teng2023). This difference could potentially be due to the choice of different excitation lines (as discussed in Appendix [11](#sec:ratio_sensitivity)). We also note the difference in absolute values between our prescription and that in (cite: teng2023), which could be due to their overestimate of $x_\mathrm{CO}$ (as suggested by (cite: teng2024)) or the different galactic environments we study.

The $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 1{-}0}}$ relation has a significantly larger scatter compared to the $\alpha_{\mathrm{CO}}$ versus $\tau_{\mathrm{CO 1-0}}$ relation. We find that the scatter mainly comes from the varying $X_{12/13}$ value. As shown in the right panel of Fig. [9](#fig:alphaCO_tau), higher $\alpha_{\mathrm{CO}}$ values correspond to higher $X_{12/13}$ values for a fixed $R_{\mathrm{^{13}CO/CO 1{-}0}}$ value. To account for this variation, we also perform a two-variable fitting between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{^{13}CO/CO 1{-}0}}$ and $X_{12/13}$, which is $$\begin{equation}
\label{eq:alphaCO_R13to12}
\begin{split}
\log \alpha_{\mathrm{CO}} &=  1.03 (\pm 0.05) \log R_{\mathrm{^{13}CO/CO 1-0}} \\
&+ 0.21 (\pm 0.03) \log X_{12/13} + 0.7 (\pm 0.06)
\end{split}
\end{equation}$$ We note that $X_{12/13}$ is not a direct observable. For Milky Way studies, $X_{12/13}$ can be measured through line ratios of optically thin lines (cite: langer1990), which are hard to detect in extragalactic observations. Instead, the $X_{12/13}$ value for starburst U/LIRGs is constrained through RADEX modeling (cite: sliwa_pdbi_2017; sliwa2017). These systems show a large variation in the global $X_{12/13}$ value. For these systems with known global $X_{12/13}$ values, Eq. [\[eq:alphaCO_R13to12\]](#eq:alphaCO_R13to12) might be a better choice to infer $\alpha_{\mathrm{CO}}$ and hence GMC surface density.

## Dependence on GMC velocity dispersion

As an optically thick line, CO $J$=1-0 is often established as a molecular gas tracer based on the fact that the CO $J$=1-0 luminosity is proportional to virial mass for individual GMCs in both the Milky Way and nearby galaxies (cite: bolatto_co–h_2013). However, GMCs in starburst systems might have larger velocity dispersion as perturbed by starburst/merging activity and hence be less gravitationally bound. For a given fixed surface density, the increase in velocity dispersion could reduce the optical depth of the gas (Eq. [\[eq:optical_depth\]](#eq:optical_depth)) and hence reduce the $\alpha_{\mathrm{CO}}$ (Eq. [\[eq:alphaCO_tau\]](#eq:alphaCO_tau)). Early theoretical works (cite: downes1993) suggested that for starburst systems, CO instead traces the geometric mean of molecular gas mass and virial mass (cite: shetty2011). (cite: papadopoulos_molecular_2012) infer the dynamical states of GMCs in starburst U/LIRGs based on the LVG modeled volume density and velocity gradient. Their results are also consistent with recent simulation predictions (cite: bournaud2015), who find that the major cause of low $\alpha_{\mathrm{CO}}$ in starburst mergers is due to higher velocity dispersion instead of higher gas temperature in these systems compared to other types of galaxies. Recent high-resolution ALMA observations (cite: teng2023; teng2024) suggest a strong anti-correlation between $\alpha_{\mathrm{CO}}$ and GMC velocity dispersion also exists in the center of spiral galaxies.

In Fig. [10](#fig:alphaCO_vdep), we see a significant anti-correlation between $\alpha_{\mathrm{CO}}$ and $\sigma_v$, consistent with our modeling expectation. We fit the anti-correlation with a power-law function, which is $$\begin{equation}
\log \alpha_{\mathrm{CO}} = 0.7 (\pm 0.04) - 0.46 (\pm 0.03) \log \sigma_{v}
\end{equation}$$ as well as with a power law function with a fixed slope of -0.5. This power-law slope is derived from theoretical predictions under the LVG approximation for two-level optically thick systems (see detailed discussion in (cite: teng2024) and references therein).

Our fit power-law function is quite close to the theoretical prediction, which suggests that the variation in velocity dispersion could be the major driver to the $\alpha_{\mathrm{CO}}$ variation. Furthermore, this result suggests that we can use velocity dispersion to calibrate the $\alpha_{\mathrm{CO}}$ variation at GMC scales.

Fig. [10](#fig:alphaCO_vdep) also shows the $\alpha_{\mathrm{CO}}$ versus $\sigma_v$ fit from (cite: teng2023; teng2024). We can see our data align relatively well with the calibrated relation in (cite: teng2024) using a dust-based approach (cite: sandstrom2013), but are significantly higher than the calibrated relation in (cite: teng2023). (cite: teng2024) suggest that the discrepancy between their calibrated $\alpha_{\mathrm{CO}}$ versus $\sigma_v$ relations from LVG modeling and the dust-based approach might be due to their adoption of a higher $x_{\mathrm{CO}}$ in the LVG modeling. As discussed in Section [6.1](#subsec:dust_xco), our adopted value of $x_{\mathrm{CO}} = 3 \times 10^{-4}$ is reasonable for the Antennae, but might be too large for the centers of the normal spiral galaxies studied by (cite: teng2023).

## Dependence on CO line ratios

(cite: gong2020) proposed recently that the CO $J$=2-1/1-0 ratio $R_{\mathrm{CO 2{-}1/1{-}0}}$ can be used as a tracer of $\alpha_{\mathrm{CO}}$. For individual GMCs in virial equilibrium, we would expect the relation (cite: gong2020) $$\begin{equation}
\alpha_{\mathrm{CO}} \propto 
\begin{cases} 
T_{\mathrm{ex}}(\text{CO 1-0})^{-1/2}, & \mathrm{low\ density} \\ 
\frac{\sqrt{n}}{T_{\mathrm{kin}}}, & \mathrm{high\ density},
\end{cases}
\end{equation}$$ In the low volume density regime, we have an anti-correlation between $\alpha_{\mathrm{CO}}$ and $T_{\mathrm{exc}}$. Since higher $T_{\mathrm{exc}}$ will directly lead to a higher $R_{\mathrm{CO 2{-}1/1{-}0}}$ ratio, we would expect an anti-correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{CO 2{-}1/1{-}0}}$. In Fig. [11](#fig:alphaCO_r21), we see no correlation between these two quantities, which is probably due to our limited range of $R_{\mathrm{CO 2{-}1/1{-}0}}$ values (Fig. [4](#fig:co_ratio)). Furthermore, as discussed in Section [4.1](#subsec:ratio), the $R_{\mathrm{CO 2{-}1/1{-}0}}$ ratio of GMCs in the Antennae is close to 1, which is due to both lines being thermally excited in regions that are warm and optically thick. In this case, we no longer expect an anti-correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{CO 2{-}1/1{-}0}}$.

Since $R_{\mathrm{CO 2{-}1/1{-}0}}$ saturates to $\sim$ 1, it is likely the CO excitation conditions are traced by ratios between higher-$J$ CO lines, such as CO $J$=3-2, and CO $J$=1-0. However, although $R_{\mathrm{CO 3{-}2/1{-}0}}$ shows a significantly larger range of values than $R_{\mathrm{CO 2{-}1/1{-}0}}$, there is only a very weak anti-correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{CO 3{-}2/1{-}0}}$.

The weak correlation between $\alpha_{\mathrm{CO}}$ and CO line ratios suggest that excitation conditions does not play a major role in the $\alpha_{\mathrm{CO}}$ variation within starburst mergers. This is consistent with the observational studies in (cite: teng2023) for the centers of spiral galaxies, where they find temperature only has a minor ($\sim$ 20%) contribution to $\alpha_{\mathrm{CO}}$ variations. Simulations, such as (cite: bournaud2015), also find that $\alpha_{\mathrm{CO}}$ has weak or no correlation with high-$J$ CO to CO $J$=1-0 line ratios in starburst mergers.

We can also see from Fig. [11](#fig:alphaCO_r21) that our modeled $\alpha_{\mathrm{CO}}$ is mostly below the simulation prediction from (cite: gong2020). This could be due to other environmental factors. For example, given a fixed $R_{\mathrm{CO 2{-}1/1{-}0}}$ ratio, the Antennae has higher GMC surface density (and higher CO $J$=1-0 intensity) than those in Milky Way like simulations, which could contribute to the lower $\alpha_{\mathrm{CO}}$.

## Summary

The maps of $\alpha_{\mathrm{CO}}$, $\tau_{\mathrm{CO 1-0}}$ and $T_{\mathrm{kin}}$ are shown in Fig. [12](#fig:alphaCO_map). As discussed in Section [5.2](#subsubsec:alphaCO_tau), $\alpha_{\mathrm{CO}}$ is tightly correlated with $\tau_{\mathrm{CO 1-0}}$ so the two maps look quite similar. In contrast, $\alpha_{\mathrm{CO}}$ only has a weak anti-correlation with $T_{\mathrm{kin}}$ (Pearson coefficient of -0.17), which suggests that an increase in temperature is not the major factor in reducing $\alpha_{\mathrm{CO}}$ values in starburst mergers. This finding is consistent with studies of the centers of normal spiral galaxies (cite: teng2022; teng2023).

The bottom panels of Fig. [12](#fig:alphaCO_map) show the three observables that can be used to trace $\alpha_{\mathrm{CO}}$ variation. In theory, $R_{^{13}\mathrm{CO/CO}1-0}$ reflects the optical depth variation and hence the $\alpha_{\mathrm{CO}}$ variation (see Section [5.2](#subsubsec:alphaCO_tau)). The increase in $\sigma_v$ also acts in reducing the CO $J$=1-0 optical depth (Eq. [\[eq:optical_depth\]](#eq:optical_depth)), and therefore reducing the $\alpha_{\mathrm{CO}}$ value. The strong anti-correlation between $\alpha_{\mathrm{CO}}$ and $I_{\mathrm{CO1-0}}$ is less well-explained from the theoretical side. It is likely that the CO-bright regions (with high $I_{\mathrm{CO1-0}}$) have higher temperature and lower optical depth (due to large velocity dispersion), which act together to reduce the $\alpha_{\mathrm{CO}}$. We note that the $\alpha_{\mathrm{CO}}$ versus $I_{\mathrm{CO1-0}}$ relation has the shallowest slope among all the three relations, which suggests $\alpha_{\mathrm{CO}}$ is least sensitive to $I_{\mathrm{CO1-0}}$ variation.

In this section, we have given several parameterized relations to infer $\alpha_{\mathrm{CO}}$ from direct observables. These relations, although capturing the same trends, are notably different from $\alpha_{\mathrm{CO}}$ prescriptions from previous simulations and observations. We note that most previous studies at cloud-scale resolution have been focused on molecular gas in normal spiral galaxies. Therefore, it is possible that the difference is caused by different galactic environments. We recommend our relation be used to infer $\alpha_{\mathrm{CO}}$ in starburst systems, such as U/LIRGs. To test our relation in a broader range of starburst environments, we need to expand our cloud-scale RADEX modeling to a larger sample of starburst U/LIRGs.

# Constraining absolute $\alpha_{\mathrm{CO}}$ Values

## Constraining the $x_{\mathrm{CO}}$ abundance ratio with the dust mass

From the dust continuum map, we calculate the dust mass as (cite: wilson_luminous_2008) $$\begin{equation}
M_{\mathrm{dust}} = 74220 S_{880} D^2 \frac{\exp(17/T_{\mathrm{dust}})}{\kappa} 
\end{equation}$$ where $S_{880}$ is the flux in Jy, $D$ is the distance in Mpc, $T_{\mathrm{dust}}$ is the dust temperature in Kelvin and $\kappa$ is the dust opacity in g$^{-1}$ cm$^{2}$. We chose 0.9 g$^{-1}$ cm$^{2}$ as the fiducial value for $\kappa$ (cite: wilson_luminous_2008) but note that $\kappa$ can be a factor of 2 higher in starburst systems (cite: wilson2014). The dust surface density for a given pixel can then be calculated as $$\begin{equation}
\begin{split}
\Sigma_{\mathrm{dust}} &= M_{\mathrm{dust}} / (1.1331 B_{\mathrm{FWHM}}^2) \\
                       &= 2.9 I_{880} D^2 \frac{\exp(17/T_{\mathrm{dust}})}{\kappa} \left(\frac{B_{\mathrm{FWHM}}}{150\ \mathrm{pc}}\right)^{-2}
\end{split}
\end{equation}$$ where $I_{880}$ is the intensity in Jy/beam and $B_{\mathrm{FWHM}}$ is the FWHM of the round beam in pc. We adopt the dust temperature from (cite: klaas2010) for pixels in each defined subregion (Fig. [3](#fig:dust_350GHz)). For subregion A1a which does not have a temperature measurement, we assume the temperature to be the same as the overall dust temperature derived from the integrated fluxes of the entire galaxy (cite: klaas2010).

The comparison of $\Sigma_{\mathrm{mol}}$ and $\Sigma_{\mathrm{dust}}$ is shown in the left panel of Fig. [13](#fig:xco_GDR). We can see that a high $x_{\mathrm{CO}}$ value is favored in order to get a reasonable gas-to-dust ratio (GDR) below 200. Furthermore, since our modeling is targeting the densest GMCs, we would expect them to have GDR values closer to dense gas values of 50 – 100 instead of more diffuse medium values of 200 (cite: remy2017). If we instead assume a constant Milky Way $\alpha_{\mathrm{CO}}$ value, we would get GDR values of 300 – 400 (cite: klaas2010).

An alternative explanation is that the Antennae might actually have a high GDR values.

However, (cite: gunawardhana2020) derive the metallicity map for the Antennae and find most of regions in the Antennae have solar metallicity. Therefore, we would not expect the Antennae to have abnormally high GDR values.

The dust mass we calculate is affected by systematic uncertainties from parameters, such as dust temperature ($T_{\mathrm{dust}}$) and opacity ($\kappa$). The dust temperature calculated in (cite: klaas2010) is $\sim$ 20 K, while typical (U)LIRGs have temperatures of 20 – 40 K (cite: dunne_dust_2022). However, if we assume the higher dust temperature, we would obtain an even higher GDR value given a fixed $x_{\mathrm{CO}}$ value. The same logic also applies to dust opacity $\kappa$. (cite: wilson2014) suggest $\kappa$ can be two times higher in starburst systems than in the Milky Way. The higher $\kappa$ will lead to lower dust mass and hence higher GDR value given a fixed $x_{\mathrm{CO}}$. Therefore, increasing dust temperature and dust opacity does not help with reducing $x_{\mathrm{CO}}$ value, which further justifies our $x_{\mathrm{CO}}$ choice of 3$\times 10^{-4}$.

## GMC dynamical states in the Antennae

As discussed in (cite: he2023), the variation of $\alpha_{\mathrm{CO}}$ can lead to an uncertainty of a factor of 4 for GMC virial parameter ($\alpha_{\mathrm{vir}}$) measurements, hence affecting our estimates of GMC dynamical states in galaxy mergers. With our modeled $\alpha_{\mathrm{CO}}$, we can put a more accurate constraint on GMC dynamical states in the Antennae. With $x_{\mathrm{CO}}$ = $3 \times 10^{-4}$, most of our modeled $\alpha_{\mathrm{CO}}$ are close to U/LIRG values of 1.1 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$, which is different from previous works that suggest that the Antennae should have a Milky Way $\alpha_{\mathrm{CO}}$ of 4.3 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ (cite: wilson_mass_2003; zhu2003; schirm_herschel-spire_2014). This conclusion in general will increase the $\alpha_{\mathrm{vir}}$ of the Antennae, which suggests GMCs in the Antennae are less gravitationally bound than we might expect. As shown Fig. [14](#fig:vdep_Sigmol), our modeled $\alpha_{\mathrm{CO}}$ results suggest GMCs in the Antennae are more turbulent, which is consistent with the simulation prediction from (cite: he2023).

Fig. [14](#fig:vdep_Sigmol) also shows that our modeled $\alpha_{\mathrm{CO}}$ gives a similar contour shape as adopting a constant Milky Way $\alpha_{\mathrm{CO}}$. This similarity suggests that the absolute value of the average $\alpha_{\mathrm{CO}}$ matters more than the relative $\alpha_{\mathrm{CO}}$ variation within the galaxy in determining the overall GMC dynamical states in the Antennae.

(cite: wilson_mass_2003) first suggested a Milky Way $\alpha_{\mathrm{CO}}$ value based on comparison between virial mass and CO $J$=1-0 luminosity. However, GMCs in the Antennae are not necessarily in virial equilibrium. (cite: schirm_herschel-spire_2014) also suggest a typical $\alpha_{\mathrm{CO}}$ value of $\sim$ 7 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$ based on two-component LVG modeling assuming $x_{\mathrm{CO}} = 3 \times 10^{-5}$. They choose this $x_{\mathrm{CO}}$ value so that the hot component of gas from CO LVG modeling is comparable to the mass derived from infrared H$_2$ emission. However, (cite: harrington_turbulent_2021) suggest that the high-$J$ CO transitions that are used to constrain the second component might come from cold dense gas instead of hot diffuse gas, and hence not necessarily trace the same gas component as the H$_2$ emission. If (cite: schirm_herschel-spire_2014) adopt our $x_{\mathrm{CO}}$ choice of $3 \times 10^{-4}$, they will get a similar $\alpha_{\mathrm{CO}}$ value ($\sim$ 0.7) as ours.

# Modeled CO-to-H$_2$ conversion factor at kpc scales

## Modeling setup

In modeling $\alpha_{\mathrm{CO}}$ at kpc scales, we generally follow the same procedure as in Section [3.1](#subsec:RADEX_general), except that we sample the beam filling factor in log space ($\log \Phi_{\mathrm{bf}}$ from -3 to 0 with step of 0.1). This is because we expect the beam filling factor at kpc scales could be much lower than 0.1. For the $\alpha_{\mathrm{CO}}$ modeling results, we also exclude pixels with one or more modeled quantities at the edge of our parameter space (as in Appendix [10](#app:alphaCO)), specifically, pixels with $X_{\mathrm{12/13, 1dmax}} \leq 30$, $\log T_{\mathrm{kin, 1dmax}} < 1.1$ or $\log T_{\mathrm{kin, 1dmax}} > 2$.

## $\alpha_{\mathrm{CO}}$ comparison at GMC and kpc scales

Most previous studies on constraining $\alpha_{\mathrm{CO}}$ have been done at kpc scales (cite: papadopoulos_molecular_2012). Previous simulations (cite: narayanan2012) argue that $\alpha_{\mathrm{CO}}$ should be a scale-free parameter down to cloud scale. In other words, the large-scale $\alpha_{\mathrm{CO}}$ should equal the luminosity weighted cloud-scale $\alpha_{\mathrm{CO}}$. However, our observed line intensity maps at kpc-scale resolution are the convolution product of line intensity maps at cloud-scale resolution and the convolving beam set by the resolution of the telescope, and $\alpha_{\mathrm{CO}}$ modeling based on the convoluted data is not a linear process as averaging $\alpha_{\mathrm{CO}}$ weighted by the CO $J$=1-0 luminosities, and hence could lead to different $\alpha_{\mathrm{CO}}$ results. Furthermore, RADEX modeling generally assumes a uniform spherical structure, which is more applicable to individual GMCs than an ensemble of GMCs at kpc-scale resolution. Therefore, it is important to compare $\alpha_{\mathrm{CO}}$ modeling results at both scales to quantify the impact of these factors.

We generate the $\alpha_{\mathrm{CO}}$ map at kpc scale by applying the same procedure as in Section [3](#sec:RADEX_modeling) using the combo masked CO moment maps at 1 kpc resolution generated from the PHANGS-ALMA pipeline. To match the $\alpha_{\mathrm{CO}}$ maps at 150 pc and 1 kpc resolution, we regrid the 150 pc map to have the same pixel size as the 1 kpc map. For each regridded 150 pc map pixel, $\alpha_{\mathrm{CO}}$ is calculated as the CO $J$=1-0 intensity averaged value of the smaller pixels that are associated with the regridded pixel, $$\begin{equation}
\langle\alpha_{\mathrm{CO, 150pc}}\rangle_{\mathrm{1kpc}} = \frac{\sum \alpha_{\mathrm{CO, 150pc}} L^{\mathrm{150 pc}}_{\mathrm{CO(1-0)}}}{\sum  L^{\mathrm{150 pc}}_{\mathrm{CO(1-0)}}}, 
\end{equation}$$ where $L^{\mathrm{150 pc}}_{\mathrm{CO(1-0)}}$ is the CO $J$=1-0 luminosity of each pixel for 150 pc resolution map. We note that this calculation only includes pixels with robust $\alpha_{\mathrm{CO}}$ results (i.e. with detection of all five lines). The blank pixels are excluded and GMCs with highest surface densities have the highest weight. The comparison between $\alpha_{\mathrm{CO}}$ at both scales is shown in Fig. [15](#fig:alphaCO_kpc).

We can see that $\alpha_{\mathrm{CO}}$ values at kpc scale are about 60% of the CO $J$=1-0 intensity averaged $\alpha_{\mathrm{CO}}$ values at 150 pc scale. It is possible that kpc-scale CO emission includes a diffuse component that is not detected at GMC scales. This diffuse component would be warmer and more luminous and hence would have lower $\alpha_{\mathrm{CO}}$ values (cite: schirm_herschel-spire_2014; kamenetzky_warm_2017). To quantify this effect, we calculate the fraction of the emission at kpc scale that comes from dense GMCs. For each kpc-scale pixel, the total flux of GMC emission is calculated by summing up fluxes of all pixels in the 150 pc resolution map associated with the kpc-scale pixel and with valid $\alpha_{\mathrm{CO}}$ values. The GMC fraction is $$\begin{equation}
f_{\mathrm{GMC}} = \frac{\sum L^{\mathrm{150 pc}}_{\mathrm{CO(1-0)}}}{L^{\mathrm{1 kpc}}_{\mathrm{CO(1-0)}}}, 
\end{equation}$$ where $L^{\mathrm{1 kpc}}_{\mathrm{CO(1-0)}}$ is the CO $J$=1-0 luminosity for pixels in the 1 kpc resolution map. We note this sum also only includes pixels with $^{13}$CO detections, and hence is more representative of GMCs with high volume/surface density. GMCs excluded from the summing generally have low surface densities (or equivalently low CO $J$=1-0 luminosities). Therefore, we expect them to have higher $\alpha_{\mathrm{CO}}$ values based on the $\alpha_{\mathrm{CO}}$ versus $I_{\mathrm{CO 1-0}}$ trend (Fig. [8](#fig:alphaCO_Ico)). In other words, our cloud-scale averaged $\alpha_{\mathrm{CO}}$ values are biased towards lower values. In the left panel of Fig. [15](#fig:alphaCO_kpc), we color code the data points with $f_{\mathrm{GMC}}$. Data points with high fraction ($\sim$ 100%) are closer to the 1-to-1 line, which is consistent with our expectation.

We also calculate the Pearson correlation coefficient between $\alpha_{\mathrm{CO, 1kpc}}/\langle\alpha_{\mathrm{CO, 150pc}}\rangle_{\mathrm{1kpc}}$ and $f_{\mathrm{GMC}}$ and find a strong correlation between these two quantities with the coefficient of 0.62. This correlation suggests that an additional component of diffuse gas at kpc scale brings down the overall $\alpha_{\mathrm{CO}}$ value.

However, it is still under debate whether the diffuse component of molecular gas has higher or lower $\alpha_{\mathrm{CO}}$ compared to cold dense gas in GMCs. Liszt, Pety & Lucas (2010) show that $\alpha_{\mathrm{CO}}$ is relatively constant among different molecular gas components in our Milky Way. They suggest this constant $\alpha_{\mathrm{CO}}$ should be attributed to the offsetting effects of lower CO abundances with respect to H$_2$ ($x_{\mathrm{CO}}$) and a large $I_{\mathrm{CO}}$/$N_{\mathrm{CO}}$ ratio in low extinction gas. Recent studies by (cite: ramambason2023) further suggest that the abundance factor plays a more dominant role and hence actually increases $\alpha_{\mathrm{CO}}$ in diffuse molecular gas. We note that our modeling does not have the ability to constrain $x_{\mathrm{CO}}$. Therefore, the $\alpha_{\mathrm{CO}}$ we modeled is proportional to the $N_{\mathrm{CO}}$/$I_{\mathrm{CO}}$ ratio and hence does not reflect any $\alpha_{\mathrm{CO}}$ change due to CO abundance variation. For example, if the diffuse gas actually has lower $x_{\mathrm{CO}}$, we would expect the actual $\alpha_{\mathrm{CO}}$ at kpc scale to be higher than our modeled values.

## $\alpha_{\mathrm{CO}}$ dependence at kpc scale

Due to limited resolution and sensitivity, previous studies have been mostly focused on kpc-scale $\alpha_{\mathrm{CO}}$ calibrations. Besides metallicity, the two most widely used kpc-scale observables to calibrate $\alpha_{\mathrm{CO}}$ are CO $J$=1-0 intensity (cite: narayanan2012) and total galactic disk surface density (cite: bolatto_co–h_2013). However, while these prescriptions generally capture galaxy-to-galaxy variations, they are less well tested for $\alpha_{\mathrm{CO}}$ variations within individual galaxies, specifically for distant starburst galaxies that are hard to resolve. We test these two dependencies in the Antennae using our kpc-scale $\alpha_{\mathrm{CO}}$ data (Fig. [16](#fig:alphaCO_kpc_dependence)).

The left panel of Fig. [16](#fig:alphaCO_kpc_dependence) shows $\alpha_{\mathrm{CO}}$ versus $I_{\mathrm{CO 1-0}}$ in comparison with simulation predictions. We can see a negative correlation between these two quantities with slope (-0.3) close to the two simulation predictions (cite: narayanan2012). We also see offsets between observed and simulation predicted absolute values. We note that the simulation by (cite: hu2022) is focused on a typical kpc-size disk region in the Milky Way with a maximum $I_{\mathrm{CO 1-0}}$ of 1 K km s$^{-1}$ at kpc scales. Our observed $I_{\mathrm{CO 1-0}}$ is clearly out of this range. We also note that our $\alpha_{\mathrm{CO}}$ versus $I_{\mathrm{CO 1-0}}$ correlation at GMC scale is in relatively good agreement with the (cite: hu2022) prediction (Fig. [8](#fig:alphaCO_Ico)). Therefore, the discrepancy in the kpc-scale $\alpha_{\mathrm{CO}}$ versus $I_{\mathrm{CO 1-0}}$ correlation might be caused by differences in GMC beam filling factor at kpc scales. If the number of GMCs inside the simulated kpc box were increased, we would expect higher kpc-scale $I_{\mathrm{CO 1-0}}$ for a given $\alpha_{\mathrm{CO}}$, which would bring the simulation predicted relation rightward to become more aligned with our observed $\alpha_{\mathrm{CO}}$. On the other hand, the simulation from (cite: narayanan2012) gives larger $\alpha_{\mathrm{CO}}$ than our modeled results. We note that $\alpha_{\mathrm{CO}}$ at kpc scale in (cite: narayanan2012) is calculated as the CO $J$=1-0 intensity averaged value of $\alpha_{\mathrm{CO}}$ of individual clouds, which is similar to what we did to calculate $\langle\alpha_{\mathrm{CO, 150pc}}\rangle_{\mathrm{1kpc}}$ in Section [7.2](#subsec:GMC_kpc_comparison). Therefore, the discrepancy might be due to our inclusion of a diffuse molecular gas component that brings down the $\alpha_{\mathrm{CO}}$ values. It is also possible that the true $x_{\mathrm{CO}}$ is slightly lower than $3 \times 10^{-4}$ and the actual $\alpha_{\mathrm{CO}}$ in the Antennae might be higher than our derived values.

The right panel of Fig. [16](#fig:alphaCO_kpc_dependence) shows $\alpha_{\mathrm{CO}}$ versus the total surface density compared with the empirical relation by (cite: bolatto_co–h_2013). The absolute $\alpha_{\mathrm{CO}}$ values are generally consistent with the theoretical expectation but with a large scatter. We also do not see a significant correlation between these two quantities for the Antennae alone (Pearson coefficient of -0.11) or the Antennae and other U/LIRGs combined (Pearson coefficient of -0.16). However, the large uncertainty (factor of $\sim$3) in our modeled $\alpha_{\mathrm{CO}}$ values might act to smear out the trend.

# Conclusions

In this paper, we have constrained the spatial variation of the CO-to-H$_2$ conversion, $\alpha_{\mathrm{CO}}$, in the Antennae merger at both GMC and kpc scales based on high-resolution ALMA CO and $^{13}$CO lines. Our main conclusions are summarized below.

- The CO $J$=2-1/1-0 ($\sim$ 1) and CO $J$=3-2/1-0 ($\sim$ 0.7) ratios in the Antennae are significantly higher than the commonly observed ratio in normal spiral galaxies (cite: leroy2021; wilson2012; leroy2022). These large ratios suggest that molecular gas in this starburst system has higher volume density and/or kinetic temperature compared to normal spiral galaxies.

- The $^{13}$CO/CO $J$=1-0 and $^{13}$CO/CO $J$=2-1 ratios ($\sim$ 0.1) in the Antennae are similar to those in normal spiral galaxies (cite: cormier_full-disc_2018) but larger than typical U/LIRGs (cite: brown2019). The difference in the isotopologue ratios between the Antennae and U/LIRGs is likely due to optical depth effects as U/LIRGs might be undergoing stronger stellar feedback from more intense starburst activity, which disperses the molecular gas and reduces its optical depth.

- We have derived the first resolved $\alpha_{\mathrm{CO}}$ map for the Antennae down to GMC scale ($\sim$ 150 pc). We find that $\alpha_{\mathrm{CO}}$ has a significant anti-correlation with GMC integrated intensity, $I_{\mathrm{CO 1-0}}$, which is consistent with simulation predictions (cite: gong2020; hu2022). This supports the argument that $\alpha_{\mathrm{CO}}$ has a continuous dependence on $I_{\mathrm{CO 1-0}}$ instead of a bimodal distribution among normal spiral and starburst galaxies.

- We find that $\alpha_{\mathrm{CO}}$ has a strong, tight linear correlation with the CO optical depth. This suggests that $\alpha_{\mathrm{CO}}$ variations in starburst systems are mainly driven by optical depth variations rather than kinetic temperature variations, which is consistent with $\alpha_{\mathrm{CO}}$ studies in normal galaxy centers (cite: teng2022; teng2023). We also find a relatively tight correlation between $\alpha_{\mathrm{CO}}$ and the $^{13}$CO/CO $J$=1-0 ratio. This correlation is consistent with our expectation that the $^{13}$CO/CO $J$=1-0 ratio can probe the molecular gas optical depth. The scatter in the $\alpha_{\mathrm{CO}}$ versus $^{13}$CO/CO $J$=1-0 ratio is mainly driven by the varying \[$\mathrm{CO}$\]/\[$\mathrm{^{13}CO}$\] abundance ratio.

- We find that $\alpha_{\mathrm{CO}}$ is also tightly related to the GMC dynamical state. The strong anti-correlation between $\alpha_{\mathrm{CO}}$ and $\sigma_v$ has a slope consistent with theoretical prediction of -0.5. This result is consistent with previous LVG studies on U/LIRGs (cite: papadopoulos_molecular_2012), which suggested that the low $\alpha_{\mathrm{CO}}$ values in these systems are mainly caused by GMCs with large velocity dispersion and hence being out of virial equilibrium.

- We compare our modeled gas surface density with 345 GHz dust continuum. Our comparison shows that our chosen $[\mathrm{CO}]$/$[\mathrm{H_2}]$ abundance ratio $x_{\mathrm{CO}} = 3 \times 10^{-4}$ gives us reasonable gas-to-dust ratios of $\sim$ 100. Given this abundance ratio choice, we would expect most $\alpha_{\mathrm{CO}}$ values in the Antennae are close to the typical U/LIRG value of 1.1 $\mathrm{M_{\odot}\ (K\ km\ s^{-1}\ pc^{2})^{-1}}$. This $\alpha_{\mathrm{CO}}$ will put most GMCs in the Antennae out of virial equilibrium, which is consistent with simulation predictions of GMCs in starburst mergers (cite: he2023).

- We compare luminosity weighted GMC-scale $\alpha_{\mathrm{CO}}$ values averaged at kpc resolution with $\alpha_{\mathrm{CO}}$ values directly derived from kpc-resolution data. Our comparison shows that kpc-scale $\alpha_{\mathrm{CO}}$ from LVG modeling is about 60% of the averaged value of $\alpha_{\mathrm{CO}}$ at 150 pc scale. We think that the lower $\alpha_{\mathrm{CO}}$ at kpc scale might be due to a diffuse warm component that has intrinsically lower $\alpha_{\mathrm{CO}}$.

- We also explore the dependence of the modeled $\alpha_{\mathrm{CO}}$ at kpc scales on various observables. We find that the kpc-scale $\alpha_{\mathrm{CO}}$ shows a similar anti-correlation with CO intensity as predicted by simulations (cite: narayanan2012; hu2022). We also tested the anti-correlation between $\alpha_{\mathrm{CO}}$ and total surface density, $\Sigma_{\mathrm{tot}}$, as suggested in (cite: bolatto_co–h_2013). We find $\alpha_{\mathrm{CO}}$ of the Antennae lies along the trend with normal spiral galaxies and U/LIRGs with the absolute values consistent with the prescription prediction. We do not find a significant anti-correlation between $\alpha_{\mathrm{CO}}$ and $\Sigma_{\mathrm{tot}}$ for the Antennae alone, which could be due to large uncertainties in our modeled $\alpha_{\mathrm{CO}}$ values.

We thank the referee for thoughtful comments and constructive suggestions. This paper makes the uses of the following ALMA data:\
ADS/JAO.ALMA \# 2018.1.00272.S\
ADS/JAO.ALMA \# 2021.1.00439.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work is based in part on observations made with the Spitzer Space Telescope, which was operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA. The research of CDW and ER is supported by grants from the Natural Sciences and Engineering Research Council of Canada (NSERC), and also for CDW the Canada Research Chairs program. JS acknowledges support by the National Aeronautics and Space Administration (NASA) through the NASA Hubble Fellowship grant HST-HF2-51544 awarded by the Space Telescope Science Institute (STScI), which is operated by the Association of Universities for Research in Astronomy, Inc., under contract NAS 5-26555.

# Data Availability

The code to generate RADEX modeling grids and perform Bayesian analysis on multiple CO and its isotopologue lines is available on both Zenodo (<https://zenodo.org/records/10845936>) and GitHub$^{\ref{github}}$. The modeled maps of gas physical properties and CO-to-H$_2$ conversion factor are available from the corresponding author on request.

# Facilities

ALMA, Spitzer

# Software

astropy (cite: the_astropy_collaboration_astropy_2013; Astropy_2018; Astropy_2022), CASA (cite: CASA_2022)

natexlab

(ref: abdo2010) Abdo, A. A., Ackermann, M., Ajello, M., et al. 2010, The Astrophysical Journal, 710, 133, doi: [`10.1088/0004-637X/710/1/133`](http://doi.org/10.1088/0004-637X/710/1/133)

(ref: accurso2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, Monthly Notices of the Royal Astronomical Society, 470, 4750, doi: [`10.1093/mnras/stx1556`](http://doi.org/10.1093/mnras/stx1556)

(ref: amorín2016) Amorín, R., Muñoz-Tuñón, C., Aguerri, J. A. L., & Planesas, P. 2016, Astronomy and Astrophysics, 588, A23, doi: [`10.1051/0004-6361/201526397`](http://doi.org/10.1051/0004-6361/201526397)

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy_2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: bemis2019) Bemis, A., & Wilson, C. D. 2019, The Astronomical Journal, 157, 131, doi: [`10.3847/1538-3881/ab041d`](http://doi.org/10.3847/1538-3881/ab041d)

(ref: bolatto2003) Bolatto, A. D., Leroy, A., Israel, F. P., & Jackson, J. M. 2003, The Astrophysical Journal, 595, 167, doi: [`10.1086/377230`](http://doi.org/10.1086/377230)

(ref: bolatto2008) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, The Astrophysical Journal, 686, 948, doi: [`10.1086/591513`](http://doi.org/10.1086/591513)

(ref: bolatto_co–h_2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, Annual Review of Astronomy and Astrophysics, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: boulanger1996) Boulanger, F., Abergel, A., Bernard, J. P., et al. 1996, Astronomy and Astrophysics, 312, 256

(ref: bournaud2015) Bournaud, F., Daddi, E., Weiß, A., et al. 2015, A&A, 575, A56, doi: [`10.1051/0004-6361/201425078`](http://doi.org/10.1051/0004-6361/201425078)

(ref: brown2019) Brown, T., & Wilson, C. D. 2019, The Astrophysical Journal, 879, 17, doi: [`10.3847/1538-4357/ab2246`](http://doi.org/10.3847/1538-4357/ab2246)

(ref: brunetti_cloud-scale_2022) Brunetti, N. 2022, Thesis

(ref: brunetti_extreme_2022) Brunetti, N., & Wilson, C. D. 2022, Monthly Notices of the Royal Astronomical Society, 515, 2928, doi: [`10.1093/mnras/stac1975`](http://doi.org/10.1093/mnras/stac1975)

(ref: brunetti_highly_2020) Brunetti, N., Wilson, C. D., Sliwa, K., et al. 2020, Monthly Notices of the Royal Astronomical Society, 500, 4730, doi: [`10.1093/mnras/staa3425`](http://doi.org/10.1093/mnras/staa3425)

(ref: bryant1996) Bryant, P. M., & Scoville, N. Z. 1996, The Astrophysical Journal, 457, 678, doi: [`10.1086/176763`](http://doi.org/10.1086/176763)

(ref: bryant1999) —. 1999, The Astronomical Journal, 117, 2632, doi: [`10.1086/300879`](http://doi.org/10.1086/300879)

(ref: carleton2017a) Carleton, T., Cooper, M. C., Bolatto, A. D., et al. 2017, Monthly Notices of the Royal Astronomical Society, 467, 4886, doi: [`10.1093/mnras/stx390`](http://doi.org/10.1093/mnras/stx390)

(ref: CASA_2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Chandar2017) Chandar, R., Fall, S. M., Whitmore, B. C., & Mulia, A. J. 2017, The Astrophysical Journal, 849, 128, doi: [`10.3847/1538-4357/aa92ce`](http://doi.org/10.3847/1538-4357/aa92ce)

(ref: the_astropy_collaboration_astropy_2013) Collaboration, T. A., Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: cormier_full-disc_2018) Cormier, D., Bigiel, F., Jiménez-Donaire, M. J., et al. 2018, Monthly Notices of the Royal Astronomical Society, 475, 3909, doi: [`10.1093/mnras/sty059`](http://doi.org/10.1093/mnras/sty059)

(ref: dame2001) Dame, T. M., Hartmann, D., & Thaddeus, P. 2001, The Astrophysical Journal, 547, 792, doi: [`10.1086/318388`](http://doi.org/10.1086/318388)

(ref: donovanmeyer2012) Donovan Meyer, J., Koda, J., Momose, R., et al. 2012, The Astrophysical Journal, 744, 42, doi: [`10.1088/0004-637X/744/1/42`](http://doi.org/10.1088/0004-637X/744/1/42)

(ref: downes_rotating_1998) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: downes1993) Downes, D., Solomon, P. M., & Radford, S. J. E. 1993, The Astrophysical Journal, 414, L13, doi: [`10.1086/186984`](http://doi.org/10.1086/186984)

(ref: dunne_dust_2022) Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L. 2022, Monthly Notices of the Royal Astronomical Society, 517, 962, doi: [`10.1093/mnras/stac2098`](http://doi.org/10.1093/mnras/stac2098)

(ref: eskew2012) Eskew, M., Zaritsky, D., & Meidt, S. 2012, Astronomical Journal, 143, 4, doi: [`10.1088/0004-6256/143/6/139`](http://doi.org/10.1088/0004-6256/143/6/139)

(ref: goldsmith2008) Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, The Astrophysical Journal, 680, 428, doi: [`10.1086/587166`](http://doi.org/10.1086/587166)

(ref: gong2020) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, The Astrophysical Journal, 903, 142, doi: [`10.3847/1538-4357/abbdab`](http://doi.org/10.3847/1538-4357/abbdab)

(ref: grenier2005) Grenier, I. A., Casandjian, J.-M., & Terrier, R. 2005, Science, 307, 1292, doi: [`10.1126/science.1106924`](http://doi.org/10.1126/science.1106924)

(ref: gunawardhana2020) Gunawardhana, M. L. P., Brinchmann, J., Weilbacher, P. M., et al. 2020, Monthly Notices of the Royal Astronomical Society, 497, 3860, doi: [`10.1093/mnras/staa2158`](http://doi.org/10.1093/mnras/staa2158)

(ref: harrington_turbulent_2021) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, The Astrophysical Journal, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: he2023) He, H., Bottrell, C., Wilson, C., et al. 2023, Molecular Gas and Star Formation in Nearby Starburst Galaxy Mergers, doi: [`10.48550/arXiv.2301.13250`](http://doi.org/10.48550/arXiv.2301.13250)

(ref: he2022) He, H., Wilson, C., Brunetti, N., et al. 2022, The Astrophysical Journal, 928, 57, doi: [`10.3847/1538-4357/ac5628`](http://doi.org/10.3847/1538-4357/ac5628)

(ref: he2020) He, H., Wilson, C. D., Sliwa, K., Iono, D., & Saito, T. 2020, Monthly Notices of the Royal Astronomical Society, 496, 5243, doi: [`10.1093/mnras/staa1826`](http://doi.org/10.1093/mnras/staa1826)

(ref: heyer2001) Heyer, M. H., Carpenter, J. M., & Snell, R. L. 2001, The Astrophysical Journal, 551, 852, doi: [`10.1086/320218`](http://doi.org/10.1086/320218)

(ref: hu2022) Hu, C.-Y., Schruba, A., Sternberg, A., & van Dishoeck, E. F. 2022, ApJ, 931, 28, doi: [`10.3847/1538-4357/ac65fd`](http://doi.org/10.3847/1538-4357/ac65fd)

(ref: jimenez-donaire_optical_2017) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2017, Monthly Notices of the Royal Astronomical Society, 466, 49, doi: [`10.1093/mnras/stw2996`](http://doi.org/10.1093/mnras/stw2996)

(ref: kamenetzky_warm_2017) Kamenetzky, J., Rangwala, N., & Glenn, J. 2017, Monthly Notices of the Royal Astronomical Society, 471, 2917, doi: [`10.1093/mnras/stx1595`](http://doi.org/10.1093/mnras/stx1595)

(ref: karl2010) Karl, S. J., Naab, T., Johansson, P. H., et al. 2010, The Astrophysical Journal, 715, L88, doi: [`10.1088/2041-8205/715/2/L88`](http://doi.org/10.1088/2041-8205/715/2/L88)

(ref: kazandjian2015) Kazandjian, M. V., Meijerink, R., Pelupessy, I., Israel, F. P., & Spaans, M. 2015, Astronomy and Astrophysics, 574, A127, doi: [`10.1051/0004-6361/201322805`](http://doi.org/10.1051/0004-6361/201322805)

(ref: keller_superbubble_2014) Keller, B. W., Wadsley, J., Benincasa, S. M., & Couchman, H. M. P. 2014, Monthly Notices of the Royal Astronomical Society, 442, 3013, doi: [`10.1093/mnras/stu1058`](http://doi.org/10.1093/mnras/stu1058)

(ref: klaas2010) Klaas, U., Nielbock, M., Haas, M., Krause, O., & Schreiber, J. 2010, Astronomy and Astrophysics, 518, L44, doi: [`10.1051/0004-6361/201014670`](http://doi.org/10.1051/0004-6361/201014670)

(ref: langer1990) Langer, W. D., & Penzias, A. A. 1990, The Astrophysical Journal, 357, 477, doi: [`10.1086/168935`](http://doi.org/10.1086/168935)

(ref: leroy2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, The Astrophysical Journal, 737, 12, doi: [`10.1088/0004-637X/737/1/12`](http://doi.org/10.1088/0004-637X/737/1/12)

(ref: leroy2017) Leroy, A. K., Usero, A., Schruba, A., et al. 2017, The Astrophysical Journal, 835, 217, doi: [`10.3847/1538-4357/835/2/217`](http://doi.org/10.3847/1538-4357/835/2/217)

(ref: leroy2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: leroy2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, The Astrophysical Journal, 927, 149, doi: [`10.3847/1538-4357/ac3490`](http://doi.org/10.3847/1538-4357/ac3490)

(ref: li2020) Li, Z., Li, Z., Smith, M. W. L., et al. 2020, Monthly Notices of the Royal Astronomical Society, 492, 195, doi: [`10.1093/mnras/stz3409`](http://doi.org/10.1093/mnras/stz3409)

(ref: magnelli2012) Magnelli, B., Saintonge, A., Lutz, D., et al. 2012, Astronomy and Astrophysics, 548, A22, doi: [`10.1051/0004-6361/201220074`](http://doi.org/10.1051/0004-6361/201220074)

(ref: maloney1990) Maloney, P. 1990, The Astrophysical Journal, 348, L9, doi: [`10.1086/185618`](http://doi.org/10.1086/185618)

(ref: milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, The Astrophysical Journal, 634, 1126, doi: [`10.1086/497123`](http://doi.org/10.1086/497123)

(ref: mok_mass_2020) Mok, A., Chandar, R., & Fall, S. M. 2020, The Astrophysical Journal, 893, 135, doi: [`10.3847/1538-4357/ab7a14`](http://doi.org/10.3847/1538-4357/ab7a14)

(ref: montoyaarroyave2023) Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, Astronomy and Astrophysics, 673, A13, doi: [`10.1051/0004-6361/202245046`](http://doi.org/10.1051/0004-6361/202245046)

(ref: narayanan_co-h2conversion_2011) Narayanan, D., Krumholz, M., Ostriker, E. C., & Hernquist, L. 2011, Monthly Notices of the Royal Astronomical Society, 418, 664, doi: [`10.1111/j.1365-2966.2011.19516.x`](http://doi.org/10.1111/j.1365-2966.2011.19516.x)

(ref: narayanan2012) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, Monthly Notices of the Royal Astronomical Society, 421, 3127, doi: [`10.1111/j.1365-2966.2012.20536.x`](http://doi.org/10.1111/j.1365-2966.2012.20536.x)

(ref: olsen2016) Olsen, K. P., Greve, T. R., Brinch, C., et al. 2016, Monthly Notices of the Royal Astronomical Society, 457, 3306, doi: [`10.1093/mnras/stw162`](http://doi.org/10.1093/mnras/stw162)

(ref: papadopoulos_molecular_2012) Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M., et al. 2012, Monthly Notices of the Royal Astronomical Society, 426, 2601, doi: [`10.1111/j.1365-2966.2012.21001.x`](http://doi.org/10.1111/j.1365-2966.2012.21001.x)

(ref: pessa2021) Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, Astronomy and Astrophysics, 650, A134, doi: [`10.1051/0004-6361/202140733`](http://doi.org/10.1051/0004-6361/202140733)

(ref: planckcollaboration2011) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2011, Astronomy and Astrophysics, 536, A19, doi: [`10.1051/0004-6361/201116479`](http://doi.org/10.1051/0004-6361/201116479)

(ref: privon_dynamical_2013) Privon, G. C., Barnes, J. E., Evans, A. S., et al. 2013, Astrophysical Journal, 771, doi: [`10.1088/0004-637X/771/2/120`](http://doi.org/10.1088/0004-637X/771/2/120)

(ref: ramambason2023) Ramambason, L., Lebouteiller, V., Madden, S. C., et al. 2023, Molecular Gas Distribution and CO-to-H2 Conversion Factors in CO-faint Low-Metallicity Dwarf Galaxies, doi: [`10.48550/arXiv.2306.14881`](http://doi.org/10.48550/arXiv.2306.14881)

(ref: rebolledo2012) Rebolledo, D., Wong, T., Leroy, A., Koda, J., & Donovan Meyer, J. 2012, The Astrophysical Journal, 757, 155, doi: [`10.1088/0004-637X/757/2/155`](http://doi.org/10.1088/0004-637X/757/2/155)

(ref: remy2017) Remy, Q., Grenier, I. A., Marshall, D. J., & Casandjian, J. M. 2017, Astronomy and Astrophysics, 601, A78, doi: [`10.1051/0004-6361/201629632`](http://doi.org/10.1051/0004-6361/201629632)

(ref: renaud_diversity_2019) Renaud, F., Bournaud, F., Agertz, O., et al. 2019a, Astronomy & Astrophysics, 625, A65, doi: [`10.1051/0004-6361/201935222`](http://doi.org/10.1051/0004-6361/201935222)

(ref: renaud_three_2019) Renaud, F., Bournaud, F., Daddi, E., & Weiß, A. 2019b, Astronomy &amp; Astrophysics, Volume 621, id.A104, $<$NUMPAGES$>$5$<$/NUMPAGES$>$ pp., 621, A104, doi: [`10.1051/0004-6361/201834397`](http://doi.org/10.1051/0004-6361/201834397)

(ref: sandstrom_co–h2_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013a, The Astrophysical Journal, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: sandstrom2013) —. 2013b, The Astrophysical Journal, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: sargent_regularity_2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, Astrophysical Journal, 793, doi: [`10.1088/0004-637X/793/1/19`](http://doi.org/10.1088/0004-637X/793/1/19)

(ref: schirm_herschel-spire_2014) Schirm, M. R. P., Wilson, C. D., Parkin, T. J., et al. 2014, The Astrophysical Journal, 781, 101, doi: [`10.1088/0004-637X/781/2/101`](http://doi.org/10.1088/0004-637X/781/2/101)

(ref: schruba2012) Schruba, A., Leroy, A. K., Walter, F., et al. 2012, The Astronomical Journal, 143, 138, doi: [`10.1088/0004-6256/143/6/138`](http://doi.org/10.1088/0004-6256/143/6/138)

(ref: schweizer2008) Schweizer, F., Burns, C. R., Madore, B. F., et al. 2008, The Astronomical Journal, 136, 1482, doi: [`10.1088/0004-6256/136/4/1482`](http://doi.org/10.1088/0004-6256/136/4/1482)

(ref: scoville1989) Scoville, N. Z., & Good, J. C. 1989, The Astrophysical Journal, 339, 149, doi: [`10.1086/167283`](http://doi.org/10.1086/167283)

(ref: scoville1987) Scoville, N. Z., Yun, M. S., Clemens, D. P., Sanders, D. B., & Waller, W. H. 1987, The Astrophysical Journal Supplement Series, 63, 821, doi: [`10.1086/191185`](http://doi.org/10.1086/191185)

(ref: shetty2011) Shetty, R., Glover, S. C., Dullemond, C. P., et al. 2011, Monthly Notices of the Royal Astronomical Society, 415, 3253, doi: [`10.1111/j.1365-2966.2011.18937.x`](http://doi.org/10.1111/j.1365-2966.2011.18937.x)

(ref: sliwa_pdbi_2017) Sliwa, K., & Downes, D. 2017, Astronomy &amp; Astrophysics, Volume 604, id.A2, $<$NUMPAGES$>$16$<$/NUMPAGES$>$ pp., 604, A2, doi: [`10.1051/0004-6361/201630139`](http://doi.org/10.1051/0004-6361/201630139)

(ref: sliwa_extreme_2017) Sliwa, K., Wilson, C. D., Aalto, S., & Privon, G. C. 2017a, The Astrophysical Journal, 840, L11, doi: [`10.3847/2041-8213/aa6ea4`](http://doi.org/10.3847/2041-8213/aa6ea4)

(ref: sliwa_around_2014) Sliwa, K., Wilson, C. D., Iono, D., Peck, A., & Matsushita, S. 2014, The Astrophysical Journal, 796, L15, doi: [`10.1088/2041-8205/796/1/L15`](http://doi.org/10.1088/2041-8205/796/1/L15)

(ref: sliwa2017) Sliwa, K., Wilson, C. D., Matsushita, S., et al. 2017b, The Astrophysical Journal, 840, 8, doi: [`10.3847/1538-4357/aa689b`](http://doi.org/10.3847/1538-4357/aa689b)

(ref: sliwa2012) Sliwa, K., Wilson, C. D., Petitpas, G. R., et al. 2012, Astrophysical Journal, 753, doi: [`10.1088/0004-637X/753/1/46`](http://doi.org/10.1088/0004-637X/753/1/46)

(ref: sliwa2013) Sliwa, K., Wilson, C. D., Krips, M., et al. 2013, Astrophysical Journal, 777, doi: [`10.1088/0004-637X/777/2/126`](http://doi.org/10.1088/0004-637X/777/2/126)

(ref: solomon1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, The Astrophysical Journal, 478, 144, doi: [`10.1086/303765`](http://doi.org/10.1086/303765)

(ref: solomon1987) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, The Astrophysical Journal, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: solomon2005) Solomon, P. M., & Vanden Bout, P. A. 2005, Annual Review of Astronomy and Astrophysics, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: strong1996) Strong, A. W., & Mattox, J. R. 1996, Astronomy and Astrophysics, 308, L21

(ref: sun_cloud-scale_2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, The Astrophysical Journal, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: sun_molecular_2020) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020a, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: sun\_\_dynamical_2020) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020b, ApJ, 892, 148, doi: [`10.3847/1538-4357/ab781c`](http://doi.org/10.3847/1538-4357/ab781c)

(ref: sun_molecular_2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, The Astronomical Journal, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: sun2023) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, Star Formation Laws and Efficiencies across 80 Nearby Galaxies, doi: [`10.48550/arXiv.2302.12267`](http://doi.org/10.48550/arXiv.2302.12267)

(ref: teng2022) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2022, The Astrophysical Journal, 925, 72, doi: [`10.3847/1538-4357/ac382f`](http://doi.org/10.3847/1538-4357/ac382f)

(ref: teng2023) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2023, ApJ, 950, 119, doi: [`10.3847/1538-4357/accb86`](http://doi.org/10.3847/1538-4357/accb86)

(ref: teng2024) Teng, Y.-H., Chiang, I. D., Sandstrom, K. M., et al. 2024, The Astrophysical Journal, 961, 42, doi: [`10.3847/1538-4357/ad10ae`](http://doi.org/10.3847/1538-4357/ad10ae)

(ref: van_der_tak_computer_2007) Van Der Tak, F. F., Black, J. H., Schöier, F. L., Jansen, D. J., & Van Dishoeck, E. F. 2007, Astronomy and Astrophysics, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vigroux1976) Vigroux, L., Audouze, J., & Lequeux, J. 1976, Astronomy and Astrophysics, 52, 1

(ref: vlahakis2013) Vlahakis, C., van der Werf, P., Israel, F. P., & Tilanus, R. P. J. 2013, Monthly Notices of the Royal Astronomical Society, 433, 1837, doi: [`10.1093/mnras/stt841`](http://doi.org/10.1093/mnras/stt841)

(ref: whitmore2014a) Whitmore, B. C., Brogan, C., Chandar, R., et al. 2014, ApJ, 795, 156, doi: [`10.1088/0004-637X/795/2/156`](http://doi.org/10.1088/0004-637X/795/2/156)

(ref: wilson2014) Wilson, C. D., Rangwala, N., Glenn, J., et al. 2014, The Astrophysical Journal, 789, L36, doi: [`10.1088/2041-8205/789/2/L36`](http://doi.org/10.1088/2041-8205/789/2/L36)

(ref: wilson_mass_2003) Wilson, C. D., Scoville, N., Madden, S. C., & Charmandaris, V. 2003, The Astrophysical Journal, 599, 1049, doi: [`10.1086/379344`](http://doi.org/10.1086/379344)

(ref: wilson_luminous_2008) Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, The Astrophysical Journal Supplement Series, 178, 189, doi: [`10.1086/590910`](http://doi.org/10.1086/590910)

(ref: wilson2012) Wilson, C. D., Warren, B. E., Israel, F. P., et al. 2012, Monthly Notices of the Royal Astronomical Society, 424, 3050, doi: [`10.1111/j.1365-2966.2012.21453.x`](http://doi.org/10.1111/j.1365-2966.2012.21453.x)

(ref: wolfire2010) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, The Astrophysical Journal, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: young1991) Young, J. S., & Scoville, N. Z. 1991, Annual Review of Astronomy and Astrophysics, 29, 581, doi: [`10.1146/annurev.aa.29.090191.003053`](http://doi.org/10.1146/annurev.aa.29.090191.003053)

(ref: zhang_antennae_2001) Zhang, Q., Fall, S. M., & Whitmore, B. C. 2001, Observatory, 10

(ref: zhu2003) Zhu, M., Seaquist, E. R., & Kuno, N. 2003, The Astrophysical Journal, 588, 243, doi: [`10.1086/368353`](http://doi.org/10.1086/368353)

# Bayesian Analyses in Our RADEX Modeling

| Solution | Condition |
|:--:|:--:|
| Bestfit | $P(\vec{\theta}_{\mathrm{Bestfit}}|\vec{I}_{\mathrm{obs}}) = \max P(\vec{\theta}|\vec{I}_{\mathrm{obs}})$ |
| 1DMax | $P(\theta_{i, \mathrm{1DMax}}|\vec{I}_{\mathrm{obs}}) = \max P(\theta_i|\vec{I}_{\mathrm{obs}})$ |
| Neg1Sig | $\int^{\theta_{i, \mathrm{Neg1Sig}}} d\theta_i P(\theta_i|\vec{I}_{\mathrm{obs}}) = 0.16$ |
| Median | $\int^{\theta_{i, \mathrm{Median}}} d\theta_i P(\theta_i|\vec{I}_{\mathrm{obs}}) = 0.5$ |
| Pos1Sig | $\int^{\theta_{i, \mathrm{Pos1Sig}}} d\theta_i P(\theta_i|\vec{I}_{\mathrm{obs}}) = 0.84$ |

: Solutions for the Modeled Parameter

We follow the Bayesian likelihood analyses in (cite: teng2022) to characterize the probability density function (PDF) for the five varying parameters. For each pixel, the code calculates the $\chi^2$ by comparing the modeled line intensities with the measured line intensities. Note that in (cite: teng2022), they compare modeled and measured integrated line intensities. While they assumed a fixed velocity FWHM that is representative of their observed region, this may introduce the issue that the fixed velocity FWHM (15 km s$^{-1}$) in the modeling is inconsistent with varying velocity FWHMs measured for different pixels in the observations (cite: teng2023). Since our modeled intensity corresponds to linewidth of 15 km s$^{-1}$, we need to rescale modeled intensity by multiplying the ratio of measured linewidth to the fixed linewidth of 15 km s$^{-1}$ for each pixel. Then we calculate the $\chi^2$ matrix as $$\begin{equation}
\chi^2 (\vec{\theta}) = \sum_{i=1}^{N=5} \frac{I^{\mathrm{mod, scaled}}_i(\vec{\theta})-I^{\mathrm{obs}}_i}{\sigma_i^2}
\end{equation}$$ where $\vec{\theta}$ represents each modeled parameter set of $(n_{\mathrm{H_2}}, T_{\mathrm{kin}}, N_{\mathrm{CO}}/\Delta v, X_{12/13}, \Phi_{\mathrm{bf}})$, $I_i^{\mathrm{mod, scaled}} = I_i^{\mathrm{mod}} \frac{\Delta v}{15 \mathrm{km s^{-1}}}$ represents the scaled modeled integrated intensity for each line and $I_i^{\mathrm{obs}}$ represents the integrated intensities from observations, $\sigma_i$ the measurement uncertainty for $I_i^{\mathrm{obs}}$ of each line and $N$ specifies the number of lines used for the modeling. For each pixel value, we calculate the posterior probability distribution function across the 5D model parameter space as $$\begin{equation}
P(\vec{\theta}|\vec{I}_{\mathrm{obs}}) = \frac{1}{Q} \exp(-\chi^2/2)
\end{equation}$$ where $Q^2 = (2\pi)^5 \prod_{i} \sigma_i^2$ is the normalization coefficient. From the 5D distribution, we can calculate the ’Bestfit’ set of modeled parameters with maximal $P(\vec{\theta}|\vec{I}_{\mathrm{obs}})$. We can also calculate the marginalized 1D probability distribution for each individual modeled parameter by integrating the 5D $P(\vec{\theta}|\vec{I}_{\mathrm{obs}})$ over the rest of parameter space. The equation for the 1D marginalized distribution is $$\begin{equation}
P(\theta_i|\vec{I}_{\mathrm{obs}}) = \idotsint \limits_{j \neq i} d\theta_j \ P(\vec{\theta}|\vec{I}_{\mathrm{obs}}) 
\end{equation}$$ where $\theta_i$ is the one modeled parameter that we want to calculate the 1D marginalized distribution and $\theta_j$ are the rest of modeled parameters.

We show the 1D and 2D probability distribution for each modeled quantity in Fig. [17](#fig:RADEX_marginalize) for one of the pixels in north nucleus (marked as red dot in Fig. [1](#fig:co10_moments)). For most quantities, the median of the 1D probability distribution corresponds well with the ‘1DMax’ value of the distribution, which suggests that our modeling recovers the most probable solution. One exception is $X_{12/13}$, which has double peaks in its 1D distribution. This is a common behavior for most of our pixels, which suggests that the $X_{12/13}$ value is less well constrained. Therefore, for all of the modeled physical quantities except for $X_{12/13}$, we adopt the median value as our modeled solution. For $X_{12/13}$, we instead use the ‘1DMax’ value as the modeled solution.

# Modeling of the CO-to-H2 conversion factor

We calculate the $\alpha_{\mathrm{CO}}$ 1D distribution by summing up all the probabilities of parameters in 5D space that yield a given $\alpha_{\mathrm{CO}}$ value, which is $$\begin{equation}
\begin{split}
P_{\mathrm{biased}}(\alpha_{\mathrm{CO}} | \vec{I}_{\mathrm{obs}}) &= P_{\mathrm{biased}}(\frac{N_{\mathrm{CO}}\Phi_{\mathrm{bf}}} {x_{\mathrm{co}}I^{\mathrm{mod, scaled}}_{\mathrm{CO(1-0)}}}  | \vec{I}_{\mathrm{obs}}) \\
&= \int\limits_{f(\Vec{\theta}) = \alpha_{\mathrm{CO}}} d\Vec{\theta} \ P(\vec{\theta}|\vec{I}_{\mathrm{obs}})
\end{split}
\end{equation}$$ where $f(\Vec{\theta})\equiv \frac{N_{\mathrm{CO}}\Phi_{\mathrm{bf}}} {x_{\mathrm{co}}I^{\mathrm{mod, scaled}}_{\mathrm{CO(1-0)}}}$. However, we need to note that $\alpha_{\mathrm{CO}}$ is not uniformly sampled in our 5D parameter space. To get the unbiased PDF, we calculate the normalized ratio of our biased $\alpha_{\mathrm{CO}}$ probability to the $\alpha_{\mathrm{CO}}$ prior probability in our sampling space, which is $$\begin{equation}
P(\alpha_{\mathrm{CO}} | \vec{I}_{\mathrm{obs}}) = \left[\frac{P_{\mathrm{biased}}(\alpha_{\mathrm{CO}} | \vec{I}_{\mathrm{obs}})}{P_{\mathrm{prior}}(\alpha_{\mathrm{CO}})} \right]_{\mathrm{norm}} 
\end{equation}$$ An example of the 3 $\alpha_{\mathrm{CO}}$ PDFs for one pixel is shown in Fig. [18](#fig:alphaCO_marginalize).

We find that some pixels have extremely small $\alpha_{\mathrm{CO}}$ values. As shown in Fig. [18](#fig:alphaCO_marginalize), $\alpha_{\mathrm{CO}}$ values below 0.1 are not well sampled and the prior distribution has a huge drop below this threshold. Therefore, we exclude the pixels with median $\alpha_{\mathrm{CO}}$ value below 0.1. We also exclude $\alpha_{\mathrm{CO}}$ with large uncertainties ($\alpha_{\mathrm{CO, pos1sig}}/\alpha_{\mathrm{CO, neg1sig}} < 16$, which means uncertainty within a factor of 4). We further exclude pixels with 1dMax values of modeled quantities at the edge of our parameter space. Specifically, we apply the selection criterion to mask out pixels with $X_{\mathrm{12/13, 1dMax}} \leq 30$, $\log n_{\mathrm{H_2, 1dMax}} \geq 4.9$, $\log (N_{\mathrm{CO, 1dMax}} \times \frac{15 \mathrm{km s^{-1}}}{\Delta v}) \leq 16.1$ and $\log (T_{\mathrm{kin, 1dMax}}) < 1.1$. We also exclude pixels with $\chi^2$ value greater than 10.

# $\alpha_{\mathrm{CO}}$ versus $^{13}$CO/CO $J$=2-1 ratio

In Fig. [9](#fig:alphaCO_tau), we find a strong correlation between $\alpha_{\mathrm{CO}}$ and the $^{13}$CO/CO $J$=1-0 ratio, which is consistent with the literature findings in (cite: teng2022; teng2023). However, we see that our $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 1{-}0}}$ relation has a steeper slope than the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ relation found in (cite: teng2022; teng2023). One possible reason for the difference might be due to our different choice of excitation lines. To test this, we also plot the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ for the Antennae in Fig. [19](#fig:alphaCO_R21). We can see that if we include all the data points from Fig. [9](#fig:alphaCO_tau), we have at best a weak correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{^{13}CO/CO 2{-}1}}$. We note that our $^{13}$CO $J$=2-1 observation has a much lower sensitivity than the $^{13}$CO $J$=1-0 observation, which results in a much larger scatter in the observed $R_{\mathrm{^{13}CO/CO 2{-}1}}$. In the left panel of Fig. [19](#fig:alphaCO_R21), we show the S/N distribution for the $^{13}$CO $J$=1-0 and $J$=2-1 data. We can clearly see that most ($\sim$ 90%) of the $^{13}$CO $J$=1-0 data has S/N level greater than 10 while less than half ($\sim$ 30%) of the $^{13}$CO $J$=2-1 data achieve the same S/N level. In our $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ plot color coded by the S/N level, we see most points that cause the scatter have S/N less than 10. If we remove those pixels with S/N smaller than 10, we see a much stronger correlation between $\alpha_{\mathrm{CO}}$ and $R_{\mathrm{^{13}CO/CO 2{-}1}}$ with a Pearson correlation coefficient of 0.7, similar to the coefficient of $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 1{-}0}}$. This suggests that we need $^{13}$CO data with high sensitivity in order to use the $^{13}$CO/CO ratio to calibrate $\alpha_{\mathrm{CO}}$.

We perform the same power-law fit to the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 2{-}1}}$ relation for pixels with S/N$>10$, as shown in the rightmost panel in Fig. [19](#fig:alphaCO_R21). The function is $$\begin{equation}
 \log \alpha_{\mathrm{CO}} = 0.58 (\pm 0.04) \log R_{\mathrm{^{13}CO/CO 2{-}1}} + 0.65 (\pm 0.05)     
\end{equation}$$ We also overlay the $\alpha_{\mathrm{CO}}$ versus $R_{\mathrm{^{13}CO/CO 1{-}0}}$ relation in the same figure panel. We can see that the $^{13}$CO/CO $J$=2-1 ratio gives a shallower slope than the $^{13}$CO/CO $J$=1-0 ratio. It is possible that the shallower slope is due to a larger fraction of $^{13}$CO $J$=2-1 lines being subthermally excited. In the subthermal case, the $^{13}$CO/CO ratio might also track the temperature/volume density variation as the $T_{\mathrm{ex}}$ for the two lines cannot be canceled out (see Eq. [\[eq:R10_tau13\]](#eq:R10_tau13)). Hence, the $^{13}$CO/CO $J$=2-1 ratio might have a less steep dependence on the optical depth, which is tightly correlated with $\alpha_{\mathrm{CO}}$. This could result in a shallower slope for the $\alpha_{\mathrm{CO}}$ versus $^{13}$CO/CO $J$=2-1 relation.

[^1]: https://github.com/ElthaTeng/multiline-bayesian-modeling

[^2]: We also note that, for pixels with low CO intensities, both the CO $J$=2-1/1-0 and $J$=3-2/1-0 ratios increase towards the lower end. This is mainly due to the fact that the CO $J$=1-0 observation is much more sensitive than the CO $J$=2-1 and $J$=3-2 observations (Table [\[tab:line_table\]](#tab:line_table)), and hence the two higher $J$ lines already hit the noise floor.

[^3]: We need to note that our simple derivation assumes both CO and $^{13}$CO $J$=1-0 lines are thermally excited and share the same beam filling factor $\Phi_{\mathrm{bf}}$ and the same linewidth $\Delta v$. In the real case, since CO $J$=1-0 is generally optically thick while $^{13}$CO $J$=1-0 is optically thin, the effective critical density of CO $J$=1-0 is lower than that of $^{13}$CO $J$=1-0 due to the line trapping effects. This will lead to lower beam filling factor and excitation temperature for the $^{13}$CO $J$=1-0 line and hence lower $R_{\mathrm{^{13}CO/CO 1{-}0}}$ value, specifically for lower-density regions (cite: jimenez-donaire_optical_2017). Therefore, we would also expect higher $R_{\mathrm{^{13}CO/CO 1{-}0}}$ in regions with higher gas volume density.

[^4]: We note that we only include pixels with $^{13}$CO line detections for RADEX modeling. Therefore, we would expect these regions to have higher volume densities than those with only CO detections (cite: jimenez-donaire_optical_2017).

</paper>

## Items to check

```json
[
 {
  "path": "claims[3].evidence[0]",
  "value": "Most GMCs in the Antennae are out of virial equilibrium, consistent with merger simulations",
  "failed_quote": "This conclusion in general will increase the $\\alpha_{\\mathrm{CO}}$ of the Antennae"
 }
]
```
