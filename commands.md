
for i in `ls -1 *.log` ; do tar -zcvf $i.tgz $i; if [ "$?" = "0" ] ; then echo "$i Deleted";rm -fr $i;fi  ; done

for i in `ls -1 *.war` ; do tar -zcvf $i.02162017.tgz $i; done    << back up files

# # # # # Filled Filesystems # # # # #
Finding large files works in AIX, Unix and Linux. 
find / -type f -size +10000 -exec ls -lrt {} \; | sort -n +4

You can change "/" or "." or "/home" ....

Use the -xdev option of find so as not to traverse devices...
find / -xdev -type f -size +10000 -print | xargs du -ka | sort -rn

du -sm ./* | sort -n  >>  shows sizes of everything in directory (in MB), subdirectories show their total size
find . -type f | xargs ls -lS | head -n 10   >>   Find top 10 file space hoggers...
du -a . | sort -nr | head   >>   Find top directory space hoggers...
find . -xdev -size +`echo 1024*1024 | bc`c -ls   >>   Find all files larger than 1 MB
find . -xdev -size +`echo 1024*1024*40 | bc`c -ls    >>  Find all files larger than 40 MB
find . -xdev -size +`echo 1024*1024*1024 | bc`c -ls   >>  Find all files larger than 1 GB
find . -type d -ctime +90 >>   Find directories older than 90 days
find . -type d -ctime +30 >>   Find directories older than 30 days
find . -xdev -mmin -60 -ls   >>   Find all files modified in the last 60 minutes (mmin is minutes)
find . -xdev -mtime -5 -ls   >>   Find all files modified in the last 5 days (mtime is days)
du -s <directory>  >>  Find size of directory in mb
du -sh <directory>  >>  Find size of directory in gb
find <path> -size  0 -print0 |xargs -0 rm  >>  Removes all empty files in a path
Removes a specific file:
if [ ! -s /tmp/foo ] ; then
  rm /tmp/foo
fi
du -g /home | sort -n -r | grep -v wsadmin | more

# # # # #  Memory  # # # # #
CPU & Memory
     /usr/loca/tools/nmon ( l=cpu m=memory c=cpu h=help )
     topas


# # # #  Processes  # # # # #
ps aux |grep -v root  //** (determin pid's using to much memory or cpu)
ps -ef | grep CL01RoyalPRD01  (see if process exists)
kill -9 proccessID
kill -3 generate heapdump file
netstat -na | grep 13040 
ps -ef | grep -i wsadmin | grep WebSphere | grep -v splunk | awk '{print $2}' | xargs kill -9 - 
Kills all ASR WebSphere Process - excluding IHS 


# # # #  Find # # # #  
find /var/mqm/errors/*.TXT -mtime +10 -exec ls -ltr {} \; >> Above command will find files which are 10 days or older and list them. <<
find /var/mqm/errors/*.TXT -mtime +10 -exec rm {} \; >> will remove files which are 10 days or older <<
find . -name *.conf -exec grep -l "ErrorDocument 400 /errors/error.htm" {} \; (find string in .conf searching from root)
find . -name *.xml -exec grep -l "PRD1B" {} \;
find . -name <filename> 2>/dev/null  (find files but don't display files that cannot read)
cat /dev/null | tee fileABC fileXYZ
find . -name SystemOut.log |xargs grep -i "hung" |wc -l ( find hung in all SystemOut.logs wc -l counts how many)
find . -xdev -type f -size +25600 -ls  (find files larger than 25600 byes)
find /apps/IHS/logs/ -iname ".*" -maxdepth 1 -type f (find hidden files)
grep jdbc/ SystemOut* ( find jdbc connection errors related to SQL servers )
grep hung SystemOut.log
grep "e-bus" SystemOut.log
find . ! -name . -type d -mtime +3   {} \; >> Find files older than 3 days
find . ! -name . -type d -mtime -3   {} \; >> Find files less than 3 days old
ps -ef | grep /apps/IHS/v85/RoyalWeb1 | grep PRD1A   >> Find IHS start times

# # # #  TimeStamps # # # #  
touch -t 201205101024 filename (changes timestamp to 05/10/2012 10:24am)

# # # #  Space volume info # # # #  
du -g | tail   - See what is taking up the most space
tail -f *  - tail all logs simultaneously
lsvg appls_vg - Check Volume Info 
df -k or df -g - Check space 
du -ks <ear name>  -  check size of ear file
while true; do ll GBL1*; sleep 10; done
while true; do ls -latr; sleep 10; done
while true; do ls -latr CEL*; sleep 10; done
while true; do ls -latr GBL*; sleep 10; done
while true; do grep e-bus SystemOut.log; sleep 10; done

# # # #  Versions # # # #  
java -version 2>&1 | head -n 1 | cut -d'"' -f2  >> Java version

# # # #  cron # # # #  
crontab -l (list)
crontab -e (edit)

# # # #  Tar / Extract Tar # # # #  
tar -tvf (see what is in a tar file)
tar -xvf <path>/tarfile.tar (extract content of tar file from directory where you want to extract to)
tar -xf /opt/splunk/splunkforwarder-6.6.2-4b804538c686-Linux-x86_64.tgz -C /opt/splunk
tar cvf  file.tar *.*       ( create tar file )

# # # #  Networking # # # #  
netstat -na | grep <port#>
lsof -i :<port>
nc -zv <ip> <port>

# # # #  Copy / Directory # # # #  
cat /dev/null > <filename>
chown -R <ID>

# # # # Login / Sudo # # # #
sudo su - <id>
sudo -l

# # # # Unix Admin Cmds # # # #
awk -F: '{print $5"|"$1"|"$3}' /etc/passwd    - get list of users and groups
lsuser -a account_locked unsuccessful_login_count wsadmin  //*** see if user id is locked

# # # #   MQ   # # # #
dspmq - displays above list
strmqm <queuename> - starts queue
endmqm <queuename> - stops queue
runmqsc ( to issue commands to a qmanager )

# # # # ZIP & UNZIP # # # #
gzip filename	----zip a file
gzip -d filename   ----unzip a .gz file
unzip -l filname   ----file contents of zip file

# # # # LOAD # # # #
lparstat -I << CPU Busy & CPU Used
lparstat -i << Server Config Information
lparstat 4 << Live Reporting - %entc = Closer to 1000 the more choked

# # # #   Domain Groups   # # # #
net user <ID> /domain      << List user domain groups
net group <group> /domain	<< List users in a domain group

# # # #   WireShark   # # # #
ip.addr == 	<< filter by IP
ip.src == 	<< filter by Source IP
ip.dst == 	<< filter by Destination IP
tcp.port == 443		<< filter by TCP port 443
udp.port ==		<< filter by UDP port
dns and http	<< filter for dns & http calls only
dns or http	<< filter for dns or http calls only
tcp.analysis.flags	<< tcp issues
!(arp or dns or icmp)	<< ! means remove
tcp.stream eq 32
udp contains akamai
tcp contains facebook
http.request
http.response.code == 302
tcp.flags.syn == 1 //syn attack?

https://origin-secure.new.espresso.cruisingpower.com/SecureLogin.do;jsessionid=010301PPA

# # # # # SPLUNK # # # # #
index=_internal source=*license_usage.log | stats sum(b) by s,st,h,i << check license_usage.log, & breaks down # of indexed bytes by host, source, and sourcetype, and indexer
index=* earliest=-5m | eval esize=len(_raw) | stats count max(esize) by host, source << value in bytes
crcSalt = <SOURCE>

Installations:
sudo yum install telnet	<<install telnet
yum whatprovides '*/jmap'
yum whatprovides '*/jstack'

# # # # # vi editor # # # # #
:%s/word1/word2   <<  replace
