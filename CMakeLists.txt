cmake_minimum_required(VERSION 3.16.0)

list(APPEND EXTRA_COMPONENT_DIRS "components/cryptoauthlib")

set(CONFIG_DEVICE_COMMON_NAME "ecc608")

list(APPEND EXTRA_COMPONENT_DIRS "components/esp-azure/port")

include($ENV{IDF_PATH}/tools/cmake/project.cmake)

project(tngtest-azure)
