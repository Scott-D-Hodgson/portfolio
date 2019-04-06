---
title: Verify a Checksum
date: 2019-04-06T13:38:46.192Z
---
When downloading packages from the internet, many providers will identify the hashcode value of the binary data.  This allows the download to be verified after download through performing the same hashcode check of the downloaded file.

For example, the Raspbian dowload page identifies the hashcode of `2018-11-13-raspbian-stretch-lite.zip` to be SHA-256: `47ef1b2501d0e5002675a50b6868074e693f78829822eef64f3878487953234d`.

This can be done via the terminal window by using `openssl`.

```
$ openssl sha256 2018-11-13-raspbian-stretch-lite.zip
```

The result of this should be the same hashcode as on the website page.  If they match, the download has not been tampered with.
