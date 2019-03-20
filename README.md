# DFA and DFA Minimization

## Getting Started

The program "DFA and DFA Minimization" is written Ruby Programming. 

### Prerequisites

Ruby-2x
gems:
	csv
	sets
	json

## Execution

### Verify DFA
```
ruby dfa.rb -i=test1.csv
```

### Verify String Acceptence
```
ruby dfa.rb -i=test1.csv -s=abbb
```

### DFA Minimization
```
ruby dfa.rb -i=test1.csv -s=abbb -m
```
### For mor help
```
ruby dfa.rb -h
```

## Sample Output

```
gc@gc:~/Documents/TF-P/geeth$ ruby dfa.rb -i=test1.csv -s=abbb -m
Transition table of give file:

	+---------------+---------------+---------------+---------------+---------------+
	|	F	|	I	|	δ	|	a	|	b	|
	+---------------+---------------+---------------+---------------+---------------+
	|	 	|	>	|	A	|	B	|	F	|
	|	 	|	 	|	B	|	G	|	C	|
	|	*	|	 	|	C	|	A	|	C	|
	|	 	|	 	|	D	|	C	|	G	|
	|	 	|	 	|	E	|	H	|	F	|
	|	 	|	 	|	F	|	C	|	G	|
	|	 	|	 	|	G	|	G	|	E	|
	|	 	|	 	|	H	|	G	|	C	|
	+---------------+---------------+---------------+---------------+---------------+

Success: Given input file is DFA
********************** String Acceptence **********************

Input string "abbb":

	ACCEPTED

String computation:

	[A,abbb]

	├─ [B, bbb]

	├─ [C, bb]

	├─ [C, b]

	├─ [C, λ]

	 "C" is a final state
********************** DFA Minimization **********************
Step1
Table of state inequivalences:

	 +---+
	B|   |
	 +---+---+
	C|   |   |
	 +---+---+---+
	D|   |   |   |
	 +---+---+---+---+
	E|   |   |   |   |
	 +---+---+---+---+---+
	F|   |   |   |   |   |
	 +---+---+---+---+---+---+
	G|   |   |   |   |   |   |
	 +---+---+---+---+---+---+---+
	H|   |   |   |   |   |   |   |
	 +---+---+---+---+---+---+---+
	   A   B   C   D   E   F   G

Step2
Table of state inequivalences:

	 +---+
	B|   |
	 +---+---+
	C| ✓ | ✓ |
	 +---+---+---+
	D|   |   | ✓ |
	 +---+---+---+---+
	E|   |   | ✓ |   |
	 +---+---+---+---+---+
	F|   |   | ✓ |   |   |
	 +---+---+---+---+---+---+
	G|   |   | ✓ |   |   |   |
	 +---+---+---+---+---+---+---+
	H|   |   | ✓ |   |   |   |   |
	 +---+---+---+---+---+---+---+
	   A   B   C   D   E   F   G

Step3: Final Cycle
Table of state inequivalences:

	 +---+
	B| ✓ |
	 +---+---+
	C| ✓ | ✓ |
	 +---+---+---+
	D| ✓ | ✓ | ✓ |
	 +---+---+---+---+
	E|   | ✓ | ✓ | ✓ |
	 +---+---+---+---+---+
	F| ✓ | ✓ | ✓ |   | ✓ |
	 +---+---+---+---+---+---+
	G| ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
	 +---+---+---+---+---+---+---+
	H| ✓ |   | ✓ | ✓ | ✓ | ✓ | ✓ |
	 +---+---+---+---+---+---+---+
	   A   B   C   D   E   F   G

Minimized DFA Output
Transition table of give file:

	+---------------+---------------+---------------+---------------+---------------+
	|	F	|	I	|	δ	|	a	|	b	|
	+---------------+---------------+---------------+---------------+---------------+
	|	 	|	>	|	AE	|	BH	|	DF	|
	|	 	|	 	|	BH	|	G	|	C	|
	|	 	|	 	|	DF	|	C	|	G	|
	|	*	|	 	|	C	|	AE	|	C	|
	|	 	|	 	|	G	|	G	|	AE	|
	+---------------+---------------+---------------+---------------+---------------+

Success: Given input file is DFA
********************** string Acceptence for Minimized DFA **********************

Input string "abbb":

	ACCEPTED

String computation:

	[AE,abbb]

	├─ [BH, bbb]

	├─ [C, bb]

	├─ [C, b]

	├─ [C, λ]

	 "C" is a final state

```
## Authors

* **Geeth Mohan Chowdary Marathi** *