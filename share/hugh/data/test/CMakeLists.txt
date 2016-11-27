# -*- Mode:cmake -*-

####################################################################################################
#                                                                                                  #
# Copyright (C) 2016 University of Hull                                                            #
#                                                                                                  #
####################################################################################################

cma_print_current_directory()

set(SRC)
list(APPEND SRC README.rst)
list(APPEND SRC test_2squares.obj)
list(APPEND SRC test_cube.obj)
list(APPEND SRC test_lines.obj)
list(APPEND SRC test_linestrips.obj)
list(APPEND SRC test_points.obj)
list(APPEND SRC test_poly.obj)
list(APPEND SRC test_quads.obj)
list(APPEND SRC test_trifans.obj)
list(APPEND SRC test_tris.obj)
list(APPEND SRC test_tristrips.obj)

install(FILES ${SRC}
        DESTINATION ${${PROJECT_NAME}_SHARE_DIRECTORY}/hugh/data/test
	COMPONENT   ${${PROJECT_NAME}_DAT_COMPONENT_NAME})
