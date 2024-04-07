file(GLOB SRC *.c)
file(GLOB INC vec.h str.h list.h)

if (BUILD_STATIC)
    add_library(cvec-static STATIC ${SRC} ${SRC_POSIX})
    set_target_properties(cvec-static PROPERTIES OUTPUT_NAME cvec)
    set_target_properties(cvec-static PROPERTIES PUBLIC_HEADER "${INC}")
    set(TARGET_STATIC cvec-static)
endif ()

if (BUILD_SHARED)
    add_library(cvec SHARED ${SRC} ${SRC_POSIX})
    set_target_properties(cvec PROPERTIES PUBLIC_HEADER "${INC}")
    set_target_properties(cvec PROPERTIES VERSION 0.1.0 SOVERSION 0)
    set(TARGET_SHARED cvec)
endif ()

install(TARGETS ${TARGET_STATIC} ${TARGET_SHARED}
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    PUBLIC_HEADER DESTINATION include/cvec
)
