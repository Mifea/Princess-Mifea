# Princess-Mifea
2018/9/26 assignment1
TASK1:annotate running scripts (website edition)
less -S 1.gtf | head  #显示1.gtf文件前10行. less--does not have to read the entire input file before starting, so with large input files it starts up faster than text editors like vi. -S--chop-long-lines. head--Print the first 10 lines of each FILE to standard output.  With more than one FILE, precede each with a header giving the file name. With no FILE, or when FILE is -, read standard input.
UPDATED EDITION OF ASSIGNMENT1
TASK1--解释gtf/gff文件中第4、5列（$4,$5)代表什么，exon长度应该是$5-$4+1还是$5-$4？
  $4代表该基因或转录本在参考序列的起始位置，$5代表该基因或转录本在参考序列的终止位置。exon长度为$5-$4+1。
TASK2--列出 XI 号染色体上的后 10 个 CDS （按照终止位置的基因组坐标）。
Command--cat 1.gtf | awk '$1 =="XI"' |awk '$3 =="CDS"' | cut -f 5 | tail
RESULT   
632798
635179
638283
639968
642501
649862
656733
657753
660464
663286
TASK3--统计 IV 号染色体上各类 feature （1.gtf文件的第3列，同时考虑第2列） 的数目，并按升序排列
Command--grep -v ^# 1.gtf |awk '$1 =="IV"'| cut -f 3 | sort | uniq -c | sort -k 1 -n
RESULT
    853 start_codon
    853 stop_codon
    886 gene
    886 transcript
    895 CDS
    933 exon
