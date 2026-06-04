## Additional Detail: Stripped Leakage Sensitivity

### A leakage check, not a mechanism claim

The vocabulary-stripping analysis removes conditioned concepts whose embeddings are closest to the relevant persona-profile sentences before recomputing centroid-based recoverability. At the moderate 0.5 threshold, 92.3% of concepts are retained. Persona recoverability drops from 0.110 to 0.081, paired bootstrap delta -0.030 [95% CI -0.051, -0.012], suggesting that profile-proximate concepts carry some persona-surface signal. Model recoverability does not collapse: it changes from 0.836 to 0.863, delta +0.027 [0.009, 0.048]. At the 0.4 threshold, model recoverability remains 0.857, with delta +0.021 [-0.006, 0.048]. We will not use this as mechanistic proof; it is a robustness check showing that the strong model-signature result is not explained by the most profile-proximate concepts.
