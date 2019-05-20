# phpStrom 内存不足

Help ——>  VM option

```php
# custom PhpStorm VM options

-Xms256m      //
-Xmx2048m     //
-XX:ReservedCodeCacheSize=350m   //
-XX:+UseCompressedOops
-Dfile.encoding=UTF-8
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-Djdk.http.auth.tunneling.disabledSchemes=""
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-Xverify:none

-XX:ErrorFile=$USER_HOME/java_error_in_phpstorm_%p.log
-XX:HeapDumpPath=$USER_HOME/java_error_in_phpstorm.hprof
```

