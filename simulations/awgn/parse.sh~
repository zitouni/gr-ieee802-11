#!/bin/bash

files=`ls results/*.pcap`
outfile=results/all.csv
rm -f ${outfile}

echo "repetition;Encoding;SNR;received"
echo "repetition;Encoding;snr;received" > ${outfile}

for f in ${files}
do
	repetition=`python -c "print \"${f}\".split(\"_\")[1]"`
	Encoding=`python -c "print \"${f}\".split(\"_\")[2]"`
	SNR=`python -c "print \"${f}\".split(\"_\")[3]"`
	echo "file ${f}  repetition ${repetition}  Encoding ${Encoding}  SNR ${SNR}"
	rcvd=`tshark -r ${f} | wc -l | tr -d " "`
	echo "${repetition};${Encoding};${SNR};${rcvd}"
	echo "${repetition};${Encoding};${SNR};${rcvd}" >> ${outfile}
done
