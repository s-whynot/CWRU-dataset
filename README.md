# Case Western Reserve University (CWRU) Bearing Dataset

A publicly available benchmark dataset for research and experimentation in rolling-element bearing fault diagnosis and condition monitoring.

The dataset contains vibration measurements collected from normal and faulty bearings under different operating conditions. It is widely used in machine learning, signal processing, and predictive maintenance research.

## Official Dataset Source

The original dataset is provided by the Case Western Reserve University Bearing Data Center.

- **Official download page:** https://engineering.case.edu/bearingdatacenter/download-data-file

Please refer to the official source for the original data files and additional experimental documentation.

## Dataset Overview

The CWRU Bearing Dataset includes measurements from:

- Normal bearings.
- Bearings with single-point faults on the drive-end bearing.
- Bearings with single-point faults on the fan-end bearing.

The fault conditions include defects affecting the bearing's rolling elements and raceways.

The experiments include measurements collected under different motor loads and sampling frequencies.

## Sampling Frequencies

The dataset includes the following sampling configurations:

| Experiment | Sampling Frequency |
|---|---:|
| Drive-end bearing experiments | 12,000 samples/second |
| Drive-end bearing experiments | 48,000 samples/second |
| Fan-end bearing experiments | 12,000 samples/second |

The sampling frequency should be checked when selecting recordings for an experiment. Signals from different sampling configurations may require resampling before direct comparison.

## Dataset Directory Structure

The files are organized into directories according to the measurement configuration and bearing location.

The repository includes:

```text
CWRU-dataset/
│
├── 12k_Drive_End_Bearing_Fault_Data/
│
├── 12k_Fan_End_Bearing_Fault_Data/
│
├── 48k_Drive_End_Bearing_Fault_Data/
│
└── Normal/
```

The directories contain MATLAB `.mat` files representing different bearing conditions and experimental operating loads.

## Measurement Channels

The MATLAB files contain vibration measurements from accelerometers positioned at different locations, as well as motor rotational speed information where available.

| Variable Identifier | Description |
|---|---|
| `DE` | Drive-end accelerometer signal |
| `FE` | Fan-end accelerometer signal |
| `BA` | Base accelerometer signal |
| `time` | Time-series measurement |
| `RPM` | Motor rotational speed |

For example:

```text
X118_DE_time
X118_FE_time
X118_BA_time
X118RPM
```

These variable names represent drive-end, fan-end, and base vibration measurements, together with rotational speed, for the corresponding experimental recording.

Not every MATLAB file necessarily contains all measurement channels or RPM information.

## Bearing Fault Categories

The dataset includes the following bearing conditions:

| Category | Description |
|---|---|
| Normal | Healthy bearing condition |
| Ball Fault | Single-point defect on a rolling element |
| Inner Race Fault | Single-point defect on the inner raceway |
| Outer Race Fault | Single-point defect on the outer raceway |

Fault recordings are available with different defect diameters and, for outer race faults, different defect positions.

Researchers should inspect the original file names and official dataset documentation to identify the fault diameter, bearing location, position, and operating condition associated with each recording.

## MATLAB Data Files

The measurements are distributed in MATLAB `.mat` format.

Python users can load these files using SciPy:

```python
from scipy.io import loadmat

data = loadmat("path/to/recording.mat")

print(data.keys())
```

Individual measurement channels can then be accessed using their corresponding MATLAB variable names.

MATLAB users can load the files directly:

```matlab
data = load('recording.mat');

whos('-file', 'recording.mat')
```

## Working with the Dataset

When preparing the data for bearing fault diagnosis experiments, consider the following:

1. Identify the bearing condition and fault characteristics of each recording.
2. Check the sampling frequency of the selected signals.
3. Select the appropriate accelerometer channel for the experiment.
4. Account for differences in motor load and operating conditions.
5. Apply appropriate signal preprocessing and segmentation.
6. Avoid mixing training and testing windows from the same original recording when evaluating generalization to unseen recordings.

## Citation and Attribution

The dataset originates from the Case Western Reserve University Bearing Data Center.

Researchers should acknowledge the original dataset source in publications and consult the official dataset documentation for citation requirements.

**Official source:**  
https://engineering.case.edu/bearingdatacenter/download-data-file

