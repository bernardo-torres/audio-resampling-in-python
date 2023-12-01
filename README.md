Comparison of audio resampling libraries and some audio loaders.

View the two notebooks:

- [Audio Resampling in Python.ipynb](https://github.com/bernardo-torres/audio-resampling-in-python/blob/master/Audio%20Resampling%20in%20Python.ipynb)
- [Audio Loading + Resampling.ipynb](https://github.com/bernardo-torres/audio-resampling-in-python/blob/master/Audio%20Loading%20%2B%20Resampling.ipynb)


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

<!-- L: load, R: resample libs
L: torchaudio- \nR: torchaudio_hann              28.058083
L: torchaudio- \nR: torchaudio_kaiser            29.464524
L: torchaudio- \nR: torchaudio_transform_hann    31.858430
L: scipy- \nR: soxr                              33.637649
L: torchaudio- \nR: soxr                         38.724915
L: torchaudio- \nR: julius                       39.991616
L: soundfile- \nR: soxr                          42.511529
L: librosa- \nR: soxr                            47.683907 -->

| Library | Time on CPU |
| - | - |
| `torchaudio_hann` | 28.06 ms |
| `torchaudio_kaiser` | 29.46 ms |
| `torchaudio_transform_hann` | 31.86 ms |
| `scipy`/`soxr` | 33.64 ms |
| `torchaudio_transform_kaiser` | 34.06 ms |
| `torchaudio`/`soxr` | 38.72 ms |
| `torchaudio`/`julius` | 39.99 ms |
| `soundfile`/`soxr` | 42.51 ms |
| `librosa`/`soxr` | 47.68 ms |


### Best by quality (resampling only)

* according to the original notebook [Audio-resampling-in-python]
(https://github.com/bernardo-torres/audio-resampling-in-python)

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

Please check plots in the [Audio Resampling in Python.ipynb](https://github.com/bernardo-torres/audio-resampling-in-python/blob/master/Audio%20Resampling%20in%20Python.ipynb) notebook. This version is an updated version of the original notebook but does not have all the libraries tested in the original notebook.

