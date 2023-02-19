# Description

We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) kjlijdliljhdjdhfkfkhhjkkhhkihlhnhghekfhmhjhkhfhekfkkkjkghghjhlhghmhhhfkikfkfhm caesar.py

# Solution

First I observed that there are definitions for the global ALPHABET array of 16 lowercase alphabets, few assertions where the flag text.
```python
flag = ""
k = "j"
assert all([i in ALPHABET for i in k])
assert len(k) == 1
```
I assumed that the flag and a single character key are the inputs to the file and the output for the flag required is the string given to us.

We have to reverse engineer the two functions in the script that perform the encryption. The first function b16_encode takes each character of input, turns it into an 8 bit string, splits it in the middle to two 4 bit string and convert each of them into alphabets and joins them all and returns that string
```python
def b16_encode(plain):
	enc = ""
	for c in plain:
		binary = "{0:08b}".format(ord(c))
		enc += ALPHABET[int(binary[:4], 2)]
		enc += ALPHABET[int(binary[4:], 2)]
	return enc
```
Thus to reverse this function, from a string we take two characters at a time and turn them both into 4 bit binary and join both of them and turn them from an 8 bit binary to an alphabet, join all the alphabets and return the string. This is in code will look like this.
```python
def b16_decode(enc: str):
    plain = ""
    for i in range(0, len(enc), 2):
        c1 = enc[i]
        c2 = enc[i+1]
        c1 = ALPHABET.index(c1)
        c2 = ALPHABET.index(c2)
        binary1 = "{0:04b}".format(c1)
        binary2 = "{0:04b}".format(c2)
        plain += chr(int((binary1 + binary2), 2))
    return plain
```
The second function shift works with a char and a key. It's take the sum of both's ASCII ofsets and returns the remainder when it's divided by 16 (The length of the alphabet array)
```python
def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]
```
To reverse it we can take the offset of the char we want to shift back and the key and this time subtract both of their ASCII ofsets and return the remainder when it's divided by 16
```python
def shift_back(c, k):
    t1 = ord(c) - LOWERCASE_OFFSET
    t2 = ord(k) - LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]
```
Now we run these functions for all 16 alphabets and print them.
```python
enc = "kjlijdliljhdjdhfkfkhhjkkhhkihlhnhghekfhmhjhkhfhekfkkkjkghghjhlhghmhhhfkikfkfhm"
for i in ALPHABET:
    unshift = ""
    for j in range(len(enc)):
        unshift += shift_back(enc[j], i)
    flag = b16_decode(unshift)
    print("picoCTF{" + flag + "}")
```
As such all give uncomprehensible strings except one
```
picoCTF{ùÙùÜÝÜÛÑ
ßÞÞßÐ
ÛÚÓÚÒ
ÐÒÓÛßÐ}
ÈèËÌËÊÀûÎÍÍÎÏÿûÊÉþÂÉÁûÎþÁÀüÏþÁÂÊÎÏ}
picoCTF{íü×üý·×º»º¹¿ê½¼¼½¾îê¹¸í±¸°ê½í°¿ë¾í°±¹½¾}
picoCTF{ÜëÆëì¦Æ©ª©¨®Ù¬««¬­ÝÙ¨§Ü §¯Ù¬Ü¯®Ú­Ü¯ ¨¬­}
picoCTF{ËÚµÚÛµÈÌÈËÈËÉË}
picoCTF{ºÉ¤ÉÊ¤·»·º·º¸º}
picoCTF{©¸¸¹svwvu{¦yxxyzª¦ut©}t|¦y©|{§z©|}uyz}
picoCTF{§§¨befedjhgghidclckhkjikldhi}
picoCTF{qQqTUTSYWVVWXSR[RZWZYXZ[SWX}
picoCTF{v`@`CDCBHsFEEFGwsBAvJAIsFvIHtGvIJBFG}
picoCTF{et_tu?_1ac5f3d7920a85610afeb2572831daa8}
picoCTF{TcNcd.N!"! &Q$##$%UQ /T(/'Q$T'&R%T'( $%}
picoCTF{CR=RS=@D@C@CAC}
picoCTF{2A,AB
?202}
picoCTF{!01ûÿþýó.ñððñò".ýü!õüô.ñ!ôó/ò!ôõýñò}
picoCTF{/
/ ê
íîíìâàïïàáìëäëãàãâáãäìàá}
```

thus
Required flag: picoCTF{et_tu?_1ac5f3d7920a85610afeb2572831daa8}
