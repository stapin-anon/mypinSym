#
# Copyright < name removed for anonymity > 
#
# SPDX-License-Identifier: BSD-3-Clause
#

cmake_minimum_required (VERSION 3.19)
project (STAPINTOOL CXX C)



set(CMAKE_CXX_COMPILER ${PINKIT}/${ARCH}/pinrt/bin/pin-g++)

add_library(SymDebugTrace SHARED SymDebugTrace.cpp)

target_compile_definitions(SymDebugTrace PRIVATE ${PIN_DEFS})

target_compile_features(SymDebugTrace PRIVATE cxx_std_17)

target_include_directories(SymDebugTrace PRIVATE 
    ${STAPIN_REPO}/lib/include
    ${PINKIT}/source/include/pin
    ${PINKIT}/source/include/pin/gen
    ${PINKIT}/source/tools/Utils
    ${PINKIT}/extras/components/include
    ${PINKIT}/extras/xed-${ARCH}/include/xed
    ${PINKIT}/${ARCH}/pinrt/include/adaptor
)

target_compile_options(SymDebugTrace PRIVATE -Wall -Wno-unknown-pragmas -fno-stack-protector -funwind-tables -fasynchronous-unwind-tables -fno-rtti -fPIC -DTARGET_LINUX -faligned-new)

target_link_directories(SymDebugTrace PRIVATE  ${PINKIT}/${ARCH}/lib  ${PINKIT}/extras/xed-${ARCH}/lib ${STAPIN_REPO}/build/lib/)

target_link_libraries(SymDebugTrace stapin pin  pinrt-adaptor-static xed pindwarf dwarf unwind-dynamic)

target_link_options(SymDebugTrace PRIVATE -Wl,-Bsymbolic -Wl,--version-script=${PINKIT}/source/include/pin/pintool.ver)





