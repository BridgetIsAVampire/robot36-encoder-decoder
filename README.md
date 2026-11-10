# Robot36 encoder/decoder
This is a simple Robot36 encoder/decoder made in Python, the wav files it generates SHOULD work with QSSTV, if the header is invalid, rewrite the file with SoX.
## installation
python -m pip install -r requirements.txt (installs the dependencies)
## encode
JPG/PNG -> WAV:
python encoder.py input.jpg output.wav (where input/output are the filenames)
## decode
robot36 WAV -> png/jpg:
python decoder.py input.wav output.png (where input/output are the filenames)
## header issues with QSSTV
if this occurs:
sox input.wav output.wav (where input/output are the filenames)
and then open the output file
## files
encoder.py: encodes png/jpg to robot36 audio
decoder.py: decodes robot36 WAV to png/jpg
robot36.py: implementation of the en/decoding
requirements.txt: python dependencies
readme.md: this file
## robot36 spec
resolution: 320x240
VIS code: 8
duration: around 36 secs
frequencies: 1500-2300 hz
## header
300ms 1900hz leader
10ms 1200hz break
300ms 1900hz leader
30ms start bits
## VIS code
FSK with 30ms per bit
data bits: 7 bits with least significant first where 1,100 Hz = 1 and 1,300 Hz = 0
parity bit
stop bit: 30ms 1200hz
VIS code 8
## image lines
sync: 9ms
porch: 3ms
luminance: 88ms
separator: 4.5ms
porch: 1.5ms
chroma: 44ms
## chroma
even: R-Y
odd: B-Y
## example of use
python encoder.py woof.jpg meow.wav
<br>
^encodes
<br>
python decoder.py meow.wav wruff.png
<br>
^decodes
