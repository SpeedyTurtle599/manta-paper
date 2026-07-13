# Figure checklist for manta.tex

Drop each file into this directory with the exact name below and it appears in
the paper automatically on the next compile — the `\figplace` macro renders a
framed placeholder until the file exists, then switches to `\includegraphics`.
No tex edits needed. Use **hyphens** in any new filenames (underscores break
the placeholder label).

Vector (`.pdf`) for line plots/diagrams; raster (`.png`, ~300 dpi at final
width) for field renders. Final widths are 0.9\linewidth (~6.3 in) unless
noted.

| File | Content | Source / how to generate |
|---|---|---|
| `fig-hero-cylinder.png` | Split-pane T (left) vs T_ve (right) over the cylinder, bow shock visible; the hero image. | Run `examples/2d_cylinder_dissociation`, render VTKHDF in ParaView. |
| `fig-data-model.pdf` | Diagram: SoA `Field` block centre; structured ijk + unstructured CSR topologies feeding one reconstruction→Riemann→flux kernel row; ghost cells drawn as ordinary cells at the tail of the index range. | Draw (TikZ/Illustrator/draw.io). |
| `fig-mms-spatial.pdf` | Two panels, log-log: (L) reconstruction front-end L∞ vs h, slopes 1/2/4/5; (R) full-operator interior L2 vs h, slope 2 + sweep-aligned slope 5. | Data printed by `ReconConvergence/*`, `MmsEuler.*`, `StructuredMms*` tests; matplotlib. |
| `fig-temporal-order.pdf` | Log-log L2 error vs Δt for SSP-RK3 / BEuler / BDF2 / ESDIRK3, slope guides 1/2/3. Width 0.6\linewidth. | Data printed by `TemporalConvergence` test; matplotlib. |
| `fig-carbuncle-gallery.png` | Three density panels of the seeded M6 standing shock: hlle (flat), roe (carbuncle), roe+carbuncleFix (healed). | `test_carbuncle.cpp` harness states; dump fields or re-run the harness config in the solver. |
| `fig-dmg-lambda.pdf` | Bar chart of max Re λ per flux function, coloured by empirical verdict (flat/carbuncle/diverges); highlight ausm_plus_up (−10.4, stable-yet-diverging); rotated pair marked deferred. Width 0.7\linewidth. | Numbers in Table 9 of the paper / `test_carbuncle_stability.cpp` output; matplotlib. |
| `fig-jacobian-spy.pdf` | Side-by-side spy plots: compact nearest-neighbour Pmat vs wide 13-point MUSCL star, small mesh (e.g. 8×8). | Assemble both operators on a tiny case, dump COO/Mat, `plt.spy`. |
| `fig-newton-endgame.pdf` | Residual vs iteration: classical SER run vs certified endgame run on the same case (annulus/Ringleb-class certified config). | `test_newton_endgame` / a certified validation case with and without `newtonForce`; convergence.csv. |
| `fig-mbob-binning.pdf` | Schematic: line spectrum within one band coloured by opacity bin (top) vs single grey opacity smearing it (bottom). | Draw, or render an actual κ_η slice from the opacity-table generator. |
| `fig-exact-benchmarks.png` | Three panels: Shu–Osher density overlay (weno5/teno5/muscl vs N=800 reference); Sedov contours + radial profile vs Kamm–Timmes; Noh radial profile vs 16ρ₀ plateau. | `test_shu_osher.cpp`, `test_sedov_noh.cpp` states; matplotlib + field dump. |
| `fig-ringleb-annulus.png` | Mach contours + streamlines on the quarter-annulus vortex and Ringleb meshes (meshes underlaid). | `test_annulus_vortex.cpp`, `test_ringleb.cpp` configs; ParaView. |
| `fig-inviscid-suite.png` | 2×3 composite (a–e): oblique ramp, PM fan, regular reflection, Taylor–Maccoll cone (annotate β_meas=20.05°, β_exact=20.03°, β_wedge=24.32°), Billig sphere with correlation hyperbola overlay. Width 0.9\linewidth, ~9 cm tall. | `tests/validation/` cases dump VTKHDF (`dumpVolumeVtkHdf`); ParaView + annotation. |

## Commented stubs (in manta.tex, uncomment when ready)

- `fig-sbli-unit-rung.pdf` — flat-plate + sharp-cone Cf√Rex / St√Rex station
  plots vs self-similar datum. Uncomment after the 4.2 gates close.
- `fig-fireii-bands.pdf` — FIRE-II per-band radiance, MANTA vs NEQAIR.
  Uncomment only when the red gate closes.
