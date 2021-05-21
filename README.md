# statspack_visual

# snaphost script

#!/bin/bash

for i in `seq $1 $2`; do. 
  esnap=$i.  
  bsnap=$((i-1)).  

sqlplus "/ as sysdba" << !
define report_name=sp_${bsnap}_${esnap}.txt
define begin_snap=${bsnap}
define end_snap=${esnap}
@?/rdbms/admin/spreport
exit
!

done

##example 
$ sh gen.sh 13427 13860


# Python 3.7 이용
sudo wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
sudo tar xzf Python-3.7.3.tgz
cd Python-3.7.3 
sudo ./configure --enable-optimizations
sudo make altinstall
python3.7 statspack_analyzer.py /root/stat/ txt
