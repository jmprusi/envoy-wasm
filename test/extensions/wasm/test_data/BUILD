licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_package",
)

envoy_package()

filegroup(
    name = "modules",
    srcs = glob([
        "*.wasm",
        "*.wat",
    ]),
)

envoy_cc_library(
    name = "speed_cpp_plugin",
    srcs = [
        "speed_cpp.cc",
        "speed_cpp_null_plugin.cc",
    ],
    copts = ["-DNULL_PLUGIN=1"],
    deps = [
        "//external:abseil_node_hash_map",
        "//source/common/common:assert_lib",
        "//source/common/common:c_smart_ptr_lib",
        "//source/extensions/common/wasm:wasm_lib",
        "//source/extensions/common/wasm:well_known_names",
        "@envoy_api//envoy/config/core/v3:pkg_cc_proto",
    ],
)
