#  ___ _____ _   ___ _  _____ ___  ___  ___ ___
# / __|_   _/_\ / __| |/ / __/ _ \| _ \/ __| __|
# \__ \ | |/ _ \ (__| ' <| _| (_) |   / (__| _|
# |___/ |_/_/ \_\___|_|\_\_| \___/|_|_\\___|___|
# embedded.connectivity.solutions.==============
#
# copyright  STACKFORCE GmbH, Heitersheim, Germany, http://www.stackforce.de
# author     Heiko Berger (STACKFORCE)
# brief      openD dialog
#
# This work is dual-licensed under Apache 2.0 and GPL 2.0. You can choose between one of them if you use this work.
# For further details, please refer to the project home: https://github.com/opend-connect/openD
#
# SPDX-License-Identifier: Apache-2.0 OR GPL-2.0-only

project(opend_dialog)

cmake_minimum_required(VERSION 3.6)

#---------------------------------------------------------------------------------------
# Add subdirectories
#---------------------------------------------------------------------------------------

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/dect-hdlc)

if(APPLICATION STREQUAL LEGACY_FP OR APPLICATION STREQUAL LEGACY_FP_SERVER)

    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/fp_legacy)

elseif(APPLICATION STREQUAL LEGACY_PP OR APPLICATION STREQUAL LEGACY_PP_INTERCOM)

    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/pp_legacy)

elseif(APPLICATION STREQUAL HANFUN_SimpleSwitch_FP)

    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/fp_hanfun)

elseif(APPLICATION STREQUAL HANFUN_SimpleLight_PP)

    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/pp_hanfun)

endif()
