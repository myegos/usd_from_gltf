# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

find_package(tclap)
if (NOT tclap_FOUND)
  message(FATAL_ERROR "TCLAP package not found.")
endif (NOT tclap_FOUND)

include_directories(
  ..
  ${USD_INCLUDE_DIRS}
  ${tclap_INCLUDE_DIR}
)

add_executable(usd_from_gltf
  args.cc
  args.h
  usd_from_gltf.cc
)

target_link_libraries(usd_from_gltf
  convert
  ${USD_LIBS}
)

install(TARGETS usd_from_gltf DESTINATION bin)
