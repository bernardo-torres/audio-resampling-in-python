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

<!--  L: load, R: resample libs
L: torchaudio_sox_io- \nR: torchaudio_hann                 27.543033
L: torchaudio_soundfile- \nR: torchaudio_kaiser            27.635533
L: torchaudio_soundfile- \nR: torchaudio_hann              27.661973
L: torchaudio_soundfile- \nR: torchaudio_transform_hann    27.752087
L: scipy- \nR: soxr                                        28.039192
L: torchaudio_soundfile- \nR: julius                       38.328746
L: torchaudio_soundfile- \nR: soxr                         38.694766
L: librosa- \nR: soxr                                      39.542175
L: soundfile- \nR: soxr                                    41.360285 -->


| Load Library | Resampling Library | Time on CPU |
| - | - | - |
| `torchaudio-sox_io` | `torchaudio_hann` | 27.54 ms |
| `torchaudio-soundfile` | `torchaudio_kaiser` | 27.64 ms |
| `torchaudio-soundfile` | `torchaudio_hann` | 27.66 ms |
| `torchaudio-soundfile` | `torchaudio_transform_hann` | 27.75 ms |
| `scipy` | `soxr` | 28.04 ms |
| `torchaudio-soundfile` | `julius` | 38.33 ms |
| `torchaudio-soundfile` | `soxr` | 38.69 ms |
| `librosa` | `soxr` | 39.54 ms |
| `soundfile` | `soxr` | 41.36 ms |




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

