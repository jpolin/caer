IF (NOT ENABLE_IMAGESTREAMERBEEPER)
	SET(ENABLE_IMAGESTREAMERBEEPER 0 CACHE BOOL "Enable the image streamer beeper module, which generates beeps based on input variable")
ENDIF()

IF (ENABLE_IMAGESTREAMERBEEPER)

	PKG_CHECK_MODULES(ALLEGRO5_AUDIO REQUIRED)
	pkg_check_modules(ALLEGRO5_ACODEC REQUIRED)
	

	SET(CAER_COMPILE_DEFINITIONS ${CAER_COMPILE_DEFINITIONS} -DENABLE_IMAGESTREAMERBEEPER=1 PARENT_SCOPE)

	SET(CAER_IMAGESTREAMERBEEPER_FILES modules/imagestreamerbeeper/imagestreamerbeeper.c)


	# Propagate to parent scope.
	SET(CAER_C_LIBS ${CAER_C_LIBS} "-lallegro_audio -lallegro_acodec" PARENT_SCOPE)
	
	SET(CAER_C_SRC_FILES ${CAER_C_SRC_FILES} ${CAER_IMAGESTREAMERBEEPER_FILES} PARENT_SCOPE)

ENDIF()
