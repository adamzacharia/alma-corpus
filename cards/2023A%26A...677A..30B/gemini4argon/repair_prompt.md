# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...677A..30B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Matter ejections behind the highs and lows of the transitional millisecond pulsar

# Introduction

The evolutionary path that leads a neutron star (NS) in a low-mass X-ray binary (XRB) system to become a millisecond radio pulsar involves different stages, the most enigmatic of which is represented by transitional millisecond pulsars (tMSPs). These sources alternate between a radio pulsar state and an active low-luminosity X-ray disc state on timescales from weeks to months (for reviews, see (cite: campana18b; papitto22)). The archetypal tMSP is PSR J1023$+$0038 (hereafter referred to as J1023), which was discovered in 2007 as a 1.69 ms radio pulsar orbiting a low-mass ($\simeq$0.2 $M_\odot$) companion star with a period of 4.75 hr (cite: Archibald2009). In 2013, J1023 showed a sudden brightening in emission at X-ray and gamma-ray frequencies (by a factor of 5–10) as well as at ultraviolet (UV) and optical frequencies (by 1–2 mag), which coincided with the disappearance of the pulsed radio signal (cite: stappers14; patruno14). Double-peaked optical emission lines were soon detected, indicating the formation of an accretion disc (cite: cotizelati14). J1023 has remained in this active state ever since, at an X-ray luminosity of $L_X\simeq 7\times 10^{33}$ erg s$^{-1}$ in the 0.3–80 keV energy range (cite: cotizelati18a) for a distance of 1.37 kpc (cite: deller12).

During the sub-luminous X-ray state, the X-ray emission of J1023 is observed to switch between two distinct intensity modes, dubbed high and low, with sporadic flares in between (e.g. (cite: bogdanov15)). The high mode occurs 70–80% of the time, while the low mode occurs 20–30% of the time and typically lasts from a few tens of seconds to minutes. The drop and rise timescales involved in the mode switching are of the order of $\approx$10 s. X-ray, UV, and optical pulsations occur simultaneously in the X-ray high-intensity mode and disappear in the low mode (cite: archibald15; papitto19; miravalzanon22; illiano23). The UV, optical, and near-infrared (NIR) emission is dominated by the accretion disc and irradiated companion star and also shows flaring and flickering activities (cite: shahbaz15; kennedy18; papitto18; hakala18; shahbaz18). Optical polarimetric observations reveal a linear polarisation (LP) at a level of $\sim$1% (cite: baglio16; hakala18) of uncertain origin. Bright, variable radio continuum emission is also detected (cite: deller15). In particular, the low X-ray mode episodes are accompanied by an increase in the radio flux by a factor of $\simeq$3 on average, with fairly equal rise and decay times and an overall duration that matches low X-ray mode intervals (cite: bogdanov18). These re-brightenings are associated with a temporal evolution of the radio spectrum from inverted to steep. Currently, J1023 spins down at a rate that is $\simeq$4% faster than in the radio pulsar state (cite: burtovoi20). This overall behaviour is unique in the landscape of XRBs, and no comprehensive explanation for it has been found.

This paper presents the results of the largest multi-wavelength campaign ever performed on J1023. Our aim is to ultimately understand the root cause of the mode changes in the active sub-luminous X-ray state and its implication for our understanding of the accretion-ejection coupling in XRB systems that harbour rapidly spinning NSs. The observations of our campaign were conducted on two different nights in June 2021. The first night (Night 1) involved *XMM-Newton*, the Nuclear Spectroscopic Telescope Array (*NuSTAR*), the *Hubble* Space Telescope (HST), the Son OF ISAAC (SOFI) instrument mounted on the New Technology Telescope (NTT), the *Karl G. Jansky* Very Large Array (VLA), and the Five-hundred-meter Aperture Spherical Telescope (FAST); the second night (Night 2) involved the Neutron Star Interior Composition Explorer Mission (NICER), the *Neil Gehrels Swift* Observatory (*Swift*), the Very Large Telescope (VLT), the Rapid Eye Mount (REM) telescope, and the Atacama Large millimetre/sub-millimetre Array (ALMA).

The paper is structured as follows: in Sect. [2](#sec:obs) we present the observations and data analysis. The results are then reported in Sect. [3](#sec:results). In Sect. [4](#sec:discussion) we propose a scenario for the mode switching, present the results of the modelling of the spectral energy distributions (SEDs) in the two modes, and discuss the results in relation to our scenario. Conclusions follow in Sect. [5](#sec:conclusions).

+:-----------------------+:---------------:+:---------------------------------:+:---------:+:--------------------------------:+
| Telescope/Instrument   | Obs. ID/Project | Start – End time                  | Exposure  | Band (setup)                     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
|                        |                 | MMM DD hh:mm:ss (UTC)             | (ks)      |                                  |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| Night 1                                                                                                                     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *XMM-Newton*/EPIC-pn   | 0864010101      | Jun 3 20:44:32 – Jun 4 13:39:15   | 58.7      | 0.3–10 keV (fast timing)         |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *XMM-Newton*/EPIC-MOS1 | 0864010101      | Jun 3 21:09:37 – Jun 4 13:39:01   | 58.1      | 0.3–10 keV (full frame)          |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *XMM-Newton*/EPIC-MOS2 | 0864010101      | Jun 3 22:31:54 – Jun 4 13:39:02   | 53.5      | 0.3–10 keV (full frame)          |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *NuSTAR*/FPMA/FPMB     | 30601005002     | Jun 3 20:36:09 – Jun 4 10:06:09   | 22.3/22.1 | 3–79 keV                         |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012207     | Jun 3 18:29:46 – Jun 3 23:45:44   | 6.4       | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012208     | Jun 4 02:27:57 – Jun 4 12:17:45   | 9.5       | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012209     | Jun 4 03:50:46 – Jun 4 08:44:56   | 2.0       | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/UVOT           | 00033012207     | Jun 3 18:29:50 – Jun 3 23:45:46   | 6.3       | UVM2 (Event)                     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/UVOT           | 00033012209     | Jun 4 03:50:50 – Jun 4 08:44:58   | 1.9       | UVM2 (Event)                     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| HST STIS/NUV-MAMA      | 16061           | Jun 4 00:09:07 – Jun 4 00:43:27   | 2.1       | G230L (fast timing spectroscopy) |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| HST STIS/NUV-MAMA      | 16061           | Jun 4 01:35:28 – Jun 4 02:20:18   | 2.7       | G230L (fast timing spectroscopy) |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *XMM-Newton*/OM        | 0864010101      | Jun 3 22:51:01 – Jun 4 13:23:52   | 48.4      | $B$ (fast window)                |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| NTT/SOFI               |                 | Jun 3 23:49:09 – Jun 4 02:42:38   | 10.4      | $J$ (fast photometry)            |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| VLA                    | SJ6401          | Jun 3 22:30:00 – Jun 4 02:29:20   | 6.7       | Band $X$ (C configuration)       |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| FAST                   | PT2020$_-$0044  | Jun 4 08:47:45 – Jun 4 11:47:45   | 10.8      | Band $L$                         |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| Night 2                                                                                                                     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| NICER/XTI              | 4034060102      | Jun 26 21:56:04 – Jun 26 22:34:31 | 2.0       | 0.3–10 keV                       |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| NICER/XTI              | 4034060103      | Jun 26 23:29:04 – Jun 27 01:33:51 | 4.1       | 0.3–10 keV                       |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012214     | Jun 26 22:19:35 – Jun 26 22:39:47 | 1.2       | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012213     | Jun 26 23:56:12 – Jun 26 23:58:46 | 0.15      | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/XRT            | 00033012215     | Jun 27 00:04:44 – Jun 27 00:21:47 | 1.0       | 0.3–10 keV (photon counting)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/UVOT           | 00033012214     | Jun 26 22:19:35 – Jun 26 22:39:47 | 1.2       | UVM2 (Event+Imaging)             |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/UVOT           | 00033012213     | Jun 26 23:56:12 – Jun 26 23:58:46 | 0.15      | UVM2 (Event+Imaging)             |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| *Swift*/UVOT           | 00033012215     | Jun 27 00:04:44 – Jun 27 00:21:47 | 1.0       | UVM2 (Event+Imaging)             |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| VLT/FORS2              | 107.22RK.001    | Jun 26 22:51:56 – Jun 27 01:15:30 | 8.7       | $R$                              |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| REM/ROSS2              | 43013           | Jun 26 23:20:33 – Jun 27 01:24:41 | 7.4       | $griz$                           |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| REM/REMIR              | 43013           | Jun 26 23:20:44 – Jun 27 01:25:34 | 7.4       | $K$                              |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+
| ALMA                   | 2019.A.00036.S  | Jun 26 21:58:42 – Jun 27 01:12:06 | 9.3       | Band 3 (C43-7 configuration)     |
+------------------------+-----------------+-----------------------------------+-----------+----------------------------------+

# Observations and data analysis

Table [\[tab:log\]](#tab:log) lists all the observations of J1023 presented in this paper. In the following, we describe these observations and the procedures adopted to process and analyse these data.

## *XMM-Newton* (Night 1)

*XMM-Newton* (cite: jansen01; schartel22) observed J1023 on 2021 June 3–4 (Obs. ID 0864010101) using the European Photon Imaging Cameras (EPIC) and the Optical/UV Monitor (OM) telescope (cite: mason01). The EPIC-pn (cite: struder01) was set in fast timing mode (time resolution of 29.52 $\mu$s), the two EPIC-MOS (Metal Oxide Semi-conductor; (cite: turner01)) in full frame mode (time resolution of 2.6 s) and the OM in the fast window mode (time resolution of 0.5 s) with the $B$ filter (effective wavelength 4330 Å; full width at half maximum 926 Å). The observation data files were processed and analysed using the Science Analysis System (SAS; v. 20.0). The X-ray data were analysed in the same way as described by (cite: miravalzanon22). No periods of high background activity were detected. The background-subtracted light curve was extracted over the time interval during which all three EPIC instruments collected data simultaneously and was binned with a time resolution of 10 s. The optical background-subtracted light curve was extracted using the OMFCHAIN pipeline with default parameters. The light curve was binned at a time resolution of 120 s to ensure a high S/N and detect any changes in the optical brightness at least during prolonged periods of low X-ray mode. The net count rates were then converted to magnitudes in the Vega system using the formula provided on the *XMM-Newton* online threads[^2]. To align the X-ray and optical light curves with those extracted from other observatories, the arrival times of photons were converted from the terrestrial time standard to the Coordinated Universal Time (UTC) standard without applying a barycentric correction[^3].

## *NuSTAR* (Night 1)

*NuSTAR* (cite: harrison13) observed J1023 for a total of $\sim$48.6 ks and a net exposure of $\sim$22 ks (Obs. ID 30601005002), almost fully overlapping with the *XMM-Newton* observation. Data were processed and analysed using the NuSTAR Data Analysis Software (NUSTARDAS, v.2.1.2) with the instrumental calibration files stored in CALDB v20220525 and the same prescriptions reported by (cite: miravalzanon22). J1023 was detected up to energies of $\sim$50 keV in both focal plane modules (FPMA and FPMB). Light curves were extracted separately for the two modules, combined to increase the S/N, and binned at a time resolution of 50 s.

## HST (Night 1)

The Space Telescope Imaging Spectrograph (STIS; (cite: woodgate98)) on board HST observed J1023 for 4750 s using the Near-UV Multi-Anode Micro-channel Array (NUV-MAMA) detector in TIME-TAG mode (time resolution of 125 $\mu$s); the data were collected with the G230L grating equipped with a 52$^{\prime\prime}$ $\times$ 0.2 slit with a spectral resolution of $\sim$500 over the nominal range (first order). The data analysis procedure that we adopted is the same as that described by (cite: miravalzanon22). In summary, we used the `stis`$\_$`photons` package[^4] to correct the position of the slit channels and to assign the wavelengths to each time of arrival. We selected times of arrival belonging to channels 993–1005 of the slit and in the 165–310 nm wavelength interval to isolate the source signal.

## NTT/SOFI (Night 1)

We collected NIR high time-resolution imaging data using the SOFI (cite: moorwood98) instrument mounted on the European Southern Observatory (ESO) 3.6 m NTT at La Silla Observatory (Chile). Observations were carried out using the $J$ filter from 2021 June 3 at 23:49:09 UTC to June 4 at 02:42:38 UTC (Table [\[tab:log\]](#tab:log)). In order to achieve 1 \*s time resolution, observations were performed in Fast Photometry mode, which restricts the area on which the detector is read. Specifically, the instrument was set to read a 400$\times$400 pixels window ($1.9'\times1.9'$). During the observation, a series of 100 frames each with an exposure time of 1.0 s were stacked together to form a ‘data cube’. There was a gap of $\sim$3 s between each cube. Photometric data were extracted through aperture photometry with an aperture radius of $1.4''$ using a custom pipeline based on the `DAOPHOT` package (cite: DAOPHOT). In order to minimise systematic errors, we performed photometry on J1023 and a reference star (at position R.A. = 10$^\mathrm{h}$23$^\mathrm{m}$50$^\mathrm{s}$54, Dec. = +00$^{\circ}$38$^{\prime}$16.$^{\prime\prime}$4, J2000.0, and with a magnitude of $J = 15.44 \pm 0.05$ mag in the Vega system from the Two Micron All-Sky Survey (2MASS) point source catalogue), assumed to have constant brightness. We then re-binned the light curve at a time resolution of 10 s to reduce the scatter and investigate the presence of variability at the same time resolution as the light curves in the X-ray and UV bands. For a more conservative approach, we evaluated the errors on the magnitudes of the re-binned light curves as the standard deviation of the magnitudes measured in each bin.

## VLA (Night 1)

The VLA observed J1023 for 4 hours, starting on 2021 June 3 at 22:30 UTC. The array was in its C-configuration and data were taken at a central frequency of 10 GHz, with a bandwidth of 4 GHz. J1331$+$3030 was used as flux and band-pass calibrator, while J1024$-$0052 was used as phase calibrator. The separation between the target and the phase calibrator is 0.3$^{\circ}$. To calibrate and analyse the data we followed the prescription of (cite: deller15) and (cite: bogdanov18). Here we report the main steps. After initial calibration using the VLA pipeline within the Common Astronomy Software Application (CASA) package (version 5.1.1), manual flagging of bad data was performed. Unfortunately, the first half of the observation turned out to be unusable, possibly due to the bad weather conditions that occurred during the observation, and was completely flagged out.

Subsequently, we self-calibrated the data using a solution interval of 75 s for the phase calibration and 45 min for the amplitude$+$phase calibration. Upon inspection of the field of view (FOV), three main sources were identified: the target J1023, a faint source to the north, namely J102348.2$+$004017, and the brightest source in the field, located to the south-east, namely J102358.2$+$003826. J102358.2$+$003826 is a well-known galaxy at redshift $z = 0.449$ (cite: ahn14) with a resolved extended emission whose secondary lobes heavily affect the overall root mean square (rms) noise level (cite: deller15). To remove the problematic contribution of J102358.2$+$003826, we first cleaned the image using a mask with the `tclean` task. We set the `nterms` parameter equal to 2 to take into account the spectral properties of the galaxy over the wide bandwidth of the observation (cite: deller15). This step provided the model visibilities of J102358.2$+$003826. Next, we used the `uvsub` task to subtract these model visibilities from the self-calibrated visibilities and deconvolved the residuals. The resulting image therefore does not have any contribution from J102358.2$+$003826.

As pointed out by (cite: deller15), the gain solutions from the self-calibration obtained before the subtraction of J102358.2$+$003826 were dominated by the pointing errors of this source. This source was located beyond the half-power point of the antenna, resulting in inaccurate solutions. Therefore, we had to invert the amplitude and phase self-calibration after subtracting this source from the field. We used the CASA task `invgain` (cite: hales16) to invert the calibration table and applied it to the self-calibrated visibilities. The final image obtained had a beamwidth size of 3.6$^{\prime\prime} \times$2.1$^{\prime\prime}$, and an rms noise level of $\simeq$4 $\mu$Jy beam$^{-1}$.

To extract the light curve, we imaged the field using a 60 s time interval and a mask around the target with the CASA `tclean` task, setting `niters=10` and `cycleniter=10`. We selected these values after evaluating random images where the target was either detected or not detected, and ensuring that this choice did not result in false positive detections. Then, we used the `imfit` task to obtain the peak flux density of the target and the check source, J102348.2+004017, for each 60 s image to investigate possible systematic effects. To measure the rms noise level around J1023 and check source, we placed four boxes around each source and used the `imstat` task to average the rms noise level within each box. To build the light curve, we considered a source as detected whenever the flux density value obtained with `imfit` was $\ge$3$\sigma$; otherwise, we took three times the rms noise level as an upper limit. To take into account possible systematics affecting the FOV, we investigated possible correlations between the light curves of the target and the check source. No evidence of such correlations was found. Finally, we further flagged bad 60 s images and removed intervals with odd results, such as sudden increases in the flux density of J102348.2$+$004017.

## FAST (Night 1)

FAST (cite: jiang19; jiang20; qian20) observed J1023 starting on 2021 June 4 at 08:47:45 UTC. The total integration time was 3 hr (the first two minutes and the last two minutes were dedicated to the injection of an electronic noise signal, referred to as a CAL). The observation was planned so as to cover a range of orbital phases from approximately 0.5 to 1.1, and hence to encompass the epoch of passage of the pulsar at the inferior conjunction of the orbit (corresponding to a phase of 0.75). This strategy should allow us to minimise the impact of eclipses of the radio signal caused by the gas out-flowing from the companion star due to irradiation from the pulsar wind. The observation sampled a total of 21 low mode episodes according to the simultaneous *XMM-Newton* observation (see Fig. [1](#fig:timeseries1)). The central observing frequency was 1.25 GHz, with a range from 1.05 GHz to 1.45 GHz, including a 20 MHz band edge on each side. The average system temperature was 25 K. The recorded FAST data stream for pulsar observations is a time series of total power per frequency channel, stored in `psrfits` format (cite: hotan04) from a ROACH-2-based back-end[^5], which produces 8-bit sampled data over 4k frequency channels at a cadence of 49.152 $\mu$s.

We searched for pulsations with either a dispersion signature or instrumental saturation in all data collected during the observation. We performed four different types of data processing.

*Data folding based on the ephemeris derived from the X-ray data*: We analysed the data using the ephemeris derived from the strictly simultaneous X-ray data collected by *XMM-Newton* (cite: miravalzanon22). We separately folded the FAST data from the entire observation and those obtained by stacking the data acquired during all the periods of high X-ray mode and all the periods of low X-ray mode. However, no radio pulses were detected with S/N$>$6 in either case.

*Dedicated search for persistent periodic radio pulses*: For the sake of robustness, we created de-dispersed time series for each pseudo-pointing over a dispersion measure (DM) range between 3 pc cm$^{-3}$ and 100 pc cm$^{-3}$. This range covers all uncertainties of the semi-blind search, as J1023 was discovered at a DM of 14.3 pc cm$^{-3}$ (cite: Archibald2009). We set the step size between subsequent trial DMs equal to the intra-channel smearing over the entire band. This ensures that any trial DM deviating from the source DM by $\Delta$DM does not cause extra smearing beyond the intra-channel smearing[^6]. We performed a ‘jerk’ acceleration search ((cite: andersen18); see also (cite: wang21)) for periodic signals in the de-reddened power spectrum of each de-dispersed, barycentred time series. We restricted the search to various frequency ranges around the nominal spin frequency of J1023, and allowed the power of the highest harmonic component of the signal to drift in the Fourier domain up to a maximum number of 200 frequency bins and 50 frequency derivative bins. The powers of the first eight harmonics were summed (in powers-of-two harmonics). All identified candidate periodicities underwent a sifting procedure to reject less significant, duplicated (i.e. detected at different DMs and accelerations), and/or harmonically-related candidates. Using the `prepfold` tool, the data were folded at the nominal period, period derivative and DM of the sifted candidates. Corresponding diagnostic plots including the integrated pulse profile, the signal intensity as a function of time and frequency, and the DM versus $\chi^2$ values were generated and saved for visual inspection. The candidates were judged based on persistent and broadband emission, as well as distinct peaking of the signal’s significance at specific DM values. No signal with DM, period, and period derivative close to the expected values was detected.

*Search for single pulses*: We used the dedicated search scheme in (ii) to de-disperse the time series. We then applied 14 box-car width-match filter grids distributed in logarithmic space from 0.1 to 30 ms. A zero-DM matched filter was used to mitigate radio frequency interference (RFI) in the blind search. All the resulting candidate plots were visually inspected, but most candidates were determined to be RFI. No pulsed radio emission with a dispersive signature was detected with S/N$>$5.

*Search for baseline saturation*: We acknowledge that FAST would become saturated if the radio flux density reached levels as high as 1 kJy to 1 MJy. Therefore, we also searched for saturation signals in the recorded dataset. We looked for epochs where at least half of the channels satisfied one of the following conditions: (1) the channel was saturated (255 value in 8-bit channels), (2) the channel had a zero value, or (3) the rms deviation of the bandpass was $<$2. We did not find any instances of saturation lasting $>$0.5 s during the observational campaign.

We then calibrated the noise level of the baseline with noise CAL injection, and derived a 5-$\sigma$ flux density upper limit for persistent radio pulsations of 2.0$\pm$0.5 $\mu$Jy at 1.25 GHz considering the entire integration time of 2.8 hr, assuming a pulse duty cycle between 0.05–0.3 (which is typical for millisecond pulsars; see the ATNF pulsar catalogue; (cite: manchester05)) and disregarding the possible scintillation effect. Within the uncertainty of the flux measurements and stability threshold, no flux variations were seen during the observation, consistent with an apparent lack of scintillation. The 5-$\sigma$ flux upper limits on the pulsed flux density of J1023 during the high and low modes can be evaluated by scaling the above-mentioned limit for the specific integration time spans during the high and low-mode periods in the X-rays: we obtain upper limits of 2.2$\pm$0.6 $\mu$Jy in the high mode (2.3 hr) and 4.7$\pm$1.0 $\mu$Jy in the low mode (0.5 hr).

## NICER/XTI observations (Night 2)

The X-ray Timing Instrument (XTI) mounted on NICER (cite: gendreau12) observed J1023 between 2021 June 26 at 21:56:04 UTC and June 27 at 01:33:51 UTC, for an exposure time of $\sim$6.1 ks. The raw, unfiltered data were processed and analysed using tools within the NICERDAS software package and the latest version of the calibration files at the time of the analysis (CALDB v. 20221001)[^7]. We extracted the background-subtracted light curve in the 0.5–10 keV energy range with a time bin of 10 s using the nicerl3-lc pipeline. This pipeline utilises the ‘Space Weather’ background model, that is to say, it estimates the background level on the basis of the local spacecraft environment (see Fig. [3](#fig:timeseries2), first panel).

## Swift/XRT observations (Nights 1 and 2)

The *Swift* (cite: gehrels04) X-ray Telescope (XRT; (cite: burrows05)) observed J1023 in the photon-counting mode (time resolution of 2.5 s) on both Night 1 and Night 2. The first observation started on 2021 June 3 at 18:29:46 UTC and consisted of 11 snapshots, with a total elapsed time of $\simeq$51.3 ks and an effective exposure time of $\sim$17.9 ks. The second observation started on 2021 June 26 at 22:19:35 UTC and consisted of three snapshots, resulting in a total elapsed time of $\simeq$7.3 ks and an effective exposure time of $\sim$2.4 ks. The raw, level-1 data were processed and screened using standard criteria. Source photons were collected from a circular aperture of radius 47.2$^{\prime\prime}$ centred on J1023 and background photons were collected from an annular region with inner and outer radii of 94.4$^{\prime\prime}$ and 188.8$^{\prime\prime}$, respectively, also centred on J1023.

We extracted a background-subtracted time series with a time bin of 100 s, suitable to sample adequately the X-ray mode switching (see Figs. [1](#fig:timeseries1) and [3](#fig:timeseries2)).

## Swift/UVOT observations (Nights 1 and 2)

The *Swift* Ultra-Violet/Optical Telescope (UVOT; (cite: roming05)) observed J1023 simultaneously with the XRT. The observations were performed in both image and event modes using the UVM2 filter (central wavelength 2260 Å; full width at half maximum 527 Å). Data were processed and analysed in the standard way. For the source photons, we used a circular extraction region of radius of 5$^{\prime\prime}$ centred on the source position. For the background photons, we adopted a circular extraction region of radius 20$^{\prime\prime}$ away from source. For the data in image mode, photometry was carried out using the `uvotsource` task.

For the data in event mode (time resolution of 11 ms), we used the `coordinator` tool to convert raw coordinates to detector and sky coordinates, `uvotscreen` to filter out hot charge-coupled device (CCD) pixels and obtain a cleaned event list, and `uvotevtlc` to extract a background-subtracted light curve with a time bin of 120 s. This time bin provided a sufficiently high S/N to detect any changes in the UV brightness at least during the longest periods of low X-ray mode.

## REM photometric observations (Night 2)

We observed J1023 on Night 2 with the 60-cm REM telescope (cite: Zerbi2001; Covino2004) located at La Silla Observatory (Chile). We obtained 48 strictly simultaneous exposures with the ROSS2 imager, each with an integration time of 60 s, with Sloan Digital Sky Survey (SDSS) $griz$ optical filters (Table [\[tab:log\]](#tab:log)). We reduced the images following standard procedures (bias subtraction and division by a normalised flat-field), and performed aperture photometry with the `PHOT` tool in `IRAF` using an aperture size of 6 pixels. We performed flux calibration using stars in the field from the American Association of Variable Star Observers (AAVSO) Photometric All-Sky Survey (APASS) catalogue[^8] (cite: Henden2019). We obtained simultaneous $K$-band observations with the REM infrared (REMIR) camera. A total of 300 15 s integration images were acquired, which we combined 5 by 5 to correct for the background contribution. Aperture photometry was performed with `IRAF` as described above. The images were flux-calibrated against a selection of stars in the field from the 2MASS point source catalogue[^9].

## VLT/FORS2 polarimetric observations (Night 2)

We observed J1023 with the FOcal Reducer/low dispersion Spectrograph 2 (FORS2; (cite: appenzeller98)) mounted on the 8.2-m VLT at Paranal Observatory (Chile) in polarimetric mode using the optical filter $R\_SPECIAL +76$ ($R$; central wavelength 655 nm, full width at half maximum 165 nm). The observations were performed on Night 2 under thin cirrus clouds conditions, with seeing varying from $0.4$$^{\prime\prime}$ to $0.9$$^{\prime\prime}$. A total of 156 short (10 s) exposures were taken, resulting in an observing time of $\sim$2.41 hr, overheads included (about half the orbital period).

A Wollaston prism was inserted in the optical light path to split the incident radiation into two orthogonally polarised light beams called ordinary ($o$) and extraordinary ($e$) beams. A Wollaston mask was introduced to avoid overlap of the beams on the CCD. In addition, a rotating half-wave plate (HWP) was inserted, allowing images to be taken at four different angles ($\Phi_i$) of the plate with respect to the telescope axis: $\Phi_{i}=22.5^{\circ}(i-1), \, i=1, 2, 3, 4$. This step is essential to obtain a polarisation measurement, since the set of images at the four different angles must be combined to evaluate the level of LP (as described below). Therefore, a total of 39 polarisation epochs were acquired with the programme. All images were processed by subtracting an average bias frame and dividing by a normalised flat field. Aperture photometry was performed using the `daophot` tool (cite: Stetson1987), using an aperture of 6 pixels. The normalised Stokes parameters $Q$ and $U$ for the LP were evaluated following the methods described by (cite: baglio20) and references therein. These values were then corrected for instrumental polarisation by observing a non-polarised standard star[^10] (WD 1620-391) using the same setup on the same night. A polarisation level of $<0.2\%$ was measured, which is consistent with the typical instrumental polarisation level expected for the FORS2 instrument as reported on the ESO website[^11] ($<$0.3% in all optical bands). The Stokes parameters evaluated for the non-polarised standard star were then subtracted from the Stokes parameters of J1023 at each epoch.

We then used an algorithm to estimate the level and angle of LP. This algorithm is based on the evaluation of the quantity $S(\Phi)$ for each of the HWP angles (e.g. (cite: Serego) and references therein; see also (cite: Covino1999; baglio20)). $S(\Phi)$ is the component of the Stokes vector that describes the LP along the $\Phi$ direction (e.g. $S(0^{\circ})=Q$). It is defined as

$$\begin{equation}
\label{eq_S}
S(\Phi)=\left( \frac{f^{o}(\Phi)/f^e(\Phi)}{f^o_u(\Phi)/f^e_u(\Phi)}-1\right)\,\left( \frac{f^{o}(\Phi)/f^e(\Phi)}{f^o_u(\Phi)/f^e_u(\Phi)}+1\right)^{-1},
\end{equation}$$

where $\Phi$ is the angle of the HWP, $f^{o}(\Phi)$ and $f^{e}(\Phi)$ are the ordinary and extraordinary fluxes for a given angle $\Phi$, and $f^o_u(\Phi)$ and $f^e_u(\Phi)$ are the same quantities evaluated for the non-polarised standard star. $S(\Phi)$ is related to the polarisation level $P$ and angle $\theta$ by $S(\Phi) = P\, \cos 2(\theta-\Phi)$. The parameters $P$ and $\theta$ were estimated by maximising the Gaussian likelihood function and using this as the starting point for a Markov chain Monte Carlo (MCMC) procedure (cite: Hogg&Foreman2018) (see (cite: baglio20) for further details on the algorithm). The best fit parameters were then calculated as the median of the marginal posterior distributions of these parameters, while the uncertainties were estimated as the 16–84th percentiles of the distributions. For non-detections, the 99.97% percentile of the posterior distribution of the parameter $P$ was used to calculate an upper limit.

After fitting the $S(\Phi)$ curve, we obtained an LP value that is already corrected for instrumental effects. However, the polarisation angle still needs to be corrected using the Stokes parameters of a polarised standard star. For this purpose, we observed the star Hiltner 652 and measured its Stokes parameters to determine its polarisation angle. This was then compared to the tabulated value, and a difference of $1.71^{\circ}\pm 0.30^{\circ}$ was applied to the polarisation angle of J1023. However, the resulting LP will still include an interstellar component. Evaluating the interstellar contribution is not straightforward. In principle, we could use a group of reference stars in the same field as the target in Eq. [\[eq_S\]](#eq_S), under the assumption that these stars are non-polarised. This way, the LP of the target would be corrected for both instrumental and interstellar contributions. However, it is important to ensure that the chosen reference stars all have the same level of polarisation, which would be a good indication of their intrinsic non-polarised nature (see e.g. (cite: baglio20)). Unfortunately, not only is the FOV of J1023 sparse in the optical, but the very short exposure times (10 s) exclude all faint ($R>19$) stars from this study. We are therefore left with only one possible comparison star in the field, which makes it difficult to verify whether the chosen star is indeed intrinsically non-polarised. As a result, we used the fluxes of the non-polarised standard star in Eq. [\[eq_S\]](#eq_S). The field star will be used as a comparison for the analysis.

We can evaluate the maximum interstellar contribution to the LP of a source, referred to as $P_{\rm int}$, through considerations of its absorption coefficient in the $V$-band, $A_{\rm V}$: $P_{\rm int}(\%)<3A_{V}$ (cite: Serkowski75). For J1023, the best-fitting absorption column density, $N_{\rm H}$, according to *XMM-Newton* observations is $5.0^{+0.3}_{-0.2}\times 10^{20}$ cm$^{-2}$ (cite: campana19). Using the relation between $N_{\rm H}$ and $A_{\rm V}$ in our Galaxy from (cite: Foight2016), we calculate $A_{\rm V}=0.17\pm0.01$ mag and therefore $P_{\rm int}<0.52\%$. This is very low and comparable to the instrumental polarisation measured for the instrument configuration. It is also comparable to the upper limit of the interstellar polarisation measured for J1023 (cite: baglio16).

## ALMA observations (Night 2)

The ALMA observations were conducted using the 12 m array and 38 antennas in the C43-7 configuration (baselines 22–2492 m), with a FOV of $59.72''$ and a maximum recoverable scale of $11.5''$. The total integration time on source was $\sim$2 hr and the phase centre was R.A. = 10$^\mathrm{h}$23$^\mathrm{m}$47$^\mathrm{s}$68; Dec. = +00$^{\circ}$38$^{\prime}$41.$^{\prime\prime}$00 (ICRS). The weather conditions were good and stable, with an average precipitable water vapour of $\sim$1.2 mm and an average system temperature of $\simeq$65 K. The band-pass and flux calibrators used were J1058$+$0133 and J1256$-$0547, while J1028$-$0236 was used as the phase calibrator. The continuum image was obtained by averaging the four base-bands of width 1.875 GHz, each centred at 90.5003 GHz, 92.5003 GHz, 102.5003 GHz, and 104.5003 GHz, covering a total bandwidth of 7.5 GHz. No spectral lines were detected within the observed frequency range above the 3$\sigma$ noise level per spectral channel of $\sim$0.48 mJy beam$^{-1}$.

Data reduction was carried out following standard procedures using the ALMA pipeline within CASA (v. 6.1.1-15)[^12]. Continuum images were produced using `tclean` interactively and applying a manually selected mask. These images were corrected for primary beam attenuation and were produced using both natural weighting and a Briggs `robust=0` weighting (cite: briggs95). The former maximises the sensitivity whereas the latter provides higher angular resolution. The mean frequency of the continuum image is 97.51 GHz, which corresponds to a wavelength of 3.1 mm. Table [1](#tab:alma_obs) lists the synthesised beam and the rms noise of each image.

|                    |                  |              |                       |
|:-------------------|:----------------:|:------------:|:---------------------:|
| Weighting          | Synthesised beam |     P.A      |     rms$^{\rm a}$     |
|                    |  $(''\times'')$  | ($^{\circ}$) | ($\mu$Jy beam$^{-1}$) |
| Natural            | $0.87\times0.53$ |   $-$74.5    |          6.1          |
| Briggs, `robust=0` | $0.55\times0.30$ |   $-87.3$    |         10.6          |

: ALMA continuum maps.

**Notes.** $^{\rm a}$ rms noise level at the phase centre.

# Results

## X-ray and UV emissions

The X-ray light curve extracted from *XMM-Newton* data on the first night reveals flaring activity over a time span of $\sim$1.5 hr at the beginning of the observation. A total of 288 switches between high and low modes were observed during the observation (see Fig. [1](#fig:timeseries1)). Based on our thresholds for the EPIC net count rates in the different modes (see (cite: miravalzanon22)), we estimated that J1023 spent $\simeq$65, 17 and 1% of the time in the high, low and flaring modes, respectively, and the rest of the time switching between modes. The good time intervals corresponding to the high and low modes were then used to extract the background-subtracted spectra, response matrices, and ancillary files separately for each mode. The *NuSTAR* light curve is characterised by a lower S/N than the *XMM-Newton*/EPIC light curve. Nevertheless, it is possible to recognise the same flaring episodes and mode switchings detected using *XMM-Newton* (see Fig. [1](#fig:timeseries1)). We used the good time intervals for the high and low modes selected by the strictly simultaneous *XMM-Newton*/EPIC light curves to extract the background-subtracted spectra, response matrices, and ancillary files separately for each mode.

The X-ray light curve extracted from NICER data on the second night, shown in the top panel of Fig. [3](#fig:timeseries2), reveals 22 instances of X-ray mode switching, without any obvious flaring episodes. We applied intensity thresholds to the light curve to select the time intervals corresponding to the high ($>$2.5 counts s$^{-1}$) and low ($<$2.5 counts s$^{-1}$) X-ray modes. Based on this selection, we estimate that J1023 spent $\sim$70% of the time in the high mode and $\sim$30% of the time in the low mode. We also detected two periods of X-ray low mode in the *Swift*/XRT data, one of which was also covered by the NICER observations (see the second panel of Fig. [3](#fig:timeseries2)).

The UV light curves exhibit substantial variability. Specifically, the HST light curve on Night 1 displays flaring activity as well as dips in the count rate that coincide with the low-mode episodes observed in X-rays (Fig. [1](#fig:timeseries1); see also (cite: miravalzanon22; jaodand21)). A dip in the UV brightness by $\sim$0.7 mag is also clearly visible in the *Swift*/UVOT data during the third snapshot of Night 2. The decrease occurs over a span of several minutes during an episode of low mode (Fig. [3](#fig:timeseries2)).

![](PSRJ1023_lcurves_night1.pdf)

![](PSRJ1023_lcurves_night1_zoom.pdf)

![](PSRJ1023_lcurves_night2.pdf)

![](PSRJ1023_lcurves_ALMA_flares.pdf)

## Optical/NIR photometric properties

On the first night, the source is brighter at the beginning than in the rest of the observation (reaching $B\simeq17-16.5$ mag), displaying a smooth quasi-sinusoidal modulation at the orbital period with a semi-amplitude of $\simeq$0.2 mag around an average value of $B\simeq17.3$ mag. We fit a sinusoidal function to the light curve by fixing the period and reference phase of the sinusoid to the binary orbital period and the phase value obtained from the time of passage of the pulsar through the ascending node, respectively, as derived by (cite: miravalzanon22). Then, we subtracted the best-fitting function from the observed count rates. The resulting detrended light curve is shown in Fig. [1](#fig:timeseries1). After initial flaring activity resembling the X-ray behaviour, the optical intensity appears to be flickering, but without any sign of mode switching.

Figure [1](#fig:timeseries1) also shows the NIR light curve. Variability in the form of dips and flickering is evident. The fractional rms magnitude deviation of the light curve, computed following the method described by (cite: vaughan03), is (10.1$\pm$0.2)%. No NIR flare was observed at the switch from the low to the high X-ray mode, as previously reported (cite: papitto19; baglio19). Furthermore, we did not detect any signs of mode switching in the light curve. The average magnitudes measured separately during the high and low modes are compatible within 1$\sigma$ ($J=15.39\pm 0.16$ mag and $J=15.37\pm 0.13$ mag in the high and low modes, respectively), indicating that there is no significant correlation between the NIR variability and mode switching.

On Night 2, the optical light curves show clear variability on short timescales (Fig. [3](#fig:timeseries2), fourth panel). Unlike what was seen on Night 1, no modulation at the system orbital period is detected. The average magnitudes are $g=16.65\pm0.02$ mag, $r=16.45\pm0.02$ mag, $i=16.20\pm 0.03$ mag, $z=16.09\pm0.03$ mag (in the AB photometric system), all marginally consistent with those reported by (cite: cotizelati14; baglio16). To estimate the amount of intrinsic variability, we evaluated the fractional rms magnitude deviation of the light curves following (cite: vaughan94). We find a low-significance fractional rms of $6.2\pm3.4\%$, $6.9\pm2.3\%$ and $12.7\pm4.7\%$ at a time resolution of 160 s in the $g$, $r$ and $z$ bands, respectively, while no excess intrinsic variability could be detected in the $i$ band. This fractional rms is comparable to what has been observed for a few black hole XRBs in the optical band on a similar timescale, such as GX 339-4 (cite: Gandhi2009; Gandhi2010) and MAXI J1535$-$571 (cite: Baglio2018). In these systems, the variability has been attributed to the emission of a flickering jet that contributes up to optical frequencies. In contrast, when accretion dominates, lower values of fractional rms are typically measured, as seen in the case of the black hole XRB GRS 1716$-$249 (cite: Saikia22).

Unfortunately, most of the $K$-band images are of bad quality, resulting in an empty FOV. We stacked together three of the combined images in which the field was visible and J1023 was detected (so a total of 15$\times$15 s integration images, all taken during the high mode), and performed the calibration against a selection of stars in the field from the 2MASS point source catalogue. We obtained an average magnitude of $K=14.41 \pm 0.29$ mag, which is consistent with previous values reported in the literature (see e.g. (cite: cotizelati14; baglio16)).

## Optical polarimetric properties

Figure [3](#fig:timeseries2) shows the evolution of the optical LP level on the second night of observations. To improve the S/N of the observations without losing too much information on the short-term variability of the LP, we combined the measurements so that each LP data point covers 80 s (four HWP angles $\times$ 10 s of integration $\times$ two sets). We define an LP measurement as a detection when it reaches a confidence level of greater than 2$\sigma$. Using this threshold, we obtain a total of 8 LP detections and 11 upper limits at a 99.97% confidence level (see Table [2](#tab:polarisation)). The average level of LP, calculated as the average of all 2$\sigma$-significant detections, is $0.92\pm0.39\%$. This is consistent with previous results in the same band (cite: baglio16). The polarisation angle is well constrained at a value of $(6^{+18}_{-15}$)$^{\circ}$ (corrected for the polarisation angle of the standard star).

| Epoch (MJD) | LP ($\%$) | PA ($^{\circ}$) | Upper limit ($\%$) |
|:---|:--:|:--:|:--:|
| 59391.95402 (?) | $0.76^{+0.38}_{-0.37}$ | $27.32^{+15.41}_{-14.08}$ |  |
| 59391.95917 (?) | $0.81^{+0.38}_{-0.36}$ | $-3.57^{+13.33}_{-12.62}$ |  |
| 59391.96436 (?) | – | – | 1.77 |
| 59391.96949 (?) | $1.09^{+0.37}_{-0.36}$ | $-2.92^{+9.28}_{-9.37}$ |  |
| 59391.97459 (?) | $1.04^{+0.52}_{-0.50}$ | $1.56^{+13.82}_{-14.64}$ |  |
| 59391.97971 (?) | – | – | 1.99 |
| 59391.98485 (L) | – | – | 1.82 |
| 59391.99000 (H) | – | – | 3.42 |
| 59391.99517 (H) | – | – | 4.77 |
| 59392.00034 (H) | – | – | 2.33 |
| 59392.00549 (H) | $1.12\pm 0.32$ | $21.96^{+8.14}_{-8.41}$ |  |
| 59392.01063 (?) | – | – | 2.02 |
| 59392.01578 (?) | – | – | 1.22 |
| 59392.02094 (?) | $0.63^{+0.30}_{-0.28}$ | $-6.46^{+12.98}_{-12.57}$ |  |
| 59392.02608 (?) | $0.96\pm 0.29$ | $1.38^{+7.58}_{-7.56}$ |  |
| 59392.03126 (?) | – | – | 1.61 |
| 59392.03643 (?) | – | – | 1.27 |
| 59392.04160 (?) | $1.03^{+0.36}_{-0.35}$ | $9.39^{+10.11}_{-10.82}$ |  |
| 59392.04680 (H) | – | – | 2.25 |

: LP detections and angles with a significance $>$2$\sigma$.

**Notes.** For non-detections, upper limits are quoted at a confidence level of 99.97%. The first column indicates, in parentheses, which mode the MJD refers to (‘L’ for low mode, ‘H’ for high mode, ‘?’ when unknown due to the lack of simultaneous X-ray observations).

When detected, the LP appears fairly constant throughout the observations. We investigated any potential changes in the LP level as a function of the X-ray mode (low/high) by averaging all images taken during the high and low modes. We found that the LP was $0.65\pm0.43$% (with a 99.97% confidence level upper limit of $2.12\%$) in the high mode and $0.36^{+0.27}_{-0.35}\%$ (with a 99.97% confidence level upper limit of $1.58\%$) in the low mode.

The measured levels of LP are not corrected for interstellar contribution, which is expected to be low according to Serkowski’s law ($<$0.52%; (cite: Serkowski75)). Figure [5](#fig:Q_U) shows the $Q$ and $U$ Stokes parameters on the $Q-U$ plane for the whole dataset, including J1023 (black dots), a comparison star in the field (red squares), and the non-polarised standard star (green star). The non-polarised standard star is located very close to the origin of the $Q-U$ plane, indicating that the instrumental polarisation of VLT/FORS2 is low, as expected. The Stokes parameters of the comparison star, on the other hand, are scattered around a common point, consistent with the position of the non-polarised standard within $\sim$1.5$\delta$, where $\delta$ is the standard deviation of the points. Any deviation from the position of the non-polarised standard on the plane is a good estimate of the interstellar polarisation of the field (assuming that the comparison star is intrinsically non-polarised). Interestingly, the Stokes parameters of J1023 are clustered around a common point in a different region of the $Q-U$ plane, with a higher scatter than the comparison star due to larger uncertainties. For the two time series of the $Q$ and $U$ Stokes parameters, we are unable to claim any detection of short-timescale variability.

![](Q_U_global.pdf)

## Millimetre emission

Figure [6](#fig:alma) shows the ALMA 3.1 mm continuum emission towards J1023. Two sources were detected within the FOV of ALMA. J1023 was detected at a significance level of $\sim$15$\sigma$. The other source, which we designate ALMA J102349.1$+$003824 following the naming convention of new sources discovered by ALMA, is located $\sim$22$^{\prime\prime}$ south-east of J1023 and was detected at a significance level of $\sim$9$\sigma$. The panels on the right of the figure display the zoom-in maps around each source, with the continuum image obtained with natural weighting displayed in colour scale and the black contours derived from the image with `robust=0`. Table [\[tab:alma_res\]](#tab:alma_res) reports the peak coordinates, the peak intensity, the integrated flux, and the deconvolved size obtained by fitting a 2D Gaussian function to the high-resolution image (`robust=0`).

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | R.A (ICRS) | Dec. (ICRS) | $I_{\nu}$$^{\rm a}$ | $S_{\nu}$$^{\rm b}$ | Deconvolved Size$^{\rm c}$ | P.A |
|  | (hh:mm:ss) | ($^{\circ}$:$'$:”) | ($\mu$Jy beam$^{-1}$) | ($\mu$Jy) | ($''\times''$) | ($^{\circ}$) |
| PSR J1023 | 10:23:47.689$\pm$0.001 | 00:38:40.677$\pm$0.004 | 103.7$\pm$3.6 | 144.6$\pm$8.0 | (0.305$\pm$0.060)$\times$(0.205$\pm$0.031) | 86$\pm$29 |
| ALMA J102349.1 | 10:23:49.131$\pm$0.002 | 00:38:23.72$\pm$0.02 | 95$\pm$15 | 109$\pm$29 | \<0.39$\times$0.22$^{\rm d}$ | … |

**Notes.** $^{\rm a}$ Peak intensity. $^{\rm b}$ Integrated flux. $^{\rm c}$ FWHM obtained from 2D Gaussian fits. $^{\rm d}$ Component is a point source.

![](alma-images.pdf)

The 3.1 mm continuum emission from J1023 has a compact shape with some elongation towards the south-east (shown in the top right panel of Fig. [6](#fig:alma) using black contours). The millimetre continuum emission peaks $\sim$$0.32''$ south of the optical position. The deconvolved size obtained from the 2D Gaussian fit in the `robust=0` image is $0.305''\times0.205''$, which corresponds to approximately 418AU $\times$ 281AU ($\sim$$6.3\times10^{15}$ cm $\times$ $4.2\times10^{15}$ cm) at a distance of 1.37 kpc (this is approximately 7$\times$10$^4$ times the orbital separation of the system; (cite: archibald13)). The emission from ALMA J102349.1$+$003824 also appears compact (see the bottom-right panel of Fig. [6](#fig:alma)). The 2D Gaussian fit yields a point-like source with a full with at half maximum as large as $0.39''\times0.22''$ (see Table [\[tab:alma_res\]](#tab:alma_res)). The results of the searches for counterparts of this source at other wavelengths are reported in Appendix [6](#sec:appendix).

To determine the spectral index of J1023 within the ALMA bandwidth, we imaged the continuum emission from the lower and upper sidebands, which have central frequencies of 91.47886 GHz and 103.5115 GHz, respectively. The resulting spectral index is $-0.1\pm0.8$, which is consistent with previous reports for the average cm emission (cite: deller15; bogdanov18).

To probe variability in the millimetre emission, we obtained images scan by scan (typically with a duration of $\sim$4–5 minutes), using a natural weighting. We then computed the peak intensities and flux densities considering the emission above $3\sigma$ level. The bottom panel of Fig. [3](#fig:timeseries2) shows the evolution of the flux density over time. This quantity was found to vary by a factor of $\sim$5 within the range $\sim$30–160 $\mu$Jy on a timescale of about 5 minutes. In some cases, the flux density remained below the detection sensitivity, resulting in upper limits of the order of a few tens of microjanskys. Figure [3](#fig:timeseries2) also shows the ALMA time series extracted using time intervals of variable length corresponding to the durations of the X-ray-mode episodes. Two flaring episodes can be clearly seen.

We measured average flux densities of 89$\pm$13 $\mu$Jy in the high mode and 134$\pm$23 $\mu$Jy in the low mode, excluding the two flaring episodes (see Table [\[tab:mode_properties\]](#tab:mode_properties)). Overall, the anti-correlated variability pattern appears to be more pronounced between the cm and X-ray emission than between the millimetre and X-ray emissions.

The integration times adopted above are effective for studying the variability of the millimetre emission on minute timescales, but may average out large enhancements of the millimetre flux on much shorter timescales (of the order of seconds). Therefore, we performed a dedicated search for short flaring episodes by extracting images of different durations using the entire dataset. This search resulted in the detection of the two above-mentioned episodes of bright millimetre emission (Fig. [4](#fig:timeseries_alma_flares)). No other remarkable events were detected. The first episode (hereafter ‘Flare 1’) occurred on 2021 June 26 within the time range 22:19:29 – 22:19:44 (UTC) at the switch from high mode to low mode and reached a peak flux density of 1.01$\pm$0.08 mJy. The second event (‘Flare 2’) took place during the time range 23:48:29 – 23:48:44 (UTC) and reached a peak flux density of 0.7$\pm$0.1 mJy. The lack of continuous coverage in the millimetre band before and during the switch from the high to the low mode does not allow us to determine the exact epoch of the flare onset. We note that these values refer to the flux at the peak of the flares and are therefore higher than those obtained in the X-ray mode-resolved analysis (see Fig. [3](#fig:timeseries2) and Table [\[tab:flares\]](#tab:flares)), where the emission is averaged over longer time intervals. We observed a significant increase in the peak intensity above the average level: a factor of $\sim$4 for Flare 1 and a factor of $\sim$7 for Flare 2.

We observed a clear change in the morphology of the millimetre continuum emission during the two flaring episodes (see the white contours in Fig. [7](#fig:flares)). The 2D Gaussian fitting (see Table [\[tab:flares\]](#tab:flares)) indicates that the emission is elongated along the north-east to south-west direction during Flare 1 (roughly perpendicular to the ALMA 3.1 mm emission obtained with all the visibilities), while it is marginally resolved in only one direction during Flare 2.

The nominal rms absolute positional accuracy for standard ALMA observations can be estimated as $beam_{\rm FWHM} \times (0.9 \times {\rm S/N})^{-1}$ [^13], where $beam_{\rm FWHM}$ is the full width at half maximum synthesised beam in arcsec and S/N is the signal-to-noise ratio of the image target. The positional accuracy for Flare 1 is $\simeq0.12-0.15''$, while for Flare 2 it is slightly smaller at $\simeq0.1''$. However, the actual absolute positional accuracy may be worse than the nominal values, potentially by a factor of 2 or more, depending on the atmospheric phase conditions during the observation. The offset between the ALMA peak positions and the radio position (cite: deller12) is $\simeq$0.4$''$ for Flare 1 and $\simeq$0.3$''$ for Flare 2. Given the stable weather conditions during the observation, it is possible that this offset is genuine for both flares. However, caution must be exercised, as this offset is comparable to the positional accuracy of ALMA.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| X-ray mode | $\Gamma$$^{\rm a}$ | $F_{\rm X}$$^{\rm b}$ | $I_{\nu}$ | $S_{\nu}$ | Deconvolved Size | P.A |
|  |  | (10$^{-12}$ erg cm$^{-2}$ s$^{-1}$) | ($\mu$Jy beam$^{-1}$) | ($\mu$Jy) | $(''\times'')$ | ($^{\circ}$) |
| High | $1.66\pm0.03$ | $13.8\pm0.2$ | $74\pm6$ | $89\pm13$ | (0.338$\pm$0.202)$\times$(0.250$\pm$0.044) | 105$\pm$8 |
| Low | $1.7\pm0.1$ | $2.1\pm0.2$ | $117\pm11$ | $134\pm23$ | (0.384$\pm$0.245)$\times$(0.260$\pm$0.125) | 141$\pm$45 |

**Notes.** $^{\rm a}$ Best-fitting photon index for the absorbed power-law model. $^{\rm b}$ Unabsorbed flux over the 0.3–10 keV energy band.

![](alma-flares.pdf)

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Flare | R.A (ICRS) | Dec. (ICRS) | $I_{\nu}$$^{\rm a}$ | $S_{\nu}$$^{\rm a}$ | Deconvolved Size | P.A |
|  | (hh:mm:ss) | ($^{\circ}$:$'$:”) | ($\mu$Jy beam$^{-1}$) | ($\mu$Jy) | ($''\times''$) | ($^{\circ}$) |
| Flare 1 | 10:23:47.705$\pm$0.006 | 00:38:40.92$\pm$0.11 | 426$\pm$26 | 1006$\pm$84 | (0.96$\pm$0.89)$\times$(0.40$\pm$0.10) | 13.3$\pm$6.9 |
| Flare 2 | 10:23:47.702$\pm$0.002 | 00:38:40.63$\pm$0.01 | 701$\pm$62 | 675$\pm$114 | …$^{\mathrm{b}}$ | …$^{\mathrm{b}}$ |

**Notes.** $^{\rm a}$ These values are measured at the peak of the flares over time intervals of length 15 s and are therefore higher than those obtained in the X-ray mode-resolved analysis and plotted in Fig. [3](#fig:timeseries2), where the emission is averaged over longer time intervals. $^{\rm b}$ Source marginally resolved in only one direction.

## Radio emission

### Continuum emission

The radio light curve extracted from VLA data is shown in Fig. [1](#fig:timeseries1). J1023 is not detected most of the time, especially during the high mode intervals. However, it is detected during almost all episodes of low mode (here the uncertainties on the flux densities are reported at the 1$\sigma$ confidence level). The average radio flux densities measured separately in the high and low mode are reported in Table [\[tab:SED\]](#tab:SED). These values are consistent with those reported by (cite: bogdanov18) within the uncertainties. This indicates that the radio flux densities measured separately in the two modes are remarkably stable over timescales of years.

### Non-detection of pulsed emission

The limit on the radio pulsed flux density derived from the FAST observations is a factor of $>$5000 smaller than the flux density measured at similar frequencies when J1023 was active as a radio pulsar (cite: Archibald2009) and a factor of a few tens more constraining than the limits previously evaluated (again at similar frequencies) as soon as J1023 transitioned to the sub-luminous X-ray state (cite: stappers14; patruno14). The limit on the radio pulsed flux density in the high mode is also at least four orders of magnitude smaller than the value predicted by extrapolating the best-fitting power-law model for the SEDs of the optical-to-X-ray pulsed emission (cite: papitto19; miravalzanon22).

## The low-mode ingress and egress timescales

We first examined the low mode ingress and egress times in the *XMM-Newton* observation. For each low-mode episode, we used a simple model for the count rate light curve consisting of four components: a constant level for the high mode (allowing for a different count rate at the entrance and at the exit of the low-mode episode), a linear ingress in the low mode, a constant count rate in the low mode, and a linear egress. This model is similar in some aspects to what is used to model eclipses in binary stars or planetary transits. While we do not expect to accurately describe each low-mode episode individually, we consider the results in a statistical sense.

We applied this model to each low-mode episode in the *XMM-Newton*/EPIC count rate light curve, which was binned at 10 s, excluding the initial flaring mode of the observation. We performed the same procedure on the NICER data from the second night, using again a 10 s time bin. We fit the model to 56 low-mode episodes for *XMM-Newton* and 10 for NICER.

As shown in Fig. [8](#fig:ingress_egress), the ingress time is shorter than the egress time from the low mode ($\sim 80\%$). Interestingly, we observe that the two low-mode instances detected in the NICER data and coinciding with short-duration flares detected by ALMA both have comparable ingress and egress times (see the left panel of Fig. [8](#fig:ingress_egress)). This is uncommon and may be related to the detectability of flares at millimetre wavelengths. The distributions of *XMM-Newton* low-mode ingress and egress times are shown in the right panel of Fig. [8](#fig:ingress_egress). The average logarithmic ingress time is $(10.4\pm6.9)$ s, which is consistent with the time binning. The average logarithmic egress time is $(30.6\pm8.2)$ s. We also investigated whether there was any relationship between ingress time, egress time, duration of the low mode, count rate at the beginning and end of the low mode, and count rate in the low mode. However, we did not find any statistically significant correlations.

Although the model we used to describe the low-mode episodes is simple, it is clear that the duration of the ingress time in the low mode is short and consistent with the adopted time binning, and the egress time from the low mode is measurable and longer.

![](ingress-egress.pdf)

# Discussion

## The physical picture

Our campaign, along with previous findings (see e.g. (cite: ambrosino17; bogdanov18; papitto19; miravalzanon22; illiano23) and references therein), allows us to draw a comprehensive physical picture of the high-low mode switches in J1023, which involves a permanently active rotation-powered pulsar, an accretion disc and episodes of discrete mass ejection on top of a compact jet. In the following, we outline the physical scenario while in Sect. [4.2](#sec:sed) we describe in detail the SED modelling in support of our scenario. Figure [9](#fig:sketch) shows a visual representation of our scenario. We do not discuss the flaring activity here as it was not covered over a wide energy range.

We assume that during the high mode the accretion flow is kept just beyond the light cylinder radius ($\simeq$80 km) by the radiation pressure of the particle wind from an active rotation-powered pulsar (cite: papitto19). This causes the innermost region of the truncated, geometrically thin accretion disc to be replaced by a radiatively inefficient, geometrically thick flow, as expected for low-accretion rates (cite: narayan94). In this configuration, synchrotron radiation at a shock front that forms where the pulsar wind interacts with the inner flow produces the bulk of the X-ray emission as well as X-ray, UV, and optical pulsed emission (cite: papitto19; veledina19). The collision of high-energy charged particles from the pulsar wind with the in-flowing matter in the disc increases the ionisation level of the disc. As a result, the in-flowing matter is drawn into the pulsar magnetic field and accelerated, producing a compact jet of plasma that streams out. According to our SED modelling, the corresponding jet synchrotron spectrum is optically thick up to the mid-infrared band and breaks to optically thin above a frequency of $(2.4^{+1.9}_{-1.0})\times 10^{13}$ Hz, giving only a small contribution at X-ray energies ($\sim$8–18% in the 0.3–10 keV band; see Fig. [10](#fig:SED) and Table [\[Tab:fit_res\]](#Tab:fit_res)).

The switch from the high to the low mode can be connected to the occurrence of short millimetre flares. There is strong evidence that at least one such flare is directly involved in triggering the switch (see Fig. [3](#fig:timeseries2)). We interpret these flares as the fingerprint of a discrete mass ejection that marks the removal of the inner flow (see Sect. [4.1.1](#sec:mmflares)), similar to what has been observed in other black-hole and NS XRBs (e.g. Cyg X-3, Circinus X-1, V404 Cygni, MAXI J1535-571, and MAXI J1820+091; (cite: egron21; fender98; fender23; RussellT2019; Homan2020)), albeit in different accretion regimes. As soon as the inner flow is expelled in the discrete ejection, synchrotron emission from the shock no longer takes place, resulting in a drop of the X-ray flux and the quenching of X-ray, UV and optical pulsations. The system enters the low mode.

During the low mode, the pulsar wind can still penetrate the accretion disc, collide with the in-flowing matter, and launch the compact jet, contributing to the multi-band emission in the same way as in the high mode. The X-ray emission is likely to be (almost) entirely from optically thin synchrotron radiation from this jet (Fig. [10](#fig:SED), right panel), with a power-law index of $\alpha = -0.78\pm0.04$ (where the flux density $F_{\nu}$ scales with the observing frequency $\nu$ as $F_{\nu}\propto \nu^{\alpha}$; see Table [\[Tab:fit_res\]](#Tab:fit_res)). At the same time, the emission associated with the discrete ejection progressively shifts towards lower frequencies as the ejected material expands adiabatically during the low mode and quickly evolves from optically thick to optically thin (cite: bogdanov18). This emission component has a steep spectrum ($\alpha = -0.8_{-0.4}^{+0.3}$) and provides an additional flux contribution above that of the underlying optically thick emission from the compact jet at frequencies below the millimetre band (see Figs. [1](#fig:timeseries1) and [3](#fig:timeseries2)).

Eventually, the flow from the disc starts to refill the inner regions just outside the NS light cylinder on a thermal timescale (tens of seconds) due to its advection-dominated nature. The refilling of the disc re-establishes the region of shock with the pulsar wind, leading to increased emission and pulsations at X-ray, UV, and optical frequencies (cite: papitto19; miravalzanon22; illiano23). The system thus makes a switch back to the high mode.

As shown in Sect. [3.6](#sec:lowmode_times), the low mode ingress and egress times show a statistically significant difference, with the average egress time being longer than the average ingress time. In our picture, the ingress in the low mode is caused by the ejection of the innermost regions of the disc. This will occur on a dynamic timescale. We can estimate the distance at which the innermost edge of the disc in J1023 must recede away from the NS at the high-to-low mode switch by assuming that most of the X-ray emission in the low mode is due to the jet and hence imposing that the luminosity of the synchrotron emission at the shock front is at most, say, 10% of that observed in the low mode. This gives a radial distance of $r_{\rm low} = [L_{\rm sd}/(0.1L_{\rm X,low})]^{0.5}r_{\rm LC} \approx20\,r_{\rm LC} \approx$1600 km ($L_{\rm sd}=4.43\times10^{34}$ erg s$^{-1}$ is the spin-down luminosity; (cite: archibald13)). This value should be considered as a lower limit: at larger radii, the X-ray luminosity due to the shock would be even smaller. The dynamic timescale is $\sqrt{r^3/(GM)}\sim 0.1$ s at $20\,r_{\rm LC}$. Observations from *XMM-Newton* and NICER show that current X-ray instruments are capable of probing mode switching in J1023 on timescales as short as $\sim$10 s. In the future, proposed X-ray missions that offer instruments with much larger collecting areas, high throughput, and excellent time resolution, such as the New Advanced Telescope for High-ENergy Astrophysics (*NewAthena*; (cite: nandra13)), the enhanced X-ray Timing and Polarimetry mission (eXTP; (cite: Zhang2016)) and the Spectroscopic Time-Resolving Observatory for Broadband Energy X-rays (STROBE-X; (cite: ray19)), would be able to sample the switch on a timescale of $<$10 s and test our predictions.

The ejection and replenishment of the inner flow in J1023 during the switches from high to low mode and from low to high mode are reminiscent of the ejection of the X-ray corona into a jet and subsequent replenishment observed in the Galactic microquasar GRS 1915$+$105 (cite: mendez22). A previous study has demonstrated that, in the case of GRS 1915$+$105, the outer disc steadily refills the central part of the system on a viscous timescale (cite: Belloni1997). The rise time is the duration it takes for the heating front to propagate through the central disc. By assuming a subsonic velocity for the heating front, with the sound speed $c_S$ calculated in the cool ($\lesssim 6\times 10^6$  K) disc state, we can estimate the rise time to be $r_{\rm low}/c_S\approx 20$ s for J1023.

In the above picture, we have assumed that the emission from the compact jet remains relatively constant over time, but it is also possible that the jet could be partially disrupted by the discrete ejection of plasma at the switch from high to low mode. However, if the ejection is not energetic enough to overcome the magnetic fields and pressures within the jet, or if it is not dense or well aligned enough to effectively interact with the jet, then the jet would quickly re-establish itself and appear as if it had never turned off. In either case, the jet would still contribute the same amount of flux in both modes, especially in the radio band where the emission is produced at greater distances from the NS (of the order of light-minutes to light-hours; (cite: Chaty2011)) and therefore any changes are on much longer timescales than the mode switching.

![image](High.png) ![image](Low.png)

### Millimetre flares as the fingerprint of discrete ejecta

Starting from the timescales of the first millimetre flare that occurred on the second night (which has more accurate start and end times than the second flare) and the typical timescales of the radio flares that occurred on the first night, we attempted to reproduce the light curves of similar flares by assuming they are caused by the motion and expansion of a blob of plasma accelerated near the pulsar. Following the work of (cite: fender19), we assumed that a typical discrete ejection expansion is well described by the van der Laan model (cite: vanderlaan1966)[^14]. Since no flare in this study was observed simultaneously at two different frequencies, we are unable to properly constrain the model parameters. However, we are able to check whether we could reproduce flares with peak flux densities and durations that are consistent with what we observed. We assumed that the blob is launched a few hundred kilometres away from the NS with a mildly relativistic velocity ($v\approx0.05$ $c$), and expands linearly over time. We also assumed a magnetic field that scales with the distance from the compact object as $B \propto R^{-1}$, with a magnetic field at the launching site of the order of 10$^5$ G (see Eq. 6 in (cite: papitto19) for an expression of the post-shock magnetic field of an isotropic pulsar wind). Additionally, we considered an electron number density of 10$^{11}$–10$^{12}$ cm$^{-3}$, which is consistent with the lower limit estimated from high-resolution X-ray spectroscopy (cite: cotizelati18a). Our calculations show that we can reproduce flares that last for a few seconds and reach a peak flux density of the order of 1 mJy at the ALMA Band-3 centroid frequency. Furthermore, these flares would result in flares that last for a few tens of seconds and reach a peak flux density of the order of 0.2 mJy at the VLA Band-X centroid frequency, as observed. These results are consistent with the predictions of the van der Laan model for an expanding blob of plasma.

Although we cannot firmly prove the true origin of the flares, we can ascribe the non-detection of flares in five out of the seven high-to-low-mode switches covered by ALMA to the variation in the intrinsic properties of the ejected material. These include the size, density, temperature, electron energy distribution, and opening angle of the ejected material. In general, smaller, less dense, and cooler ejecta that travel at slower bulk speeds tend to produce fainter millimetre emission (see e.g. (cite: tetarenko17; wood21)). Additionally, the distribution of the ejected material along the line of sight can also affect the detectability of millimetre flares through absorption and scattering effects (this is likely the main reason for the non-detection of pulsed radio emission as well; see Sect. [4.1.2](#sec:mass_transfer_rate)). Overall, a combination of these factors can explain the varying emission properties observed at millimetre and radio frequencies during (and following) different high-to-low-mode switches. These variations are likely to affect the time it takes for the inner flow to restore itself and produce the shock emission, resulting in the observed differences in duration among the individual low-mode episodes.

### The non-detection of radio pulsations

The non-detection of radio pulsations could be due to ‘intrinsic’ phenomena within the pulsar magnetosphere (i.e. irrespective of the presence of external drivers such as accreting material) such as intermittency and/or nulling (see e.g. (cite: weng22) for recent similar considerations for the system LS I $+$61 303). However, these phenomena were not observed during extensive radio timing campaigns when the system was in the radio pulsar state (e.g. (cite: archibald13; stappers14)), so they are unlikely to be the cause of the non-detection. Alternatively, the non-detection of pulsations may be due to the presence of matter enshrouding the system (see also (cite: cotizelati14; stappers14)). In this scenario, we can estimate a lower limit on the mass transfer rate from the companion star by requiring that the optical depth due to free-free absorption is larger than unity throughout the duration of the FAST observation. The analytical expression for the free-free optical depth is given by

$$\begin{equation}
\begin{split}
\MoveEqLeft
\tau_{\rm ff,1.25\,GHz}\simeq2.126\times10^{22}\times\\ &\times \frac{\dot{m}_{\rm C}^2 (M_{\rm NS}+M_{\rm C})^2 (X+0.5Y)^2 (9.157+2\ln T_4)}{T_4^{3/2}v_8^2 P_{\rm orb}^2 (M_{\rm NS}+0.538M_{\rm C})^3}~,
\label{eq:tauff}
\end{split}
\end{equation}$$where $\dot{m}_{\rm C}$ is the mass transfer rate in units of $M_{\odot}$ yr$^{-1}$, $M_{\rm NS}$ and $M_{\rm C}$ are the mass of the NS and the companion star, respectively, $X$ and $Y$ are the mass fraction of hydrogen and helium, respectively, $T_4$ is the plasma temperature in units of $10^4$ K, $v_8$ is the velocity of the particle wind in units of $10^8$ m s$^{-1}$ and $P_{\rm orb}$ is the orbital period in hours (cite: burgay03a; iacolina09). We assume $M_{\rm NS}$ = 1.65 $M_{\odot}$, $M_{\rm C}$= 0.24 $M_{\odot}$, $P_{\rm orb}$=4.75 h (cite: Archibald2009), $v_8$=1, $X$=0.7 and $Y$=0.3[^15], and $v_8$=1. In order to have $\tau_{\rm ff,1.25\,GHz}\simeq 1$, and therefore not detect the radio signal due to free-free scattering, we estimate $\dot{m}_{\rm C}\gtrsim10^{-11}$ $M_{\odot}$ yr$^{-1}\approx6\times10^{14}$ g s$^{-1}$. This value is a factor of $\gtrsim$10–60 larger than the mass accretion rate estimated based on a systematic analysis of the X-ray aperiodic variability of J1023 in the sub-luminous X-ray state (cite: linares22). This implies that a large fraction of the accreting mass does not reach the compact object’s surface and is instead ejected from the system. It is worth mentioning that the predicted mass transfer rate for J1023, based on the transfer of mass through the loss of orbital angular momentum, is $\sim 10^{-11}M_{\odot}\rm \, yr^{-1}$ (cite: verbunt93).

## Spectral energy distributions

### Data preparation

We extracted the SEDs separately in the high and low mode and fit them using a model that reflects the physical scenario proposed in Sect. [4.1](#sec:scenario).

The NIR, optical and UV data obtained on Night 2 were de-reddened assuming $A_V=0.17\pm 0.01$ mag, calculated from the *XMM-Newton* estimate of $N_{\rm H}$ using the $N_{\rm H}$/$A_V$ relation reported by (cite: Foight2016). The absorption coefficients in the other bands were estimated using the equations reported by (cite: cardelli89), and are listed in the last column of Table [\[tab:SED\]](#tab:SED).

For the low-mode SED, we considered optical data acquired between MJD (Modified Julian Day) 59392.01085 and 59392.01434, totaling three consecutive 60 s integration images in each band; the $J$-band flux is the average of the fluxes measured with NTT/SOFI while the source was in the low mode, according to our *XMM-Newton* monitoring; the UV (uvm2) flux was measured on MJD 59392.01302; radio flux densities are taken from the VLA observation from 2021 June 3–4; the millimetre flux density was derived from stacking all the ALMA images acquired during the low modes. No $K$-band observations have been acquired during the low mode. The unabsorbed X-ray flux was calculated as the average flux during all periods of low mode.

For the high-mode SED, we considered $K$-band data acquired between MJD 59392.00237 and 59392.00289, and then from MJD 59392.00593 to 59392.00832 (i.e. all the images in which J1023 is detected, $15\times15$ s); the $J$-band flux is the average of all the fluxes measured with NTT/SOFI while the source was in the high mode, according to our XMM-Newton monitoring; for the optical $griz$ bands, we considered one 60 s image for each band, at MJD 59392.00528; the UV (uvm2) flux was acquired on MJD 59392.00413; radio flux densities are taken from the VLA observation on 2021 June 3–4; the millimetre flux density was derived after stacking all the ALMA images acquired during the high mode episodes. The unabsorbed X-ray flux was calculated as the average flux during all periods of high mode.

ccccc Band & $\nu_c$ (Hz) & 2cFlux Density (mJy) & $A_{\nu}$ (mag)\
& & Low mode & High mode &\
Radio & $1.00\times 10^{10}$ & $0.158\pm 0.009$ & $0.064\pm0.006$ & –\
mm & $9.75\times 10^{10}$ & $0.133\pm0.023$ & $0.089\pm0.013$ & –\
$K$ & $1.40\times 10^{14}$ &– & $1.17\pm0.32$& $0.02\pm 0.03$\
$J$ & $2.39\times 10^{14}$ & $1.14\pm0.13$ & $1.12\pm0.16$ & $0.05\pm 0.03$\
$z$ & $3.28\times 10^{14}$ &$1.35\pm 0.28$ &$1.34\pm0.27$ & $0.08 \pm 0.01$\
$i$ & $3.93\times 10^{14}$ &$1.32\pm 0.23$ & $1.20\pm0.21$& $0.11\pm 0.01$\
$r$ & $4.81\times 10^{14}$ &$1.09\pm0.11$& $1.03\pm0.11$& $0.14\pm 0.01$\
$g$ & $6.29\times 10^{14}$ & $0.87\pm0.10$& $0.84\pm0.10$& $0.20\pm 0.01$\
$uvm2$ & $1.34\times 10^{15}$ & $0.10 \pm 0.01$ & $0.18\pm0.02$& $0.52\pm 0.01$\

\

### Model setup

*Low mode.* To perform the fit to the SED, we used a model comprising a blackbody of an irradiated star and a multi-colour accretion disc, together with a broken power law to describe the optically thick and thin components of the synchrotron emission from the compact jet. In addition, we considered a power law to model the optically thin emission from the discrete ejecta at all frequencies. For the stellar component, we considered an irradiated star model (see Eqs. 8 and 9 of (cite: chakrabarty98)) where the surface temperature of the star ($T_{*}$) is allowed to vary and the distance to J1023 ($D$), the radius of the companion star ($R_{\rm c}$), the binary separation ($a$), the irradiation luminosity ($L_{\rm irr}$) and the albedo of the star ($\eta_{*}$) are fixed to known (or reasonable) values: $D=1368$ pc (cite: deller12), $R_{\rm c}=0.43\, R_{\odot}$ (cite: Archibald2009), $\eta_{*}=0.1$, and $a=[G(M_{\rm NS}+M_{\rm C})P_{\rm orb}^2/(4\pi)^2]^{1/3}$, where $M_{\rm NS}=1.65M_{\odot}$ is the NS mass, $M_{\rm C}=0.24M_{\odot}$ is the mass of the companion star, $P_{\rm orb}=4.75$ hrs is the binary orbital period and $G$ is the gravitational constant. $L_{\rm irr}$ was fixed to $6.5\times10^{33}$ erg s$^{-1}$, the value estimated by (cite: shahbaz19) from the difference of the temperatures of the illuminated and dark sides of the companion star of J1023. This value corresponds to 14% of the pulsar spin-down luminosity (cite: archibald13), and is of the same order of magnitude as the X-ray and gamma-ray luminosities in the sub-luminous X-ray state. For the multi-colour accretion disc model (Eqs. 10–15 by (cite: chakrabarty98)), we allowed the inner radius of the accretion disc where the optical/UV emission becomes relevant ($r_{\rm in, opt/UV}$) to vary, while we fixed the X-ray albedo of the disc to 0.95 (cite: chakrabarty98) and the mass transfer rate to $10^{-11}M_{\odot}\rm \, yr^{-1}$. This is the value predicted for an XRB system with a short orbital period hosting a main-sequence star and transferring mass through loss of angular momentum (cite: verbunt93), and is consistent with the lower limit estimated from the non-detection of radio pulsations (Sect. [2.6](#sec:FAST)). The broken power-law component has the normalisation $F_0$, the two slopes $\alpha_1$ and $\alpha_2$ and the break frequency $\nu_{\rm break}$ as free parameters; the power law associated with the emission from the discrete ejecta has the normalisation $F_{\rm thin\, ,10}$ (calculated at a frequency of 10 GHz) and the slope $\alpha_{\rm thin}$ as free parameters.

![](SED.pdf)

cllrc Component & Parameter & 2cPosterior & Prior bounds\
& & Low mode & High mode &\
Irradiated star & $T_{*}$ (K) &&$T_{*} \sim \mathcal{N}(6128, 33)^{\ast}$\
Accretion disc & Log \[$r_{\rm in,opt/UV}$ / 1 cm\] & & $\rm Log\,r_{\rm in,opt/UV}\sim \mathcal{U}(7, 12)$\
Compact jet & Log \[$\nu_{\rm break}$ / 1 Hz\] & &$\rm Log\, \nu_{\rm break} \sim \mathcal{U} (10,14)$\
& $\alpha_1$ & &$\alpha_1\sim \mathcal{N}(0.2,0.2)^{\dagger}$\
& $\alpha_2$ & &$\alpha_2\sim\mathcal{N}(-0.7, 0.2)^{\dagger}$\
& Log \[$F_0$ / 1 mJy\] & &$\rm Log \, F_{0} \sim \mathcal{U}(-2, 0)$\
Shock emission & Log \[$\nu_{\rm sync}$ / 1 Hz\] &– & $14.34^{+0.44}_{-0.30}$&$\rm Log\, \nu_{\rm sync}\sim \mathcal{U}(12, 16)$\
& $\alpha_{\rm sync}$ & – & $-0.61\pm 0.01$&$\alpha_{\rm sync}\sim\mathcal{U}(-0.9, -0.4)$\
& Log \[$F_{\rm sync}$ / 1 mJy\] & – & $-1.11_{-0.27}^{+0.18}$&$\rm Log \, F_{\rm sync} \sim \mathcal{U}(-3, 2)$\
Discrete ejecta & $\alpha_{\rm thin}$ & $-0.78_{-0.43}^{+0.24}$ & –&$\alpha_{\rm thin}\sim \mathcal{U}(-1.5, 0)$\
& Log \[$F_{\rm thin\, ,10}$ / 1 mJy\] & $-1.03\pm 0.05$ & –&$\rm Log \, F_{\rm thin\, ,10} \sim \mathcal{U}(-5, 2)$\
& Bayesian p-value & 0.07 & 0.78 &–\

\

**Notes.** The median values of the posterior distributions of the model parameters are reported, along with lower and upper uncertainties. These uncertainties correspond to the 15.9th and 84.1th percentiles of the posterior distributions for each parameter. The last column reports the prior bounds that were used for all parameters; $\mathcal{N}(\mu, \sigma)$ is a normal distribution centred in $\mu$ and with variance $\sigma^2$, and $\mathcal{U}(a,b)$ is a uniform distribution in the $(a,b)$ interval. $^{\ast}$ Value from (cite: shahbaz22). $^{\dagger}$ Value from (cite: bogdanov18).

![](cornerplot.png)

*High mode.* We used a more complicated model following the physical picture explained above. In particular, we considered that the X-rays are produced by the sum of the optically thin component of the synchrotron emission from the base of the compact jet and the synchrotron emission from the region of shock between the pulsar wind and the inner flow. For the latter, we used the analytical expression for the synchrotron spectrum by (cite: chevalier98) (see his Eq. 1). For the emission at lower frequencies, we included the blackbody of the irradiated star (fixing $L_{\rm irr}$ to $6.5\times10^{33}$ erg s$^{-1}$), the multi-colour blackbody of the accretion disc, and the optically thick component of the synchrotron emission from the compact jet. The parameters of the fit are $T_{*}$, $\nu_{\rm break}$, $\alpha_1$, $\alpha_2$, $F_0$, $r_{\rm in,opt/UV}$, $\nu_{\rm sync}$, $\alpha_{\rm sync}$ and $F_{\rm sync}$, where $\nu_{\rm sync}$, $\alpha_{\rm sync}$, $F_{\rm sync}$ are the peak frequency of the synchrotron emission, the slope of the optically thin synchrotron emission and the normalisation of the synchrotron emission, respectively.

### Model fit

Employing both datasets (high and low mode), we performed an MCMC sampling of the posterior probability density function for the parameter space of the two models simultaneously (since some of the free parameters are shared by both models). We used a Gaussian prior for the temperature of the star centred on the value measured by (cite: shahbaz22) during the disc state, $T_*$ = ($6128\pm33$) K. Gaussian priors have also been used for the parameters $\alpha_1$ (centred on $0.2\pm0.2$) and $\alpha_2$ (centred on $-0.7\pm0.2$), following the results of (cite: bogdanov18). We note that we also tried wider Gaussian priors for these parameters, resulting in wider posterior distributions with medians compatible with the results below within 1–2$\sigma$. For all other parameters, we used uniform priors in very wide intervals to sample a large region of the parameter space (see the last column of Table [\[Tab:fit_res\]](#Tab:fit_res)). This is of great importance to minimise the probability that the actual source parameters fall outside the region sampled by the chosen priors.

### Results

The results of the fit are reported in Table [\[Tab:fit_res\]](#Tab:fit_res) and are summarised in the following paragraphs. All the parameters have been estimated as the median of the marginal posterior distributions, with $1\sigma$ credible intervals coming from the 16th–84th percentiles of the posterior distributions (see Fig. [11](#fig:cornerplot) for the histograms of the parameter samples).

Most of the marginal posterior distributions of the parameters shown in Fig. [11](#fig:cornerplot) are nearly Gaussian, meaning that they are almost symmetrical. Figure [11](#fig:cornerplot) also shows a strong correlation between $\nu_{\rm sync}$ and $F_{\rm sync}$, and between $F_0$ and $\alpha_1$. This is however not surprising considering the scarce number of points at the lowest frequencies and the impossibility to constrain quantities such as $\nu_{\rm break}$ and $\nu_{\rm sync}$, due to numerous overlapping components at infrared and optical frequencies. In particular, we note that $F_{\rm sync}$, $\nu_{\rm sync}$ and $\alpha_{\rm thin}$ have a non-symmetrical posterior distributions, with long tails towards the upper or the lower limit of the chosen interval for the prior, depending on the parameter. However, the peak of their distributions is well determined (see Fig. [11](#fig:cornerplot)). To estimate the goodness of the fit, we used the Bayesian p-value (reported in the last line of Table [\[Tab:fit_res\]](#Tab:fit_res); (cite: Lucy2016)). The p-value is 0.78 for the high mode and 0.07 for the low mode, meaning that the results of the fit are indeed acceptable (with a slight indication of overestimated and underestimated uncertainties for the high and low mode fit, respectively).

The synchrotron emission caused by the shock has a higher flux density in the optical band than the average pulsed flux density fraction of $\sim$1% estimated by (cite: papitto19), which makes our scenario plausible. In particular, we find that the shock contributes $\sim$3% of the emission in the optical band in the high mode, which is similar to the contribution of the optically thin component of the compact jet emission. In the *XMM-Newton*/EPIC 0.3–10 keV range, the shock accounts for $\sim$83% of the emission, while the jet only contributes $\sim$17% of the flux in the high mode.

## Optical polarisation measurements and predictions of X-ray polarisation

The average optical polarisation reported in this work is similar to levels previously measured for this source (cite: baglio16; hakala18). Since the polarisation level is $<$1%, it could have multiple origins. Given the lack of modulation of the Stokes parameters with the orbital period, it is unlikely that the source of the polarisation is scattering of radiation in any region of the system (such as the surface of the accretion disc), in contrast to previous suggestions (cite: baglio16). We identify two possible main emission mechanisms for the polarised emission, both of which are non-thermal: optically thin synchrotron emission from the compact jet, or synchrotron emission at the shock between the pulsar wind and the accretion inflow, which also gives rise to the observed optical pulsations (as also suggested by (cite: hakala18)). The jet flux density in the $r$-band is $\sim$0.02 mJy, corresponding to a fractional contribution to the total flux in the same band of $\sim$2.4% and $\sim$2% in the high and low modes, respectively. In the high mode, where the polarisation level measured in the $R$-band is 0.65$\pm$0.43%, this translates into a polarisation level of the jet emission of $\sim$26% (or $\sim$37% if the average polarisation level of 0.92% is considered instead). In the low mode, the jet emission is instead intrinsically polarised at a level of $\sim$17%. Following (cite: Shahbaz2019book) and references therein, we estimate a level of ordering of the magnetic field lines of $\sim$30% (considering the case of an optically thin synchrotron emission with a spectral slope of $\sim$-0.78, as obtained from our fit and averaging across modes; see Table [\[Tab:fit_res\]](#Tab:fit_res)). This indeed indicates a highly ordered magnetic field and suggests that tMSPs might have a more ordered magnetic field at the base of the jet than other NS and black hole XRBs (cite: russell08; baglio14; russell16; baglio20). Based on our picture, this could be ascribed to the presence of a continuous, steady flow of plasma near the pulsar, which may help maintain a more ordered magnetic field structure at the base of the jet.

Assuming that the observed optical polarisation is due to this emission component and that the same population of accelerated electrons in the jet produces optically thin synchrotron radiation at all frequencies above the break frequency, we can predict a polarisation level in the X-ray band – in the 2–8 keV energy range of the Imaging X-ray Polarimetry Explorer (IXPE; (cite: Weisskopf2016; soffitta21)) due to the jet of $\approx$17% in the low mode, where the jet contributes to $\sim$100% of the flux according to our SED modelling.

Alternatively, the observed optical polarisation might originate from synchrotron radiation at the region of shock between the pulsar wind and the accretion flow. In this scenario, polarisation should only be detected during the high mode. Unfortunately, the significance of our polarisation results obtained in the high and low modes separately is not high enough to verify this, as the results are compatible with each other within $1\sigma$ ($0.36^{+0.27}_{-0.35}\%$ in the low mode and 0.65$\pm$0.43% in the high mode). The fractional flux contribution of the shock in the $r$-band according to the SED modelling in the high mode is $\sim$4.8%, which translates into a LP of the emission of the shock of $\sim$15–20%, with peaks of up to 65–90% at the pulsations (in fact, the fraction of pulsed radiation is typically of $\sim$1%; (cite: papitto19)). This prediction could be tested using next-generation optical high-time resolution polarimetric instruments (cite: Ghedina2022). In the X-rays instead, we predict a fractional flux contribution of the shock emission of $\sim$90% in the IXPE energy range, which converts into an intrinsic LP level of $\approx$12–17%. This could be detected in an IXPE observation of $\sim$460 ks (assuming J1023 spends 70% of the time in the high mode).

In both scenarios, the validity of these predictions depends on the assumption that the optical polarisation is solely caused by synchrotron radiation from the jet or shock. However, if the observed polarisation is due to a combination of these factors or if other processes are at play that are not being considered (such as scattering on the disc surface contributing to the modulation with a low S/N in our measurements), these predictions may need to be revised.

## The millimetre continuum emission of J1023 and other X-ray binary systems

We have reported the detection of millimetre continuum emission for the first time from J1023 (and from a tMSP in general) using ALMA observations at $\approx$100 GHz. The millimetre emission is unresolved, implying a size for the emission region smaller than $\approx6\times10^{15}$ cm (this corresponds to $\approx7\times10^{4}$ times the orbital separation of the system; (cite: archibald13)). Millimetre/sub-millimetre continuum emission has been firmly detected from a number of transiently accreting stellar-mass black holes (cite: paredes00b; ogley00; fender00; fender01; ueda02; russell13; vanderhorst13; tetarenko15; tetarenko17; tetarenko19; russell20; dehaas21; koljonen21; tetarenko21; diaztrigo21) and in three accreting NSs so far: the persistent systems 4U 1728$-$34 and 4U 1820$-$30 (cite: diaztrigo17) and the transient accreting millisecond pulsar Aql X-1 (cite: diaztrigo18). In these cases, however, such emission has been detected during accretion states that are seemingly different from the X-ray sub-luminous disc state attained by J1023 at the epoch of our ALMA observations, as detailed below.

In black hole systems, millimetre continuum emission is typically detected during the rising phase of an X-ray outburst or along the outburst decay, during the ‘hard’ X-ray spectral state. In this state, the X-ray emission is typically dominated by a power-law component that is believed to arise from Compton up-scattering of soft disc photons by a population of hot thermal electrons located either in the innermost region of the accretion flow or in an extended cloud above the disc (for a recent review, see (cite: motta21)). At low frequencies, a flat to slightly inverted optically thick spectrum ($\alpha>0$) has been observed from radio through sub-millimetre frequencies and above and has been associated with partially self-absorbed synchrotron radiation from electron populations in different regions along a compact jet. This spectrum becomes optically thin ($\alpha<0$) typically around infrared frequencies, resulting in a spectral break (cite: russell13a; russell13b). On the other hand, at very high mass accretion rates (typically close to the outburst peak), these systems can be in a ‘soft’ X-ray spectral state where the X-ray emission is dominated by a thermal component produced in the hot inner regions of the accretion disc (see (cite: motta21) and references therein). In the state that immediately precedes or follows the soft state during the outburst (the so-called soft-intermediate state), the optically thick jet emission is observed to be quenched altogether, while discrete jet ejecta characterised by an optically thin steep spectrum ($\alpha<0$) in the radio band can be launched (cite: fender04; russell20) and be accompanied by strong radio variability and bright multi-frequency flaring activity (even in the sub-millimetre band; (cite: tetarenko19)).

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Source | Distance | Millimetre luminosity$^{\rm a}$ | X-ray luminosity$^{\rm b}$ | Reference |
|  | (kpc) | (erg s$^{-1}$) | (erg s$^{-1}$) |  |
| MAXI J1659$-$152 | 6 | (7$\pm$1)$\times$10$^{31}$ | (1.389$\pm$0.001)$\times$10$^{37}$ | (cite: vanderhorst13) |
| MAXI J1659$-$152 | 6 | (5$\pm$1)$\times$10$^{31}$ | (4.60$\pm$0.01)$\times$10$^{37}$ | (cite: vanderhorst13) |
| MAXI J1659$-$152 | 6 | $<$2.6$\times$10$^{31}$ | (4.81$\pm$0.01)$\times$10$^{37}$ | (cite: vanderhorst13) |
| MAXI J1659$-$152 | 6 | $<$2.7$\times$10$^{31}$ | (4.67$\pm$0.02)$\times$10$^{37}$ | (cite: vanderhorst13) |
| V404 Cygni | 2.39 | (3.64$\pm$0.06)$\times$10$^{30}$ | (8$\pm$2)$\times$10$^{34}$ | (cite: tetarenko19) |
| V404 Cygni | 2.39 | (9.4$\pm$0.6)$\times$10$^{29}$ | (1.5$\pm$0.1)$\times$10$^{34}$ | (cite: tetarenko19) |
| MAXI J1535$-$571 | 4.1 | (4.7$\pm$0.2)$\times$10$^{32}$ | (2.00$\pm$0.01)$\times$10$^{38}$ | (cite: russell20) |
| MAXI J1535$-$571 | 4.1 | (1.0$\pm$0.2)$\times$10$^{32}$ | (8.6$\pm$0.1)$\times$10$^{38}$ | (cite: russell20) |
| GX 339$-$4 | 8 | (1.53$\pm$0.08)$\times$10$^{31}$ | (1.35$\pm$0.08)$\times$10$^{36}$ | (cite: dehaas21) |
| MAXI J1820$+$070 | 2.96 | (9.651$\pm$0.004)$\times$10$^{31}$ | (3.50$\pm$0.01)$\times$10$^{37}$ | (cite: tetarenko21) |
| GRS 1915$+$105 | 8.6 | 2.2$\times$10$^{31}$ | (2.07$\pm$0.03)$\times$10$^{37}$ | (cite: koljonen21) |
| GRS 1915$+$105 | 8.6 | 2.6$\times$10$^{31}$ | (2.69$\pm$0.01)$\times$10$^{37}$ | (cite: koljonen21) |
| XTE J1118$+$480 | 1.7 | 6.9$\times$10$^{30}$ | 2.4$\times$10$^{35}$ | (cite: fender01) |
| 4U 1820$-$30$^{\rm c}$ | 6.4 | (1.67$\pm$0.09)$\times$10$^{30}$ | (3.22$\pm$0.03)$\times$10$^{37}$ | (cite: diaztrigo17) |
| Aql X-1 | 5.2 | (2.06$\pm$0.08)$\times$10$^{30}$ | (1.73$\pm$0.01)$\times$10$^{37}$ | (cite: diaztrigo18) |
| Aql X-1 | 5.2 | (1.31$\pm$0.08)$\times$10$^{30}$ | (9.2$\pm$0.1)$\times$10$^{37}$ | (cite: diaztrigo18) |
| Aql X-1 | 5.2 | (2.44$\pm$0.09)$\times$10$^{30}$ | (6.65$\pm$0.07)$\times$10$^{36}$ | (cite: diaztrigo18) |
|  (mean) | 1.37 | (3.2$\pm$0.2)$\times$10$^{28}$ | (1.7$\pm$0.2)$\times$10$^{33}$ | This work |
|  (high) | 1.37 | (2.0$\pm$0.3)$\times$10$^{28}$ | (2.40$\pm$0.04)$\times$10$^{33}$ | This work |
|  (low) | 1.37 | (3.0$\pm$0.5)$\times$10$^{28}$ | (3.6$\pm$0.4)$\times$10$^{32}$ | This work |

\

**Notes.** Values are reported for those systems that have been clearly detected in the millimetre/sub-millimetre bands, have a known distance, and have simultaneous or nearly simultaneous millimetre/sub-millimetre and X-ray observations. Systems above the horizontal line are black hole systems, while those below the line are NS systems. $^{\rm a}$ Millimetre luminosities are evaluated at a frequency of 100 GHz. A flat spectrum was assumed to estimate the luminosity for those cases where the flux density is available at other frequencies in the literature, except for MAXI J1820$+$070 ($\alpha$=0.25) and 4U 1820$-$30 ($\alpha$=0.13). $^{\rm b}$ X-ray luminosities are evaluated over the 1–10 keV energy range and are derived from *Swift*/XRT observations except for the case of J1023, for which values are taken from Table [\[tab:mode_properties\]](#tab:mode_properties). Spectra were extracted using the *Swift*/XRT data products generator (cite: evans09) and fitted using an absorbed power-law model. For the second pair of simultaneous observations of GRS 1915$+$105, the X-ray luminosity is evaluated using NICER Obs. ID 2596010301. $^{\rm c}$ The millimetre and X-ray observations were separated by 4 days.

![](lmlx.png)

The picture for NS systems is more diverse (see (cite: vandene21) for a recent overview). All three of the above-mentioned NS systems were observed in the millimetre band with ALMA, along with observations at other frequencies, in regimes of high mass accretion rates ($L_X>5\times10^{36}$ erg s$^{-1}$). 4U 1728$-$34 was observed during a transition from a hard to a soft state. The low-frequency spectrum was compatible with synchrotron emission from a compact jet and also revealed the presence of a break from optically thick to optically thin synchrotron radiation at frequencies in the range 10$^{13}$ – 10$^{14}$ Hz. In the case of 4U 1820$-$30, enhanced millimetre emission was detected during a soft X-ray state (the first time millimetre emission has been observed for an accreting NS in the soft state). The spectrum from the radio to the sub-millimetre bands was slightly inverted and showed no evidence for the presence of a spectral break (cite: diaztrigo17). This indicates emission from a compact jet and supports earlier findings that jets in NS systems do not all appear to be completely suppressed in soft accretion states (cite: migliari04). Aql X-1 was observed five times using ALMA over a time span of $\sim$1.5 months during the decay phase of an X-ray outburst in 2016, covering multiple transitions between distinct accretion states. The spectrum from the radio to the millimetre bands was again compatible with emission from a compact jet and, for the first time in an accreting NS in a low-mass XRB, a break in the SED was detected at a frequency that varies dramatically depending on the accretion state. Specifically, the break frequency initially decreased from $\sim$100 GHz to less than $\sim$5 GHz during a transition from a hard to a soft state, and then increased again up to a frequency within the range $\sim$30–100 GHz during a transition to a hard state at later stages of the outburst decay (cite: diaztrigo18).

Unlike all the cases mentioned above, the ALMA observations of J1023 were performed at an epoch when the system did not display any changes in its spectral state and was lingering in a sub-luminous X-ray state ($\approx$10$^{33}$ erg s$^{-1}$). It is worth noting that both the average and the mode-resolved X-ray spectra of J1023 have always been hard and have not shown any substantial changes over the past ten years or so during the sub-luminous X-ray state.

We can compare the millimetre and X-ray luminosities of J1023 with those measured for black-hole and NS systems using quasi-simultaneous millimetre and X-ray observations. These luminosities are reported in Table [\[tab:mmxray\]](#tab:mmxray) and plotted in Fig. [12](#fig:mmxray). Despite the relatively low amount of existing millimetre/sub-millimetre data for XRBs, Fig. [12](#fig:mmxray) shows that millimetre continuum emission has been detected in systems that attain a wide range of X-ray luminosities ($\sim$10$^{33}$–10$^{39}$ erg s$^{-1}$) and that J1023 currently holds the record as the faintest XRB firmly detected in the millimetre band.

The mechanism responsible for the X-ray emission in the two modes in J1023 is clearly different from that at work in black hole systems in the hard state, so a proper comparison cannot be made. With this in mind, we assessed how the position of J1023 on the $L_{\rm mm}$ – $L_{\rm x}$ plane compares with those of black hole systems by parameterised the dependence of $L_{\rm mm}$ upon $L_{\rm x}$ as a relation of the form ${\rm Log}L_{\rm mm} - {\rm Log}L_{\rm mm,ave} = \alpha + \beta({\rm Log}L_{\rm X} - {\rm Log}L_{\rm X,ave})$[^16]. We then investigated the shape of the $L_{\rm mm}$ – $L_{\rm x}$ correlation for black hole systems by performing a Bayesian-based MCMC sampling of the black hole data (including upper limits) using the linear regression algorithm LINMIX$_-$ERR (cite: kelly07). There are three free parameters: the intercept $\alpha$, the slope $\beta$ and $\sigma_0$, a parameter that accounts for an intrinsic random (Gaussian) scatter of the values around the best-fit model. We calculated the median values of the fit parameters from 10$^4$ draws from the posterior distribution, and determined the 1$\sigma$ credible intervals of these parameters using the 16th–84th percentiles of the posterior distributions. We derived $\alpha= -0.04\pm0.15$, $\beta= 0.46\pm0.09$ and $\sigma_0=0.18\pm0.13$. The best-fitting slope is consistent with that derived for the $L_{\rm radio}$ – $L_{\rm x}$ correlation for black hole systems (cite: gallo18) within the uncertainties. Figure [12](#fig:mmxray) shows the best-fitting slope (black dashed line) and the region on the plane where the values of $L_{\rm mm}$ and $L_{\rm X}$ are located at a distance of less than 3$\sigma$ from the best-fitting slope (grey shaded area). This figure shows that, during the low mode, J1023 follows the same correlation as black hole systems in the hard state (cite: bogdanov18).

# Summary and conclusions

We have presented the results of the largest multi-wavelength campaign ever conducted on the tMSP . This campaign took place in June 2021 while the system was in an active low-luminosity X-ray disc state. Our key findings can be summarised as follows:

$\bullet$ On the first night of observations, flaring activity was detected at X-ray and optical wavelengths, followed by mode-switching behaviour in X-rays. The UV emission was significantly fainter in low mode, while the radio continuum emission was brighter. No evidence of pulsed radio emission was detected in either mode. Our observations provide the most stringent limits on the pulsed radio flux density to date.

$\bullet$ On the second night of observations, a low-significance variation in the optical polarised signal was detected during mode changes, with a slightly higher LP level in the high mode compared to the low mode. The millimetre emission did not strictly follow the X-ray low modes, except for two brief flares. One of these flares occurred at the high-to-low mode switch, while the exact onset time of the other flare could not be determined due to a lack of observational coverage.

$\bullet$ These results allow us to draw a physical picture of high-low mode switches in J1023, which involves a rotation-powered pulsar, an accretion disc, and discrete mass ejections on top of a relativistic compact jet. During the high mode, synchrotron radiation at the shock front between the pulsar wind and the inner accretion flow produces most of the X-ray emission, as well as X-ray, UV, and optical pulsations. The switch to low mode is triggered by discrete mass ejections, resulting in a drop in the X-ray flux and a quenching of pulsations. During the low mode, the pulsar wind still penetrates the accretion disc and launches a compact jet, contributing to the multi-band emission in the same way as in the high mode. Eventually, the flow from the disc refills the inner regions outside the NS light cylinder, leading to increased emission and pulsations at X-ray, UV, and optical frequencies. The system then switches back to the high mode. This scenario is supported by the modelling of the SEDs extracted separately during the high and low modes.

$\bullet$ Relativistic pulsar winds can shape the structure and dynamics of accretion flows in XRB systems that contain quickly spinning NSs and can be used to probe emission mechanisms in tMSPs and other XRB systems.

$\bullet$ Black hole systems and tMSPs share intriguing similarities in their phenomenological properties, which emphasises the need for further research to deepen our understanding of accretion physics in compact objects.

These results show how multi-wavelength campaigns that combine diverse observational techniques provide powerful tools for unravelling the nature of elusive objects such as tMSPs.

# Acknowledgements

We thank the referee for helpful comments. We thank the ALMA staff, particularly Edwige Chapillon, for the help with scheduling the observations; the NICER PI, Keith Gendreau, for approving our ToO request and the operation team for executing the observations; Brad Cenko and the *Swift* duty scientists and science planners, for making the *Swift* Target of Opportunity observation possible; Nando Patat, for the help with scheduling the NTT/SOFI observations; Giulia Illiano, for providing checks on timing analysis of X-ray data; Rob Fender, for providing useful notebooks on synchrotron radiation from variable radio sources; Nanda Rea, for helpful comments on the manuscript.\
The results reported in this study are based on observations obtained with XMM-Newton (PI: Campana); NuSTAR (PI: Campana); the NASA/ESA Hubble Space Telescope (obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program 16061; PI: Campana); FAST (PI: Hou); the REM Telescope, INAF Chile (PI: Baglio). Part of the observations presented in this study were obtained at the European Southern Observatory under ESO programme 107.22RK.001 (PI: Baglio). This paper makes also use of the following ALMA data: ADS/JAO.ALMA#2019.A.00036.S (PI: Coti Zelati). *XMM-Newton* is an European Space Agency (ESA) science mission with instruments and contributions directly funded by ESA member states and NASA. *NuSTAR* is a project led by the California Institute of Technology, managed by the Jet Propulsion Laboratory and funded by NASA. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. FAST is a Chinese national mega-science facility, operated by National Astronomical Observatories of the Chinese Academy of Sciences (NAOC). NICER is a 0.2–12 keV X-ray telescope operating on the International Space Station, funded by NASA. The Neil Gehrels Swift Observatory is a NASA/UK/ASI mission. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.\
The XMM-Newton SAS is developed and maintained by the Science Operations Centre at the European Space Astronomy Centre. The NuSTAR Data Analysis Software (NuSTARDAS) is jointly developed by the ASI Science Data Center (ASDC, Italy) and the California Institute of Technology (Caltech, USA).\
The data that support the findings of this study are publicly available at their respective online archive repositories (*XMM-Newton*: <http://nxsa.esac.esa.int/nxsa-web/>; NICER: <https://heasarc.gsfc.nasa.gov/FTP/nicer/data/obs>; *NuSTAR*: <https://heasarc.gsfc.nasa.gov/W3Browse/all/numaster.html>; *Swift*: <https://heasarc.gsfc.nasa.gov/cgi-bin/W3Browse/w3browse.pl>; HST: <http://hst.esac.esa.int/ehst/>; VLA: <https://data.nrao.edu/portal/>; VLT/FORS2: <http://archive.eso.org/scienceportal/>; ALMA: <http://almascience.nrao.edu/aq/>; REM: <http://ross.oas.inaf.it/REMDB/public.php>; NTT/SOFI: <http://archive.eso.org/scienceportal/>). FAST data can be accessed through the FAST Data Center: <https://fast.bao.ac.cn/cms/article/11/>.\
FCZ is supported by a Ramón y Cajal fellowship (grant agreement RYC2021-030888-I) and Catalan grant SGR-Cat 2021 (PI: Graber). FCZ and DFT are supported by the program Unidad de Excelencia María de Maeztu CEX2020-001058-M. FCZ, SCa, PD’A, FA, PC, DdM and AP acknowledge financial support from INAF-Fundamental research astrophysics project “Uncovering the optical beat of the fastest magnetised neutron stars” (FANS; PI: AP). SCa, SCo and PD’A acknowledge support from ASI grant I/004/11/5. GB acknowledges support from the PID2020-117710GB-I00 grant funded by MCIN/ AEI /10.13039/501100011033. AMZ is supported by PRIN-MIUR 2017 UnIAM (Unifying Isolated and Accreting Magnetars, PI S. Mereghetti). XH is supported by the National Natural Science Foundation of China through grant No. 12041303. JL is supported by the National Natural Science Foundation of China through grant No.12273038. DdM and AP acknowledge financial support from the Italian Space Agency (ASI) and National Institute for Astrophysics (INAF) under agreements ASI-INAF I/037/12/0 and ASI-INAF n.2017- 14-H.0, from INAF ‘Sostegno alla ricerca scientifica main streams dell‘INAF’, Presidential Decree 43/2018 and from INAF ‘SKA/CTA projects’, Presidential Decree 70/2016. DMR and DMB acknowledge the support of the NYU Abu Dhabi Research Enhancement Fund under grant RE124. DFT is supported by the grants PID2021-124581OB-I00 funded by MCIN/AEI/10.13039/501100011033, 2021SGR00426 of the Generalitat de Catalunya and by MCIN with funding from European Union NextGeneration EU (PRTR-C17.I1). MM acknowledges the research programme Athena with project number 184.034.002, which is (partly) financed by the Dutch Research Council (NWO) and thanks the Team Meeting at the International Space Science Institute (Bern) for fruitful discussions. FMV acknowledges support from the Spanish Ministry of Science for the grant PID2020–120323GB–I00 and for the FJC2020-043334-I grant financed by MCIN/AEI/10.13039/501100011033 and Next Generation EU/PRTR. This work was also partially supported by the COST Action ‘PHAROS’ (CA 16124).\
Software: APLPY v.2.1.0 (cite: robitaille12); Astropy v.5.3 (cite: astropy:2013; astropy:2018; astropy:2022); CASA v.6.5.2 (cite: casa); CIAO v.4.15 and CALDB v.4.10.4 (cite: fruscione06); CORNER PLOT v.2.2.1 (cite: corner); DAOPHOT (cite: Stetson1987), part of the Starlink software (cite: currie14; berry22); HEASOFT v.6.31.1 (cite: heasoft14); IRAF v.2.17 (<https://github.com/iraf-community/iraf>); LINMIX$_-$ERR (<https://github.com/jmeyers314/linmix>); MATPLOTLIB v.3.7.1 (cite: hunter07); NICERDAS v.10a; NUMPY v.1.24.0 (cite: harris20); NUSTARDAS, v.2.1.2; PRESTO v.4.0 (<https://github.com/scottransom/presto>); SAOImageDS9 v.8.4 (cite: joye03); SAS v.20.0 (cite: gabriel04); SCIPY v.1.10.1 (cite: scipy20); SRPAstro v.4.8.0 (<https://pypi.org/project/SRPAstro/>); XRONOS v.5.22 (cite: stella92); XSPEC v.12.13.0g (cite: arnaud96).\
Upon request, the corresponding authors (MCB and FCZ) will provide the code used to produce the figures.

147 natexlab

(ref: ahn14) Ahn, C. P., Alexandroff, R., Allende Prieto, C., et al. 2014, ApJS, 211, 17

(ref: ambrosino17) Ambrosino, F., Papitto, A., Stella, L., et al. 2017, Nat. Astron., 1, 854

(ref: andersen18) Andersen, B. C. & Ransom, S. M. 2018, ApJL, 863, L13

(ref: appenzeller98) Appenzeller, I., Fricke, K., Fürtig, W., et al. 1998, The Messenger, 94, 1

(ref: archibald15) Archibald, A. M., Bogdanov, S., Patruno, A., et al. 2015, ApJ, 807, 62

(ref: archibald13) Archibald, A. M., Kaspi, V. M., Hessels, J. W. T., et al. 2013, arXiv e-prints, arXiv:1311.5161

(ref: Archibald2009) Archibald, A. M., Stairs, I. H., Ransom, S. M., et al. 2009, Science, 324, 1411

(ref: arnaud96) Arnaud, K. A. 1996, in Astronomical Data Analysis Software and Systems V, Vol. 101, XSPEC: The First Ten Years, ed. G. H. Jacoby & J. Barnes (ASP, San Francisco), 17–20

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, aj, 156, 123

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: baglio16) Baglio, M. C., D’Avanzo, P., Campana, S., et al. 2016, A&A, 591, A101

(ref: baglio14) Baglio, M. C., Mainetti, D., D’Avanzo, P., et al. 2014, A&A, 572, A99

(ref: Baglio2018) Baglio, M. C., Russell, D. M., Casella, P., et al. 2018, ApJ, 867, 114

(ref: baglio20) Baglio, M. C., Russell, D. M., Crespi, S., et al. 2020, ApJ, 905, 87

(ref: baglio19) Baglio, M. C., Vincentelli, F., Campana, S., et al. 2019, A&A, 631, A104

(ref: Belloni1997) Belloni, T., Méndez, M., King, A. R., van der Klis, M., & van Paradijs, J. 1997, ApJL, 479, L145

(ref: berry22) Berry, D., Graves, S., Bell, G. S., et al. 2022, in Astronomical Society of the Pacific Conference Series, Vol. 532, Astronomical Society of the Pacific Conference Series, ed. J. E. Ruiz, F. Pierfedereci, & P. Teuben, 559

(ref: bogdanov15) Bogdanov, S., Archibald, A. M., Bassa, C., et al. 2015, ApJ, 806, 148

(ref: bogdanov18) Bogdanov, S., Deller, A. T., Miller-Jones, J. C. A., et al. 2018, ApJ, 856, 54

(ref: bogovalov99) Bogovalov, S. V. 1999, A&A, 349, 1017

(ref: briggs95) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology, United States

(ref: burgay03a) Burgay, M., Burderi, L., Possenti, A., et al. 2003, ApJ, 589, 902

(ref: burrows05) Burrows, D. N., Hill, J. E., Nousek, J. A., et al. 2005, Space Science Reviews, 120, 165

(ref: burtovoi20) Burtovoi, A., Zampieri, L., Fiori, M., et al. 2020, MNRAS, 498, L98

(ref: campana18b) Campana, S. & Di Salvo, T. 2018, in Astrophysics and Space Science Library, Vol. 457, Astrophysics and Space Science Library, ed. L. Rezzolla, P. Pizzochero, D. I. Jones, N. Rea, & I. Vidaña, 149

(ref: campana19) Campana, S., Miraval Zanon, A., Coti Zelati, F., et al. 2019, A&A, 629, L8

(ref: cardelli89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245

(ref: casa) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: chakrabarty98) Chakrabarty, D. 1998, ApJ, 492, 342

(ref: Chaty2011) Chaty, S., Dubus, G., & Raichoor, A. 2011, A&A, 529, A3

(ref: chevalier98) Chevalier, R. A. 1998, ApJ, 499, 810

(ref: cotizelati14) Coti Zelati, F., Baglio, M. C., Campana, S., et al. 2014, MNRAS, 444, 1783

(ref: cotizelati18a) Coti Zelati, F., Campana, S., Braito, V., et al. 2018, A&A, 611, A14

(ref: Covino1999) Covino, S., Lazzati, D., Ghisellini, G., et al. 1999, A&A, 348, L1

(ref: Covino2004) Covino, S., Zerbi, F. M., Chincarini, G., et al. 2004, Astronomische Nachrichten, 325, 543

(ref: currie14) Currie, M. J., Berry, D. S., Jenness, T., et al. 2014, in Astronomical Society of the Pacific Conference Series, Vol. 485, Astronomical Data Analysis Software and Systems XXIII, ed. N. Manset & P. Forshay, 391

(ref: dehaas21) de Haas, S. E. M., Russell, T. D., Degenaar, N., et al. 2021, MNRAS, 502, 521

(ref: deller12) Deller, A. T., Camilo, F., Reynolds, J. E., & Halpern, J. P. 2012, ApJL, 748, L1

(ref: deller15) Deller, A. T., Moldon, J., Miller-Jones, J. C. A., et al. 2015, ApJ, 809, 13

(ref: Serego) di Serego Alighieri, S. 1998, Cambridge University Press, 199, 287

(ref: diaztrigo18) Dı́az Trigo, M., Altamirano, D., Dinçer, T., et al. 2018, A&A, 616, A23

(ref: diaztrigo17) Dı́az Trigo, M., Migliari, S., Miller-Jones, J. C. A., et al. 2017, A&A, 600, A8

(ref: diaztrigo21) Dı́az Trigo, M., Petry, D., Humphreys, E., Impellizzeri, C. M. V., & Liu, H. B. 2021, A&A, 650, A37

(ref: egron21) Egron, E., Pellizzoni, A., Righini, S., et al. 2021, ApJ, 906, 10

(ref: evans09) Evans, P. A., Beardmore, A. P., Page, K. L., et al. 2009, MNRAS, 397, 1177

(ref: fender19) Fender, R. & Bright, J. 2019, MNRAS, 489, 4836

(ref: fender98) Fender, R., Spencer, R., Tzioumis, T., et al. 1998, ApJL, 506, L121

(ref: fender04) Fender, R. P., Belloni, T. M., & Gallo, E. 2004, MNRAS, 355, 1105

(ref: fender01) Fender, R. P., Hjellming, R. M., Tilanus, R. P. J., et al. 2001, MNRAS, 322, L23

(ref: fender23) Fender, R. P., Mooley, K. P., Motta, S. E., et al. 2023, MNRAS, 518, 1243

(ref: fender00) Fender, R. P., Pooley, G. G., Durouchoux, P., Tilanus, R. P. J., & Brocksopp, C. 2000, MNRAS, 312, 853

(ref: Foight2016) Foight, D. R., Güver, T., Özel, F., & Slane, P. O. 2016, ApJ, 826, 66

(ref: corner) Foreman-Mackey, D. 2016, The Journal of Open Source Software, 1, 24

(ref: fruscione06) Fruscione, A., McDowell, J. C., Allen, G. E., et al. 2006, in SPIE Conference Series, Vol. 6270, Observatory Operations: Strategies, Processes, and Systems, ed. D. R. Silva & R. E. Doxsey (SPIE, Bellingham), 62701V

(ref: gabriel04) Gabriel, C., Denby, M., Fyfe, D. J., et al. 2004, in Astronomical Data Analysis Software and Systems (ADASS) XIII, Vol. 314, The XMM-Newton SAS - Distributed Development and Maintenance of a Large Science Analysis System: A Critical Analysis, ed. F. Ochsenbein, M. G. Allen, & D. Egret (San Francisco, CA: ASP), 759

(ref: gallo18) Gallo, E., Degenaar, N., & van den Eijnden, J. 2018, MNRAS, 478, L132

(ref: Gandhi2009) Gandhi, P. 2009, ApJL, 697, L167

(ref: Gandhi2010) Gandhi, P., Dhillon, V. S., Durant, M., et al. 2010, MNRAS, 407, 2166

(ref: gehrels04) Gehrels, N., Chincarini, G., Giommi, P., et al. 2004, ApJ, 611, 1005

(ref: gendreau12) Gendreau, K. C., Arzoumanian, Z., & Okajima, T. 2012, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 8443, Space Telescopes and Instrumentation 2012: Ultraviolet to Gamma Ray, ed. T. Takahashi, S. S. Murray, & J.-W. A. den Herder, 844313

(ref: Ghedina2022) Ghedina, A., Ambrosino, F., Cecconi, M., et al. 2022, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 12184, Ground-based and Airborne Instrumentation for Astronomy IX, ed. C. J. Evans, J. J. Bryant, & K. Motohara, 121847U

(ref: hakala18) Hakala, P. & Kajava, J. J. E. 2018, MNRAS, 474, 3297

(ref: hales16) Hales, C. A. 2016, invgain v1.3

(ref: harris20) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: harrison13) Harrison, F. A., Craig, W. W., Christensen, F. E., et al. 2013, ApJ, 770, 103

(ref: Henden2019) Henden, A. A. 2019, Journal of the American Association of Variable Star Observers (JAAVSO), 47, 130

(ref: Hogg&Foreman2018) Hogg, D. W. & Foreman-Mackey, D. 2018, ApJS, 236, 11

(ref: Homan2020) Homan, J., Bright, J., Motta, S. E., et al. 2020, ApJL, 891, L29

(ref: hotan04) Hotan, A. W., van Straten, W., & Manchester, R. N. 2004, PASA, 21, 302

(ref: hunter07) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: iacolina09) Iacolina, M. N., Burgay, M., Burderi, L., Possenti, A., & di Salvo, T. 2009, A&A, 497, 445

(ref: illiano23) Illiano, G., Papitto, A., Ambrosino, F., et al. 2023, A&A, 669, A26

(ref: jansen01) Jansen, F., Lumb, D., Altieri, B., et al. 2001, A&A, 365, L1

(ref: jaodand21) Jaodand, A. D., Hernández Santisteban, J. V., Archibald, A. M., et al. 2021, arXiv e-prints, arXiv:2102.13145

(ref: jiang20) Jiang, P., Tang, N.-Y., Hou, L.-G., et al. 2020, Research in Astronomy and Astrophysics, 20, 064

(ref: jiang19) Jiang, P., Yue, Y., Gan, H., et al. 2019, Science China Physics, Mechanics, and Astronomy, 62, 959502

(ref: joye03) Joye, W. A. & Mandel, E. 2003, in Astronomical Society of the Pacific Conference Series, Vol. 295, Astronomical Data Analysis Software and Systems XII, ed. H. E. Payne, R. I. Jedrzejewski, & R. N. Hook, 489

(ref: kelly07) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: kennedy18) Kennedy, M. R., Clark, C. J., Voisin, G., & Breton, R. P. 2018, MNRAS, 477, 1120

(ref: koljonen21) Koljonen, K. I. I. & Hovatta, T. 2021, A&A, 647, A173

(ref: linares22) Linares, M., De Marco, B., Wijnands, R., & van der Klis, M. 2022, MNRAS, 512, 5269

(ref: Lucy2016) Lucy, L. B. 2016, A&A, 588, A19

(ref: manchester05) Manchester, R. N., Hobbs, G. B., Teoh, A., & Hobbs, M. 2005, AJ, 129, 1993

(ref: mason01) Mason, K. O., Breeveld, A., Much, R., et al. 2001, A&A, 365, L36

(ref: mendez22) Méndez, M., Karpouzas, K., Garcı́a, F., et al. 2022, Nature Astronomy

(ref: migliari04) Migliari, S., Fender, R. P., Rupen, M., et al. 2004, MNRAS, 351, 186

(ref: miravalzanon22) Miraval Zanon, A., Ambrosino, F., Coti Zelati, F., et al. 2022, A&A, 660, A63

(ref: moorwood98) Moorwood, A., Cuby, J. G., & Lidman, C. 1998, The Messenger, 91, 9

(ref: motta21) Motta, S. E., Rodriguez, J., Jourdain, E., et al. 2021, New A Rev., 93, 101618

(ref: nandra13) Nandra, K., Barret, D., Barcons, X., et al. 2013, arXiv e-prints, arXiv:1306.2307

(ref: narayan94) Narayan, R. & Yi, I. 1994, ApJL, 428, L13

(ref: heasoft14) Nasa High Energy Astrophysics Science Archive Research Center (Heasarc). 2014, HEAsoft: Unified Release of FTOOLS and XANADU

(ref: ogley00) Ogley, R. N., Bell Burnell, S. J., Fender, R. P., Pooley, G. G., & Waltman, E. B. 2000, MNRAS, 317, 158

(ref: papitto19) Papitto, A., Ambrosino, F., Stella, L., et al. 2019, ApJ, 882, 104

(ref: papitto22) Papitto, A. & de Martino, D. 2022, in Astrophysics and Space Science Library, Vol. 465, Astrophysics and Space Science Library, ed. S. Bhattacharyya, A. Papitto, & D. Bhattacharya, 157–200

(ref: papitto18) Papitto, A., Rea, N., Coti Zelati, F., et al. 2018, ApJL, 858, L12

(ref: paredes00b) Paredes, J. M., Martı́, J., Peracaula, M., Pooley, G., & Mirabel, I. F. 2000, A&A, 357, 507

(ref: patruno14) Patruno, A., Archibald, A. M., Hessels, J. W. T., et al. 2014, ApJL, 781, L3

(ref: qian20) Qian, L., Yao, R., Sun, J., et al. 2020, The Innovation, 1, 100053

(ref: ransom2001) Ransom, S. M. 2001, PhD thesis, Harvard University

(ref: ray19) Ray, P. S., Arzoumanian, Z., Ballantyne, D., et al. 2019, arXiv e-prints, arXiv:1903.03035

(ref: robitaille12) Robitaille, T. & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python

(ref: roming05) Roming, P. W. A., Kennedy, T. E., Mason, K. O., et al. 2005, Space Science Reviews, 120, 95

(ref: russell08) Russell, D. M. & Fender, R. P. 2008, MNRAS, 387, 713

(ref: russell13a) Russell, D. M., Markoff, S., Casella, P., et al. 2013a, MNRAS, 429, 815

(ref: russell13) Russell, D. M., Russell, T. D., Miller-Jones, J. C. A., et al. 2013b, ApJL, 768, L35

(ref: russell13b) Russell, D. M., Russell, T. D., Miller-Jones, J. C. A., et al. 2013c, ApJL, 768, L35

(ref: russell16) Russell, D. M., Shahbaz, T., Lewis, F., & Gallo, E. 2016, MNRAS, 463, 2680

(ref: russell20) Russell, T. D., Lucchini, M., Tetarenko, A. J., et al. 2020, MNRAS, 498, 5772

(ref: RussellT2019) Russell, T. D., Tetarenko, A. J., Miller-Jones, J. C. A., et al. 2019, ApJ, 883, 198

(ref: Saikia22) Saikia, P., Russell, D. M., Baglio, M. C., et al. 2022, ApJ, 932, 38

(ref: schartel22) Schartel, N., González-Riestra, R., Kretschmar, P., et al. 2022, XMM-Newton

(ref: Serkowski75) Serkowski, K., Mathewson, D. S., & Ford, V. L. 1975, ApJ, 196, 261

(ref: Shahbaz2019book) Shahbaz, T. 2019, in Astrophysics and Space Science Library, Vol. 460, Astronomical Polarisation from the Infrared to Gamma Rays, ed. R. Mignani, A. Shearer, A. Słowikowska, & S. Zane, 247

(ref: shahbaz18) Shahbaz, T., Dallilar, Y., Garner, A., et al. 2018, MNRAS, 477, 566

(ref: shahbaz22) Shahbaz, T., González-Hernández, J. I., Breton, R. P., et al. 2022, MNRAS, 513, 71

(ref: shahbaz15) Shahbaz, T., Linares, M., Nevado, S. P., et al. 2015, MNRAS, 453, 3461

(ref: shahbaz19) Shahbaz, T., Linares, M., Rodrı́guez-Gil, P., & Casares, J. 2019, MNRAS, 488, 198

(ref: soffitta21) Soffitta, P., Baldini, L., Bellazzini, R., et al. 2021, AJ, 162, 208

(ref: stappers14) Stappers, B. W., Archibald, A. M., Hessels, J. W. T., et al. 2014, ApJ, 790, 39

(ref: stella92) Stella, L. & Angelini, L. 1992, in Astronomical Society of the Pacific Conference Series, Vol. 25, Astronomical Data Analysis Software and Systems I, ed. D. M. Worrall, C. Biemesderfer, & J. Barnes, 103

(ref: Stetson1987) Stetson, P. B. 1987a, PASP, 99, 191

(ref: DAOPHOT) Stetson, P. B. 1987b, PASP, 99, 191

(ref: struder01) Strüder, L., Briel, U., Dennerl, K., et al. 2001, A&A, 365, L18

(ref: tetarenko21) Tetarenko, A. J., Casella, P., Miller-Jones, J. C. A., et al. 2021, MNRAS, 504, 3862

(ref: tetarenko19) Tetarenko, A. J., Sivakoff, G. R., Miller-Jones, J. C. A., et al. 2019, MNRAS, 482, 2950

(ref: tetarenko15) Tetarenko, A. J., Sivakoff, G. R., Miller-Jones, J. C. A., et al. 2015, ApJ, 805, 30

(ref: tetarenko17) Tetarenko, A. J., Sivakoff, G. R., Miller-Jones, J. C. A., et al. 2017, MNRAS, 469, 3141

(ref: turner01) Turner, M. J. L., Abbey, A., Arnaud, M., et al. 2001, A&A, 365, L27

(ref: ueda02) Ueda, Y., Yamaoka, K., Sánchez-Fernández, C., et al. 2002, ApJ, 571, 918

(ref: vandene21) van den Eijnden, J., Degenaar, N., Russell, T. D., et al. 2021, MNRAS, 507, 3899

(ref: vanderhorst13) van der Horst, A. J., Curran, P. A., Miller-Jones, J. C. A., et al. 2013, MNRAS, 436, 2625

(ref: vanderlaan1966) van der Laan, H. 1966, Nature, 211, 1131

(ref: vaughan94) Vaughan, B. A., van der Klis, M., Wood, K. S., et al. 1994, ApJ, 435, 362

(ref: vaughan03) Vaughan, S., Edelson, R., Warwick, R. S., & Uttley, P. 2003, MNRAS, 345, 1271

(ref: veledina19) Veledina, A., Nättilä, J., & Beloborodov, A. M. 2019, ApJ, 884, 144

(ref: verbunt93) Verbunt, F. 1993, ARA&A, 31, 93

(ref: scipy20) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nat. Methods, 17, 261

(ref: wang21) Wang, P., Li, D., Clark, C. J., et al. 2021, Science China Physics, Mechanics, and Astronomy, 64, 129562

(ref: Weisskopf2016) Weisskopf, M. C., Ramsey, B., O’Dell, S., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9905, Space Telescopes and Instrumentation 2016: Ultraviolet to Gamma Ray, ed. J.-W. A. den Herder, T. Takahashi, & M. Bautz, 990517

(ref: weng22) Weng, S.-S., Qian, L., Wang, B.-J., et al. 2022, Nature Astronomy, 6, 698

(ref: willingale13) Willingale, R., Starling, R. L. C., Beardmore, A. P., Tanvir, N. R., & O’Brien, P. T. 2013, MNRAS, 431, 394

(ref: wood21) Wood, C. M., Miller-Jones, J. C. A., Homan, J., et al. 2021, MNRAS, 505, 3393

(ref: woodgate98) Woodgate, B. E., Kimble, R. A., Bowers, C. W., et al. 1998, PASP, 110, 1183

(ref: Zerbi2001) Zerbi, R. M., Chincarini, G., Ghisellini, G., et al. 2001, Astronomische Nachrichten, 322, 275

(ref: Zhang2016) Zhang, S. N., Feroci, M., Santangelo, A., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9905, Space Telescopes and Instrumentation 2016: Ultraviolet to Gamma Ray, ed. J.-W. A. den Herder, T. Takahashi, & M. Bautz, 99051Q

# Searches for counterparts to ALMA J102349.1$+$003824

We searched for a counterpart to ALMA J102349.1$+$003824 at other wavelengths using both simultaneous and archival observations of the field. No UV emission was detected at the source position in the *Swift*/UVOT observations simultaneous with ALMA on the night of 2021 June 26–27, either in the images collected separately during the three snapshots or in the stack of these images. We set a 3$\sigma$ upper limit on the magnitude of a putative counterpart of UVM2$>$21 mag from the stacked image (total exposure of $\sim$2.4 ks). A few weeks before the ALMA observations were acquired, the FOV of ALMA J102349.1$+$003824 was also observed in the optical ($g'$, $r'$ and $i'$ SDSS filters) with the Las Cumbres Observatory (LCO) network of telescopes. No counterpart was detected in these data. We set the following 3$\sigma$ upper limits on the optical magnitude using 60 s images acquired with the 1m telescope of the LCO network located in South Africa on 2021 May 8: $i'>17.8$ mag, $r'>17.9$ mag, $g'>18.6$ mag. There is also no optical/NIR counterpart in either the third data release (DR3) from the *Gaia* space telescope or in the 2MASS point source catalogue. ALMA J102349.1$+$003824 was also not detected in the VLA observation carried out on 2021 June 3, down to a 3$\sigma$ flux density upper limit of 12 $\mu$Jy at 10 GHz.

Several observations of the field have been performed in the soft X-ray band over the past years, mainly using *Swift* and *XMM-Newton*. However, given the X-ray luminosity of J1023 and its small angular distance from ALMA J102349.1$+$003824 ($\sim$22$^{\prime\prime}$ ), the point-spread function of the X-ray instruments on board these observatories encompasses the position of ALMA J102349.1$+$003824, preventing a conclusive assessment of the presence or absence of an X-ray counterpart to this source. We then analysed a 83-ks long *Chandra*/ACIS-S (Advanced CCD Imaging Spectrometer) observation performed in March 2011 (Obs. ID 11075) to search for X-ray emission at the position of ALMA J102349.1$+$003824. We reprocessed the data using the task CHANDRA$_-$REPRO within the CIAO software and ran the WAVDETECT source detection tool. No evidence for an X-ray counterpart to ALMA J102349.1$+$003824 was found. Using SRCFLUX, we set a 3$\sigma$ upper limit on the net count rate of $1.3\times10^{-4}$ counts s$^{-1}$ over the 0.5–7.0 keV energy range. Assuming an absorbed power-law spectrum with an absorption column density of $N_{\rm H}$ = $5\times10^{20}$ cm$^{-2}$ (i.e. the one expected within the Galaxy in the direction of the source: (cite: willingale13)) and a photon index in the range $\Gamma$ = 1 – 4, the limit above translates into an unabsorbed flux of $< (2-4)\times10^{-15}$ erg cm$^{-2}$ s$^{-1}$ (depending on the assumed power-law slope) in the 0.5–7 keV range.

[^1]: The first two authors equally contributed to this work.

[^2]: <https://www.cosmos.esa.int/web/xmm-newton/sas-watchout-uvflux>

[^3]: This same procedure was also applied to the data collected with *NuSTAR*, *Swift* and NICER presented in the following.

[^4]: <https://github.com/Alymantara/stis_photons>

[^5]: <https://casper.astro.berkeley.edu/wiki/ROACH-2_Revision_2>

[^6]: The de-dispersion scheme was generated using the `DDplan.py` routine in the PulsaR Exploration and Search TOolkit pipeline (`presto`; (cite: ransom2001)).

[^7]: We followed the standard procedures outlined on the NICER data analysis webpage (<https://heasarc.gsfc.nasa.gov/docs/nicer/analysis_threads/>).

[^8]: <http://www.aavso.org/download-apass-data>

[^9]: <https://irsa.ipac.caltech.edu/applications/2MASS/IM/>

[^10]: [ https://www.eso.org/sci/facilities/paranal/instruments/fors/tools/FORS1_Std.html]( https://www.eso.org/sci/facilities/paranal/instruments/fors/tools/FORS1_Std.html)

[^11]: <http://www.eso.org/observing/dfo/quality/FORS2/reports/FULL/trend_report_PMOS_inst_pol_FULL.html>

[^12]: <https://casa.nrao.edu>

[^13]: See <https://almascience.eso.org/documents-and-tools/cycle10/alma-technical-handbook>, Sect. 10.5.2

[^14]: The calculations we made are based on (cite: vanderlaan1966) and are described in a Jupyter-notebook available at <https://github.com/robfender/ThunderBooks/blob/master/Basics.ipynb>

[^15]: We note that our assumption on $X$ and $Y$ should be regarded as a zeroth-order approximation since a recent study by (cite: shahbaz22) has shown that the chemical abundances of the companion star of J1023 are different from those found in most XRBs. However, since $\dot{m}_{\rm C} \propto (X+0.5Y)^{-1}$, the lower limit on $\dot{m}_{\rm C}$ only increases by a factor of a few if smaller values of $X$ and $Y$ are assumed.

[^16]: $L_{\rm mm,ave}=10^{31.93}$ erg s$^{-1}$ and $L_{\rm X,ave}=10^{38.03}$ erg s$^{-1}$ are the average values for the detections in our black hole sample.

</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "FAST 1.25 GHz 5sigma pulsed radio flux density upper limit (total) = 2.0 uJy",
  "failed_quote": "we derived a 5-$\\sigma$ flux density upper limit for persistent radio pulsations of 2.0$\\pm$0.5 $\\mu$Jy at 1.25 GHz considering the entire integration time of 2.8 hr"
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "No pulsed radio emission is present in either mode down to the most stringent limits to date, which is explained by free-free absorption from enshrouding material if the mass transfer rate is >= 10^-11 M_sun yr^-1, implying most transferred mass is ejected.",
  "failed_quote": "we derived a 5-$\\sigma$ flux density upper limit for persistent radio pulsations of 2.0$\\pm$0.5 $\\mu$Jy at 1.25 GHz considering the entire integration time of 2.8 hr"
 }
]
```
