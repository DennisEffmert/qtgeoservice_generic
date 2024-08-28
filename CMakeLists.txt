cmake_minimum_required(VERSION 3.14)

project(qtgeoservices_esri LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt5 REQUIRED COMPONENTS core location positioning network)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS core location positioning network)

include_directories(qtgeoservices_esri ${Qt5Location_PRIVATE_INCLUDE_DIRS})

add_library(qtgeoservices_esri SHARED
    geocodereply_esri.h
    geocodingmanagerengine_esri.h
    geomapsource.h
    georoutejsonparser_esri.h
    georoutereply_esri.h
    georoutingmanagerengine_esri.h
    geoserviceproviderfactory_esri.h
    geotiledmap_esri.h
    geotiledmappingmanagerengine_esri.h
    geotiledmapreply_esri.h
    geotilefetcher_esri.h
    placemanagerengine_esri.h
    placesearchreply_esri.h
    placecategoriesreply_esri.h
    geocodereply_esri.cpp
    geocodingmanagerengine_esri.cpp
    geomapsource.cpp
    georoutejsonparser_esri.cpp
    georoutereply_esri.cpp
    georoutingmanagerengine_esri.cpp
    geoserviceproviderfactory_esri.cpp
    geotiledmap_esri.cpp
    geotiledmappingmanagerengine_esri.cpp
    geotiledmapreply_esri.cpp
    geotilefetcher_esri.cpp
    placemanagerengine_esri.cpp
    placesearchreply_esri.cpp
    placecategoriesreply_esri.cpp
    esri.qrc
    esri_plugin.json
    maps.json
)

target_link_libraries(qtgeoservices_esri PRIVATE Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Location Qt${QT_VERSION_MAJOR}::Positioning Qt${QT_VERSION_MAJOR}::Network)

install(FILES $<TARGET_FILE:qtgeoservices_esri> TYPE BIN)
install(FILES $<TARGET_PDB_FILE_NAME:qtgeoservices_esri> CONFIGURATIONS Debug TYPE BIN)

target_compile_definitions(qtgeoservices_esri PRIVATE QT_ESRI_PLUGIN_LIBRARY)
