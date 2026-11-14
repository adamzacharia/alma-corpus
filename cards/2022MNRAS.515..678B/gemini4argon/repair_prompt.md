# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022MNRAS.515..678B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
#  High-$z$ Sudoku: A diagnostic tool for identifying robust (sub)mm redshifts

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

# Abstract

We present methods to (i) graphically identify robust redshifts using emission lines in the (sub)mm regime, (ii) evaluate the capabilities of different (sub)mm practices for measuring spectroscopic redshifts, and (iii) optimise future (sub)mm observations towards increasing the fraction of robust redshifts. Using this publicly-available code (<https://github.com/tjlcbakx/redshift-search-graphs>), we discuss scenarios where robust redshifts can be identified using both single- and multiple-line detections, as well as scenarios where the redshift remains ambiguous, even after the detection of multiple lines. Using the redshift distribution of (sub)mm samples, we quantify the efficiencies of various practices for measuring spectroscopic redshifts, including interferometers, as well as existing and future instruments specifically designed for redshift searches. Finally, we provide a method to optimise the observation strategy for future (sub)mm spectroscopic redshift searches with the Atacama Large Millimetre/submillimetre Array, where 2 mm proves indispensable for robust redshifts in the $z = 2 - 4$ region.

methods: observational – techniques: spectroscopic – infrared: galaxies – galaxies: high-redshift

# Introduction

Since their discovery in the 1990’s (cite: Smail1997; Hughes1998), the extreme star-formation rates of sub-millimetre galaxies (SMGs) have been difficult to square with our picture of galaxy evolution (cite: blain2002; casey2014). Their strong emission in sub-mm wavelengths implied star-formation rates in excess of 1000 M$_{\odot}$/yr, approaching or exceeding the limits of stable galaxy systems through excessive feedback (cite: RowanRobinson2016), while their strong dust-obscuration poses serious challenges to large-scale unbiased follow-up attempts across all wavelengths (cite: ivison16; Casey2018; Donevski2018; Duivenvoorden2018; bakx2020VIKING; reuter20). Such large-scale unbiased follow-up is crucial, as studies find SMGs to consist of a diverse population (cite: Fardal2001; Baugh2005; Lacey2008; Gonzalez2011; narayanan2015).

A first step towards such follow-up requires precise and robust redshift measurements. Unfortunately, photometric redshifts from sub-mm colours remain only indicative of a redshift range (cite: casey2012; pearson13; ivison16; bakx18; Casey2020) due to the degeneracy between dust temperature and redshift (cite: Blain2003). Redshifts derived from spectroscopic lines break this degeneracy. The first redshift searches used optical spectral lines, however they struggled with the positional uncertainty of SMGs and with a limited bandwidth. Radio observations improved the positions, but provide a strong bias towards lower redshifts, and are not workable for large, complete redshift samples (cite: chapman2005). Instead, redshift searches using (sub)millimetre spectroscopy are unhindered by dust extinction and can be related unambiguously to the (sub)millimetre source, offering a far better alternative to optical spectroscopy and to the imprecise sub-mm photometric method (cite: weiss2009). The (sub)mm spectroscopic method has only become competitive with the increased bandwidths of the receivers operating at mm and sub-mm facilities, as for example demonstrated by (cite: Vieira2013) and (cite: weiss2013), who presented the first redshift survey for 23 strongly-lensed dusty star-forming galaxies selected from the South Pole Telescope (SPT) 2500 deg$^2$ survey using the Atacama Large Millimetre/submillimetre Array (ALMA) at 3 mm.

![](RSG_Fig1_annotated.png)

The large uncertainties of photometric redshifts and the lack of discerning spectral features of (sub)mm spectral lines (i.e., unlike the resonant, a-symmetric emission from Ly$\alpha$) complicate the spectroscopic redshift determination. Instead, the process of robust redshift determination at (sub)mm wavelengths, in particular using rotational emission lines from carbon-monoxide (CO), involves the careful comparison between the potential redshift solutions of individual lines, and then selecting the solution where multiple lines agree. This method is far from ideal, as it leads to confirmation bias for solutions close to the $z_{\rm phot}$ (cite: Yanai2020), and fails to draw attention to redshift degeneracies. Similarly, sometimes redshift solutions can be excluded if we fail to detect additional spectral lines within the bandwidth. In this paper, we expand on the graphical method from (cite: Bakx2020IRAM) which provides a more user-friendly method for identifying robust redshifts. This method is capable of highlighting redshift degeneracies, and enables the easy removal of untenable redshift solutions, similar to graphical-numerical puzzles, such as the Sudoku[^2] puzzle. We describe the method in detail in Section [2](#sec:GraphMethod), where we explain different scenarios and note important caveats. In Section [\[sec:redshiftSearches\]](#sec:redshiftSearches), we quantify the efficiency of various methods for finding spectroscopic redshifts, and provide a method for finding the optimum tunings for future redshift searches in Subsection [\[sec:OptimizedTunings\]](#sec:OptimizedTunings). The python-based code and example scripts for each of the graphs in this paper are publicly available at <https://github.com/tjlcbakx/redshift-search-graphs>, and can be easily and swiftly adapted for the reader’s own needs.

# Graphical method

Robust redshifts require the exclusion of any other potential redshift interpretations of the line emission except one. Numerically solving this cross-comparison is a tedious approach, prone to errors and overlooked options. Instead, we use the following graphical method for identifying the potential spectroscopic redshifts for each line. We further detail several redshift identification examples, and list several caveats with this method specifically and redshift searches in general.

## Explanation of the graphical method

In Figure [1](#fig:fig1), we show this graphical method for a fiducial $z_{\rm phot} = 3$ example source observed with an efficient ALMA tuning setup (see Section [\[sec:OptimizedTunings\]](#sec:OptimizedTunings)). Here, the observed frequency range (*y-axis*) is shown against the redshift range (*x-axis*) using the following approach:

1.  **Observed bandwidths:** Indicate the observed bandwidths, in this case shown as both the LSB and USB of the ALMA tunings.

2.  **Single- and multiple-line detection:** The observation is expected to detect the CO-lines (*black lines*), and might detect the \[C i\] and H$_2$O lines (*dashed blue lines*; see Section [2.3.2](#sec:excludingRedshiftRegions)). *Orange* and *blue fill* indicate where the observations would be able to observe one or more CO spectral lines, respectively.

3.  **Detected spectral lines:** Each actually-observed spectral line is indicated with a *horizontal line* at the observed frequency.

4.  **Potential line solutions:** Where the observed lines cross the redshifted spectral lines, a *circle* marks the potential spectroscopic redshift, with the circle’s fill representing the underlying colour. At the top of the graph, arrows indicate each potential spectroscopic redshift solution.

5.  **Robust redshift solution:** The top arrows line up when multiple lines agree on a robust redshift, identifying the spectroscopic redshift.

This final check is important, because CO-line redshift surveys can suffer from potential multiple redshift solutions (see Section [2.3.1](#sec:inconclusiveRedshifts) and Figure [4](#fig:fig4)), since the CO-ladder increases linearly with each transition J$_{\rm up}$. For example, the observation of J$_{\rm{up}}$ = 2 and 4 CO-line transitions of a z = 2 galaxy (76.7 and 153 GHz, resp.) could also be interpreted as the J$_{\rm{up}}$ = 3 and 6 CO-line transitions of a z $\approx$ 3.5 galaxy. This mis-identification is a non-negligible possiblity given the large 13% uncertainties in sub-mm derived photometric redshifts of around $\Delta z$ $\sim$ 1 (defined as $\Delta z / (1+z)$, e.g. (cite: pearson13; ivison16; bakx18)), although Bendo et al. in prep. finds a sharp reduction in uncertainty down to $\sim 7$%.

## Robust redshifts

### Robust redshifts from CO lines

Figure [1](#fig:fig1) shows the derivation of a spectroscopic redshift of $z_{\rm spec} = 2.7$, with two lines at 93.463 and 155.772 GHz, corresponding to CO(3-2) and CO(5-4) respectively. A high-$z$ redshift solution ($z_{\rm spec} = 6.4$) exists because of the linear spacing between CO line transitions and their isotopologues, but this solution would require additional lines at 109.04 and 140.195 GHz. The lack of such emission can be used to exclude this redshift possibility.

### Robust redshifts from CO and ancillary lines

![](RSG_Fig2.png)

Non-CO lines do not scale linearly with CO line emission, and thus always offer a robust derivation of the spectroscopic redshift. These lines are typically fainter than the CO emission, however they do offer the ability of near-guaranteed robust redshift identifications (see Sec. [2.3.2](#sec:excludingRedshiftRegions)). This is because the high fidelity of the central frequency (typically in excess of $f/\Delta f$ $\approx 10^2 - 10^{4}$) leaves no room for multiple interpretations. In Figure [2](#fig:fig2), we show this scenario for a fiducial $z_{\rm spec} = 2.45$ galaxy with observed CO(3-2) and CI(1-0) at 98.804 and 140.607 GHz respectively.

### Robust redshifts from single-line detections

![](RSG_Fig3.png)

These graphs allow us to visualize the bandwidth, and associated redshift possibilities that our observations have covered. As shown in Figure [3](#fig:fig3), if we detect a convincingly-bright line (see Section [2.3.2](#sec:excludingRedshiftRegions)) at 144.089 GHz using our efficient ALMA tuning (see Section  [\[sec:OptimizedTunings\]](#sec:OptimizedTunings)), we can exclude most neighbouring redshift solutions in the same vein as the exclusion of the $z_{\rm spec}= 6.4$ solution in Fig. [1](#fig:fig1). We would have detected lines at other frequencies for all but the lowest-redshift solution ($z_{\rm spec} = 0.6$). Using the photometric redshift as a guide, we can exclude this possibility, leaving only $z_{\rm spec} = 3.0$ as a solution, with the detected line being CO(5-4). We note that the $z_{\rm spec} = 2.41$ solution (where the detected line would be \[C i\]) would still require a CO line to be detected at 101.251 GHz.

## Caveats

### Inconclusive redshifts from multiple CO lines

![](RSG_Fig4.png)

Unfortunately, not all multi-line solutions can be excluded through the non-detection of other lines (such as in Fig. [1](#fig:fig1)). We show such a scenario in Figure [4](#fig:fig4), where two redshift solutions of two lines at 107.229 and 160.844 GHz can correspond to $z_{\rm spec} = 1.15$ or 3.30. The low-redshift scenario would detect CO(2-1) and CO(3-2), while the higher-redshift solution involves CO(4-3) and CO(6-5). Such scenarios occur when the ratio of the upper transition (J$_{\rm up}$) of both CO line transitions can be multiplied to form another set of integer numbers. In this case, the common multiplier is *two*, however extensive possibilities exist. We can quantify the change in redshift between a scenario where we either detected CO($a$, $a-1$) for one redshift solution or CO($b$, $b-1$) for the other redshift solution as follows $$\begin{equation}
    \frac{\Delta z}{1+z} = \frac{b-a}{a}. \label{eq:dz}
\end{equation}$$

The 1$\sigma$ uncertainty in $\Delta z / (1+z)$ is typically on the order of 13 % (cite: pearson13). In case the photometric redshift of a line agrees with a solution of CO($a$, $a-1$), the photometric redshift can thus identify how many standard-deviations ($N$) we are offset from a solution at CO($b$, $b-1$) using $$\begin{equation}
    N [\sigma] \approx \frac{b-a}{a \times{} 0.13}. \label{eq:Nsigma}
\end{equation}$$

In case of multiple detected lines, we can identify the nearest combination of lines that can be confused for one-another. Mathematically, this multiplier can be identified using the greatest common divisor, the $GCD$. The nearest solutions are the multiplication of the remaining components with $GCD \pm 1$. In the case of a tentative redshift based on CO(4-3) and CO(6-5), the largest common multiplier of the CO transitions (J$_{\rm up} = 4$ and 6, resp.) is 2, leaving additional redshift solutions using CO(2-1) and CO(3-2), as well as CO(6-5) and CO(9-8), typically offset by $\sim 3.8 \sigma$ \[$\approx (6 - 3)/(0.13 \times{} 6)$\]. Note that equation [\[eq:dz\]](#eq:dz) and [\[eq:Nsigma\]](#eq:Nsigma) do not differ on whether one takes the lower- or higher-frequency line, nor the lower- or higher-redshift possibility.

### Excluding redshift regimes

We can exclude redshift regions where we would have seen lines in a deep enough survey. These are typically restricted to CO lines, since the correlation between CO lines and \[C i\] emission strongly depends on the particular ISM conditions (see e.g., (cite: Valentino2018)). CO lines transitions, instead, are strongly correlated to one-another through transitional partition functions following so-called spectral line energy distributions (SLEDs). The Milky Way CO SLED has a sharp drop-off in velocity-integrated fluxes for J$_{\rm up}$ transitions greater than 3, however for star-bursting galaxies, these SLEDs can approach the *maximum* thermalized profile, where velocity-integrated fluxes increase with $J^2$ (see (cite: carilli2013)).

In the case of Fig. [1](#fig:fig1), we know the undetected CO lines should be at least on the same order of brightness as the detected lines, as their transitions are in between the detected emission lines. For the single-line case in Fig. [3](#fig:fig3), the $z_{\rm spec} = 2.2$ case would have, in the most unfortunate case, a CO(3-2) line with an integrated flux of $\sim 56$% (= 3$^2$/4$^2$) fainter than the detected line. Similarly, for the higher-redshift solution at $z_{\rm spec} = 3.8$, the CO(5-4) would be $\sim 70$% (= 5$^2$/6$^2$) as bright as the detected line. We show this analysis in graphical form in Figure [5](#fig:Fig5).

![](Fig5.png)

Taking into account measurement errors, as well as this line ratio, the exclusion method thus requires relatively-high signal-to-noise ($>8 \sigma$) detections to be robust. In Figure [5](#fig:Fig5) we show that such a 8$\sigma$ detection of a single spectral line is enough to exclude the potential redshift solution. We show the CO SLED of typical bright DSFGs from *Planck*-selected sources (cite: Harrington2021), a CO SLED from the Milky Way (cite: Fixsen1996), and the maximum expected excitation from a thermalized profile. We choose the *Planck*-selected CO SLED because it traces a large range of CO-transtions, from CO(1-0) to CO(12-11), while still being broadly representative of the population of DFSGs. The Milky Way CO SLED represents typical low-excitation gas, with a steep drop-off, while the thermalized profile reflects the maximum expected excitation. For both the high- and low-redshift possibilities, the upper-limit lies below the thermalized profile. As such, no typical SLED would be able to produce both a non-detection at a low-J, and a detection at a higher-J CO line.

### Disqualifying low-redshift interlopers

As a general rule, redshift deserts become more prevalent at lower redshifts (see the discussion in Section [\[sec:redshiftSearches\]](#sec:redshiftSearches)). Observed frequencies of lines lie far apart, and relatively-narrow bandwidths cover only small $\Delta z$. For example, at $z = 0.5$, CO(1-0) is currently not accessible with ALMA and CO(3-2) requires band 6 ($\sim 345$ GHz) observations, while at $z = 4$ both CO(4-3) and CO(5-4) are covered in band 3 (3 mm; $\sim 100$GHz). As such, low-redshift interlopers can only be excluded directly using large observed bandwidths. Another solution involves multi-wavelength observations, which become capable of detecting even heavily dust-obscured galaxies themselves and provide much more accurate photometric redshifts through optical and near-infrared spectral template fitting.

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

[^2]: While invented in the USA, the late Maki Kaji (

    UTF8min鍜治 真起

    ) popularized the game as **Sū**ji wa **doku**shin ni kagiru (

    UTF8min数字は独身に限る

    ), roughly translating to *the digits must be single*.

# Redshift searches

+---------------:+:----------------:+:-------:+:---------------:+
| Instrument     | Observing bandwidth                          |
+----------------+------------------+---------+-----------------+
|                | \[GHz\]          | /       | \[mm\]          |
+----------------+------------------+---------+-----------------+
| ALMA:          | $89.1 - 112.0$ & | /       | $3.37 - 2.68$ & |
+----------------+------------------+         +-----------------+
| B3 & B4        | $139.9 - 162.7$  |         | $2.14 - 1.84$   |
+----------------+------------------+---------+-----------------+
| Spectral scan: | $84.2 - 114.9$ & | /       | $3.56-2.61$ &   |
+----------------+------------------+         +-----------------+
| B3 & B4        | $125 - 159.25$   |         | $2.40 - 1.88$   |
+----------------+------------------+---------+-----------------+
| ALMA B3 fill   | $84.2 - 114.9$   | /       | $3.56-2.61$     |
+----------------+------------------+---------+-----------------+
| RSR            | $73-111$         | /       | $4.11 - 2.70$   |
+----------------+------------------+---------+-----------------+
| Zpectrometer   | $25.6-37.7$      | /       | $11.7-7.9$      |
+----------------+------------------+---------+-----------------+
| Z-Spec         | $185-305$        | /       | $1.62-0.98$     |
+----------------+------------------+---------+-----------------+
| DESHIMA        | $220-440$        | /       | $1.36-0.68$     |
+----------------+------------------+---------+-----------------+
| Superspec      | $200 - 300$      | /       | $1.50 - 1.00$   |
+----------------+------------------+---------+-----------------+
| OST (Band 6)   | $509 - 893$      | /       | $0.59 - 0.34$   |
+----------------+------------------+---------+-----------------+

: Instruments used for redshift searches

**Notes:** The top two rows together show the optimised tuning from Figure [\[fig:band34_optimization\]](#fig:band34_optimization). The third and fourth rows together show the spectral scan set-up, assuming five stacked tunings at both 3 and 2 mm. Note that there exist a small gap in frequency coverage ($\sim 0.5$ GHz) around $\sim 101$ GHz and $\sim 151$ GHz in the optimum ALMA Band 3 & 4 configuration.

The graphical method facilitates the analysis once the observations are done. This section complements this by providing a figure of merit for past, existing and future redshift searches (Sections [1.1](#sec:interferometricredshiftsearches), [1.2](#sec:dedicatedZreceivers), and [\[sec:FutureInstrumentation\]](#sec:FutureInstrumentation), respectively). This method can then be used to optimise future redshift searches (see Section [\[sec:OptimizedTunings\]](#sec:OptimizedTunings)), and guide the design of instruments for future redshift surveys.

Figure [1](#fig:redshiftSearchEfficiency) shows the probability of a robust redshift of various configurations and instruments that are often used for redshift searches between $z = 0$ and 8, and for two different DSFG samples (HerBS; (cite: bakx18; Bakx2020Erratum), South Pole Telescope; (cite: reuter20) , see Fig. [2](#fig:zdist)). The average redshift of the *Herschel*-selected HerBS sample is $\bar{z} \approx 2.5$, while the SPT sample is selected at longer wavelengths and has an average $\bar{z} = 3.5$. Redshift searches on other DSFG samples, such as ALESS (cite: cunha2015ALESS) or the Ultrared sources (cite: ivison16), can then be scaled accordingly. The distributions are smoothed by $dz \approx 0.5$ to prevent small-number variations in the final efficiency metrics. The details of each instrument are shown in Table [1](#tab:efficiencies). For the calculation in Figure [1](#fig:redshiftSearchEfficiency), we remove regions that are opaque under normal observing conditions (assuming precipitable water vapour $> 0.5$ mm, with transmission greater than 80% of the peak). We show the total number of sources detected robustly with multiple lines and with single lines in *blue fill and hatches*, respectively. The *orange fill and hatches* show where the redshift remained ambiguous with one or two lines, while the white region provides a measure of the redshift desert. We define a robust detection by either a detection in CO where all adjacent solutions within 5$\sigma$ (eq. [\[eq:Nsigma\]](#eq:Nsigma)) can be excluded, or through the detection of a non-CO line.

![](RedshiftSearchEfficiency.pdf)

![](RedshiftDistribution.png)

## Interferometric redshift searches

Interferometers are important tools for finding spectroscopic redshifts (cite: Vieira2013; weiss2013; neri2019; Chen2022; Urquhart2022). By combining multiple spectral windows, interferometers can cover large redshift ranges while delivering high-resolution imaging of both line and continuum emission. However, the telescope array with the largest collecting area, ALMA, only offers a modest spectral coverage (up to $\sim$7.75 GHz per tuning). While the necessary integration time to detect a line from, for example, a bright *Herschel* source is only several minutes, an ALMA-based redshift search could thus result in large overheads ($\sim 30$ min.) due to the need to switch tunings. Generally, there are two ways around the large overheads. Firstly, ALMA offers the ability to observe sources close on the sky (typically $\sim10$ degrees of separation) without the need to recalibrate. Observations can then be carried out in batches of sources, reducing the overheads per source (cite: Urquhart2022). Secondly, ALMA recently started to offer[^2] spectral scans that calibrate all spectral windows on the calibrator, cutting down significantly on slewing overheads, which can amount to half or more of the total observing time. If the targeted number of sources within a 10 deg. field is modest (typically $\lesssim 3$), the spectral scan is preferred. Above this, the observation in batches outperforms the spectral scan.

### Filling the 3 mm band

The initial observations of SPT sources using the full 3 mm band of ALMA successfully demonstrated the interferometer’s redshift search capabilities (cite: Vieira2013; weiss2013; strandet2016; reuter20). These observations use five tunings with ALMA, starting at 84.2 GHz up to 114.9 GHz with overlapping coverage of around one tuning between $96.2 - 102.8$ GHz. Figure [1](#fig:redshiftSearchEfficiency) shows that, while these observations are able to guarantee a single-line detection above $z>2$, this tuning provides only moderate ability to derive robust, unambiguous redshifts on the CO emission alone. For this, 2 mm observations are needed (see e.g., (cite: Bakx2020IRAM)). \[C i\] and H$_2$O emission, as well as improved photometric redshifts can vastly improve the ability of this configuration to estimate the redshift, particularly for samples biased towards high redshifts. Improved uncertainties in the photometric redshift (*black dashed lines*) do not improve the redshift capabilities significantly. Meanwhile, these observations target the CO emission up to the CO(6-5) rotational transition (with one exception up to CO(7-6); (cite: Marrone2018)). It is good to note that these emission lines correlate with the far-infrared luminosity – which is often a direct selection function for high-redshift DSFGs – and these observations are thus less likely to bias observations. Instead, observations aiming at higher-J transitions might be particularly-sensitive to the warmer and denser molecular gas typically found in AGN (e.g., (cite: Xu2014)).

### Combined 3 and 2 mm tunings

In Section [\[sec:OptimizedTunings\]](#sec:OptimizedTunings) and Figure [\[fig:band34_optimization\]](#fig:band34_optimization) we describe how to find the optimum tuning for spectroscopic redshifts using ALMA. Figure [1](#fig:redshiftSearchEfficiency) shows the effect of including band 4 (2 mm). While there exists some regions where multiple lines fail to provide robust redshifts assuming the *Herschel*-based photometry (cite: pearson13), the refined photometric redshifts from the 2 mm continuum (*black dashed lines*) result in high ($> 70$%) robust redshifts beyond $z > 2$, at the limited cost of including an additional tuning ($\sim 20$% longer observation). The benefit is particularly stark at the low-redshift end of the galaxy distribution, without needing to rely on the unpredictable \[C i\] or H$_2$O lines in redshift searches. These results are in line with the impressive redshift search efficiency shown in (cite: Urquhart2022) (as well as in subsequent follow-up; P.I.: Bakx, 2019.2.00155.S), showing a robust redshift ratio of 72%, and even promising up to 93% with deeper observations.

### ALMA spectral scans

Recent development at ALMA allowed for efficient observations of multiple (up to five) spectral windows for a single source. By calibrating all spectral windows in one go, this observing strategy cuts down significantly on the overheads. We note here that a scan of just band 3 results in similar redshift coverage issues as seen in Figure [1](#fig:redshiftSearchEfficiency), as well as the large overlapping coverage seen in e.g., (cite: weiss2013). The coverage issue, however, can be mitigated by including a spectral scan in band 4, which vastly improves the redshift coverage across a wide range of redshifts. If this is executed as a spectral scan, the overheads will be only relatively minor, however this method will be difficult to execute using batched observations similar to (cite: Urquhart2022), requiring a doubling in observation time relative to the 3 mm band method.

### NOEMA redshift searches

Unlike ALMA, NOrthern Extended Millimeter Array (NOEMA; e.g., (cite: neri2019)) and the IRAM 30m (e.g., (cite: Bakx2020IRAM)) offer the ability to adjust the observing frequencies dynamically, based on observed spectral lines in other tunings. This is a significant advantage when looking for redshifts, further aided by the wider bandwidths (up to $\sim 16$ GHz in one tuning, with possible expansion in the future) that allow for a wide 3 mm scan in just two tunings. In the 3 mm window, this would amount to an observation similar to the 3 mm scan in Figure [1](#fig:redshiftSearchEfficiency), where one typically requires additional observations in the 2 mm band. Follow-up observations in the 2 mm band do not lend themselves for easy generalization, which is why we were not able to generate a similar plot for a NOEMA 3- and 2 mm redshift search, although simply covering the 3- and 2 mm windows similar to the Band 3 & 4 linescan suggest a near-complete redshift coverage of the HerBS and SPT samples alike using four tunings. Nevertheless, the graphical method of this paper (i.e., Fig. [\[fig:fig1\]](#fig:fig1)) can offer significant aid in determining additional observations at both 2 mm and other bands, while also highlighting redshift degeneracies.

## Dedicated redshift receivers

The advent of spectrometers with instantaneous wide-band enabled the first large-scale redshift surveys. While the first (sub)mm redshift searches involved heterodyne instruments that require multiple tunings (e.g., (cite: weiss2009)), the notable instruments that performed these dedicated redshift searches are the Redshift Search Receiver (RSR; (cite: Erickson2007)), Z-Spec (cite: Naylor2003), and Zpectrometer (cite: Harris2007) on single-dish telescopes.

### Redshift Search Receiver

The Large Millimeter Telescope (LMT)-based observations with the RSR (cite: Erickson2007) combine the instantaneous coverage of the 3 mm window with the powerful 32 to 50 m diameter of the telescope to reveal the spectral lines of galaxies out to high redshifts (e.g., (cite: Zavala2015; Zavala2018)). At lower redshifts particularly, these observations require ancillary data – such as with IRAM or $8-10$ m telescopes – to confirm the redshifts robustly. The addition of a 2 mm spectroscopic ability at the LMT would significantly increase the telescope’s ability to determine redshifts robustly (e.g., Kawabe et al. in prep).

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

[^2]: https://almascience.eso.org/proposing/proposers-guide

### Z-Spec

The wide bandwidth capability of Z-Spec (cite: Naylor2003) at 1.0 to 1.6 mm enabled the near-guaranteed ability to detect more than one spectral line. As seen in (cite: lupu2012), the higher-frequency transitions (often of CO lines) are not guaranteed. In this case, clever stacking of the line emission as a function of redshift enabled robust redshifts even though individual lines might be detected only at a few sigma. It is good to note that, unlike the RSR and Zpectrometer, the diameter of the Caltech Submillimeter Observatory (CSO) where the telescope operated was modest at 10 m, since high surface accuracy was needed given the higher-frequency observations.

### Zpectrometer

The Zpectrometer receiver (cite: Harris2007) operated on the 100 m Green Bank Telescope, and principally targeted CO(1-0) and CO(2-1). This large collecting area is crucial, since the expected emission from these low-excitation rotational transitions is faint (cite: harris2010). Observationally, the GBT/Zpectrometer set-up had another advantage to increase its efficiency. While performing on-off chopping to remove background and atmospheric noise, the telescope chopped between two galaxy positions. The emission line from the second (’off’) source would then be seen as a negative signal (cite: Frayer2011; harris2012). This method allows for the easy identification of redshifts between 2 and 3.5, as well as above 5. Interestingly, the typical uncertainty on photometric redshifts increases with redshift, going as $\sim 0.13 \times{} (1+z)$, the lower redshifts are basically robust (hatched blue), while the higher redshifts might be mis-interpreted CO(2-1) line emission that is instead CO(1-0).

## Future instrumentation

New instrumentation is underway to explore the high-redshift Universe using broad-band spectrometers, in particular using Microwave Kinetic Inductance Detectors (MKIDs; (cite: Day2003; Endo2019)) technology, and on-board of the Origin Space Telescope (OST; (cite: Battersby2018)).

### DESHIMA

The DEep Spectroscopic HIgh-redshift MApper instrument combines an integrated super-conducting spectrometer with a read-out based on MKIDs to enable ultra-wideband ($>100$ GHz) spectroscopy at medium resolution ($f/ \Delta f \approx 500$). We carefully exclude frequency regions with strong atmospheric absorption from our analysis in Figure [\[fig:redshiftSearchEfficiency\]](#fig:redshiftSearchEfficiency). As shown in detail in (cite: Rybak2021), the wide bandwidth at 1.4 to 0.7 mm means that DESHIMA will be sensitive to mid- to higher-J transitions for sources at $z < 3.3$. These emission lines vary strongly from source to source, however can be brought out through similar stacking as seen in Z-Spec (e.g., (cite: lupu2012)). Beyond $z > 3.3$, the \[C ii\] emission line will dominate the emission and will be readily detected. We note that the robust redshift coverage of DESHIMA at even the lowest redshifts is high, and DESHIMA could thus additionally be well-suited towards low-$z$ spectroscopic redshift searches.

### SuperSpec

The SuperSpec instrument aims to use a lithographically-patterned filterbank (similar to DESHIMA) to probe the high-redshift Universe, primarily through atomic lines of high-redshift targets between $z = 4 - 8$ (cite: Redford2021). The instrument is designed for operation on the LMT, whose large collecting area allows for deep integration on even faint targets. Similar to DESHIMA, this instrument also has the ability to rapidly assess the redshifts of lower-$z$ targets through mid-J emission lines.

### Origin Space Telescope

We chose to only model the longest-wavelength band of the medium-resolution spectroscopic instrument on the OST (band 6; $0.34 - 0.59$ mm, (cite: Battersby2018)) since it is more sensitive to lower-frequency lines such as CO. We note that additional bands (which are expected to be able to observe simultaneously) improve the redshift capabilities further by picking up ancillary atomic lines which further aid in the determination of robust redshifts. Beyond $z > 1.1$, OST will be able to target \[C ii\] emission, leaving only a little gap ($2.73 < z < 2.81$) where at band 6 is unable to pick up either \[O iii\]88$\mu$m or \[C ii\]158$\mu$m, although \[N ii\]122$\mu$m could also be observed.

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

## Optimising ALMA tunings for spectroscopic redshifts

![](band34_tuning.png)

We test the ability to include 2 mm spectral windows to improve the robust redshift coverage of ALMA. The proposed configuration uses a total of six tunings to generate two near-contiguous frequency coverages at both 3 and 2 mm, which removes the overlapping region of the 3 mm scan. The total figure of merit is determined not solely by robust redshifts (either through single- or multiple-lines), but we choose to additionally add non-robust redshifts, weighted down by 50%. Figure [1](#fig:band34_optimization) shows the figure of merit for each possible combination of 3 and 2 mm regions on a smoothed redshift distribution similar to the HerBS targets (cite: bakx18; Bakx2020Erratum), assuming a low uncertainty in the $z_{\rm phot}$ of $\Delta z / (1+z) \approx 7$%. Note that both the figure of merit, as well as the choice for the redshift distribution depend on the science case, and can be adjusted by the reader in the scripts provided online. The figure of merit varies between 0.83 to 0.94 for different combinations of the 3 and 2 mm window, with the optimum lying at the middle frequencies in band 3 (3 mm) and at higher frequencies in band 4 (2 mm), with the precise configuration shown in Table [\[tab:efficiencies\]](#tab:efficiencies). The frequencies of the ALMA 12m array observations in (cite: Urquhart2022) were derived using a similar method. They report redshift search efficiencies similar to the ones suggested by Figure [1](#fig:band34_optimization), with a robust redshift fraction of 72%, and promising to go up to 93% with deeper observations. While we demonstrate the efficacy of this method on ALMA, any redshift search with tunable (sub)mm receivers can be optimised using this method through the publicly-available code.

# Conclusions

This work documents new and efficient methods for (sub)mm redshift searches of high-$z$ SMGs. The tools discussed in this paper are publicly available at <https://github.com/tjlcbakx/redshift-search-graphs>. This paper reports on:

- An efficient graphical method for identifying redshifts, removing the need to manually cross-compare redshift options. Aside from a description of the method, we provide a comprehensive overview of caveats in deriving redshifts using (sub)mm spectral lines in the high-$z$. The method provides highlights the explored redshift-space, enabling the removal of untenable redshift options, while also pointing out potential redshift degeneracies.

- A method to calculate the capabilities of various instruments towards deriving robust spectroscopic redshifts. This is useful, not only to evaluate past missions, but also to guide future instruments.

- A method to optimise tunings towards robust spectroscopic redshifts (and other figures of merit) for ALMA and other tunable (sub)mm receivers. Here, we stress the need for both 3 and 2 mm observations to identify redshifts robustly.

# Acknowledgements

TB thanks the helpful contributions towards this publication from Dr. Ewoud A.I. Pool, who provided both a wider scope on the project and improved the graph descriptions. We also thank the helpful comments of the referee, which increased the scientific scope of the paper and the associated code. TB acknowledges funding from NAOJ ALMA Scientific Research Grant Numbers 2018-09B and JSPS KAKENHI No. 17H06130. HD acknowledges financial support from the Spanish Ministry of Science, Innovation and Universities (MICIU) under the 2014 Ramón y Cajal program RYC-2014-15686, from the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEI-MCINN) under grant (La evolución de los cíumulos de galaxias desde el amanecer hasta el mediodía cósmico) with reference (PID2019-105776GB-I00/DOI:10.13039/501100011033) and acknowledge support from the ACIISI, Consejería de Economía, Conocimiento y Empleo del Gobierno de Canarias and the European Regional Development Fund (ERDF) under grant with reference PROID2020010107. This paper makes use of the following ALMA data: ADS/JAO.ALMA 2016.2.00133.S, 2018.1.00804.S, 2019.1.01147 and 2019.2.00155.S.

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

# Data Availability

All code used to derive the graphs in this paper are available at <https://github.com/tjlcbakx/redshift-search-graphs> in order to assist in the robust classification of redshifts in ongoing, future and past programs.

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

[^1]: E-mail: bakx@a.phys.nagoya-u.ac.jp (Nagoya University)

</paper>

## Items to check

```json
[
 {
  "path": "data.bands.evidence[0]",
  "value": "Band 3 (3 mm) and Band 4 (2 mm)",
  "failed_quote": "ALMA: $89.1 - 112.0$ & $3.37 - 2.68$ & B3 & B4 $139.9 - 162.7$ $2.14 - 1.84$"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[0]",
  "value": "89.1 - 112.0 GHz and 139.9 - 162.7 GHz (optimised B3 & B4); 84.2 - 114.9 GHz and 125 - 159.25 GHz (spectral scan B3 & B4); 84.2 - 114.9 GHz (ALMA B3 fill)",
  "failed_quote": "ALMA: $89.1 - 112.0$ & $3.37 - 2.68$ & B3 & B4 $139.9 - 162.7$ $2.14 - 1.84$"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "89.1 - 112.0 GHz and 139.9 - 162.7 GHz (optimised B3 & B4); 84.2 - 114.9 GHz and 125 - 159.25 GHz (spectral scan B3 & B4); 84.2 - 114.9 GHz (ALMA B3 fill)",
  "failed_quote": "Spectral scan: $84.2 - 114.9$ & $3.56-2.61$ & B3 & B4 $125 - 159.25$ $2.40 - 1.88$"
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "[CI]",
  "failed_quote": "The observation is expected to detect the CO-lines (black lines), and might detect the [C i] and H$_2$O lines (dashed blue lines; see Section 2.3.2)."
 },
 {
  "path": "data.lines_targeted[2].evidence[0]",
  "value": "H2O",
  "failed_quote": "The observation is expected to detect the CO-lines (black lines), and might detect the [C i] and H$_2$O lines (dashed blue lines; see Section 2.3.2)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Demonstrated on fiducial galaxy scenarios (Figures 1 to 5)",
  "failed_quote": "In Figure 1, we show this graphical method for a fiducial $z_{\\rm phot} = 3$ example source observed with an efficient ALMA tuning setup (see Section [sec:OptimizedTunings])."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Calculate the probability of obtaining robust (single- or multi-line) and ambiguous redshifts between z = 0 and 8, weighted by smoothed HerBS and SPT redshift distributions, defining robust CO detections by exclusion of all adjacent solutions within 5 sigma or detection of a non-CO line",
  "failed_quote": "We define a robust detection by either a detection in CO where all adjacent solutions within 5$\\sigma$ (eq. [eq:Nsigma]) can be excluded, or through the detection of a non-CO line."
 },
 {
  "path": "analysis_steps[1].key_parameters[1].evidence[0]",
  "value": "Robust CO detection threshold: adjacent solutions within 5 sigma excluded",
  "failed_quote": "We define a robust detection by either a detection in CO where all adjacent solutions within 5$\\sigma$ (eq. [eq:Nsigma]) can be excluded, or through the detection of a non-CO line."
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Optimised ALMA Band 3 frequency coverage = 89.1 - 112.0 GHz",
  "failed_quote": "ALMA: $89.1 - 112.0$ & $3.37 - 2.68$ & B3 & B4 $139.9 - 162.7$ $2.14 - 1.84$"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Optimised ALMA Band 4 frequency coverage = 139.9 - 162.7 GHz",
  "failed_quote": "ALMA: $89.1 - 112.0$ & $3.37 - 2.68$ & B3 & B4 $139.9 - 162.7$ $2.14 - 1.84$"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Figure of merit for combined ALMA Band 3 and Band 4 tunings = 0.83 to 0.94 dimensionless",
  "failed_quote": "The figure of merit varies between 0.83 to 0.94 for different combinations of the 3 and 2 mm window, with the optimum lying at the middle frequencies in band 3 (3 mm) and at higher frequencies in band 4 (2 mm), with the precise configuration shown in Table [tab:efficiencies]."
 },
 {
  "path": "claims[1].evidence[2]",
  "value": "2 mm observations are indispensable for robust redshifts in the z = 2 - 4 regime with ALMA at the limited cost of an additional tuning (~20% longer observation).",
  "failed_quote": "The figure of merit varies between 0.83 to 0.94 for different combinations of the 3 and 2 mm window, with the optimum lying at the middle frequencies in band 3 (3 mm) and at higher frequencies in band 4 (2 mm), with the precise configuration shown in Table [tab:efficiencies]."
 }
]
```
