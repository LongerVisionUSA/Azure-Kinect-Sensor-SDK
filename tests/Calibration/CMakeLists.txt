# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

add_executable(calibration_ut calibration.cpp)

target_link_libraries(calibration_ut PRIVATE
    aziotsharedutil
    gtest
    k4ainternal::calibration
    k4ainternal::utcommon)

k4a_add_tests(TARGET calibration_ut TEST_TYPE UNIT)
