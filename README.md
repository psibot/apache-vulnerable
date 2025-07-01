# Scan FOR APACHE versions "ZERO-DAY" 

```Apache Version 2.4.49 and 2.4.50 ``` 


# How to use : 

You Will need nuclei ! 

https://github.com/projectdiscovery/nuclei


Check local nuclei install and verify template 

```nuclei  -t apache-vulnerable-versions.yaml -vv ```

You should see 

```[apache-vulnerable-versions] Vulnerable Apache Versions (2.4.49-2.4.50) (@psibot) [high] ```


To scan target : 

```  nuclei --silent  -t apache-vulnerable-versions.yaml -u https://*.*.*.*:port ``` 

To scan targets in a file : 

```  nuclei --silent  -t apache-vulnerable-versions.yaml -l hosts.txt``` 