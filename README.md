# Mi chefdk

Este repo tiene chedfk con soporte de git. Mi idea es usarlo a través de un
shell script wrapper como el siguiente:

```bash
#!/bin/bash

set -eo pipefail

if [ $( echo $PWD | grep -q ^$HOME ) ]; then
  EXTRA=""
else
  EXTRA="-v $PWD:$PWD "
fi

docker run --rm -it \
  -v $HOME:$HOME \
  $EXTRA \
  -v /etc/passwd:/etc/passwd:ro \
  -v /etc/group:/etc/group:ro \
  -u $(id -u):$(id -g) \
  -w $PWD chrodriguez/chefdk $@
```

Luego, es posible utilizar el comando de la siguiente forma:

```
chef-docker berks install
chef docker chef generate cookbook prueba
```


