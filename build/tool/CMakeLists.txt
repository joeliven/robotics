CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(tool NONE)
ADD_DEFINITIONS(-DTOOL)
SET(TOOL_BUILD TRUE)
INCLUDE(../common.cmake)
INCLUDE(../core/CMakeLists.txt core)
SET(CMAKE_MODULE_PATH "${NAO_HOME}/build/tool")
SET(QT_LIBRARY_DIR "${NAO_HOME}/naoqi/link_libs")
SET(QT_BINARY_DIR /usr/lib/x86_64-linux-gnu/qt4)
SET(QT_RCC_EXECUTABLE /usr/lib/x86_64-linux-gnu/qt4/bin/rcc)
SET(QT_MOC_EXECUTABLE /usr/lib/x86_64-linux-gnu/qt4/bin/moc)
SET(QT_UIC_EXECUTABLE /usr/lib/x86_64-linux-gnu/qt4/bin/uic)
SET(QT_QMAKE_EXECUTABLE /usr/lib/x86_64-linux-gnu/qt4/bin/qmake)
FIND_PACKAGE(Qt4 REQUIRED QtCore QtGui QtOpenGL QtXml QtSvg)

SET(TOOL_DIR ${NAO_HOME}/tools/UTNaoTool)
FILE(GLOB_RECURSE tool_SOURCES ${TOOL_DIR}/*.cpp)
FILE(GLOB_RECURSE tool_HEADERS ${TOOL_DIR}/*.h)
FILE(GLOB_RECURSE tool_FORMS ${TOOL_DIR}/*.ui)
FILE(GLOB_RECURSE tool_RESOURCES ${TOOL_DIR}/*.qrc)

ADD_DEFINITIONS(-DBOOST_TT_HAS_OPERATOR_HPP_INCLUDED)
QT4_WRAP_CPP(tool_HEADERS_MOC ${tool_HEADERS})
QT4_WRAP_UI(tool_FORMS_HEADERS ${tool_FORMS})
QT4_ADD_RESOURCES(tool_RESOURCES_RCC ${tool_RESOURCES})

INCLUDE(${QT_USE_FILE})
INCLUDE_DIRECTORIES(${TOOL_DIR} ${QT_DIR})
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR}) # Include ui files
ADD_DEFINITIONS(${QT_DEFINITIONS})
INCLUDE_DIRECTORIES(${NAO_HOME}/build/include)
ADD_EXECUTABLE(tool ${tool_SOURCES} ${tool_HEADERS_MOC} ${tool_FORMS_HEADERS} ${tool_RESOURCES_RCC})

TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libGL.so ${NAOQI_LINK_LIBS}/i386-linux-gnu/libGLU.so ${NAOQI_LINK_LIBS}/i386-linux-gnu/libqglviewer-qt4.a)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libqwt-qt4.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libX11.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libglapi.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXext.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXdamage.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXfixes.so.3)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libX11-xcb.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb-glx.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXxf86vm.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libdrm.so.2)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libfreetype.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXrender.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libfontconfig.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libaudio.so.2)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libz.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libgobject-2.0.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libSM.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libICE.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXi.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libglib-2.0.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libpng12.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXau.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXdmcp.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libexpat.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libXt.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libpcre.so.3)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libffi.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libuuid.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libpng15.so.15)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_highgui.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_calib3d.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_core.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_features2d.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_flann.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_imgproc.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libopencv_nonfree.so)
TARGET_LINK_LIBRARIES(tool ${QT_LIBRARIES})
TARGET_LINK_LIBRARIES(tool ${LIBYAML-CPP} ${LIBPYTHONSWIG} ${WALK_LIBS} ${ALGLIB} ${LIBFFT})
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libboost_thread.so ${NAOQI_LINK_LIBS}/libboost_system.so)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libc.so.6)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb-dri2.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb-dri3.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb-present.so.0)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxcb-sync.so.1)
TARGET_LINK_LIBRARIES(tool ${NAOQI_LINK_LIBS}/libxshmfence.so.1)
TARGET_LINK_LIBRARIES(tool core)
TARGET_LINK_LIBRARIES(core ${NAOQI_LINK_LIBS}/libpng15.so.15)
TARGET_LINK_LIBRARIES(core ${NAOQI_LINK_LIBS}/libopencv_highgui.so)
TARGET_LINK_LIBRARIES(core ${LIBYAML-CPP} ${LIBFFT} ${WALK_LIBS})
EXECUTE_PROCESS(COMMAND rm ${NAO_HOME}/build/tool/UTNaoTool)
IF(CMAKE_BUILD_TYPE STREQUAL "Debug")
  EXECUTE_PROCESS(COMMAND ln -sf ${NAO_HOME}/build/tool/UTNaoTool-debug ${NAO_HOME}/build/tool/UTNaoTool)
ELSE()
  EXECUTE_PROCESS(COMMAND ln -sf ${NAO_HOME}/build/tool/UTNaoTool-release ${NAO_HOME}/build/tool/UTNaoTool)
ENDIF()
