#################################################################################
#                       sl-platform library(CMake)
#                           SavaLione 
#                           2020-11-10
#################################################################################
# Copyright (c) 2020 Savely Pototsky (SavaLione)
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer.
# 2. Redistributions in binary form must reproduce the above copyright
#    notice, this list of conditions and the following disclaimer in the
#    documentation and/or other materials provided with the distribution.
# 3. Neither the name of the copyright holder nor the names of its contributors
#    may be used to endorse or promote products derived from this software
#    without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND
# ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
# OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
# HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
# OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
# SUCH DAMAGE.
#################################################################################
# Checking the minimum version
cmake_minimum_required (VERSION 3.13.1)

set(SL_PLATFORM_PROJECT "sl-platform")
set(SL_PLATFORM_PROJECT_VERSION "0.0.1")

#configure_file(${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.cmake ${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile)

project(${SL_PLATFORM_PROJECT}
	VERSION ${SL_PLATFORM_PROJECT_VERSION}
	LANGUAGES C CXX
)

set(SL_PLATFORM_SOURCES
	src/platform/platform.h
	src/platform/platform.cpp
)

option(SL_PLATFORM_STATIC_LIB "${SL_PLATFORM_PROJECT}. Build static library" ON)
if(SL_PLATFORM_STATIC_LIB)
	add_library(${SL_PLATFORM_PROJECT} STATIC ${SL_PLATFORM_SOURCES})
else()
	add_library(${SL_PLATFORM_PROJECT} SHARED ${SL_PLATFORM_SOURCES})
endif()

add_library(${SL_PLATFORM_PROJECT}::${SL_PLATFORM_PROJECT} ALIAS ${SL_PLATFORM_PROJECT})

target_include_directories(${SL_PLATFORM_PROJECT} PUBLIC ${PROJECT_SOURCE_DIR}/src)