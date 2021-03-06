### LATEST NEWS
The HALC paper is accepted for publication in BMC Bioinformatics!

### Overview
HALC is software that makes error correction for long reads with high throughput.

### Copy right
HALC is under the [Artistic License 2.0](http://opensource.org/licenses/Artistic-2.0).

### Short manual
1. System requirements

   HALC is suitable for 32-bit or 64-bit machines with Linux operating systems. At least 4GB of system memory is recommended for correcting larger data sets.

2. Installation

   Aligner [BLASR](https://github.com/PacificBiosciences/blasr) and error correction software [LoRDEC](http://www.atgc-montpellier.fr/lordec/) (only for -ordinary mode) are required to run HALC.
   * The source files in 'src' and 'thirdparty' folders can be compiled to generate a 'bin' folder by running Makefile: `make all`.
   * Put BLASR, LoRDEC and the 'bin' folder to your $PATH: `export PATH=PATH2BLASR:$PATH` , `export PATH=PATH2LoRDEC:$PATH` and `export PATH=PATH2bin:$PATH`, respectively.

3. Inputs
   * Long reads in FASTA format.
   * Contigs assembled from the corresponding short reads in FASTA format.
   * The initial short reads in FASTA format (only for -ordinary mode; obtained with `cat left_reads.fa >short_reads.fa` and then `cat right_reads.fa >>short_reads.fa`).

4. Using AlignGraph

   ```
   runHALC.py long_reads.fa contigs.fa [-options|-options]
   ```

   <p>Options (default value):<br>
   -o/-ordinary short_reads.fa (yes)<br>
   Ordinary mode utilizing repeats to make correction. The error correction software LoRDEC and the initial short reads are required to refine the repeat corrected regions. It is exclusive with the -repeat-free option.<br>
   -r/-repeat-free (no)<br>
   Repeat-free mode without utilizing repeats to make correction. It is exclusive with the -ordinary option.<br>
   -b/-boundary n (4)<br>
   Maximum boundary difference to split the subcontigs.<br>
   -a/-accurate (yes)<br>
   Accurate construction of the contig graph.<br>
   -c/-coverage n (auto)<br>
   Expected coverage on contigs. If not specified, it can be automatically calculated.<br>
   -w/-width n (4)<br>
   Maximum width of the dynamic programming table.<br>
   -k/-kmer n (25)<br>
   Kmer length for LoRDEC refinement.<br>
   -t/-threads n (auto)<br>
   Number of threads for one process to create. It is automatically set to the number of computing cores.<br>
   -l/-log (no)<br>
   System log to print.</p>
   
5. Outputs
   * Error corrected full long reads.
   * Error corrected trimmed long reads.
   * Error corrected split long reads.

### Chinese name
   HALC's Chinese name is 浩克.


