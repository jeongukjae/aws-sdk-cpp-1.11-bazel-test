# Description:
#   AWS C CAL

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_library(
    name = "aws-c-cal",
    srcs = glob([
        "source/*.c",
    ]),
    hdrs = glob([
        "include/aws/cal/*.h",
        "include/aws/cal/private/*.h",
    ]),
    defines = [
        "BYO_CRYPTO=1",
    ],
    includes = [
        "include",
    ],
    deps = [
        "@aws-c-common",
        "@boringssl//:crypto",
    ],
)
