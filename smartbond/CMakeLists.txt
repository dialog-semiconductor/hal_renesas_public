# SPDX-License-Identifier: Apache-2.0

zephyr_include_directories(sdk/bsp/include)

if(CONFIG_SOC_SERIES_DA1469X)
    zephyr_include_directories(da1469x_hal)
	add_subdirectory(da1469x_hal)
	message(WARNING  "Unsupported config for 1469x")
elseif(CONFIG_SOC_SERIES_DA1470X)
    #zephyr_include_directories(da1470x_hal)
	#add_subdirectory(da1470x_hal)
	message(WARNING  "Unsupported config for 1470x")
else()
    message(WARNING  "Unsupported SOC series")
endif()

zephyr_include_directories_ifdef(CONFIG_BT cmac)
add_subdirectory_ifdef(CONFIG_BT cmac)