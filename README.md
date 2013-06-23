Maxim_Java_API
==============

Maxim library update
I made a few changes to the provided android_api.pde to faciliate playing several audio files sequentially. I discovered a problem when using loadFile() multiple times. The volume would decrease dramatically on each additional AudioPlayer. So I added the ability to change the data used by an external player. This would allow me to only create one player and feed the player various sound data before playing.

Modifications include:

Changing the Maxim constructor to add a sampling rate as a parameter. The pApplet parameter was not needed. I also added a default constructor which sets sample rate at 44100 Hz.

Added new methods for the Maxim class.

The method createEmptyPlayer() creates a blank AudioPlayer without any wav file.

The method reLoadPlayer() fills the player with sound data. This method works hand and hand with justLoadAudioFile().

I modified the method loadFile() to use the new functions created.

Added new methods for the AudioPlayer class.
The first method justLoadAudioFile() just loads a file into a short array. I used the previously defined AudioPlayer constructor as a template for this function. This method also insures that the sample rate of the wav file matches the current sampleRate value. If there is a mismatch, the function throws an "InputMismatchException" exception. I don't catch the exception because I feel at this point, the user will not wish to proceed.

I separated the AudioPlayer reset code to a new method resetAudioPlayer().
