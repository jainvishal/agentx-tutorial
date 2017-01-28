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

include_directories(include)
include_directories(include/myTestTable)

add_subdirectory(src)