# Description:
#   AWS C++ SDK
#
# Not tested on Windows

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

genrule(
    name = "SDKConfig_h",
    outs = [
        "src/aws-cpp-sdk-core/include/aws/core/SDKConfig.h",
    ],
    cmd = "\n".join([
        "cat <<'EOF' >$@",
        "EOF",
    ]),
)

cc_library(
    name = "core",
    srcs = glob([
        "src/aws-cpp-sdk-core/source/*.cpp",  # AWS_SOURCE
        "src/aws-cpp-sdk-core/source/internal/*.cpp",  # AWS_INTERNAL_SOURCE
        "src/aws-cpp-sdk-core/source/external/tinyxml2/*.cpp",  # AWS_TINYXML2_SOURCE
        "src/aws-cpp-sdk-core/source/external/cjson/*.cpp",  # CJSON_SOURCE
        "src/aws-cpp-sdk-core/source/auth/*.cpp",  # AWS_AUTH_SOURCE
        "src/aws-cpp-sdk-core/source/auth/signer/*.cpp",  # AWS_AUTH_SIGNER_SOURCE
        "src/aws-cpp-sdk-core/source/auth/signer-provider/*.cpp",  # AWS_AUTH_SIGNER_PROVIDER_SOURCE
        "src/aws-cpp-sdk-core/source/auth/bearer-token-provider/*.cpp",  # AWS_AUTH_BEARER_TOKEN_PROVIDER_SOURCE
        "src/aws-cpp-sdk-core/source/client/*.cpp",  # AWS_CLIENT_SOURCE
        "src/aws-cpp-sdk-core/source/monitoring/*.cpp",  # MONITORING_SOURCE
        "src/aws-cpp-sdk-core/source/http/*.cpp",  # HTTP_STANDARD_SOURCE
        "src/aws-cpp-sdk-core/source/http/standard/*.cpp",  # HTTP_CLIENT_SOURCE
        "src/aws-cpp-sdk-core/source/http/curl/*.cpp",  # HTTP_CURL_CLIENT_SOURCE
        "src/aws-cpp-sdk-core/source/config/*.cpp",  # CONFIG_SOURCE
        "src/aws-cpp-sdk-core/source/config/defaults/*.cpp",  # CONFIG_DEFAULTS_SOURCE
        "src/aws-cpp-sdk-core/source/endpoint/*.cpp",  # ENDPOINT_SOURCE
        "src/aws-cpp-sdk-core/source/endpoint/internal/*.cpp",  # ENDPOINT_INTERNAL_SOURCE
        "src/aws-cpp-sdk-core/source/utils/*.cpp",  # UTILS_SOURCE
        "src/aws-cpp-sdk-core/source/utils/base64/*.cpp",  # UTILS_BASE64_SOURCE
        "src/aws-cpp-sdk-core/source/utils/threading/*.cpp",  # UTILS_THREADING_SOURCE
        "src/aws-cpp-sdk-core/source/utils/event/*.cpp",  # UTILS_EVENT_SOURCE
        "src/aws-cpp-sdk-core/source/utils/json/*.cpp",  # UTILS_JSON_SOURCE
        "src/aws-cpp-sdk-core/source/utils/xml/*.cpp",  # UTILS_XML_SOURCE
        "src/aws-cpp-sdk-core/source/utils/stream/*.cpp",  # UTILS_STREAM_SOURCE
        "src/aws-cpp-sdk-core/source/utils/logging/*.cpp",  # UTILS_LOGGING_SOURCE
        "src/aws-cpp-sdk-core/source/utils/memory/*.cpp",  # UTILS_MEMORY_SOURCE
        "src/aws-cpp-sdk-core/source/utils/component-registry/*.cpp",  # UTILS_COMPONENT_REGISTRY_SOURCE
        "src/aws-cpp-sdk-core/source/utils/memory/stl/*.cpp",  # UTILS_MEMORY_STL_SOURCE
        "src/aws-cpp-sdk-core/source/utils/crypto/*.cpp",  # UTILS_CRYPTO_SOURCE
        "src/aws-cpp-sdk-core/source/utils/crypto/factory/*.cpp",  # UTILS_CRYPTO_FACTORY_SOURCE
        "src/aws-cpp-sdk-core/source/utils/crypto/openssl/*.cpp",  # UTILS_CRYPTO_OPENSSL_SOURCE
        "src/aws-cpp-sdk-core/source/smithy/*.cpp",  # SMITHY_SOURCE
        "src/aws-cpp-sdk-core/source/smithy/tracing/*.cpp",  # SMITHY_TRACING_SOURCE
    ]) + select({
        "@bazel_tools//src/conditions:windows": glob([
            "src/aws-cpp-sdk-core/aws-cpp-sdk-core/source/net/windows/*.cpp",  # NET_SOURCE
            "src/aws-cpp-sdk-core/aws-cpp-sdk-core/source/platform/windows/*.cpp",  # PLATFORM_WINDOWS_SOURCE
        ]),
        "//conditions:default": glob([
            "src/aws-cpp-sdk-core/source/net/linux-shared/*.cpp",  # NET_SOURCE
            "src/aws-cpp-sdk-core/source/platform/linux-shared/*.cpp",  # PLATFORM_LINUX_SHARED_SOURCE
        ]),
    }),
    hdrs = [
        "src/aws-cpp-sdk-core/include/aws/core/SDKConfig.h",
    ] + glob([
        "src/aws-cpp-sdk-core/include/aws/core/*.h",  # AWS_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/auth/*.h",  # AWS_AUTH_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/auth/signer/*.h",  # AWS_AUTH_SIGNER_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/auth/signer-provider/*.h",  # AWS_AUTH_SIGNER_PROVIDER_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/auth/bearer-token-provider/*.h",  # AWS_AUTH_BEARER_TOKEN_PROVIDER_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/client/*.h",  # AWS_CLIENT_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/internal/*.h",  # AWS_INTERNAL_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/net/*.h",  # NET_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/http/*.h",  # HTTP_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/http/standard/*.h",  # HTTP_STANDARD_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/config/*.h",  # CONFIG_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/config/defaults/*.h",  # CONFIG_DEFAULTS_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/endpoint/*.h",  # ENDPOINT_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/endpoint/internal/*.h",  # ENDPOINT_INTERNAL_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/monitoring/*.h",  # MONITORING_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/platform/*.h",  # PLATFORM_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/*.h",  # UTILS_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/event/*.h",  # UTILS_EVENT_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/base64/*.h",  # UTILS_BASE64_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/crypto/*.h",  # UTILS_CRYPTO_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/json/*.h",  # UTILS_JSON_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/threading/*.h",  # UTILS_THREADING_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/xml/*.h",  # UTILS_XML_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/logging/*.h",  # UTILS_LOGGING_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/memory/*.h",  # UTILS_MEMORY_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/component-registry/*.h",  # UTILS_COMPONENT_REGISTRY_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/memory/stl/*.h",  # UTILS_STL_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/stream/*.h",  # UTILS_STREAM_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/ratelimiter/*.h",  # UTILS_RATE_LIMITER_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/external/cjson/*.h",  # CJSON_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/external/tinyxml2/*.h",  # TINYXML2_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/http/curl/*.h",  # HTTP_CURL_CLIENT_HEADERS
        "src/aws-cpp-sdk-core/include/aws/core/utils/crypto/openssl/*.h",  # UTILS_CRYPTO_OPENSSL_HEADERS
        "src/aws-cpp-sdk-core/include/smithy/*.h",  # SMITHY_HEADERS
        "src/aws-cpp-sdk-core/include/smithy/tracing/*.h",  # SMITHY_TRACING_HEADERS
    ]),
    defines = [
        'AWS_SDK_VERSION_STRING=\\"1.11.143\\"',
        "AWS_SDK_VERSION_MAJOR=1",
        "AWS_SDK_VERSION_MINOR=11",
        "AWS_SDK_VERSION_PATCH=143",
        "ENABLE_OPENSSL_ENCRYPTION=1",
        "ENABLE_CURL_CLIENT=1",
        "OPENSSL_IS_BORINGSSL=1",
    ] + select({
        "@bazel_tools//src/conditions:windows": [
            "PLATFORM_WINDOWS",
            "WIN32_LEAN_AND_MEAN",
        ],
        "//conditions:default": [
            "PLATFORM_LINUX",
        ],
    }),
    includes = [
        "src/aws-cpp-sdk-core/include",
    ],
    linkopts = select({
        "@bazel_tools//src/conditions:windows": [
            "-DEFAULTLIB:userenv.lib",
            "-DEFAULTLIB:version.lib",
        ],
        "//conditions:default": [],
    }),
    deps = [
        "@aws-c-event-stream",
        "@aws-crt-cpp",
        "@boringssl//:crypto",
        "@boringssl//:ssl",
        "@curl",
    ],
)

cc_library(
    name = "s3",
    srcs = glob([
        "generated/src/aws-cpp-sdk-s3/source/*.cpp",  # AWS_S3_SOURCE
        "generated/src/aws-cpp-sdk-s3/source/model/*.cpp",  # AWS_S3_MODEL_SOURCE
    ]),
    hdrs = glob([
        "generated/src/aws-cpp-sdk-s3/include/aws/s3/*.h",  # AWS_S3_HEADERS
        "generated/src/aws-cpp-sdk-s3/include/aws/s3/model/*.h",  # AWS_S3_MODEL_HEADERS
    ]),
    includes = [
        "generated/src/aws-cpp-sdk-s3/include",
    ],
    deps = [
        ":core",
    ],
)

cc_library(
    name = "transfer",
    srcs = glob([
        "generated/src/aws-cpp-sdk-transfer/source/transfer/*.cpp",  # TRANSFER_SOURCE
    ]),
    hdrs = glob([
        "generated/src/aws-cpp-sdk-transfer/include/aws/transfer/*.h",  # TRANSFER_HEADERS
    ]),
    includes = [
        "generated/src/aws-cpp-sdk-transfer/include",
    ],
    deps = [
        ":core",
        ":s3",
    ],
)
