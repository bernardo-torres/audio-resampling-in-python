Comparison of audio resampling libraries and some audio loaders.

View the two notebooks:

- [Audio Resampling in Python.ipynb](Audio Resampling in Python.ipynb)
- [Audio Loading + Resampling.ipynb](Audio Loading + Resampling.ipynb)

### Best by quality

1. Good:
   - `scikit.samplerate`/`scikits-samplerate`/`samplerate`/`libsamplerate`
   - `librosa`/`resampy` (`"kaiser_best"`)
   - `julius`
3. Acceptable:
   - `nnresample`
   - `lilfilter`
   - `torchaudio` (`transforms.Resample` + `resample_waveform`)
   - `librosa`/`resampy` (`"kaiser_fast"`)
5. Bad:
   - `scipy.signal.resample`


According to [Audio-resampling-in-python](https://github.com/bernardo-torres/audio-resampling-in-python). Please check plots in the [Audio Resampling in Python.ipynb](Audio Resampling in Python.ipynb) notebook.


### Best by speed (resampling only)


Downsampling from 48 kHz to 44.1 kHz.


| Library | Time on CPU |
| - | - |
| `torchaudio_hann` | 0.87 ms |
| `torchaudio_transform_hann` | 1.11 ms |
| `torchaudio_transform_kaiser` | 1.38 ms |
| `soxr` | 1.43 ms |
| `torchaudio_kaiser` | 1.69 ms |
| `scipy` | 2.40 ms |
| `julius` | 9.21 ms |
| `resampy_fast` | 13.63 ms |
| `nnresample` | 18.33 ms |
| `resampy_best` | 38.04 ms |



### Best by speed (loading + resampling)
