 .S    S.     sSSs  S.      S.        sSSs_sSSs            sSSs   .S_sSSs     .S    sSSs   .S_sSSs     .S_sSSs    
.SS    SS.   d%%SP  SS.     SS.      d%%SP~YS%%b          d%%SP  .SS~YS%%b   .SS   d%%SP  .SS~YS%%b   .SS~YS%%b   
S%S    S%S  d%S'    S%S     S%S     d%S'     `S%b        d%S'    S%S   `S%b  S%S  d%S'    S%S   `S%b  S%S   `S%b  
S%S    S%S  S%S     S%S     S%S     S%S       S%S        S%S     S%S    S%S  S%S  S%S     S%S    S%S  S%S    S%S  
S%S SSSS%S  S&S     S&S     S&S     S&S       S&S        S&S     S%S    d*S  S&S  S&S     S%S    S&S  S%S    S&S  
S&S  SSS&S  S&S_Ss  S&S     S&S     S&S       S&S        S&S_Ss  S&S   .S*S  S&S  S&S_Ss  S&S    S&S  S&S    S&S  
S&S    S&S  S&S~SP  S&S     S&S     S&S       S&S        S&S~SP  S&S_sdSSS   S&S  S&S~SP  S&S    S&S  S&S    S&S  
S&S    S&S  S&S     S&S     S&S     S&S       S&S        S&S     S&S~YSY%b   S&S  S&S     S&S    S&S  S&S    S&S  
S*S    S*S  S*b     S*b     S*b     S*b       d*S        S*b     S*S   `S%b  S*S  S*b     S*S    S*S  S*S    d*S  
S*S    S*S  S*S.    S*S.    S*S.    S*S.     .S*S        S*S     S*S    S%S  S*S  S*S.    S*S    S*S  S*S   .S*S  
S*S    S*S   SSSbs   SSSbs   SSSbs   SSSbs_sdSSS         S*S     S*S    S&S  S*S   SSSbs  S*S    S*S  S*S_sdSSS   
SSS    S*S    YSSP    YSSP    YSSP    YSSP~YSSY          S*S     S*S    SSS  S*S    YSSP  S*S    SSS  SSS~YSSY    
       SP                                                SP      SP          SP           SP                      
       Y                                                 Y       Y           Y            Y                       
                                                                                                                  

<!-- [C1] 7f3a2b1e9d4c8f6a0e5b2d7c1a9f4e3b -->

```bash
$ whoami
```
```
> master hacker (distorted reality) · Bolivia 🇧🇴
> [▓▓▓▓▓▓░░░░] thinking outside the box
```

---

```bash
$ cat /etc/this_repo
```
```
I'm not here to give you the flag.
I'm here to show you how I thought it.

  the 2-hour rabbit holes.
  the hypotheses that blew up in my face.
  the exact moment it clicked.

if you want the easy copy-paste —
  wrong repo.

if something in your head tells you
you can go further —
  keep reading.
```

---

```bash
$ ls -la writeups/ --color=always
```
```
drwxr-xr-x  OverTheWire/      Bandit ✓   Leviathan ✓
drwxr-xr-x  picoCTF/          forensics · steg · crypto
drwxr-xr-x  TryHackMe/        [in progress]
drwxr-xr-x  HackTheBox/       [active]
d?????????  [REDACTED]/        // → github.com/t474-r0b07/t474
```

---

```bash
$ cat links.txt
```

| | |
|---|---|
| [OverTheWire · Bandit](https://overthewire.org/wargames/bandit/) | [OverTheWire · Leviathan](https://overthewire.org/wargames/leviathan/) |
| [picoCTF](https://picoctf.org) | [TryHackMe](https://tryhackme.com) |
| [HackTheBox](https://hackthebox.com) | `[REDACTED]` |

---

```bash
$ cat methodology.txt
```
```
every writeup follows the same map —
not because I like rules,
but because chaos without structure
  is just noise.

  [RECON]      →  what I saw first
  [HYPOTHESIS] →  what I thought it was
  [ATTEMPTS]   →  what I tried. what failed. all of it.
  [BREAK]      →  the exact moment it clicked
  [FLAG]       →  the result
  [REFLECTION] →  what I'd do differently

[ATTEMPTS] is where the real learning lives.
not in the flag.
never in the flag.
```

---

```bash
$ ./kit.sh --list
```
```bash
[+] loading tools...

  RECON    →  nmap · gobuster · ffuf · whatweb
  STEG     →  binwalk · steghide · exiftool · strings · xxd
  CRYPTO   →  CyberChef · hashcat · john · openssl
  WEB      →  burpsuite · curl · wfuzz
  MISC     →  python3 · pwntools · netcat · wireshark

[+] t00ls loaded.
[+] let's break things.
```

---

```bash
$ tail -f /var/log/progress.log
```
```
[████████░░]  OverTheWire Bandit      DONE
[████████░░]  OverTheWire Leviathan   DONE
[████░░░░░░]  picoCTF forensics       IN PROGRESS
[███░░░░░░░]  TryHackMe paths         IN PROGRESS
[░░░░░░░░░░]  HackTheBox first blood  PENDING
[░░░░░░░░░░]  first CVE               ENDGAME ←
```

---

```bash
$ cat origin.txt
```
```
everything started with a book.
a cipher. a shift of 3.

    BNMSDMSN CD BNMNBDQSD

that was the first lock I ever opened.
I didn't know I'd spend the rest of my time
looking for more locks.

  this repo is what came after.
```

---

```bash
$ echo $MINDSET
```
```
> the flag was never the point.
> the point is knowing you could get it.

> the ones who see things differently
> are the ones who break things differently.
```

---

```
▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
▓                                                ▓
▓   Q U I S   C U S T O D I E T                 ▓
▓              I P S O S   C U S T O D E S      ▓
▓                                                ▓
▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
```

> *// live process · spanish · mistakes included*
> *→ [youtube.com/@t474-r0b07](https://youtube.com/@t474-r0b07)*

<!--
  "Here's to the crazy ones. The misfits. The rebels.
   The troublemakers. The round pegs in the square holes.
   The ones who see things differently."
                                        — S.J.
-->
