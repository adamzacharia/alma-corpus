# Toomre Q: inputs and reported values per paper

From the `toomre-stability` evidence pack. Values marked "(card)" were read from that paper's methods card to
settle a detail the pack summarised; each was checked against the card's verbatim quote. Off-topic papers (cluster Q statistic, Toomre-disk mass components) are left
out.

## Circumstellar disks

| Paper | Sigma source | Temperature | Central mass | Threshold / use | Reported Q |
|---|---|---|---|---|---|
| 2017A&A...603A..10B | continuum per pixel | T_rot; 200 K; T ~ r^-0.4 (1400 K at 10 AU) | 10 Msun Keplerian | map | min > ~1.5 (power-law T) |
| 2019A&A...627L...6M | column density x mu m_H, mu = 2.3 | T ~ R^-0.4 anchored to O star | Keplerian | map, min/max free-free | 2-4 in ring at 65-97 au |
| 2019ApJ...877L..25M | continuum, beta = 1 or 2 | not stated in pack | 10 Msun Keplerian | map | min 0.9 (beta 1), 0.4 (beta 2) |
| 2025NatAs...9.1833L | disk mass 2.71 Msun | T maps | 7.6 Msun enclosed | Q < 1-2 unstable | uncertainty 54% |
| 2019ApJ...871..185L | 225 GHz flux, g/d 100 | 30 K fiducial or profile | enclosed gas mass plus 0 or 30 Msun stellar | radial | (fragmentation test) |
| 2025A&A...693A..76C | CH3CN Ncol, X = 1e-9, mu = 2.8 (role not stated) | Tk = T_rot | 12 Msun | analytic | (toy model) |
| 2020MNRAS.493L.108B | 13C17O gas + dust | model midplane | 1.7 Msun | Q < ~1.7 | min 1.1 at 77 au; Q < 1.7 at 50-110 au |
| 2019ApJ...882L..31B | 13C17O gas, g/d ~260 (card) | model midplane | not stated in pack (disk gas mass 0.31 Msun at 122 pc, 0.21 Msun at 101.5 pc, card) | radial | min ~6 at ~110 au (card) |
| 2019MNRAS.485..739M | C18O gas, lower limit | | | radial | min ~24 at ~80 au (card) |
| 2016MNRAS.461..385B | C18O gas within 90 au (card), H/r ~0.1 | model | | Q = 1 (card) | well above 1 (card) |
| 2018ApJ...852..122H | dust, kappa 3.3 cm2/g at 290 GHz, g/d 100 | 15 K | | check | |
| 2016Sci...353.1519P | RADMC-3D, kappa 2.3 cm2/g at 1.3 mm, g/d 100 | RT model | | | |
| 2018ApJ...861...91H | kappa = 10 (nu/1 THz)^1 cm2/g / 100 (total opacity 0.034 cm2/g, card) | 30 K | 0.15 Msun | | ~1.8 at 85 au (card) |
| 2018ApJ...864L..25O | kappa 6.8e-4 cm2/g at 1.2 mm (dust or gas basis not established) | 20-100 K | Keplerian; mass may be upper limit or apparent | | 0.4 (20 K) to 5 (100 K) (card) |
| 2019ApJ...877..100Y | 880 um flux, kappa 3 cm2/g, g/d 100 | irradiated, phi = 0.02 | | mean Q | |
| 2020ApJ...890..130T | dust mass x 100 | T ~ R^-0.46 | 0.25 Msun fiducial | Q ~ 2 (M*/Md)(H/R) | |
| 2020ApJ...893..125U | DSHARP kappa_abs 9.2e-2 cm2/g Band 3 | 30 K | 0.8 Msun | | |
| 2015ApJ...808..102K | fitted Sigma(r) | fitted midplane | Keplerian | Q < ~1.5 unstable | |
| 2016ApJ...818..158A | kappa0 = 0.01 cm2/g at 230 GHz, beta 0.729 (dust or gas basis not established) | | | Sigma_g,min from Q plus cooling (card) | |
| 2024ApJ...966..119L | | current vs pre-burst (snowline 4 au) | | Q < 2 | > 2 now (~7 at 200 au); < 2 at r < 100 au pre-burst |
| 2024ApJ...971..129C | 1e6 draws of Sigma_d, T; g/d 100 | sampled | | Q > 2 stable | max g/d 27 in ring |
| 2018ApJ...869L..46D | dust trap model | estimated | | Q > 2 caps Sigma_g | |
| 2018ApJ...869L..47Z | outer-disk dust Sigma | | | Q = 1 caps Sigma_g | |
| 2024ApJ...970..153A | kinematic self-gravity | fitted | fitted | min Q prior (Q from this Sigma is prior-dependent) | Md/M* = 7 +/- 1% (MWC 480) |
| 2025ApJ...984L..19Y | CO line wings | | | assumed Q > 1 at peak | X_CO > 7e-4 (conditional on Q > 1) |

## Galaxy gas disks

| Paper | Sigma source | Dispersion | kappa / rotation | Reported Q |
|---|---|---|---|---|
| 2014A&A...565A..59D | [CII] luminosity proxy | measured | sqrt(2) V/r, flat | 0.58 +/- 0.15 average |
| 2015ApJ...806L..17S | Sigma_gas 4 +/- 1e9 Msun/kpc^2 | 30-35 km/s | sqrt(3) Vmax/R | 0.30 +/- 0.10 |
| 2016ApJ...827...34O | CO gas mass | measured | disk + halo model | ~0.22, ~0.35 (card) |
| 2017A&A...604A.117C | 1e4 Msun/pc^2 | measured | a = 2 | 1.0 +/- 0.3 |
| 2018A&A...613A..34P | Mdyn minus 30% DM and stars | measured | i = 54 deg | 1.07 (card) |
| 2019A&A...631A..91G | f_gas | sigma0 | Q = sqrt(2) sigma0/(vrot fgas) | ~0.6 |
| 2019ApJ...870...80L | M_g = 1.5e11 Msun split by [CII] | sigma_r (upper limit) | sqrt(3) v_r/r, 3D-Barolo | mean 0.02-0.03, max 0.13 |
| 2020Natur.581..269N | molecular mass | measured | within R = 3 R_d | 0.96 +/- 0.30 |
| 2025NatAs...9.1553F | [CII], alpha 31 Msun/Lsun | 3DBarolo sigma(R) | 3DBarolo V(R) | 0.2-0.3 |
| 2015ApJ...806...17R | warm CO gas | sigma as c_s | 135 km/s rotation | ~1.5, factor two |
| 2016ApJ...823...68S | molecular | sigma_mol | alpha = 1 | |
| 2017ApJ...845..170B | CO, alpha_CO | min sigma_LOS | k1/sin i | stable |
| 2018MNRAS.476..122V | CO | measured or 8 km/s | arctangent model | mostly > 1 (card) |
| 2021A&A...655A..25Z | moment 0 | moment 2 | a = 1 (< 1.1 arcsec), 1.4 beyond | 0.5-10 |
| 2025ApJ...995..151Y | H2 only | gas 5 km/s, stars 30 km/s | rotation curve | Q_tot 0.9-1.5 |
| 2019ApJ...876..130H | global Sigma_SFR | inferred | flat curve | sigma < 70-160 km/s from Q < 1 |
