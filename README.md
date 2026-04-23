Global View (1×1001) ──► 1D CNN + 8-head MHA ──► h_g ∈ R^256 ─┐
Local View  (1×1001) ──► 1D CNN + 8-head MHA ──► h_l ∈ R^256 ─┼──► Concat (640-d)
Stellar Params  (8,) ──► MLP (64→128)         ──► h_s ∈ R^128 ─┘
                                                        │
                                              Residual Fusion MLP
                                              (512 → 256, dropout 0.4)
                                                        │
                                              Classifier (256→64→2)
                                                        │
                                              Temperature Scaling T*=1.573
                                                        │
                                              P(planet) ∈ [0, 1]
