# TrainHornDetector
Detect train horns and track them.


## Notes:
Two approaches I can think of:

### "Classic" DSP
The idea is that train horns are always around the same volume frequency range, so we can just find them using a mix of FFT and amplitude.  Since the trains we're listening for are all the same (Austin metro red line), I expect this to work pretty well.  

### NN Audio Classifier
Use transfer learning to teach a neuralnet (i.e. YamNET) what a train sounds like, then try to run it on a lowish-power machine (i.e. TF Lite).  

## Storing Historical Data
Host a DB on a rpi or something. There are tons of examples here, and I've used this in the past for other projects.

### Time Information
Need a RTC module or something to give accurate time stamps.
