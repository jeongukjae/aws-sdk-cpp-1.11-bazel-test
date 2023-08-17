# Description:
#   AWS C++ CRT

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

genrule(
    name = "Config_h",
    outs = [
        "include/aws/crt/Config.h",
    ],
    cmd = "\n".join([
        "cat <<'EOF' >$@",
        "#define AWS_CRT_CPP_VERSION \"0.23.0\"",
        "#define AWS_CRT_CPP_VERSION_MAJOR 0",
        "#define AWS_CRT_CPP_VERSION_MINOR 23",
        "#define AWS_CRT_CPP_VERSION_PATCH 0",
        "#define AWS_CRT_CPP_GIT_HASH \"363d09e8a3509f663327d6e8414d0b2e052c815d\"",
        "EOF",
    ]),
)

cc_library(
    name = "aws-crt-cpp",
    srcs = glob([
        "source/*.cpp",  # AWS_CRT_SRC
        "source/auth/*.cpp",  # AWS_CRT_AUTH_SRC
        "source/crypto/*.cpp",  # AWS_CRT_CRYPTO_SRC
        "source/io/*.cpp",  # AWS_CRT_IO_SRC
        "source/iot/*.cpp",  # AWS_CRT_IOT_SRC
        "source/mqtt/*.cpp",  # AWS_CRT_MQTT_SRC
        "source/http/*.cpp",  # AWS_CRT_HTTP_SRC
        "source/endpoints/*.cpp",  # AWS_CRT_ENDPOINTS_SRC
        "source/external/*.cpp",  # AWS_CRT_EXTERNAL_SRC
    ]),
    hdrs = [
        "include/aws/crt/Config.h",
    ] + glob([
        "include/aws/crt/*.h",  # AWS_CRT_HEADERS
        "include/aws/crt/auth/*.h",  # AWS_CRT_AUTH_HEADERS
        "include/aws/crt/crypto/*.h",  # AWS_CRT_CRYPTO_HEADERS
        "include/aws/crt/io/*.h",  # AWS_CRT_IO_HEADERS
        "include/aws/iot/*.h",  # AWS_CRT_IOT_HEADERS
        "include/aws/crt/mqtt/*.h",  # AWS_CRT_MQTT_HEADERS
        "include/aws/crt/http/*.h",  # AWS_CRT_HTTP_HEADERS
        "include/aws/crt/endpoints/*.h",  # AWS_CRT_ENDPOINT_HEADERS
        "include/aws/crt/external/*.h",  # AWS_CRT_EXTERNAL_HEADERS
    ]),
    includes = [
        "include",
    ],
    deps = [
        "@aws-c-auth",
        "@aws-c-common",
        "@aws-c-event-stream",
        "@aws-c-io",
        "@aws-c-mqtt",
        "@aws-c-s3",
    ],
)
