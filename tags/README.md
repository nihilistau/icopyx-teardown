# iCopy-X Tags


## iCE

an iClass Elite locked with password `2020666666668888`

```
[usb] pm3 --> hf iclass rdbl -b 1 -k 2020666666668888 --elite

[+]  block   1/0x01 : 12 FF FF FF 7F 1F FF 3C 

[usb] pm3 --> hf iclass info

[=] --------------------- Tag Information ----------------------
[+]     CSN: 20 59 A7 02 F8 FF 12 E0  uid
[+]  Config: 12 FF FF FF 7F 1F FF 3C  card configuration
[+] E-purse: FF FF FF FF F9 FF FF FF  Card challenge, CC
[+]      Kd: 00 00 00 00 00 00 00 00  debit key, hidden
[+]      Kc: 00 00 00 00 00 00 00 00  credit key, hidden
[+]     AIA: FF FF FF FF FF FF FF FF  application issuer area
[=] -------------------- card configuration --------------------
[=]     Raw: 12 FF FF FF 7F 1F FF 3C 
[=]          12.....................  app limit
[=]             FFFF ( 65535 )......  OTP
[=]                   FF............  block write lock
[=]                      7F.........  chip
[=]                         1F......  mem
[=]                            FF...  EAS
[=]                               3C  fuses
[=]   Fuses:
[+]     mode......... Application (locked)
[+]     coding....... ISO 14443-2 B / 15693
[+]     crypt........ Secured page, keys not locked
[=]     RA........... Read access not enabled
[=] -------------------------- Memory --------------------------
[=]  2 KBits/2 App Areas ( 256 bytes )
[=]     AA1 blocks 13 { 0x06 - 0x12 (06 - 18) }
[=]     AA2 blocks 18 { 0x13 - 0x1F (19 - 31) }
[=] ------------------------- KeyAccess ------------------------
[=]  * Kd, Debit key, AA1    Kc, Credit key, AA2 *
[=]     Read A....... debit or credit
[=]     Read B....... debit or credit
[=]     Write A...... credit
[=]     Write B...... credit
[=]     Debit........ debit or credit
[=]     Credit....... credit
[=] ------------------------ Fingerprint -----------------------
[+]     CSN.......... HID range
[+]     Credential... iCLASS legacy
[+]     Card type.... PicoPass 2K
```

What it does when making a copy, here itself: (beware, old proxmark3 syntax)
```
hf iclass rdbl b 01 k AFA785A7DAB33378
hf iclass rdbl b 01 k AFA785A7DAB33378
hf iclass rdbl b 01 k 2020666666668888
hf iclass rdbl b 01 k 2020666666668888 e
hf iclass info
hf iclass dump k 2020666666668888 f /mnt/upan/dump/iclass/Iclass-Elite_2059A702F8FF12E0_1 e

# swapping cards

hf iclass wrbl b 06 d 030303030003E017 k 2020666666668888 e
hf iclass wrbl b 07 d 74C6C5EAF5DF3065 k 2020666666668888 e
hf iclass wrbl b 08 d 2AD4C8211F996871 k 2020666666668888 e
hf iclass wrbl b 09 d 2AD4C8211F996871 k 2020666666668888 e
hf iclass wrbl b 0a d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 0b d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 0c d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 0d d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 0e d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 0f d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 10 d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 11 d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass wrbl b 12 d FFFFFFFFFFFFFFFF k 2020666666668888 e
hf iclass calcnewkey o 2020666666668888 n 2020666666668888 ee
hf iclass wrbl b 03 d 0000000000000000 k 2020666666668888 e
hf iclass rdbl b 01 k 2020666666668888 e
hf iclass rdbl b 06 k 2020666666668888 e
hf iclass rdbl b 07 k 2020666666668888 e
hf iclass rdbl b 08 k 2020666666668888 e
hf iclass rdbl b 09 k 2020666666668888 e
hf iclass rdbl b 0a k 2020666666668888 e
hf iclass rdbl b 0b k 2020666666668888 e
hf iclass rdbl b 0c k 2020666666668888 e
hf iclass rdbl b 0d k 2020666666668888 e
hf iclass rdbl b 0e k 2020666666668888 e
hf iclass rdbl b 0f k 2020666666668888 e
hf iclass rdbl b 10 k 2020666666668888 e
hf iclass rdbl b 11 k 2020666666668888 e
hf iclass rdbl b 12 k 2020666666668888 e
```

Note that FW 1.0.3 is buggy, FW 1.0.7 is working fine

To reuse an iCopy-X iCE, it must be set back to the initial key, e.g.

```
hf iclass calcnewkey --old AFA785A7DAB33378 --new 2020666666668888 --elite2
Xor div key......... B3 56 7D DF 3E 64 E6 D7
hf iclass wrbl -b 3 -d B3567DDF3E64E6D7 -k AFA785A7DAB33378 --elite
```
## iCL

an iClass Legacy locked with password `2020666666668888`

```
[usb] pm3 --> hf iclass rdbl -b 1 -k 2020666666668888
[+]  block   1/0x01 : 12 FF FF FF 7F 1F FF 3C 

[usb] pm3 --> hf iclass info

[=] --------------------- Tag Information ----------------------
[+]     CSN: 80 71 A7 02 F8 FF 12 E0  uid
[+]  Config: 12 FF FF FF 7F 1F FF 3C  card configuration
[+] E-purse: FF FF FF FF FB FF FF FF  Card challenge, CC
[+]      Kd: 00 00 00 00 00 00 00 00  debit key, hidden
[+]      Kc: 00 00 00 00 00 00 00 00  credit key, hidden
[+]     AIA: FF FF FF FF FF FF FF FF  application issuer area
[=] -------------------- card configuration --------------------
[=]     Raw: 12 FF FF FF 7F 1F FF 3C 
[=]          12.....................  app limit
[=]             FFFF ( 65535 )......  OTP
[=]                   FF............  block write lock
[=]                      7F.........  chip
[=]                         1F......  mem
[=]                            FF...  EAS
[=]                               3C  fuses
[=]   Fuses:
[+]     mode......... Application (locked)
[+]     coding....... ISO 14443-2 B / 15693
[+]     crypt........ Secured page, keys not locked
[=]     RA........... Read access not enabled
[=] -------------------------- Memory --------------------------
[=]  2 KBits/2 App Areas ( 256 bytes )
[=]     AA1 blocks 13 { 0x06 - 0x12 (06 - 18) }
[=]     AA2 blocks 18 { 0x13 - 0x1F (19 - 31) }
[=] ------------------------- KeyAccess ------------------------
[=]  * Kd, Debit key, AA1    Kc, Credit key, AA2 *
[=]     Read A....... debit or credit
[=]     Read B....... debit or credit
[=]     Write A...... credit
[=]     Write B...... credit
[=]     Debit........ debit or credit
[=]     Credit....... credit
[=] ------------------------ Fingerprint -----------------------
[+]     CSN.......... HID range
[+]     Credential... iCLASS legacy
[+]     Card type.... PicoPass 2K
```

What it does when making a copy, here itself: (beware, old proxmark3 syntax)
```
hf iclass rdbl b 01 k AFA785A7DAB33378
hf iclass rdbl b 01 k AFA785A7DAB33378
hf iclass rdbl b 01 k 2020666666668888
hf iclass info
hf iclass dump k 2020666666668888 f /mnt/upan/dump/iclass/Iclass-Legacy_8071A702F8FF12E0_1

# swapping cards

hf iclass wrbl b 06 d 000000000000E014 k 2020666666668888
hf iclass wrbl b 07 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 08 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 09 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0a d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0b d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0c d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0d d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0e d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 0f d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 10 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 11 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass wrbl b 12 d FFFFFFFFFFFFFFFF k 2020666666668888
hf iclass calcnewkey o 2020666666668888 n 2020666666668888
hf iclass wrbl b 03 d 0000000000000000 k 2020666666668888
hf iclass rdbl b 01 k 2020666666668888
hf iclass rdbl b 06 k 2020666666668888
hf iclass rdbl b 07 k 2020666666668888
hf iclass rdbl b 08 k 2020666666668888
hf iclass rdbl b 09 k 2020666666668888
hf iclass rdbl b 0a k 2020666666668888
hf iclass rdbl b 0b k 2020666666668888
hf iclass rdbl b 0c k 2020666666668888
hf iclass rdbl b 0d k 2020666666668888
hf iclass rdbl b 0e k 2020666666668888
hf iclass rdbl b 0f k 2020666666668888
hf iclass rdbl b 10 k 2020666666668888
hf iclass rdbl b 11 k 2020666666668888
hf iclass rdbl b 12 k 2020666666668888
```

Note that FW 1.0.3 is buggy, FW 1.0.7 is working fine

To reuse an iCopy-X iCL, it must be set back to the initial key, e.g.

```
hf iclass calcnewkey --old AFA785A7DAB33378 --new 2020666666668888
Xor div key......... 1E 1E 03 6C C9 5A 76 4E 
hf iclass wrbl -b 3 -d 1E1E036CC95A764E -k AFA785A7DAB33378
```

## iCS

An iClass Legacy locked with password `6666202066668888`

```
[usb] pm3 --> hf iclass rdbl -b 1 -k 6666202066668888

[+]  block   1/0x01 : 12 FF FF FF 7F 1F FF 3C 

[usb] pm3 --> hf iclass info

[=] --------------------- Tag Information ----------------------
[+]     CSN: 95 F0 6C 01 F9 FF 12 E0  uid
[+]  Config: 12 FF FF FF 7F 1F FF 3C  card configuration
[+] E-purse: FA FF FF FF FF FF FF FF  Card challenge, CC
[+]      Kd: 00 00 00 00 00 00 00 00  debit key, hidden
[+]      Kc: 00 00 00 00 00 00 00 00  credit key, hidden
[+]     AIA: FF FF FF FF FF FF FF FF  application issuer area
[=] -------------------- card configuration --------------------
[=]     Raw: 12 FF FF FF 7F 1F FF 3C 
[=]          12.....................  app limit
[=]             FFFF ( 65535 )......  OTP
[=]                   FF............  block write lock
[=]                      7F.........  chip
[=]                         1F......  mem
[=]                            FF...  EAS
[=]                               3C  fuses
[=]   Fuses:
[+]     mode......... Application (locked)
[+]     coding....... ISO 14443-2 B / 15693
[+]     crypt........ Secured page, keys not locked
[=]     RA........... Read access not enabled
[=] -------------------------- Memory --------------------------
[=]  2 KBits/2 App Areas ( 256 bytes )
[=]     AA1 blocks 13 { 0x06 - 0x12 (06 - 18) }
[=]     AA2 blocks 18 { 0x13 - 0x1F (19 - 31) }
[=] ------------------------- KeyAccess ------------------------
[=]  * Kd, Debit key, AA1    Kc, Credit key, AA2 *
[=]     Read A....... debit or credit
[=]     Read B....... debit or credit
[=]     Write A...... credit
[=]     Write B...... credit
[=]     Debit........ debit or credit
[=]     Credit....... credit
[=] ------------------------ Fingerprint -----------------------
[+]     CSN.......... HID range
[+]     Credential... iCLASS legacy
[+]     Card type.... PicoPass 2K
```

To reuse an iCopy-X iCS, it must be set back to the initial key, e.g.

```
[usb] pm3 --> hf iclass calcnewkey --old AEA684A6DAB23278 --new 6666202066668888
[+] CSN     E1 64 6D 01 F9 FF 12 E0 
[+] epurse  FF FF FF FF FB FF FF FF 
[+] Old div key......... 7B F6 4D 4C 5E 95 07 EA 
[+] New div key......... 40 DD 85 E0 B5 A8 66 93 
[+] Xor div key......... 3B 2B C8 AC EB 3D 61 79 

[usb] pm3 --> hf iclass wrbl -b 3 -d 3B2BC8ACEB3D6179 -k AEA684A6DAB23278
[+] Wrote block   3/0x03 successful
```


## ICODE

A magic ICODE card.

```
[usb] pm3 --> hf 15 info

[+]  UID: E0 04 01 50 00 00 69 25
[+] TYPE: NXP(Philips); IC SL2 ICS20/ICS21(SLI) ICS2002/ICS2102(SLIX) ICS2602(SLIX2)
[+] Using UID... E0 04 01 50 00 00 69 25

[=] --- Tag Information ---------------------------
[=] -------------------------------------------------------------
[+]       TYPE: NXP(Philips); IC SL2 ICS20/ICS21(SLI) ICS2002/ICS2102(SLIX) ICS2602(SLIX2)
[+]        UID: E0 04 01 50 00 00 69 25
[+]    SYSINFO: 00 0F 25 69 00 00 50 01 04 E0 00 00 1B 03 01 
[+]      - DSFID supported        [0x00]
[+]      - AFI   supported        [0x00]
[+]      - IC reference supported [0x01]
[+]      - Tag provides info on memory layout (vendor dependent)
[+]            4 (or 3) bytes/blocks x 28 blocks
```


What it does when making a copy, here itself: (beware, old proxmark3 syntax)

```
hf sea
hf 15 dump f /mnt/upan/dump/icode/ICODE_E004015000006925_1

# swapping cards

hf 15 csetuid E004015000006925
hf 15 restore f /mnt/upan/dump/icode/ICODE_E004015000006925_1.bin
hf sea
```

## ID1

It's a T5577 locked with password `20206666`.
```
lf t55xx detect -p 20206666
lf t55xx dump -p 20206666 --override
```

The iCopy-X accepts to make copies on ordinary T5577 tags and will lock them with the same password.

What it does when making a copy, here an Indala: (beware, old proxmark3 syntax)
```
lf t55xx wipe p 20206666
lf t55xx detect
lf lf indala clone  -r a0000000a0002021
lf t55xx detect
# Block0         : 0x00081040
lf t55xx write b 7 d 20206666
lf t55xx write b 0 d 00081050
lf t55xx detect p 20206666
lf sea
lf indala read
```

To recover a locked tag:
```
lf t55xx wipe -p 20206666
lf t55xx detect
```

## M1-4b (L1)

MIFARE Classic 1k Gen1a / UID

First sector A & B keys are `E00000000000`. XS version doesn't verify that key.

```
hf 14a info
hf mf cload b /mnt/upan/dump/mf1/M1-1K-4B_11223344_1.bin
```

Note that by default iCopy-X is also sending commands attempting to lock a UFUID, cf "M1-4b (L3)"

## M1-4b (L2)

MIFARE Classic 1k Gen2 / CUID / DirectWrite

First sector A & B keys are `E00000000000`. XS version doesn't verify that key.

```
hf 14a info
hf mf cgetblk 0
hf mf fchk 1 /tmp/.keys/mf_tmp_keys
hf mf rdbl 63 A ffffffffffff
hf mf wrbl 60 A ffffffffffff 00000000000000000000000000000000
hf mf wrbl 61 A ffffffffffff 00000000000000000000000000000000
hf mf wrbl 62 A ffffffffffff 00000000000000000000000000000000
hf mf wrbl 56 A ffffffffffff 00000000000000000000000000000000
...
hf mf wrbl 0 A e00000000000 A43498DED688040047C1252785001906
hf mf wrbl 1 A e00000000000 140103E103E103E103E103E103E103E1
hf mf wrbl 2 A e00000000000 03E103E103E103E103E103E103E103E1
hf mf wrbl 63 A ffffffffffff D3F7D3F7D3F77F078840FFFFFFFFFFFF
hf mf wrbl 59 A ffffffffffff D3F7D3F7D3F77F078840FFFFFFFFFFFF
...
hf mf wrbl 3 A e00000000000 A0A1A2A3A4A5787788C1FFFFFFFFFFFF
```

## M1-4b (L3)

MIFARE Classic 1k Gen1a / UFUID

Same as MIFARE Classic Gen1a (L1), but block0 can be locked with special command.

First sector A & B keys are `E00000000000`. XS version doesn't verify that key.

```
hf mf cload b /mnt/upan/dump/mf1/M1-1K-4B_11223344_1.bin
hf 14a raw -p -a -b 7 40
hf 14a raw -p -a 43
hf 14a raw -c -p -a e000
hf 14a raw -c -p -a e100
hf 14a raw -c -p -a 85000000000000000000000000000008
hf 14a raw -c -a 5000
```

## M1-7b

MIFARE Classic 1k 7b-UID Gen2 / CUID / DirectWrite

All default keys.

Usage: cf "M1-4b (L2)"

## M4-4b

MIFARE Classic 4k Gen2 / CUID / DirectWrite

All default keys.

Usage: cf "M1-4b (L2)"

## M4-7b

MIFARE Classic 4k 7b-UID Gen2 / CUID / DirectWrite

All default keys.

Usage: cf "M1-4b (L2)"

## NTAG

A NTAG21x

```
[usb] pm3 --> hf mfu info

[=] --- Tag Information --------------------------
[=] -------------------------------------------------------------
[+]       TYPE: NTAG 216 888bytes (NT2H1611G0DU) ( magic  )
[+]        UID: 11 22 33 55 66 77 88 
[+]     UID[0]: 11, Emosyn-EM Microelectronics USA
      BCC0: 44, crc should be 88
      BCC1: FF, crc should be CC
[+]   Internal: FF (not default)
[+]       Lock: FF FF  - //
[+] OneTimePad: E1 10 6D 00  - @�0

[=] --- NDEF Message
[+] Capability Container: E1 10 6D 00 
[+]   E1: NDEF Magic Number
[+]   10: version 0.1 supported by tag
[+]        : Read access granted without any security / Write access granted without any security
[+]   6D: Physical Memory Size: 872 bytes
[+]   6D: NDEF Memory Size: 872 bytes
[+]   Additional feature information
[+]   00
[+]   00000000
[+]   xxx      - 00: RFU (ok)
[+]      x     - 00: don't support special frame
[+]       x    - 00: don't support lock block
[+]        xx  - 00: RFU (ok)
[+]          x - 00: IC don't support multiple block reads

[=] --- Tag Counter
[=]        [02]: FF FF FF 
[+]             - 00 tearing ( fail )

[=] --- Tag Signature
[=]     Elliptic curve parameters: NID_secp128r1
[=]              TAG IC Signature: FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
[+]        Signature verification ( fail )

[=] --- Tag Version
[=]        Raw bytes: 00 04 04 02 01 00 13 03 
[=]        Vendor ID: 04, NXP Semiconductors Germany
[=]     Product type: 04, NTAG
[=]  Product subtype: 02, 50pF
[=]    Major version: 01
[=]    Minor version: 00
[=]             Size: 13, (1024 <-> 512 bytes)
[=]    Protocol type: 03, ISO14443-3 Compliant

[=] --- Tag Configuration
[=]   cfg0 [227/0xE3]: 00 00 00 FF 
[=]                     - strong modulation mode disabled
[=]                     - pages don't need authentication
[=]   cfg1 [228/0xE4]: 00 05 00 00 
[=]                     - Unlimited password attempts
[=]                     - NFC counter disabled
[=]                     - NFC counter not protected
[=]                     - user configuration writeable
[=]                     - write access is protected with password
[=]                     - 05, Virtual Card Type Identifier is default
[=]   PWD  [229/0xE5]: FF FF FF FF - (cannot be read)
[=]   PACK [230/0xE6]: FF FF       - (cannot be read)
[=]   RFU  [230/0xE6]:       FF FF - (cannot be read)

[+] --- Known EV1/NTAG passwords
[+] Found default password FF FF FF FF  pack FF FF
[=] ------------------------ Fingerprint -----------------------
[=] Reading tag memory...
[=] ------------------------------------------------------------

[usb] pm3 --> script run hf_mfu_magicwrite -c
[+] executing lua /home/usr/local/bin/../share/proxmark3/luascripts/hf_mfu_magicwrite.lua
[+] args '-c'
----------------------------------------	
----------------------------------------	

Magic NTAG 21* Configuration	
 - Type    	NTAG 216	(genuine cardtype)	
 - Password	FFFFFFFF	
 - Pack    	0000	
 - Version 	0004040201000F03	
 - Signature	9739523E684347A7DB9B6B16CB61D4BAE6C7616AD529496DC68158F6FFB73404	

[+] finished hf_mfu_magicwrite
```

What it does when making a copy, here itself: (beware, old proxmark3 syntax)
```
hf 14a info
hf mf cgetblk 0
hf mfu info
hf mfu dump f /mnt/upan/dump/mfu/NTAG216_11223355667788_1

# swapping cards

hf mfu restore s e f /mnt/upan/dump/mfu/NTAG216_11223355667788_1.bin
[-] Failed convert on load to new Ultralight/NTAG format
hf mf cgetblk 0

```

## UL

```
[usb] pm3 --> hf mfu info

[=] --- Tag Information --------------------------
[=] -------------------------------------------------------------
[+]       TYPE: Unknown 000000  
[+]        UID: 00 00 00 00 00 00 00 
[+]     UID[0]: 00, no tag-info available
      BCC0: 00, crc should be 88
[+]       BCC1: 00 (ok)
[+]   Internal: 00 (not default)
[+]       Lock: 00 00  - 00
[+] OneTimePad: 00 00 00 00  - 0000
[=] ------------------------ Fingerprint -----------------------
[=] Reading tag memory...
[=] ------------------------------------------------------------
```

What it does when making a copy, here itself: (beware, old proxmark3 syntax)
```
hf 14a info
hf mf cgetblk 0
hf mfu info
hf mfu dump f /mnt/upan/dump/mfu/M0-UL_00000000000000_1

# swapping cards

hf mfu restore s e f /mnt/upan/dump/mfu/M0-UL_00000000000000_1.bin
[-] Failed convert on load to new Ultralight/NTAG format
```

on another card:

```
hf mfu restore s e f /mnt/upan/dump/mfu/M0-UL_044762415B2380_1.bin
[!] failed to write block ...
```

## UL-C

```
[usb] pm3 --> hf mfu info

[=] --- Tag Information --------------------------
[=] -------------------------------------------------------------
[+]       TYPE: MIFARE Ultralight C (MF0ULC)  
[+]        UID: 00 00 00 00 00 00 00 
[+]     UID[0]: 00, no tag-info available
      BCC0: 00, crc should be 88
[+]       BCC1: 00 (ok)
[+]   Internal: 00 (not default)
[+]       Lock: 00 00  - 00
[+] OneTimePad: 00 00 00 00  - 0000

--- UL-C Configuration
 Higher Lockbits [40/0x28]: 00 00 00 00  - 00
         Counter [41/0x29]: 00 00 00 00  - 00
           Auth0 [42/0x2A]: 00 00 00 00  default
           Auth1 [43/0x2B]: 00 00 00 00  read and write access restricted
[=] Trying some default 3des keys
[#] failed authentication
[#] Authentication failed
[+] Found default 3des key: 
[=]     deskey1 [44/0x2C]: 00 00 00 00  [....]
[=]     deskey1 [45/0x2D]: 00 00 00 00  [....]
[=]     deskey2 [46/0x2E]: 00 00 00 00  [....]
[=]     deskey2 [47/0x2F]: 00 00 00 00  [....]
[=] 3des key: 00000000000000000000000000000000
```

What it does when making a copy, here itself: (beware, old proxmark3 syntax)
```
hf 14a info
hf mf cgetblk 0
hf mfu info
hf mfu dump f /mnt/upan/dump/mfu/M0-UL-C_00000000000000_1

# swapping cards

hf mfu restore s e f /mnt/upan/dump/mfu/M0-UL-C_00000000000000_1.bin
[-] Failed convert on load to new Ultralight/NTAG format
```

on another card:

```
hf mfu restore s e f /mnt/upan/dump/mfu/M0-UL-C_0430B001B02780_1.bin
hf 14a info
hf mf cgetblk 0
hf mfu info
```

## UL Ev1

A NTAG21x configured as UL Ev1

```
[usb] pm3 --> script run hf_mfu_magicwrite -c
[+] executing lua /home/usr/local/bin/../share/proxmark3/luascripts/hf_mfu_magicwrite.lua
[+] args '-c'
----------------------------------------	
----------------------------------------	

Magic NTAG 21* Configuration	
 - Type    	NTAG 213	(genuine cardtype)	
 - Password	FFFFFFFF	
 - Pack    	FFFF	
 - Version 	0004030101000B03    (UL EV1 48b)
 - Signature	FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF	

[+] finished hf_mfu_magicwrite
```
