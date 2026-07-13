The paper currently has zero figures — everything is tables. For a solver paper that's a real gap: tables prove, but figures persuade and orient. In rough priority order:

Story-critical (would change how the paper reads):

A hero figure (Fig. 1). The 2d_cylinder_dissociation example is perfect: dissociating two-temperature flow over a cylinder, shown as a split-pane $T$ vs $T_{ve}$ field (or atomic-oxygen mass fraction). It says "thermal nonequilibrium solver" in one glance, before a single equation. Put it on page 2–3.
The one-data-model diagram. A hand-drawn schematic: the flat SoA Field in the middle; structured $ijk$ block and polyhedral CSR topology feeding the same reconstruction→Riemann→flux kernel row; ghost cells drawn as ordinary cells at the end of the index range. This is the load-bearing design idea and prose is working too hard to convey it.
MMS convergence plots (log-log error vs $h$: reconstruction front-end with slopes 1/2/4/5, full operator with slope 2 and the sweep-aligned slope-5 line; a second panel for temporal orders). V&V reviewers expect these; they'd complement Tables 2–4 and could shrink them.
Carbuncle gallery + stability chart. Density (or numerical-schlieren) snapshots of the M6 strip for three cases — a flat solver, Roe's carbuncle, Roe+H-fix healed — paired with a bar chart of $\lambda_{\max}$ per solver colour-coded by empirical verdict (with AUSM⁺-up's stable-yet-diverging bar highlighted). Table 7 is the evidence; this would be the argument.
Inviscid-validation composite. A 2×3 panel of Mach/pressure fields: oblique-shock ramp, PM fan, regular reflection, Taylor–Maccoll cone, Billig sphere. Annotate the cone with the measured vs exact shock angle and the wedge angle — the relieving effect as a picture. Add the Billig case with the correlation hyperbola overlaid on the captured shock. This becomes the centrepiece of Sec. VIII.J.
High value, cheap to produce:

Newton endgame residual history — residual vs iteration, classical SER vs the certified endgame dropping to machine zero. One plot tells the whole implicit-first + AD story.
Shu–Osher / Sedov / Noh gallery — the classic Shu–Osher density wiggles (WENO5/TENO5/MUSCL vs reference); Sedov 2-D density contours showing isotropy plus radial scatter against the Kamm–Timmes profile line. Pretty and evidentiary.
AMR vortex figure — the isentropic vortex mid-crossing of the 2:1 patch with mesh edges overlaid; inset bar chart of bulk/band/global orders vs the uniform control.
Jacobian sparsity spy plots — compact 5-point pattern vs the wide 13-point AD star from an actual small-mesh assembly. Trivially obtainable, visually striking, and makes Sec. IV.E concrete.
Ringleb or annulus vortex — curved mesh + Mach contours with streamlines; elegant filler for the curvilinear-metrics story.
For later revisions: the flat-plate $C_f\sqrt{Re_x}$/$\mathrm{St}\sqrt{Re_x}$ station plots against the self-similar datum (when the 4.2 gates close), a FIRE-II per-band radiance bar chart MANTA-vs-NEQAIR (once the spectral rungs land), and an MBOB concept sketch (a line spectrum coloured by opacity bin, showing why one grey band collapses the VUV).