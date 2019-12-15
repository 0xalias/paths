# paths

* [api](api.txt) - common ReST API paths.
* [jenkins](jenkins.txt)
* [springboot](springboot.txt) - paths specific to SpringBoot versions 1.x and 2.x. Check port 8080 and 8081. It may also be necessary to include the following request header: `-H 'Accept: application/json'`
* [tomcat](tomcat.txt)

## usage

First, verify domains respond on specific ports and schemes using `httprobe` (results will be saved to `httprobe-results`):

    ```cat domains | httprobe -p http:8081 | tee httprobe-results```

where `domains` file looks like:

```
google.com
yahoo.com
```

Second, use the results of `httprobe` as the `hostsFile` argument for `meg` (results will be saved to `meg-results` dir):

    ```meg -c 20 -d 1000 ./jenkins.txt ./httprobe-results ./meg-results```

