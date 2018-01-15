#
# Copyright 2018 Jeff Bush
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

project(de2_115)

add_custom_target(synthesize
	COMMAND quartus_map de2_115
	COMMAND quartus_fit de2_115
	COMMAND quartus_asm de2_115
	COMMAND quartus_sta de2_115
    COMMAND ./print_summary.py
    COMMENT "Synthesizing"
    DEPENDS bootrom)

add_custom_target(program
    COMMAND quartus_pgm -m jtag -o "P;output_files/de2_115.sof")


