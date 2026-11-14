# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A.191V\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Observing radio transients with Phased ALMA: Pulses from the Galactic Centre magnetar

Radio transients, such as pulsars and fast radio bursts (FRBs), are primarily detected at centimetre (cm) radio wavelengths, where the highest luminosities are found. However, observations of sources in dense environments are heavily affected by propagation effects, such as scattering, which may hinder a detection. Millimetre (mm)-wave observations bypass this complication but require the largest radio telescopes to compensate for the lower flux densities. When used in phased mode, the ALMA radio telescope provides an equivalent dish size of $\sim$84m, making it the most sensitive instrument at mm/sub-mm wavelengths. In combination with its high time resolution, it offers a unique opportunity to study radio transients in an unexplored frequency window. We studied the Galactic Centre (GC) magnetar, PSR J1745-2900, as a laboratory for magnetars in complex magneto-turbulent environments and for linking with FRBs. Through this pilot study, we showcase the potential of ALMA in its phased configuration to observe radio transients and to achieve, for some sources, the first ever detections outside the cm-wave range. We studied the GC magnetar using ALMA archival data of Sgr A\* at Band 3, taken during the 2017 GMVA campaign. The data were searched in intensity, and the pulses were classified based on their circular and linear polarisation properties and arrival phase. We detected eight highly polarised pulses from the GC magnetar with energies in the range of $10^{29}$ erg. We constructed its cumulative energy distribution and we fit a power law, assuming the event rate scales with the energy as $R \propto E^{\gamma}$. The result is an exponent of $\gamma = -2.4 \pm 0.1$, which is consistent with values reported for magnetars at cm-waves and repeating FRBs. With the $\gamma$-value and the system properties of the phased ALMA mode, we estimate that over 160 known pulsars could be detected by ALMA. For repeating FRBs, observing during their peak activity window could lead to detections of several bursts per hour. We expect that ALMA’s lower frequency bands with polarisation capabilities, will serve as a pioneer on mm–wave searches for pulsars and to study complex environments involving radio transients.

# Introduction

A particular type of radio emitting neutron stars (NSs) are magnetars. They are young NSs ($\sim10^{3}$ yr ; (cite: magns)) with extremely strong magnetic fields, of the order of  × 10^14^ G ( cite : magnetars ) Although more than 30 magnetars have been reported ( cite : magnetarcat ) , only a handful exhibit detectable emission at radio frequencies Recently , they have attracted significant attention as promising candidates for the origin of fast radio bursts ( FRBs ; ( cite : circularpol ) , ( cite : magnetoionic ) ) FRBs were first discovered while inspecting archival data of pulsar surveys ( cite : Lorimer ) Since then , over 4000 FRBs have been discovered ( cite : secondchime ) , the majority classified as one - off events and only 5 % as repeaters ( cite : petroff ) These radio transient events , of extragalactic origin , are characterised by their high inferred luminosities (– × 10^15^ G ( cite : magnetars ) Although more than 30 magnetars have been reported ( cite : magnetarcat ) , only a handful exhibit detectable emission at radio frequencies Recently , they have attracted significant attention as promising candidates for the origin of fast radio bursts ( FRBs ; ( cite : circularpol ) , ( cite : magnetoionic ) ) FRBs were first discovered while inspecting archival data of pulsar surveys ( cite : Lorimer ) Since then , over 4000 FRBs have been discovered ( cite : secondchime ) , the majority classified as one - off events and only 5 % as repeaters ( cite : petroff ) These radio transient events , of extragalactic origin , are characterised by their high inferred luminosities ($\rm{\nu L_{\nu} \sim 10^{43}erg\hspace{0.1cm}s^{-1}}$, (cite: locatelli)) and pulses as short as microseconds (cite: snelders). Although there is no widely accepted explanation for the origin of FRBs, one of the strongest pieces of evidence that they could be magnetars at cosmological distances is the detection of two bright radio bursts from the Galactic magnetar SGR 1935+2154. These bursts exceeded the typical isotropic energy of regular radio magnetars by approximately three orders of magnitude (cite: Bochenek; frblike), but are still relatively weak compared to FRBs.

Commonly, the observations of radio transient sources, such as pulsars and FRBs, are performed using large radio telescopes operating at centimetre (cm) wavelengths. This is because these wavelengths yield higher flux densities (cite: machester). Pulsars, for instance, are known to have a steep spectral index around $\alpha$ = -1.6 (cite: spindex). However, some magnetars have flatter or inverted values (e.g., (cite: torne2015; torne2016)). The detectable flux densities are also affected by interstellar effects such as scintillation, scattering and dispersion. The last of these effects introduces a frequency-dependent delay in the arrival of the signal, given by $$\begin{equation}
    \Delta t = \rm{k_{DM}} \times \left(\frac{1}{{\nu_{low}}^{2}} - \frac{1}{{\nu_{high}}^{2}} \right) \times \rm{DM}\hspace{0.2cm},
    \label{eq:dispersion}
\end{equation}$$ where $\rm{k_{DM}} = 1/(2.41 \cdot 10^{-4}) \hspace{0.1cm} pc^{-1}\hspace{0.1cm}cm^{3} MHz^{2}$s, $\rm{\nu_{low}}$ and $\rm{\nu_{high}}$ are the lower and higher frequencies of the observing band, respectively (cite: handbook). DM refers to the dispersion measure, and quantifies the integrated column density of electrons along the line of sight $$\begin{equation}
    \rm{DM} = \int_{0}^{d}\rm{n_{e}}dl\hspace{0.2cm},
\end{equation}$$ where $\rm{n_e}$ is the electron number density and $\rm{d}$ is the column length (distance).

From [Eq. 1](eq:dispersion), by fixing the DM, it is evident that the lower the frequency, the higher the dispersion delay. In particular, for a source with $\rm{DM}$ = 1770 $\rm{pc\hspace{0.1cm}cm^{-3}}$, observing at 1.4 GHz the delay is approximately 1.793 s, while at 42 GHz it is 366 $\mu$s, and at 86 GHz it is 46 $\mu$s (see [Table 1](tab:delay_table)).

| Instrument | $\rm{\nu_{low}}$ (GHz) | $\rm{\nu_{high}}$ (GHz) | $\rm{\nu_{c}}$ (MHz) | $\rm{\Delta \nu}$ (MHz) | $\rm{t_{samp}}$ ($\mu$s) | $\rm{\Delta t}$ ($\mu$s) | samples delay |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Effelsberg (L-band) | 1.210 | 1.510 | 1.360 | 300 | 54.6 | 1793000 | 32845 |
| ALMA (Band 1) | 42.168 | 44.168 | 43.168 | 2000 | 32 | 366 | 11 |
| ALMA (Band 3) | 85.268 | 87.268 | 86.268 | 2000 | 32 | 46 | 1 |

Table notes: We assume a DM = 1770 $\rm{pc\hspace{0.1cm}cm^{-3}}$. $\rm{\nu_{low}}$ and $\rm{\nu_{high}}$ are the lower and higher frequency of the bandwidth ($\rm{\Delta \nu}$). The central frequency of the receiver is $\rm{\nu_{c}}$ and $\rm{t_{samp}}$ is the sample time. For ALMA Band 1, we assume the same sample time as Band 3. At the final column is given the delay in number of samples.

Due to its complex and scattered medium, the vicinity of Sgr A$^{*}$ holds the potential to be used as a laboratory for testing the behaviour of pulsars and magnetars in extreme environments and the ability to link them with FRBs. The DM excess and highly varying rotation measure (RM) of FRBs indicate that they could be born in complex magneto-turbulent environments (cite: platts2019living; mottez2020; wang2022). Similar properties could be found around pulsars and the magnetar near the Galactic Centre (GC, (cite: desvignesgc), (cite: abbate)). For instance, large RMs are expected in the boundaries of massive black holes (cite: bowersgra; magnetoionic). Importantly, given the high plasma densities of regions such as the GC ($\rm{n_{e} \approx 4 \cdot 10^{7} cm^{-3}}$; (cite: witzel)), propagation effects such as the dispersion delay and scattering may hinder a detection at low radio frequencies (cite: torne2023). For scattering, the timescale is inversely proportional to the fourth power of the frequency as $\tau_{s} \approx \nu^{-4}$ (cite: handbook). One way to overcome these two propagation effects and reach the densest regions is to observe at higher frequencies. To compensate for the lower flux densities, the largest possible radio telescopes are required.

The ALMA Phasing System (APS, (cite: matthews2017)) was developed for very long baseline interferometry (VLBI) observations in global campaigns such as the Global Millimetre VLBI Array (GMVA, (cite: data)) and the Event Horizon Telescope (EHT, (cite: eht)). APS is available with an odd number of antennas as a hardware requirement (cite: matthews2017). First it was implemented in Band 6 and Band 3 (cite: goddialmadata) and then at Band 7 (cite: phasing2023) and Band 1. When combining 49 of its 12m antennas, its equivalent dish size is $\approx$ 84m, which makes it the most sensitive instrument at millimetre (mm) to sub-millimetre (sub-mm) wavelengths. Previous observations of known pulsars with phased ALMA have detected sources such as the Vela Pulsar (cite: Liu_2019). Searches for new pulsars have also been conducted in recent years (cite: Liu_2021; torne2023). For FRBs, no observations have been performed with phased ALMA to date.

Based on APS, the Phased ALMA mode (PAM) was introduced in Cycle 8 (2021) to enable observations of weak radio sources (\<50 mJy) in time domain. The phasing of ALMA antennas involves multiple steps (cite: goddialmadata). First, phase corrections align each signal to a reference antenna. Then, the signals of each antenna are coherently summed and the raw voltage data are recorded as 2 bit samples using MARK 6 recorders. When the output is used for pulsar searching, the data are packeted and divided in frequency channels, with a time resolution multiple of 8 $\mu$s (cite: almahand).

For this work we studied the GC magnetar, PSR J1745-2900, using ALMA archival data of Sgr A$^{*}$. This is because the source is located within the same synthesised beam of Sgr A$^{*}$ ($\theta \approx$ 5.7”), due to its 0.07-2 pc projected distance (cite: reapsr). We searched for the magnetar –single pulses to link them to FRB emission. We examined the potential of phased ALMA to open a window to higher frequency observations of radio transients. This paper is organized as follows. In Section [2](#sec:sec2) we describe the observations, and then in Section [3](#sec:sec3) the single pulse search. In Section [4](#sec:sec4) we present the results of the pulses characterisation. In Section [5](#sec:sec5) we discuss the future prospects of using phased ALMA for radio transient observations. Finally, in Section [6](#sec:sec6) we present our final remarks.

# Observations

We used observations of Sgr A\* from the 2017 GMVA campaign at 3.5 mm (Project Code: 2017.1.00795.V, PI: M. Johnson). The observations were carried out on April 3, using 37 12m antennas in Band 3 configuration centred at 86 GHz (cite: Liu_2021). The dataset covered a total of 5.2 hr, with on-source time of 2.5 hr. We used a total of $\sim$2 hr observing time, excluding 30 minutes of unusable data (see [Table 2](tab:table1)). The off-source time corresponds to the calibrations needed between source scans. Some calibrators were 3C 279, NRAO 530 and J1924-2914 (OV-236).

As discussed in (cite: Liu_2021), the data was converted to PSRFITS format (cite: psrfits) with full Stokes information (I,Q,U,V) and 32 frequency channels, each with a 62.5 MHz channel width. The outputs were multiple files corresponding to each scan, with an approximate duration of 52 s. Every 18.192 s there was a drop-off on the time series caused by the phasing cycle of the array. This artefact was previously reported in (cite: Liu_2021). We list the observations in [Table 2](tab:obs).

|  Scan  |  Start time (UTC)   |   End time (UTC)    |
|:------:|:-------------------:|:-------------------:|
| No0133 | 2017-04-03 07:46:05 | 2017-04-03 07:53:05 |
| No0134 | 2017-04-03 07:55:05 | 2017-04-03 08:02:05 |
| No0142 | 2017-04-03 08:16:13 | 2017-04-03 08:23:13 |
| No0143 | 2017-04-03 08:25:13 | 2017-04-03 08:32:13 |
| No0152 | 2017-04-03 08:46:22 | 2017-04-03 08:53:22 |
| No0153 | 2017-04-03 08:55:22 | 2017-04-03 09:02:22 |
| No0217 | 2017-04-03 12:17:08 | 2017-04-03 12:24:08 |
| No0220 | 2017-04-03 12:26:08 | 2017-04-03 12:33:08 |
| No0227 | 2017-04-03 12:47:05 | 2017-04-03 12:54:05 |
| No0230 | 2017-04-03 12:56:05 | 2017-04-03 13:03:05 |
| No0237 | 2017-04-03 13:17:01 | 2017-04-03 13:24:01 |
| No0240 | 2017-04-03 13:26:01 | 2017-04-03 13:33:01 |
| No0242 | 2017-04-03 13:38:31 | 2017-04-03 13:45:31 |
| No0243 | 2017-04-03 13:47:01 | 2017-04-03 13:54:01 |
| No0250 | 2017-04-03 14:12:01 | 2017-04-03 14:19:01 |
| No0252 | 2017-04-03 14:24:31 | 2017-04-03 14:31:31 |
| No0253 | 2017-04-03 14:33:01 | 2017-04-03 14:40:01 |

: Observations of Sgr A$^{*}$ used in this work, taken during the 2017 GMVA campaign.

Table notes: The data is centered at 86.268 GHz with 2 GHz of bandwidth. Each scan consists of multiple PSRFITS files containing full Stokes information.

# Methods and data processing

We searched for single pulses using a PRESTO-based pipeline (cite: presto), detailed in (cite: Braga2024) with some modifications to account for PSRFITS containing Stokes. We used a signal-to-noise ratio (S/N) threshold of 6, determined through analysis of the noise floor of the time series on pulse-free regions. These time series were constructed by summing all the frequency channels of the PSRFITS files on Stokes I. Given the high DM of the source and the high observing frequency at Band 3, the dispersion delay between the highest and the lowest frequency channel is 46 $\mu$s (see [Table 1](tab:delay_table)). Therefore, DM trials were unnecessary, and we adopted the reported value of the source, 1770 $\rm{pc \hspace{0.1cm}cm^{-3}}$ (cite: Liu_2021). Using this value we searched for single pulses in Stokes I. We inspected each candidate visually. To this end, we constructed the time series in intensity, linear and circular polarisation.

Importantly, due to the negligible dispersion delay, we relied primarily on polarisation to confirm the pulse candidates. We complemented these data with a second test –in which we used the spin period of the magnetar to assign a phase to the arrival time of each pulse. This arrival phase was compared with the region where the pulse is expected to arrive. This region was determined from the full width of the integrated pulse profile. We used this method as most single pulses are significantly narrower than their integrated pulse, which is built up from adding up thousands of pulses (cite: drakepulses). Nevertheless, in some cases magnetars also show single pulses outside the main profile (cite: camiloxte).

According to our criteria, if a pulse candidate has significant linear and circularly polarised flux and it arrives in phase with the integrated pulse profile of PSR J1745$-$2900, then it is considered a real pulse. It is worth noting that pulses with small polarisation fractions would have not been detected by our pipelines.

# Results

We report eight single pulses from the GC magnetar, PSR J1745-2900, which are shown in [Fig. 1](fig:pulses). The bottom panel shows the dynamic spectra across all 32 frequency channels. The top panel displays the integration along the bandwidth, we also refer to this as the single pulse profile. We performed this integration using Stokes I. The pulses, together with their linearly and circularly polarized flux, are shown with respect to their arrival phase in [Fig. 2](fig:pulses_phase). We calculated the time of arrival (TOA) of each reported pulse. In our search we found the three pulses reported by (cite: Liu_2021) plus five new pulses.

Using all data blocks from [Table 2](tab:table1), we created integrated pulse profiles per scan. From those with the highest S/N, we obtained TOAs that we input to TEMPO (cite: tempo), following standard timing procedures. This step was necessary as the ephemeris listed in the ATNF catalogue (cite: catalogue) was not sufficient to fully recover the signal of the magnetar. Through residual minimisation, with the spin period as the only free parameter, we generated a new ephemeris file shown in [Table 3](tab:timing4).

|                                                      | PSR J1745$-$2900  |
|:-----------------------------------------------------|:------------------|
| Right ascension, $\alpha$ (J2000)                    | 17:45:40.1662(8)  |
| Declination, $\delta$ (J2000)                        | $-$29:00:29.89(1) |
| Spin frequency, $F$ ($\text{s}^{-1}$)                | 0.26762(8)        |
| Dispersion measure, DM ($\text{cm}^{-3}\,\text{pc}$) | 1770(3)           |
| Reference Epoch, PEPOCH                              | 57846.349663      |

: Ephemeris File.

Table notes: The DM uncertainty was taken from the ATNF catalogue (cite: catalogue).

![](figures/family_plot.png)

![](figures/phase_pulses_alma.png)

## Pulse characterisation

In [Table 4](tab:pulses_table) we report the pulse properties. We report the modified Julian day (MJD), S/N, full width at half maximum (FWHM), flux density, fluence [^2] and isotropic energy. As shown in [Fig. 1](fig:new_pulses), most of the pulses from the GC magnetar have more than one component. We computed the S/N by normalising the time series using a pulse-free region and taking the pulse peak. To estimate the pulse width, we used a multi-Gaussian fitting routine developed for single pulse analysis (Limaye et al. in prep.). Then, the fluence $\rm{F}$ is obtained as $$\begin{equation}
    F = \frac{\mathrm{S/N} \times \mathrm{SEFD}}{\sqrt{n_{\mathrm{pol}} \times n_{\mathrm{sp}} \times \Delta \nu}} \sqrt{\mathrm{FWHM}} \hspace{0.2cm},
    \label{eq:radiometer}
\end{equation}$$ where $\rm{n_{pol}}$ is the number of polarisations, $\rm{n_{sp}}$ the number of spectral windows and $\Delta \nu$ the bandwidth of each spectral window. The system equivalent flux density (SEFD) is a parameter given for each telescope as $$\begin{equation}
    \rm{SEFD = \frac{2 k_{b} \times T_{sys}}{A_{eff}}= \frac{T_{sys}}{G}}\hspace{0.2cm},
\end{equation}$$ where $\rm{k_b}$ is the Boltzmann constant, $\rm{T_{sys}}$ is the system temperature, G is the system gain of phased ALMA (51 K and 1.15 K/Jy respectively on (cite: Liu_2021)), and $\rm{A_{eff}}$ is the effective area. Then, the isotropic energy is given by $$\begin{equation}
    \rm{E = F \times \Delta \nu \times 4 \pi D^{2} \times 10^{-23}}\hspace{0.2cm} (erg),
    \label{eq:energy}
\end{equation}$$ where D corresponds to the source luminosity distance, equal to 8.3 kpc (cite: yim). As listed in [Table 4](tab:pulses_table), the energy of the pulses is of the order of $10^{29}$ erg.

| Candidate | S/N | MJD (bary) | FWHM (s) | Flux density (Jy) | Fluence (Jy ms) | Energy (10$^{29}$ erg) |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 1 | 11.0 | 57846.3495 | 0.11 | 0.023 | 2.589 | 4.27 |
| 2 | 6.6 | 57846.5413 | 0.13 | 0.013 | 1.660 | 2.74 |
| 3 | 15.6 | 57846.5730 | 0.04 | 0.058 | 2.068 | 3.41 |
| 4 | 22.2 | 57846.5422 | 0.04 | 0.074 | 3.284 | 5.41 |
| 5 | 7.5 | 57846.3478 | 0.08 | 0.018 | 1.499 | 2.47 |
| 6 | 10.7 | 57846.3493 | 0.04 | 0.036 | 1.556 | 2.57 |
| 7 | 8.9 | 57846.5412 | 0.10 | 0.020 | 1.956 | 3.23 |
| 8 | 14.7 | 57846.3767 | 0.01 | 0.127 | 0.837 | 1.38 |

Table notes: The S/N was obtained from the pulse profile using a downsampling factor of 128. The FWHM was obtained from a multi-Gaussian fitting, where the width is defined from the S/N peak to the point where the value drops to 50$\%$. Whenever the pulse was fitted with multiple Gaussians, the outermost components were considered for the S/N drop. The flux density and fluence were obtained considering all the 2 GHz bandwidth of the observation.

## Energy distribution

We constructed the cumulative energy distribution by sorting the events and then counting the number above an energy threshold, until all the pulses were contained. We included only events above the completeness limit [^3], which is $\sim$1120 mJy ms using a $T_{sys} =$ 51 K and $G$ = 1.15 K Jy$^{-1}$ (cite: Liu_2021) and considering the pulse width as the mean FWHM of our pulses, $\approx$ 0.07 s. We fit a power law to the cumulative energy distribution using a least-squares minimisation considering that the event rate scales with the energy as $R \propto E^{\gamma}$. The result is a power-law exponent of $\gamma = -2.4 \pm  0.1$.

![](figures/energy_dist.png)

# Discussion

Our sample adds five pulses in addition the three previously reported by (cite: Liu_2021), mainly due to the difference in the candidate selection criteria. In our work, we defined the S/N threshold as 6, based on a statistical analysis of the noise floor. For each of these candidates the four Stokes parameters plus the linear and circular polarisation were inspected. Polarisation information was crucial as the dispersion delay between the frequency channels was negligible at ALMA Band 3 frequencies.

Among the pulses, five of them (P1, P2, P3, P5, and P8) exhibit nearly 100$\%$ of the linearly polarised flux, while the remaining three (P4, P6, and P7) have values close to 50$\%$. In addition, for the majority of them there is a degree of circular polarisation of approximately 30$\%$. Regarding the pulse morphology, as seen in [Fig. 1](fig:new_pulses), most of the pulses have at least two components, which vary in relative intensity. All pulses show emission across the entire 2 GHz bandwidth. Broadband emission is one of the features of radio pulsars (cite: handbook).

This is the first time the energy properties of the pulses from the GC magnetar have been explored at high frequencies. Previous studies were conducted at 3.1 GHz (cite: yan) and 8.6 GHz (cite: yan2015). Common fits to the energy distribution of single pulses are log-normal and power-law distributions. For the power-law method, which is the one used in our study, the defining parameter is $\gamma$, the power-law exponent such that $R \propto E^\gamma$, with $R$ the rate of events above a given energy value $E$. This definition corresponds to the cumulative energy distribution, which is broadly used in cases where the number of pulses is limited, such as the case of FRBs.

As shown in [Fig. 3](fig:energies), our sample is well fit by $\gamma$ = -2.4 $\pm$ 0.1. For the same source, at cm-wavelengths, the energy distribution of single pulses was found to be well fit by a log-normal distribution with $\mu$ = 1.34 and $\sigma$ = 0.57 at 3.1 GHz (cite: yan2015), and $\mu$ = 0.72 and $\sigma$ = 0.22 at 8.6 GHz (cite: yan). The difference with our result was expected given the sample size, where the authors considered 1900+ and 2300+ pulses, respectively. However, it is known that pulsars show a bimodal behaviour: their regular emission is well modelled with a log-normal distribution (cite: Burke-Spolaor2012), while giant pulses are modelled by a power-law distribution (cite: Ramesh2010). In the case of the GC magnetar, previous studies on the single pulse peak flux densities of giant pulses at 8.4 GHz, found that they are not well fit by a log-normal distribution (cite: Pearlman_2018). Given the steep spectral index in pulsars, the observable events at millimetre wavelengths could correspond to the most energetic pulses. Alternatively, a power-law relation for the cumulative energy distribution would be the result of the limited energy range of our pulses. Extending the observations with on-source time and frequency coverage will increase the sample and will provide us with a better general picture of the behaviour of PSR 1745-2900.

Our $\gamma=-2.4\pm0.1$ is consistent with the energy distributions of other magnetar at cm-wavelengths. For XTE J1810$-$197 (PSR J1809$-$1943) giant pulses, values between -2.1 and -7.68 at 1.4 GHz, between -1.78 and -2.86 at 4.9 GHz, and between -0.89 and -1.89 at 8.35 GHz have been reported. The differences could be attributed to its intrinsic magnetar variability and the observations at different frequencies (see Table 2 in (cite: xte)).

Importantly, our results fill a critical gap by characterising magnetar radio emission across a scarcely explored frequency window, offering valuable insights into potential changes in their emission mechanisms. Magnetar radio emission–known to be coherent at cm-wavelengths–persists into the mm-band, as demonstrated by our work, by (cite: Liu_2021), and by (cite: torne2016). However, it remains unclear exactly where a transition to an incoherent emission occurs. This transition is expected to take place in the mm to sub‑mm range; however, there are currently very few observational facilities equipped for time-domain astronomy at such frequencies. In this context, and given its sensitivity, PAM holds significant potential.

![](figures/skyplot.png)

## Comparison with FRBs

In regard to FRBs, there are three sources with seemingly periodic activity windows: FRB 20121102A with a periodicity of 159.3 days (cite: Braga2024), FRB 20180916B with 16.35 days (cite: chime_periodic), and the recently reported FRB 20240209A with 126 days (cite: newperiodic). The periodicity corresponds to the cycle of the alternating on-and-off activity. Naturally, observations carried out at their peak activity are more likely to result in a detection. FRB 20121102A has $\gamma-$values between $-1.1\pm0.1$ (cite: papermary) and $-1.8\pm0.3$ (cite: Gourdji_2019). However, (cite: li2) used a large sample of 1600+ bursts detected by the Five-hundred-metre Aperture Spherical Telescope (FAST), and showed that the energy distribution is bimodal and best fit by a combination of a log-normal and a Cauchy function. In that work, the analysis was done over the histogram of the differential energy distribution rather than the cumulative distribution, given the large sample of bursts available. In (cite: li2), when analysing the high-energy component, it was found that the sub-sample is well fit by a power law with $\gamma=-1.37\pm0.18$. It is important to note that in our work we reported a limited sample of eight pulses. With a larger sample size (hundreds of pulses) the differential energy distribution could also be fit.

For another active repeater, FRB 20201124A, $\gamma$-values of -1.5 $\pm$ 0.1 (in (cite: xu)) and from -1.95 $\pm$ 0.01 to -2.25 $\pm$ 0.02 (in (cite: kristen)) have been reported, both at cm-wavelengths. A steeper value of $\gamma$ is often seen at higher energies in repeating FRBs (cite: kristen), reaching values as steep as $\gamma=-4.9$ in the high-energy tail (cite: kumar). Recent studies of the FRB energy distribution have reported a value of -1.96 $\pm$ 0.15 for the pure power law (cite: frb_energy) using FRB data between 0.83 and 1.6 GHz.

The typical isotropic energies of FRBs are in the range of $10^{36}-10^{41}$ erg (cite: chimemag). Comparing the energy of our pulses, we find a gap of at least seven orders of magnitude. Nevertheless, the hypothesis of FRBs being extragalactic magnetars (cite: frbarxiv) is supported by the activity of the Galactic magnetar SGR 1935+2154, which emitted bursts with energies in the range of 10$^{34}$ (cite: margalit; Bochenek). This values are closer to those seen for FRBs, but still at least two orders of magnitude below. There are some phenomena that could explain the energy gap. One is multiple magnifications of the pulses due to plasma lensing, especially in environments where magnetars are orbiting a compact source such as a massive black hole (cite: Pen_2015; Pearlman_2018). In this regard, a promising laboratory to test this scenario is the GC. While for most radio pulsars and FRBs the monitoring is done at lower frequency bands, complex regions such as the GC are hard to reach with cm-waves as the pulses are heavily affected by propagation effects such as scattering and dispersion. Therefore higher frequencies allow us to probe deeper into these complex regions. The natural disadvantage is the lower luminosities expected at higher frequencies. Our study is especially remarkable given the detection of several single pulses from the GC magnetar at 86 GHz, which allow us to characterise the source, explore the potential of ALMA for radio transients and also to establish a direct link to what we could expect for FRBs at higher frequencies, if they are indeed originated by magnetars.

Although most pulsars display a steep spectral index, magnetars such as PSR 1745-2900, have a flat or inverted one (cite: torne2016; Pearlman_2018). Their spectral index could also change in time (see e.g. (cite: champion)). (cite: torne2015) reports a value of $\alpha=-0.4 \pm 0.1$ for the GC magnetar, which changes to $\alpha=0.4\pm 0.2$ in a different epoch (cite: torne2016). This positive value could reflect a turn up, related with the transition from coherent to incoherent radio emission. Observing with high-sensitivity instruments such as ALMA could be helpful to study the gap between centimetre and millimetre radio wavelengths, particularly with its new Band 1 set-up.

## PAM Band 1 predictions

Based on our detections, we report a Poissonian rate of $\rm{R_{Band\hspace{1mm}3}}$ = 4 per hour (events/hr) for PSR J1745-2900 at ALMA Band 3. We can estimate the expected rate at Band 1 (42 GHz) using $$\begin{equation}
    \rm{R_{Band\hspace{1mm}1} = R_{Band\hspace{1mm}3}\left(\frac{F_{Band\hspace{1mm}1}}{F_{Band\hspace{1mm}3}}\right)^{\gamma}},
\end{equation}$$ where $\rm{R_{Band-X}}$ corresponds to the expected event rate for a given fluence threshold at Band X. The fluence completeness limit using 37 antennas of 12m at Band 3 is $\rm{F_{Band\hspace{1mm}3}}$ = 1330 mJy ms and at Band 1 $\rm{F_{Band\hspace{1mm}1}}$ = 1200 mJy ms, considering a pulse width of 0.1 s. The exponent $\gamma$ is the power-law value derived from the cumulative energy distribution discussed in Sect. [4.2](#sec:energy_dist). We obtain a rate of $\rm{R_{Band\hspace{1mm}1}} = 5 \pm 2$ events/hr. However, if we instead consider a total of 49 antennas for the phasing, then the expected rate rises to $\rm{R_{Band\hspace{1mm}1}} = 10 \pm 3$ events/hr, as the fluence threshold drops to $\rm{F_{Band\hspace{1mm}1}}$ = 900 mJy ms. Certainly, having a larger sample of pulses will provide more constraining values for their energy and frequency behaviour. In particular, measuring the spectral index of the source at different frequencies will tell us whether there is a turn-up point when we transition to incoherent emission mechanisms.

### FRBs

If we consider the $\gamma = -2.4\pm0.1$ obtained for the GC magnetar and apply it to some actively repeating FRBs, we can estimate the event rates at ALMA bands. In this case, we re-calculated the fluence threshold for ALMA assuming bursts of 1 ms duration (typical for FRBs), and obtain $\rm{F_{Band-1}}$ = 90 mJy ms [^4]. We take FRB 20121102A, whose reported rates at L-band are 122 events/hr (cite: li2; li) and 218$\pm$16 events/hr (cite: NovRain). This leads to a rate between 1 $\pm$ 1 and 3 $\pm$ 2 events/hr, respectively. If on the contrary, we take the flatter value of $\gamma=-1.1$ reported for FRB 20121102A at L-band in (cite: papermary), we estimate instead between 10 $\pm$ 3 and 32 $\pm$ 6 events/hr. It is noteworthy that these rates consider observations at the peak activity of the source.

We highlight that PAM Band 1 could serve as a bridge to millimetre wavelengths, which would have profound implications in constraining the FRBs’ progenitor source. If detections are achieved, it will also be key to test the proposed frequency dependence of the activity window (chromaticity) of periodic FRBs. As discussed in (cite: surya), the activity window seems to starts earlier and be narrower at higher frequencies. As shown in [Fig. 4](fig:skyplot), currently ALMA could potentially detect 19 repeating FRBs. This number is expected to increase rapidly given the new surveying instruments in the southern hemisphere such as MeerKAT (cite: meerkat).

### Pulsars

![](figures/sens_band1.png)

We can also estimate the number of radio pulsars detectable in integrated pulse profile mode (also known as folding mode), which is obtained by adding hundreds to thousands of pulses using the spin period and other parameters listed in their ephemeris (see e.g. [Table 3](tab:timing4)). We derived the minimum sensitivity for Band 3 using the radiometer equation for pulsars and considering telescope parameters such as $T_{sys}$ = 74 K, $G$ = 1.08 K/Jy (cite: almahand) for Band 3, a phasing efficiency of $\eta_{p} \sim 0.6$ (cite: matthews2017), a minimum detected S/N of 6 and 1 hour of on-source integration time. For a pulsar spin period of 1 s with a duty cycle of 10%, we estimate that the Band 3 system is sensitive to 0.060 mJy. If instead we use the parameters reported by (cite: Liu_2021), we obtain 0.023 mJy. Assuming that the Band 1 system behaves similarly ($T_{sys}$ = 45 K, $G$ = 1.12 K/Jy in (cite: almahand)), then we expect a minimum detectable flux of 0.035 mJy, using the same 37-antenna set-up. When increasing to 49 antennas, the minimum flux is 0.026 mJy.

In [Fig. 5](fig:band1_pulsars) we show the sources expected to be detectable by PAM Band 1. To this end, we selected all the known pulsars from the ATNF catalogue (cite: catalogue) having flux density reported at 1.4 GHz or 2 GHz. We limited the sources detectable by ALMA based on a declination below 47° (cite: almahand). This reduced the list to 2301 pulsars.

We used the spectral index to estimate the flux of each source at 42 GHz (Band 1). To extrapolate we used a simple power-law:

$$\begin{equation}
\label{eq:fluxeq}
    \rm{S_{42\hspace{0.6mm}GHz} = S_{1.4-2 \hspace{0.6mm}GHz}\left(\frac{\nu_{42\hspace{0.6mm}GHz}}{\nu_{1.4-2\hspace{0.6mm}GHz}}\right)^{\alpha}}.
\end{equation}$$ Here $\rm{S_{X}}$ corresponds to the flux at a given frequency in GHz, $\rm{\alpha}$ is the spectral index, and $\rm{\nu_{X}}$ is the frequency. For the sources that do not have a reported spectral index, we draw a spectral index from a normal distribution, considering a mean of -1.6 and standard deviation equal to 0.54 (cite: index). We assumed a pulse width equal to 10$\%$ of the period and considered on-source integration times of 1, 1.5, and 2.5 hours. This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively. The sources detectable by PAM are the ones lying above the mentioned sensitivity lines in [Fig. 5](fig:band1_pulsars). Some remarkable detectable sources have been highlighted, such as the Vela pulsar, and three radio-loud magnetars, including PSR J1745$-$2900. It is important to mention that these surveys are unlikely to be sensitive to millisecond pulsars (MSPs, (cite: Liu_2021)).

# Conclusions

We reprocessed archival data of APS at Band 3 from Sgr A$^{*}$. We detected eight pulses from the GC magnetar PSR J1745$-$2900 and studied their cumulative energy distribution with the objective to link this with FRBs. The complex environment where the GC magnetar is located serves us to test promising progenitor scenarios for FRBs, given its high electron density and turbulent magneto ionic properties.

We obtained an exponent of $\gamma$ = 2.4 $\pm$ 0.1 for the cumulative energy distribution of the GC magnetar. Using this exponent we predict a rate of 5 events/hr if we were to observe in Band 1, using 37 antennas of 12m. This rate increases to 10 events/hr with 49 12m antennas. For the periodic FRB 20121102A, at peak activity, we obtained a rate between 1 and 32 events/hr with PAM Band 1 using 49 12m antennas. Regarding pulsar detection, we estimated that there are roughly 166 pulsars potentially detectable within 1 hr integration. This number increases with more integration time.

Currently, there are 19 repeating FRBs that are visible to ALMA. Given its high sensitivity and time resolution, instruments like PAM are crucial to exploring the FRB frequency extent to test their progenitor scenarios. Importantly, high-frequency searches are not affected by propagation effects, such as scattering, which could hinder a detection at cm-wavelengths. It is expected that the Band 1 receiver, including polarisation capabilities, will serve as a pioneer on mm-wavelengths searches for pulsars and to study complex environments involving radio transients. To cover the northern sky, telescopes such as the IRAM 30m or the NOEMA observatory could be used and, in the future, the ngVLA.

# Acknowledgements

A significant part of this work was developed during the NRAO REU Chile Internship, conducted at the Joint ALMA Observatory from January to March 2024. We extend our gratitude to AUI/NRAO Chile, D. Rebolledo and P. Cortés for their support. J.V-C gives special thanks to J.C. Fluxá for his support during the NRAO REU Chile Internship application, which ultimately led to this article. We also thank Prof. T. Cassanelli for his valuable feedback. This work made use of archival data from GMVA 2017 campaign with ALMA (Project Code: 2017.1.00795.V). We extend our gratitude to the P.I. M. Johnson and the team. This work is funded by the Max Planck Society through the Max Planck Partner Group led by Prof. M. Cruces. This work is funded by the Chinese Academy of Sciences President’s International Fellowship Initiative. Grant No. 2026PVC0050).

67 natexlab

(ref: abbate) Abbate, F., Noutsos, A., Desvignes, G., et al. 2023, MNRAS, 524, 2966–2977

(ref: eht) Akiyama, K., Alberdi, A., Alef, W., et al. 2019, ApJL, 875, L2

(ref: frb_energy) Arcus, W. R., James, C., Ekers, R., et al. 2025, PASA, 42, e003

(ref: surya) Bethapudi, S., Spitler, L. G., Main, R. A., Li, D. Z., & Wharton, R. S. 2023, MNRAS, 524, 3303

(ref: Bochenek) Bochenek, C. D., Ravi, V., Belov, K. V., et al. 2020, Nature, 587, 59

(ref: bowersgra) Bower, G. C., Wright, M. C. H., Falcke, H., & Backer, D. C. 2003, ApJ, 588, 331

(ref: Braga2024) Braga, C. A., Cruces, M., Cassanelli, T., et al. 2025, A&A, 693, A40

(ref: Burke-Spolaor2012) Burke-Spolaor, S., Johnston, S., Bailes, M., et al. 2012, MNRAS, 423, 1351

(ref: camiloxte) Camilo, F., Ransom, S. M., Peñalver, J., et al. 2007, ApJ, 669, 561

(ref: champion) Champion, D., Cognard, I., Cruces, M., et al. 2020, MNRAS, 498, 6044

(ref: chime_periodic) Chime/Frb Collaboration, Amiri, M., Andersen, B. C., et al. 2020, Nature, 582, 351

(ref: chimemag) CHIME/FRB Collaboration, Andersen, B. C., Bandura, K. M., et al. 2020, Nature, 587, 54

(ref: almahand) Cortes, P. C., Vlahakis, C., Hales, A., et al. 2024, ALMA Technical Handbook, Vol. 11.3

(ref: phasing2023) Crew, G. B., Goddi, C., Matthews, L. D., et al. 2023, PASP, 135, 025002

(ref: papermary) Cruces, M., Spitler, L. G., Scholz, P., et al. 2021, MNRAS, 500, 448

(ref: desvignesgc) Desvignes, G., Eatough, R. P., Pen, U. L., et al. 2018, ApJL, 852, L12

(ref: drakepulses) Drake, F. D. & Craft, H. D. 1968, Nature, 220, 231

(ref: magnetars) Duncan, R. C. & Thompson, C. 1992, ApJL, 392, L9

(ref: goddialmadata) Goddi, C., Crew, G., Impellizzeri, V., et al. 2019, The Messenger, 177, 25

(ref: Gourdji_2019) Gourdji, K., Michilli, D., Spitler, L. G., et al. 2019, ApJL, 877, L19

(ref: psrfits) Hotan, A. W., van Straten, W., & Manchester, R. N. 2004, PASA, 21, 302

(ref: NovRain) Jahns, J. N., Spitler, L. G., Nimmo, K., et al. 2023, MNRAS, 519, 666

(ref: spindex) Jankowski, F., van Straten, W., Keane, E. F., et al. 2017a, MNRAS, 473, 4436

(ref: index) Jankowski, F., van Straten, W., Keane, E. F., et al. 2017b, MNRAS, 473, 4436

(ref: meerkat) Jonas, J. & MeerKAT Team. 2016, in MeerKAT Science: On the Pathway to the SKA, 1

(ref: Ramesh2010) Karuppusamy, R., Stappers, B. W., & van Straten, W. 2010, A&A, 515, A36

(ref: kristen) Kirsten, F., Ould-Boukattine, O. S., Herrmann, W., et al. 2024, Nat. Astron., 8, 337

(ref: frblike) Kirsten, F., Snelders, M., Jenkins, M., et al. 2021, Nat. Astron., 5, 414

(ref: magns) Kouveliotou, C. 1999, PNAS, 96, 5351

(ref: kumar) Kumar, P., Luo, R., Price, D. C., et al. 2023, MNRAS, 526, 3652

(ref: li2) Li, D., Wang, P., Zhu, W. W., et al. 2021, Nature, 598, 267

(ref: li) Li, Q.-C., Yang, Y.-P., Wang, F. Y., Xu, K., & Dai, Z.-G. 2022, MNRAS, 517, 4612

(ref: Liu_2021) Liu, K., Desvignes, G., Eatough, R. P., et al. 2021, ApJ, 914, 30

(ref: Liu_2019) Liu, K., Young, A., Wharton, R., et al. 2019, ApJL, 885, L10

(ref: locatelli) Locatelli, N., Ronchi, M., Ghirlanda, G., & Ghisellini, G. 2019, A&A, 625, A109

(ref: Lorimer) Lorimer, D. R., Bailes, M., McLaughlin, M. A., Narkevic, D. J., & Crawford, F. 2007, Science, 318, 777

(ref: handbook) Lorimer, D. R. & Kramer, M. 2004, Handbook of Pulsar Astronomy, Vol. 4

(ref: catalogue) Manchester, R. N., Hobbs, G. B., Teoh, A., & Hobbs, M. 2005, ApJ, 129, 1993

(ref: machester) Manchester, R. N. & Taylor, J. H. 1977, Pulsars

(ref: margalit) Margalit, B., Berger, E., & Metzger, B. D. 2019, ApJ, 886, 110

(ref: circularpol) Masui, K., Lin, H.-H., Sievers, J., et al. 2015, Nature, 528, 523

(ref: matthews2017) Matthews, L. D., Crew, G. B., Doeleman, S. S., et al. 2018, PASP, 130, 015002

(ref: magnetoionic) Michilli, D., Seymour, A., Hessels, J. W. T., et al. 2018, Nature, 553, 182

(ref: mottez2020) Mottez, F., Zarka, P., & Voisin, G. 2020, A&A, 644, A145

(ref: tempo) Nice, D., Demorest, P., Stairs, I., et al. 2015, Tempo: Pulsar timing data analysis, ASCL, record ascl:1509.002

(ref: magnetarcat) Olausen, S. A. & Kaspi, V. M. 2014, ApJS, 212, 6

(ref: newperiodic) Pal, A. 2025, ApJL, accepted, arXiv:2502.11215

(ref: Pearlman_2018) Pearlman, A. B., Majid, W. A., Prince, T. A., Kocz, J., & Horiuchi, S. 2018, ApJ, 866, 160

(ref: Pen_2015) Pen, U.-L. & Connor, L. 2015, ApJ, 807, 179

(ref: petroff) Petroff, E., Hessels, J. W. T., & Lorimer, D. R. 2022, A&ARv, 30, 2

(ref: platts2019living) Platts, E., Weltman, A., Walters, A., et al. 2019, Physics Reports, 821, 1

(ref: presto) Ransom, S. 2011, PRESTO: PulsaR Exploration and Search TOolkit, ASCL, record ascl:1107.017

(ref: reapsr) Rea, N., Esposito, P., Pons, J. A., et al. 2013, ApJL, 775, L34

(ref: data) Ros, E., Krichbaum, T. P., Lobanov, A. P., et al. 2024, in Proceedings of the 16th EVN Symposium, ed. E. Ros, P. Benke, S. A. Dzib, I. Rottmann, & J. A. Zensus, 159–168

(ref: xte) Serylak, M., Stappers, B., Weltevrede, P., et al. 2009, MNRAS, 394, 295

(ref: secondchime) Siegel, S. & Fonseca, E. 2025, in AAS Meeting Abstracts, Vol. 246, American Astronomical Society Meeting Abstracts, 317.03

(ref: snelders) Snelders, M. P., Nimmo, K., Hessels, J. W. T., et al. 2023, Nat. Astron., 7, 1486

(ref: frbarxiv) Sobacchi, E., Iwamoto, M., Sironi, L., & Piran, T. 2024, A&A, 690, A332

(ref: torne2016) Torne, P., Desvignes, G., Eatough, R. P., et al. 2017, MNRAS, 465, 242

(ref: torne2015) Torne, P., Eatough, R. P., Karuppusamy, R., et al. 2015, MNRAS, 451, L50

(ref: torne2023) Torne, P., Liu, K., Eatough, R. P., et al. 2023, ApJ, 959, 14

(ref: wang2022) Wang, F., Zhang, G., Dai, Z., & Cheng, K. 2022, Nat. Commun., 13, 4382

(ref: witzel) Witzel, G., Martinez, G., Willner, S., et al. 2021, ApJ, 917, 73

(ref: xu) Xu, H., Niu, J. R., Chen, P., et al. 2022, Nature, 609, 685

(ref: yan) Yan, W. M., Wang, N., Manchester, R. N., Wen, Z. G., & Yuan, J. P. 2018, MNRAS, 476, 3677

(ref: yan2015) Yan, Z., Shen, Z.-Q., Wu, X.-J., et al. 2015, ApJ, 814, 5

(ref: yim) Yao, J. M., Manchester, R. N., & Wang, N. 2017, ApJ, 835, 29

[^1]: Email: josefina.vera@alumni.uc.cl

[^2]: Corresponding to the band-averaged peak flux density.

[^3]: This is the energy limit of a burst having the minimum detectable fluence given a telescope sensitivity.

[^4]: Using a maximum of 49 antennas of the same 12m size.

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Created integrated pulse profiles per scan, extracted TOAs from scans with highest S/N, and performed timing residual minimisation in TEMPO with spin period as the only free parameter",
  "failed_quote": "Using all data blocks from Table 2, we created integrated pulse profiles per scan. From those with the highest S/N, we obtained TOAs that we input to TEMPO (cite: tempo), following standard timing procedures."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Dispersion delay across the 2 GHz band at 86 GHz is negligible (46 microseconds, 1 sample)",
  "failed_quote": "Given the high DM of the source and the high observing frequency at Band 3, the dispersion delay between the highest and the lowest frequency channel is 46 $\\mu$s (see Table 1)."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "Most of the detected pulses from PSR J1745-2900 have at least two components and show broadband emission across the entire 2 GHz bandwidth at Band 3.",
  "failed_quote": "Regarding the pulse morphology, as seen in Fig. 1, most of the pulses have at least two components, which vary in relative intensity. All pulses show emission across the entire 2 GHz bandwidth."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Performing dispersion measure (DM) trials was rejected as unnecessary because the dispersion delay across the band at 86 GHz is only 46 microseconds (1 sample).",
  "failed_quote": "Given the high DM of the source and the high observing frequency at Band 3, the dispersion delay between the highest and the lowest frequency channel is 46 $\\mu$s (see Table 1). Therefore, DM trials were unnecessary, and we adopted the reported value of the source, 1770 $\\rm{pc \\hspace{0.1cm}cm^{-3}}$ (cite: Liu_2021)."
 }
]
```
