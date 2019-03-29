# CacheDOS

## Setup

### Initialize submodules

	$ git submodule update --init
	$ git submodule update --remote

### Make benchmarks and kernel modules

	$ cd IsolBench/bench; make; cd ../../
	$ cd memguard; make; cd ..
	$ cd base-memguard; make; cd ..

### Maximize performance

	$ sudo ./util/maxperf.sh
	$ sudo service lightdm stop

## Evaluation

### Recreate a specific figure

Move the Fig# subdirectory (replace # with the figure's numeric value):

	$ cd figures/Fig#/
	$ sudo ./run.sh

### Recreate all figures

	$ cd figures
	$ sudo ./run-tests.sh


Note that Figure 5 requires that the kernel be patched with PALLOC. For
patching instructions please refer to [https://github.com/heechul/palloc](https://github.com/heechul/palloc).

## Figure creation

### Copying Results

After a figure's tests are run, there will be one or more result text files generated
in its Fig# directory. These results need to be manually copied to figures/results.csv,
specifically in the columns for that figure (typically B through F).

For example text files and the relevant data to place in the results.csv file, please
refer to [Example Results](https://github.com/mbechtel2/CacheDOS/wiki/Example-Results).

### Plot Generation

Once all the results are copied, columns H through L will contain the data to be copied to the corresponding
.dat files. The file to place the data in will be in the cells beginning with a '#'.

A single figure can then be generated by going to the figures Fig# directory and running:

	$ gnuplot gen.gp

and all figures can be generated by running:

	$ ./gen-figures

from the figures directory.

## Citation

The paper detailing the CacheDOS attacks can be found at [https://arxiv.org/abs/1903.01314](https://arxiv.org/abs/1903.01314).
It can be cited using the following BibTeX entry:

	@inproceedings{bechtel2019dos,
		title = {Denial-of-Service Attacks on Shared Cache in Multicore: Analysis and Prevention},    
		author = {Michael G Bechtel and Heechul Yun},
		booktitle = {IEEE International Conference on Real-Time and Embedded Technology and Applications Symposium (RTAS)},
		year = {2019}
	}
