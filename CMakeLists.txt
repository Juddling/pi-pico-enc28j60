# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)

# initalize pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH "~/pico-sdk")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)
#include(pico_extras_import.cmake)

project(pico_spi_ethernet C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1

# removed pico_spi_ethernet.c
add_executable(pico_spi_ethernet enc28j60.c lwip.cpp)

# This is required to include lwipopts.h
target_include_directories(pico_spi_ethernet PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/lwip
)

# Add the standard library to the build
target_link_libraries(pico_spi_ethernet pico_stdlib)

# Add any user requested libraries
target_link_libraries(
        pico_spi_ethernet
#        pico_lwip
#        pico_lwip_arch
        pico_lwip_nosys
        hardware_spi
)

pico_set_program_name(pico_spi_ethernet "pico_spi_ethernet")
pico_set_program_version(pico_spi_ethernet "0.1")

pico_enable_stdio_usb(pico_spi_ethernet 1)
pico_enable_stdio_uart(pico_spi_ethernet 0)

pico_add_extra_outputs(pico_spi_ethernet)
