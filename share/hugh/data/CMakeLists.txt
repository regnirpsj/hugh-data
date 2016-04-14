# -*- Mode:cmake -*-

####################################################################################################
#                                                                                                  #
# Copyright (C) 2016 University of Hull                                                            #
#                                                                                                  #
####################################################################################################

cma_print_current_directory()

set(SRC)
list(APPEND SRC README.rst)

install(FILES ${SRC}
        DESTINATION ${${PROJECT_NAME}_SHARE_DIRECTORY}/hugh/data
	COMPONENT   ${${PROJECT_NAME}_DAT_COMPONENT_NAME})
