#  ___ _____ _   ___ _  _____ ___  ___  ___ ___
# / __|_   _/_\ / __| |/ / __/ _ \| _ \/ __| __|
# \__ \ | |/ _ \ (__| ' <| _| (_) |   / (__| _|
# |___/ |_/_/ \_\___|_|\_\_| \___/|_|_\\___|___|
# embedded.connectivity.solutions.==============
#
# copyright  STACKFORCE GmbH, Heitersheim, Germany, http://www.stackforce.de
# author     Heiko Berger (STACKFORCE), Patrick Weber (STACKFORCE)
# brief
#
# This work is dual-licensed under Apache 2.0 and GPL 2.0. You can choose between one of them if you use this work.
# For further details, please refer to the project home: https://github.com/opend-connect/openD
#
# SPDX-License-Identifier: Apache-2.0 OR GPL-2.0-only

cmake_minimum_required(VERSION 2.8)


##
## PROJECT
##
project(dspg_hanfun_api_fp)

enable_testing()

SET(MOCKED_MODULES_SOURCE_DIR ../../../../../src)

##
## Includes
##
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/
    ${CMAKE_CURRENT_SOURCE_DIR}/../
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/fp_hanfun/hanfun_api
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/fp_hanfun/iwu
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/test/appcmbs
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/cmbs
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/frame
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/include
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/test
    ${MOCKED_MODULES_SOURCE_DIR}/opend/dspg/cmbs/test/ListAccess
    ${MOCKED_MODULES_SOURCE_DIR}/opend
    ${MOCKED_MODULES_SOURCE_DIR}/opend/prv
    ${MOCKED_MODULES_SOURCE_DIR}/hanfun_lib/inc
)


##
## Add targets
##
add_executable(ut_dspg_openD_hanfunApi_fp_init ut_dspg_openD_hanfunApi_fp_init.cpp)
add_executable(ut_dspg_openD_hanfunApi_fp_devMgmtRequest ut_dspg_openD_hanfunApi_fp_devMgmtRequest.cpp)
add_executable(ut_dspg_openD_hanfunApi_fp_bindMgmtRequest ut_dspg_openD_hanfunApi_fp_bindMgmtRequest.cpp)
add_executable(ut_dspg_openD_hanfunApi_fp_profileRequest ut_dspg_openD_hanfunApi_fp_profileRequest.cpp)



##
## Link targets
##
target_link_libraries(ut_dspg_openD_hanfunApi_fp_init libgmock pthread libApp libMockDspgTestLib libTestHanFun mockDspgAppMsgParser)
target_compile_definitions(ut_dspg_openD_hanfunApi_fp_init PUBLIC -DCMBS_BUF_SIZE=2560 -DHF_APP_EXT_REG)

target_link_libraries(ut_dspg_openD_hanfunApi_fp_devMgmtRequest libgmock pthread libApp libMockDspgTestLib libTestHanFun mockDspgAppMsgParser)
target_compile_definitions(ut_dspg_openD_hanfunApi_fp_devMgmtRequest PUBLIC -DCMBS_BUF_SIZE=2560 -DHF_APP_EXT_REG)

target_link_libraries(ut_dspg_openD_hanfunApi_fp_bindMgmtRequest libgmock pthread libApp libMockDspgTestLib libTestHanFun mockDspgAppMsgParser)
target_compile_definitions(ut_dspg_openD_hanfunApi_fp_bindMgmtRequest PUBLIC -DCMBS_BUF_SIZE=2560 -DHF_APP_EXT_REG)

target_link_libraries(ut_dspg_openD_hanfunApi_fp_profileRequest libgmock pthread libApp libMockDspgTestLib libTestHanFun mockDspgAppMsgParser)
target_compile_definitions(ut_dspg_openD_hanfunApi_fp_profileRequest PUBLIC -DCMBS_BUF_SIZE=2560 -DHF_APP_EXT_REG)

##
## Add tests
##
add_test(NAME ut_dspg_openD_hanfunApi_fp_init
         COMMAND ut_dspg_openD_hanfunApi_fp_init --gtest_output=xml:ut_dspg_openD_hanfunApi_fp_init.xml)
add_test(NAME ut_dspg_openD_hanfunApi_fp_devMgmtRequest
         COMMAND ut_dspg_openD_hanfunApi_fp_devMgmtRequest --gtest_output=xml:ut_dspg_openD_hanfunApi_fp_devMgmtRequest.xml)
add_test(NAME ut_dspg_openD_hanfunApi_fp_bindMgmtRequest
         COMMAND ut_dspg_openD_hanfunApi_fp_bindMgmtRequest --gtest_output=xml:ut_dspg_openD_hanfunApi_fp_bindMgmtRequest.xml)
add_test(NAME ut_dspg_openD_hanfunApi_fp_profileRequest
         COMMAND ut_dspg_openD_hanfunApi_fp_profileRequest --gtest_output=xml:ut_dspg_openD_hanfunApi_fp_profileRequest.xml)
