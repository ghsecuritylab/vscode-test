cmake_minimum_required(VERSION 3.12)

set(TARGET_NAME test)

set(NRF5_LINKER_SCRIPT ${CMAKE_CURRENT_LIST_DIR}/config/nrf52.ld)

nRF52_setup()

nRF52_addBLEGATT()
nRF52_addBLEPeerManager()
nRF52_addAppFDS()

nRF52_addBLEService(ble_lbs)
nRF52_addBLEService(ble_bas)

add_definitions(-DCONFIG_GPIO_AS_PINRESET)

include_directories(${CMAKE_CURRENT_LIST_DIR}/config)
list(APPEND SOURCE_FILES main.c)

nRF52_addExecutable(test "${SOURCE_FILES}")