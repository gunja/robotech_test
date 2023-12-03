cmake_minimum_required(VERSION 2.8)

find_package(PkgConfig REQUIRED)
pkg_check_modules(MODBUS REQUIRED libmodbus)

set (SERVER_SRC srv_main.cpp 
            srv_inet.cpp 
            srv_mb.cpp
)

set  (CLT_SRC clt_main.cpp 
          clt_inet.cpp
)

add_executable(server ${SERVER_SRC})
add_executable(client ${CLT_SRC})

target_link_libraries(server PUBLIC ${MODBUS_LIBRARIES})

