# Copyright 2017-present The Material Components for iOS Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
# implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//:material_components_ios.bzl",
     "mdc_public_objc_library",
     "mdc_objc_library")
load("@build_bazel_rules_apple//apple:ios.bzl", "ios_unit_test")
load("@build_bazel_rules_apple//apple:swift.bzl", "swift_library")

licenses(["notice"])  # Apache 2.0

mdc_public_objc_library(
    name = "ButtonBar",
    sdk_frameworks = [
        "QuartzCore",
        "UIKit",
    ],
    deps = [
        "//components/Buttons",
        "@material_internationalization_ios//:MDFInternationalization",
    ],
)

mdc_objc_library(
    name = "ColorThemer",
    srcs = native.glob(["src/ColorThemer/*.m"]),
    hdrs = native.glob(["src/ColorThemer/*.h"]),
    includes = ["src/ColorThemer"],
    sdk_frameworks = [
        "UIKit",
    ],
    deps = [
        ":ButtonBar",
        "//components/NavigationBar",
        "//components/Themes",
    ],
    visibility = ["//visibility:public"],
)

mdc_objc_library(
    name = "private",
    hdrs = native.glob(["src/private/*.h"]),
    includes = ["src/private"],
    visibility = ["//visibility:private"],
)

mdc_objc_library(
    name = "unit_test_sources",
    testonly = 1,
    srcs = native.glob([
        "tests/unit/*.m",
        "tests/unit/*.h",
    ]),
    sdk_frameworks = [
        "UIKit",
        "XCTest",
    ],
    deps = [
        ":ButtonBar",
        ":ColorThemer",
        ":private",
    ],
    visibility = ["//visibility:private"],
)

swift_library(
    name = "unit_test_swift_sources",
    srcs = native.glob(["tests/unit/*.swift"]),
    deps = [
        ":ButtonBar",
        ":ColorThemer",
        ":private",
    ],
    visibility = ["//visibility:private"],
)

ios_unit_test(
    name = "unit_tests",
    deps = [
      ":unit_test_sources",
      ":unit_test_swift_sources",
    ],
    minimum_os_version = "8.0",
    visibility = ["//visibility:private"],
)