# Density Profile

## Step 1: Generate Green's Functions

- Use **`Create_Green_Function_njit.ipynb`** if you **do not have a GPU**.
- Use **`Create_Green_Function_njit_cupy.ipynb`** if you **have a GPU**.

> ⚠️ **Note:** The use of `@njit` (from Numba) is essential for speeding up the core numerical loops. It compiles Python functions to fast machine code, making the computation feasible in a reasonable amount of time.

The file `Green_R0pt75_H0pt2_N500_M200_posiE100_epsE-10.0.npy` was used in both the *Rydberg FM* paper and the *plasmon* paper.

## Step 2: Calculate Density Profiles for Desired Voltage Configurations

- Use **`Calculate_Density_Profile.ipynb`** to compute the electron density profiles for the voltage configurations you're interested in.



