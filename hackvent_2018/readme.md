# hackvent 2018

## day 01
**Description:**
After a decade of monochromity, Santa has finally updated his infrastructure with color displays. With the new color code, the gift logistic robots can now handle many more gifts:

**Solution:**
Searching for "just another bar code" lead us to JAB code:
https://github.com/jabcode/jabcode

Using a JAB code decoder (https://jabcode.org/scan) we get the flag:
```HV18-L3ts-5t4r-7Th3-Phun-G33k```

## day 02
Solution:
Our input string from the challenge is in octal encoding format:
```115 112 122 127 113 132 124 110 107 106 124 124 105 111 104 105 115 126 124 103 101 131 124 104 116 111 121 107 103 131 124 104 115 122 123 127 115 132 132 122 115 64 132 103 101 132 132 122 115 64 132 103 101 131 114 113 116 121 121 107 103 131 124 104 115 122 123 127 115 63 112 101 115 106 125 127 131 111 104 103 115 116 123 127 115 132 132 122 115 64 132 103 101 132 132 122 115 64 132 103 101 131 114 103 115 116 123 107 113 111 104 102 115 122 126 107 127 111 104 103 115 116 126 103 101 132 114 107 115 64 131 127 125 63 112 101 115 64 131 127 117 115 122 101 115 106 122 107 107 132 104 106 105 102 123 127 115 132 132 122 116 112 127 123 101 131 114 104 115 122 124 124 105 62 102 101 115 106 122 107 107 132 104 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131 63 105 115 126 124 107 117 115 122 101 115 106 122 107 113 132 124 110 107 106 124 124 105 111 104 102 115 122 123 127 115 132 132 122 115 64 132 103 101 131 114 103 115 116 123 107 117 115 124 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131 63 105 115 126 124 107 117 115 122 101 115 106 122 107 107 132 104 106 105 102 121 127 105 132 114 107 115 64 131 127 117 115 122 101 115 112 122 127 111 132 114 107 105 101 75 75 75 75 75```

decoding it we get a base32 encoded string:
```MJRWKZTHGFTTEIDEMVTCAYTDNIQGCYTDMRSWMZZRM4ZCAZZRM4ZCAYLKNQQGCYTDMRSWM3JAMFUWYIDCMNSWMZZRM4ZCAZZRM4ZCAYLCMNSGKIDBMRVGWIDCMNVCAZLGM4YWU3JAM4YWOMRAMFRGGZDFEBSWMZZRNJWSAYLDMRTTE2BAMFRGGZDJNQQGOMLHGIQGCY3EMVTGOMRAMFRGKZTHGFTTEIDBMRSWMZZRM4ZCAYLCMNSGOMTJNQQGOMLHGIQGCY3EMVTGOMRAMFRGGZDFEBQWEZLGM4YWOMRAMJRWIZLGEA=====```

decoding this one again we get a “14 segment” encoded string:
```bcefg1g2 def bcj abcdefg1g2 g1g2 ajl abcdefm ail bcefg1g2 g1g2 abcde adjk bcj efg1jm g1g2 abcde efg1jm acdg2h abcdil g1g2 acdefg2 abefg1g2 adefg1g2 abcdg2il g1g2 acdefg2 abcde abefg1g2 bcdef```

Using the decoder from http://kryptografie.de/kryptografie/chiffre/14-segment.htm we get the flag:
```HL18-7QTH-JZ1K-JKSD-GPEB-GJPU```

## day 03
Solution:
Analysing the page source we found a hex encoded string. The first part was a trick but decoding the second part
```\x43\x6F\x6E\x67\x72\x61\x74\x75\x6C\x61\x74\x69\x6F\x6E\x73\x21\x0A\x0A\x59\x6F\x75\x20\x67\x6F\x74\x20\x74\x68\x65\x20\x66\x6C\x61\x67\x3A\x20\x48\x56\x31\x38\x2D\x70\x46\x41\x54\x2D\x4F\x31\x44\x6C\x2D\x48\x6A\x56\x70\x2D\x6A\x4A\x4E\x45\x2D\x5A\x6A\x75\x38```
we get our flag:
```HV18-pFAT-O1Dl-HjVp-jJNE-Zju8```

## day 04
Solution:
Using the tool dial-a-pirate from the old game monkey island you can get the requested years by combining the faces.

http://www.oldgames.sk/codewheel/secret-of-monkey-island-dial-a-pirate

Example:
Using the wheel to combine the first face,  you get year 1585 for Nebraska.

Flag:
```HV18-5o9x-4geL-7hkJ-wc4A-xp8F```

## day 05
Solution:
Using crt.sh and criteria “%hackvent.org” you get certificates for osintiscoolisntit.hackvent.org and www.hackvent.org

You can find the flag by browsing to osintiscoolisntit.hackvent.org:
```HV18-0Sin-tI5S-R34l-lyC0-oo0L```

## day 06
Solution:
Piet (named after painter Piet Mondrian) is one of the most known esoteric programming languages, which uses images as source code.

Using the piet code decoder (https://www.bertnase.de/npiet/npiet-execute.php) on all 6 pictures to get the flag:
```HV18-M4ke-S0m3-R3Al-N1c3-artZ```

## day 07
**Solution:**
The perl script is a flappy bird game.  You have to pass the gates using the space key to get all the flags.
Since it's going too fast your chances are not so high. You can modify the script and remove the strings "||| last|" so the game won’t stop if you hit a gate or a wall.
Now you have just to run the modified script and write down the letters to get the flag.

Flag:
```HV18-bMnF-racH-XdMC-xSJJ-I2fL```

## day 08
**Solution:**
I assumed the box represents a qrcode, just not in the right order.
"snail" got me to spiral encoding.
First you have to crop the box from the input image and scale it to 25x25 pixels. Set the contrast high to emphasize black and white color.

I have written a python script to read the modified image, sort the rows and columns using spiral inward from top-left counterclockwise and write it to a new png.
Some testing was necessary to get the starting position and direction.
```python
#!/usr/bin/python2
from PIL import Image
import sys

# input image 4dv3ntSn4il.png has to be cropped to 25x25 px
# use high contrast to emphasize black and white color
im = Image.open("dec08_cropped_input_25x25.png")
pix = im.load()

(w,h) = im.size

row_begin = 0
row_end = h-1
col_begin = 0
col_end = w-1
qrcode = ''

# decode using spiral inward from top-left, counterclockwise
# input  1 2 3   output => 1,4,7,8,9,6,3,2,5
#        4 5 6
#        7 8 9
while row_begin <= row_end and col_begin <=col_end:
    # start with first column
    for i in range(row_begin, row_end+1):
        (r,g,b) = pix[col_begin,i]
        # if black then "0"
        if r == 0:
           qrcode+="0"
        # else white
        else:
           qrcode+="1"
    col_begin+=1
    
    # continue with last row
    for i in range(col_begin, col_end+1):
        (r,g,b) = pix[i,row_end]
        if r == 0:
            qrcode+="0"
        else:
            qrcode+="1"
    row_end-=1
    

    if col_begin <= col_end:
        for i in range(row_end, row_begin-1, -1):
            (r,g,b) = pix[col_end,i]
            if r == 0:
                qrcode+="0"
            else:
                qrcode+="1"
    col_end-=1

    if row_begin <= row_end:
        for i in range(col_end, col_begin-1, -1):
            (r,g,b) = pix[i,row_begin]
            if r == 0:
                qrcode+="0"
            else:
                qrcode+="1"
    row_begin+=1

# create image from generate qrcode stream
outimgname = "dec08_qrcode.png"
outimg = Image.new( 'RGB', (25,25), "white")
pixels_out = outimg.load()

for i in range(0,len(qrcode)):
    if qrcode[i] == '0':
        pixels_out[i%25,i/25]=(0,0,0)

outimg=outimg.resize((250,250))
outimg=outimg.rotate(180)
outimg.save(outimgname,"png")
```
Decoding the new image with a qr decoder we get the flag:
```HV18-$$nn-@@11-LLr0-B1ne```


