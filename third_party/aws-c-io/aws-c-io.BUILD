# Description:
#   AWS C IO

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_library(
    name = "aws-c-io",
    srcs = glob([
        "source/*.c",
        "source/*.h",
        "source/pkcs11/v2.40/*.h",
    ]) + select({
        "@platforms//os:windows": glob([
            "source/windows/*.c",
        ]),
        "@platforms//os:macos": glob([
            "source/bsd/*.c",
            "source/posix/*.c",
            "source/darwin/*.c",
        ]),
        "//conditions:default": glob([
            "source/linux/*.c",
            "source/posix/*.c",
        ]),
    }),
    hdrs = glob([
        "include/aws/io/*.h",
        "include/aws/io/private/*.h",
    ]),
    defines = [],
    includes = [
        "include",
    ],
    deps = [
        "@aws-c-cal",
        "@aws-c-common",
    ],
)
