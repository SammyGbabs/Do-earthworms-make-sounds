# Do Earthworms Make Sounds? Decoding the Vibrations of Soil Life with Python

Companion repo for my PyCon Tanzania 2026 talk.

Soil organisms such as earthworms and ants produce tiny vibrations as they move and feed. This repo shows how those vibrations, recorded with a piezoelectric sensor, can be turned into a labelled dataset and a working prediction service, all in Python.

## What's inside

| Folder | Contents |
|---|---|
| `notebooks/soil_sounds_demo.ipynb` | The notebook run during the talk: features, two independent labellers, agreement check and consensus labelling |
| `sample_clips/` | A few soil recordings for the live demo |
| `data/` | `features_extended.csv`: ecoacoustic features for the full dataset (588 clips) |
| `deployment/` | FastAPI app and Dockerfile for the model API on Hugging Face Spaces |

## Run the notebook

```bash
pip install -r requirements.txt
jupyter notebook notebooks/soil_sounds_demo.ipynb
```

## The labelling recipe

1. Compute domain features (bioacoustic index, event density) with `librosa`
2. Label the clips two independent ways: a percentile threshold (`pandas`) and KMeans clustering (`scikit-learn`)
3. Measure how much the two agree
4. Train a Random Forest on the clips where they agree, and let it settle the disputed ones

## Live API

Model served at https://sammyg123-faunapulse.hf.space (`POST /predict` with an audio file).

## Related work

- Paper: Babalola, Ogore & Nsabiyumva, *An AI-Powered IoT System for Real-Time, Non-Invasive Monitoring of Soil Biodiversity Using Bioacoustics*, ICICT 2026 (Springer LNNS)
- Full project code: https://github.com/SammyGbabs/FaunaPulse-Capstone-Project

## Contact

Samuel Babalola · Ruzivo Research Lab, African Leadership University
