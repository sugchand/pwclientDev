# Customized pwclient
====================

A customized version of pwclient to download  multiple patches/patch series
at one go. Very useful when working on various patchsets.

The default pwclient is able to download multiple patches in the following fashion.

```
    ./pwclient get 512548 512588 543129
```

The proposed changes let the user to download the patches with a sequence number instead
of inputting the ids one by one.

## How to use the proposed changes.

* Copy the default pwclientrc file to user home directory for OVS patches.
```
   cp pwclientrc ~/.pwclientrc
```

* Setup the proxy (http_proxy & https_proxy) env if the client is running
  behind network proxy.
  Note :: It is noted that the https_proxy doesnt really work for the pwclient.
  So as a workaround, set the http_proxy value for https_proxy.

* List the required patches using proper filters.

```
    ./pwclient list -n 10
```

```
    ./pwclient list -w "sugesh"
```

  The default project is OVS(openvswitch). To work on patches from different
  project 'dpdk' , mention the project name in the command line.
```
   ./pwclient list -w "sugesh" -p dpdk
```
* Download the patches using the patch sequence number instead of ID.

```
    ./pwclient download -n 2-4,5,1053
```

* Apply the patches from the patch directory to the local repo.
