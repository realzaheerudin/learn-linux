# Quiz

## Question 1 (50 Marks)

The objective is to draw up five tables, one for each type of test data, showing the following:

| File Name           | Program name | Original File size (bytes) | Compressed file size (bytes) | Compression ratio % | Comments |
|---------------------|--------------|----------------------------|------------------------------|---------------------|----------|
| executable_file.exe | huffcode     |                            |                              |                     |          |
| executable_file.exe | NTFS         |                            |                              |                     |          |
| executable_file.exe | etc.         |                            |                              |                     |          |



The programs to use are listed on Moodle.

Calculate the ratio as (compressed size) / (original size). The easiest way to do this will be to set up a spreadsheet to do the calculation for you. If a program reports the compression ratio, make sure it is defined in the same way. If you notice anything interesting, put in a comment about it.                                /mnt/third      ext4    500M  10M   490M  2% /mnt/third

## Answer 1


-rw-r--r-- 1 zaheer users  5296128 Nov 15 21:56 executable_file.exe
-rw-r--r-- 1 zaheer users   289570 Nov 15 21:56 html_file.html
-rw-r--r-- 1 zaheer users 12603504 Nov 15 21:56 image_file.tif
-rw-r--r-- 1 zaheer users  1081286 Nov 15 21:56 large_pdf_file.pdf
-rw-r--r-- 1 zaheer users    55191 Nov 15 21:56 text_file.txt

gzip executable_file.exe
gzip html_file.html
gzip image_file.tif
gzip large_pdf_file.pdf
gzip text_file.txt



rw-r--r-- 1 zaheer users 1926476 Nov 15 21:56 executable_file.exe.gz
-rw-r--r-- 1 zaheer users   28007 Nov 15 21:56 html_file.html.gz
-rw-r--r-- 1 zaheer users 1567967 Nov 15 21:56 image_file.tif.gz
-rw-r--r-- 1 zaheer users  881146 Nov 15 21:56 large_pdf_file.pdf.gz
-rw-r--r-- 1 zaheer users   19946 Nov 15 21:56 text_file.txt.gz

./huffcode -iexecutable_file.exe -oexecutable_file.exe.huff -c
./huffcode -ihtml_file.html -ohtml_file.html.huff -c
./huffcode -iimage_file.tif -oimage_file.tif.huff -c
./huffcode -ilarge_pdf_file.pdf -olarge_pdf_file.pdf.huff -c
./huffcode -itext_file.txt -otext_file.txt.huff -c

-rw-r--r-- 1 zaheer users  5296128 Nov 15 21:56 executable_file.exe
-rw-r--r-- 1 zaheer users  3953367 Nov 15 22:19 executable_file.exe.huff
-rw-r--r-- 1 zaheer users   289570 Nov 15 21:56 html_file.html
-rw-r--r-- 1 zaheer users   188037 Nov 15 22:19 html_file.html.huff
-rwxr-xr-x 1 zaheer users    39352 Nov 15 22:12 huffcode
-rw-r--r-- 1 zaheer users 12603504 Nov 15 21:56 image_file.tif
-rw-r--r-- 1 zaheer users  9336604 Nov 15 22:19 image_file.tif.huff
-rw-r--r-- 1 zaheer users  1081286 Nov 15 21:56 large_pdf_file.pdf
-rw-r--r-- 1 zaheer users  1066163 Nov 15 22:19 large_pdf_file.pdf.huff
-rw-r--r-- 1 zaheer users    55191 Nov 15 21:56 text_file.txt
-rw-r--r-- 1 zaheer users    33035 Nov 15 22:19 text_file.txt.huff

zaheer@localhost:~/learn-linux/compression> zstd executable_file.exe
executable_file.exe  : 37.07%   (  5.05 MiB =>   1.87 MiB, executable_file.exe.zst) 
zaheer@localhost:~/learn-linux/compression> zstd html_file.html
html_file.html       :  9.04%   (   283 KiB =>   25.6 KiB, html_file.html.zst) 
zaheer@localhost:~/learn-linux/compression> zstd image_file.tif
image_file.tif       : 10.75%   (  12.0 MiB =>   1.29 MiB, image_file.tif.zst) 
zaheer@localhost:~/learn-linux/compression> zstd large_pdf_file.pdf
large_pdf_file.pdf   : 82.64%   (  1.03 MiB =>    873 KiB, large_pdf_file.pdf.zst) 
zaheer@localhost:~/learn-linux/compression> zstd text_file.txt
text_file.txt        : 37.72%   (  53.9 KiB =>   20.3 KiB, text_file.txt.zst)  
zaheer@localhost:~/learn-linux/compression> dir
total 37340
-rw-r--r-- 1 zaheer users  5296128 Nov 15 21:56 executable_file.exe
-rw-r--r-- 1 zaheer users  3953367 Nov 15 22:19 executable_file.exe.huff
-rw-r--r-- 1 zaheer users  1963046 Nov 15 21:56 executable_file.exe.zst
-rw-r--r-- 1 zaheer users   289570 Nov 15 21:56 html_file.html
-rw-r--r-- 1 zaheer users   188037 Nov 15 22:19 html_file.html.huff
-rw-r--r-- 1 zaheer users    26191 Nov 15 21:56 html_file.html.zst
-rwxr-xr-x 1 zaheer users    39352 Nov 15 22:12 huffcode
-rw-r--r-- 1 zaheer users 12603504 Nov 15 21:56 image_file.tif
-rw-r--r-- 1 zaheer users  9336604 Nov 15 22:19 image_file.tif.huff
-rw-r--r-- 1 zaheer users  1354509 Nov 15 21:56 image_file.tif.zst
-rw-r--r-- 1 zaheer users  1081286 Nov 15 21:56 large_pdf_file.pdf
-rw-r--r-- 1 zaheer users  1066163 Nov 15 22:19 large_pdf_file.pdf.huff
-rw-r--r-- 1 zaheer users   893597 Nov 15 21:56 large_pdf_file.pdf.zst
-rw-r--r-- 1 zaheer users    55191 Nov 15 21:56 text_file.txt
-rw-r--r-- 1 zaheer users    33035 Nov 15 22:19 text_file.txt.huff
-rw-r--r-- 1 zaheer users    20816 Nov 15 21:56 text_file.txt.zst


| File Name           | Program name | Original File size (bytes) | Compressed file size (bytes) | Compression ratio % | Comments |
|---------------------|--------------|----------------------------|------------------------------|---------------------|----------|
| executable_file.exe | gzip         | 5296128                    | 1926476                      |                     |          |
| executable_file.exe | zstd         | 5296128                    | 1963046                      |                     |          |
| executable_file.exe | huffcode     | 5296128                    | 3953367                      |                     |          |
| html_file.html      | gzip         | 289570                     | 28007                        |                     |          |
| html_file.html      | zstd         | 289570                     | 26191                        |                     |          |
| html_file.html      | huffcode     | 289570                     | 188037                       |                     |          |
| image_file.tif      | gzip         | 12603504                   | 1567967                      |                     |          |
| image_file.tif      | zstd         | 12603504                   | 1354509                      |                     |          |
| image_file.tif      | huffcode     | 12603504                   | 9336604                      |                     |          |
| large_pdf_file.pdf  | gzip         | 1081286                    | 881146                       |                     |          |
| large_pdf_file.pdf  | zstd         | 1081286                    | 893597                       |                     |          |
| large_pdf_file.pdf  | huffcode     | 1081286                    | 1066163                      |                     |          |
| text_file.txt       | gzip         | 55191                      | 19946                        |                     |          |
| text_file.txt       | zstd         | 55191                      | 20816                        |                     |          |
| text_file.txt       | huffcode     | 55191                      | 33035                        |                     |          |



## Question 2
Using the Linux time(1) command, compare the compression and decompression speeds of gzip, zstd, and huffcode for each of the five test data files. Put your results in 5 tables, one for each data type. Upload the spreadsheet.

## Answer 2
zaheer@localhost:~/learn-linux/compression> time gzip executable_file.exe

real    0m0.436s
user    0m0.220s
sys     0m0.179s
zaheer@localhost:~/learn-linux/compression> time gzip html_file.html

real    0m0.011s
user    0m0.009s
sys     0m0.000s
zaheer@localhost:~/learn-linux/compression> time gzip image_file.tif

real    0m0.536s
user    0m0.423s
sys     0m0.107s
zaheer@localhost:~/learn-linux/compression> time gzip large_pdf_file.pdf

real    0m0.064s
user    0m0.057s
sys     0m0.005s
zaheer@localhost:~/learn-linux/compression> time gzip text_file.txt

real    0m0.012s
user    0m0.004s
sys     0m0.008s


zaheer@localhost:~/learn-linux/compression> time gunzip executable_file.exe.gz

real    0m0.097s
user    0m0.047s
sys     0m0.046s
zaheer@localhost:~/learn-linux/compression> time gunzip html_file.html.gz

real    0m0.017s
user    0m0.012s
sys     0m0.004s
zaheer@localhost:~/learn-linux/compression> time gunzip image_file.tif.gz

real    0m0.134s
user    0m0.069s
sys     0m0.064s
zaheer@localhost:~/learn-linux/compression> time gunzip large_pdf_file.pdf.gz

real    0m0.028s
user    0m0.020s
sys     0m0.006s
zaheer@localhost:~/learn-linux/compression> time gunzip text_file.txt.gz

real    0m0.015s
user    0m0.006s
sys     0m0.009s

zaheer@localhost:~/learn-linux/compression> time zstd executable_file.exe
executable_file.exe  : 37.07%   (  5.05 MiB =>   1.87 MiB, executable_file.exe.zst) 

real    0m0.176s
user    0m0.020s
sys     0m0.119s
zaheer@localhost:~/learn-linux/compression> time zstd html_file.html
html_file.html       :  9.04%   (   283 KiB =>   25.6 KiB, html_file.html.zst) 

real    0m0.042s
user    0m0.004s
sys     0m0.030s
zaheer@localhost:~/learn-linux/compression> time zstd image_file.tif
image_file.tif       : 10.75%   (  12.0 MiB =>   1.29 MiB, image_file.tif.zst) 

real    0m0.093s
user    0m0.031s
sys     0m0.059s
zaheer@localhost:~/learn-linux/compression> time zstd large_pdf_file.pdf
large_pdf_file.pdf   : 82.64%   (  1.03 MiB =>    873 KiB, large_pdf_file.pdf.zst) 

real    0m0.036s
user    0m0.012s
sys     0m0.013s
zaheer@localhost:~/learn-linux/compression> time zstd text_file.txt
text_file.txt        : 37.72%   (  53.9 KiB =>   20.3 KiB, text_file.txt.zst)  

real    0m0.012s
user    0m0.000s
sys     0m0.007s

zaheer@localhost:~/learn-linux/compression> time zstd -d executable_file.exe.zst
executable_file.exe.zst: 5296128 bytes                                         

real    0m0.088s
user    0m0.010s
sys     0m0.069s

zaheer@localhost:~/learn-linux/compression> time zstd -d html_file.html.zst
html_file.html.zst  : 289570 bytes                                             

real    0m0.011s
user    0m0.007s
sys     0m0.000s
zaheer@localhost:~/learn-linux/compression> time zstd -d image_file.tif.zst
image_file.tif.zst  : 12603504 bytes                                           

real    0m0.071s
user    0m0.010s
sys     0m0.065s
zaheer@localhost:~/learn-linux/compression> time zstd -d large_pdf_file.pdf.zst
large_pdf_file.pdf.zst: 1081286 bytes                                          

real    0m0.014s
user    0m0.005s
sys     0m0.010s
zaheer@localhost:~/learn-linux/compression> time zstd -d text_file.txt.zst
text_file.txt.zst   : 55191 bytes                                              

real    0m0.005s
user    0m0.004s
sys     0m0.000s


zaheer@localhost:~/learn-linux/compression> time ./huffcode -i executable_file.exe -o executable_file.exe.huff -c

real    0m0.504s
user    0m0.171s
sys     0m0.280s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i html_file.html -o html_file.html.huff -c

real    0m0.030s
user    0m0.016s
sys     0m0.008s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i image_file.tif -o image_file.tif.huff -c

real    0m0.983s
user    0m0.393s
sys     0m0.583s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i large_pdf_file.pdf -o large_pdf_file.pdf.huff -c

real    0m0.103s
user    0m0.046s
sys     0m0.054s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i text_file.txt -o text_file.txt.huff -c

real    0m0.006s
user    0m0.003s
sys     0m0.003s


zaheer@localhost:~/learn-linux/compression> time ./huffcode -i executable_file.exe.huff -o executable_file.exe -d

real    0m0.564s
user    0m0.149s
sys     0m0.335s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i html_file.html.huff -o html_file.html -d

real    0m0.036s
user    0m0.000s
sys     0m0.028s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i image_file.tif.huff -o image_file.tif -d

real    0m0.919s
user    0m0.380s
sys     0m0.450s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i large_pdf_file.pdf.huff -o large_pdf_file.pdf -d

real    0m0.148s
user    0m0.060s
sys     0m0.069s
zaheer@localhost:~/learn-linux/compression> time ./huffcode -i text_file.txt.huff -o text_file.txt -d

real    0m0.008s
user    0m0.003s
sys     0m0.004s

Sure, here is the table with the columns: filename, algorithm, compression time, and decompression time.

| Filename            | Algorithm | Compression Time | Decompression Time |
|---------------------|-----------|------------------|--------------------|
| executable_file.exe | gzip      | 0m0.436s         | 0m0.097s           |
| html_file.html      | gzip      | 0m0.011s         | 0m0.017s           |
| image_file.tif      | gzip      | 0m0.536s         | 0m0.134s           |
| large_pdf_file.pdf  | gzip      | 0m0.064s         | 0m0.028s           |
| text_file.txt       | gzip      | 0m0.012s         | 0m0.015s           |
| executable_file.exe | zstd      | 0m0.176s         | 0m0.088s           |
| html_file.html      | zstd      | 0m0.042s         | 0m0.011s           |
| image_file.tif      | zstd      | 0m0.093s         | 0m0.071s           |
| large_pdf_file.pdf  | zstd      | 0m0.036s         | 0m0.014s           |
| text_file.txt       | zstd      | 0m0.012s         | 0m0.005s           |
| executable_file.exe | huffcode  | 0m0.504s         | 0m0.564s           |
| html_file.html      | huffcode  | 0m0.030s         | 0m0.036s           |
| image_file.tif      | huffcode  | 0m0.983s         | 0m0.919s           |
| large_pdf_file.pdf  | huffcode  | 0m0.103s         | 0m0.148s           |
| text_file.txt       | huffcode  | 0m0.006s         | 0m0.008s           |

Note: The `zstd` decompression time for `executable_file.exe` is not available in the provided data.
