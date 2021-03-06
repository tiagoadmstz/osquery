# Copyright (c) 2014-present, Facebook, Inc.
# All rights reserved.
#
# This source code is licensed in accordance with the terms specified in
# the LICENSE file found in the root directory of this source tree.

function(osqueryDispatcherTestsMain)
  generateOsqueryDispatcherTestsTest()
  generateOsqueryDispatcherTestsSchedulerTest()
endfunction()

function(generateOsqueryDispatcherTestsTest)
  add_osquery_executable(osquery_dispatcher_tests-test dispatcher.cpp)

  target_link_libraries(osquery_dispatcher_tests-test PRIVATE
    osquery_cxx_settings
    osquery_database
    osquery_distributed
    osquery_events
    osquery_extensions
    osquery_extensions_implthrift
    osquery_registry
    osquery_remote_enroll_tlsenroll
    plugins_config_tlsconfig
    plugins_database_ephemeral
    specs_tables
    thirdparty_googletest
  )
endfunction()

function(generateOsqueryDispatcherTestsSchedulerTest)
  add_osquery_executable(osquery_dispatcher_tests_scheduler-test scheduler.cpp)

    target_link_libraries(osquery_dispatcher_tests_scheduler-test PRIVATE
    osquery_cxx_settings
    osquery_database
    osquery_distributed
    osquery_events
    osquery_extensions
    osquery_extensions_implthrift
    osquery_registry
    osquery_remote_enroll_tlsenroll
    plugins_config_tlsconfig
    plugins_database_ephemeral
    specs_tables
    osquery_utils_system_time
    thirdparty_googletest
  )
endfunction()

osqueryDispatcherTestsMain()
