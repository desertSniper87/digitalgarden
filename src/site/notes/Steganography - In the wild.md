---
{"dg-publish":true,"permalink":"/steganography-in-the-wild/"}
---

- [Using Facebook for Image Steganography](https://arxiv.org/abs/1506.02071?utm_source=chatgpt.com)
- [BLOG: Steganography in Cybersecurity: A Growing Attack Vector](https://security.pditechnologies.com/blog/steganography-in-cybersecurity-a-growing-attack-vector/?utm_source=chatgpt.com)
- [Stegomalware](https://en.wikipedia.org/wiki/Stegomalware?utm_source=chatgpt.com)
- [Real-World Steganography - Schneier on Security](https://www.schneier.com/blog/archives/2023/01/real-world-steganography.html?utm_source=chatgpt.com)
- [FBI: Spies Hid Secret Messages on Public Websites](https://www.wired.com/2010/06/alleged-spies-hid-secret-messages-on-public-websites/?utm_source=chatgpt.com)
_Steganography is the practice of concealing information within other non-suspicious data_, often used for security purposes to hide messages from prying eyes. It’s been around for centuries and has evolved with technology. In today’s world, steganography is widely used, and its methods range from hiding text within images to hiding files within other files. This report explores some common forms of steganography in the wild.

## 1. Image Steganography

One of the most popular forms of steganography involves hiding data within images. This is often done by manipulating the pixel values in an image file. Here are the key methods:

- Least Significant Bit (LSB) Technique: This method alters the least significant bits of the image pixels to encode information. **These changes are typically imperceptible to the human eye**

  Example: A digital image (like a JPEG or PNG file) is modified at the binary level. The least significant bit of each pixel is replaced by bits of the hidden message. To an untrained eye, the image looks unchanged.

- Palette-based Steganography: In this method, the colors in the image palette are manipulated to hide the message. This technique is commonly used in 8-bit images (which have a limited color palette).

## 2. Audio Steganography

This involves hiding information within sound files, such as MP3 or WAV files. Audio steganography exploits human limitations in perceiving sound, so data can be hidden without altering the sound quality significantly.

- LSB in Audio: Similar to image LSB, the least significant bit of an audio file’s samples is altered to encode information.

  Example: An MP3 file might look normal to the ear, but hidden data is concealed within the audio waveform by adjusting bits that are inaudible.

- Echo Hiding: This technique involves adding a delayed version of an audio signal (an echo) to carry the hidden data.

## 3. Text Steganography

Text steganography hides information within readable text. This can range from subtle text formatting changes to more complex encoding techniques.

- Whitespace Steganography: Information is encoded in the form of spaces, tabs, and newlines between words. While the text appears normal, the hidden data can be extracted by counting or interpreting the whitespace patterns.

  Example: A message can be hidden in the spaces between words, and a program can detect and extract the information by interpreting the number or type of spaces.

- Word Substitution: Another method is to substitute words in a sentence with synonyms or homophones, which don’t change the overall meaning of the text but can represent hidden data when decoded.

## 4. Video Steganography

Video files can hide much more data compared to images and audio due to their higher capacity and complexity.

- Video Frame Manipulation: In this method, information is hidden in the least significant bits of video frames. Since video is a series of images (frames), this technique can exploit small changes across many frames without noticeable visual differences.

  Example: A video file might appear normal to a viewer, but hidden data could be embedded in every frame using LSB or other pixel manipulation techniques.

- Motion Vector Steganography: This method involves hiding data in the motion vectors used for video compression. These vectors define how blocks in the video move from one frame to the next and can be adjusted to carry hidden data.

## 5. Network Steganography

Network steganography involves hiding data within network protocols and communications. It’s used in contexts where it’s important to keep the existence of communication hidden.

- TCP/IP Protocol Manipulation: By manipulating the headers or other aspects of TCP/IP packets, hidden data can be embedded in network traffic.

  Example: Data can be hidden in the unused fields of a packet’s header, such as in the sequence or acknowledgment numbers.

- Covert Channels: Covert channels can be used to send hidden messages by encoding information in otherwise legitimate communications, such as file transfers or web browsing.

## 6. File-based Steganography

This involves hiding data within other files, such as embedding one file inside another. The hidden file remains undetected unless the correct extraction method is used.

- File System-based Steganography: In this method, hidden data is stored in unused parts of the file system, such as in the slack space of a hard drive (unused portions of a file’s allocated disk space).

  Example: A file may look normal, but by inspecting the file system, a hidden file could be found in the unallocated space.

- Steganographic Containers: Specialized files or containers (like ZIP or TAR files) can be created that appear to hold harmless data but actually conceal one or more hidden files.

## 7. DNA-based Steganography

This is a more futuristic and experimental form of steganography where information is encoded within the sequences of DNA. Although still in early stages, this could provide a method for storing vast amounts of information in a microscopic and highly secure way.

- Encoding Information in DNA Sequences: The four nucleotides (A, T, C, and G) in DNA can be used to encode binary information. This method has the potential to store huge amounts of data in a tiny space, making it highly efficient.
