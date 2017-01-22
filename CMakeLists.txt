cmake_minimum_required(VERSION 3.6)
project(agentxtutorial)

set(CMAKE_CXX_STANDARD 11)

# Set net-snmp related configuration
set(NETSNMPCONFIG net-snmp-config)
execute_process(COMMAND ${NETSNMPCONFIG} --base-cflags
        OUTPUT_VARIABLE NETSNMPCFLAGS)
execute_process(COMMAND ${NETSNMPCONFIG} --agent-libs
        OUTPUT_VARIABLE NETSNMPLIBS)
## To take care of CMP0004 - leading or trailing whitespace
string(STRIP ${NETSNMPLIBS} NETSNMPLIBS)

set(LIBS ${NETSNMPLIBS})
set(CFLAGS "-I. ${NETSNMPCFLAGS}")

set(SOURCE_FILES
        myTestTable.c
        myTestTable.h
        myTestTable_data_access.c
        myTestTable_data_access.h
        myTestTable_data_get.c
        myTestTable_data_get.h
        myTestTable_data_set.c
        myTestTable_data_set.h
        myTestTable_enums.h
        myTestTable_interface.c
        myTestTable_interface.h
        myTestTable_oids.h
        agentxTutorial.c
        agentxTutorial.h
        agentxTutorial_subagent.c
        )

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} ${LIBS})
