# Description:
#   AWS C CHECKSUMS

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_library(
    name = "aws-checksums",
    srcs = glob([
        "source/*.c",
        "source/generic/*.c",
    ]) + select({
        "@platforms//cpu:x86_64": glob([
            "source/intel/asm/*.c",
        ]),
        "//conditions:default": glob([
            "source/arm/*.c",
        ]),
    }),
    hdrs = glob([
        "include/aws/checksums/*.h",
        "include/aws/checksums/private/*.h",
    ]),
    includes = [
        "include",
    ],
    deps = [
        "@aws-c-common",
    ],
)
