﻿
include_directories(${CMAKE_INCLUDE_PATH} "../../api/")

link_directories(${CMAKE_LIBRARY_PATH})

aux_source_directory(market MARKET_DIR)
aux_source_directory(trader TRADER_DIR)

if(UNIX)
    add_definitions( "-fPIC" )
    set(LINK_LIBS dl)
endif()

add_library(latf-adapter-v3x SHARED "interface.cpp" ${MARKET_DIR} ${TRADER_DIR})

target_link_libraries(latf-adapter-v3x ${MARKET_LIBS} ${LINK_LIBS})