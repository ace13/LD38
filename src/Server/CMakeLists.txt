set(SOURCES
    main.cpp

    GameServer.cpp
)

source_group("Header files\\" REGULAR_EXPRESSION "[^./]+.(hpp|inl)")
source_group("Source files\\" REGULAR_EXPRESSION "[^./]+.cpp")

add_executable(Server
    ${SOURCES}
)
add_executable(LD38::Server ALIAS Server)

set_target_properties(Server PROPERTIES
    ${DEFAULT_PROJECT_OPTIONS}
    FOLDER "${IDE_FOLDER}"
)
target_include_directories(Server SYSTEM PRIVATE
    ${DEFAULT_SYSTEM_INCLUDE_DIRECTORIES}
)
target_include_directories(Server PRIVATE
    ${DEFAULT_INCLUDE_DIRECTORIES}
)
target_link_libraries(Server PRIVATE
    ${DEFAULT_LIBRARIES}
    LD38::External::libyojimbo
    LD38::Common
)
target_compile_options(Server PRIVATE
    ${DEFAULT_COMPILE_OPTIONS}
)
target_link_libraries(Server PRIVATE
    ${DEFAULT_LINKER_OPTIONS}
)
