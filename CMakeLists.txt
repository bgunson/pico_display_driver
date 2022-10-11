cmake_minimum_required(VERSION 3.16)

include(pico_sdk_import.cmake)
project(pico_display_driver C CXX ASM)
pico_sdk_init()

add_subdirectory(lib/Config)
add_subdirectory(lib/Infrared)
add_subdirectory(lib/OLED)
add_subdirectory(lib/Icm20948)
add_subdirectory(lib/LCD)
add_subdirectory(lib/Fonts)
add_subdirectory(lib/GUI)
add_subdirectory(examples)

add_library(pico_display_driver INTERFACE)

target_include_directories(pico_display_driver INTERFACE
    examples
    lib/Config
    lib/GUI
    lib/Fonts
    lib/Icm20948
    lib/Infrared
    lib/LCD
    lib/OLED
)

target_link_libraries(pico_display_driver INTERFACE 
    examples 
    Config 
    GUI 
    Fonts 
    Icm20948 
    Infrared 
    LCD 
    OLED 
    pico_stdlib 
    hardware_spi
)