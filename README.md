# laughter-detection


This library contains code and models to segment  regions of laughter from an audio file. The models/ folder contains models trained on the [Switchboard](https://catalog.ldc.upenn.edu/ldc97s62) data set.

The implementation is based on the following papers:
- Knox, Mary Tai, and Nikki Mirghafori. "Automatic laughter detection using neural networks." Interspeech. 2007.
- Kaushik, Lakshmish, Abhijeet Sangwan, and John HL Hansen. "Laughter and filler detection in naturalistic audio." Interspeech. 2015.

# Usage
- To train a new model on Switchboard, see `compute_features.py` and `train_model.py`
- To run the laugh detector from the command line, use `python segment_laughter.py <input_audio_path> <stored_model_path> <output_folder> <threshold>(optional) <min_length>(optional)`
- e.g. `python segment_laughter.py my_audio_file.wav models/new_model.h5 my_folder 0.8 0.1`

  #### Parameters
  - The threshold parameter adjusts the minimum probability threshold for classifying a frame as laughter. The default is 0.5, but you can  experiment with settings between 0 and 1 to see what works best for your data. Lower threshold values may give more false positives but may also recover a higher percentage of laughs from your file.

  - The min_length parameter sets the minimum length in seconds that a laugh needs to be in order to be identified. The default value is 0.2.


  #### Output
  - The segmenter prints out a list of time segments in seconds of the form (start, end) and saves them as a list of wav files into a folder at `<output_folder>`
  
# Dependencies
- Numpy/SciPy
- Tensorflow/Keras
- [Librosa](http://librosa.github.io/librosa/)
- [Python Speech Features](https://github.com/jameslyons/python_speech_features)
