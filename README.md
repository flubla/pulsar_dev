docker run -it -p 6650:6650 -p 8585:8080 -v /var/run/docker.sock:/var/run/docker.sock --mount source=pulsardata,target=/pulsar/data --mount source=pulsarconf,target=/pulsar/conf apachepulsar/pulsar:2.10.4 bin/pulsar standalone

cd download
curl -O https://github.com/apache/pulsar/blob/master/pulsar-functions/python-examples/wordcount_function.py
cd ..
./bin/pulsar-admin functions localrun \
    --classname wordcount_function.WordCountFunction \
    --/pulsar/download/wordcount_function.py \
    --inputs persistent://public/default/wordcount-topic \
    --output persistent://public/default/test-1 \
    --tenant public \
    --namespace default \
    --name PythonFunction