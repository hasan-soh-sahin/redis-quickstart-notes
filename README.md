# redis-quickstart-notes

#download & un-tar
wget http://download.redis.io/releases/redis-6.0.5.tar.gz
tar zxvf redis-5.0.9.tar.gz

#conf
vim sentinel.conf
bind 127.0.0.1 <host>
port 26379
daemonize no
pidfile /var/run/redis-sentinel.pid
logfile /data/log/redis/redis.log
 
#start server
src/redis-server --protected-mode no

#stop server
ps -ef | grep redis | grep :6379 | awk '{print $2}' | xargs kill

#client
src/redis-cli -h <host> -p 6379
  
--commands
#delete all keys
FLUSHALL

#delete all keys with a pattern e.g. starts with asd:
redis-cli --scan --pattern asd:* | xargs redis-cli unlink

#get all keys
keys *

#get all keys
keys pattern*

#get hash values
hgetall "table:asd"

set aKey aValue
get aKey
