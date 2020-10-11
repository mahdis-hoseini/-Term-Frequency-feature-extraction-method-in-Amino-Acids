# -Term-Frequency-feature-extraction-method-in-Amino-Acids
One method of feature extraction in amino acid sequences

import re, sys, os
from collections import Counter
pPath = os.path.split(os.path.realpath(__file__))[0]
sys.path.append(pPath)
import readFasta
import checkFasta
import numpy as np
import pandas as pd
import collections, numpy

kw = {'path': r"H_train.txt",'order': 'ACDEFGHIKLMNPQRSTVWY'}
fastas = readFasta.readFasta(r"H_train.txt")
AA = kw['order'] if kw['order'] != None else 'ACDEFGHIKLMNPQRSTVWY'
header = []
encodings = []
x= ['A','C','D','E','F','G','H','I','K','L','M','N','P','Q','R','S','T','V','W','Y']
encodings.append(x)

for i in fastas:
    sequence = i[1]
    sequence=list(sequence)
    code=[]
    code.append(sequence.count('A'))
    code.append(sequence.count('C'))
    code.append(sequence.count('D'))
    code.append(sequence.count('E'))
    code.append(sequence.count('F'))
    code.append(sequence.count('G'))
    code.append(sequence.count('H'))
    code.append(sequence.count('I'))
    code.append(sequence.count('K'))
    code.append(sequence.count('L'))
    code.append(sequence.count('M'))
    code.append(sequence.count('N'))
    code.append(sequence.count('P'))
    code.append(sequence.count('Q'))
    code.append(sequence.count('R'))
    code.append(sequence.count('S'))
    code.append(sequence.count('T'))
    code.append(sequence.count('V'))
    code.append(sequence.count('W'))
    code.append(sequence.count('Y'))
    encodings.append(code)
data1=np.matrix(encodings[1:])[:,1:]
data_=pd.DataFrame(data=data1)
data_.to_csv('split_Amino_H')
