
# Airflow DAGs for my [Podcast Analysis Tool](https://github.com/RyanQuey/java-podcast-processor).
Intended as a proof of concept, to show how to connect Airflow to a data pipeline.

![Airflow UI Screenshot](https://github.com/RyanQuey/airflow-with-podcasts/raw/master/screenshots/airflow/airflow-ui-dag-wide.png)

## Start the server:
`astro dev start` 

View your DAGs at `http://localhost:8080`.

(Watch out, if Zeppelin is running this is the same port so there can be conflict).

## Customize your image
https://www.astronomer.io/docs/customizing-your-image/

### Add OS level dependencies
#### Add stuff to packages.txt
* https://pkgs.alpinelinux.org/packages
* if make changes, just run `astro dev stop && astro dev start` to rebuild
* (these commands run on top of docker compose)
* don't put any comments in that thing, as far as I can tell. requirements.txt can use `#` for comments, not packages.txt

## Project current status:

Setup to connect to Cassandra running on Datastax Enterprise. 

#### Debugging: 
Potentially will get this in the DAG log:

```sh
[2020-06-10 12:20:29,264] {bash_operator.py:115} INFO - Running command: sleep $[ ( $RANDOM % 30 )  + 1 ]s && java -jar /podcast-analysis-tool-0.2.0.jar
[2020-06-10 12:20:29,273] {bash_operator.py:124} INFO - Output:
[2020-06-10 12:20:34,423] {bash_operator.py:128} INFO - Running with options:
[2020-06-10 12:20:35,242] {bash_operator.py:128} INFO - 0    [main] INFO  com.datastax.oss.driver.internal.core.DefaultMavenCoordinates  - DataStax Java driver for Apache Cassandra(R) (com.datastax.oss:java-driver-core) version 4.6.1
[2020-06-10 12:20:36,103] {bash_operator.py:128} INFO - 861  [s0-admin-0] INFO  com.datastax.oss.driver.internal.core.time.Clock  - Using native clock for microsecond precision
[2020-06-10 12:20:36,111] {bash_operator.py:128} INFO - 870  [s0-admin-0] INFO  com.datastax.oss.driver.internal.core.metadata.MetadataManager  - [s0] No contact points provided, defaulting to /127.0.0.1:9042
[2020-06-10 12:20:36,412] {bash_operator.py:128} INFO - 1171 [s0-admin-1] WARN  com.datastax.oss.driver.internal.core.control.ControlConnection  - [s0] Error connecting to Node(endPoint=/127.0.0.1:9042, hostId=null, hashCode=736bcf54), trying next node (ConnectionInitException: [s0|control|connecting...] Protocol initialization request, step 1 (OPTIONS): failed to send request (java.nio.channels.ClosedChannelException))
[2020-06-10 12:20:36,765] {bash_operator.py:132} INFO - Command exited with return code 0
[2020-06-10 12:20:39,113] {logging_mixin.py:112} INFO - [2020-06-10 12:20:39,113] {local_task_job.py:103} INFO - Task exited with return code 0
```

<<<<<<< HEAD
This means everything is set up correctly, but you don't have DSE/Cassandra running on your local node. 

=======
And I think that's good enough for a proof of concept. Stopping there for now

# Released under MIT License

Copyright (c) 2020 Ryan Quey.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
>>>>>>> ad87b75083719332bd3c696230bbc467e6b14ced
