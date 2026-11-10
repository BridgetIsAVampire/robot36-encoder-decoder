# Robot36 encoder/decoder
This is a simple Robot36 encoder/decoder made in Python, the wav files it generates SHOULD work with QSSTV, if the header is invalid, rewrite the file with SoX.
## installation
python -m pip install -r requirements.txt (installs the dependencies)
## encode
JPG/PNG -> WAV:
<br>
python encoder.py input.jpg output.wav (where input/output are the filenames)
## decode
robot36 WAV -> png/jpg:
<br>
python decoder.py input.wav output.png (where input/output are the filenames)
## header issues with QSSTV
if this occurs:
<br>
sox input.wav output.wav (where input/output are the filenames)
and then open the output file
## files
encoder.py: encodes png/jpg to robot36 audio
<br>
decoder.py: decodes robot36 WAV to png/jpg
<br>
robot36.py: implementation of the en/decoding
<br>
requirements.txt: python dependencies
<br>
readme.md: this file
## robot36 spec
resolution: 320x240
<br>
VIS code: 8
<br>
duration: around 36 secs
<br>
frequencies: 1500-2300 hz
## header
300ms 1900hz leader
<br>
10ms 1200hz break
<br>
300ms 1900hz leader
<br>
30ms start bits
## VIS code
FSK with 30ms per bit
<br>
data bits: 7 bits with least significant first where 1,100 Hz = 1 and 1,300 Hz = 0
<br>
parity bit
<br>
stop bit: 30ms 1200hz
<br>
VIS code 8
## image lines
sync: 9ms
<br>
porch: 3ms
<br>
luminance: 88ms
<br>
separator: 4.5ms
<br>
porch: 1.5ms
<br>
chroma: 44ms
## chroma
even: R-Y
<br>
odd: B-Y
## example of use
python encoder.py woof.jpg meow.wav
<br>
^encodes
<br>
python decoder.py meow.wav wruff.png
<br>
^decodes
