#!/bin/bash

VersaoLinux() {
    /usr/bin/lsb_release -ds
}

CheckUser () {
   USER_ID=$(/usr/bin/id -u)
   
   echo "USER_ID";
   echo $USER_ID
}
 
CheckGCC () {
	echo "**** GCC_run****";
   /usr/bin/gcc -v
}
 
CheckPython() {
	echo "*** python_version ****";
   /usr/bin/python --version
}
 
CheckPerl() {
	echo "**** perl version ***";
   /usr/bin/perl -v
}
CheckSystem() {
 

   # Macete para imprimir saida de funcao dentro do echo
   echo "@@@@@ Linux version @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@";
   echo -e "nn###\033[0;31m Distrubuição:\033[0mt$(VersaoLinux)"
   #echo -e "### Distribuição:t$(VersaoLinux)"
   echo "@@@@ cpu info @@@@@@@@@@@@@@@@@@@@@@@";
   echo -e "nn###\033[0;31m Processador\033[0m"
   cat /proc/cpuinfo | grep "model name"
 
   echo -e "nn###\033[0;31m Memoria\033[0m"
   /usr/bin/free -m
   echo "@@@@ Disc @@@@@@@@@@@@@@@@@@@@@@";	
   echo -e "nn###\033[0;31m Disco\033[0m"
   /bin/df -h
}



if(! route -n)then
 echo "INFORMATION NOT AVALIABLE!"
    exit 1
else
    
	echo "@@@@@@@@@@@@ CURRET VERSIONS @@@@@@@@@@@";    
    VersaoLinux;
    CheckUser;
    CheckSystem;
    CheckPerl;
    CheckPython;
    CheckGCC;
fi

