load("@rules_cc//cc:defs.bzl", "cc_library")
load("@rules_pkg//:pkg.bzl", "pkg_tar")

package(default_visibility = ["//visibility:public"])

config_setting(
    name = "use_pre_cxx11_abi",
    values = {
        "define": "abi=pre_cxx11_abi",
    },
)

cc_library(
    name = "conversionctx",
    srcs = [
        "ConversionCtx.cpp",
    ],
    hdrs = [
        "ConversionCtx.h",
    ],
    deps = [
        "//core/ir",
        "//core/util:prelude",
        "@tensorrt//:nvinfer",
    ] + select({
        ":use_pre_cxx11_abi": ["@libtorch_pre_cxx11_abi//:libtorch"],
        "//conditions:default": ["@libtorch"],
    }),
    alwayslink = True,
)

pkg_tar(
    name = "include",
    srcs = ["ConversionCtx.h"],
    package_dir = "core/conversion/conversionctx/",
)
