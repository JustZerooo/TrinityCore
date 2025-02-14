# This file is part of the TrinityCore Project. See AUTHORS file for Copyright information
#
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without
# modifications, as long as this notice is preserved.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

CollectSourceFiles(${CMAKE_CURRENT_SOURCE_DIR} PRIVATE_SOURCES)

list(APPEND PRIVATE_SOURCES ${sources_windows})

GroupSources(${CMAKE_CURRENT_SOURCE_DIR})

if(PLATFORM EQUAL 64)
  set(target_name client_launcher_64)
else()
  set(target_name client_launcher_32)
endif()

add_executable(${target_name} ${PRIVATE_SOURCES})

target_link_libraries(${target_name}
  PRIVATE
    trinity-core-interface
  PUBLIC
    common
)

install(TARGETS ${target_name} DESTINATION "${CMAKE_INSTALL_PREFIX}")
