**changelog:**
	
** ESP 6.2 -- initial release **

* the deployment files for version 6.2.x of ESP may be found under the v6.2.2 TAG.

** ESP 7.1 **	

* an opensource postgres DB is used for client storage needs: Studio, Streamviewer, ESM and ESP Metering. A persitent volume is required for the storage needs of the postgres DB.
* the filebrowser and individual ESP projects only require a persisten volume if testing with csv files.
* each service and project no longer get a unique host via ingress for access. A single host of the form: <tenant>.<domain> is used to access all <tenant> services. 
 
path based ingress:
```
  Project X    --   <namespace>.sas.com/SASEventStreamProcessing/X
  Metering     --   <namespace>.sas.com/SASEventStreamProcessingMetering
  Studio       --   <namespace>.sas.com/SASEventStreamProcessingStudio
  Streamviewer --   <namespace>.sas.com/SASEventStreamProcessingStreamviewer
  ESM          --   <namespace>.sas.com/SASEventStreamManager
  FileBrowser  --   <namespace>.sas.com/files
```

* Multi user mode implemented with a external UAA server. The multiuser deployment comes with TLS enabled by default.

* Testing has been done with the following thord party components:

```
ghcr.io/skolodzieski/postgres             12.5
ghcr.io/skolodzieski/uaa                  74.29.0
ghcr.io/skolodzieski/uaac                 3.2.0
ghcr.io/skolodzieski/busybox              latest
ghcr.io/skolodzieski/filebrowser          latest
```
