# SHA1-Serpent
Declare
======
This is SHA1 algorithm written in Serpent, together with self-write Base64 algorithm in Serpent.
SHA1 code is modified from 
https://github.com/ajalt/python-sha1

Many thanks for the open-source python code


Property
------
This code is originally written to response to the WebSocket Upgrade, thus it's not complete SHA1 algorithm, and I don't counter the problem when the Key is too long.


How to use it?
-------
You can call it directly, if you are using this code to answer to a WebSocket Upgrade request, you can simply call

    sha1_with_magic(key)
    
where key is the key sent by the client and should be encrypted. Note this function will automatically add 'magic key' to the key message.
If you are using it for other purpose, please call 

    Sha1Hash().update(key).digest()
 
 
where key is the message to be encrypted.

Notice that <b>Sha1Hash().update(key).digest()</b> will only give you a Base64 Encrypted SHA1 message, instead of the SHA1 coded result.
If you only need the SHA1 coded message, please refer to function <b>digest</b> in class <b>Sha1Hash</b>, where the variable dig is a list of length 5,
each item in the list is an integer stands for 4 bytes, the integer is actually the binary number of 32 bits. And you can use this list to
generate all formats of SHA1 encoded message you would like to.

The pipeline way of representing the whole process is this

    String message ->  Sha1Hash().update(key).digest() -> list of 5, integer type representing SHA1 encoded message -> Base64() -> output string
    
What is Serpent?
------
Serpent is a Python-like language designed by Prof. Roger Dannenberg, I worked with him during my intern time in CMU.
Refer to this link for more information https://www.cs.cmu.edu/~music/serpent/doc/serpent.htm
