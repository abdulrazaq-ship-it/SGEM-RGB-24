# SGEM-RGB-24 — Companion Repository

Supplementary material for the manuscript
**"Authenticated RGB Image Encryption Using Switched Inverse Substitution and Multiplex Cayley-Graph Diffusion"**
(A. Razaq, H. Z. Mustafa, S. Khyzer, H. Alolaiyan).

Contents: the complete self-contained MATLAB implementation; Tables S1–S10; Figs. S1–S2; evaluation formulas; explicit multiplication formulas in $\mathbb{F}_{2^{24}}$; vector source files for Figs. 1–3; a 600-dpi Fig. 4; and the differential-uniformity and compression scripts.

---

## Table S1. Main notation

| Symbol | Description |
|---|---|
| $P$ | Plain RGB image |
| $C$ | Encrypted RGB image |
| $D$ | Decrypted RGB image |
| $H, W$ | Image height and width |
| $N = HW$ | Number of pixels |
| $K$ | 256-bit master key |
| $\nu$ | 128-bit public nonce |
| $X_i$ | Field representation of the $i$-th RGB pixel |
| $S_r$ | Switched substitution used in round $r$ |
| $M_r$ | Key-dependent MDS matrix used in round $r$ |
| $\Gamma_r$ | Spatial Cayley graph used in round $r$ |
| $\rho_r$ | Normalized nontrivial spectral radius |
| $\gamma_r = 1-\rho_r$ | Normalized spectral gap |
| $R$ | Number of encryption rounds |
| $\tau$ | Authentication tag |

## Table S2. Experimental configuration

| Parameter | Value |
|---|---|
| Rounds | 8 |
| Master-key length | 256 bits |
| Nonce length | 128 bits |
| Authentication-tag length | 256 bits |
| Spatial graph degree | 6 |
| Multiplex graph degree | 8 |
| Maximum spatial radius | 0.9 |
| Maximum multiplex radius | 0.9 |
| Local-entropy blocks | 30 |
| Local block size | 44 x 44 |
| Correlation pairs | 50000 |
| Plaintext-change trials | 10 |
| Key-change trials | 3 |
| Nonce-change trials | 3 |
| Tested ciphertext bits | 2000000 |
| Block-frequency length | 128 |
| GLCM gray levels | 16 |
| Image resizing | None; native resolution |
| Pixel permutation | 6-round Feistel with cycle walking |
| Pixel chunk size | 262144 |
| Graph-window batch size | 1024 |


## Table S3. Test images (native resolution): provenance, licences and dates

| Image | Category | Source, file identifier and URL | Licence | Available dates | Size (W × H) | Pixels | Graph windows | Overlapping window |
|---|---|---|---|---|---|---|---|---|
| Gastrointestinal endoscopy | Medical | HyperKvasir [37]; tested image: test_images/HyperKvasir_gastrointestinal_endoscopy.png (pixel SHA-256 90a50be7abe3f69af83e0cfe6f0b121c149fe282579368ed2ce8ab6c587cfd2f); https://doi.org/10.17605/OSF.IO/MH9SJ | CC BY 4.0 | Dataset collected 2008–2016; paper published 28 Aug 2020 | 1221 × 1012 | 1,235,652 | 7,356 | Yes |
| Glaucoma retinal fundus | Medical | FIVES [38]; test/Original/123_G.png; https://doi.org/10.6084/m9.figshare.19688169.v1 | CC BY 4.0 | Dataset collected 2016–2021; released 1 May 2022 | 2048 × 2048 | 4,194,304 | 24,967 | Yes |
| Healthy retinal fundus | Medical | HRF [39]; 01_h.jpg; https://www5.cs.fau.de/research/data/fundus-images/ | CC BY 4.0 | Camera EXIF 19 Oct 2006; reference paper 2013 | 3504 × 2336 | 8,185,344 | 48,723 | Yes |
| Car interior | General | Wikimedia Commons, “Car Interior”, Dhaval Surana; https://commons.wikimedia.org/wiki/File:Car_Interior.jpg | CC BY 4.0 | Photographed 17 Jul 2024; uploaded 2 Dec 2024 | 2448 × 3264 | 7,990,272 | 47,562 | Yes |
| City at sunset | General | Wikimedia Commons, “City and The Sunset”, Irs05; https://commons.wikimedia.org/wiki/File:City_and_The_Sunset.jpg | CC BY 4.0 | Photographed 16 Jun 2025; uploaded 14 Dec 2025 | 4032 × 3024 | 12,192,768 | 72,576 | No |
| Railway scene | General | Wikimedia Commons, “Indian Railways Train in 2025”, Ash7876; https://commons.wikimedia.org/wiki/File:Indian_Railways_Train_in_2025.jpg | CC BY 4.0 | Photographed 6 Jul 2025; first uploaded 13 Jul 2025 | 4080 × 3072 | 12,533,760 | 74,606 | Yes |

All images are licensed under CC BY 4.0 and were encrypted and decrypted at native resolution. Figure 4 reduces the resulting original, ciphertext and recovered images only for display. The medical images come from public research datasets collected between 2006 and 2021.

## Table S4. Histogram uniformity

| Image | Mean χ² | Mean histogram $p$-value | KL divergence from uniform | Total variation from uniform |
|---|---|---|---|---|
| Gastrointestinal endoscopy | 258.187 | 0.434235 | 0.000150607 | 0.00568945 |
| Glaucoma retinal fundus | 260.334 | 0.408117 | 4.47665e-05 | 0.00306869 |
| Healthy retinal fundus | 274.183 | 0.201983 | 2.41678e-05 | 0.00228763 |
| Car interior | 249.014 | 0.587643 | 2.24878e-05 | 0.00225608 |
| City at sunset | 241.757 | 0.675469 | 1.43037e-05 | 0.00175703 |
| Railway scene | 251.782 | 0.542465 | 1.44882e-05 | 0.00178348 |


## Table S5. Selected randomness-test $p$-values ($\alpha = 0.01$)

| Image | Monobit | Runs | Block frequency | Approximate entropy | Passed |
|---|---|---|---|---|---|
| Gastrointestinal endoscopy | 0.782723 | 0.238802 | 0.509991 | 0.744157 | 4/4 |
| Glaucoma retinal fundus | 0.140968 | 0.399366 | 0.273396 | 0.515611 | 4/4 |
| Healthy retinal fundus | 0.015715 | 0.499117 | 0.989178 | 0.157542 | 4/4 |
| Car interior | 0.311939 | 0.278374 | 0.548541 | 0.362686 | 4/4 |
| City at sunset | 0.530989 | 0.143736 | 0.805530 | 0.374904 | 4/4 |
| Railway scene | 0.090222 | 0.925000 | 0.601705 | 0.426414 | 4/4 |


## Table S6. Authentication and recovery results

| Image | Exact recovery | Wrong key rejected | Bit tamper rejected | Region tamper rejected | Channel swap rejected | Header tamper rejected |
|---|---|---|---|---|---|---|
| Gastrointestinal endoscopy | Yes | Yes | Yes | Yes | Yes | Yes |
| Glaucoma retinal fundus | Yes | Yes | Yes | Yes | Yes | Yes |
| Healthy retinal fundus | Yes | Yes | Yes | Yes | Yes | Yes |
| Car interior | Yes | Yes | Yes | Yes | Yes | Yes |
| City at sunset | Yes | Yes | Yes | Yes | Yes | Yes |
| Railway scene | Yes | Yes | Yes | Yes | Yes | Yes |


## Table S7. Mean results for medical and general images

| Category | Images | Cipher entropy | Local entropy | Mean abs. correlation | NPCR (%) | UACI (%) | Bit avalanche (%) | Randomness tests passed |
|---|---|---|---|---|---|---|---|---|
| Medical | 3 | 7.999927 | 7.901780 | 0.001480 | 99.609488 | 33.463516 | 49.999386 | 4/4 |
| General | 3 | 7.999983 | 7.902489 | 0.001193 | 99.609554 | 33.462860 | 49.999507 | 4/4 |


## Table S8. Complete per-image measures

The file `TableS8_all_metrics.csv` lists all measures computed for each image (more than 100 per image), including per-channel entropy, bit-plane entropy, lag autocorrelations, mutual information, MSE/PSNR/SSIM/UQI/NCC/NAE, GLCM statistics, per-channel NPCR/UACI, the mean, standard deviation, minimum and maximum of the plaintext-, key- and nonce-sensitivity trials, and the mean spectral radii and gaps. The per-round graph data (generators, radii and gaps for every round) are in `graph_rounds.csv`.


## Table S9. Sensitivity per image: mean ± within-trial standard deviation (%)

Plaintext: 10 one-bit changes; key: 3 one-bit changes; nonce: 3 one-bit changes per image. Table 2 of the manuscript gives the SD of the six per-image means.

| Image | Plain NPCR (mean ± SD, n=10) | Plain UACI (mean ± SD, n=10) | Plain BAR (mean ± SD, n=10) | Key NPCR (mean ± SD, n=3) | Key UACI (mean ± SD, n=3) | Key BAR (mean ± SD, n=3) | Nonce NPCR (mean ± SD, n=3) | Nonce UACI (mean ± SD, n=3) | Nonce BAR (mean ± SD, n=3) |
|---|---|---|---|---|---|---|---|---|---|
| Gastrointestinal endoscopy | 99.609718 ± 0.003735 | 33.459346 ± 0.010954 | 50.000112 ± 0.009205 | 99.608394 ± 0.001052 | 33.464463 ± 0.013460 | 49.991719 ± 0.014365 | 99.609770 ± 0.003786 | 33.456222 ± 0.019989 | 49.998245 ± 0.006150 |
| Glaucoma retinal fundus | 99.609385 ± 0.002306 | 33.466682 ± 0.004464 | 49.998675 ± 0.006622 | 99.608596 ± 0.001984 | 33.459942 ± 0.001502 | 49.995846 ± 0.005727 | 99.609802 ± 0.001905 | 33.469756 ± 0.003170 | 50.001373 ± 0.004785 |
| Healthy retinal fundus | 99.609363 ± 0.001663 | 33.464520 ± 0.002972 | 49.999370 ± 0.003240 | 99.609456 ± 0.002104 | 33.465006 ± 0.001622 | 49.998570 ± 0.001891 | 99.609144 ± 0.001339 | 33.464520 ± 0.002218 | 49.999086 ± 0.004925 |
| Car interior | 99.609828 ± 0.000718 | 33.462999 ± 0.003803 | 49.998391 ± 0.004295 | 99.610704 ± 0.000561 | 33.461742 ± 0.002055 | 50.002123 ± 0.002053 | 99.608751 ± 0.000422 | 33.462804 ± 0.006775 | 50.000569 ± 0.003445 |
| City at sunset | 99.609437 ± 0.000974 | 33.462629 ± 0.002922 | 49.999859 ± 0.002615 | 99.609539 ± 0.000595 | 33.459827 ± 0.003338 | 49.998467 ± 0.002548 | 99.609540 ± 0.000852 | 33.460003 ± 0.004466 | 49.997489 ± 0.003800 |
| Railway scene | 99.609398 ± 0.001156 | 33.462952 ± 0.004079 | 50.000269 ± 0.002636 | 99.609300 ± 0.000939 | 33.461847 ± 0.001899 | 49.999581 ± 0.001022 | 99.609599 ± 0.001120 | 33.464452 ± 0.000747 | 50.000046 ± 0.003454 |

## Table S10. Lossless compression of plaintext and ciphertext pixel data

Compressed size as a percentage of the raw RGB pixel data (3HW bytes). PNG: Pillow with optimize=True; zlib level 9 and bzip2 level 9 applied to the raw interleaved RGB bytes. Values above 100% mean that the data grew. Raw byte counts: `TableS10_compression.csv`.

| Image | Raw size (bytes) | PNG plain | PNG cipher | zlib-9 plain | zlib-9 cipher | bzip2-9 plain | bzip2-9 cipher |
|---|---|---|---|---|---|---|---|
| Gastrointestinal endoscopy | 3,706,956 | 35.69% | 100.17% | 71.45% | 100.03% | 46.22% | 100.45% |
| Glaucoma retinal fundus | 12,582,912 | 6.09% | 100.12% | 9.03% | 100.03% | 7.01% | 100.45% |
| Healthy retinal fundus | 24,556,032 | 28.69% | 100.08% | 49.54% | 100.03% | 28.87% | 100.44% |
| Car interior | 23,970,816 | 33.88% | 100.09% | 46.91% | 100.03% | 35.72% | 100.44% |
| City at sunset | 36,578,304 | 30.25% | 100.07% | 41.52% | 100.03% | 27.36% | 100.44% |
| Railway scene | 37,601,280 | 37.88% | 100.07% | 53.23% | 100.03% | 41.18% | 100.44% |

## Fig. S1. RGB histograms of original and encrypted images

![](figures/FigS1_a_Gastrointestinal_endoscopy_image_jpg.png)

![](figures/FigS1_b_Glaucoma_retinal_image_png.png)

![](figures/FigS1_c_Healthy_retinal_fundus_image_jpg.png)

![](figures/FigS1_d_Car_Interior_jpg.png)

![](figures/FigS1_e_City_and_The_Sunset_jpg.png)

![](figures/FigS1_f_Indian_Railways_Train_in_2025_jpg.png)

## Fig. S2. Switched substitution over $\mathbb{F}_{2^{24}}$

![](figures/FigS2_switched_substitution.png)

---

## Multiplication in $\mathbb{F}_{2^{24}} = \mathbb{F}_{2^8}[\theta]/\langle \theta^3+\theta+1\rangle$

For $X = a + b\theta + c\theta^2$ and $Y = d + e\theta + f\theta^2$ with $a,\dots,f \in \mathbb{F}_{2^8}$, using $\theta^3 = \theta + 1$:

$$XY = z_0 + z_1\theta + z_2\theta^2,$$
$$z_0 = ad + bf + ce,\qquad z_1 = ae + bd + bf + ce + cf,\qquad z_2 = af + be + cd + cf,$$

with all operations evaluated in $\mathbb{F}_{2^8}$.

## Evaluation measures

**Shannon entropy** of an 8-bit channel $X$: $$H(X) = -\sum_{i=0}^{255} p_i \log_2 p_i,\qquad H_{\max}=8.$$

**Local entropy** over $L = 30$ random $44\times 44$ blocks $B_k$: $$H_{\text{local}} = \frac{1}{L}\sum_{k=1}^{L} H(B_k).$$

**Adjacent-pixel correlation** (horizontal, vertical, diagonal):
$$r_{xy} = \frac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}{\sqrt{\sum_{i=1}^{n}(x_i-\bar{x})^2\,\sum_{i=1}^{n}(y_i-\bar{y})^2}}.$$

**NPCR** (random reference 99.609375%):
$$\mathrm{NPCR} = \frac{100}{3HW}\sum_{i=1}^{H}\sum_{j=1}^{W}\sum_{c=1}^{3} D(i,j,c),\qquad D(i,j,c)=\begin{cases}1, & C_1(i,j,c)\neq C_2(i,j,c)\\ 0, & \text{otherwise.}\end{cases}$$

**UACI** (random reference ≈ 33.4635%):
$$\mathrm{UACI} = \frac{100}{3HW}\sum_{i=1}^{H}\sum_{j=1}^{W}\sum_{c=1}^{3}\frac{|C_1(i,j,c)-C_2(i,j,c)|}{255}.$$

**Bit avalanche rate** (ideal ≈ 50%):
$$\mathrm{BAR} = \frac{100\,\mathrm{wt}_{\text{bit}}(C_1\oplus C_2)}{24HW}.$$

**Randomness diagnostics:** monobit frequency, runs, block frequency (block length 128 bits) and approximate entropy, at significance level $\alpha = 0.01$. These are selected NIST-style diagnostics, not the complete NIST SP 800-22 suite.

---

## Complete MATLAB implementation

`matlab/SGEM_RGB24.m` is the complete self-contained experiment. It contains the user configuration, primitive self-tests, SGEM-RGB-24 encryption and authenticated decryption, finite-field arithmetic, switched inverse substitution, key-dependent MDS mixing, PSL(2,7) graph construction and spectral certification, Feistel cycle-walking permutation, two-pass multiplex diffusion, statistical analyses, attack checks, checkpoint/restart support, plots and manuscript-table export.

To run it in MATLAB R2018b or later:

```matlab
cd matlab
run('SGEM_RGB24.m');
```

Enter the number of images, select each source image, and choose its category. The program processes every image at native resolution. `matlab/example_input.png` is included for a first execution check, and `matlab/README.md` gives the shortened test settings and full paper settings. `matlab/reported_run_records.csv` records the header, nonce and tag of each reported ciphertext, and `test_images/` contains the tested HyperKvasir image with its SHA-256 hashes.

## Figure source files

`figures/Fig1_architecture.*`, `figures/Fig2_multiplex_cayley_graph.*` and `figures/Fig3_encryption_decryption_flow.*` are vector (SVG/PDF/EPS) and 600-dpi TIFF versions of Figs. 1–3, together with the scripts that generate them. The Fig. 2 script follows Sections 3.7–3.8 exactly. It builds PSL(2,7) as 2×2 matrices over GF(7) modulo ±I, selects six involutions and accepts the spatial graph Γ_r only if it is connected with ρ ≤ 0.90. It uses three copies of Γ_r, joins them by the group-defined matchings (R,g)↔(G,g·q_RG), (G,g)↔(B,g·q_GB) and (B,g)↔(R,g·q_BR), and checks the multiplex condition ρ ≤ 0.90. The radii printed in the figure (spatial 0.720, multiplex 0.705) are computed from these graphs. `figures/Fig4_original_encrypted_decrypted.tiff` is a lossless 600-dpi version of Fig. 4.

## Differential-uniformity check (Section 2.5)

`scripts/du_check.py` recomputes by exhaustive search the differential uniformity of the switched inverse core Q(x) = i(x + δ_T(x)), with T = {x : Tr(i(x)) = Tr(i(x+1)) = 1}, over F_{2^n} for n = 4, 6, …, 16. The primitive polynomials are listed in the script and in the log. `scripts/du_log.txt` is the recorded output, which gives DU(Q) = 4 for every n. To reproduce: `python du_check.py 4 6 8 10 12 14 16`.

## Compression measurement (Table S10)

`scripts/compress_check.py <folder>` computes `TableS10_compression.csv` from the plaintext and ciphertext PNG files written by `matlab/SGEM_RGB24.m` (`*_plain.png` and `*_cipher.png`, written when `cfg.saveImages = true`). It documents the serialization (row-major interleaved RGB, 3HW bytes), the codec settings and the library versions. The conclusions apply only to the six tested images and the three tested codecs.

## Scope of this repository

This repository provides the complete MATLAB implementation, supplementary tables (S1–S10), supplementary figures (S1–S2), evaluation formulas, vector sources and generating scripts for Figs. 1–3, the 600-dpi Fig. 4, the differential-uniformity check and log, and the compression-measurement script.

The plaintext and ciphertext PNG files used for the archived compression table are not redistributed; the six plaintext images can be obtained from the sources listed in Table S3, and the archived ciphertext byte counts appear in `TableS10_compression.csv`. For every reported ciphertext, `matlab/reported_run_records.csv` gives the authenticated header (which encodes the image height and width, the round count, the bit depth, the number of channels and the channel-order code, where 1 denotes RGB), the 128-bit nonce and the 256-bit authentication tag. The reported run used a randomly generated master key, which is not published. A rerun of `matlab/SGEM_RGB24.m` therefore uses a fresh key, and its statistics are expected to agree with the archived tables within sampling variation.

Code is released under the MIT License. Third-party image rights and attribution remain with the sources listed in Table S3.
