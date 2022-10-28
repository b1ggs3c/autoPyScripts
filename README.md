#This program converts a pdf to a audio book.

First, you will need to install the packages: pyttsx3, PyPDF2

pip install pyttsx3 PyPDF2

Once you have those packages installed, use example below.

Next, import the libraries that will be used throughout the program.

import pyttsx3
import PyPDF2

Next get the file location and name.

file = 'C:/Users/<user_name>/Desktop/"story.pdf"'

import pyttsx3,PyPDF2
pdfreader = PyPDF2.PdfFileReader(open('story.pdf','rb'))
speaker = pyttsx3.init()
for page_num in range(pdfreader.numPages):   
    text = pdfreader.getPage(page_num).extractText()  ## extracting text from the PDF
    cleaned_text = text.strip().replace('\n',' ')  ## Removes unnecessary spaces and break lines
    print(cleaned_text)                ## Print the text from PDF
    #speaker.say(cleaned_text)        ## Let The Speaker Speak The Text
    speaker.save_to_file(cleaned_text,'story.mp3')  ## Saving Text In a audio file 'story.mp3'
    speaker.runAndWait()
speaker.stop()