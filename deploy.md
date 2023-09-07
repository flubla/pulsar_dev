https://pulsar.apache.org/docs/3.1.x/functions-package-python/

In this example, when you write a Python function, you need to inherit the Function class and implement the process() method.

process() mainly has two parameters:

input represents your input.

context represents an interface exposed by the Pulsar Function. You can get the attributes in the Python function based on the provided context object.

Install a Python client. The implementation of a Python function depends on the Python client.

pip install pulsar-client==2.10.2

And install protobuf tools to generate the proto files:

pip install 'protobuf==3.20.*'

Copy the Python function file to the Pulsar image.

3f0420eecc9d   apachepulsar/pulsar:2.10.4   "bin/pulsar standalo…"   2 days ago   Up 17 minutes   0.0.0.0:6650->6650/tcp, 0.0.0.0:8585->8080/tcp   eager_faraday

docker exec -it 3f0420eecc9d /bin/bash
docker cp "C:\Users\kevin\Documents\GitHub\zaidanseiko\3idetic_pulsar\pulsar_function_examples\wordcount_function.py" 3f0420eecc9d:/pulsar
wordcount_function.py
Run the Python function using the following command.

I have no name!@3f0420eecc9d:/pulsar$ ./bin/pulsar-admin topics list public/default

The following log indicates that the Python function starts successfully.

 ...
 07:55:03.724 [main] INFO  org.apache.pulsar.functions.runtime.ProcessRuntime - Started process successfully
 ...