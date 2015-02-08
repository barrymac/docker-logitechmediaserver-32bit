When I tried using the standard 64 bit images there was some issue with sox playing back flac files at 96KHz / 24 bit resolution. So I tried 32 bit 
and it works, hence I created this, my first docker image.



    docker run -d --rm=true \
      -p 3483:3483/tcp \
      -p 9000:9000/tcp \
      -p 9090:9090/tcp \
      -v "<yourconfigdir>":"/config":rw \
      -v "<yourmusicdir>":"/cmusic":ro \
      -v "/etc/localtime":"/etc/localtime":ro \
      barrymac/slim32

To run with a mysql backend you can link to an existing mysql docker container and replace the database config with the 
following in the server.prefs that are in <yourconfigdir>/prefs 

    dbhighmem: 0
    dbpassword: mysql
    dbsource: dbi:mysql:hostname=mysql;port=3306;database=slimserver
    dbtype: MySQL
    dbusername: root


    docker run -d --rm=true \
      -p 3483:3483/tcp \
      -p 9000:9000/tcp \
      -p 9090:9090/tcp \
      -v "<yourconfigdir>":"/config":rw \
      -v "<yourmusicdir>":"/cmusic":ro \
      -v "/etc/localtime":"/etc/localtime":ro \
      --link <yourmysqlhost>
      barrymac/slim32


It was inspired by gfjardim / logitechmediaserver image
