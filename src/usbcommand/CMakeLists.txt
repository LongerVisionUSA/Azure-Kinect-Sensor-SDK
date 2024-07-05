# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBUSB REQUIRED libusb-1.0)

include_directories(${LIBUSB_INCLUDE_DIRS})
link_directories(${LIBUSB_LIBRARY_DIRS})

add_library(k4a_usb_cmd STATIC
            usbcommand.c
            usbstreaming.c
            )

# Consumers should #include <k4ainternal/usbcommand.h>
target_include_directories(k4a_usb_cmd PUBLIC
    ${K4A_PRIV_INCLUDE_DIR})

# Dependencies of this library
target_link_libraries(k4a_usb_cmd PUBLIC
    aziotsharedutil
    ${LIBUSB_LIBRARIES}
    k4ainternal::allocator
    k4ainternal::image
    k4ainternal::logging)

# Define alias for other targets to link against
add_library(k4ainternal::usb_cmd ALIAS k4a_usb_cmd)
