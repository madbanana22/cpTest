cmake_minimum_required (VERSION 3.8)

# MSVC hot reload
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("cpTest")

file (GLOB_RECURSE SRCS "src/*.cpp" "src/*.hpp" "src/*.c" "src/*.h") # haha glob_recurse goes brbr

add_library (cpTest ${SRCS})

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET cpTest PROPERTY CXX_STANDARD 20)
endif()