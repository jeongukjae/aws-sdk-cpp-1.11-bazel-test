# Description:
#   AWS C Common

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

cc_library(
    name = "aws-c-common",
    srcs = glob([
        "source/*.c",
        "source/external/*.c",
        "source/arch/generic/*.c",
    ]) + select({
        "@platforms//os:windows": glob([
            "source/windows/*.c",
        ]),
        "//conditions:default": glob([
            "source/posix/*.c",
        ]),
    }) + select({
        "@platforms//cpu:x86_64": [
            "source/arch/intel/cpuid.c",
        ] + glob([
            "source/arch/intel/asm/*.c",
        ]),
        "//conditions:default": glob([
            "source/arch/arm/asm/*.c",
        ]),
    }),
    hdrs = ["include/aws/common/config.h"] + glob([
        "include/aws/common/*.h",
        "include/aws/common/private/*.h",
        "include/aws/common/external/*.h",
    ]),
    defines = [
        "AWS_AFFINITY_METHOD=0",
    ],
    includes = [
        "include",
    ],
    linkopts = select({
        "@platforms//os:macos": [
            "-framework",
            "CoreFoundation",
        ],
        "//conditions:default": [],
    }),
    textual_hdrs = glob([
        "include/**/*.inl",
    ]),
    deps = [],
)

genrule(
    name = "config_h",
    srcs = [
        "include/aws/common/config.h.in",
    ],
    outs = [
        "include/aws/common/config.h",
    ],
    cmd = "sed 's/cmakedefine/undef/g' $< > $@",
)
