cmake_minimum_required(VERSION 3.12)

set(NRF_TARGET nrf52)
if (NOT DEFINED ARM_NONE_EABI_TOOLCHAIN_PATH)
	set(ARM_NONE_EABI_TOOLCHAIN_PATH "/usr")
endif ()

set(NRF5_SDK_PATH "${CMAKE_CURRENT_LIST_DIR}/../nRF5SDK160098a08e2")
set(NRFJPROG "/usr/bin/nrfjprog")

include("${CMAKE_CURRENT_LIST_DIR}/../tools/CMake_nRF52.cmake")

nRF52_toolchainSetup()

project(test
        VERSION 0.1.0
        DESCRIPTION "personal fencer unit"
        LANGUAGES C CXX ASM)

add_subdirectory(src)