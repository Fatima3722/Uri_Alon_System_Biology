# Temporal-Programs-and-the-Global-Structure-of-Transcription-Networks

This directory contains the code and summary for Chapter 4 of Uri Alon's "An Introduction to Systems Biology". This chapter moves beyond simple motifs to explore how they are combined to control groups of genes, creating sophisticated **temporal (time-ordered) programs**.

## Core Concepts Investigated

The central question of this chapter is: how does a cell turn on a set of genes not just all at once, but in a specific, scheduled sequence? We explore two major motifs that solve this problem:

1.  **Single-Input Module (SIM):** A simple motif where one master regulator (`X`) controls a group of target genes (`Z1, Z2, ...`). By setting different activation thresholds (`K`) for each target, the SIM can generate a **LIFO (Last-In, First-Out)** temporal program. The last gene to turn on is the first to turn off.

2.  **Dense Overlapping Regulon (DOR) / Multi-Output FFL:** A more complex motif where two regulators in an FFL cascade (`X → Y`) jointly control a group of target genes. By setting an opposing hierarchy of thresholds for `X` and `Y`, this circuit can generate a **FIFO (First-In, First-Out)** temporal program. The first gene to turn on is also the first to turn off. This is crucial for efficient assembly-line processes.

## Code Implementation: `Temporal Programs and the Global Structure of Transcription Networks.ipynb`

The Python script `Temporal Programs and the Global Structure of Transcription Networks.ipynb` computationally demonstrates these two distinct temporal programs. It simulates a master regulator `X` whose concentration rises and then falls, and it shows how the SIM and DOR motifs respond differently to this signal.

The script generates a single figure with two plots, which are described below.

### Plot 1: The SIM Generates a LIFO Program

This simulation shows three output genes (`Z1, Z2, Z3`) controlled by a single input `X`. The activation thresholds (`K`) for the genes are set in increasing order.


-   **Turn-ON Order:** As the regulator `X` (black dashed line) rises, it crosses the thresholds in order from lowest to highest. The output genes activate sequentially: **Z1 (red) → Z2 (green) → Z3 (blue)**.
-   **Turn-OFF Order:** As `X` falls, it drops below the highest threshold first. The genes deactivate in the reverse order: **Z3 (blue) → Z2 (green) → Z1 (red)**.
-   **Conclusion:** The activation order is the reverse of the deactivation order, clearly demonstrating a **LIFO** program.

### Plot 2: The DOR Generates a FIFO Program

This simulation shows three output genes controlled by an `X→Y` FFL cascade with OR-logic. The thresholds for `X` are increasing, while the thresholds for `Y` are decreasing.

-   **Turn-ON Order:** The turn-on order is determined by the fast regulator `X`. Since its thresholds are increasing, the activation order is again: **Z1 (red) → Z2 (green) → Z3 (blue)**.
-   **Turn-OFF Order:** When `X` disappears, the slower regulator `Y` (gray dashed line) keeps the genes ON. As `Y` falls, it drops below the highest `Ky` threshold first (which belongs to Z1). Therefore, the deactivation order is: **Z1 (red) → Z2 (green) → Z3 (blue)**.
-   **Conclusion:** The activation order is the same as the deactivation order, demonstrating a **FIFO** program. This is ideal for "just-in-time" assembly and clean shutdown.

## How to Run the Code

1.  Ensure you have Python installed with the necessary libraries:
    ```bash
    pip install numpy matplotlib scipy
    ```
2.  Navigate to this directory (``).
3.  Run the script from your terminal:
    ```bash
    python Temporal Programs and the Global Structure of Transcription Networks.ipynb
    ```
The script will generate the plot containing both demonstrations.
