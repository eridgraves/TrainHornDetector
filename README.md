# TrainHornDetector
Detect train horns and track them.


## Notes:
Two approaches I can think of:

### "Classic" DSP
The idea is that train horns are always around the same volume frequency range, so we can just find them using a mix of FFT and amplitude.  Since the trains we're listening for are all the same (Austin metro red line), I expect this to work pretty well.  
https://dsp.stackexchange.com/questions/1317/is-there-an-algorithm-for-finding-a-frequency-without-dft-or-fft
https://www.mstarlabs.com/dsp/goertzel/goertzel.html#:~:text=There%20are%20various%20ways%20to,the%20desired%20frequency%20is%20present.

### NN Audio Classifier
Use transfer learning to teach a neuralnet (i.e. YamNET) what a train sounds like, then try to run it on a lowish-power machine (i.e. TF Lite).  
https://www.tensorflow.org/lite/examples/audio_classification/overview
https://www.tensorflow.org/tutorials/audio/transfer_learning_audio
https://github.com/tensorflow/docs/blob/master/site/en/hub/tutorials/yamnet.ipynb
https://medium.com/@antonyharfield/converting-the-yamnet-audio-detection-model-for-tensorflow-lite-inference-43d049bd357c
Need to get samples of train horns. Would do this automatically using the train schedule, but trains are too often delayed.  I don't want to just run a long recording and stitch by hand (although this would be possible using the amplitude of the sound).  Perhaps segmentation could be automated from a large recording. 

## Storing Historical Data
Host a DB on a rpi or something. There are tons of examples here, and I've used this in the past for other projects.

### Time Information
Need a RTC module or something to give accurate time stamps.

