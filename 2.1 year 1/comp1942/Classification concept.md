##### accuracy
- proportion of values in target attribute thats is correctly predicted
![[Pasted image 20220514161256.png]]
Accuracy=5/6=83.3%

##### Precision
$$\frac{total\space no\space of\space values \space in \space target \space attribute \space correctly \space predicted \space as \space yes}{total \space no \space of \space values \space in \space the \space target \space attribute \space predicted \space as \space yes}$$

![[Pasted image 20220514161732.png]]
Precision=2/3=0.67

##### Recall
$$\frac{total\space no\space of\space values \space in \space target \space attribute \space correctly \space predicted \space as \space yes}{total \space no \space of \space values \space in \space the \space target \space attribute \space equal \space to \space yes}$$
![[Pasted image 20220514161856.png]]
Recall=2/2=1.0

##### f-measure/ f1-score
$$=\frac{2*Precision*Recall}{Precision+Recall}$$
![[Pasted image 20220514162109.png]]
f-measure=$\frac{2*0.67*1.0}{0.67+1.0}=0.80$

##### Specificity (Reverse recall)
$$\frac{total\space no\space of\space values \space in \space target \space attribute \space correctly \space predicted \space as \space no}{total \space no \space of\space actual \space values \space in \space the \space target \space attribute \space equal \space to \space no}$$
![[Pasted image 20220514162327.png]]
Specificity=3/4=0.75
							predicted value      actual value
True positive      Yes                          Yes
False positive     Yes                          No
True negative     No                           No
False negative    No                           Yes

2-phases
Training Phase
training set
validation set
- used to fine-tune the model
- different model have different ways of fine tuning
test set
Prediction Phase
