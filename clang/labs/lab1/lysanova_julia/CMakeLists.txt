add_llvm_library(LysanovaDepWarnPlugin MODULE deprecatedPlugin.cpp PLUGIN_TOOL clang)

if(WIN32 OR CYGWIN)
  set(LLVM_LINK_COMPONENTS
      Support
  )
  clang_target_link_libraries(LysanovaDepWarnPlugin PRIVATE
    clangAST
    clangBasic
    clangFrontend
    )
endif()

set(CLANG_TEST_DEPS "LysanovaDepWarnPlugin" ${CLANG_TEST_DEPS} PARENT_SCOPE)
