# Oneshot Audio Recorder
oneshot_sampler.py

This is a simple Python script to record audio samples from your microphone directly from the command line. It records one or several samples in one go. The recordings are saved as `.wav` files.


## Requirements

- Python
- `sounddevice`
- `soundfile`

To install the required packages, run:

`
pip install sounddevice soundfile
`

### Features

- Use command line arguments for customization.
- Record audio with a specified duration.
- Choose a specific device for recording.
- Save multiple recordings with incremental filenames.
   
### Usage

1. Record a 1-second audio and save it as sample.wav in the current directory:
`
python oneshot_sampler.py
`

2. Record three 10-second audios and save them in a folder named "recordings":
`
python oneshot_sampler.py -f recording -d 10 -dir recordings -n 3
`

### Command Line Arguments

- `-f` or `--filename`: Base name for the file (default is 'sample').
- `-d` or `--duration`: Duration of recording in seconds (default is 1 second).
- `-dir` or `--directory`: Directory to save the recordings (default is the current directory).
- `-n` or `--num_recordings`: Number of recordings to make (default is 1).
- `-dev` or `--device`: Choose a specific device for recording. Use --list_devices to view available devices.
- `--list_devices`: List available recording devices and exit.

<br>
<br>

# Audio Dataset Recording & Augmentation Tool
audio_dataset_sampler.py


This Python-based utility enables efficient audio recording with options for categorization, augmentation, and metadata generation. It's tailored for collecting data for various audio-related machine learning tasks.

### Requirements

- Python
- `sounddevice`
- `librosa`
- `pydub`
- `soundfile`
- `pandas`

To install the required packages, run:

`
pip install sounddevice librosa pydub soundfile pandas
`

### Features

- **Multiple Recording Modes**: Supports recording audio samples in either a common folder for all samples (Variant A) or in separate folders based on class name (Variant B).
- **Audio Augmentation**: Inbuilt audio augmentation features like pitch shifting, time stretching, noise addition, and decibel adjustment.
- **Metadata Generation**: Automates the generation of metadata CSV files post-recording, with paths and labels for each audio sample.
- **Device selection**: Lists availiable input devices, selection of used device.

### Usage

1. Record using variant A (all samples in a single folder):
`
python audio_dataset_sampler.py --variant A
`

2. Record using variant B (samples segregated into class-specific folders) 20 samples of each class, and classes are: "one", "two", "three":
`
python audio_dataset_sampler.py --variant B --sample_count 20 --classes one two three
`

3. Record variant B and augment the samples, from each original sample produce 10 augmented, record classes "on", "off", "scene", record 2 original samples for each class, samples has duration of 1 second, microphone device index 1:
`
python audio_dataset_sampler.py --variant B --augment --num_augmented 10 --classes on off scene --sample_count 2 --duration 1 --device_index 1
`


### Command Line Arguments

- `--variant`: Recording variant. `A` saves all samples in one folder while `B` saves samples to separate folders for each class.
- `--augment`: include to indicate if augmentation is required otherwise samples are not augmented.
- `--num_augmented`: Number of augmented samples from every original sample.
- `--classes`: Specify classes for the recordings. (eg.: one two three)
- `--sample_count`: Number of samples in every class.
- `--duration`: Duration of one sample in seconds.
- `--device_index`: Specify microphone device index.
- `--check_devices`: check available input devices and exit.
- `--metadata`: include in command to produce metadata after recording.