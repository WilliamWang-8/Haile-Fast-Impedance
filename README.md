# hybdrt Installation Guide

The guide outlines the process to get [hybdrt]([https://pages.github.com/](https://github.com/jdhuang-csm/hybrid-drt) running on a local computer (following the instructions outlined after reading the current GitHub guide as of May 2025, since the fit requires an earlier version of Python due to outdated function call references is recommended.) Documentation is specifically written for Biologic instruments in the Haile Group in mind.

"Sample Settings Files" provides two working EC lab settings files for hybrid measurement. "test_cell_full_resistance" is the sample settings file for the Biologic test cells with a resistance ~10,000Ω (EIS: 100kHz to 100Hz & CP:0.010mA from 0.01s to 10s in 10x steps). "STM5050_Jinwook_I_0" is the sample settings file for the STM5050 films developed by Jinwook Kim with a resistance ~40,000Ω (EIS: 7E6Hz to 10Hz & CP: 0.075μA from 0.001s to 100s in 10x steps.)

## Measurement Parameters

Hybrid EIS measurement requires a general understanding of the resistive behavior of the electrochemical cell of interest and a frequency range of interest. 

1. Convert the frequency scale into a log scale
2. Determine the log scale range
3. Decide where the overlap of EIS and chronopotentiometry (CP) measurement should be made, i.e., EIS upper 2/3 and CP lower 2/3 (example overlap of 1/3 to confirm fit accuracy)
4. Determine corresponding log scale parameters
5. Convert log scale to frequency, then to seconds (recommend with starting applied current time no shorter than 0.001s and increasing time steps by 10x)
6. Determine current range using V=IR

## Export

The order of headers does not matter
EIS: TXT export w/time, frequency, real impedance, and imaginary impedance
CP: TXT export w/time, current, and voltage

## Fit

To accommodate fits with CP measurements made on Biologic instruments, replace the "fileload.py" file with the one in this folder. A sample notebook with fits made with measurements from both settings files is provided. CSV exports are also possible.


## Notes:

CP in setting files contains open circuit voltage steps of 1s for the first step and 5s for the last step
Ensure that for positive currents, "Limits: Ewe>EM" is set to a positive voltage value and a negative value for negative currents
Set "I Range" to "Auto"
Set "E Range" to the appropriate voltage range
