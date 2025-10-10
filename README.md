  java -Xmx12g -Xms2g -Xmn1g -Xss2m -XX:+UseG1GC \
    -Dfile.encoding=UTF-8 \
    -Dstdout.encoding=UTF-8 \
    -Dstderr.encoding=UTF-8 \
    -cp "./lib/*" \
    com.ibm.arc.lang.driver.CryptoCli \
    --config "cc-optimized-medium-config.json"
