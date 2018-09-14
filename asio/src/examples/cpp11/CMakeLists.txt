# allocation
add_executable(allocation ./allocation/server.cpp)
target_link_libraries(allocation ${CMAKE_THREAD_LIBS_INIT})

# buffers
add_executable(reference_counted ./buffers/reference_counted.cpp)
target_link_libraries(reference_counted ${CMAKE_THREAD_LIBS_INIT})

# chat
add_executable(chat_client ./chat/chat_client.cpp)
target_link_libraries(chat_client ${CMAKE_THREAD_LIBS_INIT})
add_executable(chat_server ./chat/chat_server.cpp)
target_link_libraries(chat_server ${CMAKE_THREAD_LIBS_INIT})

# echo
add_executable(async_tcp_echo_server ./echo/async_tcp_echo_server.cpp)
target_link_libraries(async_tcp_echo_server ${CMAKE_THREAD_LIBS_INIT})
add_executable(async_udp_echo_server ./echo/async_udp_echo_server.cpp)
target_link_libraries(async_udp_echo_server ${CMAKE_THREAD_LIBS_INIT})
add_executable(blocking_tcp_echo_client ./echo/blocking_tcp_echo_client.cpp)
target_link_libraries(blocking_tcp_echo_client ${CMAKE_THREAD_LIBS_INIT})
add_executable(blocking_tcp_echo_server ./echo/blocking_tcp_echo_server.cpp)
target_link_libraries(blocking_tcp_echo_server ${CMAKE_THREAD_LIBS_INIT})
add_executable(blocking_udp_echo_client ./echo/blocking_udp_echo_client.cpp)
target_link_libraries(blocking_udp_echo_client ${CMAKE_THREAD_LIBS_INIT})
add_executable(blocking_udp_echo_server ./echo/blocking_udp_echo_server.cpp)
target_link_libraries(blocking_udp_echo_server ${CMAKE_THREAD_LIBS_INIT})

# executors
add_executable(actor ./executors/actor.cpp)
target_link_libraries(actor ${CMAKE_THREAD_LIBS_INIT})
add_executable(bank_account_1 ./executors/bank_account_1.cpp)
target_link_libraries(bank_account_1 ${CMAKE_THREAD_LIBS_INIT})
add_executable(bank_account_2 ./executors/bank_account_2.cpp)
target_link_libraries(bank_account_2 ${CMAKE_THREAD_LIBS_INIT})
add_executable(fork_join ./executors/fork_join.cpp)
target_link_libraries(fork_join ${CMAKE_THREAD_LIBS_INIT})
add_executable(pipeline ./executors/pipeline.cpp)
target_link_libraries(pipeline ${CMAKE_THREAD_LIBS_INIT})
add_executable(priority_scheduler ./executors/priority_scheduler.cpp)
target_link_libraries(priority_scheduler ${CMAKE_THREAD_LIBS_INIT})

# fork
include(CheckIncludeFile)
check_include_file(syslog.h HAVE_SYSLOG_H)
if (${HAVE_SYSLOG_H})
    add_executable(daemon ./fork/daemon.cpp)
    target_link_libraries(daemon ${CMAKE_THREAD_LIBS_INIT})
    add_executable(process_per_connection ./fork/process_per_connection.cpp)
    target_link_libraries(process_per_connection ${CMAKE_THREAD_LIBS_INIT})
endif()

# futures
add_executable(daytime_client ./futures/daytime_client.cpp)
target_link_libraries(daytime_client ${CMAKE_THREAD_LIBS_INIT})

# http
set(SOURCES_http_server
    ./http/server/connection_manager.cpp
    ./http/server/connection.cpp
    ./http/server/main.cpp
    ./http/server/mime_types.cpp
    ./http/server/reply.cpp
    ./http/server/request_handler.cpp
    ./http/server/request_parser.cpp
    ./http/server/server.cpp
)
add_executable(http_server ${SOURCES_http_server})
target_link_libraries(http_server ${CMAKE_THREAD_LIBS_INIT})

# invocation
add_executable(prioritised_handlers ./invocation/prioritised_handlers.cpp)
target_link_libraries(prioritised_handlers ${CMAKE_THREAD_LIBS_INIT})

# iostreams
add_executable(http_client ./iostreams/http_client.cpp)
target_link_libraries(http_client ${CMAKE_THREAD_LIBS_INIT})

# local
if (NOT WIN32)
add_executable(connect_pair ./local/connect_pair.cpp)
target_link_libraries(connect_pair ${CMAKE_THREAD_LIBS_INIT})
add_executable(iostream_client ./local/iostream_client.cpp)
target_link_libraries(iostream_client ${CMAKE_THREAD_LIBS_INIT})
add_executable(stream_client ./local/stream_client.cpp)
target_link_libraries(stream_client ${CMAKE_THREAD_LIBS_INIT})
add_executable(stream_server ./local/stream_server.cpp)
target_link_libraries(stream_server ${CMAKE_THREAD_LIBS_INIT})
endif()

# multicast
add_executable(multicast_receiver ./multicast/receiver.cpp)
target_link_libraries(multicast_receiver ${CMAKE_THREAD_LIBS_INIT})
add_executable(multicast_sender ./multicast/sender.cpp)
target_link_libraries(multicast_sender ${CMAKE_THREAD_LIBS_INIT})

# nonblocking
add_executable(nonblocking ./nonblocking/third_party_lib.cpp)
target_link_libraries(nonblocking ${CMAKE_THREAD_LIBS_INIT})

# spawn
# add_executable(echo_server ./spawn/echo_server.cpp)
# target_link_libraries(echo_server ${CMAKE_THREAD_LIBS_INIT})
# add_executable(parallel_grep ./spawn/parallel_grep.cpp)
# target_link_libraries(parallel_grep ${CMAKE_THREAD_LIBS_INIT})
