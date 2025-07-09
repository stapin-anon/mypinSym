tool:
	cmake --build build	
	g++ -g hello.cpp -o hello
setup:
	cmake -G Ninja -B build -DPINKIT=${PIN_ROOT} -DARCH=intel64 -DSTAPIN_REPO=~/Tools/<removed>
setup.debug:
	cmake -G Ninja -B build -DPINKIT=${PIN_ROOT} -DARCH=intel64 -DSTAPIN_REPO=~/Tools/<removed> -DCMAKE_BUILD_TYPE=Debug
clean:
	rm -rf build hello
