# Lightweight Authentic Wireless Communications for Micro:Bit

This is the task of implement an authentication system and encrypted wireless communications
between two Micro:bits using the nRF radio (uBit.radio) and C/C++ programming language. This
includes the multiple  steps.Initially appeared on [git](https://.github.com/).

## Getting Started

Initially here  define there are 3  commands with a single secret code that must be shared by
the given two devices. Here we might simply define the shared secret inside our program, we do not
have to require typing it in the runtime, and we are free to select its format and size. A ‘command’
here is defined as any action that can be performed using a Micro:bit device, or simply launched by
it and executed by another device . 

Using the first Micro:bit (sender), the user can select thecommand using the Micro:bit buttons and 
our system should encrypt the command with AES (aes_enc) and transmit it to the other Micro:bit. The 
second Micro:bit (receiver) should be able to receive the encrypted message, decrypt it(aes_dec), then 
authentically identify the “command” and execute it


### Objectives

**Sender**
- Generate a random salt.
- Generate a data encryption key using the SHA hash function algorithm applied to the
shared secret and salt as follows: dpk=sha256(secret +salt). secret+salt here refersto any
combination function of your choice of the secret and salt such as arithmetic addition,
string appending (concatenation), etc.
- Use AES to encrypted the command with dpk: cipher=aes_enc(command, dpk). The
command here is the message that identify the command. It is up to you to define its
format if needed, and any parameter may also be included if needed.
- Send (cipher, salt) to the receiver Micro:bit via the radio.

**Reciever**
- Receive cipher  and salt.
- Generate a data encryption key using SHA hash of the shared secret and salt, dpk=sha256
 (secret+salt).
- Decrypt the cipher, command=aes_dec(cipher, dpk).
- Run the command.
	
	

### Prerequisites

Requirements for the software and other tools to build
- [UWE CYBER VM](https://www.uwe.ac.uk/study/it-services/software)
- [VS CODE ](https://code.visualstudio.com/download)
- [VI EDITOR ](https://www.example.com)


### Output

- Sample output of the executable  file

  ![image](https://github.com/ShalithaJayamal/MysqlNodeCrud/blob/a36d459e97a5d7ec3afa429713d81b7de9b8d186/e878f11d-e065-48dd-b4a7-3c6246df4c16.jpg)

### Headings Used

    - #include <stdio.h>
    - #include <stdlib.h>
    - #include <string.h>
    - #include <stdint.h>
    - #include <time.h>
    - #include "aes.h"
    - #include "MicroBit.h"
    - #include <stdint.h>

## Running
    gcc sender.cpp -o sender.out
    gcc reciever.cpp -o reciever.out
    ./sender.out
    ./reciever.out


## Authors
- **L M B Galaallu Vitharanalage** 
- **Furhan Imtiaz** 
- **Sibtain  Safdar**


## References

  - https://emn178.github.io/online-tools/sha256.html
  - http://aes.online-domain-tools.com/
  - https://github.com/kokke/tiny-AES-c

