# Description:
#   AWS C EVENT STREAM

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_library(
    name = "aws-c-event-stream",
    srcs = glob([
        "source/*.c",
    ]),
    hdrs = glob([
        "include/aws/event-stream/*.h",
        "include/aws/event-stream/private/*.h",
    ]),
    includes = [
        "include",
    ],
    deps = [
        "@aws-c-common",
        "@aws-c-io",
        "@aws-checksums",
    ],
)
