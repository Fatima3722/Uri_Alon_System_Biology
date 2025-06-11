# Network_Motifs_1

This repository contains the Python code to simulate the simple gene regulation model.

The primary goal of this code is to numerically solve the core differential equation of the chapter and visually demonstrate its key properties, especially the "speed limit" of its response time.

## The Model: Simple Regulation

The dynamics of the protein concentration `Y` are described by the following ordinary differential equation (ODE):

`dY/dt = β - αY`

### Model Parameters

The behavior of the simulation is controlled by these parameters, which are defined at the top of the `Network_Motifs_1.ipynb` script:

*   **`β` (beta): Production Rate**
    *   **Meaning:** The constant rate at which protein `Y` is produced. Biologically, this represents the strength of the gene's promoter.
    *   **Units:** Concentration / Time (e.g., molecules per second).
    *   **In the code:** `beta = 10.0` (and `beta_new = 20.0` for comparison).

*   **`α` (alpha): Removal Rate Constant**
    *   **Meaning:** The rate at which protein `Y` is removed from the system, either by active degradation or by dilution due to cell growth. It's a rate constant, so the total removal rate is `α * Y`.
    *   **Units:** 1 / Time (e.g., per second).
    *   **In the code:** `alpha = 2.0`

*   **`y0` : Initial Condition**
    *   **Meaning:** The concentration of protein `Y` at the very beginning of the simulation (at `t=0`).
    *   **In the code:** `y0 = 0.0` (we start with no protein).

*   **`t` : Time Vector**
    *   **Meaning:** The time points over which the simulation will run.
    *   **In the code:** `t = np.linspace(0, 5, 101)` (simulates from t=0 to t=5).

## How to Run the Code

1.  **Prerequisites:** Ensure you have Python and the following libraries installed:
    ```bash
    pip install numpy scipy matplotlib
    ```
2.  **Execute the Script:** Run the script from your terminal:
    ```bash
    python Network_Motifs_1.ipynb
    ```

## Expected Output

Running the script will produce two things:

### 1. Text Output in the Terminal

The script will print a verification of the theoretical concepts:

Production rate (beta): 10.0
Removal rate (alpha): 2.0
Theoretical steady state (beta/alpha): 5.0
Simulated steady state (final value): 5.0000
Theoretical response time (log(2)/alpha): 0.3466
Simulated response time (time to reach 2.50): 0.3500


*   **What this shows:** The simulation's final value perfectly matches the theoretical steady state (`β/α`). The time it took the simulation to reach 50% of this value also closely matches the theoretical response time (`log(2)/α`).

### 2. Plot Windows

Two plot windows will appear one after the other.

*   **Plot 1: Simple Gene Regulation Dynamics**
    *   **What it shows:** A single blue curve demonstrating how the protein concentration rises from 0 and levels off (saturates) at the steady-state value of 5.0. This is the fundamental behavior of the system.
    

*   **Plot 2: Response Time is Independent of Production Rate (beta)**
    *   **What it shows:** This is the key "punchline" plot.
    *   The **blue line (`β=10`)** goes to a steady state of 5.0. Its halfway point is 2.5.
    *   The **red line (`β=20`)** has a stronger promoter, so it goes to a higher steady state of 10.0. Its halfway point is 5.0.
    *   The **vertical black dashed line (`T_1/2`)** shows that both curves, despite going to different destinations, cross their respective halfway points at the *exact same time*.

      This simulation visually confirms the central lesson: for a simple gene circuit, the **response time is set by the removal rate (`α`), not the production rate (`β`)**. Increasing the promoter strength (`β`) makes more protein in the end, but it doesn't make the circuit *faster* in its characteristic response time. This creates a fundamental speed limit for cells, which they must have overcome with more clever circuit designs (network motifs).
