When I tried using the standard 64 bit images there was some issue with sox playing back flac files at 96KHz / 24 bit resolution. So I tried 32 bit 
and it works, hence I created this, my first docker image.

It was started with gfjardim / logitechmediaserver image

    docker run -d --rm=true \
      -p 3483:3483/tcp \
      -p 9000:9000/tcp \
      -p 9090:9090/tcp \
      -v "<yourconfigdir>":"/config":rw \
      -v "<yourmusicdir>":"/cmusic":ro \
      -v "/etc/localtime":"/etc/localtime":ro \
      barrymac/slim32

