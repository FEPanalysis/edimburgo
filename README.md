To run the analysis, execute the script with python

`python alchemical_analysis.py`

within the directory with the data files.

All the flags were customized to Sire; therefore, there is no need for you - at least at the stage of getting it to know - to provide any. Here is a brief overview what these flags are. (The focus is on those that are relevant to Sire, or, more accurately, to the situation when the files to be analyzed contain only the dV/dLambda data. `python alchemical_analysis.py -h` would yield a more detailed description).

-a is the name of the software the files come from; set to 'Sire'

-p is the data file prefix; set to 'actual_grad_'

-q is the data file suffix; set to 'dat'

-d is the path to where the data files are; set to '.'

-u is the units the free energy are to be reported in; kcal/mol

-r is the number of decimal places the free energies are to be reported with

-m is the methods the free energies are to be estimated with: TI and TI-CUBIC. If you want just TI-CUBIC, use -m ti_cubic

-g will produce graphs: the TI as a filled area under the interpolation curve (dhdl_TI.pdf) and the bar plot of ∆G's evaluated for each pair of adjacent states (dF_state.pdf). This requires matplotlib.

-s is to be used whenever you want to discard some initial snapshots

The file parser (`parser_sire.py`) is separated from the analysis proper (`alchemical_analysis.py`); make sure the former is either handy or a pythonpath is established for it. (There is `parser_gromacs.py`, as well, in case you want to run the analysis on Gromacs' files).

Also, to make it self-contained, all imports of not built-in modules needed for some non-trivial tasks have been hidden under the conditional statements. In other words, if you do not want to bother with the autocorrelation analysis (the -i flag) there is no need to checkout `timeseries.py` from the `pymbar` repository. numpy and matplotlib (for the graphs, optional) are the only prerequisites for the script.

(If you do not have python installed) Install one of its scientific distributions, like Enthought Canopy or Anaconda, and you will get it with a bunch of libraries (among which are numpy and matplotlib) rather than a stand-alone python.

Below is a list of the command the output files were obtained with.

output_1.txt:   
`python alchemical_analysis.py`
(Analysis with default settings)

output_2.txt:   
`python alchemical_analysis.py -m ti_cubic -u kJ -r 8`
(The free energies are to be estimated with TI-CUBIC and reported in kJ/mol, with 8 decimal places)

output_3.txt:   
`python alchemical_analysis.py -s 50`
(Skip first 50 ps)
