Building aws-sdk-cpp 1.11.x with bazel.

Build:

```shell
# Install libcurl.
#
# sudo apt install libcurl4-openssl-dev

bazel run //:s3_client
```
