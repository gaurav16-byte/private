**Challenge Name: StegBreathe**

**Date of Submisison: 18 April 2022**

**Challenge Author: GauravV9p3r**

**Description: I've received a zip file. But all is see is a skyscraper image and a file containing gibberish**

**Objective: To use stego techniques and extract the flag using the hints provided**

**Difficuly: Medium**

# WRITEUP

On extracting the zip file we get 2 files, important.txt and scyscraper.jpg
![image](https://user-images.githubusercontent.com/61114467/163855014-977a99aa-4297-402b-a34e-93347682bb36.png)

Upon reading the important.txt, its all filled up with gibberish numbers
![image](https://user-images.githubusercontent.com/61114467/163855243-389b04ac-a9d8-4023-9514-893a8fa8844d.png)

Upon opening skyscraper.jpg, its just a picture. So I'll first check some details using exiftool. We find a comment, this looks like a BASE32 string. Upon decoding this further decodes into a BASE64 string. This further decodes to ***delete armstrong numbers***
![image](https://user-images.githubusercontent.com/61114467/163857102-04c1fcbf-eb72-4068-9959-9dcc52b03062.png)
![image](https://user-images.githubusercontent.com/61114467/163857156-6d9b5000-0717-437e-a861-4ae4133cef29.png)

Looking at the important.txt again, there are a few numbers which are surrounded by $ signs. Searching the web for armstrong numbers, I find a few numbers that match the list. After removing them, there's just one big number 8704 that doesn't match the list. One more thing all the numbers range from 1-25, maybe they are numbers to alphabets. I wrote a script and this string is formed. 
"mitch remember how i told you three is a magic number remember that you need three numbers multiply them together and you will have the password it is funny how a few things are always in front of us yet we are unable to find them this is one thing i am talking about agent _8704_"
8704 is one number. According to the riddle we need three numbers. The other 2 numbers are not specifically anywhere hidden in the text file. Let's look at the exiftool output again. Let's try multiplying the number 8704 by the width and height of the image. I'll use steghide. The password works as you can see below and we are provided with a sound.wav file.
![image](https://user-images.githubusercontent.com/61114467/163866196-441804d9-d337-4911-afa4-25922e594532.png)

Upon listening to the audio, it contains morse code. Decoding it, we get a BASE32 string which further decodes to BASE64 and to ROT-13. This is a reversed string. Upon reversing the text, we get the flag to the challenge. 
