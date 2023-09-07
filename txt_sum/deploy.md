bin/pulsar-admin functions create \
  --tenant public \
  --namespace default \
  --name echo \
  --py echo.py \
  --classname echo \
  --inputs persistent://public/default/in \
  --output persistent://public/default/out

