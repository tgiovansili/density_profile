# Density Profile

**Note:**  
This discrete numerical simulation is based on:  
L. Wilen and R. Giannetta, *Impedance Methods for Surface State Electrons*, J. Low Temp. Phys. **72**, 353–369 (1988). [https://doi.org/10.1007/BF00682147](https://doi.org/10.1007/BF00682147)  
Intermediate steps follow CGS units; final results are converted to SI.

## Step 1: Generate Green's Functions

- Use **`Create_Green_Function_njit.ipynb`**.
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
> ⚠️ **Note:** Please note that there may be more effective ways to optimize the program using `njit` or `cupy` more appropriately than what we implemented above.  
It is important **not to use** `njit` and `cupy` together.  
`njit` compiles functions to run on the CPU, while `cupy` manages data on the GPU.  
Using only `cupy` may result in longer execution times, depending on the situation.  
(Here is a link where this issue is discussed: [https://github.com/numba/numba/issues/8784](https://github.com/numba/numba/issues/8784))


> 
This notebook includes an example with the following settings:

- $V_\mathrm{ib} = 10$ V
- $V_\mathrm{ob} = -32$ V
- $V_\mathrm{mb}$ is swept from $-32$ V to $10$ V, while keeping the total number of electrons fixed  
  (determined from the saturation condition at $V_\mathrm{ib} = 10$ V and $V_\mathrm{mb} = V_\mathrm{ob} = -32$ V).

The DC potential created by the applied electrode voltages, $\tilde{\phi}$, is stored as:

```
VmbSweep/Vib10V_Vobm32V/Phi_R0pt75_H0pt2_N500_M200_posiE100_epsE-10.0_Vmb_step=0pt2_Vmb_start=-32_Vmb_stop=10.npy
```

The density profile obtained for each value of $V_\mathrm{mb}$ is plotted as shown below  
(**red** corresponds to $V_\mathrm{mb} = 9.8$ V and **blue** to $V_\mathrm{mb} = -32$ V):

<img width="636" height="472" alt="Density Profile Plot" src="https://github.com/user-attachments/assets/efa95119-4b55-47aa-bd62-f3bbe9a1d4cd" />

The data is stored in:

```
VmbSweep/Vib10V_Vobm32V/fixed_electron_number_density/
```

---

## Step 3: Use the Results

- Use the computed density profiles to calculate the electric field experienced by the electron in the *Rydberg detection simulation*,  
  or to calculate the plasmon impedance for the *plasmon simulation*.

---

  ⚠️ Due to the large file size, the generated folders `GreenFunction/` and `VmbSweep/` could not be uploaded to GitHub.

Please refer to the following Google Drive link to access the data:

🔗 [Google Drive – GreenFunction and VmbSweep Data](https://drive.google.com/drive/folders/1lC1xuzMQvBS7sev4N5r9cZi6F-KcE2N-?usp=sharing)

