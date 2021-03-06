# Description:
#   Functions to convert Arrow Tables to/from Example protos.

package(default_visibility = ["//visibility:private"])

licenses(["notice"])

cc_library(
    name = "example_coder",
    srcs = ["example_coder.cc"],
    hdrs = ["example_coder.h"],
    deps = [
        "//tfx_bsl/cc/util:status",
        "//tfx_bsl/cc/util:status_util",
        "@arrow",
        "@com_github_tensorflow_metadata//tensorflow_metadata/proto/v0:cc_metadata_v0_proto_cc",
        "@com_google_absl//absl/container:flat_hash_map",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/types:optional",
        "@org_tensorflow//tensorflow/core:protos_all_cc",
    ],
)

cc_test(
    name = "example_coder_test",
    srcs = ["example_coder_test.cc"],
    deps = [
        ":example_coder",
        "//tfx_bsl/cc/util:status",
        "@arrow",
        "@com_github_tensorflow_metadata//tensorflow_metadata/proto/v0:cc_metadata_v0_proto_cc",
        "@com_google_absl//absl/strings",
        "@com_google_googletest//:gtest_main",
        "@org_tensorflow//tensorflow/core:protos_all_cc",
    ],
)

cc_library(
    name = "example_numpy_decoder",
    srcs = ["example_numpy_decoder.cc"],
    hdrs = ["example_numpy_decoder.h"],
    deps = [
        "//tfx_bsl/cc/util:status",
        "@com_google_absl//absl/strings",
        "@local_config_python//:numpy_headers",
        "@local_config_python//:python_headers",
        "@org_tensorflow//tensorflow/core:protos_all_cc",
    ],
)

cc_library(
    name = "coders_submodule",
    srcs = ["coders_submodule.cc"],
    hdrs = ["coders_submodule.h"],
    copts = [
        "-fexceptions",
    ],
    features = ["-use_header_modules"],
    visibility = [
        "//tfx_bsl/cc:__pkg__",
    ],
    deps = [
        ":example_coder",
        ":example_numpy_decoder",
        "//tfx_bsl/cc/pybind11:absl_casters",
        "//tfx_bsl/cc/pybind11:arrow_casters",
        "//tfx_bsl/cc/util:status",
        "@arrow",
        "@pybind11",
    ],
)
