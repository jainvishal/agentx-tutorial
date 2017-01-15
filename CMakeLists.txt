cmake_minimum_required(VERSION 3.6)
project(agentx-tutorial)

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
        agentxTutorial.c
        agentxTutorial.h
        agentxTutorial_subagent.c
        )

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} ${LIBS})