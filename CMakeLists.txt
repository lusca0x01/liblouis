cmake_minimum_required(VERSION 3.9)

set(LIB liblouis)
set(TABLESDIR ${CMAKE_CURRENT_SOURCE_DIR}/tables)

project(${LIB} VERSION 1.0.0 LANGUAGES C)

add_library(${LIB} SHARED
    liblouis/commonTranslationFunctions.c
    liblouis/logging.c
    liblouis/lou_translateString.c
    liblouis/metadata.c
    liblouis/utils.c
    liblouis/compileTranslationTable.c
    liblouis/lou_backTranslateString.c
    liblouis/maketable.c
    liblouis/pattern.c
)

target_compile_definitions(${LIB} PRIVATE TABLESDIR="${TABLESDIR}")

set_target_properties(${LIB} PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(${LIB} PROPERTIES SOVERSION ${PROJECT_VERSION_MAJOR})
target_include_directories(${LIB} PUBLIC liblouis)

install(TARGETS ${LIB} LIBRARY DESTINATION .)
