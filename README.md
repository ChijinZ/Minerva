# Minerva

## Overview

Minerva is a browser fuzzer augmented by API mod-ref relations, aiming to synthesize highly-relevant browser API invocations in each test case. 

Basic idea: it extracts memory-level mod-ref relations between APIs via dynamic mod-ref analysis and leverages the relations to apply weighted API selection during test case generation. 

**NOTE**: This is just a prototype to reproduce experiments in our research paper. Some features are built as dynamic shared objects and their source code is not published.

## Environment

We tested Minerva on Ubuntu 20.04 and Ubuntu 22.04.

## Usage 

First, tell the fuzzer where the mod-ref relations locate:

```
export MEM_DEP_JSON_PATH=$MINERVA_PATH/mod_ref_helper/mem_dep.json
```

Then, you can generate html files using Minerva. Minerva is implemented on the top of [Domato](https://github.com/googleprojectzero/domato). Therefore, you can use Minerva in a way similar to Domato.


To see usage information:

```
python3 generator.py
```

To generate a single .html sample run:

```
python generator.py <output file>
```

To generate multiple samples with a single call run:

```
python generator.py --output_dir <output directory> --no_of_files <number of output files>
```

## Publication

Related paper is accepted by ESEC/FSE'22. ([preprint](http://wingtecher.com/themes/WingTecherResearch/assets/papers/FSE22_Minerva.pdf), [slides](https://github.com/ChijinZ/chijinz.github.io/blob/main/archive/minerva_fse22_pre.pdf)).

``.bib`` info:

```
@inproceedings{Chijin2022Minerva,
	author={Chijin Zhou, Quan Zhang, Mingzhe Wang, Lihua Guo, Jie Liang, Zhe Liu, Mathias Payer, Yu Jiang},
	title={Minerva: Browser API Fuzzing with Dynamic Mod-Ref Analysis},
	booktitle = {Proceedings of the 30th ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering},
	series={ESEC/FSE 2022},
	location={Singapore},
	year={2022},
}
```

## Acknowledgement

We reuse code from [Domato](https://github.com/googleprojectzero/domato) for input generation.