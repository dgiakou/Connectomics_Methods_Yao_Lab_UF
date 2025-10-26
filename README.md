# Connectomics_Methods_Yao_Lab_UF
Dataset & IDs. We queried FlyWire FAFB v783 in Codex for sensory roots of the pharyngeal (PhN) and accessory pharyngeal (aPhN) nerves (nerve==PhN && super_class==sensory; nerve==aPhN) and downloaded “Cell IDs.” Unless noted, analyses used the v783 default synapse predictions (Buhmann et al., 2021). Note: newer Princeton predictions (Yu et al., 2025) exist; all results here reference the v783 defaults.

Filtering. Following FlyWire convention (Dorkenwald et al., 2023), edges with <5 synapses were removed, yielding 71 PhN sensory roots and 84 aPhN sensory roots.

Clustering. Sensory axons were clustered by similarity of downstream output partners (cosine similarity; hierarchical ward.D2). Clusters were inspected in Neuroglancer for morphological coherence, which aligned with the connectivity-based groupings. Environment: R 4.4.2 (DataSpell Jupyter); coconatfly v0.2.4.

Axon identities. We treat the internal gustatory system as DCSO, VCSO, LSO, and StN. aPhN corresponds to VCSO+LSO; PhN comprises StN+DCSO. Twelve PhN roots were assigned to DCSO based on (i) fasciculation with aPhN1 after entering the brain, (ii) clustering with aPhN1 by outputs, and (iii) shared gross morphology, consistent with prior anatomy (Kendroud et al., 2018). Remaining PhN sensory afferents were treated as StN (i.e., foregut/crop/midgut afferents), analyzed separately from pharyngeal sensory-organ axons.

Connectivity analyses (2–3 hops). Using code adapted from Walker, Peña-Garcia & Devineni (2025), we computed second- and third-order (2N/3N) downstream sets from each sensory cluster. For each hop, a source→target connection was retained if the summed synapses across neuropils ≥5; previously visited nodes were removed from deeper orders to avoid redundancy. We limited depth to 2–3 hops for interpretability and to curb combinatorial growth.

Visualizations.
• Superclass bars: 2N and 3N neurons binned by FlyWire superclass (Schlegel et al., 2023).
• NT bars (SEZ vs non-SEZ): Neurotransmitter predictions from Eckstein et al. (2024). For interpretation in brain taste circuits, ACh is typically excitatory; GABA and Glu often act inhibitory via receptor context in the SEZ, though glutamate can be excitatory in other circuits (e.g., NMJ and select CNS pathways). Treat NT predictions cautiously due to classifier error, co-transmission, receptor heterogeneity, and segmentation artifacts.
• Non-SEZ regional bars: excitatory/inhibitory composition per synapse by neuropil outside the SEZ (SEZ includes GNG, PRW, SAD, FLA_L/R, CAN). Top regions shown capture the bulk of non-SEZ synapses.


Terminology. We refer to these FAFB “neurons” as sensory axons (roots) because somata reside outside the brain (e.g., stomodeal neurons in the hypocerebral ganglion) and project via bilaterally symmetric recurrent nerves to the anterior tritocerebrum (Kendroud et al., 2018; Mahishi & Huetteroth, 2019; Min et al., 2021).

MxLbN inclusion. MxLbN axons were analyzed using FlyWire’s default gustatory receptor annotations (cf. Li et al., 2024; Walker et al., 2025).

Software & availability. R 4.4.2; Python 3.12; coconatfly v0.2.4; Neuroglancer. Data: FlyWire FAFB v783 (Codex). Code: adapted from Walker et al. (2025) plus custom scripts (to be deposited).
