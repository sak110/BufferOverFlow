# Fuzzing

## Tools
- zzuf
  - zzuf cat fuz.txt
    - changes the some of the output chars
  - zzuf -r 0 cat fuz.txt
    - 0% of chars are changed
  - zzuf -r 0.50 cat fuz.txt
    - 50% of chars are changed
  - zzuf -b 12- cat fuz.txt
    - starts changing only after byte 12 till EOF
    - 