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
    name = "moc_character_form_editor",
    srcs = [
        "character_form_editor.h",
    ],
    outs = ["moc_character_form_editor.cc"],
)

qt_moc_mozc(
    name = "moc_combobox_delegate",
    srcs = [
        "combobox_delegate.h",
    ],
    outs = ["moc_combobox_delegate.cc"],
)

qt_moc_mozc(
    name = "moc_config_dialog",
    srcs = [
        "config_dialog.h",
    ],
    outs = ["moc_config_dialog.cc"],
)

qt_moc_mozc(
    name = "moc_generic_table_editor",
    srcs = [
        "generic_table_editor.h",
    ],
    outs = ["moc_generic_table_editor.cc"],
)

qt_moc_mozc(
    name = "moc_keybinding_editor",
    srcs = [
        "keybinding_editor.h",
    ],
    outs = ["moc_keybinding_editor.cc"],
)

qt_moc_mozc(
    name = "moc_keybinding_editor_delegate",
    srcs = [
        "keybinding_editor_delegate.h",
    ],
    outs = ["moc_keybinding_editor_delegate.cc"],
)

qt_moc_mozc(
    name = "moc_keymap_editor",
    srcs = [
        "keymap_editor.h",
    ],
    outs = ["moc_keymap_editor.cc"],
)

qt_moc_mozc(
    name = "moc_roman_table_editor",
    srcs = [
        "roman_table_editor.h",
    ],
    outs = ["moc_roman_table_editor.cc"],
)

qt_uic_mozc(
    name = "uic_config_dialog",
    srcs = [
        "config_dialog.ui",
    ],
    outs = ["ui_config_dialog.h"],
)

qt_uic_mozc(
    name = "uic_generic_table_editor",
    srcs = [
        "generic_table_editor.ui",
    ],
    outs = ["ui_generic_table_editor.h"],
)

qt_uic_mozc(
    name = "uic_keybinding_editor",
    srcs = [
        "keybinding_editor.ui",
    ],
    outs = ["ui_keybinding_editor.h"],
)

qt_rcc_mozc(
    name = "qrc_config_dialog",
    srcs = [
        "config_dialog_en.qm",
        "config_dialog_ja.qm",
        "keymap_en.qm",
        "keymap_ja.qm",
        "//gui/base:tr_en.qm",
        "//gui/base:tr_ja.qm",
    ],
    outs = ["qrc_config_dialog.cc"],
    qrc_file = "config_dialog.qrc",
    qrc_name = "qrc_config_dialog",
)

cc_qt_library_mozc(
    name = "combobox_delegate",
    srcs = [
        "combobox_delegate.cc",
        ":moc_combobox_delegate",
    ],
    hdrs = [
        "combobox_delegate.h",
    ],
)

cc_qt_library_mozc(
    name = "config_dialog",
    srcs = [
        "character_form_editor.cc",
        "config_dialog.cc",
        "config_dialog_libmain.cc",
        "generic_table_editor.cc",
        "keybinding_editor.cc",
        "keybinding_editor_delegate.cc",
        "keymap_editor.cc",
        "roman_table_editor.cc",
        ":moc_character_form_editor",
        ":moc_config_dialog",
        ":moc_generic_table_editor",
        ":moc_keybinding_editor",
        ":moc_keybinding_editor_delegate",
        ":moc_keymap_editor",
        ":moc_roman_table_editor",
        ":qrc_config_dialog",
    ],
    hdrs = [
        "character_form_editor.h",
        "config_dialog.h",
        "generic_table_editor.h",
        "keybinding_editor.h",
        "keybinding_editor_delegate.h",
        "keymap_editor.h",
        "roman_table_editor.h",
        ":uic_config_dialog",
        ":uic_generic_table_editor",
        ":uic_keybinding_editor",
    ],
    deps = [
        ":combobox_delegate",
        "//base:config_file_stream",
        "//base:file_stream",
        "//base:file_util",
        "//base:logging",
        "//base:port",
        "//base:process",
        "//base:run_level",
        "//base:singleton",
        "//base:system_util",
        "//base:util",
        "//base:version",
        "//client",
        "//composer:key_parser",
        "//config:config_handler",
        "//config:stats_config_util",
        "//gui/base:gui_base",
        "//gui/base:singleton_window_helper",
        "//protocol:commands_proto",
        "//protocol:config_proto",
        "//session/internal:keymap",
        "@com_google_absl//absl/memory",
    ],
)

cc_qt_library_mozc(
    name = "config_dialog_main_lib",
    srcs = ["config_dialog_main.cc"],
    deps = [
        ":config_dialog",
        "//base:init_mozc",
        "//gui/base:gui_base",
    ],
)

cc_qt_binary_mozc(
    name = "config_dialog_main",
    deps = [":config_dialog_main_lib"],
)

macos_qt_application_mozc(
    name = "config_dialog_macos",
    bundle_name = "ConfigDialog",
    deps = [":config_dialog_main_lib"],
)
