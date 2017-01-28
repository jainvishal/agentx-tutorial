    set(SOURCE_FILES
        agentxTutorial.c
        agentxTutorial_subagent.c
        agentxTutorial_traps.c
        myTestTable/myTestTable.c
        myTestTable/myTestTable_data_access.c
        myTestTable/myTestTable_data_get.c
        myTestTable/myTestTable_data_set.c
        myTestTable/myTestTable_interface.c
        )

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} ${LIBS})