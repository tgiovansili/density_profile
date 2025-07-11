# Density Profile

## Step 1: Generate Green's Functions

- Use **`Create_Green_Function_njit.ipynb`** if you **do not have a GPU**.
- Use **`Create_Green_Function_njit_cupy.ipynb`** if you **have a GPU**.

> ⚠️ **Note:** The use of `@njit` (from Numba) is essential for speeding up core numerical loops. It compiles Python functions into fast machine code, enabling efficient computation.

The Green's function computed with a threshold error of $10^{-10}$ is stored as:

```
GreenFunction/Green_njit_R0pt75_H0pt2_N500_M200_posiE100_epsE-10.npy
```

This file was used in both the *Rydberg FM* paper and the *Plasmon* paper.

---

## Step 2: Calculate Density Profiles for Voltage Sweeps

- Use **`Calculate_Density_Profile.ipynb`** to compute electron density profiles for your desired voltage configurations.
- Use **`Calculate_Density_Profile_cupy.ipynb`** if you have a GPU.

This notebook includes an example with the following settings:

- $V_\mathrm{ib} = 10\,\mathrm{V}$
- $V_\mathrm{ob} = -32\,\mathrm{V}$
- $V_\mathrm{mb}$ is swept from $-32\,\mathrm{V}$ to $10\,\mathrm{V}$, while keeping the total number of electrons fixed  
  (determined from the saturation condition at $V_\mathrm{ib} = 10\,\mathrm{V}$ and $V_\mathrm{mb} = V_\mathrm{ob} = -32\,\mathrm{V}$).

The DC potential created by the applied electrode voltages, $\tilde{\phi}$, is stored as:

```
VmbSweep/Vib10V_Vobm32V/Phi_R0pt75_H0pt2_N500_M200_posiE100_epsE-10.0_Vmb_step=0pt2_Vmb_start=-32_Vmb_stop=10.npy
```

---

## Step 3: Use the Results

- Use the computed density profiles to calculate the electric field experienced by the electron in the *Rydberg detection simulation*,  
  or to calculate the plasmon impedance for the *plasmon simulation*.
