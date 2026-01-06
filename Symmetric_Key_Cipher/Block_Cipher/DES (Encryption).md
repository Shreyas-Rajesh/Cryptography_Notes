Basics of how DES works
![[DES_Basic_NESO.png]]

In the initial permutation function consider a 8x8 matrix (total 64 bits) and the positions are jumbled. Here each number represents represents the bit position.
![[DES_Initial_NESO.png]]


In this the Plaintext after the initial permutation is split into two halves and then undergoes functions.... read and findout :) 
Note the left half of the round output is basically the previous right half.
![[DES_Round_NESO.png]]


The swap function basically moves the first 32bits of the 64bit value to the end.


Now whatever output we get from the 32bit output function is arranged like this. Here each number represents the bit position, ie the 1bit is placed on the box containing the number 1.
![[DES_InverseIP_NESO.png]]

