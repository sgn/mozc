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
    "qt_uic_mozc",
)

package(
    default_visibility = ["//gui:__subpackages__"],
)

qt_moc_mozc(
    name = "moc_word_register_dialog",
    srcs = ["word_register_dialog.h"],
    outs = ["moc_word_register_dialog.cc"],
)

qt_uic_mozc(
    name = "uic_word_register_dialog",
    srcs = ["word_register_dialog.ui"],
    outs = ["ui_word_register_dialog.h"],
)

qt_rcc_mozc(
    name = "qrc_word_register_dialog",
    srcs = [
        "word_register_dialog_en.qm",
        "word_register_dialog_ja.qm",
        "//gui/base:tr_en.qm",
        "//gui/base:tr_ja.qm",
    ],
    outs = ["qrc_word_register_dialog.cc"],
    qrc_file = "word_register_dialog.qrc",
    qrc_name = "qrc_word_register_dialog",
)

cc_qt_library_mozc(
    name = "word_register_dialog",
    srcs = [
        "word_register_dialog.cc",
        "word_register_dialog_libmain.cc",
        ":moc_word_register_dialog",
        ":qrc_word_register_dialog",
    ],
    hdrs = [
        "word_register_dialog.h",
        ":uic_word_register_dialog",
    ],
    deps = [
        "//base",
        "//base:logging",
        "//base:port",
        "//base:system_util",
        "//base:util",
        "//client",
        "//data_manager:pos_list_provider",
        "//dictionary:pos_matcher_lib",
        "//dictionary:user_dictionary",
        "//dictionary:user_dictionary_session",
        "//dictionary:user_dictionary_storage",
        "//dictionary:user_dictionary_util",
        "//gui/base:gui_base",
        "//gui/base:singleton_window_helper",
        "//protocol:commands_proto",
        "//protocol:user_dictionary_storage_proto",
    ],
)

cc_qt_library_mozc(
    name = "word_register_dialog_main_lib",
    srcs = ["word_register_dialog_main.cc"],
    deps = [
        ":word_register_dialog",
        "//base:init_mozc",
        "//gui/base:gui_base",
    ],
)

cc_qt_binary_mozc(
    name = "word_register_dialog_main",
    deps = [":word_register_dialog_main_lib"],
)

macos_qt_application_mozc(
    name = "word_register_dialog_macos",
    bundle_name = "WordRegisterDialog",
    deps = [":word_register_dialog_main_lib"],
)
