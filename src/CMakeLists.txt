

file(GLOB UDT_SOURCES *.cpp)
file(GLOB UDT_HEADERS *.h)

if(UDT_WITH_JAVA_SUPPORT)
    file(GLOB UDT_JNI_SOURCES RELATIVE ./jni *.cpp)
    file(GLOB UDT_JNI_HEADERS RELATIVE ./jni *.h)
    include_directories(../jvm/include)
endif()

if(WIN32)
    add_definitions(-DWINDOWS)
endif()

add_library(udt STATIC ${UDT_SOURCES} ${UDT_HEADERS} ${UDT_JNI_SOURCES} ${UDT_JNI_HEADERS})
