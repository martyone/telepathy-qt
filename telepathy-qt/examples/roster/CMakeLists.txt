set(roster_SRCS
    main.cpp
    roster-window.cpp
    roster-item.cpp
    roster-widget.cpp)

set(roster_MOC_SRCS
    roster-window.h
    roster-item.h
    roster-widget.h)

tpqt_generate_mocs(${roster_MOC_SRCS})

add_executable(roster ${roster_SRCS} ${roster_MOC_SRCS})
target_link_libraries(roster
    ${Qt5Core_LIBRARIES}
    ${Qt5DBus_LIBRARIES}
    ${Qt5Gui_LIBRARIES}
    ${Qt5Network_LIBRARIES}
    ${Qt5Widgets_LIBRARIES}
    ${Qt5Xml_LIBRARIES}
    telepathy-qt${Qt5Core_VERSION_MAJOR}
    ${TP_QT_EXECUTABLE_LINKER_FLAGS})

set(telepathy_qt_examples_roster_SRCS
    roster-item.cpp
    roster-widget.cpp
    ${CMAKE_CURRENT_BINARY_DIR}/_gen/roster-item.moc.hpp
    ${CMAKE_CURRENT_BINARY_DIR}/_gen/roster-widget.moc.hpp)

add_library(telepathy-qt-examples-roster ${telepathy_qt_examples_roster_SRCS})
target_link_libraries(telepathy-qt-examples-roster
    ${Qt5Core_LIBRARIES}
    ${Qt5DBus_LIBRARIES}
    ${Qt5Gui_LIBRARIES}
    ${Qt5Network_LIBRARIES}
    ${Qt5Widgets_LIBRARIES}
    ${Qt5Xml_LIBRARIES}
    telepathy-qt${Qt5Core_VERSION_MAJOR}
    ${TP_QT_LIBRARY_LINKER_FLAGS})
