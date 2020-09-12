# Edit following two lines to set component requirements (see docs)

set(COMPONENT_REQUIRES 
)

set(COMPONENT_PRIV_REQUIRES 
)

set(COMPONENT_SRCS 
  "../AppIso/App_Base.c"
  "../AppIso/App_Main.c"
  "../AppIso/App_VTClient.c"
  "../AppIso/App_VTClient.h"
  "../AppIso/App_VTClientLev2.c"
  "../AppIso/AppMemAccess.cpp"
  "../AppCommon/AppOutput.c"
  "../Samples/AddOn/AppIso_Output.c"
)

set(COMPONENT_ADD_INCLUDEDIRS 
  "."
  ".."
  "../lib_cci"
  "../AppIso"
  "../AppCommon"
  "../Settings"
)


register_component()
  
  
# Import the library, specifying a target name and the library path.
# The private dependencies of the library is also specified.
add_prebuilt_library(prebuilt_cci "../lib_cci/libcci_ecu_driver.a")

# `main` calls a function from the library, so link it to `main`
target_link_libraries(${COMPONENT_LIB} PRIVATE libcci_ecu_driver)
