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

<!--  load, R: resample libs
L: torchaudio_soundfile- \nR: torchaudio_transform_hann    26.424762
L: torchaudio_soundfile- \nR: torchaudio_hann              27.050398
L: torchaudio_sox_io- \nR: torchaudio_hann                 27.127326
L: torchaudio_soundfile- \nR: torchaudio_kaiser            27.153835
L: torchaudio_sox_io- \nR: torchaudio_kaiser               27.646094
L: scipy- \nR: soxr                                        28.060912
L: torchaudio_sox_io- \nR: soxr                            37.961860
L: torchaudio_soundfile- \nR: soxr                         37.999496
L: torchaudio_soundfile- \nR: julius                       39.168839
L: librosa- \nR: soxr                                      39.238550
L: soundfile- \nR: soxr                                    42.834313-->


| Load Library | Resampling Library | Time on CPU |
| - | - | - |
| `torchaudio-sox_io` | `torchaudio_hann` | 26.42 ms |
| `torchaudio-soundfile` | `torchaudio_hann` | 27.05 ms |
| `torchaudio-sox_io` | `torchaudio_kaiser` | 27.65 ms |
| `torchaudio-soundfile` | `torchaudio_kaiser` | 27.15 ms |
| `scipy` | `soxr` | 28.06 ms |
| `torchaudio-sox_io` | `soxr` | 37.96 ms |
| `torchaudio-soundfile` | `soxr` | 38.00 ms |
| `torchaudio-soundfile` | `julius` | 39.17 ms |
| `librosa` | `soxr` | 39.24 ms |
| `soundfile` | `soxr` | 42.83 ms |





### Best by quality (resampling only)

* according to the original notebook [Audio-resampling-in-python](https://github.com/bernardo-torres/audio-resampling-in-python)

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

