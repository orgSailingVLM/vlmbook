# Usage

```{note}
First usage of pySailingVLm will produce numba warining. This behaviour is correct. Warining messages will disappear during second run of program.

Example warning:

/home/zuzanna/Documents/miniconda3/envs/sv_build_test_2/lib/python3.10/site-packages/numba/core/lowering.py:107: NumbaDebugInfoWarning: Could not find source for function: <function __numba_array_expr_0x7fbf333f1780 at 0x7fbf33361b40>. Debug line information may be inaccurate.
```
## Run from command line
### input file
In order to run pySailingVLM from command line you must provide a variable.py file. Example file is shown below. Modify it for your needs.
```
import os
import numpy as np
import time

# OUTPUT DIR
case_name = os.path.basename(__file__)  # get name of the current file
case_dir = os.path.dirname(os.path.realpath(__file__))  # get dir of the current file
time_stamp = time.strftime("%Y-%m-%d_%Hh%Mm%Ss")
output_dir_name = os.path.join("results_example_jib_and_mainsail_vlm", time_stamp)
file_name = 'my_fancy_results' # name of xlsx excel file

# SOLVER SETTINGS
n_spanwise = 4  # No of control points (above the water) per sail, recommended: 50
n_chordwise = 1 # No of control points (above the water) per sail, recommended: 50
interpolation_type = "linear"  # either "spline" or "linear"
LLT_twist = "real_twist"  # defines how the Lifting Line discretize the sail twist.
# It can be "sheeting_angle_const" or "average_const" or "real_twist"

# SAILING CONDITIONS
leeway_deg = 0.    # [deg]
heel_deg = 0.     # [deg]
SOG_yacht = 0.   # [m/s] yacht speed - speed over ground (leeway is a separate variable)
tws_ref = 1.     # [m/s] true wind speed
alpha_true_wind_deg = 0#10.   # [deg] true wind angle (with reference to course over ground) => Course Wind Angle to the boat track = true wind angle to centerline + Leeway
reference_water_level_for_wind_profile = 0.  # [m] this is an attempt to mimick the deck effect
# by lowering the sheer_above_waterline
# while keeping the wind profile as in original geometry
# this shall be negative (H = sail_ctrl_point - water_level)
wind_exp_coeff = 0.  # [-] coefficient to determine the exponential wind profile
wind_reference_measurment_height = 10.  # [m] reference height for exponential wind profile
rho = 1.225  # air density [kg/m3]
wind_profile = 'flat' # allowed: 'exponential' or 'flat' or 'logarithmic'
roughness = 0.05 # for logarithmic profile only

# GEOMETRY OF THE RIG
main_sail_luff = 0.5#10. # 12.4  # [m]
jib_luff = 10.0  # [m]
foretriangle_height = 11.50  # [m]
foretriangle_base = 3.90  # [m]
sheer_above_waterline = 0.  # [m]
boom_above_sheer = 0. #1.3  # [m]
rake_deg = 45+90.  # rake angle [deg]
mast_LOA = 0.0  # [m]

# INPUT - GEOMETRY OF THE SAIL
sails_def = 'main' # definition of sail set, possible: 'jib' or 'main' or 'jib_and_main'
# sails_def = 'main'
main_sail_girths = np.array([0.00, 1./8, 1./4, 1./2, 3./4, 7./8, 1.00])
main_sail_chords = np.array([0.2]* len(main_sail_girths)) # np.array([4.00, 3.82, 3.64, 3.20, 2.64, 2.32, 2.00])
main_sail_centerline_twist_deg = -2 + 0* main_sail_girths # 10 + 12. * main_sail_girths  #

# First digit describing maximum camber as percentage of the chord.
# Second digit describing the distance of maximum camber from the airfoil leading edge in tenths of the chord.
jib_sail_camber= 0*np.array([0.01, 0.01, 0.01, 0.01, 0.01])
jib_sail_camber_distance_from_luff = np.array([0.5, 0.5, 0.5, 0.5, 0.5]) # starting from leading edge
main_sail_camber= 0*np.array([0.01, 0.01, 0.01, 0.01, 0.01, 0.01, 0.01])
main_sail_camber_distance_from_luff = np.array([0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]) # starting from leading edge

jib_girths = np.array([0.00, 1./4, 1./2, 3./4, 1.00])
jib_chords = 1E-12* np.array([3.80, 2.98, 2.15, 1.33, 0.5])
jib_centerline_twist_deg =  0*(10+5)  + 0*15. * jib_girths # (10+5)  + 15. * jib_girths # 

# REFERENCE CSYS
# The origin of the default CSYS is located @ waterline level and aft face of the mast
# The positive x-coord: towards stern
# The positive y-coord: towards leeward side
# The positive z-coord: above the water
# To shift the default CSYS, adjust the 'reference_level_for_moments' variable.
# Shifted CSYS = original + reference_level_for_moments
# As a results the moments will be calculated around the new origin.

# yaw_reference [m] - distance from the aft of the mast towards stern, at which the yawing moment is calculated.
# sway_reference [m] - distance from the aft of the mast towards leeward side. 0 for symmetric yachts ;)
# heeling_reference [m] - distance from the water level,  at which the heeling moment is calculated.
reference_level_for_moments = np.array([0, 0, 0])  # [yaw_reference, sway_reference, heeling_reference]

# GEOMETRY OF THE KEEL
# to estimate heeling moment from keel, does not influence the optimizer.
# reminder: the z coord shall be negative (under the water)
center_of_lateral_resistance_upright = np.array([0, 0, -1.0])  # [m] the coordinates for a yacht 
```

### Run script
To run script with variables.py located in working directory:
```
pySailingVLM
```
If variables.py is located in different directory, you must sepecify its location by providing additional option for pySailingVLM script:

```
pySailingVLM --dvars path_to_foler_with_variables.py
```

More information is available inside script help:
```
pySailingVLM --help
```
### Output
pySailingVLM produces output files: data in xlsx file, matplotlib figures and pressure coefficient colormap in html extention (interactive plot). It is saved in the location specified in varaibles.py.





## Run from python
```
from sailing_vlm.runner import aircraft as a
import numpy as np
chord_length = 1.0             
half_wing_span = 5.0 
AoA_deg = 10.
sweep_angle_deg = 0.
tws_ref = 1.0
V = np.array([tws_ref, 0., 0.])
rho = 1.225
gamma_orientation = -1.0
n_spanwise = 32  # No of control points (above the water) per sail, recommended: 50
n_chordwise = 8 #?
b = a.Aircraft(chord_length, half_wing_span, AoA_deg, n_spanwise, n_chordwise, V, rho, gamma_orientation)
b.Cxyz
>>> (0.023472780216173314, 0.8546846987984326, 0.0) 
```

## jupyter notebook
Patrz dołącznoy plik notebooka.


