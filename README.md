# minio-gcs

Experimental setup using the deprecated minio gateway feature.

- <https://blog.min.io/deprecation-of-the-minio-gateway/>
- <https://github.com/minio/minio/blob/RELEASE.2021-08-25T00-41-18Z/docs/gateway/gcs.md>
- <https://github.com/minio/mc>

Add the following to `~/.mc/config.json`:

```json
{
    "version": "10",
    "aliases": {
        "local": {
            "url": "http://localhost:9000",
            "accessKey": "accesskey",
            "secretKey": "secretkey",
            "api": "S3v4",
            "path": "auto"
        },
        "local2": {
            "url": "http://localhost:9001",
            "accessKey": "accesskey",
            "secretKey": "secretkey",
            "api": "S3v4",
            "path": "auto"
        }
    }
}
```

Then upload some random bytes:

```plaintext
dd if=/dev/random of=random bs=1 count=1M
mc cp random local/gcsgateway/random
```
