# statspack_visual

# snaphost script

#!/bin/bash

for i in `seq $1 $2`; do
  esnap=$i
  bsnap=$((i-1))

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
