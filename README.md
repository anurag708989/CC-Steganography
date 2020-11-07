# CC-Steganography
steganography challenge tools used exiftool,steghide,sonicstudio
#Stegnography



nmap :
only port 80 is open running http on it

there is image on home page 

lets check if there is some information or not
found something using exiftool
ExifTool Version Number         : 12.00
File Name                       : task7_image_1.jpeg
Directory                       : .
File Size                       : 8.6 kB
File Modification Date/Time     : 2020:11:07 01:40:44-05:00
File Access Date/Time           : 2020:11:07 01:41:07-05:00
File Inode Change Date/Time     : 2020:11:07 01:41:07-05:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Exif Byte Order                 : Big-endian (Motorola, MM)
Document Name                   : password=admin
X Resolution                    : 1
Y Resolution                    : 1
Resolution Unit                 : None
Y Cb Cr Positioning             : Centered
Image Width                     : 213
Image Height                    : 160
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 213x160
Megapixels                      : 0.034




root@kali:~/ctf/tryhackme/CC: stegnography# steghide --extract -sf task7_image_1.jpeg 
Enter passphrase: 
wrote extracted data to "a.txt".
root@kali:~/ctf/tryhackme/CC: stegnography# cat a.tx
cat: a.tx: No such file or directory
root@kali:~/ctf/tryhackme/CC: stegnography# cat a.txt 
the key is: superkeykey



but this is the password for steghide not the key ,so the key i found using
steghide is superkeykey



then found a link in the wav2 file 
link:https://imgur.com/KTrtNI5



found!! a pencil image at this link
steghide and exiftool doesn't work
lets use zsteg it gives:
imagedata           .. text: ")))xxxLMO"
b1,bgr,lsb,xy       .. text: "\rKey: fatality"
b2,rgb,lsb,xy       .. file: SoftQuad DESC or font file binary
b2,rgb,msb,xy       .. file: VISX image file
b2,bgr,lsb,xy       .. file: SoftQuad DESC or font file binary
b2,bgr,msb,xy       .. file: VISX image file


so the key fatality works



now here in next challenge i found a qr code lets use online decoder
https://zxing.org/w/decode.jspx

i used stegsolve.jar to remove or changed the light pink layer
and taken a screenshot then found a flag : killshot

