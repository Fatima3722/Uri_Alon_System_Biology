# Autoregulation - A Network Motif

This directory contains the code and summary for Chapter 2 of Uri Alon's "An Introduction to Systems Biology". The focus is on understanding the first and simplest **network motif**: autoregulation, and specifically, the functional advantages of **Negative Autoregulation (NAR)**.

## Core Concepts Investigated

1.  **Network Motif:** The idea that some circuit patterns are not random but are "design principles" selected by evolution. We establish that NAR (a gene repressing itself) is a highly significant motif because it appears far more frequently in real biological networks than in randomly-wired ones.

2.  **Functional Advantages of NAR:** The key question is *why* this motif is so common. The code in this directory aims to computationally prove its two main benefits over a simple, non-regulated gene circuit:
    *   **Speed:** NAR circuits can reach a target protein level much faster.
    *   **Robustness:** The final protein level in an NAR circuit is much more stable and resistant to noise in the cell's production machinery.

## Code Implementation: `Autoregulation.ipynb`

The Python script `Autoregulation.ipynb` provides a computational demonstration of these two advantages. It directly compares a **Simple Regulation** circuit with a **Negative Autoregulation (NAR)** circuit in a "mathematically controlled comparison," where both are designed to reach the same final protein level.

### Demonstration 1: NAR is Faster

The first part of the script simulates both circuits starting from zero protein.

-   **The Plot:** The generated plot visually confirms that the NAR circuit (in red) reaches the target steady state much more quickly than the simple regulation circuit (in blue). This is the "floor the gas, then hit the brakes" strategy in action.

  

-   **The Output:** The script prints the numerical response times (`T_1/2`) for both circuits, showing a significant speedup factor for the NAR design.

### Demonstration 2: NAR is More Robust

The second part of the script analyzes what happens when the production rate (`β`) fluctuates by 20%.

-   **The Analysis:** The code calculates the final steady-state protein level for both circuits under nominal, high (+20%), and low (-20%) production rates.
-   **The Output:** The printed results show that while the simple circuit's output fluctuates by ~20%, the NAR circuit's output remains incredibly stable, fluctuating by only ~1-2%. This confirms that NAR provides robustness.

### How to Run the Code

1.  Ensure you have Python and the required libraries installed:
    ```bash
    pip install numpy matplotlib scipy
    ```
2.  Navigate to this directory (`/Autoregulation/`).
3.  Run the script from your terminal:
    ```bash
    Autoregulation.ipynb
    ```
The script will first display the plot comparing the response times. After you close the plot window, it will print the numerical results for the robustness analysis to your console.
