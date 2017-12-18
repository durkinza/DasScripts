# Get Columns

Usage: getcol [options]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -i STR, --insep=STR   input separator
  -o STR, --outsep=STR  output separator
  -l STR, --lastsep=STR
                        last output serparator
  -s                    strip each input column of whitespace
  -r                    allow printing columns in reverse order

ex.
cat << EOF > data.txt
0 1 2 3 4 5 6 7
000 001 010 011 100 101 110 111
EOF

cat data.txt | getcol 1
0
000

cat data.txt | getcol 1:3
0 1 2
000 001 010

cat data.txt | getcol 1:5:2
0 2 4
000 010 100

cat data.txt | getcol 5:1 -r`
4 3 2 1 0
100 011 010 001 000


cat << EOF > data.txt
0,1,2 ,3, 4,5,6,7
000,001 ,010, 011,100,101,110,111
EOF

cat data.txt | getcol 1 -i","
0
000

cat data.txt | getcol 1:4 -i"," -o":" -l";"
0:1:2 :3;
000:001 :010: 011;

cat data.txt | getcol 1:4 -i"," -o":" -l";" -s
0:1:2:3;
000:001:010:011;
