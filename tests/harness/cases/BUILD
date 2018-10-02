load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")

# gazelle:exclude go
load("@io_bazel_rules_go//go:def.bzl", "go_library")
load(
    "//bazel:pgv_proto_library.bzl",
    "pgv_cc_proto_library",
    "pgv_go_proto_library",
    "pgv_gogo_proto_library",
)

proto_library(
    name = "cases_proto",
    srcs = [
        "bool.proto",
        "bytes.proto",
        "enums.proto",
        "maps.proto",
        "messages.proto",
        "numbers.proto",
        "oneofs.proto",
        "repeated.proto",
        "strings.proto",
        "wkt_any.proto",
        "wkt_duration.proto",
        "wkt_timestamp.proto",
        "wkt_wrappers.proto",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "//tests/harness/cases/other_package:embed_proto",
        "//validate:validate_proto",
        "@com_google_protobuf//:any_proto",
        "@com_google_protobuf//:duration_proto",
        "@com_google_protobuf//:timestamp_proto",
        "@com_google_protobuf//:wrappers_proto",
    ],
)

pgv_go_proto_library(
    name = "go",
    importpath = "github.com/lyft/protoc-gen-validate/tests/harness/cases/go",
    proto = ":cases_proto",
    deps = [
        "//tests/harness/cases/other_package:go",
        "@com_github_golang_protobuf//ptypes:go_default_library_gen",
        "@io_bazel_rules_go//proto/wkt:any_go_proto",
        "@io_bazel_rules_go//proto/wkt:duration_go_proto",
        "@io_bazel_rules_go//proto/wkt:timestamp_go_proto",
        "@io_bazel_rules_go//proto/wkt:wrappers_go_proto",
    ],
)

pgv_gogo_proto_library(
    name = "gogo",
    importpath = "github.com/lyft/protoc-gen-validate/tests/harness/cases/gogo",
    proto = ":cases_proto",
    deps = [
        "//tests/harness/cases/other_package:gogo",
        "@com_github_golang_protobuf//ptypes:go_default_library_gen",
        "@io_bazel_rules_go//proto/wkt:any_go_proto",
        "@io_bazel_rules_go//proto/wkt:duration_go_proto",
        "@io_bazel_rules_go//proto/wkt:timestamp_go_proto",
        "@io_bazel_rules_go//proto/wkt:wrappers_go_proto",
    ],
)

pgv_cc_proto_library(
    name = "cc",
    cc_deps = [
        "//tests/harness/cases/other_package:cc",
    ],
    visibility = ["//tests:__subpackages__"],
    deps = [":cases_proto"],
)
