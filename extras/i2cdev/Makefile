# 
# Makefile for EM7180 i2cdev examples
#
# Copyright (C) 2018 Simon D. Levy
#
# This file is part of EM7180.
#
# EM7180 is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# EM7180 is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with EM7180.  If not, see <http://www.gnu.org/licenses/>.

# Change this to whereever you installed CrossPlatformI2C
CPDB = $(HOME)/CrossPlatformDataBus
  
ALL = MasterTest

EMSRC = ../../src

all: $(ALL)

I2CINC = $(CPDB)/src
I2CSRC = $(CPDB)/extras/i2c/i2cdev/src

MasterTest: MasterTest.o EM7180.o EM7180_Master.o I2CDevI2C.o main.o
	g++ -std=c++11 -o MasterTest MasterTest.o EM7180.o EM7180_Master.o I2CDevI2C.o main.o 

MasterTest.o: MasterTest.cpp 
	g++ -std=c++11 -Wall -I$(I2CINC) -I$(EMSRC) -c MasterTest.cpp

EM7180.o: $(EMSRC)/EM7180.cpp 
	g++ -std=c++11 -Wall -I$(I2CINC) -I$(EMSRC) -c $(EMSRC)/EM7180.cpp

EM7180_Master.o: $(EMSRC)/EM7180_Master.cpp 
	g++ -std=c++11 -Wall -I$(I2CINC) -I$(EMSRC) -c $(EMSRC)/EM7180_Master.cpp

I2CDevI2C.o: $(I2CSRC)/I2CDevI2C.cpp 
	g++ -std=c++11 -Wall -I$(I2CINC) -c $(I2CSRC)/I2CDevI2C.cpp

main.o: main.cpp 
	g++ -std=c++11 -Wall -c main.cpp

run: GetInfo
	./GetInfo

edit:
	vim GetInfo.cpp

clean:
	rm -f $(ALL) *.o *~
