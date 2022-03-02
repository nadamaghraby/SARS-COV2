# SARS-COV2 Comparative Study
## Preparations: 
#### From Ghana, the data of SARS-COV-2(COVID-19) and its variant Omicron were collected. And the data was available in GISAID which is a public database of SARS-Cov-2 sequences and its variant.
## A.Choosing & manipulating sequences:
#### We chose 10 sequences from Delta and 10 from Omicron from Ghana by reading the Fasta files using Bio python library in Jupiter notebook and saving the new files containing 10 sequences each.
#### We considered Delta the reference one, omicron the case one.
## B. Building the Consensus Sequence
#### We made a multiple sequence alignment for the reference ones in order to construct the consensus sequence which we’re going to use as a single representative for the reference sequences.
#### Alignment using muscle: Alignment using → Mega Software for alignment (muscle), align by codon.
#### Constructing the sequence: Then we construct the consensus sequence using python, we extracted the seqs from the Fasta file (type: string) then we added them into a list.
#### Then we used a library called collections, importing Counter () → a function returns the most frequent nucleotide at each index of the 10 sequences; thus, we get the consensus sequence.
## C. MSL for Case Sequences (Omicron)
#### Then we applied a multiple seq alignment with the same technique for the case one (omicron sequence).
## D. The Phylogenetic tree
#### • Generating a fasta file: we merged all the above 20 sequences together in a single fasta file using Bio python. 
#### • MSL for all sequences: Then we applied a multiple sequence alignment on them using mega software, then we built the phylogenetic tree on them by neighbor joining using the same software.
![2022-03-02](https://user-images.githubusercontent.com/61421659/156399491-9423bdbc-0e35-4ff5-a1cc-b652d18d1545.png)
#### From the Phylogenetic tree: we figured out that the distance between sequences of omicron and delta in Ghana is very small, thus they are almost the same.The figure shows the distance and the confidence percentage of the distance.

## E. Average Percentage of Chemical Constituents
#### -We calculated the average percentage of the chemical constituents using: Bio python→ reading the fasta file using → SeqIO.parse() and re. findall () → returns the length of each chemical constituent in the whole sequence
#### -For every sequence: We used the re function to get the average: len(nucleotide)/len(seq) *100
#### we got the avg percent value for each one, then we got the CG content: [len(C) + len(G)]/len(seq)  *100
#### We’ve done this for the consensus / representative sequence for the reference ones and for all of the case sequences.
![2022-03-02 (1)](https://user-images.githubusercontent.com/61421659/156400838-c46d247a-45e1-4045-98c4-1c0abe6dc1d3.png)
![2022-03-02 (3)](https://user-images.githubusercontent.com/61421659/156401129-c44fff31-88d3-494c-b076-214e641bb566.png)



## F. Extracting the dissimilar regions
#### • Apply MSL technique: We applied the multiple sequence alignment on the 10 aligned omicron sequences with the representative one, then we separated the omicron sequences from the representative one.
#### • Extracting the regions: With the help of Jupiter notebook, we iterated on the case sequences comparing the sequence at each index with each other and with the representative sequence at the same index.
#### • The dissimilar regions/columns state that at each index the case ones have the same or almost the same nucleotide but different from the representative one.
#### • We implemented a function which returns a dictionary containing the index at which the most dissimilarities occur. The function takes a third a parameter which is the percentage of the alignment the user can choose → A threshold percentage for the dissimilarities
#### • We generated a csv excel file containing the index and the dissimilar region.
