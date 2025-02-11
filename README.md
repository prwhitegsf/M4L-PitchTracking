### M4L-PitchTracking to Midi

Monophonic pitch and envelope tracking in a MaxForLive device along with another device that receives the pitch and envelope info and translates to midi notes for use with any midi instrument.

Requires the sigmund~ external, which can be found [here](https://github.com/v7b1/sigmund_64bit-version/releases)
Code can also be copied into a standard max-patch, just replace any instance of live.thisdevice with a loadmess.

#### Device 1: PitchTrackingBroadcaster
Place on desired audio channel
- For best results, apply compression, gating and any desired eq beforehand
- The "Send On" input is an integer that determines which PitchTrackingToMidi devices will receive the pitch tracking data
- Observe incoming pitch and amplitude on the left side of the device
- Adjust thresholds on the right

#### Device 2: PitchTrackingToMidi
- Set "Receive On" to match the "Send On" value from the PitchTrackingBroadcaster you want to receive from.
- There are two modes for handling note offs
  - each-note: generates a note of when a new note comes in.
  - fixed-duration: uses a makenote object to set the duration of each note
- Adjust the note-chgange threshhold and durationn as desired
