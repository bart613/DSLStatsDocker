**Application**

[DSLStats](http://www.s446074245.websitehome.co.uk/downloads.html)

This container starts DSLStats inside a virtual X session. A VNC server is created which you can connect to to interact with DSLStats.

**Usage**
```
docker run -d \
	--name=<container name> \
	--net=bridge \
	-p <vnc port>:5900/tcp \
	-p <web port>:8080/tcp \
	-e "VNC_PASSWORD"="<vnc password>"
	-v <path for DSLStats config files to be stored>:/config \
	-v /etc/localtime:/etc/localtime:ro \
	rossallan/dslstats
```

Please replace all user variables in the above command defined by <> with the correct values.

**Access application**

Connect using a VNC client (for example [VNC for Chrome](https://chrome.google.com/webstore/detail/vnc%C2%AE-viewer-for-google-ch/iabmpiboiopbgfabjmgeedhcmjenhbla?hl=en)) to port 5900 (or the port you configured) to set up DSLstats.

The built in DSLStats web server doesn't work properly. To get that working enable it which will create the necessary files, but ignore the port number setting. This container starts a web server on port 8080 which will serve the DSLStats web pages.

**Example**
```
docker run -d \
	--name=dslstats \
	--net=bridge \
	-p 5900:5900/tcp \
	-p 8080:8080/tcp \
	-e "VNC_PASSWORD"="123456789" \
	-v /mnt/cache/appdata/dslstats:/config \
	-v /etc/localtime:/etc/localtime:ro \
	rossallan/dslstats
```
