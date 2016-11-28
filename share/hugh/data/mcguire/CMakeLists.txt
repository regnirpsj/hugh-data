# -*- Mode:cmake -*-

####################################################################################################
#                                                                                                  #
# Copyright (C) 2016 University of Hull                                                            #
#                                                                                                  #
####################################################################################################

cma_print_current_directory()

install(FILES README.rst
        DESTINATION ${${PROJECT_NAME}_SHARE_DIRECTORY}/hugh/data/mcguire
	COMPONENT   ${${PROJECT_NAME}_DAT_COMPONENT_NAME})

set(SRC)
list(APPEND SRC cube.zip)            #   4KB
list(APPEND SRC teapot.zip)          # 651KB
list(APPEND SRC cornell-box.zip)     # 694KB
list(APPEND SRC lost-empire.zip)     #   2MB
list(APPEND SRC mitsuba.zip)         #   2MB
list(APPEND SRC dabrovic-sponza.zip) #   4MB
list(APPEND SRC sportsCar.zip)       #   5MB
list(APPEND SRC sibenik.zip)         #   5MB
list(APPEND SRC conference.zip)      #   7MB
list(APPEND SRC dragon.zip)          #  17MB
list(APPEND SRC buddha.zip)          #  22MB
#list(APPEND SRC head.zip)            #  42MB
#list(APPEND SRC rungholt.zip)        #  48MB
#list(APPEND SRC hairball.zip)        #  50MB
#list(APPEND SRC crytek-sponza.zip)   #  79MB
#list(APPEND SRC powerplant.zip)      #  97MB
#list(APPEND SRC san-miguel.zip)      # 413MB

set(DST)
set(BASE_URL http://graphics.cs.williams.edu/data/meshes)

foreach(f ${SRC})
  set(url ${BASE_URL}/${f})
  set(file ${CMAKE_CURRENT_BINARY_DIR}/${f})
  get_filename_component(dir ${file} NAME_WE)
  string(TOLOWER ${dir} dir)
  set(dir ${CMAKE_CURRENT_BINARY_DIR}/${dir})
  list(APPEND DST ${dir})

  cma_fetch_url(${url} ${file})
  file(MAKE_DIRECTORY ${dir})
  execute_process(COMMAND ${CMAKE_COMMAND} -E tar xf ${file} WORKING_DIRECTORY ${dir})
endforeach()

install(DIRECTORY ${DST}
        DESTINATION ${${PROJECT_NAME}_SHARE_DIRECTORY}/hugh/data/mcguire
	COMPONENT   ${${PROJECT_NAME}_DAT_COMPONENT_NAME})
