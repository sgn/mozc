# -*- coding: utf-8 -*-
# Copyright 2010-2021, Google Inc.
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are
# met:
#
#     * Redistributions of source code must retain the above copyright
# notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above
# copyright notice, this list of conditions and the following disclaimer
# in the documentation and/or other materials provided with the
# distribution.
#     * Neither the name of Google Inc. nor the names of its
# contributors may be used to endorse or promote products derived from
# this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

load(
    "//tools/build_defs:qt.bzl",
    "cc_qt_binary_mozc",
    "cc_qt_library_mozc",
    "macos_qt_application_mozc",
    "qt_moc_mozc",
    "qt_rcc_mozc",
)

package(
    default_visibility = ["//gui:__subpackages__"],
)

qt_moc_mozc(
    name = "moc_error_message_dialog",
    srcs = ["error_message_dialog.h"],
    outs = ["moc_error_message_dialog.cc"],
)

qt_rcc_mozc(
    name = "qrc_error_message_dialog",
    srcs = [
        "error_message_dialog_en.qm",
        "error_message_dialog_ja.qm",
        "//gui/base:tr_en.qm",
        "//gui/base:tr_ja.qm",
    ],
    outs = ["qrc_error_message_dialog.cc"],
    qrc_file = "error_message_dialog.qrc",
    qrc_name = "qrc_error_message_dialog",
)

cc_qt_library_mozc(
    name = "error_message_dialog",
    srcs = [
        "error_message_dialog.cc",
        "error_message_dialog_libmain.cc",
        ":moc_error_message_dialog",
        ":qrc_error_message_dialog",
    ],
    hdrs = [
        "error_message_dialog.h",
    ],
    deps = [
        "//base:file_util",
        "//base:logging",
        "//base:port",
        "//base:process",
        "//base:process_mutex",
        "//base:run_level",
        "//base:system_util",
        "//base:util",
        "//base:version",
        "//gui/base:gui_base",
        "//gui/base:singleton_window_helper",
        "@com_google_absl//absl/flags:flag",
    ],
)

cc_qt_library_mozc(
    name = "error_message_dialog_main_lib",
    srcs = ["error_message_dialog_main.cc"],
    deps = [
        ":error_message_dialog",
        "//base:init_mozc",
        "//gui/base:gui_base",
    ],
)

cc_qt_binary_mozc(
    name = "error_message_dialog_main",
    deps = [":error_message_dialog_main_lib"],
)

macos_qt_application_mozc(
    name = "error_message_dialog_macos",
    bundle_name = "ErrorMessageDialog",
    deps = [":error_message_dialog_main_lib"],
)
