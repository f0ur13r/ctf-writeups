# hackvent 2019

## 01 - censored

**Solution:**

The qrcode is hidden in the preview tile. You can export it using exiftool.

exiftool -b -ThumbnailImage f182d5f0-1d10-4f0f-a0c1-7cba0981b6da.jpg > tile.jpg
Open, zoom the qrcode to decode the flag.

flag: ```HV19{just-4-PREview!}```


## 02 - Triangulation

**Solution:**

Inside the zip file, you can find STL file (3d object model of christmas ball).
There are many tools to open the file, I've used blender.
The qr code (aztec) is hidden in the ball. I've manually deleted the ball around the code and took a screenshot of the ball. Modify it to black and white and decode with https://zxing.org/.


flag: ```HV19{Cr4ck_Th3_B411!}```


## 03 - Hodor, Hodor, Hodor

**Solution:**

The challenge is a code written in Hodor programming language.
http://www.hodor-lang.org/

npm install -g hodor-lang
hodor challenge03.hd

The output is a base64 string:
SFYxOXtoMDFkLXRoMy1kMDByLTQyMDQtbGQ0WX0=

Using a base64 decoder you get the flag:

flag: ```HV19{h01d-th3-d00r-4204-ld4Y}```

## 04 - password policy circumvention

**Solution:**

Provided is a autohotkey script:
https://www.autohotkey.com/

After you install it on a Windows machine, start it and type in your favorite editor "merry christmas geeks".
To get the correct flag, write the characters slowly and hit enter after every word.


flag: ```HV19{R3memb3r, rem3mber - the 24th 0f December}```

## 05 - Santa Parcel Tracking

**Solution:**

The solution is to dump the hex color codes from the barcode. 
Every color is represented with 6 char hex code. To get the flag you have to extract the last 2 chars.
Drop white pixels and new lines.

convert 157de28f-2190-4c6d-a1dc-02ce9e385b5c.png txt: | gawk 'match($0, /\S+,0.*#\S\S\S\S?(\S\S).*$/, m) { print m[1];}' | grep -v FF | uniq | tr -d '\n' | xxd -r -p

Because I used "uniq", the second "t" in Difficult I added manually.

flag: ```HV19{D1fficult_to_g3t_a_SPT_R3ader}```

## 06 - Bacon and eggs


## 07 - Santa rider

**Solution:**

The 8 LEDs represent a binary char.
Every third frame has a different lighting combination. light on represent a 1, otherwise 0.
You can export the frames with VLC and decode the binary to text.

flag: ```HV19{1m_als0_w0rk1ng_0n_a_r3m0t3_c0ntr0l}```

## 08 - santa api

**Solution:**

curl -s -X POST -H "Content-Type: application/json" http://whale.hacking-lab.com:10101/fsja/login --data "{\"username\":\"testuser\", \"password\":\"passwordpassword\"}"

eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjp7InVzZXJuYW1lIjoidGVzdHVzZXIiLCJwbGF0aW51bSI6ZmFsc2V9LCJleHAiOjE1NzY0NTA3ODYuMjI4MDAwMDAwfQ.zgHNCADA3DCnbApwfn8wowOIF1dsRqIQ8OOPJ8OqP8c

decode the middle (payload) part with base64 decoder, change platinum to true and encode it back to base64.

Get with the modified token a new joke:

curl -X GET "http://whale.hacking-lab.com:10101/fsja/random?token=eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjp7InVzZXJuYW1lIjoidGVzdHVzZXIiLCJwbGF0aW51bSI6dHJ1ZX0sImV4cCI6MTU3NjQ1MTUxOC41NDgwMDAwMDB9.F7rGn0KG3G7aGX8Ygya0CZE91VWyU21VrpPh6vVd0gs"

{"joke":"Congratulation! Sometimes bugs are rather stupid. But that's how it happens, sometimes. Doing all the crypto stuff right and forgetting the trivial stuff like input validation, Hohoho! Here's your flag: 

flag: ```HV19{th3cha1n1s0nlyasstr0ngasth3w3ak3st_l1nk}```

## 09 Santas Quick Response 3.0

**Solution:**

The railway station image give us a hint regarding Wolframs rule 30.
The idea is to xor the flag image with the generate rule 30 image.
https://github.com/zmwangx/rule30
rule30 -n 33 -s 5 rule30.png
the qrcode is 33x33 with 5 pixels for every cell (5x33=165).

using gimp you can overlay the two images and use "exlusive" as interpolation. to get the flag you have to move the qrcode image by 5 pixels (1 cell) to the left.

flag: ```HV19{Cha0tic_yet-0rdered}```

## 10 Guess what

**Solution:**

Use ltrace to reverse engineer the binary.

ltrace -i -o output.txt ./guess3
grep HV19 output.txt

flag: ```HV19{Sh3ll_0bfuscat10n_1s_fut1l3}```

## 13 TrieMe

**Solution:**

The idea was to use a vulnerability in the the put method of PatriciaTrie:
https://issues.apache.org/jira/browse/COLLECTIONS-714

auth_token_4835989\u0000



flag: ```HV19{get_th3_chocolateZ}```

## 17 Unicode Portal

**Solution:**

This github article and the source code inspired me to register the admin user "santa" with 
the char "ſ" instead "s" as the maybe not be a correct input validation. as the user santa is already present, only the password is updated. afterwards you can login with "santa" and the new password. navigating to the admin section you get the flag.
https://eng.getwisdom.io/hacking-github-with-unicode-dotless-i/

flag: ```HV19{h4v1ng_fun_w1th_un1c0d3}```



## hidden 01

**Solution:**

Use the copy to clipboard button from challenge 06 and paste it to a file. The code is hidden inside the text by SNOW steganography. 
Use stegsnow to decrypt:

stegsnow -C hidden1.txt

flag: ```HV19{1stHiddenFound}```

## hidden 02

**Solution:**

The flag is hidden in the filename of the extracted file in challenge 07.
The filename is encoded with base58.

flag: ```HV19{Dont_confuse_0_and_O}```

## hidden 03

**Solution:**

Performing a nmap scan on whale.hacking-lab.com we see open port 17 which is used for the qotd (quote of the day service).
A netcat or telnet on port 17 gives us a single char. I figured out that the letter is changing every hour. By using nc every hour we can get the whole flag. In this example I've used a cron job.

15 * * * * nc whale.hacking-lab.com 17 | tee -a /tmp/hidden03.txt

flag: ```HV19{an0ther_DAILY_fl4g}```
