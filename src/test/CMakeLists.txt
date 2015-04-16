message("TODO: convert rviz tests to catkin.")

add_executable(send_images EXCLUDE_FROM_ALL send_images.cpp)
target_link_libraries(send_images ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests send_images)

add_executable(marker_test EXCLUDE_FROM_ALL marker_test.cpp)
target_link_libraries(marker_test ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests marker_test)

add_executable(mesh_marker_test EXCLUDE_FROM_ALL mesh_marker_test.cpp)
target_link_libraries(mesh_marker_test ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests mesh_marker_test)



##   qt4_wrap_cpp(MOC_MOCK_PROPERTY_CHANGE_RECEIVER
##     mock_property_change_receiver.h
##   )
##   rosbuild_add_gtest(property_test
##     property_test.cpp
##     mock_property_change_receiver.cpp
##     ${MOC_MOCK_PROPERTY_CHANGE_RECEIVER}
##   )
##   target_link_libraries(property_test ${PROJECT_NAME} ${QT_LIBRARIES})
##   
##   qt4_wrap_cpp(MOC_MOCK_DISPLAY
##     mock_display.h
##   )
##   rosbuild_add_gtest(display_test
##     display_test.cpp
##     mock_context.cpp
##     mock_display.cpp
##     mock_display_factory.cpp
##     mock_property_change_receiver.cpp
##     ${MOC_MOCK_DISPLAY}
##     ${MOC_MOCK_PROPERTY_CHANGE_RECEIVER}
##   )
##   target_link_libraries(display_test ${PROJECT_NAME} ${QT_LIBRARIES})
##   
##   # qt4_wrap_cpp(MOC_PLAYGROUND
##   #   mock_display.h
##   #   playground.h
##   #   fun_display.h
##   # )
##   # rosbuild_add_executable(playground
##   #   playground.cpp
##   #   fun_display.cpp
##   #   mock_display.cpp
##   #   mock_display_factory.cpp
##   #   ${MOC_PLAYGROUND}
##   # )
##   # target_link_libraries(playground ${PROJECT_NAME} ${QT_LIBRARIES})
##   
##   ## rosbuild_add_gtest(uniform_string_stream_test uniform_string_stream_test.cpp ../rviz/uniform_string_stream.cpp)
##   ## 
##   rosbuild_add_executable(marker_test marker_test.cpp)
##   rosbuild_declare_test(marker_test)
##   
##   rosbuild_add_executable(rviz_logo_marker EXCLUDE_FROM_ALL rviz_logo_marker.cpp)
##   rosbuild_add_executable(cloud_test EXCLUDE_FROM_ALL cloud_test.cpp)
##   
##   
##   #rosbuild_add_executable(interactive_marker_test interactive_marker_test.cpp)
##   #rosbuild_declare_test(interactive_marker_test)
##   
##   ## # rosbuild_add_executable(cloud_test EXCLUDE_FROM_ALL cloud_test.cpp)
##   ## # rosbuild_declare_test(cloud_test)
##   ## # rosbuild_add_executable(image_test EXCLUDE_FROM_ALL image_test.cpp)
##   ## # rosbuild_declare_test(image_test)
##   ## # 
##   ## rosbuild_add_gtest(interactive_marker_client_test
##   ##   interactive_marker_client_test.cpp
##   ##   ../rviz/default_plugin/interactive_markers/interactive_marker_client.cpp)
##   ##  
add_executable(send_lots_of_points EXCLUDE_FROM_ALL send_lots_of_points_node.cpp)
target_link_libraries(send_lots_of_points ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests send_lots_of_points)

add_executable(send_point_cloud_2 EXCLUDE_FROM_ALL send_point_cloud_2.cpp)
target_link_libraries(send_point_cloud_2 ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests send_point_cloud_2)

add_executable(send_grid_cells EXCLUDE_FROM_ALL send_grid_cells_node.cpp)
target_link_libraries(send_grid_cells ${catkin_LIBRARIES} ${urdfdom_LIBRARIES})
add_dependencies(tests send_grid_cells)

# This is a test program that uses the rviz panel interface.
add_executable(render_panel_test render_panel_test.cpp)
target_link_libraries(render_panel_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests render_panel_test)

# This is an executable which uses the rviz new display diaglog interface.
add_executable(new_display_dialog_test new_display_dialog_test.cpp)
target_link_libraries(new_display_dialog_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests new_display_dialog_test)

# This is an executable which uses the rviz color editor test.
add_executable(color_editor_test color_editor_test.cpp)
target_link_libraries(color_editor_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests color_editor_test)

# This is a modified version of the property test.
qt4_wrap_cpp(PROPERTY_TEST_MOC_FILES
  ros_spinner.h
)
catkin_add_gtest(property_with_ros_spinner_test
  property_test.cpp
  ros_spinner.cpp
  mock_property_change_receiver.cpp
  ${PROPERTY_TEST_MOC_FILES}
  ${MOC_MOCK_PROPERTY_CHANGE_RECEIVER}
)
target_link_libraries(property_with_ros_spinner_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests property_with_ros_spinner_test)

# This is an executable that uses the line_edit_with_button property interface.
add_executable(line_edit_with_button_test line_edit_with_button_test.cpp)
target_link_libraries(line_edit_with_button_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests line_edit_with_button_test)

# This is an executable which tests the connect/disconnect behavior of signals and slots in Qt.
qt4_wrap_cpp(MOC_FILES
  connect_test.h
)
add_executable(connect_test connect_test.cpp ${MOC_FILES})
target_link_libraries(connect_test ${QT_LIBRARIES})
add_dependencies(tests connect_test)

# This is a GTest which tests the display configuration.
catkin_add_gtest(config_test config_test.cpp ../rviz/uniform_string_stream.cpp ../rviz/config.cpp)
target_link_libraries(config_test ${QT_LIBRARIES})

# This is an acceptance test executable which renders points.
qt4_wrap_cpp(RENDER_POINTS_TEST_MOC_FILES
  render_points_test.h
)
add_executable(render_points_test
  render_points_test.cpp
  ../rviz/ogre_helpers/orbit_camera.cpp
  ${RENDER_POINTS_TEST_MOC_FILES}
)
target_link_libraries(render_points_test rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests render_points_test)

# This is an example application which creates two ogre render windows.
add_executable(two_render_widgets two_render_widgets.cpp)
target_link_libraries(two_render_widgets rviz ${catkin_LIBRARIES} ${QT_LIBRARIES})
add_dependencies(tests two_render_widgets)

# This is a GTest which tests the STL loader
catkin_add_gtest(stl_loader_test stl_loader_test.cpp
  ../rviz/ogre_helpers/stl_loader.cpp)
target_link_libraries(stl_loader_test ${catkin_LIBRARIES} OgreMain)
