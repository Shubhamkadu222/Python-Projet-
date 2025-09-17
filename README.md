# Python-Projet-
Speech-to-Text Transcription  Create a simple tool that converts audio recordings into text. Use basic libraries for speech recognition (e.g., SpeechRecognition in Python).

import speech_recognition as sr

def transcribe_audio(file_path):
    # Initialize recognizer
    recognizer = sr.Recognizer()
    
    try:
        # Load the audio file
        with sr.AudioFile(file_path) as source:
            print("Listening to audio...")
            audio_data = recognizer.record(source)  # Read the entire audio file
            
        # Convert speech to text using Google Web Speech API
        text = recognizer.recognize_google(audio_data)
        print("Transcription:\n", text)
        return text
    
    except sr.UnknownValueError:
        print("Sorry, the audio could not be understood.")
    except sr.RequestError:
        print("Could not request results from the speech recognition service.")
    except Exception as e:
        print("Error:", str(e))


# Example usage:
# Replace 'sample_audio.wav' with the path to your audio file
if __name__ == "__main__":
    transcribe_audio("sample_audio.wav")
