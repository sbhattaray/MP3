# MP3
# Mp3 to Wav
import os
import sys
import glob
from pydub import AudioSegment

def convert_to_wav(input_folder, output_folder):
    if not os.path.exists(output_folder):
        os.makedirs(output_folder)

    mp3_files = glob.glob(os.path.join(input_folder, "*.mp3"))

    for mp3_file in mp3_files:
        wav_file = os.path.splitext(os.path.basename(mp3_file))[0] + ".wav"
        wav_path = os.path.join(output_folder, wav_file)
        sound = AudioSegment.from_mp3(mp3_file)
        sound.export(wav_path, format="wav")
        print(f"Converted {mp3_file} to {wav_path}")

if __name__ == '__main__':
    if len(sys.argv) != 3:
        print("Usage: python mp3_to_wav.py input_folder output_folder")
        sys.exit(1)

    input_folder = sys.argv[1]
    output_folder = sys.argv[2]
    convert_to_wav(input_folder, output_folder)
    
    
"""To run this script, you need to have the pydub library installed. You can install it using pip:"""

pip install pydub

""" To convert a set of MP3 files to WAV format, you need to specify the input folder containing the MP3 files and the output folder where the WAV files will be saved as arguments. For """

python mp3_to_wav.py input_folder output_folder
