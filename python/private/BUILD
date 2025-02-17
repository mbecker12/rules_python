# Copyright 2021 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(":stamp.bzl", "stamp_build_setting")

licenses(["notice"])  # Apache 2.0

filegroup(
    name = "distribution",
    srcs = glob(["**"]),
    visibility = ["//python:__pkg__"],
)

# Filegroup of bzl files that can be used by downstream rules for documentation generation
# Using a filegroup rather than bzl_library to not give a transitive dependency on Skylib
filegroup(
    name = "bzl",
    srcs = glob(["**/*.bzl"]),
    visibility = ["//python:__pkg__"],
)

# Needed to define bzl_library targets for docgen. (We don't define the
# bzl_library target here because it'd give our users a transitive dependency
# on Skylib.)
exports_files(
    [
        "reexports.bzl",
        "stamp.bzl",
    ],
    visibility = ["//docs:__pkg__"],
)

# Used to determine the use of `--stamp` in Starlark rules
stamp_build_setting(name = "stamp")
