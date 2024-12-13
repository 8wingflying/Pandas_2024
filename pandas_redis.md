#
- https://redis.io/blog/running-redis-on-google-colab/
- !pip install redis
```python
!pip install redis-server

import redis
import subprocess
import os

# Generate a random port number
import random
redis_port = random.randint(1024, 65535) 

# Start the redis-server process with the random port
redis_process = subprocess.Popen(['redis-server', '--port', str(redis_port), '--bind', '127.0.0.1'], stdout=subprocess.PIPE, stderr=subprocess.PIPE)

# Wait for the server to start
import time
time.sleep(2)  # Give Redis some time to start up

# Connect to Redis using the random port
client = redis.Redis(host='localhost', port=redis_port)

# Test the connection
try:
    client.ping()
    print("Successfully connected to Redis!")
except redis.exceptions.ConnectionError as e:
    print(f"Error connecting to Redis: {e}")

# Optional: When done, shut down the Redis server.
#redis_process.terminate()
```
```
ERROR: Could not find a version that satisfies the requirement redis-server (from versions: none)
ERROR: No matching distribution found for redis-server
Successfully connected to Redis!
```
```python
client.set('foo', 'bar')
client.get('foo')
```
```
!ps -aux
```
```
CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1076     8 ?        Ss   11:52   0:00 /sbin/docker-init -- /datalab/run
root           6  0.1  0.5 913208 72188 ?        Sl   11:52   0:08 /tools/node/bin/node /datalab/web
root          15  0.0  0.0   7376  3540 ?        S    11:52   0:04 /bin/bash -e /usr/local/colab/bin
root          19  0.0  0.0   7376  1964 ?        S    11:52   0:00 /bin/bash -e /datalab/run.sh
root          22  0.0  0.1 1237160 14236 ?       Sl   11:52   0:02 /usr/colab/bin/kernel_manager_pro
root          26  0.0  0.0   5808  1048 ?        Ss   11:52   0:00 tail -n +0 -F /root/.config/Googl
root          44  0.0  0.0   5808  1024 ?        Ss   11:52   0:00 tail -n +0 -F /root/.config/Googl
root          68  0.2  0.0      0     0 ?        Z    11:52   0:16 [python3] <defunct>
root          69  0.0  0.4  72692 57256 ?        S    11:52   0:01 python3 /usr/local/bin/colab-file
root          86  0.1  0.8 364284 119020 ?       Sl   11:52   0:08 /usr/bin/python3 /usr/local/bin/j
root          87  0.1  0.0 1230268 9664 ?        Sl   11:52   0:08 /usr/local/bin/dap_multiplexer --
root         567  0.6  2.2 1482336 303424 ?      Ssl  11:54   0:45 /usr/bin/python3 -m colab_kernel_
root         614  0.2  0.1 543052 19060 ?        Sl   11:54   0:19 /usr/bin/python3 /usr/local/lib/p
root       25329  0.0  0.2 102644 27304 ?        Sl   13:37   0:00 python3 -m colabxterm --port 1000
root       25331  0.0  0.0   7640  4296 pts/0    Ss   13:37   0:00 /bin/bash
root       25880  0.0  0.0  19804 12104 pts/0    S+   13:38   0:00 python3
root       28288  0.1  0.0  48784 10684 ?        Sl   13:48   0:00 redis-server 127.0.0.1:44247
root       28301  0.0  0.1 1240340 18944 ?       Sl   13:48   0:00 /usr/colab/bin/language_service -
root       28311  6.1  3.6 1202284 479396 ?      Sl   13:48   0:34 node /datalab/web/pyright/pyright
root       30594  0.0  0.0   5776  1056 ?        S    13:57   0:00 sleep 1
root       30595  0.0  0.0  10076  1608 ?        R    13:57   0:00 ps -aux
```
```python
import redis
client = redis.Redis(host = 'localhost', port=44247)
  
client.ping()
```
- https://geek-docs.com/pandas/pandas-questions/383_pandas_how_to_setget_pandas_dataframes_into_redis_using_pyarrow.html
```
!pip install pyarrow

```
