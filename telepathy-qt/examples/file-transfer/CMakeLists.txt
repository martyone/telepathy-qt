set(ft-receiver_SRCS
    file-receiver.cpp
    file-receiver-handler.cpp
    pending-file-receive.cpp
    pending-file-transfer.cpp)

set(ft-receiver_MOC_SRCS
    file-receiver.h
    file-receiver-handler.h
    pending-file-receive.h
    pending-file-transfer.h)

tpqt_generate_mocs(${ft-receiver_MOC_SRCS})

add_executable(ft-receiver ${ft-receiver_SRCS} ${ft-receiver_MOC_SRCS})
target_link_libraries(ft-receiver
    ${Qt5Core_LIBRARIES}
    ${Qt5DBus_LIBRARIES}
    ${Qt5Network_LIBRARIES}
    ${Qt5Xml_LIBRARIES}
    telepathy-qt${Qt5Core_VERSION_MAJOR}
    ${TP_QT_EXECUTABLE_LINKER_FLAGS})

set(ft-sender_SRCS
    file-sender.cpp
    pending-file-send.cpp
    pending-file-transfer.cpp)

set(ft-sender_MOC_SRCS
    file-sender.h
    pending-file-send.h
    pending-file-transfer.h)

tpqt_generate_mocs(${ft-sender_MOC_SRCS})

add_executable(ft-sender ${ft-sender_SRCS} ${ft-sender_MOC_SRCS})
target_link_libraries(ft-sender
    ${Qt5Core_LIBRARIES}
    ${Qt5DBus_LIBRARIES}
    ${Qt5Network_LIBRARIES}
    ${Qt5Xml_LIBRARIES}
    telepathy-qt${Qt5Core_VERSION_MAJOR}
    ${TP_QT_EXECUTABLE_LINKER_FLAGS})
