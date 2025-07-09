tool:
	cmake --build build	
setup:
	cmake -G Ninja -B build -DPINKIT=${PIN_ROOT} -DARCH=intel64 -DSTAPIN_REPO=~/localdisk/STAPIN/<removed>
setup.debug:
	cmake -G Ninja -B build -DPINKIT=${PIN_ROOT} -DARCH=intel64 -DSTAPIN_REPO=~/localdisk/STAPIN/<removed> -DCMAKE_BUILD_TYPE=Debug
clean:
	rm -rf build
