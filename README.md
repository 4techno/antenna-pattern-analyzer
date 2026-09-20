# Antenna Radiation Pattern Analyzer

An automated RF instrumentation and visualization suite for characterizing directional antennas. It interfaces with stepper-driven dual-axis measurement rigs, logs power values across azimuth and elevation angles, and computes essential antenna metrics including 3dB beamwidth, front-to-back (F/B) ratio, and side-lobe levels.

## Features

- **Automated Angle-to-Power Mapping**: Synchronizes angular turntable stepper positions with RF power sensor readings.
- **Polar & Rectangular Plots**: Generates publication-ready 2D polar radiation diagrams and normalized Cartesian gain curves.
- **Automated Metric Extraction**:
  - Half-Power Beamwidth (HPBW / 3dB beamwidth)
  - Front-to-Back Ratio (F/B) in dB
  - First Side Lobe Level (SLL) relative to main beam peak
- **Synthetic Test Mode**: Built-in mathematical model generator for dipole, horn, and Yagi-Uda arrays when operating offline without hardware rigs.

## Mathematical Formulation

Normalized field pattern calculations:
$$F(\theta) = \frac{|E(\theta)|}{|E_{max}|}$$

Normalized power in decibels:
$$P_{dB}(\theta) = 20 \log_{10} F(\theta)$$

Beamwidth is calculated as the angular separation $\Delta\theta = |\theta_2 - \theta_1|$ where $P_{dB}(\theta) = -3\text{ dB}$.

## Quick Start

```bash
git clone https://github.com/4techno/antenna-pattern-analyzer.git
cd antenna-pattern-analyzer
pip install -r requirements.txt
```

### Run Analysis & Generate Polar Diagram

```bash
python pattern_analyzer.py --mode simulate --antenna yagi --beamwidth 45 --output radiation_pattern.png
```

## Output Example

```
[*] Running antenna radiation analysis for Yagi-Uda Array...
------------------------------------------------------------
Peak Gain Angle       : 0.0 deg
3dB Beamwidth (HPBW)  : 44.8 deg (-22.4 to +22.4 deg)
Front-to-Back Ratio   : 21.4 dB
First Side Lobe Level : -14.2 dB
------------------------------------------------------------
[✓] Generated polar pattern chart: radiation_pattern.png
```

## Hardware Compatibility

- Stepper Controller: Dual-axis NEMA 17 with A4988 / TMC2209 drivers via ESP32
- RF Sensors: Analog AD8318 / AD8317 logarithmic power detectors (1 MHz to 10 GHz)

## License

MIT License. Open for educational and RF research experimentation.
