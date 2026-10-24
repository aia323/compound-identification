# Compound Identification from Mass Spectrometry Data

Graduate research project at Lehigh University (2026).

Identifying unknown chemicals in a sample is a key step in drug discovery,
environmental testing and metabolomics. This project builds a Python pipeline
that identifies compounds from LC-MS/MS data by matching their fragmentation
spectra against a large reference library. It also checks how often the answers
are actually right.

## What I built
1. **A clean reference library**: combined public spectral databases (MassBank, GNPS)
   into one library of **733,000+ spectra covering 65,000+ compounds**, with
   duplicate removal and data-leakage checks.
2. **A matching model**: ranks candidate compounds using spectral entropy similarity.
3. **An independent answer key**: built from known standards before looking at any
   results, so every method is graded the same fair way.
4. **Confidence calibration**: turns match scores into a real "probability this is
   correct", fit on library data and tested on separate data.
5. **Head-to-head comparison** against the built-in matching in two widely used
   tools (MS-DIAL and MZmine), using the same library and a McNemar test.
6. **Machine learning re-ranker** (in progress): LightGBM model that combines
   several match features to pick the right compound.

## Results (43 known standards)
| Method | Correct |
|---|---|
| **My model** | **32 / 43** |
| MS-DIAL built-in matching | 32 / 43 |
| MZmine built-in matching | 29 / 43 |

- My model matched MS-DIAL and got 3 more standards right than MZmine.
- Calibrated confidence held up on new data: of the matches the model was
  ≥ 90% confident in, **53 of 54 were correct**.

## Tech
Python · pandas · NumPy · scikit-learn · LightGBM · statsmodels · ms_entropy ·
Google Colab · MS-DIAL · MZmine

## Code
The code is private until this work is published. It's available on request:
aia323@lehigh.edu
