
#-----------------------------------------------------------------------------
# ZeroCrossingBasedEdgeDetectionImageFilter tests
#-----------------------------------------------------------------------------
set(BASELINE ${CMAKE_CURRENT_SOURCE_DIR}/../Data/Baseline)
set(CLP ZeroCrossingBasedEdgeDetectionImageFilter)

add_executable(${CLP}Test ${CLP}Test.cxx)
target_link_libraries(${CLP}Test ${CLP}Lib)
set_target_properties(${CLP}Test PROPERTIES LABELS ${CLP})

set(testname ${CLP}Test)
add_test(NAME ${testname} COMMAND ${Launcher_Command} $<TARGET_FILE:${CLP}Test>
  --compare ${BASELINE}/ZeroCrossingBasedEdgeDetectionImageFilterTest.nhdr
            ${TEMP}/ZeroCrossingBasedEdgeDetectionImageFilterTest.nhdr
  ModuleEntryPoint
    ${TEST_DATA}/CTHeadResampled.nhdr
    ${TEMP}/ZeroCrossingBasedEdgeDetectionImageFilterTest.nhdr
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

